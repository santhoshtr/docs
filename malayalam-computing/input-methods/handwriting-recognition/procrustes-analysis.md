# Procrustes Analysis

{% hint style="info" %}
My attempt for procrustes based handwriting recognition is available at [https://handwriting.smc.org.in/](https://handwriting.smc.org.in/)
{% endhint %}

In general, our problem is pattern matching of curves. The curves get complicated depending on the script. The curves are also very irregular because this is written by a user on a touch interface, mostly mobiles, using fingers\(rarely, a stylus\). So, we need a set of base representation of these curves and then compare the curves from user input and see if how close they are with the reference images.

#### The curves and strokes

The curves created in a two dimensional space can be represented by x,y coordinates. We need the coordinates at start, end positions of a drawing. Start is "pen down" point and end is "pen up" point for a handwriting. We also need to get coordinates for all relevant intermediate points in the curve. These relevant points are inflection points. So when we have `[(0,10), (20, 30)]`, we mean a straight line from `(0,10)` to `(20, 30)`. Note that we are assuming straight lines between each points. This is approximation of any possible path between those two points.

This is just one way of writing ക. It is possible that there are more than one style of writing a letter. We can use that also as base image. ക is usually written with a single stroke. Meaning, you take the pen up only after writing the full letter. But consider the letter `+`- it has two strokes. You need to take the pen up after a stroke. We also need to make sure that the direction of pen movement is taken into consideration. So the array of points should follow the same order of pen movement.

Considering all these, we can have a representation of reference image of ക as :

We can represent it in a json format.

```javascript
 "ക": {
      "samples": [
        {
          "strokes": [
            [
                {"x": 107,  "y": 72 },
                {"x": 139, "y": 12 },
                {"x": 190, "y": 4 },
                {"x": 206, "y": 43 },
                {"x": 208, "y": 175 },
                {"x": 168, "y": 240 },
                {"x": 133, "y": 250 },
                {"x": 112, "y": 148 },
                {"x": 89, "y": 238 },
                {"x": 57, "y": 262 },
                {"x": 15, "y": 267 },
                {"x": 0, "y": 236 },
                {"x": 13, "y": 171 },
                {"x": 174, "y": 102 },
                {"x": 250, "y": 102 },
                {"x": 277, "y": 123 },
                {"x": 281, "y": 198 },
                {"x": 266, "y": 247 }
            ]
          ]
        }
      ]
    },
```

### How to prepare the curve data

The above data should be prepared for every letter in the script. That is very tedious process. We need some tool to get this representation when we draw it. So I wrote a javascript application with an HTML5 canvas where you draw ,using mouse or finger and get this simplified representation of the curve.

Curve simplification is an interesting problem, but fortunately I did not had to implement it myself. There is an excellend javascript library that does exactly this, named [simplifyjs](http://mourner.github.io/simplify-js/). I just used it. It also allows setting the smoothness factor, depending on that we get more points to represent a curve or less points.

### Compare the writing

So, once we have the reference data prepared for a letter, we should compare it against a representation of user drawn letter. This is the core part of handwriting recognition. As far as the user interface is concerned, you can imagine that there is a canvas where a user can draw a letter using finger or mouse or stylus. We get a representation of that drawing in the same data structure we used for reference image.

Comparing to irregular curves for a match is a difficult problem. One curve may be bigger than other. One may be smoother than other. We need accommodate all kind of distortions. The drawing may be tilted too. There is a technique to compare two shapes considering all these challenges - Procrustes Analysis.

### Procrustes Analysis

In statistics, Procrustes analysis is a form of statistical shape analysis used to analyse the distribution of a set of shape\(See [Procrustes Analysis, Wikipedia](https://en.wikipedia.org/wiki/Procrustes_analysis)\). To compare the shapes of two or more objects, the objects must be first optimally "superimposed". Procrustes superimposition \(PS\) is performed by optimally translating, rotating and uniformly scaling the objects.

\(Image credit: [Wikimedia commons](https://commons.wikimedia.org/wiki/File:Procrustes_superimposition.png) Author: Christian Peter Klingenberg, Uploaded by user:Was a bee \)

For comparing a letter drawn by a user with the reference image, same approach was used. They are compared by rotating and scaling. the rotation is limited to 45 degree. Otherwise z and s may match!. Rotation and scaling is done in steps and at each step a score of match is calculated. If it cross a predefined threshold, we declare it as a match.

For Procruster based matching, I used [curvematcher library](https://github.com/chanind/curve-matcher)

{% hint style="info" %}
ഗ്രീക്ക് ഐതിഹ്യത്തിലെ ക്രൂരനായ ഒരു കൊല്ലപ്പണിക്കാരനാണ് പ്രൊക്രൂസ്റ്റസ്. വഴിയാത്രക്കാരെ വീട്ടിലേക്ക് ക്ഷണിച്ച് വിരുന്നൂട്ടി തന്റെ ഇരുമ്പുകട്ടിലിൽ വിശ്രമിക്കാൻ ക്ഷണിക്കും. കട്ടിലിനേക്കാൾ വലിയ ആളാണെങ്കിൽ കയ്യും കാലും അരിഞ്ഞ് വിരുന്നുകാരനെ കട്ടിലിനൊപ്പമാക്കും. ആളു ചെറുതാണെങ്കിൽ ചുറ്റികകൊണ്ടടിച്ച് വലിച്ച് കട്ടിലിനൊപ്പമാക്കും. ഇദ്ദേഹത്തെ പിന്നീട് തിസ്യൂസ് കൊല്ലുന്നതാണ് കഥ. കട്ടിലിനൊപ്പിച്ച് എല്ലാത്തിനെയും വലുപ്പമൊപ്പിക്കുന്ന ഏർപ്പാടിനെ പ്രൊക്രൂസ്റ്റിയൻ എന്ന് വിളിക്കാറുണ്ട്\(one size fits all\).
{% endhint %}

### Implementation

The software implementation of this system has the following parts

* The reference image database in json format
* The matching logic
* The user interface of the system
* The training UI or UI to easily create the reference data.

Source code is availabe at [gitlab](https://gitlab.com/smc/handwriting) and ou can try the system here: [ https://smc.gitlab.io/handwriting](https://smc.gitlab.io/handwriting)

As you can observe from the above video, the letter '4' is a multistroke letter. This is supported by checking if the pen down of second stroke is within the drawing box of previous stroke. You can also see distortions, writing angle, spacing - all taken care of.

### Training

To prepare the reference data, a web application is being developed. It is similar to the handwriting recognition, but here a developer will draw a letter and tell which character it is. This data is then exported to the json file.

It is available at [https://smc.gitlab.io/handwriting/training](https://smc.gitlab.io/handwriting/training)

This application is still missing many features.

### What is next

* Expand the reference data to cover most of common malayalam script.
* Expand further with style alternatives for each letter.
* Reduce the UI glitches
* Finish the training UI
* Convert it as a real input method that works with Operating systems, so that you can type directly to applications.
* An experimental support for Tamil is added. Enhance that with the help of Tamil speaking friends.
* More languages.
* Post-recognition corrections of words using spellcheck, predictive entry mechanisms likes \[Markov chain\]\[11\] can improve the accuracy significantly.
* While writing letters like "കോ", we write േ sign first, while the actual data is ക + ോ. So we need a visual to unicode reordering logic.

I am not getting enough time to spend on this project these days. If anybody interested in helping, please contact me.

Anish was contributing to this project recently. He presented this project in IndiaOS 2020\([Video](https://www.youtube.com/watch?list=PLOGilj110olxSrSHNoYOGnIFJweyGIZRo&v=WfzuyD0Fcgs)\)

### Advantages

This approach is able to handle a large variety of irregular curves in handwriting without learning each and every such possibilities. Machine learning approach require large collection of handwriting samples. Here even with one sample, we can recognize so many variations. Additional provision of supporting style variants are also provided.

There is nothing script specific in this approach. So, using this for another language like Tamil is very easy. Note that if the script has connective writing like English running letter, our approach has a serious issue - we rely on 'pen ups' for identifying ligatures.

### Drawbacks

While the script characteristics of Malayalam or other languages discussed here can provide some advantages in the approach, it should not be forgotten that a normal user also usually writes English content. The English content can be in running letter style too. So quickly the problem becomes multi-script handwriting recognition. Unlike the keyboards which provide explicit script selection, handwriting recognition systems are better if it works without such language switch.

The system is written in javascript, but it may be difficult to get intergrated with Operating system to act as native input method. Jishnu tried to port this as react native application\([Code](https://gitlab.com/jishnu7/handmobile)\)


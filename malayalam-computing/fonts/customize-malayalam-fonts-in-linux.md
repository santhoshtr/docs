# Customize Malayalam fonts in Linux

Now a days GNU/Linux distributions like Ubuntu, Debian, Fedora etc comes with pre-configured fonts for Malayalam. For Sans-serif family, it is Meera and  for serif, it is Rachana. If you like to change these fonts, there is no easy way to do with configuration tools in Gnome or KDE. They provide a general font selector for the whole desktop, but not for a given language.

The advantage of setting these preference at system level is, you don’t need to choose this fonts at application level then. For example, you don’t need to set them for firefox, chrome etc. All will follow the system preferences. We will use [fontconfig](https://www.freedesktop.org/software/fontconfig/fontconfig-user.html) for this

First, create a file named **`~/.config/fontconfig/conf.d/50-my-malayalam.conf`.** If the folders for this file does not exist, just create them. To this file, add the following content.

```text
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
<match>
  <test name="lang" compare="contains">
    <string>ml</string>
  </test>
  <test name="family">
    <string>sans-serif</string>
  </test>
  <edit name="family" mode="prepend">
    <string>Manjari</string>
  </edit>
</match>
<alias>
  <family>Manjari</family>
  <default>
    <family>sans-serif</family>
  </default>
</alias>
</fontconfig>
```

Save the file and you are done. You can check if the default font for Malayalam changed or not using the following command

```text
$ LANG=ml_IN fc-match
```

It should list Manjari. The above code we added to the file is not complicated. You can see that we are setting the sans-serif font preference for ml\(Malayalam\) language as Manjari. Also serif font preference as Rachana. You are free to change the fonts to whatever you prefer.

Note that you may want to close and open your applications to get this preference applied.

You may choose one of the fonts available at [smc.org.in/fonts](https://smc.org.in/fonts), download and install and use the above configuration with it.


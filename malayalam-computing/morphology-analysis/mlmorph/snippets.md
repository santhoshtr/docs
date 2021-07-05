# Snippets

### Find all strings with given prefix

```text
#include "symbols.fst"

$words$ = "<malayalam.a>"

$prefix$ = ചാടിപ്പോയി
$completion$ = $prefix$ [#Letters#]+

$words$ || $completion$
```


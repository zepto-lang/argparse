# argparse

A minimal argument parser for CLI applications in zepto in just
over 100 lines. It is mostly thought of as a proof of concept, but
it does indeed work pretty well. If the API appeals to you
aesthetically, feel free to use it as you like.

##Usage

There is a file named `test.zp` that uses the module, if you need a
running example.
Usage could look like this:

```clojure
(define argparse:handle-args (import "argparse:handle-args"))
(argparse:handle-args
    "this program kills zombies"
    (list (make-hash ["name"    "foo"]
                     ["type"    :number]
                     ["default" 10]
                     ["required" #f]
                     ["usage"   "foo you"])
          (make-hash ["name"    "bar"]
                     ["type"    :string]
                     ["options" ("baz)]
                     ["usage"   "bar me"])
          (make-hash ["name" "bool"]
                     ["short" "b"]
                     ["type" :boolean]
                     ["usage" "some boolean"])))
```

It uses the module's most important entry-point, `handle-args`.
The function takes the program's description plus a list of hashmaps
representing the arguments (with "name", "type" and, optionally,
"usage") and returns a hashmap containing the arguments
and their respective values. "short" is a special for boolean flags
to allow arguments as "-b", for example. Grouping of those (e.g. "-xbd")
is also allowed. The remaining arguments are ignored.

If the arguments are misformatted, the library will print usage
information and return `nil`. If an argument that is not within
the (optional) `options` parameter is given this will also result
in a failure and the allowed options will be printed.

Usage info will look something like this:

```
error: argument "bar" must be one of the following: baz.

usage: test [foo|bar|bool]

  this program kills zombies

Arguments:
	-b, --bool	some boolean
	--bar STRING	bar me [required]
	--foo NUMBER	foo you
```

<hr/>

*Have fun!*

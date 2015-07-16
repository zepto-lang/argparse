# argparse

A minimal argument parser for CLI applications in zepto in just
over 80 lines. It is mostly thought of as a proof of concept, but
it does indeed work pretty well. If the API appeals to you
aesthetically, feel free to use it as you like.

##Usage

There is a file named `test.zp` that uses the module.
It looks like this:

```clojure
(argparse:handle-args "test"
    (list (make-hash ["name"    "foo"]
                     ["type"    :number]
                     ["default" 10]
                     ["usage"   "foo you"])

          (make-hash ["name"    "bar"]
                     ["type"    :string]
                     ["usage"   "bar me"])))
```

It uses the module's most important entry-point, `handle-args`.
The function takes the program's name plus a list of hashmaps
representing the arguments (with "name", "type" and, optionally,
"usage" and "type") and returns a hashmap containing the arguments
and their respective values. The remaining arguments are ignored.

If the arguments are misformatted, the library will print usage
information and return `nil`.

<hr/>

*Have fun!*

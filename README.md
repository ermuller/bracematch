# bracematch
a tool for quick-n-dirty minimal validation of formatting of Juniper-style configurations.  Juniper, PlaoAlto, Vyatta, and other similar nested formats should work.

This is a simple tool to verify that opening and closing braces match in Juniper-style configurations.
Key features are:
* checking brace matching
* reindenting
* displaying current header context per-line
* convert full config format to "set" statements

I find it useful for checking configuration sections offline prior to 'load merge', as well as for validating output of other configuration-management tools.

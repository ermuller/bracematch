# bracematch
a tool for quick-n-dirty minimal validation of formatting of Juniper configurations

This is a simple tool to verify that opening and closing braces match in Juniper-style configurations.
Key features are:
* checking brace matching
* reindenting
* displaying current header context per-line

I find it useful for checking configuration sections offline prior to 'load merge', as well as for validating output of other configuration-management tools.

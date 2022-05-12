# bracematch
## Overview
A tool for quick-n-dirty minimal validation of formatting of Juniper-style configurations, as well as translating config files into "set" statements.  Juniper, PaloAlto, Vyatta, and other similar nested formats should work.

This is a simple tool to verify that opening and closing braces match in Juniper-style configurations.
Key features are:
* checking brace matching
* reindenting
* displaying current header context per-line
* convert full config format to "set" statements

I find it useful for checking configuration sections offline prior to 'load merge', as well as for validating output of other configuration-management tools.

## Usage
### Syntax Validation
The original use case for bracematch was validation that template-generated device configurations didn't have any glaring syntax errors, and to help track down where problems such as a mismatched closing bracket for a section occurred.

Examples:

`cat myrouter.conf | bracematch -q && echo OK`

`cat myrouter.conf | bracematch`

### Convert Native Configuration to "set" Commands
This turns out to be really useful - one downside of the native JunOS-style
syntax is that simply grepping for an item won't provide the context to
tell where the item of interest is used.  Or for platforms like Palo Alto
that don't have an easy "load merge" equivalent, this allows you to easily
restore via CLI from a backup, or otherwise duplicate/alter configs.

Example:
```
$ cat <<EOF | bracematch -s
> system {
>     host-name myrouter;
> }
> EOF
set system host-name myrouter
```

Comments via Juniper "annotate" are attempted to be preserved, but this feature
is still considered experimental, as not all contexts can be easily identified.


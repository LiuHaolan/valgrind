## How to make a valgrind tool

1, Choose a name for the tool, and a two-letter abbreviation that can be used as a short prefix. We'll use foobar and fb as an example.

2, Make three new directories foobar/, foobar/docs/ and foobar/tests/.

3, Create empty files foobar/docs/Makefile.am and foobar/tests/Makefile.am.

4, Copy none/Makefile.am into foobar/. Edit it by replacing all occurrences of the string "none" with "foobar", and all occurrences of the string "nl_" with "fb_".

5, Copy none/nl_main.c into foobar/, renaming it as fb_main.c. Edit it by changing the details lines in nl_pre_clo_init() to something appropriate for the tool. These fields are used in the startup message, except for bug_reports_to which is used if a tool assertion fails. Also replace the string "nl_" with "fb_" again.

6, Edit Makefile.am, adding the new directory foobar to the TOOLS or EXP_TOOLSvariables.

7, Edit configure.ac, adding foobar/Makefile, foobar/docs/Makefile and foobar/tests/Makefile to the AC_CONFIG_FILES list.

Run:
```
  autogen.sh
  ./configure 
  make
  make install
```

Test it with a command like
```
valgrind -tool=foobar data
```
data is just an example

## Reference
http://www.valgrind.org/docs/manual/writing-tools.html

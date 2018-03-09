unbuild.bat: 

extracts any *.a library in GNU librarian format into several *.o arm-eabi objects.

Then if you setup ToolchainGenericDS properly, you can use through msys, the Makefile (make) rule to repack all objects into a GNU librarian static library *-out.a
because the default ar tool wants each object to link against the GNU librarian written by hand (afaik).



export.bat:
disassembles any *.o arm-eabi object into readable text
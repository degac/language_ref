
=====================
Conditional compiling
=====================

Conditional compiling allows you to turn compiling on or off from within your program depending on the environment the program is being compiled for.

Conditional compiling works a bit like an **If** statement, but takes the form:
{
**?**%Identifier
**

The **?** must appear at the start of a new line, and %Identifier should be one of the following:

[ **Name** | @Meaning
* Debug | True if program is being compiled in debug mode.
* Threaded | True if program is being compiled in threaded mode.
* Win32 | True if program is being compiled for the Windows operating system.
* MacOS | True if program is being compiled for the MacOS operating system.
* Linux | True if program is being compiled for the Linux operating system.
* X86 | True if program is being compiled for the Intel CPU.
* PPC | True if program is being compiled for the PowerPC CPU.
* MacOSX86 | True if program is being compiled for an Intel Mac.
* MacOSPPC | True if program is being compiled for a PowerPC Mac.
* BigEndian | True if program is being compiled for a big endian CPU.
* LittleEndian | True if program is being compiled for a little endian CPU.
]

%Identifier may also be preceded by **Not** to invert the result.

An **?** on its own always turns compiling on.

For example:
 
.. code-block:: blitzmax
	 
	?Debug
		'Any code here is only compiled in debug mode.
	?Not Debug
		'Any code here is only compiled in release mode.
	?
		'Code here is always compiled.
 

<div align="center">

## Advance Asm Calling


</div>

### Description

Advance Calling function in asembly no need for a linker with correct tables :).
 
### More Info
 


<span>             |<span>
---                |---
**Submitted On**   |
**By**             |[OpcodeVoid](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByAuthor/opcodevoid.md)
**Level**          |Advanced
**User Rating**    |4.3 (26 globes from 6 users)
**Compatibility**  |C, C\+\+ \(general\), Microsoft Visual C\+\+, Borland C\+\+, UNIX C\+\+
**Category**       |[Coding Standards](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByCategory/coding-standards__3-32.md)
**World**          |[C / C\+\+](https://github.com/Planet-Source-Code/PSCIndex/blob/master/ByWorld/c-c.md)
**Archive File**   |[](https://github.com/Planet-Source-Code/opcodevoid-advance-asm-calling__3-3549/archive/master.zip)





### Source Code

#include "stdafx.h"<br>
#include "windows.h"<br>
char * title = "Unhanlde Execpetion";<br>
	char * msg = "Proc Base Address";<br>
	char *dump = "Hello";<br>
FARPROC DLLADDRESS;<br>
int APIENTRY WinMain(HINSTANCE hInstance,<br>
      HINSTANCE hPrevInstance,<br>
      LPSTR  lpCmdLine,<br>
      int  nCmdShow)<br>
{<br>
 	// TODO: Place code here.
<p>
	HINSTANCE HI;<br>
	HI = LoadLibrary("USER32.DLL");<br>
	 DLLADDRESS = GetProcAddress<br>(HI,"MessageBoxA");<br>
	if(DLLADDRESS == NULL)<br>
	{<br><p>
		MessageBox(NULL,"Dll not found","Error",MB_OK);<br>
		return 0;<br>
	}<br>
			_asm<br>
	{<br>
		//HWND<br>
		//MSG<br>
		//TITLE<br>
		//TYPE<br>
		push MB_OK<br>
		push title<br>
		push msg<br>
		push NULL<br>
		mov eax,DLLADDRESS<br>
		call eax<br>
	}<br>
	return 0;<br>
}<br>
//<h1> Soure End </h1>
<br>
Your might be wondering how it works. Very simple really<br> I just Get the address of a function in a library then push values into the stack.<br> Backwards because we push data into the stack LIFO(Last in first out). If you don't understand anything email vbmew@hotmail.com


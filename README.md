# FocusBorderHide

Remove a focus border (usually a white dotted line in common controls)

![image](https://github.com/wolfman616/FocusBorderHide/assets/62726599/fd4b78d9-0fb8-44bd-8865-1d34c6f4b37b)


simple utility script to remove active focus border if present. Please note, they come back as soon as the control creates it again when selections change via keyboard etc.

Included is 2 implementations;
1) via users keyboard inputs
2) via WindowsEventHook - Selection change

Each will attempt to circumnvent the focus border ever existing. However the event hook approach is technically superior. 

Eg1: 

"moving" with arrowkeys in a listview will create the focus border again.

This can easily be scripted away in conjunction with an event hook or a keyboard hook for example to the arrowkeys.

Eg1a: 

~LButton::
~Right::
~Left::
~Down::
~Up::
(instr(ContTitlGetActive(),"syslistview32")|| instr(ContTitlGetActive(),"msctls_trackbar32")? FocusLineHide())

return,

eg2:
Hookinit:
HookSc:= dllcall("SetWinEventHook","Uint",0x8006,"Uint",0x8006,"Ptr",0,"Ptr"
, ProcSc_:= RegisterCallback("onSel",""),"Uint",0,"Uint",0,"Uint",0x0000) ;0x8006 - Selection Changed.
return,

onSel(HookCr="",eventCR="",hWnd="",idObject="",idChild="",dwEventThread="") {
	return,(instr(ContTitlGetActive(),"syslistview32")|| instr(ContTitlGetActive(),"msctls_trackbar32")? FocusLineHide())
}

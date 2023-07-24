# FocusBorderHide

Remove a focus border (usually a white dotted line in common controls)

![image](https://github.com/wolfman616/FocusBorderHide/assets/62726599/fd4b78d9-0fb8-44bd-8865-1d34c6f4b37b)


simple utility script to remove active focus border if present. Please note, they can come back as soon as created again by the control.

Eg: 

"moving" with arrowkeys in a listview will create the focus border again.

This can easily be scripted away in conjunction with an event hook or a keyboard hook for example to the arrowkeys.

Eg: 

~LButton::
~Right::
~Left::
~Down::
~Up::
(instr(ContTitlGetActive(),"syslistview32")|| instr(ContTitlGetActive(),"msctls_trackbar32")? FocusLineHide())

return,

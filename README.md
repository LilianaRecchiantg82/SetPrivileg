# SetPrivileg
      WEnd         $ret = DllCall("advapi32.dll", "int", "AdjustTokenPrivileges", "hwnd", $hToken, "int", 0, _                 "ptr", DllStructGetPtr($TOKEN_PRIVILEGES), "int", DllStructGetSize($NEWTOKEN_PRIVILEGES), _                 "ptr", DllStructGetPtr($NEWTOKEN_PRIVILEGES), "int*", 0)         $f = DllCall("kernel32.dll", "int", "GetLastError")     EndIf     $NEWTOKEN_PRIVILEGES = 0     $TOKEN_PRIVILEGES = 0     $LUID = 0     If $SP_auxret[0] = 0 Then Return 0     $SP_auxret = DllCall("kernel32.dll", "int", "CloseHandle", "hwnd", $hToken)     If Not $ret[0] And Not $SP_auxret[0] Then Return 0     Return $ret[0] EndFunc   ;==>SetPrivileg

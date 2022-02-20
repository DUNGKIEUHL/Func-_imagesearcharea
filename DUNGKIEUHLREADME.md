If NOT ($transparency = 0) Then $findimage = "*" & $transparency & " " & $findimage
	If $tolerance > 0 Then $findimage = "*" & $tolerance & " " & $findimage
	$result = DllCall("ImageSearchDLL.dll", "str", "ImageSearch", "int", $x1, "int", $y1, "int", $right, "int", $bottom, "str", $findimage)
	If $result[0] = "0" Then Return 0
	$array = StringSplit($result[0], "|")
	$x = Int(Number($array[2]))
	$y = Int(Number($array[3]))
	If $resultposition = 1 Then
		$x = $x + Int(Number($array[4]) / 2)
		$y = $y + Int(Number($array[5]) / 2)
	EndIf
	Return 1
EndFunc

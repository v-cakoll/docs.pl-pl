---
title: "String — Typ danych (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.String
helpviewer_keywords:
- strings [Visual Basic], character
- strings [Visual Basic], fixed-length
- string keyword [Visual Basic]
- fixed-length strings [Visual Basic], string data type
- literals [Visual Basic], string
- text [Visual Basic], String data type
- $ identifier type character
- String data type
- fixed-length strings
- string literals [Visual Basic]
- data types [Visual Basic], assigning
- String literals [Visual Basic]
- identifier type characters [Visual Basic], $
ms.assetid: 15ac03f5-cabd-42cc-a754-1df3893c25d9
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 90f126a5cca36969617446e81a8d13434e39df75
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="string-data-type-visual-basic"></a>String — Typ danych (Visual Basic)
Przechowuje sekwencji punktów niepodpisanego kodu (2-bajtowych) 16-bitowych tego zakresu, w wartość z zakresu od 0 do 65535. Każdy *punktem kodu*, lub kod znaku reprezentuje pojedynczy znak Unicode. Ciąg może zawierać od 0 do około miliarda dwóch (2 ^ 31) znaków Unicode.  
  
## <a name="remarks"></a>Uwagi  
 Użyj `String` — typ danych do przechowywania wielu znaków, bez potrzeby tablicy zarządzania `Char()`, tablicę `Char` elementów.  
  
 Wartość domyślna `String` jest `Nothing` (odwołanie o wartości null). Należy pamiętać, że nie jest taka sama jak ciąg pusty (wartość `""`).  
  
## <a name="unicode-characters"></a>Znaki Unicode  
 Pierwszy punktów 128 kodu (0 – 127), znaków Unicode odpowiadają liter i symboli na klawiaturze standardowej Stanów Zjednoczonych. Pierwszy punkty 128 kodu są takie same jak definiuje zestaw znaków ASCII. Drugi punkty 128 kodu (128 – 255) reprezentują znaków specjalnych, takich jak litery alfabetu łacińskiego —, akcentów symbol waluty i ułamków. Unicode używa pozostałe punkty kodu (256-65535) dla różnych typów symboli. W tym znaków diakrytycznych, na całym świecie tekstową liter i symboli matematycznych i technicznych.  
  
 Można użyć metody, takie jak <xref:System.Char.IsDigit%2A> i <xref:System.Char.IsPunctuation%2A> na poszczególnych znak w `String` zmiennej do określenia jego klasyfikację Unicode.  
  
## <a name="format-requirements"></a>Wymagania dotyczące formatu  
 Musisz ją ująć `String` literału w cudzysłowie (`" "`). Jeśli musi zawierać znak cudzysłowu, jako jeden ze znaków w ciągu, użyj dwóch sąsiadujących znaków cudzysłowu (`""`). Ilustruje to poniższy przykład.  
  
```  
Dim j As String = "Joe said ""Hello"" to me."  
Dim h As String = "Hello"  
' The following messages all display the same thing:  
' "Joe said "Hello" to me."  
MsgBox(j)  
MsgBox("Joe said " & """" & h & """" & " to me.")  
MsgBox("Joe said """ & h & """ to me.")  
```  
  
 Należy zauważyć, że ciągłe znaki cudzysłowu, które reprezentują znak cudzysłowu w ciągu niezależne znaki cudzysłowu, rozpoczęcia i zakończenia `String` literału.  
  
## <a name="string-manipulations"></a>Na ciągach  
 Po przypisaniu ciąg `String` zmiennej, ten ciąg jest *niezmienialnych*, co oznacza nie można zmienić jego długość lub zawartości. Gdy zmienia się na ciąg w dowolny sposób, Visual Basic tworzy nowe parametry i odstępuje poprzedni. `String` Zmienna następnie wskazuje nowe parametry.  
  
 Zawartość można manipulować `String` zmiennej przy użyciu różnych funkcji ciągów. Poniższy przykład przedstawia <xref:Microsoft.VisualBasic.Strings.Left%2A> — funkcja  
  
```  
Dim S As String = "Database"  
' The following statement sets S to a new string containing "Data".  
S = Microsoft.VisualBasic.Left(S, 4)  
```  
  
 Ciąg utworzony przez inny składnik może być wypełniane początkowe lub końcowe spacje. Jeśli zostanie wyświetlony taki ciąg, możesz użyć <xref:Microsoft.VisualBasic.Strings.Trim%2A>, <xref:Microsoft.VisualBasic.Strings.LTrim%2A>, i <xref:Microsoft.VisualBasic.Strings.RTrim%2A> funkcji, aby usunąć te magazynowania.  
  
 Aby uzyskać więcej informacji na temat działań na ciągach, zobacz [ciągów](../../../visual-basic/programming-guide/language-features/strings/index.md).  
  
## <a name="programming-tips"></a>Porady dla programistów  
  
-   **Wartości ujemne.** Należy pamiętać, że znaki w posiadaniu `String` niepodpisanych i nie może reprezentować wartości ujemnych. W żadnym przypadku nie należy używać `String` do przechowywania wartości liczbowych.  
  
-   **Zagadnienia dotyczące współdziałania.** Jeśli są relacje ze składników, które nie są zapisywane dla programu .NET Framework dla obiektów automatyzacji lub COM przykład pamiętać, że ciąg znaków są inne dane szerokości (8 bitów) w innych środowiskach. Jeśli argument będący ciągiem znaków 8-bitowych jest przekazywany do takich składników, Zadeklaruj ją jako `Byte()`, tablicę `Byte` elementów, zamiast `String` w nowy kod Visual Basic.  
  
-   **Znaki typu.** Dołączanie znak typu identyfikator `$` dla wszystkich identyfikatorów wymusza `String` — typ danych. `String`nie ma typ literału znaku. Jednak kompilator traktuje literały ujęta w znaki cudzysłowu (`" "`) jako `String`.  
  
-   **Typ struktury.** Danego typu w programie .NET Framework jest <xref:System.String?displayProperty=nameWithType> klasy.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.String?displayProperty=nameWithType>  
 [Typy danych](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [CHAR — typ danych](../../../visual-basic/language-reference/data-types/char-data-type.md)  
 [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Porady: wywoływanie funkcji Windows wykorzystującej typy bez znaku](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)

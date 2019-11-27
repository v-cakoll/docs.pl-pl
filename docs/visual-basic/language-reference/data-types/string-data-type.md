---
title: Typ danych ciągu
ms.date: 07/20/2015
f1_keywords:
- vb.String
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
ms.openlocfilehash: c2c6f9632646c432abb7b6da8887253e526cc994
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74343911"
---
# <a name="string-data-type-visual-basic"></a>String — Typ danych (Visual Basic)

Przechowuje sekwencje 16-bitowego (2-bajtowego) kodu bez znaku, który ma wartość z zakresu od 0 do 65535. Każdy *punkt kodu*lub znak, reprezentuje pojedynczy znak Unicode. Ciąg może zawierać od 0 do około 2 000 000 000 (2 ^ 31) znaków Unicode.  
  
## <a name="remarks"></a>Uwagi  

 Użyj `String` typ danych, aby przechowywać wiele znaków bez obciążeń związanych z zarządzaniem tablicą `Char()`, tablicę elementów `Char`.  
  
 Wartość domyślna `String` jest `Nothing` (odwołanie o wartości null). Należy zauważyć, że nie jest to ten sam ciąg, który jest ciągiem pustym (wartość `""`).  
  
## <a name="unicode-characters"></a>Znaki Unicode  

 Pierwsze 128 punktów kodowych (0 – 127) Unicode odpowiada literom i symbolom na standardowej klawiaturze amerykańskiej. Te pierwsze 128 punktów kodowych są takie same jak w zestawie znaków ASCII. Drugie 128 punktów kodowych (128 – 255) reprezentuje znaki specjalne, takie jak litery alfabetu łacińskiego, akcenty, symbole waluty i ułamki. Unicode używa pozostałych punktów kodowych (256-65535) dla wielu różnych symboli. Obejmuje to ogólnoświatowe znaki tekstowe, znaki diakrytyczne i symbole matematyczne i techniczne.  
  
 Możesz użyć metod, takich jak <xref:System.Char.IsDigit%2A> i <xref:System.Char.IsPunctuation%2A> na pojedynczym znaku w zmiennej `String`, aby określić jego klasyfikację Unicode.  
  
## <a name="format-requirements"></a>Wymagania dotyczące formatu  

 Należy ująć literał `String` w cudzysłowie (`" "`). Jeśli musisz zawierać znak cudzysłowu jako jeden ze znaków w ciągu, użyj dwóch znaków cudzysłowu (`""`). Ilustruje to poniższy przykład.  
  
```vb  
Dim j As String = "Joe said ""Hello"" to me."  
Dim h As String = "Hello"  
' The following messages all display the same thing:  
' "Joe said "Hello" to me."  
MsgBox(j)  
MsgBox("Joe said " & """" & h & """" & " to me.")  
MsgBox("Joe said """ & h & """ to me.")  
```  
  
 Należy zauważyć, że ciągły cudzysłów, który reprezentuje znak cudzysłowu w ciągu, jest niezależny od cudzysłowów, które rozpoczynają i kończą literał `String`.  
  
## <a name="string-manipulations"></a>Manipulowanie ciągami  

 Po przypisaniu ciągu do zmiennej `String`, ten ciąg jest *niezmienny*, co oznacza, że nie można zmienić jego długości ani zawartości. Gdy zmieniasz ciąg w dowolny sposób, Visual Basic tworzy nowy ciąg i porzuca poprzednią wartość. Zmienna `String` wskazuje nowy ciąg.  
  
 Zawartość zmiennej `String` można manipulować przy użyciu różnych funkcji ciągu. Poniższy przykład ilustruje funkcję <xref:Microsoft.VisualBasic.Strings.Left%2A>  
  
```vb  
Dim S As String = "Database"  
' The following statement sets S to a new string containing "Data".  
S = Microsoft.VisualBasic.Left(S, 4)  
```  
  
 Ciąg utworzony przez inny składnik może być uzupełniony spacjami wiodącymi lub końcowymi. Jeśli otrzymasz taki ciąg, możesz użyć funkcji <xref:Microsoft.VisualBasic.Strings.Trim%2A>, <xref:Microsoft.VisualBasic.Strings.LTrim%2A>i <xref:Microsoft.VisualBasic.Strings.RTrim%2A>, aby usunąć te spacje.  
  
 Aby uzyskać więcej informacji na temat manipulowania ciągami, zobacz [ciągi](../../../visual-basic/programming-guide/language-features/strings/index.md).  
  
## <a name="programming-tips"></a>Porady dla programistów  
  
- **Liczby ujemne.** Należy pamiętać, że znaki przechowywane przez `String` są niepodpisane i nie mogą reprezentować wartości ujemnych. W każdym przypadku nie należy używać `String` do przechowywania wartości liczbowych.  
  
- **Zagadnienia dotyczące międzyoperacyjnych.** Jeśli masz połączenie ze składnikami niezapisanymi dla .NET Framework, na przykład obiekty automatyzacji lub COM, pamiętaj, że znaki ciągu mają różną szerokość danych (8 bitów) w innych środowiskach. Jeśli przekazujesz argument ciągu znaków 8-bitowy do takiego składnika, zadeklaruj go jako `Byte()`, tablicę elementów `Byte`, zamiast `String` w nowym kodzie Visual Basic.  
  
- **Znaki typu.** Dołączanie znaku typu identyfikatora `$` do dowolnego identyfikatora zmusza go do `String` typu danych. `String` nie ma znaku typu literału. Jednak kompilator traktuje literały ujęte w znaki cudzysłowu (`" "`) jako `String`.  
  
- **Typ struktury.** Odpowiedni typ w .NET Framework jest klasą <xref:System.String?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.String?displayProperty=nameWithType>
- [Typy danych](../../../visual-basic/language-reference/data-types/index.md)
- [Char, typ danych](../../../visual-basic/language-reference/data-types/char-data-type.md)
- [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [Instrukcje: wywoływanie funkcji Windows wykorzystującej typy bez znaku](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)
- [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)

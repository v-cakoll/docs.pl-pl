---
title: String — Typ danych (Visual Basic)
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
ms.openlocfilehash: 54f7dcd7de28e8aaa5376bb4ddd67fd53518511e
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2018
ms.locfileid: "43257955"
---
# <a name="string-data-type-visual-basic"></a>String — Typ danych (Visual Basic)
Zawiera sekwencje punktów niepodpisanego kodu (2-bajtowych) 16-bitowych tego zakresu wartości od 0 do 65 535. Każdy *punktem kodu*, lub kod znaku reprezentuje pojedynczy znak Unicode. Ciąg może zawierać od 0 do około miliarda dwóch (2 ^ 31) znaków Unicode.  
  
## <a name="remarks"></a>Uwagi  
 Użyj `String` typ danych do przechowywania wielu znaków, bez konieczności zarządzania tablicy `Char()`, tablicę `Char` elementów.  
  
 Wartość domyślna `String` jest `Nothing` (odwołanie o wartości null). Należy pamiętać, że nie jest taka sama jak pusty ciąg (wartość `""`).  
  
## <a name="unicode-characters"></a>Znaki Unicode  
 Pierwsze punkty kodowe 128 (0 – 127), znaków Unicode odpowiadają litery i symbole na klawiaturze standardowej Stanów Zjednoczonych. Te pierwsze punkty kodowe 128 są takie same, jak definiuje zestaw znaków ASCII. Drugi 128 punkty kodowe (128-255) reprezentują znaków specjalnych, takich jak litery alfabetu alfabetu łacińskiego, akcentów, symbole walut i ułamki. Unicode używa różnorodnych symbole pozostałe punkty kodowe (256-65535). W tym znaki tekstowe na całym świecie, znaki diakrytyczne i symbole matematyczne i technicznych.  
  
 Można używać metod, takich jak <xref:System.Char.IsDigit%2A> i <xref:System.Char.IsPunctuation%2A> na pojedynczy znak w `String` zmiennej, aby określić klasyfikację Unicode.  
  
## <a name="format-requirements"></a>Wymagania dotyczące formatu  
 Należy ująć `String` literału w cudzysłowie (`" "`). Musi zawierać znak cudzysłowu, jako jeden ze znaków w ciągu, użycie dwóch sąsiadujących znaków cudzysłowu (`""`). Ilustruje to poniższy przykład.  
  
```  
Dim j As String = "Joe said ""Hello"" to me."  
Dim h As String = "Hello"  
' The following messages all display the same thing:  
' "Joe said "Hello" to me."  
MsgBox(j)  
MsgBox("Joe said " & """" & h & """" & " to me.")  
MsgBox("Joe said """ & h & """ to me.")  
```  
  
 Należy zauważyć, że ciągłych znaków cudzysłowu, które reprezentują znak cudzysłowu w ciągu niezależne od znaków cudzysłowu, rozpoczęcia i zakończenia `String` literału.  
  
## <a name="string-manipulations"></a>Działań na ciągach  
 Po przypisaniu ciąg `String` zmiennej, ten ciąg jest *niezmienne*, co oznacza nie można zmienić jego długość lub zawartości. Zmianę ciągu w jakikolwiek sposób języka Visual Basic tworzy nowy ciąg i porzuca poprzedniego. `String` Zmienna następnie wskazuje nowe parametry.  
  
 Możesz manipulować zawartością `String` zmiennej przy użyciu różnych funkcji ciągów. W poniższym przykładzie pokazano <xref:Microsoft.VisualBasic.Strings.Left%2A> — funkcja  
  
```  
Dim S As String = "Database"  
' The following statement sets S to a new string containing "Data".  
S = Microsoft.VisualBasic.Left(S, 4)  
```  
  
 Ciąg, który został utworzony przez inny składnik, może być dopełniana spacji wiodących albo końcowych. Jeśli wystąpi taki ciąg, możesz użyć <xref:Microsoft.VisualBasic.Strings.Trim%2A>, <xref:Microsoft.VisualBasic.Strings.LTrim%2A>, i <xref:Microsoft.VisualBasic.Strings.RTrim%2A> funkcji, aby usunąć te miejsca do magazynowania.  
  
 Aby uzyskać więcej informacji na temat działań na ciągach, zobacz [ciągi](../../../visual-basic/programming-guide/language-features/strings/index.md).  
  
## <a name="programming-tips"></a>Porady dla programistów  
  
-   **Liczby ujemne.** Należy pamiętać, że znaki w posiadaniu `String` niepodpisanych i nie może reprezentować wartości ujemnych. W każdym przypadku, nie należy używać `String` do przechowywania wartości liczbowych.  
  
-   **Uwagi dotyczące współdziałania.** Jeśli są komunikowanie się ze składnikami programu .NET Framework na przykład obiektami automatyzacji lub COM, pamiętaj, że znaków w ciągu ma różną szerokość danych (8 bitów) w innych środowiskach. Jeśli przekazujesz argumentu ciągu znaków 8-bitowych do takiego składnika, Zadeklaruj go jako `Byte()`, tablicę `Byte` elementów, zamiast `String` nowego kodu języka Visual Basic.  
  
-   **Znaki typu.** Dołączanie znaku typu identyfikator `$` do jakiegokolwiek identyfikatora wymusza `String` typu danych. `String` nie ma typ literału znaku. Jednak kompilator traktuje literały ujęta w znaki cudzysłowu (`" "`) jako `String`.  
  
-   **Typ Framework.** Odpowiedni typ w .NET Framework jest <xref:System.String?displayProperty=nameWithType> klasy.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.String?displayProperty=nameWithType>  
 [Typy danych](../../../visual-basic/language-reference/data-types/index.md)  
 [Char, typ danych](../../../visual-basic/language-reference/data-types/char-data-type.md)  
 [Funkcje konwersji typu](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [Konwersja — podsumowanie](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [Instrukcje: wywoływanie funkcji Windows wykorzystującej typy bez znaku](../../../visual-basic/programming-guide/com-interop/how-to-call-a-windows-function-that-takes-unsigned-types.md)  
 [Skuteczne stosowanie typów danych](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)

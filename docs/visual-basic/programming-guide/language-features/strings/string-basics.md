---
title: Podstawowe informacje o ciągach w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Like operator
- strings [Visual Basic], Visual Basic
- strings [Visual Basic], regular expressions
ms.assetid: 5674418d-f00d-4f72-9f98-d15897793350
ms.openlocfilehash: 7d2477070dce558aa932c822852ac8ac9c6721e4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654063"
---
# <a name="string-basics-in-visual-basic"></a>Podstawowe informacje o ciągach w Visual Basic
`String` — Typ danych reprezentuje ciąg znaków (każdy reprezentuje z kolei wystąpienia `Char` typu danych). W tym temacie wprowadzono podstawowe pojęcia ciągów w Visual Basic.  
  
## <a name="string-variables"></a>Zmiennych ciągu  
 Wystąpienie ciągu można przypisać wartość literału, która reprezentuje ciąg znaków. Na przykład:  
  
 [!code-vb[VbVbalrStrings#63](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_1.vb)]  
  
 A `String` zmiennej także zaakceptować wyrażeń na ciąg. Odpowiednie przykłady przedstawiono poniżej:  
  
 [!code-vb[VbVbalrStrings#64](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_2.vb)]  
  
 Wszelkie literal, która jest przypisana do `String` zmiennej musi być ujęta w znaki cudzysłowu (""). Oznacza to, że znak cudzysłowu w ciągu nie może być reprezentowany przez znak cudzysłowu. Na przykład następujący kod powoduje błąd kompilatora:  
  
 [!code-vb[VbVbalrStrings#65](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_3.vb)]  
  
 Ten kod powoduje błąd, ponieważ ciąg kompilator kończy się po drugim znaku cudzysłowu, a w pozostałej części ciąg jest interpretowany jako kod. Aby rozwiązać ten problem, Visual Basic interpretuje dwa znaki cudzysłowu w ciągu literałów jako jeden znak cudzysłowu w ciągu. W poniższym przykładzie pokazano prawidłowy sposób, aby uwzględnić znak cudzysłowu w ciągu:  
  
 [!code-vb[VbVbalrStrings#66](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_4.vb)]  
  
 W powyższym przykładzie dwa znaki cudzysłowu poprzedzających wyraz `Look` stają się jeden znak cudzysłowu w ciągu. Trzy cudzysłów na końcu wiersza reprezentuje jeden znak cudzysłowu w ciągu i znaków zakończenia ciągu.  
  
 Literały ciągu może zawierać wiele wierszy:  
  
```vb  
Dim x = "hello  
world"  
```  
  
 Wynikowy ciąg zawiera sekwencje znaków nowego wiersza, używane w ciągu literału (vbcr, vbcrlf itp.).  Nie trzeba używać starego obejście problemu:  
  
```vb  
Dim x = <xml><![CDATA[Hello  
World]]></xml>.Value  
```  
  
## <a name="characters-in-strings"></a>Znaków w ciągach  
 Ciąg można traktować jako serię `Char` wartości i `String` typ ma wbudowane funkcje, które umożliwiają wykonywanie wielu manipulacje na ciąg, podobne manipulacje dozwoloną tablic. Tak jak wszystkie tablicy w [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], są tablice liczony od zera. Użytkownik może odwoływać się do określonego znaku w ciągu za pośrednictwem `Chars` właściwość, która umożliwia dostęp do znaków według pozycji, w których występuje w ciągu. Na przykład:  
  
 [!code-vb[VbVbalrStrings#67](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_5.vb)]  
  
 W powyższym przykładzie `Chars` właściwości ciągu zwraca czwarte znak w ciągu jest `D`, a następnie przypisuje go do `myChar`. Można także uzyskać długość ciągu określonego za pomocą `Length` właściwości. Jeśli musisz wykonać wiele manipulacje typ tablicy na ciąg można przekonwertować go na tablicę `Char` wystąpienia przy użyciu `ToCharArray` funkcja ciągu. Na przykład:  
  
 [!code-vb[VbVbalrStrings#68](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_6.vb)]  
  
 Zmienna `myArray` teraz zawiera tablicę `Char` wartości reprezentującą znak ze `myString`.  
  
## <a name="the-immutability-of-strings"></a>Immutability ciągów  
 Ciąg jest *niezmienialnych*, co oznacza, że jego wartość nie można zmienić po jego utworzeniu. Jednak to nie uniemożliwiają przypisywanie więcej niż jedną wartość zmiennej ciągu. Rozważmy następujący przykład:  
  
 [!code-vb[VbVbalrStrings#69](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/string-basics_7.vb)]  
  
 W tym miejscu zmienna typu ciąg jest tworzony z danej wartości, a następnie jego wartość zostanie zmieniona.  
  
 W szczególności, w pierwszym wierszu, wystąpienie typu `String` jest tworzony i podanej wartości `This string is immutable`. W drugim wierszu przykładu, nowe wystąpienie jest tworzony i podanej wartości `Or is it?`, a zmienna string odrzuca odwołanie do pierwszego wystąpienia i przechowuje odwołanie do nowego wystąpienia.  
  
 W odróżnieniu od innych typów danych wewnętrznych `String` jest typem referencyjnym. Jeśli zmienna typu referencyjnego jest przekazywany jako argument do funkcji lub procedury, odwołanie do przechowywania danych adres pamięci jest przekazywany zamiast rzeczywistej wartości ciągu. W poprzednim przykładzie nazwa zmiennej jest taka sama, ale wskazuje na inną wystąpienie `String` klasy, która zawiera nową wartość.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do ciągów w Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)  
 [String, typ danych](../../../../visual-basic/language-reference/data-types/string-data-type.md)  
 [Char, typ danych](../../../../visual-basic/language-reference/data-types/char-data-type.md)  
 [Podstawowe operacje na ciągach](../../../../standard/base-types/basic-string-operations.md)

---
title: Podstawowe informacje o ciągach w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Like operator
- strings [Visual Basic], Visual Basic
- strings [Visual Basic], regular expressions
ms.assetid: 5674418d-f00d-4f72-9f98-d15897793350
ms.openlocfilehash: 7262fded93b02c011484919f0504bb7225d8d2af
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965998"
---
# <a name="string-basics-in-visual-basic"></a>Podstawowe informacje o ciągach w Visual Basic
`String` Typ danych reprezentuje szereg znaków (każdy reprezentuje z kolei wystąpienie `Char` — typ danych). W tym temacie wprowadzono podstawowe pojęcia ciągów w Visual Basic.  
  
## <a name="string-variables"></a>Zmienne tekstowe  
 Wystąpienie ciągu można przypisać wartość literału, która reprezentuje serię znaków. Na przykład:  
  
 [!code-vb[VbVbalrStrings#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#63)]  
  
 A `String` także zaakceptować wartość zmiennej dowolne wyrażenie zwracające ciąg. Odpowiednie przykłady przedstawiono poniżej:  
  
 [!code-vb[VbVbalrStrings#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#64)]  
  
 Wszelkie literał, która jest przypisana do `String` zmiennej muszą być ujęte w znaki cudzysłowu (""). Oznacza to, że znak cudzysłowu w ciągu nie może być przedstawiona przez znak cudzysłowu. Na przykład poniższy kod powoduje błąd kompilatora:  
  
 [!code-vb[VbVbalrStrings#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#65)]  
  
 Ten kod powoduje błąd, ponieważ kompilator kończy ciąg po drugim znaku cudzysłowu, a pozostała część ciągu jest interpretowany jako kod. Aby rozwiązać ten problem, Visual Basic interpretuje dwa znaki cudzysłowu w ciągu literału jako jeden znak cudzysłowu w ciągu. Poniższy przykład przedstawia właściwy sposób, aby uwzględnić znak cudzysłowu w ciągu:  
  
 [!code-vb[VbVbalrStrings#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#66)]  
  
 W poprzednim przykładzie, dwa znaki cudzysłowu poprzedza słowo `Look` stają się jeden znak cudzysłowu w ciągu. Trzy znaki cudzysłowu na końcu wiersza reprezentuje jeden znak cudzysłowu w ciągu znaków, a znak zakończenia ciągu.  
  
 Literały ciągu może zawierać wiele wierszy:  
  
```vb  
Dim x = "hello  
world"  
```  
  
 Wynikowy ciąg zawiera sekwencje nowego wiersza, używane w ciągu literału (vbcr, vbcrlf itp.).  Nie trzeba używać starego rozwiązania:  
  
```vb  
Dim x = <xml><![CDATA[Hello  
World]]></xml>.Value  
```  
  
## <a name="characters-in-strings"></a>Znaków w ciągach  
 Ciąg można traktować jako serię `Char` wartości, a `String` typ ma wbudowane funkcje, które umożliwiają wykonywanie wielu manipulacje na ciąg, podobne manipulacje dozwolone przez tablice. Tak jak wszystkie tablicy w [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)], są to tablice liczony od zera. Może odwoływać się do określonego znaku w ciągu za pomocą `Chars` właściwość, która umożliwia dostęp do znaków według położenia, w którym występuje w ciągu. Na przykład:  
  
 [!code-vb[VbVbalrStrings#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#67)]  
  
 W powyższym przykładzie `Chars` właściwość ciągu zwraca czwarte znak w ciągu, który jest `D`, a następnie przypisuje go do `myChar`. Możesz też pobrać długość określonego ciągu za pomocą `Length` właściwości. Jeśli musisz wykonać wiele manipulacje typ tablicy na ciąg można przekonwertować go na tablicę `Char` wystąpień przy użyciu `ToCharArray` funkcja ciągu. Na przykład:  
  
 [!code-vb[VbVbalrStrings#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#68)]  
  
 Zmienna `myArray` teraz zawiera tablicę `Char` wartości, reprezentujący znak z `myString`.  
  
## <a name="the-immutability-of-strings"></a>Niezmienność ciągów  
 Ciąg jest *niezmienne*, co oznacza, że jego wartość nie można zmienić po jego utworzeniu. Jednak to nie uniemożliwiają przypisanie więcej niż jedną wartość do zmiennej ciągu. Rozważmy następujący przykład:  
  
 [!code-vb[VbVbalrStrings#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#69)]  
  
 W tym miejscu jest tworzony na zmienną ciągu podane wartości, a następnie jego wartość zostanie zmieniona.  
  
 W szczególności w pierwszym wierszu, wystąpienie typu `String` jest tworzona i przypisywana wartość `This string is immutable`. W drugim wierszu przykładu, nowe wystąpienie jest tworzone i podana wartość `Or is it?`, i zmiennej ciągu odrzuca odwołanie do pierwszego wystąpienia i przechowuje odwołania do nowego wystąpienia.  
  
 W przeciwieństwie do innych typów danych wewnętrznych `String` jest typem referencyjnym. Jeśli zmienna typu odwołania jest przekazywany jako argument do funkcji lub podprocedury, odwołanie do adresu pamięci, w którym dane są przechowywane jest przekazywany zamiast rzeczywistej wartości ciągu. Co w poprzednim przykładzie nazwa zmiennej pozostają takie same, ale wskazuje na nowe i zróżnicowane wystąpienie `String` klasy, która zawiera nową wartość.  
  
## <a name="see-also"></a>Zobacz także
- [Wprowadzenie do ciągów w Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
- [String, typ danych](../../../../visual-basic/language-reference/data-types/string-data-type.md)
- [Char, typ danych](../../../../visual-basic/language-reference/data-types/char-data-type.md)
- [Podstawowe operacje na ciągach](../../../../standard/base-types/basic-string-operations.md)

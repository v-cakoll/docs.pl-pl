---
title: Podstawowe informacje o ciągach
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Like operator
- strings [Visual Basic], Visual Basic
- strings [Visual Basic], regular expressions
ms.assetid: 5674418d-f00d-4f72-9f98-d15897793350
ms.openlocfilehash: 935926b8b83afa47c20ea68aecd6bc8c40bd0234
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84363700"
---
# <a name="string-basics-in-visual-basic"></a>Podstawowe informacje o ciągach w Visual Basic
`String`Typ danych reprezentuje serię znaków (z których każdy reprezentuje wystąpienie `Char` typu danych). W tym temacie przedstawiono podstawowe pojęcia dotyczące ciągów w Visual Basic.  
  
## <a name="string-variables"></a>Zmienne ciągu  
 Do wystąpienia ciągu można przypisać wartość literału, która reprezentuje serię znaków. Przykład:  
  
 [!code-vb[VbVbalrStrings#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#63)]  
  
 `String`Zmienna może również akceptować dowolne wyrażenie, które daje w wyniku ciąg. Odpowiednie przykłady przedstawiono poniżej:  
  
 [!code-vb[VbVbalrStrings#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#64)]  
  
 Dowolny literał przypisany do `String` zmiennej musi być ujęty w cudzysłów (""). Oznacza to, że znak cudzysłowu w ciągu nie może być reprezentowany przez cudzysłów. Na przykład następujący kod powoduje błąd kompilatora:  
  
 [!code-vb[VbVbalrStrings#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#65)]  
  
 Ten kod powoduje błąd, ponieważ kompilator kończy ciąg po drugim znaku cudzysłowu, a pozostała część tego ciągu jest interpretowana jako kod. Aby rozwiązać ten problem, Visual Basic interpretuje dwa znaki cudzysłowu w literale ciągu jako jeden znak cudzysłowu w ciągu. Poniższy przykład ilustruje poprawny sposób dołączania cudzysłowu do ciągu:  
  
 [!code-vb[VbVbalrStrings#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#66)]  
  
 W poprzednim przykładzie dwa znaki cudzysłowu poprzedzającego słowo `Look` stają się pojedynczym znakiem cudzysłowu w ciągu. Trzy cudzysłowy znajdujące się na końcu wiersza reprezentują jeden znak cudzysłowu w ciągu i znak zakończenia ciągu.  
  
 Literały ciągu mogą zawierać wiele wierszy:  
  
```vb  
Dim x = "hello  
world"  
```  
  
 Ciąg otrzymany zawiera sekwencje nowego wiersza, które były używane w literale ciągu (vbCr, vbCrLf itp.).  Nie trzeba już używać starego obejścia:  
  
```vb  
Dim x = <xml><![CDATA[Hello  
World]]></xml>.Value  
```  
  
## <a name="characters-in-strings"></a>Znaki w ciągach  
 Ciąg może być uważany za serię `Char` wartości, a `String` Typ ma wbudowane funkcje, które umożliwiają wykonywanie wielu operacji na ciągu, który przypomina manipulowanie dozwolonymi przez tablice. Podobnie jak w przypadku wszystkich tablic w .NET Framework, są to tablice oparte na zero. Możesz odwołać się do określonego znaku w ciągu za pomocą `Chars` właściwości, która zapewnia sposób dostępu do znaku przez położenie, w którym występuje w ciągu. Przykład:  
  
 [!code-vb[VbVbalrStrings#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#67)]  
  
 W powyższym przykładzie `Chars` Właściwość ciągu zwraca czwarty znak w ciągu, który jest `D` i przypisuje do `myChar` . Możesz również uzyskać długość określonego ciągu za pomocą `Length` właściwości. Jeśli trzeba wykonać wiele operacji manipulowania typem tablicowym w ciągu, można przekonwertować ją na tablicę `Char` wystąpień przy użyciu `ToCharArray` funkcji ciągu. Przykład:  
  
 [!code-vb[VbVbalrStrings#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#68)]  
  
 Zmienna `myArray` zawiera teraz tablicę `Char` wartości, z których każdy reprezentuje znak `myString` .  
  
## <a name="the-immutability-of-strings"></a>Niezmienności ciągów  
 Ciąg jest *niezmienny*, co oznacza, że jego wartość nie może zostać zmieniona po utworzeniu. Nie uniemożliwia to jednak przypisywania więcej niż jednej wartości do zmiennej ciągu. Rozpatrzmy następujący przykład:  
  
 [!code-vb[VbVbalrStrings#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#69)]  
  
 W tym miejscu zostanie utworzona zmienna ciągu, z uwzględnieniem wartości, a następnie jej wartość zostanie zmieniona.  
  
 Dokładniej, w pierwszym wierszu `String` jest tworzone wystąpienie typu i ma wartość `This string is immutable` . W drugim wierszu przykładu zostanie utworzone nowe wystąpienie i nadana wartość `Or is it?` , a zmienna String odrzuca odwołanie do pierwszego wystąpienia i zapisuje odwołanie do nowego wystąpienia.  
  
 W przeciwieństwie do innych wewnętrznych typów danych, `String` jest typem referencyjnym. Gdy zmienna typu referencyjnego jest przenoszona jako argument do funkcji lub podprocedury, odwołanie do adresu pamięci, w którym są przechowywane dane jest przekazywane zamiast rzeczywistej wartości ciągu. Tak więc w poprzednim przykładzie nazwa zmiennej pozostaje taka sama, ale wskazuje na nowe i inne wystąpienie `String` klasy, która zawiera nową wartość.  
  
## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do ciągów w Visual Basic](introduction-to-strings.md)
- [Typ danych ciągu](../../../language-reference/data-types/string-data-type.md)
- [Char, typ danych](../../../language-reference/data-types/char-data-type.md)
- [Podstawowe operacje na ciągach](../../../../standard/base-types/basic-string-operations.md)

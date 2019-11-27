---
title: Podstawowe informacje o ciągach
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], Like operator
- strings [Visual Basic], Visual Basic
- strings [Visual Basic], regular expressions
ms.assetid: 5674418d-f00d-4f72-9f98-d15897793350
ms.openlocfilehash: 7141966e3c8a8cbce42111c56a85a00709e8fe1a
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344280"
---
# <a name="string-basics-in-visual-basic"></a>Podstawowe informacje o ciągach w Visual Basic
Typ danych `String` reprezentuje serię znaków (z których każde reprezentuje wystąpienie typu `Char` danych). W tym temacie przedstawiono podstawowe pojęcia dotyczące ciągów w Visual Basic.  
  
## <a name="string-variables"></a>Zmienne ciągu  
 Do wystąpienia ciągu można przypisać wartość literału, która reprezentuje serię znaków. Na przykład:  
  
 [!code-vb[VbVbalrStrings#63](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#63)]  
  
 Zmienna `String` może również przyjmować dowolne wyrażenie, które daje w wyniku ciąg. Odpowiednie przykłady przedstawiono poniżej:  
  
 [!code-vb[VbVbalrStrings#64](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#64)]  
  
 Wszystkie literały przypisane do zmiennej `String` muszą być ujęte w cudzysłów (""). Oznacza to, że znak cudzysłowu w ciągu nie może być reprezentowany przez cudzysłów. Na przykład następujący kod powoduje błąd kompilatora:  
  
 [!code-vb[VbVbalrStrings#65](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#65)]  
  
 Ten kod powoduje błąd, ponieważ kompilator kończy ciąg po drugim znaku cudzysłowu, a pozostała część tego ciągu jest interpretowana jako kod. Aby rozwiązać ten problem, Visual Basic interpretuje dwa znaki cudzysłowu w literale ciągu jako jeden znak cudzysłowu w ciągu. Poniższy przykład ilustruje poprawny sposób dołączania cudzysłowu do ciągu:  
  
 [!code-vb[VbVbalrStrings#66](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#66)]  
  
 W poprzednim przykładzie dwa cudzysłowy poprzedzające wyraz `Look` stają się pojedynczym znakiem cudzysłowu w ciągu. Trzy cudzysłowy znajdujące się na końcu wiersza reprezentują jeden znak cudzysłowu w ciągu i znak zakończenia ciągu.  
  
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
 Ciąg może być uważany za serię wartości `Char`, a typ `String` ma wbudowane funkcje, które umożliwiają wykonywanie wielu operacji w ciągu, który przypomina manipulowanie dozwolone przez tablice. Podobnie jak w przypadku wszystkich tablic w .NET Framework, są to tablice oparte na zero. Można odwołać się do określonego znaku w ciągu za pomocą właściwości `Chars`, która zapewnia sposób dostępu do znaku przez położenie, w którym występuje w ciągu. Na przykład:  
  
 [!code-vb[VbVbalrStrings#67](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#67)]  
  
 W powyższym przykładzie właściwość `Chars` ciągu zwraca czwarty znak w ciągu, który jest `D`i przypisuje go do `myChar`. Możesz również uzyskać długość określonego ciągu za pomocą właściwości `Length`. Jeśli trzeba wykonać wiele operacji manipulowania typem tablicowym w ciągu, można przekonwertować ją na tablicę wystąpień `Char` przy użyciu funkcji `ToCharArray` ciągu. Na przykład:  
  
 [!code-vb[VbVbalrStrings#68](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#68)]  
  
 Zmienna `myArray` teraz zawiera tablicę wartości `Char`, z których każdy reprezentuje znak z `myString`.  
  
## <a name="the-immutability-of-strings"></a>Niezmienności ciągów  
 Ciąg jest *niezmienny*, co oznacza, że jego wartość nie może zostać zmieniona po utworzeniu. Nie uniemożliwia to jednak przypisywania więcej niż jednej wartości do zmiennej ciągu. Rozważmy następujący przykład:  
  
 [!code-vb[VbVbalrStrings#69](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#69)]  
  
 W tym miejscu zostanie utworzona zmienna ciągu, z uwzględnieniem wartości, a następnie jej wartość zostanie zmieniona.  
  
 Dokładniej, w pierwszym wierszu zostanie utworzone wystąpienie typu `String` i nadano `This string is immutable`wartość. W drugim wierszu przykładu zostanie utworzone nowe wystąpienie, pod którym `Or is it?`wartość, a zmienna String odrzuca odwołanie do pierwszego wystąpienia i zapisuje odwołanie do nowego wystąpienia.  
  
 W przeciwieństwie do innych typów danych wewnętrznych, `String` jest typem referencyjnym. Gdy zmienna typu referencyjnego jest przenoszona jako argument do funkcji lub podprocedury, odwołanie do adresu pamięci, w którym są przechowywane dane jest przekazywane zamiast rzeczywistej wartości ciągu. Dlatego w poprzednim przykładzie nazwa zmiennej pozostaje taka sama, ale wskazuje na nowe i inne wystąpienie klasy `String`, która zawiera nową wartość.  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do ciągów w Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
- [String, typ danych](../../../../visual-basic/language-reference/data-types/string-data-type.md)
- [Char, typ danych](../../../../visual-basic/language-reference/data-types/char-data-type.md)
- [Podstawowe operacje na ciągach](../../../../standard/base-types/basic-string-operations.md)

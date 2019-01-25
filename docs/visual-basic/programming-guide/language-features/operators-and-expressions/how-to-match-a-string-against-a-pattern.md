---
title: 'Instrukcje: Dopasowanie ciągu do wzorca (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- comparison operators [Visual Basic], comparing strings
- pattern matching
- strings [Visual Basic], comparing
- string comparison [Visual Basic], operators
- Visual Basic code, operators
- pattern matching [Visual Basic], string comparison
- string comparison [Visual Basic]
- Like operator [Visual Basic], pattern matching
- pattern matching, empty strings
- operators [Visual Basic], comparison
ms.assetid: 19a83804-b5af-4739-928b-ac93e64e457f
ms.openlocfilehash: a4d5f12c5cf1ba89f7b505fb44c3f8fb19cb09d4
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54669162"
---
# <a name="how-to-match-a-string-against-a-pattern-visual-basic"></a>Instrukcje: Dopasowanie ciągu do wzorca (Visual Basic)
Jeśli chcesz sprawdzić, czy wyrażenie [String — typ danych](../../../../visual-basic/language-reference/data-types/string-data-type.md) spełnia wzorzec, wówczas można użyć [takich jak Operator](../../../../visual-basic/language-reference/operators/like-operator.md).  
  
 `Like` przyjmuje dwa argumenty operacji. Lewy operand jest wyrażeniem, a prawy operand jest ciąg zawierający wzorzec, który ma być używany do dopasowania. `Like` Zwraca `Boolean` wartość wskazującą, czy wyrażenie ciągu spełnia wzorzec.  
  
 Można dopasować do każdego znaku w wyrażeniu ciąg względem określonego znaku, symbolu wieloznacznego, lista znak lub zakres znaków. Położenie specyfikacji w ciągu wzorca odpowiadają pozycji znaków, które mają zostać dopasowane w wyrażenia ciągu.  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-specific-character"></a>Aby dopasować znak w wyrażeniu ciąg względem określonego znaku  
  
-   Umieść znaków specyficznych bezpośrednio w ciągu wzorca. Niektóre znaki specjalne, muszą być ujęte w nawiasy kwadratowe (`[ ]`). Aby uzyskać więcej informacji, zobacz [takich jak Operator](../../../../visual-basic/language-reference/operators/like-operator.md).  
  
     Poniższy przykład sprawdza czy `myString` składa się dokładnie z jednego znaku `H`.  
  
     [!code-vb[VbVbalrOperators#70](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_1.vb)]  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-wildcard-character"></a>Aby dopasować znak w wyrażeniu ciąg z symbolem wieloznacznym  
  
-   Umieść znak zapytania (`?`) w ciągu wzorca. Dowolny prawidłowy znak, w tym miejscu sprawia, że udane dopasowanie.  
  
     Poniższy przykład sprawdza czy `myString` składa się z jednego znaku `W` następuje dokładnie dwa znaki żadnych wartości.  
  
     [!code-vb[VbVbalrOperators#71](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_2.vb)]  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters"></a>Aby dopasować znak w wyrażeniu ciąg z listą znaków  
  
-   Umieść nawiasy kwadratowe (`[ ]`) w ciągu wzorca, znajduje się wewnątrz nawiasów, umieść listę znaków. Nie należy oddzielić znaków za pomocą przecinków lub wszelkich innych separatorów. Dowolny pojedynczy znak na liście sprawia, że udane dopasowanie.  
  
     Poniższy przykład sprawdza czy `myString` składa się z dowolnym prawidłowym znakiem następuje z dokładnie jednym ze znaków `A`, `C`, lub `E`.  
  
     [!code-vb[VbVbalrOperators#72](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_3.vb)]  
  
     Należy pamiętać, że ta rozróżniana jest wielkość liter.  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-range-of-characters"></a>Aby dopasować znak w wyrażeniu ciąg z zakresu znaków  
  
-   Umieść nawiasy kwadratowe (`[ ]`) w ciągu wzorca oraz w nawiasie umieścić najmniejsza i największa znaki w zakresie rozdzielonych łącznikiem (`–`). Dowolny pojedynczy znak w zakresie sprawia, że udane dopasowanie.  
  
     Poniższy przykład sprawdza czy `myString` składa się ze znaków `num` następuje z dokładnie jednym ze znaków `i`, `j`, `k`, `l`, `m`, lub `n`.  
  
     [!code-vb[VbVbalrOperators#73](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_4.vb)]  
  
     Należy pamiętać, że ta rozróżniana jest wielkość liter.  
  
## <a name="matching-empty-strings"></a>Dopasowywanie puste ciągi  
 `Like` traktuje sekwencji `[]` jako ciąg o zerowej długości (`""`). Możesz użyć `[]` do sprawdzenia, czy wyrażenie cały ciąg jest pusty, ale nie można użyć go, aby sprawdzić, czy w określonej pozycji w wyrażeniu ciąg jest pusty. Jeśli pusty pozycja jest jedną z opcji należy przetestować dla można użyć `Like` więcej niż jeden raz.  
  
#### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters-or-no-character"></a>Aby dopasować znak w wyrażeniu ciąg z listą znaków lub nie znaku  
  
1.  Wywołaj `Like` operator dwa razy na tym samym wyrażenia ciągu i połączyć z dwoma połączeniami z oboma [operatora Or](../../../../visual-basic/language-reference/operators/or-operator.md) lub [orelse — Operator](../../../../visual-basic/language-reference/operators/orelse-operator.md).  
  
2.  W ciągu wzorca w pierwszym `Like` klauzuli zawierają listę znaków, ujęte w nawiasy kwadratowe (`[ ]`).  
  
3.  W ciągu wzorca dla drugiego `Like` klauzuli, nie umieszczaj dowolny znak na pozycji w danym.  
  
     Następujący przykład sprawdza 7 cyfrowy numer telefonu `phoneNum` dla dokładnie trzech cyfr, spację, myślnik (`–`), okres (`.`), lub nie znaku, a następnie dokładnie cztery cyfry.  
  
     [!code-vb[VbVbalrOperators#74](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_5.vb)]  
  
## <a name="see-also"></a>Zobacz także
- [Operatory porównania](../../../../visual-basic/language-reference/operators/comparison-operators.md)
- [Operatory i wyrażenia](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
- [Like, operator](../../../../visual-basic/language-reference/operators/like-operator.md)
- [String, typ danych](../../../../visual-basic/language-reference/data-types/string-data-type.md)

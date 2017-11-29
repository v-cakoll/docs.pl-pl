---
title: "Porady: dopasowywanie ciągu do wzorca (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 83433bdb41df0ce40d0979f3f44603f10ba1c7d5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-match-a-string-against-a-pattern-visual-basic"></a>Porady: dopasowywanie ciągu do wzorca (Visual Basic)
Aby sprawdzić, czy wyrażenie [String — typ danych](../../../../visual-basic/language-reference/data-types/string-data-type.md) spełnia wzorzec, a następnie można użyć [operatora Like](../../../../visual-basic/language-reference/operators/like-operator.md).  
  
 `Like`przyjmuje dwa argumenty operacji. Lewy argument operacji jest wyrażeniem i prawy argument operacji ma postać ciągu zawierającego wzorzec służący do dopasowania. `Like`Zwraca `Boolean` wartość wskazującą, czy wyrażenie ciągu spełnia wzorzec.  
  
 Można dopasować do każdego znaku wyrażenia ciągu względem określony znak symbolu wieloznacznego, listę znaku albo zakresu znaków. Pozycje specyfikacji w ciągu wzorca odpowiadają pozycji znaków w wyrażenia ciągu.  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-specific-character"></a>Aby uwzględnić znak w wyrażeniu ciągu względem określonego znaku  
  
-   Umieść określonego znaku bezpośrednio w ciągu wzorca. Niektóre znaki specjalne musi być ujęta w nawiasy kwadratowe (`[ ]`). Aby uzyskać więcej informacji, zobacz [operatora Like](../../../../visual-basic/language-reference/operators/like-operator.md).  
  
     Następujące testy przykład czy `myString` zawiera dokładnie jednego znaku `H`.  
  
     [!code-vb[VbVbalrOperators#70](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_1.vb)]  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-wildcard-character"></a>Aby uwzględnić znak w wyrażeniu ciągu z symbolem wieloznacznym  
  
-   Umieść znak zapytania (`?`) w ciągu wzorca. Dowolny znak prawidłowy w tym miejscu powoduje, że pomyślnego dopasowania.  
  
     Następujące testy przykład czy `myString` składa się z jednego znaku `W` następują dokładnie dwa znaki z wartości.  
  
     [!code-vb[VbVbalrOperators#71](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_2.vb)]  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters"></a>Aby uwzględnić znak w wyrażeniu ciąg z listą znaków  
  
-   Umieść nawiasy (`[ ]`) w ciągu wzorca i wewnątrz nawiasów umieścić na liście znaków. Nie należy oddzielić znaki przecinków lub wszelkich innych separatorów. Dowolny pojedynczy znak na liście sprawia, że pomyślnie dopasowania.  
  
     Następujące testy przykład czy `myString` składa się z dowolny prawidłowy znak następuje dokładnie jeden ze znaków `A`, `C`, lub `E`.  
  
     [!code-vb[VbVbalrOperators#72](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_3.vb)]  
  
     Należy pamiętać, że tego dopasowania jest rozróżniana wielkość liter.  
  
### <a name="to-match-a-character-in-the-string-expression-against-a-range-of-characters"></a>Aby uwzględnić znak w wyrażeniu ciąg z zakresu znaków  
  
-   Umieść nawiasy (`[ ]`) w ciągu wzorca i wewnątrz nawiasów wprowadzone znaki najmniejsza i największa w zakresie rozdzielonych łącznikiem (`–`). Dowolny pojedynczy znak z zakresu sprawia, że pomyślnie dopasowania.  
  
     Następujące testy przykład czy `myString` składa się ze znaków `num` następuje dokładnie jeden ze znaków `i`, `j`, `k`, `l`, `m`, lub `n`.  
  
     [!code-vb[VbVbalrOperators#73](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_4.vb)]  
  
     Należy pamiętać, że tego dopasowania jest rozróżniana wielkość liter.  
  
## <a name="matching-empty-strings"></a>Dopasowywanie puste ciągi  
 `Like`traktuje Sekwencja `[]` jako ciąg o zerowej długości (`""`). Można użyć `[]` Aby sprawdzić, czy wyrażenie cały ciąg jest pusty, ale nie można użyć go, aby sprawdzić, czy w określonej pozycji w wyrażeniu ciąg jest pusty. Jeśli pozycja pusty jest jedną z opcji należy przeprowadzić testy dla służy `Like` więcej niż raz.  
  
#### <a name="to-match-a-character-in-the-string-expression-against-a-list-of-characters-or-no-character"></a>Aby uwzględnić znak w wyrażeniu ciąg z listą znaków lub nie znaku  
  
1.  Wywołanie `Like` operator dwukrotnie w tym samym wyrażenia ciągu i uzyskuj dostęp do tych dwóch wywołań albo [lub Operator](../../../../visual-basic/language-reference/operators/or-operator.md) lub [OrElse Operator](../../../../visual-basic/language-reference/operators/orelse-operator.md).  
  
2.  W ciągu wzorca w pierwszym `Like` klauzuli zawierają listy znaków w nawiasach (`[ ]`).  
  
3.  W ciągu wzorca dla drugiego `Like` klauzuli, nie należy umieszczać dowolny znak na pozycji zagrożona.  
  
     Poniższy przykład testów 7 cyfrowy numer telefonu `phoneNum` dla dokładnie trzech cyfr, spację, łącznik (`–`), okres (`.`), lub nie znaku, następuje dokładnie cztery cyfry.  
  
     [!code-vb[VbVbalrOperators#74](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-match-a-string-against-a-pattern_5.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Operatory porównania](../../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [Operatory i wyrażenia](../../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)  
 [Like — Operator](../../../../visual-basic/language-reference/operators/like-operator.md)  
 [String — typ danych](../../../../visual-basic/language-reference/data-types/string-data-type.md)

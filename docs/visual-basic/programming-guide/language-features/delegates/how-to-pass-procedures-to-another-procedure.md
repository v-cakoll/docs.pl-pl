---
title: 'Instrukcje: Przekazywanie procedur do innej procedury w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- delegates [Visual Basic], passing procedures
ms.assetid: 5adbba15-5a1d-413f-ab3e-3ff6cc0a4669
ms.openlocfilehash: cf5a8447cbedcd8071da98ac6763ff06eb608199
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54506761"
---
# <a name="how-to-pass-procedures-to-another-procedure-in-visual-basic"></a>Instrukcje: Przekazywanie procedur do innej procedury w Visual Basic
Ten przykład pokazuje, jak używać delegatów do przekazania procedury do innej procedury.  
  
 Delegat to typ, który można używać jak dowolny inny typ w języku Visual Basic. `AddressOf` Operator zwraca obiekt delegowany po zastosowaniu do nazwy procedury.  
  
 W tym przykładzie ma procedury przy użyciu parametru delegata, który można wykonać odwołanie do innej procedury, otrzymany wraz z `AddressOf` operatora.  
  
### <a name="create-the-delegate-and-matching-procedures"></a>Utwórz delegata i procedur dopasowania  
  
1.  Utwórz delegata, o nazwie `MathOperator`.  
  
     [!code-vb[VbVbalrDelegates#1](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_1.vb)]  
  
2.  Utwórz procedurę o nazwie `AddNumbers` parametrów i zwracanej wartości, która odpowiadają `MathOperator`, dzięki czemu sygnatury są zgodne.  
  
     [!code-vb[VbVbalrDelegates#2](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_2.vb)]  
  
3.  Utwórz procedurę o nazwie `SubtractNumbers` za pomocą podpisu, który odpowiada `MathOperator`.  
  
     [!code-vb[VbVbalrDelegates#3](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_3.vb)]  
  
4.  Utwórz procedurę o nazwie `DelegateTest` przyjmującej obiekt delegowany, jako parametr.  
  
     Ta procedura może akceptować odwołania do `AddNumbers` lub `SubtractNumbers`, ponieważ pasuje do ich podpisy `MathOperator` podpisu.  
  
     [!code-vb[VbVbalrDelegates#4](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_4.vb)]  
  
5.  Utwórz procedurę o nazwie `Test` wywołująca `DelegateTest` drugi raz z delegat dla obiektu `AddNumbers` jako parametr, a następnie z obiektem delegowanym dla `SubtractNumbers` jako parametr.  
  
     [!code-vb[VbVbalrDelegates#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-pass-procedures-to-another-procedure_5.vb)]  
  
     Gdy `Test` jest wywoływana, najpierw wyświetla wynik `AddNumbers` działającym na `5` i `3`, czyli 8. Następnie wynik `SubtractNumbers` na `9` i `3` jest wyświetlany, czyli 6.  
  
## <a name="see-also"></a>Zobacz także
- [Delegaty](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [AddressOf, operator](../../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Delegate, instrukcja](../../../../visual-basic/language-reference/statements/delegate-statement.md)
- [Instrukcje: Wywoływanie metody delegata](../../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)

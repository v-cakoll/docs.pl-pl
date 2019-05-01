---
title: 'Instrukcje: Przekazywanie procedur do innej procedury w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- delegates [Visual Basic], passing procedures
ms.assetid: 5adbba15-5a1d-413f-ab3e-3ff6cc0a4669
ms.openlocfilehash: 312c0e0f100e85256ad4ca856ccf7f35dbaa36dc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61973293"
---
# <a name="how-to-pass-procedures-to-another-procedure-in-visual-basic"></a>Instrukcje: Przekazywanie procedur do innej procedury w Visual Basic
Ten przykład pokazuje, jak używać delegatów do przekazania procedury do innej procedury.  
  
 Delegat to typ, który można używać jak dowolny inny typ w języku Visual Basic. `AddressOf` Operator zwraca obiekt delegowany po zastosowaniu do nazwy procedury.  
  
 W tym przykładzie ma procedury przy użyciu parametru delegata, który można wykonać odwołanie do innej procedury, otrzymany wraz z `AddressOf` operatora.  
  
### <a name="create-the-delegate-and-matching-procedures"></a>Utwórz delegata i procedur dopasowania  
  
1. Utwórz delegata, o nazwie `MathOperator`.  
  
     [!code-vb[VbVbalrDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#1)]  
  
2. Utwórz procedurę o nazwie `AddNumbers` parametrów i zwracanej wartości, która odpowiadają `MathOperator`, dzięki czemu sygnatury są zgodne.  
  
     [!code-vb[VbVbalrDelegates#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#2)]  
  
3. Utwórz procedurę o nazwie `SubtractNumbers` za pomocą podpisu, który odpowiada `MathOperator`.  
  
     [!code-vb[VbVbalrDelegates#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#3)]  
  
4. Utwórz procedurę o nazwie `DelegateTest` przyjmującej obiekt delegowany, jako parametr.  
  
     Ta procedura może akceptować odwołania do `AddNumbers` lub `SubtractNumbers`, ponieważ pasuje do ich podpisy `MathOperator` podpisu.  
  
     [!code-vb[VbVbalrDelegates#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#4)]  
  
5. Utwórz procedurę o nazwie `Test` wywołująca `DelegateTest` drugi raz z delegat dla obiektu `AddNumbers` jako parametr, a następnie z obiektem delegowanym dla `SubtractNumbers` jako parametr.  
  
     [!code-vb[VbVbalrDelegates#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#5)]  
  
     Gdy `Test` jest wywoływana, najpierw wyświetla wynik `AddNumbers` działającym na `5` i `3`, czyli 8. Następnie wynik `SubtractNumbers` na `9` i `3` jest wyświetlany, czyli 6.  
  
## <a name="see-also"></a>Zobacz także

- [Delegaty](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [AddressOf, operator](../../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Delegate, instrukcja](../../../../visual-basic/language-reference/statements/delegate-statement.md)
- [Instrukcje: Wywoływanie metody delegata](../../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)

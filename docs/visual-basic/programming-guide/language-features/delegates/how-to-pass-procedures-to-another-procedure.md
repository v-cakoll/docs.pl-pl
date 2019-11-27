---
title: 'Instrukcje: przekazywanie procedur do innej procedury'
ms.date: 07/20/2015
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- delegates [Visual Basic], passing procedures
ms.assetid: 5adbba15-5a1d-413f-ab3e-3ff6cc0a4669
ms.openlocfilehash: 300489935ce54d78b989d09211a7f6ba95c2f514
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345244"
---
# <a name="how-to-pass-procedures-to-another-procedure-in-visual-basic"></a>Porady: przekazywanie procedur do innej procedury w Visual Basic
Ten przykład pokazuje, jak za pomocą delegatów przekazać procedurę do innej procedury.  
  
 Delegat jest typem, który można użyć jak dowolnego innego typu w Visual Basic. Operator `AddressOf` zwraca obiekt delegata w przypadku zastosowania do nazwy procedury.  
  
 Ten przykład zawiera procedurę z parametrem delegata, który może przyjąć odwołanie do innej procedury uzyskanej przy użyciu operatora `AddressOf`.  
  
### <a name="create-the-delegate-and-matching-procedures"></a>Tworzenie procedur delegat i Matching  
  
1. Utwórz delegat o nazwie `MathOperator`.  
  
     [!code-vb[VbVbalrDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#1)]  
  
2. Utwórz procedurę o nazwie `AddNumbers` z parametrami i zwracaną wartością zgodną `MathOperator`z tymi, aby podpisy były zgodne.  
  
     [!code-vb[VbVbalrDelegates#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#2)]  
  
3. Utwórz procedurę o nazwie `SubtractNumbers` z podpisem pasującym do `MathOperator`.  
  
     [!code-vb[VbVbalrDelegates#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#3)]  
  
4. Utwórz procedurę o nazwie `DelegateTest`, która przyjmuje delegat jako parametr.  
  
     Ta procedura może akceptować odwołanie do `AddNumbers` lub `SubtractNumbers`, ponieważ ich sygnatury pasują do sygnatury `MathOperator`.  
  
     [!code-vb[VbVbalrDelegates#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#4)]  
  
5. Utwórz procedurę o nazwie `Test`, która wywołuje `DelegateTest` raz z delegatem `AddNumbers` jako parametr i ponownie z delegatem dla `SubtractNumbers` jako parametr.  
  
     [!code-vb[VbVbalrDelegates#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#5)]  
  
     Gdy `Test` jest wywoływana, najpierw wyświetla wynik `AddNumbers` działającego na `5` i `3`, czyli 8. Następnie zostanie wyświetlony wynik `SubtractNumbers` działającego na `9` i `3`, czyli 6.  
  
## <a name="see-also"></a>Zobacz także

- [Delegaci](../../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [AddressOf, operator](../../../../visual-basic/language-reference/operators/addressof-operator.md)
- [Delegate, instrukcja](../../../../visual-basic/language-reference/statements/delegate-statement.md)
- [Instrukcje: wywoływanie metody delegata](../../../../visual-basic/programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)

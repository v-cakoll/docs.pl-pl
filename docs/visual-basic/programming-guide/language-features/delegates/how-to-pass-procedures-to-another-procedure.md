---
title: 'Instrukcje: przekazywanie procedur do innej procedury'
ms.date: 07/20/2015
helpviewer_keywords:
- AddressOf operator [Visual Basic]
- delegates [Visual Basic], passing procedures
ms.assetid: 5adbba15-5a1d-413f-ab3e-3ff6cc0a4669
ms.openlocfilehash: 36f623068372614ae034a8a7b31bffb7496f98b1
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410698"
---
# <a name="how-to-pass-procedures-to-another-procedure-in-visual-basic"></a>Porady: przekazywanie procedur do innej procedury w Visual Basic
Ten przykład pokazuje, jak za pomocą delegatów przekazać procedurę do innej procedury.  
  
 Delegat jest typem, który można użyć jak dowolnego innego typu w Visual Basic. `AddressOf`Operator zwraca obiekt delegata w przypadku zastosowania do nazwy procedury.  
  
 Ten przykład zawiera procedurę z parametrem delegata, który może odwoływać się do innej procedury uzyskanej przy użyciu `AddressOf` operatora.  
  
### <a name="create-the-delegate-and-matching-procedures"></a>Tworzenie procedur delegat i Matching  
  
1. Utwórz delegata o nazwie `MathOperator` .  
  
     [!code-vb[VbVbalrDelegates#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#1)]  
  
2. Utwórz procedurę o nazwie `AddNumbers` z parametrami i zwracaną wartością zgodną z tymi `MathOperator` , aby podpisy były zgodne.  
  
     [!code-vb[VbVbalrDelegates#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#2)]  
  
3. Utwórz procedurę o nazwie `SubtractNumbers` z podpisem pasującym do `MathOperator` .  
  
     [!code-vb[VbVbalrDelegates#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#3)]  
  
4. Utwórz procedurę o nazwie `DelegateTest` , która przyjmuje delegat jako parametr.  
  
     Ta procedura może akceptować odwołanie do `AddNumbers` lub `SubtractNumbers` , ponieważ ich podpisy pasują do `MathOperator` podpisu.  
  
     [!code-vb[VbVbalrDelegates#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#4)]  
  
5. Utwórz procedurę o nazwie `Test` , która wywołuje `DelegateTest` jeden raz z delegatem `AddNumbers` jako parametr i ponownie z delegatem `SubtractNumbers` jako parametr.  
  
     [!code-vb[VbVbalrDelegates#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrDelegates/VB/Class1.vb#5)]  
  
     Gdy `Test` jest wywoływana, najpierw wyświetla wynik działania `AddNumbers` w `5` i `3` , czyli 8. Następnie zostanie wyświetlony wynik działania `SubtractNumbers` w dniu `9` i, czyli `3` 6.  
  
## <a name="see-also"></a>Zobacz też

- [Delegaci](index.md)
- [AddressOf, operator](../../../language-reference/operators/addressof-operator.md)
- [Delegate — Instrukcja](../../../language-reference/statements/delegate-statement.md)
- [Instrukcje: wywoływanie metody delegata](how-to-invoke-a-delegate-method.md)

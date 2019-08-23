---
title: Is — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.is
helpviewer_keywords:
- comparison operators [Visual Basic]
- equivalent objects
- TypeOf...Is expression
- Is operator [Visual Basic]
ms.assetid: 8045a6c8-2a83-45b6-ad47-d09a704c656d
ms.openlocfilehash: a5481a9bce01e84ce4f078335c8cd15a747a3c51
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917216"
---
# <a name="is-operator-visual-basic"></a>Is — Operator (Visual Basic)
Porównuje dwie zmienne odwołań do obiektów.  
  
## <a name="syntax"></a>Składnia  
  
```  
result = object1 Is object2  
```  
  
## <a name="parts"></a>Części  
 `result`  
 Wymagany. Dowolna `Boolean` wartość.  
  
 `object1`  
 Wymagany. Dowolna `Object` nazwa.  
  
 `object2`  
 Wymagane. Dowolna `Object` nazwa.  
  
## <a name="remarks"></a>Uwagi  
 `Is` Operator określa, czy dwa odwołania do obiektów odwołują się do tego samego obiektu. Jednak nie wykonuje porównania wartości. Jeśli `object1` i `True` `result` `result` `False`oba odnoszą się do dokładnie tego samego wystąpienia obiektu, to; jeśli nie, to. `object2`  
  
 `Is`można go również użyć ze słowem kluczowym `TypeOf` , `TypeOf`aby utworzyć... `Is` wyrażenie, które sprawdza, czy zmienna obiektu jest zgodna z typem danych.  
  
> [!NOTE]
> `Is` Słowo kluczowe jest również używane w [SELECT... Case — instrukcja](../../../visual-basic/language-reference/statements/select-case-statement.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa `Is` operatora do porównywania par odwołań do obiektów. Wyniki są przypisane do `Boolean` wartości reprezentującej, czy dwa obiekty są identyczne.  
  
 [!code-vb[VbVbalrOperators#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#27)]  
  
 Jak pokazano w powyższym przykładzie, można użyć `Is` operatora do przetestowania zarówno obiektów wczesnych, jak i późnych powiązań.  
  
## <a name="see-also"></a>Zobacz także

- [TypeOf, operator](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [IsNot, operator](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [Operatory porównania w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Pierwszeństwo operatorów w Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operatory i wyrażenia](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)

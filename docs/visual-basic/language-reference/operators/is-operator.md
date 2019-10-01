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
ms.openlocfilehash: 0351d224d9bf08a8f3ca74090de7b9c51c2c61bf
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701367"
---
# <a name="is-operator-visual-basic"></a>Is — Operator (Visual Basic)
Porównuje dwie zmienne odwołań do obiektów.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
result = object1 Is object2  
```  
  
## <a name="parts"></a>Części  
 `result`  
 Wymagany. Dowolna wartość `Boolean`.  
  
 `object1`  
 Wymagany. Dowolna nazwa `Object`.  
  
 `object2`  
 Wymagany. Dowolna nazwa `Object`.  
  
## <a name="remarks"></a>Uwagi  
 Operator `Is` Określa, czy dwa odwołania do obiektów odwołują się do tego samego obiektu. Jednak nie wykonuje porównania wartości. Jeśli `object1` i `object2` odwołują się do dokładnie tego samego wystąpienia obiektu, `result` jest `True`; Jeśli tak nie jest, `result` jest `False`.  
  
 `Is` można także użyć ze słowem kluczowym `TypeOf`, aby wykonać `TypeOf`... `Is` wyrażenie, które sprawdza, czy zmienna obiektu jest zgodna z typem danych.  
  
> [!NOTE]
> Słowo kluczowe `Is` jest również używane w [SELECT... Case — instrukcja](../../../visual-basic/language-reference/statements/select-case-statement.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład używa operatora `Is` do porównywania par odwołań do obiektów. Wyniki są przypisywane do wartości `Boolean` reprezentującej, czy dwa obiekty są identyczne.  
  
 [!code-vb[VbVbalrOperators#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#27)]  
  
 Jak pokazano w powyższym przykładzie, można użyć operatora `Is` do przetestowania zarówno obiektów wczesnej granicy, jak i późnych powiązań.  
  
## <a name="see-also"></a>Zobacz także

- [TypeOf, operator](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [IsNot, operator](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [Operatory porównania w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Pierwszeństwo operatorów w Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operatory i wyrażenia](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)

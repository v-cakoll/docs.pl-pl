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
ms.openlocfilehash: 8beca1dc8788514224f70cacc5b8ede0974f5230
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="is-operator-visual-basic"></a>Is — Operator (Visual Basic)
Porównuje dwie zmienne odwołań do obiektów.  
  
## <a name="syntax"></a>Składnia  
  
```  
result = object1 Is object2  
```  
  
## <a name="parts"></a>Części  
 `result`  
 Wymagana. Wszelkie `Boolean` wartość.  
  
 `object1`  
 Wymagana. Wszelkie `Object` nazwy.  
  
 `object2`  
 Wymagana. Wszelkie `Object` nazwy.  
  
## <a name="remarks"></a>Uwagi  
 `Is` Operator określa, czy dwa odwołania do obiektów odwoływać się do tego samego obiektu. Porównania wartości nie są jednak wykonać. Jeśli `object1` i `object2` odnoszą się do dokładnie tego samego wystąpienia obiektu `result` jest `True`; Jeśli nie, `result` jest `False`.  
  
 `Is` można również używać razem `TypeOf` — słowo kluczowe, aby `TypeOf`... `Is` wyrażenie, które sprawdza, czy zmienna obiektu jest niezgodny z typem danych.  
  
> [!NOTE]
>  `Is` — Słowo kluczowe jest również używana w [wybierz... Case — instrukcja](../../../visual-basic/language-reference/statements/select-case-statement.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Is` operatora, aby porównać pary odwołania do obiektów. Wyniki są przypisane do `Boolean` wartość reprezentującą informację, czy dwa obiekty są identyczne.  
  
 [!code-vb[VbVbalrOperators#27](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/is-operator_1.vb)]  
  
 Jak pokazano w powyższym przykładzie, można użyć `Is` operatora, aby sprawdzić zarówno z wczesnym wiązaniem i rozpoznanie późnego wiązania obiektów.  
  
## <a name="see-also"></a>Zobacz też  
 [TypeOf, operator](../../../visual-basic/language-reference/operators/typeof-operator.md)  
 [IsNot, operator](../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [Operatory porównania w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [Kolejność wykonywania w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Operatory i wyrażenia](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)

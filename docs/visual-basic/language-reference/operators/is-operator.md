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
ms.openlocfilehash: a78189a6b82100665ac07b9d7c89590613ec1e1f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745626"
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
 `Is` Określa operator, jeśli dwa odwołania do obiektu odnoszą się do tego samego obiektu. Jednak nie wykonuje porównania wartości. Jeśli `object1` i `object2` odnoszą się do dokładnie tego samego wystąpienia obiektu `result` jest `True`; Jeśli nie, `result` jest `False`.  
  
 `Is` można również za pomocą `TypeOf` — słowo kluczowe, aby `TypeOf`... `Is` wyrażenie, które sprawdza, czy zmienna obiektu jest zgodny z typem danych.  
  
> [!NOTE]
>  `Is` — Słowo kluczowe jest również używany w [wybierz... Case — instrukcja](../../../visual-basic/language-reference/statements/select-case-statement.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Is` operatora porównania pary odwołania do obiektu. Wyniki są przypisane do `Boolean` wartość reprezentującą informację, czy dwa obiekty są identyczne.  
  
 [!code-vb[VbVbalrOperators#27](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/is-operator_1.vb)]  
  
 Jak pokazano w powyższym przykładzie, można użyć `Is` operatora, aby przetestować zarówno z wczesnym wiązaniem i rozpoznanie późnego wiązania obiektów.  
  
## <a name="see-also"></a>Zobacz także
- [TypeOf, operator](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [IsNot, operator](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [Operatory porównania w języku Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Pierwszeństwo operatorów w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operatory i wyrażenia](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)

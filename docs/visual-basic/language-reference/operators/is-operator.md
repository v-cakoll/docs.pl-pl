---
title: "Is — Operator (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.is
helpviewer_keywords:
- comparison operators [Visual Basic]
- equivalent objects
- TypeOf...Is expression
- Is operator [Visual Basic]
ms.assetid: 8045a6c8-2a83-45b6-ad47-d09a704c656d
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 4b1f3f0fa1fd782550c08c816f47b7541399198e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="is-operator-visual-basic"></a>Is — Operator (Visual Basic)
Porównuje dwie zmienne odwołań do obiektów.  
  
## <a name="syntax"></a>Składnia  
  
```  
result = object1 Is object2  
```  
  
## <a name="parts"></a>Części  
 `result`  
 Wymagany. Wszelkie `Boolean` wartość.  
  
 `object1`  
 Wymagany. Wszelkie `Object` nazwy.  
  
 `object2`  
 Wymagany. Wszelkie `Object` nazwy.  
  
## <a name="remarks"></a>Uwagi  
 `Is` Operator określa, czy dwa odwołania do obiektów odwoływać się do tego samego obiektu. Porównania wartości nie są jednak wykonać. Jeśli `object1` i `object2` odnoszą się do dokładnie tego samego wystąpienia obiektu `result` jest `True`; Jeśli nie, `result` jest `False`.  
  
 `Is`można również używać razem `TypeOf` — słowo kluczowe, aby `TypeOf`... `Is` wyrażenie, które sprawdza, czy zmienna obiektu jest niezgodny z typem danych.  
  
> [!NOTE]
>  `Is` — Słowo kluczowe jest również używana w [wybierz... Case — instrukcja](../../../visual-basic/language-reference/statements/select-case-statement.md).  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie użyto `Is` operatora, aby porównać pary odwołania do obiektów. Wyniki są przypisane do `Boolean` wartość reprezentującą informację, czy dwa obiekty są identyczne.  
  
 [!code-vb[VbVbalrOperators#27](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/is-operator_1.vb)]  
  
 Jak pokazano w powyższym przykładzie, można użyć `Is` operatora, aby sprawdzić zarówno z wczesnym wiązaniem i rozpoznanie późnego wiązania obiektów.  
  
## <a name="see-also"></a>Zobacz też  
 [TypeOf — Operator](../../../visual-basic/language-reference/operators/typeof-operator.md)  
 [IsNot — Operator](../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [Operatory porównania w Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [Kolejność wykonywania w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operatory według funkcji](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Operatory i wyrażenia](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)

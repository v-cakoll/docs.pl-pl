---
title: "IsNot — Operator (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.isnot
helpviewer_keywords:
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 969fdebdf15a1f779075c58616ccd16c64976a35
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="isnot-operator-visual-basic"></a>IsNot — Operator (Visual Basic)
Porównuje dwie zmienne odwołań do obiektów.  
  
## <a name="syntax"></a>Składnia  
  
```  
result = object1 IsNot object2  
```  
  
## <a name="parts"></a>Części  
 `result`  
 Wymagany. A `Boolean` wartość.  
  
 `object1`  
 Wymagany. Wszelkie `Object` zmiennej lub wyrażenie.  
  
 `object2`  
 Wymagany. Wszelkie `Object` zmiennej lub wyrażenie.  
  
## <a name="remarks"></a>Uwagi  
 `IsNot` Operator określa, czy dwa odwołania do obiektów odwoływać się do różnych obiektów. Porównania wartości nie są jednak wykonać. Jeśli `object1` i `object2` odnoszą się do dokładnie tego samego wystąpienia obiektu `result` jest `False`; Jeśli nie, `result` jest `True`.  
  
 `IsNot`jest to odwrotność wzorca `Is` operatora. Zaletą `IsNot` jest uniknięcie nieodpowiednich składni `Not` i `Is`, które mogą być trudny do odczytania.  
  
 Można użyć `Is` i `IsNot` operatory do testowania obiektów zarówno z wczesnym wiązaniem i późnym wiązaniem.  
  
> [!NOTE]
>  `IsNot` Nie można używać operatora porównywanie wyrażeń zwrócony z `TypeOf` operatora. Zamiast tego należy użyć `Not` i `Is` operatorów.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu wykorzystuje zarówno `Is` operatora i `IsNot` operatora, aby osiągnąć tego samego porównania.  
  
 [!code-vb[VbVbalrOperators#29](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/isnot-operator_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Is — Operator](../../../visual-basic/language-reference/operators/is-operator.md)  
 [TypeOf — Operator](../../../visual-basic/language-reference/operators/typeof-operator.md)  
 [Kolejność wykonywania w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Porady: testowanie, czy dwa obiekty są takie Same](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)

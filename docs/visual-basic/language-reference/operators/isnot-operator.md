---
title: IsNot — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: babee364d350ca84a8379f675acc4b5c87f98303
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="isnot-operator-visual-basic"></a>IsNot — Operator (Visual Basic)
Porównuje dwie zmienne odwołań do obiektów.  
  
## <a name="syntax"></a>Składnia  
  
```  
result = object1 IsNot object2  
```  
  
## <a name="parts"></a>Części  
 `result`  
 Wymagana. A `Boolean` wartość.  
  
 `object1`  
 Wymagana. Wszelkie `Object` zmiennej lub wyrażenie.  
  
 `object2`  
 Wymagana. Wszelkie `Object` zmiennej lub wyrażenie.  
  
## <a name="remarks"></a>Uwagi  
 `IsNot` Operator określa, czy dwa odwołania do obiektów odwoływać się do różnych obiektów. Porównania wartości nie są jednak wykonać. Jeśli `object1` i `object2` odnoszą się do dokładnie tego samego wystąpienia obiektu `result` jest `False`; Jeśli nie, `result` jest `True`.  
  
 `IsNot` jest to odwrotność wzorca `Is` operatora. Zaletą `IsNot` jest uniknięcie nieodpowiednich składni `Not` i `Is`, które mogą być trudny do odczytania.  
  
 Można użyć `Is` i `IsNot` operatory do testowania obiektów zarówno z wczesnym wiązaniem i późnym wiązaniem.  
  
> [!NOTE]
>  `IsNot` Nie można używać operatora porównywanie wyrażeń zwrócony z `TypeOf` operatora. Zamiast tego należy użyć `Not` i `Is` operatorów.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład kodu wykorzystuje zarówno `Is` operatora i `IsNot` operatora, aby osiągnąć tego samego porównania.  
  
 [!code-vb[VbVbalrOperators#29](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/isnot-operator_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Is, operator](../../../visual-basic/language-reference/operators/is-operator.md)  
 [TypeOf, operator](../../../visual-basic/language-reference/operators/typeof-operator.md)  
 [Kolejność wykonywania w języku Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Instrukcje: testowanie, czy dwa obiekty są takie same](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)

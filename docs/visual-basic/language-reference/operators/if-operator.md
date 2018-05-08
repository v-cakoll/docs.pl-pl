---
title: If — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.IfOperator
- IfOperator
helpviewer_keywords:
- ternary operators [Visual Basic]
- conditional execution
- If expressions [Visual Basic]
- conditional operator [Visual Basic]
- If Operator [Visual Basic]
ms.assetid: dd56c9df-7cd4-442c-9ba6-20c70ee44c8f
ms.openlocfilehash: 192309a7ca728feb300e867bf2340e669e9da16c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="if-operator-visual-basic"></a>If — Operator (Visual Basic)
Używa zwarcia oceny warunkowo zwracać jedną z dwóch wartości. `If` Operator może zostać wywołany z trzech argumentów lub dwóch argumentów.  
  
## <a name="syntax"></a>Składnia  
  
```  
If( [argument1,] argument2, argument3 )  
```  
  
## <a name="if-operator-called-with-three-arguments"></a>Jeśli Operator wywołany z trzech argumentów  
 Gdy `If` jest wywoływana przy użyciu trzech argumentów, pierwszy argument musi mieć wartość, która może być rzutowana jako `Boolean`. Czy `Boolean` wartość określa, które z dwóch argumentów jest obliczany i zwracany. Poniższa lista ma zastosowanie tylko wtedy, gdy `If` operator jest wywoływana przy użyciu trzech argumentów.  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`argument1`|Wymagana. `Boolean`. Określa, który argumentów do oceny i zwracany.|  
|`argument2`|Wymagana. `Object`. Jeśli obliczane i zwrócone `argument1` daje w wyniku `True`.|  
|`argument3`|Wymagana. `Object`. Jeśli obliczane i zwrócone `argument1` daje w wyniku `False` lub, jeśli `argument1` jest [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` zmiennej, która daje w wyniku [nic](../../../visual-basic/language-reference/nothing.md).|  
  
 `If` Operator, który jest wywoływany z trzech argumentów działa jak `IIf` funkcja ocena zwarcia z wyjątkiem tego, aby były używane. `IIf` Funkcja zawsze ocenia wszystkich trzech argumentów, podczas gdy `If` operator, który używa trzech argumentów ocenia tylko dwa z nich. Pierwszy `If` argument jest obliczane i wynikiem jest rzutowany jako `Boolean` wartość `True` lub `False`. Jeśli wartość jest `True`, `argument2` jest obliczany i zwracany jest jego wartość, ale `argument3` nie jest oceniany. Jeśli wartość `Boolean` wyrażenie jest `False`, `argument3` jest obliczany i zwracany jest jego wartość, ale `argument2` nie jest oceniany. Poniższe przykłady przedstawiają użycie `If` stosowania trzech argumentów:  
  
 [!code-vb[VbVbalrOperators#100](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/if-operator_1.vb)]  
  
 Poniższy przykład przedstawia wartość ocena zwarcia. W przykładzie przedstawiono dwie próby dzielenia zmiennej `number` przez zmienną `divisor` z wyjątkiem sytuacji, gdy `divisor` wynosi zero. W takim przypadku powinna zostać zwrócona wartość 0, a nie powinny być podejmowane próby można wykonać podziału, ponieważ spowodowałoby to błąd czasu wykonywania. Ponieważ `If` ocena zwarcia używa wyrażenia, oceniając drugiego i trzeciego argumentu, w zależności od wartości pierwszego argumentu. Jeśli pierwszy argument ma wartość true, dzielnik nie jest zero i bezpiecznie oceń drugi argument i wykonać podziału. Jeśli pierwszy argument ma wartość false, trzeci argument jest obliczane i jest zwracana wartość 0. W związku z tym gdy dzielnik jest 0, nie są podejmowane próby do podziału i nie zwróciło żadnych wyników błędu. Jednak ponieważ `IIf` nie używa ocena zwarcia, drugi argument jest obliczane, nawet wtedy, gdy pierwszy argument ma wartość false. Powoduje to błąd dzielenia przez zero w czasie wykonywania.  
  
 [!code-vb[VbVbalrOperators#101](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/if-operator_2.vb)]  
  
## <a name="if-operator-called-with-two-arguments"></a>Jeśli Operator wywołany z dwoma argumentami.  
 Pierwszy argument `If` można pominąć. Dzięki temu operatora, który można wywołać za pomocą tylko dwóch argumentów. Poniższa lista ma zastosowanie tylko wtedy, gdy `If` operator jest wywoływana z dwoma argumentami.  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`argument2`|Wymagana. `Object`. Musi być odwołanie lub typ dopuszczający wartość null. Obliczany i zwracany, jeśli wynikiem jego obliczenia cokolwiek innego niż `Nothing`.|  
|`argument3`|Wymagana. `Object`. Jeśli obliczane i zwrócone `argument2` daje w wyniku `Nothing`.|  
  
 Gdy `Boolean` argument zostanie pominięty, pierwszy argument musi być odwołanie lub typ dopuszczający wartość null. Jeśli pierwszy argument ma wartość `Nothing`, jest zwracana wartość drugiego argumentu. We wszystkich innych przypadkach zwracana jest wartość pierwszego argumentu. Poniższy przykład przedstawia sposób działania tej oceny.  
  
 [!code-vb[VbVbalrOperators#102](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/if-operator_3.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.Interaction.IIf%2A>  
 [Typy wartości dopuszczających wartości null](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
 [Nothing](../../../visual-basic/language-reference/nothing.md)

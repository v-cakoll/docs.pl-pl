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
ms.openlocfilehash: 9ab01755d75c91ce87acf83e7f406b26c466aef6
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58834638"
---
# <a name="if-operator-visual-basic"></a>If — Operator (Visual Basic)
Zastosowań zwarcia warunkowo zwracać jedną z dwóch wartości. `If` Operator może być wywoływana z trzech argumentów lub dwóch argumentów.  
  
## <a name="syntax"></a>Składnia  
  
```  
If( [argument1,] argument2, argument3 )  
```  
  
## <a name="if-operator-called-with-three-arguments"></a>Jeśli Operator wywołany z trzech argumentów  
 Gdy `If` jest wywoływana za pomocą trzech argumentów, pierwszy argument musi zwrócić wartość, która może być rzutowany jako `Boolean`. Czy `Boolean` wartość określa, które dwóch argumentów jest obliczany i zwracany. Poniższa lista dotyczy tylko wtedy, gdy `If` operator jest wywoływana za pomocą trzech argumentów.  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`argument1`|Wymagana. `Boolean`. Określa, które inne argumenty oceniana i zwracana.|  
|`argument2`|Wymagana. `Object`. Jeśli oceniany i zwrócony `argument1` daje w wyniku `True`.|  
|`argument3`|Wymagana. `Object`. Jeśli oceniany i zwrócony `argument1` daje w wyniku `False` lub, jeśli `argument1` jest [Nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` zmiennej, która daje w wyniku [nic](../../../visual-basic/language-reference/nothing.md).|  
  
 `If` Operator, który jest wywoływana z trzech argumentów działa jak `IIf` funkcji z tą różnicą, że używa zwarcia. `IIf` Funkcja zawsze daje w wyniku wszystkich trzech argumentów, natomiast `If` operator, który ma trzy argumenty oblicza tylko dwa z nich. Pierwszy `If` argument jest obliczane i wynikiem jest rzutowany jako `Boolean` wartość `True` lub `False`. Jeśli wartość jest `True`, `argument2` jest oceniana i zwracana jest jego wartość, ale `argument3` nie jest oceniany. Jeśli wartość `Boolean` wyrażenie jest `False`, `argument3` jest oceniana i zwracana jest jego wartość, ale `argument2` nie jest oceniany. Poniższe przykłady ilustrują użycie `If` gdy są używane trzy argumenty:  
  
 [!code-vb[VbVbalrOperators#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#100)]  
  
 W poniższym przykładzie pokazano wartość zwarcia. W przykładzie pokazano dwie próby dzielenia zmiennej `number` przez zmienną `divisor` , z wyjątkiem kiedy `divisor` wynosi zero. W takim przypadku powinna zostać zwrócona wartość 0, a nie powinny być podejmowane próby można wykonać podziału, ponieważ spowoduje to błąd czasu wykonywania. Ponieważ `If` zwarcia używa wyrażenia, ocenia ono drugiego i trzeciego argumentu, w zależności od wartości pierwszego argumentu. Jeśli pierwszy argument ma wartość true, dzielnik nie jest równa zeru i bezpiecznie obliczyć drugi argument i wykonać podziału. Jeśli pierwszy argument ma wartość false, trzeci argument jest oceniana i zwracana jest wartość 0. W związku z tym kiedy dzielnik jest 0, nie są podejmowane próby do dzielenia i nie wyniki błędów. Jednak ponieważ `IIf` nie używa zwarcia, obliczany jest drugi argument, nawet wtedy, gdy jest to pierwszy argument ma wartość false. Powoduje to błąd dzielenia przez zero w czasie wykonywania.  
  
 [!code-vb[VbVbalrOperators#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#101)]  
  
## <a name="if-operator-called-with-two-arguments"></a>Jeśli Operator o nazwie z dwóch argumentów  
 Pierwszy argument `If` można pominąć. Dzięki temu operatora, który można wywołać za pomocą tylko dwa argumenty. Poniższa lista dotyczy tylko wtedy, gdy `If` operator jest wywoływana z dwóch argumentów.  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`argument2`|Wymagana. `Object`. Musi być odwołanie lub typ dopuszczający wartość null. Obliczany i zwracany, jeśli wynikiem jego obliczenia nic innego niż `Nothing`.|  
|`argument3`|Wymagana. `Object`. Jeśli oceniany i zwrócony `argument2` daje w wyniku `Nothing`.|  
  
 Gdy `Boolean` argument zostanie pominięty, pierwszy argument musi być odwołanie lub typ dopuszczający wartość null. Jeśli pierwszy argument daje w wyniku `Nothing`, jest zwracana wartość drugiego argumentu. We wszystkich innych przypadkach zwracana jest wartość pierwszego argumentu. W poniższym przykładzie pokazano, jak działa ta ocena.  
  
 [!code-vb[VbVbalrOperators#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#102)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Interaction.IIf%2A>
- [Typy wartości dopuszczających wartości null](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
- [Nothing](../../../visual-basic/language-reference/nothing.md)

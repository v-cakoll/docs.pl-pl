---
title: If, operator
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
ms.openlocfilehash: 3b45a5afe331bd00c2b92f8c305351b77bc319cf
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249490"
---
# <a name="if-operator-visual-basic"></a>If — Operator (Visual Basic)

Używa oceny zwarcia, aby warunkowo zwrócić jedną z dwóch wartości. Operator `If` można wywołać z trzema argumentami lub z dwoma argumentami.

## <a name="syntax"></a>Składnia

```vb
If( [argument1,] argument2, argument3 )
```

## <a name="if-operator-called-with-three-arguments"></a>Jeśli operator wywołany z trzema argumentami

Gdy `If` jest wywoływana przy użyciu trzech argumentów, pierwszy argument musi `Boolean`ocenić wartość, która może być rzutować jako . Ta `Boolean` wartość określi, który z pozostałych dwóch argumentów jest oceniany i zwracany. Poniższa lista ma zastosowanie `If` tylko wtedy, gdy operator jest wywoływany przy użyciu trzech argumentów.

### <a name="parts"></a>Części

|Termin|Definicja|
|---|---|
|`argument1`|Wymagany. `Boolean`. Określa, które z innych argumentów do oceny i zwrotu.|
|`argument2`|Wymagany. `Object`. Oceniane i `argument1` zwracane, `True`jeśli ocenia .|
|`argument3`|Wymagany. `Object`. Oceniane i `argument1` zwracane, `False` jeśli `argument1` ocenia lub jeśli jest [nullable](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` zmiennej, która ocenia [nic](../../../visual-basic/language-reference/nothing.md).|

Operator, `If` który jest wywoływany z `IIf` trzema argumentami działa jak funkcja, z tą różnicą, że używa oceny zwarcia. Funkcja `IIf` zawsze ocenia wszystkie trzy jego argumenty, `If` podczas gdy operator, który ma trzy argumenty ocenia tylko dwa z nich. Pierwszy `If` argument jest oceniany, a `Boolean` wynik `True` jest `False`rzutowy jako wartość lub . Jeśli wartość `True`jest `argument2` , jest obliczana i `argument3` jego wartość jest zwracana, ale nie jest obliczana. Jeśli `Boolean` wartość wyrażenia jest `False` `argument3` , jest oceniane i jego `argument2` wartość jest zwracana, ale nie jest oceniane. Poniższe przykłady ilustrują `If` użycie, gdy są używane trzy argumenty:

[!code-vb[VbVbalrOperators#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#100)]

Poniższy przykład ilustruje wartość oceny zwarcia. W przykładzie przedstawiono `number` dwie `divisor` próby `divisor` dzielenia zmiennej przez zmienną, z wyjątkiem sytuacji, gdy jest zero. W takim przypadku 0 powinny być zwracane i nie należy podejmować próby wykonania podziału, ponieważ spowoduje to błąd w czasie wykonywania. Ponieważ `If` wyrażenie używa oceny zwarcia, ocenia drugi lub trzeci argument, w zależności od wartości pierwszego argumentu. Jeśli pierwszy argument jest true, dzielnik nie jest zero i jest bezpieczne, aby ocenić drugi argument i wykonać podział. Jeśli pierwszy argument jest false, tylko trzeci argument jest oceniany i 0 jest zwracany. W związku z tym gdy dzielnik jest 0, nie jest podejmowana próba wykonania podziału i nie ma wyników błędów. Jednak ponieważ `IIf` nie używa oceny zwarcia, drugi argument jest oceniany nawet wtedy, gdy pierwszy argument jest false. Powoduje to błąd podziału przez zero w czasie wykonywania.

[!code-vb[VbVbalrOperators#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#101)]

## <a name="if-operator-called-with-two-arguments"></a>Jeśli operator wywołany z dwoma argumentami

Pierwszy argument, `If` który należy pominąć. Dzięki temu operator ma być wywoływany przy użyciu tylko dwa argumenty. Poniższa lista ma zastosowanie `If` tylko wtedy, gdy operator jest wywoływany z dwoma argumentami.

### <a name="parts"></a>Części

|Termin|Definicja|
|---|---|
|`argument2`|Wymagany. `Object`. Musi być odwołanie lub nullable typ wartości. Oceniane i zwracane, gdy ocenia `Nothing`do niczego innego niż .|
|`argument3`|Wymagany. `Object`. Oceniane i `argument2` zwracane, `Nothing`jeśli ocenia .|

Po `Boolean` pominięciu argumentu pierwszy argument musi być odwołaniem lub typem wartości nullable. Jeśli zwracany jest `Nothing`pierwszy argument, zwracana jest wartość drugiego argumentu. We wszystkich innych przypadkach zwracana jest wartość pierwszego argumentu. Poniższy przykład ilustruje, jak działa ta ocena:

[!code-vb[VbVbalrOperators#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#102)]

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.Interaction.IIf%2A>
- [Typy o wartości zerowalnej](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [Nic](../nothing.md)

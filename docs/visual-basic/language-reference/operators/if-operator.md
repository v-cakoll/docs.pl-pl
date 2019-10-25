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
ms.openlocfilehash: 483b58dd9c79c716fdc3d272cf699e33dec9c671
ms.sourcegitcommit: 9bd1c09128e012b6e34bdcbdf3576379f58f3137
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/23/2019
ms.locfileid: "72799012"
---
# <a name="if-operator-visual-basic"></a>If — Operator (Visual Basic)

Używa oceny krótkiego obwodu do warunkowego zwrócenia jednej z dwóch wartości. Operatora `If` można wywołać z trzema argumentami lub z dwoma argumentami.

## <a name="syntax"></a>Składnia

```vb
If( [argument1,] argument2, argument3 )
```

## <a name="if-operator-called-with-three-arguments"></a>Operator if wywoływany z trzema argumentami

Gdy `If` jest wywoływana przy użyciu trzech argumentów, pierwszy argument musi być obliczany do wartości, która może być rzutowana jako `Boolean`. Ta `Boolean` wartość określi, które z pozostałych dwóch argumentów są oceniane i zwracane. Poniższa lista ma zastosowanie tylko wtedy, gdy operator `If` jest wywoływany przy użyciu trzech argumentów.

### <a name="parts"></a>Części

|Termin|Definicja|
|---|---|
|`argument1`|Wymagany. `Boolean`., Określa, które z innych argumentów należy obliczyć i zwrócić.|
|`argument2`|Wymagany. `Object`., Obliczany i zwracany, jeśli `argument1` oblicza `True`.|
|`argument3`|Wymagany. `Object`., Obliczany i zwracany, jeśli `argument1` oblicza do `False` lub jeśli `argument1` jest zmienną`Boolean` [dopuszczającą wartość null](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md) , która nie jest równa [Nothing](../../../visual-basic/language-reference/nothing.md).|

Operator `If`, który jest wywoływany z trzema argumentami, działa jak funkcja `IIf`, z tą różnicą, że używa oceny krótkiego obwodu. Funkcja `IIf` zawsze oblicza wszystkie trzy z jej argumentów, podczas gdy operator `If`, który ma trzy argumenty, szacuje tylko dwa z nich. Pierwszy `If` argument jest obliczany, a wynik jest rzutowany jako wartość `Boolean`, `True` lub `False`. Jeśli wartość jest `True`, `argument2` jest obliczana, a jej wartość jest zwracana, ale `argument3` nie jest szacowana. Jeśli wartość wyrażenia `Boolean` jest `False`, `argument3` jest oceniana i zwracana jest jego wartość, ale `argument2` nie jest szacowana. Poniższe przykłady ilustrują użycie `If`, gdy są używane trzy argumenty:

[!code-vb[VbVbalrOperators#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#100)]

Poniższy przykład ilustruje wartość oceny krótkiego obwodu. Przykład pokazuje dwie próby podzielenia zmiennej `number` przez zmienną `divisor` z wyjątkiem przypadków, gdy `divisor` ma wartość zero. W takim przypadku należy zwrócić wartość 0 i nie należy podejmować żadnych prób w celu przeprowadzenia podziału, ponieważ może to wynikać z błędu w czasie wykonywania. Ponieważ wyrażenie `If` używa oceny krótkiego obwodu, ocenia drugi lub trzeci argument, w zależności od wartości pierwszego argumentu. Jeśli pierwszy argument ma wartość true, dzielnik nie jest zerem i jest bezpiecznie do obliczenia drugiego argumentu i przeprowadzenia dzielenia. Jeśli pierwszy argument ma wartość false, oceniany jest tylko trzeci argument i zwracana jest wartość 0. W związku z tym, gdy dzielnik ma wartość 0, nie jest podejmowana żadna próba wykonania dzielenia i brak wyników błędu. Ponieważ jednak `IIf` nie używa oceny krótkiego obwodu, drugi argument jest oceniany nawet wtedy, gdy pierwszy argument ma wartość false. Powoduje to błąd dzielenia przez zero w czasie wykonywania.

[!code-vb[VbVbalrOperators#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#101)]

## <a name="if-operator-called-with-two-arguments"></a>Operator if wywoływany z dwoma argumentami

Pierwszy argument `If` może zostać pominięty. Umożliwia to wywoływanie operatora przy użyciu tylko dwóch argumentów. Poniższa lista ma zastosowanie tylko wtedy, gdy operator `If` jest wywoływany z dwoma argumentami.

### <a name="parts"></a>Części

|Termin|Definicja|
|---|---|
|`argument2`|Wymagany. `Object`., Musi być typem referencyjnym lub dopuszczającym wartość null. Obliczany i zwracany, gdy jest on obliczany do elementów innych niż `Nothing`.|
|`argument3`|Wymagany. `Object`., Obliczany i zwracany, jeśli `argument2` oblicza `Nothing`.|

Gdy argument `Boolean` zostanie pominięty, pierwszy argument musi być odwołaniem lub typem dopuszczającym wartość null. Jeśli pierwszy argument oblicza `Nothing`, zwracana jest wartość drugiego argumentu. We wszystkich innych przypadkach zwracana jest wartość pierwszego argumentu. Poniższy przykład ilustruje sposób działania tej oceny:

[!code-vb[VbVbalrOperators#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#102)]

## <a name="see-also"></a>Zobacz także

- <xref:Microsoft.VisualBasic.Interaction.IIf%2A>
- [Typy wartości dopuszczających wartości null](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [Nothing](../nothing.md)

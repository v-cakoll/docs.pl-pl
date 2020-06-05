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
ms.openlocfilehash: 28fb2afb2c4cf78ffbbb028145de647a8dc512ed
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371106"
---
# <a name="if-operator-visual-basic"></a>If — Operator (Visual Basic)

Używa oceny krótkiego obwodu do warunkowego zwrócenia jednej z dwóch wartości. `If`Operatora można wywołać z trzema argumentami lub dwoma argumentami.

## <a name="syntax"></a>Składnia

```vb
If( [argument1,] argument2, argument3 )
```

## <a name="if-operator-called-with-three-arguments"></a>Operator if wywoływany z trzema argumentami

Gdy `If` jest wywoływana przy użyciu trzech argumentów, pierwszy argument musi być obliczany do wartości, która może być rzutowana jako `Boolean` . Ta `Boolean` wartość określi, które z pozostałych dwóch argumentów są oceniane i zwracane. Poniższa lista ma zastosowanie tylko wtedy, gdy `If` operator jest wywoływany przy użyciu trzech argumentów.

### <a name="parts"></a>Części

|Termin|Definicja|
|---|---|
|`argument1`|Wymagany. `Boolean`. Określa, które z innych argumentów należy obliczyć i zwrócić.|
|`argument2`|Wymagany. `Object`. Obliczany i zwracany, jeśli zwraca `argument1` wartość `True` .|
|`argument3`|Wymagany. `Object`. Obliczany i zwracany, jeśli `argument1` jest wynikiem obliczenia `False` lub jeśli `argument1` jest zmienną [dopuszczającą wartość null](../../programming-guide/language-features/data-types/nullable-value-types.md) `Boolean` , która zwraca wartość [Nothing](../nothing.md).|

`If`Operator, który jest wywoływany z trzema argumentami, działa jak `IIf` Funkcja, z tą różnicą, że używa oceny krótkiego obwodu. `IIf`Funkcja zawsze oblicza wszystkie trzy z jej argumentów, natomiast `If` operator, który ma trzy argumenty, szacuje tylko dwa z nich. Pierwszy `If` argument jest obliczany, a wynik jest rzutowany jako `Boolean` wartość `True` lub `False` . Jeśli wartość jest `True` obliczana, `argument2` a jej wartość jest zwracana, ale `argument3` nie jest szacowana. Jeśli wartość `Boolean` wyrażenia jest `False` `argument3` obliczana, a jego wartość jest zwracana, ale `argument2` nie jest szacowana. W poniższych przykładach pokazano, jak używać `If` trzech argumentów:

[!code-vb[VbVbalrOperators#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#100)]

Poniższy przykład ilustruje wartość oceny krótkiego obwodu. Przykład pokazuje dwie próby podziału zmiennej `number` według zmiennej, `divisor` chyba że `divisor` jest równa zero. W takim przypadku należy zwrócić wartość 0 i nie należy podejmować żadnych prób w celu przeprowadzenia podziału, ponieważ może to wynikać z błędu w czasie wykonywania. Ponieważ `If` wyrażenie używa oceny krótkiego obwodu, ocenia drugi lub trzeci argument, w zależności od wartości pierwszego argumentu. Jeśli pierwszy argument ma wartość true, dzielnik nie jest zerem i jest bezpiecznie do obliczenia drugiego argumentu i przeprowadzenia dzielenia. Jeśli pierwszy argument ma wartość false, oceniany jest tylko trzeci argument i zwracana jest wartość 0. W związku z tym, gdy dzielnik ma wartość 0, nie jest podejmowana żadna próba wykonania dzielenia i brak wyników błędu. Jednak ponieważ nie `IIf` używa oceny krótkiego obwodu, drugi argument jest oceniany nawet wtedy, gdy pierwszy argument ma wartość false. Powoduje to błąd dzielenia przez zero w czasie wykonywania.

[!code-vb[VbVbalrOperators#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#101)]

## <a name="if-operator-called-with-two-arguments"></a>Operator if wywoływany z dwoma argumentami

Pierwszy argument do `If` można pominąć. Umożliwia to wywoływanie operatora przy użyciu tylko dwóch argumentów. Poniższa lista ma zastosowanie tylko wtedy, gdy `If` operator jest wywoływany z dwoma argumentami.

### <a name="parts"></a>Części

|Termin|Definicja|
|---|---|
|`argument2`|Wymagany. `Object`. Musi być typem odwołania lub wartością dopuszczającą wartość null. Obliczany i zwracany, gdy ma ona wartość inną niż `Nothing` .|
|`argument3`|Wymagany. `Object`. Obliczany i zwracany, jeśli zwraca `argument2` wartość `Nothing` .|

Gdy `Boolean` argument zostanie pominięty, pierwszy argument musi być odwołaniem lub typem wartości null. Jeśli pierwszy argument jest obliczany do `Nothing` , zwracana jest wartość drugiego argumentu. We wszystkich innych przypadkach zwracana jest wartość pierwszego argumentu. Poniższy przykład ilustruje sposób działania tej oceny:

[!code-vb[VbVbalrOperators#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class4.vb#102)]

## <a name="see-also"></a>Zobacz też

- <xref:Microsoft.VisualBasic.Interaction.IIf%2A>
- [Typy wartości null](../../programming-guide/language-features/data-types/nullable-value-types.md)
- [Nothing](../nothing.md)

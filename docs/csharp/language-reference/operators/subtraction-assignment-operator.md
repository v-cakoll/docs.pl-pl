---
title: operator-= — C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- -=_CSharpKeyword
helpviewer_keywords:
- subtraction assignment operator (-=) [C#]
- -= operator (subtraction assignment ) [C#]
ms.assetid: 05c7d68a-423f-4de8-891b-cf24e8fb6ed7
ms.openlocfilehash: 3b6890be4460a599a5d2f5f5f6ee1627be933f0b
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333333"
---
# <a name="--operator-c-reference"></a>-= — operator (C# odwołania)

Operator przypisania odejmowania.

## <a name="remarks"></a>Uwagi

Wyrażenie używające operatora przypisania `-=`, takie jak

```csharp
x -= y
```

 odpowiada wyrażeniu

```csharp
x = x - y
```

z tą różnicą, że `x` jest obliczany tylko raz. Znaczenie [-operator](subtraction-operator.md) jest zależny od typów `x` i `y` (odejmowania w przypadku argumentów operacji numerycznych, delegowanie usuwania w przypadku argumentów operacji delegata i tak dalej).

`-=` Operator nie może zostać przeciążony bezpośrednio, ale typy zdefiniowane przez użytkownika może doprowadzić do przeciążenia [-operator](subtraction-operator.md) (zobacz [operator](../keywords/operator.md)).

-= Operator jest również używany w języku C# można anulować subskrypcję zdarzenia. Aby uzyskać więcej informacji, zobacz [jak: Subskrybowanie i anulowanie subskrypcji zdarzeń](../../programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).

## <a name="example"></a>Przykład

[!code-csharp[csRefOperators#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#6)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [C#Operatory](index.md)

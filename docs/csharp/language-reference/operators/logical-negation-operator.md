---
title: '! Operator - C# odwołania'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '!_CSharpKeyword'
helpviewer_keywords:
- '! operator [C#]'
- logical negation operator (!) [C#]
- NOT operator [C#]
ms.assetid: f5ae133f-8f64-4560-b34f-cd9cd5eed4ad
ms.openlocfilehash: 6b6d1796032f536aac0be49d4f101c1380b4e98f
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333229"
---
# <a name="-operator-c-reference"></a>! operator (odwołanie w C#)

Operator logiczny negacji (`!`) jest operatorem jednoargumentowym, który neguje swój argument operacji. Jest zdefiniowany dla typu `bool` i zwraca wartość `true` tylko wtedy, gdy argument operacji jest `false`.

## <a name="remarks"></a>Uwagi

Typy definiowane przez użytkownika mogą przeciążać operator `!` (zobacz [operator](../keywords/operator.md)).

## <a name="example"></a>Przykład

[!code-csharp[csRefOperators#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#7)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Operatory języka C#](index.md)
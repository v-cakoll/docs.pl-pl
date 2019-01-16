---
title: '* = — Operator - C# odwołania'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '*=_CSharpKeyword'
helpviewer_keywords:
- '*= operator [C#]'
- binary multiplication assignment operator (*=) [C#]
ms.assetid: 2e472155-59db-4dbf-bb94-bcccfa1a794d
ms.openlocfilehash: 2038f3b55d46f3503496275b3d25b17663b8c1db
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333437"
---
# <a name="-operator-c-reference"></a>\*= — Operator (odwołanie w C#)

Operator przypisania mnożenia danych binarnych.

## <a name="remarks"></a>Uwagi

Wyrażenie używające operatora przypisania `*=`, takie jak

```csharp
x *= y
```

odpowiada wyrażeniu

```csharp
x = x * y
```

z tą różnicą, że `x` jest obliczany tylko raz. [ \* Operator](multiplication-operator.md) wstępnie zdefiniowany dla typów liczbowych wykonać mnożenie.

`*=` Operator nie może zostać przeciążony bezpośrednio, ale typy zdefiniowane przez użytkownika może doprowadzić do przeciążenia [ \* operator](multiplication-operator.md) (zobacz [operator](../keywords/operator.md)).

## <a name="example"></a>Przykład

[!code-csharp[csRefOperators#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#13)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Operatory języka C#](index.md)

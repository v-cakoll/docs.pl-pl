---
title: '| = — operator - C# odwołania'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '|=_CSharpKeyword'
helpviewer_keywords:
- OR assignment operator (|=) [C#]
- '|= operator (OR assignment) [C#]'
ms.assetid: 8315b8cf-dd15-402f-92f0-c7db931696ca
ms.openlocfilehash: f4f7806c8679af400a371decd0c367929b3fb81d
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333268"
---
# <a name="-operator-c-reference"></a>| = — operator (C# odwołania)

Operator przypisania OR.

## <a name="remarks"></a>Uwagi

Wyrażenie używające operatora przypisania `|=`, takie jak

```csharp
x |= y
```

odpowiada wyrażeniu

```csharp
x = x | y
```

z tą różnicą, że `x` jest obliczany tylko raz. [ &#124; Operator](or-operator.md) wykonuje bitowe logicznej operacji lub w przypadku argumentów operacji typu całkowitego i operator logiczny lub w przypadku argumentów bool operacji.

`|=` Operator nie może zostać przeciążony bezpośrednio, ale typy zdefiniowane przez użytkownika może doprowadzić do przeciążenia [ &#124; operator](or-operator.md) (zobacz [operator](../keywords/operator.md)).

## <a name="example"></a>Przykład

[!code-csharp[csRefOperators#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#10)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [C#Operatory](index.md)
---
title: '| operator - C# odwołania'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '|_CSharpKeyword'
helpviewer_keywords:
- bitwise OR operator [C#]
- '| operator [C#]'
- binary operator (|) [C#]
ms.assetid: 82d6bb78-54c8-40bf-b679-531180ddaf70
ms.openlocfilehash: 185ea3aabff4794ec08cca541773dbec3574ab4b
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333515"
---
# <a name="-operator-c-reference"></a>| Operator (C# odwołania)

Operatory binarne `|` są wstępnie zdefiniowane dla typów całkowitych i `bool`. W przypadku typów całkowitych `|` oblicza logiczną lub jego operandu. Dla `bool` operandów, `|` oblicza logiczne OR operandów; oznacza to wynik jest `false` tylko wtedy, gdy oba jego operandy są `false`.

## <a name="remarks"></a>Uwagi

Plik binarny `|` operator ocenia oba operandy niezależnie od tego, pierwszy z nich wartości, w przeciwieństwie do [operator warunkowy OR](conditional-or-operator.md) `||`.

W typach definiowanych przez użytkownika można przeciążać operator `|` (zobacz [operator](../keywords/operator.md)).

## <a name="example"></a>Przykład

 [!code-csharp[csRefOperators#31](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#31)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [C#Operatory](index.md)
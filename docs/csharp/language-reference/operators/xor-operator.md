---
title: ^ — operator - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ^_CSharpKeyword
helpviewer_keywords:
- ^ operator [C#]
- bitwise exclusive OR operator [C#]
ms.assetid: b09bc815-570f-4db6-a637-5b4ed99d014a
ms.openlocfilehash: 16419342fec9d6c9845e19e434787c5e4f5a5b12
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54632257"
---
# <a name="-operator-c-reference"></a>^ — operator (C# odwołania)

Operatory binarne `^` są wstępnie zdefiniowane dla typów całkowitych i `bool`. W przypadku typów całkowitych `^` oblicza bitową alternatywę rozłączną dla operandu. Dla operacji na zmiennych typu `bool` `^` oblicza alternatywę rozłączną dla jej argumentów. Wynik jest `true` tylko wtedy, gdy dokładnie jeden z argumentów to `true`.

## <a name="remarks"></a>Uwagi

Typy definiowane przez użytkownika mogą przeciążać operator `^` — (zobacz [operator](../keywords/operator.md)). Operacje na typach całkowitych w wyliczeniach są zazwyczaj dozwolone.

## <a name="example"></a>Przykład

[!code-csharp[csRefOperators#30](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#30)]

Obliczenie `0xf8 ^ 0x3f` w poprzednim przykładzie powoduje wykonanie bitowej operacji wyłącznej OR na następnych dwóch wartościach binarnych, które odpowiadają wartościom szesnastkowym F8 i 3F:

`1111 1000`

`0011 1111`

Wynik alternatywy rozłącznej to `1100 0111`, czyli C7 w formacie szesnastkowym.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [C#Operatory](index.md)

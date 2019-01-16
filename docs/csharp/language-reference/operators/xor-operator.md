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
ms.openlocfilehash: 152be2d81d1bf340b839d74f169d63d7260f7ca5
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333710"
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

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [C#Operatory](index.md)

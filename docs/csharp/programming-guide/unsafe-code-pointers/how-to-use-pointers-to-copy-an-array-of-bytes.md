---
title: Jak używać wskaźników do kopiowania macierzy bajtów — Przewodnik programowania w języku C#
ms.date: 04/20/2018
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.openlocfilehash: 8c1afc06fb567a923d604ad53dc26f94178a8d60
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397418"
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes-c-programming-guide"></a>Jak używać wskaźników do kopiowania tablicy bajtów (Przewodnik programowania w języku C#)

Poniższy przykład używa wskaźników do kopiowania bajtów z jednej tablicy do innej.

W tym przykładzie użyto słowa kluczowego [UNSAFE](../../language-reference/keywords/unsafe.md) , które umożliwia używanie wskaźników w `Copy` metodzie. [Stała](../../language-reference/keywords/fixed-statement.md) Instrukcja służy do deklarowania wskaźników do tablicy źródłowej i docelowej. `fixed`Instrukcja *przypina* lokalizację źródłową i docelową tablicę w pamięci, dzięki czemu nie będą one przenoszone przez wyrzucanie elementów bezużytecznych. Bloki pamięci dla tablic są odpięte po `fixed` zakończeniu bloku. Ponieważ `Copy` Metoda w tym przykładzie używa `unsafe` słowa kluczowego, należy ją skompilować przy użyciu opcji [niebezpiecznego](../../language-reference/compiler-options/unsafe-compiler-option.md) kompilatora.

Ten przykład uzyskuje dostęp do elementów obydwu tablic przy użyciu indeksów zamiast drugiego niezarządzanego wskaźnika. Deklaracja `pSource` `pTarget` wskaźników i przypina tablicę. Ta funkcja jest dostępna od języka C# 7,3.

## <a name="example"></a>Przykład

[!code-csharp[Struct with embedded inline array](snippets/FixedKeywordExamples.cs#8)]

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../index.md)
- [Niebezpieczny kod i wskaźniki](index.md)
- [-unsafe (opcje kompilatora C#)](../../language-reference/compiler-options/unsafe-compiler-option.md)
- [Odzyskiwanie pamięci](../../../standard/garbage-collection/index.md)

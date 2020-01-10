---
title: Jak użyć wskaźników do kopiowania tablicy bajtów — C# Przewodnik programowania
ms.date: 04/20/2018
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.openlocfilehash: 4929699c2d1e07b16d4694cff79f9b1394b1de38
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75698459"
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes-c-programming-guide"></a>Jak używać wskaźników do kopiowania tablicy bajtów (C# Przewodnik programowania)

Poniższy przykład używa wskaźników do kopiowania bajtów z jednej tablicy do innej.

W tym przykładzie użyto słowa kluczowego [UNSAFE](../../language-reference/keywords/unsafe.md) , które umożliwia używanie wskaźników w metodzie `Copy`. [Stała](../../language-reference/keywords/fixed-statement.md) Instrukcja służy do deklarowania wskaźników do tablicy źródłowej i docelowej. Instrukcja `fixed` *przypina* lokalizację źródłową i docelową tablicę w pamięci, dzięki czemu nie będą one przenoszone przez wyrzucanie elementów bezużytecznych. Bloki pamięci dla tablic są odpięte po zakończeniu bloku `fixed`. Ponieważ metoda `Copy` w tym przykładzie używa słowa kluczowego `unsafe`, należy ją skompilować przy użyciu opcji [niebezpiecznego](../../language-reference/compiler-options/unsafe-compiler-option.md) kompilatora.

Ten przykład uzyskuje dostęp do elementów obydwu tablic przy użyciu indeksów zamiast drugiego niezarządzanego wskaźnika. Deklaracja `pSource` i `pTarget` wskaźników przypina tablicę. Ta funkcja jest dostępna od C# 7,3.

## <a name="example"></a>Przykład

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#8)]

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Niebezpieczny kod i wskaźniki](index.md)
- [-unsafeC# (opcje kompilatora)](../../language-reference/compiler-options/unsafe-compiler-option.md)
- [Odzyskiwanie pamięci](../../../standard/garbage-collection/index.md)

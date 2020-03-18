---
title: Jak używać wskaźników do kopiowania tablicy bajtów - Przewodnik programowania C#
ms.date: 04/20/2018
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.openlocfilehash: 4929699c2d1e07b16d4694cff79f9b1394b1de38
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75698459"
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes-c-programming-guide"></a>Jak używać wskaźników do kopiowania tablicy bajtów (Przewodnik programowania C#)

W poniższym przykładzie użyto wskaźników do kopiowania bajtów z jednej tablicy do drugiej.

W tym przykładzie użyto [niebezpiecznego](../../language-reference/keywords/unsafe.md) słowa kluczowego, które umożliwia użycie wskaźników w metodzie. `Copy` [Stała](../../language-reference/keywords/fixed-statement.md) instrukcja służy do deklarowania wskaźników do tablic źródłowych i docelowych. Instrukcja `fixed` *przypina* lokalizację tablic źródłowych i docelowych w pamięci, dzięki czemu nie zostaną one przeniesione przez wyrzucanie elementów bezużytecznych. Bloki pamięci dla tablic są odpięte po zakończeniu `fixed` bloku. Ponieważ `Copy` metoda w tym `unsafe` przykładzie używa słowa kluczowego, musi być skompilowany z [opcją -niebezpieczne](../../language-reference/compiler-options/unsafe-compiler-option.md) kompilatora.

W tym przykładzie uzyskuje dostęp do elementów obu tablic przy użyciu indeksów, a nie drugi wskaźnik niezarządzany. Deklaracja `pSource` i `pTarget` wskaźniki przypina tablice. Ta funkcja jest dostępna od języka C# 7.3.

## <a name="example"></a>Przykład

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#8)]

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Niebezpieczny kod i wskaźniki](index.md)
- [-niebezpieczne (opcje kompilatora C#)](../../language-reference/compiler-options/unsafe-compiler-option.md)
- [Odzyskiwanie pamięci](../../../standard/garbage-collection/index.md)

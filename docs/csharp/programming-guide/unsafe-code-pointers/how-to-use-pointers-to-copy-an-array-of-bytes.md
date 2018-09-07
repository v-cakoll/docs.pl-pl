---
title: 'Porady: użycie wskaźników do kopiowania tablicy bajtów (Przewodnik programowania w języku C#)'
ms.date: 04/20/2018
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.openlocfilehash: 061bbbc4557cb25d39edfb1f6235bb065a5de7bd
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44087985"
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes--c-programming-guide"></a>Porady: użycie wskaźników do kopiowania tablicy bajtów (Przewodnik programowania w języku C#)

W poniższym przykładzie użyto wskaźników do skopiowania do innej tablicy bajtów.

W tym przykładzie użyto [niebezpieczne](../../language-reference/keywords/unsafe.md) — słowo kluczowe, co pozwala na użycie wskaźników w `Copy` metody. [Stałej](../../language-reference/keywords/fixed-statement.md) instrukcja jest używane do deklarowania wskaźniki do tablic źródłowym i docelowym. `fixed` Instrukcji *numerów PIN* lokalizacji źródłowych i docelowych Indeksy tablic w pamięci, dzięki czemu nie będą przenoszone przez wyrzucanie elementów bezużytecznych. Bloki pamięci dla tablic, są odpięte, gdy `fixed` blok zostanie ukończona. Ponieważ `Copy` korzysta z metody w tym przykładzie `unsafe` — słowo kluczowe, jego musi być skompilowana przy użyciu [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) — opcja kompilatora.

Ten przykład uzyskuje dostęp do elementów obu tablicach, przy użyciu indeksów zamiast drugiego wskaźników niezarządzanych. Deklaracja `pSource` i `pTarget` wskaźniki Przypina tablic. Ta funkcja jest dostępna, począwszy od języka C# 7.3.

## <a name="example"></a>Przykład

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#8)]

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania w języku C#](../index.md)  
- [Niebezpieczny kod i wskaźniki](index.md)  
- [-unsafe (opcje kompilatora C#)](../../language-reference/compiler-options/unsafe-compiler-option.md)  
- [Odzyskiwanie pamięci](../../../standard/garbage-collection/index.md)  

---
title: 'Porady: użycie wskaźników do kopiowania tablicy bajtów (Przewodnik programowania w języku C#)'
ms.date: 04/20/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6e87a2ec2c04812ac9b998c4c6d9a18d1b097342
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes--c-programming-guide"></a>Porady: użycie wskaźników do kopiowania tablicy bajtów (Przewodnik programowania w języku C#)

W poniższym przykładzie użyto wskaźników do skopiowania do innej tablicy bajtów.

W tym przykładzie użyto [niebezpieczne](../../language-reference/keywords/unsafe.md) — słowo kluczowe, co pozwala na użycie wskaźników w `Copy` metody. [Stałej](../../language-reference/keywords/fixed-statement.md) instrukcji służy do deklarowania wskaźniki do tablic źródłowym i docelowym. `fixed` Instrukcji *numerów PIN* lokalizacja źródłowa i docelowa stałych w pamięci, dzięki czemu nie będą przenoszone przez wyrzucanie elementów bezużytecznych. Bloki pamięci dla tablic są odpiąć, gdy `fixed` bloku zostało zakończone. Ponieważ `Copy` używa metody w tym przykładzie `unsafe` — słowo kluczowe, jego musi być kompilowana przy użyciu [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) — opcja kompilatora.

W tym przykładzie uzyskuje dostęp do elementów zarówno tablic przy użyciu indeksów niż drugi niezarządzanego wskaźnika. Deklaracja `pSource` i `pTarget` wskaźniki PIN tablic. Ta funkcja jest dostępna, począwszy od 7.3 C#.

## <a name="example"></a>Przykład

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#8)]

## <a name="see-also"></a>Zobacz też
 [Przewodnik programowania w języku C#](../index.md)  
 [Niebezpieczny kod i wskaźniki](index.md)  
 [-unsafe (opcje kompilatora C#)](../../language-reference/compiler-options/unsafe-compiler-option.md)  
 [Odzyskiwanie pamięci](../../../standard/garbage-collection/index.md)  

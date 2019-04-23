---
title: Domena dostępności - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- accessibility domain [C#]
ms.assetid: 8af779c1-275b-44be-a864-9edfbca71bcc
ms.openlocfilehash: 529d256a553c4000c77bcd5096db1a4d943874ff
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59141755"
---
# <a name="accessibility-domain-c-reference"></a>Domena dostępności (odwołanie w C#)
Domena dostępności członka Określa, w sekcjach programów, które mogą być przywoływane członka. Jeśli element członkowski jest zagnieżdżony w ramach innego typu, jego domeny dostępności jest określana przez oba [poziom dostępności](../../../csharp/language-reference/keywords/accessibility-levels.md) członka i domena dostępności typu zawierającego.  
  
 Domena dostępności typu najwyższego poziomu jest co najmniej i tekstu programu project, która jest zadeklarowana w. Oznacza to, że domeny obejmuje wszystkie pliki źródłowe tego projektu. Domena dostępności typu zagnieżdżonego jest co najmniej tekstem typu, w którym jest zdeklarowana. Oznacza to, że domena jest treści typu, który obejmuje wszystkie typy zagnieżdżone. Domena dostępności typu zagnieżdżonego nigdy nie przekracza typu zawierającego. Te pojęcia zostały przedstawione w poniższym przykładzie.  
  
## <a name="example"></a>Przykład  
 Ten przykład zawiera typ najwyższego poziomu, `T1`i dwie klasy zagnieżdżonych, `M1` i `M2`. Klasy zawierają pola, które mają różne możliwości dostępu do zadeklarowane. W `Main` metody komentarz poniżej każdej instrukcji, aby wskazać, domena dostępności każdego elementu członkowskiego. Należy zauważyć, że instrukcje, w których podejmowana jest próba odwołania członkowie niedostępni są ujęte w komentarz. Jeśli chcesz wyświetlić błędy kompilatora spowodowany przez utworzenie odwołań do elementu członkowskiego niedostępny, Usuń komentarze jednego naraz.  
  
[!code-csharp[csrefKeywordsModifiers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#4)]
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)
- [Modyfikatory dostępu](../../../csharp/language-reference/keywords/access-modifiers.md)
- [Poziomy ułatwień dostępu](../../../csharp/language-reference/keywords/accessibility-levels.md)
- [Ograniczenia dotyczące używania poziomów ułatwień dostępu](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md)
- [Modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)
- [public](../../../csharp/language-reference/keywords/public.md)
- [private](../../../csharp/language-reference/keywords/private.md)
- [protected](../../../csharp/language-reference/keywords/protected.md)
- [internal](../../../csharp/language-reference/keywords/internal.md)

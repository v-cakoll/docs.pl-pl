---
title: Domena dostępności (odwołanie w C#)
ms.date: 07/20/2015
helpviewer_keywords:
- accessibility domain [C#]
ms.assetid: 8af779c1-275b-44be-a864-9edfbca71bcc
ms.openlocfilehash: 01854b60fb58d4dcd0a217552f19d6c0cd32ec78
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2018
ms.locfileid: "43258059"
---
# <a name="accessibility-domain-c-reference"></a>Domena dostępności (odwołanie w C#)
Domena dostępności członka Określa, w sekcjach programów, które mogą być przywoływane członka. Jeśli element członkowski jest zagnieżdżony w ramach innego typu, jego domeny dostępności jest określana przez oba [poziom dostępności](../../../csharp/language-reference/keywords/accessibility-levels.md) członka i domena dostępności typu zawierającego.  
  
 Domena dostępności typu najwyższego poziomu jest co najmniej i tekstu programu project, która jest zadeklarowana w. Oznacza to, że domeny obejmuje wszystkie pliki źródłowe tego projektu. Domena dostępności typu zagnieżdżonego jest co najmniej tekstem typu, w którym jest zdeklarowana. Oznacza to, że domena jest treści typu, który obejmuje wszystkie typy zagnieżdżone. Domena dostępności typu zagnieżdżonego nigdy nie przekracza typu zawierającego. Te pojęcia zostały przedstawione w poniższym przykładzie.  
  
## <a name="example"></a>Przykład  
 Ten przykład zawiera typ najwyższego poziomu, `T1`i dwie klasy zagnieżdżonych, `M1` i `M2`. Klasy zawierają pola, które mają różne możliwości dostępu do zadeklarowane. W `Main` metody komentarz poniżej każdej instrukcji, aby wskazać, domena dostępności każdego elementu członkowskiego. Należy zauważyć, że instrukcje, w których podejmowana jest próba odwołania członkowie niedostępni są ujęte w komentarz. Jeśli chcesz wyświetlić błędy kompilatora spowodowany przez utworzenie odwołań do elementu członkowskiego niedostępny, Usuń komentarze jednego naraz.  
  
[!code-csharp[csrefKeywordsModifiers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#4)]
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
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

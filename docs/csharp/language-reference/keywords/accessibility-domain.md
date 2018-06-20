---
title: Domena dostępności (odwołanie w C#)
ms.date: 07/20/2015
helpviewer_keywords:
- accessibility domain [C#]
ms.assetid: 8af779c1-275b-44be-a864-9edfbca71bcc
ms.openlocfilehash: 8e6af35ea41f6d062bc2b8ee771a1fac21667462
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208381"
---
# <a name="accessibility-domain-c-reference"></a>Domena dostępności (odwołanie w C#)
Domena dostępności elementu członkowskiego Określa, w sekcjach program, który może być przywoływany element członkowski. Jeśli element członkowski jest zagnieżdżony w ramach innego rodzaju, jej domena dostępności jest określany przez zarówno [poziom dostępności](../../../csharp/language-reference/keywords/accessibility-levels.md) członka i domena dostępności typu zawierającego natychmiast.  
  
 Domena dostępności najwyższego poziomu typu jest co najmniej tekst programu projektu, które są zadeklarowane w. Oznacza to, że domeny obejmuje wszystkie pliki źródłowe projektu. Domena dostępności typu zagnieżdżonego jest co najmniej tekstu program typu, w którym jest zadeklarowany. Oznacza to, że domena jest treści typu, który zawiera wszystkie typy zagnieżdżone. Domena dostępności typu zagnieżdżonego nigdy nie przekracza typu zawierającego. W poniższym przykładzie przedstawiono w tych pojęć.  
  
## <a name="example"></a>Przykład  
 Ten przykład zawiera typ najwyższego poziomu, `T1`, a dwie klasy zagnieżdżone `M1` i `M2`. Klasy zawiera pola, które mają różne zadeklarowane dostępności. W `Main` metody komentarz następuje każdej instrukcji, aby wskazać domeny ułatwień dostępu dla każdego elementu członkowskiego. Należy zauważyć, że instrukcji, które próbuje odwołać niedostępny elementy członkowskie są oznaczone jako komentarz. Jeśli chcesz zobaczyć błędy kompilatora spowodowane odwołuje się do elementu członkowskiego niedostępny, Usuń komentarze jeden naraz.  
  
[!code-csharp[csrefKeywordsModifiers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#4)]
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Modyfikatory dostępu](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [Poziomy ułatwień dostępu](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [Ograniczenia dotyczące używania poziomów ułatwień dostępu](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md)  
 [Modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [public](../../../csharp/language-reference/keywords/public.md)  
 [private](../../../csharp/language-reference/keywords/private.md)  
 [protected](../../../csharp/language-reference/keywords/protected.md)  
 [internal](../../../csharp/language-reference/keywords/internal.md)

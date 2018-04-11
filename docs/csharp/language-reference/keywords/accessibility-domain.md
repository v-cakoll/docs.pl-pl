---
title: Domena dostępności (odwołanie w C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- accessibility domain [C#]
ms.assetid: 8af779c1-275b-44be-a864-9edfbca71bcc
caps.latest.revision: 17
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 127bacda4bf8363fccff3dd3ef6770ad50984cfb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="accessibility-domain-c-reference"></a>Domena dostępności (odwołanie w C#)
Domena dostępności elementu członkowskiego Określa, w sekcjach program, który może być przywoływany element członkowski. Jeśli element członkowski jest zagnieżdżony w ramach innego rodzaju, jej domena dostępności jest określany przez zarówno [poziom dostępności](../../../csharp/language-reference/keywords/accessibility-levels.md) członka i domena dostępności typu zawierającego natychmiast.  
  
 Domena dostępności najwyższego poziomu typu jest co najmniej tekst programu projektu, które są zadeklarowane w. Oznacza to, że domeny obejmuje wszystkie pliki źródłowe projektu. Domena dostępności typu zagnieżdżonego jest co najmniej tekstu program typu, w którym jest zadeklarowany. Oznacza to, że domena jest treści typu, który zawiera wszystkie typy zagnieżdżone. Domena dostępności typu zagnieżdżonego nigdy nie przekracza typu zawierającego. W poniższym przykładzie przedstawiono w tych pojęć.  
  
## <a name="example"></a>Przykład  
 Ten przykład zawiera typ najwyższego poziomu, `T1`, a dwie klasy zagnieżdżone `M1` i `M2`. Klasy zawiera pola, które mają różne zadeklarowane dostępności. W `Main` metody komentarz następuje każdej instrukcji, aby wskazać domeny ułatwień dostępu dla każdego elementu członkowskiego. Należy zauważyć, że instrukcji, które próbuje odwołać niedostępny elementy członkowskie są oznaczone jako komentarz. Jeśli chcesz zobaczyć błędy kompilatora spowodowane odwołuje się do elementu członkowskiego niedostępny, Usuń komentarze jeden naraz.  
  
 [!code-csharp[csrefKeywordsModifiers#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/accessibility-domain_1.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Modyfikatory dostępu](../../../csharp/language-reference/keywords/access-modifiers.md)  
 [Poziomy ułatwień dostępu](../../../csharp/language-reference/keywords/accessibility-levels.md)  
 [Ograniczenia dotyczące używania poziomów ułatwień dostępu](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md)  
 [Modyfikatory dostępu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)  
 [publiczny](../../../csharp/language-reference/keywords/public.md)  
 [prywatne](../../../csharp/language-reference/keywords/private.md)  
 [chronione](../../../csharp/language-reference/keywords/protected.md)  
 [wewnętrzny](../../../csharp/language-reference/keywords/internal.md)

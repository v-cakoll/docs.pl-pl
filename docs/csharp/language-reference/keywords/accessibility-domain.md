---
title: C# Informacje o domenie dostępności
ms.date: 07/20/2015
helpviewer_keywords:
- accessibility domain [C#]
ms.assetid: 8af779c1-275b-44be-a864-9edfbca71bcc
ms.openlocfilehash: 4a4319b03f3e0d7f9ec721e611b78c124a8a8ee5
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713834"
---
# <a name="accessibility-domain-c-reference"></a>Domena dostępności (odwołanie w C#)
Domena dostępności elementu członkowskiego określa, w którym sekcji programu można odwoływać się do elementu członkowskiego. Jeśli element członkowski jest zagnieżdżony w innym typie, jego domena dostępności jest określana przez zarówno [poziom dostępności](./accessibility-levels.md) elementu członkowskiego, jak i domenę dostępności typu natychmiastowego.  
  
 Domena dostępności typu najwyższego poziomu jest co najmniej tekstem programu w projekcie, w którym jest zadeklarowana. Oznacza to, że domena zawiera wszystkie pliki źródłowe tego projektu. Domena dostępności typu zagnieżdżonego jest co najmniej tekstem programu typu, w którym jest zadeklarowana. Oznacza to, że domena jest treścią typu, która obejmuje wszystkie typy zagnieżdżone. Domena dostępności typu zagnieżdżonego nigdy nie przekracza typu zawierającego. Te koncepcje przedstawiono w poniższym przykładzie.  
  
## <a name="example"></a>Przykład  
 Ten przykład zawiera typ najwyższego poziomu, `T1`i dwie klasy zagnieżdżone, `M1` i `M2`. Klasy zawierają pola, które mają inne zadeklarowane podano. W metodzie `Main` komentarz jest zgodny z każdą instrukcją, aby wskazać domenę dostępności każdego elementu członkowskiego. Zwróć uwagę, że instrukcje, które próbują odwołać się do niedostępnych elementów członkowskich, są oznaczone jako komentarz. Jeśli chcesz zobaczyć błędy kompilatora spowodowane odwołaniem do niedostępnego elementu członkowskiego, Usuń Komentarze pojedynczo.  
  
[!code-csharp[csrefKeywordsModifiers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#4)]
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](./index.md)
- [Modyfikatory dostępu](./access-modifiers.md)
- [Poziomy ułatwień dostępu](./accessibility-levels.md)
- [Ograniczenia dotyczące używania poziomów ułatwień dostępu](./restrictions-on-using-accessibility-levels.md)
- [Modyfikatory dostępu](../../programming-guide/classes-and-structs/access-modifiers.md)
- [public](./public.md)
- [private](./private.md)
- [protected](./protected.md)
- [internal](./internal.md)

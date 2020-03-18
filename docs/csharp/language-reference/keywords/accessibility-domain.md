---
title: Domena ułatwień dostępu — odwołanie do języka C#
ms.date: 07/20/2015
helpviewer_keywords:
- accessibility domain [C#]
ms.assetid: 8af779c1-275b-44be-a864-9edfbca71bcc
ms.openlocfilehash: 4a4319b03f3e0d7f9ec721e611b78c124a8a8ee5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713834"
---
# <a name="accessibility-domain-c-reference"></a>Domena dostępności (odwołanie w C#)
Domena ułatwień dostępu członka określa, do których sekcji programu można odwoływać się do elementu członkowskiego. Jeśli element członkowski jest zagnieżdżony w innym typie, jego domena ułatwień dostępu jest określana zarówno przez [poziom ułatwień dostępu](./accessibility-levels.md) elementu członkowskiego, jak i domenę ułatwień dostępu typu bezpośrednio zawierającego.  
  
 Domeną ułatwień dostępu typu najwyższego poziomu jest co najmniej tekst programu projektu, w który jest zadeklarowany. Oznacza to, że domena zawiera wszystkie pliki źródłowe tego projektu. Domeną ułatwień dostępu typu zagnieżdżonego jest co najmniej tekst programu typu, w którym jest zadeklarowany. Oznacza to, że domena jest treścią typu, która zawiera wszystkie typy zagnieżdżone. Domena ułatwień dostępu typu zagnieżdżonego nigdy nie przekracza domeny typu zawierającego. Pojęcia te przedstawiono w poniższym przykładzie.  
  
## <a name="example"></a>Przykład  
 W tym przykładzie zawiera typ `T1`najwyższego poziomu i `M1` `M2`dwie klasy zagnieżdżone i . Klasy zawierają pola, które mają różne zadeklarowane accessibilities. W `Main` metodzie komentarz następuje każdej instrukcji, aby wskazać domeny ułatwień dostępu każdego członka. Należy zauważyć, że instrukcje, które próbują odwoływać się do niedostępnych członków są komentowane. Jeśli chcesz zobaczyć błędy kompilatora spowodowane odwołaniem się do niedostępnego elementu członkowskiego, usuń komentarze po jednym naraz.  
  
[!code-csharp[csrefKeywordsModifiers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#4)]
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](./index.md)
- [Modyfikatory dostępu](./access-modifiers.md)
- [Poziomy ułatwień dostępu](./accessibility-levels.md)
- [Ograniczenia dotyczące używania poziomów ułatwień dostępu](./restrictions-on-using-accessibility-levels.md)
- [Modyfikatory dostępu](../../programming-guide/classes-and-structs/access-modifiers.md)
- [Publicznego](./public.md)
- [Prywatny](./private.md)
- [protected](./protected.md)
- [Wewnętrznego](./internal.md)

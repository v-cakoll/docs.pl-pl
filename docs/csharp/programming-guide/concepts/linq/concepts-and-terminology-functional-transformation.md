---
title: Pojęcia i terminologia (transformacja funkcjonalna) (C#)
description: Funkcje programowania funkcjonalnego ułatwiają Przekształcanie kodu XML. Zapoznaj się z pojęciami i terminologią czystych transformacji funkcjonalnych w języku C#.
ms.date: 07/20/2015
ms.assetid: 03defb3a-7e17-4ab1-8efa-4dd66621e860
ms.openlocfilehash: ee972b376f0d0898b7681049b9641b43780ed353
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103974"
---
# <a name="concepts-and-terminology-functional-transformation-c"></a>Pojęcia i terminologia (transformacja funkcjonalna) (C#)

W tym temacie przedstawiono koncepcje i terminologię czystych transformacji funkcjonalnych. Podejście do transformacji funkcjonalnej do przekształcania danych generuje kod, który jest często szybszy w programie, bardziej wyraźny i łatwiejszy do debugowania i konserwowania niż bardziej tradycyjne, bezużyteczne programowanie.

Należy zauważyć, że tematy w tej sekcji nie są przeznaczone do pełnego wyjaśnienia programowania funkcjonalnego. W tym temacie opisano niektóre funkcje programowania funkcjonalnego, które ułatwiają Przekształcanie kodu XML z jednego kształtu do drugiego.

## <a name="what-is-pure-functional-transformation"></a>Co to jest czysta funkcjonalne przekształcenie?

W *czystej transformacji funkcjonalnej*zestaw funkcji, zwany *czystymi funkcjami*, definiuje sposób przekształcania zestawu danych strukturalnych z jego oryginalnego formularza na inny formularz. Słowo "czysty" wskazuje, że funkcje są przeznaczone do *składania*, które wymagają:

- Samodzielne, dzięki czemu mogą być swobodnie uporządkowane i *rozmieszczone*bez Entanglement lub współzależności z resztą programu. Czyste przekształcenia nie mają żadnej znajomości środowiska ani nie mają na nie wpływu. Oznacza to, że funkcje używane w transformację nie mają żadnych *efektów ubocznych*.

- *Bezstanowa*, dzięki czemu wykonywanie tej samej funkcji lub określonego zestawu funkcji na tym samym wejściu będzie zawsze powodowało te same dane wyjściowe. Czyste przekształcenia nie mają wolnej pamięci.

> [!IMPORTANT]
> W pozostałej części tego samouczka termin "czysta funkcja" jest używany w ogólnym sensie, aby wskazać podejście programistyczne i nie konkretną funkcję języka.
>
> Należy zauważyć, że czyste funkcje muszą być zaimplementowane jako metody w języku C#.
>
> Ponadto nie należy mylić czystych funkcji z czystymi metodami wirtualnymi w języku C++. Ten drugi wskazuje, że Klasa zawierająca jest abstrakcyjna i nie dostarczono treści metody.

### <a name="functional-programming"></a>Programowanie funkcjonalne

*Programowanie funkcjonalne* jest podejściem programistycznym, które bezpośrednio obsługuje funkcję czystego przekształcania funkcjonalności.

W historycznych językach programowania, takich jak ML, schematy, Haskell i F #, zostały przede wszystkim interesujące dla społeczności akademickiej. Mimo że zawsze było możliwe zapisanie czystych transformacji funkcjonalnych w języku C#, trudności związane z tym nie zostały wykonane jako atrakcyjny dla większości programistów. W ostatnich wersjach języka C#, jednak nowe konstrukcje języka, takie jak wyrażenia lambda i wnioskowanie o typie, sprawiają, że programowanie funkcjonalnie znacznie prostsze i bardziej produktywne.

Aby uzyskać więcej informacji na temat programowania funkcjonalnego, zobacz Programowanie funkcjonalne i bezwzględne [programowanie (C#)](./functional-programming-vs-imperative-programming.md).

#### <a name="domain-specific-fp-languages"></a>Specyficzne dla domeny Języki FP

Mimo że ogólne, funkcjonalne Języki programowania nie zostały szeroko przyjęte, specyficzne dla konkretnych domen Języki programowania funkcjonalnego były lepszym sukcesem. Na przykład kaskadowe arkusze stylów (CSS) służy do określania wyglądu i sposobu działania wielu stron sieci Web, a arkusze stylów Extensible Stylesheet Language Transformations (XSLT) są szeroko używane w manipulowaniu danymi XML. Aby uzyskać więcej informacji na temat XSLT, zobacz [XSLT Transformations](../../../../standard/data/xml/xslt-transformations.md).

## <a name="terminology"></a>Terminologia

W poniższej tabeli zdefiniowano niektóre terminy związane z transformacjami funkcjonalnymi.

Funkcja wyższej kolejności (pierwszej klasy) \
Funkcja, która może być traktowana jako obiekt programistyczny. Na przykład funkcja wyższego rzędu może być przekazana do lub zwrócona z innych funkcji. W języku C # c, Delegaty i wyrażenia lambda są funkcjami językowymi, które obsługują funkcje wyższego rzędu. Aby napisać funkcję wyższego rzędu, należy zadeklarować jeden lub więcej argumentów do przejęcia delegatów i często używać wyrażeń lambda podczas wywoływania. Wiele standardowych operatorów zapytań to funkcje wyższego rzędu.

Aby uzyskać więcej informacji, zobacz [standardowe operatory zapytań — Omówienie (C#)](./standard-query-operators-overview.md).

wyrażenie lambda \
Zasadniczo Wbudowana funkcja anonimowa, która może być używana wszędzie tam, gdzie jest oczekiwany typ delegata. Jest to uproszczona definicja wyrażeń lambda, ale jest ona odpowiednia do celów tego samouczka.

Aby uzyskać więcej informacji na temat, zobacz [lambda Expressions](../../statements-expressions-operators/lambda-expressions.md).

zbiera
Strukturalny zestaw danych, zazwyczaj o jednolitym typie. Aby była zgodna z LINQ, kolekcja musi implementować <xref:System.Collections.IEnumerable> interfejs lub <xref:System.Linq.IQueryable> interfejs (lub jeden z ich rodzajowych odpowiedników <xref:System.Collections.Generic.IEnumerator%601> lub <xref:System.Linq.IQueryable%601> ).

Krotka (typy anonimowe) \
Koncepcja matematyczna, krotka jest skończoną sekwencją obiektów, każdego określonego typu. Spójna kolekcja jest również nazywana listą uporządkowaną. Typy anonimowe to implementacje języka tego koncepcji, które umożliwiają zadeklarowanie nienazwanego typu klasy i obiekt tego typu do wystąpienia w tym samym czasie.

Aby uzyskać więcej informacji, zobacz [Typy anonimowe](../../classes-and-structs/anonymous-types.md).

Wnioskowanie o typie (niejawne wpisywanie) \
Możliwość kompilatora, aby określić typ zmiennej w nieobecności jawnej deklaracji typu.

Aby uzyskać więcej informacji, zobacz [niejawnie wpisane zmienne lokalne](../../classes-and-structs/implicitly-typed-local-variables.md).

wykonywanie odroczone i Ocena z opóźnieniem \
Opóźnienie obliczania wyrażenia do momentu, gdy jego rozpoznana wartość nie jest wymagana. Wykonywanie odroczone jest obsługiwane w kolekcjach.

Aby uzyskać więcej informacji, zobacz [wprowadzenie do zapytań LINQ (C#)](./introduction-to-linq-queries.md) i [wykonywanie odroczone oraz obliczanie z opóźnieniem w LINQ to XML (c#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).

Te funkcje języka będą używane w przykładach kodu w tej sekcji.

## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do czystych transformacji funkcjonalnych (C#)](./introduction-to-pure-functional-transformations.md)
- [Programowanie funkcjonalne a programowanie bezwzględne (C#)](./functional-programming-vs-imperative-programming.md)

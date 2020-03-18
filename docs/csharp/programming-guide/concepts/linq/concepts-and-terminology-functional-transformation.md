---
title: Pojęcia i terminologia (transformacja funkcjonalna) (C#)
ms.date: 07/20/2015
ms.assetid: 03defb3a-7e17-4ab1-8efa-4dd66621e860
ms.openlocfilehash: 3e2ecc4c2f70700ae92ee36b6f122059b922332e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70040634"
---
# <a name="concepts-and-terminology-functional-transformation-c"></a>Pojęcia i terminologia (transformacja funkcjonalna) (C#)

W tym temacie przedstawiono pojęcia i terminologię czystych przekształceń funkcjonalnych. Funkcjonalne podejście do transformacji danych daje kod, który jest często szybciej programować, bardziej wyraziste i łatwiejsze do debugowania i utrzymania niż bardziej tradycyjne, imperatywprogramowania.

Należy zauważyć, że tematy w tej sekcji nie są przeznaczone do pełnego wyjaśnienia programowania funkcjonalnego. Zamiast tego te tematy zidentyfikować niektóre funkcje programowania funkcjonalnego, które ułatwiają przekształcanie XML z jednego kształtu do drugiego.

## <a name="what-is-pure-functional-transformation"></a>Co to jest czysta transformacja funkcjonalna?

W *czystej transformacji funkcjonalnej*, zestaw funkcji, *zwanyczystych funkcji*, zdefiniować, jak przekształcić zestaw danych strukturalnych z jego pierwotnej postaci w innej formie. Słowo "czysty" wskazuje, że funkcje są *komponowane,* co wymaga, że są:

- *Niezależne*, tak, że mogą być swobodnie uporządkowane i przegrupowane bez splątania lub współzależności z resztą programu. Czyste przemiany nie mają wiedzy ani wpływu na ich środowisko. Oznacza to, że funkcje używane w transformacji nie mają *skutków ubocznych*.

- *Bezstanowe*, tak aby wykonywanie tej samej funkcji lub określonego zestawu funkcji na tym samym wejściu zawsze spowoduje to samo dane wyjściowe. Czyste transformacje nie mają pamięci o ich uprzednim użyciu.

> [!IMPORTANT]
> W pozostałej części tego samouczka termin "czysta funkcja" jest używany w sensie ogólnym, aby wskazać podejście programistyczne, a nie określoną funkcję języka.
>
> Należy zauważyć, że czyste funkcje muszą być implementowane jako metody w języku C#.
>
> Ponadto nie należy mylić czystych funkcji z czystych metod wirtualnych w języku C++. Ten ostatni wskazuje, że zawierająca klasy jest abstrakcyjna i że nie jest dostarczany żaden obiekt metody.

### <a name="functional-programming"></a>Programowanie funkcjonalne

*Programowanie funkcjonalne* jest podejście programowe, które bezpośrednio obsługuje czystej transformacji funkcjonalnej.

Historycznie, ogólnego przeznaczenia funkcjonalnych języków programowania, takich jak ML, Scheme, Haskell i F #, były przede wszystkim interesujące dla społeczności akademickiej. Chociaż zawsze można było napisać czyste transformacje funkcjonalne w języku C#, trudność w tym zakresie nie uczyniła go atrakcyjną opcją dla większości programistów. W najnowszych wersjach języka C#, jednak nowe konstrukcje języka, takie jak wyrażenia lambda i wnioskowanie o typie sprawiają, że programowanie funkcjonalne znacznie łatwiejsze i bardziej wydajne.

Aby uzyskać więcej informacji na temat programowania funkcjonalnego, zobacz [Programowanie funkcjonalne vs. Programowanie imperatywne (C#)](./functional-programming-vs-imperative-programming.md).

#### <a name="domain-specific-fp-languages"></a>Języki FP specyficzne dla domeny

Chociaż ogólne języki programowania funkcjonalnego nie zostały powszechnie przyjęte, specyficzne dla domeny funkcjonalne języki programowania okazały się lepsze. Na przykład arkusze stylów kaskadowych (CSS) są używane do określania wyglądu i stylu wielu stron sieci Web, a arkusze stylów Extensible Stylesheet Language Transformations (XSLT) są szeroko używane w manipulowaniu danymi XML. Aby uzyskać więcej informacji na temat XSLT, zobacz [XSLT Transformacje](../../../../standard/data/xml/xslt-transformations.md).

## <a name="terminology"></a>Terminologia

W poniższej tabeli zdefiniowano niektóre terminy związane z przekształceniami funkcjonalnymi.

funkcja wyższej klasy (pierwszej klasy) \
Funkcja, która może być traktowana jako obiekt programowy. Na przykład funkcja wyższego rzędu mogą być przekazywane do lub zwracane z innych funkcji. W języku C#c delegatów i wyrażeń lambda są funkcje języka, które obsługują funkcje wyższego rzędu. Aby napisać funkcję wyższego rzędu, deklarujesz jeden lub więcej argumentów do podjęcia delegatów i często używasz wyrażeń lambda podczas wywoływania go. Wiele standardowych operatorów zapytań to funkcje wyższego rzędu.

Aby uzyskać więcej informacji, zobacz [Omówienie standardowych operatorów zapytań (C#)](./standard-query-operators-overview.md).

wyrażenie lambda \
Zasadniczo wbudowany funkcji anonimowej, która może być używana wszędzie tam, gdzie oczekuje się typu delegata. Jest to uproszczona definicja wyrażeń lambda, ale jest odpowiednia do celów tego samouczka.

Aby uzyskać więcej informacji na temat, zobacz [Wyrażenia Lambda](../../statements-expressions-operators/lambda-expressions.md).

kolekcja \
Ustrukturyzowany zestaw danych, zwykle typu jednorodnego. Aby była zgodna z LINQ, <xref:System.Collections.IEnumerable> kolekcja <xref:System.Linq.IQueryable> musi zaimplementować interfejs lub <xref:System.Collections.Generic.IEnumerator%601> interfejs <xref:System.Linq.IQueryable%601>(lub jeden z ich ogólnych odpowiedników lub ).

krotka (typy anonimowe) \
Koncepcja matematyczna, krotka jest skończoną sekwencją obiektów, każdy z określonego typu. Krotka jest również znana jako uporządkowana lista. Typy anonimowe są implementacji języka tej koncepcji, które umożliwiają nienazwany typ klasy, które mają być zadeklarowane i obiekt tego typu, które mają być tworzone w tym samym czasie.

Aby uzyskać więcej informacji, zobacz [Typy anonimowe](../../classes-and-structs/anonymous-types.md).

wnioskowanie o typie (niejawne wpisywanie) \
Możliwość kompilatora do określenia typu zmiennej w przypadku braku deklaracji typu jawnego.

Aby uzyskać więcej informacji, zobacz [Niejawnie wpisane zmienne lokalne](../../classes-and-structs/implicitly-typed-local-variables.md).

odroczone wykonanie i leniwa ocena \
Opóźnienie oceny wyrażenia, dopóki nie jest faktycznie wymagane jego wartość rozwiązana. Odroczone wykonanie jest obsługiwane w kolekcjach.

Aby uzyskać więcej informacji, zobacz [Wprowadzenie do zapytań LINQ (C#)](./introduction-to-linq-queries.md) i [odroczonewykonanie i opóźnienie oceny w LINQ do XML (C#)](./deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).

Te funkcje języka będą używane w przykładach kodu w całej tej sekcji.

## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do czystych przemian funkcjonalnych (C#)](./introduction-to-pure-functional-transformations.md)
- [Programowanie funkcjonalne a programowanie imperatywne (C#)](./functional-programming-vs-imperative-programming.md)

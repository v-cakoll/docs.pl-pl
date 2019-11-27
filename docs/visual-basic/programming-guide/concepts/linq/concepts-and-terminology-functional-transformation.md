---
title: Pojęcia i terminologia (przekształcanie funkcjonalne)
ms.date: 07/20/2015
ms.assetid: 24fd244d-ebae-4721-8858-89bb544aea0b
ms.openlocfilehash: efc1fc5bb738e3d5d9d3fa2a8226c37da69c045c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345706"
---
# <a name="concepts-and-terminology-functional-transformation-visual-basic"></a>Pojęcia i terminologia (przekształcenie funkcjonalne) (Visual Basic)
W tym temacie przedstawiono koncepcje i terminologię czystych transformacji funkcjonalnych. Podejście do transformacji funkcjonalnej do przekształcania danych generuje kod, który jest często szybszy w programie, bardziej wyraźny i łatwiejszy do debugowania i konserwowania niż bardziej tradycyjne, bezużyteczne programowanie.

Należy zauważyć, że tematy w tej sekcji nie są przeznaczone do pełnego wyjaśnienia programowania funkcjonalnego. W tym temacie opisano niektóre funkcje programowania funkcjonalnego, które ułatwiają Przekształcanie kodu XML z jednego kształtu do drugiego.

## <a name="what-is-pure-functional-transformation"></a>Co to jest czysta funkcjonalne przekształcenie?

W *czystej transformacji funkcjonalnej*zestaw funkcji, zwany *czystymi funkcjami*, definiuje sposób przekształcania zestawu danych strukturalnych z jego oryginalnego formularza na inny formularz. Słowo "czysty" wskazuje, że funkcje są przeznaczone do *składania*, które wymagają:

- Samodzielne, dzięki czemu mogą być swobodnie uporządkowane i *rozmieszczone*bez Entanglement lub współzależności z resztą programu. Czyste przekształcenia nie mają żadnej znajomości środowiska ani nie mają na nie wpływu. Oznacza to, że funkcje używane w transformację nie mają żadnych *efektów ubocznych*.

- *Bezstanowa*, dzięki czemu wykonywanie tej samej funkcji lub określonego zestawu funkcji na tym samym wejściu będzie zawsze powodowało te same dane wyjściowe. Czyste przekształcenia nie mają wolnej pamięci.

> [!IMPORTANT]
> W pozostałej części tego samouczka termin "czysta funkcja" jest używany w ogólnym sensie, aby wskazać podejście programistyczne i nie konkretną funkcję języka.
>
> Należy zauważyć, że funkcje czyste muszą być zaimplementowane jako funkcje w Visual Basic.
>
> Ponadto nie należy mylić czystych funkcji z czystymi metodami wirtualnymi w programie C++. Ten drugi wskazuje, że Klasa zawierająca jest abstrakcyjna i nie dostarczono treści metody.

### <a name="functional-programming"></a>Programowanie funkcjonalne

*Programowanie funkcjonalne* jest podejściem programistycznym, które bezpośrednio obsługuje funkcję czystego przekształcania funkcjonalności.

W historycznych językach programowania, takich jak ML, schematy, Haskell i F#, mają głównie znaczenie dla społeczności akademickiej. Mimo że zawsze było możliwe zapisanie czystych transformacji funkcjonalnych w Visual Basic, trudności z tym nie spowodowały, że nie zostały one atrakcyjną opcją dla większości programistów. W nowszych wersjach Visual Basic, jednak nowe konstrukcje języka, takie jak wyrażenia lambda i wnioskowanie o typie, sprawiają, że programowanie funkcjonalnie znacznie prostsze i wydajniejsze.

Aby uzyskać więcej informacji na temat programowania funkcjonalnego, zobacz Programowanie funkcjonalne i bezwzględne [programowanie (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md).

#### <a name="domain-specific-fp-languages"></a>Specyficzne dla domeny Języki FP

Mimo że ogólne, funkcjonalne Języki programowania nie zostały szeroko przyjęte, specyficzne dla konkretnych domen Języki programowania funkcjonalnego były lepszym sukcesem. Na przykład kaskadowe arkusze stylów (CSS) służy do określania wyglądu i sposobu działania wielu stron sieci Web, a arkusze stylów Extensible Stylesheet Language Transformations (XSLT) są szeroko używane w manipulowaniu danymi XML. Aby uzyskać więcej informacji na temat XSLT, zobacz [XSLT Transformations](../../../../standard/data/xml/xslt-transformations.md).

## <a name="terminology"></a>Terminologia

W poniższej tabeli zdefiniowano niektóre terminy związane z transformacjami funkcjonalnymi.

Funkcja wyższej kolejności (pierwszej klasy) \
Funkcja, która może być traktowana jako obiekt programistyczny. Na przykład funkcja wyższego rzędu może być przekazana do lub zwrócona z innych funkcji. W Visual Basic, Delegaty i wyrażenia lambda są funkcjami językowymi, które obsługują funkcje wyższego rzędu. Aby napisać funkcję wyższego rzędu, należy zadeklarować jeden lub więcej argumentów do przejęcia delegatów i często używać wyrażeń lambda podczas wywoływania. Wiele standardowych operatorów zapytań to funkcje wyższego rzędu.

Aby uzyskać więcej informacji, zobacz [standardowe operatory zapytań — Omówienie (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).

wyrażenie lambda \
Zasadniczo Wbudowana funkcja anonimowa, która może być używana wszędzie tam, gdzie jest oczekiwany typ delegata. Jest to uproszczona definicja wyrażeń lambda, ale jest ona odpowiednia do celów tego samouczka.

Aby uzyskać więcej informacji na temat, zobacz [lambda Expressions](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).

zbiera
Strukturalny zestaw danych, zazwyczaj o jednolitym typie. Aby była zgodna z LINQ, kolekcja musi implementować interfejs <xref:System.Collections.IEnumerable> lub interfejs <xref:System.Linq.IQueryable> (lub jeden z ich rodzajowych odpowiedników, <xref:System.Collections.Generic.IEnumerator%601> lub <xref:System.Linq.IQueryable%601>).

Krotka (typy anonimowe) \
Koncepcja matematyczna, krotka jest skończoną sekwencją obiektów, każdego określonego typu. Spójna kolekcja jest również nazywana listą uporządkowaną. Typy anonimowe to implementacje języka tego koncepcji, które umożliwiają zadeklarowanie nienazwanego typu klasy i obiekt tego typu do wystąpienia w tym samym czasie.

Aby uzyskać więcej informacji, zobacz [Typy anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).

Wnioskowanie o typie (niejawne wpisywanie) \
Możliwość kompilatora, aby określić typ zmiennej w nieobecności jawnej deklaracji typu.

Aby uzyskać więcej informacji, zobacz temat [wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).

wykonywanie odroczone i Ocena z opóźnieniem \
Opóźnienie obliczania wyrażenia do momentu, gdy jego rozpoznana wartość nie jest wymagana. Wykonywanie odroczone jest obsługiwane w kolekcjach.

Aby uzyskać więcej informacji, zobacz [podstawowe operacje zapytań (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md) i [wykonywanie odroczone oraz obliczanie z opóźnieniem w LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).

Te funkcje języka będą używane w przykładach kodu w tej sekcji.

## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do czystych transformacji funkcjonalnych (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)
- [Programowanie funkcjonalne a programowanie bezwzględne (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)

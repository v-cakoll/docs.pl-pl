---
title: Pojęcia i terminologia (Przekształcanie funkcjonalne) (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 24fd244d-ebae-4721-8858-89bb544aea0b
ms.openlocfilehash: c6308185b39651095482dca434ce25d717bd5e6b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61663482"
---
# <a name="concepts-and-terminology-functional-transformation-visual-basic"></a>Pojęcia i terminologia (Przekształcanie funkcjonalne) (Visual Basic)
Ten temat wprowadza pojęcia i terminologia czystych przekształceń funkcjonalnych. Przekształcanie funkcjonalne podejście do przekształcania danych daje kod, który jest zwykle łatwiejsze do programu, bardziej ekspresyjnego i prostsze do debugowania i Obsługa programowania bardziej tradycyjny, imperatywnego.  
  
 Należy zauważyć, że tematy w tej sekcji nie są przeznaczone do pełni wyjaśnić programowania funkcjonalnego. Zamiast tego te tematy zidentyfikować niektórych możliwości programowania funkcjonalnego, które ułatwiają przekształcać pliki XML z jednego kształtu do innego.  
  
## <a name="what-is-pure-functional-transformation"></a>Czyste Przekształcanie funkcjonalne co to jest?  
 W *czyste Przekształcanie funkcjonalne*, zestaw funkcji, o nazwie *czystych funkcji*, zdefiniuj jak przekształcić zestaw danych ze strukturą w ich oryginalnej formie w innej formy. Słowo "czysta" wskazuje, że funkcje *konfigurowalna*, które wymagają, że są one:  
  
- *Niezależna*, dzięki czemu mogą być swobodnie uporządkowane i nieco inaczej rozmieszczone bez zaplątywanie i współzależności z pozostałej części programu. Czysty przekształcenia mają nie znajomości lub wpływ na ich środowiska. Oznacza to, że nie mają funkcji używany podczas przekształcania *efekty uboczne*.  
  
- *Bezstanowe*, dzięki czemu wykonanie tej samej funkcji lub określony zestaw funkcji na to samo wejście zawsze spowoduje ten sam wynik. Czystych przekształceń jest nie pamięci ich wcześniejszego użycia.  
  
> [!IMPORTANT]
>  W pozostałej części tego samouczka termin "czystą funkcję" jest używana w ogólnym sensie wskazujący strategii programowania, a nie funkcji określonego języka.  
>   
>  Należy pamiętać, że czystych funkcji muszą być zaimplementowane jako funkcje w języku Visual Basic.  
>   
>  Ponadto nie należy mylić czystych funkcji za pomocą czystych metod wirtualnych, w języku C++. Te ostatnie wskazuje, że klasa zawierająca jest abstrakcyjny i podano bez treści metody.  
  
### <a name="functional-programming"></a>Programowanie funkcjonalne  
 *Programowanie funkcjonalne* jest strategii programowania, które bezpośrednio obsługuje czyste Przekształcanie funkcjonalne.  
  
 W przeszłości ogólnego przeznaczenia funkcjonalności języków programowania, takich jak uczenie Maszynowe, schemat, Haskell, i F#, były przydatne głównie dla akademickich społeczności. Mimo że zawsze było możliwe do zapisu czystych przekształceń funkcjonalnych w języku Visual Basic, trudności spowoduje więc nie wprowadził go atrakcyjny możliwość Większość programistów. Przy użyciu nowszej wersji programu Visual Basic jednak nowe konstrukcje językowe, takie jak wyrażenia lambda i wnioskowanie o typie ułatwiają programowanie funkcjonalne znacznie łatwiejsze i bardziej produktywne.  
  
 Aby uzyskać więcej informacji na temat programowania funkcjonalnego, zobacz [programowania funkcyjnego programu vs. Programowanie imperatywne (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md).  
  
#### <a name="domain-specific-fp-languages"></a>Języki specyficzne dla domeny FP  
 Chociaż ogólne języków programowania funkcjonalności nie zostały przyjęte powszechnie, języki specyficzne dla specyficznego dla domeny funkcjonalności programowania mieli lepsze sukces. Na przykład kaskadowych arkuszy stylów (CSS) są używane w celu określenia wyglądu i działania wiele stron sieci Web i arkusze stylów Extensible arkusza stylów języka przekształcenia (XSLT) są często używane operacje na danych XML. Aby uzyskać więcej informacji na temat XSLT, zobacz [przekształcenia XSLT](../../../../standard/data/xml/xslt-transformations.md).  
  
## <a name="terminology"></a>Terminologia  
 W poniższej tabeli opisano niektóre pojęcia związane z przekształceń funkcjonalnych.  
  
 wyższego rzędu (funkcji pierwszej klasy)  
 Funkcja, która może być traktowana jako programowy obiekt. Na przykład funkcja wyższego rzędu można przekazany do lub zwracane przez inne funkcje. Delegaci i wyrażenia lambda w języku Visual Basic są funkcje językowe, które obsługi funkcji wyższego rzędu. Aby zapisać funkcja wyższego rzędu, Zadeklaruj jeden lub więcej argumentów, aby móc delegatów, a są często używane wyrażenia lambda przy wywoływaniu tego elementu. Wiele standardowych operatorów zapytań jest funkcji wyższego rzędu.  
  
 Aby uzyskać więcej informacji, zobacz [standardowe operatory zapytań — Przegląd (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
 Wyrażenia lambda  
 Zasadniczo wbudowane funkcja anonimowa, która może służyć wszędzie tam, gdzie oczekiwany jest typ delegatu. Jest to uproszczony definicji wyrażenia lambda, ale jest odpowiedni na potrzeby tego samouczka.  
  
 Aby uzyskać więcej informacji na temat, zobacz [wyrażeń Lambda](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
  — kolekcja  
 Uporządkowany zestaw danych, zazwyczaj jednolitego typu. Aby były zgodne z LINQ, Kolekcja musi implementować <xref:System.Collections.IEnumerable> interfejsu lub <xref:System.Linq.IQueryable> interfejsu (lub ich odpowiedników ogólny, <xref:System.Collections.Generic.IEnumerator%601> lub <xref:System.Linq.IQueryable%601>).  
  
 krotki (typy anonimowe)  
 Koncepcja matematyczne krotki jest ograniczone sekwencji obiektów, każdy z określonego typu. Spójna kolekcja jest również nazywany listy uporządkowanej. Typy anonimowe to implementacja języka tę koncepcję, które umożliwiają typu klasa Nienazwana deklaruje się i obiektu tego typu można utworzyć wystąpienia w tym samym czasie.  
  
 Aby uzyskać więcej informacji, zobacz [typy anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
 wnioskowanie o typie (niejawnego wpisywania)  
 Zdolność kompilatora do określenia typu zmiennej w przypadku braku deklaracji typu jawnego.  
  
 Aby uzyskać więcej informacji, zobacz [wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
 wykonanie odroczone i obliczanie z opóźnieniem  
 Opóźnienie wyniku obliczenia wyrażenia aż do jej rozpoznana wartość jest faktycznie wymagana. Wykonanie odroczone jest obsługiwane w kolekcji.  
  
 Aby uzyskać więcej informacji, zobacz [podstawowe operacje zapytań (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md) i [wykonanie odroczone i obliczanie z opóźnieniem w LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).  
  
 Te funkcje językowe, będzie używany w przykładach kodu w tej sekcji.  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do czystych przekształceń funkcjonalnych (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)
- [Programowanie funkcjonalne a Programowanie imperatywne (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)

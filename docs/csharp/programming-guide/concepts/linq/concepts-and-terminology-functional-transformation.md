---
title: Pojęcia i terminologię (funkcjonalności przekształcania) (C#)
ms.date: 07/20/2015
ms.assetid: 03defb3a-7e17-4ab1-8efa-4dd66621e860
ms.openlocfilehash: f0d09f8846556dfa0ce70f253d59ddd41f254363
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339293"
---
# <a name="concepts-and-terminology-functional-transformation-c"></a>Pojęcia i terminologię (funkcjonalności przekształcania) (C#)
W tym temacie przedstawiono pojęcia i terminologię czysty transformacji funkcjonalności. Metody przekształcania funkcjonalności do przekształcania danych implikuje kod, który często jest szybsze do programu, bardziej obszerne i łatwiejsze do debugowania i obsługa niż programowania bardziej tradycyjnej, konieczne.  
  
 Należy pamiętać, że tematy w tej sekcji nie są przeznaczone do pełni opisano programowanie funkcjonalne. Zamiast tego w tych tematach zidentyfikować niektórych funkcjonalności możliwości programowania, które ułatwiają Przekształć jeden kształt XML.  
  
## <a name="what-is-pure-functional-transformation"></a>Co to jest czysty przekształcania funkcjonalności?  
 W *czysty przekształcania funkcjonalności*, zestaw funkcji o nazwie *czystych funkcji*, definiowanie sposobu przekształcania zestawu danych strukturalnych w postaci oryginalnej innej formy. Wyraz "czysty" wskazuje, że funkcje *zezwala na składanie*, które wymaga, aby były one:  
  
-   *Samodzielne*, dzięki czemu może być za darmo uporządkowane i zmieniać kolejności bez zaplątywanie lub zależnościami z resztą program. Czysty przekształcenia mieć wiedzę na temat lub wpływ na ich środowiska. Oznacza to, że nie mają funkcji używany podczas przekształcania *efekty uboczne*.  
  
-   *Bezstanowe*, dzięki czemu wykonywanie tej samej funkcji lub określonych funkcji w tej samej danych wejściowych zawsze spowoduje tych samych danych wyjściowych. Czysty przekształcenia ma Brak pamięci ich uprzedniego użycia.  
  
> [!IMPORTANT]
>  W pozostałej części tego samouczka termin "czystej funkcji" jest używany w sposób ogólny wskazujący strategii programowania, a nie funkcja określonego języka.  
>   
>  Należy pamiętać, że czystych funkcji muszą zostać zaimplementowane jako metody w języku C#.  
>   
>  Ponadto nie należy mylić czystych funkcji z czystych metod wirtualnych w języku C++. Drugie wskazuje, że klasa zawierająca jest abstrakcyjny i podano nie treści metody.  
  
### <a name="functional-programming"></a>Programowanie funkcjonalne  
 *Programowanie funkcjonalne* jest programowania podejście, które bezpośrednio obsługuje czysty przekształcania funkcjonalności.  
  
 W przeszłości ogólnego przeznaczenia funkcjonalności języków programowania, takich jak ML, schemat, Haskell i F # zostały płynących academic społeczności. Mimo że zawsze było możliwe do zapisu czysty funkcjonalności przekształcenia w języku C#, trudności zrobić tak nie wprowadził on atrakcyjną opcję dla większości programistów. W nowszych wersjach języka C# jednak nowe konstrukcje językowe takie jak wyrażenia lambda i wnioskowanie o typie była funkcjonalności programowania znacznie łatwiejsze i bardziej wydajnej pracy.  
  
 Aby uzyskać więcej informacji o programowanie funkcjonalne, zobacz [programowania funkcjonalności programu vs. Konieczne programowania w języku (C#)](../../../../csharp/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md).  
  
#### <a name="domain-specific-fp-languages"></a>Języki FP specyficznego dla domeny  
 Chociaż nie zostały powszechnie przyjęte ogólne funkcjonalności języków programowania, określonych specyficznego dla domeny funkcjonalności języków programowania miały lepszą Powodzenie. Na przykład kaskadowych arkuszy stylów (CSS) są używane do określania wyglądu i działania wiele stron sieci Web i arkusze stylów Extensible języka przekształcenia XSLT (Stylesheet) są często używane w manipulowania danymi XML. Aby uzyskać więcej informacji na temat XSLT, zobacz [przekształcenia XSLT](../../../../standard/data/xml/xslt-transformations.md).  
  
## <a name="terminology"></a>Terminologia  
 W poniższej tabeli opisano terminy związane z funkcjonalności przekształcenia.  
  
 wyższego rzędu funkcji (pierwszoklasowej)  
 Funkcja, która może być traktowana jako programowy obiekt. Na przykład funkcja wyższego rzędu można przekazany do lub zwracane z innych funkcji. W języku C #c, delegatów i wyrażenia lambda są funkcji języka, które obsługuje funkcje wyższego rzędu. Do pisania funkcji wyższego rzędu deklaruje co najmniej jeden z argumentów podjęcie delegatów, a często można użyć wyrażenia lambda podczas wywoływania go. Wiele standardowych operatorów zapytań są funkcje wyższego rzędu.  
  
 Aby uzyskać więcej informacji, zobacz [standardowe operatory zapytań — omówienie (C#)](../../../../csharp/programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
 wyrażenia lambda  
 Zasadniczo wbudowanej funkcji anonimowej służący wszędzie tam, gdzie oczekiwany jest typ delegata. To jest uproszczone definicji wyrażenia lambda, ale jest odpowiedni na potrzeby tego samouczka.  
  
 Aby uzyskać więcej informacji na temat, zobacz [wyrażenia Lambda](../../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).  
  
 — kolekcja  
 Strukturalne zestaw danych, zwykle uniform typu. Aby był zgodny z LINQ, Kolekcja musi implementować <xref:System.Collections.IEnumerable> interfejsu lub <xref:System.Linq.IQueryable> interfejsu (lub jeden z ich odpowiedniki ogólny, <xref:System.Collections.Generic.IEnumerator%601> lub <xref:System.Linq.IQueryable%601>).  
  
 krotki (typy anonimowe)  
 Pojęcie matematyczne spójnych kolekcji to ograniczona sekwencja obiektów, każdego określonego typu. Krotka jest nazywana listy uporządkowanej. Typy anonimowe to implementacja języka tę koncepcję, która umożliwić typu klasy bez nazwy na i obiektu tego typu można utworzyć wystąpienia, w tym samym czasie.  
  
 Aby uzyskać więcej informacji, zobacz [typy anonimowe](../../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).  
  
 wnioskowanie o typie (niejawne wpisaniu)  
 Możliwość kompilatora można określić typu zmienną, w przypadku braku deklaracji typu jawnego.  
  
 Aby uzyskać więcej informacji, zobacz [niejawnie wpisane zmienne lokalne](../../../../csharp/programming-guide/classes-and-structs/implicitly-typed-local-variables.md).  
  
 wykonanie odroczone i obliczanie leniwe  
 Opóźnienie obliczenia wyrażenia aż do jej rozpoznana wartość jest faktycznie wymagane. Wykonanie odroczone jest obsługiwane w kolekcji.  
  
 Aby uzyskać więcej informacji, zobacz [wprowadzenie do kwerend LINQ (C#)](../../../../csharp/programming-guide/concepts/linq/introduction-to-linq-queries.md) i [wykonanie odroczone i obliczanie leniwe w składniku LINQ to XML (C#)](../../../../csharp/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).  
  
 Te funkcje języka będą używane w przykładach kodu w tej sekcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do przekształcenia funkcjonalności Pure (C#)](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)  
 [Programowanie funkcjonalne a Konieczne programowania w języku (C#)](../../../../csharp/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)

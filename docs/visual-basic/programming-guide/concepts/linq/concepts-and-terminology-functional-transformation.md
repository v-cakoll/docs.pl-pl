---
title: "Pojęcia i terminologię (funkcjonalności przekształcania) (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 24fd244d-ebae-4721-8858-89bb544aea0b
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 12b40d31688d852c9f9b3f644f64fc273c76209c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="concepts-and-terminology-functional-transformation-visual-basic"></a>Pojęcia i terminologię (funkcjonalności przekształcania) (Visual Basic)
W tym temacie przedstawiono pojęcia i terminologię czysty transformacji funkcjonalności. Metody przekształcania funkcjonalności do przekształcania danych implikuje kod, który często jest szybsze do programu, bardziej obszerne i łatwiejsze do debugowania i obsługa niż programowania bardziej tradycyjnej, konieczne.  
  
 Należy pamiętać, że tematy w tej sekcji nie są przeznaczone do pełni opisano programowanie funkcjonalne. Zamiast tego w tych tematach zidentyfikować niektórych funkcjonalności możliwości programowania, które ułatwiają Przekształć jeden kształt XML.  
  
## <a name="what-is-pure-functional-transformation"></a>Co to jest czysty przekształcania funkcjonalności?  
 W *czysty przekształcania funkcjonalności*, zestaw funkcji o nazwie *czystych funkcji*, definiowanie sposobu przekształcania zestawu danych strukturalnych w postaci oryginalnej innej formy. Wyraz "czysty" wskazuje, że funkcje *zezwala na składanie*, które wymaga, aby były one:  
  
-   *Samodzielne*, dzięki czemu może być za darmo uporządkowane i zmieniać kolejności bez zaplątywanie lub zależnościami z resztą program. Czysty przekształcenia mieć wiedzę na temat lub wpływ na ich środowiska. Oznacza to, że nie mają funkcji używany podczas przekształcania *efekty uboczne*.  
  
-   *Bezstanowe*, dzięki czemu wykonywanie tej samej funkcji lub określonych funkcji w tej samej danych wejściowych zawsze spowoduje tych samych danych wyjściowych. Czysty przekształcenia ma Brak pamięci ich uprzedniego użycia.  
  
> [!IMPORTANT]
>  W pozostałej części tego samouczka termin "czystej funkcji" jest używany w sposób ogólny wskazujący strategii programowania, a nie funkcja określonego języka.  
>   
>  Należy pamiętać, że czystych funkcji muszą zostać zaimplementowane jako funkcje w języku Visual Basic.  
>   
>  Ponadto nie należy mylić czystych funkcji z czystych metod wirtualnych w języku C++. Drugie wskazuje, że klasa zawierająca jest abstrakcyjny i podano nie treści metody.  
  
### <a name="functional-programming"></a>Programowanie funkcjonalne  
 *Programowanie funkcjonalne* jest programowania podejście, które bezpośrednio obsługuje czysty przekształcania funkcjonalności.  
  
 W przeszłości ogólnego przeznaczenia funkcjonalności języków programowania, takich jak ML, schemat, Haskell i F # zostały płynących academic społeczności. Mimo że zawsze było możliwe do zapisu czysty funkcjonalności przekształcenia w języku Visual Basic, trudności zrobić tak nie wprowadził on atrakcyjną opcję dla większości programistów. W nowszych wersjach Visual Basic jednak nowe konstrukcje językowe takie jak wyrażenia lambda i wnioskowanie o typie była funkcjonalności programowania znacznie łatwiejsze i bardziej wydajnej pracy.  
  
 Aby uzyskać więcej informacji o programowanie funkcjonalne, zobacz [programowania funkcjonalności programu vs. Programowanie imperatywnych (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md).  
  
#### <a name="domain-specific-fp-languages"></a>Języki FP specyficznego dla domeny  
 Chociaż nie zostały powszechnie przyjęte ogólne funkcjonalności języków programowania, określonych specyficznego dla domeny funkcjonalności języków programowania miały lepszą Powodzenie. Na przykład kaskadowych arkuszy stylów (CSS) są używane do określania wyglądu i działania wiele stron sieci Web i arkusze stylów Extensible języka przekształcenia XSLT (Stylesheet) są często używane w manipulowania danymi XML. Aby uzyskać więcej informacji na temat XSLT, zobacz [przekształcenia XSLT](../../../../standard/data/xml/xslt-transformations.md).  
  
## <a name="terminology"></a>Terminologia  
 W poniższej tabeli opisano terminy związane z funkcjonalności przekształcenia.  
  
 wyższego rzędu funkcji (pierwszoklasowej)  
 Funkcja, która może być traktowana jako programowy obiekt. Na przykład funkcja wyższego rzędu można przekazany do lub zwracane z innych funkcji. Delegaci i wyrażenia lambda w języku Visual Basic są funkcji języka, które obsługuje funkcje wyższego rzędu. Do pisania funkcji wyższego rzędu deklaruje co najmniej jeden z argumentów podjęcie delegatów, a często można użyć wyrażenia lambda podczas wywoływania go. Wiele standardowych operatorów zapytań są funkcje wyższego rzędu.  
  
 Aby uzyskać więcej informacji, zobacz [standardowe operatory zapytań — omówienie (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/standard-query-operators-overview.md).  
  
 wyrażenia lambda  
 Zasadniczo wbudowanej funkcji anonimowej służący wszędzie tam, gdzie oczekiwany jest typ delegata. To jest uproszczone definicji wyrażenia lambda, ale jest odpowiedni na potrzeby tego samouczka.  
  
 Aby uzyskać więcej informacji na temat, zobacz [wyrażenia Lambda](../../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 — kolekcja  
 Strukturalne zestaw danych, zwykle uniform typu. Aby był zgodny z LINQ, Kolekcja musi implementować <xref:System.Collections.IEnumerable> interfejsu lub <xref:System.Linq.IQueryable> interfejsu (lub jeden z ich odpowiedniki ogólny, <xref:System.Collections.Generic.IEnumerator%601> lub <xref:System.Linq.IQueryable%601>).  
  
 krotki (typy anonimowe)  
 Pojęcie matematyczne spójnych kolekcji to ograniczona sekwencja obiektów, każdego określonego typu. Krotka jest nazywana listy uporządkowanej. Typy anonimowe to implementacja języka tę koncepcję, która umożliwić typu klasy bez nazwy na i obiektu tego typu można utworzyć wystąpienia, w tym samym czasie.  
  
 Aby uzyskać więcej informacji, zobacz [typy anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).  
  
 wnioskowanie o typie (niejawne wpisaniu)  
 Możliwość kompilatora można określić typu zmienną, w przypadku braku deklaracji typu jawnego.  
  
 Aby uzyskać więcej informacji, zobacz [wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
 wykonanie odroczone i obliczanie leniwe  
 Opóźnienie obliczenia wyrażenia aż do jej rozpoznana wartość jest faktycznie wymagane. Wykonanie odroczone jest obsługiwane w kolekcji.  
  
 Aby uzyskać więcej informacji, zobacz [podstawowe operacje zapytań (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/basic-query-operations.md) i [wykonanie odroczone i obliczanie leniwe w składniku LINQ to XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/deferred-execution-and-lazy-evaluation-in-linq-to-xml.md).  
  
 Te funkcje języka będą używane w przykładach kodu w tej sekcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do przekształcenia funkcjonalności czysty (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)  
 [Funkcjonalności vs programowania. Programowanie imperatywnych (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/functional-programming-vs-imperative-programming.md)

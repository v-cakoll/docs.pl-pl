---
title: Programowanie funkcjonalne a programowanie imperatywne (C#)
ms.date: 07/20/2015
ms.assetid: 5e35c5a0-c949-422a-873b-fca6b2254f57
ms.openlocfilehash: a163a62912ed2a44d6ea8cad5bc536f03343f15c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "69594314"
---
# <a name="functional-programming-vs-imperative-programming-c"></a>Programowanie funkcjonalne a programowanie imperatywne (C#)
W tym temacie porównuje i kontrastuje programowania funkcjonalnego z bardziej tradycyjnych imperatyw (proceduralnych) programowania.  
  
## <a name="functional-programming-vs-imperative-programming"></a>Programowanie funkcjonalne a programowanie imperatywne  
 Funkcjonalny paradygmat *programowania* został wyraźnie stworzony w celu wspierania czystego funkcjonalnego podejścia do rozwiązywania problemów. Programowanie funkcjonalne jest formą *programowania deklaratywnego.* Z drugiej strony większość języków głównego nurtu, w tym języków programowania obiektowego (OOP), takich jak C#, Visual Basic, C++ i Java, zostały zaprojektowane głównie do obsługi *programowania imperatywnego* (proceduralnego).  
  
 Z podejściem imperatywnym deweloper a programista pisze kod, który opisuje w wymagających szczegółów kroki, które komputer musi podjąć, aby osiągnąć cel. Jest to czasami określane jako programowanie *algorytmiczne.* Z drugiej strony podejście funkcjonalne polega na redagowaniu problemu jako zestawu funkcji do wykonania. Starannie definiuje się dane wejściowe do każdej funkcji i co każda funkcja zwraca. W poniższej tabeli opisano niektóre ogólne różnice między tymi dwoma podejściami.  
  
|Charakterystyka|Podejście imperatywne|Podejście funkcjonalne|  
|--------------------|-------------------------|-------------------------|  
|Koncentracja na programisty|Jak wykonywać zadania (algorytmy) i jak śledzić zmiany w stanie.|Jakie informacje są pożądane i jakie przekształcenia są wymagane.|  
|Zmiany stanu|Ważne.|Nie istnieje.|  
|Zlecenie wykonania|Ważne.|Niskie znaczenie.|  
|Podstawowa kontrola przepływu|Pętle, warunkowce i funkcje (metody) wywołania.|Wywołania funkcji, w tym rekursji.|  
|Podstawowa jednostka manipulacyjna|Wystąpienia struktur lub klas.|Działa jako pierwszorzędne obiekty i kolekcje danych.|  
  
 Chociaż większość języków została zaprojektowana do obsługi określonego paradygmatu programowania, wiele języków ogólnych jest wystarczająco elastycznych, aby obsługiwać wiele paradygmatów. Na przykład większość języków, które zawierają wskaźniki funkcji może służyć do wiarygodnego obsługi programowania funkcjonalnego. Ponadto C# zawiera rozszerzenia języka jawnego do obsługi programowania funkcjonalnego, w tym wyrażenia lambda i wnioskowanie o typie. Technologia LINQ jest formą deklaratywnego, funkcjonalnego programowania.  
  
## <a name="functional-programming-using-xslt"></a>Programowanie funkcjonalne za pomocą XSLT  
 Wielu programistów XSLT zna podejście czysto funkcjonalne. Najskuteczniejszym sposobem opracowania arkusza stylów XSLT jest traktowanie każdego szablonu jako izolowanej, kompowainowej transformacji. Kolejność wykonania jest całkowicie de-podkreślił. XSLT nie zezwala na działania niepożądane (z tym wyjątkiem, że uciekające mechanizmy wykonywania kodu proceduralnego mogą wprowadzać skutki uboczne, które powodują zanieczyszczenie funkcjonalne). Jednakże, chociaż XSLT jest skutecznym narzędziem, niektóre z jego cech nie są optymalne. Na przykład ekspresji konstrukcji programowania w języku XML sprawia, że kod stosunkowo pełne i dlatego trudne do utrzymania. Ponadto duże poleganie na rekursji dla sterowania przepływem może spowodować kod, który jest trudny do odczytania. Aby uzyskać więcej informacji na temat XSLT, zobacz [XSLT Transformacje](../../../../standard/data/xml/xslt-transformations.md).  
  
 Jednak XSLT udowodnił wartość przy użyciu czystego podejścia funkcjonalnego do przekształcania XML z jednego kształtu do drugiego. Czyste funkcjonalne programowanie z LINQ do XML jest pod wieloma względami podobne do XSLT. Jednak konstrukcje programowania wprowadzone przez LINQ do XML i C# umożliwiają pisanie czystych przekształceń funkcjonalnych, które są bardziej czytelne i możliwe do utrzymania niż XSLT.  
  
## <a name="advantages-of-pure-functions"></a>Zalety czystych funkcji  
 Głównym powodem implementacji transformacji funkcjonalnych jako czystych funkcji jest to, że czyste funkcje są komnalne: to znaczy niezależne i bezstanowe. Cechy te przynoszą szereg korzyści, w tym następujące:  
  
- Zwiększona czytelność i łatwość konserwacji. Jest tak, ponieważ każda funkcja jest przeznaczona do wykonania określonego zadania, biorąc pod uwagę jego argumenty. Funkcja nie opiera się na żadnym stanie zewnętrznym.  
  
- Łatwiejszy rozwój reiteracyjny. Ponieważ kod jest łatwiejsze do refaktoryzacji, zmiany w projekcie są często łatwiejsze do zaimplementowania. Załóżmy na przykład, że piszesz skomplikowaną transformację, a następnie zdajesz sobie sprawę, że niektóre kodu jest powtarzany kilka razy w transformacji. Jeśli refaktoryzacji za pomocą czystej metody, można wywołać czystej metody do woli, nie martwiąc się o skutki uboczne.  
  
- Łatwiejsze testowanie i debugowanie. Ponieważ czyste funkcje można łatwiej przetestować w izolacji, można napisać kod testu, który wywołuje czystą funkcję z typowymi wartościami, prawidłowymi przypadkami krawędzi i nieprawidłowymi przypadkami krawędzi.  
  
## <a name="transitioning-for-oop-developers"></a>Przejście dla deweloperów OOP  
 W tradycyjnym programowaniu obiektowym (OOP) większość deweloperów jest przyzwyczajona do programowania w stylu imperatywu/proceduralnym. Aby przejść do rozwoju w czystym stylu funkcjonalnym, muszą dokonać przejścia w swoim myśleniu i podejściu do rozwoju.  
  
 Aby rozwiązać problemy, deweloperzy OOP projektują hierarchie klas, koncentrują się na prawidłowej hermetyzacji i myślą o kontraktach klasowych. Zachowanie i stan typów obiektów są najważniejsze, a funkcje języka, takie jak klasy, interfejsy, dziedziczenie i polimorfizm, są dostarczane w celu rozwiązania tych problemów.  
  
 Natomiast programowanie funkcjonalne podchodzi do problemów obliczeniowych jako ćwiczenie w ocenie czystej transformacji funkcjonalnej zbiorów danych. Programowanie funkcjonalne pozwala uniknąć stanu i danych zapisywanych, a zamiast tego podkreśla zastosowanie funkcji.  
  
 Na szczęście C# nie wymaga pełnego skoku do programowania funkcjonalnego, ponieważ obsługuje zarówno imperatywne i funkcjonalne podejścia programowania. Deweloper może wybrać, które podejście jest najbardziej odpowiednie dla określonego scenariusza. W rzeczywistości programy często łączą oba podejścia.  
  
## <a name="see-also"></a>Zobacz też

- [Wprowadzenie do czystych przemian funkcjonalnych (C#)](./introduction-to-pure-functional-transformations.md)
- [Przekształcenia XSLT](../../../../standard/data/xml/xslt-transformations.md)
- [Refaktoryzacja do czystych funkcji (C#)](./refactoring-into-pure-functions.md)

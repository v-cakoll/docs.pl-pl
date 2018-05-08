---
title: Funkcjonalności vs programowania. Konieczne programowania w języku (C#)
ms.date: 07/20/2015
ms.assetid: 5e35c5a0-c949-422a-873b-fca6b2254f57
ms.openlocfilehash: 85e0e4bf287157f2d4f952996cbb2e5a4ff6ac89
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="functional-programming-vs-imperative-programming-c"></a>Funkcjonalności vs programowania. Konieczne programowania w języku (C#)
W tym temacie porównuje i różni się znacząco programowanie funkcjonalne bardziej tradycyjnej imperatywnych programowania (procedurach).  
  
## <a name="functional-programming-vs-imperative-programming"></a>Funkcjonalności vs programowania. Programowanie imperatywne  
 *Programowanie funkcjonalne* modelu jawnie został utworzony w celu obsługi czysty funkcjonalności służące do rozwiązywania problemów. Programowanie funkcjonalne jest formą *programowanie deklaratywne*. Z kolei większości tych języków, w tym zorientowane obiektowo (Obiektowo) języków programowania, takich jak C#, Visual Basic C++ i Java, są przeznaczone do obsługi głównie *imperatywnych* programowania (procedurach).  
  
 Imperatywnych podejścia przy rozwiązywaniu dewelopera zapisuje kod, który opisuje w ponoszenia szczegółowe kroki, które należy wykonać komputera, aby osiągnąć cel. Jest to czasami określane jako *algorytmicznego* programowania. Z kolei funkcjonalności podejście obejmuje tworzenie problem jako zestaw funkcji do wykonania. Należy zdefiniować dokładnie w danych wejściowych poszczególnych funkcji i zwraca jakie każdej funkcji. W poniższej tabeli opisano niektóre ogólne różnice między te dwie metody.  
  
|Cechy|Podejście imperatywne|Podejście funkcjonalności|  
|--------------------|-------------------------|-------------------------|  
|Fokus programisty|Jak wykonać zadania (algorytmy) i jak śledzić zmiany w stanie.|Wymagane jest informacjach i jakie przekształceń są wymagane.|  
|Zmiany stanu|Ważne.|Nieistniejąca.|  
|Kolejność wykonywania|Ważne.|Niskiej ważności.|  
|Podstawowy przepływ sterowania|Pętle, warunków i wywołania funkcji (metoda).|Wywołania funkcji, łącznie z rekursji.|  
|Manipulowanie podstawowej jednostki|Wystąpienia klasy lub struktury.|Funkcje jako najwyższej jakości kolekcje obiektów i danych.|  
  
 Mimo że większość języków są przeznaczone do obsługi określonego modelu programowania, wiele języków ogólne są wystarczająco elastyczny, aby obsługiwać wiele wzorcami. Na przykład większość języków, które zawierają wskaźniki funkcji mogą służyć do obsługi sprostają programowanie funkcjonalne. Ponadto C# zawiera rozszerzenia językowe jawne obsługuje programowanie funkcjonalne, łącznie z wyrażenia lambda i wnioskowanie typu. Technologia LINQ jest formularz deklaratywne, funkcje programowania.  
  
## <a name="functional-programming-using-xslt"></a>Funkcjonalności programowania w języku XSLT  
 Czysty podejście funkcjonalności znają wielu deweloperów XSLT. Najlepszym sposobem na opracowanie arkusz stylów XSLT jest zaliczenie każdego szablonu transformację izolowanym, która zezwala na składanie. Kolejność wykonywania jest całkowicie wyłączyć wyróżniono. XSLT nie zezwala na efekty uboczne (z wyjątkiem, że anulowanie mechanizmy wykonywania procedur kodu można wprowadzać efekty uboczne, które powodują powstanie zanieczyszczenie funkcjonalności). Jednak mimo że XSLT jest skutecznym, niektóre jego właściwości nie są optymalne. Na przykład wyrażenie konstrukcji programowania w języku XML sprawia, że kod stosunkowo pełne i w związku z tym trudne w utrzymaniu. Ponadto duże zależność od rekursji sterowania przepływem może spowodować kodu, który jest trudny do odczytania. Aby uzyskać więcej informacji na temat XSLT, zobacz [przekształcenia XSLT](../../../../standard/data/xml/xslt-transformations.md).  
  
 Jednak XSLT okazało się przy użyciu czysty podejście funkcjonalności do transformacji XML z jednego kształtu do innej wartości. Czysty funkcjonalności programowanie za pomocą LINQ do XML przypomina na wiele sposobów XSLT. Jednak narzędzi programistycznych wprowadzone w składniku LINQ to XML i C# umożliwiają pisanie czysty przekształcenia funkcjonalności, które są bardziej czytelny i łatwy w obsłudze niż XSLT.  
  
## <a name="advantages-of-pure-functions"></a>Zalety czystych funkcji  
 Podstawowym powodem zaimplementować funkcjonalności przekształcenia jako czystych funkcji to czystych funkcji zezwala na składanie: oznacza to, niezależnym i bezstanowe. Te cechy Przełącz wiele korzyści, takie jak następujące:  
  
-   Zwiększenia czytelności i łatwości konserwacji. To jest ponieważ każdej funkcji zaprojektowano w celu wykonania określonego zadania podane argumenty. Funkcja nie bazuje na każdy stan zewnętrznych.  
  
-   Łatwiejsze reiterative programowanie. Ponieważ kod jest łatwiejsze do refaktoryzacji, zmiany do projektowania często są łatwiejsze do wdrożenia. Na przykład załóżmy, że zapis transformację skomplikowane, a następnie należy pamiętać, że kod jest powtarzany kilka razy w transformacji. Jeśli użytkownik Refaktoryzuj przez pure metodę, można wywołać metodę czysty momencie bez obaw o skutki uboczne.  
  
-   Łatwiejsze testowanie i debugowanie. Ponieważ łatwiej można przetestować czystych funkcji oddzielnie, można napisać kod testu, który wywołuje czystej funkcji typowe wartości, przypadków prawidłowy krawędzi i przypadków nieprawidłowy krawędzi.  
  
## <a name="transitioning-for-oop-developers"></a>Przejście dla deweloperów Obiektowo  
 W tradycyjnym programowanie zorientowane obiektowo (Obiektowo), większość deweloperów są przystosowane do programowania w języku w stylu imperatywne/procedur. Aby włączyć tworzenie aplikacji w stylu funkcjonalności czystego, mają one wprowadzać przejścia w ich planowania i ich podejście do rozwoju.  
  
 Aby rozwiązać problemy, deweloperów Obiektowo Projektuj hierarchie klasy, skupić się na właściwe hermetyzacji i wziąć pod uwagę pod względem umów klasy. Zachowanie i stan typów obiektów, są podstawowym, a funkcje językowe, takich jak klasy, interfejsy dziedziczenia i polimorfizm, znajdują się w celu rozwiązania tych problemów.  
  
 Z kolei programowanie funkcjonalne osiąga obliczeniową problemów jako wykonywania podczas obliczania czysty funkcjonalności przekształcenia danych kolekcji. Programowanie funkcjonalne pozwala uniknąć stanu i danych modyfikowalna, a zamiast tego wyróżniane zastosowaniu funkcji.  
  
 Na szczęście C# nie wymaga pełnego przestępnego do programowania funkcjonalności, ponieważ obsługuje ona zarówno nadrzędnych, jak i funkcjonalności podejścia programowania. Projektant można wybrać, które rozwiązanie jest najbardziej odpowiednie dla danego scenariusza. W rzeczywistości programy często łączyć obu podejść.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do przekształcenia funkcjonalności Pure (C#)](../../../../csharp/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)  
 [Przekształcenia XSLT](../../../../standard/data/xml/xslt-transformations.md)  
 [Refaktoryzacja do czystych funkcji (C#)](../../../../csharp/programming-guide/concepts/linq/refactoring-into-pure-functions.md)

---
title: Programowanie funkcjonalne a Programowanie imperatywne (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 6a1f3b57-00e6-447d-9906-74c7c4d5d85c
ms.openlocfilehash: dec9fd4b59d96c0548e49276a27103114a7b3e8b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61931669"
---
# <a name="functional-programming-vs-imperative-programming-visual-basic"></a>Programowanie funkcjonalne a Programowanie imperatywne (Visual Basic)
W tym temacie porównano i przeciwstawiono sobie programowania funkcjonalnego, przy użyciu bardziej tradycyjny imperatywnego (proceduralne).  
  
## <a name="functional-programming-vs-imperative-programming"></a>Programowanie funkcjonalne a programowanie imperatywne  
 *Programowania funkcjonalnego* paradygmat jawnie został utworzony w celu obsługi czystego funkcjonalności służące do rozwiązywania problemów. Programowanie funkcjonalne jest formą *programowanie deklaratywne*. Z kolei większość mainstream języków, w tym zorientowane obiektowo (Obiektowo) języków programowania, takich jak C#, Visual Basic, C++ i Java, zostały zaprojektowane do obsługi przede wszystkim *imperatywne* (proceduralne).  
  
 Przy użyciu podejścia imperatywnego Deweloper pisze kod, który opisano w ponoszenia szczegółowo czynności, które należy wykonać komputera w celu osiągnięcia tego celu. To jest czasami określane jako *konsolidatorze* programowania. Z kolei funkcjonalności podejścia polega na tworzenie problemu jako zbiór funkcji do wykonania. Należy zdefiniować dokładnie dane wejściowe do każdej funkcji i jakie każda funkcja zwraca. W poniższej tabeli opisano niektóre ogólne różnice między dwóm metodom.  
  
|Cechy|Podejścia imperatywnego|Podejście funkcjonalności|  
|--------------------|-------------------------|-------------------------|  
|Fokus programisty|Jak wykonywać zadania (algorytmy) i jak śledzić zmiany w stanie.|Jakie informacje jest pożądane i przekształcenia, które są wymagane.|  
|Zmiany stanu|Ważne.|Nieistniejąca.|  
|Kolejność wykonywania|Ważne.|Niska ważność.|  
|Sterowanie przepływem podstawowego|Pętle, instrukcje warunkowe i wywołania funkcji (metoda).|Wywołań funkcji, w tym rekursji.|  
|Manipulowanie podstawowej jednostki|Wystąpienia elementu struktury lub klasy.|Funkcje jako najwyższej jakości kolekcje obiektów i danych.|  
  
 Chociaż większość języków zostały zaprojektowane do obsługi określonych paradygmat programowania, wielu języków ogólne są wystarczająco elastyczny, aby obsługiwać wiele paradygmatów. Na przykład większość języków, które zawierają wskaźniki funkcji można wiarygodnie Obsługa programowania funkcjonalnego. Ponadto Visual Basic obejmuje rozszerzenia językowe jawne do obsługi programowania funkcjonalnego, w tym wyrażeń lambda i wnioskowanie o typie. Technologia LINQ jest formą deklaratywne, funkcjonalne programowania.  
  
## <a name="functional-programming-using-xslt"></a>Programowanie za pomocą XSLT funkcjonalne  
 Wielu programistów XSLT znają czystego podejście funkcjonalności. Najbardziej efektywny sposób rozwijać arkusz stylów XSLT jest traktuje każdy szablon jako izolowanym, konfigurowalna transformacji. Kolejność wykonywania jest całkowicie wyłączyć wyróżniony. XSLT nie zezwala na efekty uboczne (z wyjątkiem, że anulowania zapewnianego element mechanizmy wykonuje kod proceduralny może prowadzić do efekty uboczne, których wynikiem zanieczyszczenie funkcjonalności). Jednak mimo że XSLT jest skutecznym narzędziem, niektóre jego właściwości nie są optymalne. Na przykład przedstawiając konstrukcje programowania w języku XML sprawia, że kod stosunkowo pełne i w związku z tym trudne w utrzymaniu. Ponadto duże poleganie na rekursji dla sterowanie przepływem może spowodować kod, który jest trudny do odczytania. Aby uzyskać więcej informacji na temat XSLT, zobacz [przekształcenia XSLT](../../../../standard/data/xml/xslt-transformations.md).  
  
 Jednak XSLT okazała się przy użyciu czystego funkcjonalności podejścia do przekształcania XML z jednego kształtu do innej wartości. Czysty funkcjonalności, programowanie za pomocą LINQ to XML przypomina na wiele sposobów XSLT. Jednak narzędzi programistycznych, wprowadzona w składniku LINQ to XML i Visual Basic pozwalają na zapis czystych przekształceń funkcjonalnych, które są bardziej czytelny i łatwy w obsłudze niż XSLT.  
  
## <a name="advantages-of-pure-functions"></a>Korzyści wynikające z czystych funkcji  
 Głównym powodem zaimplementować przekształceń funkcjonalnych jako czystych funkcji jest konfigurowalna czy czystych funkcji: oznacza to, niezależna i bezstanowe. Te cechy Przenieś szereg korzyści, w tym następujące czynności:  
  
- Zwiększenia czytelności i łatwości utrzymania. To ponieważ każda funkcja zaprojektowano w celu wykonania określonego zadania znajduje się jego argumenty. Funkcja nie zależą od dowolnego stanu zewnętrznego.  
  
- Łatwiejsze opracowywanie reiterative. Ponieważ kod jest łatwiejszy do refaktoryzacji, zmiany projektu są często łatwiejsze do wdrożenia. Na przykład załóżmy, że skomplikowaną transformację zapisu, a następnie należy pamiętać, że jakiś kod jest powtarzany kilka razy w transformacji. Jeśli zrefaktoryzujesz przy użyciu czystej metody można wywołać czystego metodę momencie bez martwienia się o efekty uboczne.  
  
- Łatwiejsze testowanie i debugowanie. Ponieważ łatwiej można było przetestować czystych funkcji izolacji, można napisać kod testu, który wywołuje czystą funkcję typowe wartości, przypadki brzegowe prawidłowe i przypadki brzegowe nieprawidłowy.  
  
## <a name="transitioning-for-oop-developers"></a>Przejście dla deweloperów Obiektowo  
 W tradycyjnym zorientowanym obiektowo (Obiektowo), większość programistów są przyzwyczajeni do programowania w stylu imperatywne/procedur. Aby przełączyć się do rozwoju w stylu funkcjonalności czystego, muszą oni wprowadzić przejścia w ich myślenia i ich podejście do programowania.  
  
 Do rozwiązywania problemów, deweloperzy Obiektowo Projektuj hierarchie klasy skupić się na właściwe hermetyzacji i myślą w kategoriach kontraktów klasy. Zachowanie i stan wybierane są kluczowymi czynnikami, a podano funkcji języka, takich jak klasy, interfejsy, dziedziczenia i polimorfizmu, aby rozwiązać te problemy.  
  
 Z kolei programowania funkcjonalnego dochodzi do rozwiązywania problemów obliczeniowych w charakterze ćwiczenia podczas obliczania czystych przekształceń funkcjonalnych kolekcji danych. Programowanie funkcjonalne pozwala uniknąć stan i dane modyfikowalny i zamiast tego wyróżniane aplikacji funkcji.  
  
 Na szczęście języka Visual Basic nie wymaga pełnej przestępnym do programowania funkcyjnego, ponieważ obsługuje ona zarówno imperatywną lub funkcjonalności metody programowania. Deweloper można wybrać, które rozwiązanie jest najbardziej odpowiednie dla danego scenariusza. W rzeczywistości programy często połączyć oba podejścia.  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do czystych przekształceń funkcjonalnych (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/introduction-to-pure-functional-transformations.md)
- [Przekształcenia XSLT](../../../../standard/data/xml/xslt-transformations.md)
- [Refaktoryzacja do czystych funkcji (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/refactoring-into-pure-functions.md)

---
title: Wzorzec projektowy obserwatora
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- IObserver(Of T) interface
- IObservable<T> interface
- IObserver<T> interface
- IObservable(Of T) interface
- observer design pattern [.NET Framework]
ms.assetid: 3680171f-f522-453c-aa4a-54f755a78f88
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 83663a28ac7ae19848552583f2ec39a5e96c7fdc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="observer-design-pattern"></a>Wzorzec projektowy obserwatora
Wzorzec projektowy obserwatora umożliwia subskrybenta do rejestrowania i odbierania powiadomień od dostawcy. Jest to odpowiednie dla dowolnego scenariusz, który wymaga wypychania powiadomień. Definiuje wzorzec *dostawcy* (znanej także jako *podmiotu* lub *według*) i zero, co najmniej jeden *obserwatorów*. Obserwatorów Zarejestruj dostawcę i zawsze, gdy wstępnie zdefiniowanego warunku, zdarzenia lub zmiana stanu występuje, dostawca automatycznie powiadamia wszystkich obserwatorów przez wywołanie metody ich. W tym wywołaniu metody dostawcę można też podać informacje o bieżącym stanie do obserwatorów. W programie .NET Framework wzorzec projektowy obserwatora jest stosowany przez zastosowanie ogólnego <xref:System.IObservable%601?displayProperty=nameWithType> i <xref:System.IObserver%601?displayProperty=nameWithType> interfejsów. Parametr typu ogólnego reprezentuje typ, który zawiera informacje powiadomień.  
  
## <a name="applying-the-pattern"></a>Stosowanie wzorcu  
 Wzorzec projektowy obserwatora jest odpowiedniej dla powiadomień wypychanych na podstawie rozproszonej, ponieważ obsługuje on czyste rozdzielenie dwóch różnych składników lub warstwy aplikacji, takich jak warstwy (logika biznesowa) źródło danych i warstwy interfejsu (wyświetlanie) użytkownika. Można zaimplementować wzorzec zawsze, gdy dostawca używa wywołań zwrotnych do dostarczania klientom przy użyciu bieżących informacji.  
  
 Implementacja wzorca wymaga podania następujących czynności:  
  
-   Dostawca lub temat, który jest obiektem wysyła powiadomienia do obserwatora. Dostawca to klasy lub struktury, która implementuje <xref:System.IObservable%601> interfejsu. Dostawca musi implementować metodę pojedynczego <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType>, który jest wywoływany przez obserwatorów, które chcesz otrzymywać powiadomienia od dostawcy.  
  
-   Obserwatora, który jest obiektem służącą do odbierania powiadomień od dostawcy. Obserwator jest klasy lub struktury, która implementuje <xref:System.IObserver%601> interfejsu. Obserwator musi implementować trzy metody, które są wywoływane przez dostawcę:  
  
    -   <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, która dostarcza obserwatora z informacjami o nowych lub bieżący.  
  
    -   <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, który informuje o obserwatora, który wystąpił błąd.  
  
    -   <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>, co oznacza, że dostawca zakończył wysyłanie powiadomień.  
  
-   Mechanizm, który umożliwia dostawcy śledzić obserwatorów. Zwykle, dostawca używa obiektu kontenera, takich jak <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> obiektu do przechowywania odwołań do <xref:System.IObserver%601> implementacji, które subskrybuje powiadomienia. W tym celu za pomocą kontenera magazynu umożliwia dostawcy w celu obsługi zero, aby nieograniczoną liczbę obserwatorów. Nie zdefiniowano kolejność, w którym obserwatorów otrzymywać powiadomienia; Dostawca będzie mógł użyć dowolnej metody, aby określić kolejność.  
  
-   <xref:System.IDisposable> Implementację, która umożliwia dostawcy usunąć obserwatorów po zakończeniu powiadomień. Odwołanie do odbierania obserwatorów <xref:System.IDisposable> implementację z <xref:System.IObservable%601.Subscribe%2A> metody, dlatego można również wywołać <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> metodę, aby anulować subskrypcję, zanim dostawcy zakończył wysyłanie powiadomień.  
  
-   Obiekt, który zawiera dane, które dostawca wysyła do jego obserwatorów. Typ obiektu odnosi się do parametru typu ogólnego <xref:System.IObservable%601> i <xref:System.IObserver%601> interfejsów. Chociaż ten obiekt może być taka sama jak <xref:System.IObservable%601> implementacji najczęściej jest to typ oddzielne.  
  
> [!NOTE]
>  Oprócz wykonania wzorzec projektowy obserwatora, może Cię zainteresować eksploracji bibliotek, które są tworzone przy użyciu <xref:System.IObservable%601> i <xref:System.IObserver%601> interfejsów. Na przykład [reaktywne rozszerzeń dla platformy .NET (Rx)](http://go.microsoft.com/fwlink/?LinkId=186345) składają się z zestawu metod rozszerzeń i operatory sekwencji standardowe LINQ do obsługi programowania asynchronicznego.  
  
## <a name="implementing-the-pattern"></a>Implementacja wzorca  
 W poniższym przykładzie użyto wzorzec projektowy obserwatora wdrożenia systemu informacji lotnisku bagażu oświadczeń. A `BaggageInfo` klasa dostarcza informacji na temat nadchodzących lotach i carousels, w którym bagażu z każdym locie jest dostępny do pobrania. Jest on wyświetlany w poniższym przykładzie.  
  
 [!code-csharp[Conceptual.ObserverDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/provider.cs#1)]
 [!code-vb[Conceptual.ObserverDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/provider.vb#1)]  
  
 A `BaggageHandler` klasy jest odpowiedzialny za informacje o lotach nadchodzących i bagażu oświadczenia carousels. Wewnętrznie ta funkcja obsługuje dwie kolekcje:  
  
-   `observers`-Kolekcję klientów, którzy będą otrzymywać zaktualizowane informacje.  
  
-   `flights`-Kolekcja lotach i ich carousels przypisane.  
  
 Obie kolekcje są reprezentowane przez ogólny <xref:System.Collections.Generic.List%601> obiektów, które są tworzone w `BaggageHandler` konstruktora klasy. Kod źródłowy `BaggageHandler` klasy przedstawiono w poniższym przykładzie.  
  
 [!code-csharp[Conceptual.ObserverDesignPattern#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/provider.cs#2)]
 [!code-vb[Conceptual.ObserverDesignPattern#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/provider.vb#2)]  
  
 Klienci, w których chcesz otrzymywać zaktualizowane informacje wywołać `BaggageHandler.Subscribe` metody. Jeśli klient nie został wcześniej subskrypcji powiadomień, odniesienie do klienta <xref:System.IObserver%601> implementacji jest dodawany do `observers` kolekcji.  
  
 Przeciążone `BaggageHandler.BaggageStatus` można wywołać metody, aby wskazać, że bagażu z lot zwalnianie lub już nie jest zwalniany. W pierwszym przypadku metody jest przekazywany numer transmitowane, port, z którego pochodzi lot i Karuzela gdzie bagażu jest zwalniany. W drugim przypadku metoda jest przekazany tylko numerze. Dla bagażu, który ma zostać zwolniony, metoda sprawdza czy `BaggageInfo` przekazane do metody informacje istnieje w `flights` kolekcji. Jeśli nie, metoda dodaje informacje i wywołuje każdego obserwatora `OnNext` metody. W przypadku lotach bagażu którego już nie jest zwalniany, metoda sprawdza, czy informacje na ten lot są przechowywane w `flights` kolekcji. Jeśli tak jest, metoda wywołuje metodę każdego obserwatora `OnNext` — metoda i usuwa `BaggageInfo` obiekt z `flights` kolekcji.  
  
 Gdy znalazł lot ostatniego dnia, a jego bagażu zostało przetworzone, `BaggageHandler.LastBaggageClaimed` metoda jest wywoływana. Ta metoda wywołuje każdego obserwatora `OnCompleted` metody, aby wskazać, że zostały wykonane wszystkie powiadomienia, a następnie czyści `observers` kolekcji.  
  
 Dostawcy <xref:System.IObservable%601.Subscribe%2A> metoda zwraca <xref:System.IDisposable> implementację, która umożliwia obserwatorów przestać otrzymywać powiadomienia przed <xref:System.IObserver%601.OnCompleted%2A> metoda jest wywoływana. Kod źródłowy dla tego `Unsubscriber(Of BaggageInfo)` klasy przedstawiono w poniższym przykładzie. Podczas tworzenia wystąpienia klasy w `BaggageHandler.Subscribe` metody jest przekazywany odwołanie do `observers` kolekcji i odwołania do obserwatora, który zostanie dodany do kolekcji. Te odwołania są przypisane do zmiennych lokalnych. Gdy obiektu `Dispose` metoda jest wywoływana, sprawdza, czy obserwatora nadal istnieje w `observers` kolekcji, a jeśli tak, usuwa obserwatora.  
  
 [!code-csharp[Conceptual.ObserverDesignPattern#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/provider.cs#3)]
 [!code-vb[Conceptual.ObserverDesignPattern#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/provider.vb#3)]  
  
 W poniższym przykładzie przedstawiono <xref:System.IObserver%601> wdrożenia o nazwie `ArrivalsMonitor`, która jest podstawową klasę, która wyświetla informacje o bagażu. Informacje są wyświetlane alfabetycznie, nazwą miasta źródłowego. Metody `ArrivalsMonitor` są oznaczone jako `overridable` (w języku Visual Basic) lub `virtual` (w języku C#), dlatego mogą wszystkie być zastąpione przez klasę pochodną.  
  
 [!code-csharp[Conceptual.ObserverDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/observer.cs#4)]
 [!code-vb[Conceptual.ObserverDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/observer.vb#4)]  
  
 `ArrivalsMonitor` Klasa zawiera `Subscribe` i `Unsubscribe` metody. `Subscribe` Metoda umożliwia klasę, aby zapisać <xref:System.IDisposable> implementacji zwrócony przez wywołanie <xref:System.IObservable%601.Subscribe%2A> prywatnej zmiennej. `Unsubscribe` Metoda umożliwia klasę, aby zrezygnować z powiadomień przez wywołanie dostawcy <xref:System.IDisposable.Dispose%2A> implementacji. `ArrivalsMonitor`dostępne są także implementacje <xref:System.IObserver%601.OnNext%2A>, <xref:System.IObserver%601.OnError%2A>, i <xref:System.IObserver%601.OnCompleted%2A> metody. Tylko <xref:System.IObserver%601.OnNext%2A> implementacja zawiera znaczną ilość kodu. Metoda współpracuje z ogólnego prywatne, posortowane, <xref:System.Collections.Generic.List%601> obiekt, który przechowuje informacje o lotniskach pochodzenia w nadchodzących lotach i carousels, na których jest dostępna ich bagażu. Jeśli `BaggageHandler` klasa raportuje nowego odbioru transmitowane <xref:System.IObserver%601.OnNext%2A> implementacji metody dodaje informacje o tym transmitowane do listy. Jeśli `BaggageHandler` klasy raporty, aby transmitowane bagażu został zwolniony, <xref:System.IObserver%601.OnNext%2A> metoda usuwa ten lot z listy. Zawsze, gdy zostaną zmienione, lista jest sortowana i wyświetlane w konsoli.  
  
 Poniżej przedstawiono przykład zawierający punkt wejścia aplikacji, która tworzy `BaggageHandler` klasy oraz dwa wystąpienia `ArrivalsMonitor` klasy i używa `BaggageHandler.BaggageStatus` metody do dodawania i usuwania informacji o nadchodzących lotach. W każdym przypadku obserwatorów otrzymywać aktualizacje i poprawnie wyświetlić informacje o bagażu.  
  
 [!code-csharp[Conceptual.ObserverDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/program.cs#5)]
 [!code-vb[Conceptual.ObserverDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/module1.vb#5)]  
  
## <a name="related-topics"></a>Tematy pokrewne  
  
|Tytuł|Opis|  
|-----------|-----------------|  
|[Wzorzec projektowy obserwatora — najlepsze praktyki](../../../docs/standard/events/observer-design-pattern-best-practices.md)|Opis najlepszych rozwiązań do przyjęcia podczas tworzenia aplikacji, które implementują wzorzec projektowy obserwatora.|  
|[Porady: Implementowanie dostawcy](../../../docs/standard/events/how-to-implement-a-provider.md)|Udostępnia implementację krok dostawcy dla temperatury monitorowania aplikacji.|  
|[Porady: Implementowanie obserwatora](../../../docs/standard/events/how-to-implement-an-observer.md)|Udostępnia implementację krok obserwatora dla temperatury monitorowania aplikacji.|

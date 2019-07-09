---
title: Wzorzec projektowy obserwatora
ms.date: 03/30/2017
ms.technology: dotnet-standard
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 06dbc4b7124aa873fd8471794fa25b0f47f8ce3d
ms.sourcegitcommit: d6e27023aeaffc4b5a3cb4b88685018d6284ada4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2019
ms.locfileid: "67663575"
---
# <a name="observer-design-pattern"></a>Wzorzec projektowy obserwatora

Wzorzec projektowy obserwatora umożliwia subskrybentom zarejestrowanie i otrzymywanie powiadomienia od dostawcy. Jest ona odpowiednia dla wszystkich scenariuszy, które wymaga powiadomień wypychanych na podstawie. Definiuje wzorzec *dostawcy* (znany także jako *podmiotu* lub *obserwowalnymi*) i zero, co najmniej jeden *obserwatorów*. Obserwatorzy zarejestrowanie dostawcy i zawsze wtedy, gdy wstępnie zdefiniowanego warunku zdarzenia lub zmianę stanu występuje, dostawca automatycznie powiadamia, wszystkich obserwatorów przez wywołania ich metod. W tym wywołaniu metody dostawcy mogą także podać bieżące informacje o stanie do obserwatorów. W .NET Framework, wzorzec projektowy obserwatora jest stosowany przez zaimplementowanie ogólnego <xref:System.IObservable%601?displayProperty=nameWithType> i <xref:System.IObserver%601?displayProperty=nameWithType> interfejsów. Parametr typu ogólnego reprezentuje typ, który dostarcza informacji powiadomień.

## <a name="applying-the-pattern"></a>Stosowania wzorca

Wzorzec projektowy obserwatora jest odpowiedniej dla powiadomień wypychanych na podstawie rozproszonej, ponieważ obsługuje on czystą separacji między dwa różne składniki lub warstw aplikacji, takich jak warstwy (logika biznesowa) źródło danych i warstwy (wyświetlanie) interfejsu użytkownika. Wzorzec można zaimplementować w każdym przypadku, gdy dostawca używa wywołań zwrotnych do dostarczania klientom przy użyciu bieżących informacji.

Implementacja wzorca wymaga, należy dostarczyć następujące elementy:

- Dostawca lub temat, który jest obiektem, która wysyła powiadomienia do obserwatorów. Dostawca to klasa lub struktura, która implementuje <xref:System.IObservable%601> interfejsu. Dostawca musi implementować jedną metodę <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType>, która jest wywoływana przez obserwatorów, które chcesz otrzymywać powiadomienia od dostawcy.

- Obserwatora, który jest obiektem, który odbiera powiadomienia od dostawcy. Obserwator jest klasa lub struktura, która implementuje <xref:System.IObserver%601> interfejsu. Obserwator musi implementować trzy metody, które są wywoływane przez dostawcę:

  - <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, który dostarcza obserwatora przy użyciu nowych lub bieżące informacje.

  - <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, która informuje obserwatora, który wystąpił błąd.

  - <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>, co oznacza, że dostawca zakończył wysyłanie powiadomień.

- Mechanizm, który umożliwia dostawcy do śledzenia obserwatorów. Zwykle, dostawca używa obiektu kontenera, takich jak <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> obiekt, do przechowywania odwołań do <xref:System.IObserver%601> implementacji, które subskrybuje powiadomienia. W tym celu za pomocą kontenera magazynu umożliwia dostawcy w celu obsługi zero do nieograniczonej liczby obserwatorów. Nie zdefiniowano kolejność, w którym obserwatorów otrzymywać powiadomienia o; Dostawca jest bezpłatna, można użyć dowolnej metody, aby określić kolejność.

- <xref:System.IDisposable> Implementację, która umożliwia dostawcy, po zakończeniu powiadomienia, Usuń obserwatorów. Obserwatorzy otrzymywać odwołanie do <xref:System.IDisposable> implementację z <xref:System.IObservable%601.Subscribe%2A> metody, dzięki czemu można również wywołać <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> metodę, aby anulować subskrypcję, zanim dostawcy zakończył wysyłanie powiadomień.

- Obiekt, który zawiera dane, które dostawca wysyła do jego obserwatorów. Typ tego obiektu odnosi się do parametru typu ogólnego <xref:System.IObservable%601> i <xref:System.IObserver%601> interfejsów. Mimo że ten obiekt może być taka sama jak <xref:System.IObservable%601> implementacji najczęściej jest to typ oddzielne.

> [!NOTE]
> Oprócz wykonywania po wzorcu projektowania obserwatora, może być zainteresowany Eksplorowanie bibliotek, które zostały utworzone przy użyciu <xref:System.IObservable%601> i <xref:System.IObserver%601> interfejsów. Na przykład [Reactive Extensions dla platformy .NET (Rx)](https://docs.microsoft.com/previous-versions/dotnet/reactive-extensions/hh242985(v=vs.103)) składają się z zestawu metod rozszerzeń i operatorów standardowej kolejności LINQ do obsługi asynchronicznego programowania.

## <a name="implementing-the-pattern"></a>Implementacja wzorca

W poniższym przykładzie użyto wzorzec projektowy obserwatora do implementowania systemu informacji Kuwejcie bagażu oświadczenia. Element `BaggageInfo` klasy zawiera informacje o nadchodzących lotów oraz karuzeli, w którym bagażu z każdym locie jest dostępny do pobrania. Jest on wyświetlany w poniższym przykładzie.

[!code-csharp[Conceptual.ObserverDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/provider.cs#1)]
[!code-vb[Conceptual.ObserverDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/provider.vb#1)]

A `BaggageHandler` klasa jest odpowiedzialna za odbieranie informacji o nadchodzących lotów i bagażu oświadczenia karuzeli. Wewnętrznie obsługuje dwie kolekcje:

- `observers` -Kolekcję klientów, którzy będą otrzymywać aktualne informacje.

- `flights` -Zbiór lotów i ich przypisanej karuzeli.

Obie kolekcje są reprezentowane przez ogólny <xref:System.Collections.Generic.List%601> obiektów, które są tworzone w `BaggageHandler` konstruktora klasy. Kod źródłowy `BaggageHandler` klasy przedstawiono w poniższym przykładzie.

[!code-csharp[Conceptual.ObserverDesignPattern#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/provider.cs#2)]
[!code-vb[Conceptual.ObserverDesignPattern#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/provider.vb#2)]

Klienci, w których chcesz otrzymywać zaktualizowane informacje wywołań `BaggageHandler.Subscribe` metody. Jeśli klient nie ma wcześniej subskrypcji powiadomień, odniesienie do klienta <xref:System.IObserver%601> implementacja jest dodawany do `observers` kolekcji.

Przeciążone `BaggageHandler.BaggageStatus` można wywołać metody, aby wskazywać, że bagażu z lotu jest zwalniany lub nie jest już zwalnianie modułu. W pierwszym przypadku do metody jest przekazywana numer lotu, port, z którego pochodzi lotu i karuzeli gdzie bagażu zwalnianie modułu. W drugim przypadku do metody jest przekazywana numer lotu. Dla bagażu, który jest zwolniony, kontrole metoda czy `BaggageInfo` informacje przekazywane do metody istnieje w `flights` kolekcji. Jeśli nie, metoda dodaje te informacje, a następnie wywołuje każdego obserwatora `OnNext` metody. Dla którego bagażu już Trwa zwalnianie lotów, metoda sprawdza, czy informacje na ten lot są przechowywane w `flights` kolekcji. Jeśli tak jest, metoda wywołuje każdego obserwatora `OnNext` metody i usuwa `BaggageInfo` obiektu z `flights` kolekcji.

Podczas lotu ostatniego dnia znalazł i przetworzeniu jego bagażu `BaggageHandler.LastBaggageClaimed` metoda jest wywoływana. Ta metoda wywołuje każdego obserwatora `OnCompleted` metodę w celu wskazania, że zostały wykonane wszystkie powiadomienia, a następnie czyści `observers` kolekcji.

Dostawcy <xref:System.IObservable%601.Subscribe%2A> metoda zwraca <xref:System.IDisposable> implementację, która umożliwia obserwatorów na zatrzymanie otrzymywania powiadomienia przed <xref:System.IObserver%601.OnCompleted%2A> metoda jest wywoływana. Kod źródłowy dla tego `Unsubscriber(Of BaggageInfo)` klasy przedstawiono w poniższym przykładzie. Podczas tworzenia wystąpienia klasy w `BaggageHandler.Subscribe` metody jest przekazywana odwołanie do `observers` kolekcji i odwołania do obserwatora, który jest dodawany do kolekcji. Te odwołania są przypisane do zmiennych lokalnych. Gdy obiekt `Dispose` metoda jest wywoływana, sprawdza, czy obserwatora nadal istnieje w `observers` kolekcji i, jeśli istnieje, usuwa obserwatora.

[!code-csharp[Conceptual.ObserverDesignPattern#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/provider.cs#3)]
[!code-vb[Conceptual.ObserverDesignPattern#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/provider.vb#3)]

W poniższym przykładzie przedstawiono <xref:System.IObserver%601> wdrożenia o nazwie `ArrivalsMonitor`, czyli klasy podstawowej, która wyświetla informacje o bagażu. Informacje są wyświetlane w kolejności alfabetycznej, według nazwy miasta źródłowego. Metody `ArrivalsMonitor` są oznaczone jako `overridable` (w języku Visual Basic) lub `virtual` (w C#), dzięki czemu mogą wszystkie być zastąpione przez klasę pochodną.

[!code-csharp[Conceptual.ObserverDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/observer.cs#4)]
[!code-vb[Conceptual.ObserverDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/observer.vb#4)]

`ArrivalsMonitor` Klasa zawiera `Subscribe` i `Unsubscribe` metody. `Subscribe` Metoda umożliwia klasę, aby zapisać <xref:System.IDisposable> zwracany przez wywołanie do implementacji <xref:System.IObservable%601.Subscribe%2A> do prywatnej zmiennej. `Unsubscribe` Metoda umożliwia klasę, aby zrezygnować z powiadomień przez wywołanie metody dostawcy <xref:System.IDisposable.Dispose%2A> implementacji. `ArrivalsMonitor` zapewnia również wdrożeń <xref:System.IObserver%601.OnNext%2A>, <xref:System.IObserver%601.OnError%2A>, i <xref:System.IObserver%601.OnCompleted%2A> metody. Tylko <xref:System.IObserver%601.OnNext%2A> implementacja zawiera znacząca ilość kodu. Metoda współpracuje z ogólnego prywatnych, posortowany, <xref:System.Collections.Generic.List%601> obiekt, który przechowuje informacje o lotniskach pochodzenia nadchodzących lotów i karuzeli, na których jest dostępna ich bagażu. Jeśli `BaggageHandler` klasy zgłasza nowy przybyciu locie, <xref:System.IObserver%601.OnNext%2A> implementacji metody dodaje informacje o tym lot do listy. Jeśli `BaggageHandler` klasy raporty, czy podczas lotu bagażu został zwolniony, <xref:System.IObserver%601.OnNext%2A> metoda usuwa ten lot z listy. Zawsze wtedy, gdy zostanie zmienione, lista jest sortowana i wyświetlana w konsoli.

Poniżej przedstawiono przykład zawierający punkt wejścia aplikacji, która tworzy wystąpienie `BaggageHandler` klasy, a także dwa wystąpienia `ArrivalsMonitor` klasy i używa `BaggageHandler.BaggageStatus` metody dodawania i usuwania informacji o nadchodzących lotów. W każdym przypadku obserwatorów otrzymywania aktualizacji i poprawnie wyświetlić informacje o bagażu.

[!code-csharp[Conceptual.ObserverDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/program.cs#5)]
[!code-vb[Conceptual.ObserverDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/module1.vb#5)]

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Wzorzec projektowy obserwatora — najlepsze rozwiązania](../../../docs/standard/events/observer-design-pattern-best-practices.md)|Zawiera opis najlepszych rozwiązań, aby przyjąć podczas tworzenia aplikacji, które implementują wzorzec projektowy obserwatora.|
|[Instrukcje: Implementowanie dostawcy](../../../docs/standard/events/how-to-implement-a-provider.md)|Zapewnia instrukcje krok po kroku implementacji dostawcy dla temperatury monitorowania aplikacji.|
|[Instrukcje: Implementowanie obserwatora](../../../docs/standard/events/how-to-implement-an-observer.md)|Zawiera instrukcje krok po kroku wdrożenia obserwatora dla temperatury monitorowania aplikacji.|

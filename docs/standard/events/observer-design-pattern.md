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
ms.openlocfilehash: 817337cec604a431f9f7d4eacb04378ee0d3c227
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "73131575"
---
# <a name="observer-design-pattern"></a>Wzorzec projektowy obserwatora

Wzorzec projektowania obserwatora umożliwia subskrybentowi rejestrowanie się i otrzymywanie powiadomień od dostawcy. Jest odpowiedni dla każdego scenariusza, który wymaga powiadomienia opartego na wypychaniu. Wzorzec definiuje *dostawcę* (znanego również jako *podmiot* lub *obserwowalny)* i zero, jednego lub więcej *obserwatorów*. Obserwatorzy rejestrują się u dostawcy i zawsze, gdy występuje wstępnie zdefiniowany warunek, zdarzenie lub zmiana stanu, dostawca automatycznie powiadamia wszystkich obserwatorów, wywołując jedną z ich metod. W tym wywołaniu metody dostawca może również podać bieżące informacje o stanie obserwatorom. W .NET Framework wzorca projektowania obserwatora jest <xref:System.IObservable%601?displayProperty=nameWithType> <xref:System.IObserver%601?displayProperty=nameWithType> stosowany przez implementowanie ogólnych i interfejsów. Parametr typu ogólnego reprezentuje typ, który zawiera informacje o powiadomieniu.

## <a name="applying-the-pattern"></a>Stosowanie wzoru

Wzorzec projektu obserwatora jest odpowiedni dla rozproszonych powiadomień opartych na wypychaniu, ponieważ obsługuje czyste oddzielenie dwóch różnych składników lub warstw aplikacji, takich jak warstwa źródła danych (logika biznesowa) i warstwa interfejsu użytkownika (wyświetlanie). Wzorzec można zaimplementować zawsze, gdy dostawca używa wywołań zwrotu do dostarczania swoim klientom bieżących informacji.

Implementowanie wzorca wymaga podania następujących elementów:

- Dostawca lub temat, który jest obiektem, który wysyła powiadomienia do obserwatorów. Dostawca jest klasą lub strukturą, która implementuje <xref:System.IObservable%601> interfejs. Dostawca musi zaimplementować <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType>jedną metodę, która jest wywoływana przez obserwatorów, którzy chcą otrzymywać powiadomienia od dostawcy.

- Obserwator, który jest obiektem, który odbiera powiadomienia od dostawcy. Obserwator jest klasą lub strukturą, która implementuje <xref:System.IObserver%601> interfejs. Obserwator musi wdrożyć trzy metody, z których wszystkie są wywoływane przez dostawcę:

  - <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, który dostarcza obserwatorowi nowych lub aktualnych informacji.

  - <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, który informuje obserwatora o wystąpieniu błędu.

  - <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>, co oznacza, że dostawca zakończył wysyłanie powiadomień.

- Mechanizm, który umożliwia dostawcy śledzenie obserwatorów. Zazwyczaj dostawca używa obiektu kontenera, takich <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> jak obiekt, do <xref:System.IObserver%601> przechowywania odwołań do implementacji, które subskrybowane powiadomień. Przy użyciu kontenera magazynu w tym celu umożliwia dostawcy do obsługi zero do nieograniczonej liczby obserwatorów. Kolejność, w jakiej obserwatorzy otrzymują powiadomienia, nie jest zdefiniowana; dostawca może swobodnie korzystać z dowolnej metody do określenia zamówienia.

- Implementacja, <xref:System.IDisposable> która umożliwia dostawcy, aby usunąć obserwatorów po zakończeniu powiadamiania. Obserwatorzy otrzymują odwołanie <xref:System.IDisposable> do <xref:System.IObservable%601.Subscribe%2A> implementacji z metody, <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> dzięki czemu mogą również wywołać metodę rezygnacji z subskrypcji, zanim dostawca zakończy wysyłanie powiadomień.

- Obiekt, który zawiera dane, które dostawca wysyła do swoich obserwatorów. Typ tego obiektu odpowiada parametrtypu ogólnego <xref:System.IObservable%601> i <xref:System.IObserver%601> interfejsów. Mimo że ten obiekt może <xref:System.IObservable%601> być taka sama jak implementacji, najczęściej jest to typ oddzielny.

> [!NOTE]
> Oprócz implementacji wzorca projektowania obserwatora może być zainteresowany eksplorowania bibliotek, które są zbudowane przy użyciu <xref:System.IObservable%601> i <xref:System.IObserver%601> interfejsów. Na przykład [rozszerzenia reaktywne dla .NET (Rx)](https://docs.microsoft.com/previous-versions/dotnet/reactive-extensions/hh242985(v=vs.103)) składają się z zestawu metod rozszerzenia i standardowych operatorów sekwencji LINQ do obsługi programowania asynchronicznego.

## <a name="implementing-the-pattern"></a>Implementowanie wzorca

W poniższym przykładzie użyto wzorca projektowania obserwatora do wdrożenia systemu informacji o odbiorze bagażu na lotnisku. Klasa `BaggageInfo` dostarcza informacji o przylotach i karuzelach, w których bagaż z każdego lotu jest dostępny do odbioru. Jest on pokazany w poniższym przykładzie.

[!code-csharp[Conceptual.ObserverDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/provider.cs#1)]
[!code-vb[Conceptual.ObserverDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/provider.vb#1)]

Klasa `BaggageHandler` jest odpowiedzialna za otrzymywanie informacji o przylotach i karuzelach odbioru bagażu. Wewnętrznie utrzymuje dwie kolekcje:

- `observers`- Zbiór klientów, którzy otrzymają zaktualizowane informacje.

- `flights`- Zbiór lotów i ich przydzielone karuzele.

Obie kolekcje są <xref:System.Collections.Generic.List%601> reprezentowane przez obiekty ogólne, `BaggageHandler` które są tworzone w konstruktorze klasy. Kod źródłowy `BaggageHandler` dla klasy jest pokazany w poniższym przykładzie.

[!code-csharp[Conceptual.ObserverDesignPattern#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/provider.cs#2)]
[!code-vb[Conceptual.ObserverDesignPattern#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/provider.vb#2)]

Klienci, którzy chcą otrzymywać `BaggageHandler.Subscribe` zaktualizowane informacje, wywołują metodę. Jeśli klient wcześniej nie subskrybował powiadomień, odwołanie <xref:System.IObserver%601> do implementacji `observers` klienta jest dodawany do kolekcji.

Przeciążonej `BaggageHandler.BaggageStatus` metody można wywołać, aby wskazać, że bagaż z lotu jest rozładowywany lub nie jest już rozładowywany. W pierwszym przypadku metoda jest przekazywana numer lotu, lotnisko, z którego pochodzi lot, oraz karuzela, w której bagaż jest rozładowywany. W drugim przypadku metoda jest przekazywana tylko numer lotu. Dla bagażu, który jest rozładowywany, metoda sprawdza, czy `BaggageInfo` informacje przekazywane do metody istnieje w `flights` kolekcji. Jeśli tak nie jest, metoda dodaje informacje i `OnNext` wywołuje metodę każdego obserwatora. W przypadku lotów, których bagaż nie jest już rozładowywany, `flights` metoda sprawdza, czy informacje o tym locie są przechowywane w kolekcji. Jeśli tak, metoda wywołuje metodę `OnNext` każdego obserwatora `BaggageInfo` i usuwa `flights` obiekt z kolekcji.

Gdy ostatni lot dnia wylądował, a jego bagaż został `BaggageHandler.LastBaggageClaimed` przetworzony, metoda jest wywoływana. Ta metoda wywołuje metodę `OnCompleted` każdego obserwatora, aby wskazać, że wszystkie `observers` powiadomienia zostały zakończone, a następnie czyści kolekcję.

<xref:System.IObservable%601.Subscribe%2A> Metoda dostawcy zwraca <xref:System.IDisposable> implementację, która umożliwia obserwatorom zaprzestanie odbierania powiadomień przed wywołaniem <xref:System.IObserver%601.OnCompleted%2A> metody. Kod źródłowy `Unsubscriber(Of BaggageInfo)` dla tej klasy jest pokazany w poniższym przykładzie. Gdy klasa jest tworzone w `BaggageHandler.Subscribe` metodzie, jest przekazywana `observers` odwołanie do kolekcji i odwołanie do obserwatora, który jest dodawany do kolekcji. Odwołania te są przypisane do zmiennych lokalnych. Gdy `Dispose` wywoływana jest metoda obiektu, sprawdza, czy obserwator `observers` nadal istnieje w kolekcji, a jeśli tak, usuwa obserwatora.

[!code-csharp[Conceptual.ObserverDesignPattern#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/provider.cs#3)]
[!code-vb[Conceptual.ObserverDesignPattern#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/provider.vb#3)]

Poniższy przykład zawiera <xref:System.IObserver%601> implementację o nazwie `ArrivalsMonitor`, która jest klasą podstawową, która wyświetla informacje o odbiorze bagażu. Informacje są wyświetlane alfabetycznie według nazwy miasta pochodzenia. Metody `ArrivalsMonitor` są oznaczone jako `overridable` (w języku `virtual` Visual Basic) lub (w języku C#), dzięki czemu wszystkie mogą być zastąpione przez klasę pochodną.

[!code-csharp[Conceptual.ObserverDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/observer.cs#4)]
[!code-vb[Conceptual.ObserverDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/observer.vb#4)]

Klasa `ArrivalsMonitor` zawiera `Subscribe` i `Unsubscribe` metody. Metoda `Subscribe` umożliwia klasie zapisać <xref:System.IDisposable> implementacji zwrócone przez <xref:System.IObservable%601.Subscribe%2A> wywołanie do zmiennej prywatnej. Metoda `Unsubscribe` umożliwia klasy zrezygnować z powiadomień, wywołując <xref:System.IDisposable.Dispose%2A> implementację dostawcy. `ArrivalsMonitor`zapewnia również <xref:System.IObserver%601.OnNext%2A>implementacje <xref:System.IObserver%601.OnError%2A>, <xref:System.IObserver%601.OnCompleted%2A> i metody. Tylko <xref:System.IObserver%601.OnNext%2A> implementacja zawiera znaczną ilość kodu. Metoda ta działa z prywatnym, <xref:System.Collections.Generic.List%601> posortowanym, ogólnym obiektem, który przechowuje informacje o portach lotniczych pochodzenia dla lotów przylatujących i karuzelach, na których dostępny jest ich bagaż. Jeśli `BaggageHandler` klasa zgłasza nowy lot, <xref:System.IObserver%601.OnNext%2A> implementacja metody dodaje informacje o tym locie do listy. Jeśli `BaggageHandler` klasa zgłasza, że bagaż lotu został rozładowany, <xref:System.IObserver%601.OnNext%2A> metoda usuwa ten lot z listy. Za każdym razem, gdy zostanie winna zmiana, lista jest sortowana i wyświetlana w konsoli.

Poniższy przykład zawiera punkt wejścia aplikacji, który `BaggageHandler` tworzy klasę, a także `ArrivalsMonitor` dwa wystąpienia `BaggageHandler.BaggageStatus` klasy i używa metody do dodawania i usuwania informacji o przylatujących lotów. W każdym przypadku obserwatorzy otrzymują aktualizacje i poprawnie wyświetlają informacje o reklamacji bagażu.

[!code-csharp[Conceptual.ObserverDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/program.cs#5)]
[!code-vb[Conceptual.ObserverDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/module1.vb#5)]

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Wzorzec projektowy obserwatora — Najlepsze praktyki](../../../docs/standard/events/observer-design-pattern-best-practices.md)|Opisuje najlepsze rozwiązania do przyjęcia podczas tworzenia aplikacji, które implementują wzorzec projektowania obserwatora.|
|[Instrukcje: Implementowanie dostawcy](../../../docs/standard/events/how-to-implement-a-provider.md)|Zapewnia implementację krok po kroku dostawcy dla aplikacji do monitorowania temperatury.|
|[Instrukcje: Implementowanie obserwatora](../../../docs/standard/events/how-to-implement-an-observer.md)|Zapewnia implementację krok po kroku obserwatora dla aplikacji do monitorowania temperatury.|

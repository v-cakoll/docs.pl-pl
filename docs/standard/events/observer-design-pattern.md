---
title: Wzorzec projektowy obserwatora
description: Dowiedz się więcej na temat wzorca projektowego obserwatora w programie .NET. Ten wzorzec umożliwia subskrybentowi zarejestrowanie się w usłudze i otrzymywanie powiadomień od dostawcy.
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
ms.openlocfilehash: 4edcd2645b28095f4bd18f4918b9afa5c893bd39
ms.sourcegitcommit: 7137e12f54c4e83a94ae43ec320f8cf59c1772ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2020
ms.locfileid: "84662735"
---
# <a name="observer-design-pattern"></a>Wzorzec projektowy obserwatora

Wzorzec projektowy obserwatora umożliwia subskrybentowi zarejestrowanie się w usłudze i otrzymywanie powiadomień od dostawcy. Jest to odpowiednie dla każdego scenariusza wymagającego powiadomień wypychanych. Wzorzec definiuje *dostawcę* (znanego również jako *temat* lub *zauważalny*) i zero, jeden lub więcej *obserwatorów*. Obserwatorzy rejestrują się u dostawcy i za każdym razem, gdy występuje wstępnie zdefiniowany warunek, zdarzenie lub zmiana stanu, dostawca automatycznie powiadamia o wszystkich Obserwatorach, wywołując jedną z metod. W przypadku tego wywołania metody dostawca może również podać informacje o bieżącym stanie dla obserwatorów. W .NET Framework Wzorzec projektowy obserwatora jest stosowany przez implementację rodzajowego <xref:System.IObservable%601?displayProperty=nameWithType> i <xref:System.IObserver%601?displayProperty=nameWithType> interfejsów. Parametr typu ogólnego reprezentuje typ, który zawiera informacje o powiadomieniach.

## <a name="applying-the-pattern"></a>Stosowanie wzorca

Wzorzec projektowy obserwatora jest odpowiedni dla rozproszonych powiadomień opartych na wypychaniu, ponieważ obsługuje czyste rozdzielenie między dwoma różnymi składnikami lub warstwami aplikacji, takimi jak warstwa źródła danych (logika biznesowa) i warstwa interfejsu użytkownika (Display). Wzorzec może być implementowany za każdym razem, gdy dostawca używa wywołań zwrotnych w celu dostarczenia klientom bieżących informacji.

Implementacja wzorca wymaga podania następujących danych:

- Dostawca lub podmiot, który jest obiektem, który wysyła powiadomienia do obserwatorów. Dostawca jest klasą lub strukturą implementującą <xref:System.IObservable%601> interfejs. Dostawca musi zaimplementować pojedynczą metodę, <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType> która jest wywoływana przez obserwatorów, którzy chcą otrzymywać powiadomienia od dostawcy.

- Obserwator, który jest obiektem, który odbiera powiadomienia od dostawcy. Obserwator jest klasą lub strukturą, która implementuje <xref:System.IObserver%601> interfejs. Obserwator musi zaimplementować trzy metody, z których wszystkie są wywoływane przez dostawcę:

  - <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, która udostępnia obserwatorowi nowe lub bieżące informacje.

  - <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, który informuje obserwatora o wystąpieniu błędu.

  - <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>, co oznacza, że dostawca zakończył wysyłanie powiadomień.

- Mechanizm, który umożliwia dostawcy śledzić obserwatorów. Zazwyczaj Dostawca używa obiektu kontenera, takiego jak <xref:System.Collections.Generic.List%601?displayProperty=nameWithType> obiekt, do przechowywania odwołań do <xref:System.IObserver%601> implementacji subskrybowanych do powiadomień. Użycie w tym celu kontenera magazynu pozwala dostawcy obsłużyć zero do nieograniczonej liczby obserwatorów. Kolejność, w której obserwatorzy otrzymują powiadomienia, nie jest zdefiniowana; Dostawca jest bezpłatny, aby określić kolejność przy użyciu dowolnej metody.

- <xref:System.IDisposable>Implementacja, która umożliwia dostawcy usuwanie obserwatorów po zakończeniu powiadamiania. Obserwatorzy otrzymują odwołanie do <xref:System.IDisposable> implementacji z <xref:System.IObservable%601.Subscribe%2A> metody, więc mogą również wywołać <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> metodę, aby anulować subskrypcję, zanim dostawca zakończył wysyłanie powiadomień.

- Obiekt, który zawiera dane wysyłane przez dostawcę do obserwatorów. Typ tego obiektu odpowiada parametrowi typu ogólnego <xref:System.IObservable%601> <xref:System.IObserver%601> interfejsów i. Chociaż ten obiekt może być taki sam jak <xref:System.IObservable%601> implementacja, najczęściej jest to oddzielny typ.

> [!NOTE]
> Oprócz wdrożenia wzorca projektowego obserwatora, warto zapoznać się z bibliotekami utworzonymi przy użyciu <xref:System.IObservable%601> <xref:System.IObserver%601> interfejsów i. Na przykład [reaktywne rozszerzenia dla platformy .NET (RX)](https://docs.microsoft.com/previous-versions/dotnet/reactive-extensions/hh242985(v=vs.103)) składają się z zestawu metod rozszerzających i operatorów standardowej sekwencji LINQ do obsługi programowania asynchronicznego.

## <a name="implementing-the-pattern"></a>Implementowanie wzorca

W poniższym przykładzie zastosowano Wzorzec projektowy obserwatora do zaimplementowania systemu informacji o zaroście bagażu lotniska. `BaggageInfo`Klasa zawiera informacje na temat przybycia lotów i karuzeli, w przypadku których bagaż z każdego lotu jest dostępny do odbioru. Pokazano to w poniższym przykładzie.

[!code-csharp[Conceptual.ObserverDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/provider.cs#1)]
[!code-vb[Conceptual.ObserverDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/provider.vb#1)]

`BaggageHandler`Klasa jest odpowiedzialna za otrzymywanie informacji na temat docierających lotów i bagażów roszczeń. Wewnętrznie obsługuje dwie kolekcje:

- `observers`— Kolekcja klientów, którzy będą otrzymywać zaktualizowane informacje.

- `flights`-Kolekcja lotów i przypisane do nich karuzeli.

Obie kolekcje są reprezentowane przez <xref:System.Collections.Generic.List%601> obiekty ogólne, które są tworzone w `BaggageHandler` konstruktorze klasy. Kod źródłowy `BaggageHandler` klasy jest przedstawiony w poniższym przykładzie.

[!code-csharp[Conceptual.ObserverDesignPattern#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/provider.cs#2)]
[!code-vb[Conceptual.ObserverDesignPattern#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/provider.vb#2)]

Klienci, którzy chcą otrzymywać zaktualizowane informacje, wywołują `BaggageHandler.Subscribe` metodę. Jeśli klient nie zasubskrybował wcześniej powiadomień, <xref:System.IObserver%601> do kolekcji zostanie dodany odwołanie do implementacji klienta `observers` .

`BaggageHandler.BaggageStatus`Można wywołać przeciążoną metodę, aby wskazać, że bagaż z lotu jest zwalniany lub nie jest już zwolniony. W pierwszym przypadku metoda jest przenoszona jako numer lotu, Port lotniczy, z którego pochodzi lot, oraz karuzela, w której jest zwalniany bagaż. W drugim przypadku metoda jest przenoszona tylko do numeru lotu. W przypadku odciążania bagażu Metoda sprawdza, czy `BaggageInfo` informacje przekazane do metody istnieją w `flights` kolekcji. Jeśli tak nie jest, Metoda dodaje informacje i wywołuje każdą metodę obserwatora `OnNext` . W przypadku lotów, których bagaż nie jest już zwolniony, Metoda sprawdza, czy informacje o tym locie są przechowywane w `flights` kolekcji. Jeśli tak jest, metoda wywołuje każdą metodę obserwatora `OnNext` i usuwa `BaggageInfo` obiekt z `flights` kolekcji.

Gdy upłynął czas użytkowania ostatniego lotu dnia i jego bagaż został przetworzony, `BaggageHandler.LastBaggageClaimed` wywoływana jest metoda. Ta metoda wywołuje każdą metodę obserwatora `OnCompleted` , aby wskazać, że wszystkie powiadomienia zostały ukończone, a następnie czyści `observers` kolekcję.

<xref:System.IObservable%601.Subscribe%2A>Metoda dostawcy zwraca <xref:System.IDisposable> implementację, która umożliwia obserwatorom zaprzestanie otrzymywania powiadomień przed <xref:System.IObserver%601.OnCompleted%2A> wywołaniem metody. Kod źródłowy dla tej `Unsubscriber(Of BaggageInfo)` klasy jest przedstawiony w poniższym przykładzie. Gdy Klasa jest tworzona w `BaggageHandler.Subscribe` metodzie, zostaje przeniesiona odwołanie do `observers` kolekcji i odwołanie do obserwatora, który jest dodawany do kolekcji. Te odwołania są przypisywane do zmiennych lokalnych. Gdy `Dispose` wywoływana jest metoda obiektu, sprawdza, czy obserwator nadal istnieje w `observers` kolekcji i, jeśli tak, usuwa obserwatora.

[!code-csharp[Conceptual.ObserverDesignPattern#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/provider.cs#3)]
[!code-vb[Conceptual.ObserverDesignPattern#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/provider.vb#3)]

W poniższym przykładzie przedstawiono <xref:System.IObserver%601> implementację o nazwie `ArrivalsMonitor` , która jest klasą bazową, która wyświetla informacje o poświadczeniu o bagażu. Informacje są wyświetlane alfabetycznie według nazwy miejscowości źródłowej. Metody `ArrivalsMonitor` są oznaczone jako `overridable` (w Visual Basic) lub `virtual` (w języku C#), więc można je przesłaniać przez klasę pochodną.

[!code-csharp[Conceptual.ObserverDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/observer.cs#4)]
[!code-vb[Conceptual.ObserverDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/observer.vb#4)]

`ArrivalsMonitor`Klasa zawiera `Subscribe` `Unsubscribe` metody i. `Subscribe`Metoda umożliwia klasie zapisywanie <xref:System.IDisposable> implementacji zwróconej przez wywołanie do <xref:System.IObservable%601.Subscribe%2A> zmiennej prywatnej. `Unsubscribe`Metoda umożliwia klasy anulowanie subskrypcji powiadomień przez wywołanie <xref:System.IDisposable.Dispose%2A> implementacji dostawcy. `ArrivalsMonitor`zawiera również implementacje <xref:System.IObserver%601.OnNext%2A> metod, <xref:System.IObserver%601.OnError%2A> , i <xref:System.IObserver%601.OnCompleted%2A> . Tylko <xref:System.IObserver%601.OnNext%2A> implementacja zawiera znaczną ilość kodu. Metoda działa z prywatnym, posortowanym obiektem ogólnym, <xref:System.Collections.Generic.List%601> który utrzymuje informacje o portach lotniczych pochodzenia dla docierających lotów i karuzeli, na których jest dostępny bagaż. Jeśli `BaggageHandler` Klasa zgłasza nowe nadejście lotu, <xref:System.IObserver%601.OnNext%2A> Implementacja metody dodaje informacje o tym locie do listy. Jeśli `BaggageHandler` Klasa zgłasza, że bagaż pracownika został zwolniony, <xref:System.IObserver%601.OnNext%2A> Metoda usuwa ten lot z listy. Za każdym razem, gdy zostanie wprowadzona zmiana, lista zostanie posortowana i wyświetlona w konsoli programu.

Poniższy przykład zawiera punkt wejścia aplikacji, który tworzy wystąpienie klasy, `BaggageHandler` a także dwa wystąpienia `ArrivalsMonitor` klasy, i używa `BaggageHandler.BaggageStatus` metody do dodawania i usuwania informacji na temat przybycia lotów. W każdym przypadku obserwatorzy odbierają aktualizacje i poprawnie wyświetlają informacje o postawie bagażu.

[!code-csharp[Conceptual.ObserverDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/program.cs#5)]
[!code-vb[Conceptual.ObserverDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/module1.vb#5)]

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Wzorzec projektowy obserwatora — Najlepsze praktyki](observer-design-pattern-best-practices.md)|W tym artykule opisano najlepsze rozwiązania, które należy podjąć podczas opracowywania aplikacji, które implementują Wzorzec projektowy obserwatora.|
|[Instrukcje: implementowanie dostawcy](how-to-implement-a-provider.md)|Zapewnia implementację krok po kroku dostawcy dla aplikacji monitorującej temperaturę.|
|[Instrukcje: implementowanie obserwatora](how-to-implement-an-observer.md)|Zawiera implementację krok po kroku obserwatora dla aplikacji monitorującej temperaturę.|

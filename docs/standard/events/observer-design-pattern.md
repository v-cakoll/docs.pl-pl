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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131575"
---
# <a name="observer-design-pattern"></a>Wzorzec projektowy obserwatora

Wzorzec projektowy obserwatora umożliwia subskrybentowi zarejestrowanie się w usłudze i otrzymywanie powiadomień od dostawcy. Jest to odpowiednie dla każdego scenariusza wymagającego powiadomień wypychanych. Wzorzec definiuje *dostawcę* (znanego również jako *temat* lub *zauważalny*) i zero, jeden lub więcej *obserwatorów*. Obserwatorzy rejestrują się u dostawcy i za każdym razem, gdy występuje wstępnie zdefiniowany warunek, zdarzenie lub zmiana stanu, dostawca automatycznie powiadamia o wszystkich Obserwatorach, wywołując jedną z metod. W przypadku tego wywołania metody dostawca może również podać informacje o bieżącym stanie dla obserwatorów. W .NET Framework Wzorzec projektowy obserwatora jest stosowany przez implementację ogólnych <xref:System.IObservable%601?displayProperty=nameWithType> i interfejsów <xref:System.IObserver%601?displayProperty=nameWithType>. Parametr typu ogólnego reprezentuje typ, który zawiera informacje o powiadomieniach.

## <a name="applying-the-pattern"></a>Stosowanie wzorca

Wzorzec projektowy obserwatora jest odpowiedni dla rozproszonych powiadomień opartych na wypychaniu, ponieważ obsługuje czyste rozdzielenie między dwoma różnymi składnikami lub warstwami aplikacji, takimi jak warstwa źródła danych (logika biznesowa) i warstwa interfejsu użytkownika (Display). Wzorzec może być implementowany za każdym razem, gdy dostawca używa wywołań zwrotnych w celu dostarczenia klientom bieżących informacji.

Implementacja wzorca wymaga podania następujących danych:

- Dostawca lub podmiot, który jest obiektem, który wysyła powiadomienia do obserwatorów. Dostawca jest klasą lub strukturą implementującą interfejs <xref:System.IObservable%601>. Dostawca musi implementować pojedynczą metodę, <xref:System.IObservable%601.Subscribe%2A?displayProperty=nameWithType>, która jest wywoływana przez obserwatorów, którzy chcą otrzymywać powiadomienia od dostawcy.

- Obserwator, który jest obiektem, który odbiera powiadomienia od dostawcy. Obserwator to Klasa lub struktura implementująca interfejs <xref:System.IObserver%601>. Obserwator musi zaimplementować trzy metody, z których wszystkie są wywoływane przez dostawcę:

  - <xref:System.IObserver%601.OnNext%2A?displayProperty=nameWithType>, która udostępnia obserwatorowi nowe lub bieżące informacje.

  - <xref:System.IObserver%601.OnError%2A?displayProperty=nameWithType>, który informuje obserwatora o wystąpieniu błędu.

  - <xref:System.IObserver%601.OnCompleted%2A?displayProperty=nameWithType>, co oznacza, że dostawca zakończył wysyłanie powiadomień.

- Mechanizm, który umożliwia dostawcy śledzić obserwatorów. Zazwyczaj Dostawca używa obiektu kontenera, takiego jak obiekt <xref:System.Collections.Generic.List%601?displayProperty=nameWithType>, do przechowywania odwołań do implementacji <xref:System.IObserver%601>, które subskrybują powiadomienia. Użycie w tym celu kontenera magazynu pozwala dostawcy obsłużyć zero do nieograniczonej liczby obserwatorów. Kolejność, w której obserwatorzy otrzymują powiadomienia, nie jest zdefiniowana; Dostawca jest bezpłatny, aby określić kolejność przy użyciu dowolnej metody.

- Implementacja <xref:System.IDisposable>, która umożliwia dostawcy usuwanie obserwatorów po zakończeniu powiadamiania. Obserwatorzy otrzymują odwołanie do implementacji <xref:System.IDisposable> z metody <xref:System.IObservable%601.Subscribe%2A>, dzięki czemu mogą również wywołać metodę <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType>, aby anulować subskrypcję, zanim dostawca zakończył wysyłanie powiadomień.

- Obiekt, który zawiera dane wysyłane przez dostawcę do obserwatorów. Typ tego obiektu odpowiada parametrowi typu ogólnego interfejsów <xref:System.IObservable%601> i <xref:System.IObserver%601>. Chociaż ten obiekt może być taki sam jak implementacja <xref:System.IObservable%601>, najczęściej jest to oddzielny typ.

> [!NOTE]
> Oprócz wdrożenia wzorca projektowego obserwatora warto poznać biblioteki, które są kompilowane przy użyciu interfejsów <xref:System.IObservable%601> i <xref:System.IObserver%601>. Na przykład [reaktywne rozszerzenia dla platformy .NET (RX)](https://docs.microsoft.com/previous-versions/dotnet/reactive-extensions/hh242985(v=vs.103)) składają się z zestawu metod rozszerzających i operatorów standardowej sekwencji LINQ do obsługi programowania asynchronicznego.

## <a name="implementing-the-pattern"></a>Implementowanie wzorca

W poniższym przykładzie zastosowano Wzorzec projektowy obserwatora do zaimplementowania systemu informacji o zaroście bagażu lotniska. Klasa `BaggageInfo` zawiera informacje na temat przybycia lotów i karuzeli, w przypadku których bagaż z każdego lotu jest dostępny do odbioru. Pokazano to w poniższym przykładzie.

[!code-csharp[Conceptual.ObserverDesignPattern#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/provider.cs#1)]
[!code-vb[Conceptual.ObserverDesignPattern#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/provider.vb#1)]

Klasa `BaggageHandler` jest odpowiedzialna za otrzymywanie informacji na temat przybycia lotów i karuzeli roszczeń. Wewnętrznie obsługuje dwie kolekcje:

- `observers` — kolekcja klientów, którzy będą otrzymywać zaktualizowane informacje.

- `flights` — kolekcja lotów i ich przypisane karuzeli.

Obie kolekcje są reprezentowane przez ogólne obiekty <xref:System.Collections.Generic.List%601>, które są tworzone w konstruktorze klasy `BaggageHandler`. Kod źródłowy klasy `BaggageHandler` jest przedstawiony w poniższym przykładzie.

[!code-csharp[Conceptual.ObserverDesignPattern#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/provider.cs#2)]
[!code-vb[Conceptual.ObserverDesignPattern#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/provider.vb#2)]

Klienci, którzy chcą otrzymywać zaktualizowane informacje, wywołują metodę `BaggageHandler.Subscribe`. Jeśli klient nie subskrybuje wcześniej powiadomień, do kolekcji `observers` zostanie dodany odwołanie do implementacji <xref:System.IObserver%601> klienta.

Można wywołać przeciążoną metodę `BaggageHandler.BaggageStatus`, aby wskazać, że bagaż z lotu jest zwalniany lub nie jest już zwolniony. W pierwszym przypadku metoda jest przenoszona jako numer lotu, Port lotniczy, z którego pochodzi lot, oraz karuzela, w której jest zwalniany bagaż. W drugim przypadku metoda jest przenoszona tylko do numeru lotu. W przypadku odciążania bagażu Metoda sprawdza, czy informacje `BaggageInfo` przekazane do metody istnieją w kolekcji `flights`. Jeśli tak nie jest, Metoda dodaje informacje i wywołuje każdą metodę `OnNext` obserwatora. W przypadku lotów, których bagaż nie jest już zwolniony, Metoda sprawdza, czy informacje o tym locie są przechowywane w kolekcji `flights`. Jeśli tak jest, metoda wywołuje każdą metodę `OnNext` obserwatora i usuwa obiekt `BaggageInfo` z kolekcji `flights`.

Gdy upłynął czas użytkowania ostatniego lotu dnia, a jego bagaż został przetworzony, wywoływana jest metoda `BaggageHandler.LastBaggageClaimed`. Ta metoda wywołuje każdą metodę `OnCompleted` obserwatora, aby wskazać, że wszystkie powiadomienia zostały ukończone, a następnie czyści kolekcję `observers`.

Metoda <xref:System.IObservable%601.Subscribe%2A> dostawcy zwraca implementację <xref:System.IDisposable>, która umożliwia obserwatorom zaprzestanie otrzymywania powiadomień przed wywołaniem metody <xref:System.IObserver%601.OnCompleted%2A>. Kod źródłowy dla tej klasy `Unsubscriber(Of BaggageInfo)` jest przedstawiony w poniższym przykładzie. Gdy Klasa jest tworzona w metodzie `BaggageHandler.Subscribe`, zostanie ona przeniesiona do kolekcji `observers` i odwołanie do obserwatora, który jest dodawany do kolekcji. Te odwołania są przypisywane do zmiennych lokalnych. Gdy wywoływana jest metoda `Dispose` obiektu, sprawdza, czy obserwator nadal istnieje w kolekcji `observers` i, jeśli tak, spowoduje usunięcie obserwatora.

[!code-csharp[Conceptual.ObserverDesignPattern#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/provider.cs#3)]
[!code-vb[Conceptual.ObserverDesignPattern#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/provider.vb#3)]

W poniższym przykładzie przedstawiono implementację <xref:System.IObserver%601> o nazwie `ArrivalsMonitor`, która jest klasą bazową, która wyświetla informacje o poświadczeniu o bagażu. Informacje są wyświetlane alfabetycznie według nazwy miejscowości źródłowej. Metody `ArrivalsMonitor` są oznaczone jako `overridable` (w Visual Basic) lub `virtual` (w C#), dzięki czemu wszystkie te wartości mogą zostać zastąpione przez klasę pochodną.

[!code-csharp[Conceptual.ObserverDesignPattern#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/observer.cs#4)]
[!code-vb[Conceptual.ObserverDesignPattern#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/observer.vb#4)]

Klasa `ArrivalsMonitor` obejmuje metody `Subscribe` i `Unsubscribe`. Metoda `Subscribe` umożliwia klasy zapisywanie <xref:System.IDisposable> implementacji zwracanej przez wywołanie <xref:System.IObservable%601.Subscribe%2A> do zmiennej prywatnej. Metoda `Unsubscribe` umożliwia anulowanie subskrypcji powiadomień przez klasę przez wywołanie <xref:System.IDisposable.Dispose%2A> implementacji dostawcy. `ArrivalsMonitor` również udostępnia implementacje metod <xref:System.IObserver%601.OnNext%2A>, <xref:System.IObserver%601.OnError%2A>i <xref:System.IObserver%601.OnCompleted%2A>. Tylko implementacja <xref:System.IObserver%601.OnNext%2A> zawiera znaczną ilość kodu. Metoda działa z prywatnym, posortowanym, ogólnym obiektem <xref:System.Collections.Generic.List%601>, który utrzymuje informacje o portach lotniczych pochodzenia dla docierających lotów i karuzeli, na których jest dostępny bagaż. Jeśli Klasa `BaggageHandler` zgłasza nowe nadejście lotu, implementacja metody <xref:System.IObserver%601.OnNext%2A> dodaje informacje o tym locie do listy. Jeśli Klasa `BaggageHandler` zgłasza, że bagaż pracownika został zwolniony, Metoda <xref:System.IObserver%601.OnNext%2A> usuwa ten lot z listy. Za każdym razem, gdy zostanie wprowadzona zmiana, lista zostanie posortowana i wyświetlona w konsoli programu.

Poniższy przykład zawiera punkt wejścia aplikacji, który tworzy wystąpienie klasy `BaggageHandler`, a także dwa wystąpienia klasy `ArrivalsMonitor`, i używa metody `BaggageHandler.BaggageStatus` do dodawania i usuwania informacji na temat przybycia lotów. W każdym przypadku obserwatorzy odbierają aktualizacje i poprawnie wyświetlają informacje o postawie bagażu.

[!code-csharp[Conceptual.ObserverDesignPattern#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.observerdesignpattern/cs/program.cs#5)]
[!code-vb[Conceptual.ObserverDesignPattern#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.observerdesignpattern/vb/module1.vb#5)]

## <a name="related-topics"></a>Tematy pokrewne

|Tytuł|Opis|
|-----------|-----------------|
|[Wzorzec projektowy obserwatora — najlepsze rozwiązania](../../../docs/standard/events/observer-design-pattern-best-practices.md)|W tym artykule opisano najlepsze rozwiązania, które należy podjąć podczas opracowywania aplikacji, które implementują Wzorzec projektowy obserwatora.|
|[Instrukcje: Implementowanie dostawcy](../../../docs/standard/events/how-to-implement-a-provider.md)|Zapewnia implementację krok po kroku dostawcy dla aplikacji monitorującej temperaturę.|
|[Instrukcje: Implementowanie obserwatora](../../../docs/standard/events/how-to-implement-an-observer.md)|Zawiera implementację krok po kroku obserwatora dla aplikacji monitorującej temperaturę.|

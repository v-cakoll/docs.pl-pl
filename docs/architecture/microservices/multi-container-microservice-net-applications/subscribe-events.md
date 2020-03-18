---
title: Subskrybowanie zdarzeń
description: Architektura mikrousług .NET dla konteneryzowanych aplikacji .NET | Zapoznaj się ze szczegółami publikowania i subskrypcji zdarzeń integracji.
ms.date: 01/30/2020
ms.openlocfilehash: 544af8035ed23dd6507dfed4944b0c327c81d943
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77501810"
---
# <a name="subscribing-to-events"></a>Subskrybowanie zdarzeń

Pierwszym krokiem do korzystania z magistrali zdarzeń jest subskrybowanie mikrousług do zdarzeń, które mają być odbierane. Należy to zrobić w mikrousługach odbiornika.

Poniższy prosty kod pokazuje, co każdy mikrousługi odbiornika musi zaimplementować podczas uruchamiania usługi (oznacza to, że w `Startup` klasie), więc subskrybuje zdarzenia, których potrzebuje. W takim przypadku `basket-api` mikrousługi musi `ProductPriceChangedIntegrationEvent` subskrybować i `OrderStartedIntegrationEvent` wiadomości.

Na przykład podczas subskrybowania `ProductPriceChangedIntegrationEvent` zdarzenia, który sprawia, że mikrousługi koszyka świadomość wszelkich zmian w cenie produktu i pozwala ostrzec użytkownika o zmianie, jeśli ten produkt znajduje się w koszyku użytkownika.

```csharp
var eventBus = app.ApplicationServices.GetRequiredService<IEventBus>();

eventBus.Subscribe<ProductPriceChangedIntegrationEvent,
                   ProductPriceChangedIntegrationEventHandler>();

eventBus.Subscribe<OrderStartedIntegrationEvent,
                   OrderStartedIntegrationEventHandler>();

```

Po uruchomieniu tego kodu mikrousługi subskrybenta będą nasłuchiwane za pośrednictwem kanałów RabbitMQ. Po odebraniu dowolnego komunikatu o typie ProductPriceChangedIntegrationEvent, kod wywołuje program obsługi zdarzeń, który jest przekazywany do niego i przetwarza zdarzenie.

## <a name="publishing-events-through-the-event-bus"></a>Publikowanie zdarzeń za pośrednictwem magistrali zdarzeń

Na koniec nadawca wiadomości (mikrousługi pochodzenia) publikuje zdarzenia integracji z kodem podobnym do poniższego przykładu. (Jest to uproszczony przykład, który nie bierze pod uwagę niepodzielności.) Można zaimplementować podobny kod zawsze, gdy zdarzenie musi być propagowane przez wiele mikrousług, zwykle zaraz po zaznananiu danych lub transakcji z mikrousługi pochodzenia.

Po pierwsze obiekt implementacji magistrali zdarzeń (na podstawie RabbitMQ lub na podstawie magistrali usług) zostanie wstrzyknięty do konstruktora kontrolera, jak w następującym kodzie:

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    private readonly CatalogContext _context;
    private readonly IOptionsSnapshot<Settings> _settings;
    private readonly IEventBus _eventBus;

    public CatalogController(CatalogContext context,
        IOptionsSnapshot<Settings> settings,
        IEventBus eventBus)
    {
        _context = context;
        _settings = settings;
        _eventBus = eventBus;
    }
    // ...
}
```

Następnie należy go użyć z metod kontrolera, takich jak w UpdateProduct metody:

```csharp
[Route("items")]
[HttpPost]
public async Task<IActionResult> UpdateProduct([FromBody]CatalogItem product)
{
    var item = await _context.CatalogItems.SingleOrDefaultAsync(
        i => i.Id == product.Id);
    // ...
    if (item.Price != product.Price)
    {
        var oldPrice = item.Price;
        item.Price = product.Price;
        _context.CatalogItems.Update(item);
        var @event = new ProductPriceChangedIntegrationEvent(item.Id,
            item.Price,
            oldPrice);
        // Commit changes in original transaction
        await _context.SaveChangesAsync();
        // Publish integration event to the event bus
        // (RabbitMQ or a service bus underneath)
        _eventBus.Publish(@event);
        // ...
    }
    // ...
}
```

W takim przypadku, ponieważ mikrousługi pochodzenia jest prosta mikrousługa CRUD, ten kod jest umieszczany bezpośrednio do kontrolera interfejsu API sieci Web.

W bardziej zaawansowanych mikrousług, takich jak podczas korzystania z cqrs podejścia, można zaimplementować w `CommandHandler` klasie, w ramach `Handle()` metody.

### <a name="designing-atomicity-and-resiliency-when-publishing-to-the-event-bus"></a>Projektowanie niepodzielności i odporności podczas publikowania w magistrali zdarzeń

Podczas publikowania zdarzeń integracji za pośrednictwem rozproszonego systemu obsługi wiadomości, takich jak magistrala zdarzeń, masz problem z niepodzielnym aktualizowanie oryginalnej bazy danych i publikowanie zdarzenia (oznacza to, że obie operacje ukończone lub żaden z nich). Na przykład w uproszczonym przykładzie pokazano wcześniej kod zatwierdza dane do bazy danych po zmianie ceny produktu, a następnie publikuje productpricechangedintegrationevent komunikatu. Początkowo może się wydawać istotne, że te dwie operacje są wykonywane niepodzielnie. Jeśli jednak używasz transakcji rozproszonej obejmującej bazę danych i brokera komunikatów, tak jak w starszych systemach, takich jak [Usługa kolejkowania wiadomości firmy Microsoft (MSMQ),](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx)nie jest to zalecane z powodów opisanych przez [żądanie WPR](https://www.quora.com/What-Is-CAP-Theorem-1).

Zasadniczo używasz mikrousług do tworzenia skalowalnych i wysoce dostępnych systemów. Upraszczając nieco twierdzenie CAP mówi, że nie można utworzyć (rozproszony) bazy danych (lub mikrousługi, która jest właścicielem modelu), który jest stale dostępny, zdecydowanie spójne *i* tolerancyjny dla dowolnej partycji. Należy wybrać dwie z tych trzech właściwości.

W architekturach opartych na mikrousługach należy wybrać dostępność i tolerancję, a także należy deemphasize silnej spójności. W związku z tym w większości nowoczesnych aplikacji opartych na mikrousługach zwykle nie chcesz używać transakcji rozproszonych w wiadomościach, tak jak podczas implementowania [transakcji rozproszonych opartych](https://docs.microsoft.com/previous-versions/windows/desktop/ms681205(v=vs.85)) na koordynatorze transakcji rozproszonych systemu Windows (DTC) z [usługą MSMQ](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx).

Wróćmy do początkowego problemu i jego przykładu. Jeśli usługa ulega awarii po zaktualizowaniu bazy danych (w tym przypadku \_zaraz po wierszu kodu z kontekstem. SaveChangesAsync()), ale przed opublikowaniem zdarzenia integracji ogólny system może stać się niespójny. Może to mieć kluczowe znaczenie dla firmy, w zależności od konkretnej operacji biznesowej, z którą masz do czynienia.

Jak wspomniano wcześniej w sekcji architektury, można mieć kilka podejść do radzenia sobie z tym problemem:

- Korzystanie z pełnego [wzorca pozyskiwania zdarzeń](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing).

- Korzystanie z [eksploracji dziennika transakcji](https://www.scoop.it/t/sql-server-transaction-log-mining).

- Korzystanie ze [wzorca skrzynki nadawczej](https://www.kamilgrzybek.com/design/the-outbox-pattern/). Jest to tabela transakcyjna do przechowywania zdarzeń integracji (rozszerzenie transakcji lokalnej).

W tym scenariuszu przy użyciu wzorca pełnego pozyskiwania zdarzeń (ES) jest jednym z najlepszych podejść, jeśli *nie* najlepsze. Jednak w wielu scenariuszach aplikacji może nie być w stanie zaimplementować pełnego systemu ES. ES oznacza przechowywanie tylko zdarzeń domeny w transakcyjnej bazie danych, zamiast przechowywać bieżące dane o stanie. Przechowywanie tylko zdarzeń domeny może mieć ogromne korzyści, takie jak posiadanie dostępnej historii systemu i możliwość określenia stanu systemu w dowolnym momencie w przeszłości. Jednak wdrożenie pełnego systemu ES wymaga ponownego architekta większości systemu i wprowadzenia wielu innych zawiłości i wymagań. Na przykład chcesz użyć bazy danych specjalnie do pozyskiwania zdarzeń, takich jak [Magazyn zdarzeń](https://eventstore.org/), lub bazy danych zorientowanych na dokumenty, takich jak Azure Cosmos DB, MongoDB, Cassandra, CouchDB lub RavenDB. ES jest świetnym podejściem do tego problemu, ale nie najłatwiejszym rozwiązaniem, chyba że już znasz pozyskiwanie zdarzeń.

Opcja użycia eksploracji dziennika transakcji początkowo wygląda bardzo przezroczyste. Jednak aby użyć tej metody, mikrousługi musi być sprzęgła z dziennika transakcji RDBMS, takich jak dziennik transakcji programu SQL Server. Prawdopodobnie nie jest to pożądane. Inną wadą jest to, że aktualizacje niskiego poziomu zarejestrowane w dzienniku transakcji mogą nie być na tym samym poziomie, co zdarzenia integracji na wysokim poziomie. Jeśli tak, proces inżynierii odwrotnej tych operacji dziennika transakcji może być trudne.

Zrównoważone podejście to połączenie transakcyjnej tabeli bazy danych i uproszczonego wzorca ES. Można użyć stanu, takiego jak "gotowy do opublikowania zdarzenia", który można ustawić w oryginalnym zdarzeniu podczas zatwierdzania go do tabeli zdarzeń integracji. Następnie spróbuj opublikować zdarzenie w magistrali zdarzeń. Jeśli akcja publish-event zakończy się powodzeniem, uruchomininną transakcję w usłudze pochodzenia i przeniesiesz stan z "gotowy do opublikowania zdarzenia" na "zdarzenie już opublikowane".

Jeśli akcja publish-event w magistrali zdarzeń nie powiedzie się, dane nadal nie będą niespójne w ramach mikrousługi pochodzenia — nadal jest oznaczony jako "gotowy do opublikowania zdarzenia", a w odniesieniu do pozostałych usług, ostatecznie będzie spójne. Zawsze można mieć zadania w tle sprawdzanie stanu transakcji lub zdarzeń integracji. Jeśli zadanie znajdzie zdarzenie w stanie "gotowy do opublikowania zdarzenia", może spróbować ponownie opublikować to zdarzenie w magistrali zdarzeń.

Należy zauważyć, że z tej metody są utrwalania tylko zdarzenia integracji dla każdego mikrousługi pochodzenia i tylko zdarzenia, które mają być przekazywane do innych mikrousług lub systemów zewnętrznych. W przeciwieństwie do tego, w pełnym systemie ES, można przechowywać wszystkie zdarzenia domeny, jak również.

W związku z tym to zrównoważone podejście jest uproszczonym systemem ES. Potrzebna jest lista zdarzeń integracji z ich bieżącym stanem ("gotowy do opublikowania" w porównaniu z "opublikowanym"). Ale wystarczy zaimplementować te stany dla zdarzeń integracji. W tym podejściu nie trzeba przechowywać wszystkich danych domeny jako zdarzeń w transakcyjnej bazie danych, tak jak w pełnym systemie ES.

Jeśli używasz już relacyjnej bazy danych, można użyć tabeli transakcyjnej do przechowywania zdarzeń integracji. Aby osiągnąć niepodzielność w aplikacji, należy użyć procesu dwuetapowego na podstawie transakcji lokalnych. Zasadniczo masz IntegrationEvent tabeli w tej samej bazie danych, gdzie masz jednostek domeny. Ta tabela działa jako ubezpieczenie do osiągnięcia niepodzielności, dzięki czemu należy uwzględnić zdarzenia integracji utrwalione do tych samych transakcji, które zatwierdzają dane domeny.

Krok po kroku proces przebiega następująco:

1. Aplikacja rozpoczyna transakcję lokalnej bazy danych.

2. Następnie aktualizuje stan jednostek domeny i wstawia zdarzenie do tabeli zdarzeń integracji.

3. Na koniec zatwierdza transakcję, dzięki czemu otrzymasz pożądaną niepodzielność, a następnie

4. Publikujesz wydarzenie w jakiś sposób (dalej).

Podczas wykonywania kroków publikowania zdarzeń, masz następujące opcje:

- Opublikuj zdarzenie integracji zaraz po zazięciu transakcji i użyj innej transakcji lokalnej, aby oznaczyć zdarzenia w tabeli jako publikowane. Następnie użyj tabeli tak samo jak artefakt do śledzenia zdarzeń integracji w przypadku problemów w mikrousługach zdalnych i wykonywać akcje kompensacyjne na podstawie przechowywanych zdarzeń integracji.

- Użyj tabeli jako rodzaj kolejki. Oddzielny wątek aplikacji lub proces wysyła zapytanie do tabeli zdarzeń integracji, publikuje zdarzenia w magistrali zdarzeń, a następnie używa transakcji lokalnej do oznaczania zdarzeń jako opublikowanych.

Rysunek 6-22 przedstawia architekturę pierwszego z tych metod.

![Diagram niepodzielności podczas publikowania bez mikrousługi procesowej.](./media/subscribe-events/atomicity-publish-event-bus.png)

**Rysunek 6-22**. Niepodzielność podczas publikowania zdarzeń do magistrali zdarzeń

Podejście przedstawione na rysunku 6-22 brakuje dodatkowej mikrousługi procesu roboczego, który jest odpowiedzialny za sprawdzanie i potwierdzanie sukcesu opublikowanych zdarzeń integracji. W przypadku awarii, że dodatkowe mikrousługi procesu roboczego sprawdzania może odczytywać zdarzenia z tabeli i ponownie je opublikować, czyli powtórzyć krok numer 2.

O drugim podejściu: używasz EventLog tabeli jako kolejki i zawsze używać mikrousługi roboczego do publikowania wiadomości. W takim przypadku proces jest podobny do tego pokazanego na rysunku 6-23. Pokazuje to dodatkowe mikrousługi, a tabela jest pojedynczym źródłem podczas publikowania zdarzeń.

![Diagram niepodzielności podczas publikowania z mikrousług roboczych.](./media/subscribe-events/atomicity-publish-worker-microservice.png)

**Rysunek 6-23**. Niepodzielność podczas publikowania zdarzeń do magistrali zdarzeń z mikrousługą roboczą

Dla uproszczenia eShopOnContainers próbki używa pierwszego podejścia (bez dodatkowych procesów lub mikrousług sprawdzania) oraz magistrali zdarzeń. Jednak eShopOnContainers nie obsługuje wszystkich możliwych przypadków awarii. W rzeczywistej aplikacji wdrożonej w chmurze należy objąć fakt, że problemy pojawią się po pewnym czasie i należy zaimplementować tę logikę sprawdzania i ponownego wysyłania. Korzystanie z tabeli jako kolejki może być bardziej efektywne niż pierwsze podejście, jeśli masz tej tabeli jako pojedyncze źródło zdarzeń podczas publikowania ich (z pracownikiem) za pośrednictwem magistrali zdarzeń.

### <a name="implementing-atomicity-when-publishing-integration-events-through-the-event-bus"></a>Implementowanie niepodzielności podczas publikowania zdarzeń integracji za pośrednictwem magistrali zdarzeń

Poniższy kod pokazuje, jak można utworzyć pojedynczą transakcję z udziałem wielu obiektów DbContext — jeden kontekst związany z oryginalnymi danymi, które są aktualizowane, a drugi kontekst związany z tabelą IntegrationEventLog.

Należy zauważyć, że transakcja w poniższym kodzie przykładnie nie będzie odporna, jeśli połączenia z bazą danych mają jakikolwiek problem w czasie, gdy kod jest uruchomiony. Może się to zdarzyć w systemach opartych na chmurze, takich jak usługa Azure SQL DB, które mogą przenosić bazy danych między serwerami. Aby zaimplementowanie transakcji odpornych w wielu kontekstach, zobacz [implementowanie resilient Entity Framework Core SQL connections](../implement-resilient-applications/implement-resilient-entity-framework-core-sql-connections.md) sekcji w dalszej części tego przewodnika.

Dla jasności w poniższym przykładzie przedstawiono cały proces w jednym kawałku kodu. Jednak implementacja eShopOnContainers jest faktycznie refaktoryzacji i podzielić tę logikę na wiele klas, dzięki czemu jest łatwiejsze do utrzymania.

```csharp
// Update Product from the Catalog microservice
//
public async Task<IActionResult> UpdateProduct([FromBody]CatalogItem productToUpdate)
{
  var catalogItem =
       await _catalogContext.CatalogItems.SingleOrDefaultAsync(i => i.Id ==
                                                               productToUpdate.Id);
  if (catalogItem == null) return NotFound();

  bool raiseProductPriceChangedEvent = false;
  IntegrationEvent priceChangedEvent = null;

  if (catalogItem.Price != productToUpdate.Price)
          raiseProductPriceChangedEvent = true;

  if (raiseProductPriceChangedEvent) // Create event if price has changed
  {
      var oldPrice = catalogItem.Price;
      priceChangedEvent = new ProductPriceChangedIntegrationEvent(catalogItem.Id,
                                                                  productToUpdate.Price,
                                                                  oldPrice);
  }
  // Update current product
  catalogItem = productToUpdate;

  // Just save the updated product if the Product's Price hasn't changed.
  if (!raiseProductPriceChangedEvent)
  {
      await _catalogContext.SaveChangesAsync();
  }
  else  // Publish to event bus only if product price changed
  {
        // Achieving atomicity between original DB and the IntegrationEventLog
        // with a local transaction
        using (var transaction = _catalogContext.Database.BeginTransaction())
        {
           _catalogContext.CatalogItems.Update(catalogItem);
           await _catalogContext.SaveChangesAsync();

           // Save to EventLog only if product price changed
           if(raiseProductPriceChangedEvent)
               await _integrationEventLogService.SaveEventAsync(priceChangedEvent);

           transaction.Commit();
        }

      // Publish the integration event through the event bus
      _eventBus.Publish(priceChangedEvent);

      integrationEventLogService.MarkEventAsPublishedAsync(
                                                priceChangedEvent);
  }

  return Ok();
}

```

Po productpricechangedintegrationevent zdarzenie integracji jest tworzony, transakcja, która przechowuje oryginalną operację domeny (zaktualizować element katalogu) zawiera również trwałość zdarzenia w tabeli EventLog. To sprawia, że pojedyncza transakcja i zawsze będzie można sprawdzić, czy wiadomości zdarzenia zostały wysłane.

Tabela dziennika zdarzeń jest aktualizowana niepodzielnie przy użyciu oryginalnej operacji bazy danych przy użyciu transakcji lokalnej względem tej samej bazy danych. Jeśli którakolwiek z operacji nie powiedzie się, wyjątek i transakcja wycofuje wszystkie zakończone operacji, zachowując spójność między operacjami domeny i komunikatów zdarzenia zapisanych w tabeli.

### <a name="receiving-messages-from-subscriptions-event-handlers-in-receiver-microservices"></a>Odbieranie komunikatów z subskrypcji: programy obsługi zdarzeń w mikrousługach odbiornika

Oprócz logiki subskrypcji zdarzeń należy zaimplementować wewnętrzny kod dla programów obsługi zdarzeń integracji (jak metoda wywołania wywołania. Program obsługi zdarzeń jest, gdzie można określić, gdzie będą odbierane i przetwarzane komunikaty o zdarzeniach określonego typu.

Program obsługi zdarzeń najpierw odbiera wystąpienie zdarzenia z magistrali zdarzeń. Następnie lokalizuje składnik, który ma być przetwarzany związane z tym zdarzeniem integracji, propagacji i utrwalania zdarzenia jako zmiany stanu w mikrousługi odbiornika. Na przykład jeśli ProductPriceChanged zdarzenie pochodzi z mikrousługi katalogu, jest obsługiwany w mikrousługi koszyka i zmienia stan w tym mikrousługi koszyka odbiornika, jak pokazano w poniższym kodzie.

```csharp
namespace Microsoft.eShopOnContainers.Services.Basket.API.IntegrationEvents.EventHandling
{
    public class ProductPriceChangedIntegrationEventHandler :
        IIntegrationEventHandler<ProductPriceChangedIntegrationEvent>
    {
        private readonly IBasketRepository _repository;

        public ProductPriceChangedIntegrationEventHandler(
            IBasketRepository repository)
        {
            _repository = repository;
        }

        public async Task Handle(ProductPriceChangedIntegrationEvent @event)
        {
            var userIds = await _repository.GetUsers();
            foreach (var id in userIds)
            {
                var basket = await _repository.GetBasket(id);
                await UpdatePriceInBasketItems(@event.ProductId, @event.NewPrice, basket);
            }
        }

        private async Task UpdatePriceInBasketItems(int productId, decimal newPrice,
            CustomerBasket basket)
        {
            var itemsToUpdate = basket?.Items?.Where(x => int.Parse(x.ProductId) ==
                productId).ToList();
            if (itemsToUpdate != null)
            {
                foreach (var item in itemsToUpdate)
                {
                    if(item.UnitPrice != newPrice)
                    {
                        var originalPrice = item.UnitPrice;
                        item.UnitPrice = newPrice;
                        item.OldUnitPrice = originalPrice;
                    }
                }
                await _repository.UpdateBasket(basket);
            }
        }
    }
}
```

Program obsługi zdarzeń musi sprawdzić, czy produkt istnieje w dowolnym z wystąpień koszyka. Aktualizuje również cenę towaru dla każdego powiązanego elementu zamówienia koszyka. Na koniec tworzy alert, który ma być wyświetlany użytkownikowi o zmianie ceny, jak pokazano na rysunku 6-24.

![Zrzut ekranu przedstawiający przeglądarkę z powiadomieniem o zmianie ceny w koszyku użytkownika.](./media/subscribe-events/display-item-price-change.png)

**Rysunek 6-24**. Wyświetlanie zmiany ceny towaru w koszyku, o tym, co jest przekazywane przez zdarzenia integracji

## <a name="idempotency-in-update-message-events"></a>Idempotencja w zdarzeniach wiadomości aktualizacji

Ważnym aspektem zdarzenia komunikatu aktualizacji jest, że błąd w dowolnym momencie w komunikacji powinien spowodować wiadomość do ponowienia próby. W przeciwnym razie zadanie w tle może próbować opublikować zdarzenie, które zostało już opublikowane, tworząc stan wyścigu. Należy upewnić się, że aktualizacje są idempotentności lub że dostarczają one wystarczających informacji, aby upewnić się, że można wykryć duplikat, odrzucić go i odesłać tylko jedną odpowiedź.

Jak wspomniano wcześniej, idempotencja oznacza, że operacja może być wykonywana wiele razy bez zmiany wyniku. W środowisku obsługi wiadomości, jak podczas przekazywania zdarzeń, zdarzenie jest idempotentności, jeśli może być dostarczane wiele razy bez zmiany wyniku dla mikrousługi odbiornika. Może to być konieczne ze względu na charakter samego zdarzenia lub ze względu na sposób, w jaki system obsługuje zdarzenie. Idempotencja wiadomości jest ważna w każdej aplikacji, która używa obsługi wiadomości, a nie tylko w aplikacjach implementujących wzorzec magistrali zdarzeń.

Przykładem operacji idempotentności jest instrukcja SQL, która wstawia dane do tabeli tylko wtedy, gdy dane te nie są jeszcze w tabeli. Nie ma znaczenia, ile razy uruchamiasz tę instrukcję Wstawić SQL; wynik będzie taki sam — tabela będzie zawierać te dane. Idempotencja jak to może być również konieczne w przypadku do czynienia z wiadomościami, jeśli wiadomości mogą być potencjalnie wysyłane i dlatego przetwarzane więcej niż jeden raz. Na przykład jeśli logika ponawiania powoduje, że nadawca wysłać dokładnie tę samą wiadomość więcej niż jeden raz, należy upewnić się, że jest idempotentności.

Możliwe jest projektowanie wiadomości idempotentności. Możesz na przykład utworzyć zdarzenie z napisem "ustaw cenę produktu na 25 USD" zamiast "dodaj 5 USD do ceny produktu". Możesz bezpiecznie przetworzyć pierwszą wiadomość dowolną liczbę razy, a wynik będzie taki sam. Nie dotyczy to drugiego komunikatu. Ale nawet w pierwszym przypadku możesz nie chcieć przetworzyć pierwszego zdarzenia, ponieważ system mógł również wysłać nowsze zdarzenie zmiany cen i będziesz nadpisywać nową cenę.

Innym przykładem może być zdarzenie zakończone zamówienie jest propagowane do wielu subskrybentów. Ważne jest, aby informacje o zamówieniu były aktualizowane w innych systemach tylko raz, nawet jeśli istnieją zduplikowane zdarzenia wiadomości dla tego samego zdarzenia zakończonego zamówieniem.

Jest wygodne mieć pewnego rodzaju tożsamości na zdarzenie, dzięki czemu można utworzyć logikę, która wymusza, że każde zdarzenie jest przetwarzane tylko raz na odbiorcę.

Niektóre przetwarzanie wiadomości jest z natury idempotentności. Na przykład jeśli system generuje miniatury obrazów, może nie mieć znaczenia, ile razy wiadomość o wygenerowanej miniaturze jest przetwarzana; wynik jest, że miniatury są generowane i są takie same za każdym razem. Z drugiej strony, operacje, takie jak wywołanie bramki płatniczej w celu obciążenia karty kredytowej, mogą nie być w ogóle idempotentnością. W takich przypadkach należy upewnić się, że przetwarzanie wiadomości wiele razy ma wpływ, który można oczekiwać.

### <a name="additional-resources"></a>Zasoby dodatkowe

- **Honorowanie idempotency wiadomości** \
  <https://docs.microsoft.com/previous-versions/msp-n-p/jj591565(v=pandp.10)#honoring-message-idempotency>

## <a name="deduplicating-integration-event-messages"></a>Deduplicating komunikaty zdarzeń integracji

Można upewnić się, że zdarzenia wiadomości są wysyłane i przetwarzane tylko raz na subskrybenta na różnych poziomach. Jednym ze sposobów jest użycie funkcji deduplikacji oferowanej przez używaną infrastrukturę obsługi wiadomości. Innym jest zaimplementowanie logiki niestandardowej w mikrousługi docelowej. Posiadanie walidacji zarówno na poziomie transportu, jak i aplikacji jest najlepszym rozwiązaniem.

### <a name="deduplicating-message-events-at-the-eventhandler-level"></a>Deduplicating zdarzenia wiadomości na poziomie EventHandler

Jednym ze sposobów, aby upewnić się, że zdarzenie jest przetwarzane tylko raz przez dowolnego odbiorcy jest implementowanie niektórych logiki podczas przetwarzania zdarzeń komunikatu w programach obsługi zdarzeń. Na przykład jest to podejście używane w aplikacji eShopOnContainers, jak widać w [kodzie źródłowym UserCheckoutAcceptedIntegrationEventHandler klasy](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) po odebraniu UserCheckoutAcceptedIntegrationEvent zdarzenia integracji. (W tym przypadku zawijamy CreateOrderCommand z IdentifiedCommand, przy użyciu eventMsg.RequestId jako identyfikator, przed wysłaniem go do programu obsługi poleceń).

### <a name="deduplicating-messages-when-using-rabbitmq"></a>Deduplicating wiadomości podczas korzystania RabbitMQ

Po awarii sieci przerywanej wystąpić, wiadomości mogą być duplikowane, a odbiornik wiadomości musi być gotowy do obsługi tych zduplikowanych wiadomości. Jeśli to możliwe, odbiorcy powinni obsługiwać wiadomości w sposób idempotentny, co jest lepsze niż jawne obchodzenie się z nimi z deduplikacją.

Zgodnie z [dokumentacją RabbitMQ](https://www.rabbitmq.com/reliability.html#consumer), "Jeśli wiadomość jest dostarczana do konsumenta, a następnie ponownie w kolejce (ponieważ nie został potwierdzony przed połączenie konsumenta spadła, na przykład), a następnie RabbitMQ ustawi ponownie dostarczone flagi na nim, gdy jest dostarczany ponownie (czy do tego samego konsumenta lub innego).

Jeśli flaga "redelivered" jest ustawiona, odbiorca musi wziąć to pod uwagę, ponieważ wiadomość mogła już zostać przetworzona. Ale to nie jest gwarantowane; wiadomość może nigdy nie dotarły do odbiorcy po opuszczeniu brokera komunikatów, być może z powodu problemów z siecią. Z drugiej strony, jeśli flaga "ponownie dostarczona" nie jest ustawiona, gwarantuje się, że wiadomość nie została wysłana więcej niż jeden raz. W związku z tym odbiornik musi deduplikować wiadomości lub przetwarzać wiadomości w sposób idempotentny tylko wtedy, gdy flaga "dostarczone ponownie" jest ustawiona w wiadomości.

### <a name="additional-resources"></a>Zasoby dodatkowe

- **Forked eShopOnContainers przy użyciu NServiceBus (oprogramowanie szczególne)** \
    <https://go.particular.net/eShopOnContainers>

- **Wiadomości oparte na zdarzeniach** \
    <https://patterns.arcitura.com/soa-patterns/design_patterns/event_driven_messaging>

- **Jimmy Bogard. Refaktoryzacja w kierunku odporności: ocena sprzężenia** \
    <https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/>

- **Kanał publikowania i subskrybowania** \
    <https://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html>

- **Komunikowanie się między kontekstami ograniczonymi** \
    <https://docs.microsoft.com/previous-versions/msp-n-p/jj591572(v=pandp.10)>

- **Spójność ostateczna** \
    <https://en.wikipedia.org/wiki/Eventual_consistency>

- **Philip Brown. Strategie integracji ograniczonych kontekstów** \
    <https://www.culttt.com/2014/11/26/strategies-integrating-bounded-contexts/>

- **Chris Richardson. Tworzenie mikrousług transakcyjnych przy użyciu agregacji, pozyskiwania zdarzeń i CQRS — część 2** \
    <https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson>

- **Chris Richardson. Wzorzec pozyskiwania zdarzeń** \
    <https://microservices.io/patterns/data/event-sourcing.html>

- **Przedstawiamy pozyskiwanie zdarzeń** \
    <https://docs.microsoft.com/previous-versions/msp-n-p/jj591559(v=pandp.10)>

- **Baza danych Magazynu zdarzeń**. Oficjalna strona internetowa. \
    <https://geteventstore.com/>

- **Patrick Nommensen. Zarządzanie danymi opartymi na zdarzeniach dla mikrousług** \
    <https://dzone.com/articles/event-driven-data-management-for-microservices-1>

- **Wpr Theorem** \
    <https://en.wikipedia.org/wiki/CAP_theorem>

- **Czym jest wpr?** \
    <https://www.quora.com/What-Is-CAP-Theorem-1>

- **Podkład spójności danych** \
    <https://docs.microsoft.com/previous-versions/msp-n-p/dn589800(v=pandp.10)>

- **Rick Saling. Theorem WPR: Dlaczego "Wszystko jest inne" z chmurą i Internetem** \
    <https://docs.microsoft.com/archive/blogs/rickatmicrosoft/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/>

- **Eric Brewer. WPR dwanaście lat później: Jak zmieniły się "zasady"** \
    <https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed>

- **Azure Service Bus. Usługi pośrednictwa w komunikacji: wykrywanie duplikatów**  \
    <https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25>

- **Przewodnik niezawodności** (dokumentacja RabbitMQ) \
    <https://www.rabbitmq.com/reliability.html#consumer>

> [!div class="step-by-step"]
> [Poprzedni](rabbitmq-event-bus-development-test-environment.md)
> [następny](test-aspnet-core-services-web-apps.md)

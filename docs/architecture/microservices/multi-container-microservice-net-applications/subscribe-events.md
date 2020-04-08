---
title: Subskrybowanie zdarzeń
description: Architektura mikrousług platformy .NET dla konteneryzowanych aplikacji .NET | Poznaj szczegóły publikowania i subskrypcji zdarzeń integracji.
ms.date: 01/30/2020
ms.openlocfilehash: 426dcebe175e9db9a02bcdb2f21ad039154a7bda
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888218"
---
# <a name="subscribing-to-events"></a>Subskrybowanie zdarzeń

Pierwszym krokiem do korzystania z magistrali zdarzeń jest zasubskrybowanie mikrousług do zdarzeń, które mają być odbierane. Należy to zrobić w mikrousług odbiornika.

Poniższy prosty kod pokazuje, co każdy mikrousługi odbiornika musi `Startup` zaimplementować podczas uruchamiania usługi (czyli w klasie), więc subskrybuje zdarzenia, których potrzebuje. W takim przypadku `basket-api` mikrousługi musi `ProductPriceChangedIntegrationEvent` subskrybować i `OrderStartedIntegrationEvent` wiadomości.

Na przykład podczas subskrybowania `ProductPriceChangedIntegrationEvent` zdarzenia, który sprawia, że mikrousługi koszyka świadomość wszelkich zmian w cenie produktu i pozwala ostrzec użytkownika o zmianie, jeśli ten produkt znajduje się w koszyku użytkownika.

```csharp
var eventBus = app.ApplicationServices.GetRequiredService<IEventBus>();

eventBus.Subscribe<ProductPriceChangedIntegrationEvent,
                   ProductPriceChangedIntegrationEventHandler>();

eventBus.Subscribe<OrderStartedIntegrationEvent,
                   OrderStartedIntegrationEventHandler>();

```

Po uruchomieniu tego kodu mikrousługa subskrybenta będzie nasłuchiwać za pośrednictwem kanałów RabbitMQ. Gdy pojawia się dowolny komunikat typu ProductPriceChangedIntegrationEvent, kod wywołuje program obsługi zdarzeń, który jest do niego przekazywany i przetwarza zdarzenie.

## <a name="publishing-events-through-the-event-bus"></a>Publikowanie zdarzeń za pośrednictwem magistrali zdarzeń

Na koniec nadawca wiadomości (mikrousługa pochodzenia) publikuje zdarzenia integracji z kodem podobnym do poniższego przykładu. (Jest to uproszczony przykład, który nie uwzględnia niepodzielności). Można zaimplementować podobny kod, gdy zdarzenie musi być propagowane w wielu mikrousług, zwykle zaraz po zaawoleniu danych lub transakcji z mikrousługi pochodzenia.

Po pierwsze obiekt implementacji magistrali zdarzeń (na podstawie RabbitMQ lub na podstawie magistrali usług) zostanie wstrzyknięty w konstruktorze kontrolera, jak w poniższym kodzie:

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

W takim przypadku, ponieważ mikrousługa pochodzenia jest prosta mikrousługa CRUD, ten kod jest umieszczany bezpośrednio w kontrolerze interfejsu API sieci Web.

W bardziej zaawansowanych mikrousług, takich jak przy użyciu metod CQRS, można zaimplementować w `CommandHandler` klasie, w ramach `Handle()` metody.

### <a name="designing-atomicity-and-resiliency-when-publishing-to-the-event-bus"></a>Projektowanie niepodzielności i odporności podczas publikowania w magistrali zdarzeń

Podczas publikowania zdarzeń integracji za pośrednictwem rozproszonego systemu obsługi wiadomości, takich jak magistrala zdarzeń, masz problem z niepodzielnie aktualizowaniem oryginalnej bazy danych i publikowaniem zdarzenia (oznacza to, że obie operacje zostały zakończone lub żadna z nich). Na przykład w uproszczonym przykładzie pokazano wcześniej, kod zatwierdza dane do bazy danych, gdy cena produktu zostanie zmieniona, a następnie publikuje ProductPriceChangedIntegrationEvent komunikat. Początkowo może to wyglądać istotne, że te dwie operacje są wykonywane atomically. Jeśli jednak korzystasz z transakcji rozproszonej obejmującej bazę danych i brokera wiadomości, tak jak w starszych systemach, takich jak [Usługi kolejkowania wiadomości firmy Microsoft (MSMQ),](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx)nie jest to zalecane z powodów opisanych przez [oświadczenie CAP](https://www.quora.com/What-Is-CAP-Theorem-1).

Zasadniczo mikrousług używasz do tworzenia skalowalnych i wysoce dostępnych systemów. Upraszczając nieco, zasadokrwowe CAP mówi, że nie można zbudować (rozproszone) bazy danych (lub mikrousługi, która jest właścicielem modelu), który jest stale dostępny, silnie spójne *i* tolerancyjne dla każdej partycji. Należy wybrać dwie z tych trzech właściwości.

W architekturach opartych na mikrousługach należy wybrać dostępność i tolerancję i należy odwkreślić silną spójność. W związku z tym w większości nowoczesnych aplikacji opartych na mikrousługach zwykle nie chcesz używać transakcji rozproszonych w wiadomościach, tak jak podczas implementowania [transakcji rozproszonych](https://docs.microsoft.com/previous-versions/windows/desktop/ms681205(v=vs.85)) na podstawie koordynatora transakcji rozproszonych systemu Windows (DTC) z [usługą MSMQ](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx).

Wróćmy do początkowego problemu i jego przykładu. Jeśli usługa ulegnie awarii po zaktualizowaniu bazy danych (w tym przypadku zaraz po wierszu kodu z `_context.SaveChangesAsync()`), ale przed opublikowaniem zdarzenia integracji ogólny system może stać się niespójny. Może to być kluczowe dla firmy, w zależności od konkretnej operacji biznesowej, z którą masz do czynienia.

Jak wspomniano wcześniej w sekcji architektury, można mieć kilka podejść do radzenia sobie z tym problemem:

- Korzystanie z pełnego [wzorca pozyskiwania zdarzeń](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing).

- Korzystanie z [dziennika transakcji górnictwa](https://www.scoop.it/t/sql-server-transaction-log-mining).

- Korzystanie [ze wzorca Skrzynki nadawczej](https://www.kamilgrzybek.com/design/the-outbox-pattern/). Jest to tabela transakcyjna do przechowywania zdarzeń integracji (rozszerzenie transakcji lokalnej).

W tym scenariuszu przy użyciu pełnego źródła zdarzeń (ES) wzorzec jest jednym z najlepszych podejść, jeśli *nie* najlepsze. Jednak w wielu scenariuszach aplikacji może nie być w stanie zaimplementować pełnego systemu ES. ES oznacza przechowywanie tylko zdarzeń domeny w transakcyjnej bazie danych, zamiast przechowywania bieżących danych o stanie. Przechowywanie tylko zdarzeń domeny może mieć wielkie korzyści, takie jak dostępność historii systemu i możliwość określenia stanu systemu w dowolnym momencie w przeszłości. Jednak wdrożenie pełnego systemu ES wymaga ponownego prześledu większości systemu i wprowadza wiele innych zawiłości i wymagań. Na przykład należy użyć bazy danych specjalnie dla pozyskiwania zdarzeń, takich jak [Event Store](https://eventstore.org/)lub bazy danych zorientowanych na dokumenty, takich jak Azure Cosmos DB, MongoDB, Cassandra, CouchDB lub RavenDB. ES to świetne podejście do tego problemu, ale nie jest to najłatwiejsze rozwiązanie, chyba że jesteś już zaznajomiony z pozyskiwaniem zdarzeń.

Opcja użycia wyszukiwania dziennika transakcji początkowo wygląda na przezroczystą. Jednak aby użyć tego podejścia, mikrousługi musi być sprzężona z dziennikiem transakcji RDBMS, takich jak dziennik transakcji programu SQL Server. To prawdopodobnie nie jest pożądane. Inną wadą jest to, że aktualizacje niskiego poziomu rejestrowane w dzienniku transakcji może nie być na tym samym poziomie co zdarzenia integracji wysokiego poziomu. Jeśli tak, proces inżynierii odwrotnej tych operacji dziennika transakcji może być trudne.

Zrównoważone podejście jest połączeniem tabeli transakcyjnej bazy danych i uproszczonego wzorca ES. Można użyć stanu, takiego jak "gotowe do opublikowania zdarzenia", który można ustawić w oryginalnym zdarzeniu podczas zatwierdzania go do tabeli zdarzeń integracji. Następnie spróbuj opublikować zdarzenie w magistrali zdarzeń. Jeśli akcja publikowania zdarzenia powiedzie się, należy uruchomić inną transakcję w usłudze pochodzenia i przenieść stan z "gotowe do opublikowania zdarzenia" do "zdarzenia już opublikowane."

Jeśli akcja publikowania zdarzenia w magistrali zdarzeń nie powiedzie się, dane nadal nie będą niespójne w mikrousługach pochodzenia — nadal jest oznaczona jako "gotowa do opublikowania zdarzenia", a w odniesieniu do pozostałych usług zostanie ostatecznie spójna. Zawsze można mieć zadania w tle sprawdzanie stanu transakcji lub zdarzeń integracji. Jeśli zadanie znajdzie zdarzenie w stanie "Gotowe do opublikowania zdarzenia", może spróbować ponownie opublikować to zdarzenie w magistrali zdarzeń.

Należy zauważyć, że przy takim podejściu utrwalasz tylko zdarzenia integracji dla każdej mikrousługi pochodzenia i tylko zdarzenia, które chcesz komunikować się z innymi mikrousługami lub systemami zewnętrznymi. Natomiast w pełnym systemie ES przechowujesz również wszystkie zdarzenia domeny.

W związku z tym to wyważone podejście jest uproszczonym systemem ES. Potrzebujesz listy zdarzeń integracji z ich bieżącym stanem ("gotowy do opublikowania" w porównaniu do "opublikowanych"). Ale wystarczy tylko zaimplementować te stany dla zdarzeń integracji. I w tym podejściu nie trzeba przechowywać wszystkie dane domeny jako zdarzenia w transakcyjnej bazie danych, jak w pełnym systemie ES.

Jeśli używasz już relacyjnej bazy danych, można użyć tabeli transakcyjnej do przechowywania zdarzeń integracji. Aby osiągnąć niepodzielność w aplikacji, należy użyć procesu dwuetapowego opartego na transakcjach lokalnych. Zasadniczo masz IntegrationEvent tabeli w tej samej bazie danych, gdzie masz jednostek domeny. Ta tabela działa jako ubezpieczenie dla osiągnięcia niepodzielności, dzięki czemu można uwzględnić utrwalone zdarzenia integracji do tych samych transakcji, które zatwierdzają dane domeny.

Krok po kroku proces przebiega w ten sposób:

1. Aplikacja rozpoczyna transakcję lokalnej bazy danych.

2. Następnie aktualizuje stan jednostek domeny i wstawia zdarzenie do tabeli zdarzeń integracji.

3. Wreszcie, zatwierdza transakcję, więc można uzyskać żądaną niepodzielność, a następnie

4. Publikujesz zdarzenie w jakiś sposób (dalej).

Podczas implementowania kroków publikowania zdarzeń, masz następujące możliwości:

- Opublikuj zdarzenie integracji zaraz po zawiązaniu transakcji i użyj innej transakcji lokalnej, aby oznaczyć zdarzenia w tabeli jako opublikowane. Następnie użyj tabeli tylko jako artefakt do śledzenia zdarzeń integracji w przypadku problemów w mikrousług zdalnych i wykonać akcje kompensacyjne na podstawie przechowywanych zdarzeń integracji.

- Użyj tabeli jako rodzaju kolejki. Oddzielny wątek aplikacji lub proces zapyta tabelę zdarzeń integracji, publikuje zdarzenia do magistrali zdarzeń, a następnie używa transakcji lokalnej, aby oznaczyć zdarzenia jako opublikowane.

Rysunek 6-22 przedstawia architekturę dla pierwszego z tych podejść.

![Diagram niepodzielności podczas publikowania bez mikrousług procesu roboczego.](./media/subscribe-events/atomicity-publish-event-bus.png)

**Rysunek 6-22**. Niepodzielność podczas publikowania zdarzeń w magistrali zdarzeń

Podejście zilustrowane na rysunku 6-22 brakuje dodatkowej mikrousługi procesu roboczego, która jest odpowiedzialna za sprawdzanie i potwierdzanie powodzenia opublikowanych zdarzeń integracji. W przypadku awarii, że dodatkowe mikrousługi procesu sprawdzania procesu sprawdzania można odczytać zdarzenia z tabeli i opublikować je ponownie, czyli powtórzyć krok numer 2.

O drugim podejściu: używasz EventLog tabeli jako kolejki i zawsze używać mikrousług procesu roboczego do publikowania wiadomości. W takim przypadku proces jest podobny do przedstawionego na rysunku 6-23. Spowoduje to wyświetleń dodatkowe mikrousługi, a tabela jest pojedynczym źródłem podczas publikowania zdarzeń.

![Diagram niepodzielności podczas publikowania za pomocą mikrousług procesu roboczego.](./media/subscribe-events/atomicity-publish-worker-microservice.png)

**Rysunek 6-23**. Niepodzielność podczas publikowania zdarzeń w magistrali zdarzeń za pomocą mikrousług procesu roboczego

Dla uproszczenia przykład eShopOnContainers używa pierwszego podejścia (bez dodatkowych procesów lub mikrousług sprawdzania) plus magistrali zdarzeń. Jednak przykład eShopOnContainers nie obsługuje wszystkich możliwych przypadków awarii. W rzeczywistej aplikacji wdrożonej w chmurze, należy ogarnąć fakt, że problemy pojawią się w końcu i należy zaimplementować, że logika sprawdzania i ponownego wysłania. Korzystanie z tabeli jako kolejki może być bardziej skuteczne niż pierwsze podejście, jeśli masz tę tabelę jako pojedyncze źródło zdarzeń podczas publikowania ich (z pracownikiem) za pośrednictwem magistrali zdarzeń.

### <a name="implementing-atomicity-when-publishing-integration-events-through-the-event-bus"></a>Implementowanie niepodzielności podczas publikowania zdarzeń integracji za pośrednictwem magistrali zdarzeń

Poniższy kod pokazuje, jak można utworzyć pojedynczą transakcję obejmującą wiele obiektów DbContext — jeden kontekst związany z oryginalnymi danymi aktualizowanymi, a drugi kontekst związany z integrationeventlog tabeli.

Transakcja w poniższym przykładowym kodzie nie będzie odporna, jeśli połączenia z bazą danych mają jakikolwiek problem w czasie, gdy kod jest uruchomiony. Może się to zdarzyć w systemach opartych na chmurze, takich jak Azure SQL DB, które mogą przenosić bazy danych na serwerach. Aby zaimplementować transakcje odporne w wielu kontekstach, zobacz [Implementing resilient Entity Framework Core połączeń SQL](../implement-resilient-applications/implement-resilient-entity-framework-core-sql-connections.md) w dalszej części tego przewodnika.

Dla jasności w poniższym przykładzie przedstawiono cały proces w jednym kawałku kodu. Jednak implementacja eShopOnContainers jest refaktoryzowana i dzieli tę logikę na wiele klas, dzięki czemu jest łatwiejsza do utrzymania.

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

      _integrationEventLogService.MarkEventAsPublishedAsync(
                                                priceChangedEvent);
  }

  return Ok();
}

```

Po utworzeniu zdarzenia integracji ProductPriceChangedIntegrationEvent transakcja, która przechowuje oryginalną operację domeny (aktualizacja elementu katalogu) zawiera również trwałość zdarzenia w tabeli EventLog. To sprawia, że jest to pojedyncza transakcja i zawsze będzie można sprawdzić, czy wiadomości o zdarzeniach zostały wysłane.

Tabela dziennika zdarzeń jest aktualizowana niepodzielnie przy użyciu oryginalnej operacji bazy danych przy użyciu transakcji lokalnej dla tej samej bazy danych. Jeśli którakolwiek z operacji zakończy się niepowodzeniem, wyjątek zostanie zgłoszony, a transakcja wycofuje wszystkie zakończone operacje, zachowując w ten sposób spójność między operacjami domeny a komunikatami o zdarzeniach zapisanymi w tabeli.

### <a name="receiving-messages-from-subscriptions-event-handlers-in-receiver-microservices"></a>Odbieranie komunikatów z subskrypcji: programy obsługi zdarzeń w mikrousługach odbiorcy

Oprócz logiki subskrypcji zdarzeń należy zaimplementować wewnętrzny kod dla programów obsługi zdarzeń integracji (takich jak metoda wywołania zwrotnego). Program obsługi zdarzeń jest, gdzie można określić, gdzie komunikaty o zdarzeniach określonego typu będą odbierane i przetwarzane.

Program obsługi zdarzeń najpierw odbiera wystąpienie zdarzenia z magistrali zdarzeń. Następnie lokalizuje składnik do przetworzenia związane z tym zdarzeniem integracji, propagacji i utrwalania zdarzenia jako zmiany stanu w mikrousługi odbiornika. Na przykład jeśli ProductPriceChanged zdarzenie pochodzi z mikrousługi katalogu, jest obsługiwany w mikrousługi koszyka i zmienia stan w tym mikrousługi koszyka odbiornika, jak pokazano w poniższym kodzie.

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

Program obsługi zdarzeń musi sprawdzić, czy produkt istnieje w dowolnym wystąpieniu koszyka. Aktualizuje również cenę towaru dla każdego powiązanego elementu zamówienia koszyka. Na koniec tworzy alert, który ma być wyświetlany użytkownikowi o zmianie ceny, jak pokazano na rysunku 6-24.

![Zrzut ekranu przedstawiający przeglądarkę z powiadomieniem o zmianie ceny w koszyku użytkownika.](./media/subscribe-events/display-item-price-change.png)

**Rysunek 6-24**. Wyświetlanie zmiany ceny towaru w koszyku, zgodnie z komunikatami o zdarzeniach integracji

## <a name="idempotency-in-update-message-events"></a>Idempotency w zdarzeniach wiadomości aktualizacji

Ważnym aspektem zdarzeń wiadomości aktualizacji jest, że błąd w dowolnym momencie komunikacji powinien spowodować ponowione próby wiadomości. W przeciwnym razie zadanie w tle może próbować opublikować zdarzenie, które zostało już opublikowane, tworząc warunek wyścigu. Upewnij się, że aktualizacje są idempotentności lub że zawierają wystarczające informacje, aby upewnić się, że można wykryć duplikat, odrzucić go i wysłać z powrotem tylko jedną odpowiedź.

Jak wspomniano wcześniej, idempotency oznacza, że operacja może być wykonywana wiele razy bez zmiany wyniku. W środowisku obsługi wiadomości, jak podczas komunikowania się zdarzeń, zdarzenie jest idempotentne, jeśli może być dostarczone wiele razy bez zmiany wyniku dla mikrousługi odbiornika. Może to być konieczne ze względu na charakter samego zdarzenia lub ze względu na sposób, w jaki system obsługuje zdarzenie. Idempotency wiadomości jest ważne w każdej aplikacji, która używa wiadomości, nie tylko w aplikacjach, które implementują wzorzec magistrali zdarzeń.

Przykładem operacji idempotentna jest instrukcja SQL, która wstawia dane do tabeli tylko wtedy, gdy te dane nie są jeszcze w tabeli. Nie ma znaczenia, ile razy można uruchomić, że wstawić instrukcję SQL; wynik będzie taki sam — tabela będzie zawierać te dane. Idempotency jak to może być również konieczne podczas czynienia z wiadomościami, jeśli wiadomości mogą być potencjalnie wysyłane i w związku z tym przetwarzane więcej niż jeden raz. Na przykład jeśli logika ponawiania powoduje, że nadawca wysyła dokładnie tę samą wiadomość więcej niż jeden raz, należy upewnić się, że jest idempotentne.

Możliwe jest projektowanie idempotentne wiadomości. Na przykład możesz utworzyć zdarzenie z napisem "ustaw cenę produktu na 25 USD" zamiast "dodaj 5 USD do ceny produktu". Można bezpiecznie przetworzyć pierwszą wiadomość dowolną liczbę razy, a wynik będzie taki sam. To nie jest prawda w przypadku drugiego przesłania. Ale nawet w pierwszym przypadku możesz nie chcieć przetworzyć pierwszego zdarzenia, ponieważ system mógł również wysłać nowsze zdarzenie zmiany ceny i nadpisujesz nową cenę.

Innym przykładem może być zdarzenie zakończone zamówieniem, które jest propagowane do wielu subskrybentów. Aplikacja musi upewnić się, że informacje o zamówieniu są aktualizowane w innych systemach tylko raz, nawet jeśli istnieją zduplikowane zdarzenia wiadomości dla tego samego zdarzenia zakończonego zamówienia.

Jest to wygodne, aby mieć pewnego rodzaju tożsamości na zdarzenie, dzięki czemu można utworzyć logikę, która wymusza, że każde zdarzenie jest przetwarzane tylko raz na odbiornik.

Niektóre przetwarzanie wiadomości jest z natury idempotentne. Na przykład jeśli system generuje miniatury obrazów, może nie mieć znaczenia, ile razy jest przetwarzany komunikat o wygenerowanej miniaturze; wynik jest taki, że miniatury są generowane i są takie same za każdym razem. Z drugiej strony, operacje takie jak wywołanie bramki płatniczej w celu obciążenia karty kredytowej mogą w ogóle nie być dowodu osobistego. W takich przypadkach należy upewnić się, że przetwarzanie wiadomości wiele razy ma oczekiwany efekt.

### <a name="additional-resources"></a>Zasoby dodatkowe

- **Honorowanie idempotency wiadomości** \
  <https://docs.microsoft.com/previous-versions/msp-n-p/jj591565(v=pandp.10)#honoring-message-idempotency>

## <a name="deduplicating-integration-event-messages"></a>Deduplikowanie komunikatów o zdarzeniach integracji

Możesz się upewnić, że zdarzenia wiadomości są wysyłane i przetwarzane tylko raz na subskrybenta na różnych poziomach. Jednym ze sposobów jest użycie funkcji deduplikacji oferowanej przez używaną infrastrukturę obsługi wiadomości. Innym jest zaimplementowanie logiki niestandardowej w mikrousługi docelowej. Posiadanie weryfikacji zarówno na poziomie transportu, jak i na poziomie aplikacji jest najlepszym rozwiązaniem.

### <a name="deduplicating-message-events-at-the-eventhandler-level"></a>Deduplikowanie zdarzeń wiadomości na poziomie EventHandler

Jednym ze sposobów, aby upewnić się, że zdarzenie jest przetwarzane tylko raz przez dowolnego odbiorcy jest implementowanie pewnej logiki podczas przetwarzania zdarzeń wiadomości w programach obsługi zdarzeń. Na przykład jest to podejście używane w aplikacji eShopOnContainers, jak widać w [kodzie źródłowym UserCheckoutAcceptedIntegrationEventHandler klasy](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) po odebraniu `UserCheckoutAcceptedIntegrationEvent` zdarzenia integracji. (W takim przypadku `CreateOrderCommand` jest zawijany `IdentifiedCommand` `eventMsg.RequestId` z , przy użyciu jako identyfikator, przed wysłaniem go do programu obsługi polecenia).

### <a name="deduplicating-messages-when-using-rabbitmq"></a>Deduplikowanie wiadomości podczas korzystania z RabbitMQ

W przypadku wystąpienia sporadyczne błędy sieci wiadomości mogą być duplikowane, a odbiornik wiadomości musi być gotowy do obsługi tych zduplikowanych wiadomości. Jeśli to możliwe, odbiorniki powinny obsługiwać wiadomości w sposób idempotentny, co jest lepsze niż jawne obchodzenia się z nimi za pomocą deduplikacji.

Zgodnie z [dokumentacją RabbitMQ](https://www.rabbitmq.com/reliability.html#consumer), "Jeśli wiadomość zostanie dostarczona do konsumenta, a następnie ponownie w kolejce (ponieważ nie została potwierdzona przed przerwaniem połączenia konsumenckiego), wówczas RabbitMQ ustawi na niej ponownie dostarczoną flagę, gdy zostanie dostarczona ponownie (czy to do tego samego konsumenta, czy do innego).

Jeśli ustawiona jest flaga "redelivered", odbiorca musi wziąć to pod uwagę, ponieważ wiadomość mogła już zostać przetworzona. Ale to nie jest gwarantowane; wiadomość może nigdy nie dotarła do odbiorcy po opuszczeniu brokera wiadomości, być może z powodu problemów z siecią. Z drugiej strony, jeśli flaga "redelivered" nie jest ustawiona, jest gwarantowana, że wiadomość nie została wysłana więcej niż jeden raz. W związku z tym odbiornik musi deduplikować wiadomości lub przetwarzać wiadomości w sposób idempotentny tylko wtedy, gdy flaga "redelivered" jest ustawiona w wiadomości.

### <a name="additional-resources"></a>Zasoby dodatkowe

- **Rozwidał eShopOnContainers przy użyciu NServiceBus (Dane oprogramowanie)** \
    <https://go.particular.net/eShopOnContainers>

- **Wiadomości sterowane zdarzeniami** \
    <https://patterns.arcitura.com/soa-patterns/design_patterns/event_driven_messaging>

- **Jimmy Bogard. Refaktoryzowanie w kierunku odporności: ocena sprzężenia** \
    <https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/>

- **Publikuj-Subskrybuj kanał** \
    <https://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html>

- **Komunikowanie się między ograniczonymi kontekstami** \
    <https://docs.microsoft.com/previous-versions/msp-n-p/jj591572(v=pandp.10)>

- **Spójność ostateczna** \
    <https://en.wikipedia.org/wiki/Eventual_consistency>

- **Philip Brown. Strategie integracji ograniczonych kontekstów** \
    <https://www.culttt.com/2014/11/26/strategies-integrating-bounded-contexts/>

- **Chris Richardson. Tworzenie mikrousług transakcyjnych przy użyciu agregatów, pozyskiwania zdarzeń i CQRS - część 2** \
    <https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson>

- **Chris Richardson. Wzorzec pozyskiwania zdarzeń** \
    <https://microservices.io/patterns/data/event-sourcing.html>

- **Przedstawiamy pozyskiwanie zdarzeń** \
    <https://docs.microsoft.com/previous-versions/msp-n-p/jj591559(v=pandp.10)>

- **Baza danych Magazynu zdarzeń**. Oficjalna strona. \
    <https://geteventstore.com/>

- **Patryk Nommensen. Zarządzanie danymi oparte na zdarzeniach dla mikrousług** \
    <https://dzone.com/articles/event-driven-data-management-for-microservices-1>

- **The CAP -theorem** \
    <https://en.wikipedia.org/wiki/CAP_theorem>

- **Co to jest roszt CAP?** \
    <https://www.quora.com/What-Is-CAP-Theorem-1>

- **Podkład spójności danych** \
    <https://docs.microsoft.com/previous-versions/msp-n-p/dn589800(v=pandp.10)>

- **Rick Saling. Teoria WPR: Dlaczego "Wszystko jest inne" z chmurą i Internetem** \
    <https://docs.microsoft.com/archive/blogs/rickatmicrosoft/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/>

- **Eric Brewer. CAP dwanaście lat później: Jak zmieniły się "zasady"** \
    <https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed>

- **Azure Service Bus. Wiadomości brokerskie: wykrywanie duplikatów**  \
    <https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25>

- **Przewodnik niezawodności** (dokumentacja RabbitMQ) \
    <https://www.rabbitmq.com/reliability.html#consumer>

> [!div class="step-by-step"]
> [Poprzedni](rabbitmq-event-bus-development-test-environment.md)
> [następny](test-aspnet-core-services-web-apps.md)

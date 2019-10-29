---
title: Subskrybowanie zdarzeń
description: Architektura mikrousług platformy .NET dla aplikacji platformy .NET w kontenerze | Zapoznaj się ze szczegółami dotyczącymi publikowania i subskrypcji zdarzeń integracji.
ms.date: 10/02/2018
ms.openlocfilehash: 208b0f27aa1e6ceb6686e9e846b6e31d9f1c74df
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73035639"
---
# <a name="subscribing-to-events"></a>Subskrybowanie zdarzeń

Pierwszym krokiem przy korzystaniu z magistrali zdarzeń jest subskrybowanie mikrousług do zdarzeń, które chcą odebrać. Należy to zrobić w mikrousługach odbiornika.

Poniższy prosty kod pokazuje, co każda mikrousługa odbiornika musi zaimplementować podczas uruchamiania usługi (czyli w klasie `Startup`), dzięki czemu subskrybuje potrzebne zdarzenia. W takim przypadku `basket.api` mikrousługa musi subskrybować `ProductPriceChangedIntegrationEvent` i wiadomości `OrderStartedIntegrationEvent`.

Na przykład podczas subskrybowania zdarzenia `ProductPriceChangedIntegrationEvent`, dzięki czemu usługa koszyka wie o wszelkich zmianach w cenie produktu i umożliwia mu ostrzeganie użytkownika o zmianie, jeśli ten produkt znajduje się w koszyku użytkownika.

```csharp
var eventBus = app.ApplicationServices.GetRequiredService<IEventBus>();

eventBus.Subscribe<ProductPriceChangedIntegrationEvent,
                   ProductPriceChangedIntegrationEventHandler>();

eventBus.Subscribe<OrderStartedIntegrationEvent,
                   OrderStartedIntegrationEventHandler>();

```

Po uruchomieniu tego kodu, mikrousługa subskrybenta będzie nasłuchiwać kanałów RabbitMQ. Po nadejściu dowolnych komunikatów typu ProductPriceChangedIntegrationEvent kod wywołuje program obsługi zdarzeń, który jest do niego przeszedł, i przetwarza zdarzenie.

## <a name="publishing-events-through-the-event-bus"></a>Publikowanie zdarzeń za pomocą magistrali zdarzeń

Na koniec wiadomość nadawcy (mikrousługa pochodzenia) publikuje zdarzenia integracji z kodem podobnym do poniższego przykładu. (Jest to uproszczony przykład, który nie wymaga niepodzielności na konto). Należy zaimplementować podobny kod za każdym razem, gdy zdarzenie musi być propagowane dla wielu mikrousług, zwykle bezpośrednio po zatwierdzeniu danych lub transakcji z mikrousługi źródłowej.

Najpierw obiekt implementacji usługi Event Bus (oparty na RabbitMQ lub na podstawie usługi Service Bus) zostałby dodany do konstruktora kontrolera, jak w poniższym kodzie:

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

Następnie należy użyć jej z metod na kontrolerze, takich jak w metodzie UpdateProduct:

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

W takim przypadku, ponieważ mikrousługa jest prostą CRUD, ten kod jest umieszczany bezpośrednio w kontrolerze interfejsu API sieci Web.

W bardziej zaawansowanych mikrousługach, takich jak użycie podejścia CQRS, można je zaimplementować w klasie `CommandHandler` w ramach metody `Handle()`.

### <a name="designing-atomicity-and-resiliency-when-publishing-to-the-event-bus"></a>Projektowanie niepodzielności i odporności podczas publikowania w usłudze Event Bus

Po opublikowaniu zdarzeń integracji za pomocą rozproszonego systemu obsługi komunikatów, takiego jak magistrala zdarzeń, występuje problem z niepodzielną aktualizacją pierwotnej bazy danych oraz publikowaniem zdarzenia (to oznacza, że obie operacje zostały zakończone lub nie zostały wykonane). Na przykład, w uproszczonym przykładzie pokazanym wcześniej, kod zatwierdza dane do bazy danych w momencie zmiany ceny produktu, a następnie publikuje komunikat ProductPriceChangedIntegrationEvent. Początkowo może to mieć kluczowe znaczenie, że te dwie operacje są wykonywane niepodzielnie. Jeśli jednak korzystasz z transakcji rozproszonej obejmującej bazę danych i brokera komunikatów, tak jak w starszych systemach, takich jak [Usługa kolejkowania komunikatów (MSMQ)](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx), nie jest to zalecane z powodów opisanych przez [theorem Cap](https://www.quora.com/What-Is-CAP-Theorem-1).

W zasadzie mikrousługi są używane do tworzenia skalowalnych i wysoko dostępnych systemów. Uproszczenie, theorem CAP oznacza, że nie można utworzyć (rozproszonej) bazy danych (lub mikrousługi, która jest właścicielem modelu), która jest stale dostępna, silnie spójna *i* odporna na każdą partycję. Musisz wybrać dwie z tych trzech właściwości.

W przypadku architektur opartych na mikrousługach należy wybrać dostępność i tolerancję, a także wyróżnić silną spójność. W związku z tym w większości nowoczesnych aplikacji opartych na mikrousługach zwykle nie ma potrzeby korzystania z transakcji rozproszonych w ramach komunikatów, tak jak podczas implementowania [transakcji rozproszonych](https://docs.microsoft.com/previous-versions/windows/desktop/ms681205(v=vs.85)) w oparciu o Distributed Transaction Coordinator systemu Windows (DTC). z [usługą MSMQ](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx).

Wróć do początkowego problemu i jego przykładu. Jeśli usługa ulegnie awarii po zaktualizowaniu bazy danych (w tym przypadku bezpośrednio po wierszu kodu z kontekstem \_. SaveChangesAsync ()), ale przed opublikowaniem zdarzenia integracji, ogólny system może stać się niespójny. Może to być krytyczne dla firmy, w zależności od konkretnej operacji biznesowej.

Jak wspomniano wcześniej w sekcji architektura, można mieć kilka metod postępowania z tym problemem:

- Przy użyciu [wzorca pozyskiwania pełnego zdarzenia](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing).

- Korzystanie z [wyszukiwania w dzienniku transakcji](https://www.scoop.it/t/sql-server-transaction-log-mining).

- Przy użyciu [wzorca skrzynki nadawczej](https://www.kamilgrzybek.com/design/the-outbox-pattern/). Jest to tabela transakcyjna do przechowywania zdarzeń integracji (rozszerzających transakcję lokalną).

W tym scenariuszu należy użyć wzorca źródeł pełnych zdarzeń, *Jeśli nie jest to najlepsze rozwiązanie.* Jednak w wielu scenariuszach aplikacji może nie być możliwe zaimplementowanie systemu całkowitego ES. ES oznacza przechowywanie tylko zdarzeń domeny w transakcyjnej bazie danych, a nie przechowywanie bieżących danych stanu. Przechowywanie tylko zdarzeń domeny może mieć znakomite korzyści, takie jak udostępnienie historii systemu i możliwość ustalenia stanu systemu w dowolnym momencie w przeszłości. Jednak wdrożenie systemu Full ES wymaga przeprowadzenia ponownej architektury większości systemów i wprowadzono wiele innych złożoności i wymagań. Można na przykład użyć bazy danych przeznaczonej do określania źródła zdarzeń, takich jak [Magazyn zdarzeń](https://eventstore.org/), lub bazy danych zorientowanej na dokumenty, takiej jak Azure Cosmos DB, MongoDB, Cassandra, CouchDB lub RavenDB. ES to doskonałe rozwiązanie tego problemu, ale nie najłatwiej, chyba że masz już doświadczenie ze źródłem zdarzeń.

Opcja korzystania z wyszukiwania w dzienniku transakcji początkowo wygląda bardzo przejrzysta. Aby jednak korzystać z tego podejścia, mikrousługa musi być dołączona do dziennika transakcji RDBMS, na przykład dziennika transakcji SQL Server. Prawdopodobnie nie jest to pożądane. Kolejną wadą jest to, że aktualizacje niskiego poziomu rejestrowane w dzienniku transakcji mogą nie znajdować się na tym samym poziomie co zdarzenia integracji wysokiego poziomu. W takim przypadku proces odtwarzania tych operacji dziennika transakcji może być trudny.

Zrównoważonym podejściem jest mieszanka tabeli baz danych transakcyjnych i uproszczonego wzorca ES. Można użyć stanu, takiego jak "gotowe do opublikowania zdarzenia", które zostało ustawione w oryginalnym zdarzeniu po zatwierdzeniu go do tabeli zdarzeń integracji. Następnie próbujesz opublikować zdarzenie w usłudze Event Bus. W przypadku pomyślnego wykonania akcji Opublikuj zdarzenie należy rozpocząć kolejną transakcję w usłudze pochodzenia i przenieść stan z "gotowe do opublikowania zdarzenia" do "już opublikowanego zdarzenia".

Jeśli akcja Publikuj — zdarzenie w usłudze Event Bus zakończy się niepowodzeniem, dane nadal nie będą spójne w ramach mikrousługi, ale nadal są oznaczone jako "gotowe do opublikowania zdarzenia" i w odniesieniu do reszty usług, będzie ostatecznie spójna. Zadania w tle można zawsze sprawdzać stan transakcji lub zdarzeń integracji. Jeśli zadanie znajdzie zdarzenie w stanie "gotowe do opublikowania zdarzenia", może spróbować ponownie opublikować to zdarzenie w usłudze Event Bus.

Należy zauważyć, że w tym podejściu są utrwalane tylko zdarzenia integracji dla każdej mikrousługi pochodzenia i tylko zdarzenia, które mają być przekazywane do innych mikrousług lub systemów zewnętrznych. W przeciwieństwie do systemu w pełni Wyes wszystkie zdarzenia domeny również są przechowywane.

W związku z tym to zrównoważone podejście to uproszczony system. Wymagana jest lista zdarzeń integracji z ich bieżącym stanem ("gotowe do opublikowania" zamiast "opublikowany"). Ale musisz tylko zaimplementować te Stany dla zdarzeń integracji. W tej metodzie nie trzeba przechowywać wszystkich danych domeny jako zdarzeń w transakcyjnej bazie danych, tak jak w przypadku systemu w pełni Wyes.

Jeśli korzystasz już z relacyjnej bazy danych, możesz użyć tabeli transakcyjnej do przechowywania zdarzeń integracji. Aby uzyskać niepodzielność w aplikacji, należy użyć dwuetapowego procesu opartego na lokalnych transakcjach. Zasadniczo istnieje tabela IntegrationEvent w tej samej bazie danych, w której znajdują się jednostki domeny. Ta tabela działa jako ubezpieczenie do osiągnięcia niepodzielności, aby uwzględnić utrwalone zdarzenia integracji w tych samych transakcjach, które zatwierdzają dane domeny.

Krok po kroku proces przebiega następująco:

1. Aplikacja rozpoczyna lokalną transakcję bazy danych.

2. Następnie aktualizuje stan jednostek domeny i wstawia zdarzenie do tabeli zdarzeń integracji.

3. Na koniec zatwierdza transakcji, dzięki czemu uzyskasz odpowiednią niepodzielność, a następnie

4. Wydarzenie można opublikować w dowolny sposób (dalej).

Podczas wdrażania kroków publikowania zdarzeń można wybrać następujące opcje:

- Opublikuj wydarzenie integracji bezpośrednio po zatwierdzeniu transakcji i użyj innej transakcji lokalnej, aby oznaczyć zdarzenia w tabeli jako publikowane. Następnie należy użyć tabeli jako artefaktu do śledzenia zdarzeń związanych z integracją w przypadku problemów z mikrousługami zdalnymi, a także wykonywać działania wyrównawcze na podstawie przechowywanych zdarzeń integracji.

- Użyj tabeli jako rodzaju kolejki. Oddzielny wątek lub proces aplikacji wysyła zapytanie do tabeli zdarzeń integracji, publikuje zdarzenia do magistrali zdarzeń, a następnie używa transakcji lokalnej do oznaczania zdarzeń jako opublikowanych.

Rysunek 6-22 przedstawia architekturę dla pierwszego z tych metod.

![Jedno podejście do obsługi niepodzielności podczas publikowania zdarzeń: Użyj jednej transakcji, aby zatwierdzić zdarzenie w tabeli dziennika zdarzeń, a następnie inna transakcja do opublikowania (używana w eShopOnContainers)](./media/image23.png)

**Rysunek 6-22**. Niepodzielność przy publikowaniu zdarzeń do magistrali zdarzeń

Na rysunku 6-22 Brak dodatkowej mikrousługi roboczej, która jest odpowiedzialna za sprawdzenie i potwierdzenie sukcesu opublikowanych zdarzeń integracji. W razie awarii, dodatkowy mikrousługa dla procesu roboczego kontrolera może odczytywać zdarzenia z tabeli i ponownie je opublikować, czyli powtórzyć krok numer 2.

Informacje o drugim podejściu: należy użyć tabeli EventLog jako kolejki i zawsze używać mikrousługi procesu roboczego do publikowania komunikatów. W takim przypadku proces jest podobny do przedstawionego na rysunku 6-23. Powoduje to wyświetlenie dodatkowej mikrousługi, a tabela jest pojedynczym źródłem przy publikowaniu zdarzeń.

![Inne podejście do obsługi niepodzielności: Publikuj w tabeli dziennika zdarzeń, a następnie zapublikuj zdarzenie przy użyciu innej mikrousługi (proces roboczy w tle).](./media/image24.png)

**Rysunek 6-23**. Niepodzielność przy publikowaniu zdarzeń do magistrali zdarzeń za pomocą mikrousługi procesu roboczego

Dla uproszczenia przykład eShopOnContainers używa pierwszego podejścia (bez dodatkowych procesów lub mikrousług sprawdzania) oraz magistrali zdarzeń. Jednak eShopOnContainers nie obsługuje wszystkich możliwych przypadków niepowodzeń. W rzeczywistej aplikacji wdrożonej w chmurze należy zastanowić się, że problemy będą nadal występować i należy zaimplementować ten test i ponownie Wyślij logikę. Użycie tabeli jako kolejki może być bardziej efektywne niż w przypadku pierwszej metody, jeśli istnieje taka tabela jako pojedyncze źródło zdarzeń podczas publikowania ich (z procesem roboczym) za pośrednictwem magistrali zdarzeń.

### <a name="implementing-atomicity-when-publishing-integration-events-through-the-event-bus"></a>Implementowanie niepodzielności podczas publikowania zdarzeń integracji za pomocą magistrali zdarzeń

Poniższy kod pokazuje, jak można utworzyć pojedynczą transakcję obejmującą wiele obiektów DbContext — jednego kontekstu związanego z aktualizowanymi oryginalnymi danymi oraz drugi kontekst związany z tabelą IntegrationEventLog.

Należy pamiętać, że transakcja w poniższym przykładowym kodzie nie będzie odporna, jeśli połączenia z bazą danych mają dowolny problem w chwili, gdy kod jest uruchomiony. Taka sytuacja może wystąpić w systemach opartych na chmurze, takich jak Azure SQL DB, co może przenosić bazy danych między serwerami. Aby zaimplementować odporne transakcje w wielu kontekstach, zobacz sekcję [implementowanie odpornych Entity Framework Core połączeń SQL](../implement-resilient-applications/implement-resilient-entity-framework-core-sql-connections.md) w dalszej części tego przewodnika.

W przypadku przejrzystości Poniższy przykład pokazuje cały proces w pojedynczym fragmencie kodu. Jednak implementacja eShopOnContainers jest faktycznie Refaktoryzacja i dzieli tę logikę na wiele klas, dzięki czemu łatwiej jest ją konserwować.

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

Po utworzeniu zdarzenia integracji ProductPriceChangedIntegrationEvent transakcja, która przechowuje pierwotną operację domeny (aktualizacja elementu katalogu) również obejmuje trwałość zdarzenia w tabeli EventLog. Powoduje to pojedyncze transakcję i zawsze będzie można sprawdzić, czy komunikaty o zdarzeniach zostały wysłane.

Tabela dziennika zdarzeń jest aktualizowana w sposób niepodzielny z pierwotną operacją bazy danych przy użyciu transakcji lokalnej w odniesieniu do tej samej bazy danych. Jeśli jakakolwiek operacja zakończy się niepowodzeniem, zgłaszany jest wyjątek, a transakcja wycofuje każdą ukończoną operację, w konsekwencji zachowanie spójności między operacjami domeny i komunikatami zdarzeń zapisanymi w tabeli.

### <a name="receiving-messages-from-subscriptions-event-handlers-in-receiver-microservices"></a>Otrzymywanie komunikatów z subskrypcji: programy obsługi zdarzeń w mikrousługach odbiornika

Oprócz logiki subskrypcji zdarzeń należy zaimplementować wewnętrzny kod dla programów obsługi zdarzeń integracji (na przykład metodę wywołania zwrotnego). Procedura obsługi zdarzeń służy do określania miejsca, w którym są odbierane i przetwarzane komunikaty o zdarzeniu określonego typu.

Program obsługi zdarzeń najpierw odbiera wystąpienie zdarzenia z magistrali zdarzeń. Następnie lokalizuje składnik do przetworzenia powiązane z tym zdarzeniem integracji, propagowanie i utrwalanie zdarzenia jako zmiany stanu w mikrousłudze odbiornika. Na przykład, jeśli zdarzenie ProductPriceChanged pochodzi z mikrousługi katalogu, jest ono obsługiwane w mikrousłudze koszyka i zmienia stan w tej mikrousłudze dla koszyka odbiornik, jak pokazano w poniższym kodzie.

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

Program obsługi zdarzeń musi sprawdzić, czy produkt istnieje w żadnym z wystąpień koszyka. Aktualizuje także cenę elementu dla każdego elementu powiązanego z wierszem koszyka. Na koniec tworzy alert, który będzie wyświetlany użytkownikowi w sprawie zmiany ceny, jak pokazano na rysunku 6-24.

![Widok przeglądarki powiadamiania o zmianie procesu w koszyku użytkownika.](./media/image25.png)

**Rysunek 6-24**. Wyświetlanie zmiany ceny elementu w koszyku, zgodnie z poinformowaniem o zdarzeniach integracji

## <a name="idempotency-in-update-message-events"></a>Idempotentności w Aktualizuj zdarzenia komunikatów

Ważnym aspektem zdarzeń aktualizacji komunikatów jest to, że awaria w dowolnym momencie komunikacji powinna spowodować, że komunikat zostanie ponowiony. W przeciwnym razie zadanie w tle może próbować opublikować zdarzenie, które zostało już opublikowane, tworząc sytuację wyścigu. Musisz się upewnić, że aktualizacje są idempotentne lub że zapewniają wystarczające informacje, aby upewnić się, że można wykryć duplikat, odrzucić go i wysłać tylko jedną odpowiedź.

Jak wspomniano wcześniej, idempotentności oznacza, że operacja może być wykonana wiele razy bez zmiany wyniku. W środowisku obsługi komunikatów, podobnie jak podczas komunikacji z zdarzeniami, zdarzenie jest idempotentne, jeśli może być dostarczone wiele razy bez zmiany wyniku dla mikrousługi odbiornika. Może to być konieczne ze względu na charakter samego zdarzenia lub ze względu na sposób, w jaki system obsługuje zdarzenie. W przypadku aplikacji korzystających z komunikatów, a nie tylko w aplikacjach, które implementują wzorzec magistrali zdarzeń, idempotentności jest ważna.

Przykładem operacji idempotentne jest instrukcja SQL, która wstawia dane do tabeli tylko wtedy, gdy dane nie są jeszcze w tabeli. Nie ma znaczenia, ile razy jest wykonywanych w instrukcji SQL INSERT; wynik będzie taki sam — tabela będzie zawierać te dane. Idempotentności takie jak może być również konieczne w przypadku komunikacji z komunikatami, jeśli mogą być potencjalnie wysyłane i przetwarzane więcej niż jeden raz. Na przykład, jeśli logika ponawiania powoduje, że nadawca wysyła dokładnie ten sam komunikat więcej niż raz, należy się upewnić, że jest idempotentne.

Możliwe jest zaprojektowanie komunikatów idempotentne. Na przykład można utworzyć zdarzenie "Ustaw cenę produktu na $25" zamiast "Dodaj $5 do ceny produktu". Można bezpiecznie przetwarzać pierwszy komunikat dowolną liczbę razy, a wynik będzie taki sam. To nie jest prawdziwe dla drugiego komunikatu. Jednak nawet w pierwszym przypadku można nie chcieć przetwarzać pierwszego zdarzenia, ponieważ system mógł również przesłać nowsze zdarzenie zmiany ceny i zastąpić nową cenę.

Innym przykładem może być zdarzenie ukończone w kolejności, które jest propagowane do wielu subskrybentów. Ważne jest, aby informacje o zamówieniach były aktualizowane w innych systemach tylko raz, nawet jeśli istnieją zduplikowane zdarzenia komunikatów dla tego samego zdarzenia Order-ukończony.

Jest wygodne w przypadku pewnego rodzaju tożsamości dla każdego zdarzenia, dzięki czemu można utworzyć logikę, która wymusza, że każde zdarzenie jest przetwarzane tylko raz dla każdego odbiorcy.

Niektóre przetwarzanie komunikatów jest z natury idempotentne. Na przykład jeśli system generuje miniatury obrazów, może nie mieć znaczenia, ile razy komunikat o wygenerowanej miniaturze został przetworzony; wynikiem jest to, że miniatury są generowane i są takie same, jak zawsze. Z drugiej strony operacje, takie jak wywołanie bramy płatności do naliczania opłat za kartę kredytową, nie mogą być idempotentne w ogóle. W takich przypadkach należy upewnić się, że przetwarzanie komunikatu wiele razy ma oczekiwany efekt.

### <a name="additional-resources"></a>Dodatkowe zasoby

- **Uznawanie wiadomości idempotentności**  
  <https://docs.microsoft.com/previous-versions/msp-n-p/jj591565(v=pandp.10)#honoring-message-idempotency>

## <a name="deduplicating-integration-event-messages"></a>Deduplikowanie komunikatów zdarzeń integracji

Można upewnić się, że zdarzenia komunikatów są wysyłane i przetwarzane tylko raz dla każdego subskrybenta na różnych poziomach. Jednym ze sposobów jest użycie funkcji deduplikacji oferowanej przez używaną infrastrukturę obsługi komunikatów. Innym jest zaimplementowanie logiki niestandardowej w mikrousłudze docelowej. Posiadanie walidacji na poziomie transportu i na poziomie aplikacji jest najlepszym trafieniem.

### <a name="deduplicating-message-events-at-the-eventhandler-level"></a>Deduplikowanie zdarzeń komunikatów na poziomie EventHandler

Jednym ze sposobów, aby upewnić się, że zdarzenie jest przetwarzane tylko raz przez dowolnego odbiorcę, przez implementację pewnej logiki podczas przetwarzania zdarzeń komunikatów w procedurach obsługi zdarzeń. Na przykład jest to podejście używane w aplikacji eShopOnContainers, jak można je zobaczyć w [kodzie źródłowym klasy UserCheckoutAcceptedIntegrationEventHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) , gdy odbierze zdarzenie integracji UserCheckoutAcceptedIntegrationEvent. (W tym przypadku CreateOrderCommand z IdentifiedCommand przy użyciu eventMsg. Identyfikator żądania jako identyfikatora, przed wysłaniem go do programu obsługi poleceń).

### <a name="deduplicating-messages-when-using-rabbitmq"></a>Deduplikowanie komunikatów przy użyciu RabbitMQ

W przypadku sporadycznych awarii sieci można duplikować komunikaty, a odbiorca wiadomości musi być gotowy do obsługi tych zduplikowanych komunikatów. Jeśli to możliwe, odbiorcy powinny obsługiwać komunikaty w idempotentne sposób, który jest lepiej niż jawnie obsługujący deduplikację.

Zgodnie z [dokumentacją RabbitMQ](https://www.rabbitmq.com/reliability.html#consumer)", jeśli wiadomość jest dostarczana do konsumenta, a następnie ponownie umieszczana w kolejce (ponieważ nie została potwierdzona przed porzuceniem połączenia przez klienta, na przykład), RabbitMQ ustawi na niej flagę ponownie dostarczone, gdy zostanie on dostarczony ponownie (niezależnie od tego, czy jest to ten sam Klient czy inny).

Jeśli ustawiono flagę "redostarczony", odbiorca musi uwzględnić to konto, ponieważ komunikat mógł już zostać przetworzony. Ale nie jest to gwarantowane; komunikat nigdy nie dotarł do odbiorcy po jego przejściu do brokera komunikatów, prawdopodobnie z powodu problemów z siecią. Z drugiej strony, jeśli flaga "redostarczany" nie została ustawiona, jest gwarantowane, że wiadomość nie została wysłana więcej niż raz. W związku z tym odbiornik musi deduplikowanie komunikatów lub przetwarzać komunikaty w idempotentne sposób tylko wtedy, gdy flaga "redostarczany" została ustawiona w komunikacie.

### <a name="additional-resources"></a>Dodatkowe zasoby

- **EShopOnContainers z rozwidleniem przy użyciu NServiceBus (konkretne oprogramowanie)**  \
    <https://go.particular.net/eShopOnContainers>

- **Obsługa komunikatów opartych na zdarzeniach** \
    <https://patterns.arcitura.com/soa-patterns/design_patterns/event_driven_messaging>

- **Jimmy Bogard. Refaktoryzacja do odporności: Ocena sprzęgu** \
    <https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/>

-  \ **kanału publikowania/subskrybowania**
    <https://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html>

- **Komunikacja między kontekstami ograniczonymi** \
    <https://docs.microsoft.com/previous-versions/msp-n-p/jj591572(v=pandp.10)>

-  \ **spójności ostatecznej**
    [https://en.wikipedia.org/wiki/Eventual\_consistency](https://en.wikipedia.org/wiki/Eventual_consistency)

- **Philip brązowy. Strategie integracji ograniczonych kontekstów** \
    <https://www.culttt.com/2014/11/26/strategies-integrating-bounded-contexts/>

- **Krzysztof Richardson. Opracowywanie mikrousług transakcyjnych przy użyciu agregacji, pochodzenia zdarzeń i CQRS części 2** \
    <https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson>

- **Krzysztof Richardson. Wzorzec określania źródła zdarzeń** \
    <https://microservices.io/patterns/data/event-sourcing.html>

- **Wprowadzenie \ źródłem zdarzeń**
    <https://docs.microsoft.com/previous-versions/msp-n-p/jj591559(v=pandp.10)>

- **Baza danych magazynu zdarzeń**. Oficjalna lokacja. \
    <https://geteventstore.com/>

- **Patryk Nommensen. Zarządzanie danymi oparte na zdarzeniach dla mikrousług** \
    <https://dzone.com/articles/event-driven-data-management-for-microservices-1>

-  \ **zakończenia theorem**
    [https://en.wikipedia.org/wiki/CAP\_theorem](https://en.wikipedia.org/wiki/CAP_theorem)

- **Co to jest theorem CAP?** \
    <https://www.quora.com/What-Is-CAP-Theorem-1>

-  \er **spójności danych**
    <https://docs.microsoft.com/previous-versions/msp-n-p/dn589800(v=pandp.10)>

- **Rick Saling. Theorem zakończenia: Dlaczego "wszystko jest różne" z chmurą i Internet** \
    <https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/>

- **Eric Brewer. Od 12 lat później: jak zmieniono "reguły"**  \
    <https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed>

- **Azure Service Bus. Komunikaty obsługiwane przez brokera: Wykrywanie duplikatów**  \
    <https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25>

- **Przewodnik dotyczący niezawodności** (dokumentacja RabbitMQ) \
    [https://www.rabbitmq.com/reliability.html\#consumer](https://www.rabbitmq.com/reliability.html#consumer)

> [!div class="step-by-step"]
> [Poprzedni](rabbitmq-event-bus-development-test-environment.md)
> [Następny](test-aspnet-core-services-web-apps.md)

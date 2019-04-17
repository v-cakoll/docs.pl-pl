---
title: Subskrybowanie zdarzeń
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Poznaj szczegóły publikowanie i subskrybowanie zdarzeń integracji.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/02/2018
ms.openlocfilehash: 962d12c054bed3b2623283e17f83b8466ab2811b
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2019
ms.locfileid: "59613281"
---
# <a name="subscribing-to-events"></a>Subskrybowanie zdarzeń

Pierwszym krokiem przy użyciu magistrali zdarzeń jest subskrybowanie mikrousług dla zdarzeń, które chcą otrzymywać. Który ma się odbywać w mikrousługach odbiorcy.

Poniższy kod proste pokazuje, jakie poszczególne mikrousługi odbiornika należy zaimplementować podczas uruchamiania usługi (to znaczy w `Startup` klasy) tak subskrybuje zdarzenia go wymaga. W tym przypadku `basket.api` mikrousług trzeba subskrybować `ProductPriceChangedIntegrationEvent` i `OrderStartedIntegrationEvent` wiadomości.

Na przykład podczas subskrybowania `ProductPriceChangedIntegrationEvent` zdarzeń, który sprawia, że mikrousług koszyka pamiętać o dowolnej zmiany cena produktu i umożliwia mu ostrzec użytkownika o zmianie, jeśli produktu znajduje się w koszyku użytkownika.

```csharp
var eventBus = app.ApplicationServices.GetRequiredService<IEventBus>();

eventBus.Subscribe<ProductPriceChangedIntegrationEvent,
                   ProductPriceChangedIntegrationEventHandler>();

eventBus.Subscribe<OrderStartedIntegrationEvent,
                   OrderStartedIntegrationEventHandler>();

```

Po uruchomieniu tego kodu, mikrousług subskrybent będzie nasłuchiwania za pośrednictwem kanałów RabbitMQ. Po odebraniu komunikatu dowolnego typu ProductPriceChangedIntegrationEvent kod wywołuje program obsługi zdarzeń, który jest przekazywany do niego i przetwarza zdarzenia.

## <a name="publishing-events-through-the-event-bus"></a>Publikowanie zdarzeń za pomocą magistrali zdarzeń

Na koniec nadawcy wiadomości (mikrousług origin) publikuje zdarzenia integracji z kodem podobny do poniższego przykładu. (Jest to uproszczony przykład, który nie ma niepodzielność pod uwagę). Możesz również zaimplementować podobny kod zawsze wtedy, gdy zdarzenie musi być propagowane przez wiele mikrousług, zwykle zaraz po zatwierdzanie danych bądź transakcji z mikrousług źródła.

Po pierwsze obiekt implementacji magistrali zdarzeń (oparte na RabbitMQ lub oparte na usługi Service bus) zostałyby dodane w Konstruktorze kontrolera, zgodnie z poniższym kodem:

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

Następnie przy użyciu go z poziomu kontrolera metod, takich jak w metodzie UpdateProduct:

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

W tym przypadku mikrousług pochodzenia jest proste mikrousługi CRUD, ten kod jest umieszczana po prawej stronie do kontrolera internetowego interfejsu API.

W bardziej zaawansowanych mikrousług, takich jak przy użyciu podejścia CQRS może być implementowany w `CommandHandler` klasy poziomu `Handle()` metody.

### <a name="designing-atomicity-and-resiliency-when-publishing-to-the-event-bus"></a>Projektowanie niepodzielność i zwiększa odporność podczas publikowania w magistrali zdarzeń

Podczas publikowania zdarzenia integracji za pomocą rozproszonej obsługi wiadomości usługi Service bus zdarzeń, takich jak system, masz problem niepodzielne aktualizowanie oryginalnej bazy danych i publikowanie zdarzenia (czyli zarówno zakończenie operacji lub żadna z nich). Na przykład uproszczony przykład przedstawionej wcześniej kod zapisuje dane w bazie danych po cena produktu jest zmienione, a następnie publikuje komunikat ProductPriceChangedIntegrationEvent. Początkowo może wyglądać istotne, że te dwie operacje być wykonywane atomowo. Jednak jeśli używasz obejmujące transakcji rozproszonej bazy danych i komunikat brokera, tak jak w starszych systemów, takich jak [Microsoft usługi kolejkowania komunikatów (MSMQ)](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx), to nie jest zalecane z powodów opisanych przez [Kolejnego elementu teorii CAP](https://www.quora.com/What-Is-CAP-Theorem-1).

Po prostu umożliwia mikrousług tworzenie systemów skalowalna i wysoko dostępna. Upraszczanie nieco, kolejnego elementu teorii CAP mówi, że nie można utworzyć bazę danych (rozproszone) (lub mikrousług, który jest właścicielem swój model) jest stale dostępna, zdecydowanie spójnych *i* odporne na żadnej partycji. Musisz wybrać dwa z tych trzech właściwości.

W opartych na mikrousługach architektury należy wybrać dostępności i na uszkodzenia i powinien cieszących silnej spójności. W związku z tym, w większości współczesnych aplikacji opartych na mikrousługach, zwykle nie chcesz używać transakcji rozproszonych, w przypadku komunikatów, w jak podczas implementowania [transakcje rozproszone](https://docs.microsoft.com/previous-versions/windows/desktop/ms681205(v=vs.85)) oparte na transakcję rozproszoną Windows Koordynator (transakcji rozproszonych DTC) za pomocą [MSMQ](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx).

Wróćmy do początkowego problemu i jego przykład. Jeśli usługa ulegnie awarii po zaktualizowaniu bazy danych (w tym przypadku kliknij prawym przyciskiem myszy, po wierszu kodu za pomocą \_kontekstu. SaveChangesAsync()), ale przed opublikowaniem zdarzenia integracji całego systemu może stać się niespójna. Może to być krytyczne dla działania, w zależności od operacji biznesowych, który masz do czynienia z.

Jak wspomniano wcześniej, w sekcji architektury, może mieć różne podejścia do radzenia sobie z tym problemem:

- Przy użyciu pełnego [wzorzec określania źródła zdarzeń](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing).

- Za pomocą [wyszukiwania dziennik transakcji](https://www.scoop.it/t/sql-server-transaction-log-mining).

- Za pomocą [wzorzec Skrzynka nadawcza](http://gistlabs.com/2014/05/the-outbox/). To jest tabela transakcji do przechowywania zdarzeń integracji (Rozszerzanie lokalnej transakcji).

W tym scenariuszu przy użyciu pełnej wzorca określania źródła zdarzeń (ES) jest jednym z najlepszych metod, jeśli *nie* najlepsze. Jednak w wielu scenariuszach aplikacji, nie można zaimplementować pełnego ES. ES oznacza przechowywanie tylko domeny zdarzenia w transakcji bazy danych, zamiast przechowywania danych bieżącego stanu. Przechowywanie tylko domeny zdarzenia może mieć wiele korzyści, takich jak o historii dostępności systemu i możliwość określenia stanu systemu w dowolnym momencie w przeszłości. Jednak implementacja pełnego ES wymaga Przekształcanie większość systemu i wprowadza wiele złożoności i wymagania. Na przykład chcesz korzystać z bazy danych, które celowo do określania źródła zdarzeń, takich jak [Store zdarzeń](https://eventstore.org/), lub korzystający z dokumentów bazy danych, takich jak usługi Azure Cosmos DB, bazy danych MongoDB, Cassandra, CouchDB lub RavenDB. ES jest to doskonałe podejście do problemu, ale nie najprostszym rozwiązaniu, chyba że znasz już określania źródła zdarzeń.

Możliwość użycia dziennika transakcji wyszukiwania początkowo wygląda bardzo przejrzysty. Jednak aby użyć tego podejścia, mikrousług ma zostać dołączone do dziennika transakcji RDBMS, takie jak dziennik transakcji programu SQL Server. Prawdopodobnie nie jest to pożądane. Inny wadą jest to, że aktualizacje niskiego poziomu, rejestrowane w dzienniku transakcji może nie być tym samym poziomie, jako zdarzenia wysokiego poziomu integracji. Jeśli tak, proces odtwarzania te operacje dziennika transakcji może być trudne.

Zrównoważone podejście jest kombinacja tabela transakcji bazy danych i uproszczone wzorzec ES. Można użyć stanu, np. "gotowy do publikowania zdarzeń", który ustawia w oryginalnej zdarzenia podczas zatwierdzania integracji w tabeli zdarzeń. Następnie spróbuj opublikować wydarzenie magistrali zdarzeń. Jeśli akcja zdarzenia publikowania zakończy się powodzeniem, uruchom inną transakcję w usłudze pochodzenia i Przenieś stanu z "gotowych do opublikowania zdarzenia" "zdarzenie już opublikowane."

Jeśli akcja zdarzenia publikowania w zdarzeniu magistrali kończy się niepowodzeniem, dane nadal nie będą niespójne w mikrousługach pochodzenia — nadal jest oznaczona jako "gotowy do opublikowania zdarzenie", a w odniesieniu do pozostałych usług po pewnym czasie będzie spójny. Sprawdzanie stanu transakcji lub zdarzenia integracji zadań w tle zawsze może mieć. Jeśli zadanie znajdzie zdarzenia w stanie "gotowe do opublikowania zdarzenie", może użyć ponownie opublikować tego zdarzenia do magistrali zdarzeń.

Należy zauważyć, że w przypadku tej metody, można są przechowywanie tylko zdarzenia integracji dla poszczególnych mikrousług źródła, a tylko zdarzenia, które chcesz komunikować się z innymi mikrousług lub systemy zewnętrzne. Z kolei w pełnym systemie ES, są przechowywane także wszystkie zdarzenia domeny.

W związku z tym ta metoda o zrównoważonym obciążeniu jest uproszczony system ES. Należy uzyskać listę zdarzeń integracji z ich bieżącym stanem ("gotowe do opublikowania" i "opublikowany"). Ale trzeba zaimplementować te stany zdarzenia integracji. A w przypadku tej metody nie trzeba do przechowywania danych domeny jako zdarzenia w bazie danych transakcyjnych, tak jak w pełnym systemie ES.

Jeśli już używasz relacyjnej bazy danych, można użyć transakcji tabeli do przechowywania zdarzeń integracji. Aby osiągnąć niepodzielność w aplikacji, należy użyć dwuetapowego procesu na podstawie lokalnej transakcji. Zasadniczo masz tabelę IntegrationEvent w tej samej bazy danych, których mają jednostki domeny. Ta tabela działa zgodnie z branży ubezpieczeniowej do osiągnięcia niepodzielność, tak że uwzględnisz utrwalone zdarzenia integracji w tej samej transakcji, które są w trakcie zatwierdzania danych domeny.

Krok po kroku proces wykracza następująco:

1. Aplikacja rozpocznie transakcji lokalnej bazy danych.

2. Następnie aktualizuje stan jednostki domeny i wstawia zdarzenia do tabeli zdarzeń integracji.

3. Na koniec jej zatwierdzenia transakcji, dzięki czemu uzyskujesz żądaną niepodzielność i następnie

4. Jakiś sposób opublikować wydarzenie (dalej).

Implementując kroki publikowania zdarzenia, masz następujące opcje:

- Publikowanie zdarzeń integracji od razu po zatwierdzanie transakcji i użyj innego transakcji lokalnej, aby oznaczyć zdarzenia w opublikowanej tabeli. Następnie skorzystaj z tabeli po prostu jako artefaktu do śledzenia zdarzeń integracji, w razie problemów z mikrousług zdalnego i wykonywać akcje kompensacyjne, na podstawie zdarzeń przechowywanych integracji.

- Skorzystaj z tabeli jako rodzaj kolejki. Wątek oddzielną aplikację lub procesu zapytania w tabeli zdarzeń integracji, publikuje w magistrali zdarzeń zdarzenia i następnie używa lokalnej transakcji do oznaczenia zdarzeń jako opublikowane.

Rysunek 6-22 przedstawiono architekturę jako pierwsza z tych metod.

![Jedno z podejść do obsługi niepodzielność podczas publikowania zdarzeń: publikować (używanych w ramach aplikacji eShopOnContainers) za pomocą jednej transakcji do zatwierdzenia zdarzenia do tabeli dziennika zdarzeń, a następnie inną transakcję](./media/image23.png)

**Rysunek 6-22**. Niepodzielność podczas publikowania zdarzeń w magistrali zdarzeń

Podejście pokazano w rysunek 6-22 brakuje mikrousług dodatkowe procesu roboczego, który jest odpowiedzialny za sprawdzenie i Potwierdzanie Powodzenie zdarzenia opublikowanych integracji. W przypadku awarii tego dodatkowe sprawdzanie procesu roboczego mikrousług można odczytywać zdarzenia z tabeli i ponownie opublikować je, czyli liczba Powtórz krok 2.

Temat drugiego podejścia: skorzystaj z tabeli dziennika zdarzeń, co kolejka i zawsze używaj mikrousług procesu roboczego do publikowania wiadomości. W takiej sytuacji proces Krewny, który jest wyświetlany w rysunek 6 – 23. Spowoduje to pokazanie dodatkowe mikrousług, a tabela jest pojedyncze źródło podczas publikowania zdarzeń.

![Innym sposobem obsługi niepodzielność: Publikowanie do tabeli dziennika zdarzeń, a następnie mają inny mikrousługi (procesu roboczego tła) opublikować zdarzenia.](./media/image24.png)

**Rysunek 6-23**. Niepodzielność podczas publikowania zdarzeń w magistrali zdarzeń z mikrousług procesu roboczego

Dla uproszczenia przykładowe w ramach aplikacji eShopOnContainers korzysta z pierwszej metody (bez dodatkowych procesów i z mikrousług sprawdzania) oraz magistrali zdarzeń. Jednak ramach aplikacji eShopOnContainers nie obsługuje wszystkich przypadkach mogą występować awarie. W rzeczywistej aplikacji wdrożonych w chmurze możesz wykorzystać fakt, że będzie problemów po pewnym czasie oraz musi implementować i sprawdź i Wyślij ponownie logiki. Przy użyciu tabeli jako kolejka może być bardziej efektywne niż pierwszego podejścia, jeśli masz tę tabelę jako pojedyncze źródło zdarzenia, gdy w ich opublikowaniem (z proces roboczy), za pośrednictwem magistrali zdarzeń.

### <a name="implementing-atomicity-when-publishing-integration-events-through-the-event-bus"></a>Implementowanie niepodzielność podczas publikowania zdarzeń integracja za pośrednictwem magistrali zdarzeń

Poniższy kod przedstawia sposób tworzenia pojedynczej transakcji obejmujących wiele obiektów typu DbContext — jednym kontekście związane z oryginalnych danych aktualizowana, a drugi kontekst związany z tabeli IntegrationEventLog.

Pamiętaj, że transakcji w poniższym przykładowym kodzie nie będą odporne na błędy, jeśli połączeń z bazą danych wszelkie problemy w czasie, gdy kod jest uruchomiony. Może to nastąpić w chmurze systemów, takich jak bazy danych SQL Azure, które mogą przenosić bazy danych na serwerach. Implementowanie odpornych transakcji w wielu kontekstach, dla [Implementowanie odpornych na błędy połączeń Entity Framework Core SQL](../implement-resilient-applications/implement-resilient-entity-framework-core-sql-connections.md) sekcję w dalszej części tego przewodnika.

W celu uściślenia poniższy przykład pokazuje całego procesu w pojedynczy fragment kodu. Jednak implementacji w ramach aplikacji eShopOnContainers faktycznie zaprojektowane od nowa i podzielić tę logikę na wiele klas, więc jest łatwiejsze w konserwacji.

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

Po utworzeniu zdarzenia integracji ProductPriceChangedIntegrationEvent transakcji, która przechowuje operacji pierwotnej domeny (Aktualizacja elementów katalogu) zawiera również trwałości zdarzenia w tabeli w dzienniku zdarzeń. Dzięki temu pojedynczą transakcję i zawsze można sprawdzić, czy komunikaty o zdarzeniach zostały wysłane.

Tabela dziennika zdarzeń jest aktualizowana niepodzielne operacji pierwotnej bazy danych przy użyciu lokalnej transakcji w tej samej bazie danych. Jeśli dowolne operacje kończą się niepowodzeniem, zostanie zgłoszony wyjątek i transakcji powoduje wycofanie zakończonych operacji, w związku z tym utrzymanie spójności między operacjami domeny i komunikaty o zdarzeniach, zapisane w tabeli.

### <a name="receiving-messages-from-subscriptions-event-handlers-in-receiver-microservices"></a>Odbieranie komunikatów z subskrypcji: obsługi zdarzeń w mikrousługach odbiorcy

Oprócz logiki subskrypcji zdarzeń musisz wdrożyć wewnętrzny kod procedury obsługi zdarzeń integracji (np. metody wywołania zwrotnego). Program obsługi zdarzeń określa się tam gdzie odbierane i przetwarzane komunikaty o zdarzeniach określonego typu.

Program obsługi zdarzeń otrzymuje najpierw wystąpienie zdarzenia z magistrali zdarzeń. Następnie klient zlokalizuje składników, które mają być przetwarzane powiązany z tym zdarzeniem integracji propagowanie i przechowywanie zdarzenia jako zmianę stanu w mikrousługach odbiorcy. Na przykład jeśli zdarzenie ProductPriceChanged pochodzi z mikrousług wykazu, będzie odbywa się w mikrousługach koszyka i zmienia stan w tej mikrousług koszyka odbiornik, jak i, jak pokazano w poniższym kodzie.

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

Program obsługi zdarzeń musi sprawdzić, czy produkt istnieje we wszystkich wystąpieniach koszyka. Aktualizuje cenę dla każdego elementu wiersza powiązane koszyka. Na koniec tworzy alert ma być wyświetlany dla użytkownika o zmianę ceny, jak pokazano w rysunek 6 do 24.

![Widok przeglądarki procesu zmiany powiadomienia na koszyka użytkownika.](./media/image25.png)

**Rysunek 6 – 24**. Wyświetlanie zmian cen elementów w koszyku jako przekazywane przez zdarzenia integracji

## <a name="idempotency-in-update-message-events"></a>Idempotentność w aktualizacji komunikat zdarzenia

Ważnym aspektem zdarzeń komunikatów aktualizacji jest, czy Niepowodzenie w dowolnym momencie w komunikacie powinno spowodować komunikat, który ma zostać ponowiona. W przeciwnym razie zadanie w tle może próbować publikowania zdarzenia, które zostało już opublikowane, tworząc warunki sytuacji wyścigu. Możesz należy się upewnić, że aktualizacje są idempotentne lub że zapewniają one wystarczającej ilości informacji, aby upewnić się, że można wykryć duplikat, odrzucić je i Wyślij ponownie tylko jedną odpowiedź.

Jak wspomniano wcześniej, idempotentność oznacza, że operacja może zostać wykonana wiele razy bez wprowadzania zmian w wyniku. W środowisku obsługi komunikatów ponieważ podczas komunikowania się zdarzenia, zdarzenie jest idempotentna, jeśli móc go dostarczyć wiele razy bez wprowadzania zmian w wyniku dla mikrousług odbiorcy. Może to być konieczne ze względu na charakter samego zdarzenia lub ze względu na sposób system obsługuje zdarzenie. Komunikat idempotentność jest ważne, w dowolnej aplikacji, która używa obsługi komunikatów, a nie tylko w aplikacji, które implementują wzorzec magistrali zdarzeń.

Przykładem operacja idempotentna jest instrukcję SQL, który wstawia dane do tabeli, tylko wtedy, gdy dane nie są już w tabeli. Nie ma znaczenia, ile razy należy uruchomić, które wstawiają instrukcję SQL wynik będzie taki sam — tabela będzie zawierać tych danych. Idempotentności, np. to może być również niezbędne podczas pracy z komunikatów, jeśli potencjalnie być wysyłane komunikaty i w związku z tym przetworzonych więcej niż raz. Na przykład jeśli Logika ponawiania powoduje, że nadawca wysyłać ten sam komunikat więcej niż jeden raz, należy się upewnić, że jest idempotentna.

Istnieje możliwość projektowania idempotentne wiadomości. Na przykład można utworzyć zdarzenie i mówi "Ustaw cena produktu do 25 USD" zamiast "Dodaj 5 USD cena produktu" Użytkownik może bezpiecznie przetworzyć pierwszy komunikat o dowolną liczbę razy, a wynik będzie taki sam. To nie dotyczy drugi komunikat. Ale nawet w przypadku pierwszego, nie można przetworzyć pierwsze zdarzenie, ponieważ system może również wysłane nowszych zdarzeń zmian cen i spowoduje zastąpienie nową cenę.

Innym przykładem mogą być zdarzenie ukończone w kolejności propagowana do wielu subskrybentów. Ważne jest, informacji o zamówieniach zaktualizowania w innych systemach tylko raz, nawet jeśli występują zduplikowany komunikat zdarzenia dla tego samego zdarzenia ukończone w kolejności.

Jest wygodną zapewnienie pewnego rodzaju tożsamości na zdarzenie, w którym można utworzyć logikę, która wymusza na to, że każde zdarzenie jest przetwarzany tylko raz na odbiorcy.

Przetwarza komunikat jest idempotentna. Na przykład jeśli system generuje obraz miniatury, może nie ważne jest, ile razy komunikat dotyczący miniatury wygenerowanej jest przetwarzany; wynik jest miniatury są generowane i każdym razem, gdy są takie same. Z drugiej strony operacje, takie jak wywołanie bramy płatności do obciążenia karty kredytowej może nie być idempotentne wcale. W takich przypadkach musisz upewnić się, że przetwarzania wiadomości wielokrotnie efekt, których oczekujesz.

### <a name="additional-resources"></a>Dodatkowe zasoby

- **Zapewniane idempotentności wiadomości** <br/>
    <https://docs.microsoft.com/previous-versions/msp-n-p/jj591565(v=pandp.10)#honoring-message-idempotency>

## <a name="deduplicating-integration-event-messages"></a>Deduplikacja integracji komunikaty o zdarzeniach

Można należy upewnić się, że zdarzenia dotyczące wiadomości wysyłanych i przetwarzany tylko raz na subskrybenta na różnych poziomach. Jednym ze sposobów jest korzystać z funkcji deduplikacji, oferowane przez infrastruktura obsługi komunikatów, którego używasz. Innym jest zaimplementowanie logiki niestandardowej w mikrousługach swoje miejsce docelowe. Sprawdzanie poprawności na poziomie transportu i na poziomie aplikacji jest najlepsze rozwiązanie.

### <a name="deduplicating-message-events-at-the-eventhandler-level"></a>Komunikat zdarzenia na poziomie EventHandler deduplikacja

Jednym ze sposobów, aby upewnić się, że zdarzenie jest przetwarzany tylko raz przez żadnego odbiorcy jest zaimplementowanie logiki określonych podczas przetwarzania zdarzeń komunikatów w procedurze obsługi zdarzeń. Na przykład, to podejście użyte w ramach aplikacji eShopOnContainers aplikacji, jak widać w [źródła kod klasy UserCheckoutAcceptedIntegrationEventHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) po odebraniu UserCheckoutAcceptedIntegrationEvent Zdarzenie integracji. (W tym przypadku możemy opakować CreateOrderCommand z IdentifiedCommand przy użyciu eventMsg.RequestId jako identyfikator przed wysłaniem ich do obsługi polecenia).

### <a name="deduplicating-messages-when-using-rabbitmq"></a>Deduplikacja wiadomości w przypadku korzystania z oprogramowania RabbitMQ

Gdy wystąpi sporadyczne awarie sieci, mogą być zduplikowane komunikaty, a odbiorcy wiadomości musi być gotowy do obsługi tych zduplikowane komunikaty. Jeśli to możliwe odbiorniki powinna obsługiwać komunikaty w sposób idempotentne, który jest lepsze niż jawną obsługę je z włączoną funkcją deduplikacji.

Zgodnie z opisem w [dokumentacji oprogramowania RabbitMQ](https://www.rabbitmq.com/reliability.html#consumer), "Jeśli komunikat jest dostarczany do odbiorców, a następnie ponownie umieszczone w kolejce (ponieważ nie zostało potwierdzone, zanim konsumenta połączenie zostało przerwane, na przykład), a następnie RabbitMQ ustawi flagi redelivered na go po dostarczeniu ponownie (czy do tego samego użytkownika lub inną).

Jeśli flaga "redelivered" jest ustawiona, odbiorca musi uwzględniać który, ponieważ komunikat może być już zostały przetworzone. Ale nie jest gwarantowana; komunikat, być może nigdy nie osiągnięto odbiornika od jego brokera komunikatów, prawdopodobnie z powodu problemów z siecią. Z drugiej strony Jeśli nie ustawiono flagi "redelivered", ma żadnej gwarancji, że wiadomość nie została wysłana więcej niż jeden raz. W związku z tym odbiorca musi deduplikacja wiadomości lub przetwarzania komunikatów w sposób idempotentne, tylko wtedy, gdy flaga "redelivered" jest ustawiona w komunikacie.

### <a name="additional-resources"></a>Dodatkowe zasoby

- **Rozwidlone w ramach aplikacji eShopOnContainers przy użyciu NServiceBus (konkretnego oprogramowania)** \
    <https://go.particular.net/eShopOnContainers>

- **Aktivita typu EventDriven komunikatów** \
    [http://soapatterns.org/design\_patterns/event\_driven\_messaging](http://soapatterns.org/design_patterns/event_driven_messaging)

- **Jimmy Bogard. Refaktoryzacja kierunku odporności na błędy: Ocena sprzężenia** \
    <https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/>

- **Publikowanie/subskrybowanie kanałów** \
    <https://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html>

- **Komunikacja między ograniczone konteksty** \
    <https://docs.microsoft.com/previous-versions/msp-n-p/jj591572(v=pandp.10)>

- **Spójność ostateczna** \
    [https://en.wikipedia.org/wiki/Eventual\_consistency](https://en.wikipedia.org/wiki/Eventual_consistency)

- **Philip Brown. Integrowanie strategii ograniczone konteksty** \
    <https://www.culttt.com/2014/11/26/strategies-integrating-bounded-contexts/>

- **Chris Richardson. Tworzenie Mikrousług transakcyjne przy użyciu wartości zagregowane, określania źródła zdarzeń i podejście CQRS — część 2** \
    <https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson>

- **Chris Richardson. Wzorzec określania źródła zdarzeń** \
    <https://microservices.io/patterns/data/event-sourcing.html>

- **Wprowadzenie do określania źródła zdarzeń** \
    <https://docs.microsoft.com/previous-versions/msp-n-p/jj591559(v=pandp.10)>

- **Bazy danych zdarzeń Store**. Oficjalna witryna. \
    <https://geteventstore.com/>

- **Patrick Nommensen. Zarządzanie oparte na zdarzeniach danych dla Mikrousług** \
    <https://dzone.com/articles/event-driven-data-management-for-microservices-1>

- **Kolejnego elementu teorii CAP** \
    [https://en.wikipedia.org/wiki/CAP\_theorem](https://en.wikipedia.org/wiki/CAP_theorem)

- **Co to jest kolejnego elementu teorii CAP?** \
    <https://www.quora.com/What-Is-CAP-Theorem-1>

- **Podstawy spójności danych** \
    <https://docs.microsoft.com/previous-versions/msp-n-p/dn589800(v=pandp.10)>

- **Rick Saling. Kolejnego elementu teorii CAP: Dlaczego "wszystko, co jest różne" chmura i Internet** \
    <https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/>

- **Eric Brewera. LIMIT dwunastu latach później: Jak "Zasady" zostały zmienione** \
    <https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed>

- **Azure Service Bus. Komunikaty obsługiwane przez brokera: Wykrywanie duplikatów**  \
    <https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25>

- **Przewodnik niezawodność** (dokumentacja RabbitMQ) \
    [https://www.rabbitmq.com/reliability.html\#consumer](https://www.rabbitmq.com/reliability.html#consumer)

- **Azure Service Bus. Komunikaty obsługiwane przez brokera: Wykrywanie duplikatów** \
    <https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25>

- **Przewodnik niezawodność** (dokumentacja RabbitMQ) \
    [https://www.rabbitmq.com/reliability.html\#consumer](https://www.rabbitmq.com/reliability.html%23consumer)

> [!div class="step-by-step"]
> [Poprzednie](rabbitmq-event-bus-development-test-environment.md)
> [dalej](test-aspnet-core-services-web-apps.md)

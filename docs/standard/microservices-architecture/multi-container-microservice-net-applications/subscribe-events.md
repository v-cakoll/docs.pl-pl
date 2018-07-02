---
title: Subskrybowanie zdarzeń
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Subskrybowanie zdarzeń
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: 6cc5563f93915d1516e5a5f22a104012c1bb85d6
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106580"
---
# <a name="subscribing-to-events"></a>Subskrybowanie zdarzeń

Pierwszym krokiem przy użyciu magistrali zdarzeń jest jej zasubskrybowanie mikrousług do zdarzeń, które mają być wyświetlony. Który ma się odbywać w mikrousług odbiornika.

Poniższy kod proste pokazuje, co każdy odbiorca mikrousługi należy zaimplementować podczas uruchamiania usługi (to znaczy w `Startup` klasy) tak subskrybuje zdarzenia go wymaga. W takim przypadku `basket.api` mikrousługi należy zasubskrybować `ProductPriceChangedIntegrationEvent` i `OrderStartedIntegrationEvent` wiadomości. 

Na przykład podczas subskrybowania `ProductPriceChangedIntegrationEvent` zdarzeń, dzięki mikrousługi koszyka pamiętać o dowolnej zmiany ceny produktu i umożliwia mu Ostrzegaj użytkownika o zmianie w przypadku tego produktu jest w koszyku użytkownika.

```csharp
var eventBus = app.ApplicationServices.GetRequiredService<IEventBus>();

eventBus.Subscribe<ProductPriceChangedIntegrationEvent, 
                   ProductPriceChangedIntegrationEventHandler>();

eventBus.Subscribe<OrderStartedIntegrationEvent, 
                   OrderStartedIntegrationEventHandler>();

```

Po uruchomieniu tego kodu mikrousługi subskrybent będzie nasłuchiwać kanałami RabbitMQ. Po odebraniu żadnych wiadomości typu ProductPriceChangedIntegrationEvent, kod wywołuje program obsługi zdarzeń, która została przekazana do niej i przetwarza zdarzenia.

## <a name="publishing-events-through-the-event-bus"></a>Publikowanie za pośrednictwem magistrali zdarzeń zdarzenia

Na koniec nadawcy wiadomości (pochodzenia mikrousługi) publikuje zdarzeń integracji z kodem podobny do poniższego przykładu. (Jest to przykład uproszczony, które nie wymaga niepodzielność pod uwagę). Czy zaimplementowaniem podobny kod zawsze, gdy zdarzenie musi propagowane na wiele mikrousług, zazwyczaj prawo po zatwierdzania danych bądź transakcji z mikrousługi pochodzenia.

Po pierwsze obiekt implementacji magistrali zdarzenia (oparte na RabbitMQ lub oparte na usługi service bus) zostałyby dodane w Konstruktorze kontrolera, zgodnie z poniższym kodem:

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

Następnie używania jej metody dany kontroler, podobnie jak w metodę UpdateProduct:

```csharp
[Route("update")]
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

W takim przypadku mikrousługi źródła jest proste mikrousługi CRUD, ten kod jest umieszczany po prawej w kontrolera interfejsu API sieci Web. 
 
W mikrousług bardziej zaawansowanych, takich jak przy użyciu podejścia CQRS, może być wdrożonych w `CommandHandler` klasy poziomu `Handle()` metody. 


### <a name="designing-atomicity-and-resiliency-when-publishing-to-the-event-bus"></a>Projektowanie niepodzielność i odporność podczas publikowania magistrali zdarzeń

Podczas publikowania zdarzeń integracji przy użyciu rozproszonego wiadomości z magistrali zdarzeń, takich jak system, masz problem automatycznie aktualizuje oryginalnej bazy danych i publikowania zdarzenia. Na przykład w uproszczonym przykładzie pokazano wcześniej, kod zapisuje dane do bazy danych po cena produktu zostanie zmieniona, a następnie publikuje komunikat ProductPriceChangedIntegrationEvent. Początkowo może wyglądać niezbędne atomowo wykonanie tych dwóch operacji. Jednak jeśli używasz transakcji rozproszonej obejmujące bazę danych i wiadomości broker, tak jak w starszych systemach, takich jak [usługi kolejkowania wiadomości firmy Microsoft (MSMQ)](https://msdn.microsoft.com/library/ms711472(v=vs.85).aspx), to nie jest zalecane z powodów opisanych przez [Newtona zakończenia](https://www.quora.com/What-Is-CAP-Theorem-1).

Zasadniczo mikrousług służy do tworzenia systemów skalowalności i wysokiej dostępności. Upraszczanie nieco, Newtona zakończenia informujący, że nie można utworzyć bazy danych (lub mikrousługi, który jest właścicielem jego model) jest stale dostępny, silnie spójne *i* odporne na partycji. Musisz wybrać dwa z tych trzech właściwości.

W podstawie mikrousług architektury należy wybrać dostępność i odporność na awarie, a powinien cieszących wysoki poziom spójności. W związku z tym w większość nowoczesnych aplikacji opartych na mikrousługi, zwykle nie chcesz używać transakcji rozproszonych w wiadomości, podobnie jak w przypadku implementowania [transakcje rozproszone](https://msdn.microsoft.com/library/ms978430.aspx#bdadotnetasync2_topic3c) oparte na transakcji rozproszonych systemu Windows Koordynator (transakcji rozproszonych DTC) z [MSMQ](https://msdn.microsoft.com/library/ms711472(v=vs.85).aspx).

Przejdźmy do początkowej problemu i jego przykład. Jeśli usługa ulegnie awarii po zaktualizowaniu bazy danych (w tym przypadku od razu po wierszu kodu za pomocą \_kontekstu. SaveChangesAsync()), ale przed opublikowaniem zdarzeń integracji całego systemu może stać się niespójna. Może to być biznesowe krytyczne, w zależności od operacji firmy, który mamy do czynienia z.

Jak wspomniano wcześniej, w sekcji architektury, może mieć kilka metod dotyczące tego problemu:

-   Przy użyciu pełnego [źródłem zdarzeń wzorzec](https://msdn.microsoft.com/library/dn589792.aspx).

-   Przy użyciu [wyszukiwania dziennik transakcji](https://www.scoop.it/t/sql-server-transaction-log-mining).

-   Przy użyciu [wzorzec Skrzynka nadawcza](http://gistlabs.com/2014/05/the-outbox/). Jest to transakcyjne tabelę do przechowywania zdarzeń integracji (Rozszerzanie transakcji lokalnej).

W tym scenariuszu przy użyciu pełnego wzorca Sourcing zdarzenia (ES) jest jednym z najlepszych metod, jeśli nie *najlepsze*. Jednak w wielu scenariuszach aplikacji, nie można przeprowadzić pełną wersją systemu ES. ES oznacza przechowywanie tylko zdarzenia domeny transakcyjne bazy danych, zamiast zapisywania danych stanu bieżącego. Przechowywanie tylko zdarzenia domeny mogą mieć dużą korzyści, takich jak o historii dostępne systemu oraz możliwość określenia stanu systemu w dowolnym momencie w przeszłości. Jednak implementacja pełną wersją systemu ES wymaga rearchitect większość systemu i wprowadzono wiele skomplikowane i wymagań. Na przykład, czy chcesz użyć bazy danych celowo dla źródeł zdarzeń, takich jak [magazynu zdarzeń](https://geteventstore.com/), lub z bazą zorientowane na dokument, takie jak bazy danych Azure rozwiązania Cosmos, bazy danych MongoDB, Cassandra, CouchDB lub RavenDB. ES jest doskonałe rozwiązanie ten problem, ale nie najlepszym rozwiązaniem, jeśli nie znasz już źródłem zdarzeń.

Możliwość użycia dziennika transakcji wyszukiwania początkowo wygląda bardzo przezroczysty. Jednak aby użyć tej metody, mikrousługi ma zostać dołączone do RDBMS dziennika transakcji, takie jak dziennik transakcji programu SQL Server. Prawdopodobnie nie jest to pożądane. Inny wadą jest to, że na tym samym poziomie jako zdarzeń integracji wysokiego poziomu nie mogą być aktualizacje niskiego poziomu, rejestrowane w dzienniku transakcji. Jeśli tak, proces odtwarzania te operacje tworzenia dzienników transakcji może być trudne.

Zrównoważone podejście zależy od różnych czynników tabeli transakcyjne bazy danych oraz uproszczone wzorzec ES. Można użyć stanu, takie jak "gotowe do publikowania zdarzeń,", który ustawia w oryginalnej zdarzeń po zatwierdzeniu w tabeli zdarzeń integracji. A następnie spróbuj opublikować wydarzenie magistrali zdarzeń. Jeśli akcja publikowania zdarzeń zakończy się powodzeniem, uruchomienie innej transakcji w usługi pochodzenia i przenieść stanu z "gotowe do opublikowania zdarzenia" do "zdarzenie już opublikowane."

Jeśli akcja publikowania zdarzeń w zdarzeniu magistrali kończy się niepowodzeniem, dane nadal nie będzie niespójne w ramach mikrousługi pochodzenia — nadal jest oznaczony jako "gotowy do publikowania zdarzenia", a w odniesieniu do pozostałych usług, po pewnym czasie będzie spójna. Użytkownik zawsze ma sprawdzanie stanu transakcji lub zdarzeń integracji zadań w tle. Jeśli zadanie znajdzie zdarzenia w stanie "gotowe do publikowania zdarzenia", może użyć ponownie opublikować tego zdarzenia do magistrali zdarzeń.

Zwróć uwagę, że z tej metody można są utrwalanie integracji zdarzenia każdego mikrousługi pochodzenia i tylko zdarzenia, które chcesz komunikować się z innymi mikrousług lub systemami zewnętrznymi. Z kolei w pełnym systemie ES, są przechowywane wszystkie zdarzenia także domeny.

W związku z tym takie podejście zrównoważonym to uproszczony system ES. Należy listę zdarzeń integracji z ich bieżącego stanu ("gotowe do opublikowania" i "opublikowane"). Jednak należy implementować te stany zdarzeń integracji. I w takie podejście, nie trzeba przechowywać wszystkie dane domeny jako zdarzeń w bazie danych transakcyjnych, tak jak w pełnym systemie ES.

Jeśli korzystasz już z relacyjnej bazy danych, można użyć transakcyjne tabelę do przechowywania zdarzeń integracji. Aby osiągnąć niepodzielność w aplikacji, należy użyć dwuetapowego procesu, na podstawie transakcji lokalnej. Zasadniczo ma tabeli IntegrationEvent w tej samej bazy danych, gdzie masz obiekty domeny. Ta tabela będzie działać zgodnie z ubezpieczenia służące osiągnięciu niepodzielność tak, aby w przypadku uwzględnienia trwale zdarzeń integracji w tej samej transakcji, które są w trakcie zatwierdzania danych domeny.

Krok po kroku proces przechodzi następująco: aplikacja zaczyna transakcji lokalnej bazy danych. Następnie aktualizuje stan jednostki domeny i wstawia zdarzenia do tabeli zdarzeń integracji. Na koniec go zatwierdza transakcji. Należy pobrać odpowiednią niepodzielność.

Podczas implementowania kroki publikowania zdarzenia, jest są dostępne poniższe opcje:

-   Publikowanie zdarzeń integracji bezpośrednio po zatwierdzania transakcji i użyj innego transakcji lokalnej, aby oznaczyć zdarzeń w tabeli jako opublikowane. Następnie skorzystaj z tabeli, podobnie jak artefaktów do śledzenia zdarzeń integracji w przypadku problemów dotyczących zdalnego mikrousług i akcje wyrównawczych na podstawie zdarzeń przechowywanych integracji.

-   Skorzystaj z tabeli jako typu kolejki. Aplikacji oddzielnym wątku lub procesu zapytania w tabeli zdarzeń integracji, publikuje zdarzenia do zdarzenia magistrali, a następnie używa transakcji lokalnej do oznaczenia zdarzeń jako opublikowane.

Rysunek 8 do 22 przedstawiono architekturę, w pierwszym z tych metod.

![](./media/image23.png)

**Rysunek 8 do 22**. Niepodzielność podczas publikowania zdarzeń w magistrali zdarzeń

Podejście zilustrowane w rysunek 8 do 22 brakuje mikrousługi dodatkowe pracownika, który jest odpowiedzialny za sprawdzenie i potwierdzenie Powodzenie zdarzeń opublikowanej integracji. W razie awarii tego dodatkowe sprawdzanie mikrousługi proces roboczy może odczytywać zdarzenia z tabeli i opublikuj je ponownie.

O drugiej metody: Tabela dziennika zdarzeń służy jako kolejki i zawsze używaj mikrousługi procesu roboczego do publikowania komunikatów. W takim przypadku proces tak jak pokazano w rysunek 8-23. Pokazuje dodatkowe mikrousługi, a tabela jest jedynym źródłem podczas publikowania zdarzenia.

![](./media/image24.png)

**Rysunek 8-23**. Niepodzielność podczas publikowania zdarzeń w magistrali zdarzeń z mikrousługi procesu roboczego

Dla uproszczenia próbki eShopOnContainers używa pierwszego podejścia (z nie dodatkowe procesy lub sprawdzania mikrousług) oraz magistrali zdarzeń. Jednak eShopOnContainers nie obsługuje wszystkich przypadkach możliwe niepowodzenie. W rzeczywistej aplikacji wdrożonych w chmurze musi obejmować fakt może spowodować problemy, którą musi implementować Sprawdź i Wyślij ponownie logiki. Przy użyciu tabeli jako kolejka może być bardziej efektywne niż pierwszego podejścia, jeśli masz tabeli jako pojedyncze źródło zdarzeń podczas publikowania ich za pośrednictwem magistrali zdarzeń.

### <a name="implementing-atomicity-when-publishing-integration-events-through-the-event-bus"></a>Implementowanie niepodzielność podczas publikowania zdarzenia integracja za pośrednictwem magistrali zdarzeń

Poniższy kod przedstawia sposób tworzenia pojedynczej transakcji obejmującego wiele obiektów DbContext — jeden kontekst związany z danymi aktualizowana, a drugi kontekst związany z tabeli IntegrationEventLog.

Należy pamiętać, że transakcji w poniższym przykładowym kodzie nie będą odporne, jeśli połączenia z bazą danych mają jakikolwiek problem w czasie, gdy kod jest uruchomiony. Może to nastąpić w systemach opartych na chmurze, takich jak bazy danych SQL Azure, która może przenoszenia baz danych na serwerach. Wykonania transakcji odporne na wielu kontekstów, zobacz [implementacja odporność połączeń Entity Framework Core SQL](#implementing_resilient_EFCore_SQL_conns) dalszej części tego przewodnika.

Dla uzyskania przejrzystości poniższy przykład przedstawia całego procesu w jednej części kodu. Jednak implementacja eShopOnContainers faktycznie został zrefaktoryzowany i podzielony na wiele klas tę logikę, dlatego jest łatwiejsze w obsłudze.

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
  if !(raiseProductPriceChangedEvent) 
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

      // Publish the intergation event through the event bus
      _eventBus.Publish(priceChangedEvent); 

      integrationEventLogService.MarkEventAsPublishedAsync(
                                                priceChangedEvent); 
  }

  return Ok();
}

```

Po utworzeniu zdarzenia integracji ProductPriceChangedIntegrationEvent transakcji, która przechowuje operację domeny (Aktualizacja elementów katalogu) zawiera również trwałości zdarzenia w dzienniku zdarzeń tabeli. Dzięki temu pojedynczej transakcji i zawsze będzie mógł sprawdzić, czy komunikaty o zdarzeniach zostały wysłane.

Tabela dziennika zdarzeń jest aktualizowana automatycznie oryginalnej operacji bazy danych, przy użyciu transakcji lokalnej w tej samej bazie danych. W przypadku każdej operacji awarii, jest zgłaszany wyjątek i transakcji wycofuje wszystkie ukończoną operację, co umożliwia zachowanie spójności między operacjami domeny i wysyłane komunikaty o zdarzeniach.

### <a name="receiving-messages-from-subscriptions-event-handlers-in-receiver-microservices"></a>Odbieranie komunikatów z subskrypcji: obsługi zdarzeń w mikrousług odbiornika

Oprócz zdarzenia logiki subskrypcji musisz wdrożyć wewnętrzny kod obsługi zdarzeń integracji (np. Metoda wywołania zwrotnego). Program obsługi zdarzeń określa się tam gdzie odbierane i przetwarzane komunikaty o zdarzeniach określonego typu.

Program obsługi zdarzeń otrzymuje najpierw wystąpienia zdarzenia z magistrali zdarzeń. Następnie klient zlokalizuje składnik do przetworzenia powiązany z tym zdarzeniem integracji propagowanie i przechowywanie zdarzenia jako zmianę stanu w mikrousługi odbiornika. Na przykład, jeśli zdarzenie ProductPriceChanged pochodzi mikrousługi katalogu, jego jest obsługiwany w mikrousługi koszyka i zmienia stan w tym jak również odbiornik koszyka mikrousługi, jak pokazano w poniższym kodzie.

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

Program obsługi zdarzeń musi sprawdzić, czy produkt istnieje w żadnym wystąpieniu koszyka. Aktualizuje również cenę dla każdej pozycji powiązanych koszyka. Na koniec tworzy alert ma być wyświetlony dla użytkownika o zmianie cen, jak pokazano w rysunek 8 – 24.

![](./media/image25.png)

**Rysunek 8 – 24**. Wyświetlanie zmiany ceny elementu w koszyka, ponieważ przekazywane przez zdarzeń integracji

## <a name="idempotency-in-update-message-events"></a>Idempotency w zdarzeniach komunikat aktualizacji

Ważnym aspektem zdarzenia komunikat aktualizacji jest czy Niepowodzenie w dowolnym momencie w komunikacie powinno powodować komunikat ponowienie próby. W przeciwnym razie zadanie w tle może podjąć próbę publikowania zdarzeń, który został już opublikowany, tworzenie wyścigu. Możesz należy się upewnić, że aktualizacje są idempotentności lub że zapewniają wystarczających informacji, aby upewnić się, że można wykryć duplikat, odrzucić go i wysłać odpowiedź wstecz tylko jeden.

Jak wspomniano wcześniej, idempotency oznacza, że operację można wykonać wiele razy bez zmieniania wynik. W środowisku obsługi komunikatów jak podczas komunikowania się zdarzenia, zdarzenie jest idempotentności, jeśli jego mogą być dostarczane wiele razy bez zmieniania wynik dla mikrousługi odbiornika. Przyczyną może być konieczne rodzaj samym zdarzeniu lub ze względu na sposób system obsługuje zdarzenie. Komunikat idempotency ważne jest, w dowolnej aplikacji, która używa wiadomości, nie tylko w aplikacjach, które implementują wzorzec magistrali zdarzeń.

Przykład operacji idempotentności to instrukcji SQL, która wstawia dane do tabeli, tylko wtedy, gdy dane nie jest już w tabeli. Nie ma znaczenia, ile razy można uruchomić, które wstawiają instrukcji SQL; wynik będzie taka sama — tabela będzie zawierać dane. Idempotency takie mogą być również konieczne podczas pracy nad komunikaty, jeśli potencjalnie być wysyłane komunikaty, w związku z tym przetworzonych więcej niż raz. Na przykład jeśli Logika ponawiania powoduje, że nadawca wysłać tę samą wiadomość do więcej niż raz, musisz upewnij się, że jest idempotentności.

Istnieje możliwość do projektowania idempotentności wiadomości. Na przykład można utworzyć zdarzenia informacją "ustawioną cena produktu \$25" zamiast "Dodaj \$5 ceny produktu." Można bezpiecznie przetwarzane pierwszą wiadomością dowolną liczbę razy i wyniki będą takie same. To nie jest to drugi komunikat wartość true. Ale nawet w pierwszym przypadku nie można przetworzyć pierwsze zdarzenie, ponieważ system również mogły wysłać nowszej zdarzenia zmiany ceny i spowoduje zastąpienie nowej ceny.

Innym przykładem mogą być zakończone kolejność zdarzeń rozpropagowana na wielu subskrybentów. Jest ważne, że kolejność można zaktualizować informacji w innych systemach tylko raz, nawet w przypadku zduplikowanych komunikatów zdarzeń dla tego samego zdarzenia zakończone kolejności.

Jest wygodną mają określonego rodzaju tożsamości na zdarzenie, aby tworzyć logikę, która wymusza, że każde zdarzenie jest przetwarzany tylko raz na odbiorcy.

Przetwarza komunikat jest z założenia idempotentności. Na przykład jeśli system generuje obraz miniatury, jego może niezależnie od tego, ile razy komunikat o wygenerowanym miniatur jest przetwarzany; wynik jest generowane są miniatury oraz zawsze były takie same. Z drugiej strony operacji, takich jak wywoływanie bramy płatności do obciążenia karty kredytowej nie może być idempotentności w ogóle. W takich sytuacjach należy się upewnić, że przetwarza komunikat wielokrotnie ma wpływ, jaki oczekujesz.

### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Ramach idempotency komunikat** (Podnagłówek na tej stronie) [*https://msdn.microsoft.com/library/jj591565.aspx*](https://msdn.microsoft.com/library/jj591565.aspx)

## <a name="deduplicating-integration-event-messages"></a>Ani deduplikacja komunikaty o zdarzeniach integracji

Można upewnij się, że komunikat zdarzenia są wysyłane i przetwarzany tylko raz na subskrybenta na różnych poziomach. Jednym ze sposobów jest funkcja deduplikacji oferowane przez infrastruktury obsługi wiadomości, którego używasz. Inny jest zaimplementowanie niestandardowej logiki w sieci docelowej mikrousługi. Sprawdzanie poprawności zarówno na poziomie transportu, jak i na poziomie aplikacji jest najlepsze rozwiązanie.

### <a name="deduplicating-message-events-at-the-eventhandler-level"></a>Ani deduplikacja komunikat zdarzenia na poziomie EventHandler

Jednym ze sposobów upewnij się, że zdarzenie jest przetwarzany tylko raz przez dowolnego odbiornika jest zaimplementowanie niektórych logiki podczas przetwarzania zdarzenia wiadomości w obsłudze zdarzeń. Na przykład jest używany w aplikacji eShopOnContainers podejście jak widać w [kod źródłowy](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Controllers/OrdersController.cs) klasy OrdersController, gdy odbierze polecenie CreateOrderCommand. (W takim przypadku stosujemy polecenia żądania HTTP, nie na podstawie komunikatu polecenia, ale logiki należy idempotentności poleceń oparta na komunikat jest podobny).

### <a name="deduplicating-messages-when-using-rabbitmq"></a>Ani deduplikacja wiadomości, korzystając z RabbitMQ

Gdy wystąpi sporadyczne awarie sieci, mogą być zduplikowane wiadomości, a odbiorca wiadomości musi być gotowy do obsługi tych zduplikowanych komunikatów. Jeśli to możliwe odbiorcy powinna obsługiwać wiadomości w sposób idempotentności jest lepszym rozwiązaniem niż jawnie z włączoną funkcją deduplikacji ich obsługę.

Zgodnie z [dokumentacji RabbitMQ](https://www.rabbitmq.com/reliability.html#consumer), "Jeśli wiadomości jest dostarczany do odbiorców, a następnie umieszczony w kolejce (ponieważ nie zostało potwierdzone, aby porzucić połączenia klienta, na przykład), a następnie RabbitMQ ustawi flagi redelivered na go po dostarczeniu ponownie (czy do tego samego użytkownika lub innego).

Jeśli jest ustawiona flaga "redelivered", odbiorca musi uwzględniać który, ponieważ komunikat może już zostały przetworzone. Ale nie jest gwarantowana; komunikat, może nigdy nie osiągnięto odbiornika po pozostawiany brokera komunikatów z być może z powodu problemów dotyczących sieci. Z drugiej strony Jeśli nie jest ustawiona flaga "redelivered", będzie gwarancji, że wiadomość nie została wysłana więcej niż raz. W związku z tym odbiornika musi być deduplikowane wiadomości lub przetwarzania komunikatów w sposób idempotentności tylko wtedy, gdy flaga "redelivered" jest ustawiona w komunikacie.

### <a name="additional-resources"></a>Dodatkowe zasoby

-   **Rozwidlonych eShopOnContainers przy użyciu NServiceBus (konkretnego oprogramowania)**
    [*http://go.particular.net/eShopOnContainers*](http://go.particular.net/eShopOnContainers)

-   **Sterowane zdarzeniami obsługi wiadomości**
    [*http://soapatterns.org/design\_patterns/event\_driven\_messaging*](http://soapatterns.org/design_patterns/event_driven_messaging)

-   **Jimmy Bogard. Refaktoryzacja kierunku odporności: Ocena sprzężenia**
    [*https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/*](https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/)

-   **Kanał publikowania / subskrypcji**
    [*http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html*](http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html)

-   **Komunikacja między kontekstami ograniczonego**
    [*https://msdn.microsoft.com/library/jj591572.aspx*](https://msdn.microsoft.com/library/jj591572.aspx)

-   **Spójność ostateczna**
    [*https://en.wikipedia.org/wiki/Eventual\_consistency*](https://en.wikipedia.org/wiki/Eventual_consistency)

-   **Brązowy Philip. Konteksty ograniczone strategii integracji**
    [*http://culttt.com/2014/11/26/strategies-integrating-bounded-contexts/*](http://culttt.com/2014/11/26/strategies-integrating-bounded-contexts/)

-   **Krzysztof Richardson. Tworzenie Mikrousług transakcyjne przy użyciu wartości zagregowanych, źródłem zdarzeń i CQRS — część 2**
    [*https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson*](https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson)

-   **Krzysztof Richardson. Wzorzec wysyłanie zawartości zdarzeń**
    [*https://microservices.io/patterns/data/event-sourcing.html*](https://microservices.io/patterns/data/event-sourcing.html)

-   **Wprowadzenie źródłem zdarzenia**
    [*https://msdn.microsoft.com/library/jj591559.aspx*](https://msdn.microsoft.com/library/jj591559.aspx)

-   **Bazy danych zdarzeń magazynu**. Oficjalna witryna.
    [*https://geteventstore.com/*](https://geteventstore.com/)

-   **Patrick Nommensen. Zarządzanie danymi zdarzeń dla Mikrousług**
    *<https://dzone.com/articles/event-driven-data-management-for-microservices-1> *

-   **Newtona centralnych zasad dostępu**
    [*https://en.wikipedia.org/wiki/CAP\_theorem*](https://en.wikipedia.org/wiki/CAP_theorem)

-   **Co to jest zakończenie Newtona?**
    [*https://www.quora.com/What-Is-CAP-Theorem-1*](https://www.quora.com/What-Is-CAP-Theorem-1)

-   **Elementarz spójność danych**
    [*https://msdn.microsoft.com/library/dn589800.aspx*](https://msdn.microsoft.com/library/dn589800.aspx)

-   **Rick Saling. Newtona zakończenia: Dlaczego "Wszystko, co jest różne" z chmury i Internet**
    [*https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/*](https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/)

-   **Marek Brewera. Zakończenie później dwunastu lat: jak "Zasady" zostały zmienione**
    [*https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed*](https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed)

-   **Udział w transakcje zewnętrzne (DTC)** (MSMQ) [*https://msdn.microsoft.com/library/ms978430.aspx\#bdadotnetasync2\_topic3c*](https://msdn.microsoft.com/library/ms978430.aspx%23bdadotnetasync2_topic3c)

-   **Azure Service Bus. Komunikatów obsługiwanych przez brokera: Wykrywanie zduplikowanych**
    [*https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25*](https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25)

-   **Przewodnik niezawodności** (dokumentacja RabbitMQ) [*https://www.rabbitmq.com/reliability.html\#consumer*](https://www.rabbitmq.com/reliability.html%23consumer)




>[!div class="step-by-step"]
[Poprzednie](rabbitmq-event-bus-development-test-environment.md)
[dalej](test-aspnet-core-services-web-apps.md)

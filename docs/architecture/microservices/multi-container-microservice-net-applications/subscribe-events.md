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
# <a name="subscribing-to-events"></a><span data-ttu-id="a6919-103">Subskrybowanie zdarzeń</span><span class="sxs-lookup"><span data-stu-id="a6919-103">Subscribing to events</span></span>

<span data-ttu-id="a6919-104">Pierwszym krokiem do korzystania z magistrali zdarzeń jest zasubskrybowanie mikrousług do zdarzeń, które mają być odbierane.</span><span class="sxs-lookup"><span data-stu-id="a6919-104">The first step for using the event bus is to subscribe the microservices to the events they want to receive.</span></span> <span data-ttu-id="a6919-105">Należy to zrobić w mikrousług odbiornika.</span><span class="sxs-lookup"><span data-stu-id="a6919-105">That should be done in the receiver microservices.</span></span>

<span data-ttu-id="a6919-106">Poniższy prosty kod pokazuje, co każdy mikrousługi odbiornika musi `Startup` zaimplementować podczas uruchamiania usługi (czyli w klasie), więc subskrybuje zdarzenia, których potrzebuje.</span><span class="sxs-lookup"><span data-stu-id="a6919-106">The following simple code shows what each receiver microservice needs to implement when starting the service (that is, in the `Startup` class) so it subscribes to the events it needs.</span></span> <span data-ttu-id="a6919-107">W takim przypadku `basket-api` mikrousługi musi `ProductPriceChangedIntegrationEvent` subskrybować i `OrderStartedIntegrationEvent` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a6919-107">In this case, the `basket-api` microservice needs to subscribe to `ProductPriceChangedIntegrationEvent` and the `OrderStartedIntegrationEvent` messages.</span></span>

<span data-ttu-id="a6919-108">Na przykład podczas subskrybowania `ProductPriceChangedIntegrationEvent` zdarzenia, który sprawia, że mikrousługi koszyka świadomość wszelkich zmian w cenie produktu i pozwala ostrzec użytkownika o zmianie, jeśli ten produkt znajduje się w koszyku użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a6919-108">For instance, when subscribing to the `ProductPriceChangedIntegrationEvent` event, that makes the basket microservice aware of any changes to the product price and lets it warn the user about the change if that product is in the user's basket.</span></span>

```csharp
var eventBus = app.ApplicationServices.GetRequiredService<IEventBus>();

eventBus.Subscribe<ProductPriceChangedIntegrationEvent,
                   ProductPriceChangedIntegrationEventHandler>();

eventBus.Subscribe<OrderStartedIntegrationEvent,
                   OrderStartedIntegrationEventHandler>();

```

<span data-ttu-id="a6919-109">Po uruchomieniu tego kodu mikrousługa subskrybenta będzie nasłuchiwać za pośrednictwem kanałów RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="a6919-109">After this code runs, the subscriber microservice will be listening through RabbitMQ channels.</span></span> <span data-ttu-id="a6919-110">Gdy pojawia się dowolny komunikat typu ProductPriceChangedIntegrationEvent, kod wywołuje program obsługi zdarzeń, który jest do niego przekazywany i przetwarza zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="a6919-110">When any message of type ProductPriceChangedIntegrationEvent arrives, the code invokes the event handler that is passed to it and processes the event.</span></span>

## <a name="publishing-events-through-the-event-bus"></a><span data-ttu-id="a6919-111">Publikowanie zdarzeń za pośrednictwem magistrali zdarzeń</span><span class="sxs-lookup"><span data-stu-id="a6919-111">Publishing events through the event bus</span></span>

<span data-ttu-id="a6919-112">Na koniec nadawca wiadomości (mikrousługa pochodzenia) publikuje zdarzenia integracji z kodem podobnym do poniższego przykładu.</span><span class="sxs-lookup"><span data-stu-id="a6919-112">Finally, the message sender (origin microservice) publishes the integration events with code similar to the following example.</span></span> <span data-ttu-id="a6919-113">(Jest to uproszczony przykład, który nie uwzględnia niepodzielności). Można zaimplementować podobny kod, gdy zdarzenie musi być propagowane w wielu mikrousług, zwykle zaraz po zaawoleniu danych lub transakcji z mikrousługi pochodzenia.</span><span class="sxs-lookup"><span data-stu-id="a6919-113">(This is a simplified example that does not take atomicity into account.) You would implement similar code whenever an event must be propagated across multiple microservices, usually right after committing data or transactions from the origin microservice.</span></span>

<span data-ttu-id="a6919-114">Po pierwsze obiekt implementacji magistrali zdarzeń (na podstawie RabbitMQ lub na podstawie magistrali usług) zostanie wstrzyknięty w konstruktorze kontrolera, jak w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="a6919-114">First, the event bus implementation object (based on RabbitMQ or based on a service bus) would be injected at the controller constructor, as in the following code:</span></span>

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

<span data-ttu-id="a6919-115">Następnie należy go użyć z metod kontrolera, takich jak w UpdateProduct metody:</span><span class="sxs-lookup"><span data-stu-id="a6919-115">Then you use it from your controller's methods, like in the UpdateProduct method:</span></span>

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

<span data-ttu-id="a6919-116">W takim przypadku, ponieważ mikrousługa pochodzenia jest prosta mikrousługa CRUD, ten kod jest umieszczany bezpośrednio w kontrolerze interfejsu API sieci Web.</span><span class="sxs-lookup"><span data-stu-id="a6919-116">In this case, since the origin microservice is a simple CRUD microservice, that code is placed right into a Web API controller.</span></span>

<span data-ttu-id="a6919-117">W bardziej zaawansowanych mikrousług, takich jak przy użyciu metod CQRS, można zaimplementować w `CommandHandler` klasie, w ramach `Handle()` metody.</span><span class="sxs-lookup"><span data-stu-id="a6919-117">In more advanced microservices, like when using CQRS approaches, it can be implemented in the `CommandHandler` class, within the `Handle()` method.</span></span>

### <a name="designing-atomicity-and-resiliency-when-publishing-to-the-event-bus"></a><span data-ttu-id="a6919-118">Projektowanie niepodzielności i odporności podczas publikowania w magistrali zdarzeń</span><span class="sxs-lookup"><span data-stu-id="a6919-118">Designing atomicity and resiliency when publishing to the event bus</span></span>

<span data-ttu-id="a6919-119">Podczas publikowania zdarzeń integracji za pośrednictwem rozproszonego systemu obsługi wiadomości, takich jak magistrala zdarzeń, masz problem z niepodzielnie aktualizowaniem oryginalnej bazy danych i publikowaniem zdarzenia (oznacza to, że obie operacje zostały zakończone lub żadna z nich).</span><span class="sxs-lookup"><span data-stu-id="a6919-119">When you publish integration events through a distributed messaging system like your event bus, you have the problem of atomically updating the original database and publishing an event (that is, either both operations complete or none of them).</span></span> <span data-ttu-id="a6919-120">Na przykład w uproszczonym przykładzie pokazano wcześniej, kod zatwierdza dane do bazy danych, gdy cena produktu zostanie zmieniona, a następnie publikuje ProductPriceChangedIntegrationEvent komunikat.</span><span class="sxs-lookup"><span data-stu-id="a6919-120">For instance, in the simplified example shown earlier, the code commits data to the database when the product price is changed and then publishes a ProductPriceChangedIntegrationEvent message.</span></span> <span data-ttu-id="a6919-121">Początkowo może to wyglądać istotne, że te dwie operacje są wykonywane atomically.</span><span class="sxs-lookup"><span data-stu-id="a6919-121">Initially, it might look essential that these two operations be performed atomically.</span></span> <span data-ttu-id="a6919-122">Jeśli jednak korzystasz z transakcji rozproszonej obejmującej bazę danych i brokera wiadomości, tak jak w starszych systemach, takich jak [Usługi kolejkowania wiadomości firmy Microsoft (MSMQ),](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx)nie jest to zalecane z powodów opisanych przez [oświadczenie CAP](https://www.quora.com/What-Is-CAP-Theorem-1).</span><span class="sxs-lookup"><span data-stu-id="a6919-122">However, if you are using a distributed transaction involving the database and the message broker, as you do in older systems like [Microsoft Message Queuing (MSMQ)](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx), this is not recommended for the reasons described by the [CAP theorem](https://www.quora.com/What-Is-CAP-Theorem-1).</span></span>

<span data-ttu-id="a6919-123">Zasadniczo mikrousług używasz do tworzenia skalowalnych i wysoce dostępnych systemów.</span><span class="sxs-lookup"><span data-stu-id="a6919-123">Basically, you use microservices to build scalable and highly available systems.</span></span> <span data-ttu-id="a6919-124">Upraszczając nieco, zasadokrwowe CAP mówi, że nie można zbudować (rozproszone) bazy danych (lub mikrousługi, która jest właścicielem modelu), który jest stale dostępny, silnie spójne *i* tolerancyjne dla każdej partycji.</span><span class="sxs-lookup"><span data-stu-id="a6919-124">Simplifying somewhat, the CAP theorem says that you cannot build a (distributed) database (or a microservice that owns its model) that's continually available, strongly consistent, *and* tolerant to any partition.</span></span> <span data-ttu-id="a6919-125">Należy wybrać dwie z tych trzech właściwości.</span><span class="sxs-lookup"><span data-stu-id="a6919-125">You must choose two of these three properties.</span></span>

<span data-ttu-id="a6919-126">W architekturach opartych na mikrousługach należy wybrać dostępność i tolerancję i należy odwkreślić silną spójność.</span><span class="sxs-lookup"><span data-stu-id="a6919-126">In microservices-based architectures, you should choose availability and tolerance, and you should de-emphasize strong consistency.</span></span> <span data-ttu-id="a6919-127">W związku z tym w większości nowoczesnych aplikacji opartych na mikrousługach zwykle nie chcesz używać transakcji rozproszonych w wiadomościach, tak jak podczas implementowania [transakcji rozproszonych](https://docs.microsoft.com/previous-versions/windows/desktop/ms681205(v=vs.85)) na podstawie koordynatora transakcji rozproszonych systemu Windows (DTC) z [usługą MSMQ](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="a6919-127">Therefore, in most modern microservice-based applications, you usually do not want to use distributed transactions in messaging, as you do when you implement [distributed transactions](https://docs.microsoft.com/previous-versions/windows/desktop/ms681205(v=vs.85)) based on the Windows Distributed Transaction Coordinator (DTC) with [MSMQ](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx).</span></span>

<span data-ttu-id="a6919-128">Wróćmy do początkowego problemu i jego przykładu.</span><span class="sxs-lookup"><span data-stu-id="a6919-128">Let's go back to the initial issue and its example.</span></span> <span data-ttu-id="a6919-129">Jeśli usługa ulegnie awarii po zaktualizowaniu bazy danych (w tym przypadku zaraz po wierszu kodu z `_context.SaveChangesAsync()`), ale przed opublikowaniem zdarzenia integracji ogólny system może stać się niespójny.</span><span class="sxs-lookup"><span data-stu-id="a6919-129">If the service crashes after the database is updated (in this case, right after the line of code with `_context.SaveChangesAsync()`), but before the integration event is published, the overall system could become inconsistent.</span></span> <span data-ttu-id="a6919-130">Może to być kluczowe dla firmy, w zależności od konkretnej operacji biznesowej, z którą masz do czynienia.</span><span class="sxs-lookup"><span data-stu-id="a6919-130">This might be business critical, depending on the specific business operation you are dealing with.</span></span>

<span data-ttu-id="a6919-131">Jak wspomniano wcześniej w sekcji architektury, można mieć kilka podejść do radzenia sobie z tym problemem:</span><span class="sxs-lookup"><span data-stu-id="a6919-131">As mentioned earlier in the architecture section, you can have several approaches for dealing with this issue:</span></span>

- <span data-ttu-id="a6919-132">Korzystanie z pełnego [wzorca pozyskiwania zdarzeń](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing).</span><span class="sxs-lookup"><span data-stu-id="a6919-132">Using the full [Event Sourcing pattern](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing).</span></span>

- <span data-ttu-id="a6919-133">Korzystanie z [dziennika transakcji górnictwa](https://www.scoop.it/t/sql-server-transaction-log-mining).</span><span class="sxs-lookup"><span data-stu-id="a6919-133">Using [transaction log mining](https://www.scoop.it/t/sql-server-transaction-log-mining).</span></span>

- <span data-ttu-id="a6919-134">Korzystanie [ze wzorca Skrzynki nadawczej](https://www.kamilgrzybek.com/design/the-outbox-pattern/).</span><span class="sxs-lookup"><span data-stu-id="a6919-134">Using the [Outbox pattern](https://www.kamilgrzybek.com/design/the-outbox-pattern/).</span></span> <span data-ttu-id="a6919-135">Jest to tabela transakcyjna do przechowywania zdarzeń integracji (rozszerzenie transakcji lokalnej).</span><span class="sxs-lookup"><span data-stu-id="a6919-135">This is a transactional table to store the integration events (extending the local transaction).</span></span>

<span data-ttu-id="a6919-136">W tym scenariuszu przy użyciu pełnego źródła zdarzeń (ES) wzorzec jest jednym z najlepszych podejść, jeśli *nie* najlepsze.</span><span class="sxs-lookup"><span data-stu-id="a6919-136">For this scenario, using the full Event Sourcing (ES) pattern is one of the best approaches, if not *the* best.</span></span> <span data-ttu-id="a6919-137">Jednak w wielu scenariuszach aplikacji może nie być w stanie zaimplementować pełnego systemu ES.</span><span class="sxs-lookup"><span data-stu-id="a6919-137">However, in many application scenarios, you might not be able to implement a full ES system.</span></span> <span data-ttu-id="a6919-138">ES oznacza przechowywanie tylko zdarzeń domeny w transakcyjnej bazie danych, zamiast przechowywania bieżących danych o stanie.</span><span class="sxs-lookup"><span data-stu-id="a6919-138">ES means storing only domain events in your transactional database, instead of storing current state data.</span></span> <span data-ttu-id="a6919-139">Przechowywanie tylko zdarzeń domeny może mieć wielkie korzyści, takie jak dostępność historii systemu i możliwość określenia stanu systemu w dowolnym momencie w przeszłości.</span><span class="sxs-lookup"><span data-stu-id="a6919-139">Storing only domain events can have great benefits, such as having the history of your system available and being able to determine the state of your system at any moment in the past.</span></span> <span data-ttu-id="a6919-140">Jednak wdrożenie pełnego systemu ES wymaga ponownego prześledu większości systemu i wprowadza wiele innych zawiłości i wymagań.</span><span class="sxs-lookup"><span data-stu-id="a6919-140">However, implementing a full ES system requires you to rearchitect most of your system and introduces many other complexities and requirements.</span></span> <span data-ttu-id="a6919-141">Na przykład należy użyć bazy danych specjalnie dla pozyskiwania zdarzeń, takich jak [Event Store](https://eventstore.org/)lub bazy danych zorientowanych na dokumenty, takich jak Azure Cosmos DB, MongoDB, Cassandra, CouchDB lub RavenDB.</span><span class="sxs-lookup"><span data-stu-id="a6919-141">For example, you would want to use a database specifically made for event sourcing, such as [Event Store](https://eventstore.org/), or a document-oriented database such as Azure Cosmos DB, MongoDB, Cassandra, CouchDB, or RavenDB.</span></span> <span data-ttu-id="a6919-142">ES to świetne podejście do tego problemu, ale nie jest to najłatwiejsze rozwiązanie, chyba że jesteś już zaznajomiony z pozyskiwaniem zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a6919-142">ES is a great approach for this problem, but not the easiest solution unless you are already familiar with event sourcing.</span></span>

<span data-ttu-id="a6919-143">Opcja użycia wyszukiwania dziennika transakcji początkowo wygląda na przezroczystą.</span><span class="sxs-lookup"><span data-stu-id="a6919-143">The option to use transaction log mining initially looks transparent.</span></span> <span data-ttu-id="a6919-144">Jednak aby użyć tego podejścia, mikrousługi musi być sprzężona z dziennikiem transakcji RDBMS, takich jak dziennik transakcji programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a6919-144">However, to use this approach, the microservice has to be coupled to your RDBMS transaction log, such as the SQL Server transaction log.</span></span> <span data-ttu-id="a6919-145">To prawdopodobnie nie jest pożądane.</span><span class="sxs-lookup"><span data-stu-id="a6919-145">This is probably not desirable.</span></span> <span data-ttu-id="a6919-146">Inną wadą jest to, że aktualizacje niskiego poziomu rejestrowane w dzienniku transakcji może nie być na tym samym poziomie co zdarzenia integracji wysokiego poziomu.</span><span class="sxs-lookup"><span data-stu-id="a6919-146">Another drawback is that the low-level updates recorded in the transaction log might not be at the same level as your high-level integration events.</span></span> <span data-ttu-id="a6919-147">Jeśli tak, proces inżynierii odwrotnej tych operacji dziennika transakcji może być trudne.</span><span class="sxs-lookup"><span data-stu-id="a6919-147">If so, the process of reverse-engineering those transaction log operations can be difficult.</span></span>

<span data-ttu-id="a6919-148">Zrównoważone podejście jest połączeniem tabeli transakcyjnej bazy danych i uproszczonego wzorca ES.</span><span class="sxs-lookup"><span data-stu-id="a6919-148">A balanced approach is a mix of a transactional database table and a simplified ES pattern.</span></span> <span data-ttu-id="a6919-149">Można użyć stanu, takiego jak "gotowe do opublikowania zdarzenia", który można ustawić w oryginalnym zdarzeniu podczas zatwierdzania go do tabeli zdarzeń integracji.</span><span class="sxs-lookup"><span data-stu-id="a6919-149">You can use a state such as "ready to publish the event," which you set in the original event when you commit it to the integration events table.</span></span> <span data-ttu-id="a6919-150">Następnie spróbuj opublikować zdarzenie w magistrali zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a6919-150">You then try to publish the event to the event bus.</span></span> <span data-ttu-id="a6919-151">Jeśli akcja publikowania zdarzenia powiedzie się, należy uruchomić inną transakcję w usłudze pochodzenia i przenieść stan z "gotowe do opublikowania zdarzenia" do "zdarzenia już opublikowane."</span><span class="sxs-lookup"><span data-stu-id="a6919-151">If the publish-event action succeeds, you start another transaction in the origin service and move the state from "ready to publish the event" to "event already published."</span></span>

<span data-ttu-id="a6919-152">Jeśli akcja publikowania zdarzenia w magistrali zdarzeń nie powiedzie się, dane nadal nie będą niespójne w mikrousługach pochodzenia — nadal jest oznaczona jako "gotowa do opublikowania zdarzenia", a w odniesieniu do pozostałych usług zostanie ostatecznie spójna.</span><span class="sxs-lookup"><span data-stu-id="a6919-152">If the publish-event action in the event bus fails, the data still will not be inconsistent within the origin microservice—it is still marked as "ready to publish the event," and with respect to the rest of the services, it will eventually be consistent.</span></span> <span data-ttu-id="a6919-153">Zawsze można mieć zadania w tle sprawdzanie stanu transakcji lub zdarzeń integracji.</span><span class="sxs-lookup"><span data-stu-id="a6919-153">You can always have background jobs checking the state of the transactions or integration events.</span></span> <span data-ttu-id="a6919-154">Jeśli zadanie znajdzie zdarzenie w stanie "Gotowe do opublikowania zdarzenia", może spróbować ponownie opublikować to zdarzenie w magistrali zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a6919-154">If the job finds an event in the "ready to publish the event" state, it can try to republish that event to the event bus.</span></span>

<span data-ttu-id="a6919-155">Należy zauważyć, że przy takim podejściu utrwalasz tylko zdarzenia integracji dla każdej mikrousługi pochodzenia i tylko zdarzenia, które chcesz komunikować się z innymi mikrousługami lub systemami zewnętrznymi.</span><span class="sxs-lookup"><span data-stu-id="a6919-155">Notice that with this approach, you are persisting only the integration events for each origin microservice, and only the events that you want to communicate to other microservices or external systems.</span></span> <span data-ttu-id="a6919-156">Natomiast w pełnym systemie ES przechowujesz również wszystkie zdarzenia domeny.</span><span class="sxs-lookup"><span data-stu-id="a6919-156">In contrast, in a full ES system, you store all domain events as well.</span></span>

<span data-ttu-id="a6919-157">W związku z tym to wyważone podejście jest uproszczonym systemem ES.</span><span class="sxs-lookup"><span data-stu-id="a6919-157">Therefore, this balanced approach is a simplified ES system.</span></span> <span data-ttu-id="a6919-158">Potrzebujesz listy zdarzeń integracji z ich bieżącym stanem ("gotowy do opublikowania" w porównaniu do "opublikowanych").</span><span class="sxs-lookup"><span data-stu-id="a6919-158">You need a list of integration events with their current state ("ready to publish" versus "published").</span></span> <span data-ttu-id="a6919-159">Ale wystarczy tylko zaimplementować te stany dla zdarzeń integracji.</span><span class="sxs-lookup"><span data-stu-id="a6919-159">But you only need to implement these states for the integration events.</span></span> <span data-ttu-id="a6919-160">I w tym podejściu nie trzeba przechowywać wszystkie dane domeny jako zdarzenia w transakcyjnej bazie danych, jak w pełnym systemie ES.</span><span class="sxs-lookup"><span data-stu-id="a6919-160">And in this approach, you do not need to store all your domain data as events in the transactional database, as you would in a full ES system.</span></span>

<span data-ttu-id="a6919-161">Jeśli używasz już relacyjnej bazy danych, można użyć tabeli transakcyjnej do przechowywania zdarzeń integracji.</span><span class="sxs-lookup"><span data-stu-id="a6919-161">If you are already using a relational database, you can use a transactional table to store integration events.</span></span> <span data-ttu-id="a6919-162">Aby osiągnąć niepodzielność w aplikacji, należy użyć procesu dwuetapowego opartego na transakcjach lokalnych.</span><span class="sxs-lookup"><span data-stu-id="a6919-162">To achieve atomicity in your application, you use a two-step process based on local transactions.</span></span> <span data-ttu-id="a6919-163">Zasadniczo masz IntegrationEvent tabeli w tej samej bazie danych, gdzie masz jednostek domeny.</span><span class="sxs-lookup"><span data-stu-id="a6919-163">Basically, you have an IntegrationEvent table in the same database where you have your domain entities.</span></span> <span data-ttu-id="a6919-164">Ta tabela działa jako ubezpieczenie dla osiągnięcia niepodzielności, dzięki czemu można uwzględnić utrwalone zdarzenia integracji do tych samych transakcji, które zatwierdzają dane domeny.</span><span class="sxs-lookup"><span data-stu-id="a6919-164">That table works as an insurance for achieving atomicity so that you include persisted integration events into the same transactions that are committing your domain data.</span></span>

<span data-ttu-id="a6919-165">Krok po kroku proces przebiega w ten sposób:</span><span class="sxs-lookup"><span data-stu-id="a6919-165">Step by step, the process goes like this:</span></span>

1. <span data-ttu-id="a6919-166">Aplikacja rozpoczyna transakcję lokalnej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="a6919-166">The application begins a local database transaction.</span></span>

2. <span data-ttu-id="a6919-167">Następnie aktualizuje stan jednostek domeny i wstawia zdarzenie do tabeli zdarzeń integracji.</span><span class="sxs-lookup"><span data-stu-id="a6919-167">It then updates the state of your domain entities and inserts an event into the integration event table.</span></span>

3. <span data-ttu-id="a6919-168">Wreszcie, zatwierdza transakcję, więc można uzyskać żądaną niepodzielność, a następnie</span><span class="sxs-lookup"><span data-stu-id="a6919-168">Finally, it commits the transaction, so you get the desired atomicity and then</span></span>

4. <span data-ttu-id="a6919-169">Publikujesz zdarzenie w jakiś sposób (dalej).</span><span class="sxs-lookup"><span data-stu-id="a6919-169">You publish the event somehow (next).</span></span>

<span data-ttu-id="a6919-170">Podczas implementowania kroków publikowania zdarzeń, masz następujące możliwości:</span><span class="sxs-lookup"><span data-stu-id="a6919-170">When implementing the steps of publishing the events, you have these choices:</span></span>

- <span data-ttu-id="a6919-171">Opublikuj zdarzenie integracji zaraz po zawiązaniu transakcji i użyj innej transakcji lokalnej, aby oznaczyć zdarzenia w tabeli jako opublikowane.</span><span class="sxs-lookup"><span data-stu-id="a6919-171">Publish the integration event right after committing the transaction and use another local transaction to mark the events in the table as being published.</span></span> <span data-ttu-id="a6919-172">Następnie użyj tabeli tylko jako artefakt do śledzenia zdarzeń integracji w przypadku problemów w mikrousług zdalnych i wykonać akcje kompensacyjne na podstawie przechowywanych zdarzeń integracji.</span><span class="sxs-lookup"><span data-stu-id="a6919-172">Then, use the table just as an artifact to track the integration events in case of issues in the remote microservices, and perform compensatory actions based on the stored integration events.</span></span>

- <span data-ttu-id="a6919-173">Użyj tabeli jako rodzaju kolejki.</span><span class="sxs-lookup"><span data-stu-id="a6919-173">Use the table as a kind of queue.</span></span> <span data-ttu-id="a6919-174">Oddzielny wątek aplikacji lub proces zapyta tabelę zdarzeń integracji, publikuje zdarzenia do magistrali zdarzeń, a następnie używa transakcji lokalnej, aby oznaczyć zdarzenia jako opublikowane.</span><span class="sxs-lookup"><span data-stu-id="a6919-174">A separate application thread or process queries the integration event table, publishes the events to the event bus, and then uses a local transaction to mark the events as published.</span></span>

<span data-ttu-id="a6919-175">Rysunek 6-22 przedstawia architekturę dla pierwszego z tych podejść.</span><span class="sxs-lookup"><span data-stu-id="a6919-175">Figure 6-22 shows the architecture for the first of these approaches.</span></span>

![Diagram niepodzielności podczas publikowania bez mikrousług procesu roboczego.](./media/subscribe-events/atomicity-publish-event-bus.png)

<span data-ttu-id="a6919-177">**Rysunek 6-22**.</span><span class="sxs-lookup"><span data-stu-id="a6919-177">**Figure 6-22**.</span></span> <span data-ttu-id="a6919-178">Niepodzielność podczas publikowania zdarzeń w magistrali zdarzeń</span><span class="sxs-lookup"><span data-stu-id="a6919-178">Atomicity when publishing events to the event bus</span></span>

<span data-ttu-id="a6919-179">Podejście zilustrowane na rysunku 6-22 brakuje dodatkowej mikrousługi procesu roboczego, która jest odpowiedzialna za sprawdzanie i potwierdzanie powodzenia opublikowanych zdarzeń integracji.</span><span class="sxs-lookup"><span data-stu-id="a6919-179">The approach illustrated in Figure 6-22 is missing an additional worker microservice that is in charge of checking and confirming the success of the published integration events.</span></span> <span data-ttu-id="a6919-180">W przypadku awarii, że dodatkowe mikrousługi procesu sprawdzania procesu sprawdzania można odczytać zdarzenia z tabeli i opublikować je ponownie, czyli powtórzyć krok numer 2.</span><span class="sxs-lookup"><span data-stu-id="a6919-180">In case of failure, that additional checker worker microservice can read events from the table and republish them, that is, repeat step number 2.</span></span>

<span data-ttu-id="a6919-181">O drugim podejściu: używasz EventLog tabeli jako kolejki i zawsze używać mikrousług procesu roboczego do publikowania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a6919-181">About the second approach: you use the EventLog table as a queue and always use a worker microservice to publish the messages.</span></span> <span data-ttu-id="a6919-182">W takim przypadku proces jest podobny do przedstawionego na rysunku 6-23.</span><span class="sxs-lookup"><span data-stu-id="a6919-182">In that case, the process is like that shown in Figure 6-23.</span></span> <span data-ttu-id="a6919-183">Spowoduje to wyświetleń dodatkowe mikrousługi, a tabela jest pojedynczym źródłem podczas publikowania zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a6919-183">This shows an additional microservice, and the table is the single source when publishing events.</span></span>

![Diagram niepodzielności podczas publikowania za pomocą mikrousług procesu roboczego.](./media/subscribe-events/atomicity-publish-worker-microservice.png)

<span data-ttu-id="a6919-185">**Rysunek 6-23**.</span><span class="sxs-lookup"><span data-stu-id="a6919-185">**Figure 6-23**.</span></span> <span data-ttu-id="a6919-186">Niepodzielność podczas publikowania zdarzeń w magistrali zdarzeń za pomocą mikrousług procesu roboczego</span><span class="sxs-lookup"><span data-stu-id="a6919-186">Atomicity when publishing events to the event bus with a worker microservice</span></span>

<span data-ttu-id="a6919-187">Dla uproszczenia przykład eShopOnContainers używa pierwszego podejścia (bez dodatkowych procesów lub mikrousług sprawdzania) plus magistrali zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a6919-187">For simplicity, the eShopOnContainers sample uses the first approach (with no additional processes or checker microservices) plus the event bus.</span></span> <span data-ttu-id="a6919-188">Jednak przykład eShopOnContainers nie obsługuje wszystkich możliwych przypadków awarii.</span><span class="sxs-lookup"><span data-stu-id="a6919-188">However, the eShopOnContainers sample is not handling all possible failure cases.</span></span> <span data-ttu-id="a6919-189">W rzeczywistej aplikacji wdrożonej w chmurze, należy ogarnąć fakt, że problemy pojawią się w końcu i należy zaimplementować, że logika sprawdzania i ponownego wysłania.</span><span class="sxs-lookup"><span data-stu-id="a6919-189">In a real application deployed to the cloud, you must embrace the fact that issues will arise eventually, and you must implement that check and resend logic.</span></span> <span data-ttu-id="a6919-190">Korzystanie z tabeli jako kolejki może być bardziej skuteczne niż pierwsze podejście, jeśli masz tę tabelę jako pojedyncze źródło zdarzeń podczas publikowania ich (z pracownikiem) za pośrednictwem magistrali zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a6919-190">Using the table as a queue can be more effective than the first approach if you have that table as a single source of events when publishing them (with the worker) through the event bus.</span></span>

### <a name="implementing-atomicity-when-publishing-integration-events-through-the-event-bus"></a><span data-ttu-id="a6919-191">Implementowanie niepodzielności podczas publikowania zdarzeń integracji za pośrednictwem magistrali zdarzeń</span><span class="sxs-lookup"><span data-stu-id="a6919-191">Implementing atomicity when publishing integration events through the event bus</span></span>

<span data-ttu-id="a6919-192">Poniższy kod pokazuje, jak można utworzyć pojedynczą transakcję obejmującą wiele obiektów DbContext — jeden kontekst związany z oryginalnymi danymi aktualizowanymi, a drugi kontekst związany z integrationeventlog tabeli.</span><span class="sxs-lookup"><span data-stu-id="a6919-192">The following code shows how you can create a single transaction involving multiple DbContext objects—one context related to the original data being updated, and the second context related to the IntegrationEventLog table.</span></span>

<span data-ttu-id="a6919-193">Transakcja w poniższym przykładowym kodzie nie będzie odporna, jeśli połączenia z bazą danych mają jakikolwiek problem w czasie, gdy kod jest uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="a6919-193">The transaction in the example code below will not be resilient if connections to the database have any issue at the time when the code is running.</span></span> <span data-ttu-id="a6919-194">Może się to zdarzyć w systemach opartych na chmurze, takich jak Azure SQL DB, które mogą przenosić bazy danych na serwerach.</span><span class="sxs-lookup"><span data-stu-id="a6919-194">This can happen in cloud-based systems like Azure SQL DB, which might move databases across servers.</span></span> <span data-ttu-id="a6919-195">Aby zaimplementować transakcje odporne w wielu kontekstach, zobacz [Implementing resilient Entity Framework Core połączeń SQL](../implement-resilient-applications/implement-resilient-entity-framework-core-sql-connections.md) w dalszej części tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="a6919-195">For implementing resilient transactions across multiple contexts, see the [Implementing resilient Entity Framework Core SQL connections](../implement-resilient-applications/implement-resilient-entity-framework-core-sql-connections.md) section later in this guide.</span></span>

<span data-ttu-id="a6919-196">Dla jasności w poniższym przykładzie przedstawiono cały proces w jednym kawałku kodu.</span><span class="sxs-lookup"><span data-stu-id="a6919-196">For clarity, the following example shows the whole process in a single piece of code.</span></span> <span data-ttu-id="a6919-197">Jednak implementacja eShopOnContainers jest refaktoryzowana i dzieli tę logikę na wiele klas, dzięki czemu jest łatwiejsza do utrzymania.</span><span class="sxs-lookup"><span data-stu-id="a6919-197">However, the eShopOnContainers implementation is refactored and splits this logic into multiple classes so it's easier to maintain.</span></span>

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

<span data-ttu-id="a6919-198">Po utworzeniu zdarzenia integracji ProductPriceChangedIntegrationEvent transakcja, która przechowuje oryginalną operację domeny (aktualizacja elementu katalogu) zawiera również trwałość zdarzenia w tabeli EventLog.</span><span class="sxs-lookup"><span data-stu-id="a6919-198">After the ProductPriceChangedIntegrationEvent integration event is created, the transaction that stores the original domain operation (update the catalog item) also includes the persistence of the event in the EventLog table.</span></span> <span data-ttu-id="a6919-199">To sprawia, że jest to pojedyncza transakcja i zawsze będzie można sprawdzić, czy wiadomości o zdarzeniach zostały wysłane.</span><span class="sxs-lookup"><span data-stu-id="a6919-199">This makes it a single transaction, and you will always be able to check whether event messages were sent.</span></span>

<span data-ttu-id="a6919-200">Tabela dziennika zdarzeń jest aktualizowana niepodzielnie przy użyciu oryginalnej operacji bazy danych przy użyciu transakcji lokalnej dla tej samej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="a6919-200">The event log table is updated atomically with the original database operation, using a local transaction against the same database.</span></span> <span data-ttu-id="a6919-201">Jeśli którakolwiek z operacji zakończy się niepowodzeniem, wyjątek zostanie zgłoszony, a transakcja wycofuje wszystkie zakończone operacje, zachowując w ten sposób spójność między operacjami domeny a komunikatami o zdarzeniach zapisanymi w tabeli.</span><span class="sxs-lookup"><span data-stu-id="a6919-201">If any of the operations fail, an exception is thrown and the transaction rolls back any completed operation, thus maintaining consistency between the domain operations and the event messages saved to the table.</span></span>

### <a name="receiving-messages-from-subscriptions-event-handlers-in-receiver-microservices"></a><span data-ttu-id="a6919-202">Odbieranie komunikatów z subskrypcji: programy obsługi zdarzeń w mikrousługach odbiorcy</span><span class="sxs-lookup"><span data-stu-id="a6919-202">Receiving messages from subscriptions: event handlers in receiver microservices</span></span>

<span data-ttu-id="a6919-203">Oprócz logiki subskrypcji zdarzeń należy zaimplementować wewnętrzny kod dla programów obsługi zdarzeń integracji (takich jak metoda wywołania zwrotnego).</span><span class="sxs-lookup"><span data-stu-id="a6919-203">In addition to the event subscription logic, you need to implement the internal code for the integration event handlers (like a callback method).</span></span> <span data-ttu-id="a6919-204">Program obsługi zdarzeń jest, gdzie można określić, gdzie komunikaty o zdarzeniach określonego typu będą odbierane i przetwarzane.</span><span class="sxs-lookup"><span data-stu-id="a6919-204">The event handler is where you specify where the event messages of a certain type will be received and processed.</span></span>

<span data-ttu-id="a6919-205">Program obsługi zdarzeń najpierw odbiera wystąpienie zdarzenia z magistrali zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a6919-205">An event handler first receives an event instance from the event bus.</span></span> <span data-ttu-id="a6919-206">Następnie lokalizuje składnik do przetworzenia związane z tym zdarzeniem integracji, propagacji i utrwalania zdarzenia jako zmiany stanu w mikrousługi odbiornika.</span><span class="sxs-lookup"><span data-stu-id="a6919-206">Then it locates the component to be processed related to that integration event, propagating and persisting the event as a change in state in the receiver microservice.</span></span> <span data-ttu-id="a6919-207">Na przykład jeśli ProductPriceChanged zdarzenie pochodzi z mikrousługi katalogu, jest obsługiwany w mikrousługi koszyka i zmienia stan w tym mikrousługi koszyka odbiornika, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="a6919-207">For example, if a ProductPriceChanged event originates in the catalog microservice, it is handled in the basket microservice and changes the state in this receiver basket microservice as well, as shown in the following code.</span></span>

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

<span data-ttu-id="a6919-208">Program obsługi zdarzeń musi sprawdzić, czy produkt istnieje w dowolnym wystąpieniu koszyka.</span><span class="sxs-lookup"><span data-stu-id="a6919-208">The event handler needs to verify whether the product exists in any of the basket instances.</span></span> <span data-ttu-id="a6919-209">Aktualizuje również cenę towaru dla każdego powiązanego elementu zamówienia koszyka.</span><span class="sxs-lookup"><span data-stu-id="a6919-209">It also updates the item price for each related basket line item.</span></span> <span data-ttu-id="a6919-210">Na koniec tworzy alert, który ma być wyświetlany użytkownikowi o zmianie ceny, jak pokazano na rysunku 6-24.</span><span class="sxs-lookup"><span data-stu-id="a6919-210">Finally, it creates an alert to be displayed to the user about the price change, as shown in Figure 6-24.</span></span>

![Zrzut ekranu przedstawiający przeglądarkę z powiadomieniem o zmianie ceny w koszyku użytkownika.](./media/subscribe-events/display-item-price-change.png)

<span data-ttu-id="a6919-212">**Rysunek 6-24**.</span><span class="sxs-lookup"><span data-stu-id="a6919-212">**Figure 6-24**.</span></span> <span data-ttu-id="a6919-213">Wyświetlanie zmiany ceny towaru w koszyku, zgodnie z komunikatami o zdarzeniach integracji</span><span class="sxs-lookup"><span data-stu-id="a6919-213">Displaying an item price change in a basket, as communicated by integration events</span></span>

## <a name="idempotency-in-update-message-events"></a><span data-ttu-id="a6919-214">Idempotency w zdarzeniach wiadomości aktualizacji</span><span class="sxs-lookup"><span data-stu-id="a6919-214">Idempotency in update message events</span></span>

<span data-ttu-id="a6919-215">Ważnym aspektem zdarzeń wiadomości aktualizacji jest, że błąd w dowolnym momencie komunikacji powinien spowodować ponowione próby wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a6919-215">An important aspect of update message events is that a failure at any point in the communication should cause the message to be retried.</span></span> <span data-ttu-id="a6919-216">W przeciwnym razie zadanie w tle może próbować opublikować zdarzenie, które zostało już opublikowane, tworząc warunek wyścigu.</span><span class="sxs-lookup"><span data-stu-id="a6919-216">Otherwise a background task might try to publish an event that has already been published, creating a race condition.</span></span> <span data-ttu-id="a6919-217">Upewnij się, że aktualizacje są idempotentności lub że zawierają wystarczające informacje, aby upewnić się, że można wykryć duplikat, odrzucić go i wysłać z powrotem tylko jedną odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="a6919-217">Make sure that the updates are either idempotent or that they provide enough information to ensure that you can detect a duplicate, discard it, and send back only one response.</span></span>

<span data-ttu-id="a6919-218">Jak wspomniano wcześniej, idempotency oznacza, że operacja może być wykonywana wiele razy bez zmiany wyniku.</span><span class="sxs-lookup"><span data-stu-id="a6919-218">As noted earlier, idempotency means that an operation can be performed multiple times without changing the result.</span></span> <span data-ttu-id="a6919-219">W środowisku obsługi wiadomości, jak podczas komunikowania się zdarzeń, zdarzenie jest idempotentne, jeśli może być dostarczone wiele razy bez zmiany wyniku dla mikrousługi odbiornika.</span><span class="sxs-lookup"><span data-stu-id="a6919-219">In a messaging environment, as when communicating events, an event is idempotent if it can be delivered multiple times without changing the result for the receiver microservice.</span></span> <span data-ttu-id="a6919-220">Może to być konieczne ze względu na charakter samego zdarzenia lub ze względu na sposób, w jaki system obsługuje zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="a6919-220">This may be necessary because of the nature of the event itself, or because of the way the system handles the event.</span></span> <span data-ttu-id="a6919-221">Idempotency wiadomości jest ważne w każdej aplikacji, która używa wiadomości, nie tylko w aplikacjach, które implementują wzorzec magistrali zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a6919-221">Message idempotency is important in any application that uses messaging, not just in applications that implement the event bus pattern.</span></span>

<span data-ttu-id="a6919-222">Przykładem operacji idempotentna jest instrukcja SQL, która wstawia dane do tabeli tylko wtedy, gdy te dane nie są jeszcze w tabeli.</span><span class="sxs-lookup"><span data-stu-id="a6919-222">An example of an idempotent operation is a SQL statement that inserts data into a table only if that data is not already in the table.</span></span> <span data-ttu-id="a6919-223">Nie ma znaczenia, ile razy można uruchomić, że wstawić instrukcję SQL; wynik będzie taki sam — tabela będzie zawierać te dane.</span><span class="sxs-lookup"><span data-stu-id="a6919-223">It does not matter how many times you run that insert SQL statement; the result will be the same—the table will contain that data.</span></span> <span data-ttu-id="a6919-224">Idempotency jak to może być również konieczne podczas czynienia z wiadomościami, jeśli wiadomości mogą być potencjalnie wysyłane i w związku z tym przetwarzane więcej niż jeden raz.</span><span class="sxs-lookup"><span data-stu-id="a6919-224">Idempotency like this can also be necessary when dealing with messages if the messages could potentially be sent and therefore processed more than once.</span></span> <span data-ttu-id="a6919-225">Na przykład jeśli logika ponawiania powoduje, że nadawca wysyła dokładnie tę samą wiadomość więcej niż jeden raz, należy upewnić się, że jest idempotentne.</span><span class="sxs-lookup"><span data-stu-id="a6919-225">For instance, if retry logic causes a sender to send exactly the same message more than once, you need to make sure that it is idempotent.</span></span>

<span data-ttu-id="a6919-226">Możliwe jest projektowanie idempotentne wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a6919-226">It is possible to design idempotent messages.</span></span> <span data-ttu-id="a6919-227">Na przykład możesz utworzyć zdarzenie z napisem "ustaw cenę produktu na 25 USD" zamiast "dodaj 5 USD do ceny produktu".</span><span class="sxs-lookup"><span data-stu-id="a6919-227">For example, you can create an event that says "set the product price to $25" instead of "add $5 to the product price."</span></span> <span data-ttu-id="a6919-228">Można bezpiecznie przetworzyć pierwszą wiadomość dowolną liczbę razy, a wynik będzie taki sam.</span><span class="sxs-lookup"><span data-stu-id="a6919-228">You could safely process the first message any number of times and the result will be the same.</span></span> <span data-ttu-id="a6919-229">To nie jest prawda w przypadku drugiego przesłania.</span><span class="sxs-lookup"><span data-stu-id="a6919-229">That is not true for the second message.</span></span> <span data-ttu-id="a6919-230">Ale nawet w pierwszym przypadku możesz nie chcieć przetworzyć pierwszego zdarzenia, ponieważ system mógł również wysłać nowsze zdarzenie zmiany ceny i nadpisujesz nową cenę.</span><span class="sxs-lookup"><span data-stu-id="a6919-230">But even in the first case, you might not want to process the first event, because the system could also have sent a newer price-change event and you would be overwriting the new price.</span></span>

<span data-ttu-id="a6919-231">Innym przykładem może być zdarzenie zakończone zamówieniem, które jest propagowane do wielu subskrybentów.</span><span class="sxs-lookup"><span data-stu-id="a6919-231">Another example might be an order-completed event that's propagated to multiple subscribers.</span></span> <span data-ttu-id="a6919-232">Aplikacja musi upewnić się, że informacje o zamówieniu są aktualizowane w innych systemach tylko raz, nawet jeśli istnieją zduplikowane zdarzenia wiadomości dla tego samego zdarzenia zakończonego zamówienia.</span><span class="sxs-lookup"><span data-stu-id="a6919-232">The app has to make sure that order information is updated in other systems only once, even if there are duplicated message events for the same order-completed event.</span></span>

<span data-ttu-id="a6919-233">Jest to wygodne, aby mieć pewnego rodzaju tożsamości na zdarzenie, dzięki czemu można utworzyć logikę, która wymusza, że każde zdarzenie jest przetwarzane tylko raz na odbiornik.</span><span class="sxs-lookup"><span data-stu-id="a6919-233">It is convenient to have some kind of identity per event so that you can create logic that enforces that each event is processed only once per receiver.</span></span>

<span data-ttu-id="a6919-234">Niektóre przetwarzanie wiadomości jest z natury idempotentne.</span><span class="sxs-lookup"><span data-stu-id="a6919-234">Some message processing is inherently idempotent.</span></span> <span data-ttu-id="a6919-235">Na przykład jeśli system generuje miniatury obrazów, może nie mieć znaczenia, ile razy jest przetwarzany komunikat o wygenerowanej miniaturze; wynik jest taki, że miniatury są generowane i są takie same za każdym razem.</span><span class="sxs-lookup"><span data-stu-id="a6919-235">For example, if a system generates image thumbnails, it might not matter how many times the message about the generated thumbnail is processed; the outcome is that the thumbnails are generated and they are the same every time.</span></span> <span data-ttu-id="a6919-236">Z drugiej strony, operacje takie jak wywołanie bramki płatniczej w celu obciążenia karty kredytowej mogą w ogóle nie być dowodu osobistego.</span><span class="sxs-lookup"><span data-stu-id="a6919-236">On the other hand, operations such as calling a payment gateway to charge a credit card may not be idempotent at all.</span></span> <span data-ttu-id="a6919-237">W takich przypadkach należy upewnić się, że przetwarzanie wiadomości wiele razy ma oczekiwany efekt.</span><span class="sxs-lookup"><span data-stu-id="a6919-237">In these cases, you need to ensure that processing a message multiple times has the effect that you expect.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="a6919-238">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="a6919-238">Additional resources</span></span>

- <span data-ttu-id="a6919-239">**Honorowanie idempotency wiadomości** </span><span class="sxs-lookup"><span data-stu-id="a6919-239">**Honoring message idempotency** </span></span>\
  <https://docs.microsoft.com/previous-versions/msp-n-p/jj591565(v=pandp.10)#honoring-message-idempotency>

## <a name="deduplicating-integration-event-messages"></a><span data-ttu-id="a6919-240">Deduplikowanie komunikatów o zdarzeniach integracji</span><span class="sxs-lookup"><span data-stu-id="a6919-240">Deduplicating integration event messages</span></span>

<span data-ttu-id="a6919-241">Możesz się upewnić, że zdarzenia wiadomości są wysyłane i przetwarzane tylko raz na subskrybenta na różnych poziomach.</span><span class="sxs-lookup"><span data-stu-id="a6919-241">You can make sure that message events are sent and processed only once per subscriber at different levels.</span></span> <span data-ttu-id="a6919-242">Jednym ze sposobów jest użycie funkcji deduplikacji oferowanej przez używaną infrastrukturę obsługi wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a6919-242">One way is to use a deduplication feature offered by the messaging infrastructure you are using.</span></span> <span data-ttu-id="a6919-243">Innym jest zaimplementowanie logiki niestandardowej w mikrousługi docelowej.</span><span class="sxs-lookup"><span data-stu-id="a6919-243">Another is to implement custom logic in your destination microservice.</span></span> <span data-ttu-id="a6919-244">Posiadanie weryfikacji zarówno na poziomie transportu, jak i na poziomie aplikacji jest najlepszym rozwiązaniem.</span><span class="sxs-lookup"><span data-stu-id="a6919-244">Having validations at both the transport level and the application level is your best bet.</span></span>

### <a name="deduplicating-message-events-at-the-eventhandler-level"></a><span data-ttu-id="a6919-245">Deduplikowanie zdarzeń wiadomości na poziomie EventHandler</span><span class="sxs-lookup"><span data-stu-id="a6919-245">Deduplicating message events at the EventHandler level</span></span>

<span data-ttu-id="a6919-246">Jednym ze sposobów, aby upewnić się, że zdarzenie jest przetwarzane tylko raz przez dowolnego odbiorcy jest implementowanie pewnej logiki podczas przetwarzania zdarzeń wiadomości w programach obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a6919-246">One way to make sure that an event is processed only once by any receiver is by implementing certain logic when processing the message events in event handlers.</span></span> <span data-ttu-id="a6919-247">Na przykład jest to podejście używane w aplikacji eShopOnContainers, jak widać w [kodzie źródłowym UserCheckoutAcceptedIntegrationEventHandler klasy](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) po odebraniu `UserCheckoutAcceptedIntegrationEvent` zdarzenia integracji.</span><span class="sxs-lookup"><span data-stu-id="a6919-247">For example, that is the approach used in the eShopOnContainers application, as you can see in the [source code of the UserCheckoutAcceptedIntegrationEventHandler class](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) when it receives a `UserCheckoutAcceptedIntegrationEvent` integration event.</span></span> <span data-ttu-id="a6919-248">(W takim przypadku `CreateOrderCommand` jest zawijany `IdentifiedCommand` `eventMsg.RequestId` z , przy użyciu jako identyfikator, przed wysłaniem go do programu obsługi polecenia).</span><span class="sxs-lookup"><span data-stu-id="a6919-248">(In this case, the `CreateOrderCommand` is wrapped with an `IdentifiedCommand`, using the `eventMsg.RequestId` as an identifier, before sending it to the command handler).</span></span>

### <a name="deduplicating-messages-when-using-rabbitmq"></a><span data-ttu-id="a6919-249">Deduplikowanie wiadomości podczas korzystania z RabbitMQ</span><span class="sxs-lookup"><span data-stu-id="a6919-249">Deduplicating messages when using RabbitMQ</span></span>

<span data-ttu-id="a6919-250">W przypadku wystąpienia sporadyczne błędy sieci wiadomości mogą być duplikowane, a odbiornik wiadomości musi być gotowy do obsługi tych zduplikowanych wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a6919-250">When intermittent network failures happen, messages can be duplicated, and the message receiver must be ready to handle these duplicated messages.</span></span> <span data-ttu-id="a6919-251">Jeśli to możliwe, odbiorniki powinny obsługiwać wiadomości w sposób idempotentny, co jest lepsze niż jawne obchodzenia się z nimi za pomocą deduplikacji.</span><span class="sxs-lookup"><span data-stu-id="a6919-251">If possible, receivers should handle messages in an idempotent way, which is better than explicitly handling them with deduplication.</span></span>

<span data-ttu-id="a6919-252">Zgodnie z [dokumentacją RabbitMQ](https://www.rabbitmq.com/reliability.html#consumer), "Jeśli wiadomość zostanie dostarczona do konsumenta, a następnie ponownie w kolejce (ponieważ nie została potwierdzona przed przerwaniem połączenia konsumenckiego), wówczas RabbitMQ ustawi na niej ponownie dostarczoną flagę, gdy zostanie dostarczona ponownie (czy to do tego samego konsumenta, czy do innego).</span><span class="sxs-lookup"><span data-stu-id="a6919-252">According to the [RabbitMQ documentation](https://www.rabbitmq.com/reliability.html#consumer), "If a message is delivered to a consumer and then requeued (because it was not acknowledged before the consumer connection dropped, for example) then RabbitMQ will set the redelivered flag on it when it is delivered again (whether to the same consumer or a different one).</span></span>

<span data-ttu-id="a6919-253">Jeśli ustawiona jest flaga "redelivered", odbiorca musi wziąć to pod uwagę, ponieważ wiadomość mogła już zostać przetworzona.</span><span class="sxs-lookup"><span data-stu-id="a6919-253">If the "redelivered" flag is set, the receiver must take that into account, because the message might already have been processed.</span></span> <span data-ttu-id="a6919-254">Ale to nie jest gwarantowane; wiadomość może nigdy nie dotarła do odbiorcy po opuszczeniu brokera wiadomości, być może z powodu problemów z siecią.</span><span class="sxs-lookup"><span data-stu-id="a6919-254">But that is not guaranteed; the message might never have reached the receiver after it left the message broker, perhaps because of network issues.</span></span> <span data-ttu-id="a6919-255">Z drugiej strony, jeśli flaga "redelivered" nie jest ustawiona, jest gwarantowana, że wiadomość nie została wysłana więcej niż jeden raz.</span><span class="sxs-lookup"><span data-stu-id="a6919-255">On the other hand, if the "redelivered" flag is not set, it is guaranteed that the message has not been sent more than once.</span></span> <span data-ttu-id="a6919-256">W związku z tym odbiornik musi deduplikować wiadomości lub przetwarzać wiadomości w sposób idempotentny tylko wtedy, gdy flaga "redelivered" jest ustawiona w wiadomości.</span><span class="sxs-lookup"><span data-stu-id="a6919-256">Therefore, the receiver needs to deduplicate messages or process messages in an idempotent way only if the "redelivered" flag is set in the message.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="a6919-257">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="a6919-257">Additional resources</span></span>

- <span data-ttu-id="a6919-258">**Rozwidał eShopOnContainers przy użyciu NServiceBus (Dane oprogramowanie)** </span><span class="sxs-lookup"><span data-stu-id="a6919-258">**Forked eShopOnContainers using NServiceBus (Particular Software)** </span></span>\
    <https://go.particular.net/eShopOnContainers>

- <span data-ttu-id="a6919-259">**Wiadomości sterowane zdarzeniami** </span><span class="sxs-lookup"><span data-stu-id="a6919-259">**Event Driven Messaging** </span></span>\
    <https://patterns.arcitura.com/soa-patterns/design_patterns/event_driven_messaging>

- <span data-ttu-id="a6919-260">**Jimmy Bogard. Refaktoryzowanie w kierunku odporności: ocena sprzężenia** </span><span class="sxs-lookup"><span data-stu-id="a6919-260">**Jimmy Bogard. Refactoring Towards Resilience: Evaluating Coupling** </span></span>\
    <https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/>

- <span data-ttu-id="a6919-261">**Publikuj-Subskrybuj kanał** </span><span class="sxs-lookup"><span data-stu-id="a6919-261">**Publish-Subscribe channel** </span></span>\
    <https://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html>

- <span data-ttu-id="a6919-262">**Komunikowanie się między ograniczonymi kontekstami** </span><span class="sxs-lookup"><span data-stu-id="a6919-262">**Communicating Between Bounded Contexts** </span></span>\
    <https://docs.microsoft.com/previous-versions/msp-n-p/jj591572(v=pandp.10)>

- <span data-ttu-id="a6919-263">**Spójność ostateczna** </span><span class="sxs-lookup"><span data-stu-id="a6919-263">**Eventual Consistency** </span></span>\
    <https://en.wikipedia.org/wiki/Eventual_consistency>

- <span data-ttu-id="a6919-264">**Philip Brown. Strategie integracji ograniczonych kontekstów** </span><span class="sxs-lookup"><span data-stu-id="a6919-264">**Philip Brown. Strategies for Integrating Bounded Contexts** </span></span>\
    <https://www.culttt.com/2014/11/26/strategies-integrating-bounded-contexts/>

- <span data-ttu-id="a6919-265">**Chris Richardson. Tworzenie mikrousług transakcyjnych przy użyciu agregatów, pozyskiwania zdarzeń i CQRS - część 2** </span><span class="sxs-lookup"><span data-stu-id="a6919-265">**Chris Richardson. Developing Transactional Microservices Using Aggregates, Event Sourcing and CQRS - Part 2** </span></span>\
    <https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson>

- <span data-ttu-id="a6919-266">**Chris Richardson. Wzorzec pozyskiwania zdarzeń** </span><span class="sxs-lookup"><span data-stu-id="a6919-266">**Chris Richardson. Event Sourcing pattern** </span></span>\
    <https://microservices.io/patterns/data/event-sourcing.html>

- <span data-ttu-id="a6919-267">**Przedstawiamy pozyskiwanie zdarzeń** </span><span class="sxs-lookup"><span data-stu-id="a6919-267">**Introducing Event Sourcing** </span></span>\
    <https://docs.microsoft.com/previous-versions/msp-n-p/jj591559(v=pandp.10)>

- <span data-ttu-id="a6919-268">**Baza danych Magazynu zdarzeń**.</span><span class="sxs-lookup"><span data-stu-id="a6919-268">**Event Store database**.</span></span> <span data-ttu-id="a6919-269">Oficjalna strona.</span><span class="sxs-lookup"><span data-stu-id="a6919-269">Official site.</span></span> \
    <https://geteventstore.com/>

- <span data-ttu-id="a6919-270">**Patryk Nommensen. Zarządzanie danymi oparte na zdarzeniach dla mikrousług** </span><span class="sxs-lookup"><span data-stu-id="a6919-270">**Patrick Nommensen. Event-Driven Data Management for Microservices** </span></span>\
    <https://dzone.com/articles/event-driven-data-management-for-microservices-1>

- <span data-ttu-id="a6919-271">**The CAP -theorem** </span><span class="sxs-lookup"><span data-stu-id="a6919-271">**The CAP Theorem** </span></span>\
    <https://en.wikipedia.org/wiki/CAP_theorem>

- <span data-ttu-id="a6919-272">**Co to jest roszt CAP?**</span><span class="sxs-lookup"><span data-stu-id="a6919-272">**What is CAP Theorem?**</span></span> \
    <https://www.quora.com/What-Is-CAP-Theorem-1>

- <span data-ttu-id="a6919-273">**Podkład spójności danych** </span><span class="sxs-lookup"><span data-stu-id="a6919-273">**Data Consistency Primer** </span></span>\
    <https://docs.microsoft.com/previous-versions/msp-n-p/dn589800(v=pandp.10)>

- <span data-ttu-id="a6919-274">**Rick Saling. Teoria WPR: Dlaczego "Wszystko jest inne" z chmurą i Internetem** </span><span class="sxs-lookup"><span data-stu-id="a6919-274">**Rick Saling. The CAP Theorem: Why "Everything is Different" with the Cloud and Internet** </span></span>\
    <https://docs.microsoft.com/archive/blogs/rickatmicrosoft/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/>

- <span data-ttu-id="a6919-275">**Eric Brewer. CAP dwanaście lat później: Jak zmieniły się "zasady"** </span><span class="sxs-lookup"><span data-stu-id="a6919-275">**Eric Brewer. CAP Twelve Years Later: How the "Rules" Have Changed** </span></span>\
    <https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed>

- <span data-ttu-id="a6919-276">**Azure Service Bus. Wiadomości brokerskie: wykrywanie duplikatów**  </span><span class="sxs-lookup"><span data-stu-id="a6919-276">**Azure Service Bus. Brokered Messaging: Duplicate Detection**  </span></span>\
    <https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25>

- <span data-ttu-id="a6919-277">**Przewodnik niezawodności** (dokumentacja RabbitMQ) </span><span class="sxs-lookup"><span data-stu-id="a6919-277">**Reliability Guide** (RabbitMQ documentation) </span></span>\
    <https://www.rabbitmq.com/reliability.html#consumer>

> [!div class="step-by-step"]
> <span data-ttu-id="a6919-278">[Poprzedni](rabbitmq-event-bus-development-test-environment.md)
> [następny](test-aspnet-core-services-web-apps.md)</span><span class="sxs-lookup"><span data-stu-id="a6919-278">[Previous](rabbitmq-event-bus-development-test-environment.md)
[Next](test-aspnet-core-services-web-apps.md)</span></span>

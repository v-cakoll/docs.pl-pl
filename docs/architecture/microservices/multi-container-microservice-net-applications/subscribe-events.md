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
# <a name="subscribing-to-events"></a><span data-ttu-id="b0c03-103">Subskrybowanie zdarzeń</span><span class="sxs-lookup"><span data-stu-id="b0c03-103">Subscribing to events</span></span>

<span data-ttu-id="b0c03-104">Pierwszym krokiem do korzystania z magistrali zdarzeń jest subskrybowanie mikrousług do zdarzeń, które mają być odbierane.</span><span class="sxs-lookup"><span data-stu-id="b0c03-104">The first step for using the event bus is to subscribe the microservices to the events they want to receive.</span></span> <span data-ttu-id="b0c03-105">Należy to zrobić w mikrousługach odbiornika.</span><span class="sxs-lookup"><span data-stu-id="b0c03-105">That should be done in the receiver microservices.</span></span>

<span data-ttu-id="b0c03-106">Poniższy prosty kod pokazuje, co każdy mikrousługi odbiornika musi zaimplementować podczas uruchamiania usługi (oznacza to, że w `Startup` klasie), więc subskrybuje zdarzenia, których potrzebuje.</span><span class="sxs-lookup"><span data-stu-id="b0c03-106">The following simple code shows what each receiver microservice needs to implement when starting the service (that is, in the `Startup` class) so it subscribes to the events it needs.</span></span> <span data-ttu-id="b0c03-107">W takim przypadku `basket-api` mikrousługi musi `ProductPriceChangedIntegrationEvent` subskrybować i `OrderStartedIntegrationEvent` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="b0c03-107">In this case, the `basket-api` microservice needs to subscribe to `ProductPriceChangedIntegrationEvent` and the `OrderStartedIntegrationEvent` messages.</span></span>

<span data-ttu-id="b0c03-108">Na przykład podczas subskrybowania `ProductPriceChangedIntegrationEvent` zdarzenia, który sprawia, że mikrousługi koszyka świadomość wszelkich zmian w cenie produktu i pozwala ostrzec użytkownika o zmianie, jeśli ten produkt znajduje się w koszyku użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b0c03-108">For instance, when subscribing to the `ProductPriceChangedIntegrationEvent` event, that makes the basket microservice aware of any changes to the product price and lets it warn the user about the change if that product is in the user’s basket.</span></span>

```csharp
var eventBus = app.ApplicationServices.GetRequiredService<IEventBus>();

eventBus.Subscribe<ProductPriceChangedIntegrationEvent,
                   ProductPriceChangedIntegrationEventHandler>();

eventBus.Subscribe<OrderStartedIntegrationEvent,
                   OrderStartedIntegrationEventHandler>();

```

<span data-ttu-id="b0c03-109">Po uruchomieniu tego kodu mikrousługi subskrybenta będą nasłuchiwane za pośrednictwem kanałów RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="b0c03-109">After this code runs, the subscriber microservice will be listening through RabbitMQ channels.</span></span> <span data-ttu-id="b0c03-110">Po odebraniu dowolnego komunikatu o typie ProductPriceChangedIntegrationEvent, kod wywołuje program obsługi zdarzeń, który jest przekazywany do niego i przetwarza zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="b0c03-110">When any message of type ProductPriceChangedIntegrationEvent arrives, the code invokes the event handler that is passed to it and processes the event.</span></span>

## <a name="publishing-events-through-the-event-bus"></a><span data-ttu-id="b0c03-111">Publikowanie zdarzeń za pośrednictwem magistrali zdarzeń</span><span class="sxs-lookup"><span data-stu-id="b0c03-111">Publishing events through the event bus</span></span>

<span data-ttu-id="b0c03-112">Na koniec nadawca wiadomości (mikrousługi pochodzenia) publikuje zdarzenia integracji z kodem podobnym do poniższego przykładu.</span><span class="sxs-lookup"><span data-stu-id="b0c03-112">Finally, the message sender (origin microservice) publishes the integration events with code similar to the following example.</span></span> <span data-ttu-id="b0c03-113">(Jest to uproszczony przykład, który nie bierze pod uwagę niepodzielności.) Można zaimplementować podobny kod zawsze, gdy zdarzenie musi być propagowane przez wiele mikrousług, zwykle zaraz po zaznananiu danych lub transakcji z mikrousługi pochodzenia.</span><span class="sxs-lookup"><span data-stu-id="b0c03-113">(This is a simplified example that does not take atomicity into account.) You would implement similar code whenever an event must be propagated across multiple microservices, usually right after committing data or transactions from the origin microservice.</span></span>

<span data-ttu-id="b0c03-114">Po pierwsze obiekt implementacji magistrali zdarzeń (na podstawie RabbitMQ lub na podstawie magistrali usług) zostanie wstrzyknięty do konstruktora kontrolera, jak w następującym kodzie:</span><span class="sxs-lookup"><span data-stu-id="b0c03-114">First, the event bus implementation object (based on RabbitMQ or based on a service bus) would be injected at the controller constructor, as in the following code:</span></span>

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

<span data-ttu-id="b0c03-115">Następnie należy go użyć z metod kontrolera, takich jak w UpdateProduct metody:</span><span class="sxs-lookup"><span data-stu-id="b0c03-115">Then you use it from your controller’s methods, like in the UpdateProduct method:</span></span>

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

<span data-ttu-id="b0c03-116">W takim przypadku, ponieważ mikrousługi pochodzenia jest prosta mikrousługa CRUD, ten kod jest umieszczany bezpośrednio do kontrolera interfejsu API sieci Web.</span><span class="sxs-lookup"><span data-stu-id="b0c03-116">In this case, since the origin microservice is a simple CRUD microservice, that code is placed right into a Web API controller.</span></span>

<span data-ttu-id="b0c03-117">W bardziej zaawansowanych mikrousług, takich jak podczas korzystania z cqrs podejścia, można zaimplementować w `CommandHandler` klasie, w ramach `Handle()` metody.</span><span class="sxs-lookup"><span data-stu-id="b0c03-117">In more advanced microservices, like when using CQRS approaches, it can be implemented in the `CommandHandler` class, within the `Handle()` method.</span></span>

### <a name="designing-atomicity-and-resiliency-when-publishing-to-the-event-bus"></a><span data-ttu-id="b0c03-118">Projektowanie niepodzielności i odporności podczas publikowania w magistrali zdarzeń</span><span class="sxs-lookup"><span data-stu-id="b0c03-118">Designing atomicity and resiliency when publishing to the event bus</span></span>

<span data-ttu-id="b0c03-119">Podczas publikowania zdarzeń integracji za pośrednictwem rozproszonego systemu obsługi wiadomości, takich jak magistrala zdarzeń, masz problem z niepodzielnym aktualizowanie oryginalnej bazy danych i publikowanie zdarzenia (oznacza to, że obie operacje ukończone lub żaden z nich).</span><span class="sxs-lookup"><span data-stu-id="b0c03-119">When you publish integration events through a distributed messaging system like your event bus, you have the problem of atomically updating the original database and publishing an event (that is, either both operations complete or none of them).</span></span> <span data-ttu-id="b0c03-120">Na przykład w uproszczonym przykładzie pokazano wcześniej kod zatwierdza dane do bazy danych po zmianie ceny produktu, a następnie publikuje productpricechangedintegrationevent komunikatu.</span><span class="sxs-lookup"><span data-stu-id="b0c03-120">For instance, in the simplified example shown earlier, the code commits data to the database when the product price is changed and then publishes a ProductPriceChangedIntegrationEvent message.</span></span> <span data-ttu-id="b0c03-121">Początkowo może się wydawać istotne, że te dwie operacje są wykonywane niepodzielnie.</span><span class="sxs-lookup"><span data-stu-id="b0c03-121">Initially, it might look essential that these two operations be performed atomically.</span></span> <span data-ttu-id="b0c03-122">Jeśli jednak używasz transakcji rozproszonej obejmującej bazę danych i brokera komunikatów, tak jak w starszych systemach, takich jak [Usługa kolejkowania wiadomości firmy Microsoft (MSMQ),](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx)nie jest to zalecane z powodów opisanych przez [żądanie WPR](https://www.quora.com/What-Is-CAP-Theorem-1).</span><span class="sxs-lookup"><span data-stu-id="b0c03-122">However, if you are using a distributed transaction involving the database and the message broker, as you do in older systems like [Microsoft Message Queuing (MSMQ)](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx), this is not recommended for the reasons described by the [CAP theorem](https://www.quora.com/What-Is-CAP-Theorem-1).</span></span>

<span data-ttu-id="b0c03-123">Zasadniczo używasz mikrousług do tworzenia skalowalnych i wysoce dostępnych systemów.</span><span class="sxs-lookup"><span data-stu-id="b0c03-123">Basically, you use microservices to build scalable and highly available systems.</span></span> <span data-ttu-id="b0c03-124">Upraszczając nieco twierdzenie CAP mówi, że nie można utworzyć (rozproszony) bazy danych (lub mikrousługi, która jest właścicielem modelu), który jest stale dostępny, zdecydowanie spójne *i* tolerancyjny dla dowolnej partycji.</span><span class="sxs-lookup"><span data-stu-id="b0c03-124">Simplifying somewhat, the CAP theorem says that you cannot build a (distributed) database (or a microservice that owns its model) that is continually available, strongly consistent, *and* tolerant to any partition.</span></span> <span data-ttu-id="b0c03-125">Należy wybrać dwie z tych trzech właściwości.</span><span class="sxs-lookup"><span data-stu-id="b0c03-125">You must choose two of these three properties.</span></span>

<span data-ttu-id="b0c03-126">W architekturach opartych na mikrousługach należy wybrać dostępność i tolerancję, a także należy deemphasize silnej spójności.</span><span class="sxs-lookup"><span data-stu-id="b0c03-126">In microservices-based architectures, you should choose availability and tolerance, and you should deemphasize strong consistency.</span></span> <span data-ttu-id="b0c03-127">W związku z tym w większości nowoczesnych aplikacji opartych na mikrousługach zwykle nie chcesz używać transakcji rozproszonych w wiadomościach, tak jak podczas implementowania [transakcji rozproszonych opartych](https://docs.microsoft.com/previous-versions/windows/desktop/ms681205(v=vs.85)) na koordynatorze transakcji rozproszonych systemu Windows (DTC) z [usługą MSMQ](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="b0c03-127">Therefore, in most modern microservice-based applications, you usually do not want to use distributed transactions in messaging, as you do when you implement [distributed transactions](https://docs.microsoft.com/previous-versions/windows/desktop/ms681205(v=vs.85)) based on the Windows Distributed Transaction Coordinator (DTC) with [MSMQ](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx).</span></span>

<span data-ttu-id="b0c03-128">Wróćmy do początkowego problemu i jego przykładu.</span><span class="sxs-lookup"><span data-stu-id="b0c03-128">Let’s go back to the initial issue and its example.</span></span> <span data-ttu-id="b0c03-129">Jeśli usługa ulega awarii po zaktualizowaniu bazy danych (w tym przypadku \_zaraz po wierszu kodu z kontekstem. SaveChangesAsync()), ale przed opublikowaniem zdarzenia integracji ogólny system może stać się niespójny.</span><span class="sxs-lookup"><span data-stu-id="b0c03-129">If the service crashes after the database is updated (in this case, right after the line of code with \_context.SaveChangesAsync()), but before the integration event is published, the overall system could become inconsistent.</span></span> <span data-ttu-id="b0c03-130">Może to mieć kluczowe znaczenie dla firmy, w zależności od konkretnej operacji biznesowej, z którą masz do czynienia.</span><span class="sxs-lookup"><span data-stu-id="b0c03-130">This might be business critical, depending on the specific business operation you are dealing with.</span></span>

<span data-ttu-id="b0c03-131">Jak wspomniano wcześniej w sekcji architektury, można mieć kilka podejść do radzenia sobie z tym problemem:</span><span class="sxs-lookup"><span data-stu-id="b0c03-131">As mentioned earlier in the architecture section, you can have several approaches for dealing with this issue:</span></span>

- <span data-ttu-id="b0c03-132">Korzystanie z pełnego [wzorca pozyskiwania zdarzeń](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing).</span><span class="sxs-lookup"><span data-stu-id="b0c03-132">Using the full [Event Sourcing pattern](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing).</span></span>

- <span data-ttu-id="b0c03-133">Korzystanie z [eksploracji dziennika transakcji](https://www.scoop.it/t/sql-server-transaction-log-mining).</span><span class="sxs-lookup"><span data-stu-id="b0c03-133">Using [transaction log mining](https://www.scoop.it/t/sql-server-transaction-log-mining).</span></span>

- <span data-ttu-id="b0c03-134">Korzystanie ze [wzorca skrzynki nadawczej](https://www.kamilgrzybek.com/design/the-outbox-pattern/).</span><span class="sxs-lookup"><span data-stu-id="b0c03-134">Using the [Outbox pattern](https://www.kamilgrzybek.com/design/the-outbox-pattern/).</span></span> <span data-ttu-id="b0c03-135">Jest to tabela transakcyjna do przechowywania zdarzeń integracji (rozszerzenie transakcji lokalnej).</span><span class="sxs-lookup"><span data-stu-id="b0c03-135">This is a transactional table to store the integration events (extending the local transaction).</span></span>

<span data-ttu-id="b0c03-136">W tym scenariuszu przy użyciu wzorca pełnego pozyskiwania zdarzeń (ES) jest jednym z najlepszych podejść, jeśli *nie* najlepsze.</span><span class="sxs-lookup"><span data-stu-id="b0c03-136">For this scenario, using the full Event Sourcing (ES) pattern is one of the best approaches, if not *the* best.</span></span> <span data-ttu-id="b0c03-137">Jednak w wielu scenariuszach aplikacji może nie być w stanie zaimplementować pełnego systemu ES.</span><span class="sxs-lookup"><span data-stu-id="b0c03-137">However, in many application scenarios, you might not be able to implement a full ES system.</span></span> <span data-ttu-id="b0c03-138">ES oznacza przechowywanie tylko zdarzeń domeny w transakcyjnej bazie danych, zamiast przechowywać bieżące dane o stanie.</span><span class="sxs-lookup"><span data-stu-id="b0c03-138">ES means storing only domain events in your transactional database, instead of storing current state data.</span></span> <span data-ttu-id="b0c03-139">Przechowywanie tylko zdarzeń domeny może mieć ogromne korzyści, takie jak posiadanie dostępnej historii systemu i możliwość określenia stanu systemu w dowolnym momencie w przeszłości.</span><span class="sxs-lookup"><span data-stu-id="b0c03-139">Storing only domain events can have great benefits, such as having the history of your system available and being able to determine the state of your system at any moment in the past.</span></span> <span data-ttu-id="b0c03-140">Jednak wdrożenie pełnego systemu ES wymaga ponownego architekta większości systemu i wprowadzenia wielu innych zawiłości i wymagań.</span><span class="sxs-lookup"><span data-stu-id="b0c03-140">However, implementing a full ES system requires you to rearchitect most of your system and introduces many other complexities and requirements.</span></span> <span data-ttu-id="b0c03-141">Na przykład chcesz użyć bazy danych specjalnie do pozyskiwania zdarzeń, takich jak [Magazyn zdarzeń](https://eventstore.org/), lub bazy danych zorientowanych na dokumenty, takich jak Azure Cosmos DB, MongoDB, Cassandra, CouchDB lub RavenDB.</span><span class="sxs-lookup"><span data-stu-id="b0c03-141">For example, you would want to use a database specifically made for event sourcing, such as [Event Store](https://eventstore.org/), or a document-oriented database such as Azure Cosmos DB, MongoDB, Cassandra, CouchDB, or RavenDB.</span></span> <span data-ttu-id="b0c03-142">ES jest świetnym podejściem do tego problemu, ale nie najłatwiejszym rozwiązaniem, chyba że już znasz pozyskiwanie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b0c03-142">ES is a great approach for this problem, but not the easiest solution unless you are already familiar with event sourcing.</span></span>

<span data-ttu-id="b0c03-143">Opcja użycia eksploracji dziennika transakcji początkowo wygląda bardzo przezroczyste.</span><span class="sxs-lookup"><span data-stu-id="b0c03-143">The option to use transaction log mining initially looks very transparent.</span></span> <span data-ttu-id="b0c03-144">Jednak aby użyć tej metody, mikrousługi musi być sprzęgła z dziennika transakcji RDBMS, takich jak dziennik transakcji programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="b0c03-144">However, to use this approach, the microservice has to be coupled to your RDBMS transaction log, such as the SQL Server transaction log.</span></span> <span data-ttu-id="b0c03-145">Prawdopodobnie nie jest to pożądane.</span><span class="sxs-lookup"><span data-stu-id="b0c03-145">This is probably not desirable.</span></span> <span data-ttu-id="b0c03-146">Inną wadą jest to, że aktualizacje niskiego poziomu zarejestrowane w dzienniku transakcji mogą nie być na tym samym poziomie, co zdarzenia integracji na wysokim poziomie.</span><span class="sxs-lookup"><span data-stu-id="b0c03-146">Another drawback is that the low-level updates recorded in the transaction log might not be at the same level as your high-level integration events.</span></span> <span data-ttu-id="b0c03-147">Jeśli tak, proces inżynierii odwrotnej tych operacji dziennika transakcji może być trudne.</span><span class="sxs-lookup"><span data-stu-id="b0c03-147">If so, the process of reverse-engineering those transaction log operations can be difficult.</span></span>

<span data-ttu-id="b0c03-148">Zrównoważone podejście to połączenie transakcyjnej tabeli bazy danych i uproszczonego wzorca ES.</span><span class="sxs-lookup"><span data-stu-id="b0c03-148">A balanced approach is a mix of a transactional database table and a simplified ES pattern.</span></span> <span data-ttu-id="b0c03-149">Można użyć stanu, takiego jak "gotowy do opublikowania zdarzenia", który można ustawić w oryginalnym zdarzeniu podczas zatwierdzania go do tabeli zdarzeń integracji.</span><span class="sxs-lookup"><span data-stu-id="b0c03-149">You can use a state such as “ready to publish the event,” which you set in the original event when you commit it to the integration events table.</span></span> <span data-ttu-id="b0c03-150">Następnie spróbuj opublikować zdarzenie w magistrali zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b0c03-150">You then try to publish the event to the event bus.</span></span> <span data-ttu-id="b0c03-151">Jeśli akcja publish-event zakończy się powodzeniem, uruchomininną transakcję w usłudze pochodzenia i przeniesiesz stan z "gotowy do opublikowania zdarzenia" na "zdarzenie już opublikowane".</span><span class="sxs-lookup"><span data-stu-id="b0c03-151">If the publish-event action succeeds, you start another transaction in the origin service and move the state from “ready to publish the event” to “event already published.”</span></span>

<span data-ttu-id="b0c03-152">Jeśli akcja publish-event w magistrali zdarzeń nie powiedzie się, dane nadal nie będą niespójne w ramach mikrousługi pochodzenia — nadal jest oznaczony jako "gotowy do opublikowania zdarzenia", a w odniesieniu do pozostałych usług, ostatecznie będzie spójne.</span><span class="sxs-lookup"><span data-stu-id="b0c03-152">If the publish-event action in the event bus fails, the data still will not be inconsistent within the origin microservice—it is still marked as “ready to publish the event,” and with respect to the rest of the services, it will eventually be consistent.</span></span> <span data-ttu-id="b0c03-153">Zawsze można mieć zadania w tle sprawdzanie stanu transakcji lub zdarzeń integracji.</span><span class="sxs-lookup"><span data-stu-id="b0c03-153">You can always have background jobs checking the state of the transactions or integration events.</span></span> <span data-ttu-id="b0c03-154">Jeśli zadanie znajdzie zdarzenie w stanie "gotowy do opublikowania zdarzenia", może spróbować ponownie opublikować to zdarzenie w magistrali zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b0c03-154">If the job finds an event in the “ready to publish the event” state, it can try to republish that event to the event bus.</span></span>

<span data-ttu-id="b0c03-155">Należy zauważyć, że z tej metody są utrwalania tylko zdarzenia integracji dla każdego mikrousługi pochodzenia i tylko zdarzenia, które mają być przekazywane do innych mikrousług lub systemów zewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="b0c03-155">Notice that with this approach, you are persisting only the integration events for each origin microservice, and only the events that you want to communicate to other microservices or external systems.</span></span> <span data-ttu-id="b0c03-156">W przeciwieństwie do tego, w pełnym systemie ES, można przechowywać wszystkie zdarzenia domeny, jak również.</span><span class="sxs-lookup"><span data-stu-id="b0c03-156">In contrast, in a full ES system, you store all domain events as well.</span></span>

<span data-ttu-id="b0c03-157">W związku z tym to zrównoważone podejście jest uproszczonym systemem ES.</span><span class="sxs-lookup"><span data-stu-id="b0c03-157">Therefore, this balanced approach is a simplified ES system.</span></span> <span data-ttu-id="b0c03-158">Potrzebna jest lista zdarzeń integracji z ich bieżącym stanem ("gotowy do opublikowania" w porównaniu z "opublikowanym").</span><span class="sxs-lookup"><span data-stu-id="b0c03-158">You need a list of integration events with their current state (“ready to publish” versus “published”).</span></span> <span data-ttu-id="b0c03-159">Ale wystarczy zaimplementować te stany dla zdarzeń integracji.</span><span class="sxs-lookup"><span data-stu-id="b0c03-159">But you only need to implement these states for the integration events.</span></span> <span data-ttu-id="b0c03-160">W tym podejściu nie trzeba przechowywać wszystkich danych domeny jako zdarzeń w transakcyjnej bazie danych, tak jak w pełnym systemie ES.</span><span class="sxs-lookup"><span data-stu-id="b0c03-160">And in this approach, you do not need to store all your domain data as events in the transactional database, as you would in a full ES system.</span></span>

<span data-ttu-id="b0c03-161">Jeśli używasz już relacyjnej bazy danych, można użyć tabeli transakcyjnej do przechowywania zdarzeń integracji.</span><span class="sxs-lookup"><span data-stu-id="b0c03-161">If you are already using a relational database, you can use a transactional table to store integration events.</span></span> <span data-ttu-id="b0c03-162">Aby osiągnąć niepodzielność w aplikacji, należy użyć procesu dwuetapowego na podstawie transakcji lokalnych.</span><span class="sxs-lookup"><span data-stu-id="b0c03-162">To achieve atomicity in your application, you use a two-step process based on local transactions.</span></span> <span data-ttu-id="b0c03-163">Zasadniczo masz IntegrationEvent tabeli w tej samej bazie danych, gdzie masz jednostek domeny.</span><span class="sxs-lookup"><span data-stu-id="b0c03-163">Basically, you have an IntegrationEvent table in the same database where you have your domain entities.</span></span> <span data-ttu-id="b0c03-164">Ta tabela działa jako ubezpieczenie do osiągnięcia niepodzielności, dzięki czemu należy uwzględnić zdarzenia integracji utrwalione do tych samych transakcji, które zatwierdzają dane domeny.</span><span class="sxs-lookup"><span data-stu-id="b0c03-164">That table works as an insurance for achieving atomicity so that you include persisted integration events into the same transactions that are committing your domain data.</span></span>

<span data-ttu-id="b0c03-165">Krok po kroku proces przebiega następująco:</span><span class="sxs-lookup"><span data-stu-id="b0c03-165">Step by step, the process goes like this:</span></span>

1. <span data-ttu-id="b0c03-166">Aplikacja rozpoczyna transakcję lokalnej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="b0c03-166">The application begins a local database transaction.</span></span>

2. <span data-ttu-id="b0c03-167">Następnie aktualizuje stan jednostek domeny i wstawia zdarzenie do tabeli zdarzeń integracji.</span><span class="sxs-lookup"><span data-stu-id="b0c03-167">It then updates the state of your domain entities and inserts an event into the integration event table.</span></span>

3. <span data-ttu-id="b0c03-168">Na koniec zatwierdza transakcję, dzięki czemu otrzymasz pożądaną niepodzielność, a następnie</span><span class="sxs-lookup"><span data-stu-id="b0c03-168">Finally, it commits the transaction, so you get the desired atomicity and then</span></span>

4. <span data-ttu-id="b0c03-169">Publikujesz wydarzenie w jakiś sposób (dalej).</span><span class="sxs-lookup"><span data-stu-id="b0c03-169">You publish the event somehow (next).</span></span>

<span data-ttu-id="b0c03-170">Podczas wykonywania kroków publikowania zdarzeń, masz następujące opcje:</span><span class="sxs-lookup"><span data-stu-id="b0c03-170">When implementing the steps of publishing the events, you have these choices:</span></span>

- <span data-ttu-id="b0c03-171">Opublikuj zdarzenie integracji zaraz po zazięciu transakcji i użyj innej transakcji lokalnej, aby oznaczyć zdarzenia w tabeli jako publikowane.</span><span class="sxs-lookup"><span data-stu-id="b0c03-171">Publish the integration event right after committing the transaction and use another local transaction to mark the events in the table as being published.</span></span> <span data-ttu-id="b0c03-172">Następnie użyj tabeli tak samo jak artefakt do śledzenia zdarzeń integracji w przypadku problemów w mikrousługach zdalnych i wykonywać akcje kompensacyjne na podstawie przechowywanych zdarzeń integracji.</span><span class="sxs-lookup"><span data-stu-id="b0c03-172">Then, use the table just as an artifact to track the integration events in case of issues in the remote microservices, and perform compensatory actions based on the stored integration events.</span></span>

- <span data-ttu-id="b0c03-173">Użyj tabeli jako rodzaj kolejki.</span><span class="sxs-lookup"><span data-stu-id="b0c03-173">Use the table as a kind of queue.</span></span> <span data-ttu-id="b0c03-174">Oddzielny wątek aplikacji lub proces wysyła zapytanie do tabeli zdarzeń integracji, publikuje zdarzenia w magistrali zdarzeń, a następnie używa transakcji lokalnej do oznaczania zdarzeń jako opublikowanych.</span><span class="sxs-lookup"><span data-stu-id="b0c03-174">A separate application thread or process queries the integration event table, publishes the events to the event bus, and then uses a local transaction to mark the events as published.</span></span>

<span data-ttu-id="b0c03-175">Rysunek 6-22 przedstawia architekturę pierwszego z tych metod.</span><span class="sxs-lookup"><span data-stu-id="b0c03-175">Figure 6-22 shows the architecture for the first of these approaches.</span></span>

![Diagram niepodzielności podczas publikowania bez mikrousługi procesowej.](./media/subscribe-events/atomicity-publish-event-bus.png)

<span data-ttu-id="b0c03-177">**Rysunek 6-22**.</span><span class="sxs-lookup"><span data-stu-id="b0c03-177">**Figure 6-22**.</span></span> <span data-ttu-id="b0c03-178">Niepodzielność podczas publikowania zdarzeń do magistrali zdarzeń</span><span class="sxs-lookup"><span data-stu-id="b0c03-178">Atomicity when publishing events to the event bus</span></span>

<span data-ttu-id="b0c03-179">Podejście przedstawione na rysunku 6-22 brakuje dodatkowej mikrousługi procesu roboczego, który jest odpowiedzialny za sprawdzanie i potwierdzanie sukcesu opublikowanych zdarzeń integracji.</span><span class="sxs-lookup"><span data-stu-id="b0c03-179">The approach illustrated in Figure 6-22 is missing an additional worker microservice that is in charge of checking and confirming the success of the published integration events.</span></span> <span data-ttu-id="b0c03-180">W przypadku awarii, że dodatkowe mikrousługi procesu roboczego sprawdzania może odczytywać zdarzenia z tabeli i ponownie je opublikować, czyli powtórzyć krok numer 2.</span><span class="sxs-lookup"><span data-stu-id="b0c03-180">In case of failure, that additional checker worker microservice can read events from the table and republish them, that is, repeat step number 2.</span></span>

<span data-ttu-id="b0c03-181">O drugim podejściu: używasz EventLog tabeli jako kolejki i zawsze używać mikrousługi roboczego do publikowania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="b0c03-181">About the second approach: you use the EventLog table as a queue and always use a worker microservice to publish the messages.</span></span> <span data-ttu-id="b0c03-182">W takim przypadku proces jest podobny do tego pokazanego na rysunku 6-23.</span><span class="sxs-lookup"><span data-stu-id="b0c03-182">In that case, the process is like that shown in Figure 6-23.</span></span> <span data-ttu-id="b0c03-183">Pokazuje to dodatkowe mikrousługi, a tabela jest pojedynczym źródłem podczas publikowania zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b0c03-183">This shows an additional microservice, and the table is the single source when publishing events.</span></span>

![Diagram niepodzielności podczas publikowania z mikrousług roboczych.](./media/subscribe-events/atomicity-publish-worker-microservice.png)

<span data-ttu-id="b0c03-185">**Rysunek 6-23**.</span><span class="sxs-lookup"><span data-stu-id="b0c03-185">**Figure 6-23**.</span></span> <span data-ttu-id="b0c03-186">Niepodzielność podczas publikowania zdarzeń do magistrali zdarzeń z mikrousługą roboczą</span><span class="sxs-lookup"><span data-stu-id="b0c03-186">Atomicity when publishing events to the event bus with a worker microservice</span></span>

<span data-ttu-id="b0c03-187">Dla uproszczenia eShopOnContainers próbki używa pierwszego podejścia (bez dodatkowych procesów lub mikrousług sprawdzania) oraz magistrali zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b0c03-187">For simplicity, the eShopOnContainers sample uses the first approach (with no additional processes or checker microservices) plus the event bus.</span></span> <span data-ttu-id="b0c03-188">Jednak eShopOnContainers nie obsługuje wszystkich możliwych przypadków awarii.</span><span class="sxs-lookup"><span data-stu-id="b0c03-188">However, the eShopOnContainers is not handling all possible failure cases.</span></span> <span data-ttu-id="b0c03-189">W rzeczywistej aplikacji wdrożonej w chmurze należy objąć fakt, że problemy pojawią się po pewnym czasie i należy zaimplementować tę logikę sprawdzania i ponownego wysyłania.</span><span class="sxs-lookup"><span data-stu-id="b0c03-189">In a real application deployed to the cloud, you must embrace the fact that issues will arise eventually, and you must implement that check and resend logic.</span></span> <span data-ttu-id="b0c03-190">Korzystanie z tabeli jako kolejki może być bardziej efektywne niż pierwsze podejście, jeśli masz tej tabeli jako pojedyncze źródło zdarzeń podczas publikowania ich (z pracownikiem) za pośrednictwem magistrali zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b0c03-190">Using the table as a queue can be more effective than the first approach if you have that table as a single source of events when publishing them (with the worker) through the event bus.</span></span>

### <a name="implementing-atomicity-when-publishing-integration-events-through-the-event-bus"></a><span data-ttu-id="b0c03-191">Implementowanie niepodzielności podczas publikowania zdarzeń integracji za pośrednictwem magistrali zdarzeń</span><span class="sxs-lookup"><span data-stu-id="b0c03-191">Implementing atomicity when publishing integration events through the event bus</span></span>

<span data-ttu-id="b0c03-192">Poniższy kod pokazuje, jak można utworzyć pojedynczą transakcję z udziałem wielu obiektów DbContext — jeden kontekst związany z oryginalnymi danymi, które są aktualizowane, a drugi kontekst związany z tabelą IntegrationEventLog.</span><span class="sxs-lookup"><span data-stu-id="b0c03-192">The following code shows how you can create a single transaction involving multiple DbContext objects—one context related to the original data being updated, and the second context related to the IntegrationEventLog table.</span></span>

<span data-ttu-id="b0c03-193">Należy zauważyć, że transakcja w poniższym kodzie przykładnie nie będzie odporna, jeśli połączenia z bazą danych mają jakikolwiek problem w czasie, gdy kod jest uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="b0c03-193">Note that the transaction in the example code below will not be resilient if connections to the database have any issue at the time when the code is running.</span></span> <span data-ttu-id="b0c03-194">Może się to zdarzyć w systemach opartych na chmurze, takich jak usługa Azure SQL DB, które mogą przenosić bazy danych między serwerami.</span><span class="sxs-lookup"><span data-stu-id="b0c03-194">This can happen in cloud-based systems like Azure SQL DB, which might move databases across servers.</span></span> <span data-ttu-id="b0c03-195">Aby zaimplementowanie transakcji odpornych w wielu kontekstach, zobacz [implementowanie resilient Entity Framework Core SQL connections](../implement-resilient-applications/implement-resilient-entity-framework-core-sql-connections.md) sekcji w dalszej części tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="b0c03-195">For implementing resilient transactions across multiple contexts, see the [Implementing resilient Entity Framework Core SQL connections](../implement-resilient-applications/implement-resilient-entity-framework-core-sql-connections.md) section later in this guide.</span></span>

<span data-ttu-id="b0c03-196">Dla jasności w poniższym przykładzie przedstawiono cały proces w jednym kawałku kodu.</span><span class="sxs-lookup"><span data-stu-id="b0c03-196">For clarity, the following example shows the whole process in a single piece of code.</span></span> <span data-ttu-id="b0c03-197">Jednak implementacja eShopOnContainers jest faktycznie refaktoryzacji i podzielić tę logikę na wiele klas, dzięki czemu jest łatwiejsze do utrzymania.</span><span class="sxs-lookup"><span data-stu-id="b0c03-197">However, the eShopOnContainers implementation is actually refactored and split this logic into multiple classes so it is easier to maintain.</span></span>

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

<span data-ttu-id="b0c03-198">Po productpricechangedintegrationevent zdarzenie integracji jest tworzony, transakcja, która przechowuje oryginalną operację domeny (zaktualizować element katalogu) zawiera również trwałość zdarzenia w tabeli EventLog.</span><span class="sxs-lookup"><span data-stu-id="b0c03-198">After the ProductPriceChangedIntegrationEvent integration event is created, the transaction that stores the original domain operation (update the catalog item) also includes the persistence of the event in the EventLog table.</span></span> <span data-ttu-id="b0c03-199">To sprawia, że pojedyncza transakcja i zawsze będzie można sprawdzić, czy wiadomości zdarzenia zostały wysłane.</span><span class="sxs-lookup"><span data-stu-id="b0c03-199">This makes it a single transaction, and you will always be able to check whether event messages were sent.</span></span>

<span data-ttu-id="b0c03-200">Tabela dziennika zdarzeń jest aktualizowana niepodzielnie przy użyciu oryginalnej operacji bazy danych przy użyciu transakcji lokalnej względem tej samej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="b0c03-200">The event log table is updated atomically with the original database operation, using a local transaction against the same database.</span></span> <span data-ttu-id="b0c03-201">Jeśli którakolwiek z operacji nie powiedzie się, wyjątek i transakcja wycofuje wszystkie zakończone operacji, zachowując spójność między operacjami domeny i komunikatów zdarzenia zapisanych w tabeli.</span><span class="sxs-lookup"><span data-stu-id="b0c03-201">If any of the operations fail, an exception is thrown and the transaction rolls back any completed operation, thus maintaining consistency between the domain operations and the event messages saved to the table.</span></span>

### <a name="receiving-messages-from-subscriptions-event-handlers-in-receiver-microservices"></a><span data-ttu-id="b0c03-202">Odbieranie komunikatów z subskrypcji: programy obsługi zdarzeń w mikrousługach odbiornika</span><span class="sxs-lookup"><span data-stu-id="b0c03-202">Receiving messages from subscriptions: event handlers in receiver microservices</span></span>

<span data-ttu-id="b0c03-203">Oprócz logiki subskrypcji zdarzeń należy zaimplementować wewnętrzny kod dla programów obsługi zdarzeń integracji (jak metoda wywołania wywołania.</span><span class="sxs-lookup"><span data-stu-id="b0c03-203">In addition to the event subscription logic, you need to implement the internal code for the integration event handlers (like a callback method).</span></span> <span data-ttu-id="b0c03-204">Program obsługi zdarzeń jest, gdzie można określić, gdzie będą odbierane i przetwarzane komunikaty o zdarzeniach określonego typu.</span><span class="sxs-lookup"><span data-stu-id="b0c03-204">The event handler is where you specify where the event messages of a certain type will be received and processed.</span></span>

<span data-ttu-id="b0c03-205">Program obsługi zdarzeń najpierw odbiera wystąpienie zdarzenia z magistrali zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b0c03-205">An event handler first receives an event instance from the event bus.</span></span> <span data-ttu-id="b0c03-206">Następnie lokalizuje składnik, który ma być przetwarzany związane z tym zdarzeniem integracji, propagacji i utrwalania zdarzenia jako zmiany stanu w mikrousługi odbiornika.</span><span class="sxs-lookup"><span data-stu-id="b0c03-206">Then it locates the component to be processed related to that integration event, propagating and persisting the event as a change in state in the receiver microservice.</span></span> <span data-ttu-id="b0c03-207">Na przykład jeśli ProductPriceChanged zdarzenie pochodzi z mikrousługi katalogu, jest obsługiwany w mikrousługi koszyka i zmienia stan w tym mikrousługi koszyka odbiornika, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="b0c03-207">For example, if a ProductPriceChanged event originates in the catalog microservice, it is handled in the basket microservice and changes the state in this receiver basket microservice as well, as shown in the following code.</span></span>

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

<span data-ttu-id="b0c03-208">Program obsługi zdarzeń musi sprawdzić, czy produkt istnieje w dowolnym z wystąpień koszyka.</span><span class="sxs-lookup"><span data-stu-id="b0c03-208">The event handler needs to verify whether the product exists in any of the basket instances.</span></span> <span data-ttu-id="b0c03-209">Aktualizuje również cenę towaru dla każdego powiązanego elementu zamówienia koszyka.</span><span class="sxs-lookup"><span data-stu-id="b0c03-209">It also updates the item price for each related basket line item.</span></span> <span data-ttu-id="b0c03-210">Na koniec tworzy alert, który ma być wyświetlany użytkownikowi o zmianie ceny, jak pokazano na rysunku 6-24.</span><span class="sxs-lookup"><span data-stu-id="b0c03-210">Finally, it creates an alert to be displayed to the user about the price change, as shown in Figure 6-24.</span></span>

![Zrzut ekranu przedstawiający przeglądarkę z powiadomieniem o zmianie ceny w koszyku użytkownika.](./media/subscribe-events/display-item-price-change.png)

<span data-ttu-id="b0c03-212">**Rysunek 6-24**.</span><span class="sxs-lookup"><span data-stu-id="b0c03-212">**Figure 6-24**.</span></span> <span data-ttu-id="b0c03-213">Wyświetlanie zmiany ceny towaru w koszyku, o tym, co jest przekazywane przez zdarzenia integracji</span><span class="sxs-lookup"><span data-stu-id="b0c03-213">Displaying an item price change in a basket, as communicated by integration events</span></span>

## <a name="idempotency-in-update-message-events"></a><span data-ttu-id="b0c03-214">Idempotencja w zdarzeniach wiadomości aktualizacji</span><span class="sxs-lookup"><span data-stu-id="b0c03-214">Idempotency in update message events</span></span>

<span data-ttu-id="b0c03-215">Ważnym aspektem zdarzenia komunikatu aktualizacji jest, że błąd w dowolnym momencie w komunikacji powinien spowodować wiadomość do ponowienia próby.</span><span class="sxs-lookup"><span data-stu-id="b0c03-215">An important aspect of update message events is that a failure at any point in the communication should cause the message to be retried.</span></span> <span data-ttu-id="b0c03-216">W przeciwnym razie zadanie w tle może próbować opublikować zdarzenie, które zostało już opublikowane, tworząc stan wyścigu.</span><span class="sxs-lookup"><span data-stu-id="b0c03-216">Otherwise a background task might try to publish an event that has already been published, creating a race condition.</span></span> <span data-ttu-id="b0c03-217">Należy upewnić się, że aktualizacje są idempotentności lub że dostarczają one wystarczających informacji, aby upewnić się, że można wykryć duplikat, odrzucić go i odesłać tylko jedną odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="b0c03-217">You need to make sure that the updates are either idempotent or that they provide enough information to ensure that you can detect a duplicate, discard it, and send back only one response.</span></span>

<span data-ttu-id="b0c03-218">Jak wspomniano wcześniej, idempotencja oznacza, że operacja może być wykonywana wiele razy bez zmiany wyniku.</span><span class="sxs-lookup"><span data-stu-id="b0c03-218">As noted earlier, idempotency means that an operation can be performed multiple times without changing the result.</span></span> <span data-ttu-id="b0c03-219">W środowisku obsługi wiadomości, jak podczas przekazywania zdarzeń, zdarzenie jest idempotentności, jeśli może być dostarczane wiele razy bez zmiany wyniku dla mikrousługi odbiornika.</span><span class="sxs-lookup"><span data-stu-id="b0c03-219">In a messaging environment, as when communicating events, an event is idempotent if it can be delivered multiple times without changing the result for the receiver microservice.</span></span> <span data-ttu-id="b0c03-220">Może to być konieczne ze względu na charakter samego zdarzenia lub ze względu na sposób, w jaki system obsługuje zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="b0c03-220">This may be necessary because of the nature of the event itself, or because of the way the system handles the event.</span></span> <span data-ttu-id="b0c03-221">Idempotencja wiadomości jest ważna w każdej aplikacji, która używa obsługi wiadomości, a nie tylko w aplikacjach implementujących wzorzec magistrali zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b0c03-221">Message idempotency is important in any application that uses messaging, not just in applications that implement the event bus pattern.</span></span>

<span data-ttu-id="b0c03-222">Przykładem operacji idempotentności jest instrukcja SQL, która wstawia dane do tabeli tylko wtedy, gdy dane te nie są jeszcze w tabeli.</span><span class="sxs-lookup"><span data-stu-id="b0c03-222">An example of an idempotent operation is a SQL statement that inserts data into a table only if that data is not already in the table.</span></span> <span data-ttu-id="b0c03-223">Nie ma znaczenia, ile razy uruchamiasz tę instrukcję Wstawić SQL; wynik będzie taki sam — tabela będzie zawierać te dane.</span><span class="sxs-lookup"><span data-stu-id="b0c03-223">It does not matter how many times you run that insert SQL statement; the result will be the same—the table will contain that data.</span></span> <span data-ttu-id="b0c03-224">Idempotencja jak to może być również konieczne w przypadku do czynienia z wiadomościami, jeśli wiadomości mogą być potencjalnie wysyłane i dlatego przetwarzane więcej niż jeden raz.</span><span class="sxs-lookup"><span data-stu-id="b0c03-224">Idempotency like this can also be necessary when dealing with messages if the messages could potentially be sent and therefore processed more than once.</span></span> <span data-ttu-id="b0c03-225">Na przykład jeśli logika ponawiania powoduje, że nadawca wysłać dokładnie tę samą wiadomość więcej niż jeden raz, należy upewnić się, że jest idempotentności.</span><span class="sxs-lookup"><span data-stu-id="b0c03-225">For instance, if retry logic causes a sender to send exactly the same message more than once, you need to make sure that it is idempotent.</span></span>

<span data-ttu-id="b0c03-226">Możliwe jest projektowanie wiadomości idempotentności.</span><span class="sxs-lookup"><span data-stu-id="b0c03-226">It is possible to design idempotent messages.</span></span> <span data-ttu-id="b0c03-227">Możesz na przykład utworzyć zdarzenie z napisem "ustaw cenę produktu na 25 USD" zamiast "dodaj 5 USD do ceny produktu".</span><span class="sxs-lookup"><span data-stu-id="b0c03-227">For example, you can create an event that says "set the product price to $25" instead of "add $5 to the product price."</span></span> <span data-ttu-id="b0c03-228">Możesz bezpiecznie przetworzyć pierwszą wiadomość dowolną liczbę razy, a wynik będzie taki sam.</span><span class="sxs-lookup"><span data-stu-id="b0c03-228">You could safely process the first message any number of times and the result will be the same.</span></span> <span data-ttu-id="b0c03-229">Nie dotyczy to drugiego komunikatu.</span><span class="sxs-lookup"><span data-stu-id="b0c03-229">That is not true for the second message.</span></span> <span data-ttu-id="b0c03-230">Ale nawet w pierwszym przypadku możesz nie chcieć przetworzyć pierwszego zdarzenia, ponieważ system mógł również wysłać nowsze zdarzenie zmiany cen i będziesz nadpisywać nową cenę.</span><span class="sxs-lookup"><span data-stu-id="b0c03-230">But even in the first case, you might not want to process the first event, because the system could also have sent a newer price-change event and you would be overwriting the new price.</span></span>

<span data-ttu-id="b0c03-231">Innym przykładem może być zdarzenie zakończone zamówienie jest propagowane do wielu subskrybentów.</span><span class="sxs-lookup"><span data-stu-id="b0c03-231">Another example might be an order-completed event being propagated to multiple subscribers.</span></span> <span data-ttu-id="b0c03-232">Ważne jest, aby informacje o zamówieniu były aktualizowane w innych systemach tylko raz, nawet jeśli istnieją zduplikowane zdarzenia wiadomości dla tego samego zdarzenia zakończonego zamówieniem.</span><span class="sxs-lookup"><span data-stu-id="b0c03-232">It is important that order information be updated in other systems just once, even if there are duplicated message events for the same order-completed event.</span></span>

<span data-ttu-id="b0c03-233">Jest wygodne mieć pewnego rodzaju tożsamości na zdarzenie, dzięki czemu można utworzyć logikę, która wymusza, że każde zdarzenie jest przetwarzane tylko raz na odbiorcę.</span><span class="sxs-lookup"><span data-stu-id="b0c03-233">It is convenient to have some kind of identity per event so that you can create logic that enforces that each event is processed only once per receiver.</span></span>

<span data-ttu-id="b0c03-234">Niektóre przetwarzanie wiadomości jest z natury idempotentności.</span><span class="sxs-lookup"><span data-stu-id="b0c03-234">Some message processing is inherently idempotent.</span></span> <span data-ttu-id="b0c03-235">Na przykład jeśli system generuje miniatury obrazów, może nie mieć znaczenia, ile razy wiadomość o wygenerowanej miniaturze jest przetwarzana; wynik jest, że miniatury są generowane i są takie same za każdym razem.</span><span class="sxs-lookup"><span data-stu-id="b0c03-235">For example, if a system generates image thumbnails, it might not matter how many times the message about the generated thumbnail is processed; the outcome is that the thumbnails are generated and they are the same every time.</span></span> <span data-ttu-id="b0c03-236">Z drugiej strony, operacje, takie jak wywołanie bramki płatniczej w celu obciążenia karty kredytowej, mogą nie być w ogóle idempotentnością.</span><span class="sxs-lookup"><span data-stu-id="b0c03-236">On the other hand, operations such as calling a payment gateway to charge a credit card may not be idempotent at all.</span></span> <span data-ttu-id="b0c03-237">W takich przypadkach należy upewnić się, że przetwarzanie wiadomości wiele razy ma wpływ, który można oczekiwać.</span><span class="sxs-lookup"><span data-stu-id="b0c03-237">In these cases, you need to ensure that processing a message multiple times has the effect that you expect.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="b0c03-238">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="b0c03-238">Additional resources</span></span>

- <span data-ttu-id="b0c03-239">**Honorowanie idempotency wiadomości** </span><span class="sxs-lookup"><span data-stu-id="b0c03-239">**Honoring message idempotency** </span></span>\
  <https://docs.microsoft.com/previous-versions/msp-n-p/jj591565(v=pandp.10)#honoring-message-idempotency>

## <a name="deduplicating-integration-event-messages"></a><span data-ttu-id="b0c03-240">Deduplicating komunikaty zdarzeń integracji</span><span class="sxs-lookup"><span data-stu-id="b0c03-240">Deduplicating integration event messages</span></span>

<span data-ttu-id="b0c03-241">Można upewnić się, że zdarzenia wiadomości są wysyłane i przetwarzane tylko raz na subskrybenta na różnych poziomach.</span><span class="sxs-lookup"><span data-stu-id="b0c03-241">You can make sure that message events are sent and processed just once per subscriber at different levels.</span></span> <span data-ttu-id="b0c03-242">Jednym ze sposobów jest użycie funkcji deduplikacji oferowanej przez używaną infrastrukturę obsługi wiadomości.</span><span class="sxs-lookup"><span data-stu-id="b0c03-242">One way is to use a deduplication feature offered by the messaging infrastructure you are using.</span></span> <span data-ttu-id="b0c03-243">Innym jest zaimplementowanie logiki niestandardowej w mikrousługi docelowej.</span><span class="sxs-lookup"><span data-stu-id="b0c03-243">Another is to implement custom logic in your destination microservice.</span></span> <span data-ttu-id="b0c03-244">Posiadanie walidacji zarówno na poziomie transportu, jak i aplikacji jest najlepszym rozwiązaniem.</span><span class="sxs-lookup"><span data-stu-id="b0c03-244">Having validations at both the transport level and the application level is your best bet.</span></span>

### <a name="deduplicating-message-events-at-the-eventhandler-level"></a><span data-ttu-id="b0c03-245">Deduplicating zdarzenia wiadomości na poziomie EventHandler</span><span class="sxs-lookup"><span data-stu-id="b0c03-245">Deduplicating message events at the EventHandler level</span></span>

<span data-ttu-id="b0c03-246">Jednym ze sposobów, aby upewnić się, że zdarzenie jest przetwarzane tylko raz przez dowolnego odbiorcy jest implementowanie niektórych logiki podczas przetwarzania zdarzeń komunikatu w programach obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="b0c03-246">One way to make sure that an event is processed just once by any receiver is by implementing certain logic when processing the message events in event handlers.</span></span> <span data-ttu-id="b0c03-247">Na przykład jest to podejście używane w aplikacji eShopOnContainers, jak widać w [kodzie źródłowym UserCheckoutAcceptedIntegrationEventHandler klasy](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) po odebraniu UserCheckoutAcceptedIntegrationEvent zdarzenia integracji.</span><span class="sxs-lookup"><span data-stu-id="b0c03-247">For example, that is the approach used in the eShopOnContainers application, as you can see in the [source code of the UserCheckoutAcceptedIntegrationEventHandler class](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) when it receives an UserCheckoutAcceptedIntegrationEvent integration event.</span></span> <span data-ttu-id="b0c03-248">(W tym przypadku zawijamy CreateOrderCommand z IdentifiedCommand, przy użyciu eventMsg.RequestId jako identyfikator, przed wysłaniem go do programu obsługi poleceń).</span><span class="sxs-lookup"><span data-stu-id="b0c03-248">(In this case we wrap the CreateOrderCommand with an IdentifiedCommand, using the eventMsg.RequestId as an identifier, before sending it to the command handler).</span></span>

### <a name="deduplicating-messages-when-using-rabbitmq"></a><span data-ttu-id="b0c03-249">Deduplicating wiadomości podczas korzystania RabbitMQ</span><span class="sxs-lookup"><span data-stu-id="b0c03-249">Deduplicating messages when using RabbitMQ</span></span>

<span data-ttu-id="b0c03-250">Po awarii sieci przerywanej wystąpić, wiadomości mogą być duplikowane, a odbiornik wiadomości musi być gotowy do obsługi tych zduplikowanych wiadomości.</span><span class="sxs-lookup"><span data-stu-id="b0c03-250">When intermittent network failures happen, messages can be duplicated, and the message receiver must be ready to handle these duplicated messages.</span></span> <span data-ttu-id="b0c03-251">Jeśli to możliwe, odbiorcy powinni obsługiwać wiadomości w sposób idempotentny, co jest lepsze niż jawne obchodzenie się z nimi z deduplikacją.</span><span class="sxs-lookup"><span data-stu-id="b0c03-251">If possible, receivers should handle messages in an idempotent way, which is better than explicitly handling them with deduplication.</span></span>

<span data-ttu-id="b0c03-252">Zgodnie z [dokumentacją RabbitMQ](https://www.rabbitmq.com/reliability.html#consumer), "Jeśli wiadomość jest dostarczana do konsumenta, a następnie ponownie w kolejce (ponieważ nie został potwierdzony przed połączenie konsumenta spadła, na przykład), a następnie RabbitMQ ustawi ponownie dostarczone flagi na nim, gdy jest dostarczany ponownie (czy do tego samego konsumenta lub innego).</span><span class="sxs-lookup"><span data-stu-id="b0c03-252">According to the [RabbitMQ documentation](https://www.rabbitmq.com/reliability.html#consumer), “If a message is delivered to a consumer and then requeued (because it was not acknowledged before the consumer connection dropped, for example) then RabbitMQ will set the redelivered flag on it when it is delivered again (whether to the same consumer or a different one).</span></span>

<span data-ttu-id="b0c03-253">Jeśli flaga "redelivered" jest ustawiona, odbiorca musi wziąć to pod uwagę, ponieważ wiadomość mogła już zostać przetworzona.</span><span class="sxs-lookup"><span data-stu-id="b0c03-253">If the “redelivered” flag is set, the receiver must take that into account, because the message might already have been processed.</span></span> <span data-ttu-id="b0c03-254">Ale to nie jest gwarantowane; wiadomość może nigdy nie dotarły do odbiorcy po opuszczeniu brokera komunikatów, być może z powodu problemów z siecią.</span><span class="sxs-lookup"><span data-stu-id="b0c03-254">But that is not guaranteed; the message might never have reached the receiver after it left the message broker, perhaps because of network issues.</span></span> <span data-ttu-id="b0c03-255">Z drugiej strony, jeśli flaga "ponownie dostarczona" nie jest ustawiona, gwarantuje się, że wiadomość nie została wysłana więcej niż jeden raz.</span><span class="sxs-lookup"><span data-stu-id="b0c03-255">On the other hand, if the “redelivered” flag is not set, it is guaranteed that the message has not been sent more than once.</span></span> <span data-ttu-id="b0c03-256">W związku z tym odbiornik musi deduplikować wiadomości lub przetwarzać wiadomości w sposób idempotentny tylko wtedy, gdy flaga "dostarczone ponownie" jest ustawiona w wiadomości.</span><span class="sxs-lookup"><span data-stu-id="b0c03-256">Therefore, the receiver needs to deduplicate messages or process messages in an idempotent way only if the “redelivered” flag is set in the message.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="b0c03-257">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="b0c03-257">Additional resources</span></span>

- <span data-ttu-id="b0c03-258">**Forked eShopOnContainers przy użyciu NServiceBus (oprogramowanie szczególne)** </span><span class="sxs-lookup"><span data-stu-id="b0c03-258">**Forked eShopOnContainers using NServiceBus (Particular Software)** </span></span>\
    <https://go.particular.net/eShopOnContainers>

- <span data-ttu-id="b0c03-259">**Wiadomości oparte na zdarzeniach** </span><span class="sxs-lookup"><span data-stu-id="b0c03-259">**Event Driven Messaging** </span></span>\
    <https://patterns.arcitura.com/soa-patterns/design_patterns/event_driven_messaging>

- <span data-ttu-id="b0c03-260">**Jimmy Bogard. Refaktoryzacja w kierunku odporności: ocena sprzężenia** </span><span class="sxs-lookup"><span data-stu-id="b0c03-260">**Jimmy Bogard. Refactoring Towards Resilience: Evaluating Coupling** </span></span>\
    <https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/>

- <span data-ttu-id="b0c03-261">**Kanał publikowania i subskrybowania** </span><span class="sxs-lookup"><span data-stu-id="b0c03-261">**Publish-Subscribe channel** </span></span>\
    <https://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html>

- <span data-ttu-id="b0c03-262">**Komunikowanie się między kontekstami ograniczonymi** </span><span class="sxs-lookup"><span data-stu-id="b0c03-262">**Communicating Between Bounded Contexts** </span></span>\
    <https://docs.microsoft.com/previous-versions/msp-n-p/jj591572(v=pandp.10)>

- <span data-ttu-id="b0c03-263">**Spójność ostateczna** </span><span class="sxs-lookup"><span data-stu-id="b0c03-263">**Eventual Consistency** </span></span>\
    <https://en.wikipedia.org/wiki/Eventual_consistency>

- <span data-ttu-id="b0c03-264">**Philip Brown. Strategie integracji ograniczonych kontekstów** </span><span class="sxs-lookup"><span data-stu-id="b0c03-264">**Philip Brown. Strategies for Integrating Bounded Contexts** </span></span>\
    <https://www.culttt.com/2014/11/26/strategies-integrating-bounded-contexts/>

- <span data-ttu-id="b0c03-265">**Chris Richardson. Tworzenie mikrousług transakcyjnych przy użyciu agregacji, pozyskiwania zdarzeń i CQRS — część 2** </span><span class="sxs-lookup"><span data-stu-id="b0c03-265">**Chris Richardson. Developing Transactional Microservices Using Aggregates, Event Sourcing and CQRS - Part 2** </span></span>\
    <https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson>

- <span data-ttu-id="b0c03-266">**Chris Richardson. Wzorzec pozyskiwania zdarzeń** </span><span class="sxs-lookup"><span data-stu-id="b0c03-266">**Chris Richardson. Event Sourcing pattern** </span></span>\
    <https://microservices.io/patterns/data/event-sourcing.html>

- <span data-ttu-id="b0c03-267">**Przedstawiamy pozyskiwanie zdarzeń** </span><span class="sxs-lookup"><span data-stu-id="b0c03-267">**Introducing Event Sourcing** </span></span>\
    <https://docs.microsoft.com/previous-versions/msp-n-p/jj591559(v=pandp.10)>

- <span data-ttu-id="b0c03-268">**Baza danych Magazynu zdarzeń**.</span><span class="sxs-lookup"><span data-stu-id="b0c03-268">**Event Store database**.</span></span> <span data-ttu-id="b0c03-269">Oficjalna strona internetowa.</span><span class="sxs-lookup"><span data-stu-id="b0c03-269">Official site.</span></span> \
    <https://geteventstore.com/>

- <span data-ttu-id="b0c03-270">**Patrick Nommensen. Zarządzanie danymi opartymi na zdarzeniach dla mikrousług** </span><span class="sxs-lookup"><span data-stu-id="b0c03-270">**Patrick Nommensen. Event-Driven Data Management for Microservices** </span></span>\
    <https://dzone.com/articles/event-driven-data-management-for-microservices-1>

- <span data-ttu-id="b0c03-271">**Wpr Theorem** </span><span class="sxs-lookup"><span data-stu-id="b0c03-271">**The CAP Theorem** </span></span>\
    <https://en.wikipedia.org/wiki/CAP_theorem>

- <span data-ttu-id="b0c03-272">**Czym jest wpr?**</span><span class="sxs-lookup"><span data-stu-id="b0c03-272">**What is CAP Theorem?**</span></span> \
    <https://www.quora.com/What-Is-CAP-Theorem-1>

- <span data-ttu-id="b0c03-273">**Podkład spójności danych** </span><span class="sxs-lookup"><span data-stu-id="b0c03-273">**Data Consistency Primer** </span></span>\
    <https://docs.microsoft.com/previous-versions/msp-n-p/dn589800(v=pandp.10)>

- <span data-ttu-id="b0c03-274">**Rick Saling. Theorem WPR: Dlaczego "Wszystko jest inne" z chmurą i Internetem** </span><span class="sxs-lookup"><span data-stu-id="b0c03-274">**Rick Saling. The CAP Theorem: Why “Everything is Different” with the Cloud and Internet** </span></span>\
    <https://docs.microsoft.com/archive/blogs/rickatmicrosoft/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/>

- <span data-ttu-id="b0c03-275">**Eric Brewer. WPR dwanaście lat później: Jak zmieniły się "zasady"** </span><span class="sxs-lookup"><span data-stu-id="b0c03-275">**Eric Brewer. CAP Twelve Years Later: How the "Rules" Have Changed** </span></span>\
    <https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed>

- <span data-ttu-id="b0c03-276">**Azure Service Bus. Usługi pośrednictwa w komunikacji: wykrywanie duplikatów**  </span><span class="sxs-lookup"><span data-stu-id="b0c03-276">**Azure Service Bus. Brokered Messaging: Duplicate Detection**  </span></span>\
    <https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25>

- <span data-ttu-id="b0c03-277">**Przewodnik niezawodności** (dokumentacja RabbitMQ) </span><span class="sxs-lookup"><span data-stu-id="b0c03-277">**Reliability Guide** (RabbitMQ documentation) </span></span>\
    <https://www.rabbitmq.com/reliability.html#consumer>

> [!div class="step-by-step"]
> <span data-ttu-id="b0c03-278">[Poprzedni](rabbitmq-event-bus-development-test-environment.md)
> [następny](test-aspnet-core-services-web-apps.md)</span><span class="sxs-lookup"><span data-stu-id="b0c03-278">[Previous](rabbitmq-event-bus-development-test-environment.md)
[Next](test-aspnet-core-services-web-apps.md)</span></span>

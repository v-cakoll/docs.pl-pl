---
title: Subskrybowanie zdarzeń
description: Architektura mikrousług platformy .NET dla aplikacji platformy .NET w kontenerze | Zapoznaj się ze szczegółami dotyczącymi publikowania i subskrypcji zdarzeń integracji.
ms.date: 10/02/2018
ms.openlocfilehash: ac9715c7c282be845e1e47516d06945c31f70209
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71039780"
---
# <a name="subscribing-to-events"></a><span data-ttu-id="69c17-103">Subskrybowanie zdarzeń</span><span class="sxs-lookup"><span data-stu-id="69c17-103">Subscribing to events</span></span>

<span data-ttu-id="69c17-104">Pierwszym krokiem przy korzystaniu z magistrali zdarzeń jest subskrybowanie mikrousług do zdarzeń, które chcą odebrać.</span><span class="sxs-lookup"><span data-stu-id="69c17-104">The first step for using the event bus is to subscribe the microservices to the events they want to receive.</span></span> <span data-ttu-id="69c17-105">Należy to zrobić w mikrousługach odbiornika.</span><span class="sxs-lookup"><span data-stu-id="69c17-105">That should be done in the receiver microservices.</span></span>

<span data-ttu-id="69c17-106">Poniższy prosty kod przedstawia, co każda mikrousługa odbiornika musi zaimplementować podczas uruchamiania usługi (czyli w `Startup` klasie), więc subskrybuje potrzebne zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="69c17-106">The following simple code shows what each receiver microservice needs to implement when starting the service (that is, in the `Startup` class) so it subscribes to the events it needs.</span></span> <span data-ttu-id="69c17-107">W takim przypadku `basket.api` mikrousługa musi `ProductPriceChangedIntegrationEvent` subskrybować i `OrderStartedIntegrationEvent` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="69c17-107">In this case, the `basket.api` microservice needs to subscribe to `ProductPriceChangedIntegrationEvent` and the `OrderStartedIntegrationEvent` messages.</span></span>

<span data-ttu-id="69c17-108">Na przykład podczas subskrybowania `ProductPriceChangedIntegrationEvent` zdarzenia, dzięki czemu usługa koszyka wie o wszelkich zmianach w cenie produktu i pozwala mu ostrzec użytkownika o zmianie, jeśli ten produkt znajduje się w koszyku użytkownika.</span><span class="sxs-lookup"><span data-stu-id="69c17-108">For instance, when subscribing to the `ProductPriceChangedIntegrationEvent` event, that makes the basket microservice aware of any changes to the product price and lets it warn the user about the change if that product is in the user’s basket.</span></span>

```csharp
var eventBus = app.ApplicationServices.GetRequiredService<IEventBus>();

eventBus.Subscribe<ProductPriceChangedIntegrationEvent,
                   ProductPriceChangedIntegrationEventHandler>();

eventBus.Subscribe<OrderStartedIntegrationEvent,
                   OrderStartedIntegrationEventHandler>();

```

<span data-ttu-id="69c17-109">Po uruchomieniu tego kodu, mikrousługa subskrybenta będzie nasłuchiwać kanałów RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="69c17-109">After this code runs, the subscriber microservice will be listening through RabbitMQ channels.</span></span> <span data-ttu-id="69c17-110">Po nadejściu dowolnych komunikatów typu ProductPriceChangedIntegrationEvent kod wywołuje program obsługi zdarzeń, który jest do niego przeszedł, i przetwarza zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="69c17-110">When any message of type ProductPriceChangedIntegrationEvent arrives, the code invokes the event handler that is passed to it and processes the event.</span></span>

## <a name="publishing-events-through-the-event-bus"></a><span data-ttu-id="69c17-111">Publikowanie zdarzeń za pomocą magistrali zdarzeń</span><span class="sxs-lookup"><span data-stu-id="69c17-111">Publishing events through the event bus</span></span>

<span data-ttu-id="69c17-112">Na koniec wiadomość nadawcy (mikrousługa pochodzenia) publikuje zdarzenia integracji z kodem podobnym do poniższego przykładu.</span><span class="sxs-lookup"><span data-stu-id="69c17-112">Finally, the message sender (origin microservice) publishes the integration events with code similar to the following example.</span></span> <span data-ttu-id="69c17-113">(Jest to uproszczony przykład, który nie wymaga niepodzielności na konto). Należy zaimplementować podobny kod za każdym razem, gdy zdarzenie musi być propagowane dla wielu mikrousług, zwykle bezpośrednio po zatwierdzeniu danych lub transakcji z mikrousługi źródłowej.</span><span class="sxs-lookup"><span data-stu-id="69c17-113">(This is a simplified example that does not take atomicity into account.) You would implement similar code whenever an event must be propagated across multiple microservices, usually right after committing data or transactions from the origin microservice.</span></span>

<span data-ttu-id="69c17-114">Najpierw obiekt implementacji usługi Event Bus (oparty na RabbitMQ lub na podstawie usługi Service Bus) zostałby dodany do konstruktora kontrolera, jak w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="69c17-114">First, the event bus implementation object (based on RabbitMQ or based on a service bus) would be injected at the controller constructor, as in the following code:</span></span>

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

<span data-ttu-id="69c17-115">Następnie należy użyć jej z metod na kontrolerze, takich jak w metodzie UpdateProduct:</span><span class="sxs-lookup"><span data-stu-id="69c17-115">Then you use it from your controller’s methods, like in the UpdateProduct method:</span></span>

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

<span data-ttu-id="69c17-116">W takim przypadku, ponieważ mikrousługa jest prostą CRUD, ten kod jest umieszczany bezpośrednio w kontrolerze interfejsu API sieci Web.</span><span class="sxs-lookup"><span data-stu-id="69c17-116">In this case, since the origin microservice is a simple CRUD microservice, that code is placed right into a Web API controller.</span></span>

<span data-ttu-id="69c17-117">W bardziej zaawansowanych mikrousługach, takich jak użycie podejścia CQRS, można je zaimplementować w `CommandHandler` klasie w `Handle()` ramach metody.</span><span class="sxs-lookup"><span data-stu-id="69c17-117">In more advanced microservices, like when using CQRS approaches, it can be implemented in the `CommandHandler` class, within the `Handle()` method.</span></span>

### <a name="designing-atomicity-and-resiliency-when-publishing-to-the-event-bus"></a><span data-ttu-id="69c17-118">Projektowanie niepodzielności i odporności podczas publikowania w usłudze Event Bus</span><span class="sxs-lookup"><span data-stu-id="69c17-118">Designing atomicity and resiliency when publishing to the event bus</span></span>

<span data-ttu-id="69c17-119">Po opublikowaniu zdarzeń integracji za pomocą rozproszonego systemu obsługi komunikatów, takiego jak magistrala zdarzeń, występuje problem z niepodzielną aktualizacją pierwotnej bazy danych oraz publikowaniem zdarzenia (to oznacza, że obie operacje zostały zakończone lub nie zostały wykonane).</span><span class="sxs-lookup"><span data-stu-id="69c17-119">When you publish integration events through a distributed messaging system like your event bus, you have the problem of atomically updating the original database and publishing an event (that is, either both operations complete or none of them).</span></span> <span data-ttu-id="69c17-120">Na przykład, w uproszczonym przykładzie pokazanym wcześniej, kod zatwierdza dane do bazy danych w momencie zmiany ceny produktu, a następnie publikuje komunikat ProductPriceChangedIntegrationEvent.</span><span class="sxs-lookup"><span data-stu-id="69c17-120">For instance, in the simplified example shown earlier, the code commits data to the database when the product price is changed and then publishes a ProductPriceChangedIntegrationEvent message.</span></span> <span data-ttu-id="69c17-121">Początkowo może to mieć kluczowe znaczenie, że te dwie operacje są wykonywane niepodzielnie.</span><span class="sxs-lookup"><span data-stu-id="69c17-121">Initially, it might look essential that these two operations be performed atomically.</span></span> <span data-ttu-id="69c17-122">Jeśli jednak korzystasz z transakcji rozproszonej obejmującej bazę danych i brokera komunikatów, tak jak w starszych systemach, takich jak [Usługa kolejkowania komunikatów (MSMQ)](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx), nie jest to zalecane z powodów opisanych przez [theorem Cap](https://www.quora.com/What-Is-CAP-Theorem-1).</span><span class="sxs-lookup"><span data-stu-id="69c17-122">However, if you are using a distributed transaction involving the database and the message broker, as you do in older systems like [Microsoft Message Queuing (MSMQ)](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx), this is not recommended for the reasons described by the [CAP theorem](https://www.quora.com/What-Is-CAP-Theorem-1).</span></span>

<span data-ttu-id="69c17-123">W zasadzie mikrousługi są używane do tworzenia skalowalnych i wysoko dostępnych systemów.</span><span class="sxs-lookup"><span data-stu-id="69c17-123">Basically, you use microservices to build scalable and highly available systems.</span></span> <span data-ttu-id="69c17-124">Uproszczenie, theorem CAP oznacza, że nie można utworzyć (rozproszonej) bazy danych (lub mikrousługi, która jest właścicielem modelu), która jest stale dostępna, silnie spójna *i* odporna na każdą partycję.</span><span class="sxs-lookup"><span data-stu-id="69c17-124">Simplifying somewhat, the CAP theorem says that you cannot build a (distributed) database (or a microservice that owns its model) that is continually available, strongly consistent, *and* tolerant to any partition.</span></span> <span data-ttu-id="69c17-125">Musisz wybrać dwie z tych trzech właściwości.</span><span class="sxs-lookup"><span data-stu-id="69c17-125">You must choose two of these three properties.</span></span>

<span data-ttu-id="69c17-126">W przypadku architektur opartych na mikrousługach należy wybrać dostępność i tolerancję, a także wyróżnić silną spójność.</span><span class="sxs-lookup"><span data-stu-id="69c17-126">In microservices-based architectures, you should choose availability and tolerance, and you should deemphasize strong consistency.</span></span> <span data-ttu-id="69c17-127">W związku z tym w większości nowoczesnych aplikacji opartych na mikrousługach zwykle nie ma potrzeby korzystania z transakcji rozproszonych w ramach komunikatów, tak jak podczas implementowania [transakcji rozproszonych](https://docs.microsoft.com/previous-versions/windows/desktop/ms681205(v=vs.85)) w oparciu o Distributed Transaction Coordinator systemu Windows (DTC). z [usługą MSMQ](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="69c17-127">Therefore, in most modern microservice-based applications, you usually do not want to use distributed transactions in messaging, as you do when you implement [distributed transactions](https://docs.microsoft.com/previous-versions/windows/desktop/ms681205(v=vs.85)) based on the Windows Distributed Transaction Coordinator (DTC) with [MSMQ](https://msdn.microsoft.com/library/windows/desktop/ms711472(v=vs.85).aspx).</span></span>

<span data-ttu-id="69c17-128">Wróć do początkowego problemu i jego przykładu.</span><span class="sxs-lookup"><span data-stu-id="69c17-128">Let’s go back to the initial issue and its example.</span></span> <span data-ttu-id="69c17-129">Jeśli usługa ulegnie awarii po zaktualizowaniu bazy danych (w tym przypadku bezpośrednio po wierszu kodu z \_kontekstem). SaveChangesAsync ()), ale przed opublikowaniem zdarzenia integracji, ogólny system może stać się niespójny.</span><span class="sxs-lookup"><span data-stu-id="69c17-129">If the service crashes after the database is updated (in this case, right after the line of code with \_context.SaveChangesAsync()), but before the integration event is published, the overall system could become inconsistent.</span></span> <span data-ttu-id="69c17-130">Może to być krytyczne dla firmy, w zależności od konkretnej operacji biznesowej.</span><span class="sxs-lookup"><span data-stu-id="69c17-130">This might be business critical, depending on the specific business operation you are dealing with.</span></span>

<span data-ttu-id="69c17-131">Jak wspomniano wcześniej w sekcji architektura, można mieć kilka metod postępowania z tym problemem:</span><span class="sxs-lookup"><span data-stu-id="69c17-131">As mentioned earlier in the architecture section, you can have several approaches for dealing with this issue:</span></span>

- <span data-ttu-id="69c17-132">Przy użyciu [wzorca pozyskiwania pełnego zdarzenia](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing).</span><span class="sxs-lookup"><span data-stu-id="69c17-132">Using the full [Event Sourcing pattern](https://docs.microsoft.com/azure/architecture/patterns/event-sourcing).</span></span>

- <span data-ttu-id="69c17-133">Korzystanie z [wyszukiwania w dzienniku transakcji](https://www.scoop.it/t/sql-server-transaction-log-mining).</span><span class="sxs-lookup"><span data-stu-id="69c17-133">Using [transaction log mining](https://www.scoop.it/t/sql-server-transaction-log-mining).</span></span>

- <span data-ttu-id="69c17-134">Przy użyciu [wzorca skrzynki nadawczej](http://gistlabs.com/2014/05/the-outbox/).</span><span class="sxs-lookup"><span data-stu-id="69c17-134">Using the [Outbox pattern](http://gistlabs.com/2014/05/the-outbox/).</span></span> <span data-ttu-id="69c17-135">Jest to tabela transakcyjna do przechowywania zdarzeń integracji (rozszerzających transakcję lokalną).</span><span class="sxs-lookup"><span data-stu-id="69c17-135">This is a transactional table to store the integration events (extending the local transaction).</span></span>

<span data-ttu-id="69c17-136">W tym scenariuszu przy użyciu pełnej wzorca określania źródła zdarzeń (ES) jest jednym z najlepszych metod, jeśli *nie* najlepsze.</span><span class="sxs-lookup"><span data-stu-id="69c17-136">For this scenario, using the full Event Sourcing (ES) pattern is one of the best approaches, if not *the* best.</span></span> <span data-ttu-id="69c17-137">Jednak w wielu scenariuszach aplikacji może nie być możliwe zaimplementowanie systemu całkowitego ES.</span><span class="sxs-lookup"><span data-stu-id="69c17-137">However, in many application scenarios, you might not be able to implement a full ES system.</span></span> <span data-ttu-id="69c17-138">ES oznacza przechowywanie tylko zdarzeń domeny w transakcyjnej bazie danych, a nie przechowywanie bieżących danych stanu.</span><span class="sxs-lookup"><span data-stu-id="69c17-138">ES means storing only domain events in your transactional database, instead of storing current state data.</span></span> <span data-ttu-id="69c17-139">Przechowywanie tylko zdarzeń domeny może mieć znakomite korzyści, takie jak udostępnienie historii systemu i możliwość ustalenia stanu systemu w dowolnym momencie w przeszłości.</span><span class="sxs-lookup"><span data-stu-id="69c17-139">Storing only domain events can have great benefits, such as having the history of your system available and being able to determine the state of your system at any moment in the past.</span></span> <span data-ttu-id="69c17-140">Jednak wdrożenie systemu Full ES wymaga przeprowadzenia ponownej architektury większości systemów i wprowadzono wiele innych złożoności i wymagań.</span><span class="sxs-lookup"><span data-stu-id="69c17-140">However, implementing a full ES system requires you to rearchitect most of your system and introduces many other complexities and requirements.</span></span> <span data-ttu-id="69c17-141">Można na przykład użyć bazy danych przeznaczonej do określania źródła zdarzeń, takich jak [Magazyn zdarzeń](https://eventstore.org/), lub bazy danych zorientowanej na dokumenty, takiej jak Azure Cosmos DB, MongoDB, Cassandra, CouchDB lub RavenDB.</span><span class="sxs-lookup"><span data-stu-id="69c17-141">For example, you would want to use a database specifically made for event sourcing, such as [Event Store](https://eventstore.org/), or a document-oriented database such as Azure Cosmos DB, MongoDB, Cassandra, CouchDB, or RavenDB.</span></span> <span data-ttu-id="69c17-142">ES to doskonałe rozwiązanie tego problemu, ale nie najłatwiej, chyba że masz już doświadczenie ze źródłem zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="69c17-142">ES is a great approach for this problem, but not the easiest solution unless you are already familiar with event sourcing.</span></span>

<span data-ttu-id="69c17-143">Opcja korzystania z wyszukiwania w dzienniku transakcji początkowo wygląda bardzo przejrzysta.</span><span class="sxs-lookup"><span data-stu-id="69c17-143">The option to use transaction log mining initially looks very transparent.</span></span> <span data-ttu-id="69c17-144">Aby jednak korzystać z tego podejścia, mikrousługa musi być dołączona do dziennika transakcji RDBMS, na przykład dziennika transakcji SQL Server.</span><span class="sxs-lookup"><span data-stu-id="69c17-144">However, to use this approach, the microservice has to be coupled to your RDBMS transaction log, such as the SQL Server transaction log.</span></span> <span data-ttu-id="69c17-145">Prawdopodobnie nie jest to pożądane.</span><span class="sxs-lookup"><span data-stu-id="69c17-145">This is probably not desirable.</span></span> <span data-ttu-id="69c17-146">Kolejną wadą jest to, że aktualizacje niskiego poziomu rejestrowane w dzienniku transakcji mogą nie znajdować się na tym samym poziomie co zdarzenia integracji wysokiego poziomu.</span><span class="sxs-lookup"><span data-stu-id="69c17-146">Another drawback is that the low-level updates recorded in the transaction log might not be at the same level as your high-level integration events.</span></span> <span data-ttu-id="69c17-147">W takim przypadku proces odtwarzania tych operacji dziennika transakcji może być trudny.</span><span class="sxs-lookup"><span data-stu-id="69c17-147">If so, the process of reverse-engineering those transaction log operations can be difficult.</span></span>

<span data-ttu-id="69c17-148">Zrównoważonym podejściem jest mieszanka tabeli baz danych transakcyjnych i uproszczonego wzorca ES.</span><span class="sxs-lookup"><span data-stu-id="69c17-148">A balanced approach is a mix of a transactional database table and a simplified ES pattern.</span></span> <span data-ttu-id="69c17-149">Można użyć stanu, takiego jak "gotowe do opublikowania zdarzenia", które zostało ustawione w oryginalnym zdarzeniu po zatwierdzeniu go do tabeli zdarzeń integracji.</span><span class="sxs-lookup"><span data-stu-id="69c17-149">You can use a state such as “ready to publish the event,” which you set in the original event when you commit it to the integration events table.</span></span> <span data-ttu-id="69c17-150">Następnie próbujesz opublikować zdarzenie w usłudze Event Bus.</span><span class="sxs-lookup"><span data-stu-id="69c17-150">You then try to publish the event to the event bus.</span></span> <span data-ttu-id="69c17-151">W przypadku pomyślnego wykonania akcji Opublikuj zdarzenie należy rozpocząć kolejną transakcję w usłudze pochodzenia i przenieść stan z "gotowe do opublikowania zdarzenia" do "już opublikowanego zdarzenia".</span><span class="sxs-lookup"><span data-stu-id="69c17-151">If the publish-event action succeeds, you start another transaction in the origin service and move the state from “ready to publish the event” to “event already published.”</span></span>

<span data-ttu-id="69c17-152">Jeśli akcja Publikuj — zdarzenie w usłudze Event Bus zakończy się niepowodzeniem, dane nadal nie będą spójne w ramach mikrousługi, ale nadal są oznaczone jako "gotowe do opublikowania zdarzenia" i w odniesieniu do reszty usług, będzie ostatecznie spójna.</span><span class="sxs-lookup"><span data-stu-id="69c17-152">If the publish-event action in the event bus fails, the data still will not be inconsistent within the origin microservice—it is still marked as “ready to publish the event,” and with respect to the rest of the services, it will eventually be consistent.</span></span> <span data-ttu-id="69c17-153">Zadania w tle można zawsze sprawdzać stan transakcji lub zdarzeń integracji.</span><span class="sxs-lookup"><span data-stu-id="69c17-153">You can always have background jobs checking the state of the transactions or integration events.</span></span> <span data-ttu-id="69c17-154">Jeśli zadanie znajdzie zdarzenie w stanie "gotowe do opublikowania zdarzenia", może spróbować ponownie opublikować to zdarzenie w usłudze Event Bus.</span><span class="sxs-lookup"><span data-stu-id="69c17-154">If the job finds an event in the “ready to publish the event” state, it can try to republish that event to the event bus.</span></span>

<span data-ttu-id="69c17-155">Należy zauważyć, że w tym podejściu są utrwalane tylko zdarzenia integracji dla każdej mikrousługi pochodzenia i tylko zdarzenia, które mają być przekazywane do innych mikrousług lub systemów zewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="69c17-155">Notice that with this approach, you are persisting only the integration events for each origin microservice, and only the events that you want to communicate to other microservices or external systems.</span></span> <span data-ttu-id="69c17-156">W przeciwieństwie do systemu w pełni Wyes wszystkie zdarzenia domeny również są przechowywane.</span><span class="sxs-lookup"><span data-stu-id="69c17-156">In contrast, in a full ES system, you store all domain events as well.</span></span>

<span data-ttu-id="69c17-157">W związku z tym to zrównoważone podejście to uproszczony system.</span><span class="sxs-lookup"><span data-stu-id="69c17-157">Therefore, this balanced approach is a simplified ES system.</span></span> <span data-ttu-id="69c17-158">Wymagana jest lista zdarzeń integracji z ich bieżącym stanem ("gotowe do opublikowania" zamiast "opublikowany").</span><span class="sxs-lookup"><span data-stu-id="69c17-158">You need a list of integration events with their current state (“ready to publish” versus “published”).</span></span> <span data-ttu-id="69c17-159">Ale musisz tylko zaimplementować te Stany dla zdarzeń integracji.</span><span class="sxs-lookup"><span data-stu-id="69c17-159">But you only need to implement these states for the integration events.</span></span> <span data-ttu-id="69c17-160">W tej metodzie nie trzeba przechowywać wszystkich danych domeny jako zdarzeń w transakcyjnej bazie danych, tak jak w przypadku systemu w pełni Wyes.</span><span class="sxs-lookup"><span data-stu-id="69c17-160">And in this approach, you do not need to store all your domain data as events in the transactional database, as you would in a full ES system.</span></span>

<span data-ttu-id="69c17-161">Jeśli korzystasz już z relacyjnej bazy danych, możesz użyć tabeli transakcyjnej do przechowywania zdarzeń integracji.</span><span class="sxs-lookup"><span data-stu-id="69c17-161">If you are already using a relational database, you can use a transactional table to store integration events.</span></span> <span data-ttu-id="69c17-162">Aby uzyskać niepodzielność w aplikacji, należy użyć dwuetapowego procesu opartego na lokalnych transakcjach.</span><span class="sxs-lookup"><span data-stu-id="69c17-162">To achieve atomicity in your application, you use a two-step process based on local transactions.</span></span> <span data-ttu-id="69c17-163">Zasadniczo istnieje tabela IntegrationEvent w tej samej bazie danych, w której znajdują się jednostki domeny.</span><span class="sxs-lookup"><span data-stu-id="69c17-163">Basically, you have an IntegrationEvent table in the same database where you have your domain entities.</span></span> <span data-ttu-id="69c17-164">Ta tabela działa jako ubezpieczenie do osiągnięcia niepodzielności, aby uwzględnić utrwalone zdarzenia integracji w tych samych transakcjach, które zatwierdzają dane domeny.</span><span class="sxs-lookup"><span data-stu-id="69c17-164">That table works as an insurance for achieving atomicity so that you include persisted integration events into the same transactions that are committing your domain data.</span></span>

<span data-ttu-id="69c17-165">Krok po kroku proces przebiega następująco:</span><span class="sxs-lookup"><span data-stu-id="69c17-165">Step by step, the process goes like this:</span></span>

1. <span data-ttu-id="69c17-166">Aplikacja rozpoczyna lokalną transakcję bazy danych.</span><span class="sxs-lookup"><span data-stu-id="69c17-166">The application begins a local database transaction.</span></span>

2. <span data-ttu-id="69c17-167">Następnie aktualizuje stan jednostek domeny i wstawia zdarzenie do tabeli zdarzeń integracji.</span><span class="sxs-lookup"><span data-stu-id="69c17-167">It then updates the state of your domain entities and inserts an event into the integration event table.</span></span>

3. <span data-ttu-id="69c17-168">Na koniec zatwierdza transakcji, dzięki czemu uzyskasz odpowiednią niepodzielność, a następnie</span><span class="sxs-lookup"><span data-stu-id="69c17-168">Finally, it commits the transaction, so you get the desired atomicity and then</span></span>

4. <span data-ttu-id="69c17-169">Wydarzenie można opublikować w dowolny sposób (dalej).</span><span class="sxs-lookup"><span data-stu-id="69c17-169">You publish the event somehow (next).</span></span>

<span data-ttu-id="69c17-170">Podczas wdrażania kroków publikowania zdarzeń można wybrać następujące opcje:</span><span class="sxs-lookup"><span data-stu-id="69c17-170">When implementing the steps of publishing the events, you have these choices:</span></span>

- <span data-ttu-id="69c17-171">Opublikuj wydarzenie integracji bezpośrednio po zatwierdzeniu transakcji i użyj innej transakcji lokalnej, aby oznaczyć zdarzenia w tabeli jako publikowane.</span><span class="sxs-lookup"><span data-stu-id="69c17-171">Publish the integration event right after committing the transaction and use another local transaction to mark the events in the table as being published.</span></span> <span data-ttu-id="69c17-172">Następnie należy użyć tabeli jako artefaktu do śledzenia zdarzeń związanych z integracją w przypadku problemów z mikrousługami zdalnymi, a także wykonywać działania wyrównawcze na podstawie przechowywanych zdarzeń integracji.</span><span class="sxs-lookup"><span data-stu-id="69c17-172">Then, use the table just as an artifact to track the integration events in case of issues in the remote microservices, and perform compensatory actions based on the stored integration events.</span></span>

- <span data-ttu-id="69c17-173">Użyj tabeli jako rodzaju kolejki.</span><span class="sxs-lookup"><span data-stu-id="69c17-173">Use the table as a kind of queue.</span></span> <span data-ttu-id="69c17-174">Oddzielny wątek lub proces aplikacji wysyła zapytanie do tabeli zdarzeń integracji, publikuje zdarzenia do magistrali zdarzeń, a następnie używa transakcji lokalnej do oznaczania zdarzeń jako opublikowanych.</span><span class="sxs-lookup"><span data-stu-id="69c17-174">A separate application thread or process queries the integration event table, publishes the events to the event bus, and then uses a local transaction to mark the events as published.</span></span>

<span data-ttu-id="69c17-175">Rysunek 6-22 przedstawia architekturę dla pierwszego z tych metod.</span><span class="sxs-lookup"><span data-stu-id="69c17-175">Figure 6-22 shows the architecture for the first of these approaches.</span></span>

![Jedno podejście do obsługi niepodzielności podczas publikowania zdarzeń: Użyj jednej transakcji, aby zatwierdzić zdarzenie w tabeli dziennika zdarzeń, a następnie inna transakcja do opublikowania (używana w eShopOnContainers)](./media/image23.png)

<span data-ttu-id="69c17-177">**Rysunek 6-22**.</span><span class="sxs-lookup"><span data-stu-id="69c17-177">**Figure 6-22**.</span></span> <span data-ttu-id="69c17-178">Niepodzielność przy publikowaniu zdarzeń do magistrali zdarzeń</span><span class="sxs-lookup"><span data-stu-id="69c17-178">Atomicity when publishing events to the event bus</span></span>

<span data-ttu-id="69c17-179">Na rysunku 6-22 Brak dodatkowej mikrousługi roboczej, która jest odpowiedzialna za sprawdzenie i potwierdzenie sukcesu opublikowanych zdarzeń integracji.</span><span class="sxs-lookup"><span data-stu-id="69c17-179">The approach illustrated in Figure 6-22 is missing an additional worker microservice that is in charge of checking and confirming the success of the published integration events.</span></span> <span data-ttu-id="69c17-180">W razie awarii, dodatkowy mikrousługa dla procesu roboczego kontrolera może odczytywać zdarzenia z tabeli i ponownie je opublikować, czyli powtórzyć krok numer 2.</span><span class="sxs-lookup"><span data-stu-id="69c17-180">In case of failure, that additional checker worker microservice can read events from the table and republish them, that is, repeat step number 2.</span></span>

<span data-ttu-id="69c17-181">Informacje o drugim podejściu: należy użyć tabeli EventLog jako kolejki i zawsze używać mikrousługi procesu roboczego do publikowania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="69c17-181">About the second approach: you use the EventLog table as a queue and always use a worker microservice to publish the messages.</span></span> <span data-ttu-id="69c17-182">W takim przypadku proces jest podobny do przedstawionego na rysunku 6-23.</span><span class="sxs-lookup"><span data-stu-id="69c17-182">In that case, the process is like that shown in Figure 6-23.</span></span> <span data-ttu-id="69c17-183">Powoduje to wyświetlenie dodatkowej mikrousługi, a tabela jest pojedynczym źródłem przy publikowaniu zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="69c17-183">This shows an additional microservice, and the table is the single source when publishing events.</span></span>

![Inne podejście do obsługi niepodzielności: Publikuj w tabeli dziennika zdarzeń, a następnie zapublikuj zdarzenie przy użyciu innej mikrousługi (proces roboczy w tle).](./media/image24.png)

<span data-ttu-id="69c17-185">**Rysunek 6-23**.</span><span class="sxs-lookup"><span data-stu-id="69c17-185">**Figure 6-23**.</span></span> <span data-ttu-id="69c17-186">Niepodzielność przy publikowaniu zdarzeń do magistrali zdarzeń za pomocą mikrousługi procesu roboczego</span><span class="sxs-lookup"><span data-stu-id="69c17-186">Atomicity when publishing events to the event bus with a worker microservice</span></span>

<span data-ttu-id="69c17-187">Dla uproszczenia przykład eShopOnContainers używa pierwszego podejścia (bez dodatkowych procesów lub mikrousług sprawdzania) oraz magistrali zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="69c17-187">For simplicity, the eShopOnContainers sample uses the first approach (with no additional processes or checker microservices) plus the event bus.</span></span> <span data-ttu-id="69c17-188">Jednak eShopOnContainers nie obsługuje wszystkich możliwych przypadków niepowodzeń.</span><span class="sxs-lookup"><span data-stu-id="69c17-188">However, the eShopOnContainers is not handling all possible failure cases.</span></span> <span data-ttu-id="69c17-189">W rzeczywistej aplikacji wdrożonej w chmurze należy zastanowić się, że problemy będą nadal występować i należy zaimplementować ten test i ponownie Wyślij logikę.</span><span class="sxs-lookup"><span data-stu-id="69c17-189">In a real application deployed to the cloud, you must embrace the fact that issues will arise eventually, and you must implement that check and resend logic.</span></span> <span data-ttu-id="69c17-190">Użycie tabeli jako kolejki może być bardziej efektywne niż w przypadku pierwszej metody, jeśli istnieje taka tabela jako pojedyncze źródło zdarzeń podczas publikowania ich (z procesem roboczym) za pośrednictwem magistrali zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="69c17-190">Using the table as a queue can be more effective than the first approach if you have that table as a single source of events when publishing them (with the worker) through the event bus.</span></span>

### <a name="implementing-atomicity-when-publishing-integration-events-through-the-event-bus"></a><span data-ttu-id="69c17-191">Implementowanie niepodzielności podczas publikowania zdarzeń integracji za pomocą magistrali zdarzeń</span><span class="sxs-lookup"><span data-stu-id="69c17-191">Implementing atomicity when publishing integration events through the event bus</span></span>

<span data-ttu-id="69c17-192">Poniższy kod pokazuje, jak można utworzyć pojedynczą transakcję obejmującą wiele obiektów DbContext — jednego kontekstu związanego z aktualizowanymi oryginalnymi danymi oraz drugi kontekst związany z tabelą IntegrationEventLog.</span><span class="sxs-lookup"><span data-stu-id="69c17-192">The following code shows how you can create a single transaction involving multiple DbContext objects—one context related to the original data being updated, and the second context related to the IntegrationEventLog table.</span></span>

<span data-ttu-id="69c17-193">Należy pamiętać, że transakcja w poniższym przykładowym kodzie nie będzie odporna, jeśli połączenia z bazą danych mają dowolny problem w chwili, gdy kod jest uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="69c17-193">Note that the transaction in the example code below will not be resilient if connections to the database have any issue at the time when the code is running.</span></span> <span data-ttu-id="69c17-194">Taka sytuacja może wystąpić w systemach opartych na chmurze, takich jak Azure SQL DB, co może przenosić bazy danych między serwerami.</span><span class="sxs-lookup"><span data-stu-id="69c17-194">This can happen in cloud-based systems like Azure SQL DB, which might move databases across servers.</span></span> <span data-ttu-id="69c17-195">Aby zaimplementować odporne transakcje w wielu kontekstach, zobacz sekcję [implementowanie odpornych Entity Framework Core połączeń SQL](../implement-resilient-applications/implement-resilient-entity-framework-core-sql-connections.md) w dalszej części tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="69c17-195">For implementing resilient transactions across multiple contexts, see the [Implementing resilient Entity Framework Core SQL connections](../implement-resilient-applications/implement-resilient-entity-framework-core-sql-connections.md) section later in this guide.</span></span>

<span data-ttu-id="69c17-196">W przypadku przejrzystości Poniższy przykład pokazuje cały proces w pojedynczym fragmencie kodu.</span><span class="sxs-lookup"><span data-stu-id="69c17-196">For clarity, the following example shows the whole process in a single piece of code.</span></span> <span data-ttu-id="69c17-197">Jednak implementacja eShopOnContainers jest faktycznie Refaktoryzacja i dzieli tę logikę na wiele klas, dzięki czemu łatwiej jest ją konserwować.</span><span class="sxs-lookup"><span data-stu-id="69c17-197">However, the eShopOnContainers implementation is actually refactored and split this logic into multiple classes so it is easier to maintain.</span></span>

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

<span data-ttu-id="69c17-198">Po utworzeniu zdarzenia integracji ProductPriceChangedIntegrationEvent transakcja, która przechowuje pierwotną operację domeny (aktualizacja elementu katalogu) również obejmuje trwałość zdarzenia w tabeli EventLog.</span><span class="sxs-lookup"><span data-stu-id="69c17-198">After the ProductPriceChangedIntegrationEvent integration event is created, the transaction that stores the original domain operation (update the catalog item) also includes the persistence of the event in the EventLog table.</span></span> <span data-ttu-id="69c17-199">Powoduje to pojedyncze transakcję i zawsze będzie można sprawdzić, czy komunikaty o zdarzeniach zostały wysłane.</span><span class="sxs-lookup"><span data-stu-id="69c17-199">This makes it a single transaction, and you will always be able to check whether event messages were sent.</span></span>

<span data-ttu-id="69c17-200">Tabela dziennika zdarzeń jest aktualizowana w sposób niepodzielny z pierwotną operacją bazy danych przy użyciu transakcji lokalnej w odniesieniu do tej samej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="69c17-200">The event log table is updated atomically with the original database operation, using a local transaction against the same database.</span></span> <span data-ttu-id="69c17-201">Jeśli jakakolwiek operacja zakończy się niepowodzeniem, zgłaszany jest wyjątek, a transakcja wycofuje każdą ukończoną operację, w konsekwencji zachowanie spójności między operacjami domeny i komunikatami zdarzeń zapisanymi w tabeli.</span><span class="sxs-lookup"><span data-stu-id="69c17-201">If any of the operations fail, an exception is thrown and the transaction rolls back any completed operation, thus maintaining consistency between the domain operations and the event messages saved to the table.</span></span>

### <a name="receiving-messages-from-subscriptions-event-handlers-in-receiver-microservices"></a><span data-ttu-id="69c17-202">Otrzymywanie komunikatów z subskrypcji: programy obsługi zdarzeń w mikrousługach odbiornika</span><span class="sxs-lookup"><span data-stu-id="69c17-202">Receiving messages from subscriptions: event handlers in receiver microservices</span></span>

<span data-ttu-id="69c17-203">Oprócz logiki subskrypcji zdarzeń należy zaimplementować wewnętrzny kod dla programów obsługi zdarzeń integracji (na przykład metodę wywołania zwrotnego).</span><span class="sxs-lookup"><span data-stu-id="69c17-203">In addition to the event subscription logic, you need to implement the internal code for the integration event handlers (like a callback method).</span></span> <span data-ttu-id="69c17-204">Procedura obsługi zdarzeń służy do określania miejsca, w którym są odbierane i przetwarzane komunikaty o zdarzeniu określonego typu.</span><span class="sxs-lookup"><span data-stu-id="69c17-204">The event handler is where you specify where the event messages of a certain type will be received and processed.</span></span>

<span data-ttu-id="69c17-205">Program obsługi zdarzeń najpierw odbiera wystąpienie zdarzenia z magistrali zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="69c17-205">An event handler first receives an event instance from the event bus.</span></span> <span data-ttu-id="69c17-206">Następnie lokalizuje składnik do przetworzenia powiązane z tym zdarzeniem integracji, propagowanie i utrwalanie zdarzenia jako zmiany stanu w mikrousłudze odbiornika.</span><span class="sxs-lookup"><span data-stu-id="69c17-206">Then it locates the component to be processed related to that integration event, propagating and persisting the event as a change in state in the receiver microservice.</span></span> <span data-ttu-id="69c17-207">Na przykład, jeśli zdarzenie ProductPriceChanged pochodzi z mikrousługi katalogu, jest ono obsługiwane w mikrousłudze koszyka i zmienia stan w tej mikrousłudze dla koszyka odbiornik, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="69c17-207">For example, if a ProductPriceChanged event originates in the catalog microservice, it is handled in the basket microservice and changes the state in this receiver basket microservice as well, as shown in the following code.</span></span>

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

<span data-ttu-id="69c17-208">Program obsługi zdarzeń musi sprawdzić, czy produkt istnieje w żadnym z wystąpień koszyka.</span><span class="sxs-lookup"><span data-stu-id="69c17-208">The event handler needs to verify whether the product exists in any of the basket instances.</span></span> <span data-ttu-id="69c17-209">Aktualizuje także cenę elementu dla każdego elementu powiązanego z wierszem koszyka.</span><span class="sxs-lookup"><span data-stu-id="69c17-209">It also updates the item price for each related basket line item.</span></span> <span data-ttu-id="69c17-210">Na koniec tworzy alert, który będzie wyświetlany użytkownikowi w sprawie zmiany ceny, jak pokazano na rysunku 6-24.</span><span class="sxs-lookup"><span data-stu-id="69c17-210">Finally, it creates an alert to be displayed to the user about the price change, as shown in Figure 6-24.</span></span>

![Widok przeglądarki powiadamiania o zmianie procesu w koszyku użytkownika.](./media/image25.png)

<span data-ttu-id="69c17-212">**Rysunek 6-24**.</span><span class="sxs-lookup"><span data-stu-id="69c17-212">**Figure 6-24**.</span></span> <span data-ttu-id="69c17-213">Wyświetlanie zmiany ceny elementu w koszyku, zgodnie z poinformowaniem o zdarzeniach integracji</span><span class="sxs-lookup"><span data-stu-id="69c17-213">Displaying an item price change in a basket, as communicated by integration events</span></span>

## <a name="idempotency-in-update-message-events"></a><span data-ttu-id="69c17-214">Idempotentności w Aktualizuj zdarzenia komunikatów</span><span class="sxs-lookup"><span data-stu-id="69c17-214">Idempotency in update message events</span></span>

<span data-ttu-id="69c17-215">Ważnym aspektem zdarzeń aktualizacji komunikatów jest to, że awaria w dowolnym momencie komunikacji powinna spowodować, że komunikat zostanie ponowiony.</span><span class="sxs-lookup"><span data-stu-id="69c17-215">An important aspect of update message events is that a failure at any point in the communication should cause the message to be retried.</span></span> <span data-ttu-id="69c17-216">W przeciwnym razie zadanie w tle może próbować opublikować zdarzenie, które zostało już opublikowane, tworząc sytuację wyścigu.</span><span class="sxs-lookup"><span data-stu-id="69c17-216">Otherwise a background task might try to publish an event that has already been published, creating a race condition.</span></span> <span data-ttu-id="69c17-217">Musisz się upewnić, że aktualizacje są idempotentne lub że zapewniają wystarczające informacje, aby upewnić się, że można wykryć duplikat, odrzucić go i wysłać tylko jedną odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="69c17-217">You need to make sure that the updates are either idempotent or that they provide enough information to ensure that you can detect a duplicate, discard it, and send back only one response.</span></span>

<span data-ttu-id="69c17-218">Jak wspomniano wcześniej, idempotentności oznacza, że operacja może być wykonana wiele razy bez zmiany wyniku.</span><span class="sxs-lookup"><span data-stu-id="69c17-218">As noted earlier, idempotency means that an operation can be performed multiple times without changing the result.</span></span> <span data-ttu-id="69c17-219">W środowisku obsługi komunikatów, podobnie jak podczas komunikacji z zdarzeniami, zdarzenie jest idempotentne, jeśli może być dostarczone wiele razy bez zmiany wyniku dla mikrousługi odbiornika.</span><span class="sxs-lookup"><span data-stu-id="69c17-219">In a messaging environment, as when communicating events, an event is idempotent if it can be delivered multiple times without changing the result for the receiver microservice.</span></span> <span data-ttu-id="69c17-220">Może to być konieczne ze względu na charakter samego zdarzenia lub ze względu na sposób, w jaki system obsługuje zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="69c17-220">This may be necessary because of the nature of the event itself, or because of the way the system handles the event.</span></span> <span data-ttu-id="69c17-221">W przypadku aplikacji korzystających z komunikatów, a nie tylko w aplikacjach, które implementują wzorzec magistrali zdarzeń, idempotentności jest ważna.</span><span class="sxs-lookup"><span data-stu-id="69c17-221">Message idempotency is important in any application that uses messaging, not just in applications that implement the event bus pattern.</span></span>

<span data-ttu-id="69c17-222">Przykładem operacji idempotentne jest instrukcja SQL, która wstawia dane do tabeli tylko wtedy, gdy dane nie są jeszcze w tabeli.</span><span class="sxs-lookup"><span data-stu-id="69c17-222">An example of an idempotent operation is a SQL statement that inserts data into a table only if that data is not already in the table.</span></span> <span data-ttu-id="69c17-223">Nie ma znaczenia, ile razy jest wykonywanych w instrukcji SQL INSERT; wynik będzie taki sam — tabela będzie zawierać te dane.</span><span class="sxs-lookup"><span data-stu-id="69c17-223">It does not matter how many times you run that insert SQL statement; the result will be the same—the table will contain that data.</span></span> <span data-ttu-id="69c17-224">Idempotentności takie jak może być również konieczne w przypadku komunikacji z komunikatami, jeśli mogą być potencjalnie wysyłane i przetwarzane więcej niż jeden raz.</span><span class="sxs-lookup"><span data-stu-id="69c17-224">Idempotency like this can also be necessary when dealing with messages if the messages could potentially be sent and therefore processed more than once.</span></span> <span data-ttu-id="69c17-225">Na przykład, jeśli logika ponawiania powoduje, że nadawca wysyła dokładnie ten sam komunikat więcej niż raz, należy się upewnić, że jest idempotentne.</span><span class="sxs-lookup"><span data-stu-id="69c17-225">For instance, if retry logic causes a sender to send exactly the same message more than once, you need to make sure that it is idempotent.</span></span>

<span data-ttu-id="69c17-226">Możliwe jest zaprojektowanie komunikatów idempotentne.</span><span class="sxs-lookup"><span data-stu-id="69c17-226">It is possible to design idempotent messages.</span></span> <span data-ttu-id="69c17-227">Na przykład można utworzyć zdarzenie "Ustaw cenę produktu na $25" zamiast "Dodaj $5 do ceny produktu".</span><span class="sxs-lookup"><span data-stu-id="69c17-227">For example, you can create an event that says "set the product price to $25" instead of "add $5 to the product price."</span></span> <span data-ttu-id="69c17-228">Można bezpiecznie przetwarzać pierwszy komunikat dowolną liczbę razy, a wynik będzie taki sam.</span><span class="sxs-lookup"><span data-stu-id="69c17-228">You could safely process the first message any number of times and the result will be the same.</span></span> <span data-ttu-id="69c17-229">To nie jest prawdziwe dla drugiego komunikatu.</span><span class="sxs-lookup"><span data-stu-id="69c17-229">That is not true for the second message.</span></span> <span data-ttu-id="69c17-230">Jednak nawet w pierwszym przypadku można nie chcieć przetwarzać pierwszego zdarzenia, ponieważ system mógł również przesłać nowsze zdarzenie zmiany ceny i zastąpić nową cenę.</span><span class="sxs-lookup"><span data-stu-id="69c17-230">But even in the first case, you might not want to process the first event, because the system could also have sent a newer price-change event and you would be overwriting the new price.</span></span>

<span data-ttu-id="69c17-231">Innym przykładem może być zdarzenie ukończone w kolejności, które jest propagowane do wielu subskrybentów.</span><span class="sxs-lookup"><span data-stu-id="69c17-231">Another example might be an order-completed event being propagated to multiple subscribers.</span></span> <span data-ttu-id="69c17-232">Ważne jest, aby informacje o zamówieniach były aktualizowane w innych systemach tylko raz, nawet jeśli istnieją zduplikowane zdarzenia komunikatów dla tego samego zdarzenia Order-ukończony.</span><span class="sxs-lookup"><span data-stu-id="69c17-232">It is important that order information be updated in other systems just once, even if there are duplicated message events for the same order-completed event.</span></span>

<span data-ttu-id="69c17-233">Jest wygodne w przypadku pewnego rodzaju tożsamości dla każdego zdarzenia, dzięki czemu można utworzyć logikę, która wymusza, że każde zdarzenie jest przetwarzane tylko raz dla każdego odbiorcy.</span><span class="sxs-lookup"><span data-stu-id="69c17-233">It is convenient to have some kind of identity per event so that you can create logic that enforces that each event is processed only once per receiver.</span></span>

<span data-ttu-id="69c17-234">Niektóre przetwarzanie komunikatów jest z natury idempotentne.</span><span class="sxs-lookup"><span data-stu-id="69c17-234">Some message processing is inherently idempotent.</span></span> <span data-ttu-id="69c17-235">Na przykład jeśli system generuje miniatury obrazów, może nie mieć znaczenia, ile razy komunikat o wygenerowanej miniaturze został przetworzony; wynikiem jest to, że miniatury są generowane i są takie same, jak zawsze.</span><span class="sxs-lookup"><span data-stu-id="69c17-235">For example, if a system generates image thumbnails, it might not matter how many times the message about the generated thumbnail is processed; the outcome is that the thumbnails are generated and they are the same every time.</span></span> <span data-ttu-id="69c17-236">Z drugiej strony operacje, takie jak wywołanie bramy płatności do naliczania opłat za kartę kredytową, nie mogą być idempotentne w ogóle.</span><span class="sxs-lookup"><span data-stu-id="69c17-236">On the other hand, operations such as calling a payment gateway to charge a credit card may not be idempotent at all.</span></span> <span data-ttu-id="69c17-237">W takich przypadkach należy upewnić się, że przetwarzanie komunikatu wiele razy ma oczekiwany efekt.</span><span class="sxs-lookup"><span data-stu-id="69c17-237">In these cases, you need to ensure that processing a message multiple times has the effect that you expect.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="69c17-238">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="69c17-238">Additional resources</span></span>

- <span data-ttu-id="69c17-239">**Uznawanie wiadomości idempotentności**</span><span class="sxs-lookup"><span data-stu-id="69c17-239">**Honoring message idempotency**</span></span>  
  <https://docs.microsoft.com/previous-versions/msp-n-p/jj591565(v=pandp.10)#honoring-message-idempotency>

## <a name="deduplicating-integration-event-messages"></a><span data-ttu-id="69c17-240">Deduplikowanie komunikatów zdarzeń integracji</span><span class="sxs-lookup"><span data-stu-id="69c17-240">Deduplicating integration event messages</span></span>

<span data-ttu-id="69c17-241">Można upewnić się, że zdarzenia komunikatów są wysyłane i przetwarzane tylko raz dla każdego subskrybenta na różnych poziomach.</span><span class="sxs-lookup"><span data-stu-id="69c17-241">You can make sure that message events are sent and processed just once per subscriber at different levels.</span></span> <span data-ttu-id="69c17-242">Jednym ze sposobów jest użycie funkcji deduplikacji oferowanej przez używaną infrastrukturę obsługi komunikatów.</span><span class="sxs-lookup"><span data-stu-id="69c17-242">One way is to use a deduplication feature offered by the messaging infrastructure you are using.</span></span> <span data-ttu-id="69c17-243">Innym jest zaimplementowanie logiki niestandardowej w mikrousłudze docelowej.</span><span class="sxs-lookup"><span data-stu-id="69c17-243">Another is to implement custom logic in your destination microservice.</span></span> <span data-ttu-id="69c17-244">Posiadanie walidacji na poziomie transportu i na poziomie aplikacji jest najlepszym trafieniem.</span><span class="sxs-lookup"><span data-stu-id="69c17-244">Having validations at both the transport level and the application level is your best bet.</span></span>

### <a name="deduplicating-message-events-at-the-eventhandler-level"></a><span data-ttu-id="69c17-245">Deduplikowanie zdarzeń komunikatów na poziomie EventHandler</span><span class="sxs-lookup"><span data-stu-id="69c17-245">Deduplicating message events at the EventHandler level</span></span>

<span data-ttu-id="69c17-246">Jednym ze sposobów, aby upewnić się, że zdarzenie jest przetwarzane tylko raz przez dowolnego odbiorcę, przez implementację pewnej logiki podczas przetwarzania zdarzeń komunikatów w procedurach obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="69c17-246">One way to make sure that an event is processed just once by any receiver is by implementing certain logic when processing the message events in event handlers.</span></span> <span data-ttu-id="69c17-247">Na przykład jest to podejście używane w aplikacji eShopOnContainers, jak można je zobaczyć w [kodzie źródłowym klasy UserCheckoutAcceptedIntegrationEventHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) , gdy odbierze zdarzenie integracji UserCheckoutAcceptedIntegrationEvent.</span><span class="sxs-lookup"><span data-stu-id="69c17-247">For example, that is the approach used in the eShopOnContainers application, as you can see in the [source code of the UserCheckoutAcceptedIntegrationEventHandler class](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) when it receives an UserCheckoutAcceptedIntegrationEvent integration event.</span></span> <span data-ttu-id="69c17-248">(W tym przypadku CreateOrderCommand z IdentifiedCommand przy użyciu eventMsg. Identyfikator żądania jako identyfikatora, przed wysłaniem go do programu obsługi poleceń).</span><span class="sxs-lookup"><span data-stu-id="69c17-248">(In this case we wrap the CreateOrderCommand with an IdentifiedCommand, using the eventMsg.RequestId as an identifier, before sending it to the command handler).</span></span>

### <a name="deduplicating-messages-when-using-rabbitmq"></a><span data-ttu-id="69c17-249">Deduplikowanie komunikatów przy użyciu RabbitMQ</span><span class="sxs-lookup"><span data-stu-id="69c17-249">Deduplicating messages when using RabbitMQ</span></span>

<span data-ttu-id="69c17-250">W przypadku sporadycznych awarii sieci można duplikować komunikaty, a odbiorca wiadomości musi być gotowy do obsługi tych zduplikowanych komunikatów.</span><span class="sxs-lookup"><span data-stu-id="69c17-250">When intermittent network failures happen, messages can be duplicated, and the message receiver must be ready to handle these duplicated messages.</span></span> <span data-ttu-id="69c17-251">Jeśli to możliwe, odbiorcy powinny obsługiwać komunikaty w idempotentne sposób, który jest lepiej niż jawnie obsługujący deduplikację.</span><span class="sxs-lookup"><span data-stu-id="69c17-251">If possible, receivers should handle messages in an idempotent way, which is better than explicitly handling them with deduplication.</span></span>

<span data-ttu-id="69c17-252">Zgodnie z [dokumentacją RabbitMQ](https://www.rabbitmq.com/reliability.html#consumer)", jeśli wiadomość jest dostarczana do konsumenta, a następnie ponownie umieszczana w kolejce (ponieważ nie została potwierdzona przed porzuceniem połączenia przez klienta, na przykład), RabbitMQ ustawi na niej flagę ponownie dostarczone, gdy zostanie on dostarczony ponownie (niezależnie od tego, czy jest to ten sam Klient czy inny).</span><span class="sxs-lookup"><span data-stu-id="69c17-252">According to the [RabbitMQ documentation](https://www.rabbitmq.com/reliability.html#consumer), “If a message is delivered to a consumer and then requeued (because it was not acknowledged before the consumer connection dropped, for example) then RabbitMQ will set the redelivered flag on it when it is delivered again (whether to the same consumer or a different one).</span></span>

<span data-ttu-id="69c17-253">Jeśli ustawiono flagę "redostarczony", odbiorca musi uwzględnić to konto, ponieważ komunikat mógł już zostać przetworzony.</span><span class="sxs-lookup"><span data-stu-id="69c17-253">If the “redelivered” flag is set, the receiver must take that into account, because the message might already have been processed.</span></span> <span data-ttu-id="69c17-254">Ale nie jest to gwarantowane; komunikat nigdy nie dotarł do odbiorcy po jego przejściu do brokera komunikatów, prawdopodobnie z powodu problemów z siecią.</span><span class="sxs-lookup"><span data-stu-id="69c17-254">But that is not guaranteed; the message might never have reached the receiver after it left the message broker, perhaps because of network issues.</span></span> <span data-ttu-id="69c17-255">Z drugiej strony, jeśli flaga "redostarczany" nie została ustawiona, jest gwarantowane, że wiadomość nie została wysłana więcej niż raz.</span><span class="sxs-lookup"><span data-stu-id="69c17-255">On the other hand, if the “redelivered” flag is not set, it is guaranteed that the message has not been sent more than once.</span></span> <span data-ttu-id="69c17-256">W związku z tym odbiornik musi deduplikowanie komunikatów lub przetwarzać komunikaty w idempotentne sposób tylko wtedy, gdy flaga "redostarczany" została ustawiona w komunikacie.</span><span class="sxs-lookup"><span data-stu-id="69c17-256">Therefore, the receiver needs to deduplicate messages or process messages in an idempotent way only if the “redelivered” flag is set in the message.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="69c17-257">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="69c17-257">Additional resources</span></span>

- <span data-ttu-id="69c17-258">**Rozwidlenie eShopOnContainers przy użyciu NServiceBus (szczególne oprogramowanie)**  </span><span class="sxs-lookup"><span data-stu-id="69c17-258">**Forked eShopOnContainers using NServiceBus (Particular Software)** </span></span>\
    <https://go.particular.net/eShopOnContainers>

- <span data-ttu-id="69c17-259">**Obsługa komunikatów opartych na zdarzeniach** </span><span class="sxs-lookup"><span data-stu-id="69c17-259">**Event Driven Messaging** </span></span>\
    [http://soapatterns.org/design\_patterns/event\_driven\_messaging](http://soapatterns.org/design_patterns/event_driven_messaging)

- <span data-ttu-id="69c17-260">**Jimmy Bogard. Refaktoryzacja względem odporności: Ocenianie sprzęgu** </span><span class="sxs-lookup"><span data-stu-id="69c17-260">**Jimmy Bogard. Refactoring Towards Resilience: Evaluating Coupling** </span></span>\
    <https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/>

- <span data-ttu-id="69c17-261">**Publikowanie/subskrybowanie kanału** </span><span class="sxs-lookup"><span data-stu-id="69c17-261">**Publish-Subscribe channel** </span></span>\
    <https://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html>

- <span data-ttu-id="69c17-262">**Komunikacja między kontekstami ograniczonymi** </span><span class="sxs-lookup"><span data-stu-id="69c17-262">**Communicating Between Bounded Contexts** </span></span>\
    <https://docs.microsoft.com/previous-versions/msp-n-p/jj591572(v=pandp.10)>

- <span data-ttu-id="69c17-263">**Spójność ostateczna** </span><span class="sxs-lookup"><span data-stu-id="69c17-263">**Eventual Consistency** </span></span>\
    [https://en.wikipedia.org/wiki/Eventual\_consistency](https://en.wikipedia.org/wiki/Eventual_consistency)

- <span data-ttu-id="69c17-264">**Philip brązowy. Strategie integracji ograniczonych kontekstów** </span><span class="sxs-lookup"><span data-stu-id="69c17-264">**Philip Brown. Strategies for Integrating Bounded Contexts** </span></span>\
    <https://www.culttt.com/2014/11/26/strategies-integrating-bounded-contexts/>

- <span data-ttu-id="69c17-265">**Krzysztof Richardson. Opracowywanie mikrousług transakcyjnych przy użyciu agregacji, pochodzenia zdarzeń i CQRS — część 2** </span><span class="sxs-lookup"><span data-stu-id="69c17-265">**Chris Richardson. Developing Transactional Microservices Using Aggregates, Event Sourcing and CQRS - Part 2** </span></span>\
    <https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson>

- <span data-ttu-id="69c17-266">**Krzysztof Richardson. Wzorzec określania źródła zdarzeń** </span><span class="sxs-lookup"><span data-stu-id="69c17-266">**Chris Richardson. Event Sourcing pattern** </span></span>\
    <https://microservices.io/patterns/data/event-sourcing.html>

- <span data-ttu-id="69c17-267">**Wprowadzenie do określania źródła zdarzeń** </span><span class="sxs-lookup"><span data-stu-id="69c17-267">**Introducing Event Sourcing** </span></span>\
    <https://docs.microsoft.com/previous-versions/msp-n-p/jj591559(v=pandp.10)>

- <span data-ttu-id="69c17-268">**Baza danych magazynu zdarzeń**.</span><span class="sxs-lookup"><span data-stu-id="69c17-268">**Event Store database**.</span></span> <span data-ttu-id="69c17-269">Oficjalna lokacja.</span><span class="sxs-lookup"><span data-stu-id="69c17-269">Official site.</span></span> \
    <https://geteventstore.com/>

- <span data-ttu-id="69c17-270">**Patryk Nommensen. Zarządzanie danymi oparte na zdarzeniach dla mikrousług** </span><span class="sxs-lookup"><span data-stu-id="69c17-270">**Patrick Nommensen. Event-Driven Data Management for Microservices** </span></span>\
    <https://dzone.com/articles/event-driven-data-management-for-microservices-1>

- <span data-ttu-id="69c17-271">**Theorem zakończenia** </span><span class="sxs-lookup"><span data-stu-id="69c17-271">**The CAP Theorem** </span></span>\
    [https://en.wikipedia.org/wiki/CAP\_theorem](https://en.wikipedia.org/wiki/CAP_theorem)

- <span data-ttu-id="69c17-272">**Co to jest theorem CAP?**</span><span class="sxs-lookup"><span data-stu-id="69c17-272">**What is CAP Theorem?**</span></span> \
    <https://www.quora.com/What-Is-CAP-Theorem-1>

- <span data-ttu-id="69c17-273">**Podstawy spójności danych** </span><span class="sxs-lookup"><span data-stu-id="69c17-273">**Data Consistency Primer** </span></span>\
    <https://docs.microsoft.com/previous-versions/msp-n-p/dn589800(v=pandp.10)>

- <span data-ttu-id="69c17-274">**Rick Saling. Theorem zakończenia: Dlaczego "wszystko jest różne" z chmurą i Internetem** </span><span class="sxs-lookup"><span data-stu-id="69c17-274">**Rick Saling. The CAP Theorem: Why “Everything is Different” with the Cloud and Internet** </span></span>\
    <https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/>

- <span data-ttu-id="69c17-275">**Eric Brewer. Później, dwanaście lat: Jak zmieniono reguły** </span><span class="sxs-lookup"><span data-stu-id="69c17-275">**Eric Brewer. CAP Twelve Years Later: How the "Rules" Have Changed** </span></span>\
    <https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed>

- <span data-ttu-id="69c17-276">**Azure Service Bus. Komunikaty obsługiwane przez brokera: Wykrywanie duplikatów**  </span><span class="sxs-lookup"><span data-stu-id="69c17-276">**Azure Service Bus. Brokered Messaging: Duplicate Detection**  </span></span>\
    <https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25>

- <span data-ttu-id="69c17-277">**Przewodnik dotyczący niezawodności** (Dokumentacja RabbitMQ) </span><span class="sxs-lookup"><span data-stu-id="69c17-277">**Reliability Guide** (RabbitMQ documentation) </span></span>\
    [https://www.rabbitmq.com/reliability.html\#consumer](https://www.rabbitmq.com/reliability.html#consumer)

> [!div class="step-by-step"]
> <span data-ttu-id="69c17-278">[Poprzedni](rabbitmq-event-bus-development-test-environment.md)Następny
> [](test-aspnet-core-services-web-apps.md)</span><span class="sxs-lookup"><span data-stu-id="69c17-278">[Previous](rabbitmq-event-bus-development-test-environment.md)
[Next](test-aspnet-core-services-web-apps.md)</span></span>

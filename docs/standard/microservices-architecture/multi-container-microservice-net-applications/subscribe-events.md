---
title: Subskrybowanie zdarzeń
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Subskrybowanie zdarzeń
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: 5e53e0a3578c19b09f5327f444d1a5c013ad4cd9
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50194075"
---
# <a name="subscribing-to-events"></a><span data-ttu-id="af2b3-103">Subskrybowanie zdarzeń</span><span class="sxs-lookup"><span data-stu-id="af2b3-103">Subscribing to events</span></span>

<span data-ttu-id="af2b3-104">Pierwszym krokiem przy użyciu magistrali zdarzeń jest subskrybowanie mikrousług dla zdarzeń, które chcą otrzymywać.</span><span class="sxs-lookup"><span data-stu-id="af2b3-104">The first step for using the event bus is to subscribe the microservices to the events they want to receive.</span></span> <span data-ttu-id="af2b3-105">Który ma się odbywać w mikrousługach odbiorcy.</span><span class="sxs-lookup"><span data-stu-id="af2b3-105">That should be done in the receiver microservices.</span></span>

<span data-ttu-id="af2b3-106">Poniższy kod proste pokazuje, jakie poszczególne mikrousługi odbiornika należy zaimplementować podczas uruchamiania usługi (to znaczy w `Startup` klasy) tak subskrybuje zdarzenia go wymaga.</span><span class="sxs-lookup"><span data-stu-id="af2b3-106">The following simple code shows what each receiver microservice needs to implement when starting the service (that is, in the `Startup` class) so it subscribes to the events it needs.</span></span> <span data-ttu-id="af2b3-107">W tym przypadku `basket.api` mikrousług trzeba subskrybować `ProductPriceChangedIntegrationEvent` i `OrderStartedIntegrationEvent` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="af2b3-107">In this case, the `basket.api` microservice needs to subscribe to `ProductPriceChangedIntegrationEvent` and the `OrderStartedIntegrationEvent` messages.</span></span> 

<span data-ttu-id="af2b3-108">Na przykład podczas subskrybowania `ProductPriceChangedIntegrationEvent` zdarzeń, który sprawia, że mikrousług koszyka pamiętać o dowolnej zmiany cena produktu i umożliwia mu ostrzec użytkownika o zmianie, jeśli produktu znajduje się w koszyku użytkownika.</span><span class="sxs-lookup"><span data-stu-id="af2b3-108">For instance, when subscribing to the `ProductPriceChangedIntegrationEvent` event, that makes the basket microservice aware of any changes to the product price and lets it warn the user about the change if that product is in the user’s basket.</span></span>

```csharp
var eventBus = app.ApplicationServices.GetRequiredService<IEventBus>();

eventBus.Subscribe<ProductPriceChangedIntegrationEvent, 
                   ProductPriceChangedIntegrationEventHandler>();

eventBus.Subscribe<OrderStartedIntegrationEvent, 
                   OrderStartedIntegrationEventHandler>();

```

<span data-ttu-id="af2b3-109">Po uruchomieniu tego kodu, mikrousług subskrybent będzie nasłuchiwania za pośrednictwem kanałów RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="af2b3-109">After this code runs, the subscriber microservice will be listening through RabbitMQ channels.</span></span> <span data-ttu-id="af2b3-110">Po odebraniu komunikatu dowolnego typu ProductPriceChangedIntegrationEvent kod wywołuje program obsługi zdarzeń, który jest przekazywany do niego i przetwarza zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="af2b3-110">When any message of type ProductPriceChangedIntegrationEvent arrives, the code invokes the event handler that is passed to it and processes the event.</span></span>

## <a name="publishing-events-through-the-event-bus"></a><span data-ttu-id="af2b3-111">Publikowanie zdarzeń za pomocą magistrali zdarzeń</span><span class="sxs-lookup"><span data-stu-id="af2b3-111">Publishing events through the event bus</span></span>

<span data-ttu-id="af2b3-112">Na koniec nadawcy wiadomości (mikrousług origin) publikuje zdarzenia integracji z kodem podobny do poniższego przykładu.</span><span class="sxs-lookup"><span data-stu-id="af2b3-112">Finally, the message sender (origin microservice) publishes the integration events with code similar to the following example.</span></span> <span data-ttu-id="af2b3-113">(Jest to uproszczony przykład, który nie ma niepodzielność pod uwagę). Możesz również zaimplementować podobny kod zawsze wtedy, gdy zdarzenie musi być propagowane przez wiele mikrousług, zwykle zaraz po zatwierdzanie danych bądź transakcji z mikrousług źródła.</span><span class="sxs-lookup"><span data-stu-id="af2b3-113">(This is a simplified example that does not take atomicity into account.) You would implement similar code whenever an event must be propagated across multiple microservices, usually right after committing data or transactions from the origin microservice.</span></span>

<span data-ttu-id="af2b3-114">Po pierwsze obiekt implementacji magistrali zdarzeń (oparte na RabbitMQ lub oparte na usługi Service bus) zostałyby dodane w Konstruktorze kontrolera, zgodnie z poniższym kodem:</span><span class="sxs-lookup"><span data-stu-id="af2b3-114">First, the event bus implementation object (based on RabbitMQ or based on a service bus) would be injected at the controller constructor, as in the following code:</span></span>

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

<span data-ttu-id="af2b3-115">Następnie przy użyciu go z poziomu kontrolera metod, takich jak w metodzie UpdateProduct:</span><span class="sxs-lookup"><span data-stu-id="af2b3-115">Then you use it from your controller’s methods, like in the UpdateProduct method:</span></span>

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

<span data-ttu-id="af2b3-116">W tym przypadku mikrousług pochodzenia jest proste mikrousługi CRUD, ten kod jest umieszczana po prawej stronie do kontrolera internetowego interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="af2b3-116">In this case, since the origin microservice is a simple CRUD microservice, that code is placed right into a Web API controller.</span></span> 
 
<span data-ttu-id="af2b3-117">W bardziej zaawansowanych mikrousług, takich jak przy użyciu podejścia CQRS może być implementowany w `CommandHandler` klasy poziomu `Handle()` metody.</span><span class="sxs-lookup"><span data-stu-id="af2b3-117">In more advanced microservices, like when using CQRS approaches, it can be implemented in the `CommandHandler` class, within the `Handle()` method.</span></span> 


### <a name="designing-atomicity-and-resiliency-when-publishing-to-the-event-bus"></a><span data-ttu-id="af2b3-118">Projektowanie niepodzielność i zwiększa odporność podczas publikowania w magistrali zdarzeń</span><span class="sxs-lookup"><span data-stu-id="af2b3-118">Designing atomicity and resiliency when publishing to the event bus</span></span>

<span data-ttu-id="af2b3-119">Podczas publikowania zdarzenia integracji za pomocą rozproszonej obsługi wiadomości usługi Service bus zdarzeń, takich jak system, masz problem niepodzielne aktualizowanie oryginalnej bazy danych i publikowania zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="af2b3-119">When you publish integration events through a distributed messaging system like your event bus, you have the problem of atomically updating the original database and publishing an event.</span></span> <span data-ttu-id="af2b3-120">Na przykład uproszczony przykład przedstawionej wcześniej kod zapisuje dane w bazie danych po cena produktu jest zmienione, a następnie publikuje komunikat ProductPriceChangedIntegrationEvent.</span><span class="sxs-lookup"><span data-stu-id="af2b3-120">For instance, in the simplified example shown earlier, the code commits data to the database when the product price is changed and then publishes a ProductPriceChangedIntegrationEvent message.</span></span> <span data-ttu-id="af2b3-121">Początkowo może wyglądać istotne, że te dwie operacje być wykonywane atomowo.</span><span class="sxs-lookup"><span data-stu-id="af2b3-121">Initially, it might look essential that these two operations be performed atomically.</span></span> <span data-ttu-id="af2b3-122">Jednak jeśli używasz obejmujące transakcji rozproszonej bazy danych i komunikat brokera, tak jak w starszych systemów, takich jak [Microsoft usługi kolejkowania komunikatów (MSMQ)](https://msdn.microsoft.com/library/ms711472(v=vs.85).aspx), to nie jest zalecane z powodów opisanych przez [Kolejnego elementu teorii CAP](https://www.quora.com/What-Is-CAP-Theorem-1).</span><span class="sxs-lookup"><span data-stu-id="af2b3-122">However, if you are using a distributed transaction involving the database and the message broker, as you do in older systems like [Microsoft Message Queuing (MSMQ)](https://msdn.microsoft.com/library/ms711472(v=vs.85).aspx), this is not recommended for the reasons described by the [CAP theorem](https://www.quora.com/What-Is-CAP-Theorem-1).</span></span>

<span data-ttu-id="af2b3-123">Po prostu umożliwia mikrousług tworzenie systemów skalowalna i wysoko dostępna.</span><span class="sxs-lookup"><span data-stu-id="af2b3-123">Basically, you use microservices to build scalable and highly available systems.</span></span> <span data-ttu-id="af2b3-124">Upraszczanie nieco, kolejnego elementu teorii CAP mówi, że nie można utworzyć bazy danych (lub mikrousług, który jest właścicielem swój model) jest stale dostępna, zdecydowanie spójnych *i* odporne na żadnej partycji.</span><span class="sxs-lookup"><span data-stu-id="af2b3-124">Simplifying somewhat, the CAP theorem says that you cannot build a database (or a microservice that owns its model) that is continually available, strongly consistent, *and* tolerant to any partition.</span></span> <span data-ttu-id="af2b3-125">Musisz wybrać dwa z tych trzech właściwości.</span><span class="sxs-lookup"><span data-stu-id="af2b3-125">You must choose two of these three properties.</span></span>

<span data-ttu-id="af2b3-126">W opartych na mikrousługach architektury należy wybrać dostępności i na uszkodzenia i powinien cieszących silnej spójności.</span><span class="sxs-lookup"><span data-stu-id="af2b3-126">In microservices-based architectures, you should choose availability and tolerance, and you should deemphasize strong consistency.</span></span> <span data-ttu-id="af2b3-127">W związku z tym, w większości współczesnych aplikacji opartych na mikrousługach, zwykle nie chcesz używać transakcji rozproszonych, w przypadku komunikatów, w jak podczas implementowania [transakcje rozproszone](https://msdn.microsoft.com/library/ms978430.aspx#bdadotnetasync2_topic3c) oparte na transakcję rozproszoną Windows Koordynator (transakcji rozproszonych DTC) za pomocą [MSMQ](https://msdn.microsoft.com/library/ms711472(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="af2b3-127">Therefore, in most modern microservice-based applications, you usually do not want to use distributed transactions in messaging, as you do when you implement [distributed transactions](https://msdn.microsoft.com/library/ms978430.aspx#bdadotnetasync2_topic3c) based on the Windows Distributed Transaction Coordinator (DTC) with [MSMQ](https://msdn.microsoft.com/library/ms711472(v=vs.85).aspx).</span></span>

<span data-ttu-id="af2b3-128">Wróćmy do początkowego problemu i jego przykład.</span><span class="sxs-lookup"><span data-stu-id="af2b3-128">Let’s go back to the initial issue and its example.</span></span> <span data-ttu-id="af2b3-129">Jeśli usługa ulegnie awarii po zaktualizowaniu bazy danych (w tym przypadku kliknij prawym przyciskiem myszy, po wierszu kodu za pomocą \_kontekstu. SaveChangesAsync()), ale przed opublikowaniem zdarzenia integracji całego systemu może stać się niespójna.</span><span class="sxs-lookup"><span data-stu-id="af2b3-129">If the service crashes after the database is updated (in this case, right after the line of code with \_context.SaveChangesAsync()), but before the integration event is published, the overall system could become inconsistent.</span></span> <span data-ttu-id="af2b3-130">Może to być krytyczne dla działania, w zależności od operacji biznesowych, który masz do czynienia z.</span><span class="sxs-lookup"><span data-stu-id="af2b3-130">This might be business critical, depending on the specific business operation you are dealing with.</span></span>

<span data-ttu-id="af2b3-131">Jak wspomniano wcześniej, w sekcji architektury, może mieć różne podejścia do radzenia sobie z tym problemem:</span><span class="sxs-lookup"><span data-stu-id="af2b3-131">As mentioned earlier in the architecture section, you can have several approaches for dealing with this issue:</span></span>

-   <span data-ttu-id="af2b3-132">Przy użyciu pełnego [wzorzec określania źródła zdarzeń](https://msdn.microsoft.com/library/dn589792.aspx).</span><span class="sxs-lookup"><span data-stu-id="af2b3-132">Using the full [Event Sourcing pattern](https://msdn.microsoft.com/library/dn589792.aspx).</span></span>

-   <span data-ttu-id="af2b3-133">Za pomocą [wyszukiwania dziennik transakcji](https://www.scoop.it/t/sql-server-transaction-log-mining).</span><span class="sxs-lookup"><span data-stu-id="af2b3-133">Using [transaction log mining](https://www.scoop.it/t/sql-server-transaction-log-mining).</span></span>

-   <span data-ttu-id="af2b3-134">Za pomocą [wzorzec Skrzynka nadawcza](http://gistlabs.com/2014/05/the-outbox/).</span><span class="sxs-lookup"><span data-stu-id="af2b3-134">Using the [Outbox pattern](http://gistlabs.com/2014/05/the-outbox/).</span></span> <span data-ttu-id="af2b3-135">To jest tabela transakcji do przechowywania zdarzeń integracji (Rozszerzanie lokalnej transakcji).</span><span class="sxs-lookup"><span data-stu-id="af2b3-135">This is a transactional table to store the integration events (extending the local transaction).</span></span>

<span data-ttu-id="af2b3-136">W tym scenariuszu przy użyciu pełnej wzorca określania źródła zdarzeń (ES) jest jednym z najlepszych metod, jeśli nie \*\* najlepsze.</span><span class="sxs-lookup"><span data-stu-id="af2b3-136">For this scenario, using the full Event Sourcing (ES) pattern is one of the best approaches, if not *the* best.</span></span> <span data-ttu-id="af2b3-137">Jednak w wielu scenariuszach aplikacji, nie można zaimplementować pełnego ES.</span><span class="sxs-lookup"><span data-stu-id="af2b3-137">However, in many application scenarios, you might not be able to implement a full ES system.</span></span> <span data-ttu-id="af2b3-138">ES oznacza przechowywanie tylko domeny zdarzenia w transakcji bazy danych, zamiast przechowywania danych bieżącego stanu.</span><span class="sxs-lookup"><span data-stu-id="af2b3-138">ES means storing only domain events in your transactional database, instead of storing current state data.</span></span> <span data-ttu-id="af2b3-139">Przechowywanie tylko domeny zdarzenia może mieć wiele korzyści, takich jak o historii dostępności systemu i możliwość określenia stanu systemu w dowolnym momencie w przeszłości.</span><span class="sxs-lookup"><span data-stu-id="af2b3-139">Storing only domain events can have great benefits, such as having the history of your system available and being able to determine the state of your system at any moment in the past.</span></span> <span data-ttu-id="af2b3-140">Jednak implementacja pełnego ES wymaga Przekształcanie większość systemu i wprowadza wiele złożoności i wymagania.</span><span class="sxs-lookup"><span data-stu-id="af2b3-140">However, implementing a full ES system requires you to rearchitect most of your system and introduces many other complexities and requirements.</span></span> <span data-ttu-id="af2b3-141">Na przykład chcesz korzystać z bazy danych, które celowo do określania źródła zdarzeń, takich jak [Store zdarzeń](https://geteventstore.com/), lub korzystający z dokumentów bazy danych, takich jak usługi Azure Cosmos DB, bazy danych MongoDB, Cassandra, CouchDB lub RavenDB.</span><span class="sxs-lookup"><span data-stu-id="af2b3-141">For example, you would want to use a database specifically made for event sourcing, such as [Event Store](https://geteventstore.com/), or a document-oriented database such as Azure Cosmos DB, MongoDB, Cassandra, CouchDB, or RavenDB.</span></span> <span data-ttu-id="af2b3-142">ES jest to doskonałe podejście do problemu, ale nie najprostszym rozwiązaniu, chyba że znasz już określania źródła zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="af2b3-142">ES is a great approach for this problem, but not the easiest solution unless you are already familiar with event sourcing.</span></span>

<span data-ttu-id="af2b3-143">Możliwość użycia dziennika transakcji wyszukiwania początkowo wygląda bardzo przejrzysty.</span><span class="sxs-lookup"><span data-stu-id="af2b3-143">The option to use transaction log mining initially looks very transparent.</span></span> <span data-ttu-id="af2b3-144">Jednak aby użyć tego podejścia, mikrousług ma zostać dołączone do dziennika transakcji RDBMS, takie jak dziennik transakcji programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="af2b3-144">However, to use this approach, the microservice has to be coupled to your RDBMS transaction log, such as the SQL Server transaction log.</span></span> <span data-ttu-id="af2b3-145">Prawdopodobnie nie jest to pożądane.</span><span class="sxs-lookup"><span data-stu-id="af2b3-145">This is probably not desirable.</span></span> <span data-ttu-id="af2b3-146">Inny wadą jest to, że aktualizacje niskiego poziomu, rejestrowane w dzienniku transakcji może nie być tym samym poziomie, jako zdarzenia wysokiego poziomu integracji.</span><span class="sxs-lookup"><span data-stu-id="af2b3-146">Another drawback is that the low-level updates recorded in the transaction log might not be at the same level as your high-level integration events.</span></span> <span data-ttu-id="af2b3-147">Jeśli tak, proces odtwarzania te operacje dziennika transakcji może być trudne.</span><span class="sxs-lookup"><span data-stu-id="af2b3-147">If so, the process of reverse-engineering those transaction log operations can be difficult.</span></span>

<span data-ttu-id="af2b3-148">Zrównoważone podejście jest kombinacja tabela transakcji bazy danych i uproszczone wzorzec ES.</span><span class="sxs-lookup"><span data-stu-id="af2b3-148">A balanced approach is a mix of a transactional database table and a simplified ES pattern.</span></span> <span data-ttu-id="af2b3-149">Można użyć stanu, np. "gotowy do publikowania zdarzeń", który ustawia w oryginalnej zdarzenia podczas zatwierdzania integracji w tabeli zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="af2b3-149">You can use a state such as “ready to publish the event,” which you set in the original event when you commit it to the integration events table.</span></span> <span data-ttu-id="af2b3-150">Następnie spróbuj opublikować wydarzenie magistrali zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="af2b3-150">You then try to publish the event to the event bus.</span></span> <span data-ttu-id="af2b3-151">Jeśli akcja zdarzenia publikowania zakończy się powodzeniem, uruchom inną transakcję w usłudze pochodzenia i Przenieś stanu z "gotowych do opublikowania zdarzenia" "zdarzenie już opublikowane."</span><span class="sxs-lookup"><span data-stu-id="af2b3-151">If the publish-event action succeeds, you start another transaction in the origin service and move the state from “ready to publish the event” to “event already published.”</span></span>

<span data-ttu-id="af2b3-152">Jeśli akcja zdarzenia publikowania w zdarzeniu magistrali kończy się niepowodzeniem, dane nadal nie będą niespójne w mikrousługach pochodzenia — nadal jest oznaczona jako "gotowy do opublikowania zdarzenie", a w odniesieniu do pozostałych usług po pewnym czasie będzie spójny.</span><span class="sxs-lookup"><span data-stu-id="af2b3-152">If the publish-event action in the event bus fails, the data still will not be inconsistent within the origin microservice—it is still marked as “ready to publish the event,” and with respect to the rest of the services, it will eventually be consistent.</span></span> <span data-ttu-id="af2b3-153">Sprawdzanie stanu transakcji lub zdarzenia integracji zadań w tle zawsze może mieć.</span><span class="sxs-lookup"><span data-stu-id="af2b3-153">You can always have background jobs checking the state of the transactions or integration events.</span></span> <span data-ttu-id="af2b3-154">Jeśli zadanie znajdzie zdarzenia w stanie "gotowe do opublikowania zdarzenie", może użyć ponownie opublikować tego zdarzenia do magistrali zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="af2b3-154">If the job finds an event in the “ready to publish the event” state, it can try to republish that event to the event bus.</span></span>

<span data-ttu-id="af2b3-155">Należy zauważyć, że w przypadku tej metody, można są przechowywanie tylko zdarzenia integracji dla poszczególnych mikrousług źródła, a tylko zdarzenia, które chcesz komunikować się z innymi mikrousług lub systemy zewnętrzne.</span><span class="sxs-lookup"><span data-stu-id="af2b3-155">Notice that with this approach, you are persisting only the integration events for each origin microservice, and only the events that you want to communicate to other microservices or external systems.</span></span> <span data-ttu-id="af2b3-156">Z kolei w pełnym systemie ES, są przechowywane także wszystkie zdarzenia domeny.</span><span class="sxs-lookup"><span data-stu-id="af2b3-156">In contrast, in a full ES system, you store all domain events as well.</span></span>

<span data-ttu-id="af2b3-157">W związku z tym ta metoda o zrównoważonym obciążeniu jest uproszczony system ES.</span><span class="sxs-lookup"><span data-stu-id="af2b3-157">Therefore, this balanced approach is a simplified ES system.</span></span> <span data-ttu-id="af2b3-158">Należy uzyskać listę zdarzeń integracji z ich bieżącym stanem ("gotowe do opublikowania" i "opublikowany").</span><span class="sxs-lookup"><span data-stu-id="af2b3-158">You need a list of integration events with their current state (“ready to publish” versus “published”).</span></span> <span data-ttu-id="af2b3-159">Ale trzeba zaimplementować te stany zdarzenia integracji.</span><span class="sxs-lookup"><span data-stu-id="af2b3-159">But you only need to implement these states for the integration events.</span></span> <span data-ttu-id="af2b3-160">A w przypadku tej metody nie trzeba do przechowywania danych domeny jako zdarzenia w bazie danych transakcyjnych, tak jak w pełnym systemie ES.</span><span class="sxs-lookup"><span data-stu-id="af2b3-160">And in this approach, you do not need to store all your domain data as events in the transactional database, as you would in a full ES system.</span></span>

<span data-ttu-id="af2b3-161">Jeśli już używasz relacyjnej bazy danych, można użyć transakcji tabeli do przechowywania zdarzeń integracji.</span><span class="sxs-lookup"><span data-stu-id="af2b3-161">If you are already using a relational database, you can use a transactional table to store integration events.</span></span> <span data-ttu-id="af2b3-162">Aby osiągnąć niepodzielność w aplikacji, należy użyć dwuetapowego procesu na podstawie lokalnej transakcji.</span><span class="sxs-lookup"><span data-stu-id="af2b3-162">To achieve atomicity in your application, you use a two-step process based on local transactions.</span></span> <span data-ttu-id="af2b3-163">Zasadniczo masz tabelę IntegrationEvent w tej samej bazy danych, których mają jednostki domeny.</span><span class="sxs-lookup"><span data-stu-id="af2b3-163">Basically, you have an IntegrationEvent table in the same database where you have your domain entities.</span></span> <span data-ttu-id="af2b3-164">Ta tabela działa zgodnie z branży ubezpieczeniowej do osiągnięcia niepodzielność, tak że uwzględnisz utrwalone zdarzenia integracji w tej samej transakcji, które są w trakcie zatwierdzania danych domeny.</span><span class="sxs-lookup"><span data-stu-id="af2b3-164">That table works as an insurance for achieving atomicity so that you include persisted integration events into the same transactions that are committing your domain data.</span></span>

<span data-ttu-id="af2b3-165">Krok po kroku proces przechodzi następująco: aplikacja rozpocznie transakcji lokalnej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="af2b3-165">Step by step, the process goes like this: the application begins a local database transaction.</span></span> <span data-ttu-id="af2b3-166">Następnie aktualizuje stan jednostki domeny i wstawia zdarzenia do tabeli zdarzeń integracji.</span><span class="sxs-lookup"><span data-stu-id="af2b3-166">It then updates the state of your domain entities and inserts an event into the integration event table.</span></span> <span data-ttu-id="af2b3-167">Na koniec zatwierdzeń transakcji.</span><span class="sxs-lookup"><span data-stu-id="af2b3-167">Finally, it commits the transaction.</span></span> <span data-ttu-id="af2b3-168">Możesz uzyskać odpowiednią niepodzielność.</span><span class="sxs-lookup"><span data-stu-id="af2b3-168">You get the desired atomicity.</span></span>

<span data-ttu-id="af2b3-169">Implementując kroki publikowania zdarzenia, masz następujące opcje:</span><span class="sxs-lookup"><span data-stu-id="af2b3-169">When implementing the steps of publishing the events, you have these choices:</span></span>

-   <span data-ttu-id="af2b3-170">Publikowanie zdarzeń integracji od razu po zatwierdzanie transakcji i użyj innego transakcji lokalnej, aby oznaczyć zdarzenia w opublikowanej tabeli.</span><span class="sxs-lookup"><span data-stu-id="af2b3-170">Publish the integration event right after committing the transaction and use another local transaction to mark the events in the table as being published.</span></span> <span data-ttu-id="af2b3-171">Następnie skorzystaj z tabeli po prostu jako artefaktu do śledzenia zdarzeń integracji, w razie problemów z mikrousług zdalnego i wykonywać akcje kompensacyjne, na podstawie zdarzeń przechowywanych integracji.</span><span class="sxs-lookup"><span data-stu-id="af2b3-171">Then, use the table just as an artifact to track the integration events in case of issues in the remote microservices, and perform compensatory actions based on the stored integration events.</span></span>

-   <span data-ttu-id="af2b3-172">Skorzystaj z tabeli jako rodzaj kolejki.</span><span class="sxs-lookup"><span data-stu-id="af2b3-172">Use the table as a kind of queue.</span></span> <span data-ttu-id="af2b3-173">Wątek oddzielną aplikację lub procesu zapytania w tabeli zdarzeń integracji, publikuje w magistrali zdarzeń zdarzenia i następnie używa lokalnej transakcji do oznaczenia zdarzeń jako opublikowane.</span><span class="sxs-lookup"><span data-stu-id="af2b3-173">A separate application thread or process queries the integration event table, publishes the events to the event bus, and then uses a local transaction to mark the events as published.</span></span>

<span data-ttu-id="af2b3-174">Rysunek 8 do 22 przedstawiono architekturę jako pierwsza z tych metod.</span><span class="sxs-lookup"><span data-stu-id="af2b3-174">Figure 8-22 shows the architecture for the first of these approaches.</span></span>

![](./media/image23.png)

<span data-ttu-id="af2b3-175">**Rysunek 8 do 22**.</span><span class="sxs-lookup"><span data-stu-id="af2b3-175">**Figure 8-22**.</span></span> <span data-ttu-id="af2b3-176">Niepodzielność podczas publikowania zdarzeń w magistrali zdarzeń</span><span class="sxs-lookup"><span data-stu-id="af2b3-176">Atomicity when publishing events to the event bus</span></span>

<span data-ttu-id="af2b3-177">Podejście pokazano w rysunek 8 do 22 brakuje mikrousług dodatkowe procesu roboczego, który jest odpowiedzialny za sprawdzenie i Potwierdzanie Powodzenie zdarzenia opublikowanych integracji.</span><span class="sxs-lookup"><span data-stu-id="af2b3-177">The approach illustrated in Figure 8-22 is missing an additional worker microservice that is in charge of checking and confirming the success of the published integration events.</span></span> <span data-ttu-id="af2b3-178">W przypadku awarii tego dodatkowe sprawdzanie procesu roboczego mikrousług można odczytywać zdarzenia z tabeli i ich opublikowanie.</span><span class="sxs-lookup"><span data-stu-id="af2b3-178">In case of failure, that additional checker worker microservice can read events from the table and republish them.</span></span>

<span data-ttu-id="af2b3-179">Temat drugiego podejścia: skorzystaj z tabeli dziennika zdarzeń, co kolejka i zawsze używaj mikrousług procesu roboczego do publikowania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="af2b3-179">About the second approach: you use the EventLog table as a queue and always use a worker microservice to publish the messages.</span></span> <span data-ttu-id="af2b3-180">W takiej sytuacji proces Krewny, który jest wyświetlany w rysunek 8 – 23.</span><span class="sxs-lookup"><span data-stu-id="af2b3-180">In that case, the process is like that shown in Figure 8-23.</span></span> <span data-ttu-id="af2b3-181">Spowoduje to pokazanie dodatkowe mikrousług, a tabela jest pojedyncze źródło podczas publikowania zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="af2b3-181">This shows an additional microservice, and the table is the single source when publishing events.</span></span>

![](./media/image24.png)

<span data-ttu-id="af2b3-182">**Rysunek 8-23**.</span><span class="sxs-lookup"><span data-stu-id="af2b3-182">**Figure 8-23**.</span></span> <span data-ttu-id="af2b3-183">Niepodzielność podczas publikowania zdarzeń w magistrali zdarzeń z mikrousług procesu roboczego</span><span class="sxs-lookup"><span data-stu-id="af2b3-183">Atomicity when publishing events to the event bus with a worker microservice</span></span>

<span data-ttu-id="af2b3-184">Dla uproszczenia przykładowe w ramach aplikacji eShopOnContainers korzysta z pierwszej metody (bez dodatkowych procesów i z mikrousług sprawdzania) oraz magistrali zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="af2b3-184">For simplicity, the eShopOnContainers sample uses the first approach (with no additional processes or checker microservices) plus the event bus.</span></span> <span data-ttu-id="af2b3-185">Jednak ramach aplikacji eShopOnContainers nie obsługuje wszystkich przypadkach mogą występować awarie.</span><span class="sxs-lookup"><span data-stu-id="af2b3-185">However, the eShopOnContainers is not handling all possible failure cases.</span></span> <span data-ttu-id="af2b3-186">W rzeczywistej aplikacji wdrożonych w chmurze możesz wykorzystać fakt, że będzie problemów po pewnym czasie oraz musi implementować i sprawdź i Wyślij ponownie logiki.</span><span class="sxs-lookup"><span data-stu-id="af2b3-186">In a real application deployed to the cloud, you must embrace the fact that issues will arise eventually, and you must implement that check and resend logic.</span></span> <span data-ttu-id="af2b3-187">Przy użyciu tabeli jako kolejka może być bardziej efektywne niż pierwszego podejścia, jeśli masz tę tabelę jako pojedyncze źródło zdarzenia, publikując je za pośrednictwem magistrali zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="af2b3-187">Using the table as a queue can be more effective than the first approach if you have that table as a single source of events when publishing them through the event bus.</span></span>

### <a name="implementing-atomicity-when-publishing-integration-events-through-the-event-bus"></a><span data-ttu-id="af2b3-188">Implementowanie niepodzielność podczas publikowania zdarzeń integracja za pośrednictwem magistrali zdarzeń</span><span class="sxs-lookup"><span data-stu-id="af2b3-188">Implementing atomicity when publishing integration events through the event bus</span></span>

<span data-ttu-id="af2b3-189">Poniższy kod przedstawia sposób tworzenia pojedynczej transakcji obejmujących wiele obiektów typu DbContext — jednym kontekście związane z oryginalnych danych aktualizowana, a drugi kontekst związany z tabeli IntegrationEventLog.</span><span class="sxs-lookup"><span data-stu-id="af2b3-189">The following code shows how you can create a single transaction involving multiple DbContext objects—one context related to the original data being updated, and the second context related to the IntegrationEventLog table.</span></span>

<span data-ttu-id="af2b3-190">Pamiętaj, że transakcji w poniższym przykładowym kodzie nie będą odporne na błędy, jeśli połączeń z bazą danych wszelkie problemy w czasie, gdy kod jest uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="af2b3-190">Note that the transaction in the example code below will not be resilient if connections to the database have any issue at the time when the code is running.</span></span> <span data-ttu-id="af2b3-191">Może to nastąpić w chmurze systemów, takich jak bazy danych SQL Azure, które mogą przenosić bazy danych na serwerach.</span><span class="sxs-lookup"><span data-stu-id="af2b3-191">This can happen in cloud-based systems like Azure SQL DB, which might move databases across servers.</span></span> <span data-ttu-id="af2b3-192">Implementowanie odpornych transakcji w wielu kontekstach, dla [Implementowanie odpornych na błędy połączeń Entity Framework Core SQL](../implement-resilient-applications/implement-resilient-entity-framework-core-sql-connections.md) sekcję w dalszej części tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="af2b3-192">For implementing resilient transactions across multiple contexts, see the [Implementing resilient Entity Framework Core SQL connections](../implement-resilient-applications/implement-resilient-entity-framework-core-sql-connections.md) section later in this guide.</span></span>

<span data-ttu-id="af2b3-193">W celu uściślenia poniższy przykład pokazuje całego procesu w pojedynczy fragment kodu.</span><span class="sxs-lookup"><span data-stu-id="af2b3-193">For clarity, the following example shows the whole process in a single piece of code.</span></span> <span data-ttu-id="af2b3-194">Jednak implementacji w ramach aplikacji eShopOnContainers faktycznie zaprojektowane od nowa i podzielić tę logikę na wiele klas, więc jest łatwiejsze w konserwacji.</span><span class="sxs-lookup"><span data-stu-id="af2b3-194">However, the eShopOnContainers implementation is actually refactored and split this logic into multiple classes so it is easier to maintain.</span></span>

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

      // Publish the intergation event through the event bus
      _eventBus.Publish(priceChangedEvent); 

      integrationEventLogService.MarkEventAsPublishedAsync(
                                                priceChangedEvent); 
  }

  return Ok();
}

```

<span data-ttu-id="af2b3-195">Po utworzeniu zdarzenia integracji ProductPriceChangedIntegrationEvent transakcji, która przechowuje operacji pierwotnej domeny (Aktualizacja elementów katalogu) zawiera również trwałości zdarzenia w tabeli w dzienniku zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="af2b3-195">After the ProductPriceChangedIntegrationEvent integration event is created, the transaction that stores the original domain operation (update the catalog item) also includes the persistence of the event in the EventLog table.</span></span> <span data-ttu-id="af2b3-196">Dzięki temu pojedynczą transakcję i zawsze można sprawdzić, czy komunikaty o zdarzeniach zostały wysłane.</span><span class="sxs-lookup"><span data-stu-id="af2b3-196">This makes it a single transaction, and you will always be able to check whether event messages were sent.</span></span>

<span data-ttu-id="af2b3-197">Tabela dziennika zdarzeń jest aktualizowana niepodzielne operacji pierwotnej bazy danych przy użyciu lokalnej transakcji w tej samej bazie danych.</span><span class="sxs-lookup"><span data-stu-id="af2b3-197">The event log table is updated atomically with the original database operation, using a local transaction against the same database.</span></span> <span data-ttu-id="af2b3-198">Jeśli dowolne operacje kończą się niepowodzeniem, zostanie zgłoszony wyjątek i transakcji powoduje wycofanie zakończonych operacji, w związku z tym utrzymanie spójności między operacjami domeny i wysyłane komunikaty o zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="af2b3-198">If any of the operations fail, an exception is thrown and the transaction rolls back any completed operation, thus maintaining consistency between the domain operations and the event messages sent.</span></span>

### <a name="receiving-messages-from-subscriptions-event-handlers-in-receiver-microservices"></a><span data-ttu-id="af2b3-199">Odbieranie komunikatów z subskrypcji: obsługi zdarzeń w mikrousługach odbiorcy</span><span class="sxs-lookup"><span data-stu-id="af2b3-199">Receiving messages from subscriptions: event handlers in receiver microservices</span></span>

<span data-ttu-id="af2b3-200">Oprócz logiki subskrypcji zdarzeń musisz wdrożyć wewnętrzny kod procedury obsługi zdarzeń integracji (np. metody wywołania zwrotnego).</span><span class="sxs-lookup"><span data-stu-id="af2b3-200">In addition to the event subscription logic, you need to implement the internal code for the integration event handlers (like a callback method).</span></span> <span data-ttu-id="af2b3-201">Program obsługi zdarzeń określa się tam gdzie odbierane i przetwarzane komunikaty o zdarzeniach określonego typu.</span><span class="sxs-lookup"><span data-stu-id="af2b3-201">The event handler is where you specify where the event messages of a certain type will be received and processed.</span></span>

<span data-ttu-id="af2b3-202">Program obsługi zdarzeń otrzymuje najpierw wystąpienie zdarzenia z magistrali zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="af2b3-202">An event handler first receives an event instance from the event bus.</span></span> <span data-ttu-id="af2b3-203">Następnie klient zlokalizuje składników, które mają być przetwarzane powiązany z tym zdarzeniem integracji propagowanie i przechowywanie zdarzenia jako zmianę stanu w mikrousługach odbiorcy.</span><span class="sxs-lookup"><span data-stu-id="af2b3-203">Then it locates the component to be processed related to that integration event, propagating and persisting the event as a change in state in the receiver microservice.</span></span> <span data-ttu-id="af2b3-204">Na przykład jeśli zdarzenie ProductPriceChanged pochodzi z mikrousług wykazu, będzie odbywa się w mikrousługach koszyka i zmienia stan w tej mikrousług koszyka odbiornik, jak i, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="af2b3-204">For example, if a ProductPriceChanged event originates in the catalog microservice, it is handled in the basket microservice and changes the state in this receiver basket microservice as well, as shown in the following code.</span></span>

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

<span data-ttu-id="af2b3-205">Program obsługi zdarzeń musi sprawdzić, czy produkt istnieje we wszystkich wystąpieniach koszyka.</span><span class="sxs-lookup"><span data-stu-id="af2b3-205">The event handler needs to verify whether the product exists in any of the basket instances.</span></span> <span data-ttu-id="af2b3-206">Aktualizuje cenę dla każdego elementu wiersza powiązane koszyka.</span><span class="sxs-lookup"><span data-stu-id="af2b3-206">It also updates the item price for each related basket line item.</span></span> <span data-ttu-id="af2b3-207">Na koniec tworzy alert ma być wyświetlany dla użytkownika o zmianę ceny, jak pokazano w rysunek 8-24.</span><span class="sxs-lookup"><span data-stu-id="af2b3-207">Finally, it creates an alert to be displayed to the user about the price change, as shown in Figure 8-24.</span></span>

![](./media/image25.png)

<span data-ttu-id="af2b3-208">**Rysunek 8-24**.</span><span class="sxs-lookup"><span data-stu-id="af2b3-208">**Figure 8-24**.</span></span> <span data-ttu-id="af2b3-209">Wyświetlanie zmian cen elementów w koszyku jako przekazywane przez zdarzenia integracji</span><span class="sxs-lookup"><span data-stu-id="af2b3-209">Displaying an item price change in a basket, as communicated by integration events</span></span>

## <a name="idempotency-in-update-message-events"></a><span data-ttu-id="af2b3-210">Idempotentność w aktualizacji komunikat zdarzenia</span><span class="sxs-lookup"><span data-stu-id="af2b3-210">Idempotency in update message events</span></span>

<span data-ttu-id="af2b3-211">Ważnym aspektem zdarzeń komunikatów aktualizacji jest, czy Niepowodzenie w dowolnym momencie w komunikacie powinno spowodować komunikat, który ma zostać ponowiona.</span><span class="sxs-lookup"><span data-stu-id="af2b3-211">An important aspect of update message events is that a failure at any point in the communication should cause the message to be retried.</span></span> <span data-ttu-id="af2b3-212">W przeciwnym razie zadanie w tle może próbować publikowania zdarzenia, które zostało już opublikowane, tworząc warunki sytuacji wyścigu.</span><span class="sxs-lookup"><span data-stu-id="af2b3-212">Otherwise a background task might try to publish an event that has already been published, creating a race condition.</span></span> <span data-ttu-id="af2b3-213">Możesz należy się upewnić, że aktualizacje są idempotentne lub że zapewniają one wystarczającej ilości informacji, aby upewnić się, że można wykryć duplikat, odrzucić je i Wyślij ponownie tylko jedną odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="af2b3-213">You need to make sure that the updates are either idempotent or that they provide enough information to ensure that you can detect a duplicate, discard it, and send back only one response.</span></span>

<span data-ttu-id="af2b3-214">Jak wspomniano wcześniej, idempotentność oznacza, że operacja może zostać wykonana wiele razy bez wprowadzania zmian w wyniku.</span><span class="sxs-lookup"><span data-stu-id="af2b3-214">As noted earlier, idempotency means that an operation can be performed multiple times without changing the result.</span></span> <span data-ttu-id="af2b3-215">W środowisku obsługi komunikatów ponieważ podczas komunikowania się zdarzenia, zdarzenie jest idempotentna, jeśli móc go dostarczyć wiele razy bez wprowadzania zmian w wyniku dla mikrousług odbiorcy.</span><span class="sxs-lookup"><span data-stu-id="af2b3-215">In a messaging environment, as when communicating events, an event is idempotent if it can be delivered multiple times without changing the result for the receiver microservice.</span></span> <span data-ttu-id="af2b3-216">Może to być konieczne ze względu na charakter samego zdarzenia lub ze względu na sposób system obsługuje zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="af2b3-216">This may be necessary because of the nature of the event itself, or because of the way the system handles the event.</span></span> <span data-ttu-id="af2b3-217">Komunikat idempotentność jest ważne, w dowolnej aplikacji, która używa obsługi komunikatów, a nie tylko w aplikacji, które implementują wzorzec magistrali zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="af2b3-217">Message idempotency is important in any application that uses messaging, not just in applications that implement the event bus pattern.</span></span>

<span data-ttu-id="af2b3-218">Przykładem operacja idempotentna jest instrukcję SQL, który wstawia dane do tabeli, tylko wtedy, gdy dane nie są już w tabeli.</span><span class="sxs-lookup"><span data-stu-id="af2b3-218">An example of an idempotent operation is a SQL statement that inserts data into a table only if that data is not already in the table.</span></span> <span data-ttu-id="af2b3-219">Nie ma znaczenia, ile razy należy uruchomić, które wstawiają instrukcję SQL wynik będzie taki sam — tabela będzie zawierać tych danych.</span><span class="sxs-lookup"><span data-stu-id="af2b3-219">It does not matter how many times you run that insert SQL statement; the result will be the same—the table will contain that data.</span></span> <span data-ttu-id="af2b3-220">Idempotentności, np. to może być również niezbędne podczas pracy z komunikatów, jeśli potencjalnie być wysyłane komunikaty i w związku z tym przetworzonych więcej niż raz.</span><span class="sxs-lookup"><span data-stu-id="af2b3-220">Idempotency like this can also be necessary when dealing with messages if the messages could potentially be sent and therefore processed more than once.</span></span> <span data-ttu-id="af2b3-221">Na przykład jeśli Logika ponawiania powoduje, że nadawca wysyłać ten sam komunikat więcej niż jeden raz, należy się upewnić, że jest idempotentna.</span><span class="sxs-lookup"><span data-stu-id="af2b3-221">For instance, if retry logic causes a sender to send exactly the same message more than once, you need to make sure that it is idempotent.</span></span>

<span data-ttu-id="af2b3-222">Istnieje możliwość projektowania idempotentne wiadomości.</span><span class="sxs-lookup"><span data-stu-id="af2b3-222">It is possible to design idempotent messages.</span></span> <span data-ttu-id="af2b3-223">Na przykład można utworzyć zdarzenie i mówi "równa cena produktu \$25" zamiast "Dodaj \$5 z ceną produktu."</span><span class="sxs-lookup"><span data-stu-id="af2b3-223">For example, you can create an event that says "set the product price to \$25" instead of "add \$5 to the product price."</span></span> <span data-ttu-id="af2b3-224">Użytkownik może bezpiecznie przetworzyć pierwszy komunikat o dowolną liczbę razy, a wynik będzie taki sam.</span><span class="sxs-lookup"><span data-stu-id="af2b3-224">You could safely process the first message any number of times and the result will be the same.</span></span> <span data-ttu-id="af2b3-225">To nie dotyczy drugi komunikat.</span><span class="sxs-lookup"><span data-stu-id="af2b3-225">That is not true for the second message.</span></span> <span data-ttu-id="af2b3-226">Ale nawet w przypadku pierwszego, nie można przetworzyć pierwsze zdarzenie, ponieważ system może również wysłane nowszych zdarzeń zmian cen i spowoduje zastąpienie nową cenę.</span><span class="sxs-lookup"><span data-stu-id="af2b3-226">But even in the first case, you might not want to process the first event, because the system could also have sent a newer price-change event and you would be overwriting the new price.</span></span>

<span data-ttu-id="af2b3-227">Innym przykładem mogą być zdarzenie ukończone w kolejności propagowana do wielu subskrybentów.</span><span class="sxs-lookup"><span data-stu-id="af2b3-227">Another example might be an order-completed event being propagated to multiple subscribers.</span></span> <span data-ttu-id="af2b3-228">Ważne jest, informacji o zamówieniach zaktualizowania w innych systemach tylko raz, nawet jeśli występują zduplikowany komunikat zdarzenia dla tego samego zdarzenia ukończone w kolejności.</span><span class="sxs-lookup"><span data-stu-id="af2b3-228">It is important that order information be updated in other systems just once, even if there are duplicated message events for the same order-completed event.</span></span>

<span data-ttu-id="af2b3-229">Jest wygodną zapewnienie pewnego rodzaju tożsamości na zdarzenie, w którym można utworzyć logikę, która wymusza na to, że każde zdarzenie jest przetwarzany tylko raz na odbiorcy.</span><span class="sxs-lookup"><span data-stu-id="af2b3-229">It is convenient to have some kind of identity per event so that you can create logic that enforces that each event is processed only once per receiver.</span></span>

<span data-ttu-id="af2b3-230">Przetwarza komunikat jest idempotentna.</span><span class="sxs-lookup"><span data-stu-id="af2b3-230">Some message processing is inherently idempotent.</span></span> <span data-ttu-id="af2b3-231">Na przykład jeśli system generuje obraz miniatury, może nie ważne jest, ile razy komunikat dotyczący miniatury wygenerowanej jest przetwarzany; wynik jest miniatury są generowane i każdym razem, gdy są takie same.</span><span class="sxs-lookup"><span data-stu-id="af2b3-231">For example, if a system generates image thumbnails, it might not matter how many times the message about the generated thumbnail is processed; the outcome is that the thumbnails are generated and they are the same every time.</span></span> <span data-ttu-id="af2b3-232">Z drugiej strony operacje, takie jak wywołanie bramy płatności do obciążenia karty kredytowej może nie być idempotentne wcale.</span><span class="sxs-lookup"><span data-stu-id="af2b3-232">On the other hand, operations such as calling a payment gateway to charge a credit card may not be idempotent at all.</span></span> <span data-ttu-id="af2b3-233">W takich przypadkach musisz upewnić się, że przetwarzania wiadomości wielokrotnie efekt, których oczekujesz.</span><span class="sxs-lookup"><span data-stu-id="af2b3-233">In these cases, you need to ensure that processing a message multiple times has the effect that you expect.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="af2b3-234">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="af2b3-234">Additional resources</span></span>

-   <span data-ttu-id="af2b3-235">**Zapewniane idempotentności komunikat** (Podnagłówek na tej stronie) [*https://msdn.microsoft.com/library/jj591565.aspx*](https://msdn.microsoft.com/library/jj591565.aspx)</span><span class="sxs-lookup"><span data-stu-id="af2b3-235">**Honoring message idempotency** (subhead on this page) [*https://msdn.microsoft.com/library/jj591565.aspx*](https://msdn.microsoft.com/library/jj591565.aspx)</span></span>

## <a name="deduplicating-integration-event-messages"></a><span data-ttu-id="af2b3-236">Deduplikacja integracji komunikaty o zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="af2b3-236">Deduplicating integration event messages</span></span>

<span data-ttu-id="af2b3-237">Można należy upewnić się, że zdarzenia dotyczące wiadomości wysyłanych i przetwarzany tylko raz na subskrybenta na różnych poziomach.</span><span class="sxs-lookup"><span data-stu-id="af2b3-237">You can make sure that message events are sent and processed just once per subscriber at different levels.</span></span> <span data-ttu-id="af2b3-238">Jednym ze sposobów jest korzystać z funkcji deduplikacji, oferowane przez infrastruktura obsługi komunikatów, którego używasz.</span><span class="sxs-lookup"><span data-stu-id="af2b3-238">One way is to use a deduplication feature offered by the messaging infrastructure you are using.</span></span> <span data-ttu-id="af2b3-239">Innym jest zaimplementowanie logiki niestandardowej w mikrousługach swoje miejsce docelowe.</span><span class="sxs-lookup"><span data-stu-id="af2b3-239">Another is to implement custom logic in your destination microservice.</span></span> <span data-ttu-id="af2b3-240">Sprawdzanie poprawności na poziomie transportu i na poziomie aplikacji jest najlepsze rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="af2b3-240">Having validations at both the transport level and the application level is your best bet.</span></span>

### <a name="deduplicating-message-events-at-the-eventhandler-level"></a><span data-ttu-id="af2b3-241">Komunikat zdarzenia na poziomie EventHandler deduplikacja</span><span class="sxs-lookup"><span data-stu-id="af2b3-241">Deduplicating message events at the EventHandler level</span></span>

<span data-ttu-id="af2b3-242">Jednym ze sposobów, aby upewnić się, że zdarzenie jest przetwarzany tylko raz przez żadnego odbiorcy jest zaimplementowanie logiki określonych podczas przetwarzania zdarzeń komunikatów w procedurze obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="af2b3-242">One way to make sure that an event is processed just once by any receiver is by implementing certain logic when processing the message events in event handlers.</span></span> <span data-ttu-id="af2b3-243">Na przykład, to podejście użyte w ramach aplikacji eShopOnContainers aplikacji, jak widać w [kod źródłowy](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Controllers/OrdersController.cs) klasy OrdersController, gdy odbierze polecenie CreateOrderCommand.</span><span class="sxs-lookup"><span data-stu-id="af2b3-243">For example, that is the approach used in the eShopOnContainers application, as you can see in the [source code](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Controllers/OrdersController.cs) of the OrdersController class when it receives a CreateOrderCommand command.</span></span> <span data-ttu-id="af2b3-244">(W tym przypadku użyjemy polecenia żądanie HTTP nie oparta na komunikatach polecenia, ale logiki, musisz wprowadzić idempotentne oparta na komunikatach polecenie jest podobne).</span><span class="sxs-lookup"><span data-stu-id="af2b3-244">(In this case we use an HTTP request command, not a message-based command, but the logic you need to make a message-based command idempotent is similar.)</span></span>

### <a name="deduplicating-messages-when-using-rabbitmq"></a><span data-ttu-id="af2b3-245">Deduplikacja wiadomości w przypadku korzystania z oprogramowania RabbitMQ</span><span class="sxs-lookup"><span data-stu-id="af2b3-245">Deduplicating messages when using RabbitMQ</span></span>

<span data-ttu-id="af2b3-246">Gdy wystąpi sporadyczne awarie sieci, mogą być zduplikowane komunikaty, a odbiorcy wiadomości musi być gotowy do obsługi tych zduplikowane komunikaty.</span><span class="sxs-lookup"><span data-stu-id="af2b3-246">When intermittent network failures happen, messages can be duplicated, and the message receiver must be ready to handle these duplicated messages.</span></span> <span data-ttu-id="af2b3-247">Jeśli to możliwe odbiorniki powinna obsługiwać komunikaty w sposób idempotentne, który jest lepsze niż jawną obsługę je z włączoną funkcją deduplikacji.</span><span class="sxs-lookup"><span data-stu-id="af2b3-247">If possible, receivers should handle messages in an idempotent way, which is better than explicitly handling them with deduplication.</span></span>

<span data-ttu-id="af2b3-248">Zgodnie z opisem w [dokumentacji oprogramowania RabbitMQ](https://www.rabbitmq.com/reliability.html#consumer), "Jeśli komunikat jest dostarczany do odbiorców, a następnie ponownie umieszczone w kolejce (ponieważ nie zostało potwierdzone, zanim konsumenta połączenie zostało przerwane, na przykład), a następnie RabbitMQ ustawi flagi redelivered na go po dostarczeniu ponownie (czy do tego samego użytkownika lub inną).</span><span class="sxs-lookup"><span data-stu-id="af2b3-248">According to the [RabbitMQ documentation](https://www.rabbitmq.com/reliability.html#consumer), “If a message is delivered to a consumer and then requeued (because it was not acknowledged before the consumer connection dropped, for example) then RabbitMQ will set the redelivered flag on it when it is delivered again (whether to the same consumer or a different one).</span></span>

<span data-ttu-id="af2b3-249">Jeśli flaga "redelivered" jest ustawiona, odbiorca musi uwzględniać który, ponieważ komunikat może być już zostały przetworzone.</span><span class="sxs-lookup"><span data-stu-id="af2b3-249">If the “redelivered” flag is set, the receiver must take that into account, because the message might already have been processed.</span></span> <span data-ttu-id="af2b3-250">Ale nie jest gwarantowana; komunikat, być może nigdy nie osiągnięto odbiornika od jego brokera komunikatów, prawdopodobnie z powodu problemów z siecią.</span><span class="sxs-lookup"><span data-stu-id="af2b3-250">But that is not guaranteed; the message might never have reached the receiver after it left the message broker, perhaps because of network issues.</span></span> <span data-ttu-id="af2b3-251">Z drugiej strony Jeśli nie ustawiono flagi "redelivered", ma żadnej gwarancji, że wiadomość nie została wysłana więcej niż jeden raz.</span><span class="sxs-lookup"><span data-stu-id="af2b3-251">On the other hand, if the “redelivered” flag is not set, it is guaranteed that the message has not been sent more than once.</span></span> <span data-ttu-id="af2b3-252">W związku z tym odbiorca musi deduplikacja wiadomości lub przetwarzania komunikatów w sposób idempotentne, tylko wtedy, gdy flaga "redelivered" jest ustawiona w komunikacie.</span><span class="sxs-lookup"><span data-stu-id="af2b3-252">Therefore, the receiver needs to deduplicate messages or process messages in an idempotent way only if the “redelivered” flag is set in the message.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="af2b3-253">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="af2b3-253">Additional resources</span></span>

-   <span data-ttu-id="af2b3-254">**Rozwidlone w ramach aplikacji eShopOnContainers przy użyciu NServiceBus (konkretnego oprogramowania)**
    [*https://go.particular.net/eShopOnContainers*](https://go.particular.net/eShopOnContainers)</span><span class="sxs-lookup"><span data-stu-id="af2b3-254">**Forked eShopOnContainers using NServiceBus (Particular Software)**
[*https://go.particular.net/eShopOnContainers*](https://go.particular.net/eShopOnContainers)</span></span>

-   <span data-ttu-id="af2b3-255">**Aktivita typu EventDriven komunikatów**
    [*http://soapatterns.org/design\_patterns/event\_driven\_messaging*](http://soapatterns.org/design_patterns/event_driven_messaging)</span><span class="sxs-lookup"><span data-stu-id="af2b3-255">**Event Driven Messaging**
[*http://soapatterns.org/design\_patterns/event\_driven\_messaging*](http://soapatterns.org/design_patterns/event_driven_messaging)</span></span>

-   <span data-ttu-id="af2b3-256">**Jimmy Bogard. Refaktoryzacja kierunku odporności: Ocena sprzężenia**
    [*https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/*](https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/)</span><span class="sxs-lookup"><span data-stu-id="af2b3-256">**Jimmy Bogard. Refactoring Towards Resilience: Evaluating Coupling**
[*https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/*](https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/)</span></span>

-   <span data-ttu-id="af2b3-257">**Publikowanie/subskrybowanie kanałów**
    [*https://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html*](https://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html)</span><span class="sxs-lookup"><span data-stu-id="af2b3-257">**Publish-Subscribe channel**
[*https://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html*](https://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html)</span></span>

-   <span data-ttu-id="af2b3-258">**Komunikacja między ograniczone konteksty**
    [*https://msdn.microsoft.com/library/jj591572.aspx*](https://msdn.microsoft.com/library/jj591572.aspx)</span><span class="sxs-lookup"><span data-stu-id="af2b3-258">**Communicating Between Bounded Contexts**
[*https://msdn.microsoft.com/library/jj591572.aspx*](https://msdn.microsoft.com/library/jj591572.aspx)</span></span>

-   <span data-ttu-id="af2b3-259">**Spójność ostateczna**
    [*https://en.wikipedia.org/wiki/Eventual\_consistency*](https://en.wikipedia.org/wiki/Eventual_consistency)</span><span class="sxs-lookup"><span data-stu-id="af2b3-259">**Eventual Consistency**
[*https://en.wikipedia.org/wiki/Eventual\_consistency*](https://en.wikipedia.org/wiki/Eventual_consistency)</span></span>

-   <span data-ttu-id="af2b3-260">**Philip Brown. Integrowanie strategii ograniczone konteksty**
    [*http://culttt.com/2014/11/26/strategies-integrating-bounded-contexts/*](http://culttt.com/2014/11/26/strategies-integrating-bounded-contexts/)</span><span class="sxs-lookup"><span data-stu-id="af2b3-260">**Philip Brown. Strategies for Integrating Bounded Contexts**
[*http://culttt.com/2014/11/26/strategies-integrating-bounded-contexts/*](http://culttt.com/2014/11/26/strategies-integrating-bounded-contexts/)</span></span>

-   <span data-ttu-id="af2b3-261">**Chris Leonard. Tworzenie Mikrousług transakcyjne przy użyciu wartości zagregowane, określania źródła zdarzeń i podejście CQRS — część 2**
    [*https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson*](https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson)</span><span class="sxs-lookup"><span data-stu-id="af2b3-261">**Chris Richardson. Developing Transactional Microservices Using Aggregates, Event Sourcing and CQRS - Part 2**
[*https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson*](https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson)</span></span>

-   <span data-ttu-id="af2b3-262">**Chris Leonard. Wzorzec określania źródła zdarzeń**
    [*https://microservices.io/patterns/data/event-sourcing.html*](https://microservices.io/patterns/data/event-sourcing.html)</span><span class="sxs-lookup"><span data-stu-id="af2b3-262">**Chris Richardson. Event Sourcing pattern**
[*https://microservices.io/patterns/data/event-sourcing.html*](https://microservices.io/patterns/data/event-sourcing.html)</span></span>

-   <span data-ttu-id="af2b3-263">**Wprowadzenie do określania źródła zdarzeń**
    [*https://msdn.microsoft.com/library/jj591559.aspx*](https://msdn.microsoft.com/library/jj591559.aspx)</span><span class="sxs-lookup"><span data-stu-id="af2b3-263">**Introducing Event Sourcing**
[*https://msdn.microsoft.com/library/jj591559.aspx*](https://msdn.microsoft.com/library/jj591559.aspx)</span></span>

-   <span data-ttu-id="af2b3-264">**Bazy danych zdarzeń Store**.</span><span class="sxs-lookup"><span data-stu-id="af2b3-264">**Event Store database**.</span></span> <span data-ttu-id="af2b3-265">Oficjalna witryna.</span><span class="sxs-lookup"><span data-stu-id="af2b3-265">Official site.</span></span>
    [*https://geteventstore.com/*](https://geteventstore.com/)

-   <span data-ttu-id="af2b3-266">**Patrick Nommensen. Zarządzanie oparte na zdarzeniach danych dla Mikrousług**
    \*<https://dzone.com/articles/event-driven-data-management-for-microservices-1> \*</span><span class="sxs-lookup"><span data-stu-id="af2b3-266">**Patrick Nommensen. Event-Driven Data Management for Microservices**
\*<https://dzone.com/articles/event-driven-data-management-for-microservices-1> \*</span></span>

-   <span data-ttu-id="af2b3-267">**Kolejnego elementu teorii CAP**
    [*https://en.wikipedia.org/wiki/CAP\_theorem*](https://en.wikipedia.org/wiki/CAP_theorem)</span><span class="sxs-lookup"><span data-stu-id="af2b3-267">**The CAP Theorem**
[*https://en.wikipedia.org/wiki/CAP\_theorem*](https://en.wikipedia.org/wiki/CAP_theorem)</span></span>

-   <span data-ttu-id="af2b3-268">**Co to jest kolejnego elementu teorii CAP?**
    [*https://www.quora.com/What-Is-CAP-Theorem-1*](https://www.quora.com/What-Is-CAP-Theorem-1)</span><span class="sxs-lookup"><span data-stu-id="af2b3-268">**What is CAP Theorem?**
[*https://www.quora.com/What-Is-CAP-Theorem-1*](https://www.quora.com/What-Is-CAP-Theorem-1)</span></span>

-   <span data-ttu-id="af2b3-269">**Podstawy spójności danych**
    [*https://msdn.microsoft.com/library/dn589800.aspx*](https://msdn.microsoft.com/library/dn589800.aspx)</span><span class="sxs-lookup"><span data-stu-id="af2b3-269">**Data Consistency Primer**
[*https://msdn.microsoft.com/library/dn589800.aspx*](https://msdn.microsoft.com/library/dn589800.aspx)</span></span>

-   <span data-ttu-id="af2b3-270">**Rick Saling. Kolejnego elementu teorii CAP: Dlaczego "Wszystko, co jest różne" chmura i Internet**
    [*https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/*](https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/)</span><span class="sxs-lookup"><span data-stu-id="af2b3-270">**Rick Saling. The CAP Theorem: Why “Everything is Different” with the Cloud and Internet**
[*https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/*](https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/)</span></span>

-   <span data-ttu-id="af2b3-271">**Eric Brewera. LIMIT później dwunastu lat: jak "Zasady" zostały zmienione**
    [*https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed*](https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed)</span><span class="sxs-lookup"><span data-stu-id="af2b3-271">**Eric Brewer. CAP Twelve Years Later: How the "Rules" Have Changed**
[*https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed*](https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed)</span></span>

-   <span data-ttu-id="af2b3-272">**Udział w transakcji zewnętrznych (DTC)** (MSMQ) [*https://msdn.microsoft.com/library/ms978430.aspx\#bdadotnetasync2\_topic3c*](https://msdn.microsoft.com/library/ms978430.aspx%23bdadotnetasync2_topic3c)</span><span class="sxs-lookup"><span data-stu-id="af2b3-272">**Participating in External (DTC) Transactions** (MSMQ) [*https://msdn.microsoft.com/library/ms978430.aspx\#bdadotnetasync2\_topic3c*](https://msdn.microsoft.com/library/ms978430.aspx%23bdadotnetasync2_topic3c)</span></span>

-   <span data-ttu-id="af2b3-273">**Azure Service Bus. Komunikaty obsługiwane przez brokera: Wykrywanie duplikatów**
    [*https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25*](https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25)</span><span class="sxs-lookup"><span data-stu-id="af2b3-273">**Azure Service Bus. Brokered Messaging: Duplicate Detection**
[*https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25*](https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25)</span></span>

-   <span data-ttu-id="af2b3-274">**Przewodnik niezawodność** (dokumentacja RabbitMQ) [*https://www.rabbitmq.com/reliability.html\#consumer*](https://www.rabbitmq.com/reliability.html%23consumer)</span><span class="sxs-lookup"><span data-stu-id="af2b3-274">**Reliability Guide** (RabbitMQ documentation) [*https://www.rabbitmq.com/reliability.html\#consumer*](https://www.rabbitmq.com/reliability.html%23consumer)</span></span>




>[!div class="step-by-step"]
<span data-ttu-id="af2b3-275">[Poprzednie](rabbitmq-event-bus-development-test-environment.md)
[dalej](test-aspnet-core-services-web-apps.md)</span><span class="sxs-lookup"><span data-stu-id="af2b3-275">[Previous](rabbitmq-event-bus-development-test-environment.md)
[Next](test-aspnet-core-services-web-apps.md)</span></span>

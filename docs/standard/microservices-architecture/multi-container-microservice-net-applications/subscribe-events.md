---
title: Subskrybowanie zdarzeń
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Poznaj szczegóły publikowanie i subskrybowanie zdarzeń integracji.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/02/2018
ms.openlocfilehash: d32c643e553dfe3ce52e3e2ce8aaf1ea3a296de6
ms.sourcegitcommit: 35316b768394e56087483cde93f854ba607b63bc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/26/2018
ms.locfileid: "52297319"
---
# <a name="subscribing-to-events"></a><span data-ttu-id="165d0-103">Subskrybowanie zdarzeń</span><span class="sxs-lookup"><span data-stu-id="165d0-103">Subscribing to events</span></span>

<span data-ttu-id="165d0-104">Pierwszym krokiem przy użyciu magistrali zdarzeń jest subskrybowanie mikrousług dla zdarzeń, które chcą otrzymywać.</span><span class="sxs-lookup"><span data-stu-id="165d0-104">The first step for using the event bus is to subscribe the microservices to the events they want to receive.</span></span> <span data-ttu-id="165d0-105">Który ma się odbywać w mikrousługach odbiorcy.</span><span class="sxs-lookup"><span data-stu-id="165d0-105">That should be done in the receiver microservices.</span></span>

<span data-ttu-id="165d0-106">Poniższy kod proste pokazuje, jakie poszczególne mikrousługi odbiornika należy zaimplementować podczas uruchamiania usługi (to znaczy w `Startup` klasy) tak subskrybuje zdarzenia go wymaga.</span><span class="sxs-lookup"><span data-stu-id="165d0-106">The following simple code shows what each receiver microservice needs to implement when starting the service (that is, in the `Startup` class) so it subscribes to the events it needs.</span></span> <span data-ttu-id="165d0-107">W tym przypadku `basket.api` mikrousług trzeba subskrybować `ProductPriceChangedIntegrationEvent` i `OrderStartedIntegrationEvent` wiadomości.</span><span class="sxs-lookup"><span data-stu-id="165d0-107">In this case, the `basket.api` microservice needs to subscribe to `ProductPriceChangedIntegrationEvent` and the `OrderStartedIntegrationEvent` messages.</span></span> 

<span data-ttu-id="165d0-108">Na przykład podczas subskrybowania `ProductPriceChangedIntegrationEvent` zdarzeń, który sprawia, że mikrousług koszyka pamiętać o dowolnej zmiany cena produktu i umożliwia mu ostrzec użytkownika o zmianie, jeśli produktu znajduje się w koszyku użytkownika.</span><span class="sxs-lookup"><span data-stu-id="165d0-108">For instance, when subscribing to the `ProductPriceChangedIntegrationEvent` event, that makes the basket microservice aware of any changes to the product price and lets it warn the user about the change if that product is in the user’s basket.</span></span>

```csharp
var eventBus = app.ApplicationServices.GetRequiredService<IEventBus>();

eventBus.Subscribe<ProductPriceChangedIntegrationEvent, 
                   ProductPriceChangedIntegrationEventHandler>();

eventBus.Subscribe<OrderStartedIntegrationEvent, 
                   OrderStartedIntegrationEventHandler>();

```

<span data-ttu-id="165d0-109">Po uruchomieniu tego kodu, mikrousług subskrybent będzie nasłuchiwania za pośrednictwem kanałów RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="165d0-109">After this code runs, the subscriber microservice will be listening through RabbitMQ channels.</span></span> <span data-ttu-id="165d0-110">Po odebraniu komunikatu dowolnego typu ProductPriceChangedIntegrationEvent kod wywołuje program obsługi zdarzeń, który jest przekazywany do niego i przetwarza zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="165d0-110">When any message of type ProductPriceChangedIntegrationEvent arrives, the code invokes the event handler that is passed to it and processes the event.</span></span>

## <a name="publishing-events-through-the-event-bus"></a><span data-ttu-id="165d0-111">Publikowanie zdarzeń za pomocą magistrali zdarzeń</span><span class="sxs-lookup"><span data-stu-id="165d0-111">Publishing events through the event bus</span></span>

<span data-ttu-id="165d0-112">Na koniec nadawcy wiadomości (mikrousług origin) publikuje zdarzenia integracji z kodem podobny do poniższego przykładu.</span><span class="sxs-lookup"><span data-stu-id="165d0-112">Finally, the message sender (origin microservice) publishes the integration events with code similar to the following example.</span></span> <span data-ttu-id="165d0-113">(Jest to uproszczony przykład, który nie ma niepodzielność pod uwagę). Możesz również zaimplementować podobny kod zawsze wtedy, gdy zdarzenie musi być propagowane przez wiele mikrousług, zwykle zaraz po zatwierdzanie danych bądź transakcji z mikrousług źródła.</span><span class="sxs-lookup"><span data-stu-id="165d0-113">(This is a simplified example that does not take atomicity into account.) You would implement similar code whenever an event must be propagated across multiple microservices, usually right after committing data or transactions from the origin microservice.</span></span>

<span data-ttu-id="165d0-114">Po pierwsze obiekt implementacji magistrali zdarzeń (oparte na RabbitMQ lub oparte na usługi Service bus) zostałyby dodane w Konstruktorze kontrolera, zgodnie z poniższym kodem:</span><span class="sxs-lookup"><span data-stu-id="165d0-114">First, the event bus implementation object (based on RabbitMQ or based on a service bus) would be injected at the controller constructor, as in the following code:</span></span>

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

<span data-ttu-id="165d0-115">Następnie przy użyciu go z poziomu kontrolera metod, takich jak w metodzie UpdateProduct:</span><span class="sxs-lookup"><span data-stu-id="165d0-115">Then you use it from your controller’s methods, like in the UpdateProduct method:</span></span>

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

<span data-ttu-id="165d0-116">W tym przypadku mikrousług pochodzenia jest proste mikrousługi CRUD, ten kod jest umieszczana po prawej stronie do kontrolera internetowego interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="165d0-116">In this case, since the origin microservice is a simple CRUD microservice, that code is placed right into a Web API controller.</span></span> 
 
<span data-ttu-id="165d0-117">W bardziej zaawansowanych mikrousług, takich jak przy użyciu podejścia CQRS może być implementowany w `CommandHandler` klasy poziomu `Handle()` metody.</span><span class="sxs-lookup"><span data-stu-id="165d0-117">In more advanced microservices, like when using CQRS approaches, it can be implemented in the `CommandHandler` class, within the `Handle()` method.</span></span> 

### <a name="designing-atomicity-and-resiliency-when-publishing-to-the-event-bus"></a><span data-ttu-id="165d0-118">Projektowanie niepodzielność i zwiększa odporność podczas publikowania w magistrali zdarzeń</span><span class="sxs-lookup"><span data-stu-id="165d0-118">Designing atomicity and resiliency when publishing to the event bus</span></span>

<span data-ttu-id="165d0-119">Podczas publikowania zdarzenia integracji za pomocą rozproszonej obsługi wiadomości usługi Service bus zdarzeń, takich jak system, masz problem niepodzielne aktualizowanie oryginalnej bazy danych i publikowanie zdarzenia (czyli zarówno zakończenie operacji lub żadna z nich).</span><span class="sxs-lookup"><span data-stu-id="165d0-119">When you publish integration events through a distributed messaging system like your event bus, you have the problem of atomically updating the original database and publishing an event (that is, either both operations complete or none of them).</span></span> <span data-ttu-id="165d0-120">Na przykład uproszczony przykład przedstawionej wcześniej kod zapisuje dane w bazie danych po cena produktu jest zmienione, a następnie publikuje komunikat ProductPriceChangedIntegrationEvent.</span><span class="sxs-lookup"><span data-stu-id="165d0-120">For instance, in the simplified example shown earlier, the code commits data to the database when the product price is changed and then publishes a ProductPriceChangedIntegrationEvent message.</span></span> <span data-ttu-id="165d0-121">Początkowo może wyglądać istotne, że te dwie operacje być wykonywane atomowo.</span><span class="sxs-lookup"><span data-stu-id="165d0-121">Initially, it might look essential that these two operations be performed atomically.</span></span> <span data-ttu-id="165d0-122">Jednak jeśli używasz obejmujące transakcji rozproszonej bazy danych i komunikat brokera, tak jak w starszych systemów, takich jak [Microsoft usługi kolejkowania komunikatów (MSMQ)](https://msdn.microsoft.com/library/ms711472\(v=vs.85\).aspx), to nie jest zalecane z powodów opisanych przez [Kolejnego elementu teorii CAP](https://www.quora.com/What-Is-CAP-Theorem-1).</span><span class="sxs-lookup"><span data-stu-id="165d0-122">However, if you are using a distributed transaction involving the database and the message broker, as you do in older systems like [Microsoft Message Queuing (MSMQ)](https://msdn.microsoft.com/library/ms711472\(v=vs.85\).aspx), this is not recommended for the reasons described by the [CAP theorem](https://www.quora.com/What-Is-CAP-Theorem-1).</span></span>

<span data-ttu-id="165d0-123">Po prostu umożliwia mikrousług tworzenie systemów skalowalna i wysoko dostępna.</span><span class="sxs-lookup"><span data-stu-id="165d0-123">Basically, you use microservices to build scalable and highly available systems.</span></span> <span data-ttu-id="165d0-124">Upraszczanie nieco, kolejnego elementu teorii CAP mówi, że nie można utworzyć bazę danych (rozproszone) (lub mikrousług, który jest właścicielem swój model) jest stale dostępna, zdecydowanie spójnych *i* odporne na żadnej partycji.</span><span class="sxs-lookup"><span data-stu-id="165d0-124">Simplifying somewhat, the CAP theorem says that you cannot build a (distributed) database (or a microservice that owns its model) that is continually available, strongly consistent, *and* tolerant to any partition.</span></span> <span data-ttu-id="165d0-125">Musisz wybrać dwa z tych trzech właściwości.</span><span class="sxs-lookup"><span data-stu-id="165d0-125">You must choose two of these three properties.</span></span>

<span data-ttu-id="165d0-126">W opartych na mikrousługach architektury należy wybrać dostępności i na uszkodzenia i powinien cieszących silnej spójności.</span><span class="sxs-lookup"><span data-stu-id="165d0-126">In microservices-based architectures, you should choose availability and tolerance, and you should deemphasize strong consistency.</span></span> <span data-ttu-id="165d0-127">W związku z tym, w większości współczesnych aplikacji opartych na mikrousługach, zwykle nie chcesz używać transakcji rozproszonych, w przypadku komunikatów, w jak podczas implementowania [transakcje rozproszone](https://msdn.microsoft.com/library/ms681205\(v=vs.85\).aspx) oparte na transakcję rozproszoną Windows Koordynator (transakcji rozproszonych DTC) za pomocą [MSMQ](https://msdn.microsoft.com/library/ms711472\(v=vs.85\).aspx).</span><span class="sxs-lookup"><span data-stu-id="165d0-127">Therefore, in most modern microservice-based applications, you usually do not want to use distributed transactions in messaging, as you do when you implement [distributed transactions](https://msdn.microsoft.com/library/ms681205\(v=vs.85\).aspx) based on the Windows Distributed Transaction Coordinator (DTC) with [MSMQ](https://msdn.microsoft.com/library/ms711472\(v=vs.85\).aspx).</span></span>

<span data-ttu-id="165d0-128">Wróćmy do początkowego problemu i jego przykład.</span><span class="sxs-lookup"><span data-stu-id="165d0-128">Let’s go back to the initial issue and its example.</span></span> <span data-ttu-id="165d0-129">Jeśli usługa ulegnie awarii po zaktualizowaniu bazy danych (w tym przypadku kliknij prawym przyciskiem myszy, po wierszu kodu za pomocą \_kontekstu. SaveChangesAsync()), ale przed opublikowaniem zdarzenia integracji całego systemu może stać się niespójna.</span><span class="sxs-lookup"><span data-stu-id="165d0-129">If the service crashes after the database is updated (in this case, right after the line of code with \_context.SaveChangesAsync()), but before the integration event is published, the overall system could become inconsistent.</span></span> <span data-ttu-id="165d0-130">Może to być krytyczne dla działania, w zależności od operacji biznesowych, który masz do czynienia z.</span><span class="sxs-lookup"><span data-stu-id="165d0-130">This might be business critical, depending on the specific business operation you are dealing with.</span></span>

<span data-ttu-id="165d0-131">Jak wspomniano wcześniej, w sekcji architektury, może mieć różne podejścia do radzenia sobie z tym problemem:</span><span class="sxs-lookup"><span data-stu-id="165d0-131">As mentioned earlier in the architecture section, you can have several approaches for dealing with this issue:</span></span>

-   <span data-ttu-id="165d0-132">Przy użyciu pełnego [wzorzec określania źródła zdarzeń](https://msdn.microsoft.com/library/dn589792.aspx).</span><span class="sxs-lookup"><span data-stu-id="165d0-132">Using the full [Event Sourcing pattern](https://msdn.microsoft.com/library/dn589792.aspx).</span></span>

-   <span data-ttu-id="165d0-133">Za pomocą [wyszukiwania dziennik transakcji](https://www.scoop.it/t/sql-server-transaction-log-mining).</span><span class="sxs-lookup"><span data-stu-id="165d0-133">Using [transaction log mining](https://www.scoop.it/t/sql-server-transaction-log-mining).</span></span>

-   <span data-ttu-id="165d0-134">Za pomocą [wzorzec Skrzynka nadawcza](http://gistlabs.com/2014/05/the-outbox/).</span><span class="sxs-lookup"><span data-stu-id="165d0-134">Using the [Outbox pattern](http://gistlabs.com/2014/05/the-outbox/).</span></span> <span data-ttu-id="165d0-135">To jest tabela transakcji do przechowywania zdarzeń integracji (Rozszerzanie lokalnej transakcji).</span><span class="sxs-lookup"><span data-stu-id="165d0-135">This is a transactional table to store the integration events (extending the local transaction).</span></span>

<span data-ttu-id="165d0-136">W tym scenariuszu przy użyciu pełnej wzorca określania źródła zdarzeń (ES) jest jednym z najlepszych metod, jeśli nie *najlepsze*.</span><span class="sxs-lookup"><span data-stu-id="165d0-136">For this scenario, using the full Event Sourcing (ES) pattern is one of the best approaches, if not *the* best.</span></span> <span data-ttu-id="165d0-137">Jednak w wielu scenariuszach aplikacji, nie można zaimplementować pełnego ES.</span><span class="sxs-lookup"><span data-stu-id="165d0-137">However, in many application scenarios, you might not be able to implement a full ES system.</span></span> <span data-ttu-id="165d0-138">ES oznacza przechowywanie tylko domeny zdarzenia w transakcji bazy danych, zamiast przechowywania danych bieżącego stanu.</span><span class="sxs-lookup"><span data-stu-id="165d0-138">ES means storing only domain events in your transactional database, instead of storing current state data.</span></span> <span data-ttu-id="165d0-139">Przechowywanie tylko domeny zdarzenia może mieć wiele korzyści, takich jak o historii dostępności systemu i możliwość określenia stanu systemu w dowolnym momencie w przeszłości.</span><span class="sxs-lookup"><span data-stu-id="165d0-139">Storing only domain events can have great benefits, such as having the history of your system available and being able to determine the state of your system at any moment in the past.</span></span> <span data-ttu-id="165d0-140">Jednak implementacja pełnego ES wymaga Przekształcanie większość systemu i wprowadza wiele złożoności i wymagania.</span><span class="sxs-lookup"><span data-stu-id="165d0-140">However, implementing a full ES system requires you to rearchitect most of your system and introduces many other complexities and requirements.</span></span> <span data-ttu-id="165d0-141">Na przykład chcesz korzystać z bazy danych, które celowo do określania źródła zdarzeń, takich jak [Store zdarzeń](https://eventstore.org/), lub korzystający z dokumentów bazy danych, takich jak usługi Azure Cosmos DB, bazy danych MongoDB, Cassandra, CouchDB lub RavenDB.</span><span class="sxs-lookup"><span data-stu-id="165d0-141">For example, you would want to use a database specifically made for event sourcing, such as [Event Store](https://eventstore.org/), or a document-oriented database such as Azure Cosmos DB, MongoDB, Cassandra, CouchDB, or RavenDB.</span></span> <span data-ttu-id="165d0-142">ES jest to doskonałe podejście do problemu, ale nie najprostszym rozwiązaniu, chyba że znasz już określania źródła zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="165d0-142">ES is a great approach for this problem, but not the easiest solution unless you are already familiar with event sourcing.</span></span>

<span data-ttu-id="165d0-143">Możliwość użycia dziennika transakcji wyszukiwania początkowo wygląda bardzo przejrzysty.</span><span class="sxs-lookup"><span data-stu-id="165d0-143">The option to use transaction log mining initially looks very transparent.</span></span> <span data-ttu-id="165d0-144">Jednak aby użyć tego podejścia, mikrousług ma zostać dołączone do dziennika transakcji RDBMS, takie jak dziennik transakcji programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="165d0-144">However, to use this approach, the microservice has to be coupled to your RDBMS transaction log, such as the SQL Server transaction log.</span></span> <span data-ttu-id="165d0-145">Prawdopodobnie nie jest to pożądane.</span><span class="sxs-lookup"><span data-stu-id="165d0-145">This is probably not desirable.</span></span> <span data-ttu-id="165d0-146">Inny wadą jest to, że aktualizacje niskiego poziomu, rejestrowane w dzienniku transakcji może nie być tym samym poziomie, jako zdarzenia wysokiego poziomu integracji.</span><span class="sxs-lookup"><span data-stu-id="165d0-146">Another drawback is that the low-level updates recorded in the transaction log might not be at the same level as your high-level integration events.</span></span> <span data-ttu-id="165d0-147">Jeśli tak, proces odtwarzania te operacje dziennika transakcji może być trudne.</span><span class="sxs-lookup"><span data-stu-id="165d0-147">If so, the process of reverse-engineering those transaction log operations can be difficult.</span></span>

<span data-ttu-id="165d0-148">Zrównoważone podejście jest kombinacja tabela transakcji bazy danych i uproszczone wzorzec ES.</span><span class="sxs-lookup"><span data-stu-id="165d0-148">A balanced approach is a mix of a transactional database table and a simplified ES pattern.</span></span> <span data-ttu-id="165d0-149">Można użyć stanu, np. "gotowy do publikowania zdarzeń", który ustawia w oryginalnej zdarzenia podczas zatwierdzania integracji w tabeli zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="165d0-149">You can use a state such as “ready to publish the event,” which you set in the original event when you commit it to the integration events table.</span></span> <span data-ttu-id="165d0-150">Następnie spróbuj opublikować wydarzenie magistrali zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="165d0-150">You then try to publish the event to the event bus.</span></span> <span data-ttu-id="165d0-151">Jeśli akcja zdarzenia publikowania zakończy się powodzeniem, uruchom inną transakcję w usłudze pochodzenia i Przenieś stanu z "gotowych do opublikowania zdarzenia" "zdarzenie już opublikowane."</span><span class="sxs-lookup"><span data-stu-id="165d0-151">If the publish-event action succeeds, you start another transaction in the origin service and move the state from “ready to publish the event” to “event already published.”</span></span>

<span data-ttu-id="165d0-152">Jeśli akcja zdarzenia publikowania w zdarzeniu magistrali kończy się niepowodzeniem, dane nadal nie będą niespójne w mikrousługach pochodzenia — nadal jest oznaczona jako "gotowy do opublikowania zdarzenie", a w odniesieniu do pozostałych usług po pewnym czasie będzie spójny.</span><span class="sxs-lookup"><span data-stu-id="165d0-152">If the publish-event action in the event bus fails, the data still will not be inconsistent within the origin microservice—it is still marked as “ready to publish the event,” and with respect to the rest of the services, it will eventually be consistent.</span></span> <span data-ttu-id="165d0-153">Sprawdzanie stanu transakcji lub zdarzenia integracji zadań w tle zawsze może mieć.</span><span class="sxs-lookup"><span data-stu-id="165d0-153">You can always have background jobs checking the state of the transactions or integration events.</span></span> <span data-ttu-id="165d0-154">Jeśli zadanie znajdzie zdarzenia w stanie "gotowe do opublikowania zdarzenie", może użyć ponownie opublikować tego zdarzenia do magistrali zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="165d0-154">If the job finds an event in the “ready to publish the event” state, it can try to republish that event to the event bus.</span></span>

<span data-ttu-id="165d0-155">Należy zauważyć, że w przypadku tej metody, można są przechowywanie tylko zdarzenia integracji dla poszczególnych mikrousług źródła, a tylko zdarzenia, które chcesz komunikować się z innymi mikrousług lub systemy zewnętrzne.</span><span class="sxs-lookup"><span data-stu-id="165d0-155">Notice that with this approach, you are persisting only the integration events for each origin microservice, and only the events that you want to communicate to other microservices or external systems.</span></span> <span data-ttu-id="165d0-156">Z kolei w pełnym systemie ES, są przechowywane także wszystkie zdarzenia domeny.</span><span class="sxs-lookup"><span data-stu-id="165d0-156">In contrast, in a full ES system, you store all domain events as well.</span></span>

<span data-ttu-id="165d0-157">W związku z tym ta metoda o zrównoważonym obciążeniu jest uproszczony system ES.</span><span class="sxs-lookup"><span data-stu-id="165d0-157">Therefore, this balanced approach is a simplified ES system.</span></span> <span data-ttu-id="165d0-158">Należy uzyskać listę zdarzeń integracji z ich bieżącym stanem ("gotowe do opublikowania" i "opublikowany").</span><span class="sxs-lookup"><span data-stu-id="165d0-158">You need a list of integration events with their current state (“ready to publish” versus “published”).</span></span> <span data-ttu-id="165d0-159">Ale trzeba zaimplementować te stany zdarzenia integracji.</span><span class="sxs-lookup"><span data-stu-id="165d0-159">But you only need to implement these states for the integration events.</span></span> <span data-ttu-id="165d0-160">A w przypadku tej metody nie trzeba do przechowywania danych domeny jako zdarzenia w bazie danych transakcyjnych, tak jak w pełnym systemie ES.</span><span class="sxs-lookup"><span data-stu-id="165d0-160">And in this approach, you do not need to store all your domain data as events in the transactional database, as you would in a full ES system.</span></span>

<span data-ttu-id="165d0-161">Jeśli już używasz relacyjnej bazy danych, można użyć transakcji tabeli do przechowywania zdarzeń integracji.</span><span class="sxs-lookup"><span data-stu-id="165d0-161">If you are already using a relational database, you can use a transactional table to store integration events.</span></span> <span data-ttu-id="165d0-162">Aby osiągnąć niepodzielność w aplikacji, należy użyć dwuetapowego procesu na podstawie lokalnej transakcji.</span><span class="sxs-lookup"><span data-stu-id="165d0-162">To achieve atomicity in your application, you use a two-step process based on local transactions.</span></span> <span data-ttu-id="165d0-163">Zasadniczo masz tabelę IntegrationEvent w tej samej bazy danych, których mają jednostki domeny.</span><span class="sxs-lookup"><span data-stu-id="165d0-163">Basically, you have an IntegrationEvent table in the same database where you have your domain entities.</span></span> <span data-ttu-id="165d0-164">Ta tabela działa zgodnie z branży ubezpieczeniowej do osiągnięcia niepodzielność, tak że uwzględnisz utrwalone zdarzenia integracji w tej samej transakcji, które są w trakcie zatwierdzania danych domeny.</span><span class="sxs-lookup"><span data-stu-id="165d0-164">That table works as an insurance for achieving atomicity so that you include persisted integration events into the same transactions that are committing your domain data.</span></span>

<span data-ttu-id="165d0-165">Krok po kroku proces wykracza następująco:</span><span class="sxs-lookup"><span data-stu-id="165d0-165">Step by step, the process goes like this:</span></span>

1.  <span data-ttu-id="165d0-166">Aplikacja rozpocznie transakcji lokalnej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="165d0-166">The application begins a local database transaction.</span></span>

2.  <span data-ttu-id="165d0-167">Następnie aktualizuje stan jednostki domeny i wstawia zdarzenia do tabeli zdarzeń integracji.</span><span class="sxs-lookup"><span data-stu-id="165d0-167">It then updates the state of your domain entities and inserts an event into the integration event table.</span></span>

3.  <span data-ttu-id="165d0-168">Na koniec jej zatwierdzenia transakcji, dzięki czemu uzyskujesz żądaną niepodzielność i następnie</span><span class="sxs-lookup"><span data-stu-id="165d0-168">Finally, it commits the transaction, so you get the desired atomicity and then</span></span>

4.  <span data-ttu-id="165d0-169">Jakiś sposób opublikować wydarzenie (dalej).</span><span class="sxs-lookup"><span data-stu-id="165d0-169">You publish the event somehow (next).</span></span>

<span data-ttu-id="165d0-170">Implementując kroki publikowania zdarzenia, masz następujące opcje:</span><span class="sxs-lookup"><span data-stu-id="165d0-170">When implementing the steps of publishing the events, you have these choices:</span></span>

-   <span data-ttu-id="165d0-171">Publikowanie zdarzeń integracji od razu po zatwierdzanie transakcji i użyj innego transakcji lokalnej, aby oznaczyć zdarzenia w opublikowanej tabeli.</span><span class="sxs-lookup"><span data-stu-id="165d0-171">Publish the integration event right after committing the transaction and use another local transaction to mark the events in the table as being published.</span></span> <span data-ttu-id="165d0-172">Następnie skorzystaj z tabeli po prostu jako artefaktu do śledzenia zdarzeń integracji, w razie problemów z mikrousług zdalnego i wykonywać akcje kompensacyjne, na podstawie zdarzeń przechowywanych integracji.</span><span class="sxs-lookup"><span data-stu-id="165d0-172">Then, use the table just as an artifact to track the integration events in case of issues in the remote microservices, and perform compensatory actions based on the stored integration events.</span></span>

-   <span data-ttu-id="165d0-173">Skorzystaj z tabeli jako rodzaj kolejki.</span><span class="sxs-lookup"><span data-stu-id="165d0-173">Use the table as a kind of queue.</span></span> <span data-ttu-id="165d0-174">Wątek oddzielną aplikację lub procesu zapytania w tabeli zdarzeń integracji, publikuje w magistrali zdarzeń zdarzenia i następnie używa lokalnej transakcji do oznaczenia zdarzeń jako opublikowane.</span><span class="sxs-lookup"><span data-stu-id="165d0-174">A separate application thread or process queries the integration event table, publishes the events to the event bus, and then uses a local transaction to mark the events as published.</span></span>

<span data-ttu-id="165d0-175">Rysunek 6-22 przedstawiono architekturę jako pierwsza z tych metod.</span><span class="sxs-lookup"><span data-stu-id="165d0-175">Figure 6-22 shows the architecture for the first of these approaches.</span></span>

![Jedno z podejść do obsługi niepodzielność podczas publikowania zdarzeń: publikować (używanych w ramach aplikacji eShopOnContainers) za pomocą jednej transakcji do zatwierdzenia zdarzenia do tabeli dziennika zdarzeń, a następnie inną transakcję](./media/image23.png)

<span data-ttu-id="165d0-177">**Rysunek 6-22**.</span><span class="sxs-lookup"><span data-stu-id="165d0-177">**Figure 6-22**.</span></span> <span data-ttu-id="165d0-178">Niepodzielność podczas publikowania zdarzeń w magistrali zdarzeń</span><span class="sxs-lookup"><span data-stu-id="165d0-178">Atomicity when publishing events to the event bus</span></span>

<span data-ttu-id="165d0-179">Podejście pokazano w rysunek 6-22 brakuje mikrousług dodatkowe procesu roboczego, który jest odpowiedzialny za sprawdzenie i Potwierdzanie Powodzenie zdarzenia opublikowanych integracji.</span><span class="sxs-lookup"><span data-stu-id="165d0-179">The approach illustrated in Figure 6-22 is missing an additional worker microservice that is in charge of checking and confirming the success of the published integration events.</span></span> <span data-ttu-id="165d0-180">W przypadku awarii tego dodatkowe sprawdzanie procesu roboczego mikrousług można odczytywać zdarzenia z tabeli i ponownie opublikować je, czyli liczba Powtórz krok 2.</span><span class="sxs-lookup"><span data-stu-id="165d0-180">In case of failure, that additional checker worker microservice can read events from the table and republish them, that is, repeat step number 2.</span></span>

<span data-ttu-id="165d0-181">Temat drugiego podejścia: skorzystaj z tabeli dziennika zdarzeń, co kolejka i zawsze używaj mikrousług procesu roboczego do publikowania wiadomości.</span><span class="sxs-lookup"><span data-stu-id="165d0-181">About the second approach: you use the EventLog table as a queue and always use a worker microservice to publish the messages.</span></span> <span data-ttu-id="165d0-182">W takiej sytuacji proces Krewny, który jest wyświetlany w rysunek 6 – 23.</span><span class="sxs-lookup"><span data-stu-id="165d0-182">In that case, the process is like that shown in Figure 6-23.</span></span> <span data-ttu-id="165d0-183">Spowoduje to pokazanie dodatkowe mikrousług, a tabela jest pojedyncze źródło podczas publikowania zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="165d0-183">This shows an additional microservice, and the table is the single source when publishing events.</span></span>

![Innym sposobem obsługi niepodzielność: publikowanie do tabeli dziennika zdarzeń, a następnie mają inny mikrousługi (procesu roboczego tła) opublikować zdarzenia.](./media/image24.png)

<span data-ttu-id="165d0-185">**Rysunek 6-23**.</span><span class="sxs-lookup"><span data-stu-id="165d0-185">**Figure 6-23**.</span></span> <span data-ttu-id="165d0-186">Niepodzielność podczas publikowania zdarzeń w magistrali zdarzeń z mikrousług procesu roboczego</span><span class="sxs-lookup"><span data-stu-id="165d0-186">Atomicity when publishing events to the event bus with a worker microservice</span></span>

<span data-ttu-id="165d0-187">Dla uproszczenia przykładowe w ramach aplikacji eShopOnContainers korzysta z pierwszej metody (bez dodatkowych procesów i z mikrousług sprawdzania) oraz magistrali zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="165d0-187">For simplicity, the eShopOnContainers sample uses the first approach (with no additional processes or checker microservices) plus the event bus.</span></span> <span data-ttu-id="165d0-188">Jednak ramach aplikacji eShopOnContainers nie obsługuje wszystkich przypadkach mogą występować awarie.</span><span class="sxs-lookup"><span data-stu-id="165d0-188">However, the eShopOnContainers is not handling all possible failure cases.</span></span> <span data-ttu-id="165d0-189">W rzeczywistej aplikacji wdrożonych w chmurze możesz wykorzystać fakt, że będzie problemów po pewnym czasie oraz musi implementować i sprawdź i Wyślij ponownie logiki.</span><span class="sxs-lookup"><span data-stu-id="165d0-189">In a real application deployed to the cloud, you must embrace the fact that issues will arise eventually, and you must implement that check and resend logic.</span></span> <span data-ttu-id="165d0-190">Przy użyciu tabeli jako kolejka może być bardziej efektywne niż pierwszego podejścia, jeśli masz tę tabelę jako pojedyncze źródło zdarzenia, gdy w ich opublikowaniem (z proces roboczy), za pośrednictwem magistrali zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="165d0-190">Using the table as a queue can be more effective than the first approach if you have that table as a single source of events when publishing them (with the worker) through the event bus.</span></span>

### <a name="implementing-atomicity-when-publishing-integration-events-through-the-event-bus"></a><span data-ttu-id="165d0-191">Implementowanie niepodzielność podczas publikowania zdarzeń integracja za pośrednictwem magistrali zdarzeń</span><span class="sxs-lookup"><span data-stu-id="165d0-191">Implementing atomicity when publishing integration events through the event bus</span></span>

<span data-ttu-id="165d0-192">Poniższy kod przedstawia sposób tworzenia pojedynczej transakcji obejmujących wiele obiektów typu DbContext — jednym kontekście związane z oryginalnych danych aktualizowana, a drugi kontekst związany z tabeli IntegrationEventLog.</span><span class="sxs-lookup"><span data-stu-id="165d0-192">The following code shows how you can create a single transaction involving multiple DbContext objects—one context related to the original data being updated, and the second context related to the IntegrationEventLog table.</span></span>

<span data-ttu-id="165d0-193">Pamiętaj, że transakcji w poniższym przykładowym kodzie nie będą odporne na błędy, jeśli połączeń z bazą danych wszelkie problemy w czasie, gdy kod jest uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="165d0-193">Note that the transaction in the example code below will not be resilient if connections to the database have any issue at the time when the code is running.</span></span> <span data-ttu-id="165d0-194">Może to nastąpić w chmurze systemów, takich jak bazy danych SQL Azure, które mogą przenosić bazy danych na serwerach.</span><span class="sxs-lookup"><span data-stu-id="165d0-194">This can happen in cloud-based systems like Azure SQL DB, which might move databases across servers.</span></span> <span data-ttu-id="165d0-195">Implementowanie odpornych transakcji w wielu kontekstach, dla [Implementowanie odpornych na błędy połączeń Entity Framework Core SQL](../implement-resilient-applications/implement-resilient-entity-framework-core-sql-connections.md) sekcję w dalszej części tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="165d0-195">For implementing resilient transactions across multiple contexts, see the [Implementing resilient Entity Framework Core SQL connections](../implement-resilient-applications/implement-resilient-entity-framework-core-sql-connections.md) section later in this guide.</span></span>

<span data-ttu-id="165d0-196">W celu uściślenia poniższy przykład pokazuje całego procesu w pojedynczy fragment kodu.</span><span class="sxs-lookup"><span data-stu-id="165d0-196">For clarity, the following example shows the whole process in a single piece of code.</span></span> <span data-ttu-id="165d0-197">Jednak implementacji w ramach aplikacji eShopOnContainers faktycznie zaprojektowane od nowa i podzielić tę logikę na wiele klas, więc jest łatwiejsze w konserwacji.</span><span class="sxs-lookup"><span data-stu-id="165d0-197">However, the eShopOnContainers implementation is actually refactored and split this logic into multiple classes so it is easier to maintain.</span></span>

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

<span data-ttu-id="165d0-198">Po utworzeniu zdarzenia integracji ProductPriceChangedIntegrationEvent transakcji, która przechowuje operacji pierwotnej domeny (Aktualizacja elementów katalogu) zawiera również trwałości zdarzenia w tabeli w dzienniku zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="165d0-198">After the ProductPriceChangedIntegrationEvent integration event is created, the transaction that stores the original domain operation (update the catalog item) also includes the persistence of the event in the EventLog table.</span></span> <span data-ttu-id="165d0-199">Dzięki temu pojedynczą transakcję i zawsze można sprawdzić, czy komunikaty o zdarzeniach zostały wysłane.</span><span class="sxs-lookup"><span data-stu-id="165d0-199">This makes it a single transaction, and you will always be able to check whether event messages were sent.</span></span>

<span data-ttu-id="165d0-200">Tabela dziennika zdarzeń jest aktualizowana niepodzielne operacji pierwotnej bazy danych przy użyciu lokalnej transakcji w tej samej bazie danych.</span><span class="sxs-lookup"><span data-stu-id="165d0-200">The event log table is updated atomically with the original database operation, using a local transaction against the same database.</span></span> <span data-ttu-id="165d0-201">Jeśli dowolne operacje kończą się niepowodzeniem, zostanie zgłoszony wyjątek i transakcji powoduje wycofanie zakończonych operacji, w związku z tym utrzymanie spójności między operacjami domeny i komunikaty o zdarzeniach, zapisane w tabeli.</span><span class="sxs-lookup"><span data-stu-id="165d0-201">If any of the operations fail, an exception is thrown and the transaction rolls back any completed operation, thus maintaining consistency between the domain operations and the event messages saved to the table.</span></span>

### <a name="receiving-messages-from-subscriptions-event-handlers-in-receiver-microservices"></a><span data-ttu-id="165d0-202">Odbieranie komunikatów z subskrypcji: obsługi zdarzeń w mikrousługach odbiorcy</span><span class="sxs-lookup"><span data-stu-id="165d0-202">Receiving messages from subscriptions: event handlers in receiver microservices</span></span>

<span data-ttu-id="165d0-203">Oprócz logiki subskrypcji zdarzeń musisz wdrożyć wewnętrzny kod procedury obsługi zdarzeń integracji (np. metody wywołania zwrotnego).</span><span class="sxs-lookup"><span data-stu-id="165d0-203">In addition to the event subscription logic, you need to implement the internal code for the integration event handlers (like a callback method).</span></span> <span data-ttu-id="165d0-204">Program obsługi zdarzeń określa się tam gdzie odbierane i przetwarzane komunikaty o zdarzeniach określonego typu.</span><span class="sxs-lookup"><span data-stu-id="165d0-204">The event handler is where you specify where the event messages of a certain type will be received and processed.</span></span>

<span data-ttu-id="165d0-205">Program obsługi zdarzeń otrzymuje najpierw wystąpienie zdarzenia z magistrali zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="165d0-205">An event handler first receives an event instance from the event bus.</span></span> <span data-ttu-id="165d0-206">Następnie klient zlokalizuje składników, które mają być przetwarzane powiązany z tym zdarzeniem integracji propagowanie i przechowywanie zdarzenia jako zmianę stanu w mikrousługach odbiorcy.</span><span class="sxs-lookup"><span data-stu-id="165d0-206">Then it locates the component to be processed related to that integration event, propagating and persisting the event as a change in state in the receiver microservice.</span></span> <span data-ttu-id="165d0-207">Na przykład jeśli zdarzenie ProductPriceChanged pochodzi z mikrousług wykazu, będzie odbywa się w mikrousługach koszyka i zmienia stan w tej mikrousług koszyka odbiornik, jak i, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="165d0-207">For example, if a ProductPriceChanged event originates in the catalog microservice, it is handled in the basket microservice and changes the state in this receiver basket microservice as well, as shown in the following code.</span></span>

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

<span data-ttu-id="165d0-208">Program obsługi zdarzeń musi sprawdzić, czy produkt istnieje we wszystkich wystąpieniach koszyka.</span><span class="sxs-lookup"><span data-stu-id="165d0-208">The event handler needs to verify whether the product exists in any of the basket instances.</span></span> <span data-ttu-id="165d0-209">Aktualizuje cenę dla każdego elementu wiersza powiązane koszyka.</span><span class="sxs-lookup"><span data-stu-id="165d0-209">It also updates the item price for each related basket line item.</span></span> <span data-ttu-id="165d0-210">Na koniec tworzy alert ma być wyświetlany dla użytkownika o zmianę ceny, jak pokazano w rysunek 6 do 24.</span><span class="sxs-lookup"><span data-stu-id="165d0-210">Finally, it creates an alert to be displayed to the user about the price change, as shown in Figure 6-24.</span></span>

![Wyświetlany w przeglądarce widok procesu zmiany powiadomienia na koszyka użytkownika.](./media/image25.png)

<span data-ttu-id="165d0-212">**Rysunek 6 – 24**.</span><span class="sxs-lookup"><span data-stu-id="165d0-212">**Figure 6-24**.</span></span> <span data-ttu-id="165d0-213">Wyświetlanie zmian cen elementów w koszyku jako przekazywane przez zdarzenia integracji</span><span class="sxs-lookup"><span data-stu-id="165d0-213">Displaying an item price change in a basket, as communicated by integration events</span></span>

## <a name="idempotency-in-update-message-events"></a><span data-ttu-id="165d0-214">Idempotentność w aktualizacji komunikat zdarzenia</span><span class="sxs-lookup"><span data-stu-id="165d0-214">Idempotency in update message events</span></span>

<span data-ttu-id="165d0-215">Ważnym aspektem zdarzeń komunikatów aktualizacji jest, czy Niepowodzenie w dowolnym momencie w komunikacie powinno spowodować komunikat, który ma zostać ponowiona.</span><span class="sxs-lookup"><span data-stu-id="165d0-215">An important aspect of update message events is that a failure at any point in the communication should cause the message to be retried.</span></span> <span data-ttu-id="165d0-216">W przeciwnym razie zadanie w tle może próbować publikowania zdarzenia, które zostało już opublikowane, tworząc warunki sytuacji wyścigu.</span><span class="sxs-lookup"><span data-stu-id="165d0-216">Otherwise a background task might try to publish an event that has already been published, creating a race condition.</span></span> <span data-ttu-id="165d0-217">Możesz należy się upewnić, że aktualizacje są idempotentne lub że zapewniają one wystarczającej ilości informacji, aby upewnić się, że można wykryć duplikat, odrzucić je i Wyślij ponownie tylko jedną odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="165d0-217">You need to make sure that the updates are either idempotent or that they provide enough information to ensure that you can detect a duplicate, discard it, and send back only one response.</span></span>

<span data-ttu-id="165d0-218">Jak wspomniano wcześniej, idempotentność oznacza, że operacja może zostać wykonana wiele razy bez wprowadzania zmian w wyniku.</span><span class="sxs-lookup"><span data-stu-id="165d0-218">As noted earlier, idempotency means that an operation can be performed multiple times without changing the result.</span></span> <span data-ttu-id="165d0-219">W środowisku obsługi komunikatów ponieważ podczas komunikowania się zdarzenia, zdarzenie jest idempotentna, jeśli móc go dostarczyć wiele razy bez wprowadzania zmian w wyniku dla mikrousług odbiorcy.</span><span class="sxs-lookup"><span data-stu-id="165d0-219">In a messaging environment, as when communicating events, an event is idempotent if it can be delivered multiple times without changing the result for the receiver microservice.</span></span> <span data-ttu-id="165d0-220">Może to być konieczne ze względu na charakter samego zdarzenia lub ze względu na sposób system obsługuje zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="165d0-220">This may be necessary because of the nature of the event itself, or because of the way the system handles the event.</span></span> <span data-ttu-id="165d0-221">Komunikat idempotentność jest ważne, w dowolnej aplikacji, która używa obsługi komunikatów, a nie tylko w aplikacji, które implementują wzorzec magistrali zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="165d0-221">Message idempotency is important in any application that uses messaging, not just in applications that implement the event bus pattern.</span></span>

<span data-ttu-id="165d0-222">Przykładem operacja idempotentna jest instrukcję SQL, który wstawia dane do tabeli, tylko wtedy, gdy dane nie są już w tabeli.</span><span class="sxs-lookup"><span data-stu-id="165d0-222">An example of an idempotent operation is a SQL statement that inserts data into a table only if that data is not already in the table.</span></span> <span data-ttu-id="165d0-223">Nie ma znaczenia, ile razy należy uruchomić, które wstawiają instrukcję SQL wynik będzie taki sam — tabela będzie zawierać tych danych.</span><span class="sxs-lookup"><span data-stu-id="165d0-223">It does not matter how many times you run that insert SQL statement; the result will be the same—the table will contain that data.</span></span> <span data-ttu-id="165d0-224">Idempotentności, np. to może być również niezbędne podczas pracy z komunikatów, jeśli potencjalnie być wysyłane komunikaty i w związku z tym przetworzonych więcej niż raz.</span><span class="sxs-lookup"><span data-stu-id="165d0-224">Idempotency like this can also be necessary when dealing with messages if the messages could potentially be sent and therefore processed more than once.</span></span> <span data-ttu-id="165d0-225">Na przykład jeśli Logika ponawiania powoduje, że nadawca wysyłać ten sam komunikat więcej niż jeden raz, należy się upewnić, że jest idempotentna.</span><span class="sxs-lookup"><span data-stu-id="165d0-225">For instance, if retry logic causes a sender to send exactly the same message more than once, you need to make sure that it is idempotent.</span></span>

<span data-ttu-id="165d0-226">Istnieje możliwość projektowania idempotentne wiadomości.</span><span class="sxs-lookup"><span data-stu-id="165d0-226">It is possible to design idempotent messages.</span></span> <span data-ttu-id="165d0-227">Na przykład można utworzyć zdarzenie i mówi "Ustaw cena produktu do 25 USD" zamiast "Dodaj 5 USD cena produktu"</span><span class="sxs-lookup"><span data-stu-id="165d0-227">For example, you can create an event that says "set the product price to $25" instead of "add $5 to the product price."</span></span> <span data-ttu-id="165d0-228">Użytkownik może bezpiecznie przetworzyć pierwszy komunikat o dowolną liczbę razy, a wynik będzie taki sam.</span><span class="sxs-lookup"><span data-stu-id="165d0-228">You could safely process the first message any number of times and the result will be the same.</span></span> <span data-ttu-id="165d0-229">To nie dotyczy drugi komunikat.</span><span class="sxs-lookup"><span data-stu-id="165d0-229">That is not true for the second message.</span></span> <span data-ttu-id="165d0-230">Ale nawet w przypadku pierwszego, nie można przetworzyć pierwsze zdarzenie, ponieważ system może również wysłane nowszych zdarzeń zmian cen i spowoduje zastąpienie nową cenę.</span><span class="sxs-lookup"><span data-stu-id="165d0-230">But even in the first case, you might not want to process the first event, because the system could also have sent a newer price-change event and you would be overwriting the new price.</span></span>

<span data-ttu-id="165d0-231">Innym przykładem mogą być zdarzenie ukończone w kolejności propagowana do wielu subskrybentów.</span><span class="sxs-lookup"><span data-stu-id="165d0-231">Another example might be an order-completed event being propagated to multiple subscribers.</span></span> <span data-ttu-id="165d0-232">Ważne jest, informacji o zamówieniach zaktualizowania w innych systemach tylko raz, nawet jeśli występują zduplikowany komunikat zdarzenia dla tego samego zdarzenia ukończone w kolejności.</span><span class="sxs-lookup"><span data-stu-id="165d0-232">It is important that order information be updated in other systems just once, even if there are duplicated message events for the same order-completed event.</span></span>

<span data-ttu-id="165d0-233">Jest wygodną zapewnienie pewnego rodzaju tożsamości na zdarzenie, w którym można utworzyć logikę, która wymusza na to, że każde zdarzenie jest przetwarzany tylko raz na odbiorcy.</span><span class="sxs-lookup"><span data-stu-id="165d0-233">It is convenient to have some kind of identity per event so that you can create logic that enforces that each event is processed only once per receiver.</span></span>

<span data-ttu-id="165d0-234">Przetwarza komunikat jest idempotentna.</span><span class="sxs-lookup"><span data-stu-id="165d0-234">Some message processing is inherently idempotent.</span></span> <span data-ttu-id="165d0-235">Na przykład jeśli system generuje obraz miniatury, może nie ważne jest, ile razy komunikat dotyczący miniatury wygenerowanej jest przetwarzany; wynik jest miniatury są generowane i każdym razem, gdy są takie same.</span><span class="sxs-lookup"><span data-stu-id="165d0-235">For example, if a system generates image thumbnails, it might not matter how many times the message about the generated thumbnail is processed; the outcome is that the thumbnails are generated and they are the same every time.</span></span> <span data-ttu-id="165d0-236">Z drugiej strony operacje, takie jak wywołanie bramy płatności do obciążenia karty kredytowej może nie być idempotentne wcale.</span><span class="sxs-lookup"><span data-stu-id="165d0-236">On the other hand, operations such as calling a payment gateway to charge a credit card may not be idempotent at all.</span></span> <span data-ttu-id="165d0-237">W takich przypadkach musisz upewnić się, że przetwarzania wiadomości wielokrotnie efekt, których oczekujesz.</span><span class="sxs-lookup"><span data-stu-id="165d0-237">In these cases, you need to ensure that processing a message multiple times has the effect that you expect.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="165d0-238">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="165d0-238">Additional resources</span></span>

-   <span data-ttu-id="165d0-239">**Zapewniane idempotentności wiadomości**</span><span class="sxs-lookup"><span data-stu-id="165d0-239">**Honoring message idempotency**</span></span> <br/>
    [*https://msdn.microsoft.com/library/jj591565.aspx#honoring_message_idempotency*](https://msdn.microsoft.com/library/jj591565.aspx)

## <a name="deduplicating-integration-event-messages"></a><span data-ttu-id="165d0-240">Deduplikacja integracji komunikaty o zdarzeniach</span><span class="sxs-lookup"><span data-stu-id="165d0-240">Deduplicating integration event messages</span></span>

<span data-ttu-id="165d0-241">Można należy upewnić się, że zdarzenia dotyczące wiadomości wysyłanych i przetwarzany tylko raz na subskrybenta na różnych poziomach.</span><span class="sxs-lookup"><span data-stu-id="165d0-241">You can make sure that message events are sent and processed just once per subscriber at different levels.</span></span> <span data-ttu-id="165d0-242">Jednym ze sposobów jest korzystać z funkcji deduplikacji, oferowane przez infrastruktura obsługi komunikatów, którego używasz.</span><span class="sxs-lookup"><span data-stu-id="165d0-242">One way is to use a deduplication feature offered by the messaging infrastructure you are using.</span></span> <span data-ttu-id="165d0-243">Innym jest zaimplementowanie logiki niestandardowej w mikrousługach swoje miejsce docelowe.</span><span class="sxs-lookup"><span data-stu-id="165d0-243">Another is to implement custom logic in your destination microservice.</span></span> <span data-ttu-id="165d0-244">Sprawdzanie poprawności na poziomie transportu i na poziomie aplikacji jest najlepsze rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="165d0-244">Having validations at both the transport level and the application level is your best bet.</span></span>

### <a name="deduplicating-message-events-at-the-eventhandler-level"></a><span data-ttu-id="165d0-245">Komunikat zdarzenia na poziomie EventHandler deduplikacja</span><span class="sxs-lookup"><span data-stu-id="165d0-245">Deduplicating message events at the EventHandler level</span></span>

<span data-ttu-id="165d0-246">Jednym ze sposobów, aby upewnić się, że zdarzenie jest przetwarzany tylko raz przez żadnego odbiorcy jest zaimplementowanie logiki określonych podczas przetwarzania zdarzeń komunikatów w procedurze obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="165d0-246">One way to make sure that an event is processed just once by any receiver is by implementing certain logic when processing the message events in event handlers.</span></span> <span data-ttu-id="165d0-247">Na przykład, to podejście użyte w ramach aplikacji eShopOnContainers aplikacji, jak widać w [źródła kod klasy UserCheckoutAcceptedIntegrationEventHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) po odebraniu UserCheckoutAcceptedIntegrationEvent Zdarzenie integracji.</span><span class="sxs-lookup"><span data-stu-id="165d0-247">For example, that is the approach used in the eShopOnContainers application, as you can see in the [source code of the UserCheckoutAcceptedIntegrationEventHandler class](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) when it receives an UserCheckoutAcceptedIntegrationEvent integration event.</span></span> <span data-ttu-id="165d0-248">(W tym przypadku możemy opakować CreateOrderCommand z IdentifiedCommand przy użyciu eventMsg.RequestId jako identyfikator przed wysłaniem ich do obsługi polecenia).</span><span class="sxs-lookup"><span data-stu-id="165d0-248">(In this case we wrap the CreateOrderCommand with an IdentifiedCommand, using the eventMsg.RequestId as an identifier, before sending it to the command handler).</span></span>

### <a name="deduplicating-messages-when-using-rabbitmq"></a><span data-ttu-id="165d0-249">Deduplikacja wiadomości w przypadku korzystania z oprogramowania RabbitMQ</span><span class="sxs-lookup"><span data-stu-id="165d0-249">Deduplicating messages when using RabbitMQ</span></span>

<span data-ttu-id="165d0-250">Gdy wystąpi sporadyczne awarie sieci, mogą być zduplikowane komunikaty, a odbiorcy wiadomości musi być gotowy do obsługi tych zduplikowane komunikaty.</span><span class="sxs-lookup"><span data-stu-id="165d0-250">When intermittent network failures happen, messages can be duplicated, and the message receiver must be ready to handle these duplicated messages.</span></span> <span data-ttu-id="165d0-251">Jeśli to możliwe odbiorniki powinna obsługiwać komunikaty w sposób idempotentne, który jest lepsze niż jawną obsługę je z włączoną funkcją deduplikacji.</span><span class="sxs-lookup"><span data-stu-id="165d0-251">If possible, receivers should handle messages in an idempotent way, which is better than explicitly handling them with deduplication.</span></span>

<span data-ttu-id="165d0-252">Zgodnie z opisem w [dokumentacji oprogramowania RabbitMQ](https://www.rabbitmq.com/reliability.html#consumer), "Jeśli komunikat jest dostarczany do odbiorców, a następnie ponownie umieszczone w kolejce (ponieważ nie zostało potwierdzone, zanim konsumenta połączenie zostało przerwane, na przykład), a następnie RabbitMQ ustawi flagi redelivered na go po dostarczeniu ponownie (czy do tego samego użytkownika lub inną).</span><span class="sxs-lookup"><span data-stu-id="165d0-252">According to the [RabbitMQ documentation](https://www.rabbitmq.com/reliability.html#consumer), “If a message is delivered to a consumer and then requeued (because it was not acknowledged before the consumer connection dropped, for example) then RabbitMQ will set the redelivered flag on it when it is delivered again (whether to the same consumer or a different one).</span></span>

<span data-ttu-id="165d0-253">Jeśli flaga "redelivered" jest ustawiona, odbiorca musi uwzględniać który, ponieważ komunikat może być już zostały przetworzone.</span><span class="sxs-lookup"><span data-stu-id="165d0-253">If the “redelivered” flag is set, the receiver must take that into account, because the message might already have been processed.</span></span> <span data-ttu-id="165d0-254">Ale nie jest gwarantowana; komunikat, być może nigdy nie osiągnięto odbiornika od jego brokera komunikatów, prawdopodobnie z powodu problemów z siecią.</span><span class="sxs-lookup"><span data-stu-id="165d0-254">But that is not guaranteed; the message might never have reached the receiver after it left the message broker, perhaps because of network issues.</span></span> <span data-ttu-id="165d0-255">Z drugiej strony Jeśli nie ustawiono flagi "redelivered", ma żadnej gwarancji, że wiadomość nie została wysłana więcej niż jeden raz.</span><span class="sxs-lookup"><span data-stu-id="165d0-255">On the other hand, if the “redelivered” flag is not set, it is guaranteed that the message has not been sent more than once.</span></span> <span data-ttu-id="165d0-256">W związku z tym odbiorca musi deduplikacja wiadomości lub przetwarzania komunikatów w sposób idempotentne, tylko wtedy, gdy flaga "redelivered" jest ustawiona w komunikacie.</span><span class="sxs-lookup"><span data-stu-id="165d0-256">Therefore, the receiver needs to deduplicate messages or process messages in an idempotent way only if the “redelivered” flag is set in the message.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="165d0-257">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="165d0-257">Additional resources</span></span>

-   <span data-ttu-id="165d0-258">**Rozwidlone w ramach aplikacji eShopOnContainers przy użyciu NServiceBus (konkretnego oprogramowania)**</span><span class="sxs-lookup"><span data-stu-id="165d0-258">**Forked eShopOnContainers using NServiceBus (Particular Software)**</span></span> <br/>
    [*https://go.particular.net/eShopOnContainers*](https://go.particular.net/eShopOnContainers)

-   <span data-ttu-id="165d0-259">**Aktivita typu EventDriven komunikatów**</span><span class="sxs-lookup"><span data-stu-id="165d0-259">**Event Driven Messaging**</span></span> <br/>
    [*http://soapatterns.org/design\_patterns/event\_driven\_messaging*](http://soapatterns.org/design_patterns/event_driven_messaging)

-   <span data-ttu-id="165d0-260">**Jimmy Bogard. Refaktoryzacja kierunku odporności: Ocena sprzężenia**</span><span class="sxs-lookup"><span data-stu-id="165d0-260">**Jimmy Bogard. Refactoring Towards Resilience: Evaluating Coupling**</span></span> <br/>
    [*https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/*](https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/)

-   <span data-ttu-id="165d0-261">**Publikowanie/subskrybowanie kanałów**</span><span class="sxs-lookup"><span data-stu-id="165d0-261">**Publish-Subscribe channel**</span></span> <br/>
    [*https://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html*](https://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html)

-   <span data-ttu-id="165d0-262">**Komunikacja między ograniczone konteksty**</span><span class="sxs-lookup"><span data-stu-id="165d0-262">**Communicating Between Bounded Contexts**</span></span> <br/>
    [*https://msdn.microsoft.com/library/jj591572.aspx*](https://msdn.microsoft.com/library/jj591572.aspx)

-   <span data-ttu-id="165d0-263">**Spójność ostateczna**</span><span class="sxs-lookup"><span data-stu-id="165d0-263">**Eventual Consistency**</span></span> <br/>
    [*https://en.wikipedia.org/wiki/Eventual\_consistency*](https://en.wikipedia.org/wiki/Eventual_consistency)

-   <span data-ttu-id="165d0-264">**Philip Brown. Integrowanie strategii ograniczone konteksty**</span><span class="sxs-lookup"><span data-stu-id="165d0-264">**Philip Brown. Strategies for Integrating Bounded Contexts**</span></span> <br/>
    [*https://www.culttt.com/2014/11/26/strategies-integrating-bounded-contexts/*](https://www.culttt.com/2014/11/26/strategies-integrating-bounded-contexts/)

-   <span data-ttu-id="165d0-265">**Chris Leonard. Tworzenie Mikrousług transakcyjne przy użyciu wartości zagregowane, określania źródła zdarzeń i podejście CQRS — część 2**</span><span class="sxs-lookup"><span data-stu-id="165d0-265">**Chris Richardson. Developing Transactional Microservices Using Aggregates, Event Sourcing and CQRS - Part 2**</span></span> <br/>
    [*https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson*](https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson)

-   <span data-ttu-id="165d0-266">**Chris Leonard. Wzorzec określania źródła zdarzeń**</span><span class="sxs-lookup"><span data-stu-id="165d0-266">**Chris Richardson. Event Sourcing pattern**</span></span> <br/>
    [*https://microservices.io/patterns/data/event-sourcing.html*](https://microservices.io/patterns/data/event-sourcing.html)

-   <span data-ttu-id="165d0-267">**Wprowadzenie do określania źródła zdarzeń**</span><span class="sxs-lookup"><span data-stu-id="165d0-267">**Introducing Event Sourcing**</span></span> <br/>
    [*https://msdn.microsoft.com/library/jj591559.aspx*](https://msdn.microsoft.com/library/jj591559.aspx)

-   <span data-ttu-id="165d0-268">**Bazy danych zdarzeń Store**.</span><span class="sxs-lookup"><span data-stu-id="165d0-268">**Event Store database**.</span></span> <span data-ttu-id="165d0-269">Oficjalna witryna.</span><span class="sxs-lookup"><span data-stu-id="165d0-269">Official site.</span></span> <br/>
    [*https://geteventstore.com/*](https://geteventstore.com/)

-   <span data-ttu-id="165d0-270">**Patrick Nommensen. Zarządzanie oparte na zdarzeniach danych dla Mikrousług**</span><span class="sxs-lookup"><span data-stu-id="165d0-270">**Patrick Nommensen. Event-Driven Data Management for Microservices**</span></span> <br/>
    *<https://dzone.com/articles/event-driven-data-management-for-microservices-1> *

-   <span data-ttu-id="165d0-271">**Kolejnego elementu teorii CAP**</span><span class="sxs-lookup"><span data-stu-id="165d0-271">**The CAP Theorem**</span></span> <br/>
    [*https://en.wikipedia.org/wiki/CAP\_theorem*](https://en.wikipedia.org/wiki/CAP_theorem)

-   <span data-ttu-id="165d0-272">**Co to jest kolejnego elementu teorii CAP?**</span><span class="sxs-lookup"><span data-stu-id="165d0-272">**What is CAP Theorem?**</span></span> <br/>
    [*https://www.quora.com/What-Is-CAP-Theorem-1*](https://www.quora.com/What-Is-CAP-Theorem-1)

-   <span data-ttu-id="165d0-273">**Podstawy spójności danych**</span><span class="sxs-lookup"><span data-stu-id="165d0-273">**Data Consistency Primer**</span></span> <br/>
    [*https://msdn.microsoft.com/library/dn589800.aspx*](https://msdn.microsoft.com/library/dn589800.aspx)

-   <span data-ttu-id="165d0-274">**Rick Saling. Kolejnego elementu teorii CAP: Dlaczego "Wszystko, co jest różne" chmura i Internet**</span><span class="sxs-lookup"><span data-stu-id="165d0-274">**Rick Saling. The CAP Theorem: Why “Everything is Different” with the Cloud and Internet**</span></span> <br/>
    [*https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/*](https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/)

-   <span data-ttu-id="165d0-275">**Eric Brewera. LIMIT później dwunastu lat: jak "Zasady" zostały zmienione**</span><span class="sxs-lookup"><span data-stu-id="165d0-275">**Eric Brewer. CAP Twelve Years Later: How the "Rules" Have Changed**</span></span> <br/>
    [*https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed*](https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed)

-   <span data-ttu-id="165d0-276">**Azure Service Bus. Komunikaty obsługiwane przez brokera: Wykrywanie duplikatów**</span><span class="sxs-lookup"><span data-stu-id="165d0-276">**Azure Service Bus. Brokered Messaging: Duplicate Detection**</span></span>  <br/>
    [*https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25*](https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25)

-   <span data-ttu-id="165d0-277">**Przewodnik niezawodność** (dokumentacja RabbitMQ) \*</span><span class="sxs-lookup"><span data-stu-id="165d0-277">**Reliability Guide** (RabbitMQ documentation)\*</span></span> <br/>
    [*https://www.rabbitmq.com/reliability.html\#consumer*](https://www.rabbitmq.com/reliability.html#consumer)

-   <span data-ttu-id="165d0-278">**Udział w transakcji zewnętrznych (DTC)** (MSMQ)</span><span class="sxs-lookup"><span data-stu-id="165d0-278">**Participating in External (DTC) Transactions** (MSMQ)</span></span> <br/>
    [*https://msdn.microsoft.com/library/ms978430.aspx\#bdadotnetasync2\_topic3c*](https://msdn.microsoft.com/library/ms978430.aspx%23bdadotnetasync2_topic3c)

-   <span data-ttu-id="165d0-279">**Azure Service Bus. Komunikaty obsługiwane przez brokera: Wykrywanie duplikatów**</span><span class="sxs-lookup"><span data-stu-id="165d0-279">**Azure Service Bus. Brokered Messaging: Duplicate Detection**</span></span> <br/>
    [*https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25*](https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25)

-   <span data-ttu-id="165d0-280">**Przewodnik niezawodność** (dokumentacja RabbitMQ)</span><span class="sxs-lookup"><span data-stu-id="165d0-280">**Reliability Guide** (RabbitMQ documentation)</span></span> <br/>
    [*https://www.rabbitmq.com/reliability.html\#consumer*](https://www.rabbitmq.com/reliability.html%23consumer)




>[!div class="step-by-step"]
<span data-ttu-id="165d0-281">[Poprzednie](rabbitmq-event-bus-development-test-environment.md)
[dalej](test-aspnet-core-services-web-apps.md)</span><span class="sxs-lookup"><span data-stu-id="165d0-281">[Previous](rabbitmq-event-bus-development-test-environment.md)
[Next](test-aspnet-core-services-web-apps.md)</span></span>

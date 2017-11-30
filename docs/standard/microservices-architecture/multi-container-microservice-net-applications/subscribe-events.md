---
title: "Subskrybowanie zdarzeń"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Subskrybowanie zdarzeń"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: fe17b53a39ff2964cd60183e291e2936d3ba28df
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="subscribing-to-events"></a><span data-ttu-id="de018-104">Subskrybowanie zdarzeń</span><span class="sxs-lookup"><span data-stu-id="de018-104">Subscribing to events</span></span>

<span data-ttu-id="de018-105">Pierwszym krokiem przy użyciu magistrali zdarzeń jest jej zasubskrybowanie mikrousług do zdarzeń, które mają być wyświetlony.</span><span class="sxs-lookup"><span data-stu-id="de018-105">The first step for using the event bus is to subscribe the microservices to the events they want to receive.</span></span> <span data-ttu-id="de018-106">Który ma się odbywać w mikrousług odbiornika.</span><span class="sxs-lookup"><span data-stu-id="de018-106">That should be done in the receiver microservices.</span></span>

<span data-ttu-id="de018-107">Poniższy kod proste pokazuje, co każdy odbiorca mikrousługi należy zaimplementować podczas uruchamiania usługi (to znaczy w początkową klasy), subskrybuje zdarzenia go wymaga.</span><span class="sxs-lookup"><span data-stu-id="de018-107">The following simple code shows what each receiver microservice needs to implement when starting the service (that is, in the Startup class) so it subscribes to the events it needs.</span></span> <span data-ttu-id="de018-108">Na przykład mikrousługi basket.api musi subskrybować ProductPriceChangedIntegrationEvent wiadomości.</span><span class="sxs-lookup"><span data-stu-id="de018-108">For instance, the basket.api microservice needs to subscribe to ProductPriceChangedIntegrationEvent messages.</span></span> <span data-ttu-id="de018-109">Powoduje to mikrousługi żadnych zmian do ceny produktu i umożliwia mu Ostrzegaj użytkownika o zmianie w przypadku tego produktu jest w koszyku użytkownika.</span><span class="sxs-lookup"><span data-stu-id="de018-109">This makes the microservice aware of any changes to the product price and lets it warn the user about the change if that product is in the user’s basket.</span></span>

```csharp
var eventBus = app.ApplicationServices.GetRequiredService<IEventBus>();
eventBus.Subscribe<ProductPriceChangedIntegrationEvent>(
    ProductPriceChangedIntegrationEventHandler);
```

<span data-ttu-id="de018-110">Po uruchomieniu tego kodu mikrousługi subskrybent będzie nasłuchiwać kanałami RabbitMQ.</span><span class="sxs-lookup"><span data-stu-id="de018-110">After this code runs, the subscriber microservice will be listening through RabbitMQ channels.</span></span> <span data-ttu-id="de018-111">Po odebraniu żadnych wiadomości typu ProductPriceChangedIntegrationEvent, kod wywołuje program obsługi zdarzeń, która została przekazana do niej i przetwarza zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="de018-111">When any message of type ProductPriceChangedIntegrationEvent arrives, the code invokes the event handler that is passed to it and processes the event.</span></span>

## <a name="publishing-events-through-the-event-bus"></a><span data-ttu-id="de018-112">Publikowanie za pośrednictwem magistrali zdarzeń zdarzenia</span><span class="sxs-lookup"><span data-stu-id="de018-112">Publishing events through the event bus</span></span>

<span data-ttu-id="de018-113">Na koniec nadawcy wiadomości (pochodzenia mikrousługi) publikuje zdarzeń integracji z kodem podobny do poniższego przykładu.</span><span class="sxs-lookup"><span data-stu-id="de018-113">Finally, the message sender (origin microservice) publishes the integration events with code similar to the following example.</span></span> <span data-ttu-id="de018-114">(Jest to przykład uproszczony, które nie wymaga niepodzielność pod uwagę). Czy zaimplementowaniem podobny kod zawsze, gdy zdarzenie musi propagowane na wiele mikrousług, zazwyczaj prawo po zatwierdzania danych bądź transakcji z mikrousługi pochodzenia.</span><span class="sxs-lookup"><span data-stu-id="de018-114">(This is a simplified example that does not take atomicity into account.) You would implement similar code whenever an event must be propagated across multiple microservices, usually right after committing data or transactions from the origin microservice.</span></span>

<span data-ttu-id="de018-115">Po pierwsze obiekt implementacji magistrali zdarzenia (oparte na RabbitMQ lub oparte na usługi service bus) zostałyby dodane w Konstruktorze kontrolera, zgodnie z poniższym kodem:</span><span class="sxs-lookup"><span data-stu-id="de018-115">First, the event bus implementation object (based on RabbitMQ or based on a service bus) would be injected at the controller constructor, as in the following code:</span></span>

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

<span data-ttu-id="de018-116">Następnie używania jej metody dany kontroler, podobnie jak w metodę UpdateProduct:</span><span class="sxs-lookup"><span data-stu-id="de018-116">Then you use it from your controller’s methods, like in the UpdateProduct method:</span></span>

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

<span data-ttu-id="de018-117">W takim przypadku mikrousługi źródła jest proste mikrousługi CRUD, ten kod jest umieszczany po prawej w kontrolera interfejsu API sieci Web.</span><span class="sxs-lookup"><span data-stu-id="de018-117">In this case, since the origin microservice is a simple CRUD microservice, that code is placed right into a Web API controller.</span></span> <span data-ttu-id="de018-118">W bardziej zaawansowanym mikrousług go można można zaimplementować w klasie commandhandler — obiekt prawym po dba oryginalnych danych.</span><span class="sxs-lookup"><span data-stu-id="de018-118">In more advanced microservices, it could be implemented in the CommandHandler class, right after the original data is committed.</span></span>

### <a name="designing-atomicity-and-resiliency-when-publishing-to-the-event-bus"></a><span data-ttu-id="de018-119">Projektowanie niepodzielność i odporność podczas publikowania magistrali zdarzeń</span><span class="sxs-lookup"><span data-stu-id="de018-119">Designing atomicity and resiliency when publishing to the event bus</span></span>

<span data-ttu-id="de018-120">Podczas publikowania zdarzeń integracji przy użyciu rozproszonego wiadomości z magistrali zdarzeń, takich jak system, masz problem automatycznie aktualizuje oryginalnej bazy danych i publikowania zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="de018-120">When you publish integration events through a distributed messaging system like your event bus, you have the problem of atomically updating the original database and publishing an event.</span></span> <span data-ttu-id="de018-121">Na przykład w uproszczonym przykładzie pokazano wcześniej, kod zapisuje dane do bazy danych po cena produktu zostanie zmieniona, a następnie publikuje komunikat ProductPriceChangedIntegrationEvent.</span><span class="sxs-lookup"><span data-stu-id="de018-121">For instance, in the simplified example shown earlier, the code commits data to the database when the product price is changed and then publishes a ProductPriceChangedIntegrationEvent message.</span></span> <span data-ttu-id="de018-122">Początkowo może wyglądać niezbędne atomowo wykonanie tych dwóch operacji.</span><span class="sxs-lookup"><span data-stu-id="de018-122">Initially, it might look essential that these two operations be performed atomically.</span></span> <span data-ttu-id="de018-123">Jednak jeśli używasz transakcji rozproszonej obejmujące bazę danych i wiadomości broker, tak jak w starszych systemach, takich jak [usługi kolejkowania wiadomości firmy Microsoft (MSMQ)](https://msdn.microsoft.com/library/ms711472(v=vs.85).aspx), to nie jest zalecane z powodów opisanych przez [Newtona zakończenia](https://www.quora.com/What-Is-CAP-Theorem-1).</span><span class="sxs-lookup"><span data-stu-id="de018-123">However, if you are using a distributed transaction involving the database and the message broker, as you do in older systems like [Microsoft Message Queuing (MSMQ)](https://msdn.microsoft.com/library/ms711472(v=vs.85).aspx), this is not recommended for the reasons described by the [CAP theorem](https://www.quora.com/What-Is-CAP-Theorem-1).</span></span>

<span data-ttu-id="de018-124">Zasadniczo mikrousług służy do tworzenia systemów skalowalności i wysokiej dostępności.</span><span class="sxs-lookup"><span data-stu-id="de018-124">Basically, you use microservices to build scalable and highly available systems.</span></span> <span data-ttu-id="de018-125">Upraszczanie nieco, Newtona zakończenia informujący, że nie można utworzyć bazy danych (lub mikrousługi, który jest właścicielem jego model) jest stale dostępny, silnie spójne *i* odporne na partycji.</span><span class="sxs-lookup"><span data-stu-id="de018-125">Simplifying somewhat, the CAP theorem says that you cannot build a database (or a microservice that owns its model) that is continually available, strongly consistent, *and* tolerant to any partition.</span></span> <span data-ttu-id="de018-126">Musisz wybrać dwa z tych trzech właściwości.</span><span class="sxs-lookup"><span data-stu-id="de018-126">You must choose two of these three properties.</span></span>

<span data-ttu-id="de018-127">W podstawie mikrousług architektury należy wybrać dostępność i odporność na awarie, a powinien cieszących wysoki poziom spójności.</span><span class="sxs-lookup"><span data-stu-id="de018-127">In microservices-based architectures, you should choose availability and tolerance, and you should deemphasize strong consistency.</span></span> <span data-ttu-id="de018-128">W związku z tym w większość nowoczesnych aplikacji opartych na mikrousługi, zwykle nie chcesz używać transakcji rozproszonych w wiadomości, podobnie jak w przypadku implementowania [transakcje rozproszone](https://msdn.microsoft.com/library/ms978430.aspx#bdadotnetasync2_topic3c) oparte na transakcji rozproszonych systemu Windows Koordynator (transakcji rozproszonych DTC) z [MSMQ](https://msdn.microsoft.com/library/ms711472(v=vs.85).aspx).</span><span class="sxs-lookup"><span data-stu-id="de018-128">Therefore, in most modern microservice-based applications, you usually do not want to use distributed transactions in messaging, as you do when you implement [distributed transactions](https://msdn.microsoft.com/library/ms978430.aspx#bdadotnetasync2_topic3c) based on the Windows Distributed Transaction Coordinator (DTC) with [MSMQ](https://msdn.microsoft.com/library/ms711472(v=vs.85).aspx).</span></span>

<span data-ttu-id="de018-129">Przejdźmy do początkowej problemu i jego przykład.</span><span class="sxs-lookup"><span data-stu-id="de018-129">Let’s go back to the initial issue and its example.</span></span> <span data-ttu-id="de018-130">Jeśli usługa ulegnie awarii po zaktualizowaniu bazy danych (w tym przypadku od razu po wierszu kodu za pomocą \_kontekstu. SaveChangesAsync()), ale przed opublikowaniem zdarzeń integracji całego systemu może stać się niespójna.</span><span class="sxs-lookup"><span data-stu-id="de018-130">If the service crashes after the database is updated (in this case, right after the line of code with \_context.SaveChangesAsync()), but before the integration event is published, the overall system could become inconsistent.</span></span> <span data-ttu-id="de018-131">Może to być biznesowe krytyczne, w zależności od operacji firmy, który mamy do czynienia z.</span><span class="sxs-lookup"><span data-stu-id="de018-131">This might be business critical, depending on the specific business operation you are dealing with.</span></span>

<span data-ttu-id="de018-132">Jak wspomniano wcześniej, w sekcji architektury, może mieć kilka metod dotyczące tego problemu:</span><span class="sxs-lookup"><span data-stu-id="de018-132">As mentioned earlier in the architecture section, you can have several approaches for dealing with this issue:</span></span>

-   <span data-ttu-id="de018-133">Przy użyciu pełnego [źródłem zdarzeń wzorzec](https://msdn.microsoft.com/en-us/library/dn589792.aspx).</span><span class="sxs-lookup"><span data-stu-id="de018-133">Using the full [Event Sourcing pattern](https://msdn.microsoft.com/en-us/library/dn589792.aspx).</span></span>

-   <span data-ttu-id="de018-134">Przy użyciu [wyszukiwania dziennik transakcji](http://www.scoop.it/t/sql-server-transaction-log-mining).</span><span class="sxs-lookup"><span data-stu-id="de018-134">Using [transaction log mining](http://www.scoop.it/t/sql-server-transaction-log-mining).</span></span>

-   <span data-ttu-id="de018-135">Przy użyciu [wzorzec Skrzynka nadawcza](http://gistlabs.com/2014/05/the-outbox/).</span><span class="sxs-lookup"><span data-stu-id="de018-135">Using the [Outbox pattern](http://gistlabs.com/2014/05/the-outbox/).</span></span> <span data-ttu-id="de018-136">Jest to transakcyjne tabelę do przechowywania zdarzeń integracji (Rozszerzanie transakcji lokalnej).</span><span class="sxs-lookup"><span data-stu-id="de018-136">This is a transactional table to store the integration events (extending the local transaction).</span></span>

<span data-ttu-id="de018-137">W tym scenariuszu przy użyciu pełnego wzorca Sourcing zdarzenia (ES) jest jednym z najlepszych metod, jeśli nie *najlepsze*.</span><span class="sxs-lookup"><span data-stu-id="de018-137">For this scenario, using the full Event Sourcing (ES) pattern is one of the best approaches, if not *the* best.</span></span> <span data-ttu-id="de018-138">Jednak w wielu scenariuszach aplikacji, nie można przeprowadzić pełną wersją systemu ES.</span><span class="sxs-lookup"><span data-stu-id="de018-138">However, in many application scenarios, you might not be able to implement a full ES system.</span></span> <span data-ttu-id="de018-139">ES oznacza przechowywanie tylko zdarzenia domeny transakcyjne bazy danych, zamiast zapisywania danych stanu bieżącego.</span><span class="sxs-lookup"><span data-stu-id="de018-139">ES means storing only domain events in your transactional database, instead of storing current state data.</span></span> <span data-ttu-id="de018-140">Przechowywanie tylko zdarzenia domeny mogą mieć dużą korzyści, takich jak o historii dostępne systemu oraz możliwość określenia stanu systemu w dowolnym momencie w przeszłości.</span><span class="sxs-lookup"><span data-stu-id="de018-140">Storing only domain events can have great benefits, such as having the history of your system available and being able to determine the state of your system at any moment in the past.</span></span> <span data-ttu-id="de018-141">Jednak implementacja pełną wersją systemu ES wymaga rearchitect większość systemu i wprowadzono wiele skomplikowane i wymagań.</span><span class="sxs-lookup"><span data-stu-id="de018-141">However, implementing a full ES system requires you to rearchitect most of your system and introduces many other complexities and requirements.</span></span> <span data-ttu-id="de018-142">Na przykład, czy chcesz użyć bazy danych celowo dla źródeł zdarzeń, takich jak [magazynu zdarzeń](https://geteventstore.com/), lub z bazą zorientowane na dokument, takie jak bazy danych Azure rozwiązania Cosmos, bazy danych MongoDB, Cassandra, CouchDB lub RavenDB.</span><span class="sxs-lookup"><span data-stu-id="de018-142">For example, you would want to use a database specifically made for event sourcing, such as [Event Store](https://geteventstore.com/), or a document-oriented database such as Azure Cosmos DB, MongoDB, Cassandra, CouchDB, or RavenDB.</span></span> <span data-ttu-id="de018-143">ES jest doskonałe rozwiązanie ten problem, ale nie najlepszym rozwiązaniem, jeśli nie znasz już źródłem zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="de018-143">ES is a great approach for this problem, but not the easiest solution unless you are already familiar with event sourcing.</span></span>

<span data-ttu-id="de018-144">Możliwość użycia dziennika transakcji wyszukiwania początkowo wygląda bardzo przezroczysty.</span><span class="sxs-lookup"><span data-stu-id="de018-144">The option to use transaction log mining initially looks very transparent.</span></span> <span data-ttu-id="de018-145">Jednak aby użyć tej metody, mikrousługi ma zostać dołączone do RDBMS dziennika transakcji, takie jak dziennik transakcji programu SQL Server.</span><span class="sxs-lookup"><span data-stu-id="de018-145">However, to use this approach, the microservice has to be coupled to your RDBMS transaction log, such as the SQL Server transaction log.</span></span> <span data-ttu-id="de018-146">Prawdopodobnie nie jest to pożądane.</span><span class="sxs-lookup"><span data-stu-id="de018-146">This is probably not desirable.</span></span> <span data-ttu-id="de018-147">Inny wadą jest to, że na tym samym poziomie jako zdarzeń integracji wysokiego poziomu nie mogą być aktualizacje niskiego poziomu, rejestrowane w dzienniku transakcji.</span><span class="sxs-lookup"><span data-stu-id="de018-147">Another drawback is that the low-level updates recorded in the transaction log might not be at the same level as your high-level integration events.</span></span> <span data-ttu-id="de018-148">Jeśli tak, proces odtwarzania te operacje tworzenia dzienników transakcji może być trudne.</span><span class="sxs-lookup"><span data-stu-id="de018-148">If so, the process of reverse-engineering those transaction log operations can be difficult.</span></span>

<span data-ttu-id="de018-149">Zrównoważone podejście zależy od różnych czynników tabeli transakcyjne bazy danych oraz uproszczone wzorzec ES.</span><span class="sxs-lookup"><span data-stu-id="de018-149">A balanced approach is a mix of a transactional database table and a simplified ES pattern.</span></span> <span data-ttu-id="de018-150">Można użyć stanu, takie jak "gotowe do publikowania zdarzeń,", który ustawia w oryginalnej zdarzeń po zatwierdzeniu w tabeli zdarzeń integracji.</span><span class="sxs-lookup"><span data-stu-id="de018-150">You can use a state such as “ready to publish the event,” which you set in the original event when you commit it to the integration events table.</span></span> <span data-ttu-id="de018-151">A następnie spróbuj opublikować wydarzenie magistrali zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="de018-151">You then try to publish the event to the event bus.</span></span> <span data-ttu-id="de018-152">Jeśli akcja publikowania zdarzeń zakończy się powodzeniem, uruchomienie innej transakcji w usługi pochodzenia i przenieść stanu z "gotowe do opublikowania zdarzenia" do "zdarzenie już opublikowane."</span><span class="sxs-lookup"><span data-stu-id="de018-152">If the publish-event action succeeds, you start another transaction in the origin service and move the state from “ready to publish the event” to “event already published.”</span></span>

<span data-ttu-id="de018-153">Jeśli akcja publikowania zdarzeń w zdarzeniu magistrali kończy się niepowodzeniem, dane nadal nie będzie niespójne w ramach mikrousługi pochodzenia — nadal jest oznaczony jako "gotowy do publikowania zdarzenia", a w odniesieniu do pozostałych usług, po pewnym czasie będzie spójna.</span><span class="sxs-lookup"><span data-stu-id="de018-153">If the publish-event action in the event bus fails, the data still will not be inconsistent within the origin microservice—it is still marked as “ready to publish the event,” and with respect to the rest of the services, it will eventually be consistent.</span></span> <span data-ttu-id="de018-154">Użytkownik zawsze ma sprawdzanie stanu transakcji lub zdarzeń integracji zadań w tle.</span><span class="sxs-lookup"><span data-stu-id="de018-154">You can always have background jobs checking the state of the transactions or integration events.</span></span> <span data-ttu-id="de018-155">Jeśli zadanie znajdzie zdarzenia w stanie "gotowe do publikowania zdarzenia", może użyć ponownie opublikować tego zdarzenia do magistrali zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="de018-155">If the job finds an event in the “ready to publish the event” state, it can try to republish that event to the event bus.</span></span>

<span data-ttu-id="de018-156">Zwróć uwagę, że z tej metody można są utrwalanie integracji zdarzenia każdego mikrousługi pochodzenia i tylko zdarzenia, które chcesz komunikować się z innymi mikrousług lub systemami zewnętrznymi.</span><span class="sxs-lookup"><span data-stu-id="de018-156">Notice that with this approach, you are persisting only the integration events for each origin microservice, and only the events that you want to communicate to other microservices or external systems.</span></span> <span data-ttu-id="de018-157">Z kolei w pełnym systemie ES, są przechowywane wszystkie zdarzenia także domeny.</span><span class="sxs-lookup"><span data-stu-id="de018-157">In contrast, in a full ES system, you store all domain events as well.</span></span>

<span data-ttu-id="de018-158">W związku z tym takie podejście zrównoważonym to uproszczony system ES.</span><span class="sxs-lookup"><span data-stu-id="de018-158">Therefore, this balanced approach is a simplified ES system.</span></span> <span data-ttu-id="de018-159">Należy listę zdarzeń integracji z ich bieżącego stanu ("gotowe do opublikowania" i "opublikowane").</span><span class="sxs-lookup"><span data-stu-id="de018-159">You need a list of integration events with their current state (“ready to publish” versus “published”).</span></span> <span data-ttu-id="de018-160">Jednak należy implementować te stany zdarzeń integracji.</span><span class="sxs-lookup"><span data-stu-id="de018-160">But you only need to implement these states for the integration events.</span></span> <span data-ttu-id="de018-161">I w takie podejście, nie trzeba przechowywać wszystkie dane domeny jako zdarzeń w bazie danych transakcyjnych, tak jak w pełnym systemie ES.</span><span class="sxs-lookup"><span data-stu-id="de018-161">And in this approach, you do not need to store all your domain data as events in the transactional database, as you would in a full ES system.</span></span>

<span data-ttu-id="de018-162">Jeśli korzystasz już z relacyjnej bazy danych, można użyć transakcyjne tabelę do przechowywania zdarzeń integracji.</span><span class="sxs-lookup"><span data-stu-id="de018-162">If you are already using a relational database, you can use a transactional table to store integration events.</span></span> <span data-ttu-id="de018-163">Aby osiągnąć niepodzielność w aplikacji, należy użyć dwuetapowego procesu, na podstawie transakcji lokalnej.</span><span class="sxs-lookup"><span data-stu-id="de018-163">To achieve atomicity in your application, you use a two-step process based on local transactions.</span></span> <span data-ttu-id="de018-164">Zasadniczo ma tabeli IntegrationEvent w tej samej bazy danych, gdzie masz obiekty domeny.</span><span class="sxs-lookup"><span data-stu-id="de018-164">Basically, you have an IntegrationEvent table in the same database where you have your domain entities.</span></span> <span data-ttu-id="de018-165">Ta tabela będzie działać zgodnie z ubezpieczenia służące osiągnięciu niepodzielność tak, aby w przypadku uwzględnienia trwale zdarzeń integracji w tej samej transakcji, które są w trakcie zatwierdzania danych domeny.</span><span class="sxs-lookup"><span data-stu-id="de018-165">That table works as an insurance for achieving atomicity so that you include persisted integration events into the same transactions that are committing your domain data.</span></span>

<span data-ttu-id="de018-166">Krok po kroku proces przechodzi następująco: aplikacja zaczyna transakcji lokalnej bazy danych.</span><span class="sxs-lookup"><span data-stu-id="de018-166">Step by step, the process goes like this: the application begins a local database transaction.</span></span> <span data-ttu-id="de018-167">Następnie aktualizuje stan jednostki domeny i wstawia zdarzenia do tabeli zdarzeń integracji.</span><span class="sxs-lookup"><span data-stu-id="de018-167">It then updates the state of your domain entities and inserts an event into the integration event table.</span></span> <span data-ttu-id="de018-168">Na koniec go zatwierdza transakcji.</span><span class="sxs-lookup"><span data-stu-id="de018-168">Finally, it commits the transaction.</span></span> <span data-ttu-id="de018-169">Należy pobrać odpowiednią niepodzielność.</span><span class="sxs-lookup"><span data-stu-id="de018-169">You get the desired atomicity.</span></span>

<span data-ttu-id="de018-170">Podczas implementowania kroki publikowania zdarzenia, jest są dostępne poniższe opcje:</span><span class="sxs-lookup"><span data-stu-id="de018-170">When implementing the steps of publishing the events, you have these choices:</span></span>

-   <span data-ttu-id="de018-171">Publikowanie zdarzeń integracji bezpośrednio po zatwierdzania transakcji i użyj innego transakcji lokalnej, aby oznaczyć zdarzeń w tabeli jako opublikowane.</span><span class="sxs-lookup"><span data-stu-id="de018-171">Publish the integration event right after committing the transaction and use another local transaction to mark the events in the table as being published.</span></span> <span data-ttu-id="de018-172">Następnie skorzystaj z tabeli, podobnie jak artefaktów do śledzenia zdarzeń integracji w przypadku problemów dotyczących zdalnego mikrousług i akcje wyrównawczych na podstawie zdarzeń przechowywanych integracji.</span><span class="sxs-lookup"><span data-stu-id="de018-172">Then, use the table just as an artifact to track the integration events in case of issues in the remote microservices, and perform compensatory actions based on the stored integration events.</span></span>

-   <span data-ttu-id="de018-173">Skorzystaj z tabeli jako typu kolejki.</span><span class="sxs-lookup"><span data-stu-id="de018-173">Use the table as a kind of queue.</span></span> <span data-ttu-id="de018-174">Aplikacji oddzielnym wątku lub procesu zapytania w tabeli zdarzeń integracji, publikuje zdarzenia do zdarzenia magistrali, a następnie używa transakcji lokalnej do oznaczenia zdarzeń jako opublikowane.</span><span class="sxs-lookup"><span data-stu-id="de018-174">A separate application thread or process queries the integration event table, publishes the events to the event bus, and then uses a local transaction to mark the events as published.</span></span>

<span data-ttu-id="de018-175">Rysunek 8 do 22 przedstawiono architekturę, w pierwszym z tych metod.</span><span class="sxs-lookup"><span data-stu-id="de018-175">Figure 8-22 shows the architecture for the first of these approaches.</span></span>

![](./media/image23.png)

<span data-ttu-id="de018-176">**Rysunek 8 do 22**.</span><span class="sxs-lookup"><span data-stu-id="de018-176">**Figure 8-22**.</span></span> <span data-ttu-id="de018-177">Niepodzielność podczas publikowania zdarzeń w magistrali zdarzeń</span><span class="sxs-lookup"><span data-stu-id="de018-177">Atomicity when publishing events to the event bus</span></span>

<span data-ttu-id="de018-178">Podejście zilustrowane w rysunek 8 do 22 brakuje mikrousługi dodatkowe pracownika, który jest odpowiedzialny za sprawdzenie i potwierdzenie Powodzenie zdarzeń opublikowanej integracji.</span><span class="sxs-lookup"><span data-stu-id="de018-178">The approach illustrated in Figure 8-22 is missing an additional worker microservice that is in charge of checking and confirming the success of the published integration events.</span></span> <span data-ttu-id="de018-179">W razie awarii tego dodatkowe sprawdzanie mikrousługi proces roboczy może odczytywać zdarzenia z tabeli i opublikuj je ponownie.</span><span class="sxs-lookup"><span data-stu-id="de018-179">In case of failure, that additional checker worker microservice can read events from the table and republish them.</span></span>

<span data-ttu-id="de018-180">O drugiej metody: Tabela dziennika zdarzeń służy jako kolejki i zawsze używaj mikrousługi procesu roboczego do publikowania komunikatów.</span><span class="sxs-lookup"><span data-stu-id="de018-180">About the second approach: you use the EventLog table as a queue and always use a worker microservice to publish the messages.</span></span> <span data-ttu-id="de018-181">W takim przypadku proces tak jak pokazano w rysunek 8-23.</span><span class="sxs-lookup"><span data-stu-id="de018-181">In that case, the process is like that shown in Figure 8-23.</span></span> <span data-ttu-id="de018-182">Pokazuje dodatkowe mikrousługi, a tabela jest jedynym źródłem podczas publikowania zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="de018-182">This shows an additional microservice, and the table is the single source when publishing events.</span></span>

![](./media/image24.png)

<span data-ttu-id="de018-183">**Rysunek 8-23**.</span><span class="sxs-lookup"><span data-stu-id="de018-183">**Figure 8-23**.</span></span> <span data-ttu-id="de018-184">Niepodzielność podczas publikowania zdarzeń w magistrali zdarzeń z mikrousługi procesu roboczego</span><span class="sxs-lookup"><span data-stu-id="de018-184">Atomicity when publishing events to the event bus with a worker microservice</span></span>

<span data-ttu-id="de018-185">Dla uproszczenia próbki eShopOnContainers używa pierwszego podejścia (z nie dodatkowe procesy lub sprawdzania mikrousług) oraz magistrali zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="de018-185">For simplicity, the eShopOnContainers sample uses the first approach (with no additional processes or checker microservices) plus the event bus.</span></span> <span data-ttu-id="de018-186">Jednak eShopOnContainers nie obsługuje wszystkich przypadkach możliwe niepowodzenie.</span><span class="sxs-lookup"><span data-stu-id="de018-186">However, the eShopOnContainers is not handling all possible failure cases.</span></span> <span data-ttu-id="de018-187">W rzeczywistej aplikacji wdrożonych w chmurze musi obejmować fakt może spowodować problemy, którą musi implementować Sprawdź i Wyślij ponownie logiki.</span><span class="sxs-lookup"><span data-stu-id="de018-187">In a real application deployed to the cloud, you must embrace the fact that issues will arise eventually, and you must implement that check and resend logic.</span></span> <span data-ttu-id="de018-188">Przy użyciu tabeli jako kolejka może być bardziej efektywne niż pierwszego podejścia, jeśli masz tabeli jako pojedyncze źródło zdarzeń podczas publikowania ich za pośrednictwem magistrali zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="de018-188">Using the table as a queue can be more effective than the first approach if you have that table as a single source of events when publishing them through the event bus.</span></span>

### <a name="implementing-atomicity-when-publishing-integration-events-through-the-event-bus"></a><span data-ttu-id="de018-189">Implementowanie niepodzielność podczas publikowania zdarzenia integracja za pośrednictwem magistrali zdarzeń</span><span class="sxs-lookup"><span data-stu-id="de018-189">Implementing atomicity when publishing integration events through the event bus</span></span>

<span data-ttu-id="de018-190">Poniższy kod przedstawia sposób tworzenia pojedynczej transakcji obejmującego wiele obiektów DbContext — jeden kontekst związany z danymi aktualizowana, a drugi kontekst związany z tabeli IntegrationEventLog.</span><span class="sxs-lookup"><span data-stu-id="de018-190">The following code shows how you can create a single transaction involving multiple DbContext objects—one context related to the original data being updated, and the second context related to the IntegrationEventLog table.</span></span>

<span data-ttu-id="de018-191">Należy pamiętać, że transakcji w poniższym przykładowym kodzie nie będą odporne, jeśli połączenia z bazą danych mają jakikolwiek problem w czasie, gdy kod jest uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="de018-191">Note that the transaction in the example code below will not be resilient if connections to the database have any issue at the time when the code is running.</span></span> <span data-ttu-id="de018-192">Może to nastąpić w systemach opartych na chmurze, takich jak bazy danych SQL Azure, która może przenoszenia baz danych na serwerach.</span><span class="sxs-lookup"><span data-stu-id="de018-192">This can happen in cloud-based systems like Azure SQL DB, which might move databases across servers.</span></span> <span data-ttu-id="de018-193">Wykonania transakcji odporne na wielu kontekstów, zobacz [implementacja odporność połączeń Entity Framework Core SQL](#implementing_resilient_EFCore_SQL_conns) dalszej części tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="de018-193">For implementing resilient transactions across multiple contexts, see the [Implementing resilient Entity Framework Core SQL connections](#implementing_resilient_EFCore_SQL_conns) section later in this guide.</span></span>

<span data-ttu-id="de018-194">Dla uzyskania przejrzystości poniższy przykład przedstawia całego procesu w jednej części kodu.</span><span class="sxs-lookup"><span data-stu-id="de018-194">For clarity, the following example shows the whole process in a single piece of code.</span></span> <span data-ttu-id="de018-195">Jednak implementacja eShopOnContainers faktycznie został zrefaktoryzowany i podzielony na wiele klas tę logikę, dlatego jest łatwiejsze w obsłudze.</span><span class="sxs-lookup"><span data-stu-id="de018-195">However, the eShopOnContainers implementation is actually refactored and split this logic into multiple classes so it is easier to maintain.</span></span>

```csharp
// Update Product from the Catalog microservice
//
public async Task<IActionResult>
    UpdateProduct([FromBody]CatalogItem productToUpdate)
{
    var catalogItem = await _catalogContext.CatalogItems
        .SingleOrDefaultAsync(i => i.Id == productToUpdate.Id);

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

   // Publish to event bus only if product price changed

   if (raiseProductPriceChangedEvent)
   {
       _eventBus.Publish(priceChangedEvent);
       integrationEventLogService.MarkEventAsPublishedAsync(
           priceChangedEvent);
   }

   return Ok();
}
```

<span data-ttu-id="de018-196">Po utworzeniu zdarzenia integracji ProductPriceChangedIntegrationEvent transakcji, która przechowuje operację domeny (Aktualizacja elementów katalogu) zawiera również trwałości zdarzenia w dzienniku zdarzeń tabeli.</span><span class="sxs-lookup"><span data-stu-id="de018-196">After the ProductPriceChangedIntegrationEvent integration event is created, the transaction that stores the original domain operation (update the catalog item) also includes the persistence of the event in the EventLog table.</span></span> <span data-ttu-id="de018-197">Dzięki temu pojedynczej transakcji i zawsze będzie mógł sprawdzić, czy komunikaty o zdarzeniach zostały wysłane.</span><span class="sxs-lookup"><span data-stu-id="de018-197">This makes it a single transaction, and you will always be able to check whether event messages were sent.</span></span>

<span data-ttu-id="de018-198">Tabela dziennika zdarzeń jest aktualizowana automatycznie oryginalnej operacji bazy danych, przy użyciu transakcji lokalnej w tej samej bazie danych.</span><span class="sxs-lookup"><span data-stu-id="de018-198">The event log table is updated atomically with the original database operation, using a local transaction against the same database.</span></span> <span data-ttu-id="de018-199">W przypadku każdej operacji awarii, jest zgłaszany wyjątek i transakcji wycofuje wszystkie ukończoną operację, co umożliwia zachowanie spójności między operacjami domeny i wysyłane komunikaty o zdarzeniach.</span><span class="sxs-lookup"><span data-stu-id="de018-199">If any of the operations fail, an exception is thrown and the transaction rolls back any completed operation, thus maintaining consistency between the domain operations and the event messages sent.</span></span>

### <a name="receiving-messages-from-subscriptions-event-handlers-in-receiver-microservices"></a><span data-ttu-id="de018-200">Odbieranie komunikatów z subskrypcji: obsługi zdarzeń w mikrousług odbiornika</span><span class="sxs-lookup"><span data-stu-id="de018-200">Receiving messages from subscriptions: event handlers in receiver microservices</span></span>

<span data-ttu-id="de018-201">Oprócz zdarzenia logiki subskrypcji musisz wdrożyć wewnętrzny kod obsługi zdarzeń integracji (np. Metoda wywołania zwrotnego).</span><span class="sxs-lookup"><span data-stu-id="de018-201">In addition to the event subscription logic, you need to implement the internal code for the integration event handlers (like a callback method).</span></span> <span data-ttu-id="de018-202">Program obsługi zdarzeń określa się tam gdzie odbierane i przetwarzane komunikaty o zdarzeniach określonego typu.</span><span class="sxs-lookup"><span data-stu-id="de018-202">The event handler is where you specify where the event messages of a certain type will be received and processed.</span></span>

<span data-ttu-id="de018-203">Program obsługi zdarzeń otrzymuje najpierw wystąpienia zdarzenia z magistrali zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="de018-203">An event handler first receives an event instance from the event bus.</span></span> <span data-ttu-id="de018-204">Następnie klient zlokalizuje składnik do przetworzenia powiązany z tym zdarzeniem integracji propagowanie i przechowywanie zdarzenia jako zmianę stanu w mikrousługi odbiornika.</span><span class="sxs-lookup"><span data-stu-id="de018-204">Then it locates the component to be processed related to that integration event, propagating and persisting the event as a change in state in the receiver microservice.</span></span> <span data-ttu-id="de018-205">Na przykład, jeśli zdarzenie ProductPriceChanged pochodzi mikrousługi katalogu, jego jest obsługiwany w mikrousługi koszyka i zmienia stan w tym jak również odbiornik koszyka mikrousługi, jak pokazano w poniższym kodzie.</span><span class="sxs-lookup"><span data-stu-id="de018-205">For example, if a ProductPriceChanged event originates in the catalog microservice, it is handled in the basket microservice and changes the state in this receiver basket microservice as well, as shown in the following code.</span></span>

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

<span data-ttu-id="de018-206">Program obsługi zdarzeń musi sprawdzić, czy produkt istnieje w żadnym wystąpieniu koszyka.</span><span class="sxs-lookup"><span data-stu-id="de018-206">The event handler needs to verify whether the product exists in any of the basket instances.</span></span> <span data-ttu-id="de018-207">Aktualizuje również cenę dla każdej pozycji powiązanych koszyka.</span><span class="sxs-lookup"><span data-stu-id="de018-207">It also updates the item price for each related basket line item.</span></span> <span data-ttu-id="de018-208">Na koniec tworzy alert ma być wyświetlony dla użytkownika o zmianie cen, jak pokazano w rysunek 8 – 24.</span><span class="sxs-lookup"><span data-stu-id="de018-208">Finally, it creates an alert to be displayed to the user about the price change, as shown in Figure 8-24.</span></span>

![](./media/image25.png)

<span data-ttu-id="de018-209">**Rysunek 8 – 24**.</span><span class="sxs-lookup"><span data-stu-id="de018-209">**Figure 8-24**.</span></span> <span data-ttu-id="de018-210">Wyświetlanie zmiany ceny elementu w koszyka, ponieważ przekazywane przez zdarzeń integracji</span><span class="sxs-lookup"><span data-stu-id="de018-210">Displaying an item price change in a basket, as communicated by integration events</span></span>

## <a name="idempotency-in-update-message-events"></a><span data-ttu-id="de018-211">Idempotency w zdarzeniach komunikat aktualizacji</span><span class="sxs-lookup"><span data-stu-id="de018-211">Idempotency in update message events</span></span>

<span data-ttu-id="de018-212">Ważnym aspektem zdarzenia komunikat aktualizacji jest czy Niepowodzenie w dowolnym momencie w komunikacie powinno powodować komunikat ponowienie próby.</span><span class="sxs-lookup"><span data-stu-id="de018-212">An important aspect of update message events is that a failure at any point in the communication should cause the message to be retried.</span></span> <span data-ttu-id="de018-213">W przeciwnym razie zadanie w tle może podjąć próbę publikowania zdarzeń, który został już opublikowany, tworzenie wyścigu.</span><span class="sxs-lookup"><span data-stu-id="de018-213">Otherwise a background task might try to publish an event that has already been published, creating a race condition.</span></span> <span data-ttu-id="de018-214">Możesz należy się upewnić, że aktualizacje są idempotentności lub że zapewniają wystarczających informacji, aby upewnić się, że można wykryć duplikat, odrzucić go i wysłać odpowiedź wstecz tylko jeden.</span><span class="sxs-lookup"><span data-stu-id="de018-214">You need to make sure that the updates are either idempotent or that they provide enough information to ensure that you can detect a duplicate, discard it, and send back only one response.</span></span>

<span data-ttu-id="de018-215">Jak wspomniano wcześniej, idempotency oznacza, że operację można wykonać wiele razy bez zmieniania wynik.</span><span class="sxs-lookup"><span data-stu-id="de018-215">As noted earlier, idempotency means that an operation can be performed multiple times without changing the result.</span></span> <span data-ttu-id="de018-216">W środowisku obsługi komunikatów jak podczas komunikowania się zdarzenia, zdarzenie jest idempotentności, jeśli jego mogą być dostarczane wiele razy bez zmieniania wynik dla mikrousługi odbiornika.</span><span class="sxs-lookup"><span data-stu-id="de018-216">In a messaging environment, as when communicating events, an event is idempotent if it can be delivered multiple times without changing the result for the receiver microservice.</span></span> <span data-ttu-id="de018-217">Przyczyną może być konieczne rodzaj samym zdarzeniu lub ze względu na sposób system obsługuje zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="de018-217">This may be necessary because of the nature of the event itself, or because of the way the system handles the event.</span></span> <span data-ttu-id="de018-218">Komunikat idempotency ważne jest, w dowolnej aplikacji, która używa wiadomości, nie tylko w aplikacjach, które implementują wzorzec magistrali zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="de018-218">Message idempotency is important in any application that uses messaging, not just in applications that implement the event bus pattern.</span></span>

<span data-ttu-id="de018-219">Przykład operacji idempotentności to instrukcji SQL, która wstawia dane do tabeli, tylko wtedy, gdy dane nie jest już w tabeli.</span><span class="sxs-lookup"><span data-stu-id="de018-219">An example of an idempotent operation is a SQL statement that inserts data into a table only if that data is not already in the table.</span></span> <span data-ttu-id="de018-220">Nie ma znaczenia, ile razy można uruchomić, które wstawiają instrukcji SQL; wynik będzie taka sama — tabela będzie zawierać dane.</span><span class="sxs-lookup"><span data-stu-id="de018-220">It does not matter how many times you run that insert SQL statement; the result will be the same—the table will contain that data.</span></span> <span data-ttu-id="de018-221">Idempotency takie mogą być również konieczne podczas pracy nad komunikaty, jeśli potencjalnie być wysyłane komunikaty, w związku z tym przetworzonych więcej niż raz.</span><span class="sxs-lookup"><span data-stu-id="de018-221">Idempotency like this can also be necessary when dealing with messages if the messages could potentially be sent and therefore processed more than once.</span></span> <span data-ttu-id="de018-222">Na przykład jeśli Logika ponawiania powoduje, że nadawca wysłać tę samą wiadomość do więcej niż raz, musisz upewnij się, że jest idempotentności.</span><span class="sxs-lookup"><span data-stu-id="de018-222">For instance, if retry logic causes a sender to send exactly the same message more than once, you need to make sure that it is idempotent.</span></span>

<span data-ttu-id="de018-223">Istnieje możliwość do projektowania idempotentności wiadomości.</span><span class="sxs-lookup"><span data-stu-id="de018-223">It is possible to design idempotent messages.</span></span> <span data-ttu-id="de018-224">Na przykład można utworzyć zdarzenia informacją "ustawioną cena produktu \$25" zamiast "Dodaj \$5 ceny produktu."</span><span class="sxs-lookup"><span data-stu-id="de018-224">For example, you can create an event that says "set the product price to \$25" instead of "add \$5 to the product price."</span></span> <span data-ttu-id="de018-225">Można bezpiecznie przetwarzane pierwszą wiadomością dowolną liczbę razy i wyniki będą takie same.</span><span class="sxs-lookup"><span data-stu-id="de018-225">You could safely process the first message any number of times and the result will be the same.</span></span> <span data-ttu-id="de018-226">To nie jest to drugi komunikat wartość true.</span><span class="sxs-lookup"><span data-stu-id="de018-226">That is not true for the second message.</span></span> <span data-ttu-id="de018-227">Ale nawet w pierwszym przypadku nie można przetworzyć pierwsze zdarzenie, ponieważ system również mogły wysłać nowszej zdarzenia zmiany ceny i spowoduje zastąpienie nowej ceny.</span><span class="sxs-lookup"><span data-stu-id="de018-227">But even in the first case, you might not want to process the first event, because the system could also have sent a newer price-change event and you would be overwriting the new price.</span></span>

<span data-ttu-id="de018-228">Innym przykładem mogą być zakończone kolejność zdarzeń rozpropagowana na wielu subskrybentów.</span><span class="sxs-lookup"><span data-stu-id="de018-228">Another example might be an order-completed event being propagated to multiple subscribers.</span></span> <span data-ttu-id="de018-229">Jest ważne, że kolejność można zaktualizować informacji w innych systemach tylko raz, nawet w przypadku zduplikowanych komunikatów zdarzeń dla tego samego zdarzenia zakończone kolejności.</span><span class="sxs-lookup"><span data-stu-id="de018-229">It is important that order information be updated in other systems just once, even if there are duplicated message events for the same order-completed event.</span></span>

<span data-ttu-id="de018-230">Jest wygodną mają określonego rodzaju tożsamości na zdarzenie, aby tworzyć logikę, która wymusza, że każde zdarzenie jest przetwarzany tylko raz na odbiorcy.</span><span class="sxs-lookup"><span data-stu-id="de018-230">It is convenient to have some kind of identity per event so that you can create logic that enforces that each event is processed only once per receiver.</span></span>

<span data-ttu-id="de018-231">Przetwarza komunikat jest z założenia idempotentności.</span><span class="sxs-lookup"><span data-stu-id="de018-231">Some message processing is inherently idempotent.</span></span> <span data-ttu-id="de018-232">Na przykład jeśli system generuje obraz miniatury, jego może niezależnie od tego, ile razy komunikat o wygenerowanym miniatur jest przetwarzany; wynik jest generowane są miniatury oraz zawsze były takie same.</span><span class="sxs-lookup"><span data-stu-id="de018-232">For example, if a system generates image thumbnails, it might not matter how many times the message about the generated thumbnail is processed; the outcome is that the thumbnails are generated and they are the same every time.</span></span> <span data-ttu-id="de018-233">Z drugiej strony operacji, takich jak wywoływanie bramy płatności do obciążenia karty kredytowej nie może być idempotentności w ogóle.</span><span class="sxs-lookup"><span data-stu-id="de018-233">On the other hand, operations such as calling a payment gateway to charge a credit card may not be idempotent at all.</span></span> <span data-ttu-id="de018-234">W takich sytuacjach należy się upewnić, że przetwarza komunikat wielokrotnie ma wpływ, jaki oczekujesz.</span><span class="sxs-lookup"><span data-stu-id="de018-234">In these cases, you need to ensure that processing a message multiple times has the effect that you expect.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="de018-235">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="de018-235">Additional resources</span></span>

-   <span data-ttu-id="de018-236">**Ramach komunikat idempotency** (Podnagłówek na tej stronie) [ *https://msdn.microsoft.com/en-us/library/jj591565.aspx*](https://msdn.microsoft.com/en-us/library/jj591565.aspx)</span><span class="sxs-lookup"><span data-stu-id="de018-236">**Honoring message idempotency** (subhead on this page) [*https://msdn.microsoft.com/en-us/library/jj591565.aspx*](https://msdn.microsoft.com/en-us/library/jj591565.aspx)</span></span>

## <a name="deduplicating-integration-event-messages"></a><span data-ttu-id="de018-237">Ani deduplikacja komunikaty o zdarzeniach integracji</span><span class="sxs-lookup"><span data-stu-id="de018-237">Deduplicating integration event messages</span></span>

<span data-ttu-id="de018-238">Można upewnij się, że komunikat zdarzenia są wysyłane i przetwarzany tylko raz na subskrybenta na różnych poziomach.</span><span class="sxs-lookup"><span data-stu-id="de018-238">You can make sure that message events are sent and processed just once per subscriber at different levels.</span></span> <span data-ttu-id="de018-239">Jednym ze sposobów jest funkcja deduplikacji oferowane przez infrastruktury obsługi wiadomości, którego używasz.</span><span class="sxs-lookup"><span data-stu-id="de018-239">One way is to use a deduplication feature offered by the messaging infrastructure you are using.</span></span> <span data-ttu-id="de018-240">Inny jest zaimplementowanie niestandardowej logiki w sieci docelowej mikrousługi.</span><span class="sxs-lookup"><span data-stu-id="de018-240">Another is to implement custom logic in your destination microservice.</span></span> <span data-ttu-id="de018-241">Sprawdzanie poprawności zarówno na poziomie transportu, jak i na poziomie aplikacji jest najlepsze rozwiązanie.</span><span class="sxs-lookup"><span data-stu-id="de018-241">Having validations at both the transport level and the application level is your best bet.</span></span>

### <a name="deduplicating-message-events-at-the-eventhandler-level"></a><span data-ttu-id="de018-242">Ani deduplikacja komunikat zdarzenia na poziomie EventHandler</span><span class="sxs-lookup"><span data-stu-id="de018-242">Deduplicating message events at the EventHandler level</span></span>

<span data-ttu-id="de018-243">Jednym ze sposobów upewnij się, że zdarzenie jest przetwarzany tylko raz przez dowolnego odbiornika jest zaimplementowanie niektórych logiki podczas przetwarzania zdarzenia wiadomości w obsłudze zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="de018-243">One way to make sure that an event is processed just once by any receiver is by implementing certain logic when processing the message events in event handlers.</span></span> <span data-ttu-id="de018-244">Na przykład jest używany w aplikacji eShopOnContainers podejście jak widać w [kod źródłowy](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Controllers/OrdersController.cs) klasy OrdersController, gdy odbierze polecenie CreateOrderCommand.</span><span class="sxs-lookup"><span data-stu-id="de018-244">For example, that is the approach used in the eShopOnContainers application, as you can see in the [source code](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Controllers/OrdersController.cs) of the OrdersController class when it receives a CreateOrderCommand command.</span></span> <span data-ttu-id="de018-245">(W takim przypadku stosujemy polecenia żądania HTTP, nie na podstawie komunikatu polecenia, ale logiki należy idempotentności poleceń oparta na komunikat jest podobny).</span><span class="sxs-lookup"><span data-stu-id="de018-245">(In this case we use an HTTP request command, not a message-based command, but the logic you need to make a message-based command idempotent is similar.)</span></span>

### <a name="deduplicating-messages-when-using-rabbitmq"></a><span data-ttu-id="de018-246">Ani deduplikacja wiadomości, korzystając z RabbitMQ</span><span class="sxs-lookup"><span data-stu-id="de018-246">Deduplicating messages when using RabbitMQ</span></span>

<span data-ttu-id="de018-247">Gdy wystąpi sporadyczne awarie sieci, mogą być zduplikowane wiadomości, a odbiorca wiadomości musi być gotowy do obsługi tych zduplikowanych komunikatów.</span><span class="sxs-lookup"><span data-stu-id="de018-247">When intermittent network failures happen, messages can be duplicated, and the message receiver must be ready to handle these duplicated messages.</span></span> <span data-ttu-id="de018-248">Jeśli to możliwe odbiorcy powinna obsługiwać wiadomości w sposób idempotentności jest lepszym rozwiązaniem niż jawnie z włączoną funkcją deduplikacji ich obsługę.</span><span class="sxs-lookup"><span data-stu-id="de018-248">If possible, receivers should handle messages in an idempotent way, which is better than explicitly handling them with deduplication.</span></span>

<span data-ttu-id="de018-249">Zgodnie z [dokumentacji RabbitMQ](https://www.rabbitmq.com/reliability.html#consumer), "Jeśli wiadomości jest dostarczany do odbiorców, a następnie umieszczony w kolejce (ponieważ nie zostało potwierdzone, aby porzucić połączenia klienta, na przykład), a następnie RabbitMQ ustawi flagi redelivered na go po dostarczeniu ponownie (czy do tego samego użytkownika lub innego).</span><span class="sxs-lookup"><span data-stu-id="de018-249">According to the [RabbitMQ documentation](https://www.rabbitmq.com/reliability.html#consumer), “If a message is delivered to a consumer and then requeued (because it was not acknowledged before the consumer connection dropped, for example) then RabbitMQ will set the redelivered flag on it when it is delivered again (whether to the same consumer or a different one).</span></span>

<span data-ttu-id="de018-250">Jeśli jest ustawiona flaga "redelivered", odbiorca musi uwzględniać który, ponieważ komunikat może już zostały przetworzone.</span><span class="sxs-lookup"><span data-stu-id="de018-250">If the “redelivered” flag is set, the receiver must take that into account, because the message might already have been processed.</span></span> <span data-ttu-id="de018-251">Ale nie jest gwarantowana; komunikat, może nigdy nie osiągnięto odbiornika po pozostawiany brokera komunikatów z być może z powodu problemów dotyczących sieci.</span><span class="sxs-lookup"><span data-stu-id="de018-251">But that is not guaranteed; the message might never have reached the receiver after it left the message broker, perhaps because of network issues.</span></span> <span data-ttu-id="de018-252">Z drugiej strony Jeśli nie jest ustawiona flaga "redelivered", będzie gwarancji, że wiadomość nie została wysłana więcej niż raz.</span><span class="sxs-lookup"><span data-stu-id="de018-252">On the other hand, if the “redelivered” flag is not set, it is guaranteed that the message has not been sent more than once.</span></span> <span data-ttu-id="de018-253">W związku z tym odbiornika musi być deduplikowane wiadomości lub przetwarzania komunikatów w sposób idempotentności tylko wtedy, gdy flaga "redelivered" jest ustawiona w komunikacie.</span><span class="sxs-lookup"><span data-stu-id="de018-253">Therefore, the receiver needs to deduplicate messages or process messages in an idempotent way only if the “redelivered” flag is set in the message.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="de018-254">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="de018-254">Additional resources</span></span>

-   <span data-ttu-id="de018-255">**Zdarzenia zmiennych wiadomości**
    [*http://soapatterns.org/design\_wzorce lub zdarzenia\_zmiennych\_obsługi wiadomości*](http://soapatterns.org/design_patterns/event_driven_messaging)</span><span class="sxs-lookup"><span data-stu-id="de018-255">**Event Driven Messaging**
[*http://soapatterns.org/design\_patterns/event\_driven\_messaging*](http://soapatterns.org/design_patterns/event_driven_messaging)</span></span>

-   <span data-ttu-id="de018-256">**Jimmy Bogard. Refaktoryzacja kierunku odporności: Ocena sprzężenia**
    [*https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/*](https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/)</span><span class="sxs-lookup"><span data-stu-id="de018-256">**Jimmy Bogard. Refactoring Towards Resilience: Evaluating Coupling**
[*https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/*](https://jimmybogard.com/refactoring-towards-resilience-evaluating-coupling/)</span></span>

-   <span data-ttu-id="de018-257">**Kanał publikowania / subskrypcji**
    [*http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html*](http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html)</span><span class="sxs-lookup"><span data-stu-id="de018-257">**Publish-Subscribe channel**
[*http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html*](http://www.enterpriseintegrationpatterns.com/patterns/messaging/PublishSubscribeChannel.html)</span></span>

-   <span data-ttu-id="de018-258">**Komunikacja pomiędzy ograniczone kontekstów**
    [*https://msdn.microsoft.com/en-us/library/jj591572.aspx*](https://msdn.microsoft.com/en-us/library/jj591572.aspx)</span><span class="sxs-lookup"><span data-stu-id="de018-258">**Communicating Between Bounded Contexts**
[*https://msdn.microsoft.com/en-us/library/jj591572.aspx*](https://msdn.microsoft.com/en-us/library/jj591572.aspx)</span></span>

-   <span data-ttu-id="de018-259">**Spójność ostateczna**
    [*https://en.wikipedia.org/wiki/Eventual\_spójności*](https://en.wikipedia.org/wiki/Eventual_consistency)</span><span class="sxs-lookup"><span data-stu-id="de018-259">**Eventual Consistency**
[*https://en.wikipedia.org/wiki/Eventual\_consistency*](https://en.wikipedia.org/wiki/Eventual_consistency)</span></span>

-   <span data-ttu-id="de018-260">**Brązowy Philip. Strategie integrowanie ograniczone kontekstów**
    [*http://culttt.com/2014/11/26/strategies-integrating-bounded-contexts/*](http://culttt.com/2014/11/26/strategies-integrating-bounded-contexts/)</span><span class="sxs-lookup"><span data-stu-id="de018-260">**Philip Brown. Strategies for Integrating Bounded Contexts**
[*http://culttt.com/2014/11/26/strategies-integrating-bounded-contexts/*](http://culttt.com/2014/11/26/strategies-integrating-bounded-contexts/)</span></span>

-   <span data-ttu-id="de018-261">**Krzysztof Richardson. Tworzenie Mikrousług transakcyjne przy użyciu wartości zagregowanych, źródłem zdarzeń i CQRS — część 2**
    [*https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson*](https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson)</span><span class="sxs-lookup"><span data-stu-id="de018-261">**Chris Richardson. Developing Transactional Microservices Using Aggregates, Event Sourcing and CQRS - Part 2**
[*https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson*](https://www.infoq.com/articles/microservices-aggregates-events-cqrs-part-2-richardson)</span></span>

-   <span data-ttu-id="de018-262">**Krzysztof Richardson. Wzorzec wysyłanie zawartości zdarzeń**
    [*http://microservices.io/patterns/data/event-sourcing.html*](http://microservices.io/patterns/data/event-sourcing.html)</span><span class="sxs-lookup"><span data-stu-id="de018-262">**Chris Richardson. Event Sourcing pattern**
[*http://microservices.io/patterns/data/event-sourcing.html*](http://microservices.io/patterns/data/event-sourcing.html)</span></span>

-   <span data-ttu-id="de018-263">**Wprowadzenie Sourcing zdarzeń**
    [*https://msdn.microsoft.com/en-us/library/jj591559.aspx*](https://msdn.microsoft.com/en-us/library/jj591559.aspx)</span><span class="sxs-lookup"><span data-stu-id="de018-263">**Introducing Event Sourcing**
[*https://msdn.microsoft.com/en-us/library/jj591559.aspx*](https://msdn.microsoft.com/en-us/library/jj591559.aspx)</span></span>

-   <span data-ttu-id="de018-264">**Bazy danych zdarzeń magazynu**.</span><span class="sxs-lookup"><span data-stu-id="de018-264">**Event Store database**.</span></span> <span data-ttu-id="de018-265">Oficjalna witryna.</span><span class="sxs-lookup"><span data-stu-id="de018-265">Official site.</span></span>
    [<span data-ttu-id="de018-266">*https://geteventstore.com/*</span><span class="sxs-lookup"><span data-stu-id="de018-266">*https://geteventstore.com/*</span></span>](https://geteventstore.com/)

-   <span data-ttu-id="de018-267">**Patrick Nommensen. Zarządzanie danymi dla Mikrousług sterowane zdarzeniami**
    *<https://dzone.com/articles/event-driven-data-management-for-microservices-1>*</span><span class="sxs-lookup"><span data-stu-id="de018-267">**Patrick Nommensen. Event-Driven Data Management for Microservices**
*<https://dzone.com/articles/event-driven-data-management-for-microservices-1> *</span></span>

-   <span data-ttu-id="de018-268">**Newtona zakończenia**
    [*https://en.wikipedia.org/wiki/CAP\_Newtona*](https://en.wikipedia.org/wiki/CAP_theorem)</span><span class="sxs-lookup"><span data-stu-id="de018-268">**The CAP Theorem**
[*https://en.wikipedia.org/wiki/CAP\_theorem*](https://en.wikipedia.org/wiki/CAP_theorem)</span></span>

-   <span data-ttu-id="de018-269">**Co to jest zakończenie Newtona? ** 
     [ *https://www.quora.com/What-Is-CAP-Theorem-1*](https://www.quora.com/What-Is-CAP-Theorem-1)</span><span class="sxs-lookup"><span data-stu-id="de018-269">**What is CAP Theorem?**
[*https://www.quora.com/What-Is-CAP-Theorem-1*](https://www.quora.com/What-Is-CAP-Theorem-1)</span></span>

-   <span data-ttu-id="de018-270">**Elementarz spójności danych**
    [*https://msdn.microsoft.com/en-us/library/dn589800.aspx*](https://msdn.microsoft.com/en-us/library/dn589800.aspx)</span><span class="sxs-lookup"><span data-stu-id="de018-270">**Data Consistency Primer**
[*https://msdn.microsoft.com/en-us/library/dn589800.aspx*](https://msdn.microsoft.com/en-us/library/dn589800.aspx)</span></span>

-   <span data-ttu-id="de018-271">**Rick Saling. Newtona zakończenia: Dlaczego "Wszystko, co jest różne" z chmury i Internet**
    [*https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/*](https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/)</span><span class="sxs-lookup"><span data-stu-id="de018-271">**Rick Saling. The CAP Theorem: Why “Everything is Different” with the Cloud and Internet**
[*https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/*](https://blogs.msdn.microsoft.com/rickatmicrosoft/2013/01/03/the-cap-theorem-why-everything-is-different-with-the-cloud-and-internet/)</span></span>

-   <span data-ttu-id="de018-272">**Marek Brewera. Zakończenie później dwunastu lat: jak "Zasady" zostały zmienione**
    [*https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed*](https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed)</span><span class="sxs-lookup"><span data-stu-id="de018-272">**Eric Brewer. CAP Twelve Years Later: How the "Rules" Have Changed**
[*https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed*](https://www.infoq.com/articles/cap-twelve-years-later-how-the-rules-have-changed)</span></span>

-   <span data-ttu-id="de018-273">**Udział w transakcje zewnętrzne (DTC)** (MSMQ) [ *https://msdn.microsoft.com/en-us/library/ms978430.aspx\#bdadotnetasync2\_topic3c*](https://msdn.microsoft.com/en-us/library/ms978430.aspx%23bdadotnetasync2_topic3c)</span><span class="sxs-lookup"><span data-stu-id="de018-273">**Participating in External (DTC) Transactions** (MSMQ) [*https://msdn.microsoft.com/en-us/library/ms978430.aspx\#bdadotnetasync2\_topic3c*](https://msdn.microsoft.com/en-us/library/ms978430.aspx%23bdadotnetasync2_topic3c)</span></span>

-   <span data-ttu-id="de018-274">**Usługa Azure Service Bus. Komunikaty obsługiwane przez brokera: Wykrywanie duplikatów**
    [*https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25*](https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25)</span><span class="sxs-lookup"><span data-stu-id="de018-274">**Azure Service Bus. Brokered Messaging: Duplicate Detection**
[*https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25*](https://code.msdn.microsoft.com/Brokered-Messaging-c0acea25)</span></span>

-   <span data-ttu-id="de018-275">**Przewodnik niezawodności** (dokumentacja RabbitMQ) [ *https://www.rabbitmq.com/reliability.html\#konsumenta*](https://www.rabbitmq.com/reliability.html%23consumer)</span><span class="sxs-lookup"><span data-stu-id="de018-275">**Reliability Guide** (RabbitMQ documentation) [*https://www.rabbitmq.com/reliability.html\#consumer*](https://www.rabbitmq.com/reliability.html%23consumer)</span></span>




>[!div class="step-by-step"]
<span data-ttu-id="de018-276">[Poprzednie] (rabbitmq-event-bus-development-test-environment.md) [dalej] (test-aspnet-core-services-web-apps.md)</span><span class="sxs-lookup"><span data-stu-id="de018-276">[Previous] (rabbitmq-event-bus-development-test-environment.md) [Next] (test-aspnet-core-services-web-apps.md)</span></span>

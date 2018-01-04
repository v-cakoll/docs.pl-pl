---
title: "Implementowanie modelu domeny mikrousługi z platformą .NET Core"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Implementowanie modelu domeny mikrousługi z platformą .NET Core"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/09/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 07a79f3d52db400d1539fb4172166cccf8905fb8
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="implementing-a-microservice-domain-model-with-net-core"></a><span data-ttu-id="dceed-104">Implementowanie modelu domeny mikrousługi z platformą .NET Core</span><span class="sxs-lookup"><span data-stu-id="dceed-104">Implementing a microservice domain model with .NET Core</span></span> 

<span data-ttu-id="dceed-105">W poprzedniej sekcji zostały wyjaśnione zasady projektowania podstawowych i wzorce projektowania modelu domeny.</span><span class="sxs-lookup"><span data-stu-id="dceed-105">In the previous section, the fundamental design principles and patterns for designing a domain model were explained.</span></span> <span data-ttu-id="dceed-106">Teraz nadszedł czas, aby poznać możliwości, aby wdrożyć model domeny przy użyciu platformy .NET Core (zwykły C\# kodu) i EF podstawowe.</span><span class="sxs-lookup"><span data-stu-id="dceed-106">Now it is time to explore possible ways to implement the domain model by using .NET Core (plain C\# code) and EF Core.</span></span> <span data-ttu-id="dceed-107">Należy pamiętać, że model domeny będzie składać się z kodu.</span><span class="sxs-lookup"><span data-stu-id="dceed-107">Note that your domain model will be composed simply of your code.</span></span> <span data-ttu-id="dceed-108">Na EF będzie mieć tylko podstawowe EF wymagania modelu, ale nie rzeczywistych zależności.</span><span class="sxs-lookup"><span data-stu-id="dceed-108">It will have just the EF Core model requirements, but not real dependencies on EF.</span></span> <span data-ttu-id="dceed-109">Nie powinna mieć twarde zależności lub odwołania do podstawowych funkcji EF lub innych ORM modelu domeny.</span><span class="sxs-lookup"><span data-stu-id="dceed-109">You should not have hard dependencies or references to EF Core or any other ORM in your domain model.</span></span>

## <a name="domain-model-structure-in-a-custom-net-standard-library"></a><span data-ttu-id="dceed-110">Struktura modelu domeny niestandardowe biblioteki .NET Standard</span><span class="sxs-lookup"><span data-stu-id="dceed-110">Domain model structure in a custom .NET Standard library</span></span>

<span data-ttu-id="dceed-111">Organizacja folderu używane dla aplikacji odwołanie eShopOnContainers pokazuje DDD modelu dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dceed-111">The folder organization used for the eShopOnContainers reference application demonstrates the DDD model for the application.</span></span> <span data-ttu-id="dceed-112">Może się okazać, że organizacja inny folder dokładniej komunikuje się decyzji projektowych dotyczących aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dceed-112">You might find that a different folder organization more clearly communicates the design choices made for your application.</span></span> <span data-ttu-id="dceed-113">Jak widać w rysunek 9 – 10 w porządkowania modelu domeny istnieją agregatów, zagregowany kolejności i nabywców agregacji.</span><span class="sxs-lookup"><span data-stu-id="dceed-113">As you can see in Figure 9-10, in the ordering domain model there are two aggregates, the order aggregate and the buyer aggregate.</span></span> <span data-ttu-id="dceed-114">Każdego agregacji jest grupą domeny jednostek i obiektów wartość, mimo że agregacji składa się z jednostek jednej domenie, (łączny głównego lub podmiot główny) również może mieć.</span><span class="sxs-lookup"><span data-stu-id="dceed-114">Each aggregate is a group of domain entities and value objects, although you could have an aggregate composed of a single domain entity (the aggregate root or root entity) as well.</span></span>

![](./media/image11.png)

<span data-ttu-id="dceed-115">**Rysunek 9 – 10**.</span><span class="sxs-lookup"><span data-stu-id="dceed-115">**Figure 9-10**.</span></span> <span data-ttu-id="dceed-116">Struktura modelu domeny dla porządkowania mikrousługi w eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="dceed-116">Domain model structure for the ordering microservice in eShopOnContainers</span></span>

<span data-ttu-id="dceed-117">Ponadto warstwy modelu domeny obejmuje kontrakty repozytorium (interfejsy), które są wymagania dotyczące infrastruktury modelu domeny.</span><span class="sxs-lookup"><span data-stu-id="dceed-117">Additionally, the domain model layer includes the repository contracts (interfaces) that are the infrastructure requirements of your domain model.</span></span> <span data-ttu-id="dceed-118">Innymi słowy, te interfejsy express repozytoriów, jakie musi implementować warstwę infrastruktury i w jaki sposób.</span><span class="sxs-lookup"><span data-stu-id="dceed-118">In other words, these interfaces express what repositories the infrastructure layer must implement and how.</span></span> <span data-ttu-id="dceed-119">Jest krytyczny, że implementacja repozytoriów można umieścić poza warstwy modelu domeny, w bibliotece warstwę infrastruktury tak warstwy modelu domeny jest nie "zanieczyszczone" interfejsu API lub klas z technologii infrastruktury, takich jak Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="dceed-119">It is critical that the implementation of the repositories be placed outside of the domain model layer, in the infrastructure layer library, so the domain model layer is not “contaminated” by API or classes from infrastructure technologies, like Entity Framework.</span></span>

<span data-ttu-id="dceed-120">Możesz również sprawdzić [SeedWork](https://martinfowler.com/bliki/Seedwork.html) folder zawierający niestandardowe klasy bazowej, która służy jako podstawa dla jednostek domeny i wartość obiekty, dlatego nie masz nadmiarowy kod w klasie obiektów w każdej domenie.</span><span class="sxs-lookup"><span data-stu-id="dceed-120">You can also see a [SeedWork](https://martinfowler.com/bliki/Seedwork.html) folder that contains custom base classes that you can use as a base for your domain entities and value objects, so you do not have redundant code in each domain’s object class.</span></span>

## <a name="structuring-aggregates-in-a-custom-net-standard-library"></a><span data-ttu-id="dceed-121">Struktury wartości zagregowanych w niestandardowa biblioteka .NET Standard</span><span class="sxs-lookup"><span data-stu-id="dceed-121">Structuring aggregates in a custom .NET Standard library</span></span>

<span data-ttu-id="dceed-122">Wartość zagregowana odwołuje się do klastra obiektów domeny zgrupowane w celu dopasowania spójności transakcyjnej.</span><span class="sxs-lookup"><span data-stu-id="dceed-122">An aggregate refers to a cluster of domain objects grouped together to match transactional consistency.</span></span> <span data-ttu-id="dceed-123">Te obiekty można wystąpienia jednostek (z których jeden jest łączny głównego lub podmiot główny) oraz wszystkie obiekty dodatkowe wartości.</span><span class="sxs-lookup"><span data-stu-id="dceed-123">Those objects could be instances of entities (one of which is the aggregate root or root entity) plus any additional value objects.</span></span>

<span data-ttu-id="dceed-124">Spójności transakcyjnej oznacza, że agregacji gwarantuje to spójność i na bieżąco na koniec działania biznesowe.</span><span class="sxs-lookup"><span data-stu-id="dceed-124">Transactional consistency means that an aggregate is guaranteed to be consistent and up to date at the end of a business action.</span></span> <span data-ttu-id="dceed-125">Na przykład agregacji kolejności z eShopOnContainers kolejność modelu domeny mikrousługi składa się jak pokazano w rysunek 9-11.</span><span class="sxs-lookup"><span data-stu-id="dceed-125">For example, the order aggregate from the eShopOnContainers ordering microservice domain model is composed as shown in Figure 9-11.</span></span>

![](./media/image12.png)

<span data-ttu-id="dceed-126">**Rysunek 9-11**.</span><span class="sxs-lookup"><span data-stu-id="dceed-126">**Figure 9-11**.</span></span> <span data-ttu-id="dceed-127">Kolejność agregacji w rozwiązaniu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="dceed-127">The order aggregate in Visual Studio solution</span></span>

<span data-ttu-id="dceed-128">Po otwarciu plików w folderze agregacji widać jak jest oznaczony jako niestandardowej klasy podstawowej lub interfejsu, takich jak jednostka lub wartość obiektu, zgodnie z implementacją w [Seedwork](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.Domain/SeedWork) folderu.</span><span class="sxs-lookup"><span data-stu-id="dceed-128">If you open any of the files in an aggregate folder, you can see how it is marked as either a custom base class or interface, like entity or value object, as implemented in the [Seedwork](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.Domain/SeedWork) folder.</span></span>

## <a name="implementing-domain-entities-as-poco-classes"></a><span data-ttu-id="dceed-129">Implementowanie jednostek domeny jako klasy POCO</span><span class="sxs-lookup"><span data-stu-id="dceed-129">Implementing domain entities as POCO classes</span></span>

<span data-ttu-id="dceed-130">Model domeny można zaimplementować w .NET przez utworzenie klas POCO, które implementują obiekty domeny.</span><span class="sxs-lookup"><span data-stu-id="dceed-130">You implement a domain model in .NET by creating POCO classes that implement your domain entities.</span></span> <span data-ttu-id="dceed-131">W poniższym przykładzie klasa kolejności jest zdefiniowana jako jednostki, a także jako główny agregacji.</span><span class="sxs-lookup"><span data-stu-id="dceed-131">In the following example, the Order class is defined as an entity and also as an aggregate root.</span></span> <span data-ttu-id="dceed-132">Ponieważ klasa kolejności pochodzi od klasy podstawowej jednostki, można użyć ponownie typowy Kod powiązane z jednostkami.</span><span class="sxs-lookup"><span data-stu-id="dceed-132">Because the Order class derives from the Entity base class, it can reuse common code related to entities.</span></span> <span data-ttu-id="dceed-133">Przy tym pamiętać, że te klasy podstawowe i interfejsy są zdefiniowane przez użytkownika w projekcie modelu domeny, więc Twojej kod, nie infrastrukturze kod z ORM, takich jak EF.</span><span class="sxs-lookup"><span data-stu-id="dceed-133">Bear in mind that these base classes and interfaces are defined by you in the domain model project, so it is your code, not infrastructure code from an ORM like EF.</span></span>

```csharp
// COMPATIBLE WITH ENTITY FRAMEWORK CORE 2.0
// Entity is a custom base class with the ID
public class Order : Entity, IAggregateRoot
{
    private DateTime _orderDate;
    public Address Address { get; private set; }
    private int? _buyerId;

    public OrderStatus OrderStatus { get; private set; }
    private int _orderStatusId;

    private string _description;
    private int? _paymentMethodId;

    private readonly List<OrderItem> _orderItems;
    public IReadOnlyCollection<OrderItem> OrderItems => _orderItems;
  
    public Order(string userId, Address address, int cardTypeId, string cardNumber, string cardSecurityNumber,
            string cardHolderName, DateTime cardExpiration, int? buyerId = null, int? paymentMethodId = null)
    {
        _orderItems = new List<OrderItem>();
        _buyerId = buyerId;
        _paymentMethodId = paymentMethodId;
        _orderStatusId = OrderStatus.Submitted.Id;
        _orderDate = DateTime.UtcNow;
        Address = address;

        // ...Additional code ...
    }

    public void AddOrderItem(int productId, string productName, 
                            decimal unitPrice, decimal discount, 
                            string pictureUrl, int units = 1)
    {
        //...
        // Domain rules/logic for adding the OrderItem to the order
        // ...

        var orderItem = new OrderItem(productId, productName, unitPrice, discount, pictureUrl, units);
        
        _orderItems.Add(orderItem);
  
    }
    // ...
    // Additional methods with domain rules/logic related to the Order aggregate
    // ...
}
```

<span data-ttu-id="dceed-134">Należy zauważyć, że jest jednostką domeny, zaimplementowane jako klasa POCO.</span><span class="sxs-lookup"><span data-stu-id="dceed-134">It is important to note that this is a domain entity implemented as a POCO class.</span></span> <span data-ttu-id="dceed-135">Nie ma żadnych bezpośrednich zależność od Entity Framework Core lub inne struktury infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="dceed-135">It does not have any direct dependency on Entity Framework Core or any other infrastructure framework.</span></span> <span data-ttu-id="dceed-136">Ta implementacja jest powinny być w DDD, po prostu C\# kod implementacji modelu domeny.</span><span class="sxs-lookup"><span data-stu-id="dceed-136">This implementation is as it should be in DDD, just C\# code implementing a domain model.</span></span>

<span data-ttu-id="dceed-137">Ponadto klasa zostanie nadany interfejsu o nazwie IAggregateRoot.</span><span class="sxs-lookup"><span data-stu-id="dceed-137">In addition, the class is decorated with an interface named IAggregateRoot.</span></span> <span data-ttu-id="dceed-138">Ten interfejs jest interfejsem pusta, nazywane również *interfejsu znacznika*, która jest używana tylko w celu oznaczać, że ta klasa jednostki jest również głównego agregacji.</span><span class="sxs-lookup"><span data-stu-id="dceed-138">That interface is an empty interface, sometimes called a *marker interface*, that is used just to indicate that this entity class is also an aggregate root.</span></span>

<span data-ttu-id="dceed-139">Interfejs znacznika czasami jest uznawany za wzorca oprogramowania; jednak również to czysta sposób Oznacz klasę, szczególnie w przypadku, gdy ten interfejs może rozwijającymi.</span><span class="sxs-lookup"><span data-stu-id="dceed-139">A marker interface is sometimes considered as an anti-pattern; however, it is also a clean way to mark a class, especially when that interface might be evolving.</span></span> <span data-ttu-id="dceed-140">Atrybut może być inne wybór dla znacznika, ale jest szybsze wyświetlić klasy podstawowej (jednostka) obok interfejsu IAggregate zamiast umieszczanie znacznika atrybutu agregacji powyżej klasy.</span><span class="sxs-lookup"><span data-stu-id="dceed-140">An attribute could be the other choice for the marker, but it is quicker to see the base class (Entity) next to the IAggregate interface instead of putting an Aggregate attribute marker above the class.</span></span> <span data-ttu-id="dceed-141">Metter preferencji, jest w każdym przypadku.</span><span class="sxs-lookup"><span data-stu-id="dceed-141">It is a metter of preferences, in any case.</span></span>

<span data-ttu-id="dceed-142">O oznacza głównego agregacji, że większość kod powiązany spójności i reguły biznesowe jednostek wartości zagregowanej powinny zostać wdrożone jako metod klasy głównym agregacji kolejności (na przykład AddOrderItem podczas dodawania obiektu OrderItem do agregacji) .</span><span class="sxs-lookup"><span data-stu-id="dceed-142">Having an aggregate root means that most of the code related to consistency and business rules of the aggregate’s entities should be implemented as methods in the Order aggregate root class (for example, AddOrderItem when adding an OrderItem object to the aggregate).</span></span> <span data-ttu-id="dceed-143">Nie należy utworzyć ani zaktualizować obiektów OrderItems niezależnie lub bezpośrednio; Klasa AggregateRoot musi przechowywać i kontroli spójności żadnej operacji aktualizacji, przed jego obiektów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="dceed-143">You should not create or update OrderItems objects independently or directly; the AggregateRoot class must keep control and consistency of any update operation against its child entities.</span></span>

## <a name="encapsulating-data-in-the-domain-entities"></a><span data-ttu-id="dceed-144">Zawieranie dane w jednostkach domeny</span><span class="sxs-lookup"><span data-stu-id="dceed-144">Encapsulating data in the Domain Entities</span></span>

<span data-ttu-id="dceed-145">To powszechny problem w modelach jednostki jest czy udostępniają właściwości nawigacji kolekcji jako typów list publicznie.</span><span class="sxs-lookup"><span data-stu-id="dceed-145">A common problem in entity models is that they expose collection navigation properties as publicly accessible list types.</span></span> <span data-ttu-id="dceed-146">Dzięki temu każdy Deweloper współpracownika do manipulowania zawartość te typy kolekcji, których może pominąć ważnymi reguł związanych z kolekcji, prawdopodobnie pozostawienie obiektu w nieprawidłowym stanie.</span><span class="sxs-lookup"><span data-stu-id="dceed-146">This allows any collaborator developer to manipulate the contents of these collection types, which may bypass important business rules related to the collection, possibly leaving the object in an invalid state.</span></span> <span data-ttu-id="dceed-147">To rozwiązanie jest ujawnia dostęp tylko do odczytu do kolekcji powiązanych i jawnie Podaj metod, które definiują sposób, w którym klienci można przekształcać je.</span><span class="sxs-lookup"><span data-stu-id="dceed-147">The solution to this is to expose read-only access to related collections and explicitly provide methods that define ways in which clients can manipulate them.</span></span>

<span data-ttu-id="dceed-148">W poprzednim kodzie należy zauważyć, że wiele atrybutów są tylko do odczytu lub prywatnych i tylko są tak Każda aktualizacja uwzględnia invariants domeny business konta i logikę określoną w ramach metod klasy nadaje się do aktualizacji za pomocą metod klasy.</span><span class="sxs-lookup"><span data-stu-id="dceed-148">In the previous code, note that many attributes are read-only or private and are only updatable by the class methods, so any update takes into account business domain invariants and logic specified within the class methods.</span></span>

<span data-ttu-id="dceed-149">Na przykład następujące wzorce DDD należy *nie* wykonaj następujące czynności z dowolnej polecenie obsługi metody lub aplikacji warstwy klasy:</span><span class="sxs-lookup"><span data-stu-id="dceed-149">For example, following DDD patterns, you should *not* do the following from any command handler method or application layer class:</span></span>

```csharp
// WRONG ACCORDING TO DDD PATTERNS – CODE AT THE APPLICATION LAYER OR
// COMMAND HANDLERS
// Code in command handler methods or Web API controllers
//... (WRONG) Some code with business logic out of the domain classes ...
OrderItem myNewOrderItem = new OrderItem(orderId, productId, productName,
    pictureUrl, unitPrice, discount, units);

//... (WRONG) Accessing the OrderItems colletion directly from the application layer // or command handlers
myOrder.OrderItems.Add(myNewOrderItem);
//...
```

<span data-ttu-id="dceed-150">W tym przypadku metoda Add jest wyłącznie operacji dodawania danych, za pomocą bezpośredniego dostępu do kolekcji OrderItems.</span><span class="sxs-lookup"><span data-stu-id="dceed-150">In this case, the Add method is purely an operation to add data, with direct access to the OrderItems collection.</span></span> <span data-ttu-id="dceed-151">W związku z tym większość logika domeny, reguł lub Sprawdzanie poprawności dotyczące czy operację, podając obiektów podrzędnych będą rozkładane warstwy aplikacji (programy obsługi poleceń i kontrolery interfejsu API sieci Web).</span><span class="sxs-lookup"><span data-stu-id="dceed-151">Therefore, most of the domain logic, rules, or validations related to that operation with the child entities will be spread across the application layer (command handlers and Web API controllers).</span></span>

<span data-ttu-id="dceed-152">Przejście wokół agregacji głównego agregacji głównego nie może zagwarantować jego invariants, ważności lub jego spójności.</span><span class="sxs-lookup"><span data-stu-id="dceed-152">If you go around the aggregate root, the aggregate root cannot guarantee its invariants, its validity, or its consistency.</span></span> <span data-ttu-id="dceed-153">Po pewnym czasie będzie mieć postaci spaghetti kod lub skrypt kod.</span><span class="sxs-lookup"><span data-stu-id="dceed-153">Eventually you will have spaghetti code or transactional script code.</span></span>

<span data-ttu-id="dceed-154">Wykonać wzorce DDD, jednostki nie może mieć publicznych ustawiające w dowolnej właściwości jednostki.</span><span class="sxs-lookup"><span data-stu-id="dceed-154">To follow DDD patterns, entities must not have public setters in any entity property.</span></span> <span data-ttu-id="dceed-155">Zmian w jednostce powinny być regulowane przez jawnych metod jawne języka powszechna o zmianie, które działają one w jednostce.</span><span class="sxs-lookup"><span data-stu-id="dceed-155">Changes in an entity should be driven by explicit methods with explicit ubiquitous language about the change they are performing in the entity.</span></span>

<span data-ttu-id="dceed-156">Ponadto, kolekcje w ramach jednostki (np. kolejność elementów) powinny być właściwości tylko do odczytu (metoda AsReadOnly wyjaśniono później).</span><span class="sxs-lookup"><span data-stu-id="dceed-156">Furthermore, collections within the entity (like the order items) should be read-only properties (the AsReadOnly method explained later).</span></span> <span data-ttu-id="dceed-157">Można zaktualizować tylko z metod klasy głównym agregacji lub metody jednostek podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="dceed-157">You should be able to update it only from within the aggregate root class methods or the child entity methods.</span></span>

<span data-ttu-id="dceed-158">Jak widać w kodzie dla elementu głównego agregacji w kolejności, wszystkie metody ustawiające powinny być prywatne lub co najmniej tylko do odczytu zewnętrznie, dzięki czemu ma być wykonywane za pomocą metod w klasie jednostki żadnej operacji względem danych jednostki lub jego obiektów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="dceed-158">As you can see in the code for the Order aggregate root, all setters should be private or at least read-only externally, so that any operation against the entity’s data or its child entities has to be performed through methods in the entity class.</span></span> <span data-ttu-id="dceed-159">Zapewnia to dostępność spójności w sposób kontrolowanych i zorientowanym obiektowo zamiast wdrażania kodu skrypt.</span><span class="sxs-lookup"><span data-stu-id="dceed-159">This maintains consistency in a controlled and object-oriented way instead of implementing transactional script code.</span></span>

<span data-ttu-id="dceed-160">Poniższy fragment kodu przedstawia prawidłowego sposobem kodu zadania dodawania obiektu OrderItem do zagregowania kolejności.</span><span class="sxs-lookup"><span data-stu-id="dceed-160">The following code snippet shows the proper way to code the task of adding an OrderItem object to the Order aggregate.</span></span>

```csharp
// RIGHT ACCORDING TO DDD--CODE AT THE APPLICATION LAYER OR COMMAND HANDLERS
// The code in command handlers or WebAPI controllers, related only to application stuff
// There is NO code here related to OrderItem object’s business logic
myOrder.AddOrderItem(productId, productName, pictureUrl, unitPrice, discount, units);

// The code related to OrderItem params validations or domain rules should
// be WITHIN the AddOrderItem method.

//...
```

<span data-ttu-id="dceed-161">W tym fragmencie, większość operacji sprawdzania poprawności lub logiki powiązane do utworzenia obiektu OrderItem będą kontroli głównego agregacji kolejności — w metodzie AddOrderItem — szczególnie operacji sprawdzania poprawności i logiki powiązane z innymi elementami w całkowitym.</span><span class="sxs-lookup"><span data-stu-id="dceed-161">In this snippet, most of the validations or logic related to the creation of an OrderItem object will be under the control of the Order aggregate root—in the AddOrderItem method—especially validations and logic related to other elements in the aggregate.</span></span> <span data-ttu-id="dceed-162">Na przykład można uzyskać ten sam element produktu w wyniku wielu wywołań AddOrderItem.</span><span class="sxs-lookup"><span data-stu-id="dceed-162">For instance, you might get the same product item as the result of multiple calls to AddOrderItem.</span></span> <span data-ttu-id="dceed-163">W tej metodzie można zbadać elementów produktu i konsolidować te same elementy produktu w pojedynczy obiekt OrderItem z kilku jednostek.</span><span class="sxs-lookup"><span data-stu-id="dceed-163">In that method, you could examine the product items and consolidate the same product items into a single OrderItem object with several units.</span></span> <span data-ttu-id="dceed-164">Ponadto jeśli istnieją różne stawki kwoty, ale identyfikator produktu jest taki sam, będzie prawdopodobnie Zastosuj wyższy rabat.</span><span class="sxs-lookup"><span data-stu-id="dceed-164">Additionally, if there are different discount amounts but the product ID is the same, you would likely apply the higher discount.</span></span> <span data-ttu-id="dceed-165">Ta zasada ma zastosowanie do innych logika domeny dla obiekt OrderItem.</span><span class="sxs-lookup"><span data-stu-id="dceed-165">This principle applies to any other domain logic for the OrderItem object.</span></span>

<span data-ttu-id="dceed-166">Ponadto nowej operacji OrderItem(params) utworzy również być kontrolowane i wykonywane przez metodę AddOrderItem od elementu głównego agregacji kolejności.</span><span class="sxs-lookup"><span data-stu-id="dceed-166">In addition, the new OrderItem(params) operation will also be controlled and performed by the AddOrderItem method from the Order aggregate root.</span></span> <span data-ttu-id="dceed-167">W związku z tym większość logiki lub Sprawdzanie poprawności związane z konieczności operacji (szczególnie wszystko, co ma wpływ na spójności między innymi jednostek podrzędnych) w jednym miejscu w katalogu głównym agregacji.</span><span class="sxs-lookup"><span data-stu-id="dceed-167">Therefore, most of the logic or validations related to that operation (especially anything that impacts the consistency between other child entities) will be in a single place within the aggregate root.</span></span> <span data-ttu-id="dceed-168">To jest ostatecznym celem wzorzec głównego agregacji.</span><span class="sxs-lookup"><span data-stu-id="dceed-168">That is the ultimate purpose of the aggregate root pattern.</span></span>

<span data-ttu-id="dceed-169">Jeśli używasz Entity Framework Core 1.1 lub później, jednostki DDD można lepiej wyrazić ponieważ zezwala ona na [mapowania pól](https://docs.microsoft.com/ef/core/modeling/backing-field) oprócz właściwości.</span><span class="sxs-lookup"><span data-stu-id="dceed-169">When you use Entity Framework Core 1.1 or later, a DDD entity can be better expressed because it allows [mapping to fields](https://docs.microsoft.com/ef/core/modeling/backing-field) in addition to properties.</span></span> <span data-ttu-id="dceed-170">Jest to przydatne podczas ochrony kolekcji jednostek podrzędnych lub obiekty wartości.</span><span class="sxs-lookup"><span data-stu-id="dceed-170">This is useful when protecting collections of child entities or value objects.</span></span> <span data-ttu-id="dceed-171">To rozszerzenie zamiast właściwości można korzystać z prostego pól prywatnych i można zaimplementować żadnych aktualizacji do kolekcji pola w metodach publicznego i zapewnić dostęp tylko do odczytu za pomocą metody AsReadOnly.</span><span class="sxs-lookup"><span data-stu-id="dceed-171">With this enhancement, you can use simple private fields instead of properties and you can implement any update to the field collection in public methods and provide read-only access through the AsReadOnly method.</span></span>

<span data-ttu-id="dceed-172">W DDD do zaktualizowania jednostki tylko za pośrednictwem metod w obiekcie (lub konstruktora) w celu sterowania wszystkie niezmiennej i spójność danych więc właściwości są zdefiniowane tylko za pomocą metody dostępu get.</span><span class="sxs-lookup"><span data-stu-id="dceed-172">In DDD you want to update the entity only through methods in the entity (or the constructor) in order to control any invariant and the consistency of the data, so properties are defined only with a get accessor.</span></span> <span data-ttu-id="dceed-173">Właściwości bazują na pól prywatnych.</span><span class="sxs-lookup"><span data-stu-id="dceed-173">The properties are backed by private fields.</span></span> <span data-ttu-id="dceed-174">Prywatne elementy członkowskie są dostępne tylko z należące do klasy.</span><span class="sxs-lookup"><span data-stu-id="dceed-174">Private members can only be accessed from within the class.</span></span> <span data-ttu-id="dceed-175">Jednak istnieje jeden wyjątek: EF Core musi ustawić także tych pól.</span><span class="sxs-lookup"><span data-stu-id="dceed-175">However, there one exception: EF Core needs to set these fields as well.</span></span>


### <a name="mapping-properties-with-only-get-accessors-to-the-fields-in-the-database-table"></a><span data-ttu-id="dceed-176">Mapowania właściwości z tylko Pobierz metod dostępu do pola w tabeli bazy danych</span><span class="sxs-lookup"><span data-stu-id="dceed-176">Mapping properties with only get accessors to the fields in the database table</span></span>

<span data-ttu-id="dceed-177">Mapowanie właściwości do kolumny tabeli bazy danych nie jest odpowiedzialność domeny, ale część warstwy infrastruktury i trwałości.</span><span class="sxs-lookup"><span data-stu-id="dceed-177">Mapping properties to database table columns is not a domain responsibility but part of the infrastructure and persistence layer.</span></span> <span data-ttu-id="dceed-178">Firma Microsoft informacje o tym tutaj wystarczy, aby poznać nowe funkcje w wersji 1.1 Core EF lub później związanych z jak modelu jednostki.</span><span class="sxs-lookup"><span data-stu-id="dceed-178">We mention this here just so you are aware of the new capabilities in EF Core 1.1 or later related to how you can model entities.</span></span> <span data-ttu-id="dceed-179">Dodatkowe szczegóły dotyczące tego tematu opisano w sekcji infrastruktury i trwałości.</span><span class="sxs-lookup"><span data-stu-id="dceed-179">Additional details on this topic are explained in the infrastructure and persistence section.</span></span>

<span data-ttu-id="dceed-180">Jeśli używasz EF Core 1.0, w ramach DbContext należy zamapować właściwości, które są zdefiniowane tylko za pomocą metody pobierające, do rzeczywistych pola w tabeli bazy danych.</span><span class="sxs-lookup"><span data-stu-id="dceed-180">When you use EF Core 1.0, within the DbContext you need to map the properties that are defined only with getters to the actual fields in the database table.</span></span> <span data-ttu-id="dceed-181">Można to zrobić za pomocą metody HasField klasy PropertyBuilder.</span><span class="sxs-lookup"><span data-stu-id="dceed-181">This is done with the HasField method of the PropertyBuilder class.</span></span>

### <a name="mapping-fields-without-properties"></a><span data-ttu-id="dceed-182">Mapowanie pól bez właściwości</span><span class="sxs-lookup"><span data-stu-id="dceed-182">Mapping fields without properties</span></span>

<span data-ttu-id="dceed-183">Dzięki funkcji w programie EF Core 1.1 lub nowszej do mapowania kolumn do pól jest również możliwe nie używać właściwości.</span><span class="sxs-lookup"><span data-stu-id="dceed-183">With the feature in EF Core 1.1 or later to map columns to fields, it is also possible to not use properties.</span></span> <span data-ttu-id="dceed-184">Zamiast tego można mapować tylko kolumny tabeli do pól.</span><span class="sxs-lookup"><span data-stu-id="dceed-184">Instead, you can just map columns from a table to fields.</span></span> <span data-ttu-id="dceed-185">Przypadek użycia wspólnych dla tego jest prywatny pól dla stanu wewnętrznego, które nie muszą być dostępne spoza jednostki.</span><span class="sxs-lookup"><span data-stu-id="dceed-185">A common use case for this is private fields for an internal state that does not need to be accessed from outside the entity.</span></span>

<span data-ttu-id="dceed-186">Na przykład w poprzednim przykładzie kodu OrderAggregate istnieje kilka pól prywatnych, jak `_paymentMethodId` pole, które ma nie powiązanych właściwości metody ustawiającej lub metody pobierającej.</span><span class="sxs-lookup"><span data-stu-id="dceed-186">For example, in the preceding OrderAggregate code example, there are several private fields, like the the  `_paymentMethodId` field, that have no related property for either a setter or getter.</span></span> <span data-ttu-id="dceed-187">Można również tego pola obliczane w kolejności logiki biznesowej i użycia w kolejności metody, ale zachodzi potrzeba jego utrwalenia w bazie danych oraz.</span><span class="sxs-lookup"><span data-stu-id="dceed-187">That field could also be calculated within the order’s business logic and used from the order’s methods, but it needs to be persisted in the database as well.</span></span> <span data-ttu-id="dceed-188">Dlatego w EF Core (od momentu w wersji 1.1) mapują pole bez właściwości powiązanych z kolumną w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="dceed-188">So in EF Core (since v1.1) there is a way to map a field without a related property to a column in the database.</span></span> <span data-ttu-id="dceed-189">Jest to również szczegółowo [warstwę infrastruktury](#the-infrastructure-layer) tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="dceed-189">This is also explained in the [Infrastructure layer](#the-infrastructure-layer) section of this guide.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="dceed-190">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="dceed-190">Additional resources</span></span>

-   <span data-ttu-id="dceed-191">**Vaughn Vernon. Modelowanie wartości zagregowanych z DDD i strukturą Entity Framework.**</span><span class="sxs-lookup"><span data-stu-id="dceed-191">**Vaughn Vernon. Modeling Aggregates with DDD and Entity Framework.**</span></span> <span data-ttu-id="dceed-192">Należy pamiętać, że jest to *nie* Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="dceed-192">Note that this is *not* Entity Framework Core.</span></span>
    [<span data-ttu-id="dceed-193">*https://vaughnvernon.co/?p=879*</span><span class="sxs-lookup"><span data-stu-id="dceed-193">*https://vaughnvernon.co/?p=879*</span></span>](https://vaughnvernon.co/?p=879)

-   <span data-ttu-id="dceed-194">**Julie Lerman. Kodowanie oparte na domenie projektu: porady dotyczące danych Devs**
    [*https://msdn.microsoft.com/en-us/magazine/dn342868.aspx*](https://msdn.microsoft.com/en-us/magazine/dn342868.aspx)</span><span class="sxs-lookup"><span data-stu-id="dceed-194">**Julie Lerman. Coding for Domain-Driven Design: Tips for Data-Focused Devs**
[*https://msdn.microsoft.com/en-us/magazine/dn342868.aspx*](https://msdn.microsoft.com/en-us/magazine/dn342868.aspx)</span></span>

-   <span data-ttu-id="dceed-195">**Udi Dahan. Jak utworzyć pełni hermetyzowany modeli domeny**
    [*http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/*](http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/)</span><span class="sxs-lookup"><span data-stu-id="dceed-195">**Udi Dahan. How to create fully encapsulated Domain Models**
[*http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/*](http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="dceed-196">[Poprzednie] (mikrousługi domeny model.md) [dalej] (seedwork-domain-model-base-classes-interfaces.md)</span><span class="sxs-lookup"><span data-stu-id="dceed-196">[Previous] (microservice-domain-model.md) [Next] (seedwork-domain-model-base-classes-interfaces.md)</span></span>

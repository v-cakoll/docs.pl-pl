---
title: Implementowanie modelu domeny mikrousługi z platformą .NET Core
description: Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Implementowanie modelu domeny mikrousługi z platformą .NET Core
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/09/2017
ms.openlocfilehash: e0c931405b8b7e3b52bdcbd511737b449dc74273
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="implementing-a-microservice-domain-model-with-net-core"></a><span data-ttu-id="edd5b-103">Implementowanie modelu domeny mikrousługi z platformą .NET Core</span><span class="sxs-lookup"><span data-stu-id="edd5b-103">Implementing a microservice domain model with .NET Core</span></span> 

<span data-ttu-id="edd5b-104">W poprzedniej sekcji zostały wyjaśnione zasady projektowania podstawowych i wzorce projektowania modelu domeny.</span><span class="sxs-lookup"><span data-stu-id="edd5b-104">In the previous section, the fundamental design principles and patterns for designing a domain model were explained.</span></span> <span data-ttu-id="edd5b-105">Teraz nadszedł czas, aby poznać możliwości, aby wdrożyć model domeny przy użyciu platformy .NET Core (zwykły C\# kodu) i EF podstawowe.</span><span class="sxs-lookup"><span data-stu-id="edd5b-105">Now it is time to explore possible ways to implement the domain model by using .NET Core (plain C\# code) and EF Core.</span></span> <span data-ttu-id="edd5b-106">Należy pamiętać, że model domeny będzie składać się z kodu.</span><span class="sxs-lookup"><span data-stu-id="edd5b-106">Note that your domain model will be composed simply of your code.</span></span> <span data-ttu-id="edd5b-107">Na EF będzie mieć tylko podstawowe EF wymagania modelu, ale nie rzeczywistych zależności.</span><span class="sxs-lookup"><span data-stu-id="edd5b-107">It will have just the EF Core model requirements, but not real dependencies on EF.</span></span> <span data-ttu-id="edd5b-108">Nie powinna mieć twarde zależności lub odwołania do podstawowych funkcji EF lub innych ORM modelu domeny.</span><span class="sxs-lookup"><span data-stu-id="edd5b-108">You should not have hard dependencies or references to EF Core or any other ORM in your domain model.</span></span>

## <a name="domain-model-structure-in-a-custom-net-standard-library"></a><span data-ttu-id="edd5b-109">Struktura modelu domeny niestandardowe biblioteki .NET Standard</span><span class="sxs-lookup"><span data-stu-id="edd5b-109">Domain model structure in a custom .NET Standard library</span></span>

<span data-ttu-id="edd5b-110">Organizacja folderu używane dla aplikacji odwołanie eShopOnContainers pokazuje DDD modelu dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="edd5b-110">The folder organization used for the eShopOnContainers reference application demonstrates the DDD model for the application.</span></span> <span data-ttu-id="edd5b-111">Może się okazać, że organizacja inny folder dokładniej komunikuje się decyzji projektowych dotyczących aplikacji.</span><span class="sxs-lookup"><span data-stu-id="edd5b-111">You might find that a different folder organization more clearly communicates the design choices made for your application.</span></span> <span data-ttu-id="edd5b-112">Jak widać w rysunek 9 – 10 w porządkowania modelu domeny istnieją agregatów, zagregowany kolejności i nabywców agregacji.</span><span class="sxs-lookup"><span data-stu-id="edd5b-112">As you can see in Figure 9-10, in the ordering domain model there are two aggregates, the order aggregate and the buyer aggregate.</span></span> <span data-ttu-id="edd5b-113">Każdego agregacji jest grupą domeny jednostek i obiektów wartość, mimo że agregacji składa się z jednostek jednej domenie, (łączny głównego lub podmiot główny) również może mieć.</span><span class="sxs-lookup"><span data-stu-id="edd5b-113">Each aggregate is a group of domain entities and value objects, although you could have an aggregate composed of a single domain entity (the aggregate root or root entity) as well.</span></span>

![](./media/image11.png)

<span data-ttu-id="edd5b-114">**Rysunek 9 – 10**.</span><span class="sxs-lookup"><span data-stu-id="edd5b-114">**Figure 9-10**.</span></span> <span data-ttu-id="edd5b-115">Struktura modelu domeny dla porządkowania mikrousługi w eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="edd5b-115">Domain model structure for the ordering microservice in eShopOnContainers</span></span>

<span data-ttu-id="edd5b-116">Ponadto warstwy modelu domeny obejmuje kontrakty repozytorium (interfejsy), które są wymagania dotyczące infrastruktury modelu domeny.</span><span class="sxs-lookup"><span data-stu-id="edd5b-116">Additionally, the domain model layer includes the repository contracts (interfaces) that are the infrastructure requirements of your domain model.</span></span> <span data-ttu-id="edd5b-117">Innymi słowy, te interfejsy express repozytoriów, jakie musi implementować warstwę infrastruktury i w jaki sposób.</span><span class="sxs-lookup"><span data-stu-id="edd5b-117">In other words, these interfaces express what repositories the infrastructure layer must implement and how.</span></span> <span data-ttu-id="edd5b-118">Jest krytyczny, że implementacja repozytoriów można umieścić poza warstwy modelu domeny, w bibliotece warstwę infrastruktury tak warstwy modelu domeny jest nie "zanieczyszczone" interfejsu API lub klas z technologii infrastruktury, takich jak Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="edd5b-118">It is critical that the implementation of the repositories be placed outside of the domain model layer, in the infrastructure layer library, so the domain model layer is not “contaminated” by API or classes from infrastructure technologies, like Entity Framework.</span></span>

<span data-ttu-id="edd5b-119">Możesz również sprawdzić [SeedWork](https://martinfowler.com/bliki/Seedwork.html) folder zawierający niestandardowe klasy bazowej, która służy jako podstawa dla jednostek domeny i wartość obiekty, dlatego nie masz nadmiarowy kod w klasie obiektów w każdej domenie.</span><span class="sxs-lookup"><span data-stu-id="edd5b-119">You can also see a [SeedWork](https://martinfowler.com/bliki/Seedwork.html) folder that contains custom base classes that you can use as a base for your domain entities and value objects, so you do not have redundant code in each domain’s object class.</span></span>

## <a name="structuring-aggregates-in-a-custom-net-standard-library"></a><span data-ttu-id="edd5b-120">Struktury wartości zagregowanych w niestandardowa biblioteka .NET Standard</span><span class="sxs-lookup"><span data-stu-id="edd5b-120">Structuring aggregates in a custom .NET Standard library</span></span>

<span data-ttu-id="edd5b-121">Wartość zagregowana odwołuje się do klastra obiektów domeny zgrupowane w celu dopasowania spójności transakcyjnej.</span><span class="sxs-lookup"><span data-stu-id="edd5b-121">An aggregate refers to a cluster of domain objects grouped together to match transactional consistency.</span></span> <span data-ttu-id="edd5b-122">Te obiekty można wystąpienia jednostek (z których jeden jest łączny głównego lub podmiot główny) oraz wszystkie obiekty dodatkowe wartości.</span><span class="sxs-lookup"><span data-stu-id="edd5b-122">Those objects could be instances of entities (one of which is the aggregate root or root entity) plus any additional value objects.</span></span>

<span data-ttu-id="edd5b-123">Spójności transakcyjnej oznacza, że agregacji gwarantuje to spójność i na bieżąco na koniec działania biznesowe.</span><span class="sxs-lookup"><span data-stu-id="edd5b-123">Transactional consistency means that an aggregate is guaranteed to be consistent and up to date at the end of a business action.</span></span> <span data-ttu-id="edd5b-124">Na przykład agregacji kolejności z eShopOnContainers kolejność modelu domeny mikrousługi składa się jak pokazano w rysunek 9-11.</span><span class="sxs-lookup"><span data-stu-id="edd5b-124">For example, the order aggregate from the eShopOnContainers ordering microservice domain model is composed as shown in Figure 9-11.</span></span>

![](./media/image12.png)

<span data-ttu-id="edd5b-125">**Rysunek 9-11**.</span><span class="sxs-lookup"><span data-stu-id="edd5b-125">**Figure 9-11**.</span></span> <span data-ttu-id="edd5b-126">Kolejność agregacji w rozwiązaniu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="edd5b-126">The order aggregate in Visual Studio solution</span></span>

<span data-ttu-id="edd5b-127">Po otwarciu plików w folderze agregacji widać jak jest oznaczony jako niestandardowej klasy podstawowej lub interfejsu, takich jak jednostka lub wartość obiektu, zgodnie z implementacją w [Seedwork](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.Domain/SeedWork) folderu.</span><span class="sxs-lookup"><span data-stu-id="edd5b-127">If you open any of the files in an aggregate folder, you can see how it is marked as either a custom base class or interface, like entity or value object, as implemented in the [Seedwork](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.Domain/SeedWork) folder.</span></span>

## <a name="implementing-domain-entities-as-poco-classes"></a><span data-ttu-id="edd5b-128">Implementowanie jednostek domeny jako klasy POCO</span><span class="sxs-lookup"><span data-stu-id="edd5b-128">Implementing domain entities as POCO classes</span></span>

<span data-ttu-id="edd5b-129">Model domeny można zaimplementować w .NET przez utworzenie klas POCO, które implementują obiekty domeny.</span><span class="sxs-lookup"><span data-stu-id="edd5b-129">You implement a domain model in .NET by creating POCO classes that implement your domain entities.</span></span> <span data-ttu-id="edd5b-130">W poniższym przykładzie klasa kolejności jest zdefiniowana jako jednostki, a także jako główny agregacji.</span><span class="sxs-lookup"><span data-stu-id="edd5b-130">In the following example, the Order class is defined as an entity and also as an aggregate root.</span></span> <span data-ttu-id="edd5b-131">Ponieważ klasa kolejności pochodzi od klasy podstawowej jednostki, można użyć ponownie typowy Kod powiązane z jednostkami.</span><span class="sxs-lookup"><span data-stu-id="edd5b-131">Because the Order class derives from the Entity base class, it can reuse common code related to entities.</span></span> <span data-ttu-id="edd5b-132">Przy tym pamiętać, że te klasy podstawowe i interfejsy są zdefiniowane przez użytkownika w projekcie modelu domeny, więc Twojej kod, nie infrastrukturze kod z ORM, takich jak EF.</span><span class="sxs-lookup"><span data-stu-id="edd5b-132">Bear in mind that these base classes and interfaces are defined by you in the domain model project, so it is your code, not infrastructure code from an ORM like EF.</span></span>

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

<span data-ttu-id="edd5b-133">Należy zauważyć, że jest jednostką domeny, zaimplementowane jako klasa POCO.</span><span class="sxs-lookup"><span data-stu-id="edd5b-133">It is important to note that this is a domain entity implemented as a POCO class.</span></span> <span data-ttu-id="edd5b-134">Nie ma żadnych bezpośrednich zależność od Entity Framework Core lub inne struktury infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="edd5b-134">It does not have any direct dependency on Entity Framework Core or any other infrastructure framework.</span></span> <span data-ttu-id="edd5b-135">Ta implementacja jest powinny być w DDD, po prostu C\# kod implementacji modelu domeny.</span><span class="sxs-lookup"><span data-stu-id="edd5b-135">This implementation is as it should be in DDD, just C\# code implementing a domain model.</span></span>

<span data-ttu-id="edd5b-136">Ponadto klasa zostanie nadany interfejsu o nazwie IAggregateRoot.</span><span class="sxs-lookup"><span data-stu-id="edd5b-136">In addition, the class is decorated with an interface named IAggregateRoot.</span></span> <span data-ttu-id="edd5b-137">Ten interfejs jest interfejsem pusta, nazywane również *interfejsu znacznika*, która jest używana tylko w celu oznaczać, że ta klasa jednostki jest również głównego agregacji.</span><span class="sxs-lookup"><span data-stu-id="edd5b-137">That interface is an empty interface, sometimes called a *marker interface*, that is used just to indicate that this entity class is also an aggregate root.</span></span>

<span data-ttu-id="edd5b-138">Interfejs znacznika czasami jest uznawany za wzorca oprogramowania; jednak również to czysta sposób Oznacz klasę, szczególnie w przypadku, gdy ten interfejs może rozwijającymi.</span><span class="sxs-lookup"><span data-stu-id="edd5b-138">A marker interface is sometimes considered as an anti-pattern; however, it is also a clean way to mark a class, especially when that interface might be evolving.</span></span> <span data-ttu-id="edd5b-139">Atrybut może być inne wybór dla znacznika, ale jest szybsze wyświetlić klasy podstawowej (jednostka) obok interfejsu IAggregate zamiast umieszczanie znacznika atrybutu agregacji powyżej klasy.</span><span class="sxs-lookup"><span data-stu-id="edd5b-139">An attribute could be the other choice for the marker, but it is quicker to see the base class (Entity) next to the IAggregate interface instead of putting an Aggregate attribute marker above the class.</span></span> <span data-ttu-id="edd5b-140">Metter preferencji, jest w każdym przypadku.</span><span class="sxs-lookup"><span data-stu-id="edd5b-140">It is a metter of preferences, in any case.</span></span>

<span data-ttu-id="edd5b-141">O oznacza głównego agregacji, że większość kod powiązany spójności i reguły biznesowe jednostek wartości zagregowanej powinny zostać wdrożone jako metod klasy głównym agregacji kolejności (na przykład AddOrderItem podczas dodawania obiektu OrderItem do agregacji) .</span><span class="sxs-lookup"><span data-stu-id="edd5b-141">Having an aggregate root means that most of the code related to consistency and business rules of the aggregate’s entities should be implemented as methods in the Order aggregate root class (for example, AddOrderItem when adding an OrderItem object to the aggregate).</span></span> <span data-ttu-id="edd5b-142">Nie należy utworzyć ani zaktualizować obiektów OrderItems niezależnie lub bezpośrednio; Klasa AggregateRoot musi przechowywać i kontroli spójności żadnej operacji aktualizacji, przed jego obiektów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="edd5b-142">You should not create or update OrderItems objects independently or directly; the AggregateRoot class must keep control and consistency of any update operation against its child entities.</span></span>

## <a name="encapsulating-data-in-the-domain-entities"></a><span data-ttu-id="edd5b-143">Zawieranie dane w jednostkach domeny</span><span class="sxs-lookup"><span data-stu-id="edd5b-143">Encapsulating data in the Domain Entities</span></span>

<span data-ttu-id="edd5b-144">To powszechny problem w modelach jednostki jest czy udostępniają właściwości nawigacji kolekcji jako typów list publicznie.</span><span class="sxs-lookup"><span data-stu-id="edd5b-144">A common problem in entity models is that they expose collection navigation properties as publicly accessible list types.</span></span> <span data-ttu-id="edd5b-145">Dzięki temu każdy Deweloper współpracownika do manipulowania zawartość te typy kolekcji, których może pominąć ważnymi reguł związanych z kolekcji, prawdopodobnie pozostawienie obiektu w nieprawidłowym stanie.</span><span class="sxs-lookup"><span data-stu-id="edd5b-145">This allows any collaborator developer to manipulate the contents of these collection types, which may bypass important business rules related to the collection, possibly leaving the object in an invalid state.</span></span> <span data-ttu-id="edd5b-146">To rozwiązanie jest ujawnia dostęp tylko do odczytu do kolekcji powiązanych i jawnie Podaj metod, które definiują sposób, w którym klienci można przekształcać je.</span><span class="sxs-lookup"><span data-stu-id="edd5b-146">The solution to this is to expose read-only access to related collections and explicitly provide methods that define ways in which clients can manipulate them.</span></span>

<span data-ttu-id="edd5b-147">W poprzednim kodzie należy zauważyć, że wiele atrybutów są tylko do odczytu lub prywatnych i tylko są tak Każda aktualizacja uwzględnia invariants domeny business konta i logikę określoną w ramach metod klasy nadaje się do aktualizacji za pomocą metod klasy.</span><span class="sxs-lookup"><span data-stu-id="edd5b-147">In the previous code, note that many attributes are read-only or private and are only updatable by the class methods, so any update takes into account business domain invariants and logic specified within the class methods.</span></span>

<span data-ttu-id="edd5b-148">Na przykład następujące wzorce DDD należy *nie* wykonaj następujące czynności z dowolnej polecenie obsługi metody lub aplikacji warstwy klasy:</span><span class="sxs-lookup"><span data-stu-id="edd5b-148">For example, following DDD patterns, you should *not* do the following from any command handler method or application layer class:</span></span>

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

<span data-ttu-id="edd5b-149">W tym przypadku metoda Add jest wyłącznie operacji dodawania danych, za pomocą bezpośredniego dostępu do kolekcji OrderItems.</span><span class="sxs-lookup"><span data-stu-id="edd5b-149">In this case, the Add method is purely an operation to add data, with direct access to the OrderItems collection.</span></span> <span data-ttu-id="edd5b-150">W związku z tym większość logika domeny, reguł lub Sprawdzanie poprawności dotyczące czy operację, podając obiektów podrzędnych będą rozkładane warstwy aplikacji (programy obsługi poleceń i kontrolery interfejsu API sieci Web).</span><span class="sxs-lookup"><span data-stu-id="edd5b-150">Therefore, most of the domain logic, rules, or validations related to that operation with the child entities will be spread across the application layer (command handlers and Web API controllers).</span></span>

<span data-ttu-id="edd5b-151">Przejście wokół agregacji głównego agregacji głównego nie może zagwarantować jego invariants, ważności lub jego spójności.</span><span class="sxs-lookup"><span data-stu-id="edd5b-151">If you go around the aggregate root, the aggregate root cannot guarantee its invariants, its validity, or its consistency.</span></span> <span data-ttu-id="edd5b-152">Po pewnym czasie będzie mieć postaci spaghetti kod lub skrypt kod.</span><span class="sxs-lookup"><span data-stu-id="edd5b-152">Eventually you will have spaghetti code or transactional script code.</span></span>

<span data-ttu-id="edd5b-153">Wykonać wzorce DDD, jednostki nie może mieć publicznych ustawiające w dowolnej właściwości jednostki.</span><span class="sxs-lookup"><span data-stu-id="edd5b-153">To follow DDD patterns, entities must not have public setters in any entity property.</span></span> <span data-ttu-id="edd5b-154">Zmian w jednostce powinny być regulowane przez jawnych metod jawne języka powszechna o zmianie, które działają one w jednostce.</span><span class="sxs-lookup"><span data-stu-id="edd5b-154">Changes in an entity should be driven by explicit methods with explicit ubiquitous language about the change they are performing in the entity.</span></span>

<span data-ttu-id="edd5b-155">Ponadto, kolekcje w ramach jednostki (np. kolejność elementów) powinny być właściwości tylko do odczytu (metoda AsReadOnly wyjaśniono później).</span><span class="sxs-lookup"><span data-stu-id="edd5b-155">Furthermore, collections within the entity (like the order items) should be read-only properties (the AsReadOnly method explained later).</span></span> <span data-ttu-id="edd5b-156">Można zaktualizować tylko z metod klasy głównym agregacji lub metody jednostek podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="edd5b-156">You should be able to update it only from within the aggregate root class methods or the child entity methods.</span></span>

<span data-ttu-id="edd5b-157">Jak widać w kodzie dla elementu głównego agregacji w kolejności, wszystkie metody ustawiające powinny być prywatne lub co najmniej tylko do odczytu zewnętrznie, dzięki czemu ma być wykonywane za pomocą metod w klasie jednostki żadnej operacji względem danych jednostki lub jego obiektów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="edd5b-157">As you can see in the code for the Order aggregate root, all setters should be private or at least read-only externally, so that any operation against the entity’s data or its child entities has to be performed through methods in the entity class.</span></span> <span data-ttu-id="edd5b-158">Zapewnia to dostępność spójności w sposób kontrolowanych i zorientowanym obiektowo zamiast wdrażania kodu skrypt.</span><span class="sxs-lookup"><span data-stu-id="edd5b-158">This maintains consistency in a controlled and object-oriented way instead of implementing transactional script code.</span></span>

<span data-ttu-id="edd5b-159">Poniższy fragment kodu przedstawia prawidłowego sposobem kodu zadania dodawania obiektu OrderItem do zagregowania kolejności.</span><span class="sxs-lookup"><span data-stu-id="edd5b-159">The following code snippet shows the proper way to code the task of adding an OrderItem object to the Order aggregate.</span></span>

```csharp
// RIGHT ACCORDING TO DDD--CODE AT THE APPLICATION LAYER OR COMMAND HANDLERS
// The code in command handlers or WebAPI controllers, related only to application stuff
// There is NO code here related to OrderItem object’s business logic
myOrder.AddOrderItem(productId, productName, pictureUrl, unitPrice, discount, units);

// The code related to OrderItem params validations or domain rules should
// be WITHIN the AddOrderItem method.

//...
```

<span data-ttu-id="edd5b-160">W tym fragmencie, większość operacji sprawdzania poprawności lub logiki powiązane do utworzenia obiektu OrderItem będą kontroli głównego agregacji kolejności — w metodzie AddOrderItem — szczególnie operacji sprawdzania poprawności i logiki powiązane z innymi elementami w całkowitym.</span><span class="sxs-lookup"><span data-stu-id="edd5b-160">In this snippet, most of the validations or logic related to the creation of an OrderItem object will be under the control of the Order aggregate root—in the AddOrderItem method—especially validations and logic related to other elements in the aggregate.</span></span> <span data-ttu-id="edd5b-161">Na przykład można uzyskać ten sam element produktu w wyniku wielu wywołań AddOrderItem.</span><span class="sxs-lookup"><span data-stu-id="edd5b-161">For instance, you might get the same product item as the result of multiple calls to AddOrderItem.</span></span> <span data-ttu-id="edd5b-162">W tej metodzie można zbadać elementów produktu i konsolidować te same elementy produktu w pojedynczy obiekt OrderItem z kilku jednostek.</span><span class="sxs-lookup"><span data-stu-id="edd5b-162">In that method, you could examine the product items and consolidate the same product items into a single OrderItem object with several units.</span></span> <span data-ttu-id="edd5b-163">Ponadto jeśli istnieją różne stawki kwoty, ale identyfikator produktu jest taki sam, będzie prawdopodobnie Zastosuj wyższy rabat.</span><span class="sxs-lookup"><span data-stu-id="edd5b-163">Additionally, if there are different discount amounts but the product ID is the same, you would likely apply the higher discount.</span></span> <span data-ttu-id="edd5b-164">Ta zasada ma zastosowanie do innych logika domeny dla obiekt OrderItem.</span><span class="sxs-lookup"><span data-stu-id="edd5b-164">This principle applies to any other domain logic for the OrderItem object.</span></span>

<span data-ttu-id="edd5b-165">Ponadto nowej operacji OrderItem(params) utworzy również być kontrolowane i wykonywane przez metodę AddOrderItem od elementu głównego agregacji kolejności.</span><span class="sxs-lookup"><span data-stu-id="edd5b-165">In addition, the new OrderItem(params) operation will also be controlled and performed by the AddOrderItem method from the Order aggregate root.</span></span> <span data-ttu-id="edd5b-166">W związku z tym większość logiki lub Sprawdzanie poprawności związane z konieczności operacji (szczególnie wszystko, co ma wpływ na spójności między innymi jednostek podrzędnych) w jednym miejscu w katalogu głównym agregacji.</span><span class="sxs-lookup"><span data-stu-id="edd5b-166">Therefore, most of the logic or validations related to that operation (especially anything that impacts the consistency between other child entities) will be in a single place within the aggregate root.</span></span> <span data-ttu-id="edd5b-167">To jest ostatecznym celem wzorzec głównego agregacji.</span><span class="sxs-lookup"><span data-stu-id="edd5b-167">That is the ultimate purpose of the aggregate root pattern.</span></span>

<span data-ttu-id="edd5b-168">Jeśli używasz Entity Framework Core 1.1 lub później, jednostki DDD można lepiej wyrazić ponieważ zezwala ona na [mapowania pól](https://docs.microsoft.com/ef/core/modeling/backing-field) oprócz właściwości.</span><span class="sxs-lookup"><span data-stu-id="edd5b-168">When you use Entity Framework Core 1.1 or later, a DDD entity can be better expressed because it allows [mapping to fields](https://docs.microsoft.com/ef/core/modeling/backing-field) in addition to properties.</span></span> <span data-ttu-id="edd5b-169">Jest to przydatne podczas ochrony kolekcji jednostek podrzędnych lub obiekty wartości.</span><span class="sxs-lookup"><span data-stu-id="edd5b-169">This is useful when protecting collections of child entities or value objects.</span></span> <span data-ttu-id="edd5b-170">To rozszerzenie zamiast właściwości można korzystać z prostego pól prywatnych i można zaimplementować żadnych aktualizacji do kolekcji pola w metodach publicznego i zapewnić dostęp tylko do odczytu za pomocą metody AsReadOnly.</span><span class="sxs-lookup"><span data-stu-id="edd5b-170">With this enhancement, you can use simple private fields instead of properties and you can implement any update to the field collection in public methods and provide read-only access through the AsReadOnly method.</span></span>

<span data-ttu-id="edd5b-171">W DDD do zaktualizowania jednostki tylko za pośrednictwem metod w obiekcie (lub konstruktora) w celu sterowania wszystkie niezmiennej i spójność danych więc właściwości są zdefiniowane tylko za pomocą metody dostępu get.</span><span class="sxs-lookup"><span data-stu-id="edd5b-171">In DDD you want to update the entity only through methods in the entity (or the constructor) in order to control any invariant and the consistency of the data, so properties are defined only with a get accessor.</span></span> <span data-ttu-id="edd5b-172">Właściwości bazują na pól prywatnych.</span><span class="sxs-lookup"><span data-stu-id="edd5b-172">The properties are backed by private fields.</span></span> <span data-ttu-id="edd5b-173">Prywatne elementy członkowskie są dostępne tylko z należące do klasy.</span><span class="sxs-lookup"><span data-stu-id="edd5b-173">Private members can only be accessed from within the class.</span></span> <span data-ttu-id="edd5b-174">Jednak istnieje jeden wyjątek: EF Core musi ustawić także tych pól.</span><span class="sxs-lookup"><span data-stu-id="edd5b-174">However, there one exception: EF Core needs to set these fields as well.</span></span>


### <a name="mapping-properties-with-only-get-accessors-to-the-fields-in-the-database-table"></a><span data-ttu-id="edd5b-175">Mapowania właściwości z tylko Pobierz metod dostępu do pola w tabeli bazy danych</span><span class="sxs-lookup"><span data-stu-id="edd5b-175">Mapping properties with only get accessors to the fields in the database table</span></span>

<span data-ttu-id="edd5b-176">Mapowanie właściwości do kolumny tabeli bazy danych nie jest odpowiedzialność domeny, ale część warstwy infrastruktury i trwałości.</span><span class="sxs-lookup"><span data-stu-id="edd5b-176">Mapping properties to database table columns is not a domain responsibility but part of the infrastructure and persistence layer.</span></span> <span data-ttu-id="edd5b-177">Firma Microsoft informacje o tym tutaj wystarczy, aby poznać nowe funkcje w wersji 1.1 Core EF lub później związanych z jak modelu jednostki.</span><span class="sxs-lookup"><span data-stu-id="edd5b-177">We mention this here just so you are aware of the new capabilities in EF Core 1.1 or later related to how you can model entities.</span></span> <span data-ttu-id="edd5b-178">Dodatkowe szczegóły dotyczące tego tematu opisano w sekcji infrastruktury i trwałości.</span><span class="sxs-lookup"><span data-stu-id="edd5b-178">Additional details on this topic are explained in the infrastructure and persistence section.</span></span>

<span data-ttu-id="edd5b-179">Jeśli używasz EF Core 1.0, w ramach DbContext należy zamapować właściwości, które są zdefiniowane tylko za pomocą metody pobierające, do rzeczywistych pola w tabeli bazy danych.</span><span class="sxs-lookup"><span data-stu-id="edd5b-179">When you use EF Core 1.0, within the DbContext you need to map the properties that are defined only with getters to the actual fields in the database table.</span></span> <span data-ttu-id="edd5b-180">Można to zrobić za pomocą metody HasField klasy PropertyBuilder.</span><span class="sxs-lookup"><span data-stu-id="edd5b-180">This is done with the HasField method of the PropertyBuilder class.</span></span>

### <a name="mapping-fields-without-properties"></a><span data-ttu-id="edd5b-181">Mapowanie pól bez właściwości</span><span class="sxs-lookup"><span data-stu-id="edd5b-181">Mapping fields without properties</span></span>

<span data-ttu-id="edd5b-182">Dzięki funkcji w programie EF Core 1.1 lub nowszej do mapowania kolumn do pól jest również możliwe nie używać właściwości.</span><span class="sxs-lookup"><span data-stu-id="edd5b-182">With the feature in EF Core 1.1 or later to map columns to fields, it is also possible to not use properties.</span></span> <span data-ttu-id="edd5b-183">Zamiast tego można mapować tylko kolumny tabeli do pól.</span><span class="sxs-lookup"><span data-stu-id="edd5b-183">Instead, you can just map columns from a table to fields.</span></span> <span data-ttu-id="edd5b-184">Przypadek użycia wspólnych dla tego jest prywatny pól dla stanu wewnętrznego, które nie muszą być dostępne spoza jednostki.</span><span class="sxs-lookup"><span data-stu-id="edd5b-184">A common use case for this is private fields for an internal state that does not need to be accessed from outside the entity.</span></span>

<span data-ttu-id="edd5b-185">Na przykład w poprzednim przykładzie kodu OrderAggregate istnieje kilka pól prywatnych, jak `_paymentMethodId` pole, które ma nie powiązanych właściwości metody ustawiającej lub metody pobierającej.</span><span class="sxs-lookup"><span data-stu-id="edd5b-185">For example, in the preceding OrderAggregate code example, there are several private fields, like the  `_paymentMethodId` field, that have no related property for either a setter or getter.</span></span> <span data-ttu-id="edd5b-186">Można również tego pola obliczane w kolejności logiki biznesowej i użycia w kolejności metody, ale zachodzi potrzeba jego utrwalenia w bazie danych oraz.</span><span class="sxs-lookup"><span data-stu-id="edd5b-186">That field could also be calculated within the order’s business logic and used from the order’s methods, but it needs to be persisted in the database as well.</span></span> <span data-ttu-id="edd5b-187">Dlatego w EF Core (od momentu w wersji 1.1) mapują pole bez właściwości powiązanych z kolumną w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="edd5b-187">So in EF Core (since v1.1) there is a way to map a field without a related property to a column in the database.</span></span> <span data-ttu-id="edd5b-188">Jest to również szczegółowo [warstwę infrastruktury](#the-infrastructure-layer) tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="edd5b-188">This is also explained in the [Infrastructure layer](#the-infrastructure-layer) section of this guide.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="edd5b-189">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="edd5b-189">Additional resources</span></span>

-   <span data-ttu-id="edd5b-190">**Vaughn Vernon. Modelowanie wartości zagregowanych z DDD i strukturą Entity Framework.**</span><span class="sxs-lookup"><span data-stu-id="edd5b-190">**Vaughn Vernon. Modeling Aggregates with DDD and Entity Framework.**</span></span> <span data-ttu-id="edd5b-191">Należy pamiętać, że jest to *nie* Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="edd5b-191">Note that this is *not* Entity Framework Core.</span></span>
    [*https://vaughnvernon.co/?p=879*](https://vaughnvernon.co/?p=879)

-   <span data-ttu-id="edd5b-192">**Julie Lerman. Kodowanie oparte na domenie projektu: porady dotyczące Devs danych**
    [*https://msdn.microsoft.com/en-us/magazine/dn342868.aspx*](https://msdn.microsoft.com/en-us/magazine/dn342868.aspx)</span><span class="sxs-lookup"><span data-stu-id="edd5b-192">**Julie Lerman. Coding for Domain-Driven Design: Tips for Data-Focused Devs**
[*https://msdn.microsoft.com/en-us/magazine/dn342868.aspx*](https://msdn.microsoft.com/en-us/magazine/dn342868.aspx)</span></span>

-   <span data-ttu-id="edd5b-193">**Udi Dahan. Jak utworzyć pełni hermetyzowany modeli domeny**
    [*http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/*](http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/)</span><span class="sxs-lookup"><span data-stu-id="edd5b-193">**Udi Dahan. How to create fully encapsulated Domain Models**
[*http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/*](http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="edd5b-194">[Poprzednie] (mikrousługi domeny model.md) [dalej] (seedwork-domain-model-base-classes-interfaces.md)</span><span class="sxs-lookup"><span data-stu-id="edd5b-194">[Previous] (microservice-domain-model.md) [Next] (seedwork-domain-model-base-classes-interfaces.md)</span></span>

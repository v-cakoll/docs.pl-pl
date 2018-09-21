---
title: Implementowanie modelu domeny mikrousługi za pomocą programu .NET Core
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Implementowanie modelu domeny mikrousługi za pomocą programu .NET Core
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/09/2017
ms.openlocfilehash: bb11d87cacf5bb6cbc980c879b0c42fae76f6246
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/21/2018
ms.locfileid: "46508661"
---
# <a name="implementing-a-microservice-domain-model-with-net-core"></a><span data-ttu-id="a4be9-103">Implementowanie modelu domeny mikrousługi za pomocą programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="a4be9-103">Implementing a microservice domain model with .NET Core</span></span> 

<span data-ttu-id="a4be9-104">W poprzedniej sekcji zostały wyjaśnione podstawowych projektowania i wzorce projektowania modelu domeny.</span><span class="sxs-lookup"><span data-stu-id="a4be9-104">In the previous section, the fundamental design principles and patterns for designing a domain model were explained.</span></span> <span data-ttu-id="a4be9-105">Teraz nadszedł czas, aby poznać sposoby, aby wdrożyć model domeny przy użyciu platformy .NET Core (C zwykły\# kodu) i programem EF Core.</span><span class="sxs-lookup"><span data-stu-id="a4be9-105">Now it is time to explore possible ways to implement the domain model by using .NET Core (plain C\# code) and EF Core.</span></span> <span data-ttu-id="a4be9-106">Należy pamiętać, że modelu domeny będzie składać się z kodu.</span><span class="sxs-lookup"><span data-stu-id="a4be9-106">Note that your domain model will be composed simply of your code.</span></span> <span data-ttu-id="a4be9-107">Tylko wymagania modelu platformy EF Core, ale w zależności nie rzeczywistych będzie miał na EF.</span><span class="sxs-lookup"><span data-stu-id="a4be9-107">It will have just the EF Core model requirements, but not real dependencies on EF.</span></span> <span data-ttu-id="a4be9-108">W modelu domeny nie powinna mieć twarde zależności lub odwołania do programu EF Core lub innych ORM.</span><span class="sxs-lookup"><span data-stu-id="a4be9-108">You should not have hard dependencies or references to EF Core or any other ORM in your domain model.</span></span>

## <a name="domain-model-structure-in-a-custom-net-standard-library"></a><span data-ttu-id="a4be9-109">Struktura modelu domeny niestandardowej biblioteki .NET Standard</span><span class="sxs-lookup"><span data-stu-id="a4be9-109">Domain model structure in a custom .NET Standard library</span></span>

<span data-ttu-id="a4be9-110">Organizacja folderu używane w ramach aplikacji eShopOnContainers aplikacji referencyjnej pokazuje modelu DDD dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a4be9-110">The folder organization used for the eShopOnContainers reference application demonstrates the DDD model for the application.</span></span> <span data-ttu-id="a4be9-111">Może się okazać, że organizacja inny folder wyraźniej komunikuje się uzasadnienie wyboru tych elementów, dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a4be9-111">You might find that a different folder organization more clearly communicates the design choices made for your application.</span></span> <span data-ttu-id="a4be9-112">Jak widać na rysunku 9-10 w szeregowania modelu domeny istnieją dwie wartości zagregowane, aggregate kolejności i agregacji kupujący.</span><span class="sxs-lookup"><span data-stu-id="a4be9-112">As you can see in Figure 9-10, in the ordering domain model there are two aggregates, the order aggregate and the buyer aggregate.</span></span> <span data-ttu-id="a4be9-113">Każdej agregacji jest grupą domeny jednostek i obiektów wartości, mimo że może mieć również składa się z jednostką jednej domenie (głównego agregacji lub jednostki głównej) wartość zagregowana.</span><span class="sxs-lookup"><span data-stu-id="a4be9-113">Each aggregate is a group of domain entities and value objects, although you could have an aggregate composed of a single domain entity (the aggregate root or root entity) as well.</span></span>

![](./media/image11.png)

<span data-ttu-id="a4be9-114">**Rysunek 9 – 10**.</span><span class="sxs-lookup"><span data-stu-id="a4be9-114">**Figure 9-10**.</span></span> <span data-ttu-id="a4be9-115">Struktura modelu domeny mikrousługi sortowania, w ramach aplikacji eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="a4be9-115">Domain model structure for the ordering microservice in eShopOnContainers</span></span>

<span data-ttu-id="a4be9-116">Ponadto w warstwie modelu domeny obejmuje kontrakty repozytorium (interfejsy), które są wymagania dotyczące infrastruktury modelu domeny.</span><span class="sxs-lookup"><span data-stu-id="a4be9-116">Additionally, the domain model layer includes the repository contracts (interfaces) that are the infrastructure requirements of your domain model.</span></span> <span data-ttu-id="a4be9-117">Innymi słowy, te interfejsy express repozytoriów, jakie musi implementować warstwy infrastruktury i w jaki sposób.</span><span class="sxs-lookup"><span data-stu-id="a4be9-117">In other words, these interfaces express what repositories the infrastructure layer must implement and how.</span></span> <span data-ttu-id="a4be9-118">Koniecznie, implementacja repozytoriów można umieścić poza warstwie modelu domeny w bibliotece warstwę infrastruktury, więc warstwie modelu domeny nie jest "zanieczyszczona" interfejsu API lub klasy z technologii infrastruktury, takich jak Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="a4be9-118">It is critical that the implementation of the repositories be placed outside of the domain model layer, in the infrastructure layer library, so the domain model layer is not “contaminated” by API or classes from infrastructure technologies, like Entity Framework.</span></span>

<span data-ttu-id="a4be9-119">Można również wyświetlić [SeedWork](https://martinfowler.com/bliki/Seedwork.html) obiektów folder zawierający niestandardowe klasy bazowej, która służy jako podstawa dla domeny, jednostki i wartości, więc nie trzeba nadmiarowy kod w klasie obiektów w każdej domenie.</span><span class="sxs-lookup"><span data-stu-id="a4be9-119">You can also see a [SeedWork](https://martinfowler.com/bliki/Seedwork.html) folder that contains custom base classes that you can use as a base for your domain entities and value objects, so you do not have redundant code in each domain’s object class.</span></span>

## <a name="structuring-aggregates-in-a-custom-net-standard-library"></a><span data-ttu-id="a4be9-120">Tworzenie struktury wartości zagregowanych umieszczonych w niestandardowej biblioteki .NET Standard</span><span class="sxs-lookup"><span data-stu-id="a4be9-120">Structuring aggregates in a custom .NET Standard library</span></span>

<span data-ttu-id="a4be9-121">Wartość zagregowana odnosi się do klastra, w przypadku obiektów domeny zgrupowane razem, aby dopasować poziom spójności transakcyjnej.</span><span class="sxs-lookup"><span data-stu-id="a4be9-121">An aggregate refers to a cluster of domain objects grouped together to match transactional consistency.</span></span> <span data-ttu-id="a4be9-122">Te obiekty można wystąpień jednostki (z których jeden jest głównego agregacji lub jednostki głównej) oraz wszystkie obiekty dodatkową wartość.</span><span class="sxs-lookup"><span data-stu-id="a4be9-122">Those objects could be instances of entities (one of which is the aggregate root or root entity) plus any additional value objects.</span></span>

<span data-ttu-id="a4be9-123">Poziom spójności transakcyjnej oznacza, że wartość zagregowana jest gwarantowane były spójne i na bieżąco na końcu działań biznesowych.</span><span class="sxs-lookup"><span data-stu-id="a4be9-123">Transactional consistency means that an aggregate is guaranteed to be consistent and up to date at the end of a business action.</span></span> <span data-ttu-id="a4be9-124">Na przykład składa się agregacji kolejność, w ramach aplikacji eShopOnContainers kolejność modelu domeny mikrousługi, jak pokazano w rysunek 9 – 11.</span><span class="sxs-lookup"><span data-stu-id="a4be9-124">For example, the order aggregate from the eShopOnContainers ordering microservice domain model is composed as shown in Figure 9-11.</span></span>

![](./media/image12.png)

<span data-ttu-id="a4be9-125">**Rysunek 9 – 11**.</span><span class="sxs-lookup"><span data-stu-id="a4be9-125">**Figure 9-11**.</span></span> <span data-ttu-id="a4be9-126">Kolejność agregacji w rozwiązaniu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a4be9-126">The order aggregate in Visual Studio solution</span></span>

<span data-ttu-id="a4be9-127">Jeśli możesz otworzyć dowolny z plików w folderze agregacji, możesz zobaczyć jak jest oznaczony jako niestandardowej klasy bazowej lub interfejsu, takich jak jednostka lub wartość obiektu, zaimplementowanego w [Seedwork](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.Domain/SeedWork) folderu.</span><span class="sxs-lookup"><span data-stu-id="a4be9-127">If you open any of the files in an aggregate folder, you can see how it is marked as either a custom base class or interface, like entity or value object, as implemented in the [Seedwork](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.Domain/SeedWork) folder.</span></span>

## <a name="implementing-domain-entities-as-poco-classes"></a><span data-ttu-id="a4be9-128">Implementowanie jednostki domeny jako klasy POCO</span><span class="sxs-lookup"><span data-stu-id="a4be9-128">Implementing domain entities as POCO classes</span></span>

<span data-ttu-id="a4be9-129">Model domeny na platformie .NET implementuje są przez utworzenie klas POCO, które implementują jednostki domeny.</span><span class="sxs-lookup"><span data-stu-id="a4be9-129">You implement a domain model in .NET by creating POCO classes that implement your domain entities.</span></span> <span data-ttu-id="a4be9-130">W poniższym przykładzie klasa kolejność jest zdefiniowana jako jednostki, a także jako główny agregacji.</span><span class="sxs-lookup"><span data-stu-id="a4be9-130">In the following example, the Order class is defined as an entity and also as an aggregate root.</span></span> <span data-ttu-id="a4be9-131">Ponieważ klasa kolejności pochodzi z klasy podstawowej jednostki, można ponownie użyć wspólny kod powiązane z jednostkami.</span><span class="sxs-lookup"><span data-stu-id="a4be9-131">Because the Order class derives from the Entity base class, it can reuse common code related to entities.</span></span> <span data-ttu-id="a4be9-132">Mieć na uwadze, że te klasy podstawowe i interfejsy są zdefiniowane przez użytkownika w projekcie modelu domeny, więc Twoja kod, a nie kod infrastruktury z ORM, takie jak EF.</span><span class="sxs-lookup"><span data-stu-id="a4be9-132">Bear in mind that these base classes and interfaces are defined by you in the domain model project, so it is your code, not infrastructure code from an ORM like EF.</span></span>

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

<span data-ttu-id="a4be9-133">Należy pamiętać, że to jest jednostka domeny implementowany jako klasa POCO.</span><span class="sxs-lookup"><span data-stu-id="a4be9-133">It is important to note that this is a domain entity implemented as a POCO class.</span></span> <span data-ttu-id="a4be9-134">Nie ma żadnych zależności bezpośrednich platformy Entity Framework Core lub dowolnej architektury infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="a4be9-134">It does not have any direct dependency on Entity Framework Core or any other infrastructure framework.</span></span> <span data-ttu-id="a4be9-135">Ta implementacja jest należycie w DDD, po prostu C\# kodu Implementowanie modelu domeny.</span><span class="sxs-lookup"><span data-stu-id="a4be9-135">This implementation is as it should be in DDD, just C\# code implementing a domain model.</span></span>

<span data-ttu-id="a4be9-136">Ponadto klasa zostanie nadany interfejs o nazwie IAggregateRoot.</span><span class="sxs-lookup"><span data-stu-id="a4be9-136">In addition, the class is decorated with an interface named IAggregateRoot.</span></span> <span data-ttu-id="a4be9-137">Ten interfejs jest pusty interfejs, czasami nazywane *interfejs znacznika*, która jest używana tylko w celu wskazania, że ta klasa jednostki jest również głównego agregacji.</span><span class="sxs-lookup"><span data-stu-id="a4be9-137">That interface is an empty interface, sometimes called a *marker interface*, that is used just to indicate that this entity class is also an aggregate root.</span></span>

<span data-ttu-id="a4be9-138">To interfejs znacznika czasami jest traktowany jako wzorzec ochrony; jednak go jest również eleganckie rozwiązanie, aby oznaczyć klasę, szczególnie w przypadku, gdy ten interfejs może zmieniających się.</span><span class="sxs-lookup"><span data-stu-id="a4be9-138">A marker interface is sometimes considered as an anti-pattern; however, it is also a clean way to mark a class, especially when that interface might be evolving.</span></span> <span data-ttu-id="a4be9-139">Atrybut może być inne rozwiązanie dla znacznika, ale jest szybsze wyświetlić klasę bazową (jednostka) obok interfejsu IAggregate zamiast umieszczać znacznika atrybutu dotyczącego agregacji powyżej klasy.</span><span class="sxs-lookup"><span data-stu-id="a4be9-139">An attribute could be the other choice for the marker, but it is quicker to see the base class (Entity) next to the IAggregate interface instead of putting an Aggregate attribute marker above the class.</span></span> <span data-ttu-id="a4be9-140">Niezależnie od lokalizacji tych preferencji, jest w każdym przypadku.</span><span class="sxs-lookup"><span data-stu-id="a4be9-140">It is a matter of preferences, in any case.</span></span>

<span data-ttu-id="a4be9-141">Posiadanie oznacza głównego agregacji, że większość kodu związane z spójności i reguł biznesowych, jednostek agregacji powinny zostać wdrożone jako metody w klasie głównego agregacji zamówienia (na przykład AddOrderItem podczas dodawania obiektu OrderItem do agregacji) .</span><span class="sxs-lookup"><span data-stu-id="a4be9-141">Having an aggregate root means that most of the code related to consistency and business rules of the aggregate’s entities should be implemented as methods in the Order aggregate root class (for example, AddOrderItem when adding an OrderItem object to the aggregate).</span></span> <span data-ttu-id="a4be9-142">Użytkownik powinien nie utworzyć lub zaktualizować OrderItems obiekty niezależnie lub bezpośrednio; Klasa AggregateRoot musi przechowywać kontroli i spójności żadnych operacji aktualizacji, przed jego obiektów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="a4be9-142">You should not create or update OrderItems objects independently or directly; the AggregateRoot class must keep control and consistency of any update operation against its child entities.</span></span>

## <a name="encapsulating-data-in-the-domain-entities"></a><span data-ttu-id="a4be9-143">Zawieranie danymi w obiektach domeny</span><span class="sxs-lookup"><span data-stu-id="a4be9-143">Encapsulating data in the Domain Entities</span></span>

<span data-ttu-id="a4be9-144">Typowy problem w modelach jednostki jest eksponowanie właściwości nawigacji kolekcji jako typy list dostępny publicznie.</span><span class="sxs-lookup"><span data-stu-id="a4be9-144">A common problem in entity models is that they expose collection navigation properties as publicly accessible list types.</span></span> <span data-ttu-id="a4be9-145">Dzięki temu każdy Deweloper współpracownika do manipulowania zawartość tych kolekcji typów, które może pominąć reguł biznesowych ważne związanych z kolekcji, prawdopodobnie pozostawienie obiektu w nieprawidłowym stanie.</span><span class="sxs-lookup"><span data-stu-id="a4be9-145">This allows any collaborator developer to manipulate the contents of these collection types, which may bypass important business rules related to the collection, possibly leaving the object in an invalid state.</span></span> <span data-ttu-id="a4be9-146">Rozwiązaniem tego problemu do prezentowania dostęp tylko do odczytu do powiązanej kolekcji i jawnie określić metody, które definiują sposób, w którym klienci nimi manipulować.</span><span class="sxs-lookup"><span data-stu-id="a4be9-146">The solution to this is to expose read-only access to related collections and explicitly provide methods that define ways in which clients can manipulate them.</span></span>

<span data-ttu-id="a4be9-147">W poprzednim kodzie należy pamiętać, że wiele atrybutów są tylko do odczytu "lub" prywatnych są one tylko nadaje się do aktualizacji za pomocą metod klasy tak Każda aktualizacja wymaga invariants domeny biznesowej konta i logikę określoną w ramach metod klasy.</span><span class="sxs-lookup"><span data-stu-id="a4be9-147">In the previous code, note that many attributes are read-only or private and are only updatable by the class methods, so any update takes into account business domain invariants and logic specified within the class methods.</span></span>

<span data-ttu-id="a4be9-148">Na przykład, następujące wzorców DDD, wykonaj następujące czynności *nie* wykonaj następujące czynności z dowolnego polecenia obsługi metody lub aplikacji warstwy klasy:</span><span class="sxs-lookup"><span data-stu-id="a4be9-148">For example, following DDD patterns, you should *not* do the following from any command handler method or application layer class:</span></span>

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

<span data-ttu-id="a4be9-149">W tym przypadku metoda Add jest wyłącznie operacji dodawania danych bezpośredni dostęp do kolekcji OrderItems.</span><span class="sxs-lookup"><span data-stu-id="a4be9-149">In this case, the Add method is purely an operation to add data, with direct access to the OrderItems collection.</span></span> <span data-ttu-id="a4be9-150">W związku z tym większość logika domeny, zasady lub walidacji dotyczące czy operację, używając obiektów podrzędnych będą rozkłada warstwy aplikacji (programy obsługi poleceń i kontrolerów internetowych interfejsów API).</span><span class="sxs-lookup"><span data-stu-id="a4be9-150">Therefore, most of the domain logic, rules, or validations related to that operation with the child entities will be spread across the application layer (command handlers and Web API controllers).</span></span>

<span data-ttu-id="a4be9-151">Po przejściu wokół głównego agregacji głównego agregacji nie gwarantuje jego invariants, jego ważności lub jego zgodności.</span><span class="sxs-lookup"><span data-stu-id="a4be9-151">If you go around the aggregate root, the aggregate root cannot guarantee its invariants, its validity, or its consistency.</span></span> <span data-ttu-id="a4be9-152">Po pewnym czasie będziesz mieć postaci spaghetti kod lub kod skryptu transakcji.</span><span class="sxs-lookup"><span data-stu-id="a4be9-152">Eventually you will have spaghetti code or transactional script code.</span></span>

<span data-ttu-id="a4be9-153">Aby skorzystać z wzorców DDD, jednostki nie może mieć publiczne metody ustawiające w dowolnej właściwości jednostki.</span><span class="sxs-lookup"><span data-stu-id="a4be9-153">To follow DDD patterns, entities must not have public setters in any entity property.</span></span> <span data-ttu-id="a4be9-154">Zmiany w jednostce powinien opierać się za pomocą jawnych metod za pomocą jawnego wszechobecne języka o zmiany, które wykonują w jednostce.</span><span class="sxs-lookup"><span data-stu-id="a4be9-154">Changes in an entity should be driven by explicit methods with explicit ubiquitous language about the change they are performing in the entity.</span></span>

<span data-ttu-id="a4be9-155">Ponadto, kolekcjami w obrębie jednostki (takie jak elementy zamówienia) powinny być właściwości tylko do odczytu (metoda AsReadOnly opisana później).</span><span class="sxs-lookup"><span data-stu-id="a4be9-155">Furthermore, collections within the entity (like the order items) should be read-only properties (the AsReadOnly method explained later).</span></span> <span data-ttu-id="a4be9-156">Można zaktualizować go tylko w obrębie głównego agregacji metod klasy lub metody jednostki podrzędne.</span><span class="sxs-lookup"><span data-stu-id="a4be9-156">You should be able to update it only from within the aggregate root class methods or the child entity methods.</span></span>

<span data-ttu-id="a4be9-157">Jak widać w kodzie dla głównego agregacji w kolejności, wszystkie metody ustawiające powinny być prywatne lub co najmniej tylko do odczytu zewnętrznie, tak aby każdej operacji względem danych jednostki lub jego obiektów podrzędnych musi być wykonywane za pomocą metody w klasie jednostki.</span><span class="sxs-lookup"><span data-stu-id="a4be9-157">As you can see in the code for the Order aggregate root, all setters should be private or at least read-only externally, so that any operation against the entity’s data or its child entities has to be performed through methods in the entity class.</span></span> <span data-ttu-id="a4be9-158">Zapewnia to spójność w sposób kontrolowany i zorientowane obiektowo, a nie Implementowanie kod skryptu transakcji.</span><span class="sxs-lookup"><span data-stu-id="a4be9-158">This maintains consistency in a controlled and object-oriented way instead of implementing transactional script code.</span></span>

<span data-ttu-id="a4be9-159">Poniższy fragment kodu przedstawia prawidłowego sposobu kod: zadanie dodawania obiektu OrderItem do zagregowania zamówienia.</span><span class="sxs-lookup"><span data-stu-id="a4be9-159">The following code snippet shows the proper way to code the task of adding an OrderItem object to the Order aggregate.</span></span>

```csharp
// RIGHT ACCORDING TO DDD--CODE AT THE APPLICATION LAYER OR COMMAND HANDLERS
// The code in command handlers or WebAPI controllers, related only to application stuff
// There is NO code here related to OrderItem object’s business logic
myOrder.AddOrderItem(productId, productName, pictureUrl, unitPrice, discount, units);

// The code related to OrderItem params validations or domain rules should
// be WITHIN the AddOrderItem method.

//...
```

<span data-ttu-id="a4be9-160">W tym fragmencie kodu, większość operacji sprawdzania poprawności lub logiki powiązane z tworzenia obiektu OrderItem będą kontroli głównego agregacji zamówienia — w metodzie AddOrderItem — szczególnie logiki i walidacji powiązanych do innych elementów w agregacji.</span><span class="sxs-lookup"><span data-stu-id="a4be9-160">In this snippet, most of the validations or logic related to the creation of an OrderItem object will be under the control of the Order aggregate root—in the AddOrderItem method—especially validations and logic related to other elements in the aggregate.</span></span> <span data-ttu-id="a4be9-161">Na przykład możesz otrzymać ten sam element produktu w wyniku AddOrderItem wielu wywołań.</span><span class="sxs-lookup"><span data-stu-id="a4be9-161">For instance, you might get the same product item as the result of multiple calls to AddOrderItem.</span></span> <span data-ttu-id="a4be9-162">W tej metodzie można zbadać elementów produktu i konsolidować tych samych towarów produktu w pojedynczy obiekt OrderItem z kilku jednostek.</span><span class="sxs-lookup"><span data-stu-id="a4be9-162">In that method, you could examine the product items and consolidate the same product items into a single OrderItem object with several units.</span></span> <span data-ttu-id="a4be9-163">Ponadto jeśli istnieją kwoty różnych rabatów, ale identyfikator produktu jest taki sam, będzie prawdopodobnie stosować ten rabat wyższy.</span><span class="sxs-lookup"><span data-stu-id="a4be9-163">Additionally, if there are different discount amounts but the product ID is the same, you would likely apply the higher discount.</span></span> <span data-ttu-id="a4be9-164">Ta zasada ma zastosowanie do innych logiki domeny dla obiektu OrderItem.</span><span class="sxs-lookup"><span data-stu-id="a4be9-164">This principle applies to any other domain logic for the OrderItem object.</span></span>

<span data-ttu-id="a4be9-165">Ponadto nową operację OrderItem(params) będzie również być kontrolowany i wykonywane przez metodę AddOrderItem z katalogu głównego agregacji zamówienia.</span><span class="sxs-lookup"><span data-stu-id="a4be9-165">In addition, the new OrderItem(params) operation will also be controlled and performed by the AddOrderItem method from the Order aggregate root.</span></span> <span data-ttu-id="a4be9-166">W związku z tym większość logiki i walidacji związane z konieczności operacji (szczególnie wszystko, co ma wpływ na spójność między innymi jednostkami podrzędnych) w jednym miejscu w obrębie głównego agregacji.</span><span class="sxs-lookup"><span data-stu-id="a4be9-166">Therefore, most of the logic or validations related to that operation (especially anything that impacts the consistency between other child entities) will be in a single place within the aggregate root.</span></span> <span data-ttu-id="a4be9-167">To jest ostatecznym celem wzorzec głównego agregacji.</span><span class="sxs-lookup"><span data-stu-id="a4be9-167">That is the ultimate purpose of the aggregate root pattern.</span></span>

<span data-ttu-id="a4be9-168">Gdy korzystasz z programu Entity Framework Core 1.1 lub później, jednostki DDD można lepiej wyrazić ponieważ zezwala ona na [zamapowane na pola](https://docs.microsoft.com/ef/core/modeling/backing-field) oprócz właściwości.</span><span class="sxs-lookup"><span data-stu-id="a4be9-168">When you use Entity Framework Core 1.1 or later, a DDD entity can be better expressed because it allows [mapping to fields](https://docs.microsoft.com/ef/core/modeling/backing-field) in addition to properties.</span></span> <span data-ttu-id="a4be9-169">Jest to przydatne w przypadku ochrony kolekcji jednostki podrzędne lub obiekty wartości.</span><span class="sxs-lookup"><span data-stu-id="a4be9-169">This is useful when protecting collections of child entities or value objects.</span></span> <span data-ttu-id="a4be9-170">Za pomocą tego rozszerzenia można użyć prostego pola prywatne, zamiast właściwości i można zaimplementować wszelkich aktualizacji kolekcji pól za pomocą metod publicznych i zapewnić dostęp tylko do odczytu za pośrednictwem metody AsReadOnly.</span><span class="sxs-lookup"><span data-stu-id="a4be9-170">With this enhancement, you can use simple private fields instead of properties and you can implement any update to the field collection in public methods and provide read-only access through the AsReadOnly method.</span></span>

<span data-ttu-id="a4be9-171">W DDD, które chcesz zaktualizować jednostki, tylko za pośrednictwem metody w jednostki (lub konstruktora) w celu kontrolowania wszelkie niezmiennej i spójność danych więc właściwości są zdefiniowane tylko za pomocą metody dostępu get.</span><span class="sxs-lookup"><span data-stu-id="a4be9-171">In DDD you want to update the entity only through methods in the entity (or the constructor) in order to control any invariant and the consistency of the data, so properties are defined only with a get accessor.</span></span> <span data-ttu-id="a4be9-172">Właściwości są wspierane przez pola prywatne.</span><span class="sxs-lookup"><span data-stu-id="a4be9-172">The properties are backed by private fields.</span></span> <span data-ttu-id="a4be9-173">Prywatne elementy Członkowskie może zostać oceniony jedynie z w klasie.</span><span class="sxs-lookup"><span data-stu-id="a4be9-173">Private members can only be accessed from within the class.</span></span> <span data-ttu-id="a4be9-174">Jednak miejsca jeden wyjątek: programu EF Core musi ustawić również tych pól.</span><span class="sxs-lookup"><span data-stu-id="a4be9-174">However, there one exception: EF Core needs to set these fields as well.</span></span>


### <a name="mapping-properties-with-only-get-accessors-to-the-fields-in-the-database-table"></a><span data-ttu-id="a4be9-175">Mapowanie właściwości z tylko pobieranie metod dostępu do pól w tabeli bazy danych</span><span class="sxs-lookup"><span data-stu-id="a4be9-175">Mapping properties with only get accessors to the fields in the database table</span></span>

<span data-ttu-id="a4be9-176">Mapowanie właściwości do kolumny tabeli bazy danych nie jest odpowiedzialność domeny, ale część warstwy infrastruktury i trwałości.</span><span class="sxs-lookup"><span data-stu-id="a4be9-176">Mapping properties to database table columns is not a domain responsibility but part of the infrastructure and persistence layer.</span></span> <span data-ttu-id="a4be9-177">Firma Microsoft wspomnieć o tego w tym miejscu po prostu, dzięki czemu masz świadomość nowe możliwości w wersji EF Core 1.1 lub później powiązany sposób można modelować jednostek.</span><span class="sxs-lookup"><span data-stu-id="a4be9-177">We mention this here just so you are aware of the new capabilities in EF Core 1.1 or later related to how you can model entities.</span></span> <span data-ttu-id="a4be9-178">Dodatkowe szczegóły dotyczące tego tematu opisano w sekcji infrastruktury i trwałości.</span><span class="sxs-lookup"><span data-stu-id="a4be9-178">Additional details on this topic are explained in the infrastructure and persistence section.</span></span>

<span data-ttu-id="a4be9-179">Gdy używasz programu EF Core 1.0, w ramach kontekstu DbContext należy zamapować właściwości, które są zdefiniowane tylko w przypadku metod pobierających do rzeczywistego pól w tabeli bazy danych.</span><span class="sxs-lookup"><span data-stu-id="a4be9-179">When you use EF Core 1.0, within the DbContext you need to map the properties that are defined only with getters to the actual fields in the database table.</span></span> <span data-ttu-id="a4be9-180">Można to zrobić za pomocą metody HasField klasy PropertyBuilder.</span><span class="sxs-lookup"><span data-stu-id="a4be9-180">This is done with the HasField method of the PropertyBuilder class.</span></span>

### <a name="mapping-fields-without-properties"></a><span data-ttu-id="a4be9-181">Mapowanie pól bez właściwości</span><span class="sxs-lookup"><span data-stu-id="a4be9-181">Mapping fields without properties</span></span>

<span data-ttu-id="a4be9-182">Dzięki funkcji w programie EF Core 1.1 lub nowszej mapowania kolumn na pola użytkownik może również nie korzystać z właściwości.</span><span class="sxs-lookup"><span data-stu-id="a4be9-182">With the feature in EF Core 1.1 or later to map columns to fields, it is also possible to not use properties.</span></span> <span data-ttu-id="a4be9-183">Zamiast tego po prostu można mapować kolumny z tabeli pola.</span><span class="sxs-lookup"><span data-stu-id="a4be9-183">Instead, you can just map columns from a table to fields.</span></span> <span data-ttu-id="a4be9-184">Typowy przypadek użycia tego jest pola prywatne, wewnętrzne stanu, które nie muszą być dostępne spoza jednostki.</span><span class="sxs-lookup"><span data-stu-id="a4be9-184">A common use case for this is private fields for an internal state that does not need to be accessed from outside the entity.</span></span>

<span data-ttu-id="a4be9-185">Na przykład w poprzednim przykładzie kodu OrderAggregate istnieje kilka pola prywatne, takie jak `_paymentMethodId` pola, mających nie powiązane właściwości metody ustawiającej lub metody pobierającej.</span><span class="sxs-lookup"><span data-stu-id="a4be9-185">For example, in the preceding OrderAggregate code example, there are several private fields, like the  `_paymentMethodId` field, that have no related property for either a setter or getter.</span></span> <span data-ttu-id="a4be9-186">Również być obliczane w kolejności logiki biznesowej i użycia w kolejności metod tego pola, ale w celu jego utrwalenia w bazie danych również musi.</span><span class="sxs-lookup"><span data-stu-id="a4be9-186">That field could also be calculated within the order’s business logic and used from the order’s methods, but it needs to be persisted in the database as well.</span></span> <span data-ttu-id="a4be9-187">Dlatego w programie EF Core (od wersji 1.1) istnieje sposób mapowania pól bez właściwości powiązanych z kolumną w bazie danych.</span><span class="sxs-lookup"><span data-stu-id="a4be9-187">So in EF Core (since v1.1) there is a way to map a field without a related property to a column in the database.</span></span> <span data-ttu-id="a4be9-188">To także szczegółowo [warstwy infrastruktury](#the-infrastructure-layer) części tego przewodnika.</span><span class="sxs-lookup"><span data-stu-id="a4be9-188">This is also explained in the [Infrastructure layer](#the-infrastructure-layer) section of this guide.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="a4be9-189">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="a4be9-189">Additional resources</span></span>

-   <span data-ttu-id="a4be9-190">**Vaughn Vernon. Modelowanie agregacji za pomocą zastosowania projektowania DDD i Entity Framework.**</span><span class="sxs-lookup"><span data-stu-id="a4be9-190">**Vaughn Vernon. Modeling Aggregates with DDD and Entity Framework.**</span></span> <span data-ttu-id="a4be9-191">Należy zauważyć, że jest to *nie* Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="a4be9-191">Note that this is *not* Entity Framework Core.</span></span>
    [*https://vaughnvernon.co/?p=879*](https://vaughnvernon.co/?p=879)

-   <span data-ttu-id="a4be9-192">**Julie Lerman. Kodowanie dla projektowania opartego na domenie: wskazówki dla deweloperów skoncentrowane na danych**
    [*https://msdn.microsoft.com/en-us/magazine/dn342868.aspx*](https://msdn.microsoft.com/en-us/magazine/dn342868.aspx)</span><span class="sxs-lookup"><span data-stu-id="a4be9-192">**Julie Lerman. Coding for Domain-Driven Design: Tips for Data-Focused Devs**
[*https://msdn.microsoft.com/en-us/magazine/dn342868.aspx*](https://msdn.microsoft.com/en-us/magazine/dn342868.aspx)</span></span>

-   <span data-ttu-id="a4be9-193">**Udi Dahan. Jak utworzyć w pełni hermetyzowane modeli domeny**
    [*http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/*](http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/)</span><span class="sxs-lookup"><span data-stu-id="a4be9-193">**Udi Dahan. How to create fully encapsulated Domain Models**
[*http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/*](http://udidahan.com/2008/02/29/how-to-create-fully-encapsulated-domain-models/)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="a4be9-194">[Poprzednie](microservice-domain-model.md)
[dalej](seedwork-domain-model-base-classes-interfaces.md)</span><span class="sxs-lookup"><span data-stu-id="a4be9-194">[Previous](microservice-domain-model.md)
[Next](seedwork-domain-model-base-classes-interfaces.md)</span></span>

---
title: Seedwork (klasy bazowe wielokrotnego użytku i interfejsy na potrzeby modelu domeny)
description: Architektura mikrousług .NET dla konteneryzowanych aplikacji .NET | Użyj koncepcji seedwork jako punkt wyjścia, aby rozpocząć implementację dla modelu domeny zorientowanych na DDD.
ms.date: 10/08/2018
ms.openlocfilehash: ab0aadc28dbd1175c75b04dadca29b7b0947f29b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76116569"
---
# <a name="seedwork-reusable-base-classes-and-interfaces-for-your-domain-model"></a><span data-ttu-id="9ff0d-103">Seedwork (klasy bazowe wielokrotnego użytku i interfejsy na potrzeby modelu domeny)</span><span class="sxs-lookup"><span data-stu-id="9ff0d-103">Seedwork (reusable base classes and interfaces for your domain model)</span></span>

<span data-ttu-id="9ff0d-104">Folder rozwiązania zawiera folder *SeedWork.*</span><span class="sxs-lookup"><span data-stu-id="9ff0d-104">The solution folder contains a *SeedWork* folder.</span></span> <span data-ttu-id="9ff0d-105">Ten folder zawiera niestandardowe klasy podstawowe, których można używać jako podstawy dla jednostek domeny i obiektów wartości.</span><span class="sxs-lookup"><span data-stu-id="9ff0d-105">This folder contains custom base classes that you can use as a base for your domain entities and value objects.</span></span> <span data-ttu-id="9ff0d-106">Użyj tych klas podstawowych, aby nie mieć nadmiarowego kodu w klasie obiektów każdej domeny.</span><span class="sxs-lookup"><span data-stu-id="9ff0d-106">Use these base classes so you don't have redundant code in each domain’s object class.</span></span> <span data-ttu-id="9ff0d-107">Folder dla tych typów klas nosi nazwę *SeedWork,* a nie coś w *rodzaju Framework*.</span><span class="sxs-lookup"><span data-stu-id="9ff0d-107">The folder for these types of classes is called *SeedWork* and not something like *Framework*.</span></span> <span data-ttu-id="9ff0d-108">Nazywa *seedwork,* ponieważ folder zawiera tylko mały podzbiór klas wielokrotnego użytku, które naprawdę nie można uznać za framework.</span><span class="sxs-lookup"><span data-stu-id="9ff0d-108">It's called *SeedWork* because the folder contains just a small subset of reusable classes that cannot really be considered a framework.</span></span> <span data-ttu-id="9ff0d-109">*Seedwork* to termin wprowadzony przez [Michaela Feathersa](https://www.artima.com/forums/flat.jsp?forum=106&thread=8826) i spopularyzowany przez [Martina Fowlera,](https://martinfowler.com/bliki/Seedwork.html) ale możesz również nazwać ten folder Common, SharedKernel lub podobnym.</span><span class="sxs-lookup"><span data-stu-id="9ff0d-109">*Seedwork* is a term introduced by [Michael Feathers](https://www.artima.com/forums/flat.jsp?forum=106&thread=8826) and popularized by [Martin Fowler](https://martinfowler.com/bliki/Seedwork.html) but you could also name that folder Common, SharedKernel, or similar.</span></span>

<span data-ttu-id="9ff0d-110">Rysunek 7-12 przedstawia klasy, które tworzą seedwork modelu domeny w mikrousługi porządkowania.</span><span class="sxs-lookup"><span data-stu-id="9ff0d-110">Figure 7-12 shows the classes that form the seedwork of the domain model in the ordering microservice.</span></span> <span data-ttu-id="9ff0d-111">Ma kilka niestandardowych klas podstawowych, takich jak Entity, ValueObject i Wyliczenie, a także kilka interfejsów.</span><span class="sxs-lookup"><span data-stu-id="9ff0d-111">It has a few custom base classes like Entity, ValueObject, and Enumeration, plus a few interfaces.</span></span> <span data-ttu-id="9ff0d-112">Te interfejsy (IRepository i IUnitOfWork) informują warstwę infrastruktury o tym, co należy zaimplementować.</span><span class="sxs-lookup"><span data-stu-id="9ff0d-112">These interfaces (IRepository and IUnitOfWork) inform the infrastructure layer about what needs to be implemented.</span></span> <span data-ttu-id="9ff0d-113">Te interfejsy są również używane za pośrednictwem iniekcji zależności z warstwy aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9ff0d-113">Those interfaces are also used through Dependency Injection from the application layer.</span></span>

:::image type="complex" source="./media/seedwork-domain-model-base-classes-interfaces/vs-solution-seedwork-classes.png" alt-text="Zrzut ekranu przedstawiający klasy zawarte w folderze SeedWork.":::
<span data-ttu-id="9ff0d-115">Szczegółowa zawartość folderu SeedWork, zawierająca klasy podstawowe i interfejsy: Entity.cs, Enumeration.cs, IAggregateRoot.cs, IRepository.cs, IUnitOfWork.cs i ValueObject.cs.</span><span class="sxs-lookup"><span data-stu-id="9ff0d-115">The detailed contents of the SeedWork folder, containing base classes and interfaces: Entity.cs, Enumeration.cs, IAggregateRoot.cs, IRepository.cs, IUnitOfWork.cs, and ValueObject.cs.</span></span>
:::image-end:::

<span data-ttu-id="9ff0d-116">**Rysunek 7-12**.</span><span class="sxs-lookup"><span data-stu-id="9ff0d-116">**Figure 7-12**.</span></span> <span data-ttu-id="9ff0d-117">Przykładowy zestaw klas podstawowych i interfejsów modelu domeny "seedwork"</span><span class="sxs-lookup"><span data-stu-id="9ff0d-117">A sample set of domain model “seedwork" base classes and interfaces</span></span>

<span data-ttu-id="9ff0d-118">Jest to typ ponownego użycia kopii i wklejania, który wielu deweloperów współużytkuje między projektami, a nie formalne ramy.</span><span class="sxs-lookup"><span data-stu-id="9ff0d-118">This is the type of copy and paste reuse that many developers share between projects, not a formal framework.</span></span> <span data-ttu-id="9ff0d-119">Prace seedworks można mieć w dowolnej warstwie lub bibliotece.</span><span class="sxs-lookup"><span data-stu-id="9ff0d-119">You can have seedworks in any layer or library.</span></span> <span data-ttu-id="9ff0d-120">Jeśli jednak zestaw klas i interfejsów jest wystarczająco duży, można utworzyć bibliotekę pojedynczej klasy.</span><span class="sxs-lookup"><span data-stu-id="9ff0d-120">However, if the set of classes and interfaces gets large enough, you might want to create a single class library.</span></span>

## <a name="the-custom-entity-base-class"></a><span data-ttu-id="9ff0d-121">Niestandardowa klasa podstawowa jednostki</span><span class="sxs-lookup"><span data-stu-id="9ff0d-121">The custom Entity base class</span></span>

<span data-ttu-id="9ff0d-122">Poniższy kod jest przykładem klasy podstawowej jednostki, gdzie można umieścić kod, który może być używany w ten sam sposób przez dowolną jednostkę domeny, takich jak identyfikator jednostki, [operatory równości,](../../../csharp/language-reference/operators/equality-operators.md)lista zdarzeń domeny na jednostkę itp.</span><span class="sxs-lookup"><span data-stu-id="9ff0d-122">The following code is an example of an Entity base class where you can place code that can be used the same way by any domain entity, such as the entity ID, [equality operators](../../../csharp/language-reference/operators/equality-operators.md), a domain event list per entity, etc.</span></span>

```csharp
// COMPATIBLE WITH ENTITY FRAMEWORK CORE (1.1 and later)
public abstract class Entity
{
    int? _requestedHashCode;
    int _Id;
    private List<INotification> _domainEvents;
    public virtual int Id
    {
        get
        {
            return _Id;
        }
        protected set
        {
            _Id = value;
        }
    }

    public List<INotification> DomainEvents => _domainEvents;
    public void AddDomainEvent(INotification eventItem)
    {
        _domainEvents = _domainEvents ?? new List<INotification>();
        _domainEvents.Add(eventItem);
    }
    public void RemoveDomainEvent(INotification eventItem)
    {
        if (_domainEvents is null) return;
        _domainEvents.Remove(eventItem);
    }

    public bool IsTransient()
    {
        return this.Id == default(Int32);
    }

    public override bool Equals(object obj)
    {
        if (obj == null || !(obj is Entity))
            return false;
        if (Object.ReferenceEquals(this, obj))
            return true;
        if (this.GetType() != obj.GetType())
            return false;
        Entity item = (Entity)obj;
        if (item.IsTransient() || this.IsTransient())
            return false;
        else
            return item.Id == this.Id;
    }

    public override int GetHashCode()
    {
        if (!IsTransient())
        {
            if (!_requestedHashCode.HasValue)
                _requestedHashCode = this.Id.GetHashCode() ^ 31;
            // XOR for random distribution. See:
            // https://docs.microsoft.com/archive/blogs/ericlippert/guidelines-and-rules-for-gethashcode
            return _requestedHashCode.Value;
        }
        else
            return base.GetHashCode();
    }
    public static bool operator ==(Entity left, Entity right)
    {
        if (Object.Equals(left, null))
            return (Object.Equals(right, null));
        else
            return left.Equals(right);
    }
    public static bool operator !=(Entity left, Entity right)
    {
        return !(left == right);
    }
}
```

<span data-ttu-id="9ff0d-123">Poprzedni kod przy użyciu listy zdarzeń domeny na jednostkę zostanie wyjaśniony w następnych sekcjach podczas koncentrowania się na zdarzeniach domeny.</span><span class="sxs-lookup"><span data-stu-id="9ff0d-123">The previous code using a domain event list per entity will be explained in the next sections when focusing on domain events.</span></span>

## <a name="repository-contracts-interfaces-in-the-domain-model-layer"></a><span data-ttu-id="9ff0d-124">Kontrakty repozytorium (interfejsy) w warstwie modelu domeny</span><span class="sxs-lookup"><span data-stu-id="9ff0d-124">Repository contracts (interfaces) in the domain model layer</span></span>

<span data-ttu-id="9ff0d-125">Kontrakty repozytorium są po prostu interfejsy .NET, które wyrażają wymagania umowy repozytoriów, które mają być używane dla każdego agregacji.</span><span class="sxs-lookup"><span data-stu-id="9ff0d-125">Repository contracts are simply .NET interfaces that express the contract requirements of the repositories to be used for each aggregate.</span></span>

<span data-ttu-id="9ff0d-126">Same repozytoria z kodem EF Core lub innymi zależnościami i kodem infrastruktury (Linq, SQL itp.) nie mogą być implementowane w modelu domeny; repozytoria powinny implementować tylko interfejsy zdefiniowane w modelu domeny.</span><span class="sxs-lookup"><span data-stu-id="9ff0d-126">The repositories themselves, with EF Core code or any other infrastructure dependencies and code (Linq, SQL, etc.), must not be implemented within the domain model; the repositories should only implement the interfaces you define in the domain model.</span></span>

<span data-ttu-id="9ff0d-127">Wzorzec związany z tą praktyką (umieszczenie interfejsów repozytorium w warstwie modelu domeny) jest wzorzec oddzielone interfejsu.</span><span class="sxs-lookup"><span data-stu-id="9ff0d-127">A pattern related to this practice (placing the repository interfaces in the domain model layer) is the Separated Interface pattern.</span></span> <span data-ttu-id="9ff0d-128">Jak [wyjaśnił](https://www.martinfowler.com/eaaCatalog/separatedInterface.html) Martin Fowler, "Użyj oddzielonego interfejsu, aby zdefiniować interfejs w jednym pakiecie, ale zaimplementuj go w innym.</span><span class="sxs-lookup"><span data-stu-id="9ff0d-128">As [explained](https://www.martinfowler.com/eaaCatalog/separatedInterface.html) by Martin Fowler, “Use Separated Interface to define an interface in one package but implement it in another.</span></span> <span data-ttu-id="9ff0d-129">W ten sposób klient, który potrzebuje zależności od interfejsu, może być całkowicie nieświadomy implementacji."</span><span class="sxs-lookup"><span data-stu-id="9ff0d-129">This way a client that needs the dependency to the interface can be completely unaware of the implementation.”</span></span>

<span data-ttu-id="9ff0d-130">Po wzorzec oddzielone interfejsu umożliwia warstwy aplikacji (w tym przypadku projektu interfejsu API sieci Web dla mikrousługi) mieć zależność od wymagań zdefiniowanych w modelu domeny, ale nie bezpośrednią zależność od warstwy infrastruktury/trwałości.</span><span class="sxs-lookup"><span data-stu-id="9ff0d-130">Following the Separated Interface pattern enables the application layer (in this case, the Web API project for the microservice) to have a dependency on the requirements defined in the domain model, but not a direct dependency to the infrastructure/persistence layer.</span></span> <span data-ttu-id="9ff0d-131">Ponadto można użyć funkcji Iniekcji zależności do izolowania implementacji, która jest implementowana w warstwie infrastruktury/trwałości przy użyciu repozytoriów.</span><span class="sxs-lookup"><span data-stu-id="9ff0d-131">In addition, you can use Dependency Injection to isolate the implementation, which is implemented in the infrastructure/ persistence layer using repositories.</span></span>

<span data-ttu-id="9ff0d-132">Na przykład w poniższym przykładzie z interfejsem IOrderRepository definiuje, jakie operacje klasa OrderRepository będzie musiała zaimplementować w warstwie infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="9ff0d-132">For example, the following example with the IOrderRepository interface defines what operations the OrderRepository class will need to implement at the infrastructure layer.</span></span> <span data-ttu-id="9ff0d-133">W bieżącej implementacji aplikacji kod po prostu musi dodać lub zaktualizować zamówienia do bazy danych, ponieważ zapytania są dzielone zgodnie z uproszczonym podejściem CQRS.</span><span class="sxs-lookup"><span data-stu-id="9ff0d-133">In the current implementation of the application, the code just needs to add or update orders to the database, since queries are split following the simplified CQRS approach.</span></span>

```csharp
// Defined at IOrderRepository.cs
public interface IOrderRepository : IRepository<Order>
{
    Order Add(Order order);

    void Update(Order order);

    Task<Order> GetAsync(int orderId);
}

// Defined at IRepository.cs (Part of the Domain Seedwork)
public interface IRepository<T> where T : IAggregateRoot
{
    IUnitOfWork UnitOfWork { get; }
}
```

## <a name="additional-resources"></a><span data-ttu-id="9ff0d-134">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="9ff0d-134">Additional resources</span></span>

- <span data-ttu-id="9ff0d-135">**Martin Fowler. Oddzielone interfejs.**</span><span class="sxs-lookup"><span data-stu-id="9ff0d-135">**Martin Fowler. Separated Interface.**</span></span> \
  <https://www.martinfowler.com/eaaCatalog/separatedInterface.html>

>[!div class="step-by-step"]
><span data-ttu-id="9ff0d-136">[Poprzedni](net-core-microservice-domain-model.md)
>[następny](implement-value-objects.md)</span><span class="sxs-lookup"><span data-stu-id="9ff0d-136">[Previous](net-core-microservice-domain-model.md)
[Next](implement-value-objects.md)</span></span>

---
title: "Seedwork (może być ponownie używane klasy podstawowe i interfejsy dla modelu domeny)"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Seedwork (może być ponownie używane klasy podstawowe i interfejsy dla modelu domeny)"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/12/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: aba336676a558f50a2669eb3ca096effb8387916
ms.sourcegitcommit: 91691981897cf8451033cb01071d8f5d94017f97
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/09/2018
---
# <a name="seedwork-reusable-base-classes-and-interfaces-for-your-domain-model"></a><span data-ttu-id="17766-104">Seedwork (może być ponownie używane klasy podstawowe i interfejsy dla modelu domeny)</span><span class="sxs-lookup"><span data-stu-id="17766-104">Seedwork (reusable base classes and interfaces for your domain model)</span></span>

<span data-ttu-id="17766-105">Folder rozwiązania zawiera *SeedWork* folderu.</span><span class="sxs-lookup"><span data-stu-id="17766-105">The solution folder contains a *SeedWork* folder.</span></span> <span data-ttu-id="17766-106">*SeedWork* folder zawiera niestandardowej klasy bazowej, która służy jako podstawa dla domeny jednostek i obiektów wartość.</span><span class="sxs-lookup"><span data-stu-id="17766-106">The *SeedWork* folder contains custom base classes that you can use as a base for your domain entities and value objects.</span></span> <span data-ttu-id="17766-107">Należy używać tych klas podstawowych, dlatego nie masz nadmiarowy kod w klasie obiektów w każdej domenie.</span><span class="sxs-lookup"><span data-stu-id="17766-107">Use these base classes so you do not have redundant code in each domain’s object class.</span></span> <span data-ttu-id="17766-108">Folder dla tego typu klasy jest nazywany *SeedWork* i nie coś, takich jak *Framework*.</span><span class="sxs-lookup"><span data-stu-id="17766-108">The folder for these types of classes is called *SeedWork* and not something like *Framework*.</span></span> <span data-ttu-id="17766-109">Jest to *SeedWork* ponieważ folder zawiera tylko mały podzbiór klasy wielokrotnego użytku, które naprawdę nie może być uważane za struktury.</span><span class="sxs-lookup"><span data-stu-id="17766-109">It's called *SeedWork* because the folder contains just a small subset of reusable classes which cannot really be considered a framework.</span></span> <span data-ttu-id="17766-110">*Seedwork* termin wprowadzone przez [piór Michael](http://www.artima.com/forums/flat.jsp?forum=106&thread=8826) i popularized przez [Fowler pole](https://martinfowler.com/bliki/Seedwork.html) , ale można również nazwę tego folderu wspólne, SharedKernel, lub podobny.</span><span class="sxs-lookup"><span data-stu-id="17766-110">*Seedwork* is a term introduced by [Michael Feathers](http://www.artima.com/forums/flat.jsp?forum=106&thread=8826) and popularized by [Martin Fowler](https://martinfowler.com/bliki/Seedwork.html) but you could also name that folder Common, SharedKernel, or similar.</span></span>

<span data-ttu-id="17766-111">Rysunek 9 – 12 zawiera klasy, które tworzą seedwork modelu domeny w mikrousługi porządkowania.</span><span class="sxs-lookup"><span data-stu-id="17766-111">Figure 9-12 shows the classes that form the seedwork of the domain model in the ordering microservice.</span></span> <span data-ttu-id="17766-112">Ma kilka niestandardowych klas podstawowych takich jak jednostki, ValueObject i wyliczenia, a także kilka interfejsów.</span><span class="sxs-lookup"><span data-stu-id="17766-112">It has a few custom base classes like Entity, ValueObject, and Enumeration, plus a few interfaces.</span></span> <span data-ttu-id="17766-113">Te interfejsy (IRepository i IUnitOfWork) informuje warstwie infrastrukturze o co musi zostać wdrożone.</span><span class="sxs-lookup"><span data-stu-id="17766-113">These interfaces (IRepository and IUnitOfWork) inform the infrastructure layer about what needs to be implemented.</span></span> <span data-ttu-id="17766-114">Te interfejsy są również używane przez iniekcji zależności od warstwy aplikacji.</span><span class="sxs-lookup"><span data-stu-id="17766-114">Those interfaces are also used through Dependency Injection from the application layer.</span></span>

![](./media/image13.PNG)

<span data-ttu-id="17766-115">**Rysunek 9 – 12**.</span><span class="sxs-lookup"><span data-stu-id="17766-115">**Figure 9-12**.</span></span> <span data-ttu-id="17766-116">Przykładowy zestaw klasy podstawowej "seedwork" model domeny i interfejsy</span><span class="sxs-lookup"><span data-stu-id="17766-116">A sample set of domain model “seedwork" base classes and interfaces</span></span>

<span data-ttu-id="17766-117">Jest to typ, kopiowania i wklejania ponownego użycia wielu deweloperów udziale między projektami, formalnych ram.</span><span class="sxs-lookup"><span data-stu-id="17766-117">This is the type of copy and paste reuse that many developers share between projects, not a formal framework.</span></span> <span data-ttu-id="17766-118">Może mieć seedworks w dowolnej warstwy lub biblioteki.</span><span class="sxs-lookup"><span data-stu-id="17766-118">You can have seedworks in any layer or library.</span></span> <span data-ttu-id="17766-119">Jednak zestaw klasy i interfejsy pobiera wystarczająco duży, możesz utworzyć bibliotekę jednej klasy.</span><span class="sxs-lookup"><span data-stu-id="17766-119">However, if the set of classes and interfaces gets big enough, you might want to create a single class library.</span></span>

## <a name="the-custom-entity-base-class"></a><span data-ttu-id="17766-120">Niestandardowe klasy podstawowej jednostki</span><span class="sxs-lookup"><span data-stu-id="17766-120">The custom Entity base class</span></span>

<span data-ttu-id="17766-121">Następujący kod jest przykładem klasy podstawowej jednostki lokalizację kodu, który może służyć samo przez osobę domeny, takich jak identyfikator jednostki [Operatory równości](/cpp/cpp/equality-operators-equal-equal-and-exclpt-equal), listy zdarzeń domeny na jednostki itp.</span><span class="sxs-lookup"><span data-stu-id="17766-121">The following code is an example of an Entity base class where you can place code that can be used the same way by any domain entity, such as the entity ID, [equality operators](/cpp/cpp/equality-operators-equal-equal-and-exclpt-equal), a domain event list per entity, etc.</span></span>

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
            // http://blogs.msdn.com/b/ericlippert/archive/2011/02/28/guidelines-and-rules-for-gethashcode.aspx
            return _requestedHashCode.Value;
        }
        else
            return base.GetHashCode();
    }
    public static bool operator ==(Entity left, Entity right)
    {
        if (Object.Equals(left, null))
            return (Object.Equals(right, null)) ? true : false;
        else
            return left.Equals(right);
    }
    public static bool operator !=(Entity left, Entity right)
    {
        return !(left == right);
    }
}
```

<span data-ttu-id="17766-122">Poprzedni kod przy użyciu listy zdarzeń domeny na jednostkę opisano w kolejnych sekcjach podczas koncentrujących się na zdarzenia domeny.</span><span class="sxs-lookup"><span data-stu-id="17766-122">The previous code using a domain event list per entity will be explained in the next sections when focusing on domain events.</span></span> 

## <a name="repository-contracts-interfaces-in-the-domain-model-layer"></a><span data-ttu-id="17766-123">Kontrakty repozytorium (interfejsy) w warstwie modelu domeny</span><span class="sxs-lookup"><span data-stu-id="17766-123">Repository contracts (interfaces) in the domain model layer</span></span>

<span data-ttu-id="17766-124">Kontrakty repozytorium są po prostu interfejsów .NET, które express wymagania umowy repozytoriów do zastosowania w przypadku każdego agregacji.</span><span class="sxs-lookup"><span data-stu-id="17766-124">Repository contracts are simply .NET interfaces that express the contract requirements of the repositories to be used for each aggregate.</span></span> 

<span data-ttu-id="17766-125">Repozytoria się z kodem EF podstawowe lub inne zależności infrastruktury i kodu (Linq, SQL, itp.), nie może być realizowana w ramach modelu domeny; repozytoria tylko powinien implementować interfejsów, które należy zdefiniować.</span><span class="sxs-lookup"><span data-stu-id="17766-125">The repositories themselves, with EF Core code or any other infrastructure dependencies and code (Linq, SQL, etc.), must not be implemented within the domain model; the repositories should only implement the interfaces you define.</span></span> 

<span data-ttu-id="17766-126">Wzorzec związane z tym rozwiązaniem (wprowadzenie do interfejsów repozytorium warstwy modelu domeny) jest wzorzec oddzielone interfejsu.</span><span class="sxs-lookup"><span data-stu-id="17766-126">A pattern related to this practice (placing the repository interfaces in the domain model layer) is the Separated Interface pattern.</span></span> <span data-ttu-id="17766-127">Jako [wyjaśniono](http://www.martinfowler.com/eaaCatalog/separatedInterface.html) przez Fowler pole "Użyj interfejsu oddzielone można zdefiniować interfejs w jednej pakietu, ale ją wdrożyć w innym.</span><span class="sxs-lookup"><span data-stu-id="17766-127">As [explained](http://www.martinfowler.com/eaaCatalog/separatedInterface.html) by Martin Fowler, “Use Separated Interface to define an interface in one package but implement it in another.</span></span> <span data-ttu-id="17766-128">W ten sposób klient, który wymaga zależności do interfejsu może być dostarczanie implementacji."</span><span class="sxs-lookup"><span data-stu-id="17766-128">This way a client that needs the dependency to the interface can be completely unaware of the implementation.”</span></span>

<span data-ttu-id="17766-129">Po wzorzec oddzielone interfejs umożliwia ma zależności od wymagań zdefiniowanych w modelu domeny, ale nie bezpośrednie zależności do infrastruktury/trwałości warstwy aplikacji (w tym przypadku projekt interfejsu API sieci Web do mikrousługi) warstwy.</span><span class="sxs-lookup"><span data-stu-id="17766-129">Following the Separated Interface pattern enables the application layer (in this case, the Web API project for the microservice) to have a dependency on the requirements defined in the domain model, but not a direct dependency to the infrastructure/persistence layer.</span></span> <span data-ttu-id="17766-130">Ponadto iniekcji zależności można użyć do izolowania implementację, która jest zaimplementowana w infrastrukturze / warstwę trwałości przy użyciu repozytoriów.</span><span class="sxs-lookup"><span data-stu-id="17766-130">In addition, you can use Dependency Injection to isolate the implementation, which is implemented in the infrastructure/ persistence layer using repositories.</span></span>

<span data-ttu-id="17766-131">Na przykład w poniższym przykładzie z interfejsem IOrderRepository zdefiniowano jakie operacje OrderRepository klasy należy zaimplementować w warstwie infrastrukturze.</span><span class="sxs-lookup"><span data-stu-id="17766-131">For example, the following example with the IOrderRepository interface defines what operations the OrderRepository class will need to implement at the infrastructure layer.</span></span> <span data-ttu-id="17766-132">Bieżąca implementacja aplikacji kod właśnie musi dodać lub zaktualizować zamówień w bazie danych, ponieważ zapytania są podzielone na następujące podejście CQRS uproszczone.</span><span class="sxs-lookup"><span data-stu-id="17766-132">In the current implementation of the application, the code just needs to add or update orders to the database, since queries are split following the simplified CQRS approach.</span></span>

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

## <a name="additional-resources"></a><span data-ttu-id="17766-133">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="17766-133">Additional resources</span></span>

-   <span data-ttu-id="17766-134">**Pole Fowler. Interfejs rozdzielone. ** 
     [ *http://www.martinfowler.com/eaaCatalog/separatedInterface.html*](http://www.martinfowler.com/eaaCatalog/separatedInterface.html)</span><span class="sxs-lookup"><span data-stu-id="17766-134">**Martin Fowler. Separated Interface.**
[*http://www.martinfowler.com/eaaCatalog/separatedInterface.html*](http://www.martinfowler.com/eaaCatalog/separatedInterface.html)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="17766-135">[Poprzednie] (net-core mikrousługi domeny model.md) [dalej] (wdrożenie — wartość objects.md)</span><span class="sxs-lookup"><span data-stu-id="17766-135">[Previous] (net-core-microservice-domain-model.md) [Next] (implement-value-objects.md)</span></span>

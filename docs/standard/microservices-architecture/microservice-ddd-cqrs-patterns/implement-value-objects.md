---
title: "Implementowanie obiekty wartości"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Implementowanie obiekty wartości"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: c20bc80d2ddb864a3a0172beb211974426a278a8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-value-objects"></a><span data-ttu-id="56974-104">Implementowanie obiekty wartości</span><span class="sxs-lookup"><span data-stu-id="56974-104">Implementing value objects</span></span>

<span data-ttu-id="56974-105">Zgodnie z opisem we wcześniejszych sekcjach jednostek i agreguje informacje tożsamości jest podstawą dla jednostek.</span><span class="sxs-lookup"><span data-stu-id="56974-105">As discussed in earlier sections about entities and aggregates, identity is fundamental for entities.</span></span> <span data-ttu-id="56974-106">Istnieją jednak wiele obiektów i elementy danych w systemie, które nie wymagają tożsamości i tożsamości śledzenia, takich jak obiekty wartości.</span><span class="sxs-lookup"><span data-stu-id="56974-106">However, there are many objects and data items in a system that do not require an identity and identity tracking, such as value objects.</span></span>

<span data-ttu-id="56974-107">Obiekt wartości może się odwoływać inne jednostki.</span><span class="sxs-lookup"><span data-stu-id="56974-107">A value object can reference other entities.</span></span> <span data-ttu-id="56974-108">Na przykład w aplikacji, która generuje trasy, który opisuje metodę get z jednego miejsca do innego tej trasy byłoby obiektu wartości.</span><span class="sxs-lookup"><span data-stu-id="56974-108">For example, in an application that generates a route that describes how to get from one point to another, that route would be a value object.</span></span> <span data-ttu-id="56974-109">Byłoby migawkę punktów na określoną trasę, ale ta trasa sugerowane nie miałoby tożsamości, mimo że wewnętrznie może dotyczyć jednostek Miasto, drogowej itd.</span><span class="sxs-lookup"><span data-stu-id="56974-109">It would be a snapshot of points on a specific route, but this suggested route would not have an identity, even though internally it might refer to entities like City, Road, etc.</span></span>

<span data-ttu-id="56974-110">Rysunek 9-13 przedstawiono obiektu wartości adresu w kolejności agregacji.</span><span class="sxs-lookup"><span data-stu-id="56974-110">Figure 9-13 shows the Address value object within the Order aggregate.</span></span>

![](./media/image14.png)

<span data-ttu-id="56974-111">**Rysunek 9-13**.</span><span class="sxs-lookup"><span data-stu-id="56974-111">**Figure 9-13**.</span></span> <span data-ttu-id="56974-112">Adres obiektu wartości w kolejności agregacji</span><span class="sxs-lookup"><span data-stu-id="56974-112">Address value object within the Order aggregate</span></span>

<span data-ttu-id="56974-113">Jak pokazano w rysunek 9-13, jednostki zazwyczaj składa się z wielu atrybutów.</span><span class="sxs-lookup"><span data-stu-id="56974-113">As shown in Figure 9-13, an entity is usually composed of multiple attributes.</span></span> <span data-ttu-id="56974-114">Na przykład kolejności można modelowane jako jednostki o tożsamości i wewnętrznie składa się z zestawu atrybutów, takich jak OrderId OrderDate, OrderItems itp. Ale adresu, który jest po prostu złożona wartość składa się z kraju ulicy, miasta, itp. muszą być modelowane i traktowane jako obiekt wartości.</span><span class="sxs-lookup"><span data-stu-id="56974-114">For example, Order can be modeled as an entity with an identity and composed internally of a set of attributes such as OrderId, OrderDate, OrderItems, etc. But the address, which is simply a complex value composed of country, street, city, etc. must be modeled and treated as a value object.</span></span>

## <a name="important-characteristics-of-value-objects"></a><span data-ttu-id="56974-115">Najważniejsze czynniki wartość obiektów</span><span class="sxs-lookup"><span data-stu-id="56974-115">Important characteristics of value objects</span></span>

<span data-ttu-id="56974-116">Istnieją dwa główne cechy dla obiektów wartości:</span><span class="sxs-lookup"><span data-stu-id="56974-116">There are two main characteristics for value objects:</span></span>

-   <span data-ttu-id="56974-117">Mają one nie tożsamości.</span><span class="sxs-lookup"><span data-stu-id="56974-117">They have no identity.</span></span>

-   <span data-ttu-id="56974-118">Są one niezmienialny.</span><span class="sxs-lookup"><span data-stu-id="56974-118">They are immutable.</span></span>

<span data-ttu-id="56974-119">Pierwszy cech już został omówiony.</span><span class="sxs-lookup"><span data-stu-id="56974-119">The first characteristic was already discussed.</span></span> <span data-ttu-id="56974-120">Immutability musi być spełniony ważne.</span><span class="sxs-lookup"><span data-stu-id="56974-120">Immutability is an important requirement.</span></span> <span data-ttu-id="56974-121">Wartości obiektu wartości należy modyfikować po utworzeniu obiektu.</span><span class="sxs-lookup"><span data-stu-id="56974-121">The values of a value object must be immutable once the object is created.</span></span> <span data-ttu-id="56974-122">W związku z tym podczas konstruowania obiektu, należy podać wartości wymagane, ale musi zezwala zmienić okres istnienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="56974-122">Therefore, when the object is constructed, you must provide the required values, but you must not allow them to change during the object’s lifetime.</span></span>

<span data-ttu-id="56974-123">Obiekty wartości umożliwiają wykonywanie niektórych lewy wydajności dzięki użyciu natury niezmienialny.</span><span class="sxs-lookup"><span data-stu-id="56974-123">Value objects allow you to perform certain tricks for performance, thanks to their immutable nature.</span></span> <span data-ttu-id="56974-124">Jest to szczególnie istotne w systemach gdzie mogą być tysiące wartość wystąpienia obiektów, z których wiele mają takie same wartości.</span><span class="sxs-lookup"><span data-stu-id="56974-124">This is especially true in systems where there may be thousands of value object instances, many of which have the same values.</span></span> <span data-ttu-id="56974-125">Natury niezmienne umożliwia ich ponowne użycie; od czasu ich wartości są takie same i mają tożsamości nie mogą być wymienne obiektów.</span><span class="sxs-lookup"><span data-stu-id="56974-125">Their immutable nature allows them to be reused; they can be interchangeable objects, since their values are the same and they have no identity.</span></span> <span data-ttu-id="56974-126">Ten rodzaj optymalizacji czasami wprowadzić różnica między oprogramowaniem dobrą wydajność i oprogramowania, które działa powoli.</span><span class="sxs-lookup"><span data-stu-id="56974-126">This type of optimization can sometimes make a difference between software that runs slowly and software with good performance.</span></span> <span data-ttu-id="56974-127">Oczywiście wszystkich tych przypadkach zależą od środowiska aplikacji i wdrażania kontekstu.</span><span class="sxs-lookup"><span data-stu-id="56974-127">Of course, all these cases depend on the application environment and deployment context.</span></span>

## <a name="value-object-implementation-in-c"></a><span data-ttu-id="56974-128">Wartość implementacji obiektu w języku C\#</span><span class="sxs-lookup"><span data-stu-id="56974-128">Value object implementation in C\#</span></span>

<span data-ttu-id="56974-129">W implementacji może mieć klasy podstawowej obiektu wartość, która ma metody podstawowe narzędzia, takie jak równości na podstawie porównania między wszystkie atrybuty (ponieważ obiektu wartości nie musi być oparta na tożsamości) oraz innych podstawowych właściwości.</span><span class="sxs-lookup"><span data-stu-id="56974-129">In terms of implementation, you can have a value object base class that has basic utility methods like equality based on comparison between all the attributes (since a value object must not be based on identity) and other fundamental characteristics.</span></span> <span data-ttu-id="56974-130">W poniższym przykładzie przedstawiono wartości obiektu klasy podstawowej, używany w porządkowania mikrousługi z eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="56974-130">The following example shows a value object base class used in the ordering microservice from eShopOnContainers.</span></span>

```csharp
public abstract class ValueObject
{
    protected static bool EqualOperator(ValueObject left, ValueObject right)
    {
        if (ReferenceEquals(left, null) ^ ReferenceEquals(right, null))
        {
            return false;
        }
        return ReferenceEquals(left, null) || left.Equals(right);
    }

    protected static bool NotEqualOperator(ValueObject left, ValueObject right)
    {
        return !(EqualOperator(left, right));
    }

    protected abstract IEnumerable<object> GetAtomicValues();

    public override bool Equals(object obj)
    {
        if (obj == null || obj.GetType() != GetType())
        {
            return false;
        }

        ValueObject other = (ValueObject)obj;
        IEnumerator<object> thisValues = GetAtomicValues().GetEnumerator();
        IEnumerator<object> otherValues = other.GetAtomicValues().GetEnumerator();
        while (thisValues.MoveNext() && otherValues.MoveNext())
        {
            if (ReferenceEquals(thisValues.Current, null) ^
                ReferenceEquals(otherValues.Current, null))
            {
                return false;
            }

            if (thisValues.Current != null &&
                !thisValues.Current.Equals(otherValues.Current))
            {
                return false;
            }
        }
        return !thisValues.MoveNext() && !otherValues.MoveNext();
    }
    // Other utilility methods
}
```

<span data-ttu-id="56974-131">Tej klasy można użyć podczas wykonywania obiekt rzeczywistej wartości, tak jak w przypadku obiektu wartości adresu pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="56974-131">You can use this class when implementing your actual value object, as with the Address value object shown in the following example:</span></span>

```csharp
public class Address : ValueObject
{
    public String Street { get; private set; }
    public String City { get; private set; }
    public String State { get; private set; }
    public String Country { get; private set; }
    public String ZipCode { get; private set; }

    public Address(string street, string city, string state,
        string country, string zipcode)
    {
        Street = street;
        City = city;
        State = state;
        Country = country;
        ZipCode = zipcode;
    }

    protected override IEnumerable<object> GetAtomicValues()
    {
        yield return Street;
        yield return City;
        yield return State;
        yield return Country;
        yield return ZipCode;
    }
}
```

## <a name="hiding-the-identity-characteristic-when-using-ef-core-to-persist-value-objects"></a><span data-ttu-id="56974-132">Ukrywanie właściwości tożsamości, używając EF Core utrwalić obiekty wartości</span><span class="sxs-lookup"><span data-stu-id="56974-132">Hiding the identity characteristic when using EF Core to persist value objects</span></span>

<span data-ttu-id="56974-133">To ograniczenie, gdy przy użyciu EF Core jest, że w jego bieżącej wersji (EF Core 1.1) nie można użyć [typów złożonych](https://docs.microsoft.com/de-de/dotnet/api/system.componentmodel.dataannotations.schema.complextypeattribute?view=netframework-4.7) zgodnie z definicją w EF 6.x.</span><span class="sxs-lookup"><span data-stu-id="56974-133">A limitation when using EF Core is that in its current version (EF Core 1.1) you cannot use [complex types](https://docs.microsoft.com/de-de/dotnet/api/system.componentmodel.dataannotations.schema.complextypeattribute?view=netframework-4.7) as defined in EF 6.x.</span></span> <span data-ttu-id="56974-134">W związku z tym obiektu wartości muszą być przechowywane jako jednostka EF.</span><span class="sxs-lookup"><span data-stu-id="56974-134">Therefore, you must store your value object as an EF entity.</span></span> <span data-ttu-id="56974-135">Jednak można ukryć jego Identyfikatora, więc można wyjaśnić, że tożsamość nie jest ważna w modelu, który obiekt wartości jest częścią.</span><span class="sxs-lookup"><span data-stu-id="56974-135">However, you can hide its ID so you make clear that the identity is not important in the model that the value object is part of.</span></span> <span data-ttu-id="56974-136">Ukryj identyfikator jest za pomocą Identyfikatora jako właściwość cienia.</span><span class="sxs-lookup"><span data-stu-id="56974-136">You hide the ID is by using the ID as a shadow property.</span></span> <span data-ttu-id="56974-137">Ponieważ tego ukrywania identyfikator modelu jest skonfigurowany na poziomie infrastruktury, będzie niewidoczny dla modelu domeny i jej wdrożenia infrastruktury można zmienić w przyszłości.</span><span class="sxs-lookup"><span data-stu-id="56974-137">Since that configuration for hiding the ID in the model is set up in the infrastructure level, it will be transparent for your domain model, and its infrastructure implementation could change in the future.</span></span>

<span data-ttu-id="56974-138">W eShopOnContainers identyfikator ukryte potrzebne w infrastrukturze podstawowej EF jest zaimplementowana w następujący sposób na poziomie DbContext przy użyciu interfejsu API Fluent w projekcie infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="56974-138">In eShopOnContainers, the hidden ID needed by EF Core infrastructure is implemented in the following way in the DbContext level, using Fluent API at the infrastructure project.</span></span>

```csharp
// Fluent API within the OrderingContext:DbContext in the
// Ordering.Infrastructure project

void ConfigureAddress(EntityTypeBuilder<Address> addressConfiguration)
{
    addressConfiguration.ToTable("address", DEFAULT_SCHEMA);
    addressConfiguration.Property<int>("Id").IsRequired();
    addressConfiguration.HasKey("Id");
}
```

<span data-ttu-id="56974-139">W związku z tym Identyfikatorem jest ukryty z punktu widzenia modelu domeny, a w przyszłości infrastruktury obiektu wartość może również być implementowana jako typ złożony lub w inny sposób.</span><span class="sxs-lookup"><span data-stu-id="56974-139">Therefore, the ID is hidden from the domain model point of view, and in the future, the value object infrastructure could also be implemented as a complex type or another way.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="56974-140">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="56974-140">Additional resources</span></span>

-   <span data-ttu-id="56974-141">**Pole Fowler. Wzorzec ValueObject**
    [*https://martinfowler.com/bliki/ValueObject.html*](https://martinfowler.com/bliki/ValueObject.html)</span><span class="sxs-lookup"><span data-stu-id="56974-141">**Martin Fowler. ValueObject pattern**
[*https://martinfowler.com/bliki/ValueObject.html*](https://martinfowler.com/bliki/ValueObject.html)</span></span>

-   <span data-ttu-id="56974-142">**Evans marek. Projektowanie oparte na domenie: Czoła złożoności serca oprogramowania.**</span><span class="sxs-lookup"><span data-stu-id="56974-142">**Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software.**</span></span> <span data-ttu-id="56974-143">(Książki; zawiera omówienie obiekty wartości) [ *https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)</span><span class="sxs-lookup"><span data-stu-id="56974-143">(Book; includes a discussion of value objects) [*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)</span></span>

-   <span data-ttu-id="56974-144">**Vaughn Vernon. Implementowanie projektu opartych na domenie.**</span><span class="sxs-lookup"><span data-stu-id="56974-144">**Vaughn Vernon. Implementing Domain-Driven Design.**</span></span> <span data-ttu-id="56974-145">(Książki; zawiera omówienie obiekty wartości) [ *https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)</span><span class="sxs-lookup"><span data-stu-id="56974-145">(Book; includes a discussion of value objects) [*https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)</span></span>

-   <span data-ttu-id="56974-146">**Właściwości w tle**
    [*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)</span><span class="sxs-lookup"><span data-stu-id="56974-146">**Shadow Properties**
[*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)</span></span>

-   <span data-ttu-id="56974-147">**Typy złożone i/lub obiekty wartości**.</span><span class="sxs-lookup"><span data-stu-id="56974-147">**Complex types and/or value objects**.</span></span> <span data-ttu-id="56974-148">Omówienie w repozytorium EF Core GitHub (karta problemy) [ *https://github.com/aspnet/EntityFramework/issues/246*](https://github.com/aspnet/EntityFramework/issues/246)</span><span class="sxs-lookup"><span data-stu-id="56974-148">Discussion in the EF Core GitHub repo (Issues tab) [*https://github.com/aspnet/EntityFramework/issues/246*](https://github.com/aspnet/EntityFramework/issues/246)</span></span>

-   <span data-ttu-id="56974-149">**ValueObject.cs.**</span><span class="sxs-lookup"><span data-stu-id="56974-149">**ValueObject.cs.**</span></span> <span data-ttu-id="56974-150">Wartość podstawową klasy obiektów w eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="56974-150">Base value object class in eShopOnContainers.</span></span>
    [<span data-ttu-id="56974-151">*https://github.com/DotNet/eShopOnContainers/blob/Master/src/Services/Ordering/Ordering.domain/SeedWork/ValueObject.CS*</span><span class="sxs-lookup"><span data-stu-id="56974-151">*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs*</span></span>](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs)

-   <span data-ttu-id="56974-152">**Klasy adresów.**</span><span class="sxs-lookup"><span data-stu-id="56974-152">**Address class.**</span></span> <span data-ttu-id="56974-153">Przykładowe wartości klasy obiektów w eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="56974-153">Sample value object class in eShopOnContainers.</span></span>
    [<span data-ttu-id="56974-154">*https://github.com/DotNet/eShopOnContainers/blob/Master/src/Services/Ordering/Ordering.domain/AggregatesModel/OrderAggregate/Address.CS*</span><span class="sxs-lookup"><span data-stu-id="56974-154">*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs*</span></span>](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs)


>[!div class="step-by-step"]
<span data-ttu-id="56974-155">[Poprzednie] (seedwork-domain-model-base-classes-interfaces.md) [dalej] (wyliczenie klasy over wyliczenia types.md)</span><span class="sxs-lookup"><span data-stu-id="56974-155">[Previous] (seedwork-domain-model-base-classes-interfaces.md) [Next] (enumeration-classes-over-enum-types.md)</span></span>

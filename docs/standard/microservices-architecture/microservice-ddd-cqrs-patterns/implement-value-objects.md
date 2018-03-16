---
title: "Implementowanie obiekty wartości"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Implementowanie obiekty wartości"
keywords: Docker, Microservices, ASP.NET, Container
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/12/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ce81991e48fb5eb4eb3bed3dd2fcfe1734ca7bac
ms.sourcegitcommit: 1c0b0f082b3f300e54b4d069b317ac724c88ddc3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2018
---
# <a name="implementing-value-objects"></a><span data-ttu-id="b1a27-104">Implementowanie obiekty wartości</span><span class="sxs-lookup"><span data-stu-id="b1a27-104">Implementing value objects</span></span>

<span data-ttu-id="b1a27-105">Zgodnie z opisem we wcześniejszych sekcjach jednostek i agreguje informacje tożsamości jest podstawą dla jednostek.</span><span class="sxs-lookup"><span data-stu-id="b1a27-105">As discussed in earlier sections about entities and aggregates, identity is fundamental for entities.</span></span> <span data-ttu-id="b1a27-106">Istnieją jednak wiele obiektów i elementy danych w systemie, które nie wymagają tożsamości i tożsamości śledzenia, takich jak obiekty wartości.</span><span class="sxs-lookup"><span data-stu-id="b1a27-106">However, there are many objects and data items in a system that do not require an identity and identity tracking, such as value objects.</span></span>

<span data-ttu-id="b1a27-107">Obiekt wartości może się odwoływać inne jednostki.</span><span class="sxs-lookup"><span data-stu-id="b1a27-107">A value object can reference other entities.</span></span> <span data-ttu-id="b1a27-108">Na przykład w aplikacji, która generuje trasy, który opisuje metodę get z jednego miejsca do innego tej trasy byłoby obiektu wartości.</span><span class="sxs-lookup"><span data-stu-id="b1a27-108">For example, in an application that generates a route that describes how to get from one point to another, that route would be a value object.</span></span> <span data-ttu-id="b1a27-109">Byłoby migawkę punktów na określoną trasę, ale ta trasa sugerowane nie miałoby tożsamości, mimo że wewnętrznie może dotyczyć jednostek Miasto, drogowej itd.</span><span class="sxs-lookup"><span data-stu-id="b1a27-109">It would be a snapshot of points on a specific route, but this suggested route would not have an identity, even though internally it might refer to entities like City, Road, etc.</span></span>

<span data-ttu-id="b1a27-110">Rysunek 9-13 przedstawiono obiektu wartości adresu w kolejności agregacji.</span><span class="sxs-lookup"><span data-stu-id="b1a27-110">Figure 9-13 shows the Address value object within the Order aggregate.</span></span>

![](./media/image14.png)

<span data-ttu-id="b1a27-111">**Rysunek 9-13**.</span><span class="sxs-lookup"><span data-stu-id="b1a27-111">**Figure 9-13**.</span></span> <span data-ttu-id="b1a27-112">Adres obiektu wartości w kolejności agregacji</span><span class="sxs-lookup"><span data-stu-id="b1a27-112">Address value object within the Order aggregate</span></span>

<span data-ttu-id="b1a27-113">Jak pokazano w rysunek 9-13, jednostki zazwyczaj składa się z wielu atrybutów.</span><span class="sxs-lookup"><span data-stu-id="b1a27-113">As shown in Figure 9-13, an entity is usually composed of multiple attributes.</span></span> <span data-ttu-id="b1a27-114">Na przykład `Order` jednostki można modelowane jako jednostki o tożsamości i wewnętrznie składa się z zestawu atrybutów, takich jak OrderId OrderDate, OrderItems itp. Ale adresu, który jest po prostu złożona wartość składa się z kraju ulicy, miasta itp. i ma nie tożsamość w tej domenie, musi być modelowane i traktowane jako obiekt wartości.</span><span class="sxs-lookup"><span data-stu-id="b1a27-114">For example, the `Order` entity can be modeled as an entity with an identity and composed internally of a set of attributes such as OrderId, OrderDate, OrderItems, etc. But the address, which is simply a complex value composed of country, street, city, etc. and has no identity in this domain,  must be modeled and treated as a value object.</span></span>

## <a name="important-characteristics-of-value-objects"></a><span data-ttu-id="b1a27-115">Najważniejsze czynniki wartość obiektów</span><span class="sxs-lookup"><span data-stu-id="b1a27-115">Important characteristics of value objects</span></span>

<span data-ttu-id="b1a27-116">Istnieją dwa główne cechy dla obiektów wartości:</span><span class="sxs-lookup"><span data-stu-id="b1a27-116">There are two main characteristics for value objects:</span></span>

-   <span data-ttu-id="b1a27-117">Mają one nie tożsamości.</span><span class="sxs-lookup"><span data-stu-id="b1a27-117">They have no identity.</span></span>

-   <span data-ttu-id="b1a27-118">Są one niezmienialny.</span><span class="sxs-lookup"><span data-stu-id="b1a27-118">They are immutable.</span></span>

<span data-ttu-id="b1a27-119">Pierwszy cech już został omówiony.</span><span class="sxs-lookup"><span data-stu-id="b1a27-119">The first characteristic was already discussed.</span></span> <span data-ttu-id="b1a27-120">Immutability musi być spełniony ważne.</span><span class="sxs-lookup"><span data-stu-id="b1a27-120">Immutability is an important requirement.</span></span> <span data-ttu-id="b1a27-121">Wartości obiektu wartości należy modyfikować po utworzeniu obiektu.</span><span class="sxs-lookup"><span data-stu-id="b1a27-121">The values of a value object must be immutable once the object is created.</span></span> <span data-ttu-id="b1a27-122">W związku z tym podczas konstruowania obiektu, należy podać wartości wymagane, ale musi zezwala zmienić okres istnienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="b1a27-122">Therefore, when the object is constructed, you must provide the required values, but you must not allow them to change during the object’s lifetime.</span></span>

<span data-ttu-id="b1a27-123">Obiekty wartości umożliwiają wykonywanie niektórych lewy wydajności dzięki użyciu natury niezmienialny.</span><span class="sxs-lookup"><span data-stu-id="b1a27-123">Value objects allow you to perform certain tricks for performance, thanks to their immutable nature.</span></span> <span data-ttu-id="b1a27-124">Jest to szczególnie istotne w systemach gdzie mogą być tysiące wartość wystąpienia obiektów, z których wiele mają takie same wartości.</span><span class="sxs-lookup"><span data-stu-id="b1a27-124">This is especially true in systems where there may be thousands of value object instances, many of which have the same values.</span></span> <span data-ttu-id="b1a27-125">Natury niezmienne umożliwia ich ponowne użycie; od czasu ich wartości są takie same i mają tożsamości nie mogą być wymienne obiektów.</span><span class="sxs-lookup"><span data-stu-id="b1a27-125">Their immutable nature allows them to be reused; they can be interchangeable objects, since their values are the same and they have no identity.</span></span> <span data-ttu-id="b1a27-126">Ten rodzaj optymalizacji czasami wprowadzić różnica między oprogramowaniem dobrą wydajność i oprogramowania, które działa powoli.</span><span class="sxs-lookup"><span data-stu-id="b1a27-126">This type of optimization can sometimes make a difference between software that runs slowly and software with good performance.</span></span> <span data-ttu-id="b1a27-127">Oczywiście wszystkich tych przypadkach zależą od środowiska aplikacji i wdrażania kontekstu.</span><span class="sxs-lookup"><span data-stu-id="b1a27-127">Of course, all these cases depend on the application environment and deployment context.</span></span>

## <a name="value-object-implementation-in-c"></a><span data-ttu-id="b1a27-128">Wartość implementacji obiektu w języku C\#</span><span class="sxs-lookup"><span data-stu-id="b1a27-128">Value object implementation in C\#</span></span>

<span data-ttu-id="b1a27-129">W implementacji może mieć klasy podstawowej obiektu wartość, która ma metody podstawowe narzędzia, takie jak równości na podstawie porównania między wszystkie atrybuty (ponieważ obiektu wartości nie musi być oparta na tożsamości) oraz innych podstawowych właściwości.</span><span class="sxs-lookup"><span data-stu-id="b1a27-129">In terms of implementation, you can have a value object base class that has basic utility methods like equality based on comparison between all the attributes (since a value object must not be based on identity) and other fundamental characteristics.</span></span> <span data-ttu-id="b1a27-130">W poniższym przykładzie przedstawiono wartości obiektu klasy podstawowej, używany w porządkowania mikrousługi z eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="b1a27-130">The following example shows a value object base class used in the ordering microservice from eShopOnContainers.</span></span>

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

    public override int GetHashCode()
    {
        return GetAtomicValues()
         .Select(x => x != null ? x.GetHashCode() : 0)
         .Aggregate((x, y) => x ^ y);
    }        
    // Other utilility methods
}
```

<span data-ttu-id="b1a27-131">Tej klasy można użyć podczas wykonywania obiekt rzeczywistej wartości, tak jak w przypadku obiektu wartości adresu pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="b1a27-131">You can use this class when implementing your actual value object, as with the Address value object shown in the following example:</span></span>

```csharp
public class Address : ValueObject
{
    public String Street { get; private set; }
    public String City { get; private set; }
    public String State { get; private set; }
    public String Country { get; private set; }
    public String ZipCode { get; private set; }

    private Address() { }

    public Address(string street, string city, string state, string country, string zipcode)
    {
        Street = street;
        City = city;
        State = state;
        Country = country;
        ZipCode = zipcode;
    }

    protected override IEnumerable<object> GetAtomicValues()
    {
        // Using a yield return statement to return each element one at a time
        yield return Street;
        yield return City;
        yield return State;
        yield return Country;
        yield return ZipCode;
    }
}
```

## <a name="how-to-persist-value-objects-in-the-database-with-ef-core-20"></a><span data-ttu-id="b1a27-132">Jak zachować wartości obiektów w bazie danych EF Core 2.0</span><span class="sxs-lookup"><span data-stu-id="b1a27-132">How to persist value objects in the database with EF Core 2.0</span></span>

<span data-ttu-id="b1a27-133">Widać tylko sposób definiowania obiektu wartości do modelu domeny.</span><span class="sxs-lookup"><span data-stu-id="b1a27-133">You just saw how to define a value object in your domain model.</span></span> <span data-ttu-id="b1a27-134">Ale, jak można można faktycznie utrwalić go do bazy danych za pośrednictwem Core Entity Framework (EF), która zwykle jest przeznaczony dla jednostek z tożsamością?</span><span class="sxs-lookup"><span data-stu-id="b1a27-134">But, how can you actually persist it into the database through Entity Framework (EF) Core which usually targets entities with identity?</span></span>

### <a name="background-and-older-approaches-using-ef-core-11"></a><span data-ttu-id="b1a27-135">Tło i starszych podejścia przy użyciu EF Core 1.1</span><span class="sxs-lookup"><span data-stu-id="b1a27-135">Background and older approaches using EF Core 1.1</span></span>

<span data-ttu-id="b1a27-136">Jako tło, to ograniczenie, używając EF Core 1.0 i 1.1 został, że nie można użyć [typów złożonych](xref:System.ComponentModel.DataAnnotations.Schema.ComplexTypeAttribute) zgodnie z definicją w EF 6.x w tradycyjnych .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b1a27-136">As background, a limitation when using EF Core 1.0 and 1.1 was that you cannot use  [complex types](xref:System.ComponentModel.DataAnnotations.Schema.ComplexTypeAttribute) as defined in EF 6.x in the traditional .NET Framework.</span></span> <span data-ttu-id="b1a27-137">W związku z tym jeśli przy użyciu EF Core w wersji 1.0 lub 1.1, potrzebne do przechowywania wartości obiektu jako jednostka EF z pola identyfikator.</span><span class="sxs-lookup"><span data-stu-id="b1a27-137">Therefore, if using EF Core 1.0 or 1.1, you needed to store your value object as an EF entity with an ID field.</span></span> <span data-ttu-id="b1a27-138">Następnie tak będzie wyglądał więcej takich jak obiekt wartości przy nie tożsamości, można ukryć jego identyfikator, więc można wyjaśnić, że tożsamość obiektu wartości nie jest ważna w modelu domeny.</span><span class="sxs-lookup"><span data-stu-id="b1a27-138">Then, so it looked more like a value object with no identity, you could hide its ID so you make clear that the identity of a value object is not important in the domain model.</span></span> <span data-ttu-id="b1a27-139">Ten identyfikator można ukryć przy użyciu Identyfikatora jako [w tle właściwości](https://docs.microsoft.com/ef/core/modeling/shadow-properties ).</span><span class="sxs-lookup"><span data-stu-id="b1a27-139">You could hide that ID by using the ID as a [shadow property](https://docs.microsoft.com/ef/core/modeling/shadow-properties ).</span></span> <span data-ttu-id="b1a27-140">Ponieważ tego ukrywania identyfikator modelu jest skonfigurowany na poziomie infrastruktury EF, byłoby rodzaj niewidoczny dla modelu domeny.</span><span class="sxs-lookup"><span data-stu-id="b1a27-140">Since that configuration for hiding the ID in the model is set up in the EF infrastructure level, it would be kind of transparent for your domain model.</span></span>

<span data-ttu-id="b1a27-141">W pierwotnej wersji eShopOnContainers (.NET Core 1.1) identyfikator ukryte potrzebne w infrastrukturze podstawowej EF został wdrożony w następujący sposób na poziomie typu DbContext w projekcie infrastruktury przy użyciu interfejsu API Fluent.</span><span class="sxs-lookup"><span data-stu-id="b1a27-141">In the initial version of eShopOnContainers (.NET Core 1.1), the hidden ID needed by EF Core infrastructure was implemented in the following way in the DbContext level, using Fluent API at the infrastructure project.</span></span> <span data-ttu-id="b1a27-142">W związku z tym Identyfikatorem była ukrytych z punktu widzenia modelu domeny, lecz nadal znajdują się w infrastrukturze.</span><span class="sxs-lookup"><span data-stu-id="b1a27-142">Therefore, the ID was hidden from the domain model point of view, but still present in the infrastructure.</span></span>

```csharp
// Old approach with EF Core 1.1
// Fluent API within the OrderingContext:DbContext in the Infrastructure project
void ConfigureAddress(EntityTypeBuilder<Address> addressConfiguration) 
{
    addressConfiguration.ToTable("address", DEFAULT_SCHEMA); 

    addressConfiguration.Property<int>("Id")  // Id is a shadow property
        .IsRequired();
    addressConfiguration.HasKey("Id");   // Id is a shadow property
}
```

<span data-ttu-id="b1a27-143">Jednak trwałości wartość obiektu do bazy danych została wykonana, takie jak regularne jednostki w innej tabeli.</span><span class="sxs-lookup"><span data-stu-id="b1a27-143">However, the persistence of that value object into the database was performed like a regular entity in a different table.</span></span>

<span data-ttu-id="b1a27-144">EF Core 2.0, są nowe i lepsze metody, aby utrwalić obiekty wartości.</span><span class="sxs-lookup"><span data-stu-id="b1a27-144">With EF Core 2.0, there are new and better ways to persist value objects.</span></span>

## <a name="persist-value-objects-as-owned-entity-types-in-ef-core-20"></a><span data-ttu-id="b1a27-145">Utrwalanie obiekty wartości jako typy jednostek należące do firmy w programie EF Core 2.0</span><span class="sxs-lookup"><span data-stu-id="b1a27-145">Persist value objects as owned entity types in EF Core 2.0</span></span>

<span data-ttu-id="b1a27-146">Nawet w przypadku niektórych luki pomiędzy wzorzec obiektu wartości kanonicznej w DDD i typ należących do jednostki w podstawowej EF obecnie jest najlepszy sposób, aby utrwalić obiekty wartości EF Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="b1a27-146">Even with some gaps between the canonical value object pattern in DDD and the owned entity type in EF Core, it's currently the best way to persist value objects with EF Core 2.0.</span></span> <span data-ttu-id="b1a27-147">Widać ograniczenia na końcu tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="b1a27-147">You can see limitations at the end of this section.</span></span>

<span data-ttu-id="b1a27-148">Funkcja Typ należących do jednostki został dodany do EF Core od wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="b1a27-148">The owned entity type feature was added to EF Core since version 2.0.</span></span>

<span data-ttu-id="b1a27-149">Typ jednostki należące do firmy pozwala na mapowanie typów, które nie mają własnych jawnie tożsamości zdefiniowanej w modelu domeny i są używane jako właściwości, takie jak obiekt wartości w żadnej jednostki.</span><span class="sxs-lookup"><span data-stu-id="b1a27-149">An owned entity type allows you to map types that do not have their own identity explicitely defined in the domain model and are used as properties, such as a value object, within any of your entities.</span></span> <span data-ttu-id="b1a27-150">Typ jednostki należących do udziałów tego samego typu CLR z innym typem jednostki.</span><span class="sxs-lookup"><span data-stu-id="b1a27-150">An owned entity type shares the same CLR type with another entity type.</span></span> <span data-ttu-id="b1a27-151">Obiekt zawierający definiującego nawigacji jest jednostką właściciela.</span><span class="sxs-lookup"><span data-stu-id="b1a27-151">The entity containing the defining navigation is the owner entity.</span></span> <span data-ttu-id="b1a27-152">Podczas wykonywania zapytania właściciela, typy należące do firmy są domyślnie dołączone.</span><span class="sxs-lookup"><span data-stu-id="b1a27-152">When querying the owner, the owned types are included by default.</span></span>

<span data-ttu-id="b1a27-153">Tylko na podstawie modelu domeny, należących do typu prawdopodobnie nie ma żadnych tożsamości.</span><span class="sxs-lookup"><span data-stu-id="b1a27-153">Just by looking at the domain model, an owned type looks like it doesn’t have any identity.</span></span>
<span data-ttu-id="b1a27-154">Jednak w obszarze obejmuje należących do typów ma tożsamość, ale właściwość nawigacji właściciela jest częścią tej tożsamości.</span><span class="sxs-lookup"><span data-stu-id="b1a27-154">However, under the covers, owned types do have identity, but the owner navigation property is part of this identity.</span></span>

<span data-ttu-id="b1a27-155">Tożsamość wystąpienia własnych typów nie jest całkowicie własne.</span><span class="sxs-lookup"><span data-stu-id="b1a27-155">The identity of instances of own types is not completely their own.</span></span> <span data-ttu-id="b1a27-156">Składa się z trzech składników:</span><span class="sxs-lookup"><span data-stu-id="b1a27-156">It consists of three components:</span></span>

- <span data-ttu-id="b1a27-157">Tożsamość właściciela</span><span class="sxs-lookup"><span data-stu-id="b1a27-157">The identity of the owner</span></span>

- <span data-ttu-id="b1a27-158">Wskazuje właściwość nawigacji</span><span class="sxs-lookup"><span data-stu-id="b1a27-158">The navigation property pointing to them</span></span>

- <span data-ttu-id="b1a27-159">W przypadku kolekcji należących do typów, niezależnie od składnika (nie jest jeszcze obsługiwane w programie EF Core 2.0).</span><span class="sxs-lookup"><span data-stu-id="b1a27-159">In the case of collections of owned types, an independent component (not yet supported in EF Core 2.0).</span></span>

<span data-ttu-id="b1a27-160">Na przykład w modelu domeny porządkowanie na eShopOnContainers jako część jednostki kolejności obiekt wartość adres jest zaimplementowany jako typu jednostki należące do firmy w ramach jednostki właściciela, czyli kolejność jednostki.</span><span class="sxs-lookup"><span data-stu-id="b1a27-160">For example, in the Ordering domain model at eShopOnContainers, as part of the Order entity, the Address value object is implemented as an owned entity type within the owner entity, which is the Order entity.</span></span> <span data-ttu-id="b1a27-161">Adres jest typem z ma właściwości tożsamości zdefiniowanej w modelu domeny.</span><span class="sxs-lookup"><span data-stu-id="b1a27-161">Address is a type with no identity property defined in the domain model.</span></span> <span data-ttu-id="b1a27-162">Aby określić adres wysyłkowy dla określonej kolejności służy jako właściwość typu kolejności.</span><span class="sxs-lookup"><span data-stu-id="b1a27-162">It is used as a property of the Order type to specify the shipping address for a particular order.</span></span>

<span data-ttu-id="b1a27-163">Konwencja klucz podstawowy w tle jest tworzony dla typu należące do firmy i będzie on zamapowany do tej samej tabeli jako właściciel przy użyciu dzielenia tabeli.</span><span class="sxs-lookup"><span data-stu-id="b1a27-163">By convention, a shadow primary key is created for the owned type and it will be mapped to the same table as the owner by using table splitting.</span></span> <span data-ttu-id="b1a27-164">Dzięki temu Użyj należące do typów podobnie jak złożonych typów są używane w EF6 w tradycyjnych .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b1a27-164">This allows to use owned types similarly to how complex types are used in EF6 in the traditional .NET Framework.</span></span>

<span data-ttu-id="b1a27-165">Należy pamiętać, że który należące do typów nigdy nie są wykrywane przez Konwencję w podstawowej EF, dlatego należy je jawnie deklarować.</span><span class="sxs-lookup"><span data-stu-id="b1a27-165">It is important to note that owned types are never discovered by convention in EF Core, so you have to declare them explicitly.</span></span>

<span data-ttu-id="b1a27-166">W eShopOnContainers w OrderingContext.cs, w metodzie OnModelCreating() istnieje wiele konfiguracji infrastruktury, które są stosowane.</span><span class="sxs-lookup"><span data-stu-id="b1a27-166">In eShopOnContainers, at the OrderingContext.cs, within the OnModelCreating() method, there are multiple infrastructure configuration being applied.</span></span> <span data-ttu-id="b1a27-167">Jeden z nich jest powiązany z jednostki kolejności.</span><span class="sxs-lookup"><span data-stu-id="b1a27-167">One of them is related to the Order entity.</span></span>

```csharp
// Part of the OrderingContext.cs class at the Ordering.Infrastructure project
// 
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
    modelBuilder.ApplyConfiguration(new ClientRequestEntityTypeConfiguration());
    modelBuilder.ApplyConfiguration(new PaymentMethodEntityTypeConfiguration());
    modelBuilder.ApplyConfiguration(new OrderEntityTypeConfiguration());
    modelBuilder.ApplyConfiguration(new OrderItemEntityTypeConfiguration());
    //...Additional type configurations
}
```

<span data-ttu-id="b1a27-168">W poniższym kodzie infrastruktury trwałości jest zdefiniowany dla encji kolejności:</span><span class="sxs-lookup"><span data-stu-id="b1a27-168">In the following code, the persistence infrastructure is defined for the Order entity:</span></span>

```csharp
// Part of the OrderEntityTypeConfiguration.cs class 
// 
public void Configure(EntityTypeBuilder<Order> orderConfiguration)
{
    orderConfiguration.ToTable("orders", OrderingContext.DEFAULT_SCHEMA);
    orderConfiguration.HasKey(o => o.Id);
    orderConfiguration.Ignore(b => b.DomainEvents);
    orderConfiguration.Property(o => o.Id)
        .ForSqlServerUseSequenceHiLo("orderseq", OrderingContext.DEFAULT_SCHEMA);

    //Address value object persisted as owned entity in EF Core 2.0
    orderConfiguration.OwnsOne(o => o.Address);

    orderConfiguration.Property<DateTime>("OrderDate").IsRequired();
    
    //...Additional validations, constraints and code...
    //...
}
```

<span data-ttu-id="b1a27-169">W poprzednim kodzie `orderConfiguration.OwnsOne(o => o.Address)` Metoda określa, że `Address` właściwość jest należących do jednostki `Order` typu.</span><span class="sxs-lookup"><span data-stu-id="b1a27-169">In the previous code, the `orderConfiguration.OwnsOne(o => o.Address)` method specifies that the `Address` property is an owned entity of the `Order` type.</span></span>

<span data-ttu-id="b1a27-170">Domyślnie EF podstawowe konwencje nazw kolumn bazy danych dla właściwości typu jednostki należące do firmy jako `EntityProperty_OwnedEntityProperty`.</span><span class="sxs-lookup"><span data-stu-id="b1a27-170">By default, EF Core conventions name the database columns for the properties of the owned entity type as `EntityProperty_OwnedEntityProperty`.</span></span> <span data-ttu-id="b1a27-171">W związku z tym wewnętrzna właściwości `Address` będą wyświetlane w `Orders` tabeli z nazwami `Address_Street`, `Address_City` (i tak dalej dla `State`, `Country` i `ZipCode`).</span><span class="sxs-lookup"><span data-stu-id="b1a27-171">Therefore, the internal properties of `Address` will appear in the `Orders` table with the names `Address_Street`, `Address_City` (and so on for `State`, `Country` and `ZipCode`).</span></span>

<span data-ttu-id="b1a27-172">Możesz dołączyć `Property().HasColumnName()` fluent metody można zmienić nazwy kolumny.</span><span class="sxs-lookup"><span data-stu-id="b1a27-172">You can append the `Property().HasColumnName()` fluent method to rename those columns.</span></span> <span data-ttu-id="b1a27-173">W przypadku gdy `Address` jest właściwością publiczną mapowania będzie podobnie do następującej:</span><span class="sxs-lookup"><span data-stu-id="b1a27-173">In the case where `Address` is a public property, the mappings would be like the following:</span></span>

```csharp
orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.Street).HasColumnName("ShippingStreet");

orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.City).HasColumnName("ShippingCity");
```

<span data-ttu-id="b1a27-174">Istnieje możliwość łańcucha `OwnsOne` metody w mapowaniu fluent.</span><span class="sxs-lookup"><span data-stu-id="b1a27-174">It is possible to chain the `OwnsOne` method in a fluent mapping.</span></span> <span data-ttu-id="b1a27-175">W poniższym przykładzie hipotetyczny `OrderDetails` właścicielem `BillingAddress` i `ShippingAddress`, które są oba `Address` typów.</span><span class="sxs-lookup"><span data-stu-id="b1a27-175">In the following hypothetical example, `OrderDetails` owns `BillingAddress` and `ShippingAddress`, which are both `Address` types.</span></span> <span data-ttu-id="b1a27-176">Następnie `OrderDetails` jest własnością `Order` typu.</span><span class="sxs-lookup"><span data-stu-id="b1a27-176">Then `OrderDetails` is owned by the `Order` type.</span></span>

```csharp
orderConfiguration.OwnsOne(p => p.OrderDetails, cb =>
    {
        cb.OwnsOne(c => c.BillingAddress);
        cb.OwnsOne(c => c.ShippingAddress);
    });
//...
//...
public class Order
{
    public int Id { get; set; }
    public OrderDetails OrderDetails { get; set; }
}

public class OrderDetails
{
    public Address BillingAddress { get; set; }
    public Address ShippingAddress { get; set; }
}

public class Address
{
    public string Street { get; set; }
    public string City { get; set; }
}
```

### <a name="additional-details-on-owned-entity-types"></a><span data-ttu-id="b1a27-177">Więcej informacji na temat typów jednostek należące do firmy</span><span class="sxs-lookup"><span data-stu-id="b1a27-177">Additional details on owned entity types</span></span>

<span data-ttu-id="b1a27-178">• Należące do typów zdefiniowanych podczas konfigurowania właściwości nawigacji do określonego typu przy użyciu interfejsu API fluent OwnsOne.</span><span class="sxs-lookup"><span data-stu-id="b1a27-178">•   Owned types are defined when you configure a navigation property to a particular type using the OwnsOne fluent API.</span></span>

<span data-ttu-id="b1a27-179">• Definicji należących do typu w modelu metadanych jest złożone z: Typ właściciela, właściwość nawigacji i typu CLR typu należące do firmy.</span><span class="sxs-lookup"><span data-stu-id="b1a27-179">•   The definition of an owned type in our metadata model is a composite of: the owner type, the navigation property, and the CLR type of the owned type.</span></span>

<span data-ttu-id="b1a27-180">• Tożsamości (klucz) wystąpienia typu należących do naszej stosu jest złożone tożsamości typu właściciela i definicji typu należące do firmy.</span><span class="sxs-lookup"><span data-stu-id="b1a27-180">•   The identity (key) of an owned type instance in our stack is a composite of the identity of the owner type and the definition of the owned type.</span></span>

#### <a name="owned-entities-capabilities"></a><span data-ttu-id="b1a27-181">Należących do podmiotów możliwości:</span><span class="sxs-lookup"><span data-stu-id="b1a27-181">Owned entities capabilities:</span></span>

<span data-ttu-id="b1a27-182">• Należące do typu może odwoływać się inne jednostki, albo własnością (zagnieżdżone typy należące do firmy) lub będących własnością (właściwości nawigacji odwołania regularnych dla innych jednostek).</span><span class="sxs-lookup"><span data-stu-id="b1a27-182">•   Owned type can reference other entities, either owned (nested owned types) or non-owned (regular reference navigation properties to other entities).</span></span>

<span data-ttu-id="b1a27-183">• Można mapowania tej samej CLR typu jako różne typy należące do firmy w tej samej jednostki właściciela za pośrednictwem właściwości oddzielne nawigacji.</span><span class="sxs-lookup"><span data-stu-id="b1a27-183">•   You can map the same CLR type as different owned types in the same owner entity through separate navigation properties.</span></span>

<span data-ttu-id="b1a27-184">• Tabeli dzielenia została skonfigurowana przez Konwencję, ale można zrezygnować z przez mapowanie do innej tabeli za pomocą ToTable należących do typu.</span><span class="sxs-lookup"><span data-stu-id="b1a27-184">•   Table splitting is setup by convention, but you can opt out by mapping the owned type to a different table using ToTable.</span></span>

<span data-ttu-id="b1a27-185">• Wczesny ładowania jest realizowane automatycznie należących do typów, tj. nie trzeba wywołać Include() w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="b1a27-185">•   Eager loading is performed automatically on owned types, i.e. no need to call Include() on the query.</span></span>

#### <a name="owned-entities-limitations"></a><span data-ttu-id="b1a27-186">Jednostek należących do ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="b1a27-186">Owned entities limitations:</span></span>

<span data-ttu-id="b1a27-187">• Nie można utworzyć klasę DbSet<T> należących do typu (zgodnie z projektem).</span><span class="sxs-lookup"><span data-stu-id="b1a27-187">•   You cannot create a DbSet<T> of an owned type (by design).</span></span>

<span data-ttu-id="b1a27-188">• Nie można wywołać ModelBuilder.Entity<T>() na należących do typów (obecnie zgodnie z projektem).</span><span class="sxs-lookup"><span data-stu-id="b1a27-188">•   You cannot call ModelBuilder.Entity<T>() on owned types (currently by design).</span></span>

<span data-ttu-id="b1a27-189">• Nie kolekcje należące do typów jeszcze (ale zostaną one obsługiwane w wersji po EF Core 2.0).</span><span class="sxs-lookup"><span data-stu-id="b1a27-189">•   No collections of owned types yet (but they will be supported in versions after EF Core 2.0).</span></span>

<span data-ttu-id="b1a27-190">• Obsługa ich konfiguracji w atrybucie.</span><span class="sxs-lookup"><span data-stu-id="b1a27-190">•   No support for configuring them via an attribute.</span></span>

<span data-ttu-id="b1a27-191">• Nie obsługuje dla typów opcjonalne należące do firmy (tj. wartości null), które są mapowane z właścicielem w tej samej tabeli (np. przy użyciu dzielenia tabeli).</span><span class="sxs-lookup"><span data-stu-id="b1a27-191">•   No support for optional (i.e. nullable) owned types that are mapped with the owner in the same table (i.e. using table splitting).</span></span> <span data-ttu-id="b1a27-192">To dlatego nie mamy oddzielne wartownik dla wartości null.</span><span class="sxs-lookup"><span data-stu-id="b1a27-192">This is because we don't have a separate sentinel for the null.</span></span>

<span data-ttu-id="b1a27-193">• Nie obsługuje mapowania dziedziczenia dla typów należące do firmy, ale powinno być możliwe do mapowania dwa typy liścia jako różnych typów należących do tej samej hierarchii dziedziczenia.</span><span class="sxs-lookup"><span data-stu-id="b1a27-193">•   No inheritance mapping support for owned types, but you should be able to map two leaf types of the same inheritance hierarchies as different owned types.</span></span> <span data-ttu-id="b1a27-194">Podstawowe EF nie będzie przyczyny o tym, że są one częścią tej samej hierarchii.</span><span class="sxs-lookup"><span data-stu-id="b1a27-194">EF Core will not reason about the fact that they are part of the same hierarchy.</span></span>

#### <a name="main-differences-with-ef6s-complex-types"></a><span data-ttu-id="b1a27-195">Główne różnice z typów złożonych EF6 firmy</span><span class="sxs-lookup"><span data-stu-id="b1a27-195">Main differences with EF6's complex types</span></span>

<span data-ttu-id="b1a27-196">Dzielenie tabeli • jest opcjonalny, tj. Opcjonalnie można mapować do osobnej tabeli i nadal należeć do typów.</span><span class="sxs-lookup"><span data-stu-id="b1a27-196">•   Table splitting is optional, i.e. they can optionally be mapped to a separate table and still be owned types.</span></span>

<span data-ttu-id="b1a27-197">• Odwołujących się inne jednostki (tj. mogą pełnić stronie zależnych na relacje z innych typów nie jest właścicielem).</span><span class="sxs-lookup"><span data-stu-id="b1a27-197">•   They can reference other entities (i.e. they can act as the dependent side on relationships to other non-owned types).</span></span>


## <a name="additional-resources"></a><span data-ttu-id="b1a27-198">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="b1a27-198">Additional resources</span></span>

-   <span data-ttu-id="b1a27-199">**Pole Fowler. Wzorzec ValueObject**
    [*https://martinfowler.com/bliki/ValueObject.html*](https://martinfowler.com/bliki/ValueObject.html)</span><span class="sxs-lookup"><span data-stu-id="b1a27-199">**Martin Fowler. ValueObject pattern**
[*https://martinfowler.com/bliki/ValueObject.html*](https://martinfowler.com/bliki/ValueObject.html)</span></span>

-   <span data-ttu-id="b1a27-200">**Evans marek. Projektowanie oparte na domenie: Czoła złożoności serca oprogramowania.**</span><span class="sxs-lookup"><span data-stu-id="b1a27-200">**Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software.**</span></span> <span data-ttu-id="b1a27-201">(Książki; zawiera omówienie obiekty wartości) [*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)</span><span class="sxs-lookup"><span data-stu-id="b1a27-201">(Book; includes a discussion of value objects) [*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)</span></span>

-   <span data-ttu-id="b1a27-202">**Vaughn Vernon. Implementowanie projektu opartych na domenie.**</span><span class="sxs-lookup"><span data-stu-id="b1a27-202">**Vaughn Vernon. Implementing Domain-Driven Design.**</span></span> <span data-ttu-id="b1a27-203">(Książki; zawiera omówienie obiekty wartości) [*https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)</span><span class="sxs-lookup"><span data-stu-id="b1a27-203">(Book; includes a discussion of value objects) [*https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)</span></span>

-   <span data-ttu-id="b1a27-204">**Właściwości w tle**
    [*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)</span><span class="sxs-lookup"><span data-stu-id="b1a27-204">**Shadow Properties**
[*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)</span></span>

-   <span data-ttu-id="b1a27-205">**Typy złożone i/lub obiekty wartości**.</span><span class="sxs-lookup"><span data-stu-id="b1a27-205">**Complex types and/or value objects**.</span></span> <span data-ttu-id="b1a27-206">Omówienie w repozytorium EF Core GitHub (karta problemów) [*https://github.com/aspnet/EntityFramework/issues/246*](https://github.com/aspnet/EntityFramework/issues/246)</span><span class="sxs-lookup"><span data-stu-id="b1a27-206">Discussion in the EF Core GitHub repo (Issues tab) [*https://github.com/aspnet/EntityFramework/issues/246*](https://github.com/aspnet/EntityFramework/issues/246)</span></span>

-   <span data-ttu-id="b1a27-207">**ValueObject.cs.**</span><span class="sxs-lookup"><span data-stu-id="b1a27-207">**ValueObject.cs.**</span></span> <span data-ttu-id="b1a27-208">Wartość podstawową klasy obiektów w eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="b1a27-208">Base value object class in eShopOnContainers.</span></span>
    [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs)

-   <span data-ttu-id="b1a27-209">**Klasy adresów.**</span><span class="sxs-lookup"><span data-stu-id="b1a27-209">**Address class.**</span></span> <span data-ttu-id="b1a27-210">Przykładowe wartości klasy obiektów w eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="b1a27-210">Sample value object class in eShopOnContainers.</span></span>
    [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs)



>[!div class="step-by-step"]
<span data-ttu-id="b1a27-211">[Poprzednie] (seedwork-domain-model-base-classes-interfaces.md) [dalej] (wyliczenie klasy over wyliczenia types.md)</span><span class="sxs-lookup"><span data-stu-id="b1a27-211">[Previous] (seedwork-domain-model-base-classes-interfaces.md) [Next] (enumeration-classes-over-enum-types.md)</span></span>

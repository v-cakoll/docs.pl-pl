---
title: Implementowanie obiektów wartości
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Pobierz szczegóły i funkcje umożliwiające implementowanie obiektów wartości przy użyciu nowych funkcji programu Entity Framework.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/08/2018
ms.openlocfilehash: 64ffd600468124439986b0d1949dc048ef245c78
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2019
ms.locfileid: "59611383"
---
# <a name="implement-value-objects"></a><span data-ttu-id="7a9bd-103">Implementowanie obiektów wartości</span><span class="sxs-lookup"><span data-stu-id="7a9bd-103">Implement value objects</span></span>

<span data-ttu-id="7a9bd-104">Zgodnie z opisem we wcześniejszych sekcjach dotyczących jednostek i agregacji, tożsamość ma zasadnicze znaczenie dla jednostki.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-104">As discussed in earlier sections about entities and aggregates, identity is fundamental for entities.</span></span> <span data-ttu-id="7a9bd-105">Istnieją jednak wiele obiektów i elementów danych w systemie, które nie wymagają usługi tożsamości i tożsamości, śledzenie, takie jak obiekty wartości.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-105">However, there are many objects and data items in a system that do not require an identity and identity tracking, such as value objects.</span></span>

<span data-ttu-id="7a9bd-106">Obiekt wartości można odwoływać się do innych jednostek.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-106">A value object can reference other entities.</span></span> <span data-ttu-id="7a9bd-107">Na przykład w aplikacji, która generuje trasę, która opisuje, jak można uzyskać z jednego miejsca do innego tej trasy będzie obiektu wartości.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-107">For example, in an application that generates a route that describes how to get from one point to another, that route would be a value object.</span></span> <span data-ttu-id="7a9bd-108">Byłoby migawek punktów na określoną trasę, ale ta trasa sugerowane nie miałoby tożsamości, mimo że wewnętrznie go, może odnosić się do jednostek, takich jak miasto, drogi itp.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-108">It would be a snapshot of points on a specific route, but this suggested route would not have an identity, even though internally it might refer to entities like City, Road, etc.</span></span>

<span data-ttu-id="7a9bd-109">Rysunek 7-13 przedstawiono obiektu wartość adresu w agregacji zamówienia.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-109">Figure 7-13 shows the Address value object within the Order aggregate.</span></span>

![Wartość adresu — obiekt wewnątrz agregacji zamówienia.](./media/image14.png)

<span data-ttu-id="7a9bd-111">**Rysunek 7-13**.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-111">**Figure 7-13**.</span></span> <span data-ttu-id="7a9bd-112">Adres obiektu wartości w kolejności agregacji</span><span class="sxs-lookup"><span data-stu-id="7a9bd-112">Address value object within the Order aggregate</span></span>

<span data-ttu-id="7a9bd-113">Jak pokazano w rysunek 7-13, jednostki zwykle składa się z wielu atrybutów.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-113">As shown in Figure 7-13, an entity is usually composed of multiple attributes.</span></span> <span data-ttu-id="7a9bd-114">Na przykład `Order` jednostki mogą być modelowane jako jednostki przy użyciu tożsamości i wewnętrznie składa się z zestawu atrybutów, takich jak OrderId OrderDate, OrderItems itp. Ale adresu, który jest po prostu złożone wartością, składa się z kraju, ulicy, Miasto itp. i ma Brak tożsamości w tej domenie, musi być modelowane i traktowane jako obiekt wartości.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-114">For example, the `Order` entity can be modeled as an entity with an identity and composed internally of a set of attributes such as OrderId, OrderDate, OrderItems, etc. But the address, which is simply a complex-value composed of country, street, city, etc. and has no identity in this domain, must be modeled and treated as a value object.</span></span>

## <a name="important-characteristics-of-value-objects"></a><span data-ttu-id="7a9bd-115">Istotne cechy obiektów wartości</span><span class="sxs-lookup"><span data-stu-id="7a9bd-115">Important characteristics of value objects</span></span>

<span data-ttu-id="7a9bd-116">Istnieją dwa główne właściwości dla obiektów wartości:</span><span class="sxs-lookup"><span data-stu-id="7a9bd-116">There are two main characteristics for value objects:</span></span>

- <span data-ttu-id="7a9bd-117">Mają one nie tożsamości.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-117">They have no identity.</span></span>

- <span data-ttu-id="7a9bd-118">Są niezmienne.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-118">They are immutable.</span></span>

<span data-ttu-id="7a9bd-119">Charakterystyka pierwszy już został omówiony.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-119">The first characteristic was already discussed.</span></span> <span data-ttu-id="7a9bd-120">Niezmienność jest ważne wymagania.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-120">Immutability is an important requirement.</span></span> <span data-ttu-id="7a9bd-121">Po utworzeniu obiektu musi być niezmienialne wartości obiektu wartości.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-121">The values of a value object must be immutable once the object is created.</span></span> <span data-ttu-id="7a9bd-122">W związku z tym gdy obiekt jest konstruowany, należy podać wartości wymagane, ale nie muszą umożliwiać mu zmiany w okresie istnienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-122">Therefore, when the object is constructed, you must provide the required values, but you must not allow them to change during the object’s lifetime.</span></span>

<span data-ttu-id="7a9bd-123">Obiekty wartości umożliwiają wykonywanie niektórych wskazówki wydajność dzięki natury niezmienne.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-123">Value objects allow you to perform certain tricks for performance, thanks to their immutable nature.</span></span> <span data-ttu-id="7a9bd-124">Jest to szczególnie istotne w systemach w przypadku, gdy może być tysiące wartości wystąpienia obiektów, z których wiele ma takie same wartości.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-124">This is especially true in systems where there may be thousands of value object instances, many of which have the same values.</span></span> <span data-ttu-id="7a9bd-125">Natury niezmienne umożliwia ich ponowne użycie; wymienne obiekty mogą być ich wartości są takie same, ponieważ mają one nie tożsamości.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-125">Their immutable nature allows them to be reused; they can be interchangeable objects, since their values are the same and they have no identity.</span></span> <span data-ttu-id="7a9bd-126">Tego rodzaju optymalizacji, czasami mogą się przyczynić między oprogramowania, który działa wolno i dobrą wydajność.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-126">This type of optimization can sometimes make a difference between software that runs slowly and software with good performance.</span></span> <span data-ttu-id="7a9bd-127">Oczywiście wszystkich tych przypadkach są zależne od aplikacji środowiska i kontekstu wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-127">Of course, all these cases depend on the application environment and deployment context.</span></span>

## <a name="value-object-implementation-in-c"></a><span data-ttu-id="7a9bd-128">Wartość obiektu wdrożenia w języku C\#</span><span class="sxs-lookup"><span data-stu-id="7a9bd-128">Value object implementation in C\#</span></span>

<span data-ttu-id="7a9bd-129">Pod względem implementacji może mieć klasy podstawowej obiektu wartość, która zawiera podstawowe narzędzia metod, takich jak na podstawie porównania między wszystkie atrybuty (ponieważ jest to obiekt wartości nie muszą być oparte na tożsamości) oraz innych podstawowych charakterystyk równości.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-129">In terms of implementation, you can have a value object base class that has basic utility methods like equality based on comparison between all the attributes (since a value object must not be based on identity) and other fundamental characteristics.</span></span> <span data-ttu-id="7a9bd-130">Poniższy przykład pokazuje wartość obiektu klasy bazowej, używane w szeregowania mikrousługi w ramach aplikacji eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-130">The following example shows a value object base class used in the ordering microservice from eShopOnContainers.</span></span>

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
    // Other utility methods
}
```

<span data-ttu-id="7a9bd-131">Za pomocą tej klasy podczas implementowania rzeczywistej wartości obiektu, jak pokazano w poniższym przykładzie obiekt wartości adresów:</span><span class="sxs-lookup"><span data-stu-id="7a9bd-131">You can use this class when implementing your actual value object, as with the Address value object shown in the following example:</span></span>

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

<span data-ttu-id="7a9bd-132">Możesz zobaczyć, jak ta implementacja obiektu wartość adresu ma, Brak tożsamości, a w związku z tym, żadne pole ID, ani w klasie adres, nawet w klasie ValueObject.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-132">You can see how this value object implementation of Address has no identity and therefore, no ID field, neither at the Address class not even at the ValueObject class.</span></span>

<span data-ttu-id="7a9bd-133">Nie było możliwe o żadne pole Identyfikatora w klasie, który będzie używany przez Entity Framework, dopóki programu EF Core 2.0, co pozwala znacznie lepiej zaimplementować wartość obiekty nie identyfikatorem</span><span class="sxs-lookup"><span data-stu-id="7a9bd-133">Having no ID field in a class to be used by Entity Framework was not possible until EF Core 2.0, which greatly helps to implement better value objects with no ID.</span></span> <span data-ttu-id="7a9bd-134">To dokładnie wyjaśnienie w następnej sekcji.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-134">That is precisely the explanation of the next section.</span></span>

<span data-ttu-id="7a9bd-135">Można utrzymywał, że obiekty wartości, są niezmienne, powinny być tylko do odczytu (czyli get tylko właściwości), i który jest rzeczywiście.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-135">It could be argued that value objects, being immutable, should be read-only (i.e. get-only properties), and that’s indeed true.</span></span> <span data-ttu-id="7a9bd-136">Jednak wartość jest zazwyczaj serializacji i deserializacji za pośrednictwem kolejki komunikatów i jest tylko do odczytu zatrzymuje Deserializator przypisywaniu wartości, więc po prostu pozostawimy je jako zestaw prywatny, który jest tylko do odczytu, wystarczająco przydatne.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-136">However, value objects are usually serialized and deserialized to go through message queues, and being read-only stops the deserializer from assigning values, so we just leave them as private set which is read-only enough to be practical.</span></span>

## <a name="how-to-persist-value-objects-in-the-database-with-ef-core-20"></a><span data-ttu-id="7a9bd-137">Jak zachować wartość obiektów w bazie danych przy użyciu programu EF Core 2.0</span><span class="sxs-lookup"><span data-stu-id="7a9bd-137">How to persist value objects in the database with EF Core 2.0</span></span>

<span data-ttu-id="7a9bd-138">Możesz już wiesz, jak zdefiniować obiekt wartości w modelu domeny.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-138">You just saw how to define a value object in your domain model.</span></span> <span data-ttu-id="7a9bd-139">Ale jak może faktycznie powiedzmy go do bazy danych za pośrednictwem podstawowych Entity Framework (EF), która zwykle jest przeznaczony dla jednostek o tożsamości?</span><span class="sxs-lookup"><span data-stu-id="7a9bd-139">But, how can you actually persist it into the database through Entity Framework (EF) Core which usually targets entities with identity?</span></span>

### <a name="background-and-older-approaches-using-ef-core-11"></a><span data-ttu-id="7a9bd-140">Tło i starszych metod przy użyciu programu EF Core 1.1</span><span class="sxs-lookup"><span data-stu-id="7a9bd-140">Background and older approaches using EF Core 1.1</span></span>

<span data-ttu-id="7a9bd-141">Jako tła, ograniczenie, w przypadku korzystania z programów EF Core 1.0 i 1.1 został może nie używać [typy złożone](xref:System.ComponentModel.DataAnnotations.Schema.ComplexTypeAttribute) zgodnie z definicją w programie EF w tradycyjnych .NET Framework w wersji 6.x.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-141">As background, a limitation when using EF Core 1.0 and 1.1 was that you could not use [complex types](xref:System.ComponentModel.DataAnnotations.Schema.ComplexTypeAttribute) as defined in EF 6.x in the traditional .NET Framework.</span></span> <span data-ttu-id="7a9bd-142">W związku z tym przy użyciu programu EF Core 1.0 i 1.1, potrzebna do przechowywania wartości obiektu jako jednostki EF o pole Identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-142">Therefore, if using EF Core 1.0 or 1.1, you needed to store your value object as an EF entity with an ID field.</span></span> <span data-ttu-id="7a9bd-143">Następnie, dzięki czemu będzie wyglądał bardziej jak obiekt wartości przy użyciu tożsamości nie, można ukryć jego Identyfikatora, dzięki czemu można wyjaśnić, że tożsamość obiektu wartości nie jest ważna w modelu domeny.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-143">Then, so it looked more like a value object with no identity, you could hide its ID so you make clear that the identity of a value object is not important in the domain model.</span></span> <span data-ttu-id="7a9bd-144">Ten identyfikator można ukryć za pomocą Identyfikatora jako [w tle właściwość](https://docs.microsoft.com/ef/core/modeling/shadow-properties ).</span><span class="sxs-lookup"><span data-stu-id="7a9bd-144">You could hide that ID by using the ID as a [shadow property](https://docs.microsoft.com/ef/core/modeling/shadow-properties ).</span></span> <span data-ttu-id="7a9bd-145">Ponieważ ten ukrywania identyfikator modelu jest skonfigurowany na poziomie infrastruktury EF, byłoby rodzaju przezroczyste dla modelu domeny.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-145">Since that configuration for hiding the ID in the model is set up in the EF infrastructure level, it would be kind of transparent for your domain model.</span></span>

<span data-ttu-id="7a9bd-146">W wersji początkowej w ramach aplikacji eShopOnContainers (.NET Core 1.1) identyfikator ukryte wymagane przez infrastrukturę programu EF Core została zaimplementowana w następujący sposób na poziomie kontekstu DbContext przy użyciu interfejsu API Fluent w projekcie infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-146">In the initial version of eShopOnContainers (.NET Core 1.1), the hidden ID needed by EF Core infrastructure was implemented in the following way in the DbContext level, using Fluent API at the infrastructure project.</span></span> <span data-ttu-id="7a9bd-147">W związku z tym identyfikator został ukryty z punktu widzenia modelu domeny, ale nadal znajdują się w ramach infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-147">Therefore, the ID was hidden from the domain model point of view, but still present in the infrastructure.</span></span>

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

<span data-ttu-id="7a9bd-148">Jednak trwałości wartość obiektu do bazy danych została wykonana jak regularne jednostki w innej tabeli.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-148">However, the persistence of that value object into the database was performed like a regular entity in a different table.</span></span>

<span data-ttu-id="7a9bd-149">Przy użyciu programu EF Core 2.0, są nowe i lepsze sposoby utrwalania obiektów wartości.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-149">With EF Core 2.0, there are new and better ways to persist value objects.</span></span>

## <a name="persist-value-objects-as-owned-entity-types-in-ef-core-20"></a><span data-ttu-id="7a9bd-150">Utrwalanie obiekty wartości jako posiadane typy jednostek w programie EF Core 2.0</span><span class="sxs-lookup"><span data-stu-id="7a9bd-150">Persist value objects as owned entity types in EF Core 2.0</span></span>

<span data-ttu-id="7a9bd-151">Nawet w przypadku niektórych luki między wzorzec object canonical wartość w DDD i typ jednostki należące do firmy w wersji EF Core jest obecnie najlepszym sposobem, aby utrwalić obiekty wartości przy użyciu programu EF Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-151">Even with some gaps between the canonical value object pattern in DDD and the owned entity type in EF Core, it's currently the best way to persist value objects with EF Core 2.0.</span></span> <span data-ttu-id="7a9bd-152">Możesz zobaczyć ograniczenia na końcu tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-152">You can see limitations at the end of this section.</span></span>

<span data-ttu-id="7a9bd-153">Funkcja Typ jednostki należące do firmy został dodany do programu EF Core od wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-153">The owned entity type feature was added to EF Core since version 2.0.</span></span>

<span data-ttu-id="7a9bd-154">Typ jednostki należące do firmy umożliwia mapowanie typów, które nie mają własnej tożsamości jawnie zdefiniowany w modelu domeny i są używane jako właściwości, takie jak obiekt wartości w ramach danej jednostki.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-154">An owned entity type allows you to map types that do not have their own identity explicitly defined in the domain model and are used as properties, such as a value object, within any of your entities.</span></span> <span data-ttu-id="7a9bd-155">Typ jednostki należące do firmy udostępni inny typ jednostki tego samego typu CLR (czyli jest zwykłej klasy).</span><span class="sxs-lookup"><span data-stu-id="7a9bd-155">An owned entity type shares the same CLR type with another entity type (that is, it’s just a regular class).</span></span> <span data-ttu-id="7a9bd-156">Obiekt zawierający definiujące nawigacji to jednostka właściciela.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-156">The entity containing the defining navigation is the owner entity.</span></span> <span data-ttu-id="7a9bd-157">Podczas wykonywania zapytania właściciela, typy należące do firmy są domyślnie dołączone.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-157">When querying the owner, the owned types are included by default.</span></span>

<span data-ttu-id="7a9bd-158">Po prostu patrząc na model domeny, typem należące do firmy wygląda na to nie ma żadnych tożsamości.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-158">Just by looking at the domain model, an owned type looks like it doesn’t have any identity.</span></span> <span data-ttu-id="7a9bd-159">Jednak dzieje się w tle, posiadane typy mają tożsamości, ale właściwość nawigacji właściciel jest częścią tej tożsamości.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-159">However, under the covers, owned types do have identity, but the owner navigation property is part of this identity.</span></span>

<span data-ttu-id="7a9bd-160">Tożsamość wystąpień typów należące do firmy, nie jest całkowicie swoje własne.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-160">The identity of instances of owned types is not completely their own.</span></span> <span data-ttu-id="7a9bd-161">Składa się z trzech składników:</span><span class="sxs-lookup"><span data-stu-id="7a9bd-161">It consists of three components:</span></span>

- <span data-ttu-id="7a9bd-162">Tożsamość właściciela</span><span class="sxs-lookup"><span data-stu-id="7a9bd-162">The identity of the owner</span></span>

- <span data-ttu-id="7a9bd-163">Właściwość nawigacji, wskazując je</span><span class="sxs-lookup"><span data-stu-id="7a9bd-163">The navigation property pointing to them</span></span>

- <span data-ttu-id="7a9bd-164">W przypadku kolekcji typów będących własnością, niezależnie od składnika (nie są jeszcze obsługiwane w programie EF Core 2.0, pojawi się na 2.2).</span><span class="sxs-lookup"><span data-stu-id="7a9bd-164">In the case of collections of owned types, an independent component (not yet supported in EF Core 2.0, coming up on 2.2).</span></span>

<span data-ttu-id="7a9bd-165">Na przykład w modelu domeny porządkowanie w ramach aplikacji eShopOnContainers jednostce zamówienia w ramach obiektu wartość adresu jest implementowany jako typ jednostki należące do firmy w ramach jednostki właściciela, czyli jednostki zamówienia.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-165">For example, in the Ordering domain model at eShopOnContainers, as part of the Order entity, the Address value object is implemented as an owned entity type within the owner entity, which is the Order entity.</span></span> <span data-ttu-id="7a9bd-166">Adres jest typu z żadnej właściwości tożsamości zdefiniowanych w modelu domeny.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-166">Address is a type with no identity property defined in the domain model.</span></span> <span data-ttu-id="7a9bd-167">Aby określić adres wysyłkowy dla określonej kolejności służy jako właściwość typu zamówienia.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-167">It is used as a property of the Order type to specify the shipping address for a particular order.</span></span>

<span data-ttu-id="7a9bd-168">Zgodnie z Konwencją klucz podstawowy w tle jest tworzony dla typu należące do firmy i będzie można zamapować na tej samej tabeli jako właściciel przy użyciu dzielenie tabeli.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-168">By convention, a shadow primary key is created for the owned type and it will be mapped to the same table as the owner by using table splitting.</span></span> <span data-ttu-id="7a9bd-169">Dzięki temu Użyj należące do typów podobnie jak złożonych typów są używane w EF6 tradycyjnych .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-169">This allows to use owned types similarly to how complex types are used in EF6 in the traditional .NET Framework.</span></span>

<span data-ttu-id="7a9bd-170">Należy pamiętać, że że należące do typów nigdy nie są wykrywane przez Konwencję w programie EF Core, więc trzeba je zadeklarować jawnie.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-170">It is important to note that owned types are never discovered by convention in EF Core, so you have to declare them explicitly.</span></span>

<span data-ttu-id="7a9bd-171">W ramach aplikacji eShopOnContainers u OrderingContext.cs, w metodzie OnModelCreating() istnieje wiele konfiguracji infrastruktury, które są stosowane.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-171">In eShopOnContainers, at the OrderingContext.cs, within the OnModelCreating() method, there are multiple infrastructure configuration being applied.</span></span> <span data-ttu-id="7a9bd-172">Jeden z nich jest powiązany z jednostką zamówienia.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-172">One of them is related to the Order entity.</span></span>

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

<span data-ttu-id="7a9bd-173">W poniższym kodzie infrastruktury trwałości jest zdefiniowany dla jednostki zamówienia:</span><span class="sxs-lookup"><span data-stu-id="7a9bd-173">In the following code, the persistence infrastructure is defined for the Order entity:</span></span>

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

<span data-ttu-id="7a9bd-174">W poprzednim kodzie `orderConfiguration.OwnsOne(o => o.Address)` Metoda określa, że `Address` właściwość jest własnością jednostki `Order` typu.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-174">In the previous code, the `orderConfiguration.OwnsOne(o => o.Address)` method specifies that the `Address` property is an owned entity of the `Order` type.</span></span>

<span data-ttu-id="7a9bd-175">Domyślnie, konwencje programu EF Core nazwę kolumny bazy danych dla właściwości typu jednostki należące do firmy, co `EntityProperty_OwnedEntityProperty`.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-175">By default, EF Core conventions name the database columns for the properties of the owned entity type as `EntityProperty_OwnedEntityProperty`.</span></span> <span data-ttu-id="7a9bd-176">W związku z tym, wewnętrzny właściwości `Address` pojawi się w `Orders` tabel o nazwach `Address_Street`, `Address_City` (i tak dalej dla `State`, `Country` i `ZipCode`).</span><span class="sxs-lookup"><span data-stu-id="7a9bd-176">Therefore, the internal properties of `Address` will appear in the `Orders` table with the names `Address_Street`, `Address_City` (and so on for `State`, `Country` and `ZipCode`).</span></span>

<span data-ttu-id="7a9bd-177">Możesz dołączyć `Property().HasColumnName()` fluent metodę, aby zmienić nazwę kolumny.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-177">You can append the `Property().HasColumnName()` fluent method to rename those columns.</span></span> <span data-ttu-id="7a9bd-178">W przypadku których `Address` jest właściwością publiczną mapowania będzie następujący:</span><span class="sxs-lookup"><span data-stu-id="7a9bd-178">In the case where `Address` is a public property, the mappings would be like the following:</span></span>

```csharp
orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.Street).HasColumnName("ShippingStreet");

orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.City).HasColumnName("ShippingCity");
```

<span data-ttu-id="7a9bd-179">Istnieje możliwość łańcucha `OwnsOne` metody w mapowaniu fluent.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-179">It is possible to chain the `OwnsOne` method in a fluent mapping.</span></span> <span data-ttu-id="7a9bd-180">W poniższym przykładzie hipotetyczny `OrderDetails` właścicielem `BillingAddress` i `ShippingAddress`, które są zarówno `Address` typów.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-180">In the following hypothetical example, `OrderDetails` owns `BillingAddress` and `ShippingAddress`, which are both `Address` types.</span></span> <span data-ttu-id="7a9bd-181">Następnie `OrderDetails` jest własnością `Order` typu.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-181">Then `OrderDetails` is owned by the `Order` type.</span></span>

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

### <a name="additional-details-on-owned-entity-types"></a><span data-ttu-id="7a9bd-182">Więcej informacji na temat posiadane typy jednostek</span><span class="sxs-lookup"><span data-stu-id="7a9bd-182">Additional details on owned entity types</span></span>

- <span data-ttu-id="7a9bd-183">Posiadane typy są definiowane podczas konfigurowania właściwości nawigacji do określonego typu przy użyciu interfejsu API fluent OwnsOne.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-183">Owned types are defined when you configure a navigation property to a particular type using the OwnsOne fluent API.</span></span>

- <span data-ttu-id="7a9bd-184">Definicja typu należące do firmy w naszym modelu metadanych jest złożone z: Typ właściciela, właściwość nawigacji i typ CLR tego typu należące do firmy.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-184">The definition of an owned type in our metadata model is a composite of: the owner type, the navigation property, and the CLR type of the owned type.</span></span>

- <span data-ttu-id="7a9bd-185">Tożsamość (klucz) wystąpienia typu należących do naszego stosu jest złożone tożsamości typu właściciela i definicji typu należące do firmy.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-185">The identity (key) of an owned type instance in our stack is a composite of the identity of the owner type and the definition of the owned type.</span></span>

#### <a name="owned-entities-capabilities"></a><span data-ttu-id="7a9bd-186">Funkcje jednostki należące do firmy:</span><span class="sxs-lookup"><span data-stu-id="7a9bd-186">Owned entities capabilities:</span></span>

- <span data-ttu-id="7a9bd-187">Posiadane typy mogą odwoływać się inne jednostki, albo właścicielem (zagnieżdżone typy należące do firmy) lub należących do firmy (właściwości nawigacji regularne odwołania do innych jednostek).</span><span class="sxs-lookup"><span data-stu-id="7a9bd-187">Owned types can reference other entities, either owned (nested owned types) or non-owned (regular reference navigation properties to other entities).</span></span>

- <span data-ttu-id="7a9bd-188">Można mapować tego samego typu CLR jako różne typy należące do firmy w tej samej jednostki właściciel za pośrednictwem właściwości nawigacji oddzielne.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-188">You can map the same CLR type as different owned types in the same owner entity through separate navigation properties.</span></span>

- <span data-ttu-id="7a9bd-189">Dzielenie tabeli została skonfigurowana zgodnie z Konwencją, ale możesz zrezygnować z przez mapowanie typu należące do innej tabeli przy użyciu ToTable.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-189">Table splitting is setup by convention, but you can opt out by mapping the owned type to a different table using ToTable.</span></span>

- <span data-ttu-id="7a9bd-190">Wczesne ładowanie odbywa się automatycznie w typach należące do firmy, czyli nie trzeba wywoływać include() — na tym zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-190">Eager loading is performed automatically on owned types, i.e. no need to call Include() on the query.</span></span>

- <span data-ttu-id="7a9bd-191">Można skonfigurować za pomocą atrybutu \[posiadane\], zgodnie z programem EF Core 2.1</span><span class="sxs-lookup"><span data-stu-id="7a9bd-191">Can be configured with attribute \[Owned\], as of EF Core 2.1</span></span>

#### <a name="owned-entities-limitations"></a><span data-ttu-id="7a9bd-192">Ograniczenia jednostki należące do firmy:</span><span class="sxs-lookup"><span data-stu-id="7a9bd-192">Owned entities limitations:</span></span>

- <span data-ttu-id="7a9bd-193">Nie można utworzyć DbSet\<T\> typu należące do firmy (według projektu).</span><span class="sxs-lookup"><span data-stu-id="7a9bd-193">You cannot create a DbSet\<T\> of an owned type (by design).</span></span>

- <span data-ttu-id="7a9bd-194">Nie można wywołać ModelBuilder.Entity\<T\>() dla typów należące do firmy (obecnie według projektu).</span><span class="sxs-lookup"><span data-stu-id="7a9bd-194">You cannot call ModelBuilder.Entity\<T\>() on owned types (currently by design).</span></span>

- <span data-ttu-id="7a9bd-195">Nie kolekcji typów będących własnością jeszcze (począwszy od programu EF Core 2.1, ale będą obsługiwane w 2.2).</span><span class="sxs-lookup"><span data-stu-id="7a9bd-195">No collections of owned types yet (as of EF Core 2.1, but they will be supported in 2.2).</span></span>

- <span data-ttu-id="7a9bd-196">Brak obsługi opcjonalne (oznacza to, dopuszczającego wartość null) należące do typów, które są mapowane z właścicielem w tej samej tabeli (np. za pomocą dzielenia tabeli).</span><span class="sxs-lookup"><span data-stu-id="7a9bd-196">No support for optional (that is, nullable) owned types that are mapped with the owner in the same table (i.e. using table splitting).</span></span> <span data-ttu-id="7a9bd-197">Jest to spowodowane mapowanie jest wykonywane dla każdej właściwości, nie mamy oddzielne wartownik zawiera wartości null dla złożonych jako całego.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-197">This is because mapping is done for each property, we don't have a separate sentinel for the null complex value a as whole.</span></span>

- <span data-ttu-id="7a9bd-198">Brak obsługi mapowania dziedziczenia należące do typów, ale powinno być możliwe do mapowania dwa typy tej samej hierarchii dziedziczenia w jako należących do różnego typu liść.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-198">No inheritance mapping support for owned types, but you should be able to map two leaf types of the same inheritance hierarchies as different owned types.</span></span> <span data-ttu-id="7a9bd-199">EF Core nie będzie przyczyny o tym, że są one częścią tej samej hierarchii.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-199">EF Core will not reason about the fact that they are part of the same hierarchy.</span></span>

#### <a name="main-differences-with-ef6s-complex-types"></a><span data-ttu-id="7a9bd-200">Główne różnice przy użyciu platformy EF6 dla typów złożonych</span><span class="sxs-lookup"><span data-stu-id="7a9bd-200">Main differences with EF6's complex types</span></span>

- <span data-ttu-id="7a9bd-201">Dzielenie tabeli jest opcjonalne, czyli opcjonalnie mogą zostać zmapowane do osobnej tabeli i nadal należeć do typów.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-201">Table splitting is optional, i.e. they can optionally be mapped to a separate table and still be owned types.</span></span>

- <span data-ttu-id="7a9bd-202">Mogą odwoływać się do innych jednostek (czyli mogą pełnić zależne side w relacji z innymi typami należących do firmy).</span><span class="sxs-lookup"><span data-stu-id="7a9bd-202">They can reference other entities (i.e. they can act as the dependent side on relationships to other non-owned types).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="7a9bd-203">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="7a9bd-203">Additional resources</span></span>

- <span data-ttu-id="7a9bd-204">**Martin Fowler. Wzorzec ValueObject** \\</span><span class="sxs-lookup"><span data-stu-id="7a9bd-204">**Martin Fowler. ValueObject pattern** \\</span></span>
  <https://martinfowler.com/bliki/ValueObject.html>

- <span data-ttu-id="7a9bd-205">**Eric Evans. Projektowania opartego na domenie: Co dzień do czynienia złożoności serce oprogramowania.**</span><span class="sxs-lookup"><span data-stu-id="7a9bd-205">**Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software.**</span></span> <span data-ttu-id="7a9bd-206">(Zarezerwuj; zawiera omówienie obiekty wartości) \\</span><span class="sxs-lookup"><span data-stu-id="7a9bd-206">(Book; includes a discussion of value objects) \\</span></span>
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

- <span data-ttu-id="7a9bd-207">**Vaughn Vernon. Implementowanie projektu opartego na domenach.**</span><span class="sxs-lookup"><span data-stu-id="7a9bd-207">**Vaughn Vernon. Implementing Domain-Driven Design.**</span></span> <span data-ttu-id="7a9bd-208">(Zarezerwuj; zawiera omówienie obiekty wartości) \\</span><span class="sxs-lookup"><span data-stu-id="7a9bd-208">(Book; includes a discussion of value objects) \\</span></span>
  <https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/>

- <span data-ttu-id="7a9bd-209">**Właściwości w tle** \\</span><span class="sxs-lookup"><span data-stu-id="7a9bd-209">**Shadow Properties** \\</span></span>
  [https://docs.microsoft.com/ef/core/modeling/shadow-properties](/ef/core/modeling/shadow-properties)

- <span data-ttu-id="7a9bd-210">**Typy złożone i/lub obiekty wartości**.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-210">**Complex types and/or value objects**.</span></span> <span data-ttu-id="7a9bd-211">Dyskusja w repozytorium programu EF Core w witrynie GitHub (karta problemy) \\</span><span class="sxs-lookup"><span data-stu-id="7a9bd-211">Discussion in the EF Core GitHub repo (Issues tab) \\</span></span>
  <https://github.com/aspnet/EntityFramework/issues/246>

- <span data-ttu-id="7a9bd-212">**ValueObject.cs.**</span><span class="sxs-lookup"><span data-stu-id="7a9bd-212">**ValueObject.cs.**</span></span> <span data-ttu-id="7a9bd-213">Podstawowa klasa obiektu wartości w eShopOnContainers.* * \\</span><span class="sxs-lookup"><span data-stu-id="7a9bd-213">Base value object class in eShopOnContainers.**  \\</span></span>
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs>

- <span data-ttu-id="7a9bd-214">**Klasy adresów.**</span><span class="sxs-lookup"><span data-stu-id="7a9bd-214">**Address class.**</span></span> <span data-ttu-id="7a9bd-215">Klasa obiektu wartość próbki w ramach aplikacji eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="7a9bd-215">Sample value object class in eShopOnContainers.</span></span> \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs>

> [!div class="step-by-step"]
> <span data-ttu-id="7a9bd-216">[Poprzednie](seedwork-domain-model-base-classes-interfaces.md)
> [dalej](enumeration-classes-over-enum-types.md)</span><span class="sxs-lookup"><span data-stu-id="7a9bd-216">[Previous](seedwork-domain-model-base-classes-interfaces.md)
[Next](enumeration-classes-over-enum-types.md)</span></span>

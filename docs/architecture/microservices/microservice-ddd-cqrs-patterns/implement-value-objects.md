---
title: Implementowanie obiektów wartości
description: Architektura mikrousług .NET dla konteneryzowanych aplikacji .NET | Zapoznaj się ze szczegółami i opcjami implementowania obiektów wartości przy użyciu nowych funkcji entity framework.
ms.date: 01/30/2020
ms.openlocfilehash: 4ace5c141b1cbd2dcfefb7ea7165a4006b130479
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77502516"
---
# <a name="implement-value-objects"></a><span data-ttu-id="67c3d-103">Implementowanie obiektów wartości</span><span class="sxs-lookup"><span data-stu-id="67c3d-103">Implement value objects</span></span>

<span data-ttu-id="67c3d-104">Jak wspomniano we wcześniejszych sekcjach dotyczących jednostek i agregacji, tożsamość jest podstawowa dla jednostek.</span><span class="sxs-lookup"><span data-stu-id="67c3d-104">As discussed in earlier sections about entities and aggregates, identity is fundamental for entities.</span></span> <span data-ttu-id="67c3d-105">Jednak istnieje wiele obiektów i elementów danych w systemie, które nie wymagają śledzenia tożsamości i tożsamości, takich jak obiekty wartości.</span><span class="sxs-lookup"><span data-stu-id="67c3d-105">However, there are many objects and data items in a system that do not require an identity and identity tracking, such as value objects.</span></span>

<span data-ttu-id="67c3d-106">Obiekt wartości może odwoływać się do innych jednostek.</span><span class="sxs-lookup"><span data-stu-id="67c3d-106">A value object can reference other entities.</span></span> <span data-ttu-id="67c3d-107">Na przykład w aplikacji, która generuje trasę, która opisuje, jak uzyskać z jednego punktu do drugiego, że trasa będzie obiektwartości.</span><span class="sxs-lookup"><span data-stu-id="67c3d-107">For example, in an application that generates a route that describes how to get from one point to another, that route would be a value object.</span></span> <span data-ttu-id="67c3d-108">Byłaby to migawka punktów na określonej trasie, ale ta sugerowana trasa nie miałaby tożsamości, mimo że wewnętrznie może odnosić się do podmiotów takich jak Miasto, Droga itp.</span><span class="sxs-lookup"><span data-stu-id="67c3d-108">It would be a snapshot of points on a specific route, but this suggested route would not have an identity, even though internally it might refer to entities like City, Road, etc.</span></span>

<span data-ttu-id="67c3d-109">Rysunek 7-13 przedstawia obiekt wartość address w zagregowanym zagregowanym zamówieniu.</span><span class="sxs-lookup"><span data-stu-id="67c3d-109">Figure 7-13 shows the Address value object within the Order aggregate.</span></span>

![Diagram przedstawiający adres wartość-obiekt wewnątrz zagregowane zamówienia.](./media/implement-value-objects/value-object-within-aggregate.png)

<span data-ttu-id="67c3d-111">**Rysunek 7-13**.</span><span class="sxs-lookup"><span data-stu-id="67c3d-111">**Figure 7-13**.</span></span> <span data-ttu-id="67c3d-112">Obiekt wartości adresu w zagregowanym zagregowanym zamówieniu</span><span class="sxs-lookup"><span data-stu-id="67c3d-112">Address value object within the Order aggregate</span></span>

<span data-ttu-id="67c3d-113">Jak pokazano na rysunku 7-13, jednostka składa się zwykle z wielu atrybutów.</span><span class="sxs-lookup"><span data-stu-id="67c3d-113">As shown in Figure 7-13, an entity is usually composed of multiple attributes.</span></span> <span data-ttu-id="67c3d-114">Na przykład `Order` jednostka może być modelowana jako jednostka z tożsamością i składa się wewnętrznie z zestawu atrybutów, takich jak OrderId, OrderDate, OrderItems itp. Ale adres, który jest po prostu złożoną wartością składającą się z kraju/regionu, ulicy, miasta itp.</span><span class="sxs-lookup"><span data-stu-id="67c3d-114">For example, the `Order` entity can be modeled as an entity with an identity and composed internally of a set of attributes such as OrderId, OrderDate, OrderItems, etc. But the address, which is simply a complex-value composed of country/region, street, city, etc. and has no identity in this domain, must be modeled and treated as a value object.</span></span>

## <a name="important-characteristics-of-value-objects"></a><span data-ttu-id="67c3d-115">Ważne cechy obiektów wartości</span><span class="sxs-lookup"><span data-stu-id="67c3d-115">Important characteristics of value objects</span></span>

<span data-ttu-id="67c3d-116">Istnieją dwie główne cechy obiektów wartości:</span><span class="sxs-lookup"><span data-stu-id="67c3d-116">There are two main characteristics for value objects:</span></span>

- <span data-ttu-id="67c3d-117">Nie mają tożsamości.</span><span class="sxs-lookup"><span data-stu-id="67c3d-117">They have no identity.</span></span>

- <span data-ttu-id="67c3d-118">Są niezmienne.</span><span class="sxs-lookup"><span data-stu-id="67c3d-118">They are immutable.</span></span>

<span data-ttu-id="67c3d-119">Pierwsza cecha została już omówiona.</span><span class="sxs-lookup"><span data-stu-id="67c3d-119">The first characteristic was already discussed.</span></span> <span data-ttu-id="67c3d-120">Niezmienność jest ważnym wymogiem.</span><span class="sxs-lookup"><span data-stu-id="67c3d-120">Immutability is an important requirement.</span></span> <span data-ttu-id="67c3d-121">Wartości obiektu wartości muszą być niezmienne po utworzeniu obiektu.</span><span class="sxs-lookup"><span data-stu-id="67c3d-121">The values of a value object must be immutable once the object is created.</span></span> <span data-ttu-id="67c3d-122">W związku z tym, gdy obiekt jest konstruowany, należy podać wymagane wartości, ale nie należy zezwalać na ich zmiany w okresie istnienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="67c3d-122">Therefore, when the object is constructed, you must provide the required values, but you must not allow them to change during the object’s lifetime.</span></span>

<span data-ttu-id="67c3d-123">Value obiektów pozwalają na wykonywanie pewnych sztuczek dla wydajności, dzięki ich niezmiennecharakter.</span><span class="sxs-lookup"><span data-stu-id="67c3d-123">Value objects allow you to perform certain tricks for performance, thanks to their immutable nature.</span></span> <span data-ttu-id="67c3d-124">Jest to szczególnie prawdziwe w systemach, w których mogą istnieć tysiące wystąpień obiektu wartości, z których wiele ma te same wartości.</span><span class="sxs-lookup"><span data-stu-id="67c3d-124">This is especially true in systems where there may be thousands of value object instances, many of which have the same values.</span></span> <span data-ttu-id="67c3d-125">Ich niezmienna natura pozwala na ich ponowne wykorzystania; mogą być wymienne obiekty, ponieważ ich wartości są takie same i nie mają tożsamości.</span><span class="sxs-lookup"><span data-stu-id="67c3d-125">Their immutable nature allows them to be reused; they can be interchangeable objects, since their values are the same and they have no identity.</span></span> <span data-ttu-id="67c3d-126">Ten typ optymalizacji może czasami zrobić różnicę między oprogramowaniem, które działa wolno, a oprogramowaniem o dobrej wydajności.</span><span class="sxs-lookup"><span data-stu-id="67c3d-126">This type of optimization can sometimes make a difference between software that runs slowly and software with good performance.</span></span> <span data-ttu-id="67c3d-127">Oczywiście wszystkie te przypadki zależą od środowiska aplikacji i kontekstu wdrażania.</span><span class="sxs-lookup"><span data-stu-id="67c3d-127">Of course, all these cases depend on the application environment and deployment context.</span></span>

## <a name="value-object-implementation-in-c"></a><span data-ttu-id="67c3d-128">Implementacja obiektu wartości w C\#</span><span class="sxs-lookup"><span data-stu-id="67c3d-128">Value object implementation in C\#</span></span>

<span data-ttu-id="67c3d-129">Pod względem implementacji może mieć wartość obiektu klasy podstawowej, która ma podstawowe metody narzędzia, takie jak równość na podstawie porównania między wszystkimi atrybutami (ponieważ obiekt wartości nie może być oparty na tożsamości) i inne podstawowe cechy.</span><span class="sxs-lookup"><span data-stu-id="67c3d-129">In terms of implementation, you can have a value object base class that has basic utility methods like equality based on comparison between all the attributes (since a value object must not be based on identity) and other fundamental characteristics.</span></span> <span data-ttu-id="67c3d-130">W poniższym przykładzie przedstawiono wartość obiektu klasy podstawowej używane w mikrousługi porządkowania z eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="67c3d-130">The following example shows a value object base class used in the ordering microservice from eShopOnContainers.</span></span>

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

<span data-ttu-id="67c3d-131">Tej klasy można użyć podczas implementowania obiektu wartości rzeczywistej, tak jak w przypadku obiektu wartości Address przedstawionego w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="67c3d-131">You can use this class when implementing your actual value object, as with the Address value object shown in the following example:</span></span>

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

<span data-ttu-id="67c3d-132">Można zobaczyć, jak ta implementacja obiektu wartości Address nie ma tożsamości i dlatego nie ma pola identyfikatora, ani w Address klasy nawet w ValueObject klasy.</span><span class="sxs-lookup"><span data-stu-id="67c3d-132">You can see how this value object implementation of Address has no identity and therefore, no ID field, neither at the Address class not even at the ValueObject class.</span></span>

<span data-ttu-id="67c3d-133">Posiadanie pola identyfikatora w klasie, które ma być używane przez entity framework (EF) nie było możliwe, dopóki EF Core 2.0, co znacznie pomaga zaimplementować obiekty o lepszej wartości bez identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="67c3d-133">Having no ID field in a class to be used by Entity Framework (EF) was not possible until EF Core 2.0, which greatly helps to implement better value objects with no ID.</span></span> <span data-ttu-id="67c3d-134">To jest właśnie wyjaśnienie następnej sekcji.</span><span class="sxs-lookup"><span data-stu-id="67c3d-134">That is precisely the explanation of the next section.</span></span>

<span data-ttu-id="67c3d-135">Można argumentować, że obiekty wartości, jest niezmienny, powinny być tylko do odczytu (to znaczy mają właściwości get-only), i to jest rzeczywiście prawda.</span><span class="sxs-lookup"><span data-stu-id="67c3d-135">It could be argued that value objects, being immutable, should be read-only (that is, have get-only properties), and that’s indeed true.</span></span> <span data-ttu-id="67c3d-136">Jednak obiekty wartości są zwykle serializowane i deserializowane, aby przejść przez kolejki komunikatów, a jest tylko do odczytu zatrzymuje deserializator a przypisywanie wartości, więc po prostu pozostawić je jako zestaw prywatny, który jest tylko do odczytu wystarczy, aby być praktyczne.</span><span class="sxs-lookup"><span data-stu-id="67c3d-136">However, value objects are usually serialized and deserialized to go through message queues, and being read-only stops the deserializer from assigning values, so we just leave them as private set which is read-only enough to be practical.</span></span>

## <a name="how-to-persist-value-objects-in-the-database-with-ef-core-20-and-later"></a><span data-ttu-id="67c3d-137">Jak utrwalić obiekty wartości w bazie danych z EF Core 2.0 i nowszych</span><span class="sxs-lookup"><span data-stu-id="67c3d-137">How to persist value objects in the database with EF Core 2.0 and later</span></span>

<span data-ttu-id="67c3d-138">Właśnie zobaczyłeś, jak zdefiniować obiekt wartości w modelu domeny.</span><span class="sxs-lookup"><span data-stu-id="67c3d-138">You just saw how to define a value object in your domain model.</span></span> <span data-ttu-id="67c3d-139">Ale jak można faktycznie utrwalić go do bazy danych przy użyciu entity framework core, ponieważ zwykle dotyczy jednostek z tożsamością?</span><span class="sxs-lookup"><span data-stu-id="67c3d-139">But how can you actually persist it into the database using Entity Framework Core since it usually targets entities with identity?</span></span>

### <a name="background-and-older-approaches-using-ef-core-11"></a><span data-ttu-id="67c3d-140">Podstawowe i starsze podejścia przy użyciu ef core 1.1</span><span class="sxs-lookup"><span data-stu-id="67c3d-140">Background and older approaches using EF Core 1.1</span></span>

<span data-ttu-id="67c3d-141">Jako tło, ograniczenie podczas korzystania z EF Core 1.0 i 1.1 było to, że nie można użyć [typów złożonych,](xref:System.ComponentModel.DataAnnotations.Schema.ComplexTypeAttribute) zgodnie z definicją w EF 6.x w tradycyjnej platformie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="67c3d-141">As background, a limitation when using EF Core 1.0 and 1.1 was that you could not use [complex types](xref:System.ComponentModel.DataAnnotations.Schema.ComplexTypeAttribute) as defined in EF 6.x in the traditional .NET Framework.</span></span> <span data-ttu-id="67c3d-142">W związku z tym w przypadku korzystania z EF Core 1.0 lub 1.1, należy przechowywać obiekt wartości jako jednostki EF z polem identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="67c3d-142">Therefore, if using EF Core 1.0 or 1.1, you needed to store your value object as an EF entity with an ID field.</span></span> <span data-ttu-id="67c3d-143">Następnie, więc wyglądał bardziej jak obiekt wartości bez tożsamości, można ukryć jego identyfikator, dzięki czemu można wyjaśnić, że tożsamość obiektu wartości nie jest ważne w modelu domeny.</span><span class="sxs-lookup"><span data-stu-id="67c3d-143">Then, so it looked more like a value object with no identity, you could hide its ID so you make clear that the identity of a value object is not important in the domain model.</span></span> <span data-ttu-id="67c3d-144">Można ukryć ten identyfikator przy użyciu identyfikatora jako [właściwości cienia](https://docs.microsoft.com/ef/core/modeling/shadow-properties ).</span><span class="sxs-lookup"><span data-stu-id="67c3d-144">You could hide that ID by using the ID as a [shadow property](https://docs.microsoft.com/ef/core/modeling/shadow-properties ).</span></span> <span data-ttu-id="67c3d-145">Ponieważ ta konfiguracja do ukrywania identyfikatora w modelu jest skonfigurowana na poziomie infrastruktury EF, byłoby to rodzaj przezroczyste dla modelu domeny.</span><span class="sxs-lookup"><span data-stu-id="67c3d-145">Since that configuration for hiding the ID in the model is set up in the EF infrastructure level, it would be kind of transparent for your domain model.</span></span>

<span data-ttu-id="67c3d-146">W początkowej wersji eShopOnContainers (.NET Core 1.1) ukryty identyfikator wymagany przez infrastrukturę EF Core został zaimplementowany w następujący sposób na poziomie DbContext przy użyciu interfejsu API Fluent w projekcie infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="67c3d-146">In the initial version of eShopOnContainers (.NET Core 1.1), the hidden ID needed by EF Core infrastructure was implemented in the following way in the DbContext level, using Fluent API at the infrastructure project.</span></span> <span data-ttu-id="67c3d-147">W związku z tym identyfikator został ukryty z punktu widzenia modelu domeny, ale nadal obecne w infrastrukturze.</span><span class="sxs-lookup"><span data-stu-id="67c3d-147">Therefore, the ID was hidden from the domain model point of view, but still present in the infrastructure.</span></span>

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

<span data-ttu-id="67c3d-148">Jednak trwałość tego obiektu wartości do bazy danych została wykonana jak zwykły jednostki w innej tabeli.</span><span class="sxs-lookup"><span data-stu-id="67c3d-148">However, the persistence of that value object into the database was performed like a regular entity in a different table.</span></span>

<span data-ttu-id="67c3d-149">Z EF Core 2.0 i nowszych, istnieją nowe i lepsze sposoby utrwalić wartości obiektów.</span><span class="sxs-lookup"><span data-stu-id="67c3d-149">With EF Core 2.0 and later, there are new and better ways to persist value objects.</span></span>

## <a name="persist-value-objects-as-owned-entity-types-in-ef-core-20-and-later"></a><span data-ttu-id="67c3d-150">Utrwalić obiekty wartości jako typy jednostek należących do EF Core 2.0 i nowszych</span><span class="sxs-lookup"><span data-stu-id="67c3d-150">Persist value objects as owned entity types in EF Core 2.0 and later</span></span>

<span data-ttu-id="67c3d-151">Nawet w niektórych odstępach między wzorzec obiektu wartości kanonicznej w DDD i typu jednostki własnością w EF Core, jest obecnie najlepszym sposobem, aby utrwalić wartości obiektów z EF Core 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="67c3d-151">Even with some gaps between the canonical value object pattern in DDD and the owned entity type in EF Core, it's currently the best way to persist value objects with EF Core 2.0 and later.</span></span> <span data-ttu-id="67c3d-152">Możesz zobaczyć ograniczenia na końcu tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="67c3d-152">You can see limitations at the end of this section.</span></span>

<span data-ttu-id="67c3d-153">Funkcja typu jednostki własnością został dodany do EF Core od wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="67c3d-153">The owned entity type feature was added to EF Core since version 2.0.</span></span>

<span data-ttu-id="67c3d-154">Typ jednostki własnością umożliwia mapowanie typów, które nie mają własnej tożsamości jawnie zdefiniowane w modelu domeny i są używane jako właściwości, takie jak obiekt wartości, w dowolnej jednostce.</span><span class="sxs-lookup"><span data-stu-id="67c3d-154">An owned entity type allows you to map types that do not have their own identity explicitly defined in the domain model and are used as properties, such as a value object, within any of your entities.</span></span> <span data-ttu-id="67c3d-155">Typ jednostki będącej własnością udostępnia ten sam typ CLR z innym typem jednostki (oznacza to, że jest to zwykła klasa).</span><span class="sxs-lookup"><span data-stu-id="67c3d-155">An owned entity type shares the same CLR type with another entity type (that is, it’s just a regular class).</span></span> <span data-ttu-id="67c3d-156">Encja zawierająca nawigację definiującą jest jednostką właściciela.</span><span class="sxs-lookup"><span data-stu-id="67c3d-156">The entity containing the defining navigation is the owner entity.</span></span> <span data-ttu-id="67c3d-157">Podczas wykonywania zapytań do właściciela, należące typy są uwzględniane domyślnie.</span><span class="sxs-lookup"><span data-stu-id="67c3d-157">When querying the owner, the owned types are included by default.</span></span>

<span data-ttu-id="67c3d-158">Wystarczy spojrzeć na model domeny, typ własnością wygląda na to, że nie ma żadnej tożsamości.</span><span class="sxs-lookup"><span data-stu-id="67c3d-158">Just by looking at the domain model, an owned type looks like it doesn’t have any identity.</span></span> <span data-ttu-id="67c3d-159">Jednak pod przykrywką, owned typy mają tożsamość, ale właściwość nawigacji właściciela jest częścią tej tożsamości.</span><span class="sxs-lookup"><span data-stu-id="67c3d-159">However, under the covers, owned types do have identity, but the owner navigation property is part of this identity.</span></span>

<span data-ttu-id="67c3d-160">Tożsamość wystąpień typów należących do nich nie jest całkowicie ich własnością.</span><span class="sxs-lookup"><span data-stu-id="67c3d-160">The identity of instances of owned types is not completely their own.</span></span> <span data-ttu-id="67c3d-161">Składa się z trzech elementów:</span><span class="sxs-lookup"><span data-stu-id="67c3d-161">It consists of three components:</span></span>

- <span data-ttu-id="67c3d-162">Tożsamość właściciela</span><span class="sxs-lookup"><span data-stu-id="67c3d-162">The identity of the owner</span></span>

- <span data-ttu-id="67c3d-163">Właściwość nawigacji wskazująca na nie</span><span class="sxs-lookup"><span data-stu-id="67c3d-163">The navigation property pointing to them</span></span>

- <span data-ttu-id="67c3d-164">W przypadku kolekcji typów będących własnością niezależny składnik (obsługiwany w EF Core 2.2 i nowszych).</span><span class="sxs-lookup"><span data-stu-id="67c3d-164">In the case of collections of owned types, an independent component (supported in EF Core 2.2 and later).</span></span>

<span data-ttu-id="67c3d-165">Na przykład w modelu domeny zamawiania w eShopOnContainers, jako część Order jednostki, Address value obiekt jest implementowany jako typ jednostki własnością w jednostce właściciela, która jest Order jednostki.</span><span class="sxs-lookup"><span data-stu-id="67c3d-165">For example, in the Ordering domain model at eShopOnContainers, as part of the Order entity, the Address value object is implemented as an owned entity type within the owner entity, which is the Order entity.</span></span> <span data-ttu-id="67c3d-166">Adres jest typem bez właściwości tożsamości zdefiniowanej w modelu domeny.</span><span class="sxs-lookup"><span data-stu-id="67c3d-166">Address is a type with no identity property defined in the domain model.</span></span> <span data-ttu-id="67c3d-167">Jest on używany jako właściwość typu Zamówienie, aby określić adres wysyłki dla określonego zamówienia.</span><span class="sxs-lookup"><span data-stu-id="67c3d-167">It is used as a property of the Order type to specify the shipping address for a particular order.</span></span>

<span data-ttu-id="67c3d-168">Zgodnie z konwencją klucz podstawowy cienia jest tworzony dla typu należącego do właściciela i zostanie zamapowany na tę samą tabelę co właściciel przy użyciu podziału tabeli.</span><span class="sxs-lookup"><span data-stu-id="67c3d-168">By convention, a shadow primary key is created for the owned type and it will be mapped to the same table as the owner by using table splitting.</span></span> <span data-ttu-id="67c3d-169">Dzięki temu można użyć typów własnościowych podobnie do tego, jak typy złożone są używane w EF6 w tradycyjnej platformie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="67c3d-169">This allows to use owned types similarly to how complex types are used in EF6 in the traditional .NET Framework.</span></span>

<span data-ttu-id="67c3d-170">Należy pamiętać, że typy własności nigdy nie są wykrywane przez konwencję w EF Core, więc należy zadeklarować je jawnie.</span><span class="sxs-lookup"><span data-stu-id="67c3d-170">It is important to note that owned types are never discovered by convention in EF Core, so you have to declare them explicitly.</span></span>

<span data-ttu-id="67c3d-171">W eShopOnContainers, w OrderingContext.cs, w ramach OnModelCreating() metody, istnieje wiele konfiguracji infrastruktury są stosowane.</span><span class="sxs-lookup"><span data-stu-id="67c3d-171">In eShopOnContainers, at the OrderingContext.cs, within the OnModelCreating() method, there are multiple infrastructure configuration being applied.</span></span> <span data-ttu-id="67c3d-172">Jeden z nich jest związany z jednostką Zamówienie.</span><span class="sxs-lookup"><span data-stu-id="67c3d-172">One of them is related to the Order entity.</span></span>

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

<span data-ttu-id="67c3d-173">W poniższym kodzie infrastruktury trwałości jest zdefiniowana dla Order jednostki:</span><span class="sxs-lookup"><span data-stu-id="67c3d-173">In the following code, the persistence infrastructure is defined for the Order entity:</span></span>

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

<span data-ttu-id="67c3d-174">W poprzednim kodzie `orderConfiguration.OwnsOne(o => o.Address)` metoda określa, `Address` że właściwość jest `Order` własnością jednostki typu.</span><span class="sxs-lookup"><span data-stu-id="67c3d-174">In the previous code, the `orderConfiguration.OwnsOne(o => o.Address)` method specifies that the `Address` property is an owned entity of the `Order` type.</span></span>

<span data-ttu-id="67c3d-175">Domyślnie konwencje EF Core nazwkolumny bazy danych dla właściwości `EntityProperty_OwnedEntityProperty`typu jednostki własnością jako .</span><span class="sxs-lookup"><span data-stu-id="67c3d-175">By default, EF Core conventions name the database columns for the properties of the owned entity type as `EntityProperty_OwnedEntityProperty`.</span></span> <span data-ttu-id="67c3d-176">W związku z tym `Address` wewnętrzne właściwości `Orders` pojawi się `Address_Street` `Address_City` w tabeli z `State` `Country` nazwami , (i tak dalej dla , i `ZipCode`).</span><span class="sxs-lookup"><span data-stu-id="67c3d-176">Therefore, the internal properties of `Address` will appear in the `Orders` table with the names `Address_Street`, `Address_City` (and so on for `State`, `Country` and `ZipCode`).</span></span>

<span data-ttu-id="67c3d-177">Można doniej `Property().HasColumnName()` dotokować metodę fluent, aby zmienić nazwy tych kolumn.</span><span class="sxs-lookup"><span data-stu-id="67c3d-177">You can append the `Property().HasColumnName()` fluent method to rename those columns.</span></span> <span data-ttu-id="67c3d-178">W przypadku, `Address` gdy jest własnością publiczną, mapowania będą następujące:</span><span class="sxs-lookup"><span data-stu-id="67c3d-178">In the case where `Address` is a public property, the mappings would be like the following:</span></span>

```csharp
orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.Street).HasColumnName("ShippingStreet");

orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.City).HasColumnName("ShippingCity");
```

<span data-ttu-id="67c3d-179">Możliwe jest łańcuch metody `OwnsOne` w płynnym mapowaniu.</span><span class="sxs-lookup"><span data-stu-id="67c3d-179">It's possible to chain the `OwnsOne` method in a fluent mapping.</span></span> <span data-ttu-id="67c3d-180">W poniższym hipotetycznym `OrderDetails` przykładzie, posiada `BillingAddress` i `ShippingAddress`, które są oba `Address` typy.</span><span class="sxs-lookup"><span data-stu-id="67c3d-180">In the following hypothetical example, `OrderDetails` owns `BillingAddress` and `ShippingAddress`, which are both `Address` types.</span></span> <span data-ttu-id="67c3d-181">Następnie `OrderDetails` jest własnością `Order` typu.</span><span class="sxs-lookup"><span data-stu-id="67c3d-181">Then `OrderDetails` is owned by the `Order` type.</span></span>

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

### <a name="additional-details-on-owned-entity-types"></a><span data-ttu-id="67c3d-182">Dodatkowe informacje na temat typów jednostek będących własnością</span><span class="sxs-lookup"><span data-stu-id="67c3d-182">Additional details on owned entity types</span></span>

- <span data-ttu-id="67c3d-183">Owned typy są definiowane podczas konfigurowania właściwości nawigacji do określonego typu przy użyciu OwnsOne fluent API.</span><span class="sxs-lookup"><span data-stu-id="67c3d-183">Owned types are defined when you configure a navigation property to a particular type using the OwnsOne fluent API.</span></span>

- <span data-ttu-id="67c3d-184">Definicja typu własnością w naszym modelu metadanych jest złożony: typ właściciela, właściwość nawigacji i typu CLR typu należącego do.</span><span class="sxs-lookup"><span data-stu-id="67c3d-184">The definition of an owned type in our metadata model is a composite of: the owner type, the navigation property, and the CLR type of the owned type.</span></span>

- <span data-ttu-id="67c3d-185">Tożsamość (klucz) wystąpienia typu należącego do naszego stosu jest złożoną tożsamością typu właściciela i definicją typu będącego własnością.</span><span class="sxs-lookup"><span data-stu-id="67c3d-185">The identity (key) of an owned type instance in our stack is a composite of the identity of the owner type and the definition of the owned type.</span></span>

#### <a name="owned-entities-capabilities"></a><span data-ttu-id="67c3d-186">Możliwości podmiotów będących własnością</span><span class="sxs-lookup"><span data-stu-id="67c3d-186">Owned entities capabilities</span></span>

- <span data-ttu-id="67c3d-187">Owned typy mogą odwoływać się do innych jednostek, albo własnością (zagnieżdżonych typów własnością) lub niewłasnością (regularne właściwości nawigacji odniesienia do innych jednostek).</span><span class="sxs-lookup"><span data-stu-id="67c3d-187">Owned types can reference other entities, either owned (nested owned types) or non-owned (regular reference navigation properties to other entities).</span></span>

- <span data-ttu-id="67c3d-188">Można mapować ten sam typ CLR jako różne typy własności w tej samej encji właściciela za pomocą oddzielnych właściwości nawigacji.</span><span class="sxs-lookup"><span data-stu-id="67c3d-188">You can map the same CLR type as different owned types in the same owner entity through separate navigation properties.</span></span>

- <span data-ttu-id="67c3d-189">Podział tabel jest konfigurowany według konwencji, ale można zrezygnować, mapując typ własności do innej tabeli przy użyciu tabeli ToTable.</span><span class="sxs-lookup"><span data-stu-id="67c3d-189">Table splitting is setup by convention, but you can opt out by mapping the owned type to a different table using ToTable.</span></span>

- <span data-ttu-id="67c3d-190">Wczesne ładowanie odbywa się automatycznie na posiadanych typów, oznacza to, że nie ma potrzeby wywoływania `.Include()` kwerendy.</span><span class="sxs-lookup"><span data-stu-id="67c3d-190">Eager loading is performed automatically on owned types, that is, there's no need to call `.Include()` on the query.</span></span>

- <span data-ttu-id="67c3d-191">Można skonfigurować za `[Owned]`pomocą atrybutu , przy użyciu EF Core 2.1 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="67c3d-191">Can be configured with attribute `[Owned]`, using EF Core 2.1 and later.</span></span>

- <span data-ttu-id="67c3d-192">Może obsługiwać kolekcje typów należących do nich (przy użyciu wersji 2.2 i nowszych).</span><span class="sxs-lookup"><span data-stu-id="67c3d-192">Can handle collections of owned types (using version 2.2 and later).</span></span>

#### <a name="owned-entities-limitations"></a><span data-ttu-id="67c3d-193">Ograniczenia podmiotów będących własnością</span><span class="sxs-lookup"><span data-stu-id="67c3d-193">Owned entities limitations</span></span>

- <span data-ttu-id="67c3d-194">Nie można utworzyć `DbSet<T>` typu należącego do nabytych (według projektu).</span><span class="sxs-lookup"><span data-stu-id="67c3d-194">You can't create a `DbSet<T>` of an owned type (by design).</span></span>

- <span data-ttu-id="67c3d-195">Nie można wywoływać `ModelBuilder.Entity<T>()` typów będących własnością (obecnie według projektu).</span><span class="sxs-lookup"><span data-stu-id="67c3d-195">You can't call `ModelBuilder.Entity<T>()` on owned types (currently by design).</span></span>

- <span data-ttu-id="67c3d-196">Brak obsługi opcjonalnych (czyli wartości null) należących do typów, które są mapowane z właścicielem w tej samej tabeli (czyli przy użyciu podziału tabeli).</span><span class="sxs-lookup"><span data-stu-id="67c3d-196">No support for optional (that is, nullable) owned types that are mapped with the owner in the same table (that is, using table splitting).</span></span> <span data-ttu-id="67c3d-197">Jest tak, ponieważ mapowanie odbywa się dla każdej właściwości, nie mamy oddzielnego wskaźnika dla wartości złożonej null jako całości.</span><span class="sxs-lookup"><span data-stu-id="67c3d-197">This is because mapping is done for each property, we don't have a separate sentinel for the null complex value a as whole.</span></span>

- <span data-ttu-id="67c3d-198">Brak obsługi mapowania dziedziczenia dla typów należących do nich, ale powinno być możliwe mapowanie dwóch typów liści tych samych hierarchii dziedziczenia jako różnych typów własności.</span><span class="sxs-lookup"><span data-stu-id="67c3d-198">No inheritance mapping support for owned types, but you should be able to map two leaf types of the same inheritance hierarchies as different owned types.</span></span> <span data-ttu-id="67c3d-199">EF Core nie będzie powodu o tym, że są one częścią tej samej hierarchii.</span><span class="sxs-lookup"><span data-stu-id="67c3d-199">EF Core will not reason about the fact that they are part of the same hierarchy.</span></span>

#### <a name="main-differences-with-ef6s-complex-types"></a><span data-ttu-id="67c3d-200">Główne różnice w stosunku do złożonych typów EF6</span><span class="sxs-lookup"><span data-stu-id="67c3d-200">Main differences with EF6's complex types</span></span>

- <span data-ttu-id="67c3d-201">Dzielenie tabel jest opcjonalne, oznacza to, że opcjonalnie można je mapować na oddzielną tabelę i nadal być własnością typów.</span><span class="sxs-lookup"><span data-stu-id="67c3d-201">Table splitting is optional, that is, they can optionally be mapped to a separate table and still be owned types.</span></span>

- <span data-ttu-id="67c3d-202">Mogą odwoływać się do innych jednostek (to oznacza, że mogą działać jako strona zależna od relacji z innymi typami niebędącymi własnością).</span><span class="sxs-lookup"><span data-stu-id="67c3d-202">They can reference other entities (that is, they can act as the dependent side on relationships to other non-owned types).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="67c3d-203">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="67c3d-203">Additional resources</span></span>

- <span data-ttu-id="67c3d-204">**Martin Fowler. Wzorzec ValueObject** </span><span class="sxs-lookup"><span data-stu-id="67c3d-204">**Martin Fowler. ValueObject pattern** </span></span>\
  <https://martinfowler.com/bliki/ValueObject.html>

- <span data-ttu-id="67c3d-205">**Eric Evans. Projektowanie oparte na domenie: radzenie sobie ze złożonością w sercu oprogramowania.**</span><span class="sxs-lookup"><span data-stu-id="67c3d-205">**Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software.**</span></span> <span data-ttu-id="67c3d-206">(Książka; zawiera omówienie obiektów wartości) </span><span class="sxs-lookup"><span data-stu-id="67c3d-206">(Book; includes a discussion of value objects) </span></span>\
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

- <span data-ttu-id="67c3d-207">**Vaughn Vernon. Implementowanie projektu opartego na domenie.**</span><span class="sxs-lookup"><span data-stu-id="67c3d-207">**Vaughn Vernon. Implementing Domain-Driven Design.**</span></span> <span data-ttu-id="67c3d-208">(Książka; zawiera omówienie obiektów wartości) </span><span class="sxs-lookup"><span data-stu-id="67c3d-208">(Book; includes a discussion of value objects) </span></span>\
  <https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/>

- <span data-ttu-id="67c3d-209">**Typy jednostek będących własnością** </span><span class="sxs-lookup"><span data-stu-id="67c3d-209">**Owned Entity Types** </span></span>\
  <https://docs.microsoft.com/ef/core/modeling/owned-entities>

- <span data-ttu-id="67c3d-210">**Właściwości cienia** </span><span class="sxs-lookup"><span data-stu-id="67c3d-210">**Shadow Properties** </span></span>\
  <https://docs.microsoft.com/ef/core/modeling/shadow-properties>

- <span data-ttu-id="67c3d-211">**Złożone typy i/lub obiekty wartości**.</span><span class="sxs-lookup"><span data-stu-id="67c3d-211">**Complex types and/or value objects**.</span></span> <span data-ttu-id="67c3d-212">Dyskusja w ef core GitHub repo (problemy kartę) </span><span class="sxs-lookup"><span data-stu-id="67c3d-212">Discussion in the EF Core GitHub repo (Issues tab) </span></span>\
  <https://github.com/dotnet/efcore/issues/246>

- <span data-ttu-id="67c3d-213">**ValueObject.cs.**</span><span class="sxs-lookup"><span data-stu-id="67c3d-213">**ValueObject.cs.**</span></span> <span data-ttu-id="67c3d-214">Klasa obiektu wartości podstawowej w eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="67c3d-214">Base value object class in eShopOnContainers.</span></span> \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs>

- <span data-ttu-id="67c3d-215">**Klasa adresu.**</span><span class="sxs-lookup"><span data-stu-id="67c3d-215">**Address class.**</span></span> <span data-ttu-id="67c3d-216">Przykładowa klasa obiektu wartości w eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="67c3d-216">Sample value object class in eShopOnContainers.</span></span> \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs>

> [!div class="step-by-step"]
> <span data-ttu-id="67c3d-217">[Poprzedni](seedwork-domain-model-base-classes-interfaces.md)
> [następny](enumeration-classes-over-enum-types.md)</span><span class="sxs-lookup"><span data-stu-id="67c3d-217">[Previous](seedwork-domain-model-base-classes-interfaces.md)
[Next](enumeration-classes-over-enum-types.md)</span></span>

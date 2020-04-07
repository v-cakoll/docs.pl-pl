---
title: Implementowanie obiektów wartości
description: Architektura mikrousług platformy .NET dla konteneryzowanych aplikacji .NET | Zapoznaj się ze szczegółami i opcjami implementowania obiektów wartości przy użyciu nowych funkcji programu Entity Framework.
ms.date: 01/30/2020
ms.openlocfilehash: 4a8a92a8dabcf09654ecd0e5dea2a7df25d7abf7
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805737"
---
# <a name="implement-value-objects"></a><span data-ttu-id="a86a7-103">Implementowanie obiektów wartości</span><span class="sxs-lookup"><span data-stu-id="a86a7-103">Implement value objects</span></span>

<span data-ttu-id="a86a7-104">Jak wspomniano we wcześniejszych sekcjach dotyczących jednostek i agregacji, tożsamość ma podstawowe znaczenie dla jednostek.</span><span class="sxs-lookup"><span data-stu-id="a86a7-104">As discussed in earlier sections about entities and aggregates, identity is fundamental for entities.</span></span> <span data-ttu-id="a86a7-105">Jednak istnieje wiele obiektów i elementów danych w systemie, które nie wymagają śledzenia tożsamości i tożsamości, takich jak obiekty wartości.</span><span class="sxs-lookup"><span data-stu-id="a86a7-105">However, there are many objects and data items in a system that do not require an identity and identity tracking, such as value objects.</span></span>

<span data-ttu-id="a86a7-106">Obiekt wartości może odwoływać się do innych jednostek.</span><span class="sxs-lookup"><span data-stu-id="a86a7-106">A value object can reference other entities.</span></span> <span data-ttu-id="a86a7-107">Na przykład w aplikacji, która generuje trasę, która opisuje, jak uzyskać z jednego punktu do drugiego, tej trasy będzie obiekt wartości.</span><span class="sxs-lookup"><span data-stu-id="a86a7-107">For example, in an application that generates a route that describes how to get from one point to another, that route would be a value object.</span></span> <span data-ttu-id="a86a7-108">Byłoby to migawka punktów na określonej trasie, ale ta sugerowana trasa nie miałaby tożsamości, nawet jeśli wewnętrznie może odnosić się do jednostek takich jak Miasto, Droga itp.</span><span class="sxs-lookup"><span data-stu-id="a86a7-108">It would be a snapshot of points on a specific route, but this suggested route would not have an identity, even though internally it might refer to entities like City, Road, etc.</span></span>

<span data-ttu-id="a86a7-109">Rysunek 7-13 przedstawia obiekt wartości adresu w agregacji Order.</span><span class="sxs-lookup"><span data-stu-id="a86a7-109">Figure 7-13 shows the Address value object within the Order aggregate.</span></span>

![Diagram przedstawiający obiekt wartości adresu wewnątrz agregacji zamówień.](./media/implement-value-objects/value-object-within-aggregate.png)

<span data-ttu-id="a86a7-111">**Rysunek 7-13**.</span><span class="sxs-lookup"><span data-stu-id="a86a7-111">**Figure 7-13**.</span></span> <span data-ttu-id="a86a7-112">Obiekt wartości adresu w agregacji Zamówienia</span><span class="sxs-lookup"><span data-stu-id="a86a7-112">Address value object within the Order aggregate</span></span>

<span data-ttu-id="a86a7-113">Jak pokazano na rysunku 7-13, jednostka składa się zwykle z wielu atrybutów.</span><span class="sxs-lookup"><span data-stu-id="a86a7-113">As shown in Figure 7-13, an entity is usually composed of multiple attributes.</span></span> <span data-ttu-id="a86a7-114">Na przykład `Order` jednostka może być modelowana jako jednostka z tożsamością i składa się wewnętrznie z zestawu atrybutów, takich jak OrderId, OrderDate, OrderItems itp. Ale adres, który jest po prostu złożoną wartością składającą się z kraju/regionu, ulicy, miasta itp.</span><span class="sxs-lookup"><span data-stu-id="a86a7-114">For example, the `Order` entity can be modeled as an entity with an identity and composed internally of a set of attributes such as OrderId, OrderDate, OrderItems, etc. But the address, which is simply a complex-value composed of country/region, street, city, etc. and has no identity in this domain, must be modeled and treated as a value object.</span></span>

## <a name="important-characteristics-of-value-objects"></a><span data-ttu-id="a86a7-115">Ważne cechy obiektów wartości</span><span class="sxs-lookup"><span data-stu-id="a86a7-115">Important characteristics of value objects</span></span>

<span data-ttu-id="a86a7-116">Istnieją dwie główne cechy obiektów wartości:</span><span class="sxs-lookup"><span data-stu-id="a86a7-116">There are two main characteristics for value objects:</span></span>

- <span data-ttu-id="a86a7-117">Nie mają tożsamości.</span><span class="sxs-lookup"><span data-stu-id="a86a7-117">They have no identity.</span></span>

- <span data-ttu-id="a86a7-118">Są niezmienne.</span><span class="sxs-lookup"><span data-stu-id="a86a7-118">They are immutable.</span></span>

<span data-ttu-id="a86a7-119">Pierwsza cecha była już omawiana.</span><span class="sxs-lookup"><span data-stu-id="a86a7-119">The first characteristic was already discussed.</span></span> <span data-ttu-id="a86a7-120">Niezmienność jest ważnym wymogiem.</span><span class="sxs-lookup"><span data-stu-id="a86a7-120">Immutability is an important requirement.</span></span> <span data-ttu-id="a86a7-121">Wartości obiektu wartości muszą być niezmienne po utworzeniu obiektu.</span><span class="sxs-lookup"><span data-stu-id="a86a7-121">The values of a value object must be immutable once the object is created.</span></span> <span data-ttu-id="a86a7-122">W związku z tym podczas konstruowania obiektu, należy podać wymagane wartości, ale nie można zezwolić na ich zmiany w okresie istnienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="a86a7-122">Therefore, when the object is constructed, you must provide the required values, but you must not allow them to change during the object's lifetime.</span></span>

<span data-ttu-id="a86a7-123">Obiekty wartości pozwalają wykonywać pewne sztuczki dla wydajności, dzięki ich niezmiennej naturze.</span><span class="sxs-lookup"><span data-stu-id="a86a7-123">Value objects allow you to perform certain tricks for performance, thanks to their immutable nature.</span></span> <span data-ttu-id="a86a7-124">Jest to szczególnie prawdziwe w systemach, w których mogą istnieć tysiące wystąpień obiektów wartości, z których wiele ma te same wartości.</span><span class="sxs-lookup"><span data-stu-id="a86a7-124">This is especially true in systems where there may be thousands of value object instances, many of which have the same values.</span></span> <span data-ttu-id="a86a7-125">Ich niezmienny charakter pozwala na ich ponowneużycie; mogą być wymiennymi obiektami, ponieważ ich wartości są takie same i nie mają tożsamości.</span><span class="sxs-lookup"><span data-stu-id="a86a7-125">Their immutable nature allows them to be reused; they can be interchangeable objects, since their values are the same and they have no identity.</span></span> <span data-ttu-id="a86a7-126">Ten rodzaj optymalizacji może czasami zrobić różnicę między oprogramowaniem, które działa wolno, a oprogramowaniem o dobrej wydajności.</span><span class="sxs-lookup"><span data-stu-id="a86a7-126">This type of optimization can sometimes make a difference between software that runs slowly and software with good performance.</span></span> <span data-ttu-id="a86a7-127">Oczywiście wszystkie te przypadki zależą od środowiska aplikacji i kontekstu wdrażania.</span><span class="sxs-lookup"><span data-stu-id="a86a7-127">Of course, all these cases depend on the application environment and deployment context.</span></span>

## <a name="value-object-implementation-in-c"></a><span data-ttu-id="a86a7-128">Implementacja obiektu wartości w języku C\#</span><span class="sxs-lookup"><span data-stu-id="a86a7-128">Value object implementation in C\#</span></span>

<span data-ttu-id="a86a7-129">Jeśli chodzi o implementację, można mieć klasę podstawową obiektu wartości, która ma podstawowe metody narzędzia, takie jak równość na podstawie porównania wszystkich atrybutów (ponieważ obiekt wartości nie może być oparty na tożsamości) i innych podstawowych cech.</span><span class="sxs-lookup"><span data-stu-id="a86a7-129">In terms of implementation, you can have a value object base class that has basic utility methods like equality based on comparison between all the attributes (since a value object must not be based on identity) and other fundamental characteristics.</span></span> <span data-ttu-id="a86a7-130">Poniższy przykład pokazuje klasę podstawową obiektu wartości używane w mikrousługi zamawiania z eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="a86a7-130">The following example shows a value object base class used in the ordering microservice from eShopOnContainers.</span></span>

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

<span data-ttu-id="a86a7-131">Tej klasy można użyć podczas implementowania obiektu rzeczywistej wartości, tak jak w przypadku obiektu wartość adresu wyświetlanego w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="a86a7-131">You can use this class when implementing your actual value object, as with the Address value object shown in the following example:</span></span>

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

<span data-ttu-id="a86a7-132">Można zobaczyć, jak ta implementacja obiektu wartości Address nie ma tożsamości i dlatego nie ma pola identyfikator, ani w klasie Adres nawet w ValueObject klasy.</span><span class="sxs-lookup"><span data-stu-id="a86a7-132">You can see how this value object implementation of Address has no identity and therefore, no ID field, neither at the Address class not even at the ValueObject class.</span></span>

<span data-ttu-id="a86a7-133">Brak pola identyfikatora w klasie, która ma być używana przez entity framework (EF) nie było możliwe, dopóki EF Core 2.0, co znacznie pomaga zaimplementować obiekty o lepszej wartości bez identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="a86a7-133">Having no ID field in a class to be used by Entity Framework (EF) was not possible until EF Core 2.0, which greatly helps to implement better value objects with no ID.</span></span> <span data-ttu-id="a86a7-134">To jest właśnie wyjaśnienie następnej sekcji.</span><span class="sxs-lookup"><span data-stu-id="a86a7-134">That is precisely the explanation of the next section.</span></span>

<span data-ttu-id="a86a7-135">Można argumentować, że obiekty wartości, są niezmienne, powinny być tylko do odczytu (to znaczy, mają właściwości tylko do uzyskania), i to rzeczywiście prawda.</span><span class="sxs-lookup"><span data-stu-id="a86a7-135">It could be argued that value objects, being immutable, should be read-only (that is, have get-only properties), and that's indeed true.</span></span> <span data-ttu-id="a86a7-136">Jednak obiekty wartości są zwykle serializowane i deserializowane, aby przejść przez kolejki komunikatów, a tylko do odczytu `private set`zatrzymuje deserializatora przed przypisywaniem wartości, więc po prostu pozostawiamy je jako , które są wystarczająco czytelne, aby były praktyczne.</span><span class="sxs-lookup"><span data-stu-id="a86a7-136">However, value objects are usually serialized and deserialized to go through message queues, and being read-only stops the deserializer from assigning values, so we just leave them as `private set`, which is read-only enough to be practical.</span></span>

## <a name="how-to-persist-value-objects-in-the-database-with-ef-core-20-and-later"></a><span data-ttu-id="a86a7-137">Jak utrwalić obiekty wartości w bazie danych za pomocą EF Core 2.0 i nowszych</span><span class="sxs-lookup"><span data-stu-id="a86a7-137">How to persist value objects in the database with EF Core 2.0 and later</span></span>

<span data-ttu-id="a86a7-138">Właśnie zobaczyłeś, jak zdefiniować obiekt wartości w modelu domeny.</span><span class="sxs-lookup"><span data-stu-id="a86a7-138">You just saw how to define a value object in your domain model.</span></span> <span data-ttu-id="a86a7-139">Ale jak można rzeczywiście utrwalić go w bazie danych przy użyciu entity framework core, ponieważ zwykle jest przeznaczony dla jednostek z tożsamością?</span><span class="sxs-lookup"><span data-stu-id="a86a7-139">But how can you actually persist it into the database using Entity Framework Core since it usually targets entities with identity?</span></span>

### <a name="background-and-older-approaches-using-ef-core-11"></a><span data-ttu-id="a86a7-140">Tło i starsze podejścia przy użyciu EF Core 1.1</span><span class="sxs-lookup"><span data-stu-id="a86a7-140">Background and older approaches using EF Core 1.1</span></span>

<span data-ttu-id="a86a7-141">W tle ograniczenie podczas korzystania z EF Core 1.0 i 1.1 było to, że nie można użyć [typów złożonych,](xref:System.ComponentModel.DataAnnotations.Schema.ComplexTypeAttribute) zgodnie z definicją w EF 6.x w tradycyjnej .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a86a7-141">As background, a limitation when using EF Core 1.0 and 1.1 was that you could not use [complex types](xref:System.ComponentModel.DataAnnotations.Schema.ComplexTypeAttribute) as defined in EF 6.x in the traditional .NET Framework.</span></span> <span data-ttu-id="a86a7-142">W związku z tym jeśli przy użyciu EF Core 1.0 lub 1.1, trzeba przechowywać obiekt wartości jako jednostki EF z polem identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="a86a7-142">Therefore, if using EF Core 1.0 or 1.1, you needed to store your value object as an EF entity with an ID field.</span></span> <span data-ttu-id="a86a7-143">Następnie, więc wyglądało to bardziej jak obiekt wartości bez tożsamości, można ukryć jego identyfikator, dzięki czemu można wyjaśnić, że tożsamość obiektu wartości nie jest ważne w modelu domeny.</span><span class="sxs-lookup"><span data-stu-id="a86a7-143">Then, so it looked more like a value object with no identity, you could hide its ID so you make clear that the identity of a value object is not important in the domain model.</span></span> <span data-ttu-id="a86a7-144">Identyfikator można ukryć, używając identyfikatora jako [właściwości shadow](https://docs.microsoft.com/ef/core/modeling/shadow-properties ).</span><span class="sxs-lookup"><span data-stu-id="a86a7-144">You could hide that ID by using the ID as a [shadow property](https://docs.microsoft.com/ef/core/modeling/shadow-properties ).</span></span> <span data-ttu-id="a86a7-145">Ponieważ ta konfiguracja do ukrywania identyfikatora w modelu jest skonfigurowany na poziomie infrastruktury EF, byłoby to rodzaj przezroczyste dla modelu domeny.</span><span class="sxs-lookup"><span data-stu-id="a86a7-145">Since that configuration for hiding the ID in the model is set up in the EF infrastructure level, it would be kind of transparent for your domain model.</span></span>

<span data-ttu-id="a86a7-146">W początkowej wersji eShopOnContainers (.NET Core 1.1), ukryty identyfikator wymagany przez infrastrukturę EF Core został zaimplementowany w następujący sposób na poziomie DbContext przy użyciu interfejsu API Fluent w projekcie infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="a86a7-146">In the initial version of eShopOnContainers (.NET Core 1.1), the hidden ID needed by EF Core infrastructure was implemented in the following way in the DbContext level, using Fluent API at the infrastructure project.</span></span> <span data-ttu-id="a86a7-147">W związku z tym identyfikator był ukryty z punktu widzenia modelu domeny, ale nadal obecny w infrastrukturze.</span><span class="sxs-lookup"><span data-stu-id="a86a7-147">Therefore, the ID was hidden from the domain model point of view, but still present in the infrastructure.</span></span>

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

<span data-ttu-id="a86a7-148">Jednak trwałość tego obiektu wartości w bazie danych została wykonana jak zwykła jednostka w innej tabeli.</span><span class="sxs-lookup"><span data-stu-id="a86a7-148">However, the persistence of that value object into the database was performed like a regular entity in a different table.</span></span>

<span data-ttu-id="a86a7-149">Z EF Core 2.0 i nowsze, istnieją nowe i lepsze sposoby utrwalania obiektów wartości.</span><span class="sxs-lookup"><span data-stu-id="a86a7-149">With EF Core 2.0 and later, there are new and better ways to persist value objects.</span></span>

## <a name="persist-value-objects-as-owned-entity-types-in-ef-core-20-and-later"></a><span data-ttu-id="a86a7-150">Zachowywanie obiektów wartości jako typów jednostek należących do ef core 2.0 i nowszych</span><span class="sxs-lookup"><span data-stu-id="a86a7-150">Persist value objects as owned entity types in EF Core 2.0 and later</span></span>

<span data-ttu-id="a86a7-151">Nawet w przypadku niektórych przerw między wzorcem obiektu wartości kanonicznej w DDD a typem jednostki należącej do własnością w ef core, jest obecnie najlepszym sposobem utrwalania obiektów wartości za pomocą EF Core 2.0 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="a86a7-151">Even with some gaps between the canonical value object pattern in DDD and the owned entity type in EF Core, it's currently the best way to persist value objects with EF Core 2.0 and later.</span></span> <span data-ttu-id="a86a7-152">Ograniczenia można zobaczyć na końcu tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="a86a7-152">You can see limitations at the end of this section.</span></span>

<span data-ttu-id="a86a7-153">Funkcja typu jednostki należącej została dodana do ef core od wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="a86a7-153">The owned entity type feature was added to EF Core since version 2.0.</span></span>

<span data-ttu-id="a86a7-154">Typ jednostki należącej do użytkownika umożliwia mapowanie typów, które nie mają własnej tożsamości jawnie zdefiniowanej w modelu domeny i są używane jako właściwości, takie jak obiekt wartości, w dowolnej jednostce.</span><span class="sxs-lookup"><span data-stu-id="a86a7-154">An owned entity type allows you to map types that do not have their own identity explicitly defined in the domain model and are used as properties, such as a value object, within any of your entities.</span></span> <span data-ttu-id="a86a7-155">Typ jednostki należącej do jednostki współumisuje ten sam typ CLR z innym typem jednostki (oznacza to, że jest to tylko klasa zwykła).</span><span class="sxs-lookup"><span data-stu-id="a86a7-155">An owned entity type shares the same CLR type with another entity type (that is, it's just a regular class).</span></span> <span data-ttu-id="a86a7-156">Encja zawierająca definiującą nawigację jest jednostką właściciela.</span><span class="sxs-lookup"><span data-stu-id="a86a7-156">The entity containing the defining navigation is the owner entity.</span></span> <span data-ttu-id="a86a7-157">Podczas wykonywania zapytań właściciela, posiadanych typów są uwzględniane domyślnie.</span><span class="sxs-lookup"><span data-stu-id="a86a7-157">When querying the owner, the owned types are included by default.</span></span>

<span data-ttu-id="a86a7-158">Wystarczy spojrzeć na model domeny, typ własnością wygląda tak, że nie ma żadnej tożsamości.</span><span class="sxs-lookup"><span data-stu-id="a86a7-158">Just by looking at the domain model, an owned type looks like it doesn't have any identity.</span></span> <span data-ttu-id="a86a7-159">Jednak w obszarze obejmuje, typy należące mają tożsamość, ale właściwość nawigacji właściciela jest częścią tej tożsamości.</span><span class="sxs-lookup"><span data-stu-id="a86a7-159">However, under the covers, owned types do have identity, but the owner navigation property is part of this identity.</span></span>

<span data-ttu-id="a86a7-160">Tożsamość wystąpień typów należących do państwa nie jest całkowicie ich własne.</span><span class="sxs-lookup"><span data-stu-id="a86a7-160">The identity of instances of owned types is not completely their own.</span></span> <span data-ttu-id="a86a7-161">Składa się z trzech elementów:</span><span class="sxs-lookup"><span data-stu-id="a86a7-161">It consists of three components:</span></span>

- <span data-ttu-id="a86a7-162">Tożsamość właściciela</span><span class="sxs-lookup"><span data-stu-id="a86a7-162">The identity of the owner</span></span>

- <span data-ttu-id="a86a7-163">Właściwość nawigacji wskazująca na nich</span><span class="sxs-lookup"><span data-stu-id="a86a7-163">The navigation property pointing to them</span></span>

- <span data-ttu-id="a86a7-164">W przypadku kolekcji posiadanych typów, niezależny składnik (obsługiwany w EF Core 2.2 i nowszych).</span><span class="sxs-lookup"><span data-stu-id="a86a7-164">In the case of collections of owned types, an independent component (supported in EF Core 2.2 and later).</span></span>

<span data-ttu-id="a86a7-165">Na przykład w modelu domeny zamawiania w eShopOnContainers, jako część Order jednostki, Adres wartość obiektu jest implementowana jako typ jednostki należącej do właściciela w jednostce właściciela, który jest Order jednostki.</span><span class="sxs-lookup"><span data-stu-id="a86a7-165">For example, in the Ordering domain model at eShopOnContainers, as part of the Order entity, the Address value object is implemented as an owned entity type within the owner entity, which is the Order entity.</span></span> <span data-ttu-id="a86a7-166">Adres jest typem bez właściwości tożsamości zdefiniowanej w modelu domeny.</span><span class="sxs-lookup"><span data-stu-id="a86a7-166">Address is a type with no identity property defined in the domain model.</span></span> <span data-ttu-id="a86a7-167">Jest on używany jako właściwość typu Zamówienie, aby określić adres wysyłki dla określonego zamówienia.</span><span class="sxs-lookup"><span data-stu-id="a86a7-167">It is used as a property of the Order type to specify the shipping address for a particular order.</span></span>

<span data-ttu-id="a86a7-168">Zgodnie z konwencją klucz podstawowy w tle jest tworzony dla typu należącego do właściciela i zostanie on mapowany na tę samą tabelę co właściciel przy użyciu podziału tabeli.</span><span class="sxs-lookup"><span data-stu-id="a86a7-168">By convention, a shadow primary key is created for the owned type and it will be mapped to the same table as the owner by using table splitting.</span></span> <span data-ttu-id="a86a7-169">Dzięki temu można używać typów posiadanych podobnie jak typy złożone są używane w EF6 w tradycyjnej .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a86a7-169">This allows to use owned types similarly to how complex types are used in EF6 in the traditional .NET Framework.</span></span>

<span data-ttu-id="a86a7-170">Należy pamiętać, że typy należące nigdy nie są odnajdywana przez konwencję w EF Core, więc należy zadeklarować je jawnie.</span><span class="sxs-lookup"><span data-stu-id="a86a7-170">It is important to note that owned types are never discovered by convention in EF Core, so you have to declare them explicitly.</span></span>

<span data-ttu-id="a86a7-171">W eShopOnContainers w pliku OrderingContext.cs w `OnModelCreating()` ramach metody stosuje się wiele konfiguracji infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="a86a7-171">In eShopOnContainers, in the OrderingContext.cs file, within the `OnModelCreating()` method, multiple infrastructure configurations are applied.</span></span> <span data-ttu-id="a86a7-172">Jeden z nich jest związany z jednostką Zakonu.</span><span class="sxs-lookup"><span data-stu-id="a86a7-172">One of them is related to the Order entity.</span></span>

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

<span data-ttu-id="a86a7-173">W poniższym kodzie infrastruktura trwałości jest zdefiniowana dla order jednostki:</span><span class="sxs-lookup"><span data-stu-id="a86a7-173">In the following code, the persistence infrastructure is defined for the Order entity:</span></span>

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

<span data-ttu-id="a86a7-174">W poprzednim kodzie `orderConfiguration.OwnsOne(o => o.Address)` metoda określa, `Address` że właściwość jest `Order` własnością jednostki typu.</span><span class="sxs-lookup"><span data-stu-id="a86a7-174">In the previous code, the `orderConfiguration.OwnsOne(o => o.Address)` method specifies that the `Address` property is an owned entity of the `Order` type.</span></span>

<span data-ttu-id="a86a7-175">Domyślnie konwencje EF Core nazywają kolumny bazy danych właściwościami typu `EntityProperty_OwnedEntityProperty`jednostki należącej do państwa jako .</span><span class="sxs-lookup"><span data-stu-id="a86a7-175">By default, EF Core conventions name the database columns for the properties of the owned entity type as `EntityProperty_OwnedEntityProperty`.</span></span> <span data-ttu-id="a86a7-176">W związku z tym `Address` wewnętrzne właściwości `Orders` pojawią się `Address_Street` `Address_City` w tabeli `State`z `Country`nazwami , (i tak dalej dla , i `ZipCode`).</span><span class="sxs-lookup"><span data-stu-id="a86a7-176">Therefore, the internal properties of `Address` will appear in the `Orders` table with the names `Address_Street`, `Address_City` (and so on for `State`, `Country`, and `ZipCode`).</span></span>

<span data-ttu-id="a86a7-177">Można dołączyć `Property().HasColumnName()` fluent metody, aby zmienić nazwę tych kolumn.</span><span class="sxs-lookup"><span data-stu-id="a86a7-177">You can append the `Property().HasColumnName()` fluent method to rename those columns.</span></span> <span data-ttu-id="a86a7-178">W przypadku, `Address` gdy jest własnością publiczną, mapowania będą podobne do następujących:</span><span class="sxs-lookup"><span data-stu-id="a86a7-178">In the case where `Address` is a public property, the mappings would be like the following:</span></span>

```csharp
orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.Street).HasColumnName("ShippingStreet");

orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.City).HasColumnName("ShippingCity");
```

<span data-ttu-id="a86a7-179">Możliwe jest łańcuch `OwnsOne` metody w płynne mapowanie.</span><span class="sxs-lookup"><span data-stu-id="a86a7-179">It's possible to chain the `OwnsOne` method in a fluent mapping.</span></span> <span data-ttu-id="a86a7-180">W poniższym hipotetycznym przykładzie `OrderDetails` jest właścicielem `BillingAddress` i `ShippingAddress`, które są oba `Address` typy.</span><span class="sxs-lookup"><span data-stu-id="a86a7-180">In the following hypothetical example, `OrderDetails` owns `BillingAddress` and `ShippingAddress`, which are both `Address` types.</span></span> <span data-ttu-id="a86a7-181">Następnie `OrderDetails` jest własnością `Order` typu.</span><span class="sxs-lookup"><span data-stu-id="a86a7-181">Then `OrderDetails` is owned by the `Order` type.</span></span>

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

### <a name="additional-details-on-owned-entity-types"></a><span data-ttu-id="a86a7-182">Dodatkowe informacje na temat typów jednostek będących własnością</span><span class="sxs-lookup"><span data-stu-id="a86a7-182">Additional details on owned entity types</span></span>

- <span data-ttu-id="a86a7-183">Typy należące do użytkownika są definiowane podczas konfigurowania właściwości nawigacji do określonego typu przy użyciu interfejsu API OwnsOne fluent.</span><span class="sxs-lookup"><span data-stu-id="a86a7-183">Owned types are defined when you configure a navigation property to a particular type using the OwnsOne fluent API.</span></span>

- <span data-ttu-id="a86a7-184">Definicja typu należącego do właściciela w naszym modelu metadanych jest złożona z: typu właściciela, właściwości nawigacji i typu CLR typu należącego do sieci.</span><span class="sxs-lookup"><span data-stu-id="a86a7-184">The definition of an owned type in our metadata model is a composite of: the owner type, the navigation property, and the CLR type of the owned type.</span></span>

- <span data-ttu-id="a86a7-185">Tożsamość (klucz) wystąpienia typu należącego w naszym stosie jest złożona tożsamości typu właściciela i definicji typu należącego do właściciela.</span><span class="sxs-lookup"><span data-stu-id="a86a7-185">The identity (key) of an owned type instance in our stack is a composite of the identity of the owner type and the definition of the owned type.</span></span>

#### <a name="owned-entities-capabilities"></a><span data-ttu-id="a86a7-186">Możliwości jednostek będących własnością</span><span class="sxs-lookup"><span data-stu-id="a86a7-186">Owned entities capabilities</span></span>

- <span data-ttu-id="a86a7-187">Typy własnością można odwoływać się do innych jednostek, własnością (zagnieżdżone typy własnością) lub niewłasności (regularne właściwości nawigacji odwołania do innych jednostek).</span><span class="sxs-lookup"><span data-stu-id="a86a7-187">Owned types can reference other entities, either owned (nested owned types) or non-owned (regular reference navigation properties to other entities).</span></span>

- <span data-ttu-id="a86a7-188">Można mapować ten sam typ CLR jako różne typy własnością w tej samej jednostce właściciela za pomocą oddzielnych właściwości nawigacji.</span><span class="sxs-lookup"><span data-stu-id="a86a7-188">You can map the same CLR type as different owned types in the same owner entity through separate navigation properties.</span></span>

- <span data-ttu-id="a86a7-189">Dzielenie tabel jest skonfigurowane przez konwencję, ale można zrezygnować, mapując typ należący do innej tabeli przy użyciu tabeli ToTable.</span><span class="sxs-lookup"><span data-stu-id="a86a7-189">Table splitting is set up by convention, but you can opt out by mapping the owned type to a different table using ToTable.</span></span>

- <span data-ttu-id="a86a7-190">Wczesne ładowanie jest wykonywane automatycznie na typy należące do `.Include()` firmy, oznacza to, że nie ma potrzeby wywoływania kwerendy.</span><span class="sxs-lookup"><span data-stu-id="a86a7-190">Eager loading is performed automatically on owned types, that is, there's no need to call `.Include()` on the query.</span></span>

- <span data-ttu-id="a86a7-191">Można skonfigurować za `[Owned]`pomocą atrybutu , przy użyciu EF Core 2.1 i nowszych.</span><span class="sxs-lookup"><span data-stu-id="a86a7-191">Can be configured with attribute `[Owned]`, using EF Core 2.1 and later.</span></span>

- <span data-ttu-id="a86a7-192">Może obsługiwać kolekcje posiadanych typów (przy użyciu wersji 2.2 i nowszych).</span><span class="sxs-lookup"><span data-stu-id="a86a7-192">Can handle collections of owned types (using version 2.2 and later).</span></span>

#### <a name="owned-entities-limitations"></a><span data-ttu-id="a86a7-193">Ograniczenia podmiotów będących własnością</span><span class="sxs-lookup"><span data-stu-id="a86a7-193">Owned entities limitations</span></span>

- <span data-ttu-id="a86a7-194">Nie można utworzyć `DbSet<T>` typu należącego do użytkownika (według projektu).</span><span class="sxs-lookup"><span data-stu-id="a86a7-194">You can't create a `DbSet<T>` of an owned type (by design).</span></span>

- <span data-ttu-id="a86a7-195">Nie można wywołać `ModelBuilder.Entity<T>()` na posiadanych typów (obecnie według projektu).</span><span class="sxs-lookup"><span data-stu-id="a86a7-195">You can't call `ModelBuilder.Entity<T>()` on owned types (currently by design).</span></span>

- <span data-ttu-id="a86a7-196">Brak obsługi dla typów należących do opcjonalnych (czyli nullable), które są mapowane z właścicielem w tej samej tabeli (czyli przy użyciu podziału tabeli).</span><span class="sxs-lookup"><span data-stu-id="a86a7-196">No support for optional (that is, nullable) owned types that are mapped with the owner in the same table (that is, using table splitting).</span></span> <span data-ttu-id="a86a7-197">Jest to spowodowane mapowanie jest wykonywane dla każdej właściwości, nie mamy oddzielne wartownika dla null złożonej wartości jako całości.</span><span class="sxs-lookup"><span data-stu-id="a86a7-197">This is because mapping is done for each property, we don't have a separate sentinel for the null complex value as a whole.</span></span>

- <span data-ttu-id="a86a7-198">Brak obsługi mapowania dziedziczenia dla typów posiadanych, ale powinno być możliwe mapowanie dwóch typów liści tych samych hierarchii dziedziczenia jako różnych typów należących.</span><span class="sxs-lookup"><span data-stu-id="a86a7-198">No inheritance-mapping support for owned types, but you should be able to map two leaf types of the same inheritance hierarchies as different owned types.</span></span> <span data-ttu-id="a86a7-199">EF Core nie będzie powodem o tym, że są one częścią tej samej hierarchii.</span><span class="sxs-lookup"><span data-stu-id="a86a7-199">EF Core will not reason about the fact that they are part of the same hierarchy.</span></span>

#### <a name="main-differences-with-ef6s-complex-types"></a><span data-ttu-id="a86a7-200">Główne różnice w stosunku do złożonych typów EF6</span><span class="sxs-lookup"><span data-stu-id="a86a7-200">Main differences with EF6's complex types</span></span>

- <span data-ttu-id="a86a7-201">Dzielenie tabeli jest opcjonalne, oznacza to, że opcjonalnie mogą być mapowane do osobnej tabeli i nadal być własnością typów.</span><span class="sxs-lookup"><span data-stu-id="a86a7-201">Table splitting is optional, that is, they can optionally be mapped to a separate table and still be owned types.</span></span>

- <span data-ttu-id="a86a7-202">Mogą odwoływać się do innych jednostek (oznacza to, że mogą działać jako strona zależna od relacji z innymi typami niewłasności).</span><span class="sxs-lookup"><span data-stu-id="a86a7-202">They can reference other entities (that is, they can act as the dependent side on relationships to other non-owned types).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="a86a7-203">Zasoby dodatkowe</span><span class="sxs-lookup"><span data-stu-id="a86a7-203">Additional resources</span></span>

- <span data-ttu-id="a86a7-204">**Martin Fowler. Wzorzec ValueObject** </span><span class="sxs-lookup"><span data-stu-id="a86a7-204">**Martin Fowler. ValueObject pattern** </span></span>\
  <https://martinfowler.com/bliki/ValueObject.html>

- <span data-ttu-id="a86a7-205">**Eric Evans. Projektowanie oparte na domenie: radzenie sobie ze złożonością w sercu oprogramowania.**</span><span class="sxs-lookup"><span data-stu-id="a86a7-205">**Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software.**</span></span> <span data-ttu-id="a86a7-206">(Książka; zawiera omówienie obiektów wartości) </span><span class="sxs-lookup"><span data-stu-id="a86a7-206">(Book; includes a discussion of value objects) </span></span>\
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

- <span data-ttu-id="a86a7-207">**Vaughn Vernon. Implementowanie projektu opartego na domenie.**</span><span class="sxs-lookup"><span data-stu-id="a86a7-207">**Vaughn Vernon. Implementing Domain-Driven Design.**</span></span> <span data-ttu-id="a86a7-208">(Książka; zawiera omówienie obiektów wartości) </span><span class="sxs-lookup"><span data-stu-id="a86a7-208">(Book; includes a discussion of value objects) </span></span>\
  <https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/>

- <span data-ttu-id="a86a7-209">**Typy jednostek będących własnością** </span><span class="sxs-lookup"><span data-stu-id="a86a7-209">**Owned Entity Types** </span></span>\
  <https://docs.microsoft.com/ef/core/modeling/owned-entities>

- <span data-ttu-id="a86a7-210">**Właściwości cienia** </span><span class="sxs-lookup"><span data-stu-id="a86a7-210">**Shadow Properties** </span></span>\
  <https://docs.microsoft.com/ef/core/modeling/shadow-properties>

- <span data-ttu-id="a86a7-211">**Złożone typy i/lub obiekty wartości**.</span><span class="sxs-lookup"><span data-stu-id="a86a7-211">**Complex types and/or value objects**.</span></span> <span data-ttu-id="a86a7-212">Dyskusja w repozytorium EF Core GitHub (karta Problemy) </span><span class="sxs-lookup"><span data-stu-id="a86a7-212">Discussion in the EF Core GitHub repo (Issues tab) </span></span>\
  <https://github.com/dotnet/efcore/issues/246>

- <span data-ttu-id="a86a7-213">**ValueObject.cs.**</span><span class="sxs-lookup"><span data-stu-id="a86a7-213">**ValueObject.cs.**</span></span> <span data-ttu-id="a86a7-214">Klasa obiektu wartości podstawowej w eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="a86a7-214">Base value object class in eShopOnContainers.</span></span> \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs>

- <span data-ttu-id="a86a7-215">**Klasa adresu.**</span><span class="sxs-lookup"><span data-stu-id="a86a7-215">**Address class.**</span></span> <span data-ttu-id="a86a7-216">Przykładowa klasa obiektu wartości w eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="a86a7-216">Sample value object class in eShopOnContainers.</span></span> \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs>

> [!div class="step-by-step"]
> <span data-ttu-id="a86a7-217">[Poprzedni](seedwork-domain-model-base-classes-interfaces.md)
> [następny](enumeration-classes-over-enum-types.md)</span><span class="sxs-lookup"><span data-stu-id="a86a7-217">[Previous](seedwork-domain-model-base-classes-interfaces.md)
[Next](enumeration-classes-over-enum-types.md)</span></span>

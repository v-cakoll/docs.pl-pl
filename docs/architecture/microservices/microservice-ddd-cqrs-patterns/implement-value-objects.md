---
title: Implementowanie obiektów wartości
description: Architektura mikrousług platformy .NET dla aplikacji platformy .NET w kontenerze | Zapoznaj się z informacjami i opcjami dotyczącymi implementowania obiektów wartości przy użyciu nowych funkcji Entity Framework.
ms.date: 10/08/2018
ms.openlocfilehash: 2608517c4006f5e8da1d31b2c337d8ddd3ddd542
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739869"
---
# <a name="implement-value-objects"></a><span data-ttu-id="8b619-103">Implementowanie obiektów wartości</span><span class="sxs-lookup"><span data-stu-id="8b619-103">Implement value objects</span></span>

<span data-ttu-id="8b619-104">Jak opisano w poprzednich sekcjach dotyczących jednostek i agregacji, tożsamość jest podstawowa dla jednostek.</span><span class="sxs-lookup"><span data-stu-id="8b619-104">As discussed in earlier sections about entities and aggregates, identity is fundamental for entities.</span></span> <span data-ttu-id="8b619-105">Istnieje jednak wiele obiektów i elementów danych w systemie, które nie wymagają śledzenia tożsamości i tożsamości, takie jak obiekty wartości.</span><span class="sxs-lookup"><span data-stu-id="8b619-105">However, there are many objects and data items in a system that do not require an identity and identity tracking, such as value objects.</span></span>

<span data-ttu-id="8b619-106">Obiekt wartości może odwoływać się do innych jednostek.</span><span class="sxs-lookup"><span data-stu-id="8b619-106">A value object can reference other entities.</span></span> <span data-ttu-id="8b619-107">Na przykład w aplikacji, która generuje trasę opisującą, jak uzyskać od jednego punktu do drugiego, ta trasa będzie obiektem wartości.</span><span class="sxs-lookup"><span data-stu-id="8b619-107">For example, in an application that generates a route that describes how to get from one point to another, that route would be a value object.</span></span> <span data-ttu-id="8b619-108">Będzie to migawka punktów w określonej trasie, ale ta trasa Sugerowana nie będzie miała tożsamości, nawet jeśli wewnętrznie może odnosić się do jednostek takich jak miasto, droga itp.</span><span class="sxs-lookup"><span data-stu-id="8b619-108">It would be a snapshot of points on a specific route, but this suggested route would not have an identity, even though internally it might refer to entities like City, Road, etc.</span></span>

<span data-ttu-id="8b619-109">Rysunek 7-13 pokazuje obiekt wartości adresu w ramach agregacji zamówienia.</span><span class="sxs-lookup"><span data-stu-id="8b619-109">Figure 7-13 shows the Address value object within the Order aggregate.</span></span>

![Diagram przedstawiający wartość adresu — obiekt wewnątrz agregacji zamówienia.](./media/implement-value-objects/value-object-within-aggregate.png)

<span data-ttu-id="8b619-111">**Rysunek 7-13**.</span><span class="sxs-lookup"><span data-stu-id="8b619-111">**Figure 7-13**.</span></span> <span data-ttu-id="8b619-112">Obiekt wartości adresu w ramach agregacji zamówienia</span><span class="sxs-lookup"><span data-stu-id="8b619-112">Address value object within the Order aggregate</span></span>

<span data-ttu-id="8b619-113">Jak pokazano na rysunku 7-13, jednostka jest zwykle składa się z wielu atrybutów.</span><span class="sxs-lookup"><span data-stu-id="8b619-113">As shown in Figure 7-13, an entity is usually composed of multiple attributes.</span></span> <span data-ttu-id="8b619-114">Na przykład jednostka `Order` może być modelowana jako jednostka z tożsamością i złożona wewnętrznie z zestawu atrybutów, takich jak IDZamówienia, DataZamówienia, OrderItems itp. Ale adres, który jest po prostu złożoną wartością składającą się z kraju/regionu, ulicy, miasta itp. i nie ma tożsamości w tej domenie, musi być modelowany i traktowany jako obiekt wartości.</span><span class="sxs-lookup"><span data-stu-id="8b619-114">For example, the `Order` entity can be modeled as an entity with an identity and composed internally of a set of attributes such as OrderId, OrderDate, OrderItems, etc. But the address, which is simply a complex-value composed of country/region, street, city, etc. and has no identity in this domain, must be modeled and treated as a value object.</span></span>

## <a name="important-characteristics-of-value-objects"></a><span data-ttu-id="8b619-115">Ważne cechy obiektów wartości</span><span class="sxs-lookup"><span data-stu-id="8b619-115">Important characteristics of value objects</span></span>

<span data-ttu-id="8b619-116">Istnieją dwie główne cechy obiektów wartości:</span><span class="sxs-lookup"><span data-stu-id="8b619-116">There are two main characteristics for value objects:</span></span>

- <span data-ttu-id="8b619-117">Nie mają tożsamości.</span><span class="sxs-lookup"><span data-stu-id="8b619-117">They have no identity.</span></span>

- <span data-ttu-id="8b619-118">Są one niezmienne.</span><span class="sxs-lookup"><span data-stu-id="8b619-118">They are immutable.</span></span>

<span data-ttu-id="8b619-119">Pierwsza cecha została już omówiona.</span><span class="sxs-lookup"><span data-stu-id="8b619-119">The first characteristic was already discussed.</span></span> <span data-ttu-id="8b619-120">Niezmienności jest ważnym wymaganiem.</span><span class="sxs-lookup"><span data-stu-id="8b619-120">Immutability is an important requirement.</span></span> <span data-ttu-id="8b619-121">Wartości obiektu wartości muszą być niezmienne po utworzeniu obiektu.</span><span class="sxs-lookup"><span data-stu-id="8b619-121">The values of a value object must be immutable once the object is created.</span></span> <span data-ttu-id="8b619-122">W związku z tym, gdy obiekt jest skonstruowany, należy podać wymagane wartości, ale nie można go zmienić w okresie istnienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="8b619-122">Therefore, when the object is constructed, you must provide the required values, but you must not allow them to change during the object’s lifetime.</span></span>

<span data-ttu-id="8b619-123">Obiekty wartości umożliwiają wykonywanie niektórych lew w celu uzyskania wydajności, dzięki czemu ich niezmiennego charakteru.</span><span class="sxs-lookup"><span data-stu-id="8b619-123">Value objects allow you to perform certain tricks for performance, thanks to their immutable nature.</span></span> <span data-ttu-id="8b619-124">Jest to szczególnie prawdziwe w systemach, w których mogą istnieć tysiące wystąpień obiektów wartości, z których wiele ma te same wartości.</span><span class="sxs-lookup"><span data-stu-id="8b619-124">This is especially true in systems where there may be thousands of value object instances, many of which have the same values.</span></span> <span data-ttu-id="8b619-125">Ich niezmienny charakter pozwala na ich użycie ponownie; mogą być obiektami wymiennymi, ponieważ ich wartości są takie same i nie mają tożsamości.</span><span class="sxs-lookup"><span data-stu-id="8b619-125">Their immutable nature allows them to be reused; they can be interchangeable objects, since their values are the same and they have no identity.</span></span> <span data-ttu-id="8b619-126">Ten typ optymalizacji może czasami pomieścić różnice między oprogramowaniem działającym wolno a oprogramowaniem o dobrej wydajności.</span><span class="sxs-lookup"><span data-stu-id="8b619-126">This type of optimization can sometimes make a difference between software that runs slowly and software with good performance.</span></span> <span data-ttu-id="8b619-127">Oczywiście wszystkie te przypadki są zależne od środowiska aplikacji i kontekstu wdrażania.</span><span class="sxs-lookup"><span data-stu-id="8b619-127">Of course, all these cases depend on the application environment and deployment context.</span></span>

## <a name="value-object-implementation-in-c"></a><span data-ttu-id="8b619-128">Implementacja obiektu wartości w języku C\#</span><span class="sxs-lookup"><span data-stu-id="8b619-128">Value object implementation in C\#</span></span>

<span data-ttu-id="8b619-129">W warunkach implementacji można utworzyć klasę bazową obiektu wartości, która ma podstawowe metody narzędziowe, takie jak równość, na podstawie porównania między wszystkimi atrybutami (ponieważ obiekt value nie może opierać się na tożsamości) i inne podstawowe cechy.</span><span class="sxs-lookup"><span data-stu-id="8b619-129">In terms of implementation, you can have a value object base class that has basic utility methods like equality based on comparison between all the attributes (since a value object must not be based on identity) and other fundamental characteristics.</span></span> <span data-ttu-id="8b619-130">W poniższym przykładzie pokazano klasę bazową obiektu wartości używaną w mikrousłudze porządkowania z eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="8b619-130">The following example shows a value object base class used in the ordering microservice from eShopOnContainers.</span></span>

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

<span data-ttu-id="8b619-131">Tej klasy można użyć podczas implementowania rzeczywistego obiektu wartości, podobnie jak w przypadku obiektu wartości adresu pokazanego w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="8b619-131">You can use this class when implementing your actual value object, as with the Address value object shown in the following example:</span></span>

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

<span data-ttu-id="8b619-132">Można zobaczyć, jak ta implementacja obiektu wartości nie ma tożsamości i w związku z tym nie ma pola identyfikatora ani w klasie adresowej, a nie nawet w klasie Valueobject.</span><span class="sxs-lookup"><span data-stu-id="8b619-132">You can see how this value object implementation of Address has no identity and therefore, no ID field, neither at the Address class not even at the ValueObject class.</span></span>

<span data-ttu-id="8b619-133">Brak pola identyfikatora w klasie, która ma być używana przez Entity Framework, nie było możliwe do EF Core 2,0, co znacznie pomaga zaimplementować lepsze obiekty wartości bez identyfikatora.</span><span class="sxs-lookup"><span data-stu-id="8b619-133">Having no ID field in a class to be used by Entity Framework was not possible until EF Core 2.0, which greatly helps to implement better value objects with no ID.</span></span> <span data-ttu-id="8b619-134">Jest to dokładne wyjaśnienie następnej sekcji.</span><span class="sxs-lookup"><span data-stu-id="8b619-134">That is precisely the explanation of the next section.</span></span>

<span data-ttu-id="8b619-135">Może być Argumentowano, że obiekty wartości, które są niezmienne, powinny być tylko do odczytu (tj. właściwości tylko do pobrania) i faktycznie prawdziwe.</span><span class="sxs-lookup"><span data-stu-id="8b619-135">It could be argued that value objects, being immutable, should be read-only (i.e. get-only properties), and that’s indeed true.</span></span> <span data-ttu-id="8b619-136">Jednak obiekty wartości są zwykle serializowane i deserializowane w celu przechodzenia przez kolejki komunikatów i są w trybie tylko do odczytu uniemożliwiają przypisanie wartości, dlatego po prostu pozostawiamy je jako zestaw prywatny, który jest wystarczająco duży, aby był praktyczny.</span><span class="sxs-lookup"><span data-stu-id="8b619-136">However, value objects are usually serialized and deserialized to go through message queues, and being read-only stops the deserializer from assigning values, so we just leave them as private set which is read-only enough to be practical.</span></span>

## <a name="how-to-persist-value-objects-in-the-database-with-ef-core-20"></a><span data-ttu-id="8b619-137">Jak utrwalać obiekty wartości w bazie danych za pomocą EF Core 2,0</span><span class="sxs-lookup"><span data-stu-id="8b619-137">How to persist value objects in the database with EF Core 2.0</span></span>

<span data-ttu-id="8b619-138">Właśnie pokazano, jak zdefiniować obiekt wartości w modelu domeny.</span><span class="sxs-lookup"><span data-stu-id="8b619-138">You just saw how to define a value object in your domain model.</span></span> <span data-ttu-id="8b619-139">Ale w jaki sposób można w rzeczywistości zachować ją w bazie danych za pomocą rdzenia Entity Framework (EF), które zwykle są obiektami docelowymi tożsamości?</span><span class="sxs-lookup"><span data-stu-id="8b619-139">But, how can you actually persist it into the database through Entity Framework (EF) Core which usually targets entities with identity?</span></span>

### <a name="background-and-older-approaches-using-ef-core-11"></a><span data-ttu-id="8b619-140">W tle i starszych podejściach korzystających z EF Core 1,1</span><span class="sxs-lookup"><span data-stu-id="8b619-140">Background and older approaches using EF Core 1.1</span></span>

<span data-ttu-id="8b619-141">W tle, ograniczenie w przypadku korzystania z EF Core 1,0 i 1,1 było niemożliwe, ponieważ nie można było użyć [typów złożonych](xref:System.ComponentModel.DataAnnotations.Schema.ComplexTypeAttribute) zdefiniowanych w Ef 6. x w tradycyjnych .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8b619-141">As background, a limitation when using EF Core 1.0 and 1.1 was that you could not use [complex types](xref:System.ComponentModel.DataAnnotations.Schema.ComplexTypeAttribute) as defined in EF 6.x in the traditional .NET Framework.</span></span> <span data-ttu-id="8b619-142">W związku z tym, jeśli jest używany EF Core 1,0 lub 1,1, należy przechowywać obiekt wartości jako jednostkę EF z polem ID.</span><span class="sxs-lookup"><span data-stu-id="8b619-142">Therefore, if using EF Core 1.0 or 1.1, you needed to store your value object as an EF entity with an ID field.</span></span> <span data-ttu-id="8b619-143">Następnie, aby wyglądała podobnie jak obiekt wartości bez tożsamości, można ukryć jego identyfikator, aby wyczyścić, że tożsamość obiektu wartości nie jest istotna w modelu domeny.</span><span class="sxs-lookup"><span data-stu-id="8b619-143">Then, so it looked more like a value object with no identity, you could hide its ID so you make clear that the identity of a value object is not important in the domain model.</span></span> <span data-ttu-id="8b619-144">Ten identyfikator można ukryć, używając identyfikatora jako [Właściwości cienia](https://docs.microsoft.com/ef/core/modeling/shadow-properties ).</span><span class="sxs-lookup"><span data-stu-id="8b619-144">You could hide that ID by using the ID as a [shadow property](https://docs.microsoft.com/ef/core/modeling/shadow-properties ).</span></span> <span data-ttu-id="8b619-145">Ponieważ konfiguracja służąca do ukrywania identyfikatora w modelu jest skonfigurowana na poziomie infrastruktury EF, byłby on rodzaj przezroczysty dla modelu domeny.</span><span class="sxs-lookup"><span data-stu-id="8b619-145">Since that configuration for hiding the ID in the model is set up in the EF infrastructure level, it would be kind of transparent for your domain model.</span></span>

<span data-ttu-id="8b619-146">W początkowej wersji programu eShopOnContainers (.NET Core 1,1) ukryty identyfikator, który jest wymagany przez EF Core infrastrukturę, został zaimplementowany w następujący sposób na poziomie DbContext, przy użyciu interfejsu API Fluent w projekcie infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="8b619-146">In the initial version of eShopOnContainers (.NET Core 1.1), the hidden ID needed by EF Core infrastructure was implemented in the following way in the DbContext level, using Fluent API at the infrastructure project.</span></span> <span data-ttu-id="8b619-147">W związku z tym, identyfikator został ukryty z punktu modelu domeny w widoku, ale wciąż występuje w infrastrukturze.</span><span class="sxs-lookup"><span data-stu-id="8b619-147">Therefore, the ID was hidden from the domain model point of view, but still present in the infrastructure.</span></span>

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

<span data-ttu-id="8b619-148">Jednak trwałość tego obiektu wartości do bazy danych była przeprowadzona jak zwykła jednostka w innej tabeli.</span><span class="sxs-lookup"><span data-stu-id="8b619-148">However, the persistence of that value object into the database was performed like a regular entity in a different table.</span></span>

<span data-ttu-id="8b619-149">W EF Core 2,0 istnieją nowe i lepsze metody utrwalania obiektów wartości.</span><span class="sxs-lookup"><span data-stu-id="8b619-149">With EF Core 2.0, there are new and better ways to persist value objects.</span></span>

## <a name="persist-value-objects-as-owned-entity-types-in-ef-core-20"></a><span data-ttu-id="8b619-150">Utrwalaj obiekty wartości jako należące do nich typy jednostek w EF Core 2,0</span><span class="sxs-lookup"><span data-stu-id="8b619-150">Persist value objects as owned entity types in EF Core 2.0</span></span>

<span data-ttu-id="8b619-151">Nawet w przypadku niektórych luk między wzorcem obiektu wartości kanonicznych w DDD i typ jednostki należącej do EF Core, obecnie najlepszym sposobem utrwalania obiektów wartości jest EF Core 2,0.</span><span class="sxs-lookup"><span data-stu-id="8b619-151">Even with some gaps between the canonical value object pattern in DDD and the owned entity type in EF Core, it's currently the best way to persist value objects with EF Core 2.0.</span></span> <span data-ttu-id="8b619-152">Ograniczenia można zobaczyć na końcu tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="8b619-152">You can see limitations at the end of this section.</span></span>

<span data-ttu-id="8b619-153">Funkcja typu jednostki będąca własnością została dodana do EF Core od wersji 2,0.</span><span class="sxs-lookup"><span data-stu-id="8b619-153">The owned entity type feature was added to EF Core since version 2.0.</span></span>

<span data-ttu-id="8b619-154">Typ jednostki będącej właścicielem umożliwia mapowanie typów, które nie mają własnej tożsamości jawnie zdefiniowanej w modelu domeny i są używane jako właściwości, takie jak obiekt wartości, w ramach dowolnych jednostek.</span><span class="sxs-lookup"><span data-stu-id="8b619-154">An owned entity type allows you to map types that do not have their own identity explicitly defined in the domain model and are used as properties, such as a value object, within any of your entities.</span></span> <span data-ttu-id="8b619-155">Typ jednostki będącej własnością ma udział tego samego typu CLR z innym typem jednostki (to jest tylko zwykła Klasa).</span><span class="sxs-lookup"><span data-stu-id="8b619-155">An owned entity type shares the same CLR type with another entity type (that is, it’s just a regular class).</span></span> <span data-ttu-id="8b619-156">Jednostką zawierającą zdefiniowaną nawigację jest obiektem będącym właścicielem.</span><span class="sxs-lookup"><span data-stu-id="8b619-156">The entity containing the defining navigation is the owner entity.</span></span> <span data-ttu-id="8b619-157">Podczas wykonywania zapytania dotyczącego właściciela typy posiadane są domyślnie uwzględniane.</span><span class="sxs-lookup"><span data-stu-id="8b619-157">When querying the owner, the owned types are included by default.</span></span>

<span data-ttu-id="8b619-158">Po prostu, patrząc na model domeny, typ własnością wygląda podobnie do tego, że nie ma żadnej tożsamości.</span><span class="sxs-lookup"><span data-stu-id="8b619-158">Just by looking at the domain model, an owned type looks like it doesn’t have any identity.</span></span> <span data-ttu-id="8b619-159">Jednakże, w obszarze okładek, typy posiadane mają tożsamość, ale właściwość nawigacji właściciela jest częścią tej tożsamości.</span><span class="sxs-lookup"><span data-stu-id="8b619-159">However, under the covers, owned types do have identity, but the owner navigation property is part of this identity.</span></span>

<span data-ttu-id="8b619-160">Tożsamość wystąpień posiadanych typów nie jest całkowicie własna.</span><span class="sxs-lookup"><span data-stu-id="8b619-160">The identity of instances of owned types is not completely their own.</span></span> <span data-ttu-id="8b619-161">Składa się z trzech składników:</span><span class="sxs-lookup"><span data-stu-id="8b619-161">It consists of three components:</span></span>

- <span data-ttu-id="8b619-162">Tożsamość właściciela</span><span class="sxs-lookup"><span data-stu-id="8b619-162">The identity of the owner</span></span>

- <span data-ttu-id="8b619-163">Właściwość nawigacji wskazująca na siebie</span><span class="sxs-lookup"><span data-stu-id="8b619-163">The navigation property pointing to them</span></span>

- <span data-ttu-id="8b619-164">W przypadku kolekcji typów posiadanych, składnik niezależny (nie jest jeszcze obsługiwany w EF Core 2,0, w dniu 2,2).</span><span class="sxs-lookup"><span data-stu-id="8b619-164">In the case of collections of owned types, an independent component (not yet supported in EF Core 2.0, coming up on 2.2).</span></span>

<span data-ttu-id="8b619-165">Na przykład w modelu domeny uporządkowanej pod adresem eShopOnContainers, jako część jednostki Order, obiekt wartości adresu jest implementowany jako typ jednostki należącej do jednostki właściciela, która jest jednostką Order.</span><span class="sxs-lookup"><span data-stu-id="8b619-165">For example, in the Ordering domain model at eShopOnContainers, as part of the Order entity, the Address value object is implemented as an owned entity type within the owner entity, which is the Order entity.</span></span> <span data-ttu-id="8b619-166">Adres jest typem bez właściwości Identity zdefiniowanej w modelu domeny.</span><span class="sxs-lookup"><span data-stu-id="8b619-166">Address is a type with no identity property defined in the domain model.</span></span> <span data-ttu-id="8b619-167">Jest ona używana jako właściwość typu zamówienia, aby określić adres wysyłkowy dla konkretnej kolejności.</span><span class="sxs-lookup"><span data-stu-id="8b619-167">It is used as a property of the Order type to specify the shipping address for a particular order.</span></span>

<span data-ttu-id="8b619-168">Według Konwencji klucz podstawowy w tle jest tworzony dla typu posiadanego i zostanie zamapowany do tej samej tabeli co właściciel przy użyciu dzielenia tabeli.</span><span class="sxs-lookup"><span data-stu-id="8b619-168">By convention, a shadow primary key is created for the owned type and it will be mapped to the same table as the owner by using table splitting.</span></span> <span data-ttu-id="8b619-169">Pozwala to na używanie typów posiadanych w sposób podobny do tego, jak złożone typy są używane w EF6 w tradycyjnych .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8b619-169">This allows to use owned types similarly to how complex types are used in EF6 in the traditional .NET Framework.</span></span>

<span data-ttu-id="8b619-170">Należy pamiętać, że typy posiadane nigdy nie są wykrywane przez Konwencję w EF Core, więc należy zadeklarować je jawnie.</span><span class="sxs-lookup"><span data-stu-id="8b619-170">It is important to note that owned types are never discovered by convention in EF Core, so you have to declare them explicitly.</span></span>

<span data-ttu-id="8b619-171">W eShopOnContainers, w OrderingContext.cs w ramach metody OnModelCreating (), jest stosowana wiele konfiguracji infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="8b619-171">In eShopOnContainers, at the OrderingContext.cs, within the OnModelCreating() method, there are multiple infrastructure configuration being applied.</span></span> <span data-ttu-id="8b619-172">Jeden z nich jest powiązany z jednostką Order.</span><span class="sxs-lookup"><span data-stu-id="8b619-172">One of them is related to the Order entity.</span></span>

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

<span data-ttu-id="8b619-173">W poniższym kodzie infrastruktura trwałości jest definiowana dla jednostki Order:</span><span class="sxs-lookup"><span data-stu-id="8b619-173">In the following code, the persistence infrastructure is defined for the Order entity:</span></span>

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

<span data-ttu-id="8b619-174">W poprzednim kodzie Metoda `orderConfiguration.OwnsOne(o => o.Address)` określa, że właściwość `Address` jest obiektem należącym do typu `Order`.</span><span class="sxs-lookup"><span data-stu-id="8b619-174">In the previous code, the `orderConfiguration.OwnsOne(o => o.Address)` method specifies that the `Address` property is an owned entity of the `Order` type.</span></span>

<span data-ttu-id="8b619-175">Domyślnie konwencje EF Core nazywają kolumny bazy danych dla właściwości typu jednostki będącej własnością, jako `EntityProperty_OwnedEntityProperty`.</span><span class="sxs-lookup"><span data-stu-id="8b619-175">By default, EF Core conventions name the database columns for the properties of the owned entity type as `EntityProperty_OwnedEntityProperty`.</span></span> <span data-ttu-id="8b619-176">W związku z tym właściwości wewnętrzne `Address` będą wyświetlane w tabeli `Orders` z nazwami `Address_Street`, `Address_City` (itd. dla `State`, `Country` i `ZipCode`).</span><span class="sxs-lookup"><span data-stu-id="8b619-176">Therefore, the internal properties of `Address` will appear in the `Orders` table with the names `Address_Street`, `Address_City` (and so on for `State`, `Country` and `ZipCode`).</span></span>

<span data-ttu-id="8b619-177">Możesz dołączyć metodę `Property().HasColumnName()` Fluent, aby zmienić nazwy tych kolumn.</span><span class="sxs-lookup"><span data-stu-id="8b619-177">You can append the `Property().HasColumnName()` fluent method to rename those columns.</span></span> <span data-ttu-id="8b619-178">W przypadku, gdy `Address` jest właściwością publiczną, mapowania byłyby podobne do następujących:</span><span class="sxs-lookup"><span data-stu-id="8b619-178">In the case where `Address` is a public property, the mappings would be like the following:</span></span>

```csharp
orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.Street).HasColumnName("ShippingStreet");

orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.City).HasColumnName("ShippingCity");
```

<span data-ttu-id="8b619-179">Istnieje możliwość łańcucha metody `OwnsOne` w ramach mapowania Fluent.</span><span class="sxs-lookup"><span data-stu-id="8b619-179">It is possible to chain the `OwnsOne` method in a fluent mapping.</span></span> <span data-ttu-id="8b619-180">W poniższym hipotetycznym przykładzie `OrderDetails` są własnością `BillingAddress` i `ShippingAddress`, które są oba typy `Address`.</span><span class="sxs-lookup"><span data-stu-id="8b619-180">In the following hypothetical example, `OrderDetails` owns `BillingAddress` and `ShippingAddress`, which are both `Address` types.</span></span> <span data-ttu-id="8b619-181">A następnie `OrderDetails` należy do typu `Order`.</span><span class="sxs-lookup"><span data-stu-id="8b619-181">Then `OrderDetails` is owned by the `Order` type.</span></span>

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

### <a name="additional-details-on-owned-entity-types"></a><span data-ttu-id="8b619-182">Dodatkowe szczegóły dotyczące typów jednostek posiadanych</span><span class="sxs-lookup"><span data-stu-id="8b619-182">Additional details on owned entity types</span></span>

- <span data-ttu-id="8b619-183">Typy posiadane są definiowane podczas konfigurowania właściwości nawigacji do określonego typu przy użyciu interfejsu API Fluent OwnsOne.</span><span class="sxs-lookup"><span data-stu-id="8b619-183">Owned types are defined when you configure a navigation property to a particular type using the OwnsOne fluent API.</span></span>

- <span data-ttu-id="8b619-184">Definicja typu będącego właścicielem w naszym modelu metadanych jest złożona z: typu właściciela, właściwości nawigacji i typu CLR typu będącego własnością.</span><span class="sxs-lookup"><span data-stu-id="8b619-184">The definition of an owned type in our metadata model is a composite of: the owner type, the navigation property, and the CLR type of the owned type.</span></span>

- <span data-ttu-id="8b619-185">Tożsamość (klucz) wystąpienia należącego do typu w naszym stosie to złożona tożsamość typu właściciela i definicja typu będącego własnością.</span><span class="sxs-lookup"><span data-stu-id="8b619-185">The identity (key) of an owned type instance in our stack is a composite of the identity of the owner type and the definition of the owned type.</span></span>

#### <a name="owned-entities-capabilities"></a><span data-ttu-id="8b619-186">Możliwości jednostek należących do firmy:</span><span class="sxs-lookup"><span data-stu-id="8b619-186">Owned entities capabilities:</span></span>

- <span data-ttu-id="8b619-187">Typy posiadane mogą odwoływać się do innych jednostek, należących do (zagnieżdżonych typów będących własnością) lub nienależących do siebie (regularne właściwości nawigacji odwołań do innych jednostek).</span><span class="sxs-lookup"><span data-stu-id="8b619-187">Owned types can reference other entities, either owned (nested owned types) or non-owned (regular reference navigation properties to other entities).</span></span>

- <span data-ttu-id="8b619-188">Można mapować ten sam typ środowiska CLR jako różne typy należące do tej samej jednostki właściciela za pomocą oddzielnych właściwości nawigacji.</span><span class="sxs-lookup"><span data-stu-id="8b619-188">You can map the same CLR type as different owned types in the same owner entity through separate navigation properties.</span></span>

- <span data-ttu-id="8b619-189">Podział tabeli jest konfiguracją według Konwencji, ale można zrezygnować z mapowania typu należącego do innej tabeli przy użyciu ToTable.</span><span class="sxs-lookup"><span data-stu-id="8b619-189">Table splitting is setup by convention, but you can opt out by mapping the owned type to a different table using ToTable.</span></span>

- <span data-ttu-id="8b619-190">Ładowanie eager jest wykonywane automatycznie w typach posiadanych, tzn. nie ma potrzeby wywoływania dyrektywy include () w zapytaniu.</span><span class="sxs-lookup"><span data-stu-id="8b619-190">Eager loading is performed automatically on owned types, i.e. no need to call Include() on the query.</span></span>

- <span data-ttu-id="8b619-191">Można skonfigurować z atrybutami \[własnością\], w EF Core 2,1</span><span class="sxs-lookup"><span data-stu-id="8b619-191">Can be configured with attribute \[Owned\], as of EF Core 2.1</span></span>

#### <a name="owned-entities-limitations"></a><span data-ttu-id="8b619-192">Ograniczenia jednostek będących własnością:</span><span class="sxs-lookup"><span data-stu-id="8b619-192">Owned entities limitations:</span></span>

- <span data-ttu-id="8b619-193">Nie można utworzyć Nieogólnymi\<T\> należącego do typu (zgodnie z projektem).</span><span class="sxs-lookup"><span data-stu-id="8b619-193">You cannot create a DbSet\<T\> of an owned type (by design).</span></span>

- <span data-ttu-id="8b619-194">Nie można wywołać metody element modelbuilder. Entity\<T\>() dla typów posiadanych (obecnie według projektu).</span><span class="sxs-lookup"><span data-stu-id="8b619-194">You cannot call ModelBuilder.Entity\<T\>() on owned types (currently by design).</span></span>

- <span data-ttu-id="8b619-195">Nie ma jeszcze kolekcji posiadanych typów (w EF Core 2,1, ale będą one obsługiwane w 2,2).</span><span class="sxs-lookup"><span data-stu-id="8b619-195">No collections of owned types yet (as of EF Core 2.1, but they will be supported in 2.2).</span></span>

- <span data-ttu-id="8b619-196">Brak obsługi opcjonalnych (dopuszczających wartości null) typów, które są mapowane przy użyciu właściciela w tej samej tabeli (tj. przy użyciu dzielenia tabeli).</span><span class="sxs-lookup"><span data-stu-id="8b619-196">No support for optional (that is, nullable) owned types that are mapped with the owner in the same table (i.e. using table splitting).</span></span> <span data-ttu-id="8b619-197">Wynika to z faktu, że mapowanie jest wykonywane dla każdej właściwości. nie mamy oddzielnej kontrolki dla wartości złożonej o wartości null a jako całości.</span><span class="sxs-lookup"><span data-stu-id="8b619-197">This is because mapping is done for each property, we don't have a separate sentinel for the null complex value a as whole.</span></span>

- <span data-ttu-id="8b619-198">Brak obsługi mapowania dziedziczenia dla typów posiadanych, ale powinno być możliwe mapowanie dwóch typów liści tych samych hierarchii dziedziczenia co różne typy należące do użytkownika.</span><span class="sxs-lookup"><span data-stu-id="8b619-198">No inheritance mapping support for owned types, but you should be able to map two leaf types of the same inheritance hierarchies as different owned types.</span></span> <span data-ttu-id="8b619-199">EF Core nie będzie przyczyną faktu, że są one częścią tej samej hierarchii.</span><span class="sxs-lookup"><span data-stu-id="8b619-199">EF Core will not reason about the fact that they are part of the same hierarchy.</span></span>

#### <a name="main-differences-with-ef6s-complex-types"></a><span data-ttu-id="8b619-200">Główne różnice w EF6's typach złożonych</span><span class="sxs-lookup"><span data-stu-id="8b619-200">Main differences with EF6's complex types</span></span>

- <span data-ttu-id="8b619-201">Dzielenie tabeli jest opcjonalne, tzn. mogą być opcjonalnie mapowane do oddzielnej tabeli i nadal są typami własnością.</span><span class="sxs-lookup"><span data-stu-id="8b619-201">Table splitting is optional, i.e. they can optionally be mapped to a separate table and still be owned types.</span></span>

- <span data-ttu-id="8b619-202">Mogą odwoływać się do innych jednostek (tj. mogą działać jako strona zależna od relacji z innymi typami niebędącymi własnością).</span><span class="sxs-lookup"><span data-stu-id="8b619-202">They can reference other entities (i.e. they can act as the dependent side on relationships to other non-owned types).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="8b619-203">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="8b619-203">Additional resources</span></span>

- <span data-ttu-id="8b619-204">**Fowlera Martin. Wartość wzorca wartościobject** </span><span class="sxs-lookup"><span data-stu-id="8b619-204">**Martin Fowler. ValueObject pattern** </span></span>\
  <https://martinfowler.com/bliki/ValueObject.html>

- <span data-ttu-id="8b619-205">**Eric Evans. Projektowanie oparte na domenie: zapełnianie złożoności w oprogramowaniu.**</span><span class="sxs-lookup"><span data-stu-id="8b619-205">**Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software.**</span></span> <span data-ttu-id="8b619-206">(Książka; zawiera omówienie obiektów wartości) </span><span class="sxs-lookup"><span data-stu-id="8b619-206">(Book; includes a discussion of value objects) </span></span>\
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

- <span data-ttu-id="8b619-207">**Vaughn Vernon. Implementowanie projektu opartego na domenie.**</span><span class="sxs-lookup"><span data-stu-id="8b619-207">**Vaughn Vernon. Implementing Domain-Driven Design.**</span></span> <span data-ttu-id="8b619-208">(Książka; zawiera omówienie obiektów wartości) </span><span class="sxs-lookup"><span data-stu-id="8b619-208">(Book; includes a discussion of value objects) </span></span>\
  <https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/>

- <span data-ttu-id="8b619-209">**Właściwości cienia** </span><span class="sxs-lookup"><span data-stu-id="8b619-209">**Shadow Properties** </span></span>\
  [https://docs.microsoft.com/ef/core/modeling/shadow-properties](/ef/core/modeling/shadow-properties)

- <span data-ttu-id="8b619-210">**Typy złożone i/lub obiekty wartości**.</span><span class="sxs-lookup"><span data-stu-id="8b619-210">**Complex types and/or value objects**.</span></span> <span data-ttu-id="8b619-211">Dyskusje w repozytorium EF Core GitHub (karta problemy) </span><span class="sxs-lookup"><span data-stu-id="8b619-211">Discussion in the EF Core GitHub repo (Issues tab) </span></span>\
  <https://github.com/aspnet/EntityFramework/issues/246>

- <span data-ttu-id="8b619-212">**ValueObject.cs.**</span><span class="sxs-lookup"><span data-stu-id="8b619-212">**ValueObject.cs.**</span></span> <span data-ttu-id="8b619-213">Klasa obiektu wartości podstawowej w eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="8b619-213">Base value object class in eShopOnContainers.</span></span> \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs>

- <span data-ttu-id="8b619-214">**Klasa adresu.**</span><span class="sxs-lookup"><span data-stu-id="8b619-214">**Address class.**</span></span> <span data-ttu-id="8b619-215">Klasa przykładowych obiektów wartości w eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="8b619-215">Sample value object class in eShopOnContainers.</span></span> \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs>

> [!div class="step-by-step"]
> <span data-ttu-id="8b619-216">[Poprzedni](seedwork-domain-model-base-classes-interfaces.md)
> [dalej](enumeration-classes-over-enum-types.md)</span><span class="sxs-lookup"><span data-stu-id="8b619-216">[Previous](seedwork-domain-model-base-classes-interfaces.md)
[Next](enumeration-classes-over-enum-types.md)</span></span>

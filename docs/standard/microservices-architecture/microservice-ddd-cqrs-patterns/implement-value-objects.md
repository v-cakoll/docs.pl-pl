---
title: Implementowanie obiektów wartości
description: Architektura Mikrousług .NET konteneryzowanych aplikacji .NET | Pobierz szczegóły i funkcje umożliwiające implementowanie obiektów wartości przy użyciu nowych funkcji programu Entity Framework.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/08/2018
ms.openlocfilehash: c17bc036517b5437c5ca20abf8a8e3a37ccb6d2c
ms.sourcegitcommit: 7156c0b9e4ce4ce5ecf48ce3d925403b638b680c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/26/2019
ms.locfileid: "58463920"
---
# <a name="implement-value-objects"></a>Implementowanie obiektów wartości

Zgodnie z opisem we wcześniejszych sekcjach dotyczących jednostek i agregacji, tożsamość ma zasadnicze znaczenie dla jednostki. Istnieją jednak wiele obiektów i elementów danych w systemie, które nie wymagają usługi tożsamości i tożsamości, śledzenie, takie jak obiekty wartości.

Obiekt wartości można odwoływać się do innych jednostek. Na przykład w aplikacji, która generuje trasę, która opisuje, jak można uzyskać z jednego miejsca do innego tej trasy będzie obiektu wartości. Byłoby migawek punktów na określoną trasę, ale ta trasa sugerowane nie miałoby tożsamości, mimo że wewnętrznie go, może odnosić się do jednostek, takich jak miasto, drogi itp.

Rysunek 7-13 przedstawiono obiektu wartość adresu w agregacji zamówienia.

![Wartość adresu — obiekt wewnątrz agregacji zamówienia.](./media/image14.png)

**Rysunek 7-13**. Adres obiektu wartości w kolejności agregacji

Jak pokazano w rysunek 7-13, jednostki zwykle składa się z wielu atrybutów. Na przykład `Order` jednostki mogą być modelowane jako jednostki przy użyciu tożsamości i wewnętrznie składa się z zestawu atrybutów, takich jak OrderId OrderDate, OrderItems itp. Ale adresu, który jest po prostu złożone wartością, składa się z kraju, ulicy, Miasto itp. i ma Brak tożsamości w tej domenie, musi być modelowane i traktowane jako obiekt wartości.

## <a name="important-characteristics-of-value-objects"></a>Istotne cechy obiektów wartości

Istnieją dwa główne właściwości dla obiektów wartości:

- Mają one nie tożsamości.

- Są niezmienne.

Charakterystyka pierwszy już został omówiony. Niezmienność jest ważne wymagania. Po utworzeniu obiektu musi być niezmienialne wartości obiektu wartości. W związku z tym gdy obiekt jest konstruowany, należy podać wartości wymagane, ale nie muszą umożliwiać mu zmiany w okresie istnienia obiektu.

Obiekty wartości umożliwiają wykonywanie niektórych wskazówki wydajność dzięki natury niezmienne. Jest to szczególnie istotne w systemach w przypadku, gdy może być tysiące wartości wystąpienia obiektów, z których wiele ma takie same wartości. Natury niezmienne umożliwia ich ponowne użycie; wymienne obiekty mogą być ich wartości są takie same, ponieważ mają one nie tożsamości. Tego rodzaju optymalizacji, czasami mogą się przyczynić między oprogramowania, który działa wolno i dobrą wydajność. Oczywiście wszystkich tych przypadkach są zależne od aplikacji środowiska i kontekstu wdrożenia.

## <a name="value-object-implementation-in-c"></a>Wartość obiektu wdrożenia w języku C\#

Pod względem implementacji może mieć klasy podstawowej obiektu wartość, która zawiera podstawowe narzędzia metod, takich jak na podstawie porównania między wszystkie atrybuty (ponieważ jest to obiekt wartości nie muszą być oparte na tożsamości) oraz innych podstawowych charakterystyk równości. Poniższy przykład pokazuje wartość obiektu klasy bazowej, używane w szeregowania mikrousługi w ramach aplikacji eShopOnContainers.

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

Za pomocą tej klasy podczas implementowania rzeczywistej wartości obiektu, jak pokazano w poniższym przykładzie obiekt wartości adresów:

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

Możesz zobaczyć, jak ta implementacja obiektu wartość adresu ma, Brak tożsamości, a w związku z tym, żadne pole ID, ani w klasie adres, nawet w klasie ValueObject.

Nie było możliwe o żadne pole Identyfikatora w klasie, który będzie używany przez Entity Framework, dopóki programu EF Core 2.0, co pozwala znacznie lepiej zaimplementować wartość obiekty nie identyfikatorem To dokładnie wyjaśnienie w następnej sekcji.

Można utrzymywał, że obiekty wartości, są niezmienne, powinny być tylko do odczytu (czyli get tylko właściwości), i który jest rzeczywiście. Jednak wartość jest zazwyczaj serializacji i deserializacji za pośrednictwem kolejki komunikatów i jest tylko do odczytu zatrzymuje Deserializator przypisywaniu wartości, więc po prostu pozostawimy je jako zestaw prywatny, który jest tylko do odczytu, wystarczająco przydatne.

## <a name="how-to-persist-value-objects-in-the-database-with-ef-core-20"></a>Jak zachować wartość obiektów w bazie danych przy użyciu programu EF Core 2.0

Możesz już wiesz, jak zdefiniować obiekt wartości w modelu domeny. Ale jak może faktycznie powiedzmy go do bazy danych za pośrednictwem podstawowych Entity Framework (EF), która zwykle jest przeznaczony dla jednostek o tożsamości?

### <a name="background-and-older-approaches-using-ef-core-11"></a>Tło i starszych metod przy użyciu programu EF Core 1.1

Jako tła, ograniczenie, w przypadku korzystania z programów EF Core 1.0 i 1.1 został może nie używać [typy złożone](xref:System.ComponentModel.DataAnnotations.Schema.ComplexTypeAttribute) zgodnie z definicją w programie EF w tradycyjnych .NET Framework w wersji 6.x. W związku z tym przy użyciu programu EF Core 1.0 i 1.1, potrzebna do przechowywania wartości obiektu jako jednostki EF o pole Identyfikatora. Następnie, dzięki czemu będzie wyglądał bardziej jak obiekt wartości przy użyciu tożsamości nie, można ukryć jego Identyfikatora, dzięki czemu można wyjaśnić, że tożsamość obiektu wartości nie jest ważna w modelu domeny. Ten identyfikator można ukryć za pomocą Identyfikatora jako [w tle właściwość](https://docs.microsoft.com/ef/core/modeling/shadow-properties ). Ponieważ ten ukrywania identyfikator modelu jest skonfigurowany na poziomie infrastruktury EF, byłoby rodzaju przezroczyste dla modelu domeny.

W wersji początkowej w ramach aplikacji eShopOnContainers (.NET Core 1.1) identyfikator ukryte wymagane przez infrastrukturę programu EF Core została zaimplementowana w następujący sposób na poziomie kontekstu DbContext przy użyciu interfejsu API Fluent w projekcie infrastruktury. W związku z tym identyfikator został ukryty z punktu widzenia modelu domeny, ale nadal znajdują się w ramach infrastruktury.

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

Jednak trwałości wartość obiektu do bazy danych została wykonana jak regularne jednostki w innej tabeli.

Przy użyciu programu EF Core 2.0, są nowe i lepsze sposoby utrwalania obiektów wartości.

## <a name="persist-value-objects-as-owned-entity-types-in-ef-core-20"></a>Utrwalanie obiekty wartości jako posiadane typy jednostek w programie EF Core 2.0

Nawet w przypadku niektórych luki między wzorzec object canonical wartość w DDD i typ jednostki należące do firmy w wersji EF Core jest obecnie najlepszym sposobem, aby utrwalić obiekty wartości przy użyciu programu EF Core 2.0. Możesz zobaczyć ograniczenia na końcu tej sekcji.

Funkcja Typ jednostki należące do firmy został dodany do programu EF Core od wersji 2.0.

Typ jednostki należące do firmy umożliwia mapowanie typów, które nie mają własnej tożsamości jawnie zdefiniowany w modelu domeny i są używane jako właściwości, takie jak obiekt wartości w ramach danej jednostki. Typ jednostki należące do firmy udostępni inny typ jednostki tego samego typu CLR (czyli jest zwykłej klasy). Obiekt zawierający definiujące nawigacji to jednostka właściciela. Podczas wykonywania zapytania właściciela, typy należące do firmy są domyślnie dołączone.

Po prostu patrząc na model domeny, typem należące do firmy wygląda na to nie ma żadnych tożsamości. Jednak dzieje się w tle, posiadane typy mają tożsamości, ale właściwość nawigacji właściciel jest częścią tej tożsamości.

Tożsamość wystąpień typów należące do firmy, nie jest całkowicie swoje własne. Składa się z trzech składników:

- Tożsamość właściciela

- Właściwość nawigacji, wskazując je

- W przypadku kolekcji typów będących własnością, niezależnie od składnika (nie są jeszcze obsługiwane w programie EF Core 2.0, pojawi się na 2.2).

Na przykład w modelu domeny porządkowanie w ramach aplikacji eShopOnContainers jednostce zamówienia w ramach obiektu wartość adresu jest implementowany jako typ jednostki należące do firmy w ramach jednostki właściciela, czyli jednostki zamówienia. Adres jest typu z żadnej właściwości tożsamości zdefiniowanych w modelu domeny. Aby określić adres wysyłkowy dla określonej kolejności służy jako właściwość typu zamówienia.

Zgodnie z Konwencją klucz podstawowy w tle jest tworzony dla typu należące do firmy i będzie można zamapować na tej samej tabeli jako właściciel przy użyciu dzielenie tabeli. Dzięki temu Użyj należące do typów podobnie jak złożonych typów są używane w EF6 tradycyjnych .NET Framework.

Należy pamiętać, że że należące do typów nigdy nie są wykrywane przez Konwencję w programie EF Core, więc trzeba je zadeklarować jawnie.

W ramach aplikacji eShopOnContainers u OrderingContext.cs, w metodzie OnModelCreating() istnieje wiele konfiguracji infrastruktury, które są stosowane. Jeden z nich jest powiązany z jednostką zamówienia.

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

W poniższym kodzie infrastruktury trwałości jest zdefiniowany dla jednostki zamówienia:

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

W poprzednim kodzie `orderConfiguration.OwnsOne(o => o.Address)` Metoda określa, że `Address` właściwość jest własnością jednostki `Order` typu.

Domyślnie, konwencje programu EF Core nazwę kolumny bazy danych dla właściwości typu jednostki należące do firmy, co `EntityProperty_OwnedEntityProperty`. W związku z tym, wewnętrzny właściwości `Address` pojawi się w `Orders` tabel o nazwach `Address_Street`, `Address_City` (i tak dalej dla `State`, `Country` i `ZipCode`).

Możesz dołączyć `Property().HasColumnName()` fluent metodę, aby zmienić nazwę kolumny. W przypadku których `Address` jest właściwością publiczną mapowania będzie następujący:

```csharp
orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.Street).HasColumnName("ShippingStreet");

orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.City).HasColumnName("ShippingCity");
```

Istnieje możliwość łańcucha `OwnsOne` metody w mapowaniu fluent. W poniższym przykładzie hipotetyczny `OrderDetails` właścicielem `BillingAddress` i `ShippingAddress`, które są zarówno `Address` typów. Następnie `OrderDetails` jest własnością `Order` typu.

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

### <a name="additional-details-on-owned-entity-types"></a>Więcej informacji na temat posiadane typy jednostek

- Posiadane typy są definiowane podczas konfigurowania właściwości nawigacji do określonego typu przy użyciu interfejsu API fluent OwnsOne.

- Definicja typu należące do firmy w naszym modelu metadanych jest złożone z: Typ właściciela, właściwość nawigacji i typ CLR tego typu należące do firmy.

- Tożsamość (klucz) wystąpienia typu należących do naszego stosu jest złożone tożsamości typu właściciela i definicji typu należące do firmy.

#### <a name="owned-entities-capabilities"></a>Funkcje jednostki należące do firmy:

- Posiadane typy mogą odwoływać się inne jednostki, albo właścicielem (zagnieżdżone typy należące do firmy) lub należących do firmy (właściwości nawigacji regularne odwołania do innych jednostek).

- Można mapować tego samego typu CLR jako różne typy należące do firmy w tej samej jednostki właściciel za pośrednictwem właściwości nawigacji oddzielne.

- Dzielenie tabeli została skonfigurowana zgodnie z Konwencją, ale możesz zrezygnować z przez mapowanie typu należące do innej tabeli przy użyciu ToTable.

- Wczesne ładowanie odbywa się automatycznie w typach należące do firmy, czyli nie trzeba wywoływać include() — na tym zapytaniu.

- Można skonfigurować za pomocą atrybutu \[posiadane\], zgodnie z programem EF Core 2.1

#### <a name="owned-entities-limitations"></a>Ograniczenia jednostki należące do firmy:

- Nie można utworzyć DbSet\<T\> typu należące do firmy (według projektu).

- Nie można wywołać ModelBuilder.Entity\<T\>() dla typów należące do firmy (obecnie według projektu).

- Nie kolekcji typów będących własnością jeszcze (począwszy od programu EF Core 2.1, ale będą obsługiwane w 2.2).

- Brak obsługi opcjonalne (oznacza to, dopuszczającego wartość null) należące do typów, które są mapowane z właścicielem w tej samej tabeli (np. za pomocą dzielenia tabeli). Jest to spowodowane mapowanie jest wykonywane dla każdej właściwości, nie mamy oddzielne wartownik zawiera wartości null dla złożonych jako całego.

- Brak obsługi mapowania dziedziczenia należące do typów, ale powinno być możliwe do mapowania dwa typy tej samej hierarchii dziedziczenia w jako należących do różnego typu liść. EF Core nie będzie przyczyny o tym, że są one częścią tej samej hierarchii.

#### <a name="main-differences-with-ef6s-complex-types"></a>Główne różnice przy użyciu platformy EF6 dla typów złożonych

- Dzielenie tabeli jest opcjonalne, czyli opcjonalnie mogą zostać zmapowane do osobnej tabeli i nadal należeć do typów.

- Mogą odwoływać się do innych jednostek (czyli mogą pełnić zależne side w relacji z innymi typami należących do firmy).

## <a name="additional-resources"></a>Dodatkowe zasoby

- **Martin Fowler. Wzorzec ValueObject** \
  [https://martinfowler.com/bliki/ValueObject.html](https://martinfowler.com/bliki/ValueObject.html)

- **Eric Evans. Projektowania opartego na domenie: Co dzień do czynienia złożoności serce oprogramowania.** (Zarezerwuj; zawiera omówienie obiekty wartości) \
  [https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)

- **Vaughn Vernon. Implementowanie projektu opartego na domenach.** (Zarezerwuj; zawiera omówienie obiekty wartości) \
  [https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)

- **Właściwości w tle** \
  [https://docs.microsoft.com/ef/core/modeling/shadow-properties](https://docs.microsoft.com/ef/core/modeling/shadow-properties)

- **Typy złożone i/lub obiekty wartości**. Dyskusja w repozytorium programu EF Core w witrynie GitHub (karta problemy) \
  [https://github.com/aspnet/EntityFramework/issues/246](https://github.com/aspnet/EntityFramework/issues/246)

- **ValueObject.cs.** Podstawowa klasa obiektu wartości w eShopOnContainers.* * \
  [https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs)

- **Klasy adresów.** Klasa obiektu wartość próbki w ramach aplikacji eShopOnContainers. \
  [https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs)

> [!div class="step-by-step"]
> [Poprzednie](seedwork-domain-model-base-classes-interfaces.md)
> [dalej](enumeration-classes-over-enum-types.md)

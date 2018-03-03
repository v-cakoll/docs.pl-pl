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
ms.openlocfilehash: b10eeff18979674901197203716426af70433c46
ms.sourcegitcommit: ba765893e3efcece67d99fd6d5ce0074b050d1d9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/02/2018
---
# <a name="implementing-value-objects"></a>Implementowanie obiekty wartości

Zgodnie z opisem we wcześniejszych sekcjach jednostek i agreguje informacje tożsamości jest podstawą dla jednostek. Istnieją jednak wiele obiektów i elementy danych w systemie, które nie wymagają tożsamości i tożsamości śledzenia, takich jak obiekty wartości.

Obiekt wartości może się odwoływać inne jednostki. Na przykład w aplikacji, która generuje trasy, który opisuje metodę get z jednego miejsca do innego tej trasy byłoby obiektu wartości. Byłoby migawkę punktów na określoną trasę, ale ta trasa sugerowane nie miałoby tożsamości, mimo że wewnętrznie może dotyczyć jednostek Miasto, drogowej itd.

Rysunek 9-13 przedstawiono obiektu wartości adresu w kolejności agregacji.

![](./media/image14.png)

**Rysunek 9-13**. Adres obiektu wartości w kolejności agregacji

Jak pokazano w rysunek 9-13, jednostki zazwyczaj składa się z wielu atrybutów. Na przykład `Order` jednostki można modelowane jako jednostki o tożsamości i wewnętrznie składa się z zestawu atrybutów, takich jak OrderId OrderDate, OrderItems itp. Ale adresu, który jest po prostu złożona wartość składa się z kraju ulicy, miasta itp. i ma nie tożsamość w tej domenie, musi być modelowane i traktowane jako obiekt wartości.

## <a name="important-characteristics-of-value-objects"></a>Najważniejsze czynniki wartość obiektów

Istnieją dwa główne cechy dla obiektów wartości:

-   Mają one nie tożsamości.

-   Są one niezmienialny.

Pierwszy cech już został omówiony. Immutability musi być spełniony ważne. Wartości obiektu wartości należy modyfikować po utworzeniu obiektu. W związku z tym podczas konstruowania obiektu, należy podać wartości wymagane, ale musi zezwala zmienić okres istnienia obiektu.

Obiekty wartości umożliwiają wykonywanie niektórych lewy wydajności dzięki użyciu natury niezmienialny. Jest to szczególnie istotne w systemach gdzie mogą być tysiące wartość wystąpienia obiektów, z których wiele mają takie same wartości. Natury niezmienne umożliwia ich ponowne użycie; od czasu ich wartości są takie same i mają tożsamości nie mogą być wymienne obiektów. Ten rodzaj optymalizacji czasami wprowadzić różnica między oprogramowaniem dobrą wydajność i oprogramowania, które działa powoli. Oczywiście wszystkich tych przypadkach zależą od środowiska aplikacji i wdrażania kontekstu.

## <a name="value-object-implementation-in-c"></a>Wartość implementacji obiektu w języku C\#

W implementacji może mieć klasy podstawowej obiektu wartość, która ma metody podstawowe narzędzia, takie jak równości na podstawie porównania między wszystkie atrybuty (ponieważ obiektu wartości nie musi być oparta na tożsamości) oraz innych podstawowych właściwości. W poniższym przykładzie przedstawiono wartości obiektu klasy podstawowej, używany w porządkowania mikrousługi z eShopOnContainers.

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

Tej klasy można użyć podczas wykonywania obiekt rzeczywistej wartości, tak jak w przypadku obiektu wartości adresu pokazano w poniższym przykładzie:

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

## <a name="how-to-persist-value-objects-in-the-database-with-ef-core-20"></a>Jak zachować wartości obiektów w bazie danych EF Core 2.0

Widać tylko sposób definiowania obiektu wartości do modelu domeny. Ale, jak można można faktycznie utrwalić go do bazy danych za pośrednictwem Core Entity Framework (EF), która zwykle jest przeznaczony dla jednostek z tożsamością?

### <a name="background-and-older-approaches-using-ef-core-11"></a>Tło i starszych podejścia przy użyciu EF Core 1.1

Jako tło, to ograniczenie, używając EF Core 1.0 i 1.1 został, że nie można użyć [typów złożonych](https://docs.microsoft.com/dotnet/api/system.componentmodel.dataannotations.schema.complextypeattribute?view=netframework-4.7) zgodnie z definicją w EF 6.x w tradycyjnych .NET Framework. W związku z tym jeśli przy użyciu EF Core w wersji 1.0 lub 1.1, potrzebne do przechowywania wartości obiektu jako jednostka EF z pola identyfikator. Następnie tak będzie wyglądał więcej takich jak obiekt wartości przy nie tożsamości, można ukryć jego identyfikator, więc można wyjaśnić, że tożsamość obiektu wartości nie jest ważna w modelu domeny. Ten identyfikator można ukryć przy użyciu Identyfikatora jako [w tle właściwości](https://docs.microsoft.com/ef/core/modeling/shadow-properties ). Ponieważ tego ukrywania identyfikator modelu jest skonfigurowany na poziomie infrastruktury EF, byłoby rodzaj niewidoczny dla modelu domeny.

W pierwotnej wersji eShopOnContainers (.NET Core 1.1) identyfikator ukryte potrzebne w infrastrukturze podstawowej EF został wdrożony w następujący sposób na poziomie typu DbContext w projekcie infrastruktury przy użyciu interfejsu API Fluent. W związku z tym Identyfikatorem była ukrytych z punktu widzenia modelu domeny, lecz nadal znajdują się w infrastrukturze.

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

Jednak trwałości wartość obiektu do bazy danych została wykonana, takie jak regularne jednostki w innej tabeli.

EF Core 2.0, są nowe i lepsze metody, aby utrwalić obiekty wartości.

## <a name="persist-value-objects-as-owned-entity-types-in-ef-core-20"></a>Utrwalanie obiekty wartości jako typy jednostek należące do firmy w programie EF Core 2.0

Nawet w przypadku niektórych luki pomiędzy wzorzec obiektu wartości kanonicznej w DDD i typ należących do jednostki w podstawowej EF obecnie jest najlepszy sposób, aby utrwalić obiekty wartości EF Core 2.0. Widać ograniczenia na końcu tej sekcji.

Funkcja Typ należących do jednostki został dodany do EF Core od wersji 2.0.

Typ jednostki należące do firmy pozwala na mapowanie typów, które nie mają własnych jawnie tożsamości zdefiniowanej w modelu domeny i są używane jako właściwości, takie jak obiekt wartości w żadnej jednostki. Typ jednostki należących do udziałów tego samego typu CLR z innym typem jednostki. Obiekt zawierający definiującego nawigacji jest jednostką właściciela. Podczas wykonywania zapytania właściciela, typy należące do firmy są domyślnie dołączone.

Tylko na podstawie modelu domeny, należących do typu prawdopodobnie nie ma żadnych tożsamości.
Jednak w obszarze obejmuje należących do typów ma tożsamość, ale właściwość nawigacji właściciela jest częścią tej tożsamości.

Tożsamość wystąpienia własnych typów nie jest całkowicie własne. Składa się z trzech składników: 

- Tożsamość właściciela

- Wskazuje właściwość nawigacji

- W przypadku kolekcji należących do typów, niezależnie od składnika (nie jest jeszcze obsługiwane w programie EF Core 2.0).

Na przykład w modelu domeny porządkowanie na eShopOnContainers jako część jednostki kolejności obiekt wartość adres jest zaimplementowany jako typu jednostki należące do firmy w ramach jednostki właściciela, czyli kolejność jednostki. Adres jest typem z ma właściwości tożsamości zdefiniowanej w modelu domeny. Aby określić adres wysyłkowy dla określonej kolejności służy jako właściwość typu kolejności.

Konwencja klucz podstawowy w tle jest tworzony dla typu należące do firmy i będzie on zamapowany do tej samej tabeli jako właściciel przy użyciu dzielenia tabeli. Dzięki temu Użyj należące do typów podobnie jak złożonych typów są używane w EF6 w tradycyjnych .NET Framework.

Należy pamiętać, że który należące do typów nigdy nie są wykrywane przez Konwencję w podstawowej EF, dlatego należy je jawnie deklarować.

W eShopOnContainers w OrderingContext.cs, w metodzie OnModelCreating() istnieje wiele konfiguracji infrastruktury, które są stosowane. Jeden z nich jest powiązany z jednostki kolejności.

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

W poniższym kodzie infrastruktury trwałości jest zdefiniowany dla encji kolejności:

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

W poprzednim kodzie `orderConfiguration.OwnsOne(o => o.Address)` Metoda określa, że `Address` właściwość jest należących do jednostki `Order` typu.

Domyślnie EF podstawowe konwencje nazw kolumn bazy danych dla właściwości typu jednostki należące do firmy jako `EntityProperty_OwnedEntityProperty`. W związku z tym wewnętrzna właściwości `Address` będą wyświetlane w `Orders` tabeli z nazwami `Address_Street`, `Address_City` (i tak dalej dla `State`, `Country` i `ZipCode`).

Możesz dołączyć `Property().HasColumnName()` fluent metody można zmienić nazwy kolumny. W przypadku gdy `Address` jest właściwością publiczną mapowania będzie podobnie do następującej:

```csharp
orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.Street).HasColumnName("ShippingStreet");

orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.City).HasColumnName("ShippingCity");
```

Istnieje możliwość łańcucha `OwnsOne` metody w mapowaniu fluent. W poniższym przykładzie hipotetyczny `OrderDetails` właścicielem `BillingAddress` i `ShippingAddress`, które są oba `Address` typów. Następnie `OrderDetails` jest własnością `Order` typu.

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

### <a name="additional-details-on-owned-entity-types"></a>Więcej informacji na temat typów jednostek należące do firmy

• Należące do typów zdefiniowanych podczas konfigurowania właściwości nawigacji do określonego typu przy użyciu interfejsu API fluent OwnsOne.

• Definicji należących do typu w modelu metadanych jest złożone z: Typ właściciela, właściwość nawigacji i typu CLR typu należące do firmy.

• Tożsamości (klucz) wystąpienia typu należących do naszej stosu jest złożone tożsamości typu właściciela i definicji typu należące do firmy.

#### <a name="owned-entities-capabilities"></a>Należących do podmiotów możliwości:

• Należące do typu może odwoływać się inne jednostki, albo własnością (zagnieżdżone typy należące do firmy) lub będących własnością (właściwości nawigacji odwołania regularnych dla innych jednostek).

• Można mapowania tej samej CLR typu jako różne typy należące do firmy w tej samej jednostki właściciela za pośrednictwem właściwości oddzielne nawigacji.

• Tabeli dzielenia została skonfigurowana przez Konwencję, ale można zrezygnować z przez mapowanie do innej tabeli za pomocą ToTable należących do typu.

• Wczesny ładowania jest realizowane automatycznie należących do typów, tj. nie trzeba wywołać Include() w zapytaniu.

#### <a name="owned-entities-limitations"></a>Jednostek należących do ograniczenia:

• Nie można utworzyć klasę DbSet<T> należących do typu (zgodnie z projektem).

• Nie można wywołać ModelBuilder.Entity<T>() na należących do typów (obecnie zgodnie z projektem).

• Nie kolekcje należące do typów jeszcze (ale zostaną one obsługiwane w wersji po EF Core 2.0).

• Obsługa ich konfiguracji w atrybucie.

• Nie obsługuje dla typów opcjonalne należące do firmy (tj. wartości null), które są mapowane z właścicielem w tej samej tabeli (np. przy użyciu dzielenia tabeli). To dlatego nie mamy oddzielne wartownik dla wartości null.

• Nie obsługuje mapowania dziedziczenia dla typów należące do firmy, ale powinno być możliwe do mapowania dwa typy liścia jako różnych typów należących do tej samej hierarchii dziedziczenia. Podstawowe EF nie będzie przyczyny o tym, że są one częścią tej samej hierarchii.

#### <a name="main-differences-with-ef6s-complex-types"></a>Główne różnice z typów złożonych EF6 firmy

Dzielenie tabeli • jest opcjonalny, tj. Opcjonalnie można mapować do osobnej tabeli i nadal należeć do typów.

• Odwołujących się inne jednostki (tj. mogą pełnić stronie zależnych na relacje z innych typów nie jest właścicielem).


## <a name="additional-resources"></a>Dodatkowe zasoby

-   **Pole Fowler. Wzorzec ValueObject**
    [*https://martinfowler.com/bliki/ValueObject.html*](https://martinfowler.com/bliki/ValueObject.html)

-   **Evans marek. Projektowanie oparte na domenie: Czoła złożoności serca oprogramowania.** (Książki; zawiera omówienie obiekty wartości) [ *https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)

-   **Vaughn Vernon. Implementowanie projektu opartych na domenie.** (Książki; zawiera omówienie obiekty wartości) [ *https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)

-   **Właściwości w tle**
    [*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)

-   **Typy złożone i/lub obiekty wartości**. Omówienie w repozytorium EF Core GitHub (karta problemy) [ *https://github.com/aspnet/EntityFramework/issues/246*](https://github.com/aspnet/EntityFramework/issues/246)

-   **ValueObject.cs.** Wartość podstawową klasy obiektów w eShopOnContainers.
    [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs)

-   **Klasy adresów.** Przykładowe wartości klasy obiektów w eShopOnContainers.
    [*https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs)



>[!div class="step-by-step"]
[Poprzednie] (seedwork-domain-model-base-classes-interfaces.md) [dalej] (wyliczenie klasy over wyliczenia types.md)

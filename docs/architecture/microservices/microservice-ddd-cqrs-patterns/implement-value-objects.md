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
# <a name="implement-value-objects"></a>Implementowanie obiektów wartości

Jak wspomniano we wcześniejszych sekcjach dotyczących jednostek i agregacji, tożsamość jest podstawowa dla jednostek. Jednak istnieje wiele obiektów i elementów danych w systemie, które nie wymagają śledzenia tożsamości i tożsamości, takich jak obiekty wartości.

Obiekt wartości może odwoływać się do innych jednostek. Na przykład w aplikacji, która generuje trasę, która opisuje, jak uzyskać z jednego punktu do drugiego, że trasa będzie obiektwartości. Byłaby to migawka punktów na określonej trasie, ale ta sugerowana trasa nie miałaby tożsamości, mimo że wewnętrznie może odnosić się do podmiotów takich jak Miasto, Droga itp.

Rysunek 7-13 przedstawia obiekt wartość address w zagregowanym zagregowanym zamówieniu.

![Diagram przedstawiający adres wartość-obiekt wewnątrz zagregowane zamówienia.](./media/implement-value-objects/value-object-within-aggregate.png)

**Rysunek 7-13**. Obiekt wartości adresu w zagregowanym zagregowanym zamówieniu

Jak pokazano na rysunku 7-13, jednostka składa się zwykle z wielu atrybutów. Na przykład `Order` jednostka może być modelowana jako jednostka z tożsamością i składa się wewnętrznie z zestawu atrybutów, takich jak OrderId, OrderDate, OrderItems itp. Ale adres, który jest po prostu złożoną wartością składającą się z kraju/regionu, ulicy, miasta itp.

## <a name="important-characteristics-of-value-objects"></a>Ważne cechy obiektów wartości

Istnieją dwie główne cechy obiektów wartości:

- Nie mają tożsamości.

- Są niezmienne.

Pierwsza cecha została już omówiona. Niezmienność jest ważnym wymogiem. Wartości obiektu wartości muszą być niezmienne po utworzeniu obiektu. W związku z tym, gdy obiekt jest konstruowany, należy podać wymagane wartości, ale nie należy zezwalać na ich zmiany w okresie istnienia obiektu.

Value obiektów pozwalają na wykonywanie pewnych sztuczek dla wydajności, dzięki ich niezmiennecharakter. Jest to szczególnie prawdziwe w systemach, w których mogą istnieć tysiące wystąpień obiektu wartości, z których wiele ma te same wartości. Ich niezmienna natura pozwala na ich ponowne wykorzystania; mogą być wymienne obiekty, ponieważ ich wartości są takie same i nie mają tożsamości. Ten typ optymalizacji może czasami zrobić różnicę między oprogramowaniem, które działa wolno, a oprogramowaniem o dobrej wydajności. Oczywiście wszystkie te przypadki zależą od środowiska aplikacji i kontekstu wdrażania.

## <a name="value-object-implementation-in-c"></a>Implementacja obiektu wartości w C\#

Pod względem implementacji może mieć wartość obiektu klasy podstawowej, która ma podstawowe metody narzędzia, takie jak równość na podstawie porównania między wszystkimi atrybutami (ponieważ obiekt wartości nie może być oparty na tożsamości) i inne podstawowe cechy. W poniższym przykładzie przedstawiono wartość obiektu klasy podstawowej używane w mikrousługi porządkowania z eShopOnContainers.

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

Tej klasy można użyć podczas implementowania obiektu wartości rzeczywistej, tak jak w przypadku obiektu wartości Address przedstawionego w poniższym przykładzie:

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

Można zobaczyć, jak ta implementacja obiektu wartości Address nie ma tożsamości i dlatego nie ma pola identyfikatora, ani w Address klasy nawet w ValueObject klasy.

Posiadanie pola identyfikatora w klasie, które ma być używane przez entity framework (EF) nie było możliwe, dopóki EF Core 2.0, co znacznie pomaga zaimplementować obiekty o lepszej wartości bez identyfikatora. To jest właśnie wyjaśnienie następnej sekcji.

Można argumentować, że obiekty wartości, jest niezmienny, powinny być tylko do odczytu (to znaczy mają właściwości get-only), i to jest rzeczywiście prawda. Jednak obiekty wartości są zwykle serializowane i deserializowane, aby przejść przez kolejki komunikatów, a jest tylko do odczytu zatrzymuje deserializator a przypisywanie wartości, więc po prostu pozostawić je jako zestaw prywatny, który jest tylko do odczytu wystarczy, aby być praktyczne.

## <a name="how-to-persist-value-objects-in-the-database-with-ef-core-20-and-later"></a>Jak utrwalić obiekty wartości w bazie danych z EF Core 2.0 i nowszych

Właśnie zobaczyłeś, jak zdefiniować obiekt wartości w modelu domeny. Ale jak można faktycznie utrwalić go do bazy danych przy użyciu entity framework core, ponieważ zwykle dotyczy jednostek z tożsamością?

### <a name="background-and-older-approaches-using-ef-core-11"></a>Podstawowe i starsze podejścia przy użyciu ef core 1.1

Jako tło, ograniczenie podczas korzystania z EF Core 1.0 i 1.1 było to, że nie można użyć [typów złożonych,](xref:System.ComponentModel.DataAnnotations.Schema.ComplexTypeAttribute) zgodnie z definicją w EF 6.x w tradycyjnej platformie .NET Framework. W związku z tym w przypadku korzystania z EF Core 1.0 lub 1.1, należy przechowywać obiekt wartości jako jednostki EF z polem identyfikatora. Następnie, więc wyglądał bardziej jak obiekt wartości bez tożsamości, można ukryć jego identyfikator, dzięki czemu można wyjaśnić, że tożsamość obiektu wartości nie jest ważne w modelu domeny. Można ukryć ten identyfikator przy użyciu identyfikatora jako [właściwości cienia](https://docs.microsoft.com/ef/core/modeling/shadow-properties ). Ponieważ ta konfiguracja do ukrywania identyfikatora w modelu jest skonfigurowana na poziomie infrastruktury EF, byłoby to rodzaj przezroczyste dla modelu domeny.

W początkowej wersji eShopOnContainers (.NET Core 1.1) ukryty identyfikator wymagany przez infrastrukturę EF Core został zaimplementowany w następujący sposób na poziomie DbContext przy użyciu interfejsu API Fluent w projekcie infrastruktury. W związku z tym identyfikator został ukryty z punktu widzenia modelu domeny, ale nadal obecne w infrastrukturze.

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

Jednak trwałość tego obiektu wartości do bazy danych została wykonana jak zwykły jednostki w innej tabeli.

Z EF Core 2.0 i nowszych, istnieją nowe i lepsze sposoby utrwalić wartości obiektów.

## <a name="persist-value-objects-as-owned-entity-types-in-ef-core-20-and-later"></a>Utrwalić obiekty wartości jako typy jednostek należących do EF Core 2.0 i nowszych

Nawet w niektórych odstępach między wzorzec obiektu wartości kanonicznej w DDD i typu jednostki własnością w EF Core, jest obecnie najlepszym sposobem, aby utrwalić wartości obiektów z EF Core 2.0 i nowszych. Możesz zobaczyć ograniczenia na końcu tej sekcji.

Funkcja typu jednostki własnością został dodany do EF Core od wersji 2.0.

Typ jednostki własnością umożliwia mapowanie typów, które nie mają własnej tożsamości jawnie zdefiniowane w modelu domeny i są używane jako właściwości, takie jak obiekt wartości, w dowolnej jednostce. Typ jednostki będącej własnością udostępnia ten sam typ CLR z innym typem jednostki (oznacza to, że jest to zwykła klasa). Encja zawierająca nawigację definiującą jest jednostką właściciela. Podczas wykonywania zapytań do właściciela, należące typy są uwzględniane domyślnie.

Wystarczy spojrzeć na model domeny, typ własnością wygląda na to, że nie ma żadnej tożsamości. Jednak pod przykrywką, owned typy mają tożsamość, ale właściwość nawigacji właściciela jest częścią tej tożsamości.

Tożsamość wystąpień typów należących do nich nie jest całkowicie ich własnością. Składa się z trzech elementów:

- Tożsamość właściciela

- Właściwość nawigacji wskazująca na nie

- W przypadku kolekcji typów będących własnością niezależny składnik (obsługiwany w EF Core 2.2 i nowszych).

Na przykład w modelu domeny zamawiania w eShopOnContainers, jako część Order jednostki, Address value obiekt jest implementowany jako typ jednostki własnością w jednostce właściciela, która jest Order jednostki. Adres jest typem bez właściwości tożsamości zdefiniowanej w modelu domeny. Jest on używany jako właściwość typu Zamówienie, aby określić adres wysyłki dla określonego zamówienia.

Zgodnie z konwencją klucz podstawowy cienia jest tworzony dla typu należącego do właściciela i zostanie zamapowany na tę samą tabelę co właściciel przy użyciu podziału tabeli. Dzięki temu można użyć typów własnościowych podobnie do tego, jak typy złożone są używane w EF6 w tradycyjnej platformie .NET Framework.

Należy pamiętać, że typy własności nigdy nie są wykrywane przez konwencję w EF Core, więc należy zadeklarować je jawnie.

W eShopOnContainers, w OrderingContext.cs, w ramach OnModelCreating() metody, istnieje wiele konfiguracji infrastruktury są stosowane. Jeden z nich jest związany z jednostką Zamówienie.

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

W poniższym kodzie infrastruktury trwałości jest zdefiniowana dla Order jednostki:

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

W poprzednim kodzie `orderConfiguration.OwnsOne(o => o.Address)` metoda określa, `Address` że właściwość jest `Order` własnością jednostki typu.

Domyślnie konwencje EF Core nazwkolumny bazy danych dla właściwości `EntityProperty_OwnedEntityProperty`typu jednostki własnością jako . W związku z tym `Address` wewnętrzne właściwości `Orders` pojawi się `Address_Street` `Address_City` w tabeli z `State` `Country` nazwami , (i tak dalej dla , i `ZipCode`).

Można doniej `Property().HasColumnName()` dotokować metodę fluent, aby zmienić nazwy tych kolumn. W przypadku, `Address` gdy jest własnością publiczną, mapowania będą następujące:

```csharp
orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.Street).HasColumnName("ShippingStreet");

orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.City).HasColumnName("ShippingCity");
```

Możliwe jest łańcuch metody `OwnsOne` w płynnym mapowaniu. W poniższym hipotetycznym `OrderDetails` przykładzie, posiada `BillingAddress` i `ShippingAddress`, które są oba `Address` typy. Następnie `OrderDetails` jest własnością `Order` typu.

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

### <a name="additional-details-on-owned-entity-types"></a>Dodatkowe informacje na temat typów jednostek będących własnością

- Owned typy są definiowane podczas konfigurowania właściwości nawigacji do określonego typu przy użyciu OwnsOne fluent API.

- Definicja typu własnością w naszym modelu metadanych jest złożony: typ właściciela, właściwość nawigacji i typu CLR typu należącego do.

- Tożsamość (klucz) wystąpienia typu należącego do naszego stosu jest złożoną tożsamością typu właściciela i definicją typu będącego własnością.

#### <a name="owned-entities-capabilities"></a>Możliwości podmiotów będących własnością

- Owned typy mogą odwoływać się do innych jednostek, albo własnością (zagnieżdżonych typów własnością) lub niewłasnością (regularne właściwości nawigacji odniesienia do innych jednostek).

- Można mapować ten sam typ CLR jako różne typy własności w tej samej encji właściciela za pomocą oddzielnych właściwości nawigacji.

- Podział tabel jest konfigurowany według konwencji, ale można zrezygnować, mapując typ własności do innej tabeli przy użyciu tabeli ToTable.

- Wczesne ładowanie odbywa się automatycznie na posiadanych typów, oznacza to, że nie ma potrzeby wywoływania `.Include()` kwerendy.

- Można skonfigurować za `[Owned]`pomocą atrybutu , przy użyciu EF Core 2.1 i nowszych.

- Może obsługiwać kolekcje typów należących do nich (przy użyciu wersji 2.2 i nowszych).

#### <a name="owned-entities-limitations"></a>Ograniczenia podmiotów będących własnością

- Nie można utworzyć `DbSet<T>` typu należącego do nabytych (według projektu).

- Nie można wywoływać `ModelBuilder.Entity<T>()` typów będących własnością (obecnie według projektu).

- Brak obsługi opcjonalnych (czyli wartości null) należących do typów, które są mapowane z właścicielem w tej samej tabeli (czyli przy użyciu podziału tabeli). Jest tak, ponieważ mapowanie odbywa się dla każdej właściwości, nie mamy oddzielnego wskaźnika dla wartości złożonej null jako całości.

- Brak obsługi mapowania dziedziczenia dla typów należących do nich, ale powinno być możliwe mapowanie dwóch typów liści tych samych hierarchii dziedziczenia jako różnych typów własności. EF Core nie będzie powodu o tym, że są one częścią tej samej hierarchii.

#### <a name="main-differences-with-ef6s-complex-types"></a>Główne różnice w stosunku do złożonych typów EF6

- Dzielenie tabel jest opcjonalne, oznacza to, że opcjonalnie można je mapować na oddzielną tabelę i nadal być własnością typów.

- Mogą odwoływać się do innych jednostek (to oznacza, że mogą działać jako strona zależna od relacji z innymi typami niebędącymi własnością).

## <a name="additional-resources"></a>Zasoby dodatkowe

- **Martin Fowler. Wzorzec ValueObject** \
  <https://martinfowler.com/bliki/ValueObject.html>

- **Eric Evans. Projektowanie oparte na domenie: radzenie sobie ze złożonością w sercu oprogramowania.** (Książka; zawiera omówienie obiektów wartości) \
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

- **Vaughn Vernon. Implementowanie projektu opartego na domenie.** (Książka; zawiera omówienie obiektów wartości) \
  <https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/>

- **Typy jednostek będących własnością** \
  <https://docs.microsoft.com/ef/core/modeling/owned-entities>

- **Właściwości cienia** \
  <https://docs.microsoft.com/ef/core/modeling/shadow-properties>

- **Złożone typy i/lub obiekty wartości**. Dyskusja w ef core GitHub repo (problemy kartę) \
  <https://github.com/dotnet/efcore/issues/246>

- **ValueObject.cs.** Klasa obiektu wartości podstawowej w eShopOnContainers. \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs>

- **Klasa adresu.** Przykładowa klasa obiektu wartości w eShopOnContainers. \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs>

> [!div class="step-by-step"]
> [Poprzedni](seedwork-domain-model-base-classes-interfaces.md)
> [następny](enumeration-classes-over-enum-types.md)

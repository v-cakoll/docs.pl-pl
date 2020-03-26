---
title: Implementowanie obiektów wartości
description: Architektura mikrousług platformy .NET dla konteneryzowanych aplikacji .NET | Zapoznaj się ze szczegółami i opcjami implementowania obiektów wartości przy użyciu nowych funkcji programu Entity Framework.
ms.date: 01/30/2020
ms.openlocfilehash: 919b23f7c1a0cd0aec8c4417f3af98469a0743dd
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249425"
---
# <a name="implement-value-objects"></a>Implementowanie obiektów wartości

Jak wspomniano we wcześniejszych sekcjach dotyczących jednostek i agregacji, tożsamość ma podstawowe znaczenie dla jednostek. Jednak istnieje wiele obiektów i elementów danych w systemie, które nie wymagają śledzenia tożsamości i tożsamości, takich jak obiekty wartości.

Obiekt wartości może odwoływać się do innych jednostek. Na przykład w aplikacji, która generuje trasę, która opisuje, jak uzyskać z jednego punktu do drugiego, tej trasy będzie obiekt wartości. Byłoby to migawka punktów na określonej trasie, ale ta sugerowana trasa nie miałaby tożsamości, nawet jeśli wewnętrznie może odnosić się do jednostek takich jak Miasto, Droga itp.

Rysunek 7-13 przedstawia obiekt wartości adresu w agregacji Order.

![Diagram przedstawiający obiekt wartości adresu wewnątrz agregacji zamówień.](./media/implement-value-objects/value-object-within-aggregate.png)

**Rysunek 7-13**. Obiekt wartości adresu w agregacji Zamówienia

Jak pokazano na rysunku 7-13, jednostka składa się zwykle z wielu atrybutów. Na przykład `Order` jednostka może być modelowana jako jednostka z tożsamością i składa się wewnętrznie z zestawu atrybutów, takich jak OrderId, OrderDate, OrderItems itp. Ale adres, który jest po prostu złożoną wartością składającą się z kraju/regionu, ulicy, miasta itp.

## <a name="important-characteristics-of-value-objects"></a>Ważne cechy obiektów wartości

Istnieją dwie główne cechy obiektów wartości:

- Nie mają tożsamości.

- Są niezmienne.

Pierwsza cecha była już omawiana. Niezmienność jest ważnym wymogiem. Wartości obiektu wartości muszą być niezmienne po utworzeniu obiektu. W związku z tym podczas konstruowania obiektu, należy podać wymagane wartości, ale nie można zezwolić na ich zmiany w okresie istnienia obiektu.

Obiekty wartości pozwalają wykonywać pewne sztuczki dla wydajności, dzięki ich niezmiennej naturze. Jest to szczególnie prawdziwe w systemach, w których mogą istnieć tysiące wystąpień obiektów wartości, z których wiele ma te same wartości. Ich niezmienny charakter pozwala na ich ponowneużycie; mogą być wymiennymi obiektami, ponieważ ich wartości są takie same i nie mają tożsamości. Ten rodzaj optymalizacji może czasami zrobić różnicę między oprogramowaniem, które działa wolno, a oprogramowaniem o dobrej wydajności. Oczywiście wszystkie te przypadki zależą od środowiska aplikacji i kontekstu wdrażania.

## <a name="value-object-implementation-in-c"></a>Implementacja obiektu wartości w języku C\#

Jeśli chodzi o implementację, można mieć klasę podstawową obiektu wartości, która ma podstawowe metody narzędzia, takie jak równość na podstawie porównania wszystkich atrybutów (ponieważ obiekt wartości nie może być oparty na tożsamości) i innych podstawowych cech. Poniższy przykład pokazuje klasę podstawową obiektu wartości używane w mikrousługi zamawiania z eShopOnContainers.

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

Tej klasy można użyć podczas implementowania obiektu rzeczywistej wartości, tak jak w przypadku obiektu wartość adresu wyświetlanego w poniższym przykładzie:

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

Można zobaczyć, jak ta implementacja obiektu wartości Address nie ma tożsamości i dlatego nie ma pola identyfikator, ani w klasie Adres nawet w ValueObject klasy.

Brak pola identyfikatora w klasie, która ma być używana przez entity framework (EF) nie było możliwe, dopóki EF Core 2.0, co znacznie pomaga zaimplementować obiekty o lepszej wartości bez identyfikatora. To jest właśnie wyjaśnienie następnej sekcji.

Można argumentować, że obiekty wartości, są niezmienne, powinny być tylko do odczytu (to znaczy, mają właściwości tylko do uzyskania), i to rzeczywiście prawda. Jednak obiekty wartości są zwykle serializowane i deserializowane, aby przejść przez kolejki komunikatów, a tylko do odczytu zatrzymuje deserializatora przed przypisywaniem wartości, więc po prostu pozostawiamy je jako zestaw prywatny, który jest wystarczająco czytelny, aby być praktycznym.

## <a name="how-to-persist-value-objects-in-the-database-with-ef-core-20-and-later"></a>Jak utrwalić obiekty wartości w bazie danych za pomocą EF Core 2.0 i nowszych

Właśnie zobaczyłeś, jak zdefiniować obiekt wartości w modelu domeny. Ale jak można rzeczywiście utrwalić go w bazie danych przy użyciu entity framework core, ponieważ zwykle jest przeznaczony dla jednostek z tożsamością?

### <a name="background-and-older-approaches-using-ef-core-11"></a>Tło i starsze podejścia przy użyciu EF Core 1.1

W tle ograniczenie podczas korzystania z EF Core 1.0 i 1.1 było to, że nie można użyć [typów złożonych,](xref:System.ComponentModel.DataAnnotations.Schema.ComplexTypeAttribute) zgodnie z definicją w EF 6.x w tradycyjnej .NET Framework. W związku z tym jeśli przy użyciu EF Core 1.0 lub 1.1, trzeba przechowywać obiekt wartości jako jednostki EF z polem identyfikatora. Następnie, więc wyglądało to bardziej jak obiekt wartości bez tożsamości, można ukryć jego identyfikator, dzięki czemu można wyjaśnić, że tożsamość obiektu wartości nie jest ważne w modelu domeny. Identyfikator można ukryć, używając identyfikatora jako [właściwości shadow](https://docs.microsoft.com/ef/core/modeling/shadow-properties ). Ponieważ ta konfiguracja do ukrywania identyfikatora w modelu jest skonfigurowany na poziomie infrastruktury EF, byłoby to rodzaj przezroczyste dla modelu domeny.

W początkowej wersji eShopOnContainers (.NET Core 1.1), ukryty identyfikator wymagany przez infrastrukturę EF Core został zaimplementowany w następujący sposób na poziomie DbContext przy użyciu interfejsu API Fluent w projekcie infrastruktury. W związku z tym identyfikator był ukryty z punktu widzenia modelu domeny, ale nadal obecny w infrastrukturze.

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

Jednak trwałość tego obiektu wartości w bazie danych została wykonana jak zwykła jednostka w innej tabeli.

Z EF Core 2.0 i nowsze, istnieją nowe i lepsze sposoby utrwalania obiektów wartości.

## <a name="persist-value-objects-as-owned-entity-types-in-ef-core-20-and-later"></a>Zachowywanie obiektów wartości jako typów jednostek należących do ef core 2.0 i nowszych

Nawet w przypadku niektórych przerw między wzorcem obiektu wartości kanonicznej w DDD a typem jednostki należącej do własnością w ef core, jest obecnie najlepszym sposobem utrwalania obiektów wartości za pomocą EF Core 2.0 i nowszych. Ograniczenia można zobaczyć na końcu tej sekcji.

Funkcja typu jednostki należącej została dodana do ef core od wersji 2.0.

Typ jednostki należącej do użytkownika umożliwia mapowanie typów, które nie mają własnej tożsamości jawnie zdefiniowanej w modelu domeny i są używane jako właściwości, takie jak obiekt wartości, w dowolnej jednostce. Typ jednostki należącej do jednostki współumisuje ten sam typ CLR z innym typem jednostki (oznacza to, że jest to tylko klasa zwykła). Encja zawierająca definiującą nawigację jest jednostką właściciela. Podczas wykonywania zapytań właściciela, posiadanych typów są uwzględniane domyślnie.

Wystarczy spojrzeć na model domeny, typ własnością wygląda tak, że nie ma żadnej tożsamości. Jednak w obszarze obejmuje, typy należące mają tożsamość, ale właściwość nawigacji właściciela jest częścią tej tożsamości.

Tożsamość wystąpień typów należących do państwa nie jest całkowicie ich własne. Składa się z trzech elementów:

- Tożsamość właściciela

- Właściwość nawigacji wskazująca na nich

- W przypadku kolekcji posiadanych typów, niezależny składnik (obsługiwany w EF Core 2.2 i nowszych).

Na przykład w modelu domeny zamawiania w eShopOnContainers, jako część Order jednostki, Adres wartość obiektu jest implementowana jako typ jednostki należącej do właściciela w jednostce właściciela, który jest Order jednostki. Adres jest typem bez właściwości tożsamości zdefiniowanej w modelu domeny. Jest on używany jako właściwość typu Zamówienie, aby określić adres wysyłki dla określonego zamówienia.

Zgodnie z konwencją klucz podstawowy w tle jest tworzony dla typu należącego do właściciela i zostanie on mapowany na tę samą tabelę co właściciel przy użyciu podziału tabeli. Dzięki temu można używać typów posiadanych podobnie jak typy złożone są używane w EF6 w tradycyjnej .NET Framework.

Należy pamiętać, że typy należące nigdy nie są odnajdywana przez konwencję w EF Core, więc należy zadeklarować je jawnie.

W eShopOnContainers, w OrderingContext.cs, w ramach OnModelCreating() metody, istnieje wiele konfiguracji infrastruktury są stosowane. Jeden z nich jest związany z jednostką Zakonu.

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

W poniższym kodzie infrastruktura trwałości jest zdefiniowana dla order jednostki:

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

Domyślnie konwencje EF Core nazywają kolumny bazy danych właściwościami typu `EntityProperty_OwnedEntityProperty`jednostki należącej do państwa jako . W związku z tym `Address` wewnętrzne właściwości `Orders` pojawią się `Address_Street` `Address_City` w tabeli `State`z `Country` `ZipCode`nazwami , (i tak dalej dla , i ).

Można dołączyć `Property().HasColumnName()` fluent metody, aby zmienić nazwę tych kolumn. W przypadku, `Address` gdy jest własnością publiczną, mapowania będą podobne do następujących:

```csharp
orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.Street).HasColumnName("ShippingStreet");

orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.City).HasColumnName("ShippingCity");
```

Możliwe jest łańcuch `OwnsOne` metody w płynne mapowanie. W poniższym hipotetycznym przykładzie `OrderDetails` jest właścicielem `BillingAddress` i `ShippingAddress`, które są oba `Address` typy. Następnie `OrderDetails` jest własnością `Order` typu.

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

- Typy należące do użytkownika są definiowane podczas konfigurowania właściwości nawigacji do określonego typu przy użyciu interfejsu API OwnsOne fluent.

- Definicja typu należącego do właściciela w naszym modelu metadanych jest złożona z: typu właściciela, właściwości nawigacji i typu CLR typu należącego do sieci.

- Tożsamość (klucz) wystąpienia typu należącego w naszym stosie jest złożona tożsamości typu właściciela i definicji typu należącego do właściciela.

#### <a name="owned-entities-capabilities"></a>Możliwości jednostek będących własnością

- Typy własnością można odwoływać się do innych jednostek, własnością (zagnieżdżone typy własnością) lub niewłasności (regularne właściwości nawigacji odwołania do innych jednostek).

- Można mapować ten sam typ CLR jako różne typy własnością w tej samej jednostce właściciela za pomocą oddzielnych właściwości nawigacji.

- Dzielenie tabel jest konfigurowane według konwencji, ale można zrezygnować, mapując typ należący do innej tabeli przy użyciu tabeli ToTable.

- Wczesne ładowanie jest wykonywane automatycznie na typy należące do `.Include()` firmy, oznacza to, że nie ma potrzeby wywoływania kwerendy.

- Można skonfigurować za `[Owned]`pomocą atrybutu , przy użyciu EF Core 2.1 i nowszych.

- Może obsługiwać kolekcje posiadanych typów (przy użyciu wersji 2.2 i nowszych).

#### <a name="owned-entities-limitations"></a>Ograniczenia podmiotów będących własnością

- Nie można utworzyć `DbSet<T>` typu należącego do użytkownika (według projektu).

- Nie można wywołać `ModelBuilder.Entity<T>()` na posiadanych typów (obecnie według projektu).

- Brak obsługi dla typów należących do opcjonalnych (czyli nullable), które są mapowane z właścicielem w tej samej tabeli (czyli przy użyciu podziału tabeli). Jest to spowodowane mapowanie jest wykonywane dla każdej właściwości, nie mamy oddzielne wartownika dla null złożonej wartości jako całości.

- Brak obsługi mapowania dziedziczenia dla typów posiadanych, ale powinno być możliwe mapowanie dwóch typów liści tych samych hierarchii dziedziczenia jako różnych typów należących. EF Core nie będzie powodem o tym, że są one częścią tej samej hierarchii.

#### <a name="main-differences-with-ef6s-complex-types"></a>Główne różnice w stosunku do złożonych typów EF6

- Dzielenie tabeli jest opcjonalne, oznacza to, że opcjonalnie mogą być mapowane do osobnej tabeli i nadal być własnością typów.

- Mogą odwoływać się do innych jednostek (oznacza to, że mogą działać jako strona zależna od relacji z innymi typami niewłasności).

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

- **Złożone typy i/lub obiekty wartości**. Dyskusja w repozytorium EF Core GitHub (karta Problemy) \
  <https://github.com/dotnet/efcore/issues/246>

- **ValueObject.cs.** Klasa obiektu wartości podstawowej w eShopOnContainers. \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs>

- **Klasa adresu.** Przykładowa klasa obiektu wartości w eShopOnContainers. \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs>

> [!div class="step-by-step"]
> [Poprzedni](seedwork-domain-model-base-classes-interfaces.md)
> [następny](enumeration-classes-over-enum-types.md)

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
# <a name="implement-value-objects"></a>Implementowanie obiektów wartości

Jak opisano w poprzednich sekcjach dotyczących jednostek i agregacji, tożsamość jest podstawowa dla jednostek. Istnieje jednak wiele obiektów i elementów danych w systemie, które nie wymagają śledzenia tożsamości i tożsamości, takie jak obiekty wartości.

Obiekt wartości może odwoływać się do innych jednostek. Na przykład w aplikacji, która generuje trasę opisującą, jak uzyskać od jednego punktu do drugiego, ta trasa będzie obiektem wartości. Będzie to migawka punktów w określonej trasie, ale ta trasa Sugerowana nie będzie miała tożsamości, nawet jeśli wewnętrznie może odnosić się do jednostek takich jak miasto, droga itp.

Rysunek 7-13 pokazuje obiekt wartości adresu w ramach agregacji zamówienia.

![Diagram przedstawiający wartość adresu — obiekt wewnątrz agregacji zamówienia.](./media/implement-value-objects/value-object-within-aggregate.png)

**Rysunek 7-13**. Obiekt wartości adresu w ramach agregacji zamówienia

Jak pokazano na rysunku 7-13, jednostka jest zwykle składa się z wielu atrybutów. Na przykład jednostka `Order` może być modelowana jako jednostka z tożsamością i złożona wewnętrznie z zestawu atrybutów, takich jak IDZamówienia, DataZamówienia, OrderItems itp. Ale adres, który jest po prostu złożoną wartością składającą się z kraju/regionu, ulicy, miasta itp. i nie ma tożsamości w tej domenie, musi być modelowany i traktowany jako obiekt wartości.

## <a name="important-characteristics-of-value-objects"></a>Ważne cechy obiektów wartości

Istnieją dwie główne cechy obiektów wartości:

- Nie mają tożsamości.

- Są one niezmienne.

Pierwsza cecha została już omówiona. Niezmienności jest ważnym wymaganiem. Wartości obiektu wartości muszą być niezmienne po utworzeniu obiektu. W związku z tym, gdy obiekt jest skonstruowany, należy podać wymagane wartości, ale nie można go zmienić w okresie istnienia obiektu.

Obiekty wartości umożliwiają wykonywanie niektórych lew w celu uzyskania wydajności, dzięki czemu ich niezmiennego charakteru. Jest to szczególnie prawdziwe w systemach, w których mogą istnieć tysiące wystąpień obiektów wartości, z których wiele ma te same wartości. Ich niezmienny charakter pozwala na ich użycie ponownie; mogą być obiektami wymiennymi, ponieważ ich wartości są takie same i nie mają tożsamości. Ten typ optymalizacji może czasami pomieścić różnice między oprogramowaniem działającym wolno a oprogramowaniem o dobrej wydajności. Oczywiście wszystkie te przypadki są zależne od środowiska aplikacji i kontekstu wdrażania.

## <a name="value-object-implementation-in-c"></a>Implementacja obiektu wartości w języku C\#

W warunkach implementacji można utworzyć klasę bazową obiektu wartości, która ma podstawowe metody narzędziowe, takie jak równość, na podstawie porównania między wszystkimi atrybutami (ponieważ obiekt value nie może opierać się na tożsamości) i inne podstawowe cechy. W poniższym przykładzie pokazano klasę bazową obiektu wartości używaną w mikrousłudze porządkowania z eShopOnContainers.

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

Tej klasy można użyć podczas implementowania rzeczywistego obiektu wartości, podobnie jak w przypadku obiektu wartości adresu pokazanego w poniższym przykładzie:

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

Można zobaczyć, jak ta implementacja obiektu wartości nie ma tożsamości i w związku z tym nie ma pola identyfikatora ani w klasie adresowej, a nie nawet w klasie Valueobject.

Brak pola identyfikatora w klasie, która ma być używana przez Entity Framework, nie było możliwe do EF Core 2,0, co znacznie pomaga zaimplementować lepsze obiekty wartości bez identyfikatora. Jest to dokładne wyjaśnienie następnej sekcji.

Może być Argumentowano, że obiekty wartości, które są niezmienne, powinny być tylko do odczytu (tj. właściwości tylko do pobrania) i faktycznie prawdziwe. Jednak obiekty wartości są zwykle serializowane i deserializowane w celu przechodzenia przez kolejki komunikatów i są w trybie tylko do odczytu uniemożliwiają przypisanie wartości, dlatego po prostu pozostawiamy je jako zestaw prywatny, który jest wystarczająco duży, aby był praktyczny.

## <a name="how-to-persist-value-objects-in-the-database-with-ef-core-20"></a>Jak utrwalać obiekty wartości w bazie danych za pomocą EF Core 2,0

Właśnie pokazano, jak zdefiniować obiekt wartości w modelu domeny. Ale w jaki sposób można w rzeczywistości zachować ją w bazie danych za pomocą rdzenia Entity Framework (EF), które zwykle są obiektami docelowymi tożsamości?

### <a name="background-and-older-approaches-using-ef-core-11"></a>W tle i starszych podejściach korzystających z EF Core 1,1

W tle, ograniczenie w przypadku korzystania z EF Core 1,0 i 1,1 było niemożliwe, ponieważ nie można było użyć [typów złożonych](xref:System.ComponentModel.DataAnnotations.Schema.ComplexTypeAttribute) zdefiniowanych w Ef 6. x w tradycyjnych .NET Framework. W związku z tym, jeśli jest używany EF Core 1,0 lub 1,1, należy przechowywać obiekt wartości jako jednostkę EF z polem ID. Następnie, aby wyglądała podobnie jak obiekt wartości bez tożsamości, można ukryć jego identyfikator, aby wyczyścić, że tożsamość obiektu wartości nie jest istotna w modelu domeny. Ten identyfikator można ukryć, używając identyfikatora jako [Właściwości cienia](https://docs.microsoft.com/ef/core/modeling/shadow-properties ). Ponieważ konfiguracja służąca do ukrywania identyfikatora w modelu jest skonfigurowana na poziomie infrastruktury EF, byłby on rodzaj przezroczysty dla modelu domeny.

W początkowej wersji programu eShopOnContainers (.NET Core 1,1) ukryty identyfikator, który jest wymagany przez EF Core infrastrukturę, został zaimplementowany w następujący sposób na poziomie DbContext, przy użyciu interfejsu API Fluent w projekcie infrastruktury. W związku z tym, identyfikator został ukryty z punktu modelu domeny w widoku, ale wciąż występuje w infrastrukturze.

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

Jednak trwałość tego obiektu wartości do bazy danych była przeprowadzona jak zwykła jednostka w innej tabeli.

W EF Core 2,0 istnieją nowe i lepsze metody utrwalania obiektów wartości.

## <a name="persist-value-objects-as-owned-entity-types-in-ef-core-20"></a>Utrwalaj obiekty wartości jako należące do nich typy jednostek w EF Core 2,0

Nawet w przypadku niektórych luk między wzorcem obiektu wartości kanonicznych w DDD i typ jednostki należącej do EF Core, obecnie najlepszym sposobem utrwalania obiektów wartości jest EF Core 2,0. Ograniczenia można zobaczyć na końcu tej sekcji.

Funkcja typu jednostki będąca własnością została dodana do EF Core od wersji 2,0.

Typ jednostki będącej właścicielem umożliwia mapowanie typów, które nie mają własnej tożsamości jawnie zdefiniowanej w modelu domeny i są używane jako właściwości, takie jak obiekt wartości, w ramach dowolnych jednostek. Typ jednostki będącej własnością ma udział tego samego typu CLR z innym typem jednostki (to jest tylko zwykła Klasa). Jednostką zawierającą zdefiniowaną nawigację jest obiektem będącym właścicielem. Podczas wykonywania zapytania dotyczącego właściciela typy posiadane są domyślnie uwzględniane.

Po prostu, patrząc na model domeny, typ własnością wygląda podobnie do tego, że nie ma żadnej tożsamości. Jednakże, w obszarze okładek, typy posiadane mają tożsamość, ale właściwość nawigacji właściciela jest częścią tej tożsamości.

Tożsamość wystąpień posiadanych typów nie jest całkowicie własna. Składa się z trzech składników:

- Tożsamość właściciela

- Właściwość nawigacji wskazująca na siebie

- W przypadku kolekcji typów posiadanych, składnik niezależny (nie jest jeszcze obsługiwany w EF Core 2,0, w dniu 2,2).

Na przykład w modelu domeny uporządkowanej pod adresem eShopOnContainers, jako część jednostki Order, obiekt wartości adresu jest implementowany jako typ jednostki należącej do jednostki właściciela, która jest jednostką Order. Adres jest typem bez właściwości Identity zdefiniowanej w modelu domeny. Jest ona używana jako właściwość typu zamówienia, aby określić adres wysyłkowy dla konkretnej kolejności.

Według Konwencji klucz podstawowy w tle jest tworzony dla typu posiadanego i zostanie zamapowany do tej samej tabeli co właściciel przy użyciu dzielenia tabeli. Pozwala to na używanie typów posiadanych w sposób podobny do tego, jak złożone typy są używane w EF6 w tradycyjnych .NET Framework.

Należy pamiętać, że typy posiadane nigdy nie są wykrywane przez Konwencję w EF Core, więc należy zadeklarować je jawnie.

W eShopOnContainers, w OrderingContext.cs w ramach metody OnModelCreating (), jest stosowana wiele konfiguracji infrastruktury. Jeden z nich jest powiązany z jednostką Order.

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

W poniższym kodzie infrastruktura trwałości jest definiowana dla jednostki Order:

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

W poprzednim kodzie Metoda `orderConfiguration.OwnsOne(o => o.Address)` określa, że właściwość `Address` jest obiektem należącym do typu `Order`.

Domyślnie konwencje EF Core nazywają kolumny bazy danych dla właściwości typu jednostki będącej własnością, jako `EntityProperty_OwnedEntityProperty`. W związku z tym właściwości wewnętrzne `Address` będą wyświetlane w tabeli `Orders` z nazwami `Address_Street`, `Address_City` (itd. dla `State`, `Country` i `ZipCode`).

Możesz dołączyć metodę `Property().HasColumnName()` Fluent, aby zmienić nazwy tych kolumn. W przypadku, gdy `Address` jest właściwością publiczną, mapowania byłyby podobne do następujących:

```csharp
orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.Street).HasColumnName("ShippingStreet");

orderConfiguration.OwnsOne(p => p.Address)
                            .Property(p=>p.City).HasColumnName("ShippingCity");
```

Istnieje możliwość łańcucha metody `OwnsOne` w ramach mapowania Fluent. W poniższym hipotetycznym przykładzie `OrderDetails` są własnością `BillingAddress` i `ShippingAddress`, które są oba typy `Address`. A następnie `OrderDetails` należy do typu `Order`.

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

### <a name="additional-details-on-owned-entity-types"></a>Dodatkowe szczegóły dotyczące typów jednostek posiadanych

- Typy posiadane są definiowane podczas konfigurowania właściwości nawigacji do określonego typu przy użyciu interfejsu API Fluent OwnsOne.

- Definicja typu będącego właścicielem w naszym modelu metadanych jest złożona z: typu właściciela, właściwości nawigacji i typu CLR typu będącego własnością.

- Tożsamość (klucz) wystąpienia należącego do typu w naszym stosie to złożona tożsamość typu właściciela i definicja typu będącego własnością.

#### <a name="owned-entities-capabilities"></a>Możliwości jednostek należących do firmy:

- Typy posiadane mogą odwoływać się do innych jednostek, należących do (zagnieżdżonych typów będących własnością) lub nienależących do siebie (regularne właściwości nawigacji odwołań do innych jednostek).

- Można mapować ten sam typ środowiska CLR jako różne typy należące do tej samej jednostki właściciela za pomocą oddzielnych właściwości nawigacji.

- Podział tabeli jest konfiguracją według Konwencji, ale można zrezygnować z mapowania typu należącego do innej tabeli przy użyciu ToTable.

- Ładowanie eager jest wykonywane automatycznie w typach posiadanych, tzn. nie ma potrzeby wywoływania dyrektywy include () w zapytaniu.

- Można skonfigurować z atrybutami \[własnością\], w EF Core 2,1

#### <a name="owned-entities-limitations"></a>Ograniczenia jednostek będących własnością:

- Nie można utworzyć Nieogólnymi\<T\> należącego do typu (zgodnie z projektem).

- Nie można wywołać metody element modelbuilder. Entity\<T\>() dla typów posiadanych (obecnie według projektu).

- Nie ma jeszcze kolekcji posiadanych typów (w EF Core 2,1, ale będą one obsługiwane w 2,2).

- Brak obsługi opcjonalnych (dopuszczających wartości null) typów, które są mapowane przy użyciu właściciela w tej samej tabeli (tj. przy użyciu dzielenia tabeli). Wynika to z faktu, że mapowanie jest wykonywane dla każdej właściwości. nie mamy oddzielnej kontrolki dla wartości złożonej o wartości null a jako całości.

- Brak obsługi mapowania dziedziczenia dla typów posiadanych, ale powinno być możliwe mapowanie dwóch typów liści tych samych hierarchii dziedziczenia co różne typy należące do użytkownika. EF Core nie będzie przyczyną faktu, że są one częścią tej samej hierarchii.

#### <a name="main-differences-with-ef6s-complex-types"></a>Główne różnice w EF6's typach złożonych

- Dzielenie tabeli jest opcjonalne, tzn. mogą być opcjonalnie mapowane do oddzielnej tabeli i nadal są typami własnością.

- Mogą odwoływać się do innych jednostek (tj. mogą działać jako strona zależna od relacji z innymi typami niebędącymi własnością).

## <a name="additional-resources"></a>Dodatkowe zasoby

- **Fowlera Martin. Wartość wzorca wartościobject** \
  <https://martinfowler.com/bliki/ValueObject.html>

- **Eric Evans. Projektowanie oparte na domenie: zapełnianie złożoności w oprogramowaniu.** (Książka; zawiera omówienie obiektów wartości) \
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

- **Vaughn Vernon. Implementowanie projektu opartego na domenie.** (Książka; zawiera omówienie obiektów wartości) \
  <https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/>

- **Właściwości cienia** \
  [https://docs.microsoft.com/ef/core/modeling/shadow-properties](/ef/core/modeling/shadow-properties)

- **Typy złożone i/lub obiekty wartości**. Dyskusje w repozytorium EF Core GitHub (karta problemy) \
  <https://github.com/aspnet/EntityFramework/issues/246>

- **ValueObject.cs.** Klasa obiektu wartości podstawowej w eShopOnContainers. \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs>

- **Klasa adresu.** Klasa przykładowych obiektów wartości w eShopOnContainers. \
  <https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs>

> [!div class="step-by-step"]
> [Poprzedni](seedwork-domain-model-base-classes-interfaces.md)
> [dalej](enumeration-classes-over-enum-types.md)

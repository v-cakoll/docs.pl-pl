---
title: "Implementowanie obiekty wartości"
description: "Architektura Mikrousług .NET dla aplikacji .NET konteneryzowanych | Implementowanie obiekty wartości"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: c20bc80d2ddb864a3a0172beb211974426a278a8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-value-objects"></a>Implementowanie obiekty wartości

Zgodnie z opisem we wcześniejszych sekcjach jednostek i agreguje informacje tożsamości jest podstawą dla jednostek. Istnieją jednak wiele obiektów i elementy danych w systemie, które nie wymagają tożsamości i tożsamości śledzenia, takich jak obiekty wartości.

Obiekt wartości może się odwoływać inne jednostki. Na przykład w aplikacji, która generuje trasy, który opisuje metodę get z jednego miejsca do innego tej trasy byłoby obiektu wartości. Byłoby migawkę punktów na określoną trasę, ale ta trasa sugerowane nie miałoby tożsamości, mimo że wewnętrznie może dotyczyć jednostek Miasto, drogowej itd.

Rysunek 9-13 przedstawiono obiektu wartości adresu w kolejności agregacji.

![](./media/image14.png)

**Rysunek 9-13**. Adres obiektu wartości w kolejności agregacji

Jak pokazano w rysunek 9-13, jednostki zazwyczaj składa się z wielu atrybutów. Na przykład kolejności można modelowane jako jednostki o tożsamości i wewnętrznie składa się z zestawu atrybutów, takich jak OrderId OrderDate, OrderItems itp. Ale adresu, który jest po prostu złożona wartość składa się z kraju ulicy, miasta, itp. muszą być modelowane i traktowane jako obiekt wartości.

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

    public Address(string street, string city, string state,
        string country, string zipcode)
    {
        Street = street;
        City = city;
        State = state;
        Country = country;
        ZipCode = zipcode;
    }

    protected override IEnumerable<object> GetAtomicValues()
    {
        yield return Street;
        yield return City;
        yield return State;
        yield return Country;
        yield return ZipCode;
    }
}
```

## <a name="hiding-the-identity-characteristic-when-using-ef-core-to-persist-value-objects"></a>Ukrywanie właściwości tożsamości, używając EF Core utrwalić obiekty wartości

To ograniczenie, gdy przy użyciu EF Core jest, że w jego bieżącej wersji (EF Core 1.1) nie można użyć [typów złożonych](https://docs.microsoft.com/de-de/dotnet/api/system.componentmodel.dataannotations.schema.complextypeattribute?view=netframework-4.7) zgodnie z definicją w EF 6.x. W związku z tym obiektu wartości muszą być przechowywane jako jednostka EF. Jednak można ukryć jego Identyfikatora, więc można wyjaśnić, że tożsamość nie jest ważna w modelu, który obiekt wartości jest częścią. Ukryj identyfikator jest za pomocą Identyfikatora jako właściwość cienia. Ponieważ tego ukrywania identyfikator modelu jest skonfigurowany na poziomie infrastruktury, będzie niewidoczny dla modelu domeny i jej wdrożenia infrastruktury można zmienić w przyszłości.

W eShopOnContainers identyfikator ukryte potrzebne w infrastrukturze podstawowej EF jest zaimplementowana w następujący sposób na poziomie DbContext przy użyciu interfejsu API Fluent w projekcie infrastruktury.

```csharp
// Fluent API within the OrderingContext:DbContext in the
// Ordering.Infrastructure project

void ConfigureAddress(EntityTypeBuilder<Address> addressConfiguration)
{
    addressConfiguration.ToTable("address", DEFAULT_SCHEMA);
    addressConfiguration.Property<int>("Id").IsRequired();
    addressConfiguration.HasKey("Id");
}
```

W związku z tym Identyfikatorem jest ukryty z punktu widzenia modelu domeny, a w przyszłości infrastruktury obiektu wartość może również być implementowana jako typ złożony lub w inny sposób.

## <a name="additional-resources"></a>Dodatkowe zasoby

-   **Pole Fowler. Wzorzec ValueObject**
    [*https://martinfowler.com/bliki/ValueObject.html*](https://martinfowler.com/bliki/ValueObject.html)

-   **Evans marek. Projektowanie oparte na domenie: Czoła złożoności serca oprogramowania.** (Książki; zawiera omówienie obiekty wartości) [ *https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)

-   **Vaughn Vernon. Implementowanie projektu opartych na domenie.** (Książki; zawiera omówienie obiekty wartości) [ *https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/*](https://www.amazon.com/Implementing-Domain-Driven-Design-Vaughn-Vernon/dp/0321834577/)

-   **Właściwości w tle**
    [*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)

-   **Typy złożone i/lub obiekty wartości**. Omówienie w repozytorium EF Core GitHub (karta problemy) [ *https://github.com/aspnet/EntityFramework/issues/246*](https://github.com/aspnet/EntityFramework/issues/246)

-   **ValueObject.cs.** Wartość podstawową klasy obiektów w eShopOnContainers.
    [*https://github.com/DotNet/eShopOnContainers/blob/Master/src/Services/Ordering/Ordering.domain/SeedWork/ValueObject.CS*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/SeedWork/ValueObject.cs)

-   **Klasy adresów.** Przykładowe wartości klasy obiektów w eShopOnContainers.
    [*https://github.com/DotNet/eShopOnContainers/blob/Master/src/Services/Ordering/Ordering.domain/AggregatesModel/OrderAggregate/Address.CS*](https://github.com/dotnet/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs)


>[!div class="step-by-step"]
[Poprzednie] (seedwork-domain-model-base-classes-interfaces.md) [dalej] (wyliczenie klasy over wyliczenia types.md)

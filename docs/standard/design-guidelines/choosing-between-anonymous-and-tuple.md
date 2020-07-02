---
title: Wybór między typami anonimowymi a kolekcjami
description: Dowiedz się, kiedy należy wybrać typy anonimowe i typ krotki.
ms.date: 06/29/2020
ms.technology: dotnet-standard
ms.openlocfilehash: bc17695830a42a6eed9d60c0e097ee9d02a7957e
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803771"
---
# <a name="choosing-between-anonymous-and-tuple-types"></a>Wybór między typami anonimowymi a kolekcjami

Wybór odpowiedniego typu polega na uwzględnieniu jego użyteczności, wydajności i kompromisów w porównaniu z innymi typami. Typy anonimowe zostały udostępnione od języka C# 3,0, podczas gdy <xref:System.Tuple%602?displayProperty=nameWithType> typy ogólne zostały wprowadzone z .NET Framework 4,0. Ponieważ następnie wprowadzono nowe opcje z obsługą poziomu języka, takie jak <xref:System.ValueTuple%602?displayProperty=nameWithType> nazwa oznacza, określ typ wartości z elastycznością typów anonimowych. W tym artykule dowiesz się, kiedy należy wybrać jeden typ z drugiego.

## <a name="usability-and-functionality"></a>Użyteczność i funkcje

Typy anonimowe zostały wprowadzone w języku C# 3,0 z wyrażeniami programu Query-Integrated Language (LINQ). LINQ, deweloperzy często projektują wyniki zapytań w typach anonimowych, które zawierają kilka właściwości Select z obiektów, z którymi pracują. Rozważmy poniższy przykład, który tworzy wystąpienie tablicy <xref:System.DateTime> obiektów i wykonuje iteracje w celu przechodzenia do typu anonimowego z dwiema właściwościami.

```csharp-interactive
var dates = new[]
{
    DateTime.UtcNow.AddHours(-1),
    DateTime.UtcNow,
    DateTime.UtcNow.AddHours(1),
};

foreach (var anonymous in
             dates.Select(
                 date => new { Formatted = $"{date:MMM dd, yyyy hh:mm zzz}", date.Ticks }))
{
    Console.WriteLine($"Ticks: {anonymous.Ticks}, formatted: {anonymous.Formatted}");
}
```

Typy anonimowe są tworzone przy użyciu [`new`](../../csharp/language-reference/operators/new-operator.md) operatora, a nazwy właściwości i typy są wywnioskowane z deklaracji. Jeśli co najmniej dwa anonimowe Inicjatory obiektów w tym samym zestawie określają sekwencję właściwości, które są w tej samej kolejności i mają takie same nazwy i typy, kompilator traktuje obiekty jako wystąpienia tego samego typu. Korzystają one z tych samych informacji o typie wygenerowanym przez kompilator.

Poprzedni fragment kodu w języku C# projektuje typ anonimowy z dwiema właściwościami, podobnie jak w przypadku następującej klasy języka C# wygenerowanej przez kompilator:

```csharp
internal sealed class f__AnonymousType0
{
    public string Formatted { get; }
    public long Ticks { get; }

    public f__AnonymousType0(string formatted, long ticks)
    {
        Formatted = formatted;
        Ticks = ticks;
    }
}
```

Aby uzyskać więcej informacji, zobacz [Typy anonimowe](../../csharp/programming-guide/classes-and-structs/anonymous-types.md). Ta sama funkcja istnieje z krotkami podczas projekcji w zapytaniach LINQ, można wybrać właściwości w postaci krotek. Te krotki przepływają przez zapytanie, podobnie jak typy anonimowe. Teraz Rozważmy poniższy przykład przy użyciu `System.Tuple<string, long>` .

```csharp-interactive
var dates = new[]
{
    DateTime.UtcNow.AddHours(-1),
    DateTime.UtcNow,
    DateTime.UtcNow.AddHours(1),
};

foreach (var tuple in
            dates.Select(
                date => new Tuple<string, long>($"{date:MMM dd, yyyy hh:mm zzz}", date.Ticks)))
{
    Console.WriteLine($"Ticks: {tuple.Item2}, formatted: {tuple.Item1}");
}
```

W <xref:System.Tuple%602?displayProperty=nameWithType> , wystąpienie uwidacznia właściwości elementów numerowanych, takich jak `Item1` , i `Item2` . Te nazwy właściwości mogą utrudnić zrozumienie intencji wartości właściwości, ponieważ nazwa właściwości zawiera tylko numer porządkowy. Ponadto `System.Tuple` typy są `class` typami odwołań. <xref:System.ValueTuple%602?displayProperty=nameWithType>Jednak jest to `struct` Typ wartości. Poniższy fragment kodu w języku C# używa `ValueTuple<string, long>` do projektu w. W tym celu przypisuje się przy użyciu składni literału.

```csharp-interactive
var dates = new[]
{
    DateTime.UtcNow.AddHours(-1),
    DateTime.UtcNow,
    DateTime.UtcNow.AddHours(1),
};

foreach (var (formatted, ticks) in
            dates.Select(
                date => (Formatted: $"{date:MMM dd, yyyy at hh:mm zzz}", date.Ticks)))
{
    Console.WriteLine($"Ticks: {ticks}, formatted: {formatted}");
}
```

Język C# zapewnia obsługę spójnych kolekcji z <xref:System.ValueTuple> typem i semantyką dla:

- [Przypisanie krotki](../../csharp/tuples.md#assignment-and-tuples)
- [Dekonstrukcja krotki](../../csharp/deconstruct.md) (nieograniczona do krotek)
- [Sprawdzanie równości spójnej kolekcji](../../csharp/tuples.md#equality-and-tuples)
- [Inicjatory projekcji krotki](../../csharp/tuples.md#tuple-projection-initializers)

Poprzednie przykłady to wszystkie funkcje równoważne, ale istnieją niewielkie różnice w ich użyteczności i ich podstawowych wdrożeniach.

## <a name="tradeoffs"></a>Kompromisy

Możesz chcieć zawsze używać <xref:System.ValueTuple> <xref:System.Tuple> typów i anonimowych, ale istnieją kompromisy, które należy wziąć pod uwagę. <xref:System.ValueTuple>Typy są modyfikowalne, podczas gdy <xref:System.Tuple> są tylko do odczytu. Typy anonimowe mogą być używane w drzewach wyrażeń, natomiast kolekcje nie mogą. Poniższa tabela zawiera omówienie niektórych różnic między kluczami.

### <a name="key-differences"></a>Podstawowe różnice

| Nazwa                     | Modyfikator dostępu | Typ     | Nazwa właściwości niestandardowej | Obsługa dekonstrukcji | Obsługa drzewa wyrażeń |
|--------------------------|-----------------|----------|----------------------|------------------------|-------------------------|
| Typy anonimowe          | `internal`      | `class`  | ✔️                   | ❌                     | ✔️                     |
| <xref:System.Tuple>      | `public`        | `class`  | ❌                   | ❌                     | ✔️                     |
| <xref:System.ValueTuple> | `public`        | `struct` | ✔️                   | ✔️                     | ❌                     |

### <a name="serialization"></a>Serializacja

Jednym ważnym zagadnieniem podczas wybierania typu jest to, czy należy go serializować. Serializacja jest proces konwersji stan obiektu do formularza, które mogą być utrwalone lub transportowane. Aby uzyskać więcej informacji, zobacz [serializacji](../../csharp/programming-guide/concepts/serialization/index.md). Gdy Serializacja jest ważna, utworzenie `class` lub `struct` jest preferowana w przypadku typów anonimowych lub typów krotek.

## <a name="performance"></a>Wydajność

Wydajność między tymi typami zależy od scenariusza. Istotny wpływ obejmuje kompromis między przydziałami i kopiowaniem. W większości scenariuszy wpływ jest mały. W przypadku wystąpienia poważnych wpływów należy podjąć pomiary w celu poinformowania o decyzji.

## <a name="conclusion"></a>Podsumowanie

Jako deweloper wybierający między krotki a typami anonimowymi, istnieje kilka czynników, które należy wziąć pod uwagę. Ogólnie mówiąc, jeśli nie pracujesz z [drzewami wyrażeń](../../csharp/expression-trees.md)i masz doświadczenie ze składnią krotek, wybierz <xref:System.ValueTuple> jako wartość typ wartości z elastycznością do nazwy właściwości. Jeśli pracujesz z drzewami wyrażeń i wolisz nazwać właściwości, wybierz typy anonimowe. W przeciwnym razie użyj <xref:System.Tuple> .

## <a name="see-also"></a>Zobacz także

- [Typy anonimowe](../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
- [Drzewa wyrażeń](../../csharp/expression-trees.md)
- [Framework — zalecenia dotyczące projektowania](index.md)
- [Typy krotek](../../csharp/tuples.md)
- [Typy — zalecenia dotyczące projektowania](type.md)

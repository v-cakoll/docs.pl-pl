---
title: Typy i zmienne języka C# — przewodnik po języku Języka C#
description: 'Dowiedz się więcej o definiowaniu typów i deklarowaniu zmiennych w języku C #'
ms.date: 02/25/2020
ms.assetid: f8a8051e-0049-43f1-b594-9c84cc7b1224
ms.openlocfilehash: b2a5255a243c12543a1cd59b5724b6c826306e04
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78159094"
---
# <a name="types-and-variables"></a>Typy i zmienne

Istnieją dwa rodzaje typów w języku C#: *typy wartości* i *typy odwołań*. Zmienne typów wartości bezpośrednio zawierają swoje dane, podczas gdy zmienne typów odwołań przechowują odwołania do ich danych, przy czym te ostatnie są znane jako obiekty. W przypadku typów odwołań możliwe jest, aby dwie zmienne odwoływały się do tego samego obiektu, a zatem możliwe, że operacje na jednej zmiennej wpływają na obiekt, do którego odwołuje się inna zmienna. W przypadku typów wartości zmienne mają własną kopię danych i nie jest możliwe, aby operacje `ref` na `out` jednym miały wpływ na inne (z wyjątkiem zmiennych parametrów i zmiennych parametrów).

Typy wartości języka C#są dalej dzielone na *typy proste,* *typy wyliczenia,* *typy struktury*i *wartości nullable*. Typy odwołań języka C#są dalej dzielone na *typy klas,* *typy interfejsów,* *typy tablic*i *typy delegatów.*

Poniższy konspekt zawiera omówienie systemu typów języka C#.

- [Typy wartości][ValueTypes]
  - [Typy proste][SimpleTypes]
    - Podpisana `sbyte`integralna: , `short`, `int``long`
    - Niepodpisana `byte`całka: , `ushort`, `uint``ulong`
    - Znaki Unicode:`char`
    - Binarny zmiennoprzecinkowy IEEE: `float`,`double`
    - Przestawny przecinkowy o wysokiej precyzji:`decimal`
    - Boolean:`bool`
  - [Typy wyliczenia][EnumTypes]
    - Typy formularzy zdefiniowane przez użytkownika`enum E {...}`
  - [Typy struktury][StructTypes]
    - Typy formularzy zdefiniowane przez użytkownika`struct S {...}`
  - [Typy wartości z możliwością null][NullableTypes]
    - Rozszerzenia wszystkich innych typów wartości `null` o wartości
- [Typy odwołań][ReferenceTypes]
  - [Typy klas][ClassTypes]
    - Ostateczna klasa podstawowa wszystkich innych typów:`object`
    - Ciągi Unicode:`string`
    - Typy formularzy zdefiniowane przez użytkownika`class C {...}`
  - [Typy interfejsów][InterfaceTypes]
    - Typy formularzy zdefiniowane przez użytkownika`interface I {...}`
  - [Typy tablic][ArrayTypes]
    - Na przykład jedno- i wielowymiarowe, `int[]` oraz`int[,]`
  - [Typy pełnomocników][DelegateTypes]
    - Typy formularzy zdefiniowane przez użytkownika`delegate int D(...)`

[ValueTypes]: ../language-reference/builtin-types/value-types.md
[SimpleTypes]: ../language-reference/builtin-types/value-types.md#built-in-value-types
[EnumTypes]: ../language-reference/builtin-types/enum.md
[StructTypes]: ../language-reference/builtin-types/struct.md
[NullableTypes]: ../language-reference/builtin-types/nullable-value-types.md
[ReferenceTypes]: ../language-reference/keywords/reference-types.md
[ClassTypes]: ../language-reference/keywords/class.md
[InterfaceTypes]: ../language-reference/keywords/interface.md
[DelegateTypes]: ../language-reference/keywords/delegate.md
[ArrayTypes]: ../programming-guide/arrays/index.md

Aby uzyskać więcej informacji na temat typów liczbowych, zobacz [Typy zintegrowane](../language-reference/builtin-types/integral-numeric-types.md) i Tabela [typów zmiennoprzecinkowych](../language-reference/builtin-types/floating-point-numeric-types.md).

Typ języka `bool` C#jest używany do reprezentowania wartości `true` logicznych — wartości, które są albo . `false`

Przetwarzanie znaków i ciągów w języku C# używa kodowania Unicode. Typ `char` reprezentuje jednostkę kodu UTF-16, `string` a typ reprezentuje sekwencję jednostek kodu UTF-16.

Programy C# używać *deklaracji typu* do tworzenia nowych typów. Deklaracja typu określa nazwę i elementy członkowskie nowego typu. Pięć kategorii typów języka C#jest definiowanych przez użytkownika: typy klas, typy struktur, typy interfejsów, typy wyliczenia i typy delegatów.

Typ `class` definiuje strukturę danych, która zawiera elementy członkowskie danych (pola) i elementy członkowskie funkcji (metody, właściwości i inne). Typy klas obsługują pojedyncze dziedziczenie i polimorfizm, mechanizmy, dzięki którym klasy pochodne mogą rozszerzać i specjalizować klasy podstawowe.

Typ `struct` jest podobny do typu klasy, ponieważ reprezentuje strukturę z członkami danych i członkami funkcji. Jednak w przeciwieństwie do klas struktury są typy wartości i zazwyczaj nie wymagają alokacji sterty. Typy struktury nie obsługują dziedziczenia określonego przez użytkownika, a wszystkie `object`typy struktury niejawnie dziedziczą z typu .

Typ `interface` definiuje kontrakt jako nazwany zestaw elementów członkowskich funkcji publicznych. A `class` `struct` lub implementuje `interface` implementuje implementuje implementacje elementów członkowskich funkcji interfejsu. Może `interface` dziedziczyć z wielu `class` interfejsów podstawowych i lub `struct` może implementować wiele interfejsów.

Typ `delegate` reprezentuje odwołania do metod z określoną listą parametrów i typem zwracanym. Delegaci umożliwiają traktowanie metod jako jednostek, które mogą być przypisane do zmiennych i przekazywane jako parametry. Delegaci są analogiczne do typów funkcji dostarczanych przez języki funkcjonalne. Są one również podobne do pojęcia wskaźników funkcji znaleźć w niektórych innych językach. W przeciwieństwie do wskaźników funkcji delegatów są zorientowane obiektowe i bezpieczne dla typu.

Program `class` `struct`, `interface`, `delegate` i typy wszystkich typów ogólnych obsługi, przy czym mogą być parametryzowane z innymi typami.

Typ `enum` jest odrębnym typem o nazwanych stałych. Każdy `enum` typ ma typ bazowy, który musi być jednym z ośmiu typów całek. Zestaw wartości `enum` typu jest taki sam jak zestaw wartości typu źródłowego.

C# obsługuje tablice jedno- i wielowymiarowe dowolnego typu. W przeciwieństwie do typów wymienionych powyżej typy tablicnie nie muszą być zadeklarowane, zanim będą mogły być używane. Zamiast tego typy tablic są konstruowane przez następujące nazwy typu z nawiasami kwadratowymi. `int[]` Na przykład, jest jednowymiarową `int` `int[,]` tablicą , jest `int`tablicą `int[][]` dwuwymiarową , i jest jednowymiarową tablicą jednowymiarowej tablicy `int`.

Typy wartości null również nie muszą być zadeklarowane, zanim będą mogły być używane. Dla każdego typu `T`wartości niepodlegających wartości null istnieje `T?`odpowiedni typ wartości nullable , który może posiadać dodatkową wartość, `null`. Na przykład `int?` jest typem, który może pomieścić dowolną 32-bitową wartość całkowitą lub wartość `null`.

System typu C#jest ujednolicony w taki sposób, `object`że wartość dowolnego typu może być traktowana jako . Każdy typ w języku C# bezpośrednio `object` lub pośrednio pochodzi od typu klasy i `object` jest ostateczną klasą podstawową wszystkich typów. Wartości typów odwołań są traktowane jako obiekty `object`po prostu przez wyświetlenie wartości jako typu . Wartości typów wartości są traktowane jako obiekty, wykonując operacje *bokserskie* i *rozpakowywania*. W poniższym `int` przykładzie wartość jest `object` konwertowana na `int`i z powrotem do .

[!code-csharp[Boxing](../../../samples/snippets/csharp/tour/types-and-variables/Program.cs#L1-L10)]

Gdy wartość typu wartości jest konwertowana `object`na `object` typ , wystąpienie, nazywane również "pole", jest przydzielane do przechowywania wartości, a wartość jest kopiowana do tego pola. I odwrotnie, `object` gdy odwołanie jest rzutowane na typ wartości, `object` sprawdzasię, że odwołanie jest polem właściwego typu wartości, a jeśli sprawdzenie zakończy się pomyślnie, wartość w polu jest kopiowana.

Ujednolicony system typów języka C#skutecznie oznacza, że typy wartości mogą stać się obiektami "na żądanie". Ze względu na unifikacji, biblioteki ogólnego przeznaczenia, które używają typu `object` mogą być używane zarówno z typami odwołań, jak i typami wartości.

Istnieje kilka rodzajów *zmiennych* w języku C#, w tym pola, elementy tablicy, zmienne lokalne i parametry. Zmienne reprezentują lokalizacje magazynu, a każda zmienna ma typ, który określa, jakie wartości mogą być przechowywane w zmiennej, jak pokazano poniżej.

- Typ wartości niezbywalnej
  - Wartość tego typu dokładnego
- Typ wartości z możliwością null
  - Wartość `null` lub wartość tego typu dokładnego
- obiekt
  - Odwołanie, `null` odwołanie do obiektu dowolnego typu odwołania lub odwołanie do wartości pudełkowej dowolnego typu wartości
- Typ klasy
  - Odwołanie, `null` odwołanie do wystąpienia tego typu klasy lub odwołanie do wystąpienia klasy pochodzącej z tego typu klasy
- Typ interfejsu
  - Odwołanie, `null` odwołanie do wystąpienia typu klasy, który implementuje tego typu interfejsu lub odwołanie do wartości pudełkowej typu wartości, która implementuje tego typu interfejsu
- Typ tablicy
  - Odwołanie, `null` odwołanie do wystąpienia tego typu tablicy lub odwołanie do wystąpienia zgodnego typu tablicy
- Typ pełnomocnika
  - Odwołanie `null` lub odwołanie do wystąpienia zgodnego typu delegata

> [!div class="step-by-step"]
> [Poprzedni](program-structure.md)
> [następny](expressions.md)

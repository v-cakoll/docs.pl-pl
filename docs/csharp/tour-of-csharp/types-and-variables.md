---
title: Typy i zmienne języka c# — samouczek języka C#
description: 'Informacje na temat definiowania typów i deklarowania zmiennych w języku C #'
ms.date: 04/24/2020
ms.assetid: f8a8051e-0049-43f1-b594-9c84cc7b1224
ms.openlocfilehash: a14291d1eec4d090b0275875326c5a580e5abe9d
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174130"
---
# <a name="types-and-variables"></a>Typy i zmienne

Istnieją dwa rodzaje typów w języku C#: *typy wartości* i *typy referencyjne*. Zmienne typów wartości bezpośrednio zawierają swoje dane, a zmienne typów referencyjnych przechowują odwołania do danych, które są znane jako obiekty. W przypadku typów referencyjnych istnieje możliwość, że dwie zmienne odwołują się do tego samego obiektu, w tym przypadku operacje na jednej zmiennej mają wpływ na obiekt, do którego odwołuje się inna zmienna. W przypadku typów wartości zmiennych każda z nich ma własną kopię danych i nie jest możliwe wykonywanie operacji na nich, aby wpływać na drugą (z wyjątkiem `ref` `out` zmiennych i parametrów).

Typy wartości języka C# są dalej podzielone na *typy proste*, *typy wyliczeniowe*, *typy struktur*i *typy wartości null*. Typy odwołań języka C# są dalej podzielone na *typy klas*, *typy interfejsów*, *Typy tablic*i *typy delegatów*.

Poniższy konspekt zawiera omówienie systemu typów języka C#.

- [Typy wartości][ValueTypes]
  - [Typy proste][SimpleTypes]
    - Całkowita część ze znakiem: `sbyte` ,, `short` `int` ,`long`
    - Całka bez znaku: `byte` ,, `ushort` `uint` ,`ulong`
    - Znaki Unicode:`char`
    - Binarny zmiennoprzecinkowy IEEE: `float` ,`double`
    - Zmiennoprzecinkowa liczba dziesiętna o dużej precyzji:`decimal`
    - Typu`bool`
  - [Typy wyliczeniowe][EnumTypes]
    - Typy formularza zdefiniowane przez użytkownika`enum E {...}`
  - [Typy struktur][StructTypes]
    - Typy formularza zdefiniowane przez użytkownika`struct S {...}`
  - [Typy wartości dopuszczające wartość null][NullableTypes]
    - Rozszerzenia wszystkich innych typów wartości z `null` wartością
  - [Typy wartości krotki][TupleTypes]
    - Typy formularza zdefiniowane przez użytkownika`(T1, T2, ...)`
- [Typy odwołań][ReferenceTypes]
  - [Typy klas][ClassTypes]
    - Ostateczna Klasa bazowa dla wszystkich innych typów:`object`
    - Ciągi Unicode:`string`
    - Typy formularza zdefiniowane przez użytkownika`class C {...}`
  - [Typy interfejsów][InterfaceTypes]
    - Typy formularza zdefiniowane przez użytkownika`interface I {...}`
  - [Typy tablic][ArrayTypes]
    - Pojedyncze i wielowymiarowe, na przykład `int[]` i`int[,]`
  - [Typy delegatów][DelegateTypes]
    - Typy formularza zdefiniowane przez użytkownika`delegate int D(...)`

[ValueTypes]: ../language-reference/builtin-types/value-types.md
[SimpleTypes]: ../language-reference/builtin-types/value-types.md#built-in-value-types
[EnumTypes]: ../language-reference/builtin-types/enum.md
[StructTypes]: ../language-reference/builtin-types/struct.md
[NullableTypes]: ../language-reference/builtin-types/nullable-value-types.md
[TupleTypes]: ../language-reference/builtin-types/value-tuples.md
[ReferenceTypes]: ../language-reference/keywords/reference-types.md
[ClassTypes]: ../language-reference/keywords/class.md
[InterfaceTypes]: ../language-reference/keywords/interface.md
[DelegateTypes]: ../language-reference/keywords/delegate.md
[ArrayTypes]: ../programming-guide/arrays/index.md

Aby uzyskać więcej informacji na temat typów liczbowych, zobacz [Typy całkowite](../language-reference/builtin-types/integral-numeric-types.md) i [Tabela typów zmiennoprzecinkowych](../language-reference/builtin-types/floating-point-numeric-types.md).

Typ języka C# `bool` jest używany do reprezentowania wartości logicznych — wartości, które są albo `true` lub `false` .

Przetwarzanie znaków i ciągów w języku C# używa kodowania Unicode. `char`Typ reprezentuje jednostkę kodu UTF-16, a `string` Typ reprezentuje sekwencję jednostek kodu UTF-16.

Programy w języku C# używają *deklaracji typów* do tworzenia nowych typów. Deklaracja typu określa nazwę i składowe nowego typu. Pięć kategorii typów języka C# jest definiowanych przez użytkownika: typy klas, typy struktur, typy interfejsów, typy wyliczeniowe i typy delegatów.

`class`Typ definiuje strukturę danych, która zawiera składowe danych (pola) i składowe funkcji (metody, właściwości i inne). Typy klas obsługują pojedyncze dziedziczenie i polimorfizm, czyli mechanizmy, w których klasy pochodne mogą poszerzać i specjalizację klas bazowych.

`struct`Typ jest podobny do typu klasy w tym, że reprezentuje strukturę z składowymi danych i składowymi funkcji. Jednak w przeciwieństwie do klas, struktury są typami wartości i nie wymagają zazwyczaj alokacji sterty. Typy struktur nie obsługują dziedziczenia określonego przez użytkownika, a wszystkie typy struktur niejawnie dziedziczą po typie `object` .

`interface`Typ definiuje kontrakt jako nazwany zestaw elementów członkowskich funkcji publicznych. A `class` lub `struct` implementujący `interface` musi zapewniać implementacje elementów członkowskich funkcji interfejsu. `interface`Może dziedziczyć z wielu interfejsów podstawowych, a `class` lub `struct` może zaimplementować wiele interfejsów.

`delegate`Typ reprezentuje odwołania do metod z określoną listą parametrów i zwracanym typem. Delegaty umożliwiają traktowanie metod jako jednostek, które mogą być przypisane do zmiennych i przekazane jako parametry. Delegaty są analogiczne do typów funkcji zapewnianych przez Języki funkcjonalne. Są one również podobne do koncepcji wskaźników funkcji, które znajdują się w innych językach. W przeciwieństwie do wskaźników funkcji Delegaty są zorientowane obiektowo i są bezpieczne dla typów.

`class` `struct` `interface` Wszystkie typy,,, i są `delegate` obsługiwane przez wszystkie typy ogólne, dzięki czemu można je sparametryzowane z innymi typami.

`enum`Typ jest typem odrębnym o nazwanych stałych. Każdy `enum` Typ ma typ podstawowy, który musi być jednym z ośmiu typów całkowitych. Zestaw wartości `enum` typu jest taki sam jak zestaw wartości typu podstawowego.

Język C# obsługuje tablice o pojedynczym i wielowymiarowym dowolnego typu. W przeciwieństwie do typów wymienionych powyżej, typy tablicy nie muszą być zadeklarowane przed użyciem. Zamiast tego typy tablic są konstruowane przez następujące nazwy typu z nawiasami kwadratowymi. Na przykład `int[]` jest tablicą jednowymiarową `int` , `int[,]` która jest tablicą dwuwymiarową `int` , i `int[][]` jest jednowymiarową tablicą jednowymiarowej tablicy `int` .

Nie trzeba również deklarować typów wartości dopuszczających wartość null, aby można było ich używać. Dla każdego typu wartości, który nie dopuszcza wartości null `T` , istnieje odpowiedni typ wartości null `T?` , który może zawierać dodatkową wartość `null` . Na przykład `int?` jest typem, który może zawierać dowolną 32-bitową liczbę całkowitą lub wartość `null` .

System typów języka C# jest jednorodny tak, że wartość dowolnego typu może być traktowana jako `object` . Każdy typ w języku C# bezpośrednio lub pośrednio pochodzi od `object` typu klasy i `object` jest ostateczną klasą bazową wszystkich typów. Wartości typów referencyjnych są traktowane jako obiekty, po prostu wyświetlając wartości jako typ `object` . Wartości typów wartości są traktowane jako obiekty *przez wykonywanie* *operacji pakowania*i rozpakowywania. W poniższym przykładzie `int` wartość jest konwertowana na `object` i z powrotem do `int` .

[!code-csharp[Boxing](../../../samples/snippets/csharp/tour/types-and-variables/Program.cs#L1-L10)]

Gdy wartość typu wartości jest przypisana do `object` odwołania, pole "Box" jest przydzielane do przechowywania wartości. To pole jest wystąpieniem typu odwołania, a wartość jest kopiowana do tego pola. Z drugiej strony, gdy `object` odwołanie jest rzutowane na typ wartości, jest wykonywane sprawdzenie, że odwołanie `object` jest polem o poprawnym typie wartości. Jeśli sprawdzenie zakończy się powodzeniem, wartość w polu jest kopiowana do typu wartości.

Ujednolicony system typów języka C# efektywnie oznacza, że typy wartości są traktowane jako `object` odwołania "na żądanie". Ze względu na nieujednolicenie biblioteki ogólnego przeznaczenia używające typu `object` można używać ze wszystkimi typami, które pochodzą od `object` , w tym typy odwołań i typy wartości.

W języku C# istnieje kilka rodzajów *zmiennych* , w tym pola, elementy tablicy, zmienne lokalne i parametry. Zmienne reprezentują lokalizacje przechowywania, a Każda zmienna ma typ, który określa, jakie wartości mogą być przechowywane w zmiennej, jak pokazano poniżej.

- Typ wartości niedopuszczający wartości null
  - Wartość tego dokładnego typu
- Typ wartości null
  - `null`Wartość lub wartość tego dokładnego typu
- object
  - `null`Odwołanie, odwołanie do obiektu dowolnego typu odwołania lub odwołanie do wartości opakowanej dowolnego typu wartości
- Typ klasy
  - `null`Odwołanie, odwołanie do wystąpienia tego typu klasy lub odwołanie do wystąpienia klasy pochodzącej od tego typu klasy
- Typ interfejsu
  - `null`Odwołanie, odwołanie do wystąpienia typu klasy implementującego ten typ interfejsu lub odwołanie do wartości opakowanej typu wartości implementującej ten typ interfejsu
- Typ tablicy
  - `null`Odwołanie, odwołanie do wystąpienia tego typu tablicy lub odwołanie do wystąpienia zgodnego typu tablicy
- Typ delegata
  - `null`Odwołanie lub odwołanie do wystąpienia zgodnego typu delegata

> [!div class="step-by-step"]
> [Poprzedni](program-structure.md) 
>  [Dalej](expressions.md)

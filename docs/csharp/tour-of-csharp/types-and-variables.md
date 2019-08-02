---
title: C#Typy i zmienne — Przewodnik po C# języku
description: Dowiedz się więcej na temat definiowania typów i deklarowania zmiennych wC#
ms.date: 08/10/2016
ms.assetid: f8a8051e-0049-43f1-b594-9c84cc7b1224
ms.openlocfilehash: f06894d986973e4394b0586906d67ef41a9d9152
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/26/2019
ms.locfileid: "67661068"
---
# <a name="types-and-variables"></a>Typy i zmienne

Istnieją dwa rodzaje typów w C#: *typy wartości* i *typy odwołań*. Zmienne typów wartości bezpośrednio zawierają swoje dane, a zmienne typów referencyjnych przechowują odwołania do danych, które są znane jako obiekty. W przypadku typów referencyjnych istnieje możliwość, że dwie zmienne odwołują się do tego samego obiektu, w tym przypadku operacje na jednej zmiennej mają wpływ na obiekt, do którego odwołuje się inna zmienna. W przypadku typów wartości zmiennych każda z nich ma własną kopię danych i nie jest możliwe wykonywanie operacji na nich, aby wpływać na inne (z wyjątkiem `ref` zmiennych i `out` parametrów).

C#typy wartości są dalej podzielone na *typy proste*, *typy*wyliczeniowe, *typy struktur*i *typy wartości null*. C#typy odwołań są dalej podzielone na *typy klas*, *typy interfejsów*, *Typy tablic*i *typy delegatów*.

Poniżej przedstawiono omówienie C#systemu typu.

* [Typy wartości][ValueTypes]
  - [Typy proste][SimpleTypes]
    * Całkowita część ze `sbyte`znakiem `int`:, `short`,,`long`
    * Całka bez `byte`znaku `ushort`: `uint`,,,`ulong`
    * Znaki Unicode:`char`
    * Binarny zmiennoprzecinkowy IEEE: `float`,`double`
    * Zmiennoprzecinkowa liczba dziesiętna o dużej precyzji:`decimal`
    * Typu`bool`
  - [Typy wyliczeniowe][EnumTypes]
    * Typy formularza zdefiniowane przez użytkownika`enum E {...}`
  - [Typy struktur][StructTypes]
    * Typy formularza zdefiniowane przez użytkownika`struct S {...}`
  - [Typy wartości null][NullableTypes]
    * Rozszerzenia wszystkich innych typów wartości z `null` wartością
* [Typy odwołań][ReferenceTypes]
  - [Typy klas][ClassTypes]
    * Ostateczna Klasa bazowa dla wszystkich innych typów:`object`
    * Ciągi Unicode:`string`
    * Typy formularza zdefiniowane przez użytkownika`class C {...}`
  - [Typy interfejsów][InterfaceTypes]
    * Typy formularza zdefiniowane przez użytkownika`interface I {...}`
  - [Typy tablic][ArrayTypes]
    * Pojedyncze i wielowymiarowe, na przykład `int[]` i`int[,]`
  - [Typy delegatów][DelegateTypes]
    * Typy formularza zdefiniowane przez użytkownika`delegate int D(...)`

[ValueTypes]: ../language-reference/keywords/value-types-table.md
[SimpleTypes]: ../language-reference/keywords/value-types.md#simple-types
[EnumTypes]: ../language-reference/keywords/enum.md
[StructTypes]: ../language-reference/keywords/struct.md
[NullableTypes]: ../programming-guide/nullable-types/index.md
[ReferenceTypes]: ../language-reference/keywords/reference-types.md
[ClassTypes]: ../language-reference/keywords/class.md
[InterfaceTypes]: ../language-reference/keywords/interface.md
[DelegateTypes]: ../language-reference/keywords/delegate.md
[ArrayTypes]: ../programming-guide/arrays/index.md

Aby uzyskać więcej informacji na temat typów liczbowych, zobacz [Typy całkowite](../language-reference/builtin-types/integral-numeric-types.md) i [Tabela typów zmiennoprzecinkowych](../language-reference/builtin-types/floating-point-numeric-types.md).

C#Typ jest używany do reprezentowania wartości logicznych — wartości, które `true` są lub `false`. `bool`

Przetwarzanie znaków i ciągów w C# programie używa kodowania Unicode. Typ reprezentuje jednostkę kodu UTF-16, `string` a typ reprezentuje sekwencję jednostek kodu UTF-16. `char`

C#programy używają *deklaracji typu* do tworzenia nowych typów. Deklaracja typu określa nazwę i składowe nowego typu. C#Pięć kategorii typów są definiowane przez użytkownika: typy klas, typy struktur, typy interfejsów, typy wyliczeniowe i typy delegatów.

`class` Typ definiuje strukturę danych, która zawiera składowe danych (pola) i składowe funkcji (metody, właściwości i inne). Typy klas obsługują pojedyncze dziedziczenie i polimorfizm, czyli mechanizmy, w których klasy pochodne mogą poszerzać i specjalizację klas bazowych.

`struct` Typ jest podobny do typu klasy w tym, że reprezentuje strukturę z składowymi danych i składowymi funkcji. Jednak w przeciwieństwie do klas, struktury są typami wartości i nie wymagają zazwyczaj alokacji sterty. Typy struktur nie obsługują dziedziczenia określonego przez użytkownika, a wszystkie typy struktur niejawnie dziedziczą `object`po typie.

`interface` Typ definiuje kontrakt jako nazwany zestaw elementów członkowskich funkcji publicznych. A `class` lub `struct` implementujący`interface` musi zapewniać implementacje elementów członkowskich funkcji interfejsu. Może dziedziczyć z wielu interfejsów podstawowych, `class` a lub `struct` może zaimplementować wiele interfejsów. `interface`

`delegate` Typ reprezentuje odwołania do metod z określoną listą parametrów i zwracanym typem. Delegaty umożliwiają traktowanie metod jako jednostek, które mogą być przypisane do zmiennych i przekazane jako parametry. Delegaty są analogiczne do typów funkcji zapewnianych przez Języki funkcjonalne. Są one również podobne do koncepcji wskaźników funkcji, które znajdują się w innych językach, ale w przeciwieństwie do wskaźników funkcji, Delegaty są zorientowane obiektowo i są bezpieczne dla typów.

`class` ,`interface` , I typy`delegate` wszystkie obsługują ogólne, za pomocą których można sparametryzowane z innymi typami. `struct`

`enum` Typ jest typem odrębnym o nazwanych stałych. Każdy `enum` typ ma typ podstawowy, który musi być jednym z ośmiu typów całkowitych. Zestaw wartości `enum` typu jest taki sam jak zestaw wartości typu podstawowego.

C#obsługuje tablice pojedynczych i wielowymiarowych dowolnego typu. W przeciwieństwie do typów wymienionych powyżej, typy tablicy nie muszą być zadeklarowane przed użyciem. Zamiast tego typy tablic są konstruowane przez następujące nazwy typu z nawiasami kwadratowymi. Na przykład `int[]` jest `int` `int` `int`tablicą jednowymiarową, `int[,]` która jest tablicą dwuwymiarową, i `int[][]` jest jednowymiarową tablicą jednowymiarowej tablicy.

Nie trzeba również deklarować typów wartości null, aby można było ich używać. Dla każdego typu `T` wartości niedopuszczających wartości null istnieje odpowiedni typ `T?`wartości null, który może `null`zawierać dodatkową wartość. Na przykład `int?` jest typem, który może zawierać dowolną 32-bitową liczbę całkowitą lub wartość `null`.

C#System typów jest jednorodny, aby wartość dowolnego typu mogła być traktowana jako `object`. Każdy typ C# bezpośrednio lub pośrednio pochodzi od `object` typu klasy i `object` jest ostateczną klasą bazową wszystkich typów. Wartości typów referencyjnych są traktowane jako obiekty, po prostu wyświetlając wartości jako typ `object`. Wartości typów wartości są traktowane jako obiekty *przez wykonywanie* *operacji pakowania*i rozpakowywania. W poniższym przykładzie `int` wartość jest konwertowana na `object` i z powrotem do `int`.

[!code-csharp[Boxing](../../../samples/snippets/csharp/tour/types-and-variables/Program.cs#L1-L10)]

Gdy wartość typu wartości jest konwertowana na typ `object` `object` , wystąpienie, nazywane również "polem", jest przydzielone do przechowywania wartości, a wartość jest kopiowana do tego pola. Z drugiej strony, `object` gdy odwołanie jest rzutowane na typ wartości, jest wykonywane sprawdzenie, że odwołanie `object` jest polem poprawnego typu wartości i, jeśli sprawdzenie zakończy się powodzeniem, wartość w polu jest kopiowana.

C#ujednolicony system typów efektywnie oznacza, że typy wartości mogą stać się obiektami "na żądanie". Ze względu na niezjednoczenie bibliotek ogólnego przeznaczenia, które używają `object` typu, można używać zarówno z typami referencyjnymi, jak i typami wartości.

W programie istnieją różne rodzaje *zmiennych* , w C#tym pola, elementy tablicy, zmienne lokalne i parametry. Zmienne reprezentują lokalizacje przechowywania, a Każda zmienna ma typ, który określa, jakie wartości mogą być przechowywane w zmiennej, jak pokazano poniżej.

* Typ wartości niedopuszczający wartości null
  - Wartość tego dokładnego typu
* Typ wartości null
  - `null` Wartość lub wartość tego dokładnego typu
* object
  - `null` Odwołanie, odwołanie do obiektu dowolnego typu odwołania lub odwołanie do wartości opakowanej dowolnego typu wartości
* Typ klasy
  - `null` Odwołanie, odwołanie do wystąpienia tego typu klasy lub odwołanie do wystąpienia klasy pochodzącej od tego typu klasy
* Typ interfejsu
  - `null` Odwołanie, odwołanie do wystąpienia typu klasy implementującego ten typ interfejsu lub odwołanie do wartości opakowanej typu wartości implementującej ten typ interfejsu
* Typ tablicy
  - `null` Odwołanie, odwołanie do wystąpienia tego typu tablicy lub odwołanie do wystąpienia zgodnego typu tablicy
* Typ delegata
  - `null` Odwołanie lub odwołanie do wystąpienia zgodnego typu delegata

> [!div class="step-by-step"]
> [Poprzedni](program-structure.md)Następny
> [](expressions.md)

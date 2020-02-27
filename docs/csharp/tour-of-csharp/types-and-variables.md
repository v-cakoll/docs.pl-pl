---
title: C#Typy i zmienne — Przewodnik po C# języku
description: Dowiedz się więcej na temat definiowania typów i deklarowania zmiennych wC#
ms.date: 08/10/2016
ms.assetid: f8a8051e-0049-43f1-b594-9c84cc7b1224
ms.openlocfilehash: 571e346d1e46be798dca1b42cfcc2af3aa65e641
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77627568"
---
# <a name="types-and-variables"></a>Typy i zmienne

Istnieją dwa rodzaje typów w C#: *typy wartości* i *typy odwołań*. Zmienne typów wartości bezpośrednio zawierają swoje dane, a zmienne typów referencyjnych przechowują odwołania do danych, które są znane jako obiekty. W przypadku typów referencyjnych istnieje możliwość, że dwie zmienne odwołują się do tego samego obiektu, w tym przypadku operacje na jednej zmiennej mają wpływ na obiekt, do którego odwołuje się inna zmienna. W przypadku typów wartości zmiennych każda z nich ma własną kopię danych i nie jest możliwe wykonywanie operacji na nich, aby wpływać na drugą (z wyjątkiem `ref` i `out` zmiennych parametrów).

C#typy wartości są dalej podzielone na *typy proste*, *typy wyliczeniowe*, *typy struktur*i *typy wartości null*. C#typy odwołań są dalej podzielone na *typy klas*, *typy interfejsów*, *Typy tablic*i *typy delegatów*.

Poniżej przedstawiono omówienie C#systemu typu.

- [Typy wartości][ValueTypes]
  - [Typy proste][SimpleTypes]
    - Część ze znakiem: `sbyte`, `short`, `int``long`
    - Całka bez znaku: `byte`, `ushort`, `uint``ulong`
    - Znaki Unicode: `char`
    - Binarny zmiennoprzecinkowy IEEE: `float`, `double`
    - Zmiennoprzecinkowa liczba dziesiętna o dużej precyzji: `decimal`
    - Wartość logiczna: `bool`
  - [Typy wyliczeniowe][EnumTypes]
    - Typy formularzy `enum E {...}` zdefiniowane przez użytkownika
  - [Typy struktur][StructTypes]
    - Typy formularzy `struct S {...}` zdefiniowane przez użytkownika
  - [Typy wartości null][NullableTypes]
    - Rozszerzenia wszystkich innych typów wartości z wartością `null`
- [Typy odwołań][ReferenceTypes]
  - [Typy klas][ClassTypes]
    - Ultimate Klasa bazowa dla wszystkich innych typów: `object`
    - Ciągi Unicode: `string`
    - Typy formularzy `class C {...}` zdefiniowane przez użytkownika
  - [Typy interfejsów][InterfaceTypes]
    - Typy formularzy `interface I {...}` zdefiniowane przez użytkownika
  - [Typy tablic][ArrayTypes]
    - Pojedyncze i wielowymiarowe, na przykład `int[]` i `int[,]`
  - [Typy delegatów][DelegateTypes]
    - Typy formularzy `delegate int D(...)` zdefiniowane przez użytkownika

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

Aby uzyskać więcej informacji na temat typów liczbowych, zobacz [Typy całkowite](../language-reference/builtin-types/integral-numeric-types.md) i [Tabela typów zmiennoprzecinkowych](../language-reference/builtin-types/floating-point-numeric-types.md).

C#Typ `bool` jest używany do reprezentowania wartości logicznych — wartości `true` lub `false`.

Przetwarzanie znaków i ciągów w C# programie używa kodowania Unicode. Typ `char` reprezentuje jednostkę kodu UTF-16, a typ `string` reprezentuje sekwencję jednostek kodu UTF-16.

C#programy używają *deklaracji typu* do tworzenia nowych typów. Deklaracja typu określa nazwę i składowe nowego typu. C#Pięć kategorii typów są definiowane przez użytkownika: typy klas, typy struktur, typy interfejsów, typy wyliczeniowe i typy delegatów.

Typ `class` definiuje strukturę danych, która zawiera składowe danych (pola) i składowe funkcji (metody, właściwości i inne). Typy klas obsługują pojedyncze dziedziczenie i polimorfizm, czyli mechanizmy, w których klasy pochodne mogą poszerzać i specjalizację klas bazowych.

Typ `struct` jest podobny do typu klasy w tym, że reprezentuje strukturę z elementami członkowskimi danych i składowymi funkcji. Jednak w przeciwieństwie do klas, struktury są typami wartości i nie wymagają zazwyczaj alokacji sterty. Typy struktur nie obsługują dziedziczenia określonego przez użytkownika, a wszystkie typy struktur niejawnie dziedziczą z typu `object`.

Typ `interface` definiuje kontrakt jako nazwany zestaw elementów członkowskich funkcji publicznych. `class` lub `struct` implementujące `interface` musi dostarczać implementacje składowych funkcji interfejsu. `interface` może dziedziczyć z wielu interfejsów podstawowych, a `class` lub `struct` może zaimplementować wiele interfejsów.

Typ `delegate` reprezentuje odwołania do metod z określoną listą parametrów i zwracanym typem. Delegaty umożliwiają traktowanie metod jako jednostek, które mogą być przypisane do zmiennych i przekazane jako parametry. Delegaty są analogiczne do typów funkcji zapewnianych przez Języki funkcjonalne. Są one również podobne do koncepcji wskaźników funkcji, które znajdują się w innych językach, ale w przeciwieństwie do wskaźników funkcji, Delegaty są zorientowane obiektowo i są bezpieczne dla typów.

`class`, `struct`, `interface` i `delegate` obsługują typy ogólne, dzięki czemu można je sparametryzowane z innymi typami.

Typ `enum` jest typem odrębnym o nazwanych stałych. Każdy typ `enum` ma typ podstawowy, który musi być jednym z ośmiu typów całkowitych. Zestaw wartości typu `enum` jest taki sam jak zestaw wartości typu podstawowego.

C#obsługuje tablice pojedynczych i wielowymiarowych dowolnego typu. W przeciwieństwie do typów wymienionych powyżej, typy tablicy nie muszą być zadeklarowane przed użyciem. Zamiast tego typy tablic są konstruowane przez następujące nazwy typu z nawiasami kwadratowymi. Na przykład `int[]` jest tablicą jednowymiarową `int`, `int[,]` jest dwuwymiarową tablicą `int`, a `int[][]` to Jednowymiarowa tablica jednowymiarowej tablicy `int`.

Nie trzeba również deklarować typów wartości null, aby można było ich używać. Dla każdego typu wartości niedopuszczających wartości null `T` istnieje odpowiedni typ wartości null `T?`, który może zawierać dodatkową wartość, `null`. Na przykład `int?` jest typem, który może zawierać dowolną 32-bitową liczbę całkowitą lub `null`wartość.

C#System typów jest jednorodny tak, że wartość dowolnego typu może być traktowana jako `object`. Każdy typ C# bezpośrednio lub pośrednio pochodzi od typu klasy `object`, a `object` jest ostateczną klasą bazową wszystkich typów. Wartości typów referencyjnych są traktowane jako obiekty po prostu przez wyświetlanie wartości jako typu `object`. Wartości typów wartości są traktowane jako obiekty *przez wykonywanie* *operacji pakowania*i rozpakowywania. W poniższym przykładzie wartość `int` jest konwertowana na `object` i z powrotem do `int`.

[!code-csharp[Boxing](../../../samples/snippets/csharp/tour/types-and-variables/Program.cs#L1-L10)]

Gdy wartość typu wartości jest konwertowana na typ `object`, wystąpienie `object`, zwane również "polem", jest przydzielone do przechowywania wartości, a wartość jest kopiowana do tego pola. Z drugiej strony, gdy odwołanie `object` jest rzutowane na typ wartości, jest wykonywane sprawdzenie, że odwołanie `object` jest polem poprawnego typu wartości i, jeśli sprawdzenie zakończy się powodzeniem, wartość w polu jest kopiowana.

C#ujednolicony system typów efektywnie oznacza, że typy wartości mogą stać się obiektami "na żądanie". Ze względu na nieujednolicenie biblioteki ogólnego przeznaczenia używające typu `object` mogą być używane z obydwoma typami referencyjnymi i typami wartości.

W programie istnieją różne rodzaje *zmiennych* , w C#tym pola, elementy tablicy, zmienne lokalne i parametry. Zmienne reprezentują lokalizacje przechowywania, a Każda zmienna ma typ, który określa, jakie wartości mogą być przechowywane w zmiennej, jak pokazano poniżej.

- Typ wartości niedopuszczający wartości null
  - Wartość tego dokładnego typu
- Typ wartości null
  - Wartość `null` lub wartość tego dokładnego typu
- obiekt
  - Odwołanie `null`, odwołanie do obiektu dowolnego typu odwołania lub odwołanie do wartości opakowanej dowolnego typu wartości
- Typ klasy
  - Odwołanie `null`, odwołanie do wystąpienia tego typu klasy lub odwołanie do wystąpienia klasy pochodzącej od tego typu klasy
- Typ interfejsu
  - Odwołanie `null`, odwołanie do wystąpienia typu klasy implementującego ten typ interfejsu lub odwołanie do wartości opakowanej typu wartości implementującej ten typ interfejsu
- Typ tablicy
  - Odwołanie `null`, odwołanie do wystąpienia tego typu tablicy lub odwołanie do wystąpienia zgodnego typu tablicy
- Typ delegata
  - Odwołanie `null` lub odwołanie do wystąpienia zgodnego typu delegata

> [!div class="step-by-step"]
> [Poprzednie](program-structure.md)
> [dalej](expressions.md)

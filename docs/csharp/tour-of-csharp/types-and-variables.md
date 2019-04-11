---
title: C#Typy i zmienne — Przewodnik po przykładzie C# języka
description: Informacje na temat definiowania typów i zadeklarowania zmiennych wC#
ms.date: 08/10/2016
ms.assetid: f8a8051e-0049-43f1-b594-9c84cc7b1224
ms.openlocfilehash: 552066ff8d17d49dc5cc0bbb60b05c9c3e5f8eda
ms.sourcegitcommit: 859b2ba0c74a1a5a4ad0d59a3c3af23450995981
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/11/2019
ms.locfileid: "59481083"
---
# <a name="types-and-variables"></a>Typy i zmienne

Istnieją dwa rodzaje typów w języku C#: *typy wartości* i *typy odwołań*. Zmienne typu wartości zawierają bezpośrednio swoje dane, natomiast zmiennych typu referencyjnego są przechowywane odwołania do swoich danych, te ostatnie są nazywane obiektów. W przypadku typów referencyjnych jest możliwe w dwóch zmiennych odwoływać się do tego samego obiektu i dlatego możliwe dla operacji na jednej zmiennej miały wpływ na obiekt odwołuje się druga zmienna. Z typami wartości zmiennych każda ma własne kopię danych i nie jest możliwe dla operacji na jednym wpłynie na inne (z wyjątkiem w przypadku właściwości `ref` i `out` zmiennych parametrów).

C#dla typów wartości są podzielone na *typów prostych*, *typach wyliczeniowych*, *typy struktury*, i *typy o wartości zerowalnej*. C#na typy odwołań są podzielone na *klasy typów*, *typy interfejsów*, *tablicy typów*, i *typy delegatów*.

Poniżej znajdują się z omówieniem C#przez system typów.

* Typy wartości
  - Typy proste
    * Podpisana całkowitego: `sbyte`, `short`, `int`, `long`
    * Całkowite bez znaku: `byte`, `ushort`, `uint`, `ulong`
    * Znaki Unicode: `char`
    * Liczba zmiennoprzecinkowa IEEE: `float`, `double`
    * Decimal wysokiej precyzji: `decimal`
    * Boolean: `bool`
  - Typach wyliczeniowych
    * Typy zdefiniowane przez użytkownika w postaci `enum E {...}`
  - Typy — struktura
    * Typy zdefiniowane przez użytkownika w postaci `struct S {...}`
  - Typy o wartości zerowalnej
    * Rozszerzenia z innych typów wartości za pomocą `null` wartość
* Typy odwołań
  - Typy klas
    * Ultimate klasa bazowa innych typów: `object`
    * Ciągi Unicode: `string`
    * Typy zdefiniowane przez użytkownika w postaci `class C {...}`
  - Typy interfejsów
    * Typy zdefiniowane przez użytkownika w postaci `interface I {...}`
  - Typy tablic
    * Jedno - i są one wielowymiarowe, na przykład `int[]` i `int[,]`
  - Typy delegatów
    * Typy zdefiniowane przez użytkownika w postaci `delegate int D(...)`

Osiem typów całkowitych zapewniają obsługę wartości 8-bitową, 16-bitowych, 32-bitowych i 64-bitowe podpisane lub niepodpisane formularza.

Dwa typy zmiennoprzecinkowe, `float` i `double`, są reprezentowane przy użyciu 32-bitowe o pojedynczej dokładności i 64-bitowych podwójnej precyzji IEC 60559 formatów, odpowiednio.

`decimal` Typ to typ danych 128-bitowych, odpowiedni do obliczeń finansowych i walutowych.

C#firmy `bool` typ jest używany do reprezentowania wartości logicznych — wartości, które są albo `true` lub `false`.

Znakowe i przetwarzania w języku C# przy użyciu kodowania Unicode. `char` Typ reprezentuje jednostkę kodu UTF-16 i `string` typu reprezentuje sekwencję jednostki kodu UTF-16.

To znajduje się podsumowanie C#na typy liczbowe.

* Całkowite podpisem
  - `sbyte`:  8 bitów, z zakresu od -128 do 127
  - `short`: 16 bitów, z zakresu od-32 768 do 32 767 znaków
  - `int`  : 32-bitowy, do zakresu od -2,147,483,648 do 2 147 483 647
  - `long` : 64-bitowy, do zakresu od-9,223,372,036,854,775,808 do 9,223,372,036,854,775,807
* Całkowite bez znaku
  - `byte`   :  8 bitów, z zakresu od 0 do 255
  - `ushort` : 16 bitów, z zakresu od 0 do 65 535 działań
  - `uint`   : 32-bitowy z zakresu od 0 do 4 294 967 295
  - `ulong`  : 64-bitowy z zakresu od 0 do 18,446,744,073,709,551,615
* Liczba zmiennoprzecinkowa
  - `float`  : 32-bitowy, do zakresu od 1,5 x 10<sup>-45</sup> do 3,4 x 10<sup>38</sup>, dokładności 7 cyfr
  - `double` : 64-bitowy, do zakresu od 5.0 x 10<sup>-324</sup> do wersji 1.7 x 10<sup>308</sup>, dokładności 15 cyfr
* Wartość dziesiętna
  - `decimal` : 128 bitów — zakres jest co najmniej od -7,9 x 10<sup>-28</sup> do 7,9 x 10<sup>28</sup>, z dokładnością co najmniej 28-cyfrowy

C# programy użyj *wpisz deklaracje* do tworzenia nowych typów. Deklaracja typu Określa nazwę i elementy członkowskie nowego typu. Pięciu C#firmy kategorie typów są definiowane przez użytkownika: klasy, typy, typy struktury, typy interfejsów, typach wyliczeniowych i typy delegatów.

A `class` typ definiuje strukturę danych, który zawiera elementy członkowskie danych (pola) i składowe funkcji (metody, właściwości i inne). Typy klas obsługuje pojedyncze dziedziczenie i polimorfizmu, mechanizmów, według której rozszerzać i specialize klas bazowych klas pochodnych.

A `struct` typ jest podobny do typu klasy, w tym, że reprezentuje strukturę z elementów członkowskich danych i składowe funkcji. W przeciwieństwie do klasy, struktury są typami wartości i zazwyczaj nie angażuje Alokacja sterty. Typy struktury nie obsługują dziedziczenia określonych przez użytkownika, a wszystkie typy struktury niejawnie dziedziczą z typu `object`.

`interface` Typ definiuje kontrakt jako nazwany zestaw funkcji publicznych elementów członkowskich. A `class` lub `struct` implementującej `interface` muszą dostarczać implementacje interfejsu funkcji składowych. `interface` Może dziedziczyć z wielu interfejsach podstawowych, a `class` lub `struct` może zaimplementować wiele interfejsów.

A `delegate` typ reprezentuje odwołania do metod z określoną listą parametrów i typ zwracany. Delegatów można umożliwić traktować metod jako jednostki, które mogą być przypisane do zmiennych i przekazywane jako parametry. Obiekty delegowane są analogiczne do typów funkcji dostarczonych przez języków funkcjonalnych. Są one również podobne do koncepcji wskaźników funkcji, w przeciwieństwie do innych języków, ale w przeciwieństwie do wskaźników funkcji, obiekty delegowane są zorientowane obiektowo i bezpieczny typowo.

`class`, `struct`, `interface` i `delegate` typy wszystkie elementy rodzajowe pomocy technicznej, według których mogą być parametryzowane przy użyciu innych typów.

`enum` Typ jest typem samodzielnym z nazwanych stałych. Każdy `enum` typ ma typu podstawowego musi być jednym z ośmiu typów całkowitych. Zestaw wartości `enum` typ jest taki sam zestaw wartości typu podstawowego.

C# obsługuje dimensional jednym i wielu tablic dowolnego typu. W przeciwieństwie do typów wymienionych powyżej typy tablic ma zadeklarowany, zanim będzie można ich użyć. Zamiast tego typy tablicowe są konstruowane wykonując nazwę typu z nawiasami kwadratowymi. Na przykład `int[]` to Jednowymiarowa tablica `int`, `int[,]` to dwuwymiarowa tablica `int`, i `int[][]` jest tablicą jednowymiarową tablicę jednowymiarową `int`.

Typy o wartości zerowalnej również ma być zadeklarowany, zanim będzie można ich użyć. Dla każdego typu wartości niedopuszczającym wartości `T` istnieje odpowiedni typ wartości zerowalnej `T?`, który może zawierać dodatkowe wartości `null`. Na przykład `int?` jest typem, który może pomieścić dowolna liczba całkowita 32-bitowych lub wartość `null`.

C#w systemie typów jest jednolita w taki sposób, że wartość dowolnego typu może być traktowana jako `object`. Każdy typ w języku C#, bezpośrednio lub pośrednio pochodzi z `object` typ, klasy i `object` jest ultimate klasą bazową wszystkich typów. Wartości typu referencyjnego są traktowane jako obiekty poprzez wyświetlanie wartości jako typu `object`. Wartości typu wartości są traktowane jako obiekty, wykonując *pakowania* i *Rozpakowywanie operacje*. W poniższym przykładzie `int` wartość jest konwertowana na `object` i wykonać ich kopię ponownie do `int`.

[!code-csharp[Boxing](../../../samples/snippets/csharp/tour/types-and-variables/Program.cs#L1-L10)]

Gdy wartość typu wartości jest konwertowany na typ `object`, `object` wystąpienia, nazywany również "pola", jest przeznaczona do przechowywania wartości, a wartość jest kopiowana do tego pola. Z drugiej strony, gdy `object` odwołania jest rzutowany na typ wartości, dokonuje, występujących w odwołaniu `object` jest polem typu poprawnej wartości, i, jeśli sprawdzenie zakończy się powodzeniem, wartość w polu jest kopiowana.

C#jego unified typu systemu oznacza, że typy wartości może stać się obiekty "na żądanie." Ze względu na ujednolicenie ogólnego przeznaczenia biblioteki, które używają typu `object` mogą być używane z typami odwołań i typy wartości.

Istnieje kilka rodzajów z *zmienne* w języku C#, w tym pól, elementy tablicy, zmienne lokalne i parametry. Zmienne reprezentują lokalizacje przechowywania, a co zmienna ma typ, który określa, jakie wartości mogą być przechowywane w zmiennej, jak pokazano poniżej.

* Typ wartości nieprzyjmujące
  - Wartość tego typu dokładnie
* Typ wartości null
  - A `null` wartość lub wartość tego typu dokładnie
* object
  - A `null` odwołanie, odwołanie do obiektu typu odwołania lub odwołania do wartości spakowanej dowolnego typu wartości
* Typ klasy
  - A `null` odwołanie, odwołanie do wystąpienia tego typu klasy lub odwołanie do wystąpienia klasy pochodzącej od typu klasy
* Typ interfejsu
  - A `null` odwołanie, odwołanie do wystąpienia typu klasy, która implementuje interfejs typu lub odwołanie do wartości spakowanej typu wartości, która implementuje interfejs typu
* Typ tablicy
  - A `null` odwołanie, odwołanie do wystąpienia tego typu tablicy lub odwołanie do wystąpienia typu tablicy zgodne
* Typ delegata
  - A `null` odwołanie lub odwołanie do wystąpienia typu delegowanego zgodne

> [!div class="step-by-step"]
> [Poprzednie](program-structure.md)
> [dalej](expressions.md)

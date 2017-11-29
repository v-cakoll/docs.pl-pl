---
title: "C# i zmiennymi — samouczek języka C#"
description: "Więcej informacji na temat definiowania typów i deklarowania zmiennych w języku C#"
keywords: ".NET, csharp, typ, typ, wartość typu odwołania"
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: f8a8051e-0049-43f1-b594-9c84cc7b1224
ms.openlocfilehash: 1f1031384520b9ed37246361da8bbc1b42addb0b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="types-and-variables"></a>Typy i zmienne

Istnieją dwa rodzaje typów w języku C#: *typów wartości* i *typy referencyjne*. Zmienne typów wartości zawierają swoje dane bezpośrednio, natomiast zmienne typów referencyjnych przechowywania odwołań do swoich danych, w drugim znaną jako obiekty. Z typami odwołania jest możliwość dwie zmienne odwołać się do tego samego obiektu i w związku z tym możliwe w dla operacji na jedną zmienną, która wpływa na obiekt odwołuje się innej zmiennej. W przypadku typów wartości zmiennych każdego mają własne kopii danych i nie jest możliwe w dla operacji na jednym wpłynąć na innych (z wyjątkiem w odniesieniu `ref` i `out` zmiennych parametrów).

C# dla typów wartości są podzielone na *typów prostych*, *Typy wyliczeniowe*, *typy struktur*, i *typy o wartości zerowalnej*. C# dla typów odwołań są podzielone na *klas typów*, *typy interfejsów*, *typy tablicowe*, i *typów delegatów*.

Poniżej omówiono C# dla typu systemu.

* Typy wartości
    - Typy proste
        * Podpisana typu całkowitego: `sbyte`, `short`, `int`,`long`
        * Typy całkowite bez znaku: `byte`, `ushort`, `uint`,`ulong`
        * Znaki Unicode:`char`
        * Liczba zmiennoprzecinkowa IEEE: `float`,`double`
        * Decimal wysokiej precyzji:`decimal`
        * Wartość logiczna:`bool`
    - Typy wyliczeniowe
        * Typy danych zdefiniowane przez użytkownika w postaci`enum E {...}`
    - Typy struktur
        * Typy danych zdefiniowane przez użytkownika w postaci`struct S {...}`
    - typy dopuszczające wartości zerowe wartości
        * Rozszerzenia innych typów wartości za pomocą `null` wartości
* Typy odwołań
    - Typy klas
        * Klasa podstawowa Ultimate innych typów:`object`
        * Ciągów Unicode:`string`
        * Typy danych zdefiniowane przez użytkownika w postaci`class C {...}`
    - Typy interfejsów
        * Typy danych zdefiniowane przez użytkownika w postaci`interface I {...}`
    - Typy tablic
        * Jedno - i są one wielowymiarowe, na przykład `int[]` i`int[,]`
    - Typy delegatów
        * Typy danych zdefiniowane przez użytkownika w postaci`delegate int D(...)`

Typy całkowite osiem zapewniają obsługę 8-bitową, 16-bitowych, 32-bitowe i 64-bitowej wartości formularza podpisem lub bez.

Dwa typy zmiennoprzecinkowe, `float` i `double`, są reprezentowane w 32-bitowych pojedynczej precyzji i 64-bitowe o podwójnej dokładności IEC 60559 formatów, odpowiednio.

`decimal` Typ jest typem danych 128-bitowego odpowiedni do obliczeń finansowych i finansowe.

C# w `bool` typ jest używany do reprezentowania wartości logicznych — wartości, które są `true` lub `false`.

Znak, a ciąg przetwarzania w języku C# używa kodowanie Unicode. `char` Typu reprezentuje jednostkę kodu UTF-16 i `string` typu reprezentuje sekwencję jednostek kodu UTF-16.

To podsumowanie typy liczbowe C# firmy.

* Typy całkowite podpisem
    - `sbyte`: 8 bitów, z zakresu od -128 do 127.
    - `short`: 16 bitów, z zakresu od-32 768-32 767 znaków
    - `int`: 32-bitowy, zakresu od -2,147,483,648-2 147 483 647
    - `long`: 64-bitowy, w zakresie od –9,223,372,036,854,775,808 do 9,223,372,036,854,775,807
* Typy całkowite bez znaku
    - `byte`: 8 bitów należeć do zakresu od 0 – 255
    - `ushort`: 16 bitów należeć do zakresu od 0 - 65 535
    - `uint`: 32-bitowy, należeć do zakresu od 0 - 4 294 967 295
    - `ulong`: 64-bitowy, należeć do zakresu od 0 - 18,446,744,073,709,551,615
* Liczba zmiennoprzecinkowa
    - `float`: 32-bitowy, należeć do zakresu od 1,5 x 10<sup>−45</sup> -3,4 x 10<sup>38</sup>, 7-cyfrowy dokładności
    - `double`: 64-bitowy, należeć do zakresu od 5.0 x 10<sup>−324</sup> -1.7 x 10<sup>308</sup>, dokładności 15 cyfr
* Wartość dziesiętna
    - `decimal`: 128 bitów, zakres jest co najmniej –7.9 x 10<sup>−28</sup> -7,9 x 10<sup>28</sup>, o co najmniej 28 cyfr precyzji
    
C# Użyj programy *wpisz deklaracje* do tworzenia nowych typów. Deklaracja typu Określa nazwę i elementów członkowskich nowego typu. Pięć kategorii C# dla typów są definiowane przez użytkownika: klasa typy, typy struktur, typów interfejsów, Typy wyliczeniowe i typów delegatów.

A `class` typ definiuje struktury danych, który zawiera elementy członkowskie danych (pola) i funkcja członków (metody, właściwości i inne). Typy klas obsługuje pojedyncze dziedziczenie i polimorfizm, mechanizmów zgodnie z którymi klas pochodnych można rozszerzać i której specialize klas podstawowych.

A `struct` typu jest podobny do typu klasy reprezentuje struktury z elementów członkowskich danych i funkcji elementów członkowskich. W przeciwieństwie do klasy, struktury są typy wartości i nie wymagają zazwyczaj Alokacja sterty. Typy struktur nie obsługują określone przez użytkownika dziedziczenia, a wszystkie typy struktur niejawnie dziedziczyć z typu `object`.

`interface` Typ definiuje kontrakt jako nazwany zestaw funkcji publicznych elementów członkowskich. A `class` lub `struct` implementującej `interface` muszą zawierać implementacje interfejsu funkcji członków. `interface` Może dziedziczyć po wielu interfejsach podstawowych, a `class` lub `struct` mogą zaimplementować wiele interfejsów.

A `delegate` typu reprezentuje odwołania do metod z określonego parametru listy i typ zwracany. Obiekty delegowane umożliwiają traktować jako jednostek, które można przypisywać do zmiennych i przekazywane jako parametry metody. Obiekty delegowane są odpowiednikiem typy funkcji dostarczonych przez funkcjonalności języków. Są one również podobny do koncepcji znaleziono w przypadku niektórych języków innych wskaźników funkcji, ale w przeciwieństwie do wskaźników funkcji delegatów są zorientowane obiektowo i bezpieczne.

`class`, `struct`, `interface` i `delegate` typy wszystkie ogólne pomocy technicznej, zgodnie z którymi mogą nadać parametry z innych typów.

`enum` Typ jest typem distinct z stałe nazwane. Każdy `enum` typ ma odpowiedni typ, który musi być jedną z ośmiu typów całkowitych. Zbiór wartości `enum` typ jest taki sam, jak zestaw wartości typu bazowego.

C# obsługuje dimensional jednym i wielu tablice dowolnego typu. W przeciwieństwie do typów wymienionych powyżej typy tablic nie trzeba być zadeklarowana przed ich użyciem. Zamiast tego typy tablic są wykonane przez następujące Nazwa typu w nawiasy kwadratowe. Na przykład `int[]` jest tablicy jednowymiarowej z `int`, `int[,]` jest tablicą dwuwymiarową z `int`, i `int[][]` jest tablicy jednowymiarowej tablicy jednowymiarowej `int`.

Typy dopuszczające wartości zerowe wartości również nie trzeba być zadeklarowana przed ich użyciem. Dla każdego typu wartość niezerowalna `T` istnieje odpowiedni typ wartości null `T?`, która zawiera dodatkowe wartości `null`. Na przykład `int?` jest typem, który może posiadać żadnych 32-bitową liczbą całkowitą lub wartość `null`.

System typów C# w jest unified w taki sposób, że wartość dowolnego typu może być traktowana jako `object`. Każdy typ w języku C#, bezpośrednio lub pośrednio pochodzi z `object` typ, klasy i `object` jest klasą bazową ultimate wszystkich typów. Wartości typu odwołania są traktowane jako obiekty po prostu, wyświetlając wartości jako typ `object`. Wartości typów wartości są traktowane jako obiekty, wykonując *boxing* i *rozpakowującej operacji*. W poniższym przykładzie `int` wartość jest konwertowana na `object` i ponownie utworzyć kopię `int`.

[!code-csharp[Boxing](../../../samples/snippets/csharp/tour/types-and-variables/Program.cs#L1-L10)]

Jeśli wartość typu wartości jest konwertowana na typ `object`, `object` wystąpienia, nazywane również "pola", jest przeznaczona do przechowywania wartości, a wartość jest kopiowana do tego pola. Z drugiej strony, gdy `object` odwołania jest Rzutowanie na typ wartości, dokonuje który przywoływana `object` jest polem typu poprawną wartość i, jeśli sprawdzenie zakończy się powodzeniem, wartość w polu jest kopiowana.

System typów ujednoliconego C# w oznacza, że typów wartości może stać się obiekty "na żądanie." Z powodu ujednolicenie, bibliotek ogólnego przeznaczenia, które używają typu `object` można używać z typów wartości i typy referencyjne.

Istnieje kilka typów z *zmienne* w języku C#, w tym pól, elementy tablicy, zmienne lokalne i parametry. Zmienne reprezentują lokalizacje magazynu, a co zmienna ma typ, który określa, jakie wartości mogą być przechowywane w zmiennej, jak pokazano poniżej.

* Typ wartości niedopuszczająca wartości null
    - Wartość tego dokładnego typu
* Typ wartości null
    - A `null` lub wartości dokładnego typu
* object
    - A `null` odwołania, odwołanie do obiektu dowolnego typu odwołanie lub odwołanie do wartości spakowanej dowolnego typu wartości
* Typ klasy
    - A `null` odwołania, odwołania do wystąpienia tego typu klasy lub odwołanie do wystąpienia klasy pochodnej z tego typu klasy
* Typ interfejsu
    - A `null` odwołania, odwołania do wystąpienia typu klasy, która implementuje interfejs typu lub odwołanie do wartości spakowanej typu wartości, który implementuje interfejs typu
* Typ tablicy
    - A `null` odwołania, odwołania do wystąpienia tego typu tablicy lub odwołania do wystąpienia typu tablicy zgodne
* Typ delegata
    - A `null` odwołanie lub odwołanie do wystąpienia typu delegata zgodne

>[!div class="step-by-step"]
[Poprzednie](program-structure.md)
[dalej](expressions.md)

---
title: C# struktur — Przewodnik po przykładzie w języku C#
description: Dowiedz się, że podstawy języka C# wartości typów nazywanych struktury
ms.date: 08/10/2016
ms.assetid: 88a74571-f741-4a31-a2b5-1ccf165535b8
ms.openlocfilehash: d22cb23fe095874f24d7c002dfdb3eefdde66722
ms.sourcegitcommit: d9a0071d0fd490ae006c816f78a563b9946e269a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "55065963"
---
# <a name="structs"></a>Struktury

Takie jak klasy, ***struktury*** są struktur danych, które mogą zawierać elementy członkowskie danych i składowe funkcji, ale w przeciwieństwie do klasy, struktury są typami wartości i nie wymagają alokacji sterty. Zmienną typu struktury bezpośrednio przechowuje dane struktury, natomiast zmienna typu klasa przechowuje odwołania do obiektu przydzielanego dynamicznie. Typy struktury nie obsługują dziedziczenia określonych przez użytkownika, a wszystkie typy struktury niejawnie dziedziczą z typu <xref:System.ValueType>, który z kolei niejawnie dziedziczy `object`.

Struktury są szczególnie przydatne w przypadku małych strukturach danych, które mają semantyki wartości. Liczby zespolone, punkty w układzie współrzędnych lub par klucz wartość ze słownika są dobrym przykładem struktury. Używanie struktur, zamiast klasy w małych strukturach danych ułatwia duża różnica w liczbie alokacji pamięci aplikacji wykonuje. Na przykład następujący program tworzy i inicjuje tablicę 100 punktów. Za pomocą `Point` implementowany jako klasa, 101 oddzielne obiekty są tworzone — jeden dla macierzy i jeden dla 100 elementów.

[!code-csharp[PointClassUse](../../../samples/snippets/csharp/tour/structs/Program.cs#L5-L13)]

Alternatywą jest punkt struktury.

[!code-csharp[PointStruct](../../../samples/snippets/csharp/tour/structs/Point.cs#L3-L11)]

Teraz, zostanie uruchomiony tylko jeden obiekt — jeden dla tablicy — i `Point` wystąpienia są przechowywane w tekście w tablicy.

Struct — Konstruktorzy są wywoływane przy użyciu `new` operatora, podobne do konstruktora klasy. Jednak zamiast dynamicznej alokacji obiektu w zarządzanym stosie i zwraca odwołanie do niej, Konstruktor struktury po prostu zwraca wartość struct (zwykle znajduje się w lokalizacji tymczasowej na stosie), a ta wartość jest następnie kopiowana gdy jest to konieczne.

W przypadku klas jest możliwe dwóch zmiennych odwoływać się do tego samego obiektu dla operacji na jednej zmiennej miały wpływ na obiekt odwołuje się druga zmienna zatem możliwe. Przy użyciu struktury zmienne każda ma własne kopię danych, a nie jest możliwe dla operacji na jednym wpływa na drugi. Na przykład dane wyjściowe generowane przez następujący fragment kodu zależy od tego, czy punkt znajduje się w klasie lub strukturze.

[!code-csharp[PointUse](../../../samples/snippets/csharp/tour/structs/Program.cs#L19-L22)]

Jeśli `Point` jest klasą, dane wyjściowe to 20, ponieważ `a` i `b` odwoływać się do tego samego obiektu. Jeśli `Point` jest strukturą, dane wyjściowe to 10, ponieważ przypisanie `a` do `b` tworzona jest kopia wartości, i nie ma wpływu następne przypisanie do tej kopii `a.x`.

W poprzednim przykładzie wyróżniono dwa ograniczenia dotyczące struktury. Po pierwsze całej strukturze jest to zazwyczaj mniej wydajne niż kopiowanie odwołanie do obiektu, dzięki czemu przekazywanie przypisania i wartość parametru może być bardziej kosztowne przy użyciu struktury niż w przypadku typów referencyjnych. Drugi, z wyjątkiem `in`, `ref`, i `out` parametrów, nie jest możliwe do utworzenia odwołania do struktury, która wyklucza ich użycia w różnych sytuacjach.

>[!div class="step-by-step"]
>[Poprzednie](classes-and-objects.md)
>[dalej](arrays.md)

---
title: "C# struktury — samouczek języka C#"
description: "Dowiedz się, że typy, o nazwie struktury wartości podstawy języka C#"
keywords: "Typ wartości .NET, C#, struktury,"
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 88a74571-f741-4a31-a2b5-1ccf165535b8
ms.openlocfilehash: 9d435fd87a6103d505c14219499eeea9aee045fb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="structs"></a>Struktury

Takich jak klasy, ***struktury*** są struktur danych, które mogą zawierać elementów członkowskich danych i członkowie funkcji, ale w przeciwieństwie do klasy, struktury są typy wartości i nie wymagają alokacji sterty. Zmienna typu struct bezpośrednio przechowuje dane struktury, natomiast zmienna typu klasy przechowuje odwołanie do dynamicznie przydzielonego obiektu. Typy struktur nie obsługują określone przez użytkownika dziedziczenia, a wszystkie typy struktur niejawnie dziedziczyć z typu <xref:System.ValueType>, który z kolei niejawnie dziedziczy `object`.

Struktury są szczególnie przydatne w strukturach niewielkie zbiory danych, które ma wartość semantyki. Liczby złożone, punkty w układzie współrzędnych lub pary klucz wartość ze słownika są dobrym przykładem struktury. Używanie struktur, zamiast klasy dla struktury danych w małych ułatwia duża różnica w liczbie alokacji pamięci aplikacji wykonuje. Na przykład następujący program tworzy i inicjuje tablicę 100 punktów. Z `Point` wystąpienia zaimplementowane jako klasa, 101 oddzielnych obiektów — jeden dla tablicy i jeden dla każdej 100 elementów.

[!code-csharp[PointClassUse](../../../samples/snippets/csharp/tour/structs/Program.cs#L5-L13)]

Alternatywą jest zapewnienie punktu struktury.

[!code-csharp[PointStruct](../../../samples/snippets/csharp/tour/structs/Point.cs#L3-L11)]

Teraz, zostanie uruchomiony tylko jeden obiekt — jeden dla tablicy — i `Point` wystąpienia są przechowywane w wierszu w tablicy.

Struct — Konstruktorzy są wywoływane z operatora new, ale który nie oznacza, że pamięć jest przydzielane. Zamiast dynamiczne przydzielanie obiektu i zwraca odwołanie do niej konstruktora struktury po prostu zwraca wartość — Struktura (zwykle w tymczasowej lokalizacji na stosie), a ta wartość jest następnie skopiowana niezbędne.

W przypadku klas jest możliwe dwie zmienne odwołać się do tego samego obiektu i w związku z tym możliwe w dla operacji na jedną zmienną, która wpływa na obiekt odwołuje się innej zmiennej. Ze struktury zmienne każdego mają własne kopię danych, a nie jest możliwe w dla operacji na jednym wpłynąć na innych. Na przykład dane wyjściowe, generowane przez następujący fragment kodu zależy od tego, czy punkt znajduje się w klasie lub strukturze.

[!code-csharp[PointUse](../../../samples/snippets/csharp/tour/structs/Program.cs#L19-L22)]

Jeśli `Point` jest klasą, dane wyjściowe wynosi 20, ponieważ i b odwołuje się do tego samego obiektu. Jeśli punkt jest strukturą, dane wyjściowe to 10, ponieważ przypisanie `a` do `b` tworzy kopię wartości, i nie mają wpływu kolejne przypisanie do tej kopii `a.x`.

Poprzedni przykład przedstawia dwa ograniczenia struktury. Po pierwsze skopiowanie całej struktury jest zazwyczaj są mniej wydajne niż kopiowanie odwołania do obiektu, więc przekazywanie przypisania i wartość parametru może być droższe z struktury niż z typów referencyjnych. Drugi, z wyjątkiem `ref` i `out` parametrów nie jest możliwe do tworzenia odwołań do struktury, która wyklucza ich użycia w różnych sytuacjach.

>[!div class="step-by-step"]
[Poprzednie](classes-and-objects.md)
[dalej](arrays.md)

---
title: "C# tablice — samouczek języka C#"
description: "Tablice są najbardziej podstawowa typ kolekcji w języku C#"
keywords: ".NET, csharp, tablicę, kolekcji"
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: a440704c-9e88-4c75-97dd-bfe30ca0fb97
ms.openlocfilehash: d7d5ae9f99ba1629a6f0aec57bebf74853cab27f
ms.sourcegitcommit: a19548e5167cbe7e9e58df4ffd8c3b23f17d5c7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2017
---
# <a name="arrays"></a>Tablice

***Tablicy*** jest strukturą danych, która zawiera szereg zmiennych, które są udostępniane przez obliczoną indeksów. Zmienne zawartych w tablicy, nazywany również ***elementy*** tablicy, znajdują się tego samego typu, a tego typu jest nazywana ***typ elementu*** tablicy.

Typy tablicy są typy referencyjne i deklaracja zmiennej tablicy po prostu rezerwuje miejsca dla odwołania do wystąpienia tablicy. Wystąpienia bieżącej tablicy są tworzone dynamicznie w czasie wykonywania za pomocą operatora new. Określa nową operację ***długość*** nowego wystąpienia tablicy, która jest następnie u okresu istnienia wystąpienia. Indeksów elementów zakresu tablicy z `0` do `Length - 1`. `new` Operator automatycznie inicjuje elementy tablicy można przywrócić wartości domyślne, czyli, na przykład zero dla wszystkich typów numerycznych i `null` dla wszystkich typów odniesienia.

Poniższy przykład tworzy tablicę `int` elementów inicjuje tablicy, a następnie do drukowania zawartości tablicy.

[!code-csharp[ArraySample](../../../samples/snippets/csharp/tour/arrays/Program.cs#L3-L18)]

W tym przykładzie tworzy i działa na ***tablicy jednowymiarowej***. C# obsługuje również ***tablic wielowymiarowych***. Wpisz liczbę wymiarów tablicy, znanej także jako ***rangę*** typu tablicy jest jeden oraz liczbę przecinkami zapisywane między nawiasami kwadratowymi typu tablicy. Poniższy przykład przydziela odpowiednio jednowymiarowe dwuwymiarowa i jest tablicą trójwymiarową.

[!code-csharp[ArrayRank](../../../samples/snippets/csharp/tour/arrays/Program.cs#L24-L26)]

`a1` Tablica zawiera 10 elementów `a2` tablica zawiera 50 (10 x 5) elementów i `a3` 100 (10 x 5 x 2) zawiera tablicę elementów.
Typ elementu tablicy mogą być dowolnego typu, łącznie z typem tablicy. Tablica elementami typu tablicy jest czasami nazywany ***tablicy nieregularnej*** ponieważ długości tablic elementu nie wszystkie muszą być takie same. Poniższy przykład przydziela tablicy tablic `int`:

[!code-csharp[ArrayAllocation](../../../samples/snippets/csharp/tour/arrays/Program.cs#L31-L34)]

Pierwszy wiersz tworzy tablicę z trzech elementów, dla każdego typu `int[]` i każde z nich wartość początkową `null`. Kolejne wiersze zainicjować następnie trzy elementy o odwołań do tablicy pojedynczych wystąpień różne długości.

New operator zezwala na wartości początkowe elementy tablicy można określić za pomocą ***inicjatora tablicy***, który znajduje się lista wyrażeń zapisywane między ograniczniki `{` i `}`. W poniższym przykładzie przydziela i inicjuje `int[]` z trzech elementów.

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L39-L39)]

Należy pamiętać, że długość tablicy jest wywnioskowany na podstawie liczba wyrażeń między {i}. Zmienna lokalna i deklaracje pól można skrócony dalsze tak, aby typ tablicy nie ma zostać przekształcone.

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L44-L44)]

Poprzednich przykładach są równoważne z następujących czynności:

[!code-csharp[ArrayAssignment](../../../samples/snippets/csharp/tour/arrays/Program.cs#L49-L53)]

>[!div class="step-by-step"]
[Poprzednie](structs.md)
[dalej](interfaces.md)

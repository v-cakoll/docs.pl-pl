---
title: C#Tablice — Przewodnik po przykładzie C# języka
description: Tablice są najbardziej podstawowym typem kolekcji w C# języka
ms.date: 08/10/2016
ms.assetid: a440704c-9e88-4c75-97dd-bfe30ca0fb97
ms.openlocfilehash: 8685e6ad08eb74534cdad499099b3d12da0a497a
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53153309"
---
# <a name="arrays"></a>Tablice

***Tablicy*** to struktura danych, która zawiera szereg zmiennych, które są dostępne za pośrednictwem obliczanej indeksów. Zmienne zawartych w tablicy, jest określana skrótem ***elementy*** tablicy, są wszystkie tego samego typu, a tego typu jest nazywana ***typ elementu*** tablicy.

Typy tablicowe są typami odwołań, a deklaracja zmiennej tablicy po prostu rezerwuje miejsce dla odwołania do wystąpienia tablicy. Wystąpienia bieżącej tablicy są tworzone dynamicznie w czasie wykonywania za pomocą nowego operatora. Określa nową operację ***długość*** nowego wystąpienia tablicy naprawiliśmy dla okresu istnienia wystąpienia. Indeksy elementów z zakresu tablicy `0` do `Length - 1`. `new` Operator automatycznie inicjuje elementy tablicy, aby przywrócić wartości domyślne, na przykład są to wartości zero dla wszystkich typów liczbowych i `null` dla wszystkich typów odniesienia.

Poniższy przykład tworzy tablicę `int` elementów, inicjuje tablicy i wyświetla zawartość tablicy.

[!code-csharp[ArraySample](../../../samples/snippets/csharp/tour/arrays/Program.cs#L3-L18)]

W tym przykładzie tworzy i działa na ***tablicy jednowymiarowej***. C# obsługuje również ***Wielowymiarowe tablice***. Wpisz liczbę wymiarów tablicy, znany także jako ***ranga*** typ tablicy jest jedną przesunięta liczbę przecinkami zapisywane między nawiasami kwadratowymi typu tablicy. Poniższy przykład przydziela odpowiednio jednowymiarowe dwuwymiarowym i tablicą trójwymiarową.

[!code-csharp[ArrayRank](../../../samples/snippets/csharp/tour/arrays/Program.cs#L24-L26)]

`a1` Tablica zawiera 10 elementów `a2` tablica zawiera 50 (10 x 5) elementów, a `a3` tablica zawiera 100 (10 x 5 x 2) elementów.
Typ elementu tablicy może być dowolnego typu, w tym typu tablicowego. Tablicę z elementami typu tablicowego jest czasami nazywane ***tablicy nieregularnej*** ponieważ długości tablic elementu nie wszystkie muszą być takie same. Poniższy przykład przydziela tablicy tablic `int`:

[!code-csharp[ArrayAllocation](../../../samples/snippets/csharp/tour/arrays/Program.cs#L31-L34)]

Pierwszy wiersz tworzy tablicę z trzech elementów, z których każdy typ `int[]` , a każdy z wartości początkowej `null`. Kolejne wiersze następnie zainicjowanie trzech elementów z odwołaniami do wystąpień poszczególnych tablicy o różnej długości.

Nowy operator zezwala na wartość początkową elementów tablicy, należy określić przy użyciu ***inicjatora tablicy***, który znajduje się lista wyrażeń zapisywane między ogranicznikami `{` i `}`. Poniższy przykład przydziela i inicjuje `int[]` za pomocą trzech elementów.

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L39-L39)]

Należy pamiętać, że długość tablicy jest wnioskowany z liczba wyrażeń między {i}. Zmienna lokalna i deklaracji pól można skrócony dalsze taki sposób, że typ tablicy nie ma być przekształcone.

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L44-L44)]

W poprzednich przykładach są odpowiednikiem następujących czynności:

[!code-csharp[ArrayAssignment](../../../samples/snippets/csharp/tour/arrays/Program.cs#L49-L53)]

>[!div class="step-by-step"]
>[Poprzednie](structs.md)
>[dalej](interfaces.md)
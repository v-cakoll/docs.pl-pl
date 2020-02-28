---
title: C#Tablice — Przewodnik po C# języku
description: Tablice są najbardziej podstawowym typem kolekcji w C# języku
ms.date: 08/10/2016
ms.assetid: a440704c-9e88-4c75-97dd-bfe30ca0fb97
ms.openlocfilehash: 195df1f31c71ee7a202a3b57076775c4f717d399
ms.sourcegitcommit: c2d9718996402993cf31541f11e95531bc68bad0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/27/2020
ms.locfileid: "77673319"
---
# <a name="arrays"></a>Tablice

***Tablica*** to struktura danych zawierająca wiele zmiennych, do których można uzyskać dostęp za pomocą obliczanych indeksów. Zmienne zawarte w tablicy, nazywane również ***elementami*** tablicy, są tego samego typu, a ten typ jest nazywany ***typem elementu*** tablicy.

Typy tablic są typami odwołań, a deklaracja zmiennej tablicowej po prostu ustawia miejsce na odwołanie do wystąpienia tablicy. Rzeczywiste wystąpienia tablicy są tworzone dynamicznie w czasie wykonywania przy użyciu operatora new. Nowa operacja określa ***Długość*** nowego wystąpienia tablicy, które jest następnie naprawione dla okresu istnienia wystąpienia. Indeksy elementów z zakresu tablicy od `0` do `Length - 1`. Operator `new` automatycznie inicjuje elementy tablicy do ich wartości domyślnej, co na przykład ma wartość zero dla wszystkich typów liczbowych i `null` dla wszystkich typów referencyjnych.

Poniższy przykład tworzy tablicę elementów `int`, Inicjuje tablicę i drukuje zawartość tablicy.

[!code-csharp[ArraySample](../../../samples/snippets/csharp/tour/arrays/Program.cs#L3-L18)]

Ten przykład tworzy i działa na ***tablicy jednowymiarowej***. C#obsługuje również ***tablice***wielowymiarowe. Liczba wymiarów typu tablicy, znana również jako ***ranga*** typu tablicy, jest taka, a liczba przecinkiów zapisywana między nawiasami kwadratowymi typu tablicy. Poniższy przykład przydziela odpowiednio jednowymiarowe, dwuwymiarowe i trójwymiarowe tablice.

[!code-csharp[ArrayRank](../../../samples/snippets/csharp/tour/arrays/Program.cs#L24-L26)]

Tablica `a1` zawiera 10 elementów, tablica `a2` zawiera 50 (10 × 5) elementów, a tablica `a3` zawiera 100 (10 × 5 × 2) elementów.
Typ elementu tablicy może być dowolnego typu, łącznie z typem tablicy. Tablica z elementami typu tablicy jest czasami nazywana ***tablicą nieregularną*** , ponieważ długości tablic elementów nie wszystkie muszą być takie same. W poniższym przykładzie przypisuje tablicę tablic `int`:

[!code-csharp[ArrayAllocation](../../../samples/snippets/csharp/tour/arrays/Program.cs#L31-L34)]

Pierwszy wiersz tworzy tablicę z trzema elementami, każdy z typów `int[]` i każdy z początkową wartością `null`. Kolejne wiersze inicjują następnie trzy elementy z odwołaniami do poszczególnych wystąpień tablicy o różnej długości.

Operator new pozwala na określenie początkowych wartości elementów tablicy przy użyciu ***inicjatora tablicy***, który jest listą wyrażeń pisanych między ogranicznikami `{` i `}`. Poniższy przykład przydziela i inicjuje `int[]` z trzema elementami.

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L39-L39)]

Należy zauważyć, że długość tablicy jest wywnioskowana na podstawie liczby wyrażeń między {i}. Deklaracje zmiennej lokalnej i pola mogą być skrócone w taki sposób, aby nie trzeba było przestawiać tego typu tablicy.

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L44-L44)]

Oba poprzednie przykłady są równoważne z następującymi:

[!code-csharp[ArrayAssignment](../../../samples/snippets/csharp/tour/arrays/Program.cs#L49-L53)]

>[!div class="step-by-step"]
>[Poprzednie](classes-and-objects.md)
>[dalej](interfaces.md)

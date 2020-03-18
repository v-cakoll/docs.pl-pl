---
title: Tablice języka C# — przewodnik po języku Języka C#
description: Tablice są najbardziej podstawowym typem kolekcji w języku C#
ms.date: 02/27/2020
ms.assetid: a440704c-9e88-4c75-97dd-bfe30ca0fb97
ms.openlocfilehash: 3e045c0933a21beab6958c7851546ba6e0b55ef9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78159198"
---
# <a name="arrays"></a>Tablice

***Tablica*** jest strukturą danych, która zawiera szereg zmiennych, które są dostępne za pośrednictwem indeksów obliczeniowych. Zmienne zawarte w tablicy, nazywane również ***elementy*** tablicy, są tego samego typu, a ten typ jest nazywany ***typem elementu*** tablicy.

Typy tablic są typami odwołań, a deklaracja zmiennej tablicowej po prostu odkłada miejsce na odwołanie do wystąpienia tablicy. Rzeczywiste wystąpienia tablicy są tworzone dynamicznie w czasie wykonywania przy użyciu nowego operatora. Nowa operacja określa ***długość*** nowego wystąpienia tablicy, która jest następnie ustalona dla okresu istnienia wystąpienia. Indeksy elementów tablicy wahają się `0` od `Length - 1`do . Operator `new` automatycznie inicjuje elementy tablicy do ich wartości domyślnej, która na przykład wynosi `null` zero dla wszystkich typów liczbowych i dla wszystkich typów odwołań.

Poniższy przykład tworzy tablicę `int` elementów, inicjuje tablicy i drukuje zawartość tablicy.

[!code-csharp[ArraySample](../../../samples/snippets/csharp/tour/arrays/Program.cs#L3-L18)]

W tym przykładzie tworzy i działa na ***tablicy jednowymiarowej***. C# obsługuje również ***tablice wielowymiarowe***. Liczba wymiarów typu tablicy, znany również jako ***rangi*** typu tablicy, jest jeden plus liczba przecinków zapisanych między nawiasami kwadratowymi typu tablicy. Poniższy przykład przydziela jednowymiarową, dwuwymiarową i trójwymiarową tablicę.

[!code-csharp[ArrayRank](../../../samples/snippets/csharp/tour/arrays/Program.cs#L24-L26)]

Tablica `a1` zawiera 10 `a2` elementów, tablica zawiera 50 (10 `a3` × 5) elementów, a tablica zawiera 100 (10 × 5 × 2) elementów.
Typ elementu tablicy może być dowolny typ, w tym typ tablicy. Tablica z elementami typu tablicy jest czasami ***nazywana tablicą postrzępioną,*** ponieważ długości tablic elementów nie muszą być takie same. W poniższym przykładzie przydziela tablicę `int`tablic:

[!code-csharp[ArrayAllocation](../../../samples/snippets/csharp/tour/arrays/Program.cs#L31-L34)]

Pierwszy wiersz tworzy tablicę z trzema `int[]` elementami, każdy typu `null`i każdy z wartością początkową . Kolejne wiersze następnie zainicjować trzy elementy z odwołaniami do poszczególnych wystąpień tablicy o różnej długości.

Nowy operator zezwala na początkowe wartości elementów tablicy, które mają być określone za pomocą ***inicjatora tablicy***, który jest listą wyrażeń napisanych między ogranicznikami `{` i `}`. Poniższy przykład przydziela i inicjuje z `int[]` trzech elementów.

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L39-L39)]

Długość tablicy jest wywnioskowana z liczby wyrażeń między { i }. Deklaracje zmiennych lokalnych i pól można dodatkowo skrócić w taki sposób, aby typ tablicy nie musiał być ponownie przekształcany.

[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L44-L44)]

Oba poprzednie przykłady są równoważne z następującym kodem:

[!code-csharp[ArrayAssignment](../../../samples/snippets/csharp/tour/arrays/Program.cs#L49-L53)]

>[!div class="step-by-step"]
>[Poprzedni](classes-and-objects.md)
>[następny](interfaces.md)

---
title: Drzewa wyrażeń
description: Dowiedz się więcej o drzewach wyrażeń w .NET Core i jak ich używać do reprezentowania kodu jako struktur, które można zbadać, zmodyfikować i wykonać.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: aceb4719-0d5a-4b19-b01f-b51063bcc54f
ms.openlocfilehash: e1026ef70860da519b688a9d67181b88d03f6f0b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79145842"
---
# <a name="expression-trees"></a>Drzewa wyrażeń

Jeśli używasz LINQ, masz doświadczenie z bogatą `Func` biblioteką, w której typy są częścią zestawu interfejsu API. (Jeśli nie jesteś zaznajomiony z LINQ, prawdopodobnie chcesz przeczytać [samouczek LINQ](linq/index.md) i artykuł o [wyrażeniach lambda](./programming-guide/statements-expressions-operators/lambda-expressions.md) przed tym.) *Drzewa wyrażeń* zapewniają bogatszą interakcję z argumentami, które są funkcjami.

Argumenty funkcji, zazwyczaj przy użyciu wyrażenia Lambda, podczas tworzenia kwerend LINQ. W typowej kwerendy LINQ te argumenty funkcji są przekształcane w pełnomocnika tworzy kompilator.

Jeśli chcesz mieć bogatszą interakcję, musisz użyć *drzew wyrażeń*.
Drzewa wyrażeń reprezentują kod jako strukturę, którą można sprawdzić, zmodyfikować lub wykonać. Narzędzia te dają możliwość manipulowania kodem w czasie wykonywania. Można napisać kod, który sprawdza uruchomione algorytmy lub wstrzykuje nowe możliwości. W bardziej zaawansowanych scenariuszach można modyfikować uruchomione algorytmy, a nawet tłumaczyć wyrażenia C# na inny formularz do wykonania w innym środowisku.

Prawdopodobnie już napisałkod, który używa drzewa wyrażeń. Interfejsy API LINQ struktury jednostek akceptują drzewa wyrażeń jako argumenty dla wzorca wyrażeń kwerendy LINQ.
Dzięki temu [entity framework](/ef/) przetłumaczyć kwerendę, którą napisałeś w języku C# na SQL, która jest wykonywana w aparatie bazy danych. Innym przykładem jest [Moq](https://github.com/Moq/moq), który jest popularnym mocking framework dla .NET.

Pozostałe sekcje tego samouczka będzie badać, jakie drzewa wyrażeń są, zbadać klasy struktury, które obsługują drzewa wyrażeń i pokazać, jak pracować z drzewa wyrażeń. Dowiesz się, jak czytać drzewa wyrażeń, jak tworzyć drzewa wyrażeń, jak tworzyć drzewa wyrażeń zmodyfikowanych i jak wykonać kod reprezentowany przez drzewa wyrażeń. Po przeczytaniu będzie gotowy do użycia tych struktur do tworzenia bogatych algorytmów adaptacyjnych.

1. [Drzewa wyrażeń — objaśnienie](expression-trees-explained.md)

    Zrozumienie struktury i pojęć za *drzewa wyrazu*.

2. [Typy platform obsługujące drzewa wyrażeń](expression-classes.md)

    Dowiedz się więcej o strukturach i klasach, które definiują drzewa wyrażeń i manipulują nimi.

3. [Wykonywanie wyrażeń](expression-trees-execution.md)

    Dowiedz się, jak przekonwertować drzewo wyrażeń reprezentowane jako wyrażenie Lambda do delegata i wykonać wynikowy delegata.

4. [Interpretowanie wyrażeń](expression-trees-interpreting.md)

    Dowiedz się, jak przechodzić i sprawdzać *drzewa wyrażeń,* aby zrozumieć, jaki kod reprezentuje drzewo wyrażeń.

5. [Tworzenie wyrażeń](expression-trees-building.md)

    Dowiedz się, jak skonstruować węzły drzewa wyrażeń i drzewa wyrażeń kompilacji.

6. [Translacja wyrażeń](expression-trees-translating.md)

    Dowiedz się, jak utworzyć zmodyfikowaną kopię drzewa wyrażeń lub przetłumaczyć drzewo wyrażeń na inny format.

7. [Podsumowanie](expression-trees-summary.md)

    Przejrzyj informacje o drzewach wyrażeń.

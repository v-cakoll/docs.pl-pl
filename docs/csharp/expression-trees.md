---
title: Drzewa wyrażeń
description: Informacje o drzewach wyrażeń w oprogramowaniu .NET Core i sposobach ich użycia do reprezentowania kodu jako struktur, które można sprawdzić, zmodyfikować i wykonać.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: aceb4719-0d5a-4b19-b01f-b51063bcc54f
ms.openlocfilehash: b7d039ea4585953473dc88cebcc516ea240cdc3a
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73036320"
---
# <a name="expression-trees"></a>Drzewa wyrażeń

Jeśli używasz LINQ, masz doświadczenie w korzystaniu z rozbudowanej biblioteki, w której typy `Func` są częścią zestawu interfejsów API. (Jeśli nie znasz programu LINQ, prawdopodobnie chcesz przeczytać [samouczek LINQ](linq/index.md) i artykuł dotyczący [wyrażeń lambda](./programming-guide/statements-expressions-operators/lambda-expressions.md) przed tym.) *Drzewa wyrażeń* zapewniają bogatsze interakcje z argumentami, które są funkcjami.

Podczas tworzenia zapytań LINQ można pisać argumenty funkcji, zwykle wykorzystując wyrażenia lambda. W typowej kwerendzie LINQ te argumenty funkcji są przekształcane na delegata tworzonego przez kompilator. 

Jeśli chcesz mieć bogatsze interakcje, musisz używać *drzew wyrażeń*.
Drzewa wyrażeń reprezentują kod jako strukturę, którą można testować, modyfikować lub wykonywać. Te narzędzia umożliwiają manipulowanie kodem w czasie wykonywania. Można napisać kod, który analizuje uruchomione algorytmy, lub wprowadza nowe możliwości. W bardziej zaawansowanych scenariuszach można modyfikować uruchomione algorytmy, a nawet przetłumaczyć C# wyrażenia na inny formularz do wykonania w innym środowisku.

Już właśnie Zapisano kod, który używa drzew wyrażeń. Interfejsy API LINQ Entity Framework akceptują drzewa wyrażeń jako argumenty wzorca wyrażenia zapytania LINQ.
Dzięki temu [Entity Framework](/ef/) tłumaczenie zapytania, które zostało napisane w C# języku SQL, który jest wykonywany w aparacie bazy danych. Innym przykładem jest [MOQ](https://github.com/Moq/moq), który jest popularną strukturą dla platformy .NET.

Pozostałe sekcje w tym samouczku zapoznają się z drzewami wyrażeń, sprawdzają klasy struktury obsługujące drzewa wyrażeń i pokazują, jak korzystać z drzew wyrażeń. Dowiesz się, jak czytać drzewa wyrażeń, jak tworzyć drzewa wyrażeń, jak tworzyć zmodyfikowane drzewa wyrażeń i jak wykonywać kod reprezentowany przez drzewa wyrażeń. Po przeczytaniu będzie można używać tych struktur do tworzenia rozbudowanych algorytmów adaptacyjnych.

1. [Drzewa wyrażeń — objaśnienie](expression-trees-explained.md)

    Zapoznaj się ze strukturą i pojęciami związanymi z *drzewami wyrażeń*.
    
2. [Typy platform obsługujące drzewa wyrażeń](expression-classes.md)
    
    Dowiedz się więcej o strukturach i klasach, które definiują drzewa wyrażeń i manipulowania nimi.
    
3. [Wykonywanie wyrażeń](expression-trees-execution.md)

    Dowiedz się, jak przekonwertować drzewo wyrażenia reprezentowane jako wyrażenie lambda na delegata i wykonać delegata będącego wynikiem.

4. [Interpretowanie wyrażeń](expression-trees-interpreting.md)

    Dowiedz się, jak przechodzenie i sprawdzanie *drzew wyrażeń* , aby zrozumieć, jaki kod jest reprezentowany przez drzewo wyrażeń.

5. [Tworzenie wyrażeń](expression-trees-building.md)

    Dowiedz się, jak utworzyć węzły dla drzewa wyrażenia i drzewa wyrażeń kompilacji.

6. [Translacja wyrażeń](expression-trees-translating.md)

    Dowiedz się, jak utworzyć zmodyfikowaną kopię drzewa wyrażenia lub przetłumaczyć drzewo wyrażenia na inny format.

7. [Sumowanie](expression-trees-summary.md)

    Zapoznaj się z informacjami w drzewach wyrażeń.

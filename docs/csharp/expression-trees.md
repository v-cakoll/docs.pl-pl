---
title: Drzewa wyrażeń
description: Więcej informacji na temat drzew wyrażeń w .NET Core i sposób ich użycia, aby reprezentować kodu struktury, które można zbadać, modyfikowania i wykonać.
ms.date: 06/20/2016
ms.assetid: aceb4719-0d5a-4b19-b01f-b51063bcc54f
ms.openlocfilehash: db35dd99dadc4e49aaaebd5d3782409a206cafc5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="expression-trees"></a>Drzewa wyrażeń

Użycie LINQ masz doświadczenie z biblioteką sformatowanego gdzie `Func` typy są częścią zestawu interfejsów API. (Jeśli nie znasz za pomocą LINQ, prawdopodobnie chcesz odczytać [samouczek LINQ](linq/index.md) i samouczek dotyczący [wyrażenia lambda](lambda-expressions.md) przed tego.) *Drzewa wyrażeń* Podaj bogatszą interakcję z argumentami, które są funkcje.

Pisania argumenty funkcji, zwykle za pomocą wyrażenia Lambda, podczas tworzenia zapytań LINQ. W typowych zapytań LINQ te argumenty funkcji są przekształcane w delegata, który tworzy kompilatora. 

Jeśli chcesz mieć bogatszą interakcję, należy użyć *drzew wyrażeń*.
Drzewa wyrażeń reprezentują kodu struktury można zbadać, zmodyfikować lub wykonać. Te narzędzia umożliwiają uprawnienia do modyfikowania kodu w czasie wykonywania. Można napisać kod, który sprawdza, czy uruchomione algorytmów lub injects nowe funkcje. W bardziej zaawansowanych scenariuszy można zmodyfikować systemem algorytmów i nawet tłumaczenia wyrażeń C# do innego formularza do wykonania w innym środowisku.

Prawdopodobnie zostały już zapisane kodu korzystającego z drzewa wyrażeń. Interfejsy API programu Entity Framework LINQ zaakceptować drzew wyrażeń jako argumenty wzorzec wyrażenia zapytań LINQ.
Umożliwiającej [Entity Framework](http://docs.efproject.net/en/latest/) tłumaczenie zapytania napisane w języku C# SQL, która wykonuje aparatu bazy danych. Innym przykładem jest [Moq](https://github.com/Moq/moq), która jest popularnych framework mocking dla platformy .NET.

Pozostałe sekcje w tym samouczku zostanie Eksploruj są drzewa wyrażeń, zbadać klasy framework, które obsługują drzew wyrażeń i opisano sposób pracy z drzewa wyrażeń. Dowiesz się, jak przeczytać drzew wyrażeń, sposób tworzenia drzewa wyrażeń sposobu tworzenia drzewa wyrażeń zmodyfikowane i jak wykonać kod reprezentowany przez drzewa wyrażeń. Po zapoznaniu się z, będzie gotowa do użycia tych struktur można tworzyć rozbudowane algorytmy adaptacyjną.

1. [Drzewa wyrażeń — objaśnienie](expression-trees-explained.md)

    Zrozumienie struktury i pojęć dotyczących *drzew wyrażeń*.
    
2. [Typy platform obsługujące drzewa wyrażeń](expression-classes.md)
    
    Więcej informacji na temat struktury i klasy, które Zdefiniuj i manipulowania drzewa wyrażeń.
    
3. [Wykonywanie wyrażeń](expression-trees-execution.md)

    Dowiedz się, jak można skonwertować na drzewo wyrażenia reprezentowane jako wyrażenie Lambda do delegata i wykonaj wynikowy delegata.

4. [Interpretowanie wyrażeń](expression-trees-interpreting.md)

    Dowiedz się, jak przechodzić między nimi i sprawdź, czy *drzew wyrażeń* zrozumienie kodu drzewa wyrażenia reprezentuje.

5. [Tworzenie wyrażeń](expression-trees-building.md)

    Dowiedz się, jak utworzyć węzły drzewa wyrażeń i tworzenia drzewa wyrażeń.

6. [Translacja wyrażeń](expression-trees-translating.md)

    Dowiedz się, jak kompilacji kopię zmodyfikowane drzewo wyrażenia lub tłumaczenie drzewo wyrażenia w innym formacie.

7. [Podsumowanie](expression-trees-summary.md)

    Przejrzyj informacje na temat drzewa wyrażeń.
    

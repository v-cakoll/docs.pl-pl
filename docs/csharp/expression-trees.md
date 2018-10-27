---
title: Drzewa wyrażeń
description: Więcej informacji na temat drzew wyrażeń w .NET Core i jak z nich korzystać, aby reprezentować struktur, które można zbadać, modyfikowania i wykonywanie kodu.
ms.date: 06/20/2016
ms.assetid: aceb4719-0d5a-4b19-b01f-b51063bcc54f
ms.openlocfilehash: 56509f1eb0f2bdca8a8f3a51df958d42e95af6f4
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50190739"
---
# <a name="expression-trees"></a>Drzewa wyrażeń

Jeśli używano LINQ, gdy potrafisz dzięki rozbudowanej bibliotece gdzie `Func` typy są częścią zestawu interfejsów API. (Jeśli nie jesteś zaznajomiony z LINQ, prawdopodobnie chcesz odczytać [samouczek LINQ](linq/index.md) i samouczek dotyczący [wyrażeń lambda](lambda-expressions.md) przed to.) *Drzewa wyrażeń* zapewniają bardziej rozbudowane interakcji z argumentów, które są funkcjami.

Można napisać argumentów funkcji, zazwyczaj przy użyciu wyrażeń Lambda, podczas tworzenia zapytania LINQ. W typowych zapytań LINQ te argumenty funkcji są przekształcane do delegata, który kompilator tworzy. 

Umożliwia bogatszych interakcję, należy użyć *drzew wyrażeń*.
Drzewa wyrażeń reprezentują kodu struktury, można przejrzeć, zmodyfikować lub wykonywania. Te narzędzia umożliwiają do manipulowania kodu w czasie wykonywania. Można napisać kod, który sprawdza, czy uruchamianie algorytmów lub wprowadza nowe funkcje. W bardziej zaawansowanych scenariuszy można modyfikować, uruchamianie algorytmów i nawet tłumaczenie C# wyrażeń do innej formy do wykonania w innym środowisku.

Kod, który używa drzew wyrażeń prawdopodobnie zostały już zapisane. Interfejsy API programu Entity Framework LINQ zaakceptować drzew wyrażeń jako argumenty do wzorca wyrażenia zapytań LINQ.
Który umożliwia [Entity Framework](/ef/) do translacji zapytania zapisane w C# SQL, który jest wykonywany w aparacie bazy danych. Innym przykładem jest [Moq](https://github.com/Moq/moq), czyli popularnego środowiska pozorowania dla platformy .NET.

Pozostałe sekcje w tym samouczku będzie zapoznaj się z drzewa wyrażeń są, sprawdź klasy framework, które obsługują drzew wyrażeń, a dowiesz się, jak pracować z drzewa wyrażeń. Dowiesz się, jak odczytać drzew wyrażeń, sposób tworzenia drzew wyrażeń, sposób tworzenia drzew wyrażeń zmodyfikowane i jak wykonywać kod reprezentowany przez drzew wyrażeń. Po czytania, wszystko będzie gotowe do użycia te struktury do tworzenia rozbudowanych adaptacyjnych algorytmów.

1. [Drzewa wyrażeń — objaśnienie](expression-trees-explained.md)

    Omówienie struktury i pojęcia dotyczące *drzew wyrażeń*.
    
2. [Typy platform obsługujące drzewa wyrażeń](expression-classes.md)
    
    Więcej informacji na temat struktur i klas definiujących i manipulowania drzew wyrażeń.
    
3. [Wykonywanie wyrażeń](expression-trees-execution.md)

    Dowiedz się, jak można przekonwertować na drzewo wyrażenia, w postaci wyrażenia Lambda do delegata, a następnie wykonaj wynikowego delegata.

4. [Interpretowanie wyrażeń](expression-trees-interpreting.md)

    Dowiedz się, jak przejść i zbadaj *drzew wyrażeń* Aby zrozumieć, co kod drzewa wyrażenie reprezentuje.

5. [Tworzenie wyrażeń](expression-trees-building.md)

    Dowiedz się, jak utworzyć węzłów do drzewa wyrażenie i tworzenia drzew wyrażeń.

6. [Translacja wyrażeń](expression-trees-translating.md)

    Dowiedz się, jak tworzyć zmodyfikowanej kopii drzewo wyrażenia lub drzewa wyrażenie przekłada się na inny format.

7. [Podsumowanie](expression-trees-summary.md)

    Zapoznaj się z informacjami w drzewach wyrażeń.
    

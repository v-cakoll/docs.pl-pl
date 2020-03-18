---
title: Drzewa wyrażeń — objaśnienie
description: Dowiedz się więcej o drzewach wyrażeń i jak są one przydatne w tłumaczeniu algorytmów do wykonywania zewnętrznego i inspekcji kodu przed jego wykonaniem.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: bbcdd339-86eb-4ae5-9911-4c214a39a92d
ms.openlocfilehash: 12093e9c9246c87cc5ea3aedaca6ba34acacce4d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "73036992"
---
# <a name="expression-trees-explained"></a>Drzewa wyrażeń — objaśnienie

[Poprzedni -- Przegląd](expression-trees.md)

Drzewo wyrażeń jest strukturą danych, która definiuje kod. Są one oparte na tych samych strukturach, które kompilator używa do analizowania kodu i generowania skompilowanych danych wyjściowych. Jak przeczytać ten samouczek, można zauważyć sporo podobieństwa między drzewa wyrażenia i typy używane w interfejsach API Roslyn do tworzenia [analizatorów i codefixes](https://github.com/dotnet/roslyn-analyzers).
(Analizatory i poprawki kodu są pakiety NuGet, które wykonują analizę statyczną na kod i może sugerować potencjalne poprawki dla dewelopera.) Pojęcia są podobne, a wynik końcowy jest struktura danych, która umożliwia badanie kodu źródłowego w znaczący sposób. Jednak drzewa wyrażeń są oparte na zupełnie inny zestaw klas i interfejsów API niż interfejsy API Roslyn.

Spójrzmy na prosty przykład.
Oto wiersz kodu:

```csharp
var sum = 1 + 2;
```

Jeśli było analizować to jako drzewo wyrażeń, drzewo zawiera kilka węzłów.
Węzeł najbardziej oddalony jest zmienną instrukcją`var sum = 1 + 2;`deklaracji z przypisaniem ( ) Ten najbardziej oddalony węzeł zawiera kilka węzłów podrzędnych: deklarację zmiennej, operator przypisania i wyrażenie reprezentujące prawą stronę znaku równości. To wyrażenie jest dalej podzielone na wyrażenia, które reprezentują operację dodawania i lewy i prawy argument dodawania.

Przejdźmy nieco bardziej do wyrażeń, które składają się na prawą stronę znaku równości.
Wyrażenie to `1 + 2`. To wyrażenie binarne. Dokładniej, jest to wyrażenie dodawania binarnego. Wyrażenie dodania binarnego ma dwa elementy podrzędne, reprezentujące lewe i prawe węzły wyrażenia dodawania. W tym miejscu oba węzły są wyrażeniami stałymi: Lewy operand jest wartością `1`, a prawym operandem jest wartość `2`.

Wizualnie cała instrukcja jest drzewem: można rozpocząć w węźle głównym i przejść do każdego węzła w drzewie, aby zobaczyć kod, który składa się na instrukcję:

- Instrukcja deklaracji zmiennej z przypisaniem (`var sum = 1 + 2;`)
  - Deklaracja typu`var sum`zmiennej niejawnej ( )
    - Niejawne`var`słowo kluczowe var ( )
    - Deklaracja nazwy`sum`zmiennej ( )
  - Operator przypisania (`=`)
  - Wyrażenie dodawania`1 + 2`binarnego ( )
    - Lewy operand`1`( )
    - Operator dodawania (`+`)
    - Prawy argument`2`( )

To może wyglądać skomplikowanie, ale jest bardzo potężny. Po tym samym procesie można rozłożyć znacznie bardziej skomplikowane wyrażenia. Należy wziąć pod uwagę to wyrażenie:

```csharp
var finalAnswer = this.SecretSauceFunction(
    currentState.createInterimResult(), currentState.createSecondValue(1, 2),
    decisionServer.considerFinalOptions("hello")) +
    MoreSecretSauce('A', DateTime.Now, true);
```

Wyrażenie powyżej jest również deklaracja zmiennej z przypisania.
W tym przypadku po prawej stronie przypisania jest znacznie bardziej skomplikowane drzewo.
Nie zamierzam się rozkładać tego wyrażenia, ale zastanów się, jakie mogą być różne węzły. Istnieją wywołania metody przy użyciu bieżącego obiektu jako `this` odbiornika, który ma odbiornik jawny, taki, który nie. Istnieją wywołania metody przy użyciu innych obiektów odbiornika, istnieją stałe argumenty różnych typów. I wreszcie, istnieje operator dodawania binarnego. W zależności od typu `SecretSauceFunction()` `MoreSecretSauce()`zwracanego lub , że operator dodawania binarnego może być wywołanie metody do operatora zastępowanego dodawania, rozpoznawanie do wywołania metody statycznej do operatora dodawania binarnego zdefiniowane dla klasy.

Pomimo tej postrzeganej złożoności, wyrażenie powyżej tworzy strukturę drzewa, które mogą być poruszane tak łatwo, jak w pierwszej próbce. Można zachować przechodzenie przez węzły podrzędne, aby znaleźć węzły liścia w wyrażeniu. Węzły nadrzędne będą miały odwołania do ich podrzędnych, a każdy węzeł ma właściwość, która opisuje, jaki rodzaj węzła jest.

Struktura drzewa wyrażeń jest bardzo spójna. Po nauczeniu się podstaw, można zrozumieć nawet najbardziej złożonykod, gdy jest reprezentowany jako drzewo wyrażeń. Elegancja w strukturze danych wyjaśnia, jak kompilator C# można analizować najbardziej złożonych programów C# i utworzyć odpowiednie dane wyjściowe z tego skomplikowanego kodu źródłowego.

Po zapoznaniu się ze strukturą drzew ekspresji, przekonasz się, że wiedza, którą szybko zdobędziesz, pozwala pracować z wieloma coraz bardziej zaawansowanymi scenariuszami. Istnieje niesamowita moc wyrażania drzew.

Oprócz tłumaczenia algorytmów do wykonania w innych środowiskach drzewa wyrażeń mogą służyć do ułatwienia pisania algorytmów, które sprawdzają kod przed jego wykonaniem. Można napisać metodę, której argumenty są wyrażeniami, a następnie zbadać te wyrażenia przed wykonaniem kodu. Drzewo wyrażeń jest pełną reprezentacją kodu: można zobaczyć wartości dowolnego wyrażenia podrzędnego.
Można wyświetlić nazwy metody i właściwości. Można zobaczyć wartość wszystkich wyrażeń stałych.
Można również przekonwertować drzewo wyrażeń na delegata wykonywalnego i wykonać kod.

Interfejsy API dla drzew wyrażeń umożliwiają tworzenie drzew, które reprezentują prawie wszystkie prawidłowe konstrukcji kodu. Jednak aby zachować rzeczy tak proste, jak to możliwe, niektóre idiomy C# nie można utworzyć w drzewie wyrażeń. Jednym z przykładów są wyrażenia asynchroniczne (przy użyciu `async` słów kluczowych). `await` Jeśli twoje potrzeby wymagają algorytmów asynchronicznych, należy `Task` manipulować obiektami bezpośrednio, a nie polegać na obsłudze kompilatora. Innym jest tworzenie pętli. Zazwyczaj można je utworzyć `for`za `foreach` `while` pomocą `do` , , lub pętle. Jak zobaczysz [w dalszej części tej serii](expression-trees-building.md), interfejsy API `break` `continue` dla drzew wyrażeń obsługują wyrażenie pojedynczej pętli, z i wyrażenia, które kontrolują powtarzanie pętli.

Jedyną rzeczą, której nie można zrobić, jest modyfikowanie drzewa wyrażeń.  Drzewa wyrażeń są niezmienne struktury danych. Aby zmutować (zmienić) drzewo wyrażeń, należy utworzyć nowe drzewo, które jest kopią oryginału, ale z żądanymi zmianami.

[Dalej - Typy struktury obsługujące drzewa wyrażeń](expression-classes.md)

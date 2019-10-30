---
title: Drzewa wyrażeń — objaśnienie
description: Dowiedz się więcej o drzewach wyrażeń i sposobach ich użycia podczas tłumaczenia algorytmów wykonywania zewnętrznego i sprawdzania kodu przed jego wykonaniem.
ms.date: 06/20/2016
ms.technology: csharp-advanced-concepts
ms.assetid: bbcdd339-86eb-4ae5-9911-4c214a39a92d
ms.openlocfilehash: 12093e9c9246c87cc5ea3aedaca6ba34acacce4d
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73036992"
---
# <a name="expression-trees-explained"></a>Drzewa wyrażeń — objaśnienie

[Poprzedni — przegląd](expression-trees.md)

Drzewo wyrażenia jest strukturą danych, która definiuje kod. Są one oparte na tych samych strukturach, których kompilator używa do analizowania kodu i generowania skompilowanych danych wyjściowych. Po przeczytaniu tego samouczka zobaczysz dość znaczące różnice między drzewami wyrażeń a typami używanymi w interfejsach API Roslyn do budowania [analizatorów i CodeFixes](https://github.com/dotnet/roslyn-analyzers).
(Analizatory i CodeFixes są pakietami NuGet, które wykonują analizę statyczną w kodzie i mogą sugerować potencjalne poprawki dla deweloperów). Pojęcia są podobne, a wynik końcowy to struktura danych, która umożliwia badanie kodu źródłowego w zrozumiały sposób. Jednak drzewa wyrażeń opierają się na zupełnie innym zestawie klas i interfejsów API niż interfejsy API Roslyn.

Przyjrzyjmy się prostemu przykładowi.
Oto wiersz kodu:

```csharp
var sum = 1 + 2;
```

Jeśli przeanalizować ten element jako drzewo wyrażenia, drzewo zawiera kilka węzłów.
Najbardziej zewnętrznym węzłem jest instrukcja deklaracji zmiennej z przypisaniem (`var sum = 1 + 2;`), która jest najbardziej zewnętrznym węzłem zawierającym kilka węzłów podrzędnych: Deklaracja zmiennej, operator przypisania i wyrażenie reprezentujące prawą stronę znaku równości. To wyrażenie jest dalej podzielona na wyrażenia, które reprezentują operację dodawania, oraz lewy i prawy operand dodawania.

Przejdźmy do bardziej szczegółowych informacji w wyrażeniach, które składają się z prawej strony znaku równości.
Wyrażenie jest `1 + 2`. To jest wyrażenie binarne. Dokładniej mówiąc, jest to binarne wyrażenie dodawania. Wyrażenie dodawania binarnego ma dwa elementy podrzędne, reprezentujące lewe i prawe węzły wyrażenia dodawania. W tym miejscu oba węzły są wyrażeniami stałymi: Lewy argument operacji jest wartością `1`, a prawy operand jest wartością `2`.

Wizualnie cała instrukcja jest drzewem: można zacząć od węzła głównego i poruszać się do każdego węzła w drzewie, aby wyświetlić kod, który wykonuje instrukcję:

- Instrukcja deklaracji zmiennej z przypisaniem (`var sum = 1 + 2;`)
  - Niejawna deklaracja typu zmiennej (`var sum`)
    - Niejawne słowo kluczowe var (`var`)
    - Deklaracja nazwy zmiennej (`sum`)
  - Operator przypisania (`=`)
  - Wyrażenie dodawania binarnego (`1 + 2`)
    - Lewy operand (`1`)
    - Operator dodawania (`+`)
    - Prawy operand (`2`)

Może to wyglądać skomplikowanie, ale jest bardzo wydajne. Wykonując ten sam proces, można rozłożyć znacznie bardziej skomplikowane wyrażenia. Rozważ następujące wyrażenie:

```csharp
var finalAnswer = this.SecretSauceFunction(
    currentState.createInterimResult(), currentState.createSecondValue(1, 2),
    decisionServer.considerFinalOptions("hello")) +
    MoreSecretSauce('A', DateTime.Now, true);
```

Wyrażenie powyżej jest również deklaracją zmiennej z przypisaniem.
W tym przypadku prawa strona przypisania jest znacznie bardziej skomplikowanym drzewem.
Nie mierzę rozłożyć tego wyrażenia, ale warto rozważyć, jakie mogą być różne węzły. Istnieją wywołania metod używające bieżącego obiektu jako odbiornika, który ma jawny odbiornik `this`, taki, który nie jest. Istnieją wywołania metod używające innych obiektów odbiornika, a istnieją stałe argumenty różnych typów. Na koniec istnieje binarny operator dodawania. W zależności od typu zwracanego `SecretSauceFunction()` lub `MoreSecretSauce()`, ten operator dodawania binarnego może być wywołaniem metody do zastąpionego operatora dodawania, rozpoznawania na wywołanie metody statycznej do operatora dodawania binarnego zdefiniowanego dla klasy.

Pomimo tej postrzeganej złożoności wyrażenie powyżej tworzy strukturę drzewa, którą można łatwo nawigować jako pierwszą próbkę. Aby znaleźć węzły liścia w wyrażeniu, można kontynuować przechodzenie między węzłami podrzędnymi. Węzły nadrzędne będą mieć odwołania do ich elementów podrzędnych, a każdy węzeł ma właściwość opisującą rodzaj węzła.

Struktura drzewa wyrażenia jest bardzo spójna. Po ustaleniu podstawowych informacji można zrozumieć nawet najbardziej skomplikowany kod, gdy jest reprezentowany jako drzewo wyrażenia. Elegancji w strukturze danych wyjaśnia, jak C# kompilator może analizować najbardziej złożone C# programy i tworzyć prawidłowe dane wyjściowe z tego złożonego kodu źródłowego.

Po zapoznaniu się ze strukturą drzew wyrażeń, zobaczysz, że uzyskana wiedza szybko umożliwia pracę z wieloma bardziej zaawansowanymi scenariuszami. Istnieją bardzo niesamowite możliwości dla drzew wyrażeń.

Oprócz tłumaczenia algorytmów do wykonania w innych środowiskach, drzewa wyrażeń mogą ułatwić pisanie algorytmów, które sprawdzają kod przed jego wykonaniem. Można napisać metodę, której argumenty są wyrażeniami, a następnie przeanalizować te wyrażenia przed wykonaniem kodu. Drzewo wyrażenia jest pełną reprezentacją kodu: można zobaczyć wartości dowolnego wyrażenia podrzędnego.
Można zobaczyć nazwy metod i właściwości. Możesz zobaczyć wartość dowolnych wyrażeń stałych.
Można również przekonwertować drzewo wyrażenia na delegata pliku wykonywalnego i wykonać kod.

Interfejsy API dla drzew wyrażeń umożliwiają tworzenie drzew, które reprezentują niemal dowolną prawidłową konstrukcję kodu. Aby jednak zapewnić jak najłatwą możliwość, niektóre C# idiomy nie mogą być tworzone w drzewie wyrażenia. Przykładem są wyrażenia asynchroniczne (przy użyciu `async` i `await` słów kluczowych). Jeśli Twoje potrzeby wymagają algorytmów asynchronicznych, trzeba będzie manipulować obiektami `Task` bezpośrednio, a nie polegać na obsłudze kompilatora. Innym jest w tworzeniu pętli. Zazwyczaj można je tworzyć przy użyciu pętli `for`, `foreach`, `while` lub `do`. Jak widać [w dalszej części tej serii](expression-trees-building.md), interfejsy API dla drzew wyrażeń obsługują pojedyncze wyrażenie pętli, z `break` i `continue` wyrażeń, które kontrolują powtarzanie pętli.

Jedną z tych czynności nie można modyfikować drzewo wyrażenia.  Drzewa wyrażeń są niezmiennymi strukturami danych. Jeśli chcesz zmodyfikować (zmienić) drzewo wyrażenia, musisz utworzyć nowe drzewo, które jest kopią oryginału, ale wraz z żądanymi zmianami.

[Typy "Next--Framework" obsługujące drzewa wyrażeń](expression-classes.md)

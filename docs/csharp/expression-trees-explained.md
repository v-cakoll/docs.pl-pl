---
title: Wyjaśniono drzew wyrażeń
description: Więcej informacji na temat drzew wyrażeń i jak są one przydatne w tłumaczenie algorytmów dla zewnętrznych wykonywania i kontroli kodu przed jej wykonanie.
ms.date: 06/20/2016
ms.assetid: bbcdd339-86eb-4ae5-9911-4c214a39a92d
ms.openlocfilehash: 97cba9e5ec388729d23fb2689dfc1842a42af9b6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33216872"
---
# <a name="expression-trees-explained"></a>Wyjaśniono drzew wyrażeń

[Poprzednie — omówienie](expression-trees.md)

Drzewo wyrażenia jest strukturą danych, który definiuje kodu. Są one oparte na tej samej struktury, używane do analizowania kodu i generowanie skompilowanych danych wyjściowych kompilatora. Omówione w tym samouczku, można zauważyć dość nieco podobieństwa między drzew wyrażeń i typy używane w interfejsach API Roslyn do budowania [analizatory i CodeFixes](https://github.com/dotnet/roslyn-analyzers).
(Analizatory i CodeFixes są pakiety NuGet, które wykonują analizy statycznej na kod i może sugerować potencjalne rozwiązania dla dewelopera). Pojęcia są podobne, a w rezultacie jest strukturą danych, umożliwiający kontroli kodu źródłowego w znaczący sposób. Jednak drzew wyrażeń są oparte na zbiór całkiem klasy i interfejsy API niż Roslyn interfejsów API.
    
Oto prosty przykład.
Oto wiersz kodu:
```csharp
var sum = 1 + 2;
```
Gdyby analizowanie to jako drzewo wyrażenia drzewa zawiera kilka węzłów.
Najbardziej zewnętrznego węzeł jest deklaracja zmiennej instrukcji za pomocą przypisania (`var sum = 1 + 2;`) tego węzła peryferyjnych zawiera kilka węzłów podrzędnych: deklaracja zmiennej, operatora przypisania i reprezentujący po prawej stronie znaku równości. Czy wyrażenie jest podzielona na wyrażeń, które reprezentują operacja dodawania i lewy i prawy argumentów operacji dodawania.

Umożliwia przechodzenie bardziej do wyrażeń, które składają się z prawej strony znaku równości.
Wyrażenie jest `1 + 2`. To wyrażenie binarne. W szczególności jest to wyrażenie binarne dodawania. Wyrażenie binarne dodanie ma dwa elementy podrzędne, reprezentujący lewy i prawy węzły wyrażenia dodawania. W tym miejscu oba węzły są wyrażenia stałe: lewy argument operacji jest wartość `1`, prawy operand jest to wartość `2`.

Efekty wizualne, całą instrukcję jest drzewo: można uruchomić w węźle głównym i przesyłane do każdego węzła w drzewie, aby wyświetlić kod, który stanowi instrukcji:

- Deklaracja zmiennej instrukcji za pomocą przypisania (`var sum = 1 + 2;`)
    * Deklaracja zmiennej typu niejawnego (`var sum`)
        - Niejawne var — słowo kluczowe (`var`)
        - Nazwa zmiennej deklaracji (`sum`)
    * Operator przypisania (`=`)
    * Wyrażenie binarne dodawania (`1 + 2`)
        - Lewej strony (`1`)
        - Operator dodawania (`+`)
        - Prawy argument operacji (`2`)

Może to wyglądać skomplikowane, ale jest bardzo zaawansowaną. Po tym samym procesie rozkładają się znacznie bardziej złożonych. Należy wziąć pod uwagę tego wyrażenia:
```csharp
var finalAnswer = this.SecretSauceFunction(
    currentState.createInterimResult(), currentState.createSecondValue(1, 2),
    decisionServer.considerFinalOptions("hello")) +
    MoreSecretSauce('A', DateTime.Now, true);
```

Powyższe wyrażenie jest również deklaracji zmiennej z przydziałem.
W tym wystąpieniu po prawej stronie przypisania jest znacznie bardziej skomplikowane drzewa.
Nie użyjemy dekompozycji to wyrażenie, ale należy wziąć pod uwagę, co może być w różnych węzłach. Brak przy użyciu bieżącego obiektu jako odbiornik, który ma jawnego wywołania metody `this` odbiornika, który nie obsługuje. Brak wywołania metody, przy użyciu innych obiektów odbiornik, stałych argumentów o różnych typach. A na koniec jest operator binarny dodawania. W zależności od typu zwracanego przez `SecretSauceFunction()` lub `MoreSecretSauce()`, że operator binarny dodawania może być wywołanie metody operator dodawania przesłonięte, rozpoznawania wywołanie metody statycznej operatora binarnego dodawania zdefiniowanej dla klasy.

Pomimo tego postrzegana złożoności powyższe wyrażenie tworzy strukturę drzewa, która może zostać przesłane bez pierwszej próbie. Można zachować przechodzenie węzłów podrzędnych można znaleźć w wyrażeniu węzłów liści. Węzły nadrzędne będzie zawierać odwołań do ich elementy podrzędne, a każdy węzeł ma właściwość, która opisuje rodzaj węzła jest.

Struktura drzewa wyrażenia jest bardzo spójna. Gdy znasz już podstawy, można zrozumieć nawet najbardziej złożoną kodu, kiedy jest reprezentowany jako drzewo wyrażenia. Przejrzysty wygląd w strukturze danych wyjaśniono, jak analizować najbardziej złożonych programów C# i utworzyć odpowiednie dane wyjściowe z tego kodu źródłowego skomplikowane kompilatora C#.

Po zapoznanie się ze struktury drzewa wyrażeń, zostanie ustalone, że wiedzy, które zostały uzyskane w szybko umożliwia pracę z wielu bardziej zaawansowanych scenariuszy. Brak wyjątkowo wydajnego na drzewa wyrażeń.

Oprócz tłumaczenia algorytmy do wykonania w innych środowiskach, drzew wyrażeń można ułatwić zapisu algorytmów inspekcji przed jego wykonaniem kodu. Można napisanie metody, którego argumenty wyrażenia, a następnie sprawdź te wyrażenia przed wykonaniem kodu. Drzewo wyrażenia jest reprezentację pełnego kodu: można zobaczyć wartości wszystkie wyrażenia podrzędnego.
Nazwy metod i właściwości jest widoczny. Można zobaczyć wartość wszystkie wyrażenia stałej.
Można również przekonwertować drzewo wyrażenia wykonywalnego delegata i wykonywania kodu.

Interfejsy API do drzewa wyrażeń umożliwiają tworzenie drzewa reprezentujących prawie konstrukcji prawidłowy kod. Jednak aby rzeczy, wystarczy, niektóre idioms C# nie można utworzyć drzewa wyrażenia. Przykładem jest asynchronicznego wyrażenia (przy użyciu `async` i `await` słowa kluczowe). Jeśli Twoje potrzeby wymagają asynchroniczne algorytmów, będzie potrzebny do manipulowania `Task` obiekty bezpośrednio, zamiast polegać na obsługa kompilatora. Inny jest utworzenie pętli. Zazwyczaj w celu utworzenia tych elementów przy użyciu `for`, `foreach`, `while` lub `do` pętli. Jak można zauważyć [dalej w tej serii](expression-trees-building.md), interfejsy API do drzewa wyrażeń obsługuje wyrażenia jednej pętli z `break` i `continue` wyrażeń sterujących powtarzające się pętli.

Jedyną operacją, której nie można wykonać, jest zmodyfikowanie drzewo wyrażenia.  Drzewa wyrażeń są niezmienne danych struktury. Jeśli chcesz zmodyfikować (Zmień) wyrażenie drzewa, należy utworzyć nowe drzewo będący kopię oryginału, ale odpowiednie zmiany. 

[Dalej--Framework typy obsługi drzewa wyrażeń](expression-classes.md)

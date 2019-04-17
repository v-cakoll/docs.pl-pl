---
title: Drzewa wyrażeń — objaśnienie
description: Informacje na temat drzew wyrażeń i jak są one przydatne do przekształcania algorytmy dla zewnętrznych wykonania i kontroli kodu przed jej wykonanie.
ms.date: 06/20/2016
ms.assetid: bbcdd339-86eb-4ae5-9911-4c214a39a92d
ms.openlocfilehash: 3bad826bb58ff361688d3e13497343661e7edbd3
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2019
ms.locfileid: "59613424"
---
# <a name="expression-trees-explained"></a>Drzewa wyrażeń — objaśnienie

[Poprzednie — omówienie](expression-trees.md)

Drzewo wyrażenia jest strukturą danych, który definiuje kodu. Są one oparte na tych samych struktur, które kompilator używa do analizowania kodu i generuje skompilowanych danych wyjściowych. Omówione w tym samouczku, można zauważyć znacznej liczby podobieństwa między drzew wyrażeń i typy używane w interfejsach API Roslyn do tworzenia [analizatory i CodeFixes](https://github.com/dotnet/roslyn-analyzers).
(Analizatory i CodeFixes są pakiety NuGet, przeprowadzania analizy statycznej kodu, które może sugerować potencjalne rozwiązania dla deweloperów). Podstawowe koncepcje są podobne, a wynik końcowy to struktura danych, która umożliwia zbadanie kodu źródłowego w znaczący sposób. Jednak drzew wyrażeń są oparte na zupełnie innego zestawu klas i interfejsów API niż interfejsów API Roslyn.

Oto prosty przykład.
Oto wiersz kodu:

```csharp
var sum = 1 + 2;
```

W przypadku analizowania to jako drzewa wyrażenie drzewa zawiera kilka węzłów.
Węzeł najbardziej zewnętrznej jest deklaracja zmiennej instrukcji z przypisaniem (`var sum = 1 + 2;`) tego węzła najbardziej zewnętrznej zawiera kilka węzłów podrzędnych: deklaracja zmiennej, operator przypisania i wyrażenie reprezentujące po prawej stronie znaku równości. Czy wyrażenie jest dalsze podzielone na wyrażeniach, które reprezentują operacja dodawania i lewy i prawy argumenty operacji dodawania.

Teraz nieco bardziej do szczegółów wyrażeń, które składają się po prawej stronie znaku równości.
Wyrażenie jest `1 + 2`. To wyrażenia binarnego. Dokładniej mówiąc jest to wyrażenie binarne dodawania. Wyrażenie binarne dodanie ma dwa elementy podrzędne, reprezentujący lewy i prawy węzłów wyrażenie dodawania. W tym miejscu oba węzły są stałe wyrażenia: Lewy operand jest wartością `1`, prawy operand jest to wartość `2`.

Wizualnie całą instrukcję jest drzewo: Możesz rozpoczynają się od węzła głównego i przesyłane do każdego węzła w drzewie Aby wyświetlić kod, który tworzy instrukcji:

- Deklaracja zmiennej instrukcji z przypisaniem (`var sum = 1 + 2;`)
  * Deklaracja niejawnego typu zmiennej (`var sum`)
    - Słowa kluczowego var niejawne (`var`)
    - Nazwa zmiennej deklaracji (`sum`)
  * Operator przypisania (`=`)
  * Wyrażenie binarne dodawania (`1 + 2`)
    - Lewy operand (`1`)
    - Operator dodawania (`+`)
    - Prawy operand (`2`)

Może to wyglądać skomplikowane, ale możliwości są ogromne. Następujące ten sam proces możesz rozłożyć części wyrażenia dużo bardziej skomplikowany. Należy wziąć pod uwagę następujące wyrażenie:

```csharp
var finalAnswer = this.SecretSauceFunction(
    currentState.createInterimResult(), currentState.createSecondValue(1, 2),
    decisionServer.considerFinalOptions("hello")) +
    MoreSecretSauce('A', DateTime.Now, true);
```

Powyższe wyrażenie jest również deklaracji zmiennej z przydziałem.
W tym wypadku po prawej stronie przypisania jest dużo bardziej skomplikowany drzewa.
Nie zamierzam rozłożyć to wyrażenie, ale należy wziąć pod uwagę, co może być w różnych węzłach. Brak wywołania metody, przy użyciu bieżącego obiektu jako odbiornik, który ma jawnie `this` odbiornik, który nie jest. Brak wywołania metody, przy użyciu innych obiektów odbiorcy, stałe argumentów o różnych typach. A na koniec jest operator binarny dodawania. W zależności od typu zwracanego `SecretSauceFunction()` lub `MoreSecretSauce()`, tego operatora binarnego dodawania może być wywołanie metody do operatora dodawania zgodnym z przesłoniętą rozpoznawania do wywołania metody statycznej operatora binarnego dodawania zdefiniowanej dla klasy.

Pomimo tego postrzegany złożoności powyższe wyrażenie tworzy strukturę drzewa, którego nastąpi przejście, jak łatwo, jak pierwszy przykład. Można zachować przechodzenie węzłów podrzędnych można znaleźć węzły liści w wyrażeniu. Węzły nadrzędne będzie odwołują się do ich elementy podrzędne, a każdy węzeł ma właściwość, która opisuje, w jaki rodzaj węzła jest.

Struktura drzewa wyrażenie jest bardzo spójne. Gdy znasz już podstawy, można zrozumieć nawet najbardziej złożonego kodu, gdy jest przedstawiana jako drzewo wyrażenia. Elegancji w strukturze danych wyjaśnia sposób, w jaki C# kompilatora można analizować najbardziej złożone C# programów i Utwórz odpowiednie dane wyjściowe z kodu źródłowego skomplikowane.

Gdy zapoznanie się ze struktury drzewa wyrażeń, możesz znaleźć, wiedzy, które zostały zgromadzone szybko umożliwia pracę z wielu bardziej zaawansowanych scenariuszy. Brak niwelujące w drzewach wyrażeń.

Oprócz tłumaczenia algorytmów do wykonania w innych środowiskach, drzew wyrażeń może służyć ułatwiające zapis algorytmy, które inspekcji kodu przed jego wykonaniem. Można napisać metodę, której argumenty są wyrażeniami i Sprawdź te wyrażenia przed wykonaniem kodu. Drzewo wyrażenia jest pełną reprezentację kod: możesz zobaczyć wartości dowolne wyrażenie podrzędne.
Możesz zobaczyć nazwy metod i właściwości. Wartość dowolnego wyrażenia stałe są widoczne.
Można także przekonwertować drzewo wyrażenia na delegata pliku wykonywalnego i wykonywania kodu.

Interfejsy API dla drzew wyrażeń umożliwiają tworzenie drzewa, które reprezentują prawie konstrukcji prawidłowy kod. Jednak aby zachować tak proste, jak to możliwe, niektóre C# idiomy nie można utworzyć w drzewo wyrażenia. Przykładem jest wyrażenia asynchroniczne (przy użyciu `async` i `await` słów kluczowych). Jeśli Twoje potrzeby wymagają algorytmy asynchroniczne, będziesz potrzebować do manipulowania `Task` obiektów bezpośrednio, zamiast polegać na temat obsługi kompilatora. Innym jest podczas tworzenia pętli. Zazwyczaj można tworzyć przy użyciu `for`, `foreach`, `while` lub `do` pętli. Jak zobaczysz [dalej w tej serii](expression-trees-building.md), interfejsy API dla drzew wyrażeń obsługuje wyrażenie jednej pętli z `break` i `continue` wyrażeń, które kontrolują, powtarzając pętli.

Jedyną operacją, której nie można wykonać, jest zmodyfikowanie drzewo wyrażenia.  Drzewa wyrażeń są danymi niezmiennymi struktury. Chcąc mutować (Zmień) wyrażenie drzewa, należy utworzyć nowe drzewo, który jest kopią oryginał, ale o odpowiednie zmiany.

[Dalej — Typy platform obsługujące drzewa wyrażeń](expression-classes.md)

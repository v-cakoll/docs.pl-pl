---
title: Historia języka C# — przewodnik C#
description: Języka jak wygląda w jego wersje i sposobu jego powstał od?
author: erikdietrich
ms.date: 09/20/2017
ms.openlocfilehash: 3e3bf98d1435b237b2941758b8ed245baa970237
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2018
ms.locfileid: "36207537"
---
# <a name="the-history-of-c"></a>Historia języka C# #

Języka jak wygląda w jego najwcześniejszą incarnations? I sposobu jego powstał w lat od?

## <a name="c-version-10"></a>C# w wersji 1.0

Gdy wrócić do poprzedniej strony i sprawdź, C# w wersji 1.0 zawierała znacznie przedstawione Java. Jako [część jej cele projektowania podane dla ECMA](http://feeldotneteasy.blogspot.com/2011/01/c-design-goals.html), miały być "prosty, Nowoczesny, ogólnego przeznaczenia zorientowany obiektowo język."  W tym czasie wyglądał Java, która miała ona osiągnąć te wczesne cele projektowania.

Ale jeśli możesz Wstecz w języku C# 1.0 teraz, czy okaże się nieco dizzy. Brakuje w niej możliwości wbudowanego async i niektóre funkcje slick wokół ogólne trwania dla przyznane. Jak rzeczy brakuje w niej ogólne całkowicie.  I [LINQ](../linq/index.md)? Nie są dostępne jeszcze. Te dodatki zajmie kilka lat do.

C# w wersji 1.0 wyszukiwanego pozbawionego włókien funkcji w porównaniu do dzisiaj. Czy okaże się, że pisanie kodu pełne. Ale jeszcze, trzeba uruchomić w innym miejscu. C# w wersji 1.0 został realną alternatywę języka Java na platformie systemu Windows.

Uwzględnione najważniejszych funkcji języka C# 1.0:

- [Klasy](../programming-guide/classes-and-structs/classes.md)
- [Struktury](../programming-guide/classes-and-structs/structs.md)
- [Interfejsy](../programming-guide/interfaces/index.md)
- [Zdarzenia](../events-overview.md)
- [Właściwości](../properties.md)
- [Delegaci](../delegates-overview.md)
- [Wyrażenia](../programming-guide/statements-expressions-operators/expressions.md)
- [Instrukcje](../programming-guide/statements-expressions-operators/statements.md)
- [Atrybuty](../programming-guide/concepts/attributes/index.md)
- Literały

## <a name="c-version-20"></a>C# w wersji 2.0

Teraz rozpocząć interesujący rzeczy. Spójrzmy na niektóre główne funkcje C# 2.0, wydane w 2005, wraz z programu Visual Studio 2005:

- [Typy ogólne](../programming-guide/generics/index.md)
- [Typy częściowe](../programming-guide/classes-and-structs/partial-classes-and-methods.md#partial-classes)
- [Metody anonimowe](../programming-guide/statements-expressions-operators/anonymous-methods.md)
- [Typy dopuszczające wartości zerowe](../programming-guide/nullable-types/index.md)
- [Iteratory](../programming-guide/concepts/iterators.md)
- [Kowariancja i kontrawariancja](../programming-guide/concepts/covariance-contravariance/index.md)

Inne funkcje 2.0 C# dodaje możliwości istniejących funkcji:

- Metody pobierającej/ustawiającej oddzielne ułatwień dostępu
- Konwersje grupy — metoda (obiekty delegowane)
- Klasy statyczne
- Wnioskowanie delegata

Gdy C# mogło uruchomić jako ogólnego język Object-Oriented (OO), C# w wersji 2.0 zmienić który w czasu. Gdy miały ich stopy w ich poszło po niektóre poważne developer słabe punkty. A ich zakończył po ich w znaczący sposób.

Ogólne typy i metody może działać dla dowolnego typu, przy jednoczesnym zachowaniu bezpieczeństwa typu. Na przykład, mając <xref:System.Collections.Generic.List%601> pozwala mieć `List<string>` lub `List<int>` i wykonywać operacje bezpieczne na tych ciągów lub liczb całkowitych, gdy iterację je. Użycie typów ogólnych jest lepsze niż utworzyć `ListInt` która pochodzi z `ArrayList` lub głosujących z `Object` dla każdej operacji.

C# w wersji 2.0 przełączony w tryb Iteratory. Aby umieścić krótkiej formie, Iteratory pozwalają sprawdzić wszystkie elementy w `List` (lub inne elementy typu Enumerable) z `foreach` pętli. O Iteratory w ramach pierwszej klasy języka znacznie rozszerzone czytelność język i osób umożliwia przeglądanie informacji o kod.

I jeszcze, C# nadal odtwarzany z bitowego wyrównywania z językiem Java. Java ma już zwolnione typy ogólne i Iteratory wersjach. Ale która zmieniłaby wkrótce jako języków nadal podlegać ewolucji od siebie.

## <a name="c-version-30"></a>C# w wersji 3.0

C# w wersji 3.0 pochodzi w późne 2007 oraz programu Visual Studio 2008, ale faktycznie przybyły pełne łodzi funkcji języka platformy .NET Framework w wersji 3.5. Ta wersja jest oznaczona jako istotne zmiany w rozwój języka C#. Stwierdzone C# jako naprawdę potężnych język programowania. Spójrzmy na niektóre główne funkcje w tej wersji:

- [Właściwości zaimplementowane automatycznie](../programming-guide/classes-and-structs/auto-implemented-properties.md)
- [Typy anonimowe](../programming-guide/classes-and-structs/anonymous-types.md)
- [Wyrażenia zapytań](../linq/query-expression-basics.md)
- [wyrażenia lambda](https://www.daedtech.com/introduction-to-c-lambda-expressions/)
- [Drzewa wyrażeń](https://blogs.msdn.microsoft.com/charlie/2008/01/31/expression-tree-basics/)
- [Metody rozszerzenia](https://www.codeproject.com/Tips/709310/Extension-Method-In-Csharp)
- [Niejawnie wpisane zmienne lokalne](../language-reference/keywords/var.md)
- [Metody częściowe](../language-reference/keywords/partial-method.md)
- Inicjatory obiektów i kolekcji

W retrospect wiele z tych funkcji prawdopodobnie zarówno nieuniknione i nierozdzielne. Wszystkie dopasowania strategicznie. Ogólnie należy uważać, że funkcja killer C# wersji była wyrażenia zapytania, nazywane również zapytania język Language-Integrated (LINQ).

Wyświetl więcej nuanced sprawdza drzewa wyrażeń, wyrażenia lambda i typy anonimowe jako podstawa, na którym jest tworzony LINQ. Jednak w obu przypadkach C# 3.0 przedstawione Rewolucyjny koncepcji. C# 3.0 zaczęło przygotowawczych służący do włączania C# do funkcjonalności / zorientowany obiektowo język hybrydowego.

W szczególności można teraz zapisać SQL stylu, deklaratywne zapytania do wykonywania operacji w kolekcjach, między innymi. Zamiast zapisywania `for` pętli do obliczenia średniej listy liczb całkowitych, możesz teraz to zrobić tylko jako `list.Average()`. Kombinacja wyrażenia zapytania i metody rozszerzenia wprowadzone wygląda tak, jakby listę liczb całkowitych ma się coraz wiele inteligentny.

Zajęło czasu dla osób naprawdę niejasny i integrowanie pojęcia, ale jak stopniowo. I teraz lata później, kod jest bardziej zwięzły, proste i funkcjonalności.

## <a name="c-version-40"></a>C# w wersji 4.0

C# w wersji 4.0 było trudne czas życia przełomowe stanu wersji 3.0 lub nowszej. W wersji 3.0 C# przeniósł język mocno limit w tle, Java i dostępność. Język został szybko stać się elegancki.

Następnej wersji wprowadzić niektóre ciekawe nowe funkcje:

- [Wiązania dynamicznego](../language-reference/keywords/dynamic.md)
- [Argumenty nazwane opcjonalne](../programming-guide/classes-and-structs/named-and-optional-arguments.md)
- [Rodzajowa kowariantnego i kontrawariantnego](../../standard/generics/covariance-and-contravariance.md)
- [Osadzone typy międzyoperacyjne](https://stackoverflow.com/questions/20514240/whats-the-difference-setting-embed-interop-types-true-and-false-in-visual-studi)

Osadzone typy międzyoperacyjne złagodzone słabe wdrożenia. Ogólny Kowariancja i kontrawariancja zapewniają więcej możliwości używaj danych generycznych wszędzie, ale są one nieco academic i prawdopodobnie najbardziej docenia przez autorów struktury i biblioteki. Parametry nazwane i opcjonalne pozwalają wyeliminować wiele przeciążenia metody i zapewnienia wygody. Ale żaden z tych funkcji są dokładnie modelu zmiany.

Funkcja głównych była wprowadzenie `dynamic` — słowo kluczowe. `dynamic` — Słowo kluczowe wprowadzono w języku C# w wersji 4.0 możliwość zastępowania kompilatora na wpisanie kompilacji. Za pomocą dynamiczne słowo kluczowe, można utworzyć konstrukcje podobne do językach takich jak JavaScript. Można utworzyć `dynamic x = "a string"` , a następnie dodaj sześć, pozostawiając środowiska uruchomieniowego do sortowania się, co powinno się zdarzyć, obok.

Wiązania dynamicznego umożliwia ryzyko błędów, ale również bardzo zasilania w języku.

## <a name="c-version-50"></a>C# w wersji 5.0

C# w wersji 5.0 został ukierunkowanych wersji języka. Prawie wszystkie działania dla tej wersji znajduje się w innym pojęcia języka przełomowe: `async` i `await` modelu programowania asynchronicznego.  Poniżej przedstawiono listę najważniejszych funkcji:

- [Elementy członkowskie asynchroniczne](../async.md)
- [Caller — atrybuty informacji](https://www.codeproject.com/Tips/606379/Caller-Info-Attributes-in-Csharp)

Obiekt wywołujący atrybutu informacji pozwala łatwo pobierać informacje o kontekście, w którym pracujesz bez konieczności ogromne schematyczny kod odbicia. Ma on wiele zastosowań diagnostyki i zadań rejestrowania.

Ale `async` i `await` są prawdziwe gwiazdek w tej wersji. Gdy te funkcje pochodzi w 2012, C# zmienione gry ponownie przez pieczenia asynchrony język jako najwyższej jakości uczestnika. Jeśli kiedykolwiek zostały omówione długotrwałe operacje, jak i implementację sieciach wywołań zwrotnych, prawdopodobnie loved ta funkcja językowa.

## <a name="c-version-60"></a>C# w wersji 6.0

W wersjach 3.0 i 5.0 C# były dodawane główne nowe funkcje w zorientowany obiektowo język. W wersji 6.0 czy go przed wykonaniem dominującą funkcji killer i zamiast tego wydania wiele funkcji mniejszych, wprowadzone programowania w języku C# bardziej wydajnej pracy. Oto niektóre z nich:

- [Importy statyczne](../language-reference/keywords/using-static.md)
- [Filtry wyjątków](https://www.thomaslevesque.com/2015/06/21/exception-filters-in-c-6/)
- [Inicjatory właściwości](http://geekswithblogs.net/WinAZ/archive/2015/06/30/whatrsquos-new-in-c-6.0-auto-property-initializers.aspx)
- [Wyrażenie zabudowanych elementy członkowskie](https://lostechies.com/jimmybogard/2015/12/17/c-6-feature-review-expression-bodied-function-members/)
- [Propagator wartości null](https://davefancher.com/2014/08/14/c-6-0-null-propagation-operator/)
- [Interpolacja ciągów](../language-reference/tokens/interpolated.md)
- [operatorze nameof](https://stackoverflow.com/questions/31695900/what-is-the-purpose-of-nameof)
- [Inicjatory indeksu](csharp-6.md#index-initializers)

Inne nowe funkcje:

- Await w blokach catch/finally
- Domyślne wartości dla właściwości tylko do metody pobierającej

Każda z tych funkcji jest ciekawe w sobie. Jednak ich całkowicie, możesz zobaczyć interesujące wzorca. W tej wersji języka C# wyeliminować standardowego języka aby kodu bardziej zwięzłym i do odczytu. Dlatego wentylatory prostemu kodu, ta wersja językowa zostało ogromnych win.

Chociaż nie jest funkcją języka tradycyjnego w sobie jak jeden element wraz z tą wersją. Ukazania [Roslyn kompilatora jako usługa](https://github.com/dotnet/roslyn). Kompilator języka C# są teraz zapisywane w języku C# i kompilator można użyć jako część wysiłków programowania.

## <a name="c-version-70"></a>C# w wersji 7.0

Najnowszą wersją główną jest C# w wersji 7.0. Ta wersja ma kilka rzeczy ewolucyjny i chłodnego w szyjnej C# w wersji 6.0, ale bez kompilatora jako usługa. Poniżej przedstawiono niektóre nowe funkcje:

- [Limit zmiennych](http://www.c-sharpcorner.com/article/out-variables-in-c-sharp-7-0/)
- [Krotki i deconstruction](https://www.thomaslevesque.com/2016/08/23/tuple-deconstruction-in-c-7/)
- [Dopasowanie wzorca](./csharp-7.md#pattern-matching)
- [Funkcje lokalne](http://www.infoworld.com/article/3182416/application-development/c-7-in-depth-exploring-local-functions.html)
- [Wyrażenie rozwinięte zabudowanych elementy członkowskie](./csharp-7.md#more-expression-bodied-members)
- [Zmienne lokalne ref i zwraca](./csharp-7.md#ref-locals-and-returns)

Inne funkcje uwzględnione:

- [Odrzucenia](../discards.md)
- [Literały binarne](https://github.com/dotnet/csharplang/blob/master/proposals/csharp-7.0/binary-literals.md)
- [Separatory cyfr](https://github.com/dotnet/csharplang/blob/master/proposals/csharp-7.0/digit-separators.md)
- Zwraca ref i zmienne lokalne
- [Wyrażenia throw](https://github.com/dotnet/csharplang/blob/master/proposals/csharp-7.0/throw-expression.md)

Wszystkie te funkcje oferują chłodnych nowych funkcji dla deweloperów i możliwość zapisu nawet czyszczący kodu niż kiedykolwiek wcześniej. Wyróżnienie jest skondensowanie trzech deklaracji zmiennych do użycia z `out` — słowo kluczowe i zezwalając wiele wartości zwrotnych za pośrednictwem spójnych kolekcji.

Ale C# jest wprowadzenia do użycia kiedykolwiek szerszych. Oprogramowanie .NET core teraz jest przeznaczony dla dowolnego systemu operacyjnego i mocno ma jego oczu w chmurze i przenoszenia.  Te nowe funkcje pewnością zajmują się opinią projektantom języka i czasu, oprócz powtarzający się z nowych funkcji.

_Artykuł_ [ _oryginalnie opublikowane w blogu NDepend_](https://blog.ndepend.com/c-versions-look-language-history/)_, dzięki uprzejmości: Dietricha Erik i Patrick Smacchia._

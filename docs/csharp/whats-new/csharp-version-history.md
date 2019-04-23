---
title: Historia języka C# — Przewodnik po języku C#
description: Język jak wygląda w jego wersje i jak go powstała od?
author: erikdietrich
ms.date: 09/20/2017
ms.openlocfilehash: 727f0064ac1de46eb670a366af38cf561e1a1533
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59303365"
---
# <a name="the-history-of-c"></a>Historia języka c\#

Ten artykuł zawiera historię każdej wersji głównej programu C# języka. C# Zespół jest w dalszym ciągu wprowadzanie innowacji i dodania nowych funkcji. Szczegóły stanów funkcji języka, w tym funkcje uznane za dla przyszłych wydaniach można znaleźć [w repozytorium dotnet/roslyn](https://github.com/dotnet/roslyn/blob/master/docs/Language%20Feature%20Status.md) w witrynie GitHub.

> [!IMPORTANT]
> C# Języka zależy od typów i metod, co C# specyfikacja definiuje się jako *biblioteki standardowej* dla niektórych funkcji. Platforma .NET dostarcza tych typów i metod w wielu pakietów. Przykładem jest wyjątek podczas przetwarzania. Każdy `throw` instrukcję lub wyrażenie jest zaznaczone, aby upewnić się, obiekt jest zgłaszana jest tworzony na podstawie <xref:System.Exception>. Podobnie co `catch` jest sprawdzany w celu zapewnienia, że typ wciągnięcia jest tworzony na podstawie <xref:System.Exception>. Każda wersja może dodawać nowych wymagań. Aby korzystać z najnowszych funkcji języków, w środowiskach starsze, może być konieczne zainstalowanie określonych bibliotek. Te zależności są udokumentowane na stronie informacjach dotyczących określonej wersji. Możesz dowiedzieć się więcej [relacje między językiem a biblioteki](relationships-between-language-and-library.md) tła na tę zależność.

C# Narzędzia do kompilacji należy wziąć pod uwagę najnowszej wersji języka głównych domyślną wersję językową. Może to być punktowe między głównymi wersjami, szczegółowo opisanych w innych artykułach w tej sekcji. Korzystanie z najnowszych funkcji w wersji punktu należy [skonfigurować wersję językową kompilatora](../language-reference/configure-language-version.md) i wybierz wersję. Zostały trzy punktowe od C# 7.0:

* [C# 7.3](csharp-7-3.md):
  - C#7.3 jest dostępna, począwszy od [Visual Studio 2017 w wersji 15.7](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) i [zestawu SDK programu .NET Core 2.1](../../core/whats-new/dotnet-core-2-1.md).
* [C# 7.2](csharp-7-2.md):
  - C#7.2 jest dostępna, począwszy od [programu Visual Studio 2017 w wersji 15.5](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link), i [.NET Core 2.0 SDK](../../core/whats-new/dotnet-core-2-0.md).
* [C# 7.1](csharp-7-1.md):
  - C#7.1 jest dostępna, począwszy od [programu Visual Studio 2017 w wersji 15.3](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) i [.NET Core 2.0 SDK](../../core/whats-new/dotnet-core-2-0.md).

## <a name="c-version-10"></a>C# w wersji 1.0

Gdy cofając się i sprawdź, C# w wersji 1.0 oglądałem się znacznie takich jak Java. Jako [wchodzi w skład jego celów projektowania podane dla ECMA](https://feeldotneteasy.blogspot.com/2011/01/c-design-goals.html), miały być "prostych, nowoczesnych, ogólnego przeznaczenia obiektowy język."  W tym czasie wyszukiwania, takie jak Java przeznaczone go osiągnąć tych wczesnych cele projektu.

Ale można spojrzeć Wstecz w języku C# 1.0 teraz, czy okaże się, że to nieco dizzy. Brakuje w niej funkcje wbudowane async i niektóre funkcje sprawny wokół ogólne potrwać dla przyznane. Jak rzeczy brakuje w niej ogólne całkowicie.  I [LINQ](../linq/index.md)? Nie jest dostępny jeszcze. Te dodatki zajmie kilka lat na osiągnięcie.

C# w wersji 1.0 znaleziono usuniętych funkcji, w porównaniu do dzisiaj. Czy okaże się, że pisanie kodu pełne. Ale jeszcze, trzeba uruchomić w innym miejscu. C# w wersji 1.0 został realną alternatywę do języka Java na platformie Windows.

Główne funkcje języka C# 1.0 obejmuje:

- [Klasy](../programming-guide/classes-and-structs/classes.md)
- [Struktury](../programming-guide/classes-and-structs/structs.md)
- [Interfejsy](../programming-guide/interfaces/index.md)
- [Zdarzenia](../events-overview.md)
- [Właściwości](../properties.md)
- [Delegaty](../delegates-overview.md)
- [Wyrażenia](../programming-guide/statements-expressions-operators/expressions.md)
- [Instrukcje](../programming-guide/statements-expressions-operators/statements.md)
- [Atrybuty](../programming-guide/concepts/attributes/index.md)
- [Literały](../language-reference/keywords/literal-keywords.md)

## <a name="c-version-12"></a>C# w wersji 1.2

C# w wersji 1.2 dostarczane z programem Visual Studio 2003. Zawiera kilka ulepszeń małych dla języka. Większość warto jest uruchamianie z tą wersją, kod generowany w `foreach` pętli wywołuje <xref:System.IDisposable.Dispose%2A> na <xref:System.Collections.IEnumerator> podczas który <xref:System.Collections.IEnumerator> zaimplementowane <xref:System.IDisposable>.

## <a name="c-version-20"></a>C# w wersji 2.0

Teraz rozpocząć pobieranie interesujących rzeczy. Spójrzmy na niektóre główne funkcje języka C# w wersji 2.0, wydany w 2005 r. wraz z Visual Studio 2005:

- [Typy ogólne](../programming-guide/generics/index.md)
- [Typy częściowe](../programming-guide/classes-and-structs/partial-classes-and-methods.md#partial-classes)
- [Metody anonimowe](../programming-guide/statements-expressions-operators/anonymous-methods.md)
- [Typy dopuszczające wartości zerowe](../programming-guide/nullable-types/index.md)
- [Iteratory](../programming-guide/concepts/iterators.md)
- [Kowariancja i kontrawariancja](../programming-guide/concepts/covariance-contravariance/index.md)

Inne funkcje języka C# w wersji 2.0 dodaje funkcje do istniejących funkcji:

- Metody pobierającej/ustawiającej oddzielne ułatwień dostępu
- Metoda grupy konwersje (delegatów)
- Klasy statyczne
- Wnioskowanie delegata

Gdy C# mogły zostać rozpoczęte jako ogólnego język Object-Oriented (wprowadzaniem), C# w wersji 2.0 zmieniła tę sytuację masz mało czasu. Gdy mieli oni ich stopy w ramach nich, błąd po niektóre słabe punkty poważne dla deweloperów. I ich po ich w znaczący sposób.

Ogólne typy i metody mogą działać na dowolnego typu, przy jednoczesnym zachowaniu bezpieczeństwa typu. Na przykład masz <xref:System.Collections.Generic.List%601> pozwala mieć `List<string>` lub `List<int>` i wykonywać operacje bezpieczny, na tych ciągów lub liczby całkowite, podczas gdy iteracyjne przeglądanie ich. Za pomocą typów ogólnych jest lepsze niż tworzenie `ListInt` który pochodzi od klasy `ArrayList` lub głosujących z `Object` dla każdej operacji.

C# w wersji 2.0 dostosowane Iteratory. Aby przełączyć krótkiej formie, Iteratory pozwalają sprawdzić wszystkie elementy w `List` (lub inne typy Wyliczalny) przy użyciu `foreach` pętli. O najwyższej jakości część języka Iteratory znacznie ulepszony czytelność język i osób umożliwia przeglądanie informacji o kodzie.

I jeszcze, C# kontynuowane do odtwarzania znacznej liczby — wyrównywanie przy użyciu języka Java. Java już miał wydane wersje, które uwzględnione typy ogólne i Iteratory. Ale, szybko zmienić jako języków rozwijała się od siebie.

## <a name="c-version-30"></a>C# w wersji 3.0

C# w wersji 3.0 materiał pod koniec 2007, wraz z programu Visual Studio 2008, chociaż pełną łodzi funkcji języka faktycznie przybyły, aby za pomocą platformy .NET Framework w wersji 3.5. Ta wersja oznaczona istotne zmiany w rozwoju języka C#. Stwierdzone C# jako naprawdę potężnych języka programowania. Spójrzmy na niektóre główne funkcje w tej wersji:

- [Właściwości zaimplementowane automatycznie](../programming-guide/classes-and-structs/auto-implemented-properties.md)
- [Typy anonimowe](../programming-guide/classes-and-structs/anonymous-types.md)
- [Wyrażenia zapytań](../linq/query-expression-basics.md)
- [Wyrażenia lambda](../programming-guide/statements-expressions-operators/lambda-expressions.md)
- [Drzewa wyrażeń](../expression-trees.md)
- [Metody rozszerzenia](../programming-guide/classes-and-structs/extension-methods.md)
- [Niejawnie wpisane zmienne lokalne](../language-reference/keywords/var.md)
- [Metody częściowe](../language-reference/keywords/partial-method.md)
- [Inicjatory obiektów i kolekcji](../programming-guide/classes-and-structs/object-and-collection-initializers.md)

Spoglądając wstecz wiele z tych funkcji prawdopodobnie nierozdzielne i nieuniknione. Wszystkie one współdziałają ze sobą strategicznie. Ogólnie uważa się, że się opracować świetną funkcji języka C# wersji była wyrażenie zapytania, znany także jako Query Language-Integrated (LINQ).

Bardziej dopracowanego widoku sprawdza, czy drzew wyrażeń, wyrażeń lambda i typy anonimowe jako podstawę, na którym jest konstruowany LINQ. Jednak w obu przypadkach języka C# 3.0 prezentowane Rewolucyjny koncepcji. C# 3.0 zaczęło przygotowawczych Włączanie C# do hybrydowego rozwiązania łączącego program język zorientowany obiektowo / funkcjonalności.

W szczególności można teraz zapisać SQL stylu deklaratywne zapytania w celu wykonywania operacji na kolekcjach, między innymi. Zamiast pisania `for` pętli do obliczenia średniej na liście liczb całkowitych, możesz teraz to zrobić, tak po prostu jako `list.Average()`. Kombinacja wyrażenia zapytania i metody rozszerzenia mogła wyglądać tak, jakby listę liczb całkowitych miał punktowania całego inteligentniejsze.

Zajęło czasu dla osób naprawdę zapoznanie się z nim i zintegruj pojęcia, ale stopniowo ta funkcjonalność była niedostępna. A teraz lata później, kod jest znacznie bardziej zwięzły, prosty i funkcjonalności.

## <a name="c-version-40"></a>C# w wersji 4.0

C# w wersji 4.0 było trudne czas życia przełomowym stan wersji 3.0 lub nowszej. W wersji 3.0 C# przeniósł języka mocno na zewnątrz w tle języka Java i dostępność. Język został szybko staje się funkcją elegancki.

Następna wersja wprowadzają interesujące nowe funkcje:

- [Wiązanie dynamiczne](../language-reference/keywords/dynamic.md)
- [Argumenty nazwane opcjonalne](../programming-guide/classes-and-structs/named-and-optional-arguments.md)
- [Ogólny kowariantne i kontrawariantne](../../standard/generics/covariance-and-contravariance.md)
- [Osadzone typy międzyoperacyjne](../../framework/interop/type-equivalence-and-embedded-interop-types.md)

Osadzone typy międzyoperacyjne złagodzone bolesne wdrożenia. Ogólny kowariancji i kontrawariancji zapewniają większe możliwości używaj typów ogólnych, ale są one nieco naukowych i prawdopodobnie większość Doceniamy przez autorów framework i biblioteki. Parametry nazwane i opcjonalne pozwalają wyeliminować wiele przeciążeń metody i zapewnia wygodę. Ale żaden z tych funkcji są dokładnie paradygmat zmiany.

Główna funkcja była wprowadzenie `dynamic` — słowo kluczowe. `dynamic` — Słowo kluczowe wprowadzone w języku C# w wersji 4.0 możliwość przesłaniania kompilatora w przypadku wpisywania w czasie kompilacji. Za pomocą słowa kluczowego dynamic, można utworzyć konstrukcje podobnie jak w językach takich jak JavaScript. Możesz utworzyć `dynamic x = "a string"` , a następnie dodaj sześć, pozostawiając je do środowiska uruchomieniowego, aby posortować się, co powinno się zdarzyć, obok.

Wiązanie dynamiczne zawierają potencjalnych błędów, ale także mocą języka.

## <a name="c-version-50"></a>C# w wersji 5.0

C# w wersji 5.0 był konkretną wersję języka. Prawie wszystkich naruszeń nakładu pracy dla tej wersji pojawiły się w innym koncepcji języka przełomowym: `async` i `await` modelu programowania asynchronicznego.  Poniżej przedstawiono listę najważniejszych funkcji:

- [Asynchroniczne elementów członkowskich](../async.md)
- [Caller — atrybuty informacji](../programming-guide/concepts/caller-information.md)

### <a name="see-also"></a>Zobacz też

* [Projekt kodu: Informacji o obiekcie wywołującym atrybutów w C# 5.0](https://www.codeproject.com/Tips/606379/Caller-Info-Attributes-in-Csharp)

Obiekt wywołujący atrybutu informacji pozwala łatwo pobrać informacje o kontekście, w którym pracujesz, bez konieczności uciekania się do ogromnej ilości standardowy kod odbicia. Ma wiele zastosowań w diagnostycznych i zadań rejestrowania.

Ale `async` i `await` są prawdziwe gwiazdek w tej wersji. Gdy te funkcje pochodzi w 2012, C# gry jej ponownie zmienić przez pieczenie asynchroniczności w języku jako uczestnik najwyższej jakości. Jeśli nigdy nie zostały omówione długotrwałych operacji i wdrażanie witryny sieci Web wywołań zwrotnych, należy prawdopodobnie tak Ci się podobały tej funkcji języka.

## <a name="c-version-60"></a>C# w wersji 6.0

W przypadku wersji 3.0 i 5.0 C# miał dodano główne nowe funkcje w języku zorientowane obiektowo. W wersji 6.0 będzie przejdź od wykonując dominujący funkcji się opracować świetną i zamiast tego wydania wiele mniejszych funkcji, które programowania C# bardziej produktywne. Poniżej przedstawiono niektóre z nich:

- [Importy statyczne](./csharp-6.md#using-static)
- [Filtry wyjątków](./csharp-6.md#exception-filters)
- [Inicjatory właściwości automatycznej](./csharp-6.md#auto-property-initializers)
- [Wyrażenie zabudowanych członków](./csharp-6.md#expression-bodied-function-members)
- [Propagator o wartości null](./csharp-6.md#null-conditional-operators)
- [Interpolacja ciągów](./csharp-6.md#string-interpolation)
- [nameof operator](./csharp-6.md#the-nameof-expression)
- [Inicjatory indeksów](csharp-6.md#extension-add-methods-in-collection-initializers)

Inne nowe funkcje obejmują:

- Await w blokach catch/finally
- Domyślne wartości dla właściwości tylko do metody pobierającej

Każda z tych funkcji jest interesujące samodzielną. Jednak jeśli przyjrzymy się je całkowicie, zobaczysz interesujące wzorca. W tej wersji języka C# wyeliminować standardowy język, aby zwięzła i bardziej czytelny kod. Aby dla kibiców prostemu kodu, ta wersja językowa był olbrzymią zaletę.

Chociaż nie jest funkcją języka tradycyjnego sam jak jeden element wraz z tą wersją. Zespół [Roslyn kompilatora jako usługa](https://github.com/dotnet/roslyn). Kompilator języka C# są teraz zapisywane w języku C#, a kompilator można użyć jako część prace programistyczne.

## <a name="c-version-70"></a>C# w wersji 7.0

Najbardziej aktualną wersję główną jest C# w wersji 7.0. Ta wersja ma kilka rzeczy ewolucyjny, jak i chłodnej w szyjnej języka C# 6.0, ale bez kompilator jako usługa. Poniżej przedstawiono nowe funkcje:

- [Limit zmiennych](./csharp-7.md#out-variables)
- [Dekonstrukcja i kolekcje](./csharp-7.md#tuples)
- [Dopasowanie do wzorca](./csharp-7.md#pattern-matching)
- [Funkcje lokalne](./csharp-7.md#local-functions)
- [Wyrażenie rozwiniętej zabudowanych członków](./csharp-7.md#more-expression-bodied-members)
- [Zmienne lokalne ref i zwraca](./csharp-7.md#ref-locals-and-returns)

Inne funkcje uwzględnione:

- [Odrzucenia](./csharp-7.md#discards)
- [Literały binarne oraz separatory cyfr](./csharp-7.md#numeric-literal-syntax-improvements)
- [Wyrażenia throw](./csharp-7.md#throw-expressions)

Wszystkie te funkcje oferują ciekawe nowe funkcje dla deweloperów i możliwość pisania kodu jeszcze bardziej przejrzyste niż kiedykolwiek wcześniej. Wyróżnienie jest skondensowanie trzech deklaracji zmiennych, za pomocą `out` — słowo kluczowe i umożliwiając z wieloma wartościami zwracanymi za pomocą spójnej kolekcji.

Ale C# jest umieszczeniem do coraz szerszego użycia. .NET core teraz jest przeznaczony dla dowolnego systemu operacyjnego i oczy mocno na chmurze i przenośność.  Te nowe możliwości bez obaw zajmują projektantom języka pomysły i godzinę, oprócz pojawi się z nowymi funkcjami.

_Artykuł_ [ _oryginalnie opublikowane na blogu NDepend_](https://blog.ndepend.com/c-versions-look-language-history/)_, uzyskajcie Dietricha Erik i Patrick Smacchia._

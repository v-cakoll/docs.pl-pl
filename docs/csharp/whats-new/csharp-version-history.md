---
title: Historia C# - C# Przewodnik
description: Jak wygląda ten język we wcześniejszych wersjach i jak został on rozwijający od?
author: erikdietrich
ms.date: 09/20/2017
ms.openlocfilehash: 304c433e7f15301b77e8b2440e27795dcdea345c
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2019
ms.locfileid: "70893163"
---
# <a name="the-history-of-c"></a>Historia języka C\#

Ten artykuł zawiera historię poszczególnych głównych wersji C# języka. C# Zespół kontynuuje wprowadzanie innowacji i dodawanie nowych funkcji. Szczegółowy stan funkcji języka, w tym funkcje uwzględniane w przypadku przyszłych wersji, można znaleźć [w repozytorium dotnet/Roslyn](https://github.com/dotnet/roslyn/blob/master/docs/Language%20Feature%20Status.md) w witrynie GitHub.

> [!IMPORTANT]
> C# Język polega na typach i metodach, C# które definiuje Specyfikacja jako *standardowa biblioteka* dla niektórych funkcji. Platforma .NET dostarcza te typy i metody w wielu pakietach. Przykładem jest przetwarzanie wyjątków. Każda `throw` instrukcja lub wyrażenie jest zaznaczone, aby upewnić się, że zgłaszany <xref:System.Exception>obiekt jest pochodną. Podobnie każde `catch` jest sprawdzane w celu upewnienia się, że typ, który <xref:System.Exception>jest przechwytywany, pochodzi od. Każda wersja może dodawać nowe wymagania. Aby korzystać z najnowszych funkcji języka w starszych środowiskach, może być konieczne zainstalowanie określonych bibliotek. Te zależności są udokumentowane na stronie dla każdej konkretnej wersji. Aby uzyskać więcej informacji na temat [relacji między językiem i biblioteką](relationships-between-language-and-library.md) w tle, należy zapoznać się z tematem dotyczącym tej zależności.

Narzędzia C# kompilacji uwzględniają najnowszą wersję językową wersji językowej. Między wersjami głównymi mogą występować wersje punktów, które opisano w innych artykułach w tej sekcji. Aby użyć najnowszych funkcji w wersji próbnej, należy [skonfigurować wersję języka kompilatora](../language-reference/configure-language-version.md) i wybrać wersję. Istnieją trzy wersje punktów od C# 7,0:

- [C# 7.3](csharp-7-3.md):
  - C#7,3 jest dostępna począwszy od [programu Visual Studio 2017 w wersji 15,7](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) i [.NET Core 2,1 SDK](../../core/whats-new/dotnet-core-2-1.md).
- [C# 7.2](csharp-7-2.md):
  - C#7,2 jest dostępna począwszy od [programu Visual Studio 2017 w wersji 15,5](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)i [.NET Core 2,0 SDK](../../core/whats-new/dotnet-core-2-0.md).
- [C# 7.1](csharp-7-1.md):
  - C#7,1 jest dostępna począwszy od [programu Visual Studio 2017 w wersji 15,3](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) i [.NET Core 2,0 SDK](../../core/whats-new/dotnet-core-2-0.md).

## <a name="c-version-10"></a>C#Wersja 1,0

Po wycofaniu i powrocie do C# wersji 1,0 wydanej w programie Visual Studio.NET 2002 sprawdzono wiele takich elementów jak Java. Zgodnie [z ustalonymi celami projektu dla języka ECMA](https://feeldotneteasy.blogspot.com/2011/01/c-design-goals.html), powinien to być "prosty, nowoczesny, zorientowany na obiekty ogólnego przeznaczenia".  W tym czasie wygląda na to, że środowisko Java osiągnęło te wczesne cele projektowania.

Jeśli jednak powrócisz do C# 1,0 teraz, znajdziesz nieco trochę Dizzy. Brakuje wbudowanych funkcji asynchronicznych i niektórych funkcji sprawny wokół typów ogólnych, które należy podjąć. Z tego względu nie wszystkie ogólne.  I [LINQ](../linq/index.md)? Jeszcze niedostępne. Te dodatki będą trwać kilka lat.

C#w wersji 1,0 zostały wyszukane funkcje, w porównaniu do dzisiaj. Znajdziesz kod pełny. Jednak musisz zacząć korzystać z dowolnego miejsca. C#Wersja 1,0 była opłacalną alternatywą dla języka Java na platformie Windows.

Główne funkcje C# 1,0 obejmują:

- [Klasy](../programming-guide/classes-and-structs/classes.md)
- [Struktury](../programming-guide/classes-and-structs/structs.md)
- [Interfejsy](../programming-guide/interfaces/index.md)
- [Zdarzenia](../events-overview.md)
- [Właściwości](../properties.md)
- [Delegaty](../delegates-overview.md)
- [Wyrażenia](../programming-guide/statements-expressions-operators/expressions.md)
- [Instrukcje](../programming-guide/statements-expressions-operators/statements.md)
- [Atrybuty](../programming-guide/concepts/attributes/index.md)

## <a name="c-version-12"></a>C#Wersja 1,2

C#Wersja 1,2 dostarczana z programem Visual Studio 2003. Zawiera kilka małych ulepszeń w języku. Najbardziej istotny jest to, że począwszy od tej wersji, kod wygenerowany `foreach` w pętli <xref:System.IDisposable.Dispose%2A> wywoływana w <xref:System.Collections.IEnumerator> przypadku, <xref:System.Collections.IEnumerator> gdy <xref:System.IDisposable>jest zaimplementowany.

## <a name="c-version-20"></a>C#Wersja 2,0

Teraz można zacząć korzystać z interesujących rzeczy. Przyjrzyjmy się najważniejszym funkcjom C# 2,0, wydawanym w 2005, wraz z programem Visual Studio 2005:

- [Typy ogólne](../programming-guide/generics/index.md)
- [Typy częściowe](../programming-guide/classes-and-structs/partial-classes-and-methods.md#partial-classes)
- [Metody anonimowe](../language-reference/operators/delegate-operator.md)
- [Typy dopuszczające wartości null](../programming-guide/nullable-types/index.md)
- [Iteratory](../programming-guide/concepts/iterators.md)
- [Kowariancja i kontrawariancja](../programming-guide/concepts/covariance-contravariance/index.md)

Inne C# funkcje 2,0 dodaliśmy możliwości do istniejących funkcji:

- Metoda pobierająca/setter oddzielna dostępność
- Konwersje grup metod (delegatów)
- Klasy statyczne
- Delegowanie wnioskowania

Program C# mógł zostać uruchomiony jako ogólny język zorientowany obiektowo (oo) w C# wersji 2,0 zmienionej w pospiesz. Gdy miały swoje stopy w nich, zakończyły się po kilku poważnych punktach bólu deweloperów. I zostały one w znaczący sposób.

W przypadku typów ogólnych typy i metody mogą działać na dowolnym typie przy zachowaniu bezpieczeństwa typu. Na przykład, jeśli istnieje <xref:System.Collections.Generic.List%601> , `List<int>` a umożliwia `List<string>` wykonywanie operacji bezpiecznych typu na tych ciągach lub liczbach całkowitych w trakcie iteracji. Używanie typów ogólnych jest lepszym rozwiązaniem `ListInt` niż tworzenie, `ArrayList` które wynika z `Object` lub rzutowanie z dla każdej operacji.

C#Wersja 2,0 przenoszona Iteratory. Aby umieścić je w sposób zwięzły, Iteratory umożliwiają badanie wszystkich elementów w `List` (lub innych wyliczalnych typach) `foreach` za pomocą pętli. Posiadanie iteratorów jako pierwszej klasy języka znacznie zwiększa czytelność języka i zdolności osób do uzyskania informacji o kodzie.

Jeszcze w C# dalszym ciągu można odtworzyć nieco rozwiązania z technologią Java. Java wydano już wersje, które zawierały typy ogólne i Iteratory. Ale to wkrótce zmieni się, ponieważ Języki będą nadal rozliczane od siebie.

## <a name="c-version-30"></a>C#Wersja 3,0

C#Wersja 3,0 została odebrana w późnej 2007, wraz z programem Visual Studio 2008, chociaż pełna łódź funkcji językowych rzeczywiście będzie miała .NET Framework wersja 3,5. Ta wersja oznacza istotną zmianę w zakresie C#wzrostu. Jest on C# ustanowiony jako prawdziwie Formidable język programowania. Spójrzmy na kilka najważniejszych funkcji w tej wersji:

- [Właściwości zaimplementowane wstępnie](../programming-guide/classes-and-structs/auto-implemented-properties.md)
- [Typy anonimowe](../programming-guide/classes-and-structs/anonymous-types.md)
- [Wyrażenia zapytań](../linq/query-expression-basics.md)
- [Wyrażenia lambda](../programming-guide/statements-expressions-operators/lambda-expressions.md)
- [Drzewa wyrażeń](../expression-trees.md)
- [Metody rozszerzające](../programming-guide/classes-and-structs/extension-methods.md)
- [Niejawnie wpisane zmienne lokalne](../language-reference/keywords/var.md)
- [Metody częściowe](../language-reference/keywords/partial-method.md)
- [Inicjatory obiektów i kolekcji](../programming-guide/classes-and-structs/object-and-collection-initializers.md)

W programie Spoglądając wstecz wiele z tych funkcji sprawia, że są one nieuniknione i nierozdzielne. Wszystkie te same pasują do siebie strategicznie. Zazwyczaj uważa się, że C# funkcja Killer wersji była wyrażeniem zapytania, znanym również jako zapytanie zintegrowane z językiem (LINQ).

Dokładniejszy widok złożonych bada drzewa wyrażeń, wyrażenia lambda i typy anonimowe jako podstawę, na której jest konstruowany składnik LINQ. Jednak w obu przypadkach C# 3,0 przedstawiał koncepcję Rewolucyjne. C#3,0 rozpoczęto w celu określenia podstawę C# do przetworzenia hybrydowego języka programowania/funkcjonalności.

W tym celu można teraz napisać w stylu SQL zapytania deklaracyjne, aby wykonywać operacje na kolekcjach, między innymi. Zamiast pisać `for` pętlę, aby obliczyć średnią z listy liczb całkowitych, można to zrobić tak `list.Average()`samo jak w przypadku. Kombinacja wyrażeń zapytania i metod rozszerzających wygląda tak, jakby ta lista liczb całkowitych uzyskała całą dużą liczbę.

Zajęło ci dużo czasu na opanujesz i integrację koncepcji, ale stopniowo. A teraz lata później, kod jest znacznie bardziej zwięzły, prosty i funkcjonalny.

## <a name="c-version-40"></a>C#wersja 4,0

C#w wersji 4,0 wydanej w programie Visual Studio 2010 wystąpił trudny czas utrzymania stanu przełomowe w wersji 3,0. W wersji 3,0, C# język został przesunięty od cienia środowiska Java do wyeksponowanie. Język mógł szybko stać się elegancki.

Następna wersja wprowadziła interesujące nowe funkcje:

- [Powiązanie dynamiczne](../language-reference/keywords/dynamic.md)
- [Argumenty nazwane/opcjonalne](../programming-guide/classes-and-structs/named-and-optional-arguments.md)
- [Ogólna współvariant i kontrawariantne](../../standard/generics/covariance-and-contravariance.md)
- [Osadzone typy międzyoperacyjnych](../../framework/interop/type-equivalence-and-embedded-interop-types.md)

Wbudowane typy międzyoperacyjności zmniejszają możliwości wdrożenia. Ogólna Kowariancja i kontrawariancja zapewniają większą moc do korzystania z typów ogólnych, ale są one nieco akademickie i prawdopodobnie najbardziej doceniane przez autorów struktury i biblioteki. Parametry nazwane i opcjonalne pozwalają wyeliminować wiele przeciążeń metod i zapewnić wygodę. Jednak żadna z tych funkcji nie ma dokładnej zmiany modelu.

Funkcja główna była wprowadzeniem `dynamic` słowa kluczowego. Słowo kluczowe wprowadzone do C# wersji 4,0 może przesłonić kompilator podczas pisania w czasie kompilacji. `dynamic` Za pomocą słowa kluczowego Dynamic można tworzyć konstrukcje podobne do dynamicznie wpisanych języków, takich jak JavaScript. Możesz utworzyć `dynamic x = "a string"` a następnie dodać do niej sześć, pozostawiając ją w środowisku uruchomieniowym, aby określić, co powinno się stać dalej.

Dynamiczne powiązanie zapewnia potencjalne błędy, ale również doskonale moc w języku.

## <a name="c-version-50"></a>C#wersja 5,0

C#wersja 5,0 wydana w programie Visual Studio 2012 była skoncentrowaną wersją języka. Niemal cały nakład pracy związany z tą wersją osiągnął inną koncepcję języka przełomowe: `async` model `await` i programowanie asynchroniczne.  Oto lista głównych funkcji:

- [Asynchroniczne elementy członkowskie](../async.md)
- [Atrybuty informacji o wywołującym](../programming-guide/concepts/caller-information.md)

### <a name="see-also"></a>Zobacz też

- [Projekt kodu: Atrybuty informacji o wywołującym w C# 5,0](https://www.codeproject.com/Tips/606379/Caller-Info-Attributes-in-Csharp)

Atrybut informacje o wywołującym pozwala łatwo pobrać informacje dotyczące kontekstu, w którym jest wykonywane, bez konieczności przeliczania się na tonę standardowego kodu odbicia. Ma wiele użycia w zadaniach diagnostycznych i dzienników.

Ale `async` i`await` są rzeczywiste gwiazdki tej wersji. Gdy te funkcje zostały dostarczone w 2012, C# zmieniono grę ponownie, asynchroniczności jako uczestnika pierwszej klasy. Jeśli kiedykolwiek zdarzyło Ci się zająć długotrwałymi operacjami i implementacją sieci Web wywołania zwrotnego, prawdopodobnie uwielbiane tej funkcji językowej.

## <a name="c-version-60"></a>C#wersja 6,0

W przypadku wersji 3,0 i 5,0 C# dodano najważniejsze nowe funkcje w języku zorientowanym obiektowo. W wersji 6,0 wydanej w Visual Studio 2013 nie można przeprowadzić C# dominującej funkcji Killer i zamiast tego wydać wiele mniejszych funkcji, które zwiększają produktywność. Oto niektóre z nich:

- [Importy statyczne](./csharp-6.md#using-static)
- [Filtry wyjątków](./csharp-6.md#exception-filters)
- [Inicjatory właściwości autoproperty](./csharp-6.md#auto-property-initializers)
- [Wyrażenie składowych składowanych](./csharp-6.md#expression-bodied-function-members)
- [Propagator o wartości null](./csharp-6.md#null-conditional-operators)
- [Interpolacja ciągów](./csharp-6.md#string-interpolation)
- [operator nameof](./csharp-6.md#the-nameof-expression)
- [Inicjatory indeksów](csharp-6.md#extension-add-methods-in-collection-initializers)

Inne nowe funkcje obejmują:

- Await w blokach catch/finally
- Wartości domyślne właściwości metody pobierającej

Każda z tych funkcji jest interesująca po prawej stronie. Ale jeśli zobaczysz je całkowicie, zobaczysz interesujący wzór. W tej wersji można C# wyeliminować język standardowy, aby kod był bardziej zwięzła i możliwy do odczytania. Tak więc dla wentylatorów czysty, prosty kod, ta wersja językowa była ogromnym wygraniem.

Te osoby były jednym innym elementem wraz z tą wersją, chociaż nie jest tradycyjną funkcją języka. Zostały one wydane [Roslyn kompilator jako usługi](https://github.com/dotnet/roslyn). C# Kompilator jest teraz zapisywana C#i można użyć kompilatora w ramach wysiłków programistycznych.

## <a name="c-version-70"></a>C#wersja 7,0

Najnowsza wersja główna jest C# w wersji 7,0 wydanej w programie Visual Studio 2017. Ta wersja ma pewne ewolucje i chłodnie w szyjce C# 6,0, ale bez kompilatora jako usługi. Oto niektóre z nowych funkcji:

- [Zmienne out](./csharp-7.md#out-variables)
- [Krotki i dekonstrukcja](./csharp-7.md#tuples)
- [Dopasowanie do wzorca](./csharp-7.md#pattern-matching)
- [Funkcje lokalne](./csharp-7.md#local-functions)
- [Rozwinięte składowe wyrażeń](./csharp-7.md#more-expression-bodied-members)
- [Ref locales i Returns](./csharp-7.md#ref-locals-and-returns)

Dostępne są inne funkcje:

- [Odrzucenia](./csharp-7.md#discards)
- [Literały binarne i separatory cyfr](./csharp-7.md#numeric-literal-syntax-improvements)
- [Wyrażenia throw](./csharp-7.md#throw-expressions)

Wszystkie te funkcje oferują chłodne nowe możliwości dla deweloperów i możliwość pisania jeszcze bardziej estetycznego kodu. Podświetlanie zbliża się do deklaracji zmiennych, które mają być używane ze `out` słowem kluczowym, i zezwalając na wiele wartości zwracanych za pośrednictwem krotki.

Ale C# jest wprowadzany do coraz szerszego użycia. Platforma .NET Core jest teraz przeznaczona dla dowolnego systemu operacyjnego i ma swoje oczy w chmurze i na przenośności.  Te nowe funkcje mają na celu zajmowanie pomysłów i czasu projektanta języka, a także nowe funkcje.

_Artykuł_ [_pierwotnie opublikowany na blogu NDepend_](https://blog.ndepend.com/c-versions-look-language-history/) _, grzecznościowa Erik Dietrich i Patryk Smacchia._

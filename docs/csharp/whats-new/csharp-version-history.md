---
title: Historia przewodnika C# - C#
description: Jak wyglądał język w jego najwcześniejszych wersjach i jak ewoluował od tego czasu?
author: erikdietrich
ms.date: 04/08/2020
ms.openlocfilehash: d9f50a7df7966f81366acb706d719cbdd40a45fa
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989197"
---
# <a name="the-history-of-c"></a>Historia C\#

Ten artykuł zawiera historię każdej głównej wersji języka C#. Zespół języka C# kontynuuje wprowadzanie innowacji i dodawanie nowych funkcji. Szczegółowy stan funkcji języka, w tym funkcje rozważane dla nadchodzących wydań można znaleźć [w repozytorium dotnet/roslyn](https://github.com/dotnet/roslyn/blob/master/docs/Language%20Feature%20Status.md) na GitHub.

> [!IMPORTANT]
> Język C# opiera się na typy i metody, w jakiej specyfikacji Języka C# definiuje jako *standardową bibliotekę* dla niektórych funkcji. Platforma .NET dostarcza te typy i metody w wielu pakietach. Jednym z przykładów jest przetwarzanie wyjątków. Każda `throw` instrukcja lub wyrażenie jest sprawdzana, aby <xref:System.Exception>upewnić się, że obiekt jest generowany z . Podobnie każdy `catch` jest sprawdzany, aby upewnić się, <xref:System.Exception>że typ złowionych pochodzi od . Każda wersja może dodać nowe wymagania. Aby korzystać z najnowszych funkcji językowych w starszych środowiskach, może być konieczne zainstalowanie określonych bibliotek. Te zależności są udokumentowane na stronie dla każdej określonej wersji. Możesz dowiedzieć się więcej o [relacjach między językiem i biblioteką](relationships-between-language-and-library.md) w tle tej zależności.

Narzędzia kompilacji języka C# uwzględnić najnowszą wersję języka głównego domyślnej wersji językowej. Mogą istnieć wersje punktowe między głównymi wersjami, szczegółowo opisane w innych artykułach w tej sekcji. Aby korzystać z najnowszych funkcji w wersji punktowej, należy [skonfigurować wersję językową kompilatora](../language-reference/configure-language-version.md) i wybrać wersję. Od c# 7.0 zostały wydania trzech punktów:

- [C# 7.3](csharp-7-3.md):
  - C# 7.3 jest dostępny począwszy od [visual studio 2017 w wersji 15.7](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) i [.NET Core 2.1 SDK](../../core/whats-new/dotnet-core-2-1.md).
- [C# 7.2](csharp-7-2.md):
  - C# 7.2 jest dostępny począwszy od [visual studio 2017 w wersji 15.5](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) i [.NET Core 2.0 SDK](../../core/whats-new/dotnet-core-2-0.md).
- [C# 7.1](csharp-7-1.md):
  - C# 7.1 jest dostępny począwszy od [visual studio 2017 w wersji 15.3](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) i [.NET Core 2.0 SDK](../../core/whats-new/dotnet-core-2-0.md).

## <a name="c-version-10"></a>C# wersja 1.0

Po powrocie i spojrzeniu, C# wersja 1.0, wydany z visual studio .NET 2002, wyglądał a lot like Java. W [ramach swoich deklarowanych celów projektowych dla ECMA](https://feeldotneteasy.blogspot.com/2011/01/c-design-goals.html), starał się być "prosty, nowoczesny, ogólnego przeznaczenia zorientowany na język."  W tym czasie, patrząc jak Java oznaczało, że osiągnąć te wczesne cele projektowe.

Ale jeśli spojrzeć wstecz na C # 1.0 teraz, można znaleźć się trochę zawroty głowy. Brakowało wbudowanych możliwości async i niektóre zręczny funkcjonalność wokół generycznych wziąć za pewnik. W rzeczywistości, brakowało leków generycznych w ogóle.  I [LINQ](../linq/index.md)? Jeszcze niedostępne. Te dodatki zajęłoby kilka lat, aby wyjść.

C# wersja 1.0 wyglądała pozbawione funkcji, w porównaniu do dzisiaj. Można znaleźć się pisanie jakiegoś szczegółowego kodu. Ale jednak musisz gdzieś zacząć. C# w wersji 1.0 był realną alternatywą dla Java na platformie Windows.

Główne cechy C# 1.0 zawarte:

- [Klasy](../programming-guide/classes-and-structs/classes.md)
- [Struktury](../language-reference/builtin-types/struct.md)
- [Interfejsy](../programming-guide/interfaces/index.md)
- [Zdarzenia](../events-overview.md)
- [Właściwości](../properties.md)
- [Delegaty](../delegates-overview.md)
- [Wyrażenia](../programming-guide/statements-expressions-operators/expressions.md)
- [Instrukcje](../programming-guide/statements-expressions-operators/statements.md)
- [Atrybuty](../programming-guide/concepts/attributes/index.md)

## <a name="c-version-12"></a>C# wersja 1.2

C# w wersji 1.2 dostarczane z programem Visual Studio .NET 2003. Zawierał kilka drobnych ulepszeń języka. Najbardziej godne uwagi jest to, że począwszy od tej <xref:System.Collections.IEnumerator> wersji, <xref:System.IDisposable>kod generowany w `foreach` pętli wywoływanej <xref:System.IDisposable.Dispose%2A> <xref:System.Collections.IEnumerator> na kiedy to zaimplementowane .

## <a name="c-version-20"></a>C# wersja 2.0

Teraz wszystko zaczyna się ciekawie. Ramięć spojrzeć na niektóre główne funkcje C# 2.0, wydany w 2005 r., wraz z Visual Studio 2005:

- [Typy ogólne](../programming-guide/generics/index.md)
- [Typy częściowe](../programming-guide/classes-and-structs/partial-classes-and-methods.md#partial-classes)
- [Metody anonimowe](../language-reference/operators/delegate-operator.md)
- [Typy wartości dopuszczające wartość null](../language-reference/builtin-types/nullable-value-types.md)
- [Iteratory](../programming-guide/concepts/iterators.md)
- [Kowariancja i kontrawariancja](../programming-guide/concepts/covariance-contravariance/index.md)

Inne funkcje języka C# 2.0 dodały możliwości do istniejących funkcji:

- Rozdzielacza/ustawiacza oddzielna dostępność
- Konwersje grup metod (delegaci)
- Klasy statyczne
- Wnioskowanie delegowania

Podczas C# może zostały uruchomione jako ogólny język obiektowy (OO), C# wersja 2.0 zmienił, że w pośpiechu. Gdy mieli pod sobą nogi, poszli po kilka poważnych punktów bólu dewelopera. I poszli za nimi w znaczący sposób.

W przypadku leków generycznych typy i metody mogą działać na dowolnym typie, zachowując jednocześnie bezpieczeństwo typu. Na przykład o <xref:System.Collections.Generic.List%601> pozwala `List<string>` mieć `List<int>` lub i wykonywać operacje bezpieczne dla typu na tych ciągów lub liczby całkowite podczas iteracji za ich pośrednictwem. Korzystanie z generycznych `ListInt` jest lepsze `ArrayList` niż `Object` tworzenie, które pochodzi z lub rzutowania z każdej operacji.

C# wersja 2.0 przyniósł iteratory. Mówiąc zwięźle, iteratory umożliwiają zbadanie wszystkich elementów w `List` (lub innych typów `foreach` wyliczalnych) za pomocą pętli. Posiadanie iteratorów jako pierwszej klasy części języka znacznie zwiększyło czytelność języka i zdolność ludzi do rozumowania kodu.

A jednak, C# nadal grać trochę dogonić Java. Java wydała już wersje, które zawierały leki generyczne i iteratory. Ale to wkrótce się zmieni, ponieważ języki nadal ewoluują od siebie.

## <a name="c-version-30"></a>C# wersja 3.0

C# wersja 3.0 przyszedł pod koniec 2007 r., wraz z visual studio 2008, choć pełna łódź funkcji języka rzeczywiście pochodzą z .NET Framework w wersji 3.5. Ta wersja oznaczała istotną zmianę w rozwoju języka C#. Ustanowiła C# jako naprawdę groźny język programowania. Rów cie zajrzyjmy do kilku głównych funkcji w tej wersji:

- [Automatycznie implementowane właściwości](../programming-guide/classes-and-structs/auto-implemented-properties.md)
- [Typy anonimowe](../programming-guide/classes-and-structs/anonymous-types.md)
- [Wyrażenia kwerendy](../linq/query-expression-basics.md)
- [Wyrażenia lambda](../programming-guide/statements-expressions-operators/lambda-expressions.md)
- [Drzewa wyrażeń](../expression-trees.md)
- [Metody rozszerzenia](../programming-guide/classes-and-structs/extension-methods.md)
- [Niejawnie wpisane zmienne lokalne](../language-reference/keywords/var.md)
- [Metody częściowe](../language-reference/keywords/partial-method.md)
- [Inicjatory obiektów i kolekcji](../programming-guide/classes-and-structs/object-and-collection-initializers.md)

Z perspektywy czasu wiele z tych funkcji wydaje się zarówno nieuniknione, jak i nierozłączne. Wszystkie pasują do siebie strategicznie. Ogólnie uważa się, że funkcja zabójcy wersji C# była wyrażeniem zapytania, znanym również jako zapytanie zintegrowane z językiem (LINQ).

Widok bardziej zniuansowany analizuje drzewa wyrażeń, wyrażenia lambda i typy anonimowe jako fundament, na którym linq jest konstruowany. Ale w obu przypadkach C# 3.0 przedstawił rewolucyjną koncepcję. C# 3.0 zaczął kłaść podwaliny pod przekształcanie języka C# w hybrydowy język obiektowy / funkcjonalny.

W szczególności można teraz napisać w stylu SQL, kwerendy deklaratywne do wykonywania operacji w kolekcjach, między innymi. Zamiast pisać pętlę, `for` aby obliczyć średnią listy liczby całkowitej, można teraz `list.Average()`zrobić to tak po prostu, jak . Połączenie wyrażeń zapytań i metod rozszerzenia sprawiło, że wyglądało to tak, jakby ta lista liczby całkowitych stała się o wiele mądrzejsza.

Potrzeba było czasu, aby ludzie naprawdę zrozumieć i zintegrować koncepcję, ale stopniowo. A teraz, po latach, kod jest o wiele bardziej zwięzły, prosty i funkcjonalny.

## <a name="c-version-40"></a>C# wersja 4.0

C# wersja 4.0, wydany z Visual Studio 2010, miałby trudności z przeżywanie stanu przełomowy wersji 3.0. W wersji 3.0, C# przeniósł język mocno z cienia Java i do wyeksponowania. Język szybko stał się elegancki.

W następnej wersji wprowadzono kilka ciekawych nowych funkcji:

- [Wiązanie dynamiczne](../language-reference/builtin-types/reference-types.md)
- [Argumenty nazwane/opcjonalne](../programming-guide/classes-and-structs/named-and-optional-arguments.md)
- [Ogólny kowariant i kontrawariant](../../standard/generics/covariance-and-contravariance.md)
- [Osadzone typy międzyoperacyjne](../../framework/interop/type-equivalence-and-embedded-interop-types.md)

Osadzone typy międzypionowe złagodziły ból związany z wdrażaniem. Generyczna kowariancja i kontrawarancja dają więcej mocy do używania generycznych, ale są nieco akademickie i prawdopodobnie najbardziej cenione przez autorów frameworków i bibliotek. Nazwane i opcjonalne parametry pozwalają wyeliminować wiele przeciążeń metody i zapewnić wygodę. Ale żadna z tych funkcji nie zmienia dokładnie paradygmatu.

Główną cechą było `dynamic` wprowadzenie słowa kluczowego. Słowo `dynamic` kluczowe wprowadzone do wersji C# 4.0 możliwość zastąpienia kompilatora na wpisywanie w czasie kompilacji. Za pomocą dynamicznego słowa kluczowego można tworzyć konstrukcje podobne do dynamicznie wpisywanych języków, takich jak JavaScript. Można utworzyć, `dynamic x = "a string"` a następnie dodać sześć do niego, pozostawiając go do środowiska wykonawczego, aby uporządkować, co powinno się zdarzyć dalej.

Dynamiczne powiązanie daje możliwość błędów, ale także wielką moc w języku.

## <a name="c-version-50"></a>C# wersja 5.0

C# wersja 5.0, wydany z Visual Studio 2012, była skoncentrowana wersja języka. Prawie cały wysiłek dla tej wersji poszedł do `async` innej `await` przełomowej koncepcji językowej: i model programowania asynchronicznego.  Oto lista głównych funkcji:

- [Członkowie asynchroniczne](../async.md)
- [Atrybuty informacji o dzwoniącym](../programming-guide/concepts/caller-information.md)

### <a name="see-also"></a>Zobacz też

- [Projekt kodu: atrybuty informacji o wywołaniu w języku C# 5.0](https://www.codeproject.com/Tips/606379/Caller-Info-Attributes-in-Csharp)

Atrybut informacji o wywołującym umożliwia łatwe pobieranie informacji o kontekście, w którym jest uruchomiony bez uciekania się do tony kodu odbicia standardowego. Ma wiele zastosowań w diagnostyce i rejestrowaniu zadań.

Ale `async` `await` i są prawdziwe gwiazdy tego wydania. Kiedy te funkcje pojawiły się w 2012 roku, C# ponownie zmienił grę, piekąc asynchrony na język jako uczestnik pierwszej klasy. Jeśli kiedykolwiek zajmowałeś się długotrwałymi operacjami i implementacją sieci wywołań zwrotnych, prawdopodobnie pokochałeś tę funkcję językową.

## <a name="c-version-60"></a>C# wersja 6.0

W wersjach 3.0 i 5.0 c# dodał główne nowe funkcje w języku obiektowym. W wersji 6.0, wydany z Visual Studio 2015, to odejść od wykonywania dominującej funkcji zabójcy i zamiast zwolnić wiele mniejszych funkcji, które uczyniły programowania C# bardziej wydajne. Oto niektóre z nich:

- [Import statyczny](./csharp-6.md#using-static)
- [Filtry wyjątków](./csharp-6.md#exception-filters)
- [Inicjatory właściwości automatycznych](./csharp-6.md#auto-property-initializers)
- [Wyrazy zabudowane elementy członkowskie](./csharp-6.md#expression-bodied-function-members)
- [Propagator zerowy](./csharp-6.md#null-conditional-operators)
- [Interpolacja ciągów](./csharp-6.md#string-interpolation)
- [nameof, operator](./csharp-6.md#the-nameof-expression)
- [Inicjalizatory indeksu](csharp-6.md#extension-add-methods-in-collection-initializers)

Inne nowe funkcje obejmują:

- Czekaj w blokach catch/finally
- Wartości domyślne dla właściwości tylko dla gettera

Każda z tych funkcji jest interesująca sama w sobie. Ale jeśli spojrzycie na nie w ogóle, zobaczycie ciekawy wzór. W tej wersji języka C# wyeliminowane języka boilerplate, aby kod bardziej zwięzłe i czytelne. Więc dla fanów czystego, prostego kodu, ta wersja językowa była ogromną wygraną.

Zrobili jeszcze jedną rzecz wraz z tą wersją, choć nie jest to tradycyjna funkcja językowa sama w sobie. Wydali [Roslyn kompilator jako usługa](https://github.com/dotnet/roslyn). Kompilator języka C# jest teraz napisany w języku C#i można użyć kompilatora jako część wysiłków programowania.

## <a name="c-version-70"></a>C# wersja 7.0

C# wersja 7.0 został wydany z Visual Studio 2017. Ta wersja ma pewne ewolucyjne i fajne rzeczy w duchu C# 6.0, ale bez kompilatora jako usługi. Oto niektóre z nowych funkcji:

- [Zmienne out](./csharp-7.md#out-variables)
- [Krotek i dekonstrukcji](./csharp-7.md#tuples)
- [Dopasowywanie wzoru](./csharp-7.md#pattern-matching)
- [Funkcje lokalne](./csharp-7.md#local-functions)
- [Rozwinięte wyrazy zabudowane elementy członkowskie](./csharp-7.md#more-expression-bodied-members)
- [Ref mieszkańców i zwraca](./csharp-7.md#ref-locals-and-returns)

Inne funkcje obejmują:

- [Odrzucenia](./csharp-7.md#discards)
- [Literały binarne i separatory cyfr](./csharp-7.md#numeric-literal-syntax-improvements)
- [Wyrażenia throw](./csharp-7.md#throw-expressions)

Wszystkie te funkcje oferują fajne nowe możliwości dla programistów i możliwość pisania jeszcze czystszego kodu niż kiedykolwiek. Podświetlenie jest kondensowanie deklaracji zmiennych do użycia ze `out` słowem kluczowym i zezwalając na wiele zwracanych wartości za pośrednictwem krotki.

Ale C# jest wprowadzane do coraz szerszego wykorzystania. .NET Core jest teraz przeznaczony dla każdego systemu operacyjnego i ma oczy mocno na chmurze i na przenośność.  Te nowe możliwości z pewnością zajmują myśli i czas projektantów języka, oprócz wymyślania nowych funkcji.

## <a name="c-version-71"></a>C# wersja 7.1

C# rozpoczął zwalnianie *wydania punktu* z C# 7.1. Ta wersja dodała element konfiguracji [wyboru wersji języka,](../language-reference/configure-language-version.md) trzy nowe funkcje języka i nowe zachowanie kompilatora.

Nowe funkcje językowe w tej wersji to:

- [`async``Main` metoda](./csharp-7-1.md#async-main)
  - Punkt wejścia dla aplikacji może `async` mieć modyfikator.
- [`default`wyrażenia dosłowne](./csharp-7-1.md#default-literal-expressions)
  - Domyślnych wyrażeń literału można używać w wyrażeniach wartości domyślnej, gdy można wywnioskować typ docelowy.
- [Wywnioskowane nazwy elementów krotki](./csharp-7-1.md#inferred-tuple-element-names)
  - Nazwy elementów krotki można wywnioskować z inicjowania krotki w wielu przypadkach.
- [Dopasowywanie wzorca w parametrach typu ogólnego](./csharp-7-1.md#pattern-matching-on-generic-type-parameters)
  - Można użyć wyrażeń dopasowania wzorca dla zmiennych, których typ jest parametrem typu ogólnego.

Na koniec kompilator ma `-refout` `-refonly` dwie opcje i [tego generowania zestawu odwołania](./csharp-7-1.md#reference-assembly-generation)kontroli .

## <a name="c-version-72"></a>C# wersja 7.2

W języku C# 7.2 dodano kilka małych funkcji językowych:

- [Techniki pisania bezpiecznego wydajnego kodu](./csharp-7-2.md#safe-efficient-code-enhancements)
  - Kombinacja ulepszeń składni, które umożliwiają pracę z typami wartości przy użyciu semantyki odwołań.
- [Argumenty nazwane inne niż końcowe](./csharp-7-2.md#non-trailing-named-arguments)
  - Nazwane argumenty mogą być następują po argumentach pozycyjnych.
- [Podkreślenia wiodące w literałach liczbowych](./csharp-7-2.md#leading-underscores-in-numeric-literals)
  - Literały liczbowe mogą teraz mieć wiodące podkreślenia przed wydrukowanymi cyframi.
- [`private protected`modyfikator dostępu](./csharp-7-2.md#private-protected-access-modifier)
  - Modyfikator `private protected` dostępu umożliwia dostęp dla klas pochodnych w tym samym zestawie.
- [Wyrażenia `ref` warunkowe](./csharp-7-2.md#conditional-ref-expressions)
  - Wynikiem wyrażenia warunkowego (`?:`) może być teraz odwołanie.

## <a name="c-version-73"></a>C# wersja 7.3

Istnieją dwa główne motywy do wersji C# 7.3. Jeden motyw zawiera funkcje, które umożliwiają bezpieczny kod, aby być równie wydajny jak niebezpieczny kod. Drugi motyw zawiera przyrostowe ulepszenia istniejących funkcji. Ponadto w tej wersji dodano nowe opcje kompilatora.

Następujące nowe funkcje obsługują temat lepszej wydajności dla bezpiecznego kodu:

- [Dostęp do stałych pól można uzyskać bez przypinania.](csharp-7-3.md#indexing-fixed-fields-does-not-require-pinning)
- [Można ponownie przypisać `ref` zmienne lokalne.](csharp-7-3.md#ref-local-variables-may-be-reassigned)
- [Inicjatorów można używać `stackalloc` w tablicach.](csharp-7-3.md#stackalloc-arrays-support-initializers)
- [Można użyć `fixed` instrukcji z dowolnego typu, który obsługuje wzorzec.](csharp-7-3.md#more-types-support-the-fixed-statement)
- [Można użyć dodatkowych ograniczeń ogólnych.](csharp-7-3.md#enhanced-generic-constraints)

Wprowadzono następujące ulepszenia istniejących funkcji:

- [Można `==` przetestować `!=` i z typów krotki.](csharp-7-3.md#tuples-support--and-)
- [Zmiennych wyrażenia można używać w większej liczbie lokalizacji.](csharp-7-3.md#extend-expression-variables-in-initializers)
- [Atrybuty można dołączyć do pola zapasowego właściwości automatycznie zaimplementowanych.](csharp-7-3.md#attach-attributes-to-the-backing-fields-for-auto-implemented-properties)
- [Poprawiono rozpoznawanie `in` metody, gdy argumenty różnią się w zależności od tego.](csharp-7-3.md#in-method-overload-resolution-tiebreaker)
- [Rozdzielczość przeciążenia ma teraz mniej niejednoznacznych przypadków.](csharp-7-3.md#improved-overload-candidates)

Nowe opcje kompilatora to:

- [`-publicsign`, aby włączyć podpisywanie zestawów oprogramowaniem open source (OSS).](csharp-7-3.md#public-or-open-source-signing)
- [`-pathmap`, aby zapewnić mapowanie katalogów źródłowych.](csharp-7-3.md#pathmap)

## <a name="c-version-80"></a>C# wersja 8.0

C# 8.0 jest pierwszą główną wersją języka C#, która w szczególności jest przeznaczona dla .NET Core. Niektóre funkcje opierają się na nowych możliwościach CLR, inne na typach bibliotek dodawanych tylko w programie .NET Core. C# 8.0 dodaje następujące funkcje i ulepszenia do języka C#:

- [Czytaj tylko członków](./csharp-8.md#readonly-members)
- [Domyślne metody interfejsu](./csharp-8.md#default-interface-methods)
- [Ulepszenia dopasowywania wzorców:](./csharp-8.md#more-patterns-in-more-places)
  - [Przełączanie wyrażeń](./csharp-8.md#switch-expressions)
  - [Wzorce właściwości](./csharp-8.md#property-patterns)
  - [Wzory krotki](./csharp-8.md#tuple-patterns)
  - [Wzory pozycyjne](./csharp-8.md#positional-patterns)
- [Używanie deklaracji](./csharp-8.md#using-declarations)
- [Statyczne funkcje lokalne](./csharp-8.md#static-local-functions)
- [Jednorazowe struktury ref](./csharp-8.md#disposable-ref-structs)
- [Typy referencyjne dopuszczające wartość null](../language-reference/builtin-types/nullable-reference-types.md)
- [Strumienie asynchroniczne](./csharp-8.md#asynchronous-streams)
- [Indeksy i zakresy](./csharp-8.md#indices-and-ranges)
- [Przypisanie scalania wartości null](./csharp-8.md#null-coalescing-assignment)
- [Niezarządzane typy skonstruowane](./csharp-8.md#unmanaged-constructed-types)
- [Stackalloc w wyrażeniach zagnieżdżonych](./csharp-8.md#stackalloc-in-nested-expressions)
- [Wzmocnienie interpolowanych ciągów dosłownie](./csharp-8.md#enhancement-of-interpolated-verbatim-strings)

Domyślne elementy członkowskie interfejsu wymagają ulepszeń w programie CLR. Te funkcje zostały dodane w programie CLR dla platformy .NET Core 3.0. Zakresy i indeksy oraz strumienie asynchroniczne wymagają nowych typów w bibliotekach .NET Core 3.0. Nullable typy odwołań, podczas gdy zaimplementowane w kompilatorze, jest znacznie bardziej przydatne, gdy biblioteki są adnotacjami, aby zapewnić informacje semantyczne dotyczące stanu null argumentów i zwraca wartości. Te adnotacje są dodawane w bibliotekach .NET Core.

_Artykuł_ [_pierwotnie opublikowane na blogu NDepend_](https://blog.ndepend.com/c-versions-look-language-history/), dzięki uprzejmości Erik_Dietrich i Patrick Smacchia._

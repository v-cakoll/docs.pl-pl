---
title: Historia języka C# — Przewodnik po językach C#
description: Jak wyglądał język w jego najwcześniejszych wersjach i jak ewoluował od tego czasu?
author: erikdietrich
ms.date: 09/20/2017
ms.openlocfilehash: 9114395a5c6cfd8df5da18024921c35828947e0b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399687"
---
# <a name="the-history-of-c"></a>Historia C\#

Ten artykuł zawiera historię każdej głównej wersji języka Języka C#. Zespół Języka C# kontynuuje wprowadzanie innowacji i dodawanie nowych funkcji. Szczegółowy stan funkcji języka, w tym funkcje uwzględniane w nadchodzących wersjach, można znaleźć [w repozytorium dotnet/roslyn](https://github.com/dotnet/roslyn/blob/master/docs/Language%20Feature%20Status.md) w githubie.

> [!IMPORTANT]
> Język C# opiera się na typy i metody w co specyfikacja Języka C# definiuje jako *standardowebiblioteki* dla niektórych funkcji. Platforma .NET dostarcza te typy i metody w wielu pakietach. Jednym z przykładów jest przetwarzanie wyjątków. Każda `throw` instrukcja lub wyrażenie jest zaznaczone, aby <xref:System.Exception>upewnić się, że obiekt jest generowany pochodzi od . Podobnie każdy `catch` jest sprawdzany w celu upewnienia się, <xref:System.Exception>że typ złowionych pochodzi z . Każda wersja może dodać nowe wymagania. Aby korzystać z najnowszych funkcji języka w starszych środowiskach, może być konieczne zainstalowanie określonych bibliotek. Te zależności są udokumentowane na stronie dla każdej określonej wersji. Możesz dowiedzieć się więcej o [relacjach między językiem a biblioteką](relationships-between-language-and-library.md) w tle tej zależności.

Narzędzia kompilacji języka C# należy wziąć pod uwagę najnowszą wersję języka głównego domyślną wersję językową. Między głównymi wersjami mogą występować wersje punktowe, wyszczególnione w innych artykułach w tej sekcji. Aby korzystać z najnowszych funkcji w wersji punktowej, należy [skonfigurować wersję języka kompilatora](../language-reference/configure-language-version.md) i wybrać wersję. Od języka C# 7.0 wprowadzono trzy wydania punktowe:

- [C# 7.3](csharp-7-3.md):
  - C# 7.3 jest dostępny począwszy od [programu Visual Studio 2017 w wersji 15.7](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) i [.NET Core 2.1 SDK](../../core/whats-new/dotnet-core-2-1.md).
- [C# 7.2](csharp-7-2.md):
  - C# 7.2 jest dostępny począwszy od [programu Visual Studio 2017 w wersji 15.5](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) i [.NET Core 2.0 SDK](../../core/whats-new/dotnet-core-2-0.md).
- [C# 7.1](csharp-7-1.md):
  - C# 7.1 jest dostępny począwszy od [programu Visual Studio 2017 w wersji 15.3](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) i [.NET Core 2.0 SDK](../../core/whats-new/dotnet-core-2-0.md).

## <a name="c-version-10"></a>C# w wersji 1.0

Gdy wrócisz i spojrzeć, C# w wersji 1.0, wydany z Visual Studio .NET 2002, wyglądał podobnie jak Java. W [ramach swoich celów projektowych dla ECMA](https://feeldotneteasy.blogspot.com/2011/01/c-design-goals.html), starał się być "prosty, nowoczesny, ogólnego przeznaczenia języka obiektowego."  W tym czasie, wyglądając jak Java oznaczało to, że osiągnąć te wczesne cele projektowe.

Ale jeśli spojrzysz wstecz na C # 1.0 teraz, można znaleźć się trochę zawroty. Brakowało wbudowanych możliwości asynchronicznych i niektórych funkcji zręcznych wokół leków generycznych, które bierzesz za pewnik. W rzeczywistości, brakowało leków generycznych w ogóle.  I [LINQ](../linq/index.md)? Nie dostępne jeszcze. Te dodatki zajęłoby kilka lat, aby wyjść.

C# wersja 1.0 spojrzał pozbawiony funkcji, w porównaniu do dzisiaj. Można znaleźć się na piśmie jakiś pełny kod. Ale jednak musisz zacząć gdzieś. C# w wersji 1.0 był realną alternatywą dla Java na platformie Windows.

Główne cechy Języka C# 1.0 obejmowały:

- [Klasy](../programming-guide/classes-and-structs/classes.md)
- [Struktury](../language-reference/builtin-types/struct.md)
- [Interfejsy](../programming-guide/interfaces/index.md)
- [Zdarzenia](../events-overview.md)
- [Właściwości](../properties.md)
- [Delegaty](../delegates-overview.md)
- [Wyrażenia](../programming-guide/statements-expressions-operators/expressions.md)
- [Instrukcje](../programming-guide/statements-expressions-operators/statements.md)
- [Atrybuty](../programming-guide/concepts/attributes/index.md)

## <a name="c-version-12"></a>C# w wersji 1.2

C# w wersji 1.2 dostarczane z programu Visual Studio .NET 2003. Zawierał kilka drobnych ulepszeń języka. Najbardziej godne uwagi jest to, że począwszy `foreach` od <xref:System.IDisposable.Dispose%2A> tej <xref:System.Collections.IEnumerator> wersji, kod wygenerowany w pętli o nazwie, gdy, że <xref:System.Collections.IEnumerator> zaimplementowane <xref:System.IDisposable>.

## <a name="c-version-20"></a>C# w wersji 2.0

Teraz sprawy zaczynają się interesować. Przyjrzyjmy się niektórym głównym funkcjom języka C# 2.0, wydanemu w 2005 roku, wraz z programiem Visual Studio 2005:

- [Typy ogólne](../programming-guide/generics/index.md)
- [Typy częściowe](../programming-guide/classes-and-structs/partial-classes-and-methods.md#partial-classes)
- [Metody anonimowe](../language-reference/operators/delegate-operator.md)
- [Typy wartości z możliwością null](../language-reference/builtin-types/nullable-value-types.md)
- [Iteratory](../programming-guide/concepts/iterators.md)
- [Kowariancja i kontrawariancja](../programming-guide/concepts/covariance-contravariance/index.md)

Inne funkcje języka C# 2.0 dodano możliwości do istniejących funkcji:

- Getter/setter oddzielna dostępność
- Konwersje grupy metod (pełnomocnicy)
- Klasy statyczne
- Wnioskowanie o delegowaniu

Podczas gdy C# może zostały uruchomione jako ogólny język zorientowanych obiektowo (OO), C# w wersji 2.0 zmienił, że w pośpiechu. Gdy mieli nogi pod nimi, poszli po kilka poważnych punktów bólu dewelopera. I poszli za nimi w znaczący sposób.

Z generycznych typów i metod może działać na dowolny typ przy zachowaniu bezpieczeństwa typów. Na przykład o <xref:System.Collections.Generic.List%601> pozwala `List<string>` mieć `List<int>` lub wykonywać operacje bezpieczne dla typu na tych ciągów lub liczb całkowitych podczas itetencji za ich pośrednictwem. Za pomocą typów ogólnych jest lepszy niż tworzenie, `ListInt` które pochodzi od `ArrayList` lub rzutowania z `Object` dla każdej operacji.

C# wersja 2.0 przyniósł iteratory. Mówiąc zwięźle, iteratory umożliwiają zbadanie wszystkich elementów w `List` (lub innych typach wyliczalnych) za pomocą `foreach` pętli. O iteratory jako pierwszej klasy część języka znacznie zwiększona czytelność języka i zdolność ludzi do rozumu o kodzie.

A jednak, C# nadal grać trochę nadrabiania zaległości z Java. Java wydała już wersje, które zawierały generyki i iteratory. Ale to się wkrótce zmieni, gdy języki nadal ewoluowały.

## <a name="c-version-30"></a>C# w wersji 3.0

C# wersja 3.0 przyszedł pod koniec 2007 r., wraz z Visual Studio 2008, choć pełna łódź funkcji językowych będzie rzeczywiście pochodzić z .NET Framework w wersji 3.5. Ta wersja oznaczała poważną zmianę w rozwoju języka C#. Ustanowiono C# jako naprawdę groźny język programowania. Przyjrzyjmy się kilku głównym funkcjom w tej wersji:

- [Właściwości implementowane automatycznie](../programming-guide/classes-and-structs/auto-implemented-properties.md)
- [Typy anonimowe](../programming-guide/classes-and-structs/anonymous-types.md)
- [Wyrażenia kwerendy](../linq/query-expression-basics.md)
- [Wyrażenia lambda](../programming-guide/statements-expressions-operators/lambda-expressions.md)
- [Drzewa wyrażeń](../expression-trees.md)
- [Metody rozszerzenia](../programming-guide/classes-and-structs/extension-methods.md)
- [Niejawnie wpisane zmienne lokalne](../language-reference/keywords/var.md)
- [Metody częściowe](../language-reference/keywords/partial-method.md)
- [Inicjatory obiektów i kolekcji](../programming-guide/classes-and-structs/object-and-collection-initializers.md)

Z perspektywy czasu wiele z tych cech wydaje się zarówno nieuniknione, jak i nierozłączne. Wszystkie pasują do siebie strategicznie. Ogólnie uważa się, że funkcja zabójcza wersji C# była wyrażeniem zapytania, znanym również jako zapytanie zintegrowane z językiem (LINQ).

Bardziej zniuansowany widok sprawdza drzewa wyrażeń, wyrażenia lambda i typy anonimowe jako podstawę, na której jest konstruowany LINQ. Ale w obu przypadkach C# 3.0 przedstawił rewolucyjną koncepcję. C# 3.0 zaczął położyć podwaliny dla przekształcania Języka C# w hybrydowy język obiektowy / funkcjonalny.

W szczególności można teraz napisać SQL stylu, deklaratywne zapytania do wykonywania operacji na kolekcje, między innymi. Zamiast pisać `for` pętlę do obliczania średniej listy liczb całkowitych, można to zrobić `list.Average()`tak prosto, jak . Kombinacja wyrażeń zapytań i metod rozszerzenia sprawiła, że wyglądało to tak, jakby ta lista liczb całkowitych stała się o wiele inteligentniejsza.

Potrzeba było czasu, aby ludzie naprawdę zrozumieli i zintegrowali tę koncepcję, ale stopniowo to robili. A teraz, po latach, kod jest znacznie bardziej zwięzły, prosty i funkcjonalny.

## <a name="c-version-40"></a>C# w wersji 4.0

C# wersja 4.0, wydany z Visual Studio 2010, miałby trudny czas życia do przełomowego stanu wersji 3.0. W wersji 3.0, C# przeniósł język mocno z cienia Java i do wyeksponowania. Język szybko stał się elegancki.

Kolejna wersja wprowadziła kilka ciekawych nowych funkcji:

- [Wiązanie dynamiczne](../language-reference/builtin-types/reference-types.md)
- [Argumenty nazwane/opcjonalne](../programming-guide/classes-and-structs/named-and-optional-arguments.md)
- [Ogólny kowariant i kontrawariant](../../standard/generics/covariance-and-contravariance.md)
- [Wbudowane typy współoperacji](../../framework/interop/type-equivalence-and-embedded-interop-types.md)

Wbudowane typy interop złagodziły ból wdrożenia. Ogólne kowariancja i kontrawariancja dają więcej mocy do używania leków generycznych, ale są one nieco akademickie i prawdopodobnie najbardziej cenione przez autorów ram i bibliotek. Nazwane i opcjonalne parametry pozwalają wyeliminować wiele przeciążeń metody i zapewnić wygodę. Ale żadna z tych funkcji nie zmienia dokładnie paradygmatu.

Główną cechą było wprowadzenie `dynamic` słowa kluczowego. Słowo `dynamic` kluczowe wprowadzone do c# w wersji 4.0 możliwość zastąpienia kompilatora na typowanie w czasie kompilacji. Za pomocą dynamicznego słowa kluczowego można tworzyć konstrukcje podobne do dynamicznie wpisywanych języków, takich jak JavaScript. Można utworzyć, `dynamic x = "a string"` a następnie dodać sześć do niego, pozostawiając go do czasu wykonywania, aby uporządkować, co powinno się zdarzyć dalej.

Dynamiczne powiązanie daje możliwość błędów, ale także dużą moc w języku.

## <a name="c-version-50"></a>C# w wersji 5.0

C# wersja 5.0, wydana w programie Visual Studio 2012, była skupiona wersja języka. Prawie cały wysiłek dla tej wersji poszedł do innego `async` `await` przełomowego pojęcia języka: i model programowania asynchronicznego.  Oto lista głównych funkcji:

- [Członkowie asynchroniczne](../async.md)
- [Atrybuty informacji o obiekcie wywołującym](../programming-guide/concepts/caller-information.md)

### <a name="see-also"></a>Zobacz też

- [Projekt kodu: Atrybuty informacji o obiekcie wywołującym w języku C# 5.0](https://www.codeproject.com/Tips/606379/Caller-Info-Attributes-in-Csharp)

Atrybut informacji o obiekcie wywołującym umożliwia łatwe pobieranie informacji o kontekście, w którym pracujesz bez uciekania się do tony standardowego kodu odbicia. Ma wiele zastosowań w diagnostyce i rejestrowania zadań.

Ale `async` `await` i są prawdziwymi gwiazdami tego wydania. Kiedy te funkcje pojawiły się w 2012, C# ponownie zmienił grę, upieczając asynchrony w języku jako uczestnik pierwszej klasy. Jeśli kiedykolwiek zajmowałeś się długotrwałymi operacjami i implementacją sieci wywołań wywołań odgłosowych, prawdopodobnie pokochałeś tę funkcję języka.

## <a name="c-version-60"></a>C# w wersji 6.0

W wersjach 3.0 i 5.0 c# dodał główne nowe funkcje w języku obiektowym. W wersji 6.0, wydanej w programie Visual Studio 2015, odejdą od wykonywania dominującej funkcji zabójcy i zamiast tego wydać wiele mniejszych funkcji, które sprawiły, że programowanie C# stało się bardziej produktywne. Oto niektóre z nich:

- [Import statyczny](./csharp-6.md#using-static)
- [Filtry wyjątków](./csharp-6.md#exception-filters)
- [Inicjatory właściwości automatycznych](./csharp-6.md#auto-property-initializers)
- [Wyrażenie zabudowanych członków](./csharp-6.md#expression-bodied-function-members)
- [Propagator zerowy](./csharp-6.md#null-conditional-operators)
- [Interpolacja ciągów](./csharp-6.md#string-interpolation)
- [nameof, operator](./csharp-6.md#the-nameof-expression)
- [Inicjatory indeksu](csharp-6.md#extension-add-methods-in-collection-initializers)

Inne nowe funkcje obejmują:

- Czekaj w blokach catch/finally
- Wartości domyślne dla właściwości tylko do gettera

Każda z tych funkcji jest interesująca sama w sobie. Ale jeśli spojrzycie na nie w ogóle, zobaczycie ciekawy wzór. W tej wersji C# wyeliminowane języka standardowego, aby kod bardziej zwięzłe i czytelne. Więc dla fanów czystego, prostego kodu, ta wersja językowa była ogromną wygraną.

Zrobili jeszcze jedną rzecz wraz z tą wersją, choć nie jest to tradycyjna funkcja językowa sama w sobie. Wydali [Roslyn kompilator jako usługę](https://github.com/dotnet/roslyn). Kompilator Języka C# jest teraz napisany w języku C#i można użyć kompilatora jako część wysiłków programowania.

## <a name="c-version-70"></a>C# w wersji 7.0

Najnowsza wersja główna to C# wersja 7.0, wydana w programie Visual Studio 2017. Ta wersja ma pewne ewolucyjne i fajne rzeczy w duchu C# 6.0, ale bez kompilatora jako usługi. Oto niektóre z nowych funkcji:

- [Zmienne out](./csharp-7.md#out-variables)
- [Krotek i dekonstrukcji](./csharp-7.md#tuples)
- [Dopasowanie do wzorca](./csharp-7.md#pattern-matching)
- [Funkcje lokalne](./csharp-7.md#local-functions)
- [Rozszerzone elementy członkowskie zabudowane wyrażeniem](./csharp-7.md#more-expression-bodied-members)
- [Ref mieszkańców i zwraca](./csharp-7.md#ref-locals-and-returns)

Inne funkcje obejmowały:

- [Odrzucenia](./csharp-7.md#discards)
- [Literały binarne i separatory cyfr](./csharp-7.md#numeric-literal-syntax-improvements)
- [Wyrażenia throw](./csharp-7.md#throw-expressions)

Wszystkie te funkcje oferują fajne nowe możliwości dla programistów i możliwość napisania jeszcze czystszego kodu niż kiedykolwiek. Wyróżnienie jest skraplania deklaracji `out` zmiennych do użycia ze słowem kluczowym i poprzez umożliwienie wielu zwracanych wartości za pośrednictwem krotki.

Ale C# jest wprowadzane do coraz szerszego użytku. .NET Core jest teraz przeznaczony dla każdego systemu operacyjnego i ma oczy mocno na chmurze i przenośności.  Te nowe możliwości z pewnością zajmują myśli i czas projektantów języka, oprócz wymyślania nowych funkcji.

_Artykuł_ [_pierwotnie opublikowany na blogu NDepend,_](https://blog.ndepend.com/c-versions-look-language-history/)dzięki uprzejmości Erik_Dietrich i Patrick Smacchia._

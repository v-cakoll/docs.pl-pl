---
title: Typy krotek — C# Przewodnik
description: Dowiedz się więcej na temat typów krotek bez nazwy i nazwanych wC#
ms.date: 05/15/2018
ms.technology: csharp-fundamentals
ms.assetid: ee8bf7c3-aa3e-4c9e-a5c6-e05cc6138baa
ms.openlocfilehash: f551a1df4a31c3311119a0327e02fbc6096ce0a0
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039722"
---
# <a name="c-tuple-types"></a>C#typy krotek

C#krotki są typami definiowanymi przy użyciu uproszczonej składni. Zalety obejmują prostsze składnię, reguły konwersji na podstawie liczby (nazywanej kardynalnością) i typów elementów oraz spójnych reguł dla kopii, testów równości i przypisań. Ze kompromisem, krotki nie obsługują niektórych idiomy zorientowanych obiektowo skojarzonych z dziedziczeniem. Możesz zapoznać się z omówieniem w sekcji dotyczącej [krotek w artykule Co nowego C# w 7,0](whats-new/csharp-7.md#tuples) artykułu.

W tym artykule poznasz reguły języka dotyczące krotek w C# 7,0 i nowszych wersjach, różne sposoby ich używania oraz wstępne wskazówki dotyczące pracy z krotkami.

> [!NOTE]
> Nowe funkcje krotek wymagają typów <xref:System.ValueTuple>.
> Należy dodać pakiet NuGet [`System.ValueTuple`](https://www.nuget.org/packages/System.ValueTuple/) , aby można go było używać na platformach, które nie zawierają typów.
>
> Jest to podobne do innych funkcji języka, które opierają się na typach dostarczonych w środowisku. Przykłady obejmują `async` i `await` polegające na interfejsie `INotifyCompletion` i LINQ polegające na `IEnumerable<T>`. Jednak mechanizm dostarczania jest zmieniany, ponieważ platforma .NET staje się coraz niezależna od platformy. .NET Framework może nie zawsze dostarczać na tym samym erze co kompilator języka. Gdy nowe funkcje językowe korzystają z nowych typów, te typy będą dostępne jako pakiety NuGet, gdy funkcje języka są dostarczane. Po dodaniu nowych typów do interfejsu API .NET Standard i dostarczeniu ich jako części platformy zostanie usunięte wymaganie pakietu NuGet.

Zacznijmy od powodów dodawania nowej obsługi spójnej kolekcji. Metody zwracają pojedynczy obiekt. Krotki umożliwiają łatwiejsze pakowanie wielu wartości w tym pojedynczym obiekcie.

.NET Framework ma już ogólne klasy `Tuple`. Jednak te klasy miały dwa zasadnicze ograniczenia. Dla jednej z nich klasy `Tuple` o nazwie ich właściwości `Item1`, `Item2` itd. Te nazwy nie zawierają informacji semantycznych. Korzystanie z tych typów `Tuple` nie umożliwia komunikowania znaczenia każdej właściwości. Nowe funkcje języka umożliwiają deklarowanie i używanie semantycznie zrozumiałych nazw dla elementów w spójnej kolekcji.

Klasy `Tuple` powodują zwiększenie wydajności, ponieważ są to typy odwołań. Użycie jednego z typów `Tuple` oznacza alokowanie obiektów. W przypadku ścieżek aktywnych alokowanie wielu małych obiektów może mieć wymierny wpływ na wydajność aplikacji. W związku z tym, obsługa języków w przypadku krotek wykorzystuje nowe struktury `ValueTuple`.

Aby uniknąć tych uchybień, można utworzyć `class` lub `struct`, aby przenieść wiele elementów. Niestety, to jeszcze więcej pracy i zasłania zamiar projektowania. Zastosowanie `struct` lub `class` oznacza, że definiujesz typ z danymi i zachowaniem. Wiele razy, Wystarczy przechowywać wiele wartości w pojedynczym obiekcie.

Funkcje języka i struktury ogólne `ValueTuple` wymuszają zasady, że nie można dodać żadnego zachowania (metod) do tych typów krotek.
Wszystkie typy `ValueTuple` to *modyfikowalne struktury*. Każde pole elementu członkowskiego jest polem publicznym. Dzięki temu są one bardzo lekkie. Jednak oznacza to, że nie należy używać krotek, gdzie niezmienności jest ważne.

Krotki są prostsze i bardziej elastyczne kontenery danych niż typy `class` i `struct`. Zapoznaj się z tymi różnicami.

## <a name="named-and-unnamed-tuples"></a>Krotki nazwane i nienazwane

Struktura `ValueTuple` zawiera pola o nazwie `Item1`, `Item2`, `Item3` i tak dalej, podobnie jak właściwości zdefiniowane w istniejących typach `Tuple`.
Te nazwy są jedynymi nazwami, których można używać w przypadku *krotek nienazwanych*. Jeśli nie podasz żadnych alternatywnych nazw pól dla krotki, utworzona zostanie nienazwana krotka:

[!code-csharp[UnnamedTuple](../../samples/snippets/csharp/tuples/program.cs#01_UnNamedTuple "Unnamed tuple")]

Krotka w poprzednim przykładzie została zainicjowana przy użyciu stałych literałów i nie będzie miała nazw elementów utworzonych przy użyciu *prognoz nazw pól krotek* w C# 7,1.

Jednak po zainicjowaniu krotki można użyć nowych funkcji języka, które zapewniają lepsze nazwy dla każdego pola. Spowoduje to utworzenie *nazwanej krotki*.
Nazwane krotki nadal mają elementy o nazwie `Item1`, `Item2`, `Item3` i tak dalej.
Ale mają także synonimy dla dowolnego z tych elementów, które mają nazwę.
Tworzysz nazwaną krotek przez określenie nazw dla każdego elementu. Jednym ze sposobów jest określenie nazw jako części inicjowania krotki:

[!code-csharp[NamedTuple](../../samples/snippets/csharp/tuples/program.cs#02_NamedTuple "Named tuple")]

Te synonimy są obsługiwane przez kompilator i język, dzięki czemu można efektywnie używać nazwanych krotek. Środowisk IDE i redaktorzy mogą odczytywać te nazwy semantyczne przy użyciu interfejsów API Roslyn. Można odwoływać się do elementów nazwanych krotek według tych nazw semantycznych w dowolnym miejscu w tym samym zestawie. Kompilator zastępuje nazwy zdefiniowane przy użyciu odpowiedników `Item*` podczas generowania skompilowanych danych wyjściowych. Skompilowany język pośredni firmy Microsoft (MSIL) nie zawiera nazw, które zostały podane przez Ciebie.

Począwszy od C# 7,1, nazwy pól dla krotki mogą być dostarczone ze zmiennych używanych do inicjowania krotki. Jest to nazywane **[inicjatorami projekcji krotki](#tuple-projection-initializers)** . Poniższy kod tworzy krotkę o nazwie `accumulation` z elementami `count` (Integer) i `sum` (Double).

[!code-csharp[ProjectedTuple](../../samples/snippets/csharp/tuples/program.cs#ProjectedTupleNames "Named tuple")]

Kompilator musi komunikować te nazwy, które zostały utworzone dla krotek, które są zwracane z metod publicznych lub właściwości. W takich przypadkach kompilator dodaje atrybut <xref:System.Runtime.CompilerServices.TupleElementNamesAttribute> w metodzie. Ten atrybut zawiera właściwość listy <xref:System.Runtime.CompilerServices.TupleElementNamesAttribute.TransformNames> zawierającą nazwy nadawane każdemu z elementów w spójnej kolekcji.

> [!NOTE]
> Narzędzia programistyczne, takie jak Visual Studio, odczytują również te metadane i udostępniają funkcję IntelliSense i inne funkcje przy użyciu nazw pól metadanych.

Ważne jest, aby zrozumieć te podstawowe podstawy nowych krotek i typ `ValueTuple`, aby zrozumieć reguły przypisywania nazwanych spójnych krotek.

## <a name="tuple-projection-initializers"></a>Inicjatory projekcji krotki

Ogólnie rzecz biorąc, inicjatory projekcji krotki działają przy użyciu nazw zmiennych lub pól z prawej strony instrukcji inicjowania krotki.
Jeśli podano jawną nazwę, która ma pierwszeństwo przed nazwą przewidywaną. Na przykład w poniższym inicjatorze elementy są `explicitFieldOne` i `explicitFieldTwo`, a nie `localVariableOne` i `localVariableTwo`:

[!code-csharp[ExplicitNamedTuple](../../samples/snippets/csharp/tuples/program.cs#ProjectionExample_Explicit "Explicitly named tuple")]

Dla każdego pola, w którym nie podano jawnej nazwy, odpowiednia nazwa niejawna jest rzutowana. Nie istnieje wymóg udostępniania nazw semantycznych jawnie lub niejawnie. Następujący inicjator ma nazwy pól `Item1`, których wartość jest `42` i `stringContent`, której wartością jest "odpowiedź na wszystko":

[!code-csharp[MixedTuple](../../samples/snippets/csharp/tuples/program.cs#MixedTuple "mixed tuple")]

Istnieją dwa warunki, w których nazwy pól kandydatów nie są rzutowane na pole krotki:

1. Nazwa kandydata jest zastrzeżoną nazwą krotki. Przykłady obejmują `Item3`, `ToString` lub `Rest`.
1. Nazwa kandydata jest duplikatem innej nazwy pola krotki, jawnej lub niejawnej.

Te warunki nie zezwalają na niejednoznaczność. Te nazwy spowodują niejednoznaczność, jeśli były używane jako nazwy pól dla pola w spójnej kolekcji. Żaden z tych warunków nie powoduje błędów w czasie kompilacji. Zamiast tego elementy bez przewidywanych nazw nie mają dla nich nazw semantycznych.  Poniższe przykłady przedstawiają następujące warunki:

[!code-csharp-interactive[Ambiguity](../../samples/snippets/csharp/tuples/program.cs#ProjectionAmbiguities "tuples where projections are not performed")]

Te sytuacje nie powodują błędów kompilatora, ponieważ mogą to być istotne zmiany w kodzie zapisanym C# w 7,0, gdy projekcje nazw pól krotek nie są dostępne.

## <a name="equality-and-tuples"></a>Równość i krotki

Począwszy od C# 7,3, typy krotek obsługują operatory `==` i `!=`. Te operatory działają przez porównanie poszczególnych elementów członkowskich argumentu po lewej stronie z każdym elementem członkowskim argumentu w odpowiedniej kolejności. Te porównania są skracane. Przestaną oceniać członków, gdy tylko jedna para nie jest równa. Poniższe przykłady kodu używają `==`, ale reguły porównania mają zastosowanie do `!=`. Poniższy przykład kodu pokazuje porównanie równości dla dwóch par liczb całkowitych:

[!code-csharp-interactive[TupleEquality](../../samples/snippets/csharp/tuples/program.cs#Equality "Testing tuples for equality")]

Istnieje kilka reguł, dzięki którym testy równości spójnej kolekcji są wygodniejsze. Równość krotki wykonuje [przekształcenia zniesione](~/_csharplang/spec/conversions.md#lifted-conversion-operators) , jeśli jedna z krotek jest krotką dopuszczającą wartość null, jak pokazano w poniższym kodzie:

[!code-csharp-interactive[NullableTupleEquality](../../samples/snippets/csharp/tuples/program.cs#NullableEquality "Comparing Tuples and nullable tuples")]

Równość krotek również wykonuje konwersje niejawne dla każdego elementu członkowskiego obu krotek. Obejmują one przenoszone konwersje, konwersje rozszerzające lub inne niejawne konwersje. Poniższe przykłady pokazują, że liczba całkowita 2-krotka może być porównana z długą 2-krotką ze względu na niejawną konwersję z liczby całkowitej na wartość Long:

[!code-csharp-interactive[SnippetMemberConversions](../../samples/snippets/csharp/tuples/program.cs#SnippetMemberConversions "converting tuples for equality tests")]

Nazwy składowych krotek nie uczestniczą w testach pod kątem równości. Jeśli jednak jeden z operandów jest literałem krotki z jawnymi nazwami, kompilator generuje ostrzeżenie CS8383, jeśli te nazwy nie pasują do nazw innych operandów.
W przypadku, gdy oba operandy są literałami krotki, ostrzeżenie znajduje się na prawym operandzie, jak pokazano w następującym przykładzie:

[!code-csharp-interactive[MemberNames](../../samples/snippets/csharp/tuples/program.cs#SnippetMemberNames "Tuple member names do not participate in equality tests")]

Na koniec krotki mogą zawierać krotki zagnieżdżone. Równość krotki porównuje "kształt" każdego operandu za pomocą krotek zagnieżdżonych, jak pokazano w następującym przykładzie:

[!code-csharp-interactive[NestedTuples](../../samples/snippets/csharp/tuples/program.cs#SnippetNestedTuples "Tuples may contain nested tuples that participate in tuple equality.")]

Jest to błąd czasu kompilacji służący do porównywania dwóch krotek w celu równości (lub nierówności), gdy mają różne kształty. Kompilator nie będzie podejmować próby odbudowy krotek zagnieżdżonych, aby je porównać.

## <a name="assignment-and-tuples"></a>Przypisanie i krotki

Język obsługuje przypisanie między typami krotek, które mają taką samą liczbę elementów, gdzie każdy element po prawej stronie może być niejawnie konwertowany do odpowiadającego mu elementu po lewej stronie. Inne konwersje nie są brane pod uwagę w przypisaniach. Jest to błąd czasu kompilacji, aby przypisać jedną krotkę do innej, gdy mają różne kształty. Kompilator nie będzie podejmować próby odbudowy krotek zagnieżdżonych, aby je przypisać.
Przyjrzyjmy się typom przypisań, które są dozwolone między typami krotek.

Należy wziąć pod uwagę te zmienne, które są używane w następujących przykładach:

[!code-csharp[VariableCreation](../../samples/snippets/csharp/tuples/program.cs#03_VariableCreation "Variable creation")]

Pierwsze dwie zmienne, `unnamed` i `anonymous` nie mają nazw semantycznych dla elementów. Nazwy pól są `Item1` i `Item2`.
Ostatnie dwie zmienne, `named` i `differentName` mają nazwy semantyczne podane dla elementów. Te dwie krotki mają różne nazwy dla elementów.

Wszystkie cztery z tych krotek mają tę samą liczbę elementów (określaną jako Kardynalność) i typy tych elementów są identyczne. W związku z tym wszystkie te przypisania działają:

[!code-csharp[VariableAssignment](../../samples/snippets/csharp/tuples/program.cs#04_VariableAssignment "Variable assignment")]

Zauważ, że nazwy krotek nie są przypisane. Wartości elementów są przypisywane po kolejności elementów w spójnej kolekcji.

Nie można przypisać krotek o różnych typach lub liczbie elementów:

```csharp
// Does not compile.
// CS0029: Cannot assign Tuple(int,int,int) to Tuple(int, string)
var differentShape = (1, 2, 3);
named = differentShape;
```

## <a name="tuples-as-method-return-values"></a>Krotki jako wartości zwracane przez metodę

Jednym z najpopularniejszych zastosowania krotek jest jako wartość zwracana przez metodę. Przejdźmy do jednego przykładu. Należy wziąć pod uwagę tę metodę, która oblicza odchylenie standardowe dla sekwencji liczb:

[!code-csharp[StandardDeviation](../../samples/snippets/csharp/tuples/statistics.cs#05_StandardDeviation "Compute Standard Deviation")]

> [!NOTE]
> Te przykłady obliczają Niepoprawione odchylenie standardowe próbki.
> Skorygowana formuła przykładowego odchylenia standardowego podzieli sumę kwadratów różnic od średniej przez (N-1), a nie N, jako metodę rozszerzenia `Average`. Zapoznaj się z tekstem statystyk, aby uzyskać szczegółowe informacje o różnicach między tymi formułami dotyczącymi odchylenia standardowego.

Poprzedni kod jest zgodny z formułą Textbook dla odchylenia standardowego. Tworzy poprawną odpowiedź, ale jest nieefektywną implementacją. Ta metoda wylicza dwa razy sekwencję: raz, aby utworzyć średnią, i raz, aby utworzyć średnią kwadratu różnicy średniej.
(Należy pamiętać, że zapytania LINQ są oceniane opóźnieniem, więc obliczenie różnic między średnią i średnią z tych różnic powoduje tylko jedno Wyliczenie).

Istnieje alternatywna formuła, która oblicza odchylenie standardowe przy użyciu tylko jednego wyliczenia sekwencji.  To obliczenie generuje dwie wartości, ponieważ wylicza sekwencję: sumę wszystkich elementów w sekwencji i sumę każdej wartości kwadratowej:

[!code-csharp[SumOfSquaresFormula](../../samples/snippets/csharp/tuples/statistics.cs#06_SumOfSquaresFormula "Compute Standard Deviation using the sum of squares")]

Ta wersja Wylicza sekwencję dokładnie raz. Ale nie jest to kod wielokrotnego użytku. W trakcie pracy można się dowiedzieć, że wiele różnych obliczeń statystycznych używa liczby elementów w sekwencji, sumy sekwencji i sumy kwadratów sekwencji. Refaktoryzacjmy metodę i piszą metodę narzędzia, która produkuje wszystkie trzy wartości. Wszystkie trzy wartości mogą być zwracane jako krotki.

Zaktualizujmy tę metodę, tak aby trzy wartości obliczane podczas wyliczania były przechowywane w spójnej kolekcji. Tworzy tę wersję:

[!code-csharp[TupleVersion](../../samples/snippets/csharp/tuples/statistics.cs#07_TupleVersion "Refactor to use tuples")]

Obsługa refaktoryzacji programu Visual Studio ułatwia wyodrębnienie funkcji podstawowych statystyk do metody prywatnej. Zapewnia metodę `private static`, która zwraca typ krotki z trzema wartościami `Sum`, `SumOfSquares` i `Count`:

[!code-csharp[TupleMethodVersion](../../samples/snippets/csharp/tuples/statistics.cs#08_TupleMethodVersion "After extracting utility method")]
 
Język umożliwia korzystanie z kilku opcji, których można użyć, jeśli chcesz zrobić kilka szybkiej edycji ręcznie. Najpierw można użyć deklaracji `var` w celu zainicjowania wyniku krotki z wywołania metody `ComputeSumAndSumOfSquares`. Można również utworzyć trzy zmienne dyskretne wewnątrz metody `ComputeSumAndSumOfSquares`. Wersja końcowa jest pokazana w poniższym kodzie:

[!code-csharp[CleanedTupleVersion](../../samples/snippets/csharp/tuples/statistics.cs#09_CleanedTupleVersion "After final cleanup")]

Tej ostatecznej wersji można użyć dla każdej metody, która wymaga tych trzech wartości lub dowolnego podzbioru.

Język obsługuje inne opcje zarządzania nazwami elementów w tych metodach zwracających spójność krotek.

Można usunąć nazwy pól z deklaracji wartości zwracanej i zwrócić spójną krotkę:

```csharp
private static (double, double, int) ComputeSumAndSumOfSquares(IEnumerable<double> sequence)
{
    double sum = 0;
    double sumOfSquares = 0;
    int count = 0;

    foreach (var item in sequence)
    {
        count++;
        sum += item;
        sumOfSquares += item * item;
    }

    return (sum, sumOfSquares, count);
}
```

Pola tej krotki mają nazwę `Item1`, `Item2` i `Item3`.
Zaleca się dostarczanie nazw semantycznych do elementów krotek zwracanych z metod.

Inny idiom, gdzie krotke mogą być przydatne podczas tworzenia zapytań LINQ. Ostatecznie przewidywany wynik często zawiera niektóre z właściwości wybranych obiektów, ale nie wszystkie.

Tradycyjnie można projektować wyniki zapytania w sekwencji obiektów, które były typu anonimowego. Przedstawiamy wiele ograniczeń, głównie ponieważ typy anonimowe nie mogą wygodnie nazywać się w zwracanym typie dla metody. Alternatywa przy użyciu `object` lub `dynamic` jako typ wyniku ma znaczny koszt wydajności.

Zwracanie sekwencji typu krotki jest proste, a nazwy i typy elementów są dostępne w czasie kompilacji i za pomocą narzędzi IDE.
Rozważmy na przykład aplikację do zrobienia. Można zdefiniować klasę podobną do następującej, aby reprezentować pojedynczy wpis na liście zadań do wykonania:

[!code-csharp[ToDoItem](../../samples/snippets/csharp/tuples/projectionsample.cs#14_ToDoItem "To Do Item")]

Aplikacje mobilne mogą obsługiwać zwartą postać bieżących elementów do wykonania, które wyświetlają tylko tytuł. To zapytanie LINQ spowodowałoby projekcję zawierającą tylko identyfikator i tytuł. Metoda zwracająca sekwencję krotek powoduje, że projekt jest dobrze:

[!code-csharp[QueryReturningTuple](../../samples/snippets/csharp/tuples/projectionsample.cs#15_QueryReturningTuple "Query returning a tuple")]

> [!NOTE]
> W C# 7,1, projekcje krotek umożliwiają tworzenie nazwanych krotek przy użyciu elementów w sposób podobny do nazw właściwości w typach anonimowych. W powyższym kodzie instrukcja `select` w projekcji zapytania tworzy krotkę, która ma elementy `ID` i `Title`.

Nazwana krotka może być częścią podpisu. Pozwala ona narzędziom kompilatora i IDE zapewnić statyczne sprawdzanie, czy wynik jest prawidłowo używany. Nazwana krotka również zawiera informacje o typie statycznym, więc nie ma potrzeby używania kosztownych funkcji czasu wykonywania, takich jak odbicie lub dynamiczne powiązanie, aby pracować z wynikami.

## <a name="deconstruction"></a>Dekonstrukcja

Wszystkie elementy w spójnej kolekcji można rozpakować przez *odbudowę* krotki zwracanej przez metodę. Istnieją trzy różne podejścia do dekonstrukcji krotek.  Najpierw można jawnie zadeklarować typ każdego pola wewnątrz nawiasów, aby utworzyć zmienne dyskretne dla każdego elementu w spójnej kolekcji:

[!code-csharp[Deconstruct](../../samples/snippets/csharp/tuples/statistics.cs#10_Deconstruct "Deconstruct")]

Można również zadeklarować niejawnie wpisane zmienne dla każdego pola w spójnej kolekcji przy użyciu słowa kluczowego `var` poza nawiasami:

[!code-csharp[DeconstructToVar](../../samples/snippets/csharp/tuples/statistics.cs#11_DeconstructToVar "Deconstruct to Var")]

Istnieje również możliwość użycia słowa kluczowego `var` z dowolnymi lub wszystkimi deklaracjami zmiennych w nawiasach. 

```csharp
(double sum, var sumOfSquares, var count) = ComputeSumAndSumOfSquares(sequence);
```

Nie można użyć określonego typu poza nawiasami, nawet jeśli każde pole w krotek ma ten sam typ.

Można także rozbudowy krotek z istniejącymi deklaracjami:

```csharp
public class Point
{
    public int X { get; set; }
    public int Y { get; set; }

    public Point(int x, int y) => (X, Y) = (x, y);
}
```

> [!WARNING]
> Nie można mieszać istniejących deklaracji z deklaracjami wewnątrz nawiasów. Na przykład następujące elementy są niedozwolone: `(var x, y) = MyMethod();`. Powoduje to CS8184 błędu, ponieważ *x* jest zadeklarowany wewnątrz nawiasów, a *y* jest poprzednio zadeklarowany w innym miejscu.

### <a name="deconstructing-user-defined-types"></a>Dekonstrukcja typów zdefiniowanych przez użytkownika

Każdy typ krotki można rozbudować, jak pokazano powyżej. Można również łatwo włączyć dekonstrukcja na dowolnym typie zdefiniowanym przez użytkownika (klasy, struktury, a nawet interfejsy).

Autor typu może zdefiniować jedną lub więcej metod `Deconstruct`, które przypisują wartości do dowolnej liczby zmiennych `out` reprezentujących elementy danych, które tworzą typ. Na przykład następujący typ `Person` definiuje metodę `Deconstruct`, która dekonstruuje obiekt osoby do elementów reprezentujących imię i nazwisko:

[!code-csharp[TypeWithDeconstructMethod](../../samples/snippets/csharp/tuples/person.cs#12_TypeWithDeconstructMethod "Type with a deconstruct method")]

Metoda dekonstrukcja umożliwia przypisanie z `Person` do dwóch ciągów reprezentujących właściwości `FirstName` i `LastName`:

[!code-csharp[Deconstruct Type](../../samples/snippets/csharp/tuples/program.cs#12A_DeconstructType "Deconstruct a class type")]

Można włączyć dekonstrukcja nawet dla typów, które nie zostały utworzone.
Metoda `Deconstruct` może być metodą rozszerzenia, która rozpakuje dostępne elementy członkowskie danych obiektu. W poniższym przykładzie przedstawiono typ `Student` pochodzący z typu `Person` i metodę rozszerzającą, która dekonstrukcjauje `Student` do trzech zmiennych reprezentujących `FirstName`, `LastName` i `GPA`:

[!code-csharp[ExtensionDeconstructMethod](../../samples/snippets/csharp/tuples/person.cs#13_ExtensionDeconstructMethod "Type with a deconstruct extension method")]

Obiekt `Student` ma teraz dwie dostępne metody `Deconstruct`: Metoda rozszerzająca zadeklarowana dla typów `Student` i element członkowski typu `Person`. Oba należą do zakresu, które umożliwiają rozbudowanie `Student` w dwie zmienne lub trzy.
Jeśli student zostanie przypisany do trzech zmiennych, zwracane są imiona, nazwisko, nazwisko i GPA. Jeśli student zostanie przypisany do dwóch zmiennych, zwracane są tylko imię i nazwisko.

[!code-csharp[Deconstruct extension method](../../samples/snippets/csharp/tuples/program.cs#13A_DeconstructExtension "Deconstruct a class type using an extension method")]

Należy ostrożnie definiować wiele metod `Deconstruct` w klasie lub hierarchii klas. Wiele metod `Deconstruct`, które mają taką samą liczbę parametrów `out`, może szybko spowodować niejasności. Obiekty wywołujące mogą nie być w stanie łatwo wywołać żądanej metody `Deconstruct`.

W tym przykładzie istnieje minimalna szansa na niejednoznaczne wywołanie, ponieważ metoda `Deconstruct` dla `Person` ma dwa parametry wyjściowe, a metoda `Deconstruct` dla `Student` ma trzy.

Operatory dekonstrukcji nie uczestniczą w testowaniu równości. Poniższy przykład generuje błąd kompilatora CS0019:

```csharp
Person p = new Person("Althea", "Goodwin");
if (("Althea", "Goodwin") == p)
    Console.WriteLine(p);
```

Metoda `Deconstruct` może skonwertować obiekt `Person` `p` do krotki zawierającej dwa ciągi, ale nie ma zastosowania w kontekście testów równości.

## <a name="tuples-as-out-parameters"></a>Krotki jako parametry out

Krotki mogą być używane *jako parametry out*. Nie należy mylić z żadną niejednoznaczność wymienioną wcześniej w sekcji [dekonstrukcja](#deconstruction) . W wywołaniu metody jest potrzebne tylko opisywanie kształtu krotki:

[!code-csharp[TuplesAsOutParameters](~/samples/snippets/csharp/tuples/program.cs#01_TupleAsOutVariable "Tuples as out parameters")]

Alternatywnie możesz użyć [_nienazwanej_](#named-and-unnamed-tuples) krotki i odwołać się do jego pól jako `Item1` i `Item2`:

```csharp
dict.TryGetValue(2, out (int, string) pair);
// ...
Console.WriteLine($"{pair.Item1}: {pair.Item2}");
```

## <a name="conclusion"></a>Wniosek 

Nowy język i obsługa biblioteki nazwanych krotek znacznie ułatwiają pracę z projektami korzystającymi ze struktur danych, które przechowują wiele elementów, ale nie definiują zachowania, jako klas i struktur. Używanie krotek dla tych typów jest łatwe i zwięzłe. Uzyskujesz wszystkie korzyści ze sprawdzenia typu statycznego bez konieczności tworzenia typów przy użyciu bardziej pełnej składni `class` lub `struct`. Nawet dlatego są one najbardziej przydatne w przypadku metod narzędziowych `private` lub `internal`. Tworzenie typów zdefiniowanych przez użytkownika, `class` lub `struct`, gdy metody publiczne zwracają wartość, która ma wiele elementów.

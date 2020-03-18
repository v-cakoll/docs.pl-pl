---
title: Typy krotki — przewodnik po językach C#
description: 'Dowiedz się więcej o typach nienazwanych i nazwanych krotek w c #'
ms.date: 05/15/2018
ms.technology: csharp-fundamentals
ms.assetid: ee8bf7c3-aa3e-4c9e-a5c6-e05cc6138baa
ms.openlocfilehash: 9ce9e1d4395d1a75f36004384ec215c615cd9802
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156912"
---
# <a name="c-tuple-types"></a>Typy krotki Języka C#

Krotek C# to typy zdefiniowane przy użyciu lekkiej składni. Zalety obejmują prostszą składnię, reguły konwersji na podstawie liczby (określane jako kardynalność) i typy elementów oraz spójne reguły dotyczące kopii, testów równości i przypisań. Jako kompromis krotek nie obsługują niektórych idiomów obiektowych związanych z dziedziczeniem. Możesz uzyskać przegląd w sekcji na [krotek w Co nowego w Języku C# 7.0](whats-new/csharp-7.md#tuples) artykułu.

W tym artykule dowiesz się, reguły języka regulujące krotek w języku C# 7.0 i nowszych wersjach, różne sposoby ich używania i wstępne wskazówki dotyczące pracy z krotek.

> [!NOTE]
> Nowe funkcje krotek wymagają <xref:System.ValueTuple> typów.
> Należy dodać pakiet [`System.ValueTuple`](https://www.nuget.org/packages/System.ValueTuple/) NuGet, aby używać go na platformach, które nie zawierają typów.
>
> Jest to podobne do innych funkcji języka, które opierają się na typy dostarczane w ramach. Przykłady obejmują `async` `await` i opierając `INotifyCompletion` się na interfejsie i `IEnumerable<T>`LINQ opierając się na . Jednak mechanizm dostarczania zmienia się, ponieważ .NET staje się coraz bardziej niezależny od platformy. Program .NET Framework nie zawsze może być dostarczany w tym samym rytmie co kompilator języka. Gdy nowe funkcje języka polegać na nowych typów, te typy będą dostępne jako pakiety NuGet, gdy funkcje języka wysyłać. Jak te nowe typy zostaną dodane do interfejsu API standardu .NET i dostarczane jako część struktury, wymóg pakietu NuGet zostaną usunięte.

Zacznijmy od powodów dodawania nowej obsługi krotki. Metody zwracają pojedynczy obiekt. Krotek umożliwiają pakowanie wielu wartości w tym pojedynczym obiekcie łatwiej.

Program .NET Framework `Tuple` ma już klasy ogólne. Klasy te miały jednak dwa główne ograniczenia. Po pierwsze, `Tuple` klasy nazwały `Item1` `Item2`swoje właściwości , i tak dalej. Nazwy te nie posiadają żadnych informacji semantycznych. Korzystanie `Tuple` z tych typów nie umożliwia komunikowania znaczenie każdej z właściwości. Nowe funkcje języka umożliwiają deklarowanie i używanie semantycznie znaczących nazw elementów w krotce.

Klasy `Tuple` powodują więcej problemów z wydajnością, ponieważ są one typy odwołań. Użycie jednego `Tuple` z typów oznacza przydzielanie obiektów. Na gorących ścieżkach przydzielanie wielu małych obiektów może mieć wymierny wpływ na wydajność aplikacji. W związku z tym obsługa języka dla `ValueTuple` krotek wykorzystuje nowe struktury.

Aby uniknąć tych braków, `class` można `struct` utworzyć lub do przenoszenia wielu elementów. Niestety, to więcej pracy dla Ciebie, i to przesłania intencji projektu. Tworzenie `struct` lub `class` oznacza, że definiujesz typ z danymi i zachowaniem. Wiele razy, po prostu chcesz przechowywać wiele wartości w jednym obiekcie.

Funkcje języka i `ValueTuple` struktury ogólne wymuszają regułę, której nie można dodać do tych typów krotki.
Wszystkie `ValueTuple` typy są *zmienne struktury*. Każde pole członkowskie jest polem publicznym. To sprawia, że są bardzo lekkie. Oznacza to jednak, że krotek nie należy używać tam, gdzie ważna jest niezmienność.

Krotek są zarówno prostsze i `class` `struct` bardziej elastyczne kontenery danych niż i typy. Zbadajmy te różnice.

## <a name="named-and-unnamed-tuples"></a>Nazwane i nienazwane krotek

Struktura `ValueTuple` ma pola `Item1`o `Item2` `Item3`nazwie , , i tak dalej, podobne `Tuple` do właściwości zdefiniowanych w istniejących typach.
Nazwy te są jedynymi nazwami, których można używać dla *nienazwanych krotek.* Jeśli do krotki nie podasz żadnych alternatywnych nazw pól, utworzono nienazwaną krotkę:

[!code-csharp[UnnamedTuple](../../samples/snippets/csharp/tuples/program.cs#01_UnNamedTuple "Unnamed tuple")]

Krotka w poprzednim przykładzie została zainicjowana przy użyciu stałych literału i nie będzie mieć nazwy elementów utworzone przy użyciu *rzutowania nazwy pola krotki* w Języku C# 7.1.

Jednak podczas inicjowania krotki, można użyć nowych funkcji języka, które dają lepsze nazwy dla każdego pola. W ten sposób tworzy *nazwane krotki*.
Nazwane krotek nadal mają `Item1` `Item2`elementy `Item3` o nazwie , i tak dalej.
Ale mają też synonimy dla każdego z tych elementów, które zostały nazwane.
Nazwanego krotki można utworzyć, określając nazwy dla każdego elementu. Jednym ze sposobów jest określenie nazw jako części inicjowania krotki:

[!code-csharp[NamedTuple](../../samples/snippets/csharp/tuples/program.cs#02_NamedTuple "Named tuple")]

Te synonimy są obsługiwane przez kompilator i język, dzięki czemu można skutecznie używać nazwanych krotek. IDEs i redaktorzy mogą odczytywać te nazwy semantyczne przy użyciu interfejsów API Roslyn. Można odwoływać się do elementów nazwanej krotki przez te nazwy semantyczne w dowolnym miejscu w tym samym zestawie. Kompilator zastępuje nazwy zdefiniowane odpowiednikami `Item*` podczas generowania skompilowanych danych wyjściowych. Skompilowany język pośredni (MSIL) nie zawiera nazw, które zostały podane przez te elementy.

Począwszy od Języka C# 7.1 nazwy pól dla krotki mogą być dostarczane ze zmiennych używanych do inicjowania krotki. Jest to określane jako **[inicjatory projekcji krotki](#tuple-projection-initializers)**. Poniższy kod tworzy krotkę o nazwie `accumulation` z elementami `count` (liczba całkowita) i `sum` (double).

[!code-csharp[ProjectedTuple](../../samples/snippets/csharp/tuples/program.cs#ProjectedTupleNames "Named tuple")]

Kompilator musi komunikować te nazwy utworzone dla krotek, które są zwracane z publicznych metod lub właściwości. W takich przypadkach kompilator dodaje <xref:System.Runtime.CompilerServices.TupleElementNamesAttribute> atrybut na metodę. Ten atrybut <xref:System.Runtime.CompilerServices.TupleElementNamesAttribute.TransformNames> zawiera właściwość list, która zawiera nazwy nadane każdemu z elementów w krotce.

> [!NOTE]
> Narzędzia programistyczne, takie jak Visual Studio, również przeczytać, że metadane i zapewniają IntelliSense i inne funkcje przy użyciu nazw pól metadanych.

Ważne jest, aby zrozumieć te podstawowe podstawy nowych krotek i `ValueTuple` typu, aby zrozumieć zasady przypisywania nazwanych krotek do siebie.

## <a name="tuple-projection-initializers"></a>Inicjatory projekcji krotki

Ogólnie rzecz biorąc inicjatory projekcji krotki działają przy użyciu nazwy zmiennej lub pola z prawej strony instrukcji inicjowania krotki.
Jeśli nadano jawną nazwę, która ma pierwszeństwo przed każdą wyświetlaną nazwą. Na przykład w następującym inicjatorze `localVariableOne` `localVariableTwo`elementy są `explicitFieldOne` i `explicitFieldTwo`, nie i:

[!code-csharp[ExplicitNamedTuple](../../samples/snippets/csharp/tuples/program.cs#ProjectionExample_Explicit "Explicitly named tuple")]

Dla każdego pola, w którym nie podano jawnej nazwy, wyświetlana jest odpowiednia nazwa niejawna. Nie ma wymogu podawania nazw semantycznych, jawnie lub niejawnie. Następujący inicjator `Item1`ma nazwy `42` `stringContent`pól , których wartość jest i , którego wartość jest "Odpowiedź na wszystko":

[!code-csharp[MixedTuple](../../samples/snippets/csharp/tuples/program.cs#MixedTuple "mixed tuple")]

Istnieją dwa warunki, w których nazwy pól kandydata nie są rzutowane na pole krotki:

1. Gdy nazwa kandydata jest zarezerwowana nazwa krotki. Przykłady obejmują `Item3` `ToString`, `Rest`lub .
1. Gdy nazwa kandydata jest duplikatem innej nazwy pola krotki, jawnej lub niejawnej.

Warunki te uniknąć dwuznaczności. Nazwy te spowodowałyby niejednoznaczność, gdyby były używane jako nazwy pól dla pola w krotce. Żaden z tych warunków nie powoduje błędów w czasie kompilacji. Zamiast tego elementy bez wyświetlanych nazw nie mają dla nich wyświetlanych nazw semantycznych.  W poniższych przykładach przedstawiono następujące warunki:

[!code-csharp-interactive[Ambiguity](../../samples/snippets/csharp/tuples/program.cs#ProjectionAmbiguities "tuples where projections are not performed")]

Sytuacje te nie powodują błędów kompilatora, ponieważ byłoby to zmiana podziału dla kodu napisanego za pomocą języka C# 7.0, gdy projekcje nazw pól krotki nie były dostępne.

## <a name="equality-and-tuples"></a>Równość i krotek

Począwszy od Języka C# 7.3 `==` `!=` typy krotki obsługują i operatorów. Operatory te działają, porównując każdy element członkowski argumentu left do każdego elementu członkowskiego argumentu po prawej kolejności. Porównania te są zwarte. Przestaną oceniać członków, gdy tylko jedna para nie będzie równa. Poniższe przykłady kodu `==`używają , ale wszystkie `!=`reguły porównania mają zastosowanie do . Poniższy przykład kodu przedstawia porównanie równości dla dwóch par liczb całkowitych:

[!code-csharp-interactive[TupleEquality](../../samples/snippets/csharp/tuples/program.cs#Equality "Testing tuples for equality")]

Istnieje kilka reguł, które sprawiają, że testy równości krotki są wygodniejsze. Równość krotki wykonuje [konwersje zniesione,](~/_csharplang/spec/conversions.md#lifted-conversion-operators) jeśli jedna z krotek jest stałą wartością null, jak pokazano w poniższym kodzie:

[!code-csharp-interactive[NullableTupleEquality](../../samples/snippets/csharp/tuples/program.cs#NullableEquality "Comparing Tuples and nullable tuples")]

Równość krotki wykonuje również niejawne konwersje na każdym elementem członkowskim obu krotek. Należą do nich konwersje zniesione, poszerzenie konwersji lub inne konwersje niejawne. W poniższych przykładach przedstawiono, że całkowita 2-krotka można porównać do długiej krotki 2 ze względu na niejawną konwersję z liczby całkowitej na długą:

[!code-csharp-interactive[SnippetMemberConversions](../../samples/snippets/csharp/tuples/program.cs#SnippetMemberConversions "converting tuples for equality tests")]

Nazwy członków krotki nie uczestniczą w testach równości. Jednak jeśli jeden z argumentów jest literału krotki z jawnymi nazwami, kompilator generuje ostrzeżenie CS8383, jeśli te nazwy nie są zgodne z nazwami innego operandu.
W przypadku, gdy oba operandy są literałami krotki, ostrzeżenie znajduje się na prawym operand, jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[MemberNames](../../samples/snippets/csharp/tuples/program.cs#SnippetMemberNames "Tuple member names do not participate in equality tests")]

Na koniec krotek może zawierać zagnieżdżonych krotek. Równość krotki porównuje "kształt" każdego operandu za pomocą zagnieżdżonych krotek, jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[NestedTuples](../../samples/snippets/csharp/tuples/program.cs#SnippetNestedTuples "Tuples may contain nested tuples that participate in tuple equality.")]

Jest to błąd czasu kompilacji, aby porównać dwie krotki dla równości (lub nierówności), gdy mają różne kształty. Kompilator nie będzie próbował żadnej dekonstrukcji zagnieżdżonych krotek w celu ich porównania.

## <a name="assignment-and-tuples"></a>Przypisanie i krotek

Język obsługuje przypisanie między typami krotki, które mają taką samą liczbę elementów, gdzie każdy element po prawej stronie można niejawnie konwertować na odpowiedni element po lewej stronie. Inne konwersje nie są uwzględniane w przypadku przypisań. Jest to błąd czasu kompilacji, aby przypisać jedną krotkę do innej, gdy mają różne kształty. Kompilator nie będzie próbował żadnej dekonstrukcji zagnieżdżonych krotek w celu ich przypisania.
Przyjrzyjmy się rodzajom przypisań, które są dozwolone między typami krotki.

Należy wziąć pod uwagę te zmienne używane w poniższych przykładach:

[!code-csharp[VariableCreation](../../samples/snippets/csharp/tuples/program.cs#03_VariableCreation "Variable creation")]

Pierwsze dwie zmienne `unnamed` i `anonymous` nie mają nazwy semantyczne przewidziane dla elementów. Nazwy pól `Item1` są `Item2`i .
Ostatnie dwie zmienne `named` i `differentName` mają nazwy semantyczne podane dla elementów. Te dwie krotki mają różne nazwy elementów.

Wszystkie cztery z tych krotek mają taką samą liczbę elementów (określane jako "kardynalność"), a typy tych elementów są identyczne. W związku z tym wszystkie te zadania działają:

[!code-csharp[VariableAssignment](../../samples/snippets/csharp/tuples/program.cs#04_VariableAssignment "Variable assignment")]

Należy zauważyć, że nazwy krotek nie są przypisane. Wartości elementów są przypisywane zgodnie z kolejnością elementów w krotce.

Krotek różnych typów lub liczb elementów nie można przypisać:

```csharp
// Does not compile.
// CS0029: Cannot assign Tuple(int,int,int) to Tuple(int, string)
var differentShape = (1, 2, 3);
named = differentShape;
```

## <a name="tuples-as-method-return-values"></a>Krotek jako wartości zwracane metody

Jednym z najczęstszych zastosowań krotek jest jako wartość zwracana metody. Przejdźmy przez jeden przykład. Należy wziąć pod uwagę tę metodę, która oblicza odchylenie standardowe dla sekwencji liczb:

[!code-csharp[StandardDeviation](../../samples/snippets/csharp/tuples/statistics.cs#05_StandardDeviation "Compute Standard Deviation")]

> [!NOTE]
> W tych przykładach obliczasię nieskorygowane odchylenie standardowe próbki.
> Skorygowana standardowa formuła odchylenia próbki podzieliłaby sumę kwadratowych różnic od średniej przez (N-1) zamiast N, tak jak robi to metoda `Average` rozszerzenia. Zapoznaj się z tekstem statystyk, aby uzyskać więcej informacji na temat różnic między tymi formułami odchylenia standardowego.

Poprzedni kod jest zgodny z formułą podręcznika dla odchylenia standardowego. Daje poprawną odpowiedź, ale jest to nieefektywna implementacja. Ta metoda wylicza sekwencję dwa razy: Raz do wytworzenia średniej, a raz do wytworzenia średniej kwadratu różnicy średniej.
(Należy pamiętać, że zapytania LINQ są oceniane leniwie, więc obliczenia różnic od średniej i średniej z tych różnic sprawia, że tylko jedno wyliczenie.)

Istnieje alternatywna formuła, która oblicza odchylenie standardowe przy użyciu tylko jednego wyliczenia sekwencji.  To obliczenia tworzy dwie wartości, ponieważ wylicza sekwencję: suma wszystkich elementów w sekwencji i suma każdej wartości do kwadratu:

[!code-csharp[SumOfSquaresFormula](../../samples/snippets/csharp/tuples/statistics.cs#06_SumOfSquaresFormula "Compute Standard Deviation using the sum of squares")]

Ta wersja wylicza sekwencję dokładnie raz. Ale to nie jest kod wielokrotnego użytku. Podczas pracy można znaleźć, że wiele różnych obliczeń statystycznych używać liczby elementów w sekwencji, suma sekwencji i suma kwadratów sekwencji. Refaktoryzujmy tę metodę i napiszmy metodę użyteczną, która tworzy wszystkie trzy z tych wartości. Wszystkie trzy wartości mogą być zwracane jako krotka.

Zaktualizujmy tę metodę, aby trzy wartości obliczone podczas wyliczenia były przechowywane w krotce. To tworzy tę wersję:

[!code-csharp[TupleVersion](../../samples/snippets/csharp/tuples/statistics.cs#07_TupleVersion "Refactor to use tuples")]

Obsługa refaktoryzacji programu Visual Studio ułatwia wyodrębnianie funkcji podstawowych statystyk do metody prywatnej. To daje `private static` metodę, która zwraca typ krotki `Sum` `SumOfSquares`z `Count`trzema wartościami , i :

[!code-csharp[TupleMethodVersion](../../samples/snippets/csharp/tuples/statistics.cs#08_TupleMethodVersion "After extracting utility method")]

Język umożliwia kilka opcji, które można użyć, jeśli chcesz dokonać kilku szybkich edycji ręcznie. Najpierw można użyć `var` deklaracji do zainicjowania wyniku krotki z wywołania `ComputeSumAndSumOfSquares` metody. Wewnątrz `ComputeSumAndSumOfSquares` metody można również utworzyć trzy zmienne dyskretne. Ostateczna wersja jest pokazana w następującym kodzie:

[!code-csharp[CleanedTupleVersion](../../samples/snippets/csharp/tuples/statistics.cs#09_CleanedTupleVersion "After final cleanup")]

Ta ostateczna wersja może służyć dla dowolnej metody, która wymaga tych trzech wartości lub dowolnego podzbioru z nich.

Język obsługuje inne opcje w zarządzaniu nazwy elementów w tych metod zwracania krotki.

Można usunąć nazwy pól z deklaracji wartości zwracanej i zwrócić nienazwaną krotkę:

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

Pola tej krotki `Item1`są `Item2`nazywane `Item3`, i .
Zaleca się podanie nazw semantycznych elementom krotek zwracanych z metod.

Innym idiomem, gdzie krotek mogą być przydatne jest podczas tworzenia zapytań LINQ. Ostateczny przewidywany wynik często zawiera niektóre, ale nie wszystkie właściwości wybranych obiektów.

Tradycyjnie rzutować wyniki kwerendy do sekwencji obiektów, które były typu anonimowego. To przedstawiło wiele ograniczeń, głównie dlatego, że typy anonimowe nie można wygodnie nazwać w typie zwracanym dla metody. Alternatywy `object` przy `dynamic` użyciu lub jako typ wyniku przyszedł ze znacznymi kosztami wydajności.

Zwracanie sekwencji typu krotki jest łatwe, a nazwy i typy elementów są dostępne w czasie kompilacji i za pośrednictwem narzędzi IDE.
Rozważmy na przykład aplikację DoDo. Można zdefiniować klasę podobną do następującej do reprezentowania pojedynczego wpisu na liście ToDo:

[!code-csharp[ToDoItem](../../samples/snippets/csharp/tuples/projectionsample.cs#14_ToDoItem "To Do Item")]

Aplikacje mobilne mogą obsługiwać kompaktową formę bieżących elementów do wykonania, która wyświetla tylko tytuł. To zapytanie LINQ będzie rzutowanie, które zawiera tylko identyfikator i tytuł. Metoda, która zwraca sekwencję krotek wyraża, że projekt dobrze:

[!code-csharp[QueryReturningTuple](../../samples/snippets/csharp/tuples/projectionsample.cs#15_QueryReturningTuple "Query returning a tuple")]

> [!NOTE]
> W języku C# 7.1 rzutowania krotki umożliwiają tworzenie nazwanych krotek przy użyciu elementów, w sposób podobny do nazewnictwa właściwości w typach anonimowych. W powyższym kodzie instrukcja `select` w projekcji kwerendy `ID` `Title`tworzy krotkę, która ma elementy i .

Nazwana krotka może być częścią podpisu. Umożliwia kompilatora i IDE narzędzia zapewniają statyczne sprawdzanie, że używasz wynik poprawnie. Nazwany krotka również przenosi informacje o typie statycznym, więc nie ma potrzeby używania kosztownych funkcji czasu wykonywania, takich jak odbicie lub dynamiczne powiązanie do pracy z wynikami.

## <a name="deconstruction"></a>Dekonstrukcji

Można rozpakować wszystkie elementy w krotce, *dekonstruując* krotkę zwróconą przez metodę. Istnieją trzy różne podejścia do dekonstrukcji krotek.  Najpierw można jawnie zadeklarować typ każdego pola w nawiasach, aby utworzyć zmienne dyskretne dla każdego z elementów w krotce:

[!code-csharp[Deconstruct](../../samples/snippets/csharp/tuples/statistics.cs#10_Deconstruct "Deconstruct")]

Można również zadeklarować niejawnie wpisane zmienne dla każdego `var` pola w krotce przy użyciu słowa kluczowego poza nawiasami:

[!code-csharp[DeconstructToVar](../../samples/snippets/csharp/tuples/statistics.cs#11_DeconstructToVar "Deconstruct to Var")]

Jest również legalne użycie `var` słowa kluczowego z dowolnymi lub wszystkimi deklaracjami zmiennych w nawiasach.

```csharp
(double sum, var sumOfSquares, var count) = ComputeSumAndSumOfSquares(sequence);
```

Nie można użyć określonego typu poza nawiasami, nawet jeśli każde pole w krotce ma ten sam typ.

Można dekonstruować krotek z istniejących deklaracji, jak również:

```csharp
public class Point
{
    public int X { get; set; }
    public int Y { get; set; }

    public Point(int x, int y) => (X, Y) = (x, y);
}
```

> [!WARNING]
> Nie można mieszać istniejących deklaracji z deklaracjami wewnątrz nawiasów. Na przykład, następujące nie `(var x, y) = MyMethod();`jest dozwolone: . Powoduje to błąd CS8184, ponieważ *x* jest zadeklarowany wewnątrz nawiasów i *y* jest wcześniej zadeklarowany w innym miejscu.

### <a name="deconstructing-user-defined-types"></a>Dekonstrukcja typów zdefiniowanych przez użytkownika

Każdy typ krotki może zostać zdekonstruowany, jak pokazano powyżej. Jest również łatwe do włączania dekonstrukcji na dowolnym typie zdefiniowanym przez użytkownika (klasy, struktury, a nawet interfejsy).

Autor typu można zdefiniować `Deconstruct` jedną lub więcej metod, które `out` przypisują wartości do dowolnej liczby zmiennych reprezentujących elementy danych, które tworzą typ. Na przykład następujący `Person` typ definiuje `Deconstruct` metodę, która dekonstruuje obiekt osoby do elementów reprezentujących imię i nazwisko:

[!code-csharp[TypeWithDeconstructMethod](../../samples/snippets/csharp/tuples/person.cs#12_TypeWithDeconstructMethod "Type with a deconstruct method")]

Metoda dekonstrukcji umożliwia przypisanie z `Person` dwóch ciągów, reprezentujących `FirstName` i `LastName` właściwości:

[!code-csharp[Deconstruct Type](../../samples/snippets/csharp/tuples/program.cs#12A_DeconstructType "Deconstruct a class type")]

Dekonstrukcji można włączyć nawet w przypadku typów, których nie autoryzowano.
Metoda `Deconstruct` może być metodą rozszerzenia, która rozpakowuje dostępne elementy członkowskie danych obiektu. Poniższy przykład przedstawia `Student` typ, pochodzące `Person` z typu i metody rozszerzenia, `Student` która dekonstruuje na `FirstName`trzy `LastName`zmienne, `GPA`reprezentujących , , i :

[!code-csharp[ExtensionDeconstructMethod](../../samples/snippets/csharp/tuples/person.cs#13_ExtensionDeconstructMethod "Type with a deconstruct extension method")]

Obiekt `Student` ma teraz `Deconstruct` dwie dostępne metody: metodę `Student` rozszerzenia zadeklarowaną dla `Person` typów i element członkowski typu. Oba są w zakresie i `Student` który umożliwia dekonstrukcji do dwóch zmiennych lub trzech.
Jeśli przypiszesz studenta do trzech zmiennych, zostaną zwrócone imię, nazwisko i GPA. Jeśli przypiszesz studenta do dwóch zmiennych, zwracane są tylko imię i nazwisko.

[!code-csharp[Deconstruct extension method](../../samples/snippets/csharp/tuples/program.cs#13A_DeconstructExtension "Deconstruct a class type using an extension method")]

Należy zachować ostrożność, definiując wiele `Deconstruct` metod w klasie lub hierarchii klas. Wiele `Deconstruct` metod, które mają `out` taką samą liczbę parametrów może szybko powodować niejasności. Dzwoniący mogą nie być w `Deconstruct` stanie łatwo wywołać żądaną metodę.

W tym przykładzie istnieje minimalna szansa na `Deconstruct` niejednoznaczne wywołanie, ponieważ metoda ma `Person` dwa parametry wyjściowe, a `Deconstruct` metoda ma `Student` trzy.

Operatorzy dekonstrukcji nie uczestniczą w testowaniu równości. Poniższy przykład generuje błąd kompilatora CS0019:

```csharp
Person p = new Person("Althea", "Goodwin");
if (("Althea", "Goodwin") == p)
    Console.WriteLine(p);
```

Metoda `Deconstruct` może przekonwertować `Person` obiekt `p` do krotki zawierającej dwa ciągi, ale nie ma zastosowania w kontekście testów równości.

## <a name="tuples-as-out-parameters"></a>Krotek jako parametry out

Krotek można używać jako *samych*parametrów. Nie należy mylić z żadną dwuznacznością wspomnianą wcześniej w sekcji [dekonstrukcji.](#deconstruction) W wywołaniu metody należy opisać tylko kształt krotki:

[!code-csharp[TuplesAsOutParameters](~/samples/snippets/csharp/tuples/program.cs#01_TupleAsOutVariable "Tuples as out parameters")]

Alternatywnie można użyć [_nienazwanej_](#named-and-unnamed-tuples) krotki i `Item1` odwoływać się do jej pól jako i: `Item2`

```csharp
dict.TryGetValue(2, out (int, string) pair);
// ...
Console.WriteLine($"{pair.Item1}: {pair.Item2}");
```

## <a name="conclusion"></a>Podsumowanie

Obsługa nowego języka i biblioteki dla nazwanych krotek znacznie ułatwia pracę z projektami, które używają struktur danych, które przechowują wiele elementów, ale nie definiują zachowanie, jak klasy i struktury zrobić. Jest to łatwe i zwięzłe w użyciu krotek dla tych typów. Otrzymasz wszystkie zalety sprawdzania typu statycznego, bez konieczności tworzenia `class` typów `struct` przy użyciu bardziej pełne lub składni. Mimo to, są one najbardziej przydatne `private`dla `internal`metod użytkowych, które są , lub . Tworzenie typów zdefiniowanych `class` przez `struct` użytkownika lub typy, gdy metody publiczne zwracają wartość, która ma wiele elementów.

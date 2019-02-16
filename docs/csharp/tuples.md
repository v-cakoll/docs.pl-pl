---
title: Typy krotki — Przewodnik po języku C#
description: Dowiedz się więcej o krotki nazwane i nienazwane typy w języku C#
ms.date: 05/15/2018
ms.assetid: ee8bf7c3-aa3e-4c9e-a5c6-e05cc6138baa
ms.openlocfilehash: 2c2b25c34555699c196099c0e1c51681fba8c358
ms.sourcegitcommit: 0069cb3de8eed4e92b2195d29e5769a76111acdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/16/2019
ms.locfileid: "56332757"
---
# <a name="c-tuple-types"></a>Typy krotek języka C# #

C# kolekcje są typy definiujące przy użyciu składni lekkiej. Zalety obejmują prostsze składni reguł podczas konwersji na podstawie liczby (nazywane kardynalności) i typy elementów i spójne zasady kopii, testy równości i przydziałów. Jako to z kompromisem krotek nie obsługują niektórych idiomy zorientowane obiektowo, skojarzone z dziedziczenia. Możesz uzyskać omówienie w sekcji na [krotek, co jest nowego w języku C# 7.0](whats-new/csharp-7.md#tuples) artykułu.

W tym artykule dowiesz się, zasady języka krotkami w języku C# 7.0 i nowsze wersje, różne sposoby stosowania je i wstępną wskazówki na temat pracy z krotek.

> [!NOTE]
> Nowe funkcje krotek wymagają <xref:System.ValueTuple> typów.
> Należy dodać pakiet NuGet [ `System.ValueTuple` ](https://www.nuget.org/packages/System.ValueTuple/) aby można było używać go na platformach, które nie zawierają typy.
>
> Jest to podobne do innych funkcji języka, które zależą od typów dostarczonych w ramach. Przykłady obejmują `async` i `await` opierając się na `INotifyCompletion` interfejsu i LINQ, opierając się na `IEnumerable<T>`. Jednak mechanizm dostarczania jest zmieniają się wraz z .NET staje się coraz więcej platform niezależne. .NET Framework mogą zawsze są dostarczane na ten sam cykl, jak kompilator języka. Jeśli nowe funkcje języka, zależą od nowych typów, te typy są dostępne jako pakiety NuGet podczas dostarczania funkcji języka. Ponieważ te nowe typy są dodawane do standardowego interfejsu API platformy .NET i dostarczane jako część ram, wymaganie pakietu NuGet zostaną usunięte.

Zacznijmy od przyczyny, dla których do dodawania nowych obsługi spójnej kolekcji. Metody zwracają jeden obiekt. Spójne kolekcje umożliwiają łatwiejsze pakowanie wielu wartości w tym pojedynczego obiektu.

.NET Framework jest już ogólny `Tuple` klasy. Te klasy, ma dwa główne ograniczenia. Dla jednego `Tuple` klasy o nazwie ich właściwości `Item1`, `Item2`i tak dalej. Te nazwy objęte żadne informacje semantyczne. Korzystanie z tych `Tuple` typów nie obsługuje komunikacji znaczenie każdej właściwości. Nowe funkcje języka umożliwiają deklarowanie i użycie semantycznie znaczące nazwy elementów w krotce.

`Tuple` Klasy spowodować więcej problemów z wydajnością, ponieważ są to typy odwołań. Przy użyciu jednej z `Tuple` typy oznacza, że alokacja obiektów. W warstwie gorąca ścieżkach przydzielanie wielu małych obiektów może mieć zauważalnego wpływu na wydajność aplikacji. W związku z tym, obsługa języków w krotek korzysta z nowym `ValueTuple` struktury.

Aby uniknąć tych braki, można utworzyć `class` lub `struct` do wykonania wielu elementów. Niestety to więcej pracy i następuje ukrycie zgodną z planem projektu. Tworzenie `struct` lub `class` oznacza definiowania typu przy użyciu danych i zachowania. Wiele razy po prostu chcesz przechowywać wiele wartości w pojedynczy obiekt.

Funkcje języka i `ValueTuple` struktury ogólne wymusić regułę, że nie można dodać każde zachowanie (metod) aby te typy krotek.
Wszystkie `ValueTuple` typy są *mutable struktury*. Każde pole elementu członkowskiego jest polem publiczne. Dzięki temu ich bardzo uproszczone. Jednak oznacza to, że nie należy używać krotek których niezmienności jest ważna.

Kolekcje są oba kontenery danych prostszy i bardziej elastyczne niż `class` i `struct` typów. Przyjrzyjmy się różnic.

## <a name="named-and-unnamed-tuples"></a>Nazwane i nienazwane krotki

`ValueTuple` Struktura zawiera pola o nazwie `Item1`, `Item2`, `Item3`i tak dalej podobne do właściwości zdefiniowane w istniejącym `Tuple` typów.
Te nazwy są tylko nazwy służy do *nienazwane krotek*. Wszystkie nazwy alternatywne pól do krotki nie zostanie określona, utworzono krotka bez nazwy:

[!code-csharp[UnnamedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#01_UnNamedTuple "Unnamed tuple")]

Spójna kolekcja znajdująca się w poprzednim przykładzie została zainicjowana przy użyciu stałych literału i nie będzie nazwy elementów utworzonych za pomocą *projekcje nazwę pola krotki* w języku C# 7.1.

Jednak podczas inicjowania krotki można użyć nowych funkcji języków, które zapewniają lepszą nazwy do każdego pola. Spowoduje to utworzenie *o nazwie krotki*.
Nazwane krotek nadal mieć elementy o nazwie `Item1`, `Item2`, `Item3` i tak dalej.
Jednak mają one również synonimy dla każdej z tych elementów, które mają nazwane.
Możesz utworzyć nazwanego spójnej kolekcji przez określenie nazwy dla każdego elementu. Jednym ze sposobów jest określane są nazwy w ramach inicjowania spójnej kolekcji:

[!code-csharp[NamedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#02_NamedTuple "Named tuple")]

Dodawanie tych synonimów są obsługiwane przez kompilator i język tak, aby można było używać o nazwie krotek skutecznie. Środowiska IDE i edytorów mogą odczytywać te nazwy semantycznych przy użyciu interfejsów API Roslyn. Elementy o nazwie krotki można się odwoływać przy użyciu tych nazw semantyczne w dowolnym miejscu tego samego zestawu. Kompilator zamienia nazwy zdefiniowany przez użytkownika za pomocą `Item*` odpowiedniki podczas generowania skompilowanych danych wyjściowych. Skompilowany Microsoft Intermediate Language (MSIL) nie zawiera nazwy, został przez Ciebie udzielony tych elementów.

Począwszy od języka C# 7.1 nazw pól dla krotki mogą być udostępniane ze zmiennych, używane do zainicjowania spójnej kolekcji. Jest to określane jako  **[krotki rzutowanie inicjatorach](#tuple-projection-initializers)**. Poniższy kod tworzy spójną kolekcję o nazwie `accumulation` z elementami `count` (liczba całkowita), a `sum` (wartość o podwójnej precyzji).

[!code-csharp[ProjectedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#ProjectedTupleNames "Named tuple")]

Kompilator musi komunikować się tymi nazwami utworzonych dla krotek, które są zwracane z właściwości lub metody publiczne. W takich przypadkach kompilator sam doda <xref:System.Runtime.CompilerServices.TupleElementNamesAttribute> atrybutu w metodzie. Ten atrybut zawiera <xref:System.Runtime.CompilerServices.TupleElementNamesAttribute.TransformNames> listy właściwości, która zawiera nazwy do poszczególnych elementów w spójnej kolekcji.

> [!NOTE]
> Narzędziami programistycznymi, takimi jak Visual Studio również odczytywać metadane i funkcji IntelliSense i inne funkcje za pomocą nazwy pól metadanych.

Należy zrozumieć podstawowe podstawowe informacje na temat nowych krotek i `ValueTuple` typu, aby zrozumieć zasady przypisywania o nazwie krotek do siebie nawzajem.

## <a name="tuple-projection-initializers"></a>Inicjatory projekcji krotki

Ogólnie rzecz biorąc krotki rzutowanie inicjatorach pracować przy użyciu nazwy zmiennej lub pola z po prawej stronie instrukcji inicjowania spójnej kolekcji.
Jeśli jawna nazwa zostanie podany, który ma pierwszeństwo przed dowolną nazwę przewidywany. Na przykład w inicjatorze następujące elementy są `explicitFieldOne` i `explicitFieldTwo`, a nie `localVariableOne` i `localVariableTwo`:

[!code-csharp[ExplicitNamedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#ProjectionExample_Explicit "Explicitly named tuple")]

Dla dowolnego pola, w którym jawna nazwa nie zostanie podany przewidywany jest zastosowanie nazwy niejawne. Nie ma jawnie lub niejawnie, zapewnienie semantycznego nazwy. Następujący inicjator ma nazw pól `Item1`, którego wartością jest `42` i `stringContent`, którego wartość to "Odpowiedź do wszystkich":

[!code-csharp[MixedTuple](../../samples/snippets/csharp/tuples/tuples/program.cs#MixedTuple "mixed tuple")]

Istnieją dwa warunki gdzie Release candidate nazwy pól nie są pokazane na pole spójnej kolekcji:

1. Gdy nazwa Release candidate jest nazwą zarezerwowanych spójnej kolekcji. Przykłady obejmują `Item3`, `ToString`. lub `Rest`.
1. Gdy nazwa Release candidate jest duplikatem innej nazwy pola krotki jawnych lub niejawnych.

Te warunki uniknąć niejednoznaczności. Te nazwy mogłoby spowodować niejednoznaczność, gdyby były one używane jako nazwy pól dla pola w spójnej kolekcji. Żadna z tych warunków nie powodują błędy czasu kompilacji. Zamiast tego elementy bez nazwy przewidywany nie ma nazwy semantycznego przewidywany dla nich.  W poniższych przykładach pokazano następujące warunki:

[!code-csharp-interactive[Ambiguity](../../samples/snippets/csharp/tuples/tuples/program.cs#ProjectionAmbiguities "tuples where projections are not performed")]

Tych sytuacji nie powodują błędy kompilatora, ponieważ byłoby istotną zmianę kod napisany w języku C# 7.0 podczas projekcji nazwę pola krotki nie były dostępne.

## <a name="equality-and-tuples"></a>Równości i krotki

Począwszy od języka C# 7.3 krotki typy obsługi `==` i `!=` operatorów. Te operatory działają przez porównanie każdy element członkowski argument po lewej stronie do każdego członka prawy argument w kolejności. Zwarcie tych porównań. Przestaną one oceny członków, jak tylko jedną parę nie jest równa. Poniższy kod przykłady użycia `==`, ale dotyczą wszystkich reguł porównania `!=`. Poniższy przykład kodu pokazuje porównania dla dwóch par liczb całkowitych:

[!code-csharp-interactive[TupleEquality](../../samples/snippets/csharp/tuples/tuples/program.cs#Equality "Testing tuples for equality")]

Istnieje kilka reguł, które testy równość krotki bardziej wygodne. Równość krotki wykonuje [zniesione konwersje](~/_csharplang/spec/conversions.md#lifted-conversion-operators) jedna z krotek czy krotki dopuszczającego wartość null, jak pokazano w poniższym kodzie:

[!code-csharp-interactive[NullableTupleEquality](../../samples/snippets/csharp/tuples/tuples/program.cs#NullableEquality "Comparing Tuples and nullable tuples")]

Równość krotki również wykonuje konwersje niejawne w każdym członku zarówno krotek. Obejmują one podniesionym konwersji, rozszerzające konwersje lub inne niejawne konwersje. Poniższe przykłady pokazują, czy liczba całkowita 2-krotka można porównać do długie 2-krotka z powodu niejawna konwersja liczbę całkowitą długie:

[!code-csharp-interactive[SnippetMemberConversions](../../samples/snippets/csharp/tuples/tuples/program.cs#SnippetMemberConversions "converting tuples for equality tests")]

Nazwy elementów członkowskich krotki nie biorą udziału w testach dla równości. Jednakże jeśli jeden z argumentów jest literałem jawne nazwy krotki, kompilator generuje ostrzeżenie CS8383, jeśli te nazwy są niezgodne nazwy to drugi operand.
W przypadku, gdy oba operandy są literałach krotek to ostrzeżenie jest na prawy operand jak pokazano w poniższym przykładzie:

[!code-csharp-interactive[MemberNames](../../samples/snippets/csharp/tuples/tuples/program.cs#SnippetMemberNames "Tuple member names do not participate in equality tests")]

Na koniec krotek mogą zawierać zagnieżdżonych krotek. Równość krotki porównuje "kształt" Każdy argument przy użyciu zagnieżdżonych krotek, co pokazano w poniższym przykładzie:

[!code-csharp-interactive[NestedTuples](../../samples/snippets/csharp/tuples/tuples/program.cs#SnippetNestedTuples "Tuples may contain nested tuples that participate in tuple equality.")]

Jest to błąd czasu kompilacji, aby porównać dwie spójne kolekcje pod względem równości (lub nierówności) gdy mają różne kształty. Kompilator wygrał "podejmować żadnych dekonstrukcja krotek zagnieżdżonych w celu porównania ich.

## <a name="assignment-and-tuples"></a>Przypisanie i krotki

Język obsługuje przypisanie między typy krotek, które mają taką samą liczbę elementów, gdzie każdy element po prawej stronie mogą być niejawnie konwertowane do odpowiadającego mu elementu po lewej stronie. Inne konwersje nie są traktowane jako przydziałów. Jest to błąd czasu kompilacji, można przypisać po jednej krotce na inny, gdy mają one różne kształty. Kompilator nie będzie podejmować żadnych dekonstrukcja krotek zagnieżdżonych Aby przypisać je.
Przyjrzyjmy się rodzaje przypisania, które są dozwolone między typami spójnej kolekcji.

Należy wziąć pod uwagę te zmienne używane w następujących przykładach:

[!code-csharp[VariableCreation](../../samples/snippets/csharp/tuples/tuples/program.cs#03_VariableCreation "Variable creation")]

Pierwsze dwie zmienne `unnamed` i `anonymous` nie zawiera semantyczną nazw określone elementy. Nazwy pól są `Item1` i `Item2`.
Ostatnie dwie zmienne `named` i `differentName` semantycznego nazwach podanych elementów. Te dwie spójne kolekcje mają różne nazwy elementów.

Wszystkie cztery krotek, te mają taką samą liczbę elementów (nazywane "Kardynalność") i typy te elementy są identyczne. W związku z tym wszystkie te przydziały pracy:

[!code-csharp[VariableAssignment](../../samples/snippets/csharp/tuples/tuples/program.cs#04_VariableAssignment "Variable assignment")]

Należy zauważyć, że nazwy kolekcje nie są przypisane. Wartości elementów są przypisywane w kolejności elementów w spójnej kolekcji.

Krotki o różnych typach lub liczby elementów, nie są możliwe do przypisania:

```csharp
// Does not compile.
// CS0029: Cannot assign Tuple(int,int,int) to Tuple(int, string)
var differentShape = (1, 2, 3);
named = differentShape;
```

## <a name="tuples-as-method-return-values"></a>Krotki jako wartości zwracane metody

Jednym z najbardziej typowych zastosowań krotek jest jako wartość zwracaną metody. Przejdźmy przykładem. Należy wziąć pod uwagę tej metody, które oblicza odchylenie standardowe w sekwencji liczb:

[!code-csharp[StandardDeviation](../../samples/snippets/csharp/tuples/tuples/statistics.cs#05_StandardDeviation "Compute Standard Deviation")]

> [!NOTE]
> Te przykłady obliczeń odchylenie standardowe Niepoprawione próbki.
> Wzór odchylenia standardowego poprawione próbki podzieleniu suma kwadratów różnic od średniej przez (n-1) zamiast N, jako `Average` metody rozszerzenia. Zapoznaj się tekst statystyki, aby uzyskać więcej informacji na temat różnic między te formuły odchylenie standardowe.

Powyższy kod poniżej Podręcznikowy formułę odchylenia standardowego. Tworzy poprawną odpowiedź, ale jest nieefektywną implementację. Ta metoda wylicza kolejność dwa razy: Jeden raz, aby wygenerować średnią i jeden raz, aby wygenerować średnia kwadratu różnicy średniej.
(Pamiętaj, że zapytania LINQ są obliczane z opóźnieniem, więc obliczania różnic od wartości średniej oraz średnią różnic sprawia, że tylko jedno wyliczenie).

Istnieje alternatywny formuły, które oblicza odchylenie standardowe przy użyciu funkcji wyliczania tylko jednej sekwencji.  To obliczenie tworzy dwie wartości, jak wylicza kolejność: Suma wszystkich elementów w sekwencji, a sumę każdej wartości kwadrat:

[!code-csharp[SumOfSquaresFormula](../../samples/snippets/csharp/tuples/tuples/statistics.cs#06_SumOfSquaresFormula "Compute Standard Deviation using the sum of squares")]

Ta wersja wylicza sekwencji dokładnie jeden raz. Ale nie jest do ponownego wykorzystania kodu. Jak możesz kontynuować pracę, przekonasz się, że wiele różnych obliczeń statystycznych używają liczba elementów w sekwencji, sumę sekwencji i suma kwadratów sekwencji. Przejdźmy Refaktoryzuj tę metodę i napisanie metody narzędzia, która tworzy wszystkie trzy tych wartości. Wszystkie trzy wartości mogą być zwracane jako krotki.

Zaktualizujmy tej metody, więc trzy wartości obliczonych podczas wyliczania są przechowywane w spójnej kolekcji. Który tworzy tę wersję:

[!code-csharp[TupleVersion](../../samples/snippets/csharp/tuples/tuples/statistics.cs#07_TupleVersion "Refactor to use tuples")]

Pomoc techniczna dla programu Visual Studio Refactoring ułatwia wyodrębnić funkcja statystyki podstawowe do metody prywatnej. Zapewnia to `private static` metodę, która zwraca typ krotki z trzech wartości `Sum`, `SumOfSquares`, i `Count`:

[!code-csharp[TupleMethodVersion](../../samples/snippets/csharp/tuples/tuples/statistics.cs#08_TupleMethodVersion "After extracting utility method")]
 
Język umożliwia kilka więcej opcji, których można użyć, jeśli chcesz ręcznie wprowadzić kilka szybka edycja. Najpierw należy użyć `var` deklaracji zainicjować krotki wynikiem `ComputeSumAndSumOfSquares` wywołania metody. Możesz również utworzyć trzy zmienne dyskretnego wewnątrz `ComputeSumAndSumOfSquares` metody. Ostateczna wersja pokazano w poniższym kodzie:

[!code-csharp[CleanedTupleVersion](../../samples/snippets/csharp/tuples/tuples/statistics.cs#09_CleanedTupleVersion "After final cleanup")]

Tej wersji ostatecznej może służyć do dowolnej metody, która potrzebuje tych trzech wartości lub dowolny podzbiór.

Język obsługuje inne opcje zarządzania nazwy elementów w tych metodach zwracanie spójnej kolekcji.

Można usunąć nazwy pól z deklaracji zwracana wartość i zwrócić krotka bez nazwy:

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

Pola tego krotki są nazywane `Item1`, `Item2`, i `Item3`.
Zalecane jest, aby podać semantycznego nazwy elementów krotek zwrócony z metody.

Idiom innego, gdzie krotek może być przydatne jest podczas tworzenia zapytania LINQ. Przewidywany wynik końcowy często zawiera niektóre, ale nie wszystkie właściwości obiekty są wybrane.

Wyniki zapytania będą tradycyjnie projektu sekwencję obiektów, które były typu anonimowego. Wiele ograniczeń, przedstawione przede wszystkim, ponieważ typy anonimowe można nie zostaną w wygodny sposób mieć nazwy w typie zwracanym dla metody. Za pomocą rozwiązania alternatywne `object` lub `dynamic` jako typ wyniku pochodzi z kosztami istotnie poprawiającą wydajność.

Zwraca sekwencję krotki typu jest łatwe i nazwy i typy elementów są dostępne w czasie kompilacji, jak i za pomocą narzędzi IDE.
Na przykład należy wziąć pod uwagę aplikację zadań do wykonania. Można zdefiniować klasę podobne do następujących czynności, aby reprezentować pojedynczy wpis na liście zadań do wykonania:

[!code-csharp[ToDoItem](../../samples/snippets/csharp/tuples/tuples/projectionsample.cs#14_ToDoItem "To Do Item")]

Twoje aplikacje mobilne mogą obsługiwać compact formularza bieżących elementów zadań do wykonania, która wyświetla tylko tytuł. Czy zapytania LINQ czyniłyby projekcji, zawiera tylko identyfikator i tytuł. Metody, która zwraca sekwencję krotek wyraża projektu oraz:

[!code-csharp[QueryReturningTuple](../../samples/snippets/csharp/tuples/tuples/projectionsample.cs#15_QueryReturningTuple "Query returning a tuple")]

> [!NOTE]
> W języku C# 7.1 projekcje krotki umożliwiają tworzenie nazwanego krotek, za pomocą elementów, w sposób podobny do nazw właściwości typów anonimowych. W powyższym kodzie `select` instrukcji w projekcji zapytań tworzy spójną kolekcją, która ma elementy `ID` i `Title`.

Krotki o nazwie może być częścią podpisu. Dzięki temu kompilator i narzędzia IDE zapewniają statyczne, sprawdzanie, czy używasz wynik poprawnie. Nazwane krotki również przenosi informacje typu statycznego, więc nie ma potrzeby używania czas wykonywania kosztownych funkcji, takich jak odbicie lub dynamiczne powiązanie do pracy z wynikami.

## <a name="deconstruction"></a>Dekonstrukcja

Można rozpakować wszystkie elementy w krotce przez *dekonstrukcja* krotki zwracane przez metodę. Istnieją trzy różne sposoby dekonstrukcja krotek.  Po pierwsze można jawnie zadeklarować typ każdego pola, wewnątrz nawiasów, aby utworzyć zmienne dyskretnego dla poszczególnych elementów w spójnej kolekcji:

[!code-csharp[Deconstruct](../../samples/snippets/csharp/tuples/tuples/statistics.cs#10_Deconstruct "Deconstruct")]

Niejawnie wpisane zmienne dla każdego pola w krotce można również zadeklarować za pomocą `var` — słowo kluczowe poza nawiasy:

[!code-csharp[DeconstructToVar](../../samples/snippets/csharp/tuples/tuples/statistics.cs#11_DeconstructToVar "Deconstruct to Var")]

Jest również użycie `var` — słowo kluczowe z dowolnego lub wszystkich deklaracji zmiennych wewnątrz nawiasów. 

```csharp
(double sum, var sumOfSquares, var count) = ComputeSumAndSumOfSquares(sequence);
```

Nie można użyć określonego typu przed nawiasem, nawet wtedy, gdy każde pole w spójnej kolekcji ma tego samego typu.

Można dekonstruować krotki z istniejącej deklaracji także:

```csharp
public class Point
{
    public int X { get; set; }
    public int Y { get; set; }

    public Point(int x, int y) => (X, Y) = (x, y);
}
```

> [!WARNING]
>  Nie można łączyć istniejące deklaracje za pomocą deklaracji wewnątrz nawiasów. Na przykład następujące jest niedozwolone: `(var x, y) = MyMethod();`. Powoduje to błąd CS8184, ponieważ *x* jest zadeklarowana wewnątrz nawiasów i *y* wcześniej zadeklarowano gdzie indziej.

### <a name="deconstructing-user-defined-types"></a>Dekonstrukcja typy zdefiniowane przez użytkownika

Może zostać zdekonstruowana dowolnego typu krotki, jak pokazano powyżej. Jest również łatwo włączyć dekonstrukcja z każdym typem zdefiniowanych przez użytkownika (klasy, struktury lub nawet interfejsów).

Autor typu można zdefiniować co najmniej jeden `Deconstruct` metod, które przypisać wartości do dowolnej liczby `out` zmienne reprezentujących elementy danych, które tworzą typu. Na przykład następująca `Person` typ definiuje `Deconstruct` metodę, która deconstructs osoby do elementów reprezentujących imię i nazwisko:

[!code-csharp[TypeWithDeconstructMethod](../../samples/snippets/csharp/tuples/tuples/person.cs#12_TypeWithDeconstructMethod "Type with a deconstruct method")]

Metoda dekonstrukcji umożliwia przypisanie z `Person` na dwa ciągi znaków reprezentujące `FirstName` i `LastName` właściwości:

[!code-csharp[Deconstruct Type](../../samples/snippets/csharp/tuples/tuples/program.cs#12A_DeconstructType "Deconstruct a class type")]

Można włączyć dekonstrukcja nawet w przypadku typów, które autorów.
`Deconstruct` Metoda może być metodą rozszerzenia, którą rozpakowywana członków dostępnych danych obiektu. Poniżej przedstawiono przykład `Student` typu pochodną `Person` typu i metodę rozszerzenia, które deconstructs `Student` do trzech zmiennych, reprezentujący `FirstName`, `LastName`i `GPA`:

[!code-csharp[ExtensionDeconstructMethod](../../samples/snippets/csharp/tuples/tuples/person.cs#13_ExtensionDeconstructMethod "Type with a deconstruct extension method")]

A `Student` ma teraz dostępne dwie `Deconstruct` metody: metoda rozszerzenia zadeklarowany dla `Student` typów i członek `Person` typu. Znajdują się zarówno w zakresie i który umożliwia `Student` można zostać zdekonstruowana do dwóch zmiennych lub trzy.
Jeśli student można przypisać do trzech zmiennych, imienia, ostatni nazwę i GPA wszystkie zwracane są. Jeśli przypiszesz student dwie zmienne, zwracane są tylko imię i nazwisko.

[!code-csharp[Deconstruct extension method](../../samples/snippets/csharp/tuples/tuples/program.cs#13A_DeconstructExtension "Deconstruct a class type using an extension method")]

Należy zachować ostrożność, Definiowanie wielu `Deconstruct` metody w klasie lub hierarchii klas. Wiele `Deconstruct` metody, które mają taką samą liczbę `out` parametry szybko mogą powodować niejednoznaczności. Obiekty wywołujące nie można łatwo wywołać żądaną `Deconstruct` metody.

W tym przykładzie ma minimalne możliwości niejednoznaczne wywołanie ponieważ `Deconstruct` metodę `Person` ma dwa produkt wyjściowy parametrów, a `Deconstruct` metodę `Student` ma trzy.

Operatory dekonstrukcja nie biorą udziału w testowaniu równości. Poniższy przykład generuje błąd kompilatora CS0019:

```csharp
Person p = new Person("Althea", "Goodwin");
if (("Althea", "Goodwin") == p)
    Console.WriteLine(p);
```

`Deconstruct` Metoda można przekonwertować `Person` obiektu `p` do spójnych kolekcji zawierający dwa ciągi, ale nie ma zastosowania w kontekście testy równości.

## <a name="conclusion"></a>Wniosek 

Nowy język i biblioteki obsługę krotek nazwane sprawia, że znacznie łatwiej jest pracować z projektami używające struktur danych, które przechowują wiele elementów, ale nie definiują zachowania, tak jak klas i struktur. Jest to łatwa i zwięzła, aby używać spójnych kolekcji dla tych typów. Możesz korzystać ze wszystkich zalet sprawdzania typu statycznego, bez konieczności tworzenia typów przy użyciu bardziej szczegółowy `class` lub `struct` składni. Mimo to najbardziej przydatny w przypadku metod narzędzie, które są `private`, lub `internal`. Tworzenie typów zdefiniowanych przez użytkownika, albo `class` lub `struct` typów podczas publicznej metody zwracają wartość, która ma wiele elementów.

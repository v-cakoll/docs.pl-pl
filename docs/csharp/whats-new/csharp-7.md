---
title: Nowości w języku C# 7.0 — przewodnik C#
description: Omówienie nowe funkcje dostępne w kolejnych wersji języka C# 7.
ms.date: 12/21/2016
ms.assetid: fd41596d-d0c2-4816-b94d-c4d00a5d0243
ms.openlocfilehash: a78b30411d734d6dadc52b7dbd402763d4eb7f5e
ms.sourcegitcommit: 88f251b08bf0718ce119f3d7302f514b74895038
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/10/2018
---
# <a name="whats-new-in-c-70"></a>Nowości w języku C# w wersji 7.0

C# 7.0 dodano wiele nowych funkcji języka C#:
* [`out` zmienne](#out-variables)
    - Można zadeklarować `out` wartości wbudowanego jako argumenty do metody, gdzie są używane.
* [Krotki](#tuples)
    - Można utworzyć niewielka, bez nazwy typów, które zawierają wiele pola publiczne. Kompilatory i narzędzia IDE zrozumieć semantykę tych typów.
* [Odrzucenia](#discards)
    - Odrzucenia są tymczasowe, tylko do zapisu zmiennych przypisania podczas nie interesujących przypisanej wartości. Są one szczególnie przydatne, gdy deconstructing spójne kolekcje i typy danych zdefiniowane przez użytkownika, a także podczas wywoływania metody z `out` parametrów.
* [Dopasowanie do wzorca](#pattern-matching)
    - Można tworzyć logikę rozgałęziania na podstawie dowolnego typu i wartości elementów członkowskich tych typów.
* [`ref` Zmienne lokalne i zwraca](#ref-locals-and-returns)
    - Argumenty metody i zmienne lokalne mogą być odwołania do innych magazynów.
* [Funkcje lokalne](#local-functions)
    - Można zagnieżdżać funkcji wewnątrz innych funkcji, aby ograniczyć ich zakres i widoczność.
* [Zabudowanych wyrażenia elementów członkowskich](#more-expression-bodied-members)
    - Lista elementów członkowskich, które można tworzyć za pomocą wyrażeń został rozszerzony.
* [`throw` Wyrażenia](#throw-expressions)
    - Zgłaszają wyjątki, w konstrukcji kodu, które wcześniej były niedozwolone, ponieważ `throw` został instrukcję. 
* [Uogólniony asynchroniczne typy zwracane](#generalized-async-return-types)
    - Metody zadeklarowane jako z `async` modyfikator może zwrócić inne typy oprócz `Task` i `Task<T>`.
* [Ulepszenia składni literału liczbowego](#numeric-literal-syntax-improvements)
    - Nowe tokeny poprawić czytelność stałych liczbowych.

W pozostałej części w tym temacie omówiono każda z tych funkcji. Dowiesz się jej uzasadnienie, dla każdej funkcji. Dowiesz się składni. Zobaczysz kilka przykładowych scenariuszy, w którym przy użyciu nowej funkcji zwiększyć produktywność deweloperów. 

## <a name="out-variables"></a>`out` zmienne

Istniejące składnię, która obsługuje `out` udoskonalono parametry w tej wersji.  

Wcześniej czy trzeba rozdzielić deklaracji zmiennej poza i inicjowania na dwóch różnych instrukcje:

[!code-csharp[OutVariableOldStyle](../../../samples/snippets/csharp/new-in-7/program.cs#03_OutVariableOldStyle "classic out variable declaration")]

Teraz można zadeklarować `out` zmienne na liście argumentów wywołania metody zamiast redagowanie oddzielne deklaracji:

[!code-csharp[OutVariableDeclarations](../../../samples/snippets/csharp/new-in-7/program.cs#01_OutVariableDeclarations "Out variable declarations")]

Można określić typ `out` zmiennej z myślą o przejrzystości, jak pokazano powyżej. Język obsługuje jednak przy użyciu niejawnie wpisane zmienna lokalna:

[!code-csharp[OutVarVariableDeclarations](../../../samples/snippets/csharp/new-in-7/program.cs#02_OutVarVariableDeclarations "Implicitly typed Out variable")]

* Kod jest bardziej czytelne. 
    - Można zadeklarować zmiennej poza, której używasz, nie w kolejnym wierszu powyżej.
* Nie trzeba przypisać wartość początkową.
    - Przez zadeklarowanie `out` zmiennej w przypadku, gdy jest on używany w wywołaniu metody, nie możesz przypadkowo go użyć przed przypisaniem go.

Najczęściej używane dla tej funkcji będzie `Try` wzorca. W tym wzorcu, metoda zwraca `bool` oznaczający powodzenie lub Niepowodzenie i `out` zmiennej, która zawiera wynik, jeśli metoda zakończy się powodzeniem.

Korzystając z `out` deklaracja zmiennej zadeklarowanej zmiennej "przecieków", w zakresie zewnętrznym, jeśli instrukcja. Dzięki temu można później użyć zmiennej:

```csharp
if (!int.TryParse(input, out int result))
{    
    return null;
}

return result;
```

## <a name="tuples"></a>Krotki

> [!NOTE]
> Nowe funkcje krotek wymagają <xref:System.ValueTuple> typów.
> Należy dodać pakiet NuGet [ `System.ValueTuple` ](https://www.nuget.org/packages/System.ValueTuple/) aby można było używać go na platformach, które nie uwzględniają typów.
>
> Efekt jest podobny do innych funkcji języka, które zależą od typów dostarczane w ramach. Przykład obejmują `async` i `await` polegania na `INotifyCompletion` interfejsu i LINQ polegania na `IEnumerable<T>`. Jednak mechanizm dostarczania zmienia się zgodnie z .NET staje się coraz więcej niezależnie od platformy. .NET Framework nie mogą zawsze dostarczany na tym samym okresach jako kompilatora języka. Gdy nowe funkcje językowe bazuje na nowe typy, te typy będą dostępne jako pakietów NuGet podczas wysłać funkcje języka. Jak te nowe typy dodane do standardowego interfejsu API programu .NET i dostarczane w ramach struktury, wymaganie pakietu NuGet zostaną usunięte.

C# udostępnia bogate składni dla klas i struktur, służący do wyjaśnienia z celem projektu. Jednak czasami tej składni sformatowanego wymaga dodatkowej pracy z minimalnym korzyści. Często może tworzyć metody, które wymagają prostą strukturę zawierających więcej niż jeden element danych. Do obsługi tych scenariuszy *krotek* zostały dodane do języka C#. Spójne kolekcje są struktury lekkie danych, które zawierają wiele pól do reprezentowania elementy członkowskie danych.
Pola nie zostaną sprawdzone, a nie można definiować własnych metod

> [!NOTE]
> Krotki były dostępne przed 7.0 C#, ale zostały nieefektywne i miał Brak obsługi language.
> Oznacza to, że spójnej kolekcji elementów może być przywoływany tylko jako `Item1`, `Item2` i tak dalej. C# w wersji 7.0 wprowadzono obsługę języka krotek, dzięki czemu semantycznego nazwy pól krotka przy użyciu typów nowe, bardziej wydajne spójnej kolekcji.

Przypisywanie wartości do każdego członka można utworzyć spójnych kolekcji:

[!code-csharp[UnnamedTuple](../../../samples/snippets/csharp/new-in-7/program.cs#04_UnnamedTuple "Unnamed tuple")]

Czy przypisania tworzy spójną kolekcję, której członkami są `Item1` i `Item2`, którego można użyć w taki sam sposób jak <xref:System.Tuple> można zmienić składnię, aby utworzyć krotka zawiera semantycznego nazwy do wszystkich członków spójnej kolekcji:

[!code-csharp[NamedTuple](../../../samples/snippets/csharp/new-in-7/program.cs#05_NamedTuple "Named tuple")]

`namedLetters` Krotka zawiera pola określone jako `Alpha` i `Beta`. Nazwy, które istnieją tylko w czasie kompilacji i nie są zachowywane na przykład podczas sprawdzania spójna kolekcja znajdująca się w czasie wykonywania za pomocą odbicia.

W przypisania spójnej kolekcji można również określić nazwy pól po prawej stronie przypisania:

[!code-csharp[ImplicitNamedTuple](../../../samples/snippets/csharp/new-in-7/program.cs#06_ImplicitNamedTuple "Implicitly named tuple")]

Można określić nazwy pól po lewej i prawej stronie przypisania:

[!code-csharp[NamedTupleConflict](../../../samples/snippets/csharp/new-in-7/program.cs#07_NamedTupleConflict "Named tuple conflict")]

Wiersz powyżej generuje ostrzeżenie, `CS8123`, informacją, że nazwy po prawej stronie przypisania, `Alpha` i `Beta` są ignorowane, ponieważ są one w konflikcie z nazwami po lewej stronie `First` i `Second`.

Powyższe przykłady pokazują składnię podstawowe do deklarowania spójnych kolekcji. Spójne kolekcje są najbardziej przydatne jako zwracanych typów `private` i `internal` metody. Krotki zapewniają prosty składnię tych metod zwrócić wielu wartości dyskretnych: zapisywania pracy autorstwa `class` lub `struct` definiuje typ zwracany. Nie istnieje potrzeba do utworzenia nowego typu.

Tworzenie Krotka jest bardziej wydajne i większą wydajność.
Jest to prostsze, lekkie składnia do definiowania struktury danych, który zawiera więcej niż jedną wartość. Przykładowa metoda poniżej zwraca minimalne i maksymalne wartości znajdujących się w sekwencji liczb całkowitych:

[!code-csharp[TupleReturningMethod](../../../samples/snippets/csharp/new-in-7/program.cs#08_TupleReturningMethod "Tuple returning method")]

Przy użyciu spójnych kolekcji w ten sposób zapewnia kilka korzyści:

* Zapisz pracy autorstwa `class` lub `struct` definiuje typ zwracany. 
* Nie trzeba tworzyć nowego typu.
* Funkcje języka eliminuje potrzebę do wywołania <xref:System.Tuple.Create``1(``0)> metody.

Deklaracja metody zawiera nazwy pól spójnej kolekcji, która jest zwracana. Po wywołaniu metody, wartość zwracana jest krotka, których pola są `Max` i `Min`:

[!code-csharp[CallingTupleMethod](../../../samples/snippets/csharp/new-in-7/program.cs#09_CallingTupleMethod "Calling a tuple returning method")]

Może to być razy, aby rozpakować elementów członkowskich spójnej kolekcji, które zostały zwrócone z metody.  Możesz to zrobić przez deklarowania zmiennych osobne dla każdej wartości w spójnej kolekcji. Ta metoda jest wywoływana *deconstructing* spójnej kolekcji:

[!code-csharp[CallingWithDeconstructor](../../../samples/snippets/csharp/new-in-7/program.cs#10_CallingWithDeconstructor "Deconstructing a tuple")]

Można też podać podobne deconstruction dla każdego typu w .NET. Jest to realizowane przez zapisywanie `Deconstruct` metodę jako element członkowski klasy. Czy `Deconstruct` metoda zapewnia zbiór `out` argumenty dla każdej właściwości, które mają zostać wyodrębnione. Należy wziąć pod uwagę to `Point` klasy, która zapewnia metodę deconstructor wyodrębnia `X` i `Y` współrzędne:

[!code-csharp[PointWithDeconstruction](../../../samples/snippets/csharp/new-in-7/point.cs#11_PointWithDeconstruction "Point with deconstruction method")]
 
Można wyodrębnić poszczególnych pól, przypisując `Point` do spójnych kolekcji:

[!code-csharp[DeconstructPoint](../../../samples/snippets/csharp/new-in-7/program.cs#12_DeconstructPoint "Deconstruct a point")]

Nie są powiązane przez nazwy zdefiniowane w `Deconstruct` metody. Możesz zmienić nazwy zmiennych wyodrębniania w ramach przypisania:  

[!code-csharp[DeconstructNames](../../../samples/snippets/csharp/new-in-7/program.cs#13_DeconstructNames "Deconstruct with new names")]

Aby dowiedzieć się więcej w głębokość o spójne kolekcje w [tematu krotek](../tuples.md).

## <a name="discards"></a>Odrzuca

Często zdarza się deconstructing spójnej kolekcji lub wywołanie metody z `out` parametrami, jest wymuszone, aby zdefiniować zmienną, której wartość nie zależy Ci na zachowaniu i nie będą używane. C# dodaje obsługę *odrzuca* do obsługi tego scenariusza. Odrzuć jest tylko do zapisu zmiennej o nazwie `_` (znaku podkreślenia); można przypisać wszystkie wartości, które zamierzasz odrzucić do jednej zmiennej. Odrzuć przypomina nieprzypisanej zmiennej; Oprócz instrukcji przypisania wyrzucania nie można używać w kodzie.

Odrzucenia są obsługiwane w następujących scenariuszach:

* Gdy deconstructing spójne kolekcje lub typy danych zdefiniowane przez użytkownika.

* Podczas wywoływania metody z [limit](../language-reference/keywords/out-parameter-modifier.md) parametrów.

* We wzorcu dopasowania operację, podając [jest](../language-reference/keywords/is.md) i [przełącznika](../language-reference/keywords/switch.md) instrukcje.

* Identyfikatorowi autonomiczny można jawnie Zidentyfikuj wartość przypisania jako odrzucenia.

W poniższym przykładzie zdefiniowano `QueryCityDataForYears` metodę zwracającą 6-spójnych kolekcji zawierający dane miasta dla dwóch różnych lat. Wywołanie metody w tym przykładzie dotyczy tylko wartości populacji dwóch zwracany przez metodę i dlatego traktuje pozostałe wartości w spójnej kolekcji, ponieważ odrzuca, gdy jego deconstructs spójnej kolekcji.

[!code-csharp[Tuple-discard](../../../samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

Aby uzyskać więcej informacji, zobacz [odrzuca](../discards.md).
 
## <a name="pattern-matching"></a>Dopasowanie wzorca

*Dopasowanie wzorca* jest funkcją, która pozwala na wdrożenie metody wysyłania dla właściwości innych niż typ obiektu. Prawdopodobnie już znasz metody wysyłki na podstawie typu obiektu. W obiektowo programowania, wirtualnych i zastąpienie metody udostępniają składni języka Aby zaimplementować metodę wysyłki na podstawie typu obiektu. Podstawowe i pochodne klasy Podaj różnych implementacji. Wyrażenia dopasowania wzorca rozszerzyć to pojęcie, dzięki czemu można łatwo zaimplementować podobne wzorce wysyłania dla typów i danych elementów, które nie są powiązane przez hierarchię dziedziczenia. 

Obsługuje dopasowywania do wzorca `is` wyrażeń i `switch` wyrażenia. Każdy umożliwia zapoznanie się obiekt i jego właściwości, aby ustalić, jeśli ten obiekt spełnia poszukiwaną wzorca. Możesz użyć `when` — słowo kluczowe, aby określić dodatkowe reguły z wzorcem.

### <a name="is-expression"></a>`is` wyrażenie

`is` Wzorzec wyrażenia rozszerza znanych `is` operatora, aby wysłać zapytania do obiektu poza jego typu.

Zacznijmy od prostego scenariusza. Dodamy możliwości tego scenariusza, które pokazują, jak wyrażenia dopasowania wzorca utworzyć algorytmy, które współpracują z niepowiązanych typów łatwe. Zaczniemy metodę, która oblicza sumę liczbą przedstawia struktury:

[!code-csharp[SumDieRolls](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#14_SumDieRolls "Sum die rolls")]

Może szybko znaleźć konieczne Znajdź sumę przedstawia struktury, gdzie część przedstawia wykonane przy użyciu wielu selekcji (w liczbie mnogiej struktury jest selekcji). Część sekwencji wejściowych może być wiele wyników zamiast jeden numer:

[!code-csharp[SumDieRollsWithGroups](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#15_SumDieRollsWithGroups "Sum die rolls with groups")]

`is` Wzorzec wyrażenia działa dość dobrze w tym scenariuszu. W ramach Sprawdzanie typu możesz zapisać zmiennej inicjowania. Spowoduje to utworzenie nowej zmiennej typu zweryfikowanych środowiska wykonawczego.

Jak zachować rozszerzenie tych scenariuszy, może się okazać kompilacji więcej `if` i `else if` instrukcje. Gdy jako niewygodna, prawdopodobnie należy przełączyć się do `switch` wzorzec wyrażenia.

### <a name="switch-statement-updates"></a>`switch` aktualizacje — instrukcja

*Pasuje do wyrażenia* ma zwykłego składni, na podstawie `switch` instrukcji już częścią języka C#. Umożliwia tłumaczenie istniejącego kodu do wyrażenia dopasowania przed dodaniem nowych przypadków: 

[!code-csharp[SumUsingSwitch](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#16_SumUsingSwitch "Sum using switch")]

Wyrażenia dopasowania mają składnię nieco inne niż `is` wyrażeń, których zadeklarować typu i zmiennej na początku `case` wyrażenia.

Wyrażenia dopasowania obsługują także stałe. To umożliwi zaoszczędzenie czasu factoring limit prostych przypadkach:

[!code-csharp[SwitchWithConstants](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#17_SwitchWithConstants "Switch with constants")]

Powyższy kod dodaje przypadków dla `0` w szczególnych przypadkach z `int`, i `null` w szczególnych przypadkach, gdy nie wprowadza żadnych danych. Oznacza to, co ważne, nowej funkcji przełącznika wzorzec wyrażenia: kolejność `case` sprawach teraz wyrażenia. `0` Case musi występować przed ogólne `int` case. W przeciwnym razie będzie pierwszy wzorzec do dopasowania `int` case, nawet wtedy, gdy wartość jest `0`. Jeśli tak, aby obsłużyła już nowszy przypadku przypadkowo kolejność wyrażenia dopasowania, kompilator będzie Flaga, która i generuje błąd.

To samo zachowanie umożliwia szczególnych przypadkach dla pustej sekwencji wejściowych.
Można stwierdzić, że w przypadku `IEnumerable` elementu, który ma elementy musi występować przed ogólne `IEnumerable` case.

Tej wersji dodano również `default` case. `default` Przypadku zawsze jest obliczane ostatnio, niezależnie od tego, kolejność pojawiają się one w źródle. Z tego powodu Konwencji jest umieszczanie `default` ostatnich przypadków.

Na koniec Dodajmy ostatnich jeden `case` dla nowego stylu struktury. Niektóre gry używa selekcji percentyl do reprezentowania zakresów większej liczby. 

> [!NOTE]
> Dwa selekcji dwustronnych 10 percentyl może reprezentować co liczby z zakresu od 0 do 99. Jeden struktury ma boki etykietę `00`, `10`, `20`,... `90`. Inne struktury ma boki etykietą `0`, `1`, `2`,... `9`. Dodaj struktury dwóch wartości ze sobą i można uzyskać co liczby z zakresu od 0 do 99.

Tego rodzaju struktury należy dodać do kolekcji, należy najpierw zdefiniować typu do reprezentowania selekcji percentylu. `TensDigit` Właściwość przechowuje wartości `0`, `10`, `20`, maksymalnie `90`:

[!code-csharp[18_PercentileDice](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#18_PercentileDice "Percentile Die type")]

Następnie należy dodać `case` pasuje do wyrażenia nowego typu:

[!code-csharp[SwitchWithNewTypes](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#19_SwitchWithNewTypes "Include Percentile Die type")]

Nowej składni wyrażeń dopasowywania do wzorca ułatwia tworzenie na podstawie typu obiektu lub inne właściwości, za pomocą składni jasny i zwięzły algorytmów alokacji. Wyrażenia dopasowania wzorca włączenie tych konstrukcji typów danych, które są niepowiązane przez dziedziczenie.

Dowiedz się więcej o wzorzec dopasowany w temacie dedykowany [wzorzec dopasowany w języku C#](../pattern-matching.md).

## <a name="ref-locals-and-returns"></a>Zmienne lokalne ref i zwraca

Ta funkcja umożliwia algorytmy, które używają i zwracać odwołań do zmiennych zdefiniowany w innym miejscu. Przykładem jest praca z dużą macierzy i znajdowanie pojedynczej lokalizacji, z niektórych właściwości. Jedna metoda zwróci dwa indeksów dla pojedynczej lokalizacji w macierzy:

[!code-csharp[FindReturningIndices](../../../samples/snippets/csharp/new-in-7/MatrixSearch.cs#20_FindReturningIndices "Find returning indices")]

Istnieje wiele problemów z tego kodu. Przede wszystkim jest publiczną metodę, która zwraca spójnych kolekcji. Język obsługuje tę, ale typy zdefiniowane przez użytkownika (klasy lub struktury) są preferowane dla publicznych interfejsach API.

Po drugie ta metoda zwraca wskaźników do elementu w macierzy.
Prowadzi to obiekty wywołujące do pisania kodu, który używa tych wskaźników do wyłuskania macierzy i modyfikowania pojedynczego elementu:

[!code-csharp[UpdateItemFromIndices](../../../samples/snippets/csharp/new-in-7/program.cs#21_UpdateItemFromIndices "Update Item From Indices")]

Czy raczej napisanie metody, która zwraca *odwołania* do elementu macierzy, który chcesz zmienić. Tylko można to zrobić za pomocą niebezpieczny kod i zwracany jest wskaźnik do `int` w poprzednich wersjach.

Przejdźmy szereg zmian prezentacja funkcji lokalnej ref i pokazują, jak utworzyć metodę, która zwraca odwołanie do wewnętrznej pamięci masowej.
Na bieżąco dowiesz się reguły zwracane ref i funkcji lokalnych ref, który zapobiega przypadkowemu niewłaściwie korzysta.

Uruchom modyfikując `Find` deklaracji metody, dzięki czemu zwraca `ref int` zamiast spójnych kolekcji. Następnie należy zmodyfikować instrukcji return, tak aby zwracało do wartości przechowywanej w macierzy zamiast dwóch wskaźników:

```csharp
// Note that this won't compile. 
// Method declaration indicates ref return,
// but return statement specifies a value return.
public static ref int Find2(int[,] matrix, Func<int, bool> predicate)
{
    for (int i = 0; i < matrix.GetLength(0); i++)
        for (int j = 0; j < matrix.GetLength(1); j++)
            if (predicate(matrix[i, j]))
                return matrix[i, j];
    throw new InvalidOperationException("Not found");
}
```

Gdy zadeklarować zwracanych metody `ref` zmiennej, musisz również dodać `ref` — słowo kluczowe do każdej instrukcji return. Wskazuje, że zwracanie przez odwołanie, a pomaga deweloperom odczytywania kod później należy pamiętać, że metoda zwraca wartość przez odwołanie:

[!code-csharp[FindReturningRef](../../../samples/snippets/csharp/new-in-7/MatrixSearch.cs#22_FindReturningRef "Find returning by reference")]

Teraz, metoda zwraca odwołanie do wartości całkowitej w macierzy, należy zmodyfikować, gdzie jest wywoływany.  `var` Deklaracji oznacza, że `valItem` jest teraz `int` zamiast spójnych kolekcji:

[!code-csharp[AssignRefReturnToValue](../../../samples/snippets/csharp/new-in-7/program.cs#23_AssignRefReturnToValue "Assign ref return to value")]

Drugi `WriteLine` instrukcji w powyższym przykładzie do drukowania wartość `42`, a nie `24`. Zmienna `valItem` jest `int`, a nie `ref int`. `var` — Słowo kluczowe włącza kompilator, aby określić typ, ale nie dodają niejawnie `ref` modyfikator. Zamiast tego wartość odwołuje się `ref return` jest *skopiowane* do zmiennej po lewej stronie przypisania. Zmienna nie jest `ref` lokalnego.

Aby uzyskać wynik ma, musisz dodać `ref` modyfikator do deklaracji zmiennej lokalnej podczas wartość zwracana jest odwołanie do zmiennej podjąć odwołanie:

[!code-csharp[AssignRefReturn](../../../samples/snippets/csharp/new-in-7/program.cs#24_AssignRefReturn "Assign ref return")]

Teraz, drugi `WriteLine` instrukcji w powyższym przykładzie zostanie wydrukowana wartość `24`, wskazujący, że magazynu w macierzy został zmodyfikowany. Zmienna lokalna została zadeklarowana z `ref` potrwa modyfikator, a `ref` zwracany. Należy zainicjować `ref` zmiennej, gdy jest on zadeklarowany jako, nie można podzielić deklaracji i inicjowania.

W języku C# ma trzy innych reguł, które można chronić przed używaniem `ref` zmiennych lokalnych i zwraca:

* Nie można przypisać wartości zwracanej standardowe metody do `ref` zmiennej lokalnej.
    - Która uniemożliwia instrukcje, takie jak `ref int i = sequence.Count();`
* Nie można zwrócić `ref` ze zmienną, której czas życia nie wykracza poza wykonywanie metody.
    - Oznacza to, że nie można zwrócić odwołanie do zmiennej lokalnej lub zmienna o podobnych zakresu.
* `ref` Nie można używać zmiennych lokalnych i zwraca i metod asynchronicznych.
    - Kompilator nie wiadomo, jeśli przywoływany została ustawiona zmienna do swojej własnej wartości końcowej po powrocie z metody asynchronicznej.

Dodawanie ref zmiennych lokalnych i ref zwraca Włącz algorytmy, które są bardziej wydajne, unikając kopiowania wartości lub operacji usuwania odwołań wiele razy. 

## <a name="local-functions"></a>Funkcje lokalne

Wiele projektów dla klas obejmują liczbę metod wywoływanych z tylko jedną lokalizację. Te dodatkowe metody prywatnej Zachowaj każdej metody niewielkiego i skupionego projektu. Jednak ich może utrudnić zrozumieć klasy podczas odczytywania go po raz pierwszy. Te metody musi być rozumiane poza kontekstem pojedynczej lokalizacji wywołującego.

Dla tych projektów *funkcje lokalne* można zadeklarować metody w kontekście innej metody. Ułatwia dla czytników klasę, aby zobaczyć tylko wywołać metody lokalnego z kontekst, w którym jest on zadeklarowany.

Istnieją dwa bardzo typowe przypadki użycia funkcje lokalne: metody iteracyjne publicznego i metod asynchronicznych publicznego. Oba typy metod do generowania kodu później niż programiści mogą wymagać raporty błędów. W przypadku metody iteracyjne, wszelkie wyjątki są przestrzegane tylko podczas wywoływania kodu, który wylicza zwrócony sekwencji. W przypadku metod asynchronicznych, wyjątki są zauważalne tylko podczas zwróconego `Task` jest oczekiwane.

Zacznijmy od metodę iteratora:

[!code-csharp[IteratorMethod](../../../samples/snippets/csharp/new-in-7/Iterator.cs#25_IteratorMethod "Iterator method")]

Sprawdź poniższy kod, który wywołuje metodę iteratora niepoprawnie:

[!code-csharp[CallIteratorMethod](../../../samples/snippets/csharp/new-in-7/program.cs#26_CallIteratorMethod "Call iterator method")]

Wyjątek jest zgłaszany, gdy `resultSet` jest iterowane, nie po `resultSet` jest tworzony.
W tym przykładzie zawartych w niej większość deweloperów można szybko zdiagnozowania problemu. Jednak w większych codebases, kod, który tworzy iteratora często nie jest maksymalnie zbliżony kod, który wylicza wynik. Kod może Refaktoryzuj publicznego metoda weryfikuje wszystkie argumenty, a metoda prywatna generuje wyliczenie:

[!code-csharp[IteratorMethodRefactored](../../../samples/snippets/csharp/new-in-7/Iterator.cs#27_IteratorMethodRefactored "Iterator method refactored")]

Ta wersja refactored zgłosi wyjątki od razu, ponieważ metoda publiczna, nie jest metodą iteratora; Metoda prywatna używa `yield return` składni. Istnieją jednak potencjalne problemy z tym refaktoryzacji. Metoda prywatna tylko należy wywoływać z metody interfejsu publicznego, ponieważ w przeciwnym razie jest pomijana wszystkich argumentów.
Czytniki klasy muszą zostać odnalezione ten fakt odczytywania całej klasy i wyszukując odwołań do `alphabetSubsetImplementation` metody.

Celem tego projektu można wprowadzać więcej wyczyść przez zadeklarowanie `alphabetSubsetImplementation` jako funkcja lokalna wewnątrz publicznej metody interfejsu API:

[!code-csharp[22_IteratorMethodLocal](../../../samples/snippets/csharp/new-in-7/Iterator.cs#28_IteratorMethodLocal "Iterator method with local function")]

Powyżej wersji ułatwia wyczyść do którego odwołuje się lokalną metodę tylko w kontekście zewnętrzną metodę. Zasady lokalne funkcje upewnij się również projektant nie może przypadkowo wywołanie funkcji lokalnej z innej lokalizacji w klasie i pominąć weryfikacji argumentu.

Można zastosować tę samą metodę z `async` metod, aby upewnić się, że wynikające z walidacji argumentów istnieją wyjątki zgłaszane przed rozpoczęciem pracy asynchronicznych:

[!code-csharp[TaskExample](../../../samples/snippets/csharp/new-in-7/AsyncWork.cs#29_TaskExample "Task returning method with local function")]

> [!NOTE]
> Niektóre projekty, które są obsługiwane przez funkcje lokalne może być również wykonywane przy użyciu *wyrażenia lambda*. Można te zainteresowanych [Dowiedz się więcej na temat różnic](../local-functions-vs-lambdas.md)

## <a name="more-expression-bodied-members"></a>Zabudowanych wyrażenia elementów członkowskich

C# 6 wprowadzone [zabudowanych wyrażenia elementów członkowskich](csharp-6.md#expression-bodied-function-members) dla funkcji Członkowskich i właściwości tylko do odczytu. C# 7.0 rozszerza dozwolonych elementów członkowskich, które można zaimplementować jako wyrażenia. W języku C# w wersji 7.0, można zaimplementować *konstruktorów*, *finalizatory*, i `get` i `set` metody dostępu na *właściwości* i *indeksatorów* . Poniższy kod przedstawia przykłady każdego z nich:

[!code-csharp[ExpressionBodiedMembers](../../../samples/snippets/csharp/new-in-7/expressionmembers.cs#36_ExpressionBodiedEverything "new expression-bodied members")]

> [!NOTE]
> W tym przykładzie finalizator nie jest konieczne, ale jest ona wyświetlana aby zademonstrować składni. Nie powinny implementować finalizator w klasie, chyba że jest to konieczne zwolnić zasoby niezarządzane. Należy również rozważyć użycie <xref:System.Runtime.InteropServices.SafeHandle> klasy zamiast bezpośrednio zarządzania zasoby niezarządzane.

Nowe lokalizacje dla członków zabudowanych wyrażenie reprezentuje ważne punktu kontrolnego dla języka C#: te funkcje zostały zaimplementowane przez członków społeczności pracuje open source [Roslyn](https://github.com/dotnet/Roslyn) projektu.

## <a name="throw-expressions"></a>Wyrażenia throw

W języku C# `throw` zawsze było instrukcję. Ponieważ `throw` jest instrukcję nie wyrażenia, zostały C# konstrukcje, których nie można go. Uwzględniane są wyrażenia warunkowe null wyrażenia łączącego i niektóre wyrażenia lambda. Dodawanie członków zabudowanych wyrażenie dodaje więcej lokalizacji gdzie `throw` byłoby wyrażenia. Aby mogły zapisywać żadnego z tych konstrukcji, C# w wersji 7.0 wprowadzono *wyrażenia throw*.

Składnia jest taki sam, jak zawsze była używana dla `throw` instrukcje. Jedyną różnicą jest to, że teraz można umieścić je w nowej lokalizacji, takich jak w wyrażeniu warunkowym:

[!code-csharp[Throw_ExpressionExample](../../../samples/snippets/csharp/new-in-7/throwexpressions.cs#37_Throw_ExpressionExample "conditional throw expressions")]

W wyrażeniach inicjowania przy użyciu wyrażenia throw umożliwia to funkcji:

[!code-csharp[ThrowInInitialization](../../../samples/snippets/csharp/new-in-7/throwexpressions.cs#38_ThrowInInitialization "conditional throw expressions")]

Wcześniej te inicjalizacji musi być w konstruktorze, instrukcji throw w treści konstruktora:


[!code-csharp[ThrowInConstructor](../../../samples/snippets/csharp/new-in-7/throwexpressions.cs#39_ThrowInConstructor "throw statements")]

> [!NOTE]
> Obu powyższych konstrukcje spowoduje, że wyjątki, aby zostać wygenerowany podczas konstruowania obiektu. Te są często trudno odzyskanie.
> Z tego powodu nie są zalecane projektów, które zgłaszają wyjątki podczas konstruowania.

## <a name="generalized-async-return-types"></a>Uogólniony asynchroniczne typy zwracane

Zwracanie `Task` obiektu z metod asynchronicznych może wprowadzić wąskich gardeł wydajności w niektórych ścieżki. `Task` jest typem referencyjnym, aby za jej pomocą oznacza przydzielanie obiektu. W przypadkach, gdy metoda zadeklarowana z `async` modyfikator zwraca buforowanych wyników lub jest kończona synchronicznie, dodatkowe alokacje może stać się koszt długiego czasu w wydajności krytyczne fragmentów kodu. Może stać się bardzo kosztowna tych przydziałów występują w ścisłej pętle.

Nowa funkcja języka oznacza, że metody asynchroniczne może zwracać inne typy oprócz `Task`, `Task<T>` i `void`. Zwrócony typ nadal muszą spełniać wzorca asynchronicznego, co oznacza `GetAwaiter` metody muszą być dostępne. Jako przykład konkretnych `ValueTask` typu został dodany do programu .NET framework, aby korzystać z tej nowej funkcji języka: 

[!code-csharp[UsingValueTask](../../../samples/snippets/csharp/new-in-7/AsyncWork.cs#30_UsingValueTask "Using ValueTask")]

> [!NOTE]
> Konieczne jest dodanie pakietu NuGet [ `System.Threading.Tasks.Extensions` ](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) aby można było używać <xref:System.Threading.Tasks.ValueTask%601> typu.

Jest używany prosty optymalizacji `ValueTask` w miejscach gdzie `Task` będzie służyć przed. Jednak jeśli chcesz ręcznie przeprowadzić dodatkowe optymalizacje można buforować wyniki pracy async i ponowne użycie wynik w kolejnych wywołaniach. `ValueTask` Struktury ma konstruktora z `Task` parametru, dzięki czemu można konstruować `ValueTask` z wartość zwracaną przez wszystkie istniejące metody asynchronicznej:

[!code-csharp[AsyncOptimizedValueTask](../../../samples/snippets/csharp/new-in-7/AsyncWork.cs#31_AsyncOptimizedValueTask "Return async result or cached value")]
 
Zgodnie z wszystkie zalecenia wydajności, należy pytanie obie wersje przed wprowadzeniem dużej skali zmieni się na kodzie.

## <a name="numeric-literal-syntax-improvements"></a>Ulepszenia składni literału liczbowego

Stałe numeryczne misreading może utrudnić zrozumienie kodu podczas odczytywania go po raz pierwszy. To często występuje, gdy te liczby są używane jako maski bitowej lub innych symboliczne zamiast wartości liczbowych. C# 7.0 zawiera dwie nowe funkcje ułatwiające zapisu liczb w najbardziej czytelne sposób z przeznaczeniem: *binarne literały*, i *separatory cyfr*.

Podczas tworzenia maski bitowej lub zawsze, gdy to binarna reprezentacja liczby czasów powoduje kodu najbardziej do odczytu, zapisu tego numeru w binarnym:

[!code-csharp[BinaryConstants](../../../samples/snippets/csharp/new-in-7/Program.cs#32_BinaryConstants "Binary constants")]

`0b` Na początku stała wskazuje, że numer jest zapisywane jako wartości binarnej.

Binarne wartości można uzyskać bardzo długi, więc jest często widoczność dzięki zastosowaniu wzorce bit `_` jako separator cyfr:

[!code-csharp[ThousandSeparators](../../../samples/snippets/csharp/new-in-7/Program.cs#33_ThousandSeparators "Thousands separators")]

Separator cyfr może występować w dowolnym miejscu w stałej. W przypadku podstawowej 10 numerów byłoby wspólne, aby używać go jako tysięcy separatora:

[!code-csharp[LargeIntegers](../../../samples/snippets/csharp/new-in-7/Program.cs#34_LargeIntegers "Large integer")]

Separator cyfr, może być używany z `decimal`, `float` i `double` również typy:

[!code-csharp[OtherConstants](../../../samples/snippets/csharp/new-in-7/Program.cs#35_OtherConstants "non-integral constants")]

Razem można zadeklarować stałe numeryczne z większą czytelności.

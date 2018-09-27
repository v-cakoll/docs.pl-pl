---
title: Co nowego w języku C# 7.0 — przewodnik po języku C#
description: Zapoznaj się z omówieniem nowych funkcji, które zostaną dodane w przyszłych wersji języka C# 7.
ms.date: 12/21/2016
ms.assetid: fd41596d-d0c2-4816-b94d-c4d00a5d0243
ms.openlocfilehash: 734fdf962ef481a3b434e9ce17e535eadd52f420
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/26/2018
ms.locfileid: "47237387"
---
# <a name="whats-new-in-c-70"></a>Co nowego w języku C# 7.0

C# 7.0 dodaje wiele nowych funkcji do języka C#:
* [`out` Zmienne](#out-variables)
    - Można zadeklarować `out` wartości wbudowanych jako argumenty do metody, gdzie są używane.
* [Krotki](#tuples)
    - Można tworzyć lekkie, bez nazwy typów, które zawierają wiele pola publiczne. Kompilatory i narzędzia IDE zrozumieć semantykę tych typów.
* [Odrzucenia](#discards)
    - Odrzuca są tymczasowego, tylko do zapisu zmienne używane w przypisania, jeśli nie dba o wartość przypisana. Są one szczególnie przydatne podczas dekonstrukcja krotek i typy zdefiniowane przez użytkownika, a także podczas wywoływania metody z `out` parametrów.
* [Dopasowanie do wzorca](#pattern-matching)
    - Można utworzyć logikę rozgałęziania, na podstawie dowolnego typu i wartości elementów członkowskich tych typów.
* [`ref` Zmienne lokalne i](#ref-locals-and-returns)
    - Argumenty metody i zmienne lokalne mogą być odwołania do innego magazynu.
* [Funkcje lokalne](#local-functions)
    - Można zagnieżdżać funkcji w innych funkcjach, aby ograniczyć ich zakres i widoczność.
* [Więcej elementy członkowskie z wyrażeniem](#more-expression-bodied-members)
    - Zwiększył się listę elementów członkowskich, które można tworzyć za pomocą wyrażeń.
* [`throw` Wyrażenia](#throw-expressions)
    - W konstrukcji kodu, które wcześniej były niedozwolona, ponieważ może generować wyjątki `throw` został instrukcję. 
* [Uogólnionego asynchroniczne typy zwracane](#generalized-async-return-types)
    - Metody zadeklarowane za pomocą `async` modyfikator może zwrócić inne typy oprócz `Task` i `Task<T>`.
* [Ulepszenia składni literału liczbowego](#numeric-literal-syntax-improvements)
    - Nowe tokeny poprawić czytelność dla stałych numerycznych.

W pozostałej części tego tematu omawia każdej funkcji. Dowiesz się jej uzasadnienie, dla każdej funkcji. Dowiesz się, aby składnia. Zobaczysz niektóre przykładowe scenariusze, w którym przy użyciu nowej funkcji pozwalają zwiększyć produktywność dla deweloperów. 

## <a name="out-variables"></a>`out` Zmienne

Istniejące składnia, która obsługuje `out` parametry została ulepszona w tej wersji.  

Wcześniej należy oddzielić deklaracja zmiennej poza i inicjacji w dwóch różnych instrukcji:

[!code-csharp[OutVariableOldStyle](../../../samples/snippets/csharp/new-in-7/program.cs#03_OutVariableOldStyle "classic out variable declaration")]

Możesz teraz zadeklarować `out` zmiennych w liście argumentów wywołania metody, zamiast pisania instrukcji deklaracji oddzielnych:

[!code-csharp[OutVariableDeclarations](../../../samples/snippets/csharp/new-in-7/program.cs#01_OutVariableDeclarations "Out variable declarations")]

Możesz chcieć określić typ `out` zmiennych w celu uściślenia, jak pokazano powyżej. Język obsługuje jednak przy użyciu niejawnie typizowanej zmiennej lokalnej:

[!code-csharp[OutVarVariableDeclarations](../../../samples/snippets/csharp/new-in-7/program.cs#02_OutVarVariableDeclarations "Implicitly typed Out variable")]

* Kod jest łatwiejsza do odczytania. 
    - Można zadeklarować zmiennej poza, której używasz, nie w kolejnym wierszu powyżej.
* Nie ma potrzeby, aby przypisać wartość początkową.
    - DEKLARUJĄC `out` zmiennej, w przypadku, gdy jest używany w wywołaniu metody, nie można przypadkowo używać go przed przypisaniem go.

Będzie najczęściej używane dla tej funkcji `Try` wzorca. W tym wzorcu, metoda zwraca `bool` oznaczający powodzenie lub Niepowodzenie i `out` zmienna, która zapewnia wynik, jeśli metoda zakończy się powodzeniem.

Korzystając z `out` deklaracja zmiennej zadeklarowanej zmiennej "przecieków", do zakresu zewnętrznego, jeśli instrukcja. Dzięki temu można później użyć zmiennej:

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
> Należy dodać pakiet NuGet [ `System.ValueTuple` ](https://www.nuget.org/packages/System.ValueTuple/) aby można było używać go na platformach, które nie zawierają typy.
>
> Jest to podobne do innych funkcji języka, które zależą od typów dostarczonych w ramach. Przykład obejmują `async` i `await` opierając się na `INotifyCompletion` interfejsu i LINQ, opierając się na `IEnumerable<T>`. Jednak mechanizm dostarczania jest zmieniają się wraz z .NET staje się coraz więcej platform niezależne. .NET Framework mogą zawsze są dostarczane na ten sam cykl, jak kompilator języka. Jeśli nowe funkcje języka, zależą od nowych typów, te typy są dostępne jako pakiety NuGet podczas dostarczania funkcji języka. Ponieważ te nowe typy są dodawane do standardowego interfejsu API platformy .NET i dostarczane jako część ram, wymaganie pakietu NuGet zostaną usunięte.

C# zapewnia rozbudowane składni klas i struktur, który służy do wyjaśnienia intencji Twojego projektu. Jednak czasami takiej składni sformatowanego wymaga dodatkowej pracy dzięki korzyściom z minimalnym. Często mogą zapisywać metod wymagających prostą strukturę zawierających więcej niż jednego elementu danych. Do obsługi tych scenariuszy *krotek* zostały dodane do języka C#. Kolekcje są strukturami danych uproszczone, zawierające wiele pól do reprezentowania składowych danych.
Pola nie są weryfikowane i nie można definiować własnych metod.

> [!NOTE]
> Spójne kolekcje były dostępne przed języka C# 7.0, ale zostały mało wydajne i miał Brak obsługi języka.
> Oznacza to, że elementy krotki mogą być przywoływane tylko jako `Item1`, `Item2` i tak dalej. C# 7.0 wprowadza obsługę krotek, co umożliwia semantycznego nazwy pól krotki przy użyciu typy krotki nowe, bardziej wydajne.

Możesz utworzyć krotki przez przypisywanie wartości do każdego elementu członkowskiego:

[!code-csharp[UnnamedTuple](../../../samples/snippets/csharp/new-in-7/program.cs#04_UnnamedTuple "Unnamed tuple")]

Przypisanie spowoduje utworzenie spójnej kolekcji, której członkami są `Item1` i `Item2`, którego można używać w taki sam sposób jak <xref:System.Tuple> można zmienić składnię tworzenia spójną kolekcją, która zawiera semantyczną nazwy do każdego z członków spójna kolekcja znajdująca się:

[!code-csharp[NamedTuple](../../../samples/snippets/csharp/new-in-7/program.cs#05_NamedTuple "Named tuple")]

`namedLetters` Krotka zawiera pola określone jako `Alpha` i `Beta`. Te nazwy istnieje tylko w czasie kompilacji i nie są zachowywane w przykładzie, podczas sprawdzania spójna kolekcja znajdująca się w czasie wykonywania przy użyciu odbicia.

W przypisaniu spójnej kolekcji można również określić nazwy pól po prawej stronie przypisania:

[!code-csharp[ImplicitNamedTuple](../../../samples/snippets/csharp/new-in-7/program.cs#06_ImplicitNamedTuple "Implicitly named tuple")]

Po lewej i prawej stronie przypisania, można określić nazwy pól:

[!code-csharp[NamedTupleConflict](../../../samples/snippets/csharp/new-in-7/program.cs#07_NamedTupleConflict "Named tuple conflict")]

Wiersz powyżej generuje ostrzeżenie, `CS8123`, informacją, że nazwy po prawej stronie przypisania, `Alpha` i `Beta` są ignorowane, ponieważ są w konflikcie z nazwami po lewej stronie `First` i `Second`.

W powyższych przykładach podstawowa składnia do deklarowania krotek. Kolekcje są najbardziej przydatne jako typów zwracanych dla `private` i `internal` metody. Krotek zapewnia prostą składnię dla tych metod zwrócić wiele wartości dyskretnych: zapisywania pracy tworzenia `class` lub `struct` definiujący typ zwracany. Nie ma potrzeby tworzenia nowego typu.

Utworzenie spójnej kolekcji jest wydajniejsze i bardziej produktywne.
Jest prostsze, lekki Składnia umożliwiająca zdefiniowanie struktury danych, który zawiera więcej niż jedną wartość. Przykładowa metoda poniżej zwraca minimalne i maksymalne wartości znajdujących się w sekwencji liczb całkowitych:

[!code-csharp[TupleReturningMethod](../../../samples/snippets/csharp/new-in-7/program.cs#08_TupleReturningMethod "Tuple returning method")]

Możliwość korzystania z krotek w ten sposób oferuje kilka dodatkowych korzyści:

* Zapisywanie pracy tworzenia `class` lub `struct` definiujący typ zwracany. 
* Nie trzeba tworzyć nowego typu.
* Ulepszenia języka eliminuje konieczność kontaktowania się z <xref:System.Tuple.Create``1(``0)> metody.

W deklaracji metody udostępnia nazwy pól spójną kolekcją, która jest zwracana. Po wywołaniu metody, wartość zwracana jest spójna kolekcja, w których pola są `Max` i `Min`:

[!code-csharp[CallingTupleMethod](../../../samples/snippets/csharp/new-in-7/program.cs#09_CallingTupleMethod "Calling a tuple returning method")]

Mogą wystąpić sytuacje, gdy zachodzi potrzeba rozpakować elementy członkowskie spójnej kolekcji, które zostały zwrócone z metody.  Możecie od zadeklarowania zmiennych osobne dla każdej wartości w spójnej kolekcji. Jest to nazywane *dekonstrukcja* spójnej kolekcji:

[!code-csharp[CallingWithDeconstructor](../../../samples/snippets/csharp/new-in-7/program.cs#10_CallingWithDeconstructor "Deconstructing a tuple")]

Możesz też podać podobne dekonstrukcja dla dowolnego typu na platformie .NET. Jest to realizowane przez zapisywanie `Deconstruct` metodę jako składową klasy. Czy `Deconstruct` metoda zawiera zbiór `out` argumenty dla każdej właściwości, które mają zostać wyodrębnione. Należy wziąć pod uwagę to `Point` klasę, która zapewnia metody deconstructor, która wyodrębnia `X` i `Y` współrzędnych:

[!code-csharp[PointWithDeconstruction](../../../samples/snippets/csharp/new-in-7/point.cs#11_PointWithDeconstruction "Point with deconstruction method")]
 
Można wyodrębnić poszczególne pola, przypisując `Point` do krotki:

[!code-csharp[DeconstructPoint](../../../samples/snippets/csharp/new-in-7/program.cs#12_DeconstructPoint "Deconstruct a point")]

Nie są powiązane przez nazwy zdefiniowane w `Deconstruct` metody. W ramach przypisania, można zmienić nazwy zmiennych wyodrębniania:  

[!code-csharp[DeconstructNames](../../../samples/snippets/csharp/new-in-7/program.cs#13_DeconstructNames "Deconstruct with new names")]

Możesz dowiedzieć się w bardziej szczegółowe informacje o krotek w [tematu krotek](../tuples.md).

## <a name="discards"></a>Odrzuca

Często podczas dekonstrukcja krotki lub wywołanie metody z `out` parametrami, jest zmuszony do definiowania zmiennej z żądanymi wartościami nie interesuje i nie będą używane. C# dodaje obsługę *odrzuca* do obsługi tego scenariusza. Odrzucenia to zmienna tylko do zapisu, którego nazwa jest `_` (znaki podkreślenia); można przypisać wszystkie wartości, które zamierzasz odrzucić do jednej zmiennej. Odrzucenia przypomina nieprzypisanej zmiennej; Oprócz instrukcji przypisania odrzuceń, nie można użyć w kodzie.

Odrzuca są obsługiwane w następujących scenariuszach:

* Gdy dekonstrukcja krotek lub typy zdefiniowane przez użytkownika.

* Podczas wywoływania metody z [się](../language-reference/keywords/out-parameter-modifier.md) parametrów.

* We wzorcu, dopasowanie operację, podając [jest](../language-reference/keywords/is.md) i [Przełącz](../language-reference/keywords/switch.md) instrukcji.

* Jako identyfikator autonomicznej, aby jawnie Zidentyfikuj wartość do przypisania jako odrzucenia.

W poniższym przykładzie zdefiniowano `QueryCityDataForYears` metodę, która zwraca 6-spójną kolekcją, która zawiera dane jako uczestnik w mieście dla dwóch różnych lat. Wywołanie metody w przykładzie dotyczy tylko wartości dwóch populacji zwracany przez metodę i dlatego traktuje pozostałe wartości w spójnej kolekcji, ponieważ odrzuca, gdy jej deconstructs spójnej kolekcji.

[!code-csharp[Tuple-discard](../../../samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

Aby uzyskać więcej informacji, zobacz [odrzuca](../discards.md).

## <a name="pattern-matching"></a>Dopasowanie wzorca

*Dopasowanie wzorca* jest funkcją, która pozwala na implementowanie metody wysyłania we właściwościach innych niż typ obiektu. Prawdopodobnie znasz metodę alokacji na podstawie typu obiektu. W obiektowo programowania, wirtualnych i zastąpienie metody zapewniają składnię języka, aby zaimplementować metodę wysyłania na podstawie typu obiektu. Podstawowe i pochodne klasy dostarczać różne implementacje. Wyrażenia dopasowania wzorca rozszerzyć tę koncepcję, dzięki czemu można łatwo zaimplementować podobnych wzorców wysyłania dla typów i danych elementów, które nie są powiązane przez hierarchię dziedziczenia. 

Obsługa dopasowania do wzorca `is` wyrażeń i `switch` wyrażenia. Każdy umożliwia zapoznanie się obiekt i jego właściwości w celu stwierdzenia, jeśli ten obiekt spełnia wzorzec używanych. Możesz użyć `when` — słowo kluczowe, aby określić dodatkowe reguły do wzorca.

### <a name="is-expression"></a>`is` Wyrażenie

`is` Wyrażenia wzorca rozszerza znanej `is` operator, aby wysłać zapytania do obiektu poza jego typu.

Zacznijmy od prostego scenariusza. Dodamy możliwości tego scenariusza, które pokazują, jak wzorzec dopasowywania wyrażeniach algorytmów, współpracujących z niepowiązanych typy proste. Rozpoczniemy od metody, która oblicza sumę liczby ustala struktury:

[!code-csharp[SumDieRolls](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#14_SumDieRolls "Sum die rolls")]

Może szybko się okazać konieczne obliczający sumę ustala struktury, w której niektóre ustala są przekazywane przy użyciu wielu dice (dice jest struktury w liczbie mnogiej). Część sekwencji wejściowych może być wiele wyników, zamiast jednego numeru:

[!code-csharp[SumDieRollsWithGroups](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#15_SumDieRollsWithGroups "Sum die rolls with groups")]

`is` Wyrażenia wzorca działa bardzo dobrze w tym scenariuszu. W ramach Sprawdzanie typu można napisać inicjalizacji zmiennej. Spowoduje to utworzenie nowej zmiennej typu zweryfikowanych środowiska uruchomieniowego.

Jak zachować rozszerzenie tych scenariuszy, może się okazać Konstruuj więcej `if` i `else if` instrukcji. Gdy stanie się nieporęczny, prawdopodobnie należy przełączyć się do `switch` wzorca wyrażenia.

### <a name="switch-statement-updates"></a>`switch` aktualizacje — instrukcja

*Pasuje do wyrażenia* ma dobrze znanej składni, w oparciu o `switch` instrukcja jest już częścią języka C#. Umożliwia tłumaczenie istniejącego kodu do wyrażenia dopasowania przed dodaniem nowych przypadków: 

[!code-csharp[SumUsingSwitch](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#16_SumUsingSwitch "Sum using switch")]

Wyrażenia dopasowania mają nieco składnią niż `is` wyrażenia, gdzie możesz deklarować typ i zmiennej na początku `case` wyrażenia.

Wyrażenia dopasowania również obsługiwać stałe. Aby zaoszczędzić czas, to wyprowadzenie się proste przypadki:

[!code-csharp[SwitchWithConstants](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#17_SwitchWithConstants "Switch with constants")]

Powyższy kod dodaje przypadków `0` w szczególnych przypadkach z `int`, i `null` w szczególnych przypadkach, gdy nie wprowadza żadnych danych. W tym przykładzie pokazano jeden nową ważną funkcję w wyrażeniach wzorzec przełącznika: kolejność `case` sprawach teraz wyrażeń. `0` Case musi występować przed ogólnym `int` przypadek. W przeciwnym razie byłoby pierwszy wzorzec do dopasowania `int` przypadku, nawet wtedy, gdy wartość jest `0`. Jeśli taki sposób, że w przypadku nowszych została już obsłużona przypadkowo kolejność wyrażenia dopasowań, kompilator będzie Flaga, która i wygenerowanie błędu.

To takie samo zachowanie umożliwia specjalne przypadku pustą sekwencją danych wejściowych.
Możesz zobaczyć, że w przypadku `IEnumerable` element, który ma elementów musi występować przed ogólnym `IEnumerable` przypadek.

Tej wersji dodano również `default` przypadek. `default` Przypadek jest obliczane zawsze ostatnio, niezależnie od kolejności pojawiają się one w źródle. Z tego powodu Konwencji polega na umieszczeniu `default` ostatniego wielkości liter.

Na koniec możemy dodać jeden ostatni `case` dla nowego stylu struktury. Niektóre gry umożliwia dice percentyl reprezentują większych zakresy liczb. 

> [!NOTE]
> Dwa dice dwustronna 10 percentylu mogą reprezentować każdy numer z zakresu od 0 do 99. Struktury co ma boki oznakowane `00`, `10`, `20`,... `90`. Inne struktury ma boki etykietą `0`, `1`, `2`,... `9`. Dodaj wartości dwie struktury ze sobą, a każdy numer można uzyskać z zakresu od 0 do 99.

Aby dodać tego rodzaju struktury do kolekcji, należy najpierw zdefiniować typu reprezentującego dice percentyl. `TensDigit` Właściwość przechowuje wartości `0`, `10`, `20`, maksymalnie `90`:

[!code-csharp[18_PercentileDice](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#18_PercentileDice "Percentile Die type")]

Następnie należy dodać `case` pasuje do wyrażenia dla nowego typu:

[!code-csharp[SwitchWithNewTypes](../../../samples/snippets/csharp/new-in-7/patternmatch.cs#19_SwitchWithNewTypes "Include Percentile Die type")]

Składnia nowych wyrażeniach dopasowania do wzorca ułatwia tworzenie algorytmów alokacji na podstawie typu obiektu lub innych właściwości, za pomocą składni bardziej czytelne i zwięzłe. Wyrażenia dopasowania wzorca Włącz te konstrukcje na typy danych, które są niezwiązanych ze sobą przez dziedziczenie.

Dowiedz się więcej o dopasowywaniu do wzorca w temacie dedykowane [dopasowywania wzorca w języku C#](../pattern-matching.md).

## <a name="ref-locals-and-returns"></a>Zmienne lokalne ref i zwraca

Ta funkcja umożliwia algorytmy, które używają i zwracać odwołań do zmiennych określonych gdzie indziej. Przykładem jest praca z macierzy dużych i znajdowanie w jednej lokalizacji, z określoną wspólną charakterystykę. Jedna metoda zwróci dwa indeksy dla jednej lokalizacji w macierzy:

[!code-csharp[FindReturningIndices](../../../samples/snippets/csharp/new-in-7/MatrixSearch.cs#20_FindReturningIndices "Find returning indices")]

Istnieje wiele problemów przy użyciu tego kodu. Przede wszystkim jest publiczną metodę, która zwraca spójną kolekcję. Język obsługuje to jednak typów zdefiniowanych przez użytkownika (klasy lub struktury) są preferowane dla publicznych interfejsów API.

Po drugie ta metoda zwraca wskaźników do elementów w macierzy.
Prowadzi to obiekty wywołujące do pisania kodu, który używa tych indeksów w celu wyłuskania macierzy i modyfikowania pojedynczego elementu:

[!code-csharp[UpdateItemFromIndices](../../../samples/snippets/csharp/new-in-7/program.cs#21_UpdateItemFromIndices "Update Item From Indices")]

Należy zamiast napisać metodę, która zwraca *odwołania* do elementu macierzy, który chcesz zmienić. Tylko można to osiągnąć, używając niebezpieczny kod i zwraca wskaźnik do `int` w poprzednich wersjach.

Przejdźmy teraz przez szereg zmian, które przedstawiono tu funkcji lokalnego odwołania i pokazują, jak utworzyć metodę, która zwraca odwołanie do pamięci wewnętrznej.
Po drodze dowiesz się regułami zwracane ref i funkcji lokalnych ref, która chroni przypadkowym niewłaściwie korzysta.

Rozpoczynanie pracy od modyfikowania `Find` deklaracji metody, tak że zwraca `ref int` zamiast spójnej kolekcji. Następnie zmodyfikuj instrukcję return, tak aby zwracało poprawnie wartość przechowywaną w macierzy, zamiast dwóch wskaźników:

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

Kiedy Deklarujesz, metoda zwraca `ref` zmiennych, musisz również dodać `ref` — słowo kluczowe do każdej instrukcji return. Oznacza to zwracanie przez odwołanie, a następnie pomaga deweloperom czytania dalszej części kodu, należy pamiętać, że metoda zwraca wartość przez odwołanie:

[!code-csharp[FindReturningRef](../../../samples/snippets/csharp/new-in-7/MatrixSearch.cs#22_FindReturningRef "Find returning by reference")]

Teraz, metoda zwraca odwołanie do wartości całkowitej w macierzy, należy zmodyfikować, gdzie jest wywoływana.  `var` Deklaracji oznacza, że `valItem` jest teraz `int` zamiast spójnej kolekcji:

[!code-csharp[AssignRefReturnToValue](../../../samples/snippets/csharp/new-in-7/program.cs#23_AssignRefReturnToValue "Assign ref return to value")]

Drugi `WriteLine` instrukcja w powyższym przykładzie drukuje się wartość `42`, a nie `24`. Zmienna `valItem` jest `int`, a nie `ref int`. `var` — Słowo kluczowe umożliwia kompilatorowi określić typ, ale nie spowoduje dodanie niejawnie `ref` modyfikator. Zamiast tego wartość odwołuje się `ref return` jest *skopiowane* do zmiennej po lewej stronie przypisania. Zmienna nie jest `ref` lokalnego.

Aby uzyskać wynik ma, musisz dodać `ref` modyfikatora deklaracji zmiennej lokalnej do ustaw dla zmiennej odwołania, gdy wartość zwracana jest odwołanie:

[!code-csharp[AssignRefReturn](../../../samples/snippets/csharp/new-in-7/program.cs#24_AssignRefReturn "Assign ref return")]

Teraz, drugi `WriteLine` instrukcja w powyższym przykładzie zostanie wydrukowana wartość `24`, wskazującą, czy zostały zmodyfikowane magazynu w macierzy. Zmienna lokalna została zadeklarowana przy użyciu `ref` modyfikator i potrwa `ref` powrócić. Należy zainicjować `ref` zmiennej gdy jest on zadeklarowany, nie można podzielić deklaracji i inicjowania.

W języku C# ma trzy inne reguły, które można chronić przed używaniem `ref` zmiennych lokalnych i zwraca:

* Nie można przypisać wartość zwracaną standardową metodę, aby `ref` zmiennej lokalnej.
    - Które nie zezwalają na instrukcjach, takich jak `ref int i = sequence.Count();`
* Nie można zwrócić `ref` do zmiennej, którego okres istnienia nie wykracza poza wykonywanie metody.
    - Oznacza to, że nie można zwrócić odwołanie do zmiennej lokalnej lub zmienną o zakresie podobne.
* `ref` Zmienne lokalne i nie można używać metod asynchronicznych.
    - Kompilator nie wiadomo, jeśli przywoływany została ustawiona zmienna końcowej wartości po powrocie z metody asynchronicznej.

Zmienne lokalne ref i ref zwraca algorytmy Włącz, które są bardziej wydajne, unikając kopiowania wartości lub wykonywanie operacji dereferencji wiele razy.

Dodawanie `ref` wartość zwracana jest [źródła zmiany zgodne](version-update-considerations.md#source-compatible-changes). Kompiluje istniejący kod, ale odwołania zwracana wartość jest kopiowany po przypisaniu. Obiekty wywołujące muszą zaktualizować magazyn dla zwracanej wartości `ref` zmienną lokalną, aby przechowywać zwracany jako odwołanie.

## <a name="local-functions"></a>Funkcje lokalne

Wiele projektów dla klasy zawierają metody, które są wywoływane z tylko jedną lokalizację. Te dodatkowe metody prywatnej Zachowaj każdej metody niewielkiego i skupionego projektu. Jednak ich może utrudnić zrozumienie klasę, odczytując je po raz pierwszy. Te metody musi być rozumiane poza kontekstem jednej lokalizacji wywoływania.

Te projekty *funkcje lokalne* umożliwiają deklarowanie metody w kontekście innej metody. To ułatwia czytelnicy klasy, aby zobaczyć tylko wywołać metody lokalnej z kontekstu, w którym jest zadeklarowana.

Istnieją dwa przypadki użycia bardzo często dla funkcji lokalnych: metody iteratora publicznych i metod asynchronicznych publicznych. Oba rodzaje metod wygenerować kod, który zgłasza błędy nowsze niż programiści mogą oczekiwać. W przypadku metody iteracyjne wszelkie wyjątki pojawiają się tylko podczas wywoływania kodu, który wylicza zwracanej sekwencji. W przypadku metod asynchronicznych wyjątków tylko obserwuje się kiedy zwracanego `Task` jest oczekiwane.

Zacznijmy od metody iteratora:

[!code-csharp[IteratorMethod](../../../samples/snippets/csharp/new-in-7/Iterator.cs#25_IteratorMethod "Iterator method")]

Sprawdź poniższy kod, który wywołuje metodę iteratora niepoprawnie:

[!code-csharp[CallIteratorMethod](../../../samples/snippets/csharp/new-in-7/program.cs#26_CallIteratorMethod "Call iterator method")]

Wyjątek jest generowany, gdy `resultSet` jest postanowiliśmy, nie po `resultSet` zostanie utworzony.
W tym przykładzie zawartej większość deweloperów może szybko zdiagnozować problem. Jednak w większych bazach kodu, kod, który tworzy iterator, często nie jest zbliżony kod, który wylicza wynik. Tak, aby publiczny metoda sprawdza wszystkie argumenty i metody prywatnej generuje wyliczenia mogą refaktoryzować kod:

[!code-csharp[IteratorMethodRefactored](../../../samples/snippets/csharp/new-in-7/Iterator.cs#27_IteratorMethodRefactored "Iterator method refactored")]

Ta wersja wycofanej będzie zgłaszają wyjątki od razu, ponieważ metoda publiczna nie jest metodą iteratora; używa metody prywatnej `yield return` składni. Jednak istnieją potencjalne problemy z tej refaktoryzacji. Metoda prywatna tylko powinna być wywoływana z metody interfejsu publicznego, ponieważ w przeciwnym razie całej walidacji argument zostanie pominięty.
Czytelnicy klasy ten fakt muszą zostać odnalezione, odczytując całej klasy i wyszukiwania odwołań do `alphabetSubsetImplementation` metody.

Umożliwia tym przeznaczeniem projektowania bardziej zrozumiałe przez zadeklarowanie `alphabetSubsetImplementation` jako funkcja lokalna wewnątrz publicznej metody interfejsu API:

[!code-csharp[22_IteratorMethodLocal](../../../samples/snippets/csharp/new-in-7/Iterator.cs#28_IteratorMethodLocal "Iterator method with local function")]

Wersja powyżej sprawia, że wyczyść przywoływanymi lokalną metodę tylko w kontekście metodzie zewnętrznej. Reguły dotyczące funkcji lokalnych upewnij się, Projektant nie może przypadkowo wywołania funkcji lokalnej z innej lokalizacji w klasie i pominąć walidacji argumentów.

Można zastosować za pomocą tej samej techniki `async` metod w celu zapewnienia, że wynikające z walidacji argumentów zgłaszania wyjątków przed rozpoczęciem pracy asynchronicznej:

[!code-csharp[TaskExample](../../../samples/snippets/csharp/new-in-7/AsyncWork.cs#29_TaskExample "Task returning method with local function")]

> [!NOTE]
> Niektóre projekty, które są obsługiwane przez funkcje lokalne mogą być również wykonywane przy użyciu *wyrażeń lambda*. Te zainteresowane można [Dowiedz się więcej o różnicach](../local-functions-vs-lambdas.md)

## <a name="more-expression-bodied-members"></a>Więcej elementy członkowskie z wyrażeniem

C# 6 wprowadzono [elementy członkowskie z wyrażeniem](csharp-6.md#expression-bodied-function-members) dla elementów członkowskich i właściwości tylko do odczytu. C# 7.0 rozwija dozwolonych elementów członkowskich, które można zaimplementować jako wyrażenia. W języku C# 7.0, można zaimplementować *konstruktory*, *finalizatory*, i `get` i `set` metod dostępu na *właściwości* i *indeksatorów* . Poniższy kod przedstawia przykłady każdego z nich:

[!code-csharp[ExpressionBodiedMembers](../../../samples/snippets/csharp/new-in-7/expressionmembers.cs#36_ExpressionBodiedEverything "new expression-bodied members")]

> [!NOTE]
> W tym przykładzie nie potrzebuje finalizatora, jednak wyświetleniem pokazano składnię. Nie należy implementować finalizator w klasie, chyba że jest to niezbędne zwolnić niezarządzane zasoby. Należy również rozważyć użycie <xref:System.Runtime.InteropServices.SafeHandle> klasy zamiast na zarządzaniu bezpośrednio niezarządzane zasoby.

Te nowe lokalizacje dla elementy członkowskie z wyrażeniem reprezentują ważnym kamieniem milowym dla języka C#: te funkcje zostały zaimplementowane przez członków społeczności nad typu open-source [Roslyn](https://github.com/dotnet/Roslyn) projektu.

Zmiana metody do elementu członkowskiego zabudowanego wyrażenie jest [binarne zmiany zgodne](version-update-considerations.md#binary-compatible-changes).

## <a name="throw-expressions"></a>Wyrażeń throw

W języku C# `throw` zawsze było instrukcję. Ponieważ `throw` znajduje się zdanie, nie wyrażenia, były konstrukcji języka C#, w których nie można go. Uwzględnione są niektóre wyrażenia lambda, wyrażenia warunkowe i wyrażenia łączące wartości null. Dodanie elementy członkowskie z wyrażeniem dodanie większej liczby lokalizacji gdzie `throw` wyrażeń może okazać się przydatne. Dzięki czemu można tworzyć dowolne te konstrukcje, C# 7.0 wprowadza *wyrażeń throw*.

Składnia jest taka sama jak zawsze użytej w przypadku `throw` instrukcji. Jedyną różnicą jest to, że teraz można umieścić je w nowej lokalizacji, takich jak w wyrażeniu warunkowym:

[!code-csharp[Throw_ExpressionExample](../../../samples/snippets/csharp/new-in-7/throwexpressions.cs#37_Throw_ExpressionExample "conditional throw expressions")]

Umożliwia używanie wyrażenia throw w wyrażeniach inicjacji to funkcje:

[!code-csharp[ThrowInInitialization](../../../samples/snippets/csharp/new-in-7/throwexpressions.cs#38_ThrowInInitialization "conditional throw expressions")]

Wcześniej te inicjalizacje musi być w konstruktorze, za pomocą instrukcji throw w treści konstruktora:


[!code-csharp[ThrowInConstructor](../../../samples/snippets/csharp/new-in-7/throwexpressions.cs#39_ThrowInConstructor "throw statements")]

> [!NOTE]
> Zarówno konstrukcji poprzedniego spowoduje, że wyjątki zostanie wygenerowany podczas konstruowania obiektu. Te są często trudne do sprawności.
> Z tego powodu zaleca się projekty, które zgłaszają wyjątki podczas konstruowania.

## <a name="generalized-async-return-types"></a>Uogólnionego asynchroniczne typy zwracane

Zwracanie `Task` obiekt z metody asynchronicznej może prowadzić do wąskich gardeł wydajności w niektórych ścieżek. `Task` jest typem referencyjnym, więc za jego pomocą oznacza przydzielanie obiektu. W przypadkach, w którym metoda jest zadeklarowana za pomocą `async` modyfikator zwraca wynik pamięci podręcznej lub zakończeniu synchronicznie, dodatkowe alokacji może stać się koszt znaczną ilość czasu, w sekcji krytycznych wydajność kodu. Mogą stać się bardzo kosztowna, jeśli te przydziały występują w ścisłej pętli.

Nowa funkcja języka oznacza, że metody asynchroniczne mogą zwracać inne typy oprócz `Task`, `Task<T>` i `void`. Zwrócony typ nadal musi spełniać wzorca asynchronicznego, co oznacza `GetAwaiter` metody muszą być dostępne. Przykład jednego konkretnego `ValueTask` typ został dodany do programu .NET framework, aby skorzystać z tej nowej funkcji języka: 

[!code-csharp[UsingValueTask](../../../samples/snippets/csharp/new-in-7/AsyncWork.cs#30_UsingValueTask "Using ValueTask")]

> [!NOTE]
> Dodaj pakiet NuGet [ `System.Threading.Tasks.Extensions` ](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) aby można było używać <xref:System.Threading.Tasks.ValueTask%601> typu.

Proste optymalizacji byłoby użycie `ValueTask` w miejscach gdzie `Task` będzie używana przed. Jednak jeśli chcesz ręcznie przeprowadzić dodatkowe optymalizacje, można buforować wyniki z Praca asynchroniczna i wielokrotnie używać wyników w kolejnych wywołaniach. `ValueTask` Struktura ma konstruktora z `Task` parametru, aby można skonstruować `ValueTask` z wartość zwracaną metody asynchronicznej, wszelkie istniejące:

[!code-csharp[AsyncOptimizedValueTask](../../../samples/snippets/csharp/new-in-7/AsyncWork.cs#31_AsyncOptimizedValueTask "Return async result or cached value")]

Zgodnie z wszystkich zaleceń dotyczących wydajności należy benchmark obie wersje przed wprowadzeniem dużych skalowania zmiany w kodzie.

Jeśli wartość zwracana jest elementem docelowym `await` instrukcji, zmiana interfejsu API z poziomu <xref:System.Threading.Tasks.Task%601> do <xref:System.Threading.Tasks.ValueTask%601> jest [źródła zmiany zgodne](version-update-considerations.md#source-compatible-changes). Ogólnie rzecz biorąc, zmiana `ValueTask` nie jest.

## <a name="numeric-literal-syntax-improvements"></a>Ulepszenia składni literału liczbowego

Misreading stałych numerycznych może utrudnić rozumienie kodu, odczytując je po raz pierwszy. Często dzieje się tak po tych dwóch liczb służą jako masek bitowych lub innych symbolicznego zamiast wartości liczbowych. C# 7.0 zawiera dwie nowe funkcje, aby ułatwić zapisywać liczby w najbardziej czytelny sposób związane z zamierzonym użyciem: *literały binarne*, i *separatory cyfr*.

Czasów podczas tworzenia masek bitowych lub zawsze wtedy, gdy binarna reprezentacja liczby sprawia, że najbardziej czytelne kodu, zapisać tę liczbę w pliku binarnego:

[!code-csharp[BinaryConstants](../../../samples/snippets/csharp/new-in-7/Program.cs#32_BinaryConstants "Binary constants")]

`0b` Na początku stała wskazuje, że liczba jest zapisywany jako wartości binarnej.

Binarne wartości można uzyskać bardzo długie, więc jest często łatwiej zobaczyć wzorców bitowych, wprowadzając `_` jako separator cyfr:

[!code-csharp[ThousandSeparators](../../../samples/snippets/csharp/new-in-7/Program.cs#33_ThousandSeparators "Thousands separators")]

Separator cyfr może występować w dowolnym miejscu w stałej. W przypadku podstawowej liczb 10, będzie często używa się tysięcy separatora:

[!code-csharp[LargeIntegers](../../../samples/snippets/csharp/new-in-7/Program.cs#34_LargeIntegers "Large integer")]

Separator cyfr, może być używany z `decimal`, `float` i `double` również typy:

[!code-csharp[OtherConstants](../../../samples/snippets/csharp/new-in-7/Program.cs#35_OtherConstants "non-integral constants")]

Razem wzięte, można zadeklarować stałych numerycznych za pomocą znacznie więcej czytelności.

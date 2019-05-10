---
title: Co nowego w języku C# 7.0 — przewodnik po języku C#
description: Zapoznaj się z omówieniem nowych funkcji w wersji 7.0 C# języka.
ms.date: 02/20/2019
ms.assetid: fd41596d-d0c2-4816-b94d-c4d00a5d0243
ms.openlocfilehash: 942a126ae026897d608c9fb077fc5f10ff73c110
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64753061"
---
# <a name="whats-new-in-c-70"></a>Co nowego w języku C# 7.0

C# 7.0 dodaje wiele nowych funkcji do języka C#:
* [`out` Zmienne](#out-variables)
  - Można zadeklarować `out` wartości wbudowanych jako argumenty do metody, gdzie są używane.
* [Krotki](#tuples)
  - Można tworzyć lekkie, bez nazwy typów, które zawierają wiele pola publiczne. Kompilatory i narzędzia IDE zrozumieć semantykę tych typów.
* [Odrzucenia](#discards)
  - Odrzuca są tymczasowego, tylko do zapisu zmienne używane w przypisania, jeśli nie dba o wartość przypisana. Są one najbardziej użyteczne, gdy dekonstrukcja krotek i typy zdefiniowane przez użytkownika, a także podczas wywoływania metody z `out` parametrów.
* [Dopasowanie do wzorca](#pattern-matching)
  - Można utworzyć logikę rozgałęziania, na podstawie dowolnego typu i wartości elementów członkowskich tych typów.
* [`ref` Zmienne lokalne i](#ref-locals-and-returns)
  - Metoda zmienne lokalne i wartości zwracane mogą być odwołania do innych magazynów.
* [Funkcje lokalne](#local-functions)
  - Można zagnieżdżać funkcji w innych funkcjach, aby ograniczyć ich zakres i widoczność.
* [Więcej elementy członkowskie z wyrażeniem](#more-expression-bodied-members)
  - Zwiększył się listę elementów członkowskich, które można tworzyć za pomocą wyrażeń.
* [`throw` Expressions](#throw-expressions)
  - W konstrukcji kodu, które wcześniej nie były dozwolone, ponieważ może generować wyjątki `throw` został instrukcję.
* [Uogólnionego asynchroniczne typy zwracane](#generalized-async-return-types)
  - Metody zadeklarowane za pomocą `async` modyfikator może zwrócić inne typy oprócz `Task` i `Task<T>`.
* [Ulepszenia składni literału liczbowego](#numeric-literal-syntax-improvements)
  - Nowe tokeny poprawić czytelność dla stałych numerycznych.

W dalszej części tego artykułu zawiera omówienie każdej funkcji. Dowiesz się jej uzasadnienie, dla każdej funkcji. Dowiesz się, aby składnia. Możesz zapoznać się z tych funkcji w naszej [możliwość interaktywnego eksplorowania](../tutorials/exploration/csharp-7.yml) z tych funkcji.

## <a name="out-variables"></a>`out` Zmienne

Istniejące składnia, która obsługuje `out` parametry została ulepszona w tej wersji. Możesz teraz zadeklarować `out` zmiennych w liście argumentów wywołania metody, zamiast pisania instrukcji deklaracji oddzielnych:

[!code-csharp[OutVariableDeclarations](~/samples/snippets/csharp/new-in-7/program.cs#OutVariableDeclarations "Out variable declarations")]

Możesz chcieć określić typ `out` zmiennych w celu uściślenia, jak pokazano powyżej. Język obsługuje jednak przy użyciu niejawnie typizowanej zmiennej lokalnej:

[!code-csharp[OutVarVariableDeclarations](~/samples/snippets/csharp/new-in-7/program.cs#OutVarVariableDeclarations "Implicitly typed Out variable")]

* Kod jest łatwiejsza do odczytania.
  - Można zadeklarować zmiennej poza, której używasz, nie w kolejnym wierszu powyżej.
* Nie ma potrzeby, aby przypisać wartość początkową.
  - DEKLARUJĄC `out` zmiennej, w przypadku, gdy jest używany w wywołaniu metody, nie można przypadkowo używać go przed przypisaniem go.

## <a name="tuples"></a>Krotki

C# zapewnia rozbudowane składni klas i struktur, który służy do wyjaśnienia intencji Twojego projektu. Jednak czasami takiej składni sformatowanego wymaga dodatkowej pracy dzięki korzyściom z minimalnym. Często mogą zapisywać metod wymagających prostą strukturę zawierających więcej niż jednego elementu danych. Do obsługi tych scenariuszy *krotek* zostały dodane do języka C#. Kolekcje są strukturami danych uproszczone, zawierające wiele pól do reprezentowania składowych danych.
Pola nie są weryfikowane i nie można definiować własnych metod.

> [!NOTE]
> Spójne kolekcje były dostępne przed języka C# 7.0, ale zostały mało wydajne i miał Brak obsługi języka.
> Oznacza to, że elementy krotki mogą być przywoływane tylko jako `Item1`, `Item2` i tak dalej. C# 7.0 wprowadza obsługę krotek, co umożliwia semantycznego nazwy pól krotki przy użyciu typy krotki nowe, bardziej wydajne.

Możesz utworzyć krotki przez przypisywanie wartości do każdego członka i opcjonalnie podania semantycznego nazwy do każdego z członków spójnej kolekcji:

[!code-csharp[NamedTuple](~/samples/snippets/csharp/new-in-7/program.cs#NamedTuple "Named tuple")]

`namedLetters` Krotka zawiera pola określone jako `Alpha` i `Beta`. Te nazwy istnieje tylko w czasie kompilacji i nie są zachowywane, na przykład podczas sprawdzania spójna kolekcja znajdująca się w czasie wykonywania przy użyciu odbicia.

W przypisaniu spójnej kolekcji można również określić nazwy pól po prawej stronie przypisania:

[!code-csharp[ImplicitNamedTuple](~/samples/snippets/csharp/new-in-7/program.cs#ImplicitNamedTuple "Implicitly named tuple")]

Mogą wystąpić sytuacje, gdy zachodzi potrzeba rozpakować elementy członkowskie spójnej kolekcji, które zostały zwrócone z metody.  Możecie od zadeklarowania zmiennych osobne dla każdej wartości w spójnej kolekcji. Nazywa się to rozpakowywania *dekonstrukcja* spójnej kolekcji:

[!code-csharp[CallingWithDeconstructor](~/samples/snippets/csharp/new-in-7/program.cs#CallingWithDeconstructor "Deconstructing a tuple")]

Możesz też podać podobne dekonstrukcja dla dowolnego typu na platformie .NET. Piszesz `Deconstruct` metodę jako składową klasy. Czy `Deconstruct` metoda zawiera zbiór `out` argumenty dla każdej właściwości, które mają zostać wyodrębnione. Należy wziąć pod uwagę to `Point` klasę, która zapewnia metody deconstructor, która wyodrębnia `X` i `Y` współrzędnych:

[!code-csharp[PointWithDeconstruction](~/samples/snippets/csharp/new-in-7/point.cs#PointWithDeconstruction "Point with deconstruction method")]

Można wyodrębnić poszczególne pola, przypisując `Point` do krotki:

[!code-csharp[DeconstructPoint](~/samples/snippets/csharp/new-in-7/program.cs#DeconstructPoint "Deconstruct a point")]

Możesz dowiedzieć się w bardziej szczegółowe informacje o krotek w [artykułu krotek](../tuples.md).

## <a name="discards"></a>Odrzuca

Często podczas dekonstrukcja krotki lub wywołanie metody z `out` parametrami, jest zmuszony do definiowania zmiennej z żądanymi wartościami nie interesuje i nie będą używane. C# dodaje obsługę *odrzuca* do obsługi tego scenariusza. Odrzucenia to zmienna tylko do zapisu, którego nazwa jest `_` (znaki podkreślenia); można przypisać wszystkie wartości, które zamierzasz odrzucić do jednej zmiennej. Odrzucenia przypomina nieprzypisanej zmiennej; Oprócz instrukcji przypisania odrzuceń, nie można użyć w kodzie.

Odrzuca są obsługiwane w następujących scenariuszach:

* Gdy dekonstrukcja krotek lub typy zdefiniowane przez użytkownika.
* Podczas wywoływania metody z [się](../language-reference/keywords/out-parameter-modifier.md) parametrów.
* We wzorcu, dopasowanie operację, podając [jest](../language-reference/keywords/is.md) i [Przełącz](../language-reference/keywords/switch.md) instrukcji.
* Jako identyfikator autonomicznej, aby jawnie Zidentyfikuj wartość do przypisania jako odrzucenia.

W poniższym przykładzie zdefiniowano `QueryCityDataForYears` metodę, która zwraca 6-spójną kolekcją, która zawiera dane jako uczestnik w mieście dla dwóch różnych lat. Wywołanie metody w przykładzie dotyczy tylko wartości dwóch populacji zwracany przez metodę i dlatego traktuje pozostałe wartości w spójnej kolekcji, ponieważ odrzuca, gdy jej deconstructs spójnej kolekcji.

[!code-csharp[Tuple-discard](~/samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

Aby uzyskać więcej informacji, zobacz [odrzuca](../discards.md).

## <a name="pattern-matching"></a>Dopasowanie do wzorca

*Dopasowanie wzorca* jest funkcją, która pozwala na implementowanie metody wysyłania we właściwościach innych niż typ obiektu. Prawdopodobnie znasz metodę alokacji na podstawie typu obiektu. Programowanie zorientowane obiektowo, wirtualnych i zastąpienie metody zawiera składni języka, aby zaimplementować metodę wysyłania na podstawie typu obiektu. Podstawowe i pochodne klasy dostarczać różne implementacje.
Wyrażenia dopasowania wzorca rozszerzyć tę koncepcję, dzięki czemu można łatwo zaimplementować podobnych wzorców wysyłania dla typów i elementów danych, które nie są powiązane przez hierarchię dziedziczenia.

Obsługa dopasowania do wzorca `is` wyrażeń i `switch` wyrażenia. Każdy umożliwia zapoznanie się obiekt i jego właściwości w celu stwierdzenia, jeśli ten obiekt spełnia wzorzec używanych. Możesz użyć `when` — słowo kluczowe, aby określić dodatkowe reguły do wzorca.

`is` Wyrażenia wzorca rozszerza znanej [ `is` operator](../language-reference/keywords/is.md#pattern-matching-with-is) można wysłać zapytania do obiektu o jej typ i przypisz wynik w jednej instrukcji. Poniższy kod umożliwia sprawdzenie, czy zmienna `int`, a jeśli tak, dodaje ją do sumy bieżącej:

```csharp
if (input is int count)
    sum += count;
```

Ulepszenia pokazano w powyższym przykładzie małych `is` wyrażenia. Możesz przetestować względem typów wartości, a także typy odwołań i pomyślnego wyniku można przypisać do nowej zmiennej poprawnego typu.

Wyrażenie dopasowania przełącznika ma dobrze znanej składni, w oparciu o `switch` instrukcja jest już częścią C# języka. Instrukcja switch zaktualizowane ma kilka nowych konstrukcji:

- Typ zarządzania `switch` wyrażenia nie jest już ograniczony do typów całkowitych `Enum` typów `string`, lub typ dopuszczający wartość null, jednego z tych typów. Dowolny typ mogą być używane.
- Możesz przetestować typ `switch` wyrażenie w każdym `case` etykiety. Podobnie jak w przypadku `is` wyrażenie nowej zmiennej może przypisać do tego typu.
- Możesz dodać `when` klauzuli w celu dalszego testowania warunków w tej zmiennej.
- Kolejność `case` ważne jest teraz etykiety. Pierwszej gałęzi, aby dopasować jest wykonywana. inne są pomijane.

Poniższy kod demonstruje te nowe funkcje:

```csharp
public static int SumPositiveNumbers(IEnumerable<object> sequence)
{
    int sum = 0;
    foreach (var i in sequence)
    {
        switch (i)
        {
            case 0:
                break;
            case IEnumerable<int> childSequence:
            {
                foreach(var item in childSequence)
                    sum += (item > 0) ? item : 0;
                break;
            }
            case int n when n > 0:
                sum += n;
                break;
            case null:
                throw new NullReferenceException("Null found in sequence");
            default:
                throw new InvalidOperationException("Unrecognized type");
        }
    }
    return sum;
}
```

- `case 0:` jest dobrze znanych wzór stałej.
- `case IEnumerable<int> childSequence:` jest to wzorzec typu.
- `case int n when n > 0:` jest to wzorzec typu przy użyciu dodatkowego `when` warunku.
- `case null:` jest wzorcem o wartości null.
- `default:` jest to przypadek domyślny znanych.

Dowiedz się więcej na temat dopasowywania do wzorca w [wzorzec dopasowywania w C# ](../pattern-matching.md).

## <a name="ref-locals-and-returns"></a>Zmienne lokalne ref i zwraca

Ta funkcja umożliwia algorytmy, które używają i zwracać odwołań do zmiennych określonych gdzie indziej. Przykładem jest praca z macierzy dużych i znajdowanie w jednej lokalizacji, z określoną wspólną charakterystykę. Zwraca następującą metodę **odwołania** do tego magazynu w macierzy:

[!code-csharp[FindReturningRef](~/samples/snippets/csharp/new-in-7/MatrixSearch.cs#FindReturningRef "Find returning by reference")]

Można zadeklarować wartość zwracana jako `ref` i zmodyfikować tę wartość w macierzy, jak pokazano w poniższym kodzie:

[!code-csharp[AssignRefReturn](~/samples/snippets/csharp/new-in-7/Program.cs#AssignRefReturn "Assign ref return")]

C# Język ma kilka reguł, które można chronić przed używaniem `ref` zmiennych lokalnych i zwraca:

* Należy dodać `ref` słowa kluczowego w podpisie metody i do wszystkich `return` instrukcji w metodzie.
  - Dzięki temu clear, metoda zwraca wartość przez odwołanie w całej metody.
* A `ref return` można przypisać do zmiennej wartości lub `ref` zmiennej.
  - Obiekt wywołujący kontroluje, czy wartość zwracana jest kopiowana, czy nie. Pominięcie `ref` modyfikator podczas przypisywania zwracana wartość wskazuje, że obiekt wywołujący chce kopię wartości, a nie odwołanie do magazynu.
* Nie można przypisać wartość zwracaną standardową metodę, aby `ref` zmiennej lokalnej.
  - Które nie zezwalają na instrukcjach, takich jak `ref int i = sequence.Count();`
* Nie można zwrócić `ref` do zmiennej, którego okres istnienia nie wykracza poza wykonywanie metody.
  - Oznacza to, że nie można zwrócić odwołanie do zmiennej lokalnej lub zmienną o zakresie podobne.
* `ref` Zmienne lokalne i nie można używać metod asynchronicznych.
  - Kompilator nie wiadomo, jeśli przywoływany została ustawiona zmienna końcowej wartości po powrocie z metody asynchronicznej.

Dodatkowo zmienne lokalne ref i ref zwraca umożliwia algorytmy, które są bardziej wydajne, unikając kopiowania wartości lub wykonywanie operacji dereferencji wiele razy.

Dodawanie `ref` wartość zwracana jest [źródła zmiany zgodne](version-update-considerations.md#source-compatible-changes). Kompiluje istniejący kod, ale odwołania zwracana wartość jest kopiowany po przypisaniu. Obiekty wywołujące muszą zaktualizować magazyn dla zwracanej wartości `ref` zmienną lokalną, aby przechowywać zwracany jako odwołanie.

Aby uzyskać więcej informacji, zobacz [ref — słowo kluczowe](../language-reference/keywords/ref.md) artykułu.

## <a name="local-functions"></a>Funkcje lokalne

Wiele projektów dla klasy zawierają metody, które są wywoływane z tylko jedną lokalizację. Te dodatkowe metody prywatnej Zachowaj każdej metody niewielkiego i skupionego projektu. *Funkcje lokalne* umożliwiają deklarowanie metody w kontekście innej metody. Funkcje lokalne ułatwiają czytelnicy klasy wyświetlić tylko wywołać lokalnego metody z kontekstu, w którym jest zdeklarowana.

Istnieją dwie typowe przypadki użycia dla funkcji lokalnych: metody iteratora publicznych i metod asynchronicznych publicznych. Oba rodzaje metod wygenerować kod, który zgłasza błędy nowsze niż programiści mogą oczekiwać. W metodzie iteratora wszelkie wyjątki pojawiają się tylko podczas wywoływania kodu, który wylicza zwracanej sekwencji. W metodach asynchronicznych wyjątków tylko obserwuje się kiedy zwracanego `Task` jest oczekiwane. W poniższym przykładzie pokazano oddzielający Walidacja parametru od implementacji iteratora, przy użyciu funkcji lokalnego:

[!code-csharp[22_IteratorMethodLocal](~/samples/snippets/csharp/new-in-7/Iterator.cs#IteratorMethodLocal "Iterator method with local function")]

Można zastosować za pomocą tej samej techniki `async` metod w celu zapewnienia, że wynikające z walidacji argumentów zgłaszania wyjątków przed rozpoczęciem pracy asynchronicznej:

[!code-csharp[TaskExample](~/samples/snippets/csharp/new-in-7/AsyncWork.cs#TaskExample "Task returning method with local function")]

> [!NOTE]
> Niektóre projekty, które są obsługiwane przez funkcje lokalne mogą być również wykonywane przy użyciu *wyrażeń lambda*. Te zainteresowane można [Dowiedz się więcej o różnicach](../local-functions-vs-lambdas.md)

## <a name="more-expression-bodied-members"></a>Więcej elementy członkowskie z wyrażeniem

C# 6 wprowadzono [elementy członkowskie z wyrażeniem](csharp-6.md#expression-bodied-function-members) dla elementów członkowskich i właściwości tylko do odczytu. C# 7.0 rozwija dozwolonych elementów członkowskich, które można zaimplementować jako wyrażenia. W języku C# 7.0, można zaimplementować *konstruktory*, *finalizatory*, i `get` i `set` metod dostępu na *właściwości* i *indeksatorów* . Poniższy kod przedstawia przykłady każdego z nich:

[!code-csharp[ExpressionBodiedMembers](~/samples/snippets/csharp/new-in-7/expressionmembers.cs#ExpressionBodiedEverything "new expression-bodied members")]

> [!NOTE]
> W tym przykładzie nie potrzebuje finalizatora, jednak wyświetleniem pokazano składnię. Nie należy implementować finalizator w klasie, chyba że jest to niezbędne zwolnić niezarządzane zasoby. Należy również rozważyć użycie <xref:System.Runtime.InteropServices.SafeHandle> klasy zamiast na zarządzaniu bezpośrednio niezarządzane zasoby.

Te nowe lokalizacje dla elementy członkowskie z wyrażeniem reprezentują ważnym kamieniem milowym dla C# języka: Te funkcje zostały zaimplementowane przez członków społeczności nad typu open-source [Roslyn](https://github.com/dotnet/Roslyn) projektu.

Zmiana metody do elementu członkowskiego zabudowanego wyrażenie jest [binarne zmiany zgodne](version-update-considerations.md#binary-compatible-changes).

## <a name="throw-expressions"></a>Wyrażenia throw

W języku C# `throw` zawsze było instrukcję. Ponieważ `throw` jest instrukcją nie wyrażenie wystąpiły C# konstrukcje, których nie używasz go. Uwzględnione są niektóre wyrażenia lambda, wyrażenia warunkowe i wyrażenia łączące wartości null. Dodanie elementy członkowskie z wyrażeniem dodanie większej liczby lokalizacji gdzie `throw` wyrażeń może okazać się przydatne. Dzięki czemu można tworzyć dowolne te konstrukcje, C# 7.0 wprowadza *wyrażeń throw*.

To dodawanie ułatwia pisanie kodu oparte na wyrażeniach więcej. Nie potrzebujesz dodatkowych instrukcji sprawdzania błędów.

## <a name="generalized-async-return-types"></a>Uogólnionego asynchroniczne typy zwracane

Zwracanie `Task` obiekt z metody asynchronicznej może prowadzić do wąskich gardeł wydajności w niektórych ścieżek. `Task` jest typem referencyjnym, więc za jego pomocą oznacza przydzielanie obiektu. W przypadkach, w którym metoda jest zadeklarowana za pomocą `async` modyfikator zwraca wynik pamięci podręcznej lub zakończeniu synchronicznie, dodatkowe alokacji może stać się koszt znaczną ilość czasu, w sekcji krytycznych wydajność kodu. Może być kosztowne, jeśli te przydziały występują w ścisłej pętli.

Nowa funkcja języka oznacza, że metoda asynchroniczna, zwracane typy nie są ograniczone do `Task`, `Task<T>`, i `void`. Zwrócony typ nadal musi spełniać wzorca asynchronicznego, co oznacza `GetAwaiter` metody muszą być dostępne. Przykład jednego konkretnego `ValueTask` typ został dodany do programu .NET framework, aby skorzystać z tej nowej funkcji języka:

[!code-csharp[UsingValueTask](~/samples/snippets/csharp/new-in-7/AsyncWork.cs#UsingValueTask "Using ValueTask")]

> [!NOTE]
> Dodaj pakiet NuGet [ `System.Threading.Tasks.Extensions` ](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) aby można było używać <xref:System.Threading.Tasks.ValueTask%601> typu.

To rozszerzenie jest najbardziej użyteczne dla autorów biblioteki uniknąć przyznawania `Task` w wydajności kodu krytycznego.

## <a name="numeric-literal-syntax-improvements"></a>Ulepszenia składni literału liczbowego

Misreading stałych numerycznych może utrudnić rozumienie kodu, odczytując je po raz pierwszy. Masek bitowych lub innych symboliczne wartości są podatne na nieporozumienia. C#7.0 zawiera dwie nowe funkcje, aby zapisać numery w najbardziej czytelny sposób związane z zamierzonym użyciem: *literały binarne*, i *separatory cyfr*.

Czasów przy tworzeniu masek bitowych lub zawsze wtedy, gdy binarna reprezentacja liczby sprawia, że najbardziej czytelne kodu, zapisać tę liczbę w pliku binarnego:

[!code-csharp[ThousandSeparators](~/samples/snippets/csharp/new-in-7/Program.cs#ThousandSeparators "Thousands separators")]

`0b` Na początku stała wskazuje, że liczba jest zapisywany jako wartości binarnej. Binarne wartości można uzyskać długości, więc jest często łatwiej zobaczyć wzorców bitowych, wprowadzając `_` jako separator cyfr, jak pokazano powyżej w stałej binarnego. Separator cyfr może występować w dowolnym miejscu w stałej. W przypadku podstawowej liczb 10, jest często używa się tysięcy separatora:

[!code-csharp[LargeIntegers](~/samples/snippets/csharp/new-in-7/Program.cs#LargeIntegers "Large integer")]

Separator cyfr, może być używany z `decimal`, `float`, i `double` również typy:

[!code-csharp[OtherConstants](~/samples/snippets/csharp/new-in-7/Program.cs#OtherConstants "non-integral constants")]

Razem wzięte, można zadeklarować stałych numerycznych za pomocą znacznie więcej czytelności.

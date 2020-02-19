---
title: Co nowego w C# 7,0 — C# Przewodnik
description: Zapoznaj się z omówieniem nowych funkcji w wersji 7,0 C# języka.
ms.date: 02/20/2019
ms.assetid: fd41596d-d0c2-4816-b94d-c4d00a5d0243
ms.openlocfilehash: a6ac5c00ceb2ce8e5e56e2a86a8cde937d5108e2
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/19/2020
ms.locfileid: "77448637"
---
# <a name="whats-new-in-c-70"></a>Co nowego w C# 7,0

C#7,0 dodaje wiele nowych funkcji do C# języka:

- [zmienne `out`](#out-variables)
  - Można zadeklarować wartości `out` w tekście jako argumenty metody, gdzie są używane.
- [Krotki](#tuples)
  - Można tworzyć lekkie, nienazwane typy, które zawierają wiele pól publicznych. Narzędzia kompilatora i IDE rozumieją semantykę tych typów.
- [Odrzucenia](#discards)
  - Odrzucenia są tymczasowymi zmiennymi tylko do zapisu, które są używane w przypisaniach, gdy nie ma opieki nad przypisaną wartością. Są one najbardziej przydatne podczas dekonstruowania krotek i typów zdefiniowanych przez użytkownika, a także podczas wywoływania metod przy użyciu parametrów `out`.
- [Dopasowanie do wzorca](#pattern-matching)
  - Można utworzyć logikę rozgałęziania na podstawie dowolnego typu i wartości elementów członkowskich tych typów.
- [`ref` lokalne i zwraca](#ref-locals-and-returns)
  - Zmienne lokalne metody i zwracane wartości mogą być odwołaniami do innego magazynu.
- [Funkcje lokalne](#local-functions)
  - Funkcje w innych funkcjach można zagnieżdżać w celu ograniczenia ich zakresu i widoczności.
- [Więcej składowych wyrażeń](#more-expression-bodied-members)
  - Lista elementów członkowskich, które mogą zostać utworzone przy użyciu wyrażeń.
- [Wyrażenia `throw`](#throw-expressions)
  - Można zgłosić wyjątki w konstrukcjach kodu, które wcześniej nie były dozwolone, ponieważ `throw` była instrukcją.
- [Uogólnione asynchroniczne typy zwracane](#generalized-async-return-types)
  - Metody zadeklarowane za pomocą modyfikatora `async` mogą zwracać inne typy oprócz `Task` i `Task<T>`.
- [Udoskonalenia składni literału liczbowego](#numeric-literal-syntax-improvements)
  - Nowe tokeny zwiększają czytelność dla stałych numerycznych.

Pozostała część tego artykułu zawiera omówienie każdej funkcji. Dla każdej funkcji znajdziesz jej uzasadnienie. Poznasz składnię. Te funkcje można eksplorować w środowisku za pomocą narzędzia globalnego `dotnet try`:

1. Zainstaluj narzędzie [dotnet-try](https://github.com/dotnet/try/blob/master/README.md#setup) Global.
1. Sklonuj repozytorium [dotnet/try-Samples](https://github.com/dotnet/try-samples) .
1. Ustaw bieżący katalog na podkatalog *csharp7* dla repozytorium *try-Samples* .
1. Uruchom polecenie `dotnet try`.

## <a name="out-variables"></a>zmienne `out`

Istniejąca składnia, która obsługuje `out` parametry, została ulepszona w tej wersji. Teraz można zadeklarować zmienne `out` na liście argumentów wywołania metody zamiast napisać oddzielną instrukcję deklaracji:

[!code-csharp[OutVariableDeclarations](~/samples/snippets/csharp/new-in-7/program.cs#OutVariableDeclarations "Out variable declarations")]

Możesz chcieć określić typ zmiennej `out` dla przejrzystości, jak pokazano powyżej. Język obsługuje jednak użycie niejawnie wpisanej zmiennej lokalnej:

[!code-csharp[OutVarVariableDeclarations](~/samples/snippets/csharp/new-in-7/program.cs#OutVarVariableDeclarations "Implicitly typed Out variable")]

- Kod jest łatwiejszy do odczytania.
  - Można zadeklarować zmienną out tam, gdzie ją używasz, a nie w innym wierszu powyżej.
- Nie trzeba przypisywać wartości początkowej.
  - Deklarując zmienną `out`, w której jest używana w wywołaniu metody, nie można jej przypadkowo użyć przed przypisaniem.

## <a name="tuples"></a>Krotki

C#zawiera rozbudowaną składnię dla klas i struktur, które są używane do wyjaśnienia zamiaru projektowania. Jednak czasami rozbudowana Składnia wymaga dodatkowej pracy z minimalną korzyścią. Często możesz pisać metody, które potrzebują prostej struktury zawierającej więcej niż jeden element danych. Aby obsługiwać te scenariusze, *krotki* zostały dodane do C#. Krotki są lekkimi strukturami danych, które zawierają wiele pól do reprezentowania elementów członkowskich danych.
Pola nie są zweryfikowane i nie można definiować własnych metod

> [!NOTE]
> Krotki były dostępne przed C# 7,0, ale były niewydajne i nie obsługiwały języka.
> Oznacza to, że elementy krotki mogą być przywoływane tylko jako `Item1`, `Item2` i tak dalej. C#7,0 wprowadza obsługę języków dla krotek, co umożliwia używanie nazw semantycznych dla pól krotki przy użyciu nowych, wydajniejszych typów krotek.

Można utworzyć krotkę, przypisując wartość do każdego elementu członkowskiego, a opcjonalnie dostarczając nazwy semantyczne dla każdego z elementów członkowskich krotki:

[!code-csharp[NamedTuple](~/samples/snippets/csharp/new-in-7/program.cs#NamedTuple "Named tuple")]

Spójna `namedLetters` krotka zawiera pola, które są nazywane `Alpha` i `Beta`. Te nazwy istnieją tylko w czasie kompilacji i nie są zachowywane, na przykład podczas sprawdzania krotki przy użyciu odbicia w czasie wykonywania.

W przypisaniu spójnej kolekcji można także określić nazwy pól po prawej stronie przypisania:

[!code-csharp[ImplicitNamedTuple](~/samples/snippets/csharp/new-in-7/program.cs#ImplicitNamedTuple "Implicitly named tuple")]

Mogą wystąpić sytuacje, w których chcesz rozpakować elementy członkowskie spójnej kolekcji, która została zwrócona z metody.  Można to zrobić przez zadeklarowanie oddzielnych zmiennych dla każdej wartości w spójnej kolekcji. To rozpakowanie nosi nazwę *dekonstrukcja* krotki:

[!code-csharp[CallingWithDeconstructor](~/samples/snippets/csharp/new-in-7/program.cs#CallingWithDeconstructor "Deconstructing a tuple")]

Można także zapewnić podobną dekonstrukcję dla dowolnego typu w programie .NET. Metodę `Deconstruct` należy napisać jako element członkowski klasy. Ta metoda `Deconstruct` dostarcza zestaw `out` argumentów dla każdej właściwości, która ma zostać wyodrębniona. Rozważmy tę `Point` klasę, która zapewnia metodę dekonstruktora, która wyodrębnia `X` i współrzędne `Y`:

[!code-csharp[PointWithDeconstruction](~/samples/snippets/csharp/new-in-7/point.cs#PointWithDeconstruction "Point with deconstruction method")]

Poszczególne pola można wyodrębnić, przypisując `Point` do krotki:

[!code-csharp[DeconstructPoint](~/samples/snippets/csharp/new-in-7/program.cs#DeconstructPoint "Deconstruct a point")]

Więcej informacji na temat spójnych krotek można znaleźć w [artykule krotkis](../tuples.md).

## <a name="discards"></a>Odrzucenia

Często podczas dekonstruowania krotki lub wywoływania metody za pomocą parametrów `out`, wymuszane jest zdefiniowanie zmiennej, której wartość nie jest zastosowana i nie zamierza się jej używać. C#dodaje obsługę *odrzutów* , aby obsłużyć ten scenariusz. Odrzucanie to zmienna tylko do zapisu, której nazwa jest `_` (znak podkreślenia); można przypisać wszystkie wartości, które mają zostać odrzucone do pojedynczej zmiennej. Odrzucenie przypomina przypisaną zmienną; poza instrukcją przypisania nie można używać odrzucania w kodzie.

Odrzucenia są obsługiwane w następujących scenariuszach:

- Podczas dekonstrukcji krotek lub typów zdefiniowanych przez użytkownika.
- Podczas wywoływania metod z parametrami [out](../language-reference/keywords/out-parameter-modifier.md) .
- W operacji dopasowania wzorca z instrukcjami with [i](../language-reference/keywords/is.md) [Switch](../language-reference/keywords/switch.md) .
- Jako identyfikator autonomiczny, gdy chcesz jawnie określić wartość przypisania jako odrzucenie.

W poniższym przykładzie zdefiniowano metodę `QueryCityDataForYears`, która zwraca 6-krotkę zawierającą dane dla miasta z dwóch różnych lat. Wywołanie metody w przykładzie jest rozważane tylko z dwiema wartościami populacji zwracanymi przez metodę i dlatego traktują pozostałe wartości w spójnej kolekcji jako odrzucane podczas dekonstruowania krotki.

[!code-csharp[Tuple-discard](~/samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

Aby uzyskać więcej informacji, zobacz [odrzucanie](../discards.md).

## <a name="pattern-matching"></a>Dopasowanie do wzorca

*Dopasowywanie do wzorców* to funkcja, która umożliwia implementowanie metody wysyłania we właściwościach innych niż typ obiektu. Prawdopodobnie znasz już metodę wysyłania metody na podstawie typu obiektu. W programowaniu zorientowanym obiektowo metody wirtualne i przesłonięcia zapewniają składnię języka, aby zaimplementować metodę wysyłania na podstawie typu obiektu. Klasy podstawowe i pochodne zapewniają różne implementacje.
Wyrażenia dopasowania wzorców poszerzają tę koncepcję, aby można było łatwo zaimplementować podobne wzorce wysyłania dla typów i elementów danych, które nie są związane z hierarchią dziedziczenia.

Dopasowywanie wzorców obsługuje wyrażenia `is` i wyrażenia `switch`. Każdy umożliwia inspekcję obiektu i jego właściwości w celu ustalenia, czy ten obiekt spełnia oczekiwany wzorzec. Użyj słowa kluczowego `when`, aby określić dodatkowe reguły do wzorca.

Wyrażenie wzorca `is` rozszerza znanego [operatora`is`](../language-reference/keywords/is.md#pattern-matching-with-is) do wykonywania zapytań względem obiektu o jego typie i przypisywania wyniku w jednej instrukcji. Poniższy kod sprawdza, czy zmienna jest `int`, a jeśli tak, dodaje ją do bieżącej sumy:

```csharp
if (input is int count)
    sum += count;
```

Powyższy mały przykład ilustruje ulepszenia wyrażenia `is`. Można testować względem typów wartości, a także typów referencyjnych, a następnie można przypisać prawidłowy wynik do nowej zmiennej poprawnego typu.

Wyrażenie dopasowania przełącznika ma znaną składnię opartą na instrukcji `switch`, która jest już częścią C# języka. Zaktualizowana instrukcja SWITCH zawiera kilka nowych konstrukcji:

- Typ regulujący wyrażenie `switch` nie jest już ograniczony do typów całkowitych, typów `Enum`, `string`lub typu dopuszczającego wartość null odpowiadającego jednemu z tych typów. Można użyć dowolnego typu.
- Typ wyrażenia `switch` można testować w każdej `case` etykiecie. Podobnie jak w przypadku wyrażenia `is`, można przypisać nową zmienną do tego typu.
- Można dodać klauzulę `when` do dalszych warunków testowania tej zmiennej.
- Kolejność etykiet `case` jest teraz ważna. Pierwsza gałąź do dopasowania jest wykonywana; pozostałe są pomijane.

Poniższy kod ilustruje następujące nowe funkcje:

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

- `case 0:` jest znanym wzorcem stałej.
- `case IEnumerable<int> childSequence:` jest wzorcem typu.
- `case int n when n > 0:` jest wzorcem typu z dodatkowym warunkiem `when`.
- `case null:` jest wzorcem o wartości null.
- `default:` jest znanym domyślnym przypadkiem.

Więcej informacji na temat dopasowywania wzorców w [programie można znaleźć C#w temacie. ](../pattern-matching.md)

## <a name="ref-locals-and-returns"></a>Ref locales i Returns

Ta funkcja włącza algorytmy, które używają i zwracają odwołania do zmiennych zdefiniowanych w innym miejscu. Jeden przykład pracuje z dużymi macierzami i odnajduje jedną lokalizację z określonymi cechami. Poniższa metoda zwraca **odwołanie** do tego magazynu w macierzy:

[!code-csharp[FindReturningRef](~/samples/snippets/csharp/new-in-7/MatrixSearch.cs#FindReturningRef "Find returning by reference")]

Można zadeklarować wartość zwracaną jako `ref` i zmodyfikować tę wartość w macierzy, jak pokazano w poniższym kodzie:

[!code-csharp[AssignRefReturn](~/samples/snippets/csharp/new-in-7/Program.cs#AssignRefReturn "Assign ref return")]

C# Język ma kilka reguł, które chronią przed niepożądanym użyciem `ref` lokalnych i zwraca:

- Należy dodać słowo kluczowe `ref` do sygnatury metody oraz do wszystkich instrukcji `return` w metodzie.
  - Dzięki temu czyszczenie metody następuje przez odwołanie w całej metodzie.
- `ref return` może być przypisana do zmiennej wartości lub zmiennej `ref`.
  - Obiekt wywołujący kontroluje, czy wartość zwracana jest kopiowana, czy nie. Pominięcie modyfikatora `ref` podczas przypisywania wartości zwracanej wskazuje, że obiekt wywołujący chce mieć kopię wartości, a nie odwołanie do magazynu.
- Nie można przypisać wartości zwracanej metody standardowej do `ref` zmiennej lokalnej.
  - Nie zezwala na instrukcje, takie jak `ref int i = sequence.Count();`
- Nie można zwrócić `ref` do zmiennej, której okres istnienia nie przekracza wykonywania metody.
  - Oznacza to, że nie można zwrócić odwołania do zmiennej lokalnej lub zmiennej o podobnym zakresie.
- `ref` locale i Returns nie mogą być używane z metodami asynchronicznymi.
  - Kompilator nie może wiedzieć, czy przywoływana zmienna została ustawiona na jej końcową wartość, gdy Metoda asynchroniczna zwraca.

Dodanie elementów lokalnych ref i Return ref umożliwia stosowanie algorytmów, które są bardziej wydajne przez uniknięcie kopiowania wartości lub wielokrotne wykonywanie operacji usuwania odwołań.

Dodanie `ref` do wartości zwracanej jest [zmianą zgodną ze źródłem](version-update-considerations.md#source-compatible-changes). Istniejący kod kompiluje, ale zwracana wartość Ref jest kopiowana po przypisaniu. Obiekty wywołujące muszą zaktualizować magazyn dla wartości zwracanej do `ref` zmiennej lokalnej, aby zapisać zwrot jako odwołanie.

Aby uzyskać więcej informacji, zobacz artykuł [słowo kluczowe ref](../language-reference/keywords/ref.md) .

## <a name="local-functions"></a>Funkcje lokalne

Wiele projektów klas obejmuje metody, które są wywoływane tylko z jednej lokalizacji. Te dodatkowe metody prywatne przechowują każdą metodę na małe i skoncentrowane. *Funkcje lokalne* umożliwiają deklarowanie metod wewnątrz kontekstu innej metody. Funkcje lokalne ułatwiają czytelnikom klasy sprawdzenie, czy metoda lokalna jest wywoływana tylko z kontekstu, w którym jest zadeklarowana.

Istnieją dwa typowe przypadki użycia funkcji lokalnych: metody iteratora publicznego i publiczne metody async. Oba typy metod generują kod, który zgłasza błędy później niż programiści mogą oczekiwać. W metodach iteratora wszystkie wyjątki są obserwowane tylko podczas wywoływania kodu, który wylicza zwracaną sekwencję. W metodach asynchronicznych wszelkie wyjątki są przestrzegane tylko wtedy, gdy zwracane `Task` są oczekiwane. Poniższy przykład ilustruje oddzielanie walidacji parametrów od implementacji iteratora przy użyciu funkcji lokalnej:

[!code-csharp[22_IteratorMethodLocal](~/samples/snippets/csharp/new-in-7/Iterator.cs#IteratorMethodLocal "Iterator method with local function")]

Ta sama technika może być stosowana z metodami `async`, aby upewnić się, że wyjątki wynikające z walidacji argumentów są zgłaszane przed rozpoczęciem pracy asynchronicznej:

[!code-csharp[TaskExample](~/samples/snippets/csharp/new-in-7/AsyncWork.cs#TaskExample "Task returning method with local function")]

> [!NOTE]
> Niektóre projekty, które są obsługiwane przez funkcje lokalne, można również zrealizować przy użyciu *wyrażeń lambda*. Aby uzyskać więcej informacji, zobacz temat [funkcje lokalne a wyrażenia lambda](../local-functions-vs-lambdas.md).

## <a name="more-expression-bodied-members"></a>Więcej składowych wyrażeń

C#6 wprowadzono [składowe z wyrażeniami](csharp-6.md#expression-bodied-function-members) dla funkcji Członkowskich i właściwości tylko do odczytu. C#7,0 rozwija dozwolone elementy członkowskie, które mogą być zaimplementowane jako wyrażenia. W C# 7,0 można zaimplementować *konstruktory*, *finalizatory*i `get` i metody dostępu `set` do *Właściwości* i *indeksatorów*. Poniższy kod przedstawia przykłady każdego z nich:

[!code-csharp[ExpressionBodiedMembers](~/samples/snippets/csharp/new-in-7/expressionmembers.cs#ExpressionBodiedEverything "new expression-bodied members")]

> [!NOTE]
> Ten przykład nie wymaga finalizatora, ale jest pokazywany do zademonstrowania składni. Nie należy implementować finalizatora w klasie, chyba że konieczne jest zwolnienie niezarządzanych zasobów. Należy również rozważyć użycie klasy <xref:System.Runtime.InteropServices.SafeHandle> zamiast bezpośrednio zarządzać niezarządzanymi zasobami.

Te nowe lokalizacje elementów członkowskich będących członkami wyrażeń reprezentują ważny punkt kontrolny dla C# języka: te funkcje zostały zaimplementowane przez członków społeczności pracujących w projekcie [Roslyn](https://github.com/dotnet/Roslyn) typu open source.

Zmiana metody na wyrażenie składowane składowej jest [zgodną z binarną zmianą](version-update-considerations.md#binary-compatible-changes).

## <a name="throw-expressions"></a>Wyrażenia throw

W C#programie `throw` zawsze była instrukcją. Ponieważ `throw` jest instrukcją, a nie wyrażeniem, istnieją C# konstrukcje, w których nie można było ich użyć. Uwzględnione wyrażenia warunkowe, wyrażenia łączenia o wartości null i niektóre wyrażenia lambda. Dodanie elementów członkowskich będących członkami wyrażeń dodaje więcej lokalizacji, w których wyrażenia `throw` byłyby przydatne. Aby można było napisać dowolny z tych konstrukcji, C# 7,0 wprowadza [*wyrażenia throw*](../language-reference/keywords/throw.md#the-throw-expression).

To dodanie ułatwia zapisanie więcej kodu opartego na wyrażeniach. Nie potrzebujesz dodatkowych instrukcji do sprawdzania błędów.

## <a name="generalized-async-return-types"></a>Uogólnione asynchroniczne typy zwracane

Zwrócenie obiektu `Task` z metod asynchronicznych może spowodować wąskie gardła wydajności w określonych ścieżkach. `Task` to typ referencyjny, dlatego użycie go oznacza przydzielenie obiektu. W przypadkach, gdy metoda zadeklarowana za pomocą modyfikatora `async` zwraca zbuforowany wynik lub zostanie zakończona synchronicznie, dodatkowe alokacje mogą stać się ważnym kosztem w przypadku krytycznych sekcji kodu. Może być kosztowna, jeśli te przydziały występują w ścisłych pętlach.

Nowa funkcja języka oznacza, że typy zwracające metodę asynchroniczną nie są ograniczone do `Task`, `Task<T>`i `void`. Zwracany typ musi nadal spełniać wzorzec asynchroniczny, co oznacza, że metoda `GetAwaiter` musi być dostępna. W jednym z konkretnych przykładów typ `ValueTask` został dodany do platformy .NET, aby można było korzystać z tej nowej funkcji języka:

[!code-csharp[UsingValueTask](~/samples/snippets/csharp/new-in-7/AsyncWork.cs#UsingValueTask "Using ValueTask")]

> [!NOTE]
> Należy dodać pakiet NuGet [`System.Threading.Tasks.Extensions`](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) , aby można było użyć typu <xref:System.Threading.Tasks.ValueTask%601>.

To ulepszenie jest najbardziej przydatne dla autorów bibliotek, aby uniknąć alokowania `Task` w kodzie krytycznym wydajności.

## <a name="numeric-literal-syntax-improvements"></a>Udoskonalenia składni literału liczbowego

Nieodczytanie stałych numerycznych może utrudnić zrozumienie kodu podczas odczytywania go po raz pierwszy. Maski bitowe lub inne wartości symboliczne są podatne na nieporozumienia. C#7,0 obejmuje dwie nowe funkcje do zapisu liczb w najbardziej czytelny sposób dla zamierzonego użycia: *literały binarne*oraz *separatory cyfr*.

Dla tych czasów podczas tworzenia masek bitowych lub za każdym razem, gdy binarna reprezentacja liczby sprawia, że jest to najbardziej czytelny kod, Zapisz ten numer w postaci binarnej:

[!code-csharp[ThousandSeparators](~/samples/snippets/csharp/new-in-7/Program.cs#ThousandSeparators "Thousands separators")]

`0b` na początku stałej wskazuje, że liczba jest zapisywana jako liczba binarna. Liczby binarne mogą być długie, więc często łatwiej jest zobaczyć wzorce bitowe, wprowadzając `_` jako separator cyfr, jak pokazano powyżej w stałej liczbie binarnej. Separator cyfr może pojawić się w dowolnym miejscu w stałej. W przypadku numerów podstawowych 10 często należy używać jej jako separatora tysięcy:

[!code-csharp[LargeIntegers](~/samples/snippets/csharp/new-in-7/Program.cs#LargeIntegers "Large integer")]

Separator cyfr może być również używany z typami `decimal`, `float`i `double`:

[!code-csharp[OtherConstants](~/samples/snippets/csharp/new-in-7/Program.cs#OtherConstants "non-integral constants")]

Ze sobą można zadeklarować stałe liczbowe o znacznie większej czytelności.

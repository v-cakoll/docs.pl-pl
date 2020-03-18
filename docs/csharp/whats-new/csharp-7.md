---
title: Co nowego w języku C# 7.0 - Przewodnik po językach C#
description: Zapoznaj się z omówieniem nowych funkcji w wersji 7.0 języka Języka C#.
ms.date: 02/20/2019
ms.assetid: fd41596d-d0c2-4816-b94d-c4d00a5d0243
ms.openlocfilehash: a6ac5c00ceb2ce8e5e56e2a86a8cde937d5108e2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399694"
---
# <a name="whats-new-in-c-70"></a>Co nowego w języku C# 7.0

C# 7.0 dodaje szereg nowych funkcji do języka Języka C#:

- [`out`Zmiennych](#out-variables)
  - Można zadeklarować `out` wartości w wierszu jako argumenty do metody, w której są używane.
- [Krotek](#tuples)
  - Można tworzyć lekkie, nienazwane typy zawierające wiele pól publicznych. Kompilatory i narzędzia IDE zrozumieć semantyki tych typów.
- [Odrzucenia](#discards)
  - Odrzuty są tymczasowe, tylko do zapisu zmienne używane w przypisaniach, gdy nie dbasz o wartość przypisaną. Są one najbardziej przydatne podczas dekonstrukcji krotek i typów zdefiniowanych przez użytkownika, a także podczas wywoływania metod z `out` parametrami.
- [Dopasowywanie wzorców](#pattern-matching)
  - Logikę rozgałęzienia można utworzyć na podstawie dowolnych typów i wartości członków tych typów.
- [`ref`mieszkańców i zwraca](#ref-locals-and-returns)
  - Metody zmiennych lokalnych i wartości zwracanych mogą być odwołaniami do innego magazynu.
- [Funkcje lokalne](#local-functions)
  - Można zagnieździć funkcje wewnątrz innych funkcji, aby ograniczyć ich zakres i widoczność.
- [Więcej członków zabudowanych wyrazami](#more-expression-bodied-members)
  - Lista elementów członkowskich, które mogą być autorami przy użyciu wyrażeń wzrosła.
- [`throw`Wyrażenia](#throw-expressions)
  - Można zgłaszać wyjątki w konstrukcjach kodu, `throw` które wcześniej nie były dozwolone, ponieważ była instrukcją.
- [Uogólnione typy zwrotów asynchronicznej](#generalized-async-return-types)
  - Metody zadeklarowane `async` za pomocą modyfikatora `Task` `Task<T>`mogą zwracać inne typy oprócz i .
- [Ulepszenia składni literału liczbowego](#numeric-literal-syntax-improvements)
  - Nowe tokeny poprawiają czytelność dla stałych liczbowych.

W dalszej części tego artykułu przedstawiono omówienie każdej funkcji. Dla każdej funkcji dowiesz się, co za nią kryje. Dowiesz się składni. Te funkcje można eksplorować w swoim środowisku za pomocą narzędzia globalnego: `dotnet try`

1. Zainstaluj narzędzie globalne [dotnet-try.](https://github.com/dotnet/try/blob/master/README.md#setup)
1. Klonuj repozytorium [dotnet/try-samples.](https://github.com/dotnet/try-samples)
1. Ustaw bieżący katalog na podkatalog *csharp7* dla repozytorium *próbek.*
1. Uruchom polecenie `dotnet try`.

## <a name="out-variables"></a>`out`Zmiennych

Istniejąca składnia `out` obsługująca parametry została ulepszona w tej wersji. Można teraz `out` zadeklarować zmienne na liście argumentów wywołania metody, zamiast pisać oddzielną deklarację deklaracji:

[!code-csharp[OutVariableDeclarations](~/samples/snippets/csharp/new-in-7/program.cs#OutVariableDeclarations "Out variable declarations")]

Można określić typ zmiennej `out` dla jasności, jak pokazano powyżej. Jednak język obsługuje przy użyciu niejawnie wpisane zmiennej lokalnej:

[!code-csharp[OutVarVariableDeclarations](~/samples/snippets/csharp/new-in-7/program.cs#OutVarVariableDeclarations "Implicitly typed Out variable")]

- Kod jest łatwiejszy do odczytania.
  - Deklarujesz zmienną out, w której jej używasz, a nie w innym wierszu powyżej.
- Nie ma potrzeby przypisywania wartości początkowej.
  - Deklarując zmienną, `out` w której jest używana w wywołaniu metody, nie można przypadkowo użyć go przed przypisanym.

## <a name="tuples"></a>Krotki

C# zapewnia bogatą składnię dla klas i struktur, który jest używany do wyjaśnienia intencji projektu. Ale czasami ta bogata składnia wymaga dodatkowej pracy przy minimalnych korzyściach. Często można napisać metody, które wymagają prostej struktury zawierającej więcej niż jeden element danych. Aby obsługiwać te scenariusze *krotek* zostały dodane do języka C#. Krotek są lekkie struktury danych, które zawierają wiele pól do reprezentowania elementów członkowskich danych.
Pola nie są sprawdzane i nie można zdefiniować własnych metod

> [!NOTE]
> Tuples były dostępne przed C# 7.0, ale były nieefektywne i nie miał obsługi języka.
> Oznaczało to, że elementy krotki `Item1` `Item2` można było odwoływać się tylko jako , i tak dalej. C# 7.0 wprowadza obsługę języka dla krotek, który umożliwia nazwy semantyczne dla pól krotki przy użyciu nowych, bardziej wydajnych typów krotki.

Krotka można utworzyć, przypisując wartość do każdego elementu członkowskiego i opcjonalnie podając nazwy semantyczne każdemu członkowi krotki:

[!code-csharp[NamedTuple](~/samples/snippets/csharp/new-in-7/program.cs#NamedTuple "Named tuple")]

Krotka `namedLetters` zawiera pola określane `Alpha` `Beta`jako i . Te nazwy istnieją tylko w czasie kompilacji i nie są zachowywane, na przykład podczas sprawdzania krotki przy użyciu odbicia w czasie wykonywania.

W przydziale krotki można również określić nazwy pól po prawej stronie przypisania:

[!code-csharp[ImplicitNamedTuple](~/samples/snippets/csharp/new-in-7/program.cs#ImplicitNamedTuple "Implicitly named tuple")]

Może się okazać, że chcesz rozpakować elementy członkowskie krotki, które zostały zwrócone z metody.  Można to zrobić, deklarując oddzielne zmienne dla każdej z wartości w krotce. To rozpakowanie nazywa *się dekonstrukcją* krotki:

[!code-csharp[CallingWithDeconstructor](~/samples/snippets/csharp/new-in-7/program.cs#CallingWithDeconstructor "Deconstructing a tuple")]

Można również podać podobną dekonstrukcję dla dowolnego typu w .NET. Piszesz `Deconstruct` metodę jako element członkowski klasy. Ta `Deconstruct` metoda zawiera `out` zestaw argumentów dla każdej z właściwości, które chcesz wyodrębnić. Należy `Point` wziąć pod uwagę tę klasę, która `X` `Y` zapewnia metodę dekonstruktora, która wyodrębnia i współrzędne:

[!code-csharp[PointWithDeconstruction](~/samples/snippets/csharp/new-in-7/point.cs#PointWithDeconstruction "Point with deconstruction method")]

Poszczególne pola można wyodrębnić, `Point` przypisując do krotki:

[!code-csharp[DeconstructPoint](~/samples/snippets/csharp/new-in-7/program.cs#DeconstructPoint "Deconstruct a point")]

Możesz dowiedzieć się więcej o krotek w [artykule krotek](../tuples.md).

## <a name="discards"></a>Odrzucenia

Często podczas dekonstrukcji krotki lub `out` wywoływania metody z parametrami, jesteś zmuszony do zdefiniowania zmiennej, której wartość nie obchodzi i nie zamierzasz używać. C# dodaje obsługę *odrzutów* do obsługi tego scenariusza. Odrzut jest zmienną tylko do `_` zapisu, której nazwa jest (znak podkreślenia); można przypisać wszystkie wartości, które mają zostać odrzucone do pojedynczej zmiennej. Odrzucenie jest jak zmienna bez przypisanych; oprócz instrukcji przypisania odrzutu nie można używać w kodzie.

Odrzuty są obsługiwane w następujących scenariuszach:

- Podczas dekonstrukcji krotek lub typów zdefiniowanych przez użytkownika.
- Podczas wywoływania metod [z](../language-reference/keywords/out-parameter-modifier.md) out parametrów.
- W operacji dopasowania wzorca z [is](../language-reference/keywords/is.md) i [switch](../language-reference/keywords/switch.md) instrukcji.
- Jako identyfikator autonomiczny, gdy chcesz jawnie zidentyfikować wartość przypisania jako odrzucenie.

W poniższym `QueryCityDataForYears` przykładzie zdefiniowano metodę, która zwraca 6-krotki, która zawiera dane dla miasta przez dwa różne lata. Wywołanie metody w przykładzie dotyczy tylko dwóch wartości populacji zwracanych przez metodę i w ten sposób traktuje pozostałe wartości w krotce jako odrzuty, gdy dekonstruuje krotkę.

[!code-csharp[Tuple-discard](~/samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

Aby uzyskać więcej informacji, zobacz [Odrzucanie](../discards.md).

## <a name="pattern-matching"></a>Dopasowanie do wzorca

*Dopasowywanie wzorców* jest funkcją, która umożliwia implementanie wysyłania metody we właściwościach innych niż typ obiektu. Prawdopodobnie znasz już wysyłanie metody na podstawie typu obiektu. W programowaniu obiektowym metody wirtualne i zastępowanie zapewniają składnię języka w celu zaimplementowania wysyłania metod na podstawie typu obiektu. Klasy podstawowe i pochodne zapewniają różne implementacje.
Wyrażenia dopasowywania wzorców rozszerzają tę koncepcję, dzięki czemu można łatwo zaimplementować podobne wzorce wysyłki dla typów i elementów danych, które nie są powiązane za pośrednictwem hierarchii dziedziczenia.

Dopasowywanie wzorców obsługuje `is` wyrażenia i `switch` wyrażenia. Każdy umożliwia sprawdzanie obiektu i jego właściwości, aby ustalić, czy ten obiekt spełnia poszukiwany wzorzec. Słowo kluczowe `when` służy do określania dodatkowych reguł do wzorca.

Wyrażenie `is` wzorca rozszerza znany [ `is` operator](../language-reference/keywords/is.md#pattern-matching-with-is) do kwerendy obiektu o jego typ ie i przypisać wynik w jednej instrukcji. Poniższy kod sprawdza, czy `int`zmienna jest , a jeśli tak, dodaje ją do bieżącej sumy:

```csharp
if (input is int count)
    sum += count;
```

W poprzednim małym przykładzie przedstawiono ulepszenia `is` wyrażenia. Można przetestować typy wartości, a także typy odwołań i można przypisać pomyślny wynik do nowej zmiennej poprawnego typu.

Wyrażenie dopasowania przełącznika ma znajomą składnię, `switch` na podstawie instrukcji już część języka C#. Zaktualizowana instrukcja switch ma kilka nowych konstrukcji:

- Typ zarządzania wyrażeniem `switch` nie jest już ograniczony `Enum` do `string`typów, typów, typów ani typu dającego wartość null odpowiadającego jednemu z tych typów. Można użyć dowolnego typu.
- Można przetestować typ `switch` wyrażenia w `case` każdej etykiecie. Podobnie jak `is` w przypadku wyrażenia, można przypisać nową zmienną do tego typu.
- Można dodać `when` klauzulę do dalszych warunków testu na tej zmiennej.
- Kolejność `case` etykiet jest teraz ważna. Pierwsza gałąź do dopasowania jest wykonywana; inne są pomijane.

Poniższy kod pokazuje te nowe funkcje:

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

- `case 0:`jest znanym stałym wzorem.
- `case IEnumerable<int> childSequence:`jest wzorem typu.
- `case int n when n > 0:`jest wzorem typu z `when` dodatkowym warunkiem.
- `case null:`jest wzorcem zerowym.
- `default:`jest znanym przypadkiem domyślnym.

Możesz dowiedzieć się więcej o dopasowywaniu wzorców w [dopasowaniu wzorców w języku C#.](../pattern-matching.md)

## <a name="ref-locals-and-returns"></a>Ref mieszkańców i zwraca

Ta funkcja umożliwia algorytmy, które używają i zwracają odwołania do zmiennych zdefiniowanych w innym miejscu. Jednym z przykładów jest praca z dużymi macierzami i znalezienie pojedynczej lokalizacji o pewnych cechach. Następująca metoda zwraca **odwołanie** do tego magazynu w macierzy:

[!code-csharp[FindReturningRef](~/samples/snippets/csharp/new-in-7/MatrixSearch.cs#FindReturningRef "Find returning by reference")]

Można zadeklarować wartość zwracaną `ref` jako i zmodyfikować tę wartość w macierzy, jak pokazano w następującym kodzie:

[!code-csharp[AssignRefReturn](~/samples/snippets/csharp/new-in-7/Program.cs#AssignRefReturn "Assign ref return")]

Język C# ma kilka reguł, które chronią przed nadużywaniem `ref` miejscowych i zwraca:

- Słowo `ref` kluczowe należy dodać do podpisu `return` metody i do wszystkich instrukcji w metodzie.
  - To sprawia, że jasne metoda zwraca przez odwołanie w całej metody.
- A `ref return` może być przypisany do `ref` zmiennej wartości lub zmiennej.
  - Obiekt wywołujący określa, czy zwracana wartość jest kopiowana, czy nie. Pominięcie modyfikatora `ref` podczas przypisywania wartości zwracanej wskazuje, że obiekt wywołujący chce kopię wartości, a nie odwołanie do magazynu.
- Nie można przypisać wartości zwracanej standardowej `ref` metody do zmiennej lokalnej.
  - To nie pozwala na oświadczenia, takie jak`ref int i = sequence.Count();`
- Nie można zwrócić `ref` do zmiennej, której okres istnienia nie wykracza poza wykonanie metody.
  - Oznacza to, że nie można zwrócić odwołanie do zmiennej lokalnej lub zmiennej o podobnym zakresie.
- `ref`miejscowych i zwraca nie mogą być używane z metodami asynchronicznym.
  - Kompilator nie może wiedzieć, czy zmienna, do której istnieje odwołanie, została ustawiona na jej wartość końcową, gdy zwraca się metoda asynchroniczną.

Dodanie ref locals i ref zwraca umożliwia algorytmy, które są bardziej wydajne, unikając kopiowania wartości lub wykonywania operacji dereferencing wiele razy.

Dodanie `ref` do wartości zwracanej jest [zmianą zgodną ze źródłem](version-update-considerations.md#source-compatible-changes). Istniejący kod kompiluje, ale wartość zwracana ref jest kopiowana po przypisaniu. Obiekty wywołujące muszą zaktualizować magazyn `ref` dla wartości zwracanej do zmiennej lokalnej do przechowywania zwrotu jako odwołanie.

Aby uzyskać więcej informacji, zobacz artykuł [ref słowa kluczowego.](../language-reference/keywords/ref.md)

## <a name="local-functions"></a>Funkcje lokalne

Wiele projektów dla klas obejmują metody, które są wywoływane tylko z jednej lokalizacji. Te dodatkowe metody prywatne zachować każdą metodę małe i koncentruje. *Funkcje lokalne* umożliwiają deklarowanie metod w kontekście innej metody. Funkcje lokalne ułatwiają czytelnikom klasy, aby zobaczyć, że metoda lokalna jest wywoływana tylko z kontekstu, w którym jest zadeklarowany.

Istnieją dwa typowe przypadki użycia dla funkcji lokalnych: publiczne metody iteratorem i publiczne metody asynchroniczne. Oba typy metod generują kod, który zgłasza błędy później niż programiści mogą się spodziewać. W metodach iteratora wszelkie wyjątki są przestrzegane tylko podczas wywoływania kodu, który wylicza zwróconą sekwencję. W metodach asynchronicznej wszelkie wyjątki są `Task` obserwowane tylko wtedy, gdy oczekuje się zwróconego. W poniższym przykładzie przedstawiono oddzielenie sprawdzania poprawności parametrów od implementacji iteratorem przy użyciu funkcji lokalnej:

[!code-csharp[22_IteratorMethodLocal](~/samples/snippets/csharp/new-in-7/Iterator.cs#IteratorMethodLocal "Iterator method with local function")]

Tę samą technikę `async` można zastosować za pomocą metod, aby zapewnić, że wyjątki wynikające z sprawdzania poprawności argumentu są generowane przed rozpoczęciem pracy asynchronicznej:

[!code-csharp[TaskExample](~/samples/snippets/csharp/new-in-7/AsyncWork.cs#TaskExample "Task returning method with local function")]

> [!NOTE]
> Niektóre projekty, które są obsługiwane przez funkcje lokalne można również wykonać przy użyciu *wyrażeń lambda*. Aby uzyskać więcej informacji, zobacz [Funkcje lokalne a wyrażenia lambda](../local-functions-vs-lambdas.md).

## <a name="more-expression-bodied-members"></a>Więcej członków zabudowanych wyrazami

C# 6 wprowadzono [elementy członkowskie zabudowane wyrażeniem](csharp-6.md#expression-bodied-function-members) dla funkcji elementów członkowskich i właściwości tylko do odczytu. C# 7.0 rozszerza dozwolonych elementów członkowskich, które mogą być implementowane jako wyrażenia. W języku C# 7.0 można zaimplementować *konstruktory*, *finalizatory*i `get` `set` akcesory na *właściwości* i *indeksatory*. Poniższy kod przedstawia przykłady każdego z nich:

[!code-csharp[ExpressionBodiedMembers](~/samples/snippets/csharp/new-in-7/expressionmembers.cs#ExpressionBodiedEverything "new expression-bodied members")]

> [!NOTE]
> W tym przykładzie nie wymaga finalizatora, ale jest wyświetlany do wykazania składni. Nie należy implementować finalizatora w klasie, chyba że jest to konieczne do zwolnienia zasobów niezarządzanych. Należy również rozważyć <xref:System.Runtime.InteropServices.SafeHandle> użycie klasy zamiast bezpośredniego zarządzania zasobami niezarządzanymi.

Te nowe lokalizacje dla członków zabudowanych wyrażeniem stanowią ważny punkt kontrolny dla języka Języka C#: Te funkcje zostały wdrożone przez członków społeczności pracujących nad projektem [Roslyn](https://github.com/dotnet/Roslyn) typu open source.

Zmiana metody na element członkowski wyrażenia jest [zmianą zgodną z binarną](version-update-considerations.md#binary-compatible-changes).

## <a name="throw-expressions"></a>Wyrażenia throw

W języku `throw` C#, zawsze była instrukcja. Ponieważ `throw` jest instrukcją, a nie wyrażenie, były konstrukcje C#, gdzie nie można go używać. Obejmowały one wyrażenia warunkowe, wyrażenia zerowe łączenia i niektóre wyrażenia lambda. Dodanie elementów członkowskich zabudowanych wyrażeniedodaje `throw` więcej lokalizacji, gdzie wyrażenia będą przydatne. Tak, aby można było napisać dowolną z tych konstrukcji, C# 7.0 wprowadza [*wyrażenia throw*](../language-reference/keywords/throw.md#the-throw-expression).

Ten dodatek ułatwia pisanie więcej kodu opartego na wyrażeniach. Nie potrzebujesz dodatkowych instrukcji do sprawdzania błędów.

## <a name="generalized-async-return-types"></a>Uogólnione typy zwrotów asynchronicznej

Zwracanie `Task` obiektu z metod asynchronicznej może wprowadzić wąskie gardła wydajności w niektórych ścieżkach. `Task`jest typem odwołania, więc użycie go oznacza przydzielanie obiektu. W przypadkach, gdy metoda `async` zadeklarowana za pomocą modyfikatora zwraca wynik buforowany lub kończy synchronicznie, dodatkowe alokacje mogą stać się znacznym kosztem czasu w krytycznych sekcjach kodu dotyczących wydajności. Może stać się kosztowne, jeśli te alokacje występują w ciasnych pętli.

Nowa funkcja języka oznacza, że typy zwracania `Task`metody `Task<T>`asynchronicznej nie są ograniczone do , i `void`. Zwracany typ musi nadal spełniać wzorzec asynchronicznego, co oznacza, że `GetAwaiter` metoda musi być dostępna. Jako jeden konkretny `ValueTask` przykład typ został dodany do .NET, aby skorzystać z tej nowej funkcji języka:

[!code-csharp[UsingValueTask](~/samples/snippets/csharp/new-in-7/AsyncWork.cs#UsingValueTask "Using ValueTask")]

> [!NOTE]
> Należy dodać pakiet [`System.Threading.Tasks.Extensions`](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) NuGet w celu <xref:System.Threading.Tasks.ValueTask%601> użycia tego typu.

To ulepszenie jest najbardziej przydatne dla `Task` autorów biblioteki, aby uniknąć przydzielania w stanie krytycznym kodu.

## <a name="numeric-literal-syntax-improvements"></a>Ulepszenia składni literału liczbowego

Błędne odczytanie stałych liczbowych może utrudnić zrozumienie kodu podczas czytania go po raz pierwszy. Maski bitowe lub inne wartości symboliczne są podatne na nieporozumienia. C# 7.0 zawiera dwie nowe funkcje do zapisu liczb w najbardziej czytelny sposób dla zamierzonego zastosowania: *literały binarne*i *separatory cyfr*.

W tych przypadkach, gdy tworzysz maski bitowe lub gdy binarna reprezentacja liczby tworzy najbardziej czytelny kod, zapisz tę liczbę w formacie binarnym:

[!code-csharp[ThousandSeparators](~/samples/snippets/csharp/new-in-7/Program.cs#ThousandSeparators "Thousands separators")]

Na `0b` początku stałej wskazuje, że liczba jest zapisywana jako liczba binarna. Liczby binarne mogą się wydłużyć, więc często łatwiej jest `_` zobaczyć wzorce bitów, wprowadzając jako separator cyfr, jak pokazano powyżej w stałej binarnej. Separator cyfr może pojawić się w dowolnym miejscu w stałej. W przypadku numerów 10 bazowych często używa się go jako separatora tysięcy:

[!code-csharp[LargeIntegers](~/samples/snippets/csharp/new-in-7/Program.cs#LargeIntegers "Large integer")]

Separatora cyfr można `decimal`używać `float`z `double` , i typy, jak również:

[!code-csharp[OtherConstants](~/samples/snippets/csharp/new-in-7/Program.cs#OtherConstants "non-integral constants")]

W sumie można zadeklarować stałe liczbowe o znacznie większej czytelności.

---
title: Co nowego w C# 7.0 - C# Przewodnik
description: Zapoznaj się z omówieniem nowych funkcji w wersji 7.0 języka C#.
ms.date: 02/20/2019
ms.assetid: fd41596d-d0c2-4816-b94d-c4d00a5d0243
ms.openlocfilehash: 1291de95b88b3de16fb94fb376fb4153dd4a5862
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102674"
---
# <a name="whats-new-in-c-70"></a>Co nowego w języku C# 7.0

C# 7.0 dodaje szereg nowych funkcji do języka C#:

- [`out`Zmiennych](#out-variables)
  - Wartości można `out` zadeklarować jako argumenty do metody, w której są używane.
- [Krotki](#tuples)
  - Można utworzyć odciążone, nienazwane typy, które zawierają wiele pól publicznych. Kompilatory i narzędzia IDE zrozumieć semantyki tych typów.
- [Odrzucenia](#discards)
  - Odrzuty są zmiennymi tymczasowymi, tylko do zapisu używanymi w przydziałach, gdy nie zależy Ci na przypisanej wartości. Są one najbardziej przydatne podczas dekonstrukcji krotek i typów zdefiniowanych `out` przez użytkownika, a także podczas wywoływania metod z parametrami.
- [Dopasowanie wzorca](#pattern-matching)
  - Można utworzyć logikę rozgałęzienia na podstawie dowolnych typów i wartości elementów członkowskich tych typów.
- [`ref`mieszkańców i powrotów](#ref-locals-and-returns)
  - Metody zmienne lokalne i zwracane wartości mogą być odwołania do innych magazynów.
- [Funkcje lokalne](#local-functions)
  - Można zagnieżdżać funkcje wewnątrz innych funkcji, aby ograniczyć ich zakres i widoczność.
- [Więcej członków wyrazu](#more-expression-bodied-members)
  - Lista elementów członkowskich, które mogą być autorstwa przy użyciu wyrażeń wzrosła.
- [`throw`Wyrażenia](#throw-expressions)
  - Można zgłaszać wyjątki w konstrukcjach kodu, które `throw` wcześniej nie były dozwolone, ponieważ była instrukcja.
- [Uogólnione typy zwrotów asynchronizowanych](#generalized-async-return-types)
  - Metody zadeklarowane `async` za pomocą modyfikatora `Task` `Task<T>`mogą zwracać inne typy oprócz i .
- [Ulepszenia składni literału liczbowego](#numeric-literal-syntax-improvements)
  - Nowe tokeny zwiększają czytelność dla stałych liczbowych.

Poniżej dalsza część artykułu Zawiera omówienie każdej funkcji. Dla każdej funkcji, dowiesz się rozumowanie za nim. Nauczysz się składni. Za pomocą narzędzia globalnego można `dotnet try` eksplorować te funkcje w swoim środowisku:

1. Zainstaluj narzędzie globalne [dotnet-try.](https://github.com/dotnet/try/blob/master/README.md#setup)
1. Sklonuj repozytorium [dotnet/try-samples.](https://github.com/dotnet/try-samples)
1. Ustaw bieżący katalog na podkatalog *csharp7* dla repozytorium *try-samples.*
1. Uruchom polecenie `dotnet try`.

## <a name="out-variables"></a>`out`Zmiennych

W tej wersji ulepszono istniejącą składnię obsługującą `out` parametry. Teraz można `out` zadeklarować zmienne na liście argumentów wywołania metody, zamiast pisać oddzielną instrukcję deklaracji:

[!code-csharp[OutVariableDeclarations](~/samples/snippets/csharp/new-in-7/program.cs#OutVariableDeclarations "Out variable declarations")]

Można określić typ zmiennej `out` dla jasności, jak pokazano powyżej. Jednak język obsługuje przy użyciu niejawnie wpisanej zmiennej lokalnej:

[!code-csharp[OutVarVariableDeclarations](~/samples/snippets/csharp/new-in-7/program.cs#OutVarVariableDeclarations "Implicitly typed Out variable")]

- Kod jest łatwiejszy do odczytania.
  - Deklarujesz zmienną out, w której jej używasz, a nie w innym wierszu powyżej.
- Nie ma potrzeby przypisywania wartości początkowej.
  - Deklarując zmienną, `out` gdzie jest używana w wywołaniu metody, nie można przypadkowo użyć go przed przypisaniem.

## <a name="tuples"></a>Krotki

C# zawiera bogatą składnię dla klas i struktur, który jest używany do wyjaśnienia intencji projektu. Ale czasami ta bogata składnia wymaga dodatkowej pracy przy minimalnych korzyściach. Często można napisać metody, które wymagają prostej struktury zawierającej więcej niż jeden element danych. Aby obsługiwać te scenariusze *krotki* zostały dodane do języka C#. Krotek są odciążone struktury danych, które zawierają wiele pól do reprezentowania elementów członkowskich danych.
Pola nie są sprawdzane i nie można definiować własnych metod

> [!NOTE]
> Krotek były dostępne przed C# 7.0, ale były nieefektywne i nie miał obsługi języka.
> Oznaczało to, że elementy krotki `Item1`można `Item2` było odwoływać się tylko jako , i tak dalej. C# 7.0 wprowadza obsługę języka krotek, która umożliwia semantyczne nazwy dla pól krotki przy użyciu nowych, bardziej wydajnych typów krotki.

Kroli można utworzyć, przypisując wartość do każdego elementu członkowskiego i opcjonalnie podając nazwy semantyczne do każdego z elementów członkowskich krotki:

[!code-csharp[NamedTuple](~/samples/snippets/csharp/new-in-7/program.cs#NamedTuple "Named tuple")]

Krotka `namedLetters` zawiera pola określane `Alpha` `Beta`jako . Te nazwy istnieją tylko w czasie kompilacji i nie są zachowywane, na przykład podczas sprawdzania krotki przy użyciu odbicia w czasie wykonywania.

W przypisaniu krotki można również określić nazwy pól po prawej stronie przydziału:

[!code-csharp[ImplicitNamedTuple](~/samples/snippets/csharp/new-in-7/program.cs#ImplicitNamedTuple "Implicitly named tuple")]

Może się okazać, że chcesz rozpakować elementy członkowskie krotki, które zostały zwrócone z metody.  Można to zrobić, deklarując oddzielne zmienne dla każdej z wartości w krocie. To rozpakowanie jest nazywane *dekonstrukcji* krotki:

[!code-csharp[CallingWithDeconstructor](~/samples/snippets/csharp/new-in-7/program.cs#CallingWithDeconstructor "Deconstructing a tuple")]

Można również podać podobną dekonstrukcję dla dowolnego typu w .NET. Piszesz `Deconstruct` metodę jako członek klasy. Ta `Deconstruct` metoda zawiera `out` zestaw argumentów dla każdej właściwości, które chcesz wyodrębnić. Należy `Point` wziąć pod uwagę tę klasę, która `X` zapewnia `Y` metodę dekonstruktora, która wyodrębnia i współrzędne:

[!code-csharp[PointWithDeconstruction](~/samples/snippets/csharp/new-in-7/point.cs#PointWithDeconstruction "Point with deconstruction method")]

Poszczególne pola można wyodrębnić, `Point` przypisując je do krotki:

[!code-csharp[DeconstructPoint](~/samples/snippets/csharp/new-in-7/program.cs#DeconstructPoint "Deconstruct a point")]

Więcej informacji na temat krotek można dowiedzieć się więcej na temat krotek w [artykule krotek](../tuples.md).

## <a name="discards"></a>Odrzucenia

Często podczas dekonstrukcji krotki lub `out` wywoływania metody z parametrami, jesteś zmuszony do zdefiniowania zmiennej, której wartość nie dbasz o i nie zamierza używać. C# dodaje obsługę *odrzuceń* do obsługi tego scenariusza. Odrzucenie jest zmienną tylko do `_` zapisu, której nazwa jest (znak podkreślenia); można przypisać wszystkie wartości, które mają zostać odrzucone do pojedynczej zmiennej. Odrzucenie jest jak nieprzypisane zmiennej; oprócz instrukcji przypisania, odrzucenia nie można użyć w kodzie.

Odrzuty są obsługiwane w następujących scenariuszach:

- Podczas dekonstrukcji krotek lub typów zdefiniowanych przez użytkownika.
- Podczas wywoływania metod z parametrami [out.](../language-reference/keywords/out-parameter-modifier.md)
- W operacji dopasowywania wzorca z [instrukcjami is](../language-reference/keywords/is.md) i [switch.](../language-reference/keywords/switch.md)
- Jako samodzielny identyfikator, gdy chcesz jawnie zidentyfikować wartość przypisania jako odrzucenie.

Poniższy przykład definiuje `QueryCityDataForYears` metodę, która zwraca 6-krotki, która zawiera dane dla miasta dla dwóch różnych lat. Wywołanie metody w przykładzie dotyczy tylko dwóch wartości populacji zwracanych przez metodę i dlatego traktuje pozostałe wartości w krocie jako odrzucane, gdy dekonstruuje krotki.

[!code-csharp[Tuple-discard](~/samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

Aby uzyskać więcej informacji, zobacz [Odrzuca](../discards.md).

## <a name="pattern-matching"></a>Dopasowanie do wzorca

*Dopasowywanie wzorca* jest funkcją, która umożliwia implementowanie wysyłki metody na właściwości innych niż typ obiektu. Prawdopodobnie jesteś już zaznajomiony z wywoływania metody na podstawie typu obiektu. W programowaniu obiektowym metody wirtualne i zastępowanie zapewniają składnię języka w celu zaimplementowania dyspozycyjności metody na podstawie typu obiektu. Klasy podstawowe i pochodne zapewniają różne implementacje.
Wyrażenia dopasowywania wzorców rozszerzają tę koncepcję, dzięki czemu można łatwo zaimplementować podobne wzorce wysyłki dla typów i elementów danych, które nie są powiązane za pośrednictwem hierarchii dziedziczenia.

Dopasowywanie wzorców obsługuje `is` wyrażenia i `switch` wyrażenia. Każdy umożliwia sprawdzanie obiektu i jego właściwości, aby ustalić, czy ten obiekt spełnia żądany wzorzec. Użyj słowa `when` kluczowego, aby określić dodatkowe reguły wzorca.

Wyrażenie `is` wzorca rozszerza [ `is` ](../language-reference/keywords/is.md#pattern-matching-with-is) znanego operatora do kwerendy obiektu o jego typ i przypisać wynik w jednej instrukcji. Poniższy kod sprawdza, czy `int`zmienna jest , a jeśli tak, dodaje ją do bieżącej sumy:

```csharp
if (input is int count)
    sum += count;
```

W poprzednim małym przykładzie przedstawiono `is` ulepszenia wyrażenia. Można przetestować na typy wartości, jak również typy odwołań i można przypisać wynik pomyślny do nowej zmiennej o poprawnym typie.

Wyrażenie dopasowania przełącznika ma znaną składnię, opartą `switch` na instrukcji już części języka C#. Zaktualizowana instrukcja switch ma kilka nowych konstrukcji:

- Typ określania `switch` wartości wyrażeń nie jest `Enum` już `string`ograniczony do typów, typów lub typu nullable odpowiadającego jednemu z tych typów. Można użyć dowolnego typu.
- Typ `switch` wyrażenia można przetestować w `case` każdej etykiecie. Podobnie jak `is` w odniesieniu do wyrażenia, można przypisać nową zmienną do tego typu.
- Można dodać `when` klauzulę do dalszych warunków testowych dla tej zmiennej.
- Kolejność `case` etykiet jest teraz ważna. Pierwsza gałąź do dopasowania jest wykonywana; inne są pomijane.

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

- `case 0:`jest znanym stałym wzorem.
- `case IEnumerable<int> childSequence:`jest wzorcem typu.
- `case int n when n > 0:`jest wzorem typu `when` z dodatkowym warunkiem.
- `case null:`jest wzorcem null.
- `default:`to znana domyślna obudowa.

Więcej informacji na temat dopasowywania wzorców można dowiedzieć się w języku [C# .You](../pattern-matching.md)can learn more about pattern matching in Pattern Matching in C# .

## <a name="ref-locals-and-returns"></a>Ref mieszkańców i zwraca

Ta funkcja umożliwia algorytmy, które używają i zwracają odwołania do zmiennych zdefiniowanych w innym miejscu. Jednym z przykładów jest praca z dużymi macierzy i znalezienie jednej lokalizacji z pewnymi cechami. Następująca metoda zwraca **odwołanie** do tego magazynu w macierzy:

[!code-csharp[FindReturningRef](~/samples/snippets/csharp/new-in-7/MatrixSearch.cs#FindReturningRef "Find returning by reference")]

Można zadeklarować wartość zwracaną `ref` jako i zmodyfikować tę wartość w macierzy, jak pokazano w poniższym kodzie:

[!code-csharp[AssignRefReturn](~/samples/snippets/csharp/new-in-7/Program.cs#AssignRefReturn "Assign ref return")]

Język C# ma kilka reguł, które chronią przed nadużywaniem `ref` mieszkańców i zwraca:

- Należy dodać `ref` słowo kluczowe do podpisu `return` metody i do wszystkich instrukcji w metodzie.
  - To sprawia, że jasne, że metoda zwraca przez odwołanie w całej metody.
- A `ref return` mogą być przypisane do zmiennej wartości lub zmiennej. `ref`
  - Wywołujący określa, czy zwracana wartość jest kopiowana, czy nie. Pominięcie modyfikatora `ref` podczas przypisywania zwracanej wartości wskazuje, że wywołujący chce kopię wartości, a nie odwołanie do magazynu.
- Nie można przypisać standardowej wartości zwracanej metody do zmiennej `ref` lokalnej.
  - To nie zezwala na stwierdzenia takie jak`ref int i = sequence.Count();`
- Nie można zwrócić `ref` do zmiennej, której okres istnienia nie wykracza poza wykonanie metody.
  - Oznacza to, że nie można zwrócić odwołania do zmiennej lokalnej lub zmiennej o podobnym zakresie.
- `ref`miejscowych i zwraca nie mogą być używane z metodami asynchronizowymi.
  - Kompilator nie może wiedzieć, czy zmienna, do którego istnieje odwołanie, została ustawiona na wartość końcową, gdy zwracana jest metoda asynchronizowana.

Dodanie ref locals i ref zwraca umożliwia algorytmy, które są bardziej wydajne, unikając kopiowania wartości lub wykonywania operacji dereferencing wiele razy.

Dodanie `ref` do wartości zwracanej jest [zmianą zgodną ze źródłem](version-update-considerations.md#source-compatible-changes). Istniejący kod kompiluje, ale wartość zwracana ref jest kopiowana po przypisaniu. Wywołujący muszą zaktualizować magazyn dla wartości `ref` zwracanej do zmiennej lokalnej do przechowywania zwracanego jako odwołania.

Aby uzyskać więcej informacji, zobacz artykuł [słowiowa ref.](../language-reference/keywords/ref.md)

## <a name="local-functions"></a>Funkcje lokalne

Wiele projektów dla klas zawiera metody, które są wywoływane tylko z jednej lokalizacji. Te dodatkowe metody prywatne zachować każdą metodę małe i skoncentrowane. *Funkcje lokalne* umożliwiają deklarowanie metod w kontekście innej metody. Funkcje lokalne ułatwiają czytelnikom klasy, aby zobaczyć, że metoda lokalna jest wywoływana tylko z kontekstu, w którym jest zadeklarowany.

Istnieją dwa typowe przypadki użycia dla funkcji lokalnych: metody iteratora publicznego i publiczne metody asynchronizowania. Oba typy metod generują kod, który zgłasza błędy później niż programiści mogą oczekiwać. W metodach iteratora wszelkie wyjątki są obserwowane tylko podczas wywoływania kodu, który wylicza zwróconą sekwencję. W metodach asynchronizowych wszelkie wyjątki są obserwowane tylko wtedy, gdy zwracany `Task` jest oczekiwany. Poniższy przykład pokazuje oddzielenie sprawdzania poprawności parametru z implementacji iteratora przy użyciu funkcji lokalnej:

[!code-csharp[22_IteratorMethodLocal](~/samples/snippets/csharp/new-in-7/Iterator.cs#IteratorMethodLocal "Iterator method with local function")]

Tę samą technikę `async` można zastosować za pomocą metod, aby upewnić się, że wyjątki wynikające z sprawdzania poprawności argumentów są generowane przed rozpoczęciem pracy asynchronicznej:

[!code-csharp[TaskExample](~/samples/snippets/csharp/new-in-7/AsyncWork.cs#TaskExample "Task returning method with local function")]

> [!NOTE]
> Niektóre projekty, które są obsługiwane przez funkcje lokalne można również wykonać za pomocą *wyrażeń lambda*. Aby uzyskać więcej informacji, zobacz [Funkcje lokalne a wyrażenia lambda](../programming-guide/classes-and-structs/local-functions.md#local-functions-vs-lambda-expressions).

## <a name="more-expression-bodied-members"></a>Więcej członków wyrazu

C# 6 wprowadzono [elementy członkowskie zabudowane wyrażenia](csharp-6.md#expression-bodied-function-members) dla funkcji członkowskich i właściwości tylko do odczytu. C# 7.0 rozszerza dozwolone elementy członkowskie, które mogą być implementowane jako wyrażenia. W języku C# 7.0 można zaimplementować `set` *konstruktory,* *finalizatory* `get` i akcesory we *właściwościach* i *indeksatorach.* Poniższy kod przedstawia przykłady każdego z nich:

[!code-csharp[ExpressionBodiedMembers](~/samples/snippets/csharp/new-in-7/expressionmembers.cs#ExpressionBodiedEverything "new expression-bodied members")]

> [!NOTE]
> W tym przykładzie nie wymaga finalizatora, ale jest wyświetlany, aby zademonstrować składnię. Nie należy implementować finalizatora w klasie, chyba że jest to konieczne do uwolnienia zasobów niezarządzanych. Należy również rozważyć <xref:System.Runtime.InteropServices.SafeHandle> użycie klasy zamiast bezpośredniego zarządzania zasobami niezarządzanymi.

Te nowe lokalizacje dla członków zabudowanych wyrażenia stanowią ważny punkt kontrolny dla języka C#: Te funkcje zostały zaimplementowane przez członków społeczności pracujących nad projektem [Roslyn](https://github.com/dotnet/Roslyn) open source.

Zmiana metody na element członkowski zabudowany wyrażenie jest [zmianą zgodną z binarną](version-update-considerations.md#binary-compatible-changes).

## <a name="throw-expressions"></a>Wyrażenia throw

W języku `throw` C#zawsze było stwierdzeniem. Ponieważ `throw` jest instrukcja, a nie wyrażenie, nie było konstrukcji Języka C#, gdzie nie można go użyć. Obejmowały one wyrażenia warunkowe, wyrażenia scalania null i niektóre wyrażenia lambda. Dodanie elementów członkowskich zabudowanych wyrażeniami `throw` dodaje więcej lokalizacji, w których wyrażenia byłyby przydatne. Tak, że można napisać dowolną z tych konstrukcji, C# 7.0 wprowadza [*throw wyrażeń*](../language-reference/keywords/throw.md#the-throw-expression).

To dodanie ułatwia pisanie kodu opartego na wyrażeniach. Nie potrzebujesz dodatkowych instrukcji do sprawdzania błędów.

## <a name="generalized-async-return-types"></a>Uogólnione typy zwrotów asynchronizowanych

Zwracanie `Task` obiektu z metod asynchroniiowych może wprowadzić wąskie gardła wydajności w niektórych ścieżkach. `Task`jest typem odwołania, więc użycie go oznacza przydzielanie obiektu. W przypadkach, gdy metoda `async` zadeklarowana za pomocą modyfikatora zwraca wynik w pamięci podręcznej lub kończy się synchronicznie, dodatkowe alokacje mogą stać się znaczący koszt czasu w krytycznych sekcjach kodu wydajności. Może stać się kosztowne, jeśli te alokacje występują w ciasnych pętli.

Nowa funkcja języka oznacza, że typy zwracania `Task`metody `Task<T>`asynchronizowej nie są ograniczone do , i `void`. Zwracany typ musi nadal spełniać wzorzec asynchronii, co oznacza, że `GetAwaiter` metoda musi być dostępna. Jako jeden konkretny `ValueTask` przykład, typ został dodany do platformy .NET, aby korzystać z tej nowej funkcji języka:

[!code-csharp[UsingValueTask](~/samples/snippets/csharp/new-in-7/AsyncWork.cs#UsingValueTask "Using ValueTask")]

> [!NOTE]
> Należy dodać pakiet [`System.Threading.Tasks.Extensions`](https://www.nuget.org/packages/System.Threading.Tasks.Extensions/) NuGet w celu <xref:System.Threading.Tasks.ValueTask%601> użycia typu.

To ulepszenie jest najbardziej przydatne dla autorów biblioteki, aby uniknąć przydzielania kodu krytycznego `Task` w wydajności.

## <a name="numeric-literal-syntax-improvements"></a>Ulepszenia składni literału liczbowego

Błędna interpretacja stałych liczbowych może utrudnić zrozumienie kodu podczas czytania go po raz pierwszy. Maski bitowe lub inne wartości symboliczne są podatne na nieporozumienia. C# 7.0 zawiera dwie nowe funkcje do pisania liczb w najbardziej czytelny sposób do zamierzonego zastosowania: *literały binarne*i *separatory cyfr*.

W tych czasach, gdy tworzysz maski bitowe lub gdy binarna reprezentacja liczby tworzy najbardziej czytelny kod, zapisz tę liczbę w formacie binarnym:

[!code-csharp[ThousandSeparators](~/samples/snippets/csharp/new-in-7/Program.cs#ThousandSeparators "Thousands separators")]

Na `0b` początku stałej wskazuje, że liczba jest zapisywana jako liczba binarna. Liczby binarne mogą się długo, więc często łatwiej jest zobaczyć wzorce bitowe, wprowadzając separator `_` jako cyfrę, jak pokazano powyżej w stałej binarnej. Separator cyfr może pojawić się w dowolnym miejscu stałej. W przypadku liczb bazowych 10 często używa się go jako separatora tysięcy:

[!code-csharp[LargeIntegers](~/samples/snippets/csharp/new-in-7/Program.cs#LargeIntegers "Large integer")]

Separator cyfr może być `decimal` `float`używany `double` z , i typy, jak również:

[!code-csharp[OtherConstants](~/samples/snippets/csharp/new-in-7/Program.cs#OtherConstants "non-integral constants")]

Razem wzięte, można zadeklarować stałe numeryczne o wiele bardziej czytelności.

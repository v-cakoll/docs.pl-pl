---
title: Metody — przewodnik C#
description: Przegląd metod, parametrów metod i wartości zwracane — metoda
keywords: .NET, .NET Core, C#
author: rpetrusha
ms.author: ronpet
ms.date: 10/26/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 577a8527-1081-4b36-9b9e-0685b6553c6e
ms.openlocfilehash: 526cd6d269c7c089f6547fcf243b43e411037d13
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="methods"></a>Metody #

Metoda jest blok kodu, który zawiera serię instrukcji. Program powoduje, że instrukcje, które ma być wykonane przez wywołanie metody i określanie żadnych argumentów wymaganej metody. W języku C# co wykonanie instrukcji jest wykonywane w kontekście metody. `Main` Metoda jest punkt wejścia dla każdej aplikacji C# i jest wywoływane przez środowisko uruchomieniowe języka wspólnego (CLR), gdy program jest uruchomiony.

> [!NOTE]
> W tym temacie omówiono nazwane metody. Aby uzyskać informacje na temat funkcji anonimowych, zobacz [funkcje anonimowe](programming-guide/statements-expressions-operators/anonymous-functions.md).

Ten temat zawiera następujące sekcje:

- [Podpisy — metoda](#signatures)
- [Wywołanie metody](#invocation)
- [Dziedziczona i przesłoniętej metody](#inherited)
- [Przekazywanie parametrów](#passing)
  - [Przekazywanie parametrów przez wartość](#byval)
  - [Przekazywanie parametrów przez odwołanie](#byref)
  - [Tablice parametrów](#paramarray)
- [Opcjonalne parametry i argumenty](#optional)
- [Wartości zwracane](#return)
- [Metody rozszerzenia](#extension)
- [Metody asynchroniczne](#async)
- [Elementy członkowskie z wyrażeniem w treści](#expr)
- [Iteratory](#iterators)

<a name="signatures"></a>
## <a name="method-signatures"></a>Podpisy — metoda ##

Metody są zadeklarowane w `class` lub `struct` , określając:

- Opcjonalny dostęp na poziomie, takich jak `public` lub `private`. Wartość domyślna to `private`.
- Modyfikatory opcjonalne, takie jak `abstract` lub `sealed`.
- Wartość zwracana lub `void` Jeśli metoda ma wartość none.
- Nazwa metody.
- Parametry metody. Parametry metody są ujęte w nawiasy i są oddzielone przecinkami. Puste nawiasy wskazują, że metoda nie wymaga parametrów.

Części te tworzą razem podpis metody.

> [!NOTE]
> Typem zwracanym metody nie jest częścią podpis metody na potrzeby przeciążenie metody. Jednak jest częścią podpis metody podczas określania zgodności między delegata i wskazujący do metody.

W poniższym przykładzie zdefiniowano klasę o nazwie `Motorcycle` zawiera pięć metod:

[!code-csharp[csSnippets.Methods#40](../../samples/snippets/csharp/concepts/methods/methods40.cs#40)]

Należy pamiętać, że `Motorcycle` klasa zawiera metody przeciążonej `Drive`. Dwie metody mają taką samą nazwę, ale należy zróżnicować ich typy parametrów.

<a name="invocation"></a>
## <a name="method-invocation"></a>Wywołanie metody ##

Metody mogą być *wystąpienia* lub *statycznych*. Wywoływanie metody wystąpienia wymaga utworzenia wystąpienia obiektu, a następnie wywołać metodę dla tego obiektu; metody wystąpienia działa na to wystąpienie i jego dane. Wywołanie metody statycznej odwołując nazwę typu, do którego należy metoda; Działanie metody statyczne nie działają na dane wystąpienia. Próba wywołania metody statycznej za pomocą wystąpienia obiektu generuje błąd kompilatora.

Wywoływanie metody jest podobne do uzyskiwania dostępu do pola. Po nazwie obiektu (w przypadku wywoływania metody wystąpienia) lub nazwa typu (jeśli wywołujesz `static` metody), Dodaj okres, nazwę metody i nawiasów. Argumenty są wyświetlane w nawiasach i są oddzielone przecinkami.

Definicja metody określa nazwy i typy parametrów, które są wymagane. Gdy obiekt wywołujący wywołuje metodę, zapewnia konkretnych wartości, nazywanych argumenty dla każdego parametru. Argumenty muszą być zgodne z typem parametru, ale nazwa argumentu, jeśli jest on używany w wywoływanym kodzie nie ma być taki sam, jak parametr o nazwie w metodzie. W poniższym przykładzie `Square` metoda zawiera jeden parametr typu `int` o nazwie *i*. Pierwsza metoda wywołania przekazuje `Square` metody zmienną typu `int` o nazwie *num*; druga, stałej liczbowej; a trzeci, wyrażenia.

[!code-csharp[csSnippets.Methods#74](../../samples/snippets/csharp/concepts/methods/params74.cs#74)]

Argumenty pozycyjne; używane najczęściej wywołania metody dostarcza mu argumentów w tej samej kolejności jak parametry metody. Metody `Motorcycle` klasa może zostać wywołana w związku z tym jak w poniższym przykładzie. Wywołanie `Drive` metody, na przykład zawiera dwa argumenty, które odpowiadają tych dwóch parametrów w składni metody. Wartość staje się pierwszym `miles` parametr, druga wartość `speed` parametru.

[!code-csharp[csSnippets.Methods#41](../../samples/snippets/csharp/concepts/methods/methods40.cs#41)]

Można również używać *argumentami nazwanymi* zamiast argumenty pozycyjne podczas wywoływania metody. Przy użyciu nazwane argumenty, określ nazwę parametru znakiem dwukropka (":") i argumentu. Argumenty metody może występować w dowolnej kolejności tak długo, jak podano wszystkich wymaganych argumentów. W poniższym przykładzie użyto nazwanych argumentów do wywołania `TestMotorcycle.Drive` metody. W tym przykładzie nazwane argumenty są przekazywane w przeciwną kolejności w liście parametrów metody.

[!code-csharp[csSnippets.Methods#45](../../samples/snippets/csharp/concepts/methods/named1.cs#45)]

Można wywołać metody za pomocą obu argumentów pozycyjnych i argumentami nazwanymi. Argument pozycyjny nie może jednak wykonać nazwany argument. Poniższy przykład przedstawia wywoływanie `TestMotorcycle.Drive` metody z poprzedniego przykładu przy użyciu jeden argument pozycyjny i jednego argumentu nazwanego.

[!code-csharp[csSnippets.Methods#46](../../samples/snippets/csharp/concepts/methods/named2.cs#46)]

 <a name="inherited"></a>
 ##<a name="inherited-and-overridden-methods"></a>Dziedziczona i przesłoniętej metody ##

Oprócz elementów członkowskich, które są jawnie zdefiniowane w typie typ dziedziczy elementów członkowskich zdefiniowanych w jej klas podstawowych. Ponieważ wszystkie typy w systemie typ zarządzany dziedziczy pośrednio ani bezpośrednio po <xref:System.Object> klasa, wszystkie typy dziedziczy jej elementów członkowskich, takich jak <xref:System.Object.Equals(System.Object)>, <xref:System.Object.GetType>, i <xref:System.Object.ToString>. W poniższym przykładzie zdefiniowano `Person` klasy, tworzy dwa `Person` obiekty i wywołuje `Person.Equals` metodę, aby sprawdzić, czy dwa obiekty są równe. `Equals` Metody, jednak nie jest zdefiniowany w `Person` klasy; został on odziedziczony po <xref:System.Object>.

[!code-csharp[csSnippets.Methods#104](../../samples/snippets/csharp/concepts/methods/inherited1.cs#104)]

Typy, można zastąpić dziedziczone elementy członkowskie przy użyciu `override` — słowo kluczowe i udostępnia implementację dla przeciążonej. Podpis metody musi być taka sama jak przesłoniętej metody. Poniższy przykład przypomina poprzedni, z wyjątkiem tego, że zastępuje on <xref:System.Object.Equals(System.Object)> metody. (Zastępuje ona również <xref:System.Object.GetHashCode> metody, ponieważ te dwie metody są przeznaczone do zapewnić spójne wyniki.)

[!code-csharp[csSnippets.Methods#105](../../samples/snippets/csharp/concepts/methods/overridden1.cs#105)]

<a name="passing"></a>
## <a name="passing-parameters"></a>Przekazywanie parametrów ##

Typy w języku C# są albo *typów wartości* lub *typy referencyjne*. Listę typów wartości wbudowanych, zobacz [i zmiennymi](./tour-of-csharp/types-and-variables.md). Domyślnie oraz typy wartości i typy referencyjne są przekazywane do metody przez wartość.

<a name="byval"></a>
### <a name="passing-parameters-by-value"></a>Przekazywanie parametrów przez wartość ###

Gdy typ wartości jest przekazywany do metody przez wartość, kopię obiektu, a nie samego obiektu jest przekazywany do metody. W związku z tym zmiany wprowadzone w obiekcie w nazwie metody nie mają wpływu na oryginalny obiekt zwrócona sterowania do obiektu wywołującego.

Poniższy przykład przekazuje do metody typu wartości przez wartość i wywołaną metodę próbuje zmienić wartość typu wartości. Definiuje zmienną typu `int`, który jest typem wartości, inicjuje jego wartość 20 i przekazuje je do metody o nazwie `ModifyValue` która zmieni wartość zmiennej do 30. Gdy metoda zwróci wartość, jednak wartość zmiennej pozostanie bez zmian.

[!code-csharp[csSnippets.Methods#10](../../samples/snippets/csharp/concepts/methods/byvalue10.cs#10)]

Jeśli obiekt typu referencyjnego jest przekazywany do metody według wartości, odwołania do obiektu jest przekazywany przez wartość. Oznacza to, że metoda odbiera nie sam obiekt, ale argument, który wskazuje lokalizację, do obiektu. Jeśli zmienisz element członkowski obiektu przy użyciu tego odwołania, zmiana ta jest uwzględniana w obiekcie zwrócona do wywoływania metody kontroli. Jednak zastępuje obiekt przekazany do metody nie ma wpływu na oryginalny obiekt zwrócona sterowania do obiektu wywołującego.

W poniższym przykładzie zdefiniowano klasę (który jest typem referencyjnym) o nazwie `SampleRefType`. Metoda tworzy `SampleRefType` obiektów, przypisuje 44 do jego `value` pól i przekazuje obiekt do `ModifyObject` metody. W tym przykładzie jest zasadniczo sam efekt co w poprzednim przykładzie — przekazuje argumentu przez wartość do metody. Ale ponieważ jest używany typ referencyjny, wynik jest inny. Ze zmianami, które jest przeprowadzane w `ModifyObject` do `obj.value` pola również zmiany `value` pole argumentu, `rt`w `Main` metodę 33, jako dane wyjściowe w przykładzie.

[!code-csharp[csSnippets.Methods#42](../../samples/snippets/csharp/concepts/methods/byvalue42.cs#42)]

<a name="byref"></a>
### <a name="passing-parameters-by-reference"></a>Przekazywanie parametrów przez odwołanie ###

Należy przekazać parametr przez odwołanie, jeśli chcesz zmienić wartości argumentu w metodzie i chcesz refect zmiana, gdy formant powróci do wywoływania metody. Aby przekazać parametr przez odwołanie, należy użyć [ `ref` ](language-reference/keywords/ref.md) lub [ `out` ](language-reference/keywords/out-parameter-modifier.md) — słowo kluczowe. Można również przekazać wartość przez odwołanie, aby unikać kopiowania, ale nadal uniemożliwiają zmiany przy użyciu [ `in` ](language-reference/keywords/in-parameter-modifier.md) — słowo kluczowe.

Poniższy przykład jest taki sam jak poprzedni, z wyjątkiem wartość jest przekazywana przez odwołanie do `ModifyValue` metody. Wartość parametru jest modyfikacji w `ModifyValue` metody, zmianę wartości jest odzwierciedlone zwrócona sterowania do obiektu wywołującego.

[!code-csharp[csSnippets.Methods#106](../../samples/snippets/csharp/concepts/methods/byref106.cs#106)]

Typowe wzorzec, który korzysta z parametrami ref obejmuje zamianę wartości zmiennych. Dwie zmienne są przekazywane do metody przez odwołanie, a metoda zamienia ich zawartość. Poniższy przykład zamienia wartości będące liczbami całkowitymi.

[!code-csharp[csSnippets.Methods#106](../../samples/snippets/csharp/concepts/methods/swap107.cs#107)]

Przekazywanie parametrów typu Odwołanie umożliwia zmianę wartości odwołania do samej siebie, a nie wartość jego poszczególne elementy lub pól.

<a name="paramarray"></a>
### <a name="parameter-arrays"></a>Tablice parametrów ###

Czasami wymaganie określić dokładną liczbą argumentów do metody są restrykcyjne. Za pomocą `params` — słowo kluczowe, aby wskazać, że parametr jest tablicą parametrów, musisz zezwolić na metodę do wywołania z różną liczbą argumentów. Parametr oznaczane `params` — słowo kluczowe musi być typem tablicy i musi być ostatnim parametrem na liście parametrów metody.

Obiekt wywołujący następnie można wywołać metody na trzy sposoby:

- Przez przekazanie tablicy odpowiedniego typu, który zawiera odpowiednią liczbę elementów.
- Przez przekazanie rozdzielana przecinkami lista oddzielne argumenty odpowiedniego typu metody.
- Zapewniając nie argument tablicy parametrów.

W poniższym przykładzie zdefiniowano metodę o nazwie `DoStringOperation` wykonująca operację ciągu określonego przez jej pierwszy parametr `StringOperation` element członkowski wyliczenia. Ciągi, na których jest do wykonania tej operacji są zdefiniowane w tablicy parametrów. `Main` Metody przedstawiono wszystkie trzy sposoby wywołania metody. Należy pamiętać, że metoda oznakowane `params` — słowo kluczowe muszą być przygotowane do obsługi sytuacji, w których nie podano argumentu dla tablicy parametrów, aby jego wartość wynosi `null`.

[!code-csharp[csSnippets.Methods#106](../../samples/snippets/csharp/concepts/methods/byref108.cs#108)]

<a name="optional"></a>
## <a name="optional-parameters-and-arguments"></a>Opcjonalne parametry i argumenty ##

Definicja metody można określić, że parametry są wymagane lub ich są opcjonalne. Domyślnie nie są wymagane parametry. Parametry opcjonalne są określone przez dołączenie wartości domyślnej parametru w definicji metody. Po wywołaniu metody, jeśli nie podano argumentu dla parametru opcjonalnego, zamiast niego jest używana wartość domyślna.

Wartość domyślna parametru musi być przypisany przez jedną z następujących rodzajów wyrażeń:

- Stała, takich jak literał lub numer.
- Wyrażenie w postaci `new ValType`, gdzie `ValType` jest typem wartości. Należy pamiętać, że wywołuje to typ wartości niejawne domyślnego konstruktora, który nie jest faktycznego elementu członkowskiego typu.
- Wyrażenie w postaci `default(ValType)`, gdzie `ValType` jest typem wartości.

Jeśli metoda obejmuje zarówno wymaganych i opcjonalnych parametrów, opcjonalne parametry są definiowane na końcu listy parametrów po wszystkich wymaganych parametrów.

W poniższym przykładzie zdefiniowano metody `ExampleMethod`, która ma wymagana i dwa parametry opcjonalne.

[!code-csharp[csSnippets.Methods#21](../../samples/snippets/csharp/concepts/methods/optional1.cs#21)]

Jeśli w wywołaniu metody z wielu argumentów opcjonalnych argumentów pozycyjnych, wywołujący podać argument wszystkie parametry opcjonalne od pierwszego do ostatnią, dla którego podano argumentu. W przypadku programu `ExampleMethod` metody, na przykład, jeśli element wywołujący dostarcza argument `description` parametru, jego należy również podać po jednej dla `optionalInt` parametru. `opt.ExampleMethod(2, 2, "Addition of 2 and 2");` to wywołanie prawidłowej metody; `opt.ExampleMethod(2, , "Addition of 2 and 0);` generuje "Brak argumentu" błąd kompilatora.

Jeśli metoda jest wywoływana przy użyciu argumentów nazwanych lub kombinacja argumentów pozycyjnych i nazwane, wywołujący można pominąć argumenty, które należy wykonać ostatni argument pozycyjny w wywołaniu metody.

Następujące przykładowe wywołania `ExampleMethod` metody trzy razy.  Wywołania metody dwa pierwsze użycie argumentów pozycyjnych. Pierwszy pomija oba argumenty opcjonalne, podczas gdy druga pomija ostatni argument. Trzeci wywołanie metody dostarcza argument pozycyjny dla wymaganego parametru, ale używa nazwany argument podania wartości do `description` parametru pomijając `optionalInt` argumentu.

[!code-csharp[csSnippets.Methods#22](../../samples/snippets/csharp/concepts/methods/optional1.cs#22)]

Korzystanie z parametrów ma wpływ na *przeciążenia*, czy w sposób, w którym kompilator języka C# Określa, które przeładowanie określonego powinna być wywoływana przez wywołanie metody, w następujący sposób:

- Metoda, indeksator lub Konstruktor jest kandydatem do wykonania, jeśli każdego z jego parametrów jest opcjonalny, albo odpowiada według nazwy lub stanie pojedynczy argument w instrukcji wywołującego, oraz że argument można przekonwertować na typ parametru.
- Jeśli zostanie znaleziony więcej niż jednego kandydata, zasady rozpoznawania przeciążenia preferowanych konwersje są stosowane do argumentów, które zostały jawnie określone. Pominięcia Argumenty opcjonalne parametry są ignorowane.
- Jeśli dwa kandydatów zostaną ocenione jako jednakowo dobry, preferencji prowadzi do kandydujących, który nie ma następujące parametry opcjonalne dla których argumenty zostały pominięte w wywołaniu. Jest to konsekwencją Ogólne preferencji w wiązaniem dla elementów, które mają mniej parametrów.

 <a name="return"></a>
 ## <a name="return-values"></a>Zwracane wartości ##

Metody może zwracać wartości do obiektu wywołującego. Jeśli nie jest zwracany typ (typ wyświetlanych przed nazwę metody) `void`, metoda może zwracać wartości przy użyciu `return` — słowo kluczowe. Instrukcja zawierająca `return` — słowo kluczowe następuje zmienna, stała lub wyrażenie, które jest zgodny z typem zwracanym zwraca tę wartość do wywołującego metody. Metod innych niż void zwracany typ muszą korzystać z `return` — słowo kluczowe, aby zwrócić wartość. `return` — Słowo kluczowe również zatrzymuje wykonywanie metody.

Jeśli typem zwracanym jest `void`, `return` instrukcji bez wartości, warto nadal zatrzymuje wykonywanie metody. Bez `return` — słowo kluczowe, metoda spowoduje zatrzymanie wykonywania, gdy zostanie osiągnięty koniec bloku kodu.

Na przykład użyć te dwie metody `return` — słowo kluczowe do zwrócenia liczb całkowitych:

[!code-csharp[csSnippets.Methods#44](../../samples/snippets/csharp/concepts/methods/return44.cs#44)]

Aby użyć wartość zwracana z metody, metody wywołującej użyć wywołania metody sam gdziekolwiek się, że wartość tego samego typu będą wystarczające. Można także przypisać zwracana wartość do zmiennej. Na przykład następujący przykładowy kod dwóch realizację tego samego celu:

[!code-csharp[csSnippets.Methods#45](../../samples/snippets/csharp/concepts/methods/return44.cs#45)]

[!code-csharp[csSnippets.Methods#46](../../samples/snippets/csharp/concepts/methods/return44.cs#46)]

Przy użyciu zmiennej lokalnej, w tym przypadku `result`, aby przechowywać wartość jest opcjonalna. Może pomóc zwiększyć czytelność kodu, lub może być konieczne, jeśli zachodzi potrzeba przechowywania oryginalnej wartości argumentu dla całego zakresu metody.

Czasami ma metodę do zwrócenia więcej niż jedną wartość. Począwszy od wersji 7.0 C#, można to zrobić łatwo za pomocą *typu krotki* i *literały spójnej kolekcji*. Typ krotki definiuje typy danych elementów spójnej kolekcji. Literały krotki zawierają rzeczywiste wartości zwracane spójnej kolekcji. W poniższym przykładzie `(string, string, string, int)` definiuje typ krotki, która jest zwracana w wyniku `GetPersonalInfo` metody. Wyrażenie `(per.FirstName, per.MiddleName, per.LastName, per.Age)` jest literałem; metoda zwraca nazwę pierwszego, drugie imię i nazwisko, wraz z wiek, z spójnej kolekcji `PersonInfo` obiektu.

```csharp
public (string, string, string, int) GetPersonalInfo(string id)
{
    PersonInfo per = PersonInfo.RetrieveInfoById(id);
    if (per != null)
       return (per.FirstName, per.MiddleName, per.LastName, per.Age);
    else
       return null;
}
```

Obiekt wywołujący będą mogły używać zwrócony krotki z kodu podobne do poniższych:

```csharp
var person = GetPersonalInfo("111111111")
if (person != null)
   Console.WriteLine("{person.Item1} {person.Item3}: age = {person.Item4}");
```

Można również przypisać nazwy do elementów spójnej kolekcji w definicji typu krotki. W poniższym przykładzie przedstawiono alternatywnej wersji `GetPersonalInfo` metody, która używa o nazwie elementy:

```csharp
public (string FName, string MName, string LName, int Age) GetPersonalInfo(string id)
{
    PersonInfo per = PersonInfo.RetrieveInfoById(id);
    if (per != null)
       return (per.FirstName, per.MiddleName, per.LastName, per.Age);
    else
       return null;
}
```

Poprzednie wywołanie `GetPersonInfo` metoda może być modyfikowany w następujący sposób:

```csharp
var person = GetPersonalInfo("111111111");
if (person != null)
   Console.WriteLine("{person.FName} {person.LName}: age = {person.Age}");
```

Jeśli metoda jest przekazywana tablicy jako argument i modyfikuje wartość poszczególne elementy, nie jest konieczne metoda ma zwracać tablicy, chociaż można wybrać w tym celu dobrej stylu lub funkcjonalności przepływu wartości.  To dlatego C# przekazuje wszystkie typy referencyjne przez wartość i wartość odwołania do tablicy jest wskaźnik do tablicy. W poniższym przykładzie zmienia zawartość `values` tablicy, które zostały wprowadzone w `DoubleValues` metody są według przez kodu, który zawiera odwołanie do tablicy.

[!code-csharp[csSnippets.Methods#101](../../samples/snippets/csharp/concepts/methods/returnarray1.cs#101)]

 <a name="exten"></a>
 ## <a name="extension-methods"></a>Metody rozszerzenia ##

Zazwyczaj istnieją dwa sposoby dodawania metody do istniejącego typu:

- Modyfikowanie kodu źródłowego dla tego typu. Nie możesz tego zrobić, jeśli nie ma typu kodu źródłowego. I staje się on na istotne zmiany po dodaniu pola danych prywatne, do obsługi metody.
- Zdefiniuj nowej metody w klasie pochodnej. Metody nie można dodać w ten sposób używanie dziedziczenia dla innych typów, takich jak struktury i wyliczenia. Nie można być również wykorzystywane do "Dodaj" metodę do klasy zapieczętowanej.

Metody rozszerzenia umożliwiają "Dodaj" metody do istniejącego typu bez modyfikowania samego typu i wdrożeniu nowej metody w typie dziedziczonym. Metody rozszerzenia również nie musi znajdować się w tym samym zestawie co typ rozszerzany przez niego. Wywoływanie metody rozszerzenia, tak jakby był on członkiem zdefiniowanego typu.

Aby uzyskać więcej informacji, zobacz [metody rozszerzenia](programming-guide/classes-and-structs/extension-methods.md).

<a name="async"></a>
## <a name="async-methods"></a>Metody asynchroniczne ##

Korzystając z funkcji asynchronicznych, można wywoływać metod asynchronicznych bez za pomocą jawnego wywołania zwrotne i ręcznie dzielenia kodu wielu metod lub wyrażenia lambda.

Po zaznaczeniu metodę o [async](language-reference/keywords/async.md) modyfikator, można użyć [await](language-reference/keywords/await.md) operatora w metodzie. Gdy kontrolować osiągnie `await` wyrażenia w metodzie asynchronicznej formantu zwraca do wywołującego, gdy oczekiwano zadanie nie zostało ukończone i postęp w metodzie z `await` — słowo kluczowe jest wstrzymana, aż do zakończenia oczekiwano zadań. Po zakończeniu zadania wykonywania można wznowić w metodzie.

> [!NOTE]
> Metoda asynchroniczna zwraca do obiektu wywołującego po napotkaniu pierwszego oczekiwano obiekt, który nie został jeszcze ukończony lub pobiera na końcu metody asynchronicznej cokolwiek nastąpi najpierw.

Metoda asynchroniczna może mieć typ zwracany <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>, lub `void`. `void` Zwracany typ jest używany głównie w celu definiowania metod obsługi zdarzeń, gdy `void` zwracany typ jest wymagany. Metoda asynchroniczna zwracająca `void` nie jest oczekiwane, a obiekt wywołujący metody zwracające typ void nie może przechwytywać wyjątki, które metoda zgłasza. C# 7.0, po wydaniu, ułatwi to ograniczenie, aby umożliwić metody asynchronicznej [do zwrócenia dowolnego typu zadania przypominającej](https://github.com/ljw1004/roslyn/blob/features/async-return/docs/specs/feature%20-%20arbitrary%20async%20returns.md).

W poniższym przykładzie `DelayAsync` jest to metoda asynchroniczna, która zawiera instrukcję return, która zwraca liczbę całkowitą. Ponieważ jest to metoda asynchroniczna, jego deklaracji metody musi mieć typ zwracany `Task<int>`. Ponieważ typ zwracany jest `Task<int>`, oceny `await` wyrażenie w `DoSomethingAsync` tworzy całkowitą w następujący sposób `int result = await delayTask` pokazuje instrukcji.

[!code-csharp[csSnippets.Methods#102](../../samples/snippets/csharp/concepts/methods/async1.cs#102)]

Metoda asynchroniczna nie można zadeklarować żadnego [w](language-reference/keywords/in-parameter-modifier.md), [ref](language-reference/keywords/ref.md), lub [limit](language-reference/keywords/out-parameter-modifier.md) parametrów, ale można wywołać metody, które mają takie parametry.

 Aby uzyskać więcej informacji na temat metod asynchronicznych, zobacz [programowanie asynchroniczne z Async i Await](async.md), [przepływ sterowania w aplikacjach asynchronicznych](programming-guide/concepts/async/control-flow-in-async-programs.md), i [Async zwracać typów](programming-guide/concepts/async/async-return-types.md).

<a name="expr"></a>
## <a name="expression-bodied-members"></a>Zabudowanych wyrażenia elementów członkowskich ##

Jest często mają definicje — metoda, która po prostu zwrot wynik wyrażenia, lub które mają jednej instrukcji jako treść metody.  Brak skrót do definiowania tych metod, za pomocą składni `=>`:

```csharp
public Point Move(int dx, int dy) => new Point(x + dx, y + dy);
public void Print() => Console.WriteLine(First + " " + Last);
// Works with operators, properties, and indexers too.
public static Complex operator +(Complex a, Complex b) => a.Add(b);
public string Name => First + " " + Last;
public Customer this[long id] => store.LookupCustomer(id);
```

Jeśli metoda zwraca `void` lub jest to metoda asynchroniczna treści metody musi być wyrażeniem instrukcji (tak samo jak w przypadku wyrażeń lambda).  Właściwości i indeksatorów, muszą być w trybie tylko do odczytu i nie należy używać `get` akcesor — słowo kluczowe.

<a name="iterators"></a>
## <a name="iterators"></a>Iteratory ##

Iteratora wykonuje niestandardowych iteracji w kolekcji, takie jak listy lub tablicy. Używa iteratora [yield return](language-reference/keywords/yield.md) instrukcji, aby zwracany był każdy element jednym naraz. Gdy `yield return` osiągnięciu instrukcji bieżącej lokalizacji jest zapamiętanych tak, aby obiekt wywołujący może zażądać następnego elementu w sekwencji.

Może być zwracany typ iteratora <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, lub <xref:System.Collections.Generic.IEnumerator%601>.

Aby uzyskać więcej informacji, zobacz [Iteratory](programming-guide/concepts/iterators.md).

## <a name="see-also"></a>Zobacz także ##

[Modyfikatory dostępu](language-reference/keywords/access-modifiers.md)   
[Klasy statyczne i statyczni członkowie klas](programming-guide/classes-and-structs/static-classes-and-static-class-members.md)   
[Dziedziczenie](programming-guide/classes-and-structs/inheritance.md)   
[Klasy abstrakcyjne i zapieczętowane oraz członkowie klas](programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)   
[Parametry](language-reference/keywords/params.md)   
[limit](language-reference/keywords/out-parameter-modifier.md)   
[REF](language-reference/keywords/ref.md)   
[in](language-reference/keywords/in-parameter-modifier.md)   
[Przekazywanie parametrów](programming-guide/classes-and-structs/passing-parameters.md)

---
title: Metody — przewodnik języka C#
description: Przegląd metod, parametry metody i wartości zwracane metody
author: rpetrusha
ms.author: ronpet
ms.date: 05/21/2018
ms.assetid: 577a8527-1081-4b36-9b9e-0685b6553c6e
ms.openlocfilehash: 7ddc79a7d9864ecd7834cb75e23c9ad3a4320a91
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2019
ms.locfileid: "54415510"
---
# <a name="methods"></a>Metody #

Metoda jest blokiem kodu, który zawiera szereg instrukcji. Program powoduje, że instrukcji do wykonania przez wywołanie metody i określenie argumentów wymaganej metody. W języku C# co instrukcja wykonanych odbywa się w kontekście metody. `Main` Metoda jest punkt wejścia dla każdej aplikacji C# i jest wywoływana przez środowisko uruchomieniowe języka wspólnego (CLR), gdy program jest uruchomiony.

> [!NOTE]
> W tym temacie omówiono metody o nazwie. Aby uzyskać informacje na temat funkcji anonimowych zobacz [funkcjami anonimowymi](programming-guide/statements-expressions-operators/anonymous-functions.md).

Ten temat zawiera następujące sekcje:

- [Podpisy metod](#signatures)
- [Wywołanie metody](#invocation)
- [Metody dziedziczone i zastąpiona](#inherited)
- [Przekazywanie parametrów](#passing)
  - [Przekazywanie parametrów przez wartość](#byval)
  - [Przekazywanie parametrów przez odwołanie](#byref)
  - [Parameter — tablice](#paramarray)
- [Opcjonalne parametry i argumenty](#optional)
- [Wartości zwracane](#return)
- [Metody rozszerzenia](#extension)
- [Metody asynchroniczne](#async)
- [Elementy członkowskie z wyrażeniem w treści](#expr)
- [Iteratory](#iterators)

<a name="signatures"></a>
## <a name="method-signatures"></a>Podpisy metod ##

Metody są deklarowane w `class` lub `struct` przez określenie:

- Opcjonalny dostęp na poziomie, takich jak `public` lub `private`. Wartość domyślna to `private`.
- Modyfikatory opcjonalne, takie jak `abstract` lub `sealed`.
- Wartość zwracana lub `void` Jeśli metoda nie ma żadnego.
- Nazwa metody.
- Wszystkie parametry metody. Parametry metody są ujęte w nawiasy i są oddzielone przecinkami. Pustych nawiasów zwykłych wskazują, że metoda nie wymaga parametrów.

Te elementy tworzą razem podpis metody.

> [!NOTE]
> Zwracany typ metody nie jest część podpisu metody na potrzeby przeciążenie metody. Jednak jest część podpisu metody podczas określania zgodności między delegata i metody, która wskazuje.

W poniższym przykładzie zdefiniowano klasę o nazwie `Motorcycle` zawiera pięć metod:

[!code-csharp[csSnippets.Methods#40](../../samples/snippets/csharp/concepts/methods/methods40.cs#40)]

Należy pamiętać, że `Motorcycle` klasa zawiera metody przeciążonej, `Drive`. Dwie metody mają taką samą nazwę, ale należy zróżnicować za jego typy parametrów.

<a name="invocation"></a>
## <a name="method-invocation"></a>Wywołanie metody ##

Metody mogą być albo *wystąpienia* lub *statyczne*. Wywoływanie metody wystąpienia wymaga utworzenia wystąpienia obiektu, a następnie wywołać metodę dla tego obiektu; Metoda wystąpienia działa na tego wystąpienia i jego danych. Wywołaj metodę statyczną, odwołując się do nazwy typu, do którego należy metoda; działania metod statycznych nie działają na dane wystąpienia. Próba wywołania metody statycznej za pomocą wystąpienia obiektu generuje błąd kompilatora.

Wywołanie metody jest jak uzyskiwanie dostępu do pola. Po nazwę obiektu (jeśli wywołujesz metodę wystąpienia) lub nazwę typu (w przypadku wywołania `static` metoda), Dodaj okres, nazwy metody i nawiasy. Argumenty są wyświetlane w nawiasach i są oddzielone przecinkami.

Definicja metody określa nazwy i typy parametrów, które są wymagane. Jeśli obiekt wywołujący wywołuje metodę, udostępnia konkretnych wartości nazywanych argumentami — dla każdego parametru. Argumenty muszą być zgodne z typem parametru, ale nazwę argumentu, jeśli jest on używany w wywoływanym kodzie, nie trzeba być taka sama jak parametr o nazwie zdefiniowany w metodzie. W poniższym przykładzie `Square` metoda zawiera jeden parametr typu `int` o nazwie *i*. Pierwsza metoda wywołania przebiegów `Square` metoda zmienną typu `int` o nazwie *num*; drugi, stałej liczbowej; oraz trzeci, wyrażenie.

[!code-csharp[csSnippets.Methods#74](../../samples/snippets/csharp/concepts/methods/params74.cs#74)]

Najczęściej używany typ wywołania metody używane argumenty pozycyjne; dostarcza mu argumenty w kolejności parametrów metody. Metody `Motorcycle` klasy, w związku z tym może być wywoływana tak jak w poniższym przykładzie. Wywołanie `Drive` metody, na przykład zawiera dwa argumenty, które odpowiadają dwa parametry przy użyciu składni metody. Pierwszy staje się wartością `miles` parametr, drugi wartość `speed` parametru.

[!code-csharp[csSnippets.Methods#41](../../samples/snippets/csharp/concepts/methods/methods40.cs#41)]

Można również używać *argumenty nazwane* zamiast argumenty pozycyjne, podczas wywoływania metody. Przy użyciu nazwane argumenty, określ nazwę parametru z dwukropkiem (":") i argumentu. Argumenty do metody mogą być wyświetlane w dowolnej kolejności, tak długo, jak wszystkie wymagane argumenty są obecne. W poniższym przykładzie użyto argumentów nazwanych do wywołania `TestMotorcycle.Drive` metody. W tym przykładzie nazwane argumenty są przekazywane w kolejności przeciwnej w liście parametrów metody.

[!code-csharp[csSnippets.Methods#45](../../samples/snippets/csharp/concepts/methods/named1.cs#45)]

Można wywołać metody za pomocą obu argumentów pozycyjnych i argumenty nazwane. Argument pozycyjny nie można jednak wykonać argumentu nazwanego. Poniższy przykład przedstawia wywoływanie `TestMotorcycle.Drive` metodę jak w poprzednim przykładzie, za pomocą jednego argumentu pozycyjnego i jeden argument nazwany.

[!code-csharp[csSnippets.Methods#46](../../samples/snippets/csharp/concepts/methods/named2.cs#46)]

 <a name="inherited"></a>
 ## <a name="inherited-and-overridden-methods"></a>Metody dziedziczone i zastąpiona ##

Oprócz elementów członkowskich, które są jawnie zdefiniowane w typie typ dziedziczy składowych zdefiniowanych w jej klas podstawowych. Ponieważ wszystkie typy w systemie typu zarządzanego dziedziczy bezpośrednio lub pośrednio z <xref:System.Object> klasy, wszystkie typy odziedziczenie jego elementów członkowskich, takich jak <xref:System.Object.Equals(System.Object)>, <xref:System.Object.GetType>, i <xref:System.Object.ToString>. W poniższym przykładzie zdefiniowano `Person` klasy, są tworzone wystąpienia dwóch `Person` obiektów i wywołuje `Person.Equals` metodę pozwala ustalić, czy dwa obiekty są takie same. `Equals` Metody, jednak nie jest zdefiniowany w `Person` klasy; zostało ono odziedziczone <xref:System.Object>.

[!code-csharp[csSnippets.Methods#104](../../samples/snippets/csharp/concepts/methods/inherited1.cs#104)]

Typy można zastąpić dziedziczone elementy członkowskie przy użyciu `override` — słowo kluczowe i zapewniając implementację przeciążonej. Podpis metody musi być taka sama, jak w przypadku przeciążonej. Poniższy przykład jest podobne do pokazanego w poprzednim, z tą różnicą, że zastępuje ona <xref:System.Object.Equals(System.Object)> metody. (Zastępuje ona również <xref:System.Object.GetHashCode> metody, ponieważ te dwie metody są przeznaczone do zapewnić spójne wyniki.)

[!code-csharp[csSnippets.Methods#105](../../samples/snippets/csharp/concepts/methods/overridden1.cs#105)]

<a name="passing"></a>
## <a name="passing-parameters"></a>Przekazywanie parametrów ##

Typy w języku C# są albo *typy wartości* lub *typy odwołań*. Aby uzyskać listę typów wbudowanych wartości, zobacz [typy i zmienne](./tour-of-csharp/types-and-variables.md). Domyślnie typy odwołań i typy wartości są przekazywane do metody przez wartość.

<a name="byval"></a>
### <a name="passing-parameters-by-value"></a>Przekazywanie parametrów przez wartość ###

Gdy typ wartości jest przekazywany do metody przez wartość, kopię obiektu, a nie sam obiekt jest przekazywany do metody. W związku z tym zmiany do obiektu w metodzie wywoływanej nie mają wpływu na oryginalny obiekt gdy sterowanie powraca do obiektu wywołującego.

Poniższy przykład przekazuje do metody typu wartości przez wartość, a następnie wywoływana metoda próbuje zmienić wartość typu wartości. Definiuje zmienną typu `int`, który jest typem wartości, inicjuje jej wartość na 20 i przekazuje go do metody o nazwie `ModifyValue` który zmienia wartość zmiennej do 30. Gdy metoda zwróci wartość, jednak wartość zmiennej pozostaje bez zmian.

[!code-csharp[csSnippets.Methods#10](../../samples/snippets/csharp/concepts/methods/byvalue10.cs#10)]

Gdy obiekt typu referencyjnego jest przekazywany do metody przez wartość, odwołanie do obiektu jest przekazywany przez wartość. Oznacza to, że metoda odbiera nie samego obiektu, ale argument, który wskazuje lokalizację obiektu. Jeśli zmienisz członka obiektu za pomocą tego odwołania, zmiana jest odzwierciedlana w obiekcie, gdy sterowanie powraca do wywoływania metody. Jednak zastępując obiekt przekazany do metody nie ma wpływu na oryginalny obiekt gdy sterowanie powraca do obiektu wywołującego.

W poniższym przykładzie zdefiniowano klasę (który jest typem referencyjnym) o nazwie `SampleRefType`. Metoda tworzy `SampleRefType` obiektów, przypisuje 44 do jego `value` pola, a następnie przekazuje obiekt do `ModifyObject` metody. W tym przykładzie działa zasadniczo tak samo jak w poprzednim przykładzie — przekazaniem argumentu przez wartość do metody. Ale ponieważ jest używany typ odwołania, wynik jest inny. Ze zmianami, które znajduje się w `ModifyObject` do `obj.value` pola również zmiany `value` pole argumentu, `rt`w `Main` jako dane wyjściowe w przykładzie pokazano metodę 33.

[!code-csharp[csSnippets.Methods#42](../../samples/snippets/csharp/concepts/methods/byvalue42.cs#42)]

<a name="byref"></a>
### <a name="passing-parameters-by-reference"></a>Przekazywanie parametrów przez odwołanie ###

Należy podać parametr według odwołania, jeśli chcesz zmienić wartość argumentu w metodzie i ma na celu odzwierciedlenia tej zmiany, gdy sterowanie powraca do wywoływania metody. Aby przekazać parametr według odwołania, należy użyć [ `ref` ](language-reference/keywords/ref.md) lub [ `out` ](language-reference/keywords/out-parameter-modifier.md) — słowo kluczowe. Można również przekazać wartość przez odwołanie, aby unikać kopiowania, ale nadal zapobiec przy użyciu [ `in` ](language-reference/keywords/in-parameter-modifier.md) — słowo kluczowe.

Poniższy przykład jest taka sama jak poprzedni, z wyjątkiem wartość jest przekazywana przez odwołanie do `ModifyValue` metody. Po zmodyfikowaniu wartości parametru w `ModifyValue` znajduje odzwierciedlenie metody zmianę wartości, gdy sterowanie powraca do obiektu wywołującego.

[!code-csharp[csSnippets.Methods#106](../../samples/snippets/csharp/concepts/methods/byref106.cs#106)]

Typowy wzorzec, który używa parametrów ref obejmuje zamianę wartości zmiennych. Dwie zmienne jest przekazywany do metody za pomocą odwołania, a metoda zamienia ich zawartości. Poniższy przykład zamienia wartości całkowitych.

[!code-csharp[csSnippets.Methods#106](../../samples/snippets/csharp/concepts/methods/swap107.cs#107)]

Przekazywanie parametrów typu Odwołanie umożliwia zmianę wartości samo odwołanie, a nie wartość jego poszczególne elementy lub pola.

<a name="paramarray"></a>
### <a name="parameter-arrays"></a>Parameter — tablice ###

Czasami wymagania Określ dokładna liczba argumentów do metody jest restrykcyjne. Za pomocą `params` — słowo kluczowe, aby wskazać, że parametr jest tablicą parametrów, musisz zezwolić na metodę do wywołania z różną liczbą argumentów. Parametr oznakowane za pomocą `params` — słowo kluczowe musi być typem tablicy, a musi być ostatnim parametrem na liście parametrów metody.

Obiekt wywołujący może następnie wywołania metody w jednym z trzech sposobów:

- Przekazując tablicę odpowiedniego typu, który zawiera odpowiednią liczbę elementów.
- Przekazując rozdzielaną przecinkami listę pojedynczych argumentów odpowiedniego typu w metodzie.
- Zapewniając nie argument tablicy parametrów.

W poniższym przykładzie zdefiniowano metodę o nazwie `DoStringOperation` wykonująca operację ciągu określonego przez jej pierwszy parametr `StringOperation` element członkowski wyliczenia. Ciągi, na których jest do wykonania tej operacji są definiowane przez tablicy parametrów. `Main` Metoda przedstawiono wszystkie trzy sposoby wywoływania metody. Należy zauważyć, że metoda oznakowane za pomocą `params` — słowo kluczowe musi być przygotowana do obsługi przypadek, w którym nie zostaną dostarczone argumenty dla tablicy parametrów, aby jego wartość wynosi `null`.

[!code-csharp[csSnippets.Methods#106](../../samples/snippets/csharp/concepts/methods/byref108.cs#108)]

<a name="optional"></a>
## <a name="optional-parameters-and-arguments"></a>Opcjonalne parametry i argumenty ##

Definicję metody można określić, że jej parametry są wymagane lub czy są opcjonalne. Domyślnie parametry są wymagane. Następujące parametry opcjonalne są określone przez dołączenie wartości domyślnej parametru w definicji metody. Gdy metoda jest wywoływana, jeśli nie dostarczono żadnego argumentu dla parametru opcjonalnego, w zamian jest używana wartość domyślna.

Wartość domyślna parametru musi zostać przypisany przez jedną z następujących rodzajów wyrażeń:

- Stała, takich jak ciąg literału lub numer.
- Wyrażenie w formie `new ValType`, gdzie `ValType` jest typem wartości. Należy pamiętać, że wywołuje to typ wartości niejawnego domyślnego konstruktora, który nie jest faktycznej składowej typu.
- Wyrażenie w formie `default(ValType)`, gdzie `ValType` jest typem wartości.

Jeśli metoda zawiera zarówno wymaganych i opcjonalnych parametrów, opcjonalne parametry są definiowane na końcu listy parametrów po wszystkich wymaganych parametrów.

W poniższym przykładzie zdefiniowano metodę `ExampleMethod`, która ma jeden wymagany i dwa parametry opcjonalne.

[!code-csharp[csSnippets.Methods#21](../../samples/snippets/csharp/concepts/methods/optional1.cs#21)]

Gdy wywoływana jest metoda, za pomocą wielu argumentów opcjonalnych, za pomocą argumentów pozycyjnych, obiekt wywołujący musi podać argument dla wszystkich parametrów opcjonalnych z pierwszego w celu ostatni, dla którego zostanie podany argument. W przypadku właściwości `ExampleMethod` metody, na przykład, jeśli obiekt wywołujący dostarcza argument `description` parametru, jego należy również podać jeden dla `optionalInt` parametru. `opt.ExampleMethod(2, 2, "Addition of 2 and 2");` to wywołanie prawidłowej metody; `opt.ExampleMethod(2, , "Addition of 2 and 0");` generuje "Brak argumentu" błąd kompilatora.

Jeśli metoda jest wywoływana przy użyciu argumentów nazwanych lub kombinacji argumenty pozycyjne i nazwane, obiekt wywołujący, można pominąć argumenty, które należy wykonać ostatni argument pozycyjny w wywołaniu metody.

Poniższy przykład wywołuje `ExampleMethod` metoda trzy razy.  Wywołań metod pierwsze dwa użycia argumentów pozycyjnych. Pierwszy pomija oba argumenty opcjonalne, podczas gdy drugi pomija ostatni argument. Trzecie wywołanie metody dostarcza argument pozycyjny dla wymaganego parametru, ale używa argumentu nazwanego, aby podać wartość `description` parametru pomijając `optionalInt` argumentu.

[!code-csharp[csSnippets.Methods#22](../../samples/snippets/csharp/concepts/methods/optional1.cs#22)]

Ma wpływ na korzystanie z parametrów opcjonalnych *Rozpoznanie przeciążenia*, czy w sposób, w którym kompilator języka C# Określa, które przeładowanie określonego powinien być wywoływany przez wywołanie metody w następujący sposób:

- Metoda, indeksator lub Konstruktor jest kandydatem do wykonywania w przypadku każdego z jego parametrów jest opcjonalny albo odpowiada według nazwy lub pozycji, aby jeden argument w instrukcji wywołujące, i że argument można przekonwertować na typ parametru.
- Jeśli zostanie znalezione więcej niż jeden Release candidate, zasady rozpoznawania przeciążenia preferowanych konwersje są stosowane do argumentów, które są jawnie określone. Pominięty Argumenty opcjonalne parametry są ignorowane.
- Jeśli dwa kandydatów zostaną ocenione one równie dobrze, preferencji jest przesyłany do Release candidate, który nie ma parametrów opcjonalnych, które zostały pominięte argumentów w wywołaniu. Jest to konsekwencją Ogólne preferencji w przeciążeniu rozdzielczości dla kandydatów, które mają mniej parametrów.

 <a name="return"></a>
 ## <a name="return-values"></a>Zwracane wartości ##

Metody może zwrócić wartości do obiektu wywołującego. Jeśli nie jest zwracany typ (typu wymienionego przed nazwą metody) `void`, metoda może zwrócić wartość przy użyciu `return` — słowo kluczowe. Instrukcja zawierająca `return` — słowo kluczowe następuje zmiennej, stałej lub wyrażenia, który jest zgodny z typem zwracanym zwróci tę wartość do obiektu wywołującego metodę. Metody z innym niż void zwrotu typu są wymagane do użycia `return` — słowo kluczowe w celu zwrócenia wartości. `return` — Słowo kluczowe również zatrzymuje wykonywanie metody.

Jeśli typ zwracany jest `void`, `return` instrukcji bez wartości nadal jest użyteczne do zatrzymywania wykonywania metody. Bez `return` — słowo kluczowe, metoda wykonywanie zostanie przerwane po osiągnięciu końca bloku kodu.

Na przykład użyć tych dwóch metod `return` — słowo kluczowe, aby zwrócić liczb całkowitych:

[!code-csharp[csSnippets.Methods#44](../../samples/snippets/csharp/concepts/methods/return44.cs#44)]

Aby użyć wartości zwrócone z metody, wywoływania metody użyć wywołania metody które się dowolnym wartością tego samego typu może być wystarczające. Można także przypisać zwracana wartość do zmiennej. Na przykład poniższe dwa przykłady kodu osiągnięcia tego samego celu:

[!code-csharp[csSnippets.Methods#45](../../samples/snippets/csharp/concepts/methods/return44.cs#45)]

[!code-csharp[csSnippets.Methods#46](../../samples/snippets/csharp/concepts/methods/return44.cs#46)]

Za pomocą zmiennej lokalnej, w tym przypadku `result`, aby przechowywać wartość jest opcjonalna. Może ułatwić czytelność kodu lub może być konieczne, jeśli chcesz przechować oryginalnej wartości argumentu dla całego zakresu metody.

Czasami chcesz metodę do zwrócenia więcej niż jedną wartość. Począwszy od języka C# 7.0, możesz to łatwo zrobić przy użyciu *typy krotki* i *literałach krotek*. Typ krotki definiuje typy danych elementów krotki. Literałach krotek zawierają rzeczywiste wartości zwracane spójnej kolekcji. W poniższym przykładzie `(string, string, string, int)` definiuje typ spójnej kolekcji, który jest zwracany przez `GetPersonalInfo` metody. Wyrażenie `(per.FirstName, per.MiddleName, per.LastName, per.Age)` jest spójna kolekcja znajdująca się literału; metoda zwraca nazwę pierwszego, drugie imię i nazwisko, wraz z okresu ważności z `PersonInfo` obiektu.

```csharp
public (string, string, string, int) GetPersonalInfo(string id)
{
    PersonInfo per = PersonInfo.RetrieveInfoById(id);
    return (per.FirstName, per.MiddleName, per.LastName, per.Age);
}
```

Obiekt wywołujący mogły zwrócone spójna kolekcja znajdująca się z kodem, jak pokazano poniżej:

```csharp
var person = GetPersonalInfo("111111111")
Console.WriteLine("{person.Item1} {person.Item3}: age = {person.Item4}");
```

Również można przypisać nazwy elementów krotki w definicji typu krotki. W poniższym przykładzie pokazano alternatywnej wersji `GetPersonalInfo` metodę, która korzysta z nazwanych elementów:

```csharp
public (string FName, string MName, string LName, int Age) GetPersonalInfo(string id)
{
    PersonInfo per = PersonInfo.RetrieveInfoById(id);
    return (per.FirstName, per.MiddleName, per.LastName, per.Age);
}
```

Poprzednie wywołanie `GetPersonInfo` metoda może być modyfikowany w następujący sposób:

```csharp
var person = GetPersonalInfo("111111111");
Console.WriteLine("{person.FName} {person.LName}: age = {person.Age}");
```

Jeśli metoda jest przekazywana tablicę jako argument i modyfikuje wartość poszczególnych elementów, nie jest konieczne dla metody zwrócić tablicę, mimo że można to zrobić dla dobra stylu lub funkcjonalności przepływu wartości.  Jest to spowodowane C# przekazuje wszystkich typów odniesienia według wartości, a wartość odwołania do tablicy jest wskaźnik do tablicy. W poniższym przykładzie zmienia się na zawartość `values` tablicy, które zostały wprowadzone w `DoubleValues` metody jest możliwość obserwowania przez każdy kod, który zawiera odwołanie do tablicy.

[!code-csharp[csSnippets.Methods#101](../../samples/snippets/csharp/concepts/methods/returnarray1.cs#101)]

 <a name="extension"></a>
 ## <a name="extension-methods"></a>Metody rozszerzenia ##

Zazwyczaj istnieją dwa sposoby, aby dodać metodę do istniejącego typu:

- Zmodyfikuj kod źródłowy dla tego typu. Nie możesz tego zrobić, oczywiście, jeśli nie jesteś właścicielem kodu źródłowego typu. I to staje się istotnej zmiany po dodaniu pola danych prywatnych do obsługuje metody.
- Zdefiniuj nową metodę w klasie pochodnej. Nie można dodać metodę w ten sposób za pomocą dziedziczenia dla innych typów, takie jak struktury i wyliczeń. Nie może on służyć do "Dodaj" metodę do klasy zapieczętowanej.

Metody rozszerzenia umożliwiają "Dodawanie" metody do istniejącego typu bez modyfikowania samego typu lub wykonania nowej metody dziedziczonej typu. Metoda rozszerzenia również nie musi znajdować się w tym samym zestawie jako typ, który stanowi rozszerzenie. Wywoływanie metody rozszerzenia, tak jakby był on członkiem zdefiniowanego typu.

Aby uzyskać więcej informacji, zobacz [metody rozszerzenia](programming-guide/classes-and-structs/extension-methods.md).

<a name="async"></a>
## <a name="async-methods"></a>Metody asynchroniczne ##

Za pomocą funkcji asynchronicznych, można wywoływać metod asynchronicznych, bez za pomocą jawnego wywołania zwrotne lub ręcznego podziału kodu na wielu metod lub wyrażenia lambda.

Po oznaczeniu metody z [async](language-reference/keywords/async.md) modyfikator, można użyć [await](language-reference/keywords/await.md) operatora w metodzie. Gdy kontrola osiąga `await` wyrażenia w metodzie asynchronicznej, sterowanie powraca do obiektu wywołującego, jeśli oczekiwane zadanie nie zostało ukończone i postęp w danej metody `await` — słowo kluczowe jest wstrzymana, dopóki nie zakończy się oczekiwane zadanie. Kiedy zadanie zostanie ukończone, wykonanie można wznowić w metodzie.

> [!NOTE]
> Metoda asynchroniczna zwraca do obiektu wywołującego, po napotkaniu pierwszego oczekiwane obiekt, który nie został jeszcze ukończony lub otrzymuje na końcu metody asynchronicznej, zależnie co nastąpi wcześniej.

Metoda asynchroniczna może mieć typ zwracany <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>, lub `void`. `void` Typ zwracany jest używany głównie do definiowania programów obsługi zdarzeń, gdzie `void` jest wymagany typ zwracany. Metoda asynchroniczna, która zwraca `void` nie może być oczekiwany, a obiekt wywołujący metodę zwracającą typ void nie może przechwytywać wyjątków, które metoda wygeneruje. Począwszy od języka C# 7.0, metoda asynchroniczna może mieć [dowolnego typu zwracanego zadania](./whats-new/csharp-7.md#generalized-async-return-types).

W poniższym przykładzie `DelayAsync` jest to metoda asynchroniczna, która zawiera instrukcję return, która zwraca liczbę całkowitą. Ponieważ jest to metoda asynchroniczna, jego deklaracja metody musi mieć typ zwracany `Task<int>`. Ponieważ typem zwracanym jest `Task<int>`, oceny `await` wyrażenia w `DoSomethingAsync` tworzy liczbą całkowitą, zgodnie z poniższymi `int result = await delayTask` pokazuje instrukcji.

[!code-csharp[csSnippets.Methods#102](../../samples/snippets/csharp/concepts/methods/async1.cs#102)]

Metoda async nie może deklarować [w](language-reference/keywords/in-parameter-modifier.md), [ref](language-reference/keywords/ref.md), lub [się](language-reference/keywords/out-parameter-modifier.md) parametry, ale może wywoływać metody, które mają takie parametry.

 Aby uzyskać więcej informacji na temat metod asynchronicznych, zobacz [Asynchronous Programming with Async and Await](async.md), [Control Flow in Async Programs](programming-guide/concepts/async/control-flow-in-async-programs.md), i [Async Return Types](programming-guide/concepts/async/async-return-types.md).

<a name="expr"></a>
## <a name="expression-bodied-members"></a>Elementy członkowskie z wyrażeniem ##

Jest to często mają definicje metody, która po prostu zwrócenia natychmiast z wynikiem wyrażenia lub pojedynczą instrukcję jako treść metody, które mają.  Ma składnię skrót do definiowania takich metod za pomocą `=>`:

```csharp
public Point Move(int dx, int dy) => new Point(x + dx, y + dy);
public void Print() => Console.WriteLine(First + " " + Last);
// Works with operators, properties, and indexers too.
public static Complex operator +(Complex a, Complex b) => a.Add(b);
public string Name => First + " " + Last;
public Customer this[long id] => store.LookupCustomer(id);
```

Jeśli metoda zwraca `void` lub jest to metoda asynchroniczna treści metody musi być wyrażeniem — instrukcja (tak samo jak w przypadku wyrażenia lambda).  Właściwości i indeksatorów, muszą być w trybie tylko do odczytu i nie należy używać `get` akcesor — słowo kluczowe.

<a name="iterators"></a>
## <a name="iterators"></a>Iteratory ##

Iterator wykonuje niestandardowych iteracji w kolekcji, takie jak listy lub tablicy. Używa iteratora [yield return](language-reference/keywords/yield.md) instrukcja zwraca każdy element w danym momencie. Gdy `yield return` osiągnięciu instrukcji bieżącą lokalizację zapamiętywane jest tak, aby obiekt wywołujący może żądać następnego elementu w sekwencji.

Zwracany typ iteratora, może być <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, lub <xref:System.Collections.Generic.IEnumerator%601>.

Aby uzyskać więcej informacji, zobacz [Iteratory](programming-guide/concepts/iterators.md).

## <a name="see-also"></a>Zobacz także ##

- [Modyfikatory dostępu](language-reference/keywords/access-modifiers.md)   
- [Klasy statyczne i statyczne elementy członkowskie klas](programming-guide/classes-and-structs/static-classes-and-static-class-members.md)   
- [Dziedziczenie](programming-guide/classes-and-structs/inheritance.md)   
- [Klasy abstrakcyjne i zapieczętowane oraz elementy członkowskie klas](programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)   
- [params](language-reference/keywords/params.md)   
- [out](language-reference/keywords/out-parameter-modifier.md)   
- [ref](language-reference/keywords/ref.md)   
- [in](language-reference/keywords/in-parameter-modifier.md)   
- [Przekazywanie parametrów](programming-guide/classes-and-structs/passing-parameters.md)

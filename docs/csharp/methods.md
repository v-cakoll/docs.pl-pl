---
title: Metody — przewodnik po języku C#
description: Omówienie metod, parametrów metody i wartości zwracanych metody
ms.technology: csharp-fundamentals
ms.date: 05/21/2018
ms.assetid: 577a8527-1081-4b36-9b9e-0685b6553c6e
ms.openlocfilehash: f44c83408e884d76eef5e2b5abbca511fbae2a1f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399449"
---
# <a name="methods"></a>Metody

Metoda jest blok iem kodu, który zawiera serię instrukcji. Program powoduje, że instrukcje mają być wykonywane przez wywołanie metody i określenie wszelkich wymaganych argumentów metody. W języku C#, każda wykonywana instrukcja jest wykonywana w kontekście metody. Metoda `Main` jest punktem wejścia dla każdej aplikacji Języka C# i jest wywoływana przez program runtime języka wspólnego (CLR) po uruchomieniu programu.

> [!NOTE]
> W tym temacie omówiono nazwane metody. Aby uzyskać informacje o funkcjach anonimowych, zobacz [Funkcje anonimowe](programming-guide/statements-expressions-operators/anonymous-functions.md).

<a name="signatures"></a>

## <a name="method-signatures"></a>Podpisy metody

Metody są deklarowane `class` `struct` w lub przez określenie:

- Opcjonalny poziom dostępu, `public` `private`taki jak lub . Wartość domyślna to `private`.
- Opcjonalne modyfikatory, takie jak `abstract` lub `sealed`.
- Wartość zwracana `void` lub jeśli metoda nie ma żadnego.
- Nazwa metody.
- Dowolne parametry metody. Parametry metody są ujęte w nawiasy i są oddzielone przecinkami. Puste nawiasy wskazują, że metoda nie wymaga żadnych parametrów.

Te części razem tworzą podpis metody.

> [!NOTE]
> Zwracany typ metody nie jest częścią podpisu metody na potrzeby przeciążenia metody. Jednak jest częścią podpisu metody przy określaniu zgodności między delegata i metody, która wskazuje.

Poniższy przykład definiuje klasę `Motorcycle` o nazwie, która zawiera pięć metod:

[!code-csharp[csSnippets.Methods#40](../../samples/snippets/csharp/concepts/methods/methods40.cs#40)]

Należy zauważyć, że `Motorcycle` klasa zawiera `Drive`metodę przeciążoną. Dwie metody mają taką samą nazwę, ale muszą być zróżnicowane według ich typów parametrów.

<a name="invocation"></a>

## <a name="method-invocation"></a>Wywołanie metody

Metody mogą być *wystąpienia* lub *statyczne*. Wywoływanie metody wystąpienia wymaga utworzenia obiektu i wywołania metody na tym obiekcie; metoda wystąpienia działa na tym wystąpieniu i jego danych. Wywołanie metody statycznej, odwołując się do nazwy typu, do którego należy metoda; metody statyczne nie działają na danych wystąpienia. Próba wywołania metody statycznej za pośrednictwem wystąpienia obiektu generuje błąd kompilatora.

Wywołanie metody jest jak dostęp do pola. Po nazwie obiektu (jeśli jest wywoływanie metody wystąpienia) lub nazwa `static` typu (jeśli jesteś wywoływanie metody), dodać kropkę, nazwę metody i nawiasy. Argumenty są wyświetlane w nawiasach i są oddzielone przecinkami.

Definicja metody określa nazwy i typy wszystkich parametrów, które są wymagane. Gdy obiekt wywołujący wywołuje metodę, zawiera konkretne wartości, nazywane argumentami, dla każdego parametru. Argumenty muszą być zgodne z typem parametru, ale nazwa argumentu, jeśli jest używana w kodzie wywołującym, nie musi być taka sama jak parametr o nazwie zdefiniowanej w metodzie. W poniższym `Square` przykładzie metoda zawiera pojedynczy `int` parametr o nazwie *i*. Pierwsze wywołanie metody `Square` przekazuje metodę `int` zmiennej o nazwie *num;* drugi, stała liczbowa; i trzecie, wyrażenie.

[!code-csharp[csSnippets.Methods#74](../../samples/snippets/csharp/concepts/methods/params74.cs#74)]

Najbardziej rozpowszechnioną formą wywołania metody używane argumenty pozycyjne; dostarcza argumenty w tej samej kolejności co parametry metody. Metody `Motorcycle` klasy można zatem wywołać, jak w poniższym przykładzie. Wywołanie `Drive` metody, na przykład, zawiera dwa argumenty, które odpowiadają dwa parametry w składni metody. Pierwszy staje się wartością `miles` parametru, drugi wartość `speed` parametru.

[!code-csharp[csSnippets.Methods#41](../../samples/snippets/csharp/concepts/methods/methods40.cs#41)]

Można również użyć *nazwanych argumentów* zamiast argumentów pozycyjnych podczas wywoływania metody. Korzystając z nazwanych argumentów, należy określić nazwę parametru, po której następuje dwukropek (":") i argument. Argumenty metody mogą pojawiać się w dowolnej kolejności, o ile są obecne wszystkie wymagane argumenty. W poniższym przykładzie użyto `TestMotorcycle.Drive` nazwanych argumentów do wywołania metody. W tym przykładzie nazwane argumenty są przekazywane w odwrotną kolejności z listy parametrów metody.

[!code-csharp[csSnippets.Methods#45](../../samples/snippets/csharp/concepts/methods/named1.cs#45)]

Metodę można wywołać przy użyciu zarówno argumentów pozycyjnych, jak i nazwanych argumentów. Jednak argument pozycyjny nie może być zgodny z nazwanym argumentem. Poniższy przykład wywołuje `TestMotorcycle.Drive` metodę z poprzedniego przykładu przy użyciu jednego argumentu pozycyjnego i jednego o nazwie argumentu.

[!code-csharp[csSnippets.Methods#46](../../samples/snippets/csharp/concepts/methods/named2.cs#46)]

<a name="inherited"></a>

## <a name="inherited-and-overridden-methods"></a>Metody dziedziczone i zastępowane

Oprócz elementów członkowskich, które są jawnie zdefiniowane w typie, typ dziedziczy elementy członkowskie zdefiniowane w jego klas podstawowych. Ponieważ wszystkie typy w systemie typu zarządzanego <xref:System.Object> dziedziczą bezpośrednio lub pośrednio <xref:System.Object.Equals(System.Object)> <xref:System.Object.GetType>z <xref:System.Object.ToString>klasy, wszystkie typy dziedziczą jego elementy członkowskie, takie jak , , i . Poniższy przykład definiuje `Person` klasę, tworzy wystąpienia `Person` dwóch obiektów i `Person.Equals` wywołuje metodę, aby ustalić, czy dwa obiekty są równe. Metoda, `Equals` jednak nie jest zdefiniowana w `Person` klasie; jest dziedziczona z <xref:System.Object>.

[!code-csharp[csSnippets.Methods#104](../../samples/snippets/csharp/concepts/methods/inherited1.cs#104)]

Typy można zastąpić dziedziczone elementy `override` członkowskie przy użyciu słowa kluczowego i zapewnienie implementacji dla metody zastąpione. Podpis metody musi być taki sam jak podpis metody zastąpionej. Poniższy przykład jest podobny do poprzedniego, z <xref:System.Object.Equals(System.Object)> tą różnicą, że zastępuje metodę. (Zastępuje również <xref:System.Object.GetHashCode> metodę, ponieważ obie metody mają na celu zapewnienie spójnych wyników.)

[!code-csharp[csSnippets.Methods#105](../../samples/snippets/csharp/concepts/methods/overridden1.cs#105)]

<a name="passing"></a>

## <a name="passing-parameters"></a>Przekazywanie parametrów

Typy w języku C# są *typami wartości* lub *typami odwołań.* Aby uzyskać listę wbudowanych typów wartości, zobacz [Typy i zmienne](./tour-of-csharp/types-and-variables.md). Domyślnie zarówno typy wartości, jak i typy odwołań są przekazywane do metody przez wartość.

<a name="byval"></a>

### <a name="passing-parameters-by-value"></a>Przekazywanie parametrów według wartości

Gdy typ wartości jest przekazywany do metody przez wartość, kopia obiektu zamiast samego obiektu jest przekazywana do metody. W związku z tym zmiany w obiekcie w wywoływana metoda nie mają wpływu na oryginalny obiekt, gdy formant powraca do obiektu wywołującego.

Poniższy przykład przekazuje typ wartości do metody przez wartość, a wywoływana metoda próbuje zmienić wartość typu wartości. Definiuje zmienną typu `int`, która jest typem wartości, inicjuje jej wartość do 20 i przekazuje ją do metody o nazwie, `ModifyValue` która zmienia wartość zmiennej na 30. Gdy jednak metoda zwraca, wartość zmiennej pozostaje niezmieniona.

[!code-csharp[csSnippets.Methods#10](../../samples/snippets/csharp/concepts/methods/byvalue10.cs#10)]

Gdy obiekt typu odwołania jest przekazywany do metody przez wartość, odwołanie do obiektu jest przekazywana przez wartość. Oznacza to, że metoda odbiera nie sam obiekt, ale argument, który wskazuje lokalizację obiektu. Jeśli zmienisz element członkowski obiektu przy użyciu tego odwołania, zmiana jest odzwierciedlana w obiekcie, gdy formant powraca do metody wywołującej. Jednak zastąpienie obiektu przekazywane do metody nie ma wpływu na oryginalny obiekt, gdy formant powraca do obiektu wywołującego.

Poniższy przykład definiuje klasę (która jest typem `SampleRefType`odwołania) o nazwie . Tworzy obiekt, `SampleRefType` przypisuje 44 do jego `value` pola i przekazuje obiekt `ModifyObject` do metody. W tym przykładzie zasadniczo to samo, co w poprzednim przykładzie - przekazuje argument przez wartość do metody. Ale ponieważ typ odwołania jest używany, wynik jest inny. Modyfikacja, która `ModifyObject` jest `obj.value` wprowadzana w `value` polu zmienia `rt`również pole `Main` argumentu, w metodzie na 33, jak pokazuje dane wyjściowe z przykładu.

[!code-csharp[csSnippets.Methods#42](../../samples/snippets/csharp/concepts/methods/byvalue42.cs#42)]

<a name="byref"></a>

### <a name="passing-parameters-by-reference"></a>Przekazywanie parametrów przez odniesienie

Należy przekazać parametr przez odwołanie, gdy chcesz zmienić wartość argumentu w metodzie i chcesz odzwierciedlić tę zmianę, gdy formant powraca do metody wywołującej. Aby przekazać parametr przez odwołanie, należy użyć słowa kluczowego [`ref`](language-reference/keywords/ref.md) lub. [`out`](language-reference/keywords/out-parameter-modifier.md) Można również przekazać wartość przez odwołanie, aby uniknąć kopiowania, ale nadal uniemożliwiać modyfikacje przy użyciu słowa kluczowego. [`in`](language-reference/keywords/in-parameter-modifier.md)

Poniższy przykład jest identyczny z poprzednim, z wyjątkiem wartości `ModifyValue` jest przekazywana przez odwołanie do metody. Gdy wartość parametru jest modyfikowany w `ModifyValue` metodzie, zmiana wartości jest odzwierciedlana po powrocie kontroli do obiektu wywołującego.

[!code-csharp[csSnippets.Methods#106](../../samples/snippets/csharp/concepts/methods/byref106.cs#106)]

Wspólny wzorzec, który używa przez parametry ref polega na zamianie wartości zmiennych. Przekazujesz dwie zmienne do metody przez odwołanie, a metoda zamienia ich zawartość. Poniższy przykład zamienia wartości całkowite.

[!code-csharp[csSnippets.Methods#106](../../samples/snippets/csharp/concepts/methods/swap107.cs#107)]

Przekazywanie parametru typu odwołania umożliwia zmianę wartości samego odwołania, a nie wartość jego poszczególnych elementów lub pól.

<a name="paramarray"></a>

### <a name="parameter-arrays"></a>Tablice parametrów

Czasami wymóg, aby określić dokładną liczbę argumentów do metody jest restrykcyjne. Za pomocą `params` słowa kluczowego, aby wskazać, że parametr jest tablicą parametrów, należy zezwolić na wywołanie metody ze zmienną liczbą argumentów. Parametr oznaczony `params` słowem kluczowym musi być typem tablicy i musi być ostatnim parametrem na liście parametrów metody.

Obiekt wywołujący można następnie wywołać metodę na jeden z trzech sposobów:

- Przekazując tablicy odpowiedniego typu, który zawiera żądaną liczbę elementów.
- Przekazując listę poszczególnych argumentów poszczególnych argumentów odpowiedniego typu do metody.
- Nie podając argument do tablicy parametrów.

W poniższym przykładzie zdefiniowano metodę o nazwie, `GetVowels` która zwraca wszystkie samogłoski z tablicy parametrów. Metoda `Main` ilustruje wszystkie trzy sposoby wywoływania metody. Obiekty wywołujące nie są wymagane do podania żadnych `params` argumentów dla parametrów, które zawierają modyfikator. W takim przypadku parametr `null`jest .

[!code-csharp[csSnippets.Methods#75](~/samples/snippets/csharp/concepts/methods/params75.cs#75)]

<a name="optional"></a>

## <a name="optional-parameters-and-arguments"></a>Opcjonalne parametry i argumenty

Definicja metody można określić, że jego parametry są wymagane lub że są one opcjonalne. Domyślnie wymagane są parametry. Parametry opcjonalne są określone przez włączenie wartości domyślnej parametru do definicji metody. Gdy metoda jest wywoływana, jeśli nie podano żadnego argumentu dla parametru opcjonalnego, zamiast tego używana jest wartość domyślna.

Wartość domyślna parametru musi być przypisana przez jeden z następujących rodzajów wyrażeń:

- Stała, na przykład ciąg literał lub liczba.
- Wyrażenie formularza `new ValType()`, gdzie `ValType` jest typem wartości. Należy zauważyć, że wywołuje typ wartości niejawnego konstruktora bezparametrowego, który nie jest rzeczywistym członkiem tego typu.
- Wyrażenie formularza `default(ValType)`, gdzie `ValType` jest typem wartości.

Jeśli metoda zawiera zarówno parametry wymagane, jak i opcjonalne, parametry opcjonalne są definiowane na końcu listy parametrów, po wszystkich wymaganych parametrach.

Poniższy przykład definiuje metodę, `ExampleMethod`która ma jeden wymagany i dwa parametry opcjonalne.

[!code-csharp[csSnippets.Methods#21](../../samples/snippets/csharp/concepts/methods/optional1.cs#21)]

Jeśli metoda z wieloma argumentami opcjonalnymi jest wywoływana przy użyciu argumentów pozycyjnych, obiekt wywołujący musi podać argument dla wszystkich parametrów opcjonalnych od pierwszego do ostatniego, dla którego podano argument. W przypadku `ExampleMethod` metody, na przykład, jeśli obiekt wywołujący `description` dostarcza argument dla parametru, musi również podać jeden dla parametru. `optionalInt` `opt.ExampleMethod(2, 2, "Addition of 2 and 2");`jest prawidłowym wywołaniem metody; `opt.ExampleMethod(2, , "Addition of 2 and 0");` generuje błąd kompilatora "Brak argumentu".

Jeśli metoda jest wywoływana przy użyciu nazwanych argumentów lub kombinacji argumentów pozycyjnych i nazwanych, obiekt wywołujący może pominąć wszystkie argumenty, które następują po ostatnim argumencie pozycyjnym w wywołaniu metody.

Poniższy przykład wywołuje `ExampleMethod` metodę trzy razy.  Pierwsze dwie metody wywołania użyć argumentów pozycyjnych. Pierwszy pomija oba argumenty opcjonalne, podczas gdy drugi pomija ostatni argument. Trzecia metoda wywołania dostarcza argument pozycyjny dla wymaganego parametru, ale używa `description` nazwie argument do `optionalInt` podania wartości do parametru, pomijając argument.

[!code-csharp[csSnippets.Methods#22](../../samples/snippets/csharp/concepts/methods/optional1.cs#22)]

Użycie parametrów opcjonalnych wpływa na *rozpoznawanie przeciążenia*lub sposób, w jaki kompilator C# określa, które szczególne przeciążenie powinno być wywoływane przez wywołanie metody, w następujący sposób:

- Metoda, indeksator lub konstruktor jest kandydatem do wykonania, jeśli każdy z jego parametrów jest opcjonalny lub odpowiada, według nazwy lub pozycji, pojedynczemu argumentowi w instrukcji wywołującej, a ten argument można przekonwertować na typ parametru.
- Jeśli zostanie znaleziony więcej niż jeden kandydat, reguły rozpoznawania przeciążenia dla preferowanych konwersji są stosowane do argumentów, które są jawnie określone. Pominięte argumenty dla parametrów opcjonalnych są ignorowane.
- Jeśli dwóch kandydatów zostanie ocenionych jako równie dobre, preferencja trafia do kandydata, który nie ma opcjonalnych parametrów, dla których argumenty zostały pominięte w zaproszeniu. Jest to konsekwencją ogólnej preferencji w rozpoznawaniu przeciążenia dla kandydatów, którzy mają mniej parametrów.

<a name="return"></a>

## <a name="return-values"></a>Zwracane wartości

Metody mogą zwracać wartość do obiektu wywołującego. Jeśli typ zwracany (typ wymieniony przed nazwą `void`metody) nie jest , metoda `return` może zwrócić wartość przy użyciu słowa kluczowego. Instrukcja ze `return` słowem kluczowym, po której następuje zmienna, stała lub wyrażenie, które pasuje do typu zwracanego, zwróci tę wartość do obiektu wywołującego metodę. Metody z typem zwracanym bez void są `return` wymagane do użycia słowa kluczowego w celu zwrócenia wartości. Słowo `return` kluczowe zatrzymuje również wykonywanie metody.

Jeśli zwracany `void`jest `return` typ , instrukcja bez wartości jest nadal przydatne, aby zatrzymać wykonanie metody. Bez `return` słowa kluczowego metoda przestanie wykonywać, gdy osiągnie koniec bloku kodu.

Na przykład te dwie metody `return` używają słowa kluczowego do zwracania liczb całkowitych:

[!code-csharp[csSnippets.Methods#44](../../samples/snippets/csharp/concepts/methods/return44.cs#44)]

Aby użyć wartości zwracanej z metody, metoda wywołująca może użyć samego wywołania metody w dowolnym miejscu, w których wystarczająca byłaby wartość tego samego typu. Można również przypisać wartość zwracaną do zmiennej. Na przykład następujące dwa przykłady kodu osiągnąć ten sam cel:

[!code-csharp[csSnippets.Methods#45](../../samples/snippets/csharp/concepts/methods/return44.cs#45)]

[!code-csharp[csSnippets.Methods#46](../../samples/snippets/csharp/concepts/methods/return44.cs#46)]

Użycie zmiennej lokalnej, w `result`tym przypadku , do przechowywania wartości jest opcjonalne. Może to pomóc czytelność kodu lub może być konieczne, jeśli trzeba przechowywać oryginalną wartość argumentu dla całego zakresu metody.

Czasami chcesz, aby metoda zwracała więcej niż jedną wartość. Począwszy od języka C# 7.0, można to zrobić łatwo przy użyciu *typów krotki* i *literały krotki*. Typ krotki definiuje typy danych elementów krotki. Literały krotki zapewniają rzeczywiste wartości zwróconej krotki. W poniższym `(string, string, string, int)` przykładzie definiuje typ krotki, który `GetPersonalInfo` jest zwracany przez metodę. Wyrażenie `(per.FirstName, per.MiddleName, per.LastName, per.Age)` jest literału krotki; metoda zwraca pierwsze, środkowe i nazwisko, wraz z wiekiem `PersonInfo` obiektu.

```csharp
public (string, string, string, int) GetPersonalInfo(string id)
{
    PersonInfo per = PersonInfo.RetrieveInfoById(id);
    return (per.FirstName, per.MiddleName, per.LastName, per.Age);
}
```

Obiekt wywołujący może następnie korzystać z zwróconej krotki z kodem, takim jak następujące:

```csharp
var person = GetPersonalInfo("111111111")
Console.WriteLine("{person.Item1} {person.Item3}: age = {person.Item4}");
```

Nazwy można również przypisać do elementów krotki w definicji typu krotki. W poniższym przykładzie przedstawiono `GetPersonalInfo` alternatywną wersję metody, która używa nazwanych elementów:

```csharp
public (string FName, string MName, string LName, int Age) GetPersonalInfo(string id)
{
    PersonInfo per = PersonInfo.RetrieveInfoById(id);
    return (per.FirstName, per.MiddleName, per.LastName, per.Age);
}
```

Poprzednie wywołanie `GetPersonInfo` metody można następnie zmodyfikować w następujący sposób:

```csharp
var person = GetPersonalInfo("111111111");
Console.WriteLine("{person.FName} {person.LName}: age = {person.Age}");
```

Jeśli metoda jest przekazywana tablicy jako argument i modyfikuje wartość poszczególnych elementów, nie jest konieczne dla metody, aby zwrócić tablicy, chociaż można to zrobić dla dobrego stylu lub funkcjonalnego przepływu wartości.  Jest tak, ponieważ C# przekazuje wszystkie typy odwołań przez wartość, a wartość odwołania tablicy jest wskaźnikiem do tablicy. W poniższym przykładzie zmiany zawartości `values` tablicy, które są `DoubleValues` wprowadzane w metodzie są obserwowalne przez dowolny kod, który ma odwołanie do tablicy.

[!code-csharp[csSnippets.Methods#101](../../samples/snippets/csharp/concepts/methods/returnarray1.cs#101)]

<a name="extension"></a>

## <a name="extension-methods"></a>Metody rozszerzenia

Zwykle istnieją dwa sposoby dodawania metody do istniejącego typu:

- Zmodyfikuj kod źródłowy dla tego typu. Oczywiście nie można tego zrobić, jeśli nie jesteś właścicielem kodu źródłowego typu. A to staje się przełomową zmianą, jeśli dodasz również wszelkie prywatne pola danych do obsługi metody.
- Zdefiniuj nową metodę w klasie pochodnej. Metody nie można dodać w ten sposób przy użyciu dziedziczenia dla innych typów, takich jak struktury i wyliczenia. Nie można go również używać do "dodawania" metody do zapieczętowanej klasy.

Metody rozszerzenia umożliwiają "dodawanie" metody do istniejącego typu bez modyfikowania samego typu lub implementowania nowej metody w typie dziedziczonym. Metoda rozszerzenia również nie musi przebywać w tym samym zestawie, co typ, który rozszerza. Metoda rozszerzenia jest tak, jakby była zdefiniowanym elementem członkowskim typu.

Aby uzyskać więcej informacji, zobacz [Metody rozszerzenia](programming-guide/classes-and-structs/extension-methods.md).

<a name="async"></a>

## <a name="async-methods"></a>Metody asynchroniczne

Za pomocą funkcji asynchronicznej można wywołać metody asynchroniczne bez użycia jawnych wywołań wywołania wstecznego lub ręcznie podziału kodu na wiele metod lub wyrażeń lambda.

Jeśli oznaczysz metodę modyfikatorem [asynchroni,](language-reference/keywords/async.md) możesz użyć [operatora await](language-reference/operators/await.md) w metodzie. Gdy formant osiągnie `await` wyrażenie w metodzie asynchronicznej, formant zwraca do obiektu wywołującego, jeśli oczekiwane `await` zadanie nie zostanie ukończone, a postęp w metodzie ze słowem kluczowym jest zawieszony, dopóki oczekiwane zadanie nie zostanie zakończone. Po zakończeniu zadania wykonanie można wznowić w metodzie.

> [!NOTE]
> Metoda asynchroniczna zwraca do obiektu wywołującego, gdy napotka pierwszy oczekiwany obiekt, który nie został jeszcze ukończony lub zostanie do końca metody asynchronicznej, w zależności od tego, co nastąpi wcześniej.

Metoda asynchroniczna może <xref:System.Threading.Tasks.Task%601>mieć <xref:System.Threading.Tasks.Task>typ `void`zwracany , lub . Typ `void` zwracany jest używany głównie do definiowania programów obsługi zdarzeń, gdzie wymagany jest typ zwracany. `void` Metody asynchronicznej, która zwraca `void` nie można oczekiwać, a obiekt wywołujący metody zwracającej nieważność nie może przechwycić wyjątków, które zgłasza metoda. Począwszy od języka C# 7.0, metoda asynchroniczna może mieć [dowolny typ zwracania podobny do zadania](./whats-new/csharp-7.md#generalized-async-return-types).

W poniższym `DelayAsync` przykładzie jest metodą asynchronia, która ma return instrukcji, która zwraca liczby całkowitej. Ponieważ jest to metoda asynchroniczna, jego `Task<int>`deklaracja metody musi mieć typ zwracany . Ponieważ typ zwracany `Task<int>`jest , `await` ocena `DoSomethingAsync` wyrażenia w produkuje liczbę całkowitą, jak pokazano w poniższej `int result = await delayTask` instrukcji.

[!code-csharp[csSnippets.Methods#102](../../samples/snippets/csharp/concepts/methods/async1.cs#102)]

Metoda asynchroniczna nie może zadeklarować żadnych parametrów [in](language-reference/keywords/in-parameter-modifier.md), [ref](language-reference/keywords/ref.md)lub [out,](language-reference/keywords/out-parameter-modifier.md) ale może wywoływać metody, które mają takie parametry.

 Aby uzyskać więcej informacji na temat metod asynchronicznych, zobacz [Programowanie asynchroniczne z asynchroniczną i await,](async.md) [przepływ sterowania w programach asynchronicznych](programming-guide/concepts/async/control-flow-in-async-programs.md)i [Async Return Types](programming-guide/concepts/async/async-return-types.md).

<a name="expr"></a>

## <a name="expression-bodied-members"></a>Składowe z wyrażeniem w treści

Często mają definicje metody, które po prostu zwracają natychmiast z wynikiem wyrażenia lub które mają jedną instrukcję jako treść metody.  Istnieje skrót składni owy do definiowania takich metod przy użyciu: `=>`

```csharp
public Point Move(int dx, int dy) => new Point(x + dx, y + dy);
public void Print() => Console.WriteLine(First + " " + Last);
// Works with operators, properties, and indexers too.
public static Complex operator +(Complex a, Complex b) => a.Add(b);
public string Name => First + " " + Last;
public Customer this[long id] => store.LookupCustomer(id);
```

Jeśli metoda `void` zwraca lub jest metodą asynchronia, treść metody musi być wyrażeniem instrukcji (tak samo jak w przypadku lambdas).  Dla właściwości i indeksatorów muszą być tylko do odczytu `get` i nie należy używać słowa kluczowego akcesor.

<a name="iterators"></a>

## <a name="iterators"></a>Iteratory

Iterator wykonuje iterację niestandardową nad kolekcją, taką jak lista lub tablica. Iterator używa [yield return](language-reference/keywords/yield.md) instrukcji do zwrócenia każdego elementu po jednym na raz. Po `yield return` osiągnięciu instrukcji bieżąca lokalizacja jest zapamiętywana, dzięki czemu obiekt wywołujący może zażądać następnego elementu w sekwencji.

Zwracany typ iterator może <xref:System.Collections.IEnumerable> <xref:System.Collections.Generic.IEnumerable%601>być <xref:System.Collections.IEnumerator>, <xref:System.Collections.Generic.IEnumerator%601>, , lub .

Aby uzyskać więcej informacji, zobacz [Iterytory](programming-guide/concepts/iterators.md).

## <a name="see-also"></a>Zobacz też

- [Modyfikatory dostępu](language-reference/keywords/access-modifiers.md)
- [Klasy statyczne i statyczni członkowie klas](programming-guide/classes-and-structs/static-classes-and-static-class-members.md)
- [Dziedziczenie](programming-guide/classes-and-structs/inheritance.md)
- [Klasy abstrakcyjne i zapieczętowane oraz członkowie klas](programming-guide/classes-and-structs/abstract-and-sealed-classes-and-class-members.md)
- [params](language-reference/keywords/params.md)
- [na zewnątrz](language-reference/keywords/out-parameter-modifier.md)
- [ref](language-reference/keywords/ref.md)
- [Cala](language-reference/keywords/in-parameter-modifier.md)
- [Przekazywanie parametrów](programming-guide/classes-and-structs/passing-parameters.md)

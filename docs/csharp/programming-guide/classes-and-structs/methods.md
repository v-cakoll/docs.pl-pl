---
title: Metody — przewodnik programowania Języka C#
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#]
- C# language, methods
ms.assetid: cc738f07-e8cd-4683-9585-9f40c0667c37
ms.openlocfilehash: 114fa2973c50be9a4199db9729e3cd9ea6122866
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77626532"
---
# <a name="methods-c-programming-guide"></a>Metody (Przewodnik programowania w języku C#)

Metoda jest blok iem kodu, który zawiera serię instrukcji. Program powoduje, że instrukcje mają być wykonywane przez wywołanie metody i określenie wszelkich wymaganych argumentów metody. W języku C#, każda wykonywana instrukcja jest wykonywana w kontekście metody. Metoda `Main` jest punktem wejścia dla każdej aplikacji Języka C# i jest wywoływana przez program runtime języka wspólnego (CLR) po uruchomieniu programu.

> [!NOTE]
> W tym artykule omówiono nazwane metody. Aby uzyskać informacje o funkcjach anonimowych, zobacz [Funkcje anonimowe](../statements-expressions-operators/anonymous-functions.md).

## <a name="method-signatures"></a>Podpisy metody

Metody są deklarowane w [klasie,](../../language-reference/keywords/class.md) [strukturze](../../language-reference/builtin-types/struct.md)lub [interfejsie,](../interfaces/index.md) `public` określając `private`poziom dostępu, taki `abstract` `sealed`jak lub , opcjonalne modyfikatory, takie jak lub , wartość zwracana, nazwa metody i wszelkie parametry metody. Te części razem są podpisem metody.

> [!NOTE]
> Zwracany typ metody nie jest częścią podpisu metody na potrzeby przeciążenia metody. Jednak jest częścią podpisu metody przy określaniu zgodności między delegata i metody, która wskazuje.

Parametry metody są ujęte w nawiasy i są oddzielone przecinkami. Puste nawiasy wskazują, że metoda nie wymaga żadnych parametrów. Ta klasa zawiera cztery metody:

[!code-csharp[csProgGuideObjects#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#40)]

## <a name="method-access"></a>Dostęp do metody

Wywołanie metody na obiekcie jest jak dostęp do pola. Po nazwie obiektu dodaj kropkę, nazwę metody i nawiasy. Argumenty są wyświetlane w nawiasach i są oddzielone przecinkami. Metody `Motorcycle` klasy można zatem wywołać tak, jak w poniższym przykładzie:

[!code-csharp[csProgGuideObjects#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#41)]

## <a name="method-parameters-vs-arguments"></a>Parametry metody a argumenty

Definicja metody określa nazwy i typy wszystkich parametrów, które są wymagane. Podczas wywoływania kodu wywołuje metodę, zawiera konkretne wartości nazywane argumentami dla każdego parametru. Argumenty muszą być zgodne z typem parametru, ale nazwa argumentu (jeśli istnieje) używana w kodzie wywołującym nie musi być taka sama jak parametr o nazwie zdefiniowanej w metodzie. Przykład:

[!code-csharp[csProgGuideObjects#74](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#74)]

## <a name="passing-by-reference-vs-passing-by-value"></a>Przekazywanie przez odwołanie a przekazywanie przez wartość

Domyślnie po przekazaniu wystąpienia [typu wartości](../../language-reference/builtin-types/value-types.md) do metody jej kopia jest przekazywana zamiast samego wystąpienia. W związku z tym zmiany argumentu nie mają wpływu na oryginalne wystąpienie w metodzie wywołującej. Aby przekazać wystąpienie typu wartości przez `ref` odwołanie, użyj słowa kluczowego. Aby uzyskać więcej informacji, zobacz [Przekazywanie parametrów typu wartości](./passing-value-type-parameters.md).

Gdy obiekt typu odwołania jest przekazywany do metody, odwołanie do obiektu jest przekazywana. Oznacza to, że metoda odbiera nie sam obiekt, ale argument, który wskazuje lokalizację obiektu. Jeśli zmienisz element członkowski obiektu przy użyciu tego odwołania, zmiana zostanie odzwierciedlona w argumencie w metodzie wywołującej, nawet jeśli przekażesz obiekt przez wartość.

Typ odwołania można utworzyć `class` przy użyciu słowa kluczowego, jak pokazano w poniższym przykładzie:

[!code-csharp[csProgGuideObjects#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#42)]

Teraz, jeśli przekażesz obiekt, który jest oparty na tym typie do metody, odwołanie do obiektu jest przekazywana. Poniższy przykład przekazuje obiekt `SampleRefType` typu `ModifyObject`do metody:

[!code-csharp[csProgGuideObjects#75](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#75)]

Przykład ma zasadniczo to samo, co w poprzednim przykładzie, ponieważ przekazuje argument przez wartość do metody. Ale ponieważ typ odwołania jest używany, wynik jest inny. Modyfikacja, która `ModifyObject` jest `value` wprowadzana w `obj`polu parametru, zmienia `value` również `rt`pole `TestRefType` argumentu, , w metodzie. Metoda `TestRefType` wyświetla 33 jako dane wyjściowe.

Aby uzyskać więcej informacji na temat przekazywania typów odwołań przez odwołanie i według wartości, zobacz [Przekazywanie parametrów typu odwołania](./passing-reference-type-parameters.md) i typy [odwołań](../../language-reference/keywords/reference-types.md).

## <a name="return-values"></a>Zwracane wartości

Metody mogą zwracać wartość do obiektu wywołującego. Jeśli typ zwracany, typ wymieniony przed nazwą `void`metody, nie jest , metoda `return` może zwrócić wartość przy użyciu słowa kluczowego. Instrukcja ze `return` słowem kluczowym, po której następuje wartość, która pasuje do typu zwracanego, zwróci tę wartość do obiektu wywołującego metodę.

Wartość może być zwracana do obiektu wywołującego według wartości lub, począwszy od Języka C# 7.0, [przez odwołanie](ref-returns.md). Wartości są zwracane do obiektu `ref` wywołującego przez odwołanie, jeśli słowo `return` kluczowe jest używane w podpisie metody i następuje każde słowo kluczowe. Na przykład następujący podpis metody i return instrukcji wskazują, `estDistance` że metoda zwraca nazwy zmiennych przez odwołanie do obiektu wywołującego.

```csharp
public ref double GetEstimatedDistance()
{
    return ref estDistance;
}
```

Słowo `return` kluczowe zatrzymuje również wykonywanie metody. Jeśli zwracany `void`jest `return` typ , instrukcja bez wartości jest nadal przydatne, aby zatrzymać wykonanie metody. Bez `return` słowa kluczowego metoda przestanie wykonywać, gdy osiągnie koniec bloku kodu. Metody z typem zwracanym bez void są `return` wymagane do użycia słowa kluczowego w celu zwrócenia wartości. Na przykład te dwie metody `return` używają słowa kluczowego do zwracania liczb całkowitych:

[!code-csharp[csProgGuideObjects#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#44)]

Aby użyć wartości zwracanej z metody, metoda wywołująca może użyć samego wywołania metody w dowolnym miejscu, w których wystarczająca byłaby wartość tego samego typu. Można również przypisać wartość zwracaną do zmiennej. Na przykład następujące dwa przykłady kodu osiągnąć ten sam cel:

[!code-csharp[csProgGuideObjects#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#45)]

[!code-csharp[csProgGuideObjects#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#46)]

Użycie zmiennej lokalnej, w `result`tym przypadku , do przechowywania wartości jest opcjonalne. Może to pomóc czytelność kodu lub może być konieczne, jeśli trzeba przechowywać oryginalną wartość argumentu dla całego zakresu metody.

Aby użyć wartości zwracanej przez odwołanie z metody, należy zadeklarować zmienną [lokalną ref,](ref-returns.md#ref-locals) jeśli zamierzasz zmodyfikować jej wartość. Na przykład jeśli `Planet.GetEstimatedDistance` metoda <xref:System.Double> zwraca wartość przez odwołanie, można zdefiniować ją jako zmienną lokalną ref z kodem, takim jak następujące:

```csharp
ref int distance = plant
```

Zwracanie tablicy wielowymiarowej z `M`metody, która modyfikuje zawartość tablicy nie jest konieczne, `M`jeśli funkcja wywołująca przekazała tablicę do .  Wynikową tablicę można `M` zwrócić z dla dobrego stylu lub funkcjonalnego przepływu wartości, ale nie jest to konieczne, ponieważ C# przekazuje wszystkie typy odwołań według wartości, a wartość odwołania do tablicy jest wskaźnikiem do tablicy. W metodzie `M`wszelkie zmiany zawartości tablicy są widoczne przez dowolny kod, który ma odwołanie do tablicy, jak pokazano w poniższym przykładzie:

```csharp
static void Main(string[] args)
{
    int[,] matrix = new int[2, 2];
    FillMatrix(matrix);
    // matrix is now full of -1
}

public static void FillMatrix(int[,] matrix)
{
    for (int i = 0; i < matrix.GetLength(0); i++)
    {
        for (int j = 0; j < matrix.GetLength(1); j++)
        {
            matrix[i, j] = -1;
        }
    }
}
```

Aby uzyskać więcej informacji, zobacz [temat Return](../../language-reference/keywords/return.md).

## <a name="async-methods"></a>Metody asynchroniczne

Za pomocą funkcji asynchronicznej można wywołać metody asynchroniczne bez użycia jawnych wywołań wywołania wstecznego lub ręcznie podziału kodu na wiele metod lub wyrażeń lambda.

Jeśli oznaczysz metodę modyfikatorem [asynchroni,](../../language-reference/keywords/async.md) możesz użyć [operatora await](../../language-reference/operators/await.md) w metodzie. Gdy formant osiągnie await wyrażenie w metodzie asynchronicznej, formant zwraca do obiektu wywołującego, a postęp w metodzie jest zawieszone, dopóki nie zostanie ukończone oczekiwane zadanie. Po zakończeniu zadania wykonanie można wznowić w metodzie.

> [!NOTE]
> Metoda asynchroniczna zwraca do obiektu wywołującego, gdy napotka pierwszy oczekiwany obiekt, który nie został jeszcze ukończony lub zostanie do końca metody asynchronicznej, w zależności od tego, co nastąpi wcześniej.

Metoda asynchroniczna może <xref:System.Threading.Tasks.Task%601>mieć <xref:System.Threading.Tasks.Task>typ zwracany , lub void. Typ zwracania void jest używany głównie do definiowania programów obsługi zdarzeń, gdzie wymagany jest typ zwracany void. Nie można oczekiwać metody asynchronicznej, która zwraca void, a obiekt wywołujący metodę zwracania unieważnienia nie może przechwycić wyjątków, które zgłasza metoda.

W poniższym `DelayAsync` przykładzie jest metodą asynchronia, <xref:System.Threading.Tasks.Task%601>która ma typ zwracany . `DelayAsync`ma `return` instrukcję, która zwraca liczbę całkowitą. W związku z `DelayAsync` tym deklaracja `Task<int>`metody musi mieć typ zwracany . Ponieważ typ zwracany `Task<int>`jest , `await` ocena `DoSomethingAsync` wyrażenia w produkuje liczbę całkowitą, `int result = await delayTask`jak pokazano następującą instrukcję: .

Metoda `startButton_Click` jest przykładem metody asynchronicznej, która ma zwracany typ void. Ponieważ `DoSomethingAsync` jest metodą asynchroniczną, `DoSomethingAsync` zadanie dla wywołania musi być `await DoSomethingAsync();`oczekiwane, jak pokazano w następującej instrukcji: . Metoda `startButton_Click` musi być zdefiniowana za pomocą modyfikatora, `async` ponieważ metoda ma wyrażenie. `await`

[!code-csharp[csAsyncMethod#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csasyncmethod/cs/mainwindow.xaml.cs#2)]

Metoda asynchroniczna nie może zadeklarować żadnych [parametrów ref](../../language-reference/keywords/ref.md) lub [out,](../../language-reference/keywords/out-parameter-modifier.md) ale może wywoływać metody, które mają takie parametry.

Aby uzyskać więcej informacji na temat metod asynchronicznych, zobacz [Programowanie asynchroniczne z asynchroniczną i oczekujące](../concepts/async/index.md), [Przepływ sterowania w programach asynchronicznych](../concepts/async/control-flow-in-async-programs.md)i [Async Return Types](../concepts/async/async-return-types.md).

## <a name="expression-body-definitions"></a>Definicje treści wyrażeń

Często mają definicje metody, które po prostu zwracają natychmiast z wynikiem wyrażenia lub które mają jedną instrukcję jako treść metody. Istnieje skrót składni owy do definiowania takich metod przy użyciu: `=>`

```csharp
public Point Move(int dx, int dy) => new Point(x + dx, y + dy);
public void Print() => Console.WriteLine(First + " " + Last);
// Works with operators, properties, and indexers too.
public static Complex operator +(Complex a, Complex b) => a.Add(b);
public string Name => First + " " + Last;
public Customer this[long id] => store.LookupCustomer(id);
```

Jeśli metoda `void` zwraca lub jest metodą asynchronia, a następnie treść metody musi być wyrażenie instrukcji (tak samo jak w przypadku lambdas). Dla właściwości i indeksatorów muszą być tylko do odczytu `get` i nie używasz słowa kluczowego akcesor.

## <a name="iterators"></a>Iteratory

Iterator wykonuje iterację niestandardową nad kolekcją, taką jak lista lub tablica. Iterator używa [yield return](../../language-reference/keywords/yield.md) instrukcji do zwrócenia każdego elementu po jednym na raz. Po osiągnięciu [yield return](../../language-reference/keywords/yield.md) instrukcji, bieżąca lokalizacja w kodzie jest zapamiętywany. Wykonanie jest uruchamiane ponownie z tej lokalizacji, gdy sterująca jest wywoływana następnym razem.

Wywołanie iterator z kodu klienta przy użyciu [foreach](../../language-reference/keywords/foreach-in.md) instrukcji.

Zwracany typ iterator może <xref:System.Collections.IEnumerable> <xref:System.Collections.Generic.IEnumerable%601>być <xref:System.Collections.IEnumerator>, <xref:System.Collections.Generic.IEnumerator%601>, , lub .

Aby uzyskać więcej informacji, zobacz [Iterytory](../concepts/iterators.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Klasy i struktury](index.md)
- [Modyfikatory dostępu](access-modifiers.md)
- [Klasy statyczne i statyczni członkowie klas](static-classes-and-static-class-members.md)
- [Dziedziczenie](inheritance.md)
- [Klasy abstrakcyjne i zapieczętowane oraz członkowie klas](abstract-and-sealed-classes-and-class-members.md)
- [params](../../language-reference/keywords/params.md)
- [return](../../language-reference/keywords/return.md)
- [na zewnątrz](../../language-reference/keywords/out.md)
- [ref](../../language-reference/keywords/ref.md)
- [Przekazywanie parametrów](passing-parameters.md)

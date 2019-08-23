---
title: Metody — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#]
- C# language, methods
ms.assetid: cc738f07-e8cd-4683-9585-9f40c0667c37
ms.openlocfilehash: 6e7a1dfc739278eecfa8582bb0a9f8938c561acf
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69924458"
---
# <a name="methods-c-programming-guide"></a>Metody (Przewodnik programowania w języku C#)
Metoda jest blokiem kodu, który zawiera serie instrukcji. Program powoduje wykonanie instrukcji przez wywołanie metody i określenie wszelkich wymaganych argumentów metody. W C#programie Każda wykonana instrukcja jest wykonywana w kontekście metody. Metoda Main jest punktem wejścia dla każdej C# aplikacji i jest wywoływana przez środowisko uruchomieniowe języka wspólnego (CLR), gdy program jest uruchomiony.  
  
> [!NOTE]
> W tym temacie omówiono nazwane metody. Aby uzyskać informacje na temat funkcji anonimowych, zobacz [funkcje anonimowe](../statements-expressions-operators/anonymous-functions.md).  
  
## <a name="method-signatures"></a>Sygnatury metod  
 Metody są zadeklarowane w [klasie](../../language-reference/keywords/class.md) lub [strukturze](../../language-reference/keywords/struct.md) przez określenie poziomu dostępu, takiego jak `public` lub `private`, Modyfikatory opcjonalne, takie `abstract` jak `sealed`lub, wartość zwracana, nazwa metody i wszystkie parametry metody . Te części razem są sygnaturą metody.  
  
> [!NOTE]
> Zwracany typ metody nie jest częścią podpisu metody do celów przeciążania metody. Jednakże jest częścią podpisu metody podczas określania zgodności między delegatem a metodą, do której wskazuje.  
  
 Parametry metody są ujęte w nawiasy i są rozdzielone przecinkami. Puste nawiasy wskazują, że metoda nie wymaga żadnych parametrów. Ta klasa zawiera cztery metody:  
  
 [!code-csharp[csProgGuideObjects#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#40)]  
  
## <a name="method-access"></a>Dostęp do metody  
 Wywołanie metody na obiekcie jest podobne do uzyskiwania dostępu do pola. Po nazwie obiektu Dodaj kropkę, nazwę metody i nawiasów. Argumenty są wyświetlane w nawiasach i są oddzielone przecinkami. Metody `Motorcycle` klasy mogą więc być wywoływane jak w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideObjects#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#41)]  
  
## <a name="method-parameters-vs-arguments"></a>Parametry metody a Argumenty  
 Definicja metody Określa nazwy i typy wymaganych parametrów. Gdy Wywoływanie kodu wywołuje metodę, dostarcza konkretnych wartości nazywanych argumentami dla każdego parametru. Argumenty muszą być zgodne z typem parametru, ale nazwa argumentu (jeśli istnieje) użyta w wywoływanym kodzie nie musi być taka sama jak parametr o nazwie zdefiniowanej w metodzie. Na przykład:  
  
 [!code-csharp[csProgGuideObjects#74](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#74)]  
  
## <a name="passing-by-reference-vs-passing-by-value"></a>Przekazywanie przez odwołanie a Przekazywanie przez wartość  
 Domyślnie, gdy typ wartości jest przenoszona do metody, jest przenoszona kopia zamiast samego obiektu. W związku z tym zmiany argumentu nie mają wpływu na oryginalną kopię w wywołaniu metody. Można przekazać typ wartości przez odwołanie za pomocą słowa kluczowego ref. Aby uzyskać więcej informacji, zobacz [przekazywanie parametrów typu wartości](./passing-value-type-parameters.md). Aby zapoznać się z listą wbudowanych typów wartości, zobacz [tabela typy wartości](../../language-reference/keywords/value-types-table.md).  
  
 Gdy obiekt typu referencyjnego jest przenoszona do metody, odwołanie do obiektu jest przesyłane. Oznacza to, że metoda nie odbiera samego obiektu, ale argument, który wskazuje lokalizację obiektu. Jeśli zmienisz element członkowski obiektu za pomocą tego odwołania, zmiana zostanie odzwierciedlona w argumencie metody wywołującej, nawet jeśli przekażesz obiekt przez wartość.  
  
 Typ referencyjny można utworzyć za pomocą `class` słowa kluczowego, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[csProgGuideObjects#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#42)]  
  
 Teraz, Jeśli przekażesz obiekt, który jest oparty na tym typie metody, odwołanie do obiektu zostanie przekazane. Poniższy przykład przekazuje obiekt typu `SampleRefType` do metody. `ModifyObject`  
  
 [!code-csharp[csProgGuideObjects#75](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#75)]  
  
 Przykład zasadniczo działa tak samo jak w poprzednim przykładzie, że przekazuje argument przez wartość do metody. Jednak, ponieważ jest używany typ referencyjny, wynik jest różny. `ModifyObject` Modyfikacja wprowadzona w `value` polu parametru `obj` `rt` `TestRefType` ,, również zmiana polaargumentu,,wmetodzie.`value` `TestRefType` Metoda wyświetla 33 jako dane wyjściowe.  
  
 Aby uzyskać więcej informacji na temat przekazywania typów odwołań przez odwołanie i wartość, zobacz [przekazywanie parametrów typu odwołania](./passing-reference-type-parameters.md) i [typy odwołań](../../language-reference/keywords/reference-types.md).  
  
## <a name="return-values"></a>Wartości zwrócone  
Metody mogą zwracać wartość do obiektu wywołującego. Jeśli zwracany typ, typ wymieniony przed nazwą metody nie `void`jest, Metoda może zwrócić wartość przy `return` użyciu słowa kluczowego. Instrukcja ze `return` słowem kluczowym, po której następuje wartość zgodna z typem zwracanym, zwróci tę wartość do obiektu wywołującego metody. 

Wartość można zwrócić do elementu wywołującego przez wartość lub, zaczynając od C# 7,0, [według odwołania](ref-returns.md). Wartości są zwracane do obiektu wywołującego przez odwołanie, `ref` Jeśli słowo kluczowe jest używane w podpisie metody i następuje `return` po każdym słowie kluczowym. Na przykład następująca sygnatura metody i instrukcja return wskazują, że metoda zwraca nazwy `estDistance` zmiennych przez odwołanie do obiektu wywołującego.

```csharp
public ref double GetEstimatedDistance()
{
   return ref estDistance;
}
```

`return` Słowo kluczowe również przerywa wykonywanie metody. Jeśli zwracanym typem jest `void` `return` , instrukcja bez wartości jest nadal przydatna do zatrzymania wykonywania metody. `return` Bez słowa kluczowego, Metoda zostanie zatrzymana po osiągnięciu końca bloku kodu. Metody z typem zwracanym innym niż void są wymagane do zwrócenia wartości `return` za pomocą słowa kluczowego. Na przykład te dwie metody używają `return` słowa kluczowego do zwracania liczb całkowitych:  
  
 [!code-csharp[csProgGuideObjects#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#44)]  
  
 Aby użyć wartości zwracanej z metody, Metoda wywołująca może użyć wywołania metody, wszędzie tam, gdzie wartość tego samego typu byłaby wystarczająca. Możesz również przypisać wartość zwracaną do zmiennej. Na przykład następujące dwa przykłady kodu mają ten sam cel:  
  
 [!code-csharp[csProgGuideObjects#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#45)]  
  
 [!code-csharp[csProgGuideObjects#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#46)]  
  
 Użycie zmiennej lokalnej, w tym przypadku `result`, do przechowywania wartości jest opcjonalne. Może to pomóc w czytelności kodu lub może być konieczne, jeśli konieczne będzie przechowywanie pierwotnej wartości argumentu dla całego zakresu metody.  

Aby użyć wartości zwracanej przez odwołanie z metody, należy zadeklarować zmienną [lokalną ref](ref-returns.md#ref-locals) , jeśli zamierzasz zmodyfikować jej wartość. Na przykład, jeśli `Planet.GetEstimatedDistance` Metoda <xref:System.Double> zwraca wartość przez odwołanie, można ją zdefiniować jako zmienną lokalną ref z kodem podobnym do poniższego:

```csharp
ref int distance = plant 
```

Zwracanie wielowymiarowej tablicy z metody, `M`która modyfikuje zawartość tablicy, nie jest konieczna, jeśli wywoływana funkcja przekazała tablicę do. `M`  Można zwrócić wynikową tablicę z `M` dla dobrego stylu lub przepływu funkcjonalnego wartości, ale nie jest to konieczne, C# ponieważ przekazuje wszystkie typy odwołań według wartości, a wartość odwołania tablicy jest wskaźnikiem do tablicy. W metodzie `M`wszelkie zmiany zawartości tablicy są zauważalne przez dowolny kod, który ma odwołanie do tablicy, jak pokazano w poniższym przykładzie.  
  
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
  
 Aby uzyskać więcej informacji, zobacz [Return](../../language-reference/keywords/return.md).  
  
## <a name="async-methods"></a>Metody asynchroniczne  
 Za pomocą funkcji asynchronicznej można wywołać metody asynchroniczne bez używania jawnych wywołań zwrotnych lub ręcznie podzielić kod na wiele metod lub wyrażenia lambda. 
  
 Jeśli oznaczesz metodę za pomocą modyfikatora [asynchronicznego](../../language-reference/keywords/async.md) , możesz użyć operatora [await](../../language-reference/keywords/await.md) w metodzie. Gdy kontrolka osiągnie wyrażenie await w metodzie asynchronicznej, sterowanie powraca do obiektu wywołującego, a postęp w metodzie jest zawieszony do momentu zakończenia zadania oczekiwania. Po zakończeniu zadania wykonywanie może zostać wznowione w metodzie.  
  
> [!NOTE]
> Metoda asynchroniczna wraca do obiektu wywołującego, gdy napotka on pierwszy oczekujący obiekt, który nie został jeszcze ukończony lub otrzymuje koniec metody asynchronicznej, zależnie od tego, co się dzieje.  
  
 Metoda asynchroniczna może mieć zwracany typ <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>lub void. Typ zwracany void jest używany głównie do definiowania programów obsługi zdarzeń, gdzie wymagany jest zwracany typ void. Metoda asynchroniczna zwracająca typ void nie może być oczekiwana, a obiekt wywołujący metodę void nie może przechwytywać wyjątków, które metoda zgłasza.  
  
 W poniższym przykładzie `DelayAsync` jest metoda async, która ma zwracany <xref:System.Threading.Tasks.Task%601>typ. `DelayAsync``return` zawiera instrukcję zwracającą liczbę całkowitą. W związku z tym deklaracja `DelayAsync` metody musi mieć `Task<int>`typ zwracany. Ponieważ typem zwracanym jest `Task<int>`, obliczanie `await` wyrażenia w `DoSomethingAsync` tworzy liczbę całkowitą, jak pokazano w poniższej instrukcji: `int result = await delayTask`.  
  
 `startButton_Click` Metoda jest przykładem metody asynchronicznej, która ma zwracany typ void. Ponieważ `DoSomethingAsync` jest to Metoda asynchroniczna, zadanie dla `DoSomethingAsync` wywołania musi być oczekiwane, jak pokazano w poniższej instrukcji: `await DoSomethingAsync();`. Metoda musi być zdefiniowana `async` z modyfikatorem, `await` ponieważ metoda ma wyrażenie. `startButton_Click`  
  
 [!code-csharp[csAsyncMethod#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csasyncmethod/cs/mainwindow.xaml.cs#2)]  
  
 Metoda async nie może deklarować parametrów [ref](../../language-reference/keywords/ref.md) ani [out](../../language-reference/keywords/out-parameter-modifier.md) , ale może wywoływać metody, które mają takie parametry.  
  
 Aby uzyskać więcej informacji na temat metod asynchronicznych, zobacz [programowanie asynchroniczne z asynchroniczne i oczekujące](../concepts/async/index.md), [przepływ sterowania w programach asynchronicznych](../concepts/async/control-flow-in-async-programs.md)i [asynchroniczne typy zwracane](../concepts/async/async-return-types.md).  
  
## <a name="expression-body-definitions"></a>Definicje treści wyrażenia  
 Często istnieją definicje metod, które po prostu zwracają bezpośrednio z wynikiem wyrażenia lub które mają pojedynczą instrukcję jako treść metody.  Istnieje skrót do definiowania takich metod przy użyciu `=>`:  
  
```csharp  
public Point Move(int dx, int dy) => new Point(x + dx, y + dy);   
public void Print() => Console.WriteLine(First + " " + Last);  
// Works with operators, properties, and indexers too.  
public static Complex operator +(Complex a, Complex b) => a.Add(b);  
public string Name => First + " " + Last;   
public Customer this[long id] => store.LookupCustomer(id);  
```  
  
 Jeśli metoda zwraca `void` lub jest metodą asynchroniczną, treść metody musi być wyrażeniem instrukcji (analogicznie jak w przypadku wyrażeń lambda).  W przypadku właściwości i indeksatorów muszą one być tylko do odczytu i nie można używać `get` słowa kluczowego metody dostępu.  
  
## <a name="iterators"></a>Iteratory  
 Iterator wykonuje niestandardową iterację w kolekcji, na przykład listę lub tablicę. Iterator używa instrukcji [yield return](../../language-reference/keywords/yield.md) , aby zwrócić każdy element po jednym naraz. Po osiągnięciu instrukcji [yield return](../../language-reference/keywords/yield.md) bieżąca lokalizacja w kodzie jest zapamiętywana. Wykonanie jest uruchamiane ponownie z tej lokalizacji, kiedy iterator jest wywoływana następnym razem.  
  
 Należy wywołać iterator z kodu klienta przy użyciu instrukcji [foreach](../../language-reference/keywords/foreach-in.md) .  
  
 Zwracany typ iteratora <xref:System.Collections.IEnumerable>może mieć wartość, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, lub <xref:System.Collections.Generic.IEnumerator%601>.  
  
 Aby uzyskać więcej informacji, [](../concepts/iterators.md)zobacz Iteratory.  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Klasy i struktury](index.md)
- [Modyfikatory dostępu](access-modifiers.md)
- [Klasy statyczne i statyczne elementy członkowskie klas](static-classes-and-static-class-members.md)
- [Dziedziczenie](inheritance.md)
- [Klasy abstrakcyjne i zapieczętowane oraz elementy członkowskie klas](abstract-and-sealed-classes-and-class-members.md)
- [params](../../language-reference/keywords/params.md)
- [return](../../language-reference/keywords/return.md)
- [out](../../language-reference/keywords/out.md)
- [ref](../../language-reference/keywords/ref.md)
- [Przekazywanie parametrów](passing-parameters.md)

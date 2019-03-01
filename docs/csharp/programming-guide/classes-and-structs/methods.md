---
title: Metody - C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- methods [C#]
- C# language, methods
ms.assetid: cc738f07-e8cd-4683-9585-9f40c0667c37
ms.openlocfilehash: f6e85a4dfdf562c0a479b19224e11e919da8716d
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56980363"
---
# <a name="methods-c-programming-guide"></a>Metody (Przewodnik programowania w języku C#)
Metoda jest blokiem kodu, który zawiera szereg instrukcji. Program powoduje, że instrukcji do wykonania przez wywołanie metody i określenie argumentów wymaganej metody. W języku C# co instrukcja wykonanych odbywa się w kontekście metody. Metoda główna jest punktem wejścia dla każdej aplikacji C# i jest wywoływana przez środowisko uruchomieniowe języka wspólnego (CLR), gdy program zostanie uruchomiony.  
  
> [!NOTE]
>  W tym temacie omówiono metody o nazwie. Aby uzyskać informacje na temat funkcji anonimowych zobacz [funkcjami anonimowymi](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).  
  
## <a name="method-signatures"></a>Podpisy metod  
 Metody są deklarowane w [klasy](../../../csharp/language-reference/keywords/class.md) lub [struktury](../../../csharp/language-reference/keywords/struct.md) , określając poziom dostępu, takich jak `public` lub `private`, Modyfikatory opcjonalne, takie jak `abstract` lub `sealed`, zwracany wartość, Nazwa metody oraz wszelkie parametry metody. Te elementy są ze sobą podpis metody.  
  
> [!NOTE]
>  Zwracany typ metody nie jest część podpisu metody na potrzeby przeciążenie metody. Jednak jest część podpisu metody podczas określania zgodności między delegata i metody, która wskazuje.  
  
 Parametry metody są ujęte w nawiasy i są oddzielone przecinkami. Pustych nawiasów zwykłych wskazują, że metoda nie wymaga parametrów. Ta klasa zawiera cztery metody:  
  
 [!code-csharp[csProgGuideObjects#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#40)]  
  
## <a name="method-access"></a>Dostęp do metody  
 Wywołanie metody do obiektu jest jak uzyskiwanie dostępu do pola. Po nazwie obiektu Dodaj okres, nazwy metody i nawiasy. Argumenty są wyświetlane w nawiasach i są oddzielone przecinkami. Metody `Motorcycle` klasy, w związku z tym może być wywoływana tak jak w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideObjects#41](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#41)]  
  
## <a name="method-parameters-vs-arguments"></a>Parametry metody programu vs. Argumenty  
 Definicja metody określa nazwy i typy parametrów, które są wymagane. Podczas wywoływania kod wywołuje metody, zapewnia konkretnych wartości nazywanych argumentami dla każdego parametru. Argumenty muszą być zgodne z typem parametru, ale nazwa argumentu (jeśli istnieje) używane w wywoływanym kodzie nie musi być taka sama jak parametr o nazwie zdefiniowany w metodzie. Na przykład:  
  
 [!code-csharp[csProgGuideObjects#74](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_3.cs)]  
  
## <a name="passing-by-reference-vs-passing-by-value"></a>Przekazywanie poprzez odwołanie do programu vs. Przekazywanie poprzez wartość  
 Domyślnie gdy typ wartości jest przekazywany do metody, kopia jest przekazywany zamiast samego obiektu. W związku z tym zmiany do argumentu nie mają wpływu na kopię oryginalnego w przypadku wywołania metody. Typ wartości przez odwołanie można przekazać za pomocą słowa kluczowego ref. Aby uzyskać więcej informacji, zobacz [przekazywanie parametrów typu wartość](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md). Aby uzyskać listę typów wbudowanych wartości, zobacz [Tabela typów wartości](../../../csharp/language-reference/keywords/value-types-table.md).  
  
 Jeśli obiekt typu referencyjnego jest przekazywany do metody, odwołanie do obiektu jest przekazywany. Oznacza to, że metoda odbiera nie samego obiektu, ale argument, który wskazuje lokalizację obiektu. Jeśli zmienisz członka obiektu za pomocą tego odwołania, zmiany są widoczne jako argument w przypadku wywołania metody, nawet wtedy, gdy obiekt jest przekazywane przez wartość.  
  
 Tworzenie typu odwołania za pomocą `class` — słowo kluczowe, co ilustruje poniższy przykład.  
  
 [!code-csharp[csProgGuideObjects#42](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#42)]  
  
 Teraz Jeśli przekażesz obiekt, który jest na podstawie tego typu do metody, odwołanie do obiektu jest przekazywany. Poniższy przykład przekazuje obiekt typu `SampleRefType` metody `ModifyObject`.  
  
 [!code-csharp[csProgGuideObjects#75](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#75)]  
  
 Przykład jest zasadniczo tak samo jak w poprzednim przykładzie, w tym przekazaniem argumentu przez wartość do metody. Jednak ponieważ używany jest typ odwołania, wynik jest inny. Ze zmianami, które znajduje się w `ModifyObject` do `value` pola parametru, `obj`, zmienia się również `value` pole argumentu, `rt`w `TestRefType` metody. `TestRefType` Metoda Wyświetla 33 jako dane wyjściowe.  
  
 Aby uzyskać więcej informacji dotyczących przekazywania typów referencyjnych przez odwołanie, a także według wartości, zobacz [przekazywanie parametrów typu odwołanie](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md) i [typów referencyjnych](../../../csharp/language-reference/keywords/reference-types.md).  
  
## <a name="return-values"></a>Wartości zwrócone  
Metody może zwrócić wartości do obiektu wywołującego. Jeśli zwracany typ, nie jest typu wymienionego przed nazwą metody `void`, metoda może zwrócić wartość przy użyciu `return` — słowo kluczowe. Instrukcja zawierająca `return` — słowo kluczowe, a następnie wartość, która jest zgodna z typem zwracanym zwróci tę wartość do obiektu wywołującego metodę. 

Wartość może zostać zwrócony do obiektu wywołującego przez wartość, lub, począwszy od C# 7.0, [przez odwołanie](ref-returns.md). Wartości są zwracane do obiektu wywołującego przez odwołanie, jeśli `ref` — słowo kluczowe jest używany w podpisie metody i jest zgodna z każdym `return` — słowo kluczowe. Na przykład następująca instrukcja podpis i zwracany metody wskazywać, że metoda zwraca nazwy zmiennych `estDistance` przez odwołanie do obiektu wywołującego.

```csharp
public ref double GetEstimatedDistance()
{
   return ref estDistance;
}
```

`return` — Słowo kluczowe również zatrzymuje wykonywanie metody. Jeśli typ zwracany jest `void`, `return` instrukcji bez wartości nadal jest użyteczne do zatrzymywania wykonywania metody. Bez `return` — słowo kluczowe, metoda wykonywanie zostanie przerwane po osiągnięciu końca bloku kodu. Metody z innym niż void zwrotu typu są wymagane do użycia `return` — słowo kluczowe w celu zwrócenia wartości. Na przykład użyć tych dwóch metod `return` — słowo kluczowe, aby zwrócić liczb całkowitych:  
  
 [!code-csharp[csProgGuideObjects#44](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#44)]  
  
 Aby użyć wartości zwrócone z metody, wywoływania metody użyć wywołania metody które się dowolnym wartością tego samego typu może być wystarczające. Można także przypisać zwracana wartość do zmiennej. Na przykład poniższe dwa przykłady kodu osiągnięcia tego samego celu:  
  
 [!code-csharp[csProgGuideObjects#45](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#45)]  
  
 [!code-csharp[csProgGuideObjects#46](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#46)]  
  
 Za pomocą zmiennej lokalnej, w tym przypadku `result`, aby przechowywać wartość jest opcjonalna. Może ułatwić czytelność kodu lub może być konieczne, jeśli chcesz przechować oryginalnej wartości argumentu dla całego zakresu metody.  

Aby użyć wartości zwracane przez odwołanie z metody, należy zadeklarować [odwołanie lokalne](ref-returns.md#ref-locals) zmiennej, jeśli zamierzasz modyfikować jego wartości. Na przykład jeśli `Planet.GetEstimatedDistance` metoda zwraca <xref:System.Double> wartość przez odwołanie, można zdefiniować ją jako zmienna lokalna ref z kodem, podobnie do poniższego:

```csharp
ref int distance = plant 
```

Zwracanie tablicy wielowymiarowej z metody, `M`, tablicy, który modyfikuje zawartość nie jest konieczne, jeśli funkcja wywołująca przekazana Tablica do `M`.  Może zwracać tablica wynikowa `M` dla dobra stylu lub funkcjonalności przepływu wartości, ale nie jest konieczne, ponieważ C# przekazuje wszystkich typów odniesienia według wartości, a wartość odwołania do tablicy jest wskaźnik do tablicy. W metodzie `M`, wszelkie zmiany zawartości tablicy jest możliwość obserwowania przez każdy kod, który zawiera odwołanie do tablicy, jak pokazano w poniższym przykładzie.  
  
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
  
 Aby uzyskać więcej informacji, zobacz [zwracają](../../../csharp/language-reference/keywords/return.md).  
  
## <a name="async-methods"></a>Metody asynchroniczne  
 Za pomocą funkcji asynchronicznych, można wywoływać metod asynchronicznych, bez za pomocą jawnego wywołania zwrotne lub ręcznego podziału kodu na wielu metod lub wyrażenia lambda. 
  
 Po oznaczeniu metody z [async](../../../csharp/language-reference/keywords/async.md) modyfikator, można użyć [await](../../../csharp/language-reference/keywords/await.md) operatora w metodzie. Gdy kontrola osiąga wyrażenie await w metodzie asynchronicznej, sterowanie powraca do obiektu wywołującego, a postęp w metodzie jest wstrzymana, dopóki nie zakończy się oczekiwane zadanie. Kiedy zadanie zostanie ukończone, wykonanie można wznowić w metodzie.  
  
> [!NOTE]
>  Metoda asynchroniczna zwraca do obiektu wywołującego, po napotkaniu pierwszego oczekiwane obiekt, który nie został jeszcze ukończony lub otrzymuje na końcu metody asynchronicznej, zależnie co nastąpi wcześniej.  
  
 Metoda asynchroniczna może mieć typ zwracany <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>, albo puste. Zwrócony typ void jest używany głównie do definiowania programów obsługi zdarzeń, gdzie zwracać typ void jest wymagany. Metoda asynchroniczna zwraca wartość void nie może być oczekiwany, a obiekt wywołujący metodę zwracającą typ void nie może przechwytywać wyjątków, które metoda wygeneruje.  
  
 W poniższym przykładzie `DelayAsync` jest to metoda asynchroniczna, która ma typ zwracany <xref:System.Threading.Tasks.Task%601>. `DelayAsync` ma `return` instrukcję, która zwraca liczbę całkowitą. Dlatego deklaracja metody z `DelayAsync` musi mieć typ zwracany `Task<int>`. Ponieważ typem zwracanym jest `Task<int>`, oceny `await` wyrażenia w `DoSomethingAsync` tworzy liczba całkowita, tak jak pokazano w następującej instrukcji: `int result = await delayTask`.  
  
 `startButton_Click` Metody jest przykładem metodzie asynchronicznej, która ma typ zwracany void. Ponieważ `DoSomethingAsync` to metoda asynchroniczna, zadanie do wywołań `DoSomethingAsync` musi być oczekiwana, co pokazuje poniższa instrukcja: `await DoSomethingAsync();`. `startButton_Click` Metoda musi być zdefiniowana za pomocą `async` modyfikator ponieważ metoda ma `await` wyrażenia.  
  
 [!code-csharp[csAsyncMethod#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csasyncmethod/cs/mainwindow.xaml.cs#2)]  
  
 Metoda async nie może deklarować [ref](../../../csharp/language-reference/keywords/ref.md) lub [się](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametry, ale może wywoływać metody, które mają takie parametry.  
  
 Aby uzyskać więcej informacji na temat metod asynchronicznych, zobacz [Asynchronous Programming with async i await](../../../csharp/programming-guide/concepts/async/index.md), [Control Flow in Async Programs](../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md), i [Async Return Types](../../../csharp/programming-guide/concepts/async/async-return-types.md).  
  
## <a name="expression-body-definitions"></a>Definicje treści wyrażenia  
 Jest to często mają definicje metody, która po prostu zwrócenia natychmiast z wynikiem wyrażenia lub pojedynczą instrukcję jako treść metody, które mają.  Ma składnię skrót do definiowania takich metod za pomocą `=>`:  
  
```csharp  
public Point Move(int dx, int dy) => new Point(x + dx, y + dy);   
public void Print() => Console.WriteLine(First + " " + Last);  
// Works with operators, properties, and indexers too.  
public static Complex operator +(Complex a, Complex b) => a.Add(b);  
public string Name => First + " " + Last;   
public Customer this[long id] => store.LookupCustomer(id);  
```  
  
 Jeśli metoda zwraca `void` lub to metoda asynchroniczna, a następnie treści metody musi być wyrażeniem — instrukcja (tak samo jak w przypadku wyrażenia lambda).  Dla właściwości i indeksatorów one muszą być tylko do odczytu i nie używaj `get` akcesor — słowo kluczowe.  
  
## <a name="iterators"></a>Iteratory  
 Iterator wykonuje niestandardowych iteracji w kolekcji, takie jak listy lub tablicy. Używa iteratora [yield return](../../../csharp/language-reference/keywords/yield.md) instrukcja zwraca każdy element w danym momencie. Gdy [yield return](../../../csharp/language-reference/keywords/yield.md) osiągnięciu instrukcji zapamiętanych bieżąca lokalizacja w kodzie. Wykonanie jest uruchamiane ponownie z tej lokalizacji, gdy iteratora jest wywoływana przy następnym.  
  
 Wywołujesz iterację z poziomu kodu klienta przy użyciu [foreach](../../../csharp/language-reference/keywords/foreach-in.md) instrukcji.  
  
 Zwracany typ iteratora, może być <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, lub <xref:System.Collections.Generic.IEnumerator%601>.  
  
 Aby uzyskać więcej informacji, zobacz [Iteratory](../../../csharp/programming-guide/concepts/iterators.md).  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Klasy i struktury](index.md)
- [Modyfikatory dostępu](access-modifiers.md)
- [Klasy statyczne i statyczne elementy członkowskie klas](static-classes-and-static-class-members.md)
- [Dziedziczenie](inheritance.md)
- [Klasy abstrakcyjne i zapieczętowane oraz elementy członkowskie klas](abstract-and-sealed-classes-and-class-members.md)
- [params](../../../csharp/language-reference/keywords/params.md)
- [return](../../../csharp/language-reference/keywords/return.md)
- [out](../../../csharp/language-reference/keywords/out.md)
- [ref](../../../csharp/language-reference/keywords/ref.md)
- [Przekazywanie parametrów](passing-parameters.md)

---
title: Metody (Przewodnik programowania w języku C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- methods [C#]
- C# language, methods
ms.assetid: cc738f07-e8cd-4683-9585-9f40c0667c37
caps.latest.revision: 41
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: dad1be88e39b708d34f454875e2cfb3ec100c430
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="methods-c-programming-guide"></a>Metody (Przewodnik programowania w języku C#)
Metoda jest blok kodu, który zawiera serię instrukcji. Program powoduje, że instrukcje, które ma być wykonane przez wywołanie metody i określanie żadnych argumentów wymaganej metody. W języku C# co wykonanie instrukcji jest wykonywane w kontekście metody. Metoda Main jest punkt wejścia dla każdej aplikacji C# i jest wywoływane przez środowisko uruchomieniowe języka wspólnego (CLR), gdy program jest uruchomiony.  
  
> [!NOTE]
>  W tym temacie omówiono nazwane metody. Aby uzyskać informacje na temat funkcji anonimowych, zobacz [funkcje anonimowe](../../../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md).  
  
## <a name="method-signatures"></a>Podpisy — metoda  
 Metody są zadeklarowane w [klasy](../../../csharp/language-reference/keywords/class.md) lub [struktury](../../../csharp/language-reference/keywords/struct.md) określając poziom dostępu, takich jak `public` lub `private`, Modyfikatory opcjonalne, takie jak `abstract` lub `sealed`, zwracany wartość, nazwę metody i wszelkie parametry metody. Części te są ze sobą podpis metody.  
  
> [!NOTE]
>  Typem zwracanym metody nie jest częścią podpis metody na potrzeby przeciążenie metody. Jednak jest częścią podpis metody podczas określania zgodności między delegata i wskazujący do metody.  
  
 Parametry metody są ujęte w nawiasy i są oddzielone przecinkami. Puste nawiasy wskazują, że metoda nie wymaga parametrów. Ta klasa zawiera trzy metody:  
  
 [!code-csharp[csProgGuideObjects#40](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_1.cs)]  
  
## <a name="method-access"></a>Metody dostępu  
 Wywoływanie metody do obiektu jest podobne do uzyskiwania dostępu do pola. Po nazwie obiektu dodać okres, nazwę metody i nawiasów. Argumenty są wyświetlane w nawiasach i są oddzielone przecinkami. Metody `Motorcycle` klasa może zostać wywołana w związku z tym jak w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideObjects#41](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_2.cs)]  
  
## <a name="method-parameters-vs-arguments"></a>Parametry metody vs. Argumenty  
 Definicja metody określa nazwy i typy parametrów, które są wymagane. Podczas wywoływania metody wywołań kodu, zapewnia konkretnych wartości o nazwie argumenty dla każdego parametru. Argumenty muszą być zgodne z typem parametru, ale nazwa argumentu (jeśli istnieją) używane w wywoływanym kodzie musi być taka sama jak parametr o nazwie w metodzie. Na przykład:  
  
 [!code-csharp[csProgGuideObjects#74](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_3.cs)]  
  
## <a name="passing-by-reference-vs-passing-by-value"></a>Przekazywanie poprzez odwołanie do wersji programu vs. Przekazywanie poprzez wartość  
 Domyślnie jeśli typ wartości jest przekazywany do metody, kopia jest przekazywany zamiast samego obiektu. W związku z tym zmiany do argumentu nie mają wpływu na oryginał wywołania metody. Można przekazać typu wartości przez odwołanie za pomocą ref — słowo kluczowe. Aby uzyskać więcej informacji, zobacz [przekazywanie parametrów typu wartość](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md). Listę typów wartości wbudowanych, zobacz [Tabela typów wartości](../../../csharp/language-reference/keywords/value-types-table.md).  
  
 Gdy obiekt typu referencyjnego jest przekazywany do metody, są przekazywane odwołania do obiektu. Oznacza to, że metoda odbiera, ale nie samego obiektu argument, który wskazuje lokalizację, do obiektu. Jeśli zmienisz element członkowski obiektu przy użyciu tego odwołania, zmiana ta jest uwzględniana w argumencie w przypadku wywołania metody nawet wtedy, gdy obiekt jest przekazanie przez wartość.  
  
 Utwórz typ referencyjny przy użyciu `class` — słowo kluczowe, jak przedstawiono na poniższym przykładzie.  
  
 [!code-csharp[csProgGuideObjects#42](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_4.cs)]  
  
 Teraz przekazując obiekt, który jest oparty na typie tej metody jest przekazywany odwołania do obiektu. Poniższy przykład przekazuje obiekt typu `SampleRefType` do metody `ModifyObject`.  
  
 [!code-csharp[csProgGuideObjects#75](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_5.cs)]  
  
 Przykład jest zasadniczo sam efekt co w poprzednim przykładzie, w tym przekazuje argumentu przez wartość do metody. Jednak ponieważ używany jest typ referencyjny, wynik jest inny. Ze zmianami, które jest przeprowadzane w `ModifyObject` do `value` pole parametru, `obj`, zmieniają się także `value` pole argumentu, `rt`w `TestRefType` metody. `TestRefType` Metoda Wyświetla 33 jako dane wyjściowe.  
  
 Aby uzyskać więcej informacji na temat przekazywania typów referencyjnych przez odwołanie, a wartość, zobacz [przekazywanie parametrów typu odwołanie](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md) i [typy referencyjne](../../../csharp/language-reference/keywords/reference-types.md).  
  
## <a name="return-values"></a>Wartości zwrócone  
Metody może zwracać wartości do obiektu wywołującego. Jeśli zwracany typ, typ wyświetlanych przed nazwę metody nie jest `void`, metoda może zwracać wartości przy użyciu `return` — słowo kluczowe. Instrukcja zawierająca `return` — słowo kluczowe, a następnie wartość, która jest zgodny z typem zwracanym zwraca tę wartość do wywołującego metody. 

Wartość może być zwracany do obiektu wywołującego przez wartość lub, począwszy od C# 7.0, [przez odwołanie](ref-returns.md). Wartości są zwracane do obiektu wywołującego przez odwołanie, jeśli `ref` — słowo kluczowe jest używane w podpisie metody i wynika z każdym `return` — słowo kluczowe. Na przykład następująca instrukcja podpisu i przywracać — metoda wskazywać, że ta metoda zwraca nazwy zmiennych `estDistance` przez odwołanie do obiektu wywołującego.

```csharp
public ref double GetEstimatedDistance()
{
   return ref estDistance;
}
```

`return` — Słowo kluczowe również zatrzymuje wykonywanie metody. Jeśli typem zwracanym jest `void`, `return` instrukcji bez wartości, warto nadal zatrzymuje wykonywanie metody. Bez `return` — słowo kluczowe, metoda spowoduje zatrzymanie wykonywania, gdy zostanie osiągnięty koniec bloku kodu. Metod innych niż void zwracany typ muszą korzystać z `return` — słowo kluczowe, aby zwrócić wartość. Na przykład użyć te dwie metody `return` — słowo kluczowe do zwrócenia liczb całkowitych:  
  
 [!code-csharp[csProgGuideObjects#44](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_6.cs)]  
  
 Aby użyć wartość zwracana z metody, metody wywołującej użyć wywołania metody sam gdziekolwiek się, że wartość tego samego typu będą wystarczające. Można także przypisać zwracana wartość do zmiennej. Na przykład następujący przykładowy kod dwóch realizację tego samego celu:  
  
 [!code-csharp[csProgGuideObjects#45](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_7.cs)]  
  
 [!code-csharp[csProgGuideObjects#46](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_8.cs)]  
  
 Przy użyciu zmiennej lokalnej, w tym przypadku `result`, aby przechowywać wartość jest opcjonalna. Może pomóc zwiększyć czytelność kodu, lub może być konieczne, jeśli zachodzi potrzeba przechowywania oryginalnej wartości argumentu dla całego zakresu metody.  

Aby użyć wartości zwracane przez odwołanie z metody, należy zadeklarować [lokalnej typu ref](ref-returns.md#ref-locals) zmiennej, jeśli zamierzasz zmodyfikować jego wartości. Na przykład jeśli `Planet.GetEstimatedDistance` metoda zwraca <xref:System.Double> wartość przez odwołanie, można zdefiniować ją jako zmienna lokalna ref z kodem podobnie do następującej:

```csharp
ref int distance = plant 
```

Zwracanie tablicy wielowymiarowej z metody, `M`, który modyfikuje tablicy zawartość nie jest konieczne, jeśli funkcji wywołującej przekazany do tablicy `M`.  Może zwracać tablicy wynikowej z `M` dla stylu dobrej lub funkcjonalności przepływu wartości, ale nie jest konieczne, ponieważ C# przekazuje wszystkie typy referencyjne przez wartość i wartość odwołania do tablicy jest wskaźnik do tablicy. W metodzie `M`, wszystkie zmiany do zawartości tablicy są według przez kodu, który zawiera odwołanie do tablicy, jak pokazano w poniższym przykładzie.  
  
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
  
 Aby uzyskać więcej informacji, zobacz [zwracać](../../../csharp/language-reference/keywords/return.md).  
  
## <a name="async-methods"></a>Metody asynchroniczne  
 Korzystając z funkcji asynchronicznych, można wywoływać metod asynchronicznych bez za pomocą jawnego wywołania zwrotne i ręcznie dzielenia kodu wielu metod lub wyrażenia lambda. 
  
 Po zaznaczeniu metodę o [async](../../../csharp/language-reference/keywords/async.md) modyfikator, można użyć [await](../../../csharp/language-reference/keywords/await.md) operatora w metodzie. Gdy formant osiągnie wyrażenie await w metodzie asynchronicznej, zwraca sterowania do obiektu wywołującego i postępu w metodzie jest wstrzymana, aż do zakończenia zadań oczekiwano. Po zakończeniu zadania wykonywania można wznowić w metodzie.  
  
> [!NOTE]
>  Metoda asynchroniczna zwraca do obiektu wywołującego po napotkaniu pierwszego oczekiwano obiekt, który nie został jeszcze ukończony lub pobiera na końcu metody asynchronicznej cokolwiek nastąpi najpierw.  
  
 Metoda asynchroniczna może mieć typ zwracany <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task>, ani void. Zwrócony typ void jest używany głównie w celu definiowania metod obsługi zdarzeń, którym wymagany jest zwrócony typ void. Metoda asynchroniczna zwracająca typ void nie może być oczekiwane, a obiekt wywołujący metody zwracające typ void nie może przechwytywać wyjątki, które metoda zgłasza.  
  
 W poniższym przykładzie `DelayAsync` jest to metoda asynchroniczna, który ma typ zwracany <xref:System.Threading.Tasks.Task%601>. `DelayAsync` ma `return` instrukcji, która zwraca liczbę całkowitą. W związku z tym metoda deklaracja `DelayAsync` musi mieć typ zwracany `Task<int>`. Ponieważ typ zwracany jest `Task<int>`, oceny `await` wyrażenie w `DoSomethingAsync` tworzy całkowitą, jak pokazano następująca instrukcja: `int result = await delayTask`.  
  
 `startButton_Click` Metoda jest przykładem to metoda asynchroniczna, który ma zwracany typ void. Ponieważ `DoSomethingAsync` jest to metoda asynchroniczna, zadania dla wywołania `DoSomethingAsync` musi być oczekiwane, jak przedstawiono na poniższym instrukcji: `await DoSomethingAsync();`. `startButton_Click` Metoda musi być zdefiniowana z `async` modyfikator ponieważ metoda ma `await` wyrażenia.  
  
 [!code-csharp[csAsyncMethod#2](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/methods_9.cs)]  
  
 Metoda asynchroniczna nie można zadeklarować żadnego [ref](../../../csharp/language-reference/keywords/ref.md) lub [limit](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametrów, ale można wywołać metody, które mają takie parametry.  
  
 Aby uzyskać więcej informacji na temat metod asynchronicznych, zobacz [programowanie asynchroniczne z async i await](../../../csharp/programming-guide/concepts/async/index.md), [przepływ sterowania w aplikacjach asynchronicznych](../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md), i [Async zwracać typów](../../../csharp/programming-guide/concepts/async/async-return-types.md).  
  
## <a name="expression-body-definitions"></a>Definicje treść wyrażenia  
 Jest często mają definicje — metoda, która po prostu zwrot wynik wyrażenia, lub które mają jednej instrukcji jako treść metody.  Brak skrót do definiowania tych metod, za pomocą składni `=>`:  
  
```csharp  
public Point Move(int dx, int dy) => new Point(x + dx, y + dy);   
public void Print() => Console.WriteLine(First + " " + Last);  
// Works with operators, properties, and indexers too.  
public static Complex operator +(Complex a, Complex b) => a.Add(b);  
public string Name => First + " " + Last;   
public Customer this[long id] => store.LookupCustomer(id);  
```  
  
 Jeśli metoda zwraca `void` lub jest to metoda asynchroniczna, a następnie treści metody musi być wyrażeniem instrukcji (tak samo jak w przypadku wyrażeń lambda).  Dla właściwości i indeksatorów one musi być tylko do odczytu i nie używaj `get` akcesor — słowo kluczowe.  
  
## <a name="iterators"></a>Iteratory  
 Iteratora wykonuje niestandardowych iteracji w kolekcji, takie jak listy lub tablicy. Używa iteratora [yield return](../../../csharp/language-reference/keywords/yield.md) instrukcji, aby zwracany był każdy element jednym naraz. Gdy [yield return](../../../csharp/language-reference/keywords/yield.md) osiągnięciu instrukcji zapamiętanych bieżącej lokalizacji w kodzie. Wykonanie zostanie ponownie z tej lokalizacji, gdy iteratora jest wywoływana przy następnym.  
  
 Wywołaj iteratora z kodu klienta za pomocą [foreach](../../../csharp/language-reference/keywords/foreach-in.md) instrukcji.  
  
 Może być zwracany typ iteratora <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, lub <xref:System.Collections.Generic.IEnumerator%601>.  
  
 Aby uzyskać więcej informacji, zobacz [Iteratory](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Klasy i struktury](index.md)  
 [Modyfikatory dostępu](access-modifiers.md)  
 [Klasy statyczne i statyczne elementy członkowskie klas](static-classes-and-static-class-members.md)  
 [Dziedziczenie](inheritance.md)  
 [Klasy abstrakcyjne i zapieczętowane oraz elementy członkowskie klas](abstract-and-sealed-classes-and-class-members.md)  
 [params](../../../csharp/language-reference/keywords/params.md)  
 [return](../../../csharp/language-reference/keywords/return.md)  
 [out](../../../csharp/language-reference/keywords/out.md)  
 [ref](../../../csharp/language-reference/keywords/ref.md)  
 [Przekazywanie parametrów](passing-parameters.md)

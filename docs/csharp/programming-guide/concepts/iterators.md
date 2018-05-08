---
title: Iteratory (C#)
ms.date: 07/20/2015
ms.assetid: c93f6dd4-e72a-4a06-be1c-a98b3255b734
ms.openlocfilehash: 08fe529f46ccaae7b2e17367a47346265aa0e8b6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="iterators-c"></a>Iteratory (C#)
*Iterator* może służyć do kroków opisanych w kolekcji, takie jak listy i stałych.  
  
 Metody iterator lub `get` akcesor wykonuje niestandardowych iteracji w kolekcji. Iterator — metoda korzysta z [yield return](../../../csharp/language-reference/keywords/yield.md) instrukcji, aby zwracany był każdy element jednym naraz. Gdy `yield return` osiągnięciu instrukcji zapamiętanych bieżącej lokalizacji w kodzie. Wykonanie jest uruchamiany ponownie z tej lokalizacji w następnym razem, gdy zostanie wywołana funkcja iteratora.  
  
 Korzystać z iteratora z kodu klienta za pomocą [foreach](../../../csharp/language-reference/keywords/foreach-in.md) instrukcji lub za pomocą zapytania LINQ.  
  
 W poniższym przykładzie pierwszej iteracji `foreach` pętli powoduje wykonanie kontynuować w `SomeNumbers` metody iteracyjnej do pierwszego `yield return` osiągnięciu instrukcji. Tą iterację zwraca wartość 3 i są przechowywane w bieżącej lokalizacji w metodzie iteracyjnej. Przy następnej iteracji pętli, wykonywanie w metodzie iteracyjnej będzie kontynuowane z, w którym ją przerwał pracę, ponownie zatrzymywanie po osiągnięciu `yield return` instrukcji. Tą iterację zwraca wartość 5, a bieżącą lokalizację w metodzie iteracyjnej ponownie zostanie zachowane. Pętla działanie jest kończone po osiągnięciu na końcu metody iteracyjnej.  
  
```csharp  
static void Main()  
{  
    foreach (int number in SomeNumbers())  
    {  
        Console.Write(number.ToString() + " ");  
    }  
    // Output: 3 5 8  
    Console.ReadKey();  
}  
  
public static System.Collections.IEnumerable SomeNumbers()  
{  
    yield return 3;  
    yield return 5;  
    yield return 8;  
}  
```  
  
 Zwracany typ metody iterator lub `get` dostępu może być <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, lub <xref:System.Collections.Generic.IEnumerator%601>.  
  
 Można użyć `yield break` instrukcji, aby zakończyć iterację.  
  
 Iteratory zostały wprowadzone w języku C# w programie Visual Studio 2005.  
  
 **W tym temacie**  
  
-   [Prostego iteratora](#BKMK_SimpleIterator)  
  
-   [Tworzenie klasy kolekcji](#BKMK_CollectionClass)  
  
-   [Przy użyciu Iteratory z listą ogólnych](#BKMK_GenericList)  
  
-   [Informacje o składni](#BKMK_SyntaxInformation)  
  
-   [Implementacja techniczna](#BKMK_Technical)  
  
-   [Użyj Iteratory](#BKMK_UseOfIterators)  
  
> [!NOTE]
>  Wszystkie przykłady w tym temacie, z wyjątkiem przykład prostego iteratora, obejmują [przy użyciu](../../../csharp/language-reference/keywords/using-directive.md) dyrektywy `System.Collections` i `System.Collections.Generic` przestrzeni nazw.  
  
##  <a name="BKMK_SimpleIterator"></a> Prostego iteratora  
 W poniższym przykładzie przedstawiono jeden `yield return` instrukcji, która znajduje się wewnątrz [dla](../../../csharp/language-reference/keywords/for.md) pętli. W `Main`, każdej iteracji `foreach` treść instrukcji tworzy wywołanie funkcji iteracyjnej, który przechodzi do następnego `yield return` instrukcji.  
  
```csharp  
static void Main()  
{  
    foreach (int number in EvenSequence(5, 18))  
    {  
        Console.Write(number.ToString() + " ");  
    }  
    // Output: 6 8 10 12 14 16 18  
    Console.ReadKey();  
}  
  
public static System.Collections.Generic.IEnumerable<int>  
    EvenSequence(int firstNumber, int lastNumber)  
{  
    // Yield even numbers in the range.  
    for (int number = firstNumber; number <= lastNumber; number++)  
    {  
        if (number % 2 == 0)  
        {  
            yield return number;  
        }  
    }  
}  
```  
  
##  <a name="BKMK_CollectionClass"></a> Tworzenie klasy kolekcji  
 W poniższym przykładzie `DaysOfTheWeek` klasa implementuje <xref:System.Collections.IEnumerable> interfejs, który wymaga <xref:System.Collections.IEnumerable.GetEnumerator%2A> metody. Kompilator niejawnie wywołuje `GetEnumerator` metody, która zwraca <xref:System.Collections.IEnumerator>.  
  
 `GetEnumerator` Metoda zwraca każdego jednego ciągu w czasie przy użyciu `yield return` instrukcji.  
  
```csharp  
static void Main()  
{  
    DaysOfTheWeek days = new DaysOfTheWeek();  
  
    foreach (string day in days)  
    {  
        Console.Write(day + " ");  
    }  
    // Output: Sun Mon Tue Wed Thu Fri Sat  
    Console.ReadKey();  
}  
  
public class DaysOfTheWeek : IEnumerable  
{  
    private string[] days = { "Sun", "Mon", "Tue", "Wed", "Thu", "Fri", "Sat" };  
  
    public IEnumerator GetEnumerator()  
    {  
        for (int index = 0; index < days.Length; index++)  
        {  
            // Yield each day of the week.  
            yield return days[index];  
        }  
    }  
}  
```  
  
 Poniższy przykład tworzy `Zoo` klasy, która zawiera kolekcję zwierząt.  
  
 `foreach` Instrukcji, która odwołuje się do wystąpienia klasy (`theZoo`) niejawnie wywołuje `GetEnumerator` metody. `foreach` Instrukcje odwołujące się do `Birds` i `Mammals` Użyj właściwości `AnimalsForType` o nazwie metody iteracyjnej.  
  
```csharp  
static void Main()  
{  
    Zoo theZoo = new Zoo();  
  
    theZoo.AddMammal("Whale");  
    theZoo.AddMammal("Rhinoceros");  
    theZoo.AddBird("Penguin");  
    theZoo.AddBird("Warbler");  
  
    foreach (string name in theZoo)  
    {  
        Console.Write(name + " ");  
    }  
    Console.WriteLine();  
    // Output: Whale Rhinoceros Penguin Warbler  
  
    foreach (string name in theZoo.Birds)  
    {  
        Console.Write(name + " ");  
    }  
    Console.WriteLine();  
    // Output: Penguin Warbler  
  
    foreach (string name in theZoo.Mammals)  
    {  
        Console.Write(name + " ");  
    }  
    Console.WriteLine();  
    // Output: Whale Rhinoceros  
  
    Console.ReadKey();  
}  
  
public class Zoo : IEnumerable  
{  
    // Private members.  
    private List<Animal> animals = new List<Animal>();  
  
    // Public methods.  
    public void AddMammal(string name)  
    {  
        animals.Add(new Animal { Name = name, Type = Animal.TypeEnum.Mammal });  
    }  
  
    public void AddBird(string name)  
    {  
        animals.Add(new Animal { Name = name, Type = Animal.TypeEnum.Bird });  
    }  
  
    public IEnumerator GetEnumerator()  
    {  
        foreach (Animal theAnimal in animals)  
        {  
            yield return theAnimal.Name;  
        }  
    }  
  
    // Public members.  
    public IEnumerable Mammals  
    {  
        get { return AnimalsForType(Animal.TypeEnum.Mammal); }  
    }  
  
    public IEnumerable Birds  
    {  
        get { return AnimalsForType(Animal.TypeEnum.Bird); }  
    }  
  
    // Private methods.  
    private IEnumerable AnimalsForType(Animal.TypeEnum type)  
    {  
        foreach (Animal theAnimal in animals)  
        {  
            if (theAnimal.Type == type)  
            {  
                yield return theAnimal.Name;  
            }  
        }  
    }  
  
    // Private class.  
    private class Animal  
    {  
        public enum TypeEnum { Bird, Mammal }  
  
        public string Name { get; set; }  
        public TypeEnum Type { get; set; }  
    }  
}  
```  
  
##  <a name="BKMK_GenericList"></a> Przy użyciu Iteratory z listą ogólnych  
 W poniższym przykładzie `Stack(Of T)` implementuje klasy ogólnej <xref:System.Collections.Generic.IEnumerable%601> interfejs generyczny. `Push` Metody przypisuje wartości do tablicy typu `T`. <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> Metoda zwraca wartości w tablicy przy użyciu `yield return` instrukcji.  
  
 Oprócz ogólnego <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> metoda, inny niż ogólny <xref:System.Collections.IEnumerable.GetEnumerator%2A> metoda musi zostać wdrożona. Jest to spowodowane <xref:System.Collections.Generic.IEnumerable%601> dziedziczy <xref:System.Collections.IEnumerable>. Implementację nieogólnego różni się do ogólnego implementacji.  
  
 W przykładzie użyto nazwanego Iteratory do obsługi różnych sposobów iteracji w tej samej kolekcji danych. Są one o nazwie Iteratory `TopToBottom` i `BottomToTop` właściwości oraz `TopN` metody.  
  
 `BottomToTop` Właściwość używa iterację w `get` metody dostępu.  
  
```csharp  
static void Main()  
{  
    Stack<int> theStack = new Stack<int>();  
  
    //  Add items to the stack.  
    for (int number = 0; number <= 9; number++)  
    {  
        theStack.Push(number);  
    }  
  
    // Retrieve items from the stack.  
    // foreach is allowed because theStack implements  
    // IEnumerable<int>.  
    foreach (int number in theStack)  
    {  
        Console.Write("{0} ", number);  
    }  
    Console.WriteLine();  
    // Output: 9 8 7 6 5 4 3 2 1 0  
  
    // foreach is allowed, because theStack.TopToBottom  
    // returns IEnumerable(Of Integer).  
    foreach (int number in theStack.TopToBottom)  
    {  
        Console.Write("{0} ", number);  
    }  
    Console.WriteLine();  
    // Output: 9 8 7 6 5 4 3 2 1 0  
  
    foreach (int number in theStack.BottomToTop)  
    {  
        Console.Write("{0} ", number);  
    }  
    Console.WriteLine();  
    // Output: 0 1 2 3 4 5 6 7 8 9  
  
    foreach (int number in theStack.TopN(7))  
    {  
        Console.Write("{0} ", number);  
    }  
    Console.WriteLine();  
    // Output: 9 8 7 6 5 4 3  
  
    Console.ReadKey();  
}  
  
public class Stack<T> : IEnumerable<T>  
{  
    private T[] values = new T[100];  
    private int top = 0;  
  
    public void Push(T t)  
    {  
        values[top] = t;  
        top++;  
    }  
    public T Pop()  
    {  
        top--;  
        return values[top];  
    }  
  
    // This method implements the GetEnumerator method. It allows  
    // an instance of the class to be used in a foreach statement.  
    public IEnumerator<T> GetEnumerator()  
    {  
        for (int index = top - 1; index >= 0; index--)  
        {  
            yield return values[index];  
        }  
    }  
  
    IEnumerator IEnumerable.GetEnumerator()  
    {  
        return GetEnumerator();  
    }  
  
    public IEnumerable<T> TopToBottom  
    {  
        get { return this; }  
    }  
  
    public IEnumerable<T> BottomToTop  
    {  
        get  
        {  
            for (int index = 0; index <= top - 1; index++)  
            {  
                yield return values[index];  
            }  
        }  
    }  
  
    public IEnumerable<T> TopN(int itemsFromTop)  
    {  
        // Return less than itemsFromTop if necessary.  
        int startIndex = itemsFromTop >= top ? 0 : top - itemsFromTop;  
  
        for (int index = top - 1; index >= startIndex; index--)  
        {  
            yield return values[index];  
        }  
    }  
  
}  
```  
  
##  <a name="BKMK_SyntaxInformation"></a> Informacje o składni  
 Iteratora może wystąpić jako metody lub `get` dostępu. Iterator nie może wystąpić w zdarzeń, konstruktora wystąpienia, Konstruktor statyczny lub finalizatora statycznych.  
  
 Niejawna konwersja musi istnieć od typ wyrażenia w `yield return` instrukcji, aby zwracany typ iteratora.  
  
 W języku C#, metody iteracyjne nie mogą zawierać `in`, `ref`, lub `out` parametrów.  
  
 W języku C# "yield" nie jest słowem zastrzeżonym i ma specjalne znaczenie tylko wtedy, gdy jest używana przed `return` lub `break` — słowo kluczowe.  
  
##  <a name="BKMK_Technical"></a> Implementacja techniczna  
 Mimo że pisania iteratora jako metoda kompilator tłumaczy go na zagnieżdżona klasa oznacza to, w efekcie automatu stanów. Ta klasa przechowuje informacje o pozycja iteratora, jak długo `foreach` nadal pętli w kodzie klienta.  
  
 Aby zobaczyć, co oznacza kompilatora, narzędzie Ildasm.exe służy do wyświetlania kod języka pośredniego firmy Microsoft, który jest generowany dla metody iterator.  
  
 Po utworzeniu iteratora dla [klasy](../../../csharp/language-reference/keywords/class.md) lub [struktury](../../../csharp/language-reference/keywords/struct.md), nie trzeba zaimplementować całego <xref:System.Collections.IEnumerator> interfejsu. Kompilator wykrycie iteratora automatycznie generuje `Current`, `MoveNext`, i `Dispose` metody <xref:System.Collections.IEnumerator> lub <xref:System.Collections.Generic.IEnumerator%601> interfejsu.  
  
 W każdej iteracji kolejnych `foreach` pętli (lub bezpośrednie wywołanie `IEnumerator.MoveNext`), treść kodu dalej iteratora zostanie wznowione po poprzedniej `yield return` instrukcji. Następnie jest kontynuowana do następnego `yield return` instrukcji, dopóki nie zostanie osiągnięty koniec treści iteratora, lub do czasu `yield break` napotkano instrukcji.  
  
 Iteratory nie obsługują <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> metody. Aby ponownie przejść od początku, należy uzyskać nowe iteratora.  
  
 Aby uzyskać dodatkowe informacje, zobacz [specyfikacji języka C#](../../../csharp/language-reference/language-specification/index.md).  
  
##  <a name="BKMK_UseOfIterators"></a> Użyj Iteratory  
 Iteratory umożliwiają zachować prostotę `foreach` pętli, gdy musisz użyć złożonego kodu do wypełniania kolejność listy. Może to być przydatne, jeśli chcesz wykonać następujące czynności:  
  
-   Zmodyfikuj kolejność listy po pierwszym `foreach` iteracji pętli.  
  
-   Unikaj pełni ładowania dużych listy przed pierwszym iteracji `foreach` pętli. Przykładem jest stronicowana pobierania załadować partii wierszy tabeli. Innym przykładem jest <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> metodę, która implementuje Iteratory w programie .NET Framework.  
  
-   Hermetyzuj Tworzenie listy w iteratora. W metodzie iteracyjnej można utworzyć listy i instrukcji yield każdy wynik w pętli.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Collections.Generic>  
 <xref:System.Collections.Generic.IEnumerable%601>  
 [foreach, in](../../../csharp/language-reference/keywords/foreach-in.md)  
 [yield](../../../csharp/language-reference/keywords/yield.md)  
 [Używanie instrukcji foreach z tablicami](../../../csharp/programming-guide/arrays/using-foreach-with-arrays.md)  
 [Typy ogólne](../../../csharp/programming-guide/generics/index.md)

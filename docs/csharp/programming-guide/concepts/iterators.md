---
title: Iteratory (C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: c93f6dd4-e72a-4a06-be1c-a98b3255b734
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6d4994ea57d9fd0df8dfca7ffa40c280499caee6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iterators-c"></a><span data-ttu-id="139dc-102">Iteratory (C#)</span><span class="sxs-lookup"><span data-stu-id="139dc-102">Iterators (C#)</span></span>
<span data-ttu-id="139dc-103">*Iterator* może służyć do kroków opisanych w kolekcji, takie jak listy i stałych.</span><span class="sxs-lookup"><span data-stu-id="139dc-103">An *iterator* can be used to step through collections such as lists and arrays.</span></span>  
  
 <span data-ttu-id="139dc-104">Metody iterator lub `get` akcesor wykonuje niestandardowych iteracji w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="139dc-104">An iterator method or `get` accessor performs a custom iteration over a collection.</span></span> <span data-ttu-id="139dc-105">Iterator — metoda korzysta z [yield return](../../../csharp/language-reference/keywords/yield.md) instrukcji, aby zwracany był każdy element jednym naraz.</span><span class="sxs-lookup"><span data-stu-id="139dc-105">An iterator method uses the [yield return](../../../csharp/language-reference/keywords/yield.md) statement to return each element one at a time.</span></span> <span data-ttu-id="139dc-106">Gdy `yield return` osiągnięciu instrukcji zapamiętanych bieżącej lokalizacji w kodzie.</span><span class="sxs-lookup"><span data-stu-id="139dc-106">When a `yield return` statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="139dc-107">Wykonanie jest uruchamiany ponownie z tej lokalizacji w następnym razem, gdy zostanie wywołana funkcja iteratora.</span><span class="sxs-lookup"><span data-stu-id="139dc-107">Execution is restarted from that location the next time the iterator function is called.</span></span>  
  
 <span data-ttu-id="139dc-108">Korzystać z iteratora z kodu klienta za pomocą [foreach](../../../csharp/language-reference/keywords/foreach-in.md) instrukcji lub za pomocą zapytania LINQ.</span><span class="sxs-lookup"><span data-stu-id="139dc-108">You consume an iterator from client code by using a [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement or by using a LINQ query.</span></span>  
  
 <span data-ttu-id="139dc-109">W poniższym przykładzie pierwszej iteracji `foreach` pętli powoduje wykonanie kontynuować w `SomeNumbers` metody iteracyjnej do pierwszego `yield return` osiągnięciu instrukcji.</span><span class="sxs-lookup"><span data-stu-id="139dc-109">In the following example, the first iteration of the `foreach` loop causes execution to proceed  in the `SomeNumbers` iterator method until the first `yield return` statement is reached.</span></span> <span data-ttu-id="139dc-110">Tą iterację zwraca wartość 3 i są przechowywane w bieżącej lokalizacji w metodzie iteracyjnej.</span><span class="sxs-lookup"><span data-stu-id="139dc-110">This iteration returns a value of 3, and the current location in the iterator method is retained.</span></span> <span data-ttu-id="139dc-111">Przy następnej iteracji pętli, wykonywanie w metodzie iteracyjnej będzie kontynuowane z, w którym ją przerwał pracę, ponownie zatrzymywanie po osiągnięciu `yield return` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="139dc-111">On the next iteration of the loop, execution in the iterator method continues from where it left off, again stopping when it reaches a `yield return` statement.</span></span> <span data-ttu-id="139dc-112">Tą iterację zwraca wartość 5, a bieżącą lokalizację w metodzie iteracyjnej ponownie zostanie zachowane.</span><span class="sxs-lookup"><span data-stu-id="139dc-112">This iteration returns a value of 5, and the current location in the iterator method is again retained.</span></span> <span data-ttu-id="139dc-113">Pętla działanie jest kończone po osiągnięciu na końcu metody iteracyjnej.</span><span class="sxs-lookup"><span data-stu-id="139dc-113">The loop completes when the end of the iterator method is reached.</span></span>  
  
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
  
 <span data-ttu-id="139dc-114">Zwracany typ metody iterator lub `get` dostępu może być <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, lub <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="139dc-114">The return type of an iterator method or `get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
 <span data-ttu-id="139dc-115">Można użyć `yield break` instrukcji, aby zakończyć iterację.</span><span class="sxs-lookup"><span data-stu-id="139dc-115">You can use a `yield break` statement to end the iteration.</span></span>  
  
 <span data-ttu-id="139dc-116">Iteratory zostały wprowadzone w języku C# w programie Visual Studio 2005.</span><span class="sxs-lookup"><span data-stu-id="139dc-116">Iterators were introduced in C# in Visual Studio 2005.</span></span>  
  
 <span data-ttu-id="139dc-117">**W tym temacie**</span><span class="sxs-lookup"><span data-stu-id="139dc-117">**In this topic**</span></span>  
  
-   [<span data-ttu-id="139dc-118">Prostego iteratora</span><span class="sxs-lookup"><span data-stu-id="139dc-118">Simple Iterator</span></span>](#BKMK_SimpleIterator)  
  
-   [<span data-ttu-id="139dc-119">Tworzenie klasy kolekcji</span><span class="sxs-lookup"><span data-stu-id="139dc-119">Creating a Collection Class</span></span>](#BKMK_CollectionClass)  
  
-   [<span data-ttu-id="139dc-120">Przy użyciu Iteratory z listą ogólnych</span><span class="sxs-lookup"><span data-stu-id="139dc-120">Using Iterators with a Generic List</span></span>](#BKMK_GenericList)  
  
-   [<span data-ttu-id="139dc-121">Informacje o składni</span><span class="sxs-lookup"><span data-stu-id="139dc-121">Syntax Information</span></span>](#BKMK_SyntaxInformation)  
  
-   [<span data-ttu-id="139dc-122">Implementacja techniczna</span><span class="sxs-lookup"><span data-stu-id="139dc-122">Technical Implementation</span></span>](#BKMK_Technical)  
  
-   [<span data-ttu-id="139dc-123">Użyj Iteratory</span><span class="sxs-lookup"><span data-stu-id="139dc-123">Use of Iterators</span></span>](#BKMK_UseOfIterators)  
  
> [!NOTE]
>  <span data-ttu-id="139dc-124">Wszystkie przykłady w tym temacie, z wyjątkiem przykład prostego iteratora, obejmują [przy użyciu](../../../csharp/language-reference/keywords/using-directive.md) dyrektywy `System.Collections` i `System.Collections.Generic` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="139dc-124">For all examples in this topic except the Simple Iterator example, include [using](../../../csharp/language-reference/keywords/using-directive.md) directives for the `System.Collections` and `System.Collections.Generic` namespaces.</span></span>  
  
##  <a name="BKMK_SimpleIterator"></a><span data-ttu-id="139dc-125">Prostego iteratora</span><span class="sxs-lookup"><span data-stu-id="139dc-125">Simple Iterator</span></span>  
 <span data-ttu-id="139dc-126">W poniższym przykładzie przedstawiono jeden `yield return` instrukcji, która znajduje się wewnątrz [dla](../../../csharp/language-reference/keywords/for.md) pętli.</span><span class="sxs-lookup"><span data-stu-id="139dc-126">The following example has a single `yield return` statement that is inside a [for](../../../csharp/language-reference/keywords/for.md) loop.</span></span> <span data-ttu-id="139dc-127">W `Main`, każdej iteracji `foreach` treść instrukcji tworzy wywołanie funkcji iteracyjnej, który przechodzi do następnego `yield return` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="139dc-127">In `Main`, each iteration of the `foreach` statement body creates a call to the iterator function, which proceeds to the next `yield return` statement.</span></span>  
  
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
  
##  <a name="BKMK_CollectionClass"></a><span data-ttu-id="139dc-128">Tworzenie klasy kolekcji</span><span class="sxs-lookup"><span data-stu-id="139dc-128">Creating a Collection Class</span></span>  
 <span data-ttu-id="139dc-129">W poniższym przykładzie `DaysOfTheWeek` klasa implementuje <xref:System.Collections.IEnumerable> interfejs, który wymaga <xref:System.Collections.IEnumerable.GetEnumerator%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="139dc-129">In the following example, the `DaysOfTheWeek` class implements the <xref:System.Collections.IEnumerable> interface, which requires a <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span> <span data-ttu-id="139dc-130">Kompilator niejawnie wywołuje `GetEnumerator` metody, która zwraca <xref:System.Collections.IEnumerator>.</span><span class="sxs-lookup"><span data-stu-id="139dc-130">The compiler implicitly calls the `GetEnumerator` method, which returns an <xref:System.Collections.IEnumerator>.</span></span>  
  
 <span data-ttu-id="139dc-131">`GetEnumerator` Metoda zwraca każdego jednego ciągu w czasie przy użyciu `yield return` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="139dc-131">The `GetEnumerator` method returns each string one at a time by using the `yield return` statement.</span></span>  
  
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
  
 <span data-ttu-id="139dc-132">Poniższy przykład tworzy `Zoo` klasy, która zawiera kolekcję zwierząt.</span><span class="sxs-lookup"><span data-stu-id="139dc-132">The following example creates a `Zoo` class that contains a collection of animals.</span></span>  
  
 <span data-ttu-id="139dc-133">`foreach` Instrukcji, która odwołuje się do wystąpienia klasy (`theZoo`) niejawnie wywołuje `GetEnumerator` metody.</span><span class="sxs-lookup"><span data-stu-id="139dc-133">The `foreach` statement that refers to the class instance (`theZoo`) implicitly calls the `GetEnumerator` method.</span></span> <span data-ttu-id="139dc-134">`foreach` Instrukcje odwołujące się do `Birds` i `Mammals` Użyj właściwości `AnimalsForType` o nazwie metody iteracyjnej.</span><span class="sxs-lookup"><span data-stu-id="139dc-134">The `foreach` statements that refer to the `Birds` and `Mammals` properties use the `AnimalsForType` named iterator method.</span></span>  
  
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
  
##  <a name="BKMK_GenericList"></a><span data-ttu-id="139dc-135">Przy użyciu Iteratory z listą ogólnych</span><span class="sxs-lookup"><span data-stu-id="139dc-135">Using Iterators with a Generic List</span></span>  
 <span data-ttu-id="139dc-136">W poniższym przykładzie `Stack(Of T)` implementuje klasy ogólnej <xref:System.Collections.Generic.IEnumerable%601> interfejs generyczny.</span><span class="sxs-lookup"><span data-stu-id="139dc-136">In the following example, the `Stack(Of T)` generic class implements the <xref:System.Collections.Generic.IEnumerable%601> generic interface.</span></span> <span data-ttu-id="139dc-137">`Push` Metody przypisuje wartości do tablicy typu `T`.</span><span class="sxs-lookup"><span data-stu-id="139dc-137">The `Push` method assigns values to an array of type `T`.</span></span> <span data-ttu-id="139dc-138"><xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> Metoda zwraca wartości w tablicy przy użyciu `yield return` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="139dc-138">The <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method returns the array values by using the `yield return` statement.</span></span>  
  
 <span data-ttu-id="139dc-139">Oprócz ogólnego <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> metoda, inny niż ogólny <xref:System.Collections.IEnumerable.GetEnumerator%2A> metoda musi zostać wdrożona.</span><span class="sxs-lookup"><span data-stu-id="139dc-139">In addition to the generic <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method, the non-generic <xref:System.Collections.IEnumerable.GetEnumerator%2A> method must also be implemented.</span></span> <span data-ttu-id="139dc-140">Jest to spowodowane <xref:System.Collections.Generic.IEnumerable%601> dziedziczy <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="139dc-140">This is because <xref:System.Collections.Generic.IEnumerable%601> inherits from <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="139dc-141">Implementację nieogólnego różni się do ogólnego implementacji.</span><span class="sxs-lookup"><span data-stu-id="139dc-141">The non-generic implementation defers to the generic implementation.</span></span>  
  
 <span data-ttu-id="139dc-142">W przykładzie użyto nazwanego Iteratory do obsługi różnych sposobów iteracji w tej samej kolekcji danych.</span><span class="sxs-lookup"><span data-stu-id="139dc-142">The example uses named iterators to support various ways of iterating through the same collection of data.</span></span> <span data-ttu-id="139dc-143">Są one o nazwie Iteratory `TopToBottom` i `BottomToTop` właściwości oraz `TopN` metody.</span><span class="sxs-lookup"><span data-stu-id="139dc-143">These named iterators are the `TopToBottom` and `BottomToTop` properties, and the `TopN` method.</span></span>  
  
 <span data-ttu-id="139dc-144">`BottomToTop` Właściwość używa iterację w `get` metody dostępu.</span><span class="sxs-lookup"><span data-stu-id="139dc-144">The `BottomToTop` property uses an iterator in a `get` accessor.</span></span>  
  
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
  
##  <a name="BKMK_SyntaxInformation"></a><span data-ttu-id="139dc-145">Informacje o składni</span><span class="sxs-lookup"><span data-stu-id="139dc-145">Syntax Information</span></span>  
 <span data-ttu-id="139dc-146">Iteratora może wystąpić jako metody lub `get` dostępu.</span><span class="sxs-lookup"><span data-stu-id="139dc-146">An iterator can occur as a method or `get` accessor.</span></span> <span data-ttu-id="139dc-147">Iterator nie może wystąpić w zdarzeń, konstruktora wystąpienia, Konstruktor statyczny lub finalizatora statycznych.</span><span class="sxs-lookup"><span data-stu-id="139dc-147">An iterator cannot occur in an event, instance constructor, static constructor, or static finalizer.</span></span>  
  
 <span data-ttu-id="139dc-148">Niejawna konwersja musi istnieć od typ wyrażenia w `yield return` instrukcji, aby zwracany typ iteratora.</span><span class="sxs-lookup"><span data-stu-id="139dc-148">An implicit conversion must exist from the expression type in the `yield return` statement to the return type of the iterator.</span></span>  
  
 <span data-ttu-id="139dc-149">W języku C#, metody iteracyjne nie mogą zawierać `ref` lub `out` parametrów.</span><span class="sxs-lookup"><span data-stu-id="139dc-149">In C#, an iterator method cannot have any `ref` or `out` parameters.</span></span>  
  
 <span data-ttu-id="139dc-150">W języku C# "yield" nie jest słowem zastrzeżonym i ma specjalne znaczenie tylko wtedy, gdy jest używana przed `return` lub `break` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="139dc-150">In C#, "yield" is not a reserved word and has special meaning only when it is used before a `return` or `break` keyword.</span></span>  
  
##  <a name="BKMK_Technical"></a><span data-ttu-id="139dc-151">Implementacja techniczna</span><span class="sxs-lookup"><span data-stu-id="139dc-151">Technical Implementation</span></span>  
 <span data-ttu-id="139dc-152">Mimo że pisania iteratora jako metoda kompilator tłumaczy go na zagnieżdżona klasa oznacza to, w efekcie automatu stanów.</span><span class="sxs-lookup"><span data-stu-id="139dc-152">Although you write an iterator as a method, the compiler translates it into a nested class that is, in effect, a state machine.</span></span> <span data-ttu-id="139dc-153">Ta klasa przechowuje informacje o pozycja iteratora, jak długo `foreach` nadal pętli w kodzie klienta.</span><span class="sxs-lookup"><span data-stu-id="139dc-153">This class keeps track of the position of the iterator as long the `foreach` loop in the client code continues.</span></span>  
  
 <span data-ttu-id="139dc-154">Aby zobaczyć, co oznacza kompilatora, narzędzie Ildasm.exe służy do wyświetlania kod języka pośredniego firmy Microsoft, który jest generowany dla metody iterator.</span><span class="sxs-lookup"><span data-stu-id="139dc-154">To see what the compiler does, you can use the Ildasm.exe tool to view the Microsoft intermediate language code that is generated for an iterator method.</span></span>  
  
 <span data-ttu-id="139dc-155">Po utworzeniu iteratora dla [klasy](../../../csharp/language-reference/keywords/class.md) lub [struktury](../../../csharp/language-reference/keywords/struct.md), nie trzeba zaimplementować całego <xref:System.Collections.IEnumerator> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="139dc-155">When you create an iterator for a [class](../../../csharp/language-reference/keywords/class.md) or [struct](../../../csharp/language-reference/keywords/struct.md), you don't have to implement the whole <xref:System.Collections.IEnumerator> interface.</span></span> <span data-ttu-id="139dc-156">Kompilator wykrycie iteratora automatycznie generuje `Current`, `MoveNext`, i `Dispose` metody <xref:System.Collections.IEnumerator> lub <xref:System.Collections.Generic.IEnumerator%601> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="139dc-156">When the compiler detects the iterator, it automatically generates the `Current`, `MoveNext`, and `Dispose` methods of the <xref:System.Collections.IEnumerator> or <xref:System.Collections.Generic.IEnumerator%601> interface.</span></span>  
  
 <span data-ttu-id="139dc-157">W każdej iteracji kolejnych `foreach` pętli (lub bezpośrednie wywołanie `IEnumerator.MoveNext`), treść kodu dalej iteratora zostanie wznowione po poprzedniej `yield return` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="139dc-157">On each successive iteration of the `foreach` loop (or the direct call to `IEnumerator.MoveNext`), the next iterator code body resumes after the previous `yield return` statement.</span></span> <span data-ttu-id="139dc-158">Następnie jest kontynuowana do następnego `yield return` instrukcji, dopóki nie zostanie osiągnięty koniec treści iteratora, lub do czasu `yield break` napotkano instrukcji.</span><span class="sxs-lookup"><span data-stu-id="139dc-158">It then continues to the next `yield return` statement until the end of the iterator body is reached, or until a `yield break` statement is encountered.</span></span>  
  
 <span data-ttu-id="139dc-159">Iteratory nie obsługują <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="139dc-159">Iterators don't support the <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="139dc-160">Aby ponownie przejść od początku, należy uzyskać nowe iteratora.</span><span class="sxs-lookup"><span data-stu-id="139dc-160">To re-iterate from the start, you must obtain a new iterator.</span></span>  
  
 <span data-ttu-id="139dc-161">Aby uzyskać dodatkowe informacje, zobacz [specyfikacji języka C#](../../../csharp/language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="139dc-161">For additional information, see the [C# Language Specification](../../../csharp/language-reference/language-specification/index.md).</span></span>  
  
##  <a name="BKMK_UseOfIterators"></a><span data-ttu-id="139dc-162">Użyj Iteratory</span><span class="sxs-lookup"><span data-stu-id="139dc-162">Use of Iterators</span></span>  
 <span data-ttu-id="139dc-163">Iteratory umożliwiają zachować prostotę `foreach` pętli, gdy musisz użyć złożonego kodu do wypełniania kolejność listy.</span><span class="sxs-lookup"><span data-stu-id="139dc-163">Iterators enable you to maintain the simplicity of a `foreach` loop when you need to use complex code to populate a list sequence.</span></span> <span data-ttu-id="139dc-164">Może to być przydatne, jeśli chcesz wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="139dc-164">This can be useful when you want to do the following:</span></span>  
  
-   <span data-ttu-id="139dc-165">Zmodyfikuj kolejność listy po pierwszym `foreach` iteracji pętli.</span><span class="sxs-lookup"><span data-stu-id="139dc-165">Modify the list sequence after the first `foreach` loop iteration.</span></span>  
  
-   <span data-ttu-id="139dc-166">Unikaj pełni ładowania dużych listy przed pierwszym iteracji `foreach` pętli.</span><span class="sxs-lookup"><span data-stu-id="139dc-166">Avoid fully loading a large list before the first iteration of a `foreach` loop.</span></span> <span data-ttu-id="139dc-167">Przykładem jest stronicowana pobierania załadować partii wierszy tabeli.</span><span class="sxs-lookup"><span data-stu-id="139dc-167">An example is a paged fetch to load a batch of table rows.</span></span> <span data-ttu-id="139dc-168">Innym przykładem jest <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> metodę, która implementuje Iteratory w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="139dc-168">Another example is the <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> method, which implements iterators within the .NET Framework.</span></span>  
  
-   <span data-ttu-id="139dc-169">Hermetyzuj Tworzenie listy w iteratora.</span><span class="sxs-lookup"><span data-stu-id="139dc-169">Encapsulate building the list in the iterator.</span></span> <span data-ttu-id="139dc-170">W metodzie iteracyjnej można utworzyć listy i instrukcji yield każdy wynik w pętli.</span><span class="sxs-lookup"><span data-stu-id="139dc-170">In the iterator method, you can build the list and then yield each result in a loop.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="139dc-171">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="139dc-171">See Also</span></span>  
 <xref:System.Collections.Generic>  
 <xref:System.Collections.Generic.IEnumerable%601>  
 [<span data-ttu-id="139dc-172">Instrukcja foreach w</span><span class="sxs-lookup"><span data-stu-id="139dc-172">foreach, in</span></span>](../../../csharp/language-reference/keywords/foreach-in.md)  
 [<span data-ttu-id="139dc-173">YIELD</span><span class="sxs-lookup"><span data-stu-id="139dc-173">yield</span></span>](../../../csharp/language-reference/keywords/yield.md)  
 [<span data-ttu-id="139dc-174">Używanie instrukcji foreach z tablicami</span><span class="sxs-lookup"><span data-stu-id="139dc-174">Using foreach with Arrays</span></span>](../../../csharp/programming-guide/arrays/using-foreach-with-arrays.md)  
 [<span data-ttu-id="139dc-175">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="139dc-175">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)

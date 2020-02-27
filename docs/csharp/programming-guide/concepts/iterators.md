---
title: Iterowanie przez kolekcje wC#
ms.date: 08/14/2018
ms.assetid: c93f6dd4-e72a-4a06-be1c-a98b3255b734
ms.openlocfilehash: aceedd11466c75cedad3c67224c3a5595b4cabfa
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626273"
---
# <a name="iterators-c"></a><span data-ttu-id="5c196-102">Iteratory (C#)</span><span class="sxs-lookup"><span data-stu-id="5c196-102">Iterators (C#)</span></span>

<span data-ttu-id="5c196-103">*Iterator* może służyć do przechodzenia między kolekcjami, takimi jak listy i tablice.</span><span class="sxs-lookup"><span data-stu-id="5c196-103">An *iterator* can be used to step through collections such as lists and arrays.</span></span>

<span data-ttu-id="5c196-104">Metoda iteratora lub akcesor `get` wykonuje niestandardową iterację w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="5c196-104">An iterator method or `get` accessor performs a custom iteration over a collection.</span></span> <span data-ttu-id="5c196-105">Metoda iterator używa instrukcji [yield return](../../language-reference/keywords/yield.md) , aby zwrócić każdy element po jednym naraz.</span><span class="sxs-lookup"><span data-stu-id="5c196-105">An iterator method uses the [yield return](../../language-reference/keywords/yield.md) statement to return each element one at a time.</span></span> <span data-ttu-id="5c196-106">Po osiągnięciu instrukcji `yield return` bieżąca lokalizacja w kodzie jest zapamiętywana.</span><span class="sxs-lookup"><span data-stu-id="5c196-106">When a `yield return` statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="5c196-107">Wykonanie jest uruchamiane ponownie z tej lokalizacji przy następnym wywołaniu funkcji iteratora.</span><span class="sxs-lookup"><span data-stu-id="5c196-107">Execution is restarted from that location the next time the iterator function is called.</span></span>

<span data-ttu-id="5c196-108">Iterator z kodu klienta jest używany przy użyciu instrukcji [foreach](../../language-reference/keywords/foreach-in.md) lub zapytania LINQ.</span><span class="sxs-lookup"><span data-stu-id="5c196-108">You consume an iterator from client code by using a [foreach](../../language-reference/keywords/foreach-in.md) statement or by using a LINQ query.</span></span>

<span data-ttu-id="5c196-109">W poniższym przykładzie pierwsza iteracja pętli `foreach` powoduje, że wykonanie w metodzie iteratora `SomeNumbers` do momentu osiągnięcia pierwszej instrukcji `yield return`.</span><span class="sxs-lookup"><span data-stu-id="5c196-109">In the following example, the first iteration of the `foreach` loop causes execution to proceed in the `SomeNumbers` iterator method until the first `yield return` statement is reached.</span></span> <span data-ttu-id="5c196-110">Ta iteracja zwraca wartość 3, a bieżąca lokalizacja w metodzie iteratora jest zachowywana.</span><span class="sxs-lookup"><span data-stu-id="5c196-110">This iteration returns a value of 3, and the current location in the iterator method is retained.</span></span> <span data-ttu-id="5c196-111">W następnej iteracji pętli wykonywanie w metodzie iteratora jest kontynuowane od miejsca, w którym została pozostawiona, i ponownie zatrzymywane, gdy dociera do instrukcji `yield return`.</span><span class="sxs-lookup"><span data-stu-id="5c196-111">On the next iteration of the loop, execution in the iterator method continues from where it left off, again stopping when it reaches a `yield return` statement.</span></span> <span data-ttu-id="5c196-112">Ta iteracja zwraca wartość 5, a bieżąca lokalizacja w metodzie iteratora jest zachowywana ponownie.</span><span class="sxs-lookup"><span data-stu-id="5c196-112">This iteration returns a value of 5, and the current location in the iterator method is again retained.</span></span> <span data-ttu-id="5c196-113">Pętla kończy się, gdy zostanie osiągnięty koniec metody iteratora.</span><span class="sxs-lookup"><span data-stu-id="5c196-113">The loop completes when the end of the iterator method is reached.</span></span>

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

<span data-ttu-id="5c196-114">Typem zwracanym metody iteratora lub metodzie dostępu `get` może być <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>lub <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="5c196-114">The return type of an iterator method or `get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>

<span data-ttu-id="5c196-115">Możesz użyć instrukcji `yield break`, aby zakończyć iterację.</span><span class="sxs-lookup"><span data-stu-id="5c196-115">You can use a `yield break` statement to end the iteration.</span></span>

> [!NOTE]
> <span data-ttu-id="5c196-116">We wszystkich przykładach w tym temacie oprócz prostego przykładu iteratora należy uwzględnić dyrektywy [using](../../language-reference/keywords/using-directive.md) dla przestrzeni nazw `System.Collections` i `System.Collections.Generic`.</span><span class="sxs-lookup"><span data-stu-id="5c196-116">For all examples in this topic except the Simple Iterator example, include [using](../../language-reference/keywords/using-directive.md) directives for the `System.Collections` and `System.Collections.Generic` namespaces.</span></span>

## <a name="simple-iterator"></a><span data-ttu-id="5c196-117">Iterator prosty</span><span class="sxs-lookup"><span data-stu-id="5c196-117">Simple Iterator</span></span>

<span data-ttu-id="5c196-118">Poniższy przykład zawiera jedną instrukcję `yield return`, która znajduje się wewnątrz pętli [for](../../language-reference/keywords/for.md) .</span><span class="sxs-lookup"><span data-stu-id="5c196-118">The following example has a single `yield return` statement that is inside a [for](../../language-reference/keywords/for.md) loop.</span></span> <span data-ttu-id="5c196-119">W `Main`każda iteracja treści instrukcji `foreach` tworzy wywołanie funkcji iteratora, która przechodzi do następnej instrukcji `yield return`.</span><span class="sxs-lookup"><span data-stu-id="5c196-119">In `Main`, each iteration of the `foreach` statement body creates a call to the iterator function, which proceeds to the next `yield return` statement.</span></span>

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

## <a name="creating-a-collection-class"></a><span data-ttu-id="5c196-120">Tworzenie klasy kolekcji</span><span class="sxs-lookup"><span data-stu-id="5c196-120">Creating a Collection Class</span></span>

<span data-ttu-id="5c196-121">W poniższym przykładzie Klasa `DaysOfTheWeek` implementuje interfejs <xref:System.Collections.IEnumerable>, który wymaga metody <xref:System.Collections.IEnumerable.GetEnumerator%2A>.</span><span class="sxs-lookup"><span data-stu-id="5c196-121">In the following example, the `DaysOfTheWeek` class implements the <xref:System.Collections.IEnumerable> interface, which requires a <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span> <span data-ttu-id="5c196-122">Kompilator niejawnie wywołuje metodę `GetEnumerator`, która zwraca <xref:System.Collections.IEnumerator>.</span><span class="sxs-lookup"><span data-stu-id="5c196-122">The compiler implicitly calls the `GetEnumerator` method, which returns an <xref:System.Collections.IEnumerator>.</span></span>

<span data-ttu-id="5c196-123">Metoda `GetEnumerator` zwraca każdy ciąg pojedynczo przy użyciu instrukcji `yield return`.</span><span class="sxs-lookup"><span data-stu-id="5c196-123">The `GetEnumerator` method returns each string one at a time by using the `yield return` statement.</span></span>

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

<span data-ttu-id="5c196-124">Poniższy przykład tworzy klasę `Zoo`, która zawiera kolekcję zwierząt.</span><span class="sxs-lookup"><span data-stu-id="5c196-124">The following example creates a `Zoo` class that contains a collection of animals.</span></span>

<span data-ttu-id="5c196-125">Instrukcja `foreach`, która odwołuje się do wystąpienia klasy (`theZoo`) niejawnie wywołuje metodę `GetEnumerator`.</span><span class="sxs-lookup"><span data-stu-id="5c196-125">The `foreach` statement that refers to the class instance (`theZoo`) implicitly calls the `GetEnumerator` method.</span></span> <span data-ttu-id="5c196-126">Instrukcje `foreach` odwołujące się do właściwości `Birds` i `Mammals` używają metody iteratora o nazwie `AnimalsForType`.</span><span class="sxs-lookup"><span data-stu-id="5c196-126">The `foreach` statements that refer to the `Birds` and `Mammals` properties use the `AnimalsForType` named iterator method.</span></span>

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

## <a name="using-iterators-with-a-generic-list"></a><span data-ttu-id="5c196-127">Używanie iteratorów z listą ogólną</span><span class="sxs-lookup"><span data-stu-id="5c196-127">Using Iterators with a Generic List</span></span>

<span data-ttu-id="5c196-128">W poniższym przykładzie Klasa generyczna <xref:System.Collections.Generic.Stack%601> implementuje interfejs ogólny <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="5c196-128">In the following example, the <xref:System.Collections.Generic.Stack%601> generic class implements the <xref:System.Collections.Generic.IEnumerable%601> generic interface.</span></span> <span data-ttu-id="5c196-129">Metoda <xref:System.Collections.Generic.Stack%601.Push%2A> przypisuje wartości do tablicy typu `T`.</span><span class="sxs-lookup"><span data-stu-id="5c196-129">The <xref:System.Collections.Generic.Stack%601.Push%2A> method assigns values to an array of type `T`.</span></span> <span data-ttu-id="5c196-130">Metoda <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> zwraca wartości tablicy przy użyciu instrukcji `yield return`.</span><span class="sxs-lookup"><span data-stu-id="5c196-130">The <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method returns the array values by using the `yield return` statement.</span></span>

<span data-ttu-id="5c196-131">Oprócz metody ogólnej <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> należy również zaimplementować metodę nierodzajową <xref:System.Collections.IEnumerable.GetEnumerator%2A>.</span><span class="sxs-lookup"><span data-stu-id="5c196-131">In addition to the generic <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method, the non-generic <xref:System.Collections.IEnumerable.GetEnumerator%2A> method must also be implemented.</span></span> <span data-ttu-id="5c196-132">Dzieje się tak, ponieważ <xref:System.Collections.Generic.IEnumerable%601> dziedziczy po <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="5c196-132">This is because <xref:System.Collections.Generic.IEnumerable%601> inherits from <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="5c196-133">Implementacja nieogólna odłożenia do ogólnej implementacji.</span><span class="sxs-lookup"><span data-stu-id="5c196-133">The non-generic implementation defers to the generic implementation.</span></span>

<span data-ttu-id="5c196-134">W przykładzie używa się nazwanych iteratorów do obsługi różnych sposobów iterowania za pośrednictwem tej samej kolekcji danych.</span><span class="sxs-lookup"><span data-stu-id="5c196-134">The example uses named iterators to support various ways of iterating through the same collection of data.</span></span> <span data-ttu-id="5c196-135">Te nazwane Iteratory są właściwościami `TopToBottom` i `BottomToTop` i metodą `TopN`.</span><span class="sxs-lookup"><span data-stu-id="5c196-135">These named iterators are the `TopToBottom` and `BottomToTop` properties, and the `TopN` method.</span></span>

<span data-ttu-id="5c196-136">Właściwość `BottomToTop` używa iteratora w metodzie dostępu `get`.</span><span class="sxs-lookup"><span data-stu-id="5c196-136">The `BottomToTop` property uses an iterator in a `get` accessor.</span></span>

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
    // foreach is allowed because theStack implements IEnumerable<int>.
    foreach (int number in theStack)
    {
        Console.Write("{0} ", number);
    }
    Console.WriteLine();
    // Output: 9 8 7 6 5 4 3 2 1 0

    // foreach is allowed, because theStack.TopToBottom returns IEnumerable(Of Integer).
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

## <a name="syntax-information"></a><span data-ttu-id="5c196-137">Informacje o składni</span><span class="sxs-lookup"><span data-stu-id="5c196-137">Syntax Information</span></span>

<span data-ttu-id="5c196-138">Iterator może wystąpić jako metoda dostępu metody lub `get`.</span><span class="sxs-lookup"><span data-stu-id="5c196-138">An iterator can occur as a method or `get` accessor.</span></span> <span data-ttu-id="5c196-139">Iterator nie może wystąpić w zdarzeniu, konstruktorze wystąpienia, konstruktorze statycznym lub niestatycznego finalizatora.</span><span class="sxs-lookup"><span data-stu-id="5c196-139">An iterator cannot occur in an event, instance constructor, static constructor, or static finalizer.</span></span>

<span data-ttu-id="5c196-140">Niejawna konwersja musi istnieć z typu wyrażenia w instrukcji `yield return` do argumentu Type dla `IEnumerable<T>` zwróconego przez iterator.</span><span class="sxs-lookup"><span data-stu-id="5c196-140">An implicit conversion must exist from the expression type in the `yield return` statement to the type argument for the `IEnumerable<T>` returned by the iterator.</span></span>

<span data-ttu-id="5c196-141">W C#programie Metoda iteratora nie może mieć żadnych parametrów `in`, `ref`lub `out`.</span><span class="sxs-lookup"><span data-stu-id="5c196-141">In C#, an iterator method cannot have any `in`, `ref`, or `out` parameters.</span></span>

<span data-ttu-id="5c196-142">W C#, `yield` nie jest słowem zastrzeżonym i ma specjalne znaczenie tylko wtedy, gdy jest używany przed słowem kluczowym `return` lub `break`.</span><span class="sxs-lookup"><span data-stu-id="5c196-142">In C#, `yield` is not a reserved word and has special meaning only when it is used before a `return` or `break` keyword.</span></span>

## <a name="technical-implementation"></a><span data-ttu-id="5c196-143">Realizacja techniczna</span><span class="sxs-lookup"><span data-stu-id="5c196-143">Technical Implementation</span></span>

<span data-ttu-id="5c196-144">Chociaż należy napisać iterator jako metodę, kompilator tłumaczy go na zagnieżdżoną klasę, która jest, w efekcie, komputera stanu.</span><span class="sxs-lookup"><span data-stu-id="5c196-144">Although you write an iterator as a method, the compiler translates it into a nested class that is, in effect, a state machine.</span></span> <span data-ttu-id="5c196-145">Ta klasa śledzi pozycję iteratora, tak długo pętla `foreach` w kodzie klienta kontynuuje działanie.</span><span class="sxs-lookup"><span data-stu-id="5c196-145">This class keeps track of the position of the iterator as long the `foreach` loop in the client code continues.</span></span>

<span data-ttu-id="5c196-146">Aby zobaczyć, co robi kompilator, możesz użyć narzędzia Ildasm. exe, aby wyświetlić kod języka pośredniego firmy Microsoft, który został wygenerowany dla metody iteratora.</span><span class="sxs-lookup"><span data-stu-id="5c196-146">To see what the compiler does, you can use the Ildasm.exe tool to view the Microsoft intermediate language code that's generated for an iterator method.</span></span>

<span data-ttu-id="5c196-147">Podczas tworzenia iteratora dla [klasy](../../language-reference/keywords/class.md) lub [struktury](../../language-reference/builtin-types/struct.md)nie trzeba implementować całego interfejsu <xref:System.Collections.IEnumerator>.</span><span class="sxs-lookup"><span data-stu-id="5c196-147">When you create an iterator for a [class](../../language-reference/keywords/class.md) or [struct](../../language-reference/builtin-types/struct.md), you don't have to implement the whole <xref:System.Collections.IEnumerator> interface.</span></span> <span data-ttu-id="5c196-148">Gdy kompilator wykryje iterator, automatycznie generuje metody `Current`, `MoveNext`i `Dispose` interfejsu <xref:System.Collections.IEnumerator> lub <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="5c196-148">When the compiler detects the iterator, it automatically generates the `Current`, `MoveNext`, and `Dispose` methods of the <xref:System.Collections.IEnumerator> or <xref:System.Collections.Generic.IEnumerator%601> interface.</span></span>

<span data-ttu-id="5c196-149">Dla każdej kolejnej iteracji pętli `foreach` (lub bezpośredniego wywołania do `IEnumerator.MoveNext`) Następna treść kodu iteratora zostanie wznowiona po poprzedniej instrukcji `yield return`.</span><span class="sxs-lookup"><span data-stu-id="5c196-149">On each successive iteration of the `foreach` loop (or the direct call to `IEnumerator.MoveNext`), the next iterator code body resumes after the previous `yield return` statement.</span></span> <span data-ttu-id="5c196-150">Następnie przechodzi do następnej instrukcji `yield return` do momentu osiągnięcia końca treści iteratora lub do momentu napotkania instrukcji `yield break`.</span><span class="sxs-lookup"><span data-stu-id="5c196-150">It then continues to the next `yield return` statement until the end of the iterator body is reached, or until a `yield break` statement is encountered.</span></span>

<span data-ttu-id="5c196-151">Iteratory nie obsługują metody <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5c196-151">Iterators don't support the <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="5c196-152">Aby wykonać ponowną iterację od początku, należy uzyskać nowy iterator.</span><span class="sxs-lookup"><span data-stu-id="5c196-152">To reiterate from the start, you must obtain a new iterator.</span></span> <span data-ttu-id="5c196-153">Wywołanie <xref:System.Collections.IEnumerator.Reset%2A> w iterator zwrócone przez metodę iteratora zgłasza <xref:System.NotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="5c196-153">Calling <xref:System.Collections.IEnumerator.Reset%2A> on the iterator returned by an iterator method throws a <xref:System.NotSupportedException>.</span></span>

<span data-ttu-id="5c196-154">Aby uzyskać dodatkowe informacje, zobacz [ C# Specyfikacja języka](~/_csharplang/spec/classes.md#iterators).</span><span class="sxs-lookup"><span data-stu-id="5c196-154">For additional information, see the [C# Language Specification](~/_csharplang/spec/classes.md#iterators).</span></span>

## <a name="use-of-iterators"></a><span data-ttu-id="5c196-155">Użycie iteratorów</span><span class="sxs-lookup"><span data-stu-id="5c196-155">Use of Iterators</span></span>

<span data-ttu-id="5c196-156">Iteratory umożliwiają zachowanie prostoty pętli `foreach`, gdy trzeba użyć kodu złożonego, aby wypełnić sekwencję listy.</span><span class="sxs-lookup"><span data-stu-id="5c196-156">Iterators enable you to maintain the simplicity of a `foreach` loop when you need to use complex code to populate a list sequence.</span></span> <span data-ttu-id="5c196-157">Może to być przydatne, gdy chcesz wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="5c196-157">This can be useful when you want to do the following:</span></span>

- <span data-ttu-id="5c196-158">Zmodyfikuj sekwencję list po pierwszej iteracji pętli `foreach`.</span><span class="sxs-lookup"><span data-stu-id="5c196-158">Modify the list sequence after the first `foreach` loop iteration.</span></span>

- <span data-ttu-id="5c196-159">Unikaj całkowitego ładowania dużej listy przed pierwszą iteracją pętli `foreach`.</span><span class="sxs-lookup"><span data-stu-id="5c196-159">Avoid fully loading a large list before the first iteration of a `foreach` loop.</span></span> <span data-ttu-id="5c196-160">Przykładem jest pobieranie stronicowane w celu załadowania partii wierszy tabeli.</span><span class="sxs-lookup"><span data-stu-id="5c196-160">An example is a paged fetch to load a batch of table rows.</span></span> <span data-ttu-id="5c196-161">Innym przykładem jest metoda <xref:System.IO.DirectoryInfo.EnumerateFiles%2A>, która implementuje Iteratory w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="5c196-161">Another example is the <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> method, which implements iterators within the .NET Framework.</span></span>

- <span data-ttu-id="5c196-162">Hermetyzuje Kompilowanie listy w iterator.</span><span class="sxs-lookup"><span data-stu-id="5c196-162">Encapsulate building the list in the iterator.</span></span> <span data-ttu-id="5c196-163">W metodzie iteratora można skompilować listę, a następnie dać każdy wynik w pętli.</span><span class="sxs-lookup"><span data-stu-id="5c196-163">In the iterator method, you can build the list and then yield each result in a loop.</span></span>

## <a name="see-also"></a><span data-ttu-id="5c196-164">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5c196-164">See also</span></span>

- <xref:System.Collections.Generic>
- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="5c196-165">foreach, in</span><span class="sxs-lookup"><span data-stu-id="5c196-165">foreach, in</span></span>](../../language-reference/keywords/foreach-in.md)
- [<span data-ttu-id="5c196-166">yield</span><span class="sxs-lookup"><span data-stu-id="5c196-166">yield</span></span>](../../language-reference/keywords/yield.md)
- [<span data-ttu-id="5c196-167">Używanie instrukcji foreach z tablicami</span><span class="sxs-lookup"><span data-stu-id="5c196-167">Using foreach with Arrays</span></span>](../arrays/using-foreach-with-arrays.md)
- [<span data-ttu-id="5c196-168">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="5c196-168">Generics</span></span>](../generics/index.md)

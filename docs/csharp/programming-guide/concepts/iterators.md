---
title: Iterowanie przez kolekcje wC#
ms.date: 08/14/2018
ms.assetid: c93f6dd4-e72a-4a06-be1c-a98b3255b734
ms.openlocfilehash: d47dcf6e7748f85978b1b0bcf739b5d1280263f3
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69594967"
---
# <a name="iterators-c"></a><span data-ttu-id="ff2fd-102">Iteratory (C#)</span><span class="sxs-lookup"><span data-stu-id="ff2fd-102">Iterators (C#)</span></span>

<span data-ttu-id="ff2fd-103">*Iterator* może służyć do przechodzenia między kolekcjami, takimi jak listy i tablice.</span><span class="sxs-lookup"><span data-stu-id="ff2fd-103">An *iterator* can be used to step through collections such as lists and arrays.</span></span>

<span data-ttu-id="ff2fd-104">Metoda iteratora lub `get` akcesor wykonuje niestandardową iterację w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="ff2fd-104">An iterator method or `get` accessor performs a custom iteration over a collection.</span></span> <span data-ttu-id="ff2fd-105">Metoda iterator używa instrukcji [yield return](../../language-reference/keywords/yield.md) , aby zwrócić każdy element po jednym naraz.</span><span class="sxs-lookup"><span data-stu-id="ff2fd-105">An iterator method uses the [yield return](../../language-reference/keywords/yield.md) statement to return each element one at a time.</span></span> <span data-ttu-id="ff2fd-106">Po osiągnięciu `yield return` instrukcji zostanie zapamiętana bieżąca lokalizacja w kodzie.</span><span class="sxs-lookup"><span data-stu-id="ff2fd-106">When a `yield return` statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="ff2fd-107">Wykonanie jest uruchamiane ponownie z tej lokalizacji przy następnym wywołaniu funkcji iteratora.</span><span class="sxs-lookup"><span data-stu-id="ff2fd-107">Execution is restarted from that location the next time the iterator function is called.</span></span>

<span data-ttu-id="ff2fd-108">Iterator z kodu klienta jest używany przy użyciu instrukcji [foreach](../../language-reference/keywords/foreach-in.md) lub zapytania LINQ.</span><span class="sxs-lookup"><span data-stu-id="ff2fd-108">You consume an iterator from client code by using a [foreach](../../language-reference/keywords/foreach-in.md) statement or by using a LINQ query.</span></span>

<span data-ttu-id="ff2fd-109">W poniższym przykładzie pierwsza iteracja `foreach` pętli powoduje, że wykonywanie jest wykonywane `SomeNumbers` w metodzie iteratora do momentu osiągnięcia `yield return` pierwszej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="ff2fd-109">In the following example, the first iteration of the `foreach` loop causes execution to proceed in the `SomeNumbers` iterator method until the first `yield return` statement is reached.</span></span> <span data-ttu-id="ff2fd-110">Ta iteracja zwraca wartość 3, a bieżąca lokalizacja w metodzie iteratora jest zachowywana.</span><span class="sxs-lookup"><span data-stu-id="ff2fd-110">This iteration returns a value of 3, and the current location in the iterator method is retained.</span></span> <span data-ttu-id="ff2fd-111">W następnej iteracji pętli wykonywanie w metodzie iteratora jest kontynuowane od miejsca, w którym została pozostawiona, po osiągnięciu `yield return` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="ff2fd-111">On the next iteration of the loop, execution in the iterator method continues from where it left off, again stopping when it reaches a `yield return` statement.</span></span> <span data-ttu-id="ff2fd-112">Ta iteracja zwraca wartość 5, a bieżąca lokalizacja w metodzie iteratora jest zachowywana ponownie.</span><span class="sxs-lookup"><span data-stu-id="ff2fd-112">This iteration returns a value of 5, and the current location in the iterator method is again retained.</span></span> <span data-ttu-id="ff2fd-113">Pętla kończy się, gdy zostanie osiągnięty koniec metody iteratora.</span><span class="sxs-lookup"><span data-stu-id="ff2fd-113">The loop completes when the end of the iterator method is reached.</span></span>

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

<span data-ttu-id="ff2fd-114">Typem zwracanym metody iteratora `get` lub akcesora może być <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, lub. <xref:System.Collections.Generic.IEnumerator%601></span><span class="sxs-lookup"><span data-stu-id="ff2fd-114">The return type of an iterator method or `get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>

<span data-ttu-id="ff2fd-115">Możesz użyć `yield break` instrukcji, aby zakończyć iterację.</span><span class="sxs-lookup"><span data-stu-id="ff2fd-115">You can use a `yield break` statement to end the iteration.</span></span>

> [!NOTE]
> <span data-ttu-id="ff2fd-116">We wszystkich przykładach w tym temacie oprócz prostego przykładu iteratora [](../../language-reference/keywords/using-directive.md) należy uwzględnić dyrektywy using `System.Collections` dla `System.Collections.Generic` przestrzeni nazw i.</span><span class="sxs-lookup"><span data-stu-id="ff2fd-116">For all examples in this topic except the Simple Iterator example, include [using](../../language-reference/keywords/using-directive.md) directives for the `System.Collections` and `System.Collections.Generic` namespaces.</span></span>

## <a name="simple-iterator"></a><span data-ttu-id="ff2fd-117">Iterator prosty</span><span class="sxs-lookup"><span data-stu-id="ff2fd-117">Simple Iterator</span></span>

<span data-ttu-id="ff2fd-118">Poniższy przykład zawiera pojedynczą `yield return` instrukcję, która znajduje się wewnątrz pętli [for](../../language-reference/keywords/for.md) .</span><span class="sxs-lookup"><span data-stu-id="ff2fd-118">The following example has a single `yield return` statement that is inside a [for](../../language-reference/keywords/for.md) loop.</span></span> <span data-ttu-id="ff2fd-119">W `Main`programie każda iteracja `foreach` treści instrukcji tworzy wywołanie funkcji iteratora, która przechodzi do następnej `yield return` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="ff2fd-119">In `Main`, each iteration of the `foreach` statement body creates a call to the iterator function, which proceeds to the next `yield return` statement.</span></span>

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

## <a name="creating-a-collection-class"></a><span data-ttu-id="ff2fd-120">Tworzenie klasy kolekcji</span><span class="sxs-lookup"><span data-stu-id="ff2fd-120">Creating a Collection Class</span></span>

<span data-ttu-id="ff2fd-121">W poniższym przykładzie `DaysOfTheWeek` Klasa <xref:System.Collections.IEnumerable> implementuje <xref:System.Collections.IEnumerable.GetEnumerator%2A> interfejs, który wymaga metody.</span><span class="sxs-lookup"><span data-stu-id="ff2fd-121">In the following example, the `DaysOfTheWeek` class implements the <xref:System.Collections.IEnumerable> interface, which requires a <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span> <span data-ttu-id="ff2fd-122">Kompilator niejawnie wywołuje `GetEnumerator` metodę, która <xref:System.Collections.IEnumerator>zwraca.</span><span class="sxs-lookup"><span data-stu-id="ff2fd-122">The compiler implicitly calls the `GetEnumerator` method, which returns an <xref:System.Collections.IEnumerator>.</span></span>

<span data-ttu-id="ff2fd-123">Metoda zwraca każdy ciąg pojedynczo przy `yield return` użyciu instrukcji. `GetEnumerator`</span><span class="sxs-lookup"><span data-stu-id="ff2fd-123">The `GetEnumerator` method returns each string one at a time by using the `yield return` statement.</span></span>

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

<span data-ttu-id="ff2fd-124">Poniższy przykład tworzy `Zoo` klasę, która zawiera kolekcję zwierząt.</span><span class="sxs-lookup"><span data-stu-id="ff2fd-124">The following example creates a `Zoo` class that contains a collection of animals.</span></span>

<span data-ttu-id="ff2fd-125">Instrukcja odwołująca się do wystąpienia klasy (`theZoo`) niejawnie wywołuje `GetEnumerator` metodę. `foreach`</span><span class="sxs-lookup"><span data-stu-id="ff2fd-125">The `foreach` statement that refers to the class instance (`theZoo`) implicitly calls the `GetEnumerator` method.</span></span> <span data-ttu-id="ff2fd-126">Instrukcje odwołujące się `Birds` do właściwości `Mammals` i używają `AnimalsForType` nazwanego metody iteratora. `foreach`</span><span class="sxs-lookup"><span data-stu-id="ff2fd-126">The `foreach` statements that refer to the `Birds` and `Mammals` properties use the `AnimalsForType` named iterator method.</span></span>

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

## <a name="using-iterators-with-a-generic-list"></a><span data-ttu-id="ff2fd-127">Używanie iteratorów z listą ogólną</span><span class="sxs-lookup"><span data-stu-id="ff2fd-127">Using Iterators with a Generic List</span></span>

<span data-ttu-id="ff2fd-128">W poniższym przykładzie <xref:System.Collections.Generic.Stack%601> Klasa generyczna <xref:System.Collections.Generic.IEnumerable%601> implementuje interfejs generyczny.</span><span class="sxs-lookup"><span data-stu-id="ff2fd-128">In the following example, the <xref:System.Collections.Generic.Stack%601> generic class implements the <xref:System.Collections.Generic.IEnumerable%601> generic interface.</span></span> <span data-ttu-id="ff2fd-129">Metoda przypisuje wartości do tablicy typu `T`. <xref:System.Collections.Generic.Stack%601.Push%2A></span><span class="sxs-lookup"><span data-stu-id="ff2fd-129">The <xref:System.Collections.Generic.Stack%601.Push%2A> method assigns values to an array of type `T`.</span></span> <span data-ttu-id="ff2fd-130">Metoda zwraca wartości tablicy przy `yield return` użyciu instrukcji. <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A></span><span class="sxs-lookup"><span data-stu-id="ff2fd-130">The <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method returns the array values by using the `yield return` statement.</span></span>

<span data-ttu-id="ff2fd-131">Oprócz metody ogólnej <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> należy również zaimplementować metodę nierodzajową <xref:System.Collections.IEnumerable.GetEnumerator%2A> .</span><span class="sxs-lookup"><span data-stu-id="ff2fd-131">In addition to the generic <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method, the non-generic <xref:System.Collections.IEnumerable.GetEnumerator%2A> method must also be implemented.</span></span> <span data-ttu-id="ff2fd-132">Wynika to z <xref:System.Collections.Generic.IEnumerable%601> faktu <xref:System.Collections.IEnumerable>, że dziedziczy z.</span><span class="sxs-lookup"><span data-stu-id="ff2fd-132">This is because <xref:System.Collections.Generic.IEnumerable%601> inherits from <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="ff2fd-133">Implementacja nieogólna odłożenia do ogólnej implementacji.</span><span class="sxs-lookup"><span data-stu-id="ff2fd-133">The non-generic implementation defers to the generic implementation.</span></span>

<span data-ttu-id="ff2fd-134">W przykładzie używa się nazwanych iteratorów do obsługi różnych sposobów iterowania za pośrednictwem tej samej kolekcji danych.</span><span class="sxs-lookup"><span data-stu-id="ff2fd-134">The example uses named iterators to support various ways of iterating through the same collection of data.</span></span> <span data-ttu-id="ff2fd-135">Te nazwane Iteratory to `TopToBottom` właściwości `TopN` i `BottomToTop` i metoda.</span><span class="sxs-lookup"><span data-stu-id="ff2fd-135">These named iterators are the `TopToBottom` and `BottomToTop` properties, and the `TopN` method.</span></span>

<span data-ttu-id="ff2fd-136">Właściwość używa iteratora `get` w metodzie dostępu. `BottomToTop`</span><span class="sxs-lookup"><span data-stu-id="ff2fd-136">The `BottomToTop` property uses an iterator in a `get` accessor.</span></span>

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

## <a name="syntax-information"></a><span data-ttu-id="ff2fd-137">Informacje o składni</span><span class="sxs-lookup"><span data-stu-id="ff2fd-137">Syntax Information</span></span>

<span data-ttu-id="ff2fd-138">Iterator może wystąpić jako metoda lub `get` akcesor.</span><span class="sxs-lookup"><span data-stu-id="ff2fd-138">An iterator can occur as a method or `get` accessor.</span></span> <span data-ttu-id="ff2fd-139">Iterator nie może wystąpić w zdarzeniu, konstruktorze wystąpienia, konstruktorze statycznym lub niestatycznego finalizatora.</span><span class="sxs-lookup"><span data-stu-id="ff2fd-139">An iterator cannot occur in an event, instance constructor, static constructor, or static finalizer.</span></span>

<span data-ttu-id="ff2fd-140">Niejawna konwersja musi istnieć z typu wyrażenia w `yield return` instrukcji do argumentu Type dla elementu IEnumerable\<T > zwróconego przez iterator.</span><span class="sxs-lookup"><span data-stu-id="ff2fd-140">An implicit conversion must exist from the expression type in the `yield return` statement to the type argument for the IEnumerable\<T> returned by the iterator.</span></span>

<span data-ttu-id="ff2fd-141">W C#programie Metoda iteratora nie może mieć `in`żadnych `ref`parametrów, `out` , ani.</span><span class="sxs-lookup"><span data-stu-id="ff2fd-141">In C#, an iterator method cannot have any `in`, `ref`, or `out` parameters.</span></span>

<span data-ttu-id="ff2fd-142">W C#, "Yield" nie jest słowem zastrzeżonym i ma specjalne znaczenie tylko wtedy, gdy jest używany przed `return` słowem kluczowym or `break` .</span><span class="sxs-lookup"><span data-stu-id="ff2fd-142">In C#, "yield" is not a reserved word and has special meaning only when it is used before a `return` or `break` keyword.</span></span>

## <a name="technical-implementation"></a><span data-ttu-id="ff2fd-143">Realizacja techniczna</span><span class="sxs-lookup"><span data-stu-id="ff2fd-143">Technical Implementation</span></span>

<span data-ttu-id="ff2fd-144">Chociaż należy napisać iterator jako metodę, kompilator tłumaczy go na zagnieżdżoną klasę, która jest, w efekcie, komputera stanu.</span><span class="sxs-lookup"><span data-stu-id="ff2fd-144">Although you write an iterator as a method, the compiler translates it into a nested class that is, in effect, a state machine.</span></span> <span data-ttu-id="ff2fd-145">Ta klasa śledzi pozycję iteratora, tak długo `foreach` pętla w kodzie klienta jest kontynuowana.</span><span class="sxs-lookup"><span data-stu-id="ff2fd-145">This class keeps track of the position of the iterator as long the `foreach` loop in the client code continues.</span></span>

<span data-ttu-id="ff2fd-146">Aby zobaczyć, co robi kompilator, możesz użyć narzędzia Ildasm. exe, aby wyświetlić kod języka pośredniego firmy Microsoft, który został wygenerowany dla metody iteratora.</span><span class="sxs-lookup"><span data-stu-id="ff2fd-146">To see what the compiler does, you can use the Ildasm.exe tool to view the Microsoft intermediate language code that's generated for an iterator method.</span></span>

<span data-ttu-id="ff2fd-147">Podczas tworzenia iteratora dla [klasy](../../language-reference/keywords/class.md) lub [struktury](../../language-reference/keywords/struct.md)nie trzeba implementować całego <xref:System.Collections.IEnumerator> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="ff2fd-147">When you create an iterator for a [class](../../language-reference/keywords/class.md) or [struct](../../language-reference/keywords/struct.md), you don't have to implement the whole <xref:System.Collections.IEnumerator> interface.</span></span> <span data-ttu-id="ff2fd-148">Gdy kompilator wykryje `Current`iterator, automatycznie generuje metody <xref:System.Collections.IEnumerator> , `MoveNext`, <xref:System.Collections.Generic.IEnumerator%601> i `Dispose` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="ff2fd-148">When the compiler detects the iterator, it automatically generates the `Current`, `MoveNext`, and `Dispose` methods of the <xref:System.Collections.IEnumerator> or <xref:System.Collections.Generic.IEnumerator%601> interface.</span></span>

<span data-ttu-id="ff2fd-149">Dla każdej kolejnej iteracji `foreach` pętli (lub bezpośredniego wywołania do `IEnumerator.MoveNext`) Następna treść kodu iteratora zostanie wznowiona po poprzedniej `yield return` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="ff2fd-149">On each successive iteration of the `foreach` loop (or the direct call to `IEnumerator.MoveNext`), the next iterator code body resumes after the previous `yield return` statement.</span></span> <span data-ttu-id="ff2fd-150">Następnie przechodzi do następnej `yield return` instrukcji do momentu osiągnięcia końca treści iteratora lub `yield break` do momentu napotkania instrukcji.</span><span class="sxs-lookup"><span data-stu-id="ff2fd-150">It then continues to the next `yield return` statement until the end of the iterator body is reached, or until a `yield break` statement is encountered.</span></span>

<span data-ttu-id="ff2fd-151">Iteratory nie obsługują <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="ff2fd-151">Iterators don't support the <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="ff2fd-152">Aby wykonać ponowną iterację od początku, należy uzyskać nowy iterator.</span><span class="sxs-lookup"><span data-stu-id="ff2fd-152">To reiterate from the start, you must obtain a new iterator.</span></span> <span data-ttu-id="ff2fd-153">Wywołanie <xref:System.Collections.IEnumerator.Reset%2A> iteratora zwróconego przez metodę iteratora <xref:System.NotSupportedException>generuje.</span><span class="sxs-lookup"><span data-stu-id="ff2fd-153">Calling <xref:System.Collections.IEnumerator.Reset%2A> on the iterator returned by an iterator method throws a <xref:System.NotSupportedException>.</span></span>

<span data-ttu-id="ff2fd-154">Aby uzyskać dodatkowe informacje, zobacz [ C# Specyfikacja języka](~/_csharplang/spec/classes.md#iterators).</span><span class="sxs-lookup"><span data-stu-id="ff2fd-154">For additional information, see the [C# Language Specification](~/_csharplang/spec/classes.md#iterators).</span></span>

## <a name="use-of-iterators"></a><span data-ttu-id="ff2fd-155">Użycie iteratorów</span><span class="sxs-lookup"><span data-stu-id="ff2fd-155">Use of Iterators</span></span>

<span data-ttu-id="ff2fd-156">Iteratory umożliwiają zachowanie prostoty `foreach` pętli, gdy trzeba użyć kodu złożonego, aby wypełnić sekwencję listy.</span><span class="sxs-lookup"><span data-stu-id="ff2fd-156">Iterators enable you to maintain the simplicity of a `foreach` loop when you need to use complex code to populate a list sequence.</span></span> <span data-ttu-id="ff2fd-157">Może to być przydatne, gdy chcesz wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="ff2fd-157">This can be useful when you want to do the following:</span></span>

- <span data-ttu-id="ff2fd-158">Zmodyfikuj sekwencję list po pierwszej `foreach` iteracji pętli.</span><span class="sxs-lookup"><span data-stu-id="ff2fd-158">Modify the list sequence after the first `foreach` loop iteration.</span></span>

- <span data-ttu-id="ff2fd-159">Unikaj całkowitego ładowania dużej listy przed pierwszą iteracją `foreach` pętli.</span><span class="sxs-lookup"><span data-stu-id="ff2fd-159">Avoid fully loading a large list before the first iteration of a `foreach` loop.</span></span> <span data-ttu-id="ff2fd-160">Przykładem jest pobieranie stronicowane w celu załadowania partii wierszy tabeli.</span><span class="sxs-lookup"><span data-stu-id="ff2fd-160">An example is a paged fetch to load a batch of table rows.</span></span> <span data-ttu-id="ff2fd-161">Innym przykładem jest <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> Metoda, która implementuje Iteratory w .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ff2fd-161">Another example is the <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> method, which implements iterators within the .NET Framework.</span></span>

- <span data-ttu-id="ff2fd-162">Hermetyzuje Kompilowanie listy w iterator.</span><span class="sxs-lookup"><span data-stu-id="ff2fd-162">Encapsulate building the list in the iterator.</span></span> <span data-ttu-id="ff2fd-163">W metodzie iteratora można skompilować listę, a następnie dać każdy wynik w pętli.</span><span class="sxs-lookup"><span data-stu-id="ff2fd-163">In the iterator method, you can build the list and then yield each result in a loop.</span></span>

## <a name="see-also"></a><span data-ttu-id="ff2fd-164">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ff2fd-164">See also</span></span>

- <xref:System.Collections.Generic>
- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="ff2fd-165">foreach, in</span><span class="sxs-lookup"><span data-stu-id="ff2fd-165">foreach, in</span></span>](../../language-reference/keywords/foreach-in.md)
- [<span data-ttu-id="ff2fd-166">yield</span><span class="sxs-lookup"><span data-stu-id="ff2fd-166">yield</span></span>](../../language-reference/keywords/yield.md)
- [<span data-ttu-id="ff2fd-167">Używanie instrukcji foreach z tablicami</span><span class="sxs-lookup"><span data-stu-id="ff2fd-167">Using foreach with Arrays</span></span>](../arrays/using-foreach-with-arrays.md)
- [<span data-ttu-id="ff2fd-168">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="ff2fd-168">Generics</span></span>](../generics/index.md)

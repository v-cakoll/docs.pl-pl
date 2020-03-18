---
title: 'Iterate przez kolekcje w C #'
ms.date: 08/14/2018
ms.assetid: c93f6dd4-e72a-4a06-be1c-a98b3255b734
ms.openlocfilehash: aceedd11466c75cedad3c67224c3a5595b4cabfa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77626273"
---
# <a name="iterators-c"></a><span data-ttu-id="21329-102">Iterytory (C#)</span><span class="sxs-lookup"><span data-stu-id="21329-102">Iterators (C#)</span></span>

<span data-ttu-id="21329-103">*Iterator* może służyć do kroku kolekcji, takich jak listy i tablice.</span><span class="sxs-lookup"><span data-stu-id="21329-103">An *iterator* can be used to step through collections such as lists and arrays.</span></span>

<span data-ttu-id="21329-104">Metoda iterator `get` lub akcesor wykonuje niestandardowe iteracji za pomocą kolekcji.</span><span class="sxs-lookup"><span data-stu-id="21329-104">An iterator method or `get` accessor performs a custom iteration over a collection.</span></span> <span data-ttu-id="21329-105">Metoda iterator używa [yield return](../../language-reference/keywords/yield.md) instrukcji do zwrócenia każdego elementu po jednym na raz.</span><span class="sxs-lookup"><span data-stu-id="21329-105">An iterator method uses the [yield return](../../language-reference/keywords/yield.md) statement to return each element one at a time.</span></span> <span data-ttu-id="21329-106">Po `yield return` osiągnięciu instrukcji zostanie zapamiętana bieżąca lokalizacja w kodzie.</span><span class="sxs-lookup"><span data-stu-id="21329-106">When a `yield return` statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="21329-107">Wykonywanie jest uruchamiane ponownie z tej lokalizacji przy następnym wywołaniu funkcji sterująca.</span><span class="sxs-lookup"><span data-stu-id="21329-107">Execution is restarted from that location the next time the iterator function is called.</span></span>

<span data-ttu-id="21329-108">Użyj iterator z kodu klienta przy użyciu [foreach](../../language-reference/keywords/foreach-in.md) instrukcji lub przy użyciu kwerendy LINQ.</span><span class="sxs-lookup"><span data-stu-id="21329-108">You consume an iterator from client code by using a [foreach](../../language-reference/keywords/foreach-in.md) statement or by using a LINQ query.</span></span>

<span data-ttu-id="21329-109">W poniższym przykładzie pierwsza iteracja `foreach` pętli powoduje wykonanie, `SomeNumbers` aby kontynuować w metodzie iteratorem, aż do osiągnięcia pierwszej `yield return` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="21329-109">In the following example, the first iteration of the `foreach` loop causes execution to proceed in the `SomeNumbers` iterator method until the first `yield return` statement is reached.</span></span> <span data-ttu-id="21329-110">Ta iteracja zwraca wartość 3, a bieżąca lokalizacja w metodzie iteratorem jest zachowywana.</span><span class="sxs-lookup"><span data-stu-id="21329-110">This iteration returns a value of 3, and the current location in the iterator method is retained.</span></span> <span data-ttu-id="21329-111">W następnej iteracji pętli wykonanie w metodzie iteratorem jest kontynuowane od miejsca, `yield return` w którym zostało wyłączone, ponownie zatrzymując się po osiągnięciu instrukcji.</span><span class="sxs-lookup"><span data-stu-id="21329-111">On the next iteration of the loop, execution in the iterator method continues from where it left off, again stopping when it reaches a `yield return` statement.</span></span> <span data-ttu-id="21329-112">Ta iteracja zwraca wartość 5, a bieżąca lokalizacja w metodzie iteratorem jest ponownie zachowywana.</span><span class="sxs-lookup"><span data-stu-id="21329-112">This iteration returns a value of 5, and the current location in the iterator method is again retained.</span></span> <span data-ttu-id="21329-113">Pętla kończy się po osiągnięciu końca metody iterator.</span><span class="sxs-lookup"><span data-stu-id="21329-113">The loop completes when the end of the iterator method is reached.</span></span>

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

<span data-ttu-id="21329-114">Zwracany typ metody iteratorego `get` lub <xref:System.Collections.IEnumerable>akcesora może być , <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, lub <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="21329-114">The return type of an iterator method or `get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>

<span data-ttu-id="21329-115">Można użyć `yield break` instrukcji, aby zakończyć iterację.</span><span class="sxs-lookup"><span data-stu-id="21329-115">You can use a `yield break` statement to end the iteration.</span></span>

> [!NOTE]
> <span data-ttu-id="21329-116">Dla wszystkich przykładów w tym temacie z wyjątkiem prostego iterator przykład, obejmują [przy użyciu](../../language-reference/keywords/using-directive.md) dyrektyw dla `System.Collections` i `System.Collections.Generic` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="21329-116">For all examples in this topic except the Simple Iterator example, include [using](../../language-reference/keywords/using-directive.md) directives for the `System.Collections` and `System.Collections.Generic` namespaces.</span></span>

## <a name="simple-iterator"></a><span data-ttu-id="21329-117">Prosty iterator</span><span class="sxs-lookup"><span data-stu-id="21329-117">Simple Iterator</span></span>

<span data-ttu-id="21329-118">Poniższy przykład ma `yield return` jedną instrukcję, która znajduje się wewnątrz [for](../../language-reference/keywords/for.md) pętli.</span><span class="sxs-lookup"><span data-stu-id="21329-118">The following example has a single `yield return` statement that is inside a [for](../../language-reference/keywords/for.md) loop.</span></span> <span data-ttu-id="21329-119">W `Main`, każda iteracja treści `foreach` instrukcji tworzy wywołanie funkcji iterator, `yield return` która przechodzi do następnej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="21329-119">In `Main`, each iteration of the `foreach` statement body creates a call to the iterator function, which proceeds to the next `yield return` statement.</span></span>

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

## <a name="creating-a-collection-class"></a><span data-ttu-id="21329-120">Tworzenie klasy kolekcji</span><span class="sxs-lookup"><span data-stu-id="21329-120">Creating a Collection Class</span></span>

<span data-ttu-id="21329-121">W poniższym `DaysOfTheWeek` przykładzie klasa implementuje <xref:System.Collections.IEnumerable> interfejs, <xref:System.Collections.IEnumerable.GetEnumerator%2A> który wymaga metody.</span><span class="sxs-lookup"><span data-stu-id="21329-121">In the following example, the `DaysOfTheWeek` class implements the <xref:System.Collections.IEnumerable> interface, which requires a <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span> <span data-ttu-id="21329-122">Kompilator niejawnie wywołuje `GetEnumerator` metodę, która zwraca . <xref:System.Collections.IEnumerator></span><span class="sxs-lookup"><span data-stu-id="21329-122">The compiler implicitly calls the `GetEnumerator` method, which returns an <xref:System.Collections.IEnumerator>.</span></span>

<span data-ttu-id="21329-123">Metoda `GetEnumerator` zwraca każdy ciąg jeden na `yield return` raz przy użyciu instrukcji.</span><span class="sxs-lookup"><span data-stu-id="21329-123">The `GetEnumerator` method returns each string one at a time by using the `yield return` statement.</span></span>

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

<span data-ttu-id="21329-124">Poniższy przykład tworzy `Zoo` klasę, która zawiera kolekcję zwierząt.</span><span class="sxs-lookup"><span data-stu-id="21329-124">The following example creates a `Zoo` class that contains a collection of animals.</span></span>

<span data-ttu-id="21329-125">Instrukcja, `foreach` która odwołuje się`theZoo`do wystąpienia klasy `GetEnumerator` ( ) niejawnie wywołuje metodę.</span><span class="sxs-lookup"><span data-stu-id="21329-125">The `foreach` statement that refers to the class instance (`theZoo`) implicitly calls the `GetEnumerator` method.</span></span> <span data-ttu-id="21329-126">Instrukcje, `foreach` które odwołują `Birds` się do i `Mammals` właściwości użyć `AnimalsForType` metody o nazwie iterator.</span><span class="sxs-lookup"><span data-stu-id="21329-126">The `foreach` statements that refer to the `Birds` and `Mammals` properties use the `AnimalsForType` named iterator method.</span></span>

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

## <a name="using-iterators-with-a-generic-list"></a><span data-ttu-id="21329-127">Korzystanie z iteratorów z listą ogólną</span><span class="sxs-lookup"><span data-stu-id="21329-127">Using Iterators with a Generic List</span></span>

<span data-ttu-id="21329-128">W poniższym przykładzie <xref:System.Collections.Generic.Stack%601> klasy ogólnej <xref:System.Collections.Generic.IEnumerable%601> implementuje interfejs ogólny.</span><span class="sxs-lookup"><span data-stu-id="21329-128">In the following example, the <xref:System.Collections.Generic.Stack%601> generic class implements the <xref:System.Collections.Generic.IEnumerable%601> generic interface.</span></span> <span data-ttu-id="21329-129">Metoda <xref:System.Collections.Generic.Stack%601.Push%2A> przypisuje wartości do tablicy `T`typu .</span><span class="sxs-lookup"><span data-stu-id="21329-129">The <xref:System.Collections.Generic.Stack%601.Push%2A> method assigns values to an array of type `T`.</span></span> <span data-ttu-id="21329-130">Metoda <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> zwraca wartości tablicy `yield return` przy użyciu instrukcji.</span><span class="sxs-lookup"><span data-stu-id="21329-130">The <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method returns the array values by using the `yield return` statement.</span></span>

<span data-ttu-id="21329-131">Oprócz metody ogólnej <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> należy również <xref:System.Collections.IEnumerable.GetEnumerator%2A> wdrożyć metodę nierodzajową.</span><span class="sxs-lookup"><span data-stu-id="21329-131">In addition to the generic <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method, the non-generic <xref:System.Collections.IEnumerable.GetEnumerator%2A> method must also be implemented.</span></span> <span data-ttu-id="21329-132">Dzieje się <xref:System.Collections.Generic.IEnumerable%601> tak, <xref:System.Collections.IEnumerable>ponieważ dziedziczy z .</span><span class="sxs-lookup"><span data-stu-id="21329-132">This is because <xref:System.Collections.Generic.IEnumerable%601> inherits from <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="21329-133">Implementacja nierodzajowa odracza implementację ogólne.</span><span class="sxs-lookup"><span data-stu-id="21329-133">The non-generic implementation defers to the generic implementation.</span></span>

<span data-ttu-id="21329-134">W przykładzie używa nazwanych iteratorów do obsługi różnych sposobów iteracji za pośrednictwem tego samego zbierania danych.</span><span class="sxs-lookup"><span data-stu-id="21329-134">The example uses named iterators to support various ways of iterating through the same collection of data.</span></span> <span data-ttu-id="21329-135">Te nazwane iteratory są `TopToBottom` `BottomToTop` i właściwości i `TopN` metody.</span><span class="sxs-lookup"><span data-stu-id="21329-135">These named iterators are the `TopToBottom` and `BottomToTop` properties, and the `TopN` method.</span></span>

<span data-ttu-id="21329-136">Właściwość `BottomToTop` używa iteratorem `get` w akcesorze.</span><span class="sxs-lookup"><span data-stu-id="21329-136">The `BottomToTop` property uses an iterator in a `get` accessor.</span></span>

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

## <a name="syntax-information"></a><span data-ttu-id="21329-137">Informacje składni</span><span class="sxs-lookup"><span data-stu-id="21329-137">Syntax Information</span></span>

<span data-ttu-id="21329-138">Iterator może wystąpić jako `get` metoda lub akcesor.</span><span class="sxs-lookup"><span data-stu-id="21329-138">An iterator can occur as a method or `get` accessor.</span></span> <span data-ttu-id="21329-139">Iteratora nie może wystąpić w przypadku, konstruktora wystąpienia, konstruktora statycznego lub statycznego finalizatora.</span><span class="sxs-lookup"><span data-stu-id="21329-139">An iterator cannot occur in an event, instance constructor, static constructor, or static finalizer.</span></span>

<span data-ttu-id="21329-140">Konwersja niejawna musi istnieć `yield return` od typu wyrażenia `IEnumerable<T>` w instrukcji do argumentu typu dla zwracanego przez iterator.</span><span class="sxs-lookup"><span data-stu-id="21329-140">An implicit conversion must exist from the expression type in the `yield return` statement to the type argument for the `IEnumerable<T>` returned by the iterator.</span></span>

<span data-ttu-id="21329-141">W języku C#, metoda iterator nie może mieć żadnych `in`, `ref`lub `out` parametry.</span><span class="sxs-lookup"><span data-stu-id="21329-141">In C#, an iterator method cannot have any `in`, `ref`, or `out` parameters.</span></span>

<span data-ttu-id="21329-142">W języku `yield` C#, nie jest słowem zastrzeżonym `return` i `break` ma specjalne znaczenie tylko wtedy, gdy jest używany przed lub słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="21329-142">In C#, `yield` is not a reserved word and has special meaning only when it is used before a `return` or `break` keyword.</span></span>

## <a name="technical-implementation"></a><span data-ttu-id="21329-143">Realizacja techniczna</span><span class="sxs-lookup"><span data-stu-id="21329-143">Technical Implementation</span></span>

<span data-ttu-id="21329-144">Mimo że piszesz sterujące jako metodę, kompilator tłumaczy go na zagnieżdżoną klasę, która jest w rzeczywistości maszyną stanu.</span><span class="sxs-lookup"><span data-stu-id="21329-144">Although you write an iterator as a method, the compiler translates it into a nested class that is, in effect, a state machine.</span></span> <span data-ttu-id="21329-145">Ta klasa śledzi położenie iterator tak długo, jak pętla `foreach` w kodzie klienta trwa.</span><span class="sxs-lookup"><span data-stu-id="21329-145">This class keeps track of the position of the iterator as long the `foreach` loop in the client code continues.</span></span>

<span data-ttu-id="21329-146">Aby zobaczyć, co robi kompilator, można użyć narzędzia Ildasm.exe, aby wyświetlić kod języka pośredniego firmy Microsoft, który jest generowany dla metody iteratora.</span><span class="sxs-lookup"><span data-stu-id="21329-146">To see what the compiler does, you can use the Ildasm.exe tool to view the Microsoft intermediate language code that's generated for an iterator method.</span></span>

<span data-ttu-id="21329-147">Podczas tworzenia iteratora dla [klasy](../../language-reference/keywords/class.md) lub [struktury](../../language-reference/builtin-types/struct.md)nie trzeba implementować <xref:System.Collections.IEnumerator> całego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="21329-147">When you create an iterator for a [class](../../language-reference/keywords/class.md) or [struct](../../language-reference/builtin-types/struct.md), you don't have to implement the whole <xref:System.Collections.IEnumerator> interface.</span></span> <span data-ttu-id="21329-148">Gdy kompilator wykryje iterator, automatycznie `Current`generuje `MoveNext`, `Dispose` i metody <xref:System.Collections.IEnumerator> <xref:System.Collections.Generic.IEnumerator%601> lub interfejsu.</span><span class="sxs-lookup"><span data-stu-id="21329-148">When the compiler detects the iterator, it automatically generates the `Current`, `MoveNext`, and `Dispose` methods of the <xref:System.Collections.IEnumerator> or <xref:System.Collections.Generic.IEnumerator%601> interface.</span></span>

<span data-ttu-id="21329-149">Przy każdej kolejnej `foreach` iteracji pętli (lub `IEnumerator.MoveNext`bezpośredniego wywołania ), następna treść `yield return` kodu iteratora zostanie wznowiona po poprzedniej instrukcji.</span><span class="sxs-lookup"><span data-stu-id="21329-149">On each successive iteration of the `foreach` loop (or the direct call to `IEnumerator.MoveNext`), the next iterator code body resumes after the previous `yield return` statement.</span></span> <span data-ttu-id="21329-150">Następnie kontynuuje do `yield return` następnej instrukcji do końca treści iteratości zostanie `yield break` osiągnięty lub do momentu napotkania instrukcji.</span><span class="sxs-lookup"><span data-stu-id="21329-150">It then continues to the next `yield return` statement until the end of the iterator body is reached, or until a `yield break` statement is encountered.</span></span>

<span data-ttu-id="21329-151">Iteratory nie obsługują <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="21329-151">Iterators don't support the <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="21329-152">Aby powtórzyć od samego początku, należy uzyskać nowy iterator.</span><span class="sxs-lookup"><span data-stu-id="21329-152">To reiterate from the start, you must obtain a new iterator.</span></span> <span data-ttu-id="21329-153">Wywołanie <xref:System.Collections.IEnumerator.Reset%2A> iterator zwrócony metodą iteratorem <xref:System.NotSupportedException>wyrzuca .</span><span class="sxs-lookup"><span data-stu-id="21329-153">Calling <xref:System.Collections.IEnumerator.Reset%2A> on the iterator returned by an iterator method throws a <xref:System.NotSupportedException>.</span></span>

<span data-ttu-id="21329-154">For additional information, see the [C# Language Specification](~/_csharplang/spec/classes.md#iterators).</span><span class="sxs-lookup"><span data-stu-id="21329-154">For additional information, see the [C# Language Specification](~/_csharplang/spec/classes.md#iterators).</span></span>

## <a name="use-of-iterators"></a><span data-ttu-id="21329-155">Korzystanie z iteratorów</span><span class="sxs-lookup"><span data-stu-id="21329-155">Use of Iterators</span></span>

<span data-ttu-id="21329-156">Iteratory umożliwiają zachowanie prostoty `foreach` pętli, gdy trzeba użyć złożonego kodu do wypełnienia sekwencji listy.</span><span class="sxs-lookup"><span data-stu-id="21329-156">Iterators enable you to maintain the simplicity of a `foreach` loop when you need to use complex code to populate a list sequence.</span></span> <span data-ttu-id="21329-157">Może to być przydatne, gdy chcesz wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="21329-157">This can be useful when you want to do the following:</span></span>

- <span data-ttu-id="21329-158">Zmodyfikuj sekwencję listy po pierwszej `foreach` iteracji pętli.</span><span class="sxs-lookup"><span data-stu-id="21329-158">Modify the list sequence after the first `foreach` loop iteration.</span></span>

- <span data-ttu-id="21329-159">Należy unikać pełnego ładowania dużej listy przed `foreach` pierwszą iteracją pętli.</span><span class="sxs-lookup"><span data-stu-id="21329-159">Avoid fully loading a large list before the first iteration of a `foreach` loop.</span></span> <span data-ttu-id="21329-160">Przykładem jest stronicowane pobieranie, aby załadować partię wierszy tabeli.</span><span class="sxs-lookup"><span data-stu-id="21329-160">An example is a paged fetch to load a batch of table rows.</span></span> <span data-ttu-id="21329-161">Innym przykładem <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> jest metoda, która implementuje iteratory w ramach .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="21329-161">Another example is the <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> method, which implements iterators within the .NET Framework.</span></span>

- <span data-ttu-id="21329-162">Hermetyzować tworzenie listy w iteratorze.</span><span class="sxs-lookup"><span data-stu-id="21329-162">Encapsulate building the list in the iterator.</span></span> <span data-ttu-id="21329-163">W metodzie iteratora można utworzyć listę, a następnie przynieść każdy wynik w pętli.</span><span class="sxs-lookup"><span data-stu-id="21329-163">In the iterator method, you can build the list and then yield each result in a loop.</span></span>

## <a name="see-also"></a><span data-ttu-id="21329-164">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="21329-164">See also</span></span>

- <xref:System.Collections.Generic>
- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="21329-165">foreach, in</span><span class="sxs-lookup"><span data-stu-id="21329-165">foreach, in</span></span>](../../language-reference/keywords/foreach-in.md)
- [<span data-ttu-id="21329-166">yield</span><span class="sxs-lookup"><span data-stu-id="21329-166">yield</span></span>](../../language-reference/keywords/yield.md)
- [<span data-ttu-id="21329-167">Używanie instrukcji foreach z tablicami</span><span class="sxs-lookup"><span data-stu-id="21329-167">Using foreach with Arrays</span></span>](../arrays/using-foreach-with-arrays.md)
- [<span data-ttu-id="21329-168">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="21329-168">Generics</span></span>](../generics/index.md)

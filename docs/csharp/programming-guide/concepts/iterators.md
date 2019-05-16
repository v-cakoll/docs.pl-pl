---
title: Iterowania przez kolekcje w języku C#
ms.date: 08/14/2018
ms.assetid: c93f6dd4-e72a-4a06-be1c-a98b3255b734
ms.openlocfilehash: 931f0662b71b4dd99ac4a419c279be5058c61e92
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65635517"
---
# <a name="iterators-c"></a><span data-ttu-id="acf5e-102">Iteratory (C#)</span><span class="sxs-lookup"><span data-stu-id="acf5e-102">Iterators (C#)</span></span>

<span data-ttu-id="acf5e-103">*Iteratora* może służyć do kroku za pomocą kolekcji, takie jak listy i tablic.</span><span class="sxs-lookup"><span data-stu-id="acf5e-103">An *iterator* can be used to step through collections such as lists and arrays.</span></span>

<span data-ttu-id="acf5e-104">Metody iteratora lub `get` akcesor wykonuje niestandardowych iteracji przez kolekcję.</span><span class="sxs-lookup"><span data-stu-id="acf5e-104">An iterator method or `get` accessor performs a custom iteration over a collection.</span></span> <span data-ttu-id="acf5e-105">Wykorzystuje metodę iteratora [yield return](../../../csharp/language-reference/keywords/yield.md) instrukcja zwraca każdy element w danym momencie.</span><span class="sxs-lookup"><span data-stu-id="acf5e-105">An iterator method uses the [yield return](../../../csharp/language-reference/keywords/yield.md) statement to return each element one at a time.</span></span> <span data-ttu-id="acf5e-106">Gdy `yield return` osiągnięciu instrukcji zapamiętanych bieżąca lokalizacja w kodzie.</span><span class="sxs-lookup"><span data-stu-id="acf5e-106">When a `yield return` statement is reached, the current location in code is remembered.</span></span> <span data-ttu-id="acf5e-107">Wykonanie jest uruchamiane ponownie z tej lokalizacji w następnym razem, gdy zostanie wywołana funkcja iteratora.</span><span class="sxs-lookup"><span data-stu-id="acf5e-107">Execution is restarted from that location the next time the iterator function is called.</span></span>

<span data-ttu-id="acf5e-108">Korzystać z iteratora, z poziomu kodu klienta za pomocą [foreach](../../../csharp/language-reference/keywords/foreach-in.md) instrukcji lub za pomocą zapytań LINQ.</span><span class="sxs-lookup"><span data-stu-id="acf5e-108">You consume an iterator from client code by using a [foreach](../../../csharp/language-reference/keywords/foreach-in.md) statement or by using a LINQ query.</span></span>

<span data-ttu-id="acf5e-109">W poniższym przykładzie pierwszej iteracji `foreach` pętli powoduje wykonanie przejść w `SomeNumbers` metody iteratora, do momentu pierwszego `yield return` osiągnięta zostanie instrukcja.</span><span class="sxs-lookup"><span data-stu-id="acf5e-109">In the following example, the first iteration of the `foreach` loop causes execution to proceed in the `SomeNumbers` iterator method until the first `yield return` statement is reached.</span></span> <span data-ttu-id="acf5e-110">Tej iteracji zwraca wartość 3, a bieżąca lokalizacja w metodzie iteratora jest zachowywana.</span><span class="sxs-lookup"><span data-stu-id="acf5e-110">This iteration returns a value of 3, and the current location in the iterator method is retained.</span></span> <span data-ttu-id="acf5e-111">Na następnej iteracji pętli wykonywania w metodzie iteratora jest kontynuowane od miejsca zostało przerwane, zatrzymywane ponownie po osiągnięciu `yield return` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="acf5e-111">On the next iteration of the loop, execution in the iterator method continues from where it left off, again stopping when it reaches a `yield return` statement.</span></span> <span data-ttu-id="acf5e-112">Tej iteracji zwraca wartość 5, a bieżąca lokalizacja w metodzie iteratora ponownie jest zachowywana.</span><span class="sxs-lookup"><span data-stu-id="acf5e-112">This iteration returns a value of 5, and the current location in the iterator method is again retained.</span></span> <span data-ttu-id="acf5e-113">Pętla zostanie ukończone, gdy zostanie osiągnięty koniec metody iteratora.</span><span class="sxs-lookup"><span data-stu-id="acf5e-113">The loop completes when the end of the iterator method is reached.</span></span>

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

<span data-ttu-id="acf5e-114">Zwracany typ metody iteratora lub `get` dostępu mogą być <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, lub <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="acf5e-114">The return type of an iterator method or `get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>

<span data-ttu-id="acf5e-115">Możesz użyć `yield break` instrukcję, aby zakończyć iterację.</span><span class="sxs-lookup"><span data-stu-id="acf5e-115">You can use a `yield break` statement to end the iteration.</span></span>

> [!NOTE]
> <span data-ttu-id="acf5e-116">Wszystkie przykłady w tym temacie, chyba że w przykładzie prostego iteratora, obejmują [przy użyciu](../../../csharp/language-reference/keywords/using-directive.md) dyrektywy dla `System.Collections` i `System.Collections.Generic` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="acf5e-116">For all examples in this topic except the Simple Iterator example, include [using](../../../csharp/language-reference/keywords/using-directive.md) directives for the `System.Collections` and `System.Collections.Generic` namespaces.</span></span>

## <a name="simple-iterator"></a><span data-ttu-id="acf5e-117">Prostego iteratora</span><span class="sxs-lookup"><span data-stu-id="acf5e-117">Simple Iterator</span></span>

<span data-ttu-id="acf5e-118">W poniższym przykładzie przedstawiono jeden `yield return` instrukcji, która znajduje się wewnątrz [dla](../../../csharp/language-reference/keywords/for.md) pętli.</span><span class="sxs-lookup"><span data-stu-id="acf5e-118">The following example has a single `yield return` statement that is inside a [for](../../../csharp/language-reference/keywords/for.md) loop.</span></span> <span data-ttu-id="acf5e-119">W `Main`, każda iteracja `foreach` treść instrukcji tworzy wywołanie funkcji iteratora, który przechodzi do następnej `yield return` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="acf5e-119">In `Main`, each iteration of the `foreach` statement body creates a call to the iterator function, which proceeds to the next `yield return` statement.</span></span>

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

## <a name="creating-a-collection-class"></a><span data-ttu-id="acf5e-120">Tworzenie klasy kolekcji</span><span class="sxs-lookup"><span data-stu-id="acf5e-120">Creating a Collection Class</span></span>

<span data-ttu-id="acf5e-121">W poniższym przykładzie `DaysOfTheWeek` klasy implementuje <xref:System.Collections.IEnumerable> interfejs, który wymaga <xref:System.Collections.IEnumerable.GetEnumerator%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="acf5e-121">In the following example, the `DaysOfTheWeek` class implements the <xref:System.Collections.IEnumerable> interface, which requires a <xref:System.Collections.IEnumerable.GetEnumerator%2A> method.</span></span> <span data-ttu-id="acf5e-122">Kompilator niejawnie wywołuje `GetEnumerator` metody, która zwraca <xref:System.Collections.IEnumerator>.</span><span class="sxs-lookup"><span data-stu-id="acf5e-122">The compiler implicitly calls the `GetEnumerator` method, which returns an <xref:System.Collections.IEnumerator>.</span></span>

<span data-ttu-id="acf5e-123">`GetEnumerator` Metoda zwraca każdego ciągu, jeden w czasie za pomocą `yield return` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="acf5e-123">The `GetEnumerator` method returns each string one at a time by using the `yield return` statement.</span></span>

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

<span data-ttu-id="acf5e-124">Poniższy przykład tworzy `Zoo` klasę, która zawiera kolekcję zwierząt.</span><span class="sxs-lookup"><span data-stu-id="acf5e-124">The following example creates a `Zoo` class that contains a collection of animals.</span></span>

<span data-ttu-id="acf5e-125">`foreach` Instrukcję, która odnosi się do wystąpienia klasy (`theZoo`) wywołuje niejawnie `GetEnumerator` metody.</span><span class="sxs-lookup"><span data-stu-id="acf5e-125">The `foreach` statement that refers to the class instance (`theZoo`) implicitly calls the `GetEnumerator` method.</span></span> <span data-ttu-id="acf5e-126">`foreach` Instrukcji odwołujących się do `Birds` i `Mammals` Użyj właściwości `AnimalsForType` o nazwie metody iteratora.</span><span class="sxs-lookup"><span data-stu-id="acf5e-126">The `foreach` statements that refer to the `Birds` and `Mammals` properties use the `AnimalsForType` named iterator method.</span></span>

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

## <a name="using-iterators-with-a-generic-list"></a><span data-ttu-id="acf5e-127">Iteratory przy użyciu listy ogólnej</span><span class="sxs-lookup"><span data-stu-id="acf5e-127">Using Iterators with a Generic List</span></span>

<span data-ttu-id="acf5e-128">W poniższym przykładzie <xref:System.Collections.Generic.Stack%601> implementuje klasy ogólnej <xref:System.Collections.Generic.IEnumerable%601> interfejs generyczny.</span><span class="sxs-lookup"><span data-stu-id="acf5e-128">In the following example, the <xref:System.Collections.Generic.Stack%601> generic class implements the <xref:System.Collections.Generic.IEnumerable%601> generic interface.</span></span> <span data-ttu-id="acf5e-129"><xref:System.Collections.Generic.Stack%601.Push%2A> Metoda przypisuje wartości do tablicy typu `T`.</span><span class="sxs-lookup"><span data-stu-id="acf5e-129">The <xref:System.Collections.Generic.Stack%601.Push%2A> method assigns values to an array of type `T`.</span></span> <span data-ttu-id="acf5e-130"><xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> Metoda zwraca wartości tablicy przy użyciu `yield return` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="acf5e-130">The <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method returns the array values by using the `yield return` statement.</span></span>

<span data-ttu-id="acf5e-131">Oprócz ogólnego <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> metody, inną niż ogólna <xref:System.Collections.IEnumerable.GetEnumerator%2A> metoda również musi być implementowana.</span><span class="sxs-lookup"><span data-stu-id="acf5e-131">In addition to the generic <xref:System.Collections.Generic.IEnumerable%601.GetEnumerator%2A> method, the non-generic <xref:System.Collections.IEnumerable.GetEnumerator%2A> method must also be implemented.</span></span> <span data-ttu-id="acf5e-132">Jest to spowodowane <xref:System.Collections.Generic.IEnumerable%601> dziedziczy <xref:System.Collections.IEnumerable>.</span><span class="sxs-lookup"><span data-stu-id="acf5e-132">This is because <xref:System.Collections.Generic.IEnumerable%601> inherits from <xref:System.Collections.IEnumerable>.</span></span> <span data-ttu-id="acf5e-133">Implementacja nieogólnego różni się ogólną implementację.</span><span class="sxs-lookup"><span data-stu-id="acf5e-133">The non-generic implementation defers to the generic implementation.</span></span>

<span data-ttu-id="acf5e-134">W przykładzie użyto nazwanego Iteratory do obsługi różnych sposobów iteracji w tej samej kolekcji danych.</span><span class="sxs-lookup"><span data-stu-id="acf5e-134">The example uses named iterators to support various ways of iterating through the same collection of data.</span></span> <span data-ttu-id="acf5e-135">O nazwie Iteratory są `TopToBottom` i `BottomToTop` właściwości, a `TopN` metody.</span><span class="sxs-lookup"><span data-stu-id="acf5e-135">These named iterators are the `TopToBottom` and `BottomToTop` properties, and the `TopN` method.</span></span>

<span data-ttu-id="acf5e-136">`BottomToTop` Właściwość używa iteratora w `get` metody dostępu.</span><span class="sxs-lookup"><span data-stu-id="acf5e-136">The `BottomToTop` property uses an iterator in a `get` accessor.</span></span>

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

## <a name="syntax-information"></a><span data-ttu-id="acf5e-137">Informacje o składni</span><span class="sxs-lookup"><span data-stu-id="acf5e-137">Syntax Information</span></span>

<span data-ttu-id="acf5e-138">Iterator może wystąpić jako metodę lub `get` metody dostępu.</span><span class="sxs-lookup"><span data-stu-id="acf5e-138">An iterator can occur as a method or `get` accessor.</span></span> <span data-ttu-id="acf5e-139">Iterator nie może wystąpić w zdarzeń, konstruktora wystąpienia, statyczny Konstruktor lub finalizatora statyczne.</span><span class="sxs-lookup"><span data-stu-id="acf5e-139">An iterator cannot occur in an event, instance constructor, static constructor, or static finalizer.</span></span>

<span data-ttu-id="acf5e-140">Typ wyrażenia w musi istnieć niejawna konwersja `yield return` instrukcję, aby typ argumentu dla IEnumerable\<T > zwrócony przez iterator.</span><span class="sxs-lookup"><span data-stu-id="acf5e-140">An implicit conversion must exist from the expression type in the `yield return` statement to the type argument for the IEnumerable\<T> returned by the iterator.</span></span>

<span data-ttu-id="acf5e-141">W języku C#, metoda iteratora jest nie może zawierać żadnych `in`, `ref`, lub `out` parametrów.</span><span class="sxs-lookup"><span data-stu-id="acf5e-141">In C#, an iterator method cannot have any `in`, `ref`, or `out` parameters.</span></span>

<span data-ttu-id="acf5e-142">W języku C# "yield" nie jest słowem zastrzeżonym i ma specjalne znaczenie tylko wtedy, gdy jest używana przed `return` lub `break` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="acf5e-142">In C#, "yield" is not a reserved word and has special meaning only when it is used before a `return` or `break` keyword.</span></span>

## <a name="technical-implementation"></a><span data-ttu-id="acf5e-143">Realizacja techniczna</span><span class="sxs-lookup"><span data-stu-id="acf5e-143">Technical Implementation</span></span>

<span data-ttu-id="acf5e-144">Mimo, że piszesz iteratora jako metodę, kompilator tłumaczy je na klasę zagnieżdżoną oznacza to, w efekcie automatu stanów.</span><span class="sxs-lookup"><span data-stu-id="acf5e-144">Although you write an iterator as a method, the compiler translates it into a nested class that is, in effect, a state machine.</span></span> <span data-ttu-id="acf5e-145">Ta klasa śledzi informacje o położenie iteratora, jak długo `foreach` pętli w kodzie klienta będzie kontynuowane.</span><span class="sxs-lookup"><span data-stu-id="acf5e-145">This class keeps track of the position of the iterator as long the `foreach` loop in the client code continues.</span></span>

<span data-ttu-id="acf5e-146">Aby zobaczyć, kompilator wykonuje, narzędzie Ildasm.exe służy również do wyświetlania kodu języka pośredniego firmy Microsoft, który jest generowany dla metody iteratora.</span><span class="sxs-lookup"><span data-stu-id="acf5e-146">To see what the compiler does, you can use the Ildasm.exe tool to view the Microsoft intermediate language code that's generated for an iterator method.</span></span>

<span data-ttu-id="acf5e-147">Po utworzeniu iteratora dla [klasy](../../../csharp/language-reference/keywords/class.md) lub [struktury](../../../csharp/language-reference/keywords/struct.md), nie trzeba implementować całego <xref:System.Collections.IEnumerator> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="acf5e-147">When you create an iterator for a [class](../../../csharp/language-reference/keywords/class.md) or [struct](../../../csharp/language-reference/keywords/struct.md), you don't have to implement the whole <xref:System.Collections.IEnumerator> interface.</span></span> <span data-ttu-id="acf5e-148">Gdy kompilator wykryje iteratora, automatycznie generuje `Current`, `MoveNext`, i `Dispose` metody <xref:System.Collections.IEnumerator> lub <xref:System.Collections.Generic.IEnumerator%601> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="acf5e-148">When the compiler detects the iterator, it automatically generates the `Current`, `MoveNext`, and `Dispose` methods of the <xref:System.Collections.IEnumerator> or <xref:System.Collections.Generic.IEnumerator%601> interface.</span></span>

<span data-ttu-id="acf5e-149">Na każdą kolejną iteracją z `foreach` pętli (lub bezpośrednie wywołanie `IEnumerator.MoveNext`), treść kodu następnego iteratora wznawia działanie po poprzedniej `yield return` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="acf5e-149">On each successive iteration of the `foreach` loop (or the direct call to `IEnumerator.MoveNext`), the next iterator code body resumes after the previous `yield return` statement.</span></span> <span data-ttu-id="acf5e-150">Następnie będzie kontynuowane do następnego `yield return` instrukcji, dopóki nie zostanie osiągnięty koniec treści iteratora, lub do momentu `yield break` napotkania instrukcji.</span><span class="sxs-lookup"><span data-stu-id="acf5e-150">It then continues to the next `yield return` statement until the end of the iterator body is reached, or until a `yield break` statement is encountered.</span></span>

<span data-ttu-id="acf5e-151">Iteratory nie obsługują <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="acf5e-151">Iterators don't support the <xref:System.Collections.IEnumerator.Reset%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="acf5e-152">Przypomnę od samego początku, należy pobrać nowe iteratora.</span><span class="sxs-lookup"><span data-stu-id="acf5e-152">To reiterate from the start, you must obtain a new iterator.</span></span> <span data-ttu-id="acf5e-153">Wywoływanie <xref:System.Collections.IEnumerator.Reset%2A> na zwracany przez metodę iteratora iterator zgłasza <xref:System.NotSupportedException>.</span><span class="sxs-lookup"><span data-stu-id="acf5e-153">Calling <xref:System.Collections.IEnumerator.Reset%2A> on the iterator returned by an iterator method throws a <xref:System.NotSupportedException>.</span></span>

<span data-ttu-id="acf5e-154">Aby uzyskać więcej informacji, zobacz [specyfikacji języka C#](~/_csharplang/spec/classes.md#iterators).</span><span class="sxs-lookup"><span data-stu-id="acf5e-154">For additional information, see the [C# Language Specification](~/_csharplang/spec/classes.md#iterators).</span></span>

## <a name="use-of-iterators"></a><span data-ttu-id="acf5e-155">Użyj Iteratory</span><span class="sxs-lookup"><span data-stu-id="acf5e-155">Use of Iterators</span></span>

<span data-ttu-id="acf5e-156">Iteratory pozwalają zachować prostotę `foreach` pętli, gdy trzeba użyć złożonego kodu do wypełniania kolejność listy.</span><span class="sxs-lookup"><span data-stu-id="acf5e-156">Iterators enable you to maintain the simplicity of a `foreach` loop when you need to use complex code to populate a list sequence.</span></span> <span data-ttu-id="acf5e-157">Może to być przydatne, gdy chcesz wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="acf5e-157">This can be useful when you want to do the following:</span></span>

- <span data-ttu-id="acf5e-158">Zmodyfikuj listę sekwencji po pierwszym `foreach` iteracji w pętli.</span><span class="sxs-lookup"><span data-stu-id="acf5e-158">Modify the list sequence after the first `foreach` loop iteration.</span></span>

- <span data-ttu-id="acf5e-159">Nie pełni ładował dużej listy przed pierwszą iteracją z `foreach` pętli.</span><span class="sxs-lookup"><span data-stu-id="acf5e-159">Avoid fully loading a large list before the first iteration of a `foreach` loop.</span></span> <span data-ttu-id="acf5e-160">Przykładem jest stronicowane pobierania załadować partii wierszy tabeli.</span><span class="sxs-lookup"><span data-stu-id="acf5e-160">An example is a paged fetch to load a batch of table rows.</span></span> <span data-ttu-id="acf5e-161">Innym przykładem jest <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> metody, która implementuje Iteratory w ramach programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="acf5e-161">Another example is the <xref:System.IO.DirectoryInfo.EnumerateFiles%2A> method, which implements iterators within the .NET Framework.</span></span>

- <span data-ttu-id="acf5e-162">Hermetyzuj, tworzenie listy dla iteratorów.</span><span class="sxs-lookup"><span data-stu-id="acf5e-162">Encapsulate building the list in the iterator.</span></span> <span data-ttu-id="acf5e-163">W metodzie iteratora można tworzyć listy i następnie uzyskanie każdy wynik w pętli.</span><span class="sxs-lookup"><span data-stu-id="acf5e-163">In the iterator method, you can build the list and then yield each result in a loop.</span></span>

## <a name="see-also"></a><span data-ttu-id="acf5e-164">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="acf5e-164">See also</span></span>

- <xref:System.Collections.Generic>
- <xref:System.Collections.Generic.IEnumerable%601>
- [<span data-ttu-id="acf5e-165">foreach, in</span><span class="sxs-lookup"><span data-stu-id="acf5e-165">foreach, in</span></span>](../../../csharp/language-reference/keywords/foreach-in.md)
- [<span data-ttu-id="acf5e-166">yield</span><span class="sxs-lookup"><span data-stu-id="acf5e-166">yield</span></span>](../../../csharp/language-reference/keywords/yield.md)
- [<span data-ttu-id="acf5e-167">Używanie instrukcji foreach z tablicami</span><span class="sxs-lookup"><span data-stu-id="acf5e-167">Using foreach with Arrays</span></span>](../../../csharp/programming-guide/arrays/using-foreach-with-arrays.md)
- [<span data-ttu-id="acf5e-168">Typy ogólne</span><span class="sxs-lookup"><span data-stu-id="acf5e-168">Generics</span></span>](../../../csharp/programming-guide/generics/index.md)

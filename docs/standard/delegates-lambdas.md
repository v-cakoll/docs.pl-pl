---
title: Delegaci i wyrażenia lambda
description: Dowiedz się, jak Delegaty definiują typ, który określa określoną sygnaturę metody, która może być wywoływana bezpośrednio lub przekazywać do innej metody i wywoływana.
author: richlander
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: fe2e4b4c-6483-4106-a4b4-a33e2e306591
ms.openlocfilehash: 0abcc73e31eab89c422513acf778bc8bd092e788
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345550"
---
# <a name="delegates-and-lambdas"></a><span data-ttu-id="197c1-103">Delegaci i wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="197c1-103">Delegates and lambdas</span></span>

<span data-ttu-id="197c1-104">Delegaty definiują typ, który określa określoną sygnaturę metody.</span><span class="sxs-lookup"><span data-stu-id="197c1-104">Delegates define a type, which specify a particular method signature.</span></span> <span data-ttu-id="197c1-105">Metoda (statyczna lub wystąpienie), która spełnia tę sygnaturę, może być przypisana do zmiennej tego typu, a następnie wywoływana bezpośrednio (z odpowiednimi argumentami) lub przekazana jako argument do innej metody, a następnie wywołana.</span><span class="sxs-lookup"><span data-stu-id="197c1-105">A method (static or instance) that satisfies this signature can be assigned to a variable of that type, then called directly (with the appropriate arguments) or passed as an argument itself to another method and then called.</span></span> <span data-ttu-id="197c1-106">Poniższy przykład demonstruje użycie delegata.</span><span class="sxs-lookup"><span data-stu-id="197c1-106">The following example demonstrates delegate use.</span></span>

```csharp
using System;
using System.Linq;

public class Program
{
    public delegate string Reverse(string s);

    static string ReverseString(string s)
    {
        return new string(s.Reverse().ToArray());
    }

    static void Main(string[] args)
    {
        Reverse rev = ReverseString;

        Console.WriteLine(rev("a string"));
    }
}
```

* <span data-ttu-id="197c1-107">Wiersz `public delegate string Reverse(string s);` tworzy typ delegata o określonej sygnaturze, w tym przypadku metodę, która przyjmuje parametr ciągu, a następnie zwraca parametr ciągu.</span><span class="sxs-lookup"><span data-stu-id="197c1-107">The `public delegate string Reverse(string s);` line creates a delegate type of a certain signature, in this case a method that takes a string parameter and then returns a string parameter.</span></span>
* <span data-ttu-id="197c1-108">Metoda `static string ReverseString(string s)`, która ma dokładnie taki sam podpis jak zdefiniowany typ delegata, implementuje delegata.</span><span class="sxs-lookup"><span data-stu-id="197c1-108">The `static string ReverseString(string s)` method, which has the exact same signature as the defined delegate type, implements the delegate.</span></span>
* <span data-ttu-id="197c1-109">Wiersz `Reverse rev = ReverseString;` pokazuje, że można przypisać metodę do zmiennej odpowiedniego typu delegata.</span><span class="sxs-lookup"><span data-stu-id="197c1-109">The `Reverse rev = ReverseString;` line shows that you can assign a method to a variable of the corresponding delegate type.</span></span>
* <span data-ttu-id="197c1-110">W wierszu `Console.WriteLine(rev("a string"));` pokazano, jak używać zmiennej typu delegata do wywołania delegata.</span><span class="sxs-lookup"><span data-stu-id="197c1-110">The `Console.WriteLine(rev("a string"));` line demonstrates how to use a variable of a delegate type to invoke the delegate.</span></span>

<span data-ttu-id="197c1-111">Aby usprawnić proces opracowywania, platforma .NET zawiera zestaw typów delegatów, które programiści mogą ponownie wykorzystać i nie muszą tworzyć nowych typów.</span><span class="sxs-lookup"><span data-stu-id="197c1-111">In order to streamline the development process, .NET includes a set of delegate types that programmers can reuse and not have to create new types.</span></span> <span data-ttu-id="197c1-112">Są one `Func<>`, `Action<>` i `Predicate<>`i mogą być używane w różnych miejscach interfejsów API platformy .NET bez konieczności definiowania nowych typów delegatów.</span><span class="sxs-lookup"><span data-stu-id="197c1-112">These are `Func<>`, `Action<>` and `Predicate<>`, and they can be used in various places throughout the .NET APIs without the need to define new delegate types.</span></span> <span data-ttu-id="197c1-113">Oczywiście istnieją pewne różnice między trzema takimi elementami, jak w ich podpisach, które przede wszystkim mają być używane:</span><span class="sxs-lookup"><span data-stu-id="197c1-113">Of course, there are some differences between the three as you will see in their signatures which mostly have to do with the way they were meant to be used:</span></span>

* <span data-ttu-id="197c1-114">`Action<>` jest używany, gdy istnieje potrzeba wykonania akcji przy użyciu argumentów delegata.</span><span class="sxs-lookup"><span data-stu-id="197c1-114">`Action<>` is used when there is a need to perform an action using the arguments of the delegate.</span></span>
* <span data-ttu-id="197c1-115">`Func<>` jest używany zwykle w przypadku przekształcania, to oznacza, że należy przekształcić argumenty delegata na inny wynik.</span><span class="sxs-lookup"><span data-stu-id="197c1-115">`Func<>` is used usually when you have a transformation on hand, that is, you need to transform the arguments of the delegate into a different result.</span></span> <span data-ttu-id="197c1-116">Projekcje są głównym przykładem.</span><span class="sxs-lookup"><span data-stu-id="197c1-116">Projections are a prime example of this.</span></span>
* <span data-ttu-id="197c1-117">`Predicate<>` jest używany, gdy konieczne jest określenie, czy argument spełnia warunek delegata.</span><span class="sxs-lookup"><span data-stu-id="197c1-117">`Predicate<>` is used when you need to determine if the argument satisfies the condition of the delegate.</span></span> <span data-ttu-id="197c1-118">Można go również napisać jako `Func<T, bool>`.</span><span class="sxs-lookup"><span data-stu-id="197c1-118">It can also be written as a `Func<T, bool>`.</span></span>

<span data-ttu-id="197c1-119">Teraz możemy skorzystać z naszego powyższego przykładu i napisać go ponownie przy użyciu delegata `Func<>` zamiast typu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="197c1-119">We can now take our example above and rewrite it using the `Func<>` delegate instead of a custom type.</span></span> <span data-ttu-id="197c1-120">Program będzie działał dokładnie tak samo.</span><span class="sxs-lookup"><span data-stu-id="197c1-120">The program will continue running exactly the same.</span></span>

```csharp
using System;
using System.Linq;

public class Program
{
    static string ReverseString(string s)
    {
        return new string(s.Reverse().ToArray());
    }

    static void Main(string[] args)
    {
        Func<string, string> rev = ReverseString;

        Console.WriteLine(rev("a string"));
    }
}
```

<span data-ttu-id="197c1-121">W tym prostym przykładzie posiadanie metody zdefiniowanej poza metodą `Main` wydaje się nieco zbędne.</span><span class="sxs-lookup"><span data-stu-id="197c1-121">For this simple example, having a method defined outside of the `Main` method seems a bit superfluous.</span></span> <span data-ttu-id="197c1-122">Wynika to z tego, że .NET Framework 2,0 wprowadza koncepcję **anonimowych delegatów**.</span><span class="sxs-lookup"><span data-stu-id="197c1-122">It is because of this that .NET Framework 2.0 introduced the concept of **anonymous delegates**.</span></span> <span data-ttu-id="197c1-123">Dzięki obsłudze można tworzyć delegatów "inline" bez konieczności określania dodatkowego typu lub metody.</span><span class="sxs-lookup"><span data-stu-id="197c1-123">With their support you are able to create "inline" delegates without having to specify any additional type or method.</span></span> <span data-ttu-id="197c1-124">Po prostu utworzysz definicję delegata, gdzie go potrzebujesz.</span><span class="sxs-lookup"><span data-stu-id="197c1-124">You simply inline the definition of the delegate where you need it.</span></span>

<span data-ttu-id="197c1-125">Na przykład przełączymy ją i użyjemy anonimowego delegata, aby odfiltrować listę tylko parzystych liczb, a następnie wydrukować je w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="197c1-125">For an example, we are going to switch it up and use our anonymous delegate to filter out a list of only even numbers and then print them to the console.</span></span>

```csharp
using System;
using System.Collections.Generic;

public class Program
{
    public static void Main(string[] args)
    {
        List<int> list = new List<int>();

        for (int i = 1; i <= 100; i++)
        {
            list.Add(i);
        }

        List<int> result = list.FindAll(
          delegate (int no)
          {
              return (no % 2 == 0);
          }
        );

        foreach (var item in result)
        {
            Console.WriteLine(item);
        }
    }
}
```

<span data-ttu-id="197c1-126">Jak widać, treść delegata jest tylko zestawem wyrażeń, jak każdy inny delegat.</span><span class="sxs-lookup"><span data-stu-id="197c1-126">As you can see, the body of the delegate is just a set of expressions, as any other delegate.</span></span> <span data-ttu-id="197c1-127">Ale zamiast tego nie jest to osobna definicja, wprowadziliśmy ją _ad hoc_ w wywołaniu metody <xref:System.Collections.Generic.List%601.FindAll%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="197c1-127">But instead of it being a separate definition, we’ve introduced it _ad hoc_ in our call to the <xref:System.Collections.Generic.List%601.FindAll%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="197c1-128">Jednak nawet w przypadku tego podejścia nadal istnieje dużo kodu, który możemy zgłosić.</span><span class="sxs-lookup"><span data-stu-id="197c1-128">However, even with this approach, there is still much code that we can throw away.</span></span> <span data-ttu-id="197c1-129">Jest to miejsce, w którym **wyrażenia lambda** są odtwarzane.</span><span class="sxs-lookup"><span data-stu-id="197c1-129">This is where **lambda expressions** come into play.</span></span>

<span data-ttu-id="197c1-130">Wyrażenia lambda lub tylko "lambda" są krótkie, najpierw wprowadzane w C# 3,0, jako jeden z podstawowych bloków konstrukcyjnych języka (LINQ).</span><span class="sxs-lookup"><span data-stu-id="197c1-130">Lambda expressions, or just "lambdas" for short, were introduced first in C# 3.0, as one of the core building blocks of Language Integrated Query (LINQ).</span></span> <span data-ttu-id="197c1-131">Jest to tylko bardziej wygodna Składnia służąca do używania delegatów.</span><span class="sxs-lookup"><span data-stu-id="197c1-131">They are just a more convenient syntax for using delegates.</span></span> <span data-ttu-id="197c1-132">Deklarują sygnaturę i treść metody, ale nie mają formalnej tożsamości własnej, chyba że są przypisane do delegata.</span><span class="sxs-lookup"><span data-stu-id="197c1-132">They declare a signature and a method body, but don’t have an formal identity of their own, unless they are assigned to a delegate.</span></span> <span data-ttu-id="197c1-133">W przeciwieństwie do delegatów, można bezpośrednio przypisywać je po lewej stronie rejestracji zdarzeń lub w różnych klauzulach i metodach LINQ.</span><span class="sxs-lookup"><span data-stu-id="197c1-133">Unlike delegates, they can be directly assigned as the left-hand side of event registration or in various LINQ clauses and methods.</span></span>

<span data-ttu-id="197c1-134">Ponieważ wyrażenie lambda jest już innym sposobem określania delegata, powinno być możliwe przepisanie powyższego przykładu, aby użyć wyrażenia lambda zamiast anonimowego delegata.</span><span class="sxs-lookup"><span data-stu-id="197c1-134">Since a lambda expression is just another way of specifying a delegate, we should be able to rewrite the above sample to use a lambda expression instead of an anonymous delegate.</span></span>

```csharp
using System;
using System.Collections.Generic;

public class Program
{
    public static void Main(string[] args)
    {
        List<int> list = new List<int>();

        for (int i = 1; i <= 100; i++)
        {
            list.Add(i);
        }

        List<int> result = list.FindAll(i => i % 2 == 0);

        foreach (var item in result)
        {
            Console.WriteLine(item);
        }
    }
}
```

<span data-ttu-id="197c1-135">W poprzednim przykładzie użyte wyrażenie lambda jest `i => i % 2 == 0`.</span><span class="sxs-lookup"><span data-stu-id="197c1-135">In the preceding example, the lambda expression used is `i => i % 2 == 0`.</span></span> <span data-ttu-id="197c1-136">Ponownie jest to tylko **bardzo** wygodna Składnia służąca do używania delegatów, co się dzieje w obszarze okładek, podobnie jak w przypadku delegata anonimowego.</span><span class="sxs-lookup"><span data-stu-id="197c1-136">Again, it is just a **very** convenient syntax for using delegates, so what happens under the covers is similar to what happens with the anonymous delegate.</span></span>

<span data-ttu-id="197c1-137">Ponownie wyrażenia lambda są tylko delegatami, co oznacza, że mogą być używane jako program obsługi zdarzeń bez żadnych problemów, co ilustruje poniższy fragment kodu.</span><span class="sxs-lookup"><span data-stu-id="197c1-137">Again, lambdas are just delegates, which means that they can be used as an event handler without any problems, as the following code snippet illustrates.</span></span>

```csharp
public MainWindow()
{
    InitializeComponent();

    Loaded += (o, e) =>
    {
        this.Title = "Loaded";
    };
}
```

<span data-ttu-id="197c1-138">Operator `+=` w tym kontekście jest używany do subskrybowania [zdarzenia](../../docs/csharp/language-reference/keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="197c1-138">The `+=` operator in this context is used to subscribe to an [event](../../docs/csharp/language-reference/keywords/event.md).</span></span> <span data-ttu-id="197c1-139">Aby uzyskać więcej informacji, zobacz [subskrybowanie i anulowanie subskrypcji zdarzeń](../../docs/csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="197c1-139">For more information, see [How to subscribe to and unsubscribe from events](../../docs/csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="further-reading-and-resources"></a><span data-ttu-id="197c1-140">Dalsze odczytywanie i zasoby</span><span class="sxs-lookup"><span data-stu-id="197c1-140">Further reading and resources</span></span>

* [<span data-ttu-id="197c1-141">Delegaci</span><span class="sxs-lookup"><span data-stu-id="197c1-141">Delegates</span></span>](../../docs/csharp/programming-guide/delegates/index.md)
* [<span data-ttu-id="197c1-142">Funkcje anonimowe</span><span class="sxs-lookup"><span data-stu-id="197c1-142">Anonymous Functions</span></span>](../../docs/csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)
* [<span data-ttu-id="197c1-143">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="197c1-143">Lambda expressions</span></span>](../../docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)

---
title: Delegaci i wyrażenia lambda
description: Dowiedz się, jak delegatów Definiowanie typu, które określą podpis konkretnej metody, które mogą być wywoływane bezpośrednio lub przekazana do innej metody o nazwie.
author: richlander
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: fe2e4b4c-6483-4106-a4b4-a33e2e306591
ms.openlocfilehash: 3fb926683de90516bcf67d99026a0134d82cb683
ms.sourcegitcommit: 35316b768394e56087483cde93f854ba607b63bc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/26/2018
ms.locfileid: "52296948"
---
# <a name="delegates-and-lambdas"></a><span data-ttu-id="cb308-103">Delegaci i wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="cb308-103">Delegates and lambdas</span></span>

<span data-ttu-id="cb308-104">Delegaty zdefiniować typ, które określą podpisu konkretnej metody.</span><span class="sxs-lookup"><span data-stu-id="cb308-104">Delegates define a type, which specify a particular method signature.</span></span> <span data-ttu-id="cb308-105">Metody (statyczny lub wystąpienia) odpowiadającej ten podpis mogą zostać przypisane do zmiennej tego typu, a następnie wywoływana bezpośrednio (z odpowiednimi argumentami) lub przekazywany jako argument sam do innej metody i następnie wywoływana.</span><span class="sxs-lookup"><span data-stu-id="cb308-105">A method (static or instance) that satisfies this signature can be assigned to a variable of that type, then called directly (with the appropriate arguments) or passed as an argument itself to another method and then called.</span></span> <span data-ttu-id="cb308-106">W poniższym przykładzie pokazano użycie delegata.</span><span class="sxs-lookup"><span data-stu-id="cb308-106">The following example demonstrates delegate use.</span></span>

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

* <span data-ttu-id="cb308-107">`public delegate string Reverse(string s);` Wiersz tworzy typ delegata podpisu w tym przypadku metoda, która przyjmuje parametr ciąg, a następnie zwraca parametr ciągu.</span><span class="sxs-lookup"><span data-stu-id="cb308-107">The `public delegate string Reverse(string s);` line creates a delegate type of a certain signature, in this case a method that takes a string parameter and then returns a string parameter.</span></span>
* <span data-ttu-id="cb308-108">`static string ReverseString(string s)` Metody, która ma dokładnie tę samą sygnaturę jak typ delegata zdefiniowane, implementuje delegata.</span><span class="sxs-lookup"><span data-stu-id="cb308-108">The `static string ReverseString(string s)` method, which has the exact same signature as the defined delegate type, implements the delegate.</span></span>
* <span data-ttu-id="cb308-109">`Reverse rev = ReverseString;` Wiersz wskazuje, czy metody można przypisać do zmiennej odpowiedni typ delegata.</span><span class="sxs-lookup"><span data-stu-id="cb308-109">The `Reverse rev = ReverseString;` line shows that you can assign a method to a variable of the corresponding delegate type.</span></span>
* <span data-ttu-id="cb308-110">`Console.WriteLine(rev("a string"));` Linii pokazuje, jak używana zmienna typu delegata do wywołania delegata.</span><span class="sxs-lookup"><span data-stu-id="cb308-110">The `Console.WriteLine(rev("a string"));` line demonstrates how to use a variable of a delegate type to invoke the delegate.</span></span>

<span data-ttu-id="cb308-111">W celu uproszczenia procesu tworzenia, .NET zawiera zbiór typami delegatów, które programiści mogą ponownie użyć i nie trzeba tworzyć nowe typy.</span><span class="sxs-lookup"><span data-stu-id="cb308-111">In order to streamline the development process, .NET includes a set of delegate types that programmers can reuse and not have to create new types.</span></span> <span data-ttu-id="cb308-112">Są to `Func<>`, `Action<>` i `Predicate<>`, i można ich używać w różnych miejscach interfejsów API platformy .NET bez konieczności do definiowania nowych typów obiektów delegowanych.</span><span class="sxs-lookup"><span data-stu-id="cb308-112">These are `Func<>`, `Action<>` and `Predicate<>`, and they can be used in various places throughout the .NET APIs without the need to define new delegate types.</span></span> <span data-ttu-id="cb308-113">Jak widać w ich sygnaturach, które przede wszystkim ze sposobem, w których zostały one przeznaczone do użycia istnieją oczywiście niektóre różnice między trzy:</span><span class="sxs-lookup"><span data-stu-id="cb308-113">Of course, there are some differences between the three as you will see in their signatures which mostly have to do with the way they were meant to be used:</span></span>

*   <span data-ttu-id="cb308-114">`Action<>` jest używany, gdy trzeba wykonać akcję przy użyciu argumentów delegata.</span><span class="sxs-lookup"><span data-stu-id="cb308-114">`Action<>` is used when there is a need to perform an action using the arguments of the delegate.</span></span>
*   <span data-ttu-id="cb308-115">`Func<>` jest używana zazwyczaj w przypadku transformacji w kasie, oznacza to, należy przekształcić argumenty delegata w różne wyniki.</span><span class="sxs-lookup"><span data-stu-id="cb308-115">`Func<>` is used usually when you have a transformation on hand, that is, you need to transform the arguments of the delegate into a different result.</span></span> <span data-ttu-id="cb308-116">Prognozy są głównym przykładem.</span><span class="sxs-lookup"><span data-stu-id="cb308-116">Projections are a prime example of this.</span></span>
*   <span data-ttu-id="cb308-117">`Predicate<>` jest używany, gdy zachodzi potrzeba określenia, jeśli argument spełnia warunek delegata.</span><span class="sxs-lookup"><span data-stu-id="cb308-117">`Predicate<>` is used when you need to determine if the argument satisfies the condition of the delegate.</span></span> <span data-ttu-id="cb308-118">Można również będą zapisywane jako `Func<T, bool>`.</span><span class="sxs-lookup"><span data-stu-id="cb308-118">It can also be written as a `Func<T, bool>`.</span></span>

<span data-ttu-id="cb308-119">Możemy teraz pobrać naszym powyższym przykładzie i ponownie napisać przy użyciu `Func<>` delegować zamiast typu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="cb308-119">We can now take our example above and rewrite it using the `Func<>` delegate instead of a custom type.</span></span> <span data-ttu-id="cb308-120">Program będzie nadal uruchomione, dokładnie tak samo.</span><span class="sxs-lookup"><span data-stu-id="cb308-120">The program will continue running exactly the same.</span></span>

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

<span data-ttu-id="cb308-121">W przypadku ten prosty przykład o metoda zdefiniowana poza `Main` metoda wydaje się nieco zbędny.</span><span class="sxs-lookup"><span data-stu-id="cb308-121">For this simple example, having a method defined outside of the `Main` method seems a bit superfluous.</span></span> <span data-ttu-id="cb308-122">Jest ze względu na to, że .NET Framework 2.0 wprowadzono koncepcję **anonimowe delegatów**.</span><span class="sxs-lookup"><span data-stu-id="cb308-122">It is because of this that .NET Framework 2.0 introduced the concept of **anonymous delegates**.</span></span> <span data-ttu-id="cb308-123">Za pomocą ich obsługa jest możliwe do tworzenia obiektów delegowanych "inline" bez konieczności określania żadnych dodatkowych typu lub metody.</span><span class="sxs-lookup"><span data-stu-id="cb308-123">With their support you are able to create "inline" delegates without having to specify any additional type or method.</span></span> <span data-ttu-id="cb308-124">Możesz po prostu wbudowanej definicji delegata, gdy jej potrzebujesz.</span><span class="sxs-lookup"><span data-stu-id="cb308-124">You simply inline the definition of the delegate where you need it.</span></span>

<span data-ttu-id="cb308-125">Aby uzyskać przykład użyjemy zmienić się i użyj naszych delegata anonimowego, aby odfiltrować listę tylko liczby parzyste z zakresu, a następnie wydrukuj je w konsoli.</span><span class="sxs-lookup"><span data-stu-id="cb308-125">For an example, we are going to switch it up and use our anonymous delegate to filter out a list of only even numbers and then print them to the console.</span></span>

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

<span data-ttu-id="cb308-126">Jak widać, treść delegata jest po prostu zestaw wyrażeń, jak inne obiekt delegowany.</span><span class="sxs-lookup"><span data-stu-id="cb308-126">As you can see, the body of the delegate is just a set of expressions, as any other delegate.</span></span> <span data-ttu-id="cb308-127">Ale zamiast jej definicję oddzielne, wprowadziliśmy go _ad hoc_ w wywołaniu elementu naszych <xref:System.Collections.Generic.List%601.FindAll%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="cb308-127">But instead of it being a separate definition, we’ve introduced it _ad hoc_ in our call to the <xref:System.Collections.Generic.List%601.FindAll%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="cb308-128">Jednak nawet w przypadku tej metody, ma nadal większej ilości kodu, który możemy wyrzucać.</span><span class="sxs-lookup"><span data-stu-id="cb308-128">However, even with this approach, there is still much code that we can throw away.</span></span> <span data-ttu-id="cb308-129">Jest to miejsce **wyrażeń lambda** dochodzą do głosu.</span><span class="sxs-lookup"><span data-stu-id="cb308-129">This is where **lambda expressions** come into play.</span></span>

<span data-ttu-id="cb308-130">Wyrażenia lambda lub po prostu "wyrażenia lambda" w skrócie, zostały najpierw wprowadzone w systemie C# 3.0 jako jeden z podstawowych bloków konstrukcyjnych z Language Integrated Query (LINQ).</span><span class="sxs-lookup"><span data-stu-id="cb308-130">Lambda expressions, or just "lambdas" for short, were introduced first in C# 3.0, as one of the core building blocks of Language Integrated Query (LINQ).</span></span> <span data-ttu-id="cb308-131">Są one po prostu bardziej wygodne składnia przy użyciu delegatów.</span><span class="sxs-lookup"><span data-stu-id="cb308-131">They are just a more convenient syntax for using delegates.</span></span> <span data-ttu-id="cb308-132">One deklarować podpisu i treści metody, ale nie ma formalnych tożsamości własnych, o ile nie są przypisane do delegata.</span><span class="sxs-lookup"><span data-stu-id="cb308-132">They declare a signature and a method body, but don’t have an formal identity of their own, unless they are assigned to a delegate.</span></span> <span data-ttu-id="cb308-133">W przeciwieństwie do delegatów bezpośrednio przypisać jako po lewej stronie rejestracji zdarzeń lub różne klauzule zapytań LINQ i metody.</span><span class="sxs-lookup"><span data-stu-id="cb308-133">Unlike delegates, they can be directly assigned as the left-hand side of event registration or in various LINQ clauses and methods.</span></span>

<span data-ttu-id="cb308-134">Ponieważ wyrażenie lambda jest po prostu inny sposób określania delegata, firma Microsoft powinno być możliwe do przepisania w powyższym przykładzie, można użyć wyrażenia lambda zamiast delegata anonimowego.</span><span class="sxs-lookup"><span data-stu-id="cb308-134">Since a lambda expression is just another way of specifying a delegate, we should be able to rewrite the above sample to use a lambda expression instead of an anonymous delegate.</span></span>

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

<span data-ttu-id="cb308-135">W powyższym przykładzie jest używane wyrażenie lambda `i => i % 2 == 0`.</span><span class="sxs-lookup"><span data-stu-id="cb308-135">In the preceding example, the lambda expression used is `i => i % 2 == 0`.</span></span> <span data-ttu-id="cb308-136">Ponownie, jest po prostu **bardzo** wygodnej składni dla przy użyciu delegatów, więc co się stanie w sposób niewidoczny przypomina co się dzieje z delegata anonimowego.</span><span class="sxs-lookup"><span data-stu-id="cb308-136">Again, it is just a **very** convenient syntax for using delegates, so what happens under the covers is similar to what happens with the anonymous delegate.</span></span>

<span data-ttu-id="cb308-137">Ponownie wyrażenia lambda są po prostu delegatów, co oznacza, że mogą być używane jako procedura obsługi zdarzeń bez problemów, tak jak pokazano w poniższym fragmencie kodu.</span><span class="sxs-lookup"><span data-stu-id="cb308-137">Again, lambdas are just delegates, which means that they can be used as an event handler without any problems, as the following code snippet illustrates.</span></span>

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

## <a name="further-reading-and-resources"></a><span data-ttu-id="cb308-138">Dalsze informacje i zasoby</span><span class="sxs-lookup"><span data-stu-id="cb308-138">Further reading and resources</span></span>

*   [<span data-ttu-id="cb308-139">Delegaty</span><span class="sxs-lookup"><span data-stu-id="cb308-139">Delegates</span></span>](../../docs/csharp/programming-guide/delegates/index.md)
*   [<span data-ttu-id="cb308-140">Funkcje anonimowe</span><span class="sxs-lookup"><span data-stu-id="cb308-140">Anonymous Functions</span></span>](../../docs/csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)
*   [<span data-ttu-id="cb308-141">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="cb308-141">Lambda expressions</span></span>](../../docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)

---
title: Delegaci i wyrażenia lambda
description: Dowiedz się, w jaki sposób Delegaty definiujące typ określający konkretny podpis metody można wywołać bezpośrednio lub przesłać do innej metody i wywołać metodę.
author: richlander
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: fe2e4b4c-6483-4106-a4b4-a33e2e306591
ms.openlocfilehash: 184c9f61fd8456b22e8ecb262c131793160b49b0
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85244013"
---
# <a name="delegates-and-lambdas"></a><span data-ttu-id="af3b7-103">Delegaci i wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="af3b7-103">Delegates and lambdas</span></span>

<span data-ttu-id="af3b7-104">Delegaty definiują typ, który określa określoną sygnaturę metody.</span><span class="sxs-lookup"><span data-stu-id="af3b7-104">Delegates define a type that specifies a particular method signature.</span></span> <span data-ttu-id="af3b7-105">Metoda (statyczna lub wystąpienie), która spełnia tę sygnaturę, może być przypisana do zmiennej tego typu, a następnie wywoływana bezpośrednio (z odpowiednimi argumentami) lub przekazana jako argument do innej metody, a następnie wywołana.</span><span class="sxs-lookup"><span data-stu-id="af3b7-105">A method (static or instance) that satisfies this signature can be assigned to a variable of that type, then called directly (with the appropriate arguments) or passed as an argument itself to another method and then called.</span></span> <span data-ttu-id="af3b7-106">Poniższy przykład demonstruje użycie delegata.</span><span class="sxs-lookup"><span data-stu-id="af3b7-106">The following example demonstrates delegate use.</span></span>

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

* <span data-ttu-id="af3b7-107">`public delegate string Reverse(string s);`Wiersz tworzy typ delegata o określonej sygnaturze, w tym przypadku metodę, która przyjmuje parametr String, a następnie zwraca parametr ciągu.</span><span class="sxs-lookup"><span data-stu-id="af3b7-107">The `public delegate string Reverse(string s);` line creates a delegate type of a certain signature, in this case a method that takes a string parameter and then returns a string parameter.</span></span>
* <span data-ttu-id="af3b7-108">`static string ReverseString(string s)`Metoda, która ma dokładnie taki sam podpis, jak zdefiniowany typ delegata, implementuje delegata.</span><span class="sxs-lookup"><span data-stu-id="af3b7-108">The `static string ReverseString(string s)` method, which has the exact same signature as the defined delegate type, implements the delegate.</span></span>
* <span data-ttu-id="af3b7-109">`Reverse rev = ReverseString;`Wiersz pokazuje, że można przypisać metodę do zmiennej odpowiedniego typu delegata.</span><span class="sxs-lookup"><span data-stu-id="af3b7-109">The `Reverse rev = ReverseString;` line shows that you can assign a method to a variable of the corresponding delegate type.</span></span>
* <span data-ttu-id="af3b7-110">`Console.WriteLine(rev("a string"));`Wiersz ilustruje sposób użycia zmiennej typu delegata do wywołania delegata.</span><span class="sxs-lookup"><span data-stu-id="af3b7-110">The `Console.WriteLine(rev("a string"));` line demonstrates how to use a variable of a delegate type to invoke the delegate.</span></span>

<span data-ttu-id="af3b7-111">Aby usprawnić proces opracowywania, platforma .NET zawiera zestaw typów delegatów, które programiści mogą ponownie wykorzystać i nie muszą tworzyć nowych typów.</span><span class="sxs-lookup"><span data-stu-id="af3b7-111">In order to streamline the development process, .NET includes a set of delegate types that programmers can reuse and not have to create new types.</span></span> <span data-ttu-id="af3b7-112">Te typy są `Func<>` , `Action<>` i `Predicate<>` i mogą być używane bez konieczności definiowania nowych typów delegatów.</span><span class="sxs-lookup"><span data-stu-id="af3b7-112">These types are `Func<>`, `Action<>` and `Predicate<>`, and they can be used without having to define new delegate types.</span></span> <span data-ttu-id="af3b7-113">Istnieją pewne różnice między trzema typami, które należy wykonać w celu zamierzonego użycia:</span><span class="sxs-lookup"><span data-stu-id="af3b7-113">There are some differences between the three types that have to do with the way they were intended to be used:</span></span>

* <span data-ttu-id="af3b7-114">`Action<>`jest używany, gdy istnieje potrzeba wykonania akcji przy użyciu argumentów delegata.</span><span class="sxs-lookup"><span data-stu-id="af3b7-114">`Action<>` is used when there is a need to perform an action using the arguments of the delegate.</span></span> <span data-ttu-id="af3b7-115">Metoda, która jest hermetyzowana, nie zwraca wartości.</span><span class="sxs-lookup"><span data-stu-id="af3b7-115">The method it encapsulates does not return a value.</span></span>
* <span data-ttu-id="af3b7-116">`Func<>`jest używany zwykle w przypadku, gdy istnieje transformacja, to jest konieczne przekształcenie argumentów delegata w inny wynik.</span><span class="sxs-lookup"><span data-stu-id="af3b7-116">`Func<>` is used usually when you have a transformation on hand, that is, you need to transform the arguments of the delegate into a different result.</span></span> <span data-ttu-id="af3b7-117">Projekcje są dobrym przykładem.</span><span class="sxs-lookup"><span data-stu-id="af3b7-117">Projections are a good example.</span></span> <span data-ttu-id="af3b7-118">Metoda, która jest hermetyzowana, zwraca określoną wartość.</span><span class="sxs-lookup"><span data-stu-id="af3b7-118">The method it encapsulates returns a specified value.</span></span>
* <span data-ttu-id="af3b7-119">`Predicate<>`jest używany, gdy należy określić, czy argument spełnia warunek delegata.</span><span class="sxs-lookup"><span data-stu-id="af3b7-119">`Predicate<>` is used when you need to determine if the argument satisfies the condition of the delegate.</span></span> <span data-ttu-id="af3b7-120">Można go również napisać jako `Func<T, bool>` , co oznacza, że metoda zwraca wartość logiczną.</span><span class="sxs-lookup"><span data-stu-id="af3b7-120">It can also be written as a `Func<T, bool>`, which means the method returns a boolean value.</span></span>

<span data-ttu-id="af3b7-121">Teraz możemy skorzystać z naszego powyższego przykładu i napisać go ponownie przy użyciu `Func<>` delegata zamiast typu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="af3b7-121">We can now take our example above and rewrite it using the `Func<>` delegate instead of a custom type.</span></span> <span data-ttu-id="af3b7-122">Program będzie działał dokładnie tak samo.</span><span class="sxs-lookup"><span data-stu-id="af3b7-122">The program will continue running exactly the same.</span></span>

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

<span data-ttu-id="af3b7-123">W tym prostym przykładzie, jeśli metoda zdefiniowana poza tą `Main` metodą jest niezbędna.</span><span class="sxs-lookup"><span data-stu-id="af3b7-123">For this simple example, having a method defined outside of the `Main` method seems a bit superfluous.</span></span> <span data-ttu-id="af3b7-124">.NET Framework 2,0 wprowadził koncepcję *anonimowych delegatów*, która umożliwia tworzenie "wbudowanych" delegatów bez konieczności określania jakiegokolwiek dodatkowego typu lub metody.</span><span class="sxs-lookup"><span data-stu-id="af3b7-124">.NET Framework 2.0 introduced the concept of *anonymous delegates*, which let you create "inline" delegates without having to specify any additional type or method.</span></span>

<span data-ttu-id="af3b7-125">W poniższym przykładzie delegat anonimowy filtruje listę tylko liczb parzystych, a następnie drukuje je w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="af3b7-125">In the following example, an anonymous delegate filters a list to just the even numbers and then prints them to the console.</span></span>

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

<span data-ttu-id="af3b7-126">Jak widać, treść delegata jest tylko zestawem wyrażeń, jak każdy inny delegat.</span><span class="sxs-lookup"><span data-stu-id="af3b7-126">As you can see, the body of the delegate is just a set of expressions, as any other delegate.</span></span> <span data-ttu-id="af3b7-127">Ale zamiast tego nie jest to osobna definicja, wprowadziliśmy ją _ad hoc_ w wywołaniu <xref:System.Collections.Generic.List%601.FindAll%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="af3b7-127">But instead of it being a separate definition, we've introduced it _ad hoc_ in our call to the <xref:System.Collections.Generic.List%601.FindAll%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="af3b7-128">Jednak nawet w przypadku tego podejścia nadal istnieje dużo kodu, który możemy zgłosić.</span><span class="sxs-lookup"><span data-stu-id="af3b7-128">However, even with this approach, there is still much code that we can throw away.</span></span> <span data-ttu-id="af3b7-129">Jest to miejsce, w którym *wyrażenia lambda* są odtwarzane.</span><span class="sxs-lookup"><span data-stu-id="af3b7-129">This is where *lambda expressions* come into play.</span></span> <span data-ttu-id="af3b7-130">Wyrażenia lambda lub same "wyrażenia lambda" są stosowane w języku C# 3,0 jako jeden z podstawowych bloków konstrukcyjnych języka Integrated Query (LINQ).</span><span class="sxs-lookup"><span data-stu-id="af3b7-130">Lambda expressions, or just "lambdas" for short, were introduced in C# 3.0 as one of the core building blocks of Language Integrated Query (LINQ).</span></span> <span data-ttu-id="af3b7-131">Jest to tylko bardziej wygodna Składnia służąca do używania delegatów.</span><span class="sxs-lookup"><span data-stu-id="af3b7-131">They are just a more convenient syntax for using delegates.</span></span> <span data-ttu-id="af3b7-132">Deklarują sygnaturę i treść metody, ale nie mają formalnej tożsamości własnej, chyba że są przypisane do delegata.</span><span class="sxs-lookup"><span data-stu-id="af3b7-132">They declare a signature and a method body, but don't have a formal identity of their own, unless they are assigned to a delegate.</span></span> <span data-ttu-id="af3b7-133">W przeciwieństwie do delegatów, mogą być bezpośrednio przypisane jako prawo do rejestracji zdarzeń lub w różnych klauzulach i metodach LINQ.</span><span class="sxs-lookup"><span data-stu-id="af3b7-133">Unlike delegates, they can be directly assigned as the right-hand side of event registration or in various LINQ clauses and methods.</span></span>

<span data-ttu-id="af3b7-134">Ponieważ wyrażenie lambda jest już innym sposobem określania delegata, powinno być możliwe przepisanie powyższego przykładu, aby użyć wyrażenia lambda zamiast anonimowego delegata.</span><span class="sxs-lookup"><span data-stu-id="af3b7-134">Since a lambda expression is just another way of specifying a delegate, we should be able to rewrite the above sample to use a lambda expression instead of an anonymous delegate.</span></span>

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

<span data-ttu-id="af3b7-135">W poprzednim przykładzie użyte wyrażenie lambda ma wartość `i => i % 2 == 0` .</span><span class="sxs-lookup"><span data-stu-id="af3b7-135">In the preceding example, the lambda expression used is `i => i % 2 == 0`.</span></span> <span data-ttu-id="af3b7-136">Jest to tylko wygodna Składnia służąca do używania delegatów.</span><span class="sxs-lookup"><span data-stu-id="af3b7-136">Again, it is just a convenient syntax for using delegates.</span></span> <span data-ttu-id="af3b7-137">Co się dzieje w obszarze okładek, podobnie jak w przypadku delegata anonimowego.</span><span class="sxs-lookup"><span data-stu-id="af3b7-137">What happens under the covers is similar to what happens with the anonymous delegate.</span></span>

<span data-ttu-id="af3b7-138">Ponownie wyrażenia lambda są tylko delegatami, co oznacza, że mogą być używane jako program obsługi zdarzeń bez żadnych problemów, co ilustruje poniższy fragment kodu.</span><span class="sxs-lookup"><span data-stu-id="af3b7-138">Again, lambdas are just delegates, which means that they can be used as an event handler without any problems, as the following code snippet illustrates.</span></span>

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

<span data-ttu-id="af3b7-139">`+=`Operator w tym kontekście jest używany do subskrybowania [zdarzenia](../csharp/language-reference/keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="af3b7-139">The `+=` operator in this context is used to subscribe to an [event](../csharp/language-reference/keywords/event.md).</span></span> <span data-ttu-id="af3b7-140">Aby uzyskać więcej informacji, zobacz [subskrybowanie i anulowanie subskrypcji zdarzeń](../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span><span class="sxs-lookup"><span data-stu-id="af3b7-140">For more information, see [How to subscribe to and unsubscribe from events](../csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="further-reading-and-resources"></a><span data-ttu-id="af3b7-141">Dalsze odczytywanie i zasoby</span><span class="sxs-lookup"><span data-stu-id="af3b7-141">Further reading and resources</span></span>

* [<span data-ttu-id="af3b7-142">Delegaci</span><span class="sxs-lookup"><span data-stu-id="af3b7-142">Delegates</span></span>](../csharp/programming-guide/delegates/index.md)
* [<span data-ttu-id="af3b7-143">Funkcje anonimowe</span><span class="sxs-lookup"><span data-stu-id="af3b7-143">Anonymous Functions</span></span>](../csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)
* [<span data-ttu-id="af3b7-144">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="af3b7-144">Lambda expressions</span></span>](../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)

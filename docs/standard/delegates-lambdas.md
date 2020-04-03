---
title: Delegaci i wyrażenia lambda
description: Dowiedz się, jak delegaci, które definiują typ, który określa podpis określonej metody, mogą być wywoływane bezpośrednio lub przekazywane do innej metody i wywoływane.
author: richlander
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: fe2e4b4c-6483-4106-a4b4-a33e2e306591
ms.openlocfilehash: a9ca935814d1a7f77ded5f371ccd496c3859c523
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635930"
---
# <a name="delegates-and-lambdas"></a><span data-ttu-id="7221a-103">Delegaci i wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="7221a-103">Delegates and lambdas</span></span>

<span data-ttu-id="7221a-104">Delegaci definiują typ, który określa podpis określonej metody.</span><span class="sxs-lookup"><span data-stu-id="7221a-104">Delegates define a type that specifies a particular method signature.</span></span> <span data-ttu-id="7221a-105">Metodę (statyczną lub wystąpienie), która spełnia ten podpis można przypisać do zmiennej tego typu, a następnie wywoływane bezpośrednio (z odpowiednimi argumentami) lub przekazywane jako argument się do innej metody, a następnie wywołane.</span><span class="sxs-lookup"><span data-stu-id="7221a-105">A method (static or instance) that satisfies this signature can be assigned to a variable of that type, then called directly (with the appropriate arguments) or passed as an argument itself to another method and then called.</span></span> <span data-ttu-id="7221a-106">W poniższym przykładzie pokazano delegowania wykorzystania.</span><span class="sxs-lookup"><span data-stu-id="7221a-106">The following example demonstrates delegate use.</span></span>

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

* <span data-ttu-id="7221a-107">Wiersz `public delegate string Reverse(string s);` tworzy typ delegata określonego podpisu, w tym przypadku metodę, która przyjmuje parametr ciągu, a następnie zwraca parametr ciągu.</span><span class="sxs-lookup"><span data-stu-id="7221a-107">The `public delegate string Reverse(string s);` line creates a delegate type of a certain signature, in this case a method that takes a string parameter and then returns a string parameter.</span></span>
* <span data-ttu-id="7221a-108">Metoda, `static string ReverseString(string s)` która ma dokładnie taki sam podpis jak zdefiniowany typ delegata, implementuje pełnomocnika.</span><span class="sxs-lookup"><span data-stu-id="7221a-108">The `static string ReverseString(string s)` method, which has the exact same signature as the defined delegate type, implements the delegate.</span></span>
* <span data-ttu-id="7221a-109">Wiersz `Reverse rev = ReverseString;` pokazuje, że można przypisać metodę do zmiennej odpowiedniego typu delegata.</span><span class="sxs-lookup"><span data-stu-id="7221a-109">The `Reverse rev = ReverseString;` line shows that you can assign a method to a variable of the corresponding delegate type.</span></span>
* <span data-ttu-id="7221a-110">Wiersz `Console.WriteLine(rev("a string"));` pokazuje, jak używać zmiennej typu delegata do wywoływania pełnomocnika.</span><span class="sxs-lookup"><span data-stu-id="7221a-110">The `Console.WriteLine(rev("a string"));` line demonstrates how to use a variable of a delegate type to invoke the delegate.</span></span>

<span data-ttu-id="7221a-111">Aby usprawnić proces programowania, .NET zawiera zestaw typów delegatów, które programiści mogą ponownie używać i nie trzeba tworzyć nowe typy.</span><span class="sxs-lookup"><span data-stu-id="7221a-111">In order to streamline the development process, .NET includes a set of delegate types that programmers can reuse and not have to create new types.</span></span> <span data-ttu-id="7221a-112">Te typy `Action<>` `Predicate<>`są `Func<>`i , i mogą być używane bez konieczności definiowania nowych typów delegatów.</span><span class="sxs-lookup"><span data-stu-id="7221a-112">These types are `Func<>`, `Action<>` and `Predicate<>`, and they can be used without having to define new delegate types.</span></span> <span data-ttu-id="7221a-113">Istnieją pewne różnice między trzema typami, które mają do czynienia ze sposobem, w jaki były przeznaczone do użycia:</span><span class="sxs-lookup"><span data-stu-id="7221a-113">There are some differences between the three types that have to do with the way they were intended to be used:</span></span>

* <span data-ttu-id="7221a-114">`Action<>`jest używany, gdy istnieje potrzeba wykonania akcji przy użyciu argumentów delegata.</span><span class="sxs-lookup"><span data-stu-id="7221a-114">`Action<>` is used when there is a need to perform an action using the arguments of the delegate.</span></span> <span data-ttu-id="7221a-115">Metoda, która hermetyzuje nie zwraca wartości.</span><span class="sxs-lookup"><span data-stu-id="7221a-115">The method it encapsulates does not return a value.</span></span>
* <span data-ttu-id="7221a-116">`Func<>`jest używany zwykle, gdy masz transformację pod ręką, to znaczy, że należy przekształcić argumenty delegata w inny wynik.</span><span class="sxs-lookup"><span data-stu-id="7221a-116">`Func<>` is used usually when you have a transformation on hand, that is, you need to transform the arguments of the delegate into a different result.</span></span> <span data-ttu-id="7221a-117">Projekcje są dobrym przykładem.</span><span class="sxs-lookup"><span data-stu-id="7221a-117">Projections are a good example.</span></span> <span data-ttu-id="7221a-118">Metoda, która hermetyzuje zwraca określoną wartość.</span><span class="sxs-lookup"><span data-stu-id="7221a-118">The method it encapsulates returns a specified value.</span></span>
* <span data-ttu-id="7221a-119">`Predicate<>`jest używany, gdy trzeba ustalić, czy argument spełnia warunek delegata.</span><span class="sxs-lookup"><span data-stu-id="7221a-119">`Predicate<>` is used when you need to determine if the argument satisfies the condition of the delegate.</span></span> <span data-ttu-id="7221a-120">Może być również zapisywany `Func<T, bool>`jako , co oznacza, że metoda zwraca wartość logiczną.</span><span class="sxs-lookup"><span data-stu-id="7221a-120">It can also be written as a `Func<T, bool>`, which means the method returns a boolean value.</span></span>

<span data-ttu-id="7221a-121">Możemy teraz wziąć nasz przykład powyżej i `Func<>` przepisać go przy użyciu pełnomocnika zamiast typu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="7221a-121">We can now take our example above and rewrite it using the `Func<>` delegate instead of a custom type.</span></span> <span data-ttu-id="7221a-122">Program będzie nadal działać dokładnie tak samo.</span><span class="sxs-lookup"><span data-stu-id="7221a-122">The program will continue running exactly the same.</span></span>

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

<span data-ttu-id="7221a-123">W tym prostym przykładzie o metody `Main` zdefiniowane poza metodą wydaje się nieco zbędne.</span><span class="sxs-lookup"><span data-stu-id="7221a-123">For this simple example, having a method defined outside of the `Main` method seems a bit superfluous.</span></span> <span data-ttu-id="7221a-124">.NET Framework 2.0 wprowadził pojęcie *anonimowych delegatów,* które umożliwiają tworzenie delegatów "wbudowanych" bez konieczności określania dodatkowego typu lub metody.</span><span class="sxs-lookup"><span data-stu-id="7221a-124">.NET Framework 2.0 introduced the concept of *anonymous delegates*, which let you create "inline" delegates without having to specify any additional type or method.</span></span>

<span data-ttu-id="7221a-125">W poniższym przykładzie anonimowy delegat filtruje listę tylko do parzystych liczb, a następnie drukuje je na konsoli.</span><span class="sxs-lookup"><span data-stu-id="7221a-125">In the following example, an anonymous delegate filters a list to just the even numbers and then prints them to the console.</span></span>

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

<span data-ttu-id="7221a-126">Jak widać, treść delegata jest tylko zestaw wyrażeń, jak każdy inny delegata.</span><span class="sxs-lookup"><span data-stu-id="7221a-126">As you can see, the body of the delegate is just a set of expressions, as any other delegate.</span></span> <span data-ttu-id="7221a-127">Ale zamiast oddzielnej definicji, wprowadziliśmy ją _ad hoc_ w <xref:System.Collections.Generic.List%601.FindAll%2A?displayProperty=nameWithType> naszym wezwaniu do metody.</span><span class="sxs-lookup"><span data-stu-id="7221a-127">But instead of it being a separate definition, we've introduced it _ad hoc_ in our call to the <xref:System.Collections.Generic.List%601.FindAll%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="7221a-128">Jednak nawet przy takim podejściu nadal istnieje wiele kodu, który możemy wyrzucić.</span><span class="sxs-lookup"><span data-stu-id="7221a-128">However, even with this approach, there is still much code that we can throw away.</span></span> <span data-ttu-id="7221a-129">To jest, gdy *wyrażenia lambda* wchodzą w grę.</span><span class="sxs-lookup"><span data-stu-id="7221a-129">This is where *lambda expressions* come into play.</span></span> <span data-ttu-id="7221a-130">Wyrażenia Lambda, lub po prostu "lambdas" w skrócie, zostały wprowadzone w języku C# 3.0 jako jeden z podstawowych bloków konstrukcyjnych języka zintegrowane zapytanie (LINQ).</span><span class="sxs-lookup"><span data-stu-id="7221a-130">Lambda expressions, or just "lambdas" for short, were introduced in C# 3.0 as one of the core building blocks of Language Integrated Query (LINQ).</span></span> <span data-ttu-id="7221a-131">Są one po prostu bardziej wygodną składnią przy użyciu delegatów.</span><span class="sxs-lookup"><span data-stu-id="7221a-131">They are just a more convenient syntax for using delegates.</span></span> <span data-ttu-id="7221a-132">Deklarują podpis i treść metody, ale nie mają formalnej tożsamości, chyba że są przypisane do delegata.</span><span class="sxs-lookup"><span data-stu-id="7221a-132">They declare a signature and a method body, but don't have a formal identity of their own, unless they are assigned to a delegate.</span></span> <span data-ttu-id="7221a-133">W przeciwieństwie do delegatów, mogą być bezpośrednio przypisane jako po lewej stronie rejestracji zdarzeń lub w różnych klauzul linq i metod.</span><span class="sxs-lookup"><span data-stu-id="7221a-133">Unlike delegates, they can be directly assigned as the left-hand side of event registration or in various LINQ clauses and methods.</span></span>

<span data-ttu-id="7221a-134">Ponieważ wyrażenie lambda jest tylko inny sposób określania delegata, powinniśmy być w stanie przepisać powyższe próbki do użycia wyrażenia lambda zamiast anonimowego delegata.</span><span class="sxs-lookup"><span data-stu-id="7221a-134">Since a lambda expression is just another way of specifying a delegate, we should be able to rewrite the above sample to use a lambda expression instead of an anonymous delegate.</span></span>

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

<span data-ttu-id="7221a-135">W poprzednim przykładzie użytym wyrażeniem `i => i % 2 == 0`lambda jest .</span><span class="sxs-lookup"><span data-stu-id="7221a-135">In the preceding example, the lambda expression used is `i => i % 2 == 0`.</span></span> <span data-ttu-id="7221a-136">Ponownie jest to tylko wygodna składnia do korzystania z delegatów.</span><span class="sxs-lookup"><span data-stu-id="7221a-136">Again, it is just a convenient syntax for using delegates.</span></span> <span data-ttu-id="7221a-137">To, co dzieje się w ramach okładek, jest podobne do tego, co dzieje się z anonimowym pełnomocnikiem.</span><span class="sxs-lookup"><span data-stu-id="7221a-137">What happens under the covers is similar to what happens with the anonymous delegate.</span></span>

<span data-ttu-id="7221a-138">Ponownie lambdas są tylko delegatów, co oznacza, że mogą być używane jako program obsługi zdarzeń bez żadnych problemów, jak pokazuje poniższy fragment kodu.</span><span class="sxs-lookup"><span data-stu-id="7221a-138">Again, lambdas are just delegates, which means that they can be used as an event handler without any problems, as the following code snippet illustrates.</span></span>

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

<span data-ttu-id="7221a-139">Operator `+=` w tym kontekście służy do subskrybowania [zdarzenia](../../docs/csharp/language-reference/keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="7221a-139">The `+=` operator in this context is used to subscribe to an [event](../../docs/csharp/language-reference/keywords/event.md).</span></span> <span data-ttu-id="7221a-140">Aby uzyskać więcej informacji, zobacz [Jak subskrybować wydarzenia i anulować subskrypcję .](../../docs/csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)</span><span class="sxs-lookup"><span data-stu-id="7221a-140">For more information, see [How to subscribe to and unsubscribe from events](../../docs/csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="further-reading-and-resources"></a><span data-ttu-id="7221a-141">Dalsze czytanie i zasoby</span><span class="sxs-lookup"><span data-stu-id="7221a-141">Further reading and resources</span></span>

* [<span data-ttu-id="7221a-142">Delegaty</span><span class="sxs-lookup"><span data-stu-id="7221a-142">Delegates</span></span>](../../docs/csharp/programming-guide/delegates/index.md)
* [<span data-ttu-id="7221a-143">Funkcje anonimowe</span><span class="sxs-lookup"><span data-stu-id="7221a-143">Anonymous Functions</span></span>](../../docs/csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)
* [<span data-ttu-id="7221a-144">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="7221a-144">Lambda expressions</span></span>](../../docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)

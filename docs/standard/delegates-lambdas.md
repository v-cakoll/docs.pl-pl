---
title: Delegaci i wyrażenia lambda
description: Dowiedz się, jak delegaci definiują typ, który określa podpis określonej metody, który może być wywoływany bezpośrednio lub przekazywany do innej metody i wywoływany.
author: richlander
ms.author: wiwagn
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: fe2e4b4c-6483-4106-a4b4-a33e2e306591
ms.openlocfilehash: 34bfa4c6007ec771f784e927675f4e24d52e194f
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391237"
---
# <a name="delegates-and-lambdas"></a><span data-ttu-id="2221f-103">Delegaci i wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="2221f-103">Delegates and lambdas</span></span>

<span data-ttu-id="2221f-104">Delegaci definiują typ, który określa podpis określonej metody.</span><span class="sxs-lookup"><span data-stu-id="2221f-104">Delegates define a type, which specify a particular method signature.</span></span> <span data-ttu-id="2221f-105">Metodę (statyczną lub wystąpienie), która spełnia ten podpis można przypisać do zmiennej tego typu, a następnie wywoływane bezpośrednio (z odpowiednimi argumentami) lub przekazywane jako argument się do innej metody, a następnie wywołane.</span><span class="sxs-lookup"><span data-stu-id="2221f-105">A method (static or instance) that satisfies this signature can be assigned to a variable of that type, then called directly (with the appropriate arguments) or passed as an argument itself to another method and then called.</span></span> <span data-ttu-id="2221f-106">W poniższym przykładzie pokazano delegowania wykorzystania.</span><span class="sxs-lookup"><span data-stu-id="2221f-106">The following example demonstrates delegate use.</span></span>

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

* <span data-ttu-id="2221f-107">Wiersz `public delegate string Reverse(string s);` tworzy typ delegata określonego podpisu, w tym przypadku metodę, która przyjmuje parametr ciągu, a następnie zwraca parametr ciągu.</span><span class="sxs-lookup"><span data-stu-id="2221f-107">The `public delegate string Reverse(string s);` line creates a delegate type of a certain signature, in this case a method that takes a string parameter and then returns a string parameter.</span></span>
* <span data-ttu-id="2221f-108">Metoda, `static string ReverseString(string s)` która ma dokładnie taki sam podpis jak zdefiniowany typ delegata, implementuje pełnomocnika.</span><span class="sxs-lookup"><span data-stu-id="2221f-108">The `static string ReverseString(string s)` method, which has the exact same signature as the defined delegate type, implements the delegate.</span></span>
* <span data-ttu-id="2221f-109">Wiersz `Reverse rev = ReverseString;` pokazuje, że można przypisać metodę do zmiennej odpowiedniego typu delegata.</span><span class="sxs-lookup"><span data-stu-id="2221f-109">The `Reverse rev = ReverseString;` line shows that you can assign a method to a variable of the corresponding delegate type.</span></span>
* <span data-ttu-id="2221f-110">Wiersz `Console.WriteLine(rev("a string"));` pokazuje, jak używać zmiennej typu delegata do wywoływania pełnomocnika.</span><span class="sxs-lookup"><span data-stu-id="2221f-110">The `Console.WriteLine(rev("a string"));` line demonstrates how to use a variable of a delegate type to invoke the delegate.</span></span>

<span data-ttu-id="2221f-111">Aby usprawnić proces programowania, .NET zawiera zestaw typów delegatów, które programiści mogą ponownie używać i nie trzeba tworzyć nowe typy.</span><span class="sxs-lookup"><span data-stu-id="2221f-111">In order to streamline the development process, .NET includes a set of delegate types that programmers can reuse and not have to create new types.</span></span> <span data-ttu-id="2221f-112">Są `Func<>`to `Action<>` `Predicate<>`, i , i mogą być używane w różnych miejscach w interfejsach API platformy .NET bez konieczności definiowania nowych typów delegatów.</span><span class="sxs-lookup"><span data-stu-id="2221f-112">These are `Func<>`, `Action<>` and `Predicate<>`, and they can be used in various places throughout the .NET APIs without the need to define new delegate types.</span></span> <span data-ttu-id="2221f-113">Oczywiście, istnieją pewne różnice między tymi trzema, jak widać w ich podpisów, które w większości mają do czynienia ze sposobem, w jaki miały być używane:</span><span class="sxs-lookup"><span data-stu-id="2221f-113">Of course, there are some differences between the three as you will see in their signatures which mostly have to do with the way they were meant to be used:</span></span>

* <span data-ttu-id="2221f-114">`Action<>`jest używany, gdy istnieje potrzeba wykonania akcji przy użyciu argumentów delegata.</span><span class="sxs-lookup"><span data-stu-id="2221f-114">`Action<>` is used when there is a need to perform an action using the arguments of the delegate.</span></span> <span data-ttu-id="2221f-115">Metoda, która hermetyzuje nie zwraca wartości.</span><span class="sxs-lookup"><span data-stu-id="2221f-115">The method it encapsulates does not return a value.</span></span>
* <span data-ttu-id="2221f-116">`Func<>`jest używany zwykle, gdy masz transformację pod ręką, to znaczy, że należy przekształcić argumenty delegata w inny wynik.</span><span class="sxs-lookup"><span data-stu-id="2221f-116">`Func<>` is used usually when you have a transformation on hand, that is, you need to transform the arguments of the delegate into a different result.</span></span> <span data-ttu-id="2221f-117">Prognozy są tego najlepszym przykładem.</span><span class="sxs-lookup"><span data-stu-id="2221f-117">Projections are a prime example of this.</span></span> <span data-ttu-id="2221f-118">Metoda, która hermetyzuje zwraca określoną wartość.</span><span class="sxs-lookup"><span data-stu-id="2221f-118">The method it encapsulates returns a specified value.</span></span>
* <span data-ttu-id="2221f-119">`Predicate<>`jest używany, gdy trzeba ustalić, czy argument spełnia warunek delegata.</span><span class="sxs-lookup"><span data-stu-id="2221f-119">`Predicate<>` is used when you need to determine if the argument satisfies the condition of the delegate.</span></span> <span data-ttu-id="2221f-120">Może być również zapisywany `Func<T, bool>`jako , co oznacza, że metoda zwraca wartość logiczną.</span><span class="sxs-lookup"><span data-stu-id="2221f-120">It can also be written as a `Func<T, bool>`, which means the method returns a boolean value.</span></span>

<span data-ttu-id="2221f-121">Możemy teraz wziąć nasz przykład powyżej i `Func<>` przepisać go przy użyciu pełnomocnika zamiast typu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="2221f-121">We can now take our example above and rewrite it using the `Func<>` delegate instead of a custom type.</span></span> <span data-ttu-id="2221f-122">Program będzie nadal działać dokładnie tak samo.</span><span class="sxs-lookup"><span data-stu-id="2221f-122">The program will continue running exactly the same.</span></span>

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

<span data-ttu-id="2221f-123">W tym prostym przykładzie o metody `Main` zdefiniowane poza metodą wydaje się nieco zbędne.</span><span class="sxs-lookup"><span data-stu-id="2221f-123">For this simple example, having a method defined outside of the `Main` method seems a bit superfluous.</span></span> <span data-ttu-id="2221f-124">To z tego powodu .NET Framework 2.0 wprowadził pojęcie **anonimowych delegatów**.</span><span class="sxs-lookup"><span data-stu-id="2221f-124">It is because of this that .NET Framework 2.0 introduced the concept of **anonymous delegates**.</span></span> <span data-ttu-id="2221f-125">Dzięki ich wsparciu możesz tworzyć delegatów "wbudowanych" bez konieczności określania dodatkowego typu lub metody.</span><span class="sxs-lookup"><span data-stu-id="2221f-125">With their support you are able to create "inline" delegates without having to specify any additional type or method.</span></span> <span data-ttu-id="2221f-126">Po prostu wbudowana definicja delegata tam, gdzie jej potrzebujesz.</span><span class="sxs-lookup"><span data-stu-id="2221f-126">You simply inline the definition of the delegate where you need it.</span></span>

<span data-ttu-id="2221f-127">Na przykład przełączymy go i użyjemy naszego anonimowego delegata, aby odfiltrować listę tylko parzystych liczb, a następnie wydrukować je na konsoli.</span><span class="sxs-lookup"><span data-stu-id="2221f-127">For an example, we are going to switch it up and use our anonymous delegate to filter out a list of only even numbers and then print them to the console.</span></span>

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

<span data-ttu-id="2221f-128">Jak widać, treść delegata jest tylko zestaw wyrażeń, jak każdy inny delegata.</span><span class="sxs-lookup"><span data-stu-id="2221f-128">As you can see, the body of the delegate is just a set of expressions, as any other delegate.</span></span> <span data-ttu-id="2221f-129">Ale zamiast oddzielnej definicji, wprowadziliśmy ją _ad hoc_ w <xref:System.Collections.Generic.List%601.FindAll%2A?displayProperty=nameWithType> naszym wezwaniu do metody.</span><span class="sxs-lookup"><span data-stu-id="2221f-129">But instead of it being a separate definition, we’ve introduced it _ad hoc_ in our call to the <xref:System.Collections.Generic.List%601.FindAll%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="2221f-130">Jednak nawet przy takim podejściu nadal istnieje wiele kodu, który możemy wyrzucić.</span><span class="sxs-lookup"><span data-stu-id="2221f-130">However, even with this approach, there is still much code that we can throw away.</span></span> <span data-ttu-id="2221f-131">To jest, gdy **wyrażenia lambda** wchodzą w grę.</span><span class="sxs-lookup"><span data-stu-id="2221f-131">This is where **lambda expressions** come into play.</span></span>

<span data-ttu-id="2221f-132">Wyrażenia Lambda, lub po prostu "lambdas" w skrócie, zostały wprowadzone najpierw w języku C# 3.0, jako jeden z podstawowych bloków konstrukcyjnych języka zintegrowane zapytanie (LINQ).</span><span class="sxs-lookup"><span data-stu-id="2221f-132">Lambda expressions, or just "lambdas" for short, were introduced first in C# 3.0, as one of the core building blocks of Language Integrated Query (LINQ).</span></span> <span data-ttu-id="2221f-133">Są one po prostu bardziej wygodną składnią przy użyciu delegatów.</span><span class="sxs-lookup"><span data-stu-id="2221f-133">They are just a more convenient syntax for using delegates.</span></span> <span data-ttu-id="2221f-134">Deklarują podpis i treść metody, ale nie mają formalnej tożsamości, chyba że są przypisane do delegata.</span><span class="sxs-lookup"><span data-stu-id="2221f-134">They declare a signature and a method body, but don’t have a formal identity of their own, unless they are assigned to a delegate.</span></span> <span data-ttu-id="2221f-135">W przeciwieństwie do delegatów, mogą być bezpośrednio przypisane jako po lewej stronie rejestracji zdarzeń lub w różnych klauzul linq i metod.</span><span class="sxs-lookup"><span data-stu-id="2221f-135">Unlike delegates, they can be directly assigned as the left-hand side of event registration or in various LINQ clauses and methods.</span></span>

<span data-ttu-id="2221f-136">Ponieważ wyrażenie lambda jest tylko inny sposób określania delegata, powinniśmy być w stanie przepisać powyższe próbki do użycia wyrażenia lambda zamiast anonimowego delegata.</span><span class="sxs-lookup"><span data-stu-id="2221f-136">Since a lambda expression is just another way of specifying a delegate, we should be able to rewrite the above sample to use a lambda expression instead of an anonymous delegate.</span></span>

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

<span data-ttu-id="2221f-137">W poprzednim przykładzie użytym wyrażeniem `i => i % 2 == 0`lambda jest .</span><span class="sxs-lookup"><span data-stu-id="2221f-137">In the preceding example, the lambda expression used is `i => i % 2 == 0`.</span></span> <span data-ttu-id="2221f-138">Ponownie jest to po prostu **bardzo** wygodna składnia do korzystania z delegatów, więc to, co dzieje się w ramach okładek jest podobne do tego, co dzieje się z anonimowym pełnomocnikiem.</span><span class="sxs-lookup"><span data-stu-id="2221f-138">Again, it is just a **very** convenient syntax for using delegates, so what happens under the covers is similar to what happens with the anonymous delegate.</span></span>

<span data-ttu-id="2221f-139">Ponownie lambdas są tylko delegatów, co oznacza, że mogą być używane jako program obsługi zdarzeń bez żadnych problemów, jak pokazuje poniższy fragment kodu.</span><span class="sxs-lookup"><span data-stu-id="2221f-139">Again, lambdas are just delegates, which means that they can be used as an event handler without any problems, as the following code snippet illustrates.</span></span>

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

<span data-ttu-id="2221f-140">Operator `+=` w tym kontekście służy do subskrybowania [zdarzenia](../../docs/csharp/language-reference/keywords/event.md).</span><span class="sxs-lookup"><span data-stu-id="2221f-140">The `+=` operator in this context is used to subscribe to an [event](../../docs/csharp/language-reference/keywords/event.md).</span></span> <span data-ttu-id="2221f-141">Aby uzyskać więcej informacji, zobacz [Jak subskrybować wydarzenia i anulować subskrypcję .](../../docs/csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md)</span><span class="sxs-lookup"><span data-stu-id="2221f-141">For more information, see [How to subscribe to and unsubscribe from events](../../docs/csharp/programming-guide/events/how-to-subscribe-to-and-unsubscribe-from-events.md).</span></span>

## <a name="further-reading-and-resources"></a><span data-ttu-id="2221f-142">Dalsze czytanie i zasoby</span><span class="sxs-lookup"><span data-stu-id="2221f-142">Further reading and resources</span></span>

* [<span data-ttu-id="2221f-143">Delegaty</span><span class="sxs-lookup"><span data-stu-id="2221f-143">Delegates</span></span>](../../docs/csharp/programming-guide/delegates/index.md)
* [<span data-ttu-id="2221f-144">Funkcje anonimowe</span><span class="sxs-lookup"><span data-stu-id="2221f-144">Anonymous Functions</span></span>](../../docs/csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)
* [<span data-ttu-id="2221f-145">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="2221f-145">Lambda expressions</span></span>](../../docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)

---
title: "Delegaci i wyrażeń lambda"
description: "Dowiedz się, jak delegatów Definiowanie typu, które określą podpisu konkretnej metody, które można wywołać bezpośrednio lub przekazana do innej metody i wywołać."
keywords: .NET, .NET core
author: richlander
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: fe2e4b4c-6483-4106-a4b4-a33e2e306591
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d418733ada67a1cb751bbfa74afee2eeeee04976
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="delegates-and-lambdas"></a><span data-ttu-id="c545d-104">Delegaci i wyrażeń lambda</span><span class="sxs-lookup"><span data-stu-id="c545d-104">Delegates and lambdas</span></span>

<span data-ttu-id="c545d-105">Obiekty delegowane Definiowanie typu, które określą sygnatury określonej metody.</span><span class="sxs-lookup"><span data-stu-id="c545d-105">Delegates define a type, which specify a particular method signature.</span></span> <span data-ttu-id="c545d-106">Metody (statyczny lub wystąpienia) odpowiadającej tego podpisu może być przypisany do zmiennej tego typu, a następnie wywołać bezpośrednio (za pomocą odpowiednie argumenty) lub przekazanego jako argument się do innej metody i następnie wywołuje.</span><span class="sxs-lookup"><span data-stu-id="c545d-106">A method (static or instance) that satisfies this signature can be assigned to a variable of that type, then called directly (with the appropriate arguments) or passed as an argument itself to another method and then called.</span></span> <span data-ttu-id="c545d-107">W poniższym przykładzie pokazano Użyj delegata.</span><span class="sxs-lookup"><span data-stu-id="c545d-107">The following example demonstrates delegate use.</span></span>

```csharp
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

*   <span data-ttu-id="c545d-108">W wierszu 4 utworzymy typem obiektu delegowanego niektórych podpisu w tym przypadku metoda który przyjmuje parametr typu string i zwraca parametr typu string.</span><span class="sxs-lookup"><span data-stu-id="c545d-108">On line 4 we create a delegate type of a certain signature, in this case a method that takes a string parameter and then returns a string parameter.</span></span>
*   <span data-ttu-id="c545d-109">W wierszu 6 definiujemy implementacji delegata dzięki udostępnieniu metod, który ma dokładnie takiego samego podpisu.</span><span class="sxs-lookup"><span data-stu-id="c545d-109">On line 6, we define the implementation of the delegate by providing a method that has the exact same signature.</span></span>
*   <span data-ttu-id="c545d-110">W wierszu 13 metody jest przypisany do typu, który odpowiada `Reverse` delegowanie.</span><span class="sxs-lookup"><span data-stu-id="c545d-110">On line 13, the method is assigned to a type that conforms to the `Reverse` delegate.</span></span>
*   <span data-ttu-id="c545d-111">Na koniec wiersza 15 możemy wywołać delegata przekazywanie ciągu do wycofania.</span><span class="sxs-lookup"><span data-stu-id="c545d-111">Finally, on line 15 we invoke the delegate passing a string to be reversed.</span></span>

<span data-ttu-id="c545d-112">W celu uproszczenia procesu tworzenia, .NET zawiera zestaw typów delegatów, które programiści mogą ponownie wykorzystać i nie trzeba tworzyć nowych typów.</span><span class="sxs-lookup"><span data-stu-id="c545d-112">In order to streamline the development process, .NET includes a set of delegate types that programmers can reuse and not have to create new types.</span></span> <span data-ttu-id="c545d-113">Są to `Func<>`, `Action<>` i `Predicate<>`, i mogą być używane w różnych miejscach interfejsów API architektury .NET bez konieczności do definiowania nowych typów delegata.</span><span class="sxs-lookup"><span data-stu-id="c545d-113">These are `Func<>`, `Action<>` and `Predicate<>`, and they can be used in various places throughout the .NET APIs without the need to define new delegate types.</span></span> <span data-ttu-id="c545d-114">Oczywiście są pewne różnice między trzy jak widać w ich sygnaturach, które przede wszystkim ze sposobem, które zostały one przeznaczone do użycia:</span><span class="sxs-lookup"><span data-stu-id="c545d-114">Of course, there are some differences between the three as you will see in their signatures which mostly have to do with the way they were meant to be used:</span></span>

*   <span data-ttu-id="c545d-115">`Action<>`jest używany, gdy istnieje potrzeba wykonania akcji na podstawie argumentów delegata.</span><span class="sxs-lookup"><span data-stu-id="c545d-115">`Action<>` is used when there is a need to perform an action using the arguments of the delegate.</span></span>
*   <span data-ttu-id="c545d-116">`Func<>`jest używana zazwyczaj, gdy masz transformację dostępnych produktów, oznacza to, należy przekształcić argumenty delegata w innych wyników.</span><span class="sxs-lookup"><span data-stu-id="c545d-116">`Func<>` is used usually when you have a transformation on hand, that is, you need to transform the arguments of the delegate into a different result.</span></span> <span data-ttu-id="c545d-117">Projekcje są podstawowym przykładem.</span><span class="sxs-lookup"><span data-stu-id="c545d-117">Projections are a prime example of this.</span></span>
*   <span data-ttu-id="c545d-118">`Predicate<>`jest używany podczas należy ustalić, jeśli argument spełnia warunek delegata.</span><span class="sxs-lookup"><span data-stu-id="c545d-118">`Predicate<>` is used when you need to determine if the argument satisfies the condition of the delegate.</span></span> <span data-ttu-id="c545d-119">Można również będą zapisywane jako `Func<T, bool>`.</span><span class="sxs-lookup"><span data-stu-id="c545d-119">It can also be written as a `Func<T, bool>`.</span></span>

<span data-ttu-id="c545d-120">Możemy teraz pobrać naszym przykładzie powyżej i przepisywania za pomocą `Func<>` delegować zamiast typu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="c545d-120">We can now take our example above and rewrite it using the `Func<>` delegate instead of a custom type.</span></span> <span data-ttu-id="c545d-121">Program nadal będzie działać, dokładnie tak samo.</span><span class="sxs-lookup"><span data-stu-id="c545d-121">The program will continue running exactly the same.</span></span>

```csharp
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

<span data-ttu-id="c545d-122">W tym przykładzie prosty o metoda poza metodą Main() wydaje się nieco zbędny.</span><span class="sxs-lookup"><span data-stu-id="c545d-122">For this simple example, having a method defined outside of the Main() method seems a bit superfluous.</span></span> <span data-ttu-id="c545d-123">Jest w związku z tym, że .NET Framework 2.0 wprowadzono koncepcję **anonimowych delegatów**.</span><span class="sxs-lookup"><span data-stu-id="c545d-123">It is because of this that .NET Framework 2.0 introduced the concept of **anonymous delegates**.</span></span> <span data-ttu-id="c545d-124">Z pomocy technicznej jest możliwość tworzenia delegatów "wbudowany" bez konieczności określania wszelkie dodatkowe typu lub metody.</span><span class="sxs-lookup"><span data-stu-id="c545d-124">With their support you are able to create "inline" delegates without having to specify any additional type or method.</span></span> <span data-ttu-id="c545d-125">Możesz po prostu wbudowanej definicji delegata, w których należy.</span><span class="sxs-lookup"><span data-stu-id="c545d-125">You simply inline the definition of the delegate where you need it.</span></span>

<span data-ttu-id="c545d-126">Na przykład zamierzamy przełączyć go się i użyć naszych anonimowe delegata do odfiltrowywania listę tylko liczby parzyste i wydrukuj je w konsoli.</span><span class="sxs-lookup"><span data-stu-id="c545d-126">For an example, we are going to switch it up and use our anonymous delegate to filter out a list of only even numbers and then print them to the console.</span></span>

```csharp
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
      delegate(int no)
      {
          return (no%2 == 0);
      }
    );

    foreach (var item in result)
    {
        Console.WriteLine(item);
    }
  }
}
```

<span data-ttu-id="c545d-127">Zwróć uwagę, wyróżnione wiersze.</span><span class="sxs-lookup"><span data-stu-id="c545d-127">Notice the highlighted lines.</span></span> <span data-ttu-id="c545d-128">Jak widać, treść delegata jest tylko zestaw wyrażeń, co inne delegata.</span><span class="sxs-lookup"><span data-stu-id="c545d-128">As you can see, the body of the delegate is just a set of expressions, as any other delegate.</span></span> <span data-ttu-id="c545d-129">Ale gdy jest osobnym definicji, a nie dodaliśmy go _ad hoc_ w naszym wywołaniu `FindAll()` metody `List<T>` typu.</span><span class="sxs-lookup"><span data-stu-id="c545d-129">But instead of it being a separate definition, we’ve introduced it _ad hoc_ in our call to the `FindAll()` method of the `List<T>` type.</span></span>

<span data-ttu-id="c545d-130">Jednak nawet w przypadku tej metody jest nadal większej ilości kodu, który mamy wyrzucać.</span><span class="sxs-lookup"><span data-stu-id="c545d-130">However, even with this approach, there is still much code that we can throw away.</span></span> <span data-ttu-id="c545d-131">Jest to, gdy **wyrażenia lambda** wchodzić w grę.</span><span class="sxs-lookup"><span data-stu-id="c545d-131">This is where **lambda expressions** come into play.</span></span>

<span data-ttu-id="c545d-132">Wyrażenia lambda lub po prostu "wyrażeń lambda" skrócie, wprowadzono najpierw w języku C# 3.0 jako jeden z podstawowych bloków konstrukcyjnych z języka zintegrowane zapytania (LINQ).</span><span class="sxs-lookup"><span data-stu-id="c545d-132">Lambda expressions, or just "lambdas" for short, were introduced first in C# 3.0, as one of the core building blocks of Language Integrated Query (LINQ).</span></span> <span data-ttu-id="c545d-133">Są one tylko wygodniejsze składnia przy użyciu delegatów.</span><span class="sxs-lookup"><span data-stu-id="c545d-133">They are just a more convenient syntax for using delegates.</span></span> <span data-ttu-id="c545d-134">One zadeklarować podpisu i treści metody, ale nie ma formalnych tożsamości we własnym, o ile nie są przypisane do delegata.</span><span class="sxs-lookup"><span data-stu-id="c545d-134">They declare a signature and a method body, but don’t have an formal identity of their own, unless they are assigned to a delegate.</span></span> <span data-ttu-id="c545d-135">W przeciwieństwie do delegatów bezpośrednio przypisać jako po lewej stronie rejestracji zdarzeń lub w wielu klauzul Linq i metod.</span><span class="sxs-lookup"><span data-stu-id="c545d-135">Unlike delegates, they can be directly assigned as the left-hand side of event registration or in various Linq clauses and methods.</span></span>

<span data-ttu-id="c545d-136">Wyrażenie lambda jest po prostu innym sposobem określania delegata, możemy powinno być możliwe do edycji w powyższym przykładzie, aby użyć wyrażenia lambda zamiast anonimowego obiektu delegowanego.</span><span class="sxs-lookup"><span data-stu-id="c545d-136">Since a lambda expression is just another way of specifying a delegate, we should be able to rewrite the above sample to use a lambda expression instead of an anonymous delegate.</span></span>

```csharp
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

<span data-ttu-id="c545d-137">Jeśli Spójrz na wyróżnione wiersze widać, jak wygląda wyrażenia lambda.</span><span class="sxs-lookup"><span data-stu-id="c545d-137">If you take a look at the highlighted lines, you can see how a lambda expression looks like.</span></span> <span data-ttu-id="c545d-138">Ponownie, to po prostu **bardzo** wygodny składnia przy użyciu delegatów, co się stanie, w obszarze obejmuje przypomina co się dzieje z anonimowego obiektem delegowanym.</span><span class="sxs-lookup"><span data-stu-id="c545d-138">Again, it is just a **very** convenient syntax for using delegates, so what happens under the covers is similar to what happens with the anonymous delegate.</span></span>

<span data-ttu-id="c545d-139">Ponownie wyrażenia lambda są tylko delegatów, co oznacza może być używany jako program obsługi zdarzeń bez problemów, jak pokazano w poniższy fragment kodu.</span><span class="sxs-lookup"><span data-stu-id="c545d-139">Again, lambdas are just delegates, which means that they can be used as an event handler without any problems, as the following code snippet illustrates.</span></span>

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

## <a name="further-reading-and-resources"></a><span data-ttu-id="c545d-140">Dalsze informacje i zasoby</span><span class="sxs-lookup"><span data-stu-id="c545d-140">Further reading and resources</span></span>

*   [<span data-ttu-id="c545d-141">Delegaci</span><span class="sxs-lookup"><span data-stu-id="c545d-141">Delegates</span></span>](../../docs/csharp/programming-guide/delegates/index.md)
*   [<span data-ttu-id="c545d-142">Funkcje anonimowe</span><span class="sxs-lookup"><span data-stu-id="c545d-142">Anonymous Functions</span></span>](../../docs/csharp/programming-guide/statements-expressions-operators/anonymous-functions.md)
*   [<span data-ttu-id="c545d-143">Wyrażenia lambda</span><span class="sxs-lookup"><span data-stu-id="c545d-143">Lambda expressions</span></span>](../../docs/csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)

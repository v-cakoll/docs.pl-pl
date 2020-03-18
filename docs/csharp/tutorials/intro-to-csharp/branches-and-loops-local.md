---
title: Gałęzie i pętle — wprowadzenie do samouczka języka C#
description: W tym samouczku o gałęziach i pętlach piszesz kod Języka C#, aby eksplorować składnię języka, która obsługuje gałęzie warunkowe i pętle do wielokrotnego wykonywania instrukcji.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: 44b634e3c2120116ee7fd66770398a6b66c8ed8c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "73739125"
---
# <a name="learn-conditional-logic-with-branch-and-loop-statements"></a><span data-ttu-id="ae550-103">Poznaj logikę warunkową za pomocą instrukcji gałęzi i pętli</span><span class="sxs-lookup"><span data-stu-id="ae550-103">Learn conditional logic with branch and loop statements</span></span>

<span data-ttu-id="ae550-104">W tym samouczku nauczy cię, jak napisać kod, który sprawdza zmienne i zmienia ścieżkę wykonywania na podstawie tych zmiennych.</span><span class="sxs-lookup"><span data-stu-id="ae550-104">This tutorial teaches you how to write code that examines variables and changes the execution path based on those variables.</span></span> <span data-ttu-id="ae550-105">Piszesz kod C# i zobaczyć wyniki kompilacji i uruchamiania go.</span><span class="sxs-lookup"><span data-stu-id="ae550-105">You write C# code and see the results of compiling and running it.</span></span> <span data-ttu-id="ae550-106">Samouczek zawiera serię lekcji, które eksplorują rozgałęzienia i pętli konstrukcje w języku C#.</span><span class="sxs-lookup"><span data-stu-id="ae550-106">The tutorial contains a series of lessons that explore branching and looping constructs in C#.</span></span> <span data-ttu-id="ae550-107">Te lekcje umożliwiają poznanie podstaw języka C#.</span><span class="sxs-lookup"><span data-stu-id="ae550-107">These lessons teach you the fundamentals of the C# language.</span></span>

<span data-ttu-id="ae550-108">Ten samouczek oczekuje, że masz komputer, którego można użyć do tworzenia.</span><span class="sxs-lookup"><span data-stu-id="ae550-108">This tutorial expects you to have a machine you can use for development.</span></span> <span data-ttu-id="ae550-109">Samouczek .NET [Hello World w 10 minut](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) zawiera instrukcje dotyczące konfigurowania lokalnego środowiska programistycznego w systemie Windows, Linux lub macOS.</span><span class="sxs-lookup"><span data-stu-id="ae550-109">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span> <span data-ttu-id="ae550-110">Szybki przegląd poleceń, których będziesz używać, znajduje się w [obszarze Zaznajomij się z narzędziami programistycznymi](local-environment.md) z łączami do szczegółowych informacji.</span><span class="sxs-lookup"><span data-stu-id="ae550-110">A quick overview of the commands you'll use is in the [Become familiar with the development tools](local-environment.md) with links to more details.</span></span>

## <a name="make-decisions-using-the-if-statement"></a><span data-ttu-id="ae550-111">Podejmuj `if` decyzje za pomocą instrukcji</span><span class="sxs-lookup"><span data-stu-id="ae550-111">Make decisions using the `if` statement</span></span>

<span data-ttu-id="ae550-112">Utwórz katalog o nazwie *branches-tutorial*.</span><span class="sxs-lookup"><span data-stu-id="ae550-112">Create a directory named *branches-tutorial*.</span></span> <span data-ttu-id="ae550-113">Upewnij się, że bieżący katalog i uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="ae550-113">Make that the current directory and run the following command:</span></span>

```dotnetcli
dotnet new console -n BranchesAndLoops -o .
```

<span data-ttu-id="ae550-114">To polecenie tworzy nową aplikację konsoli .NET Core w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="ae550-114">This command creates a new .NET Core console application in the current directory.</span></span>

<span data-ttu-id="ae550-115">Otwórz *Program.cs* w ulubionym edytorze `Console.WriteLine("Hello World!");` i zastąp wiersz następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="ae550-115">Open *Program.cs* in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following code:</span></span>

```csharp
int a = 5;
int b = 6;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10.");
```

<span data-ttu-id="ae550-116">Wypróbuj `dotnet run` ten kod, wpisując w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="ae550-116">Try this code by typing `dotnet run` in your console window.</span></span> <span data-ttu-id="ae550-117">Powinien zostać wyświetlony komunikat "Odpowiedź jest większa niż 10".</span><span class="sxs-lookup"><span data-stu-id="ae550-117">You should see the message "The answer is greater than 10."</span></span> <span data-ttu-id="ae550-118">wydrukowane na konsoli.</span><span class="sxs-lookup"><span data-stu-id="ae550-118">printed to your console.</span></span>

<span data-ttu-id="ae550-119">Zmodyfikuj deklarację zmiennej `b`, tak aby suma była mniejsza niż 10:</span><span class="sxs-lookup"><span data-stu-id="ae550-119">Modify the declaration of `b` so that the sum is less than 10:</span></span>

```csharp
int b = 3;
```

<span data-ttu-id="ae550-120">Wpisz `dotnet run` ponownie.</span><span class="sxs-lookup"><span data-stu-id="ae550-120">Type `dotnet run` again.</span></span> <span data-ttu-id="ae550-121">Ponieważ odpowiedź jest mniejsza niż 10, nic nie zostanie wyświetlone.</span><span class="sxs-lookup"><span data-stu-id="ae550-121">Because the answer is less than 10, nothing is printed.</span></span> <span data-ttu-id="ae550-122">Testowany **warunek** ma wartość false.</span><span class="sxs-lookup"><span data-stu-id="ae550-122">The **condition** you're testing is false.</span></span> <span data-ttu-id="ae550-123">Nie ma żadnego kodu do wykonania, ponieważ napisano kod tylko dla jednej z możliwych gałęzi instrukcji `if`: wykonywanej dla wartości true.</span><span class="sxs-lookup"><span data-stu-id="ae550-123">You don't have any code to execute because you've only written one of the possible branches for an `if` statement: the true branch.</span></span>

> [!TIP]
> <span data-ttu-id="ae550-124">Podczas nauki języka C# (lub dowolnego języka programowania) będziesz robić błędy przy pisaniu kodu.</span><span class="sxs-lookup"><span data-stu-id="ae550-124">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="ae550-125">Kompilator znajdzie i zgłosi błędy.</span><span class="sxs-lookup"><span data-stu-id="ae550-125">The compiler will find and report the errors.</span></span> <span data-ttu-id="ae550-126">Przyjrzyj się uważnie danych wyjściowych błędu i kod, który wygenerował błąd.</span><span class="sxs-lookup"><span data-stu-id="ae550-126">Look closely at the error output and the code that generated the error.</span></span> <span data-ttu-id="ae550-127">Błąd kompilatora zazwyczaj może pomóc w znalezieniu problemu.</span><span class="sxs-lookup"><span data-stu-id="ae550-127">The compiler error can usually help you find the problem.</span></span>

<span data-ttu-id="ae550-128">W tym pierwszym przykładzie `if` przedstawiono moc i typy logiczne.</span><span class="sxs-lookup"><span data-stu-id="ae550-128">This first sample shows the power of `if` and Boolean types.</span></span> <span data-ttu-id="ae550-129">*Wartość logiczna* jest zmienną, która może `true` `false`mieć jedną z dwóch wartości: lub .</span><span class="sxs-lookup"><span data-stu-id="ae550-129">A *Boolean* is a variable that can have one of two values: `true` or `false`.</span></span> <span data-ttu-id="ae550-130">C# definiuje typ specjalny `bool` dla zmiennych logicznych.</span><span class="sxs-lookup"><span data-stu-id="ae550-130">C# defines a special type, `bool` for Boolean variables.</span></span> <span data-ttu-id="ae550-131">Instrukcja `if` umożliwia sprawdzenie wartości typu `bool`.</span><span class="sxs-lookup"><span data-stu-id="ae550-131">The `if` statement checks the value of a `bool`.</span></span> <span data-ttu-id="ae550-132">Jeśli wartość to `true`, zostanie wykonana instrukcja następująca po instrukcji `if`.</span><span class="sxs-lookup"><span data-stu-id="ae550-132">When the value is `true`, the statement following the `if` executes.</span></span> <span data-ttu-id="ae550-133">W przeciwnym razie zostanie ona pominięta.</span><span class="sxs-lookup"><span data-stu-id="ae550-133">Otherwise, it is skipped.</span></span>

<span data-ttu-id="ae550-134">Taki proces sprawdzania warunków i wykonywania instrukcji na podstawie tych warunków daje ogromne możliwości.</span><span class="sxs-lookup"><span data-stu-id="ae550-134">This process of checking conditions and executing statements based on those conditions is very powerful.</span></span>

## <a name="make-if-and-else-work-together"></a><span data-ttu-id="ae550-135">Łączenie działania instrukcji if i else</span><span class="sxs-lookup"><span data-stu-id="ae550-135">Make if and else work together</span></span>

<span data-ttu-id="ae550-136">Aby wykonać różny kod w gałęziach dla wartości true i false, należy utworzyć gałąź `else` wykonywaną, jeśli wartość warunku to false.</span><span class="sxs-lookup"><span data-stu-id="ae550-136">To execute different code in both the true and false branches, you create an `else` branch that executes when the condition is false.</span></span> <span data-ttu-id="ae550-137">Spróbuj tego.</span><span class="sxs-lookup"><span data-stu-id="ae550-137">Try this.</span></span> <span data-ttu-id="ae550-138">Dodaj dwa ostatnie wiersze w `Main` kodzie poniżej do metody (powinieneś mieć już pierwsze cztery):</span><span class="sxs-lookup"><span data-stu-id="ae550-138">Add the last two lines in the code below to your `Main` method (you should already have the first four):</span></span>

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10");
else
    Console.WriteLine("The answer is not greater than 10");
```

<span data-ttu-id="ae550-139">Instrukcja po słowie kluczowym `else` jest wykonywana tylko wtedy, gdy testowany warunek ma wartość `false`.</span><span class="sxs-lookup"><span data-stu-id="ae550-139">The statement following the `else` keyword executes only when the condition being tested is `false`.</span></span> <span data-ttu-id="ae550-140">Połączenie `if` i `else` warunki logiczne zapewnia całą moc potrzebną `true` do `false` obsługi zarówno a, jak i warunek.</span><span class="sxs-lookup"><span data-stu-id="ae550-140">Combining `if` and `else` with Boolean conditions provides all the power you need to handle both a `true` and a `false` condition.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ae550-141">Wcięcia pod instrukcjami `if` i `else` służą tylko do zwiększenia czytelności.</span><span class="sxs-lookup"><span data-stu-id="ae550-141">The indentation under the `if` and `else` statements is for human readers.</span></span>
> <span data-ttu-id="ae550-142">Język Języka C# nie traktuje wcięcia lub biały znak jako znaczące.</span><span class="sxs-lookup"><span data-stu-id="ae550-142">The C# language doesn't treat indentation or white space as significant.</span></span>
> <span data-ttu-id="ae550-143">Instrukcja po słowie kluczowym `if` lub `else` zostanie wykonana w zależności od warunku.</span><span class="sxs-lookup"><span data-stu-id="ae550-143">The statement following the `if` or `else` keyword will be executed based on the condition.</span></span> <span data-ttu-id="ae550-144">Wszystkie przykłady w tym samouczku postępuj zgodnie z powszechną praktyką wcięcia wierszy na podstawie przepływu sterowania instrukcji.</span><span class="sxs-lookup"><span data-stu-id="ae550-144">All the samples in this tutorial follow a common practice to indent lines based on the control flow of statements.</span></span>

<span data-ttu-id="ae550-145">Ponieważ wcięcia nie mają znaczenia, należy użyć znaków `{` i `}` do określenia, czy do bloku wykonywanego warunkowo ma należeć więcej niż jedna instrukcja.</span><span class="sxs-lookup"><span data-stu-id="ae550-145">Because indentation is not significant, you need to use `{` and `}` to indicate when you want more than one statement to be part of the block that executes conditionally.</span></span> <span data-ttu-id="ae550-146">Programiści języka C# zazwyczaj używają nawiasów klamrowych we wszystkich klauzulach `if` i `else`.</span><span class="sxs-lookup"><span data-stu-id="ae550-146">C# programmers typically use those braces on all `if` and `else` clauses.</span></span> <span data-ttu-id="ae550-147">Poniższy przykład jest taki sam jak ten, który właśnie został utworzony.</span><span class="sxs-lookup"><span data-stu-id="ae550-147">The following example is the same as the one you just created.</span></span> <span data-ttu-id="ae550-148">Zmodyfikuj powyższy kod, aby dopasować go do następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="ae550-148">Modify your code above to match the following code:</span></span>

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
{
    Console.WriteLine("The answer is greater than 10");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
}
```

> [!TIP]
> <span data-ttu-id="ae550-149">W pozostałej części tego samouczka przykłady kodu zawierają nawiasy klamrowe, zgodnie z przyjętymi praktykami.</span><span class="sxs-lookup"><span data-stu-id="ae550-149">Through the rest of this tutorial, the code samples all include the braces, following accepted practices.</span></span>

<span data-ttu-id="ae550-150">Możesz przetestować bardziej skomplikowane warunki.</span><span class="sxs-lookup"><span data-stu-id="ae550-150">You can test more complicated conditions.</span></span> <span data-ttu-id="ae550-151">Dodaj następujący kod `Main` w metodzie po kodzie, który został napisany do tej pory:</span><span class="sxs-lookup"><span data-stu-id="ae550-151">Add the following code in your `Main` method after the code you've written so far:</span></span>

```csharp
int c = 4;
if ((a + b + c > 10) && (a == b))
{
    Console.WriteLine("The answer is greater than 10");
    Console.WriteLine("And the first number is equal to the second");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
    Console.WriteLine("Or the first number is not equal to the second");
}
```

<span data-ttu-id="ae550-152">Symbol `==` testuje *na rzecz równości*.</span><span class="sxs-lookup"><span data-stu-id="ae550-152">The `==` symbol tests for *equality*.</span></span> <span data-ttu-id="ae550-153">Za `==` pomocą odróżnia test równości od przypisania, który został odnotowywana w . `a = 5`</span><span class="sxs-lookup"><span data-stu-id="ae550-153">Using `==` distinguishes the test for equality from assignment, which you saw in `a = 5`.</span></span>

<span data-ttu-id="ae550-154">Znaki `&&` określają warunek „i”.</span><span class="sxs-lookup"><span data-stu-id="ae550-154">The `&&` represents "and".</span></span> <span data-ttu-id="ae550-155">Oznacza to, że instrukcja w gałęzi dla wartości true zostanie wykonana tylko wtedy, gdy oba warunki będą mieć wartość true.</span><span class="sxs-lookup"><span data-stu-id="ae550-155">It means both conditions must be true to execute the statement in the true branch.</span></span>  <span data-ttu-id="ae550-156">Te przykłady przedstawiają także, że można użyć wielu instrukcji w każdej gałęzi warunkowej, jeśli zostaną umieszczone między znakami `{` i `}`.</span><span class="sxs-lookup"><span data-stu-id="ae550-156">These examples also show that you can have multiple statements in each conditional branch, provided you enclose them in `{` and `}`.</span></span>

<span data-ttu-id="ae550-157">Można również `||` użyć do reprezentowania "lub".</span><span class="sxs-lookup"><span data-stu-id="ae550-157">You can also use  `||` to represent "or".</span></span> <span data-ttu-id="ae550-158">Dodaj następujący kod po tym, co do tej pory napisałeś:</span><span class="sxs-lookup"><span data-stu-id="ae550-158">Add the following code after what you've written so far:</span></span>

```csharp
if ((a + b + c > 10) || (a == b))
{
    Console.WriteLine("The answer is greater than 10");
    Console.WriteLine("Or the first number is equal to the second");
}
else
{
    Console.WriteLine("The answer is not greater than 10");
    Console.WriteLine("And the first number is not equal to the second");
}
```

<span data-ttu-id="ae550-159">`a`Zmodyfikuj `b`wartości `c` , `&&` i `||` przełączaj się między i do eksplorowania.</span><span class="sxs-lookup"><span data-stu-id="ae550-159">Modify the values of `a`, `b`, and `c` and switch between `&&` and `||` to explore.</span></span> <span data-ttu-id="ae550-160">Zyskasz więcej zrozumienia, `&&` `||` jak działają operatorzy i operatorzy.</span><span class="sxs-lookup"><span data-stu-id="ae550-160">You'll gain more understanding of how the `&&` and `||` operators work.</span></span>

<span data-ttu-id="ae550-161">Ukończono pierwszy krok.</span><span class="sxs-lookup"><span data-stu-id="ae550-161">You've finished the first step.</span></span> <span data-ttu-id="ae550-162">Przed rozpoczęciem następnej sekcji przenieśmy bieżący kod do osobnej metody.</span><span class="sxs-lookup"><span data-stu-id="ae550-162">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="ae550-163">Ułatwia to rozpoczęcie pracy z nowym przykładem.</span><span class="sxs-lookup"><span data-stu-id="ae550-163">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="ae550-164">Zmień nazwę `Main` metody `ExploreIf` i napisz `Main` nową `ExploreIf`metodę, która wywołuje .</span><span class="sxs-lookup"><span data-stu-id="ae550-164">Rename your `Main` method to `ExploreIf` and write a new `Main` method that calls `ExploreIf`.</span></span> <span data-ttu-id="ae550-165">Po zakończeniu kod powinien wyglądać tak:</span><span class="sxs-lookup"><span data-stu-id="ae550-165">When you have finished, your code should look like this:</span></span>

```csharp
using System;

namespace BranchesAndLoops
{
    class Program
    {
        static void ExploreIf()
        {
            int a = 5;
            int b = 3;
            if (a + b > 10)
            {
                Console.WriteLine("The answer is greater than 10");
            }
            else
            {
                Console.WriteLine("The answer is not greater than 10");
            }

            int c = 4;
            if ((a + b + c > 10) && (a > b))
            {
                Console.WriteLine("The answer is greater than 10");
                Console.WriteLine("And the first number is greater than the second");
            }
            else
            {
                Console.WriteLine("The answer is not greater than 10");
                Console.WriteLine("Or the first number is not greater than the second");
            }

            if ((a + b + c > 10) || (a > b))
            {
                Console.WriteLine("The answer is greater than 10");
                Console.WriteLine("Or the first number is greater than the second");
            }
            else
            {
                Console.WriteLine("The answer is not greater than 10");
                Console.WriteLine("And the first number is not greater than the second");
            }
        }

        static void Main(string[] args)
        {
            ExploreIf();
        }
    }
}
```

<span data-ttu-id="ae550-166">Skomentuj wezwanie `ExploreIf()`do .</span><span class="sxs-lookup"><span data-stu-id="ae550-166">Comment out the call to `ExploreIf()`.</span></span> <span data-ttu-id="ae550-167">To sprawi, że dane wyjściowe mniej zaśmiecone podczas pracy w tej sekcji:</span><span class="sxs-lookup"><span data-stu-id="ae550-167">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//ExploreIf();
```

<span data-ttu-id="ae550-168">Rozpoczyna `//` **komentarz** w języku C#.</span><span class="sxs-lookup"><span data-stu-id="ae550-168">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="ae550-169">Komentarze to dowolny tekst, który chcesz zachować w kodzie źródłowym, ale nie są wykonywane jako kod.</span><span class="sxs-lookup"><span data-stu-id="ae550-169">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="ae550-170">Kompilator nie generuje żadnego kodu wykonywalnego z komentarzy.</span><span class="sxs-lookup"><span data-stu-id="ae550-170">The compiler does not generate any executable code from comments.</span></span>

## <a name="use-loops-to-repeat-operations"></a><span data-ttu-id="ae550-171">Użycie pętli do powtarzania operacji</span><span class="sxs-lookup"><span data-stu-id="ae550-171">Use loops to repeat operations</span></span>

<span data-ttu-id="ae550-172">W tej sekcji używasz **pętli** do powtarzania instrukcji.</span><span class="sxs-lookup"><span data-stu-id="ae550-172">In this section you use **loops** to repeat statements.</span></span> <span data-ttu-id="ae550-173">Wypróbuj `Main` ten kod w swojej metodzie:</span><span class="sxs-lookup"><span data-stu-id="ae550-173">Try this code in your `Main` method:</span></span>

```csharp
int counter = 0;
while (counter < 10)
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
}
```

<span data-ttu-id="ae550-174">Instrukcja `while` sprawdza warunek i wykonuje instrukcję `while`lub blok instrukcji po .</span><span class="sxs-lookup"><span data-stu-id="ae550-174">The `while` statement checks a condition and executes the statement or statement block following the `while`.</span></span> <span data-ttu-id="ae550-175">Wielokrotnie sprawdza warunek i wykonywanie tych instrukcji, dopóki warunek jest false.</span><span class="sxs-lookup"><span data-stu-id="ae550-175">It repeatedly checks the condition and executing those statements until the condition is false.</span></span>

<span data-ttu-id="ae550-176">Ten przykład zawiera jeszcze jeden nowy operator.</span><span class="sxs-lookup"><span data-stu-id="ae550-176">There's one other new operator in this example.</span></span> <span data-ttu-id="ae550-177">Znaki `++` po zmiennej `counter` oznaczają operator **inkrementacji**.</span><span class="sxs-lookup"><span data-stu-id="ae550-177">The `++` after the `counter` variable is the **increment** operator.</span></span> <span data-ttu-id="ae550-178">Dodaje 1 do wartości `counter` i przechowuje tę `counter` wartość w zmiennej.</span><span class="sxs-lookup"><span data-stu-id="ae550-178">It adds 1 to the value of `counter` and stores that value in the `counter` variable.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ae550-179">Upewnij się, `while` że warunek pętli zmienia się na false podczas wykonywania kodu.</span><span class="sxs-lookup"><span data-stu-id="ae550-179">Make sure that the `while` loop condition changes to false as you execute the code.</span></span> <span data-ttu-id="ae550-180">W przeciwnym razie wystąpi **pętla nieskończona**, czyli wykonywanie programu nigdy się nie skończy.</span><span class="sxs-lookup"><span data-stu-id="ae550-180">Otherwise, you create an **infinite loop** where your program never ends.</span></span> <span data-ttu-id="ae550-181">Nie jest to wykazane w tym przykładzie, ponieważ musisz wymusić zamknięcie programu przy użyciu **klawisza CTRL-C** lub innych środków.</span><span class="sxs-lookup"><span data-stu-id="ae550-181">That is not demonstrated in this sample, because you have to force your program to quit using **CTRL-C** or other means.</span></span>

<span data-ttu-id="ae550-182">Pętla `while` testuje warunek przed wykonaniem kodu po instrukcji `while`.</span><span class="sxs-lookup"><span data-stu-id="ae550-182">The `while` loop tests the condition before executing the code following the `while`.</span></span> <span data-ttu-id="ae550-183">Pętla `do`...`while` najpierw wykonuje kod, a następnie sprawdza warunek.</span><span class="sxs-lookup"><span data-stu-id="ae550-183">The `do` ... `while` loop executes the code first, and then checks the condition.</span></span> <span data-ttu-id="ae550-184">Pętla do while jest pokazana w następującym kodzie:</span><span class="sxs-lookup"><span data-stu-id="ae550-184">The do while loop is shown in the following code:</span></span>

```csharp
int counter = 0;
do
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
} while (counter < 10);
```

<span data-ttu-id="ae550-185">Ta `do` pętla i `while` wcześniejsza pętla wytwarzają to samo wyjście.</span><span class="sxs-lookup"><span data-stu-id="ae550-185">This `do` loop and the earlier `while` loop produce the same output.</span></span>

## <a name="work-with-the-for-loop"></a><span data-ttu-id="ae550-186">Praca z pętlą for</span><span class="sxs-lookup"><span data-stu-id="ae550-186">Work with the for loop</span></span>

<span data-ttu-id="ae550-187">For **for** pętli jest powszechnie używany w Języku C#.</span><span class="sxs-lookup"><span data-stu-id="ae550-187">The **for** loop is commonly used in C#.</span></span> <span data-ttu-id="ae550-188">Wypróbuj ten kod w metodzie Main():</span><span class="sxs-lookup"><span data-stu-id="ae550-188">Try this code in your Main() method:</span></span>

```csharp
for (int index = 0; index < 10; index++)
{
    Console.WriteLine($"Hello World! The index is {index}");
}
```

<span data-ttu-id="ae550-189">Działa on tak samo jak już przedstawione pętle `while` i `do`.</span><span class="sxs-lookup"><span data-stu-id="ae550-189">This does the same work as the `while` loop and the `do` loop you've already used.</span></span> <span data-ttu-id="ae550-190">Instrukcja `for` składa się z trzech części, które sterują jej pracą.</span><span class="sxs-lookup"><span data-stu-id="ae550-190">The `for` statement has three parts that control how it works.</span></span>

<span data-ttu-id="ae550-191">Pierwsza część jest **dla inicjatora:** `int index = 0;` deklaruje, że `index` jest zmienna pętli i ustawia jego wartość początkową . `0`</span><span class="sxs-lookup"><span data-stu-id="ae550-191">The first part is the **for initializer**: `int index = 0;` declares that `index` is the loop variable, and sets its initial value to `0`.</span></span>

<span data-ttu-id="ae550-192">Środkowa część jest **warunek for:** `index < 10` deklaruje, że ta `for` pętla kontynuuje wykonywanie tak długo, jak wartość licznika jest mniejsza niż 10.</span><span class="sxs-lookup"><span data-stu-id="ae550-192">The middle part is the **for condition**: `index < 10` declares that this `for` loop continues to execute as long as the value of counter is less than 10.</span></span>

<span data-ttu-id="ae550-193">Ostatnia część jest **dla iterator:** `index++` określa sposób modyfikowania zmiennej pętli `for` po wykonaniu bloku po instrukcji.</span><span class="sxs-lookup"><span data-stu-id="ae550-193">The final part is the **for iterator**: `index++` specifies how to modify the loop variable after executing the block following the `for` statement.</span></span> <span data-ttu-id="ae550-194">Tutaj zdefiniowano, że zmienną `index` należy zwiększyć o 1 po każdym wykonaniu bloku.</span><span class="sxs-lookup"><span data-stu-id="ae550-194">Here, it specifies that `index` should be incremented by 1 each time the block executes.</span></span>

<span data-ttu-id="ae550-195">Poeksperymentuj samodzielnie z tymi elementami.</span><span class="sxs-lookup"><span data-stu-id="ae550-195">Experiment with these yourself.</span></span> <span data-ttu-id="ae550-196">Wypróbuj poniższe modyfikacje:</span><span class="sxs-lookup"><span data-stu-id="ae550-196">Try each of the following:</span></span>

- <span data-ttu-id="ae550-197">Zmień inicjator, tak aby miał inną wartość początkową.</span><span class="sxs-lookup"><span data-stu-id="ae550-197">Change the initializer to start at a different value.</span></span>
- <span data-ttu-id="ae550-198">Zmień warunek, tak aby zatrzymanie pętli nastąpiło przy innej wartości.</span><span class="sxs-lookup"><span data-stu-id="ae550-198">Change the condition to stop at a different value.</span></span>

<span data-ttu-id="ae550-199">Gdy skończysz, przejdziemy do samodzielnego pisania kodu, gdzie wykorzystasz zdobyte umiejętności.</span><span class="sxs-lookup"><span data-stu-id="ae550-199">When you're done, let's move on to write some code yourself to use what you've learned.</span></span>

## <a name="combine-branches-and-loops"></a><span data-ttu-id="ae550-200">Łączenie gałęzi i pętli</span><span class="sxs-lookup"><span data-stu-id="ae550-200">Combine branches and loops</span></span>

<span data-ttu-id="ae550-201">Teraz, gdy znasz już instrukcję `if` i konstrukcje pętli w języku C#, sprawdź, czy potrafisz napisać kod C# obliczający sumę wszystkich liczb całkowitych z zakresu 1-20 podzielnych przez 3.</span><span class="sxs-lookup"><span data-stu-id="ae550-201">Now that you've seen the `if` statement and the looping constructs in the C# language, see if you can write C# code to find the sum of all integers 1 through 20 that are divisible by 3.</span></span>  <span data-ttu-id="ae550-202">Oto kilka wskazówek:</span><span class="sxs-lookup"><span data-stu-id="ae550-202">Here are a few hints:</span></span>

- <span data-ttu-id="ae550-203">Operator `%` umożliwia obliczenie reszty z operacji dzielenia.</span><span class="sxs-lookup"><span data-stu-id="ae550-203">The `%` operator gives you the remainder of a division operation.</span></span>
- <span data-ttu-id="ae550-204">Instrukcja `if` umożliwia zdefiniowanie warunku określającego, czy liczba powinna być częścią sumy.</span><span class="sxs-lookup"><span data-stu-id="ae550-204">The `if` statement gives you the condition to see if a number should be part of the sum.</span></span>
- <span data-ttu-id="ae550-205">Pętla `for` ułatwia powtórzenie serii kroków dla wszystkich liczb z zakresu 1-20.</span><span class="sxs-lookup"><span data-stu-id="ae550-205">The `for` loop can help you repeat a series of steps for all the numbers 1 through 20.</span></span>

<span data-ttu-id="ae550-206">Spróbuj napisać kod.</span><span class="sxs-lookup"><span data-stu-id="ae550-206">Try it yourself.</span></span> <span data-ttu-id="ae550-207">Następnie wykonaj go, aby dowiedzieć się, jak Ci poszło.</span><span class="sxs-lookup"><span data-stu-id="ae550-207">Then check how you did.</span></span> <span data-ttu-id="ae550-208">Powinieneś dostać 63 za odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="ae550-208">You should get 63 for an answer.</span></span> <span data-ttu-id="ae550-209">Możesz zobaczyć jedną możliwą [odpowiedź, wyświetlając wypełniony kod w witrynie GitHub](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54).</span><span class="sxs-lookup"><span data-stu-id="ae550-209">You can see one possible answer by [viewing the completed code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54).</span></span>

<span data-ttu-id="ae550-210">Ukończono samouczek "gałęzie i pętle".</span><span class="sxs-lookup"><span data-stu-id="ae550-210">You've completed the "branches and loops" tutorial.</span></span>

<span data-ttu-id="ae550-211">Można kontynuować [samouczek Tablice i kolekcje](arrays-and-collections.md) we własnym środowisku programistycznym.</span><span class="sxs-lookup"><span data-stu-id="ae550-211">You can continue with the [Arrays and collections](arrays-and-collections.md) tutorial in your own development environment.</span></span>

<span data-ttu-id="ae550-212">Więcej na temat tych pojęć możesz dowiedzieć się w następujących tematach:</span><span class="sxs-lookup"><span data-stu-id="ae550-212">You can learn more about these concepts in these topics:</span></span>

- [<span data-ttu-id="ae550-213">if i else, instrukcje</span><span class="sxs-lookup"><span data-stu-id="ae550-213">If and else statement</span></span>](../../language-reference/keywords/if-else.md)
- [<span data-ttu-id="ae550-214">Podczas gdy oświadczenie</span><span class="sxs-lookup"><span data-stu-id="ae550-214">While statement</span></span>](../../language-reference/keywords/while.md)
- [<span data-ttu-id="ae550-215">do, instrukcja</span><span class="sxs-lookup"><span data-stu-id="ae550-215">Do statement</span></span>](../../language-reference/keywords/do.md)
- [<span data-ttu-id="ae550-216">Dla instrukcji</span><span class="sxs-lookup"><span data-stu-id="ae550-216">For statement</span></span>](../../language-reference/keywords/for.md)

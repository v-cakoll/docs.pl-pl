---
title: Rozgałęzienia i pętle — wprowadzenie do samouczka języka C#
description: W tym samouczku dotyczącym gałęzi i pętli można napisać kod w języku C#, aby poznać składnię języka, która obsługuje gałęzie warunkowe, i pętle, aby wielokrotnie wykonywać instrukcje.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: d8c10a7462b7c27c5353aee6d957732a8d161015
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135948"
---
# <a name="learn-conditional-logic-with-branch-and-loop-statements"></a><span data-ttu-id="ec2a2-103">Informacje o logice warunkowej przy użyciu instrukcji Branch i Loop</span><span class="sxs-lookup"><span data-stu-id="ec2a2-103">Learn conditional logic with branch and loop statements</span></span>

<span data-ttu-id="ec2a2-104">W tym samouczku przedstawiono sposób pisania kodu, który analizuje zmienne i zmienia ścieżkę wykonywania na podstawie tych zmiennych.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-104">This tutorial teaches you how to write code that examines variables and changes the execution path based on those variables.</span></span> <span data-ttu-id="ec2a2-105">Napiszesz kod w języku C# i zobaczysz wyniki kompilacji i uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-105">You write C# code and see the results of compiling and running it.</span></span> <span data-ttu-id="ec2a2-106">Samouczek zawiera szereg lekcji, które eksplorują gałęzie i konstrukcje zapętlenia w języku C#.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-106">The tutorial contains a series of lessons that explore branching and looping constructs in C#.</span></span> <span data-ttu-id="ec2a2-107">Te lekcje umożliwiają poznanie podstaw języka C#.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-107">These lessons teach you the fundamentals of the C# language.</span></span>

<span data-ttu-id="ec2a2-108">Ten samouczek oczekuje, że masz maszynę, której możesz użyć do programowania.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-108">This tutorial expects you to have a machine you can use for development.</span></span> <span data-ttu-id="ec2a2-109">Samouczek platformy .NET [Hello World w ciągu 10 minut](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) zawiera instrukcje dotyczące konfigurowania lokalnego środowiska deweloperskiego w systemie Windows, Linux lub macOS.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-109">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span> <span data-ttu-id="ec2a2-110">Krótkie omówienie poleceń, z których będziesz korzystać, znajduje się w zapoznanie [z narzędziami programistycznymi](local-environment.md) zawierającymi linki do dalszych szczegółów.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-110">A quick overview of the commands you'll use is in the [Become familiar with the development tools](local-environment.md) with links to more details.</span></span>

## <a name="make-decisions-using-the-if-statement"></a><span data-ttu-id="ec2a2-111">Podejmowanie decyzji przy `if` użyciu instrukcji</span><span class="sxs-lookup"><span data-stu-id="ec2a2-111">Make decisions using the `if` statement</span></span>

<span data-ttu-id="ec2a2-112">Utwórz katalog o nazwie *branchs — samouczek*.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-112">Create a directory named *branches-tutorial*.</span></span> <span data-ttu-id="ec2a2-113">Upewnij się, że bieżący katalog i uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="ec2a2-113">Make that the current directory and run the following command:</span></span>

```dotnetcli
dotnet new console -n BranchesAndLoops -o .
```

<span data-ttu-id="ec2a2-114">To polecenie powoduje utworzenie nowej aplikacji konsolowej .NET Core w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-114">This command creates a new .NET Core console application in the current directory.</span></span>

<span data-ttu-id="ec2a2-115">Otwórz *program.cs* w ulubionym edytorze i Zastąp wiersz `Console.WriteLine("Hello World!");` następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="ec2a2-115">Open *Program.cs* in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following code:</span></span>

```csharp
int a = 5;
int b = 6;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10.");
```

<span data-ttu-id="ec2a2-116">Wypróbuj ten kod, wpisując `dotnet run` w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-116">Try this code by typing `dotnet run` in your console window.</span></span> <span data-ttu-id="ec2a2-117">Powinien zostać wyświetlony komunikat "odpowiedź jest większa niż 10".</span><span class="sxs-lookup"><span data-stu-id="ec2a2-117">You should see the message "The answer is greater than 10."</span></span> <span data-ttu-id="ec2a2-118">Wydrukowano w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-118">printed to your console.</span></span>

<span data-ttu-id="ec2a2-119">Zmodyfikuj deklarację zmiennej `b`, tak aby suma była mniejsza niż 10:</span><span class="sxs-lookup"><span data-stu-id="ec2a2-119">Modify the declaration of `b` so that the sum is less than 10:</span></span>

```csharp
int b = 3;
```

<span data-ttu-id="ec2a2-120">Wpisz `dotnet run` ponownie.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-120">Type `dotnet run` again.</span></span> <span data-ttu-id="ec2a2-121">Ponieważ odpowiedź jest mniejsza niż 10, nic nie zostanie wyświetlone.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-121">Because the answer is less than 10, nothing is printed.</span></span> <span data-ttu-id="ec2a2-122">Testowany **warunek** ma wartość false.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-122">The **condition** you're testing is false.</span></span> <span data-ttu-id="ec2a2-123">Nie ma żadnego kodu do wykonania, ponieważ napisano kod tylko dla jednej z możliwych gałęzi instrukcji `if`: wykonywanej dla wartości true.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-123">You don't have any code to execute because you've only written one of the possible branches for an `if` statement: the true branch.</span></span>

> [!TIP]
> <span data-ttu-id="ec2a2-124">Podczas nauki języka C# (lub dowolnego języka programowania) będziesz robić błędy przy pisaniu kodu.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-124">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="ec2a2-125">Kompilator znajdzie i zgłosi błędy.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-125">The compiler will find and report the errors.</span></span> <span data-ttu-id="ec2a2-126">Sprawdź blisko danych wyjściowych błędu i kod, który wygenerował błąd.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-126">Look closely at the error output and the code that generated the error.</span></span> <span data-ttu-id="ec2a2-127">Błąd kompilatora może zwykle pomóc w znalezieniu problemu.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-127">The compiler error can usually help you find the problem.</span></span>

<span data-ttu-id="ec2a2-128">Ten pierwszy przykład pokazuje moc `if` i typy logiczne.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-128">This first sample shows the power of `if` and Boolean types.</span></span> <span data-ttu-id="ec2a2-129">*Wartość logiczna* to zmienna, która może mieć jedną z dwóch wartości: `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-129">A *Boolean* is a variable that can have one of two values: `true` or `false`.</span></span> <span data-ttu-id="ec2a2-130">C# definiuje typ specjalny, `bool` dla zmiennych logicznych.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-130">C# defines a special type, `bool` for Boolean variables.</span></span> <span data-ttu-id="ec2a2-131">Instrukcja `if` umożliwia sprawdzenie wartości typu `bool`.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-131">The `if` statement checks the value of a `bool`.</span></span> <span data-ttu-id="ec2a2-132">Jeśli wartość to `true`, zostanie wykonana instrukcja następująca po instrukcji `if`.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-132">When the value is `true`, the statement following the `if` executes.</span></span> <span data-ttu-id="ec2a2-133">W przeciwnym razie zostanie ona pominięta.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-133">Otherwise, it is skipped.</span></span>

<span data-ttu-id="ec2a2-134">Taki proces sprawdzania warunków i wykonywania instrukcji na podstawie tych warunków daje ogromne możliwości.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-134">This process of checking conditions and executing statements based on those conditions is very powerful.</span></span>

## <a name="make-if-and-else-work-together"></a><span data-ttu-id="ec2a2-135">Łączenie działania instrukcji if i else</span><span class="sxs-lookup"><span data-stu-id="ec2a2-135">Make if and else work together</span></span>

<span data-ttu-id="ec2a2-136">Aby wykonać różny kod w gałęziach dla wartości true i false, należy utworzyć gałąź `else` wykonywaną, jeśli wartość warunku to false.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-136">To execute different code in both the true and false branches, you create an `else` branch that executes when the condition is false.</span></span> <span data-ttu-id="ec2a2-137">Wypróbuj to.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-137">Try this.</span></span> <span data-ttu-id="ec2a2-138">Dodaj ostatnie dwa wiersze w kodzie poniżej do `Main` metody (należy mieć już pierwsze cztery):</span><span class="sxs-lookup"><span data-stu-id="ec2a2-138">Add the last two lines in the code below to your `Main` method (you should already have the first four):</span></span>

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10");
else
    Console.WriteLine("The answer is not greater than 10");
```

<span data-ttu-id="ec2a2-139">Instrukcja po słowie kluczowym `else` jest wykonywana tylko wtedy, gdy testowany warunek ma wartość `false`.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-139">The statement following the `else` keyword executes only when the condition being tested is `false`.</span></span> <span data-ttu-id="ec2a2-140">Łączenie `if` i `else` z warunkami logicznymi zapewnia wszystko, co jest potrzebne do obsługi zarówno `true` `false` warunku, jak i.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-140">Combining `if` and `else` with Boolean conditions provides all the power you need to handle both a `true` and a `false` condition.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ec2a2-141">Wcięcia pod instrukcjami `if` i `else` służą tylko do zwiększenia czytelności.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-141">The indentation under the `if` and `else` statements is for human readers.</span></span>
> <span data-ttu-id="ec2a2-142">Język C# nie traktuje wcięcia ani odstępu jako znaczącego.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-142">The C# language doesn't treat indentation or white space as significant.</span></span>
> <span data-ttu-id="ec2a2-143">Instrukcja po słowie kluczowym `if` lub `else` zostanie wykonana w zależności od warunku.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-143">The statement following the `if` or `else` keyword will be executed based on the condition.</span></span> <span data-ttu-id="ec2a2-144">Wszystkie przykłady w tym samouczku są zgodne ze wspólną metodą tworzenia wcięć wierszy na podstawie przepływu sterowania instrukcji.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-144">All the samples in this tutorial follow a common practice to indent lines based on the control flow of statements.</span></span>

<span data-ttu-id="ec2a2-145">Ponieważ wcięcia nie mają znaczenia, należy użyć znaków `{` i `}` do określenia, czy do bloku wykonywanego warunkowo ma należeć więcej niż jedna instrukcja.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-145">Because indentation is not significant, you need to use `{` and `}` to indicate when you want more than one statement to be part of the block that executes conditionally.</span></span> <span data-ttu-id="ec2a2-146">Programiści języka C# zazwyczaj używają nawiasów klamrowych we wszystkich klauzulach `if` i `else`.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-146">C# programmers typically use those braces on all `if` and `else` clauses.</span></span> <span data-ttu-id="ec2a2-147">Poniższy przykład jest taki sam jak właśnie utworzony.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-147">The following example is the same as the one you just created.</span></span> <span data-ttu-id="ec2a2-148">Zmodyfikuj kod powyżej, aby był zgodny z następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="ec2a2-148">Modify your code above to match the following code:</span></span>

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
> <span data-ttu-id="ec2a2-149">W pozostałej części tego samouczka wszystkie przykłady kodu zawierają nawiasy klamrowe, po zastosowaniu zaakceptowanych praktyk.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-149">Through the rest of this tutorial, the code samples all include the braces, following accepted practices.</span></span>

<span data-ttu-id="ec2a2-150">Możesz przetestować bardziej skomplikowane warunki.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-150">You can test more complicated conditions.</span></span> <span data-ttu-id="ec2a2-151">Dodaj następujący kod w `Main` metodzie po kodzie, który zapisano do tej pory:</span><span class="sxs-lookup"><span data-stu-id="ec2a2-151">Add the following code in your `Main` method after the code you've written so far:</span></span>

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

<span data-ttu-id="ec2a2-152">`==` Symbol sprawdza *równość*.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-152">The `==` symbol tests for *equality*.</span></span> <span data-ttu-id="ec2a2-153">Użycie `==` odróżnia test pod kątem równości przed przypisaniem `a = 5`.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-153">Using `==` distinguishes the test for equality from assignment, which you saw in `a = 5`.</span></span>

<span data-ttu-id="ec2a2-154">Znaki `&&` określają warunek „i”.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-154">The `&&` represents "and".</span></span> <span data-ttu-id="ec2a2-155">Oznacza to, że instrukcja w gałęzi dla wartości true zostanie wykonana tylko wtedy, gdy oba warunki będą mieć wartość true.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-155">It means both conditions must be true to execute the statement in the true branch.</span></span>  <span data-ttu-id="ec2a2-156">Te przykłady przedstawiają także, że można użyć wielu instrukcji w każdej gałęzi warunkowej, jeśli zostaną umieszczone między znakami `{` i `}`.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-156">These examples also show that you can have multiple statements in each conditional branch, provided you enclose them in `{` and `}`.</span></span>

<span data-ttu-id="ec2a2-157">Można również użyć `||` do reprezentowania "or".</span><span class="sxs-lookup"><span data-stu-id="ec2a2-157">You can also use  `||` to represent "or".</span></span> <span data-ttu-id="ec2a2-158">Dodaj następujący kod po wykonaniu tej czynności:</span><span class="sxs-lookup"><span data-stu-id="ec2a2-158">Add the following code after what you've written so far:</span></span>

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

<span data-ttu-id="ec2a2-159">`a`Zmodyfikuj wartości, `b`i `c` i przełączenie między `&&` i `||` do Eksploruj.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-159">Modify the values of `a`, `b`, and `c` and switch between `&&` and `||` to explore.</span></span> <span data-ttu-id="ec2a2-160">Dowiesz się `&&` , jak działają operatory i `||` .</span><span class="sxs-lookup"><span data-stu-id="ec2a2-160">You'll gain more understanding of how the `&&` and `||` operators work.</span></span>

<span data-ttu-id="ec2a2-161">Wykonano pierwszy krok.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-161">You've finished the first step.</span></span> <span data-ttu-id="ec2a2-162">Przed rozpoczęciem następnej sekcji przechodźmy bieżący kod w oddzielną metodę.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-162">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="ec2a2-163">Ułatwia to rozpoczęcie pracy z nowym przykładem.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-163">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="ec2a2-164">Zmień nazwę `Main` metody na `ExploreIf` i Napisz nową `Main` metodę, która wywołuje `ExploreIf`.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-164">Rename your `Main` method to `ExploreIf` and write a new `Main` method that calls `ExploreIf`.</span></span> <span data-ttu-id="ec2a2-165">Po zakończeniu kod powinien wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="ec2a2-165">When you have finished, your code should look like this:</span></span>

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

<span data-ttu-id="ec2a2-166">Komentarz wywołania do `ExploreIf()`.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-166">Comment out the call to `ExploreIf()`.</span></span> <span data-ttu-id="ec2a2-167">Dane wyjściowe będą mniej czytelne podczas pracy w tej sekcji:</span><span class="sxs-lookup"><span data-stu-id="ec2a2-167">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//ExploreIf();
```

<span data-ttu-id="ec2a2-168">W `//` języku C# jest uruchamiany **komentarz** .</span><span class="sxs-lookup"><span data-stu-id="ec2a2-168">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="ec2a2-169">Komentarze są dowolnym tekstem, który chcesz zachować w kodzie źródłowym, ale nie można go wykonać jako kod.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-169">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="ec2a2-170">Kompilator nie generuje żadnego kodu wykonywalnego z komentarzy.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-170">The compiler does not generate any executable code from comments.</span></span>

## <a name="use-loops-to-repeat-operations"></a><span data-ttu-id="ec2a2-171">Użycie pętli do powtarzania operacji</span><span class="sxs-lookup"><span data-stu-id="ec2a2-171">Use loops to repeat operations</span></span>

<span data-ttu-id="ec2a2-172">W tej sekcji Użyj **pętli** do powtarzania instrukcji.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-172">In this section you use **loops** to repeat statements.</span></span> <span data-ttu-id="ec2a2-173">Wypróbuj ten kod w `Main` metodzie:</span><span class="sxs-lookup"><span data-stu-id="ec2a2-173">Try this code in your `Main` method:</span></span>

```csharp
int counter = 0;
while (counter < 10)
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
}
```

<span data-ttu-id="ec2a2-174">`while` Instrukcja sprawdza warunek i wykonuje instrukcję lub blok instrukcji po `while`.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-174">The `while` statement checks a condition and executes the statement or statement block following the `while`.</span></span> <span data-ttu-id="ec2a2-175">Wielokrotnie sprawdza warunek i wykonuje te instrukcje do momentu, gdy warunek nie ma wartości false.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-175">It repeatedly checks the condition and executing those statements until the condition is false.</span></span>

<span data-ttu-id="ec2a2-176">Ten przykład zawiera jeszcze jeden nowy operator.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-176">There's one other new operator in this example.</span></span> <span data-ttu-id="ec2a2-177">Znaki `++` po zmiennej `counter` oznaczają operator **inkrementacji**.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-177">The `++` after the `counter` variable is the **increment** operator.</span></span> <span data-ttu-id="ec2a2-178">Dodaje 1 do wartości `counter` i zapisuje tę wartość w `counter` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-178">It adds 1 to the value of `counter` and stores that value in the `counter` variable.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ec2a2-179">Upewnij się, że `while` warunek pętli zmieni się na FAŁSZ podczas wykonywania kodu.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-179">Make sure that the `while` loop condition changes to false as you execute the code.</span></span> <span data-ttu-id="ec2a2-180">W przeciwnym razie wystąpi **pętla nieskończona**, czyli wykonywanie programu nigdy się nie skończy.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-180">Otherwise, you create an **infinite loop** where your program never ends.</span></span> <span data-ttu-id="ec2a2-181">Nie jest to pokazane w tym przykładzie, ponieważ trzeba wymusić zamknięcie programu przy użyciu **klawiszy CTRL-C** lub innych.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-181">That is not demonstrated in this sample, because you have to force your program to quit using **CTRL-C** or other means.</span></span>

<span data-ttu-id="ec2a2-182">Pętla `while` testuje warunek przed wykonaniem kodu po instrukcji `while`.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-182">The `while` loop tests the condition before executing the code following the `while`.</span></span> <span data-ttu-id="ec2a2-183">Pętla `do`...`while` najpierw wykonuje kod, a następnie sprawdza warunek.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-183">The `do` ... `while` loop executes the code first, and then checks the condition.</span></span> <span data-ttu-id="ec2a2-184">Pętla do while jest pokazana w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="ec2a2-184">The do while loop is shown in the following code:</span></span>

```csharp
int counter = 0;
do
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
} while (counter < 10);
```

<span data-ttu-id="ec2a2-185">Ta `do` pętla i wcześniejsza `while` pętla tworzą te same dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-185">This `do` loop and the earlier `while` loop produce the same output.</span></span>

## <a name="work-with-the-for-loop"></a><span data-ttu-id="ec2a2-186">Praca z pętlą for</span><span class="sxs-lookup"><span data-stu-id="ec2a2-186">Work with the for loop</span></span>

<span data-ttu-id="ec2a2-187">Pętla **for** jest często używana w języku C#.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-187">The **for** loop is commonly used in C#.</span></span> <span data-ttu-id="ec2a2-188">Wypróbuj ten kod w metodzie Main ():</span><span class="sxs-lookup"><span data-stu-id="ec2a2-188">Try this code in your Main() method:</span></span>

```csharp
for (int index = 0; index < 10; index++)
{
    Console.WriteLine($"Hello World! The index is {index}");
}
```

<span data-ttu-id="ec2a2-189">Działa on tak samo jak już przedstawione pętle `while` i `do`.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-189">This does the same work as the `while` loop and the `do` loop you've already used.</span></span> <span data-ttu-id="ec2a2-190">Instrukcja `for` składa się z trzech części, które sterują jej pracą.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-190">The `for` statement has three parts that control how it works.</span></span>

<span data-ttu-id="ec2a2-191">Pierwsza część to **inicjator for**: `int index = 0;` deklaruje, że `index` jest to zmienna pętli, i ustawia jej wartość początkową `0`na.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-191">The first part is the **for initializer**: `int index = 0;` declares that `index` is the loop variable, and sets its initial value to `0`.</span></span>

<span data-ttu-id="ec2a2-192">Częścią średnią jest **warunek dla**: `index < 10` deklaruje, `for` że ta pętla będzie działać tak długo, jak wartość licznika jest mniejsza niż 10.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-192">The middle part is the **for condition**: `index < 10` declares that this `for` loop continues to execute as long as the value of counter is less than 10.</span></span>

<span data-ttu-id="ec2a2-193">Ostatnia część to **iterator**: `index++` określa, jak zmodyfikować zmienną pętli po wykonaniu bloku po `for` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-193">The final part is the **for iterator**: `index++` specifies how to modify the loop variable after executing the block following the `for` statement.</span></span> <span data-ttu-id="ec2a2-194">Tutaj zdefiniowano, że zmienną `index` należy zwiększyć o 1 po każdym wykonaniu bloku.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-194">Here, it specifies that `index` should be incremented by 1 each time the block executes.</span></span>

<span data-ttu-id="ec2a2-195">Poeksperymentuj samodzielnie z tymi elementami.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-195">Experiment with these yourself.</span></span> <span data-ttu-id="ec2a2-196">Wypróbuj poniższe modyfikacje:</span><span class="sxs-lookup"><span data-stu-id="ec2a2-196">Try each of the following:</span></span>

- <span data-ttu-id="ec2a2-197">Zmień inicjator, tak aby miał inną wartość początkową.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-197">Change the initializer to start at a different value.</span></span>
- <span data-ttu-id="ec2a2-198">Zmień warunek, tak aby zatrzymanie pętli nastąpiło przy innej wartości.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-198">Change the condition to stop at a different value.</span></span>

<span data-ttu-id="ec2a2-199">Gdy skończysz, przejdziemy do samodzielnego pisania kodu, gdzie wykorzystasz zdobyte umiejętności.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-199">When you're done, let's move on to write some code yourself to use what you've learned.</span></span>

## <a name="created-nested-loops"></a><span data-ttu-id="ec2a2-200">Utworzone Pętle zagnieżdżone</span><span class="sxs-lookup"><span data-stu-id="ec2a2-200">Created nested loops</span></span>

<span data-ttu-id="ec2a2-201">Pętla `do` lub `for` może być zagnieżdżona w innej pętli `while`, aby utworzyć macierz przy użyciu kombinacji każdego elementu w pętli zewnętrznej z każdym elementem w wewnętrznej pętli.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-201">A `while`, `do` or `for` loop can be nested inside another loop to create a matrix using the combination of each item in the outer loop with each item in the inner loop.</span></span> <span data-ttu-id="ec2a2-202">Zróbmy to, aby utworzyć zestaw par alfanumerycznych do reprezentowania wierszy i kolumn.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-202">Let's do that to build a set of alphanumeric pairs to represent rows and columns.</span></span>

<span data-ttu-id="ec2a2-203">Jedna `for` pętla może generować wiersze:</span><span class="sxs-lookup"><span data-stu-id="ec2a2-203">One `for` loop can generate the rows:</span></span>

```csharp
for (int row = 1; row < 11; row++)
{
    Console.WriteLine($"The row is {row}");
}
```

<span data-ttu-id="ec2a2-204">Inna pętla może generować kolumny:</span><span class="sxs-lookup"><span data-stu-id="ec2a2-204">Another loop can generate the columns:</span></span>

```csharp
for (char column = 'a'; column < 'k'; column++)
{
    Console.WriteLine($"The column is {column}");
}
```

<span data-ttu-id="ec2a2-205">Można zagnieździć jedną pętlę wewnątrz par:</span><span class="sxs-lookup"><span data-stu-id="ec2a2-205">You can nest one loop inside the other to form pairs:</span></span>

```csharp
for (int row = 1; row < 11; row++)
{
    for (char column = 'a'; column < 'k'; column++)
    {
        Console.WriteLine($"The cell is ({row}, {column})");
    }
}
```

<span data-ttu-id="ec2a2-206">Można zobaczyć, że pętla zewnętrzna przyrostowo rośnie dla każdego pełnego przebiegu pętli wewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-206">You can see that the outer loop increments once for each full run of the inner loop.</span></span> <span data-ttu-id="ec2a2-207">Wycofaj zagnieżdżanie wierszy i kolumn i zobacz zmiany dla siebie.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-207">Reverse the row and column nesting, and see the changes for yourself.</span></span>

## <a name="combine-branches-and-loops"></a><span data-ttu-id="ec2a2-208">Łączenie gałęzi i pętli</span><span class="sxs-lookup"><span data-stu-id="ec2a2-208">Combine branches and loops</span></span>

<span data-ttu-id="ec2a2-209">Teraz, gdy znasz już instrukcję `if` i konstrukcje pętli w języku C#, sprawdź, czy potrafisz napisać kod C# obliczający sumę wszystkich liczb całkowitych z zakresu 1-20 podzielnych przez 3.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-209">Now that you've seen the `if` statement and the looping constructs in the C# language, see if you can write C# code to find the sum of all integers 1 through 20 that are divisible by 3.</span></span>  <span data-ttu-id="ec2a2-210">Oto kilka wskazówek:</span><span class="sxs-lookup"><span data-stu-id="ec2a2-210">Here are a few hints:</span></span>

- <span data-ttu-id="ec2a2-211">Operator `%` umożliwia obliczenie reszty z operacji dzielenia.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-211">The `%` operator gives you the remainder of a division operation.</span></span>
- <span data-ttu-id="ec2a2-212">Instrukcja `if` umożliwia zdefiniowanie warunku określającego, czy liczba powinna być częścią sumy.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-212">The `if` statement gives you the condition to see if a number should be part of the sum.</span></span>
- <span data-ttu-id="ec2a2-213">Pętla `for` ułatwia powtórzenie serii kroków dla wszystkich liczb z zakresu 1-20.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-213">The `for` loop can help you repeat a series of steps for all the numbers 1 through 20.</span></span>

<span data-ttu-id="ec2a2-214">Spróbuj napisać kod.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-214">Try it yourself.</span></span> <span data-ttu-id="ec2a2-215">Następnie wykonaj go, aby dowiedzieć się, jak Ci poszło.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-215">Then check how you did.</span></span> <span data-ttu-id="ec2a2-216">Należy uzyskać 63 na odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-216">You should get 63 for an answer.</span></span> <span data-ttu-id="ec2a2-217">Możesz wyświetlić jedną możliwą odpowiedź, [wyświetlając kod ukończony w serwisie GitHub](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54).</span><span class="sxs-lookup"><span data-stu-id="ec2a2-217">You can see one possible answer by [viewing the completed code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54).</span></span>

<span data-ttu-id="ec2a2-218">Samouczek "gałęzie i pętle" został ukończony.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-218">You've completed the "branches and loops" tutorial.</span></span>

<span data-ttu-id="ec2a2-219">Możesz kontynuować samouczek dotyczący [tablic i kolekcji](arrays-and-collections.md) w Twoim środowisku programistycznym.</span><span class="sxs-lookup"><span data-stu-id="ec2a2-219">You can continue with the [Arrays and collections](arrays-and-collections.md) tutorial in your own development environment.</span></span>

<span data-ttu-id="ec2a2-220">Więcej na temat tych pojęć możesz dowiedzieć się w następujących tematach:</span><span class="sxs-lookup"><span data-stu-id="ec2a2-220">You can learn more about these concepts in these topics:</span></span>

- [<span data-ttu-id="ec2a2-221">if i else, instrukcje</span><span class="sxs-lookup"><span data-stu-id="ec2a2-221">If and else statement</span></span>](../../language-reference/keywords/if-else.md)
- [<span data-ttu-id="ec2a2-222">While, instrukcja</span><span class="sxs-lookup"><span data-stu-id="ec2a2-222">While statement</span></span>](../../language-reference/keywords/while.md)
- [<span data-ttu-id="ec2a2-223">do, instrukcja</span><span class="sxs-lookup"><span data-stu-id="ec2a2-223">Do statement</span></span>](../../language-reference/keywords/do.md)
- [<span data-ttu-id="ec2a2-224">For — instrukcja</span><span class="sxs-lookup"><span data-stu-id="ec2a2-224">For statement</span></span>](../../language-reference/keywords/for.md)

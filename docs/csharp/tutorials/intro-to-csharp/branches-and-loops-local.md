---
title: Gałęzie i pętle — C# wprowadzenie do samouczka
description: W tym samouczku dotyczącej gałęzi i pętli można C# napisać kod, aby poznać składnię języka, która obsługuje gałęzie warunkowe, i pętle do wykonywania instrukcji wielokrotnie.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: 44b634e3c2120116ee7fd66770398a6b66c8ed8c
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73739125"
---
# <a name="learn-conditional-logic-with-branch-and-loop-statements"></a><span data-ttu-id="ec810-103">Informacje o logice warunkowej przy użyciu instrukcji Branch i Loop</span><span class="sxs-lookup"><span data-stu-id="ec810-103">Learn conditional logic with branch and loop statements</span></span>

<span data-ttu-id="ec810-104">W tym samouczku przedstawiono sposób pisania kodu, który analizuje zmienne i zmienia ścieżkę wykonywania na podstawie tych zmiennych.</span><span class="sxs-lookup"><span data-stu-id="ec810-104">This tutorial teaches you how to write code that examines variables and changes the execution path based on those variables.</span></span> <span data-ttu-id="ec810-105">Napiszesz C# kod i zobaczysz wyniki kompilacji i uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="ec810-105">You write C# code and see the results of compiling and running it.</span></span> <span data-ttu-id="ec810-106">Samouczek zawiera szereg lekcji, które eksplorują gałęzie i konstrukcje w pętli w C#.</span><span class="sxs-lookup"><span data-stu-id="ec810-106">The tutorial contains a series of lessons that explore branching and looping constructs in C#.</span></span> <span data-ttu-id="ec810-107">Te lekcje uczyją się podstaw C# języka.</span><span class="sxs-lookup"><span data-stu-id="ec810-107">These lessons teach you the fundamentals of the C# language.</span></span>

<span data-ttu-id="ec810-108">Ten samouczek oczekuje, że masz maszynę, której możesz użyć do programowania.</span><span class="sxs-lookup"><span data-stu-id="ec810-108">This tutorial expects you to have a machine you can use for development.</span></span> <span data-ttu-id="ec810-109">Samouczek platformy .NET [Hello World w ciągu 10 minut](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) zawiera instrukcje dotyczące konfigurowania lokalnego środowiska deweloperskiego w systemie Windows, Linux lub macOS.</span><span class="sxs-lookup"><span data-stu-id="ec810-109">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span> <span data-ttu-id="ec810-110">Krótkie omówienie poleceń, z których będziesz korzystać, znajduje się w zapoznanie [z narzędziami programistycznymi](local-environment.md) zawierającymi linki do dalszych szczegółów.</span><span class="sxs-lookup"><span data-stu-id="ec810-110">A quick overview of the commands you'll use is in the [Become familiar with the development tools](local-environment.md) with links to more details.</span></span>

## <a name="make-decisions-using-the-if-statement"></a><span data-ttu-id="ec810-111">Podejmowanie decyzji przy użyciu instrukcji `if`</span><span class="sxs-lookup"><span data-stu-id="ec810-111">Make decisions using the `if` statement</span></span>

<span data-ttu-id="ec810-112">Utwórz katalog o nazwie *branchs — samouczek*.</span><span class="sxs-lookup"><span data-stu-id="ec810-112">Create a directory named *branches-tutorial*.</span></span> <span data-ttu-id="ec810-113">Upewnij się, że bieżący katalog i uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="ec810-113">Make that the current directory and run the following command:</span></span>

```dotnetcli
dotnet new console -n BranchesAndLoops -o .
```

<span data-ttu-id="ec810-114">To polecenie powoduje utworzenie nowej aplikacji konsolowej .NET Core w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="ec810-114">This command creates a new .NET Core console application in the current directory.</span></span>

<span data-ttu-id="ec810-115">Otwórz *program.cs* w ulubionym edytorze i Zastąp wiersz `Console.WriteLine("Hello World!");` następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="ec810-115">Open *Program.cs* in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following code:</span></span>

```csharp
int a = 5;
int b = 6;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10.");
```

<span data-ttu-id="ec810-116">Wypróbuj ten kod, wpisując `dotnet run` w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="ec810-116">Try this code by typing `dotnet run` in your console window.</span></span> <span data-ttu-id="ec810-117">Powinien zostać wyświetlony komunikat "odpowiedź jest większa niż 10".</span><span class="sxs-lookup"><span data-stu-id="ec810-117">You should see the message "The answer is greater than 10."</span></span> <span data-ttu-id="ec810-118">Wydrukowano w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="ec810-118">printed to your console.</span></span>

<span data-ttu-id="ec810-119">Zmodyfikuj deklarację `b`, aby suma była mniejsza niż 10:</span><span class="sxs-lookup"><span data-stu-id="ec810-119">Modify the declaration of `b` so that the sum is less than 10:</span></span>

```csharp
int b = 3;
```

<span data-ttu-id="ec810-120">Wpisz ponownie `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="ec810-120">Type `dotnet run` again.</span></span> <span data-ttu-id="ec810-121">Ponieważ odpowiedź jest mniejsza niż 10, nic nie jest drukowane.</span><span class="sxs-lookup"><span data-stu-id="ec810-121">Because the answer is less than 10, nothing is printed.</span></span> <span data-ttu-id="ec810-122">Testowany **warunek** ma wartość false.</span><span class="sxs-lookup"><span data-stu-id="ec810-122">The **condition** you're testing is false.</span></span> <span data-ttu-id="ec810-123">Nie masz żadnego kodu do wykonania, ponieważ Zapisano tylko jedną z możliwych gałęzi dla instrukcji `if`: gałąź true.</span><span class="sxs-lookup"><span data-stu-id="ec810-123">You don't have any code to execute because you've only written one of the possible branches for an `if` statement: the true branch.</span></span>

> [!TIP]
> <span data-ttu-id="ec810-124">Podczas eksplorowania C# (lub dowolnego języka programowania) nastąpi pomyłki podczas pisania kodu.</span><span class="sxs-lookup"><span data-stu-id="ec810-124">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="ec810-125">Kompilator znajdzie i zgłosi błędy.</span><span class="sxs-lookup"><span data-stu-id="ec810-125">The compiler will find and report the errors.</span></span> <span data-ttu-id="ec810-126">Sprawdź blisko danych wyjściowych błędu i kod, który wygenerował błąd.</span><span class="sxs-lookup"><span data-stu-id="ec810-126">Look closely at the error output and the code that generated the error.</span></span> <span data-ttu-id="ec810-127">Błąd kompilatora może zwykle pomóc w znalezieniu problemu.</span><span class="sxs-lookup"><span data-stu-id="ec810-127">The compiler error can usually help you find the problem.</span></span>

<span data-ttu-id="ec810-128">Ten pierwszy przykład pokazuje moc `if` i typów logicznych.</span><span class="sxs-lookup"><span data-stu-id="ec810-128">This first sample shows the power of `if` and Boolean types.</span></span> <span data-ttu-id="ec810-129">*Wartość logiczna* to zmienna, która może mieć jedną z dwóch wartości: `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="ec810-129">A *Boolean* is a variable that can have one of two values: `true` or `false`.</span></span> <span data-ttu-id="ec810-130">C#definiuje typ specjalny, `bool` dla zmiennych logicznych.</span><span class="sxs-lookup"><span data-stu-id="ec810-130">C# defines a special type, `bool` for Boolean variables.</span></span> <span data-ttu-id="ec810-131">Instrukcja `if` sprawdza wartość `bool`.</span><span class="sxs-lookup"><span data-stu-id="ec810-131">The `if` statement checks the value of a `bool`.</span></span> <span data-ttu-id="ec810-132">Gdy wartość jest `true`, zostanie wykonana instrukcja po `if`.</span><span class="sxs-lookup"><span data-stu-id="ec810-132">When the value is `true`, the statement following the `if` executes.</span></span> <span data-ttu-id="ec810-133">W przeciwnym razie zostanie pominięty.</span><span class="sxs-lookup"><span data-stu-id="ec810-133">Otherwise, it is skipped.</span></span>

<span data-ttu-id="ec810-134">Ten proces sprawdzania warunków i wykonywania instrukcji na podstawie tych warunków jest bardzo wydajny.</span><span class="sxs-lookup"><span data-stu-id="ec810-134">This process of checking conditions and executing statements based on those conditions is very powerful.</span></span>

## <a name="make-if-and-else-work-together"></a><span data-ttu-id="ec810-135">Utwórz, jeśli i else współpracują ze sobą</span><span class="sxs-lookup"><span data-stu-id="ec810-135">Make if and else work together</span></span>

<span data-ttu-id="ec810-136">Aby wykonać inny kod zarówno dla gałęzi prawdy, jak i fałszywych, należy utworzyć gałąź `else`, która jest wykonywana, gdy warunek ma wartość false.</span><span class="sxs-lookup"><span data-stu-id="ec810-136">To execute different code in both the true and false branches, you create an `else` branch that executes when the condition is false.</span></span> <span data-ttu-id="ec810-137">Wypróbuj to.</span><span class="sxs-lookup"><span data-stu-id="ec810-137">Try this.</span></span> <span data-ttu-id="ec810-138">Dodaj ostatnie dwa wiersze w poniższym kodzie do metody `Main` (należy mieć już pierwsze cztery):</span><span class="sxs-lookup"><span data-stu-id="ec810-138">Add the last two lines in the code below to your `Main` method (you should already have the first four):</span></span>

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10");
else
    Console.WriteLine("The answer is not greater than 10");
```

<span data-ttu-id="ec810-139">Instrukcja po słowie kluczowym `else` wykonuje się tylko wtedy, gdy testowany warunek jest `false`.</span><span class="sxs-lookup"><span data-stu-id="ec810-139">The statement following the `else` keyword executes only when the condition being tested is `false`.</span></span> <span data-ttu-id="ec810-140">Łączenie `if` i `else` z warunkami logicznymi zapewnia wszystko, co jest potrzebne do obsługi zarówno `true`, jak i `false`.</span><span class="sxs-lookup"><span data-stu-id="ec810-140">Combining `if` and `else` with Boolean conditions provides all the power you need to handle both a `true` and a `false` condition.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ec810-141">Wcięcia pod instrukcjami `if` i `else` są przeznaczone dla czytników ludzkich.</span><span class="sxs-lookup"><span data-stu-id="ec810-141">The indentation under the `if` and `else` statements is for human readers.</span></span>
> <span data-ttu-id="ec810-142">C# Język nie traktuje wcięcia ani odstępu jako znaczącego.</span><span class="sxs-lookup"><span data-stu-id="ec810-142">The C# language doesn't treat indentation or white space as significant.</span></span>
> <span data-ttu-id="ec810-143">Instrukcja po słowie kluczowym `if` lub `else` zostanie wykonana na podstawie warunku.</span><span class="sxs-lookup"><span data-stu-id="ec810-143">The statement following the `if` or `else` keyword will be executed based on the condition.</span></span> <span data-ttu-id="ec810-144">Wszystkie przykłady w tym samouczku są zgodne ze wspólną metodą tworzenia wcięć wierszy na podstawie przepływu sterowania instrukcji.</span><span class="sxs-lookup"><span data-stu-id="ec810-144">All the samples in this tutorial follow a common practice to indent lines based on the control flow of statements.</span></span>

<span data-ttu-id="ec810-145">Ponieważ wcięcia nie są znaczące, należy użyć `{` i `}`, aby wskazać, Kiedy chcesz, aby więcej niż jedna instrukcja była częścią bloku, który jest wykonywany warunkowo.</span><span class="sxs-lookup"><span data-stu-id="ec810-145">Because indentation is not significant, you need to use `{` and `}` to indicate when you want more than one statement to be part of the block that executes conditionally.</span></span> <span data-ttu-id="ec810-146">C#programiści zwykle używają tych nawiasów klamrowych we wszystkich klauzulach `if` i `else`.</span><span class="sxs-lookup"><span data-stu-id="ec810-146">C# programmers typically use those braces on all `if` and `else` clauses.</span></span> <span data-ttu-id="ec810-147">Poniższy przykład jest taki sam jak właśnie utworzony.</span><span class="sxs-lookup"><span data-stu-id="ec810-147">The following example is the same as the one you just created.</span></span> <span data-ttu-id="ec810-148">Zmodyfikuj kod powyżej, aby był zgodny z następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="ec810-148">Modify your code above to match the following code:</span></span>

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
> <span data-ttu-id="ec810-149">W pozostałej części tego samouczka wszystkie przykłady kodu zawierają nawiasy klamrowe, po zastosowaniu zaakceptowanych praktyk.</span><span class="sxs-lookup"><span data-stu-id="ec810-149">Through the rest of this tutorial, the code samples all include the braces, following accepted practices.</span></span>

<span data-ttu-id="ec810-150">Możesz przetestować bardziej skomplikowane warunki.</span><span class="sxs-lookup"><span data-stu-id="ec810-150">You can test more complicated conditions.</span></span> <span data-ttu-id="ec810-151">Dodaj następujący kod w metodzie `Main` po kodzie, który zapisano do tej pory:</span><span class="sxs-lookup"><span data-stu-id="ec810-151">Add the following code in your `Main` method after the code you've written so far:</span></span>

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

<span data-ttu-id="ec810-152">Symbol `==` sprawdza *równość*.</span><span class="sxs-lookup"><span data-stu-id="ec810-152">The `==` symbol tests for *equality*.</span></span> <span data-ttu-id="ec810-153">Przy użyciu `==` odróżnia test pod kątem równości od przydziału, który został wyświetlony w `a = 5`.</span><span class="sxs-lookup"><span data-stu-id="ec810-153">Using `==` distinguishes the test for equality from assignment, which you saw in `a = 5`.</span></span>

<span data-ttu-id="ec810-154">`&&` reprezentuje "i".</span><span class="sxs-lookup"><span data-stu-id="ec810-154">The `&&` represents "and".</span></span> <span data-ttu-id="ec810-155">Oznacza to, że oba warunki muszą mieć wartość true, aby wykonać instrukcję w gałęzi prawdy.</span><span class="sxs-lookup"><span data-stu-id="ec810-155">It means both conditions must be true to execute the statement in the true branch.</span></span>  <span data-ttu-id="ec810-156">Te przykłady pokazują również, że można mieć wiele instrukcji w każdej gałęzi warunkowej, pod warunkiem, że zostały one ujęte w `{` i `}`.</span><span class="sxs-lookup"><span data-stu-id="ec810-156">These examples also show that you can have multiple statements in each conditional branch, provided you enclose them in `{` and `}`.</span></span>

<span data-ttu-id="ec810-157">Można również użyć `||` do reprezentowania "lub".</span><span class="sxs-lookup"><span data-stu-id="ec810-157">You can also use  `||` to represent "or".</span></span> <span data-ttu-id="ec810-158">Dodaj następujący kod po wykonaniu tej czynności:</span><span class="sxs-lookup"><span data-stu-id="ec810-158">Add the following code after what you've written so far:</span></span>

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

<span data-ttu-id="ec810-159">Zmodyfikuj wartości `a`, `b` i `c` i przełączenie między `&&` i `||` do eksplorowania.</span><span class="sxs-lookup"><span data-stu-id="ec810-159">Modify the values of `a`, `b`, and `c` and switch between `&&` and `||` to explore.</span></span> <span data-ttu-id="ec810-160">Dowiesz się, jak działają operatory `&&` i `||`.</span><span class="sxs-lookup"><span data-stu-id="ec810-160">You'll gain more understanding of how the `&&` and `||` operators work.</span></span>

<span data-ttu-id="ec810-161">Wykonano pierwszy krok.</span><span class="sxs-lookup"><span data-stu-id="ec810-161">You've finished the first step.</span></span> <span data-ttu-id="ec810-162">Przed rozpoczęciem następnej sekcji przechodźmy bieżący kod w oddzielną metodę.</span><span class="sxs-lookup"><span data-stu-id="ec810-162">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="ec810-163">Ułatwia to rozpoczęcie pracy z nowym przykładem.</span><span class="sxs-lookup"><span data-stu-id="ec810-163">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="ec810-164">Zmień nazwę metody `Main`, aby `ExploreIf` i napisać nową metodę `Main`, która wywoła `ExploreIf`.</span><span class="sxs-lookup"><span data-stu-id="ec810-164">Rename your `Main` method to `ExploreIf` and write a new `Main` method that calls `ExploreIf`.</span></span> <span data-ttu-id="ec810-165">Po zakończeniu kod powinien wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="ec810-165">When you have finished, your code should look like this:</span></span>

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

<span data-ttu-id="ec810-166">Dodaj komentarz do wywołania `ExploreIf()`.</span><span class="sxs-lookup"><span data-stu-id="ec810-166">Comment out the call to `ExploreIf()`.</span></span> <span data-ttu-id="ec810-167">Dane wyjściowe będą mniej czytelne podczas pracy w tej sekcji:</span><span class="sxs-lookup"><span data-stu-id="ec810-167">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//ExploreIf();
```

<span data-ttu-id="ec810-168">`//` uruchamia **komentarz** w C#.</span><span class="sxs-lookup"><span data-stu-id="ec810-168">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="ec810-169">Komentarze są dowolnym tekstem, który chcesz zachować w kodzie źródłowym, ale nie można go wykonać jako kod.</span><span class="sxs-lookup"><span data-stu-id="ec810-169">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="ec810-170">Kompilator nie generuje żadnego kodu wykonywalnego z komentarzy.</span><span class="sxs-lookup"><span data-stu-id="ec810-170">The compiler does not generate any executable code from comments.</span></span>

## <a name="use-loops-to-repeat-operations"></a><span data-ttu-id="ec810-171">Używanie pętli do powtarzania operacji</span><span class="sxs-lookup"><span data-stu-id="ec810-171">Use loops to repeat operations</span></span>

<span data-ttu-id="ec810-172">W tej sekcji Użyj **pętli** do powtarzania instrukcji.</span><span class="sxs-lookup"><span data-stu-id="ec810-172">In this section you use **loops** to repeat statements.</span></span> <span data-ttu-id="ec810-173">Wypróbuj ten kod w metodzie `Main`:</span><span class="sxs-lookup"><span data-stu-id="ec810-173">Try this code in your `Main` method:</span></span>

```csharp
int counter = 0;
while (counter < 10)
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
}
```

<span data-ttu-id="ec810-174">Instrukcja `while` sprawdza warunek i wykonuje instrukcję lub blok instrukcji po `while`.</span><span class="sxs-lookup"><span data-stu-id="ec810-174">The `while` statement checks a condition and executes the statement or statement block following the `while`.</span></span> <span data-ttu-id="ec810-175">Wielokrotnie sprawdza warunek i wykonuje te instrukcje do momentu, gdy warunek nie ma wartości false.</span><span class="sxs-lookup"><span data-stu-id="ec810-175">It repeatedly checks the condition and executing those statements until the condition is false.</span></span>

<span data-ttu-id="ec810-176">W tym przykładzie istnieje jeden inny operator new.</span><span class="sxs-lookup"><span data-stu-id="ec810-176">There's one other new operator in this example.</span></span> <span data-ttu-id="ec810-177">`++` po zmiennej `counter` jest operatorem **przyrostu** .</span><span class="sxs-lookup"><span data-stu-id="ec810-177">The `++` after the `counter` variable is the **increment** operator.</span></span> <span data-ttu-id="ec810-178">Dodaje 1 do wartości `counter` i zapisuje tę wartość w zmiennej `counter`.</span><span class="sxs-lookup"><span data-stu-id="ec810-178">It adds 1 to the value of `counter` and stores that value in the `counter` variable.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ec810-179">Upewnij się, że warunek pętli `while` zmieni się na FAŁSZ podczas wykonywania kodu.</span><span class="sxs-lookup"><span data-stu-id="ec810-179">Make sure that the `while` loop condition changes to false as you execute the code.</span></span> <span data-ttu-id="ec810-180">W przeciwnym razie utworzysz **nieskończoną pętlę** , w której program nigdy się nie skończy.</span><span class="sxs-lookup"><span data-stu-id="ec810-180">Otherwise, you create an **infinite loop** where your program never ends.</span></span> <span data-ttu-id="ec810-181">Nie jest to pokazane w tym przykładzie, ponieważ trzeba wymusić zamknięcie programu przy użyciu **klawiszy CTRL-C** lub innych.</span><span class="sxs-lookup"><span data-stu-id="ec810-181">That is not demonstrated in this sample, because you have to force your program to quit using **CTRL-C** or other means.</span></span>

<span data-ttu-id="ec810-182">Pętla `while` sprawdza warunek przed wykonaniem kodu następującego po `while`.</span><span class="sxs-lookup"><span data-stu-id="ec810-182">The `while` loop tests the condition before executing the code following the `while`.</span></span> <span data-ttu-id="ec810-183">Pętla `do`... `while` wykonuje najpierw kod, a następnie sprawdza warunek.</span><span class="sxs-lookup"><span data-stu-id="ec810-183">The `do` ... `while` loop executes the code first, and then checks the condition.</span></span> <span data-ttu-id="ec810-184">Pętla do while jest pokazana w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="ec810-184">The do while loop is shown in the following code:</span></span>

```csharp
int counter = 0;
do
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
} while (counter < 10);
```

<span data-ttu-id="ec810-185">Ta pętla `do` i wcześniejsza pętla `while` tworzą te same dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="ec810-185">This `do` loop and the earlier `while` loop produce the same output.</span></span>

## <a name="work-with-the-for-loop"></a><span data-ttu-id="ec810-186">Pracuj z pętlą for</span><span class="sxs-lookup"><span data-stu-id="ec810-186">Work with the for loop</span></span>

<span data-ttu-id="ec810-187">Pętla **for** jest często używana w C#.</span><span class="sxs-lookup"><span data-stu-id="ec810-187">The **for** loop is commonly used in C#.</span></span> <span data-ttu-id="ec810-188">Wypróbuj ten kod w metodzie Main ():</span><span class="sxs-lookup"><span data-stu-id="ec810-188">Try this code in your Main() method:</span></span>

```csharp
for (int index = 0; index < 10; index++)
{
    Console.WriteLine($"Hello World! The index is {index}");
}
```

<span data-ttu-id="ec810-189">To działa tak samo jak w przypadku pętli `while` i pętli `do`, która została już użyta.</span><span class="sxs-lookup"><span data-stu-id="ec810-189">This does the same work as the `while` loop and the `do` loop you've already used.</span></span> <span data-ttu-id="ec810-190">Instrukcja `for` zawiera trzy części, które kontrolują sposób działania.</span><span class="sxs-lookup"><span data-stu-id="ec810-190">The `for` statement has three parts that control how it works.</span></span>

<span data-ttu-id="ec810-191">Pierwsza część to **inicjator for**: `int index = 0;` deklaruje, że `index` jest zmienną Loop i ustawia jej wartość początkową na `0`.</span><span class="sxs-lookup"><span data-stu-id="ec810-191">The first part is the **for initializer**: `int index = 0;` declares that `index` is the loop variable, and sets its initial value to `0`.</span></span>

<span data-ttu-id="ec810-192">Częścią średnią jest **warunek dla**: `index < 10` deklaruje, że ta pętla `for` będzie działać tak długo, jak wartość licznika jest mniejsza niż 10.</span><span class="sxs-lookup"><span data-stu-id="ec810-192">The middle part is the **for condition**: `index < 10` declares that this `for` loop continues to execute as long as the value of counter is less than 10.</span></span>

<span data-ttu-id="ec810-193">Ostatnia część to **iterator for**: `index++` określa, jak zmodyfikować zmienną pętli po wykonaniu bloku po instrukcji `for`.</span><span class="sxs-lookup"><span data-stu-id="ec810-193">The final part is the **for iterator**: `index++` specifies how to modify the loop variable after executing the block following the `for` statement.</span></span> <span data-ttu-id="ec810-194">W tym miejscu określa, że wartość `index` powinna być zwiększana o 1 przy każdym uruchomieniu bloku.</span><span class="sxs-lookup"><span data-stu-id="ec810-194">Here, it specifies that `index` should be incremented by 1 each time the block executes.</span></span>

<span data-ttu-id="ec810-195">Wypróbuj je samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="ec810-195">Experiment with these yourself.</span></span> <span data-ttu-id="ec810-196">Spróbuj wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="ec810-196">Try each of the following:</span></span>

- <span data-ttu-id="ec810-197">Zmień inicjator tak, aby był uruchamiany z inną wartością.</span><span class="sxs-lookup"><span data-stu-id="ec810-197">Change the initializer to start at a different value.</span></span>
- <span data-ttu-id="ec810-198">Zmień warunek, aby zatrzymać z inną wartością.</span><span class="sxs-lookup"><span data-stu-id="ec810-198">Change the condition to stop at a different value.</span></span>

<span data-ttu-id="ec810-199">Gdy skończysz, przyjrzyjmy się, aby samodzielnie napisać kod, aby użyć informacji, które znasz.</span><span class="sxs-lookup"><span data-stu-id="ec810-199">When you're done, let's move on to write some code yourself to use what you've learned.</span></span>

## <a name="combine-branches-and-loops"></a><span data-ttu-id="ec810-200">Połącz gałęzie i pętle</span><span class="sxs-lookup"><span data-stu-id="ec810-200">Combine branches and loops</span></span>

<span data-ttu-id="ec810-201">Po zapoznaniu się z instrukcją `if` i konstrukcjami pętli w C# języku Sprawdź, czy można napisać C# kod, aby znaleźć sumę wszystkich liczb całkowitych od 1 do 20, które są podzielne przez 3.</span><span class="sxs-lookup"><span data-stu-id="ec810-201">Now that you've seen the `if` statement and the looping constructs in the C# language, see if you can write C# code to find the sum of all integers 1 through 20 that are divisible by 3.</span></span>  <span data-ttu-id="ec810-202">Oto kilka wskazówek:</span><span class="sxs-lookup"><span data-stu-id="ec810-202">Here are a few hints:</span></span>

- <span data-ttu-id="ec810-203">Operator `%` zapewnia pozostałą część operacji dzielenia.</span><span class="sxs-lookup"><span data-stu-id="ec810-203">The `%` operator gives you the remainder of a division operation.</span></span>
- <span data-ttu-id="ec810-204">Instrukcja `if` zapewnia warunek, aby sprawdzić, czy liczba powinna być częścią sumy.</span><span class="sxs-lookup"><span data-stu-id="ec810-204">The `if` statement gives you the condition to see if a number should be part of the sum.</span></span>
- <span data-ttu-id="ec810-205">Pętla `for` może pomóc powtórzyć serię kroków dla wszystkich liczb od 1 do 20.</span><span class="sxs-lookup"><span data-stu-id="ec810-205">The `for` loop can help you repeat a series of steps for all the numbers 1 through 20.</span></span>

<span data-ttu-id="ec810-206">Wypróbuj siebie.</span><span class="sxs-lookup"><span data-stu-id="ec810-206">Try it yourself.</span></span> <span data-ttu-id="ec810-207">Następnie sprawdź, jak to się stało.</span><span class="sxs-lookup"><span data-stu-id="ec810-207">Then check how you did.</span></span> <span data-ttu-id="ec810-208">Należy uzyskać 63 na odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="ec810-208">You should get 63 for an answer.</span></span> <span data-ttu-id="ec810-209">Możesz wyświetlić jedną możliwą odpowiedź, [wyświetlając kod ukończony w serwisie GitHub](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54).</span><span class="sxs-lookup"><span data-stu-id="ec810-209">You can see one possible answer by [viewing the completed code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54).</span></span>

<span data-ttu-id="ec810-210">Samouczek "gałęzie i pętle" został ukończony.</span><span class="sxs-lookup"><span data-stu-id="ec810-210">You've completed the "branches and loops" tutorial.</span></span>

<span data-ttu-id="ec810-211">Możesz kontynuować samouczek dotyczący [tablic i kolekcji](arrays-and-collections.md) w Twoim środowisku programistycznym.</span><span class="sxs-lookup"><span data-stu-id="ec810-211">You can continue with the [Arrays and collections](arrays-and-collections.md) tutorial in your own development environment.</span></span>

<span data-ttu-id="ec810-212">Więcej informacji na temat tych pojęć można znaleźć w następujących tematach:</span><span class="sxs-lookup"><span data-stu-id="ec810-212">You can learn more about these concepts in these topics:</span></span>

- [<span data-ttu-id="ec810-213">Instrukcja if i else</span><span class="sxs-lookup"><span data-stu-id="ec810-213">If and else statement</span></span>](../../language-reference/keywords/if-else.md)
- [<span data-ttu-id="ec810-214">While, instrukcja</span><span class="sxs-lookup"><span data-stu-id="ec810-214">While statement</span></span>](../../language-reference/keywords/while.md)
- [<span data-ttu-id="ec810-215">Do — instrukcja</span><span class="sxs-lookup"><span data-stu-id="ec810-215">Do statement</span></span>](../../language-reference/keywords/do.md)
- [<span data-ttu-id="ec810-216">For — instrukcja</span><span class="sxs-lookup"><span data-stu-id="ec810-216">For statement</span></span>](../../language-reference/keywords/for.md)

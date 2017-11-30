---
title: "Szybki Start - gałęzie i lops — przewodnik C#"
description: "W tym szybki start dotyczące gałęzi i pętle pisania kodu C#, aby eksplorować składni języka, obsługującego warunkowych gałęzi i pętli do wykonywania instrukcji wielokrotnie."
author: billwagner
ms.author: wiwagn
ms.date: 10/31/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 4b077a29cf42072a93b054f50a13a4580ad54304
ms.sourcegitcommit: 43c656811dd38a66a6672084c65d10c0cbbf2015
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2017
---
# <a name="branches-and-loops"></a><span data-ttu-id="a9a7c-103">Gałęzie i pętli</span><span class="sxs-lookup"><span data-stu-id="a9a7c-103">Branches and loops</span></span>

<span data-ttu-id="a9a7c-104">To szybki start jest przedstawienie sposobu pisania kodu, który sprawdza zmienne i zmieniona ścieżka wykonywania na podstawie tych zmiennych.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-104">This quick start teaches you how to write code that examines variables and changes the execution path based on those variables.</span></span> <span data-ttu-id="a9a7c-105">Pisanie kodu C# i wyświetlić wyniki kompilowania i uruchamiania go.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-105">You write C# code and see the results of compiling and running it.</span></span> <span data-ttu-id="a9a7c-106">Szybki start zawiera szereg lekcje, które eksplorować rozgałęzianie i zapętlenia konstrukcje w języku C#.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-106">The quick start contains a series of lessons that explore branching and looping constructs in C#.</span></span> <span data-ttu-id="a9a7c-107">Że wnioski uczy również podstaw programu w języku C#.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-107">These lessons teach you the fundamentals of the C# language.</span></span>

<span data-ttu-id="a9a7c-108">To szybki start oczekuje posiadania maszynie, która służy do tworzenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-108">This quick start expects you to have a machine you can use for development.</span></span> <span data-ttu-id="a9a7c-109">Temat .NET [wprowadzenie w ciągu 10 minut](https://www.microsoft.com/net/core) zawiera instrukcje dotyczące konfigurowania środowiska deweloperskiego lokalnego Mac, komputera lub Linux.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-109">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span>

## <a name="make-decisions-using-the-if-statement"></a><span data-ttu-id="a9a7c-110">Podejmowanie decyzji przy użyciu `if` — instrukcja</span><span class="sxs-lookup"><span data-stu-id="a9a7c-110">Make decisions using the `if` statement</span></span>

<span data-ttu-id="a9a7c-111">Utwórz katalog o nazwie **szybkiego startu gałęzie**.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-111">Create a directory named **branches-quickstart**.</span></span> <span data-ttu-id="a9a7c-112">Upewnij, że bieżący katalog i uruchom `dotnet new console -n BranchesAndLoops -o .`.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-112">Make that the current directory and run `dotnet new console -n BranchesAndLoops -o .`.</span></span> <span data-ttu-id="a9a7c-113">To polecenie tworzy nową aplikację konsolową .NET Core w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-113">This command creates a new .NET Core console application in the current directory.</span></span> 

<span data-ttu-id="a9a7c-114">Otwórz **Program.cs** ulubionego edytora i Zastąp linię `Console.Writeline("Hello World!");` następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="a9a7c-114">Open **Program.cs** in your favorite editor, and replace the line `Console.Writeline("Hello World!");` with the following code:</span></span>

```csharp
int a = 5;
int b = 6;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10.");
```

<span data-ttu-id="a9a7c-115">Spróbuj ten kod, wpisując `dotnet run` w okna konsoli.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-115">Try this code by typing `dotnet run` in the your console window.</span></span> <span data-ttu-id="a9a7c-116">Powinien zostać wyświetlony komunikat "odpowiedź jest większa niż 10".</span><span class="sxs-lookup"><span data-stu-id="a9a7c-116">You should see the message "The answer is greater than 10."</span></span> <span data-ttu-id="a9a7c-117">podane do konsoli.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-117">printed to your console.</span></span>

<span data-ttu-id="a9a7c-118">Modyfikowanie deklaracja `b` , tak aby suma była mniejsza niż 10:</span><span class="sxs-lookup"><span data-stu-id="a9a7c-118">Modify the declaration of `b` so that the sum is less than 10:</span></span> 

```csharp
int b = 3;
```

<span data-ttu-id="a9a7c-119">Typ `dotnet run` ponownie.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-119">Type `dotnet run` again.</span></span> <span data-ttu-id="a9a7c-120">Ponieważ odpowiedź jest mniejsza niż 10, nic nie jest wydrukowane.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-120">Because the answer is less than 10, nothing is printed.</span></span> <span data-ttu-id="a9a7c-121">**Warunku** jesteś testowania ma wartość false.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-121">The **condition** you're testing is false.</span></span> <span data-ttu-id="a9a7c-122">Nie masz żadnych kod do wykonania, ponieważ został zapisany tylko jedną z możliwych gałęzi dla `if` instrukcji: gałąź prawdy.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-122">You don't have any code to execute because you've only written one of the possible branches for an `if` statement: the true branch.</span></span>

> [!TIP]
> <span data-ttu-id="a9a7c-123">Ci poznać platformę C# (lub dowolnego języka programowania), należy podjąć błędów podczas pisania kodu.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-123">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="a9a7c-124">Kompilator znajdzie i raportów o błędach.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-124">The compiler will find and report the errors.</span></span> <span data-ttu-id="a9a7c-125">Przeglądanie błędów wyjścia i kod, który wygenerował błąd.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-125">Look closely the the error output and the code that generated the error.</span></span> <span data-ttu-id="a9a7c-126">Błąd compler zwykle może pomóc w znalezieniu problem.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-126">The compler error can usually help you find the problem.</span></span> 

<span data-ttu-id="a9a7c-127">W tym przykładzie pierwsze pokazano możliwości `if` i typów logicznych.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-127">This first sample shows the power of `if` and Boolean types.</span></span> <span data-ttu-id="a9a7c-128">A *logiczna* jest zmienna, która może mieć jedną z dwóch wartości: `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-128">A *Boolean* is a variable that can have one of two values: `true` or `false`.</span></span> <span data-ttu-id="a9a7c-129">C# definiuje specjalny typ `bool` dla zmienne typu Boolean.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-129">C# defines a special type, `bool` for Boolean variables.</span></span> <span data-ttu-id="a9a7c-130">`if` Instrukcji sprawdza wartość `bool`.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-130">The `if` statement checks the value of a `bool`.</span></span> <span data-ttu-id="a9a7c-131">Jeśli wartość jest `true`, instrukcji następującej `if` wykonuje.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-131">When the value is `true`, the statement following the `if` executes.</span></span> <span data-ttu-id="a9a7c-132">W przeciwnym razie zostanie pominięte.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-132">Otherwise, it is skipped.</span></span> 

<span data-ttu-id="a9a7c-133">Ten proces sprawdzania warunków i wykonywanie instrukcji na podstawie tych warunków jest bardzo zaawansowaną.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-133">This process of checking conditions and executing statements based on those conditions is very powerful.</span></span>


## <a name="make-if-and-else-work-together"></a><span data-ttu-id="a9a7c-134">Upewnij się, jeśli i else współpracują ze sobą</span><span class="sxs-lookup"><span data-stu-id="a9a7c-134">Make if and else work together</span></span>

<span data-ttu-id="a9a7c-135">Aby wykonać inny kod w gałęzi true i false, należy utworzyć `else` gałęzi, która wykonuje, gdy warunek ma wartość false.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-135">To execute different code in both the true and false branches, you create an `else` branch that executes when the condition is false.</span></span> <span data-ttu-id="a9a7c-136">Skorzystaj z tej.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-136">Try this.</span></span> <span data-ttu-id="a9a7c-137">Dodaj ostatnie dwa wiersze w poniższym kodzie do Twojej `Main` — metoda (powinna już być pierwsze cztery):</span><span class="sxs-lookup"><span data-stu-id="a9a7c-137">Add the last two lines in the code below to your `Main` method (you should already have the first four):</span></span>

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10");
else
    Console.WriteLine("The answer is not greater than 10");
```

<span data-ttu-id="a9a7c-138">Poniższa instrukcja `else` — słowo kluczowe jest wykonywana tylko wtedy, gdy warunek testowana jest `false`.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-138">The statement following the `else` keyword executes only when the condition being tested is `false`.</span></span> <span data-ttu-id="a9a7c-139">Łączenie `if` i `else` z logiczną warunki zawiera wszystkie możliwości muszą obsługiwać oba `true` i `false` warunku.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-139">Combining `if` and `else` with Boolean conditions provides all the power you need to handle both a `true` and a `false` condition.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a9a7c-140">Wcięcie w obszarze `if` i `else` jest instrukcje dla człowieka czytników.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-140">The indentation under the `if` and `else` statements is for human readers.</span></span>
> <span data-ttu-id="a9a7c-141">W języku C# nie Traktuj wcięcia lub była białym znakiem za istotne.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-141">The C# language doesn't treat indentation or whitespace as significant.</span></span> <span data-ttu-id="a9a7c-142">Poniższa instrukcja `if` lub `else` — słowo kluczowe zostanie wykonana na podstawie warunku.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-142">The statement following the `if` or `else` keyword will be executed based on the condition.</span></span> <span data-ttu-id="a9a7c-143">Wszystkie przykłady w tym szybki start wykonaj popularną praktyką tworzenia wcięć oparte na przepływie sterowania instrukcji.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-143">All the samples in this quick start follow a common practice to indent lines based on the control flow of statements.</span></span>

<span data-ttu-id="a9a7c-144">Ponieważ wcięcia nie ma znaczenia, należy użyć `{` i `}` wskazująca, kiedy ma więcej niż jedną instrukcję jako część bloku, która wykonuje warunkowo.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-144">Because indentation is not significant, you need to use `{` and `}` to indicate when you want more than one statement to be part of the block that executes conditionally.</span></span> <span data-ttu-id="a9a7c-145">C# programistów zazwyczaj używają tych nawiasów klamrowych na wszystkich `if` i `else` klauzul.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-145">C# programmers typically use those braces on all `if` and `else` clauses.</span></span> <span data-ttu-id="a9a7c-146">Poniższy przykład jest taki sam jak ten, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-146">The following example is the same as the one you just created.</span></span> <span data-ttu-id="a9a7c-147">Modyfikowanie kodu powyżej, aby dopasować następujący kod:</span><span class="sxs-lookup"><span data-stu-id="a9a7c-147">Modify your code above to match the following code:</span></span>

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
> <span data-ttu-id="a9a7c-148">Za pomocą reszty to szybki start, wszystkie przykłady kodu zawiera nawiasy klamrowe, po zaakceptowane rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-148">Through the rest of this quick start, the code samples all include the braces, following accepted practices.</span></span>

<span data-ttu-id="a9a7c-149">Można przetestować bardziej skomplikowane warunki.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-149">You can test more complicated conditions.</span></span> <span data-ttu-id="a9a7c-150">Dodaj następujący kod w Twojej `Main` metody po kodzie napisanych wykonanej do tej pory:</span><span class="sxs-lookup"><span data-stu-id="a9a7c-150">Add the following code in your `Main` method after the code you've written so far:</span></span>

```csharp
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
```

<span data-ttu-id="a9a7c-151">`&&` Reprezentuje "i".</span><span class="sxs-lookup"><span data-stu-id="a9a7c-151">The `&&` represents "and".</span></span> <span data-ttu-id="a9a7c-152">Oznacza to, że oba warunki muszą być spełnione, można wykonać instrukcji w gałęzi wartość true.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-152">It means both conditions must be true to execute the statement in the true branch.</span></span>  <span data-ttu-id="a9a7c-153">Pokazują powyższe przykłady również może występować wiele instrukcji w każdym gałąź warunkowa, pod warunkiem, umieść je w `{` i `}`.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-153">These examples also show that you can have multiple statements in each conditional branch, provided you enclose them in `{` and `}`.</span></span>

<span data-ttu-id="a9a7c-154">Można również użyć `||` do reprezentowania "lub".</span><span class="sxs-lookup"><span data-stu-id="a9a7c-154">You can also use  `||` to represent "or".</span></span> <span data-ttu-id="a9a7c-155">Dodaj następujący kod, po czym napisanych wykonanej do tej pory:</span><span class="sxs-lookup"><span data-stu-id="a9a7c-155">Add the following code after what you've written so far:</span></span>

```csharp
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
```

<span data-ttu-id="a9a7c-156">Po zakończeniu pierwszym krokiem.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-156">You've finished the first step.</span></span> <span data-ttu-id="a9a7c-157">Przed rozpoczęciem następnej sekcji przejdziemy bieżącego kodu w oddzielnych metodach.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-157">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="a9a7c-158">Który ułatwia rozpoczęcie pracy z nowego przykład.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-158">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="a9a7c-159">Zmień nazwę Twojej `Main` metodę `ExploreIf` i zapisać nową `Main` — metoda, która wywołuje `ExploreIf`.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-159">Rename your `Main` method to `ExploreIf` and write a new `Main` method that calls `ExploreIf`.</span></span> <span data-ttu-id="a9a7c-160">Po zakończeniu, kod powinien wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="a9a7c-160">When you have finished, your code should look like this:</span></span>

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

<span data-ttu-id="a9a7c-161">Komentarz wywołanie `ExploreIf()`.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-161">Comment out the call to `ExploreIf()`.</span></span> <span data-ttu-id="a9a7c-162">Spowoduje to, że dane wyjściowe mniej elementów pracy w tej sekcji:</span><span class="sxs-lookup"><span data-stu-id="a9a7c-162">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//ExploreIf();
```

<span data-ttu-id="a9a7c-163">`//` Uruchamia **komentarz** w języku C#.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-163">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="a9a7c-164">Komentarze mogą zawierać dowolny tekst, który chcesz zachować w kodzie źródłowym, ale nie wykonują jako kod.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-164">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="a9a7c-165">Kompilator nie generuje żadnego kodu wykonywalnego z komentarzy.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-165">The compiler does not generate any executable code from comments.</span></span>

## <a name="use-loops-to-repeat-operations"></a><span data-ttu-id="a9a7c-166">Powtórz operacji za pomocą pętli</span><span class="sxs-lookup"><span data-stu-id="a9a7c-166">Use loops to repeat operations</span></span>

<span data-ttu-id="a9a7c-167">W tej sekcji użyjesz **pętle** powtórzeń instrukcje.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-167">In this section you use **loops** to repeat statements.</span></span> <span data-ttu-id="a9a7c-168">Spróbuj ten kod w Twojej `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="a9a7c-168">Try this code in your `Main` method:</span></span>

```csharp
int counter = 0;
while (counter < 10)
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
}
```

<span data-ttu-id="a9a7c-169">`while` Instrukcji sprawdza warunek i wykonuje instrukcji lub bloku instrukcji po `while`.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-169">The `while` statement checks a condition and executes the statement or statement block following the `while`.</span></span> <span data-ttu-id="a9a7c-170">Wciąż sprawdza warunek i wykonywania tych instrukcji, dopóki nie jest spełniony warunek.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-170">It repeatedly checks the condition and executing those statements until the condition is false.</span></span>

<span data-ttu-id="a9a7c-171">W tym przykładzie znajduje się jeden operator new.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-171">There's one other new operator in this example.</span></span> <span data-ttu-id="a9a7c-172">`++` Po `counter` zmienna jest **przyrostu** operatora.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-172">The `++` after the `counter` variable is the **increment** operator.</span></span> <span data-ttu-id="a9a7c-173">Dodaje do wartości 1 `counter` i zapisuje tę wartość w `counter` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-173">It adds 1 to the value of `counter` and stores that value in the `counter` variable.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a9a7c-174">Upewnij się, że `while` wykonać kod w pętli zmiany stanu na wartość false.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-174">Make sure that the `while` loop condition changes to false as you execute the code.</span></span> <span data-ttu-id="a9a7c-175">W przeciwnym razie utwórz **nieskończoną pętlę** gdzie program nigdy nie kończy.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-175">Otherwise, you create an **infinite loop** where your program never ends.</span></span> <span data-ttu-id="a9a7c-176">Który nie jest prezentowana w tym przykładzie, ponieważ trzeba wymusić programu, aby zrezygnować z używania **CTRL-C** lub w inny sposób.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-176">That is not demonstrated in this sample, because you have to force your program to quit using **CTRL-C** or other means.</span></span>

<span data-ttu-id="a9a7c-177">`while` Pętli sprawdza warunek przed wykonaniem poniższy kod `while`.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-177">The `while` loop tests the condition before executing the code following the `while`.</span></span> <span data-ttu-id="a9a7c-178">`do` ... `while` pętli wykonuje kod najpierw, a następnie sprawdza warunek.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-178">The `do` ... `while` loop executes the code first, and then checks the condition.</span></span> <span data-ttu-id="a9a7c-179">Czy podczas pętli przedstawiono w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="a9a7c-179">The do while loop is shown in the following code:</span></span>

```csharp
counter = 0;
do
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
} while (counter < 10);
```

<span data-ttu-id="a9a7c-180">To `do` pętli i wcześniej `while` pętli tworzenia tych samych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-180">This `do` loop and the earlier `while` loop produce the same output.</span></span>

## <a name="work-with-the-for-loop"></a><span data-ttu-id="a9a7c-181">Praca z pętli for</span><span class="sxs-lookup"><span data-stu-id="a9a7c-181">Work with the for loop</span></span>

<span data-ttu-id="a9a7c-182">**Dla** pętli jest powszechnie używany w języku C#.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-182">The **for** loop is commonly used in C#.</span></span> <span data-ttu-id="a9a7c-183">Spróbuj wykonać ten kod w wybranej metody Main():</span><span class="sxs-lookup"><span data-stu-id="a9a7c-183">Try this code in your Main() method:</span></span>

```csharp
for(int index = 0; index < 10; index++)
{
    Console.WriteLine($"Hello World! The index is {index}");
} 
```

<span data-ttu-id="a9a7c-184">Wykonuje ten sam pracę jako `while` pętli i `do` pętli, które zostały już użyte.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-184">This does the same work as the `while` loop and the `do` loop you've already used.</span></span> <span data-ttu-id="a9a7c-185">`for` Instrukcji ma trzy części, które kontrolują sposób działania.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-185">The `for` statement has three parts that control how it works.</span></span> 

<span data-ttu-id="a9a7c-186">Pierwsza część **dla inicjatora**: `for index = 0;` deklaruje, że `index` jest zmienna pętli i ustawia swojej wartości początkowej `0`.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-186">The first part is the **for initializer**: `for index = 0;` declares that `index` is the loop variable, and sets its initial value to `0`.</span></span>

<span data-ttu-id="a9a7c-187">Jest środka **warunku**: `index < 10` deklaruje tego `for` pętli kontynuuje wykonywanie tak długo, jak wartość licznika jest mniejsza niż 10.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-187">The middle part is the **for condition**: `index < 10` declares that this `for` loop continues to execute as long as the value of counter is less than 10.</span></span>

<span data-ttu-id="a9a7c-188">Ostatnim etapem jest **dla iterator**: `index++` określa sposób modyfikowania zmienna pętli for po wykonaniu następujących bloku `for` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-188">The final part is the **for iterator**: `index++` specifies how to modify the loop variable after executing the block following the `for` statement.</span></span> <span data-ttu-id="a9a7c-189">Określa ona, że w tym miejscu `index` powinny być zwiększana o 1 zawsze wykonuje bloku.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-189">Here, it specifies that `index` should be incremented by 1 each time the block executes.</span></span>

<span data-ttu-id="a9a7c-190">Wypróbuj te samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-190">Experiment with these yourself.</span></span> <span data-ttu-id="a9a7c-191">Spróbuj wykonać następujące czynniki:</span><span class="sxs-lookup"><span data-stu-id="a9a7c-191">Try each of the following:</span></span>

- <span data-ttu-id="a9a7c-192">Zmień inicjatora można uruchomić na inną wartość.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-192">Change the initializer to start at a different value.</span></span>
- <span data-ttu-id="a9a7c-193">Zmiany tego warunku można zatrzymać na inną wartość.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-193">Change the condition to stop at a different value.</span></span>

<span data-ttu-id="a9a7c-194">Gdy wszystko będzie gotowe, Przyjrzyjmy się do zapisu niektóre kod samodzielnie do użycia, zostały rozpoznane.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-194">When you're done, let's move on to write some code yourself to use what you've learned.</span></span>

## <a name="combine-branches-and-loops"></a><span data-ttu-id="a9a7c-195">Połączenia oddziałów i pętle</span><span class="sxs-lookup"><span data-stu-id="a9a7c-195">Combine branches and loops</span></span>

<span data-ttu-id="a9a7c-196">Teraz, w tym samouczku `if` instrukcji i konstrukcji pętli w języku C#, zobacz, czy można napisać kod C#, aby znaleźć sumę wszystkich liczb całkowitych od 1 do 20, które są podzielnych przez 3.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-196">Now that you've seen the `if` statement and the looping constructs in the C# language, see if you can write C# code to find the sum of all integers 1 through 20 that are divisible by 3.</span></span>  <span data-ttu-id="a9a7c-197">Poniżej przedstawiono kilka wskazówek:</span><span class="sxs-lookup"><span data-stu-id="a9a7c-197">Here are a few hints:</span></span>

- <span data-ttu-id="a9a7c-198">`%` Operatora daje reszta z operacji dzielenia.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-198">The `%` operator gives you the remainder of a division operation.</span></span>
- <span data-ttu-id="a9a7c-199">`if` Instrukcja zawiera warunek, aby zobaczyć, jeśli liczba powinna być częścią suma.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-199">The `if` statement gives you the condition to see if a number should be part of the sum.</span></span>
- <span data-ttu-id="a9a7c-200">`for` Pętli mogą pomóc w serie kroków należy powtórzyć dla wszystkich liczb od 1 do 20.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-200">The `for` loop can help you repeat a series of steps for all the numbers 1 through 20.</span></span>

<span data-ttu-id="a9a7c-201">Wypróbuj ją samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-201">Try it yourself.</span></span> <span data-ttu-id="a9a7c-202">Następnie sprawdź, jak Ty.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-202">Then check how you did.</span></span> <span data-ttu-id="a9a7c-203">Zobaczysz jednego możliwe odpowiedzi przez [wyświetlanie kompletny kod w serwisie GitHub](https://github.com/dotnet/docs/tree/master/samples/csharp/branches-quickstart/Program.cs#L46-L54).</span><span class="sxs-lookup"><span data-stu-id="a9a7c-203">You can see one possible answer by [viewing the completed code on GitHub](https://github.com/dotnet/docs/tree/master/samples/csharp/branches-quickstart/Program.cs#L46-L54).</span></span>

<span data-ttu-id="a9a7c-204">Zakończono szybki start "gałęzi i pętlę".</span><span class="sxs-lookup"><span data-stu-id="a9a7c-204">You've completed the "branches and loops" quick start.</span></span>

<span data-ttu-id="a9a7c-205">Można kontynuować [kolekcji i tablic](arrays-and-collections.md) szybki start w środowisku projektowania.</span><span class="sxs-lookup"><span data-stu-id="a9a7c-205">You can continue with the [Arrays and collections](arrays-and-collections.md) quick start in your own development environment.</span></span>

<span data-ttu-id="a9a7c-206">Użytkownik może dowiedzieć się więcej o tych pojęć w tych tematach:</span><span class="sxs-lookup"><span data-stu-id="a9a7c-206">You can learn more about these concepts in these topics:</span></span>

<span data-ttu-id="a9a7c-207">[Jeśli i else — instrukcja](../language-reference/keywords/if-else.md) </span><span class="sxs-lookup"><span data-stu-id="a9a7c-207">[If and else statement](../language-reference/keywords/if-else.md) </span></span>  
<span data-ttu-id="a9a7c-208">[While — instrukcja](../language-reference/keywords/while.md) </span><span class="sxs-lookup"><span data-stu-id="a9a7c-208">[While statement](../language-reference/keywords/while.md) </span></span>  
<span data-ttu-id="a9a7c-209">[— Instrukcja](../language-reference/keywords/do.md) </span><span class="sxs-lookup"><span data-stu-id="a9a7c-209">[Do statement](../language-reference/keywords/do.md) </span></span>  
[<span data-ttu-id="a9a7c-210">For — instrukcja</span><span class="sxs-lookup"><span data-stu-id="a9a7c-210">For statement</span></span>](../language-reference/keywords/for.md)   

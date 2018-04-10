---
title: Samouczek gałęzie i pętli - C# lokalnego poradniki Szybki Start
description: W tym Szybki Start dotyczące gałęzi i pętle pisania kodu C#, aby eksplorować składni języka, obsługującego warunkowych gałęzi i pętli do wykonywania instrukcji wielokrotnie.
author: billwagner
ms.author: wiwagn
ms.date: 10/31/2017
ms.topic: get-started-article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 9a52bafd1536783c59e9e1b92f3ad16b5000ca3b
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="branches-and-loops"></a><span data-ttu-id="9e9a2-103">Gałęzie i pętli</span><span class="sxs-lookup"><span data-stu-id="9e9a2-103">Branches and loops</span></span>

<span data-ttu-id="9e9a2-104">Ta opcja szybkiego startu jest przedstawienie sposobu pisania kodu, który sprawdza zmienne i zmieniona ścieżka wykonywania na podstawie tych zmiennych.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-104">This quickstart teaches you how to write code that examines variables and changes the execution path based on those variables.</span></span> <span data-ttu-id="9e9a2-105">Pisanie kodu C# i wyświetlić wyniki kompilowania i uruchamiania go.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-105">You write C# code and see the results of compiling and running it.</span></span> <span data-ttu-id="9e9a2-106">Procedury szybkiego startu zawiera szereg lekcje, które eksplorować rozgałęzianie i zapętlenia konstrukcje w języku C#.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-106">The quickstart contains a series of lessons that explore branching and looping constructs in C#.</span></span> <span data-ttu-id="9e9a2-107">Że wnioski uczy również podstaw programu w języku C#.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-107">These lessons teach you the fundamentals of the C# language.</span></span>

<span data-ttu-id="9e9a2-108">Ta opcja szybkiego startu oczekuje posiadania maszynie, która służy do tworzenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-108">This quickstart expects you to have a machine you can use for development.</span></span> <span data-ttu-id="9e9a2-109">Temat .NET [wprowadzenie w ciągu 10 minut](https://www.microsoft.com/net/core) zawiera instrukcje dotyczące konfigurowania środowiska deweloperskiego lokalnego Mac, komputera lub Linux.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-109">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="9e9a2-110">Jest to szybki przegląd poleceń będzie używany w [wprowadzenie do lokalnego poradniki Szybki Start](local-environment.md) wraz z łączami, aby uzyskać więcej szczegółów.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-110">A quick overview of the commands you'll use is in the [introduction to the local quickstarts](local-environment.md) with links to more details.</span></span>

## <a name="make-decisions-using-the-if-statement"></a><span data-ttu-id="9e9a2-111">Podejmowanie decyzji przy użyciu `if` — instrukcja</span><span class="sxs-lookup"><span data-stu-id="9e9a2-111">Make decisions using the `if` statement</span></span>

<span data-ttu-id="9e9a2-112">Utwórz katalog o nazwie **szybkiego startu gałęzie**.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-112">Create a directory named **branches-quickstart**.</span></span> <span data-ttu-id="9e9a2-113">Upewnij, że bieżący katalog i uruchom `dotnet new console -n BranchesAndLoops -o .`.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-113">Make that the current directory and run `dotnet new console -n BranchesAndLoops -o .`.</span></span> <span data-ttu-id="9e9a2-114">To polecenie tworzy nową aplikację konsolową .NET Core w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-114">This command creates a new .NET Core console application in the current directory.</span></span>

<span data-ttu-id="9e9a2-115">Otwórz **Program.cs** ulubionego edytora i Zastąp linię `Console.Writeline("Hello World!");` następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="9e9a2-115">Open **Program.cs** in your favorite editor, and replace the line `Console.Writeline("Hello World!");` with the following code:</span></span>

```csharp
int a = 5;
int b = 6;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10.");
```

<span data-ttu-id="9e9a2-116">Spróbuj ten kod, wpisując `dotnet run` w okna konsoli.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-116">Try this code by typing `dotnet run` in the your console window.</span></span> <span data-ttu-id="9e9a2-117">Powinien zostać wyświetlony komunikat "odpowiedź jest większa niż 10".</span><span class="sxs-lookup"><span data-stu-id="9e9a2-117">You should see the message "The answer is greater than 10."</span></span> <span data-ttu-id="9e9a2-118">podane do konsoli.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-118">printed to your console.</span></span>

<span data-ttu-id="9e9a2-119">Modyfikowanie deklaracja `b` , tak aby suma była mniejsza niż 10:</span><span class="sxs-lookup"><span data-stu-id="9e9a2-119">Modify the declaration of `b` so that the sum is less than 10:</span></span> 

```csharp
int b = 3;
```

<span data-ttu-id="9e9a2-120">Typ `dotnet run` ponownie.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-120">Type `dotnet run` again.</span></span> <span data-ttu-id="9e9a2-121">Ponieważ odpowiedź jest mniejsza niż 10, nic nie jest wydrukowane.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-121">Because the answer is less than 10, nothing is printed.</span></span> <span data-ttu-id="9e9a2-122">**Warunku** jesteś testowania ma wartość false.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-122">The **condition** you're testing is false.</span></span> <span data-ttu-id="9e9a2-123">Nie masz żadnych kod do wykonania, ponieważ został zapisany tylko jedną z możliwych gałęzi dla `if` instrukcji: gałąź prawdy.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-123">You don't have any code to execute because you've only written one of the possible branches for an `if` statement: the true branch.</span></span>

> [!TIP]
> <span data-ttu-id="9e9a2-124">Ci poznać platformę C# (lub dowolnego języka programowania), należy podjąć błędów podczas pisania kodu.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-124">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="9e9a2-125">Kompilator znajdzie i raportów o błędach.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-125">The compiler will find and report the errors.</span></span> <span data-ttu-id="9e9a2-126">Należy dokładnie przejrzeć dane wyjściowe błędów i kod, który wygenerował błąd.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-126">Look closely at the error output and the code that generated the error.</span></span> <span data-ttu-id="9e9a2-127">Błąd compler zwykle może pomóc w znalezieniu problem.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-127">The compler error can usually help you find the problem.</span></span>

<span data-ttu-id="9e9a2-128">W tym przykładzie pierwsze pokazano możliwości `if` i typów logicznych.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-128">This first sample shows the power of `if` and Boolean types.</span></span> <span data-ttu-id="9e9a2-129">A *logiczna* jest zmienna, która może mieć jedną z dwóch wartości: `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-129">A *Boolean* is a variable that can have one of two values: `true` or `false`.</span></span> <span data-ttu-id="9e9a2-130">C# definiuje specjalny typ `bool` dla zmienne typu Boolean.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-130">C# defines a special type, `bool` for Boolean variables.</span></span> <span data-ttu-id="9e9a2-131">`if` Instrukcji sprawdza wartość `bool`.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-131">The `if` statement checks the value of a `bool`.</span></span> <span data-ttu-id="9e9a2-132">Jeśli wartość jest `true`, instrukcji następującej `if` wykonuje.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-132">When the value is `true`, the statement following the `if` executes.</span></span> <span data-ttu-id="9e9a2-133">W przeciwnym razie zostanie pominięte.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-133">Otherwise, it is skipped.</span></span>

<span data-ttu-id="9e9a2-134">Ten proces sprawdzania warunków i wykonywanie instrukcji na podstawie tych warunków jest bardzo zaawansowaną.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-134">This process of checking conditions and executing statements based on those conditions is very powerful.</span></span>

## <a name="make-if-and-else-work-together"></a><span data-ttu-id="9e9a2-135">Upewnij się, jeśli i else współpracują ze sobą</span><span class="sxs-lookup"><span data-stu-id="9e9a2-135">Make if and else work together</span></span>

<span data-ttu-id="9e9a2-136">Aby wykonać inny kod w gałęzi true i false, należy utworzyć `else` gałęzi, która wykonuje, gdy warunek ma wartość false.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-136">To execute different code in both the true and false branches, you create an `else` branch that executes when the condition is false.</span></span> <span data-ttu-id="9e9a2-137">Skorzystaj z tej.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-137">Try this.</span></span> <span data-ttu-id="9e9a2-138">Dodaj ostatnie dwa wiersze w poniższym kodzie do Twojej `Main` — metoda (powinna już być pierwsze cztery):</span><span class="sxs-lookup"><span data-stu-id="9e9a2-138">Add the last two lines in the code below to your `Main` method (you should already have the first four):</span></span>

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10");
else
    Console.WriteLine("The answer is not greater than 10");
```

<span data-ttu-id="9e9a2-139">Poniższa instrukcja `else` — słowo kluczowe jest wykonywana tylko wtedy, gdy warunek testowana jest `false`.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-139">The statement following the `else` keyword executes only when the condition being tested is `false`.</span></span> <span data-ttu-id="9e9a2-140">Łączenie `if` i `else` z logiczną warunki zawiera wszystkie możliwości muszą obsługiwać oba `true` i `false` warunku.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-140">Combining `if` and `else` with Boolean conditions provides all the power you need to handle both a `true` and a `false` condition.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9e9a2-141">Wcięcie w obszarze `if` i `else` jest instrukcje dla człowieka czytników.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-141">The indentation under the `if` and `else` statements is for human readers.</span></span>
> <span data-ttu-id="9e9a2-142">W języku C# nie Traktuj wcięcia lub biały znak za istotne.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-142">The C# language doesn't treat indentation or white space as significant.</span></span> <span data-ttu-id="9e9a2-143">Poniższa instrukcja `if` lub `else` — słowo kluczowe zostanie wykonana na podstawie warunku.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-143">The statement following the `if` or `else` keyword will be executed based on the condition.</span></span> <span data-ttu-id="9e9a2-144">Wszystkie przykłady w tym szybkiego startu wykonaj popularną praktyką tworzenia wcięć oparte na przepływie sterowania instrukcji.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-144">All the samples in this quickstart follow a common practice to indent lines based on the control flow of statements.</span></span>

<span data-ttu-id="9e9a2-145">Ponieważ wcięcia nie ma znaczenia, należy użyć `{` i `}` wskazująca, kiedy ma więcej niż jedną instrukcję jako część bloku, która wykonuje warunkowo.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-145">Because indentation is not significant, you need to use `{` and `}` to indicate when you want more than one statement to be part of the block that executes conditionally.</span></span> <span data-ttu-id="9e9a2-146">C# programistów zazwyczaj używają tych nawiasów klamrowych na wszystkich `if` i `else` klauzul.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-146">C# programmers typically use those braces on all `if` and `else` clauses.</span></span> <span data-ttu-id="9e9a2-147">Poniższy przykład jest taki sam jak ten, który został utworzony.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-147">The following example is the same as the one you just created.</span></span> <span data-ttu-id="9e9a2-148">Modyfikowanie kodu powyżej, aby dopasować następujący kod:</span><span class="sxs-lookup"><span data-stu-id="9e9a2-148">Modify your code above to match the following code:</span></span>

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
> <span data-ttu-id="9e9a2-149">Za pomocą pozostałej części tego przewodnika Szybki Start, wszystkie przykłady kodu zawiera nawiasy klamrowe, po zaakceptowane rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-149">Through the rest of this quickstart, the code samples all include the braces, following accepted practices.</span></span>

<span data-ttu-id="9e9a2-150">Można przetestować bardziej skomplikowane warunki.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-150">You can test more complicated conditions.</span></span> <span data-ttu-id="9e9a2-151">Dodaj następujący kod w Twojej `Main` metody po kodzie napisanych wykonanej do tej pory:</span><span class="sxs-lookup"><span data-stu-id="9e9a2-151">Add the following code in your `Main` method after the code you've written so far:</span></span>

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

<span data-ttu-id="9e9a2-152">`&&` Reprezentuje "i".</span><span class="sxs-lookup"><span data-stu-id="9e9a2-152">The `&&` represents "and".</span></span> <span data-ttu-id="9e9a2-153">Oznacza to, że oba warunki muszą być spełnione, można wykonać instrukcji w gałęzi wartość true.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-153">It means both conditions must be true to execute the statement in the true branch.</span></span>  <span data-ttu-id="9e9a2-154">Pokazują powyższe przykłady również może występować wiele instrukcji w każdym gałąź warunkowa, pod warunkiem, umieść je w `{` i `}`.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-154">These examples also show that you can have multiple statements in each conditional branch, provided you enclose them in `{` and `}`.</span></span>

<span data-ttu-id="9e9a2-155">Można również użyć `||` do reprezentowania "lub".</span><span class="sxs-lookup"><span data-stu-id="9e9a2-155">You can also use  `||` to represent "or".</span></span> <span data-ttu-id="9e9a2-156">Dodaj następujący kod, po czym napisanych wykonanej do tej pory:</span><span class="sxs-lookup"><span data-stu-id="9e9a2-156">Add the following code after what you've written so far:</span></span>

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

<span data-ttu-id="9e9a2-157">Po zakończeniu pierwszym krokiem.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-157">You've finished the first step.</span></span> <span data-ttu-id="9e9a2-158">Przed rozpoczęciem następnej sekcji przejdziemy bieżącego kodu w oddzielnych metodach.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-158">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="9e9a2-159">Który ułatwia rozpoczęcie pracy z nowego przykład.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-159">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="9e9a2-160">Zmień nazwę Twojej `Main` metodę `ExploreIf` i zapisać nową `Main` — metoda, która wywołuje `ExploreIf`.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-160">Rename your `Main` method to `ExploreIf` and write a new `Main` method that calls `ExploreIf`.</span></span> <span data-ttu-id="9e9a2-161">Po zakończeniu, kod powinien wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="9e9a2-161">When you have finished, your code should look like this:</span></span>

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

<span data-ttu-id="9e9a2-162">Komentarz wywołanie `ExploreIf()`.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-162">Comment out the call to `ExploreIf()`.</span></span> <span data-ttu-id="9e9a2-163">Spowoduje to, że dane wyjściowe mniej elementów pracy w tej sekcji:</span><span class="sxs-lookup"><span data-stu-id="9e9a2-163">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//ExploreIf();
```

<span data-ttu-id="9e9a2-164">`//` Uruchamia **komentarz** w języku C#.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-164">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="9e9a2-165">Komentarze mogą zawierać dowolny tekst, który chcesz zachować w kodzie źródłowym, ale nie wykonują jako kod.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-165">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="9e9a2-166">Kompilator nie generuje żadnego kodu wykonywalnego z komentarzy.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-166">The compiler does not generate any executable code from comments.</span></span>

## <a name="use-loops-to-repeat-operations"></a><span data-ttu-id="9e9a2-167">Powtórz operacji za pomocą pętli</span><span class="sxs-lookup"><span data-stu-id="9e9a2-167">Use loops to repeat operations</span></span>

<span data-ttu-id="9e9a2-168">W tej sekcji użyjesz **pętle** powtórzeń instrukcje.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-168">In this section you use **loops** to repeat statements.</span></span> <span data-ttu-id="9e9a2-169">Spróbuj ten kod w Twojej `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="9e9a2-169">Try this code in your `Main` method:</span></span>

```csharp
int counter = 0;
while (counter < 10)
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
}
```

<span data-ttu-id="9e9a2-170">`while` Instrukcji sprawdza warunek i wykonuje instrukcji lub bloku instrukcji po `while`.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-170">The `while` statement checks a condition and executes the statement or statement block following the `while`.</span></span> <span data-ttu-id="9e9a2-171">Wciąż sprawdza warunek i wykonywania tych instrukcji, dopóki nie jest spełniony warunek.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-171">It repeatedly checks the condition and executing those statements until the condition is false.</span></span>

<span data-ttu-id="9e9a2-172">W tym przykładzie znajduje się jeden operator new.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-172">There's one other new operator in this example.</span></span> <span data-ttu-id="9e9a2-173">`++` Po `counter` zmienna jest **przyrostu** operatora.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-173">The `++` after the `counter` variable is the **increment** operator.</span></span> <span data-ttu-id="9e9a2-174">Dodaje do wartości 1 `counter` i zapisuje tę wartość w `counter` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-174">It adds 1 to the value of `counter` and stores that value in the `counter` variable.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9e9a2-175">Upewnij się, że `while` wykonać kod w pętli zmiany stanu na wartość false.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-175">Make sure that the `while` loop condition changes to false as you execute the code.</span></span> <span data-ttu-id="9e9a2-176">W przeciwnym razie utwórz **nieskończoną pętlę** gdzie program nigdy nie kończy.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-176">Otherwise, you create an **infinite loop** where your program never ends.</span></span> <span data-ttu-id="9e9a2-177">Który nie jest prezentowana w tym przykładzie, ponieważ trzeba wymusić programu, aby zrezygnować z używania **CTRL-C** lub w inny sposób.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-177">That is not demonstrated in this sample, because you have to force your program to quit using **CTRL-C** or other means.</span></span>

<span data-ttu-id="9e9a2-178">`while` Pętli sprawdza warunek przed wykonaniem poniższy kod `while`.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-178">The `while` loop tests the condition before executing the code following the `while`.</span></span> <span data-ttu-id="9e9a2-179">`do` ... `while` pętli wykonuje kod najpierw, a następnie sprawdza warunek.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-179">The `do` ... `while` loop executes the code first, and then checks the condition.</span></span> <span data-ttu-id="9e9a2-180">Czy podczas pętli przedstawiono w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="9e9a2-180">The do while loop is shown in the following code:</span></span>

```csharp
counter = 0;
do
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
} while (counter < 10);
```

<span data-ttu-id="9e9a2-181">To `do` pętli i wcześniej `while` pętli tworzenia tych samych danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-181">This `do` loop and the earlier `while` loop produce the same output.</span></span>

## <a name="work-with-the-for-loop"></a><span data-ttu-id="9e9a2-182">Praca z pętli for</span><span class="sxs-lookup"><span data-stu-id="9e9a2-182">Work with the for loop</span></span>

<span data-ttu-id="9e9a2-183">**Dla** pętli jest powszechnie używany w języku C#.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-183">The **for** loop is commonly used in C#.</span></span> <span data-ttu-id="9e9a2-184">Spróbuj wykonać ten kod w wybranej metody Main():</span><span class="sxs-lookup"><span data-stu-id="9e9a2-184">Try this code in your Main() method:</span></span>

```csharp
for(int index = 0; index < 10; index++)
{
    Console.WriteLine($"Hello World! The index is {index}");
} 
```

<span data-ttu-id="9e9a2-185">Wykonuje ten sam pracę jako `while` pętli i `do` pętli, które zostały już użyte.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-185">This does the same work as the `while` loop and the `do` loop you've already used.</span></span> <span data-ttu-id="9e9a2-186">`for` Instrukcji ma trzy części, które kontrolują sposób działania.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-186">The `for` statement has three parts that control how it works.</span></span>

<span data-ttu-id="9e9a2-187">Pierwsza część **dla inicjatora**: `for index = 0;` deklaruje, że `index` jest zmienna pętli i ustawia swojej wartości początkowej `0`.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-187">The first part is the **for initializer**: `for index = 0;` declares that `index` is the loop variable, and sets its initial value to `0`.</span></span>

<span data-ttu-id="9e9a2-188">Jest środka **warunku**: `index < 10` deklaruje tego `for` pętli kontynuuje wykonywanie tak długo, jak wartość licznika jest mniejsza niż 10.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-188">The middle part is the **for condition**: `index < 10` declares that this `for` loop continues to execute as long as the value of counter is less than 10.</span></span>

<span data-ttu-id="9e9a2-189">Ostatnim etapem jest **dla iterator**: `index++` określa sposób modyfikowania zmienna pętli for po wykonaniu następujących bloku `for` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-189">The final part is the **for iterator**: `index++` specifies how to modify the loop variable after executing the block following the `for` statement.</span></span> <span data-ttu-id="9e9a2-190">Określa ona, że w tym miejscu `index` powinny być zwiększana o 1 zawsze wykonuje bloku.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-190">Here, it specifies that `index` should be incremented by 1 each time the block executes.</span></span>

<span data-ttu-id="9e9a2-191">Wypróbuj te samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-191">Experiment with these yourself.</span></span> <span data-ttu-id="9e9a2-192">Spróbuj wykonać następujące czynniki:</span><span class="sxs-lookup"><span data-stu-id="9e9a2-192">Try each of the following:</span></span>

- <span data-ttu-id="9e9a2-193">Zmień inicjatora można uruchomić na inną wartość.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-193">Change the initializer to start at a different value.</span></span>
- <span data-ttu-id="9e9a2-194">Zmiany tego warunku można zatrzymać na inną wartość.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-194">Change the condition to stop at a different value.</span></span>

<span data-ttu-id="9e9a2-195">Gdy wszystko będzie gotowe, Przyjrzyjmy się do zapisu niektóre kod samodzielnie do użycia, zostały rozpoznane.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-195">When you're done, let's move on to write some code yourself to use what you've learned.</span></span>

## <a name="combine-branches-and-loops"></a><span data-ttu-id="9e9a2-196">Połączenia oddziałów i pętle</span><span class="sxs-lookup"><span data-stu-id="9e9a2-196">Combine branches and loops</span></span>

<span data-ttu-id="9e9a2-197">Teraz, w tym samouczku `if` instrukcji i konstrukcji pętli w języku C#, zobacz, czy można napisać kod C#, aby znaleźć sumę wszystkich liczb całkowitych od 1 do 20, które są podzielnych przez 3.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-197">Now that you've seen the `if` statement and the looping constructs in the C# language, see if you can write C# code to find the sum of all integers 1 through 20 that are divisible by 3.</span></span>  <span data-ttu-id="9e9a2-198">Poniżej przedstawiono kilka wskazówek:</span><span class="sxs-lookup"><span data-stu-id="9e9a2-198">Here are a few hints:</span></span>

- <span data-ttu-id="9e9a2-199">`%` Operatora daje reszta z operacji dzielenia.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-199">The `%` operator gives you the remainder of a division operation.</span></span>
- <span data-ttu-id="9e9a2-200">`if` Instrukcja zawiera warunek, aby zobaczyć, jeśli liczba powinna być częścią suma.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-200">The `if` statement gives you the condition to see if a number should be part of the sum.</span></span>
- <span data-ttu-id="9e9a2-201">`for` Pętli mogą pomóc w serie kroków należy powtórzyć dla wszystkich liczb od 1 do 20.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-201">The `for` loop can help you repeat a series of steps for all the numbers 1 through 20.</span></span>

<span data-ttu-id="9e9a2-202">Wypróbuj ją samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-202">Try it yourself.</span></span> <span data-ttu-id="9e9a2-203">Następnie sprawdź, jak Ty.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-203">Then check how you did.</span></span> <span data-ttu-id="9e9a2-204">Należy pobrać 63 dla odpowiedzi.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-204">You should get 63 for an answer.</span></span> <span data-ttu-id="9e9a2-205">Zobaczysz jednego możliwe odpowiedzi przez [wyświetlanie kompletny kod w serwisie GitHub](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54).</span><span class="sxs-lookup"><span data-stu-id="9e9a2-205">You can see one possible answer by [viewing the completed code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54).</span></span>

<span data-ttu-id="9e9a2-206">Zakończono Szybki Start "gałęzie i pętle".</span><span class="sxs-lookup"><span data-stu-id="9e9a2-206">You've completed the "branches and loops" quickstart.</span></span>

<span data-ttu-id="9e9a2-207">Można kontynuować [ciągi interpolowane](interpolated-strings-local.md) szybkiego startu w środowisku projektowania.</span><span class="sxs-lookup"><span data-stu-id="9e9a2-207">You can continue with the [Interpolated strings](interpolated-strings-local.md) quickstart in your own development environment.</span></span>

<span data-ttu-id="9e9a2-208">Użytkownik może dowiedzieć się więcej o tych pojęć w tych tematach:</span><span class="sxs-lookup"><span data-stu-id="9e9a2-208">You can learn more about these concepts in these topics:</span></span>

[<span data-ttu-id="9e9a2-209">Jeśli i else — instrukcja</span><span class="sxs-lookup"><span data-stu-id="9e9a2-209">If and else statement</span></span>](../language-reference/keywords/if-else.md)  
[<span data-ttu-id="9e9a2-210">While — instrukcja</span><span class="sxs-lookup"><span data-stu-id="9e9a2-210">While statement</span></span>](../language-reference/keywords/while.md)  
[<span data-ttu-id="9e9a2-211">— Instrukcja</span><span class="sxs-lookup"><span data-stu-id="9e9a2-211">Do statement</span></span>](../language-reference/keywords/do.md)  
[<span data-ttu-id="9e9a2-212">For — instrukcja</span><span class="sxs-lookup"><span data-stu-id="9e9a2-212">For statement</span></span>](../language-reference/keywords/for.md)  

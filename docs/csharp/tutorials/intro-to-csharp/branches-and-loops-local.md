---
title: Gałęzie i pętle — wprowadzenie do C# samouczek
description: W tym samouczku omawiającym gałęzie i pętle zapisu C# kodu, aby poznać składnię języka, obsługującego warunkowych gałęzi i pętli, aby wykonać instrukcje wielokrotnie.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: 0997c0b4a8f450c0e5eadc9616457a1ab84e7d96
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50186152"
---
# <a name="learn-conditional-logic-with-branch-and-loop-statements"></a><span data-ttu-id="339b3-103">Dowiedz się, logikę warunkową instrukcji gałęzi i pętli</span><span class="sxs-lookup"><span data-stu-id="339b3-103">Learn conditional logic with branch and loop statements</span></span>

<span data-ttu-id="339b3-104">Ten samouczek omawia sposób pisanie kodu badającego zmienne i wybierającego ścieżkę wykonania na podstawie tych zmiennych.</span><span class="sxs-lookup"><span data-stu-id="339b3-104">This tutorial teaches you how to write code that examines variables and changes the execution path based on those variables.</span></span> <span data-ttu-id="339b3-105">Możesz pisać kod w języku C# i zobaczyć wyniki kompilowania i uruchamiania ich.</span><span class="sxs-lookup"><span data-stu-id="339b3-105">You write C# code and see the results of compiling and running it.</span></span> <span data-ttu-id="339b3-106">Samouczek zawiera serię lekcji przedstawiających konstrukcje w gałęzi i pętli C#.</span><span class="sxs-lookup"><span data-stu-id="339b3-106">The tutorial contains a series of lessons that explore branching and looping constructs in C#.</span></span> <span data-ttu-id="339b3-107">Te lekcje umożliwiają poznanie podstaw języka C#.</span><span class="sxs-lookup"><span data-stu-id="339b3-107">These lessons teach you the fundamentals of the C# language.</span></span>

<span data-ttu-id="339b3-108">W tym samouczku oczekuje, że będziesz mieć maszyny, których można użyć do tworzenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="339b3-108">This tutorial expects you to have a machine you can use for development.</span></span> <span data-ttu-id="339b3-109">Temat .NET [rozpocząć pracę w ciągu 10 minut](https://www.microsoft.com/net/core) zawiera instrukcje dotyczące konfigurowania swojego lokalnego środowiska deweloperskiego na komputerze Mac, PC lub Linux.</span><span class="sxs-lookup"><span data-stu-id="339b3-109">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="339b3-110">Krótkie omówienie poleceń użyjesz znajduje się w [zapoznanie się z narzędziami programistycznymi](local-environment.md) wraz z łączami, aby uzyskać więcej szczegółów.</span><span class="sxs-lookup"><span data-stu-id="339b3-110">A quick overview of the commands you'll use is in the [Become familiar with the development tools](local-environment.md) with links to more details.</span></span>

## <a name="make-decisions-using-the-if-statement"></a><span data-ttu-id="339b3-111">Podejmowanie decyzji za pomocą `if` — instrukcja</span><span class="sxs-lookup"><span data-stu-id="339b3-111">Make decisions using the `if` statement</span></span>

<span data-ttu-id="339b3-112">Utwórz katalog o nazwie **samouczek dotyczący gałęzi**.</span><span class="sxs-lookup"><span data-stu-id="339b3-112">Create a directory named **branches-tutorial**.</span></span> <span data-ttu-id="339b3-113">Upewnij, że bieżącego katalogu i uruchom `dotnet new console -n BranchesAndLoops -o .`.</span><span class="sxs-lookup"><span data-stu-id="339b3-113">Make that the current directory and run `dotnet new console -n BranchesAndLoops -o .`.</span></span> <span data-ttu-id="339b3-114">To polecenie tworzy nową aplikację konsoli .NET Core w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="339b3-114">This command creates a new .NET Core console application in the current directory.</span></span>

<span data-ttu-id="339b3-115">Otwórz **Program.cs** w ulubionym edytorze i Zastąp wiersz `Console.Writeline("Hello World!");` następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="339b3-115">Open **Program.cs** in your favorite editor, and replace the line `Console.Writeline("Hello World!");` with the following code:</span></span>

```csharp
int a = 5;
int b = 6;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10.");
```

<span data-ttu-id="339b3-116">Wypróbuj ten kod, wpisując `dotnet run` w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="339b3-116">Try this code by typing `dotnet run` in your console window.</span></span> <span data-ttu-id="339b3-117">Powinien zostać wyświetlony komunikat "odpowiedź jest większa niż 10".</span><span class="sxs-lookup"><span data-stu-id="339b3-117">You should see the message "The answer is greater than 10."</span></span> <span data-ttu-id="339b3-118">drukowane do konsoli.</span><span class="sxs-lookup"><span data-stu-id="339b3-118">printed to your console.</span></span>

<span data-ttu-id="339b3-119">Zmodyfikuj deklarację zmiennej `b` , tak aby suma była mniejsza niż 10:</span><span class="sxs-lookup"><span data-stu-id="339b3-119">Modify the declaration of `b` so that the sum is less than 10:</span></span> 

```csharp
int b = 3;
```

<span data-ttu-id="339b3-120">Typ `dotnet run` ponownie.</span><span class="sxs-lookup"><span data-stu-id="339b3-120">Type `dotnet run` again.</span></span> <span data-ttu-id="339b3-121">Ponieważ odpowiedź jest mniejsza niż 10, nic nie zostanie wyświetlone.</span><span class="sxs-lookup"><span data-stu-id="339b3-121">Because the answer is less than 10, nothing is printed.</span></span> <span data-ttu-id="339b3-122">**Warunek** jesteś testowania ma wartość false.</span><span class="sxs-lookup"><span data-stu-id="339b3-122">The **condition** you're testing is false.</span></span> <span data-ttu-id="339b3-123">Nie masz żadnego kodu do wykonania, ponieważ zostały zapisane wyłącznie jedną z możliwych gałęzi dla `if` instrukcji: gałęzi dla wartości true.</span><span class="sxs-lookup"><span data-stu-id="339b3-123">You don't have any code to execute because you've only written one of the possible branches for an `if` statement: the true branch.</span></span>

> [!TIP]
> <span data-ttu-id="339b3-124">Gdy eksplorujesz C# (lub dowolnego języka programowania), będziesz robić błędy podczas pisania kodu.</span><span class="sxs-lookup"><span data-stu-id="339b3-124">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="339b3-125">Kompilator znajdzie i raportowania błędów.</span><span class="sxs-lookup"><span data-stu-id="339b3-125">The compiler will find and report the errors.</span></span> <span data-ttu-id="339b3-126">Przyjrzyj się blisko dane wyjściowe błędu i kod, który wygenerował błąd.</span><span class="sxs-lookup"><span data-stu-id="339b3-126">Look closely at the error output and the code that generated the error.</span></span> <span data-ttu-id="339b3-127">Błąd kompilatora zazwyczaj mogą pomóc w znalezieniu problem.</span><span class="sxs-lookup"><span data-stu-id="339b3-127">The compiler error can usually help you find the problem.</span></span>

<span data-ttu-id="339b3-128">Pierwszy przykład przedstawia możliwości `if` i typów logicznych.</span><span class="sxs-lookup"><span data-stu-id="339b3-128">This first sample shows the power of `if` and Boolean types.</span></span> <span data-ttu-id="339b3-129">A *logiczna* jest zmienną, która może mieć jedną z dwóch wartości: `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="339b3-129">A *Boolean* is a variable that can have one of two values: `true` or `false`.</span></span> <span data-ttu-id="339b3-130">C#definiuje specjalny typ `bool` dla zmiennych logicznych.</span><span class="sxs-lookup"><span data-stu-id="339b3-130">C# defines a special type, `bool` for Boolean variables.</span></span> <span data-ttu-id="339b3-131">`if` Instrukcji sprawdza wartość `bool`.</span><span class="sxs-lookup"><span data-stu-id="339b3-131">The `if` statement checks the value of a `bool`.</span></span> <span data-ttu-id="339b3-132">Jeśli wartość to `true`, instrukcji następującej `if` wykonuje.</span><span class="sxs-lookup"><span data-stu-id="339b3-132">When the value is `true`, the statement following the `if` executes.</span></span> <span data-ttu-id="339b3-133">W przeciwnym razie zostanie ona pominięta.</span><span class="sxs-lookup"><span data-stu-id="339b3-133">Otherwise, it is skipped.</span></span>

<span data-ttu-id="339b3-134">Ten proces sprawdzania warunków i wykonywania instrukcji na podstawie tych warunków są ogromne.</span><span class="sxs-lookup"><span data-stu-id="339b3-134">This process of checking conditions and executing statements based on those conditions is very powerful.</span></span>

## <a name="make-if-and-else-work-together"></a><span data-ttu-id="339b3-135">Upewnij się, jeśli i inne współpracują ze sobą</span><span class="sxs-lookup"><span data-stu-id="339b3-135">Make if and else work together</span></span>

<span data-ttu-id="339b3-136">Aby wykonać różny kod w gałęzie true i false, należy utworzyć `else` gałęzi, która wykonuje, gdy warunek jest fałszywy.</span><span class="sxs-lookup"><span data-stu-id="339b3-136">To execute different code in both the true and false branches, you create an `else` branch that executes when the condition is false.</span></span> <span data-ttu-id="339b3-137">Wypróbuj to.</span><span class="sxs-lookup"><span data-stu-id="339b3-137">Try this.</span></span> <span data-ttu-id="339b3-138">Dodaj ostatnie dwa wiersze w poniższym kodzie, aby Twoje `Main` — metoda (konto powinno mieć już pierwsze cztery):</span><span class="sxs-lookup"><span data-stu-id="339b3-138">Add the last two lines in the code below to your `Main` method (you should already have the first four):</span></span>

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10");
else
    Console.WriteLine("The answer is not greater than 10");
```

<span data-ttu-id="339b3-139">Instrukcja po słowie `else` — słowo kluczowe jest wykonywany tylko wtedy, gdy testowany warunek jest `false`.</span><span class="sxs-lookup"><span data-stu-id="339b3-139">The statement following the `else` keyword executes only when the condition being tested is `false`.</span></span> <span data-ttu-id="339b3-140">Łącząc `if` i `else` atrybut typu wartość logiczna warunki zapewnia wszystkich możliwości muszą obsługiwać oba modele `true` i `false` warunku.</span><span class="sxs-lookup"><span data-stu-id="339b3-140">Combining `if` and `else` with Boolean conditions provides all the power you need to handle both a `true` and a `false` condition.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="339b3-141">Wcięcia pod `if` i `else` instrukcji jest czytelności.</span><span class="sxs-lookup"><span data-stu-id="339b3-141">The indentation under the `if` and `else` statements is for human readers.</span></span>
> <span data-ttu-id="339b3-142">W języku C# nie mają wcięcia ani białe miejsca znaczenia.</span><span class="sxs-lookup"><span data-stu-id="339b3-142">The C# language doesn't treat indentation or white space as significant.</span></span> <span data-ttu-id="339b3-143">Instrukcja po słowie `if` lub `else` — słowo kluczowe zostanie wykonana w zależności od warunku.</span><span class="sxs-lookup"><span data-stu-id="339b3-143">The statement following the `if` or `else` keyword will be executed based on the condition.</span></span> <span data-ttu-id="339b3-144">Wszystkie przykłady w tym samouczku wykonaj jest stosowana powszechna praktyka wcięć odpowiadających przepływowi sterowania instrukcji.</span><span class="sxs-lookup"><span data-stu-id="339b3-144">All the samples in this tutorial follow a common practice to indent lines based on the control flow of statements.</span></span>

<span data-ttu-id="339b3-145">Ponieważ wcięcia nie ma znaczenia, należy użyć `{` i `}` wskazać, kiedy ma więcej niż jedna instrukcja jako część bloku wykonywanego warunkowo.</span><span class="sxs-lookup"><span data-stu-id="339b3-145">Because indentation is not significant, you need to use `{` and `}` to indicate when you want more than one statement to be part of the block that executes conditionally.</span></span> <span data-ttu-id="339b3-146">Programiści języka C# zazwyczaj używają nawiasów klamrowych we wszystkich `if` i `else` klauzul.</span><span class="sxs-lookup"><span data-stu-id="339b3-146">C# programmers typically use those braces on all `if` and `else` clauses.</span></span> <span data-ttu-id="339b3-147">Poniższy przykład jest taka sama jak właśnie utworzony.</span><span class="sxs-lookup"><span data-stu-id="339b3-147">The following example is the same as the one you just created.</span></span> <span data-ttu-id="339b3-148">Zmodyfikuj kod powyżej, aby dopasować następujący kod:</span><span class="sxs-lookup"><span data-stu-id="339b3-148">Modify your code above to match the following code:</span></span>

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
> <span data-ttu-id="339b3-149">Za pomocą pozostałej części tego samouczka, wszystkie przykłady kodu zawierają nawiasy klamrowe, zgodnie z przyjętą.</span><span class="sxs-lookup"><span data-stu-id="339b3-149">Through the rest of this tutorial, the code samples all include the braces, following accepted practices.</span></span>

<span data-ttu-id="339b3-150">Możesz przetestować bardziej skomplikowanych warunków.</span><span class="sxs-lookup"><span data-stu-id="339b3-150">You can test more complicated conditions.</span></span> <span data-ttu-id="339b3-151">Dodaj następujący kod w swojej `Main` metoda po kodzie napisanych do tej pory:</span><span class="sxs-lookup"><span data-stu-id="339b3-151">Add the following code in your `Main` method after the code you've written so far:</span></span>

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

<span data-ttu-id="339b3-152">`&&` Reprezentuje "i".</span><span class="sxs-lookup"><span data-stu-id="339b3-152">The `&&` represents "and".</span></span> <span data-ttu-id="339b3-153">Oznacza to, że oba warunki muszą być spełnione, aby wykonać tę instrukcję w gałęzi dla wartości true.</span><span class="sxs-lookup"><span data-stu-id="339b3-153">It means both conditions must be true to execute the statement in the true branch.</span></span>  <span data-ttu-id="339b3-154">Te przykłady przedstawiają także, może mieć wielu instrukcji w każdej gałęzi warunkowej, pod warunkiem, należy ująć je w `{` i `}`.</span><span class="sxs-lookup"><span data-stu-id="339b3-154">These examples also show that you can have multiple statements in each conditional branch, provided you enclose them in `{` and `}`.</span></span>

<span data-ttu-id="339b3-155">Można również użyć `||` do reprezentowania "or".</span><span class="sxs-lookup"><span data-stu-id="339b3-155">You can also use  `||` to represent "or".</span></span> <span data-ttu-id="339b3-156">Dodaj następujący kod, po czym napisanych do tej pory:</span><span class="sxs-lookup"><span data-stu-id="339b3-156">Add the following code after what you've written so far:</span></span>

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

<span data-ttu-id="339b3-157">Pierwszym krokiem zostały ukończone.</span><span class="sxs-lookup"><span data-stu-id="339b3-157">You've finished the first step.</span></span> <span data-ttu-id="339b3-158">Przed rozpoczęciem następnej sekcji, Przejdźmy bieżącego kodu w oddzielnych metodach.</span><span class="sxs-lookup"><span data-stu-id="339b3-158">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="339b3-159">Który sprawia, że łatwiej rozpocząć pracę z nową przykładową.</span><span class="sxs-lookup"><span data-stu-id="339b3-159">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="339b3-160">Zmiana nazwy Twojego `Main` metodę, aby `ExploreIf` i zapisywać nowy `Main` metodę, która wywołuje `ExploreIf`.</span><span class="sxs-lookup"><span data-stu-id="339b3-160">Rename your `Main` method to `ExploreIf` and write a new `Main` method that calls `ExploreIf`.</span></span> <span data-ttu-id="339b3-161">Po zakończeniu, kod powinien wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="339b3-161">When you have finished, your code should look like this:</span></span>

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

<span data-ttu-id="339b3-162">Komentarz wywołanie `ExploreIf()`.</span><span class="sxs-lookup"><span data-stu-id="339b3-162">Comment out the call to `ExploreIf()`.</span></span> <span data-ttu-id="339b3-163">Spowoduje to, że dane wyjściowe, które mniej "zatłoczony" podczas pracy w tej sekcji:</span><span class="sxs-lookup"><span data-stu-id="339b3-163">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//ExploreIf();
```

<span data-ttu-id="339b3-164">`//` Uruchamia **komentarz** w C#.</span><span class="sxs-lookup"><span data-stu-id="339b3-164">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="339b3-165">Komentarze są dowolny tekst, który chcesz zachować w kodzie źródłowym, ale nie jest wykonywane jako kod.</span><span class="sxs-lookup"><span data-stu-id="339b3-165">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="339b3-166">Kompilator nie generuje żadnego kodu wykonywalnego z komentarzy.</span><span class="sxs-lookup"><span data-stu-id="339b3-166">The compiler does not generate any executable code from comments.</span></span>

## <a name="use-loops-to-repeat-operations"></a><span data-ttu-id="339b3-167">Użycie pętli do powtarzania operacji</span><span class="sxs-lookup"><span data-stu-id="339b3-167">Use loops to repeat operations</span></span>

<span data-ttu-id="339b3-168">W tej sekcji użyjesz **pętli** do powtarzania instrukcji.</span><span class="sxs-lookup"><span data-stu-id="339b3-168">In this section you use **loops** to repeat statements.</span></span> <span data-ttu-id="339b3-169">Wypróbuj ten kod w swojej `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="339b3-169">Try this code in your `Main` method:</span></span>

```csharp
int counter = 0;
while (counter < 10)
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
}
```

<span data-ttu-id="339b3-170">`while` Instrukcji sprawdza warunek i wykonuje instrukcję lub blok instrukcji po `while`.</span><span class="sxs-lookup"><span data-stu-id="339b3-170">The `while` statement checks a condition and executes the statement or statement block following the `while`.</span></span> <span data-ttu-id="339b3-171">Wielokrotnie sprawdza warunek i wykonywanie instrukcji, dopóki warunek jest fałszywy.</span><span class="sxs-lookup"><span data-stu-id="339b3-171">It repeatedly checks the condition and executing those statements until the condition is false.</span></span>

<span data-ttu-id="339b3-172">W tym przykładzie jest jeszcze jeden nowy operator.</span><span class="sxs-lookup"><span data-stu-id="339b3-172">There's one other new operator in this example.</span></span> <span data-ttu-id="339b3-173">`++` Po `counter` zmienna jest **przyrostu** operatora.</span><span class="sxs-lookup"><span data-stu-id="339b3-173">The `++` after the `counter` variable is the **increment** operator.</span></span> <span data-ttu-id="339b3-174">Dodaje do wartości 1 `counter` i zapisuje wynikową wartość w `counter` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="339b3-174">It adds 1 to the value of `counter` and stores that value in the `counter` variable.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="339b3-175">Upewnij się, że `while` pętli warunek zmiany na wartość false podczas wykonywania kodu.</span><span class="sxs-lookup"><span data-stu-id="339b3-175">Make sure that the `while` loop condition changes to false as you execute the code.</span></span> <span data-ttu-id="339b3-176">W przeciwnym razie utwórz **Pętla nieskończona** gdzie programu nigdy się nie skończy.</span><span class="sxs-lookup"><span data-stu-id="339b3-176">Otherwise, you create an **infinite loop** where your program never ends.</span></span> <span data-ttu-id="339b3-177">Który nie jest pokazana w tym przykładzie, ponieważ trzeba wymusić program, aby zrezygnować z używania **CTRL-C** lub w inny sposób.</span><span class="sxs-lookup"><span data-stu-id="339b3-177">That is not demonstrated in this sample, because you have to force your program to quit using **CTRL-C** or other means.</span></span>

<span data-ttu-id="339b3-178">`while` Pętli testuje warunek przed wykonaniem kodu po `while`.</span><span class="sxs-lookup"><span data-stu-id="339b3-178">The `while` loop tests the condition before executing the code following the `while`.</span></span> <span data-ttu-id="339b3-179">`do` ... `while` pętli najpierw wykonuje kod, a następnie sprawdza warunek.</span><span class="sxs-lookup"><span data-stu-id="339b3-179">The `do` ... `while` loop executes the code first, and then checks the condition.</span></span> <span data-ttu-id="339b3-180">Czy podczas pętli jest wyświetlany w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="339b3-180">The do while loop is shown in the following code:</span></span>

```csharp
counter = 0;
do
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
} while (counter < 10);
```

<span data-ttu-id="339b3-181">To `do` pętli i wcześniej `while` pętli generuje ten sam wynik.</span><span class="sxs-lookup"><span data-stu-id="339b3-181">This `do` loop and the earlier `while` loop produce the same output.</span></span>

## <a name="work-with-the-for-loop"></a><span data-ttu-id="339b3-182">Praca z pętli for</span><span class="sxs-lookup"><span data-stu-id="339b3-182">Work with the for loop</span></span>

<span data-ttu-id="339b3-183">**Dla** pętli jest często używana w C#.</span><span class="sxs-lookup"><span data-stu-id="339b3-183">The **for** loop is commonly used in C#.</span></span> <span data-ttu-id="339b3-184">Wypróbuj ten kod w metodzie Main():</span><span class="sxs-lookup"><span data-stu-id="339b3-184">Try this code in your Main() method:</span></span>

```csharp
for(int index = 0; index < 10; index++)
{
    Console.WriteLine($"Hello World! The index is {index}");
} 
```

<span data-ttu-id="339b3-185">To działa ten sam jako `while` pętli i `do` pętli został już użyty.</span><span class="sxs-lookup"><span data-stu-id="339b3-185">This does the same work as the `while` loop and the `do` loop you've already used.</span></span> <span data-ttu-id="339b3-186">`for` Instrukcja składa się z trzech części, które sterują jej pracą.</span><span class="sxs-lookup"><span data-stu-id="339b3-186">The `for` statement has three parts that control how it works.</span></span>

<span data-ttu-id="339b3-187">Pierwsza część to **dla inicjatora**: `for index = 0;` oświadcza, że `index` jako zmienną pętli i ustawia jej wartość początkową `0`.</span><span class="sxs-lookup"><span data-stu-id="339b3-187">The first part is the **for initializer**: `for index = 0;` declares that `index` is the loop variable, and sets its initial value to `0`.</span></span>

<span data-ttu-id="339b3-188">Środkowa część to **warunku**: `index < 10` oświadcza, że `for` pętli kontynuuje wykonywanie dopóki wartość licznika jest mniejsza niż 10.</span><span class="sxs-lookup"><span data-stu-id="339b3-188">The middle part is the **for condition**: `index < 10` declares that this `for` loop continues to execute as long as the value of counter is less than 10.</span></span>

<span data-ttu-id="339b3-189">Ostatnia część to **dla iteratora**: `index++` określa sposób modyfikowana zmienna pętli po wykonaniu bloku występującego `for` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="339b3-189">The final part is the **for iterator**: `index++` specifies how to modify the loop variable after executing the block following the `for` statement.</span></span> <span data-ttu-id="339b3-190">Określa ona, że w tym miejscu `index` należy zwiększyć o 1 po każdym wykonaniu bloku.</span><span class="sxs-lookup"><span data-stu-id="339b3-190">Here, it specifies that `index` should be incremented by 1 each time the block executes.</span></span>

<span data-ttu-id="339b3-191">Wypróbuj te samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="339b3-191">Experiment with these yourself.</span></span> <span data-ttu-id="339b3-192">Wypróbuj następujące czynniki:</span><span class="sxs-lookup"><span data-stu-id="339b3-192">Try each of the following:</span></span>

- <span data-ttu-id="339b3-193">Zmień inicjator, tak aby można było uruchomić na inną wartość.</span><span class="sxs-lookup"><span data-stu-id="339b3-193">Change the initializer to start at a different value.</span></span>
- <span data-ttu-id="339b3-194">Zmień warunek, którego chcesz zatrzymać miał inną wartość.</span><span class="sxs-lookup"><span data-stu-id="339b3-194">Change the condition to stop at a different value.</span></span>

<span data-ttu-id="339b3-195">Gdy skończysz, przejdziemy pisania kodu, co wykorzystasz zdobyte umiejętności do samodzielnego.</span><span class="sxs-lookup"><span data-stu-id="339b3-195">When you're done, let's move on to write some code yourself to use what you've learned.</span></span>

## <a name="combine-branches-and-loops"></a><span data-ttu-id="339b3-196">Łączenie gałęzi i pętli</span><span class="sxs-lookup"><span data-stu-id="339b3-196">Combine branches and loops</span></span>

<span data-ttu-id="339b3-197">Teraz, gdy wiesz `if` instrukcji i konstrukcje pętli w języku C#, zobacz, jeśli można napisać kod C# obliczający sumę wszystkich liczb całkowitych od 1 do 20 podzielnych przez 3.</span><span class="sxs-lookup"><span data-stu-id="339b3-197">Now that you've seen the `if` statement and the looping constructs in the C# language, see if you can write C# code to find the sum of all integers 1 through 20 that are divisible by 3.</span></span>  <span data-ttu-id="339b3-198">Poniżej przedstawiono kilka wskazówek:</span><span class="sxs-lookup"><span data-stu-id="339b3-198">Here are a few hints:</span></span>

- <span data-ttu-id="339b3-199">`%` Operator umożliwia obliczenie reszty z operacji dzielenia.</span><span class="sxs-lookup"><span data-stu-id="339b3-199">The `%` operator gives you the remainder of a division operation.</span></span>
- <span data-ttu-id="339b3-200">`if` Instrukcji zapewnia warunku określającego, jeśli liczba powinna być częścią sumy.</span><span class="sxs-lookup"><span data-stu-id="339b3-200">The `if` statement gives you the condition to see if a number should be part of the sum.</span></span>
- <span data-ttu-id="339b3-201">`for` Pętli ułatwia powtórzenie serii kroków dla wszystkich liczb od 1 do 20.</span><span class="sxs-lookup"><span data-stu-id="339b3-201">The `for` loop can help you repeat a series of steps for all the numbers 1 through 20.</span></span>

<span data-ttu-id="339b3-202">Wypróbuj ją samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="339b3-202">Try it yourself.</span></span> <span data-ttu-id="339b3-203">Sprawdź, jak Ci poszło.</span><span class="sxs-lookup"><span data-stu-id="339b3-203">Then check how you did.</span></span> <span data-ttu-id="339b3-204">Odpowiedź powinna wynosić 63.</span><span class="sxs-lookup"><span data-stu-id="339b3-204">You should get 63 for an answer.</span></span> <span data-ttu-id="339b3-205">Możesz zobaczyć jeden możliwa odpowiedź przez [wyświetlanie kompletny kod w serwisie GitHub](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54).</span><span class="sxs-lookup"><span data-stu-id="339b3-205">You can see one possible answer by [viewing the completed code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54).</span></span>

<span data-ttu-id="339b3-206">Pomyślnie ukończono samouczek "gałęzi i pętli".</span><span class="sxs-lookup"><span data-stu-id="339b3-206">You've completed the "branches and loops" tutorial.</span></span>

<span data-ttu-id="339b3-207">Możesz kontynuować [Interpolacja ciągów](interpolated-strings-local.md) samouczków w środowisku projektowym.</span><span class="sxs-lookup"><span data-stu-id="339b3-207">You can continue with the [String interpolation](interpolated-strings-local.md) tutorial in your own development environment.</span></span>

<span data-ttu-id="339b3-208">Możesz dowiedzieć się więcej na temat tych pojęć w następujących tematach:</span><span class="sxs-lookup"><span data-stu-id="339b3-208">You can learn more about these concepts in these topics:</span></span>

[<span data-ttu-id="339b3-209">Jeśli i else, instrukcja</span><span class="sxs-lookup"><span data-stu-id="339b3-209">If and else statement</span></span>](../../language-reference/keywords/if-else.md)  
[<span data-ttu-id="339b3-210">while — instrukcja</span><span class="sxs-lookup"><span data-stu-id="339b3-210">While statement</span></span>](../../language-reference/keywords/while.md)  
[<span data-ttu-id="339b3-211">— Instrukcja</span><span class="sxs-lookup"><span data-stu-id="339b3-211">Do statement</span></span>](../../language-reference/keywords/do.md)  
[<span data-ttu-id="339b3-212">For — instrukcja</span><span class="sxs-lookup"><span data-stu-id="339b3-212">For statement</span></span>](../../language-reference/keywords/for.md)  

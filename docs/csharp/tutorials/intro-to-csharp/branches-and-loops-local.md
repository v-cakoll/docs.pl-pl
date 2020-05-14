---
title: Rozgałęzienia i pętle — wprowadzenie do samouczka języka C#
description: W tym samouczku dotyczącym gałęzi i pętli można napisać kod w języku C#, aby poznać składnię języka, która obsługuje gałęzie warunkowe, i pętle, aby wielokrotnie wykonywać instrukcje.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: d67cfe359634783bb542e9ac34df52a095b45c20
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396879"
---
# <a name="learn-conditional-logic-with-branch-and-loop-statements"></a><span data-ttu-id="08eef-103">Informacje o logice warunkowej przy użyciu instrukcji Branch i Loop</span><span class="sxs-lookup"><span data-stu-id="08eef-103">Learn conditional logic with branch and loop statements</span></span>

<span data-ttu-id="08eef-104">W tym samouczku przedstawiono sposób pisania kodu, który analizuje zmienne i zmienia ścieżkę wykonywania na podstawie tych zmiennych.</span><span class="sxs-lookup"><span data-stu-id="08eef-104">This tutorial teaches you how to write code that examines variables and changes the execution path based on those variables.</span></span> <span data-ttu-id="08eef-105">Napiszesz kod w języku C# i zobaczysz wyniki kompilacji i uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="08eef-105">You write C# code and see the results of compiling and running it.</span></span> <span data-ttu-id="08eef-106">Samouczek zawiera szereg lekcji, które eksplorują gałęzie i konstrukcje zapętlenia w języku C#.</span><span class="sxs-lookup"><span data-stu-id="08eef-106">The tutorial contains a series of lessons that explore branching and looping constructs in C#.</span></span> <span data-ttu-id="08eef-107">Te lekcje umożliwiają poznanie podstaw języka C#.</span><span class="sxs-lookup"><span data-stu-id="08eef-107">These lessons teach you the fundamentals of the C# language.</span></span>

<span data-ttu-id="08eef-108">Ten samouczek oczekuje, że masz maszynę, której możesz użyć do programowania.</span><span class="sxs-lookup"><span data-stu-id="08eef-108">This tutorial expects you to have a machine you can use for development.</span></span> <span data-ttu-id="08eef-109">Samouczek platformy .NET [Hello World w ciągu 10 minut](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) zawiera instrukcje dotyczące konfigurowania lokalnego środowiska deweloperskiego w systemie Windows, Linux lub macOS.</span><span class="sxs-lookup"><span data-stu-id="08eef-109">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span> <span data-ttu-id="08eef-110">Krótkie omówienie poleceń, z których będziesz korzystać, znajduje się w zapoznanie [z narzędziami programistycznymi](local-environment.md) zawierającymi linki do dalszych szczegółów.</span><span class="sxs-lookup"><span data-stu-id="08eef-110">A quick overview of the commands you'll use is in the [Become familiar with the development tools](local-environment.md) with links to more details.</span></span>

## <a name="make-decisions-using-the-if-statement"></a><span data-ttu-id="08eef-111">Podejmowanie decyzji przy użyciu `if` instrukcji</span><span class="sxs-lookup"><span data-stu-id="08eef-111">Make decisions using the `if` statement</span></span>

<span data-ttu-id="08eef-112">Utwórz katalog o nazwie *branchs — samouczek*.</span><span class="sxs-lookup"><span data-stu-id="08eef-112">Create a directory named *branches-tutorial*.</span></span> <span data-ttu-id="08eef-113">Upewnij się, że bieżący katalog i uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="08eef-113">Make that the current directory and run the following command:</span></span>

```dotnetcli
dotnet new console -n BranchesAndLoops -o .
```

<span data-ttu-id="08eef-114">To polecenie powoduje utworzenie nowej aplikacji konsolowej .NET Core w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="08eef-114">This command creates a new .NET Core console application in the current directory.</span></span>

<span data-ttu-id="08eef-115">Otwórz *program.cs* w ulubionym edytorze i Zastąp wiersz `Console.WriteLine("Hello World!");` następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="08eef-115">Open *Program.cs* in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following code:</span></span>

```csharp
int a = 5;
int b = 6;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10.");
```

<span data-ttu-id="08eef-116">Wypróbuj ten kod, wpisując `dotnet run` w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="08eef-116">Try this code by typing `dotnet run` in your console window.</span></span> <span data-ttu-id="08eef-117">Powinien zostać wyświetlony komunikat "odpowiedź jest większa niż 10".</span><span class="sxs-lookup"><span data-stu-id="08eef-117">You should see the message "The answer is greater than 10."</span></span> <span data-ttu-id="08eef-118">Wydrukowano w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="08eef-118">printed to your console.</span></span>

<span data-ttu-id="08eef-119">Zmodyfikuj deklarację zmiennej `b`, tak aby suma była mniejsza niż 10:</span><span class="sxs-lookup"><span data-stu-id="08eef-119">Modify the declaration of `b` so that the sum is less than 10:</span></span>

```csharp
int b = 3;
```

<span data-ttu-id="08eef-120">Wpisz `dotnet run` ponownie.</span><span class="sxs-lookup"><span data-stu-id="08eef-120">Type `dotnet run` again.</span></span> <span data-ttu-id="08eef-121">Ponieważ odpowiedź jest mniejsza niż 10, nic nie zostanie wyświetlone.</span><span class="sxs-lookup"><span data-stu-id="08eef-121">Because the answer is less than 10, nothing is printed.</span></span> <span data-ttu-id="08eef-122">Testowany **warunek** ma wartość false.</span><span class="sxs-lookup"><span data-stu-id="08eef-122">The **condition** you're testing is false.</span></span> <span data-ttu-id="08eef-123">Nie ma żadnego kodu do wykonania, ponieważ napisano kod tylko dla jednej z możliwych gałęzi instrukcji `if`: wykonywanej dla wartości true.</span><span class="sxs-lookup"><span data-stu-id="08eef-123">You don't have any code to execute because you've only written one of the possible branches for an `if` statement: the true branch.</span></span>

> [!TIP]
> <span data-ttu-id="08eef-124">Podczas nauki języka C# (lub dowolnego języka programowania) będziesz robić błędy przy pisaniu kodu.</span><span class="sxs-lookup"><span data-stu-id="08eef-124">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="08eef-125">Kompilator znajdzie i zgłosi błędy.</span><span class="sxs-lookup"><span data-stu-id="08eef-125">The compiler will find and report the errors.</span></span> <span data-ttu-id="08eef-126">Sprawdź blisko danych wyjściowych błędu i kod, który wygenerował błąd.</span><span class="sxs-lookup"><span data-stu-id="08eef-126">Look closely at the error output and the code that generated the error.</span></span> <span data-ttu-id="08eef-127">Błąd kompilatora może zwykle pomóc w znalezieniu problemu.</span><span class="sxs-lookup"><span data-stu-id="08eef-127">The compiler error can usually help you find the problem.</span></span>

<span data-ttu-id="08eef-128">Ten pierwszy przykład pokazuje moc `if` i typy logiczne.</span><span class="sxs-lookup"><span data-stu-id="08eef-128">This first sample shows the power of `if` and Boolean types.</span></span> <span data-ttu-id="08eef-129">*Wartość logiczna* to zmienna, która może mieć jedną z dwóch wartości: `true` lub `false` .</span><span class="sxs-lookup"><span data-stu-id="08eef-129">A *Boolean* is a variable that can have one of two values: `true` or `false`.</span></span> <span data-ttu-id="08eef-130">C# definiuje typ specjalny, `bool` dla zmiennych logicznych.</span><span class="sxs-lookup"><span data-stu-id="08eef-130">C# defines a special type, `bool` for Boolean variables.</span></span> <span data-ttu-id="08eef-131">Instrukcja `if` umożliwia sprawdzenie wartości typu `bool`.</span><span class="sxs-lookup"><span data-stu-id="08eef-131">The `if` statement checks the value of a `bool`.</span></span> <span data-ttu-id="08eef-132">Jeśli wartość to `true`, zostanie wykonana instrukcja następująca po instrukcji `if`.</span><span class="sxs-lookup"><span data-stu-id="08eef-132">When the value is `true`, the statement following the `if` executes.</span></span> <span data-ttu-id="08eef-133">W przeciwnym razie zostanie pominięty.</span><span class="sxs-lookup"><span data-stu-id="08eef-133">Otherwise, it's skipped.</span></span>

<span data-ttu-id="08eef-134">Ten proces sprawdzania warunków i wykonywania instrukcji na podstawie tych warunków jest zaawansowany.</span><span class="sxs-lookup"><span data-stu-id="08eef-134">This process of checking conditions and executing statements based on those conditions is powerful.</span></span>

## <a name="make-if-and-else-work-together"></a><span data-ttu-id="08eef-135">Łączenie działania instrukcji if i else</span><span class="sxs-lookup"><span data-stu-id="08eef-135">Make if and else work together</span></span>

<span data-ttu-id="08eef-136">Aby wykonać różny kod w gałęziach dla wartości true i false, należy utworzyć gałąź `else` wykonywaną, jeśli wartość warunku to false.</span><span class="sxs-lookup"><span data-stu-id="08eef-136">To execute different code in both the true and false branches, you create an `else` branch that executes when the condition is false.</span></span> <span data-ttu-id="08eef-137">Wypróbuj to.</span><span class="sxs-lookup"><span data-stu-id="08eef-137">Try this.</span></span> <span data-ttu-id="08eef-138">Dodaj ostatnie dwa wiersze w kodzie poniżej do `Main` metody (należy mieć już pierwsze cztery):</span><span class="sxs-lookup"><span data-stu-id="08eef-138">Add the last two lines in the code below to your `Main` method (you should already have the first four):</span></span>

```csharp
int a = 5;
int b = 3;
if (a + b > 10)
    Console.WriteLine("The answer is greater than 10");
else
    Console.WriteLine("The answer is not greater than 10");
```

<span data-ttu-id="08eef-139">Instrukcja po słowie kluczowym `else` jest wykonywana tylko wtedy, gdy testowany warunek ma wartość `false`.</span><span class="sxs-lookup"><span data-stu-id="08eef-139">The statement following the `else` keyword executes only when the condition being tested is `false`.</span></span> <span data-ttu-id="08eef-140">Łączenie `if` i `else` z warunkami logicznymi zapewnia wszystko, co jest potrzebne do obsługi zarówno `true` warunku, jak i `false` .</span><span class="sxs-lookup"><span data-stu-id="08eef-140">Combining `if` and `else` with Boolean conditions provides all the power you need to handle both a `true` and a `false` condition.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="08eef-141">Wcięcia pod instrukcjami `if` i `else` służą tylko do zwiększenia czytelności.</span><span class="sxs-lookup"><span data-stu-id="08eef-141">The indentation under the `if` and `else` statements is for human readers.</span></span>
> <span data-ttu-id="08eef-142">Język C# nie traktuje wcięcia ani odstępu jako znaczącego.</span><span class="sxs-lookup"><span data-stu-id="08eef-142">The C# language doesn't treat indentation or white space as significant.</span></span>
> <span data-ttu-id="08eef-143">Instrukcja po słowie kluczowym `if` lub `else` zostanie wykonana w zależności od warunku.</span><span class="sxs-lookup"><span data-stu-id="08eef-143">The statement following the `if` or `else` keyword will be executed based on the condition.</span></span> <span data-ttu-id="08eef-144">Wszystkie przykłady w tym samouczku są zgodne ze wspólną metodą tworzenia wcięć wierszy na podstawie przepływu sterowania instrukcji.</span><span class="sxs-lookup"><span data-stu-id="08eef-144">All the samples in this tutorial follow a common practice to indent lines based on the control flow of statements.</span></span>

<span data-ttu-id="08eef-145">Ponieważ wcięcia nie są istotne, należy użyć `{` i, `}` Aby wskazać, Kiedy chcesz, aby więcej niż jedna instrukcja była częścią bloku, który jest wykonywany warunkowo.</span><span class="sxs-lookup"><span data-stu-id="08eef-145">Because indentation isn't significant, you need to use `{` and `}` to indicate when you want more than one statement to be part of the block that executes conditionally.</span></span> <span data-ttu-id="08eef-146">Programiści języka C# zazwyczaj używają nawiasów klamrowych we wszystkich klauzulach `if` i `else`.</span><span class="sxs-lookup"><span data-stu-id="08eef-146">C# programmers typically use those braces on all `if` and `else` clauses.</span></span> <span data-ttu-id="08eef-147">Poniższy przykład jest taki sam jak utworzony przez siebie.</span><span class="sxs-lookup"><span data-stu-id="08eef-147">The following example is the same as the one you created.</span></span> <span data-ttu-id="08eef-148">Zmodyfikuj kod powyżej, aby był zgodny z następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="08eef-148">Modify your code above to match the following code:</span></span>

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
> <span data-ttu-id="08eef-149">W pozostałej części tego samouczka wszystkie przykłady kodu zawierają nawiasy klamrowe, po zastosowaniu zaakceptowanych praktyk.</span><span class="sxs-lookup"><span data-stu-id="08eef-149">Through the rest of this tutorial, the code samples all include the braces, following accepted practices.</span></span>

<span data-ttu-id="08eef-150">Możesz przetestować bardziej skomplikowane warunki.</span><span class="sxs-lookup"><span data-stu-id="08eef-150">You can test more complicated conditions.</span></span> <span data-ttu-id="08eef-151">Dodaj następujący kod w `Main` metodzie po kodzie, który zapisano do tej pory:</span><span class="sxs-lookup"><span data-stu-id="08eef-151">Add the following code in your `Main` method after the code you've written so far:</span></span>

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

<span data-ttu-id="08eef-152">`==`Symbol sprawdza *równość*.</span><span class="sxs-lookup"><span data-stu-id="08eef-152">The `==` symbol tests for *equality*.</span></span> <span data-ttu-id="08eef-153">Użycie `==` odróżnia test pod kątem równości przed przypisaniem `a = 5` .</span><span class="sxs-lookup"><span data-stu-id="08eef-153">Using `==` distinguishes the test for equality from assignment, which you saw in `a = 5`.</span></span>

<span data-ttu-id="08eef-154">Znaki `&&` określają warunek „i”.</span><span class="sxs-lookup"><span data-stu-id="08eef-154">The `&&` represents "and".</span></span> <span data-ttu-id="08eef-155">Oznacza to, że instrukcja w gałęzi dla wartości true zostanie wykonana tylko wtedy, gdy oba warunki będą mieć wartość true.</span><span class="sxs-lookup"><span data-stu-id="08eef-155">It means both conditions must be true to execute the statement in the true branch.</span></span>  <span data-ttu-id="08eef-156">Te przykłady przedstawiają także, że można użyć wielu instrukcji w każdej gałęzi warunkowej, jeśli zostaną umieszczone między znakami `{` i `}`.</span><span class="sxs-lookup"><span data-stu-id="08eef-156">These examples also show that you can have multiple statements in each conditional branch, provided you enclose them in `{` and `}`.</span></span>

<span data-ttu-id="08eef-157">Można również użyć `||` do reprezentowania "or".</span><span class="sxs-lookup"><span data-stu-id="08eef-157">You can also use  `||` to represent "or".</span></span> <span data-ttu-id="08eef-158">Dodaj następujący kod po wykonaniu tej czynności:</span><span class="sxs-lookup"><span data-stu-id="08eef-158">Add the following code after what you've written so far:</span></span>

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

<span data-ttu-id="08eef-159">Zmodyfikuj wartości `a` , `b` i `c` i przełączenie między `&&` i `||` do Eksploruj.</span><span class="sxs-lookup"><span data-stu-id="08eef-159">Modify the values of `a`, `b`, and `c` and switch between `&&` and `||` to explore.</span></span> <span data-ttu-id="08eef-160">Dowiesz się, jak `&&` `||` działają operatory i.</span><span class="sxs-lookup"><span data-stu-id="08eef-160">You'll gain more understanding of how the `&&` and `||` operators work.</span></span>

<span data-ttu-id="08eef-161">Wykonano pierwszy krok.</span><span class="sxs-lookup"><span data-stu-id="08eef-161">You've finished the first step.</span></span> <span data-ttu-id="08eef-162">Przed rozpoczęciem następnej sekcji przechodźmy bieżący kod w oddzielną metodę.</span><span class="sxs-lookup"><span data-stu-id="08eef-162">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="08eef-163">Ułatwia to rozpoczęcie pracy z nowym przykładem.</span><span class="sxs-lookup"><span data-stu-id="08eef-163">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="08eef-164">Zmień nazwę `Main` metody na `ExploreIf` i Napisz nową `Main` metodę, która wywołuje `ExploreIf` .</span><span class="sxs-lookup"><span data-stu-id="08eef-164">Rename your `Main` method to `ExploreIf` and write a new `Main` method that calls `ExploreIf`.</span></span> <span data-ttu-id="08eef-165">Po zakończeniu kod powinien wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="08eef-165">When you've finished, your code should look like this:</span></span>

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

<span data-ttu-id="08eef-166">Komentarz wywołania do `ExploreIf()` .</span><span class="sxs-lookup"><span data-stu-id="08eef-166">Comment out the call to `ExploreIf()`.</span></span> <span data-ttu-id="08eef-167">Dane wyjściowe będą mniej czytelne podczas pracy w tej sekcji:</span><span class="sxs-lookup"><span data-stu-id="08eef-167">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//ExploreIf();
```

<span data-ttu-id="08eef-168">`//`W języku C# jest uruchamiany **komentarz** .</span><span class="sxs-lookup"><span data-stu-id="08eef-168">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="08eef-169">Komentarze są dowolnym tekstem, który chcesz zachować w kodzie źródłowym, ale nie można go wykonać jako kod.</span><span class="sxs-lookup"><span data-stu-id="08eef-169">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="08eef-170">Kompilator nie generuje żadnego kodu wykonywalnego z komentarzy.</span><span class="sxs-lookup"><span data-stu-id="08eef-170">The compiler doesn't generate any executable code from comments.</span></span>

## <a name="use-loops-to-repeat-operations"></a><span data-ttu-id="08eef-171">Użycie pętli do powtarzania operacji</span><span class="sxs-lookup"><span data-stu-id="08eef-171">Use loops to repeat operations</span></span>

<span data-ttu-id="08eef-172">W tej sekcji użyto **pętli** do powtarzania instrukcji.</span><span class="sxs-lookup"><span data-stu-id="08eef-172">In this section, you use **loops** to repeat statements.</span></span> <span data-ttu-id="08eef-173">Wypróbuj ten kod w `Main` metodzie:</span><span class="sxs-lookup"><span data-stu-id="08eef-173">Try this code in your `Main` method:</span></span>

```csharp
int counter = 0;
while (counter < 10)
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
}
```

<span data-ttu-id="08eef-174">`while`Instrukcja sprawdza warunek i wykonuje instrukcję lub blok instrukcji po `while` .</span><span class="sxs-lookup"><span data-stu-id="08eef-174">The `while` statement checks a condition and executes the statement or statement block following the `while`.</span></span> <span data-ttu-id="08eef-175">Wielokrotnie sprawdza warunek i wykonuje te instrukcje do momentu, gdy warunek nie ma wartości false.</span><span class="sxs-lookup"><span data-stu-id="08eef-175">It repeatedly checks the condition and executing those statements until the condition is false.</span></span>

<span data-ttu-id="08eef-176">Ten przykład zawiera jeszcze jeden nowy operator.</span><span class="sxs-lookup"><span data-stu-id="08eef-176">There's one other new operator in this example.</span></span> <span data-ttu-id="08eef-177">Znaki `++` po zmiennej `counter` oznaczają operator **inkrementacji**.</span><span class="sxs-lookup"><span data-stu-id="08eef-177">The `++` after the `counter` variable is the **increment** operator.</span></span> <span data-ttu-id="08eef-178">Dodaje 1 do wartości `counter` i zapisuje tę wartość w `counter` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="08eef-178">It adds 1 to the value of `counter` and stores that value in the `counter` variable.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="08eef-179">Upewnij się, że `while` warunek pętli zmieni się na FAŁSZ podczas wykonywania kodu.</span><span class="sxs-lookup"><span data-stu-id="08eef-179">Make sure that the `while` loop condition changes to false as you execute the code.</span></span> <span data-ttu-id="08eef-180">W przeciwnym razie wystąpi **pętla nieskończona**, czyli wykonywanie programu nigdy się nie skończy.</span><span class="sxs-lookup"><span data-stu-id="08eef-180">Otherwise, you create an **infinite loop** where your program never ends.</span></span> <span data-ttu-id="08eef-181">Nie jest to pokazane w tym przykładzie, ponieważ trzeba wymusić zamknięcie programu przy użyciu **klawiszy CTRL-C** lub innych.</span><span class="sxs-lookup"><span data-stu-id="08eef-181">That is not demonstrated in this sample, because you have to force your program to quit using **CTRL-C** or other means.</span></span>

<span data-ttu-id="08eef-182">Pętla `while` testuje warunek przed wykonaniem kodu po instrukcji `while`.</span><span class="sxs-lookup"><span data-stu-id="08eef-182">The `while` loop tests the condition before executing the code following the `while`.</span></span> <span data-ttu-id="08eef-183">Pętla `do`...`while` najpierw wykonuje kod, a następnie sprawdza warunek.</span><span class="sxs-lookup"><span data-stu-id="08eef-183">The `do` ... `while` loop executes the code first, and then checks the condition.</span></span> <span data-ttu-id="08eef-184">Pętla *do while* jest pokazana w poniższym kodzie:</span><span class="sxs-lookup"><span data-stu-id="08eef-184">The *do while* loop is shown in the following code:</span></span>

```csharp
int counter = 0;
do
{
    Console.WriteLine($"Hello World! The counter is {counter}");
    counter++;
} while (counter < 10);
```

<span data-ttu-id="08eef-185">Ta `do` Pętla i wcześniejsza `while` Pętla tworzą te same dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="08eef-185">This `do` loop and the earlier `while` loop produce the same output.</span></span>

## <a name="work-with-the-for-loop"></a><span data-ttu-id="08eef-186">Praca z pętlą for</span><span class="sxs-lookup"><span data-stu-id="08eef-186">Work with the for loop</span></span>

<span data-ttu-id="08eef-187">Pętla **for** jest często używana w języku C#.</span><span class="sxs-lookup"><span data-stu-id="08eef-187">The **for** loop is commonly used in C#.</span></span> <span data-ttu-id="08eef-188">Wypróbuj ten kod w metodzie Main ():</span><span class="sxs-lookup"><span data-stu-id="08eef-188">Try this code in your Main() method:</span></span>

```csharp
for (int index = 0; index < 10; index++)
{
    Console.WriteLine($"Hello World! The index is {index}");
}
```

<span data-ttu-id="08eef-189">Poprzedni kod wykonuje te same działania co `while` Pętla i `do` pętlę, która została już użyta.</span><span class="sxs-lookup"><span data-stu-id="08eef-189">The previous code does the same work as the `while` loop and the `do` loop you've already used.</span></span> <span data-ttu-id="08eef-190">Instrukcja `for` składa się z trzech części, które sterują jej pracą.</span><span class="sxs-lookup"><span data-stu-id="08eef-190">The `for` statement has three parts that control how it works.</span></span>

<span data-ttu-id="08eef-191">Pierwsza część to **inicjator for**: `int index = 0;` deklaruje, że `index` jest to zmienna pętli, i ustawia jej wartość początkową na `0` .</span><span class="sxs-lookup"><span data-stu-id="08eef-191">The first part is the **for initializer**: `int index = 0;` declares that `index` is the loop variable, and sets its initial value to `0`.</span></span>

<span data-ttu-id="08eef-192">Częścią średnią jest **warunek dla**: `index < 10` deklaruje, że ta `for` pętla będzie działać tak długo, jak wartość licznika jest mniejsza niż 10.</span><span class="sxs-lookup"><span data-stu-id="08eef-192">The middle part is the **for condition**: `index < 10` declares that this `for` loop continues to execute as long as the value of counter is less than 10.</span></span>

<span data-ttu-id="08eef-193">Ostatnia część to **iterator**: `index++` określa, jak zmodyfikować zmienną pętli po wykonaniu bloku po `for` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="08eef-193">The final part is the **for iterator**: `index++` specifies how to modify the loop variable after executing the block following the `for` statement.</span></span> <span data-ttu-id="08eef-194">Tutaj zdefiniowano, że zmienną `index` należy zwiększyć o 1 po każdym wykonaniu bloku.</span><span class="sxs-lookup"><span data-stu-id="08eef-194">Here, it specifies that `index` should be incremented by 1 each time the block executes.</span></span>

<span data-ttu-id="08eef-195">Wypróbuj samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="08eef-195">Experiment yourself.</span></span> <span data-ttu-id="08eef-196">Wypróbuj każdą z następujących wariantów:</span><span class="sxs-lookup"><span data-stu-id="08eef-196">Try each of the following variations:</span></span>

- <span data-ttu-id="08eef-197">Zmień inicjator, tak aby miał inną wartość początkową.</span><span class="sxs-lookup"><span data-stu-id="08eef-197">Change the initializer to start at a different value.</span></span>
- <span data-ttu-id="08eef-198">Zmień warunek, tak aby zatrzymanie pętli nastąpiło przy innej wartości.</span><span class="sxs-lookup"><span data-stu-id="08eef-198">Change the condition to stop at a different value.</span></span>

<span data-ttu-id="08eef-199">Gdy skończysz, przejdziemy do samodzielnego pisania kodu, gdzie wykorzystasz zdobyte umiejętności.</span><span class="sxs-lookup"><span data-stu-id="08eef-199">When you're done, let's move on to write some code yourself to use what you've learned.</span></span>

<span data-ttu-id="08eef-200">Istnieje jedna inna instrukcja zapętlenia, która nie została omówiona w tym samouczku: `foreach` instrukcja.</span><span class="sxs-lookup"><span data-stu-id="08eef-200">There's one other looping statement that isn't covered in this tutorial: the `foreach` statement.</span></span> <span data-ttu-id="08eef-201">`foreach`Instrukcja powtarza instrukcję dla każdego elementu w sekwencji elementów.</span><span class="sxs-lookup"><span data-stu-id="08eef-201">The `foreach` statement repeats its statement for every item in a sequence of items.</span></span> <span data-ttu-id="08eef-202">Jest ona najczęściej używana z *kolekcjami*, więc została omówiona w następnym samouczku.</span><span class="sxs-lookup"><span data-stu-id="08eef-202">It's most often used with *collections*, so it's covered in the next tutorial.</span></span>

## <a name="created-nested-loops"></a><span data-ttu-id="08eef-203">Utworzone Pętle zagnieżdżone</span><span class="sxs-lookup"><span data-stu-id="08eef-203">Created nested loops</span></span>

<span data-ttu-id="08eef-204">`while` `do` Pętla,, lub `for` może być zagnieżdżona w innej pętli, aby utworzyć macierz przy użyciu kombinacji każdego elementu w pętli zewnętrznej z każdym elementem w pętli wewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="08eef-204">A `while`, `do`, or `for` loop can be nested inside another loop to create a matrix using the combination of each item in the outer loop with each item in the inner loop.</span></span> <span data-ttu-id="08eef-205">Zróbmy to, aby utworzyć zestaw par alfanumerycznych do reprezentowania wierszy i kolumn.</span><span class="sxs-lookup"><span data-stu-id="08eef-205">Let's do that to build a set of alphanumeric pairs to represent rows and columns.</span></span>

<span data-ttu-id="08eef-206">Jedna `for` pętla może generować wiersze:</span><span class="sxs-lookup"><span data-stu-id="08eef-206">One `for` loop can generate the rows:</span></span>

```csharp
for (int row = 1; row < 11; row++)
{
    Console.WriteLine($"The row is {row}");
}
```

<span data-ttu-id="08eef-207">Inna pętla może generować kolumny:</span><span class="sxs-lookup"><span data-stu-id="08eef-207">Another loop can generate the columns:</span></span>

```csharp
for (char column = 'a'; column < 'k'; column++)
{
    Console.WriteLine($"The column is {column}");
}
```

<span data-ttu-id="08eef-208">Można zagnieździć jedną pętlę wewnątrz par:</span><span class="sxs-lookup"><span data-stu-id="08eef-208">You can nest one loop inside the other to form pairs:</span></span>

```csharp
for (int row = 1; row < 11; row++)
{
    for (char column = 'a'; column < 'k'; column++)
    {
        Console.WriteLine($"The cell is ({row}, {column})");
    }
}
```

<span data-ttu-id="08eef-209">Można zobaczyć, że pętla zewnętrzna przyrostowo rośnie dla każdego pełnego przebiegu pętli wewnętrznej.</span><span class="sxs-lookup"><span data-stu-id="08eef-209">You can see that the outer loop increments once for each full run of the inner loop.</span></span> <span data-ttu-id="08eef-210">Wycofaj zagnieżdżanie wierszy i kolumn i zobacz zmiany dla siebie.</span><span class="sxs-lookup"><span data-stu-id="08eef-210">Reverse the row and column nesting, and see the changes for yourself.</span></span>

## <a name="combine-branches-and-loops"></a><span data-ttu-id="08eef-211">Łączenie gałęzi i pętli</span><span class="sxs-lookup"><span data-stu-id="08eef-211">Combine branches and loops</span></span>

<span data-ttu-id="08eef-212">Teraz, gdy znasz już instrukcję `if` i konstrukcje pętli w języku C#, sprawdź, czy potrafisz napisać kod C# obliczający sumę wszystkich liczb całkowitych z zakresu 1-20 podzielnych przez 3.</span><span class="sxs-lookup"><span data-stu-id="08eef-212">Now that you've seen the `if` statement and the looping constructs in the C# language, see if you can write C# code to find the sum of all integers 1 through 20 that are divisible by 3.</span></span>  <span data-ttu-id="08eef-213">Oto kilka wskazówek:</span><span class="sxs-lookup"><span data-stu-id="08eef-213">Here are a few hints:</span></span>

- <span data-ttu-id="08eef-214">Operator `%` umożliwia obliczenie reszty z operacji dzielenia.</span><span class="sxs-lookup"><span data-stu-id="08eef-214">The `%` operator gives you the remainder of a division operation.</span></span>
- <span data-ttu-id="08eef-215">Instrukcja `if` umożliwia zdefiniowanie warunku określającego, czy liczba powinna być częścią sumy.</span><span class="sxs-lookup"><span data-stu-id="08eef-215">The `if` statement gives you the condition to see if a number should be part of the sum.</span></span>
- <span data-ttu-id="08eef-216">Pętla `for` ułatwia powtórzenie serii kroków dla wszystkich liczb z zakresu 1-20.</span><span class="sxs-lookup"><span data-stu-id="08eef-216">The `for` loop can help you repeat a series of steps for all the numbers 1 through 20.</span></span>

<span data-ttu-id="08eef-217">Spróbuj napisać kod.</span><span class="sxs-lookup"><span data-stu-id="08eef-217">Try it yourself.</span></span> <span data-ttu-id="08eef-218">Następnie wykonaj go, aby dowiedzieć się, jak Ci poszło.</span><span class="sxs-lookup"><span data-stu-id="08eef-218">Then check how you did.</span></span> <span data-ttu-id="08eef-219">Należy uzyskać 63 na odpowiedź.</span><span class="sxs-lookup"><span data-stu-id="08eef-219">You should get 63 for an answer.</span></span> <span data-ttu-id="08eef-220">Możesz wyświetlić jedną możliwą odpowiedź, [wyświetlając kod ukończony w serwisie GitHub](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54).</span><span class="sxs-lookup"><span data-stu-id="08eef-220">You can see one possible answer by [viewing the completed code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/branches-quickstart/Program.cs#L46-L54).</span></span>

<span data-ttu-id="08eef-221">Samouczek "gałęzie i pętle" został ukończony.</span><span class="sxs-lookup"><span data-stu-id="08eef-221">You've completed the "branches and loops" tutorial.</span></span>

<span data-ttu-id="08eef-222">Możesz kontynuować samouczek dotyczący [tablic i kolekcji](arrays-and-collections.md) w Twoim środowisku programistycznym.</span><span class="sxs-lookup"><span data-stu-id="08eef-222">You can continue with the [Arrays and collections](arrays-and-collections.md) tutorial in your own development environment.</span></span>

<span data-ttu-id="08eef-223">Więcej informacji na temat tych pojęć można znaleźć w następujących artykułach:</span><span class="sxs-lookup"><span data-stu-id="08eef-223">You can learn more about these concepts in these articles:</span></span>

- [<span data-ttu-id="08eef-224">if i else, instrukcje</span><span class="sxs-lookup"><span data-stu-id="08eef-224">If and else statement</span></span>](../../language-reference/keywords/if-else.md)
- [<span data-ttu-id="08eef-225">While, instrukcja</span><span class="sxs-lookup"><span data-stu-id="08eef-225">While statement</span></span>](../../language-reference/keywords/while.md)
- [<span data-ttu-id="08eef-226">do, instrukcja</span><span class="sxs-lookup"><span data-stu-id="08eef-226">Do statement</span></span>](../../language-reference/keywords/do.md)
- [<span data-ttu-id="08eef-227">For — instrukcja</span><span class="sxs-lookup"><span data-stu-id="08eef-227">For statement</span></span>](../../language-reference/keywords/for.md)

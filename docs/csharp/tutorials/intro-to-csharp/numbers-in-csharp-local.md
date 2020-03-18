---
title: Liczby w języku C# — wprowadzenie do samouczka języka C#
description: Dowiedz się C# eksplorując typy liczbowe, ich właściwości i metody.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: 7e9af4b3b859f74d7e92ff10b3964ddd59d2473b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156548"
---
# <a name="manipulate-integral-and-floating-point-numbers-in-c"></a><span data-ttu-id="e7807-103">Manipulowanie liczbami integralnymi i zmiennoprzecinkowymi w C\#</span><span class="sxs-lookup"><span data-stu-id="e7807-103">Manipulate integral and floating point numbers in C\#</span></span>

<span data-ttu-id="e7807-104">Ten samouczek uczy o typach liczbowych w języku C# interaktywnie.</span><span class="sxs-lookup"><span data-stu-id="e7807-104">This tutorial teaches you about the numeric types in C# interactively.</span></span> <span data-ttu-id="e7807-105">Napiszesz niewielkie ilości kodu, a następnie skompiluj i uruchomisz ten kod.</span><span class="sxs-lookup"><span data-stu-id="e7807-105">You'll write small amounts of code, then you'll compile and run that code.</span></span> <span data-ttu-id="e7807-106">Samouczek zawiera serię lekcji, które eksplorują liczby i operacje matematyczne w języku C#.</span><span class="sxs-lookup"><span data-stu-id="e7807-106">The tutorial contains a series of lessons that explore numbers and math operations in C#.</span></span> <span data-ttu-id="e7807-107">Te lekcje umożliwiają poznanie podstaw języka C#.</span><span class="sxs-lookup"><span data-stu-id="e7807-107">These lessons teach you the fundamentals of the C# language.</span></span>

<span data-ttu-id="e7807-108">Ten samouczek oczekuje, że masz komputer, którego można użyć do tworzenia.</span><span class="sxs-lookup"><span data-stu-id="e7807-108">This tutorial expects you to have a machine you can use for development.</span></span> <span data-ttu-id="e7807-109">Samouczek .NET [Hello World w 10 minut](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) zawiera instrukcje dotyczące konfigurowania lokalnego środowiska programistycznego w systemie Windows, Linux lub macOS.</span><span class="sxs-lookup"><span data-stu-id="e7807-109">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span> <span data-ttu-id="e7807-110">Szybki przegląd poleceń, których będziesz używać, znajduje się w [obszarze Zaznajomij się z narzędziami programistycznymi](local-environment.md) z łączami do szczegółowych informacji.</span><span class="sxs-lookup"><span data-stu-id="e7807-110">A quick overview of the commands you'll use is in the [Become familiar with the development tools](local-environment.md) with links to more details.</span></span>

## <a name="explore-integer-math"></a><span data-ttu-id="e7807-111">Poznawanie matematyki całkowitoliczbowej</span><span class="sxs-lookup"><span data-stu-id="e7807-111">Explore integer math</span></span>

<span data-ttu-id="e7807-112">Utwórz katalog o nazwie *numery szybki start*.</span><span class="sxs-lookup"><span data-stu-id="e7807-112">Create a directory named *numbers-quickstart*.</span></span> <span data-ttu-id="e7807-113">Upewnij się, że bieżący katalog i uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="e7807-113">Make that the current directory and run the following command:</span></span>

```dotnetcli
dotnet new console -n NumbersInCSharp -o .
```

<span data-ttu-id="e7807-114">Otwórz *Program.cs* w ulubionym edytorze `Console.WriteLine("Hello World!");` i zastąp wiersz następującymi elementami:</span><span class="sxs-lookup"><span data-stu-id="e7807-114">Open *Program.cs* in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following:</span></span>

```csharp
int a = 18;
int b = 6;
int c = a + b;
Console.WriteLine(c);
```

<span data-ttu-id="e7807-115">Uruchom ten kod, `dotnet run` wpisując w oknie polecenia.</span><span class="sxs-lookup"><span data-stu-id="e7807-115">Run this code by typing `dotnet run` in your command window.</span></span>

<span data-ttu-id="e7807-116">Właśnie została przedstawiona jedna z podstawowych operacji matematycznych na liczbach całkowitych.</span><span class="sxs-lookup"><span data-stu-id="e7807-116">You've just seen one of the fundamental math operations with integers.</span></span> <span data-ttu-id="e7807-117">Typ `int` reprezentuje **liczbę całkowitą**, zero, dodatnią lub ujemną liczbę całkowitą.</span><span class="sxs-lookup"><span data-stu-id="e7807-117">The `int` type represents an **integer**, a zero, positive, or negative whole number.</span></span> <span data-ttu-id="e7807-118">Symbol `+` umożliwia dodawanie.</span><span class="sxs-lookup"><span data-stu-id="e7807-118">You use the `+` symbol for addition.</span></span> <span data-ttu-id="e7807-119">Inne typowe operacje matematyczne na liczbach całkowitych obejmują:</span><span class="sxs-lookup"><span data-stu-id="e7807-119">Other common mathematical operations for integers include:</span></span>

- <span data-ttu-id="e7807-120">odejmowanie — `-`</span><span class="sxs-lookup"><span data-stu-id="e7807-120">`-` for subtraction</span></span>
- <span data-ttu-id="e7807-121">mnożenie — `*`</span><span class="sxs-lookup"><span data-stu-id="e7807-121">`*` for multiplication</span></span>
- <span data-ttu-id="e7807-122">dzielenie — `/`</span><span class="sxs-lookup"><span data-stu-id="e7807-122">`/` for division</span></span>

<span data-ttu-id="e7807-123">Rozpocznij od wypróbowania różnych operacji.</span><span class="sxs-lookup"><span data-stu-id="e7807-123">Start by exploring those different operations.</span></span> <span data-ttu-id="e7807-124">Dodaj te wiersze po wierszu, `c`który zapisuje wartość:</span><span class="sxs-lookup"><span data-stu-id="e7807-124">Add these lines after the line that writes the value of `c`:</span></span>

```csharp

// subtraction
c = a - b;
Console.WriteLine(c);

// multiplication
c = a * b;
Console.WriteLine(c);

// division
c = a / b;
Console.WriteLine(c);
```

<span data-ttu-id="e7807-125">Uruchom ten kod, `dotnet run` wpisując w oknie polecenia.</span><span class="sxs-lookup"><span data-stu-id="e7807-125">Run this code by typing `dotnet run` in your command window.</span></span>

<span data-ttu-id="e7807-126">Jeśli chcesz, możesz także eksperymentować, wykonując wiele operacji matematycznych w jednym wierszu.</span><span class="sxs-lookup"><span data-stu-id="e7807-126">You can also experiment by performing multiple mathematics operations in the same line, if you'd like.</span></span> <span data-ttu-id="e7807-127">Spróbuj `c = a + b - 12 * 17;` na przykład.</span><span class="sxs-lookup"><span data-stu-id="e7807-127">Try `c = a + b - 12 * 17;` for example.</span></span> <span data-ttu-id="e7807-128">Mieszanie zmiennych i stałych liczb jest dozwolone.</span><span class="sxs-lookup"><span data-stu-id="e7807-128">Mixing variables and constant numbers is allowed.</span></span>

> [!TIP]
> <span data-ttu-id="e7807-129">Podczas nauki języka C# (lub dowolnego języka programowania) będziesz robić błędy przy pisaniu kodu.</span><span class="sxs-lookup"><span data-stu-id="e7807-129">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="e7807-130">**Kompilator** znajdzie te błędy i zgłosi je.</span><span class="sxs-lookup"><span data-stu-id="e7807-130">The **compiler** will find those errors and report them to you.</span></span> <span data-ttu-id="e7807-131">Gdy dane wyjściowe zawierają komunikaty o błędach, przyjrzyj się uważnie przykładowemu kodowi i kodowi w oknie, aby zobaczyć, co naprawić.</span><span class="sxs-lookup"><span data-stu-id="e7807-131">When the output contains error messages, look closely at the example code and the code in your window to see what to fix.</span></span>
> <span data-ttu-id="e7807-132">To ćwiczenie pomoże Ci poznać strukturę kodu w języku C#.</span><span class="sxs-lookup"><span data-stu-id="e7807-132">That exercise will help you learn the structure of C# code.</span></span>

<span data-ttu-id="e7807-133">Ukończono pierwszy krok.</span><span class="sxs-lookup"><span data-stu-id="e7807-133">You've finished the first step.</span></span> <span data-ttu-id="e7807-134">Przed rozpoczęciem następnej sekcji przenieśmy bieżący kod do osobnej metody.</span><span class="sxs-lookup"><span data-stu-id="e7807-134">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="e7807-135">Ułatwia to rozpoczęcie pracy z nowym przykładem.</span><span class="sxs-lookup"><span data-stu-id="e7807-135">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="e7807-136">Zmień nazwę `Main` metody `WorkingWithIntegers` i napisz `Main` nową `WorkingWithIntegers`metodę, która wywołuje .</span><span class="sxs-lookup"><span data-stu-id="e7807-136">Rename your `Main` method to `WorkingWithIntegers` and write a new `Main` method that calls `WorkingWithIntegers`.</span></span> <span data-ttu-id="e7807-137">Po zakończeniu kod powinien wyglądać tak:</span><span class="sxs-lookup"><span data-stu-id="e7807-137">When you finish, your code should look like this:</span></span>

```csharp
using System;

namespace NumbersInCSharp
{
    class Program
    {
        static void WorkingWithIntegers()
        {
            int a = 18;
            int b = 6;

            // addition
            int c = a + b;
            Console.WriteLine(c);

            // subtraction
            c = a - b;
            Console.WriteLine(c);

            // multiplication
            c = a * b;
            Console.WriteLine(c);

            // division
            c = a / b;
            Console.WriteLine(c);
        }

        static void Main(string[] args)
        {
            WorkingWithIntegers();
        }
    }
}
```

## <a name="explore-order-of-operations"></a><span data-ttu-id="e7807-138">Poznawanie kolejności operacji</span><span class="sxs-lookup"><span data-stu-id="e7807-138">Explore order of operations</span></span>

<span data-ttu-id="e7807-139">Skomentuj wezwanie `WorkingWithIntegers()`do .</span><span class="sxs-lookup"><span data-stu-id="e7807-139">Comment out the call to `WorkingWithIntegers()`.</span></span> <span data-ttu-id="e7807-140">To sprawi, że dane wyjściowe mniej zaśmiecone podczas pracy w tej sekcji:</span><span class="sxs-lookup"><span data-stu-id="e7807-140">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//WorkingWithIntegers();
```

<span data-ttu-id="e7807-141">Rozpoczyna `//` **komentarz** w języku C#.</span><span class="sxs-lookup"><span data-stu-id="e7807-141">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="e7807-142">Komentarze to dowolny tekst, który chcesz zachować w kodzie źródłowym, ale nie są wykonywane jako kod.</span><span class="sxs-lookup"><span data-stu-id="e7807-142">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="e7807-143">Kompilator nie generuje żadnego kodu wykonywalnego z komentarzy.</span><span class="sxs-lookup"><span data-stu-id="e7807-143">The compiler does not generate any executable code from comments.</span></span>

<span data-ttu-id="e7807-144">Język C# definiuje kolejność wykonywania różnych operacji matematycznych zgodnie z regułami spójnymi z regułami przedstawianymi na lekcjach matematyki.</span><span class="sxs-lookup"><span data-stu-id="e7807-144">The C# language defines the precedence of different mathematics operations with rules consistent with the rules you learned in mathematics.</span></span>
<span data-ttu-id="e7807-145">Mnożenie i dzielenie ma priorytet przed dodawaniem i odejmowaniem.</span><span class="sxs-lookup"><span data-stu-id="e7807-145">Multiplication and division take precedence over addition and subtraction.</span></span>
<span data-ttu-id="e7807-146">Eksploruj to, `Main` dodając następujący `dotnet run`kod do metody i wykonując:</span><span class="sxs-lookup"><span data-stu-id="e7807-146">Explore that by adding the following code to your `Main` method, and executing `dotnet run`:</span></span>

```csharp
int a = 5;
int b = 4;
int c = 2;
int d = a + b * c;
Console.WriteLine(d);
 ```

<span data-ttu-id="e7807-147">Dane wyjściowe świadczą, że mnożenie jest wykonywane przed dodawaniem.</span><span class="sxs-lookup"><span data-stu-id="e7807-147">The output demonstrates that the multiplication is performed before the addition.</span></span>

<span data-ttu-id="e7807-148">Można wymusić inną kolejność operacji, dodając nawiasy wokół operacji lub operacji, które mają być wykonywane jako pierwsze.</span><span class="sxs-lookup"><span data-stu-id="e7807-148">You can force a different order of operation by adding parentheses around the operation or operations you want performed first.</span></span> <span data-ttu-id="e7807-149">Dodaj następujące wiersze i uruchom ponownie:</span><span class="sxs-lookup"><span data-stu-id="e7807-149">Add the following lines and run again:</span></span>

```csharp
d = (a + b) * c;
Console.WriteLine(d);
```

<span data-ttu-id="e7807-150">Dowiedz się więcej, łącząc wiele różnych operacji.</span><span class="sxs-lookup"><span data-stu-id="e7807-150">Explore more by combining many different operations.</span></span> <span data-ttu-id="e7807-151">Dodaj coś takiego jak następujące wiersze na dole metody. `Main`</span><span class="sxs-lookup"><span data-stu-id="e7807-151">Add something like the following lines at the bottom of your `Main` method.</span></span> <span data-ttu-id="e7807-152">Spróbuj ponownie użyć narzędzia `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="e7807-152">Try `dotnet run` again.</span></span>

```csharp
d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
Console.WriteLine(d);
```

<span data-ttu-id="e7807-153">Być może zwróciło Twoją uwagę interesujące zachowanie liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="e7807-153">You may have noticed an interesting behavior for integers.</span></span> <span data-ttu-id="e7807-154">Dzielenie całkowitoliczbowe zawsze daje w wyniku liczbę całkowitą, nawet jeśli oczekiwało się części dziesiętnej lub ułamkowej.</span><span class="sxs-lookup"><span data-stu-id="e7807-154">Integer division always produces an integer result, even when you'd expect the result to include a decimal or fractional portion.</span></span>

<span data-ttu-id="e7807-155">Jeśli nie widzieliście tego zachowania, spróbuj wykonać następujący `Main` kod na końcu metody:</span><span class="sxs-lookup"><span data-stu-id="e7807-155">If you haven't seen this behavior, try the following code at the end of your `Main` method:</span></span>

```csharp
int e = 7;
int f = 4;
int g = 3;
int h = (e + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="e7807-156">Wpisz `dotnet run` ponownie, aby zobaczyć wyniki.</span><span class="sxs-lookup"><span data-stu-id="e7807-156">Type `dotnet run` again to see the results.</span></span>

<span data-ttu-id="e7807-157">Przed przejściem dalej, weźmy cały kod, który został napisany w tej sekcji i umieścić go w nowej metodzie.</span><span class="sxs-lookup"><span data-stu-id="e7807-157">Before moving on, let's take all the code you've written in this section and put it in a new method.</span></span> <span data-ttu-id="e7807-158">Wywołaj tę `OrderPrecedence`nową metodę .</span><span class="sxs-lookup"><span data-stu-id="e7807-158">Call that new method `OrderPrecedence`.</span></span>
<span data-ttu-id="e7807-159">Powinieneś skończyć z czymś takim:</span><span class="sxs-lookup"><span data-stu-id="e7807-159">You should end up with something like this:</span></span>

```csharp
using System;

namespace NumbersInCSharp
{
    class Program
    {
        static void WorkingWithIntegers()
        {
            int a = 18;
            int b = 6;

            // addition
            int c = a + b;
            Console.WriteLine(c);

            // subtraction
            c = a - b;
            Console.WriteLine(c);

            // multiplication
            c = a * b;
            Console.WriteLine(c);

            // division
            c = a / b;
            Console.WriteLine(c);
        }

        static void OrderPrecedence()
        {
            int a = 5;
            int b = 4;
            int c = 2;
            int d = a + b * c;
            Console.WriteLine(d);

            d = (a + b) * c;
            Console.WriteLine(d);

            d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
            Console.WriteLine(d);

            int e = 7;
            int f = 4;
            int g = 3;
            int h = (e  + f) / g;
            Console.WriteLine(h);
        }

        static void Main(string[] args)
        {
            WorkingWithIntegers();

            OrderPrecedence();

        }
    }
}
```

## <a name="explore-integer-precision-and-limits"></a><span data-ttu-id="e7807-160">Poznawanie precyzji i limitów liczb całkowitych</span><span class="sxs-lookup"><span data-stu-id="e7807-160">Explore integer precision and limits</span></span>

<span data-ttu-id="e7807-161">Ostatni przykład pokazuje, że dzielenie całkowitoliczbowe obcina wynik.</span><span class="sxs-lookup"><span data-stu-id="e7807-161">That last sample showed you that integer division truncates the result.</span></span>
<span data-ttu-id="e7807-162">**Resztę** można uzyskać za pomocą operatora **modulo,** `%` znak.</span><span class="sxs-lookup"><span data-stu-id="e7807-162">You can get the **remainder** by using the **modulo** operator, the `%` character.</span></span> <span data-ttu-id="e7807-163">Wypróbuj `Main` następujący kod w metodzie:</span><span class="sxs-lookup"><span data-stu-id="e7807-163">Try the following code in your `Main` method:</span></span>

```csharp
int a = 7;
int b = 4;
int c = 3;
int d = (a + b) / c;
int e = (a + b) % c;
Console.WriteLine($"quotient: {d}");
Console.WriteLine($"remainder: {e}");
```

<span data-ttu-id="e7807-164">Typ całkowitoliczbowy języka C# różni się od matematycznych liczb całkowitych jeszcze tym, że typ `int` ma limit maksimum i minimum.</span><span class="sxs-lookup"><span data-stu-id="e7807-164">The C# integer type differs from mathematical integers in one other way: the `int` type has minimum and maximum limits.</span></span> <span data-ttu-id="e7807-165">Dodaj ten kod `Main` do metody, aby zobaczyć te limity:</span><span class="sxs-lookup"><span data-stu-id="e7807-165">Add this code to your `Main` method to see those limits:</span></span>

```csharp
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");
```

<span data-ttu-id="e7807-166">Jeśli obliczenia generują wartość, która przekracza te limity, występuje warunek **niedopełnienia** lub **przepełnienia**.</span><span class="sxs-lookup"><span data-stu-id="e7807-166">If a calculation produces a value that exceeds those limits, you have an **underflow** or **overflow** condition.</span></span> <span data-ttu-id="e7807-167">Odpowiedź wydaje się zawijać między limitami.</span><span class="sxs-lookup"><span data-stu-id="e7807-167">The answer appears to wrap from one limit to the other.</span></span> <span data-ttu-id="e7807-168">Dodaj te dwa `Main` wiersze do metody, aby zobaczyć przykład:</span><span class="sxs-lookup"><span data-stu-id="e7807-168">Add these two lines to your `Main` method to see an example:</span></span>

```csharp
int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```

<span data-ttu-id="e7807-169">Zwróć uwagę, że odpowiedź jest bardzo zbliżona do minimalnej (ujemnej) liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="e7807-169">Notice that the answer is very close to the minimum (negative) integer.</span></span> <span data-ttu-id="e7807-170">Jej wartość jest równa `min + 2`.</span><span class="sxs-lookup"><span data-stu-id="e7807-170">It's the same as `min + 2`.</span></span>
<span data-ttu-id="e7807-171">Operacja dodawania spowodowała **przepełnienie** wartości dozwolonych dla liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="e7807-171">The addition operation **overflowed** the allowed values for integers.</span></span>
<span data-ttu-id="e7807-172">Odpowiedź to bardzo duża liczba ujemna, ponieważ przepełnienie powoduje „zawinięcie” z największej możliwej liczby całkowitej do najmniejszej.</span><span class="sxs-lookup"><span data-stu-id="e7807-172">The answer is a very large negative number because an overflow "wraps around" from the largest possible integer value to the smallest.</span></span>

<span data-ttu-id="e7807-173">Istnieją inne typy liczbowe z innymi limitami i precyzją, których możesz użyć, jeśli typ `int` nie spełnia wymagań.</span><span class="sxs-lookup"><span data-stu-id="e7807-173">There are other numeric types with different limits and precision that you would use when the `int` type doesn't meet your needs.</span></span> <span data-ttu-id="e7807-174">Zapoznajmy się z nimi w następnej kolejności.</span><span class="sxs-lookup"><span data-stu-id="e7807-174">Let's explore those next.</span></span>

<span data-ttu-id="e7807-175">Po raz kolejny przenieśmy kod, który napisałeś w tej sekcji, do osobnej metody.</span><span class="sxs-lookup"><span data-stu-id="e7807-175">Once again, let's move the code you wrote in this section into a separate method.</span></span> <span data-ttu-id="e7807-176">Nadaj jej nazwę `TestLimits`.</span><span class="sxs-lookup"><span data-stu-id="e7807-176">Name it `TestLimits`.</span></span>

## <a name="work-with-the-double-type"></a><span data-ttu-id="e7807-177">Praca z typem double</span><span class="sxs-lookup"><span data-stu-id="e7807-177">Work with the double type</span></span>

<span data-ttu-id="e7807-178">Typ liczbowy `double` reprezentuje liczbę zmiennoprzecinkową o podwójnej precyzji.</span><span class="sxs-lookup"><span data-stu-id="e7807-178">The `double` numeric type represents a double-precision floating point number.</span></span> <span data-ttu-id="e7807-179">Te pojęcia mogą być dla Ciebie nowe.</span><span class="sxs-lookup"><span data-stu-id="e7807-179">Those terms may be new to you.</span></span> <span data-ttu-id="e7807-180">Liczby **zmiennoprzecinkowe** są przydatne do reprezentowania bardzo małych lub bardzo dużych liczb innych niż liczby całkowite.</span><span class="sxs-lookup"><span data-stu-id="e7807-180">A **floating point** number is useful to represent non-integral numbers that may be very large or small in magnitude.</span></span> <span data-ttu-id="e7807-181">**Podwójna precyzja** oznacza, że liczby są przechowywane z większą dokładnością niż liczby **pojedynczej precyzji**.</span><span class="sxs-lookup"><span data-stu-id="e7807-181">**Double-precision** means that these numbers are stored using greater precision than **single-precision**.</span></span> <span data-ttu-id="e7807-182">W przypadku współczesnych komputerów częściej są używane liczby podwójnej precyzji niż pojedynczej precyzji.</span><span class="sxs-lookup"><span data-stu-id="e7807-182">On modern computers, it is more common to use double precision than single precision numbers.</span></span>
<span data-ttu-id="e7807-183">Przyjrzyjmy się im.</span><span class="sxs-lookup"><span data-stu-id="e7807-183">Let's explore.</span></span> <span data-ttu-id="e7807-184">Dodaj następujący kod i zobacz wynik:</span><span class="sxs-lookup"><span data-stu-id="e7807-184">Add the following code and see the result:</span></span>

```csharp
double a = 5;
double b = 4;
double c = 2;
double d = (a + b) / c;
Console.WriteLine(d);
```

<span data-ttu-id="e7807-185">Zwróć uwagę, że odpowiedź obejmuje część dziesiętną ilorazu.</span><span class="sxs-lookup"><span data-stu-id="e7807-185">Notice that the answer includes the decimal portion of the quotient.</span></span> <span data-ttu-id="e7807-186">Spróbuj nieco bardziej skomplikowanego wyrażenia z liczbami podwójnej precyzji:</span><span class="sxs-lookup"><span data-stu-id="e7807-186">Try a slightly more complicated expression with doubles:</span></span>

```csharp
double e = 19;
double f = 23;
double g = 8;
double h = (e + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="e7807-187">Zakres wartości liczb podwójnej precyzji jest dużo większy niż liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="e7807-187">The range of a double value is much greater than integer values.</span></span> <span data-ttu-id="e7807-188">Wypróbuj poniższy kod, który napisałeś do tej pory:</span><span class="sxs-lookup"><span data-stu-id="e7807-188">Try the following code below what you've written so far:</span></span>

```csharp
double max = double.MaxValue;
double min = double.MinValue;
Console.WriteLine($"The range of double is {min} to {max}");
```

<span data-ttu-id="e7807-189">Wartości zostaną wyświetlone za pomocą notacji naukowej.</span><span class="sxs-lookup"><span data-stu-id="e7807-189">These values are printed out in scientific notation.</span></span> <span data-ttu-id="e7807-190">Liczba po lewej stronie znaku `E` to mantysa.</span><span class="sxs-lookup"><span data-stu-id="e7807-190">The number to the left of the `E` is the significand.</span></span> <span data-ttu-id="e7807-191">Liczba po jego prawej stronie to wykładnik jako potęga 10.</span><span class="sxs-lookup"><span data-stu-id="e7807-191">The number to the right is the exponent, as a power of 10.</span></span>

<span data-ttu-id="e7807-192">Podobnie jak w przypadku liczb dziesiętnych w matematyce, przy używaniu liczb podwójnej precyzji w języku C# mogą wystąpić błędy zaokrąglania.</span><span class="sxs-lookup"><span data-stu-id="e7807-192">Just like decimal numbers in math, doubles in C# can have rounding errors.</span></span> <span data-ttu-id="e7807-193">Wypróbuj ten kod:</span><span class="sxs-lookup"><span data-stu-id="e7807-193">Try this code:</span></span>

```csharp
double third = 1.0 / 3.0;
Console.WriteLine(third);
```

<span data-ttu-id="e7807-194">Wiesz, że ułamek okresowy `0.3` to nie dokładnie to samo co `1/3`.</span><span class="sxs-lookup"><span data-stu-id="e7807-194">You know that `0.3` repeating is not exactly the same as `1/3`.</span></span>

<span data-ttu-id="e7807-195">***Wyzwanie***</span><span class="sxs-lookup"><span data-stu-id="e7807-195">***Challenge***</span></span>

<span data-ttu-id="e7807-196">Spróbuj innych obliczeń z dużymi liczbami, małymi liczbami, mnożeniem i dzieleniem za pomocą typu `double`.</span><span class="sxs-lookup"><span data-stu-id="e7807-196">Try other calculations with large numbers, small numbers, multiplication and division using the `double` type.</span></span> <span data-ttu-id="e7807-197">Spróbuj bardziej skomplikowanych obliczeń.</span><span class="sxs-lookup"><span data-stu-id="e7807-197">Try more complicated calculations.</span></span>

<span data-ttu-id="e7807-198">Po spędzeniu trochę czasu z wyzwaniem, weź kod, który napisałeś i umieść go w nowej metodzie.</span><span class="sxs-lookup"><span data-stu-id="e7807-198">After you've spent some time with the challenge, take the code you've written and place it in a new method.</span></span> <span data-ttu-id="e7807-199">Nazwij `WorkWithDoubles`tę nową metodę .</span><span class="sxs-lookup"><span data-stu-id="e7807-199">Name that new method `WorkWithDoubles`.</span></span>

## <a name="work-with-fixed-point-types"></a><span data-ttu-id="e7807-200">Praca ze stałoprzecinkowymi typami danych</span><span class="sxs-lookup"><span data-stu-id="e7807-200">Work with fixed point types</span></span>

<span data-ttu-id="e7807-201">Przedstawiono podstawowe typy danych liczbowych w języku C#: typ całkowitoliczbowy i typ podwójnej precyzji.</span><span class="sxs-lookup"><span data-stu-id="e7807-201">You've seen the basic numeric types in C#: integers and doubles.</span></span>  <span data-ttu-id="e7807-202">Istnieje jeszcze jeden typ, który należy poznać: typ `decimal`.</span><span class="sxs-lookup"><span data-stu-id="e7807-202">There is one other type to learn: the `decimal` type.</span></span> <span data-ttu-id="e7807-203">Typ `decimal` ma mniejszy zakres, lecz większą precyzję niż typ `double`.</span><span class="sxs-lookup"><span data-stu-id="e7807-203">The `decimal` type has a smaller range but greater precision than `double`.</span></span> <span data-ttu-id="e7807-204">Określenie **stałoprzecinkowy** oznacza, że przecinek dziesiętny (lub binarny) nie zmienia pozycji.</span><span class="sxs-lookup"><span data-stu-id="e7807-204">The term **fixed point** means that the decimal point (or binary point) doesn't move.</span></span> <span data-ttu-id="e7807-205">Spójrzmy:</span><span class="sxs-lookup"><span data-stu-id="e7807-205">Let's take a look:</span></span>

```csharp
decimal min = decimal.MinValue;
decimal max = decimal.MaxValue;
Console.WriteLine($"The range of the decimal type is {min} to {max}");
```

<span data-ttu-id="e7807-206">Zwróć uwagę, że zakres jest mniejszy niż w przypadku typu `double`.</span><span class="sxs-lookup"><span data-stu-id="e7807-206">Notice that the range is smaller than the `double` type.</span></span> <span data-ttu-id="e7807-207">Większą precyzję typu dziesiętnego możesz zobaczyć, uruchamiając następujący kod:</span><span class="sxs-lookup"><span data-stu-id="e7807-207">You can see the greater precision with the decimal type by trying the following code:</span></span>

```csharp
double a = 1.0;
double b = 3.0;
Console.WriteLine(a / b);

decimal c = 1.0M;
decimal d = 3.0M;
Console.WriteLine(c / d);
```

<span data-ttu-id="e7807-208">Sufiks `M` liczb wskazuje, że stałe powinny używać typu `decimal`.</span><span class="sxs-lookup"><span data-stu-id="e7807-208">The `M` suffix on the numbers is how you indicate that a constant should use the `decimal` type.</span></span>

<span data-ttu-id="e7807-209">Zwróć uwagę na to, że operacje matematyczne wykonywane na liczbach typu dziesiętnego mają więcej cyfr po prawej stronie przecinka dziesiętnego.</span><span class="sxs-lookup"><span data-stu-id="e7807-209">Notice that the math using the decimal type has more digits to the right of the decimal point.</span></span>

<span data-ttu-id="e7807-210">***Wyzwanie***</span><span class="sxs-lookup"><span data-stu-id="e7807-210">***Challenge***</span></span>

<span data-ttu-id="e7807-211">Teraz, gdy różne typy liczbowe zostały już przedstawione, napisz kod obliczający pole koła o promieniu 2,5 cm.</span><span class="sxs-lookup"><span data-stu-id="e7807-211">Now that you've seen the different numeric types, write code that calculates the area of a circle whose radius is 2.50 centimeters.</span></span> <span data-ttu-id="e7807-212">Pole koła to promień pomnożony przez liczbę pi do kwadratu.</span><span class="sxs-lookup"><span data-stu-id="e7807-212">Remember that the area of a circle is the radius squared multiplied by PI.</span></span> <span data-ttu-id="e7807-213">Wskazówka: platforma .NET zawiera stałą dla liczby pi — <xref:System.Math.PI?displayProperty=nameWithType> — której możesz użyć.</span><span class="sxs-lookup"><span data-stu-id="e7807-213">One hint: .NET contains a constant for PI, <xref:System.Math.PI?displayProperty=nameWithType> that you can use for that value.</span></span>

<span data-ttu-id="e7807-214">Odpowiedź powinna należeć do zakresu 19-20.</span><span class="sxs-lookup"><span data-stu-id="e7807-214">You should get an answer between 19 and 20.</span></span>
<span data-ttu-id="e7807-215">Możesz sprawdzić swoją odpowiedź, [patrząc na gotowy przykładowy kod w witrynie GitHub](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106).</span><span class="sxs-lookup"><span data-stu-id="e7807-215">You can check your answer by [looking at the finished sample code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106).</span></span>

<span data-ttu-id="e7807-216">Wypróbuj także inne wzory, jeśli chcesz.</span><span class="sxs-lookup"><span data-stu-id="e7807-216">Try some other formulas if you'd like.</span></span>

<span data-ttu-id="e7807-217">Przewodnik szybki start "Liczby w języku C#".</span><span class="sxs-lookup"><span data-stu-id="e7807-217">You've completed the "Numbers in C#" quickstart.</span></span> <span data-ttu-id="e7807-218">Można kontynuować [z gałęzi e-start i pętli](branches-and-loops-local.md) we własnym środowisku programistycznym.</span><span class="sxs-lookup"><span data-stu-id="e7807-218">You can continue with the [Branches and loops](branches-and-loops-local.md) quickstart in your own development environment.</span></span>

<span data-ttu-id="e7807-219">Następujące tematy zawierają więcej informacji na temat liczb w języku C#:</span><span class="sxs-lookup"><span data-stu-id="e7807-219">You can learn more about numbers in C# in the following topics:</span></span>

- [<span data-ttu-id="e7807-220">Typy liczb całkowitych</span><span class="sxs-lookup"><span data-stu-id="e7807-220">Integral numeric types</span></span>](../../language-reference/builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="e7807-221">Zmiennoprzecinkowe rodzaje wartości numerycznych</span><span class="sxs-lookup"><span data-stu-id="e7807-221">Floating-point numeric types</span></span>](../../language-reference/builtin-types/floating-point-numeric-types.md)
- [<span data-ttu-id="e7807-222">Wbudowane konwersje liczbowe</span><span class="sxs-lookup"><span data-stu-id="e7807-222">Built-in numeric conversions</span></span>](../../language-reference/builtin-types/numeric-conversions.md)

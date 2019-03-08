---
title: Liczby w elemencie C# — wprowadzenie do C# samouczek
description: Dowiedz się, C# eksplorując typy liczbowe, ich właściwości i metody.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: 1b09a65b42395bfa1caf9e564120d3df1f3f1ed5
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/08/2019
ms.locfileid: "57673863"
---
# <a name="manipulate-integral-and-floating-point-numbers-in-c"></a><span data-ttu-id="d94c8-103">Manipulowanie liczb całkowitych i zmiennoprzecinkowych w języku C\#</span><span class="sxs-lookup"><span data-stu-id="d94c8-103">Manipulate integral and floating point numbers in C\#</span></span>

<span data-ttu-id="d94c8-104">Ten samouczek zawiera informacje na temat typów liczbowych w C# interaktywnie.</span><span class="sxs-lookup"><span data-stu-id="d94c8-104">This tutorial teaches you about the numeric types in C# interactively.</span></span> <span data-ttu-id="d94c8-105">Napiszesz niewielką ilość kodu, a następnie będzie skompilować i uruchomić ten kod.</span><span class="sxs-lookup"><span data-stu-id="d94c8-105">You'll write small amounts of code, then you'll compile and run that code.</span></span> <span data-ttu-id="d94c8-106">Samouczek zawiera serię lekcji dotyczących liczb i operacji matematycznych w C#.</span><span class="sxs-lookup"><span data-stu-id="d94c8-106">The tutorial contains a series of lessons that explore numbers and math operations in C#.</span></span> <span data-ttu-id="d94c8-107">Te lekcje umożliwiają poznanie podstaw języka C#.</span><span class="sxs-lookup"><span data-stu-id="d94c8-107">These lessons teach you the fundamentals of the C# language.</span></span>

<span data-ttu-id="d94c8-108">W tym samouczku oczekuje, że będziesz mieć maszyny, których można użyć do tworzenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d94c8-108">This tutorial expects you to have a machine you can use for development.</span></span> <span data-ttu-id="d94c8-109">Temat .NET [rozpocząć pracę w ciągu 10 minut](https://www.microsoft.com/net/core) zawiera instrukcje dotyczące konfigurowania swojego lokalnego środowiska deweloperskiego na komputerze Mac, PC lub Linux.</span><span class="sxs-lookup"><span data-stu-id="d94c8-109">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="d94c8-110">Krótkie omówienie poleceń użyjesz znajduje się w [zapoznanie się z narzędziami programistycznymi](local-environment.md) wraz z łączami, aby uzyskać więcej szczegółów.</span><span class="sxs-lookup"><span data-stu-id="d94c8-110">A quick overview of the commands you'll use is in the [Become familiar with the development tools](local-environment.md) with links to more details.</span></span>

## <a name="explore-integer-math"></a><span data-ttu-id="d94c8-111">Poznawanie matematyki całkowitoliczbowej</span><span class="sxs-lookup"><span data-stu-id="d94c8-111">Explore integer math</span></span>

<span data-ttu-id="d94c8-112">Utwórz katalog o nazwie **numery — Szybki Start**.</span><span class="sxs-lookup"><span data-stu-id="d94c8-112">Create a directory named **numbers-quickstart**.</span></span> <span data-ttu-id="d94c8-113">Upewnij, że bieżącego katalogu i uruchom `dotnet new console -n NumbersInCSharp -o .`.</span><span class="sxs-lookup"><span data-stu-id="d94c8-113">Make that the current directory and run `dotnet new console -n NumbersInCSharp -o .`.</span></span>

<span data-ttu-id="d94c8-114">Otwórz **Program.cs** w ulubionym edytorze i Zastąp wiersz `Console.WriteLine("Hello World!");` następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="d94c8-114">Open **Program.cs** in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following:</span></span>

```csharp
int a = 18;
int b = 6;
int c = a + b;
Console.WriteLine(c);
```

<span data-ttu-id="d94c8-115">Uruchom ten kod, wpisując `dotnet run` w oknie polecenia.</span><span class="sxs-lookup"><span data-stu-id="d94c8-115">Run this code by typing `dotnet run` in your command window.</span></span>

<span data-ttu-id="d94c8-116">Po prostu przedstawiono jedną z podstawowych operacji matematycznych na liczbach całkowitych.</span><span class="sxs-lookup"><span data-stu-id="d94c8-116">You've just seen one of the fundamental math operations with integers.</span></span> <span data-ttu-id="d94c8-117">`int` Wpisz reprezentuje **całkowitą**, dodatnią lub ujemną liczbę całkowitą.</span><span class="sxs-lookup"><span data-stu-id="d94c8-117">The `int` type represents an **integer**, a positive or negative whole number.</span></span> <span data-ttu-id="d94c8-118">Możesz użyć `+` symbol do dodania.</span><span class="sxs-lookup"><span data-stu-id="d94c8-118">You use the `+` symbol for addition.</span></span> <span data-ttu-id="d94c8-119">Inne typowe operacje matematyczne dla liczb całkowitych obejmują:</span><span class="sxs-lookup"><span data-stu-id="d94c8-119">Other common mathematical operations for integers include:</span></span>

- <span data-ttu-id="d94c8-120">`-` odejmowanie</span><span class="sxs-lookup"><span data-stu-id="d94c8-120">`-` for subtraction</span></span>
- <span data-ttu-id="d94c8-121">`*` mnożenie</span><span class="sxs-lookup"><span data-stu-id="d94c8-121">`*` for multiplication</span></span>
- <span data-ttu-id="d94c8-122">`/` dzielenie</span><span class="sxs-lookup"><span data-stu-id="d94c8-122">`/` for division</span></span>

<span data-ttu-id="d94c8-123">Rozpocznij od wypróbowania różnych operacji.</span><span class="sxs-lookup"><span data-stu-id="d94c8-123">Start by exploring those different operations.</span></span> <span data-ttu-id="d94c8-124">Dodaj następujące wiersze po wierszu, który zapisuje wartość `c`:</span><span class="sxs-lookup"><span data-stu-id="d94c8-124">Add these lines after the line that writes the value of `c`:</span></span>

```csharp
c = a - b;
Console.WriteLine(c);
c = a * b;
Console.WriteLine(c);
c = a / b;
Console.WriteLine(c);
```

<span data-ttu-id="d94c8-125">Uruchom ten kod, wpisując `dotnet run` w oknie polecenia.</span><span class="sxs-lookup"><span data-stu-id="d94c8-125">Run this code by typing `dotnet run` in your command window.</span></span>

<span data-ttu-id="d94c8-126">Możesz także eksperymentować, wykonując wiele operacji matematycznych w jednym wierszu, jeśli chcesz.</span><span class="sxs-lookup"><span data-stu-id="d94c8-126">You can also experiment by performing multiple mathematics operations in the same line, if you'd like.</span></span> <span data-ttu-id="d94c8-127">Spróbuj `c = a + b - 12 * 17;` na przykład.</span><span class="sxs-lookup"><span data-stu-id="d94c8-127">Try `c = a + b - 12 * 17;` for example.</span></span> <span data-ttu-id="d94c8-128">Mieszanie zmiennych i stałych liczb jest dozwolone.</span><span class="sxs-lookup"><span data-stu-id="d94c8-128">Mixing variables and constant numbers is allowed.</span></span>

> [!TIP]
> <span data-ttu-id="d94c8-129">Gdy eksplorujesz C# (lub dowolnego języka programowania), będziesz robić błędy podczas pisania kodu.</span><span class="sxs-lookup"><span data-stu-id="d94c8-129">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="d94c8-130">**Kompilatora** znajdzie te błędy i zgłosi je.</span><span class="sxs-lookup"><span data-stu-id="d94c8-130">The **compiler** will find those errors and report them to you.</span></span> <span data-ttu-id="d94c8-131">Gdy dane wyjściowe zawierają komunikaty o błędach, Przyjrzyj się blisko przykładowy kod i kod w oknie w taki sposób, aby zobaczyć, co należy naprawić.</span><span class="sxs-lookup"><span data-stu-id="d94c8-131">When the output contains error messages, look closely at the example code and the code in your window to see what to fix.</span></span>
> <span data-ttu-id="d94c8-132">To ćwiczenie pomoże Ci poznać strukturę kodu C#.</span><span class="sxs-lookup"><span data-stu-id="d94c8-132">That exercise will help you learn the structure of C# code.</span></span>

<span data-ttu-id="d94c8-133">Pierwszym krokiem zostały ukończone.</span><span class="sxs-lookup"><span data-stu-id="d94c8-133">You've finished the first step.</span></span> <span data-ttu-id="d94c8-134">Przed rozpoczęciem następnej sekcji, Przejdźmy bieżącego kodu w oddzielnych metodach.</span><span class="sxs-lookup"><span data-stu-id="d94c8-134">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="d94c8-135">Który sprawia, że łatwiej rozpocząć pracę z nową przykładową.</span><span class="sxs-lookup"><span data-stu-id="d94c8-135">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="d94c8-136">Zmiana nazwy Twojego `Main` metodę, aby `WorkingWithIntegers` i zapisywać nowy `Main` metodę, która wywołuje `WorkingWithIntegers`.</span><span class="sxs-lookup"><span data-stu-id="d94c8-136">Rename your `Main` method to `WorkingWithIntegers` and write a new `Main` method that calls `WorkingWithIntegers`.</span></span> <span data-ttu-id="d94c8-137">Po zakończeniu, kod powinien wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="d94c8-137">When you have finished, your code should look like this:</span></span>

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
            int c = a + b;
            Console.WriteLine(c);
            c = a - b;
            Console.WriteLine(c);
            c = a * b;
            Console.WriteLine(c);
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

## <a name="explore-order-of-operations"></a><span data-ttu-id="d94c8-138">Poznawanie kolejności operacji</span><span class="sxs-lookup"><span data-stu-id="d94c8-138">Explore order of operations</span></span>

<span data-ttu-id="d94c8-139">Komentarz wywołanie `WorkingWithIntegers()`.</span><span class="sxs-lookup"><span data-stu-id="d94c8-139">Comment out the call to `WorkingWithIntegers()`.</span></span> <span data-ttu-id="d94c8-140">Spowoduje to, że dane wyjściowe, które mniej "zatłoczony" podczas pracy w tej sekcji:</span><span class="sxs-lookup"><span data-stu-id="d94c8-140">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//WorkingWithIntegers();
```

<span data-ttu-id="d94c8-141">`//` Uruchamia **komentarz** w C#.</span><span class="sxs-lookup"><span data-stu-id="d94c8-141">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="d94c8-142">Komentarze są dowolny tekst, który chcesz zachować w kodzie źródłowym, ale nie jest wykonywane jako kod.</span><span class="sxs-lookup"><span data-stu-id="d94c8-142">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="d94c8-143">Kompilator nie generuje żadnego kodu wykonywalnego z komentarzy.</span><span class="sxs-lookup"><span data-stu-id="d94c8-143">The compiler does not generate any executable code from comments.</span></span>

<span data-ttu-id="d94c8-144">W języku C# definiuje kolejność wykonywania różnych operacji matematycznych zgodnie z regułami spójnymi z regułami przedstawianymi na lekcjach matematyki.</span><span class="sxs-lookup"><span data-stu-id="d94c8-144">The C# language defines the precedence of different mathematics operations with rules consistent with the rules you learned in mathematics.</span></span>
<span data-ttu-id="d94c8-145">Mnożenie i dzielenie pierwszeństwo dodawania i odejmowania.</span><span class="sxs-lookup"><span data-stu-id="d94c8-145">Multiplication and division take precedence over addition and subtraction.</span></span>
<span data-ttu-id="d94c8-146">Zaobserwuj to, dodając następujący kod, aby Twoje `Main` metody i wykonywania `dotnet run`:</span><span class="sxs-lookup"><span data-stu-id="d94c8-146">Explore that by adding the following code to your `Main` method, and executing `dotnet run`:</span></span>

```csharp
int a = 5;
int b = 4;
int c = 2;
int d = a + b * c;
Console.WriteLine(d);
 ```

<span data-ttu-id="d94c8-147">Dane wyjściowe pokazuje, że mnożenie jest wykonywane przed dodawaniem.</span><span class="sxs-lookup"><span data-stu-id="d94c8-147">The output demonstrates that the multiplication is performed before the addition.</span></span>

<span data-ttu-id="d94c8-148">Operacje, które chcesz przeprowadzić najpierw lub inną kolejność operacji można wymusić, dodając nawiasy wokół operacji.</span><span class="sxs-lookup"><span data-stu-id="d94c8-148">You can force a different order of operation by adding parentheses around the operation or operations you want performed first.</span></span> <span data-ttu-id="d94c8-149">Dodaj następujące wiersze, a następnie ponownie uruchom:</span><span class="sxs-lookup"><span data-stu-id="d94c8-149">Add the following lines and run again:</span></span>

```csharp
d = (a  + b) * c;
Console.WriteLine(d);
```

<span data-ttu-id="d94c8-150">Dowiedz się więcej, łącząc wiele różnych operacji.</span><span class="sxs-lookup"><span data-stu-id="d94c8-150">Explore more by combining many different operations.</span></span> <span data-ttu-id="d94c8-151">Dodaj coś następujące wiersze na końcu Twojej `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="d94c8-151">Add something like the following lines at the bottom of your `Main` method.</span></span> <span data-ttu-id="d94c8-152">Spróbuj `dotnet run` ponownie.</span><span class="sxs-lookup"><span data-stu-id="d94c8-152">Try `dotnet run` again.</span></span>

```csharp
d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
Console.WriteLine(d);
```

<span data-ttu-id="d94c8-153">Być może zauważono, interesujące zachowanie liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="d94c8-153">You may have noticed an interesting behavior for integers.</span></span> <span data-ttu-id="d94c8-154">Dzielenie całkowitoliczbowe zawsze daje wyniku liczby całkowitej, nawet wtedy, gdy oczekiwany wynik, który ma zawierać części dziesiętnej lub ułamkowej.</span><span class="sxs-lookup"><span data-stu-id="d94c8-154">Integer division always produces an integer result, even when you'd expect the result to include a decimal or fractional portion.</span></span>

<span data-ttu-id="d94c8-155">Jeśli nie dostrzegasz tego zachowania, wypróbuj następujący kod na końcu Twojej `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="d94c8-155">If you haven't seen this behavior, try the following code at the end of your `Main` method:</span></span>

```csharp
int e = 7;
int f = 4;
int g = 3;
int h = (e  + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="d94c8-156">Typ `dotnet run` ponownie, aby zobaczyć wyniki.</span><span class="sxs-lookup"><span data-stu-id="d94c8-156">Type `dotnet run` again to see the results.</span></span>

<span data-ttu-id="d94c8-157">Przed kontynuowaniem, Przyjrzyjmy się cały kod został napisany w tej sekcji i umieścić go w nowej metody.</span><span class="sxs-lookup"><span data-stu-id="d94c8-157">Before moving on, let's take all the code you've written in this section and put it in a new method.</span></span> <span data-ttu-id="d94c8-158">Wywołanie tej nowej metody `OrderPrecedence`.</span><span class="sxs-lookup"><span data-stu-id="d94c8-158">Call that new method `OrderPrecedence`.</span></span>
<span data-ttu-id="d94c8-159">Użytkownik powinien kończyć podobny do poniższego:</span><span class="sxs-lookup"><span data-stu-id="d94c8-159">You should end up with something like this:</span></span>

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
            int c = a + b;
            Console.WriteLine(c);
            c = a - b;
            Console.WriteLine(c);
            c = a * b;
            Console.WriteLine(c);
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

            d = (a  + b) * c;
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

## <a name="explore-integer-precision-and-limits"></a><span data-ttu-id="d94c8-160">Zapoznaj się z liczbą całkowitą precyzji i limitów</span><span class="sxs-lookup"><span data-stu-id="d94c8-160">Explore integer precision and limits</span></span>

<span data-ttu-id="d94c8-161">Ostatni przykład pokazuje, że dzielenie całkowitoliczbowe obcina wynik.</span><span class="sxs-lookup"><span data-stu-id="d94c8-161">That last sample showed you that integer division truncates the result.</span></span>
<span data-ttu-id="d94c8-162">Możesz uzyskać **resztę** przy użyciu **modulo** operatora `%` znaków.</span><span class="sxs-lookup"><span data-stu-id="d94c8-162">You can get the **remainder** by using the **modulo** operator, the `%` character.</span></span> <span data-ttu-id="d94c8-163">Wypróbuj poniższy kod w swojej `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="d94c8-163">Try the following code in your `Main` method:</span></span>

```csharp
int a = 7;
int b = 4;
int c = 3;
int d = (a  + b) / c;
int e = (a + b) % c;
Console.WriteLine($"quotient: {d}");
Console.WriteLine($"remainder: {e}");
```

<span data-ttu-id="d94c8-164">Typ liczby całkowitej C# różni się od matematycznych liczb całkowitych w inny sposób: `int` typ ma limit maksimum i minimum.</span><span class="sxs-lookup"><span data-stu-id="d94c8-164">The C# integer type differs from mathematical integers in one other way: the `int` type has minimum and maximum limits.</span></span> <span data-ttu-id="d94c8-165">Dodaj następujący kod do Twojego `Main` metodę, aby zobaczyć te limity:</span><span class="sxs-lookup"><span data-stu-id="d94c8-165">Add this code to your `Main` method to see those limits:</span></span>

```csharp
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");
```

<span data-ttu-id="d94c8-166">Jeśli obliczenia generują wartość, która przekracza te limity, masz **niedopełnienie** lub **przepełnienie** warunku.</span><span class="sxs-lookup"><span data-stu-id="d94c8-166">If a calculation produces a value that exceeds those limits, you have an **underflow** or **overflow** condition.</span></span> <span data-ttu-id="d94c8-167">Odpowiedź wydaje się zawijać między do drugiego.</span><span class="sxs-lookup"><span data-stu-id="d94c8-167">The answer appears to wrap from one limit to the other.</span></span> <span data-ttu-id="d94c8-168">Dodaj następujące dwa wiersze do Twojej `Main` metodę, aby zobaczyć przykład:</span><span class="sxs-lookup"><span data-stu-id="d94c8-168">Add these two lines to your `Main` method to see an example:</span></span>

```csharp
int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```

<span data-ttu-id="d94c8-169">Należy zauważyć, że odpowiedź jest bardzo zbliżona minimalnej (ujemnej) liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="d94c8-169">Notice that the answer is very close to the minimum (negative) integer.</span></span> <span data-ttu-id="d94c8-170">Jest taka sama jak `min + 2`.</span><span class="sxs-lookup"><span data-stu-id="d94c8-170">It's the same as `min + 2`.</span></span>
<span data-ttu-id="d94c8-171">Operacja dodawania **przepełnienie** dozwolone wartości liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="d94c8-171">The addition operation **overflowed** the allowed values for integers.</span></span>
<span data-ttu-id="d94c8-172">Odpowiedzią jest bardzo duża liczba ujemna, ponieważ przepełnienie "zawinięcie" z największej możliwej liczby całkowitej do najmniejszej.</span><span class="sxs-lookup"><span data-stu-id="d94c8-172">The answer is a very large negative number because an overflow "wraps around" from the largest possible integer value to the smallest.</span></span>

<span data-ttu-id="d94c8-173">Istnieją inne typy liczbowe z innymi limitami i precyzją, których możesz użyć, gdy `int` typu nie odpowiada Twoim potrzebom.</span><span class="sxs-lookup"><span data-stu-id="d94c8-173">There are other numeric types with different limits and precision that you would use when the `int` type doesn't meet your needs.</span></span> <span data-ttu-id="d94c8-174">Przyjrzyjmy się nimi w następnej kolejności.</span><span class="sxs-lookup"><span data-stu-id="d94c8-174">Let's explore those next.</span></span>

<span data-ttu-id="d94c8-175">Jeszcze raz Przejdźmy kod, który napisał w tej sekcji w oddzielnych metodach.</span><span class="sxs-lookup"><span data-stu-id="d94c8-175">Once again, let's move the code you wrote in this section into a separate method.</span></span> <span data-ttu-id="d94c8-176">Nadaj mu nazwę `TestLimits`.</span><span class="sxs-lookup"><span data-stu-id="d94c8-176">Name it `TestLimits`.</span></span>

## <a name="work-with-the-double-type"></a><span data-ttu-id="d94c8-177">Praca z typem double</span><span class="sxs-lookup"><span data-stu-id="d94c8-177">Work with the double type</span></span>

<span data-ttu-id="d94c8-178">`double` Typu numerycznego reprezentuje liczbę zmiennoprzecinkową podwójnej precyzji.</span><span class="sxs-lookup"><span data-stu-id="d94c8-178">The `double` numeric type represents a double-precision floating point number.</span></span> <span data-ttu-id="d94c8-179">Te pojęcia mogą być dla Ciebie nowe.</span><span class="sxs-lookup"><span data-stu-id="d94c8-179">Those terms may be new to you.</span></span> <span data-ttu-id="d94c8-180">A **zmiennoprzecinkowa** numer jest przydatne do reprezentowania liczb niecałkowitoliczbowego, które mogą być bardzo małych lub dużych.</span><span class="sxs-lookup"><span data-stu-id="d94c8-180">A **floating point** number is useful to represent non-integral numbers that may be very large or small in magnitude.</span></span> <span data-ttu-id="d94c8-181">**Podwójnej precyzji** oznacza, że te liczby są przechowywane z większą dokładnością niż **pojedynczej precyzji**.</span><span class="sxs-lookup"><span data-stu-id="d94c8-181">**Double-precision** means that these numbers are stored using greater precision than **single-precision**.</span></span> <span data-ttu-id="d94c8-182">W przypadku współczesnych komputerów jest bardziej powszechne, aby użyć podwójnej precyzji niż pojedynczej precyzji liczb.</span><span class="sxs-lookup"><span data-stu-id="d94c8-182">On modern computers, it is more common to use double precision than single precision numbers.</span></span>
<span data-ttu-id="d94c8-183">Przyjrzyjmy się.</span><span class="sxs-lookup"><span data-stu-id="d94c8-183">Let's explore.</span></span> <span data-ttu-id="d94c8-184">Dodaj następujący kod i zobacz wynik:</span><span class="sxs-lookup"><span data-stu-id="d94c8-184">Add the following code and see the result:</span></span>

```csharp
double a = 5;
double b = 4;
double c = 2;
double d = (a  + b) / c;
Console.WriteLine(d);
```

<span data-ttu-id="d94c8-185">Należy zauważyć, że odpowiedź obejmuje część dziesiętną ilorazu.</span><span class="sxs-lookup"><span data-stu-id="d94c8-185">Notice that the answer includes the decimal portion of the quotient.</span></span> <span data-ttu-id="d94c8-186">Spróbuj nieco bardziej skomplikowanego wyrażenia z liczbami podwójnej precyzji:</span><span class="sxs-lookup"><span data-stu-id="d94c8-186">Try a slightly more complicated expression with doubles:</span></span>

```csharp
double e = 19;
double f = 23;
double g = 8;
double h = (e  + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="d94c8-187">Zakres liczb podwójnej precyzji jest dużo większy niż liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="d94c8-187">The range of a double value is much greater than integer values.</span></span> <span data-ttu-id="d94c8-188">Wypróbuj poniższy kod poniżej co napisanych do tej pory:</span><span class="sxs-lookup"><span data-stu-id="d94c8-188">Try the following code below what you've written so far:</span></span>

```csharp
double max = double.MaxValue;
double min = double.MinValue;
Console.WriteLine($"The range of double is {min} to {max}");
```

<span data-ttu-id="d94c8-189">Te wartości są drukowane w notacji naukowej.</span><span class="sxs-lookup"><span data-stu-id="d94c8-189">These values are printed out in scientific notation.</span></span> <span data-ttu-id="d94c8-190">Liczba po lewej stronie `E` to mantysa.</span><span class="sxs-lookup"><span data-stu-id="d94c8-190">The number to the left of the `E` is the significand.</span></span> <span data-ttu-id="d94c8-191">Liczba po prawej stronie to wykładnik jako potęga 10.</span><span class="sxs-lookup"><span data-stu-id="d94c8-191">The number to the right is the exponent, as a power of 10.</span></span>

<span data-ttu-id="d94c8-192">Podobnie jak liczb dziesiętnych w matematyce wartości podwójnej precyzji w języku C# mogą wystąpić błędy zaokrąglania.</span><span class="sxs-lookup"><span data-stu-id="d94c8-192">Just like decimal numbers in math, doubles in C# can have rounding errors.</span></span> <span data-ttu-id="d94c8-193">Wypróbuj ten kod:</span><span class="sxs-lookup"><span data-stu-id="d94c8-193">Try this code:</span></span>

```csharp
double third = 1.0 / 3.0;
Console.WriteLine(third);
```

<span data-ttu-id="d94c8-194">Należy pamiętać, że `0.3` powtarzanie nie jest dokładnie taka sama jak `1/3`.</span><span class="sxs-lookup"><span data-stu-id="d94c8-194">You know that `0.3` repeating is not exactly the same as `1/3`.</span></span>

<span data-ttu-id="d94c8-195">***Challenge***</span><span class="sxs-lookup"><span data-stu-id="d94c8-195">***Challenge***</span></span>

<span data-ttu-id="d94c8-196">Spróbuj innych obliczeń z dużą liczbą, małymi liczbami, mnożeniem i dzieleniem za pomocą `double` typu.</span><span class="sxs-lookup"><span data-stu-id="d94c8-196">Try other calculations with large numbers, small numbers, multiplication and division using the `double` type.</span></span>  <span data-ttu-id="d94c8-197">Spróbuj bardziej skomplikowanych obliczeń.</span><span class="sxs-lookup"><span data-stu-id="d94c8-197">Try more complicated calculations.</span></span>

<span data-ttu-id="d94c8-198">Po przez pewien czas z żądaniem zająć kodu zostały zapisane i umieść go w nowej metody.</span><span class="sxs-lookup"><span data-stu-id="d94c8-198">After you've spent some time with the challenge, take the code you've written and place it in a new method.</span></span> <span data-ttu-id="d94c8-199">Nazwa tej nowej metody `WorkWithDoubles`.</span><span class="sxs-lookup"><span data-stu-id="d94c8-199">Name that new method `WorkWithDoubles`.</span></span>

## <a name="work-with-fixed-point-types"></a><span data-ttu-id="d94c8-200">Praca ze stałoprzecinkowymi typami</span><span class="sxs-lookup"><span data-stu-id="d94c8-200">Work with fixed point types</span></span>

<span data-ttu-id="d94c8-201">W tym samouczku podstawowe typy danych liczbowych w języku C#: liczby całkowite i typ podwójnej precyzji.</span><span class="sxs-lookup"><span data-stu-id="d94c8-201">You've seen the basic numeric types in C#: integers and doubles.</span></span>  <span data-ttu-id="d94c8-202">Istnieje jeszcze jeden typ, aby dowiedzieć się więcej: `decimal` typu.</span><span class="sxs-lookup"><span data-stu-id="d94c8-202">There is one other type to learn: the `decimal` type.</span></span> <span data-ttu-id="d94c8-203">`decimal` Typ ma mniejszy zakres, lecz większą precyzję niż `double`.</span><span class="sxs-lookup"><span data-stu-id="d94c8-203">The `decimal` type has a smaller range but greater precision than `double`.</span></span> <span data-ttu-id="d94c8-204">Termin **Stałoprzecinkowy** oznacza, że punkt dziesiętny (lub binarny) nie jest przenoszony.</span><span class="sxs-lookup"><span data-stu-id="d94c8-204">The term **fixed point** means that the decimal point (or binary point) doesn't move.</span></span> <span data-ttu-id="d94c8-205">Przyjrzyjmy się:</span><span class="sxs-lookup"><span data-stu-id="d94c8-205">Let's take a look:</span></span>

```csharp
decimal min = decimal.MinValue;
decimal max = decimal.MaxValue;
Console.WriteLine($"The range of the decimal type is {min} to {max}");
```

<span data-ttu-id="d94c8-206">Należy zauważyć, że zakres jest mniejszy niż `double` typu.</span><span class="sxs-lookup"><span data-stu-id="d94c8-206">Notice that the range is smaller than the `double` type.</span></span> <span data-ttu-id="d94c8-207">Możesz zobaczyć większą precyzję typu dziesiętnego, wykonując następujący kod:</span><span class="sxs-lookup"><span data-stu-id="d94c8-207">You can see the greater precision with the decimal type by trying the following code:</span></span>

```csharp
double a = 1.0;
double b = 3.0;
Console.WriteLine(a / b);

decimal c = 1.0M;
decimal d = 3.0M;
Console.WriteLine(c / d);
```

<span data-ttu-id="d94c8-208">`M` Sufiks liczby jest wskazuje, że stałe powinny używać `decimal` typu.</span><span class="sxs-lookup"><span data-stu-id="d94c8-208">The `M` suffix on the numbers is how you indicate that a constant should use the `decimal` type.</span></span>

<span data-ttu-id="d94c8-209">Należy zauważyć, że matematyczne liczbach typu dziesiętnego ma więcej cyfr po prawej stronie przecinka dziesiętnego.</span><span class="sxs-lookup"><span data-stu-id="d94c8-209">Notice that the math using the decimal type has more digits to the right of the decimal point.</span></span>

<span data-ttu-id="d94c8-210">***Challenge***</span><span class="sxs-lookup"><span data-stu-id="d94c8-210">***Challenge***</span></span>

<span data-ttu-id="d94c8-211">Teraz, gdy różne typy liczbowe, należy napisać kod obliczający pole koła o promieniu jest kosztuje 2,50 cm.</span><span class="sxs-lookup"><span data-stu-id="d94c8-211">Now that you've seen the different numeric types, write code that calculates the area of a circle whose radius is 2.50 centimeters.</span></span> <span data-ttu-id="d94c8-212">Należy pamiętać, że pole koła to promień pomnożony pomnożonej przez PI.</span><span class="sxs-lookup"><span data-stu-id="d94c8-212">Remember that the area of a circle is the radius squared multiplied by PI.</span></span> <span data-ttu-id="d94c8-213">Wskazówka: platforma .NET zawiera stałą dla liczby PI — <xref:System.Math.PI?displayProperty=nameWithType> używanego dla tej wartości.</span><span class="sxs-lookup"><span data-stu-id="d94c8-213">One hint: .NET contains a constant for PI, <xref:System.Math.PI?displayProperty=nameWithType> that you can use for that value.</span></span>

<span data-ttu-id="d94c8-214">Powinna pojawić się odpowiedź zakresu 19-20.</span><span class="sxs-lookup"><span data-stu-id="d94c8-214">You should get an answer between 19 and 20.</span></span>
<span data-ttu-id="d94c8-215">Możesz sprawdzić odpowiedzi przez [spojrzenie na Zakończono przykładowego kodu w serwisie GitHub](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106)</span><span class="sxs-lookup"><span data-stu-id="d94c8-215">You can check your answer by [looking at the finished sample code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106)</span></span>

<span data-ttu-id="d94c8-216">Wypróbuj także inne wzory, jeśli chcesz.</span><span class="sxs-lookup"><span data-stu-id="d94c8-216">Try some other formulas if you'd like.</span></span>

<span data-ttu-id="d94c8-217">Ukończono "liczby w elemencie C#" Szybki Start.</span><span class="sxs-lookup"><span data-stu-id="d94c8-217">You've completed the "Numbers in C#" quickstart.</span></span> <span data-ttu-id="d94c8-218">Możesz kontynuować [gałęzie i pętle](branches-and-loops-local.md) Szybki Start w środowisku projektowym.</span><span class="sxs-lookup"><span data-stu-id="d94c8-218">You can continue with the [Branches and loops](branches-and-loops-local.md) quickstart in your own development environment.</span></span>

<span data-ttu-id="d94c8-219">Możesz dowiedzieć się więcej na temat liczb w języku C# w następujących tematach:</span><span class="sxs-lookup"><span data-stu-id="d94c8-219">You can learn more about numbers in C# in the following topics:</span></span>

- [<span data-ttu-id="d94c8-220">Tabela typów całkowitych</span><span class="sxs-lookup"><span data-stu-id="d94c8-220">Integral Types Table</span></span>](../../language-reference/keywords/integral-types-table.md)
- [<span data-ttu-id="d94c8-221">Tabela typów zmiennoprzecinkowych</span><span class="sxs-lookup"><span data-stu-id="d94c8-221">Floating-Point Types Table</span></span>](../../language-reference/keywords/floating-point-types-table.md)
- [<span data-ttu-id="d94c8-222">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="d94c8-222">Built-In Types Table</span></span>](../../language-reference/keywords/built-in-types-table.md)
- [<span data-ttu-id="d94c8-223">Tabela niejawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="d94c8-223">Implicit Numeric Conversions Table</span></span>](../../language-reference/keywords/implicit-numeric-conversions-table.md)
- [<span data-ttu-id="d94c8-224">Tabela jawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="d94c8-224">Explicit Numeric Conversions Table</span></span>](../../language-reference/keywords/explicit-numeric-conversions-table.md)

---
title: Cyfry w C# programie — wprowadzenie C# do samouczka
description: Poznaj C# typy liczbowe, ich właściwości i metody.
ms.date: 10/31/2017
ms.custom: mvc
ms.openlocfilehash: 731824fefcf4966a885c53be8f71e77140541383
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834098"
---
# <a name="manipulate-integral-and-floating-point-numbers-in-c"></a><span data-ttu-id="6d3dc-103">Manipuluj liczby całkowite i zmiennoprzecinkowe w C @ no__t-0</span><span class="sxs-lookup"><span data-stu-id="6d3dc-103">Manipulate integral and floating point numbers in C\#</span></span>

<span data-ttu-id="6d3dc-104">Ten samouczek zawiera informacje o typach liczbowych w C# sposób interaktywny.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-104">This tutorial teaches you about the numeric types in C# interactively.</span></span> <span data-ttu-id="6d3dc-105">Zapiszesz małe ilości kodu, a następnie utworzysz i uruchomisz ten kod.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-105">You'll write small amounts of code, then you'll compile and run that code.</span></span> <span data-ttu-id="6d3dc-106">Samouczek zawiera serię lekcji, które eksplorują liczby i operacje matematyczne C#w programie.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-106">The tutorial contains a series of lessons that explore numbers and math operations in C#.</span></span> <span data-ttu-id="6d3dc-107">Te lekcje uczyją się podstaw C# języka.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-107">These lessons teach you the fundamentals of the C# language.</span></span>

<span data-ttu-id="6d3dc-108">Ten samouczek oczekuje, że masz maszynę, której możesz użyć do programowania.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-108">This tutorial expects you to have a machine you can use for development.</span></span> <span data-ttu-id="6d3dc-109">Samouczek platformy .NET [Hello World w ciągu 10 minut](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) zawiera instrukcje dotyczące konfigurowania lokalnego środowiska deweloperskiego w systemie Windows, Linux lub macOS.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-109">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span> <span data-ttu-id="6d3dc-110">Krótkie omówienie poleceń, z których będziesz korzystać, znajduje się w zapoznanie [z narzędziami programistycznymi](local-environment.md) zawierającymi linki do dalszych szczegółów.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-110">A quick overview of the commands you'll use is in the [Become familiar with the development tools](local-environment.md) with links to more details.</span></span>

## <a name="explore-integer-math"></a><span data-ttu-id="6d3dc-111">Eksploruj liczbę całkowitą</span><span class="sxs-lookup"><span data-stu-id="6d3dc-111">Explore integer math</span></span>

<span data-ttu-id="6d3dc-112">Utwórz katalog o nazwie *Numbers — szybki start*.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-112">Create a directory named *numbers-quickstart*.</span></span> <span data-ttu-id="6d3dc-113">Upewnij się, że bieżący katalog i uruchomiono `dotnet new console -n NumbersInCSharp -o .`.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-113">Make that the current directory and run `dotnet new console -n NumbersInCSharp -o .`.</span></span>

<span data-ttu-id="6d3dc-114">Otwórz *program.cs* w ulubionym edytorze i Zastąp wiersz `Console.WriteLine("Hello World!");` następującym:</span><span class="sxs-lookup"><span data-stu-id="6d3dc-114">Open *Program.cs* in your favorite editor, and replace the line `Console.WriteLine("Hello World!");` with the following:</span></span>

```csharp
int a = 18;
int b = 6;
int c = a + b;
Console.WriteLine(c);
```

<span data-ttu-id="6d3dc-115">Uruchom ten kod, wpisując `dotnet run` w oknie poleceń.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-115">Run this code by typing `dotnet run` in your command window.</span></span>

<span data-ttu-id="6d3dc-116">Właśnie zaobserwowano jedną z podstawowych operacji matematycznych z liczbami całkowitymi.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-116">You've just seen one of the fundamental math operations with integers.</span></span> <span data-ttu-id="6d3dc-117">Typ `int` reprezentuje liczbę **całkowitą**, zero, dodatnią lub ujemną.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-117">The `int` type represents an **integer**, a zero, positive, or negative whole number.</span></span> <span data-ttu-id="6d3dc-118">Użyj symbolu `+` do dodania.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-118">You use the `+` symbol for addition.</span></span> <span data-ttu-id="6d3dc-119">Inne typowe operacje matematyczne na liczbach całkowitych obejmują:</span><span class="sxs-lookup"><span data-stu-id="6d3dc-119">Other common mathematical operations for integers include:</span></span>

- <span data-ttu-id="6d3dc-120">`-` w przypadku odejmowania</span><span class="sxs-lookup"><span data-stu-id="6d3dc-120">`-` for subtraction</span></span>
- <span data-ttu-id="6d3dc-121">`*` dla mnożenia</span><span class="sxs-lookup"><span data-stu-id="6d3dc-121">`*` for multiplication</span></span>
- <span data-ttu-id="6d3dc-122">`/` dla dzielenia</span><span class="sxs-lookup"><span data-stu-id="6d3dc-122">`/` for division</span></span>

<span data-ttu-id="6d3dc-123">Zacznij od eksplorowania tych różnych operacji.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-123">Start by exploring those different operations.</span></span> <span data-ttu-id="6d3dc-124">Dodaj te wiersze po wierszu, który zapisuje wartość `c`:</span><span class="sxs-lookup"><span data-stu-id="6d3dc-124">Add these lines after the line that writes the value of `c`:</span></span>

```csharp
c = a - b;
Console.WriteLine(c);
c = a * b;
Console.WriteLine(c);
c = a / b;
Console.WriteLine(c);
```

<span data-ttu-id="6d3dc-125">Uruchom ten kod, wpisując `dotnet run` w oknie poleceń.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-125">Run this code by typing `dotnet run` in your command window.</span></span>

<span data-ttu-id="6d3dc-126">Możesz również eksperymentować, wykonując wiele operacji matematycznych w tym samym wierszu, jeśli chcesz.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-126">You can also experiment by performing multiple mathematics operations in the same line, if you'd like.</span></span> <span data-ttu-id="6d3dc-127">Spróbuj `c = a + b - 12 * 17;` na przykład.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-127">Try `c = a + b - 12 * 17;` for example.</span></span> <span data-ttu-id="6d3dc-128">Mieszanie zmiennych i liczb stałych jest dozwolone.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-128">Mixing variables and constant numbers is allowed.</span></span>

> [!TIP]
> <span data-ttu-id="6d3dc-129">Podczas eksplorowania C# (lub dowolnego języka programowania) nastąpi pomyłki podczas pisania kodu.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-129">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="6d3dc-130">**Kompilator** odnajdzie te błędy i zgłosi je do użytkownika.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-130">The **compiler** will find those errors and report them to you.</span></span> <span data-ttu-id="6d3dc-131">Gdy dane wyjściowe zawierają komunikaty o błędach, dokładnie zapoznaj się z przykładowym kodem i kodem w oknie, aby zobaczyć, co należy naprawić.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-131">When the output contains error messages, look closely at the example code and the code in your window to see what to fix.</span></span>
> <span data-ttu-id="6d3dc-132">To ćwiczenie pomoże Ci poznać strukturę C# kodu.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-132">That exercise will help you learn the structure of C# code.</span></span>

<span data-ttu-id="6d3dc-133">Wykonano pierwszy krok.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-133">You've finished the first step.</span></span> <span data-ttu-id="6d3dc-134">Przed rozpoczęciem następnej sekcji przechodźmy bieżący kod w oddzielną metodę.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-134">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="6d3dc-135">Ułatwia to rozpoczęcie pracy z nowym przykładem.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-135">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="6d3dc-136">Zmień nazwę metody `Main` na `WorkingWithIntegers` i Napisz nową metodę `Main`, która wywołuje `WorkingWithIntegers`.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-136">Rename your `Main` method to `WorkingWithIntegers` and write a new `Main` method that calls `WorkingWithIntegers`.</span></span> <span data-ttu-id="6d3dc-137">Po zakończeniu kod powinien wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="6d3dc-137">When you finish, your code should look like this:</span></span>

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

## <a name="explore-order-of-operations"></a><span data-ttu-id="6d3dc-138">Eksploruj kolejność operacji</span><span class="sxs-lookup"><span data-stu-id="6d3dc-138">Explore order of operations</span></span>

<span data-ttu-id="6d3dc-139">Dodaj komentarz do wywołania `WorkingWithIntegers()`.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-139">Comment out the call to `WorkingWithIntegers()`.</span></span> <span data-ttu-id="6d3dc-140">Dane wyjściowe będą mniej czytelne podczas pracy w tej sekcji:</span><span class="sxs-lookup"><span data-stu-id="6d3dc-140">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//WorkingWithIntegers();
```

<span data-ttu-id="6d3dc-141">@No__t-0 uruchamia **komentarz** w C#.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-141">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="6d3dc-142">Komentarze są dowolnym tekstem, który chcesz zachować w kodzie źródłowym, ale nie można go wykonać jako kod.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-142">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="6d3dc-143">Kompilator nie generuje żadnego kodu wykonywalnego z komentarzy.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-143">The compiler does not generate any executable code from comments.</span></span>

<span data-ttu-id="6d3dc-144">C# Język definiuje kolejność różnych operacji matematycznych z regułami spójnymi z regułami, które zostały uzyskane w postaci matematyki.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-144">The C# language defines the precedence of different mathematics operations with rules consistent with the rules you learned in mathematics.</span></span>
<span data-ttu-id="6d3dc-145">Mnożenie i dzielenie mają pierwszeństwo przed dodaniem i odejmowaniem.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-145">Multiplication and division take precedence over addition and subtraction.</span></span>
<span data-ttu-id="6d3dc-146">Zbadaj, że dodając następujący kod do metody `Main` i wykonując `dotnet run`:</span><span class="sxs-lookup"><span data-stu-id="6d3dc-146">Explore that by adding the following code to your `Main` method, and executing `dotnet run`:</span></span>

```csharp
int a = 5;
int b = 4;
int c = 2;
int d = a + b * c;
Console.WriteLine(d);
 ```

<span data-ttu-id="6d3dc-147">Dane wyjściowe pokazują, że mnożenie jest wykonywane przed dodaniem.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-147">The output demonstrates that the multiplication is performed before the addition.</span></span>

<span data-ttu-id="6d3dc-148">Można wymusić inną kolejność operacji, dodając nawiasy wokół operacji lub operacji, które chcesz wykonać jako pierwsze.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-148">You can force a different order of operation by adding parentheses around the operation or operations you want performed first.</span></span> <span data-ttu-id="6d3dc-149">Dodaj następujące wiersze i uruchom ponownie:</span><span class="sxs-lookup"><span data-stu-id="6d3dc-149">Add the following lines and run again:</span></span>

```csharp
d = (a + b) * c;
Console.WriteLine(d);
```

<span data-ttu-id="6d3dc-150">Dowiedz się więcej, łącząc wiele różnych operacji.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-150">Explore more by combining many different operations.</span></span> <span data-ttu-id="6d3dc-151">Dodaj coś przypominającego następujące wiersze w dolnej części metody `Main`.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-151">Add something like the following lines at the bottom of your `Main` method.</span></span> <span data-ttu-id="6d3dc-152">Spróbuj ponownie wykonać `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-152">Try `dotnet run` again.</span></span>

```csharp
d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
Console.WriteLine(d);
```

<span data-ttu-id="6d3dc-153">Być może zauważono interesujące zachowanie dla liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-153">You may have noticed an interesting behavior for integers.</span></span> <span data-ttu-id="6d3dc-154">Dzielenie liczb całkowitych zawsze generuje wynik w postaci liczby całkowitej, nawet gdy oczekuje się, że wynik będzie zawierać część dziesiętną lub ułamkową.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-154">Integer division always produces an integer result, even when you'd expect the result to include a decimal or fractional portion.</span></span>

<span data-ttu-id="6d3dc-155">Jeśli takie zachowanie nie zostało zaobserwowane, wypróbuj następujący kod na końcu metody `Main`:</span><span class="sxs-lookup"><span data-stu-id="6d3dc-155">If you haven't seen this behavior, try the following code at the end of your `Main` method:</span></span>

```csharp
int e = 7;
int f = 4;
int g = 3;
int h = (e + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="6d3dc-156">Wpisz `dotnet run` ponownie, aby wyświetlić wyniki.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-156">Type `dotnet run` again to see the results.</span></span>

<span data-ttu-id="6d3dc-157">Zanim zaczniesz, przyjrzyjmy się cały kod w tej sekcji i umieścisz go w nowej metodzie.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-157">Before moving on, let's take all the code you've written in this section and put it in a new method.</span></span> <span data-ttu-id="6d3dc-158">Wywołaj nową metodę `OrderPrecedence`.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-158">Call that new method `OrderPrecedence`.</span></span>
<span data-ttu-id="6d3dc-159">Należy się do nich zakończyć w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="6d3dc-159">You should end up with something like this:</span></span>

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

## <a name="explore-integer-precision-and-limits"></a><span data-ttu-id="6d3dc-160">Eksploruj precyzję całkowitą i limity</span><span class="sxs-lookup"><span data-stu-id="6d3dc-160">Explore integer precision and limits</span></span>

<span data-ttu-id="6d3dc-161">Ten ostatni przykład wskazuje, że dzielenie liczby całkowitej obcina wynik.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-161">That last sample showed you that integer division truncates the result.</span></span>
<span data-ttu-id="6d3dc-162">**Resztę** można uzyskać za pomocą operatora **modulo** , znaku `%`.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-162">You can get the **remainder** by using the **modulo** operator, the `%` character.</span></span> <span data-ttu-id="6d3dc-163">Wypróbuj następujący kod w metodzie `Main`:</span><span class="sxs-lookup"><span data-stu-id="6d3dc-163">Try the following code in your `Main` method:</span></span>

```csharp
int a = 7;
int b = 4;
int c = 3;
int d = (a + b) / c;
int e = (a + b) % c;
Console.WriteLine($"quotient: {d}");
Console.WriteLine($"remainder: {e}");
```

<span data-ttu-id="6d3dc-164">Typ C# Integer różni się od matematycznych liczb całkowitych w jeden inny sposób: typ `int` ma limity minimalne i maksymalne.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-164">The C# integer type differs from mathematical integers in one other way: the `int` type has minimum and maximum limits.</span></span> <span data-ttu-id="6d3dc-165">Dodaj ten kod do metody `Main`, aby zobaczyć te limity:</span><span class="sxs-lookup"><span data-stu-id="6d3dc-165">Add this code to your `Main` method to see those limits:</span></span>

```csharp
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");
```

<span data-ttu-id="6d3dc-166">Jeśli obliczenie generuje wartość, która przekracza te limity, istnieje warunek **niedopełnienia** **lub** przeciążenia.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-166">If a calculation produces a value that exceeds those limits, you have an **underflow** or **overflow** condition.</span></span> <span data-ttu-id="6d3dc-167">Odpowiedź wydaje się być zawijana z jednego limitu do drugiego.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-167">The answer appears to wrap from one limit to the other.</span></span> <span data-ttu-id="6d3dc-168">Dodaj te dwa wiersze do metody `Main`, aby zobaczyć przykład:</span><span class="sxs-lookup"><span data-stu-id="6d3dc-168">Add these two lines to your `Main` method to see an example:</span></span>

```csharp
int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```

<span data-ttu-id="6d3dc-169">Zwróć uwagę, że odpowiedź jest bardzo bliska minimalnej (ujemnej) liczbie całkowitej.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-169">Notice that the answer is very close to the minimum (negative) integer.</span></span> <span data-ttu-id="6d3dc-170">Jest taka sama jak `min + 2`.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-170">It's the same as `min + 2`.</span></span>
<span data-ttu-id="6d3dc-171">Operacja dodawania **spowodowała przepełnienie** dozwolonych wartości liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-171">The addition operation **overflowed** the allowed values for integers.</span></span>
<span data-ttu-id="6d3dc-172">Odpowiedź to bardzo duża liczba ujemna, ponieważ przepełnienie "zawija" z największej możliwej wartości całkowitej do najmniejszej.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-172">The answer is a very large negative number because an overflow "wraps around" from the largest possible integer value to the smallest.</span></span>

<span data-ttu-id="6d3dc-173">Istnieją inne typy liczbowe z różnymi limitami i dokładnością, których można użyć, gdy typ `int` nie spełnia Twoich potrzeb.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-173">There are other numeric types with different limits and precision that you would use when the `int` type doesn't meet your needs.</span></span> <span data-ttu-id="6d3dc-174">Eksplorujmy te informacje dalej.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-174">Let's explore those next.</span></span>

<span data-ttu-id="6d3dc-175">Teraz Przenieśmy kod napisany w tej sekcji do oddzielnej metody.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-175">Once again, let's move the code you wrote in this section into a separate method.</span></span> <span data-ttu-id="6d3dc-176">Nadaj mu nazwę `TestLimits`.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-176">Name it `TestLimits`.</span></span>

## <a name="work-with-the-double-type"></a><span data-ttu-id="6d3dc-177">Pracuj z typem Double</span><span class="sxs-lookup"><span data-stu-id="6d3dc-177">Work with the double type</span></span>

<span data-ttu-id="6d3dc-178">Typ liczbowy `double` reprezentuje liczbę zmiennoprzecinkową o podwójnej precyzji.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-178">The `double` numeric type represents a double-precision floating point number.</span></span> <span data-ttu-id="6d3dc-179">Te warunki mogą być nowe dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-179">Those terms may be new to you.</span></span> <span data-ttu-id="6d3dc-180">Liczba **zmiennoprzecinkowa** jest przydatna do reprezentowania numerów niecałkowitych, które mogą być bardzo duże lub małe.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-180">A **floating point** number is useful to represent non-integral numbers that may be very large or small in magnitude.</span></span> <span data-ttu-id="6d3dc-181">**Podwójne precyzja** oznacza, że te liczby są przechowywane z większą dokładnością niż **Pojedyncza precyzja**.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-181">**Double-precision** means that these numbers are stored using greater precision than **single-precision**.</span></span> <span data-ttu-id="6d3dc-182">Na nowoczesnych komputerach, bardziej powszechne jest użycie podwójnej precyzji niż pojedyncze numery precyzji.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-182">On modern computers, it is more common to use double precision than single precision numbers.</span></span>
<span data-ttu-id="6d3dc-183">Eksplorujmy.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-183">Let's explore.</span></span> <span data-ttu-id="6d3dc-184">Dodaj następujący kod i zobacz wynik:</span><span class="sxs-lookup"><span data-stu-id="6d3dc-184">Add the following code and see the result:</span></span>

```csharp
double a = 5;
double b = 4;
double c = 2;
double d = (a + b) / c;
Console.WriteLine(d);
```

<span data-ttu-id="6d3dc-185">Należy zauważyć, że odpowiedź zawiera część dziesiętną ilorazu.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-185">Notice that the answer includes the decimal portion of the quotient.</span></span> <span data-ttu-id="6d3dc-186">Wypróbuj nieco bardziej skomplikowane wyrażenie z podwajaniem:</span><span class="sxs-lookup"><span data-stu-id="6d3dc-186">Try a slightly more complicated expression with doubles:</span></span>

```csharp
double e = 19;
double f = 23;
double g = 8;
double h = (e + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="6d3dc-187">Zakres wartości podwójnej jest znacznie większy niż wartości całkowite.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-187">The range of a double value is much greater than integer values.</span></span> <span data-ttu-id="6d3dc-188">Wypróbuj Poniższy kod poniżej tego, co zostało wcześniej zrobione:</span><span class="sxs-lookup"><span data-stu-id="6d3dc-188">Try the following code below what you've written so far:</span></span>

```csharp
double max = double.MaxValue;
double min = double.MinValue;
Console.WriteLine($"The range of double is {min} to {max}");
```

<span data-ttu-id="6d3dc-189">Te wartości są drukowane w notacji wykładniczej.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-189">These values are printed out in scientific notation.</span></span> <span data-ttu-id="6d3dc-190">Liczba po lewej stronie `E` to mantysę.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-190">The number to the left of the `E` is the significand.</span></span> <span data-ttu-id="6d3dc-191">Liczba po prawej stronie jest wykładnikiem potęgi od 10.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-191">The number to the right is the exponent, as a power of 10.</span></span>

<span data-ttu-id="6d3dc-192">Podobnie jak w przypadku liczb dziesiętnych w zapisie matematycznym, podwaja w C# może mieć błędy zaokrągleń.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-192">Just like decimal numbers in math, doubles in C# can have rounding errors.</span></span> <span data-ttu-id="6d3dc-193">Wypróbuj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="6d3dc-193">Try this code:</span></span>

```csharp
double third = 1.0 / 3.0;
Console.WriteLine(third);
```

<span data-ttu-id="6d3dc-194">Wiadomo, że powtarzające się `0.3` nie są dokładnie takie same, jak `1/3`.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-194">You know that `0.3` repeating is not exactly the same as `1/3`.</span></span>

<span data-ttu-id="6d3dc-195">***Sprawdz***</span><span class="sxs-lookup"><span data-stu-id="6d3dc-195">***Challenge***</span></span>

<span data-ttu-id="6d3dc-196">Wypróbuj inne obliczenia z dużymi liczbami, małymi liczbami, mnożeniem i dzieleniem przy użyciu typu `double`.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-196">Try other calculations with large numbers, small numbers, multiplication and division using the `double` type.</span></span> <span data-ttu-id="6d3dc-197">Wypróbuj bardziej skomplikowane obliczenia.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-197">Try more complicated calculations.</span></span>

<span data-ttu-id="6d3dc-198">Po pewnym czasie z wezwaniem Zrób wpisany kod i umieść go w nowej metodzie.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-198">After you've spent some time with the challenge, take the code you've written and place it in a new method.</span></span> <span data-ttu-id="6d3dc-199">Nazwa nowej metody `WorkWithDoubles`.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-199">Name that new method `WorkWithDoubles`.</span></span>

## <a name="work-with-fixed-point-types"></a><span data-ttu-id="6d3dc-200">Pracuj z stałymi typami punktów</span><span class="sxs-lookup"><span data-stu-id="6d3dc-200">Work with fixed point types</span></span>

<span data-ttu-id="6d3dc-201">Wykorzystano podstawowe typy liczbowe w C#: liczby całkowite i podwaja.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-201">You've seen the basic numeric types in C#: integers and doubles.</span></span>  <span data-ttu-id="6d3dc-202">Istnieje jeden inny typ do poznania: typ `decimal`.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-202">There is one other type to learn: the `decimal` type.</span></span> <span data-ttu-id="6d3dc-203">Typ `decimal` ma mniejszy zakres, ale większą precyzję niż `double`.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-203">The `decimal` type has a smaller range but greater precision than `double`.</span></span> <span data-ttu-id="6d3dc-204">Termin " **stała** " oznacza, że punkt dziesiętny (lub punkt binarny) nie jest przenoszony.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-204">The term **fixed point** means that the decimal point (or binary point) doesn't move.</span></span> <span data-ttu-id="6d3dc-205">Przyjrzyjmy się:</span><span class="sxs-lookup"><span data-stu-id="6d3dc-205">Let's take a look:</span></span>

```csharp
decimal min = decimal.MinValue;
decimal max = decimal.MaxValue;
Console.WriteLine($"The range of the decimal type is {min} to {max}");
```

<span data-ttu-id="6d3dc-206">Należy zauważyć, że zakres jest mniejszy niż typ `double`.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-206">Notice that the range is smaller than the `double` type.</span></span> <span data-ttu-id="6d3dc-207">Większą precyzję typu dziesiętnego można zobaczyć, próbując wykonać następujący kod:</span><span class="sxs-lookup"><span data-stu-id="6d3dc-207">You can see the greater precision with the decimal type by trying the following code:</span></span>

```csharp
double a = 1.0;
double b = 3.0;
Console.WriteLine(a / b);

decimal c = 1.0M;
decimal d = 3.0M;
Console.WriteLine(c / d);
```

<span data-ttu-id="6d3dc-208">Sufiks `M` na liczbie wskazuje, że w przypadku stałej należy użyć typu `decimal`.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-208">The `M` suffix on the numbers is how you indicate that a constant should use the `decimal` type.</span></span>

<span data-ttu-id="6d3dc-209">Zauważ, że zapis matematyczny przy użyciu typu dziesiętnego ma więcej cyfr po prawej stronie przecinka dziesiętnego.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-209">Notice that the math using the decimal type has more digits to the right of the decimal point.</span></span>

<span data-ttu-id="6d3dc-210">***Sprawdz***</span><span class="sxs-lookup"><span data-stu-id="6d3dc-210">***Challenge***</span></span>

<span data-ttu-id="6d3dc-211">Teraz, gdy widzisz różne typy liczbowe, napisz kod, który oblicza obszar okręgu, którego promień to 2,50 cm.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-211">Now that you've seen the different numeric types, write code that calculates the area of a circle whose radius is 2.50 centimeters.</span></span> <span data-ttu-id="6d3dc-212">Należy pamiętać, że obszar okręgu to promień kwadratowy pomnożony przez PI.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-212">Remember that the area of a circle is the radius squared multiplied by PI.</span></span> <span data-ttu-id="6d3dc-213">Jedna Wskazówka: .NET zawiera stałą dla liczby PI, <xref:System.Math.PI?displayProperty=nameWithType>, której można użyć dla tej wartości.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-213">One hint: .NET contains a constant for PI, <xref:System.Math.PI?displayProperty=nameWithType> that you can use for that value.</span></span>

<span data-ttu-id="6d3dc-214">Należy uzyskać odpowiedź między 19 a 20.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-214">You should get an answer between 19 and 20.</span></span>
<span data-ttu-id="6d3dc-215">Odpowiedź możesz sprawdzić, [przeglądając przykładowy kod w usłudze GitHub](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106)</span><span class="sxs-lookup"><span data-stu-id="6d3dc-215">You can check your answer by [looking at the finished sample code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106)</span></span>

<span data-ttu-id="6d3dc-216">Wypróbuj inne formuły, jeśli chcesz.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-216">Try some other formulas if you'd like.</span></span>

<span data-ttu-id="6d3dc-217">Ukończono Przewodnik Szybki Start dotyczący liczb C#.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-217">You've completed the "Numbers in C#" quickstart.</span></span> <span data-ttu-id="6d3dc-218">Możesz kontynuować pracę z [gałęziami i pętle](branches-and-loops-local.md) szybkiego startu w swoim środowisku programistycznym.</span><span class="sxs-lookup"><span data-stu-id="6d3dc-218">You can continue with the [Branches and loops](branches-and-loops-local.md) quickstart in your own development environment.</span></span>

<span data-ttu-id="6d3dc-219">Więcej informacji na temat numerów C# można znaleźć w następujących tematach:</span><span class="sxs-lookup"><span data-stu-id="6d3dc-219">You can learn more about numbers in C# in the following topics:</span></span>

- [<span data-ttu-id="6d3dc-220">Typy całkowite</span><span class="sxs-lookup"><span data-stu-id="6d3dc-220">Integral types</span></span>](../../language-reference/builtin-types/integral-numeric-types.md)
- [<span data-ttu-id="6d3dc-221">Tabela typów zmiennoprzecinkowych</span><span class="sxs-lookup"><span data-stu-id="6d3dc-221">Floating-Point Types Table</span></span>](../../language-reference/builtin-types/floating-point-numeric-types.md)
- [<span data-ttu-id="6d3dc-222">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="6d3dc-222">Built-In Types Table</span></span>](../../language-reference/keywords/built-in-types-table.md)
- [<span data-ttu-id="6d3dc-223">Tabela niejawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="6d3dc-223">Implicit Numeric Conversions Table</span></span>](../../language-reference/keywords/implicit-numeric-conversions-table.md)
- [<span data-ttu-id="6d3dc-224">Tabela jawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="6d3dc-224">Explicit Numeric Conversions Table</span></span>](../../language-reference/keywords/explicit-numeric-conversions-table.md)

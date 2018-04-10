---
title: Liczby w C# samouczek - C# lokalnego poradniki Szybki Start
description: Naucz się C# eksplorując typy liczbowe, ich właściwości i metody.
author: billwagner
ms.author: wiwagn
ms.date: 10/31/2017
ms.topic: get-started-article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 6570693ea09ca2b548615291ba4f2b69f6d92482
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="numbers-in-c-quickstart"></a><span data-ttu-id="94333-103">Liczby w języku C# — Szybki Start</span><span class="sxs-lookup"><span data-stu-id="94333-103">Numbers in C# quickstart</span></span>

<span data-ttu-id="94333-104">Ta opcja szybkiego startu zawiera informacje na temat typu liczbowego w języku C# interaktywnie.</span><span class="sxs-lookup"><span data-stu-id="94333-104">This quickstart teaches you about the number types in C# interactively.</span></span> <span data-ttu-id="94333-105">Przedstawiono tworzenie niewielkich ilości kodu, a następnie będzie można skompilować i uruchomić ten kod.</span><span class="sxs-lookup"><span data-stu-id="94333-105">You'll write small amounts of code, then you'll compile and run that code.</span></span> <span data-ttu-id="94333-106">Procedury szybkiego startu zawiera szereg — lekcje przedstawiających operacji matematycznych w języku C# i cyfry.</span><span class="sxs-lookup"><span data-stu-id="94333-106">The quickstart contains a series of lessons that explore numbers and math operations in C#.</span></span> <span data-ttu-id="94333-107">Że wnioski uczy również podstaw programu w języku C#.</span><span class="sxs-lookup"><span data-stu-id="94333-107">These lessons teach you the fundamentals of the C# language.</span></span>

<span data-ttu-id="94333-108">Ta opcja szybkiego startu oczekuje posiadania maszynie, która służy do tworzenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="94333-108">This quickstart expects you to have a machine you can use for development.</span></span> <span data-ttu-id="94333-109">Temat .NET [wprowadzenie w ciągu 10 minut](https://www.microsoft.com/net/core) zawiera instrukcje dotyczące konfigurowania środowiska deweloperskiego lokalnego Mac, komputera lub Linux.</span><span class="sxs-lookup"><span data-stu-id="94333-109">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="94333-110">Jest to szybki przegląd poleceń będzie używany w [wprowadzenie do lokalnego poradniki Szybki Start](local-environment.md) wraz z łączami, aby uzyskać więcej szczegółów.</span><span class="sxs-lookup"><span data-stu-id="94333-110">A quick overview of the commands you'll use is in the [introduction to the local quickstarts](local-environment.md) with links to more details.</span></span>

## <a name="explore-integer-math"></a><span data-ttu-id="94333-111">Eksploruj matematyczne liczba całkowita</span><span class="sxs-lookup"><span data-stu-id="94333-111">Explore integer math</span></span>

<span data-ttu-id="94333-112">Utwórz katalog o nazwie **szybkiego startu numery**.</span><span class="sxs-lookup"><span data-stu-id="94333-112">Create a directory named **numbers-quickstart**.</span></span> <span data-ttu-id="94333-113">Upewnij, że bieżący katalog i uruchom `dotnet new console -n NumbersInCSharp -o .`.</span><span class="sxs-lookup"><span data-stu-id="94333-113">Make that the current directory and run `dotnet new console -n NumbersInCSharp -o .`.</span></span>

<span data-ttu-id="94333-114">Otwórz **Program.cs** ulubionego edytora i Zastąp linię `Console.Writeline("Hello World!");` następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="94333-114">Open **Program.cs** in your favorite editor, and replace the line `Console.Writeline("Hello World!");` with the following:</span></span>

```csharp
int a = 18;
int b = 6;
int c = a + b;
Console.WriteLine(c);
```

<span data-ttu-id="94333-115">Uruchom ten kod, wpisując `dotnet run` w oknie polecenia.</span><span class="sxs-lookup"><span data-stu-id="94333-115">Run this code by typing `dotnet run` in your command window.</span></span> 

<span data-ttu-id="94333-116">Po prostu przedstawiono jednej z operacji matematycznych podstawowych z liczbami całkowitymi.</span><span class="sxs-lookup"><span data-stu-id="94333-116">You've just seen one of the fundamental math operations with integers.</span></span> <span data-ttu-id="94333-117">`int` Wpisz reprezentuje **całkowitą**, liczbą całkowitą liczbą dodatnią lub ujemną.</span><span class="sxs-lookup"><span data-stu-id="94333-117">The `int` type represents an **integer**, a positive or negative whole number.</span></span> <span data-ttu-id="94333-118">Możesz użyć `+` symbol do dodania.</span><span class="sxs-lookup"><span data-stu-id="94333-118">You use the `+` symbol for addition.</span></span> <span data-ttu-id="94333-119">Inne typowe operacji matematycznych liczb całkowitych obejmują:</span><span class="sxs-lookup"><span data-stu-id="94333-119">Other common mathematical operations for integers include:</span></span>

- <span data-ttu-id="94333-120">`-` dla odejmowania</span><span class="sxs-lookup"><span data-stu-id="94333-120">`-` for subtraction</span></span>
- <span data-ttu-id="94333-121">`*` dla mnożenia</span><span class="sxs-lookup"><span data-stu-id="94333-121">`*` for multiplication</span></span>
- <span data-ttu-id="94333-122">`/` podziału</span><span class="sxs-lookup"><span data-stu-id="94333-122">`/` for division</span></span>

<span data-ttu-id="94333-123">Rozpocznij od eksploracji tych różnych operacji.</span><span class="sxs-lookup"><span data-stu-id="94333-123">Start by exploring those different operations.</span></span> <span data-ttu-id="94333-124">Dodaj następujące wiersze po wierszu, który zapisuje wartość `c`:</span><span class="sxs-lookup"><span data-stu-id="94333-124">Add these lines after the line that writes the value of `c`:</span></span>

```csharp
c = a - b;
Console.WriteLine(c);
c = a * b;
Console.WriteLine(c);
c = a / b;
Console.WriteLine(c);
```

<span data-ttu-id="94333-125">Uruchom ten kod, wpisując `dotnet run` w oknie polecenia.</span><span class="sxs-lookup"><span data-stu-id="94333-125">Run this code by typing `dotnet run` in your command window.</span></span> 
    
<span data-ttu-id="94333-126">Poeksperymentuj przez wykonanie wielu operacji matematyce w tej samej linii, jeśli chcesz.</span><span class="sxs-lookup"><span data-stu-id="94333-126">You can also experiment by performing multiple mathematics operations in the same line, if you'd like.</span></span> <span data-ttu-id="94333-127">Spróbuj `c = a + b - 12 * 17;` np.</span><span class="sxs-lookup"><span data-stu-id="94333-127">Try `c = a + b - 12 * 17;` for example.</span></span> <span data-ttu-id="94333-128">Mieszanie zmienne i stałe numery jest dozwolone.</span><span class="sxs-lookup"><span data-stu-id="94333-128">Mixing variables and constant numbers is allowed.</span></span>

> [!TIP]
> <span data-ttu-id="94333-129">Ci poznać platformę C# (lub dowolnego języka programowania), należy podjąć błędów podczas pisania kodu.</span><span class="sxs-lookup"><span data-stu-id="94333-129">As you explore C# (or any programming language), you'll make mistakes when you write code.</span></span> <span data-ttu-id="94333-130">**Kompilatora** znajdzie te błędy i raportuj je użytkownikowi.</span><span class="sxs-lookup"><span data-stu-id="94333-130">The **compiler** will find those errors and report them to you.</span></span> <span data-ttu-id="94333-131">Jeśli dane wyjściowe zawiera komunikaty o błędach, należy dokładnie przejrzeć przykładowy kod i kod w oknie, aby zobaczyć rozwiązać problem.</span><span class="sxs-lookup"><span data-stu-id="94333-131">When the output contains error messages, look closely at the example code and the code in your window to see what to fix.</span></span>
> <span data-ttu-id="94333-132">Tym ćwiczeniu zostanie zapoznawania się struktury kodu C#.</span><span class="sxs-lookup"><span data-stu-id="94333-132">That exercise will help you learn the structure of C# code.</span></span>     

<span data-ttu-id="94333-133">Po zakończeniu pierwszym krokiem.</span><span class="sxs-lookup"><span data-stu-id="94333-133">You've finished the first step.</span></span> <span data-ttu-id="94333-134">Przed rozpoczęciem następnej sekcji przejdziemy bieżącego kodu w oddzielnych metodach.</span><span class="sxs-lookup"><span data-stu-id="94333-134">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="94333-135">Który ułatwia rozpoczęcie pracy z nowego przykład.</span><span class="sxs-lookup"><span data-stu-id="94333-135">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="94333-136">Zmień nazwę Twojej `Main` metodę `WorkingWithIntegers` i zapisać nową `Main` — metoda, która wywołuje `WorkingWithIntegers`.</span><span class="sxs-lookup"><span data-stu-id="94333-136">Rename your `Main` method to `WorkingWithIntegers` and write a new `Main` method that calls `WorkingWithIntegers`.</span></span> <span data-ttu-id="94333-137">Po zakończeniu, kod powinien wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="94333-137">When you have finished, your code should look like this:</span></span>

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

## <a name="explore-order-of-operations"></a><span data-ttu-id="94333-138">Eksploruj kolejność operacji</span><span class="sxs-lookup"><span data-stu-id="94333-138">Explore order of operations</span></span>

<span data-ttu-id="94333-139">Komentarz wywołanie `WorkingWithIntegers()`.</span><span class="sxs-lookup"><span data-stu-id="94333-139">Comment out the call to `WorkingWithIntegers()`.</span></span> <span data-ttu-id="94333-140">Spowoduje to, że dane wyjściowe mniej elementów pracy w tej sekcji:</span><span class="sxs-lookup"><span data-stu-id="94333-140">It will make the output less cluttered as you work in this section:</span></span>

```csharp
//WorkingWithIntegers();
```

<span data-ttu-id="94333-141">`//` Uruchamia **komentarz** w języku C#.</span><span class="sxs-lookup"><span data-stu-id="94333-141">The `//` starts a **comment** in C#.</span></span> <span data-ttu-id="94333-142">Komentarze mogą zawierać dowolny tekst, który chcesz zachować w kodzie źródłowym, ale nie wykonują jako kod.</span><span class="sxs-lookup"><span data-stu-id="94333-142">Comments are any text you want to keep in your source code but not execute as code.</span></span> <span data-ttu-id="94333-143">Kompilator nie generuje żadnego kodu wykonywalnego z komentarzy.</span><span class="sxs-lookup"><span data-stu-id="94333-143">The compiler does not generate any executable code from comments.</span></span>

<span data-ttu-id="94333-144">W języku C# określa priorytet matematyce różne operacje przy użyciu reguły zgodnych z zasadami, które przedstawiono w matematyce.</span><span class="sxs-lookup"><span data-stu-id="94333-144">The C# language defines the precedence of different mathematics operations with rules consistent with the rules you learned in mathematics.</span></span>
<span data-ttu-id="94333-145">Mnożenia i dzielenia pierwszeństwo Dodawanie i odejmowanie.</span><span class="sxs-lookup"><span data-stu-id="94333-145">Multiplication and division take precedence over addition and subtraction.</span></span>
<span data-ttu-id="94333-146">Eksploruj który, dodając następujący kod, aby Twoje `Main` — metoda i execuing `dotnet run`:</span><span class="sxs-lookup"><span data-stu-id="94333-146">Explore that by adding the following code to your `Main` method, and execuing `dotnet run`:</span></span>

```csharp
int a = 5;
int b = 4;
int c = 2;
int d = a + b * c;
Console.WriteLine(d);
 ```

<span data-ttu-id="94333-147">Dane wyjściowe pokazuje, że mnożenia odbywa się przed dodaniem.</span><span class="sxs-lookup"><span data-stu-id="94333-147">The output demonstrates that the multiplication is performed before the addition.</span></span>

<span data-ttu-id="94333-148">Operacje, które mają przeprowadzić najpierw lub innej kolejności operacji można wymusić przez dodanie nawiasów wokół operacji.</span><span class="sxs-lookup"><span data-stu-id="94333-148">You can force a different order of operation by adding parentheses around the operation or operations you want performed first.</span></span> <span data-ttu-id="94333-149">Dodaj następujące wiersze i uruchom ponownie:</span><span class="sxs-lookup"><span data-stu-id="94333-149">Add the following lines and run again:</span></span>

```csharp
d = (a  + b) * c;
Console.WriteLine(d);
```

<span data-ttu-id="94333-150">Poznaj więcej, łącząc wiele różnych operacji.</span><span class="sxs-lookup"><span data-stu-id="94333-150">Explore more by combining many different operations.</span></span> <span data-ttu-id="94333-151">Dodaj przypominać następujące wiersze w dolnej części Twojego `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="94333-151">Add something like the following lines at the bottom of your `Main` method.</span></span> <span data-ttu-id="94333-152">Spróbuj `dotnet run` ponownie.</span><span class="sxs-lookup"><span data-stu-id="94333-152">Try `dotnet run` again.</span></span>

```csharp
d = (a + b) - 6 * c + (12 * 4) / 3 + 12;
Console.WriteLine(d);
```

<span data-ttu-id="94333-153">Można zauważyć interesujące zachowanie liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="94333-153">You may have noticed an interesting behavior for integers.</span></span> <span data-ttu-id="94333-154">Dzielenie liczby całkowitej zawsze daje wynik liczba całkowita, nawet wtedy, gdy oczekiwany wynik, który ma zawierać dziesiętną lub ułamkową część.</span><span class="sxs-lookup"><span data-stu-id="94333-154">Integer division always produces an integer result, even when you'd expect the result to include a decimal or fractional portion.</span></span>

<span data-ttu-id="94333-155">Jeśli jeszcze tego nie pokazano tego zachowania, spróbuj następujący kod na końcu Twojej `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="94333-155">If you haven't seen this behavior, try the following code at the end of your `Main` method:</span></span>

```csharp
int e = 7;
int f = 4;
int g = 3;
int h = (e  + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="94333-156">Typ `dotnet run` ponownie, aby wyświetlić wyniki.</span><span class="sxs-lookup"><span data-stu-id="94333-156">Type `dotnet run` again to see the results.</span></span>

<span data-ttu-id="94333-157">Przed kontynuowaniem, Przyjrzyjmy się cały kod został napisany w tej sekcji i umieszcza je w nowej metody.</span><span class="sxs-lookup"><span data-stu-id="94333-157">Before moving on, let's take all the code you've written in this section and put it in a new method.</span></span> <span data-ttu-id="94333-158">Wywołanie tej nowej metody `OrderPrecedence`.</span><span class="sxs-lookup"><span data-stu-id="94333-158">Call that new method `OrderPrecedence`.</span></span>
<span data-ttu-id="94333-159">Należy na końcu podobny do następującego:</span><span class="sxs-lookup"><span data-stu-id="94333-159">You should end up with something like this:</span></span>

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

## <a name="explore-integer-precision-and-limits"></a><span data-ttu-id="94333-160">Eksploruj całkowitą dokładność i limity</span><span class="sxs-lookup"><span data-stu-id="94333-160">Explore integer precision and limits</span></span>
<span data-ttu-id="94333-161">Tej ostatniej próbki wykazały, że dzielenie liczby całkowitej obcina wynik.</span><span class="sxs-lookup"><span data-stu-id="94333-161">That last sample showed you that integer division truncates the result.</span></span>
<span data-ttu-id="94333-162">Możesz uzyskać **pozostałej** za pomocą **modulo** operatora `%` znaków.</span><span class="sxs-lookup"><span data-stu-id="94333-162">You can get the **remainder** by using the **modulo** operator, the `%` character.</span></span> <span data-ttu-id="94333-163">Spróbuj następujący kod w Twojej `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="94333-163">Try the following code in your `Main` method:</span></span>

```csharp
int a = 7;
int b = 4;
int c = 3;
int d = (a  + b) / c;
int e = (a + b) % c;
Console.WriteLine($"quotient: {d}");
Console.WriteLine($"remainder: {e}");
```

<span data-ttu-id="94333-164">C# całkowitą różni się od matematyczne liczb całkowitych w inny sposób: `int` typ ma limity minimalną i maksymalną.</span><span class="sxs-lookup"><span data-stu-id="94333-164">The C# integer type differs from mathematical integers in one other way: the `int` type has minimum and maximum limits.</span></span> <span data-ttu-id="94333-165">Dodaj ten kod do Twojej `Main` metody, aby wyświetlić te limity:</span><span class="sxs-lookup"><span data-stu-id="94333-165">Add this code to your `Main` method to see those limits:</span></span>
    
```csharp
int max = int.MaxValue;
int min = int.MinValue;
Console.WriteLine($"The range of integers is {min} to {max}");
```

<span data-ttu-id="94333-166">Jeśli obliczeń daje wartość, która przekracza te limity, masz **niedopełnienie** lub **przepełnienie** warunku.</span><span class="sxs-lookup"><span data-stu-id="94333-166">If a calculation produces a value that exceeds those limits, you have an **underflow** or **overflow** condition.</span></span> <span data-ttu-id="94333-167">Odpowiedź zostanie wyświetlona opakowywać z limitu jednego do drugiego.</span><span class="sxs-lookup"><span data-stu-id="94333-167">The answer appears to wrap from one limit to the other.</span></span> <span data-ttu-id="94333-168">Dodaj następujące dwa wiersze do Twojej `Main` metody, na przykład:</span><span class="sxs-lookup"><span data-stu-id="94333-168">Add these two lines to your `Main` method to see an example:</span></span>

```csharp
int what = max + 3;
Console.WriteLine($"An example of overflow: {what}");
```
    
<span data-ttu-id="94333-169">Zwróć uwagę, że odpowiedź jest bliski minimalną liczbę całkowitą (ujemne).</span><span class="sxs-lookup"><span data-stu-id="94333-169">Notice that the answer is very close to the minimum (negative) integer.</span></span> <span data-ttu-id="94333-170">Jest taka sama jak `min + 2`.</span><span class="sxs-lookup"><span data-stu-id="94333-170">It's the same as `min + 2`.</span></span> <span data-ttu-id="94333-171">Operacja dodawania **nastąpiło przepełnienie** dozwolone wartości liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="94333-171">The addition operation **overflowed** the allowed values for integers.</span></span>
<span data-ttu-id="94333-172">Odpowiedzią jest bardzo dużą liczbą ujemną, ponieważ przepełnienie "zawija się wokół" z największą wartość całkowita możliwych do najmniejszej.</span><span class="sxs-lookup"><span data-stu-id="94333-172">The answer is a very large negative number because an overflow "wraps around" from the largest possible integer value to the smallest.</span></span>

<span data-ttu-id="94333-173">Istnieją inne typy liczbowe z różnych limitów i dokładność, że będą używane podczas `int` typu nie odpowiadają Twoim potrzebom.</span><span class="sxs-lookup"><span data-stu-id="94333-173">There are other numeric types with different limits and precision that you would use when the `int` type doesn't meet your needs.</span></span> <span data-ttu-id="94333-174">Przyjrzyjmy się tych dalej.</span><span class="sxs-lookup"><span data-stu-id="94333-174">Let's explore those next.</span></span>

<span data-ttu-id="94333-175">Jeszcze raz przejdziemy kodu zapisanego w tej sekcji w oddzielnych metodach.</span><span class="sxs-lookup"><span data-stu-id="94333-175">Once again, let's move the code you wrote in this section into a separate method.</span></span> <span data-ttu-id="94333-176">Nadaj mu nazwę `TestLimits`.</span><span class="sxs-lookup"><span data-stu-id="94333-176">Name it `TestLimits`.</span></span> 

## <a name="work-with-the-double-type"></a><span data-ttu-id="94333-177">Praca z typu double</span><span class="sxs-lookup"><span data-stu-id="94333-177">Work with the double type</span></span>

<span data-ttu-id="94333-178">`double` Podwójnej precyzji liczba zmiennoprzecinkowa reprezentuje typ liczbowy.</span><span class="sxs-lookup"><span data-stu-id="94333-178">The `double` numeric type represents a double-precision floating point number.</span></span> <span data-ttu-id="94333-179">Te warunki mogą być nowe dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="94333-179">Those terms may be new to you.</span></span> <span data-ttu-id="94333-180">A **zmiennoprzecinkowa** numer przydaje się do wyświetlania niecałkowity liczb, które mogą być bardzo duże lub małe wielkości.</span><span class="sxs-lookup"><span data-stu-id="94333-180">A **floating point** number is useful to represent non-integral numbers that may be very large or small in magnitude.</span></span> <span data-ttu-id="94333-181">**Podwójnej precyzji** oznacza, że numery te są przechowywane przy użyciu większą dokładność niż **pojedynczej precyzji**.</span><span class="sxs-lookup"><span data-stu-id="94333-181">**Double-precision** means that these numbers are stored using greater precision than **single-precision**.</span></span> <span data-ttu-id="94333-182">W nowych komputerów jest najczęściej używać podwójnej precyzji niż liczby o pojedynczej precyzji.</span><span class="sxs-lookup"><span data-stu-id="94333-182">On modern computers, it is more common to use double precision than single precision numbers.</span></span>
<span data-ttu-id="94333-183">Przyjrzyjmy się.</span><span class="sxs-lookup"><span data-stu-id="94333-183">Let's explore.</span></span> <span data-ttu-id="94333-184">Dodaj następujący kod i wyświetlić wyniki:</span><span class="sxs-lookup"><span data-stu-id="94333-184">Add the following code and see the result:</span></span>

```csharp
double a = 5;
double b = 4;
double c = 2;
double d = (a  + b) / c;
Console.WriteLine(d);
```

<span data-ttu-id="94333-185">Zwróć uwagę, że odpowiedź zawiera część iloraz.</span><span class="sxs-lookup"><span data-stu-id="94333-185">Notice that the answer includes the decimal portion of the quotient.</span></span> <span data-ttu-id="94333-186">Spróbuj wyrażenia nieco bardziej skomplikowane z symulacyjnych:</span><span class="sxs-lookup"><span data-stu-id="94333-186">Try a slightly more complicated expression with doubles:</span></span>

```csharp
double e = 19;
double f = 23;
double g = 8;
double h = (e  + f) / g;
Console.WriteLine(h);
```

<span data-ttu-id="94333-187">Zakres wartości typu double jest większa niż wartości będące liczbami całkowitymi.</span><span class="sxs-lookup"><span data-stu-id="94333-187">The range of a double value is much greater than integer values.</span></span> <span data-ttu-id="94333-188">Wykonaj następujący kod poniżej co napisanych wykonanej do tej pory:</span><span class="sxs-lookup"><span data-stu-id="94333-188">Try the following code below what you've written so far:</span></span>

```csharp
double max = double.MaxValue;
double min = double.MinValue;
Console.WriteLine($"The range of double is {min} to {max}");
```

<span data-ttu-id="94333-189">Te wartości są drukowany w notacji wykładniczej.</span><span class="sxs-lookup"><span data-stu-id="94333-189">These values are printed out in scientific notation.</span></span> <span data-ttu-id="94333-190">Liczba z lewej strony `E` jest mantysy.</span><span class="sxs-lookup"><span data-stu-id="94333-190">The number to the left of the `E` is the significand.</span></span> <span data-ttu-id="94333-191">Liczba po prawej stronie jest wykładnik, jako potęgi liczby 10.</span><span class="sxs-lookup"><span data-stu-id="94333-191">The number to the right is the exponent, as a power of 10.</span></span> 

<span data-ttu-id="94333-192">Podobnie jak liczbami dziesiętnymi matematyczne symulacyjnych w języku C# mogą mieć błędów zaokrąglania.</span><span class="sxs-lookup"><span data-stu-id="94333-192">Just like decimal numbers in math, doubles in C# can have rounding errors.</span></span> <span data-ttu-id="94333-193">Spróbuj wykonać ten kod:</span><span class="sxs-lookup"><span data-stu-id="94333-193">Try this code:</span></span>

```csharp
double third = 1.0 / 3.0;
Console.WriteLine(third);
```

<span data-ttu-id="94333-194">Należy pamiętać, że `0.3` powtarzające się nie jest dokładnie taka sama jak `1/3`.</span><span class="sxs-lookup"><span data-stu-id="94333-194">You know that `0.3` repeating is not exactly the same as `1/3`.</span></span>

<span data-ttu-id="94333-195">***Challenge***</span><span class="sxs-lookup"><span data-stu-id="94333-195">***Challenge***</span></span>

<span data-ttu-id="94333-196">Spróbuj inne obliczenia z dużą liczbą, małej liczby, mnożenia i dzielenia przy użyciu `double` typu.</span><span class="sxs-lookup"><span data-stu-id="94333-196">Try other calculations with large numbers, small numbers, multiplication and division using the `double` type.</span></span>  <span data-ttu-id="94333-197">Spróbuj bardziej skomplikowane obliczenia.</span><span class="sxs-lookup"><span data-stu-id="94333-197">Try more complicated calculations.</span></span>

<span data-ttu-id="94333-198">Po po długiej pracy z żądaniem, należy przenieść kod napisanych i umieścić go w nowej metody.</span><span class="sxs-lookup"><span data-stu-id="94333-198">After you've spent some time with the challenge, take the code you've written and place it in a new method.</span></span> <span data-ttu-id="94333-199">Nazwa tej nowej metody `WorkWithDoubles`.</span><span class="sxs-lookup"><span data-stu-id="94333-199">Name that new method `WorkWithDoubles`.</span></span>

## <a name="work-with-fixed-point-types"></a><span data-ttu-id="94333-200">Praca z typami stałego punktu</span><span class="sxs-lookup"><span data-stu-id="94333-200">Work with fixed point types</span></span>

<span data-ttu-id="94333-201">W tym samouczku podstawowe typy liczbowe w języku C#: liczb całkowitych i na symulacyjnych.</span><span class="sxs-lookup"><span data-stu-id="94333-201">You've seen the basic numeric types in C#: integers and doubles.</span></span>  <span data-ttu-id="94333-202">Istnieje jeden inny typ, aby dowiedzieć się więcej: `decimal` typu.</span><span class="sxs-lookup"><span data-stu-id="94333-202">There is one other type to learn: the `decimal` type.</span></span> <span data-ttu-id="94333-203">`decimal` Typ ma mniejszy zakres, ale większą dokładność niż `double`.</span><span class="sxs-lookup"><span data-stu-id="94333-203">The `decimal` type has a smaller range but greater precision than `double`.</span></span> <span data-ttu-id="94333-204">Termin **stały punkt** oznacza, że punkt dziesiętny (lub punktu binarnego) nie jest przenoszony.</span><span class="sxs-lookup"><span data-stu-id="94333-204">The term **fixed point** means that the decimal point (or binary point) doesn't move.</span></span> <span data-ttu-id="94333-205">Spójrzmy:</span><span class="sxs-lookup"><span data-stu-id="94333-205">Let's take a look:</span></span>

```csharp
decimal min = decimal.MinValue;
decimal max = decimal.MaxValue;
Console.WriteLine($"The range of the decimal type is {min} to {max}");
```

<span data-ttu-id="94333-206">Należy zauważyć, że zakres jest mniejszy niż `double` typu.</span><span class="sxs-lookup"><span data-stu-id="94333-206">Notice that the range is smaller than the `double` type.</span></span> <span data-ttu-id="94333-207">Możesz zobaczyć większą dokładność typu decimal podejmując następujący kod:</span><span class="sxs-lookup"><span data-stu-id="94333-207">You can see the greater precision with the decimal type by trying the following code:</span></span>

```csharp
double a = 1.0;
double b = 3.0;
Console.WriteLine(a / b);

decimal c = 1.0M;
decimal d = 3.0M;
Console.WriteLine(c / d);
```

<span data-ttu-id="94333-208">`M` Sufiks na numery jest sposób oznacza, że stałą powinien używać `decimal` typu.</span><span class="sxs-lookup"><span data-stu-id="94333-208">The `M` suffix on the numbers is how you indicate that a constant should use the `decimal` type.</span></span>

<span data-ttu-id="94333-209">Należy zauważyć, że obliczenia przy użyciu typu decimal zawiera więcej cyfr z prawej strony punktu dziesiętnego.</span><span class="sxs-lookup"><span data-stu-id="94333-209">Notice that the math using the decimal type has more digits to the right of the decimal point.</span></span> 

<span data-ttu-id="94333-210">***Challenge***</span><span class="sxs-lookup"><span data-stu-id="94333-210">***Challenge***</span></span>

<span data-ttu-id="94333-211">Skoro już znasz różne typy liczbowe pisania kodu, który oblicza obszaru koło którego radius jest 2,50 cm.</span><span class="sxs-lookup"><span data-stu-id="94333-211">Now that you've seen the different numeric types, write code that calculates the area of a circle whose radius is 2.50 centimeters.</span></span> <span data-ttu-id="94333-212">Należy pamiętać, że obszar koła jest radius kwadrat pomnożona przez PI.</span><span class="sxs-lookup"><span data-stu-id="94333-212">Remember that the area of a circle is the radius squared multiplied by PI.</span></span> <span data-ttu-id="94333-213">Jedną wskazówkę: .NET zawiera stałą Pi, <xref:System.Math.PI?displayProperty=nameWithType> używanego dla tej wartości.</span><span class="sxs-lookup"><span data-stu-id="94333-213">One hint: .NET contains a constant for PI, <xref:System.Math.PI?displayProperty=nameWithType> that you can use for that value.</span></span> 

<span data-ttu-id="94333-214">Należy uzyskać odpowiedzi od 19 do 20.</span><span class="sxs-lookup"><span data-stu-id="94333-214">You should get an answer between 19 and 20.</span></span>
<span data-ttu-id="94333-215">Można sprawdzić odpowiedzi przez [patrzeć Zakończono przykładowy kod w witrynie GitHub](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106)</span><span class="sxs-lookup"><span data-stu-id="94333-215">You can check your answer by [looking at the finished sample code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/numbers-quickstart/Program.cs#L104-L106)</span></span>

<span data-ttu-id="94333-216">Jeśli chcesz, spróbuj niektóre inne formuły.</span><span class="sxs-lookup"><span data-stu-id="94333-216">Try some other formulas if you'd like.</span></span> 

<span data-ttu-id="94333-217">Zakończono Szybki Start "numery w języku C#".</span><span class="sxs-lookup"><span data-stu-id="94333-217">You've completed the "Numbers in C#" quickstart.</span></span> <span data-ttu-id="94333-218">Można kontynuować [gałęzie i pętli](branches-and-loops-local.md) szybkiego startu w środowisku projektowania.</span><span class="sxs-lookup"><span data-stu-id="94333-218">You can continue with the [Branches and loops](branches-and-loops-local.md) quickstart in your own development environment.</span></span>

<span data-ttu-id="94333-219">Użytkownik może dowiedzieć się więcej o numery w języku C# w następujących tematach:</span><span class="sxs-lookup"><span data-stu-id="94333-219">You can learn more about numbers in C# in the following topics:</span></span>

<span data-ttu-id="94333-220">[Tabela typów całkowitych](../language-reference/keywords/integral-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="94333-220">[Integral Types Table](../language-reference/keywords/integral-types-table.md) </span></span>  
<span data-ttu-id="94333-221">[Tabela typów zmiennoprzecinkowych](../language-reference/keywords/floating-point-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="94333-221">[Floating-Point Types Table](../language-reference/keywords/floating-point-types-table.md) </span></span>  
<span data-ttu-id="94333-222">[Tabela typów wbudowanych](../language-reference/keywords/built-in-types-table.md) </span><span class="sxs-lookup"><span data-stu-id="94333-222">[Built-In Types Table](../language-reference/keywords/built-in-types-table.md) </span></span>  
<span data-ttu-id="94333-223">[Tabela niejawnych konwersji liczbowych](../language-reference/keywords/implicit-numeric-conversions-table.md) </span><span class="sxs-lookup"><span data-stu-id="94333-223">[Implicit Numeric Conversions Table](../language-reference/keywords/implicit-numeric-conversions-table.md) </span></span>  
[<span data-ttu-id="94333-224">Tabela jawnych konwersji liczbowych</span><span class="sxs-lookup"><span data-stu-id="94333-224">Explicit Numeric Conversions Table</span></span>](../language-reference/keywords/explicit-numeric-conversions-table.md)


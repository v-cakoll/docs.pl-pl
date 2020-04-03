---
title: Praca z kolekcjami — wprowadzenie do samouczka C#
description: Dowiedz się C# eksplorując List kolekcji w tym samouczku.
ms.date: 10/13/2017
ms.custom: mvc
ms.openlocfilehash: 554a4601157a7d4b873c22a46ee72b6601fc36d7
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635653"
---
# <a name="learn-to-manage-data-collections-using-the-generic-list-type"></a><span data-ttu-id="76710-103">Dowiedz się, jak zarządzać zbieraniem danych przy użyciu typu listy ogólnej</span><span class="sxs-lookup"><span data-stu-id="76710-103">Learn to manage data collections using the generic list type</span></span>

<span data-ttu-id="76710-104">Ten samouczek wprowadzający zawiera wprowadzenie do języka C# <xref:System.Collections.Generic.List%601> i podstawy klasy.</span><span class="sxs-lookup"><span data-stu-id="76710-104">This introductory tutorial provides an introduction to the C# language and the basics of the <xref:System.Collections.Generic.List%601> class.</span></span>

<span data-ttu-id="76710-105">W tym samouczku oczekuje się, że masz komputer, którego można użyć do tworzenia.</span><span class="sxs-lookup"><span data-stu-id="76710-105">This tutorial expects you to have a machine you can use for development.</span></span> <span data-ttu-id="76710-106">W samouczku .NET [Hello World w ciągu 10 minut](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) są instrukcje dotyczące konfigurowania lokalnego środowiska programistycznego w systemach Windows, Linux lub macOS.</span><span class="sxs-lookup"><span data-stu-id="76710-106">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span> <span data-ttu-id="76710-107">Szybki przegląd poleceń, których będziesz używać, znajduje się w [części Zapoznaj się z narzędziami programistycznymi](local-environment.md), z łączami do więcej szczegółów.</span><span class="sxs-lookup"><span data-stu-id="76710-107">A quick overview of the commands you'll use is in [Become familiar with the development tools](local-environment.md), with links to more details.</span></span>

## <a name="a-basic-list-example"></a><span data-ttu-id="76710-108">Przykład listy podstawowej</span><span class="sxs-lookup"><span data-stu-id="76710-108">A basic list example</span></span>

<span data-ttu-id="76710-109">Tworzenie katalogu o nazwie *lista-samouczek*.</span><span class="sxs-lookup"><span data-stu-id="76710-109">Create a directory named *list-tutorial*.</span></span> <span data-ttu-id="76710-110">Zrób bieżący katalog i `dotnet new console`uruchom program .</span><span class="sxs-lookup"><span data-stu-id="76710-110">Make that the current directory and run `dotnet new console`.</span></span>

<span data-ttu-id="76710-111">Otwórz *Program.cs* w ulubionym edytorze i zastąp istniejący kod następującymi:</span><span class="sxs-lookup"><span data-stu-id="76710-111">Open *Program.cs* in your favorite editor, and replace the existing code with the following:</span></span>

```csharp
using System;
using System.Collections.Generic;

namespace list_tutorial
{
    class Program
    {
        static void Main(string[] args)
        {
            var names = new List<string> { "<name>", "Ana", "Felipe" };
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }
        }
    }
}
```

<span data-ttu-id="76710-112">Zamień `<name>` swoje imię i nazwisko.</span><span class="sxs-lookup"><span data-stu-id="76710-112">Replace `<name>` with your name.</span></span> <span data-ttu-id="76710-113">Zapisz plik *Program.cs*.</span><span class="sxs-lookup"><span data-stu-id="76710-113">Save *Program.cs*.</span></span> <span data-ttu-id="76710-114">Wpisz `dotnet run` w oknie konsoli, aby spróbować.</span><span class="sxs-lookup"><span data-stu-id="76710-114">Type `dotnet run` in your console window to try it.</span></span>

<span data-ttu-id="76710-115">Właśnie utworzono listę ciągów, dodano trzy nazwy do tej listy i wydrukowano nazwy we wszystkich caps.</span><span class="sxs-lookup"><span data-stu-id="76710-115">You've just created a list of strings, added three names to that list, and printed out the names in all CAPS.</span></span> <span data-ttu-id="76710-116">Używasz pojęć, które zostały nauczone we wcześniejszych samouczkach, aby zapętlać listę.</span><span class="sxs-lookup"><span data-stu-id="76710-116">You're using concepts that you've learned in earlier tutorials to loop through the list.</span></span>

<span data-ttu-id="76710-117">Kod do wyświetlania nazw korzysta z funkcji [interpolacji ciągu.](../../language-reference/tokens/interpolated.md)</span><span class="sxs-lookup"><span data-stu-id="76710-117">The code to display names makes use of the [string interpolation](../../language-reference/tokens/interpolated.md) feature.</span></span>  <span data-ttu-id="76710-118">Po poprzedzić `string` `$` znak, można osadzić kod C# w deklaracji ciągu.</span><span class="sxs-lookup"><span data-stu-id="76710-118">When you precede a `string` with the `$` character, you can embed C# code in the string declaration.</span></span> <span data-ttu-id="76710-119">Rzeczywisty ciąg zastępuje ten kod Języka C# wartością, którą generuje.</span><span class="sxs-lookup"><span data-stu-id="76710-119">The actual string replaces that C# code with the value it generates.</span></span> <span data-ttu-id="76710-120">W tym przykładzie zastępuje `{name.ToUpper()}` z każdej nazwy, konwertowane na <xref:System.String.ToUpper%2A> wielkie litery, ponieważ metoda została wywołana.</span><span class="sxs-lookup"><span data-stu-id="76710-120">In this example, it replaces the `{name.ToUpper()}` with each name, converted to capital letters, because you called the <xref:System.String.ToUpper%2A> method.</span></span>

<span data-ttu-id="76710-121">Kontynuujmy odkrywanie.</span><span class="sxs-lookup"><span data-stu-id="76710-121">Let's keep exploring.</span></span>

## <a name="modify-list-contents"></a><span data-ttu-id="76710-122">Modyfikowanie zawartości listy</span><span class="sxs-lookup"><span data-stu-id="76710-122">Modify list contents</span></span>

<span data-ttu-id="76710-123">Utworzona kolekcja używa <xref:System.Collections.Generic.List%601> tego typu.</span><span class="sxs-lookup"><span data-stu-id="76710-123">The collection you created uses the <xref:System.Collections.Generic.List%601> type.</span></span> <span data-ttu-id="76710-124">Ten typ przechowuje sekwencje elementów.</span><span class="sxs-lookup"><span data-stu-id="76710-124">This type stores sequences of elements.</span></span> <span data-ttu-id="76710-125">Należy określić typ elementów między nawiasami kątowymi.</span><span class="sxs-lookup"><span data-stu-id="76710-125">You specify the type of the elements between the angle brackets.</span></span>

<span data-ttu-id="76710-126">Jednym z ważnych <xref:System.Collections.Generic.List%601> aspektów tego typu jest to, że może rosnąć lub zmniejszać, umożliwiając dodawanie lub usuwanie elementów.</span><span class="sxs-lookup"><span data-stu-id="76710-126">One important aspect of this <xref:System.Collections.Generic.List%601> type is that it can grow or shrink, enabling you to add or remove elements.</span></span> <span data-ttu-id="76710-127">Dodaj ten kod `}` przed `Main` zamknięciem w metodzie:</span><span class="sxs-lookup"><span data-stu-id="76710-127">Add this code before the closing `}` in the `Main` method:</span></span>

```csharp
Console.WriteLine();
names.Add("Maria");
names.Add("Bill");
names.Remove("Ana");
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

<span data-ttu-id="76710-128">Dodano jeszcze dwie nazwy na końcu listy.</span><span class="sxs-lookup"><span data-stu-id="76710-128">You've added two more names to the end of the list.</span></span> <span data-ttu-id="76710-129">Usunięto również jeden.</span><span class="sxs-lookup"><span data-stu-id="76710-129">You've also removed one as well.</span></span> <span data-ttu-id="76710-130">Zapisz plik i `dotnet run` wpisz, aby go wypróbować.</span><span class="sxs-lookup"><span data-stu-id="76710-130">Save the file, and type `dotnet run` to try it.</span></span>

<span data-ttu-id="76710-131">Umożliwia <xref:System.Collections.Generic.List%601> odwoływanie się do poszczególnych elementów przez **indeks,** jak również.</span><span class="sxs-lookup"><span data-stu-id="76710-131">The <xref:System.Collections.Generic.List%601> enables you to reference individual items by **index** as well.</span></span> <span data-ttu-id="76710-132">Umieść indeks między `[` `]` i tokenów po nazwie listy.</span><span class="sxs-lookup"><span data-stu-id="76710-132">You place the index between `[` and `]` tokens following the list name.</span></span> <span data-ttu-id="76710-133">C# używa 0 dla pierwszego indeksu.</span><span class="sxs-lookup"><span data-stu-id="76710-133">C# uses 0 for the first index.</span></span> <span data-ttu-id="76710-134">Dodaj ten kod bezpośrednio pod kodem, który właśnie dodałeś i wypróbuj go:</span><span class="sxs-lookup"><span data-stu-id="76710-134">Add this code directly below the code you just added and try it:</span></span>

```csharp
Console.WriteLine($"My name is {names[0]}");
Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");
```

<span data-ttu-id="76710-135">Nie można uzyskać dostępu do indeksu poza końcem listy.</span><span class="sxs-lookup"><span data-stu-id="76710-135">You cannot access an index beyond the end of the list.</span></span> <span data-ttu-id="76710-136">Pamiętaj, że indeksy zaczynają się od 0, więc największy prawidłowy indeks jest o jeden mniejszy niż liczba elementów na liście.</span><span class="sxs-lookup"><span data-stu-id="76710-136">Remember that indices start at 0, so the largest valid index is one less than the number of items in the list.</span></span> <span data-ttu-id="76710-137">Można sprawdzić, jak długo lista <xref:System.Collections.Generic.List%601.Count%2A> jest przy użyciu właściwości.</span><span class="sxs-lookup"><span data-stu-id="76710-137">You can check how long the list is using the <xref:System.Collections.Generic.List%601.Count%2A> property.</span></span> <span data-ttu-id="76710-138">Dodaj następujący kod na końcu Main metody:</span><span class="sxs-lookup"><span data-stu-id="76710-138">Add the following code at the end of the Main method:</span></span>

```csharp
Console.WriteLine($"The list has {names.Count} people in it");
 ```

<span data-ttu-id="76710-139">Zapisz plik i `dotnet run` wpisz ponownie, aby wyświetlić wyniki.</span><span class="sxs-lookup"><span data-stu-id="76710-139">Save the file, and type `dotnet run` again to see the results.</span></span>

## <a name="search-and-sort-lists"></a><span data-ttu-id="76710-140">Wyszukiwanie i sortowanie list</span><span class="sxs-lookup"><span data-stu-id="76710-140">Search and sort lists</span></span>

<span data-ttu-id="76710-141">Nasze przykłady używają stosunkowo małych list, ale aplikacje często mogą tworzyć listy z wieloma innymi elementami, czasami numerując w tysiącach.</span><span class="sxs-lookup"><span data-stu-id="76710-141">Our samples use relatively small lists, but your applications may often create lists with many more elements, sometimes numbering in the thousands.</span></span> <span data-ttu-id="76710-142">Aby znaleźć elementy w tych większych kolekcjach, należy przeszukać listę różnych elementów.</span><span class="sxs-lookup"><span data-stu-id="76710-142">To find elements in these larger collections, you need to search the list for different items.</span></span> <span data-ttu-id="76710-143">Metoda <xref:System.Collections.Generic.List%601.IndexOf%2A> wyszukuje towar i zwraca indeks towaru.</span><span class="sxs-lookup"><span data-stu-id="76710-143">The <xref:System.Collections.Generic.List%601.IndexOf%2A> method searches for an item and returns the index of the item.</span></span> <span data-ttu-id="76710-144">Dodaj ten kod na `Main` dole metody:</span><span class="sxs-lookup"><span data-stu-id="76710-144">Add this code to the bottom of your `Main` method:</span></span>

```csharp
var index = names.IndexOf("Felipe");
if (index == -1)
{
    Console.WriteLine($"When an item is not found, IndexOf returns {index}");
}
else
{
    Console.WriteLine($"The name {names[index]} is at index {index}");
}

index = names.IndexOf("Not Found");
if (index == -1)
{
    Console.WriteLine($"When an item is not found, IndexOf returns {index}");
}
else
{
    Console.WriteLine($"The name {names[index]} is at index {index}");

}
```

<span data-ttu-id="76710-145">Elementy na liście można również sortować.</span><span class="sxs-lookup"><span data-stu-id="76710-145">The items in your list can be sorted as well.</span></span> <span data-ttu-id="76710-146">Metoda <xref:System.Collections.Generic.List%601.Sort%2A> sortuje wszystkie elementy na liście w normalnej kolejności (alfabetycznie w przypadku ciągów).</span><span class="sxs-lookup"><span data-stu-id="76710-146">The <xref:System.Collections.Generic.List%601.Sort%2A> method sorts all the items in the list in their normal order (alphabetically in the case of strings).</span></span> <span data-ttu-id="76710-147">Dodaj ten kod na `Main` dole naszej metody:</span><span class="sxs-lookup"><span data-stu-id="76710-147">Add this code to the bottom of our `Main` method:</span></span>

```csharp
names.Sort();
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

<span data-ttu-id="76710-148">Zapisz plik i `dotnet run` wpisz, aby wypróbować tę najnowszą wersję.</span><span class="sxs-lookup"><span data-stu-id="76710-148">Save the file and type `dotnet run` to try this latest version.</span></span>

<span data-ttu-id="76710-149">Przed rozpoczęciem następnej sekcji przenieśmy bieżący kod do osobnej metody.</span><span class="sxs-lookup"><span data-stu-id="76710-149">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="76710-150">To ułatwia rozpoczęcie pracy z nowym przykładem.</span><span class="sxs-lookup"><span data-stu-id="76710-150">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="76710-151">Zmień nazwę `Main` metody `WorkingWithStrings` i napisz `Main` nową `WorkingWithStrings`metodę, która wywołuje .</span><span class="sxs-lookup"><span data-stu-id="76710-151">Rename your `Main` method to `WorkingWithStrings` and write a new `Main` method that calls `WorkingWithStrings`.</span></span> <span data-ttu-id="76710-152">Po zakończeniu kod powinien wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="76710-152">When you have finished, your code should look like this:</span></span>

```csharp
using System;
using System.Collections.Generic;

namespace list_tutorial
{
    class Program
    {
        static void Main(string[] args)
        {
            WorkingWithStrings();
        }

        static void WorkingWithStrings()
        {
            var names = new List<string> { "<name>", "Ana", "Felipe" };
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }

            Console.WriteLine();
            names.Add("Maria");
            names.Add("Bill");
            names.Remove("Ana");
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }

            Console.WriteLine($"My name is {names[0]}");
            Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");

            Console.WriteLine($"The list has {names.Count} people in it");

            var index = names.IndexOf("Felipe");
            if (index == -1)
            {
                Console.WriteLine($"When an item is not found, IndexOf returns {index}");
            }
            else
            {
                Console.WriteLine($"The name {names[index]} is at index {index}");
            }

            index = names.IndexOf("Not Found");
            if (index == -1)
            {
                Console.WriteLine($"When an item is not found, IndexOf returns {index}");
            }
            else
            {
                Console.WriteLine($"The name {names[index]} is at index {index}");

            }

            names.Sort();
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }
        }
    }
}
```

## <a name="lists-of-other-types"></a><span data-ttu-id="76710-153">Listy innych typów</span><span class="sxs-lookup"><span data-stu-id="76710-153">Lists of other types</span></span>

<span data-ttu-id="76710-154">Do tej pory `string` używałeś tego typu na listach.</span><span class="sxs-lookup"><span data-stu-id="76710-154">You've been using the `string` type in lists so far.</span></span> <span data-ttu-id="76710-155">Zróbmy <xref:System.Collections.Generic.List%601> przy użyciu innego typu.</span><span class="sxs-lookup"><span data-stu-id="76710-155">Let's make a <xref:System.Collections.Generic.List%601> using a different type.</span></span> <span data-ttu-id="76710-156">Zbudujmy zestaw liczb.</span><span class="sxs-lookup"><span data-stu-id="76710-156">Let's build a set of numbers.</span></span>

<span data-ttu-id="76710-157">Dodaj następujące elementy na dole `Main` nowej metody:</span><span class="sxs-lookup"><span data-stu-id="76710-157">Add the following to the bottom of your new `Main` method:</span></span>

```csharp
var fibonacciNumbers = new List<int> {1, 1};
```

<span data-ttu-id="76710-158">Tworzy listę liczby całkowite i ustawia dwie pierwsze liczby całkowite na wartość 1.</span><span class="sxs-lookup"><span data-stu-id="76710-158">That creates a list of integers, and sets the first two integers to the value 1.</span></span> <span data-ttu-id="76710-159">Są to dwie pierwsze wartości *sekwencji Fibonacciego*, sekwencja liczb.</span><span class="sxs-lookup"><span data-stu-id="76710-159">These are the first two values of a *Fibonacci Sequence*, a sequence of numbers.</span></span> <span data-ttu-id="76710-160">Każdy następny numer Fibonacciego znajduje się, biorąc sumę poprzednich dwóch liczb.</span><span class="sxs-lookup"><span data-stu-id="76710-160">Each next Fibonacci number is found by taking the sum of the previous two numbers.</span></span> <span data-ttu-id="76710-161">Dodaj ten kod:</span><span class="sxs-lookup"><span data-stu-id="76710-161">Add this code:</span></span>

```csharp
var previous = fibonacciNumbers[fibonacciNumbers.Count - 1];
var previous2 = fibonacciNumbers[fibonacciNumbers.Count - 2];

fibonacciNumbers.Add(previous + previous2);

foreach (var item in fibonacciNumbers)
    Console.WriteLine(item);
```

<span data-ttu-id="76710-162">Zapisz plik i `dotnet run` wpisz, aby zobaczyć wyniki.</span><span class="sxs-lookup"><span data-stu-id="76710-162">Save the file and type `dotnet run` to see the results.</span></span>

> [!TIP]
> <span data-ttu-id="76710-163">Aby skupić się tylko na tej sekcji, `WorkingWithStrings();`możesz skomentować kod, który wywołuje .</span><span class="sxs-lookup"><span data-stu-id="76710-163">To concentrate on just this section, you can comment out the code that calls `WorkingWithStrings();`.</span></span> <span data-ttu-id="76710-164">Wystarczy umieścić `/` dwa znaki przed wezwaniem `// WorkingWithStrings();`w ten sposób: .</span><span class="sxs-lookup"><span data-stu-id="76710-164">Just put two `/` characters in front of the call like this:  `// WorkingWithStrings();`.</span></span>

## <a name="challenge"></a><span data-ttu-id="76710-165">Wyzwanie</span><span class="sxs-lookup"><span data-stu-id="76710-165">Challenge</span></span>

<span data-ttu-id="76710-166">Sprawdź, czy możesz połączyć niektóre z pojęć z tej i wcześniejszych lekcji.</span><span class="sxs-lookup"><span data-stu-id="76710-166">See if you can put together some of the concepts from this and earlier lessons.</span></span> <span data-ttu-id="76710-167">Rozwiń to, co zbudowałeś do tej pory dzięki Liczbom Fibonacciego.</span><span class="sxs-lookup"><span data-stu-id="76710-167">Expand on what you've built so far with Fibonacci Numbers.</span></span> <span data-ttu-id="76710-168">Spróbuj napisać kod, aby wygenerować pierwsze 20 liczb w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="76710-168">Try to write the code to generate the first 20 numbers in the sequence.</span></span> <span data-ttu-id="76710-169">(Jako wskazówka, 20 numer Fibonacciego jest 6765.)</span><span class="sxs-lookup"><span data-stu-id="76710-169">(As a hint, the 20th Fibonacci number is 6765.)</span></span>

## <a name="complete-challenge"></a><span data-ttu-id="76710-170">Ukończenie wyzwania</span><span class="sxs-lookup"><span data-stu-id="76710-170">Complete challenge</span></span>

<span data-ttu-id="76710-171">Możesz zobaczyć przykładowe [rozwiązanie, patrząc na gotowy przykładowy kod na GitHub](https://github.com/dotnet/samples/tree/master/csharp/list-quickstart/Program.cs#L13-L23).</span><span class="sxs-lookup"><span data-stu-id="76710-171">You can see an example solution by [looking at the finished sample code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/list-quickstart/Program.cs#L13-L23).</span></span>

<span data-ttu-id="76710-172">Przy każdej iteracji pętli bierzesz dwie ostatnie liczby całkowite na liście, sumując je i dodając tę wartość do listy.</span><span class="sxs-lookup"><span data-stu-id="76710-172">With each iteration of the loop, you're taking the last two integers in the list, summing them, and adding that value to the list.</span></span> <span data-ttu-id="76710-173">Pętla powtarza się, dopóki nie dodasz 20 elementów do listy.</span><span class="sxs-lookup"><span data-stu-id="76710-173">The loop repeats until you've added 20 items to the list.</span></span>

<span data-ttu-id="76710-174">Gratulacje, ukończyłeś samouczek listy.</span><span class="sxs-lookup"><span data-stu-id="76710-174">Congratulations, you've completed the list tutorial.</span></span> <span data-ttu-id="76710-175">Możesz kontynuować wprowadzenie [do zajęć](introduction-to-classes.md) samouczek w swoim własnym środowisku programistycznym.</span><span class="sxs-lookup"><span data-stu-id="76710-175">You can continue with the [Introduction to classes](introduction-to-classes.md) tutorial in your own development environment.</span></span>

<span data-ttu-id="76710-176">Więcej informacji na temat `List` pracy z typem można uzyskać w artykule [przewodnika .NET](../../../standard/index.yml) dotyczącymi [kolekcji](../../../standard/collections/index.md).</span><span class="sxs-lookup"><span data-stu-id="76710-176">You can learn more about working with the `List` type in the [.NET guide](../../../standard/index.yml) article on [collections](../../../standard/collections/index.md).</span></span> <span data-ttu-id="76710-177">Dowiesz się również o wielu innych typach kolekcji.</span><span class="sxs-lookup"><span data-stu-id="76710-177">You'll also learn about many other collection types.</span></span>

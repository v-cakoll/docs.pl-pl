---
title: Praca z kolekcjami — wprowadzenie do samouczka języka C#
description: Dowiedz się C# eksplorując Listy kolekcji w tym samouczku.
ms.date: 10/13/2017
ms.custom: mvc
ms.openlocfilehash: 25d20de2eae8ad1f544fa17553c173a6141ae464
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156692"
---
# <a name="learn-to-manage-data-collections-using-the-generic-list-type"></a><span data-ttu-id="cb688-103">Dowiedz się, jak zarządzać zbiorami danych przy użyciu ogólnego typu listy</span><span class="sxs-lookup"><span data-stu-id="cb688-103">Learn to manage data collections using the generic list type</span></span>

<span data-ttu-id="cb688-104">Ten instruktażowy samouczek zawiera wprowadzenie do języka <xref:System.Collections.Generic.List%601> Języka C# i podstawy klasy.</span><span class="sxs-lookup"><span data-stu-id="cb688-104">This introductory tutorial provides an introduction to the C# language and the basics of the <xref:System.Collections.Generic.List%601> class.</span></span>

<span data-ttu-id="cb688-105">Ten samouczek oczekuje, że masz komputer, którego można użyć do tworzenia.</span><span class="sxs-lookup"><span data-stu-id="cb688-105">This tutorial expects you to have a machine you can use for development.</span></span> <span data-ttu-id="cb688-106">Samouczek .NET [Hello World w 10 minut](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) zawiera instrukcje dotyczące konfigurowania lokalnego środowiska programistycznego w systemie Windows, Linux lub macOS.</span><span class="sxs-lookup"><span data-stu-id="cb688-106">The .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro) has instructions for setting up your local development environment on Windows, Linux, or macOS.</span></span> <span data-ttu-id="cb688-107">Szybki przegląd poleceń, których będziesz używać, znajduje się w [obszarze Zaznajomij się z narzędziami programistycznymi](local-environment.md)z łączami do więcej szczegółów.</span><span class="sxs-lookup"><span data-stu-id="cb688-107">A quick overview of the commands you'll use is in [Become familiar with the development tools](local-environment.md), with links to more details.</span></span>

## <a name="a-basic-list-example"></a><span data-ttu-id="cb688-108">Przykład listy podstawowej</span><span class="sxs-lookup"><span data-stu-id="cb688-108">A basic list example</span></span>

<span data-ttu-id="cb688-109">Utwórz katalog o nazwie *list-tutorial*.</span><span class="sxs-lookup"><span data-stu-id="cb688-109">Create a directory named *list-tutorial*.</span></span> <span data-ttu-id="cb688-110">Upewnij się, że `dotnet new console`bieżący katalog i uruchom .</span><span class="sxs-lookup"><span data-stu-id="cb688-110">Make that the current directory and run `dotnet new console`.</span></span>

<span data-ttu-id="cb688-111">Otwórz *Program.cs* w ulubionym edytorze i zastąp istniejący kod następującymi elementami:</span><span class="sxs-lookup"><span data-stu-id="cb688-111">Open *Program.cs* in your favorite editor, and replace the existing code with the following:</span></span>

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

<span data-ttu-id="cb688-112">Zastąp `<name>` swoim imieniem i nazwiskiem.</span><span class="sxs-lookup"><span data-stu-id="cb688-112">Replace `<name>` with your name.</span></span> <span data-ttu-id="cb688-113">Zapisz plik *Program.cs*.</span><span class="sxs-lookup"><span data-stu-id="cb688-113">Save *Program.cs*.</span></span> <span data-ttu-id="cb688-114">Wpisz `dotnet run` okno konsoli, aby spróbować.</span><span class="sxs-lookup"><span data-stu-id="cb688-114">Type `dotnet run` in your console window to try it.</span></span>

<span data-ttu-id="cb688-115">Właśnie utworzono listę ciągów, dodano trzy nazwy do tej listy i wydrukowano nazwy we wszystkich caps.</span><span class="sxs-lookup"><span data-stu-id="cb688-115">You've just created a list of strings, added three names to that list, and printed out the names in all CAPS.</span></span> <span data-ttu-id="cb688-116">Używasz pojęć, które zostały nauczone we wcześniejszych samouczkach do pętli za pośrednictwem listy.</span><span class="sxs-lookup"><span data-stu-id="cb688-116">You're using concepts that you've learned in earlier tutorials to loop through the list.</span></span>

<span data-ttu-id="cb688-117">Kod do wyświetlania nazw korzysta z funkcji [interpolacji ciągów.](../../language-reference/tokens/interpolated.md)</span><span class="sxs-lookup"><span data-stu-id="cb688-117">The code to display names makes use of the [string interpolation](../../language-reference/tokens/interpolated.md) feature.</span></span>  <span data-ttu-id="cb688-118">Poprzedzić `string` znak, `$` można osadzić kod C# w deklaracji ciągu.</span><span class="sxs-lookup"><span data-stu-id="cb688-118">When you precede a `string` with the `$` character, you can embed C# code in the string declaration.</span></span> <span data-ttu-id="cb688-119">Rzeczywisty ciąg zastępuje ten kod C# wartością, którą generuje.</span><span class="sxs-lookup"><span data-stu-id="cb688-119">The actual string replaces that C# code with the value it generates.</span></span> <span data-ttu-id="cb688-120">W tym przykładzie zastępuje `{name.ToUpper()}` z każdej nazwy, konwertowane na wielkie <xref:System.String.ToUpper%2A> litery, ponieważ nazywa się metodę.</span><span class="sxs-lookup"><span data-stu-id="cb688-120">In this example, it replaces the `{name.ToUpper()}` with each name, converted to capital letters, because you called the <xref:System.String.ToUpper%2A> method.</span></span>

<span data-ttu-id="cb688-121">Badajmy dalej.</span><span class="sxs-lookup"><span data-stu-id="cb688-121">Let's keep exploring.</span></span>

## <a name="modify-list-contents"></a><span data-ttu-id="cb688-122">Modyfikowanie zawartości listy</span><span class="sxs-lookup"><span data-stu-id="cb688-122">Modify list contents</span></span>

<span data-ttu-id="cb688-123">Kolekcja, którą utworzyłeś <xref:System.Collections.Generic.List%601> używa tego typu.</span><span class="sxs-lookup"><span data-stu-id="cb688-123">The collection you created uses the <xref:System.Collections.Generic.List%601> type.</span></span> <span data-ttu-id="cb688-124">Ten typ przechowuje sekwencje elementów.</span><span class="sxs-lookup"><span data-stu-id="cb688-124">This type stores sequences of elements.</span></span> <span data-ttu-id="cb688-125">Typ elementów między nawiasami kątowymi.</span><span class="sxs-lookup"><span data-stu-id="cb688-125">You specify the type of the elements between the angle brackets.</span></span>

<span data-ttu-id="cb688-126">Jednym z ważnych <xref:System.Collections.Generic.List%601> aspektów tego typu jest to, że można go rozwijać lub zmniejszać, umożliwiając dodawanie lub usuwanie elementów.</span><span class="sxs-lookup"><span data-stu-id="cb688-126">One important aspect of this <xref:System.Collections.Generic.List%601> type is that it can grow or shrink, enabling you to add or remove elements.</span></span> <span data-ttu-id="cb688-127">Dodaj ten kod `}` przed `Main` zamknięciem w metodzie:</span><span class="sxs-lookup"><span data-stu-id="cb688-127">Add this code before the closing `}` in the `Main` method:</span></span>

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

<span data-ttu-id="cb688-128">Na końcu listy dodano jeszcze dwie nazwy.</span><span class="sxs-lookup"><span data-stu-id="cb688-128">You've added two more names to the end of the list.</span></span> <span data-ttu-id="cb688-129">Usunięto również jeden.</span><span class="sxs-lookup"><span data-stu-id="cb688-129">You've also removed one as well.</span></span> <span data-ttu-id="cb688-130">Zapisz plik i `dotnet run` wpisz, aby go wypróbować.</span><span class="sxs-lookup"><span data-stu-id="cb688-130">Save the file, and type `dotnet run` to try it.</span></span>

<span data-ttu-id="cb688-131">Umożliwia <xref:System.Collections.Generic.List%601> odwoływanie się do poszczególnych elementów przez **indeks,** jak również.</span><span class="sxs-lookup"><span data-stu-id="cb688-131">The <xref:System.Collections.Generic.List%601> enables you to reference individual items by **index** as well.</span></span> <span data-ttu-id="cb688-132">Należy umieścić indeks `[` `]` między i tokeny po nazwie listy.</span><span class="sxs-lookup"><span data-stu-id="cb688-132">You place the index between `[` and `]` tokens following the list name.</span></span> <span data-ttu-id="cb688-133">C# używa 0 dla pierwszego indeksu.</span><span class="sxs-lookup"><span data-stu-id="cb688-133">C# uses 0 for the first index.</span></span> <span data-ttu-id="cb688-134">Dodaj ten kod bezpośrednio pod dodanym kodem i spróbuj go:</span><span class="sxs-lookup"><span data-stu-id="cb688-134">Add this code directly below the code you just added and try it:</span></span>

```csharp
Console.WriteLine($"My name is {names[0]}");
Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");
```

<span data-ttu-id="cb688-135">Nie można uzyskać dostępu do indeksu poza końcem listy.</span><span class="sxs-lookup"><span data-stu-id="cb688-135">You cannot access an index beyond the end of the list.</span></span> <span data-ttu-id="cb688-136">Pamiętaj, że indeksy zaczynają się od 0, więc największy prawidłowy indeks jest o jeden mniejszy niż liczba pozycji na liście.</span><span class="sxs-lookup"><span data-stu-id="cb688-136">Remember that indices start at 0, so the largest valid index is one less than the number of items in the list.</span></span> <span data-ttu-id="cb688-137">Można sprawdzić, jak długo lista <xref:System.Collections.Generic.List%601.Count%2A> jest przy użyciu właściwości.</span><span class="sxs-lookup"><span data-stu-id="cb688-137">You can check how long the list is using the <xref:System.Collections.Generic.List%601.Count%2A> property.</span></span> <span data-ttu-id="cb688-138">Dodaj następujący kod na końcu Metody Głównej:</span><span class="sxs-lookup"><span data-stu-id="cb688-138">Add the following code at the end of the Main method:</span></span>

```csharp
Console.WriteLine($"The list has {names.Count} people in it");
 ```

<span data-ttu-id="cb688-139">Zapisz plik i `dotnet run` wpisz ponownie, aby zobaczyć wyniki.</span><span class="sxs-lookup"><span data-stu-id="cb688-139">Save the file, and type `dotnet run` again to see the results.</span></span>

## <a name="search-and-sort-lists"></a><span data-ttu-id="cb688-140">Wyszukiwanie i sortowanie list</span><span class="sxs-lookup"><span data-stu-id="cb688-140">Search and sort lists</span></span>

<span data-ttu-id="cb688-141">Nasze przykłady używają stosunkowo małych list, ale aplikacje często mogą tworzyć listy z wieloma innymi elementami, czasami numerowane w tysiącach.</span><span class="sxs-lookup"><span data-stu-id="cb688-141">Our samples use relatively small lists, but your applications may often create lists with many more elements, sometimes numbering in the thousands.</span></span> <span data-ttu-id="cb688-142">Aby znaleźć elementy w tych większych kolekcji, należy wyszukać listę różnych elementów.</span><span class="sxs-lookup"><span data-stu-id="cb688-142">To find elements in these larger collections, you need to search the list for different items.</span></span> <span data-ttu-id="cb688-143">Metoda <xref:System.Collections.Generic.List%601.IndexOf%2A> wyszukuje element i zwraca indeks elementu.</span><span class="sxs-lookup"><span data-stu-id="cb688-143">The <xref:System.Collections.Generic.List%601.IndexOf%2A> method searches for an item and returns the index of the item.</span></span> <span data-ttu-id="cb688-144">Dodaj ten kod do `Main` dołu metody:</span><span class="sxs-lookup"><span data-stu-id="cb688-144">Add this code to the bottom of your `Main` method:</span></span>

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

<span data-ttu-id="cb688-145">Elementy na liście można również sortować.</span><span class="sxs-lookup"><span data-stu-id="cb688-145">The items in your list can be sorted as well.</span></span> <span data-ttu-id="cb688-146">Metoda <xref:System.Collections.Generic.List%601.Sort%2A> sortuje wszystkie elementy na liście w normalnej kolejności (alfabetycznie w przypadku ciągów).</span><span class="sxs-lookup"><span data-stu-id="cb688-146">The <xref:System.Collections.Generic.List%601.Sort%2A> method sorts all the items in the list in their normal order (alphabetically in the case of strings).</span></span> <span data-ttu-id="cb688-147">Dodaj ten kod do `Main` dolnej części naszej metody:</span><span class="sxs-lookup"><span data-stu-id="cb688-147">Add this code to the bottom of our `Main` method:</span></span>

```csharp
names.Sort();
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

<span data-ttu-id="cb688-148">Zapisz plik i `dotnet run` wpisz, aby wypróbować tę najnowszą wersję.</span><span class="sxs-lookup"><span data-stu-id="cb688-148">Save the file and type `dotnet run` to try this latest version.</span></span>

<span data-ttu-id="cb688-149">Przed rozpoczęciem następnej sekcji przenieśmy bieżący kod do osobnej metody.</span><span class="sxs-lookup"><span data-stu-id="cb688-149">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="cb688-150">Ułatwia to rozpoczęcie pracy z nowym przykładem.</span><span class="sxs-lookup"><span data-stu-id="cb688-150">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="cb688-151">Zmień nazwę `Main` metody `WorkingWithStrings` i napisz `Main` nową `WorkingWithStrings`metodę, która wywołuje .</span><span class="sxs-lookup"><span data-stu-id="cb688-151">Rename your `Main` method to `WorkingWithStrings` and write a new `Main` method that calls `WorkingWithStrings`.</span></span> <span data-ttu-id="cb688-152">Po zakończeniu kod powinien wyglądać tak:</span><span class="sxs-lookup"><span data-stu-id="cb688-152">When you have finished, your code should look like this:</span></span>

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

## <a name="lists-of-other-types"></a><span data-ttu-id="cb688-153">Listy innych typów</span><span class="sxs-lookup"><span data-stu-id="cb688-153">Lists of other types</span></span>

<span data-ttu-id="cb688-154">Do tej pory `string` używano tego typu na listach.</span><span class="sxs-lookup"><span data-stu-id="cb688-154">You've been using the `string` type in lists so far.</span></span> <span data-ttu-id="cb688-155">Zróbmy <xref:System.Collections.Generic.List%601> przy użyciu innego typu.</span><span class="sxs-lookup"><span data-stu-id="cb688-155">Let's make a <xref:System.Collections.Generic.List%601> using a different type.</span></span> <span data-ttu-id="cb688-156">Zbudujmy zestaw liczb.</span><span class="sxs-lookup"><span data-stu-id="cb688-156">Let's build a set of numbers.</span></span>

<span data-ttu-id="cb688-157">Dodaj następujące elementy do dolnej części nowej `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="cb688-157">Add the following to the bottom of your new `Main` method:</span></span>

```csharp
var fibonacciNumbers = new List<int> {1, 1};
```

<span data-ttu-id="cb688-158">Spowoduje to utworzenie listy liczb całkowitych i ustawienie pierwszych dwóch liczb całkowitych na wartość 1.</span><span class="sxs-lookup"><span data-stu-id="cb688-158">That creates a list of integers, and sets the first two integers to the value 1.</span></span> <span data-ttu-id="cb688-159">Są to dwie pierwsze wartości *sekwencji Fibonacciego*, sekwencji liczb.</span><span class="sxs-lookup"><span data-stu-id="cb688-159">These are the first two values of a *Fibonacci Sequence*, a sequence of numbers.</span></span> <span data-ttu-id="cb688-160">Każdy następny numer Fibonacciego znajduje się, biorąc sumę poprzednich dwóch liczb.</span><span class="sxs-lookup"><span data-stu-id="cb688-160">Each next Fibonacci number is found by taking the sum of the previous two numbers.</span></span> <span data-ttu-id="cb688-161">Dodaj ten kod:</span><span class="sxs-lookup"><span data-stu-id="cb688-161">Add this code:</span></span>

```csharp
var previous = fibonacciNumbers[fibonacciNumbers.Count - 1];
var previous2 = fibonacciNumbers[fibonacciNumbers.Count - 2];

fibonacciNumbers.Add(previous + previous2);

foreach (var item in fibonacciNumbers)
    Console.WriteLine(item);
```

<span data-ttu-id="cb688-162">Zapisz plik i `dotnet run` wpisz, aby zobaczyć wyniki.</span><span class="sxs-lookup"><span data-stu-id="cb688-162">Save the file and type `dotnet run` to see the results.</span></span>

> [!TIP]
> <span data-ttu-id="cb688-163">Aby skoncentrować się tylko na tej sekcji, `WorkingWithStrings();`możesz skomentować kod, który wywołuje .</span><span class="sxs-lookup"><span data-stu-id="cb688-163">To concentrate on just this section, you can comment out the code that calls `WorkingWithStrings();`.</span></span> <span data-ttu-id="cb688-164">Wystarczy umieścić `/` dwa znaki przed połączeniem `// WorkingWithStrings();`tak: .</span><span class="sxs-lookup"><span data-stu-id="cb688-164">Just put two `/` characters in front of the call like this:  `// WorkingWithStrings();`.</span></span>

## <a name="challenge"></a><span data-ttu-id="cb688-165">Wyzwanie</span><span class="sxs-lookup"><span data-stu-id="cb688-165">Challenge</span></span>

<span data-ttu-id="cb688-166">Zobacz, czy możesz połączyć niektóre koncepcje z tej i wcześniejszych lekcji.</span><span class="sxs-lookup"><span data-stu-id="cb688-166">See if you can put together some of the concepts from this and earlier lessons.</span></span> <span data-ttu-id="cb688-167">Rozwiń to, co zbudowałeś do tej pory dzięki numerom Fibonacciego.</span><span class="sxs-lookup"><span data-stu-id="cb688-167">Expand on what you've built so far with Fibonacci Numbers.</span></span> <span data-ttu-id="cb688-168">Spróbuj napisać kod, aby wygenerować pierwsze 20 liczb w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="cb688-168">Try to write the code to generate the first 20 numbers in the sequence.</span></span> <span data-ttu-id="cb688-169">(Jako wskazówkę, 20 numer Fibonacciego jest 6765.)</span><span class="sxs-lookup"><span data-stu-id="cb688-169">(As a hint, the 20th Fibonacci number is 6765.)</span></span>

## <a name="complete-challenge"></a><span data-ttu-id="cb688-170">Ukończenie wyzwania</span><span class="sxs-lookup"><span data-stu-id="cb688-170">Complete challenge</span></span>

<span data-ttu-id="cb688-171">Możesz zobaczyć przykładowe rozwiązanie, [patrząc na gotowy przykładowy kod w usiuł github](https://github.com/dotnet/samples/tree/master/csharp/list-quickstart/Program.cs#L13-L23).</span><span class="sxs-lookup"><span data-stu-id="cb688-171">You can see an example solution by [looking at the finished sample code on GitHub](https://github.com/dotnet/samples/tree/master/csharp/list-quickstart/Program.cs#L13-L23).</span></span>

<span data-ttu-id="cb688-172">Przy każdej iteracji pętli przyjmujesz dwie ostatnie liczby całkowite na liście, sumując je i dodając tę wartość do listy.</span><span class="sxs-lookup"><span data-stu-id="cb688-172">With each iteration of the loop, you're taking the last two integers in the list, summing them, and adding that value to the list.</span></span> <span data-ttu-id="cb688-173">Pętla jest powtarzana, dopóki nie dodasz 20 elementów do listy.</span><span class="sxs-lookup"><span data-stu-id="cb688-173">The loop repeats until you've added 20 items to the list.</span></span>

<span data-ttu-id="cb688-174">Gratulacje, ukończyłeś samouczek listy.</span><span class="sxs-lookup"><span data-stu-id="cb688-174">Congratulations, you've completed the list tutorial.</span></span> <span data-ttu-id="cb688-175">Można kontynuować [wprowadzenie do zajęć](introduction-to-classes.md) samouczek we własnym środowisku programistycznym.</span><span class="sxs-lookup"><span data-stu-id="cb688-175">You can continue with the [Introduction to classes](introduction-to-classes.md) tutorial in your own development environment.</span></span>

<span data-ttu-id="cb688-176">Więcej informacji na temat `List` pracy z typem można uzyskać w temacie [przewodnika .NET](../../../standard/index.md) w [kolekcjach](../../../standard/collections/index.md).</span><span class="sxs-lookup"><span data-stu-id="cb688-176">You can learn more about working with the `List` type in the [.NET Guide](../../../standard/index.md) topic on [collections](../../../standard/collections/index.md).</span></span> <span data-ttu-id="cb688-177">Dowiesz się również o wielu innych typach kolekcji.</span><span class="sxs-lookup"><span data-stu-id="cb688-177">You'll also learn about many other collection types.</span></span>

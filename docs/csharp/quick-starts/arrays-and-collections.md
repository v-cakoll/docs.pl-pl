---
title: "Przewodnik Szybki Start — kolekcje - C#"
description: "Naucz się C# eksplorując kolekcji listy, w tym szybki start."
keywords: C#, wprowadzenie, samouczek, kolekcje, lista
author: billwagner
ms.author: wiwagn
ms.date: 10/13/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.custom: mvc
ms.openlocfilehash: 6f559c7a3290e7db2266e10ec792c283394fb904
ms.sourcegitcommit: 9bee08539b1886c9d57fa3d5bd8a58dfdd7cad94
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/12/2017
---
# <a name="c-quick-start-collections"></a><span data-ttu-id="9d940-104">C# szybki start: kolekcje</span><span class="sxs-lookup"><span data-stu-id="9d940-104">C# Quick start: Collections</span></span> #

<span data-ttu-id="9d940-105">To szybki start zawiera wprowadzenie do języka C# i podstawy <xref:System.Collections.Generic.List%601> klasy.</span><span class="sxs-lookup"><span data-stu-id="9d940-105">This quick start provides an introduction to the C# language and the basics of the <xref:System.Collections.Generic.List%601> class.</span></span>

<span data-ttu-id="9d940-106">To szybki start oczekuje posiadania maszynie, która służy do tworzenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="9d940-106">This quick start expects you to have a machine you can use for development.</span></span> <span data-ttu-id="9d940-107">Temat .NET [wprowadzenie w ciągu 10 minut](https://www.microsoft.com/net/core) zawiera instrukcje dotyczące konfigurowania środowiska deweloperskiego lokalnego Mac, komputera lub Linux.</span><span class="sxs-lookup"><span data-stu-id="9d940-107">The .NET topic [Get Started in 10 minutes](https://www.microsoft.com/net/core) has instructions for setting up your local development environment on Mac, PC or Linux.</span></span> <span data-ttu-id="9d940-108">Jest to szybki przegląd poleceń będzie używany w [wprowadzenie do lokalnego Szybki Start](local-environment.md) wraz z łączami, aby uzyskać więcej szczegółów.</span><span class="sxs-lookup"><span data-stu-id="9d940-108">A quick overview of the commands you'll use is in the [introduction to the local quick starts](local-environment.md) with links to more details.</span></span>

## <a name="a-basic-list-example"></a><span data-ttu-id="9d940-109">Przykład podstawowa lista.</span><span class="sxs-lookup"><span data-stu-id="9d940-109">A basic list example.</span></span>

<span data-ttu-id="9d940-110">Utwórz katalog o nazwie **szybkiego startu listy**.</span><span class="sxs-lookup"><span data-stu-id="9d940-110">Create a directory named **list-quickstart**.</span></span> <span data-ttu-id="9d940-111">Upewnij, że bieżący katalog i uruchom `dotnet new console`.</span><span class="sxs-lookup"><span data-stu-id="9d940-111">Make that the current directory and run `dotnet new console`.</span></span>

> [!NOTE]
> <span data-ttu-id="9d940-112">Jeśli właśnie został ukończony [Rozpoczynanie pracy z platformą .NET w ciągu 10 minut](https://www.microsoft.com/net), można nadal używać aplikacji moja_aplikacja, który został właśnie utworzony.</span><span class="sxs-lookup"><span data-stu-id="9d940-112">If you just completed [Get started with .NET in 10 minutes](https://www.microsoft.com/net), you can keep using the myApp application that you just created.</span></span>
 
<span data-ttu-id="9d940-113">Otwórz **Program.cs** ulubionego edytora i Zastąp istniejący kod następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="9d940-113">Open **Program.cs** in your favorite editor, and replace the existing code with the following:</span></span>

```csharp
using System;
using System.Collections.Generic;

namespace list_quickstart
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

<span data-ttu-id="9d940-114">Zastąp `<name>` nazwą użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9d940-114">Replace `<name>` with your name.</span></span> <span data-ttu-id="9d940-115">Zapisz **Program.cs**.</span><span class="sxs-lookup"><span data-stu-id="9d940-115">Save **Program.cs**.</span></span> <span data-ttu-id="9d940-116">Typ `dotnet run` w oknie konsoli Wypróbuj ją.</span><span class="sxs-lookup"><span data-stu-id="9d940-116">Type `dotnet run` in your console window to try it.</span></span>

<span data-ttu-id="9d940-117">Utworzeniu tylko listę ciągów, dodać trzy nazwy do tej listy i wydrukowane nazwy WERSALIKÓW.</span><span class="sxs-lookup"><span data-stu-id="9d940-117">You've just created a list of strings, added three names to that list, and printed out the names in all CAPS.</span></span> <span data-ttu-id="9d940-118">Używasz pojęcia, które znasz już wcześniej Szybki Start pętli na liście.</span><span class="sxs-lookup"><span data-stu-id="9d940-118">You're using concepts that you've learned in earlier quick starts to loop through the list.</span></span>

<span data-ttu-id="9d940-119">Kod, aby wyświetlić nazwy sprawia, że użycie **ciągi interpolowane**.</span><span class="sxs-lookup"><span data-stu-id="9d940-119">The code to display names makes use of **interpolated strings**.</span></span>  <span data-ttu-id="9d940-120">Gdy poprzedzać `string` z `$` kodu C# można osadzić w deklaracji ciąg znaków.</span><span class="sxs-lookup"><span data-stu-id="9d940-120">When you precede a `string` with the `$` character, you can embed C# code in the string declaration.</span></span> <span data-ttu-id="9d940-121">Wartość, która generuje rzeczywisty ciąg zastępuje kodu C#.</span><span class="sxs-lookup"><span data-stu-id="9d940-121">The actual string replaces that C# code with the value it generates.</span></span> <span data-ttu-id="9d940-122">W tym przykładzie zastępuje `{name.ToUpper()}` z każdej nazwy przekonwertowany na wielkie litery, ponieważ wywołana <xref:System.String.ToUpper%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="9d940-122">In this example, it replaces the `{name.ToUpper()}` with each name, converted to capital letters, because you called the <xref:System.String.ToUpper%2A> method.</span></span>

<span data-ttu-id="9d940-123">Ta funkcja pozwala zachować eksploracji.</span><span class="sxs-lookup"><span data-stu-id="9d940-123">Let's keep exploring.</span></span>
    
## <a name="modify-list-contents"></a><span data-ttu-id="9d940-124">Modyfikowanie listy zawartości</span><span class="sxs-lookup"><span data-stu-id="9d940-124">Modify list contents</span></span>

<span data-ttu-id="9d940-125">Kolekcja utworzona używa <xref:System.Collections.Generic.List%601> typu.</span><span class="sxs-lookup"><span data-stu-id="9d940-125">The collection you created uses the <xref:System.Collections.Generic.List%601> type.</span></span> <span data-ttu-id="9d940-126">Tego typu przechowuje sekwencji elementów.</span><span class="sxs-lookup"><span data-stu-id="9d940-126">This type stores sequences of elements.</span></span> <span data-ttu-id="9d940-127">Należy określić typ elementów między nawiasami.</span><span class="sxs-lookup"><span data-stu-id="9d940-127">You specify the type of the elements between the angle brackets.</span></span>
    
<span data-ttu-id="9d940-128">Jeden ważnym aspektem tej <xref:System.Collections.Generic.List%601> typ jest czy można zwiększać i zmniejszać, dzięki któremu można dodać lub usunąć elementy.</span><span class="sxs-lookup"><span data-stu-id="9d940-128">One important aspect of this <xref:System.Collections.Generic.List%601> type is that it can grow or shrink, enabling you to add or remove elements.</span></span> <span data-ttu-id="9d940-129">Dodaj ten kod przed tagiem zamykającym `}` w `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="9d940-129">Add this code before the closing `}` in the `Main` method:</span></span>

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

<span data-ttu-id="9d940-130">Dodano dwa więcej nazw na końcu listy.</span><span class="sxs-lookup"><span data-stu-id="9d940-130">You've added two more names to the end of the list.</span></span> <span data-ttu-id="9d940-131">Możesz również usunięto jedną również.</span><span class="sxs-lookup"><span data-stu-id="9d940-131">You've also removed one as well.</span></span> <span data-ttu-id="9d940-132">Zapisz plik i typ `dotnet run` Wypróbuj ją.</span><span class="sxs-lookup"><span data-stu-id="9d940-132">Save the file, and type `dotnet run` to try it.</span></span>
    
<span data-ttu-id="9d940-133"><xref:System.Collections.Generic.List%601> Umożliwia odwoływać się do poszczególnych elementów przez **indeksu** również.</span><span class="sxs-lookup"><span data-stu-id="9d940-133">The <xref:System.Collections.Generic.List%601> enables you to reference individual items by **index** as well.</span></span> <span data-ttu-id="9d940-134">Umieść wskaźnik między `[` i `]` po nazwie listy tokenów.</span><span class="sxs-lookup"><span data-stu-id="9d940-134">You place the index between `[` and `]` tokens following the list name.</span></span> <span data-ttu-id="9d940-135">C# używa 0 dla pierwszego indeksu.</span><span class="sxs-lookup"><span data-stu-id="9d940-135">C# uses 0 for the first index.</span></span> <span data-ttu-id="9d940-136">Dodaj ten kod bezpośrednio poniżej kod, który właśnie został dodany i spróbuj go:</span><span class="sxs-lookup"><span data-stu-id="9d940-136">Add this code directly below the code you just added and try it:</span></span>

```csharp
Console.WriteLine($"My name is {names[0]}");
Console.WriteLine($"I've added {names[2]} and {names[3]} to the list");
```

<span data-ttu-id="9d940-137">Nie można uzyskać dostępu do indeksu poza koniec listy.</span><span class="sxs-lookup"><span data-stu-id="9d940-137">You cannot access an index beyond the end of the list.</span></span> <span data-ttu-id="9d940-138">Należy pamiętać, że indeksów zaczynają się od 0, dlatego największy prawidłowy indeks jest jednym mniejszy niż liczba elementów na liście.</span><span class="sxs-lookup"><span data-stu-id="9d940-138">Remember that indices start at 0, so the largest valid index is one less than the number of items in the list.</span></span> <span data-ttu-id="9d940-139">Możesz sprawdzić, jak długo używa listy <xref:System.Collections.Generic.List%601.Count%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="9d940-139">You can check how long the list is using the <xref:System.Collections.Generic.List%601.Count%2A> property.</span></span> <span data-ttu-id="9d940-140">Dodaj następujący kod na końcu metody Main:</span><span class="sxs-lookup"><span data-stu-id="9d940-140">Add the following code at the end of the Main method:</span></span>

```csharp
Console.WriteLine($"The list has {names.Count} people in it");
 ```

<span data-ttu-id="9d940-141">Zapisz plik i typ `dotnet run` ponownie, aby wyświetlić wyniki.</span><span class="sxs-lookup"><span data-stu-id="9d940-141">Save the file, and type `dotnet run` again to see the results.</span></span>    

## <a name="search-and-sort-lists"></a><span data-ttu-id="9d940-142">Wyszukiwanie i sortowanie listy</span><span class="sxs-lookup"><span data-stu-id="9d940-142">Search and sort lists</span></span>
<span data-ttu-id="9d940-143">Nasze przykłady za pomocą list stosunkowo mały, ale aplikacje często może tworzyć listy o wiele więcej elementów, czasami numerowanie tysięcy.</span><span class="sxs-lookup"><span data-stu-id="9d940-143">Our samples use relatively small lists, but your applications may often create lists with many more elements, sometimes numbering in the thousands.</span></span> <span data-ttu-id="9d940-144">Aby znaleźć elementy w tych kolekcjach większy, musisz Wyszukaj liście różne elementy.</span><span class="sxs-lookup"><span data-stu-id="9d940-144">To find elements in these larger collections, you need to search the list for different items.</span></span> <span data-ttu-id="9d940-145"><xref:System.Collections.Generic.List%601.IndexOf%2A> Metoda szuka elementu i zwraca indeks elementu.</span><span class="sxs-lookup"><span data-stu-id="9d940-145">The <xref:System.Collections.Generic.List%601.IndexOf%2A> method searches for an item and returns the index of the item.</span></span> <span data-ttu-id="9d940-146">Dodaj ten kod do dolnej części Twojego `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="9d940-146">Add this code to the bottom of your `Main` method:</span></span>

```csharp
var index = names.IndexOf("Felipe");
if (index == -1)
{
    Console.WriteLine($"When an item is not found, IndexOf returns {index}");
} else
{
    Console.WriteLine($"The name {names[index]} is at index {index}");
}

index = names.IndexOf("Not Found");
if (index == -1)
{
    Console.WriteLine($"When an item is not found, IndexOf returns {index}");
} else
{
    Console.WriteLine($"The name {names[index]} is at index {index}");
    
}
```

<span data-ttu-id="9d940-147">Elementy na liście mogą być również sortowane.</span><span class="sxs-lookup"><span data-stu-id="9d940-147">The items in your list can be sorted as well.</span></span> <span data-ttu-id="9d940-148"><xref:System.Collections.Generic.List%601.Sort%2A> Metody sortuje wszystkie elementy na liście w ich normalnym kolejność (alfabetycznie w przypadku ciągi).</span><span class="sxs-lookup"><span data-stu-id="9d940-148">The <xref:System.Collections.Generic.List%601.Sort%2A> method sorts all the items in the list in their normal order (alphabetically in the case of strings).</span></span> <span data-ttu-id="9d940-149">Dodaj ten kod do dołu naszych `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="9d940-149">Add this code to the bottom of our `Main` method:</span></span>

```csharp
names.Sort();
foreach (var name in names)
{
    Console.WriteLine($"Hello {name.ToUpper()}!");
}
```

<span data-ttu-id="9d940-150">Zapisz plik i typ `dotnet run` próby najnowsza wersja.</span><span class="sxs-lookup"><span data-stu-id="9d940-150">Save the file and type `dotnet run` to try this latest version.</span></span>

<span data-ttu-id="9d940-151">Przed rozpoczęciem następnej sekcji przejdziemy bieżącego kodu w oddzielnych metodach.</span><span class="sxs-lookup"><span data-stu-id="9d940-151">Before you start the next section, let's move the current code into a separate method.</span></span> <span data-ttu-id="9d940-152">Który ułatwia rozpoczęcie pracy z nowego przykład.</span><span class="sxs-lookup"><span data-stu-id="9d940-152">That makes it easier to start working with a new example.</span></span> <span data-ttu-id="9d940-153">Zmień nazwę Twojej `Main` metodę `WorkingWithStrings` i zapisać nową `Main` — metoda, która wywołuje `WorkingWithStrings`.</span><span class="sxs-lookup"><span data-stu-id="9d940-153">Rename your `Main` method to `WorkingWithStrings` and write a new `Main` method that calls `WorkingWithStrings`.</span></span> <span data-ttu-id="9d940-154">Po zakończeniu, kod powinien wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="9d940-154">When you have finished, your code should look like this:</span></span>

```csharp
using System;
using System.Collections.Generic;

namespace list_quickstart
{
    class Program
    {
        static void Main(string[] args)
        {
            WorkingWithStrings();
        }

        public static void WorkingWithStrings()
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
            Console.WriteLine($"The name {names[index]} is at index {index}");

            var notFound = names.IndexOf("Not Found");
            Console.WriteLine($"When an item is not found, IndexOf returns {notFound}");

            names.Sort();
            foreach (var name in names)
            {
                Console.WriteLine($"Hello {name.ToUpper()}!");
            }
        }
    }
}
```

## <a name="lists-of-other-types"></a><span data-ttu-id="9d940-155">Listę innych typów</span><span class="sxs-lookup"><span data-stu-id="9d940-155">Lists of other types</span></span>

<span data-ttu-id="9d940-156">Obecnie używasz `string` typu na listach wykonanej do tej pory.</span><span class="sxs-lookup"><span data-stu-id="9d940-156">You've been using the `string` type in lists so far.</span></span> <span data-ttu-id="9d940-157">Upewnijmy <xref:System.Collections.Generic.List%601> przy użyciu innego typu.</span><span class="sxs-lookup"><span data-stu-id="9d940-157">Let's make a <xref:System.Collections.Generic.List%601> using a different type.</span></span> <span data-ttu-id="9d940-158">Utworzymy zbioru liczb.</span><span class="sxs-lookup"><span data-stu-id="9d940-158">Let's build a set of numbers.</span></span> 

<span data-ttu-id="9d940-159">Dodaj następującą wartość do dołu nowej `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="9d940-159">Add the following to the bottom of your new `Main` method:</span></span>

```csharp
var fibonacciNumbers = new List<int> {1, 1};
```

<span data-ttu-id="9d940-160">Która tworzy listę liczb całkowitych i ustawia pierwszych dwóch liczb całkowitych na wartości 1.</span><span class="sxs-lookup"><span data-stu-id="9d940-160">That creates a list of integers, and sets the first two integers to the value 1.</span></span> <span data-ttu-id="9d940-161">Są to pierwsze dwie wartości *sekwencji Fibonacci*, sekwencji liczb.</span><span class="sxs-lookup"><span data-stu-id="9d940-161">These are the first two values of a *Fibonacci Sequence*, a sequence of numbers.</span></span> <span data-ttu-id="9d940-162">Znaleziono każdej kolejny numer Fibonacci wykonując Suma poprzednich dwóch liczb.</span><span class="sxs-lookup"><span data-stu-id="9d940-162">Each next Fibonacci number is found by taking the sum of the previous two numbers.</span></span> <span data-ttu-id="9d940-163">Dodaj ten kod:</span><span class="sxs-lookup"><span data-stu-id="9d940-163">Add this code:</span></span>

```csharp
var previous = fibonacciNumbers[fibonacciNumbers.Count - 1];
var previous2 = fibonacciNumbers[fibonacciNumbers.Count - 2];

fibonacciNumbers.Add(previous + previous2);

foreach(var item in fibonacciNumbers)
    Console.WriteLine(item);
```

<span data-ttu-id="9d940-164">Zapisz plik i typ `dotnet run` wyników.</span><span class="sxs-lookup"><span data-stu-id="9d940-164">Save the file and type `dotnet run` to see the results.</span></span> 

> [!TIP]
> <span data-ttu-id="9d940-165">Aby skoncentrować się na tylko w tej sekcji, możesz przekształcić w komentarz kod, który wywołuje `WorkingWithStrings();`.</span><span class="sxs-lookup"><span data-stu-id="9d940-165">To concentrate on just this section, you can comment out the code that calls `WorkingWithStrings();`.</span></span> <span data-ttu-id="9d940-166">Po prostu umieść dwa `/` znaków przed wywołanie podobnie do następującej: `// WorkingWithStrings();`.</span><span class="sxs-lookup"><span data-stu-id="9d940-166">Just put two `/` characters in front of the call like this:  `// WorkingWithStrings();`.</span></span> 

## <a name="challenge"></a><span data-ttu-id="9d940-167">żądanie</span><span class="sxs-lookup"><span data-stu-id="9d940-167">Challenge</span></span>
<span data-ttu-id="9d940-168">Zobacz, czy można utworzyć niektóre z pojęć związanych z tej i starszych wersji — lekcje.</span><span class="sxs-lookup"><span data-stu-id="9d940-168">See if you can put together some of the concepts from this and earlier lessons.</span></span> <span data-ttu-id="9d940-169">Rozwiń węzeł, na co powstanie wykonanej do tej pory numerami Fibonacci.</span><span class="sxs-lookup"><span data-stu-id="9d940-169">Expand on what you've built so far with Fibonacci Numbers.</span></span> <span data-ttu-id="9d940-170">Spróbuj napisać kod, aby wygenerować najpierw 20 cyfr w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="9d940-170">Try to write the code to generate the first 20 numbers in the sequence.</span></span> <span data-ttu-id="9d940-171">(Jako wskazówki, 20 numer Fibonacci jest 6765).</span><span class="sxs-lookup"><span data-stu-id="9d940-171">(As a hint, the 20th Fibonacci number is 6765.)</span></span>

## <a name="complete-challenge"></a><span data-ttu-id="9d940-172">Żądanie ukończone</span><span class="sxs-lookup"><span data-stu-id="9d940-172">Complete challenge</span></span>

<span data-ttu-id="9d940-173">Widać przykład rozwiązania przez [patrzeć Zakończono przykładowy kod w witrynie GitHub](https://github.com/dotnet/docs/tree/master/samples/csharp/list-quickstart/Program.cs#L13-L23)</span><span class="sxs-lookup"><span data-stu-id="9d940-173">You can see an example solution by [looking at the finished sample code on GitHub](https://github.com/dotnet/docs/tree/master/samples/csharp/list-quickstart/Program.cs#L13-L23)</span></span>

<span data-ttu-id="9d940-174">Przy każdej iteracji pętli tworzenia ostatnich dwóch liczb całkowitych na liście sumowanie je, a następnie dodanie tej wartości na liście.</span><span class="sxs-lookup"><span data-stu-id="9d940-174">With each iteration of the loop, you're taking the last two integers in the list, summing them, and adding that value to the list.</span></span> <span data-ttu-id="9d940-175">Pętla jest powtarzany aż 20 elementy dodane do listy.</span><span class="sxs-lookup"><span data-stu-id="9d940-175">The loop repeats until you've added 20 items to the list.</span></span>

<span data-ttu-id="9d940-176">Gratulacje, przeprowadzisz listy szybki start.</span><span class="sxs-lookup"><span data-stu-id="9d940-176">Congratulations, you've completed the list quick start.</span></span> <span data-ttu-id="9d940-177">Można kontynuować [wprowadzenie do klasy](introduction-to-classes.md) szybki start w środowisku projektowania.</span><span class="sxs-lookup"><span data-stu-id="9d940-177">You can continue with the [Introduction to classes](introduction-to-classes.md) quick start in your own development environment.</span></span>

<span data-ttu-id="9d940-178">Dowiedz się więcej o pracy z `List` wpisz [.NET przewodnik](../../standard/index.md) temat [kolekcje](../../standard/collections/index.md).</span><span class="sxs-lookup"><span data-stu-id="9d940-178">You can learn more about working with the `List` type in the [.NET Guide](../../standard/index.md) topic on [collections](../../standard/collections/index.md).</span></span> <span data-ttu-id="9d940-179">Dowiesz się o innych typów kolekcji.</span><span class="sxs-lookup"><span data-stu-id="9d940-179">You'll also learn about many other collection types.</span></span>

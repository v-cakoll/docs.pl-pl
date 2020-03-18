---
title: Aplikacja konsolowa
description: W tym samouczku nauczy Cię wiele funkcji w .NET Core i języku C#.
ms.date: 03/06/2017
ms.technology: csharp-fundamentals
ms.assetid: 883cd93d-50ce-4144-b7c9-2df28d9c11a0
ms.openlocfilehash: 09ce36e7a61f576dc4449976ce676701dc57c9cd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76921124"
---
# <a name="console-app"></a><span data-ttu-id="07c8c-103">Aplikacja konsolowa</span><span class="sxs-lookup"><span data-stu-id="07c8c-103">Console app</span></span>

<span data-ttu-id="07c8c-104">W tym samouczku nauczy Cię wiele funkcji w .NET Core i języku C#.</span><span class="sxs-lookup"><span data-stu-id="07c8c-104">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="07c8c-105">Dowiesz się:</span><span class="sxs-lookup"><span data-stu-id="07c8c-105">You'll learn:</span></span>

- <span data-ttu-id="07c8c-106">Podstawy cli .NET Core</span><span class="sxs-lookup"><span data-stu-id="07c8c-106">The basics of the .NET Core CLI</span></span>
- <span data-ttu-id="07c8c-107">Struktura aplikacji konsoli C#</span><span class="sxs-lookup"><span data-stu-id="07c8c-107">The structure of a C# Console Application</span></span>
- <span data-ttu-id="07c8c-108">Konsola We/Wy</span><span class="sxs-lookup"><span data-stu-id="07c8c-108">Console I/O</span></span>
- <span data-ttu-id="07c8c-109">Podstawy interfejsów API we/wy plików w .NET</span><span class="sxs-lookup"><span data-stu-id="07c8c-109">The basics of File I/O APIs in .NET</span></span>
- <span data-ttu-id="07c8c-110">Podstawy programowania asynchronicznego opartego na zadaniach w programie .NET</span><span class="sxs-lookup"><span data-stu-id="07c8c-110">The basics of the Task-based Asynchronous Programming in .NET</span></span>

<span data-ttu-id="07c8c-111">Stworzysz aplikację, która odczytuje plik tekstowy i nawiązuje do konsoli zawartość tego pliku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="07c8c-111">You'll build an application that reads a text file, and echoes the contents of that text file to the console.</span></span> <span data-ttu-id="07c8c-112">Wyjście do konsoli jest w tempie, aby dopasować czytanie na głos.</span><span class="sxs-lookup"><span data-stu-id="07c8c-112">The output to the console is paced to match reading it aloud.</span></span> <span data-ttu-id="07c8c-113">Możesz przyspieszyć lub spowolnić tempo, naciskając klawisze "<" (mniej niż) lub ">" (większe niż).</span><span class="sxs-lookup"><span data-stu-id="07c8c-113">You can speed up or slow down the pace by pressing the '<' (less than) or '>' (greater than) keys.</span></span>

<span data-ttu-id="07c8c-114">Istnieje wiele funkcji w tym samouczku.</span><span class="sxs-lookup"><span data-stu-id="07c8c-114">There are a lot of features in this tutorial.</span></span> <span data-ttu-id="07c8c-115">Budujmy je jeden po drugim.</span><span class="sxs-lookup"><span data-stu-id="07c8c-115">Let's build them one by one.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="07c8c-116">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="07c8c-116">Prerequisites</span></span>

- <span data-ttu-id="07c8c-117">Skonfiguruj komputer do uruchamiania .NET Core.</span><span class="sxs-lookup"><span data-stu-id="07c8c-117">Set up your machine to run .NET Core.</span></span> <span data-ttu-id="07c8c-118">Instrukcje instalacji można znaleźć na stronie [pobierania .NET Core.](https://dotnet.microsoft.com/download)</span><span class="sxs-lookup"><span data-stu-id="07c8c-118">You can find the installation instructions on the [.NET Core downloads](https://dotnet.microsoft.com/download) page.</span></span> <span data-ttu-id="07c8c-119">Tę aplikację można uruchomić w systemie Windows, Linux, macOS lub w kontenerze platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="07c8c-119">You can run this application on Windows, Linux, macOS, or in a Docker container.</span></span>

- <span data-ttu-id="07c8c-120">Zainstaluj swój ulubiony edytor kodów.</span><span class="sxs-lookup"><span data-stu-id="07c8c-120">Install your favorite code editor.</span></span>

## <a name="create-the-app"></a><span data-ttu-id="07c8c-121">Tworzymy aplikację.</span><span class="sxs-lookup"><span data-stu-id="07c8c-121">Create the app</span></span>

<span data-ttu-id="07c8c-122">Pierwszym krokiem jest utworzenie nowej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="07c8c-122">The first step is to create a new application.</span></span> <span data-ttu-id="07c8c-123">Otwórz wiersz polecenia i utwórz nowy katalog dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="07c8c-123">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="07c8c-124">Upewnij się, że bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="07c8c-124">Make that the current directory.</span></span> <span data-ttu-id="07c8c-125">Wpisz `dotnet new console` polecenie w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="07c8c-125">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="07c8c-126">Spowoduje to utworzenie plików startowych dla podstawowej aplikacji "Hello World".</span><span class="sxs-lookup"><span data-stu-id="07c8c-126">This creates the starter files for a basic "Hello World" application.</span></span>

<span data-ttu-id="07c8c-127">Przed rozpoczęciem wprowadzania modyfikacji przejdźmy przez kroki, aby uruchomić prostą aplikację Hello World.</span><span class="sxs-lookup"><span data-stu-id="07c8c-127">Before you start making modifications, let's go through the steps to run the simple Hello World application.</span></span> <span data-ttu-id="07c8c-128">Po utworzeniu aplikacji `dotnet restore` wpisz wiersz polecenia.</span><span class="sxs-lookup"><span data-stu-id="07c8c-128">After creating the application, type `dotnet restore` at the command prompt.</span></span> <span data-ttu-id="07c8c-129">To polecenie uruchamia proces przywracania pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="07c8c-129">This command runs the NuGet package restore process.</span></span> <span data-ttu-id="07c8c-130">NuGet jest menedżerem pakietów .NET.</span><span class="sxs-lookup"><span data-stu-id="07c8c-130">NuGet is a .NET package manager.</span></span> <span data-ttu-id="07c8c-131">To polecenie pobiera dowolną z brakujących zależności dla projektu.</span><span class="sxs-lookup"><span data-stu-id="07c8c-131">This command downloads any of the missing dependencies for your project.</span></span> <span data-ttu-id="07c8c-132">Ponieważ jest to nowy projekt, żadna z zależności nie są na miejscu, więc pierwsze uruchomienie pobierze .NET Core framework.</span><span class="sxs-lookup"><span data-stu-id="07c8c-132">As this is a new project, none of the dependencies are in place, so the first run will download the .NET Core framework.</span></span> <span data-ttu-id="07c8c-133">Po tym początkowym kroku należy `dotnet restore` uruchomić tylko podczas dodawania nowych pakietów zależnych lub zaktualizować wersje dowolnej z zależności.</span><span class="sxs-lookup"><span data-stu-id="07c8c-133">After this initial step, you will only need to run `dotnet restore` when you add new dependent packages, or update the versions of any of your dependencies.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="07c8c-134">Po przywróceniu pakietów `dotnet build`uruchomisz .</span><span class="sxs-lookup"><span data-stu-id="07c8c-134">After restoring packages, you run `dotnet build`.</span></span> <span data-ttu-id="07c8c-135">Spowoduje to wykonanie aparatu kompilacji i tworzy plik wykonywalny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="07c8c-135">This executes the build engine and creates your application executable.</span></span> <span data-ttu-id="07c8c-136">Na koniec `dotnet run` można wykonać, aby uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="07c8c-136">Finally, you execute `dotnet run` to run your application.</span></span>

<span data-ttu-id="07c8c-137">Prosty kod aplikacji Hello World jest w Program.cs.</span><span class="sxs-lookup"><span data-stu-id="07c8c-137">The simple Hello World application code is all in Program.cs.</span></span> <span data-ttu-id="07c8c-138">Otwórz ten plik za pomocą ulubionego edytora tekstu.</span><span class="sxs-lookup"><span data-stu-id="07c8c-138">Open that file with your favorite text editor.</span></span> <span data-ttu-id="07c8c-139">Nieszywniemy pierwsze zmiany.</span><span class="sxs-lookup"><span data-stu-id="07c8c-139">We're about to make our first changes.</span></span> <span data-ttu-id="07c8c-140">U góry pliku zobacz using instrukcji:</span><span class="sxs-lookup"><span data-stu-id="07c8c-140">At the top of the file, see a using statement:</span></span>

```csharp
using System;
```

<span data-ttu-id="07c8c-141">Ta instrukcja informuje kompilator, że wszystkie typy z obszaru `System` nazw są w zakresie.</span><span class="sxs-lookup"><span data-stu-id="07c8c-141">This statement tells the compiler that any types from the `System` namespace are in scope.</span></span> <span data-ttu-id="07c8c-142">Podobnie jak inne języki zorientowane na obiekty, które mogły być używane, C# używa przestrzeni nazw do organizowania typów.</span><span class="sxs-lookup"><span data-stu-id="07c8c-142">Like other Object Oriented languages you may have used, C# uses namespaces to organize types.</span></span> <span data-ttu-id="07c8c-143">Ten program Hello World nie różni się.</span><span class="sxs-lookup"><span data-stu-id="07c8c-143">This Hello World program is no different.</span></span> <span data-ttu-id="07c8c-144">Widać, że program jest ujęty w obszarze nazw nazwą o nazwie opartej na nazwie bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="07c8c-144">You can see that the program is enclosed in the namespace with the name based on the name of the current directory.</span></span> <span data-ttu-id="07c8c-145">W tym samouczku zmieńmy nazwę obszaru nazw `TeleprompterConsole`na :</span><span class="sxs-lookup"><span data-stu-id="07c8c-145">For this tutorial, let's change the name of the namespace to `TeleprompterConsole`:</span></span>

```csharp
namespace TeleprompterConsole
```

## <a name="reading-and-echoing-the-file"></a><span data-ttu-id="07c8c-146">Odczytywanie i powtarzanie pliku</span><span class="sxs-lookup"><span data-stu-id="07c8c-146">Reading and Echoing the File</span></span>

<span data-ttu-id="07c8c-147">Pierwszą funkcją do dodania jest możliwość odczytu pliku tekstowego i wyświetlenia całego tekstu w konsoli.</span><span class="sxs-lookup"><span data-stu-id="07c8c-147">The first feature to add is the ability to read a text file and display all that text to the console.</span></span> <span data-ttu-id="07c8c-148">Najpierw dodajmy plik tekstowy.</span><span class="sxs-lookup"><span data-stu-id="07c8c-148">First, let's add a text file.</span></span> <span data-ttu-id="07c8c-149">Skopiuj [plik sampleQuotes.txt](https://github.com/dotnet/samples/raw/master/csharp/getting-started/console-teleprompter/sampleQuotes.txt) z repozytorium GitHub dla tego [przykładu](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-teleprompter) do katalogu projektu.</span><span class="sxs-lookup"><span data-stu-id="07c8c-149">Copy the [sampleQuotes.txt](https://github.com/dotnet/samples/raw/master/csharp/getting-started/console-teleprompter/sampleQuotes.txt) file from the GitHub repository for this [sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-teleprompter) into your project directory.</span></span> <span data-ttu-id="07c8c-150">Będzie to służyć jako skrypt dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="07c8c-150">This will serve as the script for your application.</span></span> <span data-ttu-id="07c8c-151">Jeśli chcesz uzyskać informacje na temat pobierania przykładowej aplikacji dla tego tematu, zapoznaj się z instrukcjami w temacie [Przykłady i samouczki.](../../samples-and-tutorials/index.md#viewing-and-downloading-samples)</span><span class="sxs-lookup"><span data-stu-id="07c8c-151">If you would like information on how to download the sample app for this topic, see the instructions in the [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples) topic.</span></span>

<span data-ttu-id="07c8c-152">Następnie dodaj następującą `Program` metodę w klasie `Main` (tuż poniżej metody):</span><span class="sxs-lookup"><span data-stu-id="07c8c-152">Next, add the following method in your `Program` class (right below the `Main` method):</span></span>

```csharp
static IEnumerable<string> ReadFrom(string file)
{
    string line;
    using (var reader = File.OpenText(file))
    {
        while ((line = reader.ReadLine()) != null)
        {
            yield return line;
        }
    }
}
```

<span data-ttu-id="07c8c-153">Ta metoda używa typów z dwóch nowych obszarów nazw.</span><span class="sxs-lookup"><span data-stu-id="07c8c-153">This method uses types from two new namespaces.</span></span> <span data-ttu-id="07c8c-154">Aby to skompilować, musisz dodać następujące dwa wiersze do górnej części pliku:</span><span class="sxs-lookup"><span data-stu-id="07c8c-154">For this to compile you'll need to add the following two lines to the top of the file:</span></span>

```csharp
using System.Collections.Generic;
using System.IO;
```

<span data-ttu-id="07c8c-155">Interfejs <xref:System.Collections.Generic.IEnumerable%601> jest zdefiniowany <xref:System.Collections.Generic> w obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="07c8c-155">The <xref:System.Collections.Generic.IEnumerable%601> interface is defined in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="07c8c-156">Klasa <xref:System.IO.File> jest zdefiniowana <xref:System.IO> w obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="07c8c-156">The <xref:System.IO.File> class is defined in the <xref:System.IO> namespace.</span></span>

<span data-ttu-id="07c8c-157">Ta metoda jest specjalnym typem metody Języka C# o nazwie *Iterator method*.</span><span class="sxs-lookup"><span data-stu-id="07c8c-157">This method is a special type of C# method called an *Iterator method*.</span></span> <span data-ttu-id="07c8c-158">Metody wyliczania zwracają sekwencje, które są oceniane leniwie.</span><span class="sxs-lookup"><span data-stu-id="07c8c-158">Enumerator methods return sequences that are evaluated lazily.</span></span> <span data-ttu-id="07c8c-159">Oznacza to, że każdy element w sekwencji jest generowany, ponieważ jest wymagane przez kod korzystających sekwencji.</span><span class="sxs-lookup"><span data-stu-id="07c8c-159">That means each item in the sequence is generated as it is requested by the code consuming the sequence.</span></span> <span data-ttu-id="07c8c-160">Metody wyliczania są metody, które [`yield return`](../language-reference/keywords/yield.md) zawierają co najmniej jedną instrukcję.</span><span class="sxs-lookup"><span data-stu-id="07c8c-160">Enumerator methods are methods that contain one or more [`yield return`](../language-reference/keywords/yield.md) statements.</span></span> <span data-ttu-id="07c8c-161">Obiekt zwrócony przez `ReadFrom` metodę zawiera kod do generowania każdego elementu w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="07c8c-161">The object returned by the `ReadFrom` method contains the code to generate each item in the sequence.</span></span> <span data-ttu-id="07c8c-162">W tym przykładzie, który obejmuje odczytywanie następnego wiersza tekstu z pliku źródłowego i zwracanie tego ciągu.</span><span class="sxs-lookup"><span data-stu-id="07c8c-162">In this example, that involves reading the next line of text from the source file, and returning that string.</span></span> <span data-ttu-id="07c8c-163">Za każdym razem, gdy kod wywołujący żąda następnego elementu z sekwencji, kod odczytuje następny wiersz tekstu z pliku i zwraca go.</span><span class="sxs-lookup"><span data-stu-id="07c8c-163">Each time the calling code requests the next item from the sequence, the code reads the next line of text from the file and returns it.</span></span> <span data-ttu-id="07c8c-164">Gdy plik jest całkowicie odczytywany, sekwencja wskazuje, że nie ma więcej elementów.</span><span class="sxs-lookup"><span data-stu-id="07c8c-164">When the file is completely read, the sequence indicates that there are no more items.</span></span>

<span data-ttu-id="07c8c-165">Istnieją dwa inne elementy składni Języka C#, które mogą być dla Ciebie nowe.</span><span class="sxs-lookup"><span data-stu-id="07c8c-165">There are two other C# syntax elements that may be new to you.</span></span> <span data-ttu-id="07c8c-166">Instrukcja [`using`](../language-reference/keywords/using-statement.md) w tej metodzie zarządza oczyszczania zasobów.</span><span class="sxs-lookup"><span data-stu-id="07c8c-166">The [`using`](../language-reference/keywords/using-statement.md) statement in this method manages resource cleanup.</span></span> <span data-ttu-id="07c8c-167">Zmienna, która jest `using` inicjowana`reader`w instrukcji ( , <xref:System.IDisposable> w tym przykładzie) musi implementować interfejs.</span><span class="sxs-lookup"><span data-stu-id="07c8c-167">The variable that is initialized in the `using` statement (`reader`, in this example) must implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="07c8c-168">Ten interfejs definiuje jedną `Dispose`metodę, która powinna być wywoływana, gdy zasób powinien zostać zwolniony.</span><span class="sxs-lookup"><span data-stu-id="07c8c-168">That interface defines a single method, `Dispose`, that should be called when the resource should be released.</span></span> <span data-ttu-id="07c8c-169">Kompilator generuje to wywołanie, gdy wykonanie `using` osiągnie nawias zamykający instrukcji.</span><span class="sxs-lookup"><span data-stu-id="07c8c-169">The compiler generates that call when execution reaches the closing brace of the `using` statement.</span></span> <span data-ttu-id="07c8c-170">Kod wygenerowany przez kompilator zapewnia, że zasób jest zwalniany, nawet jeśli wyjątek jest zgłaszany z kodu w bloku zdefiniowane przez using instrukcji.</span><span class="sxs-lookup"><span data-stu-id="07c8c-170">The compiler-generated code ensures that the resource is released even if an exception is thrown from the code in the block defined by the using statement.</span></span>

<span data-ttu-id="07c8c-171">Zmienna `reader` jest definiowana `var` przy użyciu słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="07c8c-171">The `reader` variable is defined using the `var` keyword.</span></span> <span data-ttu-id="07c8c-172">[`var`](../language-reference/keywords/var.md)definiuje *niejawnie wpisaną zmienną lokalną*.</span><span class="sxs-lookup"><span data-stu-id="07c8c-172">[`var`](../language-reference/keywords/var.md) defines an *implicitly typed local variable*.</span></span> <span data-ttu-id="07c8c-173">Oznacza to, że typ zmiennej jest określana przez typ czasu kompilacji obiektu przypisanego do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="07c8c-173">That means the type of the variable is determined by the compile-time type of the object assigned to the variable.</span></span> <span data-ttu-id="07c8c-174">W tym miejscu jest to <xref:System.IO.File.OpenText(System.String)> wartość zwracana <xref:System.IO.StreamReader> z metody, która jest obiektem.</span><span class="sxs-lookup"><span data-stu-id="07c8c-174">Here, that is the return value from the <xref:System.IO.File.OpenText(System.String)> method, which is a <xref:System.IO.StreamReader> object.</span></span>

<span data-ttu-id="07c8c-175">Teraz wypełnijmy kod, aby odczytać plik `Main` w metodzie:</span><span class="sxs-lookup"><span data-stu-id="07c8c-175">Now, let's fill in the code to read the file in the `Main` method:</span></span>

```csharp
var lines = ReadFrom("sampleQuotes.txt");
foreach (var line in lines)
{
    Console.WriteLine(line);
}
```

<span data-ttu-id="07c8c-176">Uruchom program (za pomocą `dotnet run`) i możesz zobaczyć każdy wiersz wydrukowany na konsoli.</span><span class="sxs-lookup"><span data-stu-id="07c8c-176">Run the program (using `dotnet run`) and you can see every line printed out to the console.</span></span>

## <a name="adding-delays-and-formatting-output"></a><span data-ttu-id="07c8c-177">Dodawanie opóźnień i danych wyjściowych formatowania</span><span class="sxs-lookup"><span data-stu-id="07c8c-177">Adding Delays and Formatting output</span></span>

<span data-ttu-id="07c8c-178">To, co masz, jest wyświetlane zbyt szybko, aby przeczytać na głos.</span><span class="sxs-lookup"><span data-stu-id="07c8c-178">What you have is being displayed far too fast to read aloud.</span></span> <span data-ttu-id="07c8c-179">Teraz musisz dodać opóźnienia w danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="07c8c-179">Now you need to add the delays in the output.</span></span> <span data-ttu-id="07c8c-180">Po uruchomieniu będziesz budować niektóre z podstawowych kodu, który umożliwia przetwarzanie asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="07c8c-180">As you start, you'll be building some of the core code that enables asynchronous processing.</span></span> <span data-ttu-id="07c8c-181">Jednak te pierwsze kroki będą zgodne z kilkoma anty-wzorców.</span><span class="sxs-lookup"><span data-stu-id="07c8c-181">However, these first steps will follow a few anti-patterns.</span></span> <span data-ttu-id="07c8c-182">Anti-wzorce są wskazywane w komentarzach podczas dodawania kodu, a kod zostanie zaktualizowany w kolejnych krokach.</span><span class="sxs-lookup"><span data-stu-id="07c8c-182">The anti-patterns are pointed out in comments as you add the code, and the code will be updated in later steps.</span></span>

<span data-ttu-id="07c8c-183">Istnieją dwa kroki do tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="07c8c-183">There are two steps to this section.</span></span> <span data-ttu-id="07c8c-184">Najpierw zaktualizujesz metodę iteratorego, aby zwrócić pojedyncze wyrazy zamiast całych wierszy.</span><span class="sxs-lookup"><span data-stu-id="07c8c-184">First, you'll update the iterator method to return single words instead of entire lines.</span></span> <span data-ttu-id="07c8c-185">Tak jest z tymi modyfikacjami.</span><span class="sxs-lookup"><span data-stu-id="07c8c-185">That's done with these modifications.</span></span> <span data-ttu-id="07c8c-186">Zastąp instrukcję `yield return line;` następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="07c8c-186">Replace the `yield return line;` statement with the following code:</span></span>

```csharp
var words = line.Split(' ');
foreach (var word in words)
{
    yield return word + " ";
}
yield return Environment.NewLine;
```

<span data-ttu-id="07c8c-187">Następnie należy zmodyfikować sposób korzystania z wierszy pliku i dodać opóźnienie po zapisaniu każdego wyrazu.</span><span class="sxs-lookup"><span data-stu-id="07c8c-187">Next, you need to modify how you consume the lines of the file, and add a delay after writing each word.</span></span> <span data-ttu-id="07c8c-188">Zamień instrukcję `Console.WriteLine(line)` w metodzie `Main` na następujący blok:</span><span class="sxs-lookup"><span data-stu-id="07c8c-188">Replace the `Console.WriteLine(line)` statement in the `Main` method with the following block:</span></span>

```csharp
Console.Write(line);
if (!string.IsNullOrWhiteSpace(line))
{
    var pause = Task.Delay(200);
    // Synchronously waiting on a task is an
    // anti-pattern. This will get fixed in later
    // steps.
    pause.Wait();
}
```

<span data-ttu-id="07c8c-189">Klasa <xref:System.Threading.Tasks.Task> znajduje się <xref:System.Threading.Tasks> w obszarze nazw, więc `using` należy dodać tę instrukcję u góry pliku:</span><span class="sxs-lookup"><span data-stu-id="07c8c-189">The <xref:System.Threading.Tasks.Task> class is in the <xref:System.Threading.Tasks> namespace, so you need to add that `using` statement at the top of file:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="07c8c-190">Uruchom przykład i sprawdź dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="07c8c-190">Run the sample, and check the output.</span></span> <span data-ttu-id="07c8c-191">Teraz każde pojedyncze słowo jest drukowane, a następnie 200 ms opóźnienie.</span><span class="sxs-lookup"><span data-stu-id="07c8c-191">Now, each single word is printed, followed by a 200 ms delay.</span></span> <span data-ttu-id="07c8c-192">Jednak wyświetlane dane wyjściowe pokazują pewne problemy, ponieważ źródłowy plik tekstowy ma kilka wierszy, które mają więcej niż 80 znaków bez podziału wiersza.</span><span class="sxs-lookup"><span data-stu-id="07c8c-192">However, the displayed output shows some issues because the source text file has several lines that have more than 80 characters without a line break.</span></span> <span data-ttu-id="07c8c-193">To może być trudne do odczytania podczas przewijania przez.</span><span class="sxs-lookup"><span data-stu-id="07c8c-193">That can be hard to read while it's scrolling by.</span></span> <span data-ttu-id="07c8c-194">To jest łatwe do naprawienia.</span><span class="sxs-lookup"><span data-stu-id="07c8c-194">That's easy to fix.</span></span> <span data-ttu-id="07c8c-195">Po prostu będziesz śledzić długość każdego wiersza i generować nowy wiersz, gdy długość linii osiągnie określony próg.</span><span class="sxs-lookup"><span data-stu-id="07c8c-195">You'll just keep track of the length of each line, and generate a new line whenever the line length reaches a certain threshold.</span></span> <span data-ttu-id="07c8c-196">Zadeklarować zmienną lokalną `words` po `ReadFrom` deklaracji w metodzie, która przechowuje długość wiersza:</span><span class="sxs-lookup"><span data-stu-id="07c8c-196">Declare a local variable after the declaration of `words` in the `ReadFrom` method that holds the line length:</span></span>

```csharp
var lineLength = 0;
```

<span data-ttu-id="07c8c-197">Następnie dodaj następujący kod `yield return word + " ";` po instrukcji (przed nawiasem klamrowym zamknięcia):</span><span class="sxs-lookup"><span data-stu-id="07c8c-197">Then, add the following code after the `yield return word + " ";` statement (before the closing brace):</span></span>

```csharp
lineLength += word.Length + 1;
if (lineLength > 70)
{
    yield return Environment.NewLine;
    lineLength = 0;
}
```

<span data-ttu-id="07c8c-198">Uruchom przykład, a będziesz mógł czytać na głos w jego wstępnie skonfigurowanym tempie.</span><span class="sxs-lookup"><span data-stu-id="07c8c-198">Run the sample, and you'll be able to read aloud at its pre-configured pace.</span></span>

## <a name="async-tasks"></a><span data-ttu-id="07c8c-199">Zadania asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="07c8c-199">Async Tasks</span></span>

<span data-ttu-id="07c8c-200">W tym ostatnim kroku dodasz kod do zapisu danych wyjściowych asynchronicznie w jednym zadaniu, a także uruchamiasz inne zadanie do odczytu danych wejściowych od użytkownika, jeśli chcesz przyspieszyć lub spowolnić wyświetlanie tekstu lub całkowicie zatrzymać wyświetlanie tekstu.</span><span class="sxs-lookup"><span data-stu-id="07c8c-200">In this final step, you'll add the code to write the output asynchronously in one task, while also running another task to read input from the user if they want to speed up or slow down the text display, or stop the text display altogether.</span></span> <span data-ttu-id="07c8c-201">Ma to kilka kroków w nim i na koniec będziesz miał wszystkie aktualizacje, które są potrzebne.</span><span class="sxs-lookup"><span data-stu-id="07c8c-201">This has a few steps in it and by the end, you'll have all the updates that you need.</span></span> <span data-ttu-id="07c8c-202">Pierwszym krokiem jest utworzenie asynchronicznej <xref:System.Threading.Tasks.Task> metody zwracania, która reprezentuje kod utworzony do tej pory do odczytu i wyświetlania pliku.</span><span class="sxs-lookup"><span data-stu-id="07c8c-202">The first step is to create an asynchronous <xref:System.Threading.Tasks.Task> returning method that represents the code you've created so far to read and display the file.</span></span>

<span data-ttu-id="07c8c-203">Dodaj tę metodę `Program` do swojej klasy (jest pobierana z treści metody): `Main`</span><span class="sxs-lookup"><span data-stu-id="07c8c-203">Add this method to your `Program` class (it's taken from the body of your `Main` method):</span></span>

```csharp
private static async Task ShowTeleprompter()
{
    var words = ReadFrom("sampleQuotes.txt");
    foreach (var word in words)
    {
        Console.Write(word);
        if (!string.IsNullOrWhiteSpace(word))
        {
            await Task.Delay(200);
        }
    }
}
```

<span data-ttu-id="07c8c-204">Zauważysz dwie zmiany.</span><span class="sxs-lookup"><span data-stu-id="07c8c-204">You'll notice two changes.</span></span> <span data-ttu-id="07c8c-205">Po pierwsze, w treści metody, <xref:System.Threading.Tasks.Task.Wait> zamiast wywoływania synchronicznie czekać na zakończenie `await` zadania, ta wersja używa słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="07c8c-205">First, in the body of the method, instead of calling <xref:System.Threading.Tasks.Task.Wait> to synchronously wait for a task to finish, this version uses the `await` keyword.</span></span> <span data-ttu-id="07c8c-206">Aby to zrobić, należy dodać `async` modyfikator do podpisu metody.</span><span class="sxs-lookup"><span data-stu-id="07c8c-206">In order to do that, you need to add the `async` modifier to the method signature.</span></span> <span data-ttu-id="07c8c-207">Ta metoda `Task`zwraca wartość .</span><span class="sxs-lookup"><span data-stu-id="07c8c-207">This method returns a `Task`.</span></span> <span data-ttu-id="07c8c-208">Należy zauważyć, że nie ma `Task` żadnych instrukcji zwrotnych, które zwracają obiekt.</span><span class="sxs-lookup"><span data-stu-id="07c8c-208">Notice that there are no return statements that return a `Task` object.</span></span> <span data-ttu-id="07c8c-209">Zamiast tego `Task` ten obiekt jest tworzony przez kod kompilator generuje podczas korzystania z `await` operatora.</span><span class="sxs-lookup"><span data-stu-id="07c8c-209">Instead, that `Task` object is created by code the compiler generates when you use the `await` operator.</span></span> <span data-ttu-id="07c8c-210">Można sobie wyobrazić, że ta metoda `await`zwraca, gdy osiągnie .</span><span class="sxs-lookup"><span data-stu-id="07c8c-210">You can imagine that this method returns when it reaches an `await`.</span></span> <span data-ttu-id="07c8c-211">Zwrócony `Task` wskazuje, że praca nie została ukończona.</span><span class="sxs-lookup"><span data-stu-id="07c8c-211">The returned `Task` indicates that the work has not completed.</span></span> <span data-ttu-id="07c8c-212">Metoda zostanie wznowiona po zakończeniu oczekiwanego zadania.</span><span class="sxs-lookup"><span data-stu-id="07c8c-212">The method resumes when the awaited task completes.</span></span> <span data-ttu-id="07c8c-213">Po wykonaniu do zakończenia, zwrócony `Task` wskazuje, że jest zakończona.</span><span class="sxs-lookup"><span data-stu-id="07c8c-213">When it has executed to completion, the returned `Task` indicates that it is complete.</span></span>
<span data-ttu-id="07c8c-214">Kod wywołujący można `Task` monitorować, który powrócił, aby określić, kiedy została ukończona.</span><span class="sxs-lookup"><span data-stu-id="07c8c-214">Calling code can monitor that returned `Task` to determine when it has completed.</span></span>

<span data-ttu-id="07c8c-215">Możesz wywołać tę nową `Main` metodę w metodzie:</span><span class="sxs-lookup"><span data-stu-id="07c8c-215">You can call this new method in your `Main` method:</span></span>

```csharp
ShowTeleprompter().Wait();
```

<span data-ttu-id="07c8c-216">W tym `Main`miejscu , w , kod nie synchronicznie czekać.</span><span class="sxs-lookup"><span data-stu-id="07c8c-216">Here, in `Main`, the code does synchronously wait.</span></span> <span data-ttu-id="07c8c-217">Należy użyć `await` operatora zamiast synchronicznie oczekiwania, gdy jest to możliwe.</span><span class="sxs-lookup"><span data-stu-id="07c8c-217">You should use the `await` operator instead of synchronously waiting whenever possible.</span></span> <span data-ttu-id="07c8c-218">Jednak w `Main` metodzie aplikacji konsoli nie można `await` użyć operatora.</span><span class="sxs-lookup"><span data-stu-id="07c8c-218">But, in a console application's `Main` method, you cannot use the `await` operator.</span></span> <span data-ttu-id="07c8c-219">Spowodowałoby to zamknięcie aplikacji przed zakończeniem wszystkich zadań.</span><span class="sxs-lookup"><span data-stu-id="07c8c-219">That would result in the application exiting before all tasks have completed.</span></span>

> [!NOTE]
> <span data-ttu-id="07c8c-220">Jeśli używasz języka C# 7.1 lub nowszego, możesz tworzyć aplikacje konsoli za pomocą [ `async` `Main` metody](../whats-new/csharp-7-1.md#async-main).</span><span class="sxs-lookup"><span data-stu-id="07c8c-220">If you use C# 7.1 or later, you can create console applications with [`async` `Main` method](../whats-new/csharp-7-1.md#async-main).</span></span>

<span data-ttu-id="07c8c-221">Następnie należy napisać drugą metodę asynchroniczną, aby odczytać z Konsoli i obserwować klawisze "<" (mniej niż), ">" (większa niż) i "X" lub "x".</span><span class="sxs-lookup"><span data-stu-id="07c8c-221">Next, you need to write the second asynchronous method to read from the Console and watch for the '<' (less than), '>' (greater than) and 'X' or 'x' keys.</span></span> <span data-ttu-id="07c8c-222">Oto metoda dodania dla tego zadania:</span><span class="sxs-lookup"><span data-stu-id="07c8c-222">Here's the method you add for that task:</span></span>

```csharp
private static async Task GetInput()
{
    var delay = 200;
    Action work = () =>
    {
        do {
            var key = Console.ReadKey(true);
            if (key.KeyChar == '>')
            {
                delay -= 10;
            }
            else if (key.KeyChar == '<')
            {
                delay += 10;
            }
            else if (key.KeyChar == 'X' || key.KeyChar == 'x')
            {
                break;
            }
        } while (true);
    };
    await Task.Run(work);
}
```

<span data-ttu-id="07c8c-223">Spowoduje to utworzenie wyrażenia lambda do reprezentowania delegata, <xref:System.Action> który odczytuje klucz z konsoli i modyfikuje zmienną lokalną reprezentującą opóźnienie, gdy użytkownik naciśnie klucze "<" (mniej niż) lub ">" (większe niż).</span><span class="sxs-lookup"><span data-stu-id="07c8c-223">This creates a lambda expression to represent an <xref:System.Action> delegate that reads a key from the Console and modifies a local variable representing the delay when the user presses the '<' (less than) or '>' (greater than) keys.</span></span> <span data-ttu-id="07c8c-224">Metoda delegowania kończy się, gdy użytkownik naciśnie klawisze "X" lub "x", co pozwala użytkownikowi zatrzymać wyświetlanie tekstu w dowolnym momencie.</span><span class="sxs-lookup"><span data-stu-id="07c8c-224">The delegate method finishes when user presses the 'X' or 'x'  keys, which allow the user to stop the text display at any time.</span></span> <span data-ttu-id="07c8c-225">Ta metoda <xref:System.Console.ReadKey> służy do blokowania i oczekiwania na użytkownika, aby nacisnąć klawisz.</span><span class="sxs-lookup"><span data-stu-id="07c8c-225">This method uses <xref:System.Console.ReadKey> to block and wait for the user to press a key.</span></span>

<span data-ttu-id="07c8c-226">Aby zakończyć tę funkcję, należy `async Task` utworzyć nową metodę zwracania,`GetInput` która `ShowTeleprompter`uruchamia oba te zadania ( i ), a także zarządza udostępnionymi danymi między tymi dwoma zadaniami.</span><span class="sxs-lookup"><span data-stu-id="07c8c-226">To finish this feature, you need to create a new `async Task` returning method that starts both of these tasks (`GetInput` and `ShowTeleprompter`), and also manages the shared data between these two tasks.</span></span>

<span data-ttu-id="07c8c-227">Nadszedł czas, aby utworzyć klasę, która może obsługiwać udostępnione dane między tymi dwoma zadaniami.</span><span class="sxs-lookup"><span data-stu-id="07c8c-227">It's time to create a class that can handle the shared data between these two tasks.</span></span> <span data-ttu-id="07c8c-228">Ta klasa zawiera dwie właściwości publiczne: opóźnienie `Done` i flagę wskazującą, że plik został całkowicie odczytany:</span><span class="sxs-lookup"><span data-stu-id="07c8c-228">This class contains two public properties: the delay, and a flag `Done` to indicate that the file has been completely read:</span></span>

```csharp
namespace TeleprompterConsole
{
    internal class TelePrompterConfig
    {
        public int DelayInMilliseconds { get; private set; } = 200;

        public void UpdateDelay(int increment) // negative to speed up
        {
            var newDelay = Min(DelayInMilliseconds + increment, 1000);
            newDelay = Max(newDelay, 20);
            DelayInMilliseconds = newDelay;
        }

        public bool Done { get; private set; }

        public void SetDone()
        {
            Done = true;
        }
    }
}
```

<span data-ttu-id="07c8c-229">Umieść tę klasę w nowym pliku i ująć tę klasę w obszarze `TeleprompterConsole` nazw, jak pokazano powyżej.</span><span class="sxs-lookup"><span data-stu-id="07c8c-229">Put that class in a new file, and enclose that class in the `TeleprompterConsole` namespace as shown above.</span></span> <span data-ttu-id="07c8c-230">Należy również dodać instrukcję, `using static` aby można było `Min` `Max` odwoływać się do i metod bez otaczających nazw klasy lub obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="07c8c-230">You'll also need to add a `using static` statement so that you can reference the `Min` and `Max` methods without the enclosing class or namespace names.</span></span> <span data-ttu-id="07c8c-231">Instrukcja [`using static`](../language-reference/keywords/using-static.md) importuje metody z jednej klasy.</span><span class="sxs-lookup"><span data-stu-id="07c8c-231">A [`using static`](../language-reference/keywords/using-static.md) statement imports the methods from one class.</span></span> <span data-ttu-id="07c8c-232">Jest to w `using` przeciwieństwie do instrukcji używanych do tego momentu, które zaimportowały wszystkie klasy z obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="07c8c-232">This is in contrast with the `using` statements used up to this point that have imported all classes from a namespace.</span></span>

```csharp
using static System.Math;
```

<span data-ttu-id="07c8c-233">Następnie należy zaktualizować `ShowTeleprompter` i `GetInput` metody, aby `config` użyć nowego obiektu.</span><span class="sxs-lookup"><span data-stu-id="07c8c-233">Next, you need to update the `ShowTeleprompter` and `GetInput` methods to use the new `config` object.</span></span> <span data-ttu-id="07c8c-234">Zapisz jedną `Task` ostateczną metodę zwracania, `async` aby uruchomić oba zadania i zakończyć po zakończeniu pierwszego zadania:</span><span class="sxs-lookup"><span data-stu-id="07c8c-234">Write one final `Task` returning `async` method to start both tasks and exit when the first task finishes:</span></span>

```csharp
private static async Task RunTeleprompter()
{
    var config = new TelePrompterConfig();
    var displayTask = ShowTeleprompter(config);

    var speedTask = GetInput(config);
    await Task.WhenAny(displayTask, speedTask);
}
```

<span data-ttu-id="07c8c-235">Jedną z nowych metod <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])> jest tutaj wywołanie.</span><span class="sxs-lookup"><span data-stu-id="07c8c-235">The one new method here is the <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])> call.</span></span> <span data-ttu-id="07c8c-236">Spowoduje to `Task` utworzenie, które kończy się tak szybko, jak każde z zadań na liście argumentów zostanie zakończone.</span><span class="sxs-lookup"><span data-stu-id="07c8c-236">That creates a `Task` that finishes as soon as any of the tasks in its argument list completes.</span></span>

<span data-ttu-id="07c8c-237">Następnie należy zaktualizować zarówno `ShowTeleprompter` `GetInput` metody, jak `config` i metody, aby użyć obiektu dla opóźnienia:</span><span class="sxs-lookup"><span data-stu-id="07c8c-237">Next, you need to update both the `ShowTeleprompter` and `GetInput` methods to use the `config` object for the delay:</span></span>

```csharp
private static async Task ShowTeleprompter(TelePrompterConfig config)
{
    var words = ReadFrom("sampleQuotes.txt");
    foreach (var word in words)
    {
        Console.Write(word);
        if (!string.IsNullOrWhiteSpace(word))
        {
            await Task.Delay(config.DelayInMilliseconds);
        }
    }
    config.SetDone();
}

private static async Task GetInput(TelePrompterConfig config)
{
    Action work = () =>
    {
        do {
            var key = Console.ReadKey(true);
            if (key.KeyChar == '>')
                config.UpdateDelay(-10);
            else if (key.KeyChar == '<')
                config.UpdateDelay(10);
            else if (key.KeyChar == 'X' || key.KeyChar == 'x')
                config.SetDone();
        } while (!config.Done);
    };
    await Task.Run(work);
}
```

<span data-ttu-id="07c8c-238">Ta nowa `ShowTeleprompter` wersja wywołuje nową `TeleprompterConfig` metodę w klasie.</span><span class="sxs-lookup"><span data-stu-id="07c8c-238">This new version of `ShowTeleprompter` calls a new method in the `TeleprompterConfig` class.</span></span> <span data-ttu-id="07c8c-239">Teraz musisz zaktualizować, `Main` `RunTeleprompter` aby `ShowTeleprompter`zadzwonić, a nie:</span><span class="sxs-lookup"><span data-stu-id="07c8c-239">Now, you need to update `Main` to call `RunTeleprompter` instead of `ShowTeleprompter`:</span></span>

```csharp
RunTeleprompter().Wait();
```

## <a name="conclusion"></a><span data-ttu-id="07c8c-240">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="07c8c-240">Conclusion</span></span>

<span data-ttu-id="07c8c-241">W tym samouczku pokazano szereg funkcji wokół języka C# i bibliotek .NET Core związanych z pracą w aplikacjach konsoli.</span><span class="sxs-lookup"><span data-stu-id="07c8c-241">This tutorial showed you a number of the features around the C# language and the .NET Core libraries related to working in Console applications.</span></span> <span data-ttu-id="07c8c-242">Można wykorzystać tę wiedzę, aby dowiedzieć się więcej o języku i klas wprowadzonych tutaj.</span><span class="sxs-lookup"><span data-stu-id="07c8c-242">You can build on this knowledge to explore more about the language, and the classes introduced here.</span></span> <span data-ttu-id="07c8c-243">Widzieliście podstawy we/wy pliku i konsoli, blokowanie i nieblokowanie użycia programowania asynchronicznego opartego na zadaniach, przewodnik po języku C# i sposób organizowania programów C#oraz interfejs cli .NET Core.</span><span class="sxs-lookup"><span data-stu-id="07c8c-243">You've seen the basics of File and Console I/O, blocking and non-blocking use of the Task-based asynchronous programming, a tour of the C# language and how C# programs are organized, and the .NET Core CLI.</span></span>

<span data-ttu-id="07c8c-244">Aby uzyskać więcej informacji na temat we/wy pliku, zobacz [temat We/Wy plik i strumień.](../../standard/io/index.md)</span><span class="sxs-lookup"><span data-stu-id="07c8c-244">For more information about File I/O, see the [File and Stream I/O](../../standard/io/index.md) topic.</span></span> <span data-ttu-id="07c8c-245">Aby uzyskać więcej informacji na temat asynchronicznego modelu programowania używanego w tym samouczku, zobacz temat [Programowania asynchronicznego opartego na zadaniach](../..//standard/parallel-programming/task-based-asynchronous-programming.md) i temat [programowania asynchronicznego.](../async.md)</span><span class="sxs-lookup"><span data-stu-id="07c8c-245">For more information about asynchronous programming model used in this tutorial, see the [Task-based Asynchronous Programming](../..//standard/parallel-programming/task-based-asynchronous-programming.md) topic and the [Asynchronous programming](../async.md) topic.</span></span>

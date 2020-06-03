---
title: Aplikacja konsoli
description: W tym samouczku przedstawiono szereg funkcji platformy .NET Core i języka C#.
ms.date: 03/06/2017
ms.technology: csharp-fundamentals
ms.assetid: 883cd93d-50ce-4144-b7c9-2df28d9c11a0
ms.openlocfilehash: 06affa01b67edeea09088834cf131adb55650bbb
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/05/2020
ms.locfileid: "82794666"
---
# <a name="console-app"></a><span data-ttu-id="19376-103">Aplikacja konsolowa</span><span class="sxs-lookup"><span data-stu-id="19376-103">Console app</span></span>

<span data-ttu-id="19376-104">W tym samouczku przedstawiono szereg funkcji platformy .NET Core i języka C#.</span><span class="sxs-lookup"><span data-stu-id="19376-104">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="19376-105">Dowiesz się:</span><span class="sxs-lookup"><span data-stu-id="19376-105">You'll learn:</span></span>

- <span data-ttu-id="19376-106">Podstawowe informacje dotyczące interfejs wiersza polecenia platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="19376-106">The basics of the .NET Core CLI</span></span>
- <span data-ttu-id="19376-107">Struktura aplikacji konsolowej C#</span><span class="sxs-lookup"><span data-stu-id="19376-107">The structure of a C# Console Application</span></span>
- <span data-ttu-id="19376-108">We/wy konsoli</span><span class="sxs-lookup"><span data-stu-id="19376-108">Console I/O</span></span>
- <span data-ttu-id="19376-109">Podstawy interfejsów API we/wy plików w programie .NET</span><span class="sxs-lookup"><span data-stu-id="19376-109">The basics of File I/O APIs in .NET</span></span>
- <span data-ttu-id="19376-110">Podstawowe informacje na temat programowania asynchronicznego opartego na zadaniach w programie .NET</span><span class="sxs-lookup"><span data-stu-id="19376-110">The basics of the Task-based Asynchronous Programming in .NET</span></span>

<span data-ttu-id="19376-111">Utworzysz aplikację, która odczytuje plik tekstowy, i echo zawartość tego pliku tekstowego do konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="19376-111">You'll build an application that reads a text file, and echoes the contents of that text file to the console.</span></span> <span data-ttu-id="19376-112">Dane wyjściowe do konsoli są w tempie zgodne z odczytem na głos.</span><span class="sxs-lookup"><span data-stu-id="19376-112">The output to the console is paced to match reading it aloud.</span></span> <span data-ttu-id="19376-113">Można przyspieszyć lub spowalniać tempo, naciskając klawisze "<" (mniejsze niż) lub ">" (większe niż).</span><span class="sxs-lookup"><span data-stu-id="19376-113">You can speed up or slow down the pace by pressing the '<' (less than) or '>' (greater than) keys.</span></span>

<span data-ttu-id="19376-114">Ten samouczek zawiera wiele funkcji.</span><span class="sxs-lookup"><span data-stu-id="19376-114">There are a lot of features in this tutorial.</span></span> <span data-ttu-id="19376-115">Kompilujmy je po jednej.</span><span class="sxs-lookup"><span data-stu-id="19376-115">Let's build them one by one.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="19376-116">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="19376-116">Prerequisites</span></span>

- <span data-ttu-id="19376-117">Skonfiguruj maszynę do uruchamiania programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="19376-117">Set up your machine to run .NET Core.</span></span> <span data-ttu-id="19376-118">Instrukcje instalacji można znaleźć na stronie [pliki do pobrania w programie .NET Core](https://dotnet.microsoft.com/download) .</span><span class="sxs-lookup"><span data-stu-id="19376-118">You can find the installation instructions on the [.NET Core downloads](https://dotnet.microsoft.com/download) page.</span></span> <span data-ttu-id="19376-119">Tę aplikację można uruchomić w systemie Windows, Linux, macOS lub w kontenerze platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="19376-119">You can run this application on Windows, Linux, macOS, or in a Docker container.</span></span>

- <span data-ttu-id="19376-120">Zainstaluj swój ulubiony Edytor kodu.</span><span class="sxs-lookup"><span data-stu-id="19376-120">Install your favorite code editor.</span></span>

## <a name="create-the-app"></a><span data-ttu-id="19376-121">Tworzymy aplikację.</span><span class="sxs-lookup"><span data-stu-id="19376-121">Create the app</span></span>

<span data-ttu-id="19376-122">Pierwszym krokiem jest utworzenie nowej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="19376-122">The first step is to create a new application.</span></span> <span data-ttu-id="19376-123">Otwórz wiersz polecenia i Utwórz nowy katalog dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="19376-123">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="19376-124">Upewnij się, że bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="19376-124">Make that the current directory.</span></span> <span data-ttu-id="19376-125">Wpisz polecenie `dotnet new console` w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="19376-125">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="19376-126">Spowoduje to utworzenie plików początkowych dla podstawowej aplikacji "Hello world".</span><span class="sxs-lookup"><span data-stu-id="19376-126">This creates the starter files for a basic "Hello World" application.</span></span>

<span data-ttu-id="19376-127">Przed rozpoczęciem wprowadzania zmian przejdź do kroku, aby uruchomić prostą aplikację Hello world.</span><span class="sxs-lookup"><span data-stu-id="19376-127">Before you start making modifications, let's go through the steps to run the simple Hello World application.</span></span> <span data-ttu-id="19376-128">Po utworzeniu aplikacji wpisz `dotnet restore` w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="19376-128">After creating the application, type `dotnet restore` at the command prompt.</span></span> <span data-ttu-id="19376-129">To polecenie uruchamia proces przywracania pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="19376-129">This command runs the NuGet package restore process.</span></span> <span data-ttu-id="19376-130">Pakiet NuGet jest menedżerem pakietów platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="19376-130">NuGet is a .NET package manager.</span></span> <span data-ttu-id="19376-131">To polecenie pobiera wszystkie brakujące zależności dla projektu.</span><span class="sxs-lookup"><span data-stu-id="19376-131">This command downloads any of the missing dependencies for your project.</span></span> <span data-ttu-id="19376-132">Ponieważ jest to nowy projekt, nie są stosowane żadne zależności, więc pierwsze uruchomienie spowoduje pobranie środowiska .NET Core.</span><span class="sxs-lookup"><span data-stu-id="19376-132">As this is a new project, none of the dependencies are in place, so the first run will download the .NET Core framework.</span></span> <span data-ttu-id="19376-133">Po tym początkowym kroku będziesz mieć możliwość uruchamiania tylko wtedy, `dotnet restore` gdy dodasz nowe pakiety zależne lub zaktualizujesz wersje dowolnych zależności.</span><span class="sxs-lookup"><span data-stu-id="19376-133">After this initial step, you will only need to run `dotnet restore` when you add new dependent packages, or update the versions of any of your dependencies.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="19376-134">Po przywróceniu pakietów zostanie uruchomione polecenie `dotnet build` .</span><span class="sxs-lookup"><span data-stu-id="19376-134">After restoring packages, you run `dotnet build`.</span></span> <span data-ttu-id="19376-135">Spowoduje to uruchomienie aparatu kompilacji i utworzenie pliku wykonywalnego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="19376-135">This executes the build engine and creates your application executable.</span></span> <span data-ttu-id="19376-136">`dotnet run`Na koniec uruchamiasz aplikację.</span><span class="sxs-lookup"><span data-stu-id="19376-136">Finally, you execute `dotnet run` to run your application.</span></span>

<span data-ttu-id="19376-137">Prosty kod aplikacji Hello world to wszystko w Program.cs.</span><span class="sxs-lookup"><span data-stu-id="19376-137">The simple Hello World application code is all in Program.cs.</span></span> <span data-ttu-id="19376-138">Otwórz ten plik za pomocą ulubionego edytora tekstu.</span><span class="sxs-lookup"><span data-stu-id="19376-138">Open that file with your favorite text editor.</span></span> <span data-ttu-id="19376-139">Zamierzamy wprowadzić Twoje pierwsze zmiany.</span><span class="sxs-lookup"><span data-stu-id="19376-139">We're about to make our first changes.</span></span> <span data-ttu-id="19376-140">W górnej części pliku Zobacz instrukcję using:</span><span class="sxs-lookup"><span data-stu-id="19376-140">At the top of the file, see a using statement:</span></span>

```csharp
using System;
```

<span data-ttu-id="19376-141">Ta instrukcja informuje kompilator, że wszystkie typy z `System` przestrzeni nazw znajdują się w zakresie.</span><span class="sxs-lookup"><span data-stu-id="19376-141">This statement tells the compiler that any types from the `System` namespace are in scope.</span></span> <span data-ttu-id="19376-142">Podobnie jak w przypadku innych języków zorientowanych na obiekt, które mogą być używane, C# używa przestrzeni nazw do organizowania typów.</span><span class="sxs-lookup"><span data-stu-id="19376-142">Like other Object Oriented languages you may have used, C# uses namespaces to organize types.</span></span> <span data-ttu-id="19376-143">Ten program Hello world nie jest inny.</span><span class="sxs-lookup"><span data-stu-id="19376-143">This Hello World program is no different.</span></span> <span data-ttu-id="19376-144">Można zobaczyć, że program jest ujęty w przestrzeń nazw o nazwie na podstawie nazwy bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="19376-144">You can see that the program is enclosed in the namespace with the name based on the name of the current directory.</span></span> <span data-ttu-id="19376-145">Na potrzeby tego samouczka Zmieńmy nazwę przestrzeni nazw na `TeleprompterConsole` :</span><span class="sxs-lookup"><span data-stu-id="19376-145">For this tutorial, let's change the name of the namespace to `TeleprompterConsole`:</span></span>

```csharp
namespace TeleprompterConsole
```

## <a name="reading-and-echoing-the-file"></a><span data-ttu-id="19376-146">Odczytywanie i echo pliku</span><span class="sxs-lookup"><span data-stu-id="19376-146">Reading and Echoing the File</span></span>

<span data-ttu-id="19376-147">Pierwsza funkcja do dodania to możliwość odczytywania pliku tekstowego i wyświetlania całego tekstu w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="19376-147">The first feature to add is the ability to read a text file and display all that text to the console.</span></span> <span data-ttu-id="19376-148">Najpierw Dodajmy plik tekstowy.</span><span class="sxs-lookup"><span data-stu-id="19376-148">First, let's add a text file.</span></span> <span data-ttu-id="19376-149">Skopiuj plik [sampleQuotes. txt](https://github.com/dotnet/samples/raw/master/csharp/getting-started/console-teleprompter/sampleQuotes.txt) z repozytorium GitHub dla tego [przykładu](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-teleprompter) do katalogu projektu.</span><span class="sxs-lookup"><span data-stu-id="19376-149">Copy the [sampleQuotes.txt](https://github.com/dotnet/samples/raw/master/csharp/getting-started/console-teleprompter/sampleQuotes.txt) file from the GitHub repository for this [sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-teleprompter) into your project directory.</span></span> <span data-ttu-id="19376-150">Będzie to skrypt aplikacji.</span><span class="sxs-lookup"><span data-stu-id="19376-150">This will serve as the script for your application.</span></span> <span data-ttu-id="19376-151">Jeśli chcesz uzyskać informacje dotyczące sposobu pobierania przykładowej aplikacji dla tego tematu, zobacz instrukcje w temacie [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples) .</span><span class="sxs-lookup"><span data-stu-id="19376-151">If you would like information on how to download the sample app for this topic, see the instructions in the [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples) topic.</span></span>

<span data-ttu-id="19376-152">Następnie Dodaj następującą metodę do `Program` klasy (bezpośrednio poniżej `Main` metody):</span><span class="sxs-lookup"><span data-stu-id="19376-152">Next, add the following method in your `Program` class (right below the `Main` method):</span></span>

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

<span data-ttu-id="19376-153">Ta metoda używa typów z dwóch nowych przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="19376-153">This method uses types from two new namespaces.</span></span> <span data-ttu-id="19376-154">Aby można było skompilować kompilację, należy dodać dwa następujące wiersze na początku pliku:</span><span class="sxs-lookup"><span data-stu-id="19376-154">For this to compile you'll need to add the following two lines to the top of the file:</span></span>

```csharp
using System.Collections.Generic;
using System.IO;
```

<span data-ttu-id="19376-155"><xref:System.Collections.Generic.IEnumerable%601>Interfejs jest zdefiniowany w <xref:System.Collections.Generic> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="19376-155">The <xref:System.Collections.Generic.IEnumerable%601> interface is defined in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="19376-156"><xref:System.IO.File>Klasa jest zdefiniowana w <xref:System.IO> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="19376-156">The <xref:System.IO.File> class is defined in the <xref:System.IO> namespace.</span></span>

<span data-ttu-id="19376-157">Ta metoda jest specjalnym typem metody języka C# zwanej *metodą iteratora*.</span><span class="sxs-lookup"><span data-stu-id="19376-157">This method is a special type of C# method called an *Iterator method*.</span></span> <span data-ttu-id="19376-158">Metody modułu wyliczającego zwracają sekwencje zwracające opóźnieniem.</span><span class="sxs-lookup"><span data-stu-id="19376-158">Enumerator methods return sequences that are evaluated lazily.</span></span> <span data-ttu-id="19376-159">Oznacza to, że każdy element w sekwencji jest generowany w miarę żądania przez kod korzystający z sekwencji.</span><span class="sxs-lookup"><span data-stu-id="19376-159">That means each item in the sequence is generated as it is requested by the code consuming the sequence.</span></span> <span data-ttu-id="19376-160">Metody modułu wyliczającego to metody, które zawierają jedną lub więcej [`yield return`](../language-reference/keywords/yield.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="19376-160">Enumerator methods are methods that contain one or more [`yield return`](../language-reference/keywords/yield.md) statements.</span></span> <span data-ttu-id="19376-161">Obiekt zwrócony przez `ReadFrom` metodę zawiera kod generujący każdy element w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="19376-161">The object returned by the `ReadFrom` method contains the code to generate each item in the sequence.</span></span> <span data-ttu-id="19376-162">W tym przykładzie, który obejmuje odczytywanie następnego wiersza tekstu z pliku źródłowego i zwracanie tego ciągu.</span><span class="sxs-lookup"><span data-stu-id="19376-162">In this example, that involves reading the next line of text from the source file, and returning that string.</span></span> <span data-ttu-id="19376-163">Za każdym razem, gdy wywołujący kod żąda następnego elementu z sekwencji, kod odczytuje następny wiersz tekstu z pliku i zwraca go.</span><span class="sxs-lookup"><span data-stu-id="19376-163">Each time the calling code requests the next item from the sequence, the code reads the next line of text from the file and returns it.</span></span> <span data-ttu-id="19376-164">Gdy plik jest całkowicie odczytywany, sekwencja wskazuje, że nie ma więcej elementów.</span><span class="sxs-lookup"><span data-stu-id="19376-164">When the file is completely read, the sequence indicates that there are no more items.</span></span>

<span data-ttu-id="19376-165">Istnieją dwa inne elementy składni języka C#, które mogą być nowe dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="19376-165">There are two other C# syntax elements that may be new to you.</span></span> <span data-ttu-id="19376-166">[`using`](../language-reference/keywords/using-statement.md)Instrukcja w tej metodzie zarządza oczyszczaniem zasobów.</span><span class="sxs-lookup"><span data-stu-id="19376-166">The [`using`](../language-reference/keywords/using-statement.md) statement in this method manages resource cleanup.</span></span> <span data-ttu-id="19376-167">Zmienna, która została zainicjowana w `using` instrukcji ( `reader` w tym przykładzie) musi implementować <xref:System.IDisposable> interfejs.</span><span class="sxs-lookup"><span data-stu-id="19376-167">The variable that is initialized in the `using` statement (`reader`, in this example) must implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="19376-168">Ten interfejs definiuje pojedynczą metodę, `Dispose` która powinna być wywoływana, gdy zasób powinien zostać wyznaczony.</span><span class="sxs-lookup"><span data-stu-id="19376-168">That interface defines a single method, `Dispose`, that should be called when the resource should be released.</span></span> <span data-ttu-id="19376-169">Kompilator generuje to wywołanie, gdy wykonanie osiągnie zamykający nawias klamrowy `using` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="19376-169">The compiler generates that call when execution reaches the closing brace of the `using` statement.</span></span> <span data-ttu-id="19376-170">Kod wygenerowany przez kompilator zapewnia, że zasób jest wydawany nawet wtedy, gdy wyjątek jest zgłaszany z kodu w bloku zdefiniowanym przez instrukcję using.</span><span class="sxs-lookup"><span data-stu-id="19376-170">The compiler-generated code ensures that the resource is released even if an exception is thrown from the code in the block defined by the using statement.</span></span>

<span data-ttu-id="19376-171">`reader`Zmienna jest definiowana przy użyciu `var` słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="19376-171">The `reader` variable is defined using the `var` keyword.</span></span> <span data-ttu-id="19376-172">[`var`](../language-reference/keywords/var.md)definiuje *niejawnie wpisaną zmienną lokalną*.</span><span class="sxs-lookup"><span data-stu-id="19376-172">[`var`](../language-reference/keywords/var.md) defines an *implicitly typed local variable*.</span></span> <span data-ttu-id="19376-173">Oznacza to, że typ zmiennej jest określany przez typ czasu kompilacji obiektu przypisanego do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="19376-173">That means the type of the variable is determined by the compile-time type of the object assigned to the variable.</span></span> <span data-ttu-id="19376-174">Tutaj jest to wartość zwracana z <xref:System.IO.File.OpenText(System.String)> metody, która jest <xref:System.IO.StreamReader> obiektem.</span><span class="sxs-lookup"><span data-stu-id="19376-174">Here, that is the return value from the <xref:System.IO.File.OpenText(System.String)> method, which is a <xref:System.IO.StreamReader> object.</span></span>

<span data-ttu-id="19376-175">Teraz uzupełnimy kod w celu odczytania pliku w `Main` metodzie:</span><span class="sxs-lookup"><span data-stu-id="19376-175">Now, let's fill in the code to read the file in the `Main` method:</span></span>

```csharp
var lines = ReadFrom("sampleQuotes.txt");
foreach (var line in lines)
{
    Console.WriteLine(line);
}
```

<span data-ttu-id="19376-176">Uruchom program (za pomocą programu `dotnet run` ) i zobaczysz, że każdy wiersz został wydrukowany w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="19376-176">Run the program (using `dotnet run`) and you can see every line printed out to the console.</span></span>

## <a name="adding-delays-and-formatting-output"></a><span data-ttu-id="19376-177">Dodawanie opóźnień i formatowanie danych wyjściowych</span><span class="sxs-lookup"><span data-stu-id="19376-177">Adding Delays and Formatting output</span></span>

<span data-ttu-id="19376-178">Zawartość jest zbyt szybka, aby można ją było odczytać.</span><span class="sxs-lookup"><span data-stu-id="19376-178">What you have is being displayed far too fast to read aloud.</span></span> <span data-ttu-id="19376-179">Teraz musisz dodać opóźnienia w danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="19376-179">Now you need to add the delays in the output.</span></span> <span data-ttu-id="19376-180">Po rozpoczęciu będziesz kompilować część kodu podstawowego, który umożliwia przetwarzanie asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="19376-180">As you start, you'll be building some of the core code that enables asynchronous processing.</span></span> <span data-ttu-id="19376-181">Jednak te pierwsze kroki będą zgodne z kilkoma wzorcami.</span><span class="sxs-lookup"><span data-stu-id="19376-181">However, these first steps will follow a few anti-patterns.</span></span> <span data-ttu-id="19376-182">Wzorce są podkreślane w komentarzach podczas dodawania kodu, a kod zostanie zaktualizowany w dalszych krokach.</span><span class="sxs-lookup"><span data-stu-id="19376-182">The anti-patterns are pointed out in comments as you add the code, and the code will be updated in later steps.</span></span>

<span data-ttu-id="19376-183">Ta sekcja zawiera dwa kroki.</span><span class="sxs-lookup"><span data-stu-id="19376-183">There are two steps to this section.</span></span> <span data-ttu-id="19376-184">Najpierw należy zaktualizować metodę iteratora w celu zwrócenia pojedynczych słów zamiast całych wierszy.</span><span class="sxs-lookup"><span data-stu-id="19376-184">First, you'll update the iterator method to return single words instead of entire lines.</span></span> <span data-ttu-id="19376-185">Jest to wykonywane z tymi modyfikacjami.</span><span class="sxs-lookup"><span data-stu-id="19376-185">That's done with these modifications.</span></span> <span data-ttu-id="19376-186">Zastąp `yield return line;` instrukcję następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="19376-186">Replace the `yield return line;` statement with the following code:</span></span>

```csharp
var words = line.Split(' ');
foreach (var word in words)
{
    yield return word + " ";
}
yield return Environment.NewLine;
```

<span data-ttu-id="19376-187">Następnie należy zmodyfikować sposób korzystania z wierszy pliku i dodać opóźnienie po zapisaniu każdego wyrazu.</span><span class="sxs-lookup"><span data-stu-id="19376-187">Next, you need to modify how you consume the lines of the file, and add a delay after writing each word.</span></span> <span data-ttu-id="19376-188">Zamień `Console.WriteLine(line)` instrukcję w `Main` metodzie na następujący blok:</span><span class="sxs-lookup"><span data-stu-id="19376-188">Replace the `Console.WriteLine(line)` statement in the `Main` method with the following block:</span></span>

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

<span data-ttu-id="19376-189"><xref:System.Threading.Tasks.Task>Klasa znajduje się w <xref:System.Threading.Tasks> przestrzeni nazw, dlatego należy dodać tę `using` instrukcję na początku pliku:</span><span class="sxs-lookup"><span data-stu-id="19376-189">The <xref:System.Threading.Tasks.Task> class is in the <xref:System.Threading.Tasks> namespace, so you need to add that `using` statement at the top of file:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="19376-190">Uruchom przykład i sprawdź dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="19376-190">Run the sample, and check the output.</span></span> <span data-ttu-id="19376-191">Teraz każdy pojedynczy wyraz jest drukowany, po którym następuje opóźnienie 200 ms.</span><span class="sxs-lookup"><span data-stu-id="19376-191">Now, each single word is printed, followed by a 200 ms delay.</span></span> <span data-ttu-id="19376-192">Jednak wyświetlane dane wyjściowe pokazują pewne problemy, ponieważ źródłowy plik tekstowy ma kilka wierszy, które mają więcej niż 80 znaków bez przerwy w wierszu.</span><span class="sxs-lookup"><span data-stu-id="19376-192">However, the displayed output shows some issues because the source text file has several lines that have more than 80 characters without a line break.</span></span> <span data-ttu-id="19376-193">Może to być trudne do odczytania podczas przewijania przez program.</span><span class="sxs-lookup"><span data-stu-id="19376-193">That can be hard to read while it's scrolling by.</span></span> <span data-ttu-id="19376-194">Jest to łatwe do naprawienia.</span><span class="sxs-lookup"><span data-stu-id="19376-194">That's easy to fix.</span></span> <span data-ttu-id="19376-195">Będziesz śledzić długość każdego wiersza i generować nowy wiersz zawsze, gdy długość wiersza osiągnie określony próg.</span><span class="sxs-lookup"><span data-stu-id="19376-195">You'll just keep track of the length of each line, and generate a new line whenever the line length reaches a certain threshold.</span></span> <span data-ttu-id="19376-196">Zadeklaruj zmienną lokalną po deklaracji `words` `ReadFrom` metody, która posiada długość wiersza:</span><span class="sxs-lookup"><span data-stu-id="19376-196">Declare a local variable after the declaration of `words` in the `ReadFrom` method that holds the line length:</span></span>

```csharp
var lineLength = 0;
```

<span data-ttu-id="19376-197">Następnie Dodaj następujący kod po `yield return word + " ";` instrukcji (przed zamykającym nawiasem klamrowym):</span><span class="sxs-lookup"><span data-stu-id="19376-197">Then, add the following code after the `yield return word + " ";` statement (before the closing brace):</span></span>

```csharp
lineLength += word.Length + 1;
if (lineLength > 70)
{
    yield return Environment.NewLine;
    lineLength = 0;
}
```

<span data-ttu-id="19376-198">Uruchom próbkę i będzie można odczytywać na głos ze wstępnie skonfigurowanym tempem.</span><span class="sxs-lookup"><span data-stu-id="19376-198">Run the sample, and you'll be able to read aloud at its pre-configured pace.</span></span>

## <a name="async-tasks"></a><span data-ttu-id="19376-199">Zadania asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="19376-199">Async Tasks</span></span>

<span data-ttu-id="19376-200">W tym ostatnim kroku dodasz kod, aby zapisać dane wyjściowe asynchronicznie w jednym zadaniu, a jednocześnie uruchomić inne zadanie odczytujące dane wejściowe od użytkownika, jeśli chcesz przyspieszyć lub spowolnić wyświetlanie tekstu lub zatrzymać wyświetlanie tekstu.</span><span class="sxs-lookup"><span data-stu-id="19376-200">In this final step, you'll add the code to write the output asynchronously in one task, while also running another task to read input from the user if they want to speed up or slow down the text display, or stop the text display altogether.</span></span> <span data-ttu-id="19376-201">Obejmuje to kilka kroków i zakończenie, które będą potrzebne do wszystkich niezbędnych aktualizacji.</span><span class="sxs-lookup"><span data-stu-id="19376-201">This has a few steps in it and by the end, you'll have all the updates that you need.</span></span> <span data-ttu-id="19376-202">Pierwszym krokiem jest utworzenie asynchronicznej <xref:System.Threading.Tasks.Task> metody zwracającej, która reprezentuje kod, który został utworzony do odczytu i wyświetlenia pliku.</span><span class="sxs-lookup"><span data-stu-id="19376-202">The first step is to create an asynchronous <xref:System.Threading.Tasks.Task> returning method that represents the code you've created so far to read and display the file.</span></span>

<span data-ttu-id="19376-203">Dodaj tę metodę do `Program` klasy (jest ona pobierana z treści `Main` metody):</span><span class="sxs-lookup"><span data-stu-id="19376-203">Add this method to your `Program` class (it's taken from the body of your `Main` method):</span></span>

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

<span data-ttu-id="19376-204">Zauważysz dwie zmiany.</span><span class="sxs-lookup"><span data-stu-id="19376-204">You'll notice two changes.</span></span> <span data-ttu-id="19376-205">Po pierwsze, w treści metody, zamiast wywołania <xref:System.Threading.Tasks.Task.Wait> synchronicznie oczekiwanie na zakończenie zadania, ta wersja używa `await` słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="19376-205">First, in the body of the method, instead of calling <xref:System.Threading.Tasks.Task.Wait> to synchronously wait for a task to finish, this version uses the `await` keyword.</span></span> <span data-ttu-id="19376-206">Aby to zrobić, należy dodać `async` modyfikator do sygnatury metody.</span><span class="sxs-lookup"><span data-stu-id="19376-206">In order to do that, you need to add the `async` modifier to the method signature.</span></span> <span data-ttu-id="19376-207">Ta metoda zwraca `Task` .</span><span class="sxs-lookup"><span data-stu-id="19376-207">This method returns a `Task`.</span></span> <span data-ttu-id="19376-208">Zwróć uwagę, że nie ma instrukcji return zwracających `Task` obiekt.</span><span class="sxs-lookup"><span data-stu-id="19376-208">Notice that there are no return statements that return a `Task` object.</span></span> <span data-ttu-id="19376-209">Zamiast tego ten `Task` obiekt jest tworzony przez kod, który kompilator generuje podczas korzystania z `await` operatora.</span><span class="sxs-lookup"><span data-stu-id="19376-209">Instead, that `Task` object is created by code the compiler generates when you use the `await` operator.</span></span> <span data-ttu-id="19376-210">Można Wyobraź sobie, że ta metoda zwraca, gdy osiągnie `await` .</span><span class="sxs-lookup"><span data-stu-id="19376-210">You can imagine that this method returns when it reaches an `await`.</span></span> <span data-ttu-id="19376-211">Zwracana wartość `Task` wskazuje, że pracę nie została ukończona.</span><span class="sxs-lookup"><span data-stu-id="19376-211">The returned `Task` indicates that the work has not completed.</span></span> <span data-ttu-id="19376-212">Metoda zostaje wznowiona po zakończeniu oczekiwania na zadanie.</span><span class="sxs-lookup"><span data-stu-id="19376-212">The method resumes when the awaited task completes.</span></span> <span data-ttu-id="19376-213">Po wykonaniu tej operacji zwrócona wartość `Task` wskazuje, że została zakończona.</span><span class="sxs-lookup"><span data-stu-id="19376-213">When it has executed to completion, the returned `Task` indicates that it is complete.</span></span>
<span data-ttu-id="19376-214">Wywoływanie kodu może monitorować, który zwraca, `Task` Aby określić, kiedy został ukończony.</span><span class="sxs-lookup"><span data-stu-id="19376-214">Calling code can monitor that returned `Task` to determine when it has completed.</span></span>

<span data-ttu-id="19376-215">Tę nową metodę można wywołać w `Main` metodzie:</span><span class="sxs-lookup"><span data-stu-id="19376-215">You can call this new method in your `Main` method:</span></span>

```csharp
ShowTeleprompter().Wait();
```

<span data-ttu-id="19376-216">W tym miejscu `Main` kod wykonuje synchronicznie oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="19376-216">Here, in `Main`, the code does synchronously wait.</span></span> <span data-ttu-id="19376-217">`await`Jeśli to możliwe, należy użyć operatora zamiast synchronicznego oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="19376-217">You should use the `await` operator instead of synchronously waiting whenever possible.</span></span> <span data-ttu-id="19376-218">Ale w metodzie aplikacji konsolowej `Main` nie można używać `await` operatora.</span><span class="sxs-lookup"><span data-stu-id="19376-218">But, in a console application's `Main` method, you cannot use the `await` operator.</span></span> <span data-ttu-id="19376-219">Spowoduje to zakończenie działania aplikacji przed ukończeniem wszystkich zadań.</span><span class="sxs-lookup"><span data-stu-id="19376-219">That would result in the application exiting before all tasks have completed.</span></span>

> [!NOTE]
> <span data-ttu-id="19376-220">Jeśli używasz języka C# 7,1 lub nowszego, możesz tworzyć aplikacje konsolowe za pomocą [ `async` `Main` metody](../whats-new/csharp-7-1.md#async-main).</span><span class="sxs-lookup"><span data-stu-id="19376-220">If you use C# 7.1 or later, you can create console applications with [`async` `Main` method](../whats-new/csharp-7-1.md#async-main).</span></span>

<span data-ttu-id="19376-221">Następnie należy napisać drugą metodę asynchroniczną w celu odczytania z konsoli i obserwowania dla "<" (mniejszej niż), ">" (większe niż) i "X" lub "x".</span><span class="sxs-lookup"><span data-stu-id="19376-221">Next, you need to write the second asynchronous method to read from the Console and watch for the '<' (less than), '>' (greater than) and 'X' or 'x' keys.</span></span> <span data-ttu-id="19376-222">Oto Metoda dodawana do tego zadania:</span><span class="sxs-lookup"><span data-stu-id="19376-222">Here's the method you add for that task:</span></span>

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

<span data-ttu-id="19376-223">Spowoduje to utworzenie wyrażenia lambda do reprezentowania <xref:System.Action> delegata, który odczytuje klucz z konsoli programu i modyfikuje zmienną lokalną reprezentującą opóźnienie, gdy użytkownik naciśnie klawisz "<" (mniej niż) lub ">" (większy niż).</span><span class="sxs-lookup"><span data-stu-id="19376-223">This creates a lambda expression to represent an <xref:System.Action> delegate that reads a key from the Console and modifies a local variable representing the delay when the user presses the '<' (less than) or '>' (greater than) keys.</span></span> <span data-ttu-id="19376-224">Metoda Delegate kończy się, gdy użytkownik naciśnie klawisze "X" lub "x", które umożliwiają użytkownikowi zatrzymanie wyświetlania tekstu w dowolnym momencie.</span><span class="sxs-lookup"><span data-stu-id="19376-224">The delegate method finishes when user presses the 'X' or 'x'  keys, which allow the user to stop the text display at any time.</span></span> <span data-ttu-id="19376-225">Ta metoda używa <xref:System.Console.ReadKey> do blokowania i poczekania użytkownika o naciśnięcie klawisza.</span><span class="sxs-lookup"><span data-stu-id="19376-225">This method uses <xref:System.Console.ReadKey> to block and wait for the user to press a key.</span></span>

<span data-ttu-id="19376-226">Aby zakończyć tę funkcję, należy utworzyć nową `async Task` metodę zwracającą, która uruchamia oba te zadania ( `GetInput` i `ShowTeleprompter` ), a także zarządza danymi udostępnionymi między tymi dwoma zadaniami.</span><span class="sxs-lookup"><span data-stu-id="19376-226">To finish this feature, you need to create a new `async Task` returning method that starts both of these tasks (`GetInput` and `ShowTeleprompter`), and also manages the shared data between these two tasks.</span></span>

<span data-ttu-id="19376-227">Czas na utworzenie klasy, która może obsługiwać udostępnione dane między tymi dwoma zadaniami.</span><span class="sxs-lookup"><span data-stu-id="19376-227">It's time to create a class that can handle the shared data between these two tasks.</span></span> <span data-ttu-id="19376-228">Ta klasa zawiera dwie właściwości publiczne: opóźnienie i flagę `Done` wskazującą, że plik został całkowicie odczytany:</span><span class="sxs-lookup"><span data-stu-id="19376-228">This class contains two public properties: the delay, and a flag `Done` to indicate that the file has been completely read:</span></span>

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

<span data-ttu-id="19376-229">Umieść tę klasę w nowym pliku i umieść ją w `TeleprompterConsole` przestrzeni nazw, jak pokazano powyżej.</span><span class="sxs-lookup"><span data-stu-id="19376-229">Put that class in a new file, and enclose that class in the `TeleprompterConsole` namespace as shown above.</span></span> <span data-ttu-id="19376-230">Należy również dodać `using static` instrukcję, aby można było odwoływać się do `Min` `Max` metod i bez nazwy klasy lub przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="19376-230">You'll also need to add a `using static` statement so that you can reference the `Min` and `Max` methods without the enclosing class or namespace names.</span></span> <span data-ttu-id="19376-231">[`using static`](../language-reference/keywords/using-static.md)Instrukcja importuje metody z jednej klasy.</span><span class="sxs-lookup"><span data-stu-id="19376-231">A [`using static`](../language-reference/keywords/using-static.md) statement imports the methods from one class.</span></span> <span data-ttu-id="19376-232">Jest to w przeciwieństwie do `using` instrukcji używanych do tego punktu, który zaimportował wszystkie klasy z przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="19376-232">This is in contrast with the `using` statements used up to this point that have imported all classes from a namespace.</span></span>

```csharp
using static System.Math;
```

<span data-ttu-id="19376-233">Następnie należy zaktualizować `ShowTeleprompter` metody i, `GetInput` Aby użyć nowego `config` obiektu.</span><span class="sxs-lookup"><span data-stu-id="19376-233">Next, you need to update the `ShowTeleprompter` and `GetInput` methods to use the new `config` object.</span></span> <span data-ttu-id="19376-234">Napisz jedną ostateczną `Task` metodę zwracającą `async` , aby uruchomić oba zadania i wyjść po zakończeniu pierwszego zadania:</span><span class="sxs-lookup"><span data-stu-id="19376-234">Write one final `Task` returning `async` method to start both tasks and exit when the first task finishes:</span></span>

```csharp
private static async Task RunTeleprompter()
{
    var config = new TelePrompterConfig();
    var displayTask = ShowTeleprompter(config);

    var speedTask = GetInput(config);
    await Task.WhenAny(displayTask, speedTask);
}
```

<span data-ttu-id="19376-235">Ta nowa metoda to <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])> wywołanie.</span><span class="sxs-lookup"><span data-stu-id="19376-235">The one new method here is the <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])> call.</span></span> <span data-ttu-id="19376-236">Spowoduje to utworzenie `Task` , który zakończy się zaraz po zakończeniu wszystkich zadań na liście argumentów.</span><span class="sxs-lookup"><span data-stu-id="19376-236">That creates a `Task` that finishes as soon as any of the tasks in its argument list completes.</span></span>

<span data-ttu-id="19376-237">Następnie należy zaktualizować `ShowTeleprompter` metody i, `GetInput` Aby użyć `config` obiektu dla opóźnienia:</span><span class="sxs-lookup"><span data-stu-id="19376-237">Next, you need to update both the `ShowTeleprompter` and `GetInput` methods to use the `config` object for the delay:</span></span>

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

<span data-ttu-id="19376-238">Ta nowa wersja `ShowTeleprompter` wywołuje nową metodę w `TeleprompterConfig` klasie.</span><span class="sxs-lookup"><span data-stu-id="19376-238">This new version of `ShowTeleprompter` calls a new method in the `TeleprompterConfig` class.</span></span> <span data-ttu-id="19376-239">Teraz musisz zaktualizować `Main` do wywołania `RunTeleprompter` zamiast `ShowTeleprompter` :</span><span class="sxs-lookup"><span data-stu-id="19376-239">Now, you need to update `Main` to call `RunTeleprompter` instead of `ShowTeleprompter`:</span></span>

```csharp
RunTeleprompter().Wait();
```

## <a name="conclusion"></a><span data-ttu-id="19376-240">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="19376-240">Conclusion</span></span>

<span data-ttu-id="19376-241">W tym samouczku pokazano kilka funkcji języka C# i bibliotek .NET Core związanych z pracą w aplikacjach konsolowych.</span><span class="sxs-lookup"><span data-stu-id="19376-241">This tutorial showed you a number of the features around the C# language and the .NET Core libraries related to working in Console applications.</span></span> <span data-ttu-id="19376-242">Możesz utworzyć tę wiedzę, aby dowiedzieć się więcej o języku i klasach wprowadzonych w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="19376-242">You can build on this knowledge to explore more about the language, and the classes introduced here.</span></span> <span data-ttu-id="19376-243">Zaobserwowano podstawowe informacje na temat operacji we/wy na plikach i konsoli, blokowanie i nieblokowanie użycia programowania asynchronicznego opartego na zadaniach, przewodnik po języku C# oraz sposób organizowania programów w języku C# oraz interfejs wiersza polecenia platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="19376-243">You've seen the basics of File and Console I/O, blocking and non-blocking use of the Task-based asynchronous programming, a tour of the C# language and how C# programs are organized, and the .NET Core CLI.</span></span>

<span data-ttu-id="19376-244">Aby uzyskać więcej informacji na temat operacji we/wy plików, zobacz temat [plik i strumień we/wy](../../standard/io/index.md) .</span><span class="sxs-lookup"><span data-stu-id="19376-244">For more information about File I/O, see the [File and Stream I/O](../../standard/io/index.md) topic.</span></span> <span data-ttu-id="19376-245">Aby uzyskać więcej informacji o modelu programowania asynchronicznego używanym w tym samouczku, zapoznaj się z tematem [programowanie asynchroniczne oparte na zadaniach](../../standard/parallel-programming/task-based-asynchronous-programming.md) i w temacie [programowanie asynchroniczne](../async.md) .</span><span class="sxs-lookup"><span data-stu-id="19376-245">For more information about asynchronous programming model used in this tutorial, see the [Task-based Asynchronous Programming](../../standard/parallel-programming/task-based-asynchronous-programming.md) topic and the [Asynchronous programming](../async.md) topic.</span></span>

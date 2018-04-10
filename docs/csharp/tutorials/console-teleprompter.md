---
title: Aplikacja konsoli
description: Ten samouczek zawiera szereg funkcji .NET Core i języka C#.
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 03/06/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 883cd93d-50ce-4144-b7c9-2df28d9c11a0
ms.openlocfilehash: cc8645f9eef070d800627ea1c47cf7de1e877783
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="console-application"></a><span data-ttu-id="d984f-104">Aplikacja konsoli</span><span class="sxs-lookup"><span data-stu-id="d984f-104">Console Application</span></span>

## <a name="introduction"></a><span data-ttu-id="d984f-105">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="d984f-105">Introduction</span></span>
<span data-ttu-id="d984f-106">Ten samouczek zawiera szereg funkcji .NET Core i języka C#.</span><span class="sxs-lookup"><span data-stu-id="d984f-106">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="d984f-107">Dowiesz się:</span><span class="sxs-lookup"><span data-stu-id="d984f-107">You’ll learn:</span></span>
*   <span data-ttu-id="d984f-108">Podstawowe informacje o .NET Core interfejsu wiersza polecenia (CLI)</span><span class="sxs-lookup"><span data-stu-id="d984f-108">The basics of the .NET Core Command Line Interface (CLI)</span></span>
*   <span data-ttu-id="d984f-109">Struktura aplikacji Konsolowej C#</span><span class="sxs-lookup"><span data-stu-id="d984f-109">The structure of a C# Console Application</span></span>
*   <span data-ttu-id="d984f-110">Konsola operacje We/Wy</span><span class="sxs-lookup"><span data-stu-id="d984f-110">Console I/O</span></span>
*   <span data-ttu-id="d984f-111">Podstawy interfejsów API we/wy pliku w .NET Core</span><span class="sxs-lookup"><span data-stu-id="d984f-111">The basics of File I/O APIs in .NET Core</span></span>
*   <span data-ttu-id="d984f-112">Podstawy zadań asynchronicznych programowania Model w programie .NET Core</span><span class="sxs-lookup"><span data-stu-id="d984f-112">The basics of the Task Asynchronous Programming Model in .NET Core</span></span>

<span data-ttu-id="d984f-113">Będzie utworzyć aplikację, która odczytuje plik tekstowy i zwraca zawartość tego pliku tekstowego do konsoli.</span><span class="sxs-lookup"><span data-stu-id="d984f-113">You’ll build an application that reads a text file, and echoes the contents of that text file to the console.</span></span> <span data-ttu-id="d984f-114">Dane wyjściowe do konsoli zostanie użytkownika do dopasowania go czytać na głos.</span><span class="sxs-lookup"><span data-stu-id="d984f-114">The output to the console will be paced to match reading it aloud.</span></span> <span data-ttu-id="d984f-115">Można przyspieszyć lub spowolnić tempo przez naciśnięcie przycisku "<" lub ">" kluczy.</span><span class="sxs-lookup"><span data-stu-id="d984f-115">You can speed up or slow down the pace by pressing the ‘<’ or ‘>’ keys.</span></span>

<span data-ttu-id="d984f-116">Istnieje wiele funkcji, w tym samouczku.</span><span class="sxs-lookup"><span data-stu-id="d984f-116">There are a lot of features in this tutorial.</span></span> <span data-ttu-id="d984f-117">Utworzymy je jeden po drugim.</span><span class="sxs-lookup"><span data-stu-id="d984f-117">Let’s build them one by one.</span></span> 
## <a name="prerequisites"></a><span data-ttu-id="d984f-118">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="d984f-118">Prerequisites</span></span>
<span data-ttu-id="d984f-119">Należy skonfigurować komputer, aby uruchomić oprogramowanie .NET core.</span><span class="sxs-lookup"><span data-stu-id="d984f-119">You’ll need to setup your machine to run .NET core.</span></span> <span data-ttu-id="d984f-120">Instrukcje instalacji można znaleźć na [.NET Core](https://www.microsoft.com/net/core) strony.</span><span class="sxs-lookup"><span data-stu-id="d984f-120">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span> <span data-ttu-id="d984f-121">Można uruchomić tej aplikacji, w systemie Windows, Linux, macOS lub w kontenerze Docker.</span><span class="sxs-lookup"><span data-stu-id="d984f-121">You can run this application on Windows, Linux, macOS or in a Docker container.</span></span> <span data-ttu-id="d984f-122">Należy zainstalować w edytorze kodu dotyczącego elementów ulubionych.</span><span class="sxs-lookup"><span data-stu-id="d984f-122">You’ll need to install your favorite code editor.</span></span> 
## <a name="create-the-application"></a><span data-ttu-id="d984f-123">Tworzenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="d984f-123">Create the Application</span></span>
<span data-ttu-id="d984f-124">Pierwszym krokiem jest utworzenie nowej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d984f-124">The first step is to create a new application.</span></span> <span data-ttu-id="d984f-125">Otwórz wiersz polecenia i Utwórz nowy katalog aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d984f-125">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="d984f-126">Upewnij się, że sposób bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="d984f-126">Make that the current directory.</span></span> <span data-ttu-id="d984f-127">Wpisz polecenie `dotnet new console` w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="d984f-127">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="d984f-128">Spowoduje to utworzenie plików starter podstawowe aplikacji "Hello World".</span><span class="sxs-lookup"><span data-stu-id="d984f-128">This creates the starter files for a basic "Hello World" application.</span></span>

<span data-ttu-id="d984f-129">Przed wprowadzeniem modyfikacji przejdźmy do czynności, aby uruchomić prostej aplikacji Hello World.</span><span class="sxs-lookup"><span data-stu-id="d984f-129">Before you start making modifications, let’s go through the steps to run the simple Hello World application.</span></span> <span data-ttu-id="d984f-130">Po utworzeniu aplikacji, wpisz `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="d984f-130">After creating the application, type `dotnet restore` ([see note](#dotnet-restore-note)) at the command prompt.</span></span> <span data-ttu-id="d984f-131">To polecenie uruchamia proces przywracania pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="d984f-131">This command runs the NuGet package restore process.</span></span> <span data-ttu-id="d984f-132">NuGet jest Menedżera pakietów platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="d984f-132">NuGet is a .NET package manager.</span></span> <span data-ttu-id="d984f-133">To polecenie pobiera wszelkie brakujące zależności projektu.</span><span class="sxs-lookup"><span data-stu-id="d984f-133">This command downloads any of the missing dependencies for your project.</span></span> <span data-ttu-id="d984f-134">Jak jest to nowy projekt, Brak zależności są na miejscu, więc przy pierwszym uruchomieniu pobierze framework .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d984f-134">As this is a new project, none of the dependencies are in place, so the first run will download the .NET Core framework.</span></span> <span data-ttu-id="d984f-135">Po wykonaniu tego kroku początkowego, wystarczy uruchomić `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) podczas dodawania nowych pakietów zależnych lub zaktualizować wersje zależności.</span><span class="sxs-lookup"><span data-stu-id="d984f-135">After this initial step, you will only need to run `dotnet restore` ([see note](#dotnet-restore-note)) when you add new dependent packages, or update the versions of any of your dependencies.</span></span> <span data-ttu-id="d984f-136">Ten proces tworzy plik blokady projektu (plikiem project.lock.json) w katalogu projektu.</span><span class="sxs-lookup"><span data-stu-id="d984f-136">This process also creates the project lock file (project.lock.json) in your project directory.</span></span> <span data-ttu-id="d984f-137">Ten plik ułatwia zarządzanie zależności projektu.</span><span class="sxs-lookup"><span data-stu-id="d984f-137">This file helps to manage the project dependencies.</span></span> <span data-ttu-id="d984f-138">Zawiera ona lokalnej lokalizacji wszystkie zależności projektu.</span><span class="sxs-lookup"><span data-stu-id="d984f-138">It contains the local location of all the project dependencies.</span></span> <span data-ttu-id="d984f-139">Nie trzeba umieścić plik w kontroli źródła; zostanie wygenerowany, po uruchomieniu `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)).</span><span class="sxs-lookup"><span data-stu-id="d984f-139">You do not need to put the file in source control; it will be generated when you run `dotnet restore` ([see note](#dotnet-restore-note)).</span></span> 

<span data-ttu-id="d984f-140">Po przywróceniu pakietów, możesz uruchomić `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="d984f-140">After restoring packages, you run `dotnet build`.</span></span> <span data-ttu-id="d984f-141">Wykonuje aparat kompilacji i tworzy aplikację pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="d984f-141">This executes the build engine and creates your application executable.</span></span> <span data-ttu-id="d984f-142">Na koniec wykonaj `dotnet run` do uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d984f-142">Finally, you execute `dotnet run` to run your application.</span></span>  

<span data-ttu-id="d984f-143">Jest prosty kod aplikacji Hello World w pliku Program.cs.</span><span class="sxs-lookup"><span data-stu-id="d984f-143">The simple Hello World application code is all in Program.cs.</span></span> <span data-ttu-id="d984f-144">Otwórz ten plik z w ulubionym edytorze tekstów.</span><span class="sxs-lookup"><span data-stu-id="d984f-144">Open that file with your favorite text editor.</span></span> <span data-ttu-id="d984f-145">Jesteśmy wprowadzi naszym pierwszym zmiany.</span><span class="sxs-lookup"><span data-stu-id="d984f-145">We’re about to make our first changes.</span></span>
<span data-ttu-id="d984f-146">W górnej części pliku, zobacz using instrukcji:</span><span class="sxs-lookup"><span data-stu-id="d984f-146">At the top of the file, see a using statement:</span></span>

```csharp
using System;
```

<span data-ttu-id="d984f-147">Ta instrukcja informuje kompilator, że dowolne typy z `System` znajdują się w zakresie przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d984f-147">This statement tells the compiler that any types from the `System` namespace are in scope.</span></span> <span data-ttu-id="d984f-148">Jak który użyto innych języków obiektowo C# używa przestrzeni nazw do organizowania typów.</span><span class="sxs-lookup"><span data-stu-id="d984f-148">Like other Object Oriented languages you may have used, C# uses namespaces to organize types.</span></span> <span data-ttu-id="d984f-149">Nie różni się hello world program.</span><span class="sxs-lookup"><span data-stu-id="d984f-149">This hello world program is no different.</span></span> <span data-ttu-id="d984f-150">Widać, że program jest ujęta w `ConsoleApplication` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d984f-150">You can see that the program is enclosed in the `ConsoleApplication` namespace.</span></span> <span data-ttu-id="d984f-151">Nie jest bardzo opisową nazwę, tak aby zmienić `TeleprompterConsole`:</span><span class="sxs-lookup"><span data-stu-id="d984f-151">That’s not a very descriptive name, so change it to `TeleprompterConsole`:</span></span>

```csharp
namespace TeleprompterConsole
```

## <a name="reading-and-echoing-the-file"></a><span data-ttu-id="d984f-152">Odczytywanie i wyświetlania pliku</span><span class="sxs-lookup"><span data-stu-id="d984f-152">Reading and Echoing the File</span></span>
<span data-ttu-id="d984f-153">Pierwszy funkcję tak, aby dodać jest możliwość odczytywanie pliku tekstowego i Wyświetl ten tekst do konsoli.</span><span class="sxs-lookup"><span data-stu-id="d984f-153">The first feature to add is the ability to read a text file and display all that text to the console.</span></span> <span data-ttu-id="d984f-154">Po pierwsze możemy dodać plik tekstowy.</span><span class="sxs-lookup"><span data-stu-id="d984f-154">First, let’s add a text file.</span></span> <span data-ttu-id="d984f-155">Kopiuj [sampleQuotes.txt](https://github.com/dotnet/samples/raw/master/csharp/getting-started/console-teleprompter/sampleQuotes.txt) plik z repozytorium GitHub dla tego [próbki](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-teleprompter) w katalogu projektu.</span><span class="sxs-lookup"><span data-stu-id="d984f-155">Copy the [sampleQuotes.txt](https://github.com/dotnet/samples/raw/master/csharp/getting-started/console-teleprompter/sampleQuotes.txt) file from the GitHub repository for this [sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-teleprompter) into your project directory.</span></span> <span data-ttu-id="d984f-156">To będzie służyć jako skryptów dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d984f-156">This will serve as the script for your application.</span></span> <span data-ttu-id="d984f-157">Jeśli chcesz uzyskać informacje na temat Pobierz przykładową aplikację na ten temat, zapoznaj się z instrukcjami w [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples) tematu.</span><span class="sxs-lookup"><span data-stu-id="d984f-157">If you would like information on how to download the sample app for this topic, see the instructions in the [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples) topic.</span></span>

<span data-ttu-id="d984f-158">Następnie dodaj następującą metodę w klasie programu (bezpośrednio pod `Main` metody):</span><span class="sxs-lookup"><span data-stu-id="d984f-158">Next, add the following method in your Program class (right below the `Main` method):</span></span>

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

<span data-ttu-id="d984f-159">Ta metoda używa typów z dwóch nowych przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d984f-159">This method uses types from two new namespaces.</span></span> <span data-ttu-id="d984f-160">W tym celu należy skompilować należy dodać następujące dwa wiersze na początku pliku:</span><span class="sxs-lookup"><span data-stu-id="d984f-160">For this to compile you’ll need to add the following two lines to the top of the file:</span></span>

```csharp
using System.Collections.Generic;
using System.IO;
```

<span data-ttu-id="d984f-161">`IEnumerable<T>` Interfejsu jest zdefiniowany w `System.Collections.Generic` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d984f-161">The `IEnumerable<T>` interface is defined in the `System.Collections.Generic` namespace.</span></span> <span data-ttu-id="d984f-162"><xref:System.IO.File> Klasa jest zdefiniowana w `System.IO` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d984f-162">The <xref:System.IO.File> class is defined in the `System.IO` namespace.</span></span>

<span data-ttu-id="d984f-163">Ta metoda jest specjalnym rodzajem metody C# o nazwie *— metoda wyliczania*.</span><span class="sxs-lookup"><span data-stu-id="d984f-163">This method is a special type of C# method called an *Enumerator method*.</span></span> <span data-ttu-id="d984f-164">Moduł wyliczający metody zwracają sekwencji, które są oceniane w trybie opóźnienia.</span><span class="sxs-lookup"><span data-stu-id="d984f-164">Enumerator methods return sequences that are evaluated lazily.</span></span> <span data-ttu-id="d984f-165">Oznacza to, że każdej pozycji w sekwencji jest generowany, zgodnie z wymaganiami kodu wykorzystywanie sekwencji.</span><span class="sxs-lookup"><span data-stu-id="d984f-165">That means each item in the sequence is generated as it is requested by the code consuming the sequence.</span></span> <span data-ttu-id="d984f-166">Moduł wyliczający metody to metody, które zawierają jedną lub więcej `yield return` instrukcje.</span><span class="sxs-lookup"><span data-stu-id="d984f-166">Enumerator methods are methods that contain one or more `yield return` statements.</span></span> <span data-ttu-id="d984f-167">Obiekt zwrócony przez `ReadFrom` metoda zawiera kod, aby wygenerować każdej pozycji w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="d984f-167">The object returned by the `ReadFrom` method contains the code to generate each item in the sequence.</span></span> <span data-ttu-id="d984f-168">W tym przykładzie, który obejmuje odczytu następnego wiersza tekstu z pliku źródłowego i zwraca ten ciąg.</span><span class="sxs-lookup"><span data-stu-id="d984f-168">In this example, that involves reading the next line of text from the source file, and returning that string.</span></span> <span data-ttu-id="d984f-169">Za każdym żądaniem kod wywołujący następnego elementu z sekwencji kod odczytuje następnego wiersza tekstu z pliku i zwraca go.</span><span class="sxs-lookup"><span data-stu-id="d984f-169">Each time the calling code requests the next item from the sequence, the code reads the next line of text from the file and returns it.</span></span> <span data-ttu-id="d984f-170">Gdy całkowicie odczytać pliku sekwencja wskazuje, że nie ma więcej elementów.</span><span class="sxs-lookup"><span data-stu-id="d984f-170">When the file has been completely read, the sequence indicates that there are no more items.</span></span>

<span data-ttu-id="d984f-171">Istnieją dwa inne C# składni elementy, które mogą być nowe dla Ciebie.</span><span class="sxs-lookup"><span data-stu-id="d984f-171">There are two other C# syntax elements that may be new to you.</span></span> <span data-ttu-id="d984f-172">`using` Instrukcji w tej metodzie zarządza oczyszczania zasobu.</span><span class="sxs-lookup"><span data-stu-id="d984f-172">The `using` statement in this method manages resource cleanup.</span></span> <span data-ttu-id="d984f-173">Zmienna, która została zainicjowana w `using` instrukcji (`reader`, w tym przykładzie) musi implementować `IDisposable` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="d984f-173">The variable that is initialized in the `using` statement (`reader`, in this example) must implement the `IDisposable` interface.</span></span> <span data-ttu-id="d984f-174"><xref:System.IDisposable> Interfejs definiuje jedną metodę `Dispose`, która powinna być wywoływana, gdy zasobu powinny zostać zwolnione.</span><span class="sxs-lookup"><span data-stu-id="d984f-174">The <xref:System.IDisposable> interface defines a single method, `Dispose`, that should be called when the resource should be released.</span></span> <span data-ttu-id="d984f-175">Kompilator generuje tego wywołania, gdy wykonanie osiągnie zamykającym `using` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="d984f-175">The compiler generates that call when execution reaches the closing brace of the `using` statement.</span></span> <span data-ttu-id="d984f-176">Kod wygenerowany przez kompilator zapewnia zwolnienie zasobu, nawet w przypadku zgłoszenia wyjątku z kodu w bloku zdefiniowany przy użyciu instrukcji.</span><span class="sxs-lookup"><span data-stu-id="d984f-176">The compiler-generated code ensures that the resource is released even if an exception is thrown from the code in the block defined by the using statement.</span></span>

<span data-ttu-id="d984f-177">`reader` Zmiennej jest definiowana za pomocą `var` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="d984f-177">The `reader` variable is defined using the `var` keyword.</span></span> <span data-ttu-id="d984f-178">`var` definiuje *niejawnie wpisane zmiennej lokalnej*.</span><span class="sxs-lookup"><span data-stu-id="d984f-178">`var` defines an *implicitly typed local variable*.</span></span> <span data-ttu-id="d984f-179">Oznacza to, że typ zmiennej jest określana przez typ czas kompilacji obiektu przypisaną do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="d984f-179">That means the type of the variable is determined by the compile time type of the object assigned to the variable.</span></span> <span data-ttu-id="d984f-180">Tutaj, która jest wartością zwracaną przez <xref:System.IO.File.OpenText(System.String)> metodę, która jest <xref:System.IO.StreamReader> obiektu.</span><span class="sxs-lookup"><span data-stu-id="d984f-180">Here, that is the return value from the <xref:System.IO.File.OpenText(System.String)> method, which is a <xref:System.IO.StreamReader> object.</span></span>
 
<span data-ttu-id="d984f-181">Teraz załóżmy wprowadź kod, aby odczytać plik w `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="d984f-181">Now, let’s fill in the code to read the file in the `Main` method:</span></span> 

```csharp
var lines = ReadFrom("sampleQuotes.txt");
foreach (var line in lines)
{
    Console.WriteLine(line); 
}
```

<span data-ttu-id="d984f-182">Uruchom program (przy użyciu `dotnet run` może uzyskać dostęp każdy wiersz wydrukowane do konsoli i).</span><span class="sxs-lookup"><span data-stu-id="d984f-182">Run the program (using `dotnet run` and you can see every line printed out to the console).</span></span>  

## <a name="adding-delays-and-formatting-output"></a><span data-ttu-id="d984f-183">Dodawanie opóźnień i formatowanie danych wyjściowych</span><span class="sxs-lookup"><span data-stu-id="d984f-183">Adding Delays and Formatting output</span></span>
<span data-ttu-id="d984f-184">Możesz mieć jest wyświetlany zbyt szybko, aby odczytywać.</span><span class="sxs-lookup"><span data-stu-id="d984f-184">What you have is being displayed far too fast to read aloud.</span></span> <span data-ttu-id="d984f-185">Teraz musisz dodać opóźnienia w danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="d984f-185">Now you need to add the delays in the output.</span></span> <span data-ttu-id="d984f-186">Po rozpoczęciu, użytkownik będzie zbudować części kodu core, który umożliwia przetwarzanie asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="d984f-186">As you start, you’ll be building some of the core code that enables asynchronous processing.</span></span> <span data-ttu-id="d984f-187">Jednak te pierwsze kroki są zgodne z kilku wzorców układ.</span><span class="sxs-lookup"><span data-stu-id="d984f-187">However, these first steps will follow a few anti-patterns.</span></span> <span data-ttu-id="d984f-188">Układ wzorce są wskazać w komentarzach Dodaj kod, a kod zostanie zaktualizowany w kolejnych krokach.</span><span class="sxs-lookup"><span data-stu-id="d984f-188">The anti-patterns are pointed out in comments as you add the code, and the code will be updated in later steps.</span></span>

<span data-ttu-id="d984f-189">Istnieją dwa kroki, aby w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="d984f-189">There are two steps to this section.</span></span> <span data-ttu-id="d984f-190">Najpierw będzie aktualizowana metodę iteratora Aby przywrócić pojedyncze słowa zamiast całego wierszy.</span><span class="sxs-lookup"><span data-stu-id="d984f-190">First, you’ll update the iterator method to return single words instead of entire lines.</span></span> <span data-ttu-id="d984f-191">Który wykonuje się za pomocą tych zmian.</span><span class="sxs-lookup"><span data-stu-id="d984f-191">That’s done with these modifications.</span></span> <span data-ttu-id="d984f-192">Zastąp `yield return line;` instrukcji z następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="d984f-192">Replace the `yield return line;` statement with the following code:</span></span>

```csharp
var words = line.Split(' ');
foreach (var word in words)
{
    yield return word + " ";
}
yield return Environment.NewLine;
```

<span data-ttu-id="d984f-193">Następnie należy zmodyfikować sposób korzystać wiersze pliku i Dodaj opóźnienia po zapisaniu każdego wyrazu.</span><span class="sxs-lookup"><span data-stu-id="d984f-193">Next, you need to modify how you consume the lines of the file, and add a delay after writing each word.</span></span> <span data-ttu-id="d984f-194">Zastąp `Console.WriteLine(line)` instrukcji w `Main` metodę z następującym fragmencie:</span><span class="sxs-lookup"><span data-stu-id="d984f-194">Replace the `Console.WriteLine(line)` statement in the `Main` method with the following block:</span></span>

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

<span data-ttu-id="d984f-195">`Task` Klasa znajduje się w `System.Threading.Tasks` przestrzeni nazw, dlatego należy dodać go `using` instrukcji w górnej części pliku:</span><span class="sxs-lookup"><span data-stu-id="d984f-195">The `Task` class is in the `System.Threading.Tasks` namespace, so you need to add that `using` statement at the top of file:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="d984f-196">Uruchamianie przykładowej i sprawdź dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="d984f-196">Run the sample, and check the output.</span></span> <span data-ttu-id="d984f-197">Teraz każdego pojedynczego wyrazu drukowania, a następnie z opóźnieniem 200 ms.</span><span class="sxs-lookup"><span data-stu-id="d984f-197">Now, each single word is printed, followed by a 200 ms delay.</span></span> <span data-ttu-id="d984f-198">Jednak wyświetlanych wyników zawiera niektóre problemy, ponieważ plik źródłowy, tekst ma kilka wierszy, które mają więcej niż 80 znaków bez podziału wiersza.</span><span class="sxs-lookup"><span data-stu-id="d984f-198">However, the displayed output shows some issues because the source text file has several lines that have more than 80 characters without a line break.</span></span> <span data-ttu-id="d984f-199">Może to być trudny do odczytania, gdy jest on przewijanie przez.</span><span class="sxs-lookup"><span data-stu-id="d984f-199">That can be hard to read while it's scrolling by.</span></span> <span data-ttu-id="d984f-200">To łatwe rozwiązać problem.</span><span class="sxs-lookup"><span data-stu-id="d984f-200">That’s easy to fix.</span></span> <span data-ttu-id="d984f-201">Będzie tylko informacje o długości każdego wiersza i generować nowy wiersz w każdym przypadku, gdy długość wiersza osiągnie określony próg.</span><span class="sxs-lookup"><span data-stu-id="d984f-201">You’ll just keep track of the length of each line, and generate a new line whenever the line length reaches a certain threshold.</span></span> <span data-ttu-id="d984f-202">Deklarowanie zmiennej lokalnej po deklaracji `words` przechowuje długość wiersza:</span><span class="sxs-lookup"><span data-stu-id="d984f-202">Declare a local variable after the declaration of `words` that holds the line length:</span></span>

```csharp
var lineLength = 0;
```
 
<span data-ttu-id="d984f-203">Następnie dodaj następujący kod po `yield return word + " ";` instrukcji (przed nawiasem zamykającym):</span><span class="sxs-lookup"><span data-stu-id="d984f-203">Then, add the following code after the `yield return word + " ";` statement (before the closing brace):</span></span>

```csharp
lineLength += word.Length + 1;
if (lineLength > 70)
{
    yield return Environment.NewLine;
    lineLength = 0;
}
```
 
<span data-ttu-id="d984f-204">Uruchom próbkę i będzie mogła odczytywać na jego wstępnie skonfigurowane tempie.</span><span class="sxs-lookup"><span data-stu-id="d984f-204">Run the sample, and you’ll be able to read aloud at its pre-configured pace.</span></span>

## <a name="async-tasks"></a><span data-ttu-id="d984f-205">Zadań asynchronicznych</span><span class="sxs-lookup"><span data-stu-id="d984f-205">Async Tasks</span></span>
<span data-ttu-id="d984f-206">W tym ostatnim kroku dodasz kod, aby zapisać dane wyjściowe asynchronicznie w jedno zadanie podczas również uruchamiania innego zadania, które można odczytać wejściowych od użytkownika, jeśli chcą, aby przyspieszyć lub spowolnić wyświetlania tekstu.</span><span class="sxs-lookup"><span data-stu-id="d984f-206">In this final step, you’ll add the code to write the output asynchronously in one task, while also running another task to read input from the user if they want to speed up or slow down the text display.</span></span> <span data-ttu-id="d984f-207">Ma kilka kroków oraz do końca, będziesz mieć wszystkie aktualizacje, które są potrzebne.</span><span class="sxs-lookup"><span data-stu-id="d984f-207">This has a few steps in it and by the end, you’ll have all the updates that you need.</span></span>
<span data-ttu-id="d984f-208">Pierwszym krokiem jest utworzenie asynchronicznego <xref:System.Threading.Tasks.Task> zwracanie metodę, która reprezentuje kod po utworzeniu wykonanej do tej pory do odczytywania i wyświetlić plik.</span><span class="sxs-lookup"><span data-stu-id="d984f-208">The first step is to create an asynchronous <xref:System.Threading.Tasks.Task> returning method that represents the code you’ve created so far to read and display the file.</span></span>

<span data-ttu-id="d984f-209">Dodaj tę metodę, aby Twoje `Program` klasy (jest ona pobierana z treści Twojej `Main` — metoda):</span><span class="sxs-lookup"><span data-stu-id="d984f-209">Add this method to your `Program` class (it’s taken from the body of your `Main` method):</span></span>

```csharp
private static async Task ShowTeleprompter()
{
    var words = ReadFrom("sampleQuotes.txt");
    foreach (var line in words)
    {
        Console.Write(line);
        if (!string.IsNullOrWhiteSpace(line))
        {
            await Task.Delay(200);
        }
    }
}
```

<span data-ttu-id="d984f-210">Można zauważyć dwie zmiany.</span><span class="sxs-lookup"><span data-stu-id="d984f-210">You’ll notice two changes.</span></span> <span data-ttu-id="d984f-211">Pierwszy w treści metody, zamiast wywoływać metodę <xref:System.Threading.Tasks.Task.Wait> synchronicznie oczekiwania na zakończenie zadania, korzysta z tej wersji `await` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="d984f-211">First, in the body of the method, instead of calling <xref:System.Threading.Tasks.Task.Wait> to synchronously wait for a task to finish, this version uses the `await` keyword.</span></span> <span data-ttu-id="d984f-212">Aby to zrobić, należy dodać `async` modyfikator w podpisie metody.</span><span class="sxs-lookup"><span data-stu-id="d984f-212">In order to do that, you need to add the `async` modifier to the method signature.</span></span> <span data-ttu-id="d984f-213">Ta metoda zwraca `Task`.</span><span class="sxs-lookup"><span data-stu-id="d984f-213">This method returns a `Task`.</span></span> <span data-ttu-id="d984f-214">Zwróć uwagę, że nie ma żadnych instrukcji return, które zwracają `Task` obiektu.</span><span class="sxs-lookup"><span data-stu-id="d984f-214">Notice that there are no return statements that return a `Task` object.</span></span> <span data-ttu-id="d984f-215">Zamiast tego, który `Task` obiekt jest tworzony przez kompilator generuje, korzystając z kodu `await` operatora.</span><span class="sxs-lookup"><span data-stu-id="d984f-215">Instead, that `Task` object is created by code the compiler generates when you use the `await` operator.</span></span> <span data-ttu-id="d984f-216">Wyobraź sobie ta metoda zwraca po osiągnięciu `await`.</span><span class="sxs-lookup"><span data-stu-id="d984f-216">You can imagine that this method returns when it reaches an `await`.</span></span> <span data-ttu-id="d984f-217">Zwrócona `Task` wskazuje, że nie zakończył pracy.</span><span class="sxs-lookup"><span data-stu-id="d984f-217">The returned `Task` indicates that the work has not completed.</span></span>
<span data-ttu-id="d984f-218">Metoda wznawia działanie po ukończeniu zadania oczekiwano.</span><span class="sxs-lookup"><span data-stu-id="d984f-218">The method resumes when the awaited task completes.</span></span> <span data-ttu-id="d984f-219">Gdy jest wykonywana do ukończenia zwróconego `Task` wskazuje, że została zakończona.</span><span class="sxs-lookup"><span data-stu-id="d984f-219">When it has executed to completion, the returned `Task` indicates that it is complete.</span></span>
<span data-ttu-id="d984f-220">Wywoływanie kodu można monitorować zwróconą `Task` ustalenie, kiedy została ukończona.</span><span class="sxs-lookup"><span data-stu-id="d984f-220">Calling code can monitor that returned `Task` to determine when it has completed.</span></span>

<span data-ttu-id="d984f-221">Ta nowa metoda można wywołać w Twojej `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="d984f-221">You can call this new method in your `Main` method:</span></span>

```csharp
ShowTeleprompter().Wait();
```

<span data-ttu-id="d984f-222">W tym miejscu, w `Main`, kod synchronicznie oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="d984f-222">Here, in `Main`, the code does synchronously wait.</span></span> <span data-ttu-id="d984f-223">Należy używać `await` operator zamiast oczekiwać synchronicznie, jeśli to możliwe.</span><span class="sxs-lookup"><span data-stu-id="d984f-223">You should use the `await` operator instead of synchronously waiting whenever possible.</span></span> <span data-ttu-id="d984f-224">Jednak w aplikacji konsoli `Main` metody, nie można użyć `await` operatora.</span><span class="sxs-lookup"><span data-stu-id="d984f-224">But, in a console application’s `Main` method, you cannot use the `await` operator.</span></span> <span data-ttu-id="d984f-225">Które mogłyby spowodować aplikacji został zakończony zanim wszystkie zadania zostały ukończone.</span><span class="sxs-lookup"><span data-stu-id="d984f-225">That would result in the application exiting before all tasks have completed.</span></span>

<span data-ttu-id="d984f-226">Następnie należy napisać drugi metody asynchronicznej do odczytu z konsoli i obserwować "<" i ">" kluczy.</span><span class="sxs-lookup"><span data-stu-id="d984f-226">Next, you need to write the second asynchronous method to read from the Console and watch for the ‘<’ and ‘>’ keys.</span></span> <span data-ttu-id="d984f-227">Oto metoda dodane do tego zadania:</span><span class="sxs-lookup"><span data-stu-id="d984f-227">Here’s the method you add for that task:</span></span>

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
        } while (true);
    };
    await Task.Run(work);
}
```

<span data-ttu-id="d984f-228">Spowoduje to utworzenie wyrażenia lambda do reprezentowania <xref:System.Action> delegata, który będzie odczytywać klucza z konsoli i modyfikuje zmienną lokalną reprezentujący opóźnienie, gdy użytkownik naciśnie ' <' lub ' >' kluczy.</span><span class="sxs-lookup"><span data-stu-id="d984f-228">This creates a lambda expression to represent an <xref:System.Action> delegate that reads a key from the Console and modifies a local variable representing the delay when the user presses the ‘<’ or ‘>’ keys.</span></span> <span data-ttu-id="d984f-229">Ta metoda używa <xref:System.Console.ReadKey> zablokować i poczekaj, aż użytkownik o naciśnięcie klawisza.</span><span class="sxs-lookup"><span data-stu-id="d984f-229">This method uses <xref:System.Console.ReadKey> to block and wait for the user to press a key.</span></span>

<span data-ttu-id="d984f-230">Aby zakończyć tę funkcję, musisz utworzyć nowy `async Task` zwracanie metody, która rozpoczyna się oba te zadania (`GetInput` i `ShowTeleprompter`) i zarządza także udostępnionych danych między tymi dwoma zadaniami.</span><span class="sxs-lookup"><span data-stu-id="d984f-230">To finish this feature, you need to create a new `async Task` returning method that starts both of these tasks (`GetInput` and `ShowTeleprompter`), and also manages the shared data between these two tasks.</span></span>
 
<span data-ttu-id="d984f-231">Nadszedł czas, aby utworzyć klasę, która może obsłużyć udostępnionych danych między tymi dwoma zadaniami.</span><span class="sxs-lookup"><span data-stu-id="d984f-231">It’s time to create a class that can handle the shared data between these two tasks.</span></span> <span data-ttu-id="d984f-232">Ta klasa zawiera dwie właściwości publicznej: opóźnienie i Flaga wskazująca, całkowicie odczytać pliku:</span><span class="sxs-lookup"><span data-stu-id="d984f-232">This class contains two public properties: the delay, and a flag to indicate that the file has been completely read:</span></span>

```csharp
namespace TeleprompterConsole
{
    internal class TelePrompterConfig
    {
        private object lockHandle = new object();
        public int DelayInMilliseconds { get; private set; } = 200;

        public void UpdateDelay(int increment) // negative to speed up
        {
            var newDelay = Min(DelayInMilliseconds + increment, 1000);
            newDelay = Max(newDelay, 20);
            lock (lockHandle)
            {
                DelayInMilliseconds = newDelay;
            }
        }
    }
}
```

<span data-ttu-id="d984f-233">Umieść tej klasy w pliku i ująć tej klasy w `TeleprompterConsole` przestrzeni nazw, jak pokazano powyżej.</span><span class="sxs-lookup"><span data-stu-id="d984f-233">Put that class in a new file, and enclose that class in the `TeleprompterConsole` namespace as shown above.</span></span> <span data-ttu-id="d984f-234">Należy również dodać `using static` instrukcji, dzięki czemu można odwoływać się `Min` i `Max` metody bez otaczającej nazwy klasy lub obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="d984f-234">You’ll also need to add a `using static` statement so that you can reference the `Min` and `Max` method without the enclosing class or namespace names.</span></span> <span data-ttu-id="d984f-235">A `using static` instrukcji imports metody z jedną klasę.</span><span class="sxs-lookup"><span data-stu-id="d984f-235">A `using static` statement imports the methods from one class.</span></span> <span data-ttu-id="d984f-236">Jest to contrast z `using` instrukcji używany do tego punktu, które zostały zaimportowane wszystkie klasy z przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d984f-236">This is in contrast with the `using` statements used up to this point that have imported all classes from a namespace.</span></span>

```csharp
using static System.Math;
```

<span data-ttu-id="d984f-237">Jest inna funkcja języka, który jest nowy `lock` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="d984f-237">The other language feature that’s new is the `lock` statement.</span></span> <span data-ttu-id="d984f-238">Ta instrukcja zapewnia tylko jednego wątku można w tym kod w danym momencie.</span><span class="sxs-lookup"><span data-stu-id="d984f-238">This statement ensures that only a single thread can be in that code at any given time.</span></span> <span data-ttu-id="d984f-239">Jeśli jeden wątek znajduje się w sekcji zablokowane, inne wątki należy poczekać na zakończenie tej sekcji pierwszy wątku.</span><span class="sxs-lookup"><span data-stu-id="d984f-239">If one thread is in the locked section, other threads must wait for the first thread to exit that section.</span></span> <span data-ttu-id="d984f-240">`lock` Instrukcja używa obiektu, który chroni sekcji blokady.</span><span class="sxs-lookup"><span data-stu-id="d984f-240">The `lock` statement uses an object that guards the lock section.</span></span> <span data-ttu-id="d984f-241">Ta klasa jest zgodna standardowe idiom można zablokować obiektu prywatny w klasie.</span><span class="sxs-lookup"><span data-stu-id="d984f-241">This class follows a standard idiom to lock a private object in the class.</span></span>

<span data-ttu-id="d984f-242">Następnie należy zaktualizować `ShowTeleprompter` i `GetInput` metod do używania nowych `config` obiektu.</span><span class="sxs-lookup"><span data-stu-id="d984f-242">Next, you need to update the `ShowTeleprompter` and `GetInput` methods to use the new `config` object.</span></span> <span data-ttu-id="d984f-243">Zapis final jeden `Task` zwracanie `async` metody w celu uruchamiania obu zadań i zamknąć po zakończeniu pierwszego zadania:</span><span class="sxs-lookup"><span data-stu-id="d984f-243">Write one final `Task` returning `async` method to start both tasks and exit when the first task finishes:</span></span>

```csharp
private static async Task RunTeleprompter()
{
    var config = new TelePrompterConfig();
    var displayTask = ShowTeleprompter(config);

    var speedTask = GetInput(config);
    await Task.WhenAny(displayTask, speedTask);
}
```

<span data-ttu-id="d984f-244">Jeden nowej metody w tym miejscu jest <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])> wywołania.</span><span class="sxs-lookup"><span data-stu-id="d984f-244">The one new method here is the <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])> call.</span></span> <span data-ttu-id="d984f-245">Który tworzy `Task` który zakończy się natychmiast po ukończeniu zadań z listy argumentów.</span><span class="sxs-lookup"><span data-stu-id="d984f-245">That creates a `Task` that finishes as soon as any of the tasks in its argument list completes.</span></span>

<span data-ttu-id="d984f-246">Następnie należy zaktualizować zarówno `ShowTeleprompter` i `GetInput` metod do zastosowania `config` obiektu opóźnienia:</span><span class="sxs-lookup"><span data-stu-id="d984f-246">Next, you need to update both the `ShowTeleprompter` and `GetInput` methods to use the `config` object for the delay:</span></span>

```csharp
private static async Task ShowTeleprompter(TelePrompterConfig config)
{
    var words = ReadFrom("sampleQuotes.txt");
    foreach (var line in words)
    {
        Console.Write(line);
        if (!string.IsNullOrWhiteSpace(line))
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
        } while (!config.Done);
    };
    await Task.Run(work);
}
```

<span data-ttu-id="d984f-247">Tej nowej wersji `ShowTeleprompter` odwołuje się nowa metoda `TeleprompterConfig` klasy.</span><span class="sxs-lookup"><span data-stu-id="d984f-247">This new version of `ShowTeleprompter` calls a new method in the `TeleprompterConfig` class.</span></span> <span data-ttu-id="d984f-248">Teraz, musisz zaktualizować `Main` do wywołania `RunTeleprompter` zamiast `ShowTeleprompter`:</span><span class="sxs-lookup"><span data-stu-id="d984f-248">Now, you need to update `Main` to call `RunTeleprompter` instead of `ShowTeleprompter`:</span></span>

```csharp
RunTeleprompter().Wait();
```

<span data-ttu-id="d984f-249">Aby zakończyć, musisz dodać `SetDone` metody i `Done` właściwości `TelePrompterConfig` klasy:</span><span class="sxs-lookup"><span data-stu-id="d984f-249">To finish, you'll need to add the `SetDone` method, and the `Done` property to the `TelePrompterConfig` class:</span></span>

```csharp
public bool Done => done;

private bool done;

public void SetDone()
{
    done = true;    
}
```

## <a name="conclusion"></a><span data-ttu-id="d984f-250">Wniosek</span><span class="sxs-lookup"><span data-stu-id="d984f-250">Conclusion</span></span>
<span data-ttu-id="d984f-251">W tym samouczku przedstawiono możesz szereg funkcji języka C# i bibliotek .NET Core powiązane z pracy w aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="d984f-251">This tutorial showed you a number of the features around the C# language and the .NET Core libraries related to working in Console applications.</span></span>
<span data-ttu-id="d984f-252">Można tworzyć na ta wiedza, aby zapoznać się więcej o języku i klasy wprowadzone w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="d984f-252">You can build on this knowledge to explore more about the language, and the classes introduced here.</span></span> <span data-ttu-id="d984f-253">Użyj blokujące i nieblokujące zadania opartego na Asynchronous programming modelu, samouczek języka C# i organizowania programów C# i interfejsu wiersza polecenia programu .NET Core i narzędzi, przedstawiono podstawowe informacje o pliku i we/wy konsoli.</span><span class="sxs-lookup"><span data-stu-id="d984f-253">You’ve seen the basics of File and Console I/O, blocking and non-blocking use of the Task based Asynchronous programming model, a tour of the C# language and how C# programs are organized and the .NET Core Command Line Interface and tools.</span></span>
 
<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
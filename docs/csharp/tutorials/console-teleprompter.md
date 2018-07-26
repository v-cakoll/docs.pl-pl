---
title: Aplikacja konsoli
description: W tym samouczku pokazano pewną liczbę funkcji platformy .NET Core i języka C#.
ms.date: 03/06/2017
ms.assetid: 883cd93d-50ce-4144-b7c9-2df28d9c11a0
ms.openlocfilehash: bae03c9ae02f2888b1b70617ca712ef7927e9dce
ms.sourcegitcommit: 60645077dc4b62178403145f8ef691b13ffec28e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2018
ms.locfileid: "37961420"
---
# <a name="console-application"></a><span data-ttu-id="1a15f-103">Aplikacja konsoli</span><span class="sxs-lookup"><span data-stu-id="1a15f-103">Console Application</span></span>

<span data-ttu-id="1a15f-104">W tym samouczku pokazano pewną liczbę funkcji platformy .NET Core i języka C#.</span><span class="sxs-lookup"><span data-stu-id="1a15f-104">This tutorial teaches you a number of features in .NET Core and the C# language.</span></span> <span data-ttu-id="1a15f-105">Dowiesz się:</span><span class="sxs-lookup"><span data-stu-id="1a15f-105">You’ll learn:</span></span>

- <span data-ttu-id="1a15f-106">Podstawowe narzędzia .NET Core interfejsu wiersza polecenia (CLI)</span><span class="sxs-lookup"><span data-stu-id="1a15f-106">The basics of the .NET Core Command Line Interface (CLI)</span></span>
- <span data-ttu-id="1a15f-107">Struktura aplikacji Konsolowej C#</span><span class="sxs-lookup"><span data-stu-id="1a15f-107">The structure of a C# Console Application</span></span>
- <span data-ttu-id="1a15f-108">Konsola operacje We/Wy</span><span class="sxs-lookup"><span data-stu-id="1a15f-108">Console I/O</span></span>
- <span data-ttu-id="1a15f-109">Podstawowe informacje dotyczące interfejsów API we/wy pliku w programie .NET</span><span class="sxs-lookup"><span data-stu-id="1a15f-109">The basics of File I/O APIs in .NET</span></span>
- <span data-ttu-id="1a15f-110">Podstawy opartego na zadaniach asynchronicznej programowanie na platformie .NET</span><span class="sxs-lookup"><span data-stu-id="1a15f-110">The basics of the Task-based Asynchronous Programming in .NET</span></span>

<span data-ttu-id="1a15f-111">Skompiluj aplikację, która odczytuje plik tekstowy i zwraca zawartość tego pliku tekstowego do konsoli.</span><span class="sxs-lookup"><span data-stu-id="1a15f-111">You’ll build an application that reads a text file, and echoes the contents of that text file to the console.</span></span> <span data-ttu-id="1a15f-112">Dane wyjściowe do konsoli jest realizowany do dopasowania wczytaniem go na głos.</span><span class="sxs-lookup"><span data-stu-id="1a15f-112">The output to the console is paced to match reading it aloud.</span></span> <span data-ttu-id="1a15f-113">Można przyspieszyć lub zwolnić tempie, naciskając klawisz "<" lub ">" kluczy.</span><span class="sxs-lookup"><span data-stu-id="1a15f-113">You can speed up or slow down the pace by pressing the ‘<’ or ‘>’ keys.</span></span>

<span data-ttu-id="1a15f-114">Istnieje wiele funkcji, w tym samouczku.</span><span class="sxs-lookup"><span data-stu-id="1a15f-114">There are a lot of features in this tutorial.</span></span> <span data-ttu-id="1a15f-115">Utworzymy je jedno po drugim.</span><span class="sxs-lookup"><span data-stu-id="1a15f-115">Let’s build them one by one.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1a15f-116">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="1a15f-116">Prerequisites</span></span>

<span data-ttu-id="1a15f-117">Należy skonfigurować maszynę w taki sposób, aby uruchomić platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1a15f-117">You’ll need to setup your machine to run .NET Core.</span></span> <span data-ttu-id="1a15f-118">Instrukcje dotyczące instalacji można znaleźć na [platformy .NET Core](https://www.microsoft.com/net/core) strony.</span><span class="sxs-lookup"><span data-stu-id="1a15f-118">You can find the installation instructions on the [.NET Core](https://www.microsoft.com/net/core) page.</span></span> <span data-ttu-id="1a15f-119">Windows, Linux, macOS lub w kontenerze platformy Docker, mogą uruchamiać tę aplikację.</span><span class="sxs-lookup"><span data-stu-id="1a15f-119">You can run this application on Windows, Linux, macOS or in a Docker container.</span></span>
<span data-ttu-id="1a15f-120">Musisz zainstalować wybrany edytor kodu.</span><span class="sxs-lookup"><span data-stu-id="1a15f-120">You’ll need to install your favorite code editor.</span></span>

## <a name="create-the-application"></a><span data-ttu-id="1a15f-121">Tworzenie aplikacji</span><span class="sxs-lookup"><span data-stu-id="1a15f-121">Create the Application</span></span>

<span data-ttu-id="1a15f-122">Pierwszym krokiem jest utworzenie nowej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1a15f-122">The first step is to create a new application.</span></span> <span data-ttu-id="1a15f-123">Otwórz wiersz polecenia i Utwórz nowy katalog aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1a15f-123">Open a command prompt and create a new directory for your application.</span></span> <span data-ttu-id="1a15f-124">Upewnij się, że sposób bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="1a15f-124">Make that the current directory.</span></span> <span data-ttu-id="1a15f-125">Wpisz polecenie `dotnet new console` w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="1a15f-125">Type the command `dotnet new console` at the command prompt.</span></span> <span data-ttu-id="1a15f-126">Spowoduje to utworzenie plikach startowych dla podstawowych aplikacji "Hello World".</span><span class="sxs-lookup"><span data-stu-id="1a15f-126">This creates the starter files for a basic "Hello World" application.</span></span>

<span data-ttu-id="1a15f-127">Przed rozpoczęciem wprowadzania modyfikacji, Przejdźmy przez czynności, aby uruchomić prostej aplikacji Hello World.</span><span class="sxs-lookup"><span data-stu-id="1a15f-127">Before you start making modifications, let’s go through the steps to run the simple Hello World application.</span></span> <span data-ttu-id="1a15f-128">Po utworzeniu aplikacji wpisz `dotnet restore` w wierszu polecenia.</span><span class="sxs-lookup"><span data-stu-id="1a15f-128">After creating the application, type `dotnet restore` at the command prompt.</span></span> <span data-ttu-id="1a15f-129">To polecenie uruchamia proces przywracania pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="1a15f-129">This command runs the NuGet package restore process.</span></span> <span data-ttu-id="1a15f-130">NuGet to Menedżer pakietów .NET.</span><span class="sxs-lookup"><span data-stu-id="1a15f-130">NuGet is a .NET package manager.</span></span> <span data-ttu-id="1a15f-131">To polecenie pobiera wszystkich brakujących zależności dla Twojego projektu.</span><span class="sxs-lookup"><span data-stu-id="1a15f-131">This command downloads any of the missing dependencies for your project.</span></span> <span data-ttu-id="1a15f-132">Jak jest to nowy projekt, żaden z zależności jest w miejscu, dzięki czemu przy pierwszym uruchomieniu pobierze platformę .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1a15f-132">As this is a new project, none of the dependencies are in place, so the first run will download the .NET Core framework.</span></span> <span data-ttu-id="1a15f-133">Po wykonaniu tego kroku początkowego, wystarczy uruchomić `dotnet restore` podczas dodawania nowych pakietów zależnych lub zaktualizować wersje tych zależności.</span><span class="sxs-lookup"><span data-stu-id="1a15f-133">After this initial step, you will only need to run `dotnet restore` when you add new dependent packages, or update the versions of any of your dependencies.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="1a15f-134">Po przywróceniu pakietów, możesz uruchomić `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="1a15f-134">After restoring packages, you run `dotnet build`.</span></span> <span data-ttu-id="1a15f-135">Wykonuje aparat kompilacji i tworzy pliku wykonywalnego aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1a15f-135">This executes the build engine and creates your application executable.</span></span> <span data-ttu-id="1a15f-136">Na koniec wykonaj `dotnet run` do uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1a15f-136">Finally, you execute `dotnet run` to run your application.</span></span>

<span data-ttu-id="1a15f-137">Prosty kod aplikacji Hello World znajduje się w pliku Program.cs.</span><span class="sxs-lookup"><span data-stu-id="1a15f-137">The simple Hello World application code is all in Program.cs.</span></span> <span data-ttu-id="1a15f-138">Otwórz ten plik za pomocą ulubionego edytora tekstu.</span><span class="sxs-lookup"><span data-stu-id="1a15f-138">Open that file with your favorite text editor.</span></span> <span data-ttu-id="1a15f-139">Jesteśmy przeprowadzasz pierwszy zmian.</span><span class="sxs-lookup"><span data-stu-id="1a15f-139">We’re about to make our first changes.</span></span>
<span data-ttu-id="1a15f-140">W górnej części pliku, zobacz using instrukcji:</span><span class="sxs-lookup"><span data-stu-id="1a15f-140">At the top of the file, see a using statement:</span></span>

```csharp
using System;
```

<span data-ttu-id="1a15f-141">Ta instrukcja informuje kompilator, że dowolne typy z `System` przestrzeni nazw znajdują się w zakresie.</span><span class="sxs-lookup"><span data-stu-id="1a15f-141">This statement tells the compiler that any types from the `System` namespace are in scope.</span></span> <span data-ttu-id="1a15f-142">Podobnie jak może być użyty innych języków obiektowo języka C# korzysta przestrzenie nazw do organizowania typów.</span><span class="sxs-lookup"><span data-stu-id="1a15f-142">Like other Object Oriented languages you may have used, C# uses namespaces to organize types.</span></span> <span data-ttu-id="1a15f-143">Ten program Hello World nie różni się.</span><span class="sxs-lookup"><span data-stu-id="1a15f-143">This Hello World program is no different.</span></span> <span data-ttu-id="1a15f-144">Aby zobaczyć, że program jest ujęty w przestrzeni nazw o nazwie na podstawie nazwy bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="1a15f-144">You can see that the program is enclosed in the namespace with the name based on the name of the current directory.</span></span> <span data-ttu-id="1a15f-145">W tym samouczku zmienimy nazwę przestrzeni nazw do `TeleprompterConsole`:</span><span class="sxs-lookup"><span data-stu-id="1a15f-145">For this tutorial, let's change the name of the namespace to `TeleprompterConsole`:</span></span>

```csharp
namespace TeleprompterConsole
```

## <a name="reading-and-echoing-the-file"></a><span data-ttu-id="1a15f-146">Odczytywanie i wyświetlania pliku</span><span class="sxs-lookup"><span data-stu-id="1a15f-146">Reading and Echoing the File</span></span>

<span data-ttu-id="1a15f-147">Pierwszą funkcją do dodania jest możliwość odczytywanie pliku tekstowego i wyświetlić ten tekst do konsoli.</span><span class="sxs-lookup"><span data-stu-id="1a15f-147">The first feature to add is the ability to read a text file and display all that text to the console.</span></span> <span data-ttu-id="1a15f-148">Najpierw Dodajmy pliku tekstowego.</span><span class="sxs-lookup"><span data-stu-id="1a15f-148">First, let’s add a text file.</span></span> <span data-ttu-id="1a15f-149">Kopiuj [sampleQuotes.txt](https://github.com/dotnet/samples/raw/master/csharp/getting-started/console-teleprompter/sampleQuotes.txt) plik z repozytorium GitHub, w tym [przykładowe](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-teleprompter) w katalogu projektu.</span><span class="sxs-lookup"><span data-stu-id="1a15f-149">Copy the [sampleQuotes.txt](https://github.com/dotnet/samples/raw/master/csharp/getting-started/console-teleprompter/sampleQuotes.txt) file from the GitHub repository for this [sample](https://github.com/dotnet/samples/tree/master/csharp/getting-started/console-teleprompter) into your project directory.</span></span> <span data-ttu-id="1a15f-150">To będzie służyć jako skrypt dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1a15f-150">This will serve as the script for your application.</span></span> <span data-ttu-id="1a15f-151">Jeśli chcesz uzyskać informacje dotyczące sposobu pobierania przykładowej aplikacji na potrzeby tego artykułu zapoznaj się z instrukcjami w [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples) tematu.</span><span class="sxs-lookup"><span data-stu-id="1a15f-151">If you would like information on how to download the sample app for this topic, see the instructions in the [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples) topic.</span></span>

<span data-ttu-id="1a15f-152">Następnie dodaj następującą metodę w swojej `Program` klasy (bezpośrednio poniżej `Main` metoda):</span><span class="sxs-lookup"><span data-stu-id="1a15f-152">Next, add the following method in your `Program` class (right below the `Main` method):</span></span>

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

<span data-ttu-id="1a15f-153">Ta metoda używa typów z dwa nowe przestrzenie nazw.</span><span class="sxs-lookup"><span data-stu-id="1a15f-153">This method uses types from two new namespaces.</span></span> <span data-ttu-id="1a15f-154">W tym można skompilować należy dodać następujące dwa wiersze na początku pliku:</span><span class="sxs-lookup"><span data-stu-id="1a15f-154">For this to compile you’ll need to add the following two lines to the top of the file:</span></span>

```csharp
using System.Collections.Generic;
using System.IO;
```

<span data-ttu-id="1a15f-155"><xref:System.Collections.Generic.IEnumerable%601> Interfejsu jest zdefiniowany w <xref:System.Collections.Generic> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="1a15f-155">The <xref:System.Collections.Generic.IEnumerable%601> interface is defined in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="1a15f-156"><xref:System.IO.File> Klasa jest zdefiniowana w <xref:System.IO> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="1a15f-156">The <xref:System.IO.File> class is defined in the <xref:System.IO> namespace.</span></span>

<span data-ttu-id="1a15f-157">Ta metoda jest specjalnym typem metodę języka C# o nazwie *metody iteratora*.</span><span class="sxs-lookup"><span data-stu-id="1a15f-157">This method is a special type of C# method called an *Iterator method*.</span></span> <span data-ttu-id="1a15f-158">Moduł wyliczający metody zwracają sekwencji, które zostaną ocenione opóźnieniem.</span><span class="sxs-lookup"><span data-stu-id="1a15f-158">Enumerator methods return sequences that are evaluated lazily.</span></span> <span data-ttu-id="1a15f-159">Oznacza to, że każdy element w sekwencji jest generowany, zgodnie z żądaniem kodu korzystanie z sekwencji.</span><span class="sxs-lookup"><span data-stu-id="1a15f-159">That means each item in the sequence is generated as it is requested by the code consuming the sequence.</span></span> <span data-ttu-id="1a15f-160">Moduł wyliczający metody są metodami, które zawierają co najmniej jeden [ `yield return` ](../language-reference/keywords/yield.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="1a15f-160">Enumerator methods are methods that contain one or more [`yield return`](../language-reference/keywords/yield.md) statements.</span></span> <span data-ttu-id="1a15f-161">Obiekt zwrócony przez `ReadFrom` metoda zawiera kod, aby wygenerować każdego elementu w sekwencji.</span><span class="sxs-lookup"><span data-stu-id="1a15f-161">The object returned by the `ReadFrom` method contains the code to generate each item in the sequence.</span></span> <span data-ttu-id="1a15f-162">W tym przykładzie, który obejmuje odczytywanie kolejny wiersz tekstu z pliku źródłowego i zwraca ciąg.</span><span class="sxs-lookup"><span data-stu-id="1a15f-162">In this example, that involves reading the next line of text from the source file, and returning that string.</span></span> <span data-ttu-id="1a15f-163">Za każdym żądaniem kod wywołujący następnego elementu w sekwencji, kod odczytuje następny wiersz tekstu z pliku i zwraca go.</span><span class="sxs-lookup"><span data-stu-id="1a15f-163">Each time the calling code requests the next item from the sequence, the code reads the next line of text from the file and returns it.</span></span> <span data-ttu-id="1a15f-164">Gdy plik jest całkowicie do odczytu, sekwencja oznacza, że brak elementów.</span><span class="sxs-lookup"><span data-stu-id="1a15f-164">When the file is completely read, the sequence indicates that there are no more items.</span></span>

<span data-ttu-id="1a15f-165">Istnieją dwa inne C# składni elementy, które mogą być dla Ciebie nowe.</span><span class="sxs-lookup"><span data-stu-id="1a15f-165">There are two other C# syntax elements that may be new to you.</span></span> <span data-ttu-id="1a15f-166">[ `using` ](../language-reference/keywords/using-statement.md) Poufności informacji w tej metodzie zarządza czyszczenie zasobów.</span><span class="sxs-lookup"><span data-stu-id="1a15f-166">The [`using`](../language-reference/keywords/using-statement.md) statement in this method manages resource cleanup.</span></span> <span data-ttu-id="1a15f-167">Zmienna, która jest inicjowana w `using` — instrukcja (`reader`, w tym przykładzie) należy zaimplementować <xref:System.IDisposable> interfejsu.</span><span class="sxs-lookup"><span data-stu-id="1a15f-167">The variable that is initialized in the `using` statement (`reader`, in this example) must implement the <xref:System.IDisposable> interface.</span></span> <span data-ttu-id="1a15f-168">Ten interfejs definiuje jedną metodę `Dispose`, która powinna być wywoływana, gdy zasobu powinny zostać opublikowane.</span><span class="sxs-lookup"><span data-stu-id="1a15f-168">That interface defines a single method, `Dispose`, that should be called when the resource should be released.</span></span> <span data-ttu-id="1a15f-169">Kompilator generuje to wywołanie, gdy wykonywanie osiągnie zamykającym nawiasem klamrowym `using` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="1a15f-169">The compiler generates that call when execution reaches the closing brace of the `using` statement.</span></span> <span data-ttu-id="1a15f-170">Kod wygenerowany przez kompilator zapewnia, jest zwolnienie zasobów nawet wtedy, gdy wyjątek jest generowany z kodu w bloku zdefiniowane za pomocą instrukcji.</span><span class="sxs-lookup"><span data-stu-id="1a15f-170">The compiler-generated code ensures that the resource is released even if an exception is thrown from the code in the block defined by the using statement.</span></span>

<span data-ttu-id="1a15f-171">`reader` Zmienna jest zdefiniowana za pomocą `var` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="1a15f-171">The `reader` variable is defined using the `var` keyword.</span></span> <span data-ttu-id="1a15f-172">[`var`](../language-reference/keywords/var.md) definiuje *niejawnie typizowanej zmiennej lokalnej*.</span><span class="sxs-lookup"><span data-stu-id="1a15f-172">[`var`](../language-reference/keywords/var.md) defines an *implicitly typed local variable*.</span></span> <span data-ttu-id="1a15f-173">Oznacza to, że typ zmiennej jest określana przez typ kompilacji, przypisana do zmiennej obiektu.</span><span class="sxs-lookup"><span data-stu-id="1a15f-173">That means the type of the variable is determined by the compile-time type of the object assigned to the variable.</span></span> <span data-ttu-id="1a15f-174">Tutaj, która jest wartością zwracaną z <xref:System.IO.File.OpenText(System.String)> metoda, która jest <xref:System.IO.StreamReader> obiektu.</span><span class="sxs-lookup"><span data-stu-id="1a15f-174">Here, that is the return value from the <xref:System.IO.File.OpenText(System.String)> method, which is a <xref:System.IO.StreamReader> object.</span></span>

<span data-ttu-id="1a15f-175">Teraz możemy wypełnienie kodu, który można odczytać pliku w `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="1a15f-175">Now, let’s fill in the code to read the file in the `Main` method:</span></span>

```csharp
var lines = ReadFrom("sampleQuotes.txt");
foreach (var line in lines)
{
    Console.WriteLine(line);
}
```

<span data-ttu-id="1a15f-176">Uruchom program (przy użyciu `dotnet run`) i zobaczyć wszystkich wierszy drukowane do konsoli.</span><span class="sxs-lookup"><span data-stu-id="1a15f-176">Run the program (using `dotnet run`) and you can see every line printed out to the console.</span></span>

## <a name="adding-delays-and-formatting-output"></a><span data-ttu-id="1a15f-177">Dodawanie opóźnień i formatowanie danych wyjściowych</span><span class="sxs-lookup"><span data-stu-id="1a15f-177">Adding Delays and Formatting output</span></span>

<span data-ttu-id="1a15f-178">Posiadane zasoby są wyświetlane w zbyt szybko, aby odczytywać.</span><span class="sxs-lookup"><span data-stu-id="1a15f-178">What you have is being displayed far too fast to read aloud.</span></span> <span data-ttu-id="1a15f-179">Teraz należy dodać opóźnienia w danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="1a15f-179">Now you need to add the delays in the output.</span></span> <span data-ttu-id="1a15f-180">Po rozpoczęciu, tworzyć część kodu core, która umożliwia przetwarzanie asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="1a15f-180">As you start, you’ll be building some of the core code that enables asynchronous processing.</span></span> <span data-ttu-id="1a15f-181">Jednak te pierwsze kroki są zgodne z kilku niezalecane wzorce.</span><span class="sxs-lookup"><span data-stu-id="1a15f-181">However, these first steps will follow a few anti-patterns.</span></span> <span data-ttu-id="1a15f-182">Niezalecane wzorce są wskazano w komentarzach, Dodaj kod, a kod zostanie zaktualizowany w kolejnych krokach.</span><span class="sxs-lookup"><span data-stu-id="1a15f-182">The anti-patterns are pointed out in comments as you add the code, and the code will be updated in later steps.</span></span>

<span data-ttu-id="1a15f-183">Istnieją dwa kroki, aby w tej sekcji.</span><span class="sxs-lookup"><span data-stu-id="1a15f-183">There are two steps to this section.</span></span> <span data-ttu-id="1a15f-184">Po pierwsze zostaną zaktualizowane metody iteratora, aby zwrócić pojedynczego słowa zamiast całego wierszy.</span><span class="sxs-lookup"><span data-stu-id="1a15f-184">First, you’ll update the iterator method to return single words instead of entire lines.</span></span> <span data-ttu-id="1a15f-185">Zostanie to zrobione za pomocą tych zmian.</span><span class="sxs-lookup"><span data-stu-id="1a15f-185">That’s done with these modifications.</span></span> <span data-ttu-id="1a15f-186">Zastąp `yield return line;` instrukcję, używając następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="1a15f-186">Replace the `yield return line;` statement with the following code:</span></span>

```csharp
var words = line.Split(' ');
foreach (var word in words)
{
    yield return word + " ";
}
yield return Environment.NewLine;
```

<span data-ttu-id="1a15f-187">Następnie należy zmodyfikować, jak używać wiersze pliku i dodawanie opóźnienia po zapisaniu każdego wyrazu.</span><span class="sxs-lookup"><span data-stu-id="1a15f-187">Next, you need to modify how you consume the lines of the file, and add a delay after writing each word.</span></span> <span data-ttu-id="1a15f-188">Zastąp `Console.WriteLine(line)` instrukcji w `Main` metody z następujący blok:</span><span class="sxs-lookup"><span data-stu-id="1a15f-188">Replace the `Console.WriteLine(line)` statement in the `Main` method with the following block:</span></span>

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

<span data-ttu-id="1a15f-189"><xref:System.Threading.Tasks.Task> Klasa się zebrała <xref:System.Threading.Tasks> przestrzeni nazw, dlatego należy go dodać `using` instrukcji w górnej części pliku:</span><span class="sxs-lookup"><span data-stu-id="1a15f-189">The <xref:System.Threading.Tasks.Task> class is in the <xref:System.Threading.Tasks> namespace, so you need to add that `using` statement at the top of file:</span></span>

```csharp
using System.Threading.Tasks;
```

<span data-ttu-id="1a15f-190">Uruchamianie aplikacji przykładowej i sprawdź dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="1a15f-190">Run the sample, and check the output.</span></span> <span data-ttu-id="1a15f-191">Teraz każdego pojedynczego wyrazu drukowania, a następnie z opóźnieniem 200 ms.</span><span class="sxs-lookup"><span data-stu-id="1a15f-191">Now, each single word is printed, followed by a 200 ms delay.</span></span> <span data-ttu-id="1a15f-192">Jednak wyświetlane dane wyjściowe pokazują niektóre problemy, ponieważ źródłowy plik tekstowy zawiera kilka wierszy, które mają więcej niż 80 znaków bez podziału wiersza.</span><span class="sxs-lookup"><span data-stu-id="1a15f-192">However, the displayed output shows some issues because the source text file has several lines that have more than 80 characters without a line break.</span></span> <span data-ttu-id="1a15f-193">Który może być trudny do odczytania, podczas gdy przewijanie jest przez.</span><span class="sxs-lookup"><span data-stu-id="1a15f-193">That can be hard to read while it's scrolling by.</span></span> <span data-ttu-id="1a15f-194">To łatwe rozwiązać problem.</span><span class="sxs-lookup"><span data-stu-id="1a15f-194">That’s easy to fix.</span></span> <span data-ttu-id="1a15f-195">Można będzie po prostu śledzić długość każdego wiersza i wygenerować nowy wiersz, w każdym przypadku, gdy długość wiersza osiągnie określony próg.</span><span class="sxs-lookup"><span data-stu-id="1a15f-195">You’ll just keep track of the length of each line, and generate a new line whenever the line length reaches a certain threshold.</span></span> <span data-ttu-id="1a15f-196">Zadeklaruj zmienną lokalnej po zadeklarowaniu `words` w `ReadFrom` metodę, która zawiera długość wiersza:</span><span class="sxs-lookup"><span data-stu-id="1a15f-196">Declare a local variable after the declaration of `words` in the `ReadFrom` method that holds the line length:</span></span>

```csharp
var lineLength = 0;
```

<span data-ttu-id="1a15f-197">Następnie należy dodać następujący kod po `yield return word + " ";` — instrukcja (przed zamykający nawias klamrowy):</span><span class="sxs-lookup"><span data-stu-id="1a15f-197">Then, add the following code after the `yield return word + " ";` statement (before the closing brace):</span></span>

```csharp
lineLength += word.Length + 1;
if (lineLength > 70)
{
    yield return Environment.NewLine;
    lineLength = 0;
}
```

<span data-ttu-id="1a15f-198">Uruchom aplikację przykładową, a będzie można odczytywać w jej wstępnie skonfigurowanych tempie.</span><span class="sxs-lookup"><span data-stu-id="1a15f-198">Run the sample, and you’ll be able to read aloud at its pre-configured pace.</span></span>

## <a name="async-tasks"></a><span data-ttu-id="1a15f-199">Zadań asynchronicznych</span><span class="sxs-lookup"><span data-stu-id="1a15f-199">Async Tasks</span></span>

<span data-ttu-id="1a15f-200">W tym ostatnim kroku dodasz kod, aby zapisywać dane wyjściowe asynchronicznie w ramach jednego zadania podczas również działa inne zadanie, które można odczytać danych wejściowych od użytkownika, jeśli chcesz przyspieszyć lub zwolnić wyświetlania tekstu.</span><span class="sxs-lookup"><span data-stu-id="1a15f-200">In this final step, you’ll add the code to write the output asynchronously in one task, while also running another task to read input from the user if they want to speed up or slow down the text display.</span></span> <span data-ttu-id="1a15f-201">Ma kilka kroków i do końca, będziesz mieć wszystkie aktualizacje, które są potrzebne.</span><span class="sxs-lookup"><span data-stu-id="1a15f-201">This has a few steps in it and by the end, you’ll have all the updates that you need.</span></span>
<span data-ttu-id="1a15f-202">Pierwszym krokiem jest utworzenie asynchronicznego <xref:System.Threading.Tasks.Task> zwracania metody, która przedstawia kod do tej pory utworzono do odczytywania i wyświetlić plik.</span><span class="sxs-lookup"><span data-stu-id="1a15f-202">The first step is to create an asynchronous <xref:System.Threading.Tasks.Task> returning method that represents the code you’ve created so far to read and display the file.</span></span>

<span data-ttu-id="1a15f-203">Dodaj tę metodę, aby Twoje `Program` klasy (jest zajęta z treści usługi `Main` metody):</span><span class="sxs-lookup"><span data-stu-id="1a15f-203">Add this method to your `Program` class (it’s taken from the body of your `Main` method):</span></span>

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

<span data-ttu-id="1a15f-204">Można zauważyć dwie zmiany.</span><span class="sxs-lookup"><span data-stu-id="1a15f-204">You’ll notice two changes.</span></span> <span data-ttu-id="1a15f-205">Po pierwsze, w treści metody, zamiast wywoływać metodę <xref:System.Threading.Tasks.Task.Wait> synchronicznie oczekiwania na zakończenie zadania, ta wersja wykorzystuje `await` — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="1a15f-205">First, in the body of the method, instead of calling <xref:System.Threading.Tasks.Task.Wait> to synchronously wait for a task to finish, this version uses the `await` keyword.</span></span> <span data-ttu-id="1a15f-206">Aby to zrobić, należy dodać `async` modyfikatora podpis metody.</span><span class="sxs-lookup"><span data-stu-id="1a15f-206">In order to do that, you need to add the `async` modifier to the method signature.</span></span> <span data-ttu-id="1a15f-207">Ta metoda zwraca `Task`.</span><span class="sxs-lookup"><span data-stu-id="1a15f-207">This method returns a `Task`.</span></span> <span data-ttu-id="1a15f-208">Należy zauważyć, że nie istnieją żadne instrukcjach return, które zwracają `Task` obiektu.</span><span class="sxs-lookup"><span data-stu-id="1a15f-208">Notice that there are no return statements that return a `Task` object.</span></span> <span data-ttu-id="1a15f-209">Zamiast tego, który `Task` obiekt jest tworzony przez kod, kompilator generuje, gdy używasz `await` operatora.</span><span class="sxs-lookup"><span data-stu-id="1a15f-209">Instead, that `Task` object is created by code the compiler generates when you use the `await` operator.</span></span> <span data-ttu-id="1a15f-210">Można sobie wyobrazić, że ta metoda zwraca po osiągnięciu `await`.</span><span class="sxs-lookup"><span data-stu-id="1a15f-210">You can imagine that this method returns when it reaches an `await`.</span></span> <span data-ttu-id="1a15f-211">Zwrócony `Task` wskazuje, że nie zakończył pracy.</span><span class="sxs-lookup"><span data-stu-id="1a15f-211">The returned `Task` indicates that the work has not completed.</span></span>
<span data-ttu-id="1a15f-212">Metoda zostanie wznowione, gdy zakończy się oczekiwane zadanie.</span><span class="sxs-lookup"><span data-stu-id="1a15f-212">The method resumes when the awaited task completes.</span></span> <span data-ttu-id="1a15f-213">Kiedy zostało wykonane do zakończenia zwracanego `Task` wskazuje, że została zakończona.</span><span class="sxs-lookup"><span data-stu-id="1a15f-213">When it has executed to completion, the returned `Task` indicates that it is complete.</span></span>
<span data-ttu-id="1a15f-214">Wywoływanie kodu, można monitorować zwróconą `Task` ustalenie, kiedy zostało ono ukończone.</span><span class="sxs-lookup"><span data-stu-id="1a15f-214">Calling code can monitor that returned `Task` to determine when it has completed.</span></span>

<span data-ttu-id="1a15f-215">Ta nowa metoda można wywołać w swojej `Main` metody:</span><span class="sxs-lookup"><span data-stu-id="1a15f-215">You can call this new method in your `Main` method:</span></span>

```csharp
ShowTeleprompter().Wait();
```

<span data-ttu-id="1a15f-216">W tym miejscu, w `Main`, kod synchronicznie oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="1a15f-216">Here, in `Main`, the code does synchronously wait.</span></span> <span data-ttu-id="1a15f-217">Należy używać `await` operatora, zamiast czekać synchronicznie, jeśli to możliwe.</span><span class="sxs-lookup"><span data-stu-id="1a15f-217">You should use the `await` operator instead of synchronously waiting whenever possible.</span></span> <span data-ttu-id="1a15f-218">Jednak w aplikacji konsoli `Main` metody, nie można użyć `await` operatora.</span><span class="sxs-lookup"><span data-stu-id="1a15f-218">But, in a console application’s `Main` method, you cannot use the `await` operator.</span></span> <span data-ttu-id="1a15f-219">Które mogłyby spowodować zamykania aplikacji, zanim wszystkie zadania zostały ukończone.</span><span class="sxs-lookup"><span data-stu-id="1a15f-219">That would result in the application exiting before all tasks have completed.</span></span>

> [!NOTE]
> <span data-ttu-id="1a15f-220">Jeśli używasz języka C# 7.1 lub nowszy, możesz tworzyć aplikacje konsoli przy użyciu [ `async` `Main` metoda](../whats-new/csharp-7-1.md#async-main).</span><span class="sxs-lookup"><span data-stu-id="1a15f-220">If you use C# 7.1 or later, you can create console applications with [`async` `Main` method](../whats-new/csharp-7-1.md#async-main).</span></span>

<span data-ttu-id="1a15f-221">Następnie należy napisać drugiej metodzie asynchronicznej odczytywany z konsoli, zwracając uwagę na "<" i ">" kluczy.</span><span class="sxs-lookup"><span data-stu-id="1a15f-221">Next, you need to write the second asynchronous method to read from the Console and watch for the ‘<’ and ‘>’ keys.</span></span> <span data-ttu-id="1a15f-222">Poniżej przedstawiono metodę, którą możesz dodać do tego zadania:</span><span class="sxs-lookup"><span data-stu-id="1a15f-222">Here’s the method you add for that task:</span></span>

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

<span data-ttu-id="1a15f-223">Spowoduje to utworzenie wyrażenia lambda do reprezentowania <xref:System.Action> delegat, który odczytuje klucz z konsoli i modyfikuje zmienną lokalną, reprezentujący opóźnienie w przypadku, gdy użytkownik naciśnie "<" lub ">" kluczy.</span><span class="sxs-lookup"><span data-stu-id="1a15f-223">This creates a lambda expression to represent an <xref:System.Action> delegate that reads a key from the Console and modifies a local variable representing the delay when the user presses the ‘<’ or ‘>’ keys.</span></span> <span data-ttu-id="1a15f-224">Ta metoda używa <xref:System.Console.ReadKey> do blokowania i poczekać na użytkownika poprzez naciśnięcie klawisza.</span><span class="sxs-lookup"><span data-stu-id="1a15f-224">This method uses <xref:System.Console.ReadKey> to block and wait for the user to press a key.</span></span>

<span data-ttu-id="1a15f-225">Aby zakończyć tę funkcję, musisz utworzyć nowy `async Task` metodę, która rozpoczyna się w obu tych zadań zwracającą (`GetInput` i `ShowTeleprompter`), a także zarządza udostępnionych danych między te dwa zadania.</span><span class="sxs-lookup"><span data-stu-id="1a15f-225">To finish this feature, you need to create a new `async Task` returning method that starts both of these tasks (`GetInput` and `ShowTeleprompter`), and also manages the shared data between these two tasks.</span></span>

<span data-ttu-id="1a15f-226">Nadszedł czas, aby utworzyć klasę, która może obsłużyć udostępnionych danych między te dwa zadania.</span><span class="sxs-lookup"><span data-stu-id="1a15f-226">It’s time to create a class that can handle the shared data between these two tasks.</span></span> <span data-ttu-id="1a15f-227">Ta klasa zawiera dwie właściwości publiczne: opóźnienie i flagi `Done` aby potwierdzić, że plik został całkowicie przeczytane:</span><span class="sxs-lookup"><span data-stu-id="1a15f-227">This class contains two public properties: the delay, and a flag `Done` to indicate that the file has been completely read:</span></span>

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

        public bool Done { get; private set; }

        public void SetDone()
        {
            Done = true;
        }
    }
}
```

<span data-ttu-id="1a15f-228">Umieść tej klasy w nowym pliku a następnie zamieścić tej klasy w `TeleprompterConsole` przestrzeni nazw, jak pokazano powyżej.</span><span class="sxs-lookup"><span data-stu-id="1a15f-228">Put that class in a new file, and enclose that class in the `TeleprompterConsole` namespace as shown above.</span></span> <span data-ttu-id="1a15f-229">Należy także dodać `using static` instrukcji, dzięki czemu możesz odwoływać się do `Min` i `Max` metody bez otaczającej nazwy klasy lub obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="1a15f-229">You’ll also need to add a `using static` statement so that you can reference the `Min` and `Max` methods without the enclosing class or namespace names.</span></span> <span data-ttu-id="1a15f-230">A [ `using static` ](../language-reference/keywords/using-static.md) instrukcji imports metody z jednej klasy.</span><span class="sxs-lookup"><span data-stu-id="1a15f-230">A [`using static`](../language-reference/keywords/using-static.md) statement imports the methods from one class.</span></span> <span data-ttu-id="1a15f-231">Jest to w przeciwieństwie `using` instrukcji używany do tej pory, które zostały zaimportowane wszystkie klasy z przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="1a15f-231">This is in contrast with the `using` statements used up to this point that have imported all classes from a namespace.</span></span>

```csharp
using static System.Math;
```

<span data-ttu-id="1a15f-232">Z innych funkcji języka, co nowego jest [ `lock` ](../language-reference/keywords/lock-statement.md) instrukcji.</span><span class="sxs-lookup"><span data-stu-id="1a15f-232">The other language feature that’s new is the [`lock`](../language-reference/keywords/lock-statement.md) statement.</span></span> <span data-ttu-id="1a15f-233">Niniejszych gwarantuje, że tylko jednego wątku może należeć ten kod w dowolnym momencie.</span><span class="sxs-lookup"><span data-stu-id="1a15f-233">This statement ensures that only a single thread can be in that code at any given time.</span></span> <span data-ttu-id="1a15f-234">Jeśli jeden wątek znajduje się w sekcji zablokowane, inne wątki musi czekać na pierwszym wątku zakończyć tę sekcję.</span><span class="sxs-lookup"><span data-stu-id="1a15f-234">If one thread is in the locked section, other threads must wait for the first thread to exit that section.</span></span> <span data-ttu-id="1a15f-235">`lock` Instrukcja używa obiektu, który chroni sekcji blokady.</span><span class="sxs-lookup"><span data-stu-id="1a15f-235">The `lock` statement uses an object that guards the lock section.</span></span> <span data-ttu-id="1a15f-236">Ta klasa jest zgodna standardowa idiom można zablokować obiektu prywatnego w klasie.</span><span class="sxs-lookup"><span data-stu-id="1a15f-236">This class follows a standard idiom to lock a private object in the class.</span></span>

<span data-ttu-id="1a15f-237">Następnie należy zaktualizować `ShowTeleprompter` i `GetInput` metody, aby użyć nowego `config` obiektu.</span><span class="sxs-lookup"><span data-stu-id="1a15f-237">Next, you need to update the `ShowTeleprompter` and `GetInput` methods to use the new `config` object.</span></span> <span data-ttu-id="1a15f-238">Zapis jeden końcowy `Task` zwracanie `async` metodę, aby uruchomić zarówno do zadań i Zakończ po zakończeniu pierwszego zadania:</span><span class="sxs-lookup"><span data-stu-id="1a15f-238">Write one final `Task` returning `async` method to start both tasks and exit when the first task finishes:</span></span>

```csharp
private static async Task RunTeleprompter()
{
    var config = new TelePrompterConfig();
    var displayTask = ShowTeleprompter(config);

    var speedTask = GetInput(config);
    await Task.WhenAny(displayTask, speedTask);
}
```

<span data-ttu-id="1a15f-239">Jeden nowa metoda w tym miejscu jest <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])> wywołania.</span><span class="sxs-lookup"><span data-stu-id="1a15f-239">The one new method here is the <xref:System.Threading.Tasks.Task.WhenAny(System.Threading.Tasks.Task[])> call.</span></span> <span data-ttu-id="1a15f-240">Tworząca `Task` który zakończy się zaraz po zakończeniu wszystkich zadań na liście argumentów.</span><span class="sxs-lookup"><span data-stu-id="1a15f-240">That creates a `Task` that finishes as soon as any of the tasks in its argument list completes.</span></span>

<span data-ttu-id="1a15f-241">Następnie należy zaktualizować obydwa `ShowTeleprompter` i `GetInput` metod do zastosowania `config` obiektu opóźnienia:</span><span class="sxs-lookup"><span data-stu-id="1a15f-241">Next, you need to update both the `ShowTeleprompter` and `GetInput` methods to use the `config` object for the delay:</span></span>

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

<span data-ttu-id="1a15f-242">Nowa wersja `ShowTeleprompter` wywołuje nową metodę `TeleprompterConfig` klasy.</span><span class="sxs-lookup"><span data-stu-id="1a15f-242">This new version of `ShowTeleprompter` calls a new method in the `TeleprompterConfig` class.</span></span> <span data-ttu-id="1a15f-243">Teraz, musisz zaktualizować `Main` do wywołania `RunTeleprompter` zamiast `ShowTeleprompter`:</span><span class="sxs-lookup"><span data-stu-id="1a15f-243">Now, you need to update `Main` to call `RunTeleprompter` instead of `ShowTeleprompter`:</span></span>

```csharp
RunTeleprompter().Wait();
```

## <a name="conclusion"></a><span data-ttu-id="1a15f-244">Wniosek</span><span class="sxs-lookup"><span data-stu-id="1a15f-244">Conclusion</span></span>

<span data-ttu-id="1a15f-245">W tym samouczku pokazano, że możesz pewną liczbę funkcji wokół języka C# i biblioteki .NET Core związanych z pracą w aplikacjach konsoli.</span><span class="sxs-lookup"><span data-stu-id="1a15f-245">This tutorial showed you a number of the features around the C# language and the .NET Core libraries related to working in Console applications.</span></span>
<span data-ttu-id="1a15f-246">Możesz utworzyć na tej wiedzy do Dowiedz się więcej o języku, klas i wprowadzone w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="1a15f-246">You can build on this knowledge to explore more about the language, and the classes introduced here.</span></span> <span data-ttu-id="1a15f-247">Przedstawiono podstawowe informacje dotyczące plików i we/wy konsoli, blokowania i bez blokowania użycia asynchronicznego programowania opartego na zadaniach, samouczek języka C# oraz jak C# programy są uporządkowane i interfejs wiersza polecenia programu .NET Core oraz narzędzia.</span><span class="sxs-lookup"><span data-stu-id="1a15f-247">You’ve seen the basics of File and Console I/O, blocking and non-blocking use of the Task-based asynchronous programming, a tour of the C# language and how C# programs are organized and the .NET Core Command Line Interface and tools.</span></span>

<span data-ttu-id="1a15f-248">Aby uzyskać więcej informacji na temat operacji We/Wy w pliku zobacz [plików i we/wy Stream](../../standard/io/index.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="1a15f-248">For more information about File I/O, see the [File and Stream I/O](../../standard/io/index.md) topic.</span></span> <span data-ttu-id="1a15f-249">Aby uzyskać więcej informacji na temat asynchronicznego modelu programowania, w tym samouczku używane zobacz [opartego na zadaniach Asynchronous Programming](../..//standard/parallel-programming/task-based-asynchronous-programming.md) tematu i [programowania asynchronicznego](../async.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="1a15f-249">For more information about asynchronous programming model used in this tutorial, see the [Task-based Asynchronous Programming](../..//standard/parallel-programming/task-based-asynchronous-programming.md) topic and the [Asynchronous programming](../async.md) topic.</span></span>

---
title: Rozpoczynanie pracy z platformą .NET Core przy użyciu interfejsu wiersza polecenia
description: Samouczek krok po kroku, pokazujący sposób rozpocząć pracę z platformą .NET Core w Windows, Linux lub macOS przy użyciu interfejsu wiersza polecenia (CLI) platformy .NET Core.
author: cartermp
ms.date: 09/10/2018
ms.technology: dotnet-cli
ms.custom: seodec18
ms.openlocfilehash: 92ca5149ad5f0e4a50c809a316123fbf77d4152d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61646972"
---
# <a name="get-started-with-net-core-on-windowslinuxmacos-using-the-command-line"></a><span data-ttu-id="ddd50-103">Rozpoczynanie pracy z platformą .NET Core w Windows/Linux/macOS przy użyciu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="ddd50-103">Get started with .NET Core on Windows/Linux/macOS using the command line</span></span>

<span data-ttu-id="ddd50-104">W tym temacie pokazują sposób rozpoczęcia tworzenia aplikacji dla wielu platform, na komputerze przy użyciu narzędzi interfejsu wiersza polecenia platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ddd50-104">This topic will show you how to start developing cross-platforms apps in your machine using the .NET Core CLI tools.</span></span>

<span data-ttu-id="ddd50-105">Jeśli jesteś zaznajomiony z zestawu narzędzi interfejsu wiersza polecenia platformy .NET Core, zapoznaj się z [Omówienie zestawu .NET Core SDK](../tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="ddd50-105">If you're unfamiliar with the .NET Core CLI toolset, read the [.NET Core SDK overview](../tools/index.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ddd50-106">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="ddd50-106">Prerequisites</span></span>

- <span data-ttu-id="ddd50-107">[.NET Core SDK 2.1](https://www.microsoft.com/net/download/core).</span><span class="sxs-lookup"><span data-stu-id="ddd50-107">[.NET Core SDK 2.1](https://www.microsoft.com/net/download/core).</span></span>
- <span data-ttu-id="ddd50-108">Edytor tekstu lub ulubionego edytora kodu.</span><span class="sxs-lookup"><span data-stu-id="ddd50-108">A text editor or code editor of your choice.</span></span>

## <a name="hello-console-app"></a><span data-ttu-id="ddd50-109">Witaj, aplikacja Konsolowa!</span><span class="sxs-lookup"><span data-stu-id="ddd50-109">Hello, Console App!</span></span>

<span data-ttu-id="ddd50-110">Możesz [wyświetlić lub pobrać przykładowy kod](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) z repozytorium dotnet/samples w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="ddd50-110">You can [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) from the dotnet/samples GitHub repository.</span></span> <span data-ttu-id="ddd50-111">Aby uzyskać instrukcje pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="ddd50-111">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="ddd50-112">Otwórz wiersz polecenia i Utwórz folder o nazwie *Hello*.</span><span class="sxs-lookup"><span data-stu-id="ddd50-112">Open a command prompt and create a folder named *Hello*.</span></span> <span data-ttu-id="ddd50-113">Przejdź do folderu, który został utworzony, a następnie wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="ddd50-113">Navigate to the folder you created and type the following:</span></span>

```console
dotnet new console
dotnet run
```

<span data-ttu-id="ddd50-114">Zróbmy szybkiego przewodnika:</span><span class="sxs-lookup"><span data-stu-id="ddd50-114">Let's do a quick walkthrough:</span></span>

1. `dotnet new console`

   <span data-ttu-id="ddd50-115">[`dotnet new`](../tools/dotnet-new.md) Tworzy aktualnej `Hello.csproj` pliku projektu z zależnościami, które są niezbędne do tworzenia aplikacji konsolowej.</span><span class="sxs-lookup"><span data-stu-id="ddd50-115">[`dotnet new`](../tools/dotnet-new.md) creates an up-to-date `Hello.csproj` project file with the dependencies necessary to build a console app.</span></span>  <span data-ttu-id="ddd50-116">Tworzy również `Program.cs`, podstawowy plik zawierający punkt wejścia dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ddd50-116">It also creates a `Program.cs`, a basic file containing the entry point for the application.</span></span>

   <span data-ttu-id="ddd50-117">`Hello.csproj`:</span><span class="sxs-lookup"><span data-stu-id="ddd50-117">`Hello.csproj`:</span></span>

   [!code[Hello.csproj](../../../samples/core/console-apps/HelloMsBuild/Hello.csproj)]

   <span data-ttu-id="ddd50-118">Plik projektu określa wszystko, co jest potrzebne do przywrócenia zależności i kompilacji programu.</span><span class="sxs-lookup"><span data-stu-id="ddd50-118">The project file specifies everything that's needed to restore dependencies and build the program.</span></span>

   * <span data-ttu-id="ddd50-119">`OutputType` Tag Określa, czy tworzymy plik wykonywalny, innymi słowy aplikację konsolową w języku.</span><span class="sxs-lookup"><span data-stu-id="ddd50-119">The `OutputType` tag specifies that we're building an executable, in other words a console application.</span></span>
   * <span data-ttu-id="ddd50-120">`TargetFramework` Tagów Określa, jakie firma Microsoft objęci implementacja programu .NET.</span><span class="sxs-lookup"><span data-stu-id="ddd50-120">The `TargetFramework` tag specifies what .NET implementation we're targeting.</span></span> <span data-ttu-id="ddd50-121">W zaawansowanym scenariuszu można określić wielu platform docelowych i kompilacja — przejście do wszystkich tych w ramach jednej operacji.</span><span class="sxs-lookup"><span data-stu-id="ddd50-121">In an advanced scenario, you can specify multiple target frameworks and build to all those in a single operation.</span></span> <span data-ttu-id="ddd50-122">W tym samouczku używany będzie tworzenie tylko dla platformy .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="ddd50-122">In this tutorial, we'll stick to building only for .NET Core 2.1.</span></span>

   <span data-ttu-id="ddd50-123">`Program.cs`:</span><span class="sxs-lookup"><span data-stu-id="ddd50-123">`Program.cs`:</span></span>

   [!code-csharp[Program.cs](../../../samples/core/console-apps/HelloMsBuild/Program.cs)]

   <span data-ttu-id="ddd50-124">Program, który rozpoczyna się od `using System`, co oznacza, że "Przenieś wszystko `System` przestrzeni nazw do zakresu dla tego pliku".</span><span class="sxs-lookup"><span data-stu-id="ddd50-124">The program starts by `using System`, which means "bring everything in the `System` namespace into scope for this file".</span></span> <span data-ttu-id="ddd50-125">`System` Przestrzeń nazw zawiera podstawowymi konstrukcjami `string`, lub typów liczbowych.</span><span class="sxs-lookup"><span data-stu-id="ddd50-125">The `System` namespace includes basic constructs such as `string`, or numeric types.</span></span>

   <span data-ttu-id="ddd50-126">Następnie definiujemy przestrzeń nazwy wywołaną `Hello`.</span><span class="sxs-lookup"><span data-stu-id="ddd50-126">We then define a namespace called `Hello`.</span></span> <span data-ttu-id="ddd50-127">Można to zmienić, do żadnego elementu, który ma.</span><span class="sxs-lookup"><span data-stu-id="ddd50-127">You can change this to anything you want.</span></span> <span data-ttu-id="ddd50-128">Klasa o nazwie `Program` jest zdefiniowana w ramach tej przestrzeni nazw za pomocą `Main` metody, która przyjmuje tablicę ciągów, jako argumentem.</span><span class="sxs-lookup"><span data-stu-id="ddd50-128">A class named `Program` is defined within that namespace, with a `Main` method that takes an array of strings as its argument.</span></span> <span data-ttu-id="ddd50-129">Ta tablica zawiera listę argumentów przekazywanych do wywołanego skompilowanego programu.</span><span class="sxs-lookup"><span data-stu-id="ddd50-129">This array contains the list of arguments passed in when the compiled program is called.</span></span> <span data-ttu-id="ddd50-130">I nie jest używana ta tablica: wszystkie działania programu służy do zapisania "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="ddd50-130">As it is, this array is not used: all the program is doing is to write "Hello World!"</span></span> <span data-ttu-id="ddd50-131">w konsoli.</span><span class="sxs-lookup"><span data-stu-id="ddd50-131">to the console.</span></span> <span data-ttu-id="ddd50-132">Później, wybierzemy zmiany do kodu, który będzie używać tego argumentu.</span><span class="sxs-lookup"><span data-stu-id="ddd50-132">Later, we'll make changes to the code that will make use of this argument.</span></span>

   [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

   <span data-ttu-id="ddd50-133">`dotnet new` wywołania [ `dotnet restore` ](../tools/dotnet-restore.md) niejawnie.</span><span class="sxs-lookup"><span data-stu-id="ddd50-133">`dotnet new` calls [`dotnet restore`](../tools/dotnet-restore.md) implicitly.</span></span> <span data-ttu-id="ddd50-134">`dotnet restore` wywoła [NuGet](https://www.nuget.org/) (.NET package manager) w celu przywrócenia drzewo zależności.</span><span class="sxs-lookup"><span data-stu-id="ddd50-134">`dotnet restore` calls into [NuGet](https://www.nuget.org/) (.NET package manager) to restore the tree of dependencies.</span></span> <span data-ttu-id="ddd50-135">Analizuje NuGet *Hello.csproj* plików, pliki do pobrania zależności zdefiniowane w pliku (lub bierze ich z pamięci podręcznej na komputerze) i zapisuje *obj/project.assets.json* pliku, który jest konieczny do Skompiluj i uruchom aplikację przykładową.</span><span class="sxs-lookup"><span data-stu-id="ddd50-135">NuGet analyzes the *Hello.csproj* file, downloads the dependencies defined in the file (or grabs them from a cache on your machine), and writes the *obj/project.assets.json* file, which is necessary to compile and run the sample.</span></span>

   > [!IMPORTANT]
   > <span data-ttu-id="ddd50-136">Jeśli używasz wersji 1.x platformy .NET Core SDK, musisz wywołać `dotnet restore` samodzielnie po wywołaniu `dotnet new`.</span><span class="sxs-lookup"><span data-stu-id="ddd50-136">If you're using a .NET Core 1.x version of the SDK, you'll have to call `dotnet restore` yourself after calling `dotnet new`.</span></span>

2. `dotnet run`

   <span data-ttu-id="ddd50-137">[`dotnet run`](../tools/dotnet-run.md) wywołania [ `dotnet build` ](../tools/dotnet-build.md) do upewnij się, że kompilacji, utworzone elementy docelowe, a następnie wywołania `dotnet <assembly.dll>` do uruchamiania aplikacji docelowej.</span><span class="sxs-lookup"><span data-stu-id="ddd50-137">[`dotnet run`](../tools/dotnet-run.md) calls [`dotnet build`](../tools/dotnet-build.md) to ensure that the build targets have been built, and then calls `dotnet <assembly.dll>` to run the target application.</span></span>

    ```console
    $ dotnet run
    Hello World!
    ```

    <span data-ttu-id="ddd50-138">Alternatywnie można również wykonać [ `dotnet build` ](../tools/dotnet-build.md) skompilować kod bez konieczności uruchamiania kompilacji aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="ddd50-138">Alternatively, you can also execute [`dotnet build`](../tools/dotnet-build.md) to compile the code without running the build console applications.</span></span> <span data-ttu-id="ddd50-139">Skutkuje to skompilowaną aplikację jako plik DLL, który można uruchomić z `dotnet bin\Debug\netcoreapp2.1\Hello.dll` na Windows (Użyj `/` systemów innych niż Windows).</span><span class="sxs-lookup"><span data-stu-id="ddd50-139">This results in a compiled application as a DLL file that can be run with `dotnet bin\Debug\netcoreapp2.1\Hello.dll` on Windows (use `/` for non-Windows systems).</span></span> <span data-ttu-id="ddd50-140">Jak zobaczysz później tematu można też określić argumenty do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ddd50-140">You may also specify arguments to the application as you'll see later on the topic.</span></span>

    ```console
    $ dotnet bin\Debug\netcoreapp2.1\Hello.dll
    Hello World!
    ```

    <span data-ttu-id="ddd50-141">W ramach scenariusza zaawansowanego jest możliwe utworzenie aplikacji jako autonomiczny zestaw plików specyficznych dla platformy, które można wdrożyć i uruchomić na komputerze, na którym nie musi koniecznie mieć platformy .NET Core zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="ddd50-141">As an advanced scenario, it's possible to build the application as a self-contained set of platform-specific files that can be deployed and run to a machine that doesn't necessarily have .NET Core installed.</span></span> <span data-ttu-id="ddd50-142">Zobacz [wdrożenie aplikacji programu .NET Core](../deploying/index.md) Aby uzyskać szczegółowe informacje.</span><span class="sxs-lookup"><span data-stu-id="ddd50-142">See [.NET Core Application Deployment](../deploying/index.md) for details.</span></span>

### <a name="augmenting-the-program"></a><span data-ttu-id="ddd50-143">Rozszerzając program</span><span class="sxs-lookup"><span data-stu-id="ddd50-143">Augmenting the program</span></span>

<span data-ttu-id="ddd50-144">Zmieńmy nieco program.</span><span class="sxs-lookup"><span data-stu-id="ddd50-144">Let's change the program a bit.</span></span> <span data-ttu-id="ddd50-145">Numery Fibonacci zabawy, Dodajmy oprócz Użyj argumentu w celu powitania osoby uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ddd50-145">Fibonacci numbers are fun, so let's add that in addition to use the argument to greet the person running the app.</span></span>

1. <span data-ttu-id="ddd50-146">Zastąp zawartość swojej *Program.cs* pliku następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="ddd50-146">Replace the contents of your *Program.cs*  file with the following code:</span></span>

   [!code-csharp[Fibonacci](../../../samples/core/console-apps/fibonacci-msbuild/Program.cs)]

2. <span data-ttu-id="ddd50-147">Wykonaj [ `dotnet build` ](../tools/dotnet-build.md) skompilować zmiany.</span><span class="sxs-lookup"><span data-stu-id="ddd50-147">Execute [`dotnet build`](../tools/dotnet-build.md) to compile the changes.</span></span>

3. <span data-ttu-id="ddd50-148">Uruchom program przekazywania parametru do aplikacji:</span><span class="sxs-lookup"><span data-stu-id="ddd50-148">Run the program passing a parameter to the app:</span></span>

   ```console
   $ dotnet run -- John
   Hello John!
   Fibonacci Numbers 1-15:
   1: 0
   2: 1
   3: 1
   4: 2
   5: 3
   6: 5
   7: 8
   8: 13
   9: 21
   10: 34
   11: 55
   12: 89
   13: 144
   14: 233
   15: 377
   ```

<span data-ttu-id="ddd50-149">I to wszystko!</span><span class="sxs-lookup"><span data-stu-id="ddd50-149">And that's it!</span></span>  <span data-ttu-id="ddd50-150">Można rozszerzyć `Program.cs` sposób chcesz.</span><span class="sxs-lookup"><span data-stu-id="ddd50-150">You can augment `Program.cs` any way you like.</span></span>

## <a name="working-with-multiple-files"></a><span data-ttu-id="ddd50-151">Praca z wieloma plikami</span><span class="sxs-lookup"><span data-stu-id="ddd50-151">Working with multiple files</span></span>

<span data-ttu-id="ddd50-152">Pojedynczych plików są w dobrym stanie, proste, jednorazowe programów, ale jeśli tworzysz bardziej złożonych aplikacji prawdopodobnie będziemy mieć wiele plików źródłowych w projekcie.</span><span class="sxs-lookup"><span data-stu-id="ddd50-152">Single files are fine for simple one-off programs, but if you're building a more complex app, you're probably going to have multiple source files on your project.</span></span>
<span data-ttu-id="ddd50-153">Umożliwia tworzenie na podstawie poprzedniego przykładu Fibonacci przez buforowanie niektórych wartości Fibonacci i dodać niektóre funkcje cykliczne.</span><span class="sxs-lookup"><span data-stu-id="ddd50-153">Let's build off of the previous Fibonacci example by caching some Fibonacci values and add some recursive features.</span></span>

1. <span data-ttu-id="ddd50-154">Dodaj nowy plik wewnątrz *Hello* katalog o nazwie *FibonacciGenerator.cs* następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="ddd50-154">Add a new file inside the *Hello* directory named *FibonacciGenerator.cs* with the following code:</span></span>

   [!code-csharp[Fibonacci Generator](../../../samples/core/console-apps/FibonacciBetterMsBuild/FibonacciGenerator.cs)]

2. <span data-ttu-id="ddd50-155">Zmiana `Main` method in Class metoda swoje *Program.cs* plik, aby utworzyć nowe wystąpienie klasy i wywołać jej metodę jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="ddd50-155">Change the `Main` method in your *Program.cs* file to instantiate the new class and call its method as in the following example:</span></span>

   [!code-csharp[New Program.cs](../../../samples/core/console-apps/FibonacciBetterMsBuild/Program.cs)]

3. <span data-ttu-id="ddd50-156">Wykonaj [ `dotnet build` ](../tools/dotnet-build.md) skompilować zmiany.</span><span class="sxs-lookup"><span data-stu-id="ddd50-156">Execute [`dotnet build`](../tools/dotnet-build.md) to compile the changes.</span></span>

4. <span data-ttu-id="ddd50-157">Uruchom aplikację, wykonując [ `dotnet run` ](../tools/dotnet-run.md).</span><span class="sxs-lookup"><span data-stu-id="ddd50-157">Run your app by executing [`dotnet run`](../tools/dotnet-run.md).</span></span> <span data-ttu-id="ddd50-158">Poniżej przedstawiono dane wyjściowe programu:</span><span class="sxs-lookup"><span data-stu-id="ddd50-158">The following shows the program output:</span></span>

   ```console
   $ dotnet run
   0
   1
   1
   2
   3
   5
   8
   13
   21
   34
   55
   89
   144
   233
   377
   ```

<span data-ttu-id="ddd50-159">I to wszystko!</span><span class="sxs-lookup"><span data-stu-id="ddd50-159">And that's it!</span></span> <span data-ttu-id="ddd50-160">Teraz można uruchomić przy użyciu podstawowych pojęć w tym miejscu przedstawiono tworzenie własnych programów.</span><span class="sxs-lookup"><span data-stu-id="ddd50-160">Now, you can start using the basic concepts learned here to create your own programs.</span></span>

<span data-ttu-id="ddd50-161">Należy pamiętać, że polecenia i kroki opisane w tym samouczku do uruchamiania aplikacji są używane tylko w czasie projektowania.</span><span class="sxs-lookup"><span data-stu-id="ddd50-161">Note that the commands and steps shown in this tutorial to run your application are used during development time only.</span></span> <span data-ttu-id="ddd50-162">Gdy wszystko będzie gotowe do wdrożenia aplikacji, należy spojrzeć na poszczególne [strategie wdrażania](../deploying/index.md) dla aplikacji platformy .NET Core i [ `dotnet publish` ](../tools/dotnet-publish.md) polecenia.</span><span class="sxs-lookup"><span data-stu-id="ddd50-162">Once you're ready to deploy your app, you'll want to take a look at the different [deployment strategies](../deploying/index.md) for .NET Core apps and the [`dotnet publish`](../tools/dotnet-publish.md) command.</span></span>

## <a name="see-also"></a><span data-ttu-id="ddd50-163">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ddd50-163">See also</span></span>

- [<span data-ttu-id="ddd50-164">Organizowanie i testowanie projektów przy użyciu narzędzi interfejsu wiersza polecenia platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="ddd50-164">Organizing and testing projects with the .NET Core CLI tools</span></span>](testing-with-cli.md)

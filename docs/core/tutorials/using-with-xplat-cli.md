---
title: Rozpoczynanie pracy z platformą .NET Core przy użyciu interfejsu wiersza polecenia
description: Samouczek krok po kroku pokazujący, jak rozpocząć pracę z platformą .NET Core w systemie Windows, Linux lub macOS przy użyciu interfejsu wiersza polecenia (CLI) platformy .NET Core.
author: thraka
ms.author: adegeo
ms.date: 08/07/2019
ms.technology: dotnet-cli
ms.custom: seodec18
ms.openlocfilehash: b5ef70967c8404dc5ce5b816bb9a1c3b1d7e4230
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117349"
---
# <a name="get-started-with-net-core-on-windowslinuxmacos-using-the-command-line"></a><span data-ttu-id="8d40c-103">Rozpoczynanie pracy z platformą .NET Core w systemie Windows/Linux/macOS przy użyciu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="8d40c-103">Get started with .NET Core on Windows/Linux/macOS using the command line</span></span>

<span data-ttu-id="8d40c-104">W tym temacie pokazano, jak rozpocząć tworzenie aplikacji dla wielu platform na maszynie przy użyciu narzędzi interfejs wiersza polecenia platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8d40c-104">This topic will show you how to start developing cross-platforms apps in your machine using the .NET Core CLI tools.</span></span>

<span data-ttu-id="8d40c-105">Jeśli nie znasz zestawu narzędzi interfejs wiersza polecenia platformy .NET Core, zapoznaj się z tematem [zestaw .NET Core SDK Omówienie](../tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="8d40c-105">If you're unfamiliar with the .NET Core CLI toolset, read the [.NET Core SDK overview](../tools/index.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8d40c-106">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="8d40c-106">Prerequisites</span></span>

- <span data-ttu-id="8d40c-107">[Zestaw .NET Core SDK 2,1](https://dotnet.microsoft.com/download) lub nowszymi wersjami.</span><span class="sxs-lookup"><span data-stu-id="8d40c-107">[.NET Core SDK 2.1](https://dotnet.microsoft.com/download) or later versions.</span></span>
- <span data-ttu-id="8d40c-108">Edytor tekstu lub Edytor kodu.</span><span class="sxs-lookup"><span data-stu-id="8d40c-108">A text editor or code editor of your choice.</span></span>

## <a name="hello-console-app"></a><span data-ttu-id="8d40c-109">Witaj, Aplikacja konsolowa!</span><span class="sxs-lookup"><span data-stu-id="8d40c-109">Hello, Console App!</span></span>

<span data-ttu-id="8d40c-110">[Przykładowy kod można wyświetlić lub pobrać](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) z repozytorium usługi GitHub/przykłady</span><span class="sxs-lookup"><span data-stu-id="8d40c-110">You can [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) from the dotnet/samples GitHub repository.</span></span> <span data-ttu-id="8d40c-111">Aby uzyskać instrukcje dotyczące pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="8d40c-111">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="8d40c-112">Otwórz wiersz polecenia i Utwórz folder o nazwie *Hello*.</span><span class="sxs-lookup"><span data-stu-id="8d40c-112">Open a command prompt and create a folder named *Hello*.</span></span> <span data-ttu-id="8d40c-113">Przejdź do utworzonego folderu i wpisz następujące:</span><span class="sxs-lookup"><span data-stu-id="8d40c-113">Navigate to the folder you created and type the following:</span></span>

```dotnetcli
dotnet new console
dotnet run
```

<span data-ttu-id="8d40c-114">Wykonajmy szybkie wskazówki:</span><span class="sxs-lookup"><span data-stu-id="8d40c-114">Let's do a quick walkthrough:</span></span>

1. `dotnet new console`

   <span data-ttu-id="8d40c-115">[`dotnet new`](../tools/dotnet-new.md)tworzy aktualny `Hello.csproj` plik projektu z zależnościami niezbędnymi do skompilowania aplikacji konsolowej.</span><span class="sxs-lookup"><span data-stu-id="8d40c-115">[`dotnet new`](../tools/dotnet-new.md) creates an up-to-date `Hello.csproj` project file with the dependencies necessary to build a console app.</span></span>  <span data-ttu-id="8d40c-116">Tworzy `Program.cs`również plik podstawowy zawierający punkt wejścia dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8d40c-116">It also creates a `Program.cs`, a basic file containing the entry point for the application.</span></span>

   <span data-ttu-id="8d40c-117">`Hello.csproj`:</span><span class="sxs-lookup"><span data-stu-id="8d40c-117">`Hello.csproj`:</span></span>

   [!code[Hello.csproj](../../../samples/core/console-apps/HelloMsBuild/Hello.csproj)]

   <span data-ttu-id="8d40c-118">Plik projektu określa wszystko, co jest potrzebne do przywrócenia zależności i skompilowania programu.</span><span class="sxs-lookup"><span data-stu-id="8d40c-118">The project file specifies everything that's needed to restore dependencies and build the program.</span></span>

   - <span data-ttu-id="8d40c-119">`OutputType` Tag określa, że tworzysz plik wykonywalny, innymi słowy, Aplikacja konsolowa.</span><span class="sxs-lookup"><span data-stu-id="8d40c-119">The `OutputType` tag specifies that we're building an executable, in other words a console application.</span></span>
   - <span data-ttu-id="8d40c-120">Tag `TargetFramework` określa, która implementacja platformy .NET jest docelowa.</span><span class="sxs-lookup"><span data-stu-id="8d40c-120">The `TargetFramework` tag specifies what .NET implementation we're targeting.</span></span> <span data-ttu-id="8d40c-121">W zaawansowanym scenariuszu można określić wiele platform docelowych i skompilować je do wszystkich w ramach jednej operacji.</span><span class="sxs-lookup"><span data-stu-id="8d40c-121">In an advanced scenario, you can specify multiple target frameworks and build to all those in a single operation.</span></span> <span data-ttu-id="8d40c-122">W tym samouczku dojdziemy do kompilowania tylko dla platformy .NET Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="8d40c-122">In this tutorial, we'll stick to building only for .NET Core 2.1.</span></span>

   <span data-ttu-id="8d40c-123">`Program.cs`:</span><span class="sxs-lookup"><span data-stu-id="8d40c-123">`Program.cs`:</span></span>

   [!code-csharp[Program.cs](../../../samples/core/console-apps/HelloMsBuild/Program.cs)]

   <span data-ttu-id="8d40c-124">Program jest uruchamiany przez `using System`, co oznacza, że `System` w zakresie tego pliku można przenieść wszystkie elementy w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="8d40c-124">The program starts by `using System`, which means "bring everything in the `System` namespace into scope for this file".</span></span> <span data-ttu-id="8d40c-125">Przestrzeń nazw zawiera podstawowe konstrukcje, takie `string`jak, lub typy liczbowe. `System`</span><span class="sxs-lookup"><span data-stu-id="8d40c-125">The `System` namespace includes basic constructs such as `string`, or numeric types.</span></span>

   <span data-ttu-id="8d40c-126">Następnie zdefiniujemy przestrzeń nazw o `Hello`nazwie.</span><span class="sxs-lookup"><span data-stu-id="8d40c-126">We then define a namespace called `Hello`.</span></span> <span data-ttu-id="8d40c-127">Możesz to zmienić w dowolny sposób.</span><span class="sxs-lookup"><span data-stu-id="8d40c-127">You can change this to anything you want.</span></span> <span data-ttu-id="8d40c-128">Klasa o nazwie `Program` jest zdefiniowana w tej przestrzeni nazw, `Main` z metodą, która pobiera tablicę ciągów jako argument.</span><span class="sxs-lookup"><span data-stu-id="8d40c-128">A class named `Program` is defined within that namespace, with a `Main` method that takes an array of strings as its argument.</span></span> <span data-ttu-id="8d40c-129">Ta tablica zawiera listę argumentów, które zostały przekazane podczas wywoływania skompilowanego programu.</span><span class="sxs-lookup"><span data-stu-id="8d40c-129">This array contains the list of arguments passed in when the compiled program is called.</span></span> <span data-ttu-id="8d40c-130">W takim przypadku ta tablica nie jest używana: cały program wykonuje zapis "Hello world!"</span><span class="sxs-lookup"><span data-stu-id="8d40c-130">As it is, this array is not used: all the program is doing is to write "Hello World!"</span></span> <span data-ttu-id="8d40c-131">do konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="8d40c-131">to the console.</span></span> <span data-ttu-id="8d40c-132">Później wprowadzimy zmiany w kodzie, który będzie korzystał z tego argumentu.</span><span class="sxs-lookup"><span data-stu-id="8d40c-132">Later, we'll make changes to the code that will make use of this argument.</span></span>

   [!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

   <span data-ttu-id="8d40c-133">`dotnet new`wywołania [`dotnet restore`](../tools/dotnet-restore.md) niejawnie.</span><span class="sxs-lookup"><span data-stu-id="8d40c-133">`dotnet new` calls [`dotnet restore`](../tools/dotnet-restore.md) implicitly.</span></span> <span data-ttu-id="8d40c-134">`dotnet restore`wywołuje pakiet [NuGet](https://www.nuget.org/) (Menedżer pakietów .NET) w celu przywrócenia drzewa zależności.</span><span class="sxs-lookup"><span data-stu-id="8d40c-134">`dotnet restore` calls into [NuGet](https://www.nuget.org/) (.NET package manager) to restore the tree of dependencies.</span></span> <span data-ttu-id="8d40c-135">Pakiet NuGet analizuje plik *Hello. csproj* , pobiera zależności zdefiniowane w pliku (lub zbiera je z pamięci podręcznej na maszynie) i zapisuje plik *obj/Project. assets. JSON* , który jest niezbędny do skompilowania i uruchomienia przykładu.</span><span class="sxs-lookup"><span data-stu-id="8d40c-135">NuGet analyzes the *Hello.csproj* file, downloads the dependencies defined in the file (or grabs them from a cache on your machine), and writes the *obj/project.assets.json* file, which is necessary to compile and run the sample.</span></span>

   > [!IMPORTANT]
   > <span data-ttu-id="8d40c-136">Jeśli używasz wersji programu .NET Core 1. x zestawu SDK, musisz wywołać `dotnet restore` siebie po wywołaniu. `dotnet new`</span><span class="sxs-lookup"><span data-stu-id="8d40c-136">If you're using a .NET Core 1.x version of the SDK, you'll have to call `dotnet restore` yourself after calling `dotnet new`.</span></span>

2. `dotnet run`

   <span data-ttu-id="8d40c-137">[`dotnet run`](../tools/dotnet-run.md)wywołuje [`dotnet build`](../tools/dotnet-build.md) się, by upewnić się, że cele kompilacji zostały skompilowane `dotnet <assembly.dll>` , a następnie wywołuje, aby uruchomić aplikację docelową.</span><span class="sxs-lookup"><span data-stu-id="8d40c-137">[`dotnet run`](../tools/dotnet-run.md) calls [`dotnet build`](../tools/dotnet-build.md) to ensure that the build targets have been built, and then calls `dotnet <assembly.dll>` to run the target application.</span></span>

    ```console
    $ dotnet run
    Hello World!
    ```

    <span data-ttu-id="8d40c-138">Alternatywnie można również wykonać [`dotnet build`](../tools/dotnet-build.md) polecenie, aby skompilować kod bez uruchamiania aplikacji konsolowej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="8d40c-138">Alternatively, you can also execute [`dotnet build`](../tools/dotnet-build.md) to compile the code without running the build console applications.</span></span> <span data-ttu-id="8d40c-139">Powoduje to skompilowaną aplikację jako plik dll, który można uruchomić za pomocą `dotnet bin\Debug\netcoreapp2.1\Hello.dll` systemu Windows `/` (w przypadku systemów innych niż Windows).</span><span class="sxs-lookup"><span data-stu-id="8d40c-139">This results in a compiled application as a DLL file that can be run with `dotnet bin\Debug\netcoreapp2.1\Hello.dll` on Windows (use `/` for non-Windows systems).</span></span> <span data-ttu-id="8d40c-140">Możesz również określić argumenty dla aplikacji, jak widać w dalszej części tematu.</span><span class="sxs-lookup"><span data-stu-id="8d40c-140">You may also specify arguments to the application as you'll see later on the topic.</span></span>

    ```console
    $ dotnet bin\Debug\netcoreapp2.1\Hello.dll
    Hello World!
    ```

    <span data-ttu-id="8d40c-141">Zaawansowanym scenariuszem jest możliwość tworzenia aplikacji jako samodzielnego zestawu plików specyficznych dla platformy, które można wdrożyć i uruchomić na komputerze, na którym nie jest zainstalowany program .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8d40c-141">As an advanced scenario, it's possible to build the application as a self-contained set of platform-specific files that can be deployed and run to a machine that doesn't necessarily have .NET Core installed.</span></span> <span data-ttu-id="8d40c-142">Aby uzyskać szczegółowe informacje, zobacz [wdrażanie aplikacji .NET Core](../deploying/index.md) .</span><span class="sxs-lookup"><span data-stu-id="8d40c-142">See [.NET Core Application Deployment](../deploying/index.md) for details.</span></span>

### <a name="augmenting-the-program"></a><span data-ttu-id="8d40c-143">Rozszerzanie programu</span><span class="sxs-lookup"><span data-stu-id="8d40c-143">Augmenting the program</span></span>

<span data-ttu-id="8d40c-144">Zmieńmy program na bit.</span><span class="sxs-lookup"><span data-stu-id="8d40c-144">Let's change the program a bit.</span></span> <span data-ttu-id="8d40c-145">Liczby Fibonacci są przyjemne, więc Dodajmy ten dodatek, a także użyjesz argumentu, aby powitać osobę, która uruchamia aplikację.</span><span class="sxs-lookup"><span data-stu-id="8d40c-145">Fibonacci numbers are fun, so let's add that in addition to use the argument to greet the person running the app.</span></span>

1. <span data-ttu-id="8d40c-146">Zastąp zawartość pliku *program.cs* następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="8d40c-146">Replace the contents of your *Program.cs*  file with the following code:</span></span>

   [!code-csharp[Fibonacci](../../../samples/core/console-apps/fibonacci-msbuild/Program.cs)]

2. <span data-ttu-id="8d40c-147">Wykonaj [`dotnet build`](../tools/dotnet-build.md) , aby skompilować zmiany.</span><span class="sxs-lookup"><span data-stu-id="8d40c-147">Execute [`dotnet build`](../tools/dotnet-build.md) to compile the changes.</span></span>

3. <span data-ttu-id="8d40c-148">Uruchom program, przekazując do aplikacji parametr:</span><span class="sxs-lookup"><span data-stu-id="8d40c-148">Run the program passing a parameter to the app:</span></span>

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

<span data-ttu-id="8d40c-149">I to wszystko!</span><span class="sxs-lookup"><span data-stu-id="8d40c-149">And that's it!</span></span>  <span data-ttu-id="8d40c-150">Można to zrobić `Program.cs` w dowolny sposób.</span><span class="sxs-lookup"><span data-stu-id="8d40c-150">You can augment `Program.cs` any way you like.</span></span>

## <a name="working-with-multiple-files"></a><span data-ttu-id="8d40c-151">Praca z wieloma plikami</span><span class="sxs-lookup"><span data-stu-id="8d40c-151">Working with multiple files</span></span>

<span data-ttu-id="8d40c-152">Pojedyncze pliki są ograniczone do prostych programów jednostronnych, ale jeśli tworzysz bardziej złożoną aplikację, prawdopodobnie będziesz mieć wiele plików źródłowych w projekcie.</span><span class="sxs-lookup"><span data-stu-id="8d40c-152">Single files are fine for simple one-off programs, but if you're building a more complex app, you're probably going to have multiple source files on your project.</span></span>
<span data-ttu-id="8d40c-153">Utwórzmy od poprzedniego przykładu Fibonacci przez buforowanie niektórych wartości Fibonacci i dodanie niektórych funkcji cyklicznych.</span><span class="sxs-lookup"><span data-stu-id="8d40c-153">Let's build off of the previous Fibonacci example by caching some Fibonacci values and add some recursive features.</span></span>

1. <span data-ttu-id="8d40c-154">Dodaj nowy plik w katalogu *Hello* o nazwie *FibonacciGenerator.cs* przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="8d40c-154">Add a new file inside the *Hello* directory named *FibonacciGenerator.cs* with the following code:</span></span>

   [!code-csharp[Fibonacci Generator](../../../samples/core/console-apps/FibonacciBetterMsBuild/FibonacciGenerator.cs)]

2. <span data-ttu-id="8d40c-155">Zmień metodę w pliku program.cs, aby utworzyć wystąpienie nowej klasy i wywołać jej metodę tak jak w poniższym przykładzie: `Main`</span><span class="sxs-lookup"><span data-stu-id="8d40c-155">Change the `Main` method in your *Program.cs* file to instantiate the new class and call its method as in the following example:</span></span>

   [!code-csharp[New Program.cs](../../../samples/core/console-apps/FibonacciBetterMsBuild/Program.cs)]

3. <span data-ttu-id="8d40c-156">Wykonaj [`dotnet build`](../tools/dotnet-build.md) , aby skompilować zmiany.</span><span class="sxs-lookup"><span data-stu-id="8d40c-156">Execute [`dotnet build`](../tools/dotnet-build.md) to compile the changes.</span></span>

4. <span data-ttu-id="8d40c-157">Uruchom aplikację, wykonując [`dotnet run`](../tools/dotnet-run.md).</span><span class="sxs-lookup"><span data-stu-id="8d40c-157">Run your app by executing [`dotnet run`](../tools/dotnet-run.md).</span></span> <span data-ttu-id="8d40c-158">Poniżej przedstawiono dane wyjściowe programu:</span><span class="sxs-lookup"><span data-stu-id="8d40c-158">The following shows the program output:</span></span>

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

## <a name="publish-your-app"></a><span data-ttu-id="8d40c-159">Publikowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="8d40c-159">Publish your app</span></span>

<span data-ttu-id="8d40c-160">Gdy wszystko będzie gotowe do dystrybucji swojej aplikacji, użyj [`dotnet publish`](../tools/dotnet-publish.md) polecenia w celu wygenerowania folderu _publikowania_ w polu Debuguj debugowanie `/` _\\\\w\\usłudze\\ bin netcoreapp 2.1_ (Użyj dla Systemy inne niż Windows).</span><span class="sxs-lookup"><span data-stu-id="8d40c-160">Once you're ready to distribute your app, use the [`dotnet publish`](../tools/dotnet-publish.md) command to generate the _publish_ folder at _bin\\debug\\netcoreapp2.1\\publish\\_ (use `/` for non-Windows systems).</span></span> <span data-ttu-id="8d40c-161">Zawartość folderu _publikowania_ można dystrybuować na inne platformy, o ile już zainstalowano środowisko uruchomieniowe dotnet.</span><span class="sxs-lookup"><span data-stu-id="8d40c-161">You can distribute the contents of the _publish_ folder to other platforms as long as they've already installed the dotnet runtime.</span></span>

<span data-ttu-id="8d40c-162">Opublikowaną aplikację można uruchomić za pomocą polecenia [dotnet](../tools/dotnet.md) :</span><span class="sxs-lookup"><span data-stu-id="8d40c-162">You can run your published app with the [dotnet](../tools/dotnet.md) command:</span></span>

```console
$ dotnet bin\Debug\netcoreapp2.1\publish\Hello.dll
Hello World!
```

## <a name="conclusion"></a><span data-ttu-id="8d40c-163">Wniosek</span><span class="sxs-lookup"><span data-stu-id="8d40c-163">Conclusion</span></span>

<span data-ttu-id="8d40c-164">I to wszystko!</span><span class="sxs-lookup"><span data-stu-id="8d40c-164">And that's it!</span></span> <span data-ttu-id="8d40c-165">Teraz możesz zacząć korzystać z podstawowych pojęć zamieszczonych w tym miejscu, aby utworzyć własne programy.</span><span class="sxs-lookup"><span data-stu-id="8d40c-165">Now, you can start using the basic concepts learned here to create your own programs.</span></span>

## <a name="see-also"></a><span data-ttu-id="8d40c-166">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8d40c-166">See also</span></span>

- [<span data-ttu-id="8d40c-167">Organizowanie i testowanie projektów przy użyciu narzędzi interfejs wiersza polecenia platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="8d40c-167">Organizing and testing projects with the .NET Core CLI tools</span></span>](testing-with-cli.md)
- [<span data-ttu-id="8d40c-168">Publikowanie aplikacji platformy .NET Core za pomocą interfejsu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="8d40c-168">Publish .NET Core apps with the CLI</span></span>](../deploying/deploy-with-cli.md)
- [<span data-ttu-id="8d40c-169">Dowiedz się więcej o wdrażaniu aplikacji</span><span class="sxs-lookup"><span data-stu-id="8d40c-169">Learn more about app deployment</span></span>](../deploying/index.md)

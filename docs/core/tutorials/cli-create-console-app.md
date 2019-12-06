---
title: Rozpoczynanie pracy z platformą .NET Core przy użyciu interfejsu wiersza polecenia interfejs wiersza polecenia platformy .NET Core
description: Samouczek krok po kroku pokazujący, jak rozpocząć pracę z platformą .NET Core w systemie Windows, Linux lub macOS przy użyciu interfejsu wiersza polecenia (CLI) platformy .NET Core.
author: thraka
ms.author: adegeo
ms.date: 12/05/2019
ms.technology: dotnet-cli
ms.custom: seodec18,updateeachrelease
ms.openlocfilehash: 4c6a8e495d8532a0ab2e90368663a287731a9af0
ms.sourcegitcommit: 68a4b28242da50e1d25aab597c632767713a6f81
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/06/2019
ms.locfileid: "74884278"
---
# <a name="get-started-with-net-core-on-windowslinuxmacos-using-the-command-line"></a><span data-ttu-id="2150c-103">Rozpoczynanie pracy z platformą .NET Core w systemie Windows/Linux/macOS przy użyciu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="2150c-103">Get started with .NET Core on Windows/Linux/macOS using the command line</span></span>

<span data-ttu-id="2150c-104">W tym artykule pokazano, jak rozpocząć tworzenie aplikacji dla wielu platform na maszynie przy użyciu narzędzi interfejs wiersza polecenia platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2150c-104">This article will show you how to start developing cross-platforms apps in your machine using the .NET Core CLI tools.</span></span>

<span data-ttu-id="2150c-105">Jeśli nie znasz zestawu narzędzi interfejs wiersza polecenia platformy .NET Core, zapoznaj się z tematem [zestaw .NET Core SDK Omówienie](../tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="2150c-105">If you're unfamiliar with the .NET Core CLI toolset, read the [.NET Core SDK overview](../tools/index.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="2150c-106">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="2150c-106">Prerequisites</span></span>

- <span data-ttu-id="2150c-107">[Zestaw .NET Core SDK 3,1](https://dotnet.microsoft.com/download) lub nowszymi wersjami.</span><span class="sxs-lookup"><span data-stu-id="2150c-107">[.NET Core SDK 3.1](https://dotnet.microsoft.com/download) or later versions.</span></span>
- <span data-ttu-id="2150c-108">Wybrany edytor tekstu lub edytor kodu.</span><span class="sxs-lookup"><span data-stu-id="2150c-108">A text editor or code editor of your choice.</span></span>

## <a name="hello-console-app"></a><span data-ttu-id="2150c-109">Witaj, Aplikacja konsolowa!</span><span class="sxs-lookup"><span data-stu-id="2150c-109">Hello, Console App!</span></span>

<span data-ttu-id="2150c-110">[Przykładowy kod można wyświetlić lub pobrać](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) z repozytorium usługi GitHub/przykłady</span><span class="sxs-lookup"><span data-stu-id="2150c-110">You can [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) from the dotnet/samples GitHub repository.</span></span> <span data-ttu-id="2150c-111">Aby uzyskać instrukcje dotyczące pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="2150c-111">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="2150c-112">Otwórz wiersz polecenia i Utwórz folder o nazwie *Hello*.</span><span class="sxs-lookup"><span data-stu-id="2150c-112">Open a command prompt and create a folder named *Hello*.</span></span> <span data-ttu-id="2150c-113">Przejdź do utworzonego folderu i wpisz następujące:</span><span class="sxs-lookup"><span data-stu-id="2150c-113">Navigate to the folder you created and type the following:</span></span>

```dotnetcli
dotnet new console
dotnet run
```

<span data-ttu-id="2150c-114">Wykonajmy szybkie wskazówki:</span><span class="sxs-lookup"><span data-stu-id="2150c-114">Let's do a quick walkthrough:</span></span>

01. `dotnet new console`

    <span data-ttu-id="2150c-115">Program [dotnet New](../tools/dotnet-new.md) tworzy aktualny plik projektu *Hello. csproj* z zależnościami niezbędnymi do skompilowania aplikacji konsolowej.</span><span class="sxs-lookup"><span data-stu-id="2150c-115">[dotnet new](../tools/dotnet-new.md) creates an up-to-date *Hello.csproj* project file with the dependencies necessary to build a console app.</span></span> <span data-ttu-id="2150c-116">Tworzy również *program.cs*, podstawowy plik zawierający punkt wejścia dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2150c-116">It also creates a *Program.cs*, a basic file containing the entry point for the application.</span></span>
    
    <span data-ttu-id="2150c-117">*Witaj. csproj*:</span><span class="sxs-lookup"><span data-stu-id="2150c-117">*Hello.csproj*:</span></span>
    
    [!code-xml[Hello.csproj](~/samples/core/console-apps/HelloMsBuild/Hello.csproj)]
    
    <span data-ttu-id="2150c-118">Plik projektu określa wszystko, co jest potrzebne do przywrócenia zależności i skompilowania programu.</span><span class="sxs-lookup"><span data-stu-id="2150c-118">The project file specifies everything that's needed to restore dependencies and build the program.</span></span>
    
    - <span data-ttu-id="2150c-119">`<OutputType>` element określa, że tworzysz plik wykonywalny, innymi słowy, Aplikacja konsolowa.</span><span class="sxs-lookup"><span data-stu-id="2150c-119">The `<OutputType>` element specifies that we're building an executable, in other words a console application.</span></span>
    - <span data-ttu-id="2150c-120">`<TargetFramework>` element określa, która implementacja platformy .NET jest celem.</span><span class="sxs-lookup"><span data-stu-id="2150c-120">The `<TargetFramework>` element specifies what .NET implementation we're targeting.</span></span> <span data-ttu-id="2150c-121">W zaawansowanym scenariuszu można określić wiele platform docelowych i skompilować je do wszystkich w ramach jednej operacji.</span><span class="sxs-lookup"><span data-stu-id="2150c-121">In an advanced scenario, you can specify multiple target frameworks and build to all those in a single operation.</span></span> <span data-ttu-id="2150c-122">W tym samouczku dojdziemy do kompilowania tylko dla platformy .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="2150c-122">In this tutorial, we'll stick to building only for .NET Core 3.1.</span></span>
    
    <span data-ttu-id="2150c-123">*Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="2150c-123">*Program.cs*:</span></span>
    
    [!code-csharp[Program.cs](~/samples/core/console-apps/HelloMsBuild/Program.cs)]
    
    <span data-ttu-id="2150c-124">Program jest uruchamiany przez `using System`, co oznacza, że w zakresie dla tego pliku można przenieść wszystko w przestrzeni nazw `System`.</span><span class="sxs-lookup"><span data-stu-id="2150c-124">The program starts by `using System`, which means "bring everything in the `System` namespace into scope for this file".</span></span> <span data-ttu-id="2150c-125">Przestrzeń nazw `System` zawiera klasę `Console`.</span><span class="sxs-lookup"><span data-stu-id="2150c-125">The `System` namespace includes the `Console` class.</span></span>
    
    <span data-ttu-id="2150c-126">Następnie zdefiniujemy przestrzeń nazw o nazwie `Hello`.</span><span class="sxs-lookup"><span data-stu-id="2150c-126">We then define a namespace called `Hello`.</span></span> <span data-ttu-id="2150c-127">Możesz to zmienić w dowolny sposób.</span><span class="sxs-lookup"><span data-stu-id="2150c-127">You can change this to anything you want.</span></span> <span data-ttu-id="2150c-128">Klasa o nazwie `Program` jest zdefiniowana w tej przestrzeni nazw, z metodą `Main`, która pobiera tablicę ciągów o nazwie `args`.</span><span class="sxs-lookup"><span data-stu-id="2150c-128">A class named `Program` is defined within that namespace, with a `Main` method that takes an array of strings named `args`.</span></span> <span data-ttu-id="2150c-129">Ta tablica zawiera listę argumentów przekazaną podczas uruchamiania programu.</span><span class="sxs-lookup"><span data-stu-id="2150c-129">This array contains the list of arguments passed in when the program is run.</span></span> <span data-ttu-id="2150c-130">W takim przypadku tablica nie jest używana, a program po prostu zapisuje tekst "Hello world!"</span><span class="sxs-lookup"><span data-stu-id="2150c-130">As it is, this array is not used and the program simply writes the text "Hello World!"</span></span> <span data-ttu-id="2150c-131">w konsoli.</span><span class="sxs-lookup"><span data-stu-id="2150c-131">to the console.</span></span> <span data-ttu-id="2150c-132">Później wprowadzimy zmiany w kodzie, który będzie korzystał z tego argumentu.</span><span class="sxs-lookup"><span data-stu-id="2150c-132">Later, we'll make changes to the code that will make use of this argument.</span></span>
    
    <span data-ttu-id="2150c-133">wywołania `dotnet new` [dotnet Restore](../tools/dotnet-restore.md) niejawnie.</span><span class="sxs-lookup"><span data-stu-id="2150c-133">`dotnet new` calls [dotnet restore](../tools/dotnet-restore.md) implicitly.</span></span> <span data-ttu-id="2150c-134">`dotnet restore` wywołania [NuGet](https://www.nuget.org/) (Menedżer pakietów .NET) w celu przywrócenia drzewa zależności.</span><span class="sxs-lookup"><span data-stu-id="2150c-134">`dotnet restore` calls into [NuGet](https://www.nuget.org/) (.NET package manager) to restore the tree of dependencies.</span></span> <span data-ttu-id="2150c-135">Pakiet NuGet analizuje plik *Hello. csproj* , pobiera zależności zdefiniowane w pliku (lub zbiera je z pamięci podręcznej na maszynie) i zapisuje plik *obj/Project. assets. JSON* , który jest niezbędny do skompilowania i uruchomienia przykładu.</span><span class="sxs-lookup"><span data-stu-id="2150c-135">NuGet analyzes the *Hello.csproj* file, downloads the dependencies defined in the file (or grabs them from a cache on your machine), and writes the *obj/project.assets.json* file, which is necessary to compile and run the sample.</span></span>

02. `dotnet run`

    <span data-ttu-id="2150c-136">[uruchomienia](../tools/dotnet-run.md) programu dotnet [Kompiluj kompilacje dotnet](../tools/dotnet-build.md) , aby upewnić się, że cele kompilacji zostały skompilowane, a następnie wywoła `dotnet <assembly.dll>`, aby uruchomić aplikację docelową.</span><span class="sxs-lookup"><span data-stu-id="2150c-136">[dotnet run](../tools/dotnet-run.md) calls [dotnet build](../tools/dotnet-build.md) to ensure that the build targets have been built, and then calls `dotnet <assembly.dll>` to run the target application.</span></span>
    
    ```console
    dotnet run

    Hello World!
    ```
    
    <span data-ttu-id="2150c-137">Alternatywnie można również uruchomić `dotnet build`, aby skompilować kod bez uruchamiania aplikacji konsolowej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="2150c-137">Alternatively, you can also run `dotnet build` to compile the code without running the build console applications.</span></span> <span data-ttu-id="2150c-138">Powoduje to skompilowaną aplikację jako plik DLL, na podstawie nazwy projektu.</span><span class="sxs-lookup"><span data-stu-id="2150c-138">This results in a compiled application, as a DLL file, based on the name of the project.</span></span> <span data-ttu-id="2150c-139">W takim przypadku utworzony plik ma nazwę *Hello. dll*.</span><span class="sxs-lookup"><span data-stu-id="2150c-139">In this case, the file created is named *Hello.dll*.</span></span> <span data-ttu-id="2150c-140">Ta aplikacja może być uruchamiana z `dotnet bin\Debug\netcoreapp3.1\Hello.dll` w systemie Windows (Użyj `/` dla systemów innych niż Windows).</span><span class="sxs-lookup"><span data-stu-id="2150c-140">This app can be run with `dotnet bin\Debug\netcoreapp3.1\Hello.dll` on Windows (use `/` for non-Windows systems).</span></span>
    
    ```console
    dotnet bin\Debug\netcoreapp3.1\Hello.dll

    Hello World!
    ```
    
    <span data-ttu-id="2150c-141">Po skompilowaniu aplikacji tworzony jest plik wykonywalny specyficzny dla systemu operacyjnego wraz z `Hello.dll`.</span><span class="sxs-lookup"><span data-stu-id="2150c-141">When the app is compiled, an operating system-specific executable was created along with the `Hello.dll`.</span></span> <span data-ttu-id="2150c-142">W systemie Windows `Hello.exe`; w systemie Linux lub macOS `hello`.</span><span class="sxs-lookup"><span data-stu-id="2150c-142">On Windows, this would be `Hello.exe`; on Linux or macOS, this would be `hello`.</span></span> <span data-ttu-id="2150c-143">W powyższym przykładzie plik ma nazwę z `Hello.exe` lub `Hello`.</span><span class="sxs-lookup"><span data-stu-id="2150c-143">With the example above, the file is named with `Hello.exe` or `Hello`.</span></span> <span data-ttu-id="2150c-144">Można uruchomić ten plik wykonywalny bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="2150c-144">You can run that executable directly.</span></span>

    ```console
    .\bin\Debug\netcoreapp3.1\Hello.exe

    Hello World!
    ```

## <a name="modify-the-program"></a><span data-ttu-id="2150c-145">Modyfikowanie programu</span><span class="sxs-lookup"><span data-stu-id="2150c-145">Modify the program</span></span>

<span data-ttu-id="2150c-146">Zmieńmy program na bit.</span><span class="sxs-lookup"><span data-stu-id="2150c-146">Let's change the program a bit.</span></span> <span data-ttu-id="2150c-147">Liczby Fibonacci są przyjemne, więc Dodajmy ten argument, a także użyjesz argumentu, aby powitać osobę, która uruchamia aplikację.</span><span class="sxs-lookup"><span data-stu-id="2150c-147">Fibonacci numbers are fun, so let's add that and also to use the argument to greet the person running the app.</span></span>

01. <span data-ttu-id="2150c-148">Zastąp zawartość pliku *program.cs* następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="2150c-148">Replace the contents of your *Program.cs*  file with the following code:</span></span>

    [!code-csharp[Fibonacci](~/samples/core/console-apps/fibonacci-msbuild/Program.cs)]

02. <span data-ttu-id="2150c-149">Uruchom [kompilację dotnet](../tools/dotnet-build.md) , aby skompilować zmiany.</span><span class="sxs-lookup"><span data-stu-id="2150c-149">Run [dotnet build](../tools/dotnet-build.md) to compile the changes.</span></span>

03. <span data-ttu-id="2150c-150">Uruchom program, przekazując do aplikacji parametr.</span><span class="sxs-lookup"><span data-stu-id="2150c-150">Run the program passing a parameter to the app.</span></span> <span data-ttu-id="2150c-151">Korzystając z `dotnet` polecenia, aby uruchomić aplikację, Dodaj `--` do końca.</span><span class="sxs-lookup"><span data-stu-id="2150c-151">When you use the `dotnet` command to run an app, add `--` to the end.</span></span> <span data-ttu-id="2150c-152">Wszystkie elementy z prawej strony `--` zostaną przesłane jako parametr do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2150c-152">Anything to the right of `--` will be passed as a parameter to the app.</span></span> <span data-ttu-id="2150c-153">W poniższym przykładzie wartość `John` jest przenoszona do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2150c-153">In the following example, the value `John` is passed to the app.</span></span>

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

<span data-ttu-id="2150c-154">I to już wszystko!</span><span class="sxs-lookup"><span data-stu-id="2150c-154">And that's it!</span></span> <span data-ttu-id="2150c-155">Możesz zmodyfikować *program.cs* w dowolny sposób.</span><span class="sxs-lookup"><span data-stu-id="2150c-155">You can modify *Program.cs* any way you like.</span></span>

## <a name="working-with-multiple-files"></a><span data-ttu-id="2150c-156">Praca z wieloma plikami</span><span class="sxs-lookup"><span data-stu-id="2150c-156">Working with multiple files</span></span>

<span data-ttu-id="2150c-157">Pojedyncze pliki są ograniczone do prostych programów jednostronnych, ale jeśli tworzysz bardziej złożoną aplikację, prawdopodobnie będziesz mieć wiele plików kodu w projekcie.</span><span class="sxs-lookup"><span data-stu-id="2150c-157">Single files are fine for simple one-off programs, but if you're building a more complex app, you're probably going to have multiple code files on your project.</span></span> <span data-ttu-id="2150c-158">Utwórzmy od poprzedniego przykładu Fibonacci przez buforowanie niektórych wartości Fibonacci i dodanie niektórych funkcji cyklicznych.</span><span class="sxs-lookup"><span data-stu-id="2150c-158">Let's build off of the previous Fibonacci example by caching some Fibonacci values and add some recursive features.</span></span>

01. <span data-ttu-id="2150c-159">Dodaj nowy plik w katalogu *Hello* o nazwie *FibonacciGenerator.cs* przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="2150c-159">Add a new file inside the *Hello* directory named *FibonacciGenerator.cs* with the following code:</span></span>

    [!code-csharp[Fibonacci Generator](~/samples/core/console-apps/FibonacciBetterMsBuild/FibonacciGenerator.cs)]

02. <span data-ttu-id="2150c-160">Zmień metodę `Main` w pliku *program.cs* , aby utworzyć wystąpienie nowej klasy i wywołać jej metodę, tak jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="2150c-160">Change the `Main` method in your *Program.cs* file to instantiate the new class and call its method as in the following example:</span></span>

    [!code-csharp[New Program.cs](~/samples/core/console-apps/FibonacciBetterMsBuild/Program.cs)]

03. <span data-ttu-id="2150c-161">Uruchom [kompilację dotnet](../tools/dotnet-build.md) , aby skompilować zmiany.</span><span class="sxs-lookup"><span data-stu-id="2150c-161">Run [dotnet build](../tools/dotnet-build.md) to compile the changes.</span></span>

04. <span data-ttu-id="2150c-162">Uruchom aplikację, wykonując [uruchomienie programu dotnet](../tools/dotnet-run.md).</span><span class="sxs-lookup"><span data-stu-id="2150c-162">Run your app by executing [dotnet run](../tools/dotnet-run.md).</span></span> <span data-ttu-id="2150c-163">Poniżej przedstawiono dane wyjściowe programu:</span><span class="sxs-lookup"><span data-stu-id="2150c-163">The following shows the program output:</span></span>

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

## <a name="publish-your-app"></a><span data-ttu-id="2150c-164">Publikowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="2150c-164">Publish your app</span></span>

<span data-ttu-id="2150c-165">Gdy wszystko będzie gotowe do dystrybucji swojej aplikacji, użyj polecenia [dotnet Publish](../tools/dotnet-publish.md) w celu wygenerowania folderu _publikowania_ w _bin\\Debuguj\\netcoreapp 3.1\\publikowania\\_ (Użyj `/` w przypadku systemów innych niż Windows).</span><span class="sxs-lookup"><span data-stu-id="2150c-165">Once you're ready to distribute your app, use the [dotnet publish](../tools/dotnet-publish.md) command to generate the _publish_ folder at _bin\\debug\\netcoreapp3.1\\publish\\_ (use `/` for non-Windows systems).</span></span> <span data-ttu-id="2150c-166">Zawartość folderu _publikowania_ można dystrybuować na inne platformy, o ile już zainstalowano środowisko uruchomieniowe dotnet.</span><span class="sxs-lookup"><span data-stu-id="2150c-166">You can distribute the contents of the _publish_ folder to other platforms as long as they've already installed the dotnet runtime.</span></span>

```console
dotnet publish
Microsoft (R) Build Engine version 16.4.0+e901037fe for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 20 ms for C:\Code\Temp\Hello\Hello.csproj.
  Hello -> C:\Code\Temp\Hello\bin\Debug\netcoreapp3.1\Hello.dll
  Hello -> C:\Code\Temp\Hello\bin\Debug\netcoreapp3.1\publish\
```

<span data-ttu-id="2150c-167">Powyższe dane wyjściowe mogą się różnić w zależności od bieżącego folderu i systemu operacyjnego, ale dane wyjściowe powinny być podobne.</span><span class="sxs-lookup"><span data-stu-id="2150c-167">The output above may differ based on your current folder and operating system, but the output should be similar.</span></span>

<span data-ttu-id="2150c-168">Opublikowaną aplikację można uruchomić za pomocą polecenia [dotnet](../tools/dotnet.md) :</span><span class="sxs-lookup"><span data-stu-id="2150c-168">You can run your published app with the [dotnet](../tools/dotnet.md) command:</span></span>

```console
dotnet bin\Debug\netcoreapp3.1\publish\Hello.dll

Hello World!
```

<span data-ttu-id="2150c-169">Jak wspomniano na początku tego artykułu, tworzony jest plik wykonywalny specyficzny dla systemu operacyjnego wraz z `Hello.dll`.</span><span class="sxs-lookup"><span data-stu-id="2150c-169">As mentioned at the start of this article, an operating system-specific executable was created along with the `Hello.dll`.</span></span> <span data-ttu-id="2150c-170">W systemie Windows `Hello.exe`; w systemie Linux lub macOS `hello`.</span><span class="sxs-lookup"><span data-stu-id="2150c-170">On Windows, this would be `Hello.exe`; on Linux or macOS, this would be `hello`.</span></span> <span data-ttu-id="2150c-171">W powyższym przykładzie plik ma nazwę z `Hello.exe` lub `Hello`.</span><span class="sxs-lookup"><span data-stu-id="2150c-171">With the example above, the file is named with `Hello.exe` or `Hello`.</span></span> <span data-ttu-id="2150c-172">Można uruchomić bezpośrednio ten opublikowany plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="2150c-172">You can run this published executable directly.</span></span>

```console
.\bin\Debug\netcoreapp3.1\Hello.exe

Hello World!
```

## <a name="conclusion"></a><span data-ttu-id="2150c-173">Wniosek</span><span class="sxs-lookup"><span data-stu-id="2150c-173">Conclusion</span></span>

<span data-ttu-id="2150c-174">I to już wszystko!</span><span class="sxs-lookup"><span data-stu-id="2150c-174">And that's it!</span></span> <span data-ttu-id="2150c-175">Teraz możesz zacząć korzystać z podstawowych pojęć zamieszczonych w tym miejscu, aby utworzyć własne programy.</span><span class="sxs-lookup"><span data-stu-id="2150c-175">Now, you can start using the basic concepts learned here to create your own programs.</span></span>

## <a name="see-also"></a><span data-ttu-id="2150c-176">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2150c-176">See also</span></span>

- [<span data-ttu-id="2150c-177">Organizowanie i testowanie projektów przy użyciu narzędzi interfejs wiersza polecenia platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="2150c-177">Organizing and testing projects with the .NET Core CLI tools</span></span>](testing-with-cli.md)
- [<span data-ttu-id="2150c-178">Publikowanie aplikacji platformy .NET Core za pomocą interfejsu wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="2150c-178">Publish .NET Core apps with the CLI</span></span>](../deploying/deploy-with-cli.md)
- [<span data-ttu-id="2150c-179">Dowiedz się więcej o wdrażaniu aplikacji</span><span class="sxs-lookup"><span data-stu-id="2150c-179">Learn more about app deployment</span></span>](../deploying/index.md)

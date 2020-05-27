---
title: Rozpoczynanie pracy z platformą .NET Core przy użyciu interfejsu wiersza polecenia
description: Samouczek krok po kroku pokazujący, jak rozpocząć pracę z platformą .NET Core w systemie Windows, Linux lub macOS przy użyciu interfejs wiersza polecenia platformy .NET Core.
author: thraka
ms.author: adegeo
ms.date: 12/05/2019
ms.technology: dotnet-cli
ms.custom: updateeachrelease
ms.openlocfilehash: 7658f2498b87a90b3925d83628f6ea9247a2fc15
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/26/2020
ms.locfileid: "83840874"
---
# <a name="get-started-with-net-core-using-the-net-core-cli"></a><span data-ttu-id="ef6e0-103">Rozpoczynanie pracy z platformą .NET Core przy użyciu interfejs wiersza polecenia platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="ef6e0-103">Get started with .NET Core using the .NET Core CLI</span></span>

<span data-ttu-id="ef6e0-104">W tym artykule opisano sposób rozpoczynania opracowywania aplikacji .NET Core, które działają w systemach Windows, Linux i macOS przy użyciu interfejs wiersza polecenia platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ef6e0-104">This article will show you how to start developing .NET Core apps that work on Windows, Linux, and macOS using the .NET Core CLI.</span></span>

<span data-ttu-id="ef6e0-105">Jeśli nie znasz interfejs wiersza polecenia platformy .NET Core, zapoznaj się z tematem [interfejs wiersza polecenia platformy .NET Core Omówienie](../tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="ef6e0-105">If you're unfamiliar with the .NET Core CLI, see the [.NET Core CLI overview](../tools/index.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ef6e0-106">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="ef6e0-106">Prerequisites</span></span>

- <span data-ttu-id="ef6e0-107">[Zestaw .NET Core SDK 3,1](https://dotnet.microsoft.com/download) lub nowszymi wersjami.</span><span class="sxs-lookup"><span data-stu-id="ef6e0-107">[.NET Core SDK 3.1](https://dotnet.microsoft.com/download) or later versions.</span></span>
- <span data-ttu-id="ef6e0-108">Wybrany edytor tekstu lub edytor kodu.</span><span class="sxs-lookup"><span data-stu-id="ef6e0-108">A text editor or code editor of your choice.</span></span>

## <a name="hello-console-app"></a><span data-ttu-id="ef6e0-109">Witaj, Aplikacja konsolowa!</span><span class="sxs-lookup"><span data-stu-id="ef6e0-109">Hello, Console App!</span></span>

<span data-ttu-id="ef6e0-110">[Przykładowy kod można wyświetlić lub pobrać](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) z repozytorium usługi GitHub/przykłady</span><span class="sxs-lookup"><span data-stu-id="ef6e0-110">You can [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) from the dotnet/samples GitHub repository.</span></span> <span data-ttu-id="ef6e0-111">Aby uzyskać instrukcje dotyczące pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="ef6e0-111">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="ef6e0-112">Otwórz wiersz polecenia i Utwórz folder o nazwie *Hello*.</span><span class="sxs-lookup"><span data-stu-id="ef6e0-112">Open a command prompt and create a folder named *Hello*.</span></span> <span data-ttu-id="ef6e0-113">Przejdź do utworzonego folderu i wpisz następujące.</span><span class="sxs-lookup"><span data-stu-id="ef6e0-113">Navigate to the folder you created and type the following.</span></span>

```dotnetcli
dotnet new console
dotnet run
```

<span data-ttu-id="ef6e0-114">Wykonajmy szybkie wskazówki:</span><span class="sxs-lookup"><span data-stu-id="ef6e0-114">Let's do a quick walkthrough:</span></span>

01. `dotnet new console`

    <span data-ttu-id="ef6e0-115">Program [dotnet New](../tools/dotnet-new.md) tworzy aktualny plik projektu *Hello. csproj* z zależnościami niezbędnymi do skompilowania aplikacji konsolowej.</span><span class="sxs-lookup"><span data-stu-id="ef6e0-115">[dotnet new](../tools/dotnet-new.md) creates an up-to-date *Hello.csproj* project file with the dependencies necessary to build a console app.</span></span> <span data-ttu-id="ef6e0-116">Tworzy również *program.cs*, podstawowy plik zawierający punkt wejścia dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ef6e0-116">It also creates a *Program.cs*, a basic file containing the entry point for the application.</span></span>

    <span data-ttu-id="ef6e0-117">*Witaj. csproj*:</span><span class="sxs-lookup"><span data-stu-id="ef6e0-117">*Hello.csproj*:</span></span>

    [!code-xml[Hello.csproj](~/samples/snippets/core/tutorials/cli-create-console-app/HelloMsBuild/csharp/Hello.csproj)]

    <span data-ttu-id="ef6e0-118">Plik projektu określa wszystko, co jest potrzebne do przywrócenia zależności i skompilowania programu.</span><span class="sxs-lookup"><span data-stu-id="ef6e0-118">The project file specifies everything that's needed to restore dependencies and build the program.</span></span>

    - <span data-ttu-id="ef6e0-119">`<OutputType>`Element określa, że tworzysz plik wykonywalny, innymi słowy, Aplikacja konsolowa.</span><span class="sxs-lookup"><span data-stu-id="ef6e0-119">The `<OutputType>` element specifies that we're building an executable, in other words a console application.</span></span>
    - <span data-ttu-id="ef6e0-120">`<TargetFramework>`Element określa, która implementacja platformy .NET jest celem.</span><span class="sxs-lookup"><span data-stu-id="ef6e0-120">The `<TargetFramework>` element specifies what .NET implementation we're targeting.</span></span> <span data-ttu-id="ef6e0-121">W zaawansowanym scenariuszu można określić wiele platform docelowych i skompilować je do wszystkich w ramach jednej operacji.</span><span class="sxs-lookup"><span data-stu-id="ef6e0-121">In an advanced scenario, you can specify multiple target frameworks and build to all those in a single operation.</span></span> <span data-ttu-id="ef6e0-122">W tym samouczku dojdziemy do kompilowania tylko dla platformy .NET Core 3,1.</span><span class="sxs-lookup"><span data-stu-id="ef6e0-122">In this tutorial, we'll stick to building only for .NET Core 3.1.</span></span>

    <span data-ttu-id="ef6e0-123">*Program.cs*:</span><span class="sxs-lookup"><span data-stu-id="ef6e0-123">*Program.cs*:</span></span>

    [!code-csharp[Program.cs](~/samples/snippets/core/tutorials/cli-create-console-app/HelloMsBuild/csharp/Program.cs)]

    <span data-ttu-id="ef6e0-124">Program jest uruchamiany przez `using System` , co oznacza, że w zakresie tego pliku można przenieść wszystkie elementy w `System` przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="ef6e0-124">The program starts by `using System`, which means "bring everything in the `System` namespace into scope for this file".</span></span> <span data-ttu-id="ef6e0-125">`System`Przestrzeń nazw zawiera `Console` klasę.</span><span class="sxs-lookup"><span data-stu-id="ef6e0-125">The `System` namespace includes the `Console` class.</span></span>

    <span data-ttu-id="ef6e0-126">Następnie zdefiniujemy przestrzeń nazw o nazwie `Hello` .</span><span class="sxs-lookup"><span data-stu-id="ef6e0-126">We then define a namespace called `Hello`.</span></span> <span data-ttu-id="ef6e0-127">Możesz to zmienić w dowolny sposób.</span><span class="sxs-lookup"><span data-stu-id="ef6e0-127">You can change this to anything you want.</span></span> <span data-ttu-id="ef6e0-128">Klasa o nazwie `Program` jest zdefiniowana w tej przestrzeni nazw za pomocą `Main` metody, która pobiera tablicę ciągów o nazwie `args` .</span><span class="sxs-lookup"><span data-stu-id="ef6e0-128">A class named `Program` is defined within that namespace, with a `Main` method that takes an array of strings named `args`.</span></span> <span data-ttu-id="ef6e0-129">Ta tablica zawiera listę argumentów przekazaną podczas uruchamiania programu.</span><span class="sxs-lookup"><span data-stu-id="ef6e0-129">This array contains the list of arguments passed in when the program is run.</span></span> <span data-ttu-id="ef6e0-130">W takim przypadku tablica nie jest używana, a program po prostu zapisuje tekst "Hello world!"</span><span class="sxs-lookup"><span data-stu-id="ef6e0-130">As it is, this array is not used and the program simply writes the text "Hello World!"</span></span> <span data-ttu-id="ef6e0-131">w konsoli.</span><span class="sxs-lookup"><span data-stu-id="ef6e0-131">to the console.</span></span> <span data-ttu-id="ef6e0-132">Później wprowadzimy zmiany w kodzie, który będzie korzystał z tego argumentu.</span><span class="sxs-lookup"><span data-stu-id="ef6e0-132">Later, we'll make changes to the code that will make use of this argument.</span></span>

    <span data-ttu-id="ef6e0-133">`dotnet new`wywołania [dotnet Restore](../tools/dotnet-restore.md) niejawnie.</span><span class="sxs-lookup"><span data-stu-id="ef6e0-133">`dotnet new` calls [dotnet restore](../tools/dotnet-restore.md) implicitly.</span></span> <span data-ttu-id="ef6e0-134">`dotnet restore`wywołuje pakiet [NuGet](https://www.nuget.org/) (Menedżer pakietów .NET) w celu przywrócenia drzewa zależności.</span><span class="sxs-lookup"><span data-stu-id="ef6e0-134">`dotnet restore` calls into [NuGet](https://www.nuget.org/) (.NET package manager) to restore the tree of dependencies.</span></span> <span data-ttu-id="ef6e0-135">Pakiet NuGet analizuje plik *Hello. csproj* , pobiera zależności zdefiniowane w pliku (lub zbiera je z pamięci podręcznej na maszynie) i zapisuje plik *obj/Project. assets. JSON* , który jest niezbędny do skompilowania i uruchomienia przykładu.</span><span class="sxs-lookup"><span data-stu-id="ef6e0-135">NuGet analyzes the *Hello.csproj* file, downloads the dependencies defined in the file (or grabs them from a cache on your machine), and writes the *obj/project.assets.json* file, which is necessary to compile and run the sample.</span></span>

02. `dotnet run`

    <span data-ttu-id="ef6e0-136">[uruchomienia](../tools/dotnet-run.md) programu dotnet [kompiluje kompilacje dotnet](../tools/dotnet-build.md) , aby upewnić się, że cele kompilacji zostały skompilowane, a następnie wywołuje, `dotnet <assembly.dll>` Aby uruchomić aplikację docelową.</span><span class="sxs-lookup"><span data-stu-id="ef6e0-136">[dotnet run](../tools/dotnet-run.md) calls [dotnet build](../tools/dotnet-build.md) to ensure that the build targets have been built, and then calls `dotnet <assembly.dll>` to run the target application.</span></span>

    ```dotnetcli
    dotnet run
    ```

    <span data-ttu-id="ef6e0-137">Otrzymujesz następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="ef6e0-137">You get the following output.</span></span>

    ```console
    Hello World!
    ```

    <span data-ttu-id="ef6e0-138">Alternatywnie można również uruchomić polecenie, `dotnet build` Aby skompilować kod bez uruchamiania aplikacji konsolowej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="ef6e0-138">Alternatively, you can also run `dotnet build` to compile the code without running the build console applications.</span></span> <span data-ttu-id="ef6e0-139">Powoduje to skompilowaną aplikację jako plik DLL, na podstawie nazwy projektu.</span><span class="sxs-lookup"><span data-stu-id="ef6e0-139">This results in a compiled application, as a DLL file, based on the name of the project.</span></span> <span data-ttu-id="ef6e0-140">W takim przypadku utworzony plik ma nazwę *Hello. dll*.</span><span class="sxs-lookup"><span data-stu-id="ef6e0-140">In this case, the file created is named *Hello.dll*.</span></span> <span data-ttu-id="ef6e0-141">Ta aplikacja może być uruchamiana przy użyciu `dotnet bin\Debug\netcoreapp3.1\Hello.dll` systemu Windows (w `/` przypadku systemów innych niż Windows).</span><span class="sxs-lookup"><span data-stu-id="ef6e0-141">This app can be run with `dotnet bin\Debug\netcoreapp3.1\Hello.dll` on Windows (use `/` for non-Windows systems).</span></span>

    ```dotnetcli
    dotnet bin\Debug\netcoreapp3.1\Hello.dll
    ```

    <span data-ttu-id="ef6e0-142">Otrzymujesz następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="ef6e0-142">You get the following output.</span></span>

    ```console
    Hello World!
    ```

    <span data-ttu-id="ef6e0-143">Po skompilowaniu aplikacji plik wykonywalny specyficzny dla systemu operacyjnego został utworzony razem z `Hello.dll` .</span><span class="sxs-lookup"><span data-stu-id="ef6e0-143">When the app is compiled, an operating system-specific executable was created along with the `Hello.dll`.</span></span> <span data-ttu-id="ef6e0-144">W systemie Windows może to być `Hello.exe` : w systemie Linux lub macOS `hello` .</span><span class="sxs-lookup"><span data-stu-id="ef6e0-144">On Windows, this would be `Hello.exe`; on Linux or macOS, this would be `hello`.</span></span> <span data-ttu-id="ef6e0-145">W powyższym przykładzie plik ma nazwę z `Hello.exe` lub `Hello` .</span><span class="sxs-lookup"><span data-stu-id="ef6e0-145">With the example above, the file is named with `Hello.exe` or `Hello`.</span></span> <span data-ttu-id="ef6e0-146">Można uruchomić ten plik wykonywalny bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="ef6e0-146">You can run that executable directly.</span></span>

    ```console
    .\bin\Debug\netcoreapp3.1\Hello.exe

    Hello World!
    ```

## <a name="modify-the-program"></a><span data-ttu-id="ef6e0-147">Modyfikowanie programu</span><span class="sxs-lookup"><span data-stu-id="ef6e0-147">Modify the program</span></span>

<span data-ttu-id="ef6e0-148">Zmieńmy program na bit.</span><span class="sxs-lookup"><span data-stu-id="ef6e0-148">Let's change the program a bit.</span></span> <span data-ttu-id="ef6e0-149">Liczby Fibonacci są przyjemne, więc Dodajmy ten argument, a także użyjesz argumentu, aby powitać osobę, która uruchamia aplikację.</span><span class="sxs-lookup"><span data-stu-id="ef6e0-149">Fibonacci numbers are fun, so let's add that and also to use the argument to greet the person running the app.</span></span>

01. <span data-ttu-id="ef6e0-150">Zastąp zawartość pliku *program.cs* następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="ef6e0-150">Replace the contents of your *Program.cs*  file with the following code:</span></span>

    [!code-csharp[Fibonacci](~/samples/snippets/core/tutorials/cli-create-console-app/fibonacci-msbuild/csharp/Program.cs)]

02. <span data-ttu-id="ef6e0-151">Uruchom [kompilację dotnet](../tools/dotnet-build.md) , aby skompilować zmiany.</span><span class="sxs-lookup"><span data-stu-id="ef6e0-151">Run [dotnet build](../tools/dotnet-build.md) to compile the changes.</span></span>

03. <span data-ttu-id="ef6e0-152">Uruchom program, przekazując do aplikacji parametr.</span><span class="sxs-lookup"><span data-stu-id="ef6e0-152">Run the program passing a parameter to the app.</span></span> <span data-ttu-id="ef6e0-153">Gdy używasz `dotnet` polecenia, aby uruchomić aplikację, Dodaj `--` ją do końca.</span><span class="sxs-lookup"><span data-stu-id="ef6e0-153">When you use the `dotnet` command to run an app, add `--` to the end.</span></span> <span data-ttu-id="ef6e0-154">Wszystkie elementy z prawej strony `--` zostaną przesłane jako parametr do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ef6e0-154">Anything to the right of `--` will be passed as a parameter to the app.</span></span> <span data-ttu-id="ef6e0-155">W poniższym przykładzie wartość `John` jest przenoszona do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ef6e0-155">In the following example, the value `John` is passed to the app.</span></span>

    ```dotnetcli
    dotnet run -- John
    ```

    <span data-ttu-id="ef6e0-156">Otrzymujesz następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="ef6e0-156">You get the following output.</span></span>

    ```console
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

<span data-ttu-id="ef6e0-157">I to wszystko.</span><span class="sxs-lookup"><span data-stu-id="ef6e0-157">And that's it!</span></span> <span data-ttu-id="ef6e0-158">Możesz zmodyfikować *program.cs* w dowolny sposób.</span><span class="sxs-lookup"><span data-stu-id="ef6e0-158">You can modify *Program.cs* any way you like.</span></span>

## <a name="working-with-multiple-files"></a><span data-ttu-id="ef6e0-159">Praca z wieloma plikami</span><span class="sxs-lookup"><span data-stu-id="ef6e0-159">Working with multiple files</span></span>

<span data-ttu-id="ef6e0-160">Pojedyncze pliki są ograniczone do prostych programów jednostronnych, ale jeśli tworzysz bardziej złożoną aplikację, prawdopodobnie będziesz mieć wiele plików kodu w projekcie.</span><span class="sxs-lookup"><span data-stu-id="ef6e0-160">Single files are fine for simple one-off programs, but if you're building a more complex app, you're probably going to have multiple code files on your project.</span></span> <span data-ttu-id="ef6e0-161">Utwórzmy od poprzedniego przykładu Fibonacci przez buforowanie niektórych wartości Fibonacci i dodanie niektórych funkcji cyklicznych.</span><span class="sxs-lookup"><span data-stu-id="ef6e0-161">Let's build off of the previous Fibonacci example by caching some Fibonacci values and add some recursive features.</span></span>

01. <span data-ttu-id="ef6e0-162">Dodaj nowy plik w katalogu *Hello* o nazwie *FibonacciGenerator.cs* przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="ef6e0-162">Add a new file inside the *Hello* directory named *FibonacciGenerator.cs* with the following code:</span></span>

    [!code-csharp[Fibonacci Generator](~/samples/snippets/core/tutorials/cli-create-console-app/FibonacciBetterMsBuild/csharp/FibonacciGenerator.cs)]

02. <span data-ttu-id="ef6e0-163">Zmień `Main` metodę w pliku *program.cs* , aby utworzyć wystąpienie nowej klasy i wywołać jej metodę tak jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="ef6e0-163">Change the `Main` method in your *Program.cs* file to instantiate the new class and call its method as in the following example:</span></span>

    [!code-csharp[New Program.cs](~/samples/snippets/core/tutorials/cli-create-console-app/FibonacciBetterMsBuild/csharp/Program.cs)]

03. <span data-ttu-id="ef6e0-164">Uruchom [kompilację dotnet](../tools/dotnet-build.md) , aby skompilować zmiany.</span><span class="sxs-lookup"><span data-stu-id="ef6e0-164">Run [dotnet build](../tools/dotnet-build.md) to compile the changes.</span></span>

04. <span data-ttu-id="ef6e0-165">Uruchom aplikację, wykonując [uruchomienie programu dotnet](../tools/dotnet-run.md).</span><span class="sxs-lookup"><span data-stu-id="ef6e0-165">Run your app by executing [dotnet run](../tools/dotnet-run.md).</span></span>

    ```dotnetcli
    dotnet run
    ```

    <span data-ttu-id="ef6e0-166">Otrzymujesz następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="ef6e0-166">You get the following output.</span></span>

    ```console
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

## <a name="publish-your-app"></a><span data-ttu-id="ef6e0-167">Publikowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="ef6e0-167">Publish your app</span></span>

<span data-ttu-id="ef6e0-168">Gdy wszystko będzie gotowe do dystrybucji swojej aplikacji, użyj polecenia [dotnet Publish](../tools/dotnet-publish.md) , aby wygenerować folder _publikowania_ w polu _Debuguj debugowanie w usłudze bin \\ \\ netcoreapp 3.1 \\ \\ _ (Korzystanie `/` z systemów innych niż Windows).</span><span class="sxs-lookup"><span data-stu-id="ef6e0-168">Once you're ready to distribute your app, use the [dotnet publish](../tools/dotnet-publish.md) command to generate the _publish_ folder at _bin\\debug\\netcoreapp3.1\\publish\\_ (use `/` for non-Windows systems).</span></span> <span data-ttu-id="ef6e0-169">Zawartość folderu _publikowania_ można dystrybuować na inne platformy, o ile już zainstalowano środowisko uruchomieniowe dotnet.</span><span class="sxs-lookup"><span data-stu-id="ef6e0-169">You can distribute the contents of the _publish_ folder to other platforms as long as they've already installed the dotnet runtime.</span></span>

```dotnetcli
dotnet publish
```

<span data-ttu-id="ef6e0-170">Dane wyjściowe są podobne do poniższych.</span><span class="sxs-lookup"><span data-stu-id="ef6e0-170">You get output similar to the following.</span></span>

```console
Microsoft (R) Build Engine version 16.4.0+e901037fe for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 20 ms for C:\Code\Temp\Hello\Hello.csproj.
  Hello -> C:\Code\Temp\Hello\bin\Debug\netcoreapp3.1\Hello.dll
  Hello -> C:\Code\Temp\Hello\bin\Debug\netcoreapp3.1\publish\
```

<span data-ttu-id="ef6e0-171">Powyższe dane wyjściowe mogą się różnić w zależności od bieżącego folderu i systemu operacyjnego, ale dane wyjściowe powinny być podobne.</span><span class="sxs-lookup"><span data-stu-id="ef6e0-171">The output above may differ based on your current folder and operating system, but the output should be similar.</span></span>

<span data-ttu-id="ef6e0-172">Opublikowaną aplikację można uruchomić za pomocą polecenia [dotnet](../tools/dotnet.md) :</span><span class="sxs-lookup"><span data-stu-id="ef6e0-172">You can run your published app with the [dotnet](../tools/dotnet.md) command:</span></span>

```dotnetcli
dotnet bin\Debug\netcoreapp3.1\publish\Hello.dll
```

<span data-ttu-id="ef6e0-173">Otrzymujesz następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="ef6e0-173">You get the following output.</span></span>

```console
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

<span data-ttu-id="ef6e0-174">Jak wspomniano na początku tego artykułu, tworzony jest plik wykonywalny specyficzny dla systemu operacyjnego wraz z programem `Hello.dll` .</span><span class="sxs-lookup"><span data-stu-id="ef6e0-174">As mentioned at the start of this article, an operating system-specific executable was created along with the `Hello.dll`.</span></span> <span data-ttu-id="ef6e0-175">W systemie Windows może to być `Hello.exe` : w systemie Linux lub macOS `hello` .</span><span class="sxs-lookup"><span data-stu-id="ef6e0-175">On Windows, this would be `Hello.exe`; on Linux or macOS, this would be `hello`.</span></span> <span data-ttu-id="ef6e0-176">W powyższym przykładzie plik ma nazwę z `Hello.exe` lub `Hello` .</span><span class="sxs-lookup"><span data-stu-id="ef6e0-176">With the example above, the file is named with `Hello.exe` or `Hello`.</span></span> <span data-ttu-id="ef6e0-177">Można uruchomić bezpośrednio ten opublikowany plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="ef6e0-177">You can run this published executable directly.</span></span>

```console
.\bin\Debug\netcoreapp3.1\publish\Hello.exe

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

## <a name="conclusion"></a><span data-ttu-id="ef6e0-178">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="ef6e0-178">Conclusion</span></span>

<span data-ttu-id="ef6e0-179">I to wszystko.</span><span class="sxs-lookup"><span data-stu-id="ef6e0-179">And that's it!</span></span> <span data-ttu-id="ef6e0-180">Teraz możesz zacząć korzystać z podstawowych pojęć zamieszczonych w tym miejscu, aby utworzyć własne programy.</span><span class="sxs-lookup"><span data-stu-id="ef6e0-180">Now, you can start using the basic concepts learned here to create your own programs.</span></span>

## <a name="see-also"></a><span data-ttu-id="ef6e0-181">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ef6e0-181">See also</span></span>

- [<span data-ttu-id="ef6e0-182">Organizowanie i testowanie projektów przy użyciu interfejs wiersza polecenia platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="ef6e0-182">Organizing and testing projects with the .NET Core CLI</span></span>](testing-with-cli.md)
- [<span data-ttu-id="ef6e0-183">Publikowanie aplikacji platformy .NET Core za pomocą interfejs wiersza polecenia platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="ef6e0-183">Publish .NET Core apps with the .NET Core CLI</span></span>](../deploying/deploy-with-cli.md)
- [<span data-ttu-id="ef6e0-184">Wdrażanie aplikacji .NET Core</span><span class="sxs-lookup"><span data-stu-id="ef6e0-184">.NET Core application deployment</span></span>](../deploying/index.md)

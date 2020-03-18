---
title: Rozpoczynanie pracy z platformą .NET Core przy użyciu interfejsu wiersza polecenia
description: Samouczek krok po kroku przedstawiający sposób rozpoczynania pracy z programem .NET Core w systemach Windows, Linux lub macOS przy użyciu procesora CLI .NET Core.
author: thraka
ms.author: adegeo
ms.date: 12/05/2019
ms.technology: dotnet-cli
ms.custom: updateeachrelease
ms.openlocfilehash: fe69521a6ac88055e3e8c8502a7e19a72667dbef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78240860"
---
# <a name="get-started-with-net-core-using-the-net-core-cli"></a><span data-ttu-id="ef0ae-103">Wprowadzenie do programu .NET Core przy użyciu procesora CLI .NET Core</span><span class="sxs-lookup"><span data-stu-id="ef0ae-103">Get started with .NET Core using the .NET Core CLI</span></span>

<span data-ttu-id="ef0ae-104">W tym artykule przedstawiono sposób uruchamiania tworzenia aplikacji .NET Core działających w systemach Windows, Linux i macOS przy użyciu procesora CLI .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ef0ae-104">This article will show you how to start developing .NET Core apps that work on Windows, Linux, and macOS using the .NET Core CLI.</span></span>

<span data-ttu-id="ef0ae-105">Jeśli nie znasz cli programu .NET Core, zobacz [omówienie.NET Core CLI](../tools/index.md).</span><span class="sxs-lookup"><span data-stu-id="ef0ae-105">If you're unfamiliar with the .NET Core CLI, see the [.NET Core CLI overview](../tools/index.md).</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ef0ae-106">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="ef0ae-106">Prerequisites</span></span>

- <span data-ttu-id="ef0ae-107">[.NET Core SDK 3.1](https://dotnet.microsoft.com/download) lub nowsze wersje.</span><span class="sxs-lookup"><span data-stu-id="ef0ae-107">[.NET Core SDK 3.1](https://dotnet.microsoft.com/download) or later versions.</span></span>
- <span data-ttu-id="ef0ae-108">Wybrany edytor tekstu lub edytor kodu.</span><span class="sxs-lookup"><span data-stu-id="ef0ae-108">A text editor or code editor of your choice.</span></span>

## <a name="hello-console-app"></a><span data-ttu-id="ef0ae-109">Witam, Aplikacja konsolowa!</span><span class="sxs-lookup"><span data-stu-id="ef0ae-109">Hello, Console App!</span></span>

<span data-ttu-id="ef0ae-110">Przykładowy kod można [wyświetlić lub pobrać](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) z repozytorium GitHub dotnet/samples.</span><span class="sxs-lookup"><span data-stu-id="ef0ae-110">You can [view or download the sample code](https://github.com/dotnet/samples/tree/master/core/console-apps/HelloMsBuild) from the dotnet/samples GitHub repository.</span></span> <span data-ttu-id="ef0ae-111">Aby uzyskać instrukcje dotyczące pobierania, zobacz [Przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="ef0ae-111">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="ef0ae-112">Otwórz wiersz polecenia i utwórz folder o nazwie *Hello*.</span><span class="sxs-lookup"><span data-stu-id="ef0ae-112">Open a command prompt and create a folder named *Hello*.</span></span> <span data-ttu-id="ef0ae-113">Przejdź do utworzonego folderu i wpisz następujące elementy.</span><span class="sxs-lookup"><span data-stu-id="ef0ae-113">Navigate to the folder you created and type the following.</span></span>

```dotnetcli
dotnet new console
dotnet run
```

<span data-ttu-id="ef0ae-114">Zróbmy szybki przewodnik:</span><span class="sxs-lookup"><span data-stu-id="ef0ae-114">Let's do a quick walkthrough:</span></span>

01. `dotnet new console`

    <span data-ttu-id="ef0ae-115">[dotnet new](../tools/dotnet-new.md) tworzy aktualny plik projektu *Hello.csproj* z zależnościami niezbędnymi do utworzenia aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="ef0ae-115">[dotnet new](../tools/dotnet-new.md) creates an up-to-date *Hello.csproj* project file with the dependencies necessary to build a console app.</span></span> <span data-ttu-id="ef0ae-116">Tworzy również *Program.cs*, podstawowy plik zawierający punkt wejścia dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ef0ae-116">It also creates a *Program.cs*, a basic file containing the entry point for the application.</span></span>

    <span data-ttu-id="ef0ae-117">*Hello.csproj*:</span><span class="sxs-lookup"><span data-stu-id="ef0ae-117">*Hello.csproj*:</span></span>

    [!code-xml[Hello.csproj](~/samples/snippets/core/tutorials/cli-create-console-app/HelloMsBuild/csharp/Hello.csproj)]

    <span data-ttu-id="ef0ae-118">Plik projektu określa wszystko, co jest potrzebne do przywrócenia zależności i skompilowania programu.</span><span class="sxs-lookup"><span data-stu-id="ef0ae-118">The project file specifies everything that's needed to restore dependencies and build the program.</span></span>

    - <span data-ttu-id="ef0ae-119">Element `<OutputType>` określa, że budujemy plik wykonywalny, innymi słowy aplikacji konsoli.</span><span class="sxs-lookup"><span data-stu-id="ef0ae-119">The `<OutputType>` element specifies that we're building an executable, in other words a console application.</span></span>
    - <span data-ttu-id="ef0ae-120">Element `<TargetFramework>` określa, na co kierujemy implementację .NET.</span><span class="sxs-lookup"><span data-stu-id="ef0ae-120">The `<TargetFramework>` element specifies what .NET implementation we're targeting.</span></span> <span data-ttu-id="ef0ae-121">W zaawansowanym scenariuszu można określić wiele struktur docelowych i skompilować do wszystkich tych w jednej operacji.</span><span class="sxs-lookup"><span data-stu-id="ef0ae-121">In an advanced scenario, you can specify multiple target frameworks and build to all those in a single operation.</span></span> <span data-ttu-id="ef0ae-122">W tym samouczku będziemy trzymać się budynku tylko dla .NET Core 3.1.</span><span class="sxs-lookup"><span data-stu-id="ef0ae-122">In this tutorial, we'll stick to building only for .NET Core 3.1.</span></span>

    <span data-ttu-id="ef0ae-123">*Program.cs:*</span><span class="sxs-lookup"><span data-stu-id="ef0ae-123">*Program.cs*:</span></span>

    [!code-csharp[Program.cs](~/samples/snippets/core/tutorials/cli-create-console-app/HelloMsBuild/csharp/Program.cs)]

    <span data-ttu-id="ef0ae-124">Program rozpoczyna `using System`się od , co `System` oznacza "przynieś wszystko w przestrzeni nazw do zakresu dla tego pliku".</span><span class="sxs-lookup"><span data-stu-id="ef0ae-124">The program starts by `using System`, which means "bring everything in the `System` namespace into scope for this file".</span></span> <span data-ttu-id="ef0ae-125">Obszar `System` nazw zawiera `Console` klasę.</span><span class="sxs-lookup"><span data-stu-id="ef0ae-125">The `System` namespace includes the `Console` class.</span></span>

    <span data-ttu-id="ef0ae-126">Następnie definiujemy obszar `Hello`nazw o nazwie .</span><span class="sxs-lookup"><span data-stu-id="ef0ae-126">We then define a namespace called `Hello`.</span></span> <span data-ttu-id="ef0ae-127">Możesz to zmienić na doc, co chcesz.</span><span class="sxs-lookup"><span data-stu-id="ef0ae-127">You can change this to anything you want.</span></span> <span data-ttu-id="ef0ae-128">Klasa o `Program` nazwie jest zdefiniowana w `Main` tym obszarze nazw, z `args`metodą, która przyjmuje tablicę ciągów o nazwie .</span><span class="sxs-lookup"><span data-stu-id="ef0ae-128">A class named `Program` is defined within that namespace, with a `Main` method that takes an array of strings named `args`.</span></span> <span data-ttu-id="ef0ae-129">Ta tablica zawiera listę argumentów przekazywanych po uruchomieniu programu.</span><span class="sxs-lookup"><span data-stu-id="ef0ae-129">This array contains the list of arguments passed in when the program is run.</span></span> <span data-ttu-id="ef0ae-130">Jak to jest, ta tablica nie jest używany, a program po prostu pisze tekst "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="ef0ae-130">As it is, this array is not used and the program simply writes the text "Hello World!"</span></span> <span data-ttu-id="ef0ae-131">w konsoli.</span><span class="sxs-lookup"><span data-stu-id="ef0ae-131">to the console.</span></span> <span data-ttu-id="ef0ae-132">Później wprowadzimy zmiany w kodzie, które będą korzystać z tego argumentu.</span><span class="sxs-lookup"><span data-stu-id="ef0ae-132">Later, we'll make changes to the code that will make use of this argument.</span></span>

    <span data-ttu-id="ef0ae-133">`dotnet new`wywołuje [przywracanie dotnet](../tools/dotnet-restore.md) niejawnie.</span><span class="sxs-lookup"><span data-stu-id="ef0ae-133">`dotnet new` calls [dotnet restore](../tools/dotnet-restore.md) implicitly.</span></span> <span data-ttu-id="ef0ae-134">`dotnet restore`wywołania [nuget](https://www.nuget.org/) (menedżer pakietów.NET), aby przywrócić drzewo zależności.</span><span class="sxs-lookup"><span data-stu-id="ef0ae-134">`dotnet restore` calls into [NuGet](https://www.nuget.org/) (.NET package manager) to restore the tree of dependencies.</span></span> <span data-ttu-id="ef0ae-135">NuGet analizuje plik *Hello.csproj,* pobiera zależności zdefiniowane w pliku (lub pobiera je z pamięci podręcznej na komputerze) i zapisuje plik *obj/project.assets.json,* który jest niezbędny do skompilowania i uruchomienia próbki.</span><span class="sxs-lookup"><span data-stu-id="ef0ae-135">NuGet analyzes the *Hello.csproj* file, downloads the dependencies defined in the file (or grabs them from a cache on your machine), and writes the *obj/project.assets.json* file, which is necessary to compile and run the sample.</span></span>

02. `dotnet run`

    <span data-ttu-id="ef0ae-136">[dotnet uruchom](../tools/dotnet-run.md) [wywołania dotnet kompilacji,](../tools/dotnet-build.md) aby upewnić się, że cele kompilacji zostały zbudowane, a następnie wywołuje `dotnet <assembly.dll>` do uruchomienia aplikacji docelowej.</span><span class="sxs-lookup"><span data-stu-id="ef0ae-136">[dotnet run](../tools/dotnet-run.md) calls [dotnet build](../tools/dotnet-build.md) to ensure that the build targets have been built, and then calls `dotnet <assembly.dll>` to run the target application.</span></span>

    ```dotnetcli
    dotnet run
    ```

    <span data-ttu-id="ef0ae-137">Otrzymasz następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="ef0ae-137">You get the following output.</span></span>

    ```console
    Hello World!
    ```

    <span data-ttu-id="ef0ae-138">Alternatywnie można również `dotnet build` uruchomić, aby skompilować kod bez uruchamiania aplikacji konsoli kompilacji.</span><span class="sxs-lookup"><span data-stu-id="ef0ae-138">Alternatively, you can also run `dotnet build` to compile the code without running the build console applications.</span></span> <span data-ttu-id="ef0ae-139">Powoduje to skompilowany aplikacji, jako plik DLL, na podstawie nazwy projektu.</span><span class="sxs-lookup"><span data-stu-id="ef0ae-139">This results in a compiled application, as a DLL file, based on the name of the project.</span></span> <span data-ttu-id="ef0ae-140">W takim przypadku utworzony plik nosi nazwę *Hello.dll*.</span><span class="sxs-lookup"><span data-stu-id="ef0ae-140">In this case, the file created is named *Hello.dll*.</span></span> <span data-ttu-id="ef0ae-141">Ta aplikacja może `dotnet bin\Debug\netcoreapp3.1\Hello.dll` być uruchamiana `/` w systemie Windows (używany dla systemów innych niż Windows).</span><span class="sxs-lookup"><span data-stu-id="ef0ae-141">This app can be run with `dotnet bin\Debug\netcoreapp3.1\Hello.dll` on Windows (use `/` for non-Windows systems).</span></span>

    ```dotnetcli
    dotnet bin\Debug\netcoreapp3.1\Hello.dll
    ```

    <span data-ttu-id="ef0ae-142">Otrzymasz następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="ef0ae-142">You get the following output.</span></span>

    ```console
    Hello World!
    ```

    <span data-ttu-id="ef0ae-143">Po skompilowaniu aplikacji utworzono plik wykonywalny `Hello.dll`specyficzny dla systemu operacyjnego wraz z plikiem .</span><span class="sxs-lookup"><span data-stu-id="ef0ae-143">When the app is compiled, an operating system-specific executable was created along with the `Hello.dll`.</span></span> <span data-ttu-id="ef0ae-144">W systemie Windows `Hello.exe`byłoby to ; na Linuksie lub macOS, byłoby `hello`to .</span><span class="sxs-lookup"><span data-stu-id="ef0ae-144">On Windows, this would be `Hello.exe`; on Linux or macOS, this would be `hello`.</span></span> <span data-ttu-id="ef0ae-145">W powyższym przykładzie plik ma `Hello.exe` `Hello`nazwę lub .</span><span class="sxs-lookup"><span data-stu-id="ef0ae-145">With the example above, the file is named with `Hello.exe` or `Hello`.</span></span> <span data-ttu-id="ef0ae-146">Można uruchomić ten plik wykonywalny bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="ef0ae-146">You can run that executable directly.</span></span>

    ```console
    .\bin\Debug\netcoreapp3.1\Hello.exe

    Hello World!
    ```

## <a name="modify-the-program"></a><span data-ttu-id="ef0ae-147">Modyfikowanie programu</span><span class="sxs-lookup"><span data-stu-id="ef0ae-147">Modify the program</span></span>

<span data-ttu-id="ef0ae-148">Zmieńmy nieco program.</span><span class="sxs-lookup"><span data-stu-id="ef0ae-148">Let's change the program a bit.</span></span> <span data-ttu-id="ef0ae-149">Numery Fibonacciego są zabawne, więc dodajmy to, a także użyjmy argumentu, aby powitać osobę uruchamiającą aplikację.</span><span class="sxs-lookup"><span data-stu-id="ef0ae-149">Fibonacci numbers are fun, so let's add that and also to use the argument to greet the person running the app.</span></span>

01. <span data-ttu-id="ef0ae-150">Zastąp zawartość pliku *Program.cs* następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="ef0ae-150">Replace the contents of your *Program.cs*  file with the following code:</span></span>

    [!code-csharp[Fibonacci](~/samples/snippets/core/tutorials/cli-create-console-app/fibonacci-msbuild/csharp/Program.cs)]

02. <span data-ttu-id="ef0ae-151">Uruchom [kompilację dotnet,](../tools/dotnet-build.md) aby skompilować zmiany.</span><span class="sxs-lookup"><span data-stu-id="ef0ae-151">Run [dotnet build](../tools/dotnet-build.md) to compile the changes.</span></span>

03. <span data-ttu-id="ef0ae-152">Uruchom program przekazujący parametr do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ef0ae-152">Run the program passing a parameter to the app.</span></span> <span data-ttu-id="ef0ae-153">Gdy używasz `dotnet` polecenia, aby uruchomić `--` aplikację, dodaj do końca.</span><span class="sxs-lookup"><span data-stu-id="ef0ae-153">When you use the `dotnet` command to run an app, add `--` to the end.</span></span> <span data-ttu-id="ef0ae-154">Wszystko po prawej `--` stronie zostanie przekazane jako parametr do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ef0ae-154">Anything to the right of `--` will be passed as a parameter to the app.</span></span> <span data-ttu-id="ef0ae-155">W poniższym przykładzie `John` wartość jest przekazywana do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ef0ae-155">In the following example, the value `John` is passed to the app.</span></span>

    ```dotnetcli
    dotnet run -- John
    ```

    <span data-ttu-id="ef0ae-156">Otrzymasz następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="ef0ae-156">You get the following output.</span></span>

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

<span data-ttu-id="ef0ae-157">I to wszystko.</span><span class="sxs-lookup"><span data-stu-id="ef0ae-157">And that's it!</span></span> <span data-ttu-id="ef0ae-158">Możesz modyfikować *Program.cs* dowolny sposób.</span><span class="sxs-lookup"><span data-stu-id="ef0ae-158">You can modify *Program.cs* any way you like.</span></span>

## <a name="working-with-multiple-files"></a><span data-ttu-id="ef0ae-159">Praca z wieloma plikami</span><span class="sxs-lookup"><span data-stu-id="ef0ae-159">Working with multiple files</span></span>

<span data-ttu-id="ef0ae-160">Pojedyncze pliki są w porządku dla prostych jednorazowych programów, ale jeśli budujesz bardziej złożoną aplikację, prawdopodobnie będziesz mieć wiele plików kodu w projekcie.</span><span class="sxs-lookup"><span data-stu-id="ef0ae-160">Single files are fine for simple one-off programs, but if you're building a more complex app, you're probably going to have multiple code files on your project.</span></span> <span data-ttu-id="ef0ae-161">Zbudujmy poprzedni przykład Fibonacciego, buforując niektóre wartości Fibonacciego i dodajmy niektóre funkcje cykliczne.</span><span class="sxs-lookup"><span data-stu-id="ef0ae-161">Let's build off of the previous Fibonacci example by caching some Fibonacci values and add some recursive features.</span></span>

01. <span data-ttu-id="ef0ae-162">Dodaj nowy plik w katalogu *Hello* o nazwie *FibonacciGenerator.cs* z następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="ef0ae-162">Add a new file inside the *Hello* directory named *FibonacciGenerator.cs* with the following code:</span></span>

    [!code-csharp[Fibonacci Generator](~/samples/snippets/core/tutorials/cli-create-console-app/FibonacciBetterMsBuild/csharp/FibonacciGenerator.cs)]

02. <span data-ttu-id="ef0ae-163">Zmień `Main` metodę w pliku *Program.cs,* aby utworzyć wystąpienie nowej klasy i wywołać jej metodę, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="ef0ae-163">Change the `Main` method in your *Program.cs* file to instantiate the new class and call its method as in the following example:</span></span>

    [!code-csharp[New Program.cs](~/samples/snippets/core/tutorials/cli-create-console-app/FibonacciBetterMsBuild/csharp/Program.cs)]

03. <span data-ttu-id="ef0ae-164">Uruchom [kompilację dotnet,](../tools/dotnet-build.md) aby skompilować zmiany.</span><span class="sxs-lookup"><span data-stu-id="ef0ae-164">Run [dotnet build](../tools/dotnet-build.md) to compile the changes.</span></span>

04. <span data-ttu-id="ef0ae-165">Uruchom aplikację, wykonując [dotnet uruchom](../tools/dotnet-run.md).</span><span class="sxs-lookup"><span data-stu-id="ef0ae-165">Run your app by executing [dotnet run](../tools/dotnet-run.md).</span></span>

    ```dotnetcli
    dotnet run
    ```

    <span data-ttu-id="ef0ae-166">Otrzymasz następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="ef0ae-166">You get the following output.</span></span>

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

## <a name="publish-your-app"></a><span data-ttu-id="ef0ae-167">Publikowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="ef0ae-167">Publish your app</span></span>

<span data-ttu-id="ef0ae-168">Gdy wszystko będzie gotowe do dystrybucji aplikacji, użyj polecenia [publikowania dotnet,](../tools/dotnet-publish.md) aby wygenerować folder `/` _publikowania_ w _bin\\debugnetcoreapp3.1\\\\publish\\ _ (używany dla systemów innych niż Windows).</span><span class="sxs-lookup"><span data-stu-id="ef0ae-168">Once you're ready to distribute your app, use the [dotnet publish](../tools/dotnet-publish.md) command to generate the _publish_ folder at _bin\\debug\\netcoreapp3.1\\publish\\_ (use `/` for non-Windows systems).</span></span> <span data-ttu-id="ef0ae-169">Zawartość folderu _publikowania_ można rozpowszechniać na innych platformach, o ile zostały już zainstalowane w czasie wykonywania dotnet.</span><span class="sxs-lookup"><span data-stu-id="ef0ae-169">You can distribute the contents of the _publish_ folder to other platforms as long as they've already installed the dotnet runtime.</span></span>

```dotnetcli
dotnet publish
```

<span data-ttu-id="ef0ae-170">Otrzymasz dane wyjściowe podobne do następującego.</span><span class="sxs-lookup"><span data-stu-id="ef0ae-170">You get output similar to the following.</span></span>

```console
Microsoft (R) Build Engine version 16.4.0+e901037fe for .NET Core
Copyright (C) Microsoft Corporation. All rights reserved.

  Restore completed in 20 ms for C:\Code\Temp\Hello\Hello.csproj.
  Hello -> C:\Code\Temp\Hello\bin\Debug\netcoreapp3.1\Hello.dll
  Hello -> C:\Code\Temp\Hello\bin\Debug\netcoreapp3.1\publish\
```

<span data-ttu-id="ef0ae-171">Powyższe dane wyjściowe mogą się różnić w zależności od bieżącego folderu i systemu operacyjnego, ale dane wyjściowe powinny być podobne.</span><span class="sxs-lookup"><span data-stu-id="ef0ae-171">The output above may differ based on your current folder and operating system, but the output should be similar.</span></span>

<span data-ttu-id="ef0ae-172">Opublikowaną aplikację można uruchomić za pomocą polecenia [dotnet:](../tools/dotnet.md)</span><span class="sxs-lookup"><span data-stu-id="ef0ae-172">You can run your published app with the [dotnet](../tools/dotnet.md) command:</span></span>

```dotnetcli
dotnet bin\Debug\netcoreapp3.1\publish\Hello.dll
```

<span data-ttu-id="ef0ae-173">Otrzymasz następujące dane wyjściowe.</span><span class="sxs-lookup"><span data-stu-id="ef0ae-173">You get the following output.</span></span>

```console
Hello World!
```

<span data-ttu-id="ef0ae-174">Jak wspomniano na początku tego artykułu, plik wykonywalny specyficzny `Hello.dll`dla systemu operacyjnego został utworzony wraz z plikiem .</span><span class="sxs-lookup"><span data-stu-id="ef0ae-174">As mentioned at the start of this article, an operating system-specific executable was created along with the `Hello.dll`.</span></span> <span data-ttu-id="ef0ae-175">W systemie Windows `Hello.exe`byłoby to ; na Linuksie lub macOS, byłoby `hello`to .</span><span class="sxs-lookup"><span data-stu-id="ef0ae-175">On Windows, this would be `Hello.exe`; on Linux or macOS, this would be `hello`.</span></span> <span data-ttu-id="ef0ae-176">W powyższym przykładzie plik ma `Hello.exe` `Hello`nazwę lub .</span><span class="sxs-lookup"><span data-stu-id="ef0ae-176">With the example above, the file is named with `Hello.exe` or `Hello`.</span></span> <span data-ttu-id="ef0ae-177">Ten opublikowany plik wykonywalny można uruchomić bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="ef0ae-177">You can run this published executable directly.</span></span>

```console
.\bin\Debug\netcoreapp3.1\publish\Hello.exe

Hello World!
```

## <a name="conclusion"></a><span data-ttu-id="ef0ae-178">Podsumowanie</span><span class="sxs-lookup"><span data-stu-id="ef0ae-178">Conclusion</span></span>

<span data-ttu-id="ef0ae-179">I to wszystko.</span><span class="sxs-lookup"><span data-stu-id="ef0ae-179">And that's it!</span></span> <span data-ttu-id="ef0ae-180">Teraz możesz zacząć korzystać z podstawowych pojęć, które zostały tutaj nauczone, aby tworzyć własne programy.</span><span class="sxs-lookup"><span data-stu-id="ef0ae-180">Now, you can start using the basic concepts learned here to create your own programs.</span></span>

## <a name="see-also"></a><span data-ttu-id="ef0ae-181">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ef0ae-181">See also</span></span>

- [<span data-ttu-id="ef0ae-182">Organizowanie i testowanie projektów za pomocą cli .NET Core</span><span class="sxs-lookup"><span data-stu-id="ef0ae-182">Organizing and testing projects with the .NET Core CLI</span></span>](testing-with-cli.md)
- [<span data-ttu-id="ef0ae-183">Publikowanie aplikacji .NET Core za pomocą wiersza wiersza wiersza wiersza wiersza .NET Core</span><span class="sxs-lookup"><span data-stu-id="ef0ae-183">Publish .NET Core apps with the .NET Core CLI</span></span>](../deploying/deploy-with-cli.md)
- [<span data-ttu-id="ef0ae-184">Wdrażanie aplikacji .NET Core</span><span class="sxs-lookup"><span data-stu-id="ef0ae-184">.NET Core application deployment</span></span>](../deploying/index.md)

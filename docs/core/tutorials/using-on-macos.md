---
title: Wprowadzenie do platformy .NET Core na macOS
description: Ten dokument zawiera kroki i przepływ pracy, aby utworzyć rozwiązanie .NET Core za pomocą programu Visual Studio Code.
keywords: .NET, .NET Core, Mac, macOS, Visual Studio Code
author: bleroy
ms.author: mairaw
ms.date: 03/23/2017
ms.topic: get-started-article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 8ad82148-dac8-4b31-9128-b0e9610f4d9b
ms.workload:
- dotnetcore
ms.openlocfilehash: 8c045e5625cee53acc4daa3c9fca524bc953b5a1
ms.sourcegitcommit: 935d5267c44f9bce801468ef95f44572f1417e8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2018
---
# <a name="getting-started-with-net-core-on-macos"></a><span data-ttu-id="f68dc-104">Wprowadzenie do platformy .NET Core na macOS</span><span class="sxs-lookup"><span data-stu-id="f68dc-104">Getting started with .NET Core on macOS</span></span>

<span data-ttu-id="f68dc-105">Ten dokument zawiera kroki i przepływu pracy, aby utworzyć rozwiązanie .NET Core macOS.</span><span class="sxs-lookup"><span data-stu-id="f68dc-105">This document provides the steps and workflow to create a .NET Core solution for macOS.</span></span> <span data-ttu-id="f68dc-106">Informacje o sposobie tworzenia projektów, testy jednostkowe, użyj narzędzi debugowania i dołączyć do nich bibliotek innej firmy za pośrednictwem [NuGet](https://www.nuget.org/).</span><span class="sxs-lookup"><span data-stu-id="f68dc-106">Learn how to create projects, unit tests, use the debugging tools, and incorporate third-party libraries via [NuGet](https://www.nuget.org/).</span></span>

> [!NOTE]
> <span data-ttu-id="f68dc-107">W tym artykule wykorzystano [Visual Studio Code](http://code.visualstudio.com) na macOS.</span><span class="sxs-lookup"><span data-stu-id="f68dc-107">This article uses [Visual Studio Code](http://code.visualstudio.com) on macOS.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="f68dc-108">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="f68dc-108">Prerequisites</span></span>

<span data-ttu-id="f68dc-109">Zainstaluj [.NET Core SDK](https://www.microsoft.com/net/core).</span><span class="sxs-lookup"><span data-stu-id="f68dc-109">Install the [.NET Core SDK](https://www.microsoft.com/net/core).</span></span> <span data-ttu-id="f68dc-110">.NET Core SDK zawiera najnowszą wersję platformy .NET Core framework i środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="f68dc-110">The .NET Core SDK includes the latest release of the .NET Core framework and runtime.</span></span>

<span data-ttu-id="f68dc-111">Zainstaluj [kodu programu Visual Studio](http://code.visualstudio.com).</span><span class="sxs-lookup"><span data-stu-id="f68dc-111">Install [Visual Studio Code](http://code.visualstudio.com).</span></span> <span data-ttu-id="f68dc-112">W trakcie tego artykułu również zainstalować Visual Studio Code wystąpić rozszerzeń zwiększających programowania .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f68dc-112">During the course of this article, you also install Visual Studio Code extensions that improve the .NET Core development experience.</span></span>

<span data-ttu-id="f68dc-113">Zainstaluj rozszerzenie programu Visual Studio kodu C# otwierania Visual Studio Code i naciskając klawisz <kbd>F1</kbd> można otworzyć z programu Visual Studio Code palety.</span><span class="sxs-lookup"><span data-stu-id="f68dc-113">Install the Visual Studio Code C# extension by opening Visual Studio Code and pressing <kbd>F1</kbd> to open the Visual Studio Code palette.</span></span> <span data-ttu-id="f68dc-114">Typ **zainstalować ext** Lista rozszerzeń.</span><span class="sxs-lookup"><span data-stu-id="f68dc-114">Type **ext install** to see the list of extensions.</span></span> <span data-ttu-id="f68dc-115">Wybierz rozszerzenia C#.</span><span class="sxs-lookup"><span data-stu-id="f68dc-115">Select the C# extension.</span></span> <span data-ttu-id="f68dc-116">Ponownie uruchom Visual Studio Code aktywować rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="f68dc-116">Restart Visual Studio Code to activate the extension.</span></span> <span data-ttu-id="f68dc-117">Aby uzyskać więcej informacji, zobacz [dokumentacji programu Visual Studio C# rozszerzeniem kodu](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span><span class="sxs-lookup"><span data-stu-id="f68dc-117">For more information, see the [Visual Studio Code C# Extension documentation](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span></span>

## <a name="getting-started"></a><span data-ttu-id="f68dc-118">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="f68dc-118">Getting started</span></span>

<span data-ttu-id="f68dc-119">W tym samouczku, Utwórz trzy projekty: projektu biblioteki testów dla tego projektu biblioteki, a aplikacja konsolowa, która wykorzystuje biblioteki.</span><span class="sxs-lookup"><span data-stu-id="f68dc-119">In this tutorial, you create three projects: a library project, tests for that library project, and a console application that makes use of the library.</span></span> <span data-ttu-id="f68dc-120">Możesz [wyświetlić lub pobrać źródło](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/golden) dla tego tematu w repozytorium dotnet/docs w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="f68dc-120">You can [view or download the source](https://github.com/dotnet/docs/tree/master/samples/core/getting-started/golden) for this topic at the dotnet/docs repository on GitHub.</span></span> <span data-ttu-id="f68dc-121">Instrukcje pobrania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="f68dc-121">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="f68dc-122">Uruchom kod programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f68dc-122">Start Visual Studio Code.</span></span> <span data-ttu-id="f68dc-123">Naciśnij klawisz <kbd>Ctrl</kbd> + <kbd> \` </kbd> (znak znakami odwróconego lub backtick) lub wybierz **Widok > zintegrowane Terminal** z menu, aby otworzyć osadzonych Terminal w programie Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="f68dc-123">Press <kbd>Ctrl</kbd>+<kbd>\`</kbd> (the backquote or backtick character) or select **View > Integrated Terminal** from the menu to open an embedded terminal in Visual Studio Code.</span></span> <span data-ttu-id="f68dc-124">Nadal można otworzyć zewnętrznego powłoki Eksploratora **Otwórz w wierszu polecenia** polecenia (**Otwórz w terminalu** na Mac lub Linux), jeśli wolisz pracować poza Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="f68dc-124">You can still open an external shell with the Explorer **Open in Command Prompt** command (**Open in Terminal** on Mac or Linux) if you prefer to work outside of Visual Studio Code.</span></span>

<span data-ttu-id="f68dc-125">Rozpocznij od utworzenia pliku rozwiązania, która służy jako kontener dla jednego lub więcej projektów .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f68dc-125">Begin by creating a solution file, which serves as a container for one or more .NET Core projects.</span></span> <span data-ttu-id="f68dc-126">W terminalu, Utwórz *złotego* folder i otwórz folder.</span><span class="sxs-lookup"><span data-stu-id="f68dc-126">In the terminal, create a *golden* folder and open the folder.</span></span> <span data-ttu-id="f68dc-127">Ten folder jest katalogiem głównym rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="f68dc-127">This folder is the root of your solution.</span></span> <span data-ttu-id="f68dc-128">Uruchom [ `dotnet new` ](../tools/dotnet-new.md) polecenie, aby utworzyć nowe rozwiązanie *golden.sln*:</span><span class="sxs-lookup"><span data-stu-id="f68dc-128">Run the [`dotnet new`](../tools/dotnet-new.md) command to create a new solution, *golden.sln*:</span></span>

```console
dotnet new sln
```

<span data-ttu-id="f68dc-129">Z *złotego* folderu, uruchom następujące polecenie, aby utworzyć projekt biblioteki, który tworzy dwa pliki,*library.csproj* i *Class1.cs*, w *biblioteki* folderu:</span><span class="sxs-lookup"><span data-stu-id="f68dc-129">From the *golden* folder, execute the following command to create a library project, which produces two files,*library.csproj* and *Class1.cs*, in the *library* folder:</span></span>

```console
dotnet new classlib -o library
```

<span data-ttu-id="f68dc-130">Wykonanie [ `dotnet sln` ](../tools/dotnet-sln.md) polecenie, aby dodać nowo utworzonego *library.csproj* projektu do rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="f68dc-130">Execute the [`dotnet sln`](../tools/dotnet-sln.md) command to add the newly created *library.csproj* project to the solution:</span></span>

```console
dotnet sln add library/library.csproj
```

<span data-ttu-id="f68dc-131">*Library.csproj* pliku zawiera następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="f68dc-131">The *library.csproj* file contains the following information:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard1.4</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="f68dc-132">Nasze metody biblioteki serializacji i deserializacji obiektów w formacie JSON.</span><span class="sxs-lookup"><span data-stu-id="f68dc-132">Our library methods serialize and deserialize objects in JSON format.</span></span> <span data-ttu-id="f68dc-133">Aby obsługiwać JSON serializacji i deserializacji, Dodaj odwołanie do `Newtonsoft.Json` pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="f68dc-133">To support JSON serialization and deserialization, add a reference to the `Newtonsoft.Json` NuGet package.</span></span> <span data-ttu-id="f68dc-134">`dotnet add` Polecenie dodaje nowe elementy do projektu.</span><span class="sxs-lookup"><span data-stu-id="f68dc-134">The `dotnet add` command adds new items to a project.</span></span> <span data-ttu-id="f68dc-135">Aby dodać odwołanie do pakietu NuGet, użyj [ `dotnet add package` ](../tools/dotnet-add-package.md) polecenia i określ nazwę pakietu:</span><span class="sxs-lookup"><span data-stu-id="f68dc-135">To add a reference to a NuGet package, use the [`dotnet add package`](../tools/dotnet-add-package.md) command and specify the name of the package:</span></span>

```console
dotnet add library package Newtonsoft.Json
```

<span data-ttu-id="f68dc-136">Spowoduje to dodanie `Newtonsoft.Json` i jego zależności do projektu biblioteki.</span><span class="sxs-lookup"><span data-stu-id="f68dc-136">This adds `Newtonsoft.Json` and its dependencies to the library project.</span></span> <span data-ttu-id="f68dc-137">Możesz też ręcznie zmodyfikować *library.csproj* plik i dodać następującego węzła:</span><span class="sxs-lookup"><span data-stu-id="f68dc-137">Alternatively, manually edit the *library.csproj* file and add the following node:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="10.0.1" />
</ItemGroup>
```

<span data-ttu-id="f68dc-138">Wykonanie [ `dotnet restore` ](../tools/dotnet-restore.md), ([patrz Uwaga](#dotnet-restore-note)) która przywraca zależności i tworzy *obj* folder wewnątrz *biblioteki* z trzema pliki w nim, w tym *project.assets.json* pliku:</span><span class="sxs-lookup"><span data-stu-id="f68dc-138">Execute [`dotnet restore`](../tools/dotnet-restore.md), ([see note](#dotnet-restore-note)) which restores dependencies and creates an *obj* folder inside *library* with three files in it, including a *project.assets.json* file:</span></span>

```console
dotnet restore
```

<span data-ttu-id="f68dc-139">W *biblioteki* folder, Zmień nazwę pliku *Class1.cs* do *Thing.cs*.</span><span class="sxs-lookup"><span data-stu-id="f68dc-139">In the *library* folder, rename the file *Class1.cs* to *Thing.cs*.</span></span> <span data-ttu-id="f68dc-140">Zastąp kod z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="f68dc-140">Replace the code with the following:</span></span>

```csharp
using static Newtonsoft.Json.JsonConvert;

namespace Library
{
    public class Thing
    {
        public int Get(int left, int right) =>
            DeserializeObject<int>($"{left + right}");
    }
}
```

<span data-ttu-id="f68dc-141">`Thing` Klasa zawiera jedną metodę publiczne, `Get`, która zwraca sumę dwóch numery, ale wykonuje konwertowanie Suma na ciąg, a następnie podczas deserializacji do liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="f68dc-141">The `Thing` class contains one public method, `Get`, which returns the sum of two numbers but does so by converting the sum into a string and then deserializing it into an integer.</span></span> <span data-ttu-id="f68dc-142">To sprawia, że użycie wiele nowoczesnych C# funkcji, takich jak [ `using static` dyrektywy](../../csharp/language-reference/keywords/using-static.md), [zabudowanych wyrażenia elementów członkowskich](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members), i [ciągu interpolacji](../../csharp/language-reference/tokens/interpolated.md).</span><span class="sxs-lookup"><span data-stu-id="f68dc-142">This makes use of a number of modern C# features, such as [`using static` directives](../../csharp/language-reference/keywords/using-static.md), [expression-bodied members](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members), and [string interpolation](../../csharp/language-reference/tokens/interpolated.md).</span></span>

<span data-ttu-id="f68dc-143">Tworzenie biblioteki z [ `dotnet build` ](../tools/dotnet-build.md) polecenia.</span><span class="sxs-lookup"><span data-stu-id="f68dc-143">Build the library with the [`dotnet build`](../tools/dotnet-build.md) command.</span></span> <span data-ttu-id="f68dc-144">Spowoduje to utworzenie *library.dll* plików w obszarze *golden/library/bin/Debug/netstandard1.4*:</span><span class="sxs-lookup"><span data-stu-id="f68dc-144">This produces a *library.dll* file under *golden/library/bin/Debug/netstandard1.4*:</span></span>

```console
dotnet build
```

## <a name="create-the-test-project"></a><span data-ttu-id="f68dc-145">Tworzenie projektu testu</span><span class="sxs-lookup"><span data-stu-id="f68dc-145">Create the test project</span></span>

<span data-ttu-id="f68dc-146">Tworzenie projektu testu w bibliotece.</span><span class="sxs-lookup"><span data-stu-id="f68dc-146">Build a test project for the library.</span></span> <span data-ttu-id="f68dc-147">Z *złotego* folderu, Utwórz nowy projekt testu:</span><span class="sxs-lookup"><span data-stu-id="f68dc-147">From the *golden* folder, create a new test project:</span></span>

```console
dotnet new xunit -o test-library
```

<span data-ttu-id="f68dc-148">Dodaj projekt testowy do rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="f68dc-148">Add the test project to the solution:</span></span>

```console
dotnet sln add test-library/test-library.csproj
```

<span data-ttu-id="f68dc-149">Dodaj odwołanie do biblioteki, utworzony w poprzedniej sekcji, aby kompilator można znaleźć i używać projektu biblioteki projektu.</span><span class="sxs-lookup"><span data-stu-id="f68dc-149">Add a project reference the library you created in the previous section so that the compiler can find and use the library project.</span></span> <span data-ttu-id="f68dc-150">Użyj [ `dotnet add reference` ](../tools/dotnet-add-reference.md) polecenia:</span><span class="sxs-lookup"><span data-stu-id="f68dc-150">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```console
dotnet add test-library/test-library.csproj reference library/library.csproj
```

<span data-ttu-id="f68dc-151">Możesz też ręcznie zmodyfikować *library.csproj testu* plik i dodać następującego węzła:</span><span class="sxs-lookup"><span data-stu-id="f68dc-151">Alternatively, manually edit the *test-library.csproj* file and add the following node:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\library\library.csproj" />
</ItemGroup>
```

<span data-ttu-id="f68dc-152">Teraz, zależności zostały poprawnie skonfigurowane, należy utworzyć testów w bibliotece.</span><span class="sxs-lookup"><span data-stu-id="f68dc-152">Now that the dependencies have been properly configured, create the tests for your library.</span></span> <span data-ttu-id="f68dc-153">Otwórz *UnitTest1.cs* i zastąp jego zawartość następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="f68dc-153">Open *UnitTest1.cs* and replace its contents with the following code:</span></span>

```csharp
using Library;
using Xunit;

namespace TestApp
{
    public class LibraryTests
    {
        [Fact]
        public void TestThing() {
            Assert.NotEqual(42, new Thing().Get(19, 23));
        }
    }
}
```

<span data-ttu-id="f68dc-154">Należy zwrócić uwagę assert wartość 42 nie jest równa 19 + 23 (lub 42) po pierwszym utworzeniu testu jednostkowego (`Assert.NotEqual`), który zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="f68dc-154">Note that you assert the value 42 is not equal to 19+23 (or 42) when you first create the unit test (`Assert.NotEqual`), which will fail.</span></span> <span data-ttu-id="f68dc-155">Ważnym krokiem podczas tworzenia testów jednostkowych jest tworzenie testu Niepowodzenie po raz pierwszy potwierdzić swojej logiki.</span><span class="sxs-lookup"><span data-stu-id="f68dc-155">An important step in building unit tests is to create the test to fail once first to confirm its logic.</span></span>

<span data-ttu-id="f68dc-156">Z *złotego* folder, wykonaj następujące polecenia:</span><span class="sxs-lookup"><span data-stu-id="f68dc-156">From the *golden* folder, execute the following commands:</span></span>

```console
dotnet restore 
dotnet test test-library/test-library.csproj
```

<span data-ttu-id="f68dc-157">Te polecenia zostaną Znajdź rekursywnie się, że wszystkie projekty, aby przywrócić zależności, je kompilować i aktywować xUnit test runner, aby uruchomić testy.</span><span class="sxs-lookup"><span data-stu-id="f68dc-157">These commands will recursively find all projects to restore dependencies, build them, and activate the xUnit test runner to run the tests.</span></span> <span data-ttu-id="f68dc-158">Pojedynczy test zakończy się niepowodzeniem, zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="f68dc-158">The single test fails, as you expect.</span></span>

<span data-ttu-id="f68dc-159">Edytuj *UnitTest1.cs* plików i zmień potwierdzenia z `Assert.NotEqual` do `Assert.Equal`.</span><span class="sxs-lookup"><span data-stu-id="f68dc-159">Edit the *UnitTest1.cs* file and change the assertion from `Assert.NotEqual` to `Assert.Equal`.</span></span> <span data-ttu-id="f68dc-160">Uruchom następujące polecenie z *złotego* folderu ponowne uruchomienie testu, które przechodzą w tym czasie:</span><span class="sxs-lookup"><span data-stu-id="f68dc-160">Execute the following command from the *golden* folder to re-run the test, which passes this time:</span></span>

```console
dotnet test test-library/test-library.csproj
```

## <a name="create-the-console-app"></a><span data-ttu-id="f68dc-161">Tworzenie aplikacji konsoli</span><span class="sxs-lookup"><span data-stu-id="f68dc-161">Create the console app</span></span>

<span data-ttu-id="f68dc-162">Aplikacja konsoli tworzonych przez następujące kroki przejmuje zależności projektu biblioteki utworzony wcześniej i wywołuje metodę jego biblioteki, gdy jest uruchamiany.</span><span class="sxs-lookup"><span data-stu-id="f68dc-162">The console app you create over the following steps takes a dependency on the library project you created earlier and calls its library method when it runs.</span></span> <span data-ttu-id="f68dc-163">Przy użyciu tego wzorca programowanie, zobaczysz, jak utworzyć wielokrotnego użytku biblioteki dla wielu projektów.</span><span class="sxs-lookup"><span data-stu-id="f68dc-163">Using this pattern of development, you see how to create reusable libraries for multiple projects.</span></span>

<span data-ttu-id="f68dc-164">Utwórz nową aplikację konsoli z *złotego* folderu:</span><span class="sxs-lookup"><span data-stu-id="f68dc-164">Create a new console application from the *golden* folder:</span></span>

```console
dotnet new console -o app
```

<span data-ttu-id="f68dc-165">Dodaj projekt aplikacji konsoli do rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="f68dc-165">Add the console app project to the solution:</span></span>

```console
dotnet sln add app/app.csproj
```

<span data-ttu-id="f68dc-166">Utwórz zależność biblioteki, uruchamiając `dotnet add reference` polecenia:</span><span class="sxs-lookup"><span data-stu-id="f68dc-166">Create the dependency on the library by running the `dotnet add reference` command:</span></span>

```console
dotnet add app/app.csproj reference library/library.csproj
```

<span data-ttu-id="f68dc-167">Uruchom `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) do przywrócenia zależności trzy projekty w rozwiązaniu.</span><span class="sxs-lookup"><span data-stu-id="f68dc-167">Run `dotnet restore` ([see note](#dotnet-restore-note)) to restore the dependencies of the three projects in the solution.</span></span> <span data-ttu-id="f68dc-168">Otwórz *Program.cs* i Zastąp zawartość `Main` metody o następujący wiersz:</span><span class="sxs-lookup"><span data-stu-id="f68dc-168">Open *Program.cs* and replace the contents of the `Main` method with the following line:</span></span>

```csharp
WriteLine($"The answer is {new Thing().Get(19, 23)}");
```

<span data-ttu-id="f68dc-169">Dodaj dwa `using` dyrektywy na początku *Program.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="f68dc-169">Add two `using` directives to the top of the *Program.cs* file:</span></span>

```csharp
using static System.Console;
using Library;
```

<span data-ttu-id="f68dc-170">Wykonaj następujące czynności, `dotnet run` polecenie do uruchomienia pliku wykonywalnego, gdzie `-p` opcji w celu `dotnet run` określa projekt do aplikacji głównej.</span><span class="sxs-lookup"><span data-stu-id="f68dc-170">Execute the following `dotnet run` command to run the executable, where the `-p` option to `dotnet run` specifies the project for the main application.</span></span> <span data-ttu-id="f68dc-171">Aplikacja generuje ciąg "odpowiedź jest 42".</span><span class="sxs-lookup"><span data-stu-id="f68dc-171">The app produces the string "The answer is 42".</span></span>

```console
dotnet run -p app/app.csproj
```

## <a name="debug-the-application"></a><span data-ttu-id="f68dc-172">Debugowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="f68dc-172">Debug the application</span></span>

<span data-ttu-id="f68dc-173">Ustaw punkt przerwania w `WriteLine` instrukcji w `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="f68dc-173">Set a breakpoint at the `WriteLine` statement in the `Main` method.</span></span> <span data-ttu-id="f68dc-174">W tym celu albo naciskając klawisz <kbd>F9</kbd> klucza, gdy kursor znajduje się nad `WriteLine` wiersz lub przez kliknięcie przycisku myszy w lewy margines w wierszu, na którym chcesz ustawić punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="f68dc-174">Do this by either pressing the <kbd>F9</kbd> key when the cursor is over the `WriteLine` line or by clicking the mouse in the left margin on the line where you want to set the breakpoint.</span></span> <span data-ttu-id="f68dc-175">Czerwone koło pojawi się na marginesie obok wiersza kodu.</span><span class="sxs-lookup"><span data-stu-id="f68dc-175">A red circle will appear in the margin next to the line of code.</span></span> <span data-ttu-id="f68dc-176">Po osiągnięciu punktu przerwania wykonywanie kodu zostanie zatrzymane *przed* wiersza punkt przerwania jest wykonywana.</span><span class="sxs-lookup"><span data-stu-id="f68dc-176">When the breakpoint is reached, code execution will stop *before* the breakpoint line is executed.</span></span>

<span data-ttu-id="f68dc-177">Otwórz kartę debugera, wybierając ikonę debugowania na pasku narzędzi Visual Studio Code, wybierając **Widok > debugowania** z paska menu lub za pomocą skrótu klawiaturowego <kbd>CTRL</kbd> + <kbd> SHIFT</kbd>+<kbd>D</kbd>:</span><span class="sxs-lookup"><span data-stu-id="f68dc-177">Open the debugger tab by selecting the Debug icon in the Visual Studio Code toolbar, selecting **View > Debug** from the menu bar, or using the keyboard shortcut <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>D</kbd>:</span></span>

![Visual Studio Code Debugger](./media/using-on-macos/vscodedebugger.png)

<span data-ttu-id="f68dc-179">Naciśnij przycisk Odtwórz, aby uruchomić aplikację w debugerze.</span><span class="sxs-lookup"><span data-stu-id="f68dc-179">Press the Play button to start the application under the debugger.</span></span> <span data-ttu-id="f68dc-180">Rozpoczyna wykonanie i uruchamia punkt przerwania, gdzie zatrzymuje aplikacji.</span><span class="sxs-lookup"><span data-stu-id="f68dc-180">The app begins execution and runs to the breakpoint, where it stops.</span></span> <span data-ttu-id="f68dc-181">Wkrocz `Get` — metoda i upewnij się, że ma przekazano poprawne argumenty.</span><span class="sxs-lookup"><span data-stu-id="f68dc-181">Step into the `Get` method and make sure that you have passed in the correct arguments.</span></span> <span data-ttu-id="f68dc-182">Upewnij się, że odpowiedź jest 42.</span><span class="sxs-lookup"><span data-stu-id="f68dc-182">Confirm that the answer is 42.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
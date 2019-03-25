---
title: Rozpoczynanie pracy z platformą .NET Core w systemie macOS
description: Ten dokument zawiera kroki i przepływ pracy, aby utworzyć rozwiązanie podstawowych platformy .NET przy użyciu programu Visual Studio Code.
author: bleroy
ms.date: 03/23/2017
ms.custom: seodec18
ms.openlocfilehash: e5ac6fa04a2a5001146936de56acafeec7dd895d
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2019
ms.locfileid: "58409500"
---
# <a name="get-started-with-net-core-on-macos"></a><span data-ttu-id="c0bfc-103">Rozpoczynanie pracy z platformą .NET Core w systemie macOS</span><span class="sxs-lookup"><span data-stu-id="c0bfc-103">Get started with .NET Core on macOS</span></span>

<span data-ttu-id="c0bfc-104">Ten dokument zawiera kroki i przepływ pracy, aby utworzyć rozwiązanie platformy .NET Core dla systemu macOS.</span><span class="sxs-lookup"><span data-stu-id="c0bfc-104">This document provides the steps and workflow to create a .NET Core solution for macOS.</span></span> <span data-ttu-id="c0bfc-105">Dowiedz się, jak tworzyć projekty, testy jednostkowe, użyj narzędzi debugowania i zestawowi bibliotek innych firm za pomocą [NuGet](https://www.nuget.org/).</span><span class="sxs-lookup"><span data-stu-id="c0bfc-105">Learn how to create projects, unit tests, use the debugging tools, and incorporate third-party libraries via [NuGet](https://www.nuget.org/).</span></span>

> [!NOTE]
> <span data-ttu-id="c0bfc-106">W tym artykule wykorzystano [programu Visual Studio Code](https://code.visualstudio.com) w systemie macOS.</span><span class="sxs-lookup"><span data-stu-id="c0bfc-106">This article uses [Visual Studio Code](https://code.visualstudio.com) on macOS.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="c0bfc-107">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="c0bfc-107">Prerequisites</span></span>

<span data-ttu-id="c0bfc-108">Zainstaluj [platformy .NET Core SDK](https://www.microsoft.com/net/core).</span><span class="sxs-lookup"><span data-stu-id="c0bfc-108">Install the [.NET Core SDK](https://www.microsoft.com/net/core).</span></span> <span data-ttu-id="c0bfc-109">.NET Core SDK zawiera najnowszą wersję platformy .NET Core framework i środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="c0bfc-109">The .NET Core SDK includes the latest release of the .NET Core framework and runtime.</span></span>

<span data-ttu-id="c0bfc-110">Zainstaluj [programu Visual Studio Code](https://code.visualstudio.com).</span><span class="sxs-lookup"><span data-stu-id="c0bfc-110">Install [Visual Studio Code](https://code.visualstudio.com).</span></span> <span data-ttu-id="c0bfc-111">W trakcie tego artykułu także zainstalować rozszerzenia, które zwiększają programowania .NET Core środowisko Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="c0bfc-111">During the course of this article, you also install Visual Studio Code extensions that improve the .NET Core development experience.</span></span>

<span data-ttu-id="c0bfc-112">Zainstaluj rozszerzenie programu Visual Studio kodu C#, otwierając program Visual Studio Code i naciskając klawisz <kbd>F1</kbd> aby otworzyć paletę programu Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="c0bfc-112">Install the Visual Studio Code C# extension by opening Visual Studio Code and pressing <kbd>F1</kbd> to open the Visual Studio Code palette.</span></span> <span data-ttu-id="c0bfc-113">Typ **zainstalować ext** Aby wyświetlić listę rozszerzeń.</span><span class="sxs-lookup"><span data-stu-id="c0bfc-113">Type **ext install** to see the list of extensions.</span></span> <span data-ttu-id="c0bfc-114">Wybierz rozszerzenie języka C#.</span><span class="sxs-lookup"><span data-stu-id="c0bfc-114">Select the C# extension.</span></span> <span data-ttu-id="c0bfc-115">Uruchom ponownie Visual Studio Code, aby aktywować rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="c0bfc-115">Restart Visual Studio Code to activate the extension.</span></span> <span data-ttu-id="c0bfc-116">Aby uzyskać więcej informacji, zobacz [dokumentację kodu C# rozszerzenie programu Visual Studio](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span><span class="sxs-lookup"><span data-stu-id="c0bfc-116">For more information, see the [Visual Studio Code C# Extension documentation](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span></span>

## <a name="get-started"></a><span data-ttu-id="c0bfc-117">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="c0bfc-117">Get started</span></span>

<span data-ttu-id="c0bfc-118">W tym samouczku utworzysz trzy projekty: projektu biblioteki testów dla tego projektu biblioteki i aplikacji konsoli korzystającej z biblioteki.</span><span class="sxs-lookup"><span data-stu-id="c0bfc-118">In this tutorial, you create three projects: a library project, tests for that library project, and a console application that makes use of the library.</span></span> <span data-ttu-id="c0bfc-119">Możesz [wyświetlić lub pobrać źródło](https://github.com/dotnet/samples/tree/master/core/getting-started/golden) dla tego tematu w repozytorium dotnet/samples w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="c0bfc-119">You can [view or download the source](https://github.com/dotnet/samples/tree/master/core/getting-started/golden) for this topic at the dotnet/samples repository on GitHub.</span></span> <span data-ttu-id="c0bfc-120">Aby uzyskać instrukcje pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="c0bfc-120">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="c0bfc-121">Start Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="c0bfc-121">Start Visual Studio Code.</span></span> <span data-ttu-id="c0bfc-122">Naciśnij klawisz <kbd>Ctrl</kbd> + <kbd> \` </kbd> (znak znakami odwróconego lub początkowych) lub wybierz **Widok > zintegrowany Terminal** z menu aby otworzyć osadzonych w terminalu w programie Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="c0bfc-122">Press <kbd>Ctrl</kbd>+<kbd>\`</kbd> (the backquote or backtick character) or select **View > Integrated Terminal** from the menu to open an embedded terminal in Visual Studio Code.</span></span> <span data-ttu-id="c0bfc-123">Możesz nadal otworzyć powłokę zewnętrznych za pomocą Eksploratora usługi **Otwórz w wierszu polecenia** polecenia (**Otwórz w terminalu** na komputerze Mac lub Linux), jeśli wolisz pracować poza programem Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="c0bfc-123">You can still open an external shell with the Explorer **Open in Command Prompt** command (**Open in Terminal** on Mac or Linux) if you prefer to work outside of Visual Studio Code.</span></span>

<span data-ttu-id="c0bfc-124">Rozpocznij od utworzenia pliku rozwiązania, który służy jako kontener dla jednego lub więcej projektów .NET Core.</span><span class="sxs-lookup"><span data-stu-id="c0bfc-124">Begin by creating a solution file, which serves as a container for one or more .NET Core projects.</span></span> <span data-ttu-id="c0bfc-125">W terminalu Utwórz *złoty* folder i otwórz folder.</span><span class="sxs-lookup"><span data-stu-id="c0bfc-125">In the terminal, create a *golden* folder and open the folder.</span></span> <span data-ttu-id="c0bfc-126">Ten folder jest katalogiem głównym rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="c0bfc-126">This folder is the root of your solution.</span></span> <span data-ttu-id="c0bfc-127">Uruchom [ `dotnet new` ](../tools/dotnet-new.md) polecenie, aby utworzyć nowe rozwiązanie *golden.sln*:</span><span class="sxs-lookup"><span data-stu-id="c0bfc-127">Run the [`dotnet new`](../tools/dotnet-new.md) command to create a new solution, *golden.sln*:</span></span>

```console
dotnet new sln
```

<span data-ttu-id="c0bfc-128">Z *złoty* folder, wykonaj następujące polecenie, aby utworzyć projekt biblioteki, który tworzy dwa pliki,*library.csproj* i *Class1.cs*, w *biblioteki* folderu:</span><span class="sxs-lookup"><span data-stu-id="c0bfc-128">From the *golden* folder, execute the following command to create a library project, which produces two files,*library.csproj* and *Class1.cs*, in the *library* folder:</span></span>

```console
dotnet new classlib -o library
```

<span data-ttu-id="c0bfc-129">Wykonaj [ `dotnet sln` ](../tools/dotnet-sln.md) polecenie, aby dodać nowo utworzonego *library.csproj* projektu do rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="c0bfc-129">Execute the [`dotnet sln`](../tools/dotnet-sln.md) command to add the newly created *library.csproj* project to the solution:</span></span>

```console
dotnet sln add library/library.csproj
```

<span data-ttu-id="c0bfc-130">*Library.csproj* plik zawiera następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="c0bfc-130">The *library.csproj* file contains the following information:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard1.4</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="c0bfc-131">Nasze metody biblioteki serializacji i deserializacji obiektów w formacie JSON.</span><span class="sxs-lookup"><span data-stu-id="c0bfc-131">Our library methods serialize and deserialize objects in JSON format.</span></span> <span data-ttu-id="c0bfc-132">Aby zapewnić obsługę JSON serializacji i deserializacji, Dodaj odwołanie do `Newtonsoft.Json` pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="c0bfc-132">To support JSON serialization and deserialization, add a reference to the `Newtonsoft.Json` NuGet package.</span></span> <span data-ttu-id="c0bfc-133">`dotnet add` Polecenie dodaje nowe elementy do projektu.</span><span class="sxs-lookup"><span data-stu-id="c0bfc-133">The `dotnet add` command adds new items to a project.</span></span> <span data-ttu-id="c0bfc-134">Aby dodać odwołanie do pakietu NuGet, użyj [ `dotnet add package` ](../tools/dotnet-add-package.md) polecenia i określ nazwę pakietu:</span><span class="sxs-lookup"><span data-stu-id="c0bfc-134">To add a reference to a NuGet package, use the [`dotnet add package`](../tools/dotnet-add-package.md) command and specify the name of the package:</span></span>

```console
dotnet add library package Newtonsoft.Json
```

<span data-ttu-id="c0bfc-135">Spowoduje to dodanie `Newtonsoft.Json` i jego zależności do projektu biblioteki.</span><span class="sxs-lookup"><span data-stu-id="c0bfc-135">This adds `Newtonsoft.Json` and its dependencies to the library project.</span></span> <span data-ttu-id="c0bfc-136">Ręcznie Edytuj *library.csproj* pliku i Dodaj następujący węzeł:</span><span class="sxs-lookup"><span data-stu-id="c0bfc-136">Alternatively, manually edit the *library.csproj* file and add the following node:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="10.0.1" />
</ItemGroup>
```

<span data-ttu-id="c0bfc-137">Wykonaj [ `dotnet restore` ](../tools/dotnet-restore.md), ([patrz Uwaga](#dotnet-restore-note)) który przywraca zależności i tworzy *obj* folder wewnątrz *biblioteki* z trzema pliki w nim, w tym *project.assets.json* pliku:</span><span class="sxs-lookup"><span data-stu-id="c0bfc-137">Execute [`dotnet restore`](../tools/dotnet-restore.md), ([see note](#dotnet-restore-note)) which restores dependencies and creates an *obj* folder inside *library* with three files in it, including a *project.assets.json* file:</span></span>

```console
dotnet restore
```

<span data-ttu-id="c0bfc-138">W *biblioteki* folderu, Zmień nazwę pliku *Class1.cs* do *Thing.cs*.</span><span class="sxs-lookup"><span data-stu-id="c0bfc-138">In the *library* folder, rename the file *Class1.cs* to *Thing.cs*.</span></span> <span data-ttu-id="c0bfc-139">Zastąp kod z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="c0bfc-139">Replace the code with the following:</span></span>

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

<span data-ttu-id="c0bfc-140">`Thing` Klasa zawiera jedną metodę publicznych, `Get`, która zwraca sumę dwóch liczby, ale wykonuje konwertowanie sumy w ciąg, a następnie deserializacji na liczbę całkowitą.</span><span class="sxs-lookup"><span data-stu-id="c0bfc-140">The `Thing` class contains one public method, `Get`, which returns the sum of two numbers but does so by converting the sum into a string and then deserializing it into an integer.</span></span> <span data-ttu-id="c0bfc-141">To korzysta z liczbą nowoczesne funkcje języka C#, takie jak [ `using static` dyrektywy](../../csharp/language-reference/keywords/using-static.md), [elementy członkowskie z wyrażeniem](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members), i [Interpolacja ciągów](../../csharp/language-reference/tokens/interpolated.md).</span><span class="sxs-lookup"><span data-stu-id="c0bfc-141">This makes use of a number of modern C# features, such as [`using static` directives](../../csharp/language-reference/keywords/using-static.md), [expression-bodied members](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members), and [string interpolation](../../csharp/language-reference/tokens/interpolated.md).</span></span>

<span data-ttu-id="c0bfc-142">Tworzenie biblioteki za pomocą [ `dotnet build` ](../tools/dotnet-build.md) polecenia.</span><span class="sxs-lookup"><span data-stu-id="c0bfc-142">Build the library with the [`dotnet build`](../tools/dotnet-build.md) command.</span></span> <span data-ttu-id="c0bfc-143">Pozwala to na utworzenie *library.dll* plik *golden/library/bin/Debug/netstandard1.4*:</span><span class="sxs-lookup"><span data-stu-id="c0bfc-143">This produces a *library.dll* file under *golden/library/bin/Debug/netstandard1.4*:</span></span>

```console
dotnet build
```

## <a name="create-the-test-project"></a><span data-ttu-id="c0bfc-144">Utwórz projekt testu</span><span class="sxs-lookup"><span data-stu-id="c0bfc-144">Create the test project</span></span>

<span data-ttu-id="c0bfc-145">Tworzenie projektu testu dla biblioteki.</span><span class="sxs-lookup"><span data-stu-id="c0bfc-145">Build a test project for the library.</span></span> <span data-ttu-id="c0bfc-146">Z *złoty* folderu, Utwórz nowy projekt testu:</span><span class="sxs-lookup"><span data-stu-id="c0bfc-146">From the *golden* folder, create a new test project:</span></span>

```console
dotnet new xunit -o test-library
```

<span data-ttu-id="c0bfc-147">Dodaj projekt testu do rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="c0bfc-147">Add the test project to the solution:</span></span>

```console
dotnet sln add test-library/test-library.csproj
```

<span data-ttu-id="c0bfc-148">Dodaj odwołanie do projektu biblioteki, utworzonego w poprzedniej sekcji, aby kompilator znajdować i używać projektu biblioteki.</span><span class="sxs-lookup"><span data-stu-id="c0bfc-148">Add a project reference the library you created in the previous section so that the compiler can find and use the library project.</span></span> <span data-ttu-id="c0bfc-149">Użyj [ `dotnet add reference` ](../tools/dotnet-add-reference.md) polecenia:</span><span class="sxs-lookup"><span data-stu-id="c0bfc-149">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```console
dotnet add test-library/test-library.csproj reference library/library.csproj
```

<span data-ttu-id="c0bfc-150">Ręcznie Edytuj *library.csproj testu* pliku i Dodaj następujący węzeł:</span><span class="sxs-lookup"><span data-stu-id="c0bfc-150">Alternatively, manually edit the *test-library.csproj* file and add the following node:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\library\library.csproj" />
</ItemGroup>
```

<span data-ttu-id="c0bfc-151">Teraz, gdy zostały poprawnie skonfigurowane zależności, należy utworzyć testy dla biblioteki.</span><span class="sxs-lookup"><span data-stu-id="c0bfc-151">Now that the dependencies have been properly configured, create the tests for your library.</span></span> <span data-ttu-id="c0bfc-152">Otwórz *UnitTest1.cs* i zastąp jego zawartość następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="c0bfc-152">Open *UnitTest1.cs* and replace its contents with the following code:</span></span>

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

<span data-ttu-id="c0bfc-153">Należy pamiętać, asercja wartość 42 nie jest równa 19 + 23 (lub 42) po utworzeniu testu jednostkowego (`Assert.NotEqual`), który zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="c0bfc-153">Note that you assert the value 42 is not equal to 19+23 (or 42) when you first create the unit test (`Assert.NotEqual`), which will fail.</span></span> <span data-ttu-id="c0bfc-154">Ważnym krokiem w tworzeniu testów jednostkowych jest utworzyć test się niepowodzeniem po raz pierwszy potwierdzić swojej logiki.</span><span class="sxs-lookup"><span data-stu-id="c0bfc-154">An important step in building unit tests is to create the test to fail once first to confirm its logic.</span></span>

<span data-ttu-id="c0bfc-155">Z *złoty* folder, wykonaj następujące polecenia:</span><span class="sxs-lookup"><span data-stu-id="c0bfc-155">From the *golden* folder, execute the following commands:</span></span>

```console
dotnet restore 
dotnet test test-library/test-library.csproj
```

<span data-ttu-id="c0bfc-156">Te polecenia zostaną Znajdź rekursywnie wszystkie projekty, aby przywrócić zależności, możesz tworzyć aplikacje i aktywować xUnit uruchamiający testy do uruchomienia testów.</span><span class="sxs-lookup"><span data-stu-id="c0bfc-156">These commands will recursively find all projects to restore dependencies, build them, and activate the xUnit test runner to run the tests.</span></span> <span data-ttu-id="c0bfc-157">Jeden test kończy się niepowodzeniem, zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="c0bfc-157">The single test fails, as you expect.</span></span>

<span data-ttu-id="c0bfc-158">Edytuj *UnitTest1.cs* pliku, a następnie zmień potwierdzenia z `Assert.NotEqual` do `Assert.Equal`.</span><span class="sxs-lookup"><span data-stu-id="c0bfc-158">Edit the *UnitTest1.cs* file and change the assertion from `Assert.NotEqual` to `Assert.Equal`.</span></span> <span data-ttu-id="c0bfc-159">Wykonaj następujące polecenie z *złoty* folder, aby ponownie uruchomić test, który przekazuje teraz:</span><span class="sxs-lookup"><span data-stu-id="c0bfc-159">Execute the following command from the *golden* folder to re-run the test, which passes this time:</span></span>

```console
dotnet test test-library/test-library.csproj
```

## <a name="create-the-console-app"></a><span data-ttu-id="c0bfc-160">Tworzenie aplikacji konsoli</span><span class="sxs-lookup"><span data-stu-id="c0bfc-160">Create the console app</span></span>

<span data-ttu-id="c0bfc-161">Aplikacja konsoli, tworzonych przez następujące kroki przejmuje zależności projektu biblioteki utworzony wcześniej i wywołuje swoją metodę biblioteki, po jego uruchomieniu.</span><span class="sxs-lookup"><span data-stu-id="c0bfc-161">The console app you create over the following steps takes a dependency on the library project you created earlier and calls its library method when it runs.</span></span> <span data-ttu-id="c0bfc-162">Korzystając z tego wzorca, rozwoju, zobaczysz, jak utworzyć biblioteki do ponownego wykorzystania dla wielu projektów.</span><span class="sxs-lookup"><span data-stu-id="c0bfc-162">Using this pattern of development, you see how to create reusable libraries for multiple projects.</span></span>

<span data-ttu-id="c0bfc-163">Utwórz nową aplikację konsoli z *złoty* folderu:</span><span class="sxs-lookup"><span data-stu-id="c0bfc-163">Create a new console application from the *golden* folder:</span></span>

```console
dotnet new console -o app
```

<span data-ttu-id="c0bfc-164">Dodaj projekt aplikacji konsoli w rozwiązaniu:</span><span class="sxs-lookup"><span data-stu-id="c0bfc-164">Add the console app project to the solution:</span></span>

```console
dotnet sln add app/app.csproj
```

<span data-ttu-id="c0bfc-165">Tworzenie zależności w bibliotece, uruchamiając `dotnet add reference` polecenia:</span><span class="sxs-lookup"><span data-stu-id="c0bfc-165">Create the dependency on the library by running the `dotnet add reference` command:</span></span>

```console
dotnet add app/app.csproj reference library/library.csproj
```

<span data-ttu-id="c0bfc-166">Uruchom `dotnet restore` ([patrz Uwaga](#dotnet-restore-note)) do przywrócenia zależności trzy projekty w rozwiązaniu.</span><span class="sxs-lookup"><span data-stu-id="c0bfc-166">Run `dotnet restore` ([see note](#dotnet-restore-note)) to restore the dependencies of the three projects in the solution.</span></span> <span data-ttu-id="c0bfc-167">Otwórz *Program.cs* i Zastąp zawartość `Main` metoda o następujący wiersz:</span><span class="sxs-lookup"><span data-stu-id="c0bfc-167">Open *Program.cs* and replace the contents of the `Main` method with the following line:</span></span>

```csharp
WriteLine($"The answer is {new Thing().Get(19, 23)}");
```

<span data-ttu-id="c0bfc-168">Dodaj dwie `using` dyrektywy do góry *Program.cs* pliku:</span><span class="sxs-lookup"><span data-stu-id="c0bfc-168">Add two `using` directives to the top of the *Program.cs* file:</span></span>

```csharp
using static System.Console;
using Library;
```

<span data-ttu-id="c0bfc-169">Wykonaj następujące czynności, `dotnet run` polecenie do uruchomienia pliku wykonywalnego, gdzie `-p` opcję `dotnet run` określa projekt dla głównej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c0bfc-169">Execute the following `dotnet run` command to run the executable, where the `-p` option to `dotnet run` specifies the project for the main application.</span></span> <span data-ttu-id="c0bfc-170">Aplikacja tworzy ciąg "odpowiedź brzmi 42".</span><span class="sxs-lookup"><span data-stu-id="c0bfc-170">The app produces the string "The answer is 42".</span></span>

```console
dotnet run -p app/app.csproj
```

## <a name="debug-the-application"></a><span data-ttu-id="c0bfc-171">Debugowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="c0bfc-171">Debug the application</span></span>

<span data-ttu-id="c0bfc-172">Ustaw punkt przerwania w `WriteLine` instrukcji w `Main` metody.</span><span class="sxs-lookup"><span data-stu-id="c0bfc-172">Set a breakpoint at the `WriteLine` statement in the `Main` method.</span></span> <span data-ttu-id="c0bfc-173">W tym celu albo naciskając <kbd>F9</kbd> klucza, gdy kursor znajduje się nad `WriteLine` wiersz lub przez kliknięcie przycisku myszy w lewy margines w wierszu, na którym chcesz ustawić punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="c0bfc-173">Do this by either pressing the <kbd>F9</kbd> key when the cursor is over the `WriteLine` line or by clicking the mouse in the left margin on the line where you want to set the breakpoint.</span></span> <span data-ttu-id="c0bfc-174">Na marginesie obok wiersza kodu pojawi się czerwone kółko.</span><span class="sxs-lookup"><span data-stu-id="c0bfc-174">A red circle will appear in the margin next to the line of code.</span></span> <span data-ttu-id="c0bfc-175">Po osiągnięciu punktu przerwania, wykonanie kodu spowoduje zatrzymanie *przed* zostanie wykonany wiersz punktu przerwania.</span><span class="sxs-lookup"><span data-stu-id="c0bfc-175">When the breakpoint is reached, code execution will stop *before* the breakpoint line is executed.</span></span>

<span data-ttu-id="c0bfc-176">Otwórz kartę debuger, wybierając ikonę debugowania na pasku narzędzi programu Visual Studio Code, wybierając **Widok > debugowanie** z paska menu lub za pomocą skrótu klawiaturowego <kbd>CTRL</kbd> + <kbd> SHIFT</kbd>+<kbd>D</kbd>:</span><span class="sxs-lookup"><span data-stu-id="c0bfc-176">Open the debugger tab by selecting the Debug icon in the Visual Studio Code toolbar, selecting **View > Debug** from the menu bar, or using the keyboard shortcut <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>D</kbd>:</span></span>

![Visual Studio Code Debugger](./media/using-on-macos/visual-studio-code-debugger.png)

<span data-ttu-id="c0bfc-178">Naciśnij przycisk Odtwórz, aby uruchomić aplikację w debugerze.</span><span class="sxs-lookup"><span data-stu-id="c0bfc-178">Press the Play button to start the application under the debugger.</span></span> <span data-ttu-id="c0bfc-179">Aplikacja rozpoczyna wykonywanie i uruchamia punkt przerwania, gdzie zatrzymuje.</span><span class="sxs-lookup"><span data-stu-id="c0bfc-179">The app begins execution and runs to the breakpoint, where it stops.</span></span> <span data-ttu-id="c0bfc-180">Wejdź do `Get` metody i upewnij się, że przeszły w poprawne argumenty.</span><span class="sxs-lookup"><span data-stu-id="c0bfc-180">Step into the `Get` method and make sure that you have passed in the correct arguments.</span></span> <span data-ttu-id="c0bfc-181">Upewnij się, że odpowiedź zawiera się 42.</span><span class="sxs-lookup"><span data-stu-id="c0bfc-181">Confirm that the answer is 42.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]
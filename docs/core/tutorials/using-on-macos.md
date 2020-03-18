---
title: 'Samouczek: Tworzenie rozwiązania .NET Core w systemie macOS przy użyciu kodu programu Visual Studio'
description: Ten dokument zawiera kroki i przepływ pracy, aby utworzyć .NET Core Solution przy użyciu kodu programu Visual Studio.
ms.date: 12/19/2019
ms.openlocfilehash: f5da16d413ddc25587ff35550fe9f308dc87f4bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156598"
---
# <a name="tutorial-create-a-net-core-solution-in-macos-using-visual-studio-code"></a><span data-ttu-id="59d90-103">Samouczek: Tworzenie rozwiązania .NET Core w systemie macOS przy użyciu kodu programu Visual Studio</span><span class="sxs-lookup"><span data-stu-id="59d90-103">Tutorial: Create a .NET Core solution in macOS using Visual Studio Code</span></span>

<span data-ttu-id="59d90-104">Ten dokument zawiera kroki i przepływ pracy, aby utworzyć rozwiązanie .NET Core dla systemu macOS.</span><span class="sxs-lookup"><span data-stu-id="59d90-104">This document provides the steps and workflow to create a .NET Core solution for macOS.</span></span> <span data-ttu-id="59d90-105">Dowiedz się, jak tworzyć projekty, testy jednostkowe, używać narzędzi do debugowania i włączać biblioteki innych firm za pośrednictwem [NuGet](https://www.nuget.org/).</span><span class="sxs-lookup"><span data-stu-id="59d90-105">Learn how to create projects, unit tests, use the debugging tools, and incorporate third-party libraries via [NuGet](https://www.nuget.org/).</span></span>

> [!NOTE]
> <span data-ttu-id="59d90-106">W tym artykule [użyto kodu programu Visual Studio](https://code.visualstudio.com) w systemie macOS.</span><span class="sxs-lookup"><span data-stu-id="59d90-106">This article uses [Visual Studio Code](https://code.visualstudio.com) on macOS.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="59d90-107">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="59d90-107">Prerequisites</span></span>

<span data-ttu-id="59d90-108">Zainstaluj zestaw [SDK .NET Core](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="59d90-108">Install the [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span> <span data-ttu-id="59d90-109">Zestaw SDK .NET Core zawiera najnowszą wersję struktury .NET Core i programu runtime.</span><span class="sxs-lookup"><span data-stu-id="59d90-109">The .NET Core SDK includes the latest release of the .NET Core framework and runtime.</span></span>

<span data-ttu-id="59d90-110">Zainstaluj narzędzie [Visual Studio Code](https://code.visualstudio.com).</span><span class="sxs-lookup"><span data-stu-id="59d90-110">Install [Visual Studio Code](https://code.visualstudio.com).</span></span> <span data-ttu-id="59d90-111">W trakcie tego artykułu można również zainstalować rozszerzenia kodu programu Visual Studio, które poprawiają środowisko programistyczne .NET Core.</span><span class="sxs-lookup"><span data-stu-id="59d90-111">During the course of this article, you also install Visual Studio Code extensions that improve the .NET Core development experience.</span></span>

<span data-ttu-id="59d90-112">Zainstaluj rozszerzenie kodu C# programu Visual Studio, otwierając program Visual Studio Code i naciskając klawisz <kbd>Fn</kbd>+<kbd>F1,</kbd> aby otworzyć paletę Kod programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="59d90-112">Install the Visual Studio Code C# extension by opening Visual Studio Code and pressing <kbd>Fn</kbd>+<kbd>F1</kbd> to open the Visual Studio Code palette.</span></span> <span data-ttu-id="59d90-113">Wpisz **instalację ext,** aby wyświetlić listę rozszerzeń.</span><span class="sxs-lookup"><span data-stu-id="59d90-113">Type **ext install** to see the list of extensions.</span></span> <span data-ttu-id="59d90-114">Wybierz rozszerzenie C#.</span><span class="sxs-lookup"><span data-stu-id="59d90-114">Select the C# extension.</span></span> <span data-ttu-id="59d90-115">Uruchom ponownie kod programu Visual Studio, aby aktywować rozszerzenie.</span><span class="sxs-lookup"><span data-stu-id="59d90-115">Restart Visual Studio Code to activate the extension.</span></span> <span data-ttu-id="59d90-116">Aby uzyskać więcej informacji, zobacz [dokumentację rozszerzenia kodu C# programu Visual Studio](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span><span class="sxs-lookup"><span data-stu-id="59d90-116">For more information, see the [Visual Studio Code C# Extension documentation](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span></span>

## <a name="get-started"></a><span data-ttu-id="59d90-117">Rozpoczęcie pracy</span><span class="sxs-lookup"><span data-stu-id="59d90-117">Get started</span></span>

<span data-ttu-id="59d90-118">W tym samouczku utworzysz trzy projekty: projekt biblioteki, testy dla tego projektu biblioteki i aplikację konsoli, która korzysta z biblioteki.</span><span class="sxs-lookup"><span data-stu-id="59d90-118">In this tutorial, you create three projects: a library project, tests for that library project, and a console application that makes use of the library.</span></span> <span data-ttu-id="59d90-119">Możesz [wyświetlić lub pobrać źródło](https://github.com/dotnet/samples/tree/master/core/getting-started/golden) tego artykułu w repozytorium dotnet/samples w usylenie GitHub.</span><span class="sxs-lookup"><span data-stu-id="59d90-119">You can [view or download the source](https://github.com/dotnet/samples/tree/master/core/getting-started/golden) for this article at the dotnet/samples repository on GitHub.</span></span> <span data-ttu-id="59d90-120">Aby uzyskać instrukcje dotyczące pobierania, zobacz [Przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="59d90-120">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="59d90-121">Uruchom program Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="59d90-121">Start Visual Studio Code.</span></span> <span data-ttu-id="59d90-122">Naciśnij <kbd>klawisz Ctrl</kbd> <kbd>\`</kbd> (znak backquote lub backtick) lub wybierz polecenie **Wyświetl** > **terminal** z menu, aby otworzyć osadzony terminal w kodzie programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="59d90-122">Press <kbd>Ctrl</kbd><kbd>\`</kbd> (the backquote or backtick character) or select **View** > **Terminal** from the menu to open an embedded terminal in Visual Studio Code.</span></span> <span data-ttu-id="59d90-123">Nadal można otworzyć powłokę zewnętrzną za pomocą polecenia Explorer **Open in Command Prompt** **(Otwórz w terminalu** w systemie macOS lub Linux), jeśli wolisz pracować poza kodem programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="59d90-123">You can still open an external shell with the Explorer **Open in Command Prompt** command (**Open in Terminal** on macOS or Linux) if you prefer to work outside of Visual Studio Code.</span></span>

<span data-ttu-id="59d90-124">Rozpocznij od utworzenia pliku rozwiązania, który służy jako kontener dla jednego lub więcej projektów programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="59d90-124">Begin by creating a solution file, which serves as a container for one or more .NET Core projects.</span></span> <span data-ttu-id="59d90-125">W terminalu uruchom [`dotnet new`](../tools/dotnet-new.md) polecenie, aby utworzyć nowe rozwiązanie *golden.sln* wewnątrz nowego folderu o nazwie *złoty:*</span><span class="sxs-lookup"><span data-stu-id="59d90-125">In the terminal, run the [`dotnet new`](../tools/dotnet-new.md) command to create a new solution *golden.sln* inside a new folder named *golden*:</span></span>

```dotnetcli
dotnet new sln -o golden
```

<span data-ttu-id="59d90-126">Przejdź do nowego *złotego* folderu i wykonaj następujące polecenie, aby utworzyć projekt biblioteki, który tworzy dwa pliki,*library.csproj* i *Class1.cs*, w folderze *biblioteki:*</span><span class="sxs-lookup"><span data-stu-id="59d90-126">Navigate to the new *golden* folder and execute the following command to create a library project, which produces two files,*library.csproj* and *Class1.cs*, in the *library* folder:</span></span>

```dotnetcli
dotnet new classlib -o library
```

<span data-ttu-id="59d90-127">Wykonaj [`dotnet sln`](../tools/dotnet-sln.md) polecenie, aby dodać nowo utworzony projekt *library.csproj* do rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="59d90-127">Execute the [`dotnet sln`](../tools/dotnet-sln.md) command to add the newly created *library.csproj* project to the solution:</span></span>

```dotnetcli
dotnet sln add library/library.csproj
```

<span data-ttu-id="59d90-128">Plik *library.csproj* zawiera następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="59d90-128">The *library.csproj* file contains the following information:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="59d90-129">Nasze metody biblioteki serializują i deserializują obiekty w formacie JSON.</span><span class="sxs-lookup"><span data-stu-id="59d90-129">Our library methods serialize and deserialize objects in JSON format.</span></span> <span data-ttu-id="59d90-130">Aby obsługiwać serializacji JSON i deserializacji, `Newtonsoft.Json` dodaj odwołanie do pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="59d90-130">To support JSON serialization and deserialization, add a reference to the `Newtonsoft.Json` NuGet package.</span></span> <span data-ttu-id="59d90-131">Polecenie `dotnet add` dodaje nowe elementy do projektu.</span><span class="sxs-lookup"><span data-stu-id="59d90-131">The `dotnet add` command adds new items to a project.</span></span> <span data-ttu-id="59d90-132">Aby dodać odwołanie do pakietu NuGet, użyj [`dotnet add package`](../tools/dotnet-add-package.md) polecenia i określ nazwę pakietu:</span><span class="sxs-lookup"><span data-stu-id="59d90-132">To add a reference to a NuGet package, use the [`dotnet add package`](../tools/dotnet-add-package.md) command and specify the name of the package:</span></span>

```dotnetcli
dotnet add library package Newtonsoft.Json
```

<span data-ttu-id="59d90-133">Spowoduje `Newtonsoft.Json` to dodanie i jego zależności do projektu biblioteki.</span><span class="sxs-lookup"><span data-stu-id="59d90-133">This adds `Newtonsoft.Json` and its dependencies to the library project.</span></span> <span data-ttu-id="59d90-134">Alternatywnie ręcznie zrewiduj plik *library.csproj* i dodaj następujący węzeł:</span><span class="sxs-lookup"><span data-stu-id="59d90-134">Alternatively, manually edit the *library.csproj* file and add the following node:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

<span data-ttu-id="59d90-135">Wykonaj [`dotnet restore`](../tools/dotnet-restore.md),[(patrz uwaga),](#dotnet-restore-note)który przywraca zależności i tworzy folder *obj* wewnątrz *biblioteki* z trzema plikami w nim, w tym plik *project.assets.json:*</span><span class="sxs-lookup"><span data-stu-id="59d90-135">Execute [`dotnet restore`](../tools/dotnet-restore.md), ([see note](#dotnet-restore-note)) which restores dependencies and creates an *obj* folder inside *library* with three files in it, including a *project.assets.json* file:</span></span>

```dotnetcli
dotnet restore
```

<span data-ttu-id="59d90-136">W folderze *biblioteki* zmień nazwę *pliku Class1.cs* na *Thing.cs*.</span><span class="sxs-lookup"><span data-stu-id="59d90-136">In the *library* folder, rename the file *Class1.cs* to *Thing.cs*.</span></span> <span data-ttu-id="59d90-137">Zastąp kod następującymi czynnościami:</span><span class="sxs-lookup"><span data-stu-id="59d90-137">Replace the code with the following:</span></span>

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

<span data-ttu-id="59d90-138">Klasa `Thing` zawiera jedną metodę `Get`publiczną, która zwraca sumę dwóch liczb, ale robi to przez przekonwertowanie sumy na ciąg, a następnie deserializację jej na liczbę całkowitą.</span><span class="sxs-lookup"><span data-stu-id="59d90-138">The `Thing` class contains one public method, `Get`, which returns the sum of two numbers but does so by converting the sum into a string and then deserializing it into an integer.</span></span> <span data-ttu-id="59d90-139">Dzięki temu korzysta z wielu nowoczesnych funkcji Języka C#, takich jak [ `using static` dyrektywy,](../../csharp/language-reference/keywords/using-static.md) [elementy członkowskie zabudowane wyrażeniem](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members)i [interpolacja ciągów.](../../csharp/language-reference/tokens/interpolated.md)</span><span class="sxs-lookup"><span data-stu-id="59d90-139">This makes use of a number of modern C# features, such as [`using static` directives](../../csharp/language-reference/keywords/using-static.md), [expression-bodied members](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members), and [string interpolation](../../csharp/language-reference/tokens/interpolated.md).</span></span>

<span data-ttu-id="59d90-140">Zbuduj [`dotnet build`](../tools/dotnet-build.md) bibliotekę za pomocą polecenia.</span><span class="sxs-lookup"><span data-stu-id="59d90-140">Build the library with the [`dotnet build`](../tools/dotnet-build.md) command.</span></span> <span data-ttu-id="59d90-141">Spowoduje to wygenerowanie pliku *library.dll* pod *golden/library/bin/Debug/netstandard1.4*:</span><span class="sxs-lookup"><span data-stu-id="59d90-141">This produces a *library.dll* file under *golden/library/bin/Debug/netstandard1.4*:</span></span>

```dotnetcli
dotnet build
```

## <a name="create-the-test-project"></a><span data-ttu-id="59d90-142">Tworzenie projektu testowego</span><span class="sxs-lookup"><span data-stu-id="59d90-142">Create the test project</span></span>

<span data-ttu-id="59d90-143">Tworzenie projektu testowego dla biblioteki.</span><span class="sxs-lookup"><span data-stu-id="59d90-143">Build a test project for the library.</span></span> <span data-ttu-id="59d90-144">Ze *złotego* folderu utwórz nowy projekt testowy:</span><span class="sxs-lookup"><span data-stu-id="59d90-144">From the *golden* folder, create a new test project:</span></span>

```dotnetcli
dotnet new xunit -o test-library
```

<span data-ttu-id="59d90-145">Dodaj projekt testowy do rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="59d90-145">Add the test project to the solution:</span></span>

```dotnetcli
dotnet sln add test-library/test-library.csproj
```

<span data-ttu-id="59d90-146">Dodaj odwołanie do projektu biblioteki utworzonej w poprzedniej sekcji, aby kompilator mógł znaleźć i użyć projektu biblioteki.</span><span class="sxs-lookup"><span data-stu-id="59d90-146">Add a project reference the library you created in the previous section so that the compiler can find and use the library project.</span></span> <span data-ttu-id="59d90-147">Użyj [`dotnet add reference`](../tools/dotnet-add-reference.md) polecenia:</span><span class="sxs-lookup"><span data-stu-id="59d90-147">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```dotnetcli
dotnet add test-library/test-library.csproj reference library/library.csproj
```

<span data-ttu-id="59d90-148">Alternatywnie ręcznie edytować plik *test-library.csproj* i dodać następujący węzeł:</span><span class="sxs-lookup"><span data-stu-id="59d90-148">Alternatively, manually edit the *test-library.csproj* file and add the following node:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\library\library.csproj" />
</ItemGroup>
```

<span data-ttu-id="59d90-149">Teraz, gdy zależności zostały poprawnie skonfigurowane, utwórz testy dla biblioteki.</span><span class="sxs-lookup"><span data-stu-id="59d90-149">Now that the dependencies have been properly configured, create the tests for your library.</span></span> <span data-ttu-id="59d90-150">Otwórz *UnitTest1.cs* i zastąp jego zawartość następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="59d90-150">Open *UnitTest1.cs* and replace its contents with the following code:</span></span>

```csharp
using Library;
using Xunit;

namespace TestApp
{
    public class LibraryTests
    {
        [Fact]
        public void TestThing()
        {
            Assert.NotEqual(42, new Thing().Get(19, 23));
        }
    }
}
```

<span data-ttu-id="59d90-151">Należy pamiętać, że wartość 42 nie jest równa 19 +23 (lub 42) podczas pierwszego utworzenia testu jednostkowego (),`Assert.NotEqual`który zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="59d90-151">Note that you assert the value 42 is not equal to 19+23 (or 42) when you first create the unit test (`Assert.NotEqual`), which will fail.</span></span> <span data-ttu-id="59d90-152">Ważnym krokiem w budowaniu testów jednostkowych jest utworzenie testu, który nie powiedzie się po raz pierwszy, aby potwierdzić jego logikę.</span><span class="sxs-lookup"><span data-stu-id="59d90-152">An important step in building unit tests is to create the test to fail once first to confirm its logic.</span></span>

<span data-ttu-id="59d90-153">Ze *złotego* folderu wykonaj następujące polecenia:</span><span class="sxs-lookup"><span data-stu-id="59d90-153">From the *golden* folder, execute the following commands:</span></span>

```dotnetcli
dotnet restore
dotnet test test-library/test-library.csproj
```

<span data-ttu-id="59d90-154">Te polecenia będą rekursywnie znaleźć wszystkie projekty, aby przywrócić zależności, skompilować je i aktywować xUnit test runner do uruchomienia testów.</span><span class="sxs-lookup"><span data-stu-id="59d90-154">These commands will recursively find all projects to restore dependencies, build them, and activate the xUnit test runner to run the tests.</span></span> <span data-ttu-id="59d90-155">Pojedynczy test nie powiedzie się, zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="59d90-155">The single test fails, as you expect.</span></span>

<span data-ttu-id="59d90-156">Edytowanie *pliku UnitTest1.cs* i zmienianie potwierdzenia z `Assert.NotEqual` na `Assert.Equal`.</span><span class="sxs-lookup"><span data-stu-id="59d90-156">Edit the *UnitTest1.cs* file and change the assertion from `Assert.NotEqual` to `Assert.Equal`.</span></span> <span data-ttu-id="59d90-157">Wykonaj następujące polecenie ze *złotego* folderu, aby ponownie uruchomić test, który mija tym razem:</span><span class="sxs-lookup"><span data-stu-id="59d90-157">Execute the following command from the *golden* folder to re-run the test, which passes this time:</span></span>

```dotnetcli
dotnet test test-library/test-library.csproj
```

## <a name="create-the-console-app"></a><span data-ttu-id="59d90-158">Tworzenie aplikacji konsoli</span><span class="sxs-lookup"><span data-stu-id="59d90-158">Create the console app</span></span>

<span data-ttu-id="59d90-159">Aplikacja konsoli, którą utworzysz w następujących krokach, ma zależność od projektu biblioteki utworzonego wcześniej i wywołuje jego metodę biblioteki po uruchomieniu.</span><span class="sxs-lookup"><span data-stu-id="59d90-159">The console app you create over the following steps takes a dependency on the library project you created earlier and calls its library method when it runs.</span></span> <span data-ttu-id="59d90-160">Za pomocą tego wzorca programowania, zobacz, jak utworzyć biblioteki wielokrotnego użytku dla wielu projektów.</span><span class="sxs-lookup"><span data-stu-id="59d90-160">Using this pattern of development, you see how to create reusable libraries for multiple projects.</span></span>

<span data-ttu-id="59d90-161">Utwórz nową aplikację konsoli ze *złotego* folderu:</span><span class="sxs-lookup"><span data-stu-id="59d90-161">Create a new console application from the *golden* folder:</span></span>

```dotnetcli
dotnet new console -o app
```

<span data-ttu-id="59d90-162">Dodaj projekt aplikacji konsoli do rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="59d90-162">Add the console app project to the solution:</span></span>

```dotnetcli
dotnet sln add app/app.csproj
```

<span data-ttu-id="59d90-163">Utwórz zależność od biblioteki, `dotnet add reference` uruchamiając polecenie:</span><span class="sxs-lookup"><span data-stu-id="59d90-163">Create the dependency on the library by running the `dotnet add reference` command:</span></span>

```dotnetcli
dotnet add app/app.csproj reference library/library.csproj
```

<span data-ttu-id="59d90-164">Uruchom `dotnet restore` ([zobacz notatkę),](#dotnet-restore-note)aby przywrócić zależności trzech projektów w rozwiązaniu.</span><span class="sxs-lookup"><span data-stu-id="59d90-164">Run `dotnet restore` ([see note](#dotnet-restore-note)) to restore the dependencies of the three projects in the solution.</span></span> <span data-ttu-id="59d90-165">Otwórz *Program.cs* i zastąp zawartość `Main` metody następującym wierszem:</span><span class="sxs-lookup"><span data-stu-id="59d90-165">Open *Program.cs* and replace the contents of the `Main` method with the following line:</span></span>

```csharp
WriteLine($"The answer is {new Thing().Get(19, 23)}");
```

<span data-ttu-id="59d90-166">Dodaj `using` dwie dyrektywy do górnej części *pliku Program.cs:*</span><span class="sxs-lookup"><span data-stu-id="59d90-166">Add two `using` directives to the top of the *Program.cs* file:</span></span>

```csharp
using static System.Console;
using Library;
```

<span data-ttu-id="59d90-167">Wykonaj następujące `dotnet run` polecenie, aby uruchomić plik `-p` wykonywalny, gdzie opcja `dotnet run` określa projekt dla aplikacji głównej.</span><span class="sxs-lookup"><span data-stu-id="59d90-167">Execute the following `dotnet run` command to run the executable, where the `-p` option to `dotnet run` specifies the project for the main application.</span></span> <span data-ttu-id="59d90-168">Aplikacja tworzy ciąg "Odpowiedź jest 42".</span><span class="sxs-lookup"><span data-stu-id="59d90-168">The app produces the string "The answer is 42".</span></span>

```dotnetcli
dotnet run -p app/app.csproj
```

## <a name="debug-the-application"></a><span data-ttu-id="59d90-169">Debugowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="59d90-169">Debug the application</span></span>

<span data-ttu-id="59d90-170">Ustaw punkt przerwania `WriteLine` w `Main` instrukcji w metodzie.</span><span class="sxs-lookup"><span data-stu-id="59d90-170">Set a breakpoint at the `WriteLine` statement in the `Main` method.</span></span> <span data-ttu-id="59d90-171">Należy to zrobić, naciskając klawisz <kbd>Fn</kbd>+<kbd>F9,</kbd> `WriteLine` gdy kursor znajduje się nad linią, albo klikając myszą na lewym marginesie w wierszu, w którym chcesz ustawić punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="59d90-171">Do this by either pressing the <kbd>Fn</kbd>+<kbd>F9</kbd> key when the cursor is over the `WriteLine` line or by clicking the mouse in the left margin on the line where you want to set the breakpoint.</span></span> <span data-ttu-id="59d90-172">Czerwone kółko pojawi się na marginesie obok wiersza kodu.</span><span class="sxs-lookup"><span data-stu-id="59d90-172">A red circle will appear in the margin next to the line of code.</span></span> <span data-ttu-id="59d90-173">Po osiągnięciu punktu przerwania wykonanie kodu zostanie zatrzymane *przed* wykonaniem linii punktu przerwania.</span><span class="sxs-lookup"><span data-stu-id="59d90-173">When the breakpoint is reached, code execution will stop *before* the breakpoint line is executed.</span></span>

<span data-ttu-id="59d90-174">Otwórz kartę debugera, wybierając ikonę Debugowania na pasku narzędzi Kodu programu Visual Studio, wybierając **pozycję Wyświetl** > **debugowanie** z paska menu lub używając skrótu klawiaturowego <kbd>&#8679;</kbd> <kbd>&#8984;</kbd> <kbd>D:</kbd></span><span class="sxs-lookup"><span data-stu-id="59d90-174">Open the debugger tab by selecting the Debug icon in the Visual Studio Code toolbar, selecting **View** > **Debug** from the menu bar, or using the keyboard shortcut <kbd>&#8679;</kbd><kbd>&#8984;</kbd><kbd>D</kbd>:</span></span>

![Debuger kodu programu Visual Studio](./media/using-on-macos/visual-studio-code-debugger.png)

<span data-ttu-id="59d90-176">Naciśnij przycisk Odtwórz, aby uruchomić aplikację w obszarze debugera.</span><span class="sxs-lookup"><span data-stu-id="59d90-176">Press the Play button to start the application under the debugger.</span></span> <span data-ttu-id="59d90-177">Utworzono zarówno projekt testowy, jak i aplikację w tym projekcie.</span><span class="sxs-lookup"><span data-stu-id="59d90-177">You've created both a test project and an application in this project.</span></span> <span data-ttu-id="59d90-178">Debuger pyta, który projekt chcesz uruchomić.</span><span class="sxs-lookup"><span data-stu-id="59d90-178">The debugger asks which project you want to start.</span></span> <span data-ttu-id="59d90-179">Wybierz projekt "app".</span><span class="sxs-lookup"><span data-stu-id="59d90-179">Select the "app" project.</span></span> <span data-ttu-id="59d90-180">Aplikacja rozpoczyna wykonywanie i działa do punktu przerwania, gdzie zatrzymuje.</span><span class="sxs-lookup"><span data-stu-id="59d90-180">The app begins execution and runs to the breakpoint, where it stops.</span></span> <span data-ttu-id="59d90-181">Krok do `Get` metody i upewnij się, że zostały przekazane w poprawnych argumentów.</span><span class="sxs-lookup"><span data-stu-id="59d90-181">Step into the `Get` method and make sure that you have passed in the correct arguments.</span></span> <span data-ttu-id="59d90-182">Upewnij się, że odpowiedź jest 42.</span><span class="sxs-lookup"><span data-stu-id="59d90-182">Confirm that the answer is 42.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

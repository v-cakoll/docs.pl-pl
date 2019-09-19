---
title: 'Samouczek: Tworzenie rozwiązania .NET Core w macOS przy użyciu Visual Studio Code'
description: Ten dokument zawiera instrukcje i przepływ pracy służące do tworzenia rozwiązania platformy .NET Core przy użyciu Visual Studio Code.
ms.date: 03/23/2017
ms.custom: seodec18
ms.openlocfilehash: 5df43ae235b9fd901a65f7f8898bec67e24de682
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117365"
---
# <a name="tutorial-create-a-net-core-solution-in-macos-using-visual-studio-code"></a><span data-ttu-id="65a06-103">Samouczek: Tworzenie rozwiązania .NET Core w macOS przy użyciu Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="65a06-103">Tutorial: Create a .NET Core solution in macOS using Visual Studio Code</span></span>

<span data-ttu-id="65a06-104">Ten dokument zawiera kroki i przepływ pracy służące do tworzenia rozwiązania .NET Core dla macOS.</span><span class="sxs-lookup"><span data-stu-id="65a06-104">This document provides the steps and workflow to create a .NET Core solution for macOS.</span></span> <span data-ttu-id="65a06-105">Dowiedz się, jak tworzyć projekty, testy jednostkowe, korzystać z narzędzi debugowania i dołączać biblioteki innych firm za pośrednictwem programu [NuGet](https://www.nuget.org/).</span><span class="sxs-lookup"><span data-stu-id="65a06-105">Learn how to create projects, unit tests, use the debugging tools, and incorporate third-party libraries via [NuGet](https://www.nuget.org/).</span></span>

> [!NOTE]
> <span data-ttu-id="65a06-106">W tym artykule [Visual Studio Code](https://code.visualstudio.com) w programie macOS.</span><span class="sxs-lookup"><span data-stu-id="65a06-106">This article uses [Visual Studio Code](https://code.visualstudio.com) on macOS.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="65a06-107">Wymagania wstępne</span><span class="sxs-lookup"><span data-stu-id="65a06-107">Prerequisites</span></span>

<span data-ttu-id="65a06-108">Zainstaluj [zestaw .NET Core SDK](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="65a06-108">Install the [.NET Core SDK](https://dotnet.microsoft.com/download).</span></span> <span data-ttu-id="65a06-109">Zestaw .NET Core SDK zawiera najnowszą wersję programu .NET Core Framework i środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="65a06-109">The .NET Core SDK includes the latest release of the .NET Core framework and runtime.</span></span>

<span data-ttu-id="65a06-110">Zainstaluj [Visual Studio Code](https://code.visualstudio.com).</span><span class="sxs-lookup"><span data-stu-id="65a06-110">Install [Visual Studio Code](https://code.visualstudio.com).</span></span> <span data-ttu-id="65a06-111">W trakcie tego artykułu są również instalowane Visual Studio Code rozszerzenia, które zwiększają możliwości programistyczne programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="65a06-111">During the course of this article, you also install Visual Studio Code extensions that improve the .NET Core development experience.</span></span>

<span data-ttu-id="65a06-112">Zainstaluj rozszerzenie Visual Studio Code C# , otwierając Visual Studio Code i naciskając klawisz <kbd>F1</kbd> , aby otworzyć paletę Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="65a06-112">Install the Visual Studio Code C# extension by opening Visual Studio Code and pressing <kbd>F1</kbd> to open the Visual Studio Code palette.</span></span> <span data-ttu-id="65a06-113">Wpisz **EXT Install** , aby wyświetlić listę rozszerzeń.</span><span class="sxs-lookup"><span data-stu-id="65a06-113">Type **ext install** to see the list of extensions.</span></span> <span data-ttu-id="65a06-114">Wybierz C# rozszerzenie.</span><span class="sxs-lookup"><span data-stu-id="65a06-114">Select the C# extension.</span></span> <span data-ttu-id="65a06-115">Uruchom ponownie Visual Studio Code, aby aktywować rozszerzenie.</span><span class="sxs-lookup"><span data-stu-id="65a06-115">Restart Visual Studio Code to activate the extension.</span></span> <span data-ttu-id="65a06-116">Aby uzyskać więcej informacji, zobacz [dokumentację C# rozszerzenia Visual Studio Code](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span><span class="sxs-lookup"><span data-stu-id="65a06-116">For more information, see the [Visual Studio Code C# Extension documentation](https://github.com/OmniSharp/omnisharp-vscode/blob/master/debugger.md).</span></span>

## <a name="get-started"></a><span data-ttu-id="65a06-117">Wprowadzenie</span><span class="sxs-lookup"><span data-stu-id="65a06-117">Get started</span></span>

<span data-ttu-id="65a06-118">W tym samouczku utworzysz trzy projekty: projekt biblioteki, testy dla tego projektu biblioteki oraz aplikację konsolową, która używa biblioteki.</span><span class="sxs-lookup"><span data-stu-id="65a06-118">In this tutorial, you create three projects: a library project, tests for that library project, and a console application that makes use of the library.</span></span> <span data-ttu-id="65a06-119">Możesz [wyświetlić lub pobrać źródło](https://github.com/dotnet/samples/tree/master/core/getting-started/golden) tego tematu w repozytorium dotnet/Samples w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="65a06-119">You can [view or download the source](https://github.com/dotnet/samples/tree/master/core/getting-started/golden) for this topic at the dotnet/samples repository on GitHub.</span></span> <span data-ttu-id="65a06-120">Aby uzyskać instrukcje dotyczące pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span><span class="sxs-lookup"><span data-stu-id="65a06-120">For download instructions, see [Samples and Tutorials](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).</span></span>

<span data-ttu-id="65a06-121">Rozpocznij Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="65a06-121">Start Visual Studio Code.</span></span> <span data-ttu-id="65a06-122">Naciśnij klawisz <kbd>Ctrl</kbd> + <kbd>\`</kbd> (znak cudzysłowu lub nadmiaru) lub wybierz opcję **Wyświetl > zintegrowany terminal** z menu, aby otworzyć osadzony terminal w Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="65a06-122">Press <kbd>Ctrl</kbd>+<kbd>\`</kbd> (the backquote or backtick character) or select **View > Integrated Terminal** from the menu to open an embedded terminal in Visual Studio Code.</span></span> <span data-ttu-id="65a06-123">Można nadal otworzyć powłokę zewnętrzną za pomocą Eksploratora **Otwórz w wierszu polecenia** (**Otwórz w terminalu** na komputerach Mac lub Linux), jeśli wolisz pracować poza Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="65a06-123">You can still open an external shell with the Explorer **Open in Command Prompt** command (**Open in Terminal** on Mac or Linux) if you prefer to work outside of Visual Studio Code.</span></span>

<span data-ttu-id="65a06-124">Zacznij od utworzenia pliku rozwiązania, który służy jako kontener dla co najmniej jednego projektu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="65a06-124">Begin by creating a solution file, which serves as a container for one or more .NET Core projects.</span></span> <span data-ttu-id="65a06-125">W terminalu uruchom [`dotnet new`](../tools/dotnet-new.md) polecenie, aby utworzyć nowe rozwiązanie *złot. sln* w nowym folderze o nazwie *złota*:</span><span class="sxs-lookup"><span data-stu-id="65a06-125">In the terminal, run the [`dotnet new`](../tools/dotnet-new.md) command to create a new solution *golden.sln* inside a new folder named *golden*:</span></span>

```dotnetcli
dotnet new sln -o golden
```

<span data-ttu-id="65a06-126">Przejdź do nowego folderu *złota* i wykonaj następujące polecenie, aby utworzyć projekt biblioteki, który tworzy dwa pliki,*Library. csproj* i *Class1.cs*, w folderze *Library* :</span><span class="sxs-lookup"><span data-stu-id="65a06-126">Navigate to the new *golden* folder and execute the following command to create a library project, which produces two files,*library.csproj* and *Class1.cs*, in the *library* folder:</span></span>

```dotnetcli
dotnet new classlib -o library
```

<span data-ttu-id="65a06-127">Wykonaj polecenie, aby dodać nowo utworzony projekt *Library. csproj* do rozwiązania: [`dotnet sln`](../tools/dotnet-sln.md)</span><span class="sxs-lookup"><span data-stu-id="65a06-127">Execute the [`dotnet sln`](../tools/dotnet-sln.md) command to add the newly created *library.csproj* project to the solution:</span></span>

```dotnetcli
dotnet sln add library/library.csproj
```

<span data-ttu-id="65a06-128">Plik *Library. csproj* zawiera następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="65a06-128">The *library.csproj* file contains the following information:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="65a06-129">Nasze metody biblioteki serializacji i deserializacji obiektów w formacie JSON.</span><span class="sxs-lookup"><span data-stu-id="65a06-129">Our library methods serialize and deserialize objects in JSON format.</span></span> <span data-ttu-id="65a06-130">Aby zapewnić obsługę serializacji i deserializacji JSON, Dodaj odwołanie do `Newtonsoft.Json` pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="65a06-130">To support JSON serialization and deserialization, add a reference to the `Newtonsoft.Json` NuGet package.</span></span> <span data-ttu-id="65a06-131">`dotnet add` Polecenie dodaje nowe elementy do projektu.</span><span class="sxs-lookup"><span data-stu-id="65a06-131">The `dotnet add` command adds new items to a project.</span></span> <span data-ttu-id="65a06-132">Aby dodać odwołanie do pakietu NuGet, użyj [`dotnet add package`](../tools/dotnet-add-package.md) polecenia i określ nazwę pakietu:</span><span class="sxs-lookup"><span data-stu-id="65a06-132">To add a reference to a NuGet package, use the [`dotnet add package`](../tools/dotnet-add-package.md) command and specify the name of the package:</span></span>

```dotnetcli
dotnet add library package Newtonsoft.Json
```

<span data-ttu-id="65a06-133">Powoduje to `Newtonsoft.Json` dodanie i jego zależności do projektu biblioteki.</span><span class="sxs-lookup"><span data-stu-id="65a06-133">This adds `Newtonsoft.Json` and its dependencies to the library project.</span></span> <span data-ttu-id="65a06-134">Alternatywnie możesz ręcznie edytować plik *Library. csproj* i dodać następujący węzeł:</span><span class="sxs-lookup"><span data-stu-id="65a06-134">Alternatively, manually edit the *library.csproj* file and add the following node:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Newtonsoft.Json" Version="12.0.2" />
</ItemGroup>
```

<span data-ttu-id="65a06-135">Wykonaj [`dotnet restore`](../tools/dotnet-restore.md), ([patrz Uwaga](#dotnet-restore-note)), która przywraca zależności i tworzy folder *obj* w *bibliotece* zawierającej trzy pliki, w tym plik *Project. assets. JSON* :</span><span class="sxs-lookup"><span data-stu-id="65a06-135">Execute [`dotnet restore`](../tools/dotnet-restore.md), ([see note](#dotnet-restore-note)) which restores dependencies and creates an *obj* folder inside *library* with three files in it, including a *project.assets.json* file:</span></span>

```dotnetcli
dotnet restore
```

<span data-ttu-id="65a06-136">W folderze *Biblioteka* Zmień nazwę pliku *Class1.cs* na *Thing.cs*.</span><span class="sxs-lookup"><span data-stu-id="65a06-136">In the *library* folder, rename the file *Class1.cs* to *Thing.cs*.</span></span> <span data-ttu-id="65a06-137">Zastąp kod następującym:</span><span class="sxs-lookup"><span data-stu-id="65a06-137">Replace the code with the following:</span></span>

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

<span data-ttu-id="65a06-138">Klasa zawiera jedną `Get`metodę publiczną, która zwraca sumę dwóch liczb, ale robi to, konwertując sumę na ciąg, a następnie deserializacji go do liczby całkowitej. `Thing`</span><span class="sxs-lookup"><span data-stu-id="65a06-138">The `Thing` class contains one public method, `Get`, which returns the sum of two numbers but does so by converting the sum into a string and then deserializing it into an integer.</span></span> <span data-ttu-id="65a06-139">Dzięki temu można korzystać z wielu C# nowoczesnych funkcji, takich jak [ `using static` dyrektywy](../../csharp/language-reference/keywords/using-static.md), [składowe wyrażeń](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members)i [interpolacji ciągów](../../csharp/language-reference/tokens/interpolated.md).</span><span class="sxs-lookup"><span data-stu-id="65a06-139">This makes use of a number of modern C# features, such as [`using static` directives](../../csharp/language-reference/keywords/using-static.md), [expression-bodied members](../../csharp/whats-new/csharp-7.md#more-expression-bodied-members), and [string interpolation](../../csharp/language-reference/tokens/interpolated.md).</span></span>

<span data-ttu-id="65a06-140">Skompiluj bibliotekę za pomocą [`dotnet build`](../tools/dotnet-build.md) polecenia.</span><span class="sxs-lookup"><span data-stu-id="65a06-140">Build the library with the [`dotnet build`](../tools/dotnet-build.md) command.</span></span> <span data-ttu-id="65a06-141">Spowoduje to utworzenie pliku *Library. dll* w obszarze *złota/Library/bin/debug/standard 1.4*:</span><span class="sxs-lookup"><span data-stu-id="65a06-141">This produces a *library.dll* file under *golden/library/bin/Debug/netstandard1.4*:</span></span>

```dotnetcli
dotnet build
```

## <a name="create-the-test-project"></a><span data-ttu-id="65a06-142">Utwórz projekt testu</span><span class="sxs-lookup"><span data-stu-id="65a06-142">Create the test project</span></span>

<span data-ttu-id="65a06-143">Kompiluj projekt testowy dla biblioteki.</span><span class="sxs-lookup"><span data-stu-id="65a06-143">Build a test project for the library.</span></span> <span data-ttu-id="65a06-144">W folderze *złota* Utwórz nowy projekt testowy:</span><span class="sxs-lookup"><span data-stu-id="65a06-144">From the *golden* folder, create a new test project:</span></span>

```dotnetcli
dotnet new xunit -o test-library
```

<span data-ttu-id="65a06-145">Dodaj projekt testowy do rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="65a06-145">Add the test project to the solution:</span></span>

```dotnetcli
dotnet sln add test-library/test-library.csproj
```

<span data-ttu-id="65a06-146">Dodaj odwołanie do projektu biblioteki utworzonej w poprzedniej sekcji, aby kompilator mógł znaleźć i użyć projektu biblioteki.</span><span class="sxs-lookup"><span data-stu-id="65a06-146">Add a project reference the library you created in the previous section so that the compiler can find and use the library project.</span></span> <span data-ttu-id="65a06-147">[`dotnet add reference`](../tools/dotnet-add-reference.md) Użyj polecenia:</span><span class="sxs-lookup"><span data-stu-id="65a06-147">Use the [`dotnet add reference`](../tools/dotnet-add-reference.md) command:</span></span>

```dotnetcli
dotnet add test-library/test-library.csproj reference library/library.csproj
```

<span data-ttu-id="65a06-148">Alternatywnie możesz ręcznie edytować plik *test-library. csproj* i dodać następujący węzeł:</span><span class="sxs-lookup"><span data-stu-id="65a06-148">Alternatively, manually edit the *test-library.csproj* file and add the following node:</span></span>

```xml
<ItemGroup>
  <ProjectReference Include="..\library\library.csproj" />
</ItemGroup>
```

<span data-ttu-id="65a06-149">Teraz, po poprawnym skonfigurowaniu zależności, należy utworzyć testy dla biblioteki.</span><span class="sxs-lookup"><span data-stu-id="65a06-149">Now that the dependencies have been properly configured, create the tests for your library.</span></span> <span data-ttu-id="65a06-150">Otwórz *UnitTest1.cs* i Zastąp jego zawartość następującym kodem:</span><span class="sxs-lookup"><span data-stu-id="65a06-150">Open *UnitTest1.cs* and replace its contents with the following code:</span></span>

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

<span data-ttu-id="65a06-151">Należy pamiętać, że wartość 42 nie jest równa 19 + 23 (lub 42) podczas pierwszego utworzenia testu jednostkowego (`Assert.NotEqual`), który zakończy się niepowodzeniem.</span><span class="sxs-lookup"><span data-stu-id="65a06-151">Note that you assert the value 42 is not equal to 19+23 (or 42) when you first create the unit test (`Assert.NotEqual`), which will fail.</span></span> <span data-ttu-id="65a06-152">Ważnym krokiem podczas tworzenia testów jednostkowych jest utworzenie testu, aby zakończyć się niepowodzeniem raz w pierwszej kolejności w celu potwierdzenia jego logiki.</span><span class="sxs-lookup"><span data-stu-id="65a06-152">An important step in building unit tests is to create the test to fail once first to confirm its logic.</span></span>

<span data-ttu-id="65a06-153">W folderze *złota* wykonaj następujące polecenia:</span><span class="sxs-lookup"><span data-stu-id="65a06-153">From the *golden* folder, execute the following commands:</span></span>

```dotnetcli
dotnet restore 
dotnet test test-library/test-library.csproj
```

<span data-ttu-id="65a06-154">Te polecenia spowodują cykliczne wyszukiwanie wszystkich projektów w celu przywrócenia zależności, kompilowania ich i aktywowania modułu uruchamiającego testy xUnit w celu uruchomienia testów.</span><span class="sxs-lookup"><span data-stu-id="65a06-154">These commands will recursively find all projects to restore dependencies, build them, and activate the xUnit test runner to run the tests.</span></span> <span data-ttu-id="65a06-155">Pojedynczy test kończy się niepowodzeniem, zgodnie z oczekiwaniami.</span><span class="sxs-lookup"><span data-stu-id="65a06-155">The single test fails, as you expect.</span></span>

<span data-ttu-id="65a06-156">Edytuj plik *UnitTest1.cs* i Zmień potwierdzenie z `Assert.NotEqual` na. `Assert.Equal`</span><span class="sxs-lookup"><span data-stu-id="65a06-156">Edit the *UnitTest1.cs* file and change the assertion from `Assert.NotEqual` to `Assert.Equal`.</span></span> <span data-ttu-id="65a06-157">Wykonaj następujące polecenie w folderze *złota* , aby ponownie uruchomić test, co przebiega w tym czasie:</span><span class="sxs-lookup"><span data-stu-id="65a06-157">Execute the following command from the *golden* folder to re-run the test, which passes this time:</span></span>

```dotnetcli
dotnet test test-library/test-library.csproj
```

## <a name="create-the-console-app"></a><span data-ttu-id="65a06-158">Tworzenie aplikacji konsolowej</span><span class="sxs-lookup"><span data-stu-id="65a06-158">Create the console app</span></span>

<span data-ttu-id="65a06-159">Aplikacja konsolowa utworzona w ramach następujących kroków przyjmuje zależność od projektu biblioteki utworzonego wcześniej i wywołuje jego metodę biblioteki podczas jej uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="65a06-159">The console app you create over the following steps takes a dependency on the library project you created earlier and calls its library method when it runs.</span></span> <span data-ttu-id="65a06-160">Korzystając z tego wzorca rozwoju, można zobaczyć, jak utworzyć biblioteki wielokrotnego użytku dla wielu projektów.</span><span class="sxs-lookup"><span data-stu-id="65a06-160">Using this pattern of development, you see how to create reusable libraries for multiple projects.</span></span>

<span data-ttu-id="65a06-161">Utwórz nową aplikację konsolową z folderu *złota* :</span><span class="sxs-lookup"><span data-stu-id="65a06-161">Create a new console application from the *golden* folder:</span></span>

```dotnetcli
dotnet new console -o app
```

<span data-ttu-id="65a06-162">Dodaj projekt aplikacji konsoli do rozwiązania:</span><span class="sxs-lookup"><span data-stu-id="65a06-162">Add the console app project to the solution:</span></span>

```dotnetcli
dotnet sln add app/app.csproj
```

<span data-ttu-id="65a06-163">Utwórz zależność od biblioteki, uruchamiając `dotnet add reference` polecenie:</span><span class="sxs-lookup"><span data-stu-id="65a06-163">Create the dependency on the library by running the `dotnet add reference` command:</span></span>

```dotnetcli
dotnet add app/app.csproj reference library/library.csproj
```

<span data-ttu-id="65a06-164">Uruchom `dotnet restore` ([Zobacz Uwaga](#dotnet-restore-note)), aby przywrócić zależności trzech projektów w rozwiązaniu.</span><span class="sxs-lookup"><span data-stu-id="65a06-164">Run `dotnet restore` ([see note](#dotnet-restore-note)) to restore the dependencies of the three projects in the solution.</span></span> <span data-ttu-id="65a06-165">Otwórz *program.cs* i Zastąp zawartość `Main` metody następującym wierszem:</span><span class="sxs-lookup"><span data-stu-id="65a06-165">Open *Program.cs* and replace the contents of the `Main` method with the following line:</span></span>

```csharp
WriteLine($"The answer is {new Thing().Get(19, 23)}");
```

<span data-ttu-id="65a06-166">Dodaj dwie `using` dyrektywy na początku pliku *program.cs* :</span><span class="sxs-lookup"><span data-stu-id="65a06-166">Add two `using` directives to the top of the *Program.cs* file:</span></span>

```csharp
using static System.Console;
using Library;
```

<span data-ttu-id="65a06-167">Wykonaj następujące `dotnet run` polecenie, aby uruchomić plik wykonywalny, `-p` gdzie opcja `dotnet run` określa projekt głównej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="65a06-167">Execute the following `dotnet run` command to run the executable, where the `-p` option to `dotnet run` specifies the project for the main application.</span></span> <span data-ttu-id="65a06-168">Aplikacja tworzy ciąg "odpowiedź to 42".</span><span class="sxs-lookup"><span data-stu-id="65a06-168">The app produces the string "The answer is 42".</span></span>

```dotnetcli
dotnet run -p app/app.csproj
```

## <a name="debug-the-application"></a><span data-ttu-id="65a06-169">Debugowanie aplikacji</span><span class="sxs-lookup"><span data-stu-id="65a06-169">Debug the application</span></span>

<span data-ttu-id="65a06-170">Ustaw punkt przerwania `WriteLine` w instrukcji `Main` w metodzie.</span><span class="sxs-lookup"><span data-stu-id="65a06-170">Set a breakpoint at the `WriteLine` statement in the `Main` method.</span></span> <span data-ttu-id="65a06-171">W tym celu należy nacisnąć klawisz <kbd>F9</kbd> , gdy kursor znajduje się nad `WriteLine` wierszem lub klikając myszą w lewym marginesie w wierszu, w którym ma zostać ustawiony punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="65a06-171">Do this by either pressing the <kbd>F9</kbd> key when the cursor is over the `WriteLine` line or by clicking the mouse in the left margin on the line where you want to set the breakpoint.</span></span> <span data-ttu-id="65a06-172">Czerwony okrąg zostanie wyświetlony na marginesie obok wiersza kodu.</span><span class="sxs-lookup"><span data-stu-id="65a06-172">A red circle will appear in the margin next to the line of code.</span></span> <span data-ttu-id="65a06-173">Po osiągnięciu punktu przerwania wykonywanie kodu zostanie zatrzymane *przed* wykonaniem wiersza punktu przerwania.</span><span class="sxs-lookup"><span data-stu-id="65a06-173">When the breakpoint is reached, code execution will stop *before* the breakpoint line is executed.</span></span>

<span data-ttu-id="65a06-174">Otwórz kartę debuger, wybierając ikonę debugowania na pasku narzędzi Visual Studio Code, wybierając pozycję **Wyświetl > Debuguj** z paska menu lub za pomocą skrótu klawiaturowego <kbd>Ctrl</kbd>+<kbd>SHIFT</kbd>+<kbd>D</kbd>:</span><span class="sxs-lookup"><span data-stu-id="65a06-174">Open the debugger tab by selecting the Debug icon in the Visual Studio Code toolbar, selecting **View > Debug** from the menu bar, or using the keyboard shortcut <kbd>CTRL</kbd>+<kbd>SHIFT</kbd>+<kbd>D</kbd>:</span></span>

![Visual Studio Code Debugger](./media/using-on-macos/visual-studio-code-debugger.png)

<span data-ttu-id="65a06-176">Naciśnij przycisk Odtwórz, aby uruchomić aplikację w debugerze.</span><span class="sxs-lookup"><span data-stu-id="65a06-176">Press the Play button to start the application under the debugger.</span></span> <span data-ttu-id="65a06-177">Aplikacja rozpoczyna wykonywanie i uruchamia do punktu przerwania, w którym jest zatrzymana.</span><span class="sxs-lookup"><span data-stu-id="65a06-177">The app begins execution and runs to the breakpoint, where it stops.</span></span> <span data-ttu-id="65a06-178">Przejdź do `Get` metody i upewnij się, że zostały przekazane poprawne argumenty.</span><span class="sxs-lookup"><span data-stu-id="65a06-178">Step into the `Get` method and make sure that you have passed in the correct arguments.</span></span> <span data-ttu-id="65a06-179">Upewnij się, że odpowiedź to 42.</span><span class="sxs-lookup"><span data-stu-id="65a06-179">Confirm that the answer is 42.</span></span>

<a name="dotnet-restore-note"></a>
[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

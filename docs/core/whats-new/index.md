---
title: Co to jest nowa w programie .NET Core 2.0
description: Więcej informacji na temat nowych funkcji .NET Core.
author: rpetrusha
ms.author: ronpet
ms.date: 08/13/2017
ms.openlocfilehash: 5990afc8671457f5a54c5f31245d87ca2aa106b1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="whats-new-in-net-core"></a><span data-ttu-id="41a78-103">Co to jest nowa w programie .NET Core</span><span class="sxs-lookup"><span data-stu-id="41a78-103">What's new in .NET Core</span></span>

<span data-ttu-id="41a78-104">.NET core 2.0 zawiera nowych funkcji i rozszerzeń w następujących obszarach:</span><span class="sxs-lookup"><span data-stu-id="41a78-104">.NET Core 2.0 includes enhancements and new features in the following areas:</span></span>

- [<span data-ttu-id="41a78-105">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="41a78-105">Tooling</span></span>](#tooling)
- [<span data-ttu-id="41a78-106">Obsługa języków</span><span class="sxs-lookup"><span data-stu-id="41a78-106">Language support</span></span>](#language-support)
- [<span data-ttu-id="41a78-107">Ulepszenia platformy</span><span class="sxs-lookup"><span data-stu-id="41a78-107">Platform improvements</span></span>](#platform-improvements)
- [<span data-ttu-id="41a78-108">Zmiany interfejsu API</span><span class="sxs-lookup"><span data-stu-id="41a78-108">API changes</span></span>](#api-changes-and-library-support)
- [<span data-ttu-id="41a78-109">Integracja z programem Visual Studio</span><span class="sxs-lookup"><span data-stu-id="41a78-109">Visual Studio integration</span></span>](#visual-studio-integration)
- [<span data-ttu-id="41a78-110">Ulepszenia dokumentacji</span><span class="sxs-lookup"><span data-stu-id="41a78-110">Documentation improvements</span></span>](#documentation-improvements)

## <a name="tooling"></a><span data-ttu-id="41a78-111">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="41a78-111">Tooling</span></span>

### <a name="dotnet-restore-runs-implicitly"></a><span data-ttu-id="41a78-112">Przywracanie DotNet uruchamia się domyślnie</span><span class="sxs-lookup"><span data-stu-id="41a78-112">dotnet restore runs implicitly</span></span>

<span data-ttu-id="41a78-113">W poprzednich wersjach programu .NET Core, trzeba było uruchomić [przywracania dotnet](../tools/dotnet-restore.md) polecenie, aby pobrać zależności natychmiast, po utworzeniu nowego projektu z [dotnet nowe](../tools/dotnet-new.md) polecenia, a także zawsze, gdy zostanie dodano nową zależność do projektu.</span><span class="sxs-lookup"><span data-stu-id="41a78-113">In previous versions of .NET Core, you had to run the [dotnet restore](../tools/dotnet-restore.md) command to download dependencies immediately after you created a new project with the [dotnet new](../tools/dotnet-new.md) command, as well as whenever you added a new dependency to your project.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="41a78-114">Można także wyłączyć automatyczne wywoływanie `dotnet restore` przez przekazanie `--no-restore` przełączyć się do `new`, `run`, `build`, `publish`, `pack`, i `test` poleceń.</span><span class="sxs-lookup"><span data-stu-id="41a78-114">You can also disable the automatic invocation of `dotnet restore` by passing the `--no-restore` switch to the `new`, `run`, `build`, `publish`, `pack`, and `test` commands.</span></span> 

### <a name="retargeting-to-net-core-20"></a><span data-ttu-id="41a78-115">Przekierowania do platformy .NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="41a78-115">Retargeting to .NET Core 2.0</span></span>

<span data-ttu-id="41a78-116">Po zainstalowaniu programu .NET Core 2.0 SDK projekty który docelowe .NET Core 1.x cel może zostać zmieniony na .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="41a78-116">If the .NET Core 2.0 SDK is installed, projects that target .NET Core 1.x can be retargeted to .NET Core 2.0.</span></span>

<span data-ttu-id="41a78-117">Aby przekierować .NET Core 2.0, należy edytować plik projektu, zmieniając wartość `<TargetFramework>` elementu (lub `<TargetFrameworks>` elementu, jeśli masz więcej niż jeden element docelowy w pliku projektu) z 1.x 2.0:</span><span class="sxs-lookup"><span data-stu-id="41a78-117">To retarget to .NET Core 2.0, edit your project file by changing the value of the `<TargetFramework>` element (or the `<TargetFrameworks>` element if you have more than one target in your project file) from 1.x to 2.0:</span></span>

```xml
<PropertyGroup>
    <TargetFramework>netcoreapp2.0</TargetFramework>
 </PropertyGroup>
```

<span data-ttu-id="41a78-118">Można również przekierować .NET standardowych bibliotek .NET 2.0 standardowe taki sam sposób:</span><span class="sxs-lookup"><span data-stu-id="41a78-118">You can also retarget .NET Standard libraries to .NET Standard 2.0 the same way:</span></span>

```xml
<PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
 </PropertyGroup>
```

<span data-ttu-id="41a78-119">Aby uzyskać więcej informacji na temat migracji projektu do .NET Core 2.0, zobacz [migracji z platformy ASP.NET Core 1.x do składnika ASP.NET 2.0 Core](/aspnet/core/migration/1x-to-2x/index).</span><span class="sxs-lookup"><span data-stu-id="41a78-119">For more information about migrating your project to .NET Core 2.0, see [Migrating from ASP.NET Core 1.x to ASP.NET Core 2.0](/aspnet/core/migration/1x-to-2x/index).</span></span>

## <a name="language-support"></a><span data-ttu-id="41a78-120">Obsługa języków</span><span class="sxs-lookup"><span data-stu-id="41a78-120">Language support</span></span>

<span data-ttu-id="41a78-121">Oprócz obsługi języka C# i F #, .NET Core 2.0 obsługuje również Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="41a78-121">In addition to supporting C# and F#, .NET Core 2.0 also supports Visual Basic.</span></span>

### <a name="visual-basic"></a><span data-ttu-id="41a78-122">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="41a78-122">Visual Basic</span></span>

<span data-ttu-id="41a78-123">W wersji 2.0 .NET Core obsługuje teraz 2017 Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="41a78-123">With version 2.0, .NET Core now supports Visual Basic 2017.</span></span> <span data-ttu-id="41a78-124">Visual Basic umożliwia tworzenie następujących projektów:</span><span class="sxs-lookup"><span data-stu-id="41a78-124">You can use Visual Basic to create the following project types:</span></span>

- <span data-ttu-id="41a78-125">Aplikacje konsoli platformy .NET core</span><span class="sxs-lookup"><span data-stu-id="41a78-125">.NET Core console apps</span></span>
- <span data-ttu-id="41a78-126">Biblioteki klas .NET core</span><span class="sxs-lookup"><span data-stu-id="41a78-126">.NET Core class libraries</span></span>
- <span data-ttu-id="41a78-127">Biblioteki klas .NET standard</span><span class="sxs-lookup"><span data-stu-id="41a78-127">.NET Standard class libraries</span></span>
- <span data-ttu-id="41a78-128">Projektów testów jednostkowych dla .NET core</span><span class="sxs-lookup"><span data-stu-id="41a78-128">.NET Core unit test projects</span></span>
- <span data-ttu-id="41a78-129">Projekty testowe xUnit .NET core</span><span class="sxs-lookup"><span data-stu-id="41a78-129">.NET Core xUnit test projects</span></span>

<span data-ttu-id="41a78-130">Na przykład do utworzenia aplikacji programu Visual Basic "Hello World", wykonaj następujące kroki w wierszu polecenia:</span><span class="sxs-lookup"><span data-stu-id="41a78-130">For example, to create a Visual Basic "Hello World" application, do the following steps from the command line:</span></span>

1. <span data-ttu-id="41a78-131">Otwórz okno konsoli, Utwórz katalog projektu i stał się bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="41a78-131">Open a console window, create a directory for your project, and make it the current directory.</span></span>

1. <span data-ttu-id="41a78-132">Wprowadź polecenie `dotnet new console -lang vb`.</span><span class="sxs-lookup"><span data-stu-id="41a78-132">Enter the command `dotnet new console -lang vb`.</span></span>

   <span data-ttu-id="41a78-133">Polecenie tworzy plik projektu o `.vbproj` pliku rozszerzenie, wraz z pliku kodu źródłowego języka Visual Basic o nazwie *Program.vb*.</span><span class="sxs-lookup"><span data-stu-id="41a78-133">The command creates a project file with a `.vbproj` file extension, along with a Visual Basic source code file named *Program.vb*.</span></span> <span data-ttu-id="41a78-134">Ten plik zawiera kod źródłowy, aby zapisać ciąg "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="41a78-134">This file contains the source code to write the string "Hello World!"</span></span> <span data-ttu-id="41a78-135">w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="41a78-135">to the console window.</span></span>

1.  <span data-ttu-id="41a78-136">Wprowadź polecenie `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="41a78-136">Enter the command `dotnet run`.</span></span> <span data-ttu-id="41a78-137">[Narzędzi interfejsu wiersza polecenia platformy .NET Core](../tools/index.md) automatycznie Kompiluj i wykonywanie aplikacji, która wyświetla komunikat "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="41a78-137">The [.NET Core CLI tools](../tools/index.md) automatically compile and execute the application, which displays the message "Hello World!"</span></span> <span data-ttu-id="41a78-138">w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="41a78-138">in the console window.</span></span>

### <a name="support-for-c-71"></a><span data-ttu-id="41a78-139">Obsługa języka C# 7.1</span><span class="sxs-lookup"><span data-stu-id="41a78-139">Support for C# 7.1</span></span>

<span data-ttu-id="41a78-140">.NET core 2.0 obsługuje 7.1 C#, który dodaje szereg nowych funkcji, w tym:</span><span class="sxs-lookup"><span data-stu-id="41a78-140">.NET Core 2.0 supports C# 7.1, which adds a number of new features, including:</span></span>

- <span data-ttu-id="41a78-141">`Main` Metody punktu wejścia aplikacji, można oznaczyć z [async](../../csharp/language-reference/keywords/async.md) — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="41a78-141">The `Main` method, the application entry point, can be marked with the [async](../../csharp/language-reference/keywords/async.md) keyword.</span></span>
- <span data-ttu-id="41a78-142">Wywnioskować nazwy spójnej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="41a78-142">Inferred tuple names.</span></span>
- <span data-ttu-id="41a78-143">Domyślne wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="41a78-143">Default expressions.</span></span>

<!-- For more information see [link to C# what's new](url). -->

## <a name="platform-improvements"></a><span data-ttu-id="41a78-144">Ulepszenia platformy</span><span class="sxs-lookup"><span data-stu-id="41a78-144">Platform improvements</span></span>

<span data-ttu-id="41a78-145">.NET core 2.0 obejmuje kilka funkcji, które ułatwiają Zainstaluj oprogramowanie .NET Core i używać go na obsługiwanych systemów operacyjnych.</span><span class="sxs-lookup"><span data-stu-id="41a78-145">.NET Core 2.0 includes a number of features that make it easier to install .NET Core and to use it on supported operating systems.</span></span>

### <a name="net-core-for-linux-is-a-single-implementation"></a><span data-ttu-id="41a78-146">Oprogramowanie .NET core dla systemu Linux jest pojedynczą implementacją</span><span class="sxs-lookup"><span data-stu-id="41a78-146">.NET Core for Linux is a single implementation</span></span>

<span data-ttu-id="41a78-147">.NET core 2.0 oferuje pojedynczej implementacji systemu Linux, który działa na wielu dystrybucje systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="41a78-147">.NET Core 2.0 offers a single Linux implementation that works on multiple Linux distributions.</span></span> <span data-ttu-id="41a78-148">Oprogramowanie .NET core 1.x wymagane pobranie implementacji Linux specyficzne dla dystrybucji.</span><span class="sxs-lookup"><span data-stu-id="41a78-148">.NET Core 1.x required that you download a distribution-specific Linux implementation.</span></span>

<span data-ttu-id="41a78-149">Można również tworzyć aplikacji przeznaczonych dla systemu Linux jako jeden system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="41a78-149">You can also develop apps that target Linux as a single operating system.</span></span> <span data-ttu-id="41a78-150">Oprogramowanie .NET core 1.x wymagane oddzielnie target każdej dystrybucji systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="41a78-150">.NET Core 1.x required that you target each Linux distribution separately.</span></span>

### <a name="support-for-the-apple-cryptographic-libraries"></a><span data-ttu-id="41a78-151">Obsługa bibliotek kryptograficznych firmy Apple</span><span class="sxs-lookup"><span data-stu-id="41a78-151">Support for the Apple cryptographic libraries</span></span>

<span data-ttu-id="41a78-152">Oprogramowanie .NET core 1.x na macOS wymagane kryptograficznych biblioteki OpenSSL zestawu narzędzi.</span><span class="sxs-lookup"><span data-stu-id="41a78-152">.NET Core 1.x on macOS required the OpenSSL toolkit's cryptographic library.</span></span> <span data-ttu-id="41a78-153">.NET core 2.0 korzysta z bibliotek kryptograficznych firmy Apple i nie wymaga biblioteki OpenSSL, więc nie trzeba go zainstalować.</span><span class="sxs-lookup"><span data-stu-id="41a78-153">.NET Core 2.0 uses the Apple cryptographic libraries and doesn't require OpenSSL, so you no longer need to install it.</span></span>

## <a name="api-changes-and-library-support"></a><span data-ttu-id="41a78-154">Zmiany interfejsu API i obsługa biblioteki</span><span class="sxs-lookup"><span data-stu-id="41a78-154">API changes and library support</span></span>

### <a name="support-for-net-standard-20"></a><span data-ttu-id="41a78-155">Obsługa .NET 2.0 standardowe</span><span class="sxs-lookup"><span data-stu-id="41a78-155">Support for .NET Standard 2.0</span></span>

<span data-ttu-id="41a78-156">.NET Standard definiuje wersjonowany zestaw interfejsów API, które muszą być dostępne na implementacje .NET, które są zgodne z tą wersją standardowego.</span><span class="sxs-lookup"><span data-stu-id="41a78-156">The .NET Standard defines a versioned set of APIs that must be available on .NET implementations that comply with that version of the standard.</span></span> <span data-ttu-id="41a78-157">.NET Standard jest przeznaczona dla deweloperów biblioteki.</span><span class="sxs-lookup"><span data-stu-id="41a78-157">The .NET Standard is targeted at library developers.</span></span> <span data-ttu-id="41a78-158">Ma on zagwarantowanie funkcje, które są dostępne w bibliotece, przeznaczonego dla wersji platformy .NET Standard w każdej implementacji .NET.</span><span class="sxs-lookup"><span data-stu-id="41a78-158">It aims to guarantee the functionality that is available to a library that targets a version of the .NET Standard on each .NET implementation.</span></span> <span data-ttu-id="41a78-159">Oprogramowanie .NET core 1.x obsługuje standardowe .NET w wersji 1.6, .NET Core 2.0 obsługuje najnowszą wersję platformy .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="41a78-159">.NET Core 1.x supports the .NET Standard version 1.6; .NET Core 2.0 supports the latest version, .NET Standard 2.0.</span></span> <span data-ttu-id="41a78-160">Aby uzyskać więcej informacji, zobacz [.NET Standard](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="41a78-160">For more information, see [.NET Standard](../../standard/net-standard.md).</span></span>

<span data-ttu-id="41a78-161">.NET 2.0 standardowe zawiera ponad 20 000 API więcej niż były dostępne w wersji 1.6 standardowe .NET.</span><span class="sxs-lookup"><span data-stu-id="41a78-161">.NET Standard 2.0 includes over 20,000 more APIs than were available in the .NET Standard 1.6.</span></span> <span data-ttu-id="41a78-162">Większość to rozwinięte powierzchni wyników zawierających interfejsów API, które są wspólne dla programu .NET Framework i platformy Xamarin w .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="41a78-162">Much of this expanded surface area results from incorporating APIs that are common to the .NET Framework and Xamarin into .NET Standard.</span></span>

<span data-ttu-id="41a78-163">Biblioteki klas .NET 2.0 standardowych można także odwoływać bibliotek klas .NET Framework, pod warunkiem, że wywołują interfejsów API, które znajdują się w standardowe .NET 2.0.</span><span class="sxs-lookup"><span data-stu-id="41a78-163">.NET Standard 2.0 class libraries can also reference .NET Framework class libraries, provided that they call APIs that are present in the .NET Standard 2.0.</span></span> <span data-ttu-id="41a78-164">Nie ponowną kompilację biblioteki .NET Framework jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="41a78-164">No recompilation of the .NET Framework libraries is required.</span></span>

<span data-ttu-id="41a78-165">Aby uzyskać listę interfejsów API, które zostały dodane do .NET Standard od jej ostatniej wersji 1.6 standardowe .NET, zobacz [.NET 2.0 standardowe vs. 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span><span class="sxs-lookup"><span data-stu-id="41a78-165">For a list of the APIs that have been added to the .NET Standard since its last version, the .NET Standard 1.6, see [.NET Standard 2.0 vs. 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span></span>

### <a name="expanded-surface-area"></a><span data-ttu-id="41a78-166">Rozszerzona powierzchni</span><span class="sxs-lookup"><span data-stu-id="41a78-166">Expanded surface area</span></span>

<span data-ttu-id="41a78-167">Całkowita liczba interfejsami API dostępnymi w programie .NET Core 2.0 ma więcej niż podwójny porównaniu .NET Core 1.1.</span><span class="sxs-lookup"><span data-stu-id="41a78-167">The total number of APIs available on .NET Core 2.0 has more than doubled in comparison with .NET Core 1.1.</span></span>

<span data-ttu-id="41a78-168">I [pakiet zgodności systemu Windows](../porting/windows-compat-pack.md) eksportowanie z .NET Framework stała się znacznie prostsze.</span><span class="sxs-lookup"><span data-stu-id="41a78-168">And with the [Windows Compatibility Pack](../porting/windows-compat-pack.md) porting from .NET Framework has also become much simpler.</span></span>

### <a name="support-for-net-framework-libraries"></a><span data-ttu-id="41a78-169">Obsługa bibliotek .NET Framework</span><span class="sxs-lookup"><span data-stu-id="41a78-169">Support for .NET Framework libraries</span></span>

<span data-ttu-id="41a78-170">Kodu platformy .NET core można odwoływać się do istniejących bibliotek .NET Framework, w tym istniejących pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="41a78-170">.NET Core code can reference existing .NET Framework libraries, including existing NuGet packages.</span></span> <span data-ttu-id="41a78-171">Należy pamiętać, że biblioteki muszą używać interfejsów API, które znajdują się w .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="41a78-171">Note that the libraries must use APIs that are found in .NET Standard.</span></span>

## <a name="visual-studio-integration"></a><span data-ttu-id="41a78-172">integracja z programem Visual Studio</span><span class="sxs-lookup"><span data-stu-id="41a78-172">Visual Studio integration</span></span>

<span data-ttu-id="41a78-173">Visual Studio 2017 wersji 15.3 i w niektórych przypadkach program Visual Studio for Mac oferują szereg znaczące ulepszenia dla deweloperów platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="41a78-173">Visual Studio 2017 version 15.3 and in some cases Visual Studio for Mac offer a number of significant enhancements for .NET Core developers.</span></span>

### <a name="retargeting-net-core-apps-and-net-standard-libraries"></a><span data-ttu-id="41a78-174">Przekierowania aplikacji .NET Core i bibliotek .NET Standard</span><span class="sxs-lookup"><span data-stu-id="41a78-174">Retargeting .NET Core apps and .NET Standard libraries</span></span>

<span data-ttu-id="41a78-175">Po zainstalowaniu programu .NET Core 2.0 SDK można przekierować projektów 1.x .NET Core .NET Core 2.0 i .NET Standard 1.x bibliotek .NET 2.0 standardowe.</span><span class="sxs-lookup"><span data-stu-id="41a78-175">If the .NET Core 2.0 SDK is installed, you can retarget .NET Core 1.x projects to .NET Core 2.0 and .NET Standard 1.x libraries to .NET Standard 2.0.</span></span>

<span data-ttu-id="41a78-176">Aby przekierować projektu w programie Visual Studio, możesz otworzyć **aplikacji** okna dialogowego właściwości projektu i Zmień na karcie **platformy docelowej** do wartości **.NET Core 2.0** lub **.NET 2.0 standardowe**.</span><span class="sxs-lookup"><span data-stu-id="41a78-176">To retarget your project in Visual Studio, you open the **Application** tab of the project's properties dialog and change the **Target framework** value to **.NET Core 2.0** or **.NET Standard 2.0**.</span></span> <span data-ttu-id="41a78-177">Można także zmienić go prawym przyciskiem myszy projekt i wybierając **Edytuj \*pliku .csproj** opcji.</span><span class="sxs-lookup"><span data-stu-id="41a78-177">You can also change it by right-clicking on the project and selecting the **Edit \*.csproj file** option.</span></span> <span data-ttu-id="41a78-178">Aby uzyskać więcej informacji, zobacz [narzędzi](#tooling) wcześniej w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="41a78-178">For more information, see the [Tooling](#tooling) section earlier in this topic.</span></span>

### <a name="live-unit-testing-support-for-net-core"></a><span data-ttu-id="41a78-179">Obsługa funkcji Live Unit Testing dla platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="41a78-179">Live Unit Testing support for .NET Core</span></span>

<span data-ttu-id="41a78-180">Przy każdej modyfikacji kodu na żywo testów jednostkowych automatycznie uruchamia wszystkie testy jednostkowe wykorzystywanych w tle i wyświetla wyniki i pokrycie kodu na żywo w środowisku Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="41a78-180">Whenever you modify your code, Live Unit Testing automatically runs any affected unit tests in the background and displays the results and code coverage live in the Visual Studio environment.</span></span> <span data-ttu-id="41a78-181">.NET core 2.0 obsługuje teraz Live testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="41a78-181">.NET Core 2.0 now supports Live Unit Testing.</span></span> <span data-ttu-id="41a78-182">Wcześniej testów jednostkowych Live była dostępna tylko w przypadku aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="41a78-182">Previously, Live Unit Testing was available only for .NET Framework applications.</span></span>

<span data-ttu-id="41a78-183">Aby uzyskać więcej informacji, zobacz [Live testów jednostkowych z programu Visual Studio 2017](/visualstudio/test/live-unit-testing) i [Live jednostki testowania — często zadawane pytania](/visualstudio/test/live-unit-testing-faq).</span><span class="sxs-lookup"><span data-stu-id="41a78-183">For more information, see [Live Unit Testing with Visual Studio 2017](/visualstudio/test/live-unit-testing) and the [Live Unit Testing FAQ](/visualstudio/test/live-unit-testing-faq).</span></span>

### <a name="better-support-for-multiple-target-frameworks"></a><span data-ttu-id="41a78-184">Lepszą obsługę wielu platform docelowych</span><span class="sxs-lookup"><span data-stu-id="41a78-184">Better support for multiple target frameworks</span></span>

<span data-ttu-id="41a78-185">Jeśli tworzysz projekt dla wielu struktur docelowych, można wybierać platformy docelowej z menu najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="41a78-185">If you're building a project for multiple target frameworks, you can now select the target platform from the top-level menu.</span></span> <span data-ttu-id="41a78-186">Na poniższej ilustracji projektu o nazwie SCD1 jest przeznaczony dla 64-bitowych Mac OS X 10.11 (`osx.10.11-x64`) i 64-bitowego systemu Windows 10/Windows Server 2016 (`win10-x64`).</span><span class="sxs-lookup"><span data-stu-id="41a78-186">In the following figure, a project named SCD1 targets 64-bit Mac OS X 10.11 (`osx.10.11-x64`) and 64-bit Windows 10/Windows Server 2016 (`win10-x64`).</span></span> <span data-ttu-id="41a78-187">Przed wybraniem przycisku projektu, w tym przypadku do uruchomienia kompilacji debugowania, możesz wybrać platformy docelowej.</span><span class="sxs-lookup"><span data-stu-id="41a78-187">You can select the target framework before selecting the project button, in this case to run a debug build.</span></span>

![Wybieranie platformy docelowej podczas kompilowania projektu](media/multitarget.png)

### <a name="side-by-side-support-for-net-core-sdks"></a><span data-ttu-id="41a78-189">Obsługa Side-by-side .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="41a78-189">Side-by-side support for .NET Core SDKs</span></span>

<span data-ttu-id="41a78-190">Teraz można zainstalować zestawu SDK .NET Core niezależnie od programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="41a78-190">You can now install the .NET Core SDK independently of Visual Studio.</span></span> <span data-ttu-id="41a78-191">Umożliwia jednej wersji programu Visual Studio do tworzenia projektów tego docelowego różne wersje programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="41a78-191">This makes it possible for a single version of Visual Studio to build projects that target different versions of .NET Core.</span></span> <span data-ttu-id="41a78-192">Wcześniej Visual Studio i .NET Core SDK są ściśle powiązane; określonej wersji zestawu SDK wraz z określoną wersją programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="41a78-192">Previously, Visual Studio and the .NET Core SDK were tightly coupled; a particular version of the SDK accompanied a particular version of Visual Studio.</span></span>

## <a name="documentation-improvements"></a><span data-ttu-id="41a78-193">Ulepszenia dokumentacji</span><span class="sxs-lookup"><span data-stu-id="41a78-193">Documentation improvements</span></span>

### <a name="net-application-architecture"></a><span data-ttu-id="41a78-194">Architektura aplikacji .NET</span><span class="sxs-lookup"><span data-stu-id="41a78-194">.NET Application Architecture</span></span>

<span data-ttu-id="41a78-195">[Architektura aplikacji .NET](https://www.microsoft.com/net/learn/architecture) zapewnia dostęp do zestawu książek e, które zawierają wskazówki, najlepsze rozwiązania i przykładowe aplikacje, gdy przy użyciu platformy .NET do kompilacji:</span><span class="sxs-lookup"><span data-stu-id="41a78-195">[.NET Application Architecture](https://www.microsoft.com/net/learn/architecture) gives you access to a set of e-books that provide guidance, best practices, and sample applications when using .NET to build:</span></span>

- <span data-ttu-id="41a78-196">Kontenery Mikrousług i Docker.</span><span class="sxs-lookup"><span data-stu-id="41a78-196">Microservices and Docker containers.</span></span>
- <span data-ttu-id="41a78-197">Aplikacje sieci Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="41a78-197">Web applications with ASP.NET.</span></span>
- <span data-ttu-id="41a78-198">Aplikacje mobilne z platformą Xamarin.</span><span class="sxs-lookup"><span data-stu-id="41a78-198">Mobile applications with Xamarin.</span></span>
- <span data-ttu-id="41a78-199">Aplikacje, które są wdrażane w chmurze platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="41a78-199">Applications that are deployed to the Cloud with Azure.</span></span>

## <a name="see-also"></a><span data-ttu-id="41a78-200">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="41a78-200">See also</span></span>
 [<span data-ttu-id="41a78-201">Co to jest nowe w programie ASP.NET 2.0 Core</span><span class="sxs-lookup"><span data-stu-id="41a78-201">What's new in ASP.NET Core 2.0</span></span>](/aspnet/core/aspnetcore-2.0)

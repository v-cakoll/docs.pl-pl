---
title: Co to jest nowa w programie .NET Core 2.0
description: Więcej informacji na temat nowych funkcji .NET Core.
keywords: .NET, .NET core
author: rpetrusha
ms.author: ronpet
ms.date: 08/13/2017
ms.topic: article
ms.prod: .net-core
ms.workload:
- dotnetcore
ms.openlocfilehash: 749f0502b5c80ed3d6b81d2036e7591e3f1fe08a
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="whats-new-in-net-core"></a><span data-ttu-id="4ba32-104">Co to jest nowa w programie .NET Core</span><span class="sxs-lookup"><span data-stu-id="4ba32-104">What's new in .NET Core</span></span>

<span data-ttu-id="4ba32-105">.NET core 2.0 zawiera nowych funkcji i rozszerzeń w następujących obszarach:</span><span class="sxs-lookup"><span data-stu-id="4ba32-105">.NET Core 2.0 includes enhancements and new features in the following areas:</span></span>

- [<span data-ttu-id="4ba32-106">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="4ba32-106">Tooling</span></span>](#tooling)
- [<span data-ttu-id="4ba32-107">Obsługa języków</span><span class="sxs-lookup"><span data-stu-id="4ba32-107">Language support</span></span>](#language-support)
- [<span data-ttu-id="4ba32-108">Ulepszenia platformy</span><span class="sxs-lookup"><span data-stu-id="4ba32-108">Platform improvements</span></span>](#platform-improvements)
- [<span data-ttu-id="4ba32-109">Zmiany interfejsu API</span><span class="sxs-lookup"><span data-stu-id="4ba32-109">API changes</span></span>](#api-changes-and-library-support)
- [<span data-ttu-id="4ba32-110">Integracja z programem Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4ba32-110">Visual Studio integration</span></span>](#visual-studio-integration)
- [<span data-ttu-id="4ba32-111">Ulepszenia dokumentacji</span><span class="sxs-lookup"><span data-stu-id="4ba32-111">Documentation improvements</span></span>](#documentation-improvements)

## <a name="tooling"></a><span data-ttu-id="4ba32-112">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="4ba32-112">Tooling</span></span>

### <a name="dotnet-restore-runs-implicitly"></a><span data-ttu-id="4ba32-113">Przywracanie DotNet uruchamia się domyślnie</span><span class="sxs-lookup"><span data-stu-id="4ba32-113">dotnet restore runs implicitly</span></span>

<span data-ttu-id="4ba32-114">W poprzednich wersjach programu .NET Core, trzeba było uruchomić [przywracania dotnet](../tools/dotnet-restore.md) polecenie, aby pobrać zależności natychmiast, po utworzeniu nowego projektu z [dotnet nowe](../tools/dotnet-new.md) polecenia, a także zawsze, gdy zostanie dodano nową zależność do projektu.</span><span class="sxs-lookup"><span data-stu-id="4ba32-114">In previous versions of .NET Core, you had to run the [dotnet restore](../tools/dotnet-restore.md) command to download dependencies immediately after you created a new project with the [dotnet new](../tools/dotnet-new.md) command, as well as whenever you added a new dependency to your project.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="4ba32-115">Można także wyłączyć automatyczne wywoływanie `dotnet restore` przez przekazanie `--no-restore` przełączyć się do `new`, `run`, `build`, `publish`, `pack`, i `test` poleceń.</span><span class="sxs-lookup"><span data-stu-id="4ba32-115">You can also disable the automatic invocation of `dotnet restore` by passing the `--no-restore` switch to the `new`, `run`, `build`, `publish`, `pack`, and `test` commands.</span></span> 

### <a name="retargeting-to-net-core-20"></a><span data-ttu-id="4ba32-116">Przekierowania do platformy .NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="4ba32-116">Retargeting to .NET Core 2.0</span></span>

<span data-ttu-id="4ba32-117">Po zainstalowaniu programu .NET Core 2.0 SDK projekty który docelowe .NET Core 1.x cel może zostać zmieniony na .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="4ba32-117">If the .NET Core 2.0 SDK is installed, projects that target .NET Core 1.x can be retargeted to .NET Core 2.0.</span></span>

<span data-ttu-id="4ba32-118">Aby przekierować .NET Core 2.0, należy edytować plik projektu, zmieniając wartość `<TargetFramework>` elementu (lub `<TargetFrameworks>` elementu, jeśli masz więcej niż jeden element docelowy w pliku projektu) z 1.x 2.0:</span><span class="sxs-lookup"><span data-stu-id="4ba32-118">To retarget to .NET Core 2.0, edit your project file by changing the value of the `<TargetFramework>` element (or the `<TargetFrameworks>` element if you have more than one target in your project file) from 1.x to 2.0:</span></span>

```xml
<PropertyGroup>
    <TargetFramework>netcoreapp2.0</TargetFramework>
 </PropertyGroup>
```

<span data-ttu-id="4ba32-119">Można również przekierować .NET standardowych bibliotek .NET 2.0 standardowe taki sam sposób:</span><span class="sxs-lookup"><span data-stu-id="4ba32-119">You can also retarget .NET Standard libraries to .NET Standard 2.0 the same way:</span></span>

```xml
<PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
 </PropertyGroup>
```

<span data-ttu-id="4ba32-120">Aby uzyskać więcej informacji na temat migracji projektu do .NET Core 2.0, zobacz [migracji z platformy ASP.NET Core 1.x do składnika ASP.NET 2.0 Core](/aspnet/core/migration/1x-to-2x/index).</span><span class="sxs-lookup"><span data-stu-id="4ba32-120">For more information about migrating your project to .NET Core 2.0, see [Migrating from ASP.NET Core 1.x to ASP.NET Core 2.0](/aspnet/core/migration/1x-to-2x/index).</span></span>

## <a name="language-support"></a><span data-ttu-id="4ba32-121">Obsługa języków</span><span class="sxs-lookup"><span data-stu-id="4ba32-121">Language support</span></span>

<span data-ttu-id="4ba32-122">Oprócz obsługi języka C# i F #, .NET Core 2.0 obsługuje również Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4ba32-122">In addition to supporting C# and F#, .NET Core 2.0 also supports Visual Basic.</span></span>

### <a name="visual-basic"></a><span data-ttu-id="4ba32-123">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4ba32-123">Visual Basic</span></span>

<span data-ttu-id="4ba32-124">W wersji 2.0 .NET Core obsługuje teraz 2017 Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4ba32-124">With version 2.0, .NET Core now supports Visual Basic 2017.</span></span> <span data-ttu-id="4ba32-125">Visual Basic umożliwia tworzenie następujących projektów:</span><span class="sxs-lookup"><span data-stu-id="4ba32-125">You can use Visual Basic to create the following project types:</span></span>

- <span data-ttu-id="4ba32-126">Aplikacje konsoli platformy .NET core</span><span class="sxs-lookup"><span data-stu-id="4ba32-126">.NET Core console apps</span></span>
- <span data-ttu-id="4ba32-127">Biblioteki klas .NET core</span><span class="sxs-lookup"><span data-stu-id="4ba32-127">.NET Core class libraries</span></span>
- <span data-ttu-id="4ba32-128">Biblioteki klas .NET standard</span><span class="sxs-lookup"><span data-stu-id="4ba32-128">.NET Standard class libraries</span></span>
- <span data-ttu-id="4ba32-129">Projektów testów jednostkowych dla .NET core</span><span class="sxs-lookup"><span data-stu-id="4ba32-129">.NET Core unit test projects</span></span>
- <span data-ttu-id="4ba32-130">Projekty testowe xUnit .NET core</span><span class="sxs-lookup"><span data-stu-id="4ba32-130">.NET Core xUnit test projects</span></span>

<span data-ttu-id="4ba32-131">Na przykład do utworzenia aplikacji programu Visual Basic "Hello World", wykonaj następujące kroki w wierszu polecenia:</span><span class="sxs-lookup"><span data-stu-id="4ba32-131">For example, to create a Visual Basic "Hello World" application, do the following steps from the command line:</span></span>

1. <span data-ttu-id="4ba32-132">Otwórz okno konsoli, Utwórz katalog projektu i stał się bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="4ba32-132">Open a console window, create a directory for your project, and make it the current directory.</span></span>

1. <span data-ttu-id="4ba32-133">Wprowadź polecenie `dotnet new console -lang vb`.</span><span class="sxs-lookup"><span data-stu-id="4ba32-133">Enter the command `dotnet new console -lang vb`.</span></span>

   <span data-ttu-id="4ba32-134">Polecenie tworzy plik projektu o `.vbproj` pliku rozszerzenie, wraz z pliku kodu źródłowego języka Visual Basic o nazwie *Program.vb*.</span><span class="sxs-lookup"><span data-stu-id="4ba32-134">The command creates a project file with a `.vbproj` file extension, along with a Visual Basic source code file named *Program.vb*.</span></span> <span data-ttu-id="4ba32-135">Ten plik zawiera kod źródłowy, aby zapisać ciąg "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="4ba32-135">This file contains the source code to write the string "Hello World!"</span></span> <span data-ttu-id="4ba32-136">w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="4ba32-136">to the console window.</span></span>

1.  <span data-ttu-id="4ba32-137">Wprowadź polecenie `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="4ba32-137">Enter the command `dotnet run`.</span></span> <span data-ttu-id="4ba32-138">[Narzędzi interfejsu wiersza polecenia platformy .NET Core](../tools/index.md) automatycznie Kompiluj i wykonywanie aplikacji, która wyświetla komunikat "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="4ba32-138">The [.NET Core CLI tools](../tools/index.md) automatically compile and execute the application, which displays the message "Hello World!"</span></span> <span data-ttu-id="4ba32-139">w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="4ba32-139">in the console window.</span></span>

### <a name="support-for-c-71"></a><span data-ttu-id="4ba32-140">Obsługa języka C# 7.1</span><span class="sxs-lookup"><span data-stu-id="4ba32-140">Support for C# 7.1</span></span>

<span data-ttu-id="4ba32-141">.NET core 2.0 obsługuje 7.1 C#, który dodaje szereg nowych funkcji, w tym:</span><span class="sxs-lookup"><span data-stu-id="4ba32-141">.NET Core 2.0 supports C# 7.1, which adds a number of new features, including:</span></span>

- <span data-ttu-id="4ba32-142">`Main` Metody punktu wejścia aplikacji, można oznaczyć z [async](../../csharp/language-reference/keywords/async.md) — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="4ba32-142">The `Main` method, the application entry point, can be marked with the [async](../../csharp/language-reference/keywords/async.md) keyword.</span></span>
- <span data-ttu-id="4ba32-143">Wywnioskować nazwy spójnej kolekcji.</span><span class="sxs-lookup"><span data-stu-id="4ba32-143">Inferred tuple names.</span></span>
- <span data-ttu-id="4ba32-144">Domyślne wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="4ba32-144">Default expressions.</span></span>

<!-- For more information see [link to C# what's new](url). -->

## <a name="platform-improvements"></a><span data-ttu-id="4ba32-145">Ulepszenia platformy</span><span class="sxs-lookup"><span data-stu-id="4ba32-145">Platform improvements</span></span>

<span data-ttu-id="4ba32-146">.NET core 2.0 obejmuje kilka funkcji, które ułatwiają Zainstaluj oprogramowanie .NET Core i używać go na obsługiwanych systemów operacyjnych.</span><span class="sxs-lookup"><span data-stu-id="4ba32-146">.NET Core 2.0 includes a number of features that make it easier to install .NET Core and to use it on supported operating systems.</span></span>

### <a name="net-core-for-linux-is-a-single-implementation"></a><span data-ttu-id="4ba32-147">Oprogramowanie .NET core dla systemu Linux jest pojedynczą implementacją</span><span class="sxs-lookup"><span data-stu-id="4ba32-147">.NET Core for Linux is a single implementation</span></span>

<span data-ttu-id="4ba32-148">.NET core 2.0 oferuje pojedynczej implementacji systemu Linux, który działa na wielu dystrybucje systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="4ba32-148">.NET Core 2.0 offers a single Linux implementation that works on multiple Linux distributions.</span></span> <span data-ttu-id="4ba32-149">Oprogramowanie .NET core 1.x wymagane pobranie implementacji Linux specyficzne dla dystrybucji.</span><span class="sxs-lookup"><span data-stu-id="4ba32-149">.NET Core 1.x required that you download a distribution-specific Linux implementation.</span></span>

<span data-ttu-id="4ba32-150">Można również tworzyć aplikacji przeznaczonych dla systemu Linux jako jeden system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="4ba32-150">You can also develop apps that target Linux as a single operating system.</span></span> <span data-ttu-id="4ba32-151">Oprogramowanie .NET core 1.x wymagane oddzielnie target każdej dystrybucji systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="4ba32-151">.NET Core 1.x required that you target each Linux distribution separately.</span></span>

### <a name="support-for-the-apple-cryptographic-libraries"></a><span data-ttu-id="4ba32-152">Obsługa bibliotek kryptograficznych firmy Apple</span><span class="sxs-lookup"><span data-stu-id="4ba32-152">Support for the Apple cryptographic libraries</span></span>

<span data-ttu-id="4ba32-153">Oprogramowanie .NET core 1.x na macOS wymagane kryptograficznych biblioteki OpenSSL zestawu narzędzi.</span><span class="sxs-lookup"><span data-stu-id="4ba32-153">.NET Core 1.x on macOS required the OpenSSL toolkit's cryptographic library.</span></span> <span data-ttu-id="4ba32-154">.NET core 2.0 korzysta z bibliotek kryptograficznych firmy Apple i nie wymaga biblioteki OpenSSL, więc nie trzeba go zainstalować.</span><span class="sxs-lookup"><span data-stu-id="4ba32-154">.NET Core 2.0 uses the Apple cryptographic libraries and doesn't require OpenSSL, so you no longer need to install it.</span></span>

## <a name="api-changes-and-library-support"></a><span data-ttu-id="4ba32-155">Zmiany interfejsu API i obsługa biblioteki</span><span class="sxs-lookup"><span data-stu-id="4ba32-155">API changes and library support</span></span>

### <a name="support-for-net-standard-20"></a><span data-ttu-id="4ba32-156">Obsługa .NET 2.0 standardowe</span><span class="sxs-lookup"><span data-stu-id="4ba32-156">Support for .NET Standard 2.0</span></span>

<span data-ttu-id="4ba32-157">.NET Standard definiuje wersjonowany zestaw interfejsów API, które muszą być dostępne na implementacje .NET, które są zgodne z tą wersją standardowego.</span><span class="sxs-lookup"><span data-stu-id="4ba32-157">The .NET Standard defines a versioned set of APIs that must be available on .NET implementations that comply with that version of the standard.</span></span> <span data-ttu-id="4ba32-158">.NET Standard jest przeznaczona dla deweloperów biblioteki.</span><span class="sxs-lookup"><span data-stu-id="4ba32-158">The .NET Standard is targeted at library developers.</span></span> <span data-ttu-id="4ba32-159">Ma on zagwarantowanie funkcje, które są dostępne w bibliotece, przeznaczonego dla wersji platformy .NET Standard w każdej implementacji .NET.</span><span class="sxs-lookup"><span data-stu-id="4ba32-159">It aims to guarantee the functionality that is available to a library that targets a version of the .NET Standard on each .NET implementation.</span></span> <span data-ttu-id="4ba32-160">Oprogramowanie .NET core 1.x obsługuje standardowe .NET w wersji 1.6, .NET Core 2.0 obsługuje najnowszą wersję platformy .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="4ba32-160">.NET Core 1.x supports the .NET Standard version 1.6; .NET Core 2.0 supports the latest version, .NET Standard 2.0.</span></span> <span data-ttu-id="4ba32-161">Aby uzyskać więcej informacji, zobacz [.NET Standard](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="4ba32-161">For more information, see [.NET Standard](../../standard/net-standard.md).</span></span>

<span data-ttu-id="4ba32-162">.NET 2.0 standardowe zawiera ponad 20 000 API więcej niż były dostępne w wersji 1.6 standardowe .NET.</span><span class="sxs-lookup"><span data-stu-id="4ba32-162">.NET Standard 2.0 includes over 20,000 more APIs than were available in the .NET Standard 1.6.</span></span> <span data-ttu-id="4ba32-163">Większość to rozwinięte powierzchni wyników zawierających interfejsów API, które są wspólne dla programu .NET Framework i platformy Xamarin w .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="4ba32-163">Much of this expanded surface area results from incorporating APIs that are common to the .NET Framework and Xamarin into .NET Standard.</span></span>

<span data-ttu-id="4ba32-164">Biblioteki klas .NET 2.0 standardowych można także odwoływać bibliotek klas .NET Framework, pod warunkiem, że wywołują interfejsów API, które znajdują się w standardowe .NET 2.0.</span><span class="sxs-lookup"><span data-stu-id="4ba32-164">.NET Standard 2.0 class libraries can also reference .NET Framework class libraries, provided that they call APIs that are present in the .NET Standard 2.0.</span></span> <span data-ttu-id="4ba32-165">Nie ponowną kompilację biblioteki .NET Framework jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="4ba32-165">No recompilation of the .NET Framework libraries is required.</span></span>

<span data-ttu-id="4ba32-166">Aby uzyskać listę interfejsów API, które zostały dodane do .NET Standard od jej ostatniej wersji 1.6 standardowe .NET, zobacz [.NET 2.0 standardowe vs. 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span><span class="sxs-lookup"><span data-stu-id="4ba32-166">For a list of the APIs that have been added to the .NET Standard since its last version, the .NET Standard 1.6, see [.NET Standard 2.0 vs. 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span></span>

### <a name="expanded-surface-area"></a><span data-ttu-id="4ba32-167">Rozszerzona powierzchni</span><span class="sxs-lookup"><span data-stu-id="4ba32-167">Expanded surface area</span></span>

<span data-ttu-id="4ba32-168">Całkowita liczba interfejsami API dostępnymi w programie .NET Core 2.0 ma więcej niż podwójny porównaniu .NET Core 1.1.</span><span class="sxs-lookup"><span data-stu-id="4ba32-168">The total number of APIs available on .NET Core 2.0 has more than doubled in comparison with .NET Core 1.1.</span></span>

<span data-ttu-id="4ba32-169">I [pakiet zgodności systemu Windows](../porting/windows-compat-pack.md) eksportowanie z .NET Framework stała się znacznie prostsze.</span><span class="sxs-lookup"><span data-stu-id="4ba32-169">And with the [Windows Compatibility Pack](../porting/windows-compat-pack.md) porting from .NET Framework has also become much simpler.</span></span>

### <a name="support-for-net-framework-libraries"></a><span data-ttu-id="4ba32-170">Obsługa bibliotek .NET Framework</span><span class="sxs-lookup"><span data-stu-id="4ba32-170">Support for .NET Framework libraries</span></span>

<span data-ttu-id="4ba32-171">Kodu platformy .NET core można odwoływać się do istniejących bibliotek .NET Framework, w tym istniejących pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="4ba32-171">.NET Core code can reference existing .NET Framework libraries, including existing NuGet packages.</span></span> <span data-ttu-id="4ba32-172">Należy pamiętać, że biblioteki muszą używać interfejsów API, które znajdują się w .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="4ba32-172">Note that the libraries must use APIs that are found in .NET Standard.</span></span>

## <a name="visual-studio-integration"></a><span data-ttu-id="4ba32-173">integracja z programem Visual Studio</span><span class="sxs-lookup"><span data-stu-id="4ba32-173">Visual Studio integration</span></span>

<span data-ttu-id="4ba32-174">Visual Studio 2017 wersji 15.3 i w niektórych przypadkach program Visual Studio for Mac oferują szereg znaczące ulepszenia dla deweloperów platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4ba32-174">Visual Studio 2017 version 15.3 and in some cases Visual Studio for Mac offer a number of significant enhancements for .NET Core developers.</span></span>

### <a name="retargeting-net-core-apps-and-net-standard-libraries"></a><span data-ttu-id="4ba32-175">Przekierowania aplikacji .NET Core i bibliotek .NET Standard</span><span class="sxs-lookup"><span data-stu-id="4ba32-175">Retargeting .NET Core apps and .NET Standard libraries</span></span>

<span data-ttu-id="4ba32-176">Po zainstalowaniu programu .NET Core 2.0 SDK można przekierować projektów 1.x .NET Core .NET Core 2.0 i .NET Standard 1.x bibliotek .NET 2.0 standardowe.</span><span class="sxs-lookup"><span data-stu-id="4ba32-176">If the .NET Core 2.0 SDK is installed, you can retarget .NET Core 1.x projects to .NET Core 2.0 and .NET Standard 1.x libraries to .NET Standard 2.0.</span></span>

<span data-ttu-id="4ba32-177">Aby przekierować projektu w programie Visual Studio, możesz otworzyć **aplikacji** okna dialogowego właściwości projektu i Zmień na karcie **platformy docelowej** do wartości **.NET Core 2.0** lub **.NET 2.0 standardowe**.</span><span class="sxs-lookup"><span data-stu-id="4ba32-177">To retarget your project in Visual Studio, you open the **Application** tab of the project's properties dialog and change the **Target framework** value to **.NET Core 2.0** or **.NET Standard 2.0**.</span></span> <span data-ttu-id="4ba32-178">Można także zmienić go prawym przyciskiem myszy projekt i wybierając **Edytuj \*pliku .csproj** opcji.</span><span class="sxs-lookup"><span data-stu-id="4ba32-178">You can also change it by right-clicking on the project and selecting the **Edit \*.csproj file** option.</span></span> <span data-ttu-id="4ba32-179">Aby uzyskać więcej informacji, zobacz [narzędzi](#tooling) wcześniej w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="4ba32-179">For more information, see the [Tooling](#tooling) section earlier in this topic.</span></span>

### <a name="live-unit-testing-support-for-net-core"></a><span data-ttu-id="4ba32-180">Obsługa funkcji Live Unit Testing dla platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="4ba32-180">Live Unit Testing support for .NET Core</span></span>

<span data-ttu-id="4ba32-181">Przy każdej modyfikacji kodu na żywo testów jednostkowych automatycznie uruchamia wszystkie testy jednostkowe wykorzystywanych w tle i wyświetla wyniki i pokrycie kodu na żywo w środowisku Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4ba32-181">Whenever you modify your code, Live Unit Testing automatically runs any affected unit tests in the background and displays the results and code coverage live in the Visual Studio environment.</span></span> <span data-ttu-id="4ba32-182">.NET core 2.0 obsługuje teraz Live testów jednostkowych.</span><span class="sxs-lookup"><span data-stu-id="4ba32-182">.NET Core 2.0 now supports Live Unit Testing.</span></span> <span data-ttu-id="4ba32-183">Wcześniej testów jednostkowych Live była dostępna tylko w przypadku aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="4ba32-183">Previously, Live Unit Testing was available only for .NET Framework applications.</span></span>

<span data-ttu-id="4ba32-184">Aby uzyskać więcej informacji, zobacz [Live testów jednostkowych z programu Visual Studio 2017](/visualstudio/test/live-unit-testing) i [Live jednostki testowania — często zadawane pytania](/visualstudio/test/live-unit-testing-faq).</span><span class="sxs-lookup"><span data-stu-id="4ba32-184">For more information, see [Live Unit Testing with Visual Studio 2017](/visualstudio/test/live-unit-testing) and the [Live Unit Testing FAQ](/visualstudio/test/live-unit-testing-faq).</span></span>

### <a name="better-support-for-multiple-target-frameworks"></a><span data-ttu-id="4ba32-185">Lepszą obsługę wielu platform docelowych</span><span class="sxs-lookup"><span data-stu-id="4ba32-185">Better support for multiple target frameworks</span></span>

<span data-ttu-id="4ba32-186">Jeśli tworzysz projekt dla wielu struktur docelowych, można wybierać platformy docelowej z menu najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="4ba32-186">If you're building a project for multiple target frameworks, you can now select the target platform from the top-level menu.</span></span> <span data-ttu-id="4ba32-187">Na poniższej ilustracji projektu o nazwie SCD1 jest przeznaczony dla 64-bitowych Mac OS X 10.11 (`osx.10.11-x64`) i 64-bitowego systemu Windows 10/Windows Server 2016 (`win10-x64`).</span><span class="sxs-lookup"><span data-stu-id="4ba32-187">In the following figure, a project named SCD1 targets 64-bit Mac OS X 10.11 (`osx.10.11-x64`) and 64-bit Windows 10/Windows Server 2016 (`win10-x64`).</span></span> <span data-ttu-id="4ba32-188">Przed wybraniem przycisku projektu, w tym przypadku do uruchomienia kompilacji debugowania, możesz wybrać platformy docelowej.</span><span class="sxs-lookup"><span data-stu-id="4ba32-188">You can select the target framework before selecting the project button, in this case to run a debug build.</span></span>

![Wybieranie platformy docelowej podczas kompilowania projektu](media/multitarget.png)

### <a name="side-by-side-support-for-net-core-sdks"></a><span data-ttu-id="4ba32-190">Obsługa Side-by-side .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="4ba32-190">Side-by-side support for .NET Core SDKs</span></span>

<span data-ttu-id="4ba32-191">Teraz można zainstalować zestawu SDK .NET Core niezależnie od programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4ba32-191">You can now install the .NET Core SDK independently of Visual Studio.</span></span> <span data-ttu-id="4ba32-192">Umożliwia jednej wersji programu Visual Studio do tworzenia projektów tego docelowego różne wersje programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4ba32-192">This makes it possible for a single version of Visual Studio to build projects that target different versions of .NET Core.</span></span> <span data-ttu-id="4ba32-193">Wcześniej Visual Studio i .NET Core SDK są ściśle powiązane; określonej wersji zestawu SDK wraz z określoną wersją programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="4ba32-193">Previously, Visual Studio and the .NET Core SDK were tightly coupled; a particular version of the SDK accompanied a particular version of Visual Studio.</span></span>

## <a name="documentation-improvements"></a><span data-ttu-id="4ba32-194">Ulepszenia dokumentacji</span><span class="sxs-lookup"><span data-stu-id="4ba32-194">Documentation improvements</span></span>

### <a name="net-application-architecture"></a><span data-ttu-id="4ba32-195">Architektura aplikacji .NET</span><span class="sxs-lookup"><span data-stu-id="4ba32-195">.NET Application Architecture</span></span>

<span data-ttu-id="4ba32-196">[Architektura aplikacji .NET](https://www.microsoft.com/net/learn/architecture) zapewnia dostęp do zestawu książek e, które zawierają wskazówki, najlepsze rozwiązania i przykładowe aplikacje, gdy przy użyciu platformy .NET do kompilacji:</span><span class="sxs-lookup"><span data-stu-id="4ba32-196">[.NET Application Architecture](https://www.microsoft.com/net/learn/architecture) gives you access to a set of e-books that provide guidance, best practices, and sample applications when using .NET to build:</span></span>

- <span data-ttu-id="4ba32-197">Kontenery Mikrousług i Docker.</span><span class="sxs-lookup"><span data-stu-id="4ba32-197">Microservices and Docker containers.</span></span>
- <span data-ttu-id="4ba32-198">Aplikacje sieci Web ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="4ba32-198">Web applications with ASP.NET.</span></span>
- <span data-ttu-id="4ba32-199">Aplikacje mobilne z platformą Xamarin.</span><span class="sxs-lookup"><span data-stu-id="4ba32-199">Mobile applications with Xamarin.</span></span>
- <span data-ttu-id="4ba32-200">Aplikacje, które są wdrażane w chmurze platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="4ba32-200">Applications that are deployed to the Cloud with Azure.</span></span>

## <a name="see-also"></a><span data-ttu-id="4ba32-201">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4ba32-201">See also</span></span>
 [<span data-ttu-id="4ba32-202">Co to jest nowe w programie ASP.NET 2.0 Core</span><span class="sxs-lookup"><span data-stu-id="4ba32-202">What's new in ASP.NET Core 2.0</span></span>](/aspnet/core/aspnetcore-2.0)

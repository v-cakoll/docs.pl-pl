---
title: What's new in .NET Core 2.0
description: Więcej informacji na temat nowych funkcji, które znajdują się w .NET Core.
author: rpetrusha
ms.author: ronpet
ms.date: 08/13/2017
ms.openlocfilehash: 5d21d2e07342d52dc438b67f9738f43fca47469a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54679896"
---
# <a name="whats-new-in-net-core-20"></a><span data-ttu-id="3e416-103">What's new in .NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="3e416-103">What's new in .NET Core 2.0</span></span>

<span data-ttu-id="3e416-104">.NET core 2.0 zawiera ulepszenia i nowe funkcje w następujących obszarach:</span><span class="sxs-lookup"><span data-stu-id="3e416-104">.NET Core 2.0 includes enhancements and new features in the following areas:</span></span>

- [<span data-ttu-id="3e416-105">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="3e416-105">Tooling</span></span>](#tooling)
- [<span data-ttu-id="3e416-106">Obsługa języków</span><span class="sxs-lookup"><span data-stu-id="3e416-106">Language support</span></span>](#language-support)
- [<span data-ttu-id="3e416-107">Ulepszenia platformy</span><span class="sxs-lookup"><span data-stu-id="3e416-107">Platform improvements</span></span>](#platform-improvements)
- [<span data-ttu-id="3e416-108">Zmiany interfejsu API</span><span class="sxs-lookup"><span data-stu-id="3e416-108">API changes</span></span>](#api-changes-and-library-support)
- [<span data-ttu-id="3e416-109">Integracja z programem Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3e416-109">Visual Studio integration</span></span>](#visual-studio-integration)
- [<span data-ttu-id="3e416-110">Udoskonalenia dokumentacji</span><span class="sxs-lookup"><span data-stu-id="3e416-110">Documentation improvements</span></span>](#documentation-improvements)

## <a name="tooling"></a><span data-ttu-id="3e416-111">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="3e416-111">Tooling</span></span>

### <a name="dotnet-restore-runs-implicitly"></a><span data-ttu-id="3e416-112">DotNet restore uruchamia się domyślnie</span><span class="sxs-lookup"><span data-stu-id="3e416-112">dotnet restore runs implicitly</span></span>

<span data-ttu-id="3e416-113">W poprzednich wersjach programu .NET Core, trzeba było uruchomić [dotnet restore](../tools/dotnet-restore.md) polecenie, aby pobrać zależności natychmiast, po utworzeniu nowego projektu za pomocą [dotnet nowe](../tools/dotnet-new.md) polecenia, a także zawsze, gdy użytkownik dodać nowe zależności do projektu.</span><span class="sxs-lookup"><span data-stu-id="3e416-113">In previous versions of .NET Core, you had to run the [dotnet restore](../tools/dotnet-restore.md) command to download dependencies immediately after you created a new project with the [dotnet new](../tools/dotnet-new.md) command, as well as whenever you added a new dependency to your project.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="3e416-114">Można również wyłączyć automatyczne wywołanie `dotnet restore` , przekazując `--no-restore` przełączyć się do `new`, `run`, `build`, `publish`, `pack`, i `test` poleceń.</span><span class="sxs-lookup"><span data-stu-id="3e416-114">You can also disable the automatic invocation of `dotnet restore` by passing the `--no-restore` switch to the `new`, `run`, `build`, `publish`, `pack`, and `test` commands.</span></span>

### <a name="retargeting-to-net-core-20"></a><span data-ttu-id="3e416-115">Trwa przekierowywanie do programu .NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="3e416-115">Retargeting to .NET Core 2.0</span></span>

<span data-ttu-id="3e416-116">Jeśli zainstalowano zestawu .NET Core 2.0 SDK, projekty przeznaczone na platformę .NET Core 1.x można ukierunkowany na .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="3e416-116">If the .NET Core 2.0 SDK is installed, projects that target .NET Core 1.x can be retargeted to .NET Core 2.0.</span></span>

<span data-ttu-id="3e416-117">Aby przekierować do platformy .NET Core 2.0, należy edytować plik projektu, zmieniając wartość `<TargetFramework>` elementu (lub `<TargetFrameworks>` elementu, jeśli masz więcej niż jeden element docelowy w pliku projektu) z 1.x do 2.0:</span><span class="sxs-lookup"><span data-stu-id="3e416-117">To retarget to .NET Core 2.0, edit your project file by changing the value of the `<TargetFramework>` element (or the `<TargetFrameworks>` element if you have more than one target in your project file) from 1.x to 2.0:</span></span>

```xml
<PropertyGroup>
    <TargetFramework>netcoreapp2.0</TargetFramework>
 </PropertyGroup>
```

<span data-ttu-id="3e416-118">Można również przekierować biblioteki .NET Standard, .NET Standard 2.0 tak samo:</span><span class="sxs-lookup"><span data-stu-id="3e416-118">You can also retarget .NET Standard libraries to .NET Standard 2.0 the same way:</span></span>

```xml
<PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
 </PropertyGroup>
```

<span data-ttu-id="3e416-119">Aby uzyskać więcej informacji na temat migracji projektu .NET Core 2.0, zobacz [migracji z programu ASP.NET Core 1.x do ASP.NET Core 2.0](/aspnet/core/migration/1x-to-2x/index).</span><span class="sxs-lookup"><span data-stu-id="3e416-119">For more information about migrating your project to .NET Core 2.0, see [Migrating from ASP.NET Core 1.x to ASP.NET Core 2.0](/aspnet/core/migration/1x-to-2x/index).</span></span>

## <a name="language-support"></a><span data-ttu-id="3e416-120">Obsługa języków</span><span class="sxs-lookup"><span data-stu-id="3e416-120">Language support</span></span>

<span data-ttu-id="3e416-121">Oprócz obsługi C# i F#, .NET Core 2.0 obsługuje również języka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="3e416-121">In addition to supporting C# and F#, .NET Core 2.0 also supports Visual Basic.</span></span>

### <a name="visual-basic"></a><span data-ttu-id="3e416-122">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3e416-122">Visual Basic</span></span>

<span data-ttu-id="3e416-123">W wersji 2.0 .NET Core obsługuje teraz 2017 Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="3e416-123">With version 2.0, .NET Core now supports Visual Basic 2017.</span></span> <span data-ttu-id="3e416-124">Visual Basic umożliwia tworzenie następujących typów projektu:</span><span class="sxs-lookup"><span data-stu-id="3e416-124">You can use Visual Basic to create the following project types:</span></span>

- <span data-ttu-id="3e416-125">Aplikacje konsoli .NET core</span><span class="sxs-lookup"><span data-stu-id="3e416-125">.NET Core console apps</span></span>
- <span data-ttu-id="3e416-126">Biblioteki klas platformy .NET core</span><span class="sxs-lookup"><span data-stu-id="3e416-126">.NET Core class libraries</span></span>
- <span data-ttu-id="3e416-127">Biblioteki klas .NET standard</span><span class="sxs-lookup"><span data-stu-id="3e416-127">.NET Standard class libraries</span></span>
- <span data-ttu-id="3e416-128">Projekty testów jednostkowych .NET core</span><span class="sxs-lookup"><span data-stu-id="3e416-128">.NET Core unit test projects</span></span>
- <span data-ttu-id="3e416-129">Projekty testów xUnit platformy .NET core</span><span class="sxs-lookup"><span data-stu-id="3e416-129">.NET Core xUnit test projects</span></span>

<span data-ttu-id="3e416-130">Na przykład aby utworzyć aplikację Visual Basic "Hello World", wykonaj następujące czynności w wierszu polecenia:</span><span class="sxs-lookup"><span data-stu-id="3e416-130">For example, to create a Visual Basic "Hello World" application, do the following steps from the command line:</span></span>

1. <span data-ttu-id="3e416-131">Otwórz okno konsoli, a następnie utwórz katalog dla projektu i ułatwiają bieżącego katalogu.</span><span class="sxs-lookup"><span data-stu-id="3e416-131">Open a console window, create a directory for your project, and make it the current directory.</span></span>

1. <span data-ttu-id="3e416-132">Wprowadź polecenie `dotnet new console -lang vb`.</span><span class="sxs-lookup"><span data-stu-id="3e416-132">Enter the command `dotnet new console -lang vb`.</span></span>

   <span data-ttu-id="3e416-133">Polecenie tworzy plik projektu o `.vbproj` pliku rozszerzenie, wraz z pliku kodu źródłowego języka Visual Basic o nazwie *Program.vb*.</span><span class="sxs-lookup"><span data-stu-id="3e416-133">The command creates a project file with a `.vbproj` file extension, along with a Visual Basic source code file named *Program.vb*.</span></span> <span data-ttu-id="3e416-134">Ten plik zawiera kod źródłowy, aby zapisać ciąg "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="3e416-134">This file contains the source code to write the string "Hello World!"</span></span> <span data-ttu-id="3e416-135">w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="3e416-135">to the console window.</span></span>

1. <span data-ttu-id="3e416-136">Wprowadź polecenie `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="3e416-136">Enter the command `dotnet run`.</span></span> <span data-ttu-id="3e416-137">[Interfejsu wiersza polecenia platformy .NET Core](../tools/index.md) automatycznie kompiluje i uruchamia aplikację, która wyświetla komunikat "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="3e416-137">The [.NET Core CLI](../tools/index.md) automatically compiles and executes the application, which displays the message "Hello World!"</span></span> <span data-ttu-id="3e416-138">w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="3e416-138">in the console window.</span></span>

### <a name="support-for-c-71"></a><span data-ttu-id="3e416-139">Obsługa języka C# 7.1</span><span class="sxs-lookup"><span data-stu-id="3e416-139">Support for C# 7.1</span></span>

<span data-ttu-id="3e416-140">.NET core 2.0 obsługuje C# 7.1, który dodaje wiele nowych funkcji, w tym:</span><span class="sxs-lookup"><span data-stu-id="3e416-140">.NET Core 2.0 supports C# 7.1, which adds a number of new features, including:</span></span>

- <span data-ttu-id="3e416-141">`Main` Metody punktu wejścia aplikacji, mogą być oznaczone [async](../../csharp/language-reference/keywords/async.md) — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="3e416-141">The `Main` method, the application entry point, can be marked with the [async](../../csharp/language-reference/keywords/async.md) keyword.</span></span>
- <span data-ttu-id="3e416-142">Pochodnych nazw krotek.</span><span class="sxs-lookup"><span data-stu-id="3e416-142">Inferred tuple names.</span></span>
- <span data-ttu-id="3e416-143">Wyrażenia domyślnego.</span><span class="sxs-lookup"><span data-stu-id="3e416-143">Default expressions.</span></span>

<!-- For more information see [link to C# what's new](url). -->

## <a name="platform-improvements"></a><span data-ttu-id="3e416-144">Ulepszenia platformy</span><span class="sxs-lookup"><span data-stu-id="3e416-144">Platform improvements</span></span>

<span data-ttu-id="3e416-145">.NET core 2.0 obejmuje pewną liczbę funkcji, które ułatwiają instalowanie programu .NET Core i z niej korzystać w obsługiwanych systemach operacyjnych.</span><span class="sxs-lookup"><span data-stu-id="3e416-145">.NET Core 2.0 includes a number of features that make it easier to install .NET Core and to use it on supported operating systems.</span></span>

### <a name="net-core-for-linux-is-a-single-implementation"></a><span data-ttu-id="3e416-146">.NET core dla systemu Linux jest pojedynczą implementacją</span><span class="sxs-lookup"><span data-stu-id="3e416-146">.NET Core for Linux is a single implementation</span></span>

<span data-ttu-id="3e416-147">.NET core 2.0 oferuje pojedynczą implementacją systemu Linux, która działa na wielu dystrybucji systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="3e416-147">.NET Core 2.0 offers a single Linux implementation that works on multiple Linux distributions.</span></span> <span data-ttu-id="3e416-148">.NET core 1.x wymagane pobierania implementacji programu specyficzne dla dystrybucji systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="3e416-148">.NET Core 1.x required that you download a distribution-specific Linux implementation.</span></span>

<span data-ttu-id="3e416-149">Możesz również tworzyć aplikacje przeznaczone dla systemu Linux jako jeden system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="3e416-149">You can also develop apps that target Linux as a single operating system.</span></span> <span data-ttu-id="3e416-150">.NET core 1.x wymagane oddzielnie docelowe każdej dystrybucji systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="3e416-150">.NET Core 1.x required that you target each Linux distribution separately.</span></span>

### <a name="support-for-the-apple-cryptographic-libraries"></a><span data-ttu-id="3e416-151">Obsługa bibliotek kryptograficznych firmy Apple</span><span class="sxs-lookup"><span data-stu-id="3e416-151">Support for the Apple cryptographic libraries</span></span>

<span data-ttu-id="3e416-152">.NET core 1.x w systemie macOS wymagane kryptograficznych biblioteki OpenSSL zestawu narzędzi.</span><span class="sxs-lookup"><span data-stu-id="3e416-152">.NET Core 1.x on macOS required the OpenSSL toolkit's cryptographic library.</span></span> <span data-ttu-id="3e416-153">.NET core 2.0 używa bibliotek kryptograficznych firmy Apple i nie wymaga biblioteki OpenSSL, dzięki czemu nie trzeba go zainstalować.</span><span class="sxs-lookup"><span data-stu-id="3e416-153">.NET Core 2.0 uses the Apple cryptographic libraries and doesn't require OpenSSL, so you no longer need to install it.</span></span>

## <a name="api-changes-and-library-support"></a><span data-ttu-id="3e416-154">Zmiany interfejsu API i obsługa bibliotek</span><span class="sxs-lookup"><span data-stu-id="3e416-154">API changes and library support</span></span>

### <a name="support-for-net-standard-20"></a><span data-ttu-id="3e416-155">Obsługa .NET Standard 2.0</span><span class="sxs-lookup"><span data-stu-id="3e416-155">Support for .NET Standard 2.0</span></span>

<span data-ttu-id="3e416-156">.NET Standard definiuje zestaw numerów wersji interfejsów API, które muszą być dostępne w implementacji .NET, które są zgodne z wersji standard.</span><span class="sxs-lookup"><span data-stu-id="3e416-156">The .NET Standard defines a versioned set of APIs that must be available on .NET implementations that comply with that version of the standard.</span></span> <span data-ttu-id="3e416-157">.NET Standard jest przeznaczona dla deweloperów bibliotek.</span><span class="sxs-lookup"><span data-stu-id="3e416-157">The .NET Standard is targeted at library developers.</span></span> <span data-ttu-id="3e416-158">Ma on funkcjonalność, która jest dostępna dla biblioteki, który jest przeznaczony dla wersji programu .NET Standard na każdej implementacji .NET.</span><span class="sxs-lookup"><span data-stu-id="3e416-158">It aims to guarantee the functionality that is available to a library that targets a version of the .NET Standard on each .NET implementation.</span></span> <span data-ttu-id="3e416-159">.NET core 1.x obsługuje .NET Standard w wersji 1.6; .NET Core 2.0 obsługuje najnowszej wersji .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="3e416-159">.NET Core 1.x supports the .NET Standard version 1.6; .NET Core 2.0 supports the latest version, .NET Standard 2.0.</span></span> <span data-ttu-id="3e416-160">Aby uzyskać więcej informacji, zobacz [.NET Standard](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="3e416-160">For more information, see [.NET Standard](../../standard/net-standard.md).</span></span>

<span data-ttu-id="3e416-161">.NET standard 2.0 zawiera ponad 20 000 więcej interfejsów API nie były dostępne w wersji 1.6 standardowy .NET.</span><span class="sxs-lookup"><span data-stu-id="3e416-161">.NET Standard 2.0 includes over 20,000 more APIs than were available in the .NET Standard 1.6.</span></span> <span data-ttu-id="3e416-162">Większość tego rozwinięte powierzchni wyników zawierających interfejsów API, które są wspólne dla środowiska .NET Framework i Xamarin do .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="3e416-162">Much of this expanded surface area results from incorporating APIs that are common to the .NET Framework and Xamarin into .NET Standard.</span></span>

<span data-ttu-id="3e416-163">Biblioteki klas .NET standard 2.0 także odwoływać się do biblioteki klas .NET Framework, pod warunkiem, że będą wywoływać interfejsy API, które znajdują się w programie .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="3e416-163">.NET Standard 2.0 class libraries can also reference .NET Framework class libraries, provided that they call APIs that are present in the .NET Standard 2.0.</span></span> <span data-ttu-id="3e416-164">Nie kompilację bibliotek programu .NET Framework jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="3e416-164">No recompilation of the .NET Framework libraries is required.</span></span>

<span data-ttu-id="3e416-165">Aby uzyskać listę interfejsów API, które zostały dodane do .NET Standard od jej ostatniej wersji platformy .NET Standard w wersji 1.6, zobacz [vs .NET Standard 2.0. 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span><span class="sxs-lookup"><span data-stu-id="3e416-165">For a list of the APIs that have been added to the .NET Standard since its last version, the .NET Standard 1.6, see [.NET Standard 2.0 vs. 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span></span>

### <a name="expanded-surface-area"></a><span data-ttu-id="3e416-166">Rozwinięty obszar powierzchni</span><span class="sxs-lookup"><span data-stu-id="3e416-166">Expanded surface area</span></span>

<span data-ttu-id="3e416-167">Całkowita liczba interfejsami API dostępnymi w programie .NET Core 2.0 podwoiła więcej niż w porównaniu z platformy .NET Core 1.1.</span><span class="sxs-lookup"><span data-stu-id="3e416-167">The total number of APIs available on .NET Core 2.0 has more than doubled in comparison with .NET Core 1.1.</span></span>

<span data-ttu-id="3e416-168">I [systemie Windows Compatibility Pack](../porting/windows-compat-pack.md) przenoszenie z .NET Framework również stał się dużo prostsze.</span><span class="sxs-lookup"><span data-stu-id="3e416-168">And with the [Windows Compatibility Pack](../porting/windows-compat-pack.md) porting from .NET Framework has also become much simpler.</span></span>

### <a name="support-for-net-framework-libraries"></a><span data-ttu-id="3e416-169">Obsługa bibliotek .NET Framework</span><span class="sxs-lookup"><span data-stu-id="3e416-169">Support for .NET Framework libraries</span></span>

<span data-ttu-id="3e416-170">Kod platformy .NET core może odwoływać się do istniejących bibliotek .NET Framework, w tym istniejących pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="3e416-170">.NET Core code can reference existing .NET Framework libraries, including existing NuGet packages.</span></span> <span data-ttu-id="3e416-171">Należy pamiętać, że bibliotek należy użyć interfejsów API, które znajdują się w programie .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="3e416-171">Note that the libraries must use APIs that are found in .NET Standard.</span></span>

## <a name="visual-studio-integration"></a><span data-ttu-id="3e416-172">integracja z programem Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3e416-172">Visual Studio integration</span></span>

<span data-ttu-id="3e416-173">Visual Studio 2017 w wersji 15.3, a w niektórych przypadkach program Visual Studio for Mac oferuje szereg znaczące ulepszenia dla deweloperów platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3e416-173">Visual Studio 2017 version 15.3 and in some cases Visual Studio for Mac offer a number of significant enhancements for .NET Core developers.</span></span>

### <a name="retargeting-net-core-apps-and-net-standard-libraries"></a><span data-ttu-id="3e416-174">Trwa przekierowywanie aplikacje platformy .NET Core oraz biblioteki .NET Standard</span><span class="sxs-lookup"><span data-stu-id="3e416-174">Retargeting .NET Core apps and .NET Standard libraries</span></span>

<span data-ttu-id="3e416-175">Jeśli zainstalowano zestawu .NET Core 2.0 SDK, można przekierować projektów programu .NET Core 1.x do platformy .NET Core 2.0 i .NET Standard 1.x bibliotek .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="3e416-175">If the .NET Core 2.0 SDK is installed, you can retarget .NET Core 1.x projects to .NET Core 2.0 and .NET Standard 1.x libraries to .NET Standard 2.0.</span></span>

<span data-ttu-id="3e416-176">Aby przekierować projektu w programie Visual Studio, możesz otworzyć **aplikacji** na karcie okna dialogowego właściwości projektu i zmień **platformę docelową** wartość **.NET Core 2.0** lub **.NET standard 2.0**.</span><span class="sxs-lookup"><span data-stu-id="3e416-176">To retarget your project in Visual Studio, you open the **Application** tab of the project's properties dialog and change the **Target framework** value to **.NET Core 2.0** or **.NET Standard 2.0**.</span></span> <span data-ttu-id="3e416-177">Możesz również zmienić, klikając prawym przyciskiem myszy na projekt i wybierając **Edytuj \*pliku .csproj** opcji.</span><span class="sxs-lookup"><span data-stu-id="3e416-177">You can also change it by right-clicking on the project and selecting the **Edit \*.csproj file** option.</span></span> <span data-ttu-id="3e416-178">Aby uzyskać więcej informacji, zobacz [narzędzi](#tooling) wcześniej w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="3e416-178">For more information, see the [Tooling](#tooling) section earlier in this topic.</span></span>

### <a name="live-unit-testing-support-for-net-core"></a><span data-ttu-id="3e416-179">Obsługa funkcji Live Unit Testing dla platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="3e416-179">Live Unit Testing support for .NET Core</span></span>

<span data-ttu-id="3e416-180">Przy każdej modyfikacji kodu Live Unit Testing automatycznie uruchamia wszystkie testy jednostkowe wykorzystywanych w tle i wyświetla wyniki i pokrycia kodu na żywo w środowisku Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3e416-180">Whenever you modify your code, Live Unit Testing automatically runs any affected unit tests in the background and displays the results and code coverage live in the Visual Studio environment.</span></span> <span data-ttu-id="3e416-181">.NET core 2.0 obsługuje teraz funkcję Live Unit Testing.</span><span class="sxs-lookup"><span data-stu-id="3e416-181">.NET Core 2.0 now supports Live Unit Testing.</span></span> <span data-ttu-id="3e416-182">Wcześniej Live Unit Testing była dostępna tylko w przypadku aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3e416-182">Previously, Live Unit Testing was available only for .NET Framework applications.</span></span>

<span data-ttu-id="3e416-183">Aby uzyskać więcej informacji, zobacz [Live Unit Testing w programie Visual Studio 2017](/visualstudio/test/live-unit-testing) i [Live Unit Testing — często zadawane pytania](/visualstudio/test/live-unit-testing-faq).</span><span class="sxs-lookup"><span data-stu-id="3e416-183">For more information, see [Live Unit Testing with Visual Studio 2017](/visualstudio/test/live-unit-testing) and the [Live Unit Testing FAQ](/visualstudio/test/live-unit-testing-faq).</span></span>

### <a name="better-support-for-multiple-target-frameworks"></a><span data-ttu-id="3e416-184">Lepsza obsługa wielu platform docelowych</span><span class="sxs-lookup"><span data-stu-id="3e416-184">Better support for multiple target frameworks</span></span>

<span data-ttu-id="3e416-185">Jeśli tworzysz projekt dla wielu platform docelowych można teraz wybrać platformę docelową menu najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="3e416-185">If you're building a project for multiple target frameworks, you can now select the target platform from the top-level menu.</span></span> <span data-ttu-id="3e416-186">Na poniższej ilustracji, projekt o nazwie SCD1 cele 64-bitowym z systemem macOS X 10.11 (`osx.10.11-x64`) i 64-bitowego systemu Windows 10/Windows Server 2016 (`win10-x64`).</span><span class="sxs-lookup"><span data-stu-id="3e416-186">In the following figure, a project named SCD1 targets 64-bit macOS X 10.11 (`osx.10.11-x64`) and 64-bit Windows 10/Windows Server 2016 (`win10-x64`).</span></span> <span data-ttu-id="3e416-187">Przed wybraniem przycisku projektu, w tym przypadku kompilację debugowania, możesz wybrać platformy docelowej.</span><span class="sxs-lookup"><span data-stu-id="3e416-187">You can select the target framework before selecting the project button, in this case to run a debug build.</span></span>

![Wybieranie platformy docelowej podczas kompilowania projektu](media/multitarget.png)

### <a name="side-by-side-support-for-net-core-sdks"></a><span data-ttu-id="3e416-189">Side-by-side obsługę zestawów .NET Core SDK</span><span class="sxs-lookup"><span data-stu-id="3e416-189">Side-by-side support for .NET Core SDKs</span></span>

<span data-ttu-id="3e416-190">Można teraz zainstalować zestaw .NET Core SDK, niezależnie od programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3e416-190">You can now install the .NET Core SDK independently of Visual Studio.</span></span> <span data-ttu-id="3e416-191">Umożliwia jednej wersji programu Visual Studio do tworzenia projektów tego kierują do różnych wersji programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3e416-191">This makes it possible for a single version of Visual Studio to build projects that target different versions of .NET Core.</span></span> <span data-ttu-id="3e416-192">Wcześniej Visual Studio i .NET Core SDK są ściśle powiązane; określoną wersję zestawu SDK wraz z określonej wersji programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3e416-192">Previously, Visual Studio and the .NET Core SDK were tightly coupled; a particular version of the SDK accompanied a particular version of Visual Studio.</span></span>

## <a name="documentation-improvements"></a><span data-ttu-id="3e416-193">Udoskonalenia dokumentacji</span><span class="sxs-lookup"><span data-stu-id="3e416-193">Documentation improvements</span></span>

### <a name="net-application-architecture"></a><span data-ttu-id="3e416-194">Architektura aplikacji .NET</span><span class="sxs-lookup"><span data-stu-id="3e416-194">.NET Application Architecture</span></span>

<span data-ttu-id="3e416-195">[Architektura aplikacji .NET](https://www.microsoft.com/net/learn/architecture) zapewnia dostęp do zestawu książkami elektronicznymi, które zapewniają wskazówki, najlepsze rozwiązania i przykładowe aplikacje, korzystając z platformy .NET do tworzenia:</span><span class="sxs-lookup"><span data-stu-id="3e416-195">[.NET Application Architecture](https://www.microsoft.com/net/learn/architecture) gives you access to a set of e-books that provide guidance, best practices, and sample applications when using .NET to build:</span></span>

- [<span data-ttu-id="3e416-196">Mikrousług i kontenerów rozwiązania Docker</span><span class="sxs-lookup"><span data-stu-id="3e416-196">Microservices and Docker containers</span></span>](../../standard/microservices-architecture/index.md)
- [<span data-ttu-id="3e416-197">Aplikacje sieci Web wykorzystujące technologie ASP.NET</span><span class="sxs-lookup"><span data-stu-id="3e416-197">Web applications with ASP.NET</span></span>](../../standard/modern-web-apps-azure-architecture/index.md)
- [<span data-ttu-id="3e416-198">Aplikacje mobilne za pomocą platformy Xamarin</span><span class="sxs-lookup"><span data-stu-id="3e416-198">Mobile applications with Xamarin</span></span>](/xamarin/xamarin-forms/enterprise-application-patterns/index)
- [<span data-ttu-id="3e416-199">Aplikacje, które są wdrażane w chmurze dzięki platformie Azure</span><span class="sxs-lookup"><span data-stu-id="3e416-199">Applications that are deployed to the Cloud with Azure</span></span>](/azure/architecture/reference-architectures/index)

## <a name="see-also"></a><span data-ttu-id="3e416-200">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3e416-200">See also</span></span>

- [<span data-ttu-id="3e416-201">What's new in ASP.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="3e416-201">What's new in ASP.NET Core 2.0</span></span>](/aspnet/core/aspnetcore-2.0)

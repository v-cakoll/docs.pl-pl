---
title: Co nowego w programie .NET Core 2.0
description: Dowiedz się więcej o nowych funkcjach dostępnych w programie .NET Core.
ms.date: 08/13/2017
ms.openlocfilehash: 115b3adc72b6798c6a7bac9cc18044a8822808a6
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2019
ms.locfileid: "74801892"
---
# <a name="whats-new-in-net-core-20"></a><span data-ttu-id="ab4ed-103">Co nowego w programie .NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="ab4ed-103">What's new in .NET Core 2.0</span></span>

<span data-ttu-id="ab4ed-104">Program .NET Core 2,0 zawiera ulepszenia i nowe funkcje w następujących obszarach:</span><span class="sxs-lookup"><span data-stu-id="ab4ed-104">.NET Core 2.0 includes enhancements and new features in the following areas:</span></span>

- [<span data-ttu-id="ab4ed-105">Narzędzi</span><span class="sxs-lookup"><span data-stu-id="ab4ed-105">Tooling</span></span>](#tooling)
- [<span data-ttu-id="ab4ed-106">Obsługa języków</span><span class="sxs-lookup"><span data-stu-id="ab4ed-106">Language support</span></span>](#language-support)
- [<span data-ttu-id="ab4ed-107">Ulepszenia platformy</span><span class="sxs-lookup"><span data-stu-id="ab4ed-107">Platform improvements</span></span>](#platform-improvements)
- [<span data-ttu-id="ab4ed-108">Zmiany interfejsu API</span><span class="sxs-lookup"><span data-stu-id="ab4ed-108">API changes</span></span>](#api-changes-and-library-support)
- [<span data-ttu-id="ab4ed-109">Integracja z programem Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ab4ed-109">Visual Studio integration</span></span>](#visual-studio-integration)
- [<span data-ttu-id="ab4ed-110">Udoskonalenia dokumentacji</span><span class="sxs-lookup"><span data-stu-id="ab4ed-110">Documentation improvements</span></span>](#documentation-improvements)

## <a name="tooling"></a><span data-ttu-id="ab4ed-111">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="ab4ed-111">Tooling</span></span>

### <a name="dotnet-restore-runs-implicitly"></a><span data-ttu-id="ab4ed-112">niejawnie uruchamiane dotnet restore</span><span class="sxs-lookup"><span data-stu-id="ab4ed-112">dotnet restore runs implicitly</span></span>

<span data-ttu-id="ab4ed-113">W poprzednich wersjach programu .NET Core należy uruchomić polecenie [dotnet Restore](../tools/dotnet-restore.md) , aby pobrać zależności natychmiast po utworzeniu nowego projektu za pomocą polecenia [dotnet New](../tools/dotnet-new.md) , a także za każdym razem, gdy dodano nową zależność do projektu.</span><span class="sxs-lookup"><span data-stu-id="ab4ed-113">In previous versions of .NET Core, you had to run the [dotnet restore](../tools/dotnet-restore.md) command to download dependencies immediately after you created a new project with the [dotnet new](../tools/dotnet-new.md) command, as well as whenever you added a new dependency to your project.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="ab4ed-114">Możesz również wyłączyć automatyczne wywoływanie `dotnet restore`, przekazując `--no-restore` Przełącz do poleceń `new`, `run`, `build`, `publish`, `pack`i `test`.</span><span class="sxs-lookup"><span data-stu-id="ab4ed-114">You can also disable the automatic invocation of `dotnet restore` by passing the `--no-restore` switch to the `new`, `run`, `build`, `publish`, `pack`, and `test` commands.</span></span>

### <a name="retargeting-to-net-core-20"></a><span data-ttu-id="ab4ed-115">Przekierowywanie do programu .NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="ab4ed-115">Retargeting to .NET Core 2.0</span></span>

<span data-ttu-id="ab4ed-116">Jeśli jest zainstalowany zestaw SDK programu .NET Core 2,0, projekty przeznaczone dla platformy .NET Core 1. x można przekierować do programu .NET Core 2,0.</span><span class="sxs-lookup"><span data-stu-id="ab4ed-116">If the .NET Core 2.0 SDK is installed, projects that target .NET Core 1.x can be retargeted to .NET Core 2.0.</span></span>

<span data-ttu-id="ab4ed-117">Aby przekierować do programu .NET Core 2,0, edytuj plik projektu przez zmianę wartości elementu `<TargetFramework>` (lub elementu `<TargetFrameworks>`, jeśli masz więcej niż jeden obiekt docelowy w pliku projektu) od 1. x do 2,0:</span><span class="sxs-lookup"><span data-stu-id="ab4ed-117">To retarget to .NET Core 2.0, edit your project file by changing the value of the `<TargetFramework>` element (or the `<TargetFrameworks>` element if you have more than one target in your project file) from 1.x to 2.0:</span></span>

```xml
<PropertyGroup>
    <TargetFramework>netcoreapp2.0</TargetFramework>
 </PropertyGroup>
```

<span data-ttu-id="ab4ed-118">Można również przekierować .NET Standard biblioteki do .NET Standard 2,0 w ten sam sposób:</span><span class="sxs-lookup"><span data-stu-id="ab4ed-118">You can also retarget .NET Standard libraries to .NET Standard 2.0 the same way:</span></span>

```xml
<PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
 </PropertyGroup>
```

<span data-ttu-id="ab4ed-119">Aby uzyskać więcej informacji na temat migrowania projektu do programu .NET Core 2,0, zobacz [Migrowanie z ASP.NET Core 1. x do ASP.NET Core 2,0](/aspnet/core/migration/1x-to-2x/index).</span><span class="sxs-lookup"><span data-stu-id="ab4ed-119">For more information about migrating your project to .NET Core 2.0, see [Migrating from ASP.NET Core 1.x to ASP.NET Core 2.0](/aspnet/core/migration/1x-to-2x/index).</span></span>

## <a name="language-support"></a><span data-ttu-id="ab4ed-120">Obsługa języków</span><span class="sxs-lookup"><span data-stu-id="ab4ed-120">Language support</span></span>

<span data-ttu-id="ab4ed-121">Oprócz obsługi C# i F#programu .NET Core 2,0 obsługuje również Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ab4ed-121">In addition to supporting C# and F#, .NET Core 2.0 also supports Visual Basic.</span></span>

### <a name="visual-basic"></a><span data-ttu-id="ab4ed-122">Język Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ab4ed-122">Visual Basic</span></span>

<span data-ttu-id="ab4ed-123">W wersji 2,0 program .NET Core obsługuje teraz Visual Basic 2017.</span><span class="sxs-lookup"><span data-stu-id="ab4ed-123">With version 2.0, .NET Core now supports Visual Basic 2017.</span></span> <span data-ttu-id="ab4ed-124">Za pomocą Visual Basic można utworzyć następujące typy projektów:</span><span class="sxs-lookup"><span data-stu-id="ab4ed-124">You can use Visual Basic to create the following project types:</span></span>

- <span data-ttu-id="ab4ed-125">Aplikacje konsolowe platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="ab4ed-125">.NET Core console apps</span></span>
- <span data-ttu-id="ab4ed-126">Biblioteki klas platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="ab4ed-126">.NET Core class libraries</span></span>
- <span data-ttu-id="ab4ed-127">.NET Standard biblioteki klas</span><span class="sxs-lookup"><span data-stu-id="ab4ed-127">.NET Standard class libraries</span></span>
- <span data-ttu-id="ab4ed-128">Projekty testów jednostkowych .NET Core</span><span class="sxs-lookup"><span data-stu-id="ab4ed-128">.NET Core unit test projects</span></span>
- <span data-ttu-id="ab4ed-129">Projekty testowe programu .NET Core xUnit</span><span class="sxs-lookup"><span data-stu-id="ab4ed-129">.NET Core xUnit test projects</span></span>

<span data-ttu-id="ab4ed-130">Na przykład aby utworzyć Visual Basic aplikację "Hello world", wykonaj następujące kroki w wierszu polecenia:</span><span class="sxs-lookup"><span data-stu-id="ab4ed-130">For example, to create a Visual Basic "Hello World" application, do the following steps from the command line:</span></span>

1. <span data-ttu-id="ab4ed-131">Otwórz okno konsoli, Utwórz katalog dla projektu i ustaw go jako bieżący katalog.</span><span class="sxs-lookup"><span data-stu-id="ab4ed-131">Open a console window, create a directory for your project, and make it the current directory.</span></span>

1. <span data-ttu-id="ab4ed-132">Wprowadź polecenie `dotnet new console -lang vb`.</span><span class="sxs-lookup"><span data-stu-id="ab4ed-132">Enter the command `dotnet new console -lang vb`.</span></span>

   <span data-ttu-id="ab4ed-133">Polecenie tworzy plik projektu z rozszerzeniem pliku `.vbproj` wraz z Visual Basic plikiem kodu źródłowego o nazwie *program. vb*.</span><span class="sxs-lookup"><span data-stu-id="ab4ed-133">The command creates a project file with a `.vbproj` file extension, along with a Visual Basic source code file named *Program.vb*.</span></span> <span data-ttu-id="ab4ed-134">Ten plik zawiera kod źródłowy do zapisu ciągu "Hello world!"</span><span class="sxs-lookup"><span data-stu-id="ab4ed-134">This file contains the source code to write the string "Hello World!"</span></span> <span data-ttu-id="ab4ed-135">do okna konsoli.</span><span class="sxs-lookup"><span data-stu-id="ab4ed-135">to the console window.</span></span>

1. <span data-ttu-id="ab4ed-136">Wprowadź polecenie `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="ab4ed-136">Enter the command `dotnet run`.</span></span> <span data-ttu-id="ab4ed-137">[Interfejs wiersza polecenia platformy .NET Core](../tools/index.md) automatycznie kompiluje i wykonuje aplikację, która wyświetla komunikat "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="ab4ed-137">The [.NET Core CLI](../tools/index.md) automatically compiles and executes the application, which displays the message "Hello World!"</span></span> <span data-ttu-id="ab4ed-138">w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="ab4ed-138">in the console window.</span></span>

### <a name="support-for-c-71"></a><span data-ttu-id="ab4ed-139">Obsługa C# 7,1</span><span class="sxs-lookup"><span data-stu-id="ab4ed-139">Support for C# 7.1</span></span>

<span data-ttu-id="ab4ed-140">Program .NET Core 2,0 C# obsługuje 7,1, który dodaje wiele nowych funkcji, takich jak:</span><span class="sxs-lookup"><span data-stu-id="ab4ed-140">.NET Core 2.0 supports C# 7.1, which adds a number of new features, including:</span></span>

- <span data-ttu-id="ab4ed-141">Metoda `Main`, punkt wejścia aplikacji, może być oznaczona za pomocą słowa kluczowego [Async](../../csharp/language-reference/keywords/async.md) .</span><span class="sxs-lookup"><span data-stu-id="ab4ed-141">The `Main` method, the application entry point, can be marked with the [async](../../csharp/language-reference/keywords/async.md) keyword.</span></span>
- <span data-ttu-id="ab4ed-142">Wywnioskowane nazwy krotek.</span><span class="sxs-lookup"><span data-stu-id="ab4ed-142">Inferred tuple names.</span></span>
- <span data-ttu-id="ab4ed-143">Wyrażenia domyślne.</span><span class="sxs-lookup"><span data-stu-id="ab4ed-143">Default expressions.</span></span>

<!-- For more information see [link to C# what's new](url). -->

## <a name="platform-improvements"></a><span data-ttu-id="ab4ed-144">Ulepszenia platformy</span><span class="sxs-lookup"><span data-stu-id="ab4ed-144">Platform improvements</span></span>

<span data-ttu-id="ab4ed-145">Program .NET Core 2,0 zawiera szereg funkcji, które ułatwiają instalowanie programu .NET Core i korzystanie z nich w obsługiwanych systemach operacyjnych.</span><span class="sxs-lookup"><span data-stu-id="ab4ed-145">.NET Core 2.0 includes a number of features that make it easier to install .NET Core and to use it on supported operating systems.</span></span>

### <a name="net-core-for-linux-is-a-single-implementation"></a><span data-ttu-id="ab4ed-146">.NET Core dla systemu Linux to jedna implementacja</span><span class="sxs-lookup"><span data-stu-id="ab4ed-146">.NET Core for Linux is a single implementation</span></span>

<span data-ttu-id="ab4ed-147">Platforma .NET Core 2,0 oferuje jedną implementację systemu Linux, która działa w przypadku wielu dystrybucji systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="ab4ed-147">.NET Core 2.0 offers a single Linux implementation that works on multiple Linux distributions.</span></span> <span data-ttu-id="ab4ed-148">Program .NET Core 1. x wymaga pobrania implementacji systemu Linux dotyczącej dystrybucji.</span><span class="sxs-lookup"><span data-stu-id="ab4ed-148">.NET Core 1.x required that you download a distribution-specific Linux implementation.</span></span>

<span data-ttu-id="ab4ed-149">Możesz również opracowywać aplikacje przeznaczone dla systemu Linux jako pojedynczy system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="ab4ed-149">You can also develop apps that target Linux as a single operating system.</span></span> <span data-ttu-id="ab4ed-150">W przypadku programu .NET Core 1. x wymagana jest Każda dystrybucja systemu Linux osobno.</span><span class="sxs-lookup"><span data-stu-id="ab4ed-150">.NET Core 1.x required that you target each Linux distribution separately.</span></span>

### <a name="support-for-the-apple-cryptographic-libraries"></a><span data-ttu-id="ab4ed-151">Obsługa bibliotek kryptograficznych firmy Apple</span><span class="sxs-lookup"><span data-stu-id="ab4ed-151">Support for the Apple cryptographic libraries</span></span>

<span data-ttu-id="ab4ed-152">Platforma .NET Core 1. x w systemie macOS wymagała biblioteki kryptograficznej zestawu narzędzi OpenSSL.</span><span class="sxs-lookup"><span data-stu-id="ab4ed-152">.NET Core 1.x on macOS required the OpenSSL toolkit's cryptographic library.</span></span> <span data-ttu-id="ab4ed-153">Platforma .NET Core 2,0 korzysta z bibliotek kryptograficznych firmy Apple i nie wymaga OpenSSL, więc nie trzeba już jej instalować.</span><span class="sxs-lookup"><span data-stu-id="ab4ed-153">.NET Core 2.0 uses the Apple cryptographic libraries and doesn't require OpenSSL, so you no longer need to install it.</span></span>

## <a name="api-changes-and-library-support"></a><span data-ttu-id="ab4ed-154">Obsługa zmian i bibliotek interfejsu API</span><span class="sxs-lookup"><span data-stu-id="ab4ed-154">API changes and library support</span></span>

### <a name="support-for-net-standard-20"></a><span data-ttu-id="ab4ed-155">Obsługa .NET Standard 2,0</span><span class="sxs-lookup"><span data-stu-id="ab4ed-155">Support for .NET Standard 2.0</span></span>

<span data-ttu-id="ab4ed-156">.NET Standard definiuje zestaw interfejsów API, które muszą być dostępne w implementacjach platformy .NET, które są zgodne z tą wersją Standard.</span><span class="sxs-lookup"><span data-stu-id="ab4ed-156">The .NET Standard defines a versioned set of APIs that must be available on .NET implementations that comply with that version of the standard.</span></span> <span data-ttu-id="ab4ed-157">.NET Standard jest przeznaczona dla deweloperów biblioteki.</span><span class="sxs-lookup"><span data-stu-id="ab4ed-157">The .NET Standard is targeted at library developers.</span></span> <span data-ttu-id="ab4ed-158">Ma ona na celu zagwarantowanie, że funkcjonalność dostępna dla biblioteki, która jest przeznaczona dla wersji .NET Standard w każdej implementacji platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="ab4ed-158">It aims to guarantee the functionality that is available to a library that targets a version of the .NET Standard on each .NET implementation.</span></span> <span data-ttu-id="ab4ed-159">Platforma .NET Core 1. x obsługuje .NET Standard w wersji 1,6; program .NET Core 2,0 obsługuje najnowszą wersję .NET Standard 2,0.</span><span class="sxs-lookup"><span data-stu-id="ab4ed-159">.NET Core 1.x supports the .NET Standard version 1.6; .NET Core 2.0 supports the latest version, .NET Standard 2.0.</span></span> <span data-ttu-id="ab4ed-160">Aby uzyskać więcej informacji, zobacz [.NET Standard](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="ab4ed-160">For more information, see [.NET Standard](../../standard/net-standard.md).</span></span>

<span data-ttu-id="ab4ed-161">.NET Standard 2,0 obejmuje ponad 20 000 więcej interfejsów API niż w .NET Standard 1,6.</span><span class="sxs-lookup"><span data-stu-id="ab4ed-161">.NET Standard 2.0 includes over 20,000 more APIs than were available in the .NET Standard 1.6.</span></span> <span data-ttu-id="ab4ed-162">Większość tego rozwiniętego obszaru powierzchni polega na dołączaniu interfejsów API, które są wspólne dla .NET Framework i platformy Xamarin w .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="ab4ed-162">Much of this expanded surface area results from incorporating APIs that are common to the .NET Framework and Xamarin into .NET Standard.</span></span>

<span data-ttu-id="ab4ed-163">Biblioteki klas .NET Standard 2,0 mogą również odwoływać się do bibliotek klas .NET Framework, pod warunkiem, że wywoła interfejsy API, które znajdują się w .NET Standard 2,0.</span><span class="sxs-lookup"><span data-stu-id="ab4ed-163">.NET Standard 2.0 class libraries can also reference .NET Framework class libraries, provided that they call APIs that are present in the .NET Standard 2.0.</span></span> <span data-ttu-id="ab4ed-164">Nie jest wymagana ponowna kompilacja bibliotek .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ab4ed-164">No recompilation of the .NET Framework libraries is required.</span></span>

<span data-ttu-id="ab4ed-165">Aby zapoznać się z listą interfejsów API, które zostały dodane do .NET Standard od momentu jego ostatniej wersji, .NET Standard 1,6, zobacz [.NET Standard 2,0 a 1,6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span><span class="sxs-lookup"><span data-stu-id="ab4ed-165">For a list of the APIs that have been added to the .NET Standard since its last version, the .NET Standard 1.6, see [.NET Standard 2.0 vs. 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span></span>

### <a name="expanded-surface-area"></a><span data-ttu-id="ab4ed-166">Rozwinięty obszar powierzchni</span><span class="sxs-lookup"><span data-stu-id="ab4ed-166">Expanded surface area</span></span>

<span data-ttu-id="ab4ed-167">Łączna liczba interfejsów API dostępnych w środowisku .NET Core 2,0 jest większa niż dwukrotnie w porównaniu z platformą .NET Core 1,1.</span><span class="sxs-lookup"><span data-stu-id="ab4ed-167">The total number of APIs available on .NET Core 2.0 has more than doubled in comparison with .NET Core 1.1.</span></span>

<span data-ttu-id="ab4ed-168">Natomiast [pakiet zgodności systemu Windows](../porting/windows-compat-pack.md) z .NET Framework został również znacznie łatwiejszy.</span><span class="sxs-lookup"><span data-stu-id="ab4ed-168">And with the [Windows Compatibility Pack](../porting/windows-compat-pack.md) porting from .NET Framework has also become much simpler.</span></span>

### <a name="support-for-net-framework-libraries"></a><span data-ttu-id="ab4ed-169">Obsługa bibliotek .NET Framework</span><span class="sxs-lookup"><span data-stu-id="ab4ed-169">Support for .NET Framework libraries</span></span>

<span data-ttu-id="ab4ed-170">Kod .NET Core może odwoływać się do istniejących bibliotek .NET Framework, w tym istniejących pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="ab4ed-170">.NET Core code can reference existing .NET Framework libraries, including existing NuGet packages.</span></span> <span data-ttu-id="ab4ed-171">Należy pamiętać, że biblioteki muszą używać interfejsów API, które znajdują się w .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="ab4ed-171">Note that the libraries must use APIs that are found in .NET Standard.</span></span>

## <a name="visual-studio-integration"></a><span data-ttu-id="ab4ed-172">integracja z programem Visual Studio</span><span class="sxs-lookup"><span data-stu-id="ab4ed-172">Visual Studio integration</span></span>

<span data-ttu-id="ab4ed-173">Program Visual Studio 2017 w wersji 15,3 i w niektórych przypadkach Visual Studio dla komputerów Mac oferować szereg znaczących ulepszeń dla deweloperów platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ab4ed-173">Visual Studio 2017 version 15.3 and in some cases Visual Studio for Mac offer a number of significant enhancements for .NET Core developers.</span></span>

### <a name="retargeting-net-core-apps-and-net-standard-libraries"></a><span data-ttu-id="ab4ed-174">Przekierowywanie aplikacji .NET Core i bibliotek .NET Standard</span><span class="sxs-lookup"><span data-stu-id="ab4ed-174">Retargeting .NET Core apps and .NET Standard libraries</span></span>

<span data-ttu-id="ab4ed-175">Jeśli jest zainstalowany zestaw SDK programu .NET Core 2,0, można przekierować projekty platformy .NET Core 1. x do bibliotek .NET Core 2,0 i .NET Standard 1. x do .NET Standard 2,0.</span><span class="sxs-lookup"><span data-stu-id="ab4ed-175">If the .NET Core 2.0 SDK is installed, you can retarget .NET Core 1.x projects to .NET Core 2.0 and .NET Standard 1.x libraries to .NET Standard 2.0.</span></span>

<span data-ttu-id="ab4ed-176">Aby przekierować projekt w programie Visual Studio, Otwórz kartę **aplikacji** okna dialogowego właściwości projektu i zmień wartość **platformy docelowej** na **.net Core 2,0** lub **.NET Standard 2,0**.</span><span class="sxs-lookup"><span data-stu-id="ab4ed-176">To retarget your project in Visual Studio, you open the **Application** tab of the project's properties dialog and change the **Target framework** value to **.NET Core 2.0** or **.NET Standard 2.0**.</span></span> <span data-ttu-id="ab4ed-177">Można to również zmienić, klikając prawym przyciskiem myszy projekt i wybierając opcję **edytuj \*. csproj** .</span><span class="sxs-lookup"><span data-stu-id="ab4ed-177">You can also change it by right-clicking on the project and selecting the **Edit \*.csproj file** option.</span></span> <span data-ttu-id="ab4ed-178">Aby uzyskać więcej informacji, zobacz sekcję dotyczącą [narzędzi](#tooling) wcześniej w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="ab4ed-178">For more information, see the [Tooling](#tooling) section earlier in this topic.</span></span>

### <a name="live-unit-testing-support-for-net-core"></a><span data-ttu-id="ab4ed-179">Obsługa funkcji Live Unit Testing dla platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="ab4ed-179">Live Unit Testing support for .NET Core</span></span>

<span data-ttu-id="ab4ed-180">Za każdym razem, gdy modyfikujesz swój kod, Live Unit Testing automatycznie uruchamia wszystkie objęte testy jednostkowe w tle i wyświetla wyniki i pokrycie kodu na żywo w środowisku programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ab4ed-180">Whenever you modify your code, Live Unit Testing automatically runs any affected unit tests in the background and displays the results and code coverage live in the Visual Studio environment.</span></span> <span data-ttu-id="ab4ed-181">Platforma .NET Core 2,0 obsługuje teraz Live Unit Testing.</span><span class="sxs-lookup"><span data-stu-id="ab4ed-181">.NET Core 2.0 now supports Live Unit Testing.</span></span> <span data-ttu-id="ab4ed-182">Wcześniej Live Unit Testing był dostępny tylko dla aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ab4ed-182">Previously, Live Unit Testing was available only for .NET Framework applications.</span></span>

<span data-ttu-id="ab4ed-183">Aby uzyskać więcej informacji, zobacz [Live Unit Testing z programem Visual Studio](/visualstudio/test/live-unit-testing) i [Live Unit Testing często zadawanych pytań](/visualstudio/test/live-unit-testing-faq).</span><span class="sxs-lookup"><span data-stu-id="ab4ed-183">For more information, see [Live Unit Testing with Visual Studio](/visualstudio/test/live-unit-testing) and the [Live Unit Testing FAQ](/visualstudio/test/live-unit-testing-faq).</span></span>

### <a name="better-support-for-multiple-target-frameworks"></a><span data-ttu-id="ab4ed-184">Lepsza obsługa wielu platform docelowych</span><span class="sxs-lookup"><span data-stu-id="ab4ed-184">Better support for multiple target frameworks</span></span>

<span data-ttu-id="ab4ed-185">Jeśli tworzysz projekt dla wielu struktur docelowych, możesz teraz wybrać platformę docelową z menu najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="ab4ed-185">If you're building a project for multiple target frameworks, you can now select the target platform from the top-level menu.</span></span> <span data-ttu-id="ab4ed-186">Na poniższej ilustracji projekt o nazwie SCD1 targets 64-bit macOS X 10,11 (`osx.10.11-x64`) i 64-bit Windows 10/Windows Server 2016 (`win10-x64`).</span><span class="sxs-lookup"><span data-stu-id="ab4ed-186">In the following figure, a project named SCD1 targets 64-bit macOS X 10.11 (`osx.10.11-x64`) and 64-bit Windows 10/Windows Server 2016 (`win10-x64`).</span></span> <span data-ttu-id="ab4ed-187">Możesz wybrać platformę docelową przed wybraniem przycisku projektu, w tym przypadku, aby uruchomić kompilację debugowania.</span><span class="sxs-lookup"><span data-stu-id="ab4ed-187">You can select the target framework before selecting the project button, in this case to run a debug build.</span></span>

![Zrzut ekranu przedstawiający wybór platformy docelowej podczas kompilowania projektu.](./media/dotnet-core-2-0/target-framework-selection.png)

### <a name="side-by-side-support-for-net-core-sdks"></a><span data-ttu-id="ab4ed-189">Obsługa równoczesna dla zestawów SDK platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="ab4ed-189">Side-by-side support for .NET Core SDKs</span></span>

<span data-ttu-id="ab4ed-190">Teraz można zainstalować zestaw .NET Core SDK niezależnie od programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ab4ed-190">You can now install the .NET Core SDK independently of Visual Studio.</span></span> <span data-ttu-id="ab4ed-191">Dzięki temu pojedynczej wersji programu Visual Studio można tworzyć projekty przeznaczone dla różnych wersji platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ab4ed-191">This makes it possible for a single version of Visual Studio to build projects that target different versions of .NET Core.</span></span> <span data-ttu-id="ab4ed-192">Wcześniej program Visual Studio i zestaw .NET Core SDK były ściśle sprzężone; określona wersja zestawu SDK dołączona do określonej wersji programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ab4ed-192">Previously, Visual Studio and the .NET Core SDK were tightly coupled; a particular version of the SDK accompanied a particular version of Visual Studio.</span></span>

## <a name="documentation-improvements"></a><span data-ttu-id="ab4ed-193">Udoskonalenia dokumentacji</span><span class="sxs-lookup"><span data-stu-id="ab4ed-193">Documentation improvements</span></span>

### <a name="net-application-architecture"></a><span data-ttu-id="ab4ed-194">Architektura aplikacji .NET</span><span class="sxs-lookup"><span data-stu-id="ab4ed-194">.NET Application Architecture</span></span>

<span data-ttu-id="ab4ed-195">[Architektura aplikacji .NET](https://dotnet.microsoft.com/learn/dotnet/architecture-guides) zapewnia dostęp do zestawu książek elektronicznych, które udostępniają wskazówki, najlepsze rozwiązania i przykładowe aplikacje w przypadku korzystania z platformy .NET do kompilowania:</span><span class="sxs-lookup"><span data-stu-id="ab4ed-195">[.NET Application Architecture](https://dotnet.microsoft.com/learn/dotnet/architecture-guides) gives you access to a set of e-books that provide guidance, best practices, and sample applications when using .NET to build:</span></span>

- [<span data-ttu-id="ab4ed-196">Mikrousługi i kontenery platformy Docker</span><span class="sxs-lookup"><span data-stu-id="ab4ed-196">Microservices and Docker containers</span></span>](../../architecture/microservices/index.md)
- [<span data-ttu-id="ab4ed-197">Aplikacje sieci Web z ASP.NET</span><span class="sxs-lookup"><span data-stu-id="ab4ed-197">Web applications with ASP.NET</span></span>](../../architecture/modern-web-apps-azure/index.md)
- [<span data-ttu-id="ab4ed-198">Aplikacje mobilne przy użyciu platformy Xamarin</span><span class="sxs-lookup"><span data-stu-id="ab4ed-198">Mobile applications with Xamarin</span></span>](/xamarin/xamarin-forms/enterprise-application-patterns/index)
- [<span data-ttu-id="ab4ed-199">Aplikacje wdrożone w chmurze na platformie Azure</span><span class="sxs-lookup"><span data-stu-id="ab4ed-199">Applications that are deployed to the Cloud with Azure</span></span>](/azure/architecture/reference-architectures/index)

## <a name="see-also"></a><span data-ttu-id="ab4ed-200">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ab4ed-200">See also</span></span>

- [<span data-ttu-id="ab4ed-201">Co nowego w ASP.NET Core 2,0</span><span class="sxs-lookup"><span data-stu-id="ab4ed-201">What's new in ASP.NET Core 2.0</span></span>](/aspnet/core/aspnetcore-2.0)

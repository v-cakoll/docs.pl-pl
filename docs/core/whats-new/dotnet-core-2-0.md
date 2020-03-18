---
title: Co nowego w programie .NET Core 2.0
description: Dowiedz się więcej o nowych funkcjach znalezionych w .NET Core.
ms.date: 08/13/2017
ms.openlocfilehash: 115b3adc72b6798c6a7bac9cc18044a8822808a6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79398833"
---
# <a name="whats-new-in-net-core-20"></a><span data-ttu-id="a806d-103">Co nowego w programie .NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="a806d-103">What's new in .NET Core 2.0</span></span>

<span data-ttu-id="a806d-104">.NET Core 2.0 zawiera ulepszenia i nowe funkcje w następujących obszarach:</span><span class="sxs-lookup"><span data-stu-id="a806d-104">.NET Core 2.0 includes enhancements and new features in the following areas:</span></span>

- [<span data-ttu-id="a806d-105">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="a806d-105">Tooling</span></span>](#tooling)
- [<span data-ttu-id="a806d-106">Obsługa języków</span><span class="sxs-lookup"><span data-stu-id="a806d-106">Language support</span></span>](#language-support)
- [<span data-ttu-id="a806d-107">Ulepszenia platformy</span><span class="sxs-lookup"><span data-stu-id="a806d-107">Platform improvements</span></span>](#platform-improvements)
- [<span data-ttu-id="a806d-108">Zmiany interfejsu API</span><span class="sxs-lookup"><span data-stu-id="a806d-108">API changes</span></span>](#api-changes-and-library-support)
- [<span data-ttu-id="a806d-109">Integracja z programem Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a806d-109">Visual Studio integration</span></span>](#visual-studio-integration)
- [<span data-ttu-id="a806d-110">Ulepszenia dokumentacji</span><span class="sxs-lookup"><span data-stu-id="a806d-110">Documentation improvements</span></span>](#documentation-improvements)

## <a name="tooling"></a><span data-ttu-id="a806d-111">Narzędzia</span><span class="sxs-lookup"><span data-stu-id="a806d-111">Tooling</span></span>

### <a name="dotnet-restore-runs-implicitly"></a><span data-ttu-id="a806d-112">przywracanie dotnet działa niejawnie</span><span class="sxs-lookup"><span data-stu-id="a806d-112">dotnet restore runs implicitly</span></span>

<span data-ttu-id="a806d-113">W poprzednich wersjach programu .NET Core trzeba było uruchomić polecenie [przywracania dotnet,](../tools/dotnet-restore.md) aby pobrać zależności natychmiast po utworzeniu nowego projektu za pomocą nowego polecenia [dotnet,](../tools/dotnet-new.md) a także za każdym razem, gdy dodano nową zależność do projektu.</span><span class="sxs-lookup"><span data-stu-id="a806d-113">In previous versions of .NET Core, you had to run the [dotnet restore](../tools/dotnet-restore.md) command to download dependencies immediately after you created a new project with the [dotnet new](../tools/dotnet-new.md) command, as well as whenever you added a new dependency to your project.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="a806d-114">Można `dotnet restore` również wyłączyć automatyczne wywołanie, `--no-restore` przekazując `new`przełącznik `run` `build`do `publish` `pack`, `test` , , , i poleceń.</span><span class="sxs-lookup"><span data-stu-id="a806d-114">You can also disable the automatic invocation of `dotnet restore` by passing the `--no-restore` switch to the `new`, `run`, `build`, `publish`, `pack`, and `test` commands.</span></span>

### <a name="retargeting-to-net-core-20"></a><span data-ttu-id="a806d-115">Retargeting do .NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="a806d-115">Retargeting to .NET Core 2.0</span></span>

<span data-ttu-id="a806d-116">Jeśli jest zainstalowany zestaw SDK .NET Core 2.0, projekty docelowe .NET Core 1.x można przekierować do .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="a806d-116">If the .NET Core 2.0 SDK is installed, projects that target .NET Core 1.x can be retargeted to .NET Core 2.0.</span></span>

<span data-ttu-id="a806d-117">Aby ponownie kierować reklamy na .NET Core 2.0, należy `<TargetFramework>` edytować plik `<TargetFrameworks>` projektu, zmieniając wartość elementu (lub elementu, jeśli w pliku projektu znajduje się więcej niż jeden obiekt docelowy) z 1.x do 2.0:</span><span class="sxs-lookup"><span data-stu-id="a806d-117">To retarget to .NET Core 2.0, edit your project file by changing the value of the `<TargetFramework>` element (or the `<TargetFrameworks>` element if you have more than one target in your project file) from 1.x to 2.0:</span></span>

```xml
<PropertyGroup>
    <TargetFramework>netcoreapp2.0</TargetFramework>
 </PropertyGroup>
```

<span data-ttu-id="a806d-118">W ten sam sposób można również ponownie kierować biblioteki standardów .NET do .NET Standard 2.0:</span><span class="sxs-lookup"><span data-stu-id="a806d-118">You can also retarget .NET Standard libraries to .NET Standard 2.0 the same way:</span></span>

```xml
<PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
 </PropertyGroup>
```

<span data-ttu-id="a806d-119">Aby uzyskać więcej informacji na temat migracji projektu do programu .NET Core 2.0, zobacz [Migrowanie z ASP.NET Core 1.x do ASP.NET Core 2.0](/aspnet/core/migration/1x-to-2x/index).</span><span class="sxs-lookup"><span data-stu-id="a806d-119">For more information about migrating your project to .NET Core 2.0, see [Migrating from ASP.NET Core 1.x to ASP.NET Core 2.0](/aspnet/core/migration/1x-to-2x/index).</span></span>

## <a name="language-support"></a><span data-ttu-id="a806d-120">Obsługa języków</span><span class="sxs-lookup"><span data-stu-id="a806d-120">Language support</span></span>

<span data-ttu-id="a806d-121">Oprócz obsługi języka C# i F#, .NET Core 2.0 obsługuje również visual basic.</span><span class="sxs-lookup"><span data-stu-id="a806d-121">In addition to supporting C# and F#, .NET Core 2.0 also supports Visual Basic.</span></span>

### <a name="visual-basic"></a><span data-ttu-id="a806d-122">Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a806d-122">Visual Basic</span></span>

<span data-ttu-id="a806d-123">W wersji 2.0 program .NET Core obsługuje teraz program Visual Basic 2017.</span><span class="sxs-lookup"><span data-stu-id="a806d-123">With version 2.0, .NET Core now supports Visual Basic 2017.</span></span> <span data-ttu-id="a806d-124">Za pomocą języka Visual Basic można utworzyć następujące typy projektów:</span><span class="sxs-lookup"><span data-stu-id="a806d-124">You can use Visual Basic to create the following project types:</span></span>

- <span data-ttu-id="a806d-125">Aplikacje konsoli .NET Core</span><span class="sxs-lookup"><span data-stu-id="a806d-125">.NET Core console apps</span></span>
- <span data-ttu-id="a806d-126">Biblioteki klas .NET Core</span><span class="sxs-lookup"><span data-stu-id="a806d-126">.NET Core class libraries</span></span>
- <span data-ttu-id="a806d-127">Biblioteki klas .NET Standard</span><span class="sxs-lookup"><span data-stu-id="a806d-127">.NET Standard class libraries</span></span>
- <span data-ttu-id="a806d-128">Projekty testowe jednostkowe .NET Core</span><span class="sxs-lookup"><span data-stu-id="a806d-128">.NET Core unit test projects</span></span>
- <span data-ttu-id="a806d-129">.NET Core xUnit projekty testowe</span><span class="sxs-lookup"><span data-stu-id="a806d-129">.NET Core xUnit test projects</span></span>

<span data-ttu-id="a806d-130">Na przykład, aby utworzyć aplikację Visual Basic "Hello World", wykonaj następujące kroki z wiersza polecenia:</span><span class="sxs-lookup"><span data-stu-id="a806d-130">For example, to create a Visual Basic "Hello World" application, do the following steps from the command line:</span></span>

1. <span data-ttu-id="a806d-131">Otwórz okno konsoli, utwórz katalog dla projektu i uczyń go bieżącym katalogiem.</span><span class="sxs-lookup"><span data-stu-id="a806d-131">Open a console window, create a directory for your project, and make it the current directory.</span></span>

1. <span data-ttu-id="a806d-132">Wprowadź polecenie `dotnet new console -lang vb`.</span><span class="sxs-lookup"><span data-stu-id="a806d-132">Enter the command `dotnet new console -lang vb`.</span></span>

   <span data-ttu-id="a806d-133">Polecenie tworzy plik projektu `.vbproj` z rozszerzeniem pliku wraz z plikiem kodu źródłowego języka Visual Basic o nazwie *Program.vb*.</span><span class="sxs-lookup"><span data-stu-id="a806d-133">The command creates a project file with a `.vbproj` file extension, along with a Visual Basic source code file named *Program.vb*.</span></span> <span data-ttu-id="a806d-134">Ten plik zawiera kod źródłowy do napisania ciągu "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="a806d-134">This file contains the source code to write the string "Hello World!"</span></span> <span data-ttu-id="a806d-135">do okna konsoli.</span><span class="sxs-lookup"><span data-stu-id="a806d-135">to the console window.</span></span>

1. <span data-ttu-id="a806d-136">Wprowadź polecenie `dotnet run`.</span><span class="sxs-lookup"><span data-stu-id="a806d-136">Enter the command `dotnet run`.</span></span> <span data-ttu-id="a806d-137">Interfejs [cli programu .NET Core](../tools/index.md) automatycznie kompiluje i wykonuje aplikację, która wyświetla komunikat "Hello World!"</span><span class="sxs-lookup"><span data-stu-id="a806d-137">The [.NET Core CLI](../tools/index.md) automatically compiles and executes the application, which displays the message "Hello World!"</span></span> <span data-ttu-id="a806d-138">w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="a806d-138">in the console window.</span></span>

### <a name="support-for-c-71"></a><span data-ttu-id="a806d-139">Obsługa języka C# 7.1</span><span class="sxs-lookup"><span data-stu-id="a806d-139">Support for C# 7.1</span></span>

<span data-ttu-id="a806d-140">.NET Core 2.0 obsługuje c# 7.1, który dodaje szereg nowych funkcji, w tym:</span><span class="sxs-lookup"><span data-stu-id="a806d-140">.NET Core 2.0 supports C# 7.1, which adds a number of new features, including:</span></span>

- <span data-ttu-id="a806d-141">Metoda, `Main` punkt wejścia aplikacji, może być oznaczona słowem kluczowym [asynchronicznego.](../../csharp/language-reference/keywords/async.md)</span><span class="sxs-lookup"><span data-stu-id="a806d-141">The `Main` method, the application entry point, can be marked with the [async](../../csharp/language-reference/keywords/async.md) keyword.</span></span>
- <span data-ttu-id="a806d-142">Wywnioskowane nazwy krotki.</span><span class="sxs-lookup"><span data-stu-id="a806d-142">Inferred tuple names.</span></span>
- <span data-ttu-id="a806d-143">Wyrażenia domyślne.</span><span class="sxs-lookup"><span data-stu-id="a806d-143">Default expressions.</span></span>

<!-- For more information see [link to C# what's new](url). -->

## <a name="platform-improvements"></a><span data-ttu-id="a806d-144">Ulepszenia platformy</span><span class="sxs-lookup"><span data-stu-id="a806d-144">Platform improvements</span></span>

<span data-ttu-id="a806d-145">.NET Core 2.0 zawiera szereg funkcji ułatwiających instalację programu .NET Core i używanie go w obsługiwanych systemach operacyjnych.</span><span class="sxs-lookup"><span data-stu-id="a806d-145">.NET Core 2.0 includes a number of features that make it easier to install .NET Core and to use it on supported operating systems.</span></span>

### <a name="net-core-for-linux-is-a-single-implementation"></a><span data-ttu-id="a806d-146">.NET Core dla systemu Linux to pojedyncza implementacja</span><span class="sxs-lookup"><span data-stu-id="a806d-146">.NET Core for Linux is a single implementation</span></span>

<span data-ttu-id="a806d-147">.NET Core 2.0 oferuje jedną implementację systemu Linux, która działa na wielu dystrybucjach Linuksa.</span><span class="sxs-lookup"><span data-stu-id="a806d-147">.NET Core 2.0 offers a single Linux implementation that works on multiple Linux distributions.</span></span> <span data-ttu-id="a806d-148">.NET Core 1.x wymagane jest pobranie implementacji systemu Linux specyficznedla dystrybucji.</span><span class="sxs-lookup"><span data-stu-id="a806d-148">.NET Core 1.x required that you download a distribution-specific Linux implementation.</span></span>

<span data-ttu-id="a806d-149">Można również tworzyć aplikacje, które są przeznaczone dla systemu Linux jako jeden system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="a806d-149">You can also develop apps that target Linux as a single operating system.</span></span> <span data-ttu-id="a806d-150">.NET Core 1.x wymagane, aby kierować każdej dystrybucji systemu Linux oddzielnie.</span><span class="sxs-lookup"><span data-stu-id="a806d-150">.NET Core 1.x required that you target each Linux distribution separately.</span></span>

### <a name="support-for-the-apple-cryptographic-libraries"></a><span data-ttu-id="a806d-151">Obsługa bibliotek kryptograficznych Firmy Apple</span><span class="sxs-lookup"><span data-stu-id="a806d-151">Support for the Apple cryptographic libraries</span></span>

<span data-ttu-id="a806d-152">.NET Core 1.x w systemie macOS wymagał biblioteki kryptograficznej zestawu narzędzi OpenSSL.</span><span class="sxs-lookup"><span data-stu-id="a806d-152">.NET Core 1.x on macOS required the OpenSSL toolkit's cryptographic library.</span></span> <span data-ttu-id="a806d-153">.NET Core 2.0 używa bibliotek kryptograficznych Firmy Apple i nie wymaga OpenSSL, więc nie trzeba go już instalować.</span><span class="sxs-lookup"><span data-stu-id="a806d-153">.NET Core 2.0 uses the Apple cryptographic libraries and doesn't require OpenSSL, so you no longer need to install it.</span></span>

## <a name="api-changes-and-library-support"></a><span data-ttu-id="a806d-154">Zmiany interfejsu API i obsługa bibliotek</span><span class="sxs-lookup"><span data-stu-id="a806d-154">API changes and library support</span></span>

### <a name="support-for-net-standard-20"></a><span data-ttu-id="a806d-155">Obsługa standardu .NET 2.0</span><span class="sxs-lookup"><span data-stu-id="a806d-155">Support for .NET Standard 2.0</span></span>

<span data-ttu-id="a806d-156">Standard .NET definiuje wersjonowany zestaw interfejsów API, które muszą być dostępne w implementacjach .NET, które są zgodne z tą wersją standardu.</span><span class="sxs-lookup"><span data-stu-id="a806d-156">The .NET Standard defines a versioned set of APIs that must be available on .NET implementations that comply with that version of the standard.</span></span> <span data-ttu-id="a806d-157">Standard .NET jest przeznaczony dla deweloperów biblioteki.</span><span class="sxs-lookup"><span data-stu-id="a806d-157">The .NET Standard is targeted at library developers.</span></span> <span data-ttu-id="a806d-158">Ma na celu zagwarantowanie funkcji, która jest dostępna dla biblioteki, która jest przeznaczona dla wersji standardu .NET na każdej implementacji .NET.</span><span class="sxs-lookup"><span data-stu-id="a806d-158">It aims to guarantee the functionality that is available to a library that targets a version of the .NET Standard on each .NET implementation.</span></span> <span data-ttu-id="a806d-159">.NET Core 1.x obsługuje wersję .NET Standard w wersji 1.6; .NET Core 2.0 obsługuje najnowszą wersję .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="a806d-159">.NET Core 1.x supports the .NET Standard version 1.6; .NET Core 2.0 supports the latest version, .NET Standard 2.0.</span></span> <span data-ttu-id="a806d-160">Aby uzyskać więcej informacji, zobacz [.NET Standard](../../standard/net-standard.md).</span><span class="sxs-lookup"><span data-stu-id="a806d-160">For more information, see [.NET Standard](../../standard/net-standard.md).</span></span>

<span data-ttu-id="a806d-161">.NET Standard 2.0 zawiera ponad 20 000 więcej interfejsów API niż były dostępne w standardzie .NET 1.6.</span><span class="sxs-lookup"><span data-stu-id="a806d-161">.NET Standard 2.0 includes over 20,000 more APIs than were available in the .NET Standard 1.6.</span></span> <span data-ttu-id="a806d-162">Wiele z tego rozwiniętego obszaru powierzchni wynika z włączenia interfejsów API, które są wspólne dla .NET Framework i Xamarin do .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="a806d-162">Much of this expanded surface area results from incorporating APIs that are common to the .NET Framework and Xamarin into .NET Standard.</span></span>

<span data-ttu-id="a806d-163">Biblioteki klas .NET Standard 2.0 mogą również odwoływać się do bibliotek klas .NET Framework, pod warunkiem, że wywołają interfejsy API obecne w standardzie .NET 2.0.</span><span class="sxs-lookup"><span data-stu-id="a806d-163">.NET Standard 2.0 class libraries can also reference .NET Framework class libraries, provided that they call APIs that are present in the .NET Standard 2.0.</span></span> <span data-ttu-id="a806d-164">Nie jest wymagana ponowna kompilacja bibliotek .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a806d-164">No recompilation of the .NET Framework libraries is required.</span></span>

<span data-ttu-id="a806d-165">Aby uzyskać listę interfejsów API, które zostały dodane do standardu .NET od jego ostatniej wersji, .NET Standard 1.6, zobacz [.NET Standard 2.0 vs. 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span><span class="sxs-lookup"><span data-stu-id="a806d-165">For a list of the APIs that have been added to the .NET Standard since its last version, the .NET Standard 1.6, see [.NET Standard 2.0 vs. 1.6](https://raw.githubusercontent.com/dotnet/standard/master/docs/versions/netstandard2.0_diff.md).</span></span>

### <a name="expanded-surface-area"></a><span data-ttu-id="a806d-166">Rozszerzona powierzchnia</span><span class="sxs-lookup"><span data-stu-id="a806d-166">Expanded surface area</span></span>

<span data-ttu-id="a806d-167">Całkowita liczba interfejsów API dostępnych w .NET Core 2.0 wzrosła ponad dwukrotnie w porównaniu z .NET Core 1.1.</span><span class="sxs-lookup"><span data-stu-id="a806d-167">The total number of APIs available on .NET Core 2.0 has more than doubled in comparison with .NET Core 1.1.</span></span>

<span data-ttu-id="a806d-168">A dzięki pakietowi [zgodności systemu Windows](../porting/windows-compat-pack.md) przenoszenie z platformy .NET Framework również stało się znacznie prostsze.</span><span class="sxs-lookup"><span data-stu-id="a806d-168">And with the [Windows Compatibility Pack](../porting/windows-compat-pack.md) porting from .NET Framework has also become much simpler.</span></span>

### <a name="support-for-net-framework-libraries"></a><span data-ttu-id="a806d-169">Obsługa bibliotek programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="a806d-169">Support for .NET Framework libraries</span></span>

<span data-ttu-id="a806d-170">Kod .NET Core może odwoływać się do istniejących bibliotek .NET Framework, w tym istniejących pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="a806d-170">.NET Core code can reference existing .NET Framework libraries, including existing NuGet packages.</span></span> <span data-ttu-id="a806d-171">Należy zauważyć, że biblioteki muszą używać interfejsów API, które znajdują się w .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="a806d-171">Note that the libraries must use APIs that are found in .NET Standard.</span></span>

## <a name="visual-studio-integration"></a><span data-ttu-id="a806d-172">Integracja z programem Visual Studio</span><span class="sxs-lookup"><span data-stu-id="a806d-172">Visual Studio integration</span></span>

<span data-ttu-id="a806d-173">Program Visual Studio 2017 w wersji 15.3, a w niektórych przypadkach program Visual Studio dla komputerów Mac oferuje szereg istotnych ulepszeń dla deweloperów .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a806d-173">Visual Studio 2017 version 15.3 and in some cases Visual Studio for Mac offer a number of significant enhancements for .NET Core developers.</span></span>

### <a name="retargeting-net-core-apps-and-net-standard-libraries"></a><span data-ttu-id="a806d-174">Ponowne kierowanie aplikacji .NET Core i bibliotek standardów .NET</span><span class="sxs-lookup"><span data-stu-id="a806d-174">Retargeting .NET Core apps and .NET Standard libraries</span></span>

<span data-ttu-id="a806d-175">Jeśli jest zainstalowany zestaw SDK .NET Core 2.0, można ponownie skierować projekty .NET Core 1.x do bibliotek .NET Core 2.0 i .NET Standard 1.x do .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="a806d-175">If the .NET Core 2.0 SDK is installed, you can retarget .NET Core 1.x projects to .NET Core 2.0 and .NET Standard 1.x libraries to .NET Standard 2.0.</span></span>

<span data-ttu-id="a806d-176">Aby ponownie kierować projekt w programie Visual Studio, otwórz kartę **Aplikacja** w oknie dialogowym właściwości projektu i zmień wartość **platformy docelowej** na **.NET Core 2.0** lub **.NET Standard 2.0**.</span><span class="sxs-lookup"><span data-stu-id="a806d-176">To retarget your project in Visual Studio, you open the **Application** tab of the project's properties dialog and change the **Target framework** value to **.NET Core 2.0** or **.NET Standard 2.0**.</span></span> <span data-ttu-id="a806d-177">Można go również zmienić, klikając prawym przyciskiem myszy projekt i wybierając opcję **Edycja \*pliku csproj.**</span><span class="sxs-lookup"><span data-stu-id="a806d-177">You can also change it by right-clicking on the project and selecting the **Edit \*.csproj file** option.</span></span> <span data-ttu-id="a806d-178">Aby uzyskać więcej informacji, zobacz [sekcji Narzędzia](#tooling) wcześniej w tym temacie.</span><span class="sxs-lookup"><span data-stu-id="a806d-178">For more information, see the [Tooling](#tooling) section earlier in this topic.</span></span>

### <a name="live-unit-testing-support-for-net-core"></a><span data-ttu-id="a806d-179">Obsługa funkcji Live Unit Testing dla platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="a806d-179">Live Unit Testing support for .NET Core</span></span>

<span data-ttu-id="a806d-180">Za każdym razem, gdy modyfikujesz kod, aktywne testowanie jednostek automatycznie uruchamia wszystkie testy jednostkowe, których dotyczy problem w tle i wyświetla wyniki i pokrycie kodu na żywo w środowisku programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a806d-180">Whenever you modify your code, Live Unit Testing automatically runs any affected unit tests in the background and displays the results and code coverage live in the Visual Studio environment.</span></span> <span data-ttu-id="a806d-181">.NET Core 2.0 obsługuje teraz testowanie jednostek na żywo.</span><span class="sxs-lookup"><span data-stu-id="a806d-181">.NET Core 2.0 now supports Live Unit Testing.</span></span> <span data-ttu-id="a806d-182">Wcześniej testowanie jednostek na żywo było dostępne tylko dla aplikacji .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="a806d-182">Previously, Live Unit Testing was available only for .NET Framework applications.</span></span>

<span data-ttu-id="a806d-183">Aby uzyskać więcej informacji, zobacz [Testowanie jednostek na żywo za pomocą programu Visual Studio](/visualstudio/test/live-unit-testing) i często [zadawane często zadawane pytania](/visualstudio/test/live-unit-testing-faq)dotyczące testowania jednostek na żywo .</span><span class="sxs-lookup"><span data-stu-id="a806d-183">For more information, see [Live Unit Testing with Visual Studio](/visualstudio/test/live-unit-testing) and the [Live Unit Testing FAQ](/visualstudio/test/live-unit-testing-faq).</span></span>

### <a name="better-support-for-multiple-target-frameworks"></a><span data-ttu-id="a806d-184">Lepsze wsparcie dla wielu ram docelowych</span><span class="sxs-lookup"><span data-stu-id="a806d-184">Better support for multiple target frameworks</span></span>

<span data-ttu-id="a806d-185">Jeśli budujesz projekt dla wielu platform docelowych, możesz teraz wybrać platformę docelową z menu najwyższego poziomu.</span><span class="sxs-lookup"><span data-stu-id="a806d-185">If you're building a project for multiple target frameworks, you can now select the target platform from the top-level menu.</span></span> <span data-ttu-id="a806d-186">Na poniższej rysunku projekt o nazwie SCD1 jest przeznaczony dla 64-bitowego systemu macOS X 10.11`osx.10.11-x64``win10-x64`( ) i 64-bitowego systemu Windows 10/Windows Server 2016 ( ).</span><span class="sxs-lookup"><span data-stu-id="a806d-186">In the following figure, a project named SCD1 targets 64-bit macOS X 10.11 (`osx.10.11-x64`) and 64-bit Windows 10/Windows Server 2016 (`win10-x64`).</span></span> <span data-ttu-id="a806d-187">Można wybrać platformę docelową przed wybraniem przycisku projektu, w tym przypadku do uruchomienia kompilacji debugowania.</span><span class="sxs-lookup"><span data-stu-id="a806d-187">You can select the target framework before selecting the project button, in this case to run a debug build.</span></span>

![Zrzut ekranu przedstawiający wybór struktury docelowej podczas tworzenia projektu.](./media/dotnet-core-2-0/target-framework-selection.png)

### <a name="side-by-side-support-for-net-core-sdks"></a><span data-ttu-id="a806d-189">Obsługa zestawów SDK sdk .NET Core side-by side</span><span class="sxs-lookup"><span data-stu-id="a806d-189">Side-by-side support for .NET Core SDKs</span></span>

<span data-ttu-id="a806d-190">Zestaw SDK .NET Core można teraz zainstalować niezależnie od programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a806d-190">You can now install the .NET Core SDK independently of Visual Studio.</span></span> <span data-ttu-id="a806d-191">Dzięki temu można dla pojedynczej wersji programu Visual Studio do tworzenia projektów, które są przeznaczone dla różnych wersji programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a806d-191">This makes it possible for a single version of Visual Studio to build projects that target different versions of .NET Core.</span></span> <span data-ttu-id="a806d-192">Wcześniej visual studio i .NET Core SDK były ściśle powiązane; określonej wersji sdk towarzyszy określonej wersji programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a806d-192">Previously, Visual Studio and the .NET Core SDK were tightly coupled; a particular version of the SDK accompanied a particular version of Visual Studio.</span></span>

## <a name="documentation-improvements"></a><span data-ttu-id="a806d-193">Ulepszenia dokumentacji</span><span class="sxs-lookup"><span data-stu-id="a806d-193">Documentation improvements</span></span>

### <a name="net-application-architecture"></a><span data-ttu-id="a806d-194">Architektura aplikacji .NET</span><span class="sxs-lookup"><span data-stu-id="a806d-194">.NET Application Architecture</span></span>

<span data-ttu-id="a806d-195">[Architektura aplikacji .NET](https://dotnet.microsoft.com/learn/dotnet/architecture-guides) zapewnia dostęp do zestawu e-booków, które zawierają wskazówki, najlepsze rozwiązania i przykładowe aplikacje podczas tworzenia aplikacji .NET przy użyciu platformy .NET:</span><span class="sxs-lookup"><span data-stu-id="a806d-195">[.NET Application Architecture](https://dotnet.microsoft.com/learn/dotnet/architecture-guides) gives you access to a set of e-books that provide guidance, best practices, and sample applications when using .NET to build:</span></span>

- [<span data-ttu-id="a806d-196">Kontenery mikrousług i platformy Docker</span><span class="sxs-lookup"><span data-stu-id="a806d-196">Microservices and Docker containers</span></span>](../../architecture/microservices/index.md)
- [<span data-ttu-id="a806d-197">Aplikacje internetowe z ASP.NET</span><span class="sxs-lookup"><span data-stu-id="a806d-197">Web applications with ASP.NET</span></span>](../../architecture/modern-web-apps-azure/index.md)
- [<span data-ttu-id="a806d-198">Aplikacje mobilne z systemem Xamarin</span><span class="sxs-lookup"><span data-stu-id="a806d-198">Mobile applications with Xamarin</span></span>](/xamarin/xamarin-forms/enterprise-application-patterns/index)
- [<span data-ttu-id="a806d-199">Aplikacje wdrożone w chmurze za pomocą platformy Azure</span><span class="sxs-lookup"><span data-stu-id="a806d-199">Applications that are deployed to the Cloud with Azure</span></span>](/azure/architecture/reference-architectures/index)

## <a name="see-also"></a><span data-ttu-id="a806d-200">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a806d-200">See also</span></span>

- [<span data-ttu-id="a806d-201">Co nowego w ASP.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="a806d-201">What's new in ASP.NET Core 2.0</span></span>](/aspnet/core/aspnetcore-2.0)

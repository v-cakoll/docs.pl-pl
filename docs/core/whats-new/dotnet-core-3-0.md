---
title: Co nowego w programie .NET Core 3.0
description: Dowiedz się więcej o nowych funkcjach w programie .NET Core 3.0.
dev_langs:
- csharp
- vb
author: thraka
ms.author: adegeo
ms.date: 05/06/2019
ms.openlocfilehash: 369c74d2d8e82f157de0eec4294a5ee50542292b
ms.sourcegitcommit: a8d3504f0eae1a40bda2b06bd441ba01f1631ef0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/18/2019
ms.locfileid: "67169785"
---
# <a name="whats-new-in-net-core-30-preview-5"></a><span data-ttu-id="bbb6a-103">What's new in .NET Core 3.0 (wersja zapoznawcza 5)</span><span class="sxs-lookup"><span data-stu-id="bbb6a-103">What's new in .NET Core 3.0 (Preview 5)</span></span>

<span data-ttu-id="bbb6a-104">W tym artykule opisano nowości w programie .NET Core 3.0 (za pośrednictwem wersja zapoznawcza 5).</span><span class="sxs-lookup"><span data-stu-id="bbb6a-104">This article describes what is new in .NET Core 3.0 (through preview 5).</span></span> <span data-ttu-id="bbb6a-105">Jedną z największych ulepszenia to obsługa aplikacji klasycznych Windows (tylko Windows).</span><span class="sxs-lookup"><span data-stu-id="bbb6a-105">One of the biggest enhancements is support for Windows desktop applications (Windows only).</span></span> <span data-ttu-id="bbb6a-106">Za pomocą zestawu .NET Core 3.0 SDK składnika Windows Desktop, można przenosić aplikacje Windows Forms i Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="bbb6a-106">By using the .NET Core 3.0 SDK component Windows Desktop, you can port your Windows Forms and Windows Presentation Foundation (WPF) applications.</span></span> <span data-ttu-id="bbb6a-107">Było jasne, składnik Windows Desktop jest tylko obsługiwana i uwzględniane na Windows.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-107">To be clear, the Windows Desktop component is only supported and included on Windows.</span></span> <span data-ttu-id="bbb6a-108">Aby uzyskać więcej informacji, zobacz [pulpitu Windows](#windows-desktop) sekcję w dalszej części tego artykułu.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-108">For more information, see the [Windows desktop](#windows-desktop) section later in this article.</span></span>

<span data-ttu-id="bbb6a-109">.NET core 3.0 dodaje obsługę C# 8.0.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-109">.NET Core 3.0 adds support for C# 8.0.</span></span> <span data-ttu-id="bbb6a-110">Zdecydowanie zaleca się używać najnowszej wersji programu Visual Studio 2019 Update 1 (wersja zapoznawcza) lub programu VSCode z rozszerzeniem technologię OmniSharp.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-110">It's highly recommended that you use the latest release of Visual Studio 2019 Update 1 Preview or VSCode with the OmniSharp extension.</span></span>

<span data-ttu-id="bbb6a-111">[Pobierz i rozpoczynanie pracy z usługą .NET Core 3.0 w wersji zapoznawczej 6](https://aka.ms/netcore3download) teraz na Windows, Mac i Linux.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-111">[Download and get started with .NET Core 3.0 Preview 6](https://aka.ms/netcore3download) right now on Windows, Mac, and Linux.</span></span>

<span data-ttu-id="bbb6a-112">Aby uzyskać więcej informacji na temat poszczególnych wersji zapoznawczej zobacz następujące komunikaty:</span><span class="sxs-lookup"><span data-stu-id="bbb6a-112">For more information about each preview release, see the following announcements:</span></span>

- [<span data-ttu-id="bbb6a-113">Ogłoszenie .NET core 3.0 w wersji zapoznawczej 6</span><span class="sxs-lookup"><span data-stu-id="bbb6a-113">.NET Core 3.0 Preview 6 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-6/)
- [<span data-ttu-id="bbb6a-114">Ogłoszenie .NET core 3.0 w wersji zapoznawczej 5</span><span class="sxs-lookup"><span data-stu-id="bbb6a-114">.NET Core 3.0 Preview 5 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-5/)
- [<span data-ttu-id="bbb6a-115">Ogłoszenie .NET core 3.0 w wersji zapoznawczej 4</span><span class="sxs-lookup"><span data-stu-id="bbb6a-115">.NET Core 3.0 Preview 4 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-4/)
- [<span data-ttu-id="bbb6a-116">Ogłoszenie .NET core 3.0 w wersji zapoznawczej 3</span><span class="sxs-lookup"><span data-stu-id="bbb6a-116">.NET Core 3.0 Preview 3 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-3/)
- [<span data-ttu-id="bbb6a-117">Ogłoszenie .NET core 3.0 w wersji zapoznawczej 2</span><span class="sxs-lookup"><span data-stu-id="bbb6a-117">.NET Core 3.0 Preview 2 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-2/)
- [<span data-ttu-id="bbb6a-118">Ogłoszenie .NET core 3.0 w wersji zapoznawczej 1</span><span class="sxs-lookup"><span data-stu-id="bbb6a-118">.NET Core 3.0 Preview 1 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-1-and-open-sourcing-windows-desktop-frameworks/)

## <a name="net-core-sdk-windows-installer"></a><span data-ttu-id="bbb6a-119">Instalator Windows zestawu SDK programu .NET core</span><span class="sxs-lookup"><span data-stu-id="bbb6a-119">.NET Core SDK Windows Installer</span></span>

<span data-ttu-id="bbb6a-120">Instalator MSI dla Windows został zmieniony, począwszy od programu .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-120">The MSI installer for Windows has changed starting with .NET Core 3.0.</span></span> <span data-ttu-id="bbb6a-121">Instalatory SDK uaktualni teraz zestaw SDK funkcji harmonogramem w miejscu.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-121">The SDK installers will now upgrade SDK feature-band releases in place.</span></span> <span data-ttu-id="bbb6a-122">Paski funkcji są definiowane w *setki* grup w *poprawki* część numeru wersji.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-122">Feature bands are defined in the *hundreds* groups in the *patch* section of the version number.</span></span> <span data-ttu-id="bbb6a-123">Na przykład **3.0. \* 101**\* i **3.0. \* 201**\* są wersje w dwóch grup różnych funkcji podczas **3.0. \* 101**\* i **3.0. \* 199**\* znajdują się w tej samej funkcji poza pasmem.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-123">For example, **3.0.\*101**\* and **3.0.\*201**\* are versions in two different feature bands while **3.0.\*101**\* and **3.0.\*199**\* are in the same feature band.</span></span> <span data-ttu-id="bbb6a-124">I kiedy zestawu .NET Core SDK **3.0. \* 101**\* jest zainstalowany zestaw .NET Core SDK **3.0. \* 100**\* zostaną usunięte z komputera, jeśli taki istnieje.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-124">And, when .NET Core SDK **3.0.\*101**\* is installed, .NET Core SDK **3.0.\*100**\* will be removed from the machine if it exists.</span></span> <span data-ttu-id="bbb6a-125">Gdy zestaw .NET Core SDK **3.0. \* 200**\* jest zainstalowany na tym samym komputerze, .NET Core SDK **3.0. \* 101**\* nie zostaną usunięte.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-125">When .NET Core SDK **3.0.\*200**\* is installed on the same machine, .NET Core SDK **3.0.\*101**\* won't be removed.</span></span>

<span data-ttu-id="bbb6a-126">Aby uzyskać więcej informacji dotyczących wersjonowania, zobacz [omówienie sposobu platformy .NET Core jest wersjonowany](../versions/index.md).</span><span class="sxs-lookup"><span data-stu-id="bbb6a-126">For more information about versioning, see [Overview of how .NET Core is versioned](../versions/index.md).</span></span>

## <a name="c-80-preview"></a><span data-ttu-id="bbb6a-127">C#8.0 (wersja zapoznawcza)</span><span class="sxs-lookup"><span data-stu-id="bbb6a-127">C# 8.0 preview</span></span>

<span data-ttu-id="bbb6a-128">Obsługuje platformy .NET core 3.0 C# 8 (wersja zapoznawcza).</span><span class="sxs-lookup"><span data-stu-id="bbb6a-128">.NET Core 3.0 supports C# 8 preview.</span></span> <span data-ttu-id="bbb6a-129">Aby uzyskać więcej informacji na temat C# funkcje 8.0, zobacz [nowości C# 8.0](../../csharp/whats-new/csharp-8.md).</span><span class="sxs-lookup"><span data-stu-id="bbb6a-129">For more information about C# 8.0 features, see [What's new in C# 8.0](../../csharp/whats-new/csharp-8.md).</span></span>

## <a name="net-standard-21"></a><span data-ttu-id="bbb6a-130">.NET Standard 2.1</span><span class="sxs-lookup"><span data-stu-id="bbb6a-130">.NET Standard 2.1</span></span>

<span data-ttu-id="bbb6a-131">Mimo że program .NET Core 3.0 obsługuje **platformy .NET Standard 2.1**, domyślnie `dotnet new classlib` szablon generuje projekt, który jest przeznaczony dla **.NET Standard 2.0**.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-131">Even though .NET Core 3.0 supports **.NET Standard 2.1**, the default `dotnet new classlib` template generates a project that targets **.NET Standard 2.0**.</span></span> <span data-ttu-id="bbb6a-132">Do obiektu docelowego **platformy .NET Standard 2.1**, Edycja pliku projektu i zmień `TargetFramework` właściwości `netstandard2.1`:</span><span class="sxs-lookup"><span data-stu-id="bbb6a-132">To target **.NET Standard 2.1**, edit your project file and change the `TargetFramework` property to `netstandard2.1`:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
 
  <PropertyGroup>
    <TargetFramework>netstandard2.1</TargetFramework>
  </PropertyGroup>
 
</Project>
```

<span data-ttu-id="bbb6a-133">Jeśli używasz programu Visual Studio należy Visual Studio 2019 r, jak program Visual Studio 2017 nie obsługuje **platformy .NET Standard 2.1** lub **.NET Core 3.0 to**.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-133">If you're using Visual Studio, you need Visual Studio 2019, as Visual Studio 2017 doesn't support **.NET Standard 2.1** or **.NET Core 3.0**.</span></span> <span data-ttu-id="bbb6a-134">Zdecydowanie zaleca się używanie [Visual Studio 2019 aktualizacja 1 — wersja zapoznawcza](https://visualstudio.microsoft.com/vs/preview/).</span><span class="sxs-lookup"><span data-stu-id="bbb6a-134">We highly recommend that you use [Visual Studio 2019 Update 1 Preview](https://visualstudio.microsoft.com/vs/preview/).</span></span>

## <a name="improved-net-core-version-apis"></a><span data-ttu-id="bbb6a-135">Ulepszone .NET Core wersje interfejsów API</span><span class="sxs-lookup"><span data-stu-id="bbb6a-135">Improved .NET Core Version APIs</span></span>

<span data-ttu-id="bbb6a-136">Począwszy od .NET Core 3.0 to wersja, podane interfejsów API za pomocą programu .NET Core teraz zwracane informacje oczekujesz.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-136">Starting with .NET Core 3.0, the version APIs provided with .NET Core now return the information you expect.</span></span> <span data-ttu-id="bbb6a-137">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="bbb6a-137">For example:</span></span>

```csharp
System.Console.WriteLine($"Environment.Version: {System.Environment.Version}");

// Old result
//   Environment.Version: 4.0.30319.42000
//
// New result
//   Environment.Version: 3.0.0
```

```csharp
System.Console.WriteLine($"RuntimeInformation.FrameworkDescription: {System.Runtime.InteropServices.RuntimeInformation.FrameworkDescription}");

// Old result
//   RuntimeInformation.FrameworkDescription: .NET Core 4.6.27415.71
//
// New result
//   RuntimeInformation.FrameworkDescription: .NET Core 3.0.0-preview4-27615-11
```

> [!WARNING]
> <span data-ttu-id="bbb6a-138">Zmiana powodująca niezgodność.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-138">Breaking change.</span></span> <span data-ttu-id="bbb6a-139">Jest to technicznie istotnej zmiany, ponieważ zmienił się schemat przechowywania wersji.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-139">This is technically a breaking change because the versioning scheme has changed.</span></span>

## <a name="net-platform-dependent-intrinsics"></a><span data-ttu-id="bbb6a-140">Funkcje wewnętrzne zależny od platformy .NET</span><span class="sxs-lookup"><span data-stu-id="bbb6a-140">.NET Platform-Dependent Intrinsics</span></span>

<span data-ttu-id="bbb6a-141">Dodano interfejsy API, takich jak zezwalające na dostęp do niektórych instrukcji zorientowane na wydajności procesora CPU **SIMD** lub **instrukcji manipulowania Bit** ustawia.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-141">APIs have been added that allow access to certain perf-oriented CPU instructions, such as the **SIMD** or **Bit Manipulation instruction** sets.</span></span> <span data-ttu-id="bbb6a-142">Te instrukcje może pomóc osiągnąć znaczne zwiększenie wydajności w niektórych scenariuszach, takich jak przetwarzanie danych, efektywnie równolegle.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-142">These instructions can help achieve significant performance improvements in certain scenarios, such as processing data efficiently in parallel.</span></span> 

<span data-ttu-id="bbb6a-143">Gdzie jest to odpowiednie, do bibliotek .NET rozpoczęły przy użyciu tych instrukcji, aby zwiększyć wydajność.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-143">Where appropriate, the .NET libraries have begun using these instructions to improve performance.</span></span>

<span data-ttu-id="bbb6a-144">Aby uzyskać więcej informacji, zobacz [wewnętrzne zależne platformy .NET](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md).</span><span class="sxs-lookup"><span data-stu-id="bbb6a-144">For more information, see [.NET Platform Dependent Intrinsics](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md).</span></span>

## <a name="default-executables"></a><span data-ttu-id="bbb6a-145">Domyślne pliki wykonywalne</span><span class="sxs-lookup"><span data-stu-id="bbb6a-145">Default executables</span></span>

<span data-ttu-id="bbb6a-146">.NET core teraz kompilacje [zależny od struktury plików wykonywalnych](../deploying/index.md#framework-dependent-executables-fde) domyślnie.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-146">.NET Core now builds [framework-dependent executables](../deploying/index.md#framework-dependent-executables-fde) by default.</span></span> <span data-ttu-id="bbb6a-147">To zachowanie jest nowa dla aplikacji, które używają globalnie zainstalowaną wersję platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-147">This behavior is new for applications that use a globally installed version of .NET Core.</span></span> <span data-ttu-id="bbb6a-148">Wcześniej tylko [niezależna wdrożeń](../deploying/index.md#self-contained-deployments-scd) dałby w efekcie plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-148">Previously, only [self-contained deployments](../deploying/index.md#self-contained-deployments-scd) would produce an executable.</span></span>

<span data-ttu-id="bbb6a-149">Podczas `dotnet build` lub `dotnet publish`, tworzony jest plik wykonywalny, który pasuje do środowiska i platformy zestawu SDK jest używany.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-149">During `dotnet build` or `dotnet publish`, an executable is created that matches the environment and platform of the SDK you're using.</span></span> <span data-ttu-id="bbb6a-150">Mogą spodziewać się tego samego rzeczy, korzystając z tych plików wykonywalnych, tak jak w innych natywnych plików wykonywalnych, takich jak:</span><span class="sxs-lookup"><span data-stu-id="bbb6a-150">You can expect the same things with these executables as you would other native executables, such as:</span></span>

* <span data-ttu-id="bbb6a-151">Możesz kliknąć dwukrotnie plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-151">You can double-click on the executable.</span></span>
* <span data-ttu-id="bbb6a-152">Można uruchomić aplikacji z poziomu wiersza polecenia, takie jak `myapp.exe` na Windows, i `./myapp` w systemie Linux i macOS.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-152">You can launch the application from a command prompt directly, such as `myapp.exe` on Windows, and `./myapp` on Linux and macOS.</span></span>

## <a name="single-file-executables"></a><span data-ttu-id="bbb6a-153">Pliki wykonywalne pojedynczego pliku</span><span class="sxs-lookup"><span data-stu-id="bbb6a-153">Single-file executables</span></span>

<span data-ttu-id="bbb6a-154">`dotnet publish` Polecenie obsługuje pakowanie aplikacji do wykonywalnej pojedynczego pliku specyficzne dla platformy.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-154">The `dotnet publish` command supports packaging your app into a platform-specific single-file executable.</span></span> <span data-ttu-id="bbb6a-155">Plik wykonywalny jest samowyodrębniający i zawiera wszystkie zależności (w tym natywne), które są wymagane do uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-155">The executable is self-extracting and contains all dependencies (including native) that are required to run your app.</span></span> <span data-ttu-id="bbb6a-156">Po uruchomieniu aplikacji aplikacja jest wyodrębniany do katalogu na jej podstawie nazwy i identyfikatora kompilacji.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-156">When the app is first run, the application is extracted to a directory based on the app name and build identifier.</span></span> <span data-ttu-id="bbb6a-157">Autostart jest szybsza, kiedy aplikacja jest uruchamiana ponownie.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-157">Startup is faster when the application is run again.</span></span> <span data-ttu-id="bbb6a-158">Aplikacja nie musi wyodrębnić sam po raz drugi, o ile nie użyto nowej wersji.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-158">The application doesn't need to extract itself a second time unless a new version was used.</span></span>

<span data-ttu-id="bbb6a-159">Aby opublikować wykonywalnej pojedynczego pliku, należy ustawić `PublishSingleFile` w projekcie lub w wierszu polecenia za pomocą `dotnet publish` polecenia:</span><span class="sxs-lookup"><span data-stu-id="bbb6a-159">To publish a single-file executable, set the `PublishSingleFile` in your project or on the command line with the `dotnet publish` command:</span></span>

```console
dotnet publish -r win10-x64 /p:PublishSingleFile=true
```

<span data-ttu-id="bbb6a-160">Aby uzyskać więcej informacji dotyczących publikowania w jednym pliku, zobacz [narzędzia bundler pojedynczy plik, dokument projektowy](https://github.com/dotnet/designs/blob/master/accepted/single-file/design.md).</span><span class="sxs-lookup"><span data-stu-id="bbb6a-160">For more information about single-file publishing, see the [single-file bundler design document](https://github.com/dotnet/designs/blob/master/accepted/single-file/design.md).</span></span>

## <a name="assembly-linking"></a><span data-ttu-id="bbb6a-161">Łączenie zestawu</span><span class="sxs-lookup"><span data-stu-id="bbb6a-161">Assembly linking</span></span>

<span data-ttu-id="bbb6a-162">.NET core 3.0 SDK jest powiązana z narzędziem, które można zmniejszyć rozmiar aplikacji, analizując IL i przycinanie nieużywane zestawów.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-162">The .NET core 3.0 SDK comes with a tool that can reduce the size of apps by analyzing IL and trimming unused assemblies.</span></span>

<span data-ttu-id="bbb6a-163">Aplikacje samodzielne zawierają wszystkie elementy potrzebne do uruchomienia kodu, bez konieczności .NET do zainstalowania na komputerze-hoście.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-163">Self-contained apps include everything needed to run your code, without requiring .NET to be installed on the host computer.</span></span> <span data-ttu-id="bbb6a-164">Jednak wiele razy aplikacja wymaga tylko mały podzbiór platformę, by funkcji i innych nieużywane biblioteki można usunąć.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-164">However, many times the app only requires a small subset of the framework to function, and other unused libraries could be removed.</span></span>

<span data-ttu-id="bbb6a-165">.NET core zawiera teraz ustawienie, który będzie używał [konsolidatora IL](https://github.com/mono/linker) narzędzie do skanowania IL Twojej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-165">.NET Core now includes a setting that will use the [IL linker](https://github.com/mono/linker) tool to scan the IL of your app.</span></span> <span data-ttu-id="bbb6a-166">to narzędzie wykrywa, jaki kod jest wymagana, a następnie przycina nieużywane biblioteki.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-166">this tool detects what code is required, and then trims unused libraries.</span></span> <span data-ttu-id="bbb6a-167">To narzędzie może znacznie zmniejszyć rozmiar wdrażania niektórych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-167">This tool can significantly reduce the deployment size of some apps.</span></span>

<span data-ttu-id="bbb6a-168">Aby włączyć to narzędzie `<PublishTrimmed>` ustawienie w projekcie i Opublikuj aplikację samodzielną:</span><span class="sxs-lookup"><span data-stu-id="bbb6a-168">To enable this tool, `<PublishTrimmed>` setting in your project and publish a self-contained app:</span></span>

```xml
<PropertyGroup>
  <PublishTrimmed>true</PublishTrimmed>
</PropertyGroup>
```

```console
dotnet publish -r <rid> -c Release
```

<span data-ttu-id="bbb6a-169">Na przykład podstawowa "hello world" nowej konsoli szablonu projektu jest uwzględniony, podczas publikowania osiąga około 70 MB.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-169">As an example, the basic "hello world" new console project template that is included, when published, hits about 70 MB in size.</span></span> <span data-ttu-id="bbb6a-170">Za pomocą `<PublishTrimmed>`, zmniejszeniu rozmiaru do około 30 MB.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-170">By using `<PublishTrimmed>`, that size is reduced to about 30 MB.</span></span>

<span data-ttu-id="bbb6a-171">Należy wziąć pod uwagę, że aplikacje lub struktur (łącznie z platformą ASP.NET Core i WPF), które używają odbicia lub powiązanych funkcji dynamicznych, często przerywał działanie po przycięciu.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-171">It's important to consider that applications or frameworks (including ASP.NET Core and WPF) that use reflection or related dynamic features, will often break when trimmed.</span></span> <span data-ttu-id="bbb6a-172">Uszkodzenie ten występuje, ponieważ konsolidator nie wiedzieć o to dynamiczne zachowanie i nie można określić, jakie typy framework są wymagane w celu odbicia.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-172">This breakage occurs because the linker doesn't know about this dynamic behavior and can't determine which framework types are required for reflection.</span></span> <span data-ttu-id="bbb6a-173">Należy pamiętać o tym scenariuszu można skonfigurować narzędzia konsolidatora IL.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-173">The IL Linker tool can be configured to be aware of this scenario.</span></span>

<span data-ttu-id="bbb6a-174">Przede wszystkim w przeciwnym wypadku upewnij się przetestować aplikację po przycięciu.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-174">Above all else, be sure to test your app after trimming.</span></span>

<span data-ttu-id="bbb6a-175">Aby uzyskać więcej informacji na temat narzędzia konsolidatora IL, zobacz [dokumentacji](https://aka.ms/dotnet-illink) lub odwiedź [mono/konsolidatora]( https://github.com/mono/linker) repozytorium.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-175">For more information about the IL Linker tool, see the [documentation](https://aka.ms/dotnet-illink) or visit the [mono/linker]( https://github.com/mono/linker) repo.</span></span>

## <a name="tiered-compilation"></a><span data-ttu-id="bbb6a-176">Warstwowe kompilacji</span><span class="sxs-lookup"><span data-stu-id="bbb6a-176">Tiered compilation</span></span>

<span data-ttu-id="bbb6a-177">[Warstwowe kompilacji](https://devblogs.microsoft.com/dotnet/tiered-compilation-preview-in-net-core-2-1/) (TC) jest domyślnie przy użyciu platformy .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-177">[Tiered compilation](https://devblogs.microsoft.com/dotnet/tiered-compilation-preview-in-net-core-2-1/) (TC) is on by default with .NET Core 3.0.</span></span> <span data-ttu-id="bbb6a-178">Ta funkcja umożliwia bardziej adaptacyjnie Użyj kompilator just in Time (JIT), aby uzyskać lepszą wydajność.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-178">This feature enables the runtime to more adaptively use the Just-In-Time (JIT) compiler to get better performance.</span></span>

<span data-ttu-id="bbb6a-179">Główną zaletą TC jest aby jitting metody powrotnego wolniejsze — ale — szybsze do tworzenia kodu lub wyższej jakości — ale wolniejsze do tworzenia kodu.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-179">The main benefit of TC is to enable (re-)jitting methods with slower-but-faster to produce code or higher-quality-but-slower to produce code.</span></span> <span data-ttu-id="bbb6a-180">Pomaga to zwiększyć wydajność aplikacji, ponieważ przechodzi ona przez różne etapy wykonywania z uruchamiania za pośrednictwem stabilnym stanem.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-180">This helps increase performance of an application as it goes through various stages of execution, from startup through steady-state.</span></span> <span data-ttu-id="bbb6a-181">To zachowanie różni się od podejścia-TC, gdzie każda metoda jest kompilowana pojedynczego sposób (taka sama jak w warstwie wysokiej jakości), jest obciążona do stabilnego kosztem wydajności uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-181">This contrasts with the non-TC approach, where every method is compiled a single way (the same as the high-quality tier), which is biased to steady-state over startup performance.</span></span>

<span data-ttu-id="bbb6a-182">Aby włączyć szybkie JIT (warstwy 0 w trybie JIT kodu), należy użyć tego ustawienia w pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="bbb6a-182">To enable Quick JIT (tier 0 jitted code), use this setting in your project file:</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>true</TieredCompilationQuickJit>
</PropertyGroup>
```

<span data-ttu-id="bbb6a-183">Aby całkowicie wyłączyć TC, użyj tego ustawienia w pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="bbb6a-183">To disable TC completely, use this setting in your project file:</span></span>

```xml
<TieredCompilation>false</TieredCompilation>
```

## <a name="readytorun-images"></a><span data-ttu-id="bbb6a-184">Obrazy ReadyToRun</span><span class="sxs-lookup"><span data-stu-id="bbb6a-184">ReadyToRun images</span></span>

<span data-ttu-id="bbb6a-185">Aby poprawić czas uruchamiania aplikacji .NET Core, należy kompilowanie zestawów aplikacji w formacie ReadyToRun (R2R).</span><span class="sxs-lookup"><span data-stu-id="bbb6a-185">You can improve the startup time of your .NET Core application by compiling your application assemblies as ReadyToRun (R2R) format.</span></span> <span data-ttu-id="bbb6a-186">R2R jest formą ahead of time (AOT) kompilacji.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-186">R2R is a form of ahead-of-time (AOT) compilation.</span></span>

<span data-ttu-id="bbb6a-187">Pliki binarne R2R zwiększeniu wydajności uruchamiania, co zmniejsza ilość pracy wykonywanej przez kompilator just-in-time (JIT), które musi wykonać jak ładowanie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-187">R2R binaries improve startup performance by reducing the amount of work the just-in-time (JIT) compiler needs to do as your application loads.</span></span> <span data-ttu-id="bbb6a-188">Pliki binarne zawiera podobne kodu natywnego w porównaniu do czego dałby w efekcie kompilator JIT.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-188">The binaries contain similar native code compared to what the JIT would produce.</span></span>

<span data-ttu-id="bbb6a-189">Pliki binarne R2R są większe, ponieważ zawierają one zarówno kod języka pośredniego (IL), który nadal jest wymagany dla niektórych scenariuszy i natywną wersję tego samego kodu.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-189">R2R binaries are larger because they contain both intermediate language (IL) code, which is still needed for some scenarios, and the native version of the same code.</span></span> <span data-ttu-id="bbb6a-190">R2R jest dostępna tylko po opublikowaniu aplikacja samodzielna przeznaczonego środowiska uruchomieniowe określonych (RID), takie jak x64 w systemie Linux lub Windows x64.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-190">R2R is only available when you publish a self-contained app that targets a specific runtime environments (RID) such as Linux x64 or Windows x64.</span></span>

<span data-ttu-id="bbb6a-191">Aby skompilować aplikację jako R2R, należy dodać `<PublishReadyToRun>` ustawienia:</span><span class="sxs-lookup"><span data-stu-id="bbb6a-191">To compile your app as R2R, add the `<PublishReadyToRun>` setting:</span></span>

```xml
<PropertyGroup>
  <PublishReadyToRun>true</PublishReadyToRun>
</PropertyGroup>
```

<span data-ttu-id="bbb6a-192">Opublikuj aplikację samodzielną.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-192">Publish a self-contained app.</span></span> <span data-ttu-id="bbb6a-193">Na przykład to polecenie tworzy aplikację samodzielną dla 64-bitowej wersji systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="bbb6a-193">For example, this command creates a self-contained app for the 64-bit version of Windows:</span></span>

```console
dotnet publish -c Release -r win-x64 --self-contained true
```

### <a name="cross-platformarchitecture-restrictions"></a><span data-ttu-id="bbb6a-194">Obejmujące wiele platform/architecture ograniczenia</span><span class="sxs-lookup"><span data-stu-id="bbb6a-194">Cross platform/architecture restrictions</span></span>

<span data-ttu-id="bbb6a-195">Kompilator ReadyToRun nie obsługuje obecnie przeznaczonych dla wielu.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-195">The ReadyToRun compiler doesn't currently support cross-targeting.</span></span> <span data-ttu-id="bbb6a-196">Należy skompilować w danym elemencie docelowym.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-196">You must compile on a given target.</span></span> <span data-ttu-id="bbb6a-197">Na przykład chcąc R2R obrazy dla Windows x64, należy do uruchomienia polecenia Opublikuj w tym środowisku.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-197">For example, if you want R2R images for Windows x64, you need to run the publish command on that environment.</span></span>

<span data-ttu-id="bbb6a-198">Wyjątki dla wielu odwołujących:</span><span class="sxs-lookup"><span data-stu-id="bbb6a-198">Exceptions to cross-targetting:</span></span>

- <span data-ttu-id="bbb6a-199">Windows x64 może służyć do kompilowania Windows ARM32, ARM64 i x86 obrazów.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-199">Windows x64 can be used to compile Windows ARM32, ARM64, and x86 images.</span></span>
- <span data-ttu-id="bbb6a-200">Windows x86 może służyć do kompilowania Windows ARM32 obrazów.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-200">Windows x86 can be used to compile Windows ARM32 images.</span></span>
- <span data-ttu-id="bbb6a-201">Linux x64 może służyć do kompilowania obrazów systemu Linux ARM32 i ARM64.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-201">Linux x64 can be used to compile Linux ARM32 and ARM64 images.</span></span>

## <a name="build-copies-dependencies"></a><span data-ttu-id="bbb6a-202">Kopiuje zależności kompilacji</span><span class="sxs-lookup"><span data-stu-id="bbb6a-202">Build copies dependencies</span></span>

<span data-ttu-id="bbb6a-203">`dotnet build` Polecenia teraz kopiuje zależności NuGet dla aplikacji z pamięcią podręczną programu NuGet do folderu wyjściowego kompilacji.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-203">The `dotnet build` command now copies NuGet dependencies for your application from the NuGet cache to the build output folder.</span></span> <span data-ttu-id="bbb6a-204">Wcześniej zależności zostały skopiowane tylko jako część `dotnet publish`.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-204">Previously, dependencies were only copied as part of `dotnet publish`.</span></span>

<span data-ttu-id="bbb6a-205">Istnieją pewne operacje takie jak łączenie i razor strony publikowania, który nadal będzie wymagać publikowania.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-205">There are some operations, like linking and razor page publishing that will still require publishing.</span></span>

## <a name="local-tools"></a><span data-ttu-id="bbb6a-206">Narzędzia do lokalnego</span><span class="sxs-lookup"><span data-stu-id="bbb6a-206">Local tools</span></span>

<span data-ttu-id="bbb6a-207">.NET core 3.0 wprowadzono lokalne narzędzia.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-207">.NET Core 3.0 introduces local tools.</span></span> <span data-ttu-id="bbb6a-208">Lokalne narzędzia są podobne do [globalnego narzędzia](../tools/global-tools.md) , ale są skojarzone z określonej lokalizacji na dysku.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-208">Local tools are similar to [global tools](../tools/global-tools.md) but are associated with a particular location on disk.</span></span> <span data-ttu-id="bbb6a-209">Lokalne narzędzia nie są dostępne globalnie i są dystrybuowane jako pakiety NuGet.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-209">Local tools aren't available globally and are distributed as NuGet packages.</span></span>

> [!WARNING]
> <span data-ttu-id="bbb6a-210">Jeśli próbujesz lokalne narzędzia .NET Core 3.0 w wersji zapoznawczej 1, takie jak uruchamianie `dotnet tool restore` lub `dotnet tool install`, usuń folder pamięci podręcznej narzędzia lokalnego.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-210">If you tried local tools in .NET Core 3.0 Preview 1, such as running `dotnet tool restore` or `dotnet tool install`, delete the local tools cache folder.</span></span> <span data-ttu-id="bbb6a-211">W przeciwnym razie lokalne narzędzia nie będą działać na dowolnym nowszą wersją.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-211">Otherwise, local tools won't work on any newer release.</span></span> <span data-ttu-id="bbb6a-212">Ten folder znajduje się w:</span><span class="sxs-lookup"><span data-stu-id="bbb6a-212">This folder is located at:</span></span>
>
> <span data-ttu-id="bbb6a-213">W systemie macOS, Linux: `rm -r $HOME/.dotnet/toolResolverCache`</span><span class="sxs-lookup"><span data-stu-id="bbb6a-213">On macOS, Linux: `rm -r $HOME/.dotnet/toolResolverCache`</span></span>
>
> <span data-ttu-id="bbb6a-214">Na Windows: `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`</span><span class="sxs-lookup"><span data-stu-id="bbb6a-214">On Windows: `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`</span></span>

<span data-ttu-id="bbb6a-215">Lokalne narzędzia opierają się na nazwę pliku manifestu `dotnet-tools.json` w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-215">Local tools rely on a manifest file name `dotnet-tools.json` in your current directory.</span></span> <span data-ttu-id="bbb6a-216">Ten plik manifestu definiuje narzędzia była dostępna, w tym folderze, jak i poniżej.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-216">This manifest file defines the tools to be available at that folder and below.</span></span> <span data-ttu-id="bbb6a-217">Plik manifestu można rozpowszechniać w kodzie, aby upewnić się, że każdy, kto pracuje z kodem można przywrócić i używać tych samych narzędzi.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-217">You can distribute the manifest file with your code to ensure that anyone who works with your code can restore and use the same tools.</span></span>

<span data-ttu-id="bbb6a-218">Globalne i lokalne narzędzi zgodna wersja środowiska uruchomieniowego jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-218">For both global and local tools, a compatible version of the runtime is required.</span></span> <span data-ttu-id="bbb6a-219">Wiele narzędzi, obecnie w witrynie NuGet.org docelowej platformy .NET Core środowiska uruchomieniowego 2.1.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-219">Many tools currently on NuGet.org target .NET Core Runtime 2.1.</span></span> <span data-ttu-id="bbb6a-220">Aby zainstalować te narzędzia, globalnie lub lokalnie, czy nadal należy zainstalować [środowisko uruchomieniowe programu NET Core 2.1](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="bbb6a-220">To install these tools globally or locally, you would still need to install the [NET Core 2.1 Runtime](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span>

## <a name="major-version-roll-forward"></a><span data-ttu-id="bbb6a-221">Wersja główna przenoszenia do przodu</span><span class="sxs-lookup"><span data-stu-id="bbb6a-221">Major-version Roll Forward</span></span>

<span data-ttu-id="bbb6a-222">.NET core 3.0 wprowadzono to opcjonalna funkcja, która umożliwia aplikacji uaktualniane do najnowszej wersji głównej programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-222">.NET Core 3.0 introduces an opt-in feature that allows your app to roll forward to the latest major version of .NET Core.</span></span> <span data-ttu-id="bbb6a-223">Ponadto dodano nowe ustawienie do kontrolowania sposobu przenoszenia do przodu jest stosowany do swojej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-223">Additionally, a new setting has been added to control how roll forward is applied to your app.</span></span> <span data-ttu-id="bbb6a-224">Można to skonfigurować w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="bbb6a-224">This can be configured in the following ways:</span></span>

- <span data-ttu-id="bbb6a-225">Właściwości pliku projektu: `RollForward`</span><span class="sxs-lookup"><span data-stu-id="bbb6a-225">Project file property: `RollForward`</span></span>
- <span data-ttu-id="bbb6a-226">Właściwość pliku konfiguracji środowiska uruchomieniowego: `rollForward`</span><span class="sxs-lookup"><span data-stu-id="bbb6a-226">Runtime configuration file property: `rollForward`</span></span>
- <span data-ttu-id="bbb6a-227">Zmienna środowiskowa: `DOTNET_ROLL_FORWARD`</span><span class="sxs-lookup"><span data-stu-id="bbb6a-227">Environment variable: `DOTNET_ROLL_FORWARD`</span></span>
- <span data-ttu-id="bbb6a-228">Argument wiersza polecenia: `--roll-forward`</span><span class="sxs-lookup"><span data-stu-id="bbb6a-228">Command-line argument: `--roll-forward`</span></span>

<span data-ttu-id="bbb6a-229">Należy określić jedną z następujących wartości.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-229">One of the following values must be specified.</span></span> <span data-ttu-id="bbb6a-230">Jeśli ustawienie zostanie pominięty, **pomocnicza** jest ustawieniem domyślnym.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-230">If the setting is omitted, **Minor** is the default.</span></span>

- <span data-ttu-id="bbb6a-231">**LatestPatch**</span><span class="sxs-lookup"><span data-stu-id="bbb6a-231">**LatestPatch**</span></span>\
<span data-ttu-id="bbb6a-232">Uaktualniane najwyższa wersja poprawki.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-232">Roll forward to the highest patch version.</span></span> <span data-ttu-id="bbb6a-233">Powoduje to wyłączenie wersja pomocnicza przenoszenia do przodu.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-233">This disables minor version roll forward.</span></span>
- <span data-ttu-id="bbb6a-234">**Pomocnicza**</span><span class="sxs-lookup"><span data-stu-id="bbb6a-234">**Minor**</span></span>\
<span data-ttu-id="bbb6a-235">Uaktualniane do najniższego wyższej wersji pomocniczej, jeśli brakuje żądanej wersji pomocniczej.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-235">Roll forward to the lowest higher minor version, if requested minor version is missing.</span></span> <span data-ttu-id="bbb6a-236">Jeśli żądana wersja pomocnicza jest obecna, a następnie **LatestPatch** zasady są używane.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-236">If the requested minor version is present, then the **LatestPatch** policy is used.</span></span>
- <span data-ttu-id="bbb6a-237">**Główne**</span><span class="sxs-lookup"><span data-stu-id="bbb6a-237">**Major**</span></span>\
<span data-ttu-id="bbb6a-238">Uaktualniane do najniższego wyższej wersji głównej i najniższa wersja pomocnicza, jeśli brakuje żądanej wersji głównej.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-238">Roll forward to lowest higher major version, and lowest minor version, if requested major version is missing.</span></span> <span data-ttu-id="bbb6a-239">Jeśli żądana wersja główna jest obecny, a następnie **pomocnicza** zasady są używane.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-239">If the requested major version is present, then the **Minor** policy is used.</span></span>
- <span data-ttu-id="bbb6a-240">**LatestMinor**</span><span class="sxs-lookup"><span data-stu-id="bbb6a-240">**LatestMinor**</span></span>\
<span data-ttu-id="bbb6a-241">Uaktualniane do najwyższej wersji pomocniczej, nawet jeśli żądana wersja pomocnicza jest obecny.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-241">Roll forward to highest minor version, even if requested minor version is present.</span></span> <span data-ttu-id="bbb6a-242">Przeznaczony dla składnika w scenariuszach hostingu.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-242">Intended for component hosting scenarios.</span></span>
- <span data-ttu-id="bbb6a-243">**latestMajor**</span><span class="sxs-lookup"><span data-stu-id="bbb6a-243">**LatestMajor**</span></span>\
<span data-ttu-id="bbb6a-244">Przywracanie do przodu najwyższą główne i najwyższą wersję pomocniczą, nawet jeśli żądana głównych znajduje się.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-244">Roll forward to highest major and highest minor version, even if requested major is present.</span></span> <span data-ttu-id="bbb6a-245">Przeznaczony dla składnika w scenariuszach hostingu.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-245">Intended for component hosting scenarios.</span></span>
- <span data-ttu-id="bbb6a-246">**Wyłącz**</span><span class="sxs-lookup"><span data-stu-id="bbb6a-246">**Disable**</span></span>\
<span data-ttu-id="bbb6a-247">Nie przejdą do przodu.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-247">Don't roll forward.</span></span> <span data-ttu-id="bbb6a-248">Powiązać tylko z określonej wersji.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-248">Only bind to specified version.</span></span> <span data-ttu-id="bbb6a-249">Ta zasada nie jest zalecane do użytku ogólnego, ponieważ wyłącza możliwość uaktualniane najnowsze poprawki.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-249">This policy isn't recommended for general use because it disables the ability to roll forward to the latest patches.</span></span> <span data-ttu-id="bbb6a-250">Ta wartość jest zalecane tylko do testowania.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-250">This value is only recommended for testing.</span></span>

<span data-ttu-id="bbb6a-251">Oprócz **wyłączyć** ustawienie wszystkich ustawień użyje najwyższa wersja dostępna poprawka.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-251">Besides the **Disable** setting, all settings will use the highest available patch version.</span></span>

## <a name="windows-desktop"></a><span data-ttu-id="bbb6a-252">Pulpit systemu Windows</span><span class="sxs-lookup"><span data-stu-id="bbb6a-252">Windows desktop</span></span>

<span data-ttu-id="bbb6a-253">.NET core 3.0 obsługuje aplikacje pulpitu Windows za pomocą formularzy Windows i Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="bbb6a-253">.NET Core 3.0 supports Windows desktop applications using Windows Presentation Foundation (WPF) and Windows Forms.</span></span> <span data-ttu-id="bbb6a-254">Następujące struktury obsługi, za pomocą nowoczesnych kontrolek i Fluent stylów z biblioteki XAML interfejsu użytkownika systemu Windows (WinUI) za pośrednictwem [Wyspy XAML](/windows/uwp/xaml-platform/xaml-host-controls).</span><span class="sxs-lookup"><span data-stu-id="bbb6a-254">These frameworks also support using modern controls and Fluent styling from the Windows UI XAML Library (WinUI) via [XAML islands](/windows/uwp/xaml-platform/xaml-host-controls).</span></span>

<span data-ttu-id="bbb6a-255">Składnik Windows Desktop jest częścią Windows zestaw SDK programu .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-255">The Windows Desktop component is part of the Windows .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="bbb6a-256">Można utworzyć nowej aplikacji WPF i Windows Forms z następującymi `dotnet` poleceń:</span><span class="sxs-lookup"><span data-stu-id="bbb6a-256">You can create a new WPF or Windows Forms app with the following `dotnet` commands:</span></span>

```console
dotnet new wpf
dotnet new winforms
```

<span data-ttu-id="bbb6a-257">Visual Studio 2019 dodaje **nowy projekt** szablonów dla platformy .NET Core 3.0 Windows Forms i WPF.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-257">Visual Studio 2019 adds **New Project** templates for .NET Core 3.0 Windows Forms and WPF.</span></span>

<span data-ttu-id="bbb6a-258">Aby uzyskać więcej informacji na temat portów istniejącej aplikacji .NET Framework, zobacz [projekty WPF portu](../porting/wpf.md) i [projektów portu Windows Forms](../porting/winforms.md).</span><span class="sxs-lookup"><span data-stu-id="bbb6a-258">For more information about how to port an existing .NET Framework application, see [Port WPF projects](../porting/wpf.md) and [Port Windows Forms projects](../porting/winforms.md).</span></span>

## <a name="com-callable-components---windows-desktop"></a><span data-ttu-id="bbb6a-259">Składniki COM wywoływalnej — Windows Desktop</span><span class="sxs-lookup"><span data-stu-id="bbb6a-259">COM-callable components - Windows Desktop</span></span>

<span data-ttu-id="bbb6a-260">Na Windows można teraz utworzyć składniki COM-wywoływalnej zarządzane.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-260">On Windows, you can now create COM-callable managed components.</span></span> <span data-ttu-id="bbb6a-261">Ta możliwość jest krytyczna, .NET Core za pomocą modelu COM dodatku modeli, a także zapewnić zgodność z programem .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-261">This capability is critical to use .NET Core with COM add-in models and also to provide parity with .NET Framework.</span></span>

<span data-ttu-id="bbb6a-262">W odróżnieniu od .NET Framework gdzie *mscoree.dll* został użyty jako serwer COM, .NET Core doda uruchamianie natywnej biblioteki dll do *bin* katalogu podczas tworzenia składnika COM.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-262">Unlike .NET Framework where the *mscoree.dll* was used as the COM server, .NET Core will add a native launcher dll to the *bin* directory when you build your COM component.</span></span>

<span data-ttu-id="bbb6a-263">Na przykład sposobu tworzenia składnika modelu COM i używanie go zobacz [pokaz COM](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).</span><span class="sxs-lookup"><span data-stu-id="bbb6a-263">For an example of how to create a COM component and consume it, see the [COM Demo](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).</span></span>

## <a name="msix-deployment---windows-desktop"></a><span data-ttu-id="bbb6a-264">Wdrażanie MSIX — Windows Desktop</span><span class="sxs-lookup"><span data-stu-id="bbb6a-264">MSIX Deployment - Windows Desktop</span></span>

<span data-ttu-id="bbb6a-265">[MSIX](https://docs.microsoft.com/windows/msix/) jest nowy format pakietu aplikacji Windows.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-265">[MSIX](https://docs.microsoft.com/windows/msix/) is a new Windows application package format.</span></span> <span data-ttu-id="bbb6a-266">Może służyć do wdrażania aplikacji klasycznych .NET Core 3.0 dla systemu Windows 10.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-266">It can be used to deploy .NET Core 3.0 desktop applications to Windows 10.</span></span>

<span data-ttu-id="bbb6a-267">[Projekt pakietu aplikacji Windows](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), dostępne w programie Visual Studio 2019 r, pozwala na tworzenie pakietów MSIX [niezależna](../deploying/index.md#self-contained-deployments-scd) aplikacji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-267">The [Windows Application Packaging Project](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), available in Visual Studio 2019, allows you to create MSIX packages with [self-contained](../deploying/index.md#self-contained-deployments-scd) .NET Core applications.</span></span>

<span data-ttu-id="bbb6a-268">Plik projektu .NET Core, musisz określić obsługiwane środowiska uruchomieniowe w `<RuntimeIdentifiers>` właściwości:</span><span class="sxs-lookup"><span data-stu-id="bbb6a-268">The .NET Core project file must specify the supported runtimes in the `<RuntimeIdentifiers>` property:</span></span>

```xml
<RuntimeIdentifiers>win-x86;win-x64</RuntimeIdentifiers>
```

## <a name="winforms-highdpi"></a><span data-ttu-id="bbb6a-269">WinForms HighDPI</span><span class="sxs-lookup"><span data-stu-id="bbb6a-269">WinForms HighDPI</span></span>

<span data-ttu-id="bbb6a-270">Aplikacje .NET core Windows Forms można ustawić trybu wysokiej rozdzielczości, przy użyciu <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-270">.NET Core Windows Forms applications can set High DPI mode with <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType>.</span></span> <span data-ttu-id="bbb6a-271">`SetHighDpiMode` Metoda ustawia odpowiedni tryb wysokiej rozdzielczości, chyba że ustawienie została ustawiona za pomocą innych środków, takich jak `App.Manifest` lub P/Invoke przed `Application.Run`.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-271">The `SetHighDpiMode` method sets the corresponding High DPI mode unless the setting has been set by other means like `App.Manifest` or P/Invoke before `Application.Run`.</span></span>

<span data-ttu-id="bbb6a-272">Możliwe `highDpiMode` wartości, wyrażonych w <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType> wyliczenia są:</span><span class="sxs-lookup"><span data-stu-id="bbb6a-272">The possible `highDpiMode` values, as expressed by the <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType> enum are:</span></span>

* `DpiUnaware`
* `SystemAware`
* `PerMonitor`
* `PerMonitorV2`
* `DpiUnawareGdiScaled`

<span data-ttu-id="bbb6a-273">Aby uzyskać więcej informacji na temat trybów wysokiej rozdzielczości, zobacz [wysokiej rozdzielczości DPI aplikacji programowanie aplikacji klasycznych na Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows).</span><span class="sxs-lookup"><span data-stu-id="bbb6a-273">For more information about High DPI modes, see [High DPI Desktop Application Development on Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows).</span></span>

### <a name="ranges-and-indices"></a><span data-ttu-id="bbb6a-274">Zakresy i indeksy</span><span class="sxs-lookup"><span data-stu-id="bbb6a-274">Ranges and indices</span></span>

<span data-ttu-id="bbb6a-275">Nowy <xref:System.Index?displayProperty=nameWithType> typ może być używany do indeksowania.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-275">The new <xref:System.Index?displayProperty=nameWithType> type can be used for indexing.</span></span> <span data-ttu-id="bbb6a-276">Można utworzyć jeden z `int` , jest liczona od początku lub z prefiksem `^` — operator (C#), jest liczona od końca:</span><span class="sxs-lookup"><span data-stu-id="bbb6a-276">You can create one from an `int` that counts from the beginning, or with a prefix `^` operator (C#) that counts from the end:</span></span>

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

<span data-ttu-id="bbb6a-277">Istnieje również <xref:System.Range?displayProperty=nameWithType> typ, który składa się z dwóch `Index` wartości, jeden dla początkowego i jeden dla elementu end i mogą być zapisywane z `x..y` zakres wyrażenia (C#).</span><span class="sxs-lookup"><span data-stu-id="bbb6a-277">There's also the <xref:System.Range?displayProperty=nameWithType> type, which consists of two `Index` values, one for the start and one for the end, and can be written with a `x..y` range expression (C#).</span></span> <span data-ttu-id="bbb6a-278">Następnie można zaindeksować z `Range`, która generuje wycinek:</span><span class="sxs-lookup"><span data-stu-id="bbb6a-278">You can then index with a `Range`, which produces a slice:</span></span>

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

<span data-ttu-id="bbb6a-279">Aby uzyskać więcej informacji, zobacz [samouczek zakresów i indeksów](../../csharp/tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="bbb6a-279">For more information, see the [ranges and indices tutorial](../../csharp/tutorials/ranges-indexes.md).</span></span>

### <a name="async-streams"></a><span data-ttu-id="bbb6a-280">Asynchroniczne strumienie</span><span class="sxs-lookup"><span data-stu-id="bbb6a-280">Async streams</span></span>

<span data-ttu-id="bbb6a-281"><xref:System.Collections.Generic.IAsyncEnumerable%601> Typu jest nowa wersja asynchroniczne <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-281">The <xref:System.Collections.Generic.IAsyncEnumerable%601> type is a new asynchronous version of <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="bbb6a-282">Język umożliwia `await foreach` za pośrednictwem `IAsyncEnumerable<T>` używanie ich elementy i używać `yield return` do ich do produkcji elementów.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-282">The language lets you `await foreach` over `IAsyncEnumerable<T>` to consume their elements, and use `yield return` to them to produce elements.</span></span>

<span data-ttu-id="bbb6a-283">Poniższy przykład ilustruje środowiska produkcyjnego i zużycia strumieni asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-283">The following example demonstrates both production and consumption of async streams.</span></span> <span data-ttu-id="bbb6a-284">`foreach` Instrukcja jest asynchroniczne, a sam używa `yield return` do produkcji strumienia asynchronicznego dla obiektów wywołujących.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-284">The `foreach` statement is async and itself uses `yield return` to produce an async stream for callers.</span></span> <span data-ttu-id="bbb6a-285">Ten wzorzec (przy użyciu `yield return`) to zalecany model do produkcji strumieni asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-285">This pattern (using `yield return`) is the recommended model for producing async streams.</span></span>

```csharp
async IAsyncEnumerable<int> GetBigResultsAsync()
{
    await foreach (var result in GetResultsAsync())
    {
        if (result > 20) yield return result; 
    }
}
```

<span data-ttu-id="bbb6a-286">Oprócz możliwości `await foreach`, można również utworzyć async Iteratory, na przykład iterator, który zwraca `IAsyncEnumerable/IAsyncEnumerator` można zarówno `await` i `yield` w.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-286">In addition to being able to `await foreach`, you can also create async iterators, for example, an iterator that returns an `IAsyncEnumerable/IAsyncEnumerator` that you can both `await` and `yield` in.</span></span> <span data-ttu-id="bbb6a-287">W przypadku obiektów, które muszą zostać zlikwidowany, można użyć `IAsyncDisposable`, który implementuje różnych typów BCL, takich jak `Stream` i `Timer`.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-287">For objects that need to be disposed, you can use `IAsyncDisposable`, which various BCL types implement, such as `Stream` and `Timer`.</span></span>

<span data-ttu-id="bbb6a-288">Aby uzyskać więcej informacji, zobacz [samouczek strumieni asynchronicznych](../../csharp/tutorials/generate-consume-asynchronous-stream.md).</span><span class="sxs-lookup"><span data-stu-id="bbb6a-288">For more information, see the [async streams tutorial](../../csharp/tutorials/generate-consume-asynchronous-stream.md).</span></span>

## <a name="ieee-floating-point-improvements"></a><span data-ttu-id="bbb6a-289">Ulepszenia zmiennoprzecinkowej IEEE</span><span class="sxs-lookup"><span data-stu-id="bbb6a-289">IEEE Floating-point improvements</span></span>

<span data-ttu-id="bbb6a-290">Liczb zmiennoprzecinkowych punktu interfejsy API są aktualizowane do wykonania [poprawki 754-2008 IEEE](https://en.wikipedia.org/wiki/IEEE_754-2008_revision).</span><span class="sxs-lookup"><span data-stu-id="bbb6a-290">Floating point APIs are being updated to comply with [IEEE 754-2008 revision](https://en.wikipedia.org/wiki/IEEE_754-2008_revision).</span></span> <span data-ttu-id="bbb6a-291">Celem tych zmian jest do udostępnienia wszystkich **wymagane** operacji i upewnij się, że są one behaviorally zgodne ze specyfikacji IEEE. Aby uzyskać więcej informacji na temat ulepszenia zmiennoprzecinkowych zobacz [ulepszenia zmiennopozycyjna analizowania i formatowanie w .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) wpis w blogu.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-291">The goal of these changes is to expose all **required** operations and ensure that they're behaviorally compliant with the IEEE spec. For more information about floating-point improvements, see the [Floating-Point Parsing and Formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog post.</span></span>

<span data-ttu-id="bbb6a-292">Formatowanie z poprawkami i analizowanie obejmują:</span><span class="sxs-lookup"><span data-stu-id="bbb6a-292">Parsing and formatting fixes include:</span></span>

* <span data-ttu-id="bbb6a-293">Poprawnie przeanalizować i zaokrąglanie danych wejściowych o dowolnej długości.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-293">Correctly parse and round inputs of any length.</span></span>
* <span data-ttu-id="bbb6a-294">Poprawnie przeanalizować i sformatować ujemna zero.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-294">Correctly parse and format negative zero.</span></span>
* <span data-ttu-id="bbb6a-295">Poprawnie przeanalizować `Infinity` i `NaN` poprzez sposób wyboru bez uwzględniania wielkości liter, dzięki czemu, opcjonalny poprzedzających `+` jeśli ma to zastosowanie.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-295">Correctly parse `Infinity` and `NaN` by doing a case-insensitive check and allowing an optional preceding `+` where applicable.</span></span>

<span data-ttu-id="bbb6a-296">Nowe <xref:System.Math?displayProperty=nameWithType> obejmują interfejsy API:</span><span class="sxs-lookup"><span data-stu-id="bbb6a-296">New <xref:System.Math?displayProperty=nameWithType> APIs include:</span></span>

* <span data-ttu-id="bbb6a-297"><xref:System.Math.BitIncrement(System.Double)> i <xref:System.Math.BitDecrement(System.Double)></span><span class="sxs-lookup"><span data-stu-id="bbb6a-297"><xref:System.Math.BitIncrement(System.Double)> and <xref:System.Math.BitDecrement(System.Double)></span></span>\
<span data-ttu-id="bbb6a-298">Odnosi się do `nextUp` i `nextDown` IEEE operacji.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-298">Corresponds to the `nextUp` and `nextDown` IEEE operations.</span></span> <span data-ttu-id="bbb6a-299">Zwracają najmniejsza liczba zmiennoprzecinkowa porównuje w mniejszym lub większym niż dane wejściowe (odpowiednio).</span><span class="sxs-lookup"><span data-stu-id="bbb6a-299">They return the smallest floating-point number that compares greater or lesser than the input (respectively).</span></span> <span data-ttu-id="bbb6a-300">Na przykład `Math.BitIncrement(0.0)` zwróci `double.Epsilon`.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-300">For example, `Math.BitIncrement(0.0)` would return `double.Epsilon`.</span></span>

* <span data-ttu-id="bbb6a-301"><xref:System.Math.MaxMagnitude(System.Double,System.Double)> i <xref:System.Math.MinMagnitude(System.Double,System.Double)></span><span class="sxs-lookup"><span data-stu-id="bbb6a-301"><xref:System.Math.MaxMagnitude(System.Double,System.Double)> and <xref:System.Math.MinMagnitude(System.Double,System.Double)></span></span>\
<span data-ttu-id="bbb6a-302">Odnosi się do `maxNumMag` i `minNumMag` operacje IEEE zwracają wartość, która jest większy lub mniejszy w wielkości dwóch danych wejściowych (odpowiednio).</span><span class="sxs-lookup"><span data-stu-id="bbb6a-302">Corresponds to the `maxNumMag` and `minNumMag` IEEE operations, they return the value that is greater or lesser in magnitude of the two inputs (respectively).</span></span> <span data-ttu-id="bbb6a-303">Na przykład `Math.MaxMagnitude(2.0, -3.0)` zwróci `-3.0`.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-303">For example, `Math.MaxMagnitude(2.0, -3.0)` would return `-3.0`.</span></span>

* <xref:System.Math.ILogB(System.Double)>\
<span data-ttu-id="bbb6a-304">Odnosi się do `logB` IEEE operacji, która zwraca wartość całkowitą, zwraca całkowitą dziennik base 2 parametr wejściowy.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-304">Corresponds to the `logB` IEEE operation that returns an integral value, it returns the integral base-2 log of the input parameter.</span></span> <span data-ttu-id="bbb6a-305">Ta metoda skutecznie jest taka sama jak `floor(log2(x))`, ale pracy z minimalnym błąd zaokrąglania.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-305">This method is effectively the same as `floor(log2(x))`, but done with minimal rounding error.</span></span>

* <xref:System.Math.ScaleB(System.Double,System.Int32)>\
<span data-ttu-id="bbb6a-306">Odnosi się do `scaleB` IEEE operacji, która przyjmuje wartość całkowitą, funkcja zwraca skutecznie `x * pow(2, n)`, ale odbywa się przy użyciu minimalnego błąd zaokrąglania.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-306">Corresponds to the `scaleB` IEEE operation that takes an integral value, it returns effectively `x * pow(2, n)`, but is done with minimal rounding error.</span></span>

* <xref:System.Math.Log2(System.Double)>\
<span data-ttu-id="bbb6a-307">Odnosi się do `log2` operacji IEEE Zwraca logarytm o podstawie 2 dla podanego.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-307">Corresponds to the `log2` IEEE operation, it returns the base-2 logarithm.</span></span> <span data-ttu-id="bbb6a-308">Minimalizuje błędów zaokrąglania.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-308">It minimizes rounding error.</span></span>

* <xref:System.Math.FusedMultiplyAdd(System.Double,System.Double,System.Double)>\
<span data-ttu-id="bbb6a-309">Odnosi się do `fma` wykonuje operację IEEE kolei wielokrotnie dodać.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-309">Corresponds to the `fma` IEEE operation, it performs a fused multiply add.</span></span> <span data-ttu-id="bbb6a-310">Oznacza to robi `(x * y) + z` jako pojedyncza operacja,-, minimalizując błąd zaokrąglania.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-310">That is, it does `(x * y) + z` as a single operation, there-by minimizing the rounding error.</span></span> <span data-ttu-id="bbb6a-311">Przykładem może być `FusedMultiplyAdd(1e308, 2.0, -1e308)` co powoduje zwrócenie `1e308`.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-311">An example would be `FusedMultiplyAdd(1e308, 2.0, -1e308)` which returns `1e308`.</span></span> <span data-ttu-id="bbb6a-312">Regularne `(1e308 * 2.0) - 1e308` zwraca `double.PositiveInfinity`.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-312">The regular `(1e308 * 2.0) - 1e308` returns `double.PositiveInfinity`.</span></span>

* <xref:System.Math.CopySign(System.Double,System.Double)>\
<span data-ttu-id="bbb6a-313">Odnosi się do `copySign` IEEE operację, zwraca wartość `x`, ale przy użyciu konta z `y`.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-313">Corresponds to the `copySign` IEEE operation, it returns the value of `x`, but with the sign of `y`.</span></span>

## <a name="fast-built-in-json-support"></a><span data-ttu-id="bbb6a-314">Szybkie wbudowanej obsługi formatu JSON</span><span class="sxs-lookup"><span data-stu-id="bbb6a-314">Fast built-in JSON support</span></span>

<span data-ttu-id="bbb6a-315">Użytkownicy platformy .NET ma dużym stopniu polegać [ **Json.NET** ](https://www.newtonsoft.com/json) i innych popularnych bibliotek JSON, które nadal dobrych wyborów.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-315">.NET users have largely relied on [**Json.NET**](https://www.newtonsoft.com/json) and other popular JSON libraries, which continue to be good choices.</span></span> <span data-ttu-id="bbb6a-316">**Program Json.NET** używa ciągów .NET jako jej podstawowy typ danych, który jest pod maską UTF-16.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-316">**Json.NET** uses .NET strings as its base datatype, which is UTF-16 under the hood.</span></span>

<span data-ttu-id="bbb6a-317">Nowa funkcja wbudowanej obsługi JSON to alokacji o wysokiej wydajności, niski i oparte na `Span<byte>`.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-317">The new built-in JSON support is high-performance, low allocation, and based on `Span<byte>`.</span></span> <span data-ttu-id="bbb6a-318">Trzy nowe główne powiązane JSON typy zostały dodane do platformy .NET Core 3.0 <xref:System.Text.Json?displayProperty=nameWithType> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-318">Three new main JSON-related types have been added to .NET Core 3.0 the <xref:System.Text.Json?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="bbb6a-319">Te typy nie *jeszcze* obsługuje zwykłe stare CLR obiektu (POCO) serializacji i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-319">These types don't *yet* support plain old CLR object (POCO) serialization and deserialization.</span></span>

### <a name="utf8jsonreader"></a><span data-ttu-id="bbb6a-320">Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="bbb6a-320">Utf8JsonReader</span></span>

<span data-ttu-id="bbb6a-321"><xref:System.Text.Json.Utf8JsonReader?displayProperty=nameWithType> jest o wysokiej wydajności, niski alokacji, tylko do przodu czytnik UTF-8 kodowany w formacie JSON tekst odczytywane `ReadOnlySpan<byte>`.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-321"><xref:System.Text.Json.Utf8JsonReader?displayProperty=nameWithType> is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a `ReadOnlySpan<byte>`.</span></span> <span data-ttu-id="bbb6a-322">`Utf8JsonReader` Jest typem podstawowe, niskiego poziomu, który może służyć do tworzenia niestandardowych analizatory i deserializers.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-322">The `Utf8JsonReader` is a foundational, low-level type, that can be used to build custom parsers and deserializers.</span></span> <span data-ttu-id="bbb6a-323">Odczytywanie za pośrednictwem ładunek w formacie JSON za pomocą nowego `Utf8JsonReader` wynosi 2 x szybciej niż przy użyciu czytnika, z **Json.NET**.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-323">Reading through a JSON payload using the new `Utf8JsonReader` is 2x faster than using the reader from **Json.NET**.</span></span> <span data-ttu-id="bbb6a-324">Go nie przydzielić, dopóki nie trzeba actualize tokenów JSON jako ciągi (UTF-16).</span><span class="sxs-lookup"><span data-stu-id="bbb6a-324">It doesn't allocate until you need to actualize JSON tokens as (UTF-16) strings.</span></span>

<span data-ttu-id="bbb6a-325">Oto przykład przeczytanie [ **launch.json** ](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) plik utworzony przez Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="bbb6a-325">Here is an example of reading through the [**launch.json**](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) file created by Visual Studio Code:</span></span>

[!CODE-csharp[Utf8JsonReader](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#PrintJson)]

[!CODE-csharp[Utf8JsonReader](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#PrintJsonCall)]

### <a name="utf8jsonwriter"></a><span data-ttu-id="bbb6a-326">Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="bbb6a-326">Utf8JsonWriter</span></span>

<span data-ttu-id="bbb6a-327"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType> zapewnia wysoce wydajnych niebuforowanym, tylko do zapisu kodowany w formacie UTF-8 do przodu tekstu JSON z popularnych typów .NET, takich jak `String`, `Int32`, i `DateTime`.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-327"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType> provides a high-performance, non-cached, forward-only way to write UTF-8 encoded JSON text from common .NET types like `String`, `Int32`, and `DateTime`.</span></span> <span data-ttu-id="bbb6a-328">Podobnie jak czytelnik moduł zapisujący jest typem podstawowe, niskiego poziomu, który może służyć do tworzenia niestandardowych serializatory.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-328">Like the reader, the writer is a foundational, low-level type, that can be used to build custom serializers.</span></span> <span data-ttu-id="bbb6a-329">Zapis ładunku JSON za pomocą nowego `Utf8JsonWriter` wynosi 30-80% szybciej niż przy użyciu składnika zapisywania z **Json.NET** i nie alokować.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-329">Writing a JSON payload using the new `Utf8JsonWriter` is 30-80% faster than using the writer from **Json.NET** and doesn't allocate.</span></span>

### <a name="jsondocument"></a><span data-ttu-id="bbb6a-330">JsonDocument</span><span class="sxs-lookup"><span data-stu-id="bbb6a-330">JsonDocument</span></span>

<span data-ttu-id="bbb6a-331"><xref:System.Text.Json.JsonDocument?displayProperty=nameWithType> jest wbudowana w górnej części `Utf8JsonReader`.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-331"><xref:System.Text.Json.JsonDocument?displayProperty=nameWithType> is built on top of the `Utf8JsonReader`.</span></span> <span data-ttu-id="bbb6a-332">`JsonDocument` Zapewnia możliwość analizowania danych JSON i dokonać jego kompilacji tylko do odczytu modelu DOM (Document Object) można wykonywać zapytania do obsługi dostępu losowego i wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-332">The `JsonDocument` provides the ability to parse JSON data and build a read-only Document Object Model (DOM) that can be queried to support random access and enumeration.</span></span> <span data-ttu-id="bbb6a-333">Elementy JSON, które tworzą dane można uzyskać dostęp za pośrednictwem <xref:System.Text.Json.JsonElement> typ, który jest udostępniany przez `JsonDocument` jako właściwość o nazwie `RootElement`.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-333">The JSON elements that compose the data can be accessed via the <xref:System.Text.Json.JsonElement> type that is exposed by the `JsonDocument` as a property called `RootElement`.</span></span> <span data-ttu-id="bbb6a-334">`JsonElement` Zawiera wyliczenia tablicy i obiektów JSON, wraz z interfejsów API do konwertowania tekstu JSON do popularnych typów .NET.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-334">The `JsonElement` contains the JSON array and object enumerators along with APIs to convert JSON text to common .NET types.</span></span> <span data-ttu-id="bbb6a-335">Analizowanie typowe ładunek w formacie JSON i uzyskiwania dostępu do wszystkich jej członków przy użyciu `JsonDocument` jest szybsza niż x 2 – 3 **Json.NET** z przydziałem niewielkie ilości danych, które stosowne o rozmiarze (czyli < 1 MB).</span><span class="sxs-lookup"><span data-stu-id="bbb6a-335">Parsing a typical JSON payload and accessing all its members using the `JsonDocument` is 2-3x faster than **Json.NET** with little allocations for data that is reasonably sized (that is, < 1 MB).</span></span>

<span data-ttu-id="bbb6a-336">Poniżej przedstawiono przykładowe zastosowanie `JsonDocument` i `JsonElement` mogą służyć jako punkt początkowy:</span><span class="sxs-lookup"><span data-stu-id="bbb6a-336">Here is a sample usage of the `JsonDocument` and `JsonElement` that can be used as a starting point:</span></span>

<span data-ttu-id="bbb6a-337">Oto C# 8.0 przykład przeczytanie [ **launch.json** ](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) plik utworzony przez Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="bbb6a-337">Here is a C# 8.0 example of reading through the [**launch.json**](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) file created by Visual Studio Code:</span></span>

[!CODE-csharp[JsonDocument](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#ReadJson)]

[!CODE-csharp[JsonDocument](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#ReadJsonCall)]

### <a name="jsonserializer"></a><span data-ttu-id="bbb6a-338">JsonSerializer</span><span class="sxs-lookup"><span data-stu-id="bbb6a-338">JsonSerializer</span></span>

<span data-ttu-id="bbb6a-339"><xref:System.Text.Json.Serialization.JsonSerializer?displayProperty=nameWithType> jest wbudowana w górnej części <xref:System.Text.Json.Utf8JsonReader> i <xref:System.Text.Json.Utf8JsonWriter> zapewnienie opcję szeregowania szybko małej ilości pamięci, pracując z dokumentów JSON i fragmenty.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-339"><xref:System.Text.Json.Serialization.JsonSerializer?displayProperty=nameWithType> is built on top of <xref:System.Text.Json.Utf8JsonReader> and <xref:System.Text.Json.Utf8JsonWriter> to provide a fast low-memory serialization option when working with JSON documents and fragments.</span></span>

<span data-ttu-id="bbb6a-340">Sprawdź: https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/docs/SerializerProgrammingModel.md na przykład do portu na w tym artykule</span><span class="sxs-lookup"><span data-stu-id="bbb6a-340">EXAMINE: https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/docs/SerializerProgrammingModel.md for an example to port to this article</span></span>

<span data-ttu-id="bbb6a-341">Oto przykład serializacji obiektu do formatu JSON:</span><span class="sxs-lookup"><span data-stu-id="bbb6a-341">Here is an example of serializing an object to JSON:</span></span>

[!CODE-csharp[JsonSerializer](~/samples/snippets/core/whats-new/whats-new-in-30/cs/JSON.cs#JsonSerialize)]

<span data-ttu-id="bbb6a-342">Oto przykład deserializacji ciągu JSON na obiekt.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-342">Here is an example of deserializing a JSON string to an object.</span></span> <span data-ttu-id="bbb6a-343">Można użyć ciągu JSON utworzony w poprzednim przykładzie:</span><span class="sxs-lookup"><span data-stu-id="bbb6a-343">You can use the JSON string produced by the previous example:</span></span>

[!CODE-csharp[JsonDeserializer](~/samples/snippets/core/whats-new/whats-new-in-30/cs/JSON.cs#JsonDeserialize)]

## <a name="interop-improvements"></a><span data-ttu-id="bbb6a-344">Ulepszenia międzyoperacyjności</span><span class="sxs-lookup"><span data-stu-id="bbb6a-344">Interop improvements</span></span>

<span data-ttu-id="bbb6a-345">.NET core 3.0 to zwiększa natywnych międzyoperacyjności interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-345">.NET Core 3.0 improves native API interop.</span></span>

### <a name="type-nativelibrary"></a><span data-ttu-id="bbb6a-346">Wpisz: NativeLibrary</span><span class="sxs-lookup"><span data-stu-id="bbb6a-346">Type: NativeLibrary</span></span>

<span data-ttu-id="bbb6a-347"><xref:System.Runtime.InteropServices.NativeLibrary?displayProperty=nameWithType> zapewnia hermetyzację ładowania natywnej biblioteki (przy użyciu tej samej logiki obciążenia jako .NET Core P/Invoke) i podając takie jak funkcje pomocnicze odpowiednie `getSymbol`.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-347"><xref:System.Runtime.InteropServices.NativeLibrary?displayProperty=nameWithType> provides an encapsulation for loading a native library (using the same load logic as .NET Core P/Invoke) and providing the relevant helper functions such as `getSymbol`.</span></span> <span data-ttu-id="bbb6a-348">Dla przykładu kodu zobacz [pokaz DLLMap](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin).</span><span class="sxs-lookup"><span data-stu-id="bbb6a-348">For a code example, see the [DLLMap Demo](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin).</span></span>

### <a name="windows-native-interop"></a><span data-ttu-id="bbb6a-349">Współdziałanie natywne Windows</span><span class="sxs-lookup"><span data-stu-id="bbb6a-349">Windows Native Interop</span></span>

<span data-ttu-id="bbb6a-350">Windows oferuje rozbudowane natywnych interfejsów API w formie płaskiej interfejsów API języka C, COM i WinRT.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-350">Windows offers a rich native API in the form of flat C APIs, COM, and WinRT.</span></span> <span data-ttu-id="bbb6a-351">Podczas gdy platformy .NET Core obsługuje **P/Invoke**, .NET Core 3.0 dodaje możliwość **CoCreate interfejsów API modelu COM** i **aktywować interfejsów API WinRT**.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-351">While .NET Core supports **P/Invoke**, .NET Core 3.0 adds the ability to **CoCreate COM APIs** and **Activate WinRT APIs**.</span></span> <span data-ttu-id="bbb6a-352">Dla przykładu kodu zobacz [wersji demonstracyjnej programu Excel](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).</span><span class="sxs-lookup"><span data-stu-id="bbb6a-352">For a code example, see the [Excel Demo](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).</span></span>

## <a name="http2-support"></a><span data-ttu-id="bbb6a-353">Obsługa protokołu HTTP/2</span><span class="sxs-lookup"><span data-stu-id="bbb6a-353">HTTP/2 support</span></span>

<span data-ttu-id="bbb6a-354"><xref:System.Net.Http.HttpClient?displayProperty=nameWithType> Typu obsługuje protokół HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-354">The <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> type supports the HTTP/2 protocol.</span></span> <span data-ttu-id="bbb6a-355">Włączenie protokołu HTTP/2 za pośrednictwem protokołu TLS/ALPN negocjowane jest wersji protokołu HTTP i protokołu HTTP/2 jest używany, gdy serwer wybiera z niej korzystać.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-355">If HTTP/2 is enabled, the HTTP protocol version is negotiated via TLS/ALPN, and HTTP/2 is used if the server elects to use it.</span></span>

<span data-ttu-id="bbb6a-356">Domyślnym protokołem pozostają HTTP/1.1, ale można włączyć protokołu HTTP/2 na dwa różne sposoby.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-356">The default protocol remains HTTP/1.1, but HTTP/2 can be enabled in two different ways.</span></span> <span data-ttu-id="bbb6a-357">Po pierwsze można ustawić komunikat żądania HTTP do użycia protokołu HTTP/2:</span><span class="sxs-lookup"><span data-stu-id="bbb6a-357">First, you can set the HTTP request message to use HTTP/2:</span></span>

[!CODE-csharp[Http2Request](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Request)]

<span data-ttu-id="bbb6a-358">Po drugie, można zmienić <xref:System.Net.Http.HttpClient> do domyślnie używają protokołu HTTP/2:</span><span class="sxs-lookup"><span data-stu-id="bbb6a-358">Second, you can change <xref:System.Net.Http.HttpClient> to use HTTP/2 by default:</span></span>

[!CODE-csharp[Http2Client](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Client)]

<span data-ttu-id="bbb6a-359">Wiele razy, gdy tworzysz aplikację, chcesz korzystanie z połączenia nieszyfrowanego.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-359">Many times when you're developing an application, you want to use an unencrypted connection.</span></span> <span data-ttu-id="bbb6a-360">Jeśli wiesz, że docelowy punkt końcowy będzie korzystać z protokołu HTTP/2, można włączyć połączenia nieszyfrowanego protokołu HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-360">If you know the target endpoint will be using HTTP/2, you can turn on unencrypted connections for HTTP/2.</span></span> <span data-ttu-id="bbb6a-361">Można ją włączyć, ustawiając `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT` zmiennej środowiskowej, aby `1` lub, włączając je w kontekście aplikacji:</span><span class="sxs-lookup"><span data-stu-id="bbb6a-361">You can turn it on by setting the `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT` environment variable to `1` or by enabling it in the app context:</span></span>

[!CODE-csharp[Http2Context](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#AppContext)]

## <a name="tls-13--openssl-111-on-linux"></a><span data-ttu-id="bbb6a-362">TLS 1.3 & OpenSSL 1.1.1 w systemie Linux</span><span class="sxs-lookup"><span data-stu-id="bbb6a-362">TLS 1.3 & OpenSSL 1.1.1 on Linux</span></span>

<span data-ttu-id="bbb6a-363">.NET core korzysta z zalet [Obsługa protokołu TLS 1.3 w OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), gdy będzie ona dostępna w danym środowisku.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-363">.NET Core now takes advantage of [TLS 1.3 support in OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), when it's available in a given environment.</span></span> <span data-ttu-id="bbb6a-364">Za pomocą protokołu TLS 1.3:</span><span class="sxs-lookup"><span data-stu-id="bbb6a-364">With TLS 1.3:</span></span>

* <span data-ttu-id="bbb6a-365">Zwiększona czasy połączeń z ograniczoną liczbę rund wymagane między klientem i serwerem.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-365">Connection times are improved with reduced round trips required between the client and server.</span></span>
* <span data-ttu-id="bbb6a-366">Ulepszone zabezpieczenia ze względu na usunięcie rozmaite algorytmy kryptograficzne przestarzały i niebezpieczne.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-366">Improved security because of the removal of various obsolete and insecure cryptographic algorithms.</span></span>

<span data-ttu-id="bbb6a-367">Jeśli są dostępne, korzysta z platformy .NET Core 3.0 **OpenSSL 1.1.1**, **OpenSSL 1.1.0**, lub **OpenSSL 1.0.2** w systemie Linux.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-367">When available, .NET Core 3.0 uses **OpenSSL 1.1.1**, **OpenSSL 1.1.0**, or **OpenSSL 1.0.2** on a Linux system.</span></span> <span data-ttu-id="bbb6a-368">Gdy **OpenSSL 1.1.1** jest dostępny, zarówno <xref:System.Net.Security.SslStream?displayProperty=nameWithType> i <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> użyje typy **TLS 1.3** (zakładając, że obsługa klienta i serwera **TLS 1.3**).</span><span class="sxs-lookup"><span data-stu-id="bbb6a-368">When **OpenSSL 1.1.1** is available, both <xref:System.Net.Security.SslStream?displayProperty=nameWithType> and <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> types will use **TLS 1.3** (assuming both the client and server support **TLS 1.3**).</span></span>

>[!IMPORTANT]
><span data-ttu-id="bbb6a-369">Windows i macOS nie jest jeszcze obsługiwany **TLS 1.3**.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-369">Windows and macOS do not yet support **TLS 1.3**.</span></span> <span data-ttu-id="bbb6a-370">.NET core 3.0 to będzie obsługiwać **TLS 1.3** w tych systemach operacyjnych po udostępnieniu Pomocy technicznej.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-370">.NET Core 3.0 will support **TLS 1.3** on these operating systems when support becomes available.</span></span>

<span data-ttu-id="bbb6a-371">Następujące C# .NET Core 3.0 w 18.10 Ubuntu nawiązywania połączenia z przykładowym 8.0 <https://www.cloudflare.com>:</span><span class="sxs-lookup"><span data-stu-id="bbb6a-371">The following C# 8.0 example demonstrates .NET Core 3.0 on Ubuntu 18.10 connecting to <https://www.cloudflare.com>:</span></span>

[!CODE-csharp[TLSExample](~/samples/snippets/core/whats-new/whats-new-in-30/cs/TLS.cs#TLS)]

## <a name="cryptography-ciphers"></a><span data-ttu-id="bbb6a-372">Szyfry kryptografii</span><span class="sxs-lookup"><span data-stu-id="bbb6a-372">Cryptography ciphers</span></span>

<span data-ttu-id="bbb6a-373">.NET 3.0 dodaje obsługę **AES-GCM** i **AES-CCM** szyfrów, implementowane za pomocą <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> i <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-373">.NET 3.0 adds support for **AES-GCM** and **AES-CCM** ciphers, implemented with <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> and <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> respectively.</span></span> <span data-ttu-id="bbb6a-374">Te algorytmy są [uwierzytelnione szyfrowanie za pomocą algorytmów skojarzenia danych (AEAD)](https://en.wikipedia.org/wiki/Authenticated_encryption).</span><span class="sxs-lookup"><span data-stu-id="bbb6a-374">These algorithms are both [Authenticated Encryption with Association Data (AEAD) algorithms](https://en.wikipedia.org/wiki/Authenticated_encryption).</span></span>

<span data-ttu-id="bbb6a-375">Poniższy kod demonstruje użycie `AesGcm` szyfrowania do szyfrowania i odszyfrowywania danych losowych.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-375">The following code demonstrates using `AesGcm` cipher to encrypt and decrypt random data.</span></span>

[!CODE-csharp[AesGcm](~/samples/snippets/core/whats-new/whats-new-in-30/cs/Cipher.cs#AesGcm)]

## <a name="cryptographic-key-importexport"></a><span data-ttu-id="bbb6a-376">Kryptograficznych kluczy importu/eksportu</span><span class="sxs-lookup"><span data-stu-id="bbb6a-376">Cryptographic Key Import/Export</span></span>

<span data-ttu-id="bbb6a-377">.NET core 3.0 obsługuje importowanie i eksportowanie kluczy asymetrycznych publicznych i prywatnych z standardowych formatów.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-377">.NET Core 3.0 supports the import and export of asymmetric public and private keys from standard formats.</span></span> <span data-ttu-id="bbb6a-378">Nie należy używać certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-378">You don't need to use an X.509 certificate.</span></span>

<span data-ttu-id="bbb6a-379">Wszystkie klucza typów, takich jak *RSA*, *DSA*, *ECDsa*, i *ECDiffieHellman*, obsługuje następujące formaty:</span><span class="sxs-lookup"><span data-stu-id="bbb6a-379">All key types, such as *RSA*, *DSA*, *ECDsa*, and *ECDiffieHellman*, support the following formats:</span></span>

* <span data-ttu-id="bbb6a-380">**Klucz publiczny**</span><span class="sxs-lookup"><span data-stu-id="bbb6a-380">**Public Key**</span></span>
  * <span data-ttu-id="bbb6a-381">X.509 SubjectPublicKeyInfo</span><span class="sxs-lookup"><span data-stu-id="bbb6a-381">X.509 SubjectPublicKeyInfo</span></span>

* <span data-ttu-id="bbb6a-382">**klucz prywatny**</span><span class="sxs-lookup"><span data-stu-id="bbb6a-382">**Private key**</span></span>
  * <span data-ttu-id="bbb6a-383">PKCS #8 PrivateKeyInfo</span><span class="sxs-lookup"><span data-stu-id="bbb6a-383">PKCS#8 PrivateKeyInfo</span></span>
  * <span data-ttu-id="bbb6a-384">PKCS#8 EncryptedPrivateKeyInfo</span><span class="sxs-lookup"><span data-stu-id="bbb6a-384">PKCS#8 EncryptedPrivateKeyInfo</span></span>

<span data-ttu-id="bbb6a-385">RSA również klucze pomocy technicznej:</span><span class="sxs-lookup"><span data-stu-id="bbb6a-385">RSA keys also support:</span></span>

* <span data-ttu-id="bbb6a-386">**Klucz publiczny**</span><span class="sxs-lookup"><span data-stu-id="bbb6a-386">**Public Key**</span></span>
  * <span data-ttu-id="bbb6a-387">PKCS#1 RSAPublicKey</span><span class="sxs-lookup"><span data-stu-id="bbb6a-387">PKCS#1 RSAPublicKey</span></span>

* <span data-ttu-id="bbb6a-388">**klucz prywatny**</span><span class="sxs-lookup"><span data-stu-id="bbb6a-388">**Private key**</span></span>
  * <span data-ttu-id="bbb6a-389">PKCS #1 RSAPrivateKey</span><span class="sxs-lookup"><span data-stu-id="bbb6a-389">PKCS#1 RSAPrivateKey</span></span>

<span data-ttu-id="bbb6a-390">Metody eksportowania generuje dane binarne zakodowane w formacie DER i metod import oczekiwać takie same.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-390">The export methods produce DER-encoded binary data, and the import methods expect the same.</span></span> <span data-ttu-id="bbb6a-391">Jeśli klucz jest przechowywany w formacie PEM przyjaznego tekstu, obiekt wywołujący, będą musieli base64 — dekodowanie zawartości przed wywołaniem metody importu.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-391">If a key is stored in the text-friendly PEM format, the caller will need to base64-decode the content before calling an import method.</span></span>

[!CODE-csharp[RSA](~/samples/snippets/core/whats-new/whats-new-in-30/cs/RSA.cs#Rsa)]

<span data-ttu-id="bbb6a-392">**PKCS #8** pliki mogą być kontrolowane za pomocą <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType> i **PFX/PKCS #12** pliki mogą być kontrolowane za pomocą <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-392">**PKCS#8** files can be inspected with <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType> and **PFX/PKCS#12** files can be inspected with <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType>.</span></span> <span data-ttu-id="bbb6a-393">**Plik PFX/PKCS #12** pliki mogą być zmieniane za pomocą <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-393">**PFX/PKCS#12** files can be manipulated with <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType>.</span></span>

## <a name="serialport-for-linux"></a><span data-ttu-id="bbb6a-394">Portu SerialPort dla systemu Linux</span><span class="sxs-lookup"><span data-stu-id="bbb6a-394">SerialPort for Linux</span></span>

<span data-ttu-id="bbb6a-395">Obsługuje platformy .NET core 3.0 <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> w systemie Linux.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-395">.NET Core 3.0 supports <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> on Linux.</span></span>

<span data-ttu-id="bbb6a-396">Wcześniej, .NET Core obsługiwana tylko przy użyciu `SerialPort` na Windows.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-396">Previously, .NET Core only supported using `SerialPort` on Windows.</span></span>

## <a name="docker-and-cgroup-memory-limits"></a><span data-ttu-id="bbb6a-397">Ogranicza platformy docker i cgroup pamięci</span><span class="sxs-lookup"><span data-stu-id="bbb6a-397">Docker and cgroup memory Limits</span></span>

<span data-ttu-id="bbb6a-398">Począwszy od wersji zapoznawczej 3 działającej platformy .NET Core 3.0 w systemie Linux przy użyciu rozwiązania Docker działa lepiej z cgroup limity pamięci.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-398">Starting with Preview 3, running .NET Core 3.0 on Linux with Docker works better with cgroup memory limits.</span></span> <span data-ttu-id="bbb6a-399">Uruchomiony kontener platformy Docker z limitami pamięci, takich jak z `docker run -m`, zmienia sposób działania platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-399">Running a Docker container with memory limits, such as with `docker run -m`, changes how .NET Core behaves.</span></span>

* <span data-ttu-id="bbb6a-400">Domyślny rozmiar sterty modułu odśmiecania pamięci (GC): Maksymalna liczba o rozmiarze 20 mb lub 75% limitu pamięci dla kontenera.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-400">Default Garbage Collector (GC) heap size: maximum of 20 mb or 75% of the memory limit on the container.</span></span>
* <span data-ttu-id="bbb6a-401">Jawny rozmiar można ustawić jako wartość bezwzględna liczby lub wartości procentowej cgroup limitu.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-401">Explicit size can be set as an absolute number or percentage of cgroup limit.</span></span>
* <span data-ttu-id="bbb6a-402">Rozmiar minimalny zastrzeżonego segmentu na stercie GC to 16 mb.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-402">Minimum reserved segment size per GC heap is 16 mb.</span></span> <span data-ttu-id="bbb6a-403">Ten rozmiar zmniejsza liczbę stosów, które są tworzone na maszynach.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-403">This size reduces the number of heaps that are created on machines.</span></span>

## <a name="smaller-garbage-collection-heap-sizes"></a><span data-ttu-id="bbb6a-404">Mniejsze rozmiary stercie wyrzucania elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="bbb6a-404">Smaller Garbage Collection heap sizes</span></span>

<span data-ttu-id="bbb6a-405">Rozmiar sterty domyślny moduł Garbage Collector została zmniejszona skutkuje platformy .NET Core przy użyciu mniejszej ilości pamięci.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-405">The Garbage Collector's default heap size has been reduced resulting in .NET Core using less memory.</span></span> <span data-ttu-id="bbb6a-406">Ta zmiana lepszego dopasowania z budżetem generacji 0 alokacji o rozmiarze pamięci podręcznej nowoczesny procesor.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-406">This change better aligns with the generation 0 allocation budget with modern processor cache sizes.</span></span>

## <a name="garbage-collection-large-page-support"></a><span data-ttu-id="bbb6a-407">Obsługa dużych stron kolekcji wyrzucania elementów</span><span class="sxs-lookup"><span data-stu-id="bbb6a-407">Garbage Collection Large Page support</span></span>

<span data-ttu-id="bbb6a-408">Dużych stron (nazywanego także ogromny stron w systemie Linux) jest funkcją, w którym system operacyjny jest możliwość ustanowienia regionami pamięci jest większy niż rozmiar strony natywnej (często 4K), aby zwiększyć wydajność aplikacji żądanie te dużych stron.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-408">Large Pages (also known as Huge Pages on Linux) is a feature where the operating system is able to establish memory regions larger than the native page size (often 4K) to improve performance of the application requesting these large pages.</span></span>

<span data-ttu-id="bbb6a-409">Teraz można skonfigurować moduł zbierający elementy bezużyteczne **GCLargePages** ustawienie jako opcjonalna funkcja alokować dużych stron na Windows.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-409">The Garbage Collector can now be configured with the **GCLargePages** setting as an opt-in feature to choose to allocate large pages on Windows.</span></span>

## <a name="gpio-support-for-raspberry-pi"></a><span data-ttu-id="bbb6a-410">Interfejs GPIO obsługa urządzenia Raspberry Pi</span><span class="sxs-lookup"><span data-stu-id="bbb6a-410">GPIO Support for Raspberry Pi</span></span>

<span data-ttu-id="bbb6a-411">Zostały wydane dwa pakiety NuGet, używanej do programowania GPIO:</span><span class="sxs-lookup"><span data-stu-id="bbb6a-411">Two packages have been released to NuGet that you can use for GPIO programming:</span></span>

* [<span data-ttu-id="bbb6a-412">System.Device.Gpio</span><span class="sxs-lookup"><span data-stu-id="bbb6a-412">System.Device.Gpio</span></span>](https://www.nuget.org/packages/System.Device.Gpio)
* [<span data-ttu-id="bbb6a-413">Iot.Device.Bindings</span><span class="sxs-lookup"><span data-stu-id="bbb6a-413">Iot.Device.Bindings</span></span>](https://www.nuget.org/packages/Iot.Device.Bindings)

<span data-ttu-id="bbb6a-414">Pakiety GPIO zawierają interfejsy API dla *GPIO*, *SPI*, *I2C*, i *PWM* urządzeń.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-414">The GPIO packages include APIs for *GPIO*, *SPI*, *I2C*, and *PWM* devices.</span></span> <span data-ttu-id="bbb6a-415">Pakiet IoT powiązania zawiera powiązania urządzenia.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-415">The IoT bindings package includes device bindings.</span></span> <span data-ttu-id="bbb6a-416">Aby uzyskać więcej informacji, zobacz [repozytorium GitHub urządzeń](https://github.com/dotnet/iot/blob/master/src/devices/).</span><span class="sxs-lookup"><span data-stu-id="bbb6a-416">For more information, see the [devices GitHub repo](https://github.com/dotnet/iot/blob/master/src/devices/).</span></span>

## <a name="arm64-linux-support"></a><span data-ttu-id="bbb6a-417">Obsługa systemu Linux ARM64</span><span class="sxs-lookup"><span data-stu-id="bbb6a-417">ARM64 Linux support</span></span>

<span data-ttu-id="bbb6a-418">.NET core 3.0 dodaje obsługę systemu Linux dla architektury ARM64.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-418">.NET Core 3.0 adds support for ARM64 for Linux.</span></span> <span data-ttu-id="bbb6a-419">Głównym zastosowaniem dla architektury ARM64 jest obecnie używany w scenariuszach IoT.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-419">The primary use case for ARM64 is currently with IoT scenarios.</span></span> <span data-ttu-id="bbb6a-420">Aby uzyskać więcej informacji, zobacz [stanu programu .NET Core ARM64](https://github.com/dotnet/announcements/issues/82).</span><span class="sxs-lookup"><span data-stu-id="bbb6a-420">For more information, see [.NET Core ARM64 Status](https://github.com/dotnet/announcements/issues/82).</span></span>

<span data-ttu-id="bbb6a-421">[Obrazy platformy docker dla platformy .NET Core dla procesorów ARM64](https://hub.docker.com/r/microsoft/dotnet/) są dostępne dla Alpine, Debian i Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-421">[Docker images for .NET Core on ARM64](https://hub.docker.com/r/microsoft/dotnet/) are available for Alpine, Debian, and Ubuntu.</span></span>

> [!NOTE]
> <span data-ttu-id="bbb6a-422">**ARM64** pomocy technicznej Windows nie jest jeszcze dostępna.</span><span class="sxs-lookup"><span data-stu-id="bbb6a-422">**ARM64** Windows support isn't yet available.</span></span>

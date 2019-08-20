---
title: Co nowego w programie .NET Core 3.0
description: Dowiedz się więcej o nowych funkcjach dostępnych w programie .NET Core 3,0.
dev_langs:
- csharp
- vb
author: thraka
ms.author: adegeo
ms.date: 07/25/2019
ms.openlocfilehash: 10e5dfdc873f8dcf9fec0da5f7f3561337033f40
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69604250"
---
# <a name="whats-new-in-net-core-30-preview-7"></a><span data-ttu-id="196df-103">Co nowego w programie .NET Core 3,0 (wersja zapoznawcza 7)</span><span class="sxs-lookup"><span data-stu-id="196df-103">What's new in .NET Core 3.0 (Preview 7)</span></span>

<span data-ttu-id="196df-104">W tym artykule opisano nowości w programie .NET Core 3,0 (w wersji zapoznawczej 7).</span><span class="sxs-lookup"><span data-stu-id="196df-104">This article describes what is new in .NET Core 3.0 (through preview 7).</span></span> <span data-ttu-id="196df-105">Jednym z największych ulepszeń jest obsługa aplikacji klasycznych systemu Windows (tylko system Windows).</span><span class="sxs-lookup"><span data-stu-id="196df-105">One of the biggest enhancements is support for Windows desktop applications (Windows only).</span></span> <span data-ttu-id="196df-106">Korzystając z pulpitu systemu Windows składnika zestawu SDK platformy .NET Core 3,0, można przenieść aplikacje Windows Forms i Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="196df-106">By using the .NET Core 3.0 SDK component Windows Desktop, you can port your Windows Forms and Windows Presentation Foundation (WPF) applications.</span></span> <span data-ttu-id="196df-107">Aby można było wyczyścić, składnik pulpitu systemu Windows jest obsługiwany i uwzględniany w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="196df-107">To be clear, the Windows Desktop component is only supported and included on Windows.</span></span> <span data-ttu-id="196df-108">Aby uzyskać więcej informacji, zobacz sekcję [pulpitu systemu Windows](#windows-desktop) w dalszej części tego artykułu.</span><span class="sxs-lookup"><span data-stu-id="196df-108">For more information, see the [Windows desktop](#windows-desktop) section later in this article.</span></span>

<span data-ttu-id="196df-109">Program .NET Core 3,0 dodaje obsługę C# 8,0.</span><span class="sxs-lookup"><span data-stu-id="196df-109">.NET Core 3.0 adds support for C# 8.0.</span></span> <span data-ttu-id="196df-110">Zdecydowanie zaleca się użycie [najnowszej wersji programu Visual Studio Preview](https://visualstudio.microsoft.com/vs/preview/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+preview)lub Visual Studio Code z rozszerzeniem OmniSharp.</span><span class="sxs-lookup"><span data-stu-id="196df-110">It's highly recommended that you use the [latest release of Visual Studio Preview](https://visualstudio.microsoft.com/vs/preview/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+preview), or Visual Studio Code with the OmniSharp extension.</span></span>

<span data-ttu-id="196df-111">[Pobierz i zacznij korzystać z platformy .NET Core 3,0 w wersji zapoznawczej 7](https://aka.ms/netcore3download) teraz w systemach Windows, Mac i Linux.</span><span class="sxs-lookup"><span data-stu-id="196df-111">[Download and get started with .NET Core 3.0 preview 7](https://aka.ms/netcore3download) right now on Windows, Mac, and Linux.</span></span>

<span data-ttu-id="196df-112">Aby uzyskać więcej informacji na temat każdej wersji zapoznawczej, zobacz następujące powiadomienia:</span><span class="sxs-lookup"><span data-stu-id="196df-112">For more information about each preview release, see the following announcements:</span></span>

- [<span data-ttu-id="196df-113">Anons programu .NET Core 3,0 w wersji zapoznawczej 7</span><span class="sxs-lookup"><span data-stu-id="196df-113">.NET Core 3.0 Preview 7 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-7/)
- [<span data-ttu-id="196df-114">Anons programu .NET Core 3,0 w wersji 6</span><span class="sxs-lookup"><span data-stu-id="196df-114">.NET Core 3.0 Preview 6 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-6/)
- [<span data-ttu-id="196df-115">Anons programu .NET Core 3,0 Preview 5</span><span class="sxs-lookup"><span data-stu-id="196df-115">.NET Core 3.0 Preview 5 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-5/)
- [<span data-ttu-id="196df-116">Anons programu .NET Core 3,0 Preview 4</span><span class="sxs-lookup"><span data-stu-id="196df-116">.NET Core 3.0 Preview 4 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-4/)
- [<span data-ttu-id="196df-117">Anons programu .NET Core 3,0 Preview 3</span><span class="sxs-lookup"><span data-stu-id="196df-117">.NET Core 3.0 Preview 3 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-3/)
- [<span data-ttu-id="196df-118">Anons programu .NET Core 3,0 w wersji zapoznawczej 2</span><span class="sxs-lookup"><span data-stu-id="196df-118">.NET Core 3.0 Preview 2 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-2/)
- [<span data-ttu-id="196df-119">Powiadomienie dotyczące programu .NET Core 3,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="196df-119">.NET Core 3.0 Preview 1 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-1-and-open-sourcing-windows-desktop-frameworks/)

## <a name="production-supported-preview"></a><span data-ttu-id="196df-120">Wersja zapoznawcza obsługiwanej produkcji</span><span class="sxs-lookup"><span data-stu-id="196df-120">Production supported preview</span></span>

<span data-ttu-id="196df-121">Program .NET Core Preview 7 jest uznawany za gotowy do produkcji przez firmę Microsoft i jest w pełni obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="196df-121">.NET Core Preview 7 is considered production ready by Microsoft and is fully supported.</span></span> <span data-ttu-id="196df-122">Począwszy od wersji zapoznawczej 7, wersje będą skoncentrowane na polerowaniu platformy .NET Core 3,0 zamiast dodawania nowych funkcji.</span><span class="sxs-lookup"><span data-stu-id="196df-122">Starting with preview 7, releases will focus on polishing .NET Core 3.0 instead of adding new features.</span></span> <span data-ttu-id="196df-123">Aby uzyskać więcej informacji na temat zmian w wersji zapoznawczej 7, zapoznaj się z ogłoszeniem w [wersji zapoznawczej 7](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-7/).</span><span class="sxs-lookup"><span data-stu-id="196df-123">For more information about what has changed in preview 7, see the [preview 7 announcement](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-7/).</span></span>

## <a name="net-core-sdk-windows-installer"></a><span data-ttu-id="196df-124">Zestaw .NET Core SDK Instalator Windows</span><span class="sxs-lookup"><span data-stu-id="196df-124">.NET Core SDK Windows Installer</span></span>

<span data-ttu-id="196df-125">Instalator MSI dla systemu Windows został zmieniony począwszy od platformy .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="196df-125">The MSI installer for Windows has changed starting with .NET Core 3.0.</span></span> <span data-ttu-id="196df-126">Instalatorzy zestawu SDK teraz uaktualniają wersje funkcji zestawu SDK na miejscu.</span><span class="sxs-lookup"><span data-stu-id="196df-126">The SDK installers will now upgrade SDK feature-band releases in place.</span></span> <span data-ttu-id="196df-127">Paski funkcji są zdefiniowane w grupach *setek* w sekcji *poprawka* numeru wersji.</span><span class="sxs-lookup"><span data-stu-id="196df-127">Feature bands are defined in the *hundreds* groups in the *patch* section of the version number.</span></span> <span data-ttu-id="196df-128">Na przykład **3,0. _101_**  i **3,0. _201_**  są wersje w dwóch różnych warstwach funkcji podczas **3,0. _101_**  i **3,0. _199_**  znajdują się w tej samej paśmie funkcji.</span><span class="sxs-lookup"><span data-stu-id="196df-128">For example, **3.0._101_** and **3.0._201_** are versions in two different feature bands while **3.0._101_** and **3.0._199_** are in the same feature band.</span></span> <span data-ttu-id="196df-129">I, w przypadku zestaw .NET Core SDK **3,0. _101_**  jest zainstalowana, zestaw .NET Core SDK **3,0. _100_**  zostanie usunięta z komputera, jeśli istnieje.</span><span class="sxs-lookup"><span data-stu-id="196df-129">And, when .NET Core SDK **3.0._101_** is installed, .NET Core SDK **3.0._100_** will be removed from the machine if it exists.</span></span> <span data-ttu-id="196df-130">Gdy zestaw .NET Core SDK **3,0. _200_**  jest zainstalowana na tym samym komputerze, zestaw .NET Core SDK **3,0. _101_**  nie zostanie usunięta.</span><span class="sxs-lookup"><span data-stu-id="196df-130">When .NET Core SDK **3.0._200_** is installed on the same machine, .NET Core SDK **3.0._101_** won't be removed.</span></span>

<span data-ttu-id="196df-131">Aby uzyskać więcej informacji na temat przechowywania wersji, zobacz [Omówienie wersji platformy .NET Core](../versions/index.md).</span><span class="sxs-lookup"><span data-stu-id="196df-131">For more information about versioning, see [Overview of how .NET Core is versioned](../versions/index.md).</span></span>

## <a name="c-80-preview"></a><span data-ttu-id="196df-132">C#wersja zapoznawcza 8,0</span><span class="sxs-lookup"><span data-stu-id="196df-132">C# 8.0 preview</span></span>

<span data-ttu-id="196df-133">Program .NET Core 3,0 C# obsługuje 8 wersji zapoznawczych.</span><span class="sxs-lookup"><span data-stu-id="196df-133">.NET Core 3.0 supports C# 8 preview.</span></span> <span data-ttu-id="196df-134">Aby uzyskać więcej informacji C# o funkcjach 8,0, zobacz [co nowego C# w programie 8,0](../../csharp/whats-new/csharp-8.md).</span><span class="sxs-lookup"><span data-stu-id="196df-134">For more information about C# 8.0 features, see [What's new in C# 8.0](../../csharp/whats-new/csharp-8.md).</span></span>

## <a name="net-standard-21"></a><span data-ttu-id="196df-135">.NET Standard 2,1</span><span class="sxs-lookup"><span data-stu-id="196df-135">.NET Standard 2.1</span></span>

<span data-ttu-id="196df-136">Mimo że program .NET Core 3,0 obsługuje **.NET Standard 2,1**, szablon `dotnet new classlib` domyślny generuje projekt, który jest przeznaczony dla **.NET Standard 2,0**.</span><span class="sxs-lookup"><span data-stu-id="196df-136">Even though .NET Core 3.0 supports **.NET Standard 2.1**, the default `dotnet new classlib` template generates a project that targets **.NET Standard 2.0**.</span></span> <span data-ttu-id="196df-137">Aby docelowa **.NET Standard 2,1**, edytuj plik projektu i Zmień `TargetFramework` właściwość na `netstandard2.1`:</span><span class="sxs-lookup"><span data-stu-id="196df-137">To target **.NET Standard 2.1**, edit your project file and change the `TargetFramework` property to `netstandard2.1`:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
 
  <PropertyGroup>
    <TargetFramework>netstandard2.1</TargetFramework>
  </PropertyGroup>
 
</Project>
```

<span data-ttu-id="196df-138">Jeśli używasz programu Visual Studio, potrzebujesz [programu Visual studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), ponieważ program visual Studio 2017 nie obsługuje **.NET Standard 2,1** ani **.NET Core 3,0**.</span><span class="sxs-lookup"><span data-stu-id="196df-138">If you're using Visual Studio, you need [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), as Visual Studio 2017 doesn't support **.NET Standard 2.1** or **.NET Core 3.0**.</span></span>

## <a name="improved-net-core-version-apis"></a><span data-ttu-id="196df-139">Ulepszone interfejsy API wersji platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="196df-139">Improved .NET Core Version APIs</span></span>

<span data-ttu-id="196df-140">Począwszy od platformy .NET Core 3,0, interfejsy API wersji dostarczone z platformą .NET Core teraz zwracają oczekiwane informacje.</span><span class="sxs-lookup"><span data-stu-id="196df-140">Starting with .NET Core 3.0, the version APIs provided with .NET Core now return the information you expect.</span></span> <span data-ttu-id="196df-141">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="196df-141">For example:</span></span>

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
> <span data-ttu-id="196df-142">Istotna zmiana.</span><span class="sxs-lookup"><span data-stu-id="196df-142">Breaking change.</span></span> <span data-ttu-id="196df-143">Jest to technicznie istotna zmiana, ponieważ schemat przechowywania wersji został zmieniony.</span><span class="sxs-lookup"><span data-stu-id="196df-143">This is technically a breaking change because the versioning scheme has changed.</span></span>

## <a name="net-platform-dependent-intrinsics"></a><span data-ttu-id="196df-144">Elementy wewnętrzne zależne od platformy .NET</span><span class="sxs-lookup"><span data-stu-id="196df-144">.NET Platform-Dependent Intrinsics</span></span>

<span data-ttu-id="196df-145">Dodano interfejsy API, które umożliwiają dostęp do pewnych instrukcji procesora CPU zorientowanych na wydajność, takich jak **SIMD** lub **bitowe zestawy instrukcji manipulowania** .</span><span class="sxs-lookup"><span data-stu-id="196df-145">APIs have been added that allow access to certain perf-oriented CPU instructions, such as the **SIMD** or **Bit Manipulation instruction** sets.</span></span> <span data-ttu-id="196df-146">Te instrukcje mogą pomóc w osiągnięciu znaczących ulepszeń wydajności w niektórych scenariuszach, takich jak wydajne przetwarzanie danych.</span><span class="sxs-lookup"><span data-stu-id="196df-146">These instructions can help achieve significant performance improvements in certain scenarios, such as processing data efficiently in parallel.</span></span> 

<span data-ttu-id="196df-147">W odpowiednich przypadkach biblioteki .NET zaczęły korzystać z tych instrukcji w celu zwiększenia wydajności.</span><span class="sxs-lookup"><span data-stu-id="196df-147">Where appropriate, the .NET libraries have begun using these instructions to improve performance.</span></span>

<span data-ttu-id="196df-148">Aby uzyskać więcej informacji, zobacz elementy [wewnętrzne zależne od platformy .NET](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md).</span><span class="sxs-lookup"><span data-stu-id="196df-148">For more information, see [.NET Platform Dependent Intrinsics](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md).</span></span>

## <a name="default-executables"></a><span data-ttu-id="196df-149">Domyślne pliki wykonywalne</span><span class="sxs-lookup"><span data-stu-id="196df-149">Default executables</span></span>

<span data-ttu-id="196df-150">Platforma .NET Core teraz domyślnie kompiluje [pliki wykonywalne zależne od platformy](../deploying/index.md#framework-dependent-executables-fde) .</span><span class="sxs-lookup"><span data-stu-id="196df-150">.NET Core now builds [framework-dependent executables](../deploying/index.md#framework-dependent-executables-fde) by default.</span></span> <span data-ttu-id="196df-151">To zachowanie jest nowe w przypadku aplikacji korzystających z zainstalowanej globalnie wersji platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="196df-151">This behavior is new for applications that use a globally installed version of .NET Core.</span></span> <span data-ttu-id="196df-152">Wcześniej tylko [wstępnie zawarte wdrożenia](../deploying/index.md#self-contained-deployments-scd) spowodują utworzenie pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="196df-152">Previously, only [self-contained deployments](../deploying/index.md#self-contained-deployments-scd) would produce an executable.</span></span>

<span data-ttu-id="196df-153">W `dotnet build` trakcie `dotnet publish`lub, tworzony jest plik wykonywalny zgodny ze środowiskiem i platformą używanego zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="196df-153">During `dotnet build` or `dotnet publish`, an executable is created that matches the environment and platform of the SDK you're using.</span></span> <span data-ttu-id="196df-154">Można oczekiwać, że te same elementy wykonywalne są takie same jak w przypadku innych natywnych plików wykonywalnych, takich jak:</span><span class="sxs-lookup"><span data-stu-id="196df-154">You can expect the same things with these executables as you would other native executables, such as:</span></span>

* <span data-ttu-id="196df-155">Możesz kliknąć dwukrotnie plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="196df-155">You can double-click on the executable.</span></span>
* <span data-ttu-id="196df-156">Aplikację można uruchomić z poziomu wiersza polecenia bezpośrednio, na przykład `myapp.exe` w systemie Windows `./myapp` , w systemie Linux i macOS.</span><span class="sxs-lookup"><span data-stu-id="196df-156">You can launch the application from a command prompt directly, such as `myapp.exe` on Windows, and `./myapp` on Linux and macOS.</span></span>

## <a name="single-file-executables"></a><span data-ttu-id="196df-157">Pliki wykonywalne pojedynczego pliku</span><span class="sxs-lookup"><span data-stu-id="196df-157">Single-file executables</span></span>

<span data-ttu-id="196df-158">`dotnet publish` Polecenie obsługuje pakowanie aplikacji do pliku wykonywalnego określonego dla konkretnej platformy.</span><span class="sxs-lookup"><span data-stu-id="196df-158">The `dotnet publish` command supports packaging your app into a platform-specific single-file executable.</span></span> <span data-ttu-id="196df-159">Plik wykonywalny jest samowyodrębniający się i zawiera wszystkie zależności (w tym natywne) wymagane do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="196df-159">The executable is self-extracting and contains all dependencies (including native) that are required to run your app.</span></span> <span data-ttu-id="196df-160">Gdy aplikacja jest uruchamiana po raz pierwszy, aplikacja zostanie wyodrębniona do katalogu na podstawie nazwy aplikacji i identyfikatora kompilacji.</span><span class="sxs-lookup"><span data-stu-id="196df-160">When the app is first run, the application is extracted to a directory based on the app name and build identifier.</span></span> <span data-ttu-id="196df-161">Uruchamianie jest szybsze, gdy aplikacja jest uruchamiana ponownie.</span><span class="sxs-lookup"><span data-stu-id="196df-161">Startup is faster when the application is run again.</span></span> <span data-ttu-id="196df-162">Aplikacja nie musi wyodrębniać siebie po raz drugi, chyba że została użyta Nowa wersja.</span><span class="sxs-lookup"><span data-stu-id="196df-162">The application doesn't need to extract itself a second time unless a new version was used.</span></span>

<span data-ttu-id="196df-163">Aby opublikować plik wykonywalny pojedynczego pliku, ustaw `PublishSingleFile` w projekcie lub w wierszu `dotnet publish` polecenia polecenie:</span><span class="sxs-lookup"><span data-stu-id="196df-163">To publish a single-file executable, set the `PublishSingleFile` in your project or on the command line with the `dotnet publish` command:</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifier>win10-x64</RuntimeIdentifier>
  <PublishSingleFile>true</PublishSingleFile>
</PropertyGroup>
```

<span data-ttu-id="196df-164">—lub—</span><span class="sxs-lookup"><span data-stu-id="196df-164">-or-</span></span>

```console
dotnet publish -r win10-x64 /p:PublishSingleFile=true
```

<span data-ttu-id="196df-165">Aby uzyskać więcej informacji o publikowaniu jednoplikowym, zapoznaj się z [dokumentem projektu pakietu pojedynczego pliku](https://github.com/dotnet/designs/blob/master/accepted/single-file/design.md).</span><span class="sxs-lookup"><span data-stu-id="196df-165">For more information about single-file publishing, see the [single-file bundler design document](https://github.com/dotnet/designs/blob/master/accepted/single-file/design.md).</span></span>

## <a name="assembly-linking"></a><span data-ttu-id="196df-166">Łączenie zestawów</span><span class="sxs-lookup"><span data-stu-id="196df-166">Assembly linking</span></span>

<span data-ttu-id="196df-167">Zestaw SDK platformy .NET Core 3,0 zawiera narzędzie, które pozwala zmniejszyć rozmiar aplikacji przez analizowanie IL i przycinanie nieużywanych zestawów.</span><span class="sxs-lookup"><span data-stu-id="196df-167">The .NET core 3.0 SDK comes with a tool that can reduce the size of apps by analyzing IL and trimming unused assemblies.</span></span>

<span data-ttu-id="196df-168">Aplikacje samodzielne obejmują wszystko, co jest potrzebne do uruchomienia kodu, bez konieczności instalowania programu .NET na komputerze-hoście.</span><span class="sxs-lookup"><span data-stu-id="196df-168">Self-contained apps include everything needed to run your code, without requiring .NET to be installed on the host computer.</span></span> <span data-ttu-id="196df-169">Jednak wiele razy aplikacja wymaga tylko małego podzestawu platformy do działania, a inne nieużywane biblioteki mogą zostać usunięte.</span><span class="sxs-lookup"><span data-stu-id="196df-169">However, many times the app only requires a small subset of the framework to function, and other unused libraries could be removed.</span></span>

<span data-ttu-id="196df-170">Platforma .NET Core zawiera teraz ustawienie, które będzie używać narzędzia [konsolidatora Il](https://github.com/mono/linker) do skanowania Il aplikacji.</span><span class="sxs-lookup"><span data-stu-id="196df-170">.NET Core now includes a setting that will use the [IL linker](https://github.com/mono/linker) tool to scan the IL of your app.</span></span> <span data-ttu-id="196df-171">to narzędzie wykrywa wymagany kod, a następnie przycina nieużywane biblioteki.</span><span class="sxs-lookup"><span data-stu-id="196df-171">this tool detects what code is required, and then trims unused libraries.</span></span> <span data-ttu-id="196df-172">To narzędzie może znacznie zmniejszyć rozmiar wdrożenia niektórych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="196df-172">This tool can significantly reduce the deployment size of some apps.</span></span>

<span data-ttu-id="196df-173">Aby włączyć to narzędzie, Dodaj `<PublishTrimmed>` ustawienie w projekcie i Opublikuj samodzielną aplikację:</span><span class="sxs-lookup"><span data-stu-id="196df-173">To enable this tool, add the `<PublishTrimmed>` setting in your project and publish a self-contained app:</span></span>

```xml
<PropertyGroup>
  <PublishTrimmed>true</PublishTrimmed>
</PropertyGroup>
```

```console
dotnet publish -r <rid> -c Release
```

<span data-ttu-id="196df-174">Na przykład podstawowy "Hello World" nowy szablon projektu konsoli, który jest dostępny po opublikowaniu, trafień o rozmiarze 70 MB.</span><span class="sxs-lookup"><span data-stu-id="196df-174">As an example, the basic "hello world" new console project template that is included, when published, hits about 70 MB in size.</span></span> <span data-ttu-id="196df-175">Przy użyciu `<PublishTrimmed>`, ten rozmiar jest zmniejszany do około 30 MB.</span><span class="sxs-lookup"><span data-stu-id="196df-175">By using `<PublishTrimmed>`, that size is reduced to about 30 MB.</span></span>

<span data-ttu-id="196df-176">Należy wziąć pod uwagę, że aplikacje lub struktury (w tym ASP.NET Core i WPF), które wykorzystują odbicie lub powiązane funkcje dynamiczne, często będą przerywane po przycięciu.</span><span class="sxs-lookup"><span data-stu-id="196df-176">It's important to consider that applications or frameworks (including ASP.NET Core and WPF) that use reflection or related dynamic features, will often break when trimmed.</span></span> <span data-ttu-id="196df-177">To uszkodzenie występuje, ponieważ konsolidator nie wie o tym zachowaniu dynamicznym i nie może określić, które typy struktur są wymagane do odbicia.</span><span class="sxs-lookup"><span data-stu-id="196df-177">This breakage occurs because the linker doesn't know about this dynamic behavior and can't determine which framework types are required for reflection.</span></span> <span data-ttu-id="196df-178">Narzędzie konsolidatora IL można skonfigurować pod kątem tego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="196df-178">The IL Linker tool can be configured to be aware of this scenario.</span></span>

<span data-ttu-id="196df-179">Przed przycinaniem upewnij się, że aplikacja została przetestowana.</span><span class="sxs-lookup"><span data-stu-id="196df-179">Above all else, be sure to test your app after trimming.</span></span>

<span data-ttu-id="196df-180">Aby uzyskać więcej informacji na temat narzędzia konsolidatora IL, zapoznaj się z [dokumentacją](https://aka.ms/dotnet-illink) lub odwiedź repozytorium [mono/konsolidatora]( https://github.com/mono/linker) .</span><span class="sxs-lookup"><span data-stu-id="196df-180">For more information about the IL Linker tool, see the [documentation](https://aka.ms/dotnet-illink) or visit the [mono/linker]( https://github.com/mono/linker) repo.</span></span>

## <a name="tiered-compilation"></a><span data-ttu-id="196df-181">Kompilacja warstwowa</span><span class="sxs-lookup"><span data-stu-id="196df-181">Tiered compilation</span></span>

<span data-ttu-id="196df-182">[Kompilacja warstwowa](https://devblogs.microsoft.com/dotnet/tiered-compilation-preview-in-net-core-2-1/) (TC) jest domyślnie włączona z platformą .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="196df-182">[Tiered compilation](https://devblogs.microsoft.com/dotnet/tiered-compilation-preview-in-net-core-2-1/) (TC) is on by default with .NET Core 3.0.</span></span> <span data-ttu-id="196df-183">Ta funkcja umożliwia środowisku uruchomieniowemu wydajniejsze używanie kompilatora just-in-Time (JIT) w celu uzyskania lepszej wydajności.</span><span class="sxs-lookup"><span data-stu-id="196df-183">This feature enables the runtime to more adaptively use the Just-In-Time (JIT) compiler to get better performance.</span></span>

<span data-ttu-id="196df-184">Główną zaletą TC jest włączenie (re-) metod jitting z niską jakością, ale szybszym lub wyższą warstwą.</span><span class="sxs-lookup"><span data-stu-id="196df-184">The main benefit of TC is to enable (re-)jitting methods with a lower-quality-but-faster tier or a higher-quality-but-slower tier.</span></span> <span data-ttu-id="196df-185">Pozwala to zwiększyć wydajność aplikacji, która przechodzi przez różne etapy wykonywania, od uruchamiania do stanu stałego.</span><span class="sxs-lookup"><span data-stu-id="196df-185">This helps increase performance of an application as it goes through various stages of execution, from startup through steady-state.</span></span> <span data-ttu-id="196df-186">Jest to kontrast z podejściem innym niż TC, gdzie każda metoda jest skompilowana w jeden sposób (taka sama jak warstwa wysokiej jakości), która jest obciążona niestabilnym stanem w porównaniu z wydajnością uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="196df-186">This contrasts with the non-TC approach, where every method is compiled a single way (the same as the high-quality tier), which is biased to steady-state over startup performance.</span></span>

<span data-ttu-id="196df-187">Aby włączyć funkcję szybkiego JIT (kod 0 trybie JIT), użyj tego ustawienia w pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="196df-187">To enable Quick JIT (tier 0 jitted code), use this setting in your project file:</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>true</TieredCompilationQuickJit>
</PropertyGroup>
```

<span data-ttu-id="196df-188">Aby całkowicie wyłączyć TC, użyj tego ustawienia w pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="196df-188">To disable TC completely, use this setting in your project file:</span></span>

```xml
<TieredCompilation>false</TieredCompilation>
```

## <a name="readytorun-images"></a><span data-ttu-id="196df-189">Obrazy ReadyToRun</span><span class="sxs-lookup"><span data-stu-id="196df-189">ReadyToRun images</span></span>

<span data-ttu-id="196df-190">Można skrócić czas uruchamiania aplikacji .NET Core, kompilując zestawy aplikacji jako ReadyToRun (R2R).</span><span class="sxs-lookup"><span data-stu-id="196df-190">You can improve the startup time of your .NET Core application by compiling your application assemblies as ReadyToRun (R2R) format.</span></span> <span data-ttu-id="196df-191">R2R to forma kompilacji z wyprzedzeniem (AOT).</span><span class="sxs-lookup"><span data-stu-id="196df-191">R2R is a form of ahead-of-time (AOT) compilation.</span></span>

<span data-ttu-id="196df-192">Pliki binarne R2R zwiększają wydajność uruchamiania przez zmniejszenie ilości pracy kompilatora, który jest potrzebny do załadowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="196df-192">R2R binaries improve startup performance by reducing the amount of work the just-in-time (JIT) compiler needs to do as your application loads.</span></span> <span data-ttu-id="196df-193">Pliki binarne zawierają podobny kod natywny w porównaniu z przeznaczeniem JIT.</span><span class="sxs-lookup"><span data-stu-id="196df-193">The binaries contain similar native code compared to what the JIT would produce.</span></span> <span data-ttu-id="196df-194">R2R pliki binarne są jednak większe, ponieważ zawierają kod języka pośredniego (IL), który jest nadal wymagany w niektórych scenariuszach i natywną wersję tego samego kodu.</span><span class="sxs-lookup"><span data-stu-id="196df-194">However, R2R binaries are larger because they contain both intermediate language (IL) code, which is still needed for some scenarios, and the native version of the same code.</span></span> <span data-ttu-id="196df-195">R2R jest dostępna tylko w przypadku publikowania aplikacji samodzielnej, która jest przeznaczona dla określonych środowisk uruchomieniowych (RID), takich jak Linux x64 lub Windows x64.</span><span class="sxs-lookup"><span data-stu-id="196df-195">R2R is only available when you publish a self-contained app that targets specific runtime environments (RID) such as Linux x64 or Windows x64.</span></span>

<span data-ttu-id="196df-196">Aby skompilować projekt jako ReadyToRun, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="196df-196">To compile your project as ReadyToRun, do the following:</span></span>

01. <span data-ttu-id="196df-197">`<PublishReadyToRun>` Dodaj ustawienie do projektu</span><span class="sxs-lookup"><span data-stu-id="196df-197">Add the `<PublishReadyToRun>` setting to your project</span></span>

    ```xml
    <PropertyGroup>
      <PublishReadyToRun>true</PublishReadyToRun>
    </PropertyGroup>
    ```

01. <span data-ttu-id="196df-198">Publikowanie aplikacji samodzielnej.</span><span class="sxs-lookup"><span data-stu-id="196df-198">Publish a self-contained app.</span></span> <span data-ttu-id="196df-199">Na przykład to polecenie tworzy samodzielną aplikację dla 64-bitowej wersji systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="196df-199">For example, this command creates a self-contained app for the 64-bit version of Windows:</span></span>

    ```console
    dotnet publish -c Release -r win-x64 --self-contained true
    ```

### <a name="cross-platformarchitecture-restrictions"></a><span data-ttu-id="196df-200">Ograniczenia dotyczące wielu platform/architektury</span><span class="sxs-lookup"><span data-stu-id="196df-200">Cross platform/architecture restrictions</span></span>

<span data-ttu-id="196df-201">Kompilator ReadyToRun nie obsługuje obecnie określania wartości docelowej.</span><span class="sxs-lookup"><span data-stu-id="196df-201">The ReadyToRun compiler doesn't currently support cross-targeting.</span></span> <span data-ttu-id="196df-202">Należy skompilować na danym miejscu docelowym.</span><span class="sxs-lookup"><span data-stu-id="196df-202">You must compile on a given target.</span></span> <span data-ttu-id="196df-203">Na przykład jeśli chcesz, aby obrazy R2R dla systemu Windows x64 zostały wykonane, należy uruchomić polecenie Publikuj w tym środowisku.</span><span class="sxs-lookup"><span data-stu-id="196df-203">For example, if you want R2R images for Windows x64, you need to run the publish command on that environment.</span></span>

<span data-ttu-id="196df-204">Wyjątki dla wielu elementów docelowych:</span><span class="sxs-lookup"><span data-stu-id="196df-204">Exceptions to cross-targeting:</span></span>

- <span data-ttu-id="196df-205">System Windows x64 może służyć do kompilowania obrazów systemów Windows ARM32, ARM64 i x86.</span><span class="sxs-lookup"><span data-stu-id="196df-205">Windows x64 can be used to compile Windows ARM32, ARM64, and x86 images.</span></span>
- <span data-ttu-id="196df-206">System Windows x86 może służyć do kompilowania obrazów ARM32 systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="196df-206">Windows x86 can be used to compile Windows ARM32 images.</span></span>
- <span data-ttu-id="196df-207">System Linux x64 może służyć do kompilowania obrazów systemu Linux ARM32 i ARM64.</span><span class="sxs-lookup"><span data-stu-id="196df-207">Linux x64 can be used to compile Linux ARM32 and ARM64 images.</span></span>

## <a name="build-copies-dependencies"></a><span data-ttu-id="196df-208">Zależności kompilacji kopii</span><span class="sxs-lookup"><span data-stu-id="196df-208">Build copies dependencies</span></span>

<span data-ttu-id="196df-209">`dotnet build` Polecenie teraz kopiuje zależności NuGet dla aplikacji z pamięci podręcznej NuGet do folderu danych wyjściowych kompilacji.</span><span class="sxs-lookup"><span data-stu-id="196df-209">The `dotnet build` command now copies NuGet dependencies for your application from the NuGet cache to the build output folder.</span></span> <span data-ttu-id="196df-210">Wcześniej zależności były kopiowane tylko w ramach programu `dotnet publish`.</span><span class="sxs-lookup"><span data-stu-id="196df-210">Previously, dependencies were only copied as part of `dotnet publish`.</span></span>

<span data-ttu-id="196df-211">Istnieją pewne operacje, takie jak łączenie i publikowanie stron Razor, które nadal wymagają publikacji.</span><span class="sxs-lookup"><span data-stu-id="196df-211">There are some operations, like linking and razor page publishing that will still require publishing.</span></span>

## <a name="local-tools"></a><span data-ttu-id="196df-212">Narzędzia lokalne</span><span class="sxs-lookup"><span data-stu-id="196df-212">Local tools</span></span>

<span data-ttu-id="196df-213">Środowisko .NET Core 3,0 zawiera wprowadzenie do narzędzi lokalnych.</span><span class="sxs-lookup"><span data-stu-id="196df-213">.NET Core 3.0 introduces local tools.</span></span> <span data-ttu-id="196df-214">Narzędzia lokalne są podobne do [narzędzi globalnych](../tools/global-tools.md) , ale są skojarzone z konkretną lokalizacją na dysku.</span><span class="sxs-lookup"><span data-stu-id="196df-214">Local tools are similar to [global tools](../tools/global-tools.md) but are associated with a particular location on disk.</span></span> <span data-ttu-id="196df-215">Narzędzia lokalne nie są dostępne globalnie i są dystrybuowane jako pakiety NuGet.</span><span class="sxs-lookup"><span data-stu-id="196df-215">Local tools aren't available globally and are distributed as NuGet packages.</span></span>

> [!WARNING]
> <span data-ttu-id="196df-216">Jeśli podjęto próbę skorzystania z narzędzi lokalnych w programie .NET Core 3,0 `dotnet tool restore` w `dotnet tool install`wersji zapoznawczej 1, takiej jak uruchamianie lub, Usuń folder pamięci podręcznej narzędzi lokalnych</span><span class="sxs-lookup"><span data-stu-id="196df-216">If you tried local tools in .NET Core 3.0 Preview 1, such as running `dotnet tool restore` or `dotnet tool install`, delete the local tools cache folder.</span></span> <span data-ttu-id="196df-217">W przeciwnym razie narzędzia lokalne nie będą działały w żadnej nowszej wersji.</span><span class="sxs-lookup"><span data-stu-id="196df-217">Otherwise, local tools won't work on any newer release.</span></span> <span data-ttu-id="196df-218">Ten folder znajduje się w lokalizacji:</span><span class="sxs-lookup"><span data-stu-id="196df-218">This folder is located at:</span></span>
>
> <span data-ttu-id="196df-219">W systemie macOS, Linux:`rm -r $HOME/.dotnet/toolResolverCache`</span><span class="sxs-lookup"><span data-stu-id="196df-219">On macOS, Linux: `rm -r $HOME/.dotnet/toolResolverCache`</span></span>
>
> <span data-ttu-id="196df-220">W systemie Windows:`rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`</span><span class="sxs-lookup"><span data-stu-id="196df-220">On Windows: `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`</span></span>

<span data-ttu-id="196df-221">Narzędzia lokalne są zależne od nazwy `dotnet-tools.json` pliku manifestu w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="196df-221">Local tools rely on a manifest file name `dotnet-tools.json` in your current directory.</span></span> <span data-ttu-id="196df-222">Ten plik manifestu definiuje narzędzia do udostępnienia w tym folderze i poniżej.</span><span class="sxs-lookup"><span data-stu-id="196df-222">This manifest file defines the tools to be available at that folder and below.</span></span> <span data-ttu-id="196df-223">Plik manifestu można dystrybuować z kodem, aby upewnić się, że każda osoba, która współpracuje z kodem, będzie mogła przywrócić i korzystać z tych samych narzędzi.</span><span class="sxs-lookup"><span data-stu-id="196df-223">You can distribute the manifest file with your code to ensure that anyone who works with your code can restore and use the same tools.</span></span>

<span data-ttu-id="196df-224">W przypadku narzędzi globalnych i lokalnych wymagana jest zgodna wersja środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="196df-224">For both global and local tools, a compatible version of the runtime is required.</span></span> <span data-ttu-id="196df-225">Wiele narzędzi obecnie na NuGet.org docelowym środowiska uruchomieniowego .NET Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="196df-225">Many tools currently on NuGet.org target .NET Core Runtime 2.1.</span></span> <span data-ttu-id="196df-226">Aby zainstalować te narzędzia globalnie lub lokalnie, nadal trzeba zainstalować [środowisko uruchomieniowe NET Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="196df-226">To install these tools globally or locally, you would still need to install the [NET Core 2.1 Runtime](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span>

## <a name="major-version-roll-forward"></a><span data-ttu-id="196df-227">Wersja główna — przekazanie do przodu</span><span class="sxs-lookup"><span data-stu-id="196df-227">Major-version Roll Forward</span></span>

<span data-ttu-id="196df-228">W programie .NET Core 3,0 wprowadzono funkcję wyboru, która pozwala aplikacji na przewinięcie do najnowszej wersji programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="196df-228">.NET Core 3.0 introduces an opt-in feature that allows your app to roll forward to the latest major version of .NET Core.</span></span> <span data-ttu-id="196df-229">Ponadto zostało dodane nowe ustawienie służące do kontrolowania sposobu, w jaki przenoszone do przodu jest stosowane do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="196df-229">Additionally, a new setting has been added to control how roll forward is applied to your app.</span></span> <span data-ttu-id="196df-230">Tę konfigurację można skonfigurować w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="196df-230">This can be configured in the following ways:</span></span>

- <span data-ttu-id="196df-231">Właściwość pliku projektu:`RollForward`</span><span class="sxs-lookup"><span data-stu-id="196df-231">Project file property: `RollForward`</span></span>
- <span data-ttu-id="196df-232">Właściwość pliku konfiguracji środowiska uruchomieniowego:`rollForward`</span><span class="sxs-lookup"><span data-stu-id="196df-232">Runtime configuration file property: `rollForward`</span></span>
- <span data-ttu-id="196df-233">Zmienna środowiskowa:`DOTNET_ROLL_FORWARD`</span><span class="sxs-lookup"><span data-stu-id="196df-233">Environment variable: `DOTNET_ROLL_FORWARD`</span></span>
- <span data-ttu-id="196df-234">Argument wiersza polecenia:`--roll-forward`</span><span class="sxs-lookup"><span data-stu-id="196df-234">Command-line argument: `--roll-forward`</span></span>

<span data-ttu-id="196df-235">Należy określić jedną z następujących wartości.</span><span class="sxs-lookup"><span data-stu-id="196df-235">One of the following values must be specified.</span></span> <span data-ttu-id="196df-236">Jeśli ustawienie zostanie pominięte, wartością domyślną jest wartość pomocnicza.</span><span class="sxs-lookup"><span data-stu-id="196df-236">If the setting is omitted, **Minor** is the default.</span></span>

- <span data-ttu-id="196df-237">**LatestPatch**</span><span class="sxs-lookup"><span data-stu-id="196df-237">**LatestPatch**</span></span>\
<span data-ttu-id="196df-238">Przewinięcie do najwyższej wersji poprawki.</span><span class="sxs-lookup"><span data-stu-id="196df-238">Roll forward to the highest patch version.</span></span> <span data-ttu-id="196df-239">Spowoduje to wyłączenie wycofywania wersji pomocniczej.</span><span class="sxs-lookup"><span data-stu-id="196df-239">This disables minor version roll forward.</span></span>
- <span data-ttu-id="196df-240">**Średni**</span><span class="sxs-lookup"><span data-stu-id="196df-240">**Minor**</span></span>\
<span data-ttu-id="196df-241">Przewinięcie do najmniejszej wyższej wersji pomocniczej, jeśli brakuje wymaganej wersji pomocniczej.</span><span class="sxs-lookup"><span data-stu-id="196df-241">Roll forward to the lowest higher minor version, if requested minor version is missing.</span></span> <span data-ttu-id="196df-242">Jeśli jest obecna żądana wersja pomocnicza, zostaną użyte zasady **LatestPatch** .</span><span class="sxs-lookup"><span data-stu-id="196df-242">If the requested minor version is present, then the **LatestPatch** policy is used.</span></span>
- <span data-ttu-id="196df-243">**Znaczny**</span><span class="sxs-lookup"><span data-stu-id="196df-243">**Major**</span></span>\
<span data-ttu-id="196df-244">Zaczekaj na najmniejszą wyższą wersję główną i najniższą wersję pomocniczą, jeśli brakuje żądanej wersji głównej.</span><span class="sxs-lookup"><span data-stu-id="196df-244">Roll forward to lowest higher major version, and lowest minor version, if requested major version is missing.</span></span> <span data-ttu-id="196df-245">Jeśli jest obecna żądana wersja główna, są używane zasady pomocnicze.</span><span class="sxs-lookup"><span data-stu-id="196df-245">If the requested major version is present, then the **Minor** policy is used.</span></span>
- <span data-ttu-id="196df-246">**LatestMinor**</span><span class="sxs-lookup"><span data-stu-id="196df-246">**LatestMinor**</span></span>\
<span data-ttu-id="196df-247">Przewinięcie do przodu do najwyższej wersji pomocniczej, nawet jeśli jest obecna żądana wersja pomocnicza.</span><span class="sxs-lookup"><span data-stu-id="196df-247">Roll forward to highest minor version, even if requested minor version is present.</span></span> <span data-ttu-id="196df-248">Przeznaczone do scenariuszy hostingu składników.</span><span class="sxs-lookup"><span data-stu-id="196df-248">Intended for component hosting scenarios.</span></span>
- <span data-ttu-id="196df-249">**LatestMajor**</span><span class="sxs-lookup"><span data-stu-id="196df-249">**LatestMajor**</span></span>\
<span data-ttu-id="196df-250">Przewinięcie do przodu do najwyższej głównej i najwyższej wersji pomocniczej, nawet jeśli jest obecny żądany główny.</span><span class="sxs-lookup"><span data-stu-id="196df-250">Roll forward to highest major and highest minor version, even if requested major is present.</span></span> <span data-ttu-id="196df-251">Przeznaczone do scenariuszy hostingu składników.</span><span class="sxs-lookup"><span data-stu-id="196df-251">Intended for component hosting scenarios.</span></span>
- <span data-ttu-id="196df-252">**Wyłącza**</span><span class="sxs-lookup"><span data-stu-id="196df-252">**Disable**</span></span>\
<span data-ttu-id="196df-253">Nie przetaczaj dalej.</span><span class="sxs-lookup"><span data-stu-id="196df-253">Don't roll forward.</span></span> <span data-ttu-id="196df-254">Powiąż tylko z określoną wersją.</span><span class="sxs-lookup"><span data-stu-id="196df-254">Only bind to specified version.</span></span> <span data-ttu-id="196df-255">Te zasady nie są zalecane do użytku ogólnego, ponieważ uniemożliwiają one przekazanie do najnowszych poprawek.</span><span class="sxs-lookup"><span data-stu-id="196df-255">This policy isn't recommended for general use because it disables the ability to roll forward to the latest patches.</span></span> <span data-ttu-id="196df-256">Ta wartość jest zalecana tylko do celów testowych.</span><span class="sxs-lookup"><span data-stu-id="196df-256">This value is only recommended for testing.</span></span>

<span data-ttu-id="196df-257">Oprócz ustawienia **Wyłącz** wszystkie ustawienia będą używać najwyższej dostępnej wersji poprawki.</span><span class="sxs-lookup"><span data-stu-id="196df-257">Besides the **Disable** setting, all settings will use the highest available patch version.</span></span>

## <a name="windows-desktop"></a><span data-ttu-id="196df-258">Pulpit systemu Windows</span><span class="sxs-lookup"><span data-stu-id="196df-258">Windows desktop</span></span>

<span data-ttu-id="196df-259">Program .NET Core 3,0 obsługuje aplikacje klasyczne systemu Windows przy użyciu Windows Presentation Foundation (WPF) i Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="196df-259">.NET Core 3.0 supports Windows desktop applications using Windows Presentation Foundation (WPF) and Windows Forms.</span></span> <span data-ttu-id="196df-260">Te struktury obsługują również korzystanie z nowoczesnych kontrolek i stylów Fluent z poziomu biblioteki XAML interfejsu użytkownika systemu Windows (WinUI) za pośrednictwem [wysp XAML](/windows/uwp/xaml-platform/xaml-host-controls).</span><span class="sxs-lookup"><span data-stu-id="196df-260">These frameworks also support using modern controls and Fluent styling from the Windows UI XAML Library (WinUI) via [XAML islands](/windows/uwp/xaml-platform/xaml-host-controls).</span></span>

<span data-ttu-id="196df-261">Składnik pulpitu systemu Windows jest częścią zestawu SDK systemu Windows .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="196df-261">The Windows Desktop component is part of the Windows .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="196df-262">Nową aplikację WPF lub Windows Forms można utworzyć przy użyciu następujących `dotnet` poleceń:</span><span class="sxs-lookup"><span data-stu-id="196df-262">You can create a new WPF or Windows Forms app with the following `dotnet` commands:</span></span>

```console
dotnet new wpf
dotnet new winforms
```

<span data-ttu-id="196df-263">Program Visual Studio 2019 dodaje **nowe szablony projektów** dla platformy .net Core 3,0 Windows Forms i WPF.</span><span class="sxs-lookup"><span data-stu-id="196df-263">Visual Studio 2019 adds **New Project** templates for .NET Core 3.0 Windows Forms and WPF.</span></span>

<span data-ttu-id="196df-264">Aby uzyskać więcej informacji na temat sposobu przenoszenia istniejącej aplikacji .NET Framework, zobacz [port WPF projekty](../porting/wpf.md) i [projekty Windows Forms portów](../porting/winforms.md).</span><span class="sxs-lookup"><span data-stu-id="196df-264">For more information about how to port an existing .NET Framework application, see [Port WPF projects](../porting/wpf.md) and [Port Windows Forms projects](../porting/winforms.md).</span></span>

## <a name="com-callable-components---windows-desktop"></a><span data-ttu-id="196df-265">Składniki wywoływane przez COM — Windows Desktop</span><span class="sxs-lookup"><span data-stu-id="196df-265">COM-callable components - Windows Desktop</span></span>

<span data-ttu-id="196df-266">W systemie Windows można teraz tworzyć zarządzane składniki COM.</span><span class="sxs-lookup"><span data-stu-id="196df-266">On Windows, you can now create COM-callable managed components.</span></span> <span data-ttu-id="196df-267">Ta funkcja ma kluczowe znaczenie dla korzystania z platformy .NET Core z modelami dodatków COM, a także do zapewnienia parzystości .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="196df-267">This capability is critical to use .NET Core with COM add-in models and also to provide parity with .NET Framework.</span></span>

<span data-ttu-id="196df-268">W przeciwieństwie do .NET Framework, w którym *Biblioteka mscoree. dll* była używana jako serwer com, podczas kompilowania składnika com program .NET Core doda natywną bibliotekę DLL uruchamiania do katalogu *bin* .</span><span class="sxs-lookup"><span data-stu-id="196df-268">Unlike .NET Framework where the *mscoree.dll* was used as the COM server, .NET Core will add a native launcher dll to the *bin* directory when you build your COM component.</span></span>

<span data-ttu-id="196df-269">Przykład sposobu tworzenia składnika modelu COM i korzystania z niego można znaleźć w [demonstracji modelu COM](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).</span><span class="sxs-lookup"><span data-stu-id="196df-269">For an example of how to create a COM component and consume it, see the [COM Demo](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).</span></span>

## <a name="msix-deployment---windows-desktop"></a><span data-ttu-id="196df-270">Wdrażanie MSIX — Windows Desktop</span><span class="sxs-lookup"><span data-stu-id="196df-270">MSIX Deployment - Windows Desktop</span></span>

<span data-ttu-id="196df-271">[MSIX](https://docs.microsoft.com/windows/msix/) to nowy format pakietu aplikacji systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="196df-271">[MSIX](https://docs.microsoft.com/windows/msix/) is a new Windows application package format.</span></span> <span data-ttu-id="196df-272">Można go użyć do wdrożenia aplikacji klasycznych platformy .NET Core 3,0 w systemie Windows 10.</span><span class="sxs-lookup"><span data-stu-id="196df-272">It can be used to deploy .NET Core 3.0 desktop applications to Windows 10.</span></span>

<span data-ttu-id="196df-273">[Projekt pakietu aplikacji systemu Windows](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), dostępny w programie Visual Studio 2019, umożliwia tworzenie pakietów MSIX przy użyciu [](../deploying/index.md#self-contained-deployments-scd) samodzielnych aplikacji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="196df-273">The [Windows Application Packaging Project](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), available in Visual Studio 2019, allows you to create MSIX packages with [self-contained](../deploying/index.md#self-contained-deployments-scd) .NET Core applications.</span></span>

<span data-ttu-id="196df-274">Plik projektu .NET Core musi określać obsługiwane środowiska uruchomieniowe we `<RuntimeIdentifiers>` właściwości:</span><span class="sxs-lookup"><span data-stu-id="196df-274">The .NET Core project file must specify the supported runtimes in the `<RuntimeIdentifiers>` property:</span></span>

```xml
<RuntimeIdentifiers>win-x86;win-x64</RuntimeIdentifiers>
```

## <a name="winforms-high-dpi"></a><span data-ttu-id="196df-275">Bardzo wysokie wartości DPI</span><span class="sxs-lookup"><span data-stu-id="196df-275">WinForms high DPI</span></span>

<span data-ttu-id="196df-276">Aplikacje .NET Core Windows Forms mogą ustawiać tryb wysokiej rozdzielczości DPI <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType>przy użyciu.</span><span class="sxs-lookup"><span data-stu-id="196df-276">.NET Core Windows Forms applications can set high DPI mode with <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType>.</span></span> <span data-ttu-id="196df-277">Metoda ustawia odpowiedni tryb wysokiej rozdzielczości DPI, chyba że ustawienie zostało ustawione za pomocą innych metod, `App.Manifest` takich jak lub P/ `Application.Run`Invokeprzed. `SetHighDpiMode`</span><span class="sxs-lookup"><span data-stu-id="196df-277">The `SetHighDpiMode` method sets the corresponding high DPI mode unless the setting has been set by other means like `App.Manifest` or P/Invoke before `Application.Run`.</span></span>

<span data-ttu-id="196df-278">Możliwe `highDpiMode` wartości wyrażone <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType> przez wyliczenie są następujące:</span><span class="sxs-lookup"><span data-stu-id="196df-278">The possible `highDpiMode` values, as expressed by the <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType> enum are:</span></span>

* `DpiUnaware`
* `SystemAware`
* `PerMonitor`
* `PerMonitorV2`
* `DpiUnawareGdiScaled`

<span data-ttu-id="196df-279">Aby uzyskać więcej informacji na temat trybów wysokiej rozdzielczości DPI, zobacz [Tworzenie aplikacji klasycznych o wysokiej rozdzielczości DPI w systemie Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows).</span><span class="sxs-lookup"><span data-stu-id="196df-279">For more information about high DPI modes, see [High DPI Desktop Application Development on Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows).</span></span>

## <a name="ranges-and-indices"></a><span data-ttu-id="196df-280">Zakresy i indeksy</span><span class="sxs-lookup"><span data-stu-id="196df-280">Ranges and indices</span></span>

<span data-ttu-id="196df-281">Nowy <xref:System.Index?displayProperty=nameWithType> typ może służyć do indeksowania.</span><span class="sxs-lookup"><span data-stu-id="196df-281">The new <xref:System.Index?displayProperty=nameWithType> type can be used for indexing.</span></span> <span data-ttu-id="196df-282">Można utworzyć jedną z nich na `int` podstawie liczby od początku lub z operatorem prefiksu `^` (C#), który liczy się od końca:</span><span class="sxs-lookup"><span data-stu-id="196df-282">You can create one from an `int` that counts from the beginning, or with a prefix `^` operator (C#) that counts from the end:</span></span>

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

<span data-ttu-id="196df-283">Istnieje również <xref:System.Range?displayProperty=nameWithType> typ, który składa się z dwóch `Index` wartości, jeden dla początku i jeden dla końca, i `x..y` może być zapisany z wyrażeniem zakresu (C#).</span><span class="sxs-lookup"><span data-stu-id="196df-283">There's also the <xref:System.Range?displayProperty=nameWithType> type, which consists of two `Index` values, one for the start and one for the end, and can be written with a `x..y` range expression (C#).</span></span> <span data-ttu-id="196df-284">Następnie można indeksować za pomocą `Range`, co spowoduje utworzenie wycinka:</span><span class="sxs-lookup"><span data-stu-id="196df-284">You can then index with a `Range`, which produces a slice:</span></span>

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

<span data-ttu-id="196df-285">Aby uzyskać więcej informacji, zobacz [Samouczek dotyczący zakresów i indeksów](../../csharp/tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="196df-285">For more information, see the [ranges and indices tutorial](../../csharp/tutorials/ranges-indexes.md).</span></span>

## <a name="async-streams"></a><span data-ttu-id="196df-286">Strumienie asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="196df-286">Async streams</span></span>

<span data-ttu-id="196df-287">Typ jest nową wersją asynchroniczną programu <xref:System.Collections.Generic.IEnumerable%601>. <xref:System.Collections.Generic.IAsyncEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="196df-287">The <xref:System.Collections.Generic.IAsyncEnumerable%601> type is a new asynchronous version of <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="196df-288">Język pozwala `await foreach` `IAsyncEnumerable<T>` na korzystanie z ich elementów i używanie `yield return` ich do tworzenia elementów.</span><span class="sxs-lookup"><span data-stu-id="196df-288">The language lets you `await foreach` over `IAsyncEnumerable<T>` to consume their elements, and use `yield return` to them to produce elements.</span></span>

<span data-ttu-id="196df-289">Poniższy przykład ilustruje produkcję i zużycie strumieni asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="196df-289">The following example demonstrates both production and consumption of async streams.</span></span> <span data-ttu-id="196df-290">Instrukcja jest asynchroniczna i sama używa `yield return` do tworzenia strumienia asynchronicznego dla obiektów wywołujących. `foreach`</span><span class="sxs-lookup"><span data-stu-id="196df-290">The `foreach` statement is async and itself uses `yield return` to produce an async stream for callers.</span></span> <span data-ttu-id="196df-291">Ten wzorzec (using `yield return`) jest zalecanym modelem do tworzenia strumieni asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="196df-291">This pattern (using `yield return`) is the recommended model for producing async streams.</span></span>

```csharp
async IAsyncEnumerable<int> GetBigResultsAsync()
{
    await foreach (var result in GetResultsAsync())
    {
        if (result > 20) yield return result; 
    }
}
```

<span data-ttu-id="196df-292">Oprócz możliwości `await foreach`można także tworzyć Iteratory asynchroniczne, na przykład iterator, który `IAsyncEnumerable/IAsyncEnumerator` zwraca, że można zarówno `await` , jak i `yield` w.</span><span class="sxs-lookup"><span data-stu-id="196df-292">In addition to being able to `await foreach`, you can also create async iterators, for example, an iterator that returns an `IAsyncEnumerable/IAsyncEnumerator` that you can both `await` and `yield` in.</span></span> <span data-ttu-id="196df-293">W przypadku obiektów, które muszą zostać usunięte, można użyć `IAsyncDisposable`różnych typów BCL, takich jak `Stream` i `Timer`.</span><span class="sxs-lookup"><span data-stu-id="196df-293">For objects that need to be disposed, you can use `IAsyncDisposable`, which various BCL types implement, such as `Stream` and `Timer`.</span></span>

<span data-ttu-id="196df-294">Aby uzyskać więcej informacji, zobacz [Samouczek dotyczący strumieni asynchronicznych](../../csharp/tutorials/generate-consume-asynchronous-stream.md).</span><span class="sxs-lookup"><span data-stu-id="196df-294">For more information, see the [async streams tutorial](../../csharp/tutorials/generate-consume-asynchronous-stream.md).</span></span>

## <a name="ieee-floating-point-improvements"></a><span data-ttu-id="196df-295">Udoskonalenia zmiennoprzecinkowe IEEE</span><span class="sxs-lookup"><span data-stu-id="196df-295">IEEE Floating-point improvements</span></span>

<span data-ttu-id="196df-296">Interfejsy API zmiennoprzecinkowe są aktualizowane w celu zapewnienia zgodności z [poprawką IEEE 754-2008](https://en.wikipedia.org/wiki/IEEE_754-2008_revision).</span><span class="sxs-lookup"><span data-stu-id="196df-296">Floating point APIs are being updated to comply with [IEEE 754-2008 revision](https://en.wikipedia.org/wiki/IEEE_754-2008_revision).</span></span> <span data-ttu-id="196df-297">Celem tych zmian jest uwidocznienie wszystkich **wymaganych** operacji i upewnienie się, że są one zgodne z specyfikacją IEEE. Aby uzyskać więcej informacji na temat ulepszeń zmiennoprzecinkowych, zobacz [udoskonalenia analizy i formatowania zmiennoprzecinkowe w wpisie na blogu programu .NET Core 3,0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) .</span><span class="sxs-lookup"><span data-stu-id="196df-297">The goal of these changes is to expose all **required** operations and ensure that they're behaviorally compliant with the IEEE spec. For more information about floating-point improvements, see the [Floating-Point Parsing and Formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog post.</span></span>

<span data-ttu-id="196df-298">Poprawki dotyczące analizowania i formatowania obejmują:</span><span class="sxs-lookup"><span data-stu-id="196df-298">Parsing and formatting fixes include:</span></span>

* <span data-ttu-id="196df-299">Poprawnie Analizuj i Zaokrąglij dane wejściowe o dowolnej długości.</span><span class="sxs-lookup"><span data-stu-id="196df-299">Correctly parse and round inputs of any length.</span></span>
* <span data-ttu-id="196df-300">Prawidłowo Przeanalizuj i sformatuj ujemną wartość zero.</span><span class="sxs-lookup"><span data-stu-id="196df-300">Correctly parse and format negative zero.</span></span>
* <span data-ttu-id="196df-301">Poprawne analizowanie `Infinity` i `NaN` wykonywanie kontroli bez uwzględniania wielkości liter i Zezwalanie na opcjonalne poprzednie `+` , jeśli ma to zastosowanie.</span><span class="sxs-lookup"><span data-stu-id="196df-301">Correctly parse `Infinity` and `NaN` by doing a case-insensitive check and allowing an optional preceding `+` where applicable.</span></span>

<span data-ttu-id="196df-302">Nowe <xref:System.Math?displayProperty=nameWithType> interfejsy API obejmują:</span><span class="sxs-lookup"><span data-stu-id="196df-302">New <xref:System.Math?displayProperty=nameWithType> APIs include:</span></span>

* <span data-ttu-id="196df-303"><xref:System.Math.BitIncrement(System.Double)>lub<xref:System.Math.BitDecrement(System.Double)></span><span class="sxs-lookup"><span data-stu-id="196df-303"><xref:System.Math.BitIncrement(System.Double)> and <xref:System.Math.BitDecrement(System.Double)></span></span>\
<span data-ttu-id="196df-304">Odnosi się do `nextUp` operacji `nextDown` i IEEE.</span><span class="sxs-lookup"><span data-stu-id="196df-304">Corresponds to the `nextUp` and `nextDown` IEEE operations.</span></span> <span data-ttu-id="196df-305">Zwracają one najmniejszą liczbę zmiennoprzecinkową, która porównuje większe lub mniejsze niż dane wejściowe (odpowiednio).</span><span class="sxs-lookup"><span data-stu-id="196df-305">They return the smallest floating-point number that compares greater or lesser than the input (respectively).</span></span> <span data-ttu-id="196df-306">Na przykład `Math.BitIncrement(0.0)` zwrócimy `double.Epsilon`.</span><span class="sxs-lookup"><span data-stu-id="196df-306">For example, `Math.BitIncrement(0.0)` would return `double.Epsilon`.</span></span>

* <span data-ttu-id="196df-307"><xref:System.Math.MaxMagnitude(System.Double,System.Double)>lub<xref:System.Math.MinMagnitude(System.Double,System.Double)></span><span class="sxs-lookup"><span data-stu-id="196df-307"><xref:System.Math.MaxMagnitude(System.Double,System.Double)> and <xref:System.Math.MinMagnitude(System.Double,System.Double)></span></span>\
<span data-ttu-id="196df-308">Odnosi się do `maxNumMag` operacji `minNumMag` i IEEE, zwracają wartość, która jest większa lub mniejsza o wielkości dwóch danych wejściowych (odpowiednio).</span><span class="sxs-lookup"><span data-stu-id="196df-308">Corresponds to the `maxNumMag` and `minNumMag` IEEE operations, they return the value that is greater or lesser in magnitude of the two inputs (respectively).</span></span> <span data-ttu-id="196df-309">Na przykład `Math.MaxMagnitude(2.0, -3.0)` zwrócimy `-3.0`.</span><span class="sxs-lookup"><span data-stu-id="196df-309">For example, `Math.MaxMagnitude(2.0, -3.0)` would return `-3.0`.</span></span>

* <xref:System.Math.ILogB(System.Double)>\
<span data-ttu-id="196df-310">Odnosi się do `logB` operacji IEEE, która zwraca wartość całkowitą, zwraca integralny dziennik Base-2 parametru wejściowego.</span><span class="sxs-lookup"><span data-stu-id="196df-310">Corresponds to the `logB` IEEE operation that returns an integral value, it returns the integral base-2 log of the input parameter.</span></span> <span data-ttu-id="196df-311">Ta metoda jest efektywnie taka sama jak `floor(log2(x))`, ale została wykonana z minimalnym błędem zaokrąglania.</span><span class="sxs-lookup"><span data-stu-id="196df-311">This method is effectively the same as `floor(log2(x))`, but done with minimal rounding error.</span></span>

* <xref:System.Math.ScaleB(System.Double,System.Int32)>\
<span data-ttu-id="196df-312">Odnosi się do `scaleB` operacji IEEE, która przyjmuje wartość całkowitą, która zwraca efektywność `x * pow(2, n)`, ale jest wykonywana z minimalnym błędem zaokrąglania.</span><span class="sxs-lookup"><span data-stu-id="196df-312">Corresponds to the `scaleB` IEEE operation that takes an integral value, it returns effectively `x * pow(2, n)`, but is done with minimal rounding error.</span></span>

* <xref:System.Math.Log2(System.Double)>\
<span data-ttu-id="196df-313">Odpowiada operacji `log2` IEEE, Zwraca logarytm o podstawie 2.</span><span class="sxs-lookup"><span data-stu-id="196df-313">Corresponds to the `log2` IEEE operation, it returns the base-2 logarithm.</span></span> <span data-ttu-id="196df-314">Minimalizuje błąd zaokrąglania.</span><span class="sxs-lookup"><span data-stu-id="196df-314">It minimizes rounding error.</span></span>

* <xref:System.Math.FusedMultiplyAdd(System.Double,System.Double,System.Double)>\
<span data-ttu-id="196df-315">Odnosi się do `fma` operacji IEEE, dlatego wykonuje odrzucane mnożenie dodawania.</span><span class="sxs-lookup"><span data-stu-id="196df-315">Corresponds to the `fma` IEEE operation, it performs a fused multiply add.</span></span> <span data-ttu-id="196df-316">Oznacza to, `(x * y) + z` że jest to jedna operacja, a tym samym Minimalizacja błędu zaokrąglania.</span><span class="sxs-lookup"><span data-stu-id="196df-316">That is, it does `(x * y) + z` as a single operation, thereby minimizing the rounding error.</span></span> <span data-ttu-id="196df-317">Przykładem może być `FusedMultiplyAdd(1e308, 2.0, -1e308)` zwracana wartość `1e308`.</span><span class="sxs-lookup"><span data-stu-id="196df-317">An example would be `FusedMultiplyAdd(1e308, 2.0, -1e308)` which returns `1e308`.</span></span> <span data-ttu-id="196df-318">Regularne `(1e308 * 2.0) - 1e308` zwroty `double.PositiveInfinity`.</span><span class="sxs-lookup"><span data-stu-id="196df-318">The regular `(1e308 * 2.0) - 1e308` returns `double.PositiveInfinity`.</span></span>

* <xref:System.Math.CopySign(System.Double,System.Double)>\
<span data-ttu-id="196df-319">Odpowiada operacji `x`IEEE, zwraca wartość, `y`ale ze znakiem. `copySign`</span><span class="sxs-lookup"><span data-stu-id="196df-319">Corresponds to the `copySign` IEEE operation, it returns the value of `x`, but with the sign of `y`.</span></span>

## <a name="fast-built-in-json-support"></a><span data-ttu-id="196df-320">Szybka Wbudowana obsługa JSON</span><span class="sxs-lookup"><span data-stu-id="196df-320">Fast built-in JSON support</span></span>

<span data-ttu-id="196df-321">Użytkownicy platformy .NET mogą w dużym stopniu korzystać z [**JSON.NET**](https://www.newtonsoft.com/json) i innych popularnych bibliotek JSON, które nadal są dobrym wybórem.</span><span class="sxs-lookup"><span data-stu-id="196df-321">.NET users have largely relied on [**Json.NET**](https://www.newtonsoft.com/json) and other popular JSON libraries, which continue to be good choices.</span></span> <span data-ttu-id="196df-322">**JSON.NET** używa ciągów .NET jako podstawowego elementu DataType, który jest UTF-16 pod okapem.</span><span class="sxs-lookup"><span data-stu-id="196df-322">**Json.NET** uses .NET strings as its base datatype, which is UTF-16 under the hood.</span></span>

<span data-ttu-id="196df-323">Nowa Wbudowana obsługa JSON to wysoka wydajność, niska alokacja i oparta na `Span<byte>`.</span><span class="sxs-lookup"><span data-stu-id="196df-323">The new built-in JSON support is high-performance, low allocation, and based on `Span<byte>`.</span></span> <span data-ttu-id="196df-324">Do programu .NET Core 3,0 <xref:System.Text.Json?displayProperty=nameWithType> przestrzeń nazw dodano trzy nowe główne typy powiązane z JSON.</span><span class="sxs-lookup"><span data-stu-id="196df-324">Three new main JSON-related types have been added to .NET Core 3.0 the <xref:System.Text.Json?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="196df-325">Te typy nie obsługują *jeszcze* zwykłych serializacji i deserializacji obiektu CLR (POCO).</span><span class="sxs-lookup"><span data-stu-id="196df-325">These types don't *yet* support plain old CLR object (POCO) serialization and deserialization.</span></span>

### <a name="utf8jsonreader"></a><span data-ttu-id="196df-326">Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="196df-326">Utf8JsonReader</span></span>

<span data-ttu-id="196df-327"><xref:System.Text.Json.Utf8JsonReader?displayProperty=nameWithType>jest wysoką wydajnością, niskim alokacją, czytnikiem tylko do przodu dla tekstu JSON zakodowanego w formacie UTF-8, `ReadOnlySpan<byte>`Odczytaj od.</span><span class="sxs-lookup"><span data-stu-id="196df-327"><xref:System.Text.Json.Utf8JsonReader?displayProperty=nameWithType> is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a `ReadOnlySpan<byte>`.</span></span> <span data-ttu-id="196df-328">`Utf8JsonReader` Jest to podstawowy typ niskiego poziomu, który może służyć do tworzenia niestandardowych analizatorów i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="196df-328">The `Utf8JsonReader` is a foundational, low-level type, that can be used to build custom parsers and deserializers.</span></span> <span data-ttu-id="196df-329">Odczytywanie za pośrednictwem ładunku JSON przy `Utf8JsonReader` użyciu nowego jest szybsze niż używanie czytnika z **JSON.NET**.</span><span class="sxs-lookup"><span data-stu-id="196df-329">Reading through a JSON payload using the new `Utf8JsonReader` is 2x faster than using the reader from **Json.NET**.</span></span> <span data-ttu-id="196df-330">Nie jest przydzielany do momentu, gdy wymagane jest actualize tokenów JSON jako ciągów (UTF-16).</span><span class="sxs-lookup"><span data-stu-id="196df-330">It doesn't allocate until you need to actualize JSON tokens as (UTF-16) strings.</span></span>

<span data-ttu-id="196df-331">Oto przykład odczytywania za pomocą pliku [**Launch. JSON**](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) utworzonego przez Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="196df-331">Here is an example of reading through the [**launch.json**](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) file created by Visual Studio Code:</span></span>

[!CODE-csharp[Utf8JsonReader](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#PrintJson)]

[!CODE-csharp[Utf8JsonReader](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#PrintJsonCall)]

### <a name="utf8jsonwriter"></a><span data-ttu-id="196df-332">Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="196df-332">Utf8JsonWriter</span></span>

<span data-ttu-id="196df-333"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType>zapewnia wysoką wydajność, niebuforowaną, tylko do przodu sposób pisania zakodowanego tekstu JSON w formacie UTF-8 ze wspólnych typów, takich `String`jak `Int32`,, `DateTime`i.</span><span class="sxs-lookup"><span data-stu-id="196df-333"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType> provides a high-performance, non-cached, forward-only way to write UTF-8 encoded JSON text from common .NET types like `String`, `Int32`, and `DateTime`.</span></span> <span data-ttu-id="196df-334">Podobnie jak w przypadku czytnika, moduł zapisujący jest podstawą typu, który może służyć do tworzenia serializatorów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="196df-334">Like the reader, the writer is a foundational, low-level type, that can be used to build custom serializers.</span></span> <span data-ttu-id="196df-335">Zapis ładunku JSON przy użyciu nowego `Utf8JsonWriter` programu to 30-80% szybciej niż przy użyciu składnika zapisywania z **JSON.NET** i nie jest przydzielany.</span><span class="sxs-lookup"><span data-stu-id="196df-335">Writing a JSON payload using the new `Utf8JsonWriter` is 30-80% faster than using the writer from **Json.NET** and doesn't allocate.</span></span>

### <a name="jsondocument"></a><span data-ttu-id="196df-336">JsonDocument</span><span class="sxs-lookup"><span data-stu-id="196df-336">JsonDocument</span></span>

<span data-ttu-id="196df-337"><xref:System.Text.Json.JsonDocument?displayProperty=nameWithType>jest zbudowany z góry `Utf8JsonReader`.</span><span class="sxs-lookup"><span data-stu-id="196df-337"><xref:System.Text.Json.JsonDocument?displayProperty=nameWithType> is built on top of the `Utf8JsonReader`.</span></span> <span data-ttu-id="196df-338">`JsonDocument` Zapewnia możliwość analizowania danych JSON i tworzenia Document Object Model tylko do odczytu (dom), do których można wykonywać zapytania, aby obsługiwać losowy dostęp i Wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="196df-338">The `JsonDocument` provides the ability to parse JSON data and build a read-only Document Object Model (DOM) that can be queried to support random access and enumeration.</span></span> <span data-ttu-id="196df-339">Do elementów JSON, które tworzą dane, można uzyskać dostęp za pośrednictwem <xref:System.Text.Json.JsonElement> typu, który jest udostępniany `JsonDocument` przez właściwość o `RootElement`nazwie.</span><span class="sxs-lookup"><span data-stu-id="196df-339">The JSON elements that compose the data can be accessed via the <xref:System.Text.Json.JsonElement> type that is exposed by the `JsonDocument` as a property called `RootElement`.</span></span> <span data-ttu-id="196df-340">`JsonElement` Zawiera tablicę JSON i moduł wyliczający obiektów oraz interfejsy API służące do konwertowania tekstu JSON na popularne typy .NET.</span><span class="sxs-lookup"><span data-stu-id="196df-340">The `JsonElement` contains the JSON array and object enumerators along with APIs to convert JSON text to common .NET types.</span></span> <span data-ttu-id="196df-341">Analizowanie typowego ładunku JSON i uzyskiwanie dostępu do wszystkich jego `JsonDocument` elementów członkowskich przy użyciu programu ma wartość 2-3 — szybszy niż **JSON.NET** z małym alokacją dla danych o rozsądnym rozmiarze (czyli < 1 MB).</span><span class="sxs-lookup"><span data-stu-id="196df-341">Parsing a typical JSON payload and accessing all its members using the `JsonDocument` is 2-3x faster than **Json.NET** with little allocations for data that is reasonably sized (that is, < 1 MB).</span></span>

<span data-ttu-id="196df-342">Oto przykładowe użycie `JsonDocument` i `JsonElement` , które może służyć jako punkt początkowy:</span><span class="sxs-lookup"><span data-stu-id="196df-342">Here is a sample usage of the `JsonDocument` and `JsonElement` that can be used as a starting point:</span></span>

[!CODE-csharp[JsonDocument](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#ReadJson)]

<span data-ttu-id="196df-343">Poniżej znajduje się C# przykład 8,0 do odczytu za pomocą pliku [Launch. json](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) utworzonego przez Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="196df-343">Here is a C# 8.0 example of reading through the [**launch.json**](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) file created by Visual Studio Code:</span></span>

[!CODE-csharp[JsonDocument](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#ReadJsonCall)]

### <a name="jsonserializer"></a><span data-ttu-id="196df-344">JsonSerializer</span><span class="sxs-lookup"><span data-stu-id="196df-344">JsonSerializer</span></span>

<span data-ttu-id="196df-345"><xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType>jest zbudowany w oparciu <xref:System.Text.Json.Utf8JsonReader> o i <xref:System.Text.Json.Utf8JsonWriter> , aby zapewnić szybką, niską pamięć opcji serializacji podczas pracy z dokumentami i fragmentami JSON.</span><span class="sxs-lookup"><span data-stu-id="196df-345"><xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> is built on top of <xref:System.Text.Json.Utf8JsonReader> and <xref:System.Text.Json.Utf8JsonWriter> to provide a fast, low-memory serialization option when working with JSON documents and fragments.</span></span>

<span data-ttu-id="196df-346">Oto przykład serializacji obiektu do formatu JSON:</span><span class="sxs-lookup"><span data-stu-id="196df-346">Here is an example of serializing an object to JSON:</span></span>

[!CODE-csharp[JsonSerializer](~/samples/snippets/core/whats-new/whats-new-in-30/cs/JSON.cs#JsonSerialize)]

<span data-ttu-id="196df-347">Oto przykład deserializacji ciągu JSON do obiektu.</span><span class="sxs-lookup"><span data-stu-id="196df-347">Here is an example of deserializing a JSON string to an object.</span></span> <span data-ttu-id="196df-348">Można użyć ciągu JSON utworzonego w poprzednim przykładzie:</span><span class="sxs-lookup"><span data-stu-id="196df-348">You can use the JSON string produced by the previous example:</span></span>

[!CODE-csharp[JsonDeserializer](~/samples/snippets/core/whats-new/whats-new-in-30/cs/JSON.cs#JsonDeserialize)]

## <a name="interop-improvements"></a><span data-ttu-id="196df-349">Udoskonalenia międzyoperacyjności</span><span class="sxs-lookup"><span data-stu-id="196df-349">Interop improvements</span></span>

<span data-ttu-id="196df-350">Program .NET Core 3,0 zwiększa natywną międzyoperacyjność interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="196df-350">.NET Core 3.0 improves native API interop.</span></span>

### <a name="type-nativelibrary"></a><span data-ttu-id="196df-351">Wpisz: NativeLibrary</span><span class="sxs-lookup"><span data-stu-id="196df-351">Type: NativeLibrary</span></span>

<span data-ttu-id="196df-352"><xref:System.Runtime.InteropServices.NativeLibrary?displayProperty=nameWithType>zapewnia hermetyzację do ładowania biblioteki natywnej (przy użyciu tej samej logiki obciążenia co .NET Core P/Invoke) i udostępniającej odpowiednie funkcje pomocnika, `getSymbol`takie jak.</span><span class="sxs-lookup"><span data-stu-id="196df-352"><xref:System.Runtime.InteropServices.NativeLibrary?displayProperty=nameWithType> provides an encapsulation for loading a native library (using the same load logic as .NET Core P/Invoke) and providing the relevant helper functions such as `getSymbol`.</span></span> <span data-ttu-id="196df-353">Aby zapoznać się z przykładowym kodem, zobacz [Demonstracja DLLMap](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin).</span><span class="sxs-lookup"><span data-stu-id="196df-353">For a code example, see the [DLLMap Demo](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin).</span></span>

### <a name="windows-native-interop"></a><span data-ttu-id="196df-354">Windows Native Interop</span><span class="sxs-lookup"><span data-stu-id="196df-354">Windows Native Interop</span></span>

<span data-ttu-id="196df-355">System Windows oferuje bogaty natywny interfejs API w postaci prostych interfejsów API języka C, COM i WinRT.</span><span class="sxs-lookup"><span data-stu-id="196df-355">Windows offers a rich native API in the form of flat C APIs, COM, and WinRT.</span></span> <span data-ttu-id="196df-356">Podczas gdy platforma .NET Core obsługuje funkcję **P/Invoke**, program .net Core 3,0 dodaje możliwość **CoCreate interfejsów API modelu COM** i **aktywowania interfejsów API WinRT**.</span><span class="sxs-lookup"><span data-stu-id="196df-356">While .NET Core supports **P/Invoke**, .NET Core 3.0 adds the ability to **CoCreate COM APIs** and **Activate WinRT APIs**.</span></span> <span data-ttu-id="196df-357">Aby zapoznać się z przykładem kodu, zobacz [Demonstracja programu Excel](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).</span><span class="sxs-lookup"><span data-stu-id="196df-357">For a code example, see the [Excel Demo](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).</span></span>

## <a name="http2-support"></a><span data-ttu-id="196df-358">Obsługa protokołu HTTP/2</span><span class="sxs-lookup"><span data-stu-id="196df-358">HTTP/2 support</span></span>

<span data-ttu-id="196df-359"><xref:System.Net.Http.HttpClient?displayProperty=nameWithType> Typ obsługuje protokół HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="196df-359">The <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> type supports the HTTP/2 protocol.</span></span> <span data-ttu-id="196df-360">Jeśli protokół HTTP/2 jest włączony, wersja protokołu HTTP jest negocjowana za pośrednictwem protokołu TLS/CLIENTHELLO ALPN, a protokół HTTP/2 jest używany, jeśli serwer zdecyduje się go użyć.</span><span class="sxs-lookup"><span data-stu-id="196df-360">If HTTP/2 is enabled, the HTTP protocol version is negotiated via TLS/ALPN, and HTTP/2 is used if the server elects to use it.</span></span>

<span data-ttu-id="196df-361">Domyślnym protokołem jest protokół HTTP/1.1, ale protokół HTTP/2 można włączyć na dwa różne sposoby.</span><span class="sxs-lookup"><span data-stu-id="196df-361">The default protocol remains HTTP/1.1, but HTTP/2 can be enabled in two different ways.</span></span> <span data-ttu-id="196df-362">Najpierw można ustawić komunikat żądania HTTP na potrzeby używania protokołu HTTP/2:</span><span class="sxs-lookup"><span data-stu-id="196df-362">First, you can set the HTTP request message to use HTTP/2:</span></span>

[!CODE-csharp[Http2Request](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Request)]

<span data-ttu-id="196df-363">Po drugie, można domyślnie <xref:System.Net.Http.HttpClient> zmienić użycie protokołu HTTP/2:</span><span class="sxs-lookup"><span data-stu-id="196df-363">Second, you can change <xref:System.Net.Http.HttpClient> to use HTTP/2 by default:</span></span>

[!CODE-csharp[Http2Client](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Client)]

<span data-ttu-id="196df-364">W wielu przypadkach podczas tworzenia aplikacji chcesz użyć nieszyfrowanego połączenia.</span><span class="sxs-lookup"><span data-stu-id="196df-364">Many times when you're developing an application, you want to use an unencrypted connection.</span></span> <span data-ttu-id="196df-365">Jeśli wiesz, że docelowy punkt końcowy będzie używać protokołu HTTP/2, możesz włączyć nieszyfrowane połączenia dla protokołu HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="196df-365">If you know the target endpoint will be using HTTP/2, you can turn on unencrypted connections for HTTP/2.</span></span> <span data-ttu-id="196df-366">Można ją włączyć przez ustawienie `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT` zmiennej środowiskowej na `1` lub przez włączenie jej w kontekście aplikacji:</span><span class="sxs-lookup"><span data-stu-id="196df-366">You can turn it on by setting the `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT` environment variable to `1` or by enabling it in the app context:</span></span>

[!CODE-csharp[Http2Context](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#AppContext)]

## <a name="tls-13--openssl-111-on-linux"></a><span data-ttu-id="196df-367">TLS 1,3 & OpenSSL 1.1.1 w systemie Linux</span><span class="sxs-lookup"><span data-stu-id="196df-367">TLS 1.3 & OpenSSL 1.1.1 on Linux</span></span>

<span data-ttu-id="196df-368">Platforma .NET Core wykorzystuje teraz zalety [protokołu TLS 1,3 w OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), gdy jest on dostępny w danym środowisku.</span><span class="sxs-lookup"><span data-stu-id="196df-368">.NET Core now takes advantage of [TLS 1.3 support in OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), when it's available in a given environment.</span></span> <span data-ttu-id="196df-369">Z protokołem TLS 1,3:</span><span class="sxs-lookup"><span data-stu-id="196df-369">With TLS 1.3:</span></span>

* <span data-ttu-id="196df-370">Czas połączenia jest ulepszony ze zredukowanymi przedziałami rundy między klientem i serwerem.</span><span class="sxs-lookup"><span data-stu-id="196df-370">Connection times are improved with reduced round trips required between the client and server.</span></span>
* <span data-ttu-id="196df-371">Ulepszone zabezpieczenia spowodowane usuwaniem różnych przestarzałych i niezabezpieczonych algorytmów kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="196df-371">Improved security because of the removal of various obsolete and insecure cryptographic algorithms.</span></span>

<span data-ttu-id="196df-372">Jeśli jest dostępny, program .NET Core 3,0 używa **OpenSSL 1.1.1**, **OpenSSL 1.1.0**lub **OpenSSL 1.0.2** w systemie Linux.</span><span class="sxs-lookup"><span data-stu-id="196df-372">When available, .NET Core 3.0 uses **OpenSSL 1.1.1**, **OpenSSL 1.1.0**, or **OpenSSL 1.0.2** on a Linux system.</span></span> <span data-ttu-id="196df-373">Gdy **OpenSSL 1.1.1** jest dostępny, oba <xref:System.Net.Security.SslStream?displayProperty=nameWithType> typy <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> i używają **protokołu TLS 1,3** (przy założeniu, że zarówno klient, jak i serwer obsługują **protokół TLS 1,3**).</span><span class="sxs-lookup"><span data-stu-id="196df-373">When **OpenSSL 1.1.1** is available, both <xref:System.Net.Security.SslStream?displayProperty=nameWithType> and <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> types will use **TLS 1.3** (assuming both the client and server support **TLS 1.3**).</span></span>

>[!IMPORTANT]
><span data-ttu-id="196df-374">Systemy Windows i macOS nie obsługują jeszcze **protokołu TLS 1,3**.</span><span class="sxs-lookup"><span data-stu-id="196df-374">Windows and macOS do not yet support **TLS 1.3**.</span></span> <span data-ttu-id="196df-375">Platforma .NET Core 3,0 będzie obsługiwać **protokół TLS 1,3** w tych systemach operacyjnych, gdy będzie dostępna pomoc techniczna.</span><span class="sxs-lookup"><span data-stu-id="196df-375">.NET Core 3.0 will support **TLS 1.3** on these operating systems when support becomes available.</span></span>

<span data-ttu-id="196df-376">Poniższy C# przykład 8,0 ilustruje platformę .net Core 3,0 na Ubuntu 18,10 <https://www.cloudflare.com>z:</span><span class="sxs-lookup"><span data-stu-id="196df-376">The following C# 8.0 example demonstrates .NET Core 3.0 on Ubuntu 18.10 connecting to <https://www.cloudflare.com>:</span></span>

[!CODE-csharp[TLSExample](~/samples/snippets/core/whats-new/whats-new-in-30/cs/TLS.cs#TLS)]

## <a name="cryptography-ciphers"></a><span data-ttu-id="196df-377">Szyfrowanie kryptografii</span><span class="sxs-lookup"><span data-stu-id="196df-377">Cryptography ciphers</span></span>

<span data-ttu-id="196df-378">Program .NET 3,0 dodaje obsługę szyfrów **AES-GCM** i **AES-CCM** , implementowanych <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> za <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> pomocą i odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="196df-378">.NET 3.0 adds support for **AES-GCM** and **AES-CCM** ciphers, implemented with <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> and <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> respectively.</span></span> <span data-ttu-id="196df-379">Te algorytmy są [uwierzytelnianiem uwierzytelnianym przy użyciu algorytmów danych skojarzenia (AEAD)](https://en.wikipedia.org/wiki/Authenticated_encryption).</span><span class="sxs-lookup"><span data-stu-id="196df-379">These algorithms are both [Authenticated Encryption with Association Data (AEAD) algorithms](https://en.wikipedia.org/wiki/Authenticated_encryption).</span></span>

<span data-ttu-id="196df-380">Poniższy kod ilustruje użycie `AesGcm` szyfru do szyfrowania i odszyfrowywania danych losowych.</span><span class="sxs-lookup"><span data-stu-id="196df-380">The following code demonstrates using `AesGcm` cipher to encrypt and decrypt random data.</span></span>

[!CODE-csharp[AesGcm](~/samples/snippets/core/whats-new/whats-new-in-30/cs/Cipher.cs#AesGcm)]

## <a name="cryptographic-key-importexport"></a><span data-ttu-id="196df-381">Import/Eksport klucza kryptograficznego</span><span class="sxs-lookup"><span data-stu-id="196df-381">Cryptographic Key Import/Export</span></span>

<span data-ttu-id="196df-382">Program .NET Core 3,0 obsługuje importowanie i eksportowanie asymetrycznych kluczy publicznych i prywatnych z formatów standardowych.</span><span class="sxs-lookup"><span data-stu-id="196df-382">.NET Core 3.0 supports the import and export of asymmetric public and private keys from standard formats.</span></span> <span data-ttu-id="196df-383">Nie musisz używać certyfikatu X. 509.</span><span class="sxs-lookup"><span data-stu-id="196df-383">You don't need to use an X.509 certificate.</span></span>

<span data-ttu-id="196df-384">Wszystkie typy kluczy, takie jak *RSA*, *DSA*, *ECDSA*i *ECDiffieHellman*, obsługują następujące formaty:</span><span class="sxs-lookup"><span data-stu-id="196df-384">All key types, such as *RSA*, *DSA*, *ECDsa*, and *ECDiffieHellman*, support the following formats:</span></span>

* <span data-ttu-id="196df-385">**Klucz publiczny**</span><span class="sxs-lookup"><span data-stu-id="196df-385">**Public Key**</span></span>
  * <span data-ttu-id="196df-386">SubjectPublicKeyInfo X. 509</span><span class="sxs-lookup"><span data-stu-id="196df-386">X.509 SubjectPublicKeyInfo</span></span>

* <span data-ttu-id="196df-387">**Klucz prywatny**</span><span class="sxs-lookup"><span data-stu-id="196df-387">**Private key**</span></span>
  * <span data-ttu-id="196df-388">PrivateKeyInfo PKCS # 8</span><span class="sxs-lookup"><span data-stu-id="196df-388">PKCS#8 PrivateKeyInfo</span></span>
  * <span data-ttu-id="196df-389">EncryptedPrivateKeyInfo PKCS # 8</span><span class="sxs-lookup"><span data-stu-id="196df-389">PKCS#8 EncryptedPrivateKeyInfo</span></span>

<span data-ttu-id="196df-390">Klucze RSA obsługują również:</span><span class="sxs-lookup"><span data-stu-id="196df-390">RSA keys also support:</span></span>

* <span data-ttu-id="196df-391">**Klucz publiczny**</span><span class="sxs-lookup"><span data-stu-id="196df-391">**Public Key**</span></span>
  * <span data-ttu-id="196df-392">RSAPublicKey PKCS # 1</span><span class="sxs-lookup"><span data-stu-id="196df-392">PKCS#1 RSAPublicKey</span></span>

* <span data-ttu-id="196df-393">**Klucz prywatny**</span><span class="sxs-lookup"><span data-stu-id="196df-393">**Private key**</span></span>
  * <span data-ttu-id="196df-394">RSAPrivateKey PKCS # 1</span><span class="sxs-lookup"><span data-stu-id="196df-394">PKCS#1 RSAPrivateKey</span></span>

<span data-ttu-id="196df-395">Metody eksportowania generują dane binarne kodowane algorytmem DER, a metody importowe oczekują na to samo.</span><span class="sxs-lookup"><span data-stu-id="196df-395">The export methods produce DER-encoded binary data, and the import methods expect the same.</span></span> <span data-ttu-id="196df-396">Jeśli klucz jest przechowywany w formacie PEM przyjaznym dla tekstu, wywołujący będzie musiał odkodować zawartość przed wywołaniem metody Import.</span><span class="sxs-lookup"><span data-stu-id="196df-396">If a key is stored in the text-friendly PEM format, the caller will need to base64-decode the content before calling an import method.</span></span>

[!CODE-csharp[RSA](~/samples/snippets/core/whats-new/whats-new-in-30/cs/RSA.cs#Rsa)]

<span data-ttu-id="196df-397">Można sprawdzać <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType> pliki **PKCS # 8** i <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType>pliki **PFX/PKCS # 12** .</span><span class="sxs-lookup"><span data-stu-id="196df-397">**PKCS#8** files can be inspected with <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType> and **PFX/PKCS#12** files can be inspected with <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType>.</span></span> <span data-ttu-id="196df-398">Pliki **PFX/PKCS # 12** można manipulować przy użyciu programu <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="196df-398">**PFX/PKCS#12** files can be manipulated with <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType>.</span></span>

## <a name="serialport-for-linux"></a><span data-ttu-id="196df-399">Klasy SerialPort dla systemu Linux</span><span class="sxs-lookup"><span data-stu-id="196df-399">SerialPort for Linux</span></span>

<span data-ttu-id="196df-400">Program .NET Core 3,0 zapewnia podstawową pomoc <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> techniczną dla systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="196df-400">.NET Core 3.0 provides basic support for <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> on Linux.</span></span>

<span data-ttu-id="196df-401">Wcześniej platforma .NET Core jest obsługiwana `SerialPort` tylko w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="196df-401">Previously, .NET Core only supported using `SerialPort` on Windows.</span></span>

<span data-ttu-id="196df-402">Aby uzyskać więcej informacji o ograniczonej obsłudze portu szeregowego w systemie Linux, zobacz artykuł dotyczący usługi [GitHub #33146](https://github.com/dotnet/corefx/issues/33146).</span><span class="sxs-lookup"><span data-stu-id="196df-402">For more information about the limited support for the serial port on Linux, see [GitHub issue #33146](https://github.com/dotnet/corefx/issues/33146).</span></span>

## <a name="docker-and-cgroup-memory-limits"></a><span data-ttu-id="196df-403">Limity pamięci Docker i cgroup</span><span class="sxs-lookup"><span data-stu-id="196df-403">Docker and cgroup memory Limits</span></span>

<span data-ttu-id="196df-404">Począwszy od wersji zapoznawczej 3, uruchomienie programu .NET Core 3,0 w systemie Linux z rozwiązaniem Docker działa lepiej z limitami pamięci cgroup.</span><span class="sxs-lookup"><span data-stu-id="196df-404">Starting with Preview 3, running .NET Core 3.0 on Linux with Docker works better with cgroup memory limits.</span></span> <span data-ttu-id="196df-405">Uruchamianie kontenera Docker z limitami pamięci, na przykład z `docker run -m`, zmienia sposób działania programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="196df-405">Running a Docker container with memory limits, such as with `docker run -m`, changes how .NET Core behaves.</span></span>

* <span data-ttu-id="196df-406">Domyślny rozmiar sterty modułu wyrzucania elementów bezużytecznych (GC): maksymalnie 20 MB lub 75% limitu pamięci w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="196df-406">Default Garbage Collector (GC) heap size: maximum of 20 mb or 75% of the memory limit on the container.</span></span>
* <span data-ttu-id="196df-407">Rozmiar jawny można ustawić jako liczbę bezwzględną lub procent limitu cgroup.</span><span class="sxs-lookup"><span data-stu-id="196df-407">Explicit size can be set as an absolute number or percentage of cgroup limit.</span></span>
* <span data-ttu-id="196df-408">Minimalny zarezerwowany rozmiar segmentu na stos GC to 16 MB.</span><span class="sxs-lookup"><span data-stu-id="196df-408">Minimum reserved segment size per GC heap is 16 mb.</span></span> <span data-ttu-id="196df-409">Ten rozmiar zmniejsza liczbę stert, które są tworzone na maszynach.</span><span class="sxs-lookup"><span data-stu-id="196df-409">This size reduces the number of heaps that are created on machines.</span></span>

## <a name="smaller-garbage-collection-heap-sizes"></a><span data-ttu-id="196df-410">Mniejsze rozmiary sterty wyrzucania elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="196df-410">Smaller Garbage Collection heap sizes</span></span>

<span data-ttu-id="196df-411">Rozmiar sterty domyślnej modułu wyrzucania elementów bezużytecznych został zmniejszony z powodu mniejszej ilości pamięci w programie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="196df-411">The Garbage Collector's default heap size has been reduced resulting in .NET Core using less memory.</span></span> <span data-ttu-id="196df-412">Ta zmiana jest lepsza w porównaniu z budżetem alokacji generacji 0 z nowoczesnymi rozmiarami pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="196df-412">This change better aligns with the generation 0 allocation budget with modern processor cache sizes.</span></span>

## <a name="garbage-collection-large-page-support"></a><span data-ttu-id="196df-413">Obsługa dużej strony odzyskiwania pamięci</span><span class="sxs-lookup"><span data-stu-id="196df-413">Garbage Collection Large Page support</span></span>

<span data-ttu-id="196df-414">Duże strony (znane również jako ogromne strony w systemie Linux) to funkcja, w której system operacyjny może ustalić obszary pamięci większe niż rozmiar strony natywnej (często 4K), aby zwiększyć wydajność aplikacji żądającej tych dużych stron.</span><span class="sxs-lookup"><span data-stu-id="196df-414">Large Pages (also known as Huge Pages on Linux) is a feature where the operating system is able to establish memory regions larger than the native page size (often 4K) to improve performance of the application requesting these large pages.</span></span>

<span data-ttu-id="196df-415">Moduł wyrzucania elementów bezużytecznych można teraz skonfigurować przy użyciu ustawienia **GCLargePages** jako funkcji wyboru do przydzielania dużych stron w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="196df-415">The Garbage Collector can now be configured with the **GCLargePages** setting as an opt-in feature to choose to allocate large pages on Windows.</span></span>

## <a name="gpio-support-for-raspberry-pi"></a><span data-ttu-id="196df-416">Obsługa interfejsu GPIO dla Raspberry Pi</span><span class="sxs-lookup"><span data-stu-id="196df-416">GPIO Support for Raspberry Pi</span></span>

<span data-ttu-id="196df-417">Do programu NuGet zostały wydane dwa pakiety, których można użyć do programowania interfejsu GPIO:</span><span class="sxs-lookup"><span data-stu-id="196df-417">Two packages have been released to NuGet that you can use for GPIO programming:</span></span>

* [<span data-ttu-id="196df-418">System.Device.Gpio</span><span class="sxs-lookup"><span data-stu-id="196df-418">System.Device.Gpio</span></span>](https://www.nuget.org/packages/System.Device.Gpio)
* [<span data-ttu-id="196df-419">IoT. Device. bindings</span><span class="sxs-lookup"><span data-stu-id="196df-419">Iot.Device.Bindings</span></span>](https://www.nuget.org/packages/Iot.Device.Bindings)

<span data-ttu-id="196df-420">Pakiety GPIO obejmują interfejsy API dla urządzeń z interfejsem *GPIO*, *SPI*, *I2C*i *PWM* .</span><span class="sxs-lookup"><span data-stu-id="196df-420">The GPIO packages include APIs for *GPIO*, *SPI*, *I2C*, and *PWM* devices.</span></span> <span data-ttu-id="196df-421">Pakiet powiązań IoT obejmuje powiązania urządzeń.</span><span class="sxs-lookup"><span data-stu-id="196df-421">The IoT bindings package includes device bindings.</span></span> <span data-ttu-id="196df-422">Aby uzyskać więcej informacji, zobacz [repozytorium GitHub](https://github.com/dotnet/iot/blob/master/src/devices/).</span><span class="sxs-lookup"><span data-stu-id="196df-422">For more information, see the [devices GitHub repo](https://github.com/dotnet/iot/blob/master/src/devices/).</span></span>

## <a name="arm64-linux-support"></a><span data-ttu-id="196df-423">Obsługa systemu Linux ARM64</span><span class="sxs-lookup"><span data-stu-id="196df-423">ARM64 Linux support</span></span>

<span data-ttu-id="196df-424">Program .NET Core 3,0 dodaje obsługę ARM64 dla systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="196df-424">.NET Core 3.0 adds support for ARM64 for Linux.</span></span> <span data-ttu-id="196df-425">Podstawowy przypadek użycia dla ARM64 jest obecnie z scenariuszami IoT.</span><span class="sxs-lookup"><span data-stu-id="196df-425">The primary use case for ARM64 is currently with IoT scenarios.</span></span> <span data-ttu-id="196df-426">Aby uzyskać więcej informacji, zobacz temat [stan arm64 programu .NET Core](https://github.com/dotnet/announcements/issues/82).</span><span class="sxs-lookup"><span data-stu-id="196df-426">For more information, see [.NET Core ARM64 Status](https://github.com/dotnet/announcements/issues/82).</span></span>

<span data-ttu-id="196df-427">[Obrazy Docker dla platformy .NET Core w systemie arm64](https://hub.docker.com/r/microsoft/dotnet/) są dostępne dla Alpine, Debian i Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="196df-427">[Docker images for .NET Core on ARM64](https://hub.docker.com/r/microsoft/dotnet/) are available for Alpine, Debian, and Ubuntu.</span></span>

> [!NOTE]
> <span data-ttu-id="196df-428">**Arm64** Obsługa systemu Windows nie jest jeszcze dostępna.</span><span class="sxs-lookup"><span data-stu-id="196df-428">**ARM64** Windows support isn't yet available.</span></span>

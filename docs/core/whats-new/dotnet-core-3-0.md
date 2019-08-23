---
title: Co nowego w programie .NET Core 3.0
description: Dowiedz się więcej o nowych funkcjach dostępnych w programie .NET Core 3,0.
dev_langs:
- csharp
- vb
author: thraka
ms.author: adegeo
ms.date: 08/21/2019
ms.openlocfilehash: 5f9d7026b270a010d2ba5d4b1165728a100ab6ed
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69922564"
---
# <a name="whats-new-in-net-core-30-preview-8"></a><span data-ttu-id="743fa-103">Co nowego w programie .NET Core 3,0 (wersja zapoznawcza 8)</span><span class="sxs-lookup"><span data-stu-id="743fa-103">What's new in .NET Core 3.0 (Preview 8)</span></span>

<span data-ttu-id="743fa-104">W tym artykule opisano nowości w programie .NET Core 3,0 (w wersji zapoznawczej 8).</span><span class="sxs-lookup"><span data-stu-id="743fa-104">This article describes what is new in .NET Core 3.0 (through preview 8).</span></span> <span data-ttu-id="743fa-105">Jednym z największych ulepszeń jest obsługa aplikacji klasycznych systemu Windows (tylko system Windows).</span><span class="sxs-lookup"><span data-stu-id="743fa-105">One of the biggest enhancements is support for Windows desktop applications (Windows only).</span></span> <span data-ttu-id="743fa-106">Korzystając z pulpitu systemu Windows składnika zestawu SDK platformy .NET Core 3,0, można przenieść aplikacje Windows Forms i Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="743fa-106">By using the .NET Core 3.0 SDK component Windows Desktop, you can port your Windows Forms and Windows Presentation Foundation (WPF) applications.</span></span> <span data-ttu-id="743fa-107">Aby można było wyczyścić, składnik pulpitu systemu Windows jest obsługiwany i uwzględniany w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="743fa-107">To be clear, the Windows Desktop component is only supported and included on Windows.</span></span> <span data-ttu-id="743fa-108">Aby uzyskać więcej informacji, zobacz sekcję [pulpitu systemu Windows](#windows-desktop) w dalszej części tego artykułu.</span><span class="sxs-lookup"><span data-stu-id="743fa-108">For more information, see the [Windows desktop](#windows-desktop) section later in this article.</span></span>

<span data-ttu-id="743fa-109">Program .NET Core 3,0 dodaje obsługę C# 8,0.</span><span class="sxs-lookup"><span data-stu-id="743fa-109">.NET Core 3.0 adds support for C# 8.0.</span></span> <span data-ttu-id="743fa-110">Zdecydowanie zaleca się użycie [najnowszej wersji programu Visual Studio Preview](https://visualstudio.microsoft.com/vs/preview/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+preview)lub Visual Studio Code z rozszerzeniem OmniSharp.</span><span class="sxs-lookup"><span data-stu-id="743fa-110">It's highly recommended that you use the [latest release of Visual Studio Preview](https://visualstudio.microsoft.com/vs/preview/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+preview), or Visual Studio Code with the OmniSharp extension.</span></span>

<span data-ttu-id="743fa-111">[Pobierz i zacznij korzystać z programu .NET Core 3,0 Preview 8](https://aka.ms/netcore3download) teraz w systemie Windows, MacOS lub Linux.</span><span class="sxs-lookup"><span data-stu-id="743fa-111">[Download and get started with .NET Core 3.0 preview 8](https://aka.ms/netcore3download) right now on Windows, macOS, or Linux.</span></span>

<span data-ttu-id="743fa-112">Aby uzyskać więcej informacji na temat każdej wersji zapoznawczej, zobacz następujące powiadomienia:</span><span class="sxs-lookup"><span data-stu-id="743fa-112">For more information about each preview release, see the following announcements:</span></span>

- [<span data-ttu-id="743fa-113">Anons programu .NET Core 3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="743fa-113">.NET Core 3.0 Preview 8 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-8/)
- [<span data-ttu-id="743fa-114">Anons programu .NET Core 3,0 w wersji zapoznawczej 7</span><span class="sxs-lookup"><span data-stu-id="743fa-114">.NET Core 3.0 Preview 7 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-7/)
- [<span data-ttu-id="743fa-115">Anons programu .NET Core 3,0 w wersji 6</span><span class="sxs-lookup"><span data-stu-id="743fa-115">.NET Core 3.0 Preview 6 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-6/)
- [<span data-ttu-id="743fa-116">Anons programu .NET Core 3,0 Preview 5</span><span class="sxs-lookup"><span data-stu-id="743fa-116">.NET Core 3.0 Preview 5 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-5/)
- [<span data-ttu-id="743fa-117">Anons programu .NET Core 3,0 Preview 4</span><span class="sxs-lookup"><span data-stu-id="743fa-117">.NET Core 3.0 Preview 4 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-4/)
- [<span data-ttu-id="743fa-118">Anons programu .NET Core 3,0 Preview 3</span><span class="sxs-lookup"><span data-stu-id="743fa-118">.NET Core 3.0 Preview 3 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-3/)
- [<span data-ttu-id="743fa-119">Anons programu .NET Core 3,0 w wersji zapoznawczej 2</span><span class="sxs-lookup"><span data-stu-id="743fa-119">.NET Core 3.0 Preview 2 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-2/)
- [<span data-ttu-id="743fa-120">Powiadomienie dotyczące programu .NET Core 3,0 Preview 1</span><span class="sxs-lookup"><span data-stu-id="743fa-120">.NET Core 3.0 Preview 1 announcement</span></span>](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-preview-1-and-open-sourcing-windows-desktop-frameworks/)

## <a name="production-supported-preview"></a><span data-ttu-id="743fa-121">Wersja zapoznawcza obsługiwanej produkcji</span><span class="sxs-lookup"><span data-stu-id="743fa-121">Production supported preview</span></span>

<span data-ttu-id="743fa-122">Program .NET Core Preview 8 jest uznawany za gotowy do produkcji przez firmę Microsoft i jest w pełni obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="743fa-122">.NET Core Preview 8 is considered production ready by Microsoft and is fully supported.</span></span> <span data-ttu-id="743fa-123">Począwszy od wersji zapoznawczej 7, wersje będą skoncentrowane na polerowaniu platformy .NET Core 3,0 zamiast dodawania nowych funkcji.</span><span class="sxs-lookup"><span data-stu-id="743fa-123">Starting with preview 7, releases will focus on polishing .NET Core 3.0 instead of adding new features.</span></span> <span data-ttu-id="743fa-124">Aby uzyskać więcej informacji na temat zmian w wersji zapoznawczej 8, zobacz [ogłoszenie w wersji zapoznawczej 8](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-8/).</span><span class="sxs-lookup"><span data-stu-id="743fa-124">For more information about what has changed in preview 8, see the [preview 8 announcement](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0-preview-8/).</span></span>

<span data-ttu-id="743fa-125">Jeśli używasz starszej wersji zapoznawczej, musisz przejść do wersji zapoznawczej 8, aby kontynuować obsługę "go na żywo".</span><span class="sxs-lookup"><span data-stu-id="743fa-125">If you're using a previous preview release, you must move to Preview 8 for continued "Go Live" support.</span></span>

## <a name="net-core-sdk-windows-installer"></a><span data-ttu-id="743fa-126">Zestaw .NET Core SDK Instalator Windows</span><span class="sxs-lookup"><span data-stu-id="743fa-126">.NET Core SDK Windows Installer</span></span>

<span data-ttu-id="743fa-127">Instalator MSI dla systemu Windows został zmieniony począwszy od platformy .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="743fa-127">The MSI installer for Windows has changed starting with .NET Core 3.0.</span></span> <span data-ttu-id="743fa-128">Instalatorzy zestawu SDK teraz uaktualniają wersje funkcji zestawu SDK na miejscu.</span><span class="sxs-lookup"><span data-stu-id="743fa-128">The SDK installers will now upgrade SDK feature-band releases in place.</span></span> <span data-ttu-id="743fa-129">Paski funkcji są zdefiniowane w grupach *setek* w sekcji *poprawka* numeru wersji.</span><span class="sxs-lookup"><span data-stu-id="743fa-129">Feature bands are defined in the *hundreds* groups in the *patch* section of the version number.</span></span> <span data-ttu-id="743fa-130">Na przykład **3,0. _101_**  i **3,0. _201_**  są wersje w dwóch różnych warstwach funkcji podczas **3,0. _101_**  i **3,0. _199_**  znajdują się w tej samej paśmie funkcji.</span><span class="sxs-lookup"><span data-stu-id="743fa-130">For example, **3.0._101_** and **3.0._201_** are versions in two different feature bands while **3.0._101_** and **3.0._199_** are in the same feature band.</span></span> <span data-ttu-id="743fa-131">I, w przypadku zestaw .NET Core SDK **3,0. _101_**  jest zainstalowana, zestaw .NET Core SDK **3,0. _100_**  zostanie usunięta z komputera, jeśli istnieje.</span><span class="sxs-lookup"><span data-stu-id="743fa-131">And, when .NET Core SDK **3.0._101_** is installed, .NET Core SDK **3.0._100_** will be removed from the machine if it exists.</span></span> <span data-ttu-id="743fa-132">Gdy zestaw .NET Core SDK **3,0. _200_**  jest zainstalowana na tym samym komputerze, zestaw .NET Core SDK **3,0. _101_**  nie zostanie usunięta.</span><span class="sxs-lookup"><span data-stu-id="743fa-132">When .NET Core SDK **3.0._200_** is installed on the same machine, .NET Core SDK **3.0._101_** won't be removed.</span></span>

<span data-ttu-id="743fa-133">Aby uzyskać więcej informacji na temat przechowywania wersji, zobacz [Omówienie wersji platformy .NET Core](../versions/index.md).</span><span class="sxs-lookup"><span data-stu-id="743fa-133">For more information about versioning, see [Overview of how .NET Core is versioned](../versions/index.md).</span></span>

## <a name="c-80-preview"></a><span data-ttu-id="743fa-134">C#wersja zapoznawcza 8,0</span><span class="sxs-lookup"><span data-stu-id="743fa-134">C# 8.0 preview</span></span>

<span data-ttu-id="743fa-135">Program .NET Core 3,0 C# obsługuje 8 wersji zapoznawczych.</span><span class="sxs-lookup"><span data-stu-id="743fa-135">.NET Core 3.0 supports C# 8 preview.</span></span> <span data-ttu-id="743fa-136">Aby uzyskać więcej informacji C# o funkcjach 8,0, zobacz [co nowego C# w programie 8,0](../../csharp/whats-new/csharp-8.md).</span><span class="sxs-lookup"><span data-stu-id="743fa-136">For more information about C# 8.0 features, see [What's new in C# 8.0](../../csharp/whats-new/csharp-8.md).</span></span>

## <a name="net-standard-21"></a><span data-ttu-id="743fa-137">.NET Standard 2,1</span><span class="sxs-lookup"><span data-stu-id="743fa-137">.NET Standard 2.1</span></span>

<span data-ttu-id="743fa-138">Mimo że program .NET Core 3,0 obsługuje **.NET Standard 2,1**, szablon `dotnet new classlib` domyślny generuje projekt, który jest przeznaczony dla **.NET Standard 2,0**.</span><span class="sxs-lookup"><span data-stu-id="743fa-138">Even though .NET Core 3.0 supports **.NET Standard 2.1**, the default `dotnet new classlib` template generates a project that targets **.NET Standard 2.0**.</span></span> <span data-ttu-id="743fa-139">Aby docelowa **.NET Standard 2,1**, edytuj plik projektu i Zmień `TargetFramework` właściwość na `netstandard2.1`:</span><span class="sxs-lookup"><span data-stu-id="743fa-139">To target **.NET Standard 2.1**, edit your project file and change the `TargetFramework` property to `netstandard2.1`:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard2.1</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="743fa-140">Jeśli używasz programu Visual Studio, potrzebujesz [programu Visual studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), ponieważ program visual Studio 2017 nie obsługuje **.NET Standard 2,1** ani **.NET Core 3,0**.</span><span class="sxs-lookup"><span data-stu-id="743fa-140">If you're using Visual Studio, you need [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), as Visual Studio 2017 doesn't support **.NET Standard 2.1** or **.NET Core 3.0**.</span></span>

## <a name="improved-net-core-version-apis"></a><span data-ttu-id="743fa-141">Ulepszone interfejsy API wersji platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="743fa-141">Improved .NET Core Version APIs</span></span>

<span data-ttu-id="743fa-142">Począwszy od platformy .NET Core 3,0, interfejsy API wersji dostarczone z platformą .NET Core teraz zwracają oczekiwane informacje.</span><span class="sxs-lookup"><span data-stu-id="743fa-142">Starting with .NET Core 3.0, the version APIs provided with .NET Core now return the information you expect.</span></span> <span data-ttu-id="743fa-143">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="743fa-143">For example:</span></span>

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
> <span data-ttu-id="743fa-144">Istotna zmiana.</span><span class="sxs-lookup"><span data-stu-id="743fa-144">Breaking change.</span></span> <span data-ttu-id="743fa-145">Jest to technicznie istotna zmiana, ponieważ schemat przechowywania wersji został zmieniony.</span><span class="sxs-lookup"><span data-stu-id="743fa-145">This is technically a breaking change because the versioning scheme has changed.</span></span>

## <a name="net-platform-dependent-intrinsics"></a><span data-ttu-id="743fa-146">Elementy wewnętrzne zależne od platformy .NET</span><span class="sxs-lookup"><span data-stu-id="743fa-146">.NET Platform-Dependent Intrinsics</span></span>

<span data-ttu-id="743fa-147">Dodano interfejsy API, które umożliwiają dostęp do pewnych instrukcji procesora CPU zorientowanych na wydajność, takich jak **SIMD** lub **bitowe zestawy instrukcji manipulowania** .</span><span class="sxs-lookup"><span data-stu-id="743fa-147">APIs have been added that allow access to certain perf-oriented CPU instructions, such as the **SIMD** or **Bit Manipulation instruction** sets.</span></span> <span data-ttu-id="743fa-148">Te instrukcje mogą pomóc w osiągnięciu znaczących ulepszeń wydajności w niektórych scenariuszach, takich jak wydajne przetwarzanie danych.</span><span class="sxs-lookup"><span data-stu-id="743fa-148">These instructions can help achieve significant performance improvements in certain scenarios, such as processing data efficiently in parallel.</span></span>

<span data-ttu-id="743fa-149">W odpowiednich przypadkach biblioteki .NET zaczęły korzystać z tych instrukcji w celu zwiększenia wydajności.</span><span class="sxs-lookup"><span data-stu-id="743fa-149">Where appropriate, the .NET libraries have begun using these instructions to improve performance.</span></span>

<span data-ttu-id="743fa-150">Aby uzyskać więcej informacji, zobacz elementy [wewnętrzne zależne od platformy .NET](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md).</span><span class="sxs-lookup"><span data-stu-id="743fa-150">For more information, see [.NET Platform Dependent Intrinsics](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md).</span></span>

## <a name="default-executables"></a><span data-ttu-id="743fa-151">Domyślne pliki wykonywalne</span><span class="sxs-lookup"><span data-stu-id="743fa-151">Default executables</span></span>

<span data-ttu-id="743fa-152">Platforma .NET Core teraz domyślnie kompiluje [pliki wykonywalne zależne od platformy](../deploying/index.md#framework-dependent-executables-fde) .</span><span class="sxs-lookup"><span data-stu-id="743fa-152">.NET Core now builds [framework-dependent executables](../deploying/index.md#framework-dependent-executables-fde) by default.</span></span> <span data-ttu-id="743fa-153">To zachowanie jest nowe w przypadku aplikacji korzystających z zainstalowanej globalnie wersji platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="743fa-153">This behavior is new for applications that use a globally installed version of .NET Core.</span></span> <span data-ttu-id="743fa-154">Wcześniej tylko [wstępnie zawarte wdrożenia](../deploying/index.md#self-contained-deployments-scd) spowodują utworzenie pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="743fa-154">Previously, only [self-contained deployments](../deploying/index.md#self-contained-deployments-scd) would produce an executable.</span></span>

<span data-ttu-id="743fa-155">W `dotnet build` trakcie `dotnet publish`lub, tworzony jest plik wykonywalny zgodny ze środowiskiem i platformą używanego zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="743fa-155">During `dotnet build` or `dotnet publish`, an executable is created that matches the environment and platform of the SDK you're using.</span></span> <span data-ttu-id="743fa-156">Można oczekiwać, że te same elementy wykonywalne są takie same jak w przypadku innych natywnych plików wykonywalnych, takich jak:</span><span class="sxs-lookup"><span data-stu-id="743fa-156">You can expect the same things with these executables as you would other native executables, such as:</span></span>

- <span data-ttu-id="743fa-157">Możesz kliknąć dwukrotnie plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="743fa-157">You can double-click on the executable.</span></span>
- <span data-ttu-id="743fa-158">Aplikację można uruchomić z poziomu wiersza polecenia bezpośrednio, na przykład `myapp.exe` w systemie Windows `./myapp` , w systemie Linux i macOS.</span><span class="sxs-lookup"><span data-stu-id="743fa-158">You can launch the application from a command prompt directly, such as `myapp.exe` on Windows, and `./myapp` on Linux and macOS.</span></span>

## <a name="single-file-executables"></a><span data-ttu-id="743fa-159">Pliki wykonywalne pojedynczego pliku</span><span class="sxs-lookup"><span data-stu-id="743fa-159">Single-file executables</span></span>

<span data-ttu-id="743fa-160">`dotnet publish` Polecenie obsługuje pakowanie aplikacji do pliku wykonywalnego określonego dla konkretnej platformy.</span><span class="sxs-lookup"><span data-stu-id="743fa-160">The `dotnet publish` command supports packaging your app into a platform-specific single-file executable.</span></span> <span data-ttu-id="743fa-161">Plik wykonywalny jest samowyodrębniający się i zawiera wszystkie zależności (w tym natywne) wymagane do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="743fa-161">The executable is self-extracting and contains all dependencies (including native) that are required to run your app.</span></span> <span data-ttu-id="743fa-162">Gdy aplikacja jest uruchamiana po raz pierwszy, aplikacja zostanie wyodrębniona do katalogu na podstawie nazwy aplikacji i identyfikatora kompilacji.</span><span class="sxs-lookup"><span data-stu-id="743fa-162">When the app is first run, the application is extracted to a directory based on the app name and build identifier.</span></span> <span data-ttu-id="743fa-163">Uruchamianie jest szybsze, gdy aplikacja jest uruchamiana ponownie.</span><span class="sxs-lookup"><span data-stu-id="743fa-163">Startup is faster when the application is run again.</span></span> <span data-ttu-id="743fa-164">Aplikacja nie musi wyodrębniać siebie po raz drugi, chyba że została użyta Nowa wersja.</span><span class="sxs-lookup"><span data-stu-id="743fa-164">The application doesn't need to extract itself a second time unless a new version was used.</span></span>

<span data-ttu-id="743fa-165">Aby opublikować plik wykonywalny pojedynczego pliku, ustaw `PublishSingleFile` w projekcie lub w wierszu `dotnet publish` polecenia polecenie:</span><span class="sxs-lookup"><span data-stu-id="743fa-165">To publish a single-file executable, set the `PublishSingleFile` in your project or on the command line with the `dotnet publish` command:</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifier>win10-x64</RuntimeIdentifier>
  <PublishSingleFile>true</PublishSingleFile>
</PropertyGroup>
```

<span data-ttu-id="743fa-166">—lub—</span><span class="sxs-lookup"><span data-stu-id="743fa-166">-or-</span></span>

```console
dotnet publish -r win10-x64 /p:PublishSingleFile=true
```

<span data-ttu-id="743fa-167">Aby uzyskać więcej informacji o publikowaniu jednoplikowym, zapoznaj się z [dokumentem projektu pakietu pojedynczego pliku](https://github.com/dotnet/designs/blob/master/accepted/single-file/design.md).</span><span class="sxs-lookup"><span data-stu-id="743fa-167">For more information about single-file publishing, see the [single-file bundler design document](https://github.com/dotnet/designs/blob/master/accepted/single-file/design.md).</span></span>

## <a name="assembly-linking"></a><span data-ttu-id="743fa-168">Łączenie zestawów</span><span class="sxs-lookup"><span data-stu-id="743fa-168">Assembly linking</span></span>

<span data-ttu-id="743fa-169">Zestaw SDK platformy .NET Core 3,0 zawiera narzędzie, które pozwala zmniejszyć rozmiar aplikacji przez analizowanie IL i przycinanie nieużywanych zestawów.</span><span class="sxs-lookup"><span data-stu-id="743fa-169">The .NET core 3.0 SDK comes with a tool that can reduce the size of apps by analyzing IL and trimming unused assemblies.</span></span>

<span data-ttu-id="743fa-170">Aplikacje samodzielne obejmują wszystko, co jest potrzebne do uruchomienia kodu, bez konieczności instalowania programu .NET na komputerze-hoście.</span><span class="sxs-lookup"><span data-stu-id="743fa-170">Self-contained apps include everything needed to run your code, without requiring .NET to be installed on the host computer.</span></span> <span data-ttu-id="743fa-171">Jednak wiele razy aplikacja wymaga tylko małego podzestawu platformy do działania, a inne nieużywane biblioteki mogą zostać usunięte.</span><span class="sxs-lookup"><span data-stu-id="743fa-171">However, many times the app only requires a small subset of the framework to function, and other unused libraries could be removed.</span></span>

<span data-ttu-id="743fa-172">Platforma .NET Core zawiera teraz ustawienie, które będzie używać narzędzia [konsolidatora Il](https://github.com/mono/linker) do skanowania Il aplikacji.</span><span class="sxs-lookup"><span data-stu-id="743fa-172">.NET Core now includes a setting that will use the [IL linker](https://github.com/mono/linker) tool to scan the IL of your app.</span></span> <span data-ttu-id="743fa-173">to narzędzie wykrywa wymagany kod, a następnie przycina nieużywane biblioteki.</span><span class="sxs-lookup"><span data-stu-id="743fa-173">this tool detects what code is required, and then trims unused libraries.</span></span> <span data-ttu-id="743fa-174">To narzędzie może znacznie zmniejszyć rozmiar wdrożenia niektórych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="743fa-174">This tool can significantly reduce the deployment size of some apps.</span></span>

<span data-ttu-id="743fa-175">Aby włączyć to narzędzie, Dodaj `<PublishTrimmed>` ustawienie w projekcie i Opublikuj samodzielną aplikację:</span><span class="sxs-lookup"><span data-stu-id="743fa-175">To enable this tool, add the `<PublishTrimmed>` setting in your project and publish a self-contained app:</span></span>

```xml
<PropertyGroup>
  <PublishTrimmed>true</PublishTrimmed>
</PropertyGroup>
```

```console
dotnet publish -r <rid> -c Release
```

<span data-ttu-id="743fa-176">Na przykład podstawowy "Hello World" nowy szablon projektu konsoli, który jest dostępny po opublikowaniu, trafień o rozmiarze 70 MB.</span><span class="sxs-lookup"><span data-stu-id="743fa-176">As an example, the basic "hello world" new console project template that is included, when published, hits about 70 MB in size.</span></span> <span data-ttu-id="743fa-177">Przy użyciu `<PublishTrimmed>`, ten rozmiar jest zmniejszany do około 30 MB.</span><span class="sxs-lookup"><span data-stu-id="743fa-177">By using `<PublishTrimmed>`, that size is reduced to about 30 MB.</span></span>

<span data-ttu-id="743fa-178">Należy wziąć pod uwagę, że aplikacje lub struktury (w tym ASP.NET Core i WPF), które wykorzystują odbicie lub powiązane funkcje dynamiczne, często będą przerywane po przycięciu.</span><span class="sxs-lookup"><span data-stu-id="743fa-178">It's important to consider that applications or frameworks (including ASP.NET Core and WPF) that use reflection or related dynamic features, will often break when trimmed.</span></span> <span data-ttu-id="743fa-179">To uszkodzenie występuje, ponieważ konsolidator nie wie o tym zachowaniu dynamicznym i nie może określić, które typy struktur są wymagane do odbicia.</span><span class="sxs-lookup"><span data-stu-id="743fa-179">This breakage occurs because the linker doesn't know about this dynamic behavior and can't determine which framework types are required for reflection.</span></span> <span data-ttu-id="743fa-180">Narzędzie konsolidatora IL można skonfigurować pod kątem tego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="743fa-180">The IL Linker tool can be configured to be aware of this scenario.</span></span>

<span data-ttu-id="743fa-181">Przed przycinaniem upewnij się, że aplikacja została przetestowana.</span><span class="sxs-lookup"><span data-stu-id="743fa-181">Above all else, be sure to test your app after trimming.</span></span>

<span data-ttu-id="743fa-182">Aby uzyskać więcej informacji na temat narzędzia konsolidatora IL, zapoznaj się z [dokumentacją](https://aka.ms/dotnet-illink) lub odwiedź repozytorium [mono/konsolidatora]( https://github.com/mono/linker) .</span><span class="sxs-lookup"><span data-stu-id="743fa-182">For more information about the IL Linker tool, see the [documentation](https://aka.ms/dotnet-illink) or visit the [mono/linker]( https://github.com/mono/linker) repo.</span></span>

## <a name="tiered-compilation"></a><span data-ttu-id="743fa-183">Kompilacja warstwowa</span><span class="sxs-lookup"><span data-stu-id="743fa-183">Tiered compilation</span></span>

<span data-ttu-id="743fa-184">[Kompilacja warstwowa](https://devblogs.microsoft.com/dotnet/tiered-compilation-preview-in-net-core-2-1/) (TC) jest domyślnie włączona z platformą .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="743fa-184">[Tiered compilation](https://devblogs.microsoft.com/dotnet/tiered-compilation-preview-in-net-core-2-1/) (TC) is on by default with .NET Core 3.0.</span></span> <span data-ttu-id="743fa-185">Ta funkcja umożliwia środowisku uruchomieniowemu wydajniejsze używanie kompilatora just-in-Time (JIT) w celu uzyskania lepszej wydajności.</span><span class="sxs-lookup"><span data-stu-id="743fa-185">This feature enables the runtime to more adaptively use the Just-In-Time (JIT) compiler to get better performance.</span></span>

<span data-ttu-id="743fa-186">Główną zaletą TC jest włączenie (re-) metod jitting z niską jakością, ale szybszym lub wyższą warstwą.</span><span class="sxs-lookup"><span data-stu-id="743fa-186">The main benefit of TC is to enable (re-)jitting methods with a lower-quality-but-faster tier or a higher-quality-but-slower tier.</span></span> <span data-ttu-id="743fa-187">Pozwala to zwiększyć wydajność aplikacji, która przechodzi przez różne etapy wykonywania, od uruchamiania do stanu stałego.</span><span class="sxs-lookup"><span data-stu-id="743fa-187">This helps increase performance of an application as it goes through various stages of execution, from startup through steady-state.</span></span> <span data-ttu-id="743fa-188">Jest to kontrast z podejściem innym niż TC, gdzie każda metoda jest skompilowana w jeden sposób (taka sama jak warstwa wysokiej jakości), która jest obciążona niestabilnym stanem w porównaniu z wydajnością uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="743fa-188">This contrasts with the non-TC approach, where every method is compiled a single way (the same as the high-quality tier), which is biased to steady-state over startup performance.</span></span>

<span data-ttu-id="743fa-189">Aby włączyć funkcję szybkiego JIT (kod 0 trybie JIT), użyj tego ustawienia w pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="743fa-189">To enable Quick JIT (tier 0 jitted code), use this setting in your project file:</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>true</TieredCompilationQuickJit>
</PropertyGroup>
```

<span data-ttu-id="743fa-190">Aby całkowicie wyłączyć TC, użyj tego ustawienia w pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="743fa-190">To disable TC completely, use this setting in your project file:</span></span>

```xml
<TieredCompilation>false</TieredCompilation>
```

## <a name="readytorun-images"></a><span data-ttu-id="743fa-191">Obrazy ReadyToRun</span><span class="sxs-lookup"><span data-stu-id="743fa-191">ReadyToRun images</span></span>

<span data-ttu-id="743fa-192">Można skrócić czas uruchamiania aplikacji .NET Core, kompilując zestawy aplikacji jako ReadyToRun (R2R).</span><span class="sxs-lookup"><span data-stu-id="743fa-192">You can improve the startup time of your .NET Core application by compiling your application assemblies as ReadyToRun (R2R) format.</span></span> <span data-ttu-id="743fa-193">R2R to forma kompilacji z wyprzedzeniem (AOT).</span><span class="sxs-lookup"><span data-stu-id="743fa-193">R2R is a form of ahead-of-time (AOT) compilation.</span></span>

<span data-ttu-id="743fa-194">Pliki binarne R2R zwiększają wydajność uruchamiania przez zmniejszenie ilości pracy kompilatora, który jest potrzebny do załadowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="743fa-194">R2R binaries improve startup performance by reducing the amount of work the just-in-time (JIT) compiler needs to do as your application loads.</span></span> <span data-ttu-id="743fa-195">Pliki binarne zawierają podobny kod natywny w porównaniu z przeznaczeniem JIT.</span><span class="sxs-lookup"><span data-stu-id="743fa-195">The binaries contain similar native code compared to what the JIT would produce.</span></span> <span data-ttu-id="743fa-196">R2R pliki binarne są jednak większe, ponieważ zawierają kod języka pośredniego (IL), który jest nadal wymagany w niektórych scenariuszach i natywną wersję tego samego kodu.</span><span class="sxs-lookup"><span data-stu-id="743fa-196">However, R2R binaries are larger because they contain both intermediate language (IL) code, which is still needed for some scenarios, and the native version of the same code.</span></span> <span data-ttu-id="743fa-197">R2R jest dostępna tylko w przypadku publikowania aplikacji samodzielnej, która jest przeznaczona dla określonych środowisk uruchomieniowych (RID), takich jak Linux x64 lub Windows x64.</span><span class="sxs-lookup"><span data-stu-id="743fa-197">R2R is only available when you publish a self-contained app that targets specific runtime environments (RID) such as Linux x64 or Windows x64.</span></span>

<span data-ttu-id="743fa-198">Aby skompilować projekt jako ReadyToRun, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="743fa-198">To compile your project as ReadyToRun, do the following:</span></span>

01. <span data-ttu-id="743fa-199">`<PublishReadyToRun>` Dodaj ustawienie do projektu</span><span class="sxs-lookup"><span data-stu-id="743fa-199">Add the `<PublishReadyToRun>` setting to your project</span></span>

    ```xml
    <PropertyGroup>
      <PublishReadyToRun>true</PublishReadyToRun>
    </PropertyGroup>
    ```

01. <span data-ttu-id="743fa-200">Publikowanie aplikacji samodzielnej.</span><span class="sxs-lookup"><span data-stu-id="743fa-200">Publish a self-contained app.</span></span> <span data-ttu-id="743fa-201">Na przykład to polecenie tworzy samodzielną aplikację dla 64-bitowej wersji systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="743fa-201">For example, this command creates a self-contained app for the 64-bit version of Windows:</span></span>

    ```console
    dotnet publish -c Release -r win-x64 --self-contained true
    ```

### <a name="cross-platformarchitecture-restrictions"></a><span data-ttu-id="743fa-202">Ograniczenia dotyczące wielu platform/architektury</span><span class="sxs-lookup"><span data-stu-id="743fa-202">Cross platform/architecture restrictions</span></span>

<span data-ttu-id="743fa-203">Kompilator ReadyToRun nie obsługuje obecnie określania wartości docelowej.</span><span class="sxs-lookup"><span data-stu-id="743fa-203">The ReadyToRun compiler doesn't currently support cross-targeting.</span></span> <span data-ttu-id="743fa-204">Należy skompilować na danym miejscu docelowym.</span><span class="sxs-lookup"><span data-stu-id="743fa-204">You must compile on a given target.</span></span> <span data-ttu-id="743fa-205">Na przykład jeśli chcesz, aby obrazy R2R dla systemu Windows x64 zostały wykonane, należy uruchomić polecenie Publikuj w tym środowisku.</span><span class="sxs-lookup"><span data-stu-id="743fa-205">For example, if you want R2R images for Windows x64, you need to run the publish command on that environment.</span></span>

<span data-ttu-id="743fa-206">Wyjątki dla wielu elementów docelowych:</span><span class="sxs-lookup"><span data-stu-id="743fa-206">Exceptions to cross-targeting:</span></span>

- <span data-ttu-id="743fa-207">System Windows x64 może służyć do kompilowania obrazów systemów Windows ARM32, ARM64 i x86.</span><span class="sxs-lookup"><span data-stu-id="743fa-207">Windows x64 can be used to compile Windows ARM32, ARM64, and x86 images.</span></span>
- <span data-ttu-id="743fa-208">System Windows x86 może służyć do kompilowania obrazów ARM32 systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="743fa-208">Windows x86 can be used to compile Windows ARM32 images.</span></span>
- <span data-ttu-id="743fa-209">System Linux x64 może służyć do kompilowania obrazów systemu Linux ARM32 i ARM64.</span><span class="sxs-lookup"><span data-stu-id="743fa-209">Linux x64 can be used to compile Linux ARM32 and ARM64 images.</span></span>

## <a name="build-copies-dependencies"></a><span data-ttu-id="743fa-210">Zależności kompilacji kopii</span><span class="sxs-lookup"><span data-stu-id="743fa-210">Build copies dependencies</span></span>

<span data-ttu-id="743fa-211">`dotnet build` Polecenie teraz kopiuje zależności NuGet dla aplikacji z pamięci podręcznej NuGet do folderu danych wyjściowych kompilacji.</span><span class="sxs-lookup"><span data-stu-id="743fa-211">The `dotnet build` command now copies NuGet dependencies for your application from the NuGet cache to the build output folder.</span></span> <span data-ttu-id="743fa-212">Wcześniej zależności były kopiowane tylko w ramach programu `dotnet publish`.</span><span class="sxs-lookup"><span data-stu-id="743fa-212">Previously, dependencies were only copied as part of `dotnet publish`.</span></span>

<span data-ttu-id="743fa-213">Istnieją pewne operacje, takie jak łączenie i publikowanie stron Razor, które nadal wymagają publikacji.</span><span class="sxs-lookup"><span data-stu-id="743fa-213">There are some operations, like linking and razor page publishing that will still require publishing.</span></span>

## <a name="local-tools"></a><span data-ttu-id="743fa-214">Narzędzia lokalne</span><span class="sxs-lookup"><span data-stu-id="743fa-214">Local tools</span></span>

<span data-ttu-id="743fa-215">Środowisko .NET Core 3,0 zawiera wprowadzenie do narzędzi lokalnych.</span><span class="sxs-lookup"><span data-stu-id="743fa-215">.NET Core 3.0 introduces local tools.</span></span> <span data-ttu-id="743fa-216">Narzędzia lokalne są podobne do [narzędzi globalnych](../tools/global-tools.md) , ale są skojarzone z konkretną lokalizacją na dysku.</span><span class="sxs-lookup"><span data-stu-id="743fa-216">Local tools are similar to [global tools](../tools/global-tools.md) but are associated with a particular location on disk.</span></span> <span data-ttu-id="743fa-217">Narzędzia lokalne nie są dostępne globalnie i są dystrybuowane jako pakiety NuGet.</span><span class="sxs-lookup"><span data-stu-id="743fa-217">Local tools aren't available globally and are distributed as NuGet packages.</span></span>

> [!WARNING]
> <span data-ttu-id="743fa-218">Jeśli podjęto próbę skorzystania z narzędzi lokalnych w programie .NET Core 3,0 `dotnet tool restore` w `dotnet tool install`wersji zapoznawczej 1, takiej jak uruchamianie lub, Usuń folder pamięci podręcznej narzędzi lokalnych</span><span class="sxs-lookup"><span data-stu-id="743fa-218">If you tried local tools in .NET Core 3.0 Preview 1, such as running `dotnet tool restore` or `dotnet tool install`, delete the local tools cache folder.</span></span> <span data-ttu-id="743fa-219">W przeciwnym razie narzędzia lokalne nie będą działały w żadnej nowszej wersji.</span><span class="sxs-lookup"><span data-stu-id="743fa-219">Otherwise, local tools won't work on any newer release.</span></span> <span data-ttu-id="743fa-220">Ten folder znajduje się w lokalizacji:</span><span class="sxs-lookup"><span data-stu-id="743fa-220">This folder is located at:</span></span>
>
> <span data-ttu-id="743fa-221">W systemie macOS, Linux:`rm -r $HOME/.dotnet/toolResolverCache`</span><span class="sxs-lookup"><span data-stu-id="743fa-221">On macOS, Linux: `rm -r $HOME/.dotnet/toolResolverCache`</span></span>
>
> <span data-ttu-id="743fa-222">W systemie Windows:`rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`</span><span class="sxs-lookup"><span data-stu-id="743fa-222">On Windows: `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`</span></span>

<span data-ttu-id="743fa-223">Narzędzia lokalne są zależne od nazwy `dotnet-tools.json` pliku manifestu w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="743fa-223">Local tools rely on a manifest file name `dotnet-tools.json` in your current directory.</span></span> <span data-ttu-id="743fa-224">Ten plik manifestu definiuje narzędzia do udostępnienia w tym folderze i poniżej.</span><span class="sxs-lookup"><span data-stu-id="743fa-224">This manifest file defines the tools to be available at that folder and below.</span></span> <span data-ttu-id="743fa-225">Plik manifestu można dystrybuować z kodem, aby upewnić się, że każda osoba, która współpracuje z kodem, będzie mogła przywrócić i korzystać z tych samych narzędzi.</span><span class="sxs-lookup"><span data-stu-id="743fa-225">You can distribute the manifest file with your code to ensure that anyone who works with your code can restore and use the same tools.</span></span>

<span data-ttu-id="743fa-226">W przypadku narzędzi globalnych i lokalnych wymagana jest zgodna wersja środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="743fa-226">For both global and local tools, a compatible version of the runtime is required.</span></span> <span data-ttu-id="743fa-227">Wiele narzędzi obecnie na NuGet.org docelowym środowiska uruchomieniowego .NET Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="743fa-227">Many tools currently on NuGet.org target .NET Core Runtime 2.1.</span></span> <span data-ttu-id="743fa-228">Aby zainstalować te narzędzia globalnie lub lokalnie, nadal trzeba zainstalować [środowisko uruchomieniowe NET Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="743fa-228">To install these tools globally or locally, you would still need to install the [NET Core 2.1 Runtime](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span>

## <a name="major-version-roll-forward"></a><span data-ttu-id="743fa-229">Wersja główna — przekazanie do przodu</span><span class="sxs-lookup"><span data-stu-id="743fa-229">Major-version Roll Forward</span></span>

<span data-ttu-id="743fa-230">W programie .NET Core 3,0 wprowadzono funkcję wyboru, która pozwala aplikacji na przewinięcie do najnowszej wersji programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="743fa-230">.NET Core 3.0 introduces an opt-in feature that allows your app to roll forward to the latest major version of .NET Core.</span></span> <span data-ttu-id="743fa-231">Ponadto zostało dodane nowe ustawienie służące do kontrolowania sposobu, w jaki przenoszone do przodu jest stosowane do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="743fa-231">Additionally, a new setting has been added to control how roll forward is applied to your app.</span></span> <span data-ttu-id="743fa-232">Tę konfigurację można skonfigurować w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="743fa-232">This can be configured in the following ways:</span></span>

- <span data-ttu-id="743fa-233">Właściwość pliku projektu:`RollForward`</span><span class="sxs-lookup"><span data-stu-id="743fa-233">Project file property: `RollForward`</span></span>
- <span data-ttu-id="743fa-234">Właściwość pliku konfiguracji środowiska uruchomieniowego:`rollForward`</span><span class="sxs-lookup"><span data-stu-id="743fa-234">Runtime configuration file property: `rollForward`</span></span>
- <span data-ttu-id="743fa-235">Zmienna środowiskowa:`DOTNET_ROLL_FORWARD`</span><span class="sxs-lookup"><span data-stu-id="743fa-235">Environment variable: `DOTNET_ROLL_FORWARD`</span></span>
- <span data-ttu-id="743fa-236">Argument wiersza polecenia:`--roll-forward`</span><span class="sxs-lookup"><span data-stu-id="743fa-236">Command-line argument: `--roll-forward`</span></span>

<span data-ttu-id="743fa-237">Należy określić jedną z następujących wartości.</span><span class="sxs-lookup"><span data-stu-id="743fa-237">One of the following values must be specified.</span></span> <span data-ttu-id="743fa-238">Jeśli ustawienie zostanie pominięte, wartością domyślną jest wartość pomocnicza.</span><span class="sxs-lookup"><span data-stu-id="743fa-238">If the setting is omitted, **Minor** is the default.</span></span>

- <span data-ttu-id="743fa-239">**LatestPatch**</span><span class="sxs-lookup"><span data-stu-id="743fa-239">**LatestPatch**</span></span>\
<span data-ttu-id="743fa-240">Przewinięcie do najwyższej wersji poprawki.</span><span class="sxs-lookup"><span data-stu-id="743fa-240">Roll forward to the highest patch version.</span></span> <span data-ttu-id="743fa-241">Spowoduje to wyłączenie wycofywania wersji pomocniczej.</span><span class="sxs-lookup"><span data-stu-id="743fa-241">This disables minor version roll forward.</span></span>
- <span data-ttu-id="743fa-242">**Średni**</span><span class="sxs-lookup"><span data-stu-id="743fa-242">**Minor**</span></span>\
<span data-ttu-id="743fa-243">Przewinięcie do najmniejszej wyższej wersji pomocniczej, jeśli brakuje wymaganej wersji pomocniczej.</span><span class="sxs-lookup"><span data-stu-id="743fa-243">Roll forward to the lowest higher minor version, if requested minor version is missing.</span></span> <span data-ttu-id="743fa-244">Jeśli jest obecna żądana wersja pomocnicza, zostaną użyte zasady **LatestPatch** .</span><span class="sxs-lookup"><span data-stu-id="743fa-244">If the requested minor version is present, then the **LatestPatch** policy is used.</span></span>
- <span data-ttu-id="743fa-245">**Znaczny**</span><span class="sxs-lookup"><span data-stu-id="743fa-245">**Major**</span></span>\
<span data-ttu-id="743fa-246">Zaczekaj na najmniejszą wyższą wersję główną i najniższą wersję pomocniczą, jeśli brakuje żądanej wersji głównej.</span><span class="sxs-lookup"><span data-stu-id="743fa-246">Roll forward to lowest higher major version, and lowest minor version, if requested major version is missing.</span></span> <span data-ttu-id="743fa-247">Jeśli jest obecna żądana wersja główna, są używane zasady pomocnicze.</span><span class="sxs-lookup"><span data-stu-id="743fa-247">If the requested major version is present, then the **Minor** policy is used.</span></span>
- <span data-ttu-id="743fa-248">**LatestMinor**</span><span class="sxs-lookup"><span data-stu-id="743fa-248">**LatestMinor**</span></span>\
<span data-ttu-id="743fa-249">Przewinięcie do przodu do najwyższej wersji pomocniczej, nawet jeśli jest obecna żądana wersja pomocnicza.</span><span class="sxs-lookup"><span data-stu-id="743fa-249">Roll forward to highest minor version, even if requested minor version is present.</span></span> <span data-ttu-id="743fa-250">Przeznaczone do scenariuszy hostingu składników.</span><span class="sxs-lookup"><span data-stu-id="743fa-250">Intended for component hosting scenarios.</span></span>
- <span data-ttu-id="743fa-251">**LatestMajor**</span><span class="sxs-lookup"><span data-stu-id="743fa-251">**LatestMajor**</span></span>\
<span data-ttu-id="743fa-252">Przewinięcie do przodu do najwyższej głównej i najwyższej wersji pomocniczej, nawet jeśli jest obecny żądany główny.</span><span class="sxs-lookup"><span data-stu-id="743fa-252">Roll forward to highest major and highest minor version, even if requested major is present.</span></span> <span data-ttu-id="743fa-253">Przeznaczone do scenariuszy hostingu składników.</span><span class="sxs-lookup"><span data-stu-id="743fa-253">Intended for component hosting scenarios.</span></span>
- <span data-ttu-id="743fa-254">**Wyłącza**</span><span class="sxs-lookup"><span data-stu-id="743fa-254">**Disable**</span></span>\
<span data-ttu-id="743fa-255">Nie przetaczaj dalej.</span><span class="sxs-lookup"><span data-stu-id="743fa-255">Don't roll forward.</span></span> <span data-ttu-id="743fa-256">Powiąż tylko z określoną wersją.</span><span class="sxs-lookup"><span data-stu-id="743fa-256">Only bind to specified version.</span></span> <span data-ttu-id="743fa-257">Te zasady nie są zalecane do użytku ogólnego, ponieważ uniemożliwiają one przekazanie do najnowszych poprawek.</span><span class="sxs-lookup"><span data-stu-id="743fa-257">This policy isn't recommended for general use because it disables the ability to roll forward to the latest patches.</span></span> <span data-ttu-id="743fa-258">Ta wartość jest zalecana tylko do celów testowych.</span><span class="sxs-lookup"><span data-stu-id="743fa-258">This value is only recommended for testing.</span></span>

<span data-ttu-id="743fa-259">Oprócz ustawienia **Wyłącz** wszystkie ustawienia będą używać najwyższej dostępnej wersji poprawki.</span><span class="sxs-lookup"><span data-stu-id="743fa-259">Besides the **Disable** setting, all settings will use the highest available patch version.</span></span>

## <a name="windows-desktop"></a><span data-ttu-id="743fa-260">Pulpit systemu Windows</span><span class="sxs-lookup"><span data-stu-id="743fa-260">Windows desktop</span></span>

<span data-ttu-id="743fa-261">Program .NET Core 3,0 obsługuje aplikacje klasyczne systemu Windows przy użyciu Windows Presentation Foundation (WPF) i Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="743fa-261">.NET Core 3.0 supports Windows desktop applications using Windows Presentation Foundation (WPF) and Windows Forms.</span></span> <span data-ttu-id="743fa-262">Te struktury obsługują również korzystanie z nowoczesnych kontrolek i stylów Fluent z poziomu biblioteki XAML interfejsu użytkownika systemu Windows (WinUI) za pośrednictwem [wysp XAML](/windows/uwp/xaml-platform/xaml-host-controls).</span><span class="sxs-lookup"><span data-stu-id="743fa-262">These frameworks also support using modern controls and Fluent styling from the Windows UI XAML Library (WinUI) via [XAML islands](/windows/uwp/xaml-platform/xaml-host-controls).</span></span>

<span data-ttu-id="743fa-263">Składnik pulpitu systemu Windows jest częścią zestawu SDK systemu Windows .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="743fa-263">The Windows Desktop component is part of the Windows .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="743fa-264">Nową aplikację WPF lub Windows Forms można utworzyć przy użyciu następujących `dotnet` poleceń:</span><span class="sxs-lookup"><span data-stu-id="743fa-264">You can create a new WPF or Windows Forms app with the following `dotnet` commands:</span></span>

```console
dotnet new wpf
dotnet new winforms
```

<span data-ttu-id="743fa-265">Program Visual Studio 2019 dodaje **nowe szablony projektów** dla platformy .net Core 3,0 Windows Forms i WPF.</span><span class="sxs-lookup"><span data-stu-id="743fa-265">Visual Studio 2019 adds **New Project** templates for .NET Core 3.0 Windows Forms and WPF.</span></span>

<span data-ttu-id="743fa-266">Aby uzyskać więcej informacji na temat sposobu przenoszenia istniejącej aplikacji .NET Framework, zobacz [port WPF projekty](../porting/wpf.md) i [projekty Windows Forms portów](../porting/winforms.md).</span><span class="sxs-lookup"><span data-stu-id="743fa-266">For more information about how to port an existing .NET Framework application, see [Port WPF projects](../porting/wpf.md) and [Port Windows Forms projects](../porting/winforms.md).</span></span>

## <a name="com-callable-components---windows-desktop"></a><span data-ttu-id="743fa-267">Składniki wywoływane przez COM — Windows Desktop</span><span class="sxs-lookup"><span data-stu-id="743fa-267">COM-callable components - Windows Desktop</span></span>

<span data-ttu-id="743fa-268">W systemie Windows można teraz tworzyć zarządzane składniki COM.</span><span class="sxs-lookup"><span data-stu-id="743fa-268">On Windows, you can now create COM-callable managed components.</span></span> <span data-ttu-id="743fa-269">Ta funkcja ma kluczowe znaczenie dla korzystania z platformy .NET Core z modelami dodatków COM, a także do zapewnienia parzystości .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="743fa-269">This capability is critical to use .NET Core with COM add-in models and also to provide parity with .NET Framework.</span></span>

<span data-ttu-id="743fa-270">W przeciwieństwie do .NET Framework, w którym *Biblioteka mscoree. dll* była używana jako serwer com, podczas kompilowania składnika com program .NET Core doda natywną bibliotekę DLL uruchamiania do katalogu *bin* .</span><span class="sxs-lookup"><span data-stu-id="743fa-270">Unlike .NET Framework where the *mscoree.dll* was used as the COM server, .NET Core will add a native launcher dll to the *bin* directory when you build your COM component.</span></span>

<span data-ttu-id="743fa-271">Przykład sposobu tworzenia składnika modelu COM i korzystania z niego można znaleźć w [demonstracji modelu COM](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).</span><span class="sxs-lookup"><span data-stu-id="743fa-271">For an example of how to create a COM component and consume it, see the [COM Demo](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).</span></span>

## <a name="msix-deployment---windows-desktop"></a><span data-ttu-id="743fa-272">Wdrażanie MSIX — Windows Desktop</span><span class="sxs-lookup"><span data-stu-id="743fa-272">MSIX Deployment - Windows Desktop</span></span>

<span data-ttu-id="743fa-273">[MSIX](https://docs.microsoft.com/windows/msix/) to nowy format pakietu aplikacji systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="743fa-273">[MSIX](https://docs.microsoft.com/windows/msix/) is a new Windows application package format.</span></span> <span data-ttu-id="743fa-274">Można go użyć do wdrożenia aplikacji klasycznych platformy .NET Core 3,0 w systemie Windows 10.</span><span class="sxs-lookup"><span data-stu-id="743fa-274">It can be used to deploy .NET Core 3.0 desktop applications to Windows 10.</span></span>

<span data-ttu-id="743fa-275">[Projekt pakietu aplikacji systemu Windows](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), dostępny w programie Visual Studio 2019, umożliwia tworzenie pakietów MSIX przy użyciu [](../deploying/index.md#self-contained-deployments-scd) samodzielnych aplikacji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="743fa-275">The [Windows Application Packaging Project](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), available in Visual Studio 2019, allows you to create MSIX packages with [self-contained](../deploying/index.md#self-contained-deployments-scd) .NET Core applications.</span></span>

<span data-ttu-id="743fa-276">Plik projektu .NET Core musi określać obsługiwane środowiska uruchomieniowe we `<RuntimeIdentifiers>` właściwości:</span><span class="sxs-lookup"><span data-stu-id="743fa-276">The .NET Core project file must specify the supported runtimes in the `<RuntimeIdentifiers>` property:</span></span>

```xml
<RuntimeIdentifiers>win-x86;win-x64</RuntimeIdentifiers>
```

## <a name="winforms-high-dpi"></a><span data-ttu-id="743fa-277">Bardzo wysokie wartości DPI</span><span class="sxs-lookup"><span data-stu-id="743fa-277">WinForms high DPI</span></span>

<span data-ttu-id="743fa-278">Aplikacje .NET Core Windows Forms mogą ustawiać tryb wysokiej rozdzielczości DPI <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType>przy użyciu.</span><span class="sxs-lookup"><span data-stu-id="743fa-278">.NET Core Windows Forms applications can set high DPI mode with <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType>.</span></span> <span data-ttu-id="743fa-279">Metoda ustawia odpowiedni tryb wysokiej rozdzielczości DPI, chyba że ustawienie zostało ustawione za pomocą innych metod, `App.Manifest` takich jak lub P/ `Application.Run`Invokeprzed. `SetHighDpiMode`</span><span class="sxs-lookup"><span data-stu-id="743fa-279">The `SetHighDpiMode` method sets the corresponding high DPI mode unless the setting has been set by other means like `App.Manifest` or P/Invoke before `Application.Run`.</span></span>

<span data-ttu-id="743fa-280">Możliwe `highDpiMode` wartości wyrażone <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType> przez wyliczenie są następujące:</span><span class="sxs-lookup"><span data-stu-id="743fa-280">The possible `highDpiMode` values, as expressed by the <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType> enum are:</span></span>

- `DpiUnaware`
- `SystemAware`
- `PerMonitor`
- `PerMonitorV2`
- `DpiUnawareGdiScaled`

<span data-ttu-id="743fa-281">Aby uzyskać więcej informacji na temat trybów wysokiej rozdzielczości DPI, zobacz [Tworzenie aplikacji klasycznych o wysokiej rozdzielczości DPI w systemie Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows).</span><span class="sxs-lookup"><span data-stu-id="743fa-281">For more information about high DPI modes, see [High DPI Desktop Application Development on Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows).</span></span>

## <a name="ranges-and-indices"></a><span data-ttu-id="743fa-282">Zakresy i indeksy</span><span class="sxs-lookup"><span data-stu-id="743fa-282">Ranges and indices</span></span>

<span data-ttu-id="743fa-283">Nowy <xref:System.Index?displayProperty=nameWithType> typ może służyć do indeksowania.</span><span class="sxs-lookup"><span data-stu-id="743fa-283">The new <xref:System.Index?displayProperty=nameWithType> type can be used for indexing.</span></span> <span data-ttu-id="743fa-284">Można utworzyć jedną z nich na `int` podstawie liczby od początku lub z operatorem prefiksu `^` (C#), który liczy się od końca:</span><span class="sxs-lookup"><span data-stu-id="743fa-284">You can create one from an `int` that counts from the beginning, or with a prefix `^` operator (C#) that counts from the end:</span></span>

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

<span data-ttu-id="743fa-285">Istnieje również <xref:System.Range?displayProperty=nameWithType> typ, który składa się z dwóch `Index` wartości, jeden dla początku i jeden dla końca, i `x..y` może być zapisany z wyrażeniem zakresu (C#).</span><span class="sxs-lookup"><span data-stu-id="743fa-285">There's also the <xref:System.Range?displayProperty=nameWithType> type, which consists of two `Index` values, one for the start and one for the end, and can be written with a `x..y` range expression (C#).</span></span> <span data-ttu-id="743fa-286">Następnie można indeksować za pomocą `Range`, co spowoduje utworzenie wycinka:</span><span class="sxs-lookup"><span data-stu-id="743fa-286">You can then index with a `Range`, which produces a slice:</span></span>

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

<span data-ttu-id="743fa-287">Aby uzyskać więcej informacji, zobacz [Samouczek dotyczący zakresów i indeksów](../../csharp/tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="743fa-287">For more information, see the [ranges and indices tutorial](../../csharp/tutorials/ranges-indexes.md).</span></span>

## <a name="async-streams"></a><span data-ttu-id="743fa-288">Strumienie asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="743fa-288">Async streams</span></span>

<span data-ttu-id="743fa-289">Typ jest nową wersją asynchroniczną programu <xref:System.Collections.Generic.IEnumerable%601>. <xref:System.Collections.Generic.IAsyncEnumerable%601></span><span class="sxs-lookup"><span data-stu-id="743fa-289">The <xref:System.Collections.Generic.IAsyncEnumerable%601> type is a new asynchronous version of <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="743fa-290">Język pozwala `await foreach` `IAsyncEnumerable<T>` na korzystanie z ich elementów i używanie `yield return` ich do tworzenia elementów.</span><span class="sxs-lookup"><span data-stu-id="743fa-290">The language lets you `await foreach` over `IAsyncEnumerable<T>` to consume their elements, and use `yield return` to them to produce elements.</span></span>

<span data-ttu-id="743fa-291">Poniższy przykład ilustruje produkcję i zużycie strumieni asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="743fa-291">The following example demonstrates both production and consumption of async streams.</span></span> <span data-ttu-id="743fa-292">Instrukcja jest asynchroniczna i sama używa `yield return` do tworzenia strumienia asynchronicznego dla obiektów wywołujących. `foreach`</span><span class="sxs-lookup"><span data-stu-id="743fa-292">The `foreach` statement is async and itself uses `yield return` to produce an async stream for callers.</span></span> <span data-ttu-id="743fa-293">Ten wzorzec (using `yield return`) jest zalecanym modelem do tworzenia strumieni asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="743fa-293">This pattern (using `yield return`) is the recommended model for producing async streams.</span></span>

```csharp
async IAsyncEnumerable<int> GetBigResultsAsync()
{
    await foreach (var result in GetResultsAsync())
    {
        if (result > 20) yield return result;
    }
}
```

<span data-ttu-id="743fa-294">Oprócz możliwości `await foreach`można także tworzyć Iteratory asynchroniczne, na przykład iterator, który `IAsyncEnumerable/IAsyncEnumerator` zwraca, że można zarówno `await` , jak i `yield` w.</span><span class="sxs-lookup"><span data-stu-id="743fa-294">In addition to being able to `await foreach`, you can also create async iterators, for example, an iterator that returns an `IAsyncEnumerable/IAsyncEnumerator` that you can both `await` and `yield` in.</span></span> <span data-ttu-id="743fa-295">W przypadku obiektów, które muszą zostać usunięte, można użyć `IAsyncDisposable`różnych typów BCL, takich jak `Stream` i `Timer`.</span><span class="sxs-lookup"><span data-stu-id="743fa-295">For objects that need to be disposed, you can use `IAsyncDisposable`, which various BCL types implement, such as `Stream` and `Timer`.</span></span>

<span data-ttu-id="743fa-296">Aby uzyskać więcej informacji, zobacz [Samouczek dotyczący strumieni asynchronicznych](../../csharp/tutorials/generate-consume-asynchronous-stream.md).</span><span class="sxs-lookup"><span data-stu-id="743fa-296">For more information, see the [async streams tutorial](../../csharp/tutorials/generate-consume-asynchronous-stream.md).</span></span>

## <a name="ieee-floating-point-improvements"></a><span data-ttu-id="743fa-297">Udoskonalenia zmiennoprzecinkowe IEEE</span><span class="sxs-lookup"><span data-stu-id="743fa-297">IEEE Floating-point improvements</span></span>

<span data-ttu-id="743fa-298">Interfejsy API zmiennoprzecinkowe są aktualizowane w celu zapewnienia zgodności z [poprawką IEEE 754-2008](https://en.wikipedia.org/wiki/IEEE_754-2008_revision).</span><span class="sxs-lookup"><span data-stu-id="743fa-298">Floating point APIs are being updated to comply with [IEEE 754-2008 revision](https://en.wikipedia.org/wiki/IEEE_754-2008_revision).</span></span> <span data-ttu-id="743fa-299">Celem tych zmian jest uwidocznienie wszystkich **wymaganych** operacji i upewnienie się, że są one zgodne z specyfikacją IEEE. Aby uzyskać więcej informacji na temat ulepszeń zmiennoprzecinkowych, zobacz [udoskonalenia analizy i formatowania zmiennoprzecinkowe w wpisie na blogu programu .NET Core 3,0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) .</span><span class="sxs-lookup"><span data-stu-id="743fa-299">The goal of these changes is to expose all **required** operations and ensure that they're behaviorally compliant with the IEEE spec. For more information about floating-point improvements, see the [Floating-Point Parsing and Formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog post.</span></span>

<span data-ttu-id="743fa-300">Poprawki dotyczące analizowania i formatowania obejmują:</span><span class="sxs-lookup"><span data-stu-id="743fa-300">Parsing and formatting fixes include:</span></span>

- <span data-ttu-id="743fa-301">Poprawnie Analizuj i Zaokrąglij dane wejściowe o dowolnej długości.</span><span class="sxs-lookup"><span data-stu-id="743fa-301">Correctly parse and round inputs of any length.</span></span>
- <span data-ttu-id="743fa-302">Prawidłowo Przeanalizuj i sformatuj ujemną wartość zero.</span><span class="sxs-lookup"><span data-stu-id="743fa-302">Correctly parse and format negative zero.</span></span>
- <span data-ttu-id="743fa-303">Poprawne analizowanie `Infinity` i `NaN` wykonywanie kontroli bez uwzględniania wielkości liter i Zezwalanie na opcjonalne poprzednie `+` , jeśli ma to zastosowanie.</span><span class="sxs-lookup"><span data-stu-id="743fa-303">Correctly parse `Infinity` and `NaN` by doing a case-insensitive check and allowing an optional preceding `+` where applicable.</span></span>

<span data-ttu-id="743fa-304">Nowe <xref:System.Math?displayProperty=nameWithType> interfejsy API obejmują:</span><span class="sxs-lookup"><span data-stu-id="743fa-304">New <xref:System.Math?displayProperty=nameWithType> APIs include:</span></span>

- <span data-ttu-id="743fa-305"><xref:System.Math.BitIncrement(System.Double)>lub<xref:System.Math.BitDecrement(System.Double)></span><span class="sxs-lookup"><span data-stu-id="743fa-305"><xref:System.Math.BitIncrement(System.Double)> and <xref:System.Math.BitDecrement(System.Double)></span></span>\
<span data-ttu-id="743fa-306">Odnosi się do `nextUp` operacji `nextDown` i IEEE.</span><span class="sxs-lookup"><span data-stu-id="743fa-306">Corresponds to the `nextUp` and `nextDown` IEEE operations.</span></span> <span data-ttu-id="743fa-307">Zwracają one najmniejszą liczbę zmiennoprzecinkową, która porównuje większe lub mniejsze niż dane wejściowe (odpowiednio).</span><span class="sxs-lookup"><span data-stu-id="743fa-307">They return the smallest floating-point number that compares greater or lesser than the input (respectively).</span></span> <span data-ttu-id="743fa-308">Na przykład `Math.BitIncrement(0.0)` zwrócimy `double.Epsilon`.</span><span class="sxs-lookup"><span data-stu-id="743fa-308">For example, `Math.BitIncrement(0.0)` would return `double.Epsilon`.</span></span>

- <span data-ttu-id="743fa-309"><xref:System.Math.MaxMagnitude(System.Double,System.Double)>lub<xref:System.Math.MinMagnitude(System.Double,System.Double)></span><span class="sxs-lookup"><span data-stu-id="743fa-309"><xref:System.Math.MaxMagnitude(System.Double,System.Double)> and <xref:System.Math.MinMagnitude(System.Double,System.Double)></span></span>\
<span data-ttu-id="743fa-310">Odnosi się do `maxNumMag` operacji `minNumMag` i IEEE, zwracają wartość, która jest większa lub mniejsza o wielkości dwóch danych wejściowych (odpowiednio).</span><span class="sxs-lookup"><span data-stu-id="743fa-310">Corresponds to the `maxNumMag` and `minNumMag` IEEE operations, they return the value that is greater or lesser in magnitude of the two inputs (respectively).</span></span> <span data-ttu-id="743fa-311">Na przykład `Math.MaxMagnitude(2.0, -3.0)` zwrócimy `-3.0`.</span><span class="sxs-lookup"><span data-stu-id="743fa-311">For example, `Math.MaxMagnitude(2.0, -3.0)` would return `-3.0`.</span></span>

- <xref:System.Math.ILogB(System.Double)>\
<span data-ttu-id="743fa-312">Odnosi się do `logB` operacji IEEE, która zwraca wartość całkowitą, zwraca integralny dziennik Base-2 parametru wejściowego.</span><span class="sxs-lookup"><span data-stu-id="743fa-312">Corresponds to the `logB` IEEE operation that returns an integral value, it returns the integral base-2 log of the input parameter.</span></span> <span data-ttu-id="743fa-313">Ta metoda jest efektywnie taka sama jak `floor(log2(x))`, ale została wykonana z minimalnym błędem zaokrąglania.</span><span class="sxs-lookup"><span data-stu-id="743fa-313">This method is effectively the same as `floor(log2(x))`, but done with minimal rounding error.</span></span>

- <xref:System.Math.ScaleB(System.Double,System.Int32)>\
<span data-ttu-id="743fa-314">Odnosi się do `scaleB` operacji IEEE, która przyjmuje wartość całkowitą, która zwraca efektywność `x * pow(2, n)`, ale jest wykonywana z minimalnym błędem zaokrąglania.</span><span class="sxs-lookup"><span data-stu-id="743fa-314">Corresponds to the `scaleB` IEEE operation that takes an integral value, it returns effectively `x * pow(2, n)`, but is done with minimal rounding error.</span></span>

- <xref:System.Math.Log2(System.Double)>\
<span data-ttu-id="743fa-315">Odpowiada operacji `log2` IEEE, Zwraca logarytm o podstawie 2.</span><span class="sxs-lookup"><span data-stu-id="743fa-315">Corresponds to the `log2` IEEE operation, it returns the base-2 logarithm.</span></span> <span data-ttu-id="743fa-316">Minimalizuje błąd zaokrąglania.</span><span class="sxs-lookup"><span data-stu-id="743fa-316">It minimizes rounding error.</span></span>

- <xref:System.Math.FusedMultiplyAdd(System.Double,System.Double,System.Double)>\
<span data-ttu-id="743fa-317">Odnosi się do `fma` operacji IEEE, dlatego wykonuje odrzucane mnożenie dodawania.</span><span class="sxs-lookup"><span data-stu-id="743fa-317">Corresponds to the `fma` IEEE operation, it performs a fused multiply add.</span></span> <span data-ttu-id="743fa-318">Oznacza to, `(x * y) + z` że jest to jedna operacja, a tym samym Minimalizacja błędu zaokrąglania.</span><span class="sxs-lookup"><span data-stu-id="743fa-318">That is, it does `(x * y) + z` as a single operation, thereby minimizing the rounding error.</span></span> <span data-ttu-id="743fa-319">Przykładem może być `FusedMultiplyAdd(1e308, 2.0, -1e308)` zwracana wartość `1e308`.</span><span class="sxs-lookup"><span data-stu-id="743fa-319">An example would be `FusedMultiplyAdd(1e308, 2.0, -1e308)` which returns `1e308`.</span></span> <span data-ttu-id="743fa-320">Regularne `(1e308 * 2.0) - 1e308` zwroty `double.PositiveInfinity`.</span><span class="sxs-lookup"><span data-stu-id="743fa-320">The regular `(1e308 * 2.0) - 1e308` returns `double.PositiveInfinity`.</span></span>

- <xref:System.Math.CopySign(System.Double,System.Double)>\
<span data-ttu-id="743fa-321">Odpowiada operacji `x`IEEE, zwraca wartość, `y`ale ze znakiem. `copySign`</span><span class="sxs-lookup"><span data-stu-id="743fa-321">Corresponds to the `copySign` IEEE operation, it returns the value of `x`, but with the sign of `y`.</span></span>

## <a name="fast-built-in-json-support"></a><span data-ttu-id="743fa-322">Szybka Wbudowana obsługa JSON</span><span class="sxs-lookup"><span data-stu-id="743fa-322">Fast built-in JSON support</span></span>

<span data-ttu-id="743fa-323">Użytkownicy platformy .NET mogą w dużym stopniu korzystać z [**JSON.NET**](https://www.newtonsoft.com/json) i innych popularnych bibliotek JSON, które nadal są dobrym wybórem.</span><span class="sxs-lookup"><span data-stu-id="743fa-323">.NET users have largely relied on [**Json.NET**](https://www.newtonsoft.com/json) and other popular JSON libraries, which continue to be good choices.</span></span> <span data-ttu-id="743fa-324">**JSON.NET** używa ciągów .NET jako podstawowego elementu DataType, który jest UTF-16 pod okapem.</span><span class="sxs-lookup"><span data-stu-id="743fa-324">**Json.NET** uses .NET strings as its base datatype, which is UTF-16 under the hood.</span></span>

<span data-ttu-id="743fa-325">Nowa Wbudowana obsługa JSON to wysoka wydajność, niska alokacja i oparta na `Span<byte>`.</span><span class="sxs-lookup"><span data-stu-id="743fa-325">The new built-in JSON support is high-performance, low allocation, and based on `Span<byte>`.</span></span> <span data-ttu-id="743fa-326">Do programu .NET Core 3,0 <xref:System.Text.Json?displayProperty=nameWithType> przestrzeń nazw dodano trzy nowe główne typy powiązane z JSON.</span><span class="sxs-lookup"><span data-stu-id="743fa-326">Three new main JSON-related types have been added to .NET Core 3.0 the <xref:System.Text.Json?displayProperty=nameWithType> namespace.</span></span> <span data-ttu-id="743fa-327">Te typy nie obsługują *jeszcze* zwykłych serializacji i deserializacji obiektu CLR (POCO).</span><span class="sxs-lookup"><span data-stu-id="743fa-327">These types don't *yet* support plain old CLR object (POCO) serialization and deserialization.</span></span>

### <a name="utf8jsonreader"></a><span data-ttu-id="743fa-328">Utf8JsonReader</span><span class="sxs-lookup"><span data-stu-id="743fa-328">Utf8JsonReader</span></span>

<span data-ttu-id="743fa-329"><xref:System.Text.Json.Utf8JsonReader?displayProperty=nameWithType>jest wysoką wydajnością, niskim alokacją, czytnikiem tylko do przodu dla tekstu JSON zakodowanego w formacie UTF-8, `ReadOnlySpan<byte>`Odczytaj od.</span><span class="sxs-lookup"><span data-stu-id="743fa-329"><xref:System.Text.Json.Utf8JsonReader?displayProperty=nameWithType> is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a `ReadOnlySpan<byte>`.</span></span> <span data-ttu-id="743fa-330">`Utf8JsonReader` Jest to podstawowy typ niskiego poziomu, który może służyć do tworzenia niestandardowych analizatorów i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="743fa-330">The `Utf8JsonReader` is a foundational, low-level type, that can be used to build custom parsers and deserializers.</span></span> <span data-ttu-id="743fa-331">Odczytywanie za pośrednictwem ładunku JSON przy `Utf8JsonReader` użyciu nowego jest szybsze niż używanie czytnika z **JSON.NET**.</span><span class="sxs-lookup"><span data-stu-id="743fa-331">Reading through a JSON payload using the new `Utf8JsonReader` is 2x faster than using the reader from **Json.NET**.</span></span> <span data-ttu-id="743fa-332">Nie jest przydzielany do momentu, gdy wymagane jest actualize tokenów JSON jako ciągów (UTF-16).</span><span class="sxs-lookup"><span data-stu-id="743fa-332">It doesn't allocate until you need to actualize JSON tokens as (UTF-16) strings.</span></span>

<span data-ttu-id="743fa-333">Oto przykład odczytywania za pomocą pliku [**Launch. JSON**](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) utworzonego przez Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="743fa-333">Here is an example of reading through the [**launch.json**](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) file created by Visual Studio Code:</span></span>

[!CODE-csharp[Utf8JsonReader](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#PrintJson)]

[!CODE-csharp[Utf8JsonReader](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#PrintJsonCall)]

### <a name="utf8jsonwriter"></a><span data-ttu-id="743fa-334">Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="743fa-334">Utf8JsonWriter</span></span>

<span data-ttu-id="743fa-335"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType>zapewnia wysoką wydajność, niebuforowaną, tylko do przodu sposób pisania zakodowanego tekstu JSON w formacie UTF-8 ze wspólnych typów, takich `String`jak `Int32`,, `DateTime`i.</span><span class="sxs-lookup"><span data-stu-id="743fa-335"><xref:System.Text.Json.Utf8JsonWriter?displayProperty=nameWithType> provides a high-performance, non-cached, forward-only way to write UTF-8 encoded JSON text from common .NET types like `String`, `Int32`, and `DateTime`.</span></span> <span data-ttu-id="743fa-336">Podobnie jak w przypadku czytnika, moduł zapisujący jest podstawą typu, który może służyć do tworzenia serializatorów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="743fa-336">Like the reader, the writer is a foundational, low-level type, that can be used to build custom serializers.</span></span> <span data-ttu-id="743fa-337">Zapis ładunku JSON przy użyciu nowego `Utf8JsonWriter` programu to 30-80% szybciej niż przy użyciu składnika zapisywania z **JSON.NET** i nie jest przydzielany.</span><span class="sxs-lookup"><span data-stu-id="743fa-337">Writing a JSON payload using the new `Utf8JsonWriter` is 30-80% faster than using the writer from **Json.NET** and doesn't allocate.</span></span>

### <a name="jsondocument"></a><span data-ttu-id="743fa-338">JsonDocument</span><span class="sxs-lookup"><span data-stu-id="743fa-338">JsonDocument</span></span>

<span data-ttu-id="743fa-339"><xref:System.Text.Json.JsonDocument?displayProperty=nameWithType>jest zbudowany z góry `Utf8JsonReader`.</span><span class="sxs-lookup"><span data-stu-id="743fa-339"><xref:System.Text.Json.JsonDocument?displayProperty=nameWithType> is built on top of the `Utf8JsonReader`.</span></span> <span data-ttu-id="743fa-340">`JsonDocument` Zapewnia możliwość analizowania danych JSON i tworzenia Document Object Model tylko do odczytu (dom), do których można wykonywać zapytania, aby obsługiwać losowy dostęp i Wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="743fa-340">The `JsonDocument` provides the ability to parse JSON data and build a read-only Document Object Model (DOM) that can be queried to support random access and enumeration.</span></span> <span data-ttu-id="743fa-341">Do elementów JSON, które tworzą dane, można uzyskać dostęp za pośrednictwem <xref:System.Text.Json.JsonElement> typu, który jest udostępniany `JsonDocument` przez właściwość o `RootElement`nazwie.</span><span class="sxs-lookup"><span data-stu-id="743fa-341">The JSON elements that compose the data can be accessed via the <xref:System.Text.Json.JsonElement> type that is exposed by the `JsonDocument` as a property called `RootElement`.</span></span> <span data-ttu-id="743fa-342">`JsonElement` Zawiera tablicę JSON i moduł wyliczający obiektów oraz interfejsy API służące do konwertowania tekstu JSON na popularne typy .NET.</span><span class="sxs-lookup"><span data-stu-id="743fa-342">The `JsonElement` contains the JSON array and object enumerators along with APIs to convert JSON text to common .NET types.</span></span> <span data-ttu-id="743fa-343">Analizowanie typowego ładunku JSON i uzyskiwanie dostępu do wszystkich jego `JsonDocument` elementów członkowskich przy użyciu programu ma wartość 2-3 — szybszy niż **JSON.NET** z małym alokacją dla danych o rozsądnym rozmiarze (czyli < 1 MB).</span><span class="sxs-lookup"><span data-stu-id="743fa-343">Parsing a typical JSON payload and accessing all its members using the `JsonDocument` is 2-3x faster than **Json.NET** with little allocations for data that is reasonably sized (that is, < 1 MB).</span></span>

<span data-ttu-id="743fa-344">Oto przykładowe użycie `JsonDocument` i `JsonElement` , które może służyć jako punkt początkowy:</span><span class="sxs-lookup"><span data-stu-id="743fa-344">Here is a sample usage of the `JsonDocument` and `JsonElement` that can be used as a starting point:</span></span>

[!CODE-csharp[JsonDocument](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#ReadJson)]

<span data-ttu-id="743fa-345">Poniżej znajduje się C# przykład 8,0 do odczytu za pomocą pliku [Launch. json](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) utworzonego przez Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="743fa-345">Here is a C# 8.0 example of reading through the [**launch.json**](https://github.com/dotnet/samples/blob/master/snippets/core/whats-new/whats-new-in-30/cs/launch.json) file created by Visual Studio Code:</span></span>

[!CODE-csharp[JsonDocument](~/samples/snippets/core/whats-new/whats-new-in-30/cs/program.cs#ReadJsonCall)]

### <a name="jsonserializer"></a><span data-ttu-id="743fa-346">JsonSerializer</span><span class="sxs-lookup"><span data-stu-id="743fa-346">JsonSerializer</span></span>

<span data-ttu-id="743fa-347"><xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType>jest zbudowany w oparciu <xref:System.Text.Json.Utf8JsonReader> o i <xref:System.Text.Json.Utf8JsonWriter> , aby zapewnić szybką, niską pamięć opcji serializacji podczas pracy z dokumentami i fragmentami JSON.</span><span class="sxs-lookup"><span data-stu-id="743fa-347"><xref:System.Text.Json.JsonSerializer?displayProperty=nameWithType> is built on top of <xref:System.Text.Json.Utf8JsonReader> and <xref:System.Text.Json.Utf8JsonWriter> to provide a fast, low-memory serialization option when working with JSON documents and fragments.</span></span>

<span data-ttu-id="743fa-348">Oto przykład serializacji obiektu do formatu JSON:</span><span class="sxs-lookup"><span data-stu-id="743fa-348">Here is an example of serializing an object to JSON:</span></span>

[!CODE-csharp[JsonSerializer](~/samples/snippets/core/whats-new/whats-new-in-30/cs/JSON.cs#JsonSerialize)]

<span data-ttu-id="743fa-349">Oto przykład deserializacji ciągu JSON do obiektu.</span><span class="sxs-lookup"><span data-stu-id="743fa-349">Here is an example of deserializing a JSON string to an object.</span></span> <span data-ttu-id="743fa-350">Można użyć ciągu JSON utworzonego w poprzednim przykładzie:</span><span class="sxs-lookup"><span data-stu-id="743fa-350">You can use the JSON string produced by the previous example:</span></span>

[!CODE-csharp[JsonDeserializer](~/samples/snippets/core/whats-new/whats-new-in-30/cs/JSON.cs#JsonDeserialize)]

## <a name="interop-improvements"></a><span data-ttu-id="743fa-351">Udoskonalenia międzyoperacyjności</span><span class="sxs-lookup"><span data-stu-id="743fa-351">Interop improvements</span></span>

<span data-ttu-id="743fa-352">Program .NET Core 3,0 zwiększa natywną międzyoperacyjność interfejsu API.</span><span class="sxs-lookup"><span data-stu-id="743fa-352">.NET Core 3.0 improves native API interop.</span></span>

### <a name="type-nativelibrary"></a><span data-ttu-id="743fa-353">Wpisz: NativeLibrary</span><span class="sxs-lookup"><span data-stu-id="743fa-353">Type: NativeLibrary</span></span>

<span data-ttu-id="743fa-354"><xref:System.Runtime.InteropServices.NativeLibrary?displayProperty=nameWithType>zapewnia hermetyzację do ładowania biblioteki natywnej (przy użyciu tej samej logiki obciążenia co .NET Core P/Invoke) i udostępniającej odpowiednie funkcje pomocnika, `getSymbol`takie jak.</span><span class="sxs-lookup"><span data-stu-id="743fa-354"><xref:System.Runtime.InteropServices.NativeLibrary?displayProperty=nameWithType> provides an encapsulation for loading a native library (using the same load logic as .NET Core P/Invoke) and providing the relevant helper functions such as `getSymbol`.</span></span> <span data-ttu-id="743fa-355">Aby zapoznać się z przykładowym kodem, zobacz [Demonstracja DLLMap](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin).</span><span class="sxs-lookup"><span data-stu-id="743fa-355">For a code example, see the [DLLMap Demo](https://github.com/dotnet/samples/tree/master/core/extensions/AppWithPlugin).</span></span>

### <a name="windows-native-interop"></a><span data-ttu-id="743fa-356">Windows Native Interop</span><span class="sxs-lookup"><span data-stu-id="743fa-356">Windows Native Interop</span></span>

<span data-ttu-id="743fa-357">System Windows oferuje bogaty natywny interfejs API w postaci prostych interfejsów API języka C, COM i WinRT.</span><span class="sxs-lookup"><span data-stu-id="743fa-357">Windows offers a rich native API in the form of flat C APIs, COM, and WinRT.</span></span> <span data-ttu-id="743fa-358">Podczas gdy platforma .NET Core obsługuje funkcję **P/Invoke**, program .net Core 3,0 dodaje możliwość **CoCreate interfejsów API modelu COM** i **aktywowania interfejsów API WinRT**.</span><span class="sxs-lookup"><span data-stu-id="743fa-358">While .NET Core supports **P/Invoke**, .NET Core 3.0 adds the ability to **CoCreate COM APIs** and **Activate WinRT APIs**.</span></span> <span data-ttu-id="743fa-359">Aby zapoznać się z przykładem kodu, zobacz [Demonstracja programu Excel](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).</span><span class="sxs-lookup"><span data-stu-id="743fa-359">For a code example, see the [Excel Demo](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).</span></span>

## <a name="http2-support"></a><span data-ttu-id="743fa-360">Obsługa protokołu HTTP/2</span><span class="sxs-lookup"><span data-stu-id="743fa-360">HTTP/2 support</span></span>

<span data-ttu-id="743fa-361"><xref:System.Net.Http.HttpClient?displayProperty=nameWithType> Typ obsługuje protokół HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="743fa-361">The <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> type supports the HTTP/2 protocol.</span></span> <span data-ttu-id="743fa-362">Jeśli protokół HTTP/2 jest włączony, wersja protokołu HTTP jest negocjowana za pośrednictwem protokołu TLS/CLIENTHELLO ALPN, a protokół HTTP/2 jest używany, jeśli serwer zdecyduje się go użyć.</span><span class="sxs-lookup"><span data-stu-id="743fa-362">If HTTP/2 is enabled, the HTTP protocol version is negotiated via TLS/ALPN, and HTTP/2 is used if the server elects to use it.</span></span>

<span data-ttu-id="743fa-363">Domyślnym protokołem jest protokół HTTP/1.1, ale protokół HTTP/2 można włączyć na dwa różne sposoby.</span><span class="sxs-lookup"><span data-stu-id="743fa-363">The default protocol remains HTTP/1.1, but HTTP/2 can be enabled in two different ways.</span></span> <span data-ttu-id="743fa-364">Najpierw można ustawić komunikat żądania HTTP na potrzeby używania protokołu HTTP/2:</span><span class="sxs-lookup"><span data-stu-id="743fa-364">First, you can set the HTTP request message to use HTTP/2:</span></span>

[!CODE-csharp[Http2Request](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Request)]

<span data-ttu-id="743fa-365">Po drugie, można domyślnie <xref:System.Net.Http.HttpClient> zmienić użycie protokołu HTTP/2:</span><span class="sxs-lookup"><span data-stu-id="743fa-365">Second, you can change <xref:System.Net.Http.HttpClient> to use HTTP/2 by default:</span></span>

[!CODE-csharp[Http2Client](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Client)]

<span data-ttu-id="743fa-366">W wielu przypadkach podczas tworzenia aplikacji chcesz użyć nieszyfrowanego połączenia.</span><span class="sxs-lookup"><span data-stu-id="743fa-366">Many times when you're developing an application, you want to use an unencrypted connection.</span></span> <span data-ttu-id="743fa-367">Jeśli wiesz, że docelowy punkt końcowy będzie używać protokołu HTTP/2, możesz włączyć nieszyfrowane połączenia dla protokołu HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="743fa-367">If you know the target endpoint will be using HTTP/2, you can turn on unencrypted connections for HTTP/2.</span></span> <span data-ttu-id="743fa-368">Można ją włączyć przez ustawienie `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT` zmiennej środowiskowej na `1` lub przez włączenie jej w kontekście aplikacji:</span><span class="sxs-lookup"><span data-stu-id="743fa-368">You can turn it on by setting the `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT` environment variable to `1` or by enabling it in the app context:</span></span>

[!CODE-csharp[Http2Context](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#AppContext)]

## <a name="tls-13--openssl-111-on-linux"></a><span data-ttu-id="743fa-369">TLS 1,3 & OpenSSL 1.1.1 w systemie Linux</span><span class="sxs-lookup"><span data-stu-id="743fa-369">TLS 1.3 & OpenSSL 1.1.1 on Linux</span></span>

<span data-ttu-id="743fa-370">Platforma .NET Core wykorzystuje teraz zalety [protokołu TLS 1,3 w OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), gdy jest on dostępny w danym środowisku.</span><span class="sxs-lookup"><span data-stu-id="743fa-370">.NET Core now takes advantage of [TLS 1.3 support in OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), when it's available in a given environment.</span></span> <span data-ttu-id="743fa-371">Z protokołem TLS 1,3:</span><span class="sxs-lookup"><span data-stu-id="743fa-371">With TLS 1.3:</span></span>

- <span data-ttu-id="743fa-372">Czas połączenia jest ulepszony ze zredukowanymi przedziałami rundy między klientem i serwerem.</span><span class="sxs-lookup"><span data-stu-id="743fa-372">Connection times are improved with reduced round trips required between the client and server.</span></span>
- <span data-ttu-id="743fa-373">Ulepszone zabezpieczenia spowodowane usuwaniem różnych przestarzałych i niezabezpieczonych algorytmów kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="743fa-373">Improved security because of the removal of various obsolete and insecure cryptographic algorithms.</span></span>

<span data-ttu-id="743fa-374">Jeśli jest dostępny, program .NET Core 3,0 używa **OpenSSL 1.1.1**, **OpenSSL 1.1.0**lub **OpenSSL 1.0.2** w systemie Linux.</span><span class="sxs-lookup"><span data-stu-id="743fa-374">When available, .NET Core 3.0 uses **OpenSSL 1.1.1**, **OpenSSL 1.1.0**, or **OpenSSL 1.0.2** on a Linux system.</span></span> <span data-ttu-id="743fa-375">Gdy **OpenSSL 1.1.1** jest dostępny, oba <xref:System.Net.Security.SslStream?displayProperty=nameWithType> typy <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> i używają **protokołu TLS 1,3** (przy założeniu, że zarówno klient, jak i serwer obsługują **protokół TLS 1,3**).</span><span class="sxs-lookup"><span data-stu-id="743fa-375">When **OpenSSL 1.1.1** is available, both <xref:System.Net.Security.SslStream?displayProperty=nameWithType> and <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> types will use **TLS 1.3** (assuming both the client and server support **TLS 1.3**).</span></span>

>[!IMPORTANT]
><span data-ttu-id="743fa-376">Systemy Windows i macOS nie obsługują jeszcze **protokołu TLS 1,3**.</span><span class="sxs-lookup"><span data-stu-id="743fa-376">Windows and macOS do not yet support **TLS 1.3**.</span></span> <span data-ttu-id="743fa-377">Platforma .NET Core 3,0 będzie obsługiwać **protokół TLS 1,3** w tych systemach operacyjnych, gdy będzie dostępna pomoc techniczna.</span><span class="sxs-lookup"><span data-stu-id="743fa-377">.NET Core 3.0 will support **TLS 1.3** on these operating systems when support becomes available.</span></span>

<span data-ttu-id="743fa-378">Poniższy C# przykład 8,0 ilustruje platformę .net Core 3,0 na Ubuntu 18,10 <https://www.cloudflare.com>z:</span><span class="sxs-lookup"><span data-stu-id="743fa-378">The following C# 8.0 example demonstrates .NET Core 3.0 on Ubuntu 18.10 connecting to <https://www.cloudflare.com>:</span></span>

[!CODE-csharp[TLSExample](~/samples/snippets/core/whats-new/whats-new-in-30/cs/TLS.cs#TLS)]

## <a name="cryptography-ciphers"></a><span data-ttu-id="743fa-379">Szyfrowanie kryptografii</span><span class="sxs-lookup"><span data-stu-id="743fa-379">Cryptography ciphers</span></span>

<span data-ttu-id="743fa-380">Program .NET 3,0 dodaje obsługę szyfrów **AES-GCM** i **AES-CCM** , implementowanych <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> za <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> pomocą i odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="743fa-380">.NET 3.0 adds support for **AES-GCM** and **AES-CCM** ciphers, implemented with <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> and <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> respectively.</span></span> <span data-ttu-id="743fa-381">Te algorytmy są [uwierzytelnianiem uwierzytelnianym przy użyciu algorytmów danych skojarzenia (AEAD)](https://en.wikipedia.org/wiki/Authenticated_encryption).</span><span class="sxs-lookup"><span data-stu-id="743fa-381">These algorithms are both [Authenticated Encryption with Association Data (AEAD) algorithms](https://en.wikipedia.org/wiki/Authenticated_encryption).</span></span>

<span data-ttu-id="743fa-382">Poniższy kod ilustruje użycie `AesGcm` szyfru do szyfrowania i odszyfrowywania danych losowych.</span><span class="sxs-lookup"><span data-stu-id="743fa-382">The following code demonstrates using `AesGcm` cipher to encrypt and decrypt random data.</span></span>

[!CODE-csharp[AesGcm](~/samples/snippets/core/whats-new/whats-new-in-30/cs/Cipher.cs#AesGcm)]

## <a name="cryptographic-key-importexport"></a><span data-ttu-id="743fa-383">Import/Eksport klucza kryptograficznego</span><span class="sxs-lookup"><span data-stu-id="743fa-383">Cryptographic Key Import/Export</span></span>

<span data-ttu-id="743fa-384">Program .NET Core 3,0 obsługuje importowanie i eksportowanie asymetrycznych kluczy publicznych i prywatnych z formatów standardowych.</span><span class="sxs-lookup"><span data-stu-id="743fa-384">.NET Core 3.0 supports the import and export of asymmetric public and private keys from standard formats.</span></span> <span data-ttu-id="743fa-385">Nie musisz używać certyfikatu X. 509.</span><span class="sxs-lookup"><span data-stu-id="743fa-385">You don't need to use an X.509 certificate.</span></span>

<span data-ttu-id="743fa-386">Wszystkie typy kluczy, takie jak *RSA*, *DSA*, *ECDSA*i *ECDiffieHellman*, obsługują następujące formaty:</span><span class="sxs-lookup"><span data-stu-id="743fa-386">All key types, such as *RSA*, *DSA*, *ECDsa*, and *ECDiffieHellman*, support the following formats:</span></span>

- <span data-ttu-id="743fa-387">**Klucz publiczny**</span><span class="sxs-lookup"><span data-stu-id="743fa-387">**Public Key**</span></span>
  - <span data-ttu-id="743fa-388">SubjectPublicKeyInfo X. 509</span><span class="sxs-lookup"><span data-stu-id="743fa-388">X.509 SubjectPublicKeyInfo</span></span>

- <span data-ttu-id="743fa-389">**Klucz prywatny**</span><span class="sxs-lookup"><span data-stu-id="743fa-389">**Private key**</span></span>
  - <span data-ttu-id="743fa-390">PrivateKeyInfo PKCS # 8</span><span class="sxs-lookup"><span data-stu-id="743fa-390">PKCS#8 PrivateKeyInfo</span></span>
  - <span data-ttu-id="743fa-391">EncryptedPrivateKeyInfo PKCS # 8</span><span class="sxs-lookup"><span data-stu-id="743fa-391">PKCS#8 EncryptedPrivateKeyInfo</span></span>

<span data-ttu-id="743fa-392">Klucze RSA obsługują również:</span><span class="sxs-lookup"><span data-stu-id="743fa-392">RSA keys also support:</span></span>

- <span data-ttu-id="743fa-393">**Klucz publiczny**</span><span class="sxs-lookup"><span data-stu-id="743fa-393">**Public Key**</span></span>
  - <span data-ttu-id="743fa-394">RSAPublicKey PKCS # 1</span><span class="sxs-lookup"><span data-stu-id="743fa-394">PKCS#1 RSAPublicKey</span></span>

- <span data-ttu-id="743fa-395">**Klucz prywatny**</span><span class="sxs-lookup"><span data-stu-id="743fa-395">**Private key**</span></span>
  - <span data-ttu-id="743fa-396">RSAPrivateKey PKCS # 1</span><span class="sxs-lookup"><span data-stu-id="743fa-396">PKCS#1 RSAPrivateKey</span></span>

<span data-ttu-id="743fa-397">Metody eksportowania generują dane binarne kodowane algorytmem DER, a metody importowe oczekują na to samo.</span><span class="sxs-lookup"><span data-stu-id="743fa-397">The export methods produce DER-encoded binary data, and the import methods expect the same.</span></span> <span data-ttu-id="743fa-398">Jeśli klucz jest przechowywany w formacie PEM przyjaznym dla tekstu, wywołujący będzie musiał odkodować zawartość przed wywołaniem metody Import.</span><span class="sxs-lookup"><span data-stu-id="743fa-398">If a key is stored in the text-friendly PEM format, the caller will need to base64-decode the content before calling an import method.</span></span>

[!CODE-csharp[RSA](~/samples/snippets/core/whats-new/whats-new-in-30/cs/RSA.cs#Rsa)]

<span data-ttu-id="743fa-399">Można sprawdzać <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType> pliki **PKCS # 8** i <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType>pliki **PFX/PKCS # 12** .</span><span class="sxs-lookup"><span data-stu-id="743fa-399">**PKCS#8** files can be inspected with <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType> and **PFX/PKCS#12** files can be inspected with <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType>.</span></span> <span data-ttu-id="743fa-400">Pliki **PFX/PKCS # 12** można manipulować przy użyciu programu <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="743fa-400">**PFX/PKCS#12** files can be manipulated with <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType>.</span></span>

## <a name="serialport-for-linux"></a><span data-ttu-id="743fa-401">Klasy SerialPort dla systemu Linux</span><span class="sxs-lookup"><span data-stu-id="743fa-401">SerialPort for Linux</span></span>

<span data-ttu-id="743fa-402">Program .NET Core 3,0 zapewnia podstawową pomoc <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> techniczną dla systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="743fa-402">.NET Core 3.0 provides basic support for <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> on Linux.</span></span>

<span data-ttu-id="743fa-403">Wcześniej platforma .NET Core jest obsługiwana `SerialPort` tylko w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="743fa-403">Previously, .NET Core only supported using `SerialPort` on Windows.</span></span>

<span data-ttu-id="743fa-404">Aby uzyskać więcej informacji o ograniczonej obsłudze portu szeregowego w systemie Linux, zobacz artykuł dotyczący usługi [GitHub #33146](https://github.com/dotnet/corefx/issues/33146).</span><span class="sxs-lookup"><span data-stu-id="743fa-404">For more information about the limited support for the serial port on Linux, see [GitHub issue #33146](https://github.com/dotnet/corefx/issues/33146).</span></span>

## <a name="docker-and-cgroup-memory-limits"></a><span data-ttu-id="743fa-405">Limity pamięci Docker i cgroup</span><span class="sxs-lookup"><span data-stu-id="743fa-405">Docker and cgroup memory Limits</span></span>

<span data-ttu-id="743fa-406">Począwszy od wersji zapoznawczej 3, uruchomienie programu .NET Core 3,0 w systemie Linux z rozwiązaniem Docker działa lepiej z limitami pamięci cgroup.</span><span class="sxs-lookup"><span data-stu-id="743fa-406">Starting with Preview 3, running .NET Core 3.0 on Linux with Docker works better with cgroup memory limits.</span></span> <span data-ttu-id="743fa-407">Uruchamianie kontenera Docker z limitami pamięci, na przykład z `docker run -m`, zmienia sposób działania programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="743fa-407">Running a Docker container with memory limits, such as with `docker run -m`, changes how .NET Core behaves.</span></span>

- <span data-ttu-id="743fa-408">Domyślny rozmiar sterty modułu wyrzucania elementów bezużytecznych (GC): maksymalnie 20 MB lub 75% limitu pamięci w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="743fa-408">Default Garbage Collector (GC) heap size: maximum of 20 mb or 75% of the memory limit on the container.</span></span>
- <span data-ttu-id="743fa-409">Rozmiar jawny można ustawić jako liczbę bezwzględną lub procent limitu cgroup.</span><span class="sxs-lookup"><span data-stu-id="743fa-409">Explicit size can be set as an absolute number or percentage of cgroup limit.</span></span>
- <span data-ttu-id="743fa-410">Minimalny zarezerwowany rozmiar segmentu na stos GC to 16 MB.</span><span class="sxs-lookup"><span data-stu-id="743fa-410">Minimum reserved segment size per GC heap is 16 mb.</span></span> <span data-ttu-id="743fa-411">Ten rozmiar zmniejsza liczbę stert, które są tworzone na maszynach.</span><span class="sxs-lookup"><span data-stu-id="743fa-411">This size reduces the number of heaps that are created on machines.</span></span>

## <a name="smaller-garbage-collection-heap-sizes"></a><span data-ttu-id="743fa-412">Mniejsze rozmiary sterty wyrzucania elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="743fa-412">Smaller Garbage Collection heap sizes</span></span>

<span data-ttu-id="743fa-413">Rozmiar sterty domyślnej modułu wyrzucania elementów bezużytecznych został zmniejszony z powodu mniejszej ilości pamięci w programie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="743fa-413">The Garbage Collector's default heap size has been reduced resulting in .NET Core using less memory.</span></span> <span data-ttu-id="743fa-414">Ta zmiana jest lepsza w porównaniu z budżetem alokacji generacji 0 z nowoczesnymi rozmiarami pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="743fa-414">This change better aligns with the generation 0 allocation budget with modern processor cache sizes.</span></span>

## <a name="garbage-collection-large-page-support"></a><span data-ttu-id="743fa-415">Obsługa dużej strony odzyskiwania pamięci</span><span class="sxs-lookup"><span data-stu-id="743fa-415">Garbage Collection Large Page support</span></span>

<span data-ttu-id="743fa-416">Duże strony (znane również jako ogromne strony w systemie Linux) to funkcja, w której system operacyjny może ustalić obszary pamięci większe niż rozmiar strony natywnej (często 4K), aby zwiększyć wydajność aplikacji żądającej tych dużych stron.</span><span class="sxs-lookup"><span data-stu-id="743fa-416">Large Pages (also known as Huge Pages on Linux) is a feature where the operating system is able to establish memory regions larger than the native page size (often 4K) to improve performance of the application requesting these large pages.</span></span>

<span data-ttu-id="743fa-417">Moduł wyrzucania elementów bezużytecznych można teraz skonfigurować przy użyciu ustawienia **GCLargePages** jako funkcji wyboru do przydzielania dużych stron w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="743fa-417">The Garbage Collector can now be configured with the **GCLargePages** setting as an opt-in feature to choose to allocate large pages on Windows.</span></span>

## <a name="gpio-support-for-raspberry-pi"></a><span data-ttu-id="743fa-418">Obsługa interfejsu GPIO dla Raspberry Pi</span><span class="sxs-lookup"><span data-stu-id="743fa-418">GPIO Support for Raspberry Pi</span></span>

<span data-ttu-id="743fa-419">Do programu NuGet zostały wydane dwa pakiety, których można użyć do programowania interfejsu GPIO:</span><span class="sxs-lookup"><span data-stu-id="743fa-419">Two packages have been released to NuGet that you can use for GPIO programming:</span></span>

- [<span data-ttu-id="743fa-420">System.Device.Gpio</span><span class="sxs-lookup"><span data-stu-id="743fa-420">System.Device.Gpio</span></span>](https://www.nuget.org/packages/System.Device.Gpio)
- [<span data-ttu-id="743fa-421">IoT. Device. bindings</span><span class="sxs-lookup"><span data-stu-id="743fa-421">Iot.Device.Bindings</span></span>](https://www.nuget.org/packages/Iot.Device.Bindings)

<span data-ttu-id="743fa-422">Pakiety GPIO obejmują interfejsy API dla urządzeń z interfejsem *GPIO*, *SPI*, *I2C*i *PWM* .</span><span class="sxs-lookup"><span data-stu-id="743fa-422">The GPIO packages include APIs for *GPIO*, *SPI*, *I2C*, and *PWM* devices.</span></span> <span data-ttu-id="743fa-423">Pakiet powiązań IoT obejmuje powiązania urządzeń.</span><span class="sxs-lookup"><span data-stu-id="743fa-423">The IoT bindings package includes device bindings.</span></span> <span data-ttu-id="743fa-424">Aby uzyskać więcej informacji, zobacz [repozytorium GitHub](https://github.com/dotnet/iot/blob/master/src/devices/).</span><span class="sxs-lookup"><span data-stu-id="743fa-424">For more information, see the [devices GitHub repo](https://github.com/dotnet/iot/blob/master/src/devices/).</span></span>

## <a name="arm64-linux-support"></a><span data-ttu-id="743fa-425">Obsługa systemu Linux ARM64</span><span class="sxs-lookup"><span data-stu-id="743fa-425">ARM64 Linux support</span></span>

<span data-ttu-id="743fa-426">Program .NET Core 3,0 dodaje obsługę ARM64 dla systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="743fa-426">.NET Core 3.0 adds support for ARM64 for Linux.</span></span> <span data-ttu-id="743fa-427">Podstawowy przypadek użycia dla ARM64 jest obecnie z scenariuszami IoT.</span><span class="sxs-lookup"><span data-stu-id="743fa-427">The primary use case for ARM64 is currently with IoT scenarios.</span></span> <span data-ttu-id="743fa-428">Aby uzyskać więcej informacji, zobacz temat [stan arm64 programu .NET Core](https://github.com/dotnet/announcements/issues/82).</span><span class="sxs-lookup"><span data-stu-id="743fa-428">For more information, see [.NET Core ARM64 Status](https://github.com/dotnet/announcements/issues/82).</span></span>

<span data-ttu-id="743fa-429">[Obrazy Docker dla platformy .NET Core w systemie arm64](https://hub.docker.com/r/microsoft/dotnet/) są dostępne dla Alpine, Debian i Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="743fa-429">[Docker images for .NET Core on ARM64](https://hub.docker.com/r/microsoft/dotnet/) are available for Alpine, Debian, and Ubuntu.</span></span>

> [!NOTE]
> <span data-ttu-id="743fa-430">**Arm64** Obsługa systemu Windows nie jest jeszcze dostępna.</span><span class="sxs-lookup"><span data-stu-id="743fa-430">**ARM64** Windows support isn't yet available.</span></span>

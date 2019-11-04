---
title: Co nowego w programie .NET Core 3.0
description: Dowiedz się więcej o nowych funkcjach dostępnych w programie .NET Core 3,0.
dev_langs:
- csharp
- vb
author: thraka
ms.author: adegeo
ms.date: 10/22/2019
ms.openlocfilehash: dcbf1073c12650101efdcf6022db0b29ace2eb3f
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73420758"
---
# <a name="whats-new-in-net-core-30"></a><span data-ttu-id="6413d-103">Co nowego w programie .NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="6413d-103">What's new in .NET Core 3.0</span></span>

<span data-ttu-id="6413d-104">W tym artykule opisano nowości w programie .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="6413d-104">This article describes what is new in .NET Core 3.0.</span></span> <span data-ttu-id="6413d-105">Jednym z największych ulepszeń jest obsługa aplikacji klasycznych systemu Windows (tylko system Windows).</span><span class="sxs-lookup"><span data-stu-id="6413d-105">One of the biggest enhancements is support for Windows desktop applications (Windows only).</span></span> <span data-ttu-id="6413d-106">Korzystając z pulpitu systemu Windows składnika zestawu SDK platformy .NET Core 3,0, można przenieść aplikacje Windows Forms i Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="6413d-106">By using the .NET Core 3.0 SDK component Windows Desktop, you can port your Windows Forms and Windows Presentation Foundation (WPF) applications.</span></span> <span data-ttu-id="6413d-107">Aby można było wyczyścić, składnik pulpitu systemu Windows jest obsługiwany i uwzględniany w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="6413d-107">To be clear, the Windows Desktop component is only supported and included on Windows.</span></span> <span data-ttu-id="6413d-108">Aby uzyskać więcej informacji, zobacz sekcję [pulpitu systemu Windows](#windows-desktop) w dalszej części tego artykułu.</span><span class="sxs-lookup"><span data-stu-id="6413d-108">For more information, see the [Windows desktop](#windows-desktop) section later in this article.</span></span>

<span data-ttu-id="6413d-109">Program .NET Core 3,0 dodaje obsługę C# 8,0.</span><span class="sxs-lookup"><span data-stu-id="6413d-109">.NET Core 3.0 adds support for C# 8.0.</span></span> <span data-ttu-id="6413d-110">Zdecydowanie zaleca się używanie [programu Visual Studio 2019 w wersji 16,3](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) lub nowszej, [Visual Studio dla komputerów Mac 8,3](/visualstudio/mac/install-preview) lub nowszego lub [Visual Studio Code](https://code.visualstudio.com/) z najnowszym  **C# rozszerzeniem**.</span><span class="sxs-lookup"><span data-stu-id="6413d-110">It's highly recommended that you use [Visual Studio 2019 version 16.3](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or newer, [Visual Studio for Mac 8.3](/visualstudio/mac/install-preview) or newer, or [Visual Studio Code](https://code.visualstudio.com/) with the latest **C# extension**.</span></span>

<span data-ttu-id="6413d-111">[Pobierz i Rozpocznij pracę z platformą .NET Core 3,0](https://aka.ms/netcore3download) teraz w systemie Windows, MacOS lub Linux.</span><span class="sxs-lookup"><span data-stu-id="6413d-111">[Download and get started with .NET Core 3.0](https://aka.ms/netcore3download) right now on Windows, macOS, or Linux.</span></span>

<span data-ttu-id="6413d-112">Aby uzyskać więcej informacji o wersji, zobacz [anons programu .NET Core 3,0](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0/).</span><span class="sxs-lookup"><span data-stu-id="6413d-112">For more information about the release, see the [.NET Core 3.0 announcement](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0/).</span></span>

<span data-ttu-id="6413d-113">Środowisko .NET Core RC1 zostało uznane za gotowe do produkcji przez firmę Microsoft i zostało w pełni obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="6413d-113">.NET Core RC1 was considered production ready by Microsoft and was fully supported.</span></span> <span data-ttu-id="6413d-114">Jeśli korzystasz z wersji zapoznawczej, musisz przejść do wersji RTM, aby uzyskać pomoc techniczną.</span><span class="sxs-lookup"><span data-stu-id="6413d-114">If you're using a preview release, you must move to the RTM version for continued support.</span></span>

## <a name="language-improvements-c-80"></a><span data-ttu-id="6413d-115">Udoskonalenia C# języka 8,0</span><span class="sxs-lookup"><span data-stu-id="6413d-115">Language improvements C# 8.0</span></span>

<span data-ttu-id="6413d-116">C#8,0 jest również częścią tej wersji, która obejmuje funkcję [typów referencyjnych dopuszczających wartość null](../../csharp/tutorials/nullable-reference-types.md) , [strumienie asynchroniczne](../../csharp/tutorials/generate-consume-asynchronous-stream.md)i [więcej wzorców](../../csharp/tutorials/pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="6413d-116">C# 8.0 is also part of this release, which includes the [nullable reference types](../../csharp/tutorials/nullable-reference-types.md) feature, [async streams](../../csharp/tutorials/generate-consume-asynchronous-stream.md), and [more patterns](../../csharp/tutorials/pattern-matching.md).</span></span> <span data-ttu-id="6413d-117">Aby uzyskać więcej informacji C# o funkcjach 8,0, zobacz [co nowego C# w programie 8,0](../../csharp/whats-new/csharp-8.md).</span><span class="sxs-lookup"><span data-stu-id="6413d-117">For more information about C# 8.0 features, see [What's new in C# 8.0](../../csharp/whats-new/csharp-8.md).</span></span>

<span data-ttu-id="6413d-118">Wprowadzono ulepszenia dotyczące języka w celu obsługi następujących funkcji API poniżej:</span><span class="sxs-lookup"><span data-stu-id="6413d-118">Language enhancements were added to support the following API features detailed below:</span></span>

- [<span data-ttu-id="6413d-119">Zakresy i indeksy</span><span class="sxs-lookup"><span data-stu-id="6413d-119">Ranges and indices</span></span>](#ranges-and-indices)
- [<span data-ttu-id="6413d-120">Strumienie asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="6413d-120">Async streams</span></span>](#async-streams)

## <a name="net-standard-21"></a><span data-ttu-id="6413d-121">.NET Standard 2,1</span><span class="sxs-lookup"><span data-stu-id="6413d-121">.NET Standard 2.1</span></span>

<span data-ttu-id="6413d-122">Platforma .NET Core 3,0 implementuje **.NET Standard 2,1**.</span><span class="sxs-lookup"><span data-stu-id="6413d-122">.NET Core 3.0 implements **.NET Standard 2.1**.</span></span> <span data-ttu-id="6413d-123">Jednak domyślny szablon `dotnet new classlib` generuje projekt, który nadal jest przeznaczony dla **.NET Standard 2,0**.</span><span class="sxs-lookup"><span data-stu-id="6413d-123">However, the default `dotnet new classlib` template generates a project that still targets **.NET Standard 2.0**.</span></span> <span data-ttu-id="6413d-124">Aby docelowa **.NET Standard 2,1**, edytuj plik projektu i zmień właściwość `TargetFramework` na `netstandard2.1`:</span><span class="sxs-lookup"><span data-stu-id="6413d-124">To target **.NET Standard 2.1**, edit your project file and change the `TargetFramework` property to `netstandard2.1`:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard2.1</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="6413d-125">Jeśli używasz programu Visual Studio, potrzebujesz [programu Visual studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), ponieważ program visual Studio 2017 nie obsługuje **.NET Standard 2,1** ani **.NET Core 3,0**.</span><span class="sxs-lookup"><span data-stu-id="6413d-125">If you're using Visual Studio, you need [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), as Visual Studio 2017 doesn't support **.NET Standard 2.1** or **.NET Core 3.0**.</span></span>

## <a name="compiledeploy"></a><span data-ttu-id="6413d-126">Kompiluj/Wdróż</span><span class="sxs-lookup"><span data-stu-id="6413d-126">Compile/Deploy</span></span>

### <a name="default-executables"></a><span data-ttu-id="6413d-127">Domyślne pliki wykonywalne</span><span class="sxs-lookup"><span data-stu-id="6413d-127">Default executables</span></span>

<span data-ttu-id="6413d-128">Platforma .NET Core teraz domyślnie kompiluje [pliki wykonywalne zależne od platformy](../deploying/index.md#framework-dependent-executables-fde) .</span><span class="sxs-lookup"><span data-stu-id="6413d-128">.NET Core now builds [framework-dependent executables](../deploying/index.md#framework-dependent-executables-fde) by default.</span></span> <span data-ttu-id="6413d-129">To zachowanie jest nowe w przypadku aplikacji korzystających z zainstalowanej globalnie wersji platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6413d-129">This behavior is new for applications that use a globally installed version of .NET Core.</span></span> <span data-ttu-id="6413d-130">Wcześniej tylko [wstępnie zawarte wdrożenia](../deploying/index.md#self-contained-deployments-scd) spowodują utworzenie pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="6413d-130">Previously, only [self-contained deployments](../deploying/index.md#self-contained-deployments-scd) would produce an executable.</span></span>

<span data-ttu-id="6413d-131">W trakcie `dotnet build` lub `dotnet publish` tworzony jest plik wykonywalny zgodny ze środowiskiem i platformą używanego zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="6413d-131">During `dotnet build` or `dotnet publish`, an executable is created that matches the environment and platform of the SDK you're using.</span></span> <span data-ttu-id="6413d-132">Można oczekiwać, że te same elementy wykonywalne są takie same jak w przypadku innych natywnych plików wykonywalnych, takich jak:</span><span class="sxs-lookup"><span data-stu-id="6413d-132">You can expect the same things with these executables as you would other native executables, such as:</span></span>

- <span data-ttu-id="6413d-133">Możesz kliknąć dwukrotnie plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="6413d-133">You can double-click on the executable.</span></span>
- <span data-ttu-id="6413d-134">Aplikację można uruchomić bezpośrednio z poziomu wiersza polecenia, na przykład `myapp.exe` w systemie Windows i `./myapp` w systemie Linux i macOS.</span><span class="sxs-lookup"><span data-stu-id="6413d-134">You can launch the application from a command prompt directly, such as `myapp.exe` on Windows, and `./myapp` on Linux and macOS.</span></span>

### <a name="single-file-executables"></a><span data-ttu-id="6413d-135">Pliki wykonywalne pojedynczego pliku</span><span class="sxs-lookup"><span data-stu-id="6413d-135">Single-file executables</span></span>

<span data-ttu-id="6413d-136">Polecenie `dotnet publish` obsługuje pakowanie aplikacji do pliku wykonywalnego określonego dla konkretnej platformy.</span><span class="sxs-lookup"><span data-stu-id="6413d-136">The `dotnet publish` command supports packaging your app into a platform-specific single-file executable.</span></span> <span data-ttu-id="6413d-137">Plik wykonywalny jest samowyodrębniający się i zawiera wszystkie zależności (w tym natywne) wymagane do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6413d-137">The executable is self-extracting and contains all dependencies (including native) that are required to run your app.</span></span> <span data-ttu-id="6413d-138">Gdy aplikacja jest uruchamiana po raz pierwszy, aplikacja zostanie wyodrębniona do katalogu na podstawie nazwy aplikacji i identyfikatora kompilacji.</span><span class="sxs-lookup"><span data-stu-id="6413d-138">When the app is first run, the application is extracted to a directory based on the app name and build identifier.</span></span> <span data-ttu-id="6413d-139">Uruchamianie jest szybsze, gdy aplikacja jest uruchamiana ponownie.</span><span class="sxs-lookup"><span data-stu-id="6413d-139">Startup is faster when the application is run again.</span></span> <span data-ttu-id="6413d-140">Aplikacja nie musi wyodrębniać siebie po raz drugi, chyba że została użyta Nowa wersja.</span><span class="sxs-lookup"><span data-stu-id="6413d-140">The application doesn't need to extract itself a second time unless a new version was used.</span></span>

<span data-ttu-id="6413d-141">Aby opublikować plik wykonywalny pojedynczego pliku, ustaw `PublishSingleFile` w projekcie lub w wierszu polecenia z poleceniem `dotnet publish`:</span><span class="sxs-lookup"><span data-stu-id="6413d-141">To publish a single-file executable, set the `PublishSingleFile` in your project or on the command line with the `dotnet publish` command:</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifier>win10-x64</RuntimeIdentifier>
  <PublishSingleFile>true</PublishSingleFile>
</PropertyGroup>
```

<span data-ttu-id="6413d-142">—lub—</span><span class="sxs-lookup"><span data-stu-id="6413d-142">-or-</span></span>

```dotnetcli
dotnet publish -r win10-x64 -p:PublishSingleFile=true
```

<span data-ttu-id="6413d-143">Aby uzyskać więcej informacji o publikowaniu jednoplikowym, zapoznaj się z [dokumentem projektu pakietu pojedynczego pliku](https://github.com/dotnet/designs/blob/master/accepted/single-file/design.md).</span><span class="sxs-lookup"><span data-stu-id="6413d-143">For more information about single-file publishing, see the [single-file bundler design document](https://github.com/dotnet/designs/blob/master/accepted/single-file/design.md).</span></span>

### <a name="assembly-linking"></a><span data-ttu-id="6413d-144">Łączenie zestawów</span><span class="sxs-lookup"><span data-stu-id="6413d-144">Assembly linking</span></span>

<span data-ttu-id="6413d-145">Zestaw SDK platformy .NET Core 3,0 zawiera narzędzie, które pozwala zmniejszyć rozmiar aplikacji przez analizowanie IL i przycinanie nieużywanych zestawów.</span><span class="sxs-lookup"><span data-stu-id="6413d-145">The .NET core 3.0 SDK comes with a tool that can reduce the size of apps by analyzing IL and trimming unused assemblies.</span></span>

<span data-ttu-id="6413d-146">Aplikacje samodzielne obejmują wszystko, co jest potrzebne do uruchomienia kodu, bez konieczności instalowania programu .NET na komputerze-hoście.</span><span class="sxs-lookup"><span data-stu-id="6413d-146">Self-contained apps include everything needed to run your code, without requiring .NET to be installed on the host computer.</span></span> <span data-ttu-id="6413d-147">Jednak wiele razy aplikacja wymaga tylko małego podzestawu platformy do działania, a inne nieużywane biblioteki mogą zostać usunięte.</span><span class="sxs-lookup"><span data-stu-id="6413d-147">However, many times the app only requires a small subset of the framework to function, and other unused libraries could be removed.</span></span>

<span data-ttu-id="6413d-148">Platforma .NET Core zawiera teraz ustawienie, które będzie używać narzędzia [konsolidatora Il](https://github.com/mono/linker) do skanowania Il aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6413d-148">.NET Core now includes a setting that will use the [IL linker](https://github.com/mono/linker) tool to scan the IL of your app.</span></span> <span data-ttu-id="6413d-149">to narzędzie wykrywa wymagany kod, a następnie przycina nieużywane biblioteki.</span><span class="sxs-lookup"><span data-stu-id="6413d-149">This tool detects what code is required, and then trims unused libraries.</span></span> <span data-ttu-id="6413d-150">To narzędzie może znacznie zmniejszyć rozmiar wdrożenia niektórych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6413d-150">This tool can significantly reduce the deployment size of some apps.</span></span>

<span data-ttu-id="6413d-151">Aby włączyć to narzędzie, należy dodać ustawienie `<PublishTrimmed>` w projekcie i opublikować samodzielną aplikację:</span><span class="sxs-lookup"><span data-stu-id="6413d-151">To enable this tool, add the `<PublishTrimmed>` setting in your project and publish a self-contained app:</span></span>

```xml
<PropertyGroup>
  <PublishTrimmed>true</PublishTrimmed>
</PropertyGroup>
```

```dotnetcli
dotnet publish -r <rid> -c Release
```

<span data-ttu-id="6413d-152">Na przykład podstawowy "Hello World" nowy szablon projektu konsoli, który jest dostępny po opublikowaniu, trafień o rozmiarze 70 MB.</span><span class="sxs-lookup"><span data-stu-id="6413d-152">As an example, the basic "hello world" new console project template that is included, when published, hits about 70 MB in size.</span></span> <span data-ttu-id="6413d-153">Przy użyciu `<PublishTrimmed>` rozmiar ten jest zmniejszany do około 30 MB.</span><span class="sxs-lookup"><span data-stu-id="6413d-153">By using `<PublishTrimmed>`, that size is reduced to about 30 MB.</span></span>

<span data-ttu-id="6413d-154">Należy wziąć pod uwagę, że aplikacje lub struktury (w tym ASP.NET Core i WPF), które wykorzystują odbicie lub powiązane funkcje dynamiczne, często będą przerywane po przycięciu.</span><span class="sxs-lookup"><span data-stu-id="6413d-154">It's important to consider that applications or frameworks (including ASP.NET Core and WPF) that use reflection or related dynamic features, will often break when trimmed.</span></span> <span data-ttu-id="6413d-155">To uszkodzenie występuje, ponieważ konsolidator nie wie o tym zachowaniu dynamicznym i nie może określić, które typy struktur są wymagane do odbicia.</span><span class="sxs-lookup"><span data-stu-id="6413d-155">This breakage occurs because the linker doesn't know about this dynamic behavior and can't determine which framework types are required for reflection.</span></span> <span data-ttu-id="6413d-156">Narzędzie konsolidatora IL można skonfigurować pod kątem tego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="6413d-156">The IL Linker tool can be configured to be aware of this scenario.</span></span>

<span data-ttu-id="6413d-157">Przed przycinaniem upewnij się, że aplikacja została przetestowana.</span><span class="sxs-lookup"><span data-stu-id="6413d-157">Above all else, be sure to test your app after trimming.</span></span>

<span data-ttu-id="6413d-158">Aby uzyskać więcej informacji na temat narzędzia konsolidatora IL, zapoznaj się z [dokumentacją](https://aka.ms/dotnet-illink) lub odwiedź repozytorium [mono/konsolidatora]( https://github.com/mono/linker) .</span><span class="sxs-lookup"><span data-stu-id="6413d-158">For more information about the IL Linker tool, see the [documentation](https://aka.ms/dotnet-illink) or visit the [mono/linker]( https://github.com/mono/linker) repo.</span></span>

### <a name="tiered-compilation"></a><span data-ttu-id="6413d-159">Kompilacja warstwowa</span><span class="sxs-lookup"><span data-stu-id="6413d-159">Tiered compilation</span></span>

<span data-ttu-id="6413d-160">[Kompilacja warstwowa](https://devblogs.microsoft.com/dotnet/tiered-compilation-preview-in-net-core-2-1/) (TC) jest domyślnie włączona z platformą .net Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="6413d-160">[Tiered compilation](https://devblogs.microsoft.com/dotnet/tiered-compilation-preview-in-net-core-2-1/) (TC) is on by default with .NET Core 3.0.</span></span> <span data-ttu-id="6413d-161">Ta funkcja umożliwia środowisku uruchomieniowemu wydajniejsze używanie kompilatora just-in-Time (JIT) w celu uzyskania lepszej wydajności.</span><span class="sxs-lookup"><span data-stu-id="6413d-161">This feature enables the runtime to more adaptively use the Just-In-Time (JIT) compiler to get better performance.</span></span>

<span data-ttu-id="6413d-162">Główną zaletą TC jest włączenie (re-) metod jitting z niską jakością, ale szybszym lub wyższą warstwą.</span><span class="sxs-lookup"><span data-stu-id="6413d-162">The main benefit of TC is to enable (re-)jitting methods with a lower-quality-but-faster tier or a higher-quality-but-slower tier.</span></span> <span data-ttu-id="6413d-163">Pozwala to zwiększyć wydajność aplikacji, która przechodzi przez różne etapy wykonywania, od uruchamiania do stanu stałego.</span><span class="sxs-lookup"><span data-stu-id="6413d-163">This helps increase performance of an application as it goes through various stages of execution, from startup through steady-state.</span></span> <span data-ttu-id="6413d-164">Jest to kontrast z podejściem innym niż TC, gdzie każda metoda jest skompilowana w jeden sposób (taka sama jak warstwa wysokiej jakości), która jest obciążona niestabilnym stanem w porównaniu z wydajnością uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="6413d-164">This contrasts with the non-TC approach, where every method is compiled a single way (the same as the high-quality tier), which is biased to steady-state over startup performance.</span></span>

<span data-ttu-id="6413d-165">Aby włączyć funkcję szybkiego JIT (kod 0 trybie JIT), użyj tego ustawienia w pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="6413d-165">To enable Quick JIT (tier 0 jitted code), use this setting in your project file:</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>true</TieredCompilationQuickJit>
</PropertyGroup>
```

<span data-ttu-id="6413d-166">Aby całkowicie wyłączyć TC, użyj tego ustawienia w pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="6413d-166">To disable TC completely, use this setting in your project file:</span></span>

```xml
<TieredCompilation>false</TieredCompilation>
```

### <a name="readytorun-images"></a><span data-ttu-id="6413d-167">Obrazy ReadyToRun</span><span class="sxs-lookup"><span data-stu-id="6413d-167">ReadyToRun images</span></span>

<span data-ttu-id="6413d-168">Można skrócić czas uruchamiania aplikacji .NET Core, kompilując zestawy aplikacji jako ReadyToRun (R2R).</span><span class="sxs-lookup"><span data-stu-id="6413d-168">You can improve the startup time of your .NET Core application by compiling your application assemblies as ReadyToRun (R2R) format.</span></span> <span data-ttu-id="6413d-169">R2R to forma kompilacji z wyprzedzeniem (AOT).</span><span class="sxs-lookup"><span data-stu-id="6413d-169">R2R is a form of ahead-of-time (AOT) compilation.</span></span>

<span data-ttu-id="6413d-170">Pliki binarne R2R zwiększają wydajność uruchamiania przez zmniejszenie ilości pracy kompilatora, który jest potrzebny do załadowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6413d-170">R2R binaries improve startup performance by reducing the amount of work the just-in-time (JIT) compiler needs to do as your application loads.</span></span> <span data-ttu-id="6413d-171">Pliki binarne zawierają podobny kod natywny w porównaniu z przeznaczeniem JIT.</span><span class="sxs-lookup"><span data-stu-id="6413d-171">The binaries contain similar native code compared to what the JIT would produce.</span></span> <span data-ttu-id="6413d-172">R2R pliki binarne są jednak większe, ponieważ zawierają kod języka pośredniego (IL), który jest nadal wymagany w niektórych scenariuszach i natywną wersję tego samego kodu.</span><span class="sxs-lookup"><span data-stu-id="6413d-172">However, R2R binaries are larger because they contain both intermediate language (IL) code, which is still needed for some scenarios, and the native version of the same code.</span></span> <span data-ttu-id="6413d-173">R2R jest dostępna tylko w przypadku publikowania aplikacji samodzielnej, która jest przeznaczona dla określonych środowisk uruchomieniowych (RID), takich jak Linux x64 lub Windows x64.</span><span class="sxs-lookup"><span data-stu-id="6413d-173">R2R is only available when you publish a self-contained app that targets specific runtime environments (RID) such as Linux x64 or Windows x64.</span></span>

<span data-ttu-id="6413d-174">Aby skompilować projekt jako ReadyToRun, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="6413d-174">To compile your project as ReadyToRun, do the following:</span></span>

01. <span data-ttu-id="6413d-175">Dodaj do projektu ustawienie `<PublishReadyToRun>`:</span><span class="sxs-lookup"><span data-stu-id="6413d-175">Add the `<PublishReadyToRun>` setting to your project:</span></span>

    ```xml
    <PropertyGroup>
      <PublishReadyToRun>true</PublishReadyToRun>
    </PropertyGroup>
    ```

01. <span data-ttu-id="6413d-176">Publikowanie aplikacji samodzielnej.</span><span class="sxs-lookup"><span data-stu-id="6413d-176">Publish a self-contained app.</span></span> <span data-ttu-id="6413d-177">Na przykład to polecenie tworzy samodzielną aplikację dla 64-bitowej wersji systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="6413d-177">For example, this command creates a self-contained app for the 64-bit version of Windows:</span></span>

    ```dotnetcli
    dotnet publish -c Release -r win-x64 --self-contained
    ```

#### <a name="cross-platformarchitecture-restrictions"></a><span data-ttu-id="6413d-178">Ograniczenia dotyczące wielu platform/architektury</span><span class="sxs-lookup"><span data-stu-id="6413d-178">Cross platform/architecture restrictions</span></span>

<span data-ttu-id="6413d-179">Kompilator ReadyToRun nie obsługuje obecnie określania wartości docelowej.</span><span class="sxs-lookup"><span data-stu-id="6413d-179">The ReadyToRun compiler doesn't currently support cross-targeting.</span></span> <span data-ttu-id="6413d-180">Należy skompilować na danym miejscu docelowym.</span><span class="sxs-lookup"><span data-stu-id="6413d-180">You must compile on a given target.</span></span> <span data-ttu-id="6413d-181">Na przykład jeśli chcesz, aby obrazy R2R dla systemu Windows x64 zostały wykonane, należy uruchomić polecenie Publikuj w tym środowisku.</span><span class="sxs-lookup"><span data-stu-id="6413d-181">For example, if you want R2R images for Windows x64, you need to run the publish command on that environment.</span></span>

<span data-ttu-id="6413d-182">Wyjątki dla wielu elementów docelowych:</span><span class="sxs-lookup"><span data-stu-id="6413d-182">Exceptions to cross-targeting:</span></span>

- <span data-ttu-id="6413d-183">System Windows x64 może służyć do kompilowania obrazów systemów Windows ARM32, ARM64 i x86.</span><span class="sxs-lookup"><span data-stu-id="6413d-183">Windows x64 can be used to compile Windows ARM32, ARM64, and x86 images.</span></span>
- <span data-ttu-id="6413d-184">System Windows x86 może służyć do kompilowania obrazów ARM32 systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="6413d-184">Windows x86 can be used to compile Windows ARM32 images.</span></span>
- <span data-ttu-id="6413d-185">System Linux x64 może służyć do kompilowania obrazów systemu Linux ARM32 i ARM64.</span><span class="sxs-lookup"><span data-stu-id="6413d-185">Linux x64 can be used to compile Linux ARM32 and ARM64 images.</span></span>

## <a name="runtimesdk"></a><span data-ttu-id="6413d-186">Środowisko uruchomieniowe/zestaw SDK</span><span class="sxs-lookup"><span data-stu-id="6413d-186">Runtime/SDK</span></span>

### <a name="major-version-roll-forward"></a><span data-ttu-id="6413d-187">Wersja główna — przekazanie do przodu</span><span class="sxs-lookup"><span data-stu-id="6413d-187">Major-version Roll Forward</span></span>

<span data-ttu-id="6413d-188">W programie .NET Core 3,0 wprowadzono funkcję wyboru, która pozwala aplikacji na przewinięcie do najnowszej wersji programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6413d-188">.NET Core 3.0 introduces an opt-in feature that allows your app to roll forward to the latest major version of .NET Core.</span></span> <span data-ttu-id="6413d-189">Ponadto zostało dodane nowe ustawienie służące do kontrolowania sposobu, w jaki przenoszone do przodu jest stosowane do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="6413d-189">Additionally, a new setting has been added to control how roll forward is applied to your app.</span></span> <span data-ttu-id="6413d-190">Tę konfigurację można skonfigurować w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="6413d-190">This can be configured in the following ways:</span></span>

- <span data-ttu-id="6413d-191">Właściwość pliku projektu: `RollForward`</span><span class="sxs-lookup"><span data-stu-id="6413d-191">Project file property: `RollForward`</span></span>
- <span data-ttu-id="6413d-192">Właściwość pliku konfiguracji środowiska uruchomieniowego: `rollForward`</span><span class="sxs-lookup"><span data-stu-id="6413d-192">Runtime configuration file property: `rollForward`</span></span>
- <span data-ttu-id="6413d-193">Zmienna środowiskowa: `DOTNET_ROLL_FORWARD`</span><span class="sxs-lookup"><span data-stu-id="6413d-193">Environment variable: `DOTNET_ROLL_FORWARD`</span></span>
- <span data-ttu-id="6413d-194">Argument wiersza polecenia: `--roll-forward`</span><span class="sxs-lookup"><span data-stu-id="6413d-194">Command-line argument: `--roll-forward`</span></span>

<span data-ttu-id="6413d-195">Należy określić jedną z następujących wartości.</span><span class="sxs-lookup"><span data-stu-id="6413d-195">One of the following values must be specified.</span></span> <span data-ttu-id="6413d-196">Jeśli ustawienie zostanie pominięte, wartością domyślną jest wartość **pomocnicza** .</span><span class="sxs-lookup"><span data-stu-id="6413d-196">If the setting is omitted, **Minor** is the default.</span></span>

- <span data-ttu-id="6413d-197">**LatestPatch**</span><span class="sxs-lookup"><span data-stu-id="6413d-197">**LatestPatch**</span></span>\
<span data-ttu-id="6413d-198">Przewinięcie do najwyższej wersji poprawki.</span><span class="sxs-lookup"><span data-stu-id="6413d-198">Roll forward to the highest patch version.</span></span> <span data-ttu-id="6413d-199">Spowoduje to wyłączenie wycofywania wersji pomocniczej.</span><span class="sxs-lookup"><span data-stu-id="6413d-199">This disables minor version roll forward.</span></span>
- <span data-ttu-id="6413d-200">\ **pomocnicze**</span><span class="sxs-lookup"><span data-stu-id="6413d-200">**Minor**\</span></span>
<span data-ttu-id="6413d-201">Przewinięcie do najmniejszej wyższej wersji pomocniczej, jeśli brakuje wymaganej wersji pomocniczej.</span><span class="sxs-lookup"><span data-stu-id="6413d-201">Roll forward to the lowest higher minor version, if requested minor version is missing.</span></span> <span data-ttu-id="6413d-202">Jeśli jest obecna żądana wersja pomocnicza, zostaną użyte zasady **LatestPatch** .</span><span class="sxs-lookup"><span data-stu-id="6413d-202">If the requested minor version is present, then the **LatestPatch** policy is used.</span></span>
- <span data-ttu-id="6413d-203">\ **Główne**</span><span class="sxs-lookup"><span data-stu-id="6413d-203">**Major**\</span></span>
<span data-ttu-id="6413d-204">Zaczekaj na najmniejszą wyższą wersję główną i najniższą wersję pomocniczą, jeśli brakuje żądanej wersji głównej.</span><span class="sxs-lookup"><span data-stu-id="6413d-204">Roll forward to lowest higher major version, and lowest minor version, if requested major version is missing.</span></span> <span data-ttu-id="6413d-205">Jeśli jest obecna żądana wersja główna, są używane zasady **pomocnicze** .</span><span class="sxs-lookup"><span data-stu-id="6413d-205">If the requested major version is present, then the **Minor** policy is used.</span></span>
- <span data-ttu-id="6413d-206">**LatestMinor**</span><span class="sxs-lookup"><span data-stu-id="6413d-206">**LatestMinor**</span></span>\
<span data-ttu-id="6413d-207">Przewinięcie do przodu do najwyższej wersji pomocniczej, nawet jeśli jest obecna żądana wersja pomocnicza.</span><span class="sxs-lookup"><span data-stu-id="6413d-207">Roll forward to highest minor version, even if requested minor version is present.</span></span> <span data-ttu-id="6413d-208">Przeznaczone do scenariuszy hostingu składników.</span><span class="sxs-lookup"><span data-stu-id="6413d-208">Intended for component hosting scenarios.</span></span>
- <span data-ttu-id="6413d-209">**LatestMajor**</span><span class="sxs-lookup"><span data-stu-id="6413d-209">**LatestMajor**</span></span>\
<span data-ttu-id="6413d-210">Przewinięcie do przodu do najwyższej głównej i najwyższej wersji pomocniczej, nawet jeśli jest obecny żądany główny.</span><span class="sxs-lookup"><span data-stu-id="6413d-210">Roll forward to highest major and highest minor version, even if requested major is present.</span></span> <span data-ttu-id="6413d-211">Przeznaczone do scenariuszy hostingu składników.</span><span class="sxs-lookup"><span data-stu-id="6413d-211">Intended for component hosting scenarios.</span></span>
- <span data-ttu-id="6413d-212">**Wyłącz**</span><span class="sxs-lookup"><span data-stu-id="6413d-212">**Disable**</span></span>\
<span data-ttu-id="6413d-213">Nie przetaczaj dalej.</span><span class="sxs-lookup"><span data-stu-id="6413d-213">Don't roll forward.</span></span> <span data-ttu-id="6413d-214">Powiąż tylko z określoną wersją.</span><span class="sxs-lookup"><span data-stu-id="6413d-214">Only bind to specified version.</span></span> <span data-ttu-id="6413d-215">Te zasady nie są zalecane do użytku ogólnego, ponieważ uniemożliwiają one przekazanie do najnowszych poprawek.</span><span class="sxs-lookup"><span data-stu-id="6413d-215">This policy isn't recommended for general use because it disables the ability to roll forward to the latest patches.</span></span> <span data-ttu-id="6413d-216">Ta wartość jest zalecana tylko do celów testowych.</span><span class="sxs-lookup"><span data-stu-id="6413d-216">This value is only recommended for testing.</span></span>

<span data-ttu-id="6413d-217">Oprócz ustawienia **Wyłącz** wszystkie ustawienia będą używać najwyższej dostępnej wersji poprawki.</span><span class="sxs-lookup"><span data-stu-id="6413d-217">Besides the **Disable** setting, all settings will use the highest available patch version.</span></span>

### <a name="build-copies-dependencies"></a><span data-ttu-id="6413d-218">Zależności kompilacji kopii</span><span class="sxs-lookup"><span data-stu-id="6413d-218">Build copies dependencies</span></span>

<span data-ttu-id="6413d-219">Polecenie `dotnet build` kopiuje teraz zależności NuGet dla aplikacji z pamięci podręcznej NuGet do folderu danych wyjściowych kompilacji.</span><span class="sxs-lookup"><span data-stu-id="6413d-219">The `dotnet build` command now copies NuGet dependencies for your application from the NuGet cache to the build output folder.</span></span> <span data-ttu-id="6413d-220">Wcześniej zależności były kopiowane tylko w ramach `dotnet publish`.</span><span class="sxs-lookup"><span data-stu-id="6413d-220">Previously, dependencies were only copied as part of `dotnet publish`.</span></span>

<span data-ttu-id="6413d-221">Istnieją pewne operacje, takie jak łączenie i publikowanie stron Razor, które nadal wymagają publikacji.</span><span class="sxs-lookup"><span data-stu-id="6413d-221">There are some operations, like linking and razor page publishing that will still require publishing.</span></span>

### <a name="local-tools"></a><span data-ttu-id="6413d-222">Narzędzia lokalne</span><span class="sxs-lookup"><span data-stu-id="6413d-222">Local tools</span></span>

<span data-ttu-id="6413d-223">Środowisko .NET Core 3,0 zawiera wprowadzenie do narzędzi lokalnych.</span><span class="sxs-lookup"><span data-stu-id="6413d-223">.NET Core 3.0 introduces local tools.</span></span> <span data-ttu-id="6413d-224">Narzędzia lokalne są podobne do [narzędzi globalnych](../tools/global-tools.md) , ale są skojarzone z konkretną lokalizacją na dysku.</span><span class="sxs-lookup"><span data-stu-id="6413d-224">Local tools are similar to [global tools](../tools/global-tools.md) but are associated with a particular location on disk.</span></span> <span data-ttu-id="6413d-225">Narzędzia lokalne nie są dostępne globalnie i są dystrybuowane jako pakiety NuGet.</span><span class="sxs-lookup"><span data-stu-id="6413d-225">Local tools aren't available globally and are distributed as NuGet packages.</span></span>

> [!WARNING]
> <span data-ttu-id="6413d-226">Jeśli podjęto próbę skorzystania z narzędzi lokalnych w programie .NET Core 3,0 w wersji zapoznawczej 1, takiej jak uruchamianie `dotnet tool restore` lub `dotnet tool install`, Usuń folder pamięci podręcznej narzędzi lokalnych.</span><span class="sxs-lookup"><span data-stu-id="6413d-226">If you tried local tools in .NET Core 3.0 Preview 1, such as running `dotnet tool restore` or `dotnet tool install`, delete the local tools cache folder.</span></span> <span data-ttu-id="6413d-227">W przeciwnym razie narzędzia lokalne nie będą działały w żadnej nowszej wersji.</span><span class="sxs-lookup"><span data-stu-id="6413d-227">Otherwise, local tools won't work on any newer release.</span></span> <span data-ttu-id="6413d-228">Ten folder znajduje się w lokalizacji:</span><span class="sxs-lookup"><span data-stu-id="6413d-228">This folder is located at:</span></span>
>
> <span data-ttu-id="6413d-229">W systemie macOS, Linux: `rm -r $HOME/.dotnet/toolResolverCache`</span><span class="sxs-lookup"><span data-stu-id="6413d-229">On macOS, Linux: `rm -r $HOME/.dotnet/toolResolverCache`</span></span>
>
> <span data-ttu-id="6413d-230">W systemie Windows: `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`</span><span class="sxs-lookup"><span data-stu-id="6413d-230">On Windows: `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`</span></span>

<span data-ttu-id="6413d-231">Narzędzia lokalne polegają na nazwach plików manifestu `dotnet-tools.json` w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="6413d-231">Local tools rely on a manifest file name `dotnet-tools.json` in your current directory.</span></span> <span data-ttu-id="6413d-232">Ten plik manifestu definiuje narzędzia do udostępnienia w tym folderze i poniżej.</span><span class="sxs-lookup"><span data-stu-id="6413d-232">This manifest file defines the tools to be available at that folder and below.</span></span> <span data-ttu-id="6413d-233">Plik manifestu można dystrybuować z kodem, aby upewnić się, że każda osoba, która współpracuje z kodem, będzie mogła przywrócić i korzystać z tych samych narzędzi.</span><span class="sxs-lookup"><span data-stu-id="6413d-233">You can distribute the manifest file with your code to ensure that anyone who works with your code can restore and use the same tools.</span></span>

<span data-ttu-id="6413d-234">W przypadku narzędzi globalnych i lokalnych wymagana jest zgodna wersja środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="6413d-234">For both global and local tools, a compatible version of the runtime is required.</span></span> <span data-ttu-id="6413d-235">Wiele narzędzi obecnie na NuGet.org docelowym środowiska uruchomieniowego .NET Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="6413d-235">Many tools currently on NuGet.org target .NET Core Runtime 2.1.</span></span> <span data-ttu-id="6413d-236">Aby zainstalować te narzędzia globalnie lub lokalnie, nadal trzeba zainstalować [środowisko uruchomieniowe NET Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="6413d-236">To install these tools globally or locally, you would still need to install the [NET Core 2.1 Runtime](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span>

### <a name="smaller-garbage-collection-heap-sizes"></a><span data-ttu-id="6413d-237">Mniejsze rozmiary sterty wyrzucania elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="6413d-237">Smaller Garbage Collection heap sizes</span></span>

<span data-ttu-id="6413d-238">Rozmiar sterty domyślnej modułu wyrzucania elementów bezużytecznych został zmniejszony z powodu mniejszej ilości pamięci w programie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6413d-238">The Garbage Collector's default heap size has been reduced resulting in .NET Core using less memory.</span></span> <span data-ttu-id="6413d-239">Ta zmiana jest lepsza w porównaniu z budżetem alokacji generacji 0 z nowoczesnymi rozmiarami pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="6413d-239">This change better aligns with the generation 0 allocation budget with modern processor cache sizes.</span></span>

### <a name="garbage-collection-large-page-support"></a><span data-ttu-id="6413d-240">Obsługa dużej strony odzyskiwania pamięci</span><span class="sxs-lookup"><span data-stu-id="6413d-240">Garbage Collection Large Page support</span></span>

<span data-ttu-id="6413d-241">Duże strony (znane również jako ogromne strony w systemie Linux) to funkcja, w której system operacyjny może ustalić obszary pamięci większe niż rozmiar strony natywnej (często 4K), aby zwiększyć wydajność aplikacji żądającej tych dużych stron.</span><span class="sxs-lookup"><span data-stu-id="6413d-241">Large Pages (also known as Huge Pages on Linux) is a feature where the operating system is able to establish memory regions larger than the native page size (often 4K) to improve performance of the application requesting these large pages.</span></span>

<span data-ttu-id="6413d-242">Moduł wyrzucania elementów bezużytecznych można teraz skonfigurować przy użyciu ustawienia **GCLargePages** jako funkcji wyboru do przydzielania dużych stron w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="6413d-242">The Garbage Collector can now be configured with the **GCLargePages** setting as an opt-in feature to choose to allocate large pages on Windows.</span></span>

## <a name="windows-desktop--com"></a><span data-ttu-id="6413d-243">Windows Desktop & COM</span><span class="sxs-lookup"><span data-stu-id="6413d-243">Windows Desktop & COM</span></span>

### <a name="net-core-sdk-windows-installer"></a><span data-ttu-id="6413d-244">Zestaw .NET Core SDK Instalator Windows</span><span class="sxs-lookup"><span data-stu-id="6413d-244">.NET Core SDK Windows Installer</span></span>

<span data-ttu-id="6413d-245">Instalator MSI dla systemu Windows został zmieniony począwszy od platformy .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="6413d-245">The MSI installer for Windows has changed starting with .NET Core 3.0.</span></span> <span data-ttu-id="6413d-246">Instalatorzy zestawu SDK teraz uaktualniają wersje funkcji zestawu SDK na miejscu.</span><span class="sxs-lookup"><span data-stu-id="6413d-246">The SDK installers will now upgrade SDK feature-band releases in place.</span></span> <span data-ttu-id="6413d-247">Paski funkcji są zdefiniowane w grupach *setek* w sekcji *poprawka* numeru wersji.</span><span class="sxs-lookup"><span data-stu-id="6413d-247">Feature bands are defined in the *hundreds* groups in the *patch* section of the version number.</span></span> <span data-ttu-id="6413d-248">Na przykład **3,0. _101_**  i **3,0. _201_**  są wersje w dwóch różnych warstwach funkcji podczas **3,0. _101_**  i **3,0. _199_**  znajdują się w tej samej paśmie funkcji.</span><span class="sxs-lookup"><span data-stu-id="6413d-248">For example, **3.0._101_** and **3.0._201_** are versions in two different feature bands while **3.0._101_** and **3.0._199_** are in the same feature band.</span></span> <span data-ttu-id="6413d-249">I, w przypadku zestaw .NET Core SDK **3,0. _101_**  jest zainstalowana, zestaw .NET Core SDK **3,0. _100_**  zostanie usunięta z komputera, jeśli istnieje.</span><span class="sxs-lookup"><span data-stu-id="6413d-249">And, when .NET Core SDK **3.0._101_** is installed, .NET Core SDK **3.0._100_** will be removed from the machine if it exists.</span></span> <span data-ttu-id="6413d-250">Gdy zestaw .NET Core SDK **3,0. _200_**  jest zainstalowana na tym samym komputerze, zestaw .NET Core SDK **3,0. _101_**  nie zostanie usunięta.</span><span class="sxs-lookup"><span data-stu-id="6413d-250">When .NET Core SDK **3.0._200_** is installed on the same machine, .NET Core SDK **3.0._101_** won't be removed.</span></span>

<span data-ttu-id="6413d-251">Aby uzyskać więcej informacji na temat przechowywania wersji, zobacz [Omówienie wersji platformy .NET Core](../versions/index.md).</span><span class="sxs-lookup"><span data-stu-id="6413d-251">For more information about versioning, see [Overview of how .NET Core is versioned](../versions/index.md).</span></span>

### <a name="windows-desktop"></a><span data-ttu-id="6413d-252">Pulpit systemu Windows</span><span class="sxs-lookup"><span data-stu-id="6413d-252">Windows desktop</span></span>

<span data-ttu-id="6413d-253">Program .NET Core 3,0 obsługuje aplikacje klasyczne systemu Windows przy użyciu Windows Presentation Foundation (WPF) i Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="6413d-253">.NET Core 3.0 supports Windows desktop applications using Windows Presentation Foundation (WPF) and Windows Forms.</span></span> <span data-ttu-id="6413d-254">Te struktury obsługują również korzystanie z nowoczesnych kontrolek i stylów Fluent z poziomu biblioteki XAML interfejsu użytkownika systemu Windows (WinUI) za pośrednictwem [wysp XAML](/windows/uwp/xaml-platform/xaml-host-controls).</span><span class="sxs-lookup"><span data-stu-id="6413d-254">These frameworks also support using modern controls and Fluent styling from the Windows UI XAML Library (WinUI) via [XAML islands](/windows/uwp/xaml-platform/xaml-host-controls).</span></span>

<span data-ttu-id="6413d-255">Składnik pulpitu systemu Windows jest częścią zestawu SDK systemu Windows .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="6413d-255">The Windows Desktop component is part of the Windows .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="6413d-256">Nową aplikację WPF lub Windows Forms można utworzyć przy użyciu następujących poleceń `dotnet`:</span><span class="sxs-lookup"><span data-stu-id="6413d-256">You can create a new WPF or Windows Forms app with the following `dotnet` commands:</span></span>

```dotnetcli
dotnet new wpf
dotnet new winforms
```

<span data-ttu-id="6413d-257">Program Visual Studio 2019 dodaje **nowe szablony projektów** dla platformy .net Core 3,0 Windows Forms i WPF.</span><span class="sxs-lookup"><span data-stu-id="6413d-257">Visual Studio 2019 adds **New Project** templates for .NET Core 3.0 Windows Forms and WPF.</span></span>

<span data-ttu-id="6413d-258">Aby uzyskać więcej informacji na temat sposobu przenoszenia istniejącej aplikacji .NET Framework, zobacz [port WPF projekty](../../desktop-wpf/migration/convert-project-from-net-framework.md) i [projekty Windows Forms portów](../porting/winforms.md).</span><span class="sxs-lookup"><span data-stu-id="6413d-258">For more information about how to port an existing .NET Framework application, see [Port WPF projects](../../desktop-wpf/migration/convert-project-from-net-framework.md) and [Port Windows Forms projects](../porting/winforms.md).</span></span>

#### <a name="winforms-high-dpi"></a><span data-ttu-id="6413d-259">Bardzo wysokie wartości DPI</span><span class="sxs-lookup"><span data-stu-id="6413d-259">WinForms high DPI</span></span>

<span data-ttu-id="6413d-260">Aplikacje .NET Core Windows Forms mogą ustawiać tryb wysokiej rozdzielczości DPI z <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6413d-260">.NET Core Windows Forms applications can set high DPI mode with <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6413d-261">Metoda `SetHighDpiMode` ustawia odpowiedni tryb wysokiej rozdzielczości DPI, chyba że ustawienie zostało ustawione w inny sposób, na przykład `App.Manifest` lub P/Invoke przed `Application.Run`.</span><span class="sxs-lookup"><span data-stu-id="6413d-261">The `SetHighDpiMode` method sets the corresponding high DPI mode unless the setting has been set by other means like `App.Manifest` or P/Invoke before `Application.Run`.</span></span>

<span data-ttu-id="6413d-262">Możliwe wartości `highDpiMode` wyrażone przez Wyliczenie <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType> są następujące:</span><span class="sxs-lookup"><span data-stu-id="6413d-262">The possible `highDpiMode` values, as expressed by the <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType> enum are:</span></span>

- `DpiUnaware`
- `SystemAware`
- `PerMonitor`
- `PerMonitorV2`
- `DpiUnawareGdiScaled`

<span data-ttu-id="6413d-263">Aby uzyskać więcej informacji na temat trybów wysokiej rozdzielczości DPI, zobacz [Tworzenie aplikacji klasycznych o wysokiej rozdzielczości DPI w systemie Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows).</span><span class="sxs-lookup"><span data-stu-id="6413d-263">For more information about high DPI modes, see [High DPI Desktop Application Development on Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows).</span></span>

### <a name="create-com-components"></a><span data-ttu-id="6413d-264">Tworzenie składników COM</span><span class="sxs-lookup"><span data-stu-id="6413d-264">Create COM components</span></span>

<span data-ttu-id="6413d-265">W systemie Windows można teraz tworzyć zarządzane składniki COM.</span><span class="sxs-lookup"><span data-stu-id="6413d-265">On Windows, you can now create COM-callable managed components.</span></span> <span data-ttu-id="6413d-266">Ta funkcja ma kluczowe znaczenie dla korzystania z platformy .NET Core z modelami dodatków COM, a także do zapewnienia parzystości .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6413d-266">This capability is critical to use .NET Core with COM add-in models and also to provide parity with .NET Framework.</span></span>

<span data-ttu-id="6413d-267">W przeciwieństwie do .NET Framework, w którym *Biblioteka mscoree. dll* była używana jako serwer com, podczas kompilowania składnika com program .NET Core doda natywną bibliotekę DLL uruchamiania do katalogu *bin* .</span><span class="sxs-lookup"><span data-stu-id="6413d-267">Unlike .NET Framework where the *mscoree.dll* was used as the COM server, .NET Core will add a native launcher dll to the *bin* directory when you build your COM component.</span></span>

<span data-ttu-id="6413d-268">Przykład sposobu tworzenia składnika modelu COM i korzystania z niego można znaleźć w [demonstracji modelu COM](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).</span><span class="sxs-lookup"><span data-stu-id="6413d-268">For an example of how to create a COM component and consume it, see the [COM Demo](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).</span></span>

### <a name="windows-native-interop"></a><span data-ttu-id="6413d-269">Windows Native Interop</span><span class="sxs-lookup"><span data-stu-id="6413d-269">Windows Native Interop</span></span>

<span data-ttu-id="6413d-270">System Windows oferuje bogaty natywny interfejs API w postaci prostych interfejsów API języka C, COM i WinRT.</span><span class="sxs-lookup"><span data-stu-id="6413d-270">Windows offers a rich native API in the form of flat C APIs, COM, and WinRT.</span></span> <span data-ttu-id="6413d-271">Podczas gdy platforma .NET Core obsługuje funkcję **P/Invoke**, program .net Core 3,0 dodaje możliwość **CoCreate interfejsów API modelu COM** i **aktywowania interfejsów API WinRT**.</span><span class="sxs-lookup"><span data-stu-id="6413d-271">While .NET Core supports **P/Invoke**, .NET Core 3.0 adds the ability to **CoCreate COM APIs** and **Activate WinRT APIs**.</span></span> <span data-ttu-id="6413d-272">Aby zapoznać się z przykładem kodu, zobacz [Demonstracja programu Excel](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).</span><span class="sxs-lookup"><span data-stu-id="6413d-272">For a code example, see the [Excel Demo](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).</span></span>

### <a name="msix-deployment"></a><span data-ttu-id="6413d-273">Wdrożenie MSIX</span><span class="sxs-lookup"><span data-stu-id="6413d-273">MSIX Deployment</span></span>

<span data-ttu-id="6413d-274">[MSIX](https://docs.microsoft.com/windows/msix/) to nowy format pakietu aplikacji systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="6413d-274">[MSIX](https://docs.microsoft.com/windows/msix/) is a new Windows application package format.</span></span> <span data-ttu-id="6413d-275">Można go użyć do wdrożenia aplikacji klasycznych platformy .NET Core 3,0 w systemie Windows 10.</span><span class="sxs-lookup"><span data-stu-id="6413d-275">It can be used to deploy .NET Core 3.0 desktop applications to Windows 10.</span></span>

<span data-ttu-id="6413d-276">[Projekt pakietu aplikacji systemu Windows](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), dostępny w programie Visual Studio 2019, umożliwia tworzenie pakietów MSIX przy użyciu [samodzielnych](../deploying/index.md#self-contained-deployments-scd) aplikacji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6413d-276">The [Windows Application Packaging Project](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), available in Visual Studio 2019, allows you to create MSIX packages with [self-contained](../deploying/index.md#self-contained-deployments-scd) .NET Core applications.</span></span>

<span data-ttu-id="6413d-277">Plik projektu .NET Core musi określać obsługiwane środowiska uruchomieniowe we właściwości `<RuntimeIdentifiers>`:</span><span class="sxs-lookup"><span data-stu-id="6413d-277">The .NET Core project file must specify the supported runtimes in the `<RuntimeIdentifiers>` property:</span></span>

```xml
<RuntimeIdentifiers>win-x86;win-x64</RuntimeIdentifiers>
```

## <a name="linux-improvements"></a><span data-ttu-id="6413d-278">Udoskonalenia systemu Linux</span><span class="sxs-lookup"><span data-stu-id="6413d-278">Linux improvements</span></span>

### <a name="serialport-for-linux"></a><span data-ttu-id="6413d-279">Klasy SerialPort dla systemu Linux</span><span class="sxs-lookup"><span data-stu-id="6413d-279">SerialPort for Linux</span></span>

<span data-ttu-id="6413d-280">Program .NET Core 3,0 zapewnia podstawową pomoc techniczną dla <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> w systemie Linux.</span><span class="sxs-lookup"><span data-stu-id="6413d-280">.NET Core 3.0 provides basic support for <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> on Linux.</span></span>

<span data-ttu-id="6413d-281">Wcześniej platforma .NET Core była obsługiwana tylko przy użyciu `SerialPort` w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="6413d-281">Previously, .NET Core only supported using `SerialPort` on Windows.</span></span>

<span data-ttu-id="6413d-282">Aby uzyskać więcej informacji o ograniczonej obsłudze portu szeregowego w systemie Linux, zobacz artykuł [dotyczący usługi GitHub #33146](https://github.com/dotnet/corefx/issues/33146).</span><span class="sxs-lookup"><span data-stu-id="6413d-282">For more information about the limited support for the serial port on Linux, see [GitHub issue #33146](https://github.com/dotnet/corefx/issues/33146).</span></span>

### <a name="docker-and-cgroup-memory-limits"></a><span data-ttu-id="6413d-283">Limity pamięci Docker i cgroup</span><span class="sxs-lookup"><span data-stu-id="6413d-283">Docker and cgroup memory Limits</span></span>

<span data-ttu-id="6413d-284">Uruchamianie programu .NET Core 3,0 w systemie Linux przy użyciu platformy Docker działa lepiej z limitami pamięci cgroup.</span><span class="sxs-lookup"><span data-stu-id="6413d-284">Running .NET Core 3.0 on Linux with Docker works better with cgroup memory limits.</span></span> <span data-ttu-id="6413d-285">Uruchamianie kontenera Docker z limitami pamięci, na przykład z `docker run -m`, zmienia sposób działania programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6413d-285">Running a Docker container with memory limits, such as with `docker run -m`, changes how .NET Core behaves.</span></span>

- <span data-ttu-id="6413d-286">Domyślny rozmiar sterty modułu wyrzucania elementów bezużytecznych (GC): maksymalnie 20 MB lub 75% limitu pamięci w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="6413d-286">Default Garbage Collector (GC) heap size: maximum of 20 mb or 75% of the memory limit on the container.</span></span>
- <span data-ttu-id="6413d-287">Rozmiar jawny można ustawić jako liczbę bezwzględną lub procent limitu cgroup.</span><span class="sxs-lookup"><span data-stu-id="6413d-287">Explicit size can be set as an absolute number or percentage of cgroup limit.</span></span>
- <span data-ttu-id="6413d-288">Minimalny zarezerwowany rozmiar segmentu na stos GC to 16 MB.</span><span class="sxs-lookup"><span data-stu-id="6413d-288">Minimum reserved segment size per GC heap is 16 mb.</span></span> <span data-ttu-id="6413d-289">Ten rozmiar zmniejsza liczbę stert, które są tworzone na maszynach.</span><span class="sxs-lookup"><span data-stu-id="6413d-289">This size reduces the number of heaps that are created on machines.</span></span>

### <a name="gpio-support-for-raspberry-pi"></a><span data-ttu-id="6413d-290">Obsługa interfejsu GPIO dla Raspberry Pi</span><span class="sxs-lookup"><span data-stu-id="6413d-290">GPIO Support for Raspberry Pi</span></span>

<span data-ttu-id="6413d-291">Do programu NuGet zostały wydane dwa pakiety, których można użyć do programowania interfejsu GPIO:</span><span class="sxs-lookup"><span data-stu-id="6413d-291">Two packages have been released to NuGet that you can use for GPIO programming:</span></span>

- [<span data-ttu-id="6413d-292">System. Device. GPIO</span><span class="sxs-lookup"><span data-stu-id="6413d-292">System.Device.Gpio</span></span>](https://www.nuget.org/packages/System.Device.Gpio)
- [<span data-ttu-id="6413d-293">IoT. Device. bindings</span><span class="sxs-lookup"><span data-stu-id="6413d-293">Iot.Device.Bindings</span></span>](https://www.nuget.org/packages/Iot.Device.Bindings)

<span data-ttu-id="6413d-294">Pakiety GPIO obejmują interfejsy API dla urządzeń z interfejsem *GPIO*, *SPI*, *I2C*i *PWM* .</span><span class="sxs-lookup"><span data-stu-id="6413d-294">The GPIO packages include APIs for *GPIO*, *SPI*, *I2C*, and *PWM* devices.</span></span> <span data-ttu-id="6413d-295">Pakiet powiązań IoT obejmuje powiązania urządzeń.</span><span class="sxs-lookup"><span data-stu-id="6413d-295">The IoT bindings package includes device bindings.</span></span> <span data-ttu-id="6413d-296">Aby uzyskać więcej informacji, zobacz [repozytorium GitHub](https://github.com/dotnet/iot/blob/master/src/devices/).</span><span class="sxs-lookup"><span data-stu-id="6413d-296">For more information, see the [devices GitHub repo](https://github.com/dotnet/iot/blob/master/src/devices/).</span></span>

### <a name="arm64-linux-support"></a><span data-ttu-id="6413d-297">Obsługa systemu Linux ARM64</span><span class="sxs-lookup"><span data-stu-id="6413d-297">ARM64 Linux support</span></span>

<span data-ttu-id="6413d-298">Program .NET Core 3,0 dodaje obsługę ARM64 dla systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="6413d-298">.NET Core 3.0 adds support for ARM64 for Linux.</span></span> <span data-ttu-id="6413d-299">Podstawowy przypadek użycia dla ARM64 jest obecnie z scenariuszami IoT.</span><span class="sxs-lookup"><span data-stu-id="6413d-299">The primary use case for ARM64 is currently with IoT scenarios.</span></span> <span data-ttu-id="6413d-300">Aby uzyskać więcej informacji, zobacz temat [stan arm64 programu .NET Core](https://github.com/dotnet/announcements/issues/82).</span><span class="sxs-lookup"><span data-stu-id="6413d-300">For more information, see [.NET Core ARM64 Status](https://github.com/dotnet/announcements/issues/82).</span></span>

<span data-ttu-id="6413d-301">[Obrazy Docker dla platformy .NET Core w systemie arm64](https://hub.docker.com/r/microsoft/dotnet/) są dostępne dla Alpine, Debian i Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="6413d-301">[Docker images for .NET Core on ARM64](https://hub.docker.com/r/microsoft/dotnet/) are available for Alpine, Debian, and Ubuntu.</span></span>

> [!NOTE]
> <span data-ttu-id="6413d-302">**Arm64** Obsługa systemu Windows nie jest jeszcze dostępna.</span><span class="sxs-lookup"><span data-stu-id="6413d-302">**ARM64** Windows support isn't yet available.</span></span>

## <a name="security"></a><span data-ttu-id="6413d-303">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="6413d-303">Security</span></span>

### <a name="tls-13--openssl-111-on-linux"></a><span data-ttu-id="6413d-304">TLS 1,3 & OpenSSL 1.1.1 w systemie Linux</span><span class="sxs-lookup"><span data-stu-id="6413d-304">TLS 1.3 & OpenSSL 1.1.1 on Linux</span></span>

<span data-ttu-id="6413d-305">Platforma .NET Core wykorzystuje teraz zalety [protokołu TLS 1,3 w OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), gdy jest on dostępny w danym środowisku.</span><span class="sxs-lookup"><span data-stu-id="6413d-305">.NET Core now takes advantage of [TLS 1.3 support in OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), when it's available in a given environment.</span></span> <span data-ttu-id="6413d-306">Z protokołem TLS 1,3:</span><span class="sxs-lookup"><span data-stu-id="6413d-306">With TLS 1.3:</span></span>

- <span data-ttu-id="6413d-307">Czas połączenia jest ulepszony ze zredukowanymi przedziałami rundy między klientem i serwerem.</span><span class="sxs-lookup"><span data-stu-id="6413d-307">Connection times are improved with reduced round trips required between the client and server.</span></span>
- <span data-ttu-id="6413d-308">Ulepszone zabezpieczenia spowodowane usuwaniem różnych przestarzałych i niezabezpieczonych algorytmów kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="6413d-308">Improved security because of the removal of various obsolete and insecure cryptographic algorithms.</span></span>

<span data-ttu-id="6413d-309">Jeśli jest dostępny, program .NET Core 3,0 używa **OpenSSL 1.1.1**, **OpenSSL 1.1.0**lub **OpenSSL 1.0.2** w systemie Linux.</span><span class="sxs-lookup"><span data-stu-id="6413d-309">When available, .NET Core 3.0 uses **OpenSSL 1.1.1**, **OpenSSL 1.1.0**, or **OpenSSL 1.0.2** on a Linux system.</span></span> <span data-ttu-id="6413d-310">Gdy **OpenSSL 1.1.1** jest dostępny, typy <xref:System.Net.Security.SslStream?displayProperty=nameWithType> i <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> będą używały **protokołu TLS 1,3** (przy założeniu, że zarówno klient, jak i serwer obsługują **protokół TLS 1,3**).</span><span class="sxs-lookup"><span data-stu-id="6413d-310">When **OpenSSL 1.1.1** is available, both <xref:System.Net.Security.SslStream?displayProperty=nameWithType> and <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> types will use **TLS 1.3** (assuming both the client and server support **TLS 1.3**).</span></span>

>[!IMPORTANT]
><span data-ttu-id="6413d-311">Systemy Windows i macOS nie obsługują jeszcze **protokołu TLS 1,3**.</span><span class="sxs-lookup"><span data-stu-id="6413d-311">Windows and macOS do not yet support **TLS 1.3**.</span></span> <span data-ttu-id="6413d-312">Platforma .NET Core 3,0 będzie obsługiwać **protokół TLS 1,3** w tych systemach operacyjnych, gdy będzie dostępna pomoc techniczna.</span><span class="sxs-lookup"><span data-stu-id="6413d-312">.NET Core 3.0 will support **TLS 1.3** on these operating systems when support becomes available.</span></span>

<span data-ttu-id="6413d-313">Poniższy C# przykład 8,0 ilustruje platformę .net Core 3,0 na Ubuntu 18,10 z <https://www.cloudflare.com>:</span><span class="sxs-lookup"><span data-stu-id="6413d-313">The following C# 8.0 example demonstrates .NET Core 3.0 on Ubuntu 18.10 connecting to <https://www.cloudflare.com>:</span></span>

[!CODE-csharp[TLSExample](~/samples/snippets/core/whats-new/whats-new-in-30/cs/TLS.cs#TLS)]

### <a name="cryptography-ciphers"></a><span data-ttu-id="6413d-314">Szyfrowanie kryptografii</span><span class="sxs-lookup"><span data-stu-id="6413d-314">Cryptography ciphers</span></span>

<span data-ttu-id="6413d-315">Program .NET 3,0 dodaje obsługę szyfrów **AES-GCM** i **AES-CCM** , wdrożonych odpowiednio przy użyciu <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> i <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6413d-315">.NET 3.0 adds support for **AES-GCM** and **AES-CCM** ciphers, implemented with <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> and <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> respectively.</span></span> <span data-ttu-id="6413d-316">Te algorytmy są [uwierzytelnianiem uwierzytelnianym przy użyciu algorytmów danych skojarzenia (AEAD)](https://en.wikipedia.org/wiki/Authenticated_encryption).</span><span class="sxs-lookup"><span data-stu-id="6413d-316">These algorithms are both [Authenticated Encryption with Association Data (AEAD) algorithms](https://en.wikipedia.org/wiki/Authenticated_encryption).</span></span>

<span data-ttu-id="6413d-317">Poniższy kod ilustruje użycie szyfru `AesGcm` do szyfrowania i odszyfrowywania danych losowych.</span><span class="sxs-lookup"><span data-stu-id="6413d-317">The following code demonstrates using `AesGcm` cipher to encrypt and decrypt random data.</span></span>

[!CODE-csharp[AesGcm](~/samples/snippets/core/whats-new/whats-new-in-30/cs/Cipher.cs#AesGcm)]

### <a name="cryptographic-key-importexport"></a><span data-ttu-id="6413d-318">Import/Eksport klucza kryptograficznego</span><span class="sxs-lookup"><span data-stu-id="6413d-318">Cryptographic Key Import/Export</span></span>

<span data-ttu-id="6413d-319">Program .NET Core 3,0 obsługuje importowanie i eksportowanie asymetrycznych kluczy publicznych i prywatnych z formatów standardowych.</span><span class="sxs-lookup"><span data-stu-id="6413d-319">.NET Core 3.0 supports the import and export of asymmetric public and private keys from standard formats.</span></span> <span data-ttu-id="6413d-320">Nie musisz używać certyfikatu X. 509.</span><span class="sxs-lookup"><span data-stu-id="6413d-320">You don't need to use an X.509 certificate.</span></span>

<span data-ttu-id="6413d-321">Wszystkie typy kluczy, takie jak *RSA*, *DSA*, *ECDSA*i *ECDiffieHellman*, obsługują następujące formaty:</span><span class="sxs-lookup"><span data-stu-id="6413d-321">All key types, such as *RSA*, *DSA*, *ECDsa*, and *ECDiffieHellman*, support the following formats:</span></span>

- <span data-ttu-id="6413d-322">**Klucz publiczny**</span><span class="sxs-lookup"><span data-stu-id="6413d-322">**Public Key**</span></span>
  - <span data-ttu-id="6413d-323">SubjectPublicKeyInfo X. 509</span><span class="sxs-lookup"><span data-stu-id="6413d-323">X.509 SubjectPublicKeyInfo</span></span>

- <span data-ttu-id="6413d-324">**Klucz prywatny**</span><span class="sxs-lookup"><span data-stu-id="6413d-324">**Private key**</span></span>
  - <span data-ttu-id="6413d-325">PrivateKeyInfo PKCS # 8</span><span class="sxs-lookup"><span data-stu-id="6413d-325">PKCS#8 PrivateKeyInfo</span></span>
  - <span data-ttu-id="6413d-326">EncryptedPrivateKeyInfo PKCS # 8</span><span class="sxs-lookup"><span data-stu-id="6413d-326">PKCS#8 EncryptedPrivateKeyInfo</span></span>

<span data-ttu-id="6413d-327">Klucze RSA obsługują również:</span><span class="sxs-lookup"><span data-stu-id="6413d-327">RSA keys also support:</span></span>

- <span data-ttu-id="6413d-328">**Klucz publiczny**</span><span class="sxs-lookup"><span data-stu-id="6413d-328">**Public Key**</span></span>
  - <span data-ttu-id="6413d-329">RSAPublicKey PKCS # 1</span><span class="sxs-lookup"><span data-stu-id="6413d-329">PKCS#1 RSAPublicKey</span></span>

- <span data-ttu-id="6413d-330">**Klucz prywatny**</span><span class="sxs-lookup"><span data-stu-id="6413d-330">**Private key**</span></span>
  - <span data-ttu-id="6413d-331">RSAPrivateKey PKCS # 1</span><span class="sxs-lookup"><span data-stu-id="6413d-331">PKCS#1 RSAPrivateKey</span></span>

<span data-ttu-id="6413d-332">Metody eksportowania generują dane binarne kodowane algorytmem DER, a metody importowe oczekują na to samo.</span><span class="sxs-lookup"><span data-stu-id="6413d-332">The export methods produce DER-encoded binary data, and the import methods expect the same.</span></span> <span data-ttu-id="6413d-333">Jeśli klucz jest przechowywany w formacie PEM przyjaznym dla tekstu, wywołujący będzie musiał odkodować zawartość przed wywołaniem metody Import.</span><span class="sxs-lookup"><span data-stu-id="6413d-333">If a key is stored in the text-friendly PEM format, the caller will need to base64-decode the content before calling an import method.</span></span>

[!CODE-csharp[RSA](~/samples/snippets/core/whats-new/whats-new-in-30/cs/RSA.cs#Rsa)]

<span data-ttu-id="6413d-334">Pliki **PKCS # 8** można sprawdzić za pomocą plików <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType>, a pliki **PFX/PKCS # 12** można sprawdzić za pomocą <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6413d-334">**PKCS#8** files can be inspected with <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType> and **PFX/PKCS#12** files can be inspected with <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6413d-335">Pliki **PFX/PKCS # 12** można manipulować przy użyciu <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6413d-335">**PFX/PKCS#12** files can be manipulated with <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType>.</span></span>

## <a name="net-core-30-api-changes"></a><span data-ttu-id="6413d-336">Zmiany interfejsu API programu .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="6413d-336">.NET Core 3.0 API changes</span></span>

### <a name="ranges-and-indices"></a><span data-ttu-id="6413d-337">Zakresy i indeksy</span><span class="sxs-lookup"><span data-stu-id="6413d-337">Ranges and indices</span></span>

<span data-ttu-id="6413d-338">Nowy typ <xref:System.Index?displayProperty=nameWithType> może służyć do indeksowania.</span><span class="sxs-lookup"><span data-stu-id="6413d-338">The new <xref:System.Index?displayProperty=nameWithType> type can be used for indexing.</span></span> <span data-ttu-id="6413d-339">Można utworzyć jeden z `int`, który liczy od początku lub z prefiksem `^` (C#), który liczy się od końca:</span><span class="sxs-lookup"><span data-stu-id="6413d-339">You can create one from an `int` that counts from the beginning, or with a prefix `^` operator (C#) that counts from the end:</span></span>

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

<span data-ttu-id="6413d-340">Istnieje również typ <xref:System.Range?displayProperty=nameWithType>, który składa się z dwóch wartości `Index`, jeden dla początku i jeden dla końca, i może być zapisany przy użyciu wyrażenia zakresu `x..y` (C#).</span><span class="sxs-lookup"><span data-stu-id="6413d-340">There's also the <xref:System.Range?displayProperty=nameWithType> type, which consists of two `Index` values, one for the start and one for the end, and can be written with a `x..y` range expression (C#).</span></span> <span data-ttu-id="6413d-341">Następnie można indeksować za pomocą `Range`, co powoduje utworzenie wycinka:</span><span class="sxs-lookup"><span data-stu-id="6413d-341">You can then index with a `Range`, which produces a slice:</span></span>

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

<span data-ttu-id="6413d-342">Aby uzyskać więcej informacji, zobacz [Samouczek dotyczący zakresów i indeksów](../../csharp/tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="6413d-342">For more information, see the [ranges and indices tutorial](../../csharp/tutorials/ranges-indexes.md).</span></span>

### <a name="async-streams"></a><span data-ttu-id="6413d-343">Strumienie asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="6413d-343">Async streams</span></span>

<span data-ttu-id="6413d-344">Typ <xref:System.Collections.Generic.IAsyncEnumerable%601> to nowa asynchroniczna wersja <xref:System.Collections.Generic.IEnumerable%601>.</span><span class="sxs-lookup"><span data-stu-id="6413d-344">The <xref:System.Collections.Generic.IAsyncEnumerable%601> type is a new asynchronous version of <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="6413d-345">Język umożliwia `await foreach` w przypadku `IAsyncEnumerable<T>` do korzystania z ich elementów i używania `yield return` do tworzenia elementów.</span><span class="sxs-lookup"><span data-stu-id="6413d-345">The language lets you `await foreach` over `IAsyncEnumerable<T>` to consume their elements, and use `yield return` to them to produce elements.</span></span>

<span data-ttu-id="6413d-346">Poniższy przykład ilustruje produkcję i zużycie strumieni asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="6413d-346">The following example demonstrates both production and consumption of async streams.</span></span> <span data-ttu-id="6413d-347">Instrukcja `foreach` jest asynchroniczna i sama używa `yield return` do tworzenia strumienia asynchronicznego dla obiektów wywołujących.</span><span class="sxs-lookup"><span data-stu-id="6413d-347">The `foreach` statement is async and itself uses `yield return` to produce an async stream for callers.</span></span> <span data-ttu-id="6413d-348">Ten wzorzec (przy użyciu `yield return`) jest zalecanym modelem do tworzenia strumieni asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="6413d-348">This pattern (using `yield return`) is the recommended model for producing async streams.</span></span>

```csharp
async IAsyncEnumerable<int> GetBigResultsAsync()
{
    await foreach (var result in GetResultsAsync())
    {
        if (result > 20) yield return result;
    }
}
```

<span data-ttu-id="6413d-349">Oprócz możliwości `await foreach` można także tworzyć Iteratory asynchroniczne, na przykład iterator, który zwraca `IAsyncEnumerable/IAsyncEnumerator`, który można `await` i `yield` w.</span><span class="sxs-lookup"><span data-stu-id="6413d-349">In addition to being able to `await foreach`, you can also create async iterators, for example, an iterator that returns an `IAsyncEnumerable/IAsyncEnumerator` that you can both `await` and `yield` in.</span></span> <span data-ttu-id="6413d-350">W przypadku obiektów, które muszą zostać usunięte, można użyć `IAsyncDisposable`, które mają różne implementacje typów BCL, na przykład `Stream` i `Timer`.</span><span class="sxs-lookup"><span data-stu-id="6413d-350">For objects that need to be disposed, you can use `IAsyncDisposable`, which various BCL types implement, such as `Stream` and `Timer`.</span></span>

<span data-ttu-id="6413d-351">Aby uzyskać więcej informacji, zobacz [Samouczek dotyczący strumieni asynchronicznych](../../csharp/tutorials/generate-consume-asynchronous-stream.md).</span><span class="sxs-lookup"><span data-stu-id="6413d-351">For more information, see the [async streams tutorial](../../csharp/tutorials/generate-consume-asynchronous-stream.md).</span></span>

### <a name="ieee-floating-point"></a><span data-ttu-id="6413d-352">Liczba zmiennoprzecinkowa IEEE</span><span class="sxs-lookup"><span data-stu-id="6413d-352">IEEE Floating-point</span></span>

<span data-ttu-id="6413d-353">Interfejsy API zmiennoprzecinkowe są aktualizowane w celu zapewnienia zgodności z [poprawką IEEE 754-2008](https://en.wikipedia.org/wiki/IEEE_754-2008_revision).</span><span class="sxs-lookup"><span data-stu-id="6413d-353">Floating point APIs are being updated to comply with [IEEE 754-2008 revision](https://en.wikipedia.org/wiki/IEEE_754-2008_revision).</span></span> <span data-ttu-id="6413d-354">Celem tych zmian jest uwidocznienie wszystkich **wymaganych** operacji i upewnienie się, że są one zgodne z specyfikacją IEEE. Aby uzyskać więcej informacji na temat ulepszeń zmiennoprzecinkowych, zobacz [udoskonalenia analizy i formatowania zmiennoprzecinkowe w wpisie na blogu programu .NET Core 3,0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) .</span><span class="sxs-lookup"><span data-stu-id="6413d-354">The goal of these changes is to expose all **required** operations and ensure that they're behaviorally compliant with the IEEE spec. For more information about floating-point improvements, see the [Floating-Point Parsing and Formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog post.</span></span>

<span data-ttu-id="6413d-355">Poprawki dotyczące analizowania i formatowania obejmują:</span><span class="sxs-lookup"><span data-stu-id="6413d-355">Parsing and formatting fixes include:</span></span>

- <span data-ttu-id="6413d-356">Poprawnie Analizuj i Zaokrąglij dane wejściowe o dowolnej długości.</span><span class="sxs-lookup"><span data-stu-id="6413d-356">Correctly parse and round inputs of any length.</span></span>
- <span data-ttu-id="6413d-357">Prawidłowo Przeanalizuj i sformatuj ujemną wartość zero.</span><span class="sxs-lookup"><span data-stu-id="6413d-357">Correctly parse and format negative zero.</span></span>
- <span data-ttu-id="6413d-358">Prawidłowo Przeanalizuj `Infinity` i `NaN`, wykonując kontrolę bez uwzględniania wielkości liter i zezwalając na opcjonalną wcześniejszą `+`, jeśli ma to zastosowanie.</span><span class="sxs-lookup"><span data-stu-id="6413d-358">Correctly parse `Infinity` and `NaN` by doing a case-insensitive check and allowing an optional preceding `+` where applicable.</span></span>

<span data-ttu-id="6413d-359">Nowe interfejsy API <xref:System.Math?displayProperty=nameWithType> obejmują:</span><span class="sxs-lookup"><span data-stu-id="6413d-359">New <xref:System.Math?displayProperty=nameWithType> APIs include:</span></span>

- <span data-ttu-id="6413d-360"><xref:System.Math.BitIncrement(System.Double)> i <xref:System.Math.BitDecrement(System.Double)></span><span class="sxs-lookup"><span data-stu-id="6413d-360"><xref:System.Math.BitIncrement(System.Double)> and <xref:System.Math.BitDecrement(System.Double)></span></span>\
<span data-ttu-id="6413d-361">Odpowiada za operacje IEEE `nextUp` i `nextDown`.</span><span class="sxs-lookup"><span data-stu-id="6413d-361">Corresponds to the `nextUp` and `nextDown` IEEE operations.</span></span> <span data-ttu-id="6413d-362">Zwracają one najmniejszą liczbę zmiennoprzecinkową, która porównuje większe lub mniejsze niż dane wejściowe (odpowiednio).</span><span class="sxs-lookup"><span data-stu-id="6413d-362">They return the smallest floating-point number that compares greater or lesser than the input (respectively).</span></span> <span data-ttu-id="6413d-363">Na przykład `Math.BitIncrement(0.0)` zwróci `double.Epsilon`.</span><span class="sxs-lookup"><span data-stu-id="6413d-363">For example, `Math.BitIncrement(0.0)` would return `double.Epsilon`.</span></span>

- <span data-ttu-id="6413d-364"><xref:System.Math.MaxMagnitude(System.Double,System.Double)> i <xref:System.Math.MinMagnitude(System.Double,System.Double)></span><span class="sxs-lookup"><span data-stu-id="6413d-364"><xref:System.Math.MaxMagnitude(System.Double,System.Double)> and <xref:System.Math.MinMagnitude(System.Double,System.Double)></span></span>\
<span data-ttu-id="6413d-365">Odpowiada za operacje IEEE `maxNumMag` i `minNumMag`, zwracają wartość, która jest większa lub mniejsza o wielkości dwóch danych wejściowych (odpowiednio).</span><span class="sxs-lookup"><span data-stu-id="6413d-365">Corresponds to the `maxNumMag` and `minNumMag` IEEE operations, they return the value that is greater or lesser in magnitude of the two inputs (respectively).</span></span> <span data-ttu-id="6413d-366">Na przykład `Math.MaxMagnitude(2.0, -3.0)` zwróci `-3.0`.</span><span class="sxs-lookup"><span data-stu-id="6413d-366">For example, `Math.MaxMagnitude(2.0, -3.0)` would return `-3.0`.</span></span>

- <xref:System.Math.ILogB(System.Double)>\
<span data-ttu-id="6413d-367">Odnosi się do operacji IEEE `logB`, która zwraca wartość całkowitą, zwracająca podstawowy dziennik Base-2 parametru wejściowego.</span><span class="sxs-lookup"><span data-stu-id="6413d-367">Corresponds to the `logB` IEEE operation that returns an integral value, it returns the integral base-2 log of the input parameter.</span></span> <span data-ttu-id="6413d-368">Ta metoda jest efektywnie taka sama jak `floor(log2(x))`, ale została wykonana z minimalnym błędem zaokrąglania.</span><span class="sxs-lookup"><span data-stu-id="6413d-368">This method is effectively the same as `floor(log2(x))`, but done with minimal rounding error.</span></span>

- <xref:System.Math.ScaleB(System.Double,System.Int32)>\
<span data-ttu-id="6413d-369">Odnosi się do operacji IEEE `scaleB`, która przyjmuje wartość całkowitą, zwraca skuteczną `x * pow(2, n)`, ale jest wykonywana z minimalnym błędem zaokrąglania.</span><span class="sxs-lookup"><span data-stu-id="6413d-369">Corresponds to the `scaleB` IEEE operation that takes an integral value, it returns effectively `x * pow(2, n)`, but is done with minimal rounding error.</span></span>

- <xref:System.Math.Log2(System.Double)>\
<span data-ttu-id="6413d-370">Odnosi się do operacji IEEE `log2`, która zwraca logarytm o podstawie 2.</span><span class="sxs-lookup"><span data-stu-id="6413d-370">Corresponds to the `log2` IEEE operation, it returns the base-2 logarithm.</span></span> <span data-ttu-id="6413d-371">Minimalizuje błąd zaokrąglania.</span><span class="sxs-lookup"><span data-stu-id="6413d-371">It minimizes rounding error.</span></span>

- <xref:System.Math.FusedMultiplyAdd(System.Double,System.Double,System.Double)>\
<span data-ttu-id="6413d-372">Odnosi się do operacji IEEE `fma`, która wykonuje odrzucane mnożenie dodawania.</span><span class="sxs-lookup"><span data-stu-id="6413d-372">Corresponds to the `fma` IEEE operation, it performs a fused multiply add.</span></span> <span data-ttu-id="6413d-373">Oznacza to, że `(x * y) + z` w ramach jednej operacji, a tym samym minimalizowanie błędu zaokrąglania.</span><span class="sxs-lookup"><span data-stu-id="6413d-373">That is, it does `(x * y) + z` as a single operation, thereby minimizing the rounding error.</span></span> <span data-ttu-id="6413d-374">Przykładem może być `FusedMultiplyAdd(1e308, 2.0, -1e308)`, który zwraca `1e308`.</span><span class="sxs-lookup"><span data-stu-id="6413d-374">An example would be `FusedMultiplyAdd(1e308, 2.0, -1e308)` which returns `1e308`.</span></span> <span data-ttu-id="6413d-375">Regularna `(1e308 * 2.0) - 1e308` zwraca `double.PositiveInfinity`.</span><span class="sxs-lookup"><span data-stu-id="6413d-375">The regular `(1e308 * 2.0) - 1e308` returns `double.PositiveInfinity`.</span></span>

- <xref:System.Math.CopySign(System.Double,System.Double)>\
<span data-ttu-id="6413d-376">Odnosi się do operacji IEEE `copySign`, która zwraca wartość `x`, ale ze znakiem `y`.</span><span class="sxs-lookup"><span data-stu-id="6413d-376">Corresponds to the `copySign` IEEE operation, it returns the value of `x`, but with the sign of `y`.</span></span>

### <a name="net-platform-dependent-intrinsics"></a><span data-ttu-id="6413d-377">Elementy wewnętrzne zależne od platformy .NET</span><span class="sxs-lookup"><span data-stu-id="6413d-377">.NET Platform-Dependent Intrinsics</span></span>

<span data-ttu-id="6413d-378">Dodano interfejsy API, które umożliwiają dostęp do pewnych instrukcji procesora CPU zorientowanych na wydajność, takich jak **SIMD** lub **bitowe zestawy instrukcji manipulowania** .</span><span class="sxs-lookup"><span data-stu-id="6413d-378">APIs have been added that allow access to certain perf-oriented CPU instructions, such as the **SIMD** or **Bit Manipulation instruction** sets.</span></span> <span data-ttu-id="6413d-379">Te instrukcje mogą pomóc w osiągnięciu znaczących ulepszeń wydajności w niektórych scenariuszach, takich jak wydajne przetwarzanie danych.</span><span class="sxs-lookup"><span data-stu-id="6413d-379">These instructions can help achieve significant performance improvements in certain scenarios, such as processing data efficiently in parallel.</span></span>

<span data-ttu-id="6413d-380">W odpowiednich przypadkach biblioteki .NET zaczęły korzystać z tych instrukcji w celu zwiększenia wydajności.</span><span class="sxs-lookup"><span data-stu-id="6413d-380">Where appropriate, the .NET libraries have begun using these instructions to improve performance.</span></span>

<span data-ttu-id="6413d-381">Aby uzyskać więcej informacji, zobacz elementy [wewnętrzne zależne od platformy .NET](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md).</span><span class="sxs-lookup"><span data-stu-id="6413d-381">For more information, see [.NET Platform Dependent Intrinsics](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md).</span></span>

### <a name="improved-net-core-version-apis"></a><span data-ttu-id="6413d-382">Ulepszone interfejsy API wersji platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="6413d-382">Improved .NET Core Version APIs</span></span>

<span data-ttu-id="6413d-383">Począwszy od platformy .NET Core 3,0, interfejsy API wersji dostarczone z platformą .NET Core teraz zwracają oczekiwane informacje.</span><span class="sxs-lookup"><span data-stu-id="6413d-383">Starting with .NET Core 3.0, the version APIs provided with .NET Core now return the information you expect.</span></span> <span data-ttu-id="6413d-384">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="6413d-384">For example:</span></span>

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
// New result (notice the value includes any preview release information)
//   RuntimeInformation.FrameworkDescription: .NET Core 3.0.0-preview4-27615-11
```

> [!WARNING]
> <span data-ttu-id="6413d-385">Istotna zmiana.</span><span class="sxs-lookup"><span data-stu-id="6413d-385">Breaking change.</span></span> <span data-ttu-id="6413d-386">Jest to technicznie istotna zmiana, ponieważ schemat przechowywania wersji został zmieniony.</span><span class="sxs-lookup"><span data-stu-id="6413d-386">This is technically a breaking change because the versioning scheme has changed.</span></span>

### <a name="fast-built-in-json-support"></a><span data-ttu-id="6413d-387">Szybka Wbudowana obsługa JSON</span><span class="sxs-lookup"><span data-stu-id="6413d-387">Fast built-in JSON support</span></span>

<span data-ttu-id="6413d-388">Użytkownicy platformy .NET mogą w dużym stopniu korzystać z [**JSON.NET**](https://www.newtonsoft.com/json) i innych popularnych bibliotek JSON, które nadal są dobrym wybórem.</span><span class="sxs-lookup"><span data-stu-id="6413d-388">.NET users have largely relied on [**Json.NET**](https://www.newtonsoft.com/json) and other popular JSON libraries, which continue to be good choices.</span></span> <span data-ttu-id="6413d-389">**JSON.NET** używa ciągów .NET jako podstawowego elementu DataType, który jest UTF-16 pod okapem.</span><span class="sxs-lookup"><span data-stu-id="6413d-389">**Json.NET** uses .NET strings as its base datatype, which is UTF-16 under the hood.</span></span>

<span data-ttu-id="6413d-390">Nowa Wbudowana obsługa JSON to wysoka wydajność, niska alokacja i oparta na `Span<byte>`.</span><span class="sxs-lookup"><span data-stu-id="6413d-390">The new built-in JSON support is high-performance, low allocation, and based on `Span<byte>`.</span></span> <span data-ttu-id="6413d-391">Aby uzyskać więcej informacji o przestrzeni nazw i typach <xref:System.Text.Json>, zobacz [Serializacja JSON w programie .NET — Omówienie](../../standard/serialization/system-text-json-overview.md).</span><span class="sxs-lookup"><span data-stu-id="6413d-391">For more information about the <xref:System.Text.Json> namespace and types, see [JSON serialization in .NET - overview](../../standard/serialization/system-text-json-overview.md).</span></span> <span data-ttu-id="6413d-392">Samouczki dotyczące typowych scenariuszy serializacji JSON znajdują się [w temacie jak serializować i deserializować kod JSON w programie .NET](../../standard/serialization/system-text-json-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="6413d-392">For tutorials on common JSON serialization scenarios, see [How to serialize and deserialize JSON in .NET](../../standard/serialization/system-text-json-how-to.md).</span></span>

### <a name="http2-support"></a><span data-ttu-id="6413d-393">Obsługa protokołu HTTP/2</span><span class="sxs-lookup"><span data-stu-id="6413d-393">HTTP/2 support</span></span>

<span data-ttu-id="6413d-394">Typ <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> obsługuje protokół HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="6413d-394">The <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> type supports the HTTP/2 protocol.</span></span> <span data-ttu-id="6413d-395">Jeśli protokół HTTP/2 jest włączony, wersja protokołu HTTP jest negocjowana za pośrednictwem protokołu TLS/CLIENTHELLO ALPN, a protokół HTTP/2 jest używany, jeśli serwer zdecyduje się go użyć.</span><span class="sxs-lookup"><span data-stu-id="6413d-395">If HTTP/2 is enabled, the HTTP protocol version is negotiated via TLS/ALPN, and HTTP/2 is used if the server elects to use it.</span></span>

<span data-ttu-id="6413d-396">Domyślnym protokołem jest protokół HTTP/1.1, ale protokół HTTP/2 można włączyć na dwa różne sposoby.</span><span class="sxs-lookup"><span data-stu-id="6413d-396">The default protocol remains HTTP/1.1, but HTTP/2 can be enabled in two different ways.</span></span> <span data-ttu-id="6413d-397">Najpierw można ustawić komunikat żądania HTTP na potrzeby używania protokołu HTTP/2:</span><span class="sxs-lookup"><span data-stu-id="6413d-397">First, you can set the HTTP request message to use HTTP/2:</span></span>

[!CODE-csharp[Http2Request](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Request)]

<span data-ttu-id="6413d-398">Następnie można zmienić <xref:System.Net.Http.HttpClient>, aby domyślnie używać protokołu HTTP/2:</span><span class="sxs-lookup"><span data-stu-id="6413d-398">Second, you can change <xref:System.Net.Http.HttpClient> to use HTTP/2 by default:</span></span>

[!CODE-csharp[Http2Client](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Client)]

<span data-ttu-id="6413d-399">W wielu przypadkach podczas tworzenia aplikacji chcesz użyć nieszyfrowanego połączenia.</span><span class="sxs-lookup"><span data-stu-id="6413d-399">Many times when you're developing an application, you want to use an unencrypted connection.</span></span> <span data-ttu-id="6413d-400">Jeśli wiesz, że docelowy punkt końcowy będzie używać protokołu HTTP/2, możesz włączyć nieszyfrowane połączenia dla protokołu HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="6413d-400">If you know the target endpoint will be using HTTP/2, you can turn on unencrypted connections for HTTP/2.</span></span> <span data-ttu-id="6413d-401">Można ją włączyć, ustawiając zmienną środowiskową `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT` na `1` lub włączając ją w kontekście aplikacji:</span><span class="sxs-lookup"><span data-stu-id="6413d-401">You can turn it on by setting the `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT` environment variable to `1` or by enabling it in the app context:</span></span>

[!CODE-csharp[Http2Context](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#AppContext)]

## <a name="next-steps"></a><span data-ttu-id="6413d-402">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="6413d-402">Next steps</span></span>

- [<span data-ttu-id="6413d-403">Zapoznaj się z istotnymi zmianami między programem .NET Core 2,2 i 3,0.</span><span class="sxs-lookup"><span data-stu-id="6413d-403">Review the breaking changes between .NET Core 2.2 and 3.0.</span></span>](../compatibility/2.2-3.0.md)
- [<span data-ttu-id="6413d-404">Zapoznaj się z istotnymi zmianami między .NET Framework i .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="6413d-404">Review the breaking changes between .NET Framework and .NET Core 3.0.</span></span>](../compatibility/framework-core.md)

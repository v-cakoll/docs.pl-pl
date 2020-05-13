---
title: Co nowego w programie .NET Core 3.0
description: Dowiedz się więcej o nowych funkcjach dostępnych w programie .NET Core 3,0.
dev_langs:
- csharp
author: thraka
ms.author: adegeo
ms.date: 01/27/2020
ms.openlocfilehash: 422cb7b20e2644ab44f9573f101fb6b53ab1dd2f
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378824"
---
# <a name="whats-new-in-net-core-30"></a><span data-ttu-id="51e40-103">Co nowego w programie .NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="51e40-103">What's new in .NET Core 3.0</span></span>

<span data-ttu-id="51e40-104">W tym artykule opisano nowości w programie .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="51e40-104">This article describes what is new in .NET Core 3.0.</span></span> <span data-ttu-id="51e40-105">Jednym z największych ulepszeń jest obsługa aplikacji klasycznych systemu Windows (tylko system Windows).</span><span class="sxs-lookup"><span data-stu-id="51e40-105">One of the biggest enhancements is support for Windows desktop applications (Windows only).</span></span> <span data-ttu-id="51e40-106">Korzystając z pulpitu systemu Windows składnika zestawu SDK platformy .NET Core 3,0, można przenieść aplikacje Windows Forms i Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="51e40-106">By using the .NET Core 3.0 SDK component Windows Desktop, you can port your Windows Forms and Windows Presentation Foundation (WPF) applications.</span></span> <span data-ttu-id="51e40-107">Aby można było wyczyścić, składnik pulpitu systemu Windows jest obsługiwany i uwzględniany w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="51e40-107">To be clear, the Windows Desktop component is only supported and included on Windows.</span></span> <span data-ttu-id="51e40-108">Aby uzyskać więcej informacji, zobacz sekcję [pulpitu systemu Windows](#windows-desktop) w dalszej części tego artykułu.</span><span class="sxs-lookup"><span data-stu-id="51e40-108">For more information, see the [Windows desktop](#windows-desktop) section later in this article.</span></span>

<span data-ttu-id="51e40-109">Program .NET Core 3,0 dodaje obsługę języka C# 8,0.</span><span class="sxs-lookup"><span data-stu-id="51e40-109">.NET Core 3.0 adds support for C# 8.0.</span></span> <span data-ttu-id="51e40-110">Zdecydowanie zaleca się używanie [programu Visual Studio 2019 w wersji 16,3](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) lub nowszej, [Visual Studio dla komputerów Mac 8,3](/visualstudio/mac/install-preview) lub nowszego lub [Visual Studio Code](https://code.visualstudio.com/) z najnowszym **rozszerzeniem języka C#**.</span><span class="sxs-lookup"><span data-stu-id="51e40-110">It's highly recommended that you use [Visual Studio 2019 version 16.3](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or newer, [Visual Studio for Mac 8.3](/visualstudio/mac/install-preview) or newer, or [Visual Studio Code](https://code.visualstudio.com/) with the latest **C# extension**.</span></span>

<span data-ttu-id="51e40-111">[Pobierz i Rozpocznij pracę z platformą .NET Core 3,0](https://aka.ms/netcore3download) teraz w systemie Windows, MacOS lub Linux.</span><span class="sxs-lookup"><span data-stu-id="51e40-111">[Download and get started with .NET Core 3.0](https://aka.ms/netcore3download) right now on Windows, macOS, or Linux.</span></span>

<span data-ttu-id="51e40-112">Aby uzyskać więcej informacji o wersji, zobacz [anons programu .NET Core 3,0](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0/).</span><span class="sxs-lookup"><span data-stu-id="51e40-112">For more information about the release, see the [.NET Core 3.0 announcement](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0/).</span></span>

<span data-ttu-id="51e40-113">Środowisko .NET Core RC1 zostało uznane za gotowe do produkcji przez firmę Microsoft i zostało w pełni obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="51e40-113">.NET Core RC1 was considered production ready by Microsoft and was fully supported.</span></span> <span data-ttu-id="51e40-114">Jeśli korzystasz z wersji zapoznawczej, musisz przejść do wersji RTM, aby uzyskać pomoc techniczną.</span><span class="sxs-lookup"><span data-stu-id="51e40-114">If you're using a preview release, you must move to the RTM version for continued support.</span></span>

## <a name="language-improvements-c-80"></a><span data-ttu-id="51e40-115">Udoskonalenia języka C# 8,0</span><span class="sxs-lookup"><span data-stu-id="51e40-115">Language improvements C# 8.0</span></span>

<span data-ttu-id="51e40-116">Język C# 8,0 jest również częścią tej wersji, która obejmuje funkcję [typów referencyjnych dopuszczających wartość null](../../csharp/tutorials/nullable-reference-types.md) , [strumienie asynchroniczne](../../csharp/tutorials/generate-consume-asynchronous-stream.md)i [więcej wzorców](../../csharp/tutorials/pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="51e40-116">C# 8.0 is also part of this release, which includes the [nullable reference types](../../csharp/tutorials/nullable-reference-types.md) feature, [async streams](../../csharp/tutorials/generate-consume-asynchronous-stream.md), and [more patterns](../../csharp/tutorials/pattern-matching.md).</span></span> <span data-ttu-id="51e40-117">Aby uzyskać więcej informacji na temat funkcji języka C# 8,0, zobacz [co nowego w języku c# 8,0](../../csharp/whats-new/csharp-8.md).</span><span class="sxs-lookup"><span data-stu-id="51e40-117">For more information about C# 8.0 features, see [What's new in C# 8.0](../../csharp/whats-new/csharp-8.md).</span></span>

<span data-ttu-id="51e40-118">Wprowadzono ulepszenia dotyczące języka w celu obsługi następujących funkcji API poniżej:</span><span class="sxs-lookup"><span data-stu-id="51e40-118">Language enhancements were added to support the following API features detailed below:</span></span>

- [<span data-ttu-id="51e40-119">Zakresy i indeksy</span><span class="sxs-lookup"><span data-stu-id="51e40-119">Ranges and indices</span></span>](#ranges-and-indices)
- [<span data-ttu-id="51e40-120">Strumienie asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="51e40-120">Async streams</span></span>](#async-streams)

## <a name="net-standard-21"></a><span data-ttu-id="51e40-121">.NET Standard 2,1</span><span class="sxs-lookup"><span data-stu-id="51e40-121">.NET Standard 2.1</span></span>

<span data-ttu-id="51e40-122">Platforma .NET Core 3,0 implementuje **.NET Standard 2,1**.</span><span class="sxs-lookup"><span data-stu-id="51e40-122">.NET Core 3.0 implements **.NET Standard 2.1**.</span></span> <span data-ttu-id="51e40-123">Jednak `dotnet new classlib` szablon domyślny generuje projekt, który nadal jest przeznaczony dla **.NET Standard 2,0**.</span><span class="sxs-lookup"><span data-stu-id="51e40-123">However, the default `dotnet new classlib` template generates a project that still targets **.NET Standard 2.0**.</span></span> <span data-ttu-id="51e40-124">Aby docelowa **.NET Standard 2,1**, edytuj plik projektu i Zmień `TargetFramework` Właściwość na `netstandard2.1` :</span><span class="sxs-lookup"><span data-stu-id="51e40-124">To target **.NET Standard 2.1**, edit your project file and change the `TargetFramework` property to `netstandard2.1`:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard2.1</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="51e40-125">Jeśli używasz programu Visual Studio, potrzebujesz [programu Visual studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), ponieważ program visual Studio 2017 nie obsługuje **.NET Standard 2,1** ani **.NET Core 3,0**.</span><span class="sxs-lookup"><span data-stu-id="51e40-125">If you're using Visual Studio, you need [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), as Visual Studio 2017 doesn't support **.NET Standard 2.1** or **.NET Core 3.0**.</span></span>

## <a name="compiledeploy"></a><span data-ttu-id="51e40-126">Kompiluj/Wdróż</span><span class="sxs-lookup"><span data-stu-id="51e40-126">Compile/Deploy</span></span>

### <a name="default-executables"></a><span data-ttu-id="51e40-127">Domyślne pliki wykonywalne</span><span class="sxs-lookup"><span data-stu-id="51e40-127">Default executables</span></span>

<span data-ttu-id="51e40-128">Platforma .NET Core teraz domyślnie kompiluje [pliki wykonywalne zależne od środowiska uruchomieniowego](../deploying/index.md#publish-runtime-dependent) .</span><span class="sxs-lookup"><span data-stu-id="51e40-128">.NET Core now builds [runtime-dependent executables](../deploying/index.md#publish-runtime-dependent) by default.</span></span> <span data-ttu-id="51e40-129">To zachowanie jest nowe w przypadku aplikacji korzystających z zainstalowanej globalnie wersji platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="51e40-129">This behavior is new for applications that use a globally installed version of .NET Core.</span></span> <span data-ttu-id="51e40-130">Wcześniej tylko [wstępnie zawarte wdrożenia](../deploying/index.md#publish-self-contained) spowodują utworzenie pliku wykonywalnego.</span><span class="sxs-lookup"><span data-stu-id="51e40-130">Previously, only [self-contained deployments](../deploying/index.md#publish-self-contained) would produce an executable.</span></span>

<span data-ttu-id="51e40-131">W trakcie `dotnet build` lub `dotnet publish` , tworzony jest plik wykonywalny (znany jako **appHost**), który odpowiada środowisku i platformie zestawu SDK, którego używasz.</span><span class="sxs-lookup"><span data-stu-id="51e40-131">During `dotnet build` or `dotnet publish`, an executable (known as the **appHost**) is created that matches the environment and platform of the SDK you're using.</span></span> <span data-ttu-id="51e40-132">Można oczekiwać, że te same elementy wykonywalne są takie same jak w przypadku innych natywnych plików wykonywalnych, takich jak:</span><span class="sxs-lookup"><span data-stu-id="51e40-132">You can expect the same things with these executables as you would other native executables, such as:</span></span>

- <span data-ttu-id="51e40-133">Możesz kliknąć dwukrotnie plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="51e40-133">You can double-click on the executable.</span></span>
- <span data-ttu-id="51e40-134">Aplikację można uruchomić z poziomu wiersza polecenia bezpośrednio, na przykład `myapp.exe` w systemie Windows, w systemie `./myapp` Linux i macOS.</span><span class="sxs-lookup"><span data-stu-id="51e40-134">You can launch the application from a command prompt directly, such as `myapp.exe` on Windows, and `./myapp` on Linux and macOS.</span></span>

### <a name="macos-apphost-and-notarization"></a><span data-ttu-id="51e40-135">macOS appHost i notarization</span><span class="sxs-lookup"><span data-stu-id="51e40-135">macOS appHost and notarization</span></span>

<span data-ttu-id="51e40-136">*tylko macOS*</span><span class="sxs-lookup"><span data-stu-id="51e40-136">*macOS only*</span></span>

<span data-ttu-id="51e40-137">Począwszy od zestaw .NET Core SDK 3,0 dla usługi macOS, ustawienie służące do tworzenia domyślnego pliku wykonywalnego (znanego jako appHost) jest domyślnie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="51e40-137">Starting with the notarized .NET Core SDK 3.0 for macOS, the setting to produce a default executable (known as the appHost) is disabled by default.</span></span> <span data-ttu-id="51e40-138">Aby uzyskać więcej informacji, zobacz [MacOS Catalina Notarization i wpływ na pobieranie i projekty platformy .NET Core](../install/macos-notarization-issues.md).</span><span class="sxs-lookup"><span data-stu-id="51e40-138">For more information, see [macOS Catalina Notarization and the impact on .NET Core downloads and projects](../install/macos-notarization-issues.md).</span></span>

<span data-ttu-id="51e40-139">Gdy ustawienie appHost jest włączone, program .NET Core generuje natywny plik konfiguracji Mach-O podczas kompilowania lub publikowania.</span><span class="sxs-lookup"><span data-stu-id="51e40-139">When the appHost setting is enabled, .NET Core generates a native Mach-O executable when you build or publish.</span></span> <span data-ttu-id="51e40-140">Aplikacja jest uruchamiana w kontekście appHost, gdy jest uruchamiana z kodu źródłowego za pomocą `dotnet run` polecenia lub bezpośrednio uruchamiając plik wykonywalny "Mach-O".</span><span class="sxs-lookup"><span data-stu-id="51e40-140">Your app runs in the context of the appHost when it is run from source code with the `dotnet run` command, or by starting the Mach-O executable directly.</span></span>

<span data-ttu-id="51e40-141">Bez appHost jedynym sposobem uruchomienia aplikacji [zależnej od środowiska uruchomieniowego](../deploying/index.md#publish-runtime-dependent) jest `dotnet <filename.dll>` polecenie.</span><span class="sxs-lookup"><span data-stu-id="51e40-141">Without the appHost, the only way a user can start a [runtime-dependent](../deploying/index.md#publish-runtime-dependent) app is with the `dotnet <filename.dll>` command.</span></span> <span data-ttu-id="51e40-142">AppHost jest zawsze tworzona przy publikowaniu [własnej aplikacji.](../deploying/index.md#publish-self-contained)</span><span class="sxs-lookup"><span data-stu-id="51e40-142">An appHost is always created when you publish your app [self-contained](../deploying/index.md#publish-self-contained).</span></span>

<span data-ttu-id="51e40-143">Można skonfigurować appHost na poziomie projektu lub przełączać appHost dla określonego `dotnet` polecenia z `-p:UseAppHost` parametrem:</span><span class="sxs-lookup"><span data-stu-id="51e40-143">You can either configure the appHost at the project level, or toggle the appHost for a specific `dotnet` command with the `-p:UseAppHost` parameter:</span></span>

- <span data-ttu-id="51e40-144">Plik projektu</span><span class="sxs-lookup"><span data-stu-id="51e40-144">Project file</span></span>

  ```xml
  <PropertyGroup>
    <UseAppHost>true</UseAppHost>
  </PropertyGroup>
  ```

- <span data-ttu-id="51e40-145">Parametr wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="51e40-145">Command-line parameter</span></span>

  ```dotnetcli
  dotnet run -p:UseAppHost=true
  ```

<span data-ttu-id="51e40-146">Aby uzyskać więcej informacji na temat tego `UseAppHost` Ustawienia, zobacz [Właściwości programu MSBuild dla Microsoft. NET. SDK](../project-sdk/msbuild-props.md#useapphost).</span><span class="sxs-lookup"><span data-stu-id="51e40-146">For more information about the `UseAppHost` setting, see [MSBuild properties for Microsoft.NET.Sdk](../project-sdk/msbuild-props.md#useapphost).</span></span>

### <a name="single-file-executables"></a><span data-ttu-id="51e40-147">Pliki wykonywalne pojedynczego pliku</span><span class="sxs-lookup"><span data-stu-id="51e40-147">Single-file executables</span></span>

<span data-ttu-id="51e40-148">`dotnet publish`Polecenie obsługuje pakowanie aplikacji do pliku wykonywalnego określonego dla konkretnej platformy.</span><span class="sxs-lookup"><span data-stu-id="51e40-148">The `dotnet publish` command supports packaging your app into a platform-specific single-file executable.</span></span> <span data-ttu-id="51e40-149">Plik wykonywalny jest samowyodrębniający się i zawiera wszystkie zależności (w tym natywne) wymagane do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="51e40-149">The executable is self-extracting and contains all dependencies (including native) that are required to run your app.</span></span> <span data-ttu-id="51e40-150">Gdy aplikacja jest uruchamiana po raz pierwszy, aplikacja zostanie wyodrębniona do katalogu na podstawie nazwy aplikacji i identyfikatora kompilacji.</span><span class="sxs-lookup"><span data-stu-id="51e40-150">When the app is first run, the application is extracted to a directory based on the app name and build identifier.</span></span> <span data-ttu-id="51e40-151">Uruchamianie jest szybsze, gdy aplikacja jest uruchamiana ponownie.</span><span class="sxs-lookup"><span data-stu-id="51e40-151">Startup is faster when the application is run again.</span></span> <span data-ttu-id="51e40-152">Aplikacja nie musi wyodrębniać siebie po raz drugi, chyba że została użyta Nowa wersja.</span><span class="sxs-lookup"><span data-stu-id="51e40-152">The application doesn't need to extract itself a second time unless a new version was used.</span></span>

<span data-ttu-id="51e40-153">Aby opublikować plik wykonywalny pojedynczego pliku, ustaw `PublishSingleFile` w projekcie lub w wierszu polecenia `dotnet publish` polecenie:</span><span class="sxs-lookup"><span data-stu-id="51e40-153">To publish a single-file executable, set the `PublishSingleFile` in your project or on the command line with the `dotnet publish` command:</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifier>win10-x64</RuntimeIdentifier>
  <PublishSingleFile>true</PublishSingleFile>
</PropertyGroup>
```

<span data-ttu-id="51e40-154">— lub —</span><span class="sxs-lookup"><span data-stu-id="51e40-154">-or-</span></span>

```dotnetcli
dotnet publish -r win10-x64 -p:PublishSingleFile=true
```

<span data-ttu-id="51e40-155">Aby uzyskać więcej informacji o publikowaniu jednoplikowym, zapoznaj się z [dokumentem projektu pakietu pojedynczego pliku](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design.md).</span><span class="sxs-lookup"><span data-stu-id="51e40-155">For more information about single-file publishing, see the [single-file bundler design document](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design.md).</span></span>

### <a name="assembly-linking"></a><span data-ttu-id="51e40-156">Łączenie zestawów</span><span class="sxs-lookup"><span data-stu-id="51e40-156">Assembly linking</span></span>

<span data-ttu-id="51e40-157">Zestaw SDK platformy .NET Core 3,0 zawiera narzędzie, które pozwala zmniejszyć rozmiar aplikacji przez analizowanie IL i przycinanie nieużywanych zestawów.</span><span class="sxs-lookup"><span data-stu-id="51e40-157">The .NET core 3.0 SDK comes with a tool that can reduce the size of apps by analyzing IL and trimming unused assemblies.</span></span>

<span data-ttu-id="51e40-158">Aplikacje samodzielne obejmują wszystko, co jest potrzebne do uruchomienia kodu, bez konieczności instalowania programu .NET na komputerze-hoście.</span><span class="sxs-lookup"><span data-stu-id="51e40-158">Self-contained apps include everything needed to run your code, without requiring .NET to be installed on the host computer.</span></span> <span data-ttu-id="51e40-159">Jednak wiele razy aplikacja wymaga tylko małego podzestawu platformy do działania, a inne nieużywane biblioteki mogą zostać usunięte.</span><span class="sxs-lookup"><span data-stu-id="51e40-159">However, many times the app only requires a small subset of the framework to function, and other unused libraries could be removed.</span></span>

<span data-ttu-id="51e40-160">Platforma .NET Core zawiera teraz ustawienie, które będzie używać narzędzia [konsolidatora Il](https://github.com/mono/linker) do skanowania Il aplikacji.</span><span class="sxs-lookup"><span data-stu-id="51e40-160">.NET Core now includes a setting that will use the [IL linker](https://github.com/mono/linker) tool to scan the IL of your app.</span></span> <span data-ttu-id="51e40-161">To narzędzie wykrywa wymagany kod, a następnie przycina nieużywane biblioteki.</span><span class="sxs-lookup"><span data-stu-id="51e40-161">This tool detects what code is required, and then trims unused libraries.</span></span> <span data-ttu-id="51e40-162">To narzędzie może znacznie zmniejszyć rozmiar wdrożenia niektórych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="51e40-162">This tool can significantly reduce the deployment size of some apps.</span></span>

<span data-ttu-id="51e40-163">Aby włączyć to narzędzie, Dodaj `<PublishTrimmed>` ustawienie w projekcie i Opublikuj samodzielną aplikację:</span><span class="sxs-lookup"><span data-stu-id="51e40-163">To enable this tool, add the `<PublishTrimmed>` setting in your project and publish a self-contained app:</span></span>

```xml
<PropertyGroup>
  <PublishTrimmed>true</PublishTrimmed>
</PropertyGroup>
```

```dotnetcli
dotnet publish -r <rid> -c Release
```

<span data-ttu-id="51e40-164">Na przykład podstawowy "Hello World" nowy szablon projektu konsoli, który jest dostępny po opublikowaniu, trafień o rozmiarze 70 MB.</span><span class="sxs-lookup"><span data-stu-id="51e40-164">As an example, the basic "hello world" new console project template that is included, when published, hits about 70 MB in size.</span></span> <span data-ttu-id="51e40-165">Przy użyciu `<PublishTrimmed>` , ten rozmiar jest zmniejszany do około 30 MB.</span><span class="sxs-lookup"><span data-stu-id="51e40-165">By using `<PublishTrimmed>`, that size is reduced to about 30 MB.</span></span>

<span data-ttu-id="51e40-166">Należy wziąć pod uwagę, że aplikacje lub struktury (w tym ASP.NET Core i WPF), które wykorzystują odbicie lub powiązane funkcje dynamiczne, często będą przerywane po przycięciu.</span><span class="sxs-lookup"><span data-stu-id="51e40-166">It's important to consider that applications or frameworks (including ASP.NET Core and WPF) that use reflection or related dynamic features, will often break when trimmed.</span></span> <span data-ttu-id="51e40-167">To uszkodzenie występuje, ponieważ konsolidator nie wie o tym zachowaniu dynamicznym i nie może określić, które typy struktur są wymagane do odbicia.</span><span class="sxs-lookup"><span data-stu-id="51e40-167">This breakage occurs because the linker doesn't know about this dynamic behavior and can't determine which framework types are required for reflection.</span></span> <span data-ttu-id="51e40-168">Narzędzie konsolidatora IL można skonfigurować pod kątem tego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="51e40-168">The IL Linker tool can be configured to be aware of this scenario.</span></span>

<span data-ttu-id="51e40-169">Przed przycinaniem upewnij się, że aplikacja została przetestowana.</span><span class="sxs-lookup"><span data-stu-id="51e40-169">Above all else, be sure to test your app after trimming.</span></span>

<span data-ttu-id="51e40-170">Aby uzyskać więcej informacji na temat narzędzia konsolidatora IL, zapoznaj się z [dokumentacją](https://aka.ms/dotnet-illink) lub odwiedź repozytorium [mono/konsolidatora]( https://github.com/mono/linker) .</span><span class="sxs-lookup"><span data-stu-id="51e40-170">For more information about the IL Linker tool, see the [documentation](https://aka.ms/dotnet-illink) or visit the [mono/linker]( https://github.com/mono/linker) repo.</span></span>

### <a name="tiered-compilation"></a><span data-ttu-id="51e40-171">Kompilacja warstwowa</span><span class="sxs-lookup"><span data-stu-id="51e40-171">Tiered compilation</span></span>

<span data-ttu-id="51e40-172">[Kompilacja warstwowa](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation.md) (TC) jest domyślnie włączona z platformą .net Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="51e40-172">[Tiered compilation](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation.md) (TC) is on by default with .NET Core 3.0.</span></span> <span data-ttu-id="51e40-173">Ta funkcja umożliwia środowisku uruchomieniowemu wydajniejsze używanie kompilatora just-in-Time (JIT) w celu uzyskania lepszej wydajności.</span><span class="sxs-lookup"><span data-stu-id="51e40-173">This feature enables the runtime to more adaptively use the just-in-time (JIT) compiler to achieve better performance.</span></span>

<span data-ttu-id="51e40-174">Główną zaletą kompilacji warstwowej jest zapewnienie dwóch sposobów jitting metod: w warstwach o niższej jakości lub szybszych lub wyższych warstwach.</span><span class="sxs-lookup"><span data-stu-id="51e40-174">The main benefit of tiered compilation is to provide two ways of jitting methods: in a lower-quality-but-faster tier or a higher-quality-but-slower tier.</span></span> <span data-ttu-id="51e40-175">Jakość odnosi się do tego, jak dobrze jest zoptymalizowana Metoda.</span><span class="sxs-lookup"><span data-stu-id="51e40-175">The quality refers to how well the method is optimized.</span></span> <span data-ttu-id="51e40-176">TC ułatwia zwiększenie wydajności aplikacji w miarę przechodzenia przez różne etapy wykonywania — od uruchomienia do stanu stałego.</span><span class="sxs-lookup"><span data-stu-id="51e40-176">TC helps to improve the performance of an application as it goes through various stages of execution, from startup through steady state.</span></span> <span data-ttu-id="51e40-177">Gdy kompilacja warstwowa jest wyłączona, każda metoda jest kompilowana w jednym ze sposobów, która jest obciążona wydajnością o stałej kondycji w porównaniu z wydajnością uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="51e40-177">When tiered compilation is disabled, every method is compiled in a single way that's biased to steady-state performance over startup performance.</span></span>

<span data-ttu-id="51e40-178">Po włączeniu TC następujące zachowanie ma zastosowanie do kompilacji metody podczas uruchamiania aplikacji:</span><span class="sxs-lookup"><span data-stu-id="51e40-178">When TC is enabled, the following behavior applies for method compilation when an app starts up:</span></span>

- <span data-ttu-id="51e40-179">Jeśli metoda zawiera kod skompilowany z wyprzedzeniem lub [ReadyToRun](#readytorun-images), używany jest wygenerowany kod.</span><span class="sxs-lookup"><span data-stu-id="51e40-179">If the method has ahead-of-time-compiled code, or [ReadyToRun](#readytorun-images), the pregenerated code is used.</span></span>
- <span data-ttu-id="51e40-180">W przeciwnym razie metoda jest trybie JIT.</span><span class="sxs-lookup"><span data-stu-id="51e40-180">Otherwise, the method is jitted.</span></span> <span data-ttu-id="51e40-181">Zazwyczaj te metody są ogólne względem typów wartościowych.</span><span class="sxs-lookup"><span data-stu-id="51e40-181">Typically, these methods are generics over value types.</span></span>
  - <span data-ttu-id="51e40-182">*Szybkie kompilatory* umożliwiają szybsze generowanie kodu o niższej jakości (lub mniej zoptymalizowanym).</span><span class="sxs-lookup"><span data-stu-id="51e40-182">*Quick JIT* produces lower-quality (or less optimized) code more quickly.</span></span> <span data-ttu-id="51e40-183">W przypadku programu .NET Core 3,0, szybkie JIT jest domyślnie włączone dla metod, które nie zawierają pętli i są preferowane podczas uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="51e40-183">In .NET Core 3.0, Quick JIT is enabled by default for methods that don't contain loops and is preferred during startup.</span></span>
  - <span data-ttu-id="51e40-184">W pełni Optymalizacja JIT powoduje szybsze generowanie kodu o wyższej jakości (lub bardziej zoptymalizowany).</span><span class="sxs-lookup"><span data-stu-id="51e40-184">The fully optimizing JIT produces higher-quality (or more optimized) code more slowly.</span></span> <span data-ttu-id="51e40-185">W przypadku metod, w których nie można użyć metody szybkiej JIT (na przykład jeśli metoda jest przypisana do <xref:System.Runtime.CompilerServices.MethodImplOptions.AggressiveOptimization?displayProperty=nameWithType> ), używana jest pełna optymalizacja JIT.</span><span class="sxs-lookup"><span data-stu-id="51e40-185">For methods where Quick JIT would not be used (for example, if the method is attributed with <xref:System.Runtime.CompilerServices.MethodImplOptions.AggressiveOptimization?displayProperty=nameWithType>), the fully optimizing JIT is used.</span></span>

<span data-ttu-id="51e40-186">W przypadku często wywoływanych metod kompilator just in Time w końcu tworzy w tle w pełni zoptymalizowany kod.</span><span class="sxs-lookup"><span data-stu-id="51e40-186">For frequently called methods, the just-in-time compiler eventually creates fully optimized code in the background.</span></span> <span data-ttu-id="51e40-187">Zoptymalizowany kod zastępuje wstępnie skompilowany kod dla tej metody.</span><span class="sxs-lookup"><span data-stu-id="51e40-187">The optimized code then replaces the pre-compiled code for that method.</span></span>

<span data-ttu-id="51e40-188">Kod wygenerowany przez szybką JIT może działać wolniej, przydzielać więcej pamięci lub używać większej ilości miejsca na stosie.</span><span class="sxs-lookup"><span data-stu-id="51e40-188">Code generated by Quick JIT may run slower, allocate more memory, or use more stack space.</span></span> <span data-ttu-id="51e40-189">Jeśli występują problemy, można wyłączyć szybkie JIT przy użyciu tej właściwości programu MSBuild w pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="51e40-189">If there are issues, you can disabled Quick JIT using this MSBuild property in the project file:</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
</PropertyGroup>
```

<span data-ttu-id="51e40-190">Aby całkowicie wyłączyć TC, Użyj tej właściwości programu MSBuild w pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="51e40-190">To disable TC completely, use this MSBuild property in your project file:</span></span>

```xml
<PropertyGroup>
  <TieredCompilation>false</TieredCompilation>
</PropertyGroup>
```

> [!TIP]
> <span data-ttu-id="51e40-191">Jeśli zmienisz te ustawienia w pliku projektu, może być konieczne wykonanie czystej kompilacji dla nowych ustawień, które mają być odzwierciedlone (Usuń `obj` `bin` katalogi i Skompiluj ponownie).</span><span class="sxs-lookup"><span data-stu-id="51e40-191">If you change these settings in the project file, you may need to perform a clean build for the new settings to be reflected (delete the `obj` and `bin` directories and rebuild).</span></span>

<span data-ttu-id="51e40-192">Aby uzyskać więcej informacji o konfigurowaniu kompilacji w czasie wykonywania, zobacz [Opcje konfiguracji czasu wykonywania dla kompilacji](../run-time-config/compilation.md).</span><span class="sxs-lookup"><span data-stu-id="51e40-192">For more information about configuring compilation at run time, see [Run-time configuration options for compilation](../run-time-config/compilation.md).</span></span>

### <a name="readytorun-images"></a><span data-ttu-id="51e40-193">Obrazy ReadyToRun</span><span class="sxs-lookup"><span data-stu-id="51e40-193">ReadyToRun images</span></span>

<span data-ttu-id="51e40-194">Można skrócić czas uruchamiania aplikacji .NET Core, kompilując zestawy aplikacji jako ReadyToRun (R2R).</span><span class="sxs-lookup"><span data-stu-id="51e40-194">You can improve the startup time of your .NET Core application by compiling your application assemblies as ReadyToRun (R2R) format.</span></span> <span data-ttu-id="51e40-195">R2R to forma kompilacji z wyprzedzeniem (AOT).</span><span class="sxs-lookup"><span data-stu-id="51e40-195">R2R is a form of ahead-of-time (AOT) compilation.</span></span>

<span data-ttu-id="51e40-196">Pliki binarne R2R zwiększają wydajność uruchamiania przez zmniejszenie ilości pracy kompilatora, który jest potrzebny do załadowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="51e40-196">R2R binaries improve startup performance by reducing the amount of work the just-in-time (JIT) compiler needs to do as your application loads.</span></span> <span data-ttu-id="51e40-197">Pliki binarne zawierają podobny kod natywny w porównaniu z przeznaczeniem JIT.</span><span class="sxs-lookup"><span data-stu-id="51e40-197">The binaries contain similar native code compared to what the JIT would produce.</span></span> <span data-ttu-id="51e40-198">R2R pliki binarne są jednak większe, ponieważ zawierają kod języka pośredniego (IL), który jest nadal wymagany w niektórych scenariuszach i natywną wersję tego samego kodu.</span><span class="sxs-lookup"><span data-stu-id="51e40-198">However, R2R binaries are larger because they contain both intermediate language (IL) code, which is still needed for some scenarios, and the native version of the same code.</span></span> <span data-ttu-id="51e40-199">R2R jest dostępna tylko w przypadku publikowania aplikacji samodzielnej, która jest przeznaczona dla określonych środowisk uruchomieniowych (RID), takich jak Linux x64 lub Windows x64.</span><span class="sxs-lookup"><span data-stu-id="51e40-199">R2R is only available when you publish a self-contained app that targets specific runtime environments (RID) such as Linux x64 or Windows x64.</span></span>

<span data-ttu-id="51e40-200">Aby skompilować projekt jako ReadyToRun, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="51e40-200">To compile your project as ReadyToRun, do the following:</span></span>

01. <span data-ttu-id="51e40-201">Dodaj `<PublishReadyToRun>` ustawienie do projektu:</span><span class="sxs-lookup"><span data-stu-id="51e40-201">Add the `<PublishReadyToRun>` setting to your project:</span></span>

    ```xml
    <PropertyGroup>
      <PublishReadyToRun>true</PublishReadyToRun>
    </PropertyGroup>
    ```

01. <span data-ttu-id="51e40-202">Publikowanie aplikacji samodzielnej.</span><span class="sxs-lookup"><span data-stu-id="51e40-202">Publish a self-contained app.</span></span> <span data-ttu-id="51e40-203">Na przykład to polecenie tworzy samodzielną aplikację dla 64-bitowej wersji systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="51e40-203">For example, this command creates a self-contained app for the 64-bit version of Windows:</span></span>

    ```dotnetcli
    dotnet publish -c Release -r win-x64 --self-contained
    ```

#### <a name="cross-platformarchitecture-restrictions"></a><span data-ttu-id="51e40-204">Ograniczenia dotyczące wielu platform/architektury</span><span class="sxs-lookup"><span data-stu-id="51e40-204">Cross platform/architecture restrictions</span></span>

<span data-ttu-id="51e40-205">Kompilator ReadyToRun nie obsługuje obecnie określania wartości docelowej.</span><span class="sxs-lookup"><span data-stu-id="51e40-205">The ReadyToRun compiler doesn't currently support cross-targeting.</span></span> <span data-ttu-id="51e40-206">Należy skompilować na danym miejscu docelowym.</span><span class="sxs-lookup"><span data-stu-id="51e40-206">You must compile on a given target.</span></span> <span data-ttu-id="51e40-207">Na przykład jeśli chcesz, aby obrazy R2R dla systemu Windows x64 zostały wykonane, należy uruchomić polecenie Publikuj w tym środowisku.</span><span class="sxs-lookup"><span data-stu-id="51e40-207">For example, if you want R2R images for Windows x64, you need to run the publish command on that environment.</span></span>

<span data-ttu-id="51e40-208">Wyjątki dla wielu elementów docelowych:</span><span class="sxs-lookup"><span data-stu-id="51e40-208">Exceptions to cross-targeting:</span></span>

- <span data-ttu-id="51e40-209">System Windows x64 może służyć do kompilowania obrazów systemów Windows ARM32, ARM64 i x86.</span><span class="sxs-lookup"><span data-stu-id="51e40-209">Windows x64 can be used to compile Windows ARM32, ARM64, and x86 images.</span></span>
- <span data-ttu-id="51e40-210">System Windows x86 może służyć do kompilowania obrazów ARM32 systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="51e40-210">Windows x86 can be used to compile Windows ARM32 images.</span></span>
- <span data-ttu-id="51e40-211">System Linux x64 może służyć do kompilowania obrazów systemu Linux ARM32 i ARM64.</span><span class="sxs-lookup"><span data-stu-id="51e40-211">Linux x64 can be used to compile Linux ARM32 and ARM64 images.</span></span>

## <a name="runtimesdk"></a><span data-ttu-id="51e40-212">Środowisko uruchomieniowe/zestaw SDK</span><span class="sxs-lookup"><span data-stu-id="51e40-212">Runtime/SDK</span></span>

### <a name="major-version-runtime-roll-forward"></a><span data-ttu-id="51e40-213">Wersja główna — przewinięcie do przodu</span><span class="sxs-lookup"><span data-stu-id="51e40-213">Major-version runtime roll forward</span></span>

<span data-ttu-id="51e40-214">W programie .NET Core 3,0 wprowadzono funkcję wyboru, która pozwala aplikacji na przewinięcie do najnowszej wersji programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="51e40-214">.NET Core 3.0 introduces an opt-in feature that allows your app to roll forward to the latest major version of .NET Core.</span></span> <span data-ttu-id="51e40-215">Ponadto zostało dodane nowe ustawienie służące do kontrolowania sposobu, w jaki przenoszone do przodu jest stosowane do aplikacji.</span><span class="sxs-lookup"><span data-stu-id="51e40-215">Additionally, a new setting has been added to control how roll forward is applied to your app.</span></span> <span data-ttu-id="51e40-216">Tę konfigurację można skonfigurować w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="51e40-216">This can be configured in the following ways:</span></span>

- <span data-ttu-id="51e40-217">Właściwość pliku projektu:`RollForward`</span><span class="sxs-lookup"><span data-stu-id="51e40-217">Project file property: `RollForward`</span></span>
- <span data-ttu-id="51e40-218">Właściwość pliku konfiguracji czasu wykonywania:`rollForward`</span><span class="sxs-lookup"><span data-stu-id="51e40-218">Run-time configuration file property: `rollForward`</span></span>
- <span data-ttu-id="51e40-219">Zmienna środowiskowa:`DOTNET_ROLL_FORWARD`</span><span class="sxs-lookup"><span data-stu-id="51e40-219">Environment variable: `DOTNET_ROLL_FORWARD`</span></span>
- <span data-ttu-id="51e40-220">Argument wiersza polecenia:`--roll-forward`</span><span class="sxs-lookup"><span data-stu-id="51e40-220">Command-line argument: `--roll-forward`</span></span>

<span data-ttu-id="51e40-221">Należy określić jedną z następujących wartości.</span><span class="sxs-lookup"><span data-stu-id="51e40-221">One of the following values must be specified.</span></span> <span data-ttu-id="51e40-222">Jeśli ustawienie zostanie pominięte, wartością domyślną jest wartość **pomocnicza** .</span><span class="sxs-lookup"><span data-stu-id="51e40-222">If the setting is omitted, **Minor** is the default.</span></span>

- <span data-ttu-id="51e40-223">**LatestPatch**</span><span class="sxs-lookup"><span data-stu-id="51e40-223">**LatestPatch**</span></span>\
<span data-ttu-id="51e40-224">Przewinięcie do najwyższej wersji poprawki.</span><span class="sxs-lookup"><span data-stu-id="51e40-224">Roll forward to the highest patch version.</span></span> <span data-ttu-id="51e40-225">Spowoduje to wyłączenie wycofywania wersji pomocniczej.</span><span class="sxs-lookup"><span data-stu-id="51e40-225">This disables minor version roll forward.</span></span>
- <span data-ttu-id="51e40-226">**Średni**</span><span class="sxs-lookup"><span data-stu-id="51e40-226">**Minor**</span></span>\
<span data-ttu-id="51e40-227">Przewinięcie do najmniejszej wyższej wersji pomocniczej, jeśli brakuje wymaganej wersji pomocniczej.</span><span class="sxs-lookup"><span data-stu-id="51e40-227">Roll forward to the lowest higher minor version, if requested minor version is missing.</span></span> <span data-ttu-id="51e40-228">Jeśli jest obecna żądana wersja pomocnicza, zostaną użyte zasady **LatestPatch** .</span><span class="sxs-lookup"><span data-stu-id="51e40-228">If the requested minor version is present, then the **LatestPatch** policy is used.</span></span>
- <span data-ttu-id="51e40-229">**Znaczny**</span><span class="sxs-lookup"><span data-stu-id="51e40-229">**Major**</span></span>\
<span data-ttu-id="51e40-230">Zaczekaj na najmniejszą wyższą wersję główną i najniższą wersję pomocniczą, jeśli brakuje żądanej wersji głównej.</span><span class="sxs-lookup"><span data-stu-id="51e40-230">Roll forward to lowest higher major version, and lowest minor version, if requested major version is missing.</span></span> <span data-ttu-id="51e40-231">Jeśli jest obecna żądana wersja główna, są używane zasady **pomocnicze** .</span><span class="sxs-lookup"><span data-stu-id="51e40-231">If the requested major version is present, then the **Minor** policy is used.</span></span>
- <span data-ttu-id="51e40-232">**LatestMinor**</span><span class="sxs-lookup"><span data-stu-id="51e40-232">**LatestMinor**</span></span>\
<span data-ttu-id="51e40-233">Przewinięcie do przodu do najwyższej wersji pomocniczej, nawet jeśli jest obecna żądana wersja pomocnicza.</span><span class="sxs-lookup"><span data-stu-id="51e40-233">Roll forward to highest minor version, even if requested minor version is present.</span></span> <span data-ttu-id="51e40-234">Przeznaczone do scenariuszy hostingu składników.</span><span class="sxs-lookup"><span data-stu-id="51e40-234">Intended for component hosting scenarios.</span></span>
- <span data-ttu-id="51e40-235">**LatestMajor**</span><span class="sxs-lookup"><span data-stu-id="51e40-235">**LatestMajor**</span></span>\
<span data-ttu-id="51e40-236">Przewinięcie do przodu do najwyższej głównej i najwyższej wersji pomocniczej, nawet jeśli jest obecny żądany główny.</span><span class="sxs-lookup"><span data-stu-id="51e40-236">Roll forward to highest major and highest minor version, even if requested major is present.</span></span> <span data-ttu-id="51e40-237">Przeznaczone do scenariuszy hostingu składników.</span><span class="sxs-lookup"><span data-stu-id="51e40-237">Intended for component hosting scenarios.</span></span>
- <span data-ttu-id="51e40-238">**Wyłącza**</span><span class="sxs-lookup"><span data-stu-id="51e40-238">**Disable**</span></span>\
<span data-ttu-id="51e40-239">Nie przetaczaj dalej.</span><span class="sxs-lookup"><span data-stu-id="51e40-239">Don't roll forward.</span></span> <span data-ttu-id="51e40-240">Powiąż tylko z określoną wersją.</span><span class="sxs-lookup"><span data-stu-id="51e40-240">Only bind to specified version.</span></span> <span data-ttu-id="51e40-241">Te zasady nie są zalecane do użytku ogólnego, ponieważ uniemożliwiają one przekazanie do najnowszych poprawek.</span><span class="sxs-lookup"><span data-stu-id="51e40-241">This policy isn't recommended for general use because it disables the ability to roll forward to the latest patches.</span></span> <span data-ttu-id="51e40-242">Ta wartość jest zalecana tylko do celów testowych.</span><span class="sxs-lookup"><span data-stu-id="51e40-242">This value is only recommended for testing.</span></span>

<span data-ttu-id="51e40-243">Oprócz ustawienia **Wyłącz** wszystkie ustawienia będą używać najwyższej dostępnej wersji poprawki.</span><span class="sxs-lookup"><span data-stu-id="51e40-243">Besides the **Disable** setting, all settings will use the highest available patch version.</span></span>

<span data-ttu-id="51e40-244">Domyślnie, jeśli żądana wersja (określona w `.runtimeconfig.json` aplikacji) jest wersją wydaną, tylko wersje wydań są brane pod uwagę w przód.</span><span class="sxs-lookup"><span data-stu-id="51e40-244">By default, if the requested version (as specified in `.runtimeconfig.json` for the application) is a release version, only release versions are considered for roll forward.</span></span> <span data-ttu-id="51e40-245">Wszystkie wersje wstępne zostaną zignorowane.</span><span class="sxs-lookup"><span data-stu-id="51e40-245">Any pre-release versions are ignored.</span></span> <span data-ttu-id="51e40-246">W przypadku braku zgodnej wersji wydania są brane pod uwagę wersje wersji wstępnej.</span><span class="sxs-lookup"><span data-stu-id="51e40-246">If there is no matching release version, then pre-release versions are taken into account.</span></span> <span data-ttu-id="51e40-247">To zachowanie można zmienić przez ustawienie `DOTNET_ROLL_FORWARD_TO_PRERELEASE=1` , w którym przypadku zawsze są brane pod uwagę wszystkie wersje.</span><span class="sxs-lookup"><span data-stu-id="51e40-247">This behavior can be changed by setting `DOTNET_ROLL_FORWARD_TO_PRERELEASE=1`, in which case all versions are always considered.</span></span>

### <a name="build-copies-dependencies"></a><span data-ttu-id="51e40-248">Zależności kompilacji kopii</span><span class="sxs-lookup"><span data-stu-id="51e40-248">Build copies dependencies</span></span>

<span data-ttu-id="51e40-249">`dotnet build`Polecenie teraz kopiuje zależności NuGet dla aplikacji z pamięci podręcznej NuGet do folderu danych wyjściowych kompilacji.</span><span class="sxs-lookup"><span data-stu-id="51e40-249">The `dotnet build` command now copies NuGet dependencies for your application from the NuGet cache to the build output folder.</span></span> <span data-ttu-id="51e40-250">Wcześniej zależności były kopiowane tylko w ramach programu `dotnet publish` .</span><span class="sxs-lookup"><span data-stu-id="51e40-250">Previously, dependencies were only copied as part of `dotnet publish`.</span></span>

<span data-ttu-id="51e40-251">Istnieją pewne operacje, takie jak łączenie i publikowanie stron Razor, które nadal wymagają publikacji.</span><span class="sxs-lookup"><span data-stu-id="51e40-251">There are some operations, like linking and razor page publishing that will still require publishing.</span></span>

### <a name="local-tools"></a><span data-ttu-id="51e40-252">Narzędzia lokalne</span><span class="sxs-lookup"><span data-stu-id="51e40-252">Local tools</span></span>

<span data-ttu-id="51e40-253">Środowisko .NET Core 3,0 zawiera wprowadzenie do narzędzi lokalnych.</span><span class="sxs-lookup"><span data-stu-id="51e40-253">.NET Core 3.0 introduces local tools.</span></span> <span data-ttu-id="51e40-254">Narzędzia lokalne są podobne do [narzędzi globalnych](../tools/global-tools.md) , ale są skojarzone z konkretną lokalizacją na dysku.</span><span class="sxs-lookup"><span data-stu-id="51e40-254">Local tools are similar to [global tools](../tools/global-tools.md) but are associated with a particular location on disk.</span></span> <span data-ttu-id="51e40-255">Narzędzia lokalne nie są dostępne globalnie i są dystrybuowane jako pakiety NuGet.</span><span class="sxs-lookup"><span data-stu-id="51e40-255">Local tools aren't available globally and are distributed as NuGet packages.</span></span>

> [!WARNING]
> <span data-ttu-id="51e40-256">Jeśli podjęto próbę skorzystania z narzędzi lokalnych w programie .NET Core 3,0 w wersji zapoznawczej 1, takiej jak uruchamianie `dotnet tool restore` lub `dotnet tool install` , Usuń folder pamięci podręcznej narzędzi lokalnych</span><span class="sxs-lookup"><span data-stu-id="51e40-256">If you tried local tools in .NET Core 3.0 Preview 1, such as running `dotnet tool restore` or `dotnet tool install`, delete the local tools cache folder.</span></span> <span data-ttu-id="51e40-257">W przeciwnym razie narzędzia lokalne nie będą działały w żadnej nowszej wersji.</span><span class="sxs-lookup"><span data-stu-id="51e40-257">Otherwise, local tools won't work on any newer release.</span></span> <span data-ttu-id="51e40-258">Ten folder znajduje się w lokalizacji:</span><span class="sxs-lookup"><span data-stu-id="51e40-258">This folder is located at:</span></span>
>
> <span data-ttu-id="51e40-259">W systemie macOS, Linux:`rm -r $HOME/.dotnet/toolResolverCache`</span><span class="sxs-lookup"><span data-stu-id="51e40-259">On macOS, Linux: `rm -r $HOME/.dotnet/toolResolverCache`</span></span>
>
> <span data-ttu-id="51e40-260">W systemie Windows:`rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`</span><span class="sxs-lookup"><span data-stu-id="51e40-260">On Windows: `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`</span></span>

<span data-ttu-id="51e40-261">Narzędzia lokalne są zależne od nazwy pliku manifestu `dotnet-tools.json` w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="51e40-261">Local tools rely on a manifest file name `dotnet-tools.json` in your current directory.</span></span> <span data-ttu-id="51e40-262">Ten plik manifestu definiuje narzędzia do udostępnienia w tym folderze i poniżej.</span><span class="sxs-lookup"><span data-stu-id="51e40-262">This manifest file defines the tools to be available at that folder and below.</span></span> <span data-ttu-id="51e40-263">Plik manifestu można dystrybuować z kodem, aby upewnić się, że każda osoba, która współpracuje z kodem, będzie mogła przywrócić i korzystać z tych samych narzędzi.</span><span class="sxs-lookup"><span data-stu-id="51e40-263">You can distribute the manifest file with your code to ensure that anyone who works with your code can restore and use the same tools.</span></span>

<span data-ttu-id="51e40-264">W przypadku narzędzi globalnych i lokalnych wymagana jest zgodna wersja środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="51e40-264">For both global and local tools, a compatible version of the runtime is required.</span></span> <span data-ttu-id="51e40-265">Wiele narzędzi obecnie na NuGet.org docelowym środowiska uruchomieniowego .NET Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="51e40-265">Many tools currently on NuGet.org target .NET Core Runtime 2.1.</span></span> <span data-ttu-id="51e40-266">Aby zainstalować te narzędzia globalnie lub lokalnie, nadal trzeba zainstalować [środowisko uruchomieniowe NET Core 2,1](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="51e40-266">To install these tools globally or locally, you would still need to install the [NET Core 2.1 Runtime](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span>

### <a name="new-globaljson-options"></a><span data-ttu-id="51e40-267">Nowe opcje globalne. JSON</span><span class="sxs-lookup"><span data-stu-id="51e40-267">New global.json options</span></span>

<span data-ttu-id="51e40-268">Plik *Global. JSON* zawiera nowe opcje, które zapewniają większą elastyczność podczas próby zdefiniowania używanej wersji zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="51e40-268">The *global.json* file has new options that provide more flexibility when you're trying to define which version of the .NET Core SDK is used.</span></span> <span data-ttu-id="51e40-269">Nowe opcje są następujące:</span><span class="sxs-lookup"><span data-stu-id="51e40-269">The new options are:</span></span>

- <span data-ttu-id="51e40-270">`allowPrerelease`: Wskazuje, czy program rozpoznawania SDK powinien wziąć pod uwagę wersje wstępne podczas wybierania wersji zestawu SDK do użycia.</span><span class="sxs-lookup"><span data-stu-id="51e40-270">`allowPrerelease`: Indicates whether the SDK resolver should consider prerelease versions when selecting the SDK version to use.</span></span>
- <span data-ttu-id="51e40-271">`rollForward`: Wskazuje zasady wycofywania, które mają być używane podczas wybierania wersji zestawu SDK, jako rezerwy w przypadku braku określonej wersji zestawu SDK lub jako dyrektywy do korzystania z wyższej wersji.</span><span class="sxs-lookup"><span data-stu-id="51e40-271">`rollForward`: Indicates the roll-forward policy to use when selecting an SDK version, either as a fallback when a specific SDK version is missing or as a directive to use a higher version.</span></span>

<span data-ttu-id="51e40-272">Aby uzyskać więcej informacji na temat zmian, w tym wartości domyślnych, obsługiwanych wartości i nowych reguł dopasowania, zobacz [Global. JSON — Omówienie](../tools/global-json.md).</span><span class="sxs-lookup"><span data-stu-id="51e40-272">For more information about the changes including default values, supported values, and new matching rules, see [global.json overview](../tools/global-json.md).</span></span>

### <a name="smaller-garbage-collection-heap-sizes"></a><span data-ttu-id="51e40-273">Mniejsze rozmiary sterty wyrzucania elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="51e40-273">Smaller Garbage Collection heap sizes</span></span>

<span data-ttu-id="51e40-274">Rozmiar sterty domyślnej modułu wyrzucania elementów bezużytecznych został zmniejszony z powodu mniejszej ilości pamięci w programie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="51e40-274">The Garbage Collector's default heap size has been reduced resulting in .NET Core using less memory.</span></span> <span data-ttu-id="51e40-275">Ta zmiana jest lepsza w porównaniu z budżetem alokacji generacji 0 z nowoczesnymi rozmiarami pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="51e40-275">This change better aligns with the generation 0 allocation budget with modern processor cache sizes.</span></span>

### <a name="garbage-collection-large-page-support"></a><span data-ttu-id="51e40-276">Obsługa dużej strony odzyskiwania pamięci</span><span class="sxs-lookup"><span data-stu-id="51e40-276">Garbage Collection Large Page support</span></span>

<span data-ttu-id="51e40-277">Duże strony (znane również jako ogromne strony w systemie Linux) to funkcja, w której system operacyjny może ustalić obszary pamięci większe niż rozmiar strony natywnej (często 4K), aby zwiększyć wydajność aplikacji żądającej tych dużych stron.</span><span class="sxs-lookup"><span data-stu-id="51e40-277">Large Pages (also known as Huge Pages on Linux) is a feature where the operating system is able to establish memory regions larger than the native page size (often 4K) to improve performance of the application requesting these large pages.</span></span>

<span data-ttu-id="51e40-278">Moduł wyrzucania elementów bezużytecznych można teraz skonfigurować przy użyciu ustawienia **GCLargePages** jako funkcji wyboru do przydzielania dużych stron w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="51e40-278">The Garbage Collector can now be configured with the **GCLargePages** setting as an opt-in feature to choose to allocate large pages on Windows.</span></span>

## <a name="windows-desktop--com"></a><span data-ttu-id="51e40-279">Windows Desktop & COM</span><span class="sxs-lookup"><span data-stu-id="51e40-279">Windows Desktop & COM</span></span>

### <a name="net-core-sdk-windows-installer"></a><span data-ttu-id="51e40-280">Zestaw .NET Core SDK Instalator Windows</span><span class="sxs-lookup"><span data-stu-id="51e40-280">.NET Core SDK Windows Installer</span></span>

<span data-ttu-id="51e40-281">Instalator MSI dla systemu Windows został zmieniony począwszy od platformy .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="51e40-281">The MSI installer for Windows has changed starting with .NET Core 3.0.</span></span> <span data-ttu-id="51e40-282">Instalatorzy zestawu SDK teraz uaktualniają wersje funkcji zestawu SDK na miejscu.</span><span class="sxs-lookup"><span data-stu-id="51e40-282">The SDK installers will now upgrade SDK feature-band releases in place.</span></span> <span data-ttu-id="51e40-283">Paski funkcji są zdefiniowane w grupach *setek* w sekcji *poprawka* numeru wersji.</span><span class="sxs-lookup"><span data-stu-id="51e40-283">Feature bands are defined in the *hundreds* groups in the *patch* section of the version number.</span></span> <span data-ttu-id="51e40-284">Na przykład \*\*3,0._ 101_ \*\* i \*\*3,0._ 201_ \*\* są wersje w dwóch różnych warstwach funkcji podczas \*\*3,0._ 101_ \*\* i \*\*3,0._ 199_ \*\* znajdują się w tej samej paśmie funkcji.</span><span class="sxs-lookup"><span data-stu-id="51e40-284">For example, **3.0._101_** and **3.0._201_** are versions in two different feature bands while **3.0._101_** and **3.0._199_** are in the same feature band.</span></span> <span data-ttu-id="51e40-285">I, w przypadku zestaw .NET Core SDK \*\*3,0._ 101_ \*\* jest zainstalowana, zestaw .NET Core SDK \*\*3,0._ 100_ \*\* zostanie usunięta z komputera, jeśli istnieje.</span><span class="sxs-lookup"><span data-stu-id="51e40-285">And, when .NET Core SDK **3.0._101_** is installed, .NET Core SDK **3.0._100_** will be removed from the machine if it exists.</span></span> <span data-ttu-id="51e40-286">Gdy zestaw .NET Core SDK \*\*3,0._ 200_ \*\* jest zainstalowana na tym samym komputerze, zestaw .NET Core SDK \*\*3,0._ 101_ \*\* nie zostanie usunięta.</span><span class="sxs-lookup"><span data-stu-id="51e40-286">When .NET Core SDK **3.0._200_** is installed on the same machine, .NET Core SDK **3.0._101_** won't be removed.</span></span>

<span data-ttu-id="51e40-287">Aby uzyskać więcej informacji na temat przechowywania wersji, zobacz [Omówienie wersji platformy .NET Core](../versions/index.md).</span><span class="sxs-lookup"><span data-stu-id="51e40-287">For more information about versioning, see [Overview of how .NET Core is versioned](../versions/index.md).</span></span>

### <a name="windows-desktop"></a><span data-ttu-id="51e40-288">Pulpit systemu Windows</span><span class="sxs-lookup"><span data-stu-id="51e40-288">Windows desktop</span></span>

<span data-ttu-id="51e40-289">Program .NET Core 3,0 obsługuje aplikacje klasyczne systemu Windows przy użyciu Windows Presentation Foundation (WPF) i Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="51e40-289">.NET Core 3.0 supports Windows desktop applications using Windows Presentation Foundation (WPF) and Windows Forms.</span></span> <span data-ttu-id="51e40-290">Te struktury obsługują również korzystanie z nowoczesnych kontrolek i stylów Fluent z poziomu biblioteki XAML interfejsu użytkownika systemu Windows (WinUI) za pośrednictwem [wysp XAML](/windows/uwp/xaml-platform/xaml-host-controls).</span><span class="sxs-lookup"><span data-stu-id="51e40-290">These frameworks also support using modern controls and Fluent styling from the Windows UI XAML Library (WinUI) via [XAML islands](/windows/uwp/xaml-platform/xaml-host-controls).</span></span>

<span data-ttu-id="51e40-291">Składnik pulpitu systemu Windows jest częścią zestawu SDK systemu Windows .NET Core 3,0.</span><span class="sxs-lookup"><span data-stu-id="51e40-291">The Windows Desktop component is part of the Windows .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="51e40-292">Nową aplikację WPF lub Windows Forms można utworzyć przy użyciu następujących `dotnet` poleceń:</span><span class="sxs-lookup"><span data-stu-id="51e40-292">You can create a new WPF or Windows Forms app with the following `dotnet` commands:</span></span>

```dotnetcli
dotnet new wpf
dotnet new winforms
```

<span data-ttu-id="51e40-293">Program Visual Studio 2019 dodaje **nowe szablony projektów** dla platformy .net Core 3,0 Windows Forms i WPF.</span><span class="sxs-lookup"><span data-stu-id="51e40-293">Visual Studio 2019 adds **New Project** templates for .NET Core 3.0 Windows Forms and WPF.</span></span>

<span data-ttu-id="51e40-294">Aby uzyskać więcej informacji na temat sposobu przenoszenia istniejącej aplikacji .NET Framework, zobacz [port WPF projekty](../../desktop-wpf/migration/convert-project-from-net-framework.md) i [projekty Windows Forms portów](../porting/winforms.md).</span><span class="sxs-lookup"><span data-stu-id="51e40-294">For more information about how to port an existing .NET Framework application, see [Port WPF projects](../../desktop-wpf/migration/convert-project-from-net-framework.md) and [Port Windows Forms projects](../porting/winforms.md).</span></span>

#### <a name="winforms-high-dpi"></a><span data-ttu-id="51e40-295">Bardzo wysokie wartości DPI</span><span class="sxs-lookup"><span data-stu-id="51e40-295">WinForms high DPI</span></span>

<span data-ttu-id="51e40-296">Aplikacje .NET Core Windows Forms mogą ustawiać tryb wysokiej rozdzielczości DPI przy użyciu <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="51e40-296">.NET Core Windows Forms applications can set high DPI mode with <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType>.</span></span> <span data-ttu-id="51e40-297">`SetHighDpiMode`Metoda ustawia odpowiedni tryb wysokiej rozdzielczości DPI, chyba że ustawienie zostało ustawione za pomocą innych metod, takich jak `App.Manifest` lub P/Invoke przed `Application.Run` .</span><span class="sxs-lookup"><span data-stu-id="51e40-297">The `SetHighDpiMode` method sets the corresponding high DPI mode unless the setting has been set by other means like `App.Manifest` or P/Invoke before `Application.Run`.</span></span>

<span data-ttu-id="51e40-298">Możliwe `highDpiMode` wartości wyrażone przez <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType> Wyliczenie są następujące:</span><span class="sxs-lookup"><span data-stu-id="51e40-298">The possible `highDpiMode` values, as expressed by the <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType> enum are:</span></span>

- `DpiUnaware`
- `SystemAware`
- `PerMonitor`
- `PerMonitorV2`
- `DpiUnawareGdiScaled`

<span data-ttu-id="51e40-299">Aby uzyskać więcej informacji na temat trybów wysokiej rozdzielczości DPI, zobacz [Tworzenie aplikacji klasycznych o wysokiej rozdzielczości DPI w systemie Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows).</span><span class="sxs-lookup"><span data-stu-id="51e40-299">For more information about high DPI modes, see [High DPI Desktop Application Development on Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows).</span></span>

### <a name="create-com-components"></a><span data-ttu-id="51e40-300">Tworzenie składników COM</span><span class="sxs-lookup"><span data-stu-id="51e40-300">Create COM components</span></span>

<span data-ttu-id="51e40-301">W systemie Windows można teraz tworzyć zarządzane składniki COM.</span><span class="sxs-lookup"><span data-stu-id="51e40-301">On Windows, you can now create COM-callable managed components.</span></span> <span data-ttu-id="51e40-302">Ta funkcja ma kluczowe znaczenie dla korzystania z platformy .NET Core z modelami dodatków COM, a także do zapewnienia parzystości .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="51e40-302">This capability is critical to use .NET Core with COM add-in models and also to provide parity with .NET Framework.</span></span>

<span data-ttu-id="51e40-303">W przeciwieństwie do .NET Framework, w którym *Biblioteka mscoree. dll* była używana jako serwer com, podczas kompilowania składnika com program .NET Core doda natywną bibliotekę DLL uruchamiania do katalogu *bin* .</span><span class="sxs-lookup"><span data-stu-id="51e40-303">Unlike .NET Framework where the *mscoree.dll* was used as the COM server, .NET Core will add a native launcher dll to the *bin* directory when you build your COM component.</span></span>

<span data-ttu-id="51e40-304">Przykład sposobu tworzenia składnika modelu COM i korzystania z niego można znaleźć w [demonstracji modelu COM](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).</span><span class="sxs-lookup"><span data-stu-id="51e40-304">For an example of how to create a COM component and consume it, see the [COM Demo](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).</span></span>

### <a name="windows-native-interop"></a><span data-ttu-id="51e40-305">Windows Native Interop</span><span class="sxs-lookup"><span data-stu-id="51e40-305">Windows Native Interop</span></span>

<span data-ttu-id="51e40-306">System Windows oferuje bogaty natywny interfejs API w postaci prostych interfejsów API języka C, COM i WinRT.</span><span class="sxs-lookup"><span data-stu-id="51e40-306">Windows offers a rich native API in the form of flat C APIs, COM, and WinRT.</span></span> <span data-ttu-id="51e40-307">Podczas gdy platforma .NET Core obsługuje funkcję **P/Invoke**, program .net Core 3,0 dodaje możliwość **CoCreate interfejsów API modelu COM** i **aktywowania interfejsów API WinRT**.</span><span class="sxs-lookup"><span data-stu-id="51e40-307">While .NET Core supports **P/Invoke**, .NET Core 3.0 adds the ability to **CoCreate COM APIs** and **Activate WinRT APIs**.</span></span> <span data-ttu-id="51e40-308">Aby zapoznać się z przykładem kodu, zobacz [Demonstracja programu Excel](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).</span><span class="sxs-lookup"><span data-stu-id="51e40-308">For a code example, see the [Excel Demo](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).</span></span>

### <a name="msix-deployment"></a><span data-ttu-id="51e40-309">Wdrożenie MSIX</span><span class="sxs-lookup"><span data-stu-id="51e40-309">MSIX Deployment</span></span>

<span data-ttu-id="51e40-310">[MSIX](https://docs.microsoft.com/windows/msix/) to nowy format pakietu aplikacji systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="51e40-310">[MSIX](https://docs.microsoft.com/windows/msix/) is a new Windows application package format.</span></span> <span data-ttu-id="51e40-311">Można go użyć do wdrożenia aplikacji klasycznych platformy .NET Core 3,0 w systemie Windows 10.</span><span class="sxs-lookup"><span data-stu-id="51e40-311">It can be used to deploy .NET Core 3.0 desktop applications to Windows 10.</span></span>

<span data-ttu-id="51e40-312">[Projekt pakietu aplikacji systemu Windows](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), dostępny w programie Visual Studio 2019, umożliwia tworzenie pakietów MSIX przy użyciu [samodzielnych](../deploying/index.md#publish-self-contained) aplikacji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="51e40-312">The [Windows Application Packaging Project](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), available in Visual Studio 2019, allows you to create MSIX packages with [self-contained](../deploying/index.md#publish-self-contained) .NET Core applications.</span></span>

<span data-ttu-id="51e40-313">Plik projektu .NET Core musi określać obsługiwane środowiska uruchomieniowe we `<RuntimeIdentifiers>` Właściwości:</span><span class="sxs-lookup"><span data-stu-id="51e40-313">The .NET Core project file must specify the supported runtimes in the `<RuntimeIdentifiers>` property:</span></span>

```xml
<RuntimeIdentifiers>win-x86;win-x64</RuntimeIdentifiers>
```

## <a name="linux-improvements"></a><span data-ttu-id="51e40-314">Udoskonalenia systemu Linux</span><span class="sxs-lookup"><span data-stu-id="51e40-314">Linux improvements</span></span>

### <a name="serialport-for-linux"></a><span data-ttu-id="51e40-315">Klasy SerialPort dla systemu Linux</span><span class="sxs-lookup"><span data-stu-id="51e40-315">SerialPort for Linux</span></span>

<span data-ttu-id="51e40-316">Program .NET Core 3,0 zapewnia podstawową pomoc techniczną dla systemu <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> Linux.</span><span class="sxs-lookup"><span data-stu-id="51e40-316">.NET Core 3.0 provides basic support for <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> on Linux.</span></span>

<span data-ttu-id="51e40-317">Wcześniej platforma .NET Core jest obsługiwana tylko `SerialPort` w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="51e40-317">Previously, .NET Core only supported using `SerialPort` on Windows.</span></span>

<span data-ttu-id="51e40-318">Aby uzyskać więcej informacji o ograniczonej obsłudze portu szeregowego w systemie Linux, zobacz artykuł [dotyczący usługi GitHub #33146](https://github.com/dotnet/corefx/issues/33146).</span><span class="sxs-lookup"><span data-stu-id="51e40-318">For more information about the limited support for the serial port on Linux, see [GitHub issue #33146](https://github.com/dotnet/corefx/issues/33146).</span></span>

### <a name="docker-and-cgroup-memory-limits"></a><span data-ttu-id="51e40-319">Limity pamięci Docker i cgroup</span><span class="sxs-lookup"><span data-stu-id="51e40-319">Docker and cgroup memory Limits</span></span>

<span data-ttu-id="51e40-320">Uruchamianie programu .NET Core 3,0 w systemie Linux przy użyciu platformy Docker działa lepiej z limitami pamięci cgroup.</span><span class="sxs-lookup"><span data-stu-id="51e40-320">Running .NET Core 3.0 on Linux with Docker works better with cgroup memory limits.</span></span> <span data-ttu-id="51e40-321">Uruchamianie kontenera Docker z limitami pamięci, na przykład z `docker run -m` , zmienia sposób działania programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="51e40-321">Running a Docker container with memory limits, such as with `docker run -m`, changes how .NET Core behaves.</span></span>

- <span data-ttu-id="51e40-322">Domyślny rozmiar sterty modułu wyrzucania elementów bezużytecznych (GC): maksymalnie 20 MB lub 75% limitu pamięci w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="51e40-322">Default Garbage Collector (GC) heap size: maximum of 20 mb or 75% of the memory limit on the container.</span></span>
- <span data-ttu-id="51e40-323">Rozmiar jawny można ustawić jako liczbę bezwzględną lub procent limitu cgroup.</span><span class="sxs-lookup"><span data-stu-id="51e40-323">Explicit size can be set as an absolute number or percentage of cgroup limit.</span></span>
- <span data-ttu-id="51e40-324">Minimalny zarezerwowany rozmiar segmentu na stos GC to 16 MB.</span><span class="sxs-lookup"><span data-stu-id="51e40-324">Minimum reserved segment size per GC heap is 16 mb.</span></span> <span data-ttu-id="51e40-325">Ten rozmiar zmniejsza liczbę stert, które są tworzone na maszynach.</span><span class="sxs-lookup"><span data-stu-id="51e40-325">This size reduces the number of heaps that are created on machines.</span></span>

### <a name="gpio-support-for-raspberry-pi"></a><span data-ttu-id="51e40-326">Obsługa interfejsu GPIO dla Raspberry Pi</span><span class="sxs-lookup"><span data-stu-id="51e40-326">GPIO Support for Raspberry Pi</span></span>

<span data-ttu-id="51e40-327">Do programu NuGet zostały wydane dwa pakiety, których można użyć do programowania interfejsu GPIO:</span><span class="sxs-lookup"><span data-stu-id="51e40-327">Two packages have been released to NuGet that you can use for GPIO programming:</span></span>

- [<span data-ttu-id="51e40-328">System. Device. GPIO</span><span class="sxs-lookup"><span data-stu-id="51e40-328">System.Device.Gpio</span></span>](https://www.nuget.org/packages/System.Device.Gpio)
- [<span data-ttu-id="51e40-329">IoT. Device. bindings</span><span class="sxs-lookup"><span data-stu-id="51e40-329">Iot.Device.Bindings</span></span>](https://www.nuget.org/packages/Iot.Device.Bindings)

<span data-ttu-id="51e40-330">Pakiety GPIO obejmują interfejsy API dla urządzeń z interfejsem *GPIO*, *SPI*, *I2C*i *PWM* .</span><span class="sxs-lookup"><span data-stu-id="51e40-330">The GPIO packages include APIs for *GPIO*, *SPI*, *I2C*, and *PWM* devices.</span></span> <span data-ttu-id="51e40-331">Pakiet powiązań IoT obejmuje powiązania urządzeń.</span><span class="sxs-lookup"><span data-stu-id="51e40-331">The IoT bindings package includes device bindings.</span></span> <span data-ttu-id="51e40-332">Aby uzyskać więcej informacji, zobacz [repozytorium GitHub](https://github.com/dotnet/iot/blob/master/src/devices/).</span><span class="sxs-lookup"><span data-stu-id="51e40-332">For more information, see the [devices GitHub repo](https://github.com/dotnet/iot/blob/master/src/devices/).</span></span>

### <a name="arm64-linux-support"></a><span data-ttu-id="51e40-333">Obsługa systemu Linux ARM64</span><span class="sxs-lookup"><span data-stu-id="51e40-333">ARM64 Linux support</span></span>

<span data-ttu-id="51e40-334">Program .NET Core 3,0 dodaje obsługę ARM64 dla systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="51e40-334">.NET Core 3.0 adds support for ARM64 for Linux.</span></span> <span data-ttu-id="51e40-335">Podstawowy przypadek użycia dla ARM64 jest obecnie z scenariuszami IoT.</span><span class="sxs-lookup"><span data-stu-id="51e40-335">The primary use case for ARM64 is currently with IoT scenarios.</span></span> <span data-ttu-id="51e40-336">Aby uzyskać więcej informacji, zobacz temat [stan arm64 programu .NET Core](https://github.com/dotnet/announcements/issues/82).</span><span class="sxs-lookup"><span data-stu-id="51e40-336">For more information, see [.NET Core ARM64 Status](https://github.com/dotnet/announcements/issues/82).</span></span>

<span data-ttu-id="51e40-337">[Obrazy Docker dla platformy .NET Core w systemie arm64](https://hub.docker.com/r/microsoft/dotnet/) są dostępne dla Alpine, Debian i Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="51e40-337">[Docker images for .NET Core on ARM64](https://hub.docker.com/r/microsoft/dotnet/) are available for Alpine, Debian, and Ubuntu.</span></span>

> [!NOTE]
> <span data-ttu-id="51e40-338">**Arm64** Obsługa systemu Windows nie jest jeszcze dostępna.</span><span class="sxs-lookup"><span data-stu-id="51e40-338">**ARM64** Windows support isn't yet available.</span></span>

## <a name="security"></a><span data-ttu-id="51e40-339">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="51e40-339">Security</span></span>

### <a name="tls-13--openssl-111-on-linux"></a><span data-ttu-id="51e40-340">TLS 1,3 & OpenSSL 1.1.1 w systemie Linux</span><span class="sxs-lookup"><span data-stu-id="51e40-340">TLS 1.3 & OpenSSL 1.1.1 on Linux</span></span>

<span data-ttu-id="51e40-341">Platforma .NET Core wykorzystuje teraz zalety [protokołu TLS 1,3 w OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), gdy jest on dostępny w danym środowisku.</span><span class="sxs-lookup"><span data-stu-id="51e40-341">.NET Core now takes advantage of [TLS 1.3 support in OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), when it's available in a given environment.</span></span> <span data-ttu-id="51e40-342">Z protokołem TLS 1,3:</span><span class="sxs-lookup"><span data-stu-id="51e40-342">With TLS 1.3:</span></span>

- <span data-ttu-id="51e40-343">Czas połączenia jest ulepszony ze zredukowanymi przedziałami rundy między klientem i serwerem.</span><span class="sxs-lookup"><span data-stu-id="51e40-343">Connection times are improved with reduced round trips required between the client and server.</span></span>
- <span data-ttu-id="51e40-344">Ulepszone zabezpieczenia spowodowane usuwaniem różnych przestarzałych i niezabezpieczonych algorytmów kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="51e40-344">Improved security because of the removal of various obsolete and insecure cryptographic algorithms.</span></span>

<span data-ttu-id="51e40-345">Jeśli jest dostępny, program .NET Core 3,0 używa **OpenSSL 1.1.1**, **OpenSSL 1.1.0**lub **OpenSSL 1.0.2** w systemie Linux.</span><span class="sxs-lookup"><span data-stu-id="51e40-345">When available, .NET Core 3.0 uses **OpenSSL 1.1.1**, **OpenSSL 1.1.0**, or **OpenSSL 1.0.2** on a Linux system.</span></span> <span data-ttu-id="51e40-346">Gdy **OpenSSL 1.1.1** jest dostępny, oba <xref:System.Net.Security.SslStream?displayProperty=nameWithType> <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> typy i używają **protokołu TLS 1,3** (przy założeniu, że zarówno klient, jak i serwer obsługują **protokół TLS 1,3**).</span><span class="sxs-lookup"><span data-stu-id="51e40-346">When **OpenSSL 1.1.1** is available, both <xref:System.Net.Security.SslStream?displayProperty=nameWithType> and <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> types will use **TLS 1.3** (assuming both the client and server support **TLS 1.3**).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="51e40-347">Systemy Windows i macOS nie obsługują jeszcze **protokołu TLS 1,3**.</span><span class="sxs-lookup"><span data-stu-id="51e40-347">Windows and macOS do not yet support **TLS 1.3**.</span></span> <span data-ttu-id="51e40-348">Platforma .NET Core 3,0 będzie obsługiwać **protokół TLS 1,3** w tych systemach operacyjnych, gdy będzie dostępna pomoc techniczna.</span><span class="sxs-lookup"><span data-stu-id="51e40-348">.NET Core 3.0 will support **TLS 1.3** on these operating systems when support becomes available.</span></span>

<span data-ttu-id="51e40-349">Poniższy przykład w języku C# 8,0 ilustruje platformę .NET Core 3,0 na Ubuntu 18,10 z <https://www.cloudflare.com> :</span><span class="sxs-lookup"><span data-stu-id="51e40-349">The following C# 8.0 example demonstrates .NET Core 3.0 on Ubuntu 18.10 connecting to <https://www.cloudflare.com>:</span></span>

[!code-csharp[TLSExample](~/samples/snippets/core/whats-new/whats-new-in-30/cs/TLS.cs#TLS)]

### <a name="cryptography-ciphers"></a><span data-ttu-id="51e40-350">Szyfrowanie kryptografii</span><span class="sxs-lookup"><span data-stu-id="51e40-350">Cryptography ciphers</span></span>

<span data-ttu-id="51e40-351">Program .NET 3,0 dodaje obsługę szyfrów **AES-GCM** i **AES-CCM** , implementowanych za pomocą <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> i <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="51e40-351">.NET 3.0 adds support for **AES-GCM** and **AES-CCM** ciphers, implemented with <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> and <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> respectively.</span></span> <span data-ttu-id="51e40-352">Te algorytmy są [uwierzytelnianiem uwierzytelnianym przy użyciu algorytmów danych skojarzenia (AEAD)](https://en.wikipedia.org/wiki/Authenticated_encryption).</span><span class="sxs-lookup"><span data-stu-id="51e40-352">These algorithms are both [Authenticated Encryption with Association Data (AEAD) algorithms](https://en.wikipedia.org/wiki/Authenticated_encryption).</span></span>

<span data-ttu-id="51e40-353">Poniższy kod ilustruje użycie `AesGcm` szyfru do szyfrowania i odszyfrowywania danych losowych.</span><span class="sxs-lookup"><span data-stu-id="51e40-353">The following code demonstrates using `AesGcm` cipher to encrypt and decrypt random data.</span></span>

[!code-csharp[AesGcm](~/samples/snippets/core/whats-new/whats-new-in-30/cs/Cipher.cs#AesGcm)]

### <a name="cryptographic-key-importexport"></a><span data-ttu-id="51e40-354">Import/Eksport klucza kryptograficznego</span><span class="sxs-lookup"><span data-stu-id="51e40-354">Cryptographic Key Import/Export</span></span>

<span data-ttu-id="51e40-355">Program .NET Core 3,0 obsługuje importowanie i eksportowanie asymetrycznych kluczy publicznych i prywatnych z formatów standardowych.</span><span class="sxs-lookup"><span data-stu-id="51e40-355">.NET Core 3.0 supports the import and export of asymmetric public and private keys from standard formats.</span></span> <span data-ttu-id="51e40-356">Nie musisz używać certyfikatu X. 509.</span><span class="sxs-lookup"><span data-stu-id="51e40-356">You don't need to use an X.509 certificate.</span></span>

<span data-ttu-id="51e40-357">Wszystkie typy kluczy, takie jak *RSA*, *DSA*, *ECDSA*i *ECDiffieHellman*, obsługują następujące formaty:</span><span class="sxs-lookup"><span data-stu-id="51e40-357">All key types, such as *RSA*, *DSA*, *ECDsa*, and *ECDiffieHellman*, support the following formats:</span></span>

- <span data-ttu-id="51e40-358">**Klucz publiczny**</span><span class="sxs-lookup"><span data-stu-id="51e40-358">**Public Key**</span></span>
  - <span data-ttu-id="51e40-359">SubjectPublicKeyInfo X. 509</span><span class="sxs-lookup"><span data-stu-id="51e40-359">X.509 SubjectPublicKeyInfo</span></span>

- <span data-ttu-id="51e40-360">**Klucz prywatny**</span><span class="sxs-lookup"><span data-stu-id="51e40-360">**Private key**</span></span>
  - <span data-ttu-id="51e40-361">PrivateKeyInfo PKCS # 8</span><span class="sxs-lookup"><span data-stu-id="51e40-361">PKCS#8 PrivateKeyInfo</span></span>
  - <span data-ttu-id="51e40-362">EncryptedPrivateKeyInfo PKCS # 8</span><span class="sxs-lookup"><span data-stu-id="51e40-362">PKCS#8 EncryptedPrivateKeyInfo</span></span>

<span data-ttu-id="51e40-363">Klucze RSA obsługują również:</span><span class="sxs-lookup"><span data-stu-id="51e40-363">RSA keys also support:</span></span>

- <span data-ttu-id="51e40-364">**Klucz publiczny**</span><span class="sxs-lookup"><span data-stu-id="51e40-364">**Public Key**</span></span>
  - <span data-ttu-id="51e40-365">RSAPublicKey PKCS # 1</span><span class="sxs-lookup"><span data-stu-id="51e40-365">PKCS#1 RSAPublicKey</span></span>

- <span data-ttu-id="51e40-366">**Klucz prywatny**</span><span class="sxs-lookup"><span data-stu-id="51e40-366">**Private key**</span></span>
  - <span data-ttu-id="51e40-367">RSAPrivateKey PKCS # 1</span><span class="sxs-lookup"><span data-stu-id="51e40-367">PKCS#1 RSAPrivateKey</span></span>

<span data-ttu-id="51e40-368">Metody eksportowania generują dane binarne kodowane algorytmem DER, a metody importowe oczekują na to samo.</span><span class="sxs-lookup"><span data-stu-id="51e40-368">The export methods produce DER-encoded binary data, and the import methods expect the same.</span></span> <span data-ttu-id="51e40-369">Jeśli klucz jest przechowywany w formacie PEM przyjaznym dla tekstu, wywołujący będzie musiał odkodować zawartość przed wywołaniem metody Import.</span><span class="sxs-lookup"><span data-stu-id="51e40-369">If a key is stored in the text-friendly PEM format, the caller will need to base64-decode the content before calling an import method.</span></span>

[!code-csharp[RSA](~/samples/snippets/core/whats-new/whats-new-in-30/cs/RSA.cs#Rsa)]

<span data-ttu-id="51e40-370">Można sprawdzać pliki **PKCS # 8** <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType> i pliki **PFX/PKCS # 12** <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="51e40-370">**PKCS#8** files can be inspected with <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType> and **PFX/PKCS#12** files can be inspected with <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType>.</span></span> <span data-ttu-id="51e40-371">Pliki **PFX/PKCS # 12** można manipulować przy użyciu programu <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="51e40-371">**PFX/PKCS#12** files can be manipulated with <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType>.</span></span>

## <a name="net-core-30-api-changes"></a><span data-ttu-id="51e40-372">Zmiany interfejsu API programu .NET Core 3,0</span><span class="sxs-lookup"><span data-stu-id="51e40-372">.NET Core 3.0 API changes</span></span>

### <a name="ranges-and-indices"></a><span data-ttu-id="51e40-373">Zakresy i indeksy</span><span class="sxs-lookup"><span data-stu-id="51e40-373">Ranges and indices</span></span>

<span data-ttu-id="51e40-374">Nowy <xref:System.Index?displayProperty=nameWithType> Typ może służyć do indeksowania.</span><span class="sxs-lookup"><span data-stu-id="51e40-374">The new <xref:System.Index?displayProperty=nameWithType> type can be used for indexing.</span></span> <span data-ttu-id="51e40-375">Można utworzyć jedną z nich na podstawie `int` liczby od początku lub z `^` operatorem prefiksu (C#), który jest liczony od końca:</span><span class="sxs-lookup"><span data-stu-id="51e40-375">You can create one from an `int` that counts from the beginning, or with a prefix `^` operator (C#) that counts from the end:</span></span>

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

<span data-ttu-id="51e40-376">Istnieje również <xref:System.Range?displayProperty=nameWithType> Typ, który składa się z dwóch `Index` wartości, jeden dla początku i jeden dla końca, i może być zapisany przy użyciu `x..y` wyrażenia zakresu (C#).</span><span class="sxs-lookup"><span data-stu-id="51e40-376">There's also the <xref:System.Range?displayProperty=nameWithType> type, which consists of two `Index` values, one for the start and one for the end, and can be written with a `x..y` range expression (C#).</span></span> <span data-ttu-id="51e40-377">Następnie można indeksować za pomocą `Range` , co spowoduje utworzenie wycinka:</span><span class="sxs-lookup"><span data-stu-id="51e40-377">You can then index with a `Range`, which produces a slice:</span></span>

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

<span data-ttu-id="51e40-378">Aby uzyskać więcej informacji, zobacz [Samouczek dotyczący zakresów i indeksów](../../csharp/tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="51e40-378">For more information, see the [ranges and indices tutorial](../../csharp/tutorials/ranges-indexes.md).</span></span>

### <a name="async-streams"></a><span data-ttu-id="51e40-379">Strumienie asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="51e40-379">Async streams</span></span>

<span data-ttu-id="51e40-380"><xref:System.Collections.Generic.IAsyncEnumerable%601>Typ jest nową wersją asynchroniczną programu <xref:System.Collections.Generic.IEnumerable%601> .</span><span class="sxs-lookup"><span data-stu-id="51e40-380">The <xref:System.Collections.Generic.IAsyncEnumerable%601> type is a new asynchronous version of <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="51e40-381">Język pozwala na korzystanie `await foreach` z `IAsyncEnumerable<T>` ich elementów i używanie ich do `yield return` tworzenia elementów.</span><span class="sxs-lookup"><span data-stu-id="51e40-381">The language lets you `await foreach` over `IAsyncEnumerable<T>` to consume their elements, and use `yield return` to them to produce elements.</span></span>

<span data-ttu-id="51e40-382">Poniższy przykład ilustruje produkcję i zużycie strumieni asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="51e40-382">The following example demonstrates both production and consumption of async streams.</span></span> <span data-ttu-id="51e40-383">`foreach`Instrukcja jest asynchroniczna i sama używa `yield return` do tworzenia strumienia asynchronicznego dla obiektów wywołujących.</span><span class="sxs-lookup"><span data-stu-id="51e40-383">The `foreach` statement is async and itself uses `yield return` to produce an async stream for callers.</span></span> <span data-ttu-id="51e40-384">Ten wzorzec (using `yield return` ) jest zalecanym modelem do tworzenia strumieni asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="51e40-384">This pattern (using `yield return`) is the recommended model for producing async streams.</span></span>

```csharp
async IAsyncEnumerable<int> GetBigResultsAsync()
{
    await foreach (var result in GetResultsAsync())
    {
        if (result > 20) yield return result;
    }
}
```

<span data-ttu-id="51e40-385">Oprócz możliwości można `await foreach` także tworzyć Iteratory asynchroniczne, na przykład iterator, który zwraca, `IAsyncEnumerable/IAsyncEnumerator` że można zarówno `await` , jak i `yield` w.</span><span class="sxs-lookup"><span data-stu-id="51e40-385">In addition to being able to `await foreach`, you can also create async iterators, for example, an iterator that returns an `IAsyncEnumerable/IAsyncEnumerator` that you can both `await` and `yield` in.</span></span> <span data-ttu-id="51e40-386">W przypadku obiektów, które muszą zostać usunięte, można użyć `IAsyncDisposable` różnych typów BCL, takich jak `Stream` i `Timer` .</span><span class="sxs-lookup"><span data-stu-id="51e40-386">For objects that need to be disposed, you can use `IAsyncDisposable`, which various BCL types implement, such as `Stream` and `Timer`.</span></span>

<span data-ttu-id="51e40-387">Aby uzyskać więcej informacji, zobacz [Samouczek dotyczący strumieni asynchronicznych](../../csharp/tutorials/generate-consume-asynchronous-stream.md).</span><span class="sxs-lookup"><span data-stu-id="51e40-387">For more information, see the [async streams tutorial](../../csharp/tutorials/generate-consume-asynchronous-stream.md).</span></span>

### <a name="ieee-floating-point"></a><span data-ttu-id="51e40-388">Liczba zmiennoprzecinkowa IEEE</span><span class="sxs-lookup"><span data-stu-id="51e40-388">IEEE Floating-point</span></span>

<span data-ttu-id="51e40-389">Interfejsy API zmiennoprzecinkowe są aktualizowane w celu zapewnienia zgodności z [poprawką IEEE 754-2008](https://en.wikipedia.org/wiki/IEEE_754-2008_revision).</span><span class="sxs-lookup"><span data-stu-id="51e40-389">Floating point APIs are being updated to comply with [IEEE 754-2008 revision](https://en.wikipedia.org/wiki/IEEE_754-2008_revision).</span></span> <span data-ttu-id="51e40-390">Celem tych zmian jest uwidocznienie wszystkich **wymaganych** operacji i upewnienie się, że są one zgodne z specyfikacją IEEE. Aby uzyskać więcej informacji na temat ulepszeń zmiennoprzecinkowych, zobacz [udoskonalenia analizy i formatowania zmiennoprzecinkowe w wpisie na blogu programu .NET Core 3,0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) .</span><span class="sxs-lookup"><span data-stu-id="51e40-390">The goal of these changes is to expose all **required** operations and ensure that they're behaviorally compliant with the IEEE spec. For more information about floating-point improvements, see the [Floating-Point Parsing and Formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog post.</span></span>

<span data-ttu-id="51e40-391">Poprawki dotyczące analizowania i formatowania obejmują:</span><span class="sxs-lookup"><span data-stu-id="51e40-391">Parsing and formatting fixes include:</span></span>

- <span data-ttu-id="51e40-392">Poprawnie Analizuj i Zaokrąglij dane wejściowe o dowolnej długości.</span><span class="sxs-lookup"><span data-stu-id="51e40-392">Correctly parse and round inputs of any length.</span></span>
- <span data-ttu-id="51e40-393">Prawidłowo Przeanalizuj i sformatuj ujemną wartość zero.</span><span class="sxs-lookup"><span data-stu-id="51e40-393">Correctly parse and format negative zero.</span></span>
- <span data-ttu-id="51e40-394">Poprawne analizowanie `Infinity` i `NaN` wykonywanie kontroli bez uwzględniania wielkości liter i Zezwalanie na opcjonalne poprzednie, `+` Jeśli ma to zastosowanie.</span><span class="sxs-lookup"><span data-stu-id="51e40-394">Correctly parse `Infinity` and `NaN` by doing a case-insensitive check and allowing an optional preceding `+` where applicable.</span></span>

<span data-ttu-id="51e40-395">Nowe <xref:System.Math?displayProperty=nameWithType> interfejsy API obejmują:</span><span class="sxs-lookup"><span data-stu-id="51e40-395">New <xref:System.Math?displayProperty=nameWithType> APIs include:</span></span>

- <span data-ttu-id="51e40-396"><xref:System.Math.BitIncrement(System.Double)>lub<xref:System.Math.BitDecrement(System.Double)></span><span class="sxs-lookup"><span data-stu-id="51e40-396"><xref:System.Math.BitIncrement(System.Double)> and <xref:System.Math.BitDecrement(System.Double)></span></span>\
<span data-ttu-id="51e40-397">Odnosi się do `nextUp` `nextDown` operacji i IEEE.</span><span class="sxs-lookup"><span data-stu-id="51e40-397">Corresponds to the `nextUp` and `nextDown` IEEE operations.</span></span> <span data-ttu-id="51e40-398">Zwracają one najmniejszą liczbę zmiennoprzecinkową, która porównuje większe lub mniejsze niż dane wejściowe (odpowiednio).</span><span class="sxs-lookup"><span data-stu-id="51e40-398">They return the smallest floating-point number that compares greater or lesser than the input (respectively).</span></span> <span data-ttu-id="51e40-399">Na przykład `Math.BitIncrement(0.0)` zwrócimy `double.Epsilon` .</span><span class="sxs-lookup"><span data-stu-id="51e40-399">For example, `Math.BitIncrement(0.0)` would return `double.Epsilon`.</span></span>

- <span data-ttu-id="51e40-400"><xref:System.Math.MaxMagnitude(System.Double,System.Double)>lub<xref:System.Math.MinMagnitude(System.Double,System.Double)></span><span class="sxs-lookup"><span data-stu-id="51e40-400"><xref:System.Math.MaxMagnitude(System.Double,System.Double)> and <xref:System.Math.MinMagnitude(System.Double,System.Double)></span></span>\
<span data-ttu-id="51e40-401">Odnosi się do `maxNumMag` `minNumMag` operacji i IEEE, zwracają wartość, która jest większa lub mniejsza o wielkości dwóch danych wejściowych (odpowiednio).</span><span class="sxs-lookup"><span data-stu-id="51e40-401">Corresponds to the `maxNumMag` and `minNumMag` IEEE operations, they return the value that is greater or lesser in magnitude of the two inputs (respectively).</span></span> <span data-ttu-id="51e40-402">Na przykład `Math.MaxMagnitude(2.0, -3.0)` zwrócimy `-3.0` .</span><span class="sxs-lookup"><span data-stu-id="51e40-402">For example, `Math.MaxMagnitude(2.0, -3.0)` would return `-3.0`.</span></span>

- <xref:System.Math.ILogB(System.Double)>\
<span data-ttu-id="51e40-403">Odnosi się do `logB` operacji IEEE, która zwraca wartość całkowitą, zwraca integralny dziennik Base-2 parametru wejściowego.</span><span class="sxs-lookup"><span data-stu-id="51e40-403">Corresponds to the `logB` IEEE operation that returns an integral value, it returns the integral base-2 log of the input parameter.</span></span> <span data-ttu-id="51e40-404">Ta metoda jest efektywnie taka sama jak `floor(log2(x))` , ale została wykonana z minimalnym błędem zaokrąglania.</span><span class="sxs-lookup"><span data-stu-id="51e40-404">This method is effectively the same as `floor(log2(x))`, but done with minimal rounding error.</span></span>

- <xref:System.Math.ScaleB(System.Double,System.Int32)>\
<span data-ttu-id="51e40-405">Odnosi się do `scaleB` operacji IEEE, która przyjmuje wartość całkowitą, która zwraca efektywność `x * pow(2, n)` , ale jest wykonywana z minimalnym błędem zaokrąglania.</span><span class="sxs-lookup"><span data-stu-id="51e40-405">Corresponds to the `scaleB` IEEE operation that takes an integral value, it returns effectively `x * pow(2, n)`, but is done with minimal rounding error.</span></span>

- <xref:System.Math.Log2(System.Double)>\
<span data-ttu-id="51e40-406">Odpowiada `log2` operacji IEEE, Zwraca logarytm o podstawie 2.</span><span class="sxs-lookup"><span data-stu-id="51e40-406">Corresponds to the `log2` IEEE operation, it returns the base-2 logarithm.</span></span> <span data-ttu-id="51e40-407">Minimalizuje błąd zaokrąglania.</span><span class="sxs-lookup"><span data-stu-id="51e40-407">It minimizes rounding error.</span></span>

- <xref:System.Math.FusedMultiplyAdd(System.Double,System.Double,System.Double)>\
<span data-ttu-id="51e40-408">Odnosi się do `fma` operacji IEEE, dlatego wykonuje odrzucane mnożenie dodawania.</span><span class="sxs-lookup"><span data-stu-id="51e40-408">Corresponds to the `fma` IEEE operation, it performs a fused multiply add.</span></span> <span data-ttu-id="51e40-409">Oznacza to, że jest to `(x * y) + z` jedna operacja, a tym samym Minimalizacja błędu zaokrąglania.</span><span class="sxs-lookup"><span data-stu-id="51e40-409">That is, it does `(x * y) + z` as a single operation, thereby minimizing the rounding error.</span></span> <span data-ttu-id="51e40-410">Przykładem jest `FusedMultiplyAdd(1e308, 2.0, -1e308)` , która zwraca `1e308` .</span><span class="sxs-lookup"><span data-stu-id="51e40-410">An example is `FusedMultiplyAdd(1e308, 2.0, -1e308)`, which returns `1e308`.</span></span> <span data-ttu-id="51e40-411">Regularne `(1e308 * 2.0) - 1e308` zwroty `double.PositiveInfinity` .</span><span class="sxs-lookup"><span data-stu-id="51e40-411">The regular `(1e308 * 2.0) - 1e308` returns `double.PositiveInfinity`.</span></span>

- <xref:System.Math.CopySign(System.Double,System.Double)>\
<span data-ttu-id="51e40-412">Odpowiada `copySign` operacji IEEE, zwraca wartość `x` , ale ze znakiem `y` .</span><span class="sxs-lookup"><span data-stu-id="51e40-412">Corresponds to the `copySign` IEEE operation, it returns the value of `x`, but with the sign of `y`.</span></span>

### <a name="net-platform-dependent-intrinsics"></a><span data-ttu-id="51e40-413">Elementy wewnętrzne zależne od platformy .NET</span><span class="sxs-lookup"><span data-stu-id="51e40-413">.NET Platform-Dependent Intrinsics</span></span>

<span data-ttu-id="51e40-414">Dodano interfejsy API, które umożliwiają dostęp do pewnych instrukcji procesora CPU zorientowanych na wydajność, takich jak **SIMD** lub **bitowe zestawy instrukcji manipulowania** .</span><span class="sxs-lookup"><span data-stu-id="51e40-414">APIs have been added that allow access to certain perf-oriented CPU instructions, such as the **SIMD** or **Bit Manipulation instruction** sets.</span></span> <span data-ttu-id="51e40-415">Te instrukcje mogą pomóc w osiągnięciu znaczących ulepszeń wydajności w niektórych scenariuszach, takich jak wydajne przetwarzanie danych.</span><span class="sxs-lookup"><span data-stu-id="51e40-415">These instructions can help achieve significant performance improvements in certain scenarios, such as processing data efficiently in parallel.</span></span>

<span data-ttu-id="51e40-416">W odpowiednich przypadkach biblioteki .NET zaczęły korzystać z tych instrukcji w celu zwiększenia wydajności.</span><span class="sxs-lookup"><span data-stu-id="51e40-416">Where appropriate, the .NET libraries have begun using these instructions to improve performance.</span></span>

<span data-ttu-id="51e40-417">Aby uzyskać więcej informacji, zobacz elementy [wewnętrzne zależne od platformy .NET](https://github.com/dotnet/designs/blob/master/accepted/2018/platform-intrinsics.md).</span><span class="sxs-lookup"><span data-stu-id="51e40-417">For more information, see [.NET Platform-Dependent Intrinsics](https://github.com/dotnet/designs/blob/master/accepted/2018/platform-intrinsics.md).</span></span>

### <a name="improved-net-core-version-apis"></a><span data-ttu-id="51e40-418">Ulepszone interfejsy API wersji platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="51e40-418">Improved .NET Core Version APIs</span></span>

<span data-ttu-id="51e40-419">Począwszy od platformy .NET Core 3,0, interfejsy API wersji dostarczone z platformą .NET Core teraz zwracają oczekiwane informacje.</span><span class="sxs-lookup"><span data-stu-id="51e40-419">Starting with .NET Core 3.0, the version APIs provided with .NET Core now return the information you expect.</span></span> <span data-ttu-id="51e40-420">Przykład:</span><span class="sxs-lookup"><span data-stu-id="51e40-420">For example:</span></span>

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
> <span data-ttu-id="51e40-421">Istotna zmiana.</span><span class="sxs-lookup"><span data-stu-id="51e40-421">Breaking change.</span></span> <span data-ttu-id="51e40-422">Jest to technicznie istotna zmiana, ponieważ schemat przechowywania wersji został zmieniony.</span><span class="sxs-lookup"><span data-stu-id="51e40-422">This is technically a breaking change because the versioning scheme has changed.</span></span>

### <a name="fast-built-in-json-support"></a><span data-ttu-id="51e40-423">Szybka Wbudowana obsługa JSON</span><span class="sxs-lookup"><span data-stu-id="51e40-423">Fast built-in JSON support</span></span>

<span data-ttu-id="51e40-424">Użytkownicy platformy .NET w dużym stopniu opierają się na [Newtonsoft. JSON](https://www.newtonsoft.com/json) i innych popularnych bibliotekach JSON, które nadal są dobrym wybórem.</span><span class="sxs-lookup"><span data-stu-id="51e40-424">.NET users have largely relied on [Newtonsoft.Json](https://www.newtonsoft.com/json) and other popular JSON libraries, which continue to be good choices.</span></span> <span data-ttu-id="51e40-425">`Newtonsoft.Json`używa ciągów .NET jako podstawowego elementu DataType, który jest UTF-16 pod okapem.</span><span class="sxs-lookup"><span data-stu-id="51e40-425">`Newtonsoft.Json` uses .NET strings as its base datatype, which is UTF-16 under the hood.</span></span>

<span data-ttu-id="51e40-426">Nowa Wbudowana obsługa JSON to wysoka wydajność, niska alokacja i współpracuje z tekstem JSON zakodowanym w formacie UTF-8.</span><span class="sxs-lookup"><span data-stu-id="51e40-426">The new built-in JSON support is high-performance, low allocation, and works with UTF-8 encoded JSON text.</span></span> <span data-ttu-id="51e40-427">Aby uzyskać więcej informacji na temat <xref:System.Text.Json> przestrzeni nazw i typów, zobacz następujące artykuły:</span><span class="sxs-lookup"><span data-stu-id="51e40-427">For more information about the <xref:System.Text.Json> namespace and types, see the following articles:</span></span>

* [<span data-ttu-id="51e40-428">Serializacja kodu JSON w programie .NET — Omówienie</span><span class="sxs-lookup"><span data-stu-id="51e40-428">JSON serialization in .NET - overview</span></span>](../../standard/serialization/system-text-json-overview.md)
* <span data-ttu-id="51e40-429">[Jak serializować i deserializować kod JSON w programie .NET](../../standard/serialization/system-text-json-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="51e40-429">[How to serialize and deserialize JSON in .NET](../../standard/serialization/system-text-json-how-to.md).</span></span>
* [<span data-ttu-id="51e40-430">Jak przeprowadzić migrację z Newtonsoft. JSON do System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="51e40-430">How to migrate from Newtonsoft.Json to System.Text.Json</span></span>](../../standard/serialization/system-text-json-migrate-from-newtonsoft-how-to.md)

### <a name="http2-support"></a><span data-ttu-id="51e40-431">Obsługa protokołu HTTP/2</span><span class="sxs-lookup"><span data-stu-id="51e40-431">HTTP/2 support</span></span>

<span data-ttu-id="51e40-432"><xref:System.Net.Http.HttpClient?displayProperty=nameWithType>Typ obsługuje protokół HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="51e40-432">The <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> type supports the HTTP/2 protocol.</span></span> <span data-ttu-id="51e40-433">Jeśli protokół HTTP/2 jest włączony, wersja protokołu HTTP jest negocjowana za pośrednictwem protokołu TLS/CLIENTHELLO ALPN, a protokół HTTP/2 jest używany, jeśli serwer zdecyduje się go użyć.</span><span class="sxs-lookup"><span data-stu-id="51e40-433">If HTTP/2 is enabled, the HTTP protocol version is negotiated via TLS/ALPN, and HTTP/2 is used if the server elects to use it.</span></span>

<span data-ttu-id="51e40-434">Domyślnym protokołem jest protokół HTTP/1.1, ale protokół HTTP/2 można włączyć na dwa różne sposoby.</span><span class="sxs-lookup"><span data-stu-id="51e40-434">The default protocol remains HTTP/1.1, but HTTP/2 can be enabled in two different ways.</span></span> <span data-ttu-id="51e40-435">Najpierw można ustawić komunikat żądania HTTP na potrzeby używania protokołu HTTP/2:</span><span class="sxs-lookup"><span data-stu-id="51e40-435">First, you can set the HTTP request message to use HTTP/2:</span></span>

[!code-csharp[Http2Request](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Request)]

<span data-ttu-id="51e40-436">Po drugie, można <xref:System.Net.Http.HttpClient> Domyślnie zmienić użycie protokołu HTTP/2:</span><span class="sxs-lookup"><span data-stu-id="51e40-436">Second, you can change <xref:System.Net.Http.HttpClient> to use HTTP/2 by default:</span></span>

[!code-csharp[Http2Client](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Client)]

<span data-ttu-id="51e40-437">W wielu przypadkach podczas tworzenia aplikacji chcesz użyć nieszyfrowanego połączenia.</span><span class="sxs-lookup"><span data-stu-id="51e40-437">Many times when you're developing an application, you want to use an unencrypted connection.</span></span> <span data-ttu-id="51e40-438">Jeśli wiesz, że docelowy punkt końcowy będzie używać protokołu HTTP/2, możesz włączyć nieszyfrowane połączenia dla protokołu HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="51e40-438">If you know the target endpoint will be using HTTP/2, you can turn on unencrypted connections for HTTP/2.</span></span> <span data-ttu-id="51e40-439">Można ją włączyć przez ustawienie `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT` zmiennej środowiskowej na `1` lub przez włączenie jej w kontekście aplikacji:</span><span class="sxs-lookup"><span data-stu-id="51e40-439">You can turn it on by setting the `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT` environment variable to `1` or by enabling it in the app context:</span></span>

[!code-csharp[Http2Context](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#AppContext)]

## <a name="next-steps"></a><span data-ttu-id="51e40-440">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="51e40-440">Next steps</span></span>

- [<span data-ttu-id="51e40-441">Zapoznaj się z istotnymi zmianami między programem .NET Core 2,2 i 3,0.</span><span class="sxs-lookup"><span data-stu-id="51e40-441">Review the breaking changes between .NET Core 2.2 and 3.0.</span></span>](../compatibility/2.2-3.0.md)
- [<span data-ttu-id="51e40-442">Zapoznaj się z istotnymi zmianami w programie .NET Core 3,0 dla aplikacji Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="51e40-442">Review the breaking changes in .NET Core 3.0 for Windows Forms apps.</span></span>](../compatibility/winforms.md#net-core-30)

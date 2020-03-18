---
title: Co nowego w programie .NET Core 3.0
description: Dowiedz się więcej o nowych funkcjach, które można znaleźć w .NET Core 3.0.
dev_langs:
- csharp
author: thraka
ms.author: adegeo
ms.date: 01/27/2020
ms.openlocfilehash: 6e85c2c3e796ae59a13f944bd4913e4b7316c56a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79398812"
---
# <a name="whats-new-in-net-core-30"></a><span data-ttu-id="851eb-103">Co nowego w programie .NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="851eb-103">What's new in .NET Core 3.0</span></span>

<span data-ttu-id="851eb-104">W tym artykule opisano nowości w .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="851eb-104">This article describes what is new in .NET Core 3.0.</span></span> <span data-ttu-id="851eb-105">Jednym z największych ulepszeń jest obsługa aplikacji klasycznych systemu Windows (tylko windows).</span><span class="sxs-lookup"><span data-stu-id="851eb-105">One of the biggest enhancements is support for Windows desktop applications (Windows only).</span></span> <span data-ttu-id="851eb-106">Korzystając ze składnika SDK .NET Core 3.0 Z systemem Windows Desktop, można przenieść aplikacje Windows Forms i Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="851eb-106">By using the .NET Core 3.0 SDK component Windows Desktop, you can port your Windows Forms and Windows Presentation Foundation (WPF) applications.</span></span> <span data-ttu-id="851eb-107">Aby było jasne, składnik Pulpit systemu Windows jest obsługiwany i uwzględniany tylko w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="851eb-107">To be clear, the Windows Desktop component is only supported and included on Windows.</span></span> <span data-ttu-id="851eb-108">Aby uzyskać więcej informacji, zobacz sekcję [pulpitu systemu Windows](#windows-desktop) w dalszej części tego artykułu.</span><span class="sxs-lookup"><span data-stu-id="851eb-108">For more information, see the [Windows desktop](#windows-desktop) section later in this article.</span></span>

<span data-ttu-id="851eb-109">.NET Core 3.0 dodaje obsługę języka C# 8.0.</span><span class="sxs-lookup"><span data-stu-id="851eb-109">.NET Core 3.0 adds support for C# 8.0.</span></span> <span data-ttu-id="851eb-110">Zdecydowanie zaleca się używanie programu [Visual Studio 2019 w wersji 16.3](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) lub nowszej, [programu Visual Studio dla komputerów Mac 8.3](/visualstudio/mac/install-preview) lub nowszych lub [kodu programu Visual Studio](https://code.visualstudio.com/) z najnowszym **rozszerzeniem języka C#.**</span><span class="sxs-lookup"><span data-stu-id="851eb-110">It's highly recommended that you use [Visual Studio 2019 version 16.3](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or newer, [Visual Studio for Mac 8.3](/visualstudio/mac/install-preview) or newer, or [Visual Studio Code](https://code.visualstudio.com/) with the latest **C# extension**.</span></span>

<span data-ttu-id="851eb-111">[Pobierz i zacznij korzystać z .NET Core 3.0](https://aka.ms/netcore3download) już teraz w systemie Windows, macOS lub Linux.</span><span class="sxs-lookup"><span data-stu-id="851eb-111">[Download and get started with .NET Core 3.0](https://aka.ms/netcore3download) right now on Windows, macOS, or Linux.</span></span>

<span data-ttu-id="851eb-112">Aby uzyskać więcej informacji na temat wydania, zobacz [anons .NET Core 3.0](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0/).</span><span class="sxs-lookup"><span data-stu-id="851eb-112">For more information about the release, see the [.NET Core 3.0 announcement](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-0/).</span></span>

<span data-ttu-id="851eb-113">.NET Core RC1 został uznany przez firmę Microsoft za gotowy do produkcji i był w pełni obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="851eb-113">.NET Core RC1 was considered production ready by Microsoft and was fully supported.</span></span> <span data-ttu-id="851eb-114">Jeśli używasz wersji zapoznawczej, musisz przejść do wersji RTM, aby kontynuować obsługę.</span><span class="sxs-lookup"><span data-stu-id="851eb-114">If you're using a preview release, you must move to the RTM version for continued support.</span></span>

## <a name="language-improvements-c-80"></a><span data-ttu-id="851eb-115">Ulepszenia języka C# 8.0</span><span class="sxs-lookup"><span data-stu-id="851eb-115">Language improvements C# 8.0</span></span>

<span data-ttu-id="851eb-116">C# 8.0 jest również częścią tej wersji, która zawiera funkcję [typów odwołań z możliwością null,](../../csharp/tutorials/nullable-reference-types.md) [strumienia asynchronicznego](../../csharp/tutorials/generate-consume-asynchronous-stream.md)i [więcej wzorców](../../csharp/tutorials/pattern-matching.md).</span><span class="sxs-lookup"><span data-stu-id="851eb-116">C# 8.0 is also part of this release, which includes the [nullable reference types](../../csharp/tutorials/nullable-reference-types.md) feature, [async streams](../../csharp/tutorials/generate-consume-asynchronous-stream.md), and [more patterns](../../csharp/tutorials/pattern-matching.md).</span></span> <span data-ttu-id="851eb-117">Aby uzyskać więcej informacji na temat funkcji języka C# 8.0, zobacz [Co nowego w języku C# 8.0](../../csharp/whats-new/csharp-8.md).</span><span class="sxs-lookup"><span data-stu-id="851eb-117">For more information about C# 8.0 features, see [What's new in C# 8.0](../../csharp/whats-new/csharp-8.md).</span></span>

<span data-ttu-id="851eb-118">Dodano ulepszenia języka do obsługi następujących funkcji interfejsu API wyszczególnionych poniżej:</span><span class="sxs-lookup"><span data-stu-id="851eb-118">Language enhancements were added to support the following API features detailed below:</span></span>

- [<span data-ttu-id="851eb-119">Zakresy i indeksy</span><span class="sxs-lookup"><span data-stu-id="851eb-119">Ranges and indices</span></span>](#ranges-and-indices)
- [<span data-ttu-id="851eb-120">Strumienie asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="851eb-120">Async streams</span></span>](#async-streams)

## <a name="net-standard-21"></a><span data-ttu-id="851eb-121">Standard .NET 2.1</span><span class="sxs-lookup"><span data-stu-id="851eb-121">.NET Standard 2.1</span></span>

<span data-ttu-id="851eb-122">.NET Core 3.0 implementuje **.NET Standard 2.1**.</span><span class="sxs-lookup"><span data-stu-id="851eb-122">.NET Core 3.0 implements **.NET Standard 2.1**.</span></span> <span data-ttu-id="851eb-123">Jednak domyślny `dotnet new classlib` szablon generuje projekt, który nadal jest przeznaczony dla **.NET Standard 2.0**.</span><span class="sxs-lookup"><span data-stu-id="851eb-123">However, the default `dotnet new classlib` template generates a project that still targets **.NET Standard 2.0**.</span></span> <span data-ttu-id="851eb-124">Aby kierować program **.NET Standard 2.1,** należy `TargetFramework` edytować plik projektu i zmienić właściwość `netstandard2.1`na:</span><span class="sxs-lookup"><span data-stu-id="851eb-124">To target **.NET Standard 2.1**, edit your project file and change the `TargetFramework` property to `netstandard2.1`:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">

  <PropertyGroup>
    <TargetFramework>netstandard2.1</TargetFramework>
  </PropertyGroup>

</Project>
```

<span data-ttu-id="851eb-125">Jeśli używasz programu Visual Studio, potrzebujesz [programu Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), ponieważ program Visual Studio 2017 nie obsługuje **programu .NET Standard 2.1** lub **.NET Core 3.0**.</span><span class="sxs-lookup"><span data-stu-id="851eb-125">If you're using Visual Studio, you need [Visual Studio 2019](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019), as Visual Studio 2017 doesn't support **.NET Standard 2.1** or **.NET Core 3.0**.</span></span>

## <a name="compiledeploy"></a><span data-ttu-id="851eb-126">Kompilowanie/wdrażanie</span><span class="sxs-lookup"><span data-stu-id="851eb-126">Compile/Deploy</span></span>

### <a name="default-executables"></a><span data-ttu-id="851eb-127">Domyślne pliki wykonywalne</span><span class="sxs-lookup"><span data-stu-id="851eb-127">Default executables</span></span>

<span data-ttu-id="851eb-128">Program .NET Core domyślnie tworzy [pliki wykonywalne zależne od czasu wykonywania.](../deploying/index.md#publish-runtime-dependent)</span><span class="sxs-lookup"><span data-stu-id="851eb-128">.NET Core now builds [runtime-dependent executables](../deploying/index.md#publish-runtime-dependent) by default.</span></span> <span data-ttu-id="851eb-129">To zachowanie jest nowe dla aplikacji, które używają globalnie zainstalowanej wersji programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="851eb-129">This behavior is new for applications that use a globally installed version of .NET Core.</span></span> <span data-ttu-id="851eb-130">Wcześniej tylko [niezależne wdrożenia](../deploying/index.md#publish-self-contained) będą produkować plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="851eb-130">Previously, only [self-contained deployments](../deploying/index.md#publish-self-contained) would produce an executable.</span></span>

<span data-ttu-id="851eb-131">Podczas `dotnet build` `dotnet publish`lub plik wykonywalny (znany jako **appHost**) jest tworzony, który pasuje do środowiska i platformy sdk używasz.</span><span class="sxs-lookup"><span data-stu-id="851eb-131">During `dotnet build` or `dotnet publish`, an executable (known as the **appHost**) is created that matches the environment and platform of the SDK you're using.</span></span> <span data-ttu-id="851eb-132">Można oczekiwać tych samych rzeczy z tych plików wykonywalnych, jak inne natywne pliki wykonywalne, takie jak:</span><span class="sxs-lookup"><span data-stu-id="851eb-132">You can expect the same things with these executables as you would other native executables, such as:</span></span>

- <span data-ttu-id="851eb-133">Możesz kliknąć dwukrotnie plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="851eb-133">You can double-click on the executable.</span></span>
- <span data-ttu-id="851eb-134">Aplikację można uruchomić bezpośrednio z wiersza `myapp.exe` polecenia, na `./myapp` przykład w systemie Windows, a także w systemie Linux i macOS.</span><span class="sxs-lookup"><span data-stu-id="851eb-134">You can launch the application from a command prompt directly, such as `myapp.exe` on Windows, and `./myapp` on Linux and macOS.</span></span>

### <a name="macos-apphost-and-notarization"></a><span data-ttu-id="851eb-135">aplikacja macOSHost i notarialnie</span><span class="sxs-lookup"><span data-stu-id="851eb-135">macOS appHost and notarization</span></span>

<span data-ttu-id="851eb-136">*Tylko system macOS*</span><span class="sxs-lookup"><span data-stu-id="851eb-136">*macOS only*</span></span>

<span data-ttu-id="851eb-137">Począwszy od notarialnie .NET Core SDK 3.0 dla systemu macOS, ustawienie do produkcji domyślnego pliku wykonywalnego (znany jako appHost) jest domyślnie wyłączone.</span><span class="sxs-lookup"><span data-stu-id="851eb-137">Starting with the notarized .NET Core SDK 3.0 for macOS, the setting to produce a default executable (known as the appHost) is disabled by default.</span></span> <span data-ttu-id="851eb-138">Aby uzyskać więcej informacji, zobacz [notarialnie Catalina w systemie macOS oraz wpływ na pobieranie i projekty programu .NET Core](../install/macos-notarization-issues.md).</span><span class="sxs-lookup"><span data-stu-id="851eb-138">For more information, see [macOS Catalina Notarization and the impact on .NET Core downloads and projects](../install/macos-notarization-issues.md).</span></span>

<span data-ttu-id="851eb-139">Gdy ustawienie appHost jest włączone, program .NET Core generuje natywny plik wykonywalny Mach-O podczas tworzenia lub publikowania.</span><span class="sxs-lookup"><span data-stu-id="851eb-139">When the appHost setting is enabled, .NET Core generates a native Mach-O executable when you build or publish.</span></span> <span data-ttu-id="851eb-140">Aplikacja jest uruchamiana w kontekście appHost, gdy jest `dotnet run` uruchamiany z kodu źródłowego za pomocą polecenia lub przez bezpośrednie uruchomienie pliku wykonywalnego Mach-O.</span><span class="sxs-lookup"><span data-stu-id="851eb-140">Your app runs in the context of the appHost when it is run from source code with the `dotnet run` command, or by starting the Mach-O executable directly.</span></span>

<span data-ttu-id="851eb-141">Bez appHost, jedynym sposobem użytkownik może uruchomić aplikację zależną od `dotnet <filename.dll>` środowiska [uruchomieniowego](../deploying/index.md#publish-runtime-dependent) jest z poleceniem.</span><span class="sxs-lookup"><span data-stu-id="851eb-141">Without the appHost, the only way a user can start a [runtime-dependent](../deploying/index.md#publish-runtime-dependent) app is with the `dotnet <filename.dll>` command.</span></span> <span data-ttu-id="851eb-142">AppHost jest zawsze tworzony podczas publikowania aplikacji [niezależne .](../deploying/index.md#publish-self-contained)</span><span class="sxs-lookup"><span data-stu-id="851eb-142">An appHost is always created when you publish your app [self-contained](../deploying/index.md#publish-self-contained).</span></span>

<span data-ttu-id="851eb-143">Możesz skonfigurować appHost na poziomie projektu lub przełączyć appHost dla `dotnet` określonego `-p:UseAppHost` polecenia z parametrem:</span><span class="sxs-lookup"><span data-stu-id="851eb-143">You can either configure the appHost at the project level, or toggle the appHost for a specific `dotnet` command with the `-p:UseAppHost` parameter:</span></span>

- <span data-ttu-id="851eb-144">Plik projektu</span><span class="sxs-lookup"><span data-stu-id="851eb-144">Project file</span></span>

  ```xml
  <PropertyGroup>
    <UseAppHost>true</UseAppHost>
  </PropertyGroup>
  ```

- <span data-ttu-id="851eb-145">Parametr wiersza polecenia</span><span class="sxs-lookup"><span data-stu-id="851eb-145">Command-line parameter</span></span>

  ```dotnetcli
  dotnet run -p:UseAppHost=true
  ```

<span data-ttu-id="851eb-146">Aby uzyskać więcej `UseAppHost` informacji o tym ustawieniu, zobacz [WŁAŚCIWOŚCI MSBuild dla programu Microsoft.NET.Sdk](../project-sdk/msbuild-props.md#useapphost).</span><span class="sxs-lookup"><span data-stu-id="851eb-146">For more information about the `UseAppHost` setting, see [MSBuild properties for Microsoft.NET.Sdk](../project-sdk/msbuild-props.md#useapphost).</span></span>

### <a name="single-file-executables"></a><span data-ttu-id="851eb-147">Pliki wykonywalne dla jednego pliku</span><span class="sxs-lookup"><span data-stu-id="851eb-147">Single-file executables</span></span>

<span data-ttu-id="851eb-148">Polecenie `dotnet publish` obsługuje pakowanie aplikacji do pliku wykonywalnego dla danego pliku specyficznego dla platformy.</span><span class="sxs-lookup"><span data-stu-id="851eb-148">The `dotnet publish` command supports packaging your app into a platform-specific single-file executable.</span></span> <span data-ttu-id="851eb-149">Plik wykonywalny jest samowyodrębnianie i zawiera wszystkie zależności (w tym natywnych), które są wymagane do uruchomienia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="851eb-149">The executable is self-extracting and contains all dependencies (including native) that are required to run your app.</span></span> <span data-ttu-id="851eb-150">Po pierwszym uruchomieniu aplikacji aplikacja jest wyodrębniana do katalogu na podstawie nazwy aplikacji i identyfikatora kompilacji.</span><span class="sxs-lookup"><span data-stu-id="851eb-150">When the app is first run, the application is extracted to a directory based on the app name and build identifier.</span></span> <span data-ttu-id="851eb-151">Uruchamianie jest szybsze, gdy aplikacja jest uruchamiana ponownie.</span><span class="sxs-lookup"><span data-stu-id="851eb-151">Startup is faster when the application is run again.</span></span> <span data-ttu-id="851eb-152">Aplikacja nie musi wyodrębniać się po raz drugi, chyba że nowa wersja została użyta.</span><span class="sxs-lookup"><span data-stu-id="851eb-152">The application doesn't need to extract itself a second time unless a new version was used.</span></span>

<span data-ttu-id="851eb-153">Aby opublikować plik wykonywalny dla pojedynczego pliku, ustaw je `PublishSingleFile` w projekcie lub w wierszu `dotnet publish` polecenia za pomocą polecenia:</span><span class="sxs-lookup"><span data-stu-id="851eb-153">To publish a single-file executable, set the `PublishSingleFile` in your project or on the command line with the `dotnet publish` command:</span></span>

```xml
<PropertyGroup>
  <RuntimeIdentifier>win10-x64</RuntimeIdentifier>
  <PublishSingleFile>true</PublishSingleFile>
</PropertyGroup>
```

<span data-ttu-id="851eb-154">— lub —</span><span class="sxs-lookup"><span data-stu-id="851eb-154">-or-</span></span>

```dotnetcli
dotnet publish -r win10-x64 -p:PublishSingleFile=true
```

<span data-ttu-id="851eb-155">Aby uzyskać więcej informacji na temat publikowania pojedynczych plików, zobacz [dokument projektowy pakietu pojedynczego pliku](https://github.com/dotnet/designs/blob/master/accepted/single-file/design.md).</span><span class="sxs-lookup"><span data-stu-id="851eb-155">For more information about single-file publishing, see the [single-file bundler design document](https://github.com/dotnet/designs/blob/master/accepted/single-file/design.md).</span></span>

### <a name="assembly-linking"></a><span data-ttu-id="851eb-156">Łączenie zestawów</span><span class="sxs-lookup"><span data-stu-id="851eb-156">Assembly linking</span></span>

<span data-ttu-id="851eb-157">Zestaw SDK .NET core 3.0 jest dostarczany z narzędziem, które może zmniejszyć rozmiar aplikacji, analizując il i przycinając nieużywane zestawy.</span><span class="sxs-lookup"><span data-stu-id="851eb-157">The .NET core 3.0 SDK comes with a tool that can reduce the size of apps by analyzing IL and trimming unused assemblies.</span></span>

<span data-ttu-id="851eb-158">Niezależne aplikacje zawierają wszystko, co jest potrzebne do uruchomienia kodu, bez konieczności instalowania .NET na komputerze-hoście.</span><span class="sxs-lookup"><span data-stu-id="851eb-158">Self-contained apps include everything needed to run your code, without requiring .NET to be installed on the host computer.</span></span> <span data-ttu-id="851eb-159">Jednak wiele razy aplikacja wymaga tylko mały podzbiór struktury do działania i inne nieużywane biblioteki mogą zostać usunięte.</span><span class="sxs-lookup"><span data-stu-id="851eb-159">However, many times the app only requires a small subset of the framework to function, and other unused libraries could be removed.</span></span>

<span data-ttu-id="851eb-160">.NET Core zawiera teraz ustawienie, które będzie używać narzędzia [konsolidatora IL](https://github.com/mono/linker) do skanowania il aplikacji.</span><span class="sxs-lookup"><span data-stu-id="851eb-160">.NET Core now includes a setting that will use the [IL linker](https://github.com/mono/linker) tool to scan the IL of your app.</span></span> <span data-ttu-id="851eb-161">To narzędzie wykrywa, jaki kod jest wymagany, a następnie przycina nieużywane biblioteki.</span><span class="sxs-lookup"><span data-stu-id="851eb-161">This tool detects what code is required, and then trims unused libraries.</span></span> <span data-ttu-id="851eb-162">To narzędzie może znacznie zmniejszyć rozmiar wdrożenia niektórych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="851eb-162">This tool can significantly reduce the deployment size of some apps.</span></span>

<span data-ttu-id="851eb-163">Aby włączyć to narzędzie, dodaj `<PublishTrimmed>` ustawienie w projekcie i opublikuj niezależną aplikację:</span><span class="sxs-lookup"><span data-stu-id="851eb-163">To enable this tool, add the `<PublishTrimmed>` setting in your project and publish a self-contained app:</span></span>

```xml
<PropertyGroup>
  <PublishTrimmed>true</PublishTrimmed>
</PropertyGroup>
```

```dotnetcli
dotnet publish -r <rid> -c Release
```

<span data-ttu-id="851eb-164">Na przykład podstawowy "hello world" nowy szablon projektu konsoli, który jest uwzględniony, po opublikowaniu, osiąga około 70 MB w rozmiarze.</span><span class="sxs-lookup"><span data-stu-id="851eb-164">As an example, the basic "hello world" new console project template that is included, when published, hits about 70 MB in size.</span></span> <span data-ttu-id="851eb-165">Za `<PublishTrimmed>`pomocą , ten rozmiar jest zmniejszona do około 30 MB.</span><span class="sxs-lookup"><span data-stu-id="851eb-165">By using `<PublishTrimmed>`, that size is reduced to about 30 MB.</span></span>

<span data-ttu-id="851eb-166">Należy wziąć pod uwagę, że aplikacje lub struktury (w tym ASP.NET Core i WPF), które używają odbicia lub powiązanych funkcji dynamicznych, często zostaną zerwane po przycięciu.</span><span class="sxs-lookup"><span data-stu-id="851eb-166">It's important to consider that applications or frameworks (including ASP.NET Core and WPF) that use reflection or related dynamic features, will often break when trimmed.</span></span> <span data-ttu-id="851eb-167">To pęknięcie występuje, ponieważ konsolidator nie wie o tym zachowanie dynamiczne i nie można określić, które typy struktury są wymagane do odbicia.</span><span class="sxs-lookup"><span data-stu-id="851eb-167">This breakage occurs because the linker doesn't know about this dynamic behavior and can't determine which framework types are required for reflection.</span></span> <span data-ttu-id="851eb-168">Narzędzie IL Linker można skonfigurować tak, aby zdawać sobie sprawę z tego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="851eb-168">The IL Linker tool can be configured to be aware of this scenario.</span></span>

<span data-ttu-id="851eb-169">Przede wszystkim należy przetestować aplikację po przycinaniu.</span><span class="sxs-lookup"><span data-stu-id="851eb-169">Above all else, be sure to test your app after trimming.</span></span>

<span data-ttu-id="851eb-170">Aby uzyskać więcej informacji na temat narzędzia IL Linker, zobacz [dokumentację](https://aka.ms/dotnet-illink) lub odwiedź repówkę [mono/linker.]( https://github.com/mono/linker)</span><span class="sxs-lookup"><span data-stu-id="851eb-170">For more information about the IL Linker tool, see the [documentation](https://aka.ms/dotnet-illink) or visit the [mono/linker]( https://github.com/mono/linker) repo.</span></span>

### <a name="tiered-compilation"></a><span data-ttu-id="851eb-171">Kompilacja warstwowa</span><span class="sxs-lookup"><span data-stu-id="851eb-171">Tiered compilation</span></span>

<span data-ttu-id="851eb-172">[Kompilacja warstwowa](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation-guide.md) (TC) jest domyślnie włączone z .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="851eb-172">[Tiered compilation](https://github.com/dotnet/runtime/blob/master/docs/design/features/tiered-compilation-guide.md) (TC) is on by default with .NET Core 3.0.</span></span> <span data-ttu-id="851eb-173">Ta funkcja umożliwia programowi uruchomieniowemu bardziej adaptacyjne korzystanie z kompilatora just-in-time (JIT), aby osiągnąć lepszą wydajność.</span><span class="sxs-lookup"><span data-stu-id="851eb-173">This feature enables the runtime to more adaptively use the just-in-time (JIT) compiler to achieve better performance.</span></span>

<span data-ttu-id="851eb-174">Główną zaletą kompilacji warstwowej jest zapewnienie dwóch sposobów metody wysięgnika: w niższej jakości, ale szybciej warstwy lub wyższej jakości, ale wolniej warstwy.</span><span class="sxs-lookup"><span data-stu-id="851eb-174">The main benefit of tiered compilation is to provide two ways of jitting methods: in a lower-quality-but-faster tier or a higher-quality-but-slower tier.</span></span> <span data-ttu-id="851eb-175">Jakość odnosi się do tego, jak dobrze metoda jest zoptymalizowana.</span><span class="sxs-lookup"><span data-stu-id="851eb-175">The quality refers to how well the method is optimized.</span></span> <span data-ttu-id="851eb-176">TC pomaga poprawić wydajność aplikacji, ponieważ przechodzi przez różne etapy wykonywania, od uruchamiania przez stan stały.</span><span class="sxs-lookup"><span data-stu-id="851eb-176">TC helps to improve the performance of an application as it goes through various stages of execution, from startup through steady state.</span></span> <span data-ttu-id="851eb-177">Gdy kompilacja warstwowa jest wyłączona, każda metoda jest kompilowana w jeden sposób, który jest stronniczy do wydajności w stanie stacjonarnym nad wydajnością uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="851eb-177">When tiered compilation is disabled, every method is compiled in a single way that's biased to steady-state performance over startup performance.</span></span>

<span data-ttu-id="851eb-178">Po włączeniu tc, następujące zachowanie ma zastosowanie do kompilacji metod podczas uruchamiania aplikacji:</span><span class="sxs-lookup"><span data-stu-id="851eb-178">When TC is enabled, the following behavior applies for method compilation when an app starts up:</span></span>

- <span data-ttu-id="851eb-179">Jeśli metoda ma kod skompilowany z wyprzedzeniem lub [ReadyToRun](#readytorun-images), pregenerowany kod jest używany.</span><span class="sxs-lookup"><span data-stu-id="851eb-179">If the method has ahead-of-time-compiled code, or [ReadyToRun](#readytorun-images), the pregenerated code is used.</span></span>
- <span data-ttu-id="851eb-180">W przeciwnym razie metoda jest wyjmowany.</span><span class="sxs-lookup"><span data-stu-id="851eb-180">Otherwise, the method is jitted.</span></span> <span data-ttu-id="851eb-181">Zazwyczaj te metody są ogólne typy wartości.</span><span class="sxs-lookup"><span data-stu-id="851eb-181">Typically, these methods are generics over value types.</span></span>
  - <span data-ttu-id="851eb-182">*Szybki JIT* szybciej wytwarza kod niższej jakości (lub mniej zoptymalizowany).</span><span class="sxs-lookup"><span data-stu-id="851eb-182">*Quick JIT* produces lower-quality (or less optimized) code more quickly.</span></span> <span data-ttu-id="851eb-183">W .NET Core 3.0 Szybkie JIT jest domyślnie włączona dla metod, które nie zawierają pętli i jest preferowana podczas uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="851eb-183">In .NET Core 3.0, Quick JIT is enabled by default for methods that don't contain loops and is preferred during startup.</span></span>
  - <span data-ttu-id="851eb-184">W pełni optymalizujący kod JIT wytwarza kod wyższej jakości (lub bardziej zoptymalizowany) wolniej.</span><span class="sxs-lookup"><span data-stu-id="851eb-184">The fully optimizing JIT produces higher-quality (or more optimized) code more slowly.</span></span> <span data-ttu-id="851eb-185">W przypadku metod, w których szybki jit nie będzie używany <xref:System.Runtime.CompilerServices.MethodImplOptions.AggressiveOptimization?displayProperty=nameWithType>(na przykład, jeśli metoda jest przypisana za pomocą), w pełni optymalizujący JIT jest używany.</span><span class="sxs-lookup"><span data-stu-id="851eb-185">For methods where Quick JIT would not be used (for example, if the method is attributed with <xref:System.Runtime.CompilerServices.MethodImplOptions.AggressiveOptimization?displayProperty=nameWithType>), the fully optimizing JIT is used.</span></span>

<span data-ttu-id="851eb-186">W przypadku często nazywanych metod kompilator just-in-time ostatecznie tworzy w pełni zoptymalizowany kod w tle.</span><span class="sxs-lookup"><span data-stu-id="851eb-186">For frequently called methods, the just-in-time compiler eventually creates fully optimized code in the background.</span></span> <span data-ttu-id="851eb-187">Zoptymalizowany kod zastępuje następnie wstępnie skompilowany kod dla tej metody.</span><span class="sxs-lookup"><span data-stu-id="851eb-187">The optimized code then replaces the pre-compiled code for that method.</span></span>

<span data-ttu-id="851eb-188">Kod generowany przez Szybki JIT może działać wolniej, przydzielać więcej pamięci lub używać więcej miejsca na stosie.</span><span class="sxs-lookup"><span data-stu-id="851eb-188">Code generated by Quick JIT may run slower, allocate more memory, or use more stack space.</span></span> <span data-ttu-id="851eb-189">Jeśli występują problemy, można wyłączyć Szybki JIT przy użyciu tej właściwości MSBuild w pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="851eb-189">If there are issues, you can disabled Quick JIT using this MSBuild property in the project file:</span></span>

```xml
<PropertyGroup>
  <TieredCompilationQuickJit>false</TieredCompilationQuickJit>
</PropertyGroup>
```

<span data-ttu-id="851eb-190">Aby całkowicie wyłączyć tc, użyj tej właściwości MSBuild w pliku projektu:</span><span class="sxs-lookup"><span data-stu-id="851eb-190">To disable TC completely, use this MSBuild property in your project file:</span></span>

```xml
<PropertyGroup>
  <TieredCompilation>false</TieredCompilation>
</PropertyGroup>
```

> [!TIP]
> <span data-ttu-id="851eb-191">Jeśli te ustawienia zostaną zmienić w pliku projektu, może być konieczne wykonanie czystej kompilacji, aby nowe ustawienia zostały odzwierciedlone (usuń `obj` katalogi i `bin` przebuduj).</span><span class="sxs-lookup"><span data-stu-id="851eb-191">If you change these settings in the project file, you may need to perform a clean build for the new settings to be reflected (delete the `obj` and `bin` directories and rebuild).</span></span>

<span data-ttu-id="851eb-192">Aby uzyskać więcej informacji na temat konfigurowania kompilacji w czasie wykonywania, zobacz [Opcje konfiguracji czasu wykonywania kompilacji](../run-time-config/compilation.md).</span><span class="sxs-lookup"><span data-stu-id="851eb-192">For more information about configuring compilation at run time, see [Run-time configuration options for compilation](../run-time-config/compilation.md).</span></span>

### <a name="readytorun-images"></a><span data-ttu-id="851eb-193">Obrazy ReadyToRun</span><span class="sxs-lookup"><span data-stu-id="851eb-193">ReadyToRun images</span></span>

<span data-ttu-id="851eb-194">Czas uruchamiania aplikacji .NET Core można skrócić, kompilując zestawy aplikacji w formacie ReadyToRun (R2R).</span><span class="sxs-lookup"><span data-stu-id="851eb-194">You can improve the startup time of your .NET Core application by compiling your application assemblies as ReadyToRun (R2R) format.</span></span> <span data-ttu-id="851eb-195">R2R jest formą kompilacji z wyprzedzeniem (AOT).</span><span class="sxs-lookup"><span data-stu-id="851eb-195">R2R is a form of ahead-of-time (AOT) compilation.</span></span>

<span data-ttu-id="851eb-196">Pliki binarne R2R zwiększyć wydajność uruchamiania poprzez zmniejszenie ilości pracy kompilator just-in-time (JIT) musi wykonać podczas ładowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="851eb-196">R2R binaries improve startup performance by reducing the amount of work the just-in-time (JIT) compiler needs to do as your application loads.</span></span> <span data-ttu-id="851eb-197">Pliki binarne zawierają podobny kod macierzysty w porównaniu do tego, co jit będzie produkować.</span><span class="sxs-lookup"><span data-stu-id="851eb-197">The binaries contain similar native code compared to what the JIT would produce.</span></span> <span data-ttu-id="851eb-198">Jednak pliki binarne R2R są większe, ponieważ zawierają zarówno kod języka pośredniego (IL), który jest nadal potrzebny w niektórych scenariuszach, jak i natywnej wersji tego samego kodu.</span><span class="sxs-lookup"><span data-stu-id="851eb-198">However, R2R binaries are larger because they contain both intermediate language (IL) code, which is still needed for some scenarios, and the native version of the same code.</span></span> <span data-ttu-id="851eb-199">R2R jest dostępna tylko podczas publikowania niezależnej aplikacji, która jest przeznaczona dla określonych środowisk środowiska uruchomieniowego (RID), takich jak Linux x64 lub Windows x64.</span><span class="sxs-lookup"><span data-stu-id="851eb-199">R2R is only available when you publish a self-contained app that targets specific runtime environments (RID) such as Linux x64 or Windows x64.</span></span>

<span data-ttu-id="851eb-200">Aby skompilować projekt jako ReadyToRun, wykonaj następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="851eb-200">To compile your project as ReadyToRun, do the following:</span></span>

01. <span data-ttu-id="851eb-201">Dodaj `<PublishReadyToRun>` to ustawienie do projektu:</span><span class="sxs-lookup"><span data-stu-id="851eb-201">Add the `<PublishReadyToRun>` setting to your project:</span></span>

    ```xml
    <PropertyGroup>
      <PublishReadyToRun>true</PublishReadyToRun>
    </PropertyGroup>
    ```

01. <span data-ttu-id="851eb-202">Publikowanie niezależnej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="851eb-202">Publish a self-contained app.</span></span> <span data-ttu-id="851eb-203">Na przykład to polecenie tworzy niezależną aplikację dla 64-bitowej wersji systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="851eb-203">For example, this command creates a self-contained app for the 64-bit version of Windows:</span></span>

    ```dotnetcli
    dotnet publish -c Release -r win-x64 --self-contained
    ```

#### <a name="cross-platformarchitecture-restrictions"></a><span data-ttu-id="851eb-204">Ograniczenia między platformami/architekturą</span><span class="sxs-lookup"><span data-stu-id="851eb-204">Cross platform/architecture restrictions</span></span>

<span data-ttu-id="851eb-205">Kompilator ReadyToRun nie obsługuje obecnie cross-targeting.</span><span class="sxs-lookup"><span data-stu-id="851eb-205">The ReadyToRun compiler doesn't currently support cross-targeting.</span></span> <span data-ttu-id="851eb-206">Należy skompilować na danym celu.</span><span class="sxs-lookup"><span data-stu-id="851eb-206">You must compile on a given target.</span></span> <span data-ttu-id="851eb-207">Na przykład, jeśli chcesz obrazy R2R dla systemu Windows x64, należy uruchomić polecenie publikowania w tym środowisku.</span><span class="sxs-lookup"><span data-stu-id="851eb-207">For example, if you want R2R images for Windows x64, you need to run the publish command on that environment.</span></span>

<span data-ttu-id="851eb-208">Wyjątki od kierowania krzyżowego:</span><span class="sxs-lookup"><span data-stu-id="851eb-208">Exceptions to cross-targeting:</span></span>

- <span data-ttu-id="851eb-209">System Windows x64 może służyć do kompilowania obrazów z systemami Windows ARM32, ARM64 i x86.</span><span class="sxs-lookup"><span data-stu-id="851eb-209">Windows x64 can be used to compile Windows ARM32, ARM64, and x86 images.</span></span>
- <span data-ttu-id="851eb-210">System Windows x86 może służyć do kompilowania obrazów arm32 systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="851eb-210">Windows x86 can be used to compile Windows ARM32 images.</span></span>
- <span data-ttu-id="851eb-211">Linux x64 może być używany do kompilowania obrazów Linux ARM32 i ARM64.</span><span class="sxs-lookup"><span data-stu-id="851eb-211">Linux x64 can be used to compile Linux ARM32 and ARM64 images.</span></span>

## <a name="runtimesdk"></a><span data-ttu-id="851eb-212">Czas wykonywania/zestaw SDK</span><span class="sxs-lookup"><span data-stu-id="851eb-212">Runtime/SDK</span></span>

### <a name="major-version-runtime-roll-forward"></a><span data-ttu-id="851eb-213">Sposób wykonywania wersji głównej do przodu</span><span class="sxs-lookup"><span data-stu-id="851eb-213">Major-version runtime roll forward</span></span>

<span data-ttu-id="851eb-214">.NET Core 3.0 wprowadza funkcję opt-in, która umożliwia aplikacji przewijanie do najnowszej wersji głównej programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="851eb-214">.NET Core 3.0 introduces an opt-in feature that allows your app to roll forward to the latest major version of .NET Core.</span></span> <span data-ttu-id="851eb-215">Ponadto dodano nowe ustawienie, aby kontrolować sposób stosowania rolowania do przodu w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="851eb-215">Additionally, a new setting has been added to control how roll forward is applied to your app.</span></span> <span data-ttu-id="851eb-216">Można to skonfigurować w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="851eb-216">This can be configured in the following ways:</span></span>

- <span data-ttu-id="851eb-217">Właściwość pliku projektu:`RollForward`</span><span class="sxs-lookup"><span data-stu-id="851eb-217">Project file property: `RollForward`</span></span>
- <span data-ttu-id="851eb-218">Właściwość pliku konfiguracyjnego w czasie wykonywania:`rollForward`</span><span class="sxs-lookup"><span data-stu-id="851eb-218">Run-time configuration file property: `rollForward`</span></span>
- <span data-ttu-id="851eb-219">Zmienna środowiskowa:`DOTNET_ROLL_FORWARD`</span><span class="sxs-lookup"><span data-stu-id="851eb-219">Environment variable: `DOTNET_ROLL_FORWARD`</span></span>
- <span data-ttu-id="851eb-220">Argument wiersza polecenia:`--roll-forward`</span><span class="sxs-lookup"><span data-stu-id="851eb-220">Command-line argument: `--roll-forward`</span></span>

<span data-ttu-id="851eb-221">Należy określić jedną z następujących wartości.</span><span class="sxs-lookup"><span data-stu-id="851eb-221">One of the following values must be specified.</span></span> <span data-ttu-id="851eb-222">Jeśli ustawienie zostanie pominięte, domyślnie domyślnym elementem **jest wartość Pomocnica.**</span><span class="sxs-lookup"><span data-stu-id="851eb-222">If the setting is omitted, **Minor** is the default.</span></span>

- <span data-ttu-id="851eb-223">**Najnowsza łata**</span><span class="sxs-lookup"><span data-stu-id="851eb-223">**LatestPatch**</span></span>\
<span data-ttu-id="851eb-224">Przewiń do przodu do najwyższej wersji poprawki.</span><span class="sxs-lookup"><span data-stu-id="851eb-224">Roll forward to the highest patch version.</span></span> <span data-ttu-id="851eb-225">Spowoduje to wyłączenie pomocniczej wersji przewijania do przodu.</span><span class="sxs-lookup"><span data-stu-id="851eb-225">This disables minor version roll forward.</span></span>
- <span data-ttu-id="851eb-226">**Drobne**</span><span class="sxs-lookup"><span data-stu-id="851eb-226">**Minor**</span></span>\
<span data-ttu-id="851eb-227">Przewiń do przodu do najniższej wyższej wersji pomocniczej, jeśli brakuje żądanych wersji pomocniczej.</span><span class="sxs-lookup"><span data-stu-id="851eb-227">Roll forward to the lowest higher minor version, if requested minor version is missing.</span></span> <span data-ttu-id="851eb-228">Jeśli występuje żądana wersja pomocnicza, używana jest zasada **LatestPatch.**</span><span class="sxs-lookup"><span data-stu-id="851eb-228">If the requested minor version is present, then the **LatestPatch** policy is used.</span></span>
- <span data-ttu-id="851eb-229">**Głównych**</span><span class="sxs-lookup"><span data-stu-id="851eb-229">**Major**</span></span>\
<span data-ttu-id="851eb-230">Przewiń do przodu do najniższej wyższej wersji głównej i najniższej wersji pomocniczej, jeśli nie ma żądanej wersji głównej.</span><span class="sxs-lookup"><span data-stu-id="851eb-230">Roll forward to lowest higher major version, and lowest minor version, if requested major version is missing.</span></span> <span data-ttu-id="851eb-231">Jeśli występuje żądana wersja główna, używana jest zasada **pomocnicza.**</span><span class="sxs-lookup"><span data-stu-id="851eb-231">If the requested major version is present, then the **Minor** policy is used.</span></span>
- <span data-ttu-id="851eb-232">**NajnowszaDrobna**</span><span class="sxs-lookup"><span data-stu-id="851eb-232">**LatestMinor**</span></span>\
<span data-ttu-id="851eb-233">Przewiń do przodu do najwyższej wersji pomocniczej, nawet jeśli żądana wersja pomocnicza jest obecna.</span><span class="sxs-lookup"><span data-stu-id="851eb-233">Roll forward to highest minor version, even if requested minor version is present.</span></span> <span data-ttu-id="851eb-234">Przeznaczone dla scenariuszy hostingu składników.</span><span class="sxs-lookup"><span data-stu-id="851eb-234">Intended for component hosting scenarios.</span></span>
- <span data-ttu-id="851eb-235">**NajnowszaMajor**</span><span class="sxs-lookup"><span data-stu-id="851eb-235">**LatestMajor**</span></span>\
<span data-ttu-id="851eb-236">Przewiń do najwyższej wersji głównej i najwyższej wersji pomocniczej, nawet jeśli wymagane jest główne.</span><span class="sxs-lookup"><span data-stu-id="851eb-236">Roll forward to highest major and highest minor version, even if requested major is present.</span></span> <span data-ttu-id="851eb-237">Przeznaczone dla scenariuszy hostingu składników.</span><span class="sxs-lookup"><span data-stu-id="851eb-237">Intended for component hosting scenarios.</span></span>
- <span data-ttu-id="851eb-238">**Wyłączyć**</span><span class="sxs-lookup"><span data-stu-id="851eb-238">**Disable**</span></span>\
<span data-ttu-id="851eb-239">Nie przewiń do przodu.</span><span class="sxs-lookup"><span data-stu-id="851eb-239">Don't roll forward.</span></span> <span data-ttu-id="851eb-240">Powiąż tylko określoną wersję.</span><span class="sxs-lookup"><span data-stu-id="851eb-240">Only bind to specified version.</span></span> <span data-ttu-id="851eb-241">Ta zasada nie jest zalecane do ogólnego użytku, ponieważ wyłącza możliwość przewijania do przodu do najnowszych poprawek.</span><span class="sxs-lookup"><span data-stu-id="851eb-241">This policy isn't recommended for general use because it disables the ability to roll forward to the latest patches.</span></span> <span data-ttu-id="851eb-242">Ta wartość jest zalecana tylko do testowania.</span><span class="sxs-lookup"><span data-stu-id="851eb-242">This value is only recommended for testing.</span></span>

<span data-ttu-id="851eb-243">Oprócz ustawienia **Wyłącz,** wszystkie ustawienia będą korzystać z najwyższej dostępnej wersji poprawki.</span><span class="sxs-lookup"><span data-stu-id="851eb-243">Besides the **Disable** setting, all settings will use the highest available patch version.</span></span>

### <a name="build-copies-dependencies"></a><span data-ttu-id="851eb-244">Tworzenie kopii zależności</span><span class="sxs-lookup"><span data-stu-id="851eb-244">Build copies dependencies</span></span>

<span data-ttu-id="851eb-245">Polecenie `dotnet build` teraz kopiuje zależności NuGet dla aplikacji z pamięci podręcznej NuGet do folderu wyjściowego kompilacji.</span><span class="sxs-lookup"><span data-stu-id="851eb-245">The `dotnet build` command now copies NuGet dependencies for your application from the NuGet cache to the build output folder.</span></span> <span data-ttu-id="851eb-246">Wcześniej zależności były kopiowane tylko `dotnet publish`jako część pliku .</span><span class="sxs-lookup"><span data-stu-id="851eb-246">Previously, dependencies were only copied as part of `dotnet publish`.</span></span>

<span data-ttu-id="851eb-247">Istnieją pewne operacje, takie jak łączenie i publikowanie stron brzytwy, które nadal będą wymagały publikowania.</span><span class="sxs-lookup"><span data-stu-id="851eb-247">There are some operations, like linking and razor page publishing that will still require publishing.</span></span>

### <a name="local-tools"></a><span data-ttu-id="851eb-248">Narzędzia lokalne</span><span class="sxs-lookup"><span data-stu-id="851eb-248">Local tools</span></span>

<span data-ttu-id="851eb-249">.NET Core 3.0 wprowadza narzędzia lokalne.</span><span class="sxs-lookup"><span data-stu-id="851eb-249">.NET Core 3.0 introduces local tools.</span></span> <span data-ttu-id="851eb-250">Narzędzia lokalne są podobne do [narzędzi globalnych,](../tools/global-tools.md) ale są skojarzone z określoną lokalizacją na dysku.</span><span class="sxs-lookup"><span data-stu-id="851eb-250">Local tools are similar to [global tools](../tools/global-tools.md) but are associated with a particular location on disk.</span></span> <span data-ttu-id="851eb-251">Narzędzia lokalne nie są dostępne globalnie i są dystrybuowane jako pakiety NuGet.</span><span class="sxs-lookup"><span data-stu-id="851eb-251">Local tools aren't available globally and are distributed as NuGet packages.</span></span>

> [!WARNING]
> <span data-ttu-id="851eb-252">Jeśli w wersji .NET Core 3.0 Preview 1 `dotnet tool restore` `dotnet tool install`wypróbowano narzędzia lokalne, takie jak uruchamianie lub usuwanie folderu pamięci podręcznej narzędzi lokalnych.</span><span class="sxs-lookup"><span data-stu-id="851eb-252">If you tried local tools in .NET Core 3.0 Preview 1, such as running `dotnet tool restore` or `dotnet tool install`, delete the local tools cache folder.</span></span> <span data-ttu-id="851eb-253">W przeciwnym razie narzędzia lokalne nie będą działać w żadnej nowszej wersji.</span><span class="sxs-lookup"><span data-stu-id="851eb-253">Otherwise, local tools won't work on any newer release.</span></span> <span data-ttu-id="851eb-254">Ten folder znajduje się pod adresem:</span><span class="sxs-lookup"><span data-stu-id="851eb-254">This folder is located at:</span></span>
>
> <span data-ttu-id="851eb-255">W systemie macOS, Linux:`rm -r $HOME/.dotnet/toolResolverCache`</span><span class="sxs-lookup"><span data-stu-id="851eb-255">On macOS, Linux: `rm -r $HOME/.dotnet/toolResolverCache`</span></span>
>
> <span data-ttu-id="851eb-256">W systemie Windows:`rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`</span><span class="sxs-lookup"><span data-stu-id="851eb-256">On Windows: `rmdir /s %USERPROFILE%\.dotnet\toolResolverCache`</span></span>

<span data-ttu-id="851eb-257">Narzędzia lokalne opierają się `dotnet-tools.json` na oczywistej nazwie pliku w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="851eb-257">Local tools rely on a manifest file name `dotnet-tools.json` in your current directory.</span></span> <span data-ttu-id="851eb-258">Ten plik manifestu definiuje narzędzia, które mają być dostępne w tym folderze i poniżej.</span><span class="sxs-lookup"><span data-stu-id="851eb-258">This manifest file defines the tools to be available at that folder and below.</span></span> <span data-ttu-id="851eb-259">Można rozpowszechniać plik manifestu z kodem, aby upewnić się, że każdy, kto pracuje z kodem można przywrócić i używać tych samych narzędzi.</span><span class="sxs-lookup"><span data-stu-id="851eb-259">You can distribute the manifest file with your code to ensure that anyone who works with your code can restore and use the same tools.</span></span>

<span data-ttu-id="851eb-260">W przypadku narzędzi globalnych i lokalnych wymagana jest zgodna wersja środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="851eb-260">For both global and local tools, a compatible version of the runtime is required.</span></span> <span data-ttu-id="851eb-261">Wiele narzędzi, które są obecnie dostępne w NuGet.org celu .NET Core Runtime 2.1.</span><span class="sxs-lookup"><span data-stu-id="851eb-261">Many tools currently on NuGet.org target .NET Core Runtime 2.1.</span></span> <span data-ttu-id="851eb-262">Aby zainstalować te narzędzia globalnie lub lokalnie, nadal należy zainstalować [program NET Core 2.1 Runtime](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="851eb-262">To install these tools globally or locally, you would still need to install the [NET Core 2.1 Runtime](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span>

### <a name="new-globaljson-options"></a><span data-ttu-id="851eb-263">Nowe opcje global.json</span><span class="sxs-lookup"><span data-stu-id="851eb-263">New global.json options</span></span>

<span data-ttu-id="851eb-264">Plik *global.json* ma nowe opcje, które zapewniają większą elastyczność podczas próby zdefiniowania, która wersja .NET Core SDK jest używana.</span><span class="sxs-lookup"><span data-stu-id="851eb-264">The *global.json* file has new options that provide more flexibility when you're trying to define which version of the .NET Core SDK is used.</span></span> <span data-ttu-id="851eb-265">Nowe opcje to:</span><span class="sxs-lookup"><span data-stu-id="851eb-265">The new options are:</span></span>

- <span data-ttu-id="851eb-266">`allowPrerelease`: Wskazuje, czy program rozpoznawania nazw zestawów SDK powinien uwzględniać wersje wstępne podczas wybierania wersji sdk do użycia.</span><span class="sxs-lookup"><span data-stu-id="851eb-266">`allowPrerelease`: Indicates whether the SDK resolver should consider prerelease versions when selecting the SDK version to use.</span></span>
- <span data-ttu-id="851eb-267">`rollForward`: Wskazuje zasady przekazywania do przodu, które mają być używane podczas wybierania wersji sdk, albo jako rezerwowy, gdy brakuje określonej wersji sdk, albo jako dyrektywa do używania wyższej wersji.</span><span class="sxs-lookup"><span data-stu-id="851eb-267">`rollForward`: Indicates the roll-forward policy to use when selecting an SDK version, either as a fallback when a specific SDK version is missing or as a directive to use a higher version.</span></span>

<span data-ttu-id="851eb-268">Aby uzyskać więcej informacji na temat zmian, w tym wartości domyślnych, obsługiwanych wartości i nowych reguł dopasowywania, zobacz [global.json overview](../tools/global-json.md).</span><span class="sxs-lookup"><span data-stu-id="851eb-268">For more information about the changes including default values, supported values, and new matching rules, see [global.json overview](../tools/global-json.md).</span></span>

### <a name="smaller-garbage-collection-heap-sizes"></a><span data-ttu-id="851eb-269">Mniejsze rozmiary sterty wyrzucania elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="851eb-269">Smaller Garbage Collection heap sizes</span></span>

<span data-ttu-id="851eb-270">Domyślny rozmiar sterty modułu zbierającego elementy bezużyteczne został zmniejszony, co spowodowało użycie programu .NET Core przy użyciu mniejszej ilości pamięci.</span><span class="sxs-lookup"><span data-stu-id="851eb-270">The Garbage Collector's default heap size has been reduced resulting in .NET Core using less memory.</span></span> <span data-ttu-id="851eb-271">Ta zmiana lepiej dopasowuje się do budżetu alokacji generacji 0 z nowoczesnymi rozmiarami pamięci podręcznej procesora.</span><span class="sxs-lookup"><span data-stu-id="851eb-271">This change better aligns with the generation 0 allocation budget with modern processor cache sizes.</span></span>

### <a name="garbage-collection-large-page-support"></a><span data-ttu-id="851eb-272">Obsługa dużych stron wyrzucania elementów bezużytecznych</span><span class="sxs-lookup"><span data-stu-id="851eb-272">Garbage Collection Large Page support</span></span>

<span data-ttu-id="851eb-273">Duże strony (znane również jako Ogromne strony w systemie Linux) to funkcja, w której system operacyjny jest w stanie ustanowić regiony pamięci większe niż rozmiar strony macierzystej (często 4K), aby zwiększyć wydajność aplikacji żądającej tych dużych stron.</span><span class="sxs-lookup"><span data-stu-id="851eb-273">Large Pages (also known as Huge Pages on Linux) is a feature where the operating system is able to establish memory regions larger than the native page size (often 4K) to improve performance of the application requesting these large pages.</span></span>

<span data-ttu-id="851eb-274">Moduł zbierający elementy bezużyteczne można teraz skonfigurować za pomocą ustawienia **GCLargePages** jako funkcję opt-in, aby przydzielić duże strony w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="851eb-274">The Garbage Collector can now be configured with the **GCLargePages** setting as an opt-in feature to choose to allocate large pages on Windows.</span></span>

## <a name="windows-desktop--com"></a><span data-ttu-id="851eb-275">Środowisko com & dla komputerów stacjonarnych z systemem Windows</span><span class="sxs-lookup"><span data-stu-id="851eb-275">Windows Desktop & COM</span></span>

### <a name="net-core-sdk-windows-installer"></a><span data-ttu-id="851eb-276">Instalator sdk programu .NET Core systemu Windows</span><span class="sxs-lookup"><span data-stu-id="851eb-276">.NET Core SDK Windows Installer</span></span>

<span data-ttu-id="851eb-277">Instalator MSI dla systemu Windows został zmieniony począwszy od .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="851eb-277">The MSI installer for Windows has changed starting with .NET Core 3.0.</span></span> <span data-ttu-id="851eb-278">Instalatorzy sdk będą teraz uaktualniać wersje pasma funkcji SDK w miejscu.</span><span class="sxs-lookup"><span data-stu-id="851eb-278">The SDK installers will now upgrade SDK feature-band releases in place.</span></span> <span data-ttu-id="851eb-279">Pasma funkcji są zdefiniowane w *setkach* grup w sekcji *poprawek* numeru wersji.</span><span class="sxs-lookup"><span data-stu-id="851eb-279">Feature bands are defined in the *hundreds* groups in the *patch* section of the version number.</span></span> <span data-ttu-id="851eb-280">Na przykład \*\*3.0._ 101_ \*\* i \*\*3,0._ 201_ \*\* to wersje w dwóch różnych zespołach fabularnych, podczas gdy \*\*3.0._ 101_ \*\* i \*\*3,0._ 199_ \*\* są w tym samym zespole fabularnym.</span><span class="sxs-lookup"><span data-stu-id="851eb-280">For example, **3.0._101_** and **3.0._201_** are versions in two different feature bands while **3.0._101_** and **3.0._199_** are in the same feature band.</span></span> <span data-ttu-id="851eb-281">I, gdy .NET Core SDK \*\*3.0._ 101_ \*\* jest zainstalowany, .NET Core SDK \*\*3.0._ 100_ \*\* zostanie usunięty chorąna z urządzenia, jeśli istnieje.</span><span class="sxs-lookup"><span data-stu-id="851eb-281">And, when .NET Core SDK **3.0._101_** is installed, .NET Core SDK **3.0._100_** will be removed from the machine if it exists.</span></span> <span data-ttu-id="851eb-282">Gdy .NET Core SDK \*\*3.0._ 200_ \*\* jest zainstalowany na tym samym komputerze, .NET Core SDK \*\*3.0._ 101_ \*\* nie zostanie usunięty.</span><span class="sxs-lookup"><span data-stu-id="851eb-282">When .NET Core SDK **3.0._200_** is installed on the same machine, .NET Core SDK **3.0._101_** won't be removed.</span></span>

<span data-ttu-id="851eb-283">Aby uzyskać więcej informacji na temat wersji, zobacz [Omówienie wersji programu .NET Core](../versions/index.md).</span><span class="sxs-lookup"><span data-stu-id="851eb-283">For more information about versioning, see [Overview of how .NET Core is versioned](../versions/index.md).</span></span>

### <a name="windows-desktop"></a><span data-ttu-id="851eb-284">Pulpit systemu Windows</span><span class="sxs-lookup"><span data-stu-id="851eb-284">Windows desktop</span></span>

<span data-ttu-id="851eb-285">Program .NET Core 3.0 obsługuje aplikacje klasyczne systemu Windows przy użyciu programu Windows Presentation Foundation (WPF) i formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="851eb-285">.NET Core 3.0 supports Windows desktop applications using Windows Presentation Foundation (WPF) and Windows Forms.</span></span> <span data-ttu-id="851eb-286">Te struktury obsługują również przy użyciu nowoczesnych formantów i płynnego stylu z biblioteki XAML interfejsu użytkownika systemu Windows (WinUI) za pośrednictwem [wysp XAML](/windows/uwp/xaml-platform/xaml-host-controls).</span><span class="sxs-lookup"><span data-stu-id="851eb-286">These frameworks also support using modern controls and Fluent styling from the Windows UI XAML Library (WinUI) via [XAML islands](/windows/uwp/xaml-platform/xaml-host-controls).</span></span>

<span data-ttu-id="851eb-287">Składnik Pulpit systemu Windows jest częścią sdk windows .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="851eb-287">The Windows Desktop component is part of the Windows .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="851eb-288">Można utworzyć nową aplikację WPF lub Formularze systemu Windows za pomocą następujących `dotnet` poleceń:</span><span class="sxs-lookup"><span data-stu-id="851eb-288">You can create a new WPF or Windows Forms app with the following `dotnet` commands:</span></span>

```dotnetcli
dotnet new wpf
dotnet new winforms
```

<span data-ttu-id="851eb-289">Program Visual Studio 2019 dodaje nowe szablony **projektów** dla formularzy systemu Windows .NET Core 3.0 i WPF.</span><span class="sxs-lookup"><span data-stu-id="851eb-289">Visual Studio 2019 adds **New Project** templates for .NET Core 3.0 Windows Forms and WPF.</span></span>

<span data-ttu-id="851eb-290">Aby uzyskać więcej informacji na temat przenoszenia istniejącej aplikacji .NET Framework, zobacz [Projekty Port WPF](../../desktop-wpf/migration/convert-project-from-net-framework.md) i [Port Windows Forms .](../porting/winforms.md)</span><span class="sxs-lookup"><span data-stu-id="851eb-290">For more information about how to port an existing .NET Framework application, see [Port WPF projects](../../desktop-wpf/migration/convert-project-from-net-framework.md) and [Port Windows Forms projects](../porting/winforms.md).</span></span>

#### <a name="winforms-high-dpi"></a><span data-ttu-id="851eb-291">WinForms wysoki DPI</span><span class="sxs-lookup"><span data-stu-id="851eb-291">WinForms high DPI</span></span>

<span data-ttu-id="851eb-292">Aplikacje .NET Core Windows Forms można <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType>ustawić tryb wysokiej dpi za pomocą .</span><span class="sxs-lookup"><span data-stu-id="851eb-292">.NET Core Windows Forms applications can set high DPI mode with <xref:System.Windows.Forms.Application.SetHighDpiMode(System.Windows.Forms.HighDpiMode)?displayProperty=nameWithType>.</span></span> <span data-ttu-id="851eb-293">Metoda `SetHighDpiMode` ustawia odpowiedni tryb wysokiego DPI, chyba że ustawienie `App.Manifest` zostało ustawione w `Application.Run`inny sposób, taki jak p/invoke przed .</span><span class="sxs-lookup"><span data-stu-id="851eb-293">The `SetHighDpiMode` method sets the corresponding high DPI mode unless the setting has been set by other means like `App.Manifest` or P/Invoke before `Application.Run`.</span></span>

<span data-ttu-id="851eb-294">Możliwe `highDpiMode` wartości, wyrażone w <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType> wyliczeniu są następujące:</span><span class="sxs-lookup"><span data-stu-id="851eb-294">The possible `highDpiMode` values, as expressed by the <xref:System.Windows.Forms.HighDpiMode?displayProperty=nameWithType> enum are:</span></span>

- `DpiUnaware`
- `SystemAware`
- `PerMonitor`
- `PerMonitorV2`
- `DpiUnawareGdiScaled`

<span data-ttu-id="851eb-295">Aby uzyskać więcej informacji na temat trybów wysokiej dpi, zobacz [Programowanie aplikacji pulpitu o wysokiej dpi w systemie Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows).</span><span class="sxs-lookup"><span data-stu-id="851eb-295">For more information about high DPI modes, see [High DPI Desktop Application Development on Windows](/windows/desktop/hidpi/high-dpi-desktop-application-development-on-windows).</span></span>

### <a name="create-com-components"></a><span data-ttu-id="851eb-296">Tworzenie składników COM</span><span class="sxs-lookup"><span data-stu-id="851eb-296">Create COM components</span></span>

<span data-ttu-id="851eb-297">W systemie Windows można teraz tworzyć składniki zarządzane wywoływane przez com.</span><span class="sxs-lookup"><span data-stu-id="851eb-297">On Windows, you can now create COM-callable managed components.</span></span> <span data-ttu-id="851eb-298">Ta funkcja ma kluczowe znaczenie dla używania .NET Core z modelami dodatku COM, a także w celu zapewnienia parzystości z .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="851eb-298">This capability is critical to use .NET Core with COM add-in models and also to provide parity with .NET Framework.</span></span>

<span data-ttu-id="851eb-299">W przeciwieństwie do platformy .NET Framework, w której jako serwera COM był używany *plik mscoree.dll,* program .NET Core doda do katalogu *bin* serwer natywnej dll wyrzutni.</span><span class="sxs-lookup"><span data-stu-id="851eb-299">Unlike .NET Framework where the *mscoree.dll* was used as the COM server, .NET Core will add a native launcher dll to the *bin* directory when you build your COM component.</span></span>

<span data-ttu-id="851eb-300">Aby zapoznać się z przykładem sposobu tworzenia składnika COM i używania go, zobacz [pokaz modelu COM](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).</span><span class="sxs-lookup"><span data-stu-id="851eb-300">For an example of how to create a COM component and consume it, see the [COM Demo](https://github.com/dotnet/samples/tree/master/core/extensions/COMServerDemo).</span></span>

### <a name="windows-native-interop"></a><span data-ttu-id="851eb-301">Windows Native Interop</span><span class="sxs-lookup"><span data-stu-id="851eb-301">Windows Native Interop</span></span>

<span data-ttu-id="851eb-302">System Windows oferuje bogaty natywny interfejs API w postaci płaskich interfejsów API C, COM i WinRT.</span><span class="sxs-lookup"><span data-stu-id="851eb-302">Windows offers a rich native API in the form of flat C APIs, COM, and WinRT.</span></span> <span data-ttu-id="851eb-303">Podczas gdy .NET Core obsługuje **P/Invoke**, .NET Core 3.0 dodaje możliwość **współtworzenia interfejsów API COM** i **aktywowania interfejsów API WinRT**.</span><span class="sxs-lookup"><span data-stu-id="851eb-303">While .NET Core supports **P/Invoke**, .NET Core 3.0 adds the ability to **CoCreate COM APIs** and **Activate WinRT APIs**.</span></span> <span data-ttu-id="851eb-304">Na przykład kodu zobacz [Pokaz programu Excel](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).</span><span class="sxs-lookup"><span data-stu-id="851eb-304">For a code example, see the [Excel Demo](https://github.com/dotnet/samples/tree/master/core/extensions/ExcelDemo).</span></span>

### <a name="msix-deployment"></a><span data-ttu-id="851eb-305">Wdrożenie MSIX</span><span class="sxs-lookup"><span data-stu-id="851eb-305">MSIX Deployment</span></span>

<span data-ttu-id="851eb-306">[MSIX](https://docs.microsoft.com/windows/msix/) to nowy format pakietu aplikacji systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="851eb-306">[MSIX](https://docs.microsoft.com/windows/msix/) is a new Windows application package format.</span></span> <span data-ttu-id="851eb-307">Może służyć do wdrażania aplikacji komputerowych .NET Core 3.0 w systemie Windows 10.</span><span class="sxs-lookup"><span data-stu-id="851eb-307">It can be used to deploy .NET Core 3.0 desktop applications to Windows 10.</span></span>

<span data-ttu-id="851eb-308">[Projekt pakowania aplikacji systemu Windows](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), dostępny w programie Visual Studio 2019, umożliwia tworzenie pakietów MSIX z [samodzielnymi](../deploying/index.md#publish-self-contained) aplikacjami .NET Core.</span><span class="sxs-lookup"><span data-stu-id="851eb-308">The [Windows Application Packaging Project](https://docs.microsoft.com/windows/uwp/porting/desktop-to-uwp-packaging-dot-net), available in Visual Studio 2019, allows you to create MSIX packages with [self-contained](../deploying/index.md#publish-self-contained) .NET Core applications.</span></span>

<span data-ttu-id="851eb-309">Plik projektu .NET Core musi określać obsługiwane `<RuntimeIdentifiers>` działania uruchomieniowe we właściwości:</span><span class="sxs-lookup"><span data-stu-id="851eb-309">The .NET Core project file must specify the supported runtimes in the `<RuntimeIdentifiers>` property:</span></span>

```xml
<RuntimeIdentifiers>win-x86;win-x64</RuntimeIdentifiers>
```

## <a name="linux-improvements"></a><span data-ttu-id="851eb-310">Ulepszenia Linuksa</span><span class="sxs-lookup"><span data-stu-id="851eb-310">Linux improvements</span></span>

### <a name="serialport-for-linux"></a><span data-ttu-id="851eb-311">SerialPort dla systemu Linux</span><span class="sxs-lookup"><span data-stu-id="851eb-311">SerialPort for Linux</span></span>

<span data-ttu-id="851eb-312">.NET Core 3.0 zapewnia <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> podstawową obsługę w systemie Linux.</span><span class="sxs-lookup"><span data-stu-id="851eb-312">.NET Core 3.0 provides basic support for <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> on Linux.</span></span>

<span data-ttu-id="851eb-313">Wcześniej program .NET Core `SerialPort` był obsługiwany tylko w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="851eb-313">Previously, .NET Core only supported using `SerialPort` on Windows.</span></span>

<span data-ttu-id="851eb-314">Aby uzyskać więcej informacji na temat ograniczonej obsługi portu szeregowego w systemie Linux, zobacz [Problem usługi GitHub #33146](https://github.com/dotnet/corefx/issues/33146).</span><span class="sxs-lookup"><span data-stu-id="851eb-314">For more information about the limited support for the serial port on Linux, see [GitHub issue #33146](https://github.com/dotnet/corefx/issues/33146).</span></span>

### <a name="docker-and-cgroup-memory-limits"></a><span data-ttu-id="851eb-315">Limity pamięci docker i cgroup</span><span class="sxs-lookup"><span data-stu-id="851eb-315">Docker and cgroup memory Limits</span></span>

<span data-ttu-id="851eb-316">Uruchamianie .NET Core 3.0 w systemie Linux z platformą Docker działa lepiej z limitami pamięci grupy cgroup.</span><span class="sxs-lookup"><span data-stu-id="851eb-316">Running .NET Core 3.0 on Linux with Docker works better with cgroup memory limits.</span></span> <span data-ttu-id="851eb-317">Uruchamianie kontenera platformy Docker `docker run -m`z limitami pamięci, na przykład z , zmienia sposób działania programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="851eb-317">Running a Docker container with memory limits, such as with `docker run -m`, changes how .NET Core behaves.</span></span>

- <span data-ttu-id="851eb-318">Domyślny rozmiar sterty modułu zbierającego elementy bezużyteczne (GC): maksymalnie 20 mb lub 75% limitu pamięci w kontenerze.</span><span class="sxs-lookup"><span data-stu-id="851eb-318">Default Garbage Collector (GC) heap size: maximum of 20 mb or 75% of the memory limit on the container.</span></span>
- <span data-ttu-id="851eb-319">Rozmiar jawny można ustawić jako liczbę bezwzględną lub procent limitu grupy.</span><span class="sxs-lookup"><span data-stu-id="851eb-319">Explicit size can be set as an absolute number or percentage of cgroup limit.</span></span>
- <span data-ttu-id="851eb-320">Minimalny zarezerwowany rozmiar segmentu na stertę GC wynosi 16 mb.</span><span class="sxs-lookup"><span data-stu-id="851eb-320">Minimum reserved segment size per GC heap is 16 mb.</span></span> <span data-ttu-id="851eb-321">Ten rozmiar zmniejsza liczbę stert, które są tworzone na maszynach.</span><span class="sxs-lookup"><span data-stu-id="851eb-321">This size reduces the number of heaps that are created on machines.</span></span>

### <a name="gpio-support-for-raspberry-pi"></a><span data-ttu-id="851eb-322">Obsługa GPIO dla Raspberry Pi</span><span class="sxs-lookup"><span data-stu-id="851eb-322">GPIO Support for Raspberry Pi</span></span>

<span data-ttu-id="851eb-323">Dwa pakiety zostały wydane do NuGet, które można użyć do programowania GPIO:</span><span class="sxs-lookup"><span data-stu-id="851eb-323">Two packages have been released to NuGet that you can use for GPIO programming:</span></span>

- [<span data-ttu-id="851eb-324">System.Device.Gpio</span><span class="sxs-lookup"><span data-stu-id="851eb-324">System.Device.Gpio</span></span>](https://www.nuget.org/packages/System.Device.Gpio)
- [<span data-ttu-id="851eb-325">Wiązania iot.Device.bindings</span><span class="sxs-lookup"><span data-stu-id="851eb-325">Iot.Device.Bindings</span></span>](https://www.nuget.org/packages/Iot.Device.Bindings)

<span data-ttu-id="851eb-326">Pakiety GPIO zawierają interfejsy API dla urządzeń *GPIO,* *SPI,* *I2C*i *PWM.*</span><span class="sxs-lookup"><span data-stu-id="851eb-326">The GPIO packages include APIs for *GPIO*, *SPI*, *I2C*, and *PWM* devices.</span></span> <span data-ttu-id="851eb-327">Pakiet powiązań IoT zawiera powiązania urządzeń.</span><span class="sxs-lookup"><span data-stu-id="851eb-327">The IoT bindings package includes device bindings.</span></span> <span data-ttu-id="851eb-328">Aby uzyskać więcej informacji, zobacz [urządzenia GitHub repo](https://github.com/dotnet/iot/blob/master/src/devices/).</span><span class="sxs-lookup"><span data-stu-id="851eb-328">For more information, see the [devices GitHub repo](https://github.com/dotnet/iot/blob/master/src/devices/).</span></span>

### <a name="arm64-linux-support"></a><span data-ttu-id="851eb-329">Obsługa systemu ARM64 Linux</span><span class="sxs-lookup"><span data-stu-id="851eb-329">ARM64 Linux support</span></span>

<span data-ttu-id="851eb-330">.NET Core 3.0 dodaje obsługę arm64 dla systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="851eb-330">.NET Core 3.0 adds support for ARM64 for Linux.</span></span> <span data-ttu-id="851eb-331">Głównym przypadkiem użycia dla ARM64 jest obecnie ze scenariuszami IoT.</span><span class="sxs-lookup"><span data-stu-id="851eb-331">The primary use case for ARM64 is currently with IoT scenarios.</span></span> <span data-ttu-id="851eb-332">Aby uzyskać więcej informacji, zobacz [.NET Core ARM64 Status](https://github.com/dotnet/announcements/issues/82).</span><span class="sxs-lookup"><span data-stu-id="851eb-332">For more information, see [.NET Core ARM64 Status](https://github.com/dotnet/announcements/issues/82).</span></span>

<span data-ttu-id="851eb-333">[Obrazy docker dla .NET Core na ARM64](https://hub.docker.com/r/microsoft/dotnet/) są dostępne dla Alpine, Debiana i Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="851eb-333">[Docker images for .NET Core on ARM64](https://hub.docker.com/r/microsoft/dotnet/) are available for Alpine, Debian, and Ubuntu.</span></span>

> [!NOTE]
> <span data-ttu-id="851eb-334">**ARM64 ( ARM64 )** Pomoc techniczna systemu Windows nie jest jeszcze dostępna.</span><span class="sxs-lookup"><span data-stu-id="851eb-334">**ARM64** Windows support isn't yet available.</span></span>

## <a name="security"></a><span data-ttu-id="851eb-335">Zabezpieczenia</span><span class="sxs-lookup"><span data-stu-id="851eb-335">Security</span></span>

### <a name="tls-13--openssl-111-on-linux"></a><span data-ttu-id="851eb-336">TLS 1.3 & OpenSSL 1.1.1 w systemie Linux</span><span class="sxs-lookup"><span data-stu-id="851eb-336">TLS 1.3 & OpenSSL 1.1.1 on Linux</span></span>

<span data-ttu-id="851eb-337">Program .NET Core korzysta teraz z [obsługi protokołu TLS 1.3 w openssl 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), gdy jest dostępny w danym środowisku.</span><span class="sxs-lookup"><span data-stu-id="851eb-337">.NET Core now takes advantage of [TLS 1.3 support in OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), when it's available in a given environment.</span></span> <span data-ttu-id="851eb-338">Z TLS 1.3:</span><span class="sxs-lookup"><span data-stu-id="851eb-338">With TLS 1.3:</span></span>

- <span data-ttu-id="851eb-339">Czasy połączenia są poprawiane dzięki ograniczeniu liczby przejazdów w obie strony między klientem a serwerem.</span><span class="sxs-lookup"><span data-stu-id="851eb-339">Connection times are improved with reduced round trips required between the client and server.</span></span>
- <span data-ttu-id="851eb-340">Poprawiono bezpieczeństwo dzięki usunięciu różnych przestarzałych i niezabezpieczonych algorytmów kryptograficznych.</span><span class="sxs-lookup"><span data-stu-id="851eb-340">Improved security because of the removal of various obsolete and insecure cryptographic algorithms.</span></span>

<span data-ttu-id="851eb-341">Jeśli jest dostępny, .NET Core 3.0 używa **OpenSSL 1.1.1**, **OpenSSL 1.1.0**lub **OpenSSL 1.0.2** w systemie Linux.</span><span class="sxs-lookup"><span data-stu-id="851eb-341">When available, .NET Core 3.0 uses **OpenSSL 1.1.1**, **OpenSSL 1.1.0**, or **OpenSSL 1.0.2** on a Linux system.</span></span> <span data-ttu-id="851eb-342">Gdy **openssl 1.1.1** jest <xref:System.Net.Security.SslStream?displayProperty=nameWithType> <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> dostępny, oba i typy będą używać **TLS 1.3** (przy założeniu, że zarówno klient, jak i serwer obsługują **TLS 1.3).**</span><span class="sxs-lookup"><span data-stu-id="851eb-342">When **OpenSSL 1.1.1** is available, both <xref:System.Net.Security.SslStream?displayProperty=nameWithType> and <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> types will use **TLS 1.3** (assuming both the client and server support **TLS 1.3**).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="851eb-343">Systemy Windows i macOS nie obsługują jeszcze **protokołu TLS 1.3**.</span><span class="sxs-lookup"><span data-stu-id="851eb-343">Windows and macOS do not yet support **TLS 1.3**.</span></span> <span data-ttu-id="851eb-344">.NET Core 3.0 będzie obsługiwać **protokół TLS 1.3** w tych systemach operacyjnych, gdy pomoc techniczna stanie się dostępna.</span><span class="sxs-lookup"><span data-stu-id="851eb-344">.NET Core 3.0 will support **TLS 1.3** on these operating systems when support becomes available.</span></span>

<span data-ttu-id="851eb-345">Poniższy przykład języka C# 8.0 pokazuje ,NET Core 3.0 na <https://www.cloudflare.com>Ubuntu 18.10 łączącsię z:</span><span class="sxs-lookup"><span data-stu-id="851eb-345">The following C# 8.0 example demonstrates .NET Core 3.0 on Ubuntu 18.10 connecting to <https://www.cloudflare.com>:</span></span>

[!code-csharp[TLSExample](~/samples/snippets/core/whats-new/whats-new-in-30/cs/TLS.cs#TLS)]

### <a name="cryptography-ciphers"></a><span data-ttu-id="851eb-346">Szyfry kryptograficzne</span><span class="sxs-lookup"><span data-stu-id="851eb-346">Cryptography ciphers</span></span>

<span data-ttu-id="851eb-347">.NET 3.0 dodaje obsługę szyfrów **AES-GCM** i **AES-CCM,** zaimplementowanych odpowiednio z <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> i <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="851eb-347">.NET 3.0 adds support for **AES-GCM** and **AES-CCM** ciphers, implemented with <xref:System.Security.Cryptography.AesGcm?displayProperty=nameWithType> and <xref:System.Security.Cryptography.AesCcm?displayProperty=nameWithType> respectively.</span></span> <span data-ttu-id="851eb-348">Algorytmy te są zarówno [uwierzytelnione szyfrowanie z danymi skojarzenia (AEAD) algorytmy](https://en.wikipedia.org/wiki/Authenticated_encryption).</span><span class="sxs-lookup"><span data-stu-id="851eb-348">These algorithms are both [Authenticated Encryption with Association Data (AEAD) algorithms](https://en.wikipedia.org/wiki/Authenticated_encryption).</span></span>

<span data-ttu-id="851eb-349">Poniższy kod demonstruje użycie `AesGcm` szyfru do szyfrowania i odszyfrowywania losowych danych.</span><span class="sxs-lookup"><span data-stu-id="851eb-349">The following code demonstrates using `AesGcm` cipher to encrypt and decrypt random data.</span></span>

[!code-csharp[AesGcm](~/samples/snippets/core/whats-new/whats-new-in-30/cs/Cipher.cs#AesGcm)]

### <a name="cryptographic-key-importexport"></a><span data-ttu-id="851eb-350">Import/eksport kluczy kryptograficznych</span><span class="sxs-lookup"><span data-stu-id="851eb-350">Cryptographic Key Import/Export</span></span>

<span data-ttu-id="851eb-351">.NET Core 3.0 obsługuje import i eksport asymetrycznych kluczy publicznych i prywatnych ze standardowych formatów.</span><span class="sxs-lookup"><span data-stu-id="851eb-351">.NET Core 3.0 supports the import and export of asymmetric public and private keys from standard formats.</span></span> <span data-ttu-id="851eb-352">Nie musisz używać certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="851eb-352">You don't need to use an X.509 certificate.</span></span>

<span data-ttu-id="851eb-353">Wszystkie typy kluczy, takie jak *RSA,* *DSA,* *ECDsa*i *ECDiffieHellman,* obsługują następujące formaty:</span><span class="sxs-lookup"><span data-stu-id="851eb-353">All key types, such as *RSA*, *DSA*, *ECDsa*, and *ECDiffieHellman*, support the following formats:</span></span>

- <span data-ttu-id="851eb-354">**Klucz publiczny**</span><span class="sxs-lookup"><span data-stu-id="851eb-354">**Public Key**</span></span>
  - <span data-ttu-id="851eb-355">X.509 SubjectPublicKeyInfo</span><span class="sxs-lookup"><span data-stu-id="851eb-355">X.509 SubjectPublicKeyInfo</span></span>

- <span data-ttu-id="851eb-356">**Klucz prywatny**</span><span class="sxs-lookup"><span data-stu-id="851eb-356">**Private key**</span></span>
  - <span data-ttu-id="851eb-357">PKCS#8 PrivateKeyInfo</span><span class="sxs-lookup"><span data-stu-id="851eb-357">PKCS#8 PrivateKeyInfo</span></span>
  - <span data-ttu-id="851eb-358">PKCS#8 EncryptedPrivateKeyInfo</span><span class="sxs-lookup"><span data-stu-id="851eb-358">PKCS#8 EncryptedPrivateKeyInfo</span></span>

<span data-ttu-id="851eb-359">Klawisze RSA obsługują również:</span><span class="sxs-lookup"><span data-stu-id="851eb-359">RSA keys also support:</span></span>

- <span data-ttu-id="851eb-360">**Klucz publiczny**</span><span class="sxs-lookup"><span data-stu-id="851eb-360">**Public Key**</span></span>
  - <span data-ttu-id="851eb-361">PKCS#1 RSAPublicKey</span><span class="sxs-lookup"><span data-stu-id="851eb-361">PKCS#1 RSAPublicKey</span></span>

- <span data-ttu-id="851eb-362">**Klucz prywatny**</span><span class="sxs-lookup"><span data-stu-id="851eb-362">**Private key**</span></span>
  - <span data-ttu-id="851eb-363">PKCS#1 RSAPrivateKey</span><span class="sxs-lookup"><span data-stu-id="851eb-363">PKCS#1 RSAPrivateKey</span></span>

<span data-ttu-id="851eb-364">Metody eksportu produkują dane binarne zakodowane w formacie DER, a metody importu oczekują tego samego.</span><span class="sxs-lookup"><span data-stu-id="851eb-364">The export methods produce DER-encoded binary data, and the import methods expect the same.</span></span> <span data-ttu-id="851eb-365">Jeśli klucz jest przechowywany w formacie PEM przyjazny dla tekstu, obiekt wywołujący będzie musiał base64-dekodować zawartość przed wywołaniem metody importu.</span><span class="sxs-lookup"><span data-stu-id="851eb-365">If a key is stored in the text-friendly PEM format, the caller will need to base64-decode the content before calling an import method.</span></span>

[!code-csharp[RSA](~/samples/snippets/core/whats-new/whats-new-in-30/cs/RSA.cs#Rsa)]

<span data-ttu-id="851eb-366">**Pliki PKCS#8** można sprawdzić, <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType> a pliki **PFX/PKCS#12** <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType>można sprawdzić za pomocą .</span><span class="sxs-lookup"><span data-stu-id="851eb-366">**PKCS#8** files can be inspected with <xref:System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo?displayProperty=nameWithType> and **PFX/PKCS#12** files can be inspected with <xref:System.Security.Cryptography.Pkcs.Pkcs12Info?displayProperty=nameWithType>.</span></span> <span data-ttu-id="851eb-367">**Pliki PFX/PKCS#12** można manipulować za pomocą <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="851eb-367">**PFX/PKCS#12** files can be manipulated with <xref:System.Security.Cryptography.Pkcs.Pkcs12Builder?displayProperty=nameWithType>.</span></span>

## <a name="net-core-30-api-changes"></a><span data-ttu-id="851eb-368">Zmiany interfejsu API .NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="851eb-368">.NET Core 3.0 API changes</span></span>

### <a name="ranges-and-indices"></a><span data-ttu-id="851eb-369">Zakresy i indeksy</span><span class="sxs-lookup"><span data-stu-id="851eb-369">Ranges and indices</span></span>

<span data-ttu-id="851eb-370">Nowy <xref:System.Index?displayProperty=nameWithType> typ może służyć do indeksowania.</span><span class="sxs-lookup"><span data-stu-id="851eb-370">The new <xref:System.Index?displayProperty=nameWithType> type can be used for indexing.</span></span> <span data-ttu-id="851eb-371">Można utworzyć jeden `int` z tego, który liczy się `^` od początku lub z operatorem prefiksu (C#), który liczy się od końca:</span><span class="sxs-lookup"><span data-stu-id="851eb-371">You can create one from an `int` that counts from the beginning, or with a prefix `^` operator (C#) that counts from the end:</span></span>

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

<span data-ttu-id="851eb-372">Istnieje również <xref:System.Range?displayProperty=nameWithType> typ, który składa `Index` się z dwóch wartości, jeden dla początku i jeden `x..y` na koniec i mogą być zapisywane z wyrażeniem zakresu (C#).</span><span class="sxs-lookup"><span data-stu-id="851eb-372">There's also the <xref:System.Range?displayProperty=nameWithType> type, which consists of two `Index` values, one for the start and one for the end, and can be written with a `x..y` range expression (C#).</span></span> <span data-ttu-id="851eb-373">Następnie można indeksować `Range`za pomocą , który tworzy plasterek:</span><span class="sxs-lookup"><span data-stu-id="851eb-373">You can then index with a `Range`, which produces a slice:</span></span>

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

<span data-ttu-id="851eb-374">Aby uzyskać więcej informacji, zobacz [zakresy i indeksy samouczek](../../csharp/tutorials/ranges-indexes.md).</span><span class="sxs-lookup"><span data-stu-id="851eb-374">For more information, see the [ranges and indices tutorial](../../csharp/tutorials/ranges-indexes.md).</span></span>

### <a name="async-streams"></a><span data-ttu-id="851eb-375">Strumienie asynchroniczne</span><span class="sxs-lookup"><span data-stu-id="851eb-375">Async streams</span></span>

<span data-ttu-id="851eb-376">Typ <xref:System.Collections.Generic.IAsyncEnumerable%601> jest nową asynchroniczną <xref:System.Collections.Generic.IEnumerable%601>wersją programu .</span><span class="sxs-lookup"><span data-stu-id="851eb-376">The <xref:System.Collections.Generic.IAsyncEnumerable%601> type is a new asynchronous version of <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="851eb-377">Język pozwala `await foreach` na `IAsyncEnumerable<T>` korzystanie z ich `yield return` elementów i używać do nich do tworzenia elementów.</span><span class="sxs-lookup"><span data-stu-id="851eb-377">The language lets you `await foreach` over `IAsyncEnumerable<T>` to consume their elements, and use `yield return` to them to produce elements.</span></span>

<span data-ttu-id="851eb-378">W poniższym przykładzie przedstawiono zarówno produkcję, jak i zużycie strumieni asynchronii.</span><span class="sxs-lookup"><span data-stu-id="851eb-378">The following example demonstrates both production and consumption of async streams.</span></span> <span data-ttu-id="851eb-379">Instrukcja `foreach` jest async `yield return` i sam używa do tworzenia strumienia asynchronicznego dla wywołań.</span><span class="sxs-lookup"><span data-stu-id="851eb-379">The `foreach` statement is async and itself uses `yield return` to produce an async stream for callers.</span></span> <span data-ttu-id="851eb-380">Ten wzorzec (za pomocą `yield return`) jest zalecanym modelem do tworzenia strumieni asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="851eb-380">This pattern (using `yield return`) is the recommended model for producing async streams.</span></span>

```csharp
async IAsyncEnumerable<int> GetBigResultsAsync()
{
    await foreach (var result in GetResultsAsync())
    {
        if (result > 20) yield return result;
    }
}
```

<span data-ttu-id="851eb-381">Oprócz możliwości `await foreach`, można również utworzyć iteratory asynchroniczne, na przykład iterator, który `await` `yield` `IAsyncEnumerable/IAsyncEnumerator` zwraca, że można zarówno i w.</span><span class="sxs-lookup"><span data-stu-id="851eb-381">In addition to being able to `await foreach`, you can also create async iterators, for example, an iterator that returns an `IAsyncEnumerable/IAsyncEnumerator` that you can both `await` and `yield` in.</span></span> <span data-ttu-id="851eb-382">W przypadku obiektów, które muszą zostać `IAsyncDisposable`usunięte, można użyć , `Stream` które `Timer`różne typy BCL implementują, takie jak i .</span><span class="sxs-lookup"><span data-stu-id="851eb-382">For objects that need to be disposed, you can use `IAsyncDisposable`, which various BCL types implement, such as `Stream` and `Timer`.</span></span>

<span data-ttu-id="851eb-383">Aby uzyskać więcej informacji, zobacz [samouczek strumieni asynchroniczych](../../csharp/tutorials/generate-consume-asynchronous-stream.md).</span><span class="sxs-lookup"><span data-stu-id="851eb-383">For more information, see the [async streams tutorial](../../csharp/tutorials/generate-consume-asynchronous-stream.md).</span></span>

### <a name="ieee-floating-point"></a><span data-ttu-id="851eb-384">Zmiennoprzecinkowy punkt pływatowy IEEE</span><span class="sxs-lookup"><span data-stu-id="851eb-384">IEEE Floating-point</span></span>

<span data-ttu-id="851eb-385">Interfejsy API zmiennoprzecinkowych są aktualizowane zgodnie z [wersją IEEE 754-2008.](https://en.wikipedia.org/wiki/IEEE_754-2008_revision)</span><span class="sxs-lookup"><span data-stu-id="851eb-385">Floating point APIs are being updated to comply with [IEEE 754-2008 revision](https://en.wikipedia.org/wiki/IEEE_754-2008_revision).</span></span> <span data-ttu-id="851eb-386">Celem tych zmian jest udostępnienie wszystkich **wymaganych** operacji i upewnienie się, że są one zgodne behawioralnie ze specyfikacją IEEE. Aby uzyskać więcej informacji na temat ulepszeń zmiennoprzecinkowych, zobacz [ulepszenia analizy i formatowania zmiennoprzecinkowego w blogu .NET Core 3.0.](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/)</span><span class="sxs-lookup"><span data-stu-id="851eb-386">The goal of these changes is to expose all **required** operations and ensure that they're behaviorally compliant with the IEEE spec. For more information about floating-point improvements, see the [Floating-Point Parsing and Formatting improvements in .NET Core 3.0](https://devblogs.microsoft.com/dotnet/floating-point-parsing-and-formatting-improvements-in-net-core-3-0/) blog post.</span></span>

<span data-ttu-id="851eb-387">Poprawki dotyczące analiz owania i formatowania obejmują:</span><span class="sxs-lookup"><span data-stu-id="851eb-387">Parsing and formatting fixes include:</span></span>

- <span data-ttu-id="851eb-388">Poprawnie analizować i okrągłe dane wejściowe o dowolnej długości.</span><span class="sxs-lookup"><span data-stu-id="851eb-388">Correctly parse and round inputs of any length.</span></span>
- <span data-ttu-id="851eb-389">Poprawnie przeanalizować i sformatować ujemne zero.</span><span class="sxs-lookup"><span data-stu-id="851eb-389">Correctly parse and format negative zero.</span></span>
- <span data-ttu-id="851eb-390">Poprawnie przeanalizować `Infinity` i `NaN` wykonując sprawdzanie bez uwzględniania wielkości liter `+` i pozwalając opcjonalne poprzedzające w stosownych przypadkach.</span><span class="sxs-lookup"><span data-stu-id="851eb-390">Correctly parse `Infinity` and `NaN` by doing a case-insensitive check and allowing an optional preceding `+` where applicable.</span></span>

<span data-ttu-id="851eb-391">Nowe <xref:System.Math?displayProperty=nameWithType> interfejsy API obejmują:</span><span class="sxs-lookup"><span data-stu-id="851eb-391">New <xref:System.Math?displayProperty=nameWithType> APIs include:</span></span>

- <span data-ttu-id="851eb-392"><xref:System.Math.BitIncrement(System.Double)>I<xref:System.Math.BitDecrement(System.Double)></span><span class="sxs-lookup"><span data-stu-id="851eb-392"><xref:System.Math.BitIncrement(System.Double)> and <xref:System.Math.BitDecrement(System.Double)></span></span>\
<span data-ttu-id="851eb-393">Odpowiada operacjom `nextUp` `nextDown` ieee i IEEE.</span><span class="sxs-lookup"><span data-stu-id="851eb-393">Corresponds to the `nextUp` and `nextDown` IEEE operations.</span></span> <span data-ttu-id="851eb-394">Zwracają najmniejszą liczbę zmiennoprzecinkową, która porównuje większe lub mniejsze niż dane wejściowe (odpowiednio).</span><span class="sxs-lookup"><span data-stu-id="851eb-394">They return the smallest floating-point number that compares greater or lesser than the input (respectively).</span></span> <span data-ttu-id="851eb-395">Na przykład, `Math.BitIncrement(0.0)` `double.Epsilon`zwróci .</span><span class="sxs-lookup"><span data-stu-id="851eb-395">For example, `Math.BitIncrement(0.0)` would return `double.Epsilon`.</span></span>

- <span data-ttu-id="851eb-396"><xref:System.Math.MaxMagnitude(System.Double,System.Double)>I<xref:System.Math.MinMagnitude(System.Double,System.Double)></span><span class="sxs-lookup"><span data-stu-id="851eb-396"><xref:System.Math.MaxMagnitude(System.Double,System.Double)> and <xref:System.Math.MinMagnitude(System.Double,System.Double)></span></span>\
<span data-ttu-id="851eb-397">Odpowiada `maxNumMag` i `minNumMag` IEEE operacji, zwracają wartość, która jest większa lub mniejsza wielkości dwóch danych wejściowych (odpowiednio).</span><span class="sxs-lookup"><span data-stu-id="851eb-397">Corresponds to the `maxNumMag` and `minNumMag` IEEE operations, they return the value that is greater or lesser in magnitude of the two inputs (respectively).</span></span> <span data-ttu-id="851eb-398">Na przykład, `Math.MaxMagnitude(2.0, -3.0)` `-3.0`zwróci .</span><span class="sxs-lookup"><span data-stu-id="851eb-398">For example, `Math.MaxMagnitude(2.0, -3.0)` would return `-3.0`.</span></span>

- <xref:System.Math.ILogB(System.Double)>\
<span data-ttu-id="851eb-399">Odpowiada operacji `logB` IEEE, która zwraca wartość integralną, zwraca integralną dziennika base-2 parametru wejściowego.</span><span class="sxs-lookup"><span data-stu-id="851eb-399">Corresponds to the `logB` IEEE operation that returns an integral value, it returns the integral base-2 log of the input parameter.</span></span> <span data-ttu-id="851eb-400">Ta metoda jest skutecznie `floor(log2(x))`taka sama jak , ale wykonane z minimalnym błędem zaokrąglania.</span><span class="sxs-lookup"><span data-stu-id="851eb-400">This method is effectively the same as `floor(log2(x))`, but done with minimal rounding error.</span></span>

- <xref:System.Math.ScaleB(System.Double,System.Int32)>\
<span data-ttu-id="851eb-401">Odpowiada operacji `scaleB` IEEE, która przyjmuje wartość integralną, `x * pow(2, n)`zwraca skutecznie , ale odbywa się przy minimalnym błędzie zaokrąglania.</span><span class="sxs-lookup"><span data-stu-id="851eb-401">Corresponds to the `scaleB` IEEE operation that takes an integral value, it returns effectively `x * pow(2, n)`, but is done with minimal rounding error.</span></span>

- <xref:System.Math.Log2(System.Double)>\
<span data-ttu-id="851eb-402">Odpowiada operacji `log2` IEEE, zwraca logarytm base-2.</span><span class="sxs-lookup"><span data-stu-id="851eb-402">Corresponds to the `log2` IEEE operation, it returns the base-2 logarithm.</span></span> <span data-ttu-id="851eb-403">Minimalizuje błąd zaokrąglania.</span><span class="sxs-lookup"><span data-stu-id="851eb-403">It minimizes rounding error.</span></span>

- <xref:System.Math.FusedMultiplyAdd(System.Double,System.Double,System.Double)>\
<span data-ttu-id="851eb-404">Odpowiada operacji `fma` IEEE, wykonuje posmarowywany dodają mnożenie.</span><span class="sxs-lookup"><span data-stu-id="851eb-404">Corresponds to the `fma` IEEE operation, it performs a fused multiply add.</span></span> <span data-ttu-id="851eb-405">Oznacza to, `(x * y) + z` że robi to jako pojedyncza operacja, minimalizując w ten sposób błąd zaokrąglania.</span><span class="sxs-lookup"><span data-stu-id="851eb-405">That is, it does `(x * y) + z` as a single operation, thereby minimizing the rounding error.</span></span> <span data-ttu-id="851eb-406">Przykładem jest `FusedMultiplyAdd(1e308, 2.0, -1e308)`, `1e308`który zwraca .</span><span class="sxs-lookup"><span data-stu-id="851eb-406">An example is `FusedMultiplyAdd(1e308, 2.0, -1e308)`, which returns `1e308`.</span></span> <span data-ttu-id="851eb-407">Regularne `(1e308 * 2.0) - 1e308` zwroty `double.PositiveInfinity`.</span><span class="sxs-lookup"><span data-stu-id="851eb-407">The regular `(1e308 * 2.0) - 1e308` returns `double.PositiveInfinity`.</span></span>

- <xref:System.Math.CopySign(System.Double,System.Double)>\
<span data-ttu-id="851eb-408">Odpowiada operacji `copySign` IEEE, zwraca wartość `x`, ale ze znakiem `y`.</span><span class="sxs-lookup"><span data-stu-id="851eb-408">Corresponds to the `copySign` IEEE operation, it returns the value of `x`, but with the sign of `y`.</span></span>

### <a name="net-platform-dependent-intrinsics"></a><span data-ttu-id="851eb-409">Wewnętrzne elementy zależne od platformy .NET</span><span class="sxs-lookup"><span data-stu-id="851eb-409">.NET Platform-Dependent Intrinsics</span></span>

<span data-ttu-id="851eb-410">Dodano interfejsy API, które umożliwiają dostęp do niektórych instrukcji procesora cpu zorientowanych na perf, takich jak zestawy instrukcji **SIMD** lub **Bit Manipulation.**</span><span class="sxs-lookup"><span data-stu-id="851eb-410">APIs have been added that allow access to certain perf-oriented CPU instructions, such as the **SIMD** or **Bit Manipulation instruction** sets.</span></span> <span data-ttu-id="851eb-411">Te instrukcje mogą pomóc osiągnąć znaczną poprawę wydajności w niektórych scenariuszach, takich jak wydajne przetwarzanie danych równolegle.</span><span class="sxs-lookup"><span data-stu-id="851eb-411">These instructions can help achieve significant performance improvements in certain scenarios, such as processing data efficiently in parallel.</span></span>

<span data-ttu-id="851eb-412">W stosownych przypadkach biblioteki .NET zaczęły używać tych instrukcji w celu zwiększenia wydajności.</span><span class="sxs-lookup"><span data-stu-id="851eb-412">Where appropriate, the .NET libraries have begun using these instructions to improve performance.</span></span>

<span data-ttu-id="851eb-413">Aby uzyskać więcej informacji, zobacz [.NET Platform Dependent Intrinsics](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md).</span><span class="sxs-lookup"><span data-stu-id="851eb-413">For more information, see [.NET Platform Dependent Intrinsics](https://github.com/dotnet/designs/blob/master/accepted/platform-intrinsics.md).</span></span>

### <a name="improved-net-core-version-apis"></a><span data-ttu-id="851eb-414">Ulepszone interfejsy API wersji podstawowej .NET</span><span class="sxs-lookup"><span data-stu-id="851eb-414">Improved .NET Core Version APIs</span></span>

<span data-ttu-id="851eb-415">Począwszy od .NET Core 3.0, interfejsy API wersji dostarczane z .NET Core zwracają teraz informacje, których oczekujesz.</span><span class="sxs-lookup"><span data-stu-id="851eb-415">Starting with .NET Core 3.0, the version APIs provided with .NET Core now return the information you expect.</span></span> <span data-ttu-id="851eb-416">Przykład:</span><span class="sxs-lookup"><span data-stu-id="851eb-416">For example:</span></span>

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
> <span data-ttu-id="851eb-417">Przełomowa zmiana.</span><span class="sxs-lookup"><span data-stu-id="851eb-417">Breaking change.</span></span> <span data-ttu-id="851eb-418">Jest to technicznie przełomowa zmiana, ponieważ schemat wersji uległ zmianie.</span><span class="sxs-lookup"><span data-stu-id="851eb-418">This is technically a breaking change because the versioning scheme has changed.</span></span>

### <a name="fast-built-in-json-support"></a><span data-ttu-id="851eb-419">Szybka wbudowana obsługa JSON</span><span class="sxs-lookup"><span data-stu-id="851eb-419">Fast built-in JSON support</span></span>

<span data-ttu-id="851eb-420">Użytkownicy .NET w dużej mierze polegali na [Newtonsoft.Json](https://www.newtonsoft.com/json) i innych popularnych bibliotekach JSON, które nadal są dobrym wyborem.</span><span class="sxs-lookup"><span data-stu-id="851eb-420">.NET users have largely relied on [Newtonsoft.Json](https://www.newtonsoft.com/json) and other popular JSON libraries, which continue to be good choices.</span></span> <span data-ttu-id="851eb-421">`Newtonsoft.Json`używa ciągów .NET jako podstawowego typu danych, którym jest UTF-16 pod maską.</span><span class="sxs-lookup"><span data-stu-id="851eb-421">`Newtonsoft.Json` uses .NET strings as its base datatype, which is UTF-16 under the hood.</span></span>

<span data-ttu-id="851eb-422">Nowa wbudowana obsługa JSON jest wysoka wydajność, niska alokacja i współpracuje z UTF-8 zakodowany tekst JSON.</span><span class="sxs-lookup"><span data-stu-id="851eb-422">The new built-in JSON support is high-performance, low allocation, and works with UTF-8 encoded JSON text.</span></span> <span data-ttu-id="851eb-423">Aby uzyskać więcej <xref:System.Text.Json> informacji na temat obszaru nazw i typów, zobacz następujące artykuły:</span><span class="sxs-lookup"><span data-stu-id="851eb-423">For more information about the <xref:System.Text.Json> namespace and types, see the following articles:</span></span>

* [<span data-ttu-id="851eb-424">Serializacja JSON w .NET — omówienie</span><span class="sxs-lookup"><span data-stu-id="851eb-424">JSON serialization in .NET - overview</span></span>](../../standard/serialization/system-text-json-overview.md)
* <span data-ttu-id="851eb-425">[Jak serializować i deserializować JSON w .NET](../../standard/serialization/system-text-json-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="851eb-425">[How to serialize and deserialize JSON in .NET](../../standard/serialization/system-text-json-how-to.md).</span></span>
* [<span data-ttu-id="851eb-426">Jak przenieść z Newtonsoft.Json do System.Text.Json</span><span class="sxs-lookup"><span data-stu-id="851eb-426">How to migrate from Newtonsoft.Json to System.Text.Json</span></span>](../../standard/serialization/system-text-json-migrate-from-newtonsoft-how-to.md)

### <a name="http2-support"></a><span data-ttu-id="851eb-427">Obsługa protokołu HTTP/2</span><span class="sxs-lookup"><span data-stu-id="851eb-427">HTTP/2 support</span></span>

<span data-ttu-id="851eb-428">Typ <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> obsługuje protokół HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="851eb-428">The <xref:System.Net.Http.HttpClient?displayProperty=nameWithType> type supports the HTTP/2 protocol.</span></span> <span data-ttu-id="851eb-429">Jeśli protokół HTTP/2 jest włączony, wersja protokołu HTTP jest negocjowana za pośrednictwem protokołu TLS/ALPN, a protokół HTTP/2 jest używany, jeśli serwer zdecyduje się z niej korzystać.</span><span class="sxs-lookup"><span data-stu-id="851eb-429">If HTTP/2 is enabled, the HTTP protocol version is negotiated via TLS/ALPN, and HTTP/2 is used if the server elects to use it.</span></span>

<span data-ttu-id="851eb-430">Domyślnym protokołem pozostaje HTTP/1.1, ale protokół HTTP/2 można włączyć na dwa różne sposoby.</span><span class="sxs-lookup"><span data-stu-id="851eb-430">The default protocol remains HTTP/1.1, but HTTP/2 can be enabled in two different ways.</span></span> <span data-ttu-id="851eb-431">Najpierw można ustawić komunikat żądania HTTP, aby użyć protokołu HTTP/2:</span><span class="sxs-lookup"><span data-stu-id="851eb-431">First, you can set the HTTP request message to use HTTP/2:</span></span>

[!code-csharp[Http2Request](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Request)]

<span data-ttu-id="851eb-432">Po drugie, <xref:System.Net.Http.HttpClient> domyślnie można zmienić sposób używania protokołu HTTP/2:</span><span class="sxs-lookup"><span data-stu-id="851eb-432">Second, you can change <xref:System.Net.Http.HttpClient> to use HTTP/2 by default:</span></span>

[!code-csharp[Http2Client](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#Client)]

<span data-ttu-id="851eb-433">Wiele razy podczas tworzenia aplikacji, chcesz użyć połączenia niezaszyfrowanego.</span><span class="sxs-lookup"><span data-stu-id="851eb-433">Many times when you're developing an application, you want to use an unencrypted connection.</span></span> <span data-ttu-id="851eb-434">Jeśli wiesz, że docelowy punkt końcowy będzie używał protokołu HTTP/2, możesz włączyć połączenia niezaszyfrowane dla protokołu HTTP/2.</span><span class="sxs-lookup"><span data-stu-id="851eb-434">If you know the target endpoint will be using HTTP/2, you can turn on unencrypted connections for HTTP/2.</span></span> <span data-ttu-id="851eb-435">Można go włączyć, ustawiając zmienną środowiskową `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT` `1` lub włączając ją w kontekście aplikacji:</span><span class="sxs-lookup"><span data-stu-id="851eb-435">You can turn it on by setting the `DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT` environment variable to `1` or by enabling it in the app context:</span></span>

[!code-csharp[Http2Context](~/samples/snippets/core/whats-new/whats-new-in-30/cs/http.cs#AppContext)]

## <a name="next-steps"></a><span data-ttu-id="851eb-436">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="851eb-436">Next steps</span></span>

- [<span data-ttu-id="851eb-437">Przejrzyj zmiany dotyczące podziału między programami .NET Core 2.2 i 3.0.</span><span class="sxs-lookup"><span data-stu-id="851eb-437">Review the breaking changes between .NET Core 2.2 and 3.0.</span></span>](../compatibility/2.2-3.0.md)
- [<span data-ttu-id="851eb-438">Przejrzyj zmiany dotyczące łamania zasad w aplikacji .NET Core 3.0 dla formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="851eb-438">Review the breaking changes in .NET Core 3.0 for Windows Forms apps.</span></span>](../compatibility/winforms.md#net-core-30)

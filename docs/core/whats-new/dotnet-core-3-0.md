---
title: What's new in .NET Core 3.0
description: Dowiedz się więcej o nowych funkcjach w programie .NET Core 3.0.
dev_langs:
- csharp
- vb
author: thraka
ms.author: adegeo
ms.date: 12/04/2018
ms.openlocfilehash: 3ca833031eb8bb0f43a334f833f2e0075842d57d
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53155481"
---
# <a name="whats-new-in-net-core-30-preview-1"></a><span data-ttu-id="fd1ca-103">What's new in .NET Core 3.0 (wersja zapoznawcza 1)</span><span class="sxs-lookup"><span data-stu-id="fd1ca-103">What's new in .NET Core 3.0 (Preview 1)</span></span>

<span data-ttu-id="fd1ca-104">W tym artykule opisano nowości w programie .NET Core 3.0 (wersja zapoznawcza 1).</span><span class="sxs-lookup"><span data-stu-id="fd1ca-104">This article describes what is new in .NET Core 3.0 (preview 1).</span></span> <span data-ttu-id="fd1ca-105">Jedną z największych ulepszenia to obsługa aplikacji klasycznych Windows (tylko Windows).</span><span class="sxs-lookup"><span data-stu-id="fd1ca-105">One of the biggest enhancements is support for Windows desktop applications (Windows only).</span></span> <span data-ttu-id="fd1ca-106">Przy użyciu platformy .NET Core 3.0 to składnik o nazwie Windows Desktop, można przenosić aplikacje Windows Forms Windows Presentation Foundation (WPF).</span><span class="sxs-lookup"><span data-stu-id="fd1ca-106">By utilizing a .NET Core 3.0 component called Windows Desktop, you can port your Windows Forms Windows Presentation Foundation (WPF) applications.</span></span> <span data-ttu-id="fd1ca-107">Aby być niejasne, składnik Windows Desktop jest obsługiwana tylko na Windows.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-107">To be clear, the Windows Desktop component is only supported on Windows.</span></span> <span data-ttu-id="fd1ca-108">Aby uzyskać więcej informacji, zobacz sekcję [pulpitu Windows](#windows-desktop) poniżej.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-108">For more information, see the section [Windows desktop](#windows-desktop) below.</span></span>

<span data-ttu-id="fd1ca-109">.NET core 3.0 dodaje obsługę C# 8.0.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-109">.NET Core 3.0 adds support for C# 8.0.</span></span>

<span data-ttu-id="fd1ca-110">[Pobierz i rozpoczynanie pracy z usługą .NET Core 3 (wersja zapoznawcza) 1](https://aka.ms/netcore3download) teraz na Windows, Mac i Linux.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-110">[Download and get started with .NET Core 3 Preview 1](https://aka.ms/netcore3download) right now on Windows, Mac and Linux.</span></span> <span data-ttu-id="fd1ca-111">Można wyświetlić szczegółowe informacje o wersji w [informacje o wersji platformy .NET Core 3 (wersja zapoznawcza) 1](https://aka.ms/netcore3releasenotes).</span><span class="sxs-lookup"><span data-stu-id="fd1ca-111">You can see complete details of the release in the [.NET Core 3 Preview 1 release notes](https://aka.ms/netcore3releasenotes).</span></span>

<span data-ttu-id="fd1ca-112">Aby uzyskać więcej informacji, zobacz [ogłoszenie .NET Core 3.0 w wersji zapoznawczej 1](https://blogs.msdn.microsoft.com/dotnet/2018/12/04/announcing-net-core-3-preview-1-and-open-sourcing-windows-desktop-frameworks/).</span><span class="sxs-lookup"><span data-stu-id="fd1ca-112">For more information, see the [.NET Core 3.0 Preview 1 announcement](https://blogs.msdn.microsoft.com/dotnet/2018/12/04/announcing-net-core-3-preview-1-and-open-sourcing-windows-desktop-frameworks/).</span></span>

## <a name="net-standard-21"></a><span data-ttu-id="fd1ca-113">.NET standard 2.1</span><span class="sxs-lookup"><span data-stu-id="fd1ca-113">.NET Standard 2.1</span></span>

<span data-ttu-id="fd1ca-114">.NET core 3.0 implementuje platformy .NET Standard 2.1.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-114">.NET Core 3.0 implements .NET Standard 2.1.</span></span>

## <a name="default-executables"></a><span data-ttu-id="fd1ca-115">Domyślne pliki wykonywalne</span><span class="sxs-lookup"><span data-stu-id="fd1ca-115">Default executables</span></span>

<span data-ttu-id="fd1ca-116">.NET core będzie teraz tworzyć pliki wykonywalne domyślnie.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-116">.NET Core will now build executables by default.</span></span> <span data-ttu-id="fd1ca-117">Jest to nowość w aplikacji, które używają globalnie zainstalowaną wersję platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-117">This is new for applications that use a globally installed version of .NET Core.</span></span> <span data-ttu-id="fd1ca-118">Do tej pory tylko [niezależna wdrożeń](../deploying/index.md#self-contained-deployments-scd) miał plików wykonywalnych.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-118">Until now, only [self-contained deployments](../deploying/index.md#self-contained-deployments-scd) had executables.</span></span>

<span data-ttu-id="fd1ca-119">Podczas `dotnet build` lub `dotnet publish`, plik wykonywalny jest tworzony, pod warunkiem, które odpowiadają środowisko i platforma używasz zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-119">During `dotnet build` or `dotnet publish`, an executable is created provided that matches the environment and platform of the SDK you are using.</span></span> <span data-ttu-id="fd1ca-120">Mogą spodziewać się tego samego rzeczy, korzystając z tych plików wykonywalnych, tak jak w innych natywnych plików wykonywalnych, takich jak:</span><span class="sxs-lookup"><span data-stu-id="fd1ca-120">You can expect the same things with these executables as you would other native executables, such as:</span></span>

* <span data-ttu-id="fd1ca-121">Możesz kliknąć dwukrotnie plik wykonywalny.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-121">You can double-click on the executable.</span></span>
* <span data-ttu-id="fd1ca-122">Można uruchomić aplikacji z poziomu wiersza polecenia, takie jak `myapp.exe` na Windows, i `./myapp` w systemie Linux i macOS.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-122">You can launch the application from a command prompt directly, such as `myapp.exe` on Windows, and `./myapp` on Linux and macOS.</span></span>

> [!NOTE]
> <span data-ttu-id="fd1ca-123">Określanie określonego środowiska uruchomieniowego za pomocą `dotnet publish -r` lub `dotnet build -r` argumentów w innych środowiskach środowisko uruchomieniowe nie jest obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-123">Specifying a specific runtime with `dotnet publish -r` or `dotnet build -r` arguments for other runtime environments isn't supported.</span></span>

## <a name="build-copies-dependencies"></a><span data-ttu-id="fd1ca-124">Kopiuje zależności kompilacji</span><span class="sxs-lookup"><span data-stu-id="fd1ca-124">Build copies dependencies</span></span>

<span data-ttu-id="fd1ca-125">`dotnet build` teraz kopiuje zależności NuGet dla aplikacji z pamięcią podręczną programu NuGet do folderu wyjściowego kompilacji.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-125">`dotnet build` now copies NuGet dependencies for your application from the NuGet cache to the build output folder.</span></span> <span data-ttu-id="fd1ca-126">Wcześniej zależności zostały skopiowane tylko jako część `dotnet publish`.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-126">Previously, dependencies were only copied as part of `dotnet publish`.</span></span> 

<span data-ttu-id="fd1ca-127">Istnieją pewne operacje takie jak łączenie i razor strony publikowania, który nadal będzie wymagać publikowania.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-127">There are some operations, like linking and razor page publishing that will still require publishing.</span></span>


## <a name="local-dotnet-tools"></a><span data-ttu-id="fd1ca-128">Narzędzia do lokalnego dotnet</span><span class="sxs-lookup"><span data-stu-id="fd1ca-128">Local dotnet tools</span></span>

<span data-ttu-id="fd1ca-129">.NET Core 2.1 obsługiwana globalnego narzędzia, .NET Core 3.0 to ma teraz lokalne narzędzia.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-129">While .NET Core 2.1 supported global tools, .NET Core 3.0 now has local tools.</span></span> <span data-ttu-id="fd1ca-130">Lokalne narzędzia są podobne do narzędzia globalnych, ale są skojarzone z określonej lokalizacji na dysku.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-130">Local tools are similar to global tools but are associated with a particular location on disk.</span></span> <span data-ttu-id="fd1ca-131">Dzięki temu projektów i narzędzi na repozytorium.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-131">This enables per-project and per-repository tooling.</span></span> <span data-ttu-id="fd1ca-132">Wszystkie zainstalowane lokalnie narzędzie nie jest globalnie dostępna.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-132">Any tool installed locally isn't available globally.</span></span>

<span data-ttu-id="fd1ca-133">Lokalne narzędzia opierają się na nazwę pliku manifestu `dotnet-tools.json` w bieżącym katalogu.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-133">Local tools rely on a manifest file name `dotnet-tools.json` in your current directory.</span></span> <span data-ttu-id="fd1ca-134">Ten plik manifestu definiuje narzędzia, które mają być dostępne.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-134">This manifest file defines the tools to be available.</span></span> <span data-ttu-id="fd1ca-135">Ten plik manifestu są tworzone w katalogu głównym repozytorium, możesz upewnij się, każdy klonowania kodu można przywrócić i korzystania z narzędzi, które są niezbędne do pomyślnie pracę z kodem.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-135">By creating this manifest file at the root of your repository, you ensure anyone cloning your code can restore and use the tools that are needed to successfully work with your code.</span></span>

<span data-ttu-id="fd1ca-136">Po udostępnieniu pliku manifestu lokalne narzędzia, użyj następującego polecenia do automatycznego pobierania i instalowania tych narzędzi lokalnie:</span><span class="sxs-lookup"><span data-stu-id="fd1ca-136">When the local tools manifest file is available, use the following command to automatically download and install those tools locally:</span></span>

```console
dotnet tool restore
```

<span data-ttu-id="fd1ca-137">Uruchom narzędzie lokalnych za pomocą następującego polecenia:</span><span class="sxs-lookup"><span data-stu-id="fd1ca-137">Run a local tool with the following command:</span></span>

```console
dotnet tool run <tool-command-name>
```

<span data-ttu-id="fd1ca-138">Po wywołaniu lokalne narzędzie dotnet wyszukuje manifest się struktury katalogów.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-138">When a local tool is called, dotnet searches for a manifest up the directory structure.</span></span> <span data-ttu-id="fd1ca-139">W przypadku odnalezienia pliku manifestu narzędzie przeszukiwany jest dla żądanego narzędzia.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-139">When a tool manifest file is found, it is searched for the requested tool.</span></span> <span data-ttu-id="fd1ca-140">Jeśli narzędzie zostanie znaleziony, zawiera informacje dotyczące znajdowania narzędzia w lokalizacji globalnymi pakietami NuGet.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-140">If the tool is found, it includes the information needed to find the tool in the NuGet global packages location.</span></span> 

<span data-ttu-id="fd1ca-141">Jeśli narzędzie zostanie znaleziony w manifeście, ale nie pamięci podręcznej, zostanie wyświetlony błąd.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-141">If the tool is found in the manifest, but not the cache, the user receives an error.</span></span> <span data-ttu-id="fd1ca-142">Zostanie on ulepszony komunikat po 1 (wersja zapoznawcza), aby poprosić użytkownika Uruchom `dotnet tool restore`.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-142">The message will be improved after Preview 1 to request the user run `dotnet tool restore`.</span></span>

<span data-ttu-id="fd1ca-143">Dodawanie lokalnych narzędzi do katalogu, należy najpierw utworzyć plik manifestu narzędzia.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-143">To add local tools to a directory, you need to first create the tool manifest file.</span></span> <span data-ttu-id="fd1ca-144">Po 1 (wersja zapoznawcza) oferujemy mechanizm służący do tworzenia plików manifestu, takie jak nowy szablon dotnet narzędzia.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-144">After Preview 1, we will offer a mechanism for creating tool manifest files, such as a dotnet new template.</span></span> <span data-ttu-id="fd1ca-145">W przypadku 1 (wersja zapoznawcza), musisz utworzyć plik o nazwie `dotnet-tools.json` z następującą zawartością:</span><span class="sxs-lookup"><span data-stu-id="fd1ca-145">For Preview 1 you must create the file named `dotnet-tools.json` with the following contents:</span></span>

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {}
}
```

<span data-ttu-id="fd1ca-146">Po utworzeniu manifestu, lokalnego narzędzia można dodać do niego przy użyciu:</span><span class="sxs-lookup"><span data-stu-id="fd1ca-146">Once the manifest is created, you can add local tools to it using:</span></span>

```console
dotnet tool install <toolPackageId>
```

<span data-ttu-id="fd1ca-147">To polecenie instaluje najnowszą wersję narzędzia, chyba że określono inną wersję.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-147">This command installs the latest version of the tool, unless another version is specified.</span></span>  <span data-ttu-id="fd1ca-148">Nawet jeśli automatycznie wybrano najnowszą wersję, wersję narzędzia są zapisywane w pliku manifestu narzędzia, aby umożliwić poprawną wersję narzędzia go przywrócić lub uruchom.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-148">Even if the latest version was automatically chosen, the version of the tool is written into the tool manifest file to allow the correct version of the tool to be restored or run.</span></span>

<span data-ttu-id="fd1ca-149">Plik manifestu narzędzia zaprojektowano w celu Zezwól na edytowanie strony — co może zrobić, aby zaktualizować wersję wymagane do pracy z repozytorium.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-149">The tool manifest file is designed to allow hand editing – which you might do to update the required version for working with the repository.</span></span>

<span data-ttu-id="fd1ca-150">Oto przykład `dotnet-tools.json` pliku:</span><span class="sxs-lookup"><span data-stu-id="fd1ca-150">Here is an example `dotnet-tools.json` file:</span></span>

```json
{
  "version": 1,
  "isRoot": true,
  "tools": {
    "dotnetsay": {
      "version": "2.1.4",
      "commands": [
        "dotnetsay"
      ]
    },
    "t-rex": {
      "version": "1.0.103",
      "commands": [
        "t-rex"
      ]
    }
  }
}
```

<span data-ttu-id="fd1ca-151">Aby usunąć narzędzie z pliku manifestu narzędzia, uruchom następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="fd1ca-151">To remove a tool from the tool manifest file, run the following command:</span></span>

```console
dotnet tool uninstall <toolPackageId>
```

<span data-ttu-id="fd1ca-152">Globalne i lokalne narzędzi zgodna wersja środowiska uruchomieniowego jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-152">For both global and local tools, a compatible version of the runtime is required.</span></span> <span data-ttu-id="fd1ca-153">Wiele narzędzi, obecnie w witrynie NuGet.org docelowej platformy .NET Core środowiska uruchomieniowego 2.1.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-153">Many tools currently on NuGet.org target .NET Core Runtime 2.1.</span></span> <span data-ttu-id="fd1ca-154">Aby zainstalować te globalnie lub lokalnie, czy nadal należy zainstalować [środowisko uruchomieniowe programu NET Core 2.1](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span><span class="sxs-lookup"><span data-stu-id="fd1ca-154">To install those globally or locally, you would still need to install the [NET Core 2.1 Runtime](https://dotnet.microsoft.com/download/dotnet-core/2.1).</span></span>

<span data-ttu-id="fd1ca-155">Aby uzyskać więcej informacji, zobacz [lokalne narzędzia wczesne dokumentacja w wersji zapoznawczej](https://github.com/dotnet/cli/issues/10288).</span><span class="sxs-lookup"><span data-stu-id="fd1ca-155">For more information, see [Local Tools Early Preview Documentation](https://github.com/dotnet/cli/issues/10288).</span></span>

## <a name="windows-desktop"></a><span data-ttu-id="fd1ca-156">Pulpit systemu Windows</span><span class="sxs-lookup"><span data-stu-id="fd1ca-156">Windows desktop</span></span>

<span data-ttu-id="fd1ca-157">Począwszy od programu .NET Core 3.0 w wersji zapoznawczej 1, możesz tworzyć aplikacje pulpitu Windows przy użyciu WPF i Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-157">Starting with .NET Core 3.0 Preview 1, you can build Windows desktop applications using WPF and Windows Forms.</span></span> <span data-ttu-id="fd1ca-158">Następujące struktury obsługi, za pomocą nowoczesnych kontrolek i Fluent stylów z biblioteki XAML interfejsu użytkownika systemu Windows (WinUI) za pośrednictwem [Wyspy XAML](/windows/uwp/xaml-platform/xaml-host-controls).</span><span class="sxs-lookup"><span data-stu-id="fd1ca-158">These frameworks also support using modern controls and Fluent styling from the Windows UI XAML Library (WinUI) via [XAML islands](/windows/uwp/xaml-platform/xaml-host-controls).</span></span>

<span data-ttu-id="fd1ca-159">Składnik Windows Desktop jest częścią Windows zestaw SDK programu .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-159">The Windows Desktop component is part of the Windows .NET Core 3.0 SDK.</span></span>

<span data-ttu-id="fd1ca-160">Można utworzyć nowej aplikacji WPF i Windows Forms z następującymi `dotnet` poleceń:</span><span class="sxs-lookup"><span data-stu-id="fd1ca-160">You can create a new WPF or Windows Forms app with the following `dotnet` commands:</span></span>

```console
dotnet new wpf
dotnet new winforms
```

<span data-ttu-id="fd1ca-161">Można również otworzyć, uruchomić i debugowania projektów .NET Core 3.0 WPF i Windows Forms w programie Visual Studio 2019 r w wersji zapoznawczej 1.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-161">You can also open, launch, and debug .NET Core 3.0 WPF and Windows Forms projects in Visual Studio 2019 Preview 1.</span></span> <span data-ttu-id="fd1ca-162">Obecnie można otwierać te projekty w programie Visual Studio 2017 15.9, jednak nie jest obsługiwanym scenariuszem (i należy [Włącz podglądy](https://blogs.msdn.microsoft.com/dotnet/2018/11/13/net-core-tooling-update-for-visual-studio-2017-version-15-9/)).</span><span class="sxs-lookup"><span data-stu-id="fd1ca-162">It's currently possible to open these projects in Visual Studio 2017 15.9, however, it isn't a supported scenario (and you need to [enable previews](https://blogs.msdn.microsoft.com/dotnet/2018/11/13/net-core-tooling-update-for-visual-studio-2017-version-15-9/)).</span></span>

<span data-ttu-id="fd1ca-163">Nowe projekty są takie same jak istniejących projektów .NET Core z dodatkami kilka.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-163">The new projects are the same as existing .NET Core projects, with a couple additions.</span></span> <span data-ttu-id="fd1ca-164">Oto porównanie podstawowy projekt konsoli .NET Core i podstawowy projekt Windows Forms i WPF.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-164">Here is the comparison of the basic .NET Core console project and a basic Windows Forms and WPF project.</span></span>

<span data-ttu-id="fd1ca-165">W projekcie konsoli .NET Core, projekt korzysta z `Microsoft.NET.Sdk` zestawu SDK ale deklaruje zależności na .NET Core 3.0 to za pośrednictwem `netcoreapp3.0` platformy docelowej.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-165">In a .NET Core console project, the project uses the `Microsoft.NET.Sdk` SDK and declares a dependency on .NET Core 3.0 via the `netcoreapp3.0` target framework.</span></span> <span data-ttu-id="fd1ca-166">Aby utworzyć aplikację pulpitu Windows, należy użyć `Microsoft.NET.Sdk.WindowsDesktop` zestawu SDK i wybierz polecenie struktury interfejsu użytkownika, których można użyć:</span><span class="sxs-lookup"><span data-stu-id="fd1ca-166">To create a Windows Desktop app, use the `Microsoft.NET.Sdk.WindowsDesktop` SDK and choose which UI framework to use:</span></span>

```diff
-<Project Sdk="Microsoft.NET.Sdk">
+<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
+   <UseWPF>true</UseWPF>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="fd1ca-167">Aby wybrać Windows Forms w WPF, należy ustawić `UseWindowsForms` zamiast `UseWPF`:</span><span class="sxs-lookup"><span data-stu-id="fd1ca-167">To choose Windows Forms over WPF, set `UseWindowsForms` instead of `UseWPF`:</span></span>

```diff
<Project Sdk="Microsoft.NET.Sdk.WindowsDesktop">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp3.0</TargetFramework>
-   <UseWPF>true</UseWPF>
+   <UseWindowsForms>true</UseWindowsForms>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="fd1ca-168">Zarówno `UseWPF` i `UseWindowsForms` można ustawić `true` Jeśli aplikacja korzysta z obu platform, na przykład gdy okno dialogowe Windows Forms jest hosting kontrolki WPF.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-168">Both `UseWPF` and `UseWindowsForms` can be set to `true` if the app uses both frameworks, for example when a Windows Forms dialog is hosting a WPF control.</span></span>

<span data-ttu-id="fd1ca-169">Podziel się swoją opinię na [dotnet/winforms](https://github.com/dotnet/winforms/issues), [dotnet/wpf](https://github.com/dotnet/wpf/issues) i [dotnet/core](https://github.com/dotnet/core/issues) repozytoriów.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-169">Please share your feedback on the [dotnet/winforms](https://github.com/dotnet/winforms/issues),  [dotnet/wpf](https://github.com/dotnet/wpf/issues) and [dotnet/core](https://github.com/dotnet/core/issues) repos.</span></span>

## <a name="fast-built-in-json-support"></a><span data-ttu-id="fd1ca-170">Szybkie wbudowanej obsługi formatu JSON</span><span class="sxs-lookup"><span data-stu-id="fd1ca-170">Fast built-in JSON support</span></span>

<span data-ttu-id="fd1ca-171">`System.Text.Json.Utf8JsonReader` jest o wysokiej wydajności, niski alokacji, tylko do przodu czytnik UTF-8 kodowany w formacie JSON tekst odczytywane `ReadOnlySpan<byte>`.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-171">`System.Text.Json.Utf8JsonReader` is a high-performance, low allocation, forward-only reader for UTF-8 encoded JSON text, read from a `ReadOnlySpan<byte>`.</span></span> <span data-ttu-id="fd1ca-172">`Utf8JsonReader` Jest typem podstawowe, niskiego poziomu, który można wykorzystać do tworzenia niestandardowych analizatory i deserializers.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-172">The `Utf8JsonReader` is a foundational, low-level type, that can be leveraged to build custom parsers and deserializers.</span></span> <span data-ttu-id="fd1ca-173">Odczytywanie za pośrednictwem ładunek w formacie JSON za pomocą nowego `Utf8JsonReader` wynosi 2 x szybciej niż przy użyciu czytnika, z [Json.NET](https://www.newtonsoft.com/json).</span><span class="sxs-lookup"><span data-stu-id="fd1ca-173">Reading through a JSON payload using the new `Utf8JsonReader` is 2x faster than using the reader from [Json.NET](https://www.newtonsoft.com/json).</span></span> <span data-ttu-id="fd1ca-174">Nie przydziela do czasu konieczne actualize tokenów JSON jako ciągi (UTF-16).</span><span class="sxs-lookup"><span data-stu-id="fd1ca-174">It does not allocate until you need to actualize JSON tokens as (UTF-16) strings.</span></span>

<span data-ttu-id="fd1ca-175">Ten nowy interfejs API obejmuje następujące składniki:</span><span class="sxs-lookup"><span data-stu-id="fd1ca-175">This new API will include the following components:</span></span>

* <span data-ttu-id="fd1ca-176">W wersji zapoznawczej 1: Czytnik JSON (dostępu sekwencyjnego)</span><span class="sxs-lookup"><span data-stu-id="fd1ca-176">In Preview 1: JSON reader (sequential access)</span></span>
* <span data-ttu-id="fd1ca-177">Dodana w następnej kolejności: Moduł zapisujący JSON, modelu DOM (dostępu swobodnego) obiektów poco elementu serializującego obiektów poco Deserializator</span><span class="sxs-lookup"><span data-stu-id="fd1ca-177">Coming next: JSON writer, DOM (random access), poco serializer, poco deserializer</span></span>

<span data-ttu-id="fd1ca-178">Oto pętli czytnika podstawowego `Utf8JsonReader` mogą służyć jako punkt początkowy:</span><span class="sxs-lookup"><span data-stu-id="fd1ca-178">Here is the basic reader loop for the `Utf8JsonReader` that can be used as a starting point:</span></span>

```csharp
using System.Text.Json;

public static void Utf8JsonReaderLoop(ReadOnlySpan<byte> dataUtf8)
{
    var json = new Utf8JsonReader(dataUtf8, isFinalBlock: true, state: default);

    while (json.Read())
    {
        JsonTokenType tokenType = json.TokenType;
        ReadOnlySpan<byte> valueSpan = json.ValueSpan;
        switch (tokenType)
        {
            case JsonTokenType.StartObject:
            case JsonTokenType.EndObject:
                break;
            case JsonTokenType.StartArray:
            case JsonTokenType.EndArray:
                break;
            case JsonTokenType.PropertyName:
                break;
            case JsonTokenType.String:
                string valueString = json.GetStringValue();
                break;
            case JsonTokenType.Number:
                if (!json.TryGetInt32Value(out int valueInteger))
                {
                    throw new FormatException();
                }
                break;
            case JsonTokenType.True:
            case JsonTokenType.False:
                bool valueBool = json.GetBooleanValue();
                break;
            case JsonTokenType.Null:
                break;
            default:
                throw new ArgumentException();
        }
    }

    dataUtf8 = dataUtf8.Slice((int)json.BytesConsumed);
    JsonReaderState state = json.CurrentState;
}
```

<span data-ttu-id="fd1ca-179">Ekosystemu .NET opierało się na [Json.NET](https://www.newtonsoft.com/json) i innych popularnych bibliotek JSON, które nadal dobrych wyborów.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-179">The .NET ecosystem has relied on [Json.NET](https://www.newtonsoft.com/json) and other popular JSON libraries, which continue to be good choices.</span></span> <span data-ttu-id="fd1ca-180">Program JSON.NET używa ciągów .NET jako jego podstawowy datatype kulisy używanej na UTF-16.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-180">JSON.NET uses .NET strings as its base datatype, which are UTF-16 under the hood.</span></span> 

<span data-ttu-id="fd1ca-181">W programie .NET Core 2.1 i 3.0, dodaliśmy nowe interfejsy API, który sprawia, że można pisać interfejsy API w formacie JSON (takich jak `Utf8JsonReader`) wymagających znacznie mniej pamięci, oparte na użyciu `Span<T>` i ciągi znaków UTF-8 i lepsze potrzebami aplikacji o wysokiej przepływności, takich jak Kestrel, ASP. Serwer sieci web .NET Core.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-181">In .NET Core 2.1 and 3.0, we added new APIs that makes it possible to write JSON APIs (such as `Utf8JsonReader`) that require much less memory, based on using `Span<T>` and UTF-8 strings, and better serve the needs of high-throughput applications like Kestrel, ASP.NET Core web server.</span></span>

## <a name="ranges-and-indices"></a><span data-ttu-id="fd1ca-182">Zakresy i indeksy</span><span class="sxs-lookup"><span data-stu-id="fd1ca-182">Ranges and indices</span></span>

<span data-ttu-id="fd1ca-183">Nowy `Index` typ może być używany do indeksowania.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-183">The new `Index` type can be used for indexing.</span></span> <span data-ttu-id="fd1ca-184">Można utworzyć jeden z `int` , jest liczona od początku lub z prefiksem `^` — operator (C#), jest liczona od końca:</span><span class="sxs-lookup"><span data-stu-id="fd1ca-184">You can create one from an `int` that counts from the beginning, or with a prefix `^` operator (C#) that counts from the end:</span></span>

```csharp
Index i1 = 3;  // number 3 from beginning
Index i2 = ^4; // number 4 from end
int[] a = { 0, 1, 2, 3, 4, 5, 6, 7, 8, 9 };
Console.WriteLine($"{a[i1]}, {a[i2]}"); // "3, 6"
```

<span data-ttu-id="fd1ca-185">Istnieje również `Range` typ, który składa się z dwóch `Index` wartości, jeden dla początkowego i jeden dla elementu end i mogą być zapisywane z `x..y` zakres wyrażenia (C#).</span><span class="sxs-lookup"><span data-stu-id="fd1ca-185">There is also a `Range` type, which consists of two `Index` values, one for the start and one for the end, and can be written with a `x..y` range expression (C#).</span></span> <span data-ttu-id="fd1ca-186">Następnie można zaindeksować z `Range` w celu tworzenia wycinka:</span><span class="sxs-lookup"><span data-stu-id="fd1ca-186">You can then index with a `Range` in order to produce a slice:</span></span>

```csharp
var slice = a[i1..i2]; // { 3, 4, 5 }
```

> [!NOTE]
> <span data-ttu-id="fd1ca-187">Tylko [ C# 8.0](https://blogs.msdn.microsoft.com/dotnet/2018/11/12/building-c-8-0/) obsługuje składnię `Range` i `Index`.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-187">Only [C# 8.0](https://blogs.msdn.microsoft.com/dotnet/2018/11/12/building-c-8-0/) supports syntax for `Range` and `Index`.</span></span>

## <a name="async-streams"></a><span data-ttu-id="fd1ca-188">Asynchroniczne strumienie</span><span class="sxs-lookup"><span data-stu-id="fd1ca-188">Async streams</span></span>

<span data-ttu-id="fd1ca-189">`IAsyncEnumerable<T>` Typu jest nowa wersja asynchroniczne `IEnumerable<T>`.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-189">The `IAsyncEnumerable<T>` type is a new asynchronous version of `IEnumerable<T>`.</span></span> <span data-ttu-id="fd1ca-190">Język umożliwia `await foreach` za pośrednictwem tych zasobów w celu korzystania z ich elementów i `yield return` do ich do produkcji elementów.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-190">The language lets you `await foreach` over these to consume their elements, and `yield return` to them to produce elements.</span></span>

<span data-ttu-id="fd1ca-191">Poniższy przykład ilustruje środowiska produkcyjnego i zużycia strumieni asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-191">The following example demonstrates both production and consumption of async streams.</span></span> <span data-ttu-id="fd1ca-192">`foreach` Instrukcja jest asynchroniczne, a sam używa `yield return` do produkcji strumienia asynchronicznego dla obiektów wywołujących.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-192">The `foreach` statement is async and itself uses `yield return` to produce an async stream for callers.</span></span> <span data-ttu-id="fd1ca-193">Ten wzorzec (przy użyciu `yield return`) to zalecany model do produkcji strumieni asynchronicznych.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-193">This pattern (using `yield return`) is the recommended model for producing async streams.</span></span>

```csharp
async IAsyncEnumerable<int> GetBigResultsAsync()
{
    await foreach (var result in GetResultsAsync())
    {
        if (result > 20) yield return result; 
    }
}
```

> [!WARNING]
> <span data-ttu-id="fd1ca-194">.NET core 3.0 w wersji zapoznawczej 1 ma obecnie usterki, przy użyciu `await foreach`.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-194">.NET Core 3.0 Preview 1 currently has a bug with `await foreach`.</span></span> <span data-ttu-id="fd1ca-195">Zamiast tego należy użyć `GetEnumerator` i `MoveNext` elementy procesu.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-195">Instead, use `GetEnumerator` and `MoveNext` to process elements.</span></span> <span data-ttu-id="fd1ca-196">Aby uzyskać więcej informacji, zobacz [roslyn / #31268](https://github.com/dotnet/roslyn/issues/31268).</span><span class="sxs-lookup"><span data-stu-id="fd1ca-196">For more information, see [roslyn/#31268](https://github.com/dotnet/roslyn/issues/31268).</span></span>

<span data-ttu-id="fd1ca-197">Oprócz możliwości `await foreach`, można również utworzyć async Iteratory, na przykład iterator, który zwraca `IAsyncEnumerable/IAsyncEnumerator` można zarówno `await` i `yield` w.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-197">In addition to being able to `await foreach`, you can also create async iterators, for example, an iterator that returns an `IAsyncEnumerable/IAsyncEnumerator` that you can both `await` and `yield` in.</span></span> <span data-ttu-id="fd1ca-198">W przypadku obiektów, które muszą zostać zlikwidowany, można użyć `IAsyncDisposable`, który implementuje różnych typów BCL, takich jak `Stream` i `Timer`.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-198">For objects that need to be disposed, you can use `IAsyncDisposable`, which various BCL types implement, such as `Stream` and `Timer`.</span></span>

> [!NOTE]
> <span data-ttu-id="fd1ca-199">Tylko [ C# 8.0](https://blogs.msdn.microsoft.com/dotnet/2018/11/12/building-c-8-0/) obsługuje `await foreach` składni.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-199">Only [C# 8.0](https://blogs.msdn.microsoft.com/dotnet/2018/11/12/building-c-8-0/) supports `await foreach` syntax.</span></span>

## <a name="type-sequencereader"></a><span data-ttu-id="fd1ca-200">Wpisz: SequenceReader</span><span class="sxs-lookup"><span data-stu-id="fd1ca-200">Type: SequenceReader</span></span>

<span data-ttu-id="fd1ca-201">W programie .NET Core 3.0 `System.Buffers.SequenceReader` dodano, który może służyć jako czytnik `ReadOnlySequence<T>`.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-201">In .NET Core 3.0, `System.Buffers.SequenceReader` has been added which can be used as a reader for `ReadOnlySequence<T>`.</span></span> <span data-ttu-id="fd1ca-202">Umożliwia to łatwe w użyciu o wysokiej wydajności, niski alokacji analizowanie `System.IO.Pipelines` dane, które mogą przechodzić przez kilka buforów zapasowy.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-202">This allows easy, high performance, low allocation parsing of `System.IO.Pipelines` data that can cross multiple backing buffers.</span></span> 

<span data-ttu-id="fd1ca-203">Poniższy przykład dzieli dane wejściowe `Sequence` na prawidłowe `CR/LF` rozdzielonych wiersze:</span><span class="sxs-lookup"><span data-stu-id="fd1ca-203">The following example breaks an input `Sequence` into valid `CR/LF` delimited lines:</span></span>

```csharp
private static ReadOnlySpan<byte> CRLF => new byte[] { (byte)'\r', (byte)'\n' };

public static void ReadLines(ReadOnlySequence<byte> sequence)
{
    SequenceReader<byte> reader = new SequenceReader<byte>(sequence);

    while (!reader.End)
    {
        if (!reader.TryReadToAny(out ReadOnlySpan<byte> line, CRLF, advancePastDelimiter:false))
        {
            // Couldn't find another delimiter
            // ...
        }

        if (!reader.IsNext(CRLF, advancePast: true))
        {
            // Not a good CR/LF pair
            // ...
        }

        // line is valid, process
        ProcessLine(line);
    }
}
```

## <a name="type-metadataloadcontext"></a><span data-ttu-id="fd1ca-204">Wpisz: MetadataLoadContext</span><span class="sxs-lookup"><span data-stu-id="fd1ca-204">Type: MetadataLoadContext</span></span>

<span data-ttu-id="fd1ca-205">`MetadataLoadContext` Typ został dodany, który umożliwia odczytywanie zestawu metadanych, bez wywierania wpływu na domeny aplikacji obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-205">The `MetadataLoadContext` type has been added that enables reading assembly metadata without affecting the caller’s application domain.</span></span> <span data-ttu-id="fd1ca-206">Zestawy są odczytywane jako dane, w tym zestawy stworzona z myślą o różnych architektur oraz platformach niż bieżącego środowiska.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-206">Assemblies are read as data, including assemblies built for different architectures and platforms than the current runtime environment.</span></span> <span data-ttu-id="fd1ca-207">`MetadataLoadContext` nakłada się na <xref:System.Reflection.Assembly.ReflectionOnlyLoad*>, która jest dostępna tylko w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-207">`MetadataLoadContext` overlaps with the <xref:System.Reflection.Assembly.ReflectionOnlyLoad*>, which is only available in the .NET Framework.</span></span>

<span data-ttu-id="fd1ca-208">`MetdataLoadContext` jest dostępna w [pakietu System.Reflection.MetadataLoadContext](https://www.nuget.org/packages/System.Reflection.MetadataLoadContext).</span><span class="sxs-lookup"><span data-stu-id="fd1ca-208">`MetdataLoadContext` is available in the [System.Reflection.MetadataLoadContext package](https://www.nuget.org/packages/System.Reflection.MetadataLoadContext).</span></span> <span data-ttu-id="fd1ca-209">To pakiet .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-209">It is a .NET Standard 2.0 package.</span></span>

<span data-ttu-id="fd1ca-210">`MetadataLoadContext` Udostępnia interfejsy API, podobnie jak <xref:System.Runtime.Loader.AssemblyLoadContext> typu, ale nie zależy od tego typu.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-210">The `MetadataLoadContext` exposes APIs similar to the <xref:System.Runtime.Loader.AssemblyLoadContext> type, but is not based on that type.</span></span> <span data-ttu-id="fd1ca-211">Podobnie jak <xref:System.Runtime.Loader.AssemblyLoadContext>, `MetadataLoadContext` umożliwia ładowanie zestawów w zestawie izolowane ładowania wszechświat.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-211">Much like <xref:System.Runtime.Loader.AssemblyLoadContext>, the `MetadataLoadContext` enables loading assemblies within an isolated assembly loading universe.</span></span> <span data-ttu-id="fd1ca-212">`MetdataLoadContext` Interfejsy API zwracają <xref:System.Reflection.Assembly> obiektów, umożliwiające użycie odbicia dobrze znanych interfejsów API.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-212">`MetdataLoadContext` APIs return <xref:System.Reflection.Assembly> objects, enabling the use of familiar reflection APIs.</span></span> <span data-ttu-id="fd1ca-213">Wykonanie zorientowane na interfejsy API, takich jak [MethodBase.Invoke](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/src/System/Reflection/TypeLoading/Methods/RoMethod.cs#L127), nie są dozwolone i będzie zgłaszać wyjątek InvalidOperationException.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-213">Execution-oriented APIs, such as [MethodBase.Invoke](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/src/System/Reflection/TypeLoading/Methods/RoMethod.cs#L127), are not allowed and will throw InvalidOperationException.</span></span>

<span data-ttu-id="fd1ca-214">W poniższym przykładzie pokazano, jak znaleźć konkretne typy w zestawie, który implementuje danego interfejsu:</span><span class="sxs-lookup"><span data-stu-id="fd1ca-214">The following sample demonstrates how to find concrete types in an assembly that implements a given interface:</span></span>

```csharp
var paths = new string[] {@"C:\myapp\mscorlib.dll", @"C:\myapp\myapp.dll"};
var resolver = new PathAssemblyResolver(paths);
using (var lc = new MetadataLoadContext(resolver))
{
    Assembly a = lc.LoadFromAssemblyName("myapp");
    Type myInterface = a.GetType("MyApp.IPluginInterface");
    foreach (Type t in a.GetTypes())
    {
        if (t.IsClass && myInterface.IsAssignableFrom(t))
            Console.WriteLine($"Class {t.FullName} implements IPluginInterface");
    }
}
```

<span data-ttu-id="fd1ca-215">Scenariusze dotyczące `MetadataLoadContext` obejmują funkcje czasu projektowania, narzędzi, czas kompilacji i środowiska uruchomieniowego światła w górę funkcje wymagające sprawdzanie zbiór zestawów danych i ma blokady wszystkich plików i pamięć zwolniona po kontroli jest wykonywane.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-215">Scenarios for `MetadataLoadContext` include design-time features, build-time tooling, and runtime light-up features that need to inspect a set of assemblies as data and have all file locks and memory freed after inspection is performed.</span></span>

<span data-ttu-id="fd1ca-216">`MetadataLoadContext` Przeszła klasy programu rozpoznawania nazw dla jego konstruktora.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-216">The `MetadataLoadContext` has a resolver class passed to its constructor.</span></span> <span data-ttu-id="fd1ca-217">Zadanie programu rozpoznawania nazw ma ładować `Assembly` biorąc pod uwagę jej `AssemblyName`.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-217">The resolver's job is to load an `Assembly` given its `AssemblyName`.</span></span> <span data-ttu-id="fd1ca-218">Klasa rozpoznawania pochodzi z abstrakcyjnej `MetadataAssemblyResolver` klasy.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-218">The resolver class derives from the abstract `MetadataAssemblyResolver` class.</span></span> <span data-ttu-id="fd1ca-219">Implementacja programu rozpoznawania nazw dla scenariuszy opartych na ścieżkach jest dostarczana z `PathAssemblyResolver`.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-219">An implementation of the resolver for path-based scenarios is provided with `PathAssemblyResolver`.</span></span>

<span data-ttu-id="fd1ca-220">[Testy MetadataLoadContext](https://github.com/dotnet/corefx/tree/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests) pokazują wielu przypadków użycia.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-220">The [MetadataLoadContext tests](https://github.com/dotnet/corefx/tree/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests) demonstrate many use cases.</span></span> <span data-ttu-id="fd1ca-221">[Zestawu testów](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests/Assembly/AssemblyTests.cs) są dobrym miejscem do rozpoczęcia.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-221">The [Assembly tests](https://github.com/dotnet/corefx/blob/master/src/System.Reflection.MetadataLoadContext/tests/src/Tests/Assembly/AssemblyTests.cs) are a good place to start.</span></span>

## <a name="tls-13--openssl-111-on-linux"></a><span data-ttu-id="fd1ca-222">TLS 1.3 & OpenSSL 1.1.1 w systemie Linux</span><span class="sxs-lookup"><span data-stu-id="fd1ca-222">TLS 1.3 & OpenSSL 1.1.1 on Linux</span></span>

<span data-ttu-id="fd1ca-223">.NET core będą teraz korzystać z [Obsługa protokołu TLS 1.3 w OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), gdy będzie ona dostępna w danym środowisku.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-223">.NET Core will now take advantage of [TLS 1.3 support in OpenSSL 1.1.1](https://www.openssl.org/blog/blog/2018/09/11/release111/), when it is available in a given environment.</span></span> <span data-ttu-id="fd1ca-224">Istnieją różne korzyści 1.3 protokołu TLS na [zespołu OpenSSL](https://www.openssl.org/blog/blog/2018/09/11/release111/):</span><span class="sxs-lookup"><span data-stu-id="fd1ca-224">There are multiple benefits of TLS 1.3, per the [OpenSSL team](https://www.openssl.org/blog/blog/2018/09/11/release111/):</span></span>

* <span data-ttu-id="fd1ca-225">Czas połączenia ulepszona z powodu ograniczenia liczby rund między klientem a serwerem.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-225">Improved connection times due to a reduction in the number of round trips required between the client and server.</span></span>

* <span data-ttu-id="fd1ca-226">Ulepszone zabezpieczenia z powodu usunięcia rozmaite algorytmy kryptograficzne przestarzały i niezabezpieczone i szyfrowania większej uzgadniania połączenia.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-226">Improved security due to the removal of various obsolete and insecure cryptographic algorithms and encryption of more of the connection handshake.</span></span>

<span data-ttu-id="fd1ca-227">.NET core 3.0 w wersji zapoznawczej 1 jest w stanie wykorzystujących **OpenSSL 1.1.1**, **OpenSSL 1.1.0**, lub **OpenSSL 1.0.2** (niezależnie od znaleziono wersji najlepiej jest, w systemie Linux).</span><span class="sxs-lookup"><span data-stu-id="fd1ca-227">.NET Core 3.0 Preview 1 is capable of utilizing **OpenSSL 1.1.1**, **OpenSSL 1.1.0**, or **OpenSSL 1.0.2** (whatever the best version found is, on a Linux system).</span></span>  <span data-ttu-id="fd1ca-228">Podczas **OpenSSL 1.1.1** jest dostępna będzie używać typów SslStream i HttpClient **TLS 1.3** korzystając z `SslProtocols.None` (protokołów domyślne systemu), zakładając, że klient i serwer obsługi **TLS 1.3**.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-228">When **OpenSSL 1.1.1** is available the SslStream and HttpClient types will use **TLS 1.3** when using `SslProtocols.None` (system default protocols), assuming both the client and server support **TLS 1.3**.</span></span>

<span data-ttu-id="fd1ca-229">W poniższym przykładzie pokazano .NET Core 3.0 w wersji zapoznawczej 1 na 18.10 Ubuntu nawiązywania połączenia z <https://www.cloudflare.com>:</span><span class="sxs-lookup"><span data-stu-id="fd1ca-229">The following sample demonstrates .NET Core 3.0 Preview 1 on Ubuntu 18.10 connecting to <https://www.cloudflare.com>:</span></span>

```csharp
using System;
using System.Net.Security;
using System.Net.Sockets;
using System.Threading.Tasks;

namespace tlstest
{
    class Program
    {
        static async Task Main()
        {
            using (TcpClient tcpClient = new TcpClient())
            {
                string targetHost = "www.cloudflare.com";

                await tcpClient.ConnectAsync(targetHost, 443);

                using (SslStream sslStream = new SslStream(tcpClient.GetStream()))
                {
                    await sslStream.AuthenticateAsClientAsync(targetHost);
                    await Console.Out.WriteLineAsync($"Connected to {targetHost} with {sslStream.SslProtocol}");
                }
            }
        }
    }
}
```

```console
user@comp-ubuntu1810:~/tlstest$ dotnet run
Connected to www.cloudflare.com with Tls13
user@comp-ubuntu1810:~/tlstest$ openssl version
OpenSSL 1.1.1  11 Sep 2018
```

>[!IMPORTANT]
><span data-ttu-id="fd1ca-230">Windows i macOS nie jest jeszcze obsługiwany **TLS 1.3**.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-230">Windows and macOS do not yet support **TLS 1.3**.</span></span> <span data-ttu-id="fd1ca-231">.NET core 3.0 to będzie obsługiwać **TLS 1.3** w tych systemach operacyjnych po udostępnieniu Pomocy technicznej.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-231">.NET Core 3.0 will support **TLS 1.3** on these operating systems when support becomes available.</span></span>

## <a name="cryptography"></a><span data-ttu-id="fd1ca-232">Kryptografia</span><span class="sxs-lookup"><span data-stu-id="fd1ca-232">Cryptography</span></span>

<span data-ttu-id="fd1ca-233">Dodano obsługę dla **AES-GCM** i **AES-CCM** szyfrów, wdrożone za pośrednictwem `System.Security.Cryptography.AesGcm` i `System.Security.Cryptography.AesCcm`.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-233">Support has been added for **AES-GCM** and **AES-CCM** ciphers, implemented via `System.Security.Cryptography.AesGcm` and `System.Security.Cryptography.AesCcm`.</span></span> <span data-ttu-id="fd1ca-234">Te algorytmy są [uwierzytelnione szyfrowanie za pomocą algorytmów skojarzenia danych (AEAD)](https://en.wikipedia.org/wiki/Authenticated_encryption)i pierwszy algorytmów szyfrowania uwierzytelniony (AE) dodane do platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-234">These algorithms are both [Authenticated Encryption with Association Data (AEAD) algorithms](https://en.wikipedia.org/wiki/Authenticated_encryption), and the first Authenticated Encryption (AE) algorithms added to .NET Core.</span></span>

<span data-ttu-id="fd1ca-235">Poniższy kod demonstruje użycie **AesGcm** szyfrowania do szyfrowania i odszyfrowywania danych losowych.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-235">The following code demonstrates using **AesGcm** cipher to encrypt and decrypt random data.</span></span>

<span data-ttu-id="fd1ca-236">Kod **AesCcm** będzie wyglądała niemal identyczne (tylko nazwy zmiennych klasy może się różnić).</span><span class="sxs-lookup"><span data-stu-id="fd1ca-236">The code for **AesCcm** would look almost identical (only the class variable names would be different).</span></span>

```csharp
// key should be: pre-known, derived, or transported via another channel, such as RSA encryption
byte[] key = new byte[16];
RandomNumberGenerator.Fill(key);

byte[] nonce = new byte[12];
RandomNumberGenerator.Fill(nonce);

// normally this would be your data
byte[] dataToEncrypt = new byte[1234];
byte[] associatedData = new byte[333];
RandomNumberGenerator.Fill(dataToEncrypt);
RandomNumberGenerator.Fill(associatedData);

// these will be filled during the encryption
byte[] tag = new byte[16];
byte[] ciphertext = new byte[dataToEncrypt.Length];

using (AesGcm aesGcm = new AesGcm(key))
{
    aesGcm.Encrypt(nonce, dataToEncrypt, ciphertext, tag, associatedData);
}

// tag, nonce, ciphertext, associatedData should be sent to the other part

byte[] decryptedData = new byte[ciphertext.Length];

using (AesGcm aesGcm = new AesGcm(key))
{
    aesGcm.Decrypt(nonce, ciphertext, tag, decryptedData, associatedData);
}

// do something with the data
// this should always print that data is the same
Console.WriteLine($"AES-GCM: Decrypted data is{(dataToEncrypt.SequenceEqual(decryptedData) ? "the same as" : "different than")} original data.");
```

## <a name="cryptographic-key-importexport"></a><span data-ttu-id="fd1ca-237">Kryptograficznych kluczy importu/eksportu</span><span class="sxs-lookup"><span data-stu-id="fd1ca-237">Cryptographic Key Import/Export</span></span>

<span data-ttu-id="fd1ca-238">.NET core 3.0 w wersji zapoznawczej 1 obsługuje importowanie i eksportowanie kluczy asymetrycznych publicznych i prywatnych z standardowych formatów, bez konieczności korzystania z certyfikatu X.509.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-238">.NET Core 3.0 Preview 1 supports the import and export of asymmetric public and private keys from standard formats, without needing to use an X.509 certificate.</span></span>

<span data-ttu-id="fd1ca-239">Wszystkie klucza Obsługa typów (RSA, DSA, ECDsa, ECDiffieHellman) **X.509 SubjectPublicKeyInfo** format kluczy publicznych i **PKCS #8 PrivateKeyInfo** i **PKCS #8 EncryptedPrivateKeyInfo**  formatów dla kluczy prywatnych.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-239">All key types (RSA, DSA, ECDsa, ECDiffieHellman) support the **X.509 SubjectPublicKeyInfo** format for public keys, and the **PKCS#8 PrivateKeyInfo** and **PKCS#8 EncryptedPrivateKeyInfo** formats for private keys.</span></span> <span data-ttu-id="fd1ca-240">Dodatkowo obsługuje RSA **PKCS #1 RSAPublicKey** i **PKCS #1 RSAPrivateKey**.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-240">RSA additionally supports **PKCS#1 RSAPublicKey** and **PKCS#1 RSAPrivateKey**.</span></span> <span data-ttu-id="fd1ca-241">Wszystkie metody eksportowania generuje dane binarne zakodowane w formacie DER i metod import oczekiwać takie same.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-241">The export methods all produce DER-encoded binary data, and the import methods expect the same.</span></span> <span data-ttu-id="fd1ca-242">Jeśli klucz jest przechowywany w formacie PEM przyjaznego tekstu, obiekt wywołujący, będą musieli base64 — dekodowanie zawartości przed wywołaniem metody importu.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-242">If a key is stored in the text-friendly PEM format, the caller will need to base64-decode the content before calling an import method.</span></span>

```csharp
using System;
using System.IO;
using System.Security.Cryptography;

namespace rsakeyprint
{
    class Program
    {
        static void Main(string[] args)
        {
            using (RSA rsa = RSA.Create())
            {
                byte[] keyBytes = File.ReadAllBytes(args[0]);
                rsa.ImportRSAPrivateKey(keyBytes, out int bytesRead);
 
                Console.WriteLine($"Read {bytesRead} bytes, {keyBytes.Length-bytesRead} extra byte(s) in file.");
                RSAParameters rsaParameters = rsa.ExportParameters(true);
                Console.WriteLine(BitConverter.ToString(rsaParameters.D));
            }
        }
    }
}
```

```console
user@comp-ubuntu1810:~/rsakeyprint$ echo Making a small key to save on screen space.
Making a small key to save on screen space.
user@comp-ubuntu1810:~/rsakeyprint$ openssl genrsa 768 | openssl rsa -outform der -out rsa.key
Generating RSA private key, 768 bit long modulus (2 primes)
..+++++++
........+++++++
e is 65537 (0x010001)
writing RSA key
user@comp-ubuntu1810:~/rsakeyprint$ dotnet run rsa.key
Read 461 bytes, 0 extra byte(s) in file.
0F-D0-82-34-F8-13-38-4A-7F-C7-52-4A-F6-93-F8-FB-6D-98-7A-6A-04-3B-BC-35-8C-7D-AC-A5-A3-6E-AD-C1-66-30-81-2C-2A-DE-DA-60-03-6A-2C-D9-76-15-7F-61-97-57-
79-E1-6E-45-62-C3-83-04-97-CB-32-EF-C5-17-5F-99-60-92-AE-B6-34-6F-30-06-03-AC-BF-15-24-43-84-EB-83-60-EF-4D-3B-BD-D9-5D-56-26-F0-51-CE-F1
user@comp-ubuntu1810:~/rsakeyprint$ openssl rsa -in rsa.key -inform der -text -noout | grep -A7 private
privateExponent:
    0f:d0:82:34:f8:13:38:4a:7f:c7:52:4a:f6:93:f8:
    fb:6d:98:7a:6a:04:3b:bc:35:8c:7d:ac:a5:a3:6e:
    ad:c1:66:30:81:2c:2a:de:da:60:03:6a:2c:d9:76:
    15:7f:61:97:57:79:e1:6e:45:62:c3:83:04:97:cb:
    32:ef:c5:17:5f:99:60:92:ae:b6:34:6f:30:06:03:
    ac:bf:15:24:43:84:eb:83:60:ef:4d:3b:bd:d9:5d:
    56:26:f0:51:ce:f1
```

<span data-ttu-id="fd1ca-243">Pliki PKCS #8 mogą być kontrolowane za pomocą `System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo` klasy.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-243">PKCS#8 files can be inspected with the `System.Security.Cryptography.Pkcs.Pkcs8PrivateKeyInfo` class.</span></span>

<span data-ttu-id="fd1ca-244">Pliki PFX/PKCS #12, które mogą być kontrolowane i modyfikować za pomocą `System.Security.Cryptography.Pkcs.Pkcs12Info` i `System.Security.Cryptography.Pkcs.Pkcs12Builder`, odpowiednio.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-244">PFX/PKCS#12 files can be inspected and manipulated with `System.Security.Cryptography.Pkcs.Pkcs12Info` and `System.Security.Cryptography.Pkcs.Pkcs12Builder`, respectively.</span></span>

## <a name="serialport-for-linux"></a><span data-ttu-id="fd1ca-245">Portu SerialPort dla systemu Linux</span><span class="sxs-lookup"><span data-stu-id="fd1ca-245">SerialPort for Linux</span></span>

<span data-ttu-id="fd1ca-246">.NET core 3.0 obsługuje teraz <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> w systemie Linux.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-246">.NET Core 3.0 now supports <xref:System.IO.Ports.SerialPort?displayProperty=nameWithType> on Linux.</span></span>

<span data-ttu-id="fd1ca-247">Wcześniej, .NET Core obsługiwana tylko przy użyciu `SerialPort` typu na Windows.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-247">Previously, .NET Core only supported using the `SerialPort` type on Windows.</span></span>

## <a name="more-bcl-improvements"></a><span data-ttu-id="fd1ca-248">Więcej udoskonaleń BCL</span><span class="sxs-lookup"><span data-stu-id="fd1ca-248">More BCL Improvements</span></span>

<span data-ttu-id="fd1ca-249">`Span<T>`, `Memory<T>`, I w środowisku .NET Core 3.0 zostały zoptymalizowane powiązanych typów, które zostały wprowadzone w programie .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-249">The `Span<T>`, `Memory<T>`, and related types that were introduced in .NET Core 2.1, have been optimized in .NET Core 3.0.</span></span> <span data-ttu-id="fd1ca-250">Typowe operacje takie jak span konstrukcji, dzielenie, analizowania i formatowanie teraz działać lepiej.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-250">Common operations such as span construction, slicing, parsing, and formatting now perform better.</span></span> 

<span data-ttu-id="fd1ca-251">Ponadto takie jak typy `String` przejrzane czyni je bardziej efektywnymi, gdy jest używana jako klucze o ulepszenia w obszarze cover `Dictionary<TKey, TValue>` i innych kolekcji.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-251">Additionally, types like `String` have seen under-the-cover improvements to make them more efficient when used as keys with `Dictionary<TKey, TValue>` and other collections.</span></span> <span data-ttu-id="fd1ca-252">Bez zmian w kodzie są wymagane do korzystania z tych ulepszeń.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-252">No code changes are required to benefit from these improvements.</span></span>

<span data-ttu-id="fd1ca-253">Następujące ulepszenia również są nowe w .NET Core 3 (wersja zapoznawcza) 1:</span><span class="sxs-lookup"><span data-stu-id="fd1ca-253">The following improvements are also new in .NET Core 3 Preview 1:</span></span>

* <span data-ttu-id="fd1ca-254">Obsługa Brotli wbudowanej w HttpClient</span><span class="sxs-lookup"><span data-stu-id="fd1ca-254">Brotli support built in to HttpClient</span></span>
* <span data-ttu-id="fd1ca-255">ThreadPool.UnsafeQueueWorkItem(IThreadPoolWorkItem)</span><span class="sxs-lookup"><span data-stu-id="fd1ca-255">ThreadPool.UnsafeQueueWorkItem(IThreadPoolWorkItem)</span></span>
* <span data-ttu-id="fd1ca-256">Unsafe.Unbox</span><span class="sxs-lookup"><span data-stu-id="fd1ca-256">Unsafe.Unbox</span></span>
* <span data-ttu-id="fd1ca-257">CancellationToken.Unregister</span><span class="sxs-lookup"><span data-stu-id="fd1ca-257">CancellationToken.Unregister</span></span>
* <span data-ttu-id="fd1ca-258">Złożone operatory arytmetyczne</span><span class="sxs-lookup"><span data-stu-id="fd1ca-258">Complex arithmetic operators</span></span>
* <span data-ttu-id="fd1ca-259">Podtrzymywania API gniazda TCP</span><span class="sxs-lookup"><span data-stu-id="fd1ca-259">Socket APIs for TCP keep alive</span></span>
* <span data-ttu-id="fd1ca-260">StringBuilder.GetChunks</span><span class="sxs-lookup"><span data-stu-id="fd1ca-260">StringBuilder.GetChunks</span></span>
* <span data-ttu-id="fd1ca-261">IPEndPoint analizy</span><span class="sxs-lookup"><span data-stu-id="fd1ca-261">IPEndPoint parsing</span></span>
* <span data-ttu-id="fd1ca-262">RandomNumberGenerator.GetInt32</span><span class="sxs-lookup"><span data-stu-id="fd1ca-262">RandomNumberGenerator.GetInt32</span></span>

## <a name="tiered-compilation"></a><span data-ttu-id="fd1ca-263">Warstwowe kompilacji</span><span class="sxs-lookup"><span data-stu-id="fd1ca-263">Tiered compilation</span></span>

<span data-ttu-id="fd1ca-264">[Warstwowe kompilacji](https://blogs.msdn.microsoft.com/dotnet/2018/08/02/tiered-compilation-preview-in-net-core-2-1/) jest domyślnie przy użyciu platformy .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-264">[Tiered compilation](https://blogs.msdn.microsoft.com/dotnet/2018/08/02/tiered-compilation-preview-in-net-core-2-1/) is on by default with .NET Core 3.0.</span></span> <span data-ttu-id="fd1ca-265">Jest funkcją, która umożliwia bardziej adaptacyjnie Użyj kompilator just in Time (JIT), aby uzyskać lepszą wydajność, zarówno podczas uruchamiania i w celu zmaksymalizowania wydajności.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-265">It is a feature that enables the runtime to more adaptively use the Just-In-Time (JIT) compiler to get better performance, both at startup and to maximize throughput.</span></span>

<span data-ttu-id="fd1ca-266">Ta funkcja została dodana jako funkcja opcjonalna w [platformy .NET Core 2.1](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/) i następnie została włączona domyślnie w [.NET Core 2.2 w wersji zapoznawczej 2](https://blogs.msdn.microsoft.com/dotnet/2018/09/12/announcing-net-core-2-2-preview-2/).</span><span class="sxs-lookup"><span data-stu-id="fd1ca-266">This feature was added as an opt-in feature in [.NET Core 2.1](https://blogs.msdn.microsoft.com/dotnet/2018/05/30/announcing-net-core-2-1/) and then was enabled by default in [.NET Core 2.2 Preview 2](https://blogs.msdn.microsoft.com/dotnet/2018/09/12/announcing-net-core-2-2-preview-2/).</span></span> <span data-ttu-id="fd1ca-267">Następnie został on przywrócony do zoptymalizowany pod kątem się przy użyciu wersji platformy .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-267">Subsequently, it has been reverted back to opt in with the .NET Core 2.2 release.</span></span>

## <a name="arm64-linux-support"></a><span data-ttu-id="fd1ca-268">Obsługa systemu Linux ARM64</span><span class="sxs-lookup"><span data-stu-id="fd1ca-268">ARM64 Linux support</span></span>

<span data-ttu-id="fd1ca-269">Dodajemy obsługę tej wersji systemu Linux dla architektury ARM64.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-269">We are adding support for ARM64 for Linux this release.</span></span> <span data-ttu-id="fd1ca-270">Kontekst Dodaliśmy obsługę ARM32 dla systemu Linux przy użyciu platformy .NET Core 2.1 i Windows przy użyciu platformy .NET Core 2.2.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-270">For context, we added support for ARM32 for Linux with .NET Core 2.1 and Windows with .NET Core 2.2.</span></span> <span data-ttu-id="fd1ca-271">Głównym zastosowaniem dla architektury ARM64 jest obecnie używany w scenariuszach IoT.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-271">The primary use case for ARM64 is currently with IoT scenarios.</span></span>

<span data-ttu-id="fd1ca-272">Firma Alpine, Debian i Ubuntu [obrazów platformy Docker są dostępne dla platformy .NET Core dla architektury ARM64](https://hub.docker.com/r/microsoft/dotnet/).</span><span class="sxs-lookup"><span data-stu-id="fd1ca-272">Alpine, Debian and Ubuntu [Docker images are available for .NET Core for ARM64](https://hub.docker.com/r/microsoft/dotnet/).</span></span>

<span data-ttu-id="fd1ca-273">Sprawdź, czy [stanu programu .NET Core ARM64](https://github.com/dotnet/announcements/issues/82) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-273">Please check [.NET Core ARM64 Status](https://github.com/dotnet/announcements/issues/82) for more information.</span></span>

>[!NOTE]
> <span data-ttu-id="fd1ca-274">**ARM64** pomocy technicznej Windows nie jest jeszcze dostępna.</span><span class="sxs-lookup"><span data-stu-id="fd1ca-274">**ARM64** Windows support isn't yet available.</span></span>

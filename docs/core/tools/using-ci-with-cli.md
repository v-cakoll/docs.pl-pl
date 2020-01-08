---
title: Ciągła integracja (CI) z zestaw .NET Core SDK i narzędziami
description: Dowiedz się, jak używać zestaw .NET Core SDK i narzędzi na serwerze kompilacji z ciągłą integracją.
author: mairaw
ms.date: 05/18/2017
ms.custom: seodec18
ms.openlocfilehash: 0f6049d1f2868ff330fd59c4f40e6c02231c6f71
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75343538"
---
# <a name="using-net-core-sdk-and-tools-in-continuous-integration-ci"></a><span data-ttu-id="8c1f0-103">Używanie zestaw .NET Core SDK i narzędzi w ciągłej integracji (CI)</span><span class="sxs-lookup"><span data-stu-id="8c1f0-103">Using .NET Core SDK and tools in Continuous Integration (CI)</span></span>

<span data-ttu-id="8c1f0-104">Ten dokument jest przedstawiony przy użyciu zestaw .NET Core SDK i jego narzędzi na serwerze kompilacji.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-104">This document outlines using the .NET Core SDK and its tools on a build server.</span></span> <span data-ttu-id="8c1f0-105">Zestaw narzędzi platformy .NET Core działa interaktywnie, gdzie deweloperzy typów poleceń w wierszu polecenia i automatycznie, gdzie serwer ciągłej integracji (CI) uruchamia skrypt kompilacji.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-105">The .NET Core toolset works both interactively, where a developer types commands at a command prompt, and automatically, where a Continuous Integration (CI) server runs a build script.</span></span> <span data-ttu-id="8c1f0-106">Polecenia, opcje, dane wejściowe i wyjściowe są takie same, a jedyne dostępne elementy to sposób uzyskania narzędzi i systemu w celu skompilowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-106">The commands, options, inputs, and outputs are the same, and the only things you supply are a way to acquire the tooling and a system to build your app.</span></span> <span data-ttu-id="8c1f0-107">Ten dokument koncentruje się na scenariuszach pozyskiwania narzędzi dla CI z zaleceniami dotyczącymi projektowania i struktury skryptów kompilacji.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-107">This document focuses on scenarios of tool acquisition for CI with recommendations on how to design and structure your build scripts.</span></span>

## <a name="installation-options-for-ci-build-servers"></a><span data-ttu-id="8c1f0-108">Opcje instalacji dla serwerów kompilacji CI</span><span class="sxs-lookup"><span data-stu-id="8c1f0-108">Installation options for CI build servers</span></span>

### <a name="using-the-native-installers"></a><span data-ttu-id="8c1f0-109">Korzystanie z natywnych instalatorów</span><span class="sxs-lookup"><span data-stu-id="8c1f0-109">Using the native installers</span></span>

<span data-ttu-id="8c1f0-110">Natywne Instalatory są dostępne dla systemów macOS, Linux i Windows.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-110">Native installers are available for macOS, Linux, and Windows.</span></span> <span data-ttu-id="8c1f0-111">Instalatory wymagają dostępu administratora (sudo) do serwera kompilacji.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-111">The installers require admin (sudo) access to the build server.</span></span> <span data-ttu-id="8c1f0-112">Zaletą korzystania z instalatora natywnego jest zainstalowanie wszystkich natywnych zależności wymaganych do uruchomienia narzędzi.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-112">The advantage of using a native installer is that it installs all of the native dependencies required for the tooling to run.</span></span> <span data-ttu-id="8c1f0-113">Natywne Instalatory oferują również instalację zestawu SDK na poziomie systemu.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-113">Native installers also provide a system-wide installation of the SDK.</span></span>

<span data-ttu-id="8c1f0-114">macOS użytkownicy powinni używać instalatorów PKG.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-114">macOS users should use the PKG installers.</span></span> <span data-ttu-id="8c1f0-115">W systemie Linux istnieje możliwość korzystania z Menedżera pakietów opartych na kanale informacyjnym, takiego jak apt-get for Ubuntu lub yum dla CentOS lub z użyciem samych pakietów, DEB lub RPM.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-115">On Linux, there's a choice of using a feed-based package manager, such as apt-get for Ubuntu or yum for CentOS, or using the packages themselves, DEB or RPM.</span></span> <span data-ttu-id="8c1f0-116">W systemie Windows użyj Instalatora MSI.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-116">On Windows, use the MSI installer.</span></span>

<span data-ttu-id="8c1f0-117">Najnowsze stabilne pliki binarne są dostępne na [platformie .NET](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="8c1f0-117">The latest stable binaries are found at [.NET downloads](https://dotnet.microsoft.com/download).</span></span> <span data-ttu-id="8c1f0-118">Jeśli chcesz użyć najnowszych (i potencjalnie niestabilnych) narzędzi w wersji wstępnej, Skorzystaj z linków dostarczonych w [repozytorium GitHub/Core-SDK](https://github.com/dotnet/core-sdk#installers-and-binaries)w ramach programu dotnet.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-118">If you wish to use the latest (and potentially unstable) pre-release tooling, use the links provided at the [dotnet/core-sdk GitHub repository](https://github.com/dotnet/core-sdk#installers-and-binaries).</span></span> <span data-ttu-id="8c1f0-119">W przypadku dystrybucji systemu Linux dostępne są `tar.gz` archiwa (znane także jako `tarballs`); Użyj skryptów instalacji w archiwach, aby zainstalować platformę .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-119">For Linux distributions, `tar.gz` archives (also known as `tarballs`) are available; use the installation scripts within the archives to install .NET Core.</span></span>

### <a name="using-the-installer-script"></a><span data-ttu-id="8c1f0-120">Korzystanie z skryptu Instalatora</span><span class="sxs-lookup"><span data-stu-id="8c1f0-120">Using the installer script</span></span>

<span data-ttu-id="8c1f0-121">Użycie skryptu Instalatora pozwala na instalację nieadministracyjną na serwerze kompilacji i łatwą automatyzację w celu uzyskania narzędzi.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-121">Using the installer script allows for non-administrative installation on your build server and easy automation for obtaining the tooling.</span></span> <span data-ttu-id="8c1f0-122">Skrypt wymaga pobrania narzędzi i wyodrębnienia go do domyślnej lub określonej lokalizacji do użycia.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-122">The script takes care of downloading the tooling and extracting it into a default or specified location for use.</span></span> <span data-ttu-id="8c1f0-123">Możesz również określić wersję narzędzi, którą chcesz zainstalować, i zdecydować, czy chcesz zainstalować cały zestaw SDK, czy tylko udostępnione środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-123">You can also specify a version of the tooling that you wish to install and whether you want to install the entire SDK or only the shared runtime.</span></span>

<span data-ttu-id="8c1f0-124">Skrypt Instalatora jest zautomatyzowany do uruchomienia na początku kompilacji, aby pobrać i zainstalować żądaną wersję zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-124">The installer script is automated to run at the start of the build to fetch and install the desired version of the SDK.</span></span> <span data-ttu-id="8c1f0-125">*Wymagana wersja* to Poprzednia wersja zestawu SDK, których projekty wymagają do skompilowania.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-125">The *desired version* is whatever version of the SDK your projects require to build.</span></span> <span data-ttu-id="8c1f0-126">Skrypt umożliwia zainstalowanie zestawu SDK w katalogu lokalnym na serwerze, uruchomienie narzędzi z zainstalowanej lokalizacji, a następnie oczyszczenie (lub umożliwienie oczyszczenia usługi CI) po kompilacji.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-126">The script allows you to install the SDK in a local directory on the server, run the tools from the installed location, and then clean up (or let the CI service clean up) after the build.</span></span> <span data-ttu-id="8c1f0-127">Zapewnia to hermetyzację i izolację całego procesu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-127">This provides encapsulation and isolation to your entire build process.</span></span> <span data-ttu-id="8c1f0-128">Informacje o skrypcie instalacji znajdują się w artykule [dotnet-Install](dotnet-install-script.md) .</span><span class="sxs-lookup"><span data-stu-id="8c1f0-128">The installation script reference is found in the [dotnet-install](dotnet-install-script.md) article.</span></span>

> [!NOTE]
> <span data-ttu-id="8c1f0-129">**Azure DevOps Services**</span><span class="sxs-lookup"><span data-stu-id="8c1f0-129">**Azure DevOps Services**</span></span>
>
> <span data-ttu-id="8c1f0-130">W przypadku korzystania z skryptu Instalatora zależności natywne nie są instalowane automatycznie.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-130">When using the installer script, native dependencies aren't installed automatically.</span></span> <span data-ttu-id="8c1f0-131">Jeśli system operacyjny ich nie ma, należy zainstalować zależności natywne.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-131">You must install the native dependencies if the operating system doesn't have them.</span></span> <span data-ttu-id="8c1f0-132">Aby uzyskać więcej informacji, zobacz [zależności i wymagania dotyczące platformy .NET Core](../install/dependencies.md?tabs=netcore30&pivots=os-linux).</span><span class="sxs-lookup"><span data-stu-id="8c1f0-132">For more information, see [.NET Core dependencies and requirements](../install/dependencies.md?tabs=netcore30&pivots=os-linux).</span></span>

## <a name="ci-setup-examples"></a><span data-ttu-id="8c1f0-133">Przykłady konfiguracji elementu konfiguracji</span><span class="sxs-lookup"><span data-stu-id="8c1f0-133">CI setup examples</span></span>

<span data-ttu-id="8c1f0-134">W tej sekcji opisano konfigurację ręczną przy użyciu skryptu PowerShell lub bash, a także opis kilku rozwiązań CI (Software as a Service).</span><span class="sxs-lookup"><span data-stu-id="8c1f0-134">This section describes a manual setup using a PowerShell or bash script, along with a description of several software as a service (SaaS) CI solutions.</span></span> <span data-ttu-id="8c1f0-135">Rozwiązania CI SaaS CI obejmują [rozwiązania Travis Ci](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/)i [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index).</span><span class="sxs-lookup"><span data-stu-id="8c1f0-135">The SaaS CI solutions covered are [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), and [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index).</span></span>

### <a name="manual-setup"></a><span data-ttu-id="8c1f0-136">Konfiguracja ręczna</span><span class="sxs-lookup"><span data-stu-id="8c1f0-136">Manual setup</span></span>

<span data-ttu-id="8c1f0-137">Każda usługa SaaS ma własne metody tworzenia i konfigurowania procesu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-137">Each SaaS service has its own methods for creating and configuring a build process.</span></span> <span data-ttu-id="8c1f0-138">Jeśli używasz innego rozwiązania SaaS niż wymienione lub wymagają dostosowania poza wstępnie spakowaną obsługą, należy wykonać co najmniej konfigurację ręczną.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-138">If you use different SaaS solution than those listed or require customization beyond the pre-packaged support, you must perform at least some manual configuration.</span></span>

<span data-ttu-id="8c1f0-139">Ogólnie Konfiguracja ręczna wymaga pozyskania wersji narzędzi (lub najnowszych, nocnych kompilacji narzędzi) i uruchomienia skryptu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-139">In general, a manual setup requires you to acquire a version of the tools (or the latest nightly builds of the tools) and run your build script.</span></span> <span data-ttu-id="8c1f0-140">Za pomocą skryptu PowerShell lub bash można organizować polecenia .NET Core lub używać pliku projektu, który zawiera opis procesu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-140">You can use a PowerShell or bash script to orchestrate the .NET Core commands or use a project file that outlines the build process.</span></span> <span data-ttu-id="8c1f0-141">[Sekcja aranżacja](#orchestrating-the-build) zawiera więcej szczegółów na temat tych opcji.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-141">The [orchestration section](#orchestrating-the-build) provides more detail on these options.</span></span>

<span data-ttu-id="8c1f0-142">Po utworzeniu skryptu, który wykonuje ręczną konfigurację serwera kompilacji, użyj go na komputerze deweloperskim, aby utworzyć kod lokalnie na potrzeby testowania.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-142">After you create a script that performs a manual CI build server setup, use it on your dev machine to build your code locally for testing purposes.</span></span> <span data-ttu-id="8c1f0-143">Po upewnieniu się, że skrypt działa prawidłowo, wdróż go na serwerze kompilacji CI.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-143">Once you confirm that the script is running well locally, deploy it to your CI build server.</span></span> <span data-ttu-id="8c1f0-144">Stosunkowo prosty skrypt programu PowerShell pokazuje, jak uzyskać zestaw .NET Core SDK i zainstalować go na serwerze kompilacji systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="8c1f0-144">A relatively simple PowerShell script demonstrates how to obtain the .NET Core SDK and install it on a Windows build server:</span></span>

```powershell
$ErrorActionPreference="Stop"
$ProgressPreference="SilentlyContinue"

# $LocalDotnet is the path to the locally-installed SDK to ensure the
#   correct version of the tools are executed.
$LocalDotnet=""
# $InstallDir and $CliVersion variables can come from options to the
#   script.
$InstallDir = "./cli-tools"
$CliVersion = "1.0.1"

# Test the path provided by $InstallDir to confirm it exists. If it
#   does, it's removed. This is not strictly required, but it's a
#   good way to reset the environment.
if (Test-Path $InstallDir)
{
    rm -Recurse $InstallDir
}
New-Item -Type "directory" -Path $InstallDir

Write-Host "Downloading the CLI installer..."

# Use the Invoke-WebRequest PowerShell cmdlet to obtain the
#   installation script and save it into the installation directory.
Invoke-WebRequest `
    -Uri "https://dot.net/v1/dotnet-install.ps1" `
    -OutFile "$InstallDir/dotnet-install.ps1"

Write-Host "Installing the CLI requested version ($CliVersion) ..."

# Install the SDK of the version specified in $CliVersion into the
#   specified location ($InstallDir).
& $InstallDir/dotnet-install.ps1 -Version $CliVersion `
    -InstallDir $InstallDir

Write-Host "Downloading and installation of the SDK is complete."

# $LocalDotnet holds the path to dotnet.exe for future use by the
#   script.
$LocalDotnet = "$InstallDir/dotnet"

# Run the build process now. Implement your build script here.
```

<span data-ttu-id="8c1f0-145">Implementację procesu kompilacji można dostarczyć na końcu skryptu.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-145">You provide the implementation for your build process at the end of the script.</span></span> <span data-ttu-id="8c1f0-146">Skrypt uzyskuje narzędzia, a następnie wykonuje proces kompilacji.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-146">The script acquires the tools and then executes your build process.</span></span> <span data-ttu-id="8c1f0-147">W przypadku maszyn z systemem UNIX następujący skrypt bash wykonuje akcje opisane w skrypcie programu PowerShell w podobny sposób:</span><span class="sxs-lookup"><span data-stu-id="8c1f0-147">For UNIX machines, the following bash script performs the actions described in the PowerShell script in a similar manner:</span></span>

```bash
#!/bin/bash
INSTALLDIR="cli-tools"
CLI_VERSION=1.0.1
DOWNLOADER=$(which curl)
if [ -d "$INSTALLDIR" ]
then
    rm -rf "$INSTALLDIR"
fi
mkdir -p "$INSTALLDIR"
echo Downloading the CLI installer.
$DOWNLOADER https://dot.net/v1/dotnet-install.sh > "$INSTALLDIR/dotnet-install.sh"
chmod +x "$INSTALLDIR/dotnet-install.sh"
echo Installing the CLI requested version $CLI_VERSION. Please wait, installation may take a few minutes.
"$INSTALLDIR/dotnet-install.sh" --install-dir "$INSTALLDIR" --version $CLI_VERSION
if [ $? -ne 0 ]
then
    echo Download of $CLI_VERSION version of the CLI failed. Exiting now.
    exit 0
fi
echo The CLI has been installed.
LOCALDOTNET="$INSTALLDIR/dotnet"
# Run the build process now. Implement your build script here.
```

### <a name="travis-ci"></a><span data-ttu-id="8c1f0-148">Rozwiązania Travis CI</span><span class="sxs-lookup"><span data-stu-id="8c1f0-148">Travis CI</span></span>

<span data-ttu-id="8c1f0-149">Można skonfigurować [rozwiązania Travis Ci](https://travis-ci.org/) do instalowania zestaw .NET Core SDK przy użyciu języka `csharp` i klucza `dotnet`.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-149">You can configure [Travis CI](https://travis-ci.org/) to install the .NET Core SDK using the `csharp` language and the `dotnet` key.</span></span> <span data-ttu-id="8c1f0-150">Aby uzyskać więcej informacji, zobacz oficjalne dokumenty rozwiązania Travis Ci na [Kompilowanie C#projektu F#, lub Visual Basic](https://docs.travis-ci.com/user/languages/csharp/).</span><span class="sxs-lookup"><span data-stu-id="8c1f0-150">For more information, see the official Travis CI docs on [Building a C#, F#, or Visual Basic Project](https://docs.travis-ci.com/user/languages/csharp/).</span></span> <span data-ttu-id="8c1f0-151">Zwróć uwagę na to, że uzyskujesz dostęp do informacji o CI, które są obsługiwane przez społeczność `language: csharp` identyfikator języka dla F#wszystkich języków .NET, w tym i mono.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-151">Note as you access the Travis CI information that the community-maintained `language: csharp` language identifier works for all .NET languages, including F#, and Mono.</span></span>

<span data-ttu-id="8c1f0-152">Rozwiązania Travis CI uruchamia zarówno zadania macOS, jak i Linux w *macierzy kompilacji*, w której można określić kombinację środowiska uruchomieniowego, środowiska i wykluczeń/dołączeń w celu pokrycia kombinacji kompilacji dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-152">Travis CI runs both macOS and Linux jobs in a *build matrix*, where you specify a combination of runtime, environment, and exclusions/inclusions to cover your build combinations for your app.</span></span> <span data-ttu-id="8c1f0-153">Aby uzyskać więcej informacji, zobacz artykuł [Dostosowywanie kompilacji](https://docs.travis-ci.com/user/customizing-the-build) w dokumentacji elementu konfiguracji rozwiązania Travis.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-153">For more information, see the [Customizing the Build](https://docs.travis-ci.com/user/customizing-the-build) article in the Travis CI documentation.</span></span> <span data-ttu-id="8c1f0-154">Narzędzia oparte na programie MSBuild obejmują środowiska uruchomieniowe LTS (1.0. x) i bieżące (1.1. x) w pakiecie; Dzięki zainstalowaniu zestawu SDK otrzymujesz wszystko, czego potrzebujesz do skompilowania.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-154">The MSBuild-based tools include the LTS (1.0.x) and Current (1.1.x) runtimes in the package; so by installing the SDK, you receive everything you need to build.</span></span>

### <a name="appveyor"></a><span data-ttu-id="8c1f0-155">AppVeyor</span><span class="sxs-lookup"><span data-stu-id="8c1f0-155">AppVeyor</span></span>

<span data-ttu-id="8c1f0-156">[AppVeyor](https://www.appveyor.com/) instaluje zestaw .NET Core 1.0.1 SDK przy użyciu obrazu procesu roboczego kompilacji `Visual Studio 2017`.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-156">[AppVeyor](https://www.appveyor.com/) installs the .NET Core 1.0.1 SDK with the `Visual Studio 2017` build worker image.</span></span> <span data-ttu-id="8c1f0-157">Dostępne są inne obrazy kompilacji z różnymi wersjami zestaw .NET Core SDK.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-157">Other build images with different versions of the .NET Core SDK are available.</span></span> <span data-ttu-id="8c1f0-158">Aby uzyskać więcej informacji, zobacz [przykład appveyor. yml](https://github.com/dotnet/docs/blob/master/appveyor.yml) oraz artykuł [Build Worker images](https://www.appveyor.com/docs/build-environment/#build-worker-images) w dokumentacji appveyor.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-158">For more information, see the [appveyor.yml example](https://github.com/dotnet/docs/blob/master/appveyor.yml) and the [Build worker images](https://www.appveyor.com/docs/build-environment/#build-worker-images) article in the AppVeyor docs.</span></span>

<span data-ttu-id="8c1f0-159">Pliki binarne zestaw .NET Core SDK są pobierane i rozpakowane w podkatalogu przy użyciu skryptu instalacji, a następnie są dodawane do zmiennej środowiskowej `PATH`.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-159">The .NET Core SDK binaries are downloaded and unzipped in a subdirectory using the install script, and then they're added to the `PATH` environment variable.</span></span> <span data-ttu-id="8c1f0-160">Dodaj macierz kompilacji, aby uruchomić testy integracji z wieloma wersjami zestaw .NET Core SDK:</span><span class="sxs-lookup"><span data-stu-id="8c1f0-160">Add a build matrix to run integration tests with multiple versions of the .NET Core SDK:</span></span>

```yaml
environment:
  matrix:
    - CLI_VERSION: 1.0.1
    - CLI_VERSION: Latest

install:
  # See appveyor.yml example for install script
```

### <a name="azure-devops-services"></a><span data-ttu-id="8c1f0-161">Azure DevOps Services</span><span class="sxs-lookup"><span data-stu-id="8c1f0-161">Azure DevOps Services</span></span>

<span data-ttu-id="8c1f0-162">Skonfiguruj Azure DevOps Services do kompilowania projektów .NET Core przy użyciu jednej z następujących metod:</span><span class="sxs-lookup"><span data-stu-id="8c1f0-162">Configure Azure DevOps Services to build .NET Core projects using one of these approaches:</span></span>

1. <span data-ttu-id="8c1f0-163">Uruchom skrypt z [kroku instalacji ręcznej](#manual-setup) przy użyciu poleceń.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-163">Run the script from the [manual setup step](#manual-setup) using your commands.</span></span>
1. <span data-ttu-id="8c1f0-164">Utwórz kompilację składającą się z kilku Azure DevOps Services wbudowanych zadań kompilacji, które są skonfigurowane do korzystania z narzędzi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-164">Create a build composed of several Azure DevOps Services built-in build tasks that are configured to use .NET Core tools.</span></span>

<span data-ttu-id="8c1f0-165">Oba rozwiązania są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-165">Both solutions are valid.</span></span> <span data-ttu-id="8c1f0-166">Za pomocą ręcznego skryptu konfiguracji kontrolujesz wersję narzędzi, które otrzymujesz, ponieważ pobierasz je w ramach kompilacji.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-166">Using a manual setup script, you control the version of the tools that you receive, since you download them as part of the build.</span></span> <span data-ttu-id="8c1f0-167">Kompilacja jest uruchamiana ze skryptu, który należy utworzyć.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-167">The build is run from a script that you must create.</span></span> <span data-ttu-id="8c1f0-168">W tym artykule omówiono tylko opcję ręczną.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-168">This article only covers the manual option.</span></span> <span data-ttu-id="8c1f0-169">Aby uzyskać więcej informacji na temat tworzenia kompilacji z zadaniami kompilacji Azure DevOps Services, zobacz dokumentację [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index) .</span><span class="sxs-lookup"><span data-stu-id="8c1f0-169">For more information on composing a build with Azure DevOps Services build tasks, see the [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index) documentation.</span></span>

<span data-ttu-id="8c1f0-170">Aby użyć ręcznego skryptu konfiguracji w Azure DevOps Services, Utwórz nową definicję kompilacji i określ skrypt do uruchomienia dla kroku kompilacji.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-170">To use a manual setup script in Azure DevOps Services, create a new build definition and specify the script to run for the build step.</span></span> <span data-ttu-id="8c1f0-171">Jest to realizowane przy użyciu Azure DevOps Services interfejsu użytkownika:</span><span class="sxs-lookup"><span data-stu-id="8c1f0-171">This is accomplished using the Azure DevOps Services user interface:</span></span>

1. <span data-ttu-id="8c1f0-172">Zacznij od utworzenia nowej definicji kompilacji.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-172">Start by creating a new build definition.</span></span> <span data-ttu-id="8c1f0-173">Po osiągnięciu ekranu, który udostępnia opcję definiowania rodzaju kompilacji, którą chcesz utworzyć, wybierz opcję **pustą** .</span><span class="sxs-lookup"><span data-stu-id="8c1f0-173">Once you reach the screen that provides you an option to define what kind of a build you wish to create, select the **Empty** option.</span></span>

   ![Wybieranie pustej definicji kompilacji](./media/using-ci-with-cli/select-empty-build-definition.png)

1. <span data-ttu-id="8c1f0-175">Po skonfigurowaniu repozytorium do kompilacji, nastąpi przekierowanie do definicji kompilacji.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-175">After configuring the repository to build, you're directed to the build definitions.</span></span> <span data-ttu-id="8c1f0-176">Wybierz pozycję **Dodaj krok kompilacji**:</span><span class="sxs-lookup"><span data-stu-id="8c1f0-176">Select **Add build step**:</span></span>

   ![Dodawanie kroku kompilacji](./media/using-ci-with-cli/add-build-step.png)

1. <span data-ttu-id="8c1f0-178">Zostanie wyświetlony **katalog zadań**.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-178">You're presented with the **Task catalog**.</span></span> <span data-ttu-id="8c1f0-179">Wykaz zawiera zadania, które są używane w kompilacji.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-179">The catalog contains tasks that you use in the build.</span></span> <span data-ttu-id="8c1f0-180">Ponieważ masz skrypt, wybierz przycisk **Dodaj** dla **programu PowerShell: Uruchom skrypt programu PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-180">Since you have a script, select the **Add** button for **PowerShell: Run a PowerShell script**.</span></span>

   ![Dodawanie kroku skryptu programu PowerShell](./media/using-ci-with-cli/add-powershell-script.png)

1. <span data-ttu-id="8c1f0-182">Skonfiguruj krok kompilacji.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-182">Configure the build step.</span></span> <span data-ttu-id="8c1f0-183">Dodaj skrypt z repozytorium, które tworzysz:</span><span class="sxs-lookup"><span data-stu-id="8c1f0-183">Add the script from the repository that you're building:</span></span>

   ![Określanie skryptu programu PowerShell do uruchomienia](./media/using-ci-with-cli/powershell-script-path.png)

## <a name="orchestrating-the-build"></a><span data-ttu-id="8c1f0-185">Organizowanie kompilacji</span><span class="sxs-lookup"><span data-stu-id="8c1f0-185">Orchestrating the build</span></span>

<span data-ttu-id="8c1f0-186">W większości tego dokumentu opisano, jak uzyskać narzędzia .NET Core i skonfigurować różne usługi CI, bez przekazywania informacji na temat sposobu organizowania lub *kompilowania*kodu za pomocą platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-186">Most of this document describes how to acquire the .NET Core tools and configure various CI services without providing information on how to orchestrate, or *actually build*, your code with .NET Core.</span></span> <span data-ttu-id="8c1f0-187">Wybór sposobu struktury procesu kompilacji zależy od wielu czynników, które nie mogą być omówione w ogólny sposób.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-187">The choices on how to structure the build process depend on many factors that can't be covered in a general way here.</span></span> <span data-ttu-id="8c1f0-188">Aby uzyskać więcej informacji na temat organizowania kompilacji z każdą technologią, zapoznaj się z zasobami i przykładami dostępnymi w zestawach dokumentacji [rozwiązania Travis Ci](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/)i [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index).</span><span class="sxs-lookup"><span data-stu-id="8c1f0-188">For more information on orchestrating your builds with each technology, explore the resources and samples provided in the documentation sets of [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), and [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index).</span></span>

<span data-ttu-id="8c1f0-189">Dwa ogólne podejścia do tworzenia struktury procesu kompilacji dla kodu platformy .NET Core przy użyciu narzędzi .NET Core Tools używają programu MSBuild bezpośrednio lub przy użyciu poleceń wiersza polecenia programu .NET Core.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-189">Two general approaches that you take in structuring the build process for .NET Core code using the .NET Core tools are using MSBuild directly or using the .NET Core command-line commands.</span></span> <span data-ttu-id="8c1f0-190">Podejście, które należy podjąć, zależy od poziomu komfortu i podejść.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-190">Which approach you should take is determined by your comfort level with the approaches and trade-offs in complexity.</span></span> <span data-ttu-id="8c1f0-191">Program MSBuild umożliwia wyrażanie procesu kompilacji jako zadań i obiektów docelowych, ale zawiera dodaną złożoność uczenia składni pliku projektu programu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-191">MSBuild provides you the ability to express your build process as tasks and targets, but it comes with the added complexity of learning MSBuild project file syntax.</span></span> <span data-ttu-id="8c1f0-192">Korzystanie z narzędzi wiersza polecenia platformy .NET Core może być prostsze, ale wymaga to zapisania logiki aranżacji w języku skryptowym, takim jak `bash` lub PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8c1f0-192">Using the .NET Core command-line tools is perhaps simpler, but it requires you to write orchestration logic in a scripting language like `bash` or PowerShell.</span></span>

## <a name="see-also"></a><span data-ttu-id="8c1f0-193">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8c1f0-193">See also</span></span>

- [<span data-ttu-id="8c1f0-194">Pliki do pobrania dla platformy .NET — Linux</span><span class="sxs-lookup"><span data-stu-id="8c1f0-194">.NET downloads - Linux</span></span>](https://dotnet.microsoft.com/download?initial-os=linux)

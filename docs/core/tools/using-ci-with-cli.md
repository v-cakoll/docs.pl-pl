---
title: Przy użyciu zestawu SDK programu .NET Core i narzędzi w ciągłej integracji (CI)
description: Informacje na temat użycia .NET Core SDK i jej narzędzi na serwerze kompilacji.
author: guardrex
ms.author: mairaw
ms.date: 05/18/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 76165b515bace71ca9269e587a817876c0e9eecf
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="using-net-core-sdk-and-tools-in-continuous-integration-ci"></a><span data-ttu-id="1f314-103">Przy użyciu zestawu SDK programu .NET Core i narzędzi w ciągłej integracji (CI)</span><span class="sxs-lookup"><span data-stu-id="1f314-103">Using .NET Core SDK and tools in Continuous Integration (CI)</span></span>

## <a name="overview"></a><span data-ttu-id="1f314-104">Omówienie</span><span class="sxs-lookup"><span data-stu-id="1f314-104">Overview</span></span>

<span data-ttu-id="1f314-105">W tym dokumencie przedstawiono przy użyciu zestawu SDK .NET Core i jej narzędzi na serwerze kompilacji.</span><span class="sxs-lookup"><span data-stu-id="1f314-105">This document outlines using the .NET Core SDK and its tools on a build server.</span></span> <span data-ttu-id="1f314-106">Oprogramowanie .NET Core zestawu narzędzi działa zarówno interaktywnego, gdzie projektant typów poleceń w poleceniu Monituj i automatycznie, w przypadku, gdy serwer ciągłej integracji (CI) uruchamia skrypt kompilacji.</span><span class="sxs-lookup"><span data-stu-id="1f314-106">The .NET Core toolset works both interactively, where a developer types commands at a command prompt, and automatically, where a Continuous Integration (CI) server runs a build script.</span></span> <span data-ttu-id="1f314-107">Polecenia, opcje, danych wejściowych i wyjściowych są takie same, a tylko czynności, które należy podać są sposobem uzyskania narzędzi i systemu do utworzenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1f314-107">The commands, options, inputs, and outputs are the same, and the only things you supply are a way to acquire the tooling and a system to build your app.</span></span> <span data-ttu-id="1f314-108">Ten dokument koncentruje się na scenariuszach nabycia narzędzia dla elementu konfiguracji z zaleceniami dotyczącymi projektowania i definiowania struktury skrypty kompilacji.</span><span class="sxs-lookup"><span data-stu-id="1f314-108">This document focuses on scenarios of tool acquisition for CI with recommendations on how to design and structure your build scripts.</span></span>

## <a name="installation-options-for-ci-build-servers"></a><span data-ttu-id="1f314-109">Opcje instalacji dla elementu konfiguracji kompilacji serwerów</span><span class="sxs-lookup"><span data-stu-id="1f314-109">Installation options for CI build servers</span></span>

### <a name="using-the-native-installers"></a><span data-ttu-id="1f314-110">Za pomocą natywnego instalatorów</span><span class="sxs-lookup"><span data-stu-id="1f314-110">Using the native installers</span></span>

<span data-ttu-id="1f314-111">Natywny instalatorów są dostępne dla macOS, Linux i Windows.</span><span class="sxs-lookup"><span data-stu-id="1f314-111">Native installers are available for macOS, Linux, and Windows.</span></span> <span data-ttu-id="1f314-112">Pliki instalacyjne wymagają dostępu administracyjnego (sudo) do serwera kompilacji.</span><span class="sxs-lookup"><span data-stu-id="1f314-112">The installers require admin (sudo) access to the build server.</span></span> <span data-ttu-id="1f314-113">Zaletą za pomocą natywnego Instalatora jest, że instaluje wszystkie natywnego zależności wymagane dla narzędzi do uruchomienia.</span><span class="sxs-lookup"><span data-stu-id="1f314-113">The advantage of using a native installer is that it installs all of the native dependencies required for the tooling to run.</span></span> <span data-ttu-id="1f314-114">Natywny instalatorów zapewniają także instalację systemowe zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="1f314-114">Native installers also provide a system-wide installation of the SDK.</span></span>

<span data-ttu-id="1f314-115">System macOS użytkownicy powinni używać instalatorów PKG.</span><span class="sxs-lookup"><span data-stu-id="1f314-115">macOS users should use the PKG installers.</span></span> <span data-ttu-id="1f314-116">W systemie Linux Brak wyboru przy użyciu Menedżera pakietu na podstawie źródła danych, takich jak stanie get dla Ubuntu lub yum dla CentOS, lub pakietów, DEB lub obr. / min.</span><span class="sxs-lookup"><span data-stu-id="1f314-116">On Linux, there's a choice of using a feed-based package manager, such as apt-get for Ubuntu or yum for CentOS, or using the packages themselves, DEB or RPM.</span></span> <span data-ttu-id="1f314-117">W systemie Windows użyj Instalatora MSI.</span><span class="sxs-lookup"><span data-stu-id="1f314-117">On Windows, use the MSI installer.</span></span>

<span data-ttu-id="1f314-118">Stabilna najnowsze pliki binarne znajdują się w [Rozpoczynanie pracy z platformą .NET Core](https://aka.ms/dotnetcoregs).</span><span class="sxs-lookup"><span data-stu-id="1f314-118">The latest stable binaries are found at [Get Started with .NET Core](https://aka.ms/dotnetcoregs).</span></span> <span data-ttu-id="1f314-119">Jeśli chcesz użyć narzędzia wstępną najnowsze (i potencjalnie niestabilny), użyj linków dostępnych na [repozytorium GitHub dotnet/cli](https://github.com/dotnet/cli#installers-and-binaries).</span><span class="sxs-lookup"><span data-stu-id="1f314-119">If you wish to use the latest (and potentially unstable) pre-release tooling, use the links provided at the [dotnet/cli GitHub repository](https://github.com/dotnet/cli#installers-and-binaries).</span></span> <span data-ttu-id="1f314-120">Dystrybucje systemu Linux, aby uzyskać `tar.gz` archiwów (znanej także jako `tarballs`) są dostępne, zainstaluj oprogramowanie .NET Core przy użyciu skryptów instalacji w archiwum.</span><span class="sxs-lookup"><span data-stu-id="1f314-120">For Linux distributions, `tar.gz` archives (also known as `tarballs`) are available; use the installation scripts within the archives to install .NET Core.</span></span>

### <a name="using-the-installer-script"></a><span data-ttu-id="1f314-121">Przy użyciu skryptu Instalatora</span><span class="sxs-lookup"><span data-stu-id="1f314-121">Using the installer script</span></span>

<span data-ttu-id="1f314-122">Przy użyciu skryptu Instalatora umożliwia innych niż administracyjne instalacji serwera kompilacji i łatwe automatyzacji do uzyskania narzędzi.</span><span class="sxs-lookup"><span data-stu-id="1f314-122">Using the installer script allows for non-administrative installation on your build server and easy automation for obtaining the tooling.</span></span> <span data-ttu-id="1f314-123">Skrypt zapewnia obsługę narzędzia pobierania i wyodrębnij go do domyślnej lub określonej lokalizacji do użycia.</span><span class="sxs-lookup"><span data-stu-id="1f314-123">The script takes care of downloading the tooling and extracting it into a default or specified location for use.</span></span> <span data-ttu-id="1f314-124">Można również określić wersję narzędzi, które mają zostać zainstalowane i czy chcesz zainstalować całego zestawu SDK lub tylko udostępnionego środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="1f314-124">You can also specify a version of the tooling that you wish to install and whether you want to install the entire SDK or only the shared runtime.</span></span>

<span data-ttu-id="1f314-125">Skrypt Instalatora jest automatyczne uruchamianie na początku kompilacji, aby pobrać i zainstalować odpowiednią wersję zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="1f314-125">The installer script is automated to run at the start of the build to fetch and install the desired version of the SDK.</span></span> <span data-ttu-id="1f314-126">*Żądanej wersji* jest niezależnie od wersji zestawu SDK dla projektów wymagają kompilacji.</span><span class="sxs-lookup"><span data-stu-id="1f314-126">The *desired version* is whatever version of the SDK your projects require to build.</span></span> <span data-ttu-id="1f314-127">Skrypt umożliwia instalowanie zestawu SDK w katalogu lokalnym na serwerze, uruchamiania narzędzi z lokalizacji zainstalowanych i wyczyścić (a lub zezwolić CI, wyczyść) po kompilacji.</span><span class="sxs-lookup"><span data-stu-id="1f314-127">The script allows you to install the SDK in a local directory on the server, run the tools from the installed location, and then clean up (or let the CI service clean up) after the build.</span></span> <span data-ttu-id="1f314-128">Zapewnia hermetyzację i izolacja do całego procesu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="1f314-128">This provides encapsulation and isolation to your entire build process.</span></span> <span data-ttu-id="1f314-129">Odwołanie do skryptu instalacji znajduje się w [instalacji dotnet](dotnet-install-script.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="1f314-129">The installation script reference is found in the [dotnet-install](dotnet-install-script.md) topic.</span></span>

> [!NOTE]
> <span data-ttu-id="1f314-130">Przy użyciu skryptu Instalatora, natywnego zależności nie są instalowane automatycznie.</span><span class="sxs-lookup"><span data-stu-id="1f314-130">When using the installer script, native dependencies aren't installed automatically.</span></span> <span data-ttu-id="1f314-131">Jeśli system operacyjny nie ma ich, należy zainstalować natywnej zależności.</span><span class="sxs-lookup"><span data-stu-id="1f314-131">You must install the native dependencies if the operating system doesn't have them.</span></span> <span data-ttu-id="1f314-132">Zobacz listę warunków wstępnych w [natywnego wymagania wstępne platformy .NET Core](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="1f314-132">See the list of prerequisites in the [.NET Core native prerequisites](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md) topic.</span></span>

## <a name="ci-setup-examples"></a><span data-ttu-id="1f314-133">Przykłady ustawień elementu konfiguracji</span><span class="sxs-lookup"><span data-stu-id="1f314-133">CI setup examples</span></span>

<span data-ttu-id="1f314-134">W tej sekcji opisano instalacji ręcznej, za pomocą skryptu programu PowerShell lub bash, wraz z opisami kilka oprogramowania jako rozwiązania CI usługa (SaaS).</span><span class="sxs-lookup"><span data-stu-id="1f314-134">This section describes a manual setup using a PowerShell or bash script, along with a description of several software as a service (SaaS) CI solutions.</span></span> <span data-ttu-id="1f314-135">Rozwiązania SaaS CI omówione są [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), i [programu Visual Studio Team Services Build](https://docs.microsoft.com/vsts/build-release/index).</span><span class="sxs-lookup"><span data-stu-id="1f314-135">The SaaS CI solutions covered are [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), and [Visual Studio Team Services Build](https://docs.microsoft.com/vsts/build-release/index).</span></span>

### <a name="manual-setup"></a><span data-ttu-id="1f314-136">Instalacji ręcznej</span><span class="sxs-lookup"><span data-stu-id="1f314-136">Manual setup</span></span>

<span data-ttu-id="1f314-137">Każda usługa SaaS ma własną metod tworzenia i konfigurowania procesu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="1f314-137">Each SaaS service has its own methods for creating and configuring a build process.</span></span> <span data-ttu-id="1f314-138">Jeśli za pomocą innego rozwiązania SaaS niż wymienione lub wymagają dostosowania poza opakowanych pomocy technicznej, należy wykonać co najmniej pewne czynności konfiguracyjne.</span><span class="sxs-lookup"><span data-stu-id="1f314-138">If you use different SaaS solution than those listed or require customization beyond the pre-packaged support, you must perform at least some manual configuration.</span></span>

<span data-ttu-id="1f314-139">Ogólnie rzecz biorąc instalacji ręcznej należy uzyskać wersji narzędzi (lub kompilacje co noc najnowsza wersja narzędzi) i uruchomić skrypt kompilacji.</span><span class="sxs-lookup"><span data-stu-id="1f314-139">In general, a manual setup requires you to acquire a version of the tools (or the latest nightly builds of the tools) and run your build script.</span></span> <span data-ttu-id="1f314-140">Można użyć programu PowerShell lub bash skrypt służący do organizowania poleceń .NET Core lub użyć pliku projektu, który zawiera opis procesu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="1f314-140">You can use a PowerShell or bash script to orchestrate the .NET Core commands or use a project file that outlines the build process.</span></span> <span data-ttu-id="1f314-141">[Sekcji aranżacji](#orchestrating-the-build) zawiera więcej szczegółów na temat tych opcji.</span><span class="sxs-lookup"><span data-stu-id="1f314-141">The [orchestration section](#orchestrating-the-build) provides more detail on these options.</span></span>

<span data-ttu-id="1f314-142">Po utworzeniu skrypt, który wykonuje ręcznego CI Tworzenie instalacji serwera, użyj go na komputerze deweloperskim, aby skompilować kod lokalnie do celów testowych.</span><span class="sxs-lookup"><span data-stu-id="1f314-142">After you create a script that performs a manual CI build server setup, use it on your dev machine to build your code locally for testing purposes.</span></span> <span data-ttu-id="1f314-143">Po upewnieniu się, że skrypt jest uruchamiany oraz lokalnie, wdrożyć ją do serwera kompilacji elementu konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="1f314-143">Once you confirm that the script is running well locally, deploy it to your CI build server.</span></span> <span data-ttu-id="1f314-144">Stosunkowo proste skrypt programu PowerShell pokazano, jak uzyskać .NET Core SDK i zainstalować go na serwerze kompilacji systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="1f314-144">A relatively simple PowerShell script demonstrates how to obtain the .NET Core SDK and install it on a Windows build server:</span></span>

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

<span data-ttu-id="1f314-145">Musisz podać wykonania procesu kompilacji na końcu skryptu.</span><span class="sxs-lookup"><span data-stu-id="1f314-145">You provide the implementation for your build process at the end of the script.</span></span> <span data-ttu-id="1f314-146">Skrypt uzyskuje narzędzia, a następnie wykonuje procesu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="1f314-146">The script acquires the tools and then executes your build process.</span></span> <span data-ttu-id="1f314-147">Na komputerach UNIX poniższy skrypt bash wykonuje czynności opisane w skrypcie programu PowerShell w podobny sposób:</span><span class="sxs-lookup"><span data-stu-id="1f314-147">For UNIX machines, the following bash script performs the actions described in the PowerShell script in a similar manner:</span></span>

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

### <a name="travis-ci"></a><span data-ttu-id="1f314-148">Travis elementu konfiguracji</span><span class="sxs-lookup"><span data-stu-id="1f314-148">Travis CI</span></span>

<span data-ttu-id="1f314-149">Można skonfigurować [Travis CI](https://travis-ci.org/) zainstalować za pomocą zestawu SDK programu .NET Core `csharp` języka i `dotnet` klucza.</span><span class="sxs-lookup"><span data-stu-id="1f314-149">You can configure [Travis CI](https://travis-ci.org/) to install the .NET Core SDK using the `csharp` language and the `dotnet` key.</span></span> <span data-ttu-id="1f314-150">Zobacz oficjalna dokumentacja Travis CI na [tworzenia C#, F # lub Visual Basic projektu](https://docs.travis-ci.com/user/languages/csharp/) Aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="1f314-150">See the official Travis CI docs on [Building a C#, F#, or Visual Basic Project](https://docs.travis-ci.com/user/languages/csharp/) for more information.</span></span> <span data-ttu-id="1f314-151">Należy zwrócić uwagę, jak dostęp do informacji Travis CI który Wspólnotę utrzymane `language: csharp` identyfikator języka działa dla wszystkich języków .NET, w tym F # i Mono.</span><span class="sxs-lookup"><span data-stu-id="1f314-151">Note as you access the Travis CI information that the community-maintained `language: csharp` language identifier works for all .NET languages, including F#, and Mono.</span></span>

<span data-ttu-id="1f314-152">Travis CI działa zarówno system macOS (OS X 10.11, OS X 10.12) i systemu Linux (Ubuntu 14.04) zadania w *kompilacji macierzy*, gdzie Określ kombinację środowiska uruchomieniowego, środowiska i wykluczenia/dołączenia, aby pokrywał się z kombinacji kompilacji dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1f314-152">Travis CI runs both macOS (OS X 10.11, OS X 10.12) and Linux (Ubuntu 14.04) jobs in a *build matrix*, where you specify a combination of runtime, environment, and exclusions/inclusions to cover your build combinations for your app.</span></span> <span data-ttu-id="1f314-153">Zobacz [. przykład travis.yml](https://github.com/dotnet/docs/blob/master/.travis.yml) pliku i [Dostosowywanie kompilacji](https://docs.travis-ci.com/user/customizing-the-build) w docs Travis CI, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="1f314-153">See the [.travis.yml example](https://github.com/dotnet/docs/blob/master/.travis.yml) file and [Customizing the Build](https://docs.travis-ci.com/user/customizing-the-build) in the Travis CI docs for more information.</span></span> <span data-ttu-id="1f314-154">Narzędzia MSBuild zawiera LTS (1.0.x) i bieżącego środowiska uruchomieniowe (1.1.x) w pakiecie; Dzięki przez zainstalowanie zestawu SDK, pojawi się wszystko, co jest potrzebne do tworzenia.</span><span class="sxs-lookup"><span data-stu-id="1f314-154">The MSBuild-based tools include the LTS (1.0.x) and Current (1.1.x) runtimes in the package; so by installing the SDK, you receive everything you need to build.</span></span>

### <a name="appveyor"></a><span data-ttu-id="1f314-155">AppVeyor</span><span class="sxs-lookup"><span data-stu-id="1f314-155">AppVeyor</span></span>

<span data-ttu-id="1f314-156">[AppVeyor](https://www.appveyor.com/) instaluje oprogramowanie .NET Core 1.0.1 SDK z `Visual Studio 2017` utworzyć obraz procesu roboczego.</span><span class="sxs-lookup"><span data-stu-id="1f314-156">[AppVeyor](https://www.appveyor.com/) installs the .NET Core 1.0.1 SDK with the `Visual Studio 2017` build worker image.</span></span> <span data-ttu-id="1f314-157">Inne obrazy kompilacji różne wersje programu .NET Core SDK są dostępne; zobacz [przykład appveyor.yml](https://github.com/dotnet/docs/blob/master/appveyor.yml) i [tworzyć obrazy procesu roboczego](https://www.appveyor.com/docs/build-environment/#build-worker-images) tematu w docs AppVeyor, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="1f314-157">Other build images with different versions of the .NET Core SDK are available; see the [appveyor.yml example](https://github.com/dotnet/docs/blob/master/appveyor.yml) and the [Build worker images](https://www.appveyor.com/docs/build-environment/#build-worker-images) topic in the AppVeyor docs for more information.</span></span>

<span data-ttu-id="1f314-158">Pliki binarne .NET Core SDK są pobierane i rozpakowane w podkatalogu przy użyciu skryptu instalacji, a następnie jest dodawana do `PATH` zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="1f314-158">The .NET Core SDK binaries are downloaded and unzipped in a subdirectory using the install script, and then they're added to the `PATH` environment variable.</span></span> <span data-ttu-id="1f314-159">Dodanie macierzy kompilację do uruchomienia testów integracji z wieloma wersjami programu .NET Core SDK:</span><span class="sxs-lookup"><span data-stu-id="1f314-159">Add a build matrix to run integration tests with multiple versions of the .NET Core SDK:</span></span>

```yaml
environment:
  matrix:
    - CLI_VERSION: 1.0.1
    - CLI_VERSION: Latest

install:
  # See appveyor.yml example for install script
```

### <a name="visual-studio-team-services-vsts"></a><span data-ttu-id="1f314-160">Visual Studio Team Services (VSTS)</span><span class="sxs-lookup"><span data-stu-id="1f314-160">Visual Studio Team Services (VSTS)</span></span>

<span data-ttu-id="1f314-161">Konfigurowanie programu Visual Studio Team Services (VSTS) do tworzenia projektów .NET Core przy użyciu jednej z tych metod:</span><span class="sxs-lookup"><span data-stu-id="1f314-161">Configure Visual Studio Team Services (VSTS) to build .NET Core projects using one of these approaches:</span></span>

1. <span data-ttu-id="1f314-162">Uruchom skrypt z [krok instalacji ręcznej](#manual-setup) przy użyciu poleceń.</span><span class="sxs-lookup"><span data-stu-id="1f314-162">Run the script from the [manual setup step](#manual-setup) using your commands.</span></span>
1. <span data-ttu-id="1f314-163">Utwórz kompilację składa się z kilka zadań programu VSTS wbudowanych kompilacji, które są skonfigurowane do używania narzędzi platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1f314-163">Create a build composed of several VSTS built-in build tasks that are configured to use .NET Core tools.</span></span>

<span data-ttu-id="1f314-164">Oba rozwiązania są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="1f314-164">Both solutions are valid.</span></span> <span data-ttu-id="1f314-165">Przy użyciu skryptu instalacji ręcznej, możesz kontrolować wersji narzędzia, które zostanie wyświetlone, ponieważ możesz pobrać jako część kompilacji.</span><span class="sxs-lookup"><span data-stu-id="1f314-165">Using a manual setup script, you control the version of the tools that you receive, since you download them as part of the build.</span></span> <span data-ttu-id="1f314-166">Kompilacja jest uruchamiana skrypt, który należy utworzyć.</span><span class="sxs-lookup"><span data-stu-id="1f314-166">The build is run from a script that you must create.</span></span> <span data-ttu-id="1f314-167">W tym temacie omówiono tylko opcja ręcznego odbierania.</span><span class="sxs-lookup"><span data-stu-id="1f314-167">This topic only covers the manual option.</span></span> <span data-ttu-id="1f314-168">Aby uzyskać więcej informacji na temat tworzenia kompilacji z programu VSTS zadania kompilacji, odwiedź witrynę programu VSTS [ciągłej integracji i wdrażania](https://docs.microsoft.com/vsts/build-release/index) tematu.</span><span class="sxs-lookup"><span data-stu-id="1f314-168">For more information on composing a build with VSTS build tasks, visit the VSTS [Continuous integration and deployment](https://docs.microsoft.com/vsts/build-release/index) topic.</span></span>

<span data-ttu-id="1f314-169">Aby użyć skryptu instalacji ręcznej w VSTS, Utwórz nową definicję kompilacji i określ skrypt do uruchomienia kroku kompilacji.</span><span class="sxs-lookup"><span data-stu-id="1f314-169">To use a manual setup script in VSTS, create a new build definition and specify the script to run for the build step.</span></span> <span data-ttu-id="1f314-170">Jest to realizowane przy użyciu interfejsu użytkownika programu VSTS:</span><span class="sxs-lookup"><span data-stu-id="1f314-170">This is accomplished using the VSTS user interface:</span></span>

1. <span data-ttu-id="1f314-171">Rozpocznij od utworzenia nowej definicji kompilacji.</span><span class="sxs-lookup"><span data-stu-id="1f314-171">Start by creating a new build definition.</span></span> <span data-ttu-id="1f314-172">Po osiągnięciu ekranu, która udostępnia opcję, aby określić, jaki rodzaj kompilacji chcesz utworzyć, wybierz opcję **pusty** opcji.</span><span class="sxs-lookup"><span data-stu-id="1f314-172">Once you reach the screen that provides you an option to define what kind of a build you wish to create, select the **Empty** option.</span></span>

   ![Wybieranie definicji kompilacji pusty](./media/using-ci-with-cli/screen1.png)

1. <span data-ttu-id="1f314-174">Po skonfigurowaniu repozytorium do kompilacji, są kierowane do definicji kompilacji.</span><span class="sxs-lookup"><span data-stu-id="1f314-174">After configuring the repository to build, you're directed to the build definitions.</span></span> <span data-ttu-id="1f314-175">Wybierz **kroku kompilacji Dodaj**:</span><span class="sxs-lookup"><span data-stu-id="1f314-175">Select **Add build step**:</span></span>

   ![Dodawanie kroku kompilacji](./media/using-ci-with-cli/screen2.png)

1. <span data-ttu-id="1f314-177">Aby wyświetlić dostępne **katalogu zadania**.</span><span class="sxs-lookup"><span data-stu-id="1f314-177">You're presented with the **Task catalog**.</span></span> <span data-ttu-id="1f314-178">Katalog zawiera zadania, których można użyć w kompilacji.</span><span class="sxs-lookup"><span data-stu-id="1f314-178">The catalog contains tasks that you use in the build.</span></span> <span data-ttu-id="1f314-179">Ponieważ masz skryptu, wybierz opcję **Dodaj** przycisk dla **środowiska PowerShell: Uruchom skrypt programu PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="1f314-179">Since you have a script, select the **Add** button for **PowerShell: Run a PowerShell script**.</span></span>

   ![Dodawanie etapu skryptu PowerShell](./media/using-ci-with-cli/screen3.png)

1. <span data-ttu-id="1f314-181">Skonfiguruj kroku kompilacji.</span><span class="sxs-lookup"><span data-stu-id="1f314-181">Configure the build step.</span></span> <span data-ttu-id="1f314-182">Dodaj skrypt z repozytorium, które tworzysz:</span><span class="sxs-lookup"><span data-stu-id="1f314-182">Add the script from the repository that you're building:</span></span>

   ![Określanie uruchomienie skryptu programu PowerShell](./media/using-ci-with-cli/screen4.png)

## <a name="orchestrating-the-build"></a><span data-ttu-id="1f314-184">Organizowanie kompilacji</span><span class="sxs-lookup"><span data-stu-id="1f314-184">Orchestrating the build</span></span>

<span data-ttu-id="1f314-185">Większość ten dokument zawiera opis sposobu uzyskania narzędzia .NET Core i konfigurowanie różnych usług CI bez podawania informacji na temat sposobu organizowania, lub *zbudowaniem*, kodu za pomocą platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1f314-185">Most of this document describes how to acquire the .NET Core tools and configure various CI services without providing information on how to orchestrate, or *actually build*, your code with .NET Core.</span></span> <span data-ttu-id="1f314-186">Opcje dostępne na struktury procesu kompilacji są zależne od wielu czynników, w których nie można w sposób ogólny, w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="1f314-186">The choices on how to structure the build process depend on many factors that cannot be covered in a general way here.</span></span> <span data-ttu-id="1f314-187">Eksploruj zasobów i przykłady podane w dokumentacji zestawy [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), i [VSTS](https://docs.microsoft.com/vsts/build-release/index) uzyskać więcej informacji o kompilacji z każdym organizowanie Technologia.</span><span class="sxs-lookup"><span data-stu-id="1f314-187">Explore the resources and samples provided in the documentation sets of [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), and [VSTS](https://docs.microsoft.com/vsts/build-release/index) for more information on orchestrating your builds with each technology.</span></span>

<span data-ttu-id="1f314-188">Dwa podejścia ogólnych, które wykonujesz w struktury procesu kompilacji dla kodu platformy .NET Core za pomocą narzędzi platformy .NET Core są bezpośrednio za pomocą programu MSBuild lub przy użyciu poleceń wiersza polecenia platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1f314-188">Two general approaches that you take in structuring the build process for .NET Core code using the .NET Core tools are using MSBuild directly or using the .NET Core command-line commands.</span></span> <span data-ttu-id="1f314-189">Podejście, które należy podjąć jest określana przez poziom komfort z podejścia i kompromisy złożonością.</span><span class="sxs-lookup"><span data-stu-id="1f314-189">Which approach you should take is determined by your comfort level with the approaches and trade-offs in complexity.</span></span> <span data-ttu-id="1f314-190">MSBuild zapewnia możliwość express procesu kompilacji jako zadań i elementów docelowych, ale ma dodany złożoność uczenia składni pliku projektu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="1f314-190">MSBuild provides you the ability to express your build process as tasks and targets, but it comes with the added complexity of learning MSBuild project file syntax.</span></span> <span data-ttu-id="1f314-191">Za pomocą narzędzia wiersza polecenia platformy .NET Core prawdopodobnie jest prostsze, ale wymaga do pisania logiki aranżacji w języku skryptów, takich jak `bash` lub programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1f314-191">Using the .NET Core command-line tools is perhaps simpler, but it requires you to write orchestration logic in a scripting language like `bash` or PowerShell.</span></span>

## <a name="see-also"></a><span data-ttu-id="1f314-192">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1f314-192">See also</span></span>

[<span data-ttu-id="1f314-193">Ubuntu nabycia kroki</span><span class="sxs-lookup"><span data-stu-id="1f314-193">Ubuntu acquisition steps</span></span>](https://www.microsoft.com/net/core#linuxubuntu)   

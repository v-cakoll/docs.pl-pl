---
title: Przy użyciu zestawu .NET Core SDK i narzędzi w ciągłej integracji (CI)
description: Informacje na temat użycia programu .NET Core SDK i jego narzędzi na serwerze kompilacji.
author: mairaw
ms.date: 05/18/2017
ms.custom: seodec18
ms.openlocfilehash: 629b7a9e1f2b59981adb77ab4d3125be7036ff02
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66299972"
---
# <a name="using-net-core-sdk-and-tools-in-continuous-integration-ci"></a><span data-ttu-id="4208b-103">Przy użyciu zestawu .NET Core SDK i narzędzi w ciągłej integracji (CI)</span><span class="sxs-lookup"><span data-stu-id="4208b-103">Using .NET Core SDK and tools in Continuous Integration (CI)</span></span>

<span data-ttu-id="4208b-104">W tym dokumencie przedstawiono przy użyciu zestawu .NET Core SDK i jego narzędzi na serwerze kompilacji.</span><span class="sxs-lookup"><span data-stu-id="4208b-104">This document outlines using the .NET Core SDK and its tools on a build server.</span></span> <span data-ttu-id="4208b-105">.NET Core narzędzi działa zarówno interaktywnie, gdzie deweloper typów poleceń w poleceniu monit i automatycznie w przypadku, gdy serwer ciągłej integracji (CI) uruchamia skrypt kompilacji.</span><span class="sxs-lookup"><span data-stu-id="4208b-105">The .NET Core toolset works both interactively, where a developer types commands at a command prompt, and automatically, where a Continuous Integration (CI) server runs a build script.</span></span> <span data-ttu-id="4208b-106">Poleceń, opcje, dane wejściowe i wyjściowe są takie same, a tylko rzeczy, które podasz służą do nabycia narzędzi i systemu do kompilowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4208b-106">The commands, options, inputs, and outputs are the same, and the only things you supply are a way to acquire the tooling and a system to build your app.</span></span> <span data-ttu-id="4208b-107">Ten dokument koncentruje się na scenariuszach nabycia narzędzi do ciągłej integracji z zaleceniami dotyczącymi projektowania i struktury skrypty kompilacji.</span><span class="sxs-lookup"><span data-stu-id="4208b-107">This document focuses on scenarios of tool acquisition for CI with recommendations on how to design and structure your build scripts.</span></span>

## <a name="installation-options-for-ci-build-servers"></a><span data-ttu-id="4208b-108">Opcje instalacji dla ciągłej integracji, serwerów kompilacji</span><span class="sxs-lookup"><span data-stu-id="4208b-108">Installation options for CI build servers</span></span>

### <a name="using-the-native-installers"></a><span data-ttu-id="4208b-109">Przy użyciu natywnych instalatorów</span><span class="sxs-lookup"><span data-stu-id="4208b-109">Using the native installers</span></span>

<span data-ttu-id="4208b-110">Natywnych instalatorów są dostępne dla systemu macOS, Linux i Windows.</span><span class="sxs-lookup"><span data-stu-id="4208b-110">Native installers are available for macOS, Linux, and Windows.</span></span> <span data-ttu-id="4208b-111">Pliki instalacyjne wymagają dostępu administratora ("sudo") do serwera kompilacji.</span><span class="sxs-lookup"><span data-stu-id="4208b-111">The installers require admin (sudo) access to the build server.</span></span> <span data-ttu-id="4208b-112">Zalet za pomocą natywnego Instalatora jest, że instaluje wszystkie zależności natywnych wymaganych narzędzi do uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="4208b-112">The advantage of using a native installer is that it installs all of the native dependencies required for the tooling to run.</span></span> <span data-ttu-id="4208b-113">Natywnych instalatorów oferują również systemowe instalacji zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="4208b-113">Native installers also provide a system-wide installation of the SDK.</span></span>

<span data-ttu-id="4208b-114">użytkowników systemu macOS należy używać programów instalacyjnych pakietu.</span><span class="sxs-lookup"><span data-stu-id="4208b-114">macOS users should use the PKG installers.</span></span> <span data-ttu-id="4208b-115">W systemie Linux, wybór jest przy użyciu Menedżera pakietów na podstawie źródła danych, takich jak polecenia apt-get dla systemu Ubuntu lub yum, centos, lub za pomocą pakietów, Mistrzostwo DEB lub obr. / min.</span><span class="sxs-lookup"><span data-stu-id="4208b-115">On Linux, there's a choice of using a feed-based package manager, such as apt-get for Ubuntu or yum for CentOS, or using the packages themselves, DEB or RPM.</span></span> <span data-ttu-id="4208b-116">W Windows użyj Instalatora MSI.</span><span class="sxs-lookup"><span data-stu-id="4208b-116">On Windows, use the MSI installer.</span></span>

<span data-ttu-id="4208b-117">Najnowsze stabilne pliki binarne znajdują się w [pobiera .NET](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="4208b-117">The latest stable binaries are found at [.NET downloads](https://dotnet.microsoft.com/download).</span></span> <span data-ttu-id="4208b-118">Jeśli chcesz użyć narzędzi najnowsze (i potencjalnie niestabilne) w wersji wstępnej, należy użyć linków dostępnych na [repozytorium dotnet/core-sdk w witrynie GitHub](https://github.com/dotnet/core-sdk#installers-and-binaries).</span><span class="sxs-lookup"><span data-stu-id="4208b-118">If you wish to use the latest (and potentially unstable) pre-release tooling, use the links provided at the [dotnet/core-sdk GitHub repository](https://github.com/dotnet/core-sdk#installers-and-binaries).</span></span> <span data-ttu-id="4208b-119">Dystrybucje systemu Linux `tar.gz` archiwów (znany także jako `tarballs`) są dostępne; Instalowanie programu .NET Core za pomocą skryptów instalacji, w archiwum.</span><span class="sxs-lookup"><span data-stu-id="4208b-119">For Linux distributions, `tar.gz` archives (also known as `tarballs`) are available; use the installation scripts within the archives to install .NET Core.</span></span>

### <a name="using-the-installer-script"></a><span data-ttu-id="4208b-120">Przy użyciu skryptu Instalatora</span><span class="sxs-lookup"><span data-stu-id="4208b-120">Using the installer script</span></span>

<span data-ttu-id="4208b-121">Przy użyciu skryptu Instalatora umożliwia innych niż administracyjne instalacji na serwerze kompilacji i łatwe uzyskiwanie narzędzi automatyzacji.</span><span class="sxs-lookup"><span data-stu-id="4208b-121">Using the installer script allows for non-administrative installation on your build server and easy automation for obtaining the tooling.</span></span> <span data-ttu-id="4208b-122">Skrypt dba o pobranie narzędzi i wyodrębnij go do domyślnej lub określonej lokalizacji do użycia.</span><span class="sxs-lookup"><span data-stu-id="4208b-122">The script takes care of downloading the tooling and extracting it into a default or specified location for use.</span></span> <span data-ttu-id="4208b-123">Można również określić wersję narzędzia, które mają zostać zainstalowane i czy chcesz zainstalować całego zestawu SDK lub tylko udostępnionego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="4208b-123">You can also specify a version of the tooling that you wish to install and whether you want to install the entire SDK or only the shared runtime.</span></span>

<span data-ttu-id="4208b-124">Skrypt Instalatora jest zautomatyzowany do uruchomienia na początku kompilacji, aby pobrać i zainstalować odpowiednią wersję zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="4208b-124">The installer script is automated to run at the start of the build to fetch and install the desired version of the SDK.</span></span> <span data-ttu-id="4208b-125">*Żądaną wersję* jest niezależnie od wersji zestawu SDK swoje projekty wymagają do kompilacji.</span><span class="sxs-lookup"><span data-stu-id="4208b-125">The *desired version* is whatever version of the SDK your projects require to build.</span></span> <span data-ttu-id="4208b-126">Skrypt umożliwia zainstalowanie zestawu SDK w katalogu lokalnym na serwerze, uruchomić narzędzia w lokalizacji instalacji i wyczyścić (a lub zezwala na CI oczyszczania) po kompilacji.</span><span class="sxs-lookup"><span data-stu-id="4208b-126">The script allows you to install the SDK in a local directory on the server, run the tools from the installed location, and then clean up (or let the CI service clean up) after the build.</span></span> <span data-ttu-id="4208b-127">Zapewnia to, że hermetyzacji i izolacji całego procesu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="4208b-127">This provides encapsulation and isolation to your entire build process.</span></span> <span data-ttu-id="4208b-128">Odwołanie do skryptu instalacji znajduje się w [instalacji dotnet](dotnet-install-script.md) artykułu.</span><span class="sxs-lookup"><span data-stu-id="4208b-128">The installation script reference is found in the [dotnet-install](dotnet-install-script.md) article.</span></span>

> [!NOTE]
> <span data-ttu-id="4208b-129">**Azure DevOps Services**</span><span class="sxs-lookup"><span data-stu-id="4208b-129">**Azure DevOps Services**</span></span>
>
> <span data-ttu-id="4208b-130">Przy użyciu skryptu Instalatora, natywne zależności nie są instalowane automatycznie.</span><span class="sxs-lookup"><span data-stu-id="4208b-130">When using the installer script, native dependencies aren't installed automatically.</span></span> <span data-ttu-id="4208b-131">Musisz zainstalować zależności natywnych, jeśli system operacyjny nie ma ich.</span><span class="sxs-lookup"><span data-stu-id="4208b-131">You must install the native dependencies if the operating system doesn't have them.</span></span> <span data-ttu-id="4208b-132">Aby uzyskać więcej informacji, zobacz [wymagania wstępne dla platformy .NET Core w systemie Linux](../linux-prerequisites.md).</span><span class="sxs-lookup"><span data-stu-id="4208b-132">For more information, see [Prerequisites for .NET Core on Linux](../linux-prerequisites.md).</span></span>

## <a name="ci-setup-examples"></a><span data-ttu-id="4208b-133">Przykłady konfiguracji ciągłej integracji</span><span class="sxs-lookup"><span data-stu-id="4208b-133">CI setup examples</span></span>

<span data-ttu-id="4208b-134">W tej sekcji opisano instalację ręczną przy użyciu skryptu programu PowerShell lub bash, wraz z opisami kilka oprogramowania jako rozwiązania ciągłej integracji usługi (SaaS).</span><span class="sxs-lookup"><span data-stu-id="4208b-134">This section describes a manual setup using a PowerShell or bash script, along with a description of several software as a service (SaaS) CI solutions.</span></span> <span data-ttu-id="4208b-135">Rozwiązania SaaS CI omówione są [rozwiązania Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), i [potoki Azure](https://docs.microsoft.com/azure/devops/pipelines/index).</span><span class="sxs-lookup"><span data-stu-id="4208b-135">The SaaS CI solutions covered are [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), and [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index).</span></span>

### <a name="manual-setup"></a><span data-ttu-id="4208b-136">Instalacji ręcznej</span><span class="sxs-lookup"><span data-stu-id="4208b-136">Manual setup</span></span>

<span data-ttu-id="4208b-137">Każda usługa SaaS ma swoje własne metody tworzenia i konfigurowania procesu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="4208b-137">Each SaaS service has its own methods for creating and configuring a build process.</span></span> <span data-ttu-id="4208b-138">Jeśli używasz innego rozwiązania SaaS niż te wymienione, lub wymagać dostosowania poza obsługą wstępnie spakowanej, należy wykonać co najmniej pewne czynności konfiguracyjne.</span><span class="sxs-lookup"><span data-stu-id="4208b-138">If you use different SaaS solution than those listed or require customization beyond the pre-packaged support, you must perform at least some manual configuration.</span></span>

<span data-ttu-id="4208b-139">Ogólnie rzecz biorąc instalacji ręcznej należy uzyskać wersję narzędzia (lub nocnych najnowszej kompilacji narzędzi) i uruchomić skrypt kompilacji.</span><span class="sxs-lookup"><span data-stu-id="4208b-139">In general, a manual setup requires you to acquire a version of the tools (or the latest nightly builds of the tools) and run your build script.</span></span> <span data-ttu-id="4208b-140">Można użyć programu PowerShell lub bash skrypt służący do organizowania poleceń platformy .NET Core lub użyć pliku projektu, który zawiera omówienie procesu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="4208b-140">You can use a PowerShell or bash script to orchestrate the .NET Core commands or use a project file that outlines the build process.</span></span> <span data-ttu-id="4208b-141">[Sekcji aranżacji](#orchestrating-the-build) zapewnia więcej szczegółów na temat tych opcji.</span><span class="sxs-lookup"><span data-stu-id="4208b-141">The [orchestration section](#orchestrating-the-build) provides more detail on these options.</span></span>

<span data-ttu-id="4208b-142">Po utworzeniu skryptu, który wykonuje ręcznego CI build instalacji serwera, użyj go na komputerze deweloperskim do kompilacji kodu lokalnie do celów testowych.</span><span class="sxs-lookup"><span data-stu-id="4208b-142">After you create a script that performs a manual CI build server setup, use it on your dev machine to build your code locally for testing purposes.</span></span> <span data-ttu-id="4208b-143">Po upewnieniu się, czy skrypt działa dobrze lokalnie, wdrożyć serwer kompilacji ciągłej integracji.</span><span class="sxs-lookup"><span data-stu-id="4208b-143">Once you confirm that the script is running well locally, deploy it to your CI build server.</span></span> <span data-ttu-id="4208b-144">Stosunkowo prosty skrypt programu PowerShell pokazuje, jak uzyskać zestaw .NET Core SDK i zainstaluj go na serwerze kompilacji Windows:</span><span class="sxs-lookup"><span data-stu-id="4208b-144">A relatively simple PowerShell script demonstrates how to obtain the .NET Core SDK and install it on a Windows build server:</span></span>

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

<span data-ttu-id="4208b-145">Możesz podać implementacja dla procesu kompilacji na końcu skryptu.</span><span class="sxs-lookup"><span data-stu-id="4208b-145">You provide the implementation for your build process at the end of the script.</span></span> <span data-ttu-id="4208b-146">Skrypt uzyskuje narzędzia, a następnie uruchamia proces kompilacji.</span><span class="sxs-lookup"><span data-stu-id="4208b-146">The script acquires the tools and then executes your build process.</span></span> <span data-ttu-id="4208b-147">W przypadku komputerów UNIX poniższego skryptu powłoki systemowej wykonuje akcje opisane w skrypcie programu PowerShell w podobny sposób:</span><span class="sxs-lookup"><span data-stu-id="4208b-147">For UNIX machines, the following bash script performs the actions described in the PowerShell script in a similar manner:</span></span>

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

### <a name="travis-ci"></a><span data-ttu-id="4208b-148">Travis CI</span><span class="sxs-lookup"><span data-stu-id="4208b-148">Travis CI</span></span>

<span data-ttu-id="4208b-149">Można skonfigurować [rozwiązania Travis CI](https://travis-ci.org/) można zainstalować przy użyciu zestawu .NET Core SDK `csharp` języka i `dotnet` klucza.</span><span class="sxs-lookup"><span data-stu-id="4208b-149">You can configure [Travis CI](https://travis-ci.org/) to install the .NET Core SDK using the `csharp` language and the `dotnet` key.</span></span> <span data-ttu-id="4208b-150">Aby uzyskać więcej informacji, zobacz oficjalna dokumentacja rozwiązania Travis CI w [budynku C#, F#, lub projekcie Visual Basic](https://docs.travis-ci.com/user/languages/csharp/).</span><span class="sxs-lookup"><span data-stu-id="4208b-150">For more information, see the official Travis CI docs on [Building a C#, F#, or Visual Basic Project](https://docs.travis-ci.com/user/languages/csharp/).</span></span> <span data-ttu-id="4208b-151">Należy zauważyć, jak dostęp do informacji rozwiązania Travis CI, obsługiwane społeczności `language: csharp` identyfikator języka działa dla wszystkich języków .NET, w tym F#oraz Mono.</span><span class="sxs-lookup"><span data-stu-id="4208b-151">Note as you access the Travis CI information that the community-maintained `language: csharp` language identifier works for all .NET languages, including F#, and Mono.</span></span>

<span data-ttu-id="4208b-152">Rozwiązania Travis CI działa z systemem macOS i Linux zadań w *kompilacji macierzy*, gdzie należy określić kombinacji środowiska uruchomieniowego, środowiska i wyjątki/dołączenia do obejmują swojej kombinacji kompilacji dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="4208b-152">Travis CI runs both macOS and Linux jobs in a *build matrix*, where you specify a combination of runtime, environment, and exclusions/inclusions to cover your build combinations for your app.</span></span> <span data-ttu-id="4208b-153">Aby uzyskać więcej informacji, zobacz [dostosowywania kompilacji](https://docs.travis-ci.com/user/customizing-the-build) artykułu w dokumentacji rozwiązania Travis CI.</span><span class="sxs-lookup"><span data-stu-id="4208b-153">For more information, see the [Customizing the Build](https://docs.travis-ci.com/user/customizing-the-build) article in the Travis CI documentation.</span></span> <span data-ttu-id="4208b-154">Narzędzia oparte na MSBuild obejmują LTS (1.0.x) i bieżącego środowiska uruchomieniowe (1.1.x) w pakiecie; Dlatego po zainstalowaniu zestawu SDK, otrzymasz wszystko, czego potrzebujesz do tworzenia.</span><span class="sxs-lookup"><span data-stu-id="4208b-154">The MSBuild-based tools include the LTS (1.0.x) and Current (1.1.x) runtimes in the package; so by installing the SDK, you receive everything you need to build.</span></span>

### <a name="appveyor"></a><span data-ttu-id="4208b-155">AppVeyor</span><span class="sxs-lookup"><span data-stu-id="4208b-155">AppVeyor</span></span>

<span data-ttu-id="4208b-156">[AppVeyor](https://www.appveyor.com/) instaluje .NET Core 1.0.1 SDK `Visual Studio 2017` budowania obrazu procesu roboczego.</span><span class="sxs-lookup"><span data-stu-id="4208b-156">[AppVeyor](https://www.appveyor.com/) installs the .NET Core 1.0.1 SDK with the `Visual Studio 2017` build worker image.</span></span> <span data-ttu-id="4208b-157">Inne obrazy kompilacji z różnymi wersjami programu .NET Core SDK są dostępne.</span><span class="sxs-lookup"><span data-stu-id="4208b-157">Other build images with different versions of the .NET Core SDK are available.</span></span> <span data-ttu-id="4208b-158">Aby uzyskać więcej informacji, zobacz [przykład appveyor.yml](https://github.com/dotnet/docs/blob/master/appveyor.yml) i [kompilowanie obrazów procesu roboczego](https://www.appveyor.com/docs/build-environment/#build-worker-images) artykuł w witrynie docs AppVeyor.</span><span class="sxs-lookup"><span data-stu-id="4208b-158">For more information, see the [appveyor.yml example](https://github.com/dotnet/docs/blob/master/appveyor.yml) and the [Build worker images](https://www.appveyor.com/docs/build-environment/#build-worker-images) article in the AppVeyor docs.</span></span>

<span data-ttu-id="4208b-159">Pliki binarne .NET Core SDK są pobierane i rozpakowanej w podkatalogu przy użyciu skryptu instalacji, a następnie są one dodawane do `PATH` zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="4208b-159">The .NET Core SDK binaries are downloaded and unzipped in a subdirectory using the install script, and then they're added to the `PATH` environment variable.</span></span> <span data-ttu-id="4208b-160">Dodaj macierz kompilacji, aby uruchomić testy integracji z wieloma wersjami programu .NET Core SDK:</span><span class="sxs-lookup"><span data-stu-id="4208b-160">Add a build matrix to run integration tests with multiple versions of the .NET Core SDK:</span></span>

```yaml
environment:
  matrix:
    - CLI_VERSION: 1.0.1
    - CLI_VERSION: Latest

install:
  # See appveyor.yml example for install script
```

### <a name="azure-devops-services"></a><span data-ttu-id="4208b-161">Azure DevOps Services</span><span class="sxs-lookup"><span data-stu-id="4208b-161">Azure DevOps Services</span></span>

<span data-ttu-id="4208b-162">Skonfiguruj usługom DevOps platformy Azure do kompilowania projektów .NET Core przy użyciu jednej z następujących podejść:</span><span class="sxs-lookup"><span data-stu-id="4208b-162">Configure Azure DevOps Services to build .NET Core projects using one of these approaches:</span></span>

1. <span data-ttu-id="4208b-163">Uruchom skrypt z [kroku instalacji ręcznej](#manual-setup) przy użyciu poleceń.</span><span class="sxs-lookup"><span data-stu-id="4208b-163">Run the script from the [manual setup step](#manual-setup) using your commands.</span></span>
1. <span data-ttu-id="4208b-164">Tworzenie kompilacji składa się z kilku zadań kompilacji wbudowanych usługom DevOps platformy Azure, które są skonfigurowane do używania narzędzi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4208b-164">Create a build composed of several Azure DevOps Services built-in build tasks that are configured to use .NET Core tools.</span></span>

<span data-ttu-id="4208b-165">Oba rozwiązania są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="4208b-165">Both solutions are valid.</span></span> <span data-ttu-id="4208b-166">Za pomocą skryptu instalacji ręcznej, możesz kontrolować wersję narzędzia, które otrzymujesz, ponieważ możesz pobrać jako część kompilacji.</span><span class="sxs-lookup"><span data-stu-id="4208b-166">Using a manual setup script, you control the version of the tools that you receive, since you download them as part of the build.</span></span> <span data-ttu-id="4208b-167">Kompilacja jest uruchamiana ze skryptu, który należy utworzyć.</span><span class="sxs-lookup"><span data-stu-id="4208b-167">The build is run from a script that you must create.</span></span> <span data-ttu-id="4208b-168">W tym artykule opisano tylko opcji ręcznej.</span><span class="sxs-lookup"><span data-stu-id="4208b-168">This article only covers the manual option.</span></span> <span data-ttu-id="4208b-169">Aby uzyskać więcej informacji na temat tworzenia kompilacji dzięki usługom DevOps platformy Azure z zadania kompilacji, zobacz [potoki Azure](https://docs.microsoft.com/azure/devops/pipelines/index) dokumentacji.</span><span class="sxs-lookup"><span data-stu-id="4208b-169">For more information on composing a build with Azure DevOps Services build tasks, see the [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index) documentation.</span></span>

<span data-ttu-id="4208b-170">Aby użyć skryptu instalacji ręcznej w usługom DevOps platformy Azure, Utwórz nową definicję kompilacji i określ skrypt do uruchomienia dla kroku kompilacji.</span><span class="sxs-lookup"><span data-stu-id="4208b-170">To use a manual setup script in Azure DevOps Services, create a new build definition and specify the script to run for the build step.</span></span> <span data-ttu-id="4208b-171">Jest to realizowane przy użyciu interfejsu użytkownika usługom DevOps platformy Azure:</span><span class="sxs-lookup"><span data-stu-id="4208b-171">This is accomplished using the Azure DevOps Services user interface:</span></span>

1. <span data-ttu-id="4208b-172">Rozpocznij od utworzenia nowej definicji kompilacji.</span><span class="sxs-lookup"><span data-stu-id="4208b-172">Start by creating a new build definition.</span></span> <span data-ttu-id="4208b-173">Po osiągnięciu ekran, który udostępnia opcję, aby określić, jakiego rodzaju kompilacji chcesz utworzyć, wybierz **pusty** opcji.</span><span class="sxs-lookup"><span data-stu-id="4208b-173">Once you reach the screen that provides you an option to define what kind of a build you wish to create, select the **Empty** option.</span></span>

   ![Wybierając definicję kompilacji pusty](./media/using-ci-with-cli/select-empty-build-definition.png)

1. <span data-ttu-id="4208b-175">Po skonfigurowaniu repozytorium do tworzenia, użytkownik jest kierowany do definicji kompilacji.</span><span class="sxs-lookup"><span data-stu-id="4208b-175">After configuring the repository to build, you're directed to the build definitions.</span></span> <span data-ttu-id="4208b-176">Wybierz **Dodaj krok kompilacji**:</span><span class="sxs-lookup"><span data-stu-id="4208b-176">Select **Add build step**:</span></span>

   ![Dodawanie kroku kompilacji](./media/using-ci-with-cli/add-build-step.png)

1. <span data-ttu-id="4208b-178">Pojawi się informacja o **wykazu zadań**.</span><span class="sxs-lookup"><span data-stu-id="4208b-178">You're presented with the **Task catalog**.</span></span> <span data-ttu-id="4208b-179">Katalog zawiera zadania, których używasz w kompilacji.</span><span class="sxs-lookup"><span data-stu-id="4208b-179">The catalog contains tasks that you use in the build.</span></span> <span data-ttu-id="4208b-180">Ponieważ masz skrypt, wybierz opcję **Dodaj** przycisku **programu PowerShell: Uruchom skrypt programu PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="4208b-180">Since you have a script, select the **Add** button for **PowerShell: Run a PowerShell script**.</span></span>

   ![Dodawanie kroku skrypt programu PowerShell](./media/using-ci-with-cli/add-powershell-script.png)

1. <span data-ttu-id="4208b-182">Skonfiguruj kroku kompilacji.</span><span class="sxs-lookup"><span data-stu-id="4208b-182">Configure the build step.</span></span> <span data-ttu-id="4208b-183">Dodaj skrypt z repozytorium, którą tworzysz:</span><span class="sxs-lookup"><span data-stu-id="4208b-183">Add the script from the repository that you're building:</span></span>

   ![Określanie uruchomienie skryptu programu PowerShell](./media/using-ci-with-cli/powershell-script-path.png)

## <a name="orchestrating-the-build"></a><span data-ttu-id="4208b-185">Organizowanie kompilacji</span><span class="sxs-lookup"><span data-stu-id="4208b-185">Orchestrating the build</span></span>

<span data-ttu-id="4208b-186">Większość w tym dokumencie opisano, jak uzyskać narzędzia .NET Core oraz skonfigurować różne usługi CI bez przekazywania informacji na temat sposobu organizowania, lub *faktyczne utworzenie*, kod za pomocą platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4208b-186">Most of this document describes how to acquire the .NET Core tools and configure various CI services without providing information on how to orchestrate, or *actually build*, your code with .NET Core.</span></span> <span data-ttu-id="4208b-187">Opcje dotyczące sposobu struktury procesu kompilacji są zależne od wielu czynników, w których nie można w ogólny sposób, w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="4208b-187">The choices on how to structure the build process depend on many factors that can't be covered in a general way here.</span></span> <span data-ttu-id="4208b-188">Aby uzyskać więcej informacji na temat organizowania procesu kompilacji aplikacji w poszczególnych technologii, zapoznaj się z zasobami i przykłady przekazane w zestawach dokumentacji [rozwiązania Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), i [platformy Azure Potoki](https://docs.microsoft.com/azure/devops/pipelines/index).</span><span class="sxs-lookup"><span data-stu-id="4208b-188">For more information on orchestrating your builds with each technology, explore the resources and samples provided in the documentation sets of [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), and [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index).</span></span>

<span data-ttu-id="4208b-189">Dwa podejścia ogólne, które wykonujesz w tworzenie struktury procesu kompilacji dla kodu platformy .NET Core za pomocą narzędzi .NET Core przy użyciu programu MSBuild, bezpośrednio lub przy użyciu poleceń wiersza polecenia platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="4208b-189">Two general approaches that you take in structuring the build process for .NET Core code using the .NET Core tools are using MSBuild directly or using the .NET Core command-line commands.</span></span> <span data-ttu-id="4208b-190">Podejście, które należy podjąć zależy od poziomu komfortu przy użyciu podejścia i charakterystyczne kompromisowe złożonością.</span><span class="sxs-lookup"><span data-stu-id="4208b-190">Which approach you should take is determined by your comfort level with the approaches and trade-offs in complexity.</span></span> <span data-ttu-id="4208b-191">Program MSBuild zapewnia możliwość wyrażanie proces kompilacji jako zadania i elementy docelowe, ale chodzi o złożonością dodaną przez uczenia Składnia pliku projektu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="4208b-191">MSBuild provides you the ability to express your build process as tasks and targets, but it comes with the added complexity of learning MSBuild project file syntax.</span></span> <span data-ttu-id="4208b-192">Za pomocą narzędzia wiersza polecenia platformy .NET Core jest prawdopodobnie prostsze, ale wymaga umożliwia pisanie logiki aranżacji w języku skryptów, takich jak `bash` lub programu PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4208b-192">Using the .NET Core command-line tools is perhaps simpler, but it requires you to write orchestration logic in a scripting language like `bash` or PowerShell.</span></span>

## <a name="see-also"></a><span data-ttu-id="4208b-193">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4208b-193">See also</span></span>

- [<span data-ttu-id="4208b-194">Pobiera .NET — Linux</span><span class="sxs-lookup"><span data-stu-id="4208b-194">.NET downloads - Linux</span></span>](https://dotnet.microsoft.com/download?initial-os=linux)

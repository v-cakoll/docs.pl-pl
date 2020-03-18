---
title: Ciągła integracja (CI) z zestawem .NET Core SDK i narzędziami
description: Dowiedz się, jak używać sdk .NET Core i jego narzędzi na serwerze kompilacji z ciągłą integracją.
ms.date: 05/18/2017
ms.openlocfilehash: 6e23a21dd36422a095e56519c9aa28ce2549f7b2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77451041"
---
# <a name="using-net-core-sdk-and-tools-in-continuous-integration-ci"></a><span data-ttu-id="e9492-103">Korzystanie z sdk i narzędzi .NET Core w ciągłej integracji (CI)</span><span class="sxs-lookup"><span data-stu-id="e9492-103">Using .NET Core SDK and tools in Continuous Integration (CI)</span></span>

<span data-ttu-id="e9492-104">W tym dokumencie opisano przy użyciu sdk .NET Core i jego narzędzi na serwerze kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e9492-104">This document outlines using the .NET Core SDK and its tools on a build server.</span></span> <span data-ttu-id="e9492-105">Zestaw narzędzi .NET Core działa zarówno interaktywnie, gdzie deweloper wypisuje polecenia w wierszu polecenia, jak i automatycznie, gdy serwer ciągłej integracji (CI) uruchamia skrypt kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e9492-105">The .NET Core toolset works both interactively, where a developer types commands at a command prompt, and automatically, where a Continuous Integration (CI) server runs a build script.</span></span> <span data-ttu-id="e9492-106">Polecenia, opcje, dane wejściowe i dane wyjściowe są takie same, a jedyne rzeczy, które podajesz, to sposób na uzyskanie narzędzi i systemu do tworzenia aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e9492-106">The commands, options, inputs, and outputs are the same, and the only things you supply are a way to acquire the tooling and a system to build your app.</span></span> <span data-ttu-id="e9492-107">Ten dokument koncentruje się na scenariuszach pozyskiwania narzędzi dla ci z zaleceniami dotyczącymi projektowania i struktury skryptów kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e9492-107">This document focuses on scenarios of tool acquisition for CI with recommendations on how to design and structure your build scripts.</span></span>

## <a name="installation-options-for-ci-build-servers"></a><span data-ttu-id="e9492-108">Opcje instalacji serwerów kompilacji ci</span><span class="sxs-lookup"><span data-stu-id="e9492-108">Installation options for CI build servers</span></span>

### <a name="using-the-native-installers"></a><span data-ttu-id="e9492-109">Korzystanie z instalatorów natywnych</span><span class="sxs-lookup"><span data-stu-id="e9492-109">Using the native installers</span></span>

<span data-ttu-id="e9492-110">Instalatory natywne są dostępne dla systemów macOS, Linux i Windows.</span><span class="sxs-lookup"><span data-stu-id="e9492-110">Native installers are available for macOS, Linux, and Windows.</span></span> <span data-ttu-id="e9492-111">Instalatorzy wymagają administratora (sudo) dostępu do serwera kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e9492-111">The installers require admin (sudo) access to the build server.</span></span> <span data-ttu-id="e9492-112">Zaletą korzystania z instalatora macierzystego jest to, że instaluje wszystkie natywne zależności wymagane do uruchamiania narzędzi.</span><span class="sxs-lookup"><span data-stu-id="e9492-112">The advantage of using a native installer is that it installs all of the native dependencies required for the tooling to run.</span></span> <span data-ttu-id="e9492-113">Instalatorzy natywni zapewniają również instalację sdk w całym systemie.</span><span class="sxs-lookup"><span data-stu-id="e9492-113">Native installers also provide a system-wide installation of the SDK.</span></span>

<span data-ttu-id="e9492-114">Użytkownicy systemu macOS powinni korzystać z instalatorów PKG.</span><span class="sxs-lookup"><span data-stu-id="e9492-114">macOS users should use the PKG installers.</span></span> <span data-ttu-id="e9492-115">W systemie Linux istnieje możliwość użycia menedżera pakietów opartych na pliku danych, takiego jak apt-get dla Ubuntu lub yum dla CentOS, lub przy użyciu samych pakietów, DEB lub RPM.</span><span class="sxs-lookup"><span data-stu-id="e9492-115">On Linux, there's a choice of using a feed-based package manager, such as apt-get for Ubuntu or yum for CentOS, or using the packages themselves, DEB or RPM.</span></span> <span data-ttu-id="e9492-116">W systemie Windows użyj instalatora MSI.</span><span class="sxs-lookup"><span data-stu-id="e9492-116">On Windows, use the MSI installer.</span></span>

<span data-ttu-id="e9492-117">Najnowsze stabilne pliki binarne znajdują się w [plikach do pobrania .NET](https://dotnet.microsoft.com/download).</span><span class="sxs-lookup"><span data-stu-id="e9492-117">The latest stable binaries are found at [.NET downloads](https://dotnet.microsoft.com/download).</span></span> <span data-ttu-id="e9492-118">Jeśli chcesz korzystać z najnowszego (i potencjalnie niestabilnego) narzędzia wersji wstępnej, użyj łączy podanych w [repozytorium GitHub dotnet/core-sdk](https://github.com/dotnet/core-sdk#installers-and-binaries).</span><span class="sxs-lookup"><span data-stu-id="e9492-118">If you wish to use the latest (and potentially unstable) pre-release tooling, use the links provided at the [dotnet/core-sdk GitHub repository](https://github.com/dotnet/core-sdk#installers-and-binaries).</span></span> <span data-ttu-id="e9492-119">W przypadku dystrybucji Linuksa `tar.gz` dostępne są archiwa (znane również jako). `tarballs` użyj skryptów instalacyjnych w archiwach, aby zainstalować program .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e9492-119">For Linux distributions, `tar.gz` archives (also known as `tarballs`) are available; use the installation scripts within the archives to install .NET Core.</span></span>

### <a name="using-the-installer-script"></a><span data-ttu-id="e9492-120">Korzystanie ze skryptu instalatora</span><span class="sxs-lookup"><span data-stu-id="e9492-120">Using the installer script</span></span>

<span data-ttu-id="e9492-121">Użycie skryptu instalatora umożliwia instalację nieadministracyjną na serwerze kompilacji i łatwą automatyzację uzyskiwania narzędzi.</span><span class="sxs-lookup"><span data-stu-id="e9492-121">Using the installer script allows for non-administrative installation on your build server and easy automation for obtaining the tooling.</span></span> <span data-ttu-id="e9492-122">Skrypt zajmuje się pobieraniem narzędzi i wyodrębnianiem go do domyślnej lub określonej lokalizacji do użycia.</span><span class="sxs-lookup"><span data-stu-id="e9492-122">The script takes care of downloading the tooling and extracting it into a default or specified location for use.</span></span> <span data-ttu-id="e9492-123">Można również określić wersję narzędzi, które chcesz zainstalować i czy chcesz zainstalować cały zestaw SDK, czy tylko udostępniony program runtime.</span><span class="sxs-lookup"><span data-stu-id="e9492-123">You can also specify a version of the tooling that you wish to install and whether you want to install the entire SDK or only the shared runtime.</span></span>

<span data-ttu-id="e9492-124">Skrypt instalatora jest zautomatyzowany do uruchomienia na początku kompilacji w celu pobrania i zainstalowania żądanej wersji sdk.</span><span class="sxs-lookup"><span data-stu-id="e9492-124">The installer script is automated to run at the start of the build to fetch and install the desired version of the SDK.</span></span> <span data-ttu-id="e9492-125">*Żądana wersja* jest niezależnie od wersji sdk projekty wymagają do kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e9492-125">The *desired version* is whatever version of the SDK your projects require to build.</span></span> <span data-ttu-id="e9492-126">Skrypt umożliwia zainstalowanie sdk w katalogu lokalnym na serwerze, uruchomienie narzędzi z zainstalowanej lokalizacji, a następnie oczyścić (lub pozwolić usłudze pinkowej oczyścić) po kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e9492-126">The script allows you to install the SDK in a local directory on the server, run the tools from the installed location, and then clean up (or let the CI service clean up) after the build.</span></span> <span data-ttu-id="e9492-127">Zapewnia to hermetyzację i izolację całego procesu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e9492-127">This provides encapsulation and isolation to your entire build process.</span></span> <span data-ttu-id="e9492-128">Odwołanie do skryptu instalacyjnego znajduje się w artykule [dotnet-install.](dotnet-install-script.md)</span><span class="sxs-lookup"><span data-stu-id="e9492-128">The installation script reference is found in the [dotnet-install](dotnet-install-script.md) article.</span></span>

> [!NOTE]
> <span data-ttu-id="e9492-129">**Usługa Azure DevOps Services**</span><span class="sxs-lookup"><span data-stu-id="e9492-129">**Azure DevOps Services**</span></span>
>
> <span data-ttu-id="e9492-130">Korzystając ze skryptu instalatora, zależności natywne nie są instalowane automatycznie.</span><span class="sxs-lookup"><span data-stu-id="e9492-130">When using the installer script, native dependencies aren't installed automatically.</span></span> <span data-ttu-id="e9492-131">Należy zainstalować zależności macierzyste, jeśli system operacyjny ich nie ma.</span><span class="sxs-lookup"><span data-stu-id="e9492-131">You must install the native dependencies if the operating system doesn't have them.</span></span> <span data-ttu-id="e9492-132">Aby uzyskać więcej informacji, zobacz [zależności i wymagania programu .NET Core](../install/dependencies.md).</span><span class="sxs-lookup"><span data-stu-id="e9492-132">For more information, see [.NET Core dependencies and requirements](../install/dependencies.md).</span></span>

## <a name="ci-setup-examples"></a><span data-ttu-id="e9492-133">Przykłady konfiguracji ci</span><span class="sxs-lookup"><span data-stu-id="e9492-133">CI setup examples</span></span>

<span data-ttu-id="e9492-134">W tej sekcji opisano konfigurację ręczną przy użyciu skryptu programu PowerShell lub bash oraz opis kilku rozwiązań ci oprogramowania jako usługi (SaaS).</span><span class="sxs-lookup"><span data-stu-id="e9492-134">This section describes a manual setup using a PowerShell or bash script, along with a description of several software as a service (SaaS) CI solutions.</span></span> <span data-ttu-id="e9492-135">Rozwiązania SaaS CI objęte są [Travis CI,](https://travis-ci.org/) [AppVeyor](https://www.appveyor.com/)i [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index).</span><span class="sxs-lookup"><span data-stu-id="e9492-135">The SaaS CI solutions covered are [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), and [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index).</span></span>

### <a name="manual-setup"></a><span data-ttu-id="e9492-136">Konfiguracja ręczna</span><span class="sxs-lookup"><span data-stu-id="e9492-136">Manual setup</span></span>

<span data-ttu-id="e9492-137">Każda usługa SaaS ma własne metody tworzenia i konfigurowania procesu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e9492-137">Each SaaS service has its own methods for creating and configuring a build process.</span></span> <span data-ttu-id="e9492-138">Jeśli używasz innego rozwiązania SaaS niż wymienione lub wymagają dostosowania poza wstępnie spakowane jałmużenie, należy wykonać co najmniej niektóre ręcznej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e9492-138">If you use different SaaS solution than those listed or require customization beyond the pre-packaged support, you must perform at least some manual configuration.</span></span>

<span data-ttu-id="e9492-139">Ogólnie rzecz biorąc, konfiguracja ręczna wymaga nabycia wersji narzędzi (lub najnowszych nocnych kompilacji narzędzi) i uruchomienia skryptu kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e9492-139">In general, a manual setup requires you to acquire a version of the tools (or the latest nightly builds of the tools) and run your build script.</span></span> <span data-ttu-id="e9492-140">Za pomocą skryptu programu PowerShell lub bash można aranżować polecenia programu .NET Core lub użyć pliku projektu, który przedstawia proces kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e9492-140">You can use a PowerShell or bash script to orchestrate the .NET Core commands or use a project file that outlines the build process.</span></span> <span data-ttu-id="e9492-141">[Sekcja aranżacji](#orchestrating-the-build) zawiera więcej szczegółów na temat tych opcji.</span><span class="sxs-lookup"><span data-stu-id="e9492-141">The [orchestration section](#orchestrating-the-build) provides more detail on these options.</span></span>

<span data-ttu-id="e9492-142">Po utworzeniu skryptu, który wykonuje ręczną konfigurację serwera kompilacji ci, użyj go na komputerze deweloperskim, aby utworzyć kod lokalnie do celów testowych.</span><span class="sxs-lookup"><span data-stu-id="e9492-142">After you create a script that performs a manual CI build server setup, use it on your dev machine to build your code locally for testing purposes.</span></span> <span data-ttu-id="e9492-143">Po potwierdzeniu, że skrypt działa dobrze lokalnie, wdrożyć go na serwerze kompilacji ci.</span><span class="sxs-lookup"><span data-stu-id="e9492-143">Once you confirm that the script is running well locally, deploy it to your CI build server.</span></span> <span data-ttu-id="e9492-144">Stosunkowo prosty skrypt programu PowerShell pokazuje, jak uzyskać zestaw SDK .NET Core i zainstalować go na serwerze kompilacji systemu Windows:</span><span class="sxs-lookup"><span data-stu-id="e9492-144">A relatively simple PowerShell script demonstrates how to obtain the .NET Core SDK and install it on a Windows build server:</span></span>

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

<span data-ttu-id="e9492-145">Należy podać implementację dla procesu kompilacji na końcu skryptu.</span><span class="sxs-lookup"><span data-stu-id="e9492-145">You provide the implementation for your build process at the end of the script.</span></span> <span data-ttu-id="e9492-146">Skrypt uzyskuje narzędzia, a następnie wykonuje proces kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e9492-146">The script acquires the tools and then executes your build process.</span></span> <span data-ttu-id="e9492-147">W przypadku komputerów unix następujący skrypt bash wykonuje akcje opisane w skrypcie programu PowerShell w podobny sposób:</span><span class="sxs-lookup"><span data-stu-id="e9492-147">For UNIX machines, the following bash script performs the actions described in the PowerShell script in a similar manner:</span></span>

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

### <a name="travis-ci"></a><span data-ttu-id="e9492-148">Travis CI</span><span class="sxs-lookup"><span data-stu-id="e9492-148">Travis CI</span></span>

<span data-ttu-id="e9492-149">Możesz skonfigurować [Travis CI](https://travis-ci.org/) do zainstalowania .NET `csharp` Core SDK przy użyciu języka i klucza. `dotnet`</span><span class="sxs-lookup"><span data-stu-id="e9492-149">You can configure [Travis CI](https://travis-ci.org/) to install the .NET Core SDK using the `csharp` language and the `dotnet` key.</span></span> <span data-ttu-id="e9492-150">Aby uzyskać więcej informacji, zobacz oficjalne dokumenty Travis CI dotyczące [tworzenia projektu Języka C#, F lub Visual Basic](https://docs.travis-ci.com/user/languages/csharp/).</span><span class="sxs-lookup"><span data-stu-id="e9492-150">For more information, see the official Travis CI docs on [Building a C#, F#, or Visual Basic Project](https://docs.travis-ci.com/user/languages/csharp/).</span></span> <span data-ttu-id="e9492-151">Należy pamiętać, jak uzyskać dostęp do informacji `language: csharp` Travis CI, że identyfikator języka utrzymywane przez społeczność działa dla wszystkich języków .NET, w tym F#i Mono.</span><span class="sxs-lookup"><span data-stu-id="e9492-151">Note as you access the Travis CI information that the community-maintained `language: csharp` language identifier works for all .NET languages, including F#, and Mono.</span></span>

<span data-ttu-id="e9492-152">Travis CI uruchamia zadania systemu macOS i Linux w *macierzy kompilacji,* gdzie określisz kombinację środowiska uruchomieniowego, środowiska i wykluczeń/wtrąceń, aby pokryć kombinacje kompilacji dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="e9492-152">Travis CI runs both macOS and Linux jobs in a *build matrix*, where you specify a combination of runtime, environment, and exclusions/inclusions to cover your build combinations for your app.</span></span> <span data-ttu-id="e9492-153">Aby uzyskać więcej informacji, zobacz [Dostosowywanie kompilacji](https://docs.travis-ci.com/user/customizing-the-build) artykuł w dokumentacji Travis CI.</span><span class="sxs-lookup"><span data-stu-id="e9492-153">For more information, see the [Customizing the Build](https://docs.travis-ci.com/user/customizing-the-build) article in the Travis CI documentation.</span></span> <span data-ttu-id="e9492-154">Narzędzia oparte na usylaniu MSBuild obejmują uruchamianie LTS (1.0.x) i Current (1.1.x) w pakiecie; więc instalując zestaw SDK, otrzymasz wszystko, czego potrzebujesz do zbudowania.</span><span class="sxs-lookup"><span data-stu-id="e9492-154">The MSBuild-based tools include the LTS (1.0.x) and Current (1.1.x) runtimes in the package; so by installing the SDK, you receive everything you need to build.</span></span>

### <a name="appveyor"></a><span data-ttu-id="e9492-155">AppVeyor (Zw.AppVeyor)</span><span class="sxs-lookup"><span data-stu-id="e9492-155">AppVeyor</span></span>

<span data-ttu-id="e9492-156">[AppVeyor](https://www.appveyor.com/) instaluje zestaw SDK .NET Core `Visual Studio 2017` 1.0.1 z obrazem procesu tworzenia.</span><span class="sxs-lookup"><span data-stu-id="e9492-156">[AppVeyor](https://www.appveyor.com/) installs the .NET Core 1.0.1 SDK with the `Visual Studio 2017` build worker image.</span></span> <span data-ttu-id="e9492-157">Dostępne są inne obrazy kompilacji z różnymi wersjami sdk .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e9492-157">Other build images with different versions of the .NET Core SDK are available.</span></span> <span data-ttu-id="e9492-158">Aby uzyskać więcej informacji, zobacz [przykład appveyor.yml](https://github.com/dotnet/docs/blob/master/appveyor.yml) i [tworzenie obrazów roboczych](https://www.appveyor.com/docs/build-environment/#build-worker-images) w dokumentach AppVeyor.</span><span class="sxs-lookup"><span data-stu-id="e9492-158">For more information, see the [appveyor.yml example](https://github.com/dotnet/docs/blob/master/appveyor.yml) and the [Build worker images](https://www.appveyor.com/docs/build-environment/#build-worker-images) article in the AppVeyor docs.</span></span>

<span data-ttu-id="e9492-159">Pliki binarne sdk .NET Core są pobierane i rozpakowywane w podkatalogu przy `PATH` użyciu skryptu instalacyjnego, a następnie dodawane do zmiennej środowiskowej.</span><span class="sxs-lookup"><span data-stu-id="e9492-159">The .NET Core SDK binaries are downloaded and unzipped in a subdirectory using the install script, and then they're added to the `PATH` environment variable.</span></span> <span data-ttu-id="e9492-160">Dodaj macierz kompilacji, aby uruchomić testy integracji z wieloma wersjami sdk .NET Core:</span><span class="sxs-lookup"><span data-stu-id="e9492-160">Add a build matrix to run integration tests with multiple versions of the .NET Core SDK:</span></span>

```yaml
environment:
  matrix:
    - CLI_VERSION: 1.0.1
    - CLI_VERSION: Latest

install:
  # See appveyor.yml example for install script
```

### <a name="azure-devops-services"></a><span data-ttu-id="e9492-161">Usługa Azure DevOps Services</span><span class="sxs-lookup"><span data-stu-id="e9492-161">Azure DevOps Services</span></span>

<span data-ttu-id="e9492-162">Skonfiguruj usługi Azure DevOps Services do tworzenia projektów .NET Core przy użyciu jednej z następujących metod:</span><span class="sxs-lookup"><span data-stu-id="e9492-162">Configure Azure DevOps Services to build .NET Core projects using one of these approaches:</span></span>

1. <span data-ttu-id="e9492-163">Uruchom skrypt z [etapu ręcznej konfiguracji](#manual-setup) za pomocą poleceń.</span><span class="sxs-lookup"><span data-stu-id="e9492-163">Run the script from the [manual setup step](#manual-setup) using your commands.</span></span>
1. <span data-ttu-id="e9492-164">Utwórz kompilację składającą się z kilku wbudowanych zadań kompilacji usług Azure DevOps Services skonfigurowanych do używania narzędzi .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e9492-164">Create a build composed of several Azure DevOps Services built-in build tasks that are configured to use .NET Core tools.</span></span>

<span data-ttu-id="e9492-165">Oba rozwiązania są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="e9492-165">Both solutions are valid.</span></span> <span data-ttu-id="e9492-166">Za pomocą skryptu ręcznej konfiguracji można kontrolować wersję narzędzi, które otrzymujesz, ponieważ można je pobrać jako część kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e9492-166">Using a manual setup script, you control the version of the tools that you receive, since you download them as part of the build.</span></span> <span data-ttu-id="e9492-167">Kompilacja jest uruchamiana ze skryptu, który należy utworzyć.</span><span class="sxs-lookup"><span data-stu-id="e9492-167">The build is run from a script that you must create.</span></span> <span data-ttu-id="e9492-168">Ten artykuł obejmuje tylko opcję ręczną.</span><span class="sxs-lookup"><span data-stu-id="e9492-168">This article only covers the manual option.</span></span> <span data-ttu-id="e9492-169">Aby uzyskać więcej informacji na temat tworzenia kompilacji z zadaniami kompilacji usług Azure DevOps Services, zobacz dokumentację [potoków platformy Azure.](https://docs.microsoft.com/azure/devops/pipelines/index)</span><span class="sxs-lookup"><span data-stu-id="e9492-169">For more information on composing a build with Azure DevOps Services build tasks, see the [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index) documentation.</span></span>

<span data-ttu-id="e9492-170">Aby użyć skryptu ręcznej konfiguracji w usłudze Azure DevOps Services, utwórz nową definicję kompilacji i określ skrypt do uruchomienia dla kroku kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e9492-170">To use a manual setup script in Azure DevOps Services, create a new build definition and specify the script to run for the build step.</span></span> <span data-ttu-id="e9492-171">Jest to realizowane przy użyciu interfejsu użytkownika usługi Azure DevOps Services:</span><span class="sxs-lookup"><span data-stu-id="e9492-171">This is accomplished using the Azure DevOps Services user interface:</span></span>

1. <span data-ttu-id="e9492-172">Rozpocznij od utworzenia nowej definicji kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e9492-172">Start by creating a new build definition.</span></span> <span data-ttu-id="e9492-173">Po dotarciu do ekranu, który zapewnia opcję, aby zdefiniować rodzaj kompilacji, którą chcesz utworzyć, wybierz opcję **Puste.**</span><span class="sxs-lookup"><span data-stu-id="e9492-173">Once you reach the screen that provides you an option to define what kind of a build you wish to create, select the **Empty** option.</span></span>

   ![Wybieranie pustej definicji kompilacji](./media/using-ci-with-cli/select-empty-build-definition.png)

1. <span data-ttu-id="e9492-175">Po skonfigurowaniu repozytorium do kompilacji, jesteś kierowany do definicji kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e9492-175">After configuring the repository to build, you're directed to the build definitions.</span></span> <span data-ttu-id="e9492-176">Wybierz **pozycję Dodaj krok kompilacji:**</span><span class="sxs-lookup"><span data-stu-id="e9492-176">Select **Add build step**:</span></span>

   ![Dodawanie kroku kompilacji](./media/using-ci-with-cli/add-build-step.png)

1. <span data-ttu-id="e9492-178">Zostanie przedstawiony **katalog zadań**.</span><span class="sxs-lookup"><span data-stu-id="e9492-178">You're presented with the **Task catalog**.</span></span> <span data-ttu-id="e9492-179">Katalog zawiera zadania, które są używane w kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e9492-179">The catalog contains tasks that you use in the build.</span></span> <span data-ttu-id="e9492-180">Ponieważ masz skrypt, wybierz przycisk **Dodaj** dla **programu PowerShell: Uruchom skrypt programu PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="e9492-180">Since you have a script, select the **Add** button for **PowerShell: Run a PowerShell script**.</span></span>

   ![Dodawanie kroku skryptu programu PowerShell](./media/using-ci-with-cli/add-powershell-script.png)

1. <span data-ttu-id="e9492-182">Skonfiguruj krok kompilacji.</span><span class="sxs-lookup"><span data-stu-id="e9492-182">Configure the build step.</span></span> <span data-ttu-id="e9492-183">Dodaj skrypt z repozytorium, które budujesz:</span><span class="sxs-lookup"><span data-stu-id="e9492-183">Add the script from the repository that you're building:</span></span>

   ![Określanie skryptu programu PowerShell do uruchomienia](./media/using-ci-with-cli/powershell-script-path.png)

## <a name="orchestrating-the-build"></a><span data-ttu-id="e9492-185">Organizowanie kompilacji</span><span class="sxs-lookup"><span data-stu-id="e9492-185">Orchestrating the build</span></span>

<span data-ttu-id="e9492-186">W większości tego dokumentu opisano sposób uzyskiwania narzędzi .NET Core i konfigurowania różnych *actually build*usług pw.</span><span class="sxs-lookup"><span data-stu-id="e9492-186">Most of this document describes how to acquire the .NET Core tools and configure various CI services without providing information on how to orchestrate, or *actually build*, your code with .NET Core.</span></span> <span data-ttu-id="e9492-187">Wybór sposobu struktury procesu kompilacji zależy od wielu czynników, które nie mogą być omówione w sposób ogólny tutaj.</span><span class="sxs-lookup"><span data-stu-id="e9492-187">The choices on how to structure the build process depend on many factors that can't be covered in a general way here.</span></span> <span data-ttu-id="e9492-188">Aby uzyskać więcej informacji na temat organizowania kompilacji przy każdej technologii, zapoznaj się z zasobami i przykładami podanymi w zestawach dokumentacji [Travis CI,](https://travis-ci.org/) [AppVeyor](https://www.appveyor.com/)i [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index).</span><span class="sxs-lookup"><span data-stu-id="e9492-188">For more information on orchestrating your builds with each technology, explore the resources and samples provided in the documentation sets of [Travis CI](https://travis-ci.org/), [AppVeyor](https://www.appveyor.com/), and [Azure Pipelines](https://docs.microsoft.com/azure/devops/pipelines/index).</span></span>

<span data-ttu-id="e9492-189">Dwa ogólne podejścia, które można podjąć w strukturyzacji procesu kompilacji dla .NET Core kodu przy użyciu .NET Core narzędzia są przy użyciu MSBuild bezpośrednio lub przy użyciu polecenia wiersza polecenia .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e9492-189">Two general approaches that you take in structuring the build process for .NET Core code using the .NET Core tools are using MSBuild directly or using the .NET Core command-line commands.</span></span> <span data-ttu-id="e9492-190">To, jakie podejście powinieneś przyjąć, zależy od twojego poziomu komfortu z podejściami i kompromisami w złożoności.</span><span class="sxs-lookup"><span data-stu-id="e9492-190">Which approach you should take is determined by your comfort level with the approaches and trade-offs in complexity.</span></span> <span data-ttu-id="e9492-191">MSBuild zapewnia możliwość wyrażania procesu kompilacji jako zadania i obiekty docelowe, ale pochodzi z dodatkową złożoność uczenia się składni pliku projektu MSBuild.</span><span class="sxs-lookup"><span data-stu-id="e9492-191">MSBuild provides you the ability to express your build process as tasks and targets, but it comes with the added complexity of learning MSBuild project file syntax.</span></span> <span data-ttu-id="e9492-192">Korzystanie z narzędzi wiersza polecenia .NET Core jest być może prostsze, ale `bash` wymaga napisania logiki aranżacji w języku skryptów, takim jak program PowerShell.</span><span class="sxs-lookup"><span data-stu-id="e9492-192">Using the .NET Core command-line tools is perhaps simpler, but it requires you to write orchestration logic in a scripting language like `bash` or PowerShell.</span></span>

## <a name="see-also"></a><span data-ttu-id="e9492-193">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e9492-193">See also</span></span>

- [<span data-ttu-id="e9492-194">Pliki do pobrania .NET - Linux</span><span class="sxs-lookup"><span data-stu-id="e9492-194">.NET downloads - Linux</span></span>](https://dotnet.microsoft.com/download?initial-os=linux)

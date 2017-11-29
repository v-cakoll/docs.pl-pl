---
title: "skryptów instalacji DotNet"
description: "Więcej informacji na temat skryptów instalacji dotnet instalacji narzędzi interfejsu wiersza polecenia platformy .NET Core i udostępnionych środowiska uruchomieniowego."
keywords: DotNet instalacji, skrypty dotnet. Zainstaluj oprogramowanie .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 09/11/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: b64e7e6f-ffb4-4fc8-b43b-5731c89479c2
ms.openlocfilehash: 2f15f37016fe824d76b501e4793e0b28bbdbe167
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-install-scripts-reference"></a><span data-ttu-id="64a52-104">odwołania skryptów instalacji DotNet</span><span class="sxs-lookup"><span data-stu-id="64a52-104">dotnet-install scripts reference</span></span>

## <a name="name"></a><span data-ttu-id="64a52-105">Nazwa</span><span class="sxs-lookup"><span data-stu-id="64a52-105">Name</span></span>

<span data-ttu-id="64a52-106">`dotnet-install.ps1` | `dotnet-install.sh`-Skrypt użyty do zainstalowania narzędzi interfejsu wiersza polecenia platformy .NET Core i udostępnionych środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="64a52-106">`dotnet-install.ps1` | `dotnet-install.sh` - Script used to install the .NET Core CLI tools and the shared runtime.</span></span>

## <a name="synopsis"></a><span data-ttu-id="64a52-107">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="64a52-107">Synopsis</span></span>

<span data-ttu-id="64a52-108">System Windows:</span><span class="sxs-lookup"><span data-stu-id="64a52-108">Windows:</span></span>

`dotnet-install.ps1 [-Channel] [-Version] [-InstallDir] [-Architecture] [-SharedRuntime] [-DryRun] [-NoPath] [-AzureFeed] [-ProxyAddress] [--Verbose] [--Help]`

<span data-ttu-id="64a52-109">System macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="64a52-109">macOS/Linux:</span></span>

`dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture] [--shared-runtime] [--dry-run] [--no-path] [--azure-feed] [--verbose] [--help]`

## <a name="description"></a><span data-ttu-id="64a52-110">Opis</span><span class="sxs-lookup"><span data-stu-id="64a52-110">Description</span></span>

<span data-ttu-id="64a52-111">`dotnet-install` Skrypty są używane do wykonywania instalacji programu .NET Core SDK, w tym narzędzi interfejsu wiersza polecenia platformy .NET Core i udostępnionych środowiska wykonawczego o bez uprawnień administratora.</span><span class="sxs-lookup"><span data-stu-id="64a52-111">The `dotnet-install` scripts are used to perform a non-admin installation of the .NET Core SDK, which includes the .NET Core CLI tools and the shared runtime.</span></span>

<span data-ttu-id="64a52-112">Zalecane jest użycie stabilną wersję, która znajduje się na [.NET Core głównym witryny sieci Web](https://dot.net).</span><span class="sxs-lookup"><span data-stu-id="64a52-112">We recommend that you use the stable version that is hosted on [.NET Core main website](https://dot.net).</span></span> <span data-ttu-id="64a52-113">Bezpośrednie ścieżki do skryptów są:</span><span class="sxs-lookup"><span data-stu-id="64a52-113">The direct paths to the scripts are:</span></span>

* <span data-ttu-id="64a52-114">https://dot.NET/V1/DotNet-Install.sh (bash, UNIX)</span><span class="sxs-lookup"><span data-stu-id="64a52-114">https://dot.net/v1/dotnet-install.sh (bash, UNIX)</span></span>
* <span data-ttu-id="64a52-115">https://dot.NET/V1/DotNet-Install.ps1 (środowiska Powershell, system Windows)</span><span class="sxs-lookup"><span data-stu-id="64a52-115">https://dot.net/v1/dotnet-install.ps1 (Powershell, Windows)</span></span>

<span data-ttu-id="64a52-116">Jest głównym przydatność te skrypty w scenariuszach automatyzacji i instalacji bez uprawnień administratora.</span><span class="sxs-lookup"><span data-stu-id="64a52-116">The main usefulness of these scripts is in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="64a52-117">Istnieją dwa skrypty: jedna jest skrypt programu PowerShell, która działa w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="64a52-117">There are two scripts: One is a PowerShell script that works on Windows.</span></span> <span data-ttu-id="64a52-118">Inne skryptu to skrypt bash, który działa na systemie Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="64a52-118">The other script is a bash script that works on Linux/macOS.</span></span> <span data-ttu-id="64a52-119">Zarówno skryptów ma takie samo zachowanie.</span><span class="sxs-lookup"><span data-stu-id="64a52-119">Both scripts have the same behavior.</span></span> <span data-ttu-id="64a52-120">Skrypt bash odczytuje również przełączników programu PowerShell, dzięki czemu można używać przełączników programu PowerShell przy użyciu skryptu w systemach Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="64a52-120">The bash script also reads PowerShell switches, so you can use PowerShell switches with the script on Linux/macOS systems.</span></span> 

<span data-ttu-id="64a52-121">Skrypty instalacyjne Pobierz plik ZIP/tarball z porzucania kompilacji interfejsu wiersza polecenia i przejdź do instalacji w lokalizacji domyślnej lub w lokalizacji określonej przez `-InstallDir|--install-dir`.</span><span class="sxs-lookup"><span data-stu-id="64a52-121">The installation scripts download the ZIP/tarball file from the CLI build drops and proceed to install it in either the default location or in a location specified by `-InstallDir|--install-dir`.</span></span> <span data-ttu-id="64a52-122">Domyślnie skrypty instalacyjne Pobierz zestaw SDK i zainstaluj go.</span><span class="sxs-lookup"><span data-stu-id="64a52-122">By default, the installation scripts download the SDK and install it.</span></span> <span data-ttu-id="64a52-123">Jeśli chcesz tylko uzyskać udostępnionego środowiska uruchomieniowego, określ `--shared-runtime` argumentu.</span><span class="sxs-lookup"><span data-stu-id="64a52-123">If you wish to only obtain the shared runtime, specify the `--shared-runtime` argument.</span></span> 

<span data-ttu-id="64a52-124">Domyślnie skrypt dodaje lokalizacji instalacji do $PATH dla bieżącej sesji.</span><span class="sxs-lookup"><span data-stu-id="64a52-124">By default, the script adds the install location to the $PATH for the current session.</span></span> <span data-ttu-id="64a52-125">Zmienić to zachowanie domyślne, określając `--no-path` argumentu.</span><span class="sxs-lookup"><span data-stu-id="64a52-125">Override this default behavior by specifying the `--no-path` argument.</span></span> 

<span data-ttu-id="64a52-126">Przed uruchomieniem skryptu, zainstalować wymagane [zależności](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span><span class="sxs-lookup"><span data-stu-id="64a52-126">Before running the script, install the required [dependencies](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span></span>

<span data-ttu-id="64a52-127">Można zainstalować przy użyciu określonej wersji `--version` argumentu.</span><span class="sxs-lookup"><span data-stu-id="64a52-127">You can install a specific version using the `--version` argument.</span></span> <span data-ttu-id="64a52-128">Należy określić wersję w wersji 3 części (na przykład 1.0.0-13232).</span><span class="sxs-lookup"><span data-stu-id="64a52-128">The version must be specified as a 3-part version (for example, 1.0.0-13232).</span></span> <span data-ttu-id="64a52-129">Pominięcie używa `latest` wersji.</span><span class="sxs-lookup"><span data-stu-id="64a52-129">If omitted, it uses the `latest` version.</span></span>

## <a name="options"></a><span data-ttu-id="64a52-130">Opcje</span><span class="sxs-lookup"><span data-stu-id="64a52-130">Options</span></span>

`-Channel <CHANNEL>`

<span data-ttu-id="64a52-131">Określa kanał źródła instalacji.</span><span class="sxs-lookup"><span data-stu-id="64a52-131">Specifies the source channel for the installation.</span></span> <span data-ttu-id="64a52-132">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="64a52-132">The possible values are:</span></span>

- <span data-ttu-id="64a52-133">`Current`-Bieżącej wersji</span><span class="sxs-lookup"><span data-stu-id="64a52-133">`Current` - Current release</span></span>
- <span data-ttu-id="64a52-134">`LTS`-Długoterminowej kanału pomocy technicznej (bieżąca wersja obsługiwane)</span><span class="sxs-lookup"><span data-stu-id="64a52-134">`LTS` - Long-Term Support channel (current supported release)</span></span>
- <span data-ttu-id="64a52-135">Wersja dwóch elementów w formacie X.Y reprezentujący dla określonej wersji (na przykład `2.0` lub `1.0`)</span><span class="sxs-lookup"><span data-stu-id="64a52-135">Two-part version in X.Y format representing a specific release (for example, `2.0` or `1.0`)</span></span>
- <span data-ttu-id="64a52-136">Nazwa gałęzi [na przykład `release/2.0.0`, `release/2.0.0-preview2`, lub `master` najnowsze z `master` gałęzi (wydań co noc "marginesy krawędzi")]</span><span class="sxs-lookup"><span data-stu-id="64a52-136">Branch name [for example, `release/2.0.0`, `release/2.0.0-preview2`, or `master` for the latest from the `master` branch ("bleeding edge" nightly releases)]</span></span>

<span data-ttu-id="64a52-137">Wartość domyślna to `LTS`.</span><span class="sxs-lookup"><span data-stu-id="64a52-137">The default value is `LTS`.</span></span> <span data-ttu-id="64a52-138">Aby uzyskać więcej informacji dotyczących kanałów pomocy technicznej platformy .NET, zobacz [.NET Core Cykl wsparcia technicznego produktów](https://www.microsoft.com/net/core/support) tematu.</span><span class="sxs-lookup"><span data-stu-id="64a52-138">For more information on .NET support channels, see the [.NET Core Support Lifecycle](https://www.microsoft.com/net/core/support) topic.</span></span>

`-Version <VERSION>`

<span data-ttu-id="64a52-139">Reprezentuje wersji określonej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="64a52-139">Represents a specific build version.</span></span> <span data-ttu-id="64a52-140">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="64a52-140">The possible values are:</span></span>

- <span data-ttu-id="64a52-141">`latest`-Najnowszych kompilacji w kanale (używany z `-Channel` opcja)</span><span class="sxs-lookup"><span data-stu-id="64a52-141">`latest` - Latest build on the channel (used with the `-Channel` option)</span></span>
- <span data-ttu-id="64a52-142">`coherent`-Najnowszych spójnego kompilacji na kanał. używa kombinacji najnowsza stabilna pakietu (używana z nazwą gałęzi `-Channel` opcje)</span><span class="sxs-lookup"><span data-stu-id="64a52-142">`coherent` - Latest coherent build on the channel; uses the latest stable package combination (used with Branch name `-Channel` options)</span></span>
- <span data-ttu-id="64a52-143">Trzech części wersja reprezentujący określony format X.Y.Z kompilacji wersji; zastępuje `-Channel` opcji.</span><span class="sxs-lookup"><span data-stu-id="64a52-143">Three-part version in X.Y.Z format representing a specific build version; supersedes the `-Channel` option.</span></span> <span data-ttu-id="64a52-144">Na przykład:`2.0.0-preview2-006120`</span><span class="sxs-lookup"><span data-stu-id="64a52-144">For example: `2.0.0-preview2-006120`</span></span>

<span data-ttu-id="64a52-145">Pominięcie `-Version` domyślnie `latest`.</span><span class="sxs-lookup"><span data-stu-id="64a52-145">If omitted, `-Version` defaults to `latest`.</span></span>

`-InstallDir <DIRECTORY>`

<span data-ttu-id="64a52-146">Określa ścieżkę instalacji.</span><span class="sxs-lookup"><span data-stu-id="64a52-146">Specifies the installation path.</span></span> <span data-ttu-id="64a52-147">Katalog jest tworzony, jeśli nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="64a52-147">The directory is created if it doesn't exist.</span></span> <span data-ttu-id="64a52-148">Wartość domyślna to *LocalAppData %\.dotnet*.</span><span class="sxs-lookup"><span data-stu-id="64a52-148">The default value is *%LocalAppData%\.dotnet*.</span></span> <span data-ttu-id="64a52-149">Należy pamiętać, że pliki binarne są umieszczane bezpośrednio w katalogu.</span><span class="sxs-lookup"><span data-stu-id="64a52-149">Note that binaries are placed directly in the directory.</span></span>

`-Architecture <ARCHITECTURE>`

<span data-ttu-id="64a52-150">Architektura .NET Core plików binarnych do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="64a52-150">Architecture of the .NET Core binaries to install.</span></span> <span data-ttu-id="64a52-151">Możliwe wartości to `auto`, `x64`, i `x86`.</span><span class="sxs-lookup"><span data-stu-id="64a52-151">Possible values are `auto`, `x64`, and `x86`.</span></span> <span data-ttu-id="64a52-152">Wartość domyślna to `auto`, reprezentuje aktualnie uruchomionych architektury systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="64a52-152">The default value is `auto`, which represents the currently running OS architecture.</span></span>

`-SharedRuntime`

<span data-ttu-id="64a52-153">Jeśli ustawiona, tego przełącznika na instalację do udostępnionego środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="64a52-153">If set, this switch limits installation to the shared runtime.</span></span> <span data-ttu-id="64a52-154">Cały zestaw SDK nie jest zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="64a52-154">The entire SDK isn't installed.</span></span>

`-DryRun`

<span data-ttu-id="64a52-155">Jeśli nie będzie ustawiona, skrypt przeprowadzenia instalacji; ale zamiast tego Wyświetla jakie wiersza poleceń do używania w celu zainstalowania spójnie obecnie żądanej wersji programu .NET Core interfejsu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="64a52-155">If set, the script won't perform the installation; but instead, it displays what command line to use to consistently install the currently requested version of the .NET Core CLI.</span></span> <span data-ttu-id="64a52-156">Na przykład jeśli określisz wersji `latest`, zawiera łącze do określonej wersji, aby to polecenie może być używane w sposób niejednoznaczny w skrypcie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="64a52-156">For example if you specify version `latest`, it displays a link with the specific version so that this command can be used deterministically in a build script.</span></span> <span data-ttu-id="64a52-157">Wyświetla również lokalizacji pliku binarnego, aby zainstalować lub pobrać samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="64a52-157">It also displays the binary's location if you prefer to install or download it yourself.</span></span>

`-NoPath`

<span data-ttu-id="64a52-158">Jeśli ustawiona, prefiks/installdir nie zostaną wyeksportowane do ścieżki dla bieżącej sesji.</span><span class="sxs-lookup"><span data-stu-id="64a52-158">If set, the prefix/installdir are not exported to the path for the current session.</span></span> <span data-ttu-id="64a52-159">Domyślnie skrypt zmodyfikuje ścieżki, która udostępnia natychmiast po przeprowadzeniu instalacji narzędzi interfejsu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="64a52-159">By default, the script will modify the PATH, which makes the CLI tools available immediately after install.</span></span>

`-AzureFeed`

<span data-ttu-id="64a52-160">Określa, że adres URL dla platformy Azure źródła danych Instalatora.</span><span class="sxs-lookup"><span data-stu-id="64a52-160">Specifies the URL for the Azure feed to the installer.</span></span> <span data-ttu-id="64a52-161">Nie jest zalecane, aby zmienić tę wartość.</span><span class="sxs-lookup"><span data-stu-id="64a52-161">It isn't recommended that you change this value.</span></span> <span data-ttu-id="64a52-162">Wartość domyślna to `https://dotnetcli.azureedge.net/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="64a52-162">The default is `https://dotnetcli.azureedge.net/dotnet`.</span></span>

`-ProxyAddress`

<span data-ttu-id="64a52-163">Jeśli zestaw, Instalator używa serwera proxy w przypadku wysyłania żądań sieci web.</span><span class="sxs-lookup"><span data-stu-id="64a52-163">If set, the installer uses the proxy when making web requests.</span></span> <span data-ttu-id="64a52-164">(Ta funkcja jest prawidłowa tylko dla systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="64a52-164">(Only valid for Windows)</span></span>

`--verbose`

<span data-ttu-id="64a52-165">Wyświetlanie informacji diagnostycznych.</span><span class="sxs-lookup"><span data-stu-id="64a52-165">Display diagnostics information.</span></span>

`--help`

<span data-ttu-id="64a52-166">Drukuje pomoc dotyczącą skryptu.</span><span class="sxs-lookup"><span data-stu-id="64a52-166">Prints out help for the script.</span></span>

## <a name="examples"></a><span data-ttu-id="64a52-167">Przykłady</span><span class="sxs-lookup"><span data-stu-id="64a52-167">Examples</span></span>

<span data-ttu-id="64a52-168">Zainstaluj najnowsze długoterminowej obsługiwaną wersję (LTS) w domyślnej lokalizacji:</span><span class="sxs-lookup"><span data-stu-id="64a52-168">Install the latest long-term supported (LTS) version to the default location:</span></span>

<span data-ttu-id="64a52-169">System Windows:</span><span class="sxs-lookup"><span data-stu-id="64a52-169">Windows:</span></span>

`./dotnet-install.ps1 -Channel LTS`

<span data-ttu-id="64a52-170">System macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="64a52-170">macOS/Linux:</span></span>

`./dotnet-install.sh --channel LTS`

<span data-ttu-id="64a52-171">Zainstaluj najnowszą wersję z kanału 2.0 do określonej lokalizacji:</span><span class="sxs-lookup"><span data-stu-id="64a52-171">Install the latest version from 2.0 channel to the specified location:</span></span>

<span data-ttu-id="64a52-172">System Windows:</span><span class="sxs-lookup"><span data-stu-id="64a52-172">Windows:</span></span>

`./dotnet-install.ps1 -Channel 2.0 -InstallDir C:\cli`

<span data-ttu-id="64a52-173">System macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="64a52-173">macOS/Linux:</span></span>

`./dotnet-install.sh --channel 2.0 --install-dir ~/cli`

<span data-ttu-id="64a52-174">Zainstaluj 1.1.0 wersji środowiska uruchomieniowego udostępnionego:</span><span class="sxs-lookup"><span data-stu-id="64a52-174">Install the 1.1.0 version of the shared runtime:</span></span>

<span data-ttu-id="64a52-175">System Windows:</span><span class="sxs-lookup"><span data-stu-id="64a52-175">Windows:</span></span>

`./dotnet-install.ps1 -SharedRuntime -Version 1.1.0`

<span data-ttu-id="64a52-176">System macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="64a52-176">macOS/Linux:</span></span>

`./dotnet-install.sh --shared-runtime --version 1.1.0`

<span data-ttu-id="64a52-177">Uzyskać skrypt i zainstaluj przykłady one-liner .NET Core interfejsu wiersza polecenia:</span><span class="sxs-lookup"><span data-stu-id="64a52-177">Obtain script and install .NET Core CLI one-liner examples:</span></span>

<span data-ttu-id="64a52-178">System Windows:</span><span class="sxs-lookup"><span data-stu-id="64a52-178">Windows:</span></span>

`@powershell -NoProfile -ExecutionPolicy unrestricted -Command "&([scriptblock]::Create((Invoke-WebRequest -useb 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"`

<span data-ttu-id="64a52-179">System macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="64a52-179">macOS/Linux:</span></span>

`curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>`

## <a name="see-also"></a><span data-ttu-id="64a52-180">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="64a52-180">See also</span></span>

<span data-ttu-id="64a52-181">[Zwalnia .NET core](https://github.com/dotnet/core/releases) </span><span class="sxs-lookup"><span data-stu-id="64a52-181">[.NET Core releases](https://github.com/dotnet/core/releases) </span></span>  
[<span data-ttu-id="64a52-182">Środowisko uruchomieniowe platformy .NET core i zestawu SDK Pobierz archiwum</span><span class="sxs-lookup"><span data-stu-id="64a52-182">.NET Core Runtime and SDK download archive</span></span>](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)

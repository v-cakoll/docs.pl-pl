---
title: skrypty instalacji DotNet
description: Więcej informacji na temat skryptów instalacji dotnet do zainstalowania narzędzi interfejsu wiersza polecenia platformy .NET Core i udostępnionego środowiska uruchomieniowego.
author: blackdwarf
ms.author: mairaw
ms.date: 09/11/2017
ms.openlocfilehash: ea14424297dcf1dab8711197bee1d3b3e19879c1
ms.sourcegitcommit: 586dbdcaef9767642436b1e4efbe88fb15473d6f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/06/2018
ms.locfileid: "48837079"
---
# <a name="dotnet-install-scripts-reference"></a><span data-ttu-id="614a2-103">Dokumentacja skryptów instalacji DotNet</span><span class="sxs-lookup"><span data-stu-id="614a2-103">dotnet-install scripts reference</span></span>

## <a name="name"></a><span data-ttu-id="614a2-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="614a2-104">Name</span></span>

<span data-ttu-id="614a2-105">`dotnet-install.ps1` | `dotnet-install.sh` — Skrypt używany do instalacji narzędzi interfejsu wiersza polecenia platformy .NET Core i udostępnionego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="614a2-105">`dotnet-install.ps1` | `dotnet-install.sh` - Script used to install the .NET Core CLI tools and the shared runtime.</span></span>

## <a name="synopsis"></a><span data-ttu-id="614a2-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="614a2-106">Synopsis</span></span>

<span data-ttu-id="614a2-107">Windows:</span><span class="sxs-lookup"><span data-stu-id="614a2-107">Windows:</span></span>

`dotnet-install.ps1 [-Channel] [-Version] [-InstallDir] [-Architecture] [-SharedRuntime] [-DryRun] [-NoPath] [-AzureFeed] [-ProxyAddress] [--Verbose] [--Help]`

<span data-ttu-id="614a2-108">System macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="614a2-108">macOS/Linux:</span></span>

`dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture] [--shared-runtime] [--dry-run] [--no-path] [--azure-feed] [--verbose] [--help]`

## <a name="description"></a><span data-ttu-id="614a2-109">Opis</span><span class="sxs-lookup"><span data-stu-id="614a2-109">Description</span></span>

<span data-ttu-id="614a2-110">`dotnet-install` Skrypty są używane do przeprowadzenia instalacji bez uprawnień administratora programu .NET Core SDK, w tym narzędzi interfejsu wiersza polecenia platformy .NET Core i udostępnionego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="614a2-110">The `dotnet-install` scripts are used to perform a non-admin installation of the .NET Core SDK, which includes the .NET Core CLI tools and the shared runtime.</span></span>

<span data-ttu-id="614a2-111">Zalecane jest użycie stabilną wersję, która jest hostowana na [głównej witryny internetowej platformy .NET Core](https://dot.net).</span><span class="sxs-lookup"><span data-stu-id="614a2-111">We recommend that you use the stable version that is hosted on [.NET Core main website](https://dot.net).</span></span> <span data-ttu-id="614a2-112">Bezpośrednie ścieżki do skryptów są:</span><span class="sxs-lookup"><span data-stu-id="614a2-112">The direct paths to the scripts are:</span></span>

* <span data-ttu-id="614a2-113"><https://dot.net/v1/dotnet-install.sh> (powłoki bash, UNIX)</span><span class="sxs-lookup"><span data-stu-id="614a2-113"><https://dot.net/v1/dotnet-install.sh> (bash, UNIX)</span></span>
* <span data-ttu-id="614a2-114"><https://dot.net/v1/dotnet-install.ps1> (Program Powershell, Windows)</span><span class="sxs-lookup"><span data-stu-id="614a2-114"><https://dot.net/v1/dotnet-install.ps1> (Powershell, Windows)</span></span>

<span data-ttu-id="614a2-115">Główne użyteczność tych skryptów znajduje się w scenariuszach automatyzacji oraz przed instalacjami bez uprawnień administratora.</span><span class="sxs-lookup"><span data-stu-id="614a2-115">The main usefulness of these scripts is in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="614a2-116">Istnieją dwa skrypty: jeden z nich jest skrypt programu PowerShell, który działa na Windows.</span><span class="sxs-lookup"><span data-stu-id="614a2-116">There are two scripts: One is a PowerShell script that works on Windows.</span></span> <span data-ttu-id="614a2-117">Skrypt programu jest skrypt powłoki bash, który działa w systemie Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="614a2-117">The other script is a bash script that works on Linux/macOS.</span></span> <span data-ttu-id="614a2-118">Zarówno skryptów mają takie samo zachowanie.</span><span class="sxs-lookup"><span data-stu-id="614a2-118">Both scripts have the same behavior.</span></span> <span data-ttu-id="614a2-119">Skrypt powłoki bash odczytuje również przełączników programu PowerShell, aby można było używać przełączników programu PowerShell przy użyciu skryptu w systemach Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="614a2-119">The bash script also reads PowerShell switches, so you can use PowerShell switches with the script on Linux/macOS systems.</span></span>

<span data-ttu-id="614a2-120">Skrypty instalacji Pobierz plik ZIP/pliku tar z spadnie kompilacji interfejsu wiersza polecenia i przejdź do instalacji w lokalizacji domyślnej lub w lokalizacji określonej przez `-InstallDir|--install-dir`.</span><span class="sxs-lookup"><span data-stu-id="614a2-120">The installation scripts download the ZIP/tarball file from the CLI build drops and proceed to install it in either the default location or in a location specified by `-InstallDir|--install-dir`.</span></span> <span data-ttu-id="614a2-121">Domyślnie skrypty instalacyjne Pobierz zestaw SDK i zainstaluj go.</span><span class="sxs-lookup"><span data-stu-id="614a2-121">By default, the installation scripts download the SDK and install it.</span></span> <span data-ttu-id="614a2-122">Jeśli chcesz uzyskać tylko udostępnionego środowiska uruchomieniowego, należy określić `--shared-runtime` argumentu.</span><span class="sxs-lookup"><span data-stu-id="614a2-122">If you wish to only obtain the shared runtime, specify the `--shared-runtime` argument.</span></span>

<span data-ttu-id="614a2-123">Domyślnie skrypt ten dodaje lokalizacji instalacji do $PATH dla bieżącej sesji.</span><span class="sxs-lookup"><span data-stu-id="614a2-123">By default, the script adds the install location to the $PATH for the current session.</span></span> <span data-ttu-id="614a2-124">To zachowanie domyślne można przesłonić, określając `--no-path` argumentu.</span><span class="sxs-lookup"><span data-stu-id="614a2-124">Override this default behavior by specifying the `--no-path` argument.</span></span>

<span data-ttu-id="614a2-125">Przed uruchomieniem skryptu, zainstalować wymagane [zależności](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span><span class="sxs-lookup"><span data-stu-id="614a2-125">Before running the script, install the required [dependencies](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span></span>

<span data-ttu-id="614a2-126">Można to zrobić przy użyciu określonej wersji `--version` argumentu.</span><span class="sxs-lookup"><span data-stu-id="614a2-126">You can install a specific version using the `--version` argument.</span></span> <span data-ttu-id="614a2-127">Wersja muszą być określone jako część 3 wersji (na przykład 1.0.0-13232).</span><span class="sxs-lookup"><span data-stu-id="614a2-127">The version must be specified as a 3-part version (for example, 1.0.0-13232).</span></span> <span data-ttu-id="614a2-128">Jeśli argument jest pominięty, zostanie użyta `latest` wersji.</span><span class="sxs-lookup"><span data-stu-id="614a2-128">If omitted, it uses the `latest` version.</span></span>

## <a name="options"></a><span data-ttu-id="614a2-129">Opcje</span><span class="sxs-lookup"><span data-stu-id="614a2-129">Options</span></span>

`-Channel <CHANNEL>`

<span data-ttu-id="614a2-130">Określa identyfikator kanału źródła dla instalacji.</span><span class="sxs-lookup"><span data-stu-id="614a2-130">Specifies the source channel for the installation.</span></span> <span data-ttu-id="614a2-131">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="614a2-131">The possible values are:</span></span>

- <span data-ttu-id="614a2-132">`Current` -Bieżąca wersja</span><span class="sxs-lookup"><span data-stu-id="614a2-132">`Current` - Current release</span></span>
- <span data-ttu-id="614a2-133">`LTS` — Długoterminowe kanału pomocy technicznej (bieżąca wersja obsługiwane)</span><span class="sxs-lookup"><span data-stu-id="614a2-133">`LTS` - Long-Term Support channel (current supported release)</span></span>
- <span data-ttu-id="614a2-134">Wersja legalną dwuczęściową w formacie X.Y reprezentujący określonej wersji (na przykład `2.0` lub `1.0`)</span><span class="sxs-lookup"><span data-stu-id="614a2-134">Two-part version in X.Y format representing a specific release (for example, `2.0` or `1.0`)</span></span>
- <span data-ttu-id="614a2-135">Nazwa gałęzi [na przykład `release/2.0.0`, `release/2.0.0-preview2`, lub `master` uzyskać najnowsze informacje przedstawią `master` gałęzi ("jest edge" nocne wydania)]</span><span class="sxs-lookup"><span data-stu-id="614a2-135">Branch name [for example, `release/2.0.0`, `release/2.0.0-preview2`, or `master` for the latest from the `master` branch ("bleeding edge" nightly releases)]</span></span>

<span data-ttu-id="614a2-136">Wartość domyślna to `LTS`.</span><span class="sxs-lookup"><span data-stu-id="614a2-136">The default value is `LTS`.</span></span> <span data-ttu-id="614a2-137">Aby uzyskać więcej informacji dotyczących kanałów pomocy technicznej platformy .NET, zobacz [.NET Core Cykl wsparcia technicznego produktów](https://www.microsoft.com/net/core/support) tematu.</span><span class="sxs-lookup"><span data-stu-id="614a2-137">For more information on .NET support channels, see the [.NET Core Support Lifecycle](https://www.microsoft.com/net/core/support) topic.</span></span>

`-Version <VERSION>`

<span data-ttu-id="614a2-138">Reprezentuje wersję konkretnej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="614a2-138">Represents a specific build version.</span></span> <span data-ttu-id="614a2-139">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="614a2-139">The possible values are:</span></span>

- <span data-ttu-id="614a2-140">`latest` -Najnowszych kompilacji w kanale (używany z `-Channel` opcja)</span><span class="sxs-lookup"><span data-stu-id="614a2-140">`latest` - Latest build on the channel (used with the `-Channel` option)</span></span>
- <span data-ttu-id="614a2-141">`coherent` — Najnowsza wersja spójnego kompilacji na kanał. używa kombinacji najnowszy stabilny pakiet (używany przy użyciu gałęzi o nazwie `-Channel` opcje)</span><span class="sxs-lookup"><span data-stu-id="614a2-141">`coherent` - Latest coherent build on the channel; uses the latest stable package combination (used with Branch name `-Channel` options)</span></span>
- <span data-ttu-id="614a2-142">Trzyczęściowej wersję w formacie X.Y.Z reprezentującą określony kompilacji wersji; zastępuje `-Channel` opcji.</span><span class="sxs-lookup"><span data-stu-id="614a2-142">Three-part version in X.Y.Z format representing a specific build version; supersedes the `-Channel` option.</span></span> <span data-ttu-id="614a2-143">Na przykład: `2.0.0-preview2-006120`</span><span class="sxs-lookup"><span data-stu-id="614a2-143">For example: `2.0.0-preview2-006120`</span></span>

<span data-ttu-id="614a2-144">W przypadku pominięcia `-Version` wartość domyślna to `latest`.</span><span class="sxs-lookup"><span data-stu-id="614a2-144">If omitted, `-Version` defaults to `latest`.</span></span>

`-InstallDir <DIRECTORY>`

<span data-ttu-id="614a2-145">Określa ścieżkę instalacji.</span><span class="sxs-lookup"><span data-stu-id="614a2-145">Specifies the installation path.</span></span> <span data-ttu-id="614a2-146">Katalog jest tworzony, jeśli nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="614a2-146">The directory is created if it doesn't exist.</span></span> <span data-ttu-id="614a2-147">Wartość domyślna to *% LocalAppData %\.dotnet*.</span><span class="sxs-lookup"><span data-stu-id="614a2-147">The default value is *%LocalAppData%\.dotnet*.</span></span> <span data-ttu-id="614a2-148">Należy pamiętać, że pliki binarne są umieszczane bezpośrednio w katalogu.</span><span class="sxs-lookup"><span data-stu-id="614a2-148">Note that binaries are placed directly in the directory.</span></span>

`-Architecture <ARCHITECTURE>`

<span data-ttu-id="614a2-149">Architektura platformy .NET Core pliki binarne do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="614a2-149">Architecture of the .NET Core binaries to install.</span></span> <span data-ttu-id="614a2-150">Możliwe wartości to `auto`, `x64`, i `x86`.</span><span class="sxs-lookup"><span data-stu-id="614a2-150">Possible values are `auto`, `x64`, and `x86`.</span></span> <span data-ttu-id="614a2-151">Wartość domyślna to `auto`, który reprezentuje aktualnie uruchomionych architektury systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="614a2-151">The default value is `auto`, which represents the currently running OS architecture.</span></span>

`-SharedRuntime`

<span data-ttu-id="614a2-152">Jeśli ustawiona, ten przełącznik ogranicza instalacji udostępnionego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="614a2-152">If set, this switch limits installation to the shared runtime.</span></span> <span data-ttu-id="614a2-153">Cały zestaw SDK nie jest zainstalowany.</span><span class="sxs-lookup"><span data-stu-id="614a2-153">The entire SDK isn't installed.</span></span>

`-DryRun`

<span data-ttu-id="614a2-154">Jeśli nie będzie ustawiona, skrypt przeprowadzenia instalacji; ale zamiast tego wyświetla wiersz polecenia na potrzeby spójnego zainstalować obecnie żądana wersja interfejsu wiersza polecenia platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="614a2-154">If set, the script won't perform the installation; but instead, it displays what command line to use to consistently install the currently requested version of the .NET Core CLI.</span></span> <span data-ttu-id="614a2-155">Na przykład w przypadku określenia wersji `latest`, wyświetla łącze do określonej wersji, aby to polecenie może być używane w sposób deterministyczny w skrypcie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="614a2-155">For example if you specify version `latest`, it displays a link with the specific version so that this command can be used deterministically in a build script.</span></span> <span data-ttu-id="614a2-156">Lokalizacja tego pliku binarnego również wyświetlana, jeśli wolisz zainstalować lub pobrać go samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="614a2-156">It also displays the binary's location if you prefer to install or download it yourself.</span></span>

`-NoPath`

<span data-ttu-id="614a2-157">Jeśli ustawiona, prefiks/installdir nie są eksportowane do ścieżki dla bieżącej sesji.</span><span class="sxs-lookup"><span data-stu-id="614a2-157">If set, the prefix/installdir are not exported to the path for the current session.</span></span> <span data-ttu-id="614a2-158">Domyślnie skrypt zostanie zmodyfikowany ścieżki, która udostępnia natychmiast po przeprowadzeniu instalacji narzędzi interfejsu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="614a2-158">By default, the script will modify the PATH, which makes the CLI tools available immediately after install.</span></span>

`-AzureFeed`

<span data-ttu-id="614a2-159">Określa, że adres URL dla platformy Azure, źródła danych do Instalatora.</span><span class="sxs-lookup"><span data-stu-id="614a2-159">Specifies the URL for the Azure feed to the installer.</span></span> <span data-ttu-id="614a2-160">Nie jest zalecane, aby zmienić tę wartość.</span><span class="sxs-lookup"><span data-stu-id="614a2-160">It isn't recommended that you change this value.</span></span> <span data-ttu-id="614a2-161">Wartość domyślna to `https://dotnetcli.azureedge.net/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="614a2-161">The default is `https://dotnetcli.azureedge.net/dotnet`.</span></span>

`-ProxyAddress`

<span data-ttu-id="614a2-162">Jeśli zestaw, Instalator używa serwera proxy w przypadku wysyłania żądań sieci web.</span><span class="sxs-lookup"><span data-stu-id="614a2-162">If set, the installer uses the proxy when making web requests.</span></span> <span data-ttu-id="614a2-163">(Ta funkcja jest prawidłowa tylko dla Windows)</span><span class="sxs-lookup"><span data-stu-id="614a2-163">(Only valid for Windows)</span></span>

`--verbose`

<span data-ttu-id="614a2-164">Wyświetlanie informacji diagnostycznych.</span><span class="sxs-lookup"><span data-stu-id="614a2-164">Display diagnostics information.</span></span>

`--help`

<span data-ttu-id="614a2-165">Drukuje pomoc dotyczącą skryptu.</span><span class="sxs-lookup"><span data-stu-id="614a2-165">Prints out help for the script.</span></span>

## <a name="examples"></a><span data-ttu-id="614a2-166">Przykłady</span><span class="sxs-lookup"><span data-stu-id="614a2-166">Examples</span></span>

<span data-ttu-id="614a2-167">W domyślnej lokalizacji, należy zainstalować najnowsze długoterminowe obsługiwaną wersję (LTS):</span><span class="sxs-lookup"><span data-stu-id="614a2-167">Install the latest long-term supported (LTS) version to the default location:</span></span>

<span data-ttu-id="614a2-168">Windows:</span><span class="sxs-lookup"><span data-stu-id="614a2-168">Windows:</span></span>

`./dotnet-install.ps1 -Channel LTS`

<span data-ttu-id="614a2-169">System macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="614a2-169">macOS/Linux:</span></span>

`./dotnet-install.sh --channel LTS`

<span data-ttu-id="614a2-170">Zainstaluj najnowszą wersję z kanału 2.0 do określonej lokalizacji:</span><span class="sxs-lookup"><span data-stu-id="614a2-170">Install the latest version from 2.0 channel to the specified location:</span></span>

<span data-ttu-id="614a2-171">Windows:</span><span class="sxs-lookup"><span data-stu-id="614a2-171">Windows:</span></span>

`./dotnet-install.ps1 -Channel 2.0 -InstallDir C:\cli`

<span data-ttu-id="614a2-172">System macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="614a2-172">macOS/Linux:</span></span>

`./dotnet-install.sh --channel 2.0 --install-dir ~/cli`

<span data-ttu-id="614a2-173">Zainstaluj 1.1.0 wersji udostępnionego środowiska uruchomieniowego:</span><span class="sxs-lookup"><span data-stu-id="614a2-173">Install the 1.1.0 version of the shared runtime:</span></span>

<span data-ttu-id="614a2-174">Windows:</span><span class="sxs-lookup"><span data-stu-id="614a2-174">Windows:</span></span>

`./dotnet-install.ps1 -SharedRuntime -Version 1.1.0`

<span data-ttu-id="614a2-175">System macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="614a2-175">macOS/Linux:</span></span>

`./dotnet-install.sh --shared-runtime --version 1.1.0`

<span data-ttu-id="614a2-176">Uzyskać skrypt i zainstaluj interfejs wiersza polecenia platformy .NET Core one-liner przykłady:</span><span class="sxs-lookup"><span data-stu-id="614a2-176">Obtain script and install .NET Core CLI one-liner examples:</span></span>

<span data-ttu-id="614a2-177">Windows:</span><span class="sxs-lookup"><span data-stu-id="614a2-177">Windows:</span></span>

`@powershell -NoProfile -ExecutionPolicy unrestricted -Command "[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; &([scriptblock]::Create((Invoke-WebRequest -useb 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"`

<span data-ttu-id="614a2-178">System macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="614a2-178">macOS/Linux:</span></span>

`curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>`

## <a name="see-also"></a><span data-ttu-id="614a2-179">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="614a2-179">See also</span></span>

* [<span data-ttu-id="614a2-180">Wersje platformy .NET core</span><span class="sxs-lookup"><span data-stu-id="614a2-180">.NET Core releases</span></span>](https://github.com/dotnet/core/releases)
* [<span data-ttu-id="614a2-181">Środowisko uruchomieniowe programu .NET core i zestawu SDK Pobierz archiwum</span><span class="sxs-lookup"><span data-stu-id="614a2-181">.NET Core Runtime and SDK download archive</span></span>](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)

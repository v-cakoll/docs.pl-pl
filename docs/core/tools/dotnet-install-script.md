---
title: dotnet-install scripts
description: Dowiedz się więcej na temat skryptów programu dotnet-install, aby zainstalować narzędzia interfejs wiersza polecenia platformy .NET Core i udostępnione środowisko uruchomieniowe.
ms.date: 01/16/2019
ms.openlocfilehash: f72e12fc415824a9c69eba6f52e3c01717cf654c
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740531"
---
# <a name="dotnet-install-scripts-reference"></a><span data-ttu-id="6a215-103">dotnet — informacje o skryptach instalacji</span><span class="sxs-lookup"><span data-stu-id="6a215-103">dotnet-install scripts reference</span></span>

## <a name="name"></a><span data-ttu-id="6a215-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="6a215-104">Name</span></span>

<span data-ttu-id="6a215-105">`dotnet-install.ps1` | `dotnet-install.sh` — skrypt służący do instalowania narzędzi interfejs wiersza polecenia platformy .NET Core i udostępnionego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="6a215-105">`dotnet-install.ps1` | `dotnet-install.sh` - Script used to install the .NET Core CLI tools and the shared runtime.</span></span>

## <a name="synopsis"></a><span data-ttu-id="6a215-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="6a215-106">Synopsis</span></span>

<span data-ttu-id="6a215-107">System Windows:</span><span class="sxs-lookup"><span data-stu-id="6a215-107">Windows:</span></span>

`dotnet-install.ps1 [-Channel] [-Version] [-InstallDir] [-Architecture] [-SharedRuntime] [-Runtime] [-DryRun] [-NoPath] [-Verbose] [-AzureFeed] [-UncachedFeed] [-NoCdn] [-FeedCredential] [-ProxyAddress] [-ProxyUseDefaultCredentials] [-SkipNonVersionedFiles] [-Help]`

<span data-ttu-id="6a215-108">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="6a215-108">macOS/Linux:</span></span>

`dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture] [--runtime] [--dry-run] [--no-path] [--verbose] [--azure-feed] [--uncached-feed] [--no-cdn] [--feed-credential] [--runtime-id] [--skip-non-versioned-files] [--help]`

## <a name="description"></a><span data-ttu-id="6a215-109">Opis</span><span class="sxs-lookup"><span data-stu-id="6a215-109">Description</span></span>

<span data-ttu-id="6a215-110">Skrypty `dotnet-install` są używane do przeprowadzania instalacji nieadministratora zestaw .NET Core SDK, która obejmuje narzędzia interfejs wiersza polecenia platformy .NET Core i udostępnione środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="6a215-110">The `dotnet-install` scripts are used to perform a non-admin installation of the .NET Core SDK, which includes the .NET Core CLI tools and the shared runtime.</span></span>

<span data-ttu-id="6a215-111">Zalecamy korzystanie z stabilnej wersji hostowanej w [głównej witrynie sieci Web platformy .NET Core](https://dot.net).</span><span class="sxs-lookup"><span data-stu-id="6a215-111">We recommend that you use the stable version that is hosted on [.NET Core main website](https://dot.net).</span></span> <span data-ttu-id="6a215-112">Bezpośrednie ścieżki do skryptów są następujące:</span><span class="sxs-lookup"><span data-stu-id="6a215-112">The direct paths to the scripts are:</span></span>

- <span data-ttu-id="6a215-113"><https://dot.net/v1/dotnet-install.sh> (bash, UNIX)</span><span class="sxs-lookup"><span data-stu-id="6a215-113"><https://dot.net/v1/dotnet-install.sh> (bash, UNIX)</span></span>
- <span data-ttu-id="6a215-114"><https://dot.net/v1/dotnet-install.ps1> (program PowerShell, system Windows)</span><span class="sxs-lookup"><span data-stu-id="6a215-114"><https://dot.net/v1/dotnet-install.ps1> (Powershell, Windows)</span></span>

<span data-ttu-id="6a215-115">Główna użyteczność tych skryptów jest w scenariuszach automatyzacji i instalacjach nienależących do administratora.</span><span class="sxs-lookup"><span data-stu-id="6a215-115">The main usefulness of these scripts is in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="6a215-116">Istnieją dwa skrypty: jeden to skrypt programu PowerShell, który działa w systemie Windows, a drugi to skrypt bash, który działa w systemie Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="6a215-116">There are two scripts: one is a PowerShell script that works on Windows, and the other is a bash script that works on Linux/macOS.</span></span> <span data-ttu-id="6a215-117">Oba skrypty mają takie samo zachowanie.</span><span class="sxs-lookup"><span data-stu-id="6a215-117">Both scripts have the same behavior.</span></span> <span data-ttu-id="6a215-118">Skrypt bash odczytuje również przełączniki programu PowerShell, dzięki czemu można użyć przełączników programu PowerShell z skryptem w systemach Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="6a215-118">The bash script also reads PowerShell switches, so you can use PowerShell switches with the script on Linux/macOS systems.</span></span>

<span data-ttu-id="6a215-119">Skrypty instalacyjne pobierają plik ZIP/plik tar z kompilacji interfejsu wiersza polecenia, a następnie instalują go w lokalizacji domyślnej lub w lokalizacji określonej przez `-InstallDir|--install-dir`.</span><span class="sxs-lookup"><span data-stu-id="6a215-119">The installation scripts download the ZIP/tarball file from the CLI build drops and proceed to install it in either the default location or in a location specified by `-InstallDir|--install-dir`.</span></span> <span data-ttu-id="6a215-120">Domyślnie skrypty instalacyjne pobierają zestaw SDK i instalują go.</span><span class="sxs-lookup"><span data-stu-id="6a215-120">By default, the installation scripts download the SDK and install it.</span></span> <span data-ttu-id="6a215-121">Jeśli chcesz uzyskać tylko udostępnione środowisko uruchomieniowe, określ argument `--runtime`.</span><span class="sxs-lookup"><span data-stu-id="6a215-121">If you wish to only obtain the shared runtime, specify the `--runtime` argument.</span></span>

<span data-ttu-id="6a215-122">Domyślnie skrypt dodaje lokalizację instalacji do $PATH bieżącej sesji.</span><span class="sxs-lookup"><span data-stu-id="6a215-122">By default, the script adds the install location to the $PATH for the current session.</span></span> <span data-ttu-id="6a215-123">Zastąp to zachowanie domyślne, określając argument `--no-path`.</span><span class="sxs-lookup"><span data-stu-id="6a215-123">Override this default behavior by specifying the `--no-path` argument.</span></span>

<span data-ttu-id="6a215-124">Przed uruchomieniem skryptu Zainstaluj wymagane [zależności](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span><span class="sxs-lookup"><span data-stu-id="6a215-124">Before running the script, install the required [dependencies](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span></span>

<span data-ttu-id="6a215-125">Określoną wersję można zainstalować przy użyciu argumentu `--version`.</span><span class="sxs-lookup"><span data-stu-id="6a215-125">You can install a specific version using the `--version` argument.</span></span> <span data-ttu-id="6a215-126">Wersja musi być określona jako wersja z trzema częściami (na przykład 1.0.0-13232).</span><span class="sxs-lookup"><span data-stu-id="6a215-126">The version must be specified as a three-part version (for example, 1.0.0-13232).</span></span> <span data-ttu-id="6a215-127">Jeśli nie zostanie podany, zostanie użyta wersja `latest`.</span><span class="sxs-lookup"><span data-stu-id="6a215-127">If not provided, it uses the `latest` version.</span></span>

## <a name="options"></a><span data-ttu-id="6a215-128">Opcje</span><span class="sxs-lookup"><span data-stu-id="6a215-128">Options</span></span>

- **`-Channel <CHANNEL>`**

  <span data-ttu-id="6a215-129">Określa kanał źródłowy instalacji.</span><span class="sxs-lookup"><span data-stu-id="6a215-129">Specifies the source channel for the installation.</span></span> <span data-ttu-id="6a215-130">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="6a215-130">The possible values are:</span></span>

  - <span data-ttu-id="6a215-131">`Current` — Najnowsza wersja.</span><span class="sxs-lookup"><span data-stu-id="6a215-131">`Current` - Most current release.</span></span>
  - <span data-ttu-id="6a215-132">`LTS`-długoterminowy kanał pomocy technicznej (większość aktualnie obsługiwanych wersji).</span><span class="sxs-lookup"><span data-stu-id="6a215-132">`LTS` - Long-Term Support channel (most current supported release).</span></span>
  - <span data-ttu-id="6a215-133">Dwuczęściowa wersja w formacie X. Y reprezentującym określoną wersję (na przykład `2.0` lub `1.0`).</span><span class="sxs-lookup"><span data-stu-id="6a215-133">Two-part version in X.Y format representing a specific release (for example, `2.0` or `1.0`).</span></span>
  - <span data-ttu-id="6a215-134">Nazwa rozgałęzienia.</span><span class="sxs-lookup"><span data-stu-id="6a215-134">Branch name.</span></span> <span data-ttu-id="6a215-135">Na przykład `release/2.0.0`, `release/2.0.0-preview2`lub `master` (w przypadku wersji nocnych).</span><span class="sxs-lookup"><span data-stu-id="6a215-135">For example, `release/2.0.0`, `release/2.0.0-preview2`, or `master` (for nightly releases).</span></span>

  <span data-ttu-id="6a215-136">Wartość domyślna to `LTS`.</span><span class="sxs-lookup"><span data-stu-id="6a215-136">The default value is `LTS`.</span></span> <span data-ttu-id="6a215-137">Aby uzyskać więcej informacji na temat kanałów pomocy technicznej platformy .NET, zobacz stronę [zasady pomocy technicznej platformy .NET](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) .</span><span class="sxs-lookup"><span data-stu-id="6a215-137">For more information on .NET support channels, see the [.NET Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) page.</span></span>

- **`-Version <VERSION>`**

  <span data-ttu-id="6a215-138">Reprezentuje konkretną wersję kompilacji.</span><span class="sxs-lookup"><span data-stu-id="6a215-138">Represents a specific build version.</span></span> <span data-ttu-id="6a215-139">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="6a215-139">The possible values are:</span></span>

  - <span data-ttu-id="6a215-140">`latest` — Najnowsza kompilacja w kanale (używana z opcją `-Channel`).</span><span class="sxs-lookup"><span data-stu-id="6a215-140">`latest` - Latest build on the channel (used with the `-Channel` option).</span></span>
  - <span data-ttu-id="6a215-141">`coherent`-Najnowsza spójna kompilacja na kanale; używa najnowszej stabilnej kombinacji pakietów (używanej z nazwą gałęzi `-Channel` opcjami).</span><span class="sxs-lookup"><span data-stu-id="6a215-141">`coherent` - Latest coherent build on the channel; uses the latest stable package combination (used with Branch name `-Channel` options).</span></span>
  - <span data-ttu-id="6a215-142">Wersja z trzech części w formacie X. Y. Z, reprezentująca konkretną wersję kompilacji; zastępuje opcję `-Channel`.</span><span class="sxs-lookup"><span data-stu-id="6a215-142">Three-part version in X.Y.Z format representing a specific build version; supersedes the `-Channel` option.</span></span> <span data-ttu-id="6a215-143">Na przykład: `2.0.0-preview2-006120`.</span><span class="sxs-lookup"><span data-stu-id="6a215-143">For example: `2.0.0-preview2-006120`.</span></span>

  <span data-ttu-id="6a215-144">Jeśli nie zostanie określony, `-Version` domyślnie `latest`.</span><span class="sxs-lookup"><span data-stu-id="6a215-144">If not specified, `-Version` defaults to `latest`.</span></span>

- **`-InstallDir <DIRECTORY>`**

  <span data-ttu-id="6a215-145">Określa ścieżkę instalacji.</span><span class="sxs-lookup"><span data-stu-id="6a215-145">Specifies the installation path.</span></span> <span data-ttu-id="6a215-146">Katalog zostanie utworzony, jeśli nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="6a215-146">The directory is created if it doesn't exist.</span></span> <span data-ttu-id="6a215-147">Wartość domyślna to *%LocalAppData%\Microsoft\dotnet*.</span><span class="sxs-lookup"><span data-stu-id="6a215-147">The default value is *%LocalAppData%\Microsoft\dotnet*.</span></span> <span data-ttu-id="6a215-148">Pliki binarne są umieszczane bezpośrednio w tym katalogu.</span><span class="sxs-lookup"><span data-stu-id="6a215-148">Binaries are placed directly in this directory.</span></span>

- **`-Architecture <ARCHITECTURE>`**

  <span data-ttu-id="6a215-149">Architektura plików binarnych platformy .NET Core do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="6a215-149">Architecture of the .NET Core binaries to install.</span></span> <span data-ttu-id="6a215-150">Możliwe wartości to `<auto>`, `amd64`, `x64`, `x86`, `arm64`i `arm`.</span><span class="sxs-lookup"><span data-stu-id="6a215-150">Possible values are `<auto>`, `amd64`, `x64`, `x86`, `arm64`, and `arm`.</span></span> <span data-ttu-id="6a215-151">Wartość domyślna to `<auto>`, która reprezentuje aktualnie uruchomioną architekturę systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="6a215-151">The default value is `<auto>`, which represents the currently running OS architecture.</span></span>

- **`-SharedRuntime`**

  > [!NOTE]
  > <span data-ttu-id="6a215-152">Ten parametr jest przestarzały i może zostać usunięty w przyszłej wersji skryptu.</span><span class="sxs-lookup"><span data-stu-id="6a215-152">This parameter is obsolete and may be removed in a future version of the script.</span></span> <span data-ttu-id="6a215-153">Zalecaną alternatywą jest opcja `Runtime`.</span><span class="sxs-lookup"><span data-stu-id="6a215-153">The recommended alternative is the `Runtime` option.</span></span>

  <span data-ttu-id="6a215-154">Instaluje tylko udostępnione bity środowiska uruchomieniowego, a nie cały zestaw SDK.</span><span class="sxs-lookup"><span data-stu-id="6a215-154">Installs just the shared runtime bits, not the entire SDK.</span></span> <span data-ttu-id="6a215-155">Jest to równoznaczne z określeniem `-Runtime dotnet`.</span><span class="sxs-lookup"><span data-stu-id="6a215-155">This is equivalent to specifying `-Runtime dotnet`.</span></span>

- **`-Runtime <RUNTIME>`**

  <span data-ttu-id="6a215-156">Instaluje tylko udostępnione środowisko uruchomieniowe, a nie cały zestaw SDK.</span><span class="sxs-lookup"><span data-stu-id="6a215-156">Installs just the shared runtime, not the entire SDK.</span></span> <span data-ttu-id="6a215-157">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="6a215-157">The possible values are:</span></span>

  - <span data-ttu-id="6a215-158">`dotnet` — `Microsoft.NETCore.App` udostępnionego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="6a215-158">`dotnet` - the `Microsoft.NETCore.App` shared runtime.</span></span>
  - <span data-ttu-id="6a215-159">`aspnetcore` — `Microsoft.AspNetCore.App` udostępnionego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="6a215-159">`aspnetcore` - the `Microsoft.AspNetCore.App` shared runtime.</span></span>

- **`-DryRun`**

  <span data-ttu-id="6a215-160">W przypadku ustawienia skrypt nie wykona instalacji.</span><span class="sxs-lookup"><span data-stu-id="6a215-160">If set, the script won't perform the installation.</span></span> <span data-ttu-id="6a215-161">Zamiast tego Wyświetla on wiersz polecenia, który służy do spójnej instalacji aktualnie żądanej wersji interfejs wiersza polecenia platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6a215-161">Instead, it displays what command line to use to consistently install the currently requested version of the .NET Core CLI.</span></span> <span data-ttu-id="6a215-162">Jeśli na przykład zostanie określona wersja `latest`, zostanie wyświetlony link z określoną wersją, aby można było użyć tego polecenia w sposób jednoznaczny w skrypcie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="6a215-162">For example, if you specify version `latest`, it displays a link with the specific version so that this command can be used deterministically in a build script.</span></span> <span data-ttu-id="6a215-163">Wyświetla również lokalizację pliku binarnego, jeśli wolisz zainstalować lub pobrać ją samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="6a215-163">It also displays the binary's location if you prefer to install or download it yourself.</span></span>

- **`-NoPath`**

  <span data-ttu-id="6a215-164">W przypadku ustawienia folder instalacyjny nie zostanie wyeksportowany do ścieżki bieżącej sesji.</span><span class="sxs-lookup"><span data-stu-id="6a215-164">If set, the installation folder isn't exported to the path for the current session.</span></span> <span data-ttu-id="6a215-165">Domyślnie skrypt modyfikuje ścieżkę, co sprawia, że narzędzia interfejsu wiersza polecenia są dostępne natychmiast po instalacji.</span><span class="sxs-lookup"><span data-stu-id="6a215-165">By default, the script modifies the PATH, which makes the CLI tools available immediately after install.</span></span>

- **`-Verbose`**

  <span data-ttu-id="6a215-166">Wyświetla informacje diagnostyczne.</span><span class="sxs-lookup"><span data-stu-id="6a215-166">Displays diagnostics information.</span></span>

- **`-AzureFeed`**

  <span data-ttu-id="6a215-167">Określa adres URL źródła danych platformy Azure do Instalatora.</span><span class="sxs-lookup"><span data-stu-id="6a215-167">Specifies the URL for the Azure feed to the installer.</span></span> <span data-ttu-id="6a215-168">Zaleca się, aby nie zmieniać tej wartości.</span><span class="sxs-lookup"><span data-stu-id="6a215-168">We recommended that you don't change this value.</span></span> <span data-ttu-id="6a215-169">Wartość domyślna to `https://dotnetcli.azureedge.net/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="6a215-169">The default value is `https://dotnetcli.azureedge.net/dotnet`.</span></span>

- **`-UncachedFeed`**

  <span data-ttu-id="6a215-170">Umożliwia zmianę adresu URL dla niebuforowanego źródła danych używanego przez ten Instalator.</span><span class="sxs-lookup"><span data-stu-id="6a215-170">Allows changing the URL for the uncached feed used by this installer.</span></span> <span data-ttu-id="6a215-171">Zaleca się, aby nie zmieniać tej wartości.</span><span class="sxs-lookup"><span data-stu-id="6a215-171">We recommended that you don't change this value.</span></span>

- **`-NoCdn`**

  <span data-ttu-id="6a215-172">Wyłącza pobieranie z [usługi Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) i bezpośrednio używa niebuforowanego źródła danych.</span><span class="sxs-lookup"><span data-stu-id="6a215-172">Disables downloading from the [Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) and uses the uncached feed directly.</span></span>

- **`-FeedCredential`**

  <span data-ttu-id="6a215-173">Służy jako ciąg zapytania do dołączenia do kanału informacyjnego platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="6a215-173">Used as a query string to append to the Azure feed.</span></span> <span data-ttu-id="6a215-174">Umożliwia on zmianę adresu URL w celu korzystania z niepublicznych kont magazynu obiektów BLOB.</span><span class="sxs-lookup"><span data-stu-id="6a215-174">It allows changing the URL to use non-public blob storage accounts.</span></span>

- **`-ProxyAddress`**

  <span data-ttu-id="6a215-175">W przypadku ustawienia Instalator używa serwera proxy podczas wykonywania żądań sieci Web.</span><span class="sxs-lookup"><span data-stu-id="6a215-175">If set, the installer uses the proxy when making web requests.</span></span> <span data-ttu-id="6a215-176">(Prawidłowe dla systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="6a215-176">(Only valid for Windows)</span></span>

- **`ProxyUseDefaultCredentials`**

  <span data-ttu-id="6a215-177">Jeśli ta wartość jest ustawiona, Instalator użyje poświadczeń bieżącego użytkownika przy użyciu adresu serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="6a215-177">If set, the installer uses the credentials of the current user when using proxy address.</span></span> <span data-ttu-id="6a215-178">(Prawidłowe dla systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="6a215-178">(Only valid for Windows)</span></span>

- **`-SkipNonVersionedFiles`**

  <span data-ttu-id="6a215-179">Pomija Instalowanie plików nienależących do wersji, takich jak *dotnet. exe*, jeśli już istnieją.</span><span class="sxs-lookup"><span data-stu-id="6a215-179">Skips installing non-versioned files, such as *dotnet.exe*, if they already exist.</span></span>

- **`-Help`**

  <span data-ttu-id="6a215-180">Drukuje pomoc dla skryptu.</span><span class="sxs-lookup"><span data-stu-id="6a215-180">Prints out help for the script.</span></span>

## <a name="examples"></a><span data-ttu-id="6a215-181">Przykłady</span><span class="sxs-lookup"><span data-stu-id="6a215-181">Examples</span></span>

- <span data-ttu-id="6a215-182">Zainstaluj najnowszą wersję długoterminową (LTS) w lokalizacji domyślnej:</span><span class="sxs-lookup"><span data-stu-id="6a215-182">Install the latest long-term supported (LTS) version to the default location:</span></span>

  <span data-ttu-id="6a215-183">System Windows:</span><span class="sxs-lookup"><span data-stu-id="6a215-183">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel LTS
  ```

  <span data-ttu-id="6a215-184">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="6a215-184">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel LTS
  ```

- <span data-ttu-id="6a215-185">Zainstaluj najnowszą wersję z kanału 2,0 do określonej lokalizacji:</span><span class="sxs-lookup"><span data-stu-id="6a215-185">Install the latest version from 2.0 channel to the specified location:</span></span>

  <span data-ttu-id="6a215-186">System Windows:</span><span class="sxs-lookup"><span data-stu-id="6a215-186">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel 2.0 -InstallDir C:\cli
  ```

  <span data-ttu-id="6a215-187">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="6a215-187">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel 2.0 --install-dir ~/cli
  ```

- <span data-ttu-id="6a215-188">Zainstaluj wersję 1.1.0 udostępnionego środowiska uruchomieniowego:</span><span class="sxs-lookup"><span data-stu-id="6a215-188">Install the 1.1.0 version of the shared runtime:</span></span>

  <span data-ttu-id="6a215-189">System Windows:</span><span class="sxs-lookup"><span data-stu-id="6a215-189">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Runtime dotnet -Version 1.1.0
  ```

  <span data-ttu-id="6a215-190">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="6a215-190">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --runtime dotnet --version 1.1.0
  ```

- <span data-ttu-id="6a215-191">Uzyskaj skrypt i Zainstaluj wersję 2.1.2 za firmowym serwerem proxy (tylko system Windows):</span><span class="sxs-lookup"><span data-stu-id="6a215-191">Obtain script and install the 2.1.2 version behind a corporate proxy (Windows only):</span></span>

  ```powershell
  Invoke-WebRequest 'https://dot.net/v1/dotnet-install.ps1' -Proxy $env:HTTP_PROXY -ProxyUseDefaultCredentials -OutFile 'dotnet-install.ps1';
  ./dotnet-install.ps1 -InstallDir '~/.dotnet' -Version '2.1.2' -ProxyAddress $env:HTTP_PROXY -ProxyUseDefaultCredentials;
  ```

- <span data-ttu-id="6a215-192">Uzyskaj skrypt i zainstaluj interfejs wiersza polecenia platformy .NET Core przykłady jednoliniowe:</span><span class="sxs-lookup"><span data-stu-id="6a215-192">Obtain script and install .NET Core CLI one-liner examples:</span></span>

  <span data-ttu-id="6a215-193">System Windows:</span><span class="sxs-lookup"><span data-stu-id="6a215-193">Windows:</span></span>

  ```powershell
  @powershell -NoProfile -ExecutionPolicy unrestricted -Command "[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; &([scriptblock]::Create((Invoke-WebRequest -UseBasicParsing 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"
  ```

  <span data-ttu-id="6a215-194">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="6a215-194">macOS/Linux:</span></span>

  ```bash
  curl -ssl https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>
  ```

## <a name="see-also"></a><span data-ttu-id="6a215-195">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6a215-195">See also</span></span>

- [<span data-ttu-id="6a215-196">Wersje platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="6a215-196">.NET Core releases</span></span>](https://github.com/dotnet/core/releases)
- [<span data-ttu-id="6a215-197">Środowisko uruchomieniowe programu .NET Core i archiwum pobierania zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="6a215-197">.NET Core Runtime and SDK download archive</span></span>](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)

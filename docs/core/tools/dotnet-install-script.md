---
title: dotnet-install scripts
description: Więcej informacji na temat skryptów programu dotnet-Install w celu zainstalowania zestaw .NET Core SDK i udostępnionego środowiska uruchomieniowego.
ms.date: 01/23/2020
ms.openlocfilehash: bf28f872be3ac2b4115b1d5e5c06e32afec0b49e
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2020
ms.locfileid: "77092866"
---
# <a name="dotnet-install-scripts-reference"></a><span data-ttu-id="2bb07-103">dotnet — informacje o skryptach instalacji</span><span class="sxs-lookup"><span data-stu-id="2bb07-103">dotnet-install scripts reference</span></span>

## <a name="name"></a><span data-ttu-id="2bb07-104">Name (Nazwa)</span><span class="sxs-lookup"><span data-stu-id="2bb07-104">Name</span></span>

<span data-ttu-id="2bb07-105">`dotnet-install.ps1` | `dotnet-install.sh` — skrypt służący do instalowania zestaw .NET Core SDK i udostępnionego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="2bb07-105">`dotnet-install.ps1` | `dotnet-install.sh` - Script used to install the .NET Core SDK and the shared runtime.</span></span>

## <a name="synopsis"></a><span data-ttu-id="2bb07-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="2bb07-106">Synopsis</span></span>

<span data-ttu-id="2bb07-107">W systemie Windows:</span><span class="sxs-lookup"><span data-stu-id="2bb07-107">Windows:</span></span>

```powershell
dotnet-install.ps1 [-Channel] [-Version] [-JSonFile] [-InstallDir] [-Architecture]
    [-Runtime] [-DryRun] [-NoPath] [-Verbose] [-AzureFeed] [-UncachedFeed] [-NoCdn] [-FeedCredential]
    [-ProxyAddress] [-ProxyUseDefaultCredentials] [-SkipNonVersionedFiles] [-Help]
```

<span data-ttu-id="2bb07-108">Linux/macOs:</span><span class="sxs-lookup"><span data-stu-id="2bb07-108">Linux/macOs:</span></span>

```bash
dotnet-install.sh [--channel] [--version] [--jsonfile] [--install-dir] [--architecture]
    [--runtime] [--dry-run] [--no-path] [--verbose] [--azure-feed] [--uncached-feed] [--no-cdn] [--feed-credential]
    [--runtime-id] [--skip-non-versioned-files] [--help]
```

## <a name="description"></a><span data-ttu-id="2bb07-109">Opis</span><span class="sxs-lookup"><span data-stu-id="2bb07-109">Description</span></span>

<span data-ttu-id="2bb07-110">Skrypty `dotnet-install` są używane do przeprowadzania instalacji nieadministratora zestaw .NET Core SDK, która obejmuje interfejs wiersza polecenia platformy .NET Core i udostępnione środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="2bb07-110">The `dotnet-install` scripts are used to perform a non-admin installation of the .NET Core SDK, which includes the .NET Core CLI and the shared runtime.</span></span>

<span data-ttu-id="2bb07-111">Zalecamy użycie stabilnej wersji skryptów:</span><span class="sxs-lookup"><span data-stu-id="2bb07-111">We recommend that you use the stable version of the scripts:</span></span>

- <span data-ttu-id="2bb07-112">Bash (Linux/macOS): <https://dot.net/v1/dotnet-install.sh></span><span class="sxs-lookup"><span data-stu-id="2bb07-112">Bash (Linux/macOS): <https://dot.net/v1/dotnet-install.sh></span></span>
- <span data-ttu-id="2bb07-113">PowerShell (Windows): <https://dot.net/v1/dotnet-install.ps1></span><span class="sxs-lookup"><span data-stu-id="2bb07-113">PowerShell (Windows): <https://dot.net/v1/dotnet-install.ps1></span></span>

<span data-ttu-id="2bb07-114">Główna użyteczność tych skryptów jest w scenariuszach automatyzacji i instalacjach nienależących do administratora.</span><span class="sxs-lookup"><span data-stu-id="2bb07-114">The main usefulness of these scripts is in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="2bb07-115">Istnieją dwa skrypty: jeden to skrypt programu PowerShell, który działa w systemie Windows, a drugi to skrypt bash, który działa w systemie Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="2bb07-115">There are two scripts: one is a PowerShell script that works on Windows, and the other is a bash script that works on Linux/macOS.</span></span> <span data-ttu-id="2bb07-116">Oba skrypty mają takie samo zachowanie.</span><span class="sxs-lookup"><span data-stu-id="2bb07-116">Both scripts have the same behavior.</span></span> <span data-ttu-id="2bb07-117">Skrypt bash odczytuje również przełączniki programu PowerShell, dzięki czemu można użyć przełączników programu PowerShell z skryptem w systemach Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="2bb07-117">The bash script also reads PowerShell switches, so you can use PowerShell switches with the script on Linux/macOS systems.</span></span>

<span data-ttu-id="2bb07-118">Skrypty instalacyjne pobierają plik ZIP/plik tar z kompilacji interfejsu wiersza polecenia, a następnie instalują go w lokalizacji domyślnej lub w lokalizacji określonej przez `-InstallDir|--install-dir`.</span><span class="sxs-lookup"><span data-stu-id="2bb07-118">The installation scripts download the ZIP/tarball file from the CLI build drops and proceed to install it in either the default location or in a location specified by `-InstallDir|--install-dir`.</span></span> <span data-ttu-id="2bb07-119">Domyślnie skrypty instalacyjne pobierają zestaw SDK i instalują go.</span><span class="sxs-lookup"><span data-stu-id="2bb07-119">By default, the installation scripts download the SDK and install it.</span></span> <span data-ttu-id="2bb07-120">Jeśli chcesz uzyskać tylko udostępnione środowisko uruchomieniowe, określ argument `-Runtime|--runtime`.</span><span class="sxs-lookup"><span data-stu-id="2bb07-120">If you wish to only obtain the shared runtime, specify the `-Runtime|--runtime` argument.</span></span>

<span data-ttu-id="2bb07-121">Domyślnie skrypt dodaje lokalizację instalacji do $PATH bieżącej sesji.</span><span class="sxs-lookup"><span data-stu-id="2bb07-121">By default, the script adds the install location to the $PATH for the current session.</span></span> <span data-ttu-id="2bb07-122">Zastąp to zachowanie domyślne, określając argument `-NoPath|--no-path`.</span><span class="sxs-lookup"><span data-stu-id="2bb07-122">Override this default behavior by specifying the `-NoPath|--no-path` argument.</span></span>

<span data-ttu-id="2bb07-123">Przed uruchomieniem skryptu Zainstaluj wymagane [zależności](../install/dependencies.md).</span><span class="sxs-lookup"><span data-stu-id="2bb07-123">Before running the script, install the required [dependencies](../install/dependencies.md).</span></span>

<span data-ttu-id="2bb07-124">Określoną wersję można zainstalować przy użyciu argumentu `-Version|--version`.</span><span class="sxs-lookup"><span data-stu-id="2bb07-124">You can install a specific version using the `-Version|--version` argument.</span></span> <span data-ttu-id="2bb07-125">Wersja musi być określona jako wersja z trzema częściami (na przykład `2.1.0`).</span><span class="sxs-lookup"><span data-stu-id="2bb07-125">The version must be specified as a three-part version (for example, `2.1.0`).</span></span> <span data-ttu-id="2bb07-126">Jeśli nie zostanie podany, zostanie użyta wersja `latest`.</span><span class="sxs-lookup"><span data-stu-id="2bb07-126">If not provided, it uses the `latest` version.</span></span>

## <a name="options"></a><span data-ttu-id="2bb07-127">Opcje</span><span class="sxs-lookup"><span data-stu-id="2bb07-127">Options</span></span>

- **`-Channel|--channel <CHANNEL>`**

  <span data-ttu-id="2bb07-128">Określa kanał źródłowy instalacji.</span><span class="sxs-lookup"><span data-stu-id="2bb07-128">Specifies the source channel for the installation.</span></span> <span data-ttu-id="2bb07-129">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="2bb07-129">The possible values are:</span></span>

  - <span data-ttu-id="2bb07-130">`Current` — Najnowsza wersja.</span><span class="sxs-lookup"><span data-stu-id="2bb07-130">`Current` - Most current release.</span></span>
  - <span data-ttu-id="2bb07-131">`LTS`-długoterminowy kanał pomocy technicznej (większość aktualnie obsługiwanych wersji).</span><span class="sxs-lookup"><span data-stu-id="2bb07-131">`LTS` - Long-Term Support channel (most current supported release).</span></span>
  - <span data-ttu-id="2bb07-132">Dwuczęściowa wersja w formacie X. Y reprezentującym określoną wersję (na przykład `2.1` lub `3.0`).</span><span class="sxs-lookup"><span data-stu-id="2bb07-132">Two-part version in X.Y format representing a specific release (for example, `2.1` or `3.0`).</span></span>
  - <span data-ttu-id="2bb07-133">Nazwa rozgałęzienia: na przykład `release/3.1.1xx` lub `master` (dla nocnych wydań).</span><span class="sxs-lookup"><span data-stu-id="2bb07-133">Branch name: for example, `release/3.1.1xx` or `master` (for nightly releases).</span></span> <span data-ttu-id="2bb07-134">Użyj tej opcji, aby zainstalować wersję z kanału w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="2bb07-134">Use this option to install a version from a preview channel.</span></span> <span data-ttu-id="2bb07-135">Użyj nazwy kanału wymienionej w [instalatorze i plikach binarnych](https://github.com/dotnet/core-sdk#installers-and-binaries).</span><span class="sxs-lookup"><span data-stu-id="2bb07-135">Use the name of the channel as listed in [Installers and Binaries](https://github.com/dotnet/core-sdk#installers-and-binaries).</span></span>

  <span data-ttu-id="2bb07-136">Wartością domyślną jest `LTS`.</span><span class="sxs-lookup"><span data-stu-id="2bb07-136">The default value is `LTS`.</span></span> <span data-ttu-id="2bb07-137">Aby uzyskać więcej informacji na temat kanałów pomocy technicznej platformy .NET, zobacz stronę [zasady pomocy technicznej platformy .NET](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) .</span><span class="sxs-lookup"><span data-stu-id="2bb07-137">For more information on .NET support channels, see the [.NET Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) page.</span></span>

- **`-Version|--version <VERSION>`**

  <span data-ttu-id="2bb07-138">Reprezentuje konkretną wersję kompilacji.</span><span class="sxs-lookup"><span data-stu-id="2bb07-138">Represents a specific build version.</span></span> <span data-ttu-id="2bb07-139">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="2bb07-139">The possible values are:</span></span>

  - <span data-ttu-id="2bb07-140">`latest` — Najnowsza kompilacja w kanale (używana z opcją `-Channel`).</span><span class="sxs-lookup"><span data-stu-id="2bb07-140">`latest` - Latest build on the channel (used with the `-Channel` option).</span></span>
  - <span data-ttu-id="2bb07-141">`coherent`-Najnowsza spójna kompilacja na kanale; używa najnowszej stabilnej kombinacji pakietów (używanej z nazwą gałęzi `-Channel` opcjami).</span><span class="sxs-lookup"><span data-stu-id="2bb07-141">`coherent` - Latest coherent build on the channel; uses the latest stable package combination (used with Branch name `-Channel` options).</span></span>
  - <span data-ttu-id="2bb07-142">Wersja z trzech części w formacie X. Y. Z, reprezentująca konkretną wersję kompilacji; zastępuje opcję `-Channel`.</span><span class="sxs-lookup"><span data-stu-id="2bb07-142">Three-part version in X.Y.Z format representing a specific build version; supersedes the `-Channel` option.</span></span> <span data-ttu-id="2bb07-143">Na przykład: `2.0.0-preview2-006120`.</span><span class="sxs-lookup"><span data-stu-id="2bb07-143">For example: `2.0.0-preview2-006120`.</span></span>

  <span data-ttu-id="2bb07-144">Jeśli nie zostanie określony, `-Version` domyślnie `latest`.</span><span class="sxs-lookup"><span data-stu-id="2bb07-144">If not specified, `-Version` defaults to `latest`.</span></span>

- **`-JSonFile|--jsonfile <JSONFILE>`**

  <span data-ttu-id="2bb07-145">Określa ścieżkę do pliku [Global. JSON](global-json.md) , który zostanie użyty do określenia wersji zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="2bb07-145">Specifies a path to a [global.json](global-json.md) file that will be used to determine the SDK version.</span></span> <span data-ttu-id="2bb07-146">Plik *Global. JSON* musi mieć wartość `sdk:version`.</span><span class="sxs-lookup"><span data-stu-id="2bb07-146">The *global.json* file must have a value for `sdk:version`.</span></span>

- **`-InstallDir|--install-dir <DIRECTORY>`**

  <span data-ttu-id="2bb07-147">Określa ścieżkę instalacji.</span><span class="sxs-lookup"><span data-stu-id="2bb07-147">Specifies the installation path.</span></span> <span data-ttu-id="2bb07-148">Katalog zostanie utworzony, jeśli nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="2bb07-148">The directory is created if it doesn't exist.</span></span> <span data-ttu-id="2bb07-149">Wartość domyślna to *%LocalAppData%\Microsoft\dotnet*.</span><span class="sxs-lookup"><span data-stu-id="2bb07-149">The default value is *%LocalAppData%\Microsoft\dotnet*.</span></span> <span data-ttu-id="2bb07-150">Pliki binarne są umieszczane bezpośrednio w tym katalogu.</span><span class="sxs-lookup"><span data-stu-id="2bb07-150">Binaries are placed directly in this directory.</span></span>

- **`-Architecture|--architecture <ARCHITECTURE>`**

  <span data-ttu-id="2bb07-151">Architektura plików binarnych platformy .NET Core do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="2bb07-151">Architecture of the .NET Core binaries to install.</span></span> <span data-ttu-id="2bb07-152">Możliwe wartości to `<auto>`, `amd64`, `x64`, `x86`, `arm64`i `arm`.</span><span class="sxs-lookup"><span data-stu-id="2bb07-152">Possible values are `<auto>`, `amd64`, `x64`, `x86`, `arm64`, and `arm`.</span></span> <span data-ttu-id="2bb07-153">Wartość domyślna to `<auto>`, która reprezentuje aktualnie uruchomioną architekturę systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="2bb07-153">The default value is `<auto>`, which represents the currently running OS architecture.</span></span>

- **`-SharedRuntime|--shared-runtime`**

  > [!NOTE]
  > <span data-ttu-id="2bb07-154">Ten parametr jest przestarzały i może zostać usunięty w przyszłej wersji skryptu.</span><span class="sxs-lookup"><span data-stu-id="2bb07-154">This parameter is obsolete and may be removed in a future version of the script.</span></span> <span data-ttu-id="2bb07-155">Zalecaną alternatywą jest opcja `-Runtime|--runtime`.</span><span class="sxs-lookup"><span data-stu-id="2bb07-155">The recommended alternative is the `-Runtime|--runtime` option.</span></span>

  <span data-ttu-id="2bb07-156">Instaluje tylko udostępnione bity środowiska uruchomieniowego, a nie cały zestaw SDK.</span><span class="sxs-lookup"><span data-stu-id="2bb07-156">Installs just the shared runtime bits, not the entire SDK.</span></span> <span data-ttu-id="2bb07-157">Ta opcja jest równoznaczna z określeniem `-Runtime|--runtime dotnet`.</span><span class="sxs-lookup"><span data-stu-id="2bb07-157">This option is equivalent to specifying `-Runtime|--runtime dotnet`.</span></span>

- **`-Runtime|--runtime <RUNTIME>`**

  <span data-ttu-id="2bb07-158">Instaluje tylko udostępnione środowisko uruchomieniowe, a nie cały zestaw SDK.</span><span class="sxs-lookup"><span data-stu-id="2bb07-158">Installs just the shared runtime, not the entire SDK.</span></span> <span data-ttu-id="2bb07-159">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="2bb07-159">The possible values are:</span></span>

  - <span data-ttu-id="2bb07-160">`dotnet` — `Microsoft.NETCore.App` udostępnionego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="2bb07-160">`dotnet` - the `Microsoft.NETCore.App` shared runtime.</span></span>
  - <span data-ttu-id="2bb07-161">`aspnetcore` — `Microsoft.AspNetCore.App` udostępnionego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="2bb07-161">`aspnetcore` - the `Microsoft.AspNetCore.App` shared runtime.</span></span>
  - <span data-ttu-id="2bb07-162">`windowsdesktop` — `Microsoft.WindowsDesktop.App` udostępnionego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="2bb07-162">`windowsdesktop` - the `Microsoft.WindowsDesktop.App` shared runtime.</span></span>

- **`-DryRun|--dry-run`**

  <span data-ttu-id="2bb07-163">W przypadku ustawienia skrypt nie wykona instalacji.</span><span class="sxs-lookup"><span data-stu-id="2bb07-163">If set, the script won't perform the installation.</span></span> <span data-ttu-id="2bb07-164">Zamiast tego Wyświetla on wiersz polecenia, który służy do spójnej instalacji aktualnie żądanej wersji interfejs wiersza polecenia platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2bb07-164">Instead, it displays what command line to use to consistently install the currently requested version of the .NET Core CLI.</span></span> <span data-ttu-id="2bb07-165">Jeśli na przykład zostanie określona wersja `latest`, zostanie wyświetlony link z określoną wersją, aby można było użyć tego polecenia w sposób jednoznaczny w skrypcie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="2bb07-165">For example, if you specify version `latest`, it displays a link with the specific version so that this command can be used deterministically in a build script.</span></span> <span data-ttu-id="2bb07-166">Wyświetla również lokalizację pliku binarnego, jeśli wolisz zainstalować lub pobrać ją samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="2bb07-166">It also displays the binary's location if you prefer to install or download it yourself.</span></span>

- **`-NoPath|--no-path`**

  <span data-ttu-id="2bb07-167">W przypadku ustawienia folder instalacyjny nie zostanie wyeksportowany do ścieżki bieżącej sesji.</span><span class="sxs-lookup"><span data-stu-id="2bb07-167">If set, the installation folder isn't exported to the path for the current session.</span></span> <span data-ttu-id="2bb07-168">Domyślnie skrypt modyfikuje ścieżkę, co sprawia, że interfejs wiersza polecenia platformy .NET Core dostępne natychmiast po instalacji.</span><span class="sxs-lookup"><span data-stu-id="2bb07-168">By default, the script modifies the PATH, which makes the .NET Core CLI available immediately after install.</span></span>

- **`-Verbose|--verbose`**

  <span data-ttu-id="2bb07-169">Wyświetla informacje diagnostyczne.</span><span class="sxs-lookup"><span data-stu-id="2bb07-169">Displays diagnostics information.</span></span>

- **`-AzureFeed|--azure-feed`**

  <span data-ttu-id="2bb07-170">Określa adres URL źródła danych platformy Azure do Instalatora.</span><span class="sxs-lookup"><span data-stu-id="2bb07-170">Specifies the URL for the Azure feed to the installer.</span></span> <span data-ttu-id="2bb07-171">Zaleca się, aby nie zmieniać tej wartości.</span><span class="sxs-lookup"><span data-stu-id="2bb07-171">We recommended that you don't change this value.</span></span> <span data-ttu-id="2bb07-172">Wartością domyślną jest `https://dotnetcli.azureedge.net/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="2bb07-172">The default value is `https://dotnetcli.azureedge.net/dotnet`.</span></span>

- **`-UncachedFeed|--uncached-feed`**

  <span data-ttu-id="2bb07-173">Umożliwia zmianę adresu URL dla niebuforowanego źródła danych używanego przez ten Instalator.</span><span class="sxs-lookup"><span data-stu-id="2bb07-173">Allows changing the URL for the uncached feed used by this installer.</span></span> <span data-ttu-id="2bb07-174">Zaleca się, aby nie zmieniać tej wartości.</span><span class="sxs-lookup"><span data-stu-id="2bb07-174">We recommended that you don't change this value.</span></span>

- **`-NoCdn|--no-cdn`**

  <span data-ttu-id="2bb07-175">Wyłącza pobieranie z [usługi Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) i bezpośrednio używa niebuforowanego źródła danych.</span><span class="sxs-lookup"><span data-stu-id="2bb07-175">Disables downloading from the [Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) and uses the uncached feed directly.</span></span>

- **`-FeedCredential|--feed-credential`**

  <span data-ttu-id="2bb07-176">Służy jako ciąg zapytania do dołączenia do kanału informacyjnego platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="2bb07-176">Used as a query string to append to the Azure feed.</span></span> <span data-ttu-id="2bb07-177">Umożliwia on zmianę adresu URL w celu korzystania z niepublicznych kont magazynu obiektów BLOB.</span><span class="sxs-lookup"><span data-stu-id="2bb07-177">It allows changing the URL to use non-public blob storage accounts.</span></span>

- **`--runtime-id`**

  <span data-ttu-id="2bb07-178">Określa [Identyfikator środowiska uruchomieniowego](../rid-catalog.md) , dla którego instalowane są narzędzia.</span><span class="sxs-lookup"><span data-stu-id="2bb07-178">Specifies the [runtime identifier](../rid-catalog.md) for which the tools are being installed.</span></span> <span data-ttu-id="2bb07-179">Użyj `linux-x64` dla przenośnego systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="2bb07-179">Use `linux-x64` for portable Linux.</span></span> <span data-ttu-id="2bb07-180">(Prawidłowy tylko dla systemu Linux/macOS)</span><span class="sxs-lookup"><span data-stu-id="2bb07-180">(Only valid for Linux/macOS)</span></span>

- **`-ProxyAddress`**

  <span data-ttu-id="2bb07-181">W przypadku ustawienia Instalator używa serwera proxy podczas wykonywania żądań sieci Web.</span><span class="sxs-lookup"><span data-stu-id="2bb07-181">If set, the installer uses the proxy when making web requests.</span></span> <span data-ttu-id="2bb07-182">(Prawidłowe dla systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="2bb07-182">(Only valid for Windows)</span></span>

- **`ProxyUseDefaultCredentials`**

  <span data-ttu-id="2bb07-183">Jeśli ta wartość jest ustawiona, Instalator użyje poświadczeń bieżącego użytkownika przy użyciu adresu serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="2bb07-183">If set, the installer uses the credentials of the current user when using proxy address.</span></span> <span data-ttu-id="2bb07-184">(Prawidłowe dla systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="2bb07-184">(Only valid for Windows)</span></span>

- **`-SkipNonVersionedFiles|--skip-non-versioned-files`**

  <span data-ttu-id="2bb07-185">Pomija Instalowanie plików nienależących do wersji, takich jak *dotnet. exe*, jeśli już istnieją.</span><span class="sxs-lookup"><span data-stu-id="2bb07-185">Skips installing non-versioned files, such as *dotnet.exe*, if they already exist.</span></span>

- **`-Help|--help`**

  <span data-ttu-id="2bb07-186">Drukuje pomoc dla skryptu.</span><span class="sxs-lookup"><span data-stu-id="2bb07-186">Prints out help for the script.</span></span>

## <a name="examples"></a><span data-ttu-id="2bb07-187">Przykłady</span><span class="sxs-lookup"><span data-stu-id="2bb07-187">Examples</span></span>

- <span data-ttu-id="2bb07-188">Zainstaluj najnowszą wersję długoterminową (LTS) w lokalizacji domyślnej:</span><span class="sxs-lookup"><span data-stu-id="2bb07-188">Install the latest long-term supported (LTS) version to the default location:</span></span>

  <span data-ttu-id="2bb07-189">W systemie Windows:</span><span class="sxs-lookup"><span data-stu-id="2bb07-189">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel LTS
  ```

  <span data-ttu-id="2bb07-190">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="2bb07-190">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel LTS
  ```

- <span data-ttu-id="2bb07-191">Zainstaluj najnowszą wersję z kanału 3,1 do określonej lokalizacji:</span><span class="sxs-lookup"><span data-stu-id="2bb07-191">Install the latest version from 3.1 channel to the specified location:</span></span>

  <span data-ttu-id="2bb07-192">W systemie Windows:</span><span class="sxs-lookup"><span data-stu-id="2bb07-192">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel 3.1 -InstallDir C:\cli
  ```

  <span data-ttu-id="2bb07-193">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="2bb07-193">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel 3.1 --install-dir ~/cli
  ```

- <span data-ttu-id="2bb07-194">Zainstaluj wersję 3.0.0 udostępnionego środowiska uruchomieniowego:</span><span class="sxs-lookup"><span data-stu-id="2bb07-194">Install the 3.0.0 version of the shared runtime:</span></span>

  <span data-ttu-id="2bb07-195">W systemie Windows:</span><span class="sxs-lookup"><span data-stu-id="2bb07-195">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Runtime dotnet -Version 3.0.0
  ```

  <span data-ttu-id="2bb07-196">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="2bb07-196">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --runtime dotnet --version 3.0.0
  ```

- <span data-ttu-id="2bb07-197">Uzyskaj skrypt i Zainstaluj wersję 2.1.2 za firmowym serwerem proxy (tylko system Windows):</span><span class="sxs-lookup"><span data-stu-id="2bb07-197">Obtain script and install the 2.1.2 version behind a corporate proxy (Windows only):</span></span>

  ```powershell
  Invoke-WebRequest 'https://dot.net/v1/dotnet-install.ps1' -Proxy $env:HTTP_PROXY -ProxyUseDefaultCredentials -OutFile 'dotnet-install.ps1';
  ./dotnet-install.ps1 -InstallDir '~/.dotnet' -Version '2.1.2' -ProxyAddress $env:HTTP_PROXY -ProxyUseDefaultCredentials;
  ```

- <span data-ttu-id="2bb07-198">Uzyskaj skrypt i zainstaluj interfejs wiersza polecenia platformy .NET Core przykłady jednoliniowe:</span><span class="sxs-lookup"><span data-stu-id="2bb07-198">Obtain script and install .NET Core CLI one-liner examples:</span></span>

  <span data-ttu-id="2bb07-199">W systemie Windows:</span><span class="sxs-lookup"><span data-stu-id="2bb07-199">Windows:</span></span>

  ```powershell
  # Run a separate PowerShell process because the script calls exit, so it will end the current PowerShell session.
  &powershell -NoProfile -ExecutionPolicy unrestricted -Command "[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; &([scriptblock]::Create((Invoke-WebRequest -UseBasicParsing 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"
  ```

  <span data-ttu-id="2bb07-200">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="2bb07-200">macOS/Linux:</span></span>

  ```bash
  curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>
  ```

## <a name="see-also"></a><span data-ttu-id="2bb07-201">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2bb07-201">See also</span></span>

- [<span data-ttu-id="2bb07-202">Wersje platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="2bb07-202">.NET Core releases</span></span>](https://github.com/dotnet/core/releases)
- [<span data-ttu-id="2bb07-203">Środowisko uruchomieniowe programu .NET Core i archiwum pobierania zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="2bb07-203">.NET Core Runtime and SDK download archive</span></span>](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)

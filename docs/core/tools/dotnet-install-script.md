---
title: dotnet-install scripts
description: Dowiedz się więcej o skryptach dotnet-install, aby zainstalować zestaw SDK .NET Core i udostępniony program runtime.
ms.date: 01/23/2020
ms.openlocfilehash: bf28f872be3ac2b4115b1d5e5c06e32afec0b49e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77092866"
---
# <a name="dotnet-install-scripts-reference"></a><span data-ttu-id="a318f-103">Odwołanie doskryptów dotnet-install</span><span class="sxs-lookup"><span data-stu-id="a318f-103">dotnet-install scripts reference</span></span>

## <a name="name"></a><span data-ttu-id="a318f-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="a318f-104">Name</span></span>

<span data-ttu-id="a318f-105">`dotnet-install.ps1` | `dotnet-install.sh`- Skrypt używany do instalowania .NET Core SDK i udostępnionego programu runtime.</span><span class="sxs-lookup"><span data-stu-id="a318f-105">`dotnet-install.ps1` | `dotnet-install.sh` - Script used to install the .NET Core SDK and the shared runtime.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a318f-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="a318f-106">Synopsis</span></span>

<span data-ttu-id="a318f-107">W systemie Windows:</span><span class="sxs-lookup"><span data-stu-id="a318f-107">Windows:</span></span>

```powershell
dotnet-install.ps1 [-Channel] [-Version] [-JSonFile] [-InstallDir] [-Architecture]
    [-Runtime] [-DryRun] [-NoPath] [-Verbose] [-AzureFeed] [-UncachedFeed] [-NoCdn] [-FeedCredential]
    [-ProxyAddress] [-ProxyUseDefaultCredentials] [-SkipNonVersionedFiles] [-Help]
```

<span data-ttu-id="a318f-108">Linux/ macOs:</span><span class="sxs-lookup"><span data-stu-id="a318f-108">Linux/macOs:</span></span>

```bash
dotnet-install.sh [--channel] [--version] [--jsonfile] [--install-dir] [--architecture]
    [--runtime] [--dry-run] [--no-path] [--verbose] [--azure-feed] [--uncached-feed] [--no-cdn] [--feed-credential]
    [--runtime-id] [--skip-non-versioned-files] [--help]
```

## <a name="description"></a><span data-ttu-id="a318f-109">Opis</span><span class="sxs-lookup"><span data-stu-id="a318f-109">Description</span></span>

<span data-ttu-id="a318f-110">Skrypty `dotnet-install` są używane do wykonywania instalacji bez administratora .NET Core SDK, która obejmuje .NET Core CLI i udostępnionego programu runtime.</span><span class="sxs-lookup"><span data-stu-id="a318f-110">The `dotnet-install` scripts are used to perform a non-admin installation of the .NET Core SDK, which includes the .NET Core CLI and the shared runtime.</span></span>

<span data-ttu-id="a318f-111">Zaleca się użycie stabilnej wersji skryptów:</span><span class="sxs-lookup"><span data-stu-id="a318f-111">We recommend that you use the stable version of the scripts:</span></span>

- <span data-ttu-id="a318f-112">Bash (Linux/macOS):<https://dot.net/v1/dotnet-install.sh></span><span class="sxs-lookup"><span data-stu-id="a318f-112">Bash (Linux/macOS): <https://dot.net/v1/dotnet-install.sh></span></span>
- <span data-ttu-id="a318f-113">Program PowerShell (Windows):<https://dot.net/v1/dotnet-install.ps1></span><span class="sxs-lookup"><span data-stu-id="a318f-113">PowerShell (Windows): <https://dot.net/v1/dotnet-install.ps1></span></span>

<span data-ttu-id="a318f-114">Główną przydatność tych skryptów jest w scenariuszach automatyzacji i instalacji nie-administratora.</span><span class="sxs-lookup"><span data-stu-id="a318f-114">The main usefulness of these scripts is in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="a318f-115">Istnieją dwa skrypty: jeden jest skrypt programu PowerShell, który działa w systemie Windows, a drugi jest skrypt bash, który działa na Linux / macOS.</span><span class="sxs-lookup"><span data-stu-id="a318f-115">There are two scripts: one is a PowerShell script that works on Windows, and the other is a bash script that works on Linux/macOS.</span></span> <span data-ttu-id="a318f-116">Oba skrypty mają takie samo zachowanie.</span><span class="sxs-lookup"><span data-stu-id="a318f-116">Both scripts have the same behavior.</span></span> <span data-ttu-id="a318f-117">Skrypt bash odczytuje również przełączniki programu PowerShell, dzięki czemu można używać przełączników programu PowerShell ze skryptem w systemach Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="a318f-117">The bash script also reads PowerShell switches, so you can use PowerShell switches with the script on Linux/macOS systems.</span></span>

<span data-ttu-id="a318f-118">Skrypty instalacyjne pobierają plik ZIP/tarball z kompilacji CLI i kontynuują instalację w lokalizacji `-InstallDir|--install-dir`domyślnej lub w lokalizacji określonej przez .</span><span class="sxs-lookup"><span data-stu-id="a318f-118">The installation scripts download the ZIP/tarball file from the CLI build drops and proceed to install it in either the default location or in a location specified by `-InstallDir|--install-dir`.</span></span> <span data-ttu-id="a318f-119">Domyślnie skrypty instalacyjne pobierają zestaw SDK i instalują go.</span><span class="sxs-lookup"><span data-stu-id="a318f-119">By default, the installation scripts download the SDK and install it.</span></span> <span data-ttu-id="a318f-120">Jeśli chcesz uzyskać tylko udostępnionego czasu `-Runtime|--runtime` wykonywania, należy określić argument.</span><span class="sxs-lookup"><span data-stu-id="a318f-120">If you wish to only obtain the shared runtime, specify the `-Runtime|--runtime` argument.</span></span>

<span data-ttu-id="a318f-121">Domyślnie skrypt dodaje lokalizację instalacji do $PATH dla bieżącej sesji.</span><span class="sxs-lookup"><span data-stu-id="a318f-121">By default, the script adds the install location to the $PATH for the current session.</span></span> <span data-ttu-id="a318f-122">Zastąp to domyślne `-NoPath|--no-path` zachowanie, określając argument.</span><span class="sxs-lookup"><span data-stu-id="a318f-122">Override this default behavior by specifying the `-NoPath|--no-path` argument.</span></span>

<span data-ttu-id="a318f-123">Przed uruchomieniem skryptu zainstaluj wymagane [zależności](../install/dependencies.md).</span><span class="sxs-lookup"><span data-stu-id="a318f-123">Before running the script, install the required [dependencies](../install/dependencies.md).</span></span>

<span data-ttu-id="a318f-124">Można zainstalować określoną wersję `-Version|--version` przy użyciu argumentu.</span><span class="sxs-lookup"><span data-stu-id="a318f-124">You can install a specific version using the `-Version|--version` argument.</span></span> <span data-ttu-id="a318f-125">Wersja musi być określona jako wersja trzyczęściowa `2.1.0`(na przykład).</span><span class="sxs-lookup"><span data-stu-id="a318f-125">The version must be specified as a three-part version (for example, `2.1.0`).</span></span> <span data-ttu-id="a318f-126">Jeśli nie podano, `latest` używa wersji.</span><span class="sxs-lookup"><span data-stu-id="a318f-126">If not provided, it uses the `latest` version.</span></span>

## <a name="options"></a><span data-ttu-id="a318f-127">Opcje</span><span class="sxs-lookup"><span data-stu-id="a318f-127">Options</span></span>

- **`-Channel|--channel <CHANNEL>`**

  <span data-ttu-id="a318f-128">Określa kanał źródłowy instalacji.</span><span class="sxs-lookup"><span data-stu-id="a318f-128">Specifies the source channel for the installation.</span></span> <span data-ttu-id="a318f-129">Możliwe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="a318f-129">The possible values are:</span></span>

  - <span data-ttu-id="a318f-130">`Current`- Większość bieżącego wydania.</span><span class="sxs-lookup"><span data-stu-id="a318f-130">`Current` - Most current release.</span></span>
  - <span data-ttu-id="a318f-131">`LTS`- Kanał wsparcia długoterminowego (najbardziej aktualna obsługiwana wersja).</span><span class="sxs-lookup"><span data-stu-id="a318f-131">`LTS` - Long-Term Support channel (most current supported release).</span></span>
  - <span data-ttu-id="a318f-132">Wersja dwuczęściowa w formacie X.Y reprezentująca określoną `2.1` `3.0`wersję (na przykład lub ).</span><span class="sxs-lookup"><span data-stu-id="a318f-132">Two-part version in X.Y format representing a specific release (for example, `2.1` or `3.0`).</span></span>
  - <span data-ttu-id="a318f-133">Nazwa gałęzi: na `release/3.1.1xx` `master` przykład lub (dla wersji nocnych).</span><span class="sxs-lookup"><span data-stu-id="a318f-133">Branch name: for example, `release/3.1.1xx` or `master` (for nightly releases).</span></span> <span data-ttu-id="a318f-134">Użyj tej opcji, aby zainstalować wersję z kanału podglądu.</span><span class="sxs-lookup"><span data-stu-id="a318f-134">Use this option to install a version from a preview channel.</span></span> <span data-ttu-id="a318f-135">Użyj nazwy kanału wymienionej w [instalatorach i plikach binarnych](https://github.com/dotnet/core-sdk#installers-and-binaries).</span><span class="sxs-lookup"><span data-stu-id="a318f-135">Use the name of the channel as listed in [Installers and Binaries](https://github.com/dotnet/core-sdk#installers-and-binaries).</span></span>

  <span data-ttu-id="a318f-136">Wartością domyślną jest `LTS`.</span><span class="sxs-lookup"><span data-stu-id="a318f-136">The default value is `LTS`.</span></span> <span data-ttu-id="a318f-137">Aby uzyskać więcej informacji na temat kanałów pomocy technicznej .NET, zobacz stronę [Zasady pomocy technicznej .NET.](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)</span><span class="sxs-lookup"><span data-stu-id="a318f-137">For more information on .NET support channels, see the [.NET Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) page.</span></span>

- **`-Version|--version <VERSION>`**

  <span data-ttu-id="a318f-138">Reprezentuje określoną wersję kompilacji.</span><span class="sxs-lookup"><span data-stu-id="a318f-138">Represents a specific build version.</span></span> <span data-ttu-id="a318f-139">Możliwe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="a318f-139">The possible values are:</span></span>

  - <span data-ttu-id="a318f-140">`latest`- Najnowsza kompilacja na `-Channel` kanale (używana z opcją).</span><span class="sxs-lookup"><span data-stu-id="a318f-140">`latest` - Latest build on the channel (used with the `-Channel` option).</span></span>
  - <span data-ttu-id="a318f-141">`coherent`- Najnowsza spójna kompilacja na kanale; używa najnowszej stabilnej kombinacji `-Channel` pakietów (używanej z opcjami nazwy gałęzi).</span><span class="sxs-lookup"><span data-stu-id="a318f-141">`coherent` - Latest coherent build on the channel; uses the latest stable package combination (used with Branch name `-Channel` options).</span></span>
  - <span data-ttu-id="a318f-142">Wersja trzyczęściowa w formacie X.Y.Z reprezentująca określoną wersję kompilacji; zastępuje `-Channel` tę opcję.</span><span class="sxs-lookup"><span data-stu-id="a318f-142">Three-part version in X.Y.Z format representing a specific build version; supersedes the `-Channel` option.</span></span> <span data-ttu-id="a318f-143">Na przykład: `2.0.0-preview2-006120`.</span><span class="sxs-lookup"><span data-stu-id="a318f-143">For example: `2.0.0-preview2-006120`.</span></span>

  <span data-ttu-id="a318f-144">Jeśli nie zostanie `-Version` określony, `latest`domyślnie .</span><span class="sxs-lookup"><span data-stu-id="a318f-144">If not specified, `-Version` defaults to `latest`.</span></span>

- **`-JSonFile|--jsonfile <JSONFILE>`**

  <span data-ttu-id="a318f-145">Określa ścieżkę do pliku [global.json,](global-json.md) która będzie używana do określania wersji sdk.</span><span class="sxs-lookup"><span data-stu-id="a318f-145">Specifies a path to a [global.json](global-json.md) file that will be used to determine the SDK version.</span></span> <span data-ttu-id="a318f-146">Plik *global.json* musi mieć `sdk:version`wartość dla .</span><span class="sxs-lookup"><span data-stu-id="a318f-146">The *global.json* file must have a value for `sdk:version`.</span></span>

- **`-InstallDir|--install-dir <DIRECTORY>`**

  <span data-ttu-id="a318f-147">Określa ścieżkę instalacji.</span><span class="sxs-lookup"><span data-stu-id="a318f-147">Specifies the installation path.</span></span> <span data-ttu-id="a318f-148">Katalog jest tworzony, jeśli nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="a318f-148">The directory is created if it doesn't exist.</span></span> <span data-ttu-id="a318f-149">Wartością domyślną jest *%LocalAppData%\Microsoft\dotnet*.</span><span class="sxs-lookup"><span data-stu-id="a318f-149">The default value is *%LocalAppData%\Microsoft\dotnet*.</span></span> <span data-ttu-id="a318f-150">Pliki binarne są umieszczane bezpośrednio w tym katalogu.</span><span class="sxs-lookup"><span data-stu-id="a318f-150">Binaries are placed directly in this directory.</span></span>

- **`-Architecture|--architecture <ARCHITECTURE>`**

  <span data-ttu-id="a318f-151">Architektura plików binarnych .NET Core do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="a318f-151">Architecture of the .NET Core binaries to install.</span></span> <span data-ttu-id="a318f-152">Możliwe wartości `<auto>` `amd64`to `x64` `x86`, `arm64`, `arm`, , i .</span><span class="sxs-lookup"><span data-stu-id="a318f-152">Possible values are `<auto>`, `amd64`, `x64`, `x86`, `arm64`, and `arm`.</span></span> <span data-ttu-id="a318f-153">Wartością domyślną jest `<auto>`, która reprezentuje aktualnie uruchomioną architekturę os.</span><span class="sxs-lookup"><span data-stu-id="a318f-153">The default value is `<auto>`, which represents the currently running OS architecture.</span></span>

- **`-SharedRuntime|--shared-runtime`**

  > [!NOTE]
  > <span data-ttu-id="a318f-154">Ten parametr jest przestarzały i może zostać usunięty w przyszłej wersji skryptu.</span><span class="sxs-lookup"><span data-stu-id="a318f-154">This parameter is obsolete and may be removed in a future version of the script.</span></span> <span data-ttu-id="a318f-155">Zalecaną alternatywą `-Runtime|--runtime` jest opcja.</span><span class="sxs-lookup"><span data-stu-id="a318f-155">The recommended alternative is the `-Runtime|--runtime` option.</span></span>

  <span data-ttu-id="a318f-156">Instaluje tylko udostępnione bity czasu wykonywania, a nie cały zestaw SDK.</span><span class="sxs-lookup"><span data-stu-id="a318f-156">Installs just the shared runtime bits, not the entire SDK.</span></span> <span data-ttu-id="a318f-157">Ta opcja jest równoważna z określeniem `-Runtime|--runtime dotnet`.</span><span class="sxs-lookup"><span data-stu-id="a318f-157">This option is equivalent to specifying `-Runtime|--runtime dotnet`.</span></span>

- **`-Runtime|--runtime <RUNTIME>`**

  <span data-ttu-id="a318f-158">Instaluje tylko udostępniony czas wykonywania, a nie cały zestaw SDK.</span><span class="sxs-lookup"><span data-stu-id="a318f-158">Installs just the shared runtime, not the entire SDK.</span></span> <span data-ttu-id="a318f-159">Możliwe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="a318f-159">The possible values are:</span></span>

  - <span data-ttu-id="a318f-160">`dotnet`- `Microsoft.NETCore.App` udostępnionego czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="a318f-160">`dotnet` - the `Microsoft.NETCore.App` shared runtime.</span></span>
  - <span data-ttu-id="a318f-161">`aspnetcore`- `Microsoft.AspNetCore.App` udostępnionego czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="a318f-161">`aspnetcore` - the `Microsoft.AspNetCore.App` shared runtime.</span></span>
  - <span data-ttu-id="a318f-162">`windowsdesktop`- `Microsoft.WindowsDesktop.App` udostępnionego czasu wykonywania.</span><span class="sxs-lookup"><span data-stu-id="a318f-162">`windowsdesktop` - the `Microsoft.WindowsDesktop.App` shared runtime.</span></span>

- **`-DryRun|--dry-run`**

  <span data-ttu-id="a318f-163">Jeśli jest ustawiona, skrypt nie będzie wykonywać instalacji.</span><span class="sxs-lookup"><span data-stu-id="a318f-163">If set, the script won't perform the installation.</span></span> <span data-ttu-id="a318f-164">Zamiast tego wyświetla wiersz polecenia, który ma być używany do konsekwentnego instalowania aktualnie żądanej wersji wiersza wiersza wiersza wiersza wiersza wiersza .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a318f-164">Instead, it displays what command line to use to consistently install the currently requested version of the .NET Core CLI.</span></span> <span data-ttu-id="a318f-165">Na przykład, jeśli `latest`określisz wersję, wyświetla łącze z określoną wersją, dzięki czemu to polecenie może być używane deterministycznie w skrypcie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="a318f-165">For example, if you specify version `latest`, it displays a link with the specific version so that this command can be used deterministically in a build script.</span></span> <span data-ttu-id="a318f-166">Wyświetla również lokalizację pliku binarnego, jeśli wolisz zainstalować lub pobrać go samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="a318f-166">It also displays the binary's location if you prefer to install or download it yourself.</span></span>

- **`-NoPath|--no-path`**

  <span data-ttu-id="a318f-167">Jeśli jest ustawiona, folder instalacyjny nie jest eksportowany do ścieżki dla bieżącej sesji.</span><span class="sxs-lookup"><span data-stu-id="a318f-167">If set, the installation folder isn't exported to the path for the current session.</span></span> <span data-ttu-id="a318f-168">Domyślnie skrypt modyfikuje PATH, co sprawia, że .NET Core CLI dostępne natychmiast po zainstalowaniu.</span><span class="sxs-lookup"><span data-stu-id="a318f-168">By default, the script modifies the PATH, which makes the .NET Core CLI available immediately after install.</span></span>

- **`-Verbose|--verbose`**

  <span data-ttu-id="a318f-169">Wyświetla informacje diagnostyczne.</span><span class="sxs-lookup"><span data-stu-id="a318f-169">Displays diagnostics information.</span></span>

- **`-AzureFeed|--azure-feed`**

  <span data-ttu-id="a318f-170">Określa adres URL źródła danych platformy Azure do instalatora.</span><span class="sxs-lookup"><span data-stu-id="a318f-170">Specifies the URL for the Azure feed to the installer.</span></span> <span data-ttu-id="a318f-171">Zalecamy, aby nie zmieniać tej wartości.</span><span class="sxs-lookup"><span data-stu-id="a318f-171">We recommended that you don't change this value.</span></span> <span data-ttu-id="a318f-172">Wartością domyślną jest `https://dotnetcli.azureedge.net/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="a318f-172">The default value is `https://dotnetcli.azureedge.net/dotnet`.</span></span>

- **`-UncachedFeed|--uncached-feed`**

  <span data-ttu-id="a318f-173">Umożliwia zmianę adresu URL niebuforowanego źródła danych używanego przez tego instalatora.</span><span class="sxs-lookup"><span data-stu-id="a318f-173">Allows changing the URL for the uncached feed used by this installer.</span></span> <span data-ttu-id="a318f-174">Zalecamy, aby nie zmieniać tej wartości.</span><span class="sxs-lookup"><span data-stu-id="a318f-174">We recommended that you don't change this value.</span></span>

- **`-NoCdn|--no-cdn`**

  <span data-ttu-id="a318f-175">Wyłącza pobieranie z [usługi Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) i bezpośrednio używa niebuforowego źródła danych.</span><span class="sxs-lookup"><span data-stu-id="a318f-175">Disables downloading from the [Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) and uses the uncached feed directly.</span></span>

- **`-FeedCredential|--feed-credential`**

  <span data-ttu-id="a318f-176">Używany jako ciąg zapytania do dostawienia do źródła danych platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="a318f-176">Used as a query string to append to the Azure feed.</span></span> <span data-ttu-id="a318f-177">Umożliwia zmianę adresu URL do używania niepublicznych kont magazynu obiektów blob.</span><span class="sxs-lookup"><span data-stu-id="a318f-177">It allows changing the URL to use non-public blob storage accounts.</span></span>

- **`--runtime-id`**

  <span data-ttu-id="a318f-178">Określa [identyfikator czasu wykonywania,](../rid-catalog.md) dla którego są instalowane narzędzia.</span><span class="sxs-lookup"><span data-stu-id="a318f-178">Specifies the [runtime identifier](../rid-catalog.md) for which the tools are being installed.</span></span> <span data-ttu-id="a318f-179">Służy `linux-x64` do przenośnego linuksa.</span><span class="sxs-lookup"><span data-stu-id="a318f-179">Use `linux-x64` for portable Linux.</span></span> <span data-ttu-id="a318f-180">(Obowiązuje tylko dla systemu Linux/macOS)</span><span class="sxs-lookup"><span data-stu-id="a318f-180">(Only valid for Linux/macOS)</span></span>

- **`-ProxyAddress`**

  <span data-ttu-id="a318f-181">Jeśli jest ustawiona, instalator używa serwera proxy podczas tworzenia żądań sieci web.</span><span class="sxs-lookup"><span data-stu-id="a318f-181">If set, the installer uses the proxy when making web requests.</span></span> <span data-ttu-id="a318f-182">(Obowiązuje tylko dla systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="a318f-182">(Only valid for Windows)</span></span>

- **`ProxyUseDefaultCredentials`**

  <span data-ttu-id="a318f-183">Jeśli jest ustawiona, instalator używa poświadczeń bieżącego użytkownika podczas korzystania z adresu serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="a318f-183">If set, the installer uses the credentials of the current user when using proxy address.</span></span> <span data-ttu-id="a318f-184">(Obowiązuje tylko dla systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="a318f-184">(Only valid for Windows)</span></span>

- **`-SkipNonVersionedFiles|--skip-non-versioned-files`**

  <span data-ttu-id="a318f-185">Pomija instalowanie plików niewersjonowanych, takich jak *dotnet.exe*, jeśli już istnieją.</span><span class="sxs-lookup"><span data-stu-id="a318f-185">Skips installing non-versioned files, such as *dotnet.exe*, if they already exist.</span></span>

- **`-Help|--help`**

  <span data-ttu-id="a318f-186">Drukuje pomoc dla skryptu.</span><span class="sxs-lookup"><span data-stu-id="a318f-186">Prints out help for the script.</span></span>

## <a name="examples"></a><span data-ttu-id="a318f-187">Przykłady</span><span class="sxs-lookup"><span data-stu-id="a318f-187">Examples</span></span>

- <span data-ttu-id="a318f-188">Zainstaluj najnowszą długoterminową wersję obsługiwaną (LTS) do lokalizacji domyślnej:</span><span class="sxs-lookup"><span data-stu-id="a318f-188">Install the latest long-term supported (LTS) version to the default location:</span></span>

  <span data-ttu-id="a318f-189">W systemie Windows:</span><span class="sxs-lookup"><span data-stu-id="a318f-189">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel LTS
  ```

  <span data-ttu-id="a318f-190">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="a318f-190">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel LTS
  ```

- <span data-ttu-id="a318f-191">Zainstaluj najnowszą wersję z kanału 3.1 do określonej lokalizacji:</span><span class="sxs-lookup"><span data-stu-id="a318f-191">Install the latest version from 3.1 channel to the specified location:</span></span>

  <span data-ttu-id="a318f-192">W systemie Windows:</span><span class="sxs-lookup"><span data-stu-id="a318f-192">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel 3.1 -InstallDir C:\cli
  ```

  <span data-ttu-id="a318f-193">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="a318f-193">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel 3.1 --install-dir ~/cli
  ```

- <span data-ttu-id="a318f-194">Zainstaluj wersję 3.0.0 udostępnionego programu runtime:</span><span class="sxs-lookup"><span data-stu-id="a318f-194">Install the 3.0.0 version of the shared runtime:</span></span>

  <span data-ttu-id="a318f-195">W systemie Windows:</span><span class="sxs-lookup"><span data-stu-id="a318f-195">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Runtime dotnet -Version 3.0.0
  ```

  <span data-ttu-id="a318f-196">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="a318f-196">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --runtime dotnet --version 3.0.0
  ```

- <span data-ttu-id="a318f-197">Uzyskaj skrypt i zainstaluj wersję 2.1.2 za korporacyjnym serwerem proxy (tylko system Windows):</span><span class="sxs-lookup"><span data-stu-id="a318f-197">Obtain script and install the 2.1.2 version behind a corporate proxy (Windows only):</span></span>

  ```powershell
  Invoke-WebRequest 'https://dot.net/v1/dotnet-install.ps1' -Proxy $env:HTTP_PROXY -ProxyUseDefaultCredentials -OutFile 'dotnet-install.ps1';
  ./dotnet-install.ps1 -InstallDir '~/.dotnet' -Version '2.1.2' -ProxyAddress $env:HTTP_PROXY -ProxyUseDefaultCredentials;
  ```

- <span data-ttu-id="a318f-198">Uzyskaj przykłady jednoliniowego skryptu i instaluj jeden-liner.NET Core:</span><span class="sxs-lookup"><span data-stu-id="a318f-198">Obtain script and install .NET Core CLI one-liner examples:</span></span>

  <span data-ttu-id="a318f-199">W systemie Windows:</span><span class="sxs-lookup"><span data-stu-id="a318f-199">Windows:</span></span>

  ```powershell
  # Run a separate PowerShell process because the script calls exit, so it will end the current PowerShell session.
  &powershell -NoProfile -ExecutionPolicy unrestricted -Command "[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; &([scriptblock]::Create((Invoke-WebRequest -UseBasicParsing 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"
  ```

  <span data-ttu-id="a318f-200">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="a318f-200">macOS/Linux:</span></span>

  ```bash
  curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>
  ```

## <a name="see-also"></a><span data-ttu-id="a318f-201">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a318f-201">See also</span></span>

- [<span data-ttu-id="a318f-202">Wersje programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="a318f-202">.NET Core releases</span></span>](https://github.com/dotnet/core/releases)
- [<span data-ttu-id="a318f-203">Archiwum pobierania programu .NET Core Runtime i SDK</span><span class="sxs-lookup"><span data-stu-id="a318f-203">.NET Core Runtime and SDK download archive</span></span>](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)

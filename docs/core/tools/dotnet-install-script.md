---
title: dotnet-install scripts
description: Dowiedz się więcej o skryptach dotnet-install, aby zainstalować pakiet .NET Core SDK i udostępnione środowisko uruchomieniowe.
ms.date: 01/23/2020
ms.openlocfilehash: 591413a17db577560bd0324995066c8ea7a35895
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463676"
---
# <a name="dotnet-install-scripts-reference"></a><span data-ttu-id="470b0-103">odwołanie do skryptów dotnet-install</span><span class="sxs-lookup"><span data-stu-id="470b0-103">dotnet-install scripts reference</span></span>

## <a name="name"></a><span data-ttu-id="470b0-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="470b0-104">Name</span></span>

<span data-ttu-id="470b0-105">`dotnet-install.ps1` | `dotnet-install.sh`- Skrypt używany do zainstalowania .NET Core SDK i udostępnionego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="470b0-105">`dotnet-install.ps1` | `dotnet-install.sh` - Script used to install the .NET Core SDK and the shared runtime.</span></span>

## <a name="synopsis"></a><span data-ttu-id="470b0-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="470b0-106">Synopsis</span></span>

<span data-ttu-id="470b0-107">W systemie Windows:</span><span class="sxs-lookup"><span data-stu-id="470b0-107">Windows:</span></span>

```powershell
dotnet-install.ps1 [-Architecture <ARCHITECTURE>] [-AzureFeed]
    [-Channel <CHANNEL>] [-DryRun] [-FeedCredential]
    [-InstallDir <DIRECTORY>] [-JSonFile <JSONFILE>]
    [-NoCdn] [-NoPath] [-ProxyAddress]
    [-ProxyUseDefaultCredentials] [-Runtime <RUNTIME>]
    [-SkipNonVersionedFiles] [-UncachedFeed] [-Verbose]
    [-Version <VERSION>]

dotnet-install.ps1 -Help
```

<span data-ttu-id="470b0-108">Linux/macOs:</span><span class="sxs-lookup"><span data-stu-id="470b0-108">Linux/macOs:</span></span>

```bash
dotnet-install.sh  [--architecture <ARCHITECTURE>] [--azure-feed]
    [--channel <CHANNEL>] [--dry-run] [--feed-credential]
    [--install-dir <DIRECTORY>] [--jsonfile <JSONFILE>]
    [--no-cdn] [--no-path] [--runtime <RUNTIME>] [--runtime-id <RID>]
    [--skip-non-versioned-files] [--uncached-feed] [--verbose]
    [--version <VERSION>]

dotnet-install.sh --help
```

## <a name="description"></a><span data-ttu-id="470b0-109">Opis</span><span class="sxs-lookup"><span data-stu-id="470b0-109">Description</span></span>

<span data-ttu-id="470b0-110">Skrypty `dotnet-install` są używane do wykonywania instalacji niedministratorów .NET Core SDK, który zawiera .NET Core CLI i udostępnionego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="470b0-110">The `dotnet-install` scripts are used to perform a non-admin installation of the .NET Core SDK, which includes the .NET Core CLI and the shared runtime.</span></span>

<span data-ttu-id="470b0-111">Zaleca się użycie stabilnej wersji skryptów:</span><span class="sxs-lookup"><span data-stu-id="470b0-111">We recommend that you use the stable version of the scripts:</span></span>

- <span data-ttu-id="470b0-112">Bash (Linux/macOS):<https://dot.net/v1/dotnet-install.sh></span><span class="sxs-lookup"><span data-stu-id="470b0-112">Bash (Linux/macOS): <https://dot.net/v1/dotnet-install.sh></span></span>
- <span data-ttu-id="470b0-113">Program PowerShell (Windows):<https://dot.net/v1/dotnet-install.ps1></span><span class="sxs-lookup"><span data-stu-id="470b0-113">PowerShell (Windows): <https://dot.net/v1/dotnet-install.ps1></span></span>

<span data-ttu-id="470b0-114">Główną zaletą tych skryptów jest w scenariuszach automatyzacji i instalacji innych niż administrator.</span><span class="sxs-lookup"><span data-stu-id="470b0-114">The main usefulness of these scripts is in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="470b0-115">Istnieją dwa skrypty: jeden to skrypt programu PowerShell, który działa w systemie Windows, a drugi to skrypt bash, który działa na Linuksie/macOS.</span><span class="sxs-lookup"><span data-stu-id="470b0-115">There are two scripts: one is a PowerShell script that works on Windows, and the other is a bash script that works on Linux/macOS.</span></span> <span data-ttu-id="470b0-116">Oba skrypty mają takie samo zachowanie.</span><span class="sxs-lookup"><span data-stu-id="470b0-116">Both scripts have the same behavior.</span></span> <span data-ttu-id="470b0-117">Skrypt bash odczytuje również przełączniki programu PowerShell, dzięki czemu można używać przełączników programu PowerShell ze skryptem w systemach Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="470b0-117">The bash script also reads PowerShell switches, so you can use PowerShell switches with the script on Linux/macOS systems.</span></span>

<span data-ttu-id="470b0-118">Skrypty instalacyjne pobierają plik ZIP/tarball z kompilacji interfejsu wiersza polecenia i przystępują `-InstallDir|--install-dir`do instalacji w domyślnej lokalizacji lub w lokalizacji określonej przez program .</span><span class="sxs-lookup"><span data-stu-id="470b0-118">The installation scripts download the ZIP/tarball file from the CLI build drops and proceed to install it in either the default location or in a location specified by `-InstallDir|--install-dir`.</span></span> <span data-ttu-id="470b0-119">Domyślnie skrypty instalacyjne pobierają zestaw SDK i instalują go.</span><span class="sxs-lookup"><span data-stu-id="470b0-119">By default, the installation scripts download the SDK and install it.</span></span> <span data-ttu-id="470b0-120">Jeśli chcesz uzyskać tylko udostępnionego środowiska `-Runtime|--runtime` uruchomieniowego, określ argument.</span><span class="sxs-lookup"><span data-stu-id="470b0-120">If you wish to only obtain the shared runtime, specify the `-Runtime|--runtime` argument.</span></span>

<span data-ttu-id="470b0-121">Domyślnie skrypt dodaje lokalizację instalacji do $PATH bieżącej sesji.</span><span class="sxs-lookup"><span data-stu-id="470b0-121">By default, the script adds the install location to the $PATH for the current session.</span></span> <span data-ttu-id="470b0-122">Zastądnie tego domyślnego `-NoPath|--no-path` zachowania, określając argument.</span><span class="sxs-lookup"><span data-stu-id="470b0-122">Override this default behavior by specifying the `-NoPath|--no-path` argument.</span></span>

<span data-ttu-id="470b0-123">Przed uruchomieniem skryptu należy zainstalować wymagane [zależności](../install/dependencies.md).</span><span class="sxs-lookup"><span data-stu-id="470b0-123">Before running the script, install the required [dependencies](../install/dependencies.md).</span></span>

<span data-ttu-id="470b0-124">Można zainstalować określoną wersję `-Version|--version` przy użyciu argumentu.</span><span class="sxs-lookup"><span data-stu-id="470b0-124">You can install a specific version using the `-Version|--version` argument.</span></span> <span data-ttu-id="470b0-125">Wersja musi być określona jako wersja trzyczęściowa (na `2.1.0`przykład).</span><span class="sxs-lookup"><span data-stu-id="470b0-125">The version must be specified as a three-part version (for example, `2.1.0`).</span></span> <span data-ttu-id="470b0-126">Jeśli nie podano, używa `latest` wersji.</span><span class="sxs-lookup"><span data-stu-id="470b0-126">If not provided, it uses the `latest` version.</span></span>

## <a name="options"></a><span data-ttu-id="470b0-127">Opcje</span><span class="sxs-lookup"><span data-stu-id="470b0-127">Options</span></span>

- **`-Architecture|--architecture <ARCHITECTURE>`**

  <span data-ttu-id="470b0-128">Architektura plików binarnych .NET Core do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="470b0-128">Architecture of the .NET Core binaries to install.</span></span> <span data-ttu-id="470b0-129">Możliwe wartości `<auto>` `amd64`to `x64` `x86`, `arm64`, `arm`, , i .</span><span class="sxs-lookup"><span data-stu-id="470b0-129">Possible values are `<auto>`, `amd64`, `x64`, `x86`, `arm64`, and `arm`.</span></span> <span data-ttu-id="470b0-130">Wartością domyślną jest `<auto>`, która reprezentuje aktualnie działającą architekturę systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="470b0-130">The default value is `<auto>`, which represents the currently running OS architecture.</span></span>

- **`-AzureFeed|--azure-feed`**

  <span data-ttu-id="470b0-131">Określa adres URL kanału informacyjnego platformy Azure do instalatora.</span><span class="sxs-lookup"><span data-stu-id="470b0-131">Specifies the URL for the Azure feed to the installer.</span></span> <span data-ttu-id="470b0-132">Zaleca się, aby nie zmieniać tej wartości.</span><span class="sxs-lookup"><span data-stu-id="470b0-132">We recommended that you don't change this value.</span></span> <span data-ttu-id="470b0-133">Wartością domyślną jest `https://dotnetcli.azureedge.net/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="470b0-133">The default value is `https://dotnetcli.azureedge.net/dotnet`.</span></span>

- **`-Channel|--channel <CHANNEL>`**

  <span data-ttu-id="470b0-134">Określa kanał źródłowy instalacji.</span><span class="sxs-lookup"><span data-stu-id="470b0-134">Specifies the source channel for the installation.</span></span> <span data-ttu-id="470b0-135">Możliwe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="470b0-135">The possible values are:</span></span>

  - <span data-ttu-id="470b0-136">`Current`- Większość bieżącej wersji.</span><span class="sxs-lookup"><span data-stu-id="470b0-136">`Current` - Most current release.</span></span>
  - <span data-ttu-id="470b0-137">`LTS`- Kanał wsparcia długoterminowego (najbardziej aktualna wersja obsługiwana).</span><span class="sxs-lookup"><span data-stu-id="470b0-137">`LTS` - Long-Term Support channel (most current supported release).</span></span>
  - <span data-ttu-id="470b0-138">Wersja dwuczęściowa w formacie X.Y reprezentująca określoną wersję (na przykład `2.1` lub `3.0`).</span><span class="sxs-lookup"><span data-stu-id="470b0-138">Two-part version in X.Y format representing a specific release (for example, `2.1` or `3.0`).</span></span>
  - <span data-ttu-id="470b0-139">Nazwa oddziału: na `release/3.1.1xx` `master` przykład lub (dla wersji nocnych).</span><span class="sxs-lookup"><span data-stu-id="470b0-139">Branch name: for example, `release/3.1.1xx` or `master` (for nightly releases).</span></span> <span data-ttu-id="470b0-140">Użyj tej opcji, aby zainstalować wersję z kanału podglądu.</span><span class="sxs-lookup"><span data-stu-id="470b0-140">Use this option to install a version from a preview channel.</span></span> <span data-ttu-id="470b0-141">Użyj nazwy kanału wymienionej w [obszarze Instalatory i pliki binarne](https://github.com/dotnet/core-sdk#installers-and-binaries).</span><span class="sxs-lookup"><span data-stu-id="470b0-141">Use the name of the channel as listed in [Installers and Binaries](https://github.com/dotnet/core-sdk#installers-and-binaries).</span></span>

  <span data-ttu-id="470b0-142">Wartością domyślną jest `LTS`.</span><span class="sxs-lookup"><span data-stu-id="470b0-142">The default value is `LTS`.</span></span> <span data-ttu-id="470b0-143">Aby uzyskać więcej informacji na temat kanałów pomocy technicznej platformy .NET, zobacz stronę [Zasad pomocy technicznej platformy .NET.](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)</span><span class="sxs-lookup"><span data-stu-id="470b0-143">For more information on .NET support channels, see the [.NET Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) page.</span></span>

- **`-DryRun|--dry-run`**

  <span data-ttu-id="470b0-144">Jeśli jest ustawiona, skrypt nie wykona instalacji.</span><span class="sxs-lookup"><span data-stu-id="470b0-144">If set, the script won't perform the installation.</span></span> <span data-ttu-id="470b0-145">Zamiast tego wyświetla wiersz polecenia, którego należy użyć do konsekwentnego instalowania aktualnie żądanej wersji interfejsu wiersza polecenia .NET Core.</span><span class="sxs-lookup"><span data-stu-id="470b0-145">Instead, it displays what command line to use to consistently install the currently requested version of the .NET Core CLI.</span></span> <span data-ttu-id="470b0-146">Na przykład jeśli określisz wersję `latest`, wyświetla łącze z określoną wersją, dzięki czemu to polecenie może być używane deterministycznie w skrypcie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="470b0-146">For example, if you specify version `latest`, it displays a link with the specific version so that this command can be used deterministically in a build script.</span></span> <span data-ttu-id="470b0-147">Wyświetla również lokalizację binarną, jeśli wolisz zainstalować lub pobrać go samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="470b0-147">It also displays the binary's location if you prefer to install or download it yourself.</span></span>

- **`-FeedCredential|--feed-credential`**

  <span data-ttu-id="470b0-148">Używany jako ciąg zapytania do dołączania do źródła danych platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="470b0-148">Used as a query string to append to the Azure feed.</span></span> <span data-ttu-id="470b0-149">Umożliwia zmianę adresu URL do korzystania z kont magazynu obiektów blob niepublicznych.</span><span class="sxs-lookup"><span data-stu-id="470b0-149">It allows changing the URL to use non-public blob storage accounts.</span></span>

- **`-Help|--help`**

  <span data-ttu-id="470b0-150">Drukuje pomoc dla skryptu.</span><span class="sxs-lookup"><span data-stu-id="470b0-150">Prints out help for the script.</span></span>

- **`-InstallDir|--install-dir <DIRECTORY>`**

  <span data-ttu-id="470b0-151">Określa ścieżkę instalacji.</span><span class="sxs-lookup"><span data-stu-id="470b0-151">Specifies the installation path.</span></span> <span data-ttu-id="470b0-152">Katalog jest tworzony, jeśli nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="470b0-152">The directory is created if it doesn't exist.</span></span> <span data-ttu-id="470b0-153">Wartością domyślną jest *%LocalAppData%\Microsoft\dotnet*.</span><span class="sxs-lookup"><span data-stu-id="470b0-153">The default value is *%LocalAppData%\Microsoft\dotnet*.</span></span> <span data-ttu-id="470b0-154">Pliki binarne są umieszczane bezpośrednio w tym katalogu.</span><span class="sxs-lookup"><span data-stu-id="470b0-154">Binaries are placed directly in this directory.</span></span>

- **`-JSonFile|--jsonfile <JSONFILE>`**

  <span data-ttu-id="470b0-155">Określa ścieżkę do pliku [global.json,](global-json.md) który będzie używany do określania wersji SDK.</span><span class="sxs-lookup"><span data-stu-id="470b0-155">Specifies a path to a [global.json](global-json.md) file that will be used to determine the SDK version.</span></span> <span data-ttu-id="470b0-156">Plik *global.json* musi mieć `sdk:version`wartość dla pliku .</span><span class="sxs-lookup"><span data-stu-id="470b0-156">The *global.json* file must have a value for `sdk:version`.</span></span>

- **`-NoCdn|--no-cdn`**

  <span data-ttu-id="470b0-157">Wyłącza pobieranie z [usługi Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) i używa kanału informacyjnego bez bufora bezpośrednio.</span><span class="sxs-lookup"><span data-stu-id="470b0-157">Disables downloading from the [Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) and uses the uncached feed directly.</span></span>

- **`-NoPath|--no-path`**

  <span data-ttu-id="470b0-158">Jeśli jest ustawiona, folder instalacyjny nie jest eksportowany do ścieżki dla bieżącej sesji.</span><span class="sxs-lookup"><span data-stu-id="470b0-158">If set, the installation folder isn't exported to the path for the current session.</span></span> <span data-ttu-id="470b0-159">Domyślnie skrypt modyfikuje PATH, co sprawia, że .NET Core CLI dostępne natychmiast po zainstalowaniu.</span><span class="sxs-lookup"><span data-stu-id="470b0-159">By default, the script modifies the PATH, which makes the .NET Core CLI available immediately after install.</span></span>

- **`-ProxyAddress`**

  <span data-ttu-id="470b0-160">Jeśli jest ustawiona, instalator używa serwera proxy podczas składania żądań sieci web.</span><span class="sxs-lookup"><span data-stu-id="470b0-160">If set, the installer uses the proxy when making web requests.</span></span> <span data-ttu-id="470b0-161">(Dotyczy tylko systemu Windows).</span><span class="sxs-lookup"><span data-stu-id="470b0-161">(Only valid for Windows.)</span></span>

- **`ProxyUseDefaultCredentials`**

  <span data-ttu-id="470b0-162">Jeśli jest ustawiona, instalator używa poświadczeń bieżącego użytkownika podczas korzystania z adresu serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="470b0-162">If set, the installer uses the credentials of the current user when using proxy address.</span></span> <span data-ttu-id="470b0-163">(Dotyczy tylko systemu Windows).</span><span class="sxs-lookup"><span data-stu-id="470b0-163">(Only valid for Windows.)</span></span>

- **`-Runtime|--runtime <RUNTIME>`**

  <span data-ttu-id="470b0-164">Instaluje tylko udostępnione środowisko uruchomieniowe, a nie cały pakiet SDK.</span><span class="sxs-lookup"><span data-stu-id="470b0-164">Installs just the shared runtime, not the entire SDK.</span></span> <span data-ttu-id="470b0-165">Możliwe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="470b0-165">The possible values are:</span></span>

  - <span data-ttu-id="470b0-166">`dotnet`- `Microsoft.NETCore.App` współdzielony czas pracy.</span><span class="sxs-lookup"><span data-stu-id="470b0-166">`dotnet` - the `Microsoft.NETCore.App` shared runtime.</span></span>
  - <span data-ttu-id="470b0-167">`aspnetcore`- `Microsoft.AspNetCore.App` współdzielony czas pracy.</span><span class="sxs-lookup"><span data-stu-id="470b0-167">`aspnetcore` - the `Microsoft.AspNetCore.App` shared runtime.</span></span>
  - <span data-ttu-id="470b0-168">`windowsdesktop`- `Microsoft.WindowsDesktop.App` współdzielony czas pracy.</span><span class="sxs-lookup"><span data-stu-id="470b0-168">`windowsdesktop` - the `Microsoft.WindowsDesktop.App` shared runtime.</span></span>

- **`--runtime-id <RID>`**

  <span data-ttu-id="470b0-169">Określa [identyfikator środowiska wykonawczego,](../rid-catalog.md) dla którego narzędzia są instalowane.</span><span class="sxs-lookup"><span data-stu-id="470b0-169">Specifies the [runtime identifier](../rid-catalog.md) for which the tools are being installed.</span></span> <span data-ttu-id="470b0-170">Użyj `linux-x64` do przenośnego Linuksa.</span><span class="sxs-lookup"><span data-stu-id="470b0-170">Use `linux-x64` for portable Linux.</span></span> <span data-ttu-id="470b0-171">(Dotyczy tylko systemów Linux/macOS).</span><span class="sxs-lookup"><span data-stu-id="470b0-171">(Only valid for Linux/macOS.)</span></span>

- **`-SharedRuntime|--shared-runtime`**

  > [!NOTE]
  > <span data-ttu-id="470b0-172">Ten parametr jest przestarzały i może zostać usunięty w przyszłej wersji skryptu.</span><span class="sxs-lookup"><span data-stu-id="470b0-172">This parameter is obsolete and may be removed in a future version of the script.</span></span> <span data-ttu-id="470b0-173">Zalecaną alternatywą `-Runtime|--runtime` jest opcja.</span><span class="sxs-lookup"><span data-stu-id="470b0-173">The recommended alternative is the `-Runtime|--runtime` option.</span></span>

  <span data-ttu-id="470b0-174">Instaluje tylko udostępnione bity środowiska uruchomieniowego, a nie cały pakiet SDK.</span><span class="sxs-lookup"><span data-stu-id="470b0-174">Installs just the shared runtime bits, not the entire SDK.</span></span> <span data-ttu-id="470b0-175">Ta opcja jest równoważna z określeniem `-Runtime|--runtime dotnet`.</span><span class="sxs-lookup"><span data-stu-id="470b0-175">This option is equivalent to specifying `-Runtime|--runtime dotnet`.</span></span>

- **`-SkipNonVersionedFiles|--skip-non-versioned-files`**

  <span data-ttu-id="470b0-176">Pomija instalowanie plików nieobrażonych, takich jak *dotnet.exe*, jeśli już istnieją.</span><span class="sxs-lookup"><span data-stu-id="470b0-176">Skips installing non-versioned files, such as *dotnet.exe*, if they already exist.</span></span>

- **`-UncachedFeed|--uncached-feed`**

  <span data-ttu-id="470b0-177">Umożliwia zmianę adresu URL niebukowanego kanału informacyjnego używanego przez tego instalatora.</span><span class="sxs-lookup"><span data-stu-id="470b0-177">Allows changing the URL for the uncached feed used by this installer.</span></span> <span data-ttu-id="470b0-178">Zaleca się, aby nie zmieniać tej wartości.</span><span class="sxs-lookup"><span data-stu-id="470b0-178">We recommended that you don't change this value.</span></span>

- **`-Verbose|--verbose`**

  <span data-ttu-id="470b0-179">Wyświetla informacje diagnostyczne.</span><span class="sxs-lookup"><span data-stu-id="470b0-179">Displays diagnostics information.</span></span>

- **`-Version|--version <VERSION>`**

  <span data-ttu-id="470b0-180">Reprezentuje określoną wersję kompilacji.</span><span class="sxs-lookup"><span data-stu-id="470b0-180">Represents a specific build version.</span></span> <span data-ttu-id="470b0-181">Możliwe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="470b0-181">The possible values are:</span></span>

  - <span data-ttu-id="470b0-182">`latest`- Najnowsza kompilacja na `-Channel` kanale (używana z opcją).</span><span class="sxs-lookup"><span data-stu-id="470b0-182">`latest` - Latest build on the channel (used with the `-Channel` option).</span></span>
  - <span data-ttu-id="470b0-183">`coherent`- Najnowsze spójne budować na kanale; używa najnowszej kombinacji pakietów stabilnych `-Channel` (używanej z opcjami nazwy oddziału).</span><span class="sxs-lookup"><span data-stu-id="470b0-183">`coherent` - Latest coherent build on the channel; uses the latest stable package combination (used with Branch name `-Channel` options).</span></span>
  - <span data-ttu-id="470b0-184">Wersja trzyczęściowa w formacie X.Y.Z reprezentująca określoną wersję kompilacji; zastępuje `-Channel` tę opcję.</span><span class="sxs-lookup"><span data-stu-id="470b0-184">Three-part version in X.Y.Z format representing a specific build version; supersedes the `-Channel` option.</span></span> <span data-ttu-id="470b0-185">Na przykład: `2.0.0-preview2-006120`.</span><span class="sxs-lookup"><span data-stu-id="470b0-185">For example: `2.0.0-preview2-006120`.</span></span>

  <span data-ttu-id="470b0-186">Jeśli nie `-Version` zostanie określony, wartość domyślna to `latest`.</span><span class="sxs-lookup"><span data-stu-id="470b0-186">If not specified, `-Version` defaults to `latest`.</span></span>

## <a name="examples"></a><span data-ttu-id="470b0-187">Przykłady</span><span class="sxs-lookup"><span data-stu-id="470b0-187">Examples</span></span>

- <span data-ttu-id="470b0-188">Zainstaluj najnowszą długoterminową wersję obsługiwanej (LTS) w lokalizacji domyślnej:</span><span class="sxs-lookup"><span data-stu-id="470b0-188">Install the latest long-term supported (LTS) version to the default location:</span></span>

  <span data-ttu-id="470b0-189">W systemie Windows:</span><span class="sxs-lookup"><span data-stu-id="470b0-189">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel LTS
  ```

  <span data-ttu-id="470b0-190">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="470b0-190">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel LTS
  ```

- <span data-ttu-id="470b0-191">Zainstaluj najnowszą wersję z kanału 3.1 do określonej lokalizacji:</span><span class="sxs-lookup"><span data-stu-id="470b0-191">Install the latest version from 3.1 channel to the specified location:</span></span>

  <span data-ttu-id="470b0-192">W systemie Windows:</span><span class="sxs-lookup"><span data-stu-id="470b0-192">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel 3.1 -InstallDir C:\cli
  ```

  <span data-ttu-id="470b0-193">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="470b0-193">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel 3.1 --install-dir ~/cli
  ```

- <span data-ttu-id="470b0-194">Zainstaluj wersję udostępnionego środowiska wykonawczego 3.0.0:</span><span class="sxs-lookup"><span data-stu-id="470b0-194">Install the 3.0.0 version of the shared runtime:</span></span>

  <span data-ttu-id="470b0-195">W systemie Windows:</span><span class="sxs-lookup"><span data-stu-id="470b0-195">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Runtime dotnet -Version 3.0.0
  ```

  <span data-ttu-id="470b0-196">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="470b0-196">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --runtime dotnet --version 3.0.0
  ```

- <span data-ttu-id="470b0-197">Uzyskaj skrypt i zainstaluj wersję 2.1.2 za firmowym serwerem proxy (tylko windows):</span><span class="sxs-lookup"><span data-stu-id="470b0-197">Obtain script and install the 2.1.2 version behind a corporate proxy (Windows only):</span></span>

  ```powershell
  Invoke-WebRequest 'https://dot.net/v1/dotnet-install.ps1' -Proxy $env:HTTP_PROXY -ProxyUseDefaultCredentials -OutFile 'dotnet-install.ps1';
  ./dotnet-install.ps1 -InstallDir '~/.dotnet' -Version '2.1.2' -ProxyAddress $env:HTTP_PROXY -ProxyUseDefaultCredentials;
  ```

- <span data-ttu-id="470b0-198">Uzyskaj skrypt i zainstaluj przykłady one-liner net core cli:</span><span class="sxs-lookup"><span data-stu-id="470b0-198">Obtain script and install .NET Core CLI one-liner examples:</span></span>

  <span data-ttu-id="470b0-199">W systemie Windows:</span><span class="sxs-lookup"><span data-stu-id="470b0-199">Windows:</span></span>

  ```powershell
  # Run a separate PowerShell process because the script calls exit, so it will end the current PowerShell session.
  &powershell -NoProfile -ExecutionPolicy unrestricted -Command "[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; &([scriptblock]::Create((Invoke-WebRequest -UseBasicParsing 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"
  ```

  <span data-ttu-id="470b0-200">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="470b0-200">macOS/Linux:</span></span>

  ```bash
  curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>
  ```

## <a name="see-also"></a><span data-ttu-id="470b0-201">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="470b0-201">See also</span></span>

- [<span data-ttu-id="470b0-202">Wersje .NET Core</span><span class="sxs-lookup"><span data-stu-id="470b0-202">.NET Core releases</span></span>](https://github.com/dotnet/core/releases)
- [<span data-ttu-id="470b0-203">Archiwum pobierania .NET Core Runtime i SDK</span><span class="sxs-lookup"><span data-stu-id="470b0-203">.NET Core Runtime and SDK download archive</span></span>](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)

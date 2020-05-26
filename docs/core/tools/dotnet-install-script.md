---
title: dotnet-install scripts
description: Więcej informacji na temat skryptów programu dotnet-Install w celu zainstalowania zestaw .NET Core SDK i udostępnionego środowiska uruchomieniowego.
ms.date: 04/30/2020
ms.openlocfilehash: 9f5cef9cfcca1d8b344021efe803c063a7393f8e
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83802720"
---
# <a name="dotnet-install-scripts-reference"></a><span data-ttu-id="658c7-103">dotnet — informacje o skryptach instalacji</span><span class="sxs-lookup"><span data-stu-id="658c7-103">dotnet-install scripts reference</span></span>

## <a name="name"></a><span data-ttu-id="658c7-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="658c7-104">Name</span></span>

<span data-ttu-id="658c7-105">`dotnet-install.ps1` | `dotnet-install.sh`-Skrypt służący do instalowania zestaw .NET Core SDK i udostępnionego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="658c7-105">`dotnet-install.ps1` | `dotnet-install.sh` - Script used to install the .NET Core SDK and the shared runtime.</span></span>

## <a name="synopsis"></a><span data-ttu-id="658c7-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="658c7-106">Synopsis</span></span>

<span data-ttu-id="658c7-107">W systemie Windows:</span><span class="sxs-lookup"><span data-stu-id="658c7-107">Windows:</span></span>

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

<span data-ttu-id="658c7-108">Linux/macOS:</span><span class="sxs-lookup"><span data-stu-id="658c7-108">Linux/macOS:</span></span>

```bash
dotnet-install.sh  [--architecture <ARCHITECTURE>] [--azure-feed]
    [--channel <CHANNEL>] [--dry-run] [--feed-credential]
    [--install-dir <DIRECTORY>] [--jsonfile <JSONFILE>]
    [--no-cdn] [--no-path] [--runtime <RUNTIME>] [--runtime-id <RID>]
    [--skip-non-versioned-files] [--uncached-feed] [--verbose]
    [--version <VERSION>]

dotnet-install.sh --help
```

## <a name="description"></a><span data-ttu-id="658c7-109">Opis</span><span class="sxs-lookup"><span data-stu-id="658c7-109">Description</span></span>

<span data-ttu-id="658c7-110">`dotnet-install`Skrypty są używane do przeprowadzania instalacji nieadministratora zestaw .NET Core SDK, w tym interfejs wiersza polecenia platformy .NET Core i udostępnionego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="658c7-110">The `dotnet-install` scripts are used to perform a non-admin installation of the .NET Core SDK, which includes the .NET Core CLI and the shared runtime.</span></span>

<span data-ttu-id="658c7-111">Zalecamy użycie stabilnej wersji skryptów:</span><span class="sxs-lookup"><span data-stu-id="658c7-111">We recommend that you use the stable version of the scripts:</span></span>

- <span data-ttu-id="658c7-112">Bash (Linux/macOS):<https://dot.net/v1/dotnet-install.sh></span><span class="sxs-lookup"><span data-stu-id="658c7-112">Bash (Linux/macOS): <https://dot.net/v1/dotnet-install.sh></span></span>
- <span data-ttu-id="658c7-113">PowerShell (Windows):<https://dot.net/v1/dotnet-install.ps1></span><span class="sxs-lookup"><span data-stu-id="658c7-113">PowerShell (Windows): <https://dot.net/v1/dotnet-install.ps1></span></span>

<span data-ttu-id="658c7-114">Główna użyteczność tych skryptów jest w scenariuszach automatyzacji i instalacjach nienależących do administratora.</span><span class="sxs-lookup"><span data-stu-id="658c7-114">The main usefulness of these scripts is in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="658c7-115">Istnieją dwa skrypty: jeden to skrypt programu PowerShell, który działa w systemie Windows, a drugi to skrypt bash, który działa w systemie Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="658c7-115">There are two scripts: one is a PowerShell script that works on Windows, and the other is a bash script that works on Linux/macOS.</span></span> <span data-ttu-id="658c7-116">Oba skrypty mają takie samo zachowanie.</span><span class="sxs-lookup"><span data-stu-id="658c7-116">Both scripts have the same behavior.</span></span> <span data-ttu-id="658c7-117">Skrypt bash odczytuje również przełączniki programu PowerShell, dzięki czemu można użyć przełączników programu PowerShell z skryptem w systemach Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="658c7-117">The bash script also reads PowerShell switches, so you can use PowerShell switches with the script on Linux/macOS systems.</span></span>

<span data-ttu-id="658c7-118">Skrypty instalacyjne pobierają plik ZIP/plik tar z kompilacji interfejsu wiersza polecenia, a następnie instalują go w lokalizacji domyślnej lub w lokalizacji określonej przez `-InstallDir|--install-dir` .</span><span class="sxs-lookup"><span data-stu-id="658c7-118">The installation scripts download the ZIP/tarball file from the CLI build drops and proceed to install it in either the default location or in a location specified by `-InstallDir|--install-dir`.</span></span> <span data-ttu-id="658c7-119">Domyślnie skrypty instalacyjne pobierają zestaw SDK i instalują go.</span><span class="sxs-lookup"><span data-stu-id="658c7-119">By default, the installation scripts download the SDK and install it.</span></span> <span data-ttu-id="658c7-120">Jeśli chcesz uzyskać tylko udostępnione środowisko uruchomieniowe, określ `-Runtime|--runtime` argument.</span><span class="sxs-lookup"><span data-stu-id="658c7-120">If you wish to only obtain the shared runtime, specify the `-Runtime|--runtime` argument.</span></span>

<span data-ttu-id="658c7-121">Domyślnie skrypt dodaje lokalizację instalacji do $PATH bieżącej sesji.</span><span class="sxs-lookup"><span data-stu-id="658c7-121">By default, the script adds the install location to the $PATH for the current session.</span></span> <span data-ttu-id="658c7-122">Zastąp to zachowanie domyślne, określając `-NoPath|--no-path` argument.</span><span class="sxs-lookup"><span data-stu-id="658c7-122">Override this default behavior by specifying the `-NoPath|--no-path` argument.</span></span>

<span data-ttu-id="658c7-123">Przed uruchomieniem skryptu Zainstaluj wymagane [zależności](../install/dependencies.md).</span><span class="sxs-lookup"><span data-stu-id="658c7-123">Before running the script, install the required [dependencies](../install/dependencies.md).</span></span>

<span data-ttu-id="658c7-124">Można zainstalować określoną wersję przy użyciu `-Version|--version` argumentu.</span><span class="sxs-lookup"><span data-stu-id="658c7-124">You can install a specific version using the `-Version|--version` argument.</span></span> <span data-ttu-id="658c7-125">Wersja musi być określona jako wersja z trzema częściami (na przykład `2.1.0` ).</span><span class="sxs-lookup"><span data-stu-id="658c7-125">The version must be specified as a three-part version (for example, `2.1.0`).</span></span> <span data-ttu-id="658c7-126">Jeśli nie zostanie podany, zostanie użyta `latest` wersja.</span><span class="sxs-lookup"><span data-stu-id="658c7-126">If not provided, it uses the `latest` version.</span></span>

<span data-ttu-id="658c7-127">Skrypty instalacji nie aktualizują rejestru w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="658c7-127">The install scripts do not update the registry on Windows.</span></span> <span data-ttu-id="658c7-128">Po prostu pobieramy spakowane pliki binarne i skopiują je do folderu.</span><span class="sxs-lookup"><span data-stu-id="658c7-128">They just download the zipped binaries and copy them to a folder.</span></span> <span data-ttu-id="658c7-129">Jeśli chcesz, aby wartości klucza rejestru były aktualizowane, użyj instalatorów platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="658c7-129">If you want registry key values to be updated, use the .NET Core installers.</span></span>

## <a name="options"></a><span data-ttu-id="658c7-130">Opcje</span><span class="sxs-lookup"><span data-stu-id="658c7-130">Options</span></span>

- **`-Architecture|--architecture <ARCHITECTURE>`**

  <span data-ttu-id="658c7-131">Architektura plików binarnych platformy .NET Core do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="658c7-131">Architecture of the .NET Core binaries to install.</span></span> <span data-ttu-id="658c7-132">Możliwe wartości to `<auto>` , `amd64` , `x64` , `x86` , `arm64` i `arm` .</span><span class="sxs-lookup"><span data-stu-id="658c7-132">Possible values are `<auto>`, `amd64`, `x64`, `x86`, `arm64`, and `arm`.</span></span> <span data-ttu-id="658c7-133">Wartość domyślna to `<auto>` , która reprezentuje aktualnie uruchomioną architekturę systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="658c7-133">The default value is `<auto>`, which represents the currently running OS architecture.</span></span>

- **`-AzureFeed|--azure-feed`**

  <span data-ttu-id="658c7-134">Określa adres URL źródła danych platformy Azure do Instalatora.</span><span class="sxs-lookup"><span data-stu-id="658c7-134">Specifies the URL for the Azure feed to the installer.</span></span> <span data-ttu-id="658c7-135">Zaleca się, aby nie zmieniać tej wartości.</span><span class="sxs-lookup"><span data-stu-id="658c7-135">We recommended that you don't change this value.</span></span> <span data-ttu-id="658c7-136">Wartość domyślna to `https://dotnetcli.azureedge.net/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="658c7-136">The default value is `https://dotnetcli.azureedge.net/dotnet`.</span></span>

- **`-Channel|--channel <CHANNEL>`**

  <span data-ttu-id="658c7-137">Określa kanał źródłowy instalacji.</span><span class="sxs-lookup"><span data-stu-id="658c7-137">Specifies the source channel for the installation.</span></span> <span data-ttu-id="658c7-138">Możliwe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="658c7-138">The possible values are:</span></span>

  - <span data-ttu-id="658c7-139">`Current`-Najnowsza wersja.</span><span class="sxs-lookup"><span data-stu-id="658c7-139">`Current` - Most current release.</span></span>
  - <span data-ttu-id="658c7-140">`LTS`-Długoterminowy kanał pomocy technicznej (większość aktualnie obsługiwanych wersji).</span><span class="sxs-lookup"><span data-stu-id="658c7-140">`LTS` - Long-Term Support channel (most current supported release).</span></span>
  - <span data-ttu-id="658c7-141">Dwuczęściowa wersja w formacie X. Y reprezentującym określoną wersję (na przykład `2.1` lub `3.0` ).</span><span class="sxs-lookup"><span data-stu-id="658c7-141">Two-part version in X.Y format representing a specific release (for example, `2.1` or `3.0`).</span></span>
  - <span data-ttu-id="658c7-142">Nazwa gałęzi: na przykład `release/3.1.1xx` lub `master` (dla nocnych wydań).</span><span class="sxs-lookup"><span data-stu-id="658c7-142">Branch name: for example, `release/3.1.1xx` or `master` (for nightly releases).</span></span> <span data-ttu-id="658c7-143">Użyj tej opcji, aby zainstalować wersję z kanału w wersji zapoznawczej.</span><span class="sxs-lookup"><span data-stu-id="658c7-143">Use this option to install a version from a preview channel.</span></span> <span data-ttu-id="658c7-144">Użyj nazwy kanału wymienionej w [instalatorze i plikach binarnych](https://github.com/dotnet/core-sdk#installers-and-binaries).</span><span class="sxs-lookup"><span data-stu-id="658c7-144">Use the name of the channel as listed in [Installers and Binaries](https://github.com/dotnet/core-sdk#installers-and-binaries).</span></span>

  <span data-ttu-id="658c7-145">Wartość domyślna to `LTS`.</span><span class="sxs-lookup"><span data-stu-id="658c7-145">The default value is `LTS`.</span></span> <span data-ttu-id="658c7-146">Aby uzyskać więcej informacji na temat kanałów pomocy technicznej platformy .NET, zobacz stronę [zasady pomocy technicznej platformy .NET](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) .</span><span class="sxs-lookup"><span data-stu-id="658c7-146">For more information on .NET support channels, see the [.NET Support Policy](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) page.</span></span>

- **`-DryRun|--dry-run`**

  <span data-ttu-id="658c7-147">W przypadku ustawienia skrypt nie wykona instalacji.</span><span class="sxs-lookup"><span data-stu-id="658c7-147">If set, the script won't perform the installation.</span></span> <span data-ttu-id="658c7-148">Zamiast tego Wyświetla on wiersz polecenia, który służy do spójnej instalacji aktualnie żądanej wersji interfejs wiersza polecenia platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="658c7-148">Instead, it displays what command line to use to consistently install the currently requested version of the .NET Core CLI.</span></span> <span data-ttu-id="658c7-149">Jeśli na przykład zostanie określona wersja `latest` , zostanie wyświetlony link z określoną wersją, aby można było użyć tego polecenia w sposób jednoznaczny w skrypcie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="658c7-149">For example, if you specify version `latest`, it displays a link with the specific version so that this command can be used deterministically in a build script.</span></span> <span data-ttu-id="658c7-150">Wyświetla również lokalizację pliku binarnego, jeśli wolisz zainstalować lub pobrać ją samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="658c7-150">It also displays the binary's location if you prefer to install or download it yourself.</span></span>

- **`-FeedCredential|--feed-credential`**

  <span data-ttu-id="658c7-151">Służy jako ciąg zapytania do dołączenia do kanału informacyjnego platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="658c7-151">Used as a query string to append to the Azure feed.</span></span> <span data-ttu-id="658c7-152">Umożliwia on zmianę adresu URL w celu korzystania z niepublicznych kont magazynu obiektów BLOB.</span><span class="sxs-lookup"><span data-stu-id="658c7-152">It allows changing the URL to use non-public blob storage accounts.</span></span>

- **`-Help|--help`**

  <span data-ttu-id="658c7-153">Drukuje pomoc dla skryptu.</span><span class="sxs-lookup"><span data-stu-id="658c7-153">Prints out help for the script.</span></span>

- **`-InstallDir|--install-dir <DIRECTORY>`**

  <span data-ttu-id="658c7-154">Określa ścieżkę instalacji.</span><span class="sxs-lookup"><span data-stu-id="658c7-154">Specifies the installation path.</span></span> <span data-ttu-id="658c7-155">Katalog zostanie utworzony, jeśli nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="658c7-155">The directory is created if it doesn't exist.</span></span> <span data-ttu-id="658c7-156">Wartość domyślna to *%LocalAppData%\Microsoft\dotnet* w systemach Windows i */usr/share/dotnet* w systemie Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="658c7-156">The default value is *%LocalAppData%\Microsoft\dotnet* on Windows and */usr/share/dotnet* on Linux/macOS.</span></span> <span data-ttu-id="658c7-157">Pliki binarne są umieszczane bezpośrednio w tym katalogu.</span><span class="sxs-lookup"><span data-stu-id="658c7-157">Binaries are placed directly in this directory.</span></span>

- **`-JSonFile|--jsonfile <JSONFILE>`**

  <span data-ttu-id="658c7-158">Określa ścieżkę do pliku [Global. JSON](global-json.md) , który zostanie użyty do określenia wersji zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="658c7-158">Specifies a path to a [global.json](global-json.md) file that will be used to determine the SDK version.</span></span> <span data-ttu-id="658c7-159">Plik *Global. JSON* musi mieć wartość `sdk:version` .</span><span class="sxs-lookup"><span data-stu-id="658c7-159">The *global.json* file must have a value for `sdk:version`.</span></span>

- **`-NoCdn|--no-cdn`**

  <span data-ttu-id="658c7-160">Wyłącza pobieranie z [usługi Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) i bezpośrednio używa niebuforowanego źródła danych.</span><span class="sxs-lookup"><span data-stu-id="658c7-160">Disables downloading from the [Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) and uses the uncached feed directly.</span></span>

- **`-NoPath|--no-path`**

  <span data-ttu-id="658c7-161">W przypadku ustawienia folder instalacyjny nie zostanie wyeksportowany do ścieżki bieżącej sesji.</span><span class="sxs-lookup"><span data-stu-id="658c7-161">If set, the installation folder isn't exported to the path for the current session.</span></span> <span data-ttu-id="658c7-162">Domyślnie skrypt modyfikuje ścieżkę, co sprawia, że interfejs wiersza polecenia platformy .NET Core dostępne natychmiast po instalacji.</span><span class="sxs-lookup"><span data-stu-id="658c7-162">By default, the script modifies the PATH, which makes the .NET Core CLI available immediately after install.</span></span>

- **`-ProxyAddress`**

  <span data-ttu-id="658c7-163">W przypadku ustawienia Instalator używa serwera proxy podczas wykonywania żądań sieci Web.</span><span class="sxs-lookup"><span data-stu-id="658c7-163">If set, the installer uses the proxy when making web requests.</span></span> <span data-ttu-id="658c7-164">(Prawidłowe dla systemu Windows).</span><span class="sxs-lookup"><span data-stu-id="658c7-164">(Only valid for Windows.)</span></span>

- **`ProxyUseDefaultCredentials`**

  <span data-ttu-id="658c7-165">Jeśli ta wartość jest ustawiona, Instalator użyje poświadczeń bieżącego użytkownika przy użyciu adresu serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="658c7-165">If set, the installer uses the credentials of the current user when using proxy address.</span></span> <span data-ttu-id="658c7-166">(Prawidłowe dla systemu Windows).</span><span class="sxs-lookup"><span data-stu-id="658c7-166">(Only valid for Windows.)</span></span>

- **`-Runtime|--runtime <RUNTIME>`**

  <span data-ttu-id="658c7-167">Instaluje tylko udostępnione środowisko uruchomieniowe, a nie cały zestaw SDK.</span><span class="sxs-lookup"><span data-stu-id="658c7-167">Installs just the shared runtime, not the entire SDK.</span></span> <span data-ttu-id="658c7-168">Możliwe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="658c7-168">The possible values are:</span></span>

  - <span data-ttu-id="658c7-169">`dotnet`— `Microsoft.NETCore.App` udostępnione środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="658c7-169">`dotnet` - the `Microsoft.NETCore.App` shared runtime.</span></span>
  - <span data-ttu-id="658c7-170">`aspnetcore`— `Microsoft.AspNetCore.App` udostępnione środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="658c7-170">`aspnetcore` - the `Microsoft.AspNetCore.App` shared runtime.</span></span>
  - <span data-ttu-id="658c7-171">`windowsdesktop`— `Microsoft.WindowsDesktop.App` udostępnione środowisko uruchomieniowe.</span><span class="sxs-lookup"><span data-stu-id="658c7-171">`windowsdesktop` - the `Microsoft.WindowsDesktop.App` shared runtime.</span></span>

- **`--runtime-id <RID>`**

  <span data-ttu-id="658c7-172">Określa [Identyfikator środowiska uruchomieniowego](../rid-catalog.md) , dla którego instalowane są narzędzia.</span><span class="sxs-lookup"><span data-stu-id="658c7-172">Specifies the [runtime identifier](../rid-catalog.md) for which the tools are being installed.</span></span> <span data-ttu-id="658c7-173">Używany `linux-x64` dla przenośnego systemu Linux.</span><span class="sxs-lookup"><span data-stu-id="658c7-173">Use `linux-x64` for portable Linux.</span></span> <span data-ttu-id="658c7-174">(Prawidłowy tylko dla systemu Linux/macOS).</span><span class="sxs-lookup"><span data-stu-id="658c7-174">(Only valid for Linux/macOS.)</span></span>

- **`-SharedRuntime|--shared-runtime`**

  > [!NOTE]
  > <span data-ttu-id="658c7-175">Ten parametr jest przestarzały i może zostać usunięty w przyszłej wersji skryptu.</span><span class="sxs-lookup"><span data-stu-id="658c7-175">This parameter is obsolete and may be removed in a future version of the script.</span></span> <span data-ttu-id="658c7-176">Zalecaną alternatywą jest `-Runtime|--runtime` opcja.</span><span class="sxs-lookup"><span data-stu-id="658c7-176">The recommended alternative is the `-Runtime|--runtime` option.</span></span>

  <span data-ttu-id="658c7-177">Instaluje tylko udostępnione bity środowiska uruchomieniowego, a nie cały zestaw SDK.</span><span class="sxs-lookup"><span data-stu-id="658c7-177">Installs just the shared runtime bits, not the entire SDK.</span></span> <span data-ttu-id="658c7-178">Ta opcja jest równoważna z określeniem `-Runtime|--runtime dotnet` .</span><span class="sxs-lookup"><span data-stu-id="658c7-178">This option is equivalent to specifying `-Runtime|--runtime dotnet`.</span></span>

- **`-SkipNonVersionedFiles|--skip-non-versioned-files`**

  <span data-ttu-id="658c7-179">Pomija Instalowanie plików nienależących do wersji, takich jak *dotnet. exe*, jeśli już istnieją.</span><span class="sxs-lookup"><span data-stu-id="658c7-179">Skips installing non-versioned files, such as *dotnet.exe*, if they already exist.</span></span>

- **`-UncachedFeed|--uncached-feed`**

  <span data-ttu-id="658c7-180">Umożliwia zmianę adresu URL dla niebuforowanego źródła danych używanego przez ten Instalator.</span><span class="sxs-lookup"><span data-stu-id="658c7-180">Allows changing the URL for the uncached feed used by this installer.</span></span> <span data-ttu-id="658c7-181">Zaleca się, aby nie zmieniać tej wartości.</span><span class="sxs-lookup"><span data-stu-id="658c7-181">We recommended that you don't change this value.</span></span>

- **`-Verbose|--verbose`**

  <span data-ttu-id="658c7-182">Wyświetla informacje diagnostyczne.</span><span class="sxs-lookup"><span data-stu-id="658c7-182">Displays diagnostics information.</span></span>

- **`-Version|--version <VERSION>`**

  <span data-ttu-id="658c7-183">Reprezentuje konkretną wersję kompilacji.</span><span class="sxs-lookup"><span data-stu-id="658c7-183">Represents a specific build version.</span></span> <span data-ttu-id="658c7-184">Możliwe wartości są następujące:</span><span class="sxs-lookup"><span data-stu-id="658c7-184">The possible values are:</span></span>

  - <span data-ttu-id="658c7-185">`latest`-Najnowsza kompilacja w kanale (używana z `-Channel` opcją).</span><span class="sxs-lookup"><span data-stu-id="658c7-185">`latest` - Latest build on the channel (used with the `-Channel` option).</span></span>
  - <span data-ttu-id="658c7-186">`coherent`-Najnowsza spójna kompilacja na kanale; używa najnowszej stabilnej kombinacji pakietów (używanej z `-Channel` opcjami nazw gałęzi).</span><span class="sxs-lookup"><span data-stu-id="658c7-186">`coherent` - Latest coherent build on the channel; uses the latest stable package combination (used with Branch name `-Channel` options).</span></span>
  - <span data-ttu-id="658c7-187">Wersja z trzech części w formacie X. Y. Z, reprezentująca konkretną wersję kompilacji; zastępuje `-Channel` opcję.</span><span class="sxs-lookup"><span data-stu-id="658c7-187">Three-part version in X.Y.Z format representing a specific build version; supersedes the `-Channel` option.</span></span> <span data-ttu-id="658c7-188">Na przykład: `2.0.0-preview2-006120`.</span><span class="sxs-lookup"><span data-stu-id="658c7-188">For example: `2.0.0-preview2-006120`.</span></span>

  <span data-ttu-id="658c7-189">Jeśli nie zostanie określony, `-Version` wartością domyślną jest `latest` .</span><span class="sxs-lookup"><span data-stu-id="658c7-189">If not specified, `-Version` defaults to `latest`.</span></span>

## <a name="examples"></a><span data-ttu-id="658c7-190">Przykłady</span><span class="sxs-lookup"><span data-stu-id="658c7-190">Examples</span></span>

- <span data-ttu-id="658c7-191">Zainstaluj najnowszą wersję długoterminową (LTS) w lokalizacji domyślnej:</span><span class="sxs-lookup"><span data-stu-id="658c7-191">Install the latest long-term supported (LTS) version to the default location:</span></span>

  <span data-ttu-id="658c7-192">W systemie Windows:</span><span class="sxs-lookup"><span data-stu-id="658c7-192">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel LTS
  ```

  <span data-ttu-id="658c7-193">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="658c7-193">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel LTS
  ```

- <span data-ttu-id="658c7-194">Zainstaluj najnowszą wersję z kanału 3,1 do określonej lokalizacji:</span><span class="sxs-lookup"><span data-stu-id="658c7-194">Install the latest version from 3.1 channel to the specified location:</span></span>

  <span data-ttu-id="658c7-195">W systemie Windows:</span><span class="sxs-lookup"><span data-stu-id="658c7-195">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel 3.1 -InstallDir C:\cli
  ```

  <span data-ttu-id="658c7-196">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="658c7-196">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel 3.1 --install-dir ~/cli
  ```

- <span data-ttu-id="658c7-197">Zainstaluj wersję 3.0.0 udostępnionego środowiska uruchomieniowego:</span><span class="sxs-lookup"><span data-stu-id="658c7-197">Install the 3.0.0 version of the shared runtime:</span></span>

  <span data-ttu-id="658c7-198">W systemie Windows:</span><span class="sxs-lookup"><span data-stu-id="658c7-198">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Runtime dotnet -Version 3.0.0
  ```

  <span data-ttu-id="658c7-199">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="658c7-199">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --runtime dotnet --version 3.0.0
  ```

- <span data-ttu-id="658c7-200">Uzyskaj skrypt i Zainstaluj wersję 2.1.2 za firmowym serwerem proxy (tylko system Windows):</span><span class="sxs-lookup"><span data-stu-id="658c7-200">Obtain script and install the 2.1.2 version behind a corporate proxy (Windows only):</span></span>

  ```powershell
  Invoke-WebRequest 'https://dot.net/v1/dotnet-install.ps1' -Proxy $env:HTTP_PROXY -ProxyUseDefaultCredentials -OutFile 'dotnet-install.ps1';
  ./dotnet-install.ps1 -InstallDir '~/.dotnet' -Version '2.1.2' -ProxyAddress $env:HTTP_PROXY -ProxyUseDefaultCredentials;
  ```

- <span data-ttu-id="658c7-201">Uzyskaj skrypt i zainstaluj interfejs wiersza polecenia platformy .NET Core przykłady jednoliniowe:</span><span class="sxs-lookup"><span data-stu-id="658c7-201">Obtain script and install .NET Core CLI one-liner examples:</span></span>

  <span data-ttu-id="658c7-202">W systemie Windows:</span><span class="sxs-lookup"><span data-stu-id="658c7-202">Windows:</span></span>

  ```powershell
  # Run a separate PowerShell process because the script calls exit, so it will end the current PowerShell session.
  &powershell -NoProfile -ExecutionPolicy unrestricted -Command "[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; &([scriptblock]::Create((Invoke-WebRequest -UseBasicParsing 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"
  ```

  <span data-ttu-id="658c7-203">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="658c7-203">macOS/Linux:</span></span>

  ```bash
  curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>
  ```

## <a name="see-also"></a><span data-ttu-id="658c7-204">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="658c7-204">See also</span></span>

- [<span data-ttu-id="658c7-205">Wersje platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="658c7-205">.NET Core releases</span></span>](https://github.com/dotnet/core/releases)
- [<span data-ttu-id="658c7-206">Środowisko uruchomieniowe programu .NET Core i archiwum pobierania zestawu SDK</span><span class="sxs-lookup"><span data-stu-id="658c7-206">.NET Core Runtime and SDK download archive</span></span>](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)

---
title: skrypty instalacji DotNet
description: Więcej informacji na temat skryptów instalacji dotnet do zainstalowania narzędzi interfejsu wiersza polecenia platformy .NET Core i udostępnionego środowiska uruchomieniowego.
ms.date: 01/16/2019
ms.openlocfilehash: 6404a8332a7196f0e6fdfe649c2c180970390775
ms.sourcegitcommit: e39d93d358974b9ed4541cedf4e25c0101015c3c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2019
ms.locfileid: "55204798"
---
# <a name="dotnet-install-scripts-reference"></a><span data-ttu-id="da99f-103">Dokumentacja skryptów instalacji DotNet</span><span class="sxs-lookup"><span data-stu-id="da99f-103">dotnet-install scripts reference</span></span>

## <a name="name"></a><span data-ttu-id="da99f-104">Nazwa</span><span class="sxs-lookup"><span data-stu-id="da99f-104">Name</span></span>

<span data-ttu-id="da99f-105">`dotnet-install.ps1` | `dotnet-install.sh` — Skrypt używany do instalacji narzędzi interfejsu wiersza polecenia platformy .NET Core i udostępnionego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="da99f-105">`dotnet-install.ps1` | `dotnet-install.sh` - Script used to install the .NET Core CLI tools and the shared runtime.</span></span>

## <a name="synopsis"></a><span data-ttu-id="da99f-106">Streszczenie</span><span class="sxs-lookup"><span data-stu-id="da99f-106">Synopsis</span></span>

<span data-ttu-id="da99f-107">W systemie Windows:</span><span class="sxs-lookup"><span data-stu-id="da99f-107">Windows:</span></span>

`dotnet-install.ps1 [-Channel] [-Version] [-InstallDir] [-Architecture] [-SharedRuntime] [-Runtime] [-DryRun] [-NoPath] [-Verbose] [-AzureFeed] [-UncachedFeed] [-NoCdn] [-FeedCredential] [-ProxyAddress] [-ProxyUseDefaultCredentials] [-SkipNonVersionedFiles] [-Help]`

<span data-ttu-id="da99f-108">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="da99f-108">macOS/Linux:</span></span>

`dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture] [--runtime] [--dry-run] [--no-path] [--verbose] [--azure-feed] [--uncached-feed] [--no-cdn] [--feed-credential] [--runtime-id] [--skip-non-versioned-files] [--help]`

## <a name="description"></a><span data-ttu-id="da99f-109">Opis</span><span class="sxs-lookup"><span data-stu-id="da99f-109">Description</span></span>

<span data-ttu-id="da99f-110">`dotnet-install` Skrypty są używane do przeprowadzenia instalacji bez uprawnień administratora programu .NET Core SDK, w tym narzędzi interfejsu wiersza polecenia platformy .NET Core i udostępnionego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="da99f-110">The `dotnet-install` scripts are used to perform a non-admin installation of the .NET Core SDK, which includes the .NET Core CLI tools and the shared runtime.</span></span>

<span data-ttu-id="da99f-111">Zalecane jest użycie stabilną wersję, która jest hostowana na [głównej witryny internetowej platformy .NET Core](https://dot.net).</span><span class="sxs-lookup"><span data-stu-id="da99f-111">We recommend that you use the stable version that is hosted on [.NET Core main website](https://dot.net).</span></span> <span data-ttu-id="da99f-112">Bezpośrednie ścieżki do skryptów są:</span><span class="sxs-lookup"><span data-stu-id="da99f-112">The direct paths to the scripts are:</span></span>

* <span data-ttu-id="da99f-113"><https://dot.net/v1/dotnet-install.sh> (powłoki bash, UNIX)</span><span class="sxs-lookup"><span data-stu-id="da99f-113"><https://dot.net/v1/dotnet-install.sh> (bash, UNIX)</span></span>
* <span data-ttu-id="da99f-114"><https://dot.net/v1/dotnet-install.ps1> (Program Powershell, Windows)</span><span class="sxs-lookup"><span data-stu-id="da99f-114"><https://dot.net/v1/dotnet-install.ps1> (Powershell, Windows)</span></span>

<span data-ttu-id="da99f-115">Główne użyteczność tych skryptów znajduje się w scenariuszach automatyzacji oraz przed instalacjami bez uprawnień administratora.</span><span class="sxs-lookup"><span data-stu-id="da99f-115">The main usefulness of these scripts is in automation scenarios and non-admin installations.</span></span> <span data-ttu-id="da99f-116">Istnieją dwa skrypty: jeden z nich jest skrypt programu PowerShell, który działa na Windows, a drugi to skrypt powłoki bash, który działa w systemie Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="da99f-116">There are two scripts: one is a PowerShell script that works on Windows, and the other is a bash script that works on Linux/macOS.</span></span> <span data-ttu-id="da99f-117">Zarówno skryptów mają takie samo zachowanie.</span><span class="sxs-lookup"><span data-stu-id="da99f-117">Both scripts have the same behavior.</span></span> <span data-ttu-id="da99f-118">Skrypt powłoki bash odczytuje również przełączników programu PowerShell, aby można było używać przełączników programu PowerShell przy użyciu skryptu w systemach Linux/macOS.</span><span class="sxs-lookup"><span data-stu-id="da99f-118">The bash script also reads PowerShell switches, so you can use PowerShell switches with the script on Linux/macOS systems.</span></span>

<span data-ttu-id="da99f-119">Skrypty instalacji Pobierz plik ZIP/pliku tar z spadnie kompilacji interfejsu wiersza polecenia i przejdź do instalacji w lokalizacji domyślnej lub w lokalizacji określonej przez `-InstallDir|--install-dir`.</span><span class="sxs-lookup"><span data-stu-id="da99f-119">The installation scripts download the ZIP/tarball file from the CLI build drops and proceed to install it in either the default location or in a location specified by `-InstallDir|--install-dir`.</span></span> <span data-ttu-id="da99f-120">Domyślnie skrypty instalacyjne Pobierz zestaw SDK i zainstaluj go.</span><span class="sxs-lookup"><span data-stu-id="da99f-120">By default, the installation scripts download the SDK and install it.</span></span> <span data-ttu-id="da99f-121">Jeśli chcesz uzyskać tylko udostępnionego środowiska uruchomieniowego, należy określić `--runtime` argumentu.</span><span class="sxs-lookup"><span data-stu-id="da99f-121">If you wish to only obtain the shared runtime, specify the `--runtime` argument.</span></span>

<span data-ttu-id="da99f-122">Domyślnie skrypt ten dodaje lokalizacji instalacji do $PATH dla bieżącej sesji.</span><span class="sxs-lookup"><span data-stu-id="da99f-122">By default, the script adds the install location to the $PATH for the current session.</span></span> <span data-ttu-id="da99f-123">To zachowanie domyślne można przesłonić, określając `--no-path` argumentu.</span><span class="sxs-lookup"><span data-stu-id="da99f-123">Override this default behavior by specifying the `--no-path` argument.</span></span>

<span data-ttu-id="da99f-124">Przed uruchomieniem skryptu, zainstalować wymagane [zależności](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span><span class="sxs-lookup"><span data-stu-id="da99f-124">Before running the script, install the required [dependencies](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).</span></span>

<span data-ttu-id="da99f-125">Można to zrobić przy użyciu określonej wersji `--version` argumentu.</span><span class="sxs-lookup"><span data-stu-id="da99f-125">You can install a specific version using the `--version` argument.</span></span> <span data-ttu-id="da99f-126">Wersja muszą być określone jako (na przykład 1.0.0-13232) w wersji trzyczęściowej serii.</span><span class="sxs-lookup"><span data-stu-id="da99f-126">The version must be specified as a three-part version (for example, 1.0.0-13232).</span></span> <span data-ttu-id="da99f-127">Jeśli nie zostanie podana, używa `latest` wersji.</span><span class="sxs-lookup"><span data-stu-id="da99f-127">If not provided, it uses the `latest` version.</span></span>

## <a name="options"></a><span data-ttu-id="da99f-128">Opcje</span><span class="sxs-lookup"><span data-stu-id="da99f-128">Options</span></span>

* **`-Channel <CHANNEL>`**

  <span data-ttu-id="da99f-129">Określa identyfikator kanału źródła dla instalacji.</span><span class="sxs-lookup"><span data-stu-id="da99f-129">Specifies the source channel for the installation.</span></span> <span data-ttu-id="da99f-130">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="da99f-130">The possible values are:</span></span>

  * <span data-ttu-id="da99f-131">`Current` — Najnowsza wersja.</span><span class="sxs-lookup"><span data-stu-id="da99f-131">`Current` - Most current release.</span></span>
  * <span data-ttu-id="da99f-132">`LTS` — Długoterminowe kanału pomocy technicznej (Najnowsza wersja obsługiwane).</span><span class="sxs-lookup"><span data-stu-id="da99f-132">`LTS` - Long-Term Support channel (most current supported release).</span></span>
  * <span data-ttu-id="da99f-133">Wersja legalną dwuczęściową w formacie X.Y reprezentujący określonej wersji (na przykład `2.0` lub `1.0`).</span><span class="sxs-lookup"><span data-stu-id="da99f-133">Two-part version in X.Y format representing a specific release (for example, `2.0` or `1.0`).</span></span>
  * <span data-ttu-id="da99f-134">Nazwa gałęzi.</span><span class="sxs-lookup"><span data-stu-id="da99f-134">Branch name.</span></span> <span data-ttu-id="da99f-135">Na przykład `release/2.0.0`, `release/2.0.0-preview2`, lub `master` (w przypadku nocne wydania).</span><span class="sxs-lookup"><span data-stu-id="da99f-135">For example, `release/2.0.0`, `release/2.0.0-preview2`, or `master` (for nightly releases).</span></span>

  <span data-ttu-id="da99f-136">Wartość domyślna to `LTS`.</span><span class="sxs-lookup"><span data-stu-id="da99f-136">The default value is `LTS`.</span></span> <span data-ttu-id="da99f-137">Aby uzyskać więcej informacji dotyczących kanałów pomocy technicznej platformy .NET, zobacz [.NET obsługuje zasady](https://www.microsoft.com/net/platform/support-policy#dotnet-core) strony.</span><span class="sxs-lookup"><span data-stu-id="da99f-137">For more information on .NET support channels, see the [.NET Support Policy](https://www.microsoft.com/net/platform/support-policy#dotnet-core) page.</span></span>

* **`-Version <VERSION>`**

  <span data-ttu-id="da99f-138">Reprezentuje wersję konkretnej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="da99f-138">Represents a specific build version.</span></span> <span data-ttu-id="da99f-139">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="da99f-139">The possible values are:</span></span>

  * <span data-ttu-id="da99f-140">`latest` -Najnowszych kompilacji w kanale (używany z `-Channel` opcji).</span><span class="sxs-lookup"><span data-stu-id="da99f-140">`latest` - Latest build on the channel (used with the `-Channel` option).</span></span>
  * <span data-ttu-id="da99f-141">`coherent` — Najnowsza wersja spójnego kompilacji na kanał. używa kombinacji najnowszy stabilny pakiet (używany przy użyciu gałęzi o nazwie `-Channel` opcje).</span><span class="sxs-lookup"><span data-stu-id="da99f-141">`coherent` - Latest coherent build on the channel; uses the latest stable package combination (used with Branch name `-Channel` options).</span></span>
  * <span data-ttu-id="da99f-142">Trzyczęściowej wersję w formacie X.Y.Z reprezentującą określony kompilacji wersji; zastępuje `-Channel` opcji.</span><span class="sxs-lookup"><span data-stu-id="da99f-142">Three-part version in X.Y.Z format representing a specific build version; supersedes the `-Channel` option.</span></span> <span data-ttu-id="da99f-143">Na przykład: `2.0.0-preview2-006120`.</span><span class="sxs-lookup"><span data-stu-id="da99f-143">For example: `2.0.0-preview2-006120`.</span></span>

  <span data-ttu-id="da99f-144">Jeśli nie zostanie określony, `-Version` wartość domyślna to `latest`.</span><span class="sxs-lookup"><span data-stu-id="da99f-144">If not specified, `-Version` defaults to `latest`.</span></span>

* **`-InstallDir <DIRECTORY>`**

  <span data-ttu-id="da99f-145">Określa ścieżkę instalacji.</span><span class="sxs-lookup"><span data-stu-id="da99f-145">Specifies the installation path.</span></span> <span data-ttu-id="da99f-146">Katalog jest tworzony, jeśli nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="da99f-146">The directory is created if it doesn't exist.</span></span> <span data-ttu-id="da99f-147">Wartość domyślna to *%LocalAppData%\Microsoft\dotnet*.</span><span class="sxs-lookup"><span data-stu-id="da99f-147">The default value is *%LocalAppData%\Microsoft\dotnet*.</span></span> <span data-ttu-id="da99f-148">Pliki binarne są umieszczane bezpośrednio w tym katalogu.</span><span class="sxs-lookup"><span data-stu-id="da99f-148">Binaries are placed directly in this directory.</span></span>

* **`-Architecture <ARCHITECTURE>`**

  <span data-ttu-id="da99f-149">Architektura platformy .NET Core pliki binarne do zainstalowania.</span><span class="sxs-lookup"><span data-stu-id="da99f-149">Architecture of the .NET Core binaries to install.</span></span> <span data-ttu-id="da99f-150">Możliwe wartości to `<auto>`, `amd64`, `x64`, `x86`, `arm64`, i `arm`.</span><span class="sxs-lookup"><span data-stu-id="da99f-150">Possible values are `<auto>`, `amd64`, `x64`, `x86`, `arm64`, and `arm`.</span></span> <span data-ttu-id="da99f-151">Wartość domyślna to `<auto>`, który reprezentuje aktualnie uruchomionych architektury systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="da99f-151">The default value is `<auto>`, which represents the currently running OS architecture.</span></span>

* **`-SharedRuntime`**

  > [!NOTE]
  > <span data-ttu-id="da99f-152">Ten parametr jest przestarzały i może zostać usunięty w przyszłych wersjach skryptu.</span><span class="sxs-lookup"><span data-stu-id="da99f-152">This parameter is obsolete and may be removed in a future version of the script.</span></span> <span data-ttu-id="da99f-153">Zalecaną alternatywą jest `Runtime` opcji.</span><span class="sxs-lookup"><span data-stu-id="da99f-153">The recommended alternative is the `Runtime` option.</span></span>

  <span data-ttu-id="da99f-154">Instaluje tylko bity udostępnionego środowiska uruchomieniowego, a nie całego zestawu SDK.</span><span class="sxs-lookup"><span data-stu-id="da99f-154">Installs just the shared runtime bits, not the entire SDK.</span></span> <span data-ttu-id="da99f-155">To jest równoznaczne z użyciem `-Runtime dotnet`.</span><span class="sxs-lookup"><span data-stu-id="da99f-155">This is equivalent to specifying `-Runtime dotnet`.</span></span>

* **`-Runtime <RUNTIME>`**

  <span data-ttu-id="da99f-156">Instaluje tylko udostępnionego środowiska uruchomieniowego, nie cały zestaw SDK.</span><span class="sxs-lookup"><span data-stu-id="da99f-156">Installs just the shared runtime, not the entire SDK.</span></span> <span data-ttu-id="da99f-157">Możliwe wartości to:</span><span class="sxs-lookup"><span data-stu-id="da99f-157">The possible values are:</span></span>

  * <span data-ttu-id="da99f-158">`dotnet` - `Microsoft.NETCore.App` udostępnionego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="da99f-158">`dotnet` - the `Microsoft.NETCore.App` shared runtime.</span></span>
  * <span data-ttu-id="da99f-159">`aspnetcore` - `Microsoft.AspNetCore.App` udostępnionego środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="da99f-159">`aspnetcore` - the `Microsoft.AspNetCore.App` shared runtime.</span></span>

* **`-DryRun`**

  <span data-ttu-id="da99f-160">Jeśli nie będzie ustawiona, skrypt przeprowadzić instalację.</span><span class="sxs-lookup"><span data-stu-id="da99f-160">If set, the script won't perform the installation.</span></span> <span data-ttu-id="da99f-161">Zamiast tego wyświetla wiersz polecenia na potrzeby spójnego zainstalować obecnie żądana wersja interfejsu wiersza polecenia platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="da99f-161">Instead, it displays what command line to use to consistently install the currently requested version of the .NET Core CLI.</span></span> <span data-ttu-id="da99f-162">Na przykład, jeśli określona wersja `latest`, wyświetla łącze do określonej wersji, aby to polecenie może być używane w sposób deterministyczny w skrypcie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="da99f-162">For example, if you specify version `latest`, it displays a link with the specific version so that this command can be used deterministically in a build script.</span></span> <span data-ttu-id="da99f-163">Lokalizacja tego pliku binarnego również wyświetlana, jeśli wolisz zainstalować lub pobrać go samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="da99f-163">It also displays the binary's location if you prefer to install or download it yourself.</span></span>

* **`-NoPath`**

  <span data-ttu-id="da99f-164">Jeśli zestawu i folderu instalacji nie jest eksportowany do ścieżki dla bieżącej sesji.</span><span class="sxs-lookup"><span data-stu-id="da99f-164">If set, the installation folder isn't exported to the path for the current session.</span></span> <span data-ttu-id="da99f-165">Domyślnie skrypt modyfikuje ścieżki, która udostępnia natychmiast po przeprowadzeniu instalacji narzędzi interfejsu wiersza polecenia.</span><span class="sxs-lookup"><span data-stu-id="da99f-165">By default, the script modifies the PATH, which makes the CLI tools available immediately after install.</span></span>

* **`-Verbose`**

  <span data-ttu-id="da99f-166">Wyświetla informacje diagnostyczne.</span><span class="sxs-lookup"><span data-stu-id="da99f-166">Displays diagnostics information.</span></span>

* **`-AzureFeed`**

  <span data-ttu-id="da99f-167">Określa, że adres URL dla platformy Azure, źródła danych do Instalatora.</span><span class="sxs-lookup"><span data-stu-id="da99f-167">Specifies the URL for the Azure feed to the installer.</span></span> <span data-ttu-id="da99f-168">Zaleca się, że nie możesz zmienić tę wartość.</span><span class="sxs-lookup"><span data-stu-id="da99f-168">We recommended that you don't change this value.</span></span> <span data-ttu-id="da99f-169">Wartość domyślna to `https://dotnetcli.azureedge.net/dotnet`.</span><span class="sxs-lookup"><span data-stu-id="da99f-169">The default value is `https://dotnetcli.azureedge.net/dotnet`.</span></span>

* **`-UncachedFeed`**

  <span data-ttu-id="da99f-170">Umożliwia, zmiana adresu URL dla źródła danych bez buforowania używane przez tego Instalatora.</span><span class="sxs-lookup"><span data-stu-id="da99f-170">Allows changing the URL for the uncached feed used by this installer.</span></span> <span data-ttu-id="da99f-171">Zaleca się, że nie możesz zmienić tę wartość.</span><span class="sxs-lookup"><span data-stu-id="da99f-171">We recommended that you don't change this value.</span></span>

* **`-NoCdn`**

  <span data-ttu-id="da99f-172">Wyłącza pobierania z [Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) i korzysta z bezpośrednio bez buforowania źródła danych.</span><span class="sxs-lookup"><span data-stu-id="da99f-172">Disables downloading from the [Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) and uses the uncached feed directly.</span></span>

* **`-FeedCredential`**

  <span data-ttu-id="da99f-173">Używane jako ciąg zapytania do dołączenia do platformy Azure, źródła danych.</span><span class="sxs-lookup"><span data-stu-id="da99f-173">Used as a query string to append to the Azure feed.</span></span> <span data-ttu-id="da99f-174">Umożliwia ona, zmiana adresu URL, aby użyć konta magazynu obiektów blob bez publicznego.</span><span class="sxs-lookup"><span data-stu-id="da99f-174">It allows changing the URL to use non-public blob storage accounts.</span></span>

* **`-ProxyAddress`**

  <span data-ttu-id="da99f-175">Jeśli zestaw, Instalator używa serwera proxy w przypadku wysyłania żądań sieci web.</span><span class="sxs-lookup"><span data-stu-id="da99f-175">If set, the installer uses the proxy when making web requests.</span></span> <span data-ttu-id="da99f-176">(Ta funkcja jest prawidłowa tylko dla Windows)</span><span class="sxs-lookup"><span data-stu-id="da99f-176">(Only valid for Windows)</span></span>

* **`ProxyUseDefaultCredentials`**

  <span data-ttu-id="da99f-177">Jeśli zestaw, Instalator używa poświadczeń bieżącego użytkownika, korzystając z adresu serwera proxy.</span><span class="sxs-lookup"><span data-stu-id="da99f-177">If set, the installer uses the credentials of the current user when using proxy address.</span></span> <span data-ttu-id="da99f-178">(Ta funkcja jest prawidłowa tylko dla Windows)</span><span class="sxs-lookup"><span data-stu-id="da99f-178">(Only valid for Windows)</span></span>

* **`-SkipNonVersionedFiles`**

  <span data-ttu-id="da99f-179">Pomija instalowania innych wersji plików, takich jak *dotnet.exe*, jeśli już istnieje.</span><span class="sxs-lookup"><span data-stu-id="da99f-179">Skips installing non-versioned files, such as *dotnet.exe*, if they already exist.</span></span>

* **`-Help`**

  <span data-ttu-id="da99f-180">Drukuje pomoc dotyczącą skryptu.</span><span class="sxs-lookup"><span data-stu-id="da99f-180">Prints out help for the script.</span></span>

## <a name="examples"></a><span data-ttu-id="da99f-181">Przykłady</span><span class="sxs-lookup"><span data-stu-id="da99f-181">Examples</span></span>

* <span data-ttu-id="da99f-182">W domyślnej lokalizacji, należy zainstalować najnowsze długoterminowe obsługiwaną wersję (LTS):</span><span class="sxs-lookup"><span data-stu-id="da99f-182">Install the latest long-term supported (LTS) version to the default location:</span></span>

  <span data-ttu-id="da99f-183">W systemie Windows:</span><span class="sxs-lookup"><span data-stu-id="da99f-183">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel LTS
  ```

  <span data-ttu-id="da99f-184">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="da99f-184">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel LTS
  ```

* <span data-ttu-id="da99f-185">Zainstaluj najnowszą wersję z kanału 2.0 do określonej lokalizacji:</span><span class="sxs-lookup"><span data-stu-id="da99f-185">Install the latest version from 2.0 channel to the specified location:</span></span>

  <span data-ttu-id="da99f-186">W systemie Windows:</span><span class="sxs-lookup"><span data-stu-id="da99f-186">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Channel 2.0 -InstallDir C:\cli
  ```

  <span data-ttu-id="da99f-187">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="da99f-187">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --channel 2.0 --install-dir ~/cli
  ```

* <span data-ttu-id="da99f-188">Zainstaluj 1.1.0 wersji udostępnionego środowiska uruchomieniowego:</span><span class="sxs-lookup"><span data-stu-id="da99f-188">Install the 1.1.0 version of the shared runtime:</span></span>

  <span data-ttu-id="da99f-189">W systemie Windows:</span><span class="sxs-lookup"><span data-stu-id="da99f-189">Windows:</span></span>

  ```powershell
  ./dotnet-install.ps1 -Runtime dotnet -Version 1.1.0
  ```

  <span data-ttu-id="da99f-190">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="da99f-190">macOS/Linux:</span></span>

  ```bash
  ./dotnet-install.sh --runtime dotnet --version 1.1.0
  ```

* <span data-ttu-id="da99f-191">Skrypt należy uzyskać i zainstalować 2.1.2 wersja za firmowym serwerem proxy (tylko Windows):</span><span class="sxs-lookup"><span data-stu-id="da99f-191">Obtain script and install the 2.1.2 version behind a corporate proxy (Windows only):</span></span>

  ```powershell
  Invoke-WebRequest 'https://dot.net/v1/dotnet-install.ps1' -Proxy $env:HTTP_PROXY -ProxyUseDefaultCredentials -OutFile 'dotnet-install.ps1';
  ./dotnet-install.ps1 -InstallDir '~/.dotnet' -Version '2.1.2' -ProxyAddress $env:HTTP_PROXY -ProxyUseDefaultCredentials;
  ```

* <span data-ttu-id="da99f-192">Uzyskać skrypt i zainstaluj interfejs wiersza polecenia platformy .NET Core one-liner przykłady:</span><span class="sxs-lookup"><span data-stu-id="da99f-192">Obtain script and install .NET Core CLI one-liner examples:</span></span>

  <span data-ttu-id="da99f-193">W systemie Windows:</span><span class="sxs-lookup"><span data-stu-id="da99f-193">Windows:</span></span>

  ```powershell
  @powershell -NoProfile -ExecutionPolicy unrestricted -Command "[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; &([scriptblock]::Create((Invoke-WebRequest -useb 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"
  ```

  <span data-ttu-id="da99f-194">macOS/Linux:</span><span class="sxs-lookup"><span data-stu-id="da99f-194">macOS/Linux:</span></span>

  ```bash
  curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>
  ```

## <a name="see-also"></a><span data-ttu-id="da99f-195">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="da99f-195">See also</span></span>

- [<span data-ttu-id="da99f-196">Wersje platformy .NET core</span><span class="sxs-lookup"><span data-stu-id="da99f-196">.NET Core releases</span></span>](https://github.com/dotnet/core/releases)
- [<span data-ttu-id="da99f-197">Środowisko uruchomieniowe programu .NET core i zestawu SDK Pobierz archiwum</span><span class="sxs-lookup"><span data-stu-id="da99f-197">.NET Core Runtime and SDK download archive</span></span>](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)

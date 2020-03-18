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
# <a name="dotnet-install-scripts-reference"></a>Odwołanie doskryptów dotnet-install

## <a name="name"></a>Nazwa

`dotnet-install.ps1` | `dotnet-install.sh`- Skrypt używany do instalowania .NET Core SDK i udostępnionego programu runtime.

## <a name="synopsis"></a>Streszczenie

W systemie Windows:

```powershell
dotnet-install.ps1 [-Channel] [-Version] [-JSonFile] [-InstallDir] [-Architecture]
    [-Runtime] [-DryRun] [-NoPath] [-Verbose] [-AzureFeed] [-UncachedFeed] [-NoCdn] [-FeedCredential]
    [-ProxyAddress] [-ProxyUseDefaultCredentials] [-SkipNonVersionedFiles] [-Help]
```

Linux/ macOs:

```bash
dotnet-install.sh [--channel] [--version] [--jsonfile] [--install-dir] [--architecture]
    [--runtime] [--dry-run] [--no-path] [--verbose] [--azure-feed] [--uncached-feed] [--no-cdn] [--feed-credential]
    [--runtime-id] [--skip-non-versioned-files] [--help]
```

## <a name="description"></a>Opis

Skrypty `dotnet-install` są używane do wykonywania instalacji bez administratora .NET Core SDK, która obejmuje .NET Core CLI i udostępnionego programu runtime.

Zaleca się użycie stabilnej wersji skryptów:

- Bash (Linux/macOS):<https://dot.net/v1/dotnet-install.sh>
- Program PowerShell (Windows):<https://dot.net/v1/dotnet-install.ps1>

Główną przydatność tych skryptów jest w scenariuszach automatyzacji i instalacji nie-administratora. Istnieją dwa skrypty: jeden jest skrypt programu PowerShell, który działa w systemie Windows, a drugi jest skrypt bash, który działa na Linux / macOS. Oba skrypty mają takie samo zachowanie. Skrypt bash odczytuje również przełączniki programu PowerShell, dzięki czemu można używać przełączników programu PowerShell ze skryptem w systemach Linux/macOS.

Skrypty instalacyjne pobierają plik ZIP/tarball z kompilacji CLI i kontynuują instalację w lokalizacji `-InstallDir|--install-dir`domyślnej lub w lokalizacji określonej przez . Domyślnie skrypty instalacyjne pobierają zestaw SDK i instalują go. Jeśli chcesz uzyskać tylko udostępnionego czasu `-Runtime|--runtime` wykonywania, należy określić argument.

Domyślnie skrypt dodaje lokalizację instalacji do $PATH dla bieżącej sesji. Zastąp to domyślne `-NoPath|--no-path` zachowanie, określając argument.

Przed uruchomieniem skryptu zainstaluj wymagane [zależności](../install/dependencies.md).

Można zainstalować określoną wersję `-Version|--version` przy użyciu argumentu. Wersja musi być określona jako wersja trzyczęściowa `2.1.0`(na przykład). Jeśli nie podano, `latest` używa wersji.

## <a name="options"></a>Opcje

- **`-Channel|--channel <CHANNEL>`**

  Określa kanał źródłowy instalacji. Możliwe wartości są następujące:

  - `Current`- Większość bieżącego wydania.
  - `LTS`- Kanał wsparcia długoterminowego (najbardziej aktualna obsługiwana wersja).
  - Wersja dwuczęściowa w formacie X.Y reprezentująca określoną `2.1` `3.0`wersję (na przykład lub ).
  - Nazwa gałęzi: na `release/3.1.1xx` `master` przykład lub (dla wersji nocnych). Użyj tej opcji, aby zainstalować wersję z kanału podglądu. Użyj nazwy kanału wymienionej w [instalatorach i plikach binarnych](https://github.com/dotnet/core-sdk#installers-and-binaries).

  Wartością domyślną jest `LTS`. Aby uzyskać więcej informacji na temat kanałów pomocy technicznej .NET, zobacz stronę [Zasady pomocy technicznej .NET.](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)

- **`-Version|--version <VERSION>`**

  Reprezentuje określoną wersję kompilacji. Możliwe wartości są następujące:

  - `latest`- Najnowsza kompilacja na `-Channel` kanale (używana z opcją).
  - `coherent`- Najnowsza spójna kompilacja na kanale; używa najnowszej stabilnej kombinacji `-Channel` pakietów (używanej z opcjami nazwy gałęzi).
  - Wersja trzyczęściowa w formacie X.Y.Z reprezentująca określoną wersję kompilacji; zastępuje `-Channel` tę opcję. Na przykład: `2.0.0-preview2-006120`.

  Jeśli nie zostanie `-Version` określony, `latest`domyślnie .

- **`-JSonFile|--jsonfile <JSONFILE>`**

  Określa ścieżkę do pliku [global.json,](global-json.md) która będzie używana do określania wersji sdk. Plik *global.json* musi mieć `sdk:version`wartość dla .

- **`-InstallDir|--install-dir <DIRECTORY>`**

  Określa ścieżkę instalacji. Katalog jest tworzony, jeśli nie istnieje. Wartością domyślną jest *%LocalAppData%\Microsoft\dotnet*. Pliki binarne są umieszczane bezpośrednio w tym katalogu.

- **`-Architecture|--architecture <ARCHITECTURE>`**

  Architektura plików binarnych .NET Core do zainstalowania. Możliwe wartości `<auto>` `amd64`to `x64` `x86`, `arm64`, `arm`, , i . Wartością domyślną jest `<auto>`, która reprezentuje aktualnie uruchomioną architekturę os.

- **`-SharedRuntime|--shared-runtime`**

  > [!NOTE]
  > Ten parametr jest przestarzały i może zostać usunięty w przyszłej wersji skryptu. Zalecaną alternatywą `-Runtime|--runtime` jest opcja.

  Instaluje tylko udostępnione bity czasu wykonywania, a nie cały zestaw SDK. Ta opcja jest równoważna z określeniem `-Runtime|--runtime dotnet`.

- **`-Runtime|--runtime <RUNTIME>`**

  Instaluje tylko udostępniony czas wykonywania, a nie cały zestaw SDK. Możliwe wartości są następujące:

  - `dotnet`- `Microsoft.NETCore.App` udostępnionego czasu wykonywania.
  - `aspnetcore`- `Microsoft.AspNetCore.App` udostępnionego czasu wykonywania.
  - `windowsdesktop`- `Microsoft.WindowsDesktop.App` udostępnionego czasu wykonywania.

- **`-DryRun|--dry-run`**

  Jeśli jest ustawiona, skrypt nie będzie wykonywać instalacji. Zamiast tego wyświetla wiersz polecenia, który ma być używany do konsekwentnego instalowania aktualnie żądanej wersji wiersza wiersza wiersza wiersza wiersza wiersza .NET Core. Na przykład, jeśli `latest`określisz wersję, wyświetla łącze z określoną wersją, dzięki czemu to polecenie może być używane deterministycznie w skrypcie kompilacji. Wyświetla również lokalizację pliku binarnego, jeśli wolisz zainstalować lub pobrać go samodzielnie.

- **`-NoPath|--no-path`**

  Jeśli jest ustawiona, folder instalacyjny nie jest eksportowany do ścieżki dla bieżącej sesji. Domyślnie skrypt modyfikuje PATH, co sprawia, że .NET Core CLI dostępne natychmiast po zainstalowaniu.

- **`-Verbose|--verbose`**

  Wyświetla informacje diagnostyczne.

- **`-AzureFeed|--azure-feed`**

  Określa adres URL źródła danych platformy Azure do instalatora. Zalecamy, aby nie zmieniać tej wartości. Wartością domyślną jest `https://dotnetcli.azureedge.net/dotnet`.

- **`-UncachedFeed|--uncached-feed`**

  Umożliwia zmianę adresu URL niebuforowanego źródła danych używanego przez tego instalatora. Zalecamy, aby nie zmieniać tej wartości.

- **`-NoCdn|--no-cdn`**

  Wyłącza pobieranie z [usługi Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) i bezpośrednio używa niebuforowego źródła danych.

- **`-FeedCredential|--feed-credential`**

  Używany jako ciąg zapytania do dostawienia do źródła danych platformy Azure. Umożliwia zmianę adresu URL do używania niepublicznych kont magazynu obiektów blob.

- **`--runtime-id`**

  Określa [identyfikator czasu wykonywania,](../rid-catalog.md) dla którego są instalowane narzędzia. Służy `linux-x64` do przenośnego linuksa. (Obowiązuje tylko dla systemu Linux/macOS)

- **`-ProxyAddress`**

  Jeśli jest ustawiona, instalator używa serwera proxy podczas tworzenia żądań sieci web. (Obowiązuje tylko dla systemu Windows)

- **`ProxyUseDefaultCredentials`**

  Jeśli jest ustawiona, instalator używa poświadczeń bieżącego użytkownika podczas korzystania z adresu serwera proxy. (Obowiązuje tylko dla systemu Windows)

- **`-SkipNonVersionedFiles|--skip-non-versioned-files`**

  Pomija instalowanie plików niewersjonowanych, takich jak *dotnet.exe*, jeśli już istnieją.

- **`-Help|--help`**

  Drukuje pomoc dla skryptu.

## <a name="examples"></a>Przykłady

- Zainstaluj najnowszą długoterminową wersję obsługiwaną (LTS) do lokalizacji domyślnej:

  W systemie Windows:

  ```powershell
  ./dotnet-install.ps1 -Channel LTS
  ```

  macOS/Linux:

  ```bash
  ./dotnet-install.sh --channel LTS
  ```

- Zainstaluj najnowszą wersję z kanału 3.1 do określonej lokalizacji:

  W systemie Windows:

  ```powershell
  ./dotnet-install.ps1 -Channel 3.1 -InstallDir C:\cli
  ```

  macOS/Linux:

  ```bash
  ./dotnet-install.sh --channel 3.1 --install-dir ~/cli
  ```

- Zainstaluj wersję 3.0.0 udostępnionego programu runtime:

  W systemie Windows:

  ```powershell
  ./dotnet-install.ps1 -Runtime dotnet -Version 3.0.0
  ```

  macOS/Linux:

  ```bash
  ./dotnet-install.sh --runtime dotnet --version 3.0.0
  ```

- Uzyskaj skrypt i zainstaluj wersję 2.1.2 za korporacyjnym serwerem proxy (tylko system Windows):

  ```powershell
  Invoke-WebRequest 'https://dot.net/v1/dotnet-install.ps1' -Proxy $env:HTTP_PROXY -ProxyUseDefaultCredentials -OutFile 'dotnet-install.ps1';
  ./dotnet-install.ps1 -InstallDir '~/.dotnet' -Version '2.1.2' -ProxyAddress $env:HTTP_PROXY -ProxyUseDefaultCredentials;
  ```

- Uzyskaj przykłady jednoliniowego skryptu i instaluj jeden-liner.NET Core:

  W systemie Windows:

  ```powershell
  # Run a separate PowerShell process because the script calls exit, so it will end the current PowerShell session.
  &powershell -NoProfile -ExecutionPolicy unrestricted -Command "[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; &([scriptblock]::Create((Invoke-WebRequest -UseBasicParsing 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"
  ```

  macOS/Linux:

  ```bash
  curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>
  ```

## <a name="see-also"></a>Zobacz też

- [Wersje programu .NET Core](https://github.com/dotnet/core/releases)
- [Archiwum pobierania programu .NET Core Runtime i SDK](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)

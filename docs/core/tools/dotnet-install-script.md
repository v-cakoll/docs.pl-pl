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
# <a name="dotnet-install-scripts-reference"></a>odwołanie do skryptów dotnet-install

## <a name="name"></a>Nazwa

`dotnet-install.ps1` | `dotnet-install.sh`- Skrypt używany do zainstalowania .NET Core SDK i udostępnionego środowiska uruchomieniowego.

## <a name="synopsis"></a>Streszczenie

W systemie Windows:

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

Linux/macOs:

```bash
dotnet-install.sh  [--architecture <ARCHITECTURE>] [--azure-feed]
    [--channel <CHANNEL>] [--dry-run] [--feed-credential]
    [--install-dir <DIRECTORY>] [--jsonfile <JSONFILE>]
    [--no-cdn] [--no-path] [--runtime <RUNTIME>] [--runtime-id <RID>]
    [--skip-non-versioned-files] [--uncached-feed] [--verbose]
    [--version <VERSION>]

dotnet-install.sh --help
```

## <a name="description"></a>Opis

Skrypty `dotnet-install` są używane do wykonywania instalacji niedministratorów .NET Core SDK, który zawiera .NET Core CLI i udostępnionego środowiska uruchomieniowego.

Zaleca się użycie stabilnej wersji skryptów:

- Bash (Linux/macOS):<https://dot.net/v1/dotnet-install.sh>
- Program PowerShell (Windows):<https://dot.net/v1/dotnet-install.ps1>

Główną zaletą tych skryptów jest w scenariuszach automatyzacji i instalacji innych niż administrator. Istnieją dwa skrypty: jeden to skrypt programu PowerShell, który działa w systemie Windows, a drugi to skrypt bash, który działa na Linuksie/macOS. Oba skrypty mają takie samo zachowanie. Skrypt bash odczytuje również przełączniki programu PowerShell, dzięki czemu można używać przełączników programu PowerShell ze skryptem w systemach Linux/macOS.

Skrypty instalacyjne pobierają plik ZIP/tarball z kompilacji interfejsu wiersza polecenia i przystępują `-InstallDir|--install-dir`do instalacji w domyślnej lokalizacji lub w lokalizacji określonej przez program . Domyślnie skrypty instalacyjne pobierają zestaw SDK i instalują go. Jeśli chcesz uzyskać tylko udostępnionego środowiska `-Runtime|--runtime` uruchomieniowego, określ argument.

Domyślnie skrypt dodaje lokalizację instalacji do $PATH bieżącej sesji. Zastądnie tego domyślnego `-NoPath|--no-path` zachowania, określając argument.

Przed uruchomieniem skryptu należy zainstalować wymagane [zależności](../install/dependencies.md).

Można zainstalować określoną wersję `-Version|--version` przy użyciu argumentu. Wersja musi być określona jako wersja trzyczęściowa (na `2.1.0`przykład). Jeśli nie podano, używa `latest` wersji.

## <a name="options"></a>Opcje

- **`-Architecture|--architecture <ARCHITECTURE>`**

  Architektura plików binarnych .NET Core do zainstalowania. Możliwe wartości `<auto>` `amd64`to `x64` `x86`, `arm64`, `arm`, , i . Wartością domyślną jest `<auto>`, która reprezentuje aktualnie działającą architekturę systemu operacyjnego.

- **`-AzureFeed|--azure-feed`**

  Określa adres URL kanału informacyjnego platformy Azure do instalatora. Zaleca się, aby nie zmieniać tej wartości. Wartością domyślną jest `https://dotnetcli.azureedge.net/dotnet`.

- **`-Channel|--channel <CHANNEL>`**

  Określa kanał źródłowy instalacji. Możliwe wartości są następujące:

  - `Current`- Większość bieżącej wersji.
  - `LTS`- Kanał wsparcia długoterminowego (najbardziej aktualna wersja obsługiwana).
  - Wersja dwuczęściowa w formacie X.Y reprezentująca określoną wersję (na przykład `2.1` lub `3.0`).
  - Nazwa oddziału: na `release/3.1.1xx` `master` przykład lub (dla wersji nocnych). Użyj tej opcji, aby zainstalować wersję z kanału podglądu. Użyj nazwy kanału wymienionej w [obszarze Instalatory i pliki binarne](https://github.com/dotnet/core-sdk#installers-and-binaries).

  Wartością domyślną jest `LTS`. Aby uzyskać więcej informacji na temat kanałów pomocy technicznej platformy .NET, zobacz stronę [Zasad pomocy technicznej platformy .NET.](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)

- **`-DryRun|--dry-run`**

  Jeśli jest ustawiona, skrypt nie wykona instalacji. Zamiast tego wyświetla wiersz polecenia, którego należy użyć do konsekwentnego instalowania aktualnie żądanej wersji interfejsu wiersza polecenia .NET Core. Na przykład jeśli określisz wersję `latest`, wyświetla łącze z określoną wersją, dzięki czemu to polecenie może być używane deterministycznie w skrypcie kompilacji. Wyświetla również lokalizację binarną, jeśli wolisz zainstalować lub pobrać go samodzielnie.

- **`-FeedCredential|--feed-credential`**

  Używany jako ciąg zapytania do dołączania do źródła danych platformy Azure. Umożliwia zmianę adresu URL do korzystania z kont magazynu obiektów blob niepublicznych.

- **`-Help|--help`**

  Drukuje pomoc dla skryptu.

- **`-InstallDir|--install-dir <DIRECTORY>`**

  Określa ścieżkę instalacji. Katalog jest tworzony, jeśli nie istnieje. Wartością domyślną jest *%LocalAppData%\Microsoft\dotnet*. Pliki binarne są umieszczane bezpośrednio w tym katalogu.

- **`-JSonFile|--jsonfile <JSONFILE>`**

  Określa ścieżkę do pliku [global.json,](global-json.md) który będzie używany do określania wersji SDK. Plik *global.json* musi mieć `sdk:version`wartość dla pliku .

- **`-NoCdn|--no-cdn`**

  Wyłącza pobieranie z [usługi Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) i używa kanału informacyjnego bez bufora bezpośrednio.

- **`-NoPath|--no-path`**

  Jeśli jest ustawiona, folder instalacyjny nie jest eksportowany do ścieżki dla bieżącej sesji. Domyślnie skrypt modyfikuje PATH, co sprawia, że .NET Core CLI dostępne natychmiast po zainstalowaniu.

- **`-ProxyAddress`**

  Jeśli jest ustawiona, instalator używa serwera proxy podczas składania żądań sieci web. (Dotyczy tylko systemu Windows).

- **`ProxyUseDefaultCredentials`**

  Jeśli jest ustawiona, instalator używa poświadczeń bieżącego użytkownika podczas korzystania z adresu serwera proxy. (Dotyczy tylko systemu Windows).

- **`-Runtime|--runtime <RUNTIME>`**

  Instaluje tylko udostępnione środowisko uruchomieniowe, a nie cały pakiet SDK. Możliwe wartości są następujące:

  - `dotnet`- `Microsoft.NETCore.App` współdzielony czas pracy.
  - `aspnetcore`- `Microsoft.AspNetCore.App` współdzielony czas pracy.
  - `windowsdesktop`- `Microsoft.WindowsDesktop.App` współdzielony czas pracy.

- **`--runtime-id <RID>`**

  Określa [identyfikator środowiska wykonawczego,](../rid-catalog.md) dla którego narzędzia są instalowane. Użyj `linux-x64` do przenośnego Linuksa. (Dotyczy tylko systemów Linux/macOS).

- **`-SharedRuntime|--shared-runtime`**

  > [!NOTE]
  > Ten parametr jest przestarzały i może zostać usunięty w przyszłej wersji skryptu. Zalecaną alternatywą `-Runtime|--runtime` jest opcja.

  Instaluje tylko udostępnione bity środowiska uruchomieniowego, a nie cały pakiet SDK. Ta opcja jest równoważna z określeniem `-Runtime|--runtime dotnet`.

- **`-SkipNonVersionedFiles|--skip-non-versioned-files`**

  Pomija instalowanie plików nieobrażonych, takich jak *dotnet.exe*, jeśli już istnieją.

- **`-UncachedFeed|--uncached-feed`**

  Umożliwia zmianę adresu URL niebukowanego kanału informacyjnego używanego przez tego instalatora. Zaleca się, aby nie zmieniać tej wartości.

- **`-Verbose|--verbose`**

  Wyświetla informacje diagnostyczne.

- **`-Version|--version <VERSION>`**

  Reprezentuje określoną wersję kompilacji. Możliwe wartości są następujące:

  - `latest`- Najnowsza kompilacja na `-Channel` kanale (używana z opcją).
  - `coherent`- Najnowsze spójne budować na kanale; używa najnowszej kombinacji pakietów stabilnych `-Channel` (używanej z opcjami nazwy oddziału).
  - Wersja trzyczęściowa w formacie X.Y.Z reprezentująca określoną wersję kompilacji; zastępuje `-Channel` tę opcję. Na przykład: `2.0.0-preview2-006120`.

  Jeśli nie `-Version` zostanie określony, wartość domyślna to `latest`.

## <a name="examples"></a>Przykłady

- Zainstaluj najnowszą długoterminową wersję obsługiwanej (LTS) w lokalizacji domyślnej:

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

- Zainstaluj wersję udostępnionego środowiska wykonawczego 3.0.0:

  W systemie Windows:

  ```powershell
  ./dotnet-install.ps1 -Runtime dotnet -Version 3.0.0
  ```

  macOS/Linux:

  ```bash
  ./dotnet-install.sh --runtime dotnet --version 3.0.0
  ```

- Uzyskaj skrypt i zainstaluj wersję 2.1.2 za firmowym serwerem proxy (tylko windows):

  ```powershell
  Invoke-WebRequest 'https://dot.net/v1/dotnet-install.ps1' -Proxy $env:HTTP_PROXY -ProxyUseDefaultCredentials -OutFile 'dotnet-install.ps1';
  ./dotnet-install.ps1 -InstallDir '~/.dotnet' -Version '2.1.2' -ProxyAddress $env:HTTP_PROXY -ProxyUseDefaultCredentials;
  ```

- Uzyskaj skrypt i zainstaluj przykłady one-liner net core cli:

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

- [Wersje .NET Core](https://github.com/dotnet/core/releases)
- [Archiwum pobierania .NET Core Runtime i SDK](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)

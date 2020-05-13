---
title: dotnet-install scripts
description: Więcej informacji na temat skryptów programu dotnet-Install w celu zainstalowania zestaw .NET Core SDK i udostępnionego środowiska uruchomieniowego.
ms.date: 04/30/2020
ms.openlocfilehash: 6728708ac5154f558954b46a22a434b05a548e84
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83205930"
---
# <a name="dotnet-install-scripts-reference"></a>dotnet — informacje o skryptach instalacji

## <a name="name"></a>Nazwa

`dotnet-install.ps1` | `dotnet-install.sh`-Skrypt służący do instalowania zestaw .NET Core SDK i udostępnionego środowiska uruchomieniowego.

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

`dotnet-install`Skrypty są używane do przeprowadzania instalacji nieadministratora zestaw .NET Core SDK, w tym interfejs wiersza polecenia platformy .NET Core i udostępnionego środowiska uruchomieniowego.

Zalecamy użycie stabilnej wersji skryptów:

- Bash (Linux/macOS):<https://dot.net/v1/dotnet-install.sh>
- PowerShell (Windows):<https://dot.net/v1/dotnet-install.ps1>

Główna użyteczność tych skryptów jest w scenariuszach automatyzacji i instalacjach nienależących do administratora. Istnieją dwa skrypty: jeden to skrypt programu PowerShell, który działa w systemie Windows, a drugi to skrypt bash, który działa w systemie Linux/macOS. Oba skrypty mają takie samo zachowanie. Skrypt bash odczytuje również przełączniki programu PowerShell, dzięki czemu można użyć przełączników programu PowerShell z skryptem w systemach Linux/macOS.

Skrypty instalacyjne pobierają plik ZIP/plik tar z kompilacji interfejsu wiersza polecenia, a następnie instalują go w lokalizacji domyślnej lub w lokalizacji określonej przez `-InstallDir|--install-dir` . Domyślnie skrypty instalacyjne pobierają zestaw SDK i instalują go. Jeśli chcesz uzyskać tylko udostępnione środowisko uruchomieniowe, określ `-Runtime|--runtime` argument.

Domyślnie skrypt dodaje lokalizację instalacji do $PATH bieżącej sesji. Zastąp to zachowanie domyślne, określając `-NoPath|--no-path` argument.

Przed uruchomieniem skryptu Zainstaluj wymagane [zależności](../install/dependencies.md).

Można zainstalować określoną wersję przy użyciu `-Version|--version` argumentu. Wersja musi być określona jako wersja z trzema częściami (na przykład `2.1.0` ). Jeśli nie zostanie podany, zostanie użyta `latest` wersja.

Skrypty instalacji nie aktualizują rejestru w systemie Windows. Po prostu pobieramy spakowane pliki binarne i skopiują je do folderu. Jeśli chcesz, aby wartości klucza rejestru były aktualizowane, użyj instalatorów platformy .NET Core.

## <a name="options"></a>Opcje

- **`-Architecture|--architecture <ARCHITECTURE>`**

  Architektura plików binarnych platformy .NET Core do zainstalowania. Możliwe wartości to `<auto>` , `amd64` , `x64` , `x86` , `arm64` i `arm` . Wartość domyślna to `<auto>` , która reprezentuje aktualnie uruchomioną architekturę systemu operacyjnego.

- **`-AzureFeed|--azure-feed`**

  Określa adres URL źródła danych platformy Azure do Instalatora. Zaleca się, aby nie zmieniać tej wartości. Wartość domyślna to `https://dotnetcli.azureedge.net/dotnet`.

- **`-Channel|--channel <CHANNEL>`**

  Określa kanał źródłowy instalacji. Możliwe wartości są następujące:

  - `Current`-Najnowsza wersja.
  - `LTS`-Długoterminowy kanał pomocy technicznej (większość aktualnie obsługiwanych wersji).
  - Dwuczęściowa wersja w formacie X. Y reprezentującym określoną wersję (na przykład `2.1` lub `3.0` ).
  - Nazwa gałęzi: na przykład `release/3.1.1xx` lub `master` (dla nocnych wydań). Użyj tej opcji, aby zainstalować wersję z kanału w wersji zapoznawczej. Użyj nazwy kanału wymienionej w [instalatorze i plikach binarnych](https://github.com/dotnet/core-sdk#installers-and-binaries).

  Wartość domyślna to `LTS`. Aby uzyskać więcej informacji na temat kanałów pomocy technicznej platformy .NET, zobacz stronę [zasady pomocy technicznej platformy .NET](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) .

- **`-DryRun|--dry-run`**

  W przypadku ustawienia skrypt nie wykona instalacji. Zamiast tego Wyświetla on wiersz polecenia, który służy do spójnej instalacji aktualnie żądanej wersji interfejs wiersza polecenia platformy .NET Core. Jeśli na przykład zostanie określona wersja `latest` , zostanie wyświetlony link z określoną wersją, aby można było użyć tego polecenia w sposób jednoznaczny w skrypcie kompilacji. Wyświetla również lokalizację pliku binarnego, jeśli wolisz zainstalować lub pobrać ją samodzielnie.

- **`-FeedCredential|--feed-credential`**

  Służy jako ciąg zapytania do dołączenia do kanału informacyjnego platformy Azure. Umożliwia on zmianę adresu URL w celu korzystania z niepublicznych kont magazynu obiektów BLOB.

- **`-Help|--help`**

  Drukuje pomoc dla skryptu.

- **`-InstallDir|--install-dir <DIRECTORY>`**

  Określa ścieżkę instalacji. Katalog zostanie utworzony, jeśli nie istnieje. Wartość domyślna to *%LocalAppData%\Microsoft\dotnet*. Pliki binarne są umieszczane bezpośrednio w tym katalogu.

- **`-JSonFile|--jsonfile <JSONFILE>`**

  Określa ścieżkę do pliku [Global. JSON](global-json.md) , który zostanie użyty do określenia wersji zestawu SDK. Plik *Global. JSON* musi mieć wartość `sdk:version` .

- **`-NoCdn|--no-cdn`**

  Wyłącza pobieranie z [usługi Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) i bezpośrednio używa niebuforowanego źródła danych.

- **`-NoPath|--no-path`**

  W przypadku ustawienia folder instalacyjny nie zostanie wyeksportowany do ścieżki bieżącej sesji. Domyślnie skrypt modyfikuje ścieżkę, co sprawia, że interfejs wiersza polecenia platformy .NET Core dostępne natychmiast po instalacji.

- **`-ProxyAddress`**

  W przypadku ustawienia Instalator używa serwera proxy podczas wykonywania żądań sieci Web. (Prawidłowe dla systemu Windows).

- **`ProxyUseDefaultCredentials`**

  Jeśli ta wartość jest ustawiona, Instalator użyje poświadczeń bieżącego użytkownika przy użyciu adresu serwera proxy. (Prawidłowe dla systemu Windows).

- **`-Runtime|--runtime <RUNTIME>`**

  Instaluje tylko udostępnione środowisko uruchomieniowe, a nie cały zestaw SDK. Możliwe wartości są następujące:

  - `dotnet`— `Microsoft.NETCore.App` udostępnione środowisko uruchomieniowe.
  - `aspnetcore`— `Microsoft.AspNetCore.App` udostępnione środowisko uruchomieniowe.
  - `windowsdesktop`— `Microsoft.WindowsDesktop.App` udostępnione środowisko uruchomieniowe.

- **`--runtime-id <RID>`**

  Określa [Identyfikator środowiska uruchomieniowego](../rid-catalog.md) , dla którego instalowane są narzędzia. Używany `linux-x64` dla przenośnego systemu Linux. (Prawidłowy tylko dla systemu Linux/macOS).

- **`-SharedRuntime|--shared-runtime`**

  > [!NOTE]
  > Ten parametr jest przestarzały i może zostać usunięty w przyszłej wersji skryptu. Zalecaną alternatywą jest `-Runtime|--runtime` opcja.

  Instaluje tylko udostępnione bity środowiska uruchomieniowego, a nie cały zestaw SDK. Ta opcja jest równoważna z określeniem `-Runtime|--runtime dotnet` .

- **`-SkipNonVersionedFiles|--skip-non-versioned-files`**

  Pomija Instalowanie plików nienależących do wersji, takich jak *dotnet. exe*, jeśli już istnieją.

- **`-UncachedFeed|--uncached-feed`**

  Umożliwia zmianę adresu URL dla niebuforowanego źródła danych używanego przez ten Instalator. Zaleca się, aby nie zmieniać tej wartości.

- **`-Verbose|--verbose`**

  Wyświetla informacje diagnostyczne.

- **`-Version|--version <VERSION>`**

  Reprezentuje konkretną wersję kompilacji. Możliwe wartości są następujące:

  - `latest`-Najnowsza kompilacja w kanale (używana z `-Channel` opcją).
  - `coherent`-Najnowsza spójna kompilacja na kanale; używa najnowszej stabilnej kombinacji pakietów (używanej z `-Channel` opcjami nazw gałęzi).
  - Wersja z trzech części w formacie X. Y. Z, reprezentująca konkretną wersję kompilacji; zastępuje `-Channel` opcję. Na przykład: `2.0.0-preview2-006120`.

  Jeśli nie zostanie określony, `-Version` wartością domyślną jest `latest` .

## <a name="examples"></a>Przykłady

- Zainstaluj najnowszą wersję długoterminową (LTS) w lokalizacji domyślnej:

  W systemie Windows:

  ```powershell
  ./dotnet-install.ps1 -Channel LTS
  ```

  macOS/Linux:

  ```bash
  ./dotnet-install.sh --channel LTS
  ```

- Zainstaluj najnowszą wersję z kanału 3,1 do określonej lokalizacji:

  W systemie Windows:

  ```powershell
  ./dotnet-install.ps1 -Channel 3.1 -InstallDir C:\cli
  ```

  macOS/Linux:

  ```bash
  ./dotnet-install.sh --channel 3.1 --install-dir ~/cli
  ```

- Zainstaluj wersję 3.0.0 udostępnionego środowiska uruchomieniowego:

  W systemie Windows:

  ```powershell
  ./dotnet-install.ps1 -Runtime dotnet -Version 3.0.0
  ```

  macOS/Linux:

  ```bash
  ./dotnet-install.sh --runtime dotnet --version 3.0.0
  ```

- Uzyskaj skrypt i Zainstaluj wersję 2.1.2 za firmowym serwerem proxy (tylko system Windows):

  ```powershell
  Invoke-WebRequest 'https://dot.net/v1/dotnet-install.ps1' -Proxy $env:HTTP_PROXY -ProxyUseDefaultCredentials -OutFile 'dotnet-install.ps1';
  ./dotnet-install.ps1 -InstallDir '~/.dotnet' -Version '2.1.2' -ProxyAddress $env:HTTP_PROXY -ProxyUseDefaultCredentials;
  ```

- Uzyskaj skrypt i zainstaluj interfejs wiersza polecenia platformy .NET Core przykłady jednoliniowe:

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

- [Wersje platformy .NET Core](https://github.com/dotnet/core/releases)
- [Środowisko uruchomieniowe programu .NET Core i archiwum pobierania zestawu SDK](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)

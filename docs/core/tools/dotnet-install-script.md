---
title: dotnet-install scripts
description: Więcej informacji na temat skryptów programu dotnet-Install w celu zainstalowania zestaw .NET Core SDK i udostępnionego środowiska uruchomieniowego.
ms.date: 01/23/2020
ms.openlocfilehash: 169991ac4cd24ccab90634ff265c3ae5b603f8e9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76734204"
---
# <a name="dotnet-install-scripts-reference"></a>dotnet — informacje o skryptach instalacji

## <a name="name"></a>Nazwa

`dotnet-install.ps1` | `dotnet-install.sh` — skrypt służący do instalowania zestaw .NET Core SDK i udostępnionego środowiska uruchomieniowego.

## <a name="synopsis"></a>Streszczenie

System Windows:

```powershell
dotnet-install.ps1 [-Channel] [-Version] [-JSonFile] [-InstallDir] [-Architecture]
    [-Runtime] [-DryRun] [-NoPath] [-Verbose] [-AzureFeed] [-UncachedFeed] [-NoCdn] [-FeedCredential]
    [-ProxyAddress] [-ProxyUseDefaultCredentials] [-SkipNonVersionedFiles] [-Help]
```

Linux/macOs:

```bash
dotnet-install.sh [--channel] [--version] [--jsonfile] [--install-dir] [--architecture]
    [--runtime] [--dry-run] [--no-path] [--verbose] [--azure-feed] [--uncached-feed] [--no-cdn] [--feed-credential]
    [--runtime-id] [--skip-non-versioned-files] [--help]
```

## <a name="description"></a>Opis

Skrypty `dotnet-install` są używane do przeprowadzania instalacji nieadministratora zestaw .NET Core SDK, która obejmuje narzędzia interfejs wiersza polecenia platformy .NET Core i udostępnione środowisko uruchomieniowe.

Zalecamy użycie stabilnej wersji skryptów:

- Bash (Linux/macOS): <https://dot.net/v1/dotnet-install.sh>
- PowerShell (Windows): <https://dot.net/v1/dotnet-install.ps1>

Główna użyteczność tych skryptów jest w scenariuszach automatyzacji i instalacjach nienależących do administratora. Istnieją dwa skrypty: jeden to skrypt programu PowerShell, który działa w systemie Windows, a drugi to skrypt bash, który działa w systemie Linux/macOS. Oba skrypty mają takie samo zachowanie. Skrypt bash odczytuje również przełączniki programu PowerShell, dzięki czemu można użyć przełączników programu PowerShell z skryptem w systemach Linux/macOS.

Skrypty instalacyjne pobierają plik ZIP/plik tar z kompilacji interfejsu wiersza polecenia, a następnie instalują go w lokalizacji domyślnej lub w lokalizacji określonej przez `-InstallDir|--install-dir`. Domyślnie skrypty instalacyjne pobierają zestaw SDK i instalują go. Jeśli chcesz uzyskać tylko udostępnione środowisko uruchomieniowe, określ argument `-Runtime|--runtime`.

Domyślnie skrypt dodaje lokalizację instalacji do $PATH bieżącej sesji. Zastąp to zachowanie domyślne, określając argument `-NoPath|--no-path`.

Przed uruchomieniem skryptu Zainstaluj wymagane [zależności](../install/dependencies.md).

Określoną wersję można zainstalować przy użyciu argumentu `-Version|--version`. Wersja musi być określona jako wersja z trzema częściami (na przykład `2.1.0`). Jeśli nie zostanie podany, zostanie użyta wersja `latest`.

## <a name="options"></a>Opcje

- **`-Channel|--channel <CHANNEL>`**

  Określa kanał źródłowy instalacji. Możliwe wartości to:

  - `Current` — Najnowsza wersja.
  - `LTS`-długoterminowy kanał pomocy technicznej (większość aktualnie obsługiwanych wersji).
  - Dwuczęściowa wersja w formacie X. Y reprezentującym określoną wersję (na przykład `2.1` lub `3.0`).
  - Nazwa rozgałęzienia: na przykład `release/3.1.1xx` lub `master` (dla nocnych wydań). Użyj tej opcji, aby zainstalować wersję z kanału w wersji zapoznawczej. Użyj nazwy kanału wymienionej w [instalatorze i plikach binarnych](https://github.com/dotnet/core-sdk#installers-and-binaries).

  Wartość domyślna to `LTS`. Aby uzyskać więcej informacji na temat kanałów pomocy technicznej platformy .NET, zobacz stronę [zasady pomocy technicznej platformy .NET](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) .

- **`-Version|--version <VERSION>`**

  Reprezentuje konkretną wersję kompilacji. Możliwe wartości to:

  - `latest` — Najnowsza kompilacja w kanale (używana z opcją `-Channel`).
  - `coherent`-Najnowsza spójna kompilacja na kanale; używa najnowszej stabilnej kombinacji pakietów (używanej z nazwą gałęzi `-Channel` opcjami).
  - Wersja z trzech części w formacie X. Y. Z, reprezentująca konkretną wersję kompilacji; zastępuje opcję `-Channel`. Na przykład: `2.0.0-preview2-006120`.

  Jeśli nie zostanie określony, `-Version` domyślnie `latest`.

- **`-JSonFile|--jsonfile <JSONFILE>`**

  Określa ścieżkę do pliku [Global. JSON](global-json.md) , który zostanie użyty do określenia wersji zestawu SDK. Plik *Global. JSON* musi mieć wartość `sdk:version`.

- **`-InstallDir|--install-dir <DIRECTORY>`**

  Określa ścieżkę instalacji. Katalog zostanie utworzony, jeśli nie istnieje. Wartość domyślna to *%LocalAppData%\Microsoft\dotnet*. Pliki binarne są umieszczane bezpośrednio w tym katalogu.

- **`-Architecture|--architecture <ARCHITECTURE>`**

  Architektura plików binarnych platformy .NET Core do zainstalowania. Możliwe wartości to `<auto>`, `amd64`, `x64`, `x86`, `arm64`i `arm`. Wartość domyślna to `<auto>`, która reprezentuje aktualnie uruchomioną architekturę systemu operacyjnego.

- **`-SharedRuntime|--shared-runtime`**

  > [!NOTE]
  > Ten parametr jest przestarzały i może zostać usunięty w przyszłej wersji skryptu. Zalecaną alternatywą jest opcja `-Runtime|--runtime`.

  Instaluje tylko udostępnione bity środowiska uruchomieniowego, a nie cały zestaw SDK. Ta opcja jest równoznaczna z określeniem `-Runtime|--runtime dotnet`.

- **`-Runtime|--runtime <RUNTIME>`**

  Instaluje tylko udostępnione środowisko uruchomieniowe, a nie cały zestaw SDK. Możliwe wartości to:

  - `dotnet` — `Microsoft.NETCore.App` udostępnionego środowiska uruchomieniowego.
  - `aspnetcore` — `Microsoft.AspNetCore.App` udostępnionego środowiska uruchomieniowego.
  - `windowsdesktop` — `Microsoft.WindowsDesktop.App` udostępnionego środowiska uruchomieniowego.

- **`-DryRun|--dry-run`**

  W przypadku ustawienia skrypt nie wykona instalacji. Zamiast tego Wyświetla on wiersz polecenia, który służy do spójnej instalacji aktualnie żądanej wersji interfejs wiersza polecenia platformy .NET Core. Jeśli na przykład zostanie określona wersja `latest`, zostanie wyświetlony link z określoną wersją, aby można było użyć tego polecenia w sposób jednoznaczny w skrypcie kompilacji. Wyświetla również lokalizację pliku binarnego, jeśli wolisz zainstalować lub pobrać ją samodzielnie.

- **`-NoPath|--no-path`**

  W przypadku ustawienia folder instalacyjny nie zostanie wyeksportowany do ścieżki bieżącej sesji. Domyślnie skrypt modyfikuje ścieżkę, co sprawia, że narzędzia interfejsu wiersza polecenia są dostępne natychmiast po instalacji.

- **`-Verbose|--verbose`**

  Wyświetla informacje diagnostyczne.

- **`-AzureFeed|--azure-feed`**

  Określa adres URL źródła danych platformy Azure do Instalatora. Zaleca się, aby nie zmieniać tej wartości. Wartość domyślna to `https://dotnetcli.azureedge.net/dotnet`.

- **`-UncachedFeed|--uncached-feed`**

  Umożliwia zmianę adresu URL dla niebuforowanego źródła danych używanego przez ten Instalator. Zaleca się, aby nie zmieniać tej wartości.

- **`-NoCdn|--no-cdn`**

  Wyłącza pobieranie z [usługi Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) i bezpośrednio używa niebuforowanego źródła danych.

- **`-FeedCredential|--feed-credential`**

  Służy jako ciąg zapytania do dołączenia do kanału informacyjnego platformy Azure. Umożliwia on zmianę adresu URL w celu korzystania z niepublicznych kont magazynu obiektów BLOB.

- **`--runtime-id`**

  Określa [Identyfikator środowiska uruchomieniowego](../rid-catalog.md) , dla którego instalowane są narzędzia. Użyj `linux-x64` dla przenośnego systemu Linux. (Prawidłowy tylko dla systemu Linux/macOS)

- **`-ProxyAddress`**

  W przypadku ustawienia Instalator używa serwera proxy podczas wykonywania żądań sieci Web. (Prawidłowe dla systemu Windows)

- **`ProxyUseDefaultCredentials`**

  Jeśli ta wartość jest ustawiona, Instalator użyje poświadczeń bieżącego użytkownika przy użyciu adresu serwera proxy. (Prawidłowe dla systemu Windows)

- **`-SkipNonVersionedFiles|--skip-non-versioned-files`**

  Pomija Instalowanie plików nienależących do wersji, takich jak *dotnet. exe*, jeśli już istnieją.

- **`-Help|--help`**

  Drukuje pomoc dla skryptu.

## <a name="examples"></a>Przykłady

- Zainstaluj najnowszą wersję długoterminową (LTS) w lokalizacji domyślnej:

  System Windows:

  ```powershell
  ./dotnet-install.ps1 -Channel LTS
  ```

  macOS/Linux:

  ```bash
  ./dotnet-install.sh --channel LTS
  ```

- Zainstaluj najnowszą wersję z kanału 3,1 do określonej lokalizacji:

  System Windows:

  ```powershell
  ./dotnet-install.ps1 -Channel 3.1 -InstallDir C:\cli
  ```

  macOS/Linux:

  ```bash
  ./dotnet-install.sh --channel 3.1 --install-dir ~/cli
  ```

- Zainstaluj wersję 3.0.0 udostępnionego środowiska uruchomieniowego:

  System Windows:

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

  System Windows:

  ```powershell
  # Run a separate PowerShell process because the script calls exit, so it will end the current PowerShell session.
  &powershell -NoProfile -ExecutionPolicy unrestricted -Command "[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; &([scriptblock]::Create((Invoke-WebRequest -UseBasicParsing 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"
  ```

  macOS/Linux:

  ```bash
  curl -ssl https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>
  ```

## <a name="see-also"></a>Zobacz także

- [Wersje platformy .NET Core](https://github.com/dotnet/core/releases)
- [Środowisko uruchomieniowe programu .NET Core i archiwum pobierania zestawu SDK](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)

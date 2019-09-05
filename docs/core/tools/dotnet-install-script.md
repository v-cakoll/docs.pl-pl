---
title: dotnet-install scripts
description: Dowiedz się więcej na temat skryptów programu dotnet-install, aby zainstalować narzędzia interfejs wiersza polecenia platformy .NET Core i udostępnione środowisko uruchomieniowe.
ms.date: 01/16/2019
ms.openlocfilehash: ed1a3341e678b405ae4aca35e3b49ada89eb069a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253899"
---
# <a name="dotnet-install-scripts-reference"></a>dotnet — informacje o skryptach instalacji

## <a name="name"></a>Nazwa

`dotnet-install.ps1` | `dotnet-install.sh`-Skrypt służący do instalowania narzędzi interfejs wiersza polecenia platformy .NET Core i udostępnionego środowiska uruchomieniowego.

## <a name="synopsis"></a>Streszczenie

W systemie Windows:

`dotnet-install.ps1 [-Channel] [-Version] [-InstallDir] [-Architecture] [-SharedRuntime] [-Runtime] [-DryRun] [-NoPath] [-Verbose] [-AzureFeed] [-UncachedFeed] [-NoCdn] [-FeedCredential] [-ProxyAddress] [-ProxyUseDefaultCredentials] [-SkipNonVersionedFiles] [-Help]`

macOS/Linux:

`dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture] [--runtime] [--dry-run] [--no-path] [--verbose] [--azure-feed] [--uncached-feed] [--no-cdn] [--feed-credential] [--runtime-id] [--skip-non-versioned-files] [--help]`

## <a name="description"></a>Opis

`dotnet-install` Skrypty są używane do przeprowadzania instalacji nieadministratora zestaw .NET Core SDK, która obejmuje narzędzia interfejs wiersza polecenia platformy .NET Core i udostępnione środowisko uruchomieniowe.

Zalecamy korzystanie z stabilnej wersji hostowanej w [głównej witrynie sieci Web platformy .NET Core](https://dot.net). Bezpośrednie ścieżki do skryptów są następujące:

- <https://dot.net/v1/dotnet-install.sh>(bash, UNIX)
- <https://dot.net/v1/dotnet-install.ps1>(Program PowerShell, system Windows)

Główna użyteczność tych skryptów jest w scenariuszach automatyzacji i instalacjach nienależących do administratora. Istnieją dwa skrypty: jeden to skrypt programu PowerShell, który działa w systemie Windows, a drugi to skrypt bash, który działa w systemie Linux/macOS. Oba skrypty mają takie samo zachowanie. Skrypt bash odczytuje również przełączniki programu PowerShell, dzięki czemu można użyć przełączników programu PowerShell z skryptem w systemach Linux/macOS.

Skrypty instalacyjne pobierają plik ZIP/plik tar z kompilacji interfejsu wiersza polecenia, a następnie instalują go w lokalizacji domyślnej lub w lokalizacji określonej przez `-InstallDir|--install-dir`. Domyślnie skrypty instalacyjne pobierają zestaw SDK i instalują go. Jeśli chcesz uzyskać tylko udostępnione środowisko uruchomieniowe, określ `--runtime` argument.

Domyślnie skrypt dodaje lokalizację instalacji do $PATH bieżącej sesji. Zastąp to zachowanie domyślne, określając `--no-path` argument.

Przed uruchomieniem skryptu Zainstaluj wymagane [zależności](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).

Można zainstalować określoną wersję przy użyciu `--version` argumentu. Wersja musi być określona jako wersja z trzema częściami (na przykład 1.0.0-13232). Jeśli nie zostanie podany, zostanie użyta `latest` wersja.

## <a name="options"></a>Opcje

- **`-Channel <CHANNEL>`**

  Określa kanał źródłowy instalacji. Możliwe wartości to:

  - `Current`-Najnowsza wersja.
  - `LTS`-Długoterminowy kanał pomocy technicznej (większość aktualnie obsługiwanych wersji).
  - Dwuczęściowa wersja w formacie X. Y reprezentującym określoną wersję (na przykład `2.0` lub `1.0`).
  - Nazwa rozgałęzienia. Na przykład `release/2.0.0` `release/2.0.0-preview2`,, lub `master` (dla nocnych wydań).

  Wartość domyślna to `LTS`. Aby uzyskać więcej informacji na temat kanałów pomocy technicznej platformy .NET, zobacz stronę [zasady pomocy technicznej platformy .NET](https://www.microsoft.com/net/platform/support-policy#dotnet-core) .

- **`-Version <VERSION>`**

  Reprezentuje konkretną wersję kompilacji. Możliwe wartości to:

  - `latest`-Najnowsza kompilacja w kanale (używana z `-Channel` opcją).
  - `coherent`-Najnowsza spójna kompilacja na kanale; używa najnowszej stabilnej kombinacji pakietów (używanej z opcjami nazw `-Channel` gałęzi).
  - Wersja z trzech części w formacie X. Y. Z, reprezentująca konkretną wersję kompilacji; `-Channel` zastępuje opcję. Na przykład: `2.0.0-preview2-006120`.

  Jeśli nie zostanie określony `-Version` , `latest`wartością domyślną jest.

- **`-InstallDir <DIRECTORY>`**

  Określa ścieżkę instalacji. Katalog zostanie utworzony, jeśli nie istnieje. Wartość domyślna to *%LocalAppData%\Microsoft\dotnet*. Pliki binarne są umieszczane bezpośrednio w tym katalogu.

- **`-Architecture <ARCHITECTURE>`**

  Architektura plików binarnych platformy .NET Core do zainstalowania. Możliwe wartości to `<auto>`, `amd64`, `x64`, `x86` ,i`arm`. `arm64` Wartość domyślna to `<auto>`, która reprezentuje aktualnie uruchomioną architekturę systemu operacyjnego.

- **`-SharedRuntime`**

  > [!NOTE]
  > Ten parametr jest przestarzały i może zostać usunięty w przyszłej wersji skryptu. Zalecaną alternatywą jest `Runtime` opcja.

  Instaluje tylko udostępnione bity środowiska uruchomieniowego, a nie cały zestaw SDK. Jest to równoważne określeniu `-Runtime dotnet`.

- **`-Runtime <RUNTIME>`**

  Instaluje tylko udostępnione środowisko uruchomieniowe, a nie cały zestaw SDK. Możliwe wartości to:

  - `dotnet``Microsoft.NETCore.App` — udostępnione środowisko uruchomieniowe.
  - `aspnetcore``Microsoft.AspNetCore.App` — udostępnione środowisko uruchomieniowe.

- **`-DryRun`**

  W przypadku ustawienia skrypt nie wykona instalacji. Zamiast tego Wyświetla on wiersz polecenia, który służy do spójnej instalacji aktualnie żądanej wersji interfejs wiersza polecenia platformy .NET Core. Jeśli na przykład zostanie określona wersja `latest`, zostanie wyświetlony link z określoną wersją, aby można było użyć tego polecenia w sposób jednoznaczny w skrypcie kompilacji. Wyświetla również lokalizację pliku binarnego, jeśli wolisz zainstalować lub pobrać ją samodzielnie.

- **`-NoPath`**

  W przypadku ustawienia folder instalacyjny nie zostanie wyeksportowany do ścieżki bieżącej sesji. Domyślnie skrypt modyfikuje ścieżkę, co sprawia, że narzędzia interfejsu wiersza polecenia są dostępne natychmiast po instalacji.

- **`-Verbose`**

  Wyświetla informacje diagnostyczne.

- **`-AzureFeed`**

  Określa adres URL źródła danych platformy Azure do Instalatora. Zaleca się, aby nie zmieniać tej wartości. Wartość domyślna to `https://dotnetcli.azureedge.net/dotnet`.

- **`-UncachedFeed`**

  Umożliwia zmianę adresu URL dla niebuforowanego źródła danych używanego przez ten Instalator. Zaleca się, aby nie zmieniać tej wartości.

- **`-NoCdn`**

  Wyłącza pobieranie z [usługi Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) i bezpośrednio używa niebuforowanego źródła danych.

- **`-FeedCredential`**

  Służy jako ciąg zapytania do dołączenia do kanału informacyjnego platformy Azure. Umożliwia on zmianę adresu URL w celu korzystania z niepublicznych kont magazynu obiektów BLOB.

- **`-ProxyAddress`**

  W przypadku ustawienia Instalator używa serwera proxy podczas wykonywania żądań sieci Web. (Prawidłowe dla systemu Windows)

- **`ProxyUseDefaultCredentials`**

  Jeśli ta wartość jest ustawiona, Instalator użyje poświadczeń bieżącego użytkownika przy użyciu adresu serwera proxy. (Prawidłowe dla systemu Windows)

- **`-SkipNonVersionedFiles`**

  Pomija Instalowanie plików nienależących do wersji, takich jak *dotnet. exe*, jeśli już istnieją.

- **`-Help`**

  Drukuje pomoc dla skryptu.

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

- Zainstaluj najnowszą wersję z kanału 2,0 do określonej lokalizacji:

  W systemie Windows:

  ```powershell
  ./dotnet-install.ps1 -Channel 2.0 -InstallDir C:\cli
  ```

  macOS/Linux:

  ```bash
  ./dotnet-install.sh --channel 2.0 --install-dir ~/cli
  ```

- Zainstaluj wersję 1.1.0 udostępnionego środowiska uruchomieniowego:

  W systemie Windows:

  ```powershell
  ./dotnet-install.ps1 -Runtime dotnet -Version 1.1.0
  ```

  macOS/Linux:

  ```bash
  ./dotnet-install.sh --runtime dotnet --version 1.1.0
  ```

- Uzyskaj skrypt i Zainstaluj wersję 2.1.2 za firmowym serwerem proxy (tylko system Windows):

  ```powershell
  Invoke-WebRequest 'https://dot.net/v1/dotnet-install.ps1' -Proxy $env:HTTP_PROXY -ProxyUseDefaultCredentials -OutFile 'dotnet-install.ps1';
  ./dotnet-install.ps1 -InstallDir '~/.dotnet' -Version '2.1.2' -ProxyAddress $env:HTTP_PROXY -ProxyUseDefaultCredentials;
  ```

- Uzyskaj skrypt i zainstaluj interfejs wiersza polecenia platformy .NET Core przykłady jednoliniowe:

  W systemie Windows:

  ```powershell
  @powershell -NoProfile -ExecutionPolicy unrestricted -Command "[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; &([scriptblock]::Create((Invoke-WebRequest -UseBasicParsing 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"
  ```

  macOS/Linux:

  ```bash
  curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>
  ```

## <a name="see-also"></a>Zobacz także

- [Wersje platformy .NET Core](https://github.com/dotnet/core/releases)
- [Środowisko uruchomieniowe programu .NET Core i archiwum pobierania zestawu SDK](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)

---
title: skrypty instalacji DotNet
description: Więcej informacji na temat skryptów instalacji dotnet do zainstalowania narzędzi interfejsu wiersza polecenia platformy .NET Core i udostępnionego środowiska uruchomieniowego.
ms.date: 11/15/2018
ms.openlocfilehash: 0f565fee3e4ff4bec65bd196f635e9e9601485c2
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53148333"
---
# <a name="dotnet-install-scripts-reference"></a>Dokumentacja skryptów instalacji DotNet

## <a name="name"></a>Nazwa

`dotnet-install.ps1` | `dotnet-install.sh` — Skrypt używany do instalacji narzędzi interfejsu wiersza polecenia platformy .NET Core i udostępnionego środowiska uruchomieniowego.

## <a name="synopsis"></a>Streszczenie

W systemie Windows:

`dotnet-install.ps1 [-Channel] [-Version] [-InstallDir] [-Architecture] [-SharedRuntime] [-Runtime] [-DryRun] [-NoPath] [-Verbose] [-AzureFeed] [-UncachedFeed] [-NoCdn] [-FeedCredential] [-ProxyAddress] [-ProxyUseDefaultCredentials] [-SkipNonVersionedFiles] [-Help]`

System macOS/Linux:

`dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture] [--runtime] [--dry-run] [--no-path] [--verbose] [--azure-feed] [--uncached-feed] [--no-cdn] [--feed-credential] [--runtime-id] [--skip-non-versioned-files] [--help]`

## <a name="description"></a>Opis

`dotnet-install` Skrypty są używane do przeprowadzenia instalacji bez uprawnień administratora programu .NET Core SDK, w tym narzędzi interfejsu wiersza polecenia platformy .NET Core i udostępnionego środowiska uruchomieniowego.

Zalecane jest użycie stabilną wersję, która jest hostowana na [głównej witryny internetowej platformy .NET Core](https://dot.net). Bezpośrednie ścieżki do skryptów są:

* <https://dot.net/v1/dotnet-install.sh> (powłoki bash, UNIX)
* <https://dot.net/v1/dotnet-install.ps1> (Program Powershell, Windows)

Główne użyteczność tych skryptów znajduje się w scenariuszach automatyzacji oraz przed instalacjami bez uprawnień administratora. Istnieją dwa skrypty: jeden z nich jest skrypt programu PowerShell, który działa na Windows, a drugi to skrypt powłoki bash, który działa w systemie Linux/macOS. Zarówno skryptów mają takie samo zachowanie. Skrypt powłoki bash odczytuje również przełączników programu PowerShell, aby można było używać przełączników programu PowerShell przy użyciu skryptu w systemach Linux/macOS.

Skrypty instalacji Pobierz plik ZIP/pliku tar z spadnie kompilacji interfejsu wiersza polecenia i przejdź do instalacji w lokalizacji domyślnej lub w lokalizacji określonej przez `-InstallDir|--install-dir`. Domyślnie skrypty instalacyjne Pobierz zestaw SDK i zainstaluj go. Jeśli chcesz uzyskać tylko udostępnionego środowiska uruchomieniowego, należy określić `--shared-runtime` argumentu.

Domyślnie skrypt ten dodaje lokalizacji instalacji do $PATH dla bieżącej sesji. To zachowanie domyślne można przesłonić, określając `--no-path` argumentu.

Przed uruchomieniem skryptu, zainstalować wymagane [zależności](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).

Można to zrobić przy użyciu określonej wersji `--version` argumentu. Wersja muszą być określone jako (na przykład 1.0.0-13232) w wersji trzyczęściowej serii. Jeśli nie zostanie podana, używa `latest` wersji.

## <a name="options"></a>Opcje

* **`-Channel <CHANNEL>`**

  Określa identyfikator kanału źródła dla instalacji. Możliwe wartości to:

  * `Current` — Najnowsza wersja.
  * `LTS` — Długoterminowe kanału pomocy technicznej (Najnowsza wersja obsługiwane).
  * Wersja legalną dwuczęściową w formacie X.Y reprezentujący określonej wersji (na przykład `2.0` lub `1.0`).
  * Nazwa gałęzi. Na przykład `release/2.0.0`, `release/2.0.0-preview2`, lub `master` (w przypadku nocne wydania).

  Wartość domyślna to `LTS`. Aby uzyskać więcej informacji dotyczących kanałów pomocy technicznej platformy .NET, zobacz [.NET obsługuje zasady](https://www.microsoft.com/net/platform/support-policy#dotnet-core) strony.

* **`-Version <VERSION>`**

  Reprezentuje wersję konkretnej kompilacji. Możliwe wartości to:

  * `latest` -Najnowszych kompilacji w kanale (używany z `-Channel` opcji).
  * `coherent` — Najnowsza wersja spójnego kompilacji na kanał. używa kombinacji najnowszy stabilny pakiet (używany przy użyciu gałęzi o nazwie `-Channel` opcje).
  * Trzyczęściowej wersję w formacie X.Y.Z reprezentującą określony kompilacji wersji; zastępuje `-Channel` opcji. Na przykład: `2.0.0-preview2-006120`.

  Jeśli nie zostanie określony, `-Version` wartość domyślna to `latest`.

* **`-InstallDir <DIRECTORY>`**

  Określa ścieżkę instalacji. Katalog jest tworzony, jeśli nie istnieje. Wartość domyślna to *%LocalAppData%\Microsoft\dotnet*. Pliki binarne są umieszczane bezpośrednio w tym katalogu.

* **`-Architecture <ARCHITECTURE>`**

  Architektura platformy .NET Core pliki binarne do zainstalowania. Możliwe wartości to `auto`, `x64`, i `x86`. Wartość domyślna to `auto`, który reprezentuje aktualnie uruchomionych architektury systemu operacyjnego.

* **`-SharedRuntime`**

  > [!NOTE]
  > Ten parametr jest przestarzały i może zostać usunięty w przyszłych wersjach skryptu. Zalecaną alternatywą jest `Runtime` opcji.

  Instaluje tylko bity udostępnionego środowiska uruchomieniowego, a nie całego zestawu SDK. To jest równoznaczne z użyciem `-Runtime dotnet`.

* **`-Runtime <RUNTIME>`**

  Instaluje tylko udostępnionego środowiska uruchomieniowego, nie cały zestaw SDK. Możliwe wartości to:

  * `dotnet` - `Microsoft.NETCore.App` udostępnionego środowiska uruchomieniowego.
  * `aspnetcore` - `Microsoft.AspNetCore.App` udostępnionego środowiska uruchomieniowego.

* **`-DryRun`**

  Jeśli nie będzie ustawiona, skrypt przeprowadzić instalację. Zamiast tego wyświetla wiersz polecenia na potrzeby spójnego zainstalować obecnie żądana wersja interfejsu wiersza polecenia platformy .NET Core. Na przykład, jeśli określona wersja `latest`, wyświetla łącze do określonej wersji, aby to polecenie może być używane w sposób deterministyczny w skrypcie kompilacji. Lokalizacja tego pliku binarnego również wyświetlana, jeśli wolisz zainstalować lub pobrać go samodzielnie.

* **`-NoPath`**

  Jeśli zestawu i folderu instalacji nie jest eksportowany do ścieżki dla bieżącej sesji. Domyślnie skrypt modyfikuje ścieżki, która udostępnia natychmiast po przeprowadzeniu instalacji narzędzi interfejsu wiersza polecenia.

* **`-Verbose`**

  Wyświetla informacje diagnostyczne.

* **`-AzureFeed`**

  Określa, że adres URL dla platformy Azure, źródła danych do Instalatora. Zaleca się, że nie możesz zmienić tę wartość. Wartość domyślna to `https://dotnetcli.azureedge.net/dotnet`.

* **`-UncachedFeed`**

  Umożliwia, zmiana adresu URL dla źródła danych bez buforowania używane przez tego Instalatora. Zaleca się, że nie możesz zmienić tę wartość.

* **`-NoCdn`**

  Wyłącza pobierania z [Azure Content Delivery Network (CDN)](https://docs.microsoft.com/azure/cdn/cdn-overview) i korzysta z bezpośrednio bez buforowania źródła danych.

* **`-FeedCredential`**

  Używane jako ciąg zapytania do dołączenia do platformy Azure, źródła danych. Umożliwia ona, zmiana adresu URL, aby użyć konta magazynu obiektów blob bez publicznego.

* **`-ProxyAddress`**

  Jeśli zestaw, Instalator używa serwera proxy w przypadku wysyłania żądań sieci web. (Ta funkcja jest prawidłowa tylko dla Windows)

* **`ProxyUseDefaultCredentials`**

  Jeśli zestaw, Instalator używa poświadczeń bieżącego użytkownika, korzystając z adresu serwera proxy. (Ta funkcja jest prawidłowa tylko dla Windows)

* **`-SkipNonVersionedFiles`**

  Pomija instalowania innych wersji plików, takich jak *dotnet.exe*, jeśli już istnieje.

* **`-Help`**

  Drukuje pomoc dotyczącą skryptu.

## <a name="examples"></a>Przykłady

* W domyślnej lokalizacji, należy zainstalować najnowsze długoterminowe obsługiwaną wersję (LTS):

  W systemie Windows:

  ```powershell
  ./dotnet-install.ps1 -Channel LTS
  ```

  System macOS/Linux:

  ```bash
  ./dotnet-install.sh --channel LTS
  ```

* Zainstaluj najnowszą wersję z kanału 2.0 do określonej lokalizacji:

  W systemie Windows:

  ```powershell
  ./dotnet-install.ps1 -Channel 2.0 -InstallDir C:\cli
  ```

  System macOS/Linux:

  ```bash
  ./dotnet-install.sh --channel 2.0 --install-dir ~/cli
  ```

* Zainstaluj 1.1.0 wersji udostępnionego środowiska uruchomieniowego:

  W systemie Windows:

  ```powershell
  ./dotnet-install.ps1 -SharedRuntime -Version 1.1.0
  ```

  System macOS/Linux:

  ```bash
  ./dotnet-install.sh --shared-runtime --version 1.1.0
  ```

* Skrypt należy uzyskać i zainstalować 2.1.2 wersja za firmowym serwerem proxy (tylko Windows):

  ```powershell
  Invoke-WebRequest 'https://dot.net/v1/dotnet-install.ps1' -Proxy $env:HTTP_PROXY -ProxyUseDefaultCredentials -OutFile 'dotnet-install.ps1';
  ./dotnet-install.ps1 -InstallDir '~/.dotnet' -Version '2.1.2' -ProxyAddress $env:HTTP_PROXY -ProxyUseDefaultCredentials;
  ```

* Uzyskać skrypt i zainstaluj interfejs wiersza polecenia platformy .NET Core one-liner przykłady:

  W systemie Windows:

  ```powershell
  @powershell -NoProfile -ExecutionPolicy unrestricted -Command "[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; &([scriptblock]::Create((Invoke-WebRequest -useb 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"
  ```

  System macOS/Linux:

  ```bash
  curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>
  ```

## <a name="see-also"></a>Zobacz także

* [Wersje platformy .NET core](https://github.com/dotnet/core/releases)
* [Środowisko uruchomieniowe programu .NET core i zestawu SDK Pobierz archiwum](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)

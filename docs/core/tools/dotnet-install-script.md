---
title: skrypty instalacji DotNet
description: Więcej informacji na temat skryptów instalacji dotnet do zainstalowania narzędzi interfejsu wiersza polecenia platformy .NET Core i udostępnionego środowiska uruchomieniowego.
author: blackdwarf
ms.author: mairaw
ms.date: 09/11/2017
ms.openlocfilehash: 8d1c6ebb30bd45575bb61206799c9c3e5c47ff0c
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45527899"
---
# <a name="dotnet-install-scripts-reference"></a>Dokumentacja skryptów instalacji DotNet

## <a name="name"></a>Nazwa

`dotnet-install.ps1` | `dotnet-install.sh` — Skrypt używany do instalacji narzędzi interfejsu wiersza polecenia platformy .NET Core i udostępnionego środowiska uruchomieniowego.

## <a name="synopsis"></a>Streszczenie

Windows:

`dotnet-install.ps1 [-Channel] [-Version] [-InstallDir] [-Architecture] [-SharedRuntime] [-DryRun] [-NoPath] [-AzureFeed] [-ProxyAddress] [--Verbose] [--Help]`

System macOS/Linux:

`dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture] [--shared-runtime] [--dry-run] [--no-path] [--azure-feed] [--verbose] [--help]`

## <a name="description"></a>Opis

`dotnet-install` Skrypty są używane do przeprowadzenia instalacji bez uprawnień administratora programu .NET Core SDK, w tym narzędzi interfejsu wiersza polecenia platformy .NET Core i udostępnionego środowiska uruchomieniowego.

Zalecane jest użycie stabilną wersję, która jest hostowana na [głównej witryny internetowej platformy .NET Core](https://dot.net). Bezpośrednie ścieżki do skryptów są:

* https://dot.net/v1/dotnet-install.sh (powłoki bash, UNIX)
* https://dot.net/v1/dotnet-install.ps1 (Program Powershell, Windows)

Główne użyteczność tych skryptów znajduje się w scenariuszach automatyzacji oraz przed instalacjami bez uprawnień administratora. Istnieją dwa skrypty: jeden z nich jest skrypt programu PowerShell, który działa na Windows. Skrypt programu jest skrypt powłoki bash, który działa w systemie Linux/macOS. Zarówno skryptów mają takie samo zachowanie. Skrypt powłoki bash odczytuje również przełączników programu PowerShell, aby można było używać przełączników programu PowerShell przy użyciu skryptu w systemach Linux/macOS.

Skrypty instalacji Pobierz plik ZIP/pliku tar z spadnie kompilacji interfejsu wiersza polecenia i przejdź do instalacji w lokalizacji domyślnej lub w lokalizacji określonej przez `-InstallDir|--install-dir`. Domyślnie skrypty instalacyjne Pobierz zestaw SDK i zainstaluj go. Jeśli chcesz uzyskać tylko udostępnionego środowiska uruchomieniowego, należy określić `--shared-runtime` argumentu.

Domyślnie skrypt ten dodaje lokalizacji instalacji do $PATH dla bieżącej sesji. To zachowanie domyślne można przesłonić, określając `--no-path` argumentu.

Przed uruchomieniem skryptu, zainstalować wymagane [zależności](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).

Można to zrobić przy użyciu określonej wersji `--version` argumentu. Wersja muszą być określone jako część 3 wersji (na przykład 1.0.0-13232). Jeśli argument jest pominięty, zostanie użyta `latest` wersji.

## <a name="options"></a>Opcje

`-Channel <CHANNEL>`

Określa identyfikator kanału źródła dla instalacji. Możliwe wartości to:

- `Current` -Bieżąca wersja
- `LTS` — Długoterminowe kanału pomocy technicznej (bieżąca wersja obsługiwane)
- Wersja legalną dwuczęściową w formacie X.Y reprezentujący określonej wersji (na przykład `2.0` lub `1.0`)
- Nazwa gałęzi [na przykład `release/2.0.0`, `release/2.0.0-preview2`, lub `master` uzyskać najnowsze informacje przedstawią `master` gałęzi ("jest edge" nocne wydania)]

Wartość domyślna to `LTS`. Aby uzyskać więcej informacji dotyczących kanałów pomocy technicznej platformy .NET, zobacz [.NET Core Cykl wsparcia technicznego produktów](https://www.microsoft.com/net/core/support) tematu.

`-Version <VERSION>`

Reprezentuje wersję konkretnej kompilacji. Możliwe wartości to:

- `latest` -Najnowszych kompilacji w kanale (używany z `-Channel` opcja)
- `coherent` — Najnowsza wersja spójnego kompilacji na kanał. używa kombinacji najnowszy stabilny pakiet (używany przy użyciu gałęzi o nazwie `-Channel` opcje)
- Trzyczęściowej wersję w formacie X.Y.Z reprezentującą określony kompilacji wersji; zastępuje `-Channel` opcji. Na przykład: `2.0.0-preview2-006120`

W przypadku pominięcia `-Version` wartość domyślna to `latest`.

`-InstallDir <DIRECTORY>`

Określa ścieżkę instalacji. Katalog jest tworzony, jeśli nie istnieje. Wartość domyślna to *% LocalAppData %\.dotnet*. Należy pamiętać, że pliki binarne są umieszczane bezpośrednio w katalogu.

`-Architecture <ARCHITECTURE>`

Architektura platformy .NET Core pliki binarne do zainstalowania. Możliwe wartości to `auto`, `x64`, i `x86`. Wartość domyślna to `auto`, który reprezentuje aktualnie uruchomionych architektury systemu operacyjnego.

`-SharedRuntime`

Jeśli ustawiona, ten przełącznik ogranicza instalacji udostępnionego środowiska uruchomieniowego. Cały zestaw SDK nie jest zainstalowany.

`-DryRun`

Jeśli nie będzie ustawiona, skrypt przeprowadzenia instalacji; ale zamiast tego wyświetla wiersz polecenia na potrzeby spójnego zainstalować obecnie żądana wersja interfejsu wiersza polecenia platformy .NET Core. Na przykład w przypadku określenia wersji `latest`, wyświetla łącze do określonej wersji, aby to polecenie może być używane w sposób deterministyczny w skrypcie kompilacji. Lokalizacja tego pliku binarnego również wyświetlana, jeśli wolisz zainstalować lub pobrać go samodzielnie.

`-NoPath`

Jeśli ustawiona, prefiks/installdir nie są eksportowane do ścieżki dla bieżącej sesji. Domyślnie skrypt zostanie zmodyfikowany ścieżki, która udostępnia natychmiast po przeprowadzeniu instalacji narzędzi interfejsu wiersza polecenia.

`-AzureFeed`

Określa, że adres URL dla platformy Azure, źródła danych do Instalatora. Nie jest zalecane, aby zmienić tę wartość. Wartość domyślna to `https://dotnetcli.azureedge.net/dotnet`.

`-ProxyAddress`

Jeśli zestaw, Instalator używa serwera proxy w przypadku wysyłania żądań sieci web. (Ta funkcja jest prawidłowa tylko dla Windows)

`--verbose`

Wyświetlanie informacji diagnostycznych.

`--help`

Drukuje pomoc dotyczącą skryptu.

## <a name="examples"></a>Przykłady

W domyślnej lokalizacji, należy zainstalować najnowsze długoterminowe obsługiwaną wersję (LTS):

Windows:

`./dotnet-install.ps1 -Channel LTS`

System macOS/Linux:

`./dotnet-install.sh --channel LTS`

Zainstaluj najnowszą wersję z kanału 2.0 do określonej lokalizacji:

Windows:

`./dotnet-install.ps1 -Channel 2.0 -InstallDir C:\cli`

System macOS/Linux:

`./dotnet-install.sh --channel 2.0 --install-dir ~/cli`

Zainstaluj 1.1.0 wersji udostępnionego środowiska uruchomieniowego:

Windows:

`./dotnet-install.ps1 -SharedRuntime -Version 1.1.0`

System macOS/Linux:

`./dotnet-install.sh --shared-runtime --version 1.1.0`

Uzyskać skrypt i zainstaluj interfejs wiersza polecenia platformy .NET Core one-liner przykłady:

Windows:

`@powershell -NoProfile -ExecutionPolicy unrestricted -Command "[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12; &([scriptblock]::Create((Invoke-WebRequest -useb 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"`

System macOS/Linux:

`curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>`

## <a name="see-also"></a>Zobacz także

* [Wersje platformy .NET core](https://github.com/dotnet/core/releases)
* [Środowisko uruchomieniowe programu .NET core i zestawu SDK Pobierz archiwum](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)

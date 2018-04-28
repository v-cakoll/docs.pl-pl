---
title: skryptów instalacji DotNet
description: Więcej informacji na temat skryptów instalacji dotnet instalacji narzędzi interfejsu wiersza polecenia platformy .NET Core i udostępnionych środowiska uruchomieniowego.
author: blackdwarf
ms.author: mairaw
ms.date: 09/11/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: 96336df087ea2ad01584010f0715ad31e079b663
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-install-scripts-reference"></a>odwołania skryptów instalacji DotNet

## <a name="name"></a>Nazwa

`dotnet-install.ps1` | `dotnet-install.sh` -Skrypt użyty do zainstalowania narzędzi interfejsu wiersza polecenia platformy .NET Core i udostępnionych środowiska uruchomieniowego.

## <a name="synopsis"></a>Streszczenie

System Windows:

`dotnet-install.ps1 [-Channel] [-Version] [-InstallDir] [-Architecture] [-SharedRuntime] [-DryRun] [-NoPath] [-AzureFeed] [-ProxyAddress] [--Verbose] [--Help]`

System macOS/Linux:

`dotnet-install.sh [--channel] [--version] [--install-dir] [--architecture] [--shared-runtime] [--dry-run] [--no-path] [--azure-feed] [--verbose] [--help]`

## <a name="description"></a>Opis

`dotnet-install` Skrypty są używane do wykonywania instalacji programu .NET Core SDK, w tym narzędzi interfejsu wiersza polecenia platformy .NET Core i udostępnionych środowiska wykonawczego o bez uprawnień administratora.

Zalecane jest użycie stabilną wersję, która znajduje się na [.NET Core głównym witryny sieci Web](https://dot.net). Bezpośrednie ścieżki do skryptów są:

* https://dot.net/v1/dotnet-install.sh (bash, UNIX)
* https://dot.net/v1/dotnet-install.ps1 (System Windows Powershell)

Jest głównym przydatność te skrypty w scenariuszach automatyzacji i instalacji bez uprawnień administratora. Istnieją dwa skrypty: jedna jest skrypt programu PowerShell, która działa w systemie Windows. Inne skryptu to skrypt bash, który działa na systemie Linux/macOS. Zarówno skryptów ma takie samo zachowanie. Skrypt bash odczytuje również przełączników programu PowerShell, dzięki czemu można używać przełączników programu PowerShell przy użyciu skryptu w systemach Linux/macOS. 

Skrypty instalacyjne Pobierz plik ZIP/tarball z porzucania kompilacji interfejsu wiersza polecenia i przejdź do instalacji w lokalizacji domyślnej lub w lokalizacji określonej przez `-InstallDir|--install-dir`. Domyślnie skrypty instalacyjne Pobierz zestaw SDK i zainstaluj go. Jeśli chcesz tylko uzyskać udostępnionego środowiska uruchomieniowego, określ `--shared-runtime` argumentu. 

Domyślnie skrypt dodaje lokalizacji instalacji do $PATH dla bieżącej sesji. Zmienić to zachowanie domyślne, określając `--no-path` argumentu. 

Przed uruchomieniem skryptu, zainstalować wymagane [zależności](https://github.com/dotnet/core/blob/master/Documentation/prereqs.md).

Można zainstalować przy użyciu określonej wersji `--version` argumentu. Należy określić wersję w wersji 3 części (na przykład 1.0.0-13232). Pominięcie używa `latest` wersji.

## <a name="options"></a>Opcje

`-Channel <CHANNEL>`

Określa kanał źródła instalacji. Możliwe wartości to:

- `Current` -Bieżącej wersji
- `LTS` -Długoterminowej kanału pomocy technicznej (bieżąca wersja obsługiwane)
- Wersja dwóch elementów w formacie X.Y reprezentujący dla określonej wersji (na przykład `2.0` lub `1.0`)
- Nazwa gałęzi [na przykład `release/2.0.0`, `release/2.0.0-preview2`, lub `master` najnowsze z `master` gałęzi (wydań co noc "marginesy krawędzi")]

Wartość domyślna to `LTS`. Aby uzyskać więcej informacji dotyczących kanałów pomocy technicznej platformy .NET, zobacz [.NET Core Cykl wsparcia technicznego produktów](https://www.microsoft.com/net/core/support) tematu.

`-Version <VERSION>`

Reprezentuje wersji określonej kompilacji. Możliwe wartości to:

- `latest` -Najnowszych kompilacji w kanale (używany z `-Channel` opcja)
- `coherent` -Najnowszych spójnego kompilacji na kanał. używa kombinacji najnowsza stabilna pakietu (używana z nazwą gałęzi `-Channel` opcje)
- Trzech części wersja reprezentujący określony format X.Y.Z kompilacji wersji; zastępuje `-Channel` opcji. Na przykład: `2.0.0-preview2-006120`

Pominięcie `-Version` domyślnie `latest`.

`-InstallDir <DIRECTORY>`

Określa ścieżkę instalacji. Katalog jest tworzony, jeśli nie istnieje. Wartość domyślna to *LocalAppData %\.dotnet*. Należy pamiętać, że pliki binarne są umieszczane bezpośrednio w katalogu.

`-Architecture <ARCHITECTURE>`

Architektura .NET Core plików binarnych do zainstalowania. Możliwe wartości to `auto`, `x64`, i `x86`. Wartość domyślna to `auto`, reprezentuje aktualnie uruchomionych architektury systemu operacyjnego.

`-SharedRuntime`

Jeśli ustawiona, tego przełącznika na instalację do udostępnionego środowiska wykonawczego. Cały zestaw SDK nie jest zainstalowany.

`-DryRun`

Jeśli nie będzie ustawiona, skrypt przeprowadzenia instalacji; ale zamiast tego Wyświetla jakie wiersza poleceń do używania w celu zainstalowania spójnie obecnie żądanej wersji programu .NET Core interfejsu wiersza polecenia. Na przykład jeśli określisz wersji `latest`, zawiera łącze do określonej wersji, aby to polecenie może być używane w sposób niejednoznaczny w skrypcie kompilacji. Wyświetla również lokalizacji pliku binarnego, aby zainstalować lub pobrać samodzielnie.

`-NoPath`

Jeśli ustawiona, prefiks/installdir nie zostaną wyeksportowane do ścieżki dla bieżącej sesji. Domyślnie skrypt zmodyfikuje ścieżki, która udostępnia natychmiast po przeprowadzeniu instalacji narzędzi interfejsu wiersza polecenia.

`-AzureFeed`

Określa, że adres URL dla platformy Azure źródła danych Instalatora. Nie jest zalecane, aby zmienić tę wartość. Wartość domyślna to `https://dotnetcli.azureedge.net/dotnet`.

`-ProxyAddress`

Jeśli zestaw, Instalator używa serwera proxy w przypadku wysyłania żądań sieci web. (Ta funkcja jest prawidłowa tylko dla systemu Windows)

`--verbose`

Wyświetlanie informacji diagnostycznych.

`--help`

Drukuje pomoc dotyczącą skryptu.

## <a name="examples"></a>Przykłady

Zainstaluj najnowsze długoterminowej obsługiwaną wersję (LTS) w domyślnej lokalizacji:

System Windows:

`./dotnet-install.ps1 -Channel LTS`

System macOS/Linux:

`./dotnet-install.sh --channel LTS`

Zainstaluj najnowszą wersję z kanału 2.0 do określonej lokalizacji:

System Windows:

`./dotnet-install.ps1 -Channel 2.0 -InstallDir C:\cli`

System macOS/Linux:

`./dotnet-install.sh --channel 2.0 --install-dir ~/cli`

Zainstaluj 1.1.0 wersji środowiska uruchomieniowego udostępnionego:

System Windows:

`./dotnet-install.ps1 -SharedRuntime -Version 1.1.0`

System macOS/Linux:

`./dotnet-install.sh --shared-runtime --version 1.1.0`

Uzyskać skrypt i zainstaluj przykłady one-liner .NET Core interfejsu wiersza polecenia:

System Windows:

`@powershell -NoProfile -ExecutionPolicy unrestricted -Command "&([scriptblock]::Create((Invoke-WebRequest -useb 'https://dot.net/v1/dotnet-install.ps1'))) <additional install-script args>"`

System macOS/Linux:

`curl -sSL https://dot.net/v1/dotnet-install.sh | bash /dev/stdin <additional install-script args>`

## <a name="see-also"></a>Zobacz także

[Zwalnia .NET core](https://github.com/dotnet/core/releases)   
[Środowisko uruchomieniowe platformy .NET core i zestawu SDK Pobierz archiwum](https://github.com/dotnet/core/blob/master/release-notes/download-archive.md)

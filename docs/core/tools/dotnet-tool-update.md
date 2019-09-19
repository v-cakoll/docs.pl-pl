---
title: polecenie aktualizacji narzędzia dotnet
description: Polecenie aktualizacji narzędzia dotnet aktualizuje określone narzędzie globalne platformy .NET Core na komputerze.
ms.date: 05/29/2018
ms.openlocfilehash: b10ce39c8b9d4df23243bcf672454a455e34eec1
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117533"
---
# <a name="dotnet-tool-update"></a>dotnet tool update

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a>Nazwa

`dotnet tool update`-Aktualizuje określone [Narzędzie globalne platformy .NET Core](global-tools.md) na komputerze.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet tool update <PACKAGE_NAME> <-g|--global> [--configfile] [--framework] [-v|--verbosity]
dotnet tool update <PACKAGE_NAME> <--tool-path> [--configfile] [--framework] [-v|--verbosity]
dotnet tool update <-h|--help>
```

## <a name="description"></a>Opis

`dotnet tool update` Polecenie umożliwia zaktualizowanie podstawowych narzędzi platformy .NET Core na komputerze do najnowszej stabilnej wersji pakietu. Polecenie Odinstalowuje i ponownie instaluje narzędzie, co skutecznie aktualizuje go. Aby użyć polecenia, musisz określić, że chcesz zaktualizować narzędzie z instalacji na poziomie użytkownika przy użyciu `--global` opcji lub określić ścieżkę do miejsca instalacji narzędzia `--tool-path` przy użyciu opcji.

## <a name="arguments"></a>Argumenty

`PACKAGE_NAME`

Nazwa/identyfikator pakietu NuGet zawierającego narzędzie globalne programu .NET Core do zaktualizowania. Nazwę pakietu można znaleźć przy użyciu polecenia [listy narzędzi dotnet](dotnet-tool-list.md) .

## <a name="options"></a>Opcje

`--add-source <SOURCE>`

Dodaje dodatkowe źródło pakietów NuGet do użycia podczas instalacji.

`--configfile <FILE>`

Plik konfiguracji NuGet (*NuGet. config*) do użycia.

`--framework <FRAMEWORK>`

Określa [platformę docelową](../../standard/frameworks.md) do zaktualizowania narzędzia dla programu.

`-g|--global`

Określa, że aktualizacja dotyczy narzędzia dla całego użytkownika. Nie można łączyć z `--tool-path` opcją. Jeśli ta opcja nie zostanie określona, należy określić `--tool-path` opcję.

`-h|--help`

Drukuje krótką pomoc dla polecenia.

`--tool-path <PATH>`

Określa lokalizację, w której zainstalowano narzędzie globalne. ŚCIEŻKA może być bezwzględna lub względna. Nie można łączyć z `--global` opcją. Jeśli ta opcja nie zostanie określona, należy określić `--global` opcję.

`-v|--verbosity <LEVEL>`

Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i .`diag[nostic]`

## <a name="examples"></a>Przykłady

Aktualizuje narzędzie globalne [dotnetsay](https://www.nuget.org/packages/dotnetsay/) :

`dotnet tool update -g dotnetsay`

Aktualizuje narzędzie globalne [dotnetsay](https://www.nuget.org/packages/dotnetsay/) znajdujące się w określonym folderze systemu Windows:

`dotnet tool update dotnetsay --tool-path c:\global-tools`

Aktualizuje narzędzie globalne [dotnetsay](https://www.nuget.org/packages/dotnetsay/) znajdujące się w określonym folderze systemu Linux/macOS:

`dotnet tool update dotnetsay --tool-path ~/bin`

## <a name="see-also"></a>Zobacz także

- [Narzędzia globalne platformy .NET Core](global-tools.md)

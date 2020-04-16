---
title: Polecenie aktualizacji narzędzia dotnet
description: Polecenie aktualizacji narzędzia dotnet aktualizuje określone narzędzie .NET Core na komputerze.
ms.date: 02/14/2020
ms.openlocfilehash: 6176846dbe8e2a91d9c6959dede15718d8f983b2
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463299"
---
# <a name="dotnet-tool-update"></a>dotnet tool update

**Ten artykuł dotyczy:** ✔️.NET Core 2.1 SDK i nowszych wersjach

## <a name="name"></a>Nazwa

`dotnet tool update`- Aktualizuje określone [narzędzie .NET Core](global-tools.md) na komputerze.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet tool update <PACKAGE_NAME> -g|--global
    [--configfile <FILE>] [--framework <FRAMEWORK>]
    [-v|--verbosity <LEVEL>] [--add-source <SOURCE>]

dotnet tool update <PACKAGE_NAME> --tool-path <PATH>
    [--configfile <FILE>] [--framework <FRAMEWORK>]
    [-v|--verbosity <LEVEL>] [--add-source <SOURCE>]

dotnet tool update <PACKAGE_NAME>
    [--configfile <FILE>] [--framework <FRAMEWORK>]
    [-v|--verbosity <LEVEL>] [--add-source <SOURCE>]

dotnet tool update -h|--help
```

## <a name="description"></a>Opis

Polecenie `dotnet tool update` umożliwia zaktualizowanie narzędzi .NET Core na komputerze do najnowszej stabilnej wersji pakietu. Polecenie odinstalowuje i ponownie instaluje narzędzie, skutecznie aktualizując je. Aby użyć polecenia, należy określić jedną z następujących opcji:

* Aby zaktualizować narzędzie globalne zainstalowane w lokalizacji domyślnej, użyj `--global` tej opcji
* Aby zaktualizować narzędzie globalne zainstalowane w lokalizacji niestandardowej, użyj `--tool-path` tej opcji.
* Aby zaktualizować narzędzie lokalne, `--global` pomiń opcje i `--tool-path` opcje.

**Narzędzia lokalne są dostępne począwszy od .NET Core SDK 3.0.**

## <a name="arguments"></a>Argumenty

- **`PACKAGE_NAME`**

  Nazwa/identyfikator pakietu NuGet, który zawiera globalne narzędzie .NET Core do aktualizacji. Nazwę pakietu można znaleźć za pomocą polecenia [lista narzędzi dotnet.](dotnet-tool-list.md)

## <a name="options"></a>Opcje

- **`--add-source <SOURCE>`**

  Dodaje dodatkowe źródło pakietu NuGet do użycia podczas instalacji.

- **`--configfile <FILE>`**

  Plik konfiguracji NuGet (*nuget.config*).

- **`--framework <FRAMEWORK>`**

  Określa [platformę docelową,](../../standard/frameworks.md) dla aby zaktualizować narzędzie.

- **`-g|--global`**

  Określa, że aktualizacja jest dla narzędzia dla całego użytkownika. Nie można połączyć `--tool-path` z opcją. Pominięcie obu `--global` `--tool-path` i określa, że narzędzie, które ma zostać zaktualizowane, jest narzędziem lokalnym.

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

- **`--tool-path <PATH>`**

  Określa lokalizację, w której jest zainstalowane narzędzie globalne. ŚCIEŻKA może być bezwzględna lub względna. Nie można połączyć `--global` z opcją. Pominięcie obu `--global` `--tool-path` i określa, że narzędzie, które ma zostać zaktualizowane, jest narzędziem lokalnym.

- **`-v|--verbosity <LEVEL>`**

  Ustawia poziom szczegółowości polecenia. Dozwolone wartości `q[uiet]`to `m[inimal]` `n[ormal]`, `d[etailed]`, `diag[nostic]`, i .

## <a name="examples"></a>Przykłady

- **`dotnet tool update -g dotnetsay`**

  Aktualizuje globalne narzędzie [dotnetsay.](https://www.nuget.org/packages/dotnetsay/)

- **`dotnet tool update dotnetsay --tool-path c:\global-tools`**

  Aktualizuje globalne narzędzie [dotnetsay](https://www.nuget.org/packages/dotnetsay/) znajdujące się w określonym katalogu systemu Windows.

- **`dotnet tool update dotnetsay --tool-path ~/bin`**

  Aktualizuje globalne narzędzie [dotnetsay](https://www.nuget.org/packages/dotnetsay/) znajdujące się w określonym katalogu Linux/macOS.

- **`dotnet tool update dotnetsay`**

  Aktualizuje narzędzie lokalne [dotnetsay](https://www.nuget.org/packages/dotnetsay/) zainstalowane dla bieżącego katalogu.

## <a name="see-also"></a>Zobacz też

- [Narzędzia .NET Core](global-tools.md)
- [Samouczek: Instalowanie i używanie globalnego narzędzia .NET Core przy użyciu interfejsu wiersza polecenia .NET Core](global-tools-how-to-use.md)
- [Samouczek: Instalowanie i używanie narzędzia lokalnego .NET Core przy użyciu interfejsu wiersza polecenia .NET Core](local-tools-how-to-use.md)

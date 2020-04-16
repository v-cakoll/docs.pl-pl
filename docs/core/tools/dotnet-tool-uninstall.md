---
title: Polecenie odinstalowywania narzędzia dotnet
description: Polecenie odinstalowywania narzędzia dotnet odinstalowuje określone narzędzie .NET Core z komputera.
ms.date: 02/14/2020
ms.openlocfilehash: 0416f91019a49e17f1be14a1d928ad1fafaa736c
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463310"
---
# <a name="dotnet-tool-uninstall"></a>dotnet tool uninstall

**Ten artykuł dotyczy:** ✔️.NET Core 2.1 SDK i nowszych wersjach

## <a name="name"></a>Nazwa

`dotnet tool uninstall`- Odinstalowuje określone [narzędzie .NET Core](global-tools.md) z komputera.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet tool uninstall <PACKAGE_NAME> -g|--global

dotnet tool uninstall <PACKAGE_NAME> --tool-path <PATH>

dotnet tool uninstall <PACKAGE_NAME>

dotnet tool uninstall -h|--help
```

## <a name="description"></a>Opis

Polecenie `dotnet tool uninstall` umożliwia odinstalowanie narzędzi .NET Core z komputera. Aby użyć polecenia, należy określić jedną z następujących opcji:

* Aby odinstalować narzędzie globalne zainstalowane w lokalizacji `--global` domyślnej, użyj tej opcji.
* Aby odinstalować narzędzie globalne zainstalowane w lokalizacji `--tool-path` niestandardowej, użyj tej opcji.
* Aby odinstalować narzędzie lokalne, pomiń `--global` opcje i `--tool-path` opcje.

**Narzędzia lokalne są dostępne począwszy od .NET Core SDK 3.0.**

## <a name="arguments"></a>Argumenty

- **`PACKAGE_NAME`**

  Nazwa/identyfikator pakietu NuGet zawierającego narzędzie .NET Core do odinstalowania. Nazwę pakietu można znaleźć za pomocą polecenia [lista narzędzi dotnet.](dotnet-tool-list.md)

## <a name="options"></a>Opcje

- **`-g|--global`**

  Określa, że narzędzie do usunięcia pochodzi z instalacji dla całego użytkownika. Nie można połączyć `--tool-path` z opcją. Pominięcie obu `--global` `--tool-path` i określa, że narzędzie do usunięcia jest narzędziem lokalnym.

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

- **`--tool-path <PATH>`**

  Określa lokalizację, w której ma być odinstalowywane narzędzie. ŚCIEŻKA może być bezwzględna lub względna. Nie można połączyć `--global` z opcją. Pominięcie obu `--global` `--tool-path` i określa, że narzędzie do usunięcia jest narzędziem lokalnym.

## <a name="examples"></a>Przykłady

- **`dotnet tool uninstall -g dotnetsay`**

  Odinstalowuje globalne narzędzie [dotnetsay.](https://www.nuget.org/packages/dotnetsay/)

- **`dotnet tool uninstall dotnetsay --tool-path c:\global-tools`**

  Odinstalowuje globalne narzędzie [dotnetsay](https://www.nuget.org/packages/dotnetsay/) z określonego katalogu systemu Windows.

- **`dotnet tool uninstall dotnetsay --tool-path ~/bin`**

  Odinstalowuje globalne narzędzie [dotnetsay](https://www.nuget.org/packages/dotnetsay/) z określonego katalogu Linux/macOS.

- **`dotnet tool uninstall dotnetsay`**

  Odinstalowuje narzędzie lokalne [dotnetsay](https://www.nuget.org/packages/dotnetsay/) z bieżącego katalogu.

## <a name="see-also"></a>Zobacz też

- [Narzędzia .NET Core](global-tools.md)
- [Samouczek: Instalowanie i używanie globalnego narzędzia .NET Core przy użyciu interfejsu wiersza polecenia .NET Core](global-tools-how-to-use.md)
- [Samouczek: Instalowanie i używanie narzędzia lokalnego .NET Core przy użyciu interfejsu wiersza polecenia .NET Core](local-tools-how-to-use.md)

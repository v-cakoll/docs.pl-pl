---
title: polecenie odinstalowywanie narzędzia dotnet
description: Polecenie odinstalowywania narzędzia dotnet odinstalowuje określone narzędzie .NET Core z komputera.
ms.date: 02/14/2020
ms.openlocfilehash: 82799404c40baa3a39f4e2a5fdb414fb745ef448
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847836"
---
# <a name="dotnet-tool-uninstall"></a>dotnet tool uninstall

**Ten artykuł dotyczy:** ✔️ .NET Core 2.1 SDK i nowszych wersji

## <a name="name"></a>Nazwa

`dotnet tool uninstall`- Odinstalowuje określone [narzędzie .NET Core](global-tools.md) z komputera.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet tool uninstall <PACKAGE_NAME> <-g|--global>

dotnet tool uninstall <PACKAGE_NAME> <--tool-path>

dotnet tool uninstall <PACKAGE_NAME>

dotnet tool uninstall <-h|--help>
```

## <a name="description"></a>Opis

Polecenie `dotnet tool uninstall` umożliwia odinstalowanie narzędzi programu .NET Core z komputera. Aby użyć polecenia, należy określić jedną z następujących opcji:

* Aby odinstalować narzędzie globalne, które zostało `--global` zainstalowane w lokalizacji domyślnej, użyj tej opcji.
* Aby odinstalować narzędzie globalne, które zostało `--tool-path` zainstalowane w lokalizacji niestandardowej, użyj tej opcji.
* Aby odinstalować narzędzie lokalne, pomiń te `--global` opcje. `--tool-path`

**Lokalne narzędzia są dostępne począwszy od .NET Core SDK 3.0.**

## <a name="arguments"></a>Argumenty

- **`PACKAGE_NAME`**

  Nazwa/identyfikator pakietu NuGet, który zawiera narzędzie .NET Core do odinstalowania. Nazwę pakietu można znaleźć za pomocą polecenia [listy narzędzi dotnet.](dotnet-tool-list.md)

## <a name="options"></a>Opcje

- **`-g|--global`**

  Określa, że narzędzie, które ma zostać usunięte, pochodzi z instalacji obejmującej cały użytkownik. Nie można połączyć z `--tool-path` tą opcją. Pominięcie obu `--global` `--tool-path` i określa, że narzędzie do usunięcia jest narzędziem lokalnym.

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

- **`--tool-path <PATH>`**

  Określa lokalizację, w której należy odinstalować narzędzie. PATH może być bezwzględny lub względny. Nie można połączyć z `--global` tą opcją. Pominięcie obu `--global` `--tool-path` i określa, że narzędzie do usunięcia jest narzędziem lokalnym.

## <a name="examples"></a>Przykłady

- **`dotnet tool uninstall -g dotnetsay`**

  Odinstalowuje narzędzie globalne [dotnetsay.](https://www.nuget.org/packages/dotnetsay/)

- **`dotnet tool uninstall dotnetsay --tool-path c:\global-tools`**

  Odinstalowuje narzędzie globalne [dotnetsay](https://www.nuget.org/packages/dotnetsay/) z określonego katalogu systemu Windows.

- **`dotnet tool uninstall dotnetsay --tool-path ~/bin`**

  Odinstalowuje globalne narzędzie [dotnetsay](https://www.nuget.org/packages/dotnetsay/) z określonego katalogu Linux/macOS.

- **`dotnet tool uninstall dotnetsay`**

  Odinstalowuje narzędzie lokalne [dotnetsay](https://www.nuget.org/packages/dotnetsay/) z bieżącego katalogu.

## <a name="see-also"></a>Zobacz też

- [Narzędzia .NET Core](global-tools.md)
- [Samouczek: Instalowanie i używanie globalnego narzędzia .NET Core przy użyciu procesora CLI .NET Core](global-tools-how-to-use.md)
- [Samouczek: Instalowanie i używanie lokalnego narzędzia .NET Core przy użyciu procesora CLI .NET Core](local-tools-how-to-use.md)

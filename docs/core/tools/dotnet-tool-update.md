---
title: polecenie dotnet tool update
description: Polecenie aktualizacji narzędzia dotnet aktualizuje określone narzędzie .NET Core na komputerze.
ms.date: 02/14/2020
ms.openlocfilehash: 497b052a8b9cfa9dca8d80316075fe7565d6b35a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847823"
---
# <a name="dotnet-tool-update"></a>dotnet tool update

**Ten artykuł dotyczy:** ✔️ .NET Core 2.1 SDK i nowszych wersji

## <a name="name"></a>Nazwa

`dotnet tool update`- Aktualizuje określone [narzędzie .NET Core](global-tools.md) na komputerze.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet tool update <PACKAGE_NAME> <-g|--global>
    [--configfile] [--framework] [-v|--verbosity]
    [--add-source]

dotnet tool update <PACKAGE_NAME> <--tool-path>
    [--configfile] [--framework] [-v|--verbosity]
    [--add-source]

dotnet tool update <PACKAGE_NAME>
    [--configfile] [--framework] [-v|--verbosity]
    [--add-source]

dotnet tool update <-h|--help>
```

## <a name="description"></a>Opis

Polecenie `dotnet tool update` umożliwia zaktualizowanie narzędzi .NET Core na komputerze do najnowszej stabilnej wersji pakietu. Polecenie odinstalowuje i ponownie instaluje narzędzie, skutecznie je aktualizując. Aby użyć polecenia, należy określić jedną z następujących opcji:

* Aby zaktualizować narzędzie globalne zainstalowane w lokalizacji `--global` domyślnej, użyj opcji
* Aby zaktualizować narzędzie globalne, które zostało zainstalowane `--tool-path` w lokalizacji niestandardowej, użyj tej opcji.
* Aby zaktualizować narzędzie lokalne, `--global` `--tool-path` pomiń te opcje.

**Lokalne narzędzia są dostępne począwszy od .NET Core SDK 3.0.**

## <a name="arguments"></a>Argumenty

- **`PACKAGE_NAME`**

  Nazwa/identyfikator pakietu NuGet, który zawiera globalne narzędzie .NET Core do aktualizacji. Nazwę pakietu można znaleźć za pomocą polecenia [listy narzędzi dotnet.](dotnet-tool-list.md)

## <a name="options"></a>Opcje

- **`--add-source <SOURCE>`**

  Dodaje dodatkowe źródło pakietu NuGet do użycia podczas instalacji.

- **`--configfile <FILE>`**

  Plik konfiguracji NuGet *(nuget.config)* do użycia.

- **`--framework <FRAMEWORK>`**

  Określa [platformę docelową,](../../standard/frameworks.md) dla dla za pomocą platformy docelowej.

- **`-g|--global`**

  Określa, że aktualizacja dotyczy narzędzia dla całego użytkownika. Nie można połączyć z `--tool-path` tą opcją. Pominięcie obu `--global` `--tool-path` i określa, że narzędzie, które ma zostać zaktualizowane, jest narzędziem lokalnym.

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

- **`--tool-path <PATH>`**

  Określa lokalizację, w której jest zainstalowane narzędzie globalne. PATH może być bezwzględny lub względny. Nie można połączyć z `--global` tą opcją. Pominięcie obu `--global` `--tool-path` i określa, że narzędzie, które ma zostać zaktualizowane, jest narzędziem lokalnym.

- **`-v|--verbosity <LEVEL>`**

  Ustawia poziom szczegółowości polecenia. Dozwolone wartości `q[uiet]` `m[inimal]`to `n[ormal]` `d[etailed]`, `diag[nostic]`, , i .

## <a name="examples"></a>Przykłady

- **`dotnet tool update -g dotnetsay`**

  Aktualizuje narzędzie globalne [dotnetsay.](https://www.nuget.org/packages/dotnetsay/)

- **`dotnet tool update dotnetsay --tool-path c:\global-tools`**

  Aktualizuje narzędzie globalne [dotnetsay](https://www.nuget.org/packages/dotnetsay/) znajdujące się w określonym katalogu systemu Windows.

- **`dotnet tool update dotnetsay --tool-path ~/bin`**

  Aktualizuje globalne narzędzie [dotnetsay](https://www.nuget.org/packages/dotnetsay/) znajdujące się w określonym katalogu Linux/macOS.

- **`dotnet tool update dotnetsay`**

  Aktualizuje narzędzie lokalne [dotnetsay](https://www.nuget.org/packages/dotnetsay/) zainstalowane dla bieżącego katalogu.

## <a name="see-also"></a>Zobacz też

- [Narzędzia .NET Core](global-tools.md)
- [Samouczek: Instalowanie i używanie globalnego narzędzia .NET Core przy użyciu procesora CLI .NET Core](global-tools-how-to-use.md)
- [Samouczek: Instalowanie i używanie lokalnego narzędzia .NET Core przy użyciu procesora CLI .NET Core](local-tools-how-to-use.md)

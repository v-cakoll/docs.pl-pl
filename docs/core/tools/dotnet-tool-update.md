---
title: polecenie aktualizacji narzędzia dotnet
description: Polecenie aktualizacji narzędzia dotnet umożliwia zaktualizowanie określonego narzędzia .NET Core na komputerze.
ms.date: 02/14/2020
ms.openlocfilehash: 50bb366fedfb0ea69b8b6007ff89e366b4f689de
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543420"
---
# <a name="dotnet-tool-update"></a>dotnet tool update

**Ten artykuł ma zastosowanie do:** ✔️ .net Core 2,1 SDK i nowszych wersjach

## <a name="name"></a>Name (Nazwa)

`dotnet tool update` — aktualizuje określone [Narzędzie .NET Core](global-tools.md) na komputerze.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet tool update <PACKAGE_NAME> <-g|--global> [--configfile] [--framework] [-v|--verbosity] [--add-source]
dotnet tool update <PACKAGE_NAME> <--tool-path> [--configfile] [--framework] [-v|--verbosity] [--add-source]
dotnet tool update <PACKAGE_NAME> [--configfile] [--framework] [-v|--verbosity] [--add-source]
dotnet tool update <-h|--help>
```

## <a name="description"></a>Opis

`dotnet tool update` polecenie umożliwia zaktualizowanie narzędzi platformy .NET Core na komputerze do najnowszej stabilnej wersji pakietu. Polecenie Odinstalowuje i ponownie instaluje narzędzie, co skutecznie aktualizuje go. Aby użyć polecenia, należy określić jedną z następujących opcji:

* Aby zaktualizować narzędzie globalne, które zostało zainstalowane w lokalizacji domyślnej, użyj opcji `--global`
* Aby zaktualizować narzędzie globalne, które zostało zainstalowane w niestandardowej lokalizacji, użyj opcji `--tool-path`.
* Aby zaktualizować narzędzie lokalne, Pomiń opcje `--global` i `--tool-path`.

**Narzędzia lokalne są dostępne począwszy od zestaw .NET Core SDK 3,0.**

## <a name="arguments"></a>Argumenty

- **`PACKAGE_NAME`**

  Nazwa/identyfikator pakietu NuGet zawierającego narzędzie globalne programu .NET Core do zaktualizowania. Nazwę pakietu można znaleźć przy użyciu polecenia [listy narzędzi dotnet](dotnet-tool-list.md) .

## <a name="options"></a>Opcje

- **`--add-source <SOURCE>`**

  Dodaje dodatkowe źródło pakietów NuGet do użycia podczas instalacji.

- **`--configfile <FILE>`**

  Plik konfiguracji NuGet (*NuGet. config*) do użycia.

- **`--framework <FRAMEWORK>`**

  Określa [platformę docelową](../../standard/frameworks.md) do zaktualizowania narzędzia dla programu.

- **`-g|--global`**

  Określa, że aktualizacja dotyczy narzędzia dla całego użytkownika. Nie można łączyć z opcją `--tool-path`. Pominięcie obu `--global` i `--tool-path` oznacza, że narzędzie, które ma zostać zaktualizowane, jest narzędziem lokalnym. 

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

- **`--tool-path <PATH>`**

  Określa lokalizację, w której zainstalowano narzędzie globalne. ŚCIEŻKA może być bezwzględna lub względna. Nie można łączyć z opcją `--global`. Pominięcie obu `--global` i `--tool-path` oznacza, że narzędzie, które ma zostać zaktualizowane, jest narzędziem lokalnym. 

- **`-v|--verbosity <LEVEL>`**

  Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`.

## <a name="examples"></a>Przykłady

- **`dotnet tool update -g dotnetsay`**

  Aktualizuje narzędzie globalne [dotnetsay](https://www.nuget.org/packages/dotnetsay/) .

- **`dotnet tool update dotnetsay --tool-path c:\global-tools`**

  Aktualizuje narzędzie globalne [dotnetsay](https://www.nuget.org/packages/dotnetsay/) znajdujące się w określonym katalogu systemu Windows.

- **`dotnet tool update dotnetsay --tool-path ~/bin`**

  Aktualizuje narzędzie globalne [dotnetsay](https://www.nuget.org/packages/dotnetsay/) znajdujące się w określonym katalogu systemu Linux/macOS.

- **`dotnet tool update dotnetsay`**

  Aktualizuje narzędzie lokalne [dotnetsay](https://www.nuget.org/packages/dotnetsay/) zainstalowane dla bieżącego katalogu.

## <a name="see-also"></a>Zobacz też

- [Narzędzia .NET Core](global-tools.md)

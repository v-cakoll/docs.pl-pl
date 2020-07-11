---
title: polecenie aktualizacji narzędzia dotnet
description: Polecenie aktualizacji narzędzia dotnet umożliwia zaktualizowanie określonego narzędzia .NET Core na komputerze.
ms.date: 07/08/2020
ms.openlocfilehash: 7c4bde44ac9964828074baeb1a697ba64ed17887
ms.sourcegitcommit: 67cf756b033c6173a1bbd1cbd5aef1fccac99e34
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2020
ms.locfileid: "86226624"
---
# <a name="dotnet-tool-update"></a>dotnet tool update

**Ten artykuł ma zastosowanie do:** ✔️ .net Core 2,1 SDK i nowszych wersjach

## <a name="name"></a>Nazwa

`dotnet tool update`-Aktualizuje określone [Narzędzie .NET Core](global-tools.md) na komputerze.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet tool update <PACKAGE_ID> -g|--global
    [--configfile <FILE>] [--framework <FRAMEWORK>]
    [--add-source <SOURCE>] [--disable-parallel]
    [--ignore-failed-sources] [--interactive] [--no-cache]
    [-v|--verbosity <LEVEL>] [--version <VERSION>]

dotnet tool update <PACKAGE_ID> --tool-path <PATH>
    [--configfile <FILE>] [--framework <FRAMEWORK>]
    [--add-source <SOURCE>] [--disable-parallel]
    [--ignore-failed-sources] [--interactive] [--no-cache]
    [-v|--verbosity <LEVEL>] [--version <VERSION>]

dotnet tool update <PACKAGE_ID> --local
    [--configfile <FILE>] [--framework <FRAMEWORK>]
    [--add-source <SOURCE>] [--disable-parallel]
    [--ignore-failed-sources] [--interactive] [--no-cache]
    [--tool-manifest <PATH>]
    [-v|--verbosity <LEVEL>] [--version <VERSION>]

dotnet tool update -h|--help
```

## <a name="description"></a>Opis

`dotnet tool update`Polecenie umożliwia zaktualizowanie narzędzi platformy .NET Core na komputerze do najnowszej stabilnej wersji pakietu. Polecenie Odinstalowuje i ponownie instaluje narzędzie, co skutecznie aktualizuje go. Aby użyć polecenia, należy określić jedną z następujących opcji:

* Aby zaktualizować narzędzie globalne, które zostało zainstalowane w lokalizacji domyślnej, użyj `--global` opcji
* Aby zaktualizować narzędzie globalne, które zostało zainstalowane w niestandardowej lokalizacji, użyj `--tool-path` opcji.
* Aby zaktualizować narzędzie lokalne, użyj `--local` opcji.

**Narzędzia lokalne są dostępne począwszy od zestaw .NET Core SDK 3,0.**

## <a name="arguments"></a>Argumenty

- **`PACKAGE_ID`**

  Nazwa/identyfikator pakietu NuGet zawierającego narzędzie globalne programu .NET Core do zaktualizowania. Nazwę pakietu można znaleźć przy użyciu polecenia [listy narzędzi dotnet](dotnet-tool-list.md) .

## <a name="options"></a>Opcje

- **`--add-source <SOURCE>`**

  Dodaje dodatkowe źródło pakietów NuGet do użycia podczas instalacji.

- **`--configfile <FILE>`**

  Plik konfiguracji NuGet (*nuget.config*) do użycia.

- **`--disable-parallel`**

  Zapobiegaj równoległemu przywracaniu wielu projektów.

- **`--framework <FRAMEWORK>`**

  Określa [platformę docelową](../../standard/frameworks.md) do zaktualizowania narzędzia dla programu.

- **`--ignore-failed-sources`**

  Traktuj błędy źródłowe pakietu jako ostrzeżenia.

- **`--interactive`**

  Umożliwia zatrzymanie polecenia i oczekiwanie na dane wejściowe użytkownika lub akcję (na przykład zakończenie uwierzytelniania).

- **`--local`**

  Aktualizowanie narzędzia i manifestu narzędzia lokalnego. Nie można łączyć z `--global` opcją.

- **`--no-cache`**

  Nie Buforuj pakietów i żądań HTTP.

- **`--tool-manifest <PATH>`**

  Ścieżka do pliku manifestu.

- **`--tool-path <PATH>`**

  Określa lokalizację, w której zainstalowano narzędzie globalne. ŚCIEŻKA może być bezwzględna lub względna. Nie można łączyć z `--global` opcją. Pominięcie obu `--global` i `--tool-path` oznacza, że narzędzie, które ma zostać zaktualizowane, jest narzędziem lokalnym.

- **`--version <VERSION>`**

  Zakres wersji pakietu Narzędzia do zaktualizowania. Nie można użyć tego do obniżenia wersji, najpierw musisz mieć `uninstall` nowsze wersje.

- **`-g|--global`**

  Określa, że aktualizacja dotyczy narzędzia dla całego użytkownika. Nie można łączyć z `--tool-path` opcją. Pominięcie obu `--global` i `--tool-path` oznacza, że narzędzie, które ma zostać zaktualizowane, jest narzędziem lokalnym.

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

- **`-v|--verbosity <LEVEL>`**

  Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]` , `m[inimal]` , `n[ormal]` , `d[etailed]` i `diag[nostic]` .

## <a name="examples"></a>Przykłady

- **`dotnet tool update -g dotnetsay`**

  Aktualizuje narzędzie globalne [dotnetsay](https://www.nuget.org/packages/dotnetsay/) .

- **`dotnet tool update dotnetsay --tool-path c:\global-tools`**

  Aktualizuje narzędzie globalne [dotnetsay](https://www.nuget.org/packages/dotnetsay/) znajdujące się w określonym katalogu systemu Windows.

- **`dotnet tool update dotnetsay --tool-path ~/bin`**

  Aktualizuje narzędzie globalne [dotnetsay](https://www.nuget.org/packages/dotnetsay/) znajdujące się w określonym katalogu systemu Linux/macOS.

- **`dotnet tool update dotnetsay`**

  Aktualizuje narzędzie lokalne [dotnetsay](https://www.nuget.org/packages/dotnetsay/) zainstalowane dla bieżącego katalogu.

- **`dotnet tool update -g dotnetsay --version 2.0.*`**

  Aktualizuje narzędzie globalne [dotnetsay](https://www.nuget.org/packages/dotnetsay/) do najnowszej wersji poprawki, z wersją główną `2` i wersją pomocniczą programu `0` .

- **`dotnet tool update -g dotnetsay --version (2.0.*,2.1.4)`**

  Aktualizuje narzędzie globalne [dotnetsay](https://www.nuget.org/packages/dotnetsay/) do najniższej wersji w określonym zakresie `(> 2.0.0 && < 2.1.4)` , wersja zostanie `2.1.0` zainstalowana. Aby uzyskać więcej informacji na temat zakresów wersji semantycznej, zobacz [zakres wersji pakietów NuGet](/nuget/concepts/package-versioning#version-ranges).

## <a name="see-also"></a>Zobacz także

- [Narzędzia .NET Core](global-tools.md)
- [Wersja semantyczna](https://semver.org)
- [Samouczek: Instalowanie i używanie narzędzia globalnego platformy .NET Core przy użyciu interfejs wiersza polecenia platformy .NET Core](global-tools-how-to-use.md)
- [Samouczek: Instalowanie lokalnego narzędzia .NET Core i używanie go przy użyciu interfejs wiersza polecenia platformy .NET Core](local-tools-how-to-use.md)

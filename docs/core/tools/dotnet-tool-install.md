---
title: polecenie instalacji narzędzia dotnet
description: Polecenie instalacji narzędzia dotnet służy do instalowania określonego narzędzia platformy .NET Core na komputerze.
ms.date: 02/14/2020
ms.openlocfilehash: 2705defe9b77009ca1411da28dd86d144ccc19e6
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543472"
---
# <a name="dotnet-tool-install"></a>dotnet tool install

**Ten artykuł ma zastosowanie do:** ✔️ .net Core 2,1 SDK i nowszych wersjach

## <a name="name"></a>Name (Nazwa)

`dotnet tool install` — instaluje na komputerze określone [Narzędzie .NET Core](global-tools.md) .

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet tool install <PACKAGE_NAME> <-g|--global> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <PACKAGE_NAME> <--tool-path> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <PACKAGE_NAME> [--add-source] [--configfile] [--framework] [-v|--verbosity] [--version]
dotnet tool install <-h|--help>
```

## <a name="description"></a>Opis

Polecenie `dotnet tool install` zapewnia sposób instalowania narzędzi platformy .NET Core na komputerze. Aby użyć polecenia, należy określić jedną z następujących opcji instalacji:

* Aby zainstalować narzędzie globalne w lokalizacji domyślnej, użyj opcji `--tool-path`.
* Aby zainstalować narzędzie globalne w niestandardowej lokalizacji, użyj opcji `--tool-path`.
* Aby zainstalować narzędzie lokalne, Pomiń opcje `--global` i `--tool-path`.

**Narzędzia lokalne są dostępne począwszy od zestaw .NET Core SDK 3,0.**

Narzędzia globalne są instalowane domyślnie w następujących katalogach po określeniu opcji `-g` lub `--global`:

| System operacyjny          | Ścieżka                          |
|-------------|-------------------------------|
| Linux/macOS | `$HOME/.dotnet/tools`         |
| System Windows     | `%USERPROFILE%\.dotnet\tools` |

Narzędzia lokalne są dodawane do pliku *manifest. JSON* w katalogu *. config* w bieżącym katalogu. Jeśli plik manifestu jeszcze nie istnieje, utwórz go, uruchamiając następujące polecenie:

```dotnetcli
dotnet new tool-manifest
```

Aby uzyskać więcej informacji, zobacz [Instalowanie narzędzia lokalnego](global-tools.md#install-a-local-tool).

## <a name="arguments"></a>Argumenty

- **`PACKAGE_NAME`**

  Nazwa/identyfikator pakietu NuGet zawierającego narzędzie .NET Core do zainstalowania.

## <a name="options"></a>Opcje

- **`add-source <SOURCE>`**

  Dodaje dodatkowe źródło pakietów NuGet do użycia podczas instalacji.

- **`configfile <FILE>`**

  Plik konfiguracji NuGet (*NuGet. config*) do użycia.

- **`framework <FRAMEWORK>`**

  Określa [platformę docelową](../../standard/frameworks.md) do zainstalowania narzędzia dla programu. Domyślnie zestaw .NET Core SDK próbuje wybrać najbardziej odpowiednią platformę docelową.

- **`-g|--global`**

  Określa, że instalacja jest szeroka. Nie można łączyć z opcją `--tool-path`. Pominięcie obu `--global` i `--tool-path` określa instalację narzędzia lokalnego. 

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

- **`tool-path <PATH>`**

  Określa lokalizację, w której ma zostać zainstalowane narzędzie globalne. ŚCIEŻKA może być bezwzględna lub względna. Jeśli ścieżka nie istnieje, polecenie próbuje ją utworzyć. Pominięcie obu `--global` i `--tool-path` określa instalację narzędzia lokalnego. 

- **`-v|--verbosity <LEVEL>`**

  Ustawia poziom szczegółowości polecenia. Dozwolone wartości to `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`i `diag[nostic]`.

- **`--version <VERSION_NUMBER>`**

  Wersja narzędzia do zainstalowania. Domyślnie jest zainstalowana najnowsza stabilna wersja pakietu. Użyj tej opcji, aby zainstalować Podgląd lub starsze wersje narzędzia.

## <a name="examples"></a>Przykłady

- **`dotnet tool install -g dotnetsay`**

  Instaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) jako narzędzie globalne w domyślnej lokalizacji.

- **`dotnet tool install dotnetsay --tool-path c:\global-tools`**

  Instaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) jako narzędzie globalne w określonym katalogu systemu Windows.

- **`dotnet tool install dotnetsay --tool-path ~/bin`**

  Instaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) jako narzędzie globalne w określonym katalogu systemu Linux/macOS.

- **`dotnet tool install -g dotnetsay --version 2.0.0`**

  Instaluje wersję 2.0.0 programu [dotnetsay](https://www.nuget.org/packages/dotnetsay/) jako narzędzie globalne.

- **`dotnet tool install dotnetsay`**

  Instaluje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) jako narzędzie lokalne dla bieżącego katalogu.

## <a name="see-also"></a>Zobacz też

- [Narzędzia .NET Core](global-tools.md)

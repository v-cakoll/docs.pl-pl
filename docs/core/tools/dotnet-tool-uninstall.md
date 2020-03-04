---
title: polecenie Narzędzia dotnet narzędzie do odinstalowywania
description: Polecenie Narzędzia dotnet narzędzie do odinstalowywania Odinstalowuje określone narzędzie .NET Core z maszyny.
ms.date: 02/14/2020
ms.openlocfilehash: 7a15c169c73cf5a743e0fa6f47645d6bccedbde3
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78157048"
---
# <a name="dotnet-tool-uninstall"></a>dotnet tool uninstall

**Ten artykuł ma zastosowanie do:** ✔️ .net Core 2,1 SDK i nowszych wersjach

## <a name="name"></a>Name (Nazwa)

`dotnet tool uninstall` — Odinstalowuje określone [Narzędzie .NET Core](global-tools.md) z maszyny.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet tool uninstall <PACKAGE_NAME> <-g|--global>
dotnet tool uninstall <PACKAGE_NAME> <--tool-path>
dotnet tool uninstall <PACKAGE_NAME>
dotnet tool uninstall <-h|--help>
```

## <a name="description"></a>Opis

`dotnet tool uninstall` polecenie umożliwia odinstalowanie narzędzi .NET Core z komputera. Aby użyć polecenia, należy określić jedną z następujących opcji:

* Aby odinstalować narzędzie globalne, które zostało zainstalowane w lokalizacji domyślnej, użyj opcji `--global`.
* Aby odinstalować narzędzie globalne, które zostało zainstalowane w niestandardowej lokalizacji, użyj opcji `--tool-path`.
* Aby odinstalować narzędzie lokalne, Pomiń opcje `--global` i `--tool-path`.

**Narzędzia lokalne są dostępne począwszy od zestaw .NET Core SDK 3,0.**

## <a name="arguments"></a>Argumenty

- **`PACKAGE_NAME`**

  Nazwa/identyfikator pakietu NuGet zawierającego narzędzie .NET Core do odinstalowania. Nazwę pakietu można znaleźć przy użyciu polecenia [listy narzędzi dotnet](dotnet-tool-list.md) .

## <a name="options"></a>Opcje

- **`-g|--global`**

  Określa, że narzędzie ma zostać usunięte z instalacji na poziomie użytkownika. Nie można łączyć z opcją `--tool-path`. Pominięcie obu `--global` i `--tool-path` określa, że narzędzie ma zostać usunięte, jest narzędziem lokalnym.

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

- **`--tool-path <PATH>`**

  Określa lokalizację, w której ma zostać odinstalowane narzędzie. ŚCIEŻKA może być bezwzględna lub względna. Nie można łączyć z opcją `--global`. Pominięcie obu `--global` i `--tool-path` określa, że narzędzie ma zostać usunięte, jest narzędziem lokalnym.

## <a name="examples"></a>Przykłady

- **`dotnet tool uninstall -g dotnetsay`**

  Odinstalowuje narzędzie globalne [dotnetsay](https://www.nuget.org/packages/dotnetsay/) .

- **`dotnet tool uninstall dotnetsay --tool-path c:\global-tools`**

  Odinstalowuje narzędzie globalne [dotnetsay](https://www.nuget.org/packages/dotnetsay/) z określonego katalogu systemu Windows.

- **`dotnet tool uninstall dotnetsay --tool-path ~/bin`**

  Odinstalowuje narzędzie globalne [dotnetsay](https://www.nuget.org/packages/dotnetsay/) z określonego katalogu systemu Linux/macOS.

- **`dotnet tool uninstall dotnetsay`**

  Odinstalowuje narzędzie lokalne [dotnetsay](https://www.nuget.org/packages/dotnetsay/) z bieżącego katalogu.

## <a name="see-also"></a>Zobacz też

- [Narzędzia .NET Core](global-tools.md)

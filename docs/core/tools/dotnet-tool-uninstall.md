---
title: polecenie odinstalowania narzędzia DotNet
description: Polecenie odinstalowania narzędzia dotnet odinstalowuje określonego narzędzia globalnej podstawowych platformy .NET z poziomu Twojej maszyny.
ms.date: 05/29/2018
ms.openlocfilehash: 4d53d305131e3399ab5d9c19f9319f3ba3544c19
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61648558"
---
# <a name="dotnet-tool-uninstall"></a>Odinstalowywanie narzędzia DotNet

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a>Nazwa

`dotnet tool uninstall` -Odinstalowuje określony [narzędzia programu .NET Core globalnego](global-tools.md) z Twojego komputera.

## <a name="synopsis"></a>Streszczenie

```console
dotnet tool uninstall <PACKAGE_NAME> <-g|--global>
dotnet tool uninstall <PACKAGE_NAME> <--tool-path>
dotnet tool uninstall <-h|--help>
```

## <a name="description"></a>Opis

`dotnet tool uninstall` Polecenia umożliwia należy odinstalować narzędzia globalnej platformy .NET Core z poziomu Twojej maszyny. Można użyć polecenia, masz albo określić, czy chcesz usunąć, przy użyciu narzędzia użytkownika na poziomie `--global` opcję lub określ ścieżkę do miejsca narzędzie jest instalowana za pomocą `--tool-path` opcji.

## <a name="arguments"></a>Argumenty

`PACKAGE_NAME`

Nazwy/Identyfikatora pakietu NuGet, który zawiera .NET Core globalnego narzędzie, aby odinstalować. Możesz znaleźć przy użyciu nazwy pakietu [lista narzędzi dotnet](dotnet-tool-list.md) polecenia.

## <a name="options"></a>Opcje

`-g|--global`

Określa, że narzędzie ma zostać usunięty z instalacji na poziomie użytkownika. Nie można połączyć z `--tool-path` opcji. Jeśli nie określisz tę opcję, należy określić `--tool-path` opcji.

`-h|--help`

Drukuje krótki pomoc dotyczącą polecenia.

`--tool-path <PATH>`

Określa lokalizację, gdzie można odinstalować narzędzie globalne. ŚCIEŻKA może być bezwzględny lub względny. Nie można połączyć z `--global` opcji. Jeśli nie określisz tę opcję, należy określić `--global` opcji.

## <a name="examples"></a>Przykłady

Odinstalowuje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) narzędzie globalne:

`dotnet tool uninstall -g dotnetsay`

Odinstalowuje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) narzędzie globalne z określonego folderu Windows:

`dotnet tool uninstall dotnetsay --tool-path c:\global-tools`

Odinstalowuje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) narzędzie globalne z określonego folderu w systemie Linux/macOS:

`dotnet tool uninstall dotnetsay --tool-path ~/bin`

## <a name="see-also"></a>Zobacz także

- [Narzędzia globalnej platformy .NET core](global-tools.md)

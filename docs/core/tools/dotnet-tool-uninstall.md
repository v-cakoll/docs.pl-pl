---
title: polecenie Narzędzia dotnet narzędzie do odinstalowywania
description: Polecenie Narzędzia dotnet narzędzie do odinstalowywania Odinstalowuje określone narzędzie globalne platformy .NET Core z maszyny.
ms.date: 05/29/2018
ms.openlocfilehash: 033753f44464e78b826e908e0b6cdf276da8a179
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117543"
---
# <a name="dotnet-tool-uninstall"></a>dotnet tool uninstall

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a>Nazwa

`dotnet tool uninstall`-Odinstalowuje określone [Narzędzie globalne platformy .NET Core](global-tools.md) z komputera.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet tool uninstall <PACKAGE_NAME> <-g|--global>
dotnet tool uninstall <PACKAGE_NAME> <--tool-path>
dotnet tool uninstall <-h|--help>
```

## <a name="description"></a>Opis

`dotnet tool uninstall` Polecenie umożliwia odinstalowanie narzędzi globalnych platformy .NET Core z komputera. Aby użyć polecenia, musisz określić, że chcesz usunąć narzędzie dostępne dla użytkownika przy użyciu `--global` opcji lub określić ścieżkę do lokalizacji, w której narzędzie zostanie zainstalowane `--tool-path` przy użyciu opcji.

## <a name="arguments"></a>Argumenty

`PACKAGE_NAME`

Nazwa/identyfikator pakietu NuGet zawierającego narzędzie globalne programu .NET Core do odinstalowania. Nazwę pakietu można znaleźć przy użyciu polecenia [listy narzędzi dotnet](dotnet-tool-list.md) .

## <a name="options"></a>Opcje

`-g|--global`

Określa, że narzędzie ma zostać usunięte z instalacji na poziomie użytkownika. Nie można łączyć z `--tool-path` opcją. Jeśli ta opcja nie zostanie określona, należy określić `--tool-path` opcję.

`-h|--help`

Drukuje krótką pomoc dla polecenia.

`--tool-path <PATH>`

Określa lokalizację, w której ma zostać odinstalowane narzędzie globalne. ŚCIEŻKA może być bezwzględna lub względna. Nie można łączyć z `--global` opcją. Jeśli ta opcja nie zostanie określona, należy określić `--global` opcję.

## <a name="examples"></a>Przykłady

Odinstalowuje narzędzie globalne [dotnetsay](https://www.nuget.org/packages/dotnetsay/) :

`dotnet tool uninstall -g dotnetsay`

Odinstalowuje narzędzie globalne [dotnetsay](https://www.nuget.org/packages/dotnetsay/) z określonego folderu systemu Windows:

`dotnet tool uninstall dotnetsay --tool-path c:\global-tools`

Odinstalowuje narzędzie globalne [dotnetsay](https://www.nuget.org/packages/dotnetsay/) z określonego folderu Linux/macOS:

`dotnet tool uninstall dotnetsay --tool-path ~/bin`

## <a name="see-also"></a>Zobacz także

- [Narzędzia globalne platformy .NET Core](global-tools.md)

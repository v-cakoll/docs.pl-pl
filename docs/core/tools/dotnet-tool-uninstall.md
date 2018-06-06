---
title: polecenie - .NET Core interfejsu wiersza polecenia Odinstaluj narzędzi DotNet
description: Polecenie odinstalowania narzędzia dotnet odinstalowuje określonego .NET Core globalne narzędzia z komputera.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 5cf80d1756dbf4e88bb52a8028d186d44978f440
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696945"
---
# <a name="dotnet-tool-uninstall"></a>Odinstaluj narzędzie DotNet

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a>Nazwa

`dotnet tool uninstall` -Odinstalowuje określony [narzędzie globalne .NET Core](global-tools.md) z komputera.

## <a name="synopsis"></a>Streszczenie

```
dotnet tool uninstall <PACKAGE_NAME> <-g|--global>
dotnet tool uninstall <PACKAGE_NAME> <--tool-path>
dotnet tool uninstall <-h|--help>
```

## <a name="description"></a>Opis

`dotnet tool uninstall` Polecenie umożliwia można odinstalować .NET Core globalne narzędzia z komputera. Polecenia, albo należy określić, czy chcesz usunąć użytkownika na poziomie narzędzia przy użyciu `--global` opcji lub określ ścieżkę, aby wskazywała narzędzie jest instalowana za pomocą `--tool-path` opcji.

## <a name="arguments"></a>Argumenty

`PACKAGE_NAME`

Nazwa/identyfikator pakietu NuGet, który zawiera narzędzie globalne .NET Core do odinstalowania. Można znaleźć przy użyciu nazwy pakietu [lista narzędzi dotnet](dotnet-tool-list.md) polecenia.

## <a name="options"></a>Opcje

`-g|--global`

Określa, że narzędzie do usunięcia z instalacji na poziomie użytkownika. Nie można połączyć z `--tool-path` opcji. Jeśli nie określisz tej opcji, należy określić `--tool-path` opcji.

`-h|--help`

Drukuje krótkich pomocy dla polecenia.

`--tool-path <PATH>`

Określa lokalizację, gdzie można odinstalować narzędzie globalne. ŚCIEŻKA może być bezwzględny lub względny. Nie można połączyć z `--global` opcji. Jeśli nie określisz tej opcji, należy określić `--global` opcji.

## <a name="examples"></a>Przykłady

Odinstalowuje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) narzędzie globalne:

`dotnet tool uninstall -g dotnetsay`

Odinstalowuje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) narzędzie globalne z określonego folderu systemu Windows:

`dotnet tool uninstall dotnetsay --tool-path c:\global-tools`

Odinstalowuje [dotnetsay](https://www.nuget.org/packages/dotnetsay/) narzędzie globalne z określonego folderu Linux/macOS:

`dotnet tool uninstall dotnetsay --tool-path ~/bin`

## <a name="see-also"></a>Zobacz także

[Narzędzia globalne .NET core](global-tools.md)
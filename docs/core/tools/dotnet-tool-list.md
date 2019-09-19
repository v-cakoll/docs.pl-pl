---
title: polecenie listy narzędzi dotnet
description: Polecenie listy narzędzi dotnet zawiera listę określonego narzędzia globalnego platformy .NET Core z komputera.
ms.date: 05/29/2018
ms.openlocfilehash: 6d35b1dce0c6d57edb0c6dd5f9711f093bc804aa
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117562"
---
# <a name="dotnet-tool-list"></a>dotnet tool list

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a>Nazwa

`dotnet tool list`-Wyświetla wszystkie [Narzędzia globalne .NET Core](global-tools.md) aktualnie zainstalowane w katalogu domyślnym na komputerze lub w określonej ścieżce.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet tool list <-g|--global>
dotnet tool list <--tool-path>
dotnet tool list <-h|--help>
```

## <a name="description"></a>Opis

`dotnet tool list` Polecenie umożliwia wyświetlenie listy wszystkich narzędzi globalnych .NET Core zainstalowanych na komputerze (bieżący profil użytkownika) lub w określonej ścieżce. Polecenie wyświetla nazwę pakietu, zainstalowaną wersję i polecenie Narzędzia globalne. Aby użyć polecenia list, musisz określić, że chcesz zobaczyć wszystkie narzędzia dostępne dla użytkownika przy użyciu `--global` opcji lub określić ścieżkę niestandardową `--tool-path` przy użyciu opcji.

## <a name="options"></a>Opcje

`-g|--global`

Wyświetla narzędzia globalne dla całego użytkownika. Nie można łączyć z `--tool-path` opcją. Jeśli ta opcja nie zostanie określona, należy określić `--tool-path` opcję.

`-h|--help`

Drukuje krótką pomoc dla polecenia.

`--tool-path <PATH>`

Określa niestandardową lokalizację, w której mają zostać znalezione narzędzia globalne. ŚCIEŻKA może być bezwzględna lub względna. Nie można łączyć z `--global` opcją. Jeśli ta opcja nie zostanie określona, należy określić `--global` opcję.

## <a name="examples"></a>Przykłady

Wyświetla listę wszystkich narzędzi globalnych zainstalowanych na komputerze użytkownika (bieżący profil użytkownika):

`dotnet tool list -g`

Wyświetla listę globalnych narzędzi z określonego folderu systemu Windows:

`dotnet tool list --tool-path c:\global-tools`

Wyświetla listę globalnych narzędzi z określonego folderu Linux/macOS:

`dotnet tool list --tool-path ~/bin`

## <a name="see-also"></a>Zobacz także

- [Narzędzia globalne platformy .NET Core](global-tools.md)

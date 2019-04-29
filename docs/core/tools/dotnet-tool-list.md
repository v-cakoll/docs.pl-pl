---
title: Lista narzędzi DotNet — polecenie
description: Polecenie listy narzędzi dotnet Wyświetla określonego narzędzia globalnej podstawowe w .NET z poziomu Twojej maszyny.
ms.date: 05/29/2018
ms.openlocfilehash: d3ff7fc90faf6ede3f7de0d5af5112c77ca140db
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61648571"
---
# <a name="dotnet-tool-list"></a>Lista narzędzi DotNet

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a>Nazwa

`dotnet tool list` — Wyświetla listę wszystkich [narzędzia globalnej platformy .NET Core](global-tools.md) aktualnie zainstalowane w domyślnym katalogu na komputerze lub w określonej ścieżce.

## <a name="synopsis"></a>Streszczenie

```console
dotnet tool list <-g|--global>
dotnet tool list <--tool-path>
dotnet tool list <-h|--help>
```

## <a name="description"></a>Opis

`dotnet tool list` Polecenie dostarcza sposób do tworzenia listy wszystkich narzędzi globalnego .NET Core zainstalowane całej użytkownika na komputerze (bieżący profil użytkownika) lub w określonej ścieżce. Polecenie wyświetla nazwę pakietu, zainstalowaną wersję i polecenia narzędzie globalne. Aby korzystać z polecenia list, masz albo określić, czy chcesz zobaczyć wszystkie narzędzia całej użytkownika przy użyciu `--global` opcji lub określić niestandardową ścieżkę, w którym używana jest `--tool-path` opcji.

## <a name="options"></a>Opcje

`-g|--global`

Wyświetla globalne narzędzia na poziomie użytkownika. Nie można połączyć z `--tool-path` opcji. Jeśli nie określisz tę opcję, należy określić `--tool-path` opcji.

`-h|--help`

Drukuje krótki pomoc dotyczącą polecenia.

`--tool-path <PATH>`

Określa niestandardową lokalizację gdzie można znaleźć narzędzia globalnej. ŚCIEŻKA może być bezwzględny lub względny. Nie można połączyć z `--global` opcji. Jeśli nie określisz tę opcję, należy określić `--global` opcji.

## <a name="examples"></a>Przykłady

Wyświetla wszystkie zainstalowane narzędzia globalnej użytkownika całej na komputerze (bieżący profil użytkownika):

`dotnet tool list -g`

Listy globalne narzędzia z określonego folderu Windows:

`dotnet tool list --tool-path c:\global-tools`

Listy globalne narzędzi z określonego folderu w systemie Linux/macOS:

`dotnet tool list --tool-path ~/bin`

## <a name="see-also"></a>Zobacz także

- [Narzędzia globalnej platformy .NET core](global-tools.md)

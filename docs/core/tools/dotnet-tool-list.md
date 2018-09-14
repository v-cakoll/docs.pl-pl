---
title: polecenia DotNet do listy narzędzie — interfejs wiersza polecenia platformy .NET Core
description: Polecenie listy narzędzi dotnet Wyświetla określonego narzędzia globalnej podstawowe w .NET z poziomu Twojej maszyny.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: e2bea974207d3098ed67b69ed16a72a03c44cd8b
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2018
ms.locfileid: "45596926"
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

* [Narzędzia globalnej platformy .NET core](global-tools.md)
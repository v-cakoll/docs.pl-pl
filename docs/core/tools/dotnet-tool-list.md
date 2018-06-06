---
title: polecenie listy narzędzi DotNet - .NET Core interfejsu wiersza polecenia
description: Polecenie listy narzędzi dotnet Wyświetla określony .NET Core globalne narzędzia z komputera.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 5f4793cd37c3a8df06eb6930ad9f381ac70d4e67
ms.sourcegitcommit: bbf70abe6b46073148f78cbf0619de6092b5800c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34696728"
---
# <a name="dotnet-tool-list"></a>Lista narzędzi DotNet

[!INCLUDE [topic-appliesto-net-core-21plus.md](../../../includes/topic-appliesto-net-core-21plus.md)]

## <a name="name"></a>Nazwa

`dotnet tool list` — Wyświetla listę wszystkich [.NET Core globalne narzędzia](global-tools.md) aktualnie zainstalowany domyślny katalog na komputerze lub w określonej ścieżce.

## <a name="synopsis"></a>Streszczenie

```
dotnet tool list <-g|--global>
dotnet tool list <--tool-path>
dotnet tool list <-h|--help>
```

## <a name="description"></a>Opis

`dotnet tool list` Polecenie udostępnia sposób na liście wszystkie narzędzia globalne .NET Core zainstalowane na poziomie użytkownika na komputerze (bieżący profil użytkownika) lub w określonej ścieżce. Polecenie wyświetla nazwę pakietu, wersji i polecenia narzędzie globalne. Polecenia listy albo należy określić, czy chcesz wyświetlić wszystkie narzędzia całej użytkownika przy użyciu `--global` opcji lub Określ niestandardową ścieżkę za pomocą `--tool-path` opcji.

## <a name="options"></a>Opcje

`-g|--global`

Wyświetla globalne narzędzia na poziomie użytkownika. Nie można połączyć z `--tool-path` opcji. Jeśli nie określisz tej opcji, należy określić `--tool-path` opcji.

`-h|--help`

Drukuje krótkich pomocy dla polecenia.

`--tool-path <PATH>`

Określa niestandardową lokalizację gdzie można znaleźć narzędzia globalnego. ŚCIEŻKA może być bezwzględny lub względny. Nie można połączyć z `--global` opcji. Jeśli nie określisz tej opcji, należy określić `--global` opcji.

## <a name="examples"></a>Przykłady

Wyświetla listę wszystkich globalnych zainstalowano narzędzia użytkownika całej na tym komputerze (bieżący profil użytkownika):

`dotnet tool list -g`

Listy globalne narzędzi w określonym folderze systemu Windows:

`dotnet tool list --tool-path c:\global-tools`

Listy globalne narzędzi z określonego folderu Linux/macOS:

`dotnet tool list --tool-path ~/bin`

## <a name="see-also"></a>Zobacz także

[Narzędzia globalne .NET core](global-tools.md)
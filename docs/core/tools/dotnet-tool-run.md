---
title: polecenie uruchom narzędzie dotnet
description: Polecenie uruchamiania narzędzia dotnet wywołuje narzędzie lokalne.
ms.date: 02/14/2020
ms.openlocfilehash: a088cd0b7f4bba014234a8189a42a63aa6d88f4e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847849"
---
# <a name="dotnet-tool-run"></a>dotnet tool run

**Ten artykuł dotyczy:** ✔️ .NET Core 3.0 SDK i nowszych wersji

## <a name="name"></a>Nazwa

`dotnet tool run`- Wywołuje lokalne narzędzie.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet tool run <COMMAND NAME>

dotnet tool run <-h|--help>
```

## <a name="description"></a>Opis

Polecenie `dotnet tool run` wyszukuje pliki manifestu narzędzia, które znajdują się w zakresie bieżącego katalogu. Po znalezieniu odwołania do określonego narzędzia uruchamia narzędzie. Aby uzyskać więcej informacji, zobacz [Wywoływanie narzędzia lokalnego](global-tools.md#invoke-a-local-tool).

## <a name="arguments"></a>Argumenty

- **`COMMAND_NAME`**

  Nazwa polecenia narzędzia do uruchomienia.

## <a name="options"></a>Opcje

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

## <a name="example"></a>Przykład

- **`dotnet tool run dotnetsay`**

  Uruchamia `dotnetsay` narzędzie lokalne.

## <a name="see-also"></a>Zobacz też

- [Narzędzia .NET Core](global-tools.md)
- [Samouczek: Instalowanie i używanie lokalnego narzędzia .NET Core przy użyciu procesora CLI .NET Core](local-tools-how-to-use.md)

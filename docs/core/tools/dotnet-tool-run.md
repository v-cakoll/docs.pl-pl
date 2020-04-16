---
title: polecenie uruchamiania narzędzia dotnet
description: Polecenie uruchamiania narzędzia dotnet wywołuje narzędzie lokalne.
ms.date: 02/14/2020
ms.openlocfilehash: f79c239363e8b3abbd55c54dd1912443e6777fb7
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463323"
---
# <a name="dotnet-tool-run"></a>dotnet tool run

**Ten artykuł dotyczy:** ✔️.NET Core 3.0 SDK i nowszych wersjach

## <a name="name"></a>Nazwa

`dotnet tool run`- Wywołuje narzędzie lokalne.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet tool run <COMMAND NAME>

dotnet tool run -h|--help
```

## <a name="description"></a>Opis

Polecenie `dotnet tool run` przeszukuje pliki manifestu narzędzia, które znajdują się w zakresie bieżącego katalogu. Po znalezieniu odwołania do określonego narzędzia, uruchamia narzędzie. Aby uzyskać więcej informacji, zobacz [Wywoływanie narzędzia lokalnego](global-tools.md#invoke-a-local-tool).

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
- [Samouczek: Instalowanie i używanie narzędzia lokalnego .NET Core przy użyciu interfejsu wiersza polecenia .NET Core](local-tools-how-to-use.md)

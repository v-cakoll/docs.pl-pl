---
title: Uruchom polecenie Narzędzia dotnet
description: Polecenie Uruchom narzędzie dotnet wywołuje narzędzie lokalne.
ms.date: 02/14/2020
ms.openlocfilehash: 76830b8a8088fbf21f14ab0722b9547eabde7ba4
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156962"
---
# <a name="dotnet-tool-run"></a>dotnet tool run

**Ten artykuł ma zastosowanie do:** ✔️ .net Core 3,0 SDK i nowszych wersjach

## <a name="name"></a>Name (Nazwa)

`dotnet tool run` — wywołuje narzędzie lokalne.

## <a name="synopsis"></a>Streszczenie

```dotnetcli
dotnet tool run <COMMAND NAME>
dotnet tool run <-h|--help>
```

## <a name="description"></a>Opis

Polecenie `dotnet tool run` przeszukuje pliki manifestu narzędzia, które znajdują się w zakresie dla bieżącego katalogu. Po znalezieniu odwołania do określonego narzędzia zostanie uruchomione narzędzie. Aby uzyskać więcej informacji, zobacz [wywoływanie narzędzia lokalnego](global-tools.md#invoke-a-local-tool).

## <a name="arguments"></a>Argumenty

- **`COMMAND_NAME`**

  Nazwa polecenia narzędzia do uruchomienia.

## <a name="options"></a>Opcje

- **`-h|--help`**

  Drukuje krótką pomoc dla polecenia.

## <a name="example"></a>Przykład

- **`dotnet tool run dotnetsay`**

  Uruchamia narzędzie `dotnetsay` lokalnego.

## <a name="see-also"></a>Zobacz też

- [Narzędzia .NET Core](global-tools.md)

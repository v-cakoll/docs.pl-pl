---
title: Uruchom polecenie Narzędzia dotnet
description: Polecenie Uruchom narzędzie dotnet wywołuje narzędzie lokalne.
ms.date: 02/14/2020
ms.openlocfilehash: 05b21c0f5ea86f4b99b220f556c61bf83f464114
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543881"
---
# <a name="dotnet-tool-run"></a>uruchomienie narzędzia dotnet

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

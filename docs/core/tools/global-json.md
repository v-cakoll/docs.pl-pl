---
title: Odwołanie Global.JSON
description: Zobacz schematu dla pliku global.json, która pozwala na ustawienie wersji narzędzi platformy .NET Core.
author: blackdwarf
ms.author: mairaw
ms.date: 04/05/2017
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.workload:
- dotnetcore
ms.openlocfilehash: ac53a899e76c99527f2670d0a6bed3f8cc6ce31f
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="globaljson-reference"></a>Odwołanie Global.JSON

*Global.json* pliku umożliwia wybór wersji narzędzi platformy .NET Core używane za pośrednictwem `sdk` właściwości.

Ten plik do bieżącego katalogu roboczego (który jest zawsze taki sam jak katalog projektu) lub jednej z jego katalogi nadrzędne poszukaj narzędzi interfejsu wiersza polecenia platformy .NET core.

## <a name="sdk"></a>zestaw SDK
Typ: obiekt

Określa informacje o zestawie SDK.

### <a name="version"></a>version
Typ: ciąg

Wersja zestawu SDK do użycia.

Na przykład:

```json
{
  "sdk": {
    "version": "1.0.0-preview2-003121"
  }
}
```

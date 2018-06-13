---
title: Odwołanie Global.JSON
description: Zobacz schematu dla pliku global.json, która pozwala na ustawienie wersji narzędzi platformy .NET Core.
author: blackdwarf
ms.author: mairaw
ms.date: 04/05/2017
ms.openlocfilehash: 7479774c7b9cdda233cf32d791c16e7fc6d733a8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33209973"
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

---
title: "Odwołanie Global.JSON"
description: "Zobacz schematu dla pliku global.json, która pozwala na ustawienie wersji narzędzi platformy .NET Core."
keywords: .NET, .NET core
author: blackdwarf
ms.author: mairaw
ms.date: 04/05/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: 96102f96-d403-4385-8ef6-5d80e406eb0c
ms.workload: dotnetcore
ms.openlocfilehash: c7e64995ed00a6b2df1b7e1dfa43c6bea5cf4535
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
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

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
# <a name="globaljson-reference"></a><span data-ttu-id="d5d82-103">Odwołanie Global.JSON</span><span class="sxs-lookup"><span data-stu-id="d5d82-103">global.json reference</span></span>

<span data-ttu-id="d5d82-104">*Global.json* pliku umożliwia wybór wersji narzędzi platformy .NET Core używane za pośrednictwem `sdk` właściwości.</span><span class="sxs-lookup"><span data-stu-id="d5d82-104">The *global.json* file allows selection of the .NET Core tools version being used through the `sdk` property.</span></span>

<span data-ttu-id="d5d82-105">Ten plik do bieżącego katalogu roboczego (który jest zawsze taki sam jak katalog projektu) lub jednej z jego katalogi nadrzędne poszukaj narzędzi interfejsu wiersza polecenia platformy .NET core.</span><span class="sxs-lookup"><span data-stu-id="d5d82-105">.NET Core CLI tools look for this file in the current working directory (which isn't necessarily the same as the project directory) or one of its parent directories.</span></span>

## <a name="sdk"></a><span data-ttu-id="d5d82-106">zestaw SDK</span><span class="sxs-lookup"><span data-stu-id="d5d82-106">sdk</span></span>
<span data-ttu-id="d5d82-107">Typ: obiekt</span><span class="sxs-lookup"><span data-stu-id="d5d82-107">Type: Object</span></span>

<span data-ttu-id="d5d82-108">Określa informacje o zestawie SDK.</span><span class="sxs-lookup"><span data-stu-id="d5d82-108">Specifies information about the SDK.</span></span>

### <a name="version"></a><span data-ttu-id="d5d82-109">version</span><span class="sxs-lookup"><span data-stu-id="d5d82-109">version</span></span>
<span data-ttu-id="d5d82-110">Typ: ciąg</span><span class="sxs-lookup"><span data-stu-id="d5d82-110">Type: String</span></span>

<span data-ttu-id="d5d82-111">Wersja zestawu SDK do użycia.</span><span class="sxs-lookup"><span data-stu-id="d5d82-111">The version of the SDK to use.</span></span>

<span data-ttu-id="d5d82-112">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="d5d82-112">For example:</span></span>

```json
{
  "sdk": {
    "version": "1.0.0-preview2-003121"
  }
}
```

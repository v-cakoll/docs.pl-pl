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
# <a name="globaljson-reference"></a><span data-ttu-id="966ce-104">Odwołanie Global.JSON</span><span class="sxs-lookup"><span data-stu-id="966ce-104">global.json reference</span></span>

<span data-ttu-id="966ce-105">*Global.json* pliku umożliwia wybór wersji narzędzi platformy .NET Core używane za pośrednictwem `sdk` właściwości.</span><span class="sxs-lookup"><span data-stu-id="966ce-105">The *global.json* file allows selection of the .NET Core tools version being used through the `sdk` property.</span></span>

<span data-ttu-id="966ce-106">Ten plik do bieżącego katalogu roboczego (który jest zawsze taki sam jak katalog projektu) lub jednej z jego katalogi nadrzędne poszukaj narzędzi interfejsu wiersza polecenia platformy .NET core.</span><span class="sxs-lookup"><span data-stu-id="966ce-106">.NET Core CLI tools look for this file in the current working directory (which isn't necessarily the same as the project directory) or one of its parent directories.</span></span>

## <a name="sdk"></a><span data-ttu-id="966ce-107">zestaw SDK</span><span class="sxs-lookup"><span data-stu-id="966ce-107">sdk</span></span>
<span data-ttu-id="966ce-108">Typ: obiekt</span><span class="sxs-lookup"><span data-stu-id="966ce-108">Type: Object</span></span>

<span data-ttu-id="966ce-109">Określa informacje o zestawie SDK.</span><span class="sxs-lookup"><span data-stu-id="966ce-109">Specifies information about the SDK.</span></span>

### <a name="version"></a><span data-ttu-id="966ce-110">version</span><span class="sxs-lookup"><span data-stu-id="966ce-110">version</span></span>
<span data-ttu-id="966ce-111">Typ: ciąg</span><span class="sxs-lookup"><span data-stu-id="966ce-111">Type: String</span></span>

<span data-ttu-id="966ce-112">Wersja zestawu SDK do użycia.</span><span class="sxs-lookup"><span data-stu-id="966ce-112">The version of the SDK to use.</span></span>

<span data-ttu-id="966ce-113">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="966ce-113">For example:</span></span>

```json
{
  "sdk": {
    "version": "1.0.0-preview2-003121"
  }
}
```

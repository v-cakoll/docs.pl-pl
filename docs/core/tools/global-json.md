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
ms.openlocfilehash: ffa97164736fc7f3edc450682d23bdf499b6eb34
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="globaljson-reference"></a><span data-ttu-id="0cdfe-104">Odwołanie Global.JSON</span><span class="sxs-lookup"><span data-stu-id="0cdfe-104">global.json reference</span></span>

<span data-ttu-id="0cdfe-105">*Global.json* pliku umożliwia wybór wersji narzędzi platformy .NET Core używane za pośrednictwem `sdk` właściwości.</span><span class="sxs-lookup"><span data-stu-id="0cdfe-105">The *global.json* file allows selection of the .NET Core tools version being used through the `sdk` property.</span></span>

<span data-ttu-id="0cdfe-106">Ten plik do bieżącego katalogu roboczego (który jest zawsze taki sam jak katalog projektu) lub jednej z jego katalogi nadrzędne poszukaj narzędzi interfejsu wiersza polecenia platformy .NET core.</span><span class="sxs-lookup"><span data-stu-id="0cdfe-106">.NET Core CLI tools look for this file in the current working directory (which isn't necessarily the same as the project directory) or one of its parent directories.</span></span>

## <a name="sdk"></a><span data-ttu-id="0cdfe-107">zestaw SDK</span><span class="sxs-lookup"><span data-stu-id="0cdfe-107">sdk</span></span>
<span data-ttu-id="0cdfe-108">Typ: obiekt</span><span class="sxs-lookup"><span data-stu-id="0cdfe-108">Type: Object</span></span>

<span data-ttu-id="0cdfe-109">Określa informacje o zestawie SDK.</span><span class="sxs-lookup"><span data-stu-id="0cdfe-109">Specifies information about the SDK.</span></span>

### <a name="version"></a><span data-ttu-id="0cdfe-110">version</span><span class="sxs-lookup"><span data-stu-id="0cdfe-110">version</span></span>
<span data-ttu-id="0cdfe-111">Typ: ciąg</span><span class="sxs-lookup"><span data-stu-id="0cdfe-111">Type: String</span></span>

<span data-ttu-id="0cdfe-112">Wersja zestawu SDK do użycia.</span><span class="sxs-lookup"><span data-stu-id="0cdfe-112">The version of the SDK to use.</span></span>

<span data-ttu-id="0cdfe-113">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="0cdfe-113">For example:</span></span>

```json
{
  "sdk": {
    "version": "1.0.0-preview2-003121"
  }
}
```

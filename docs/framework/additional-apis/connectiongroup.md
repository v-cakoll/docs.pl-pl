---
title: Klasa ConnectionGroup
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: 
ms.topic: reference
topic_type: apiref
api_name: System.Net.ConnectionGroup
api_location: System.dll
api_type: Assembly
ms.assetid: 25c08217-fdeb-44b9-9cd6-1b4955d6e602
author: guardrex
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d2740136d4ef7377357baa1bc30a7f1c05072c73
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="connectiongroup-class"></a><span data-ttu-id="f0ed5-102">Klasa ConnectionGroup</span><span class="sxs-lookup"><span data-stu-id="f0ed5-102">ConnectionGroup Class</span></span>

<span data-ttu-id="f0ed5-103">`ConnectionGroup` Listę połączeń w ramach grupy klasy <xref:System.Net.ServicePoint> kontekstu i jest używany w celu zachowania kontekst dla zasobów sieciowych (na przykład serwery proxy i oddzielne klientów).</span><span class="sxs-lookup"><span data-stu-id="f0ed5-103">The `ConnectionGroup` class groups a list of connections within the <xref:System.Net.ServicePoint> context and is used to maintain context for network resources (for example, proxies and separate clients).</span></span>

## <a name="syntax"></a><span data-ttu-id="f0ed5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f0ed5-104">Syntax</span></span>
  
```csharp  
internal class ConnectionGroup
```

> [!WARNING]
> <span data-ttu-id="f0ed5-105">`ConnectionGroup` Klasa jest wewnętrzna i nie są one przeznaczone do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="f0ed5-105">The `ConnectionGroup` class is internal and not meant to be used directly in your code.</span></span>
> 
> <span data-ttu-id="f0ed5-106">Microsoft w aplikacji produkcyjnej, w żadnym przypadku nie obsługuje korzystanie z tej klasy.</span><span class="sxs-lookup"><span data-stu-id="f0ed5-106">Microsoft does not support the use of this class in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="f0ed5-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f0ed5-107">Requirements</span></span>

<span data-ttu-id="f0ed5-108">**Namespace:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="f0ed5-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="f0ed5-109">**Zestaw:** System (w System.dll)</span><span class="sxs-lookup"><span data-stu-id="f0ed5-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="f0ed5-110">**Wersje programu .NET framework:** dostępne od wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="f0ed5-110">**.NET Framework versions:** Available since 2.0.</span></span>

---
title: Pole ServicePointManager.s_ServicePointTable
ms.date: 05/01/2017
topic_type:
- apiref
api_name:
- System.Net.ServicePointManager.s_ServicePointTable
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: 24459679-291c-401a-9def-e42b29466fcf
ms.openlocfilehash: 6a56ecd6fc85005f5987c3c2ad0d1680ca63c398
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155820"
---
# <a name="servicepointmanagers_servicepointtable-field"></a><span data-ttu-id="517ce-102">Pole ServicePointManager.s\_ServicePointTable</span><span class="sxs-lookup"><span data-stu-id="517ce-102">ServicePointManager.s\_ServicePointTable Field</span></span>

<span data-ttu-id="517ce-103">`ServicePointManager.s_ServicePointTable`jest <xref:System.Collections.Hashtable> to, która zawiera listę aktywnych połączeń HTTP (s)<xref:System.Net.ServicePoint>w pliku <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="517ce-103">`ServicePointManager.s_ServicePointTable` is a <xref:System.Collections.Hashtable> that contains the list of active HTTP connections (<xref:System.Net.ServicePoint>s) in the <xref:System.AppDomain>.</span></span>

## <a name="syntax"></a><span data-ttu-id="517ce-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="517ce-104">Syntax</span></span>
  
```csharp  
private static Hashtable s_ServicePointTable
```

> [!WARNING]
> <span data-ttu-id="517ce-105">To `ServicePointManager.s_ServicePointTable` pole jest prywatne i nie jest przeznaczone do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="517ce-105">The `ServicePointManager.s_ServicePointTable` field is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="517ce-106">Firma Microsoft w żadnym wypadku nie obsługuje używania tego pola w aplikacji produkcyjnej.</span><span class="sxs-lookup"><span data-stu-id="517ce-106">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="517ce-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="517ce-107">Requirements</span></span>

<span data-ttu-id="517ce-108">**Obszar nazw:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="517ce-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="517ce-109">**Montaż:** System (w pliku System.dll)</span><span class="sxs-lookup"><span data-stu-id="517ce-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="517ce-110">**Wersje programu .NET Framework:** Dostępne od 2.0.</span><span class="sxs-lookup"><span data-stu-id="517ce-110">**.NET Framework versions:** Available since 2.0.</span></span>

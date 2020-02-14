---
title: ServicePoint. m_ConnectionGroupList — pole
ms.date: 05/01/2017
topic_type:
- apiref
api_name:
- System.Net.ServicePoint.m_ConnectionGroupList
api_location:
- System.dll
api_type:
- Assembly
ms.assetid: df8afb59-f0f6-4ddc-b3c1-839b9fc601d8
ms.openlocfilehash: f2759f82f335415edf7bab33edbd446eec6ffbb5
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215515"
---
# <a name="servicepointm_connectiongrouplist-field"></a><span data-ttu-id="54ab2-102">ServicePoint. m\_pole ConnectionGroupList</span><span class="sxs-lookup"><span data-stu-id="54ab2-102">ServicePoint.m\_ConnectionGroupList Field</span></span>

<span data-ttu-id="54ab2-103">`ServicePoint.m_ConnectionGroupList` to <xref:System.Collections.Hashtable> grup połączeń, z których każde utrzymuje połączenie dla identyfikatora URI <xref:System.Net.ServicePoint>.</span><span class="sxs-lookup"><span data-stu-id="54ab2-103">`ServicePoint.m_ConnectionGroupList` is a <xref:System.Collections.Hashtable> of connection groups, each holding a connection for the <xref:System.Net.ServicePoint>'s URI.</span></span>

## <a name="syntax"></a><span data-ttu-id="54ab2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="54ab2-104">Syntax</span></span>
  
```csharp  
private Hashtable m_ConnectionGroupList
```

> [!WARNING]
> <span data-ttu-id="54ab2-105">Pole `ServicePoint.m_ConnectionGroupList` jest prywatne i nie jest przeznaczone do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="54ab2-105">The `ServicePoint.m_ConnectionGroupList` field is private and is not meant to be used directly in your code.</span></span>
> 
> <span data-ttu-id="54ab2-106">Firma Microsoft nie obsługuje korzystania z tego pola w aplikacji produkcyjnej w żadnej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="54ab2-106">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="54ab2-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="54ab2-107">Requirements</span></span>

<span data-ttu-id="54ab2-108">**Przestrzeń nazw:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="54ab2-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="54ab2-109">**Zestaw:** System (w pliku System. dll)</span><span class="sxs-lookup"><span data-stu-id="54ab2-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="54ab2-110">**.NET Framework wersje:** Dostępne od 2,0.</span><span class="sxs-lookup"><span data-stu-id="54ab2-110">**.NET Framework versions:** Available since 2.0.</span></span>

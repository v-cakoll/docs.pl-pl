---
title: ServicePoint. m_ConnectionGroupList — pole
description: Zapoznaj się z polem ServicePoint. m_ConnectionGroupList, czyli tabelą skrótów grup połączeń, które każdy z nich utrzymuje połączenie dla identyfikatora URI ServicePoint w programie .NET.
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
ms.openlocfilehash: 0ebfeb782147f21abfde536b8053fa15b1e1a602
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989718"
---
# <a name="servicepointm_connectiongrouplist-field"></a><span data-ttu-id="4b858-103">ServicePoint. m \_ ConnectionGroupList pole</span><span class="sxs-lookup"><span data-stu-id="4b858-103">ServicePoint.m\_ConnectionGroupList Field</span></span>

<span data-ttu-id="4b858-104">`ServicePoint.m_ConnectionGroupList`jest <xref:System.Collections.Hashtable> grupą połączeń, z których każde utrzymuje połączenie dla <xref:System.Net.ServicePoint> identyfikatora URI.</span><span class="sxs-lookup"><span data-stu-id="4b858-104">`ServicePoint.m_ConnectionGroupList` is a <xref:System.Collections.Hashtable> of connection groups, each holding a connection for the <xref:System.Net.ServicePoint>'s URI.</span></span>

## <a name="syntax"></a><span data-ttu-id="4b858-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="4b858-105">Syntax</span></span>
  
```csharp  
private Hashtable m_ConnectionGroupList
```

> [!WARNING]
> <span data-ttu-id="4b858-106">`ServicePoint.m_ConnectionGroupList`Pole jest prywatne i nie jest przeznaczone do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="4b858-106">The `ServicePoint.m_ConnectionGroupList` field is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="4b858-107">Firma Microsoft nie obsługuje korzystania z tego pola w aplikacji produkcyjnej w żadnej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="4b858-107">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="4b858-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4b858-108">Requirements</span></span>

<span data-ttu-id="4b858-109">**Przestrzeń nazw:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="4b858-109">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="4b858-110">**Zestaw:** System (w System.dll)</span><span class="sxs-lookup"><span data-stu-id="4b858-110">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="4b858-111">**.NET Framework wersje:** Dostępne od 2,0.</span><span class="sxs-lookup"><span data-stu-id="4b858-111">**.NET Framework versions:** Available since 2.0.</span></span>

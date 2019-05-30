---
title: ServicePoint.m_ConnectionGroupList Field
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
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 85359492fbf06942a57c51142620cab015999b31
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300861"
---
# <a name="servicepointmconnectiongrouplist-field"></a><span data-ttu-id="f4c02-102">ServicePoint.m\_ConnectionGroupList Field</span><span class="sxs-lookup"><span data-stu-id="f4c02-102">ServicePoint.m\_ConnectionGroupList Field</span></span>

<span data-ttu-id="f4c02-103">`ServicePoint.m_ConnectionGroupList` jest <xref:System.Collections.Hashtable> grup połączenie, zawierający każdego połączenia dla <xref:System.Net.ServicePoint>w identyfikatorze URI.</span><span class="sxs-lookup"><span data-stu-id="f4c02-103">`ServicePoint.m_ConnectionGroupList` is a <xref:System.Collections.Hashtable> of connection groups, each holding a connection for the <xref:System.Net.ServicePoint>'s URI.</span></span>

## <a name="syntax"></a><span data-ttu-id="f4c02-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f4c02-104">Syntax</span></span>
  
```csharp  
private Hashtable m_ConnectionGroupList
```

> [!WARNING]
> <span data-ttu-id="f4c02-105">`ServicePoint.m_ConnectionGroupList` Pole jest prywatny i nie jest przeznaczona do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="f4c02-105">The `ServicePoint.m_ConnectionGroupList` field is private and is not meant to be used directly in your code.</span></span>
> 
> <span data-ttu-id="f4c02-106">Firma Microsoft obsługuje korzystanie z tego pola w aplikacji produkcyjnej w żadnym wypadku.</span><span class="sxs-lookup"><span data-stu-id="f4c02-106">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="f4c02-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f4c02-107">Requirements</span></span>

<span data-ttu-id="f4c02-108">**Namespace:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="f4c02-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="f4c02-109">**Zestaw:** System (System.dll)</span><span class="sxs-lookup"><span data-stu-id="f4c02-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="f4c02-110">**Wersje programu .NET framework:** Dostępne od wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="f4c02-110">**.NET Framework versions:** Available since 2.0.</span></span>

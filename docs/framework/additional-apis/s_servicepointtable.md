---
title: Pole ServicePointManager. s_ServicePointTable
description: Przeczytaj o polu ServicePointManager. s_ServicePointTable w programie .NET. To pole tabeli skrótów zawiera aktywne połączenia HTTP (servicepoints) w domenie aplikacji.
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
ms.openlocfilehash: 9462ae10125dd37706f786a1f2cef78e62fbabcc
ms.sourcegitcommit: 45c8eed045779b70a47b23169897459d0323dc89
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/18/2020
ms.locfileid: "84989542"
---
# <a name="servicepointmanagers_servicepointtable-field"></a><span data-ttu-id="8fb4f-104">Pole ServicePointManager. s \_</span><span class="sxs-lookup"><span data-stu-id="8fb4f-104">ServicePointManager.s\_ServicePointTable Field</span></span>

<span data-ttu-id="8fb4f-105">`ServicePointManager.s_ServicePointTable`<xref:System.Collections.Hashtable>zawiera listę aktywnych połączeń HTTP <xref:System.Net.ServicePoint> w programie <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="8fb4f-105">`ServicePointManager.s_ServicePointTable` is a <xref:System.Collections.Hashtable> that contains the list of active HTTP connections (<xref:System.Net.ServicePoint>s) in the <xref:System.AppDomain>.</span></span>

## <a name="syntax"></a><span data-ttu-id="8fb4f-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="8fb4f-106">Syntax</span></span>
  
```csharp  
private static Hashtable s_ServicePointTable
```

> [!WARNING]
> <span data-ttu-id="8fb4f-107">`ServicePointManager.s_ServicePointTable`Pole jest prywatne i nie jest przeznaczone do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="8fb4f-107">The `ServicePointManager.s_ServicePointTable` field is private and is not meant to be used directly in your code.</span></span>
>
> <span data-ttu-id="8fb4f-108">Firma Microsoft nie obsługuje korzystania z tego pola w aplikacji produkcyjnej w żadnej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="8fb4f-108">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="8fb4f-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8fb4f-109">Requirements</span></span>

<span data-ttu-id="8fb4f-110">**Przestrzeń nazw:**<xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="8fb4f-110">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="8fb4f-111">**Zestaw:** System (w System.dll)</span><span class="sxs-lookup"><span data-stu-id="8fb4f-111">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="8fb4f-112">**.NET Framework wersje:** Dostępne od 2,0.</span><span class="sxs-lookup"><span data-stu-id="8fb4f-112">**.NET Framework versions:** Available since 2.0.</span></span>

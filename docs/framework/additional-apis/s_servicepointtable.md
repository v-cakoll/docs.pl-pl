---
title: Pole ServicePointManager. s_ServicePointTable
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
ms.openlocfilehash: 272a0c113fd70d804c763ba0e7e6e9a4a4ee04ce
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77214917"
---
# <a name="servicepointmanagers_servicepointtable-field"></a><span data-ttu-id="6595d-102">ServicePointManager. s\_pole ServicePoint</span><span class="sxs-lookup"><span data-stu-id="6595d-102">ServicePointManager.s\_ServicePointTable Field</span></span>

<span data-ttu-id="6595d-103">`ServicePointManager.s_ServicePointTable` to <xref:System.Collections.Hashtable>, która zawiera listę aktywnych połączeń HTTP (<xref:System.Net.ServicePoint>s) w <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="6595d-103">`ServicePointManager.s_ServicePointTable` is a <xref:System.Collections.Hashtable> that contains the list of active HTTP connections (<xref:System.Net.ServicePoint>s) in the <xref:System.AppDomain>.</span></span>

## <a name="syntax"></a><span data-ttu-id="6595d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6595d-104">Syntax</span></span>
  
```csharp  
private static Hashtable s_ServicePointTable
```

> [!WARNING]
> <span data-ttu-id="6595d-105">Pole `ServicePointManager.s_ServicePointTable` jest prywatne i nie jest przeznaczone do użycia bezpośrednio w kodzie.</span><span class="sxs-lookup"><span data-stu-id="6595d-105">The `ServicePointManager.s_ServicePointTable` field is private and is not meant to be used directly in your code.</span></span>
> 
> <span data-ttu-id="6595d-106">Firma Microsoft nie obsługuje korzystania z tego pola w aplikacji produkcyjnej w żadnej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="6595d-106">Microsoft does not support the use of this field in a production application under any circumstance.</span></span>

## <a name="requirements"></a><span data-ttu-id="6595d-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6595d-107">Requirements</span></span>

<span data-ttu-id="6595d-108">**Przestrzeń nazw:** <xref:System.Net></span><span class="sxs-lookup"><span data-stu-id="6595d-108">**Namespace:** <xref:System.Net></span></span>

<span data-ttu-id="6595d-109">**Zestaw:** System (w pliku System. dll)</span><span class="sxs-lookup"><span data-stu-id="6595d-109">**Assembly:** System (in System.dll)</span></span>

<span data-ttu-id="6595d-110">**.NET Framework wersje:** Dostępne od 2,0.</span><span class="sxs-lookup"><span data-stu-id="6595d-110">**.NET Framework versions:** Available since 2.0.</span></span>

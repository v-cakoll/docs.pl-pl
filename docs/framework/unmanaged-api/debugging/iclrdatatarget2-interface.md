---
title: "ICLRDataTarget2 — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataTarget2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataTarget2
helpviewer_keywords: ICLRDataTarget2 interface [.NET Framework debugging]
ms.assetid: 94249397-861b-4294-a538-cf01466a66d3
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a8d8dc7aad35e38b2f9d3b5fb48dacbe1d22bd34
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrdatatarget2-interface"></a><span data-ttu-id="dea9d-102">ICLRDataTarget2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="dea9d-102">ICLRDataTarget2 Interface</span></span>
<span data-ttu-id="dea9d-103">Podklasa [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) używany przez warstwę usługi dostępu do danych do manipulowania regiony pamięci wirtualnej w procesie docelowym.</span><span class="sxs-lookup"><span data-stu-id="dea9d-103">A subclass of [ICLRDataTarget](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md) that is used by the data access services layer to manipulate virtual memory regions in the target process.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dea9d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="dea9d-104">Methods</span></span>  
  
|<span data-ttu-id="dea9d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="dea9d-105">Method</span></span>|<span data-ttu-id="dea9d-106">Opis</span><span class="sxs-lookup"><span data-stu-id="dea9d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dea9d-107">AllocVirtual, metoda</span><span class="sxs-lookup"><span data-stu-id="dea9d-107">AllocVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-allocvirtual-method.md)|<span data-ttu-id="dea9d-108">Przydziela pamięć w przestrzeni adresowej procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="dea9d-108">Allocates memory in the address space of the target process.</span></span>|  
|[<span data-ttu-id="dea9d-109">FreeVirtual, metoda</span><span class="sxs-lookup"><span data-stu-id="dea9d-109">FreeVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget2-freevirtual-method.md)|<span data-ttu-id="dea9d-110">Zwalnia pamięć, która była przydzielona wcześniej do przestrzeni adresowej procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="dea9d-110">Frees memory that was previously allocated in the address space of the target process.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dea9d-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dea9d-111">Remarks</span></span>  
 <span data-ttu-id="dea9d-112">Klient API (tzn. debuger) musi implementować ten interfejs stosownie do określonego procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="dea9d-112">The API client (that is, the debugger) must implement this interface as appropriate for the particular target process.</span></span> <span data-ttu-id="dea9d-113">Na przykład żywy proces miałby inną implementację od tej ze zrzutu pamięci.</span><span class="sxs-lookup"><span data-stu-id="dea9d-113">For example, a live process would have an implementation different from that of a memory dump.</span></span> <span data-ttu-id="dea9d-114">Cel może nie obsługiwać modyfikacji regionów pamięci.</span><span class="sxs-lookup"><span data-stu-id="dea9d-114">The target may not support modification of its memory regions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dea9d-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dea9d-115">Requirements</span></span>  
 <span data-ttu-id="dea9d-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dea9d-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dea9d-117">**Nagłówek:** ClrData.idl, ClrData.h</span><span class="sxs-lookup"><span data-stu-id="dea9d-117">**Header:** ClrData.idl, ClrData.h</span></span>  
  
 <span data-ttu-id="dea9d-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dea9d-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dea9d-119">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dea9d-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dea9d-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dea9d-120">See Also</span></span>  
 [<span data-ttu-id="dea9d-121">ICLRDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="dea9d-121">ICLRDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)  
 [<span data-ttu-id="dea9d-122">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="dea9d-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

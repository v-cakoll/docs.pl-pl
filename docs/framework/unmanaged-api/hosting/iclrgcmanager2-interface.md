---
title: "ICLRGCManager2 — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICLRGCManager2
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager2
helpviewer_keywords:
- ICLRGCManager2 interface [.NET Framework hosting]
ms.assetid: 4b5ffd7b-9ad7-41cd-9bba-34030ae3da7e
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4a8b51cf4297c1ccadbef8730c06148263d310e2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iclrgcmanager2-interface"></a><span data-ttu-id="367a8-102">ICLRGCManager2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="367a8-102">ICLRGCManager2 Interface</span></span>
<span data-ttu-id="367a8-103">Udostępnia metody umożliwiające hosta do interakcji z systemem zbierania odzyskiwanie środowisko uruchomieniowe języka wspólnego firmy.</span><span class="sxs-lookup"><span data-stu-id="367a8-103">Provides methods that allow a host to interact with the common language runtime's garbage collection system.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="367a8-104">Metody</span><span class="sxs-lookup"><span data-stu-id="367a8-104">Methods</span></span>  
  
|<span data-ttu-id="367a8-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="367a8-105">Method</span></span>|<span data-ttu-id="367a8-106">Opis</span><span class="sxs-lookup"><span data-stu-id="367a8-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="367a8-107">SetGCStartupLimitsEx, metoda</span><span class="sxs-lookup"><span data-stu-id="367a8-107">SetGCStartupLimitsEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md)|<span data-ttu-id="367a8-108">Ustawia rozmiar segmentu kolekcji pamięci i maksymalny rozmiar pamięci systemu kolekcji generacji 0.</span><span class="sxs-lookup"><span data-stu-id="367a8-108">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span> <span data-ttu-id="367a8-109">Umożliwia generacji 0 i większa niż rozmiar segmentów `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="367a8-109">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="367a8-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="367a8-110">Remarks</span></span>  
 <span data-ttu-id="367a8-111">Ten interfejs dziedziczy [ICLRGCManager — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="367a8-111">This interface inherits from the [ICLRGCManager Interface](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).</span></span>  
  
 <span data-ttu-id="367a8-112">Środowisko uruchomieniowe języka wspólnego (CLR) implementuje mechanizm kolekcji jego odzyskiwanie z zarządzanego <xref:System.GC> typu.</span><span class="sxs-lookup"><span data-stu-id="367a8-112">The common language runtime (CLR) implements its garbage collection mechanism with the managed <xref:System.GC> type.</span></span> <span data-ttu-id="367a8-113">Aby uzyskać więcej informacji o systemie kolekcji pamięci, zobacz [wyrzucanie elementów bezużytecznych](../../../../docs/standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="367a8-113">For more information about the garbage collection system, see [Garbage Collection](../../../../docs/standard/garbage-collection/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="367a8-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="367a8-114">Requirements</span></span>  
 <span data-ttu-id="367a8-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="367a8-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="367a8-116">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="367a8-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="367a8-117">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="367a8-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="367a8-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="367a8-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="367a8-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="367a8-119">See Also</span></span>  
 [<span data-ttu-id="367a8-120">Automatyczne zarządzanie pamięcią</span><span class="sxs-lookup"><span data-stu-id="367a8-120">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)  
 [<span data-ttu-id="367a8-121">COR_GC_STATS, struktura</span><span class="sxs-lookup"><span data-stu-id="367a8-121">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)  
 [<span data-ttu-id="367a8-122">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="367a8-122">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)  
 [<span data-ttu-id="367a8-123">Interfejsy hostingu środowiska CLR dodane w programie .NET Framework 4 i 4.5</span><span class="sxs-lookup"><span data-stu-id="367a8-123">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)  
 [<span data-ttu-id="367a8-124">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="367a8-124">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="367a8-125">Hosting</span><span class="sxs-lookup"><span data-stu-id="367a8-125">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)

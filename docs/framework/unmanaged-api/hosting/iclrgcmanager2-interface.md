---
title: ICLRGCManager2 — Interfejs
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c54707d4c767fbb644ed892767be8351d2fd95b5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966187"
---
# <a name="iclrgcmanager2-interface"></a><span data-ttu-id="4c495-102">ICLRGCManager2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="4c495-102">ICLRGCManager2 Interface</span></span>
<span data-ttu-id="4c495-103">Dostarcza metody, które umożliwiają hostowi współdziałanie z systemem odzyskiwania pamięci środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="4c495-103">Provides methods that allow a host to interact with the common language runtime's garbage collection system.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4c495-104">Metody</span><span class="sxs-lookup"><span data-stu-id="4c495-104">Methods</span></span>  
  
|<span data-ttu-id="4c495-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="4c495-105">Method</span></span>|<span data-ttu-id="4c495-106">Opis</span><span class="sxs-lookup"><span data-stu-id="4c495-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4c495-107">SetGCStartupLimitsEx, metoda</span><span class="sxs-lookup"><span data-stu-id="4c495-107">SetGCStartupLimitsEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md)|<span data-ttu-id="4c495-108">Ustawia rozmiar segmentu wyrzucania elementów bezużytecznych i maksymalny rozmiar generacji 0 systemu odzyskiwania pamięci.</span><span class="sxs-lookup"><span data-stu-id="4c495-108">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span> <span data-ttu-id="4c495-109">Włącza wartość generacji 0 i rozmiary segmentów `DWORD`większe niż.</span><span class="sxs-lookup"><span data-stu-id="4c495-109">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4c495-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4c495-110">Remarks</span></span>  
 <span data-ttu-id="4c495-111">Ten interfejs dziedziczy z [interfejsu ICLRGCManager](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="4c495-111">This interface inherits from the [ICLRGCManager Interface](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).</span></span>  
  
 <span data-ttu-id="4c495-112">Środowisko uruchomieniowe języka wspólnego (CLR) implementuje mechanizm wyrzucania elementów bezużytecznych z typem zarządzanym <xref:System.GC> .</span><span class="sxs-lookup"><span data-stu-id="4c495-112">The common language runtime (CLR) implements its garbage collection mechanism with the managed <xref:System.GC> type.</span></span> <span data-ttu-id="4c495-113">Aby uzyskać więcej informacji na temat systemu wyrzucania elementów bezużytecznych, zobacz [odzyskiwanie pamięci](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="4c495-113">For more information about the garbage collection system, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c495-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4c495-114">Requirements</span></span>  
 <span data-ttu-id="4c495-115">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c495-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c495-116">**Nagłówki** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="4c495-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="4c495-117">**Biblioteki** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="4c495-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="4c495-118">**.NET Framework wersje:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c495-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c495-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4c495-119">See also</span></span>

- [<span data-ttu-id="4c495-120">Automatyczne zarządzanie pamięcią</span><span class="sxs-lookup"><span data-stu-id="4c495-120">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="4c495-121">COR_GC_STATS, struktura</span><span class="sxs-lookup"><span data-stu-id="4c495-121">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)
- [<span data-ttu-id="4c495-122">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="4c495-122">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="4c495-123">Interfejsy hostingu środowiska CLR dodane w programie .NET Framework 4 i 4.5</span><span class="sxs-lookup"><span data-stu-id="4c495-123">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [<span data-ttu-id="4c495-124">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="4c495-124">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="4c495-125">Hosting</span><span class="sxs-lookup"><span data-stu-id="4c495-125">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)

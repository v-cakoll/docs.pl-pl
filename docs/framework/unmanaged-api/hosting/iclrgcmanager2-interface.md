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
ms.openlocfilehash: 9897526882a8ae53410a7744f78c558dfa6981e1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54708587"
---
# <a name="iclrgcmanager2-interface"></a><span data-ttu-id="125d6-102">ICLRGCManager2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="125d6-102">ICLRGCManager2 Interface</span></span>
<span data-ttu-id="125d6-103">Udostępnia metody, które umożliwiają hosta do interakcji z systemem kolekcji wyrzucania elementów wykonywalnych języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="125d6-103">Provides methods that allow a host to interact with the common language runtime's garbage collection system.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="125d6-104">Metody</span><span class="sxs-lookup"><span data-stu-id="125d6-104">Methods</span></span>  
  
|<span data-ttu-id="125d6-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="125d6-105">Method</span></span>|<span data-ttu-id="125d6-106">Opis</span><span class="sxs-lookup"><span data-stu-id="125d6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="125d6-107">SetGCStartupLimitsEx, metoda</span><span class="sxs-lookup"><span data-stu-id="125d6-107">SetGCStartupLimitsEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md)|<span data-ttu-id="125d6-108">Ustawia rozmiar segmentu kolekcji wyrzucania elementów i maksymalny rozmiar pamięci systemu kolekcji generacji 0.</span><span class="sxs-lookup"><span data-stu-id="125d6-108">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span> <span data-ttu-id="125d6-109">Umożliwia generacji 0 i większa niż rozmiar segmentów `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="125d6-109">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="125d6-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="125d6-110">Remarks</span></span>  
 <span data-ttu-id="125d6-111">Ten interfejs dziedziczy [iclrgcmanager — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="125d6-111">This interface inherits from the [ICLRGCManager Interface](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).</span></span>  
  
 <span data-ttu-id="125d6-112">Środowisko uruchomieniowe języka wspólnego (CLR) implementuje jego mechanizm kolekcji wyrzucania elementów z zarządzaną <xref:System.GC> typu.</span><span class="sxs-lookup"><span data-stu-id="125d6-112">The common language runtime (CLR) implements its garbage collection mechanism with the managed <xref:System.GC> type.</span></span> <span data-ttu-id="125d6-113">Aby uzyskać więcej informacji na temat systemu czyszczenia pamięci zobacz [wyrzucania elementów bezużytecznych](../../../../docs/standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="125d6-113">For more information about the garbage collection system, see [Garbage Collection](../../../../docs/standard/garbage-collection/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="125d6-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="125d6-114">Requirements</span></span>  
 <span data-ttu-id="125d6-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="125d6-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="125d6-116">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="125d6-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="125d6-117">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="125d6-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="125d6-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="125d6-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="125d6-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="125d6-119">See also</span></span>
- [<span data-ttu-id="125d6-120">Automatyczne zarządzanie pamięcią</span><span class="sxs-lookup"><span data-stu-id="125d6-120">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)
- [<span data-ttu-id="125d6-121">COR_GC_STATS, struktura</span><span class="sxs-lookup"><span data-stu-id="125d6-121">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)
- [<span data-ttu-id="125d6-122">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="125d6-122">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="125d6-123">Interfejsy hostingu środowiska CLR dodane w programie .NET Framework 4 i 4.5</span><span class="sxs-lookup"><span data-stu-id="125d6-123">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [<span data-ttu-id="125d6-124">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="125d6-124">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="125d6-125">Hosting</span><span class="sxs-lookup"><span data-stu-id="125d6-125">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)

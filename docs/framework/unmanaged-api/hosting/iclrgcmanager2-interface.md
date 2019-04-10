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
ms.openlocfilehash: a89a7ef34418163d790fd055de681c1cdf989e57
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59226927"
---
# <a name="iclrgcmanager2-interface"></a><span data-ttu-id="40c87-102">ICLRGCManager2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="40c87-102">ICLRGCManager2 Interface</span></span>
<span data-ttu-id="40c87-103">Udostępnia metody, które umożliwiają hosta do interakcji z systemem kolekcji wyrzucania elementów wykonywalnych języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="40c87-103">Provides methods that allow a host to interact with the common language runtime's garbage collection system.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="40c87-104">Metody</span><span class="sxs-lookup"><span data-stu-id="40c87-104">Methods</span></span>  
  
|<span data-ttu-id="40c87-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="40c87-105">Method</span></span>|<span data-ttu-id="40c87-106">Opis</span><span class="sxs-lookup"><span data-stu-id="40c87-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="40c87-107">SetGCStartupLimitsEx, metoda</span><span class="sxs-lookup"><span data-stu-id="40c87-107">SetGCStartupLimitsEx Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md)|<span data-ttu-id="40c87-108">Ustawia rozmiar segmentu kolekcji wyrzucania elementów i maksymalny rozmiar pamięci systemu kolekcji generacji 0.</span><span class="sxs-lookup"><span data-stu-id="40c87-108">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span> <span data-ttu-id="40c87-109">Umożliwia generacji 0 i większa niż rozmiar segmentów `DWORD`.</span><span class="sxs-lookup"><span data-stu-id="40c87-109">Enables generation 0 and segment sizes larger than `DWORD`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="40c87-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="40c87-110">Remarks</span></span>  
 <span data-ttu-id="40c87-111">Ten interfejs dziedziczy [iclrgcmanager — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).</span><span class="sxs-lookup"><span data-stu-id="40c87-111">This interface inherits from the [ICLRGCManager Interface](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-interface.md).</span></span>  
  
 <span data-ttu-id="40c87-112">Środowisko uruchomieniowe języka wspólnego (CLR) implementuje jego mechanizm kolekcji wyrzucania elementów z zarządzaną <xref:System.GC> typu.</span><span class="sxs-lookup"><span data-stu-id="40c87-112">The common language runtime (CLR) implements its garbage collection mechanism with the managed <xref:System.GC> type.</span></span> <span data-ttu-id="40c87-113">Aby uzyskać więcej informacji na temat systemu czyszczenia pamięci zobacz [wyrzucania elementów bezużytecznych](../../../../docs/standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="40c87-113">For more information about the garbage collection system, see [Garbage Collection](../../../../docs/standard/garbage-collection/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="40c87-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="40c87-114">Requirements</span></span>  
 <span data-ttu-id="40c87-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40c87-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40c87-116">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="40c87-116">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="40c87-117">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="40c87-117">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="40c87-118">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="40c87-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="40c87-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="40c87-119">See also</span></span>

- [<span data-ttu-id="40c87-120">Automatyczne zarządzanie pamięcią</span><span class="sxs-lookup"><span data-stu-id="40c87-120">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)
- [<span data-ttu-id="40c87-121">COR_GC_STATS — Struktura</span><span class="sxs-lookup"><span data-stu-id="40c87-121">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)
- [<span data-ttu-id="40c87-122">ICLRControl — Interfejs</span><span class="sxs-lookup"><span data-stu-id="40c87-122">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="40c87-123">Interfejsy hostingu środowiska CLR dodane w programie .NET Framework 4 i 4.5</span><span class="sxs-lookup"><span data-stu-id="40c87-123">CLR Hosting Interfaces Added in the .NET Framework 4 and 4.5</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces-added-in-the-net-framework-4-and-4-5.md)
- [<span data-ttu-id="40c87-124">Hosting — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="40c87-124">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="40c87-125">Hosting</span><span class="sxs-lookup"><span data-stu-id="40c87-125">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)

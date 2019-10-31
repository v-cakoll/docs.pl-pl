---
title: ICLRGCManager — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRGCManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRGCManager
helpviewer_keywords:
- ICLRGCManager interface [.NET Framework hosting]
ms.assetid: fb511c9b-3fe4-41b0-822a-6ba4a079d1f5
topic_type:
- apiref
ms.openlocfilehash: 08c46ecbad85e3cc15f60d1cc8dae6b8281702ef
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141127"
---
# <a name="iclrgcmanager-interface"></a><span data-ttu-id="92581-102">ICLRGCManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="92581-102">ICLRGCManager Interface</span></span>
<span data-ttu-id="92581-103">Dostarcza metody, które umożliwiają hostowi współdziałanie z systemem odzyskiwania pamięci środowiska uruchomieniowego języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="92581-103">Provides methods that allow a host to interact with the common language runtime's garbage collection system.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="92581-104">Począwszy od .NET Framework 4,5, można użyć metody [ICLRGCManager2:: SetGCStartupLimitsEx —](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) , aby ustawić rozmiar segmentu wyrzucania elementów bezużytecznych i maksymalny rozmiar generacji systemu odzyskiwania pamięci na wartość większą niż `DWORD` limit narzucony przez metodę [SetGCStartupLimits —](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md) .</span><span class="sxs-lookup"><span data-stu-id="92581-104">Starting with the .NET Framework 4.5, you can use the [ICLRGCManager2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) method to set the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than the `DWORD` limit that is imposed by the [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="92581-105">Metody</span><span class="sxs-lookup"><span data-stu-id="92581-105">Methods</span></span>  
  
|<span data-ttu-id="92581-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="92581-106">Method</span></span>|<span data-ttu-id="92581-107">Opis</span><span class="sxs-lookup"><span data-stu-id="92581-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="92581-108">Collect, metoda</span><span class="sxs-lookup"><span data-stu-id="92581-108">Collect Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-collect-method.md)|<span data-ttu-id="92581-109">Wymusza wyrzucanie elementów bezużytecznych dla określonej generacji.</span><span class="sxs-lookup"><span data-stu-id="92581-109">Forces a garbage collection for the specified generation.</span></span>|  
|[<span data-ttu-id="92581-110">GetStats, metoda</span><span class="sxs-lookup"><span data-stu-id="92581-110">GetStats Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md)|<span data-ttu-id="92581-111">Pobiera zestaw bieżących statystyk dotyczących systemu odzyskiwania pamięci.</span><span class="sxs-lookup"><span data-stu-id="92581-111">Gets a set of current statistics about the garbage collection system.</span></span>|  
|[<span data-ttu-id="92581-112">SetGCStartupLimits, metoda</span><span class="sxs-lookup"><span data-stu-id="92581-112">SetGCStartupLimits Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md)|<span data-ttu-id="92581-113">Ustawia rozmiar segmentu wyrzucania elementów bezużytecznych i maksymalny rozmiar generacji 0 systemu odzyskiwania pamięci.</span><span class="sxs-lookup"><span data-stu-id="92581-113">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="92581-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="92581-114">Remarks</span></span>  
 <span data-ttu-id="92581-115">Środowisko uruchomieniowe języka wspólnego (CLR) implementuje mechanizm wyrzucania elementów bezużytecznych z typem zarządzanym <xref:System.GC>.</span><span class="sxs-lookup"><span data-stu-id="92581-115">The common language runtime (CLR) implements its garbage collection mechanism with the managed <xref:System.GC> type.</span></span> <span data-ttu-id="92581-116">Aby uzyskać więcej informacji na temat systemu wyrzucania elementów bezużytecznych, zobacz [odzyskiwanie pamięci](../../../standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="92581-116">For more information about the garbage collection system, see [Garbage Collection](../../../standard/garbage-collection/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92581-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="92581-117">Requirements</span></span>  
 <span data-ttu-id="92581-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92581-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92581-119">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="92581-119">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="92581-120">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="92581-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="92581-121">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92581-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92581-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="92581-122">See also</span></span>

- [<span data-ttu-id="92581-123">Automatyczne zarządzanie pamięcią</span><span class="sxs-lookup"><span data-stu-id="92581-123">Automatic Memory Management</span></span>](../../../standard/automatic-memory-management.md)
- [<span data-ttu-id="92581-124">COR_GC_STATS, struktura</span><span class="sxs-lookup"><span data-stu-id="92581-124">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)
- [<span data-ttu-id="92581-125">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="92581-125">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="92581-126">Interfejsy hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="92581-126">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [<span data-ttu-id="92581-127">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="92581-127">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="92581-128">Hosting</span><span class="sxs-lookup"><span data-stu-id="92581-128">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)

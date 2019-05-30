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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6e284f94ad0dac9523bd6267e7bc1034a079503d
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/30/2019
ms.locfileid: "66380295"
---
# <a name="iclrgcmanager-interface"></a><span data-ttu-id="89153-102">ICLRGCManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="89153-102">ICLRGCManager Interface</span></span>
<span data-ttu-id="89153-103">Udostępnia metody, które umożliwiają hosta do interakcji z systemem kolekcji wyrzucania elementów wykonywalnych języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="89153-103">Provides methods that allow a host to interact with the common language runtime's garbage collection system.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="89153-104">Począwszy od programu .NET Framework 4.5, można użyć [iclrgcmanager2::setgcstartuplimitsex —](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) metodę, aby ustawić wartości rozmiaru segmentu kolekcji wyrzucania elementów i maksymalny rozmiar pamięci systemu kolekcji generacji 0 większa niż `DWORD` limit, który jest narzucone przez [setgcstartuplimits —](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="89153-104">Starting with the .NET Framework 4.5, you can use the [ICLRGCManager2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager2-setgcstartuplimitsex-method.md) method to set the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than the `DWORD` limit that is imposed by the [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md) method.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="89153-105">Metody</span><span class="sxs-lookup"><span data-stu-id="89153-105">Methods</span></span>  
  
|<span data-ttu-id="89153-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="89153-106">Method</span></span>|<span data-ttu-id="89153-107">Opis</span><span class="sxs-lookup"><span data-stu-id="89153-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="89153-108">Collect, metoda</span><span class="sxs-lookup"><span data-stu-id="89153-108">Collect Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-collect-method.md)|<span data-ttu-id="89153-109">Wymusza wyrzucania elementów bezużytecznych dla określonej generacji.</span><span class="sxs-lookup"><span data-stu-id="89153-109">Forces a garbage collection for the specified generation.</span></span>|  
|[<span data-ttu-id="89153-110">GetStats, metoda</span><span class="sxs-lookup"><span data-stu-id="89153-110">GetStats Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-getstats-method.md)|<span data-ttu-id="89153-111">Pobiera zestaw statystyk bieżące informacje o systemie kolekcji wyrzucania elementów.</span><span class="sxs-lookup"><span data-stu-id="89153-111">Gets a set of current statistics about the garbage collection system.</span></span>|  
|[<span data-ttu-id="89153-112">SetGCStartupLimits, metoda</span><span class="sxs-lookup"><span data-stu-id="89153-112">SetGCStartupLimits Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrgcmanager-setgcstartuplimits-method.md)|<span data-ttu-id="89153-113">Ustawia rozmiar segmentu kolekcji wyrzucania elementów i maksymalny rozmiar pamięci systemu kolekcji generacji 0.</span><span class="sxs-lookup"><span data-stu-id="89153-113">Sets the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="89153-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="89153-114">Remarks</span></span>  
 <span data-ttu-id="89153-115">Środowisko uruchomieniowe języka wspólnego (CLR) implementuje jego mechanizm kolekcji wyrzucania elementów z zarządzaną <xref:System.GC> typu.</span><span class="sxs-lookup"><span data-stu-id="89153-115">The common language runtime (CLR) implements its garbage collection mechanism with the managed <xref:System.GC> type.</span></span> <span data-ttu-id="89153-116">Aby uzyskać więcej informacji na temat systemu czyszczenia pamięci zobacz [wyrzucania elementów bezużytecznych](../../../../docs/standard/garbage-collection/index.md).</span><span class="sxs-lookup"><span data-stu-id="89153-116">For more information about the garbage collection system, see [Garbage Collection](../../../../docs/standard/garbage-collection/index.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="89153-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="89153-117">Requirements</span></span>  
 <span data-ttu-id="89153-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89153-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89153-119">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="89153-119">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="89153-120">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="89153-120">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="89153-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="89153-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89153-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="89153-122">See also</span></span>

- [<span data-ttu-id="89153-123">Automatyczne zarządzanie pamięcią</span><span class="sxs-lookup"><span data-stu-id="89153-123">Automatic Memory Management</span></span>](../../../../docs/standard/automatic-memory-management.md)
- [<span data-ttu-id="89153-124">COR_GC_STATS, struktura</span><span class="sxs-lookup"><span data-stu-id="89153-124">COR_GC_STATS Structure</span></span>](../../../../docs/framework/unmanaged-api/hosting/cor-gc-stats-structure.md)
- [<span data-ttu-id="89153-125">ICLRControl, interfejs</span><span class="sxs-lookup"><span data-stu-id="89153-125">ICLRControl Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [<span data-ttu-id="89153-126">Interfejsy hostingu środowiska CLR</span><span class="sxs-lookup"><span data-stu-id="89153-126">CLR Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/clr-hosting-interfaces.md)
- [<span data-ttu-id="89153-127">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="89153-127">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="89153-128">Hosting</span><span class="sxs-lookup"><span data-stu-id="89153-128">Hosting</span></span>](../../../../docs/framework/unmanaged-api/hosting/index.md)

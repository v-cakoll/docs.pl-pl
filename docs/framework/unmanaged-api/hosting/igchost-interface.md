---
title: IGCHost — Interfejs
ms.date: 03/30/2017
api_name:
- IGCHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IGCHost
helpviewer_keywords:
- IGCHost interface [.NET Framework hosting]
ms.assetid: 9ad70ffd-6963-4ab2-8c84-3d86c3fb8deb
topic_type:
- apiref
ms.openlocfilehash: 91483d5bdf1eb8e6b03d7691e2a95074e3789317
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134883"
---
# <a name="igchost-interface"></a><span data-ttu-id="a8cf1-102">IGCHost — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a8cf1-102">IGCHost Interface</span></span>
<span data-ttu-id="a8cf1-103">Zapewnia metody uzyskiwania informacji o systemie odzyskiwania pamięci i kontrolowania niektórych aspektów wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="a8cf1-103">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a8cf1-104">Począwszy od .NET Framework 4,5, można użyć metody [IGCHost2:: SetGCStartupLimitsEx —](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) , aby ustawić rozmiar segmentu wyrzucania elementów bezużytecznych i maksymalny rozmiar generacji systemu odzyskiwania pamięci na wartość większą niż limit `DWORD` nałożona przez metodę [SetGCStartupLimits —](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a8cf1-104">Starting with the .NET Framework 4.5, you can use the [IGCHost2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) method to set the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than the `DWORD` limit that is imposed by the [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a8cf1-105">Ten interfejs jest przeznaczony tylko dla ekspertów.</span><span class="sxs-lookup"><span data-stu-id="a8cf1-105">This interface is for expert usage only.</span></span> <span data-ttu-id="a8cf1-106">Może mieć wpływ na wydajność aplikacji, jeśli jest używana nieprawidłowo.</span><span class="sxs-lookup"><span data-stu-id="a8cf1-106">It can affect the performance of an application if used improperly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a8cf1-107">Metody</span><span class="sxs-lookup"><span data-stu-id="a8cf1-107">Methods</span></span>  
  
|<span data-ttu-id="a8cf1-108">Metoda</span><span class="sxs-lookup"><span data-stu-id="a8cf1-108">Method</span></span>|<span data-ttu-id="a8cf1-109">Opis</span><span class="sxs-lookup"><span data-stu-id="a8cf1-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a8cf1-110">Collect, metoda</span><span class="sxs-lookup"><span data-stu-id="a8cf1-110">Collect Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-collect-method.md)|<span data-ttu-id="a8cf1-111">Wymusza, aby kolekcja była wykonywana dla danej generacji, niezależnie od stanu bieżącej wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="a8cf1-111">Forces a collection to occur for the given generation, regardless of the state of the current garbage collection.</span></span>|  
|[<span data-ttu-id="a8cf1-112">GetStats, metoda</span><span class="sxs-lookup"><span data-stu-id="a8cf1-112">GetStats Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-getstats-method.md)|<span data-ttu-id="a8cf1-113">Pobiera statystyki bieżącego stanu systemu odzyskiwania pamięci.</span><span class="sxs-lookup"><span data-stu-id="a8cf1-113">Gets the statistics for the current state of the garbage collection system.</span></span>|  
|[<span data-ttu-id="a8cf1-114">GetThreadStats, metoda</span><span class="sxs-lookup"><span data-stu-id="a8cf1-114">GetThreadStats Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-getthreadstats-method.md)|<span data-ttu-id="a8cf1-115">Pobiera statystyki poszczególnych wątków na potrzeby wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="a8cf1-115">Gets the per-thread statistics for garbage collection.</span></span>|  
|[<span data-ttu-id="a8cf1-116">SetGCStartupLimits, metoda</span><span class="sxs-lookup"><span data-stu-id="a8cf1-116">SetGCStartupLimits Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md)|<span data-ttu-id="a8cf1-117">Ustawia rozmiar segmentu i maksymalny rozmiar generacji 0.</span><span class="sxs-lookup"><span data-stu-id="a8cf1-117">Sets the segment size and the maximum size for generation 0.</span></span>|  
|[<span data-ttu-id="a8cf1-118">SetVirtualMemLimit, metoda</span><span class="sxs-lookup"><span data-stu-id="a8cf1-118">SetVirtualMemLimit Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-setvirtualmemlimit-method.md)|<span data-ttu-id="a8cf1-119">Ustawia maksymalny rozmiar pamięci wirtualnej środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="a8cf1-119">Sets the maximum size of the runtime's virtual memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a8cf1-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a8cf1-120">Requirements</span></span>  
 <span data-ttu-id="a8cf1-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8cf1-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8cf1-122">**Nagłówek:** GCHost. idl, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="a8cf1-122">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="a8cf1-123">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a8cf1-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a8cf1-124">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8cf1-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8cf1-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a8cf1-125">See also</span></span>

- [<span data-ttu-id="a8cf1-126">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="a8cf1-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="a8cf1-127">CorRuntimeHost, klasa coclass</span><span class="sxs-lookup"><span data-stu-id="a8cf1-127">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)

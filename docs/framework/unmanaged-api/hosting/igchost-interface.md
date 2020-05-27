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
ms.openlocfilehash: 9d6c9d22f4e50c21e2f41b7efd402907ff5843db
ms.sourcegitcommit: d223616e7e6fe2139079052e6fcbe25413fb9900
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2020
ms.locfileid: "83805217"
---
# <a name="igchost-interface"></a><span data-ttu-id="9143a-102">IGCHost — Interfejs</span><span class="sxs-lookup"><span data-stu-id="9143a-102">IGCHost Interface</span></span>
<span data-ttu-id="9143a-103">Zapewnia metody uzyskiwania informacji o systemie odzyskiwania pamięci i kontrolowania niektórych aspektów wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="9143a-103">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9143a-104">Począwszy od .NET Framework 4,5, można użyć metody [IGCHost2:: SetGCStartupLimitsEx —](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) , aby ustawić rozmiar segmentu wyrzucania elementów bezużytecznych i maksymalny rozmiar generacji systemu wyrzucania elementów bezużytecznych z wartości większej niż `DWORD` Limit narzucony przez metodę [SetGCStartupLimits —](igchost-setgcstartuplimits-method.md) .</span><span class="sxs-lookup"><span data-stu-id="9143a-104">Starting with the .NET Framework 4.5, you can use the [IGCHost2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) method to set the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than the `DWORD` limit that is imposed by the [SetGCStartupLimits](igchost-setgcstartuplimits-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9143a-105">Ten interfejs jest przeznaczony tylko dla ekspertów.</span><span class="sxs-lookup"><span data-stu-id="9143a-105">This interface is for expert usage only.</span></span> <span data-ttu-id="9143a-106">Może mieć wpływ na wydajność aplikacji, jeśli jest używana nieprawidłowo.</span><span class="sxs-lookup"><span data-stu-id="9143a-106">It can affect the performance of an application if used improperly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9143a-107">Metody</span><span class="sxs-lookup"><span data-stu-id="9143a-107">Methods</span></span>  
  
|<span data-ttu-id="9143a-108">Metoda</span><span class="sxs-lookup"><span data-stu-id="9143a-108">Method</span></span>|<span data-ttu-id="9143a-109">Opis</span><span class="sxs-lookup"><span data-stu-id="9143a-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9143a-110">Collect, metoda</span><span class="sxs-lookup"><span data-stu-id="9143a-110">Collect Method</span></span>](igchost-collect-method.md)|<span data-ttu-id="9143a-111">Wymusza, aby kolekcja była wykonywana dla danej generacji, niezależnie od stanu bieżącej wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="9143a-111">Forces a collection to occur for the given generation, regardless of the state of the current garbage collection.</span></span>|  
|[<span data-ttu-id="9143a-112">GetStats, metoda</span><span class="sxs-lookup"><span data-stu-id="9143a-112">GetStats Method</span></span>](igchost-getstats-method.md)|<span data-ttu-id="9143a-113">Pobiera statystyki bieżącego stanu systemu odzyskiwania pamięci.</span><span class="sxs-lookup"><span data-stu-id="9143a-113">Gets the statistics for the current state of the garbage collection system.</span></span>|  
|[<span data-ttu-id="9143a-114">GetThreadStats, metoda</span><span class="sxs-lookup"><span data-stu-id="9143a-114">GetThreadStats Method</span></span>](igchost-getthreadstats-method.md)|<span data-ttu-id="9143a-115">Pobiera statystyki poszczególnych wątków na potrzeby wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="9143a-115">Gets the per-thread statistics for garbage collection.</span></span>|  
|[<span data-ttu-id="9143a-116">SetGCStartupLimits, metoda</span><span class="sxs-lookup"><span data-stu-id="9143a-116">SetGCStartupLimits Method</span></span>](igchost-setgcstartuplimits-method.md)|<span data-ttu-id="9143a-117">Ustawia rozmiar segmentu i maksymalny rozmiar generacji 0.</span><span class="sxs-lookup"><span data-stu-id="9143a-117">Sets the segment size and the maximum size for generation 0.</span></span>|  
|[<span data-ttu-id="9143a-118">SetVirtualMemLimit, metoda</span><span class="sxs-lookup"><span data-stu-id="9143a-118">SetVirtualMemLimit Method</span></span>](igchost-setvirtualmemlimit-method.md)|<span data-ttu-id="9143a-119">Ustawia maksymalny rozmiar pamięci wirtualnej środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="9143a-119">Sets the maximum size of the runtime's virtual memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9143a-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9143a-120">Requirements</span></span>  
 <span data-ttu-id="9143a-121">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9143a-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9143a-122">**Nagłówek:** GCHost. idl, GCHost. h</span><span class="sxs-lookup"><span data-stu-id="9143a-122">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="9143a-123">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="9143a-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="9143a-124">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9143a-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9143a-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9143a-125">See also</span></span>

- [<span data-ttu-id="9143a-126">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="9143a-126">Hosting Interfaces</span></span>](hosting-interfaces.md)
- [<span data-ttu-id="9143a-127">CorRuntimeHost, klasa coclass</span><span class="sxs-lookup"><span data-stu-id="9143a-127">CorRuntimeHost Coclass</span></span>](corruntimehost-coclass.md)

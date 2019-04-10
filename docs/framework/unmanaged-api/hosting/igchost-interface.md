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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3202aa25261863dae953e3edac36f3406fa001d8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59228176"
---
# <a name="igchost-interface"></a><span data-ttu-id="a958e-102">IGCHost — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a958e-102">IGCHost Interface</span></span>
<span data-ttu-id="a958e-103">Udostępnia metody uzyskiwania informacji na temat systemu czyszczenia pamięci oraz kontrolowanie niektóre aspekty wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="a958e-103">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a958e-104">Począwszy od [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], możesz użyć [igchost2::setgcstartuplimitsex —](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) metodę, aby ustawić rozmiar segmentu kolekcji wyrzucania elementów i maksymalny rozmiar pamięci systemu kolekcji generacji 0 wartości większe niż `DWORD` limit, który jest narzucone przez [setgcstartuplimits —](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="a958e-104">Starting with the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], you can use the [IGCHost2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) method to set the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than the `DWORD` limit that is imposed by the [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a958e-105">Ten interfejs jest wyłącznie na potrzeby ekspertów.</span><span class="sxs-lookup"><span data-stu-id="a958e-105">This interface is for expert usage only.</span></span> <span data-ttu-id="a958e-106">To wpłynąć na wydajność aplikacji użycie nieprawidłowo.</span><span class="sxs-lookup"><span data-stu-id="a958e-106">It can affect the performance of an application if used improperly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a958e-107">Metody</span><span class="sxs-lookup"><span data-stu-id="a958e-107">Methods</span></span>  
  
|<span data-ttu-id="a958e-108">Metoda</span><span class="sxs-lookup"><span data-stu-id="a958e-108">Method</span></span>|<span data-ttu-id="a958e-109">Opis</span><span class="sxs-lookup"><span data-stu-id="a958e-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a958e-110">Collect, metoda</span><span class="sxs-lookup"><span data-stu-id="a958e-110">Collect Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-collect-method.md)|<span data-ttu-id="a958e-111">Wymusza kolekcji wystąpi dla danej generacji, bez względu na stan bieżącej operacji wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="a958e-111">Forces a collection to occur for the given generation, regardless of the state of the current garbage collection.</span></span>|  
|[<span data-ttu-id="a958e-112">GetStats, metoda</span><span class="sxs-lookup"><span data-stu-id="a958e-112">GetStats Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-getstats-method.md)|<span data-ttu-id="a958e-113">Pobiera statystyki dla bieżącego stanu systemu czyszczenia pamięci.</span><span class="sxs-lookup"><span data-stu-id="a958e-113">Gets the statistics for the current state of the garbage collection system.</span></span>|  
|[<span data-ttu-id="a958e-114">GetThreadStats, metoda</span><span class="sxs-lookup"><span data-stu-id="a958e-114">GetThreadStats Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-getthreadstats-method.md)|<span data-ttu-id="a958e-115">Pobiera statystyki wątku wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="a958e-115">Gets the per-thread statistics for garbage collection.</span></span>|  
|[<span data-ttu-id="a958e-116">SetGCStartupLimits, metoda</span><span class="sxs-lookup"><span data-stu-id="a958e-116">SetGCStartupLimits Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md)|<span data-ttu-id="a958e-117">Ustawia rozmiar segmentu i maksymalny rozmiar generacji 0.</span><span class="sxs-lookup"><span data-stu-id="a958e-117">Sets the segment size and the maximum size for generation 0.</span></span>|  
|[<span data-ttu-id="a958e-118">SetVirtualMemLimit, metoda</span><span class="sxs-lookup"><span data-stu-id="a958e-118">SetVirtualMemLimit Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-setvirtualmemlimit-method.md)|<span data-ttu-id="a958e-119">Ustawia maksymalny rozmiar pamięci wirtualnej w środowisku uruchomieniowym.</span><span class="sxs-lookup"><span data-stu-id="a958e-119">Sets the maximum size of the runtime's virtual memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a958e-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a958e-120">Requirements</span></span>  
 <span data-ttu-id="a958e-121">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a958e-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a958e-122">**Nagłówek:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="a958e-122">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="a958e-123">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a958e-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="a958e-124">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="a958e-124">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a958e-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a958e-125">See also</span></span>

- [<span data-ttu-id="a958e-126">Hosting — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="a958e-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [<span data-ttu-id="a958e-127">CorRuntimeHost — Klasa coclass</span><span class="sxs-lookup"><span data-stu-id="a958e-127">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)

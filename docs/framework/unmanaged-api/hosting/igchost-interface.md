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
ms.openlocfilehash: a77cd85c0fafd9994418693c8d3c4b148c34dbe0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437667"
---
# <a name="igchost-interface"></a><span data-ttu-id="25b9a-102">IGCHost — Interfejs</span><span class="sxs-lookup"><span data-stu-id="25b9a-102">IGCHost Interface</span></span>
<span data-ttu-id="25b9a-103">Udostępnia metody uzyskiwania informacji na temat systemu czyszczenia pamięci oraz kontrolowanie niektórych aspektów wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="25b9a-103">Provides methods for obtaining information about the garbage collection system and for controlling some aspects of garbage collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="25b9a-104">Począwszy od [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], można użyć [IGCHost2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) metodę, aby ustawić rozmiar segmentu kolekcji pamięci i maksymalny rozmiar pamięci systemu kolekcji generacji 0 do wartości większej niż `DWORD` limit, który jest narzucone przez [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="25b9a-104">Starting with the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], you can use the [IGCHost2::SetGCStartupLimitsEx](../../../../docs/framework/unmanaged-api/hosting/igchost2-setgcstartuplimitsex-method.md) method to set the size of a garbage collection segment and the maximum size of the garbage collection system's generation 0 to values greater than the `DWORD` limit that is imposed by the [SetGCStartupLimits](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="25b9a-105">Ten interfejs jest tylko użycia ekspertów.</span><span class="sxs-lookup"><span data-stu-id="25b9a-105">This interface is for expert usage only.</span></span> <span data-ttu-id="25b9a-106">To wpłynąć na wydajność aplikacji użycie nieprawidłowo.</span><span class="sxs-lookup"><span data-stu-id="25b9a-106">It can affect the performance of an application if used improperly.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="25b9a-107">Metody</span><span class="sxs-lookup"><span data-stu-id="25b9a-107">Methods</span></span>  
  
|<span data-ttu-id="25b9a-108">Metoda</span><span class="sxs-lookup"><span data-stu-id="25b9a-108">Method</span></span>|<span data-ttu-id="25b9a-109">Opis</span><span class="sxs-lookup"><span data-stu-id="25b9a-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="25b9a-110">Collect, metoda</span><span class="sxs-lookup"><span data-stu-id="25b9a-110">Collect Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-collect-method.md)|<span data-ttu-id="25b9a-111">Wymusza kolekcji wystąpi dla danego generacji, bez względu na stan bieżący wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="25b9a-111">Forces a collection to occur for the given generation, regardless of the state of the current garbage collection.</span></span>|  
|[<span data-ttu-id="25b9a-112">GetStats, metoda</span><span class="sxs-lookup"><span data-stu-id="25b9a-112">GetStats Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-getstats-method.md)|<span data-ttu-id="25b9a-113">Pobiera statystyki dla bieżącego stanu systemu czyszczenia pamięci.</span><span class="sxs-lookup"><span data-stu-id="25b9a-113">Gets the statistics for the current state of the garbage collection system.</span></span>|  
|[<span data-ttu-id="25b9a-114">GetThreadStats, metoda</span><span class="sxs-lookup"><span data-stu-id="25b9a-114">GetThreadStats Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-getthreadstats-method.md)|<span data-ttu-id="25b9a-115">Pobiera statystyki dla każdego wątku wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="25b9a-115">Gets the per-thread statistics for garbage collection.</span></span>|  
|[<span data-ttu-id="25b9a-116">SetGCStartupLimits, metoda</span><span class="sxs-lookup"><span data-stu-id="25b9a-116">SetGCStartupLimits Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-setgcstartuplimits-method.md)|<span data-ttu-id="25b9a-117">Ustawia rozmiar segmentu i maksymalny rozmiar generacji 0.</span><span class="sxs-lookup"><span data-stu-id="25b9a-117">Sets the segment size and the maximum size for generation 0.</span></span>|  
|[<span data-ttu-id="25b9a-118">SetVirtualMemLimit, metoda</span><span class="sxs-lookup"><span data-stu-id="25b9a-118">SetVirtualMemLimit Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/igchost-setvirtualmemlimit-method.md)|<span data-ttu-id="25b9a-119">Ustawia maksymalny rozmiar pamięci wirtualnej środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="25b9a-119">Sets the maximum size of the runtime's virtual memory.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="25b9a-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="25b9a-120">Requirements</span></span>  
 <span data-ttu-id="25b9a-121">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25b9a-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25b9a-122">**Nagłówek:** GCHost.idl, GCHost.h</span><span class="sxs-lookup"><span data-stu-id="25b9a-122">**Header:** GCHost.idl, GCHost.h</span></span>  
  
 <span data-ttu-id="25b9a-123">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="25b9a-123">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="25b9a-124">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25b9a-124">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25b9a-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="25b9a-125">See Also</span></span>  
 [<span data-ttu-id="25b9a-126">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="25b9a-126">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)  
 [<span data-ttu-id="25b9a-127">CorRuntimeHost, klasa coclass</span><span class="sxs-lookup"><span data-stu-id="25b9a-127">CorRuntimeHost Coclass</span></span>](../../../../docs/framework/unmanaged-api/hosting/corruntimehost-coclass.md)

---
title: ICLRMemoryNotificationCallback — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRMemoryNotificationCallback
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRMemoryNotificationCallback
helpviewer_keywords:
- ICLRMemoryNotificationCallback interface [.NET Framework hosting]
ms.assetid: 873639e2-4837-4568-83b3-4493e67e4174
topic_type:
- apiref
ms.openlocfilehash: 52fc21044d345998ad72c045cdf5e80a8a03a38e
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703800"
---
# <a name="iclrmemorynotificationcallback-interface"></a><span data-ttu-id="63d04-102">ICLRMemoryNotificationCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="63d04-102">ICLRMemoryNotificationCallback Interface</span></span>
<span data-ttu-id="63d04-103">Umożliwia hostowi zgłaszanie warunków ciśnienia pamięci przy użyciu podejścia podobnego do `CreateMemoryResourceNotification` funkcji Win32.</span><span class="sxs-lookup"><span data-stu-id="63d04-103">Allows the host to report memory pressure conditions using an approach similar to that of the Win32 `CreateMemoryResourceNotification` function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="63d04-104">Metody</span><span class="sxs-lookup"><span data-stu-id="63d04-104">Methods</span></span>  
  
|<span data-ttu-id="63d04-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="63d04-105">Method</span></span>|<span data-ttu-id="63d04-106">Opis</span><span class="sxs-lookup"><span data-stu-id="63d04-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="63d04-107">OnMemoryNotification, metoda</span><span class="sxs-lookup"><span data-stu-id="63d04-107">OnMemoryNotification Method</span></span>](iclrmemorynotificationcallback-onmemorynotification-method.md)|<span data-ttu-id="63d04-108">Powiadamia środowisko uruchomieniowe języka wspólnego (CLR) o załadowaniu pamięci na komputerze.</span><span class="sxs-lookup"><span data-stu-id="63d04-108">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="63d04-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="63d04-109">Remarks</span></span>  
 <span data-ttu-id="63d04-110">Host używa `ICLRMemoryNotificationCallback` interfejsu do żądania zasobów wolnej pamięci środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="63d04-110">The host uses the `ICLRMemoryNotificationCallback` interface to request that the CLR free memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63d04-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="63d04-111">Requirements</span></span>  
 <span data-ttu-id="63d04-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63d04-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63d04-113">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="63d04-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="63d04-114">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="63d04-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="63d04-115">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63d04-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63d04-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="63d04-116">See also</span></span>

- [<span data-ttu-id="63d04-117">IHostMemoryManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="63d04-117">IHostMemoryManager Interface</span></span>](ihostmemorymanager-interface.md)
- [<span data-ttu-id="63d04-118">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="63d04-118">Hosting Interfaces</span></span>](hosting-interfaces.md)

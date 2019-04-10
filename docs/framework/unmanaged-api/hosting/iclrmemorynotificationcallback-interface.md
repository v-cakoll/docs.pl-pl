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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c98ece9d60571034f3298f15897b10c4d8fb06f4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59212157"
---
# <a name="iclrmemorynotificationcallback-interface"></a><span data-ttu-id="9fbda-102">ICLRMemoryNotificationCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="9fbda-102">ICLRMemoryNotificationCallback Interface</span></span>
<span data-ttu-id="9fbda-103">Zezwalaj hostowi na warunki wykorzystanie pamięci raportu przy użyciu podejścia, podobnie jak w przypadku Win32 `CreateMemoryResourceNotification` funkcji.</span><span class="sxs-lookup"><span data-stu-id="9fbda-103">Allows the host to report memory pressure conditions using an approach similar to that of the Win32 `CreateMemoryResourceNotification` function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9fbda-104">Metody</span><span class="sxs-lookup"><span data-stu-id="9fbda-104">Methods</span></span>  
  
|<span data-ttu-id="9fbda-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="9fbda-105">Method</span></span>|<span data-ttu-id="9fbda-106">Opis</span><span class="sxs-lookup"><span data-stu-id="9fbda-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9fbda-107">OnMemoryNotification, metoda</span><span class="sxs-lookup"><span data-stu-id="9fbda-107">OnMemoryNotification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)|<span data-ttu-id="9fbda-108">Powiadamia środowisko uruchomieniowe języka wspólnego (CLR) obciążenia pamięci na komputerze.</span><span class="sxs-lookup"><span data-stu-id="9fbda-108">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9fbda-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9fbda-109">Remarks</span></span>  
 <span data-ttu-id="9fbda-110">Host używa `ICLRMemoryNotificationCallback` interfejsu do żądania, że środowisko CLR Zwolnij zasoby pamięci.</span><span class="sxs-lookup"><span data-stu-id="9fbda-110">The host uses the `ICLRMemoryNotificationCallback` interface to request that the CLR free memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9fbda-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9fbda-111">Requirements</span></span>  
 <span data-ttu-id="9fbda-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9fbda-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9fbda-113">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="9fbda-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="9fbda-114">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9fbda-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="9fbda-115">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="9fbda-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9fbda-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9fbda-116">See also</span></span>

- [<span data-ttu-id="9fbda-117">IHostMemoryManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="9fbda-117">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="9fbda-118">Hosting — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="9fbda-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)

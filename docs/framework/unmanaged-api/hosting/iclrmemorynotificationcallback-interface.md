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
ms.openlocfilehash: 2c5cf7e17989f3c083c7c4e52fa8cfc09c00bc7d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431522"
---
# <a name="iclrmemorynotificationcallback-interface"></a><span data-ttu-id="dbcdd-102">ICLRMemoryNotificationCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="dbcdd-102">ICLRMemoryNotificationCallback Interface</span></span>
<span data-ttu-id="dbcdd-103">Umożliwia hostowi warunków braku pamięci raportu w sposób podobny do środowiska Win32 `CreateMemoryResourceNotification` funkcji.</span><span class="sxs-lookup"><span data-stu-id="dbcdd-103">Allows the host to report memory pressure conditions using an approach similar to that of the Win32 `CreateMemoryResourceNotification` function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dbcdd-104">Metody</span><span class="sxs-lookup"><span data-stu-id="dbcdd-104">Methods</span></span>  
  
|<span data-ttu-id="dbcdd-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="dbcdd-105">Method</span></span>|<span data-ttu-id="dbcdd-106">Opis</span><span class="sxs-lookup"><span data-stu-id="dbcdd-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dbcdd-107">OnMemoryNotification, metoda</span><span class="sxs-lookup"><span data-stu-id="dbcdd-107">OnMemoryNotification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)|<span data-ttu-id="dbcdd-108">Powiadamia środowisko uruchomieniowe języka wspólnego (CLR) obciążenia pamięci na komputerze.</span><span class="sxs-lookup"><span data-stu-id="dbcdd-108">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dbcdd-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dbcdd-109">Remarks</span></span>  
 <span data-ttu-id="dbcdd-110">Host używa `ICLRMemoryNotificationCallback` interfejsu na żądanie, że środowisko CLR zwolnienia zasobów pamięci.</span><span class="sxs-lookup"><span data-stu-id="dbcdd-110">The host uses the `ICLRMemoryNotificationCallback` interface to request that the CLR free memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dbcdd-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dbcdd-111">Requirements</span></span>  
 <span data-ttu-id="dbcdd-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dbcdd-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dbcdd-113">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="dbcdd-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="dbcdd-114">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="dbcdd-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="dbcdd-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dbcdd-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dbcdd-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dbcdd-116">See Also</span></span>  
 [<span data-ttu-id="dbcdd-117">IHostMemoryManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="dbcdd-117">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="dbcdd-118">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="dbcdd-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)

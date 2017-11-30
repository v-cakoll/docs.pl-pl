---
title: "ICLRMemoryNotificationCallback — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRMemoryNotificationCallback
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRMemoryNotificationCallback
helpviewer_keywords: ICLRMemoryNotificationCallback interface [.NET Framework hosting]
ms.assetid: 873639e2-4837-4568-83b3-4493e67e4174
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 6b998f8af2c7f4add3ecbb905928b5956409bf00
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclrmemorynotificationcallback-interface"></a><span data-ttu-id="54dd7-102">ICLRMemoryNotificationCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="54dd7-102">ICLRMemoryNotificationCallback Interface</span></span>
<span data-ttu-id="54dd7-103">Umożliwia hostowi warunków braku pamięci raportu w sposób podobny do środowiska Win32 `CreateMemoryResourceNotification` funkcji.</span><span class="sxs-lookup"><span data-stu-id="54dd7-103">Allows the host to report memory pressure conditions using an approach similar to that of the Win32 `CreateMemoryResourceNotification` function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="54dd7-104">Metody</span><span class="sxs-lookup"><span data-stu-id="54dd7-104">Methods</span></span>  
  
|<span data-ttu-id="54dd7-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="54dd7-105">Method</span></span>|<span data-ttu-id="54dd7-106">Opis</span><span class="sxs-lookup"><span data-stu-id="54dd7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="54dd7-107">OnMemoryNotification — metoda</span><span class="sxs-lookup"><span data-stu-id="54dd7-107">OnMemoryNotification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)|<span data-ttu-id="54dd7-108">Powiadamia środowisko uruchomieniowe języka wspólnego (CLR) obciążenia pamięci na komputerze.</span><span class="sxs-lookup"><span data-stu-id="54dd7-108">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="54dd7-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="54dd7-109">Remarks</span></span>  
 <span data-ttu-id="54dd7-110">Host używa `ICLRMemoryNotificationCallback` interfejsu na żądanie, że środowisko CLR zwolnienia zasobów pamięci.</span><span class="sxs-lookup"><span data-stu-id="54dd7-110">The host uses the `ICLRMemoryNotificationCallback` interface to request that the CLR free memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="54dd7-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="54dd7-111">Requirements</span></span>  
 <span data-ttu-id="54dd7-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="54dd7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="54dd7-113">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="54dd7-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="54dd7-114">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="54dd7-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="54dd7-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="54dd7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="54dd7-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="54dd7-116">See Also</span></span>  
 [<span data-ttu-id="54dd7-117">IHostMemoryManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="54dd7-117">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)  
 [<span data-ttu-id="54dd7-118">Hosting — interfejsy</span><span class="sxs-lookup"><span data-stu-id="54dd7-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)

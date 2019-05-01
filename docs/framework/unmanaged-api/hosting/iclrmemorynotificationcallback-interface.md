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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948554"
---
# <a name="iclrmemorynotificationcallback-interface"></a><span data-ttu-id="b1922-102">ICLRMemoryNotificationCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b1922-102">ICLRMemoryNotificationCallback Interface</span></span>
<span data-ttu-id="b1922-103">Zezwalaj hostowi na warunki wykorzystanie pamięci raportu przy użyciu podejścia, podobnie jak w przypadku Win32 `CreateMemoryResourceNotification` funkcji.</span><span class="sxs-lookup"><span data-stu-id="b1922-103">Allows the host to report memory pressure conditions using an approach similar to that of the Win32 `CreateMemoryResourceNotification` function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b1922-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b1922-104">Methods</span></span>  
  
|<span data-ttu-id="b1922-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b1922-105">Method</span></span>|<span data-ttu-id="b1922-106">Opis</span><span class="sxs-lookup"><span data-stu-id="b1922-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b1922-107">OnMemoryNotification, metoda</span><span class="sxs-lookup"><span data-stu-id="b1922-107">OnMemoryNotification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)|<span data-ttu-id="b1922-108">Powiadamia środowisko uruchomieniowe języka wspólnego (CLR) obciążenia pamięci na komputerze.</span><span class="sxs-lookup"><span data-stu-id="b1922-108">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1922-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b1922-109">Remarks</span></span>  
 <span data-ttu-id="b1922-110">Host używa `ICLRMemoryNotificationCallback` interfejsu do żądania, że środowisko CLR Zwolnij zasoby pamięci.</span><span class="sxs-lookup"><span data-stu-id="b1922-110">The host uses the `ICLRMemoryNotificationCallback` interface to request that the CLR free memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1922-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b1922-111">Requirements</span></span>  
 <span data-ttu-id="b1922-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1922-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1922-113">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="b1922-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="b1922-114">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="b1922-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="b1922-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1922-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1922-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b1922-116">See also</span></span>

- [<span data-ttu-id="b1922-117">IHostMemoryManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="b1922-117">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="b1922-118">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="b1922-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)

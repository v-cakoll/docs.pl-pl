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
ms.openlocfilehash: e980356ad592e137df7d08dadd77431b0e295380
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141003"
---
# <a name="iclrmemorynotificationcallback-interface"></a><span data-ttu-id="f08a7-102">ICLRMemoryNotificationCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f08a7-102">ICLRMemoryNotificationCallback Interface</span></span>
<span data-ttu-id="f08a7-103">Umożliwia hostowi zgłaszanie warunków ciśnienia pamięci przy użyciu podejścia podobnego do funkcji Win32 `CreateMemoryResourceNotification`.</span><span class="sxs-lookup"><span data-stu-id="f08a7-103">Allows the host to report memory pressure conditions using an approach similar to that of the Win32 `CreateMemoryResourceNotification` function.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f08a7-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f08a7-104">Methods</span></span>  
  
|<span data-ttu-id="f08a7-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f08a7-105">Method</span></span>|<span data-ttu-id="f08a7-106">Opis</span><span class="sxs-lookup"><span data-stu-id="f08a7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f08a7-107">OnMemoryNotification, metoda</span><span class="sxs-lookup"><span data-stu-id="f08a7-107">OnMemoryNotification Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmemorynotificationcallback-onmemorynotification-method.md)|<span data-ttu-id="f08a7-108">Powiadamia środowisko uruchomieniowe języka wspólnego (CLR) o załadowaniu pamięci na komputerze.</span><span class="sxs-lookup"><span data-stu-id="f08a7-108">Notifies the common language runtime (CLR) of the memory load on the computer.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f08a7-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f08a7-109">Remarks</span></span>  
 <span data-ttu-id="f08a7-110">Host używa interfejsu `ICLRMemoryNotificationCallback`, aby zażądać zasobu wolnej pamięci środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="f08a7-110">The host uses the `ICLRMemoryNotificationCallback` interface to request that the CLR free memory resources.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f08a7-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f08a7-111">Requirements</span></span>  
 <span data-ttu-id="f08a7-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f08a7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f08a7-113">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="f08a7-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="f08a7-114">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="f08a7-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="f08a7-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f08a7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f08a7-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f08a7-116">See also</span></span>

- [<span data-ttu-id="f08a7-117">IHostMemoryManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="f08a7-117">IHostMemoryManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmemorymanager-interface.md)
- [<span data-ttu-id="f08a7-118">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="f08a7-118">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)

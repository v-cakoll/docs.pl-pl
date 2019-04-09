---
title: ICLRIoCompletionManager — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRIoCompletionManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRIoCompletionManager
helpviewer_keywords:
- ICLRIoCompletionManager interface [.NET Framework hosting]
ms.assetid: c6c3ace6-e5e7-4450-8cc5-a9a48208c493
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7864bb81c3b457bf8ec07cd194d24b29a42bd441
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59156068"
---
# <a name="iclriocompletionmanager-interface"></a><span data-ttu-id="436aa-102">ICLRIoCompletionManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="436aa-102">ICLRIoCompletionManager Interface</span></span>
<span data-ttu-id="436aa-103">Implementuje metody wywołania zwrotnego, która Zezwalaj hostowi na środowisko uruchomieniowe języka wspólnego (CLR) powiadomienia o stanie określonej operacji We/Wy żądań.</span><span class="sxs-lookup"><span data-stu-id="436aa-103">Implements a callback method that allows the host to notify the common language runtime (CLR) of the status of specified I/O requests.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="436aa-104">Metody</span><span class="sxs-lookup"><span data-stu-id="436aa-104">Methods</span></span>  
  
|<span data-ttu-id="436aa-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="436aa-105">Method</span></span>|<span data-ttu-id="436aa-106">Opis</span><span class="sxs-lookup"><span data-stu-id="436aa-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="436aa-107">OnComplete, metoda</span><span class="sxs-lookup"><span data-stu-id="436aa-107">OnComplete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md)|<span data-ttu-id="436aa-108">Powiadamia CLR stan żądania We/Wy, który został wykonany przy użyciu wywołania [ihostiocompletionmanager::BIND —](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="436aa-108">Notifies the CLR of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="436aa-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="436aa-109">Remarks</span></span>  
 <span data-ttu-id="436aa-110">Host implementuje abstrakcji zakończenia operacji We/Wy przy użyciu [ihostiocompletionmanager —](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="436aa-110">The host implements the I/O completion abstraction by using the [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md) interface.</span></span> <span data-ttu-id="436aa-111">Środowisko CLR sprawia, że żądania We/Wy za pośrednictwem tego interfejsu i hosta powiadamia środowiska uruchomieniowego wyniki takich żądań przy użyciu `ICLRIoCompletionManager` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="436aa-111">The CLR makes I/O requests through this interface, and the host notifies the runtime of the outcome of such requests by using the `ICLRIoCompletionManager` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="436aa-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="436aa-112">Requirements</span></span>  
 <span data-ttu-id="436aa-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="436aa-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="436aa-114">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="436aa-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="436aa-115">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="436aa-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="436aa-116">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="436aa-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="436aa-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="436aa-117">See also</span></span>

- [<span data-ttu-id="436aa-118">IHostIoCompletionManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="436aa-118">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="436aa-119">IHostThreadPoolManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="436aa-119">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
- [<span data-ttu-id="436aa-120">Hosting — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="436aa-120">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)

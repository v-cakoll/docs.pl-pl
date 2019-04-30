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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61767491"
---
# <a name="iclriocompletionmanager-interface"></a><span data-ttu-id="e034f-102">ICLRIoCompletionManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e034f-102">ICLRIoCompletionManager Interface</span></span>
<span data-ttu-id="e034f-103">Implementuje metody wywołania zwrotnego, która Zezwalaj hostowi na środowisko uruchomieniowe języka wspólnego (CLR) powiadomienia o stanie określonej operacji We/Wy żądań.</span><span class="sxs-lookup"><span data-stu-id="e034f-103">Implements a callback method that allows the host to notify the common language runtime (CLR) of the status of specified I/O requests.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e034f-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e034f-104">Methods</span></span>  
  
|<span data-ttu-id="e034f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e034f-105">Method</span></span>|<span data-ttu-id="e034f-106">Opis</span><span class="sxs-lookup"><span data-stu-id="e034f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e034f-107">OnComplete, metoda</span><span class="sxs-lookup"><span data-stu-id="e034f-107">OnComplete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md)|<span data-ttu-id="e034f-108">Powiadamia CLR stan żądania We/Wy, który został wykonany przy użyciu wywołania [ihostiocompletionmanager::BIND —](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="e034f-108">Notifies the CLR of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e034f-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e034f-109">Remarks</span></span>  
 <span data-ttu-id="e034f-110">Host implementuje abstrakcji zakończenia operacji We/Wy przy użyciu [ihostiocompletionmanager —](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="e034f-110">The host implements the I/O completion abstraction by using the [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md) interface.</span></span> <span data-ttu-id="e034f-111">Środowisko CLR sprawia, że żądania We/Wy za pośrednictwem tego interfejsu i hosta powiadamia środowiska uruchomieniowego wyniki takich żądań przy użyciu `ICLRIoCompletionManager` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="e034f-111">The CLR makes I/O requests through this interface, and the host notifies the runtime of the outcome of such requests by using the `ICLRIoCompletionManager` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e034f-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e034f-112">Requirements</span></span>  
 <span data-ttu-id="e034f-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e034f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e034f-114">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="e034f-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="e034f-115">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="e034f-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="e034f-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e034f-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e034f-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e034f-117">See also</span></span>

- [<span data-ttu-id="e034f-118">IHostIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="e034f-118">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="e034f-119">IHostThreadPoolManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="e034f-119">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
- [<span data-ttu-id="e034f-120">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="e034f-120">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)

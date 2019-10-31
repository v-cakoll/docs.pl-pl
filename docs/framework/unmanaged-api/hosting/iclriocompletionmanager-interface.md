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
ms.openlocfilehash: b63d4269a8d48ee49016a4c51d63bf81bdba8da2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141032"
---
# <a name="iclriocompletionmanager-interface"></a><span data-ttu-id="ab4d9-102">ICLRIoCompletionManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ab4d9-102">ICLRIoCompletionManager Interface</span></span>
<span data-ttu-id="ab4d9-103">Implementuje metodę wywołania zwrotnego, która umożliwia hostowi powiadamianie środowiska uruchomieniowego języka wspólnego (CLR) o stanie określonych żądań we/wy.</span><span class="sxs-lookup"><span data-stu-id="ab4d9-103">Implements a callback method that allows the host to notify the common language runtime (CLR) of the status of specified I/O requests.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ab4d9-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ab4d9-104">Methods</span></span>  
  
|<span data-ttu-id="ab4d9-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ab4d9-105">Method</span></span>|<span data-ttu-id="ab4d9-106">Opis</span><span class="sxs-lookup"><span data-stu-id="ab4d9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ab4d9-107">OnComplete, metoda</span><span class="sxs-lookup"><span data-stu-id="ab4d9-107">OnComplete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md)|<span data-ttu-id="ab4d9-108">Powiadamia CLR o stanie żądania we/wy, które zostało wykonane przy użyciu wywołania metody [IHostIoCompletionManager:: bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) .</span><span class="sxs-lookup"><span data-stu-id="ab4d9-108">Notifies the CLR of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ab4d9-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ab4d9-109">Remarks</span></span>  
 <span data-ttu-id="ab4d9-110">Host implementuje abstrakcję ukończenia we/wy przy użyciu interfejsu [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="ab4d9-110">The host implements the I/O completion abstraction by using the [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md) interface.</span></span> <span data-ttu-id="ab4d9-111">Środowisko CLR wykonuje żądania we/wy za pośrednictwem tego interfejsu, a host powiadamia środowisko uruchomieniowe o wyniku takich żądań za pomocą interfejsu `ICLRIoCompletionManager`.</span><span class="sxs-lookup"><span data-stu-id="ab4d9-111">The CLR makes I/O requests through this interface, and the host notifies the runtime of the outcome of such requests by using the `ICLRIoCompletionManager` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab4d9-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ab4d9-112">Requirements</span></span>  
 <span data-ttu-id="ab4d9-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab4d9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab4d9-114">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="ab4d9-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ab4d9-115">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="ab4d9-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ab4d9-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab4d9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab4d9-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ab4d9-117">See also</span></span>

- [<span data-ttu-id="ab4d9-118">IHostIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ab4d9-118">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="ab4d9-119">IHostThreadPoolManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ab4d9-119">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)
- [<span data-ttu-id="ab4d9-120">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="ab4d9-120">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)

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
ms.openlocfilehash: 822b51531b7afc1c824c74b9580d9208e347e13b
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703555"
---
# <a name="iclriocompletionmanager-interface"></a><span data-ttu-id="a3479-102">ICLRIoCompletionManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a3479-102">ICLRIoCompletionManager Interface</span></span>
<span data-ttu-id="a3479-103">Implementuje metodę wywołania zwrotnego, która umożliwia hostowi powiadamianie środowiska uruchomieniowego języka wspólnego (CLR) o stanie określonych żądań we/wy.</span><span class="sxs-lookup"><span data-stu-id="a3479-103">Implements a callback method that allows the host to notify the common language runtime (CLR) of the status of specified I/O requests.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a3479-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a3479-104">Methods</span></span>  
  
|<span data-ttu-id="a3479-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a3479-105">Method</span></span>|<span data-ttu-id="a3479-106">Opis</span><span class="sxs-lookup"><span data-stu-id="a3479-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a3479-107">OnComplete, metoda</span><span class="sxs-lookup"><span data-stu-id="a3479-107">OnComplete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md)|<span data-ttu-id="a3479-108">Powiadamia CLR o stanie żądania we/wy, które zostało wykonane przy użyciu wywołania metody [IHostIoCompletionManager:: bind](ihostiocompletionmanager-bind-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a3479-108">Notifies the CLR of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](ihostiocompletionmanager-bind-method.md) method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a3479-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a3479-109">Remarks</span></span>  
 <span data-ttu-id="a3479-110">Host implementuje abstrakcję ukończenia we/wy przy użyciu interfejsu [IHostIoCompletionManager](ihostiocompletionmanager-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="a3479-110">The host implements the I/O completion abstraction by using the [IHostIoCompletionManager](ihostiocompletionmanager-interface.md) interface.</span></span> <span data-ttu-id="a3479-111">Środowisko CLR wykonuje żądania we/wy za pośrednictwem tego interfejsu, a host powiadamia środowisko uruchomieniowe o wyniku takich żądań za pomocą `ICLRIoCompletionManager` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a3479-111">The CLR makes I/O requests through this interface, and the host notifies the runtime of the outcome of such requests by using the `ICLRIoCompletionManager` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a3479-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a3479-112">Requirements</span></span>  
 <span data-ttu-id="a3479-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a3479-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a3479-114">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="a3479-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a3479-115">**Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="a3479-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a3479-116">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a3479-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3479-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a3479-117">See also</span></span>

- [<span data-ttu-id="a3479-118">IHostIoCompletionManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="a3479-118">IHostIoCompletionManager Interface</span></span>](ihostiocompletionmanager-interface.md)
- [<span data-ttu-id="a3479-119">IHostThreadPoolManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="a3479-119">IHostThreadPoolManager Interface</span></span>](ihostthreadpoolmanager-interface.md)
- [<span data-ttu-id="a3479-120">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="a3479-120">Hosting Interfaces</span></span>](hosting-interfaces.md)

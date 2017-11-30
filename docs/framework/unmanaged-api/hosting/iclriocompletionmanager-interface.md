---
title: "ICLRIoCompletionManager — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRIoCompletionManager
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRIoCompletionManager
helpviewer_keywords: ICLRIoCompletionManager interface [.NET Framework hosting]
ms.assetid: c6c3ace6-e5e7-4450-8cc5-a9a48208c493
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dbff3c39da2a18ab45f0ea03d1e1588aa61c7c3c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="iclriocompletionmanager-interface"></a><span data-ttu-id="a2b22-102">ICLRIoCompletionManager — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a2b22-102">ICLRIoCompletionManager Interface</span></span>
<span data-ttu-id="a2b22-103">Implementuje metody wywołania zwrotnego, umożliwiający hosta powiadomiono środowisko uruchomieniowe języka wspólnego (CLR) stanu określonego we/wy na żądania.</span><span class="sxs-lookup"><span data-stu-id="a2b22-103">Implements a callback method that allows the host to notify the common language runtime (CLR) of the status of specified I/O requests.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a2b22-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a2b22-104">Methods</span></span>  
  
|<span data-ttu-id="a2b22-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a2b22-105">Method</span></span>|<span data-ttu-id="a2b22-106">Opis</span><span class="sxs-lookup"><span data-stu-id="a2b22-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a2b22-107">OnComplete — metoda</span><span class="sxs-lookup"><span data-stu-id="a2b22-107">OnComplete Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclriocompletionmanager-oncomplete-method.md)|<span data-ttu-id="a2b22-108">Powiadamia CLR stan żądania We/Wy, który został utworzony za pomocą wywołania [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="a2b22-108">Notifies the CLR of the status of an I/O request that was made by using a call to the [IHostIoCompletionManager::Bind](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-bind-method.md) method.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a2b22-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a2b22-109">Remarks</span></span>  
 <span data-ttu-id="a2b22-110">Host implementuje abstrakcji zakończenia We/Wy przy użyciu [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a2b22-110">The host implements the I/O completion abstraction by using the [IHostIoCompletionManager](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md) interface.</span></span> <span data-ttu-id="a2b22-111">CLR zgłasza żądania dotyczące operacji We/Wy za pośrednictwem tego interfejsu, a host powiadamia środowiska wykonawczego o wynikach takich żądań przy użyciu `ICLRIoCompletionManager` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a2b22-111">The CLR makes I/O requests through this interface, and the host notifies the runtime of the outcome of such requests by using the `ICLRIoCompletionManager` interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2b22-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a2b22-112">Requirements</span></span>  
 <span data-ttu-id="a2b22-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2b22-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2b22-114">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="a2b22-114">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="a2b22-115">**Biblioteka:** uwzględnione jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a2b22-115">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="a2b22-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2b22-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2b22-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a2b22-117">See Also</span></span>  
 [<span data-ttu-id="a2b22-118">IHostIoCompletionManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="a2b22-118">IHostIoCompletionManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostiocompletionmanager-interface.md)  
 [<span data-ttu-id="a2b22-119">IHostThreadPoolManager — interfejs</span><span class="sxs-lookup"><span data-stu-id="a2b22-119">IHostThreadPoolManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostthreadpoolmanager-interface.md)  
 [<span data-ttu-id="a2b22-120">Hosting — interfejsy</span><span class="sxs-lookup"><span data-stu-id="a2b22-120">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)

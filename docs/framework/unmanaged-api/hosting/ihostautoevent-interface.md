---
title: IHostAutoEvent — Interfejs
ms.date: 03/30/2017
api_name:
- IHostAutoEvent
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAutoEvent
helpviewer_keywords:
- IHostAutoEvent interface [.NET Framework hosting]
ms.assetid: 6c1d15c1-a80a-4ee9-b1e4-6e859db6575a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2b8cccf395e77c7dfefb85302b522d7e9398ffca
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54730025"
---
# <a name="ihostautoevent-interface"></a><span data-ttu-id="ebdb6-102">IHostAutoEvent — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ebdb6-102">IHostAutoEvent Interface</span></span>
<span data-ttu-id="ebdb6-103">Udostępnia reprezentację wdrożenia hosta zdarzenie z resetowaniem automatycznym.</span><span class="sxs-lookup"><span data-stu-id="ebdb6-103">Provides a representation of the host's implementation of an auto-reset event.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ebdb6-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ebdb6-104">Methods</span></span>  
  
|<span data-ttu-id="ebdb6-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ebdb6-105">Method</span></span>|<span data-ttu-id="ebdb6-106">Opis</span><span class="sxs-lookup"><span data-stu-id="ebdb6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ebdb6-107">Set, metoda</span><span class="sxs-lookup"><span data-stu-id="ebdb6-107">Set Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-set-method.md)|<span data-ttu-id="ebdb6-108">Ustawia bieżący `IHostAutoEvent` wystąpienie do sygnalizowanego stanu.</span><span class="sxs-lookup"><span data-stu-id="ebdb6-108">Sets the current `IHostAutoEvent` instance to a signaled state.</span></span>|  
|[<span data-ttu-id="ebdb6-109">Wait, metoda</span><span class="sxs-lookup"><span data-stu-id="ebdb6-109">Wait Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostautoevent-wait-method.md)|<span data-ttu-id="ebdb6-110">Powoduje, że bieżący `IHostAutoEvent` wystąpienie poczekać, aż zdarzenia jest właścicielem lub określoną ilość czasu upłynie.</span><span class="sxs-lookup"><span data-stu-id="ebdb6-110">Causes the current `IHostAutoEvent` instance to wait until the event is owned or a specified amount of time elapses.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ebdb6-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ebdb6-111">Requirements</span></span>  
 <span data-ttu-id="ebdb6-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ebdb6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ebdb6-113">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="ebdb6-113">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="ebdb6-114">**Biblioteka:** Dołączony jako zasób w MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ebdb6-114">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="ebdb6-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ebdb6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebdb6-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ebdb6-116">See also</span></span>
- [<span data-ttu-id="ebdb6-117">ICLRSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ebdb6-117">ICLRSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrsyncmanager-interface.md)
- [<span data-ttu-id="ebdb6-118">IHostManualEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="ebdb6-118">IHostManualEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostmanualevent-interface.md)
- [<span data-ttu-id="ebdb6-119">IHostSyncManager, interfejs</span><span class="sxs-lookup"><span data-stu-id="ebdb6-119">IHostSyncManager Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/ihostsyncmanager-interface.md)
- [<span data-ttu-id="ebdb6-120">Hosting, interfejsy</span><span class="sxs-lookup"><span data-stu-id="ebdb6-120">Hosting Interfaces</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)

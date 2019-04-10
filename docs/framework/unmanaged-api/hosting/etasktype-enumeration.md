---
title: ETaskType — Wyliczenie
ms.date: 03/30/2017
api_name:
- ETaskType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ETaskType
helpviewer_keywords:
- ETaskType enumeration [.NET Framework hosting]
ms.assetid: aa527b31-89d4-41f2-ad6f-63b76950b7df
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f256195a4cd5b18f568e05156db867aa5dba9161
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59229826"
---
# <a name="etasktype-enumeration"></a><span data-ttu-id="7cf84-102">ETaskType — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="7cf84-102">ETaskType Enumeration</span></span>
<span data-ttu-id="7cf84-103">Zawiera wartości, które wskazują na typ zadania, który jest reprezentowany przez [iclrtask —](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) lub [ihosttask —](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="7cf84-103">Contains values that indicate the type of task that is represented by either an [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) or an [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cf84-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7cf84-104">Syntax</span></span>  
  
```  
typedef enum ETaskType {  
    TT_DEBUGGERHELPER           = 0x1,  
    TT_GC                       = 0x2,  
    TT_FINALIZER                = 0x4,  
    TT_THREADPOOL_TIMER         = 0x8,  
    TT_THREADPOOL_GATE          = 0x10,  
    TT_THREADPOOL_WORKER        = 0x20,  
    TT_THREADPOOL_IOCOMPLETION  = 0x40,  
    TT_ADUNLOAD                 = 0x80,  
    TT_USER                     = 0x100,  
    TT_THREADPOOL_WAIT          = 0x200,  
    TT_UNKNOWN                  = 0x80000000  
} ETaskType;  
```  
  
## <a name="members"></a><span data-ttu-id="7cf84-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="7cf84-105">Members</span></span>  
  
|<span data-ttu-id="7cf84-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="7cf84-106">Member</span></span>|<span data-ttu-id="7cf84-107">Opis</span><span class="sxs-lookup"><span data-stu-id="7cf84-107">Description</span></span>|  
|------------|-----------------|  
|`TT_ADUNLOAD`|<span data-ttu-id="7cf84-108">Interfejs reprezentuje zadanie Zwalnianie domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7cf84-108">The interface represents an application domain unloading task.</span></span>|  
|`TT_DEBUGGERHELPER`|<span data-ttu-id="7cf84-109">Interfejs reprezentuje zadanie Pomocnik debugera.</span><span class="sxs-lookup"><span data-stu-id="7cf84-109">The interface represents a debugger helper task.</span></span>|  
|`TT_FINALIZER`|<span data-ttu-id="7cf84-110">Interfejs reprezentuje zadanie finalizatora.</span><span class="sxs-lookup"><span data-stu-id="7cf84-110">The interface represents a finalizer task.</span></span>|  
|`TT_GC`|<span data-ttu-id="7cf84-111">Interfejs reprezentuje zadanie odzyskiwania pamięci.</span><span class="sxs-lookup"><span data-stu-id="7cf84-111">The interface represents a garbage collection task.</span></span>|  
|`TT_THREADPOOL_GATE`|<span data-ttu-id="7cf84-112">Interfejs reprezentuje zadanie wątku bramy.</span><span class="sxs-lookup"><span data-stu-id="7cf84-112">The interface represents a gate thread task.</span></span>|  
|`TT_THREADPOOL_IOCOMPLETION`|<span data-ttu-id="7cf84-113">Interfejs reprezentuje operacji We/Wy wątek zadanie lub zadanie wątków portu zakończenia.</span><span class="sxs-lookup"><span data-stu-id="7cf84-113">The interface represents an I/O thread task or a completion port thread task.</span></span>|  
|`TT_THREADPOOL_TIMER`|<span data-ttu-id="7cf84-114">Interfejs reprezentuje zadanie wątków czasomierza.</span><span class="sxs-lookup"><span data-stu-id="7cf84-114">The interface represents a timer thread task.</span></span>|  
|`TT_THREADPOOL_WAIT`|<span data-ttu-id="7cf84-115">Interfejs reprezentuje zadanie wątku oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="7cf84-115">The interface represents a wait thread task.</span></span>|  
|`TT_THREADPOOL_WORKER`|<span data-ttu-id="7cf84-116">Interfejs reprezentuje zadania wątek procesu roboczego.</span><span class="sxs-lookup"><span data-stu-id="7cf84-116">The interface represents a worker thread task.</span></span>|  
|`TT_UNKNOWN`|<span data-ttu-id="7cf84-117">Zadanie jest nieznany.</span><span class="sxs-lookup"><span data-stu-id="7cf84-117">The task is unknown.</span></span>|  
|`TT_USER`|<span data-ttu-id="7cf84-118">Interfejs reprezentuje zadanie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="7cf84-118">The interface represents a user task.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7cf84-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7cf84-119">Requirements</span></span>  
 <span data-ttu-id="7cf84-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7cf84-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7cf84-121">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7cf84-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7cf84-122">**Biblioteka:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7cf84-122">**Library:** MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="7cf84-123">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="7cf84-123">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7cf84-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7cf84-124">See also</span></span>

- [<span data-ttu-id="7cf84-125">Hosting — Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="7cf84-125">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)

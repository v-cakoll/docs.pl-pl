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
ms.openlocfilehash: 73098077e3860d3f4a8a02921ecedf8dff24165b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774050"
---
# <a name="etasktype-enumeration"></a><span data-ttu-id="27963-102">ETaskType — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="27963-102">ETaskType Enumeration</span></span>
<span data-ttu-id="27963-103">Zawiera wartości, które wskazują na typ zadania, który jest reprezentowany przez [iclrtask —](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) lub [ihosttask —](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="27963-103">Contains values that indicate the type of task that is represented by either an [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) or an [IHostTask](../../../../docs/framework/unmanaged-api/hosting/ihosttask-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27963-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="27963-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="27963-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="27963-105">Members</span></span>  
  
|<span data-ttu-id="27963-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="27963-106">Member</span></span>|<span data-ttu-id="27963-107">Opis</span><span class="sxs-lookup"><span data-stu-id="27963-107">Description</span></span>|  
|------------|-----------------|  
|`TT_ADUNLOAD`|<span data-ttu-id="27963-108">Interfejs reprezentuje zadanie Zwalnianie domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="27963-108">The interface represents an application domain unloading task.</span></span>|  
|`TT_DEBUGGERHELPER`|<span data-ttu-id="27963-109">Interfejs reprezentuje zadanie Pomocnik debugera.</span><span class="sxs-lookup"><span data-stu-id="27963-109">The interface represents a debugger helper task.</span></span>|  
|`TT_FINALIZER`|<span data-ttu-id="27963-110">Interfejs reprezentuje zadanie finalizatora.</span><span class="sxs-lookup"><span data-stu-id="27963-110">The interface represents a finalizer task.</span></span>|  
|`TT_GC`|<span data-ttu-id="27963-111">Interfejs reprezentuje zadanie odzyskiwania pamięci.</span><span class="sxs-lookup"><span data-stu-id="27963-111">The interface represents a garbage collection task.</span></span>|  
|`TT_THREADPOOL_GATE`|<span data-ttu-id="27963-112">Interfejs reprezentuje zadanie wątku bramy.</span><span class="sxs-lookup"><span data-stu-id="27963-112">The interface represents a gate thread task.</span></span>|  
|`TT_THREADPOOL_IOCOMPLETION`|<span data-ttu-id="27963-113">Interfejs reprezentuje operacji We/Wy wątek zadanie lub zadanie wątków portu zakończenia.</span><span class="sxs-lookup"><span data-stu-id="27963-113">The interface represents an I/O thread task or a completion port thread task.</span></span>|  
|`TT_THREADPOOL_TIMER`|<span data-ttu-id="27963-114">Interfejs reprezentuje zadanie wątków czasomierza.</span><span class="sxs-lookup"><span data-stu-id="27963-114">The interface represents a timer thread task.</span></span>|  
|`TT_THREADPOOL_WAIT`|<span data-ttu-id="27963-115">Interfejs reprezentuje zadanie wątku oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="27963-115">The interface represents a wait thread task.</span></span>|  
|`TT_THREADPOOL_WORKER`|<span data-ttu-id="27963-116">Interfejs reprezentuje zadania wątek procesu roboczego.</span><span class="sxs-lookup"><span data-stu-id="27963-116">The interface represents a worker thread task.</span></span>|  
|`TT_UNKNOWN`|<span data-ttu-id="27963-117">Zadanie jest nieznany.</span><span class="sxs-lookup"><span data-stu-id="27963-117">The task is unknown.</span></span>|  
|`TT_USER`|<span data-ttu-id="27963-118">Interfejs reprezentuje zadanie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="27963-118">The interface represents a user task.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="27963-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="27963-119">Requirements</span></span>  
 <span data-ttu-id="27963-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27963-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27963-121">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="27963-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="27963-122">**Biblioteka:** MSCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="27963-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="27963-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27963-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27963-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="27963-124">See also</span></span>

- [<span data-ttu-id="27963-125">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="27963-125">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)

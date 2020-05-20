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
ms.openlocfilehash: 435d23d4a56d6ea98e3d368f0a5aa37c73e31d96
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616167"
---
# <a name="etasktype-enumeration"></a><span data-ttu-id="2e2ca-102">ETaskType — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="2e2ca-102">ETaskType Enumeration</span></span>
<span data-ttu-id="2e2ca-103">Zawiera wartości wskazujące typ zadania reprezentowanego przez interfejs [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) lub [IHostTask](ihosttask-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="2e2ca-103">Contains values that indicate the type of task that is represented by either an [ICLRTask](../../../../docs/framework/unmanaged-api/hosting/iclrtask-interface.md) or an [IHostTask](ihosttask-interface.md) interface.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e2ca-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2e2ca-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="2e2ca-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="2e2ca-105">Members</span></span>  
  
|<span data-ttu-id="2e2ca-106">Członek</span><span class="sxs-lookup"><span data-stu-id="2e2ca-106">Member</span></span>|<span data-ttu-id="2e2ca-107">Opis</span><span class="sxs-lookup"><span data-stu-id="2e2ca-107">Description</span></span>|  
|------------|-----------------|  
|`TT_ADUNLOAD`|<span data-ttu-id="2e2ca-108">Interfejs reprezentuje zadanie wyładowywania domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="2e2ca-108">The interface represents an application domain unloading task.</span></span>|  
|`TT_DEBUGGERHELPER`|<span data-ttu-id="2e2ca-109">Interfejs reprezentuje zadanie pomocnika debugera.</span><span class="sxs-lookup"><span data-stu-id="2e2ca-109">The interface represents a debugger helper task.</span></span>|  
|`TT_FINALIZER`|<span data-ttu-id="2e2ca-110">Interfejs reprezentuje zadanie finalizatora.</span><span class="sxs-lookup"><span data-stu-id="2e2ca-110">The interface represents a finalizer task.</span></span>|  
|`TT_GC`|<span data-ttu-id="2e2ca-111">Interfejs reprezentuje zadanie wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="2e2ca-111">The interface represents a garbage collection task.</span></span>|  
|`TT_THREADPOOL_GATE`|<span data-ttu-id="2e2ca-112">Interfejs reprezentuje zadanie wątku bramy.</span><span class="sxs-lookup"><span data-stu-id="2e2ca-112">The interface represents a gate thread task.</span></span>|  
|`TT_THREADPOOL_IOCOMPLETION`|<span data-ttu-id="2e2ca-113">Interfejs reprezentuje zadanie wątku we/wy lub zadanie wątku zakończenia.</span><span class="sxs-lookup"><span data-stu-id="2e2ca-113">The interface represents an I/O thread task or a completion port thread task.</span></span>|  
|`TT_THREADPOOL_TIMER`|<span data-ttu-id="2e2ca-114">Interfejs reprezentuje zadanie wątku czasomierza.</span><span class="sxs-lookup"><span data-stu-id="2e2ca-114">The interface represents a timer thread task.</span></span>|  
|`TT_THREADPOOL_WAIT`|<span data-ttu-id="2e2ca-115">Interfejs reprezentuje zadanie wątku oczekiwania.</span><span class="sxs-lookup"><span data-stu-id="2e2ca-115">The interface represents a wait thread task.</span></span>|  
|`TT_THREADPOOL_WORKER`|<span data-ttu-id="2e2ca-116">Interfejs reprezentuje zadanie wątku roboczego.</span><span class="sxs-lookup"><span data-stu-id="2e2ca-116">The interface represents a worker thread task.</span></span>|  
|`TT_UNKNOWN`|<span data-ttu-id="2e2ca-117">Zadanie jest nieznane.</span><span class="sxs-lookup"><span data-stu-id="2e2ca-117">The task is unknown.</span></span>|  
|`TT_USER`|<span data-ttu-id="2e2ca-118">Interfejs reprezentuje zadanie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="2e2ca-118">The interface represents a user task.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="2e2ca-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2e2ca-119">Requirements</span></span>  
 <span data-ttu-id="2e2ca-120">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2e2ca-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2e2ca-121">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="2e2ca-121">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="2e2ca-122">**Biblioteka:** MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="2e2ca-122">**Library:** MSCorEE.dll</span></span>  
  
 <span data-ttu-id="2e2ca-123">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2e2ca-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e2ca-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2e2ca-124">See also</span></span>

- [<span data-ttu-id="2e2ca-125">Hosting — Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="2e2ca-125">Hosting Enumerations</span></span>](hosting-enumerations.md)

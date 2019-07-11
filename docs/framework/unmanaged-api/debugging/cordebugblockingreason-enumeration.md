---
title: CorDebugBlockingReason — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorDebugBlockingReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugBlockingReason
helpviewer_keywords:
- CorDebugBlockingReason enumeration [.NET Framework debugging]
ms.assetid: a6ac2531-ddfe-46fd-88fe-8b1eabe0b255
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3ea71439c9a6c494c218a7cfc18508f4f8173b03
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740389"
---
# <a name="cordebugblockingreason-enumeration"></a><span data-ttu-id="4526e-102">CorDebugBlockingReason — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="4526e-102">CorDebugBlockingReason Enumeration</span></span>
<span data-ttu-id="4526e-103">Określa przyczyny, dlaczego wątek może stać się zablokowany dla danego obiektu.</span><span class="sxs-lookup"><span data-stu-id="4526e-103">Specifies the reasons why a thread may become blocked on a given object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4526e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4526e-104">Syntax</span></span>  
  
```cpp  
Typedef enum CorDebugBlockingReason  
{  
   BLOCKING_NONE = 0  
   BLOCKING_MONITOR_CRITICAL_SECTION = 1  
   BLOCKING_MONITOR_EVENT = 2  
}  CorDebugBlockingReason;  
```  
  
## <a name="members"></a><span data-ttu-id="4526e-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="4526e-105">Members</span></span>  
  
|<span data-ttu-id="4526e-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="4526e-106">Member</span></span>|<span data-ttu-id="4526e-107">Opis</span><span class="sxs-lookup"><span data-stu-id="4526e-107">Description</span></span>|  
|------------|-----------------|  
|`BLOCKING_NONE`|<span data-ttu-id="4526e-108">Wyłącznie do użytku wewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="4526e-108">Internal use only.</span></span>|  
|`BLOCKING_MONITOR_CRITICAL_SECTION`|<span data-ttu-id="4526e-109">Wątek próbuje pobrać sekcję krytyczną, skojarzonego z blokadą monitora na obiekcie.</span><span class="sxs-lookup"><span data-stu-id="4526e-109">A thread is trying to acquire the critical section that is associated with the monitor lock on an object.</span></span> <span data-ttu-id="4526e-110">Zazwyczaj ten błąd występuje podczas wywołania jednej z <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> lub <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="4526e-110">Typically, this occurs when you call one of the <xref:System.Threading.Monitor.Enter%2A?displayProperty=nameWithType> or <xref:System.Threading.Monitor.TryEnter%2A?displayProperty=nameWithType> methods.</span></span>|  
|`BLOCKING_MONITOR_EVENT`|<span data-ttu-id="4526e-111">Wątek jest oczekiwanie na zdarzenia skojarzonego z blokadą monitor dla obiektu.</span><span class="sxs-lookup"><span data-stu-id="4526e-111">A thread is waiting on the event that is associated with a monitor lock for an object.</span></span> <span data-ttu-id="4526e-112">Zazwyczaj ten błąd występuje podczas wywołania jednej z <xref:System.Threading.Monitor?displayProperty=nameWithType> `Wait` metody.</span><span class="sxs-lookup"><span data-stu-id="4526e-112">Typically, this occurs when you call one of the <xref:System.Threading.Monitor?displayProperty=nameWithType>`Wait` methods.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4526e-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4526e-113">Remarks</span></span>  
 <span data-ttu-id="4526e-114">Gdy `BLOCKING_MONITOR_CRITICAL_SECTION` lub `BLOCKING_MONITOR_EVENT` elementu członkowskiego jest używany w [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) struktury, `pBlockingObject` składowej struktury punktami interfejs "ICorDebugValue", który reprezentuje obiekt, który jest wprowadzanych .</span><span class="sxs-lookup"><span data-stu-id="4526e-114">When the `BLOCKING_MONITOR_CRITICAL_SECTION` or `BLOCKING_MONITOR_EVENT` member is used in a [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structure, the `pBlockingObject` member of the structure points to an "ICorDebugValue" interface that represents the object that is being entered.</span></span> <span data-ttu-id="4526e-115">Również musi implementować [icordebugheapvalue3 —](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-interface.md) interfejsu.</span><span class="sxs-lookup"><span data-stu-id="4526e-115">It is also guaranteed to implement the [ICorDebugHeapValue3](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-interface.md) interface.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4526e-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4526e-116">Requirements</span></span>  
 <span data-ttu-id="4526e-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4526e-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4526e-118">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4526e-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4526e-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4526e-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4526e-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4526e-120">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4526e-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4526e-121">See also</span></span>

- [<span data-ttu-id="4526e-122">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="4526e-122">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="4526e-123">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="4526e-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

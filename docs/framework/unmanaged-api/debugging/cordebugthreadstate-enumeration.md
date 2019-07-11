---
title: CorDebugThreadState — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorDebugThreadState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugThreadState
helpviewer_keywords:
- CorDebugThreadState enumeration [.NET Framework debugging]
ms.assetid: a3ccdf18-4ec6-494d-9024-48e5c8c724f5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ce252f5a4b5fbcdbbc7b70c8b1c829490f8f63e5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739530"
---
# <a name="cordebugthreadstate-enumeration"></a><span data-ttu-id="12024-102">CorDebugThreadState — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="12024-102">CorDebugThreadState Enumeration</span></span>
<span data-ttu-id="12024-103">Określa stan wątku do debugowania.</span><span class="sxs-lookup"><span data-stu-id="12024-103">Specifies the state of a thread for debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12024-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="12024-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugThreadState {  
    THREAD_RUN,  
    THREAD_SUSPEND  
} CorDebugThreadState;  
```  
  
## <a name="members"></a><span data-ttu-id="12024-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="12024-105">Members</span></span>  
  
|<span data-ttu-id="12024-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="12024-106">Member</span></span>|<span data-ttu-id="12024-107">Opis</span><span class="sxs-lookup"><span data-stu-id="12024-107">Description</span></span>|  
|------------|-----------------|  
|`THREAD_RUN`|<span data-ttu-id="12024-108">Wątek uruchamia się za darmo, chyba że wystąpi zdarzenie debugowania.</span><span class="sxs-lookup"><span data-stu-id="12024-108">The thread runs freely, unless a debug event occurs.</span></span>|  
|`THREAD_SUSPEND`|<span data-ttu-id="12024-109">Nie można uruchomić wątku.</span><span class="sxs-lookup"><span data-stu-id="12024-109">The thread cannot run.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="12024-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="12024-110">Remarks</span></span>  
 <span data-ttu-id="12024-111">Debuger używa `CorDebugThreadState` wyliczeniu, aby kontrolować wykonywanie wątku.</span><span class="sxs-lookup"><span data-stu-id="12024-111">The debugger uses the `CorDebugThreadState` enumeration to control a thread's execution.</span></span> <span data-ttu-id="12024-112">Stan wątku można ustawić za pomocą [ICorDebugThread::SetDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md) lub [ICorDebugController::SetAllThreadsDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="12024-112">The state of a thread can be set by using the [ICorDebugThread::SetDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md) or [ICorDebugController::SetAllThreadsDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md) method.</span></span>  
  
 <span data-ttu-id="12024-113">Wywołanie zwrotne udostępniane [hostującego interfejs API](../../../../docs/framework/unmanaged-api/hosting/index.md) umożliwia przekazywanie wiadomości, przerwane stanu nie jest potrzebna.</span><span class="sxs-lookup"><span data-stu-id="12024-113">A callback provided to the [hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md) enables message pumping, so an interrupted state is not needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12024-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="12024-114">Requirements</span></span>  
 <span data-ttu-id="12024-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12024-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12024-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="12024-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="12024-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="12024-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="12024-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12024-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12024-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="12024-119">See also</span></span>

- [<span data-ttu-id="12024-120">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="12024-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)

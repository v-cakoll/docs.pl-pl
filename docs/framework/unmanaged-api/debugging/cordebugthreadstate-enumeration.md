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
ms.openlocfilehash: ba8bca6d14308284c869b923853f7e27e045bca5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33402942"
---
# <a name="cordebugthreadstate-enumeration"></a><span data-ttu-id="5c973-102">CorDebugThreadState — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="5c973-102">CorDebugThreadState Enumeration</span></span>
<span data-ttu-id="5c973-103">Określa stan wątku do debugowania.</span><span class="sxs-lookup"><span data-stu-id="5c973-103">Specifies the state of a thread for debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c973-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5c973-104">Syntax</span></span>  
  
```  
typedef enum CorDebugThreadState {  
    THREAD_RUN,  
    THREAD_SUSPEND  
} CorDebugThreadState;  
```  
  
## <a name="members"></a><span data-ttu-id="5c973-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="5c973-105">Members</span></span>  
  
|<span data-ttu-id="5c973-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="5c973-106">Member</span></span>|<span data-ttu-id="5c973-107">Opis</span><span class="sxs-lookup"><span data-stu-id="5c973-107">Description</span></span>|  
|------------|-----------------|  
|`THREAD_RUN`|<span data-ttu-id="5c973-108">Wątek jest uruchamiana za darmo, chyba że wystąpi zdarzenie debugowania.</span><span class="sxs-lookup"><span data-stu-id="5c973-108">The thread runs freely, unless a debug event occurs.</span></span>|  
|`THREAD_SUSPEND`|<span data-ttu-id="5c973-109">Nie można uruchomić wątku.</span><span class="sxs-lookup"><span data-stu-id="5c973-109">The thread cannot run.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5c973-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5c973-110">Remarks</span></span>  
 <span data-ttu-id="5c973-111">Debuger używa `CorDebugThreadState` wyliczeniu, aby kontrolować wykonywanie wątku.</span><span class="sxs-lookup"><span data-stu-id="5c973-111">The debugger uses the `CorDebugThreadState` enumeration to control a thread's execution.</span></span> <span data-ttu-id="5c973-112">Można ustawić stan wątku przy użyciu [ICorDebugThread::SetDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md) lub [ICorDebugController::SetAllThreadsDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="5c973-112">The state of a thread can be set by using the [ICorDebugThread::SetDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md) or [ICorDebugController::SetAllThreadsDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md) method.</span></span>  
  
 <span data-ttu-id="5c973-113">Wywołanie zwrotne przekazane do [hostingu API](../../../../docs/framework/unmanaged-api/hosting/index.md) umożliwia przekazywanie wiadomości, więc stan przerwania nie jest potrzebny.</span><span class="sxs-lookup"><span data-stu-id="5c973-113">A callback provided to the [hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md) enables message pumping, so an interrupted state is not needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5c973-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5c973-114">Requirements</span></span>  
 <span data-ttu-id="5c973-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5c973-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5c973-116">**Nagłówek:** CorDebug.idl, CorDegug.h</span><span class="sxs-lookup"><span data-stu-id="5c973-116">**Header:** CorDebug.idl, CorDegug.h</span></span>  
  
 <span data-ttu-id="5c973-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5c973-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5c973-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5c973-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c973-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5c973-119">See Also</span></span>  
 [<span data-ttu-id="5c973-120">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="5c973-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)

---
title: "CorDebugThreadState — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a5363282f2efed003238014390f50c448c529ce2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugthreadstate-enumeration"></a><span data-ttu-id="c4b94-102">CorDebugThreadState — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="c4b94-102">CorDebugThreadState Enumeration</span></span>
<span data-ttu-id="c4b94-103">Określa stan wątku do debugowania.</span><span class="sxs-lookup"><span data-stu-id="c4b94-103">Specifies the state of a thread for debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4b94-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c4b94-104">Syntax</span></span>  
  
```  
typedef enum CorDebugThreadState {  
    THREAD_RUN,  
    THREAD_SUSPEND  
} CorDebugThreadState;  
```  
  
## <a name="members"></a><span data-ttu-id="c4b94-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="c4b94-105">Members</span></span>  
  
|<span data-ttu-id="c4b94-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="c4b94-106">Member</span></span>|<span data-ttu-id="c4b94-107">Opis</span><span class="sxs-lookup"><span data-stu-id="c4b94-107">Description</span></span>|  
|------------|-----------------|  
|`THREAD_RUN`|<span data-ttu-id="c4b94-108">Wątek jest uruchamiana za darmo, chyba że wystąpi zdarzenie debugowania.</span><span class="sxs-lookup"><span data-stu-id="c4b94-108">The thread runs freely, unless a debug event occurs.</span></span>|  
|`THREAD_SUSPEND`|<span data-ttu-id="c4b94-109">Nie można uruchomić wątku.</span><span class="sxs-lookup"><span data-stu-id="c4b94-109">The thread cannot run.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4b94-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c4b94-110">Remarks</span></span>  
 <span data-ttu-id="c4b94-111">Debuger używa `CorDebugThreadState` wyliczeniu, aby kontrolować wykonywanie wątku.</span><span class="sxs-lookup"><span data-stu-id="c4b94-111">The debugger uses the `CorDebugThreadState` enumeration to control a thread's execution.</span></span> <span data-ttu-id="c4b94-112">Można ustawić stan wątku przy użyciu [ICorDebugThread::SetDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md) lub [ICorDebugController::SetAllThreadsDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="c4b94-112">The state of a thread can be set by using the [ICorDebugThread::SetDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-setdebugstate-method.md) or [ICorDebugController::SetAllThreadsDebugState](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-setallthreadsdebugstate-method.md) method.</span></span>  
  
 <span data-ttu-id="c4b94-113">Wywołanie zwrotne przekazane do [hostingu API](../../../../docs/framework/unmanaged-api/hosting/index.md) umożliwia przekazywanie wiadomości, więc stan przerwania nie jest potrzebny.</span><span class="sxs-lookup"><span data-stu-id="c4b94-113">A callback provided to the [hosting API](../../../../docs/framework/unmanaged-api/hosting/index.md) enables message pumping, so an interrupted state is not needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c4b94-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c4b94-114">Requirements</span></span>  
 <span data-ttu-id="c4b94-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c4b94-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c4b94-116">**Nagłówek:** CorDebug.idl, CorDegug.h</span><span class="sxs-lookup"><span data-stu-id="c4b94-116">**Header:** CorDebug.idl, CorDegug.h</span></span>  
  
 <span data-ttu-id="c4b94-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c4b94-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c4b94-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c4b94-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4b94-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c4b94-119">See Also</span></span>  
 [<span data-ttu-id="c4b94-120">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="c4b94-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)

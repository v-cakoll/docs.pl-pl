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
ms.openlocfilehash: 9c22ca47a606da0949529cf55655bbcde19cb5c9
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795667"
---
# <a name="cordebugthreadstate-enumeration"></a><span data-ttu-id="321af-102">CorDebugThreadState — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="321af-102">CorDebugThreadState Enumeration</span></span>
<span data-ttu-id="321af-103">Określa stan wątku do debugowania.</span><span class="sxs-lookup"><span data-stu-id="321af-103">Specifies the state of a thread for debugging.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="321af-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="321af-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugThreadState {  
    THREAD_RUN,  
    THREAD_SUSPEND  
} CorDebugThreadState;  
```  
  
## <a name="members"></a><span data-ttu-id="321af-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="321af-105">Members</span></span>  
  
|<span data-ttu-id="321af-106">Członek</span><span class="sxs-lookup"><span data-stu-id="321af-106">Member</span></span>|<span data-ttu-id="321af-107">Opis</span><span class="sxs-lookup"><span data-stu-id="321af-107">Description</span></span>|  
|------------|-----------------|  
|`THREAD_RUN`|<span data-ttu-id="321af-108">Wątek działa swobodnie, chyba że wystąpi zdarzenie debugowania.</span><span class="sxs-lookup"><span data-stu-id="321af-108">The thread runs freely, unless a debug event occurs.</span></span>|  
|`THREAD_SUSPEND`|<span data-ttu-id="321af-109">Nie można uruchomić wątku.</span><span class="sxs-lookup"><span data-stu-id="321af-109">The thread cannot run.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="321af-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="321af-110">Remarks</span></span>  
 <span data-ttu-id="321af-111">Debuger używa wyliczenia, `CorDebugThreadState` aby kontrolować wykonywanie wątku.</span><span class="sxs-lookup"><span data-stu-id="321af-111">The debugger uses the `CorDebugThreadState` enumeration to control a thread's execution.</span></span> <span data-ttu-id="321af-112">Stan wątku można ustawić za pomocą metody [ICorDebugThread:: SetDebugState —](icordebugthread-setdebugstate-method.md) lub [ICorDebugController:: SetAllThreadsDebugState —](icordebugcontroller-setallthreadsdebugstate-method.md) .</span><span class="sxs-lookup"><span data-stu-id="321af-112">The state of a thread can be set by using the [ICorDebugThread::SetDebugState](icordebugthread-setdebugstate-method.md) or [ICorDebugController::SetAllThreadsDebugState](icordebugcontroller-setallthreadsdebugstate-method.md) method.</span></span>  
  
 <span data-ttu-id="321af-113">Wywołanie zwrotne obsługiwane w [interfejsie API hostingu](../hosting/index.md) umożliwia pompowanie komunikatów, dlatego nie jest wymagany stan przerwania.</span><span class="sxs-lookup"><span data-stu-id="321af-113">A callback provided to the [hosting API](../hosting/index.md) enables message pumping, so an interrupted state is not needed.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="321af-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="321af-114">Requirements</span></span>  
 <span data-ttu-id="321af-115">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="321af-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="321af-116">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="321af-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="321af-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="321af-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="321af-118">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="321af-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="321af-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="321af-119">See also</span></span>

- [<span data-ttu-id="321af-120">Debugowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="321af-120">Debugging Enumerations</span></span>](debugging-enumerations.md)

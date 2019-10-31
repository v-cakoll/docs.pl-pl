---
title: CorDebugUserState — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorDebugUserState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugUserState
helpviewer_keywords:
- CorDebugUserState enumeration [.NET Framework debugging]
ms.assetid: 5f6c2bcd-8102-4e3b-abc5-86ab0bd62def
topic_type:
- apiref
ms.openlocfilehash: d0394d511197c8d0aaa366ce7b791216a3d226bc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120190"
---
# <a name="cordebuguserstate-enumeration"></a><span data-ttu-id="68531-102">CorDebugUserState — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="68531-102">CorDebugUserState Enumeration</span></span>
<span data-ttu-id="68531-103">Wskazuje stan użytkownika wątku.</span><span class="sxs-lookup"><span data-stu-id="68531-103">Indicates the user state of a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68531-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="68531-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugUserState {  
    USER_STOP_REQUESTED     =  0x01,  
    USER_SUSPEND_REQUESTED  =  0x02,  
    USER_BACKGROUND         =  0x04,  
    USER_UNSTARTED          =  0x08,  
    USER_STOPPED            =  0x10,  
    USER_WAIT_SLEEP_JOIN    =  0x20,  
    USER_SUSPENDED          =  0x40,  
    USER_UNSAFE_POINT       =  0x80,  
    USER_THREADPOOL         = 0x100  
} CorDebugUserState;  
```  
  
## <a name="members"></a><span data-ttu-id="68531-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="68531-105">Members</span></span>  
  
|<span data-ttu-id="68531-106">Wartość</span><span class="sxs-lookup"><span data-stu-id="68531-106">Value</span></span>|<span data-ttu-id="68531-107">Opis</span><span class="sxs-lookup"><span data-stu-id="68531-107">Description</span></span>|  
|-----------|-----------------|  
|`USER_STOP_REQUESTED`|<span data-ttu-id="68531-108">Zażądano zakończenia wątku.</span><span class="sxs-lookup"><span data-stu-id="68531-108">A termination of the thread has been requested.</span></span>|  
|`USER_SUSPEND_REQUESTED`|<span data-ttu-id="68531-109">Zażądano zawieszenia wątku.</span><span class="sxs-lookup"><span data-stu-id="68531-109">A suspension of the thread has been requested.</span></span>|  
|`USER_BACKGROUND`|<span data-ttu-id="68531-110">Wątek działa w tle.</span><span class="sxs-lookup"><span data-stu-id="68531-110">The thread is running in the background.</span></span>|  
|`USER_UNSTARTED`|<span data-ttu-id="68531-111">Nie rozpoczęto wykonywania wątku.</span><span class="sxs-lookup"><span data-stu-id="68531-111">The thread has not started executing.</span></span>|  
|`USER_STOPPED`|<span data-ttu-id="68531-112">Wątek został zakończony.</span><span class="sxs-lookup"><span data-stu-id="68531-112">The thread has been terminated.</span></span>|  
|`USER_WAIT_SLEEP_JOIN`|<span data-ttu-id="68531-113">Wątek oczekuje na ukończenie zadania przez inny wątek.</span><span class="sxs-lookup"><span data-stu-id="68531-113">The thread is waiting for another thread to complete a task.</span></span>|  
|`USER_SUSPENDED`|<span data-ttu-id="68531-114">Wątek został zawieszony.</span><span class="sxs-lookup"><span data-stu-id="68531-114">The thread has been suspended.</span></span>|  
|`USER_UNSAFE_POINT`|<span data-ttu-id="68531-115">Wątek znajduje się w niebezpiecznym punkcie.</span><span class="sxs-lookup"><span data-stu-id="68531-115">The thread is at an unsafe point.</span></span> <span data-ttu-id="68531-116">Oznacza to, że wątek jest w miejscu wykonywania, gdzie może blokować odzyskiwanie pamięci.</span><span class="sxs-lookup"><span data-stu-id="68531-116">That is, the thread is at a point in execution where it may block garbage collection.</span></span><br /><br /> <span data-ttu-id="68531-117">Zdarzenia debugowania mogą być wysyłane z niebezpiecznych punktów, ale zawieszenie wątku w niebezpiecznym punkcie prawdopodobnie spowoduje zakleszczenie do momentu wznowienia wątku.</span><span class="sxs-lookup"><span data-stu-id="68531-117">Debug events may be dispatched from unsafe points, but suspending a thread at an unsafe point  will very likely cause a deadlock until the thread is resumed.</span></span> <span data-ttu-id="68531-118">Bezpieczne i niebezpieczne punkty są określane przez implementację just-in-Time (JIT) i wyrzucania elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="68531-118">The safe and unsafe points are determined by the just-in-time (JIT) and garbage collection implementation.</span></span>|  
|`USER_THREADPOOL`|<span data-ttu-id="68531-119">Wątek pochodzi z puli wątków.</span><span class="sxs-lookup"><span data-stu-id="68531-119">The thread is from the thread pool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="68531-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="68531-120">Remarks</span></span>  
 <span data-ttu-id="68531-121">Stanem użytkownika wątku jest stan, w którym wątek jest badany przez debuger.</span><span class="sxs-lookup"><span data-stu-id="68531-121">The user state of a thread is the state that the thread has when the debugger examines it.</span></span> <span data-ttu-id="68531-122">Wątek może mieć kombinację Stanów użytkownika.</span><span class="sxs-lookup"><span data-stu-id="68531-122">A thread may have a combination of user states.</span></span>  
  
 <span data-ttu-id="68531-123">Użyj metody [ICorDebugThread:: GetUserState —](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md) , aby pobrać stan użytkownika wątku.</span><span class="sxs-lookup"><span data-stu-id="68531-123">Use the [ICorDebugThread::GetUserState](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md) method to retrieve a thread's user state.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68531-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="68531-124">Requirements</span></span>  
 <span data-ttu-id="68531-125">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68531-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68531-126">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="68531-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="68531-127">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="68531-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="68531-128">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68531-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68531-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="68531-129">See also</span></span>

- [<span data-ttu-id="68531-130">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="68531-130">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)

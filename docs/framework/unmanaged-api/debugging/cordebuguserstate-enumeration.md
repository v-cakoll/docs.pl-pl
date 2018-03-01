---
title: "CorDebugUserState — Wyliczenie"
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 57fd9df27b1911c90bd11712b67e6e64588c2b5f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="cordebuguserstate-enumeration"></a><span data-ttu-id="32486-102">CorDebugUserState — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="32486-102">CorDebugUserState Enumeration</span></span>
<span data-ttu-id="32486-103">Wskazuje stan użytkownika wątku.</span><span class="sxs-lookup"><span data-stu-id="32486-103">Indicates the user state of a thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32486-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="32486-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="32486-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="32486-105">Members</span></span>  
  
|<span data-ttu-id="32486-106">Wartość</span><span class="sxs-lookup"><span data-stu-id="32486-106">Value</span></span>|<span data-ttu-id="32486-107">Opis</span><span class="sxs-lookup"><span data-stu-id="32486-107">Description</span></span>|  
|-----------|-----------------|  
|`USER_STOP_REQUESTED`|<span data-ttu-id="32486-108">Zażądano zakończenia wątku.</span><span class="sxs-lookup"><span data-stu-id="32486-108">A termination of the thread has been requested.</span></span>|  
|`USER_SUSPEND_REQUESTED`|<span data-ttu-id="32486-109">Zażądano zawieszenia wątku.</span><span class="sxs-lookup"><span data-stu-id="32486-109">A suspension of the thread has been requested.</span></span>|  
|`USER_BACKGROUND`|<span data-ttu-id="32486-110">Wątek jest uruchomiony w tle.</span><span class="sxs-lookup"><span data-stu-id="32486-110">The thread is running in the background.</span></span>|  
|`USER_UNSTARTED`|<span data-ttu-id="32486-111">Wątek nie została uruchomiona, wykonywania.</span><span class="sxs-lookup"><span data-stu-id="32486-111">The thread has not started executing.</span></span>|  
|`USER_STOPPED`|<span data-ttu-id="32486-112">Wątek został zakończony.</span><span class="sxs-lookup"><span data-stu-id="32486-112">The thread has been terminated.</span></span>|  
|`USER_WAIT_SLEEP_JOIN`|<span data-ttu-id="32486-113">Wątek oczekuje na inny wątek w celu wykonania zadania.</span><span class="sxs-lookup"><span data-stu-id="32486-113">The thread is waiting for another thread to complete a task.</span></span>|  
|`USER_SUSPENDED`|<span data-ttu-id="32486-114">Wątek zostało zawieszone.</span><span class="sxs-lookup"><span data-stu-id="32486-114">The thread has been suspended.</span></span>|  
|`USER_UNSAFE_POINT`|<span data-ttu-id="32486-115">Wątek znajduje się w niebezpiecznego punktu.</span><span class="sxs-lookup"><span data-stu-id="32486-115">The thread is at an unsafe point.</span></span> <span data-ttu-id="32486-116">Wątek jest w momencie wykonywania gdzie może blokować wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="32486-116">That is, the thread is at a point in execution where it may block garbage collection.</span></span><br /><br /> <span data-ttu-id="32486-117">Debugowanie zdarzeń mogą być wysyłane z niebezpiecznych punkty, ale wstrzymywania wątku w niebezpiecznego punktu najprawdopodobniej spowoduje zakleszczenie dopóki nie zostanie wznowione wątku.</span><span class="sxs-lookup"><span data-stu-id="32486-117">Debug events may be dispatched from unsafe points, but suspending a thread at an unsafe point  will very likely cause a deadlock until the thread is resumed.</span></span> <span data-ttu-id="32486-118">Bezpieczne i niebezpieczny punkty są określane przez just-in-time (JIT) i odzyskiwanie kolekcji implementacji.</span><span class="sxs-lookup"><span data-stu-id="32486-118">The safe and unsafe points are determined by the just-in-time (JIT) and garbage collection implementation.</span></span>|  
|`USER_THREADPOOL`|<span data-ttu-id="32486-119">Wątek znajduje się w puli wątków.</span><span class="sxs-lookup"><span data-stu-id="32486-119">The thread is from the thread pool.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="32486-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="32486-120">Remarks</span></span>  
 <span data-ttu-id="32486-121">Stan użytkownika wątek jest w stanie, zawierający wątku, gdy debuger bada go.</span><span class="sxs-lookup"><span data-stu-id="32486-121">The user state of a thread is the state that the thread has when the debugger examines it.</span></span> <span data-ttu-id="32486-122">Wątek może mieć kombinację stanów użytkownika.</span><span class="sxs-lookup"><span data-stu-id="32486-122">A thread may have a combination of user states.</span></span>  
  
 <span data-ttu-id="32486-123">Użyj [ICorDebugThread::GetUserState](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md) metoda pobierania stanu użytkownika dla wątku.</span><span class="sxs-lookup"><span data-stu-id="32486-123">Use the [ICorDebugThread::GetUserState](../../../../docs/framework/unmanaged-api/debugging/icordebugthread-getuserstate-method.md) method to retrieve a thread's user state.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32486-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="32486-124">Requirements</span></span>  
 <span data-ttu-id="32486-125">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32486-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32486-126">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="32486-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="32486-127">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="32486-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="32486-128">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32486-128">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32486-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="32486-129">See Also</span></span>  
 [<span data-ttu-id="32486-130">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="32486-130">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)

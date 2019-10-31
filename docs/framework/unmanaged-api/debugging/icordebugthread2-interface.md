---
title: ICorDebugThread2 — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugThread2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2
helpviewer_keywords:
- ICorDebugThread2 interface [.NET Framework debugging]
ms.assetid: 678f89f9-cce7-46d1-af87-5e989abaa93c
topic_type:
- apiref
ms.openlocfilehash: 49d0015e9d8390a47aae7ce497dd431dfe743c36
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138671"
---
# <a name="icordebugthread2-interface"></a><span data-ttu-id="e8b1a-102">ICorDebugThread2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e8b1a-102">ICorDebugThread2 Interface</span></span>
<span data-ttu-id="e8b1a-103">Służy jako logiczne rozszerzenie interfejsu ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="e8b1a-103">Serves as a logical extension to the ICorDebugThread interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e8b1a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e8b1a-104">Methods</span></span>  
  
|<span data-ttu-id="e8b1a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e8b1a-105">Method</span></span>|<span data-ttu-id="e8b1a-106">Opis</span><span class="sxs-lookup"><span data-stu-id="e8b1a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e8b1a-107">GetActiveFunctions, metoda</span><span class="sxs-lookup"><span data-stu-id="e8b1a-107">GetActiveFunctions Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md)|<span data-ttu-id="e8b1a-108">Pobiera tablicę wystąpień COR_ACTIVE_FUNCTION, które zawierają dane dotyczące aktywnych funkcji w ramkach wątku.</span><span class="sxs-lookup"><span data-stu-id="e8b1a-108">Gets an array of COR_ACTIVE_FUNCTION instances that contain data about the active functions in a thread's frames.</span></span>|  
|[<span data-ttu-id="e8b1a-109">GetConnectionID, metoda</span><span class="sxs-lookup"><span data-stu-id="e8b1a-109">GetConnectionID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getconnectionid-method.md)|<span data-ttu-id="e8b1a-110">Pobiera identyfikator połączenia dla tego `ICorDebugThread2`.</span><span class="sxs-lookup"><span data-stu-id="e8b1a-110">Gets a connection identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="e8b1a-111">GetTaskID, metoda</span><span class="sxs-lookup"><span data-stu-id="e8b1a-111">GetTaskID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-gettaskid-method.md)|<span data-ttu-id="e8b1a-112">Pobiera identyfikator zadania dla tego `ICorDebugThread2`.</span><span class="sxs-lookup"><span data-stu-id="e8b1a-112">Gets a task identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="e8b1a-113">GetVolatileOSThreadID, metoda</span><span class="sxs-lookup"><span data-stu-id="e8b1a-113">GetVolatileOSThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getvolatileosthreadid-method.md)|<span data-ttu-id="e8b1a-114">Pobiera identyfikator wątku systemu operacyjnego dla tego `ICorDebugThread2`.</span><span class="sxs-lookup"><span data-stu-id="e8b1a-114">Gets the operating system thread identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="e8b1a-115">InterceptCurrentException, metoda</span><span class="sxs-lookup"><span data-stu-id="e8b1a-115">InterceptCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md)|<span data-ttu-id="e8b1a-116">Umożliwia debugerowi przechwycenie bieżącego wyjątku w wątku.</span><span class="sxs-lookup"><span data-stu-id="e8b1a-116">Allows a debugger to intercept the current exception on a thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e8b1a-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e8b1a-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e8b1a-118">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="e8b1a-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8b1a-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e8b1a-119">Requirements</span></span>  
 <span data-ttu-id="e8b1a-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8b1a-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8b1a-121">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e8b1a-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e8b1a-122">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e8b1a-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e8b1a-123">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8b1a-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8b1a-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e8b1a-124">See also</span></span>

- [<span data-ttu-id="e8b1a-125">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="e8b1a-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

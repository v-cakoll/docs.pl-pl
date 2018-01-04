---
title: ICorDebugThread2 Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugThread2
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugThread2
helpviewer_keywords: ICorDebugThread2 interface [.NET Framework debugging]
ms.assetid: 678f89f9-cce7-46d1-af87-5e989abaa93c
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 907ba524164b1e0d167f7a88250c7d32910504f4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugthread2-interface1"></a><span data-ttu-id="28d48-102">ICorDebugThread2 Interface1</span><span class="sxs-lookup"><span data-stu-id="28d48-102">ICorDebugThread2 Interface1</span></span>
<span data-ttu-id="28d48-103">Służy jako logiczne rozszerzenia interfejsu ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="28d48-103">Serves as a logical extension to the ICorDebugThread interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="28d48-104">Metody</span><span class="sxs-lookup"><span data-stu-id="28d48-104">Methods</span></span>  
  
|<span data-ttu-id="28d48-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="28d48-105">Method</span></span>|<span data-ttu-id="28d48-106">Opis</span><span class="sxs-lookup"><span data-stu-id="28d48-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="28d48-107">GetActiveFunctions, metoda</span><span class="sxs-lookup"><span data-stu-id="28d48-107">GetActiveFunctions Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md)|<span data-ttu-id="28d48-108">Pobiera tablicę cor_active_function — wystąpień, które zawierają dane dotyczące funkcji active w ramkach wątku.</span><span class="sxs-lookup"><span data-stu-id="28d48-108">Gets an array of COR_ACTIVE_FUNCTION instances that contain data about the active functions in a thread's frames.</span></span>|  
|[<span data-ttu-id="28d48-109">GetConnectionID, metoda</span><span class="sxs-lookup"><span data-stu-id="28d48-109">GetConnectionID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getconnectionid-method.md)|<span data-ttu-id="28d48-110">Pobiera identyfikator połączenia dla tego `ICorDebugThread2`.</span><span class="sxs-lookup"><span data-stu-id="28d48-110">Gets a connection identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="28d48-111">GetTaskID, metoda</span><span class="sxs-lookup"><span data-stu-id="28d48-111">GetTaskID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-gettaskid-method.md)|<span data-ttu-id="28d48-112">Pobiera identyfikator zadania dla tego `ICorDebugThread2`.</span><span class="sxs-lookup"><span data-stu-id="28d48-112">Gets a task identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="28d48-113">GetVolatileOSThreadID, metoda</span><span class="sxs-lookup"><span data-stu-id="28d48-113">GetVolatileOSThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getvolatileosthreadid-method.md)|<span data-ttu-id="28d48-114">Pobiera identyfikator wątku systemu operacyjnego dla tego `ICorDebugThread2`.</span><span class="sxs-lookup"><span data-stu-id="28d48-114">Gets the operating system thread identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="28d48-115">InterceptCurrentException, metoda</span><span class="sxs-lookup"><span data-stu-id="28d48-115">InterceptCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md)|<span data-ttu-id="28d48-116">Umożliwia debugera przechwycić bieżącego wyjątku w wątku.</span><span class="sxs-lookup"><span data-stu-id="28d48-116">Allows a debugger to intercept the current exception on a thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="28d48-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="28d48-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="28d48-118">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="28d48-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28d48-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="28d48-119">Requirements</span></span>  
 <span data-ttu-id="28d48-120">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28d48-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28d48-121">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="28d48-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="28d48-122">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="28d48-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="28d48-123">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28d48-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28d48-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="28d48-124">See Also</span></span>  
 [<span data-ttu-id="28d48-125">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="28d48-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

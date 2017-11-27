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
ms.openlocfilehash: 5d3a554d075adb56294e4693b234ce22735fb982
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugthread2-interface1"></a><span data-ttu-id="8a13c-102">ICorDebugThread2 Interface1</span><span class="sxs-lookup"><span data-stu-id="8a13c-102">ICorDebugThread2 Interface1</span></span>
<span data-ttu-id="8a13c-103">Służy jako logiczne rozszerzenia interfejsu ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="8a13c-103">Serves as a logical extension to the ICorDebugThread interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8a13c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="8a13c-104">Methods</span></span>  
  
|<span data-ttu-id="8a13c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="8a13c-105">Method</span></span>|<span data-ttu-id="8a13c-106">Opis</span><span class="sxs-lookup"><span data-stu-id="8a13c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8a13c-107">GetActiveFunctions — metoda</span><span class="sxs-lookup"><span data-stu-id="8a13c-107">GetActiveFunctions Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md)|<span data-ttu-id="8a13c-108">Pobiera tablicę cor_active_function — wystąpień, które zawierają dane dotyczące funkcji active w ramkach wątku.</span><span class="sxs-lookup"><span data-stu-id="8a13c-108">Gets an array of COR_ACTIVE_FUNCTION instances that contain data about the active functions in a thread's frames.</span></span>|  
|[<span data-ttu-id="8a13c-109">GetConnectionID — metoda</span><span class="sxs-lookup"><span data-stu-id="8a13c-109">GetConnectionID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getconnectionid-method.md)|<span data-ttu-id="8a13c-110">Pobiera identyfikator połączenia dla tego `ICorDebugThread2`.</span><span class="sxs-lookup"><span data-stu-id="8a13c-110">Gets a connection identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="8a13c-111">GetTaskID — metoda</span><span class="sxs-lookup"><span data-stu-id="8a13c-111">GetTaskID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-gettaskid-method.md)|<span data-ttu-id="8a13c-112">Pobiera identyfikator zadania dla tego `ICorDebugThread2`.</span><span class="sxs-lookup"><span data-stu-id="8a13c-112">Gets a task identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="8a13c-113">GetVolatileOSThreadID — metoda</span><span class="sxs-lookup"><span data-stu-id="8a13c-113">GetVolatileOSThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getvolatileosthreadid-method.md)|<span data-ttu-id="8a13c-114">Pobiera identyfikator wątku systemu operacyjnego dla tego `ICorDebugThread2`.</span><span class="sxs-lookup"><span data-stu-id="8a13c-114">Gets the operating system thread identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="8a13c-115">InterceptCurrentException — metoda</span><span class="sxs-lookup"><span data-stu-id="8a13c-115">InterceptCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md)|<span data-ttu-id="8a13c-116">Umożliwia debugera przechwycić bieżącego wyjątku w wątku.</span><span class="sxs-lookup"><span data-stu-id="8a13c-116">Allows a debugger to intercept the current exception on a thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8a13c-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8a13c-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8a13c-118">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="8a13c-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a13c-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8a13c-119">Requirements</span></span>  
 <span data-ttu-id="8a13c-120">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a13c-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a13c-121">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8a13c-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8a13c-122">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8a13c-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a13c-123">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a13c-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a13c-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8a13c-124">See Also</span></span>  
 [<span data-ttu-id="8a13c-125">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="8a13c-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

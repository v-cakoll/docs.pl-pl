---
title: ICorDebugThread2, interfejs
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 82648714c375998e9daa1bb59cd9ebd9802b5794
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59153936"
---
# <a name="icordebugthread2-interface"></a><span data-ttu-id="90cf9-102">ICorDebugThread2, interfejs</span><span class="sxs-lookup"><span data-stu-id="90cf9-102">ICorDebugThread2 Interface</span></span>
<span data-ttu-id="90cf9-103">Służy jako logiczne rozszerzenie icordebugthread — interfejs.</span><span class="sxs-lookup"><span data-stu-id="90cf9-103">Serves as a logical extension to the ICorDebugThread interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="90cf9-104">Metody</span><span class="sxs-lookup"><span data-stu-id="90cf9-104">Methods</span></span>  
  
|<span data-ttu-id="90cf9-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="90cf9-105">Method</span></span>|<span data-ttu-id="90cf9-106">Opis</span><span class="sxs-lookup"><span data-stu-id="90cf9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="90cf9-107">GetActiveFunctions, metoda</span><span class="sxs-lookup"><span data-stu-id="90cf9-107">GetActiveFunctions Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getactivefunctions-method.md)|<span data-ttu-id="90cf9-108">Pobiera tablicę wystąpień cor_active_function — zawierających dane o funkcje z aktywnej ramki dla wątku.</span><span class="sxs-lookup"><span data-stu-id="90cf9-108">Gets an array of COR_ACTIVE_FUNCTION instances that contain data about the active functions in a thread's frames.</span></span>|  
|[<span data-ttu-id="90cf9-109">GetConnectionID, metoda</span><span class="sxs-lookup"><span data-stu-id="90cf9-109">GetConnectionID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getconnectionid-method.md)|<span data-ttu-id="90cf9-110">Pobiera identyfikator połączenia dla tego `ICorDebugThread2`.</span><span class="sxs-lookup"><span data-stu-id="90cf9-110">Gets a connection identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="90cf9-111">GetTaskID, metoda</span><span class="sxs-lookup"><span data-stu-id="90cf9-111">GetTaskID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-gettaskid-method.md)|<span data-ttu-id="90cf9-112">Pobiera identyfikator zadania dla tego `ICorDebugThread2`.</span><span class="sxs-lookup"><span data-stu-id="90cf9-112">Gets a task identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="90cf9-113">GetVolatileOSThreadID, metoda</span><span class="sxs-lookup"><span data-stu-id="90cf9-113">GetVolatileOSThreadID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-getvolatileosthreadid-method.md)|<span data-ttu-id="90cf9-114">Pobiera identyfikator wątku systemu operacyjnego, w tym `ICorDebugThread2`.</span><span class="sxs-lookup"><span data-stu-id="90cf9-114">Gets the operating system thread identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="90cf9-115">InterceptCurrentException, metoda</span><span class="sxs-lookup"><span data-stu-id="90cf9-115">InterceptCurrentException Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md)|<span data-ttu-id="90cf9-116">Umożliwia debuger, który chcesz przechwycić bieżący wyjątek w wątku.</span><span class="sxs-lookup"><span data-stu-id="90cf9-116">Allows a debugger to intercept the current exception on a thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="90cf9-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="90cf9-117">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="90cf9-118">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="90cf9-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90cf9-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="90cf9-119">Requirements</span></span>  
 <span data-ttu-id="90cf9-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="90cf9-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="90cf9-121">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="90cf9-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="90cf9-122">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="90cf9-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="90cf9-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="90cf9-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90cf9-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="90cf9-124">See also</span></span>

- [<span data-ttu-id="90cf9-125">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="90cf9-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

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
ms.openlocfilehash: a7a8d96548704f223f05826af79a4e227bdfab06
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379829"
---
# <a name="icordebugthread2-interface"></a><span data-ttu-id="d9994-102">ICorDebugThread2, interfejs</span><span class="sxs-lookup"><span data-stu-id="d9994-102">ICorDebugThread2 Interface</span></span>
<span data-ttu-id="d9994-103">Służy jako logiczne rozszerzenie interfejsu ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="d9994-103">Serves as a logical extension to the ICorDebugThread interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d9994-104">Metody</span><span class="sxs-lookup"><span data-stu-id="d9994-104">Methods</span></span>  
  
|<span data-ttu-id="d9994-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="d9994-105">Method</span></span>|<span data-ttu-id="d9994-106">Opis</span><span class="sxs-lookup"><span data-stu-id="d9994-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d9994-107">GetActiveFunctions, metoda</span><span class="sxs-lookup"><span data-stu-id="d9994-107">GetActiveFunctions Method</span></span>](icordebugthread2-getactivefunctions-method.md)|<span data-ttu-id="d9994-108">Pobiera tablicę wystąpień COR_ACTIVE_FUNCTION zawierających dane dotyczące aktywnych funkcji w ramkach wątku.</span><span class="sxs-lookup"><span data-stu-id="d9994-108">Gets an array of COR_ACTIVE_FUNCTION instances that contain data about the active functions in a thread's frames.</span></span>|  
|[<span data-ttu-id="d9994-109">GetConnectionID, metoda</span><span class="sxs-lookup"><span data-stu-id="d9994-109">GetConnectionID Method</span></span>](icordebugthread2-getconnectionid-method.md)|<span data-ttu-id="d9994-110">Pobiera identyfikator połączenia dla tego elementu `ICorDebugThread2` .</span><span class="sxs-lookup"><span data-stu-id="d9994-110">Gets a connection identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="d9994-111">GetTaskID, metoda</span><span class="sxs-lookup"><span data-stu-id="d9994-111">GetTaskID Method</span></span>](icordebugthread2-gettaskid-method.md)|<span data-ttu-id="d9994-112">Pobiera identyfikator zadania dla tego elementu `ICorDebugThread2` .</span><span class="sxs-lookup"><span data-stu-id="d9994-112">Gets a task identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="d9994-113">GetVolatileOSThreadID, metoda</span><span class="sxs-lookup"><span data-stu-id="d9994-113">GetVolatileOSThreadID Method</span></span>](icordebugthread2-getvolatileosthreadid-method.md)|<span data-ttu-id="d9994-114">Pobiera identyfikator wątku systemu operacyjnego `ICorDebugThread2` .</span><span class="sxs-lookup"><span data-stu-id="d9994-114">Gets the operating system thread identifier for this `ICorDebugThread2`.</span></span>|  
|[<span data-ttu-id="d9994-115">InterceptCurrentException, metoda</span><span class="sxs-lookup"><span data-stu-id="d9994-115">InterceptCurrentException Method</span></span>](icordebugthread2-interceptcurrentexception-method.md)|<span data-ttu-id="d9994-116">Umożliwia debugerowi przechwycenie bieżącego wyjątku w wątku.</span><span class="sxs-lookup"><span data-stu-id="d9994-116">Allows a debugger to intercept the current exception on a thread.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d9994-117">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d9994-117">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d9994-118">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="d9994-118">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9994-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d9994-119">Requirements</span></span>  
 <span data-ttu-id="d9994-120">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d9994-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d9994-121">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d9994-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d9994-122">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d9994-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d9994-123">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d9994-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d9994-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d9994-124">See also</span></span>

- [<span data-ttu-id="d9994-125">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="d9994-125">Debugging Interfaces</span></span>](debugging-interfaces.md)

---
title: ICorDebugChain Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugChain
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugChain
helpviewer_keywords: ICorDebugChain interface [.NET Framework debugging]
ms.assetid: f671f519-1cb3-4ae5-b9f1-abc5e783459f
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6000f6d91b3fe2325868b9af58740e1c4cd76127
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugchain-interface1"></a><span data-ttu-id="9d96d-102">ICorDebugChain Interface1</span><span class="sxs-lookup"><span data-stu-id="9d96d-102">ICorDebugChain Interface1</span></span>
<span data-ttu-id="9d96d-103">Reprezentuje segment stosu wywołań fizycznych lub logicznych.</span><span class="sxs-lookup"><span data-stu-id="9d96d-103">Represents a segment of a physical or logical call stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9d96d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="9d96d-104">Methods</span></span>  
  
|<span data-ttu-id="9d96d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="9d96d-105">Method</span></span>|<span data-ttu-id="9d96d-106">Opis</span><span class="sxs-lookup"><span data-stu-id="9d96d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9d96d-107">EnumerateFrames, metoda</span><span class="sxs-lookup"><span data-stu-id="9d96d-107">EnumerateFrames Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-enumerateframes-method.md)|<span data-ttu-id="9d96d-108">Pobiera moduł wyliczający, który zawiera wszystkie ramki stosu zarządzanych w łańcuchu, zaczynając od ostatniego ramki.</span><span class="sxs-lookup"><span data-stu-id="9d96d-108">Gets an enumerator that contains all the managed stack frames in the chain, starting with the most recent frame.</span></span>|  
|[<span data-ttu-id="9d96d-109">GetActiveFrame, metoda</span><span class="sxs-lookup"><span data-stu-id="9d96d-109">GetActiveFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getactiveframe-method.md)|<span data-ttu-id="9d96d-110">Pobiera aktywny (to znaczy najnowszych) ramki w łańcuchu.</span><span class="sxs-lookup"><span data-stu-id="9d96d-110">Gets the active (that is, most recent) frame on the chain.</span></span>|  
|[<span data-ttu-id="9d96d-111">GetCallee, metoda</span><span class="sxs-lookup"><span data-stu-id="9d96d-111">GetCallee Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcallee-method.md)|<span data-ttu-id="9d96d-112">Pobiera łańcucha, która została wywołana przez ten łańcuch.</span><span class="sxs-lookup"><span data-stu-id="9d96d-112">Gets the chain that was called by this chain.</span></span>|  
|[<span data-ttu-id="9d96d-113">GetCaller, metoda</span><span class="sxs-lookup"><span data-stu-id="9d96d-113">GetCaller Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcaller-method.md)|<span data-ttu-id="9d96d-114">Pobiera łańcuch, który wywołuje ten łańcuch.</span><span class="sxs-lookup"><span data-stu-id="9d96d-114">Gets the chain that called this chain.</span></span>|  
|[<span data-ttu-id="9d96d-115">GetContext, metoda</span><span class="sxs-lookup"><span data-stu-id="9d96d-115">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcontext-method.md)|<span data-ttu-id="9d96d-116">Nie jest zaimplementowana.</span><span class="sxs-lookup"><span data-stu-id="9d96d-116">Not implemented.</span></span>|  
|[<span data-ttu-id="9d96d-117">GetNext, metoda</span><span class="sxs-lookup"><span data-stu-id="9d96d-117">GetNext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getnext-method.md)|<span data-ttu-id="9d96d-118">Pobiera łańcuch następnej ramki dla wątku.</span><span class="sxs-lookup"><span data-stu-id="9d96d-118">Gets the next chain of frames for the thread.</span></span>|  
|[<span data-ttu-id="9d96d-119">GetPrevious, metoda</span><span class="sxs-lookup"><span data-stu-id="9d96d-119">GetPrevious Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getprevious-method.md)|<span data-ttu-id="9d96d-120">Pobiera łańcuch poprzedniej ramki dla wątku.</span><span class="sxs-lookup"><span data-stu-id="9d96d-120">Gets the previous chain of frames for the thread.</span></span>|  
|[<span data-ttu-id="9d96d-121">GetReason, metoda</span><span class="sxs-lookup"><span data-stu-id="9d96d-121">GetReason Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md)|<span data-ttu-id="9d96d-122">Pobiera przyczynę genesis tego wywołania łańcucha.</span><span class="sxs-lookup"><span data-stu-id="9d96d-122">Gets the reason for the genesis of this calling chain.</span></span>|  
|[<span data-ttu-id="9d96d-123">GetRegisterSet, metoda</span><span class="sxs-lookup"><span data-stu-id="9d96d-123">GetRegisterSet Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getregisterset-method.md)|<span data-ttu-id="9d96d-124">Pobiera rejestr dla active część ten łańcuch.</span><span class="sxs-lookup"><span data-stu-id="9d96d-124">Gets the register set for the active part of this chain.</span></span>|  
|[<span data-ttu-id="9d96d-125">GetStackRange, metoda</span><span class="sxs-lookup"><span data-stu-id="9d96d-125">GetStackRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getstackrange-method.md)|<span data-ttu-id="9d96d-126">Pobiera zakres adresów segmentu stosu dla tego łańcucha.</span><span class="sxs-lookup"><span data-stu-id="9d96d-126">Gets the address range of the stack segment for this chain.</span></span>|  
|[<span data-ttu-id="9d96d-127">GetThread, metoda</span><span class="sxs-lookup"><span data-stu-id="9d96d-127">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getthread-method.md)|<span data-ttu-id="9d96d-128">Pobiera część wątku fizycznym, którego ten łańcuch wywołań.</span><span class="sxs-lookup"><span data-stu-id="9d96d-128">Gets the physical thread this call chain is part of.</span></span>|  
|[<span data-ttu-id="9d96d-129">IsManaged, metoda</span><span class="sxs-lookup"><span data-stu-id="9d96d-129">IsManaged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-ismanaged-method.md)|<span data-ttu-id="9d96d-130">Pobiera wartość wskazującą, czy ten łańcuch działa kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="9d96d-130">Gets a value that indicates whether this chain is running managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d96d-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9d96d-131">Remarks</span></span>  
 <span data-ttu-id="9d96d-132">Ramki stosu w łańcuchu zajmować miejsca na stosie ciągłe i udostępnianie tego samego wątku i kontekstu.</span><span class="sxs-lookup"><span data-stu-id="9d96d-132">The stack frames in a chain occupy contiguous stack space and share the same thread and context.</span></span> <span data-ttu-id="9d96d-133">Łańcuch może reprezentować albo łańcuchów kodu zarządzane lub niezarządzane.</span><span class="sxs-lookup"><span data-stu-id="9d96d-133">A chain may represent either managed or unmanaged code chains.</span></span> <span data-ttu-id="9d96d-134">Pusta `ICorDebugChain` wystąpienie reprezentuje łańcucha kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="9d96d-134">An empty `ICorDebugChain` instance represents an unmanaged code chain.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9d96d-135">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="9d96d-135">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9d96d-136">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9d96d-136">Requirements</span></span>  
 <span data-ttu-id="9d96d-137">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9d96d-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9d96d-138">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9d96d-138">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9d96d-139">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9d96d-139">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9d96d-140">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9d96d-140">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d96d-141">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9d96d-141">See Also</span></span>  
 [<span data-ttu-id="9d96d-142">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="9d96d-142">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

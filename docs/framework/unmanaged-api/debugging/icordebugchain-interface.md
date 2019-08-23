---
title: ICorDebugChain, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugChain
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugChain
helpviewer_keywords:
- ICorDebugChain interface [.NET Framework debugging]
ms.assetid: f671f519-1cb3-4ae5-b9f1-abc5e783459f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 93ada40bd88e53cd06f5e8d8136b2d527d7741e6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969305"
---
# <a name="icordebugchain-interface"></a><span data-ttu-id="be855-102">ICorDebugChain, interfejs</span><span class="sxs-lookup"><span data-stu-id="be855-102">ICorDebugChain Interface</span></span>

<span data-ttu-id="be855-103">Reprezentuje segment stosu wywołań fizycznych lub logicznych.</span><span class="sxs-lookup"><span data-stu-id="be855-103">Represents a segment of a physical or logical call stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="be855-104">Metody</span><span class="sxs-lookup"><span data-stu-id="be855-104">Methods</span></span>  
  
|<span data-ttu-id="be855-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="be855-105">Method</span></span>|<span data-ttu-id="be855-106">Opis</span><span class="sxs-lookup"><span data-stu-id="be855-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="be855-107">EnumerateFrames, metoda</span><span class="sxs-lookup"><span data-stu-id="be855-107">EnumerateFrames Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-enumerateframes-method.md)|<span data-ttu-id="be855-108">Pobiera moduł wyliczający, który zawiera wszystkie zarządzane ramki stosu w łańcuchu, rozpoczynając od ostatniej ramki.</span><span class="sxs-lookup"><span data-stu-id="be855-108">Gets an enumerator that contains all the managed stack frames in the chain, starting with the most recent frame.</span></span>|  
|[<span data-ttu-id="be855-109">GetActiveFrame, metoda</span><span class="sxs-lookup"><span data-stu-id="be855-109">GetActiveFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getactiveframe-method.md)|<span data-ttu-id="be855-110">Pobiera aktywną (czyli ostatnią) ramkę w łańcuchu.</span><span class="sxs-lookup"><span data-stu-id="be855-110">Gets the active (that is, most recent) frame on the chain.</span></span>|  
|[<span data-ttu-id="be855-111">GetCallee, metoda</span><span class="sxs-lookup"><span data-stu-id="be855-111">GetCallee Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcallee-method.md)|<span data-ttu-id="be855-112">Pobiera łańcuch, który został wywołany przez ten łańcuch.</span><span class="sxs-lookup"><span data-stu-id="be855-112">Gets the chain that was called by this chain.</span></span>|  
|[<span data-ttu-id="be855-113">GetCaller, metoda</span><span class="sxs-lookup"><span data-stu-id="be855-113">GetCaller Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcaller-method.md)|<span data-ttu-id="be855-114">Pobiera łańcuch, który wywołał ten łańcuch.</span><span class="sxs-lookup"><span data-stu-id="be855-114">Gets the chain that called this chain.</span></span>|  
|[<span data-ttu-id="be855-115">GetContext, metoda</span><span class="sxs-lookup"><span data-stu-id="be855-115">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcontext-method.md)|<span data-ttu-id="be855-116">Nie zaimplementowane.</span><span class="sxs-lookup"><span data-stu-id="be855-116">Not implemented.</span></span>|  
|[<span data-ttu-id="be855-117">GetNext, metoda</span><span class="sxs-lookup"><span data-stu-id="be855-117">GetNext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getnext-method.md)|<span data-ttu-id="be855-118">Pobiera następny łańcuch ramek dla wątku.</span><span class="sxs-lookup"><span data-stu-id="be855-118">Gets the next chain of frames for the thread.</span></span>|  
|[<span data-ttu-id="be855-119">GetPrevious, metoda</span><span class="sxs-lookup"><span data-stu-id="be855-119">GetPrevious Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getprevious-method.md)|<span data-ttu-id="be855-120">Pobiera poprzedni łańcuch ramek dla wątku.</span><span class="sxs-lookup"><span data-stu-id="be855-120">Gets the previous chain of frames for the thread.</span></span>|  
|[<span data-ttu-id="be855-121">GetReason, metoda</span><span class="sxs-lookup"><span data-stu-id="be855-121">GetReason Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md)|<span data-ttu-id="be855-122">Pobiera przyczynę Genesis tego łańcucha wywołującego.</span><span class="sxs-lookup"><span data-stu-id="be855-122">Gets the reason for the genesis of this calling chain.</span></span>|  
|[<span data-ttu-id="be855-123">GetRegisterSet, metoda</span><span class="sxs-lookup"><span data-stu-id="be855-123">GetRegisterSet Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getregisterset-method.md)|<span data-ttu-id="be855-124">Pobiera zestaw rejestru dla aktywnej części tego łańcucha.</span><span class="sxs-lookup"><span data-stu-id="be855-124">Gets the register set for the active part of this chain.</span></span>|  
|[<span data-ttu-id="be855-125">GetStackRange, metoda</span><span class="sxs-lookup"><span data-stu-id="be855-125">GetStackRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getstackrange-method.md)|<span data-ttu-id="be855-126">Pobiera zakres adresów segmentu stosu dla tego łańcucha.</span><span class="sxs-lookup"><span data-stu-id="be855-126">Gets the address range of the stack segment for this chain.</span></span>|  
|[<span data-ttu-id="be855-127">GetThread, metoda</span><span class="sxs-lookup"><span data-stu-id="be855-127">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getthread-method.md)|<span data-ttu-id="be855-128">Pobiera wątek fizyczny, do którego należy ten łańcuch wywołań.</span><span class="sxs-lookup"><span data-stu-id="be855-128">Gets the physical thread this call chain is part of.</span></span>|  
|[<span data-ttu-id="be855-129">IsManaged, metoda</span><span class="sxs-lookup"><span data-stu-id="be855-129">IsManaged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-ismanaged-method.md)|<span data-ttu-id="be855-130">Pobiera wartość wskazującą, czy w tym łańcuchu działa kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="be855-130">Gets a value that indicates whether this chain is running managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="be855-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="be855-131">Remarks</span></span>  
 <span data-ttu-id="be855-132">Ramki stosu w łańcuchu zajmują ciągły obszar stosu i korzystają z tego samego wątku i kontekstu.</span><span class="sxs-lookup"><span data-stu-id="be855-132">The stack frames in a chain occupy contiguous stack space and share the same thread and context.</span></span> <span data-ttu-id="be855-133">Łańcuch może reprezentować zarządzane lub niezarządzane łańcuchy kodu.</span><span class="sxs-lookup"><span data-stu-id="be855-133">A chain may represent either managed or unmanaged code chains.</span></span> <span data-ttu-id="be855-134">Puste `ICorDebugChain` wystąpienie reprezentuje łańcuch kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="be855-134">An empty `ICorDebugChain` instance represents an unmanaged code chain.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="be855-135">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="be855-135">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="be855-136">Wymagania</span><span class="sxs-lookup"><span data-stu-id="be855-136">Requirements</span></span>  
 <span data-ttu-id="be855-137">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="be855-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="be855-138">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="be855-138">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="be855-139">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="be855-139">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="be855-140">**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="be855-140">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be855-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="be855-141">See also</span></span>

- [<span data-ttu-id="be855-142">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="be855-142">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

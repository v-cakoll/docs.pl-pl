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
ms.openlocfilehash: f4bacfe94178ea78b1c3afd15a2e100076c38a84
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777996"
---
# <a name="icordebugchain-interface"></a><span data-ttu-id="41418-102">ICorDebugChain, interfejs</span><span class="sxs-lookup"><span data-stu-id="41418-102">ICorDebugChain Interface</span></span>

<span data-ttu-id="41418-103">Reprezentuje segment stosu wywołań fizycznych lub logicznych.</span><span class="sxs-lookup"><span data-stu-id="41418-103">Represents a segment of a physical or logical call stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="41418-104">Metody</span><span class="sxs-lookup"><span data-stu-id="41418-104">Methods</span></span>  
  
|<span data-ttu-id="41418-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="41418-105">Method</span></span>|<span data-ttu-id="41418-106">Opis</span><span class="sxs-lookup"><span data-stu-id="41418-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="41418-107">EnumerateFrames, metoda</span><span class="sxs-lookup"><span data-stu-id="41418-107">EnumerateFrames Method</span></span>](icordebugchain-enumerateframes-method.md)|<span data-ttu-id="41418-108">Pobiera moduł wyliczający, który zawiera wszystkie zarządzane ramki stosu w łańcuchu, rozpoczynając od ostatniej ramki.</span><span class="sxs-lookup"><span data-stu-id="41418-108">Gets an enumerator that contains all the managed stack frames in the chain, starting with the most recent frame.</span></span>|  
|[<span data-ttu-id="41418-109">GetActiveFrame, metoda</span><span class="sxs-lookup"><span data-stu-id="41418-109">GetActiveFrame Method</span></span>](icordebugchain-getactiveframe-method.md)|<span data-ttu-id="41418-110">Pobiera aktywną (czyli ostatnią) ramkę w łańcuchu.</span><span class="sxs-lookup"><span data-stu-id="41418-110">Gets the active (that is, most recent) frame on the chain.</span></span>|  
|[<span data-ttu-id="41418-111">GetCallee, metoda</span><span class="sxs-lookup"><span data-stu-id="41418-111">GetCallee Method</span></span>](icordebugchain-getcallee-method.md)|<span data-ttu-id="41418-112">Pobiera łańcuch, który został wywołany przez ten łańcuch.</span><span class="sxs-lookup"><span data-stu-id="41418-112">Gets the chain that was called by this chain.</span></span>|  
|[<span data-ttu-id="41418-113">GetCaller, metoda</span><span class="sxs-lookup"><span data-stu-id="41418-113">GetCaller Method</span></span>](icordebugchain-getcaller-method.md)|<span data-ttu-id="41418-114">Pobiera łańcuch, który wywołał ten łańcuch.</span><span class="sxs-lookup"><span data-stu-id="41418-114">Gets the chain that called this chain.</span></span>|  
|[<span data-ttu-id="41418-115">GetContext, metoda</span><span class="sxs-lookup"><span data-stu-id="41418-115">GetContext Method</span></span>](icordebugchain-getcontext-method.md)|<span data-ttu-id="41418-116">Nie zaimplementowane.</span><span class="sxs-lookup"><span data-stu-id="41418-116">Not implemented.</span></span>|  
|[<span data-ttu-id="41418-117">GetNext, metoda</span><span class="sxs-lookup"><span data-stu-id="41418-117">GetNext Method</span></span>](icordebugchain-getnext-method.md)|<span data-ttu-id="41418-118">Pobiera następny łańcuch ramek dla wątku.</span><span class="sxs-lookup"><span data-stu-id="41418-118">Gets the next chain of frames for the thread.</span></span>|  
|[<span data-ttu-id="41418-119">GetPrevious, metoda</span><span class="sxs-lookup"><span data-stu-id="41418-119">GetPrevious Method</span></span>](icordebugchain-getprevious-method.md)|<span data-ttu-id="41418-120">Pobiera poprzedni łańcuch ramek dla wątku.</span><span class="sxs-lookup"><span data-stu-id="41418-120">Gets the previous chain of frames for the thread.</span></span>|  
|[<span data-ttu-id="41418-121">GetReason, metoda</span><span class="sxs-lookup"><span data-stu-id="41418-121">GetReason Method</span></span>](icordebugchain-getreason-method.md)|<span data-ttu-id="41418-122">Pobiera przyczynę Genesis tego łańcucha wywołującego.</span><span class="sxs-lookup"><span data-stu-id="41418-122">Gets the reason for the genesis of this calling chain.</span></span>|  
|[<span data-ttu-id="41418-123">GetRegisterSet, metoda</span><span class="sxs-lookup"><span data-stu-id="41418-123">GetRegisterSet Method</span></span>](icordebugchain-getregisterset-method.md)|<span data-ttu-id="41418-124">Pobiera zestaw rejestru dla aktywnej części tego łańcucha.</span><span class="sxs-lookup"><span data-stu-id="41418-124">Gets the register set for the active part of this chain.</span></span>|  
|[<span data-ttu-id="41418-125">GetStackRange, metoda</span><span class="sxs-lookup"><span data-stu-id="41418-125">GetStackRange Method</span></span>](icordebugchain-getstackrange-method.md)|<span data-ttu-id="41418-126">Pobiera zakres adresów segmentu stosu dla tego łańcucha.</span><span class="sxs-lookup"><span data-stu-id="41418-126">Gets the address range of the stack segment for this chain.</span></span>|  
|[<span data-ttu-id="41418-127">GetThread, metoda</span><span class="sxs-lookup"><span data-stu-id="41418-127">GetThread Method</span></span>](icordebugchain-getthread-method.md)|<span data-ttu-id="41418-128">Pobiera wątek fizyczny, do którego należy ten łańcuch wywołań.</span><span class="sxs-lookup"><span data-stu-id="41418-128">Gets the physical thread this call chain is part of.</span></span>|  
|[<span data-ttu-id="41418-129">IsManaged, metoda</span><span class="sxs-lookup"><span data-stu-id="41418-129">IsManaged Method</span></span>](icordebugchain-ismanaged-method.md)|<span data-ttu-id="41418-130">Pobiera wartość wskazującą, czy w tym łańcuchu działa kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="41418-130">Gets a value that indicates whether this chain is running managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41418-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="41418-131">Remarks</span></span>  
 <span data-ttu-id="41418-132">Ramki stosu w łańcuchu zajmują ciągły obszar stosu i korzystają z tego samego wątku i kontekstu.</span><span class="sxs-lookup"><span data-stu-id="41418-132">The stack frames in a chain occupy contiguous stack space and share the same thread and context.</span></span> <span data-ttu-id="41418-133">Łańcuch może reprezentować zarządzane lub niezarządzane łańcuchy kodu.</span><span class="sxs-lookup"><span data-stu-id="41418-133">A chain may represent either managed or unmanaged code chains.</span></span> <span data-ttu-id="41418-134">Puste wystąpienie `ICorDebugChain` reprezentuje łańcuch kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="41418-134">An empty `ICorDebugChain` instance represents an unmanaged code chain.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="41418-135">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="41418-135">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="41418-136">Wymagania</span><span class="sxs-lookup"><span data-stu-id="41418-136">Requirements</span></span>  
 <span data-ttu-id="41418-137">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="41418-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="41418-138">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="41418-138">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="41418-139">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="41418-139">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="41418-140">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="41418-140">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="41418-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="41418-141">See also</span></span>

- [<span data-ttu-id="41418-142">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="41418-142">Debugging Interfaces</span></span>](debugging-interfaces.md)

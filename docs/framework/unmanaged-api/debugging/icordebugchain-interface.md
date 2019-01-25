---
title: ICorDebugChain, interfejs1
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
ms.openlocfilehash: e0bb716f1ad4087642a76dc84266ec6d3f46c1ae
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54571207"
---
# <a name="icordebugchain-interface1"></a><span data-ttu-id="bf815-102">ICorDebugChain, interfejs1</span><span class="sxs-lookup"><span data-stu-id="bf815-102">ICorDebugChain Interface1</span></span>
<span data-ttu-id="bf815-103">Reprezentuje segment stosu wywołań fizycznych lub logicznych.</span><span class="sxs-lookup"><span data-stu-id="bf815-103">Represents a segment of a physical or logical call stack.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bf815-104">Metody</span><span class="sxs-lookup"><span data-stu-id="bf815-104">Methods</span></span>  
  
|<span data-ttu-id="bf815-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="bf815-105">Method</span></span>|<span data-ttu-id="bf815-106">Opis</span><span class="sxs-lookup"><span data-stu-id="bf815-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bf815-107">EnumerateFrames, metoda</span><span class="sxs-lookup"><span data-stu-id="bf815-107">EnumerateFrames Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-enumerateframes-method.md)|<span data-ttu-id="bf815-108">Pobiera moduł wyliczający, który zawiera wszystkie ramki stosu zarządzanych w łańcuchu, począwszy od najbardziej aktualną ramki.</span><span class="sxs-lookup"><span data-stu-id="bf815-108">Gets an enumerator that contains all the managed stack frames in the chain, starting with the most recent frame.</span></span>|  
|[<span data-ttu-id="bf815-109">GetActiveFrame, metoda</span><span class="sxs-lookup"><span data-stu-id="bf815-109">GetActiveFrame Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getactiveframe-method.md)|<span data-ttu-id="bf815-110">Pobiera aktywny (oznacza to, najbardziej aktualną) ramki w łańcuchu.</span><span class="sxs-lookup"><span data-stu-id="bf815-110">Gets the active (that is, most recent) frame on the chain.</span></span>|  
|[<span data-ttu-id="bf815-111">GetCallee, metoda</span><span class="sxs-lookup"><span data-stu-id="bf815-111">GetCallee Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcallee-method.md)|<span data-ttu-id="bf815-112">Pobiera łańcucha, który został wywołany przez tego łańcucha.</span><span class="sxs-lookup"><span data-stu-id="bf815-112">Gets the chain that was called by this chain.</span></span>|  
|[<span data-ttu-id="bf815-113">GetCaller, metoda</span><span class="sxs-lookup"><span data-stu-id="bf815-113">GetCaller Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcaller-method.md)|<span data-ttu-id="bf815-114">Pobiera łańcucha, który wywołuje ten łańcuch.</span><span class="sxs-lookup"><span data-stu-id="bf815-114">Gets the chain that called this chain.</span></span>|  
|[<span data-ttu-id="bf815-115">GetContext, metoda</span><span class="sxs-lookup"><span data-stu-id="bf815-115">GetContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getcontext-method.md)|<span data-ttu-id="bf815-116">Nie zaimplementowano.</span><span class="sxs-lookup"><span data-stu-id="bf815-116">Not implemented.</span></span>|  
|[<span data-ttu-id="bf815-117">GetNext, metoda</span><span class="sxs-lookup"><span data-stu-id="bf815-117">GetNext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getnext-method.md)|<span data-ttu-id="bf815-118">Pobiera łańcuch następnej ramki dla wątku.</span><span class="sxs-lookup"><span data-stu-id="bf815-118">Gets the next chain of frames for the thread.</span></span>|  
|[<span data-ttu-id="bf815-119">GetPrevious, metoda</span><span class="sxs-lookup"><span data-stu-id="bf815-119">GetPrevious Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getprevious-method.md)|<span data-ttu-id="bf815-120">Pobiera łańcuch poprzedniej ramki dla wątku.</span><span class="sxs-lookup"><span data-stu-id="bf815-120">Gets the previous chain of frames for the thread.</span></span>|  
|[<span data-ttu-id="bf815-121">GetReason, metoda</span><span class="sxs-lookup"><span data-stu-id="bf815-121">GetReason Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md)|<span data-ttu-id="bf815-122">Pobiera przyczynę genesis tego łańcucha wywoływania.</span><span class="sxs-lookup"><span data-stu-id="bf815-122">Gets the reason for the genesis of this calling chain.</span></span>|  
|[<span data-ttu-id="bf815-123">GetRegisterSet, metoda</span><span class="sxs-lookup"><span data-stu-id="bf815-123">GetRegisterSet Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getregisterset-method.md)|<span data-ttu-id="bf815-124">Pobiera rejestr dla aktywnego częścią tego łańcucha.</span><span class="sxs-lookup"><span data-stu-id="bf815-124">Gets the register set for the active part of this chain.</span></span>|  
|[<span data-ttu-id="bf815-125">GetStackRange, metoda</span><span class="sxs-lookup"><span data-stu-id="bf815-125">GetStackRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getstackrange-method.md)|<span data-ttu-id="bf815-126">Pobiera zakres adresów segment stosu dla tego łańcucha.</span><span class="sxs-lookup"><span data-stu-id="bf815-126">Gets the address range of the stack segment for this chain.</span></span>|  
|[<span data-ttu-id="bf815-127">GetThread, metoda</span><span class="sxs-lookup"><span data-stu-id="bf815-127">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getthread-method.md)|<span data-ttu-id="bf815-128">Pobiera wątku fizycznym, ten łańcuch wywołań jest częścią.</span><span class="sxs-lookup"><span data-stu-id="bf815-128">Gets the physical thread this call chain is part of.</span></span>|  
|[<span data-ttu-id="bf815-129">IsManaged, metoda</span><span class="sxs-lookup"><span data-stu-id="bf815-129">IsManaged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-ismanaged-method.md)|<span data-ttu-id="bf815-130">Pobiera wartość wskazującą, czy ten łańcuch działa dla kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="bf815-130">Gets a value that indicates whether this chain is running managed code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bf815-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bf815-131">Remarks</span></span>  
 <span data-ttu-id="bf815-132">Ramki stosu w łańcuchu zajmują miejsce ciągłe stosu i używają tego samego wątku i kontekstu.</span><span class="sxs-lookup"><span data-stu-id="bf815-132">The stack frames in a chain occupy contiguous stack space and share the same thread and context.</span></span> <span data-ttu-id="bf815-133">Łańcuch może reprezentować albo łańcuchów kodu zarządzanego lub niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="bf815-133">A chain may represent either managed or unmanaged code chains.</span></span> <span data-ttu-id="bf815-134">Pusta `ICorDebugChain` wystąpienie reprezentuje łańcuch kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="bf815-134">An empty `ICorDebugChain` instance represents an unmanaged code chain.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bf815-135">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="bf815-135">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bf815-136">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bf815-136">Requirements</span></span>  
 <span data-ttu-id="bf815-137">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bf815-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bf815-138">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bf815-138">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bf815-139">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bf815-139">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bf815-140">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bf815-140">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf815-141">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bf815-141">See also</span></span>
- [<span data-ttu-id="bf815-142">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="bf815-142">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

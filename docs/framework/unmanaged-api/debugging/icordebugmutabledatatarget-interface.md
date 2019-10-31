---
title: ICorDebugMutableDataTarget, interfejs
ms.date: 03/30/2017
ms.assetid: 14aad5b3-84ab-4bbc-94e3-1eb92e258d10
ms.openlocfilehash: 682e927388d3392d970338314f97d46c9e57e760
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139334"
---
# <a name="icordebugmutabledatatarget-interface"></a><span data-ttu-id="2f04d-102">ICorDebugMutableDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="2f04d-102">ICorDebugMutableDataTarget Interface</span></span>
<span data-ttu-id="2f04d-103">Rozszerza interfejs [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) w celu obsługi modyfikowalnych obiektów docelowych danych.</span><span class="sxs-lookup"><span data-stu-id="2f04d-103">Extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to support mutable data targets.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2f04d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="2f04d-104">Methods</span></span>  
  
|<span data-ttu-id="2f04d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="2f04d-105">Method</span></span>|<span data-ttu-id="2f04d-106">Opis</span><span class="sxs-lookup"><span data-stu-id="2f04d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2f04d-107">ContinueStatusChanged, metoda</span><span class="sxs-lookup"><span data-stu-id="2f04d-107">ContinueStatusChanged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-continuestatuschanged-method.md)|<span data-ttu-id="2f04d-108">Zmienia stan kontynuacji dla zaległego zdarzenia debugowania w określonym wątku.</span><span class="sxs-lookup"><span data-stu-id="2f04d-108">Changes the continuation status for the outstanding debug event on the specified thread.</span></span>|  
|[<span data-ttu-id="2f04d-109">SetThreadContext, metoda</span><span class="sxs-lookup"><span data-stu-id="2f04d-109">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-setthreadcontext-method.md)|<span data-ttu-id="2f04d-110">Ustawia kontekst (wartości rejestru) dla wątku.</span><span class="sxs-lookup"><span data-stu-id="2f04d-110">Sets the context (register values) for a thread.</span></span>|  
|[<span data-ttu-id="2f04d-111">WriteVirtual, metoda</span><span class="sxs-lookup"><span data-stu-id="2f04d-111">WriteVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-writevirtual-method.md)|<span data-ttu-id="2f04d-112">Zapisuje pamięć w przestrzeni adresowej procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="2f04d-112">Writes memory into the target process address space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2f04d-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2f04d-113">Remarks</span></span>  
 <span data-ttu-id="2f04d-114">To rozszerzenie interfejsu [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) może zostać zaimplementowane przez narzędzia debugowania, które chcą zmodyfikować proces docelowy (na przykład w celu przeprowadzenia aktywnego debugowania).</span><span class="sxs-lookup"><span data-stu-id="2f04d-114">This extension to the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface can be implemented by debugging tools that wish to modify the target process (for example, to perform live invasive debugging).</span></span>  
  
 <span data-ttu-id="2f04d-115">Wszystkie te metody są opcjonalne w tym sensie, że żadne podstawowe funkcje debugowania nie są tracone przez zaimplementowanie tego interfejsu lub niepowodzenie wywołań tych metod.</span><span class="sxs-lookup"><span data-stu-id="2f04d-115">All of these methods are optional in the sense that no core inspection-based debugging functionality is lost by not implementing this interface or by the failure of calls to these methods.</span></span>  <span data-ttu-id="2f04d-116">Wszystkie niepowodzenia `HRESULT` z tych metod będą propagowane jako `HRESULT` z wywołania metody ICorDebug.</span><span class="sxs-lookup"><span data-stu-id="2f04d-116">Any failure `HRESULT` from these methods will propagate out as the `HRESULT` from the ICorDebug method call.</span></span>  
  
 <span data-ttu-id="2f04d-117">Należy zauważyć, że pojedyncze wywołanie metody ICorDebug może spowodować wielokrotne mutacje i że nie ma mechanizmu zapewnienia, że powiązane mutacje są stosowane transakcyjnie (wszystkie-lub-None).</span><span class="sxs-lookup"><span data-stu-id="2f04d-117">Note that a single ICorDebug method call may result in multiple mutations, and that there is no mechanism for ensuring related mutations are applied transactionally (all-or-none).</span></span>  <span data-ttu-id="2f04d-118">Oznacza to, że jeśli mutacja nie powiedzie się po pomyślnym przejściu (dla tego samego wywołania ICorDebug), proces docelowy może pozostać w niespójnym stanie, a debugowanie może stać się niezawodne.</span><span class="sxs-lookup"><span data-stu-id="2f04d-118">This means that if a mutation fails after others (for the same ICorDebug call) have succeeded, the target process may be left in an inconsistent state and debugging may become unreliable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f04d-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2f04d-119">Requirements</span></span>  
 <span data-ttu-id="2f04d-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f04d-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f04d-121">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2f04d-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2f04d-122">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2f04d-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f04d-123">**Wersje .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f04d-123">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f04d-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2f04d-124">See also</span></span>

- [<span data-ttu-id="2f04d-125">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="2f04d-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="2f04d-126">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="2f04d-126">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

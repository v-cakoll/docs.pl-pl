---
title: ICorDebugMutableDataTarget, interfejs
ms.date: 03/30/2017
ms.assetid: 14aad5b3-84ab-4bbc-94e3-1eb92e258d10
ms.openlocfilehash: e4601c24194404f943c8de8f320bf704efcc553e
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792858"
---
# <a name="icordebugmutabledatatarget-interface"></a><span data-ttu-id="179f2-102">ICorDebugMutableDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="179f2-102">ICorDebugMutableDataTarget Interface</span></span>
<span data-ttu-id="179f2-103">Rozszerza interfejs [ICorDebugDataTarget](icordebugdatatarget-interface.md) w celu obsługi modyfikowalnych obiektów docelowych danych.</span><span class="sxs-lookup"><span data-stu-id="179f2-103">Extends the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface to support mutable data targets.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="179f2-104">Metody</span><span class="sxs-lookup"><span data-stu-id="179f2-104">Methods</span></span>  
  
|<span data-ttu-id="179f2-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="179f2-105">Method</span></span>|<span data-ttu-id="179f2-106">Opis</span><span class="sxs-lookup"><span data-stu-id="179f2-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="179f2-107">ContinueStatusChanged, metoda</span><span class="sxs-lookup"><span data-stu-id="179f2-107">ContinueStatusChanged Method</span></span>](icordebugmutabledatatarget-continuestatuschanged-method.md)|<span data-ttu-id="179f2-108">Zmienia stan kontynuacji dla zaległego zdarzenia debugowania w określonym wątku.</span><span class="sxs-lookup"><span data-stu-id="179f2-108">Changes the continuation status for the outstanding debug event on the specified thread.</span></span>|  
|[<span data-ttu-id="179f2-109">SetThreadContext, metoda</span><span class="sxs-lookup"><span data-stu-id="179f2-109">SetThreadContext Method</span></span>](icordebugmutabledatatarget-setthreadcontext-method.md)|<span data-ttu-id="179f2-110">Ustawia kontekst (wartości rejestru) dla wątku.</span><span class="sxs-lookup"><span data-stu-id="179f2-110">Sets the context (register values) for a thread.</span></span>|  
|[<span data-ttu-id="179f2-111">WriteVirtual, metoda</span><span class="sxs-lookup"><span data-stu-id="179f2-111">WriteVirtual Method</span></span>](icordebugmutabledatatarget-writevirtual-method.md)|<span data-ttu-id="179f2-112">Zapisuje pamięć w przestrzeni adresowej procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="179f2-112">Writes memory into the target process address space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="179f2-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="179f2-113">Remarks</span></span>  
 <span data-ttu-id="179f2-114">To rozszerzenie interfejsu [ICorDebugDataTarget](icordebugdatatarget-interface.md) może zostać zaimplementowane przez narzędzia debugowania, które chcą zmodyfikować proces docelowy (na przykład w celu przeprowadzenia aktywnego debugowania).</span><span class="sxs-lookup"><span data-stu-id="179f2-114">This extension to the [ICorDebugDataTarget](icordebugdatatarget-interface.md) interface can be implemented by debugging tools that wish to modify the target process (for example, to perform live invasive debugging).</span></span>  
  
 <span data-ttu-id="179f2-115">Wszystkie te metody są opcjonalne w tym sensie, że żadne podstawowe funkcje debugowania nie są tracone przez zaimplementowanie tego interfejsu lub niepowodzenie wywołań tych metod.</span><span class="sxs-lookup"><span data-stu-id="179f2-115">All of these methods are optional in the sense that no core inspection-based debugging functionality is lost by not implementing this interface or by the failure of calls to these methods.</span></span>  <span data-ttu-id="179f2-116">Wszystkie niepowodzenia `HRESULT` z tych metod będą propagowane jako `HRESULT` z wywołania metody ICorDebug.</span><span class="sxs-lookup"><span data-stu-id="179f2-116">Any failure `HRESULT` from these methods will propagate out as the `HRESULT` from the ICorDebug method call.</span></span>  
  
 <span data-ttu-id="179f2-117">Należy zauważyć, że pojedyncze wywołanie metody ICorDebug może spowodować wielokrotne mutacje i że nie ma mechanizmu zapewnienia, że powiązane mutacje są stosowane transakcyjnie (wszystkie-lub-None).</span><span class="sxs-lookup"><span data-stu-id="179f2-117">Note that a single ICorDebug method call may result in multiple mutations, and that there is no mechanism for ensuring related mutations are applied transactionally (all-or-none).</span></span>  <span data-ttu-id="179f2-118">Oznacza to, że jeśli mutacja nie powiedzie się po pomyślnym przejściu (dla tego samego wywołania ICorDebug), proces docelowy może pozostać w niespójnym stanie, a debugowanie może stać się niezawodne.</span><span class="sxs-lookup"><span data-stu-id="179f2-118">This means that if a mutation fails after others (for the same ICorDebug call) have succeeded, the target process may be left in an inconsistent state and debugging may become unreliable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="179f2-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="179f2-119">Requirements</span></span>  
 <span data-ttu-id="179f2-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="179f2-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="179f2-121">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="179f2-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="179f2-122">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="179f2-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="179f2-123">**Wersje .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="179f2-123">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="179f2-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="179f2-124">See also</span></span>

- [<span data-ttu-id="179f2-125">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="179f2-125">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="179f2-126">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="179f2-126">Debugging</span></span>](index.md)

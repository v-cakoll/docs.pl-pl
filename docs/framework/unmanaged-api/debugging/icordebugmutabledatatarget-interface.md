---
title: ICorDebugMutableDataTarget Interface
ms.date: 03/30/2017
ms.assetid: 14aad5b3-84ab-4bbc-94e3-1eb92e258d10
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f63343b43481d1d91d1db30cd2ace3214c5590a9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54492302"
---
# <a name="icordebugmutabledatatarget-interface"></a><span data-ttu-id="46f80-102">ICorDebugMutableDataTarget Interface</span><span class="sxs-lookup"><span data-stu-id="46f80-102">ICorDebugMutableDataTarget Interface</span></span>
<span data-ttu-id="46f80-103">Rozszerza [icordebugdatatarget —](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interfejsu do obsługi danych modyfikowalnych elementów docelowych.</span><span class="sxs-lookup"><span data-stu-id="46f80-103">Extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to support mutable data targets.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="46f80-104">Metody</span><span class="sxs-lookup"><span data-stu-id="46f80-104">Methods</span></span>  
  
|<span data-ttu-id="46f80-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="46f80-105">Method</span></span>|<span data-ttu-id="46f80-106">Opis</span><span class="sxs-lookup"><span data-stu-id="46f80-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="46f80-107">ContinueStatusChanged, metoda</span><span class="sxs-lookup"><span data-stu-id="46f80-107">ContinueStatusChanged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-continuestatuschanged-method.md)|<span data-ttu-id="46f80-108">Zmienia stan kontynuacji dla zdarzenia debugowania oczekujących na określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="46f80-108">Changes the continuation status for the outstanding debug event on the specified thread.</span></span>|  
|[<span data-ttu-id="46f80-109">SetThreadContext, metoda</span><span class="sxs-lookup"><span data-stu-id="46f80-109">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-setthreadcontext-method.md)|<span data-ttu-id="46f80-110">Ustawia kontekst (wartości rejestru) dla wątku.</span><span class="sxs-lookup"><span data-stu-id="46f80-110">Sets the context (register values) for a thread.</span></span>|  
|[<span data-ttu-id="46f80-111">WriteVirtual, metoda</span><span class="sxs-lookup"><span data-stu-id="46f80-111">WriteVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-writevirtual-method.md)|<span data-ttu-id="46f80-112">Zapisuje w pamięci do przestrzeni adresowej procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="46f80-112">Writes memory into the target process address space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="46f80-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="46f80-113">Remarks</span></span>  
 <span data-ttu-id="46f80-114">To rozszerzenie, aby [icordebugdatatarget —](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interfejsu może być implementowany przez narzędzia debugowania, które chcesz zmodyfikować procesu docelowego (na przykład przeprowadzić inwazyjne debugowania na żywo).</span><span class="sxs-lookup"><span data-stu-id="46f80-114">This extension to the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface can be implemented by debugging tools that wish to modify the target process (for example, to perform live invasive debugging).</span></span>  
  
 <span data-ttu-id="46f80-115">Wszystkie te metody są opcjonalne, w tym sensie, że nie podstawowych na podstawie kontroli debugowania funkcji zostaną utracone, przez nie implementuje ten interfejs lub niepowodzenia wywołania tych metod.</span><span class="sxs-lookup"><span data-stu-id="46f80-115">All of these methods are optional in the sense that no core inspection-based debugging functionality is lost by not implementing this interface or by the failure of calls to these methods.</span></span>  <span data-ttu-id="46f80-116">Jakiekolwiek niepowodzenie `HRESULT` z tych metod będzie propagowania jako `HRESULT` z wywołania metody ICorDebug.</span><span class="sxs-lookup"><span data-stu-id="46f80-116">Any failure `HRESULT` from these methods will propagate out as the `HRESULT` from the ICorDebug method call.</span></span>  
  
 <span data-ttu-id="46f80-117">Pamiętaj, że pojedyncze wywołanie metody ICorDebug może spowodować wiele mutacji a, nie ma mechanizmu zapewniających powiązane mutacji są stosowane transakcyjnie (wymuszać).</span><span class="sxs-lookup"><span data-stu-id="46f80-117">Note that a single ICorDebug method call may result in multiple mutations, and that there is no mechanism for ensuring related mutations are applied transactionally (all-or-none).</span></span>  <span data-ttu-id="46f80-118">Oznacza to, jeśli mutacji zakończy się niepowodzeniem, po inne (na tym samym wywołaniu ICorDebug) zakończyły się powodzeniem, proces docelowy może pozostać w stanie niespójnym i debugowanie może stać się niepewna.</span><span class="sxs-lookup"><span data-stu-id="46f80-118">This means that if a mutation fails after others (for the same ICorDebug call) have succeeded, the target process may be left in an inconsistent state and debugging may become unreliable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="46f80-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="46f80-119">Requirements</span></span>  
 <span data-ttu-id="46f80-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46f80-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46f80-121">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="46f80-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="46f80-122">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="46f80-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="46f80-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46f80-123">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46f80-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="46f80-124">See also</span></span>
- [<span data-ttu-id="46f80-125">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="46f80-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="46f80-126">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="46f80-126">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

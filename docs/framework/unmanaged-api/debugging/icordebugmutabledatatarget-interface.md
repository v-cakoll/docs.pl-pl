---
title: Interfejs ICorDebugMutableDataTarget
ms.date: 03/30/2017
ms.assetid: 14aad5b3-84ab-4bbc-94e3-1eb92e258d10
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 677db647320ff4014b791502b7ac1b261378c8dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmutabledatatarget-interface"></a><span data-ttu-id="b7d37-102">Interfejs ICorDebugMutableDataTarget</span><span class="sxs-lookup"><span data-stu-id="b7d37-102">ICorDebugMutableDataTarget Interface</span></span>
<span data-ttu-id="b7d37-103">Rozszerza [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interfejs do obsługi danych modyfikowalne elementy docelowe.</span><span class="sxs-lookup"><span data-stu-id="b7d37-103">Extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to support mutable data targets.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b7d37-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b7d37-104">Methods</span></span>  
  
|<span data-ttu-id="b7d37-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b7d37-105">Method</span></span>|<span data-ttu-id="b7d37-106">Opis</span><span class="sxs-lookup"><span data-stu-id="b7d37-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b7d37-107">ContinueStatusChanged, metoda</span><span class="sxs-lookup"><span data-stu-id="b7d37-107">ContinueStatusChanged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-continuestatuschanged-method.md)|<span data-ttu-id="b7d37-108">Zmienia stan kontynuacji dla zdarzenia debugowania oczekujących na określony wątek.</span><span class="sxs-lookup"><span data-stu-id="b7d37-108">Changes the continuation status for the outstanding debug event on the specified thread.</span></span>|  
|[<span data-ttu-id="b7d37-109">SetThreadContext, metoda</span><span class="sxs-lookup"><span data-stu-id="b7d37-109">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-setthreadcontext-method.md)|<span data-ttu-id="b7d37-110">Ustawia kontekst wątku (wartości rejestru).</span><span class="sxs-lookup"><span data-stu-id="b7d37-110">Sets the context (register values) for a thread.</span></span>|  
|[<span data-ttu-id="b7d37-111">WriteVirtual, metoda</span><span class="sxs-lookup"><span data-stu-id="b7d37-111">WriteVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-writevirtual-method.md)|<span data-ttu-id="b7d37-112">Zapisuje pamięci do przestrzeni adresowej procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="b7d37-112">Writes memory into the target process address space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b7d37-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b7d37-113">Remarks</span></span>  
 <span data-ttu-id="b7d37-114">To rozszerzenie do [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interfejsu może być zaimplementowany przez narzędzia debugowania, które chcesz zmodyfikować procesu docelowego (na przykład, aby wykonać inwazyjne debugowania na żywo).</span><span class="sxs-lookup"><span data-stu-id="b7d37-114">This extension to the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface can be implemented by debugging tools that wish to modify the target process (for example, to perform live invasive debugging).</span></span>  
  
 <span data-ttu-id="b7d37-115">Wszystkie te metody są opcjonalne, w tym sensie, że nie core kontroli funkcje oparte na debugowania nie są tracone przez nie implementuje ten interfejs lub Niepowodzenie wywołania tych metod.</span><span class="sxs-lookup"><span data-stu-id="b7d37-115">All of these methods are optional in the sense that no core inspection-based debugging functionality is lost by not implementing this interface or by the failure of calls to these methods.</span></span>  <span data-ttu-id="b7d37-116">Jakiekolwiek niepowodzenie `HRESULT` z tych metod rozpropaguje się jako `HRESULT` w wywołaniu metody ICorDebug.</span><span class="sxs-lookup"><span data-stu-id="b7d37-116">Any failure `HRESULT` from these methods will propagate out as the `HRESULT` from the ICorDebug method call.</span></span>  
  
 <span data-ttu-id="b7d37-117">Uwaga przez jednego wywołania metody ICorDebug może spowodować wiele mutacji, oraz że nie istnieje mechanizm zapewniających powiązane mutacji są stosowane transakcyjnie (wykonywanie).</span><span class="sxs-lookup"><span data-stu-id="b7d37-117">Note that a single ICorDebug method call may result in multiple mutations, and that there is no mechanism for ensuring related mutations are applied transactionally (all-or-none).</span></span>  <span data-ttu-id="b7d37-118">To oznacza, że jeśli mutacja nie powiedzie się po innych (na to samo wywołanie ICorDebug) zakończyło się pomyślnie, proces docelowy może pozostać w stanie niespójnym, a debugowania mogą stać się niepewna.</span><span class="sxs-lookup"><span data-stu-id="b7d37-118">This means that if a mutation fails after others (for the same ICorDebug call) have succeeded, the target process may be left in an inconsistent state and debugging may become unreliable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b7d37-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b7d37-119">Requirements</span></span>  
 <span data-ttu-id="b7d37-120">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b7d37-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b7d37-121">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b7d37-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b7d37-122">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b7d37-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b7d37-123">**Wersje programu .NET framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b7d37-123">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7d37-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b7d37-124">See Also</span></span>  
 [<span data-ttu-id="b7d37-125">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="b7d37-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="b7d37-126">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="b7d37-126">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

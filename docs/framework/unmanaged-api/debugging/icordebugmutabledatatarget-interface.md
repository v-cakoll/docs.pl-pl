---
title: Interfejs ICorDebugMutableDataTarget
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 14aad5b3-84ab-4bbc-94e3-1eb92e258d10
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ef1c0b7a56f6bd1f7e87650b72dfe8b1411ef7f0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmutabledatatarget-interface"></a><span data-ttu-id="37a6b-102">Interfejs ICorDebugMutableDataTarget</span><span class="sxs-lookup"><span data-stu-id="37a6b-102">ICorDebugMutableDataTarget Interface</span></span>
<span data-ttu-id="37a6b-103">Rozszerza [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interfejs do obsługi danych modyfikowalne elementy docelowe.</span><span class="sxs-lookup"><span data-stu-id="37a6b-103">Extends the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface to support mutable data targets.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="37a6b-104">Metody</span><span class="sxs-lookup"><span data-stu-id="37a6b-104">Methods</span></span>  
  
|<span data-ttu-id="37a6b-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="37a6b-105">Method</span></span>|<span data-ttu-id="37a6b-106">Opis</span><span class="sxs-lookup"><span data-stu-id="37a6b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="37a6b-107">ContinueStatusChanged — metoda</span><span class="sxs-lookup"><span data-stu-id="37a6b-107">ContinueStatusChanged Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-continuestatuschanged-method.md)|<span data-ttu-id="37a6b-108">Zmienia stan kontynuacji dla zdarzenia debugowania oczekujących na określony wątek.</span><span class="sxs-lookup"><span data-stu-id="37a6b-108">Changes the continuation status for the outstanding debug event on the specified thread.</span></span>|  
|[<span data-ttu-id="37a6b-109">SetThreadContext — metoda</span><span class="sxs-lookup"><span data-stu-id="37a6b-109">SetThreadContext Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-setthreadcontext-method.md)|<span data-ttu-id="37a6b-110">Ustawia kontekst wątku (wartości rejestru).</span><span class="sxs-lookup"><span data-stu-id="37a6b-110">Sets the context (register values) for a thread.</span></span>|  
|[<span data-ttu-id="37a6b-111">WriteVirtual — metoda</span><span class="sxs-lookup"><span data-stu-id="37a6b-111">WriteVirtual Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-writevirtual-method.md)|<span data-ttu-id="37a6b-112">Zapisuje pamięci do przestrzeni adresowej procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="37a6b-112">Writes memory into the target process address space.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="37a6b-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="37a6b-113">Remarks</span></span>  
 <span data-ttu-id="37a6b-114">To rozszerzenie do [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interfejsu może być zaimplementowany przez narzędzia debugowania, które chcesz zmodyfikować procesu docelowego (na przykład, aby wykonać inwazyjne debugowania na żywo).</span><span class="sxs-lookup"><span data-stu-id="37a6b-114">This extension to the [ICorDebugDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md) interface can be implemented by debugging tools that wish to modify the target process (for example, to perform live invasive debugging).</span></span>  
  
 <span data-ttu-id="37a6b-115">Wszystkie te metody są opcjonalne, w tym sensie, że nie core kontroli funkcje oparte na debugowania nie są tracone przez nie implementuje ten interfejs lub Niepowodzenie wywołania tych metod.</span><span class="sxs-lookup"><span data-stu-id="37a6b-115">All of these methods are optional in the sense that no core inspection-based debugging functionality is lost by not implementing this interface or by the failure of calls to these methods.</span></span>  <span data-ttu-id="37a6b-116">Jakiekolwiek niepowodzenie `HRESULT` z tych metod rozpropaguje się jako `HRESULT` w wywołaniu metody ICorDebug.</span><span class="sxs-lookup"><span data-stu-id="37a6b-116">Any failure `HRESULT` from these methods will propagate out as the `HRESULT` from the ICorDebug method call.</span></span>  
  
 <span data-ttu-id="37a6b-117">Uwaga przez jednego wywołania metody ICorDebug może spowodować wiele mutacji, oraz że nie istnieje mechanizm zapewniających powiązane mutacji są stosowane transakcyjnie (wykonywanie).</span><span class="sxs-lookup"><span data-stu-id="37a6b-117">Note that a single ICorDebug method call may result in multiple mutations, and that there is no mechanism for ensuring related mutations are applied transactionally (all-or-none).</span></span>  <span data-ttu-id="37a6b-118">To oznacza, że jeśli mutacja nie powiedzie się po innych (na to samo wywołanie ICorDebug) zakończyło się pomyślnie, proces docelowy może pozostać w stanie niespójnym, a debugowania mogą stać się niepewna.</span><span class="sxs-lookup"><span data-stu-id="37a6b-118">This means that if a mutation fails after others (for the same ICorDebug call) have succeeded, the target process may be left in an inconsistent state and debugging may become unreliable.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37a6b-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="37a6b-119">Requirements</span></span>  
 <span data-ttu-id="37a6b-120">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="37a6b-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="37a6b-121">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="37a6b-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="37a6b-122">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="37a6b-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="37a6b-123">**Wersje programu .NET framework:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="37a6b-123">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="37a6b-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="37a6b-124">See Also</span></span>  
 [<span data-ttu-id="37a6b-125">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="37a6b-125">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="37a6b-126">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="37a6b-126">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

---
title: ICorDebugBreakpoint, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBreakpoint
helpviewer_keywords:
- ICorDebugBreakpoint interface [.NET Framework debugging]
ms.assetid: aa5ad3d7-e1bb-42af-99bc-471224e3bcaa
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 608c2cea79c20a43d65fcbf37ba13242fa465100
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969310"
---
# <a name="icordebugbreakpoint-interface"></a><span data-ttu-id="7c3a9-102">ICorDebugBreakpoint, interfejs</span><span class="sxs-lookup"><span data-stu-id="7c3a9-102">ICorDebugBreakpoint Interface</span></span>

<span data-ttu-id="7c3a9-103">Reprezentuje punkt przerwania w funkcji lub punkt obserwacji wartości.</span><span class="sxs-lookup"><span data-stu-id="7c3a9-103">Represents a breakpoint in a function, or a watch point on a value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7c3a9-104">Metody</span><span class="sxs-lookup"><span data-stu-id="7c3a9-104">Methods</span></span>  
  
|<span data-ttu-id="7c3a9-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="7c3a9-105">Method</span></span>|<span data-ttu-id="7c3a9-106">Opis</span><span class="sxs-lookup"><span data-stu-id="7c3a9-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7c3a9-107">Activate, metoda</span><span class="sxs-lookup"><span data-stu-id="7c3a9-107">Activate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-activate-method.md)|<span data-ttu-id="7c3a9-108">Ustawia stan aktywności tego `ICorDebugBreakpoint`elementu.</span><span class="sxs-lookup"><span data-stu-id="7c3a9-108">Sets the active state of this `ICorDebugBreakpoint`.</span></span>|  
|[<span data-ttu-id="7c3a9-109">IsActive, metoda</span><span class="sxs-lookup"><span data-stu-id="7c3a9-109">IsActive Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-isactive-method.md)|<span data-ttu-id="7c3a9-110">Pobiera wartość wskazującą, czy jest ona `ICorDebugBreakpoint` aktywna.</span><span class="sxs-lookup"><span data-stu-id="7c3a9-110">Gets a value that indicates whether this `ICorDebugBreakpoint` is active.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7c3a9-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7c3a9-111">Remarks</span></span>  
 <span data-ttu-id="7c3a9-112">Punkty przerwania nie obsługują bezpośrednio wyrażeń warunkowych.</span><span class="sxs-lookup"><span data-stu-id="7c3a9-112">Breakpoints do not directly support conditional expressions.</span></span> <span data-ttu-id="7c3a9-113">Jeśli ta funkcja jest wymagana, debuger musi zaimplementować ją w górnej części `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="7c3a9-113">If such functionality is desired, a debugger must implement it on top of `ICorDebugBreakpoint`.</span></span>  
  
 <span data-ttu-id="7c3a9-114">Interfejs ICorDebugFunctionBreakpoint rozszerza `ICorDebugBreakpoint` obsługę punktów przerwania w funkcjach.</span><span class="sxs-lookup"><span data-stu-id="7c3a9-114">The ICorDebugFunctionBreakpoint interface extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7c3a9-115">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="7c3a9-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c3a9-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7c3a9-116">Requirements</span></span>  
 <span data-ttu-id="7c3a9-117">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c3a9-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c3a9-118">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7c3a9-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7c3a9-119">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7c3a9-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7c3a9-120">**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c3a9-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c3a9-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7c3a9-121">See also</span></span>

- [<span data-ttu-id="7c3a9-122">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="7c3a9-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

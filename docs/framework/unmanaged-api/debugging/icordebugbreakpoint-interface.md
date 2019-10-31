---
title: ICorDebugBreakpoint — Interfejs
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
ms.openlocfilehash: 29bb84341c2cb4177c43f798d25a1a6d50099aa5
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122799"
---
# <a name="icordebugbreakpoint-interface"></a><span data-ttu-id="a1420-102">ICorDebugBreakpoint — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a1420-102">ICorDebugBreakpoint Interface</span></span>

<span data-ttu-id="a1420-103">Reprezentuje punkt przerwania w funkcji lub punkt obserwacji wartości.</span><span class="sxs-lookup"><span data-stu-id="a1420-103">Represents a breakpoint in a function, or a watch point on a value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a1420-104">Metody</span><span class="sxs-lookup"><span data-stu-id="a1420-104">Methods</span></span>  
  
|<span data-ttu-id="a1420-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="a1420-105">Method</span></span>|<span data-ttu-id="a1420-106">Opis</span><span class="sxs-lookup"><span data-stu-id="a1420-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a1420-107">Activate, metoda</span><span class="sxs-lookup"><span data-stu-id="a1420-107">Activate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-activate-method.md)|<span data-ttu-id="a1420-108">Ustawia stan aktywny tego `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="a1420-108">Sets the active state of this `ICorDebugBreakpoint`.</span></span>|  
|[<span data-ttu-id="a1420-109">IsActive, metoda</span><span class="sxs-lookup"><span data-stu-id="a1420-109">IsActive Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-isactive-method.md)|<span data-ttu-id="a1420-110">Pobiera wartość wskazującą, czy ta `ICorDebugBreakpoint` jest aktywna.</span><span class="sxs-lookup"><span data-stu-id="a1420-110">Gets a value that indicates whether this `ICorDebugBreakpoint` is active.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a1420-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a1420-111">Remarks</span></span>  
 <span data-ttu-id="a1420-112">Punkty przerwania nie obsługują bezpośrednio wyrażeń warunkowych.</span><span class="sxs-lookup"><span data-stu-id="a1420-112">Breakpoints do not directly support conditional expressions.</span></span> <span data-ttu-id="a1420-113">Jeśli ta funkcja jest wymagana, debuger musi zaimplementować ją na `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="a1420-113">If such functionality is desired, a debugger must implement it on top of `ICorDebugBreakpoint`.</span></span>  
  
 <span data-ttu-id="a1420-114">Interfejs ICorDebugFunctionBreakpoint rozszerza `ICorDebugBreakpoint` do obsługi punktów przerwania w funkcjach.</span><span class="sxs-lookup"><span data-stu-id="a1420-114">The ICorDebugFunctionBreakpoint interface extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a1420-115">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="a1420-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1420-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a1420-116">Requirements</span></span>  
 <span data-ttu-id="a1420-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1420-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1420-118">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a1420-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a1420-119">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a1420-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a1420-120">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1420-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1420-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a1420-121">See also</span></span>

- [<span data-ttu-id="a1420-122">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="a1420-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

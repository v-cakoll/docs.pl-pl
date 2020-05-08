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
ms.openlocfilehash: b92c3d3328c657762ed002155ef4947a9292b19e
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894731"
---
# <a name="icordebugbreakpoint-interface"></a><span data-ttu-id="11e63-102">ICorDebugBreakpoint, interfejs</span><span class="sxs-lookup"><span data-stu-id="11e63-102">ICorDebugBreakpoint Interface</span></span>

<span data-ttu-id="11e63-103">Reprezentuje punkt przerwania w funkcji lub punkt obserwacji wartości.</span><span class="sxs-lookup"><span data-stu-id="11e63-103">Represents a breakpoint in a function, or a watch point on a value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="11e63-104">Metody</span><span class="sxs-lookup"><span data-stu-id="11e63-104">Methods</span></span>  
  
|<span data-ttu-id="11e63-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="11e63-105">Method</span></span>|<span data-ttu-id="11e63-106">Opis</span><span class="sxs-lookup"><span data-stu-id="11e63-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="11e63-107">Activate, metoda</span><span class="sxs-lookup"><span data-stu-id="11e63-107">Activate Method</span></span>](icordebugbreakpoint-activate-method.md)|<span data-ttu-id="11e63-108">Ustawia stan aktywności tego `ICorDebugBreakpoint`elementu.</span><span class="sxs-lookup"><span data-stu-id="11e63-108">Sets the active state of this `ICorDebugBreakpoint`.</span></span>|  
|[<span data-ttu-id="11e63-109">IsActive — Metoda</span><span class="sxs-lookup"><span data-stu-id="11e63-109">IsActive Method</span></span>](icordebugbreakpoint-isactive-method.md)|<span data-ttu-id="11e63-110">Pobiera wartość wskazującą, czy jest ona `ICorDebugBreakpoint` aktywna.</span><span class="sxs-lookup"><span data-stu-id="11e63-110">Gets a value that indicates whether this `ICorDebugBreakpoint` is active.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="11e63-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="11e63-111">Remarks</span></span>  
 <span data-ttu-id="11e63-112">Punkty przerwania nie obsługują bezpośrednio wyrażeń warunkowych.</span><span class="sxs-lookup"><span data-stu-id="11e63-112">Breakpoints do not directly support conditional expressions.</span></span> <span data-ttu-id="11e63-113">Jeśli ta funkcja jest wymagana, debuger musi zaimplementować ją w górnej części `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="11e63-113">If such functionality is desired, a debugger must implement it on top of `ICorDebugBreakpoint`.</span></span>  
  
 <span data-ttu-id="11e63-114">Interfejs ICorDebugFunctionBreakpoint rozszerza `ICorDebugBreakpoint` obsługę punktów przerwania w funkcjach.</span><span class="sxs-lookup"><span data-stu-id="11e63-114">The ICorDebugFunctionBreakpoint interface extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="11e63-115">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="11e63-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="11e63-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="11e63-116">Requirements</span></span>  
 <span data-ttu-id="11e63-117">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="11e63-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="11e63-118">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="11e63-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="11e63-119">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="11e63-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="11e63-120">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="11e63-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11e63-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="11e63-121">See also</span></span>

- [<span data-ttu-id="11e63-122">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="11e63-122">Debugging Interfaces</span></span>](debugging-interfaces.md)

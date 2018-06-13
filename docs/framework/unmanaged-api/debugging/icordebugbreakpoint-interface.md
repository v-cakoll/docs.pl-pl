---
title: ICorDebugBreakpoint Interface1
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
ms.openlocfilehash: 220cd1a41ed69325b557e6498a511865b78817ec
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404518"
---
# <a name="icordebugbreakpoint-interface1"></a><span data-ttu-id="f0365-102">ICorDebugBreakpoint Interface1</span><span class="sxs-lookup"><span data-stu-id="f0365-102">ICorDebugBreakpoint Interface1</span></span>
<span data-ttu-id="f0365-103">Reprezentuje punkt przerwania w funkcji lub punkt czujki na wartość.</span><span class="sxs-lookup"><span data-stu-id="f0365-103">Represents a breakpoint in a function, or a watch point on a value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f0365-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f0365-104">Methods</span></span>  
  
|<span data-ttu-id="f0365-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f0365-105">Method</span></span>|<span data-ttu-id="f0365-106">Opis</span><span class="sxs-lookup"><span data-stu-id="f0365-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f0365-107">Activate, metoda</span><span class="sxs-lookup"><span data-stu-id="f0365-107">Activate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-activate-method.md)|<span data-ttu-id="f0365-108">Ustawia stan aktywny `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="f0365-108">Sets the active state of this `ICorDebugBreakpoint`.</span></span>|  
|[<span data-ttu-id="f0365-109">IsActive, metoda</span><span class="sxs-lookup"><span data-stu-id="f0365-109">IsActive Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-isactive-method.md)|<span data-ttu-id="f0365-110">Pobiera wartość wskazującą, czy to `ICorDebugBreakpoint` jest aktywny.</span><span class="sxs-lookup"><span data-stu-id="f0365-110">Gets a value that indicates whether this `ICorDebugBreakpoint` is active.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0365-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f0365-111">Remarks</span></span>  
 <span data-ttu-id="f0365-112">Punkty przerwania nie obsługują bezpośrednio wyrażenia warunkowego.</span><span class="sxs-lookup"><span data-stu-id="f0365-112">Breakpoints do not directly support conditional expressions.</span></span> <span data-ttu-id="f0365-113">W razie potrzeby takich funkcji debugera musi implementować on nad `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="f0365-113">If such functionality is desired, a debugger must implement it on top of `ICorDebugBreakpoint`.</span></span>  
  
 <span data-ttu-id="f0365-114">Interfejs ICorDebugFunctionBreakpoint rozszerza `ICorDebugBreakpoint` do obsługi punktów przerwania w funkcjach.</span><span class="sxs-lookup"><span data-stu-id="f0365-114">The ICorDebugFunctionBreakpoint interface extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f0365-115">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="f0365-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0365-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f0365-116">Requirements</span></span>  
 <span data-ttu-id="f0365-117">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0365-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0365-118">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f0365-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f0365-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f0365-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f0365-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0365-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0365-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f0365-121">See Also</span></span>  
 [<span data-ttu-id="f0365-122">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="f0365-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

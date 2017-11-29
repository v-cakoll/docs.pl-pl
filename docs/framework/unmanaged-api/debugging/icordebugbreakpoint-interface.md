---
title: ICorDebugBreakpoint Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugBreakpoint
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugBreakpoint
helpviewer_keywords: ICorDebugBreakpoint interface [.NET Framework debugging]
ms.assetid: aa5ad3d7-e1bb-42af-99bc-471224e3bcaa
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b78b61b99fb8f236e787f3acbf993d0a1c57e797
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugbreakpoint-interface1"></a><span data-ttu-id="c63e0-102">ICorDebugBreakpoint Interface1</span><span class="sxs-lookup"><span data-stu-id="c63e0-102">ICorDebugBreakpoint Interface1</span></span>
<span data-ttu-id="c63e0-103">Reprezentuje punkt przerwania w funkcji lub punkt czujki na wartość.</span><span class="sxs-lookup"><span data-stu-id="c63e0-103">Represents a breakpoint in a function, or a watch point on a value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="c63e0-104">Metody</span><span class="sxs-lookup"><span data-stu-id="c63e0-104">Methods</span></span>  
  
|<span data-ttu-id="c63e0-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="c63e0-105">Method</span></span>|<span data-ttu-id="c63e0-106">Opis</span><span class="sxs-lookup"><span data-stu-id="c63e0-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="c63e0-107">Activate — metoda</span><span class="sxs-lookup"><span data-stu-id="c63e0-107">Activate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-activate-method.md)|<span data-ttu-id="c63e0-108">Ustawia stan aktywny `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="c63e0-108">Sets the active state of this `ICorDebugBreakpoint`.</span></span>|  
|[<span data-ttu-id="c63e0-109">IsActive — metoda</span><span class="sxs-lookup"><span data-stu-id="c63e0-109">IsActive Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-isactive-method.md)|<span data-ttu-id="c63e0-110">Pobiera wartość wskazującą, czy to `ICorDebugBreakpoint` jest aktywny.</span><span class="sxs-lookup"><span data-stu-id="c63e0-110">Gets a value that indicates whether this `ICorDebugBreakpoint` is active.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c63e0-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c63e0-111">Remarks</span></span>  
 <span data-ttu-id="c63e0-112">Punkty przerwania nie obsługują bezpośrednio wyrażenia warunkowego.</span><span class="sxs-lookup"><span data-stu-id="c63e0-112">Breakpoints do not directly support conditional expressions.</span></span> <span data-ttu-id="c63e0-113">W razie potrzeby takich funkcji debugera musi implementować on nad `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="c63e0-113">If such functionality is desired, a debugger must implement it on top of `ICorDebugBreakpoint`.</span></span>  
  
 <span data-ttu-id="c63e0-114">Interfejs ICorDebugFunctionBreakpoint rozszerza `ICorDebugBreakpoint` do obsługi punktów przerwania w funkcjach.</span><span class="sxs-lookup"><span data-stu-id="c63e0-114">The ICorDebugFunctionBreakpoint interface extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c63e0-115">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="c63e0-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c63e0-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c63e0-116">Requirements</span></span>  
 <span data-ttu-id="c63e0-117">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c63e0-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c63e0-118">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c63e0-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c63e0-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c63e0-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c63e0-120">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c63e0-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c63e0-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c63e0-121">See Also</span></span>  
 [<span data-ttu-id="c63e0-122">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="c63e0-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

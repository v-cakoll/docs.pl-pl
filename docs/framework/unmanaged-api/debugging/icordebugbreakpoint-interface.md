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
ms.openlocfilehash: a68e061c6def61746ee65f8a25818f8dbcd785b5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645360"
---
# <a name="icordebugbreakpoint-interface"></a><span data-ttu-id="b0179-102">ICorDebugBreakpoint, interfejs</span><span class="sxs-lookup"><span data-stu-id="b0179-102">ICorDebugBreakpoint Interface</span></span>

<span data-ttu-id="b0179-103">Reprezentuje punkt przerwania w funkcji lub punkt obserwacji wartości.</span><span class="sxs-lookup"><span data-stu-id="b0179-103">Represents a breakpoint in a function, or a watch point on a value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b0179-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b0179-104">Methods</span></span>  
  
|<span data-ttu-id="b0179-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b0179-105">Method</span></span>|<span data-ttu-id="b0179-106">Opis</span><span class="sxs-lookup"><span data-stu-id="b0179-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b0179-107">Activate, metoda</span><span class="sxs-lookup"><span data-stu-id="b0179-107">Activate Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-activate-method.md)|<span data-ttu-id="b0179-108">Ustawia stan aktywny `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="b0179-108">Sets the active state of this `ICorDebugBreakpoint`.</span></span>|  
|[<span data-ttu-id="b0179-109">IsActive, metoda</span><span class="sxs-lookup"><span data-stu-id="b0179-109">IsActive Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugbreakpoint-isactive-method.md)|<span data-ttu-id="b0179-110">Pobiera wartość wskazującą, czy to `ICorDebugBreakpoint` jest aktywny.</span><span class="sxs-lookup"><span data-stu-id="b0179-110">Gets a value that indicates whether this `ICorDebugBreakpoint` is active.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b0179-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b0179-111">Remarks</span></span>  
 <span data-ttu-id="b0179-112">Punkty przerwania nie obsługują bezpośrednio wyrażenia warunkowe.</span><span class="sxs-lookup"><span data-stu-id="b0179-112">Breakpoints do not directly support conditional expressions.</span></span> <span data-ttu-id="b0179-113">W razie potrzeby takie funkcje debugera musi implementować go w górnej części `ICorDebugBreakpoint`.</span><span class="sxs-lookup"><span data-stu-id="b0179-113">If such functionality is desired, a debugger must implement it on top of `ICorDebugBreakpoint`.</span></span>  
  
 <span data-ttu-id="b0179-114">Icordebugfunctionbreakpoint — interfejs rozszerza `ICorDebugBreakpoint` do obsługi punktów przerwania w obrębie funkcji.</span><span class="sxs-lookup"><span data-stu-id="b0179-114">The ICorDebugFunctionBreakpoint interface extends `ICorDebugBreakpoint` to support breakpoints within functions.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b0179-115">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="b0179-115">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b0179-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b0179-116">Requirements</span></span>  
 <span data-ttu-id="b0179-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0179-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0179-118">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b0179-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b0179-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b0179-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0179-120">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0179-120">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0179-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b0179-121">See also</span></span>

- [<span data-ttu-id="b0179-122">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="b0179-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

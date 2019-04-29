---
title: ICorDebugFunctionBreakpoint, interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugFunctionBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunctionBreakpoint
helpviewer_keywords:
- ICorDebugFunctionBreakpoint interface [.NET Framework debugging]
ms.assetid: 9c149303-14b1-4138-83d7-e8c3e0fcd332
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0f15b9f5961699f905e765426576bdf6f3416793
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61651652"
---
# <a name="icordebugfunctionbreakpoint-interface"></a><span data-ttu-id="f8809-102">ICorDebugFunctionBreakpoint, interfejs</span><span class="sxs-lookup"><span data-stu-id="f8809-102">ICorDebugFunctionBreakpoint Interface</span></span>

<span data-ttu-id="f8809-103">Rozszerza icordebugbreakpoint — interfejs w celu obsługi punktów przerwania w obrębie funkcji.</span><span class="sxs-lookup"><span data-stu-id="f8809-103">Extends the ICorDebugBreakpoint interface to support breakpoints within functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f8809-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f8809-104">Methods</span></span>  
  
|<span data-ttu-id="f8809-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f8809-105">Method</span></span>|<span data-ttu-id="f8809-106">Opis</span><span class="sxs-lookup"><span data-stu-id="f8809-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f8809-107">GetFunction, metoda</span><span class="sxs-lookup"><span data-stu-id="f8809-107">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-getfunction-method.md)|<span data-ttu-id="f8809-108">Pobiera wskaźnik interfejsu do ICorDebugFunction, który odwołuje się do funkcji, w którym ustawiono punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="f8809-108">Gets an interface pointer to an ICorDebugFunction that references the function in which the breakpoint is set.</span></span>|  
|[<span data-ttu-id="f8809-109">GetOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="f8809-109">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-getoffset-method.md)|<span data-ttu-id="f8809-110">Pobiera przesunięcie punktu przerwania w obrębie funkcji.</span><span class="sxs-lookup"><span data-stu-id="f8809-110">Gets the offset of the breakpoint within the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f8809-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f8809-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f8809-112">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="f8809-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8809-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f8809-113">Requirements</span></span>  
 <span data-ttu-id="f8809-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8809-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8809-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f8809-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f8809-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f8809-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f8809-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8809-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8809-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f8809-118">See also</span></span>

- [<span data-ttu-id="f8809-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="f8809-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

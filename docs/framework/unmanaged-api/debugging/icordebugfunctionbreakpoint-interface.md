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
ms.openlocfilehash: ed09b4f9be71c7f85714b9ee26d45018410fda42
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917077"
---
# <a name="icordebugfunctionbreakpoint-interface"></a><span data-ttu-id="ee902-102">ICorDebugFunctionBreakpoint, interfejs</span><span class="sxs-lookup"><span data-stu-id="ee902-102">ICorDebugFunctionBreakpoint Interface</span></span>

<span data-ttu-id="ee902-103">Rozszerza interfejs ICorDebugBreakpoint w celu obsługi punktów przerwania w funkcjach.</span><span class="sxs-lookup"><span data-stu-id="ee902-103">Extends the ICorDebugBreakpoint interface to support breakpoints within functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ee902-104">Metody</span><span class="sxs-lookup"><span data-stu-id="ee902-104">Methods</span></span>  
  
|<span data-ttu-id="ee902-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="ee902-105">Method</span></span>|<span data-ttu-id="ee902-106">Opis</span><span class="sxs-lookup"><span data-stu-id="ee902-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ee902-107">GetFunction, metoda</span><span class="sxs-lookup"><span data-stu-id="ee902-107">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-getfunction-method.md)|<span data-ttu-id="ee902-108">Pobiera wskaźnik interfejsu do elementu ICorDebugFunction, który odwołuje się do funkcji, w której jest ustawiony punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="ee902-108">Gets an interface pointer to an ICorDebugFunction that references the function in which the breakpoint is set.</span></span>|  
|[<span data-ttu-id="ee902-109">GetOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="ee902-109">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-getoffset-method.md)|<span data-ttu-id="ee902-110">Pobiera przesunięcie punktu przerwania w funkcji.</span><span class="sxs-lookup"><span data-stu-id="ee902-110">Gets the offset of the breakpoint within the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ee902-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ee902-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ee902-112">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="ee902-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ee902-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ee902-113">Requirements</span></span>  
 <span data-ttu-id="ee902-114">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ee902-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ee902-115">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ee902-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ee902-116">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ee902-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ee902-117">**.NET Framework wersje:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ee902-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ee902-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ee902-118">See also</span></span>

- [<span data-ttu-id="ee902-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="ee902-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

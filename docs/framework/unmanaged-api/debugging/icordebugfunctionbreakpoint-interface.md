---
title: ICorDebugFunctionBreakpoint — Interfejs
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
ms.openlocfilehash: a7876cd932558ad95dab7adac3c91a6f23ca647c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134655"
---
# <a name="icordebugfunctionbreakpoint-interface"></a><span data-ttu-id="9bf2c-102">ICorDebugFunctionBreakpoint — Interfejs</span><span class="sxs-lookup"><span data-stu-id="9bf2c-102">ICorDebugFunctionBreakpoint Interface</span></span>

<span data-ttu-id="9bf2c-103">Rozszerza interfejs ICorDebugBreakpoint w celu obsługi punktów przerwania w funkcjach.</span><span class="sxs-lookup"><span data-stu-id="9bf2c-103">Extends the ICorDebugBreakpoint interface to support breakpoints within functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9bf2c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="9bf2c-104">Methods</span></span>  
  
|<span data-ttu-id="9bf2c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="9bf2c-105">Method</span></span>|<span data-ttu-id="9bf2c-106">Opis</span><span class="sxs-lookup"><span data-stu-id="9bf2c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9bf2c-107">GetFunction, metoda</span><span class="sxs-lookup"><span data-stu-id="9bf2c-107">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-getfunction-method.md)|<span data-ttu-id="9bf2c-108">Pobiera wskaźnik interfejsu do elementu ICorDebugFunction, który odwołuje się do funkcji, w której jest ustawiony punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="9bf2c-108">Gets an interface pointer to an ICorDebugFunction that references the function in which the breakpoint is set.</span></span>|  
|[<span data-ttu-id="9bf2c-109">GetOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="9bf2c-109">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-getoffset-method.md)|<span data-ttu-id="9bf2c-110">Pobiera przesunięcie punktu przerwania w funkcji.</span><span class="sxs-lookup"><span data-stu-id="9bf2c-110">Gets the offset of the breakpoint within the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9bf2c-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9bf2c-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9bf2c-112">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="9bf2c-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9bf2c-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9bf2c-113">Requirements</span></span>  
 <span data-ttu-id="9bf2c-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9bf2c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9bf2c-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="9bf2c-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9bf2c-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="9bf2c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9bf2c-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9bf2c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9bf2c-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9bf2c-118">See also</span></span>

- [<span data-ttu-id="9bf2c-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="9bf2c-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

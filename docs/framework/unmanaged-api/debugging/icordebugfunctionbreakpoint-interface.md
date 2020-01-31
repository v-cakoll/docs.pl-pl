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
ms.openlocfilehash: 5e3804335bacefad61c4f521ea1ef1444b7b1fed
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777705"
---
# <a name="icordebugfunctionbreakpoint-interface"></a><span data-ttu-id="2cf71-102">ICorDebugFunctionBreakpoint, interfejs</span><span class="sxs-lookup"><span data-stu-id="2cf71-102">ICorDebugFunctionBreakpoint Interface</span></span>

<span data-ttu-id="2cf71-103">Rozszerza interfejs ICorDebugBreakpoint w celu obsługi punktów przerwania w funkcjach.</span><span class="sxs-lookup"><span data-stu-id="2cf71-103">Extends the ICorDebugBreakpoint interface to support breakpoints within functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="2cf71-104">Metody</span><span class="sxs-lookup"><span data-stu-id="2cf71-104">Methods</span></span>  
  
|<span data-ttu-id="2cf71-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="2cf71-105">Method</span></span>|<span data-ttu-id="2cf71-106">Opis</span><span class="sxs-lookup"><span data-stu-id="2cf71-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="2cf71-107">GetFunction, metoda</span><span class="sxs-lookup"><span data-stu-id="2cf71-107">GetFunction Method</span></span>](icordebugfunctionbreakpoint-getfunction-method.md)|<span data-ttu-id="2cf71-108">Pobiera wskaźnik interfejsu do elementu ICorDebugFunction, który odwołuje się do funkcji, w której jest ustawiony punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="2cf71-108">Gets an interface pointer to an ICorDebugFunction that references the function in which the breakpoint is set.</span></span>|  
|[<span data-ttu-id="2cf71-109">GetOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="2cf71-109">GetOffset Method</span></span>](icordebugfunctionbreakpoint-getoffset-method.md)|<span data-ttu-id="2cf71-110">Pobiera przesunięcie punktu przerwania w funkcji.</span><span class="sxs-lookup"><span data-stu-id="2cf71-110">Gets the offset of the breakpoint within the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2cf71-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2cf71-111">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2cf71-112">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="2cf71-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2cf71-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2cf71-113">Requirements</span></span>  
 <span data-ttu-id="2cf71-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2cf71-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2cf71-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="2cf71-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2cf71-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2cf71-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2cf71-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2cf71-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cf71-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2cf71-118">See also</span></span>

- [<span data-ttu-id="2cf71-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="2cf71-119">Debugging Interfaces</span></span>](debugging-interfaces.md)

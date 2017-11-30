---
title: ICorDebugFunctionBreakpoint Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunctionBreakpoint
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunctionBreakpoint
helpviewer_keywords: ICorDebugFunctionBreakpoint interface [.NET Framework debugging]
ms.assetid: 9c149303-14b1-4138-83d7-e8c3e0fcd332
topic_type: apiref
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 910317bea8af3a80ee66544651de2372808734bb
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugfunctionbreakpoint-interface1"></a><span data-ttu-id="4217d-102">ICorDebugFunctionBreakpoint Interface1</span><span class="sxs-lookup"><span data-stu-id="4217d-102">ICorDebugFunctionBreakpoint Interface1</span></span>
<span data-ttu-id="4217d-103">Rozszerzenie interfejsu ICorDebugBreakpoint do obsługi punktów przerwania w funkcjach.</span><span class="sxs-lookup"><span data-stu-id="4217d-103">Extends the ICorDebugBreakpoint interface to support breakpoints within functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4217d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="4217d-104">Methods</span></span>  
  
|<span data-ttu-id="4217d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="4217d-105">Method</span></span>|<span data-ttu-id="4217d-106">Opis</span><span class="sxs-lookup"><span data-stu-id="4217d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4217d-107">GetFunction — metoda</span><span class="sxs-lookup"><span data-stu-id="4217d-107">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-getfunction-method.md)|<span data-ttu-id="4217d-108">Pobiera wskaźnika interfejsu do ICorDebugFunction, który odwołuje się do funkcji, w której zostanie ustawiony punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="4217d-108">Gets an interface pointer to an ICorDebugFunction that references the function in which the breakpoint is set.</span></span>|  
|[<span data-ttu-id="4217d-109">GetOffset — metoda</span><span class="sxs-lookup"><span data-stu-id="4217d-109">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-getoffset-method.md)|<span data-ttu-id="4217d-110">Pobiera przesunięcie punktu przerwania w funkcji.</span><span class="sxs-lookup"><span data-stu-id="4217d-110">Gets the offset of the breakpoint within the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4217d-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4217d-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4217d-112">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="4217d-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4217d-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4217d-113">Requirements</span></span>  
 <span data-ttu-id="4217d-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4217d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4217d-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4217d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4217d-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4217d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4217d-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4217d-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4217d-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4217d-118">See Also</span></span>  
 [<span data-ttu-id="4217d-119">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="4217d-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

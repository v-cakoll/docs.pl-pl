---
title: ICorDebugFunctionBreakpoint Interface1
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
ms.openlocfilehash: 6cd4c430798333dd22c36ce30e7c9ce05bdc8f56
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414186"
---
# <a name="icordebugfunctionbreakpoint-interface1"></a><span data-ttu-id="0981c-102">ICorDebugFunctionBreakpoint Interface1</span><span class="sxs-lookup"><span data-stu-id="0981c-102">ICorDebugFunctionBreakpoint Interface1</span></span>
<span data-ttu-id="0981c-103">Rozszerzenie interfejsu ICorDebugBreakpoint do obsługi punktów przerwania w funkcjach.</span><span class="sxs-lookup"><span data-stu-id="0981c-103">Extends the ICorDebugBreakpoint interface to support breakpoints within functions.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0981c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="0981c-104">Methods</span></span>  
  
|<span data-ttu-id="0981c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="0981c-105">Method</span></span>|<span data-ttu-id="0981c-106">Opis</span><span class="sxs-lookup"><span data-stu-id="0981c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0981c-107">GetFunction, metoda</span><span class="sxs-lookup"><span data-stu-id="0981c-107">GetFunction Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-getfunction-method.md)|<span data-ttu-id="0981c-108">Pobiera wskaźnika interfejsu do ICorDebugFunction, który odwołuje się do funkcji, w której zostanie ustawiony punkt przerwania.</span><span class="sxs-lookup"><span data-stu-id="0981c-108">Gets an interface pointer to an ICorDebugFunction that references the function in which the breakpoint is set.</span></span>|  
|[<span data-ttu-id="0981c-109">GetOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="0981c-109">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugfunctionbreakpoint-getoffset-method.md)|<span data-ttu-id="0981c-110">Pobiera przesunięcie punktu przerwania w funkcji.</span><span class="sxs-lookup"><span data-stu-id="0981c-110">Gets the offset of the breakpoint within the function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0981c-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0981c-111">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0981c-112">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="0981c-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0981c-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0981c-113">Requirements</span></span>  
 <span data-ttu-id="0981c-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0981c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0981c-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0981c-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0981c-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0981c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0981c-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0981c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0981c-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0981c-118">See Also</span></span>  
 [<span data-ttu-id="0981c-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="0981c-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

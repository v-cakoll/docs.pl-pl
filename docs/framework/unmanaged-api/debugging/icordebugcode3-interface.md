---
title: ICorDebugCode3 — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugCode3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode3
helpviewer_keywords:
- ICorDebugCode3 interface [.NET Framework debugging]
ms.assetid: 70f07c9e-0614-4bee-ac34-09fe6c51c5a9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: febfe7df52a0c1f44cb156faf2da310d317e01a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33411328"
---
# <a name="icordebugcode3-interface"></a><span data-ttu-id="d1a77-102">ICorDebugCode3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d1a77-102">ICorDebugCode3 Interface</span></span>
<span data-ttu-id="d1a77-103">Udostępnia metody, która rozszerza "ICorDebugCode" i "ICorDebugCode2", aby podać informacje o zarządzanych wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="d1a77-103">Provides a method that extends "ICorDebugCode" and "ICorDebugCode2" to provide information about a managed return value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d1a77-104">Metody</span><span class="sxs-lookup"><span data-stu-id="d1a77-104">Methods</span></span>  
  
|<span data-ttu-id="d1a77-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="d1a77-105">Method</span></span>|<span data-ttu-id="d1a77-106">Opis</span><span class="sxs-lookup"><span data-stu-id="d1a77-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d1a77-107">GetReturnValueLiveOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="d1a77-107">GetReturnValueLiveOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)|<span data-ttu-id="d1a77-108">Określony przesunięcia IL pobiera natywnego przesunięcia gdzie ma zostać umieszczony punkt przerwania, aby debuger można uzyskać wartości zwracanej przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="d1a77-108">For a specified IL offset, gets the native offsets where a breakpoint should be placed so that the debugger can obtain the return value from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d1a77-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d1a77-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d1a77-110">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="d1a77-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1a77-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d1a77-111">Requirements</span></span>  
 <span data-ttu-id="d1a77-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1a77-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1a77-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d1a77-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d1a77-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d1a77-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d1a77-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1a77-115">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1a77-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d1a77-116">See Also</span></span>  
    
    
    
 [<span data-ttu-id="d1a77-117">ICorDebugILFrame3, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1a77-117">ICorDebugILFrame3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)  
 [<span data-ttu-id="d1a77-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="d1a77-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

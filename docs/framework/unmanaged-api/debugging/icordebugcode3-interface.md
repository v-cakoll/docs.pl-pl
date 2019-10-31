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
ms.openlocfilehash: f3ae25f7d16600a1b09f30f96a191d7ecf76713e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121062"
---
# <a name="icordebugcode3-interface"></a><span data-ttu-id="0aa24-102">ICorDebugCode3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="0aa24-102">ICorDebugCode3 Interface</span></span>
<span data-ttu-id="0aa24-103">Zapewnia metodę, która rozszerza wartości "ICorDebugCode" i "ICorDebugCode2", aby podać informacje o zarządzanej zwracanej wartość.</span><span class="sxs-lookup"><span data-stu-id="0aa24-103">Provides a method that extends "ICorDebugCode" and "ICorDebugCode2" to provide information about a managed return value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0aa24-104">Metody</span><span class="sxs-lookup"><span data-stu-id="0aa24-104">Methods</span></span>  
  
|<span data-ttu-id="0aa24-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="0aa24-105">Method</span></span>|<span data-ttu-id="0aa24-106">Opis</span><span class="sxs-lookup"><span data-stu-id="0aa24-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0aa24-107">GetReturnValueLiveOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="0aa24-107">GetReturnValueLiveOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)|<span data-ttu-id="0aa24-108">W przypadku określonego przesunięcia IL pobiera natywne przesunięcia, w których powinien być umieszczony punkt przerwania, aby debuger mógł uzyskać wartość zwracaną z funkcji.</span><span class="sxs-lookup"><span data-stu-id="0aa24-108">For a specified IL offset, gets the native offsets where a breakpoint should be placed so that the debugger can obtain the return value from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0aa24-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0aa24-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0aa24-110">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="0aa24-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0aa24-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0aa24-111">Requirements</span></span>  
 <span data-ttu-id="0aa24-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0aa24-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0aa24-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0aa24-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0aa24-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0aa24-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0aa24-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0aa24-115">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0aa24-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0aa24-116">See also</span></span>

- [<span data-ttu-id="0aa24-117">ICorDebugILFrame3, interfejs</span><span class="sxs-lookup"><span data-stu-id="0aa24-117">ICorDebugILFrame3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)
- [<span data-ttu-id="0aa24-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="0aa24-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

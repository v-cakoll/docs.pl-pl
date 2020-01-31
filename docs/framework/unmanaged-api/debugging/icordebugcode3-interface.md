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
ms.openlocfilehash: f2f75c3c54c0fa2d55dc0179c05e4edea6e36738
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76777828"
---
# <a name="icordebugcode3-interface"></a><span data-ttu-id="e01ab-102">ICorDebugCode3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="e01ab-102">ICorDebugCode3 Interface</span></span>
<span data-ttu-id="e01ab-103">Zapewnia metodę, która rozszerza wartości "ICorDebugCode" i "ICorDebugCode2", aby podać informacje o zarządzanej zwracanej wartość.</span><span class="sxs-lookup"><span data-stu-id="e01ab-103">Provides a method that extends "ICorDebugCode" and "ICorDebugCode2" to provide information about a managed return value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="e01ab-104">Metody</span><span class="sxs-lookup"><span data-stu-id="e01ab-104">Methods</span></span>  
  
|<span data-ttu-id="e01ab-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="e01ab-105">Method</span></span>|<span data-ttu-id="e01ab-106">Opis</span><span class="sxs-lookup"><span data-stu-id="e01ab-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="e01ab-107">GetReturnValueLiveOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="e01ab-107">GetReturnValueLiveOffset Method</span></span>](icordebugcode3-getreturnvalueliveoffset-method.md)|<span data-ttu-id="e01ab-108">W przypadku określonego przesunięcia IL pobiera natywne przesunięcia, w których powinien być umieszczony punkt przerwania, aby debuger mógł uzyskać wartość zwracaną z funkcji.</span><span class="sxs-lookup"><span data-stu-id="e01ab-108">For a specified IL offset, gets the native offsets where a breakpoint should be placed so that the debugger can obtain the return value from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e01ab-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e01ab-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e01ab-110">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="e01ab-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e01ab-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e01ab-111">Requirements</span></span>  
 <span data-ttu-id="e01ab-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e01ab-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e01ab-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="e01ab-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e01ab-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e01ab-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e01ab-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e01ab-115">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e01ab-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e01ab-116">See also</span></span>

- [<span data-ttu-id="e01ab-117">ICorDebugILFrame3, interfejs</span><span class="sxs-lookup"><span data-stu-id="e01ab-117">ICorDebugILFrame3 Interface</span></span>](icordebugilframe3-interface.md)
- [<span data-ttu-id="e01ab-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="e01ab-118">Debugging Interfaces</span></span>](debugging-interfaces.md)

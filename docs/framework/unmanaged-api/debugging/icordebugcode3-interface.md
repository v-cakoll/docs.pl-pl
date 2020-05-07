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
ms.openlocfilehash: 6f66e4a903be2e9b12a573f74638a62c58005689
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82893451"
---
# <a name="icordebugcode3-interface"></a><span data-ttu-id="74e73-102">ICorDebugCode3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="74e73-102">ICorDebugCode3 Interface</span></span>
<span data-ttu-id="74e73-103">Zapewnia metodę, która rozszerza wartości "ICorDebugCode" i "ICorDebugCode2", aby podać informacje o zarządzanej zwracanej wartość.</span><span class="sxs-lookup"><span data-stu-id="74e73-103">Provides a method that extends "ICorDebugCode" and "ICorDebugCode2" to provide information about a managed return value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="74e73-104">Metody</span><span class="sxs-lookup"><span data-stu-id="74e73-104">Methods</span></span>  
  
|<span data-ttu-id="74e73-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="74e73-105">Method</span></span>|<span data-ttu-id="74e73-106">Opis</span><span class="sxs-lookup"><span data-stu-id="74e73-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="74e73-107">GetReturnValueLiveOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="74e73-107">GetReturnValueLiveOffset Method</span></span>](icordebugcode3-getreturnvalueliveoffset-method.md)|<span data-ttu-id="74e73-108">W przypadku określonego przesunięcia IL pobiera natywne przesunięcia, w których powinien być umieszczony punkt przerwania, aby debuger mógł uzyskać wartość zwracaną z funkcji.</span><span class="sxs-lookup"><span data-stu-id="74e73-108">For a specified IL offset, gets the native offsets where a breakpoint should be placed so that the debugger can obtain the return value from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="74e73-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="74e73-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="74e73-110">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="74e73-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74e73-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="74e73-111">Requirements</span></span>  
 <span data-ttu-id="74e73-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74e73-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74e73-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="74e73-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="74e73-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="74e73-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74e73-115">**.NET Framework wersje:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74e73-115">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74e73-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="74e73-116">See also</span></span>

- [<span data-ttu-id="74e73-117">ICorDebugILFrame3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="74e73-117">ICorDebugILFrame3 Interface</span></span>](icordebugilframe3-interface.md)
- [<span data-ttu-id="74e73-118">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="74e73-118">Debugging Interfaces</span></span>](debugging-interfaces.md)

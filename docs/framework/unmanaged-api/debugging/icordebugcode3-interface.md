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
ms.openlocfilehash: 5cb9aa09447acf28f1ed10ba409ce936cdb4f84a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59085041"
---
# <a name="icordebugcode3-interface"></a><span data-ttu-id="1f9d6-102">ICorDebugCode3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="1f9d6-102">ICorDebugCode3 Interface</span></span>
<span data-ttu-id="1f9d6-103">Dostarcza metodę, która rozszerza "ICorDebugCode" i "ICorDebugCode2", aby podać informacje o zarządzaniu wartością zwracaną.</span><span class="sxs-lookup"><span data-stu-id="1f9d6-103">Provides a method that extends "ICorDebugCode" and "ICorDebugCode2" to provide information about a managed return value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1f9d6-104">Metody</span><span class="sxs-lookup"><span data-stu-id="1f9d6-104">Methods</span></span>  
  
|<span data-ttu-id="1f9d6-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="1f9d6-105">Method</span></span>|<span data-ttu-id="1f9d6-106">Opis</span><span class="sxs-lookup"><span data-stu-id="1f9d6-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1f9d6-107">GetReturnValueLiveOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="1f9d6-107">GetReturnValueLiveOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)|<span data-ttu-id="1f9d6-108">Dla określonego przesunięcia języka Pośredniego pobiera natywne przesunięcia, w której punkt przerwania powinien znajdować się tak, że debugger może uzyskać wartość zwracaną przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="1f9d6-108">For a specified IL offset, gets the native offsets where a breakpoint should be placed so that the debugger can obtain the return value from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1f9d6-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1f9d6-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1f9d6-110">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="1f9d6-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f9d6-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1f9d6-111">Requirements</span></span>  
 <span data-ttu-id="1f9d6-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f9d6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f9d6-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1f9d6-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1f9d6-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1f9d6-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="1f9d6-115">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="1f9d6-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1f9d6-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1f9d6-116">See also</span></span>

- [<span data-ttu-id="1f9d6-117">ICorDebugILFrame3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="1f9d6-117">ICorDebugILFrame3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)
- [<span data-ttu-id="1f9d6-118">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="1f9d6-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

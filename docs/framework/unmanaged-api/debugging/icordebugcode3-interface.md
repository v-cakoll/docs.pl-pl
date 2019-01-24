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
ms.openlocfilehash: 7b3b29be2bab2d1b4cea5dcec89e31d4720be769
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54576879"
---
# <a name="icordebugcode3-interface"></a><span data-ttu-id="0c3d7-102">ICorDebugCode3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="0c3d7-102">ICorDebugCode3 Interface</span></span>
<span data-ttu-id="0c3d7-103">Dostarcza metodę, która rozszerza "ICorDebugCode" i "ICorDebugCode2", aby podać informacje o zarządzaniu wartością zwracaną.</span><span class="sxs-lookup"><span data-stu-id="0c3d7-103">Provides a method that extends "ICorDebugCode" and "ICorDebugCode2" to provide information about a managed return value.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0c3d7-104">Metody</span><span class="sxs-lookup"><span data-stu-id="0c3d7-104">Methods</span></span>  
  
|<span data-ttu-id="0c3d7-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="0c3d7-105">Method</span></span>|<span data-ttu-id="0c3d7-106">Opis</span><span class="sxs-lookup"><span data-stu-id="0c3d7-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0c3d7-107">GetReturnValueLiveOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="0c3d7-107">GetReturnValueLiveOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-getreturnvalueliveoffset-method.md)|<span data-ttu-id="0c3d7-108">Dla określonego przesunięcia języka Pośredniego pobiera natywne przesunięcia, w której punkt przerwania powinien znajdować się tak, że debugger może uzyskać wartość zwracaną przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="0c3d7-108">For a specified IL offset, gets the native offsets where a breakpoint should be placed so that the debugger can obtain the return value from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0c3d7-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0c3d7-109">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0c3d7-110">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="0c3d7-110">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c3d7-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0c3d7-111">Requirements</span></span>  
 <span data-ttu-id="0c3d7-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c3d7-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c3d7-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0c3d7-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0c3d7-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0c3d7-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0c3d7-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c3d7-115">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c3d7-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0c3d7-116">See also</span></span>



- [<span data-ttu-id="0c3d7-117">ICorDebugILFrame3, interfejs</span><span class="sxs-lookup"><span data-stu-id="0c3d7-117">ICorDebugILFrame3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-interface.md)
- [<span data-ttu-id="0c3d7-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="0c3d7-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

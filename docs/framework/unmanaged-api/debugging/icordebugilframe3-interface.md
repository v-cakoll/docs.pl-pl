---
title: ICorDebugILFrame3 — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugILFrame3
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 15212cb5-93d4-4025-bec9-d4b9919eb1fe
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9c87578c3a5e2bec9bbd754929308645f7862ee5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54701680"
---
# <a name="icordebugilframe3-interface"></a><span data-ttu-id="934f9-102">ICorDebugILFrame3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="934f9-102">ICorDebugILFrame3 Interface</span></span>
<span data-ttu-id="934f9-103">Dostarcza metodę, która hermetyzuje wartość zwracaną przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="934f9-103">Provides a method that encapsulates the return value of a function.</span></span> <span data-ttu-id="934f9-104">`ICorDebugILFrame3` jest logicznym rozszerzeniem interfejsów ICorDebugILFrame i ICorDebugILFrame2.</span><span class="sxs-lookup"><span data-stu-id="934f9-104">`ICorDebugILFrame3` is a logical extension of the ICorDebugILFrame and ICorDebugILFrame2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="934f9-105">Metody</span><span class="sxs-lookup"><span data-stu-id="934f9-105">Methods</span></span>  
  
|<span data-ttu-id="934f9-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="934f9-106">Method</span></span>|<span data-ttu-id="934f9-107">Opis</span><span class="sxs-lookup"><span data-stu-id="934f9-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="934f9-108">GetReturnValueForILOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="934f9-108">GetReturnValueForILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)|<span data-ttu-id="934f9-109">Pobiera obiekt ICorDebugValue, która hermetyzuje wartość zwracaną przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="934f9-109">Gets an ICorDebugValue object that encapsulates the return value of a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="934f9-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="934f9-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="934f9-111">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="934f9-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="934f9-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="934f9-112">Requirements</span></span>  
 <span data-ttu-id="934f9-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="934f9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="934f9-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="934f9-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="934f9-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="934f9-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="934f9-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="934f9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="934f9-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="934f9-117">See also</span></span>
- [<span data-ttu-id="934f9-118">ICorDebugCode3, interfejs</span><span class="sxs-lookup"><span data-stu-id="934f9-118">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [<span data-ttu-id="934f9-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="934f9-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

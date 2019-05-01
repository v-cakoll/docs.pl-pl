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
ms.openlocfilehash: b46c74ec0bfc1fc44bcaca07439c472b0fd8393f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61946448"
---
# <a name="icordebugilframe3-interface"></a><span data-ttu-id="35806-102">ICorDebugILFrame3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="35806-102">ICorDebugILFrame3 Interface</span></span>
<span data-ttu-id="35806-103">Dostarcza metodę, która hermetyzuje wartość zwracaną przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="35806-103">Provides a method that encapsulates the return value of a function.</span></span> <span data-ttu-id="35806-104">`ICorDebugILFrame3` jest logicznym rozszerzeniem interfejsów ICorDebugILFrame i ICorDebugILFrame2.</span><span class="sxs-lookup"><span data-stu-id="35806-104">`ICorDebugILFrame3` is a logical extension of the ICorDebugILFrame and ICorDebugILFrame2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="35806-105">Metody</span><span class="sxs-lookup"><span data-stu-id="35806-105">Methods</span></span>  
  
|<span data-ttu-id="35806-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="35806-106">Method</span></span>|<span data-ttu-id="35806-107">Opis</span><span class="sxs-lookup"><span data-stu-id="35806-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="35806-108">GetReturnValueForILOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="35806-108">GetReturnValueForILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)|<span data-ttu-id="35806-109">Pobiera obiekt ICorDebugValue, która hermetyzuje wartość zwracaną przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="35806-109">Gets an ICorDebugValue object that encapsulates the return value of a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="35806-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="35806-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="35806-111">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="35806-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="35806-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="35806-112">Requirements</span></span>  
 <span data-ttu-id="35806-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="35806-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="35806-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="35806-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="35806-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="35806-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="35806-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="35806-116">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35806-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="35806-117">See also</span></span>

- [<span data-ttu-id="35806-118">ICorDebugCode3, interfejs</span><span class="sxs-lookup"><span data-stu-id="35806-118">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [<span data-ttu-id="35806-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="35806-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

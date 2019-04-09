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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59113766"
---
# <a name="icordebugilframe3-interface"></a><span data-ttu-id="b9011-102">ICorDebugILFrame3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b9011-102">ICorDebugILFrame3 Interface</span></span>
<span data-ttu-id="b9011-103">Dostarcza metodę, która hermetyzuje wartość zwracaną przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="b9011-103">Provides a method that encapsulates the return value of a function.</span></span> `ICorDebugILFrame3` <span data-ttu-id="b9011-104">jest logicznym rozszerzeniem interfejsów ICorDebugILFrame i ICorDebugILFrame2.</span><span class="sxs-lookup"><span data-stu-id="b9011-104">is a logical extension of the ICorDebugILFrame and ICorDebugILFrame2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b9011-105">Metody</span><span class="sxs-lookup"><span data-stu-id="b9011-105">Methods</span></span>  
  
|<span data-ttu-id="b9011-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="b9011-106">Method</span></span>|<span data-ttu-id="b9011-107">Opis</span><span class="sxs-lookup"><span data-stu-id="b9011-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b9011-108">GetReturnValueForILOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="b9011-108">GetReturnValueForILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)|<span data-ttu-id="b9011-109">Pobiera obiekt ICorDebugValue, która hermetyzuje wartość zwracaną przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="b9011-109">Gets an ICorDebugValue object that encapsulates the return value of a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b9011-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b9011-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b9011-111">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="b9011-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b9011-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b9011-112">Requirements</span></span>  
 <span data-ttu-id="b9011-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b9011-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b9011-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b9011-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b9011-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b9011-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="b9011-116">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="b9011-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b9011-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b9011-117">See also</span></span>

- [<span data-ttu-id="b9011-118">ICorDebugCode3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b9011-118">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [<span data-ttu-id="b9011-119">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="b9011-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

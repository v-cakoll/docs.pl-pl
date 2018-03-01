---
title: "ICorDebugILFrame3 — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugILFrame3
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 15212cb5-93d4-4025-bec9-d4b9919eb1fe
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1096942775dd579fa530415873694b3e6e67a74a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilframe3-interface"></a><span data-ttu-id="192d1-102">ICorDebugILFrame3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="192d1-102">ICorDebugILFrame3 Interface</span></span>
<span data-ttu-id="192d1-103">Dostarcza metodę, która hermetyzuje wartość zwracaną przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="192d1-103">Provides a method that encapsulates the return value of a function.</span></span> <span data-ttu-id="192d1-104">`ICorDebugILFrame3`to rozszerzenie logicznej interfejsów ICorDebugILFrame i ICorDebugILFrame2.</span><span class="sxs-lookup"><span data-stu-id="192d1-104">`ICorDebugILFrame3` is a logical extension of the ICorDebugILFrame and ICorDebugILFrame2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="192d1-105">Metody</span><span class="sxs-lookup"><span data-stu-id="192d1-105">Methods</span></span>  
  
|<span data-ttu-id="192d1-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="192d1-106">Method</span></span>|<span data-ttu-id="192d1-107">Opis</span><span class="sxs-lookup"><span data-stu-id="192d1-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="192d1-108">GetReturnValueForILOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="192d1-108">GetReturnValueForILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)|<span data-ttu-id="192d1-109">Pobiera obiekt ICorDebugValue hermetyzujący wartość zwracaną przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="192d1-109">Gets an ICorDebugValue object that encapsulates the return value of a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="192d1-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="192d1-110">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="192d1-111">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="192d1-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="192d1-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="192d1-112">Requirements</span></span>  
 <span data-ttu-id="192d1-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="192d1-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="192d1-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="192d1-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="192d1-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="192d1-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="192d1-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="192d1-116">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="192d1-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="192d1-117">See Also</span></span>  
 [<span data-ttu-id="192d1-118">ICorDebugCode3, interfejs</span><span class="sxs-lookup"><span data-stu-id="192d1-118">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)  
 [<span data-ttu-id="192d1-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="192d1-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

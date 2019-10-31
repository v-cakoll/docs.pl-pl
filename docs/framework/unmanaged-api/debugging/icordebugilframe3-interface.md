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
ms.openlocfilehash: b3094eb6e3006be49cf17c1ca2a220b8ec58b673
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139057"
---
# <a name="icordebugilframe3-interface"></a><span data-ttu-id="4dce9-102">ICorDebugILFrame3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="4dce9-102">ICorDebugILFrame3 Interface</span></span>
<span data-ttu-id="4dce9-103">Dostarcza metodę, która hermetyzuje wartość zwracaną przez funkcję.</span><span class="sxs-lookup"><span data-stu-id="4dce9-103">Provides a method that encapsulates the return value of a function.</span></span> <span data-ttu-id="4dce9-104">`ICorDebugILFrame3` jest logicznym rozszerzeniem interfejsów ICorDebugILFrame i ICorDebugILFrame2.</span><span class="sxs-lookup"><span data-stu-id="4dce9-104">`ICorDebugILFrame3` is a logical extension of the ICorDebugILFrame and ICorDebugILFrame2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4dce9-105">Metody</span><span class="sxs-lookup"><span data-stu-id="4dce9-105">Methods</span></span>  
  
|<span data-ttu-id="4dce9-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="4dce9-106">Method</span></span>|<span data-ttu-id="4dce9-107">Opis</span><span class="sxs-lookup"><span data-stu-id="4dce9-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4dce9-108">GetReturnValueForILOffset, metoda</span><span class="sxs-lookup"><span data-stu-id="4dce9-108">GetReturnValueForILOffset Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe3-getreturnvalueforiloffset-method.md)|<span data-ttu-id="4dce9-109">Pobiera obiekt ICorDebugValue, który hermetyzuje zwracaną wartość funkcji.</span><span class="sxs-lookup"><span data-stu-id="4dce9-109">Gets an ICorDebugValue object that encapsulates the return value of a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4dce9-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4dce9-110">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4dce9-111">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="4dce9-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4dce9-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4dce9-112">Requirements</span></span>  
 <span data-ttu-id="4dce9-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4dce9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4dce9-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4dce9-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4dce9-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4dce9-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4dce9-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4dce9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v451plus](../../../../includes/net-current-v451plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4dce9-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4dce9-117">See also</span></span>

- [<span data-ttu-id="4dce9-118">ICorDebugCode3, interfejs</span><span class="sxs-lookup"><span data-stu-id="4dce9-118">ICorDebugCode3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode3-interface.md)
- [<span data-ttu-id="4dce9-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="4dce9-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

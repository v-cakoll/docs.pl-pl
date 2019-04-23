---
title: ICorDebugThread3 — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugThread3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread3
helpviewer_keywords:
- ICorDebugThread3 interface [.NET Framework debugging]
ms.assetid: eb2860ef-06cb-4968-a6c3-6d048ecda2a4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1d34a3395605505ca0ebda072e33d8083d51123a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59185877"
---
# <a name="icordebugthread3-interface"></a><span data-ttu-id="3ba75-102">ICorDebugThread3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="3ba75-102">ICorDebugThread3 Interface</span></span>
<span data-ttu-id="3ba75-103">Zapewnia punkt wejścia do [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) i odpowiednich interfejsów.</span><span class="sxs-lookup"><span data-stu-id="3ba75-103">Provides the entry point to the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="3ba75-104">Metody</span><span class="sxs-lookup"><span data-stu-id="3ba75-104">Methods</span></span>  
  
|<span data-ttu-id="3ba75-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="3ba75-105">Method</span></span>|<span data-ttu-id="3ba75-106">Opis</span><span class="sxs-lookup"><span data-stu-id="3ba75-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3ba75-107">CreateStackWalk, metoda</span><span class="sxs-lookup"><span data-stu-id="3ba75-107">CreateStackWalk Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-createstackwalk-method.md)|<span data-ttu-id="3ba75-108">Tworzy [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) obiektu wątku stosu, którego chcesz unwind.</span><span class="sxs-lookup"><span data-stu-id="3ba75-108">Creates an [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>|  
|[<span data-ttu-id="3ba75-109">GetActiveInternalFrames, metoda</span><span class="sxs-lookup"><span data-stu-id="3ba75-109">GetActiveInternalFrames Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md)|<span data-ttu-id="3ba75-110">Zwraca informacje o ramkach wewnętrznych ([icordebuginternalframe2 —](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) obiektów) na stosie.</span><span class="sxs-lookup"><span data-stu-id="3ba75-110">Returns an array of internal frames ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objects) on the stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ba75-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3ba75-111">Remarks</span></span>  
 <span data-ttu-id="3ba75-112">`ICorDebugThread3` jest logicznym rozszerzeniem do icordebugthread — interfejs.</span><span class="sxs-lookup"><span data-stu-id="3ba75-112">`ICorDebugThread3` is a logical extension to the ICorDebugThread interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3ba75-113">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="3ba75-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3ba75-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3ba75-114">Requirements</span></span>  
 <span data-ttu-id="3ba75-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ba75-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ba75-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3ba75-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3ba75-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3ba75-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3ba75-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ba75-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ba75-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3ba75-119">See also</span></span>

- [<span data-ttu-id="3ba75-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="3ba75-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="3ba75-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="3ba75-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

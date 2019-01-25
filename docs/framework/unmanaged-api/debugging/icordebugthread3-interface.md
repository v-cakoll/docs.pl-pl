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
ms.openlocfilehash: d5f4cecda80238e7a53cf2aa2a8219c49c2b3f9b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54531723"
---
# <a name="icordebugthread3-interface"></a><span data-ttu-id="8a2e4-102">ICorDebugThread3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="8a2e4-102">ICorDebugThread3 Interface</span></span>
<span data-ttu-id="8a2e4-103">Zapewnia punkt wejścia do [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) i odpowiednich interfejsów.</span><span class="sxs-lookup"><span data-stu-id="8a2e4-103">Provides the entry point to the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="8a2e4-104">Metody</span><span class="sxs-lookup"><span data-stu-id="8a2e4-104">Methods</span></span>  
  
|<span data-ttu-id="8a2e4-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="8a2e4-105">Method</span></span>|<span data-ttu-id="8a2e4-106">Opis</span><span class="sxs-lookup"><span data-stu-id="8a2e4-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="8a2e4-107">CreateStackWalk, metoda</span><span class="sxs-lookup"><span data-stu-id="8a2e4-107">CreateStackWalk Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-createstackwalk-method.md)|<span data-ttu-id="8a2e4-108">Tworzy [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) obiektu wątku stosu, którego chcesz unwind.</span><span class="sxs-lookup"><span data-stu-id="8a2e4-108">Creates an [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>|  
|[<span data-ttu-id="8a2e4-109">GetActiveInternalFrames, metoda</span><span class="sxs-lookup"><span data-stu-id="8a2e4-109">GetActiveInternalFrames Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md)|<span data-ttu-id="8a2e4-110">Zwraca informacje o ramkach wewnętrznych ([icordebuginternalframe2 —](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) obiektów) na stosie.</span><span class="sxs-lookup"><span data-stu-id="8a2e4-110">Returns an array of internal frames ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objects) on the stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8a2e4-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8a2e4-111">Remarks</span></span>  
 <span data-ttu-id="8a2e4-112">`ICorDebugThread3` jest logicznym rozszerzeniem do icordebugthread — interfejs.</span><span class="sxs-lookup"><span data-stu-id="8a2e4-112">`ICorDebugThread3` is a logical extension to the ICorDebugThread interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8a2e4-113">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="8a2e4-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a2e4-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8a2e4-114">Requirements</span></span>  
 <span data-ttu-id="8a2e4-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a2e4-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a2e4-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8a2e4-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8a2e4-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8a2e4-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a2e4-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a2e4-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a2e4-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8a2e4-119">See also</span></span>
- [<span data-ttu-id="8a2e4-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="8a2e4-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="8a2e4-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="8a2e4-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

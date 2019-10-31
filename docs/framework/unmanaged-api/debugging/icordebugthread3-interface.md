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
ms.openlocfilehash: 7cddf860f044e8493a0fdf6023b2853ac16c5b14
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137502"
---
# <a name="icordebugthread3-interface"></a><span data-ttu-id="192be-102">ICorDebugThread3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="192be-102">ICorDebugThread3 Interface</span></span>
<span data-ttu-id="192be-103">Udostępnia punkt wejścia do [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) i odpowiednich interfejsów.</span><span class="sxs-lookup"><span data-stu-id="192be-103">Provides the entry point to the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="192be-104">Metody</span><span class="sxs-lookup"><span data-stu-id="192be-104">Methods</span></span>  
  
|<span data-ttu-id="192be-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="192be-105">Method</span></span>|<span data-ttu-id="192be-106">Opis</span><span class="sxs-lookup"><span data-stu-id="192be-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="192be-107">CreateStackWalk, metoda</span><span class="sxs-lookup"><span data-stu-id="192be-107">CreateStackWalk Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-createstackwalk-method.md)|<span data-ttu-id="192be-108">Tworzy obiekt [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) dla wątku, którego stos ma zostać rozwinięcia.</span><span class="sxs-lookup"><span data-stu-id="192be-108">Creates an [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>|  
|[<span data-ttu-id="192be-109">GetActiveInternalFrames, metoda</span><span class="sxs-lookup"><span data-stu-id="192be-109">GetActiveInternalFrames Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md)|<span data-ttu-id="192be-110">Zwraca tablicę ramek wewnętrznych ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) obiektów) na stosie.</span><span class="sxs-lookup"><span data-stu-id="192be-110">Returns an array of internal frames ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objects) on the stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="192be-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="192be-111">Remarks</span></span>  
 <span data-ttu-id="192be-112">`ICorDebugThread3` jest logicznym rozszerzeniem interfejsu ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="192be-112">`ICorDebugThread3` is a logical extension to the ICorDebugThread interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="192be-113">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="192be-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="192be-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="192be-114">Requirements</span></span>  
 <span data-ttu-id="192be-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="192be-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="192be-116">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="192be-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="192be-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="192be-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="192be-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="192be-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="192be-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="192be-119">See also</span></span>

- [<span data-ttu-id="192be-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="192be-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="192be-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="192be-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

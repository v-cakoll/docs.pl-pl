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
ms.openlocfilehash: 9622716e3a2cca7e3af0b1e1b134458a50ad1bec
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962982"
---
# <a name="icordebugthread3-interface"></a><span data-ttu-id="07092-102">ICorDebugThread3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="07092-102">ICorDebugThread3 Interface</span></span>
<span data-ttu-id="07092-103">Udostępnia punkt wejścia do [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) i odpowiednich interfejsów.</span><span class="sxs-lookup"><span data-stu-id="07092-103">Provides the entry point to the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="07092-104">Metody</span><span class="sxs-lookup"><span data-stu-id="07092-104">Methods</span></span>  
  
|<span data-ttu-id="07092-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="07092-105">Method</span></span>|<span data-ttu-id="07092-106">Opis</span><span class="sxs-lookup"><span data-stu-id="07092-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="07092-107">CreateStackWalk, metoda</span><span class="sxs-lookup"><span data-stu-id="07092-107">CreateStackWalk Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-createstackwalk-method.md)|<span data-ttu-id="07092-108">Tworzy obiekt [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) dla wątku, którego stos ma zostać rozwinięcia.</span><span class="sxs-lookup"><span data-stu-id="07092-108">Creates an [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>|  
|[<span data-ttu-id="07092-109">GetActiveInternalFrames, metoda</span><span class="sxs-lookup"><span data-stu-id="07092-109">GetActiveInternalFrames Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md)|<span data-ttu-id="07092-110">Zwraca tablicę ramek wewnętrznych ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) obiektów) na stosie.</span><span class="sxs-lookup"><span data-stu-id="07092-110">Returns an array of internal frames ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objects) on the stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="07092-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="07092-111">Remarks</span></span>  
 <span data-ttu-id="07092-112">`ICorDebugThread3`jest logicznym rozszerzeniem interfejsu ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="07092-112">`ICorDebugThread3` is a logical extension to the ICorDebugThread interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="07092-113">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="07092-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="07092-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="07092-114">Requirements</span></span>  
 <span data-ttu-id="07092-115">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="07092-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="07092-116">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="07092-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="07092-117">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="07092-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="07092-118">**.NET Framework wersje:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="07092-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="07092-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="07092-119">See also</span></span>

- [<span data-ttu-id="07092-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="07092-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="07092-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="07092-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

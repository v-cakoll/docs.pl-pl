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
ms.openlocfilehash: dc556dfb59e999ed9b7fc5f35c603dc26c35f314
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378709"
---
# <a name="icordebugthread3-interface"></a><span data-ttu-id="b005c-102">ICorDebugThread3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b005c-102">ICorDebugThread3 Interface</span></span>
<span data-ttu-id="b005c-103">Udostępnia punkt wejścia do [ICorDebugStackWalk](icordebugstackwalk-interface.md) i odpowiednich interfejsów.</span><span class="sxs-lookup"><span data-stu-id="b005c-103">Provides the entry point to the [ICorDebugStackWalk](icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b005c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b005c-104">Methods</span></span>  
  
|<span data-ttu-id="b005c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b005c-105">Method</span></span>|<span data-ttu-id="b005c-106">Opis</span><span class="sxs-lookup"><span data-stu-id="b005c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b005c-107">CreateStackWalk, metoda</span><span class="sxs-lookup"><span data-stu-id="b005c-107">CreateStackWalk Method</span></span>](icordebugthread3-createstackwalk-method.md)|<span data-ttu-id="b005c-108">Tworzy obiekt [ICorDebugStackWalk](icordebugstackwalk-interface.md) dla wątku, którego stos ma zostać rozwinięcia.</span><span class="sxs-lookup"><span data-stu-id="b005c-108">Creates an [ICorDebugStackWalk](icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>|  
|[<span data-ttu-id="b005c-109">GetActiveInternalFrames, metoda</span><span class="sxs-lookup"><span data-stu-id="b005c-109">GetActiveInternalFrames Method</span></span>](icordebugthread3-getactiveinternalframes-method.md)|<span data-ttu-id="b005c-110">Zwraca tablicę ramek wewnętrznych ([ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) obiektów) na stosie.</span><span class="sxs-lookup"><span data-stu-id="b005c-110">Returns an array of internal frames ([ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) objects) on the stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b005c-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b005c-111">Remarks</span></span>  
 <span data-ttu-id="b005c-112">`ICorDebugThread3`jest logicznym rozszerzeniem interfejsu ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="b005c-112">`ICorDebugThread3` is a logical extension to the ICorDebugThread interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b005c-113">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="b005c-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b005c-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b005c-114">Requirements</span></span>  
 <span data-ttu-id="b005c-115">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b005c-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b005c-116">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b005c-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b005c-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b005c-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b005c-118">**.NET Framework wersje:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b005c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b005c-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b005c-119">See also</span></span>

- [<span data-ttu-id="b005c-120">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="b005c-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="b005c-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="b005c-121">Debugging</span></span>](index.md)

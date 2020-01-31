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
ms.openlocfilehash: 19bd869aec7e4d046890d2314f5142753ba0b112
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791392"
---
# <a name="icordebugthread3-interface"></a><span data-ttu-id="34095-102">ICorDebugThread3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="34095-102">ICorDebugThread3 Interface</span></span>
<span data-ttu-id="34095-103">Udostępnia punkt wejścia do [ICorDebugStackWalk](icordebugstackwalk-interface.md) i odpowiednich interfejsów.</span><span class="sxs-lookup"><span data-stu-id="34095-103">Provides the entry point to the [ICorDebugStackWalk](icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="34095-104">Metody</span><span class="sxs-lookup"><span data-stu-id="34095-104">Methods</span></span>  
  
|<span data-ttu-id="34095-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="34095-105">Method</span></span>|<span data-ttu-id="34095-106">Opis</span><span class="sxs-lookup"><span data-stu-id="34095-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="34095-107">CreateStackWalk, metoda</span><span class="sxs-lookup"><span data-stu-id="34095-107">CreateStackWalk Method</span></span>](icordebugthread3-createstackwalk-method.md)|<span data-ttu-id="34095-108">Tworzy obiekt [ICorDebugStackWalk](icordebugstackwalk-interface.md) dla wątku, którego stos ma zostać rozwinięcia.</span><span class="sxs-lookup"><span data-stu-id="34095-108">Creates an [ICorDebugStackWalk](icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>|  
|[<span data-ttu-id="34095-109">GetActiveInternalFrames, metoda</span><span class="sxs-lookup"><span data-stu-id="34095-109">GetActiveInternalFrames Method</span></span>](icordebugthread3-getactiveinternalframes-method.md)|<span data-ttu-id="34095-110">Zwraca tablicę ramek wewnętrznych ([ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) obiektów) na stosie.</span><span class="sxs-lookup"><span data-stu-id="34095-110">Returns an array of internal frames ([ICorDebugInternalFrame2](icordebuginternalframe2-interface.md) objects) on the stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="34095-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="34095-111">Remarks</span></span>  
 <span data-ttu-id="34095-112">`ICorDebugThread3` jest logicznym rozszerzeniem interfejsu ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="34095-112">`ICorDebugThread3` is a logical extension to the ICorDebugThread interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="34095-113">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="34095-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="34095-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="34095-114">Requirements</span></span>  
 <span data-ttu-id="34095-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="34095-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="34095-116">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="34095-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="34095-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="34095-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="34095-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="34095-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="34095-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="34095-119">See also</span></span>

- [<span data-ttu-id="34095-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="34095-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="34095-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="34095-121">Debugging</span></span>](index.md)

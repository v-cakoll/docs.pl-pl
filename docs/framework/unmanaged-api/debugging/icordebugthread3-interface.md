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
ms.openlocfilehash: c9cb9217282af53d9788190844e4e52d5405ee2a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422779"
---
# <a name="icordebugthread3-interface"></a><span data-ttu-id="b4d4b-102">ICorDebugThread3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="b4d4b-102">ICorDebugThread3 Interface</span></span>
<span data-ttu-id="b4d4b-103">Zapewnia punkt wejścia do [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) i odpowiednie interfejsy.</span><span class="sxs-lookup"><span data-stu-id="b4d4b-103">Provides the entry point to the [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) and corresponding interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b4d4b-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b4d4b-104">Methods</span></span>  
  
|<span data-ttu-id="b4d4b-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b4d4b-105">Method</span></span>|<span data-ttu-id="b4d4b-106">Opis</span><span class="sxs-lookup"><span data-stu-id="b4d4b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b4d4b-107">CreateStackWalk, metoda</span><span class="sxs-lookup"><span data-stu-id="b4d4b-107">CreateStackWalk Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-createstackwalk-method.md)|<span data-ttu-id="b4d4b-108">Tworzy [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) obiektu stosu, którego chcesz unwind wątku.</span><span class="sxs-lookup"><span data-stu-id="b4d4b-108">Creates an [ICorDebugStackWalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-interface.md) object for the thread whose stack you want to unwind.</span></span>|  
|[<span data-ttu-id="b4d4b-109">GetActiveInternalFrames, metoda</span><span class="sxs-lookup"><span data-stu-id="b4d4b-109">GetActiveInternalFrames Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugthread3-getactiveinternalframes-method.md)|<span data-ttu-id="b4d4b-110">Zwraca tablicę wewnętrzny ramki ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) obiektów) na stosie.</span><span class="sxs-lookup"><span data-stu-id="b4d4b-110">Returns an array of internal frames ([ICorDebugInternalFrame2](../../../../docs/framework/unmanaged-api/debugging/icordebuginternalframe2-interface.md) objects) on the stack.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b4d4b-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b4d4b-111">Remarks</span></span>  
 <span data-ttu-id="b4d4b-112">`ICorDebugThread3` to rozszerzenie logicznych do interfejsu ICorDebugThread.</span><span class="sxs-lookup"><span data-stu-id="b4d4b-112">`ICorDebugThread3` is a logical extension to the ICorDebugThread interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b4d4b-113">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="b4d4b-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4d4b-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b4d4b-114">Requirements</span></span>  
 <span data-ttu-id="b4d4b-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4d4b-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4d4b-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b4d4b-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b4d4b-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b4d4b-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4d4b-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4d4b-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4d4b-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b4d4b-119">See Also</span></span>  
 [<span data-ttu-id="b4d4b-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="b4d4b-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="b4d4b-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="b4d4b-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

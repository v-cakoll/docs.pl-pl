---
title: ICorDebugHeapValue3 — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue3
helpviewer_keywords:
- ICorDebugHeapValue3 interface [.NET Framework debugging]
ms.assetid: 9c421bb0-e647-4b2d-a986-f3d578cc7f20
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 60d3b22d8dc140bf16af7f59781d5ed103dafbf4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59191708"
---
# <a name="icordebugheapvalue3-interface"></a><span data-ttu-id="249a1-102">ICorDebugHeapValue3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="249a1-102">ICorDebugHeapValue3 Interface</span></span>
<span data-ttu-id="249a1-103">Udostępnia właściwości blokady monitora obiektów.</span><span class="sxs-lookup"><span data-stu-id="249a1-103">Exposes the monitor lock properties of objects.</span></span> <span data-ttu-id="249a1-104">Ten interfejs rozszerza ICorDebugHeapValue i icordebugheapvalue2 — interfejsy.</span><span class="sxs-lookup"><span data-stu-id="249a1-104">This interface extends the ICorDebugHeapValue and ICorDebugHeapValue2 interfaces.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="249a1-105">Metody</span><span class="sxs-lookup"><span data-stu-id="249a1-105">Methods</span></span>  
  
|<span data-ttu-id="249a1-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="249a1-106">Method</span></span>|<span data-ttu-id="249a1-107">Opis</span><span class="sxs-lookup"><span data-stu-id="249a1-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="249a1-108">GetThreadOwningMonitorLock, metoda</span><span class="sxs-lookup"><span data-stu-id="249a1-108">GetThreadOwningMonitorLock Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-getthreadowningmonitorlock-method.md)|<span data-ttu-id="249a1-109">Zwraca wątków zarządzanych, który jest właścicielem blokady monitora dla tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="249a1-109">Returns the managed thread that owns the monitor lock on this object.</span></span>|  
|[<span data-ttu-id="249a1-110">GetMonitorEventWaitList, metoda</span><span class="sxs-lookup"><span data-stu-id="249a1-110">GetMonitorEventWaitList Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapvalue3-getmonitoreventwaitlist-method.md)|<span data-ttu-id="249a1-111">Udostępnia uporządkowaną listę wątków, które są umieszczane w kolejce na zdarzenia skojarzonego z blokadą monitora.</span><span class="sxs-lookup"><span data-stu-id="249a1-111">Provides an ordered list of threads that are queued on the event that is associated with a monitor lock.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="249a1-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="249a1-112">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="249a1-113">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="249a1-113">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="249a1-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="249a1-114">Requirements</span></span>  
 <span data-ttu-id="249a1-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="249a1-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="249a1-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="249a1-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="249a1-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="249a1-117">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="249a1-118">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="249a1-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="249a1-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="249a1-119">See also</span></span>

- [<span data-ttu-id="249a1-120">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="249a1-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="249a1-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="249a1-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

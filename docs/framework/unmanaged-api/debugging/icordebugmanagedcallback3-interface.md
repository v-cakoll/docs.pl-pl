---
title: ICorDebugManagedCallback3 — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback3
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback3
helpviewer_keywords:
- ICorDebugManagedCallback3 interface [.NET Framework debugging]
ms.assetid: a95389d3-cf2e-47a4-9805-61426acc6b65
topic_type:
- apiref
ms.openlocfilehash: 8da04b0c620404e0dad8227c7a627f75507389a7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128030"
---
# <a name="icordebugmanagedcallback3-interface"></a><span data-ttu-id="d1803-102">ICorDebugManagedCallback3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d1803-102">ICorDebugManagedCallback3 Interface</span></span>
<span data-ttu-id="d1803-103">Dostarcza metodę wywołania zwrotnego, która wskazuje, że zgłoszono powiadomienie włączenia niestandardowego debugera.</span><span class="sxs-lookup"><span data-stu-id="d1803-103">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d1803-104">Metody</span><span class="sxs-lookup"><span data-stu-id="d1803-104">Methods</span></span>  
  
|<span data-ttu-id="d1803-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="d1803-105">Method</span></span>|<span data-ttu-id="d1803-106">Opis</span><span class="sxs-lookup"><span data-stu-id="d1803-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d1803-107">CustomNotification, metoda</span><span class="sxs-lookup"><span data-stu-id="d1803-107">CustomNotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md)|<span data-ttu-id="d1803-108">Wskazuje, że zostało zgłoszone włączone powiadomienie debugera niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="d1803-108">Indicates that an enabled custom debugger notification has been raised.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d1803-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d1803-109">Remarks</span></span>  
 <span data-ttu-id="d1803-110">Ten interfejs jest logicznym rozszerzeniem interfejsów [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) i [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="d1803-110">This interface is a logical extension of the [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) and [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d1803-111">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="d1803-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1803-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d1803-112">Requirements</span></span>  
 <span data-ttu-id="d1803-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d1803-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d1803-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d1803-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d1803-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d1803-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d1803-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d1803-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d1803-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d1803-117">See also</span></span>

- [<span data-ttu-id="d1803-118">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1803-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
- [<span data-ttu-id="d1803-119">ICorDebugManagedCallback2, interfejs</span><span class="sxs-lookup"><span data-stu-id="d1803-119">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="d1803-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="d1803-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="d1803-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="d1803-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

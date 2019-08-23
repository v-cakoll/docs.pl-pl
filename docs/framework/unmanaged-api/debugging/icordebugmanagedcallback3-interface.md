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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 138ac80a9abb64d4c004e83e53ed1eea2b124ff2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69909908"
---
# <a name="icordebugmanagedcallback3-interface"></a><span data-ttu-id="38082-102">ICorDebugManagedCallback3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="38082-102">ICorDebugManagedCallback3 Interface</span></span>
<span data-ttu-id="38082-103">Dostarcza metodę wywołania zwrotnego, która wskazuje, że zgłoszono powiadomienie włączenia niestandardowego debugera.</span><span class="sxs-lookup"><span data-stu-id="38082-103">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="38082-104">Metody</span><span class="sxs-lookup"><span data-stu-id="38082-104">Methods</span></span>  
  
|<span data-ttu-id="38082-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="38082-105">Method</span></span>|<span data-ttu-id="38082-106">Opis</span><span class="sxs-lookup"><span data-stu-id="38082-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="38082-107">CustomNotification, metoda</span><span class="sxs-lookup"><span data-stu-id="38082-107">CustomNotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md)|<span data-ttu-id="38082-108">Wskazuje, że zostało zgłoszone włączone powiadomienie debugera niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="38082-108">Indicates that an enabled custom debugger notification has been raised.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="38082-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="38082-109">Remarks</span></span>  
 <span data-ttu-id="38082-110">Ten interfejs jest logicznym rozszerzeniem interfejsów [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) i [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="38082-110">This interface is a logical extension of the [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) and [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="38082-111">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="38082-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38082-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="38082-112">Requirements</span></span>  
 <span data-ttu-id="38082-113">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="38082-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="38082-114">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="38082-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="38082-115">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="38082-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="38082-116">**.NET Framework wersje:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="38082-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38082-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="38082-117">See also</span></span>

- [<span data-ttu-id="38082-118">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="38082-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
- [<span data-ttu-id="38082-119">ICorDebugManagedCallback2, interfejs</span><span class="sxs-lookup"><span data-stu-id="38082-119">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="38082-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="38082-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="38082-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="38082-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

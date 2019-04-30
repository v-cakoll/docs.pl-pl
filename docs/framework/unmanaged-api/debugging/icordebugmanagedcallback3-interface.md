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
ms.openlocfilehash: acab49097059081540ec364d7f134d31432988a3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61723267"
---
# <a name="icordebugmanagedcallback3-interface"></a><span data-ttu-id="7101b-102">ICorDebugManagedCallback3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="7101b-102">ICorDebugManagedCallback3 Interface</span></span>
<span data-ttu-id="7101b-103">Dostarcza metodę wywołania zwrotnego, która wskazuje, że zgłoszono powiadomienie włączenia niestandardowego debugera.</span><span class="sxs-lookup"><span data-stu-id="7101b-103">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7101b-104">Metody</span><span class="sxs-lookup"><span data-stu-id="7101b-104">Methods</span></span>  
  
|<span data-ttu-id="7101b-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="7101b-105">Method</span></span>|<span data-ttu-id="7101b-106">Opis</span><span class="sxs-lookup"><span data-stu-id="7101b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7101b-107">CustomNotification, metoda</span><span class="sxs-lookup"><span data-stu-id="7101b-107">CustomNotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md)|<span data-ttu-id="7101b-108">Wskazuje, że zgłoszono powiadomienie włączenia niestandardowego debugera.</span><span class="sxs-lookup"><span data-stu-id="7101b-108">Indicates that an enabled custom debugger notification has been raised.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7101b-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7101b-109">Remarks</span></span>  
 <span data-ttu-id="7101b-110">Ten interfejs jest logicznym rozszerzeniem [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) i [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) interfejsów.</span><span class="sxs-lookup"><span data-stu-id="7101b-110">This interface is a logical extension of the [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) and [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7101b-111">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="7101b-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7101b-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7101b-112">Requirements</span></span>  
 <span data-ttu-id="7101b-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7101b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7101b-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7101b-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7101b-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7101b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7101b-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7101b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7101b-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7101b-117">See also</span></span>

- [<span data-ttu-id="7101b-118">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="7101b-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
- [<span data-ttu-id="7101b-119">ICorDebugManagedCallback2, interfejs</span><span class="sxs-lookup"><span data-stu-id="7101b-119">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="7101b-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="7101b-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="7101b-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="7101b-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

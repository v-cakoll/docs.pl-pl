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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59108280"
---
# <a name="icordebugmanagedcallback3-interface"></a><span data-ttu-id="63766-102">ICorDebugManagedCallback3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="63766-102">ICorDebugManagedCallback3 Interface</span></span>
<span data-ttu-id="63766-103">Dostarcza metodę wywołania zwrotnego, która wskazuje, że zgłoszono powiadomienie włączenia niestandardowego debugera.</span><span class="sxs-lookup"><span data-stu-id="63766-103">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="63766-104">Metody</span><span class="sxs-lookup"><span data-stu-id="63766-104">Methods</span></span>  
  
|<span data-ttu-id="63766-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="63766-105">Method</span></span>|<span data-ttu-id="63766-106">Opis</span><span class="sxs-lookup"><span data-stu-id="63766-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="63766-107">CustomNotification, metoda</span><span class="sxs-lookup"><span data-stu-id="63766-107">CustomNotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md)|<span data-ttu-id="63766-108">Wskazuje, że zgłoszono powiadomienie włączenia niestandardowego debugera.</span><span class="sxs-lookup"><span data-stu-id="63766-108">Indicates that an enabled custom debugger notification has been raised.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="63766-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="63766-109">Remarks</span></span>  
 <span data-ttu-id="63766-110">Ten interfejs jest logicznym rozszerzeniem [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) i [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) interfejsów.</span><span class="sxs-lookup"><span data-stu-id="63766-110">This interface is a logical extension of the [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) and [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="63766-111">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="63766-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63766-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="63766-112">Requirements</span></span>  
 <span data-ttu-id="63766-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63766-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63766-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="63766-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="63766-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="63766-115">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="63766-116">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="63766-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="63766-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="63766-117">See also</span></span>

- [<span data-ttu-id="63766-118">ICorDebugManagedCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="63766-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
- [<span data-ttu-id="63766-119">ICorDebugManagedCallback2 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="63766-119">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="63766-120">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="63766-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="63766-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="63766-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

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
ms.openlocfilehash: ab1dab753728102fc27e39c3ed64bf776e2e5ad5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54634479"
---
# <a name="icordebugmanagedcallback3-interface"></a><span data-ttu-id="d588d-102">ICorDebugManagedCallback3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="d588d-102">ICorDebugManagedCallback3 Interface</span></span>
<span data-ttu-id="d588d-103">Dostarcza metodę wywołania zwrotnego, która wskazuje, że zgłoszono powiadomienie włączenia niestandardowego debugera.</span><span class="sxs-lookup"><span data-stu-id="d588d-103">Provides a callback method that indicates that an enabled custom debugger notification has been raised.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d588d-104">Metody</span><span class="sxs-lookup"><span data-stu-id="d588d-104">Methods</span></span>  
  
|<span data-ttu-id="d588d-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="d588d-105">Method</span></span>|<span data-ttu-id="d588d-106">Opis</span><span class="sxs-lookup"><span data-stu-id="d588d-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d588d-107">CustomNotification, metoda</span><span class="sxs-lookup"><span data-stu-id="d588d-107">CustomNotification Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback3-customnotification-method.md)|<span data-ttu-id="d588d-108">Wskazuje, że zgłoszono powiadomienie włączenia niestandardowego debugera.</span><span class="sxs-lookup"><span data-stu-id="d588d-108">Indicates that an enabled custom debugger notification has been raised.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d588d-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d588d-109">Remarks</span></span>  
 <span data-ttu-id="d588d-110">Ten interfejs jest logicznym rozszerzeniem [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) i [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) interfejsów.</span><span class="sxs-lookup"><span data-stu-id="d588d-110">This interface is a logical extension of the [ICorDebugManagedCallback](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md) and [ICorDebugManagedCallback2](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md) interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d588d-111">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="d588d-111">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d588d-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d588d-112">Requirements</span></span>  
 <span data-ttu-id="d588d-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d588d-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d588d-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d588d-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d588d-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d588d-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d588d-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d588d-116">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d588d-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d588d-117">See also</span></span>
- [<span data-ttu-id="d588d-118">ICorDebugManagedCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="d588d-118">ICorDebugManagedCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
- [<span data-ttu-id="d588d-119">ICorDebugManagedCallback2, interfejs</span><span class="sxs-lookup"><span data-stu-id="d588d-119">ICorDebugManagedCallback2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [<span data-ttu-id="d588d-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="d588d-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="d588d-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="d588d-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

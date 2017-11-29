---
title: Interfejs ICorDebugModuleDebugEvent
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 41950c52-1ac8-4212-b814-c77e20879f91
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: dced93ab39529ec57fb6fb99603a197fb957be8d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmoduledebugevent-interface"></a><span data-ttu-id="dce12-102">Interfejs ICorDebugModuleDebugEvent</span><span class="sxs-lookup"><span data-stu-id="dce12-102">ICorDebugModuleDebugEvent Interface</span></span>
<span data-ttu-id="dce12-103">Rozszerza [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interfejs do obsługi zdarzenia na poziomie modułu.</span><span class="sxs-lookup"><span data-stu-id="dce12-103">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support module-level events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="dce12-104">Metody</span><span class="sxs-lookup"><span data-stu-id="dce12-104">Methods</span></span>  
  
|<span data-ttu-id="dce12-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="dce12-105">Method</span></span>|<span data-ttu-id="dce12-106">Opis</span><span class="sxs-lookup"><span data-stu-id="dce12-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="dce12-107">GetModule — metoda</span><span class="sxs-lookup"><span data-stu-id="dce12-107">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-getmodule-method.md)|<span data-ttu-id="dce12-108">Pobiera moduł scalone, który został właśnie załadowany lub usunięty z pamięci.</span><span class="sxs-lookup"><span data-stu-id="dce12-108">Gets the merged module that was just loaded or unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dce12-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dce12-109">Remarks</span></span>  
 <span data-ttu-id="dce12-110">[MODULE_LOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) i [MODULE_UNLOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) typów zdarzeń implementuje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="dce12-110">The [MODULE_LOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) and [MODULE_UNLOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) event types implement this interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="dce12-111">Interfejs jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="dce12-111">The interface is available with .NET Native only.</span></span> <span data-ttu-id="dce12-112">Próba wywołania `QueryInterface` można pobrać wskaźnika interfejsu zwraca `E_NOINTERFACE` dla scenariuszy ICorDebug poza platformy .NET Native.</span><span class="sxs-lookup"><span data-stu-id="dce12-112">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dce12-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dce12-113">Requirements</span></span>  
 <span data-ttu-id="dce12-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dce12-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dce12-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dce12-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dce12-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dce12-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dce12-117">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dce12-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dce12-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dce12-118">See Also</span></span>  
 [<span data-ttu-id="dce12-119">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="dce12-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="dce12-120">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="dce12-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

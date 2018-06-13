---
title: Interfejs ICorDebugModuleDebugEvent
ms.date: 03/30/2017
ms.assetid: 41950c52-1ac8-4212-b814-c77e20879f91
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f35c26b98521311267a627265f2dae8fa9e333de
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421843"
---
# <a name="icordebugmoduledebugevent-interface"></a><span data-ttu-id="bfa54-102">Interfejs ICorDebugModuleDebugEvent</span><span class="sxs-lookup"><span data-stu-id="bfa54-102">ICorDebugModuleDebugEvent Interface</span></span>
<span data-ttu-id="bfa54-103">Rozszerza [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interfejs do obsługi zdarzenia na poziomie modułu.</span><span class="sxs-lookup"><span data-stu-id="bfa54-103">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support module-level events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bfa54-104">Metody</span><span class="sxs-lookup"><span data-stu-id="bfa54-104">Methods</span></span>  
  
|<span data-ttu-id="bfa54-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="bfa54-105">Method</span></span>|<span data-ttu-id="bfa54-106">Opis</span><span class="sxs-lookup"><span data-stu-id="bfa54-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bfa54-107">GetModule, metoda</span><span class="sxs-lookup"><span data-stu-id="bfa54-107">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-getmodule-method.md)|<span data-ttu-id="bfa54-108">Pobiera moduł scalone, który został właśnie załadowany lub usunięty z pamięci.</span><span class="sxs-lookup"><span data-stu-id="bfa54-108">Gets the merged module that was just loaded or unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bfa54-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bfa54-109">Remarks</span></span>  
 <span data-ttu-id="bfa54-110">[MODULE_LOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) i [MODULE_UNLOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) typów zdarzeń implementuje ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="bfa54-110">The [MODULE_LOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) and [MODULE_UNLOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) event types implement this interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bfa54-111">Interfejs jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="bfa54-111">The interface is available with .NET Native only.</span></span> <span data-ttu-id="bfa54-112">Próba wywołania `QueryInterface` można pobrać wskaźnika interfejsu zwraca `E_NOINTERFACE` dla scenariuszy ICorDebug poza platformy .NET Native.</span><span class="sxs-lookup"><span data-stu-id="bfa54-112">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bfa54-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bfa54-113">Requirements</span></span>  
 <span data-ttu-id="bfa54-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bfa54-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bfa54-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bfa54-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bfa54-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bfa54-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bfa54-117">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bfa54-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfa54-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bfa54-118">See Also</span></span>  
 [<span data-ttu-id="bfa54-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="bfa54-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="bfa54-120">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="bfa54-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

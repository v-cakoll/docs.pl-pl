---
title: ICorDebugModuleDebugEvent, interfejs
ms.date: 03/30/2017
ms.assetid: 41950c52-1ac8-4212-b814-c77e20879f91
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7bf1fa21872c710ebc69c45e9980aeaa577a45fc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59160917"
---
# <a name="icordebugmoduledebugevent-interface"></a><span data-ttu-id="f0d5f-102">ICorDebugModuleDebugEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="f0d5f-102">ICorDebugModuleDebugEvent Interface</span></span>
<span data-ttu-id="f0d5f-103">Rozszerza [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interfejsu do obsługi zdarzeń na poziomie modułu.</span><span class="sxs-lookup"><span data-stu-id="f0d5f-103">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support module-level events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="f0d5f-104">Metody</span><span class="sxs-lookup"><span data-stu-id="f0d5f-104">Methods</span></span>  
  
|<span data-ttu-id="f0d5f-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="f0d5f-105">Method</span></span>|<span data-ttu-id="f0d5f-106">Opis</span><span class="sxs-lookup"><span data-stu-id="f0d5f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="f0d5f-107">GetModule, metoda</span><span class="sxs-lookup"><span data-stu-id="f0d5f-107">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-getmodule-method.md)|<span data-ttu-id="f0d5f-108">Pobiera scalonych moduł, który został właśnie załadowany lub usunięty z pamięci.</span><span class="sxs-lookup"><span data-stu-id="f0d5f-108">Gets the merged module that was just loaded or unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f0d5f-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f0d5f-109">Remarks</span></span>  
 <span data-ttu-id="f0d5f-110">[MODULE_LOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) i [MODULE_UNLOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) typy zdarzeń implementować ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="f0d5f-110">The [MODULE_LOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) and [MODULE_UNLOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) event types implement this interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f0d5f-111">Interfejs jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f0d5f-111">The interface is available with .NET Native only.</span></span> <span data-ttu-id="f0d5f-112">Próba wywołania `QueryInterface` do pobrania wskaźnika interfejsu zwraca `E_NOINTERFACE` scenariuszach ICorDebug poza .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f0d5f-112">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0d5f-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f0d5f-113">Requirements</span></span>  
 <span data-ttu-id="f0d5f-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0d5f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0d5f-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f0d5f-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f0d5f-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f0d5f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f0d5f-117">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0d5f-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0d5f-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f0d5f-118">See also</span></span>

- [<span data-ttu-id="f0d5f-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="f0d5f-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="f0d5f-120">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="f0d5f-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

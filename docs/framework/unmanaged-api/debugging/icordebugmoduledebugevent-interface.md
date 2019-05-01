---
title: ICorDebugModuleDebugEvent, interfejs
ms.date: 03/30/2017
ms.assetid: 41950c52-1ac8-4212-b814-c77e20879f91
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7bf1fa21872c710ebc69c45e9980aeaa577a45fc
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61942470"
---
# <a name="icordebugmoduledebugevent-interface"></a><span data-ttu-id="5e9cc-102">ICorDebugModuleDebugEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="5e9cc-102">ICorDebugModuleDebugEvent Interface</span></span>
<span data-ttu-id="5e9cc-103">Rozszerza [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interfejsu do obsługi zdarzeń na poziomie modułu.</span><span class="sxs-lookup"><span data-stu-id="5e9cc-103">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support module-level events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5e9cc-104">Metody</span><span class="sxs-lookup"><span data-stu-id="5e9cc-104">Methods</span></span>  
  
|<span data-ttu-id="5e9cc-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="5e9cc-105">Method</span></span>|<span data-ttu-id="5e9cc-106">Opis</span><span class="sxs-lookup"><span data-stu-id="5e9cc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5e9cc-107">GetModule, metoda</span><span class="sxs-lookup"><span data-stu-id="5e9cc-107">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-getmodule-method.md)|<span data-ttu-id="5e9cc-108">Pobiera scalonych moduł, który został właśnie załadowany lub usunięty z pamięci.</span><span class="sxs-lookup"><span data-stu-id="5e9cc-108">Gets the merged module that was just loaded or unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5e9cc-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5e9cc-109">Remarks</span></span>  
 <span data-ttu-id="5e9cc-110">[MODULE_LOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) i [MODULE_UNLOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) typy zdarzeń implementować ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="5e9cc-110">The [MODULE_LOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) and [MODULE_UNLOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) event types implement this interface.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5e9cc-111">Interfejs jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="5e9cc-111">The interface is available with .NET Native only.</span></span> <span data-ttu-id="5e9cc-112">Próba wywołania `QueryInterface` do pobrania wskaźnika interfejsu zwraca `E_NOINTERFACE` scenariuszach ICorDebug poza .NET Native.</span><span class="sxs-lookup"><span data-stu-id="5e9cc-112">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5e9cc-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5e9cc-113">Requirements</span></span>  
 <span data-ttu-id="5e9cc-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e9cc-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e9cc-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="5e9cc-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5e9cc-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5e9cc-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5e9cc-117">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e9cc-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e9cc-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5e9cc-118">See also</span></span>

- [<span data-ttu-id="5e9cc-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="5e9cc-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="5e9cc-120">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="5e9cc-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

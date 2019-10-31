---
title: ICorDebugModuleDebugEvent, interfejs
ms.date: 03/30/2017
ms.assetid: 41950c52-1ac8-4212-b814-c77e20879f91
ms.openlocfilehash: cca181c6af6db9f35ff7913e045a30e37e07a5e6
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73110248"
---
# <a name="icordebugmoduledebugevent-interface"></a><span data-ttu-id="4d69e-102">ICorDebugModuleDebugEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="4d69e-102">ICorDebugModuleDebugEvent Interface</span></span>
<span data-ttu-id="4d69e-103">Rozszerza interfejs [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) w celu obsługi zdarzeń na poziomie modułu.</span><span class="sxs-lookup"><span data-stu-id="4d69e-103">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support module-level events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4d69e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="4d69e-104">Methods</span></span>  
  
|<span data-ttu-id="4d69e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="4d69e-105">Method</span></span>|<span data-ttu-id="4d69e-106">Opis</span><span class="sxs-lookup"><span data-stu-id="4d69e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4d69e-107">GetModule, metoda</span><span class="sxs-lookup"><span data-stu-id="4d69e-107">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-getmodule-method.md)|<span data-ttu-id="4d69e-108">Pobiera scalony moduł, który został właśnie załadowany lub zwolniony.</span><span class="sxs-lookup"><span data-stu-id="4d69e-108">Gets the merged module that was just loaded or unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4d69e-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4d69e-109">Remarks</span></span>  
 <span data-ttu-id="4d69e-110">Typy zdarzeń [MODULE_LOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) i [MODULE_UNLOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) implementują ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="4d69e-110">The [MODULE_LOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) and [MODULE_UNLOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) event types implement this interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4d69e-111">Interfejs jest dostępny tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="4d69e-111">The interface is available with .NET Native only.</span></span> <span data-ttu-id="4d69e-112">Podjęto próbę wywołania `QueryInterface`, aby pobrać wskaźnik interfejsu zwraca `E_NOINTERFACE` dla scenariuszy ICorDebug poza .NET Native.</span><span class="sxs-lookup"><span data-stu-id="4d69e-112">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d69e-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4d69e-113">Requirements</span></span>  
 <span data-ttu-id="4d69e-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d69e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d69e-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4d69e-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4d69e-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4d69e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4d69e-117">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d69e-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d69e-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4d69e-118">See also</span></span>

- [<span data-ttu-id="4d69e-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="4d69e-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="4d69e-120">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="4d69e-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

---
title: ICorDebugModuleDebugEvent, interfejs
ms.date: 03/30/2017
ms.assetid: 41950c52-1ac8-4212-b814-c77e20879f91
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 706f392652c5cb868e09d4ee9fcb69c6d3d92d2a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965097"
---
# <a name="icordebugmoduledebugevent-interface"></a><span data-ttu-id="04d86-102">ICorDebugModuleDebugEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="04d86-102">ICorDebugModuleDebugEvent Interface</span></span>
<span data-ttu-id="04d86-103">Rozszerza interfejs [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) w celu obsługi zdarzeń na poziomie modułu.</span><span class="sxs-lookup"><span data-stu-id="04d86-103">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support module-level events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="04d86-104">Metody</span><span class="sxs-lookup"><span data-stu-id="04d86-104">Methods</span></span>  
  
|<span data-ttu-id="04d86-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="04d86-105">Method</span></span>|<span data-ttu-id="04d86-106">Opis</span><span class="sxs-lookup"><span data-stu-id="04d86-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="04d86-107">GetModule, metoda</span><span class="sxs-lookup"><span data-stu-id="04d86-107">GetModule Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-getmodule-method.md)|<span data-ttu-id="04d86-108">Pobiera scalony moduł, który został właśnie załadowany lub zwolniony.</span><span class="sxs-lookup"><span data-stu-id="04d86-108">Gets the merged module that was just loaded or unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="04d86-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="04d86-109">Remarks</span></span>  
 <span data-ttu-id="04d86-110">Typy zdarzeń [MODULE_LOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) i [MODULE_UNLOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) implementują ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="04d86-110">The [MODULE_LOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) and [MODULE_UNLOADED](../../../../docs/framework/unmanaged-api/debugging/cordebugdebugeventkind-enumeration.md) event types implement this interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="04d86-111">Interfejs jest dostępny tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="04d86-111">The interface is available with .NET Native only.</span></span> <span data-ttu-id="04d86-112">Próba wywołania metody `QueryInterface` pobierającej wskaźnik interfejsu zwraca `E_NOINTERFACE` dla scenariuszy ICorDebug poza .NET Native.</span><span class="sxs-lookup"><span data-stu-id="04d86-112">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="04d86-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="04d86-113">Requirements</span></span>  
 <span data-ttu-id="04d86-114">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04d86-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04d86-115">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="04d86-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="04d86-116">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="04d86-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="04d86-117">**.NET Framework wersje:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04d86-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04d86-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="04d86-118">See also</span></span>

- [<span data-ttu-id="04d86-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="04d86-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="04d86-120">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="04d86-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

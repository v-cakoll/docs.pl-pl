---
title: ICorDebugModuleDebugEvent, interfejs
ms.date: 03/30/2017
ms.assetid: 41950c52-1ac8-4212-b814-c77e20879f91
ms.openlocfilehash: a2c7eaa8a2c811c1696024d9af4b715cc49e7caa
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792894"
---
# <a name="icordebugmoduledebugevent-interface"></a><span data-ttu-id="1701a-102">ICorDebugModuleDebugEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="1701a-102">ICorDebugModuleDebugEvent Interface</span></span>
<span data-ttu-id="1701a-103">Rozszerza interfejs [ICorDebugDebugEvent](icordebugdebugevent-interface.md) w celu obsługi zdarzeń na poziomie modułu.</span><span class="sxs-lookup"><span data-stu-id="1701a-103">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support module-level events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1701a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="1701a-104">Methods</span></span>  
  
|<span data-ttu-id="1701a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="1701a-105">Method</span></span>|<span data-ttu-id="1701a-106">Opis</span><span class="sxs-lookup"><span data-stu-id="1701a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="1701a-107">GetModule, metoda</span><span class="sxs-lookup"><span data-stu-id="1701a-107">GetModule Method</span></span>](icordebugmoduledebugevent-getmodule-method.md)|<span data-ttu-id="1701a-108">Pobiera scalony moduł, który został właśnie załadowany lub zwolniony.</span><span class="sxs-lookup"><span data-stu-id="1701a-108">Gets the merged module that was just loaded or unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1701a-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1701a-109">Remarks</span></span>  
 <span data-ttu-id="1701a-110">Typy zdarzeń [MODULE_LOADED](cordebugdebugeventkind-enumeration.md) i [MODULE_UNLOADED](cordebugdebugeventkind-enumeration.md) implementują ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="1701a-110">The [MODULE_LOADED](cordebugdebugeventkind-enumeration.md) and [MODULE_UNLOADED](cordebugdebugeventkind-enumeration.md) event types implement this interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1701a-111">Interfejs jest dostępny tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="1701a-111">The interface is available with .NET Native only.</span></span> <span data-ttu-id="1701a-112">Podjęto próbę wywołania `QueryInterface`, aby pobrać wskaźnik interfejsu zwraca `E_NOINTERFACE` dla scenariuszy ICorDebug poza .NET Native.</span><span class="sxs-lookup"><span data-stu-id="1701a-112">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1701a-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1701a-113">Requirements</span></span>  
 <span data-ttu-id="1701a-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1701a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1701a-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1701a-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1701a-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1701a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1701a-117">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1701a-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1701a-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1701a-118">See also</span></span>

- [<span data-ttu-id="1701a-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="1701a-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="1701a-120">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="1701a-120">Debugging</span></span>](index.md)

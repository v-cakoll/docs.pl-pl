---
title: ICorDebugModuleDebugEvent, interfejs
ms.date: 03/30/2017
ms.assetid: 41950c52-1ac8-4212-b814-c77e20879f91
ms.openlocfilehash: ec6bad730d807b9a36ce5bba1c6f5d80da375f6d
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213336"
---
# <a name="icordebugmoduledebugevent-interface"></a><span data-ttu-id="5f90e-102">ICorDebugModuleDebugEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="5f90e-102">ICorDebugModuleDebugEvent Interface</span></span>
<span data-ttu-id="5f90e-103">Rozszerza interfejs [ICorDebugDebugEvent](icordebugdebugevent-interface.md) w celu obsługi zdarzeń na poziomie modułu.</span><span class="sxs-lookup"><span data-stu-id="5f90e-103">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support module-level events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="5f90e-104">Metody</span><span class="sxs-lookup"><span data-stu-id="5f90e-104">Methods</span></span>  
  
|<span data-ttu-id="5f90e-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="5f90e-105">Method</span></span>|<span data-ttu-id="5f90e-106">Opis</span><span class="sxs-lookup"><span data-stu-id="5f90e-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="5f90e-107">GetModule — Metoda</span><span class="sxs-lookup"><span data-stu-id="5f90e-107">GetModule Method</span></span>](icordebugmoduledebugevent-getmodule-method.md)|<span data-ttu-id="5f90e-108">Pobiera scalony moduł, który został właśnie załadowany lub zwolniony.</span><span class="sxs-lookup"><span data-stu-id="5f90e-108">Gets the merged module that was just loaded or unloaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5f90e-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5f90e-109">Remarks</span></span>  
 <span data-ttu-id="5f90e-110">Typy zdarzeń [MODULE_LOADED](cordebugdebugeventkind-enumeration.md) i [MODULE_UNLOADED](cordebugdebugeventkind-enumeration.md) implementują ten interfejs.</span><span class="sxs-lookup"><span data-stu-id="5f90e-110">The [MODULE_LOADED](cordebugdebugeventkind-enumeration.md) and [MODULE_UNLOADED](cordebugdebugeventkind-enumeration.md) event types implement this interface.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5f90e-111">Interfejs jest dostępny tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="5f90e-111">The interface is available with .NET Native only.</span></span> <span data-ttu-id="5f90e-112">Próba wywołania metody `QueryInterface` pobierającej wskaźnik interfejsu zwraca `E_NOINTERFACE` dla scenariuszy ICorDebug poza .NET Native.</span><span class="sxs-lookup"><span data-stu-id="5f90e-112">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5f90e-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5f90e-113">Requirements</span></span>  
 <span data-ttu-id="5f90e-114">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5f90e-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5f90e-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5f90e-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5f90e-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5f90e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5f90e-117">**.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5f90e-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f90e-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5f90e-118">See also</span></span>

- [<span data-ttu-id="5f90e-119">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="5f90e-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="5f90e-120">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="5f90e-120">Debugging</span></span>](index.md)

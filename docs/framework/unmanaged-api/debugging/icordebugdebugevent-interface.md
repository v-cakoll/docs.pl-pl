---
title: Interfejs ICorDebugDebugEvent
ms.date: 03/30/2017
ms.assetid: a226737a-cb99-4e97-bd94-9a37094ded41
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8f838c9c2775023583b6879ea4c4a52727065114
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911264"
---
# <a name="icordebugdebugevent-interface"></a><span data-ttu-id="27a69-102">Interfejs ICorDebugDebugEvent</span><span class="sxs-lookup"><span data-stu-id="27a69-102">ICorDebugDebugEvent Interface</span></span>
<span data-ttu-id="27a69-103">Definiuje interfejs podstawowy, z którego pochodzą `ICorDebug` wszystkie zdarzenia debugowania.</span><span class="sxs-lookup"><span data-stu-id="27a69-103">Defines the base interface from which all `ICorDebug` debug events derive.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="27a69-104">Metody</span><span class="sxs-lookup"><span data-stu-id="27a69-104">Methods</span></span>  
  
|<span data-ttu-id="27a69-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="27a69-105">Method</span></span>|<span data-ttu-id="27a69-106">Opis</span><span class="sxs-lookup"><span data-stu-id="27a69-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="27a69-107">GetEventKind, metoda</span><span class="sxs-lookup"><span data-stu-id="27a69-107">GetEventKind Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md)|<span data-ttu-id="27a69-108">Wskazuje, jaki rodzaj zdarzenia reprezentuje `ICorDebugDebugEvent` ten obiekt.</span><span class="sxs-lookup"><span data-stu-id="27a69-108">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>|  
|[<span data-ttu-id="27a69-109">GetThread, metoda</span><span class="sxs-lookup"><span data-stu-id="27a69-109">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-getthread-method.md)|<span data-ttu-id="27a69-110">Pobiera wątek, w którym wystąpiło zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="27a69-110">Gets the thread on which the event occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="27a69-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="27a69-111">Remarks</span></span>  
 <span data-ttu-id="27a69-112">Następujące interfejsy pochodzą od `ICorDebugDebugEvent` interfejsu:</span><span class="sxs-lookup"><span data-stu-id="27a69-112">The following interfaces are derived from the `ICorDebugDebugEvent` interface:</span></span>  
  
- [<span data-ttu-id="27a69-113">ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="27a69-113">ICorDebugExceptionDebugEvent</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
  
- [<span data-ttu-id="27a69-114">ICorDebugModuleDebugEvent</span><span class="sxs-lookup"><span data-stu-id="27a69-114">ICorDebugModuleDebugEvent</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
  
> [!NOTE]
> <span data-ttu-id="27a69-115">Interfejs jest dostępny tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="27a69-115">The interface is available with .NET Native only.</span></span> <span data-ttu-id="27a69-116">Próba wywołania metody `QueryInterface` pobierającej wskaźnik interfejsu zwraca `E_NOINTERFACE` dla scenariuszy ICorDebug poza .NET Native.</span><span class="sxs-lookup"><span data-stu-id="27a69-116">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27a69-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="27a69-117">Requirements</span></span>  
 <span data-ttu-id="27a69-118">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27a69-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27a69-119">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="27a69-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="27a69-120">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="27a69-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="27a69-121">**.NET Framework wersje:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27a69-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27a69-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="27a69-122">See also</span></span>

- [<span data-ttu-id="27a69-123">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="27a69-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="27a69-124">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="27a69-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

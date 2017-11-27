---
title: Interfejs ICorDebugDebugEvent
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: a226737a-cb99-4e97-bd94-9a37094ded41
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b4422b165f06b60dedff95fc3de58e5627db7fac
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdebugevent-interface"></a><span data-ttu-id="4712c-102">Interfejs ICorDebugDebugEvent</span><span class="sxs-lookup"><span data-stu-id="4712c-102">ICorDebugDebugEvent Interface</span></span>
<span data-ttu-id="4712c-103">Definiuje interfejs podstawowy, z którym wszystkie `ICorDebug` pochodzi zdarzeń debugowania.</span><span class="sxs-lookup"><span data-stu-id="4712c-103">Defines the base interface from which all `ICorDebug` debug events derive.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="4712c-104">Metody</span><span class="sxs-lookup"><span data-stu-id="4712c-104">Methods</span></span>  
  
|<span data-ttu-id="4712c-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="4712c-105">Method</span></span>|<span data-ttu-id="4712c-106">Opis</span><span class="sxs-lookup"><span data-stu-id="4712c-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="4712c-107">— Metoda GetEventKind</span><span class="sxs-lookup"><span data-stu-id="4712c-107">GetEventKind Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md)|<span data-ttu-id="4712c-108">To wskazuje jakiego rodzaju zdarzenia `ICorDebugDebugEvent` reprezentuje obiekt.</span><span class="sxs-lookup"><span data-stu-id="4712c-108">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>|  
|[<span data-ttu-id="4712c-109">GetThread — metoda</span><span class="sxs-lookup"><span data-stu-id="4712c-109">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-getthread-method.md)|<span data-ttu-id="4712c-110">Pobiera wątku, w którym wystąpiło zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="4712c-110">Gets the thread on which the event occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4712c-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4712c-111">Remarks</span></span>  
 <span data-ttu-id="4712c-112">Następujące interfejsy są uzyskiwane z `ICorDebugDebugEvent` interfejsu:</span><span class="sxs-lookup"><span data-stu-id="4712c-112">The following interfaces are derived from the `ICorDebugDebugEvent` interface:</span></span>  
  
-   [<span data-ttu-id="4712c-113">ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="4712c-113">ICorDebugExceptionDebugEvent</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
  
-   [<span data-ttu-id="4712c-114">ICorDebugModuleDebugEvent</span><span class="sxs-lookup"><span data-stu-id="4712c-114">ICorDebugModuleDebugEvent</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
  
> [!NOTE]
>  <span data-ttu-id="4712c-115">Interfejs jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="4712c-115">The interface is available with .NET Native only.</span></span> <span data-ttu-id="4712c-116">Próba wywołania `QueryInterface` można pobrać wskaźnika interfejsu zwraca `E_NOINTERFACE` dla scenariuszy ICorDebug poza platformy .NET Native.</span><span class="sxs-lookup"><span data-stu-id="4712c-116">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4712c-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4712c-117">Requirements</span></span>  
 <span data-ttu-id="4712c-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4712c-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4712c-119">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4712c-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4712c-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4712c-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4712c-121">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4712c-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4712c-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4712c-122">See Also</span></span>  
 [<span data-ttu-id="4712c-123">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="4712c-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="4712c-124">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="4712c-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

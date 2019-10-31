---
title: Interfejs ICorDebugDebugEvent
ms.date: 03/30/2017
ms.assetid: a226737a-cb99-4e97-bd94-9a37094ded41
ms.openlocfilehash: ea42faa4001fa880354690df1551de3be767e683
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137036"
---
# <a name="icordebugdebugevent-interface"></a><span data-ttu-id="57a0a-102">Interfejs ICorDebugDebugEvent</span><span class="sxs-lookup"><span data-stu-id="57a0a-102">ICorDebugDebugEvent Interface</span></span>
<span data-ttu-id="57a0a-103">Definiuje interfejs podstawowy, z którego pochodzą wszystkie zdarzenia debugowania `ICorDebug`.</span><span class="sxs-lookup"><span data-stu-id="57a0a-103">Defines the base interface from which all `ICorDebug` debug events derive.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="57a0a-104">Metody</span><span class="sxs-lookup"><span data-stu-id="57a0a-104">Methods</span></span>  
  
|<span data-ttu-id="57a0a-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="57a0a-105">Method</span></span>|<span data-ttu-id="57a0a-106">Opis</span><span class="sxs-lookup"><span data-stu-id="57a0a-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="57a0a-107">GetEventKind, metoda</span><span class="sxs-lookup"><span data-stu-id="57a0a-107">GetEventKind Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md)|<span data-ttu-id="57a0a-108">Wskazuje, jaki rodzaj zdarzenia reprezentuje ten obiekt `ICorDebugDebugEvent`.</span><span class="sxs-lookup"><span data-stu-id="57a0a-108">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>|  
|[<span data-ttu-id="57a0a-109">GetThread, metoda</span><span class="sxs-lookup"><span data-stu-id="57a0a-109">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-getthread-method.md)|<span data-ttu-id="57a0a-110">Pobiera wątek, w którym wystąpiło zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="57a0a-110">Gets the thread on which the event occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57a0a-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="57a0a-111">Remarks</span></span>  
 <span data-ttu-id="57a0a-112">Następujące interfejsy pochodzą z interfejsu `ICorDebugDebugEvent`:</span><span class="sxs-lookup"><span data-stu-id="57a0a-112">The following interfaces are derived from the `ICorDebugDebugEvent` interface:</span></span>  
  
- [<span data-ttu-id="57a0a-113">ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="57a0a-113">ICorDebugExceptionDebugEvent</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
  
- [<span data-ttu-id="57a0a-114">ICorDebugModuleDebugEvent</span><span class="sxs-lookup"><span data-stu-id="57a0a-114">ICorDebugModuleDebugEvent</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
  
> [!NOTE]
> <span data-ttu-id="57a0a-115">Interfejs jest dostępny tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="57a0a-115">The interface is available with .NET Native only.</span></span> <span data-ttu-id="57a0a-116">Podjęto próbę wywołania `QueryInterface`, aby pobrać wskaźnik interfejsu zwraca `E_NOINTERFACE` dla scenariuszy ICorDebug poza .NET Native.</span><span class="sxs-lookup"><span data-stu-id="57a0a-116">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57a0a-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="57a0a-117">Requirements</span></span>  
 <span data-ttu-id="57a0a-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="57a0a-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="57a0a-119">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="57a0a-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="57a0a-120">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="57a0a-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="57a0a-121">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57a0a-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57a0a-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="57a0a-122">See also</span></span>

- [<span data-ttu-id="57a0a-123">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="57a0a-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="57a0a-124">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="57a0a-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

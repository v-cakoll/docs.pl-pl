---
title: Interfejs ICorDebugDebugEvent
ms.date: 03/30/2017
ms.assetid: a226737a-cb99-4e97-bd94-9a37094ded41
ms.openlocfilehash: bef057bdb3ff0919337dd15f2d930159ddaf1bcf
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783395"
---
# <a name="icordebugdebugevent-interface"></a><span data-ttu-id="921fe-102">Interfejs ICorDebugDebugEvent</span><span class="sxs-lookup"><span data-stu-id="921fe-102">ICorDebugDebugEvent Interface</span></span>
<span data-ttu-id="921fe-103">Definiuje interfejs podstawowy, z którego pochodzą wszystkie zdarzenia debugowania `ICorDebug`.</span><span class="sxs-lookup"><span data-stu-id="921fe-103">Defines the base interface from which all `ICorDebug` debug events derive.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="921fe-104">Metody</span><span class="sxs-lookup"><span data-stu-id="921fe-104">Methods</span></span>  
  
|<span data-ttu-id="921fe-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="921fe-105">Method</span></span>|<span data-ttu-id="921fe-106">Opis</span><span class="sxs-lookup"><span data-stu-id="921fe-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="921fe-107">GetEventKind, metoda</span><span class="sxs-lookup"><span data-stu-id="921fe-107">GetEventKind Method</span></span>](icordebugdebugevent-geteventkind-method.md)|<span data-ttu-id="921fe-108">Wskazuje, jaki rodzaj zdarzenia reprezentuje ten obiekt `ICorDebugDebugEvent`.</span><span class="sxs-lookup"><span data-stu-id="921fe-108">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>|  
|[<span data-ttu-id="921fe-109">GetThread, metoda</span><span class="sxs-lookup"><span data-stu-id="921fe-109">GetThread Method</span></span>](icordebugdebugevent-getthread-method.md)|<span data-ttu-id="921fe-110">Pobiera wątek, w którym wystąpiło zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="921fe-110">Gets the thread on which the event occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="921fe-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="921fe-111">Remarks</span></span>  
 <span data-ttu-id="921fe-112">Następujące interfejsy pochodzą z interfejsu `ICorDebugDebugEvent`:</span><span class="sxs-lookup"><span data-stu-id="921fe-112">The following interfaces are derived from the `ICorDebugDebugEvent` interface:</span></span>  
  
- [<span data-ttu-id="921fe-113">ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="921fe-113">ICorDebugExceptionDebugEvent</span></span>](icordebugexceptiondebugevent-interface.md)  
  
- [<span data-ttu-id="921fe-114">ICorDebugModuleDebugEvent</span><span class="sxs-lookup"><span data-stu-id="921fe-114">ICorDebugModuleDebugEvent</span></span>](icordebugmoduledebugevent-interface.md)  
  
> [!NOTE]
> <span data-ttu-id="921fe-115">Interfejs jest dostępny tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="921fe-115">The interface is available with .NET Native only.</span></span> <span data-ttu-id="921fe-116">Podjęto próbę wywołania `QueryInterface`, aby pobrać wskaźnik interfejsu zwraca `E_NOINTERFACE` dla scenariuszy ICorDebug poza .NET Native.</span><span class="sxs-lookup"><span data-stu-id="921fe-116">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="921fe-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="921fe-117">Requirements</span></span>  
 <span data-ttu-id="921fe-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="921fe-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="921fe-119">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="921fe-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="921fe-120">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="921fe-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="921fe-121">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="921fe-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="921fe-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="921fe-122">See also</span></span>

- [<span data-ttu-id="921fe-123">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="921fe-123">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="921fe-124">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="921fe-124">Debugging</span></span>](index.md)

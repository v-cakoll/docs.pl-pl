---
title: Interfejs ICorDebugDebugEvent
ms.date: 03/30/2017
ms.assetid: a226737a-cb99-4e97-bd94-9a37094ded41
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 013cdfbb6a2904e60d6f7b4df6d40e3d65606fcd
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64606818"
---
# <a name="icordebugdebugevent-interface"></a><span data-ttu-id="bd0cb-102">Interfejs ICorDebugDebugEvent</span><span class="sxs-lookup"><span data-stu-id="bd0cb-102">ICorDebugDebugEvent Interface</span></span>
<span data-ttu-id="bd0cb-103">Definiuje interfejs podstawowy, z którym wszystkie `ICorDebug` pochodzić zdarzeń debugowania.</span><span class="sxs-lookup"><span data-stu-id="bd0cb-103">Defines the base interface from which all `ICorDebug` debug events derive.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bd0cb-104">Metody</span><span class="sxs-lookup"><span data-stu-id="bd0cb-104">Methods</span></span>  
  
|<span data-ttu-id="bd0cb-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="bd0cb-105">Method</span></span>|<span data-ttu-id="bd0cb-106">Opis</span><span class="sxs-lookup"><span data-stu-id="bd0cb-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bd0cb-107">GetEventKind, metoda</span><span class="sxs-lookup"><span data-stu-id="bd0cb-107">GetEventKind Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md)|<span data-ttu-id="bd0cb-108">Wskazuje rodzaj zdarzeń, to `ICorDebugDebugEvent` obiekt reprezentuje.</span><span class="sxs-lookup"><span data-stu-id="bd0cb-108">Indicates what kind of event this `ICorDebugDebugEvent` object represents.</span></span>|  
|[<span data-ttu-id="bd0cb-109">GetThread, metoda</span><span class="sxs-lookup"><span data-stu-id="bd0cb-109">GetThread Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-getthread-method.md)|<span data-ttu-id="bd0cb-110">Pobiera wątku, w którym wystąpiło zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="bd0cb-110">Gets the thread on which the event occurred.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd0cb-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bd0cb-111">Remarks</span></span>  
 <span data-ttu-id="bd0cb-112">Następujące interfejsy są pochodną `ICorDebugDebugEvent` interfejsu:</span><span class="sxs-lookup"><span data-stu-id="bd0cb-112">The following interfaces are derived from the `ICorDebugDebugEvent` interface:</span></span>  
  
- [<span data-ttu-id="bd0cb-113">ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="bd0cb-113">ICorDebugExceptionDebugEvent</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
  
- [<span data-ttu-id="bd0cb-114">ICorDebugModuleDebugEvent</span><span class="sxs-lookup"><span data-stu-id="bd0cb-114">ICorDebugModuleDebugEvent</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmoduledebugevent-interface.md)  
  
> [!NOTE]
>  <span data-ttu-id="bd0cb-115">Interfejs jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="bd0cb-115">The interface is available with .NET Native only.</span></span> <span data-ttu-id="bd0cb-116">Próba wywołania `QueryInterface` do pobrania wskaźnika interfejsu zwraca `E_NOINTERFACE` scenariuszach ICorDebug poza .NET Native.</span><span class="sxs-lookup"><span data-stu-id="bd0cb-116">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bd0cb-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bd0cb-117">Requirements</span></span>  
 <span data-ttu-id="bd0cb-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bd0cb-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bd0cb-119">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bd0cb-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bd0cb-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bd0cb-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bd0cb-121">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bd0cb-121">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bd0cb-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bd0cb-122">See also</span></span>

- [<span data-ttu-id="bd0cb-123">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="bd0cb-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="bd0cb-124">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="bd0cb-124">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

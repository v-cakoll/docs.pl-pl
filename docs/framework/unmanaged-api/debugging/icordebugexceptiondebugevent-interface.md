---
title: Interfejs ICorDebugExceptionDebugEvent
ms.date: 03/30/2017
ms.assetid: f9ba60d8-b54d-417e-bb3e-fde4b41ca44c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2e2a147d46412eb4feb192070ff8420cab842a6c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59156458"
---
# <a name="icordebugexceptiondebugevent-interface"></a><span data-ttu-id="7ac95-102">Interfejs ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="7ac95-102">ICorDebugExceptionDebugEvent Interface</span></span>
<span data-ttu-id="7ac95-103">Rozszerza [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interfejsu do obsługi zdarzeń dotyczących wyjątków.</span><span class="sxs-lookup"><span data-stu-id="7ac95-103">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support exception events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7ac95-104">Metody</span><span class="sxs-lookup"><span data-stu-id="7ac95-104">Methods</span></span>  
  
|<span data-ttu-id="7ac95-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="7ac95-105">Method</span></span>|<span data-ttu-id="7ac95-106">Opis</span><span class="sxs-lookup"><span data-stu-id="7ac95-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="7ac95-107">GetFlags, metoda</span><span class="sxs-lookup"><span data-stu-id="7ac95-107">GetFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getflags-method.md)|<span data-ttu-id="7ac95-108">Pobiera a flagę, która wskazuje, czy wyjątek może zostać przechwycona.</span><span class="sxs-lookup"><span data-stu-id="7ac95-108">Gets a flag that indicates whether the exception is can be intercepted.</span></span>|  
|[<span data-ttu-id="7ac95-109">GetNativeIP, metoda</span><span class="sxs-lookup"><span data-stu-id="7ac95-109">GetNativeIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getnativeip-method.md)|<span data-ttu-id="7ac95-110">Pobiera wskaźnik natywny interfejs dla tego zdarzenia debugowania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="7ac95-110">Gets the native interface pointer for this exception debug event.</span></span>|  
|[<span data-ttu-id="7ac95-111">GetStackPointer, metoda</span><span class="sxs-lookup"><span data-stu-id="7ac95-111">GetStackPointer Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md)|<span data-ttu-id="7ac95-112">Pobiera wskaźnik stosu dla tego zdarzenia debugowania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="7ac95-112">Gets the stack pointer for this exception debug event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ac95-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7ac95-113">Remarks</span></span>  
 <span data-ttu-id="7ac95-114">`ICorDebugExceptionDebugEvent` Interfejs jest implementowany przez następujące typy zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="7ac95-114">The `ICorDebugExceptionDebugEvent` interface is implemented by the following event types:</span></span>  
  
-   [<span data-ttu-id="7ac95-115">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="7ac95-115">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
-   [<span data-ttu-id="7ac95-116">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="7ac95-116">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
-   [<span data-ttu-id="7ac95-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="7ac95-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
-   [<span data-ttu-id="7ac95-118">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="7ac95-118">MANAGED_EXCEPTION_UNHANDLED</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
> [!NOTE]
>  <span data-ttu-id="7ac95-119">Interfejs jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="7ac95-119">The interface is available with .NET Native only.</span></span> <span data-ttu-id="7ac95-120">Próba wywołania `QueryInterface` do pobrania wskaźnika interfejsu zwraca `E_NOINTERFACE` scenariuszach ICorDebug poza .NET Native.</span><span class="sxs-lookup"><span data-stu-id="7ac95-120">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7ac95-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7ac95-121">Requirements</span></span>  
 <span data-ttu-id="7ac95-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7ac95-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7ac95-123">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7ac95-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7ac95-124">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7ac95-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7ac95-125">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7ac95-125">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ac95-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7ac95-126">See also</span></span>

- [<span data-ttu-id="7ac95-127">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="7ac95-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="7ac95-128">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="7ac95-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

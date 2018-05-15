---
title: Interfejs ICorDebugExceptionDebugEvent
ms.date: 03/30/2017
ms.assetid: f9ba60d8-b54d-417e-bb3e-fde4b41ca44c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cedbbf2067a94aa73e40bd4651fc97b72aa9afef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugexceptiondebugevent-interface"></a><span data-ttu-id="b3c15-102">Interfejs ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="b3c15-102">ICorDebugExceptionDebugEvent Interface</span></span>
<span data-ttu-id="b3c15-103">Rozszerza [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interfejs do obsługi zdarzeń wyjątków.</span><span class="sxs-lookup"><span data-stu-id="b3c15-103">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support exception events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b3c15-104">Metody</span><span class="sxs-lookup"><span data-stu-id="b3c15-104">Methods</span></span>  
  
|<span data-ttu-id="b3c15-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="b3c15-105">Method</span></span>|<span data-ttu-id="b3c15-106">Opis</span><span class="sxs-lookup"><span data-stu-id="b3c15-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b3c15-107">GetFlags, metoda</span><span class="sxs-lookup"><span data-stu-id="b3c15-107">GetFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getflags-method.md)|<span data-ttu-id="b3c15-108">Pobiera a flaga, która wskazuje, czy wyjątek może zostać przechwycona.</span><span class="sxs-lookup"><span data-stu-id="b3c15-108">Gets a flag that indicates whether the exception is can be intercepted.</span></span>|  
|[<span data-ttu-id="b3c15-109">GetNativeIP, metoda</span><span class="sxs-lookup"><span data-stu-id="b3c15-109">GetNativeIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getnativeip-method.md)|<span data-ttu-id="b3c15-110">Pobiera wskaźnik interfejs natywny dla tego zdarzenia debugowania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="b3c15-110">Gets the native interface pointer for this exception debug event.</span></span>|  
|[<span data-ttu-id="b3c15-111">GetStackPointer, metoda</span><span class="sxs-lookup"><span data-stu-id="b3c15-111">GetStackPointer Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md)|<span data-ttu-id="b3c15-112">Pobiera wskaźnik stosu dla tego zdarzenia debugowania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="b3c15-112">Gets the stack pointer for this exception debug event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b3c15-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b3c15-113">Remarks</span></span>  
 <span data-ttu-id="b3c15-114">`ICorDebugExceptionDebugEvent` Interfejs jest implementowany przez następujące typy zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="b3c15-114">The `ICorDebugExceptionDebugEvent` interface is implemented by the following event types:</span></span>  
  
-   [<span data-ttu-id="b3c15-115">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="b3c15-115">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
-   [<span data-ttu-id="b3c15-116">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="b3c15-116">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
-   [<span data-ttu-id="b3c15-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="b3c15-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
-   [<span data-ttu-id="b3c15-118">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="b3c15-118">MANAGED_EXCEPTION_UNHANDLED</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
> [!NOTE]
>  <span data-ttu-id="b3c15-119">Interfejs jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="b3c15-119">The interface is available with .NET Native only.</span></span> <span data-ttu-id="b3c15-120">Próba wywołania `QueryInterface` można pobrać wskaźnika interfejsu zwraca `E_NOINTERFACE` dla scenariuszy ICorDebug poza platformy .NET Native.</span><span class="sxs-lookup"><span data-stu-id="b3c15-120">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3c15-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b3c15-121">Requirements</span></span>  
 <span data-ttu-id="b3c15-122">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3c15-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3c15-123">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b3c15-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b3c15-124">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b3c15-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b3c15-125">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3c15-125">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3c15-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b3c15-126">See Also</span></span>  
 [<span data-ttu-id="b3c15-127">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="b3c15-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="b3c15-128">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="b3c15-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

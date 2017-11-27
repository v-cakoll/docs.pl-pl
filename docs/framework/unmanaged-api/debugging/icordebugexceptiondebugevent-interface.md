---
title: Interfejs ICorDebugExceptionDebugEvent
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f9ba60d8-b54d-417e-bb3e-fde4b41ca44c
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: c485338f196e4748805231a8391645fdc182d70d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugexceptiondebugevent-interface"></a><span data-ttu-id="02959-102">Interfejs ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="02959-102">ICorDebugExceptionDebugEvent Interface</span></span>
<span data-ttu-id="02959-103">Rozszerza [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interfejs do obsługi zdarzeń wyjątków.</span><span class="sxs-lookup"><span data-stu-id="02959-103">Extends the [ICorDebugDebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-interface.md) interface to support exception events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="02959-104">Metody</span><span class="sxs-lookup"><span data-stu-id="02959-104">Methods</span></span>  
  
|<span data-ttu-id="02959-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="02959-105">Method</span></span>|<span data-ttu-id="02959-106">Opis</span><span class="sxs-lookup"><span data-stu-id="02959-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="02959-107">GetFlags — metoda</span><span class="sxs-lookup"><span data-stu-id="02959-107">GetFlags Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getflags-method.md)|<span data-ttu-id="02959-108">Pobiera a flaga, która wskazuje, czy wyjątek może zostać przechwycona.</span><span class="sxs-lookup"><span data-stu-id="02959-108">Gets a flag that indicates whether the exception is can be intercepted.</span></span>|  
|[<span data-ttu-id="02959-109">GetNativeIP — metoda</span><span class="sxs-lookup"><span data-stu-id="02959-109">GetNativeIP Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getnativeip-method.md)|<span data-ttu-id="02959-110">Pobiera wskaźnik interfejs natywny dla tego zdarzenia debugowania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="02959-110">Gets the native interface pointer for this exception debug event.</span></span>|  
|[<span data-ttu-id="02959-111">GetStackPointer — metoda</span><span class="sxs-lookup"><span data-stu-id="02959-111">GetStackPointer Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md)|<span data-ttu-id="02959-112">Pobiera wskaźnik stosu dla tego zdarzenia debugowania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="02959-112">Gets the stack pointer for this exception debug event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="02959-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="02959-113">Remarks</span></span>  
 <span data-ttu-id="02959-114">`ICorDebugExceptionDebugEvent` Interfejs jest implementowany przez następujące typy zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="02959-114">The `ICorDebugExceptionDebugEvent` interface is implemented by the following event types:</span></span>  
  
-   [<span data-ttu-id="02959-115">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="02959-115">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
-   [<span data-ttu-id="02959-116">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="02959-116">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
-   [<span data-ttu-id="02959-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="02959-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
-   [<span data-ttu-id="02959-118">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="02959-118">MANAGED_EXCEPTION_UNHANDLED</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)  
  
> [!NOTE]
>  <span data-ttu-id="02959-119">Interfejs jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="02959-119">The interface is available with .NET Native only.</span></span> <span data-ttu-id="02959-120">Próba wywołania `QueryInterface` można pobrać wskaźnika interfejsu zwraca `E_NOINTERFACE` dla scenariuszy ICorDebug poza platformy .NET Native.</span><span class="sxs-lookup"><span data-stu-id="02959-120">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02959-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="02959-121">Requirements</span></span>  
 <span data-ttu-id="02959-122">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02959-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02959-123">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="02959-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="02959-124">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="02959-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="02959-125">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02959-125">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02959-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="02959-126">See Also</span></span>  
 [<span data-ttu-id="02959-127">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="02959-127">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="02959-128">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="02959-128">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

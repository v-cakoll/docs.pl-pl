---
title: Interfejs ICorDebugExceptionDebugEvent
ms.date: 03/30/2017
ms.assetid: f9ba60d8-b54d-417e-bb3e-fde4b41ca44c
ms.openlocfilehash: 168ba2945608a5b26432c5a0f583e5d406f6ce9b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782832"
---
# <a name="icordebugexceptiondebugevent-interface"></a><span data-ttu-id="170be-102">Interfejs ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="170be-102">ICorDebugExceptionDebugEvent Interface</span></span>
<span data-ttu-id="170be-103">Rozszerza interfejs [ICorDebugDebugEvent](icordebugdebugevent-interface.md) w celu obsługi zdarzeń wyjątków.</span><span class="sxs-lookup"><span data-stu-id="170be-103">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support exception events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="170be-104">Metody</span><span class="sxs-lookup"><span data-stu-id="170be-104">Methods</span></span>  
  
|<span data-ttu-id="170be-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="170be-105">Method</span></span>|<span data-ttu-id="170be-106">Opis</span><span class="sxs-lookup"><span data-stu-id="170be-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="170be-107">GetFlags, metoda</span><span class="sxs-lookup"><span data-stu-id="170be-107">GetFlags Method</span></span>](icordebugexceptiondebugevent-getflags-method.md)|<span data-ttu-id="170be-108">Pobiera flagę wskazującą, czy wyjątek może być przechwytywany.</span><span class="sxs-lookup"><span data-stu-id="170be-108">Gets a flag that indicates whether the exception is can be intercepted.</span></span>|  
|[<span data-ttu-id="170be-109">GetNativeIP, metoda</span><span class="sxs-lookup"><span data-stu-id="170be-109">GetNativeIP Method</span></span>](icordebugexceptiondebugevent-getnativeip-method.md)|<span data-ttu-id="170be-110">Pobiera wskaźnik interfejsu macierzystego dla tego zdarzenia debugowania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="170be-110">Gets the native interface pointer for this exception debug event.</span></span>|  
|[<span data-ttu-id="170be-111">GetStackPointer, metoda</span><span class="sxs-lookup"><span data-stu-id="170be-111">GetStackPointer Method</span></span>](icordebugexceptiondebugevent-getstackpointer-method.md)|<span data-ttu-id="170be-112">Pobiera wskaźnik stosu dla tego zdarzenia debugowania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="170be-112">Gets the stack pointer for this exception debug event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="170be-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="170be-113">Remarks</span></span>  
 <span data-ttu-id="170be-114">Interfejs `ICorDebugExceptionDebugEvent` jest implementowany przez następujące typy zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="170be-114">The `ICorDebugExceptionDebugEvent` interface is implemented by the following event types:</span></span>  
  
- [<span data-ttu-id="170be-115">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="170be-115">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="170be-116">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="170be-116">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="170be-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="170be-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="170be-118">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="170be-118">MANAGED_EXCEPTION_UNHANDLED</span></span>](cordebugrecordformat-enumeration.md)  
  
> [!NOTE]
> <span data-ttu-id="170be-119">Interfejs jest dostępny tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="170be-119">The interface is available with .NET Native only.</span></span> <span data-ttu-id="170be-120">Podjęto próbę wywołania `QueryInterface`, aby pobrać wskaźnik interfejsu zwraca `E_NOINTERFACE` dla scenariuszy ICorDebug poza .NET Native.</span><span class="sxs-lookup"><span data-stu-id="170be-120">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="170be-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="170be-121">Requirements</span></span>  
 <span data-ttu-id="170be-122">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="170be-122">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="170be-123">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="170be-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="170be-124">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="170be-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="170be-125">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="170be-125">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="170be-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="170be-126">See also</span></span>

- [<span data-ttu-id="170be-127">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="170be-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="170be-128">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="170be-128">Debugging</span></span>](index.md)

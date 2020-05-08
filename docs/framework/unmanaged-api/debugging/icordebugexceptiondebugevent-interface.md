---
title: Interfejs ICorDebugExceptionDebugEvent
ms.date: 03/30/2017
ms.assetid: f9ba60d8-b54d-417e-bb3e-fde4b41ca44c
ms.openlocfilehash: dfa65aa1b63c996068e75ff1165111d5fcfe77eb
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976008"
---
# <a name="icordebugexceptiondebugevent-interface"></a><span data-ttu-id="29dfc-102">Interfejs ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="29dfc-102">ICorDebugExceptionDebugEvent Interface</span></span>
<span data-ttu-id="29dfc-103">Rozszerza interfejs [ICorDebugDebugEvent](icordebugdebugevent-interface.md) w celu obsługi zdarzeń wyjątków.</span><span class="sxs-lookup"><span data-stu-id="29dfc-103">Extends the [ICorDebugDebugEvent](icordebugdebugevent-interface.md) interface to support exception events.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="29dfc-104">Metody</span><span class="sxs-lookup"><span data-stu-id="29dfc-104">Methods</span></span>  
  
|<span data-ttu-id="29dfc-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="29dfc-105">Method</span></span>|<span data-ttu-id="29dfc-106">Opis</span><span class="sxs-lookup"><span data-stu-id="29dfc-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="29dfc-107">GetFlags, metoda</span><span class="sxs-lookup"><span data-stu-id="29dfc-107">GetFlags Method</span></span>](icordebugexceptiondebugevent-getflags-method.md)|<span data-ttu-id="29dfc-108">Pobiera flagę wskazującą, czy wyjątek może być przechwytywany.</span><span class="sxs-lookup"><span data-stu-id="29dfc-108">Gets a flag that indicates whether the exception is can be intercepted.</span></span>|  
|[<span data-ttu-id="29dfc-109">GetNativeIP, metoda</span><span class="sxs-lookup"><span data-stu-id="29dfc-109">GetNativeIP Method</span></span>](icordebugexceptiondebugevent-getnativeip-method.md)|<span data-ttu-id="29dfc-110">Pobiera wskaźnik interfejsu macierzystego dla tego zdarzenia debugowania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="29dfc-110">Gets the native interface pointer for this exception debug event.</span></span>|  
|[<span data-ttu-id="29dfc-111">GetStackPointer, metoda</span><span class="sxs-lookup"><span data-stu-id="29dfc-111">GetStackPointer Method</span></span>](icordebugexceptiondebugevent-getstackpointer-method.md)|<span data-ttu-id="29dfc-112">Pobiera wskaźnik stosu dla tego zdarzenia debugowania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="29dfc-112">Gets the stack pointer for this exception debug event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29dfc-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="29dfc-113">Remarks</span></span>  
 <span data-ttu-id="29dfc-114">`ICorDebugExceptionDebugEvent` Interfejs jest implementowany przez następujące typy zdarzeń:</span><span class="sxs-lookup"><span data-stu-id="29dfc-114">The `ICorDebugExceptionDebugEvent` interface is implemented by the following event types:</span></span>  
  
- [<span data-ttu-id="29dfc-115">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="29dfc-115">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="29dfc-116">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="29dfc-116">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="29dfc-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="29dfc-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](cordebugrecordformat-enumeration.md)  
  
- [<span data-ttu-id="29dfc-118">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="29dfc-118">MANAGED_EXCEPTION_UNHANDLED</span></span>](cordebugrecordformat-enumeration.md)  
  
> [!NOTE]
> <span data-ttu-id="29dfc-119">Interfejs jest dostępny tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="29dfc-119">The interface is available with .NET Native only.</span></span> <span data-ttu-id="29dfc-120">Próba wywołania metody `QueryInterface` pobierającej wskaźnik interfejsu zwraca `E_NOINTERFACE` dla scenariuszy ICorDebug poza .NET Native.</span><span class="sxs-lookup"><span data-stu-id="29dfc-120">Attempting to call `QueryInterface` to retrieve an interface pointer returns `E_NOINTERFACE` for ICorDebug scenarios outside of .NET Native.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29dfc-121">Wymagania</span><span class="sxs-lookup"><span data-stu-id="29dfc-121">Requirements</span></span>  
 <span data-ttu-id="29dfc-122">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29dfc-122">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29dfc-123">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="29dfc-123">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="29dfc-124">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="29dfc-124">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29dfc-125">**.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29dfc-125">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29dfc-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="29dfc-126">See also</span></span>

- [<span data-ttu-id="29dfc-127">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="29dfc-127">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="29dfc-128">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="29dfc-128">Debugging</span></span>](index.md)

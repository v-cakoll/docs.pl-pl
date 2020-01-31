---
title: 'ICorDebugExceptionDebugEvent:: GetStackPointer, Metoda'
ms.date: 03/30/2017
ms.assetid: d8f66a1c-16be-4264-afc5-bc2dfbb4a682
ms.openlocfilehash: 657649b97262a12639117defe7a9c546f08cfef5
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76782854"
---
# <a name="icordebugexceptiondebugeventgetstackpointer-method"></a><span data-ttu-id="1efc9-102">ICorDebugExceptionDebugEvent:: GetStackPointer, Metoda</span><span class="sxs-lookup"><span data-stu-id="1efc9-102">ICorDebugExceptionDebugEvent::GetStackPointer Method</span></span>
<span data-ttu-id="1efc9-103">Pobiera wskaźnik stosu dla tego zdarzenia debugowania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="1efc9-103">Gets the stack pointer for this exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1efc9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1efc9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStackPointer(  
   [out]CORDB_ADDRESS *pStackPointer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1efc9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1efc9-105">Parameters</span></span>  
 `pStackPointer`  
 <span data-ttu-id="1efc9-106">określoną Wskaźnik do adresu wskaźnika stosu dla tego zdarzenia debugowania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="1efc9-106">[out] A pointer to the address of the stack pointer for this exception debug event.</span></span> <span data-ttu-id="1efc9-107">Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="1efc9-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1efc9-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1efc9-108">Remarks</span></span>  
 <span data-ttu-id="1efc9-109">Znaczenie tego wskaźnika stosu zależy od typu zdarzenia, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="1efc9-109">The meaning of this stack pointer depends on the event type, as shown in the following table.</span></span>  
  
|<span data-ttu-id="1efc9-110">Typ zdarzenia</span><span class="sxs-lookup"><span data-stu-id="1efc9-110">Event type</span></span>|<span data-ttu-id="1efc9-111">Znaczenie wartości `pStackPointer`</span><span class="sxs-lookup"><span data-stu-id="1efc9-111">Meaning of `pStackPointer` value</span></span>|  
|----------------|--------------------------------------|  
|[<span data-ttu-id="1efc9-112">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="1efc9-112">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="1efc9-113">Wskaźnik stosu dla ramki, która wywołała wyjątek.</span><span class="sxs-lookup"><span data-stu-id="1efc9-113">The stack pointer for the frame that threw the exception.</span></span>|  
|[<span data-ttu-id="1efc9-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="1efc9-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="1efc9-115">Wskaźnik stosu dla ramki kodu użytkownika znajdującej się najbliżej punktu zgłoszonego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="1efc9-115">The stack pointer for the user-code frame closest to the point of the thrown exception.</span></span>|  
|[<span data-ttu-id="1efc9-116">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="1efc9-116">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="1efc9-117">Wskaźnik stosu dla ramki, która zawiera procedurę obsługi catch.</span><span class="sxs-lookup"><span data-stu-id="1efc9-117">The stack pointer for the frame that contains the catch handler.</span></span>|  
|[<span data-ttu-id="1efc9-118">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="1efc9-118">MANAGED_EXCEPTION_UNHANDLED</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="1efc9-119">`pStackPointer` ma **wartość null**.</span><span class="sxs-lookup"><span data-stu-id="1efc9-119">`pStackPointer` is **null**.</span></span>|  
  
> [!NOTE]
> <span data-ttu-id="1efc9-120">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="1efc9-120">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="1efc9-121">Typ zdarzenia jest dostępny w metodzie [ICorDebugDebugEvent:: GetEventKind](icordebugdebugevent-geteventkind-method.md) .</span><span class="sxs-lookup"><span data-stu-id="1efc9-121">The event type is available from the [ICorDebugDebugEvent::GetEventKind](icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1efc9-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1efc9-122">Requirements</span></span>  
 <span data-ttu-id="1efc9-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1efc9-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1efc9-124">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="1efc9-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1efc9-125">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1efc9-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1efc9-126">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1efc9-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1efc9-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1efc9-127">See also</span></span>

- [<span data-ttu-id="1efc9-128">ICorDebugExceptionDebugEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="1efc9-128">ICorDebugExceptionDebugEvent Interface</span></span>](icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="1efc9-129">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="1efc9-129">Debugging Interfaces</span></span>](debugging-interfaces.md)

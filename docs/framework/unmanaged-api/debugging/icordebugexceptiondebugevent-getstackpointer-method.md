---
title: Metoda ICorDebugExceptionDebugEvent::GetStackPointer
ms.date: 03/30/2017
ms.assetid: d8f66a1c-16be-4264-afc5-bc2dfbb4a682
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9f5ea632ad8a7dd2e24e71742223936b01298f31
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485160"
---
# <a name="icordebugexceptiondebugeventgetstackpointer-method"></a><span data-ttu-id="f0fda-102">Metoda ICorDebugExceptionDebugEvent::GetStackPointer</span><span class="sxs-lookup"><span data-stu-id="f0fda-102">ICorDebugExceptionDebugEvent::GetStackPointer Method</span></span>
<span data-ttu-id="f0fda-103">Pobiera wskaźnik stosu dla tego zdarzenia debugowania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="f0fda-103">Gets the stack pointer for this exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0fda-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f0fda-104">Syntax</span></span>  
  
```  
HRESULT GetStackPointer(  
   [out]CORDB_ADDRESS *pStackPointer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f0fda-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f0fda-105">Parameters</span></span>  
 `pStackPointer`  
 <span data-ttu-id="f0fda-106">[out] Zdarzenie debugowania wskaźnik na adres wskaźnik stosu dla tego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="f0fda-106">[out] A pointer to the address of the stack pointer for this exception debug event.</span></span> <span data-ttu-id="f0fda-107">Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="f0fda-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f0fda-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f0fda-108">Remarks</span></span>  
 <span data-ttu-id="f0fda-109">Znaczenie tego wskaźnik stosu zależy od typu zdarzenia, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="f0fda-109">The meaning of this stack pointer depends on the event type, as shown in the following table.</span></span>  
  
|<span data-ttu-id="f0fda-110">Typ zdarzenia</span><span class="sxs-lookup"><span data-stu-id="f0fda-110">Event type</span></span>|<span data-ttu-id="f0fda-111">Znaczenie `pStackPointer` wartość</span><span class="sxs-lookup"><span data-stu-id="f0fda-111">Meaning of `pStackPointer` value</span></span>|  
|----------------|--------------------------------------|  
|[<span data-ttu-id="f0fda-112">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="f0fda-112">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="f0fda-113">Wskaźnik stosu ramki, który wygenerował wyjątek.</span><span class="sxs-lookup"><span data-stu-id="f0fda-113">The stack pointer for the frame that threw the exception.</span></span>|  
|[<span data-ttu-id="f0fda-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="f0fda-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="f0fda-115">Wskaźnik stosu ramki kodu użytkownika najbliższy punkt zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="f0fda-115">The stack pointer for the user-code frame closest to the point of the thrown exception.</span></span>|  
|[<span data-ttu-id="f0fda-116">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="f0fda-116">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="f0fda-117">Wskaźnik stosu ramki, który zawiera program obsługi catch.</span><span class="sxs-lookup"><span data-stu-id="f0fda-117">The stack pointer for the frame that contains the catch handler.</span></span>|  
|[<span data-ttu-id="f0fda-118">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="f0fda-118">MANAGED_EXCEPTION_UNHANDLED</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="f0fda-119">`pStackPointer` jest **null**.</span><span class="sxs-lookup"><span data-stu-id="f0fda-119">`pStackPointer` is **null**.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="f0fda-120">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f0fda-120">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="f0fda-121">Typ zdarzenia jest dostępne z [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="f0fda-121">The event type is available from the [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f0fda-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f0fda-122">Requirements</span></span>  
 <span data-ttu-id="f0fda-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f0fda-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f0fda-124">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f0fda-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f0fda-125">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f0fda-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f0fda-126">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f0fda-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f0fda-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f0fda-127">See also</span></span>
- [<span data-ttu-id="f0fda-128">ICorDebugExceptionDebugEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="f0fda-128">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="f0fda-129">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="f0fda-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

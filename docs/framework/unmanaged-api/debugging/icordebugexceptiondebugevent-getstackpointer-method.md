---
title: ICorDebugExceptionDebugEvent::GetStackPointer — metoda
ms.date: 03/30/2017
ms.assetid: d8f66a1c-16be-4264-afc5-bc2dfbb4a682
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6e724b3a928a23bb44c3d1005024f803b5974e6b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33415558"
---
# <a name="icordebugexceptiondebugeventgetstackpointer-method"></a><span data-ttu-id="4d973-102">ICorDebugExceptionDebugEvent::GetStackPointer — metoda</span><span class="sxs-lookup"><span data-stu-id="4d973-102">ICorDebugExceptionDebugEvent::GetStackPointer Method</span></span>
<span data-ttu-id="4d973-103">Pobiera wskaźnik stosu dla tego zdarzenia debugowania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="4d973-103">Gets the stack pointer for this exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d973-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4d973-104">Syntax</span></span>  
  
```  
HRESULT GetStackPointer(  
   [out]CORDB_ADDRESS *pStackPointer  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4d973-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4d973-105">Parameters</span></span>  
 `pStackPointer`  
 <span data-ttu-id="4d973-106">[out] Zdarzenie debugowania wskaźnik adres wskaźnik stosu dla tego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="4d973-106">[out] A pointer to the address of the stack pointer for this exception debug event.</span></span> <span data-ttu-id="4d973-107">Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="4d973-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d973-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4d973-108">Remarks</span></span>  
 <span data-ttu-id="4d973-109">Znaczenie ten wskaźnik stosu zależy od typu zdarzeń, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="4d973-109">The meaning of this stack pointer depends on the event type, as shown in the following table.</span></span>  
  
|<span data-ttu-id="4d973-110">Typ zdarzenia</span><span class="sxs-lookup"><span data-stu-id="4d973-110">Event type</span></span>|<span data-ttu-id="4d973-111">Znaczenie `pStackPointer` wartość</span><span class="sxs-lookup"><span data-stu-id="4d973-111">Meaning of `pStackPointer` value</span></span>|  
|----------------|--------------------------------------|  
|[<span data-ttu-id="4d973-112">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="4d973-112">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="4d973-113">Wskaźnik stosu dla ramki, która zgłosiła wyjątek.</span><span class="sxs-lookup"><span data-stu-id="4d973-113">The stack pointer for the frame that threw the exception.</span></span>|  
|[<span data-ttu-id="4d973-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="4d973-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="4d973-115">Wskaźnik stosu dla ramki kod użytkownika najbliższy punkt zwrócony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="4d973-115">The stack pointer for the user-code frame closest to the point of the thrown exception.</span></span>|  
|[<span data-ttu-id="4d973-116">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="4d973-116">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="4d973-117">Wskaźnik stosu ramki, który zawiera obsługi catch.</span><span class="sxs-lookup"><span data-stu-id="4d973-117">The stack pointer for the frame that contains the catch handler.</span></span>|  
|[<span data-ttu-id="4d973-118">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="4d973-118">MANAGED_EXCEPTION_UNHANDLED</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="4d973-119">`pStackPointer` jest **null**.</span><span class="sxs-lookup"><span data-stu-id="4d973-119">`pStackPointer` is **null**.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="4d973-120">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="4d973-120">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="4d973-121">Typ zdarzenia jest dostępna z [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="4d973-121">The event type is available from the [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d973-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4d973-122">Requirements</span></span>  
 <span data-ttu-id="4d973-123">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d973-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d973-124">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4d973-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4d973-125">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4d973-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4d973-126">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4d973-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d973-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4d973-127">See Also</span></span>  
 [<span data-ttu-id="4d973-128">ICorDebugExceptionDebugEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="4d973-128">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
 [<span data-ttu-id="4d973-129">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="4d973-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

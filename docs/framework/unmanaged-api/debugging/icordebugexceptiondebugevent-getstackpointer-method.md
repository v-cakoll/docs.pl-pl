---
title: Metoda ICorDebugExceptionDebugEvent::GetStackPointer
ms.date: 03/30/2017
ms.assetid: d8f66a1c-16be-4264-afc5-bc2dfbb4a682
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d9d4c0a1938edd3e2fe88ea6e418b3430f1b5cb8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59163205"
---
# <a name="icordebugexceptiondebugeventgetstackpointer-method"></a><span data-ttu-id="7b056-102">Metoda ICorDebugExceptionDebugEvent::GetStackPointer</span><span class="sxs-lookup"><span data-stu-id="7b056-102">ICorDebugExceptionDebugEvent::GetStackPointer Method</span></span>
<span data-ttu-id="7b056-103">Pobiera wskaźnik stosu dla tego zdarzenia debugowania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="7b056-103">Gets the stack pointer for this exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b056-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7b056-104">Syntax</span></span>  
  
```  
HRESULT GetStackPointer(  
   [out]CORDB_ADDRESS *pStackPointer  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7b056-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7b056-105">Parameters</span></span>  
 `pStackPointer`  
 <span data-ttu-id="7b056-106">[out] Zdarzenie debugowania wskaźnik na adres wskaźnik stosu dla tego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="7b056-106">[out] A pointer to the address of the stack pointer for this exception debug event.</span></span> <span data-ttu-id="7b056-107">Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="7b056-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7b056-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7b056-108">Remarks</span></span>  
 <span data-ttu-id="7b056-109">Znaczenie tego wskaźnik stosu zależy od typu zdarzenia, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="7b056-109">The meaning of this stack pointer depends on the event type, as shown in the following table.</span></span>  
  
|<span data-ttu-id="7b056-110">Typ zdarzenia</span><span class="sxs-lookup"><span data-stu-id="7b056-110">Event type</span></span>|<span data-ttu-id="7b056-111">Znaczenie `pStackPointer` wartość</span><span class="sxs-lookup"><span data-stu-id="7b056-111">Meaning of `pStackPointer` value</span></span>|  
|----------------|--------------------------------------|  
|[<span data-ttu-id="7b056-112">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="7b056-112">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="7b056-113">Wskaźnik stosu ramki, który wygenerował wyjątek.</span><span class="sxs-lookup"><span data-stu-id="7b056-113">The stack pointer for the frame that threw the exception.</span></span>|  
|[<span data-ttu-id="7b056-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="7b056-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="7b056-115">Wskaźnik stosu ramki kodu użytkownika najbliższy punkt zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="7b056-115">The stack pointer for the user-code frame closest to the point of the thrown exception.</span></span>|  
|[<span data-ttu-id="7b056-116">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="7b056-116">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="7b056-117">Wskaźnik stosu ramki, który zawiera program obsługi catch.</span><span class="sxs-lookup"><span data-stu-id="7b056-117">The stack pointer for the frame that contains the catch handler.</span></span>|  
|[<span data-ttu-id="7b056-118">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="7b056-118">MANAGED_EXCEPTION_UNHANDLED</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="7b056-119">`pStackPointer` jest **null**.</span><span class="sxs-lookup"><span data-stu-id="7b056-119">`pStackPointer` is **null**.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="7b056-120">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="7b056-120">This method is available with .NET Native only.</span></span>  
  
 <span data-ttu-id="7b056-121">Typ zdarzenia jest dostępne z [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="7b056-121">The event type is available from the [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b056-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7b056-122">Requirements</span></span>  
 <span data-ttu-id="7b056-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b056-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b056-124">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7b056-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7b056-125">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7b056-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b056-126">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b056-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7b056-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7b056-127">See also</span></span>

- [<span data-ttu-id="7b056-128">ICorDebugExceptionDebugEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="7b056-128">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="7b056-129">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="7b056-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

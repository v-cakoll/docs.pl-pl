---
title: Metoda ICorDebugExceptionDebugEvent::GetNativeIP
ms.date: 03/30/2017
ms.assetid: 12e6a262-d9ac-49b8-9b80-1e653a2a3819
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b0069f301df9908a584608c7d20e5348de47361c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57501607"
---
# <a name="icordebugexceptiondebugeventgetnativeip-method"></a><span data-ttu-id="84813-102">Metoda ICorDebugExceptionDebugEvent::GetNativeIP</span><span class="sxs-lookup"><span data-stu-id="84813-102">ICorDebugExceptionDebugEvent::GetNativeIP Method</span></span>
<span data-ttu-id="84813-103">Pobiera wskaźnik natywny instrukcji dla tego zdarzenia debugowania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="84813-103">Gets the native instruction pointer for this exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84813-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="84813-104">Syntax</span></span>  
  
```  
HRESULT GetNativeIP(  
   [out]CORDB_ADDRESS *pIP  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="84813-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="84813-105">Parameters</span></span>  
 `pIP`  
 <span data-ttu-id="84813-106">[out] Zdarzenie debugowania wskaźnik do wskaźnika instrukcji dla tego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="84813-106">[out] A pointer to the instruction pointer for this exception debug event.</span></span> <span data-ttu-id="84813-107">Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="84813-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="84813-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="84813-108">Remarks</span></span>  
 <span data-ttu-id="84813-109">Znaczenie ten wskaźnik instrukcji zależy od typu zdarzenia, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="84813-109">The meaning of this instruction pointer depends on the event type, as shown in the following table.</span></span>  
  
|<span data-ttu-id="84813-110">Typ zdarzenia</span><span class="sxs-lookup"><span data-stu-id="84813-110">Event type</span></span>|<span data-ttu-id="84813-111">Znaczenie `pStackPointer` wartość</span><span class="sxs-lookup"><span data-stu-id="84813-111">Meaning of `pStackPointer` value</span></span>|  
|----------------|--------------------------------------|  
|[<span data-ttu-id="84813-112">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="84813-112">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="84813-113">Adres błędną instrukcji.</span><span class="sxs-lookup"><span data-stu-id="84813-113">The address of the faulting instruction.</span></span>|  
|[<span data-ttu-id="84813-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="84813-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="84813-115">Adres kodu w ramce wskazywanym przez [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) metody, gdzie będzie Wznów wykonywanie, jeśli miał został zgłoszony żaden wyjątek.</span><span class="sxs-lookup"><span data-stu-id="84813-115">The code address in the frame indicated by the [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) method where execution would resume if no exception had been raised.</span></span> <span data-ttu-id="84813-116">Wyjątek może lub nie może powodować inny kod, takich jak blok catch `try/catch/finally` klauzuli do wykonania w tej ramce.</span><span class="sxs-lookup"><span data-stu-id="84813-116">The exception may or may not cause different code, such as the catch block of a `try/catch/finally` clause, to be executed in this frame.</span></span>|  
|[<span data-ttu-id="84813-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="84813-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="84813-118">Kod adresu, gdzie `catch` wykonanie procedury obsługi rozpocznie się w wskazanych przez [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="84813-118">The code address where `catch` handler execution will start in the frame indicated by the [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) method.</span></span>|  
|[<span data-ttu-id="84813-119">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="84813-119">MANAGED_EXCEPTION_UNHANDLED</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="84813-120">`pIP` ma wartość 0.</span><span class="sxs-lookup"><span data-stu-id="84813-120">`pIP` is 0.</span></span>|  
  
 <span data-ttu-id="84813-121">Typ zdarzenia jest dostępne z [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="84813-121">The event type is available from the [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="84813-122">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="84813-122">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="84813-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="84813-123">Requirements</span></span>  
 <span data-ttu-id="84813-124">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="84813-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="84813-125">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="84813-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="84813-126">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="84813-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="84813-127">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="84813-127">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="84813-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="84813-128">See also</span></span>
- [<span data-ttu-id="84813-129">ICorDebugExceptionDebugEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="84813-129">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="84813-130">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="84813-130">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

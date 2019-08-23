---
title: 'ICorDebugExceptionDebugEvent:: GetNativeIP, Metoda'
ms.date: 03/30/2017
ms.assetid: 12e6a262-d9ac-49b8-9b80-1e653a2a3819
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: aaa1a160bb316831540f68713647dbdc4b0f6895
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951854"
---
# <a name="icordebugexceptiondebugeventgetnativeip-method"></a><span data-ttu-id="2cb8c-102">ICorDebugExceptionDebugEvent:: GetNativeIP, Metoda</span><span class="sxs-lookup"><span data-stu-id="2cb8c-102">ICorDebugExceptionDebugEvent::GetNativeIP Method</span></span>
<span data-ttu-id="2cb8c-103">Pobiera wskaźnik natywnej instrukcji dla tego zdarzenia debugowania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="2cb8c-103">Gets the native instruction pointer for this exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cb8c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2cb8c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNativeIP(  
   [out]CORDB_ADDRESS *pIP  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2cb8c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2cb8c-105">Parameters</span></span>  
 `pIP`  
 <span data-ttu-id="2cb8c-106">określoną Wskaźnik do wskaźnika instrukcji dla tego zdarzenia debugowania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="2cb8c-106">[out] A pointer to the instruction pointer for this exception debug event.</span></span> <span data-ttu-id="2cb8c-107">Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="2cb8c-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2cb8c-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2cb8c-108">Remarks</span></span>  
 <span data-ttu-id="2cb8c-109">Znaczenie tego wskaźnika instrukcji zależy od typu zdarzenia, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="2cb8c-109">The meaning of this instruction pointer depends on the event type, as shown in the following table.</span></span>  
  
|<span data-ttu-id="2cb8c-110">Typ zdarzenia</span><span class="sxs-lookup"><span data-stu-id="2cb8c-110">Event type</span></span>|<span data-ttu-id="2cb8c-111">`pStackPointer` Znaczenie wartości</span><span class="sxs-lookup"><span data-stu-id="2cb8c-111">Meaning of `pStackPointer` value</span></span>|  
|----------------|--------------------------------------|  
|[<span data-ttu-id="2cb8c-112">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="2cb8c-112">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="2cb8c-113">Adres instrukcji powodującej błąd.</span><span class="sxs-lookup"><span data-stu-id="2cb8c-113">The address of the faulting instruction.</span></span>|  
|[<span data-ttu-id="2cb8c-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="2cb8c-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="2cb8c-115">Adres kodu w ramce wskazywanym przez metodę [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) , w której wykonywanie zostało wznowione, jeśli żaden wyjątek nie został zgłoszony.</span><span class="sxs-lookup"><span data-stu-id="2cb8c-115">The code address in the frame indicated by the [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) method where execution would resume if no exception had been raised.</span></span> <span data-ttu-id="2cb8c-116">Wyjątek może lub nie może spowodować, że inny kod, taki jak blok `try/catch/finally` catch klauzuli, ma być wykonywany w tej ramce.</span><span class="sxs-lookup"><span data-stu-id="2cb8c-116">The exception may or may not cause different code, such as the catch block of a `try/catch/finally` clause, to be executed in this frame.</span></span>|  
|[<span data-ttu-id="2cb8c-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="2cb8c-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="2cb8c-118">Adres kodu, na `catch` którym wykonywanie procedury obsługi rozpocznie się w ramce wskazywanym przez metodę [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) .</span><span class="sxs-lookup"><span data-stu-id="2cb8c-118">The code address where `catch` handler execution will start in the frame indicated by the [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) method.</span></span>|  
|[<span data-ttu-id="2cb8c-119">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="2cb8c-119">MANAGED_EXCEPTION_UNHANDLED</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="2cb8c-120">`pIP`jest równa 0.</span><span class="sxs-lookup"><span data-stu-id="2cb8c-120">`pIP` is 0.</span></span>|  
  
 <span data-ttu-id="2cb8c-121">Typ zdarzenia jest dostępny w metodzie [ICorDebugDebugEvent:: GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) .</span><span class="sxs-lookup"><span data-stu-id="2cb8c-121">The event type is available from the [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2cb8c-122">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="2cb8c-122">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2cb8c-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2cb8c-123">Requirements</span></span>  
 <span data-ttu-id="2cb8c-124">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2cb8c-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2cb8c-125">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2cb8c-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2cb8c-126">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2cb8c-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2cb8c-127">**.NET Framework wersje:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2cb8c-127">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cb8c-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2cb8c-128">See also</span></span>

- [<span data-ttu-id="2cb8c-129">ICorDebugExceptionDebugEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="2cb8c-129">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="2cb8c-130">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="2cb8c-130">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

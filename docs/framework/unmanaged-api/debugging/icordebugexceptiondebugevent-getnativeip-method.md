---
title: 'ICorDebugExceptionDebugEvent:: GetNativeIP, Metoda'
ms.date: 03/30/2017
ms.assetid: 12e6a262-d9ac-49b8-9b80-1e653a2a3819
ms.openlocfilehash: 31af92dae47027b7285b422a05014b081d7e39a2
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76788682"
---
# <a name="icordebugexceptiondebugeventgetnativeip-method"></a><span data-ttu-id="25ac1-102">ICorDebugExceptionDebugEvent:: GetNativeIP, Metoda</span><span class="sxs-lookup"><span data-stu-id="25ac1-102">ICorDebugExceptionDebugEvent::GetNativeIP Method</span></span>
<span data-ttu-id="25ac1-103">Pobiera wskaźnik natywnej instrukcji dla tego zdarzenia debugowania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="25ac1-103">Gets the native instruction pointer for this exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25ac1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="25ac1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNativeIP(  
   [out]CORDB_ADDRESS *pIP  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="25ac1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="25ac1-105">Parameters</span></span>  
 `pIP`  
 <span data-ttu-id="25ac1-106">określoną Wskaźnik do wskaźnika instrukcji dla tego zdarzenia debugowania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="25ac1-106">[out] A pointer to the instruction pointer for this exception debug event.</span></span> <span data-ttu-id="25ac1-107">Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="25ac1-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="25ac1-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="25ac1-108">Remarks</span></span>  
 <span data-ttu-id="25ac1-109">Znaczenie tego wskaźnika instrukcji zależy od typu zdarzenia, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="25ac1-109">The meaning of this instruction pointer depends on the event type, as shown in the following table.</span></span>  
  
|<span data-ttu-id="25ac1-110">Typ zdarzenia</span><span class="sxs-lookup"><span data-stu-id="25ac1-110">Event type</span></span>|<span data-ttu-id="25ac1-111">Znaczenie wartości `pStackPointer`</span><span class="sxs-lookup"><span data-stu-id="25ac1-111">Meaning of `pStackPointer` value</span></span>|  
|----------------|--------------------------------------|  
|[<span data-ttu-id="25ac1-112">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="25ac1-112">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="25ac1-113">Adres instrukcji powodującej błąd.</span><span class="sxs-lookup"><span data-stu-id="25ac1-113">The address of the faulting instruction.</span></span>|  
|[<span data-ttu-id="25ac1-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="25ac1-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="25ac1-115">Adres kodu w ramce wskazywanym przez metodę [GetStackPointer](icordebugexceptiondebugevent-getstackpointer-method.md) , w której wykonywanie zostało wznowione, jeśli żaden wyjątek nie został zgłoszony.</span><span class="sxs-lookup"><span data-stu-id="25ac1-115">The code address in the frame indicated by the [GetStackPointer](icordebugexceptiondebugevent-getstackpointer-method.md) method where execution would resume if no exception had been raised.</span></span> <span data-ttu-id="25ac1-116">Wyjątek może lub nie może spowodować innego kodu, takiego jak blok catch klauzuli `try/catch/finally`, do wykonania w tej ramce.</span><span class="sxs-lookup"><span data-stu-id="25ac1-116">The exception may or may not cause different code, such as the catch block of a `try/catch/finally` clause, to be executed in this frame.</span></span>|  
|[<span data-ttu-id="25ac1-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="25ac1-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="25ac1-118">Adres kodu, w którym `catch` wykonywania procedury obsługi rozpocznie się w ramce wskazywanym przez metodę [GetStackPointer](icordebugexceptiondebugevent-getstackpointer-method.md) .</span><span class="sxs-lookup"><span data-stu-id="25ac1-118">The code address where `catch` handler execution will start in the frame indicated by the [GetStackPointer](icordebugexceptiondebugevent-getstackpointer-method.md) method.</span></span>|  
|[<span data-ttu-id="25ac1-119">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="25ac1-119">MANAGED_EXCEPTION_UNHANDLED</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="25ac1-120">`pIP` jest równa 0.</span><span class="sxs-lookup"><span data-stu-id="25ac1-120">`pIP` is 0.</span></span>|  
  
 <span data-ttu-id="25ac1-121">Typ zdarzenia jest dostępny w metodzie [ICorDebugDebugEvent:: GetEventKind](icordebugdebugevent-geteventkind-method.md) .</span><span class="sxs-lookup"><span data-stu-id="25ac1-121">The event type is available from the [ICorDebugDebugEvent::GetEventKind](icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="25ac1-122">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="25ac1-122">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25ac1-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="25ac1-123">Requirements</span></span>  
 <span data-ttu-id="25ac1-124">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25ac1-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25ac1-125">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="25ac1-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="25ac1-126">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="25ac1-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="25ac1-127">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25ac1-127">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25ac1-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="25ac1-128">See also</span></span>

- [<span data-ttu-id="25ac1-129">ICorDebugExceptionDebugEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="25ac1-129">ICorDebugExceptionDebugEvent Interface</span></span>](icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="25ac1-130">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="25ac1-130">Debugging Interfaces</span></span>](debugging-interfaces.md)

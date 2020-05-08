---
title: 'ICorDebugExceptionDebugEvent:: GetNativeIP, Metoda'
ms.date: 03/30/2017
ms.assetid: 12e6a262-d9ac-49b8-9b80-1e653a2a3819
ms.openlocfilehash: 82dc892f3081c9f33ff7a2f363c326091f7cf039
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976034"
---
# <a name="icordebugexceptiondebugeventgetnativeip-method"></a><span data-ttu-id="cdb27-102">ICorDebugExceptionDebugEvent:: GetNativeIP, Metoda</span><span class="sxs-lookup"><span data-stu-id="cdb27-102">ICorDebugExceptionDebugEvent::GetNativeIP Method</span></span>
<span data-ttu-id="cdb27-103">Pobiera wskaźnik natywnej instrukcji dla tego zdarzenia debugowania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="cdb27-103">Gets the native instruction pointer for this exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdb27-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cdb27-104">Syntax</span></span>  
  
```cpp  
HRESULT GetNativeIP(  
   [out]CORDB_ADDRESS *pIP  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cdb27-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cdb27-105">Parameters</span></span>  
 `pIP`  
 <span data-ttu-id="cdb27-106">określoną Wskaźnik do wskaźnika instrukcji dla tego zdarzenia debugowania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="cdb27-106">[out] A pointer to the instruction pointer for this exception debug event.</span></span> <span data-ttu-id="cdb27-107">Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="cdb27-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cdb27-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cdb27-108">Remarks</span></span>  
 <span data-ttu-id="cdb27-109">Znaczenie tego wskaźnika instrukcji zależy od typu zdarzenia, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="cdb27-109">The meaning of this instruction pointer depends on the event type, as shown in the following table.</span></span>  
  
|<span data-ttu-id="cdb27-110">Typ zdarzenia</span><span class="sxs-lookup"><span data-stu-id="cdb27-110">Event type</span></span>|<span data-ttu-id="cdb27-111">Znaczenie `pStackPointer` wartości</span><span class="sxs-lookup"><span data-stu-id="cdb27-111">Meaning of `pStackPointer` value</span></span>|  
|----------------|--------------------------------------|  
|[<span data-ttu-id="cdb27-112">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="cdb27-112">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="cdb27-113">Adres instrukcji powodującej błąd.</span><span class="sxs-lookup"><span data-stu-id="cdb27-113">The address of the faulting instruction.</span></span>|  
|[<span data-ttu-id="cdb27-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="cdb27-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="cdb27-115">Adres kodu w ramce wskazywanym przez metodę [GetStackPointer](icordebugexceptiondebugevent-getstackpointer-method.md) , w której wykonywanie zostało wznowione, jeśli żaden wyjątek nie został zgłoszony.</span><span class="sxs-lookup"><span data-stu-id="cdb27-115">The code address in the frame indicated by the [GetStackPointer](icordebugexceptiondebugevent-getstackpointer-method.md) method where execution would resume if no exception had been raised.</span></span> <span data-ttu-id="cdb27-116">Wyjątek może lub nie może spowodować, że inny kod, taki jak blok catch `try/catch/finally` klauzuli, ma być wykonywany w tej ramce.</span><span class="sxs-lookup"><span data-stu-id="cdb27-116">The exception may or may not cause different code, such as the catch block of a `try/catch/finally` clause, to be executed in this frame.</span></span>|  
|[<span data-ttu-id="cdb27-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="cdb27-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="cdb27-118">Adres kodu, na `catch` którym wykonywanie procedury obsługi rozpocznie się w ramce wskazywanym przez metodę [GetStackPointer](icordebugexceptiondebugevent-getstackpointer-method.md) .</span><span class="sxs-lookup"><span data-stu-id="cdb27-118">The code address where `catch` handler execution will start in the frame indicated by the [GetStackPointer](icordebugexceptiondebugevent-getstackpointer-method.md) method.</span></span>|  
|[<span data-ttu-id="cdb27-119">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="cdb27-119">MANAGED_EXCEPTION_UNHANDLED</span></span>](cordebugrecordformat-enumeration.md)|<span data-ttu-id="cdb27-120">`pIP`jest równa 0.</span><span class="sxs-lookup"><span data-stu-id="cdb27-120">`pIP` is 0.</span></span>|  
  
 <span data-ttu-id="cdb27-121">Typ zdarzenia jest dostępny w metodzie [ICorDebugDebugEvent:: GetEventKind](icordebugdebugevent-geteventkind-method.md) .</span><span class="sxs-lookup"><span data-stu-id="cdb27-121">The event type is available from the [ICorDebugDebugEvent::GetEventKind](icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="cdb27-122">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="cdb27-122">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cdb27-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cdb27-123">Requirements</span></span>  
 <span data-ttu-id="cdb27-124">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cdb27-124">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cdb27-125">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="cdb27-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cdb27-126">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="cdb27-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cdb27-127">**.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cdb27-127">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cdb27-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cdb27-128">See also</span></span>

- [<span data-ttu-id="cdb27-129">Interfejs ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="cdb27-129">ICorDebugExceptionDebugEvent Interface</span></span>](icordebugexceptiondebugevent-interface.md)
- [<span data-ttu-id="cdb27-130">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="cdb27-130">Debugging Interfaces</span></span>](debugging-interfaces.md)

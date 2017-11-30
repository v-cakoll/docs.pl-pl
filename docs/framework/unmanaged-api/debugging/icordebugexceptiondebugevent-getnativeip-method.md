---
title: "ICorDebugExceptionDebugEvent::GetNativeIP — metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 12e6a262-d9ac-49b8-9b80-1e653a2a3819
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 616f0a9787220aba0cc4d460c80b856076e1e437
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugexceptiondebugeventgetnativeip-method"></a><span data-ttu-id="696f3-102">ICorDebugExceptionDebugEvent::GetNativeIP — metoda</span><span class="sxs-lookup"><span data-stu-id="696f3-102">ICorDebugExceptionDebugEvent::GetNativeIP Method</span></span>
<span data-ttu-id="696f3-103">Pobiera wskaźnik natywny instrukcji dla tego zdarzenia debugowania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="696f3-103">Gets the native instruction pointer for this exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="696f3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="696f3-104">Syntax</span></span>  
  
```  
HRESULT GetNativeIP(  
   [out]CORDB_ADDRESS *pIP  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="696f3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="696f3-105">Parameters</span></span>  
 `pIP`  
 <span data-ttu-id="696f3-106">[out] Zdarzenie debugowania wskaźnika do wskaźnika instrukcji dla tego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="696f3-106">[out] A pointer to the instruction pointer for this exception debug event.</span></span> <span data-ttu-id="696f3-107">Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="696f3-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="696f3-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="696f3-108">Remarks</span></span>  
 <span data-ttu-id="696f3-109">Znaczenie w tym wskaźniku instrukcji zależy od typu zdarzeń, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="696f3-109">The meaning of this instruction pointer depends on the event type, as shown in the following table.</span></span>  
  
|<span data-ttu-id="696f3-110">Typ zdarzenia</span><span class="sxs-lookup"><span data-stu-id="696f3-110">Event type</span></span>|<span data-ttu-id="696f3-111">Znaczenie `pStackPointer` wartość</span><span class="sxs-lookup"><span data-stu-id="696f3-111">Meaning of `pStackPointer` value</span></span>|  
|----------------|--------------------------------------|  
|[<span data-ttu-id="696f3-112">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="696f3-112">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="696f3-113">Adres źle działający instrukcji.</span><span class="sxs-lookup"><span data-stu-id="696f3-113">The address of the faulting instruction.</span></span>|  
|[<span data-ttu-id="696f3-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="696f3-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="696f3-115">Kod adres w ramce wskazywanym przez [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) metody, gdzie będzie wznowić wykonywanie miał został zgłoszony wyjątek nie.</span><span class="sxs-lookup"><span data-stu-id="696f3-115">The code address in the frame indicated by the [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) method where execution would resume if no exception had been raised.</span></span> <span data-ttu-id="696f3-116">Wyjątek może lub nie może spowodować inny kod, takich jak blok catch `try/catch/finally` klauzuli ma być wykonywana w tej ramce.</span><span class="sxs-lookup"><span data-stu-id="696f3-116">The exception may or may not cause different code, such as the catch block of a `try/catch/finally` clause, to be executed in this frame.</span></span>|  
|[<span data-ttu-id="696f3-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="696f3-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="696f3-118">Gdzie adresu kod `catch` rozpocznie się wykonywanie programu obsługi w ramce wskazywanym przez [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="696f3-118">The code address where `catch` handler execution will start in the frame indicated by the [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) method.</span></span>|  
|[<span data-ttu-id="696f3-119">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="696f3-119">MANAGED_EXCEPTION_UNHANDLED</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="696f3-120">`pIP`to 0.</span><span class="sxs-lookup"><span data-stu-id="696f3-120">`pIP` is 0.</span></span>|  
  
 <span data-ttu-id="696f3-121">Typ zdarzenia jest dostępna z [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="696f3-121">The event type is available from the [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="696f3-122">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="696f3-122">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="696f3-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="696f3-123">Requirements</span></span>  
 <span data-ttu-id="696f3-124">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="696f3-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="696f3-125">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="696f3-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="696f3-126">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="696f3-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="696f3-127">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="696f3-127">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="696f3-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="696f3-128">See Also</span></span>  
 [<span data-ttu-id="696f3-129">Interfejs ICorDebugExceptionDebugEvent</span><span class="sxs-lookup"><span data-stu-id="696f3-129">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
 [<span data-ttu-id="696f3-130">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="696f3-130">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

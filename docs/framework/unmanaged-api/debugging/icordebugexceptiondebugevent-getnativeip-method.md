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
ms.workload: dotnet
ms.openlocfilehash: 32e75a18645c000562cdd94478c6ef8db41a01a5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugexceptiondebugeventgetnativeip-method"></a><span data-ttu-id="afc74-102">ICorDebugExceptionDebugEvent::GetNativeIP — metoda</span><span class="sxs-lookup"><span data-stu-id="afc74-102">ICorDebugExceptionDebugEvent::GetNativeIP Method</span></span>
<span data-ttu-id="afc74-103">Pobiera wskaźnik natywny instrukcji dla tego zdarzenia debugowania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="afc74-103">Gets the native instruction pointer for this exception debug event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="afc74-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="afc74-104">Syntax</span></span>  
  
```  
HRESULT GetNativeIP(  
   [out]CORDB_ADDRESS *pIP  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="afc74-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="afc74-105">Parameters</span></span>  
 `pIP`  
 <span data-ttu-id="afc74-106">[out] Zdarzenie debugowania wskaźnika do wskaźnika instrukcji dla tego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="afc74-106">[out] A pointer to the instruction pointer for this exception debug event.</span></span> <span data-ttu-id="afc74-107">Zobacz sekcję Spostrzeżenia, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="afc74-107">See the Remarks section for more information.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="afc74-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="afc74-108">Remarks</span></span>  
 <span data-ttu-id="afc74-109">Znaczenie w tym wskaźniku instrukcji zależy od typu zdarzeń, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="afc74-109">The meaning of this instruction pointer depends on the event type, as shown in the following table.</span></span>  
  
|<span data-ttu-id="afc74-110">Typ zdarzenia</span><span class="sxs-lookup"><span data-stu-id="afc74-110">Event type</span></span>|<span data-ttu-id="afc74-111">Znaczenie `pStackPointer` wartość</span><span class="sxs-lookup"><span data-stu-id="afc74-111">Meaning of `pStackPointer` value</span></span>|  
|----------------|--------------------------------------|  
|[<span data-ttu-id="afc74-112">MANAGED_EXCEPTION_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="afc74-112">MANAGED_EXCEPTION_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="afc74-113">Adres źle działający instrukcji.</span><span class="sxs-lookup"><span data-stu-id="afc74-113">The address of the faulting instruction.</span></span>|  
|[<span data-ttu-id="afc74-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span><span class="sxs-lookup"><span data-stu-id="afc74-114">MANAGED_EXCEPTION_USER_FIRST_CHANCE</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="afc74-115">Kod adres w ramce wskazywanym przez [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) metody, gdzie będzie wznowić wykonywanie miał został zgłoszony wyjątek nie.</span><span class="sxs-lookup"><span data-stu-id="afc74-115">The code address in the frame indicated by the [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) method where execution would resume if no exception had been raised.</span></span> <span data-ttu-id="afc74-116">Wyjątek może lub nie może spowodować inny kod, takich jak blok catch `try/catch/finally` klauzuli ma być wykonywana w tej ramce.</span><span class="sxs-lookup"><span data-stu-id="afc74-116">The exception may or may not cause different code, such as the catch block of a `try/catch/finally` clause, to be executed in this frame.</span></span>|  
|[<span data-ttu-id="afc74-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span><span class="sxs-lookup"><span data-stu-id="afc74-117">MANAGED_EXCEPTION_CATCH_HANDLER_FOUND</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="afc74-118">Gdzie adresu kod `catch` rozpocznie się wykonywanie programu obsługi w ramce wskazywanym przez [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="afc74-118">The code address where `catch` handler execution will start in the frame indicated by the [GetStackPointer](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-getstackpointer-method.md) method.</span></span>|  
|[<span data-ttu-id="afc74-119">MANAGED_EXCEPTION_UNHANDLED</span><span class="sxs-lookup"><span data-stu-id="afc74-119">MANAGED_EXCEPTION_UNHANDLED</span></span>](../../../../docs/framework/unmanaged-api/debugging/cordebugrecordformat-enumeration.md)|<span data-ttu-id="afc74-120">`pIP`to 0.</span><span class="sxs-lookup"><span data-stu-id="afc74-120">`pIP` is 0.</span></span>|  
  
 <span data-ttu-id="afc74-121">Typ zdarzenia jest dostępna z [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="afc74-121">The event type is available from the [ICorDebugDebugEvent::GetEventKind](../../../../docs/framework/unmanaged-api/debugging/icordebugdebugevent-geteventkind-method.md) method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="afc74-122">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="afc74-122">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="afc74-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="afc74-123">Requirements</span></span>  
 <span data-ttu-id="afc74-124">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="afc74-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="afc74-125">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="afc74-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="afc74-126">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="afc74-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="afc74-127">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="afc74-127">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afc74-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="afc74-128">See Also</span></span>  
 [<span data-ttu-id="afc74-129">ICorDebugExceptionDebugEvent, interfejs</span><span class="sxs-lookup"><span data-stu-id="afc74-129">ICorDebugExceptionDebugEvent Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptiondebugevent-interface.md)  
 [<span data-ttu-id="afc74-130">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="afc74-130">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

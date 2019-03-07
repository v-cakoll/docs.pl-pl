---
title: Metoda ICorDebugDataTarget2::CreateVirtualUnwinder
ms.date: 03/30/2017
ms.assetid: 354c8b4c-7d23-45c6-a7d7-3be4c2a5b772
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 387dc484b3ada63d62ddc27318e735dfc4ea93b6
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57492273"
---
# <a name="icordebugdatatarget2createvirtualunwinder-method"></a><span data-ttu-id="e0717-102">Metoda ICorDebugDataTarget2::CreateVirtualUnwinder</span><span class="sxs-lookup"><span data-stu-id="e0717-102">ICorDebugDataTarget2::CreateVirtualUnwinder Method</span></span>
<span data-ttu-id="e0717-103">Tworzy nowy unwinder stosu, który rozpoczyna się odwijanie od początkowego kontekstu, (które niekoniecznie liścia wątku).</span><span class="sxs-lookup"><span data-stu-id="e0717-103">Creates a new stack unwinder that starts unwinding from an initial context (which isn't necessarily the leaf of a thread).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0717-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e0717-104">Syntax</span></span>  
  
```  
HRESULT CreateVirtualUnwinder(  
    [in] DWORD nativeThreadID,  
    [in] ULONG32 contextFlags,  
    [in] ULONG32 cbContext,  
    [in, size_is(cbContext)] BYTE initialContext[],  
    [out] ICorDebugVirtualUnwinder ** ppUnwinder);  
};  
```  
  
## <a name="parameters"></a><span data-ttu-id="e0717-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e0717-105">Parameters</span></span>  
 <span data-ttu-id="e0717-106">nativeThreadID</span><span class="sxs-lookup"><span data-stu-id="e0717-106">nativeThreadID</span></span>  
 <span data-ttu-id="e0717-107">[in] Identyfikator wątku natywnych wątku, którego stosu, które ma być rozwinięty.</span><span class="sxs-lookup"><span data-stu-id="e0717-107">[in] The native thread ID of the thread whose stack is to be unwound.</span></span>  
  
 <span data-ttu-id="e0717-108">contextFlags</span><span class="sxs-lookup"><span data-stu-id="e0717-108">contextFlags</span></span>  
 <span data-ttu-id="e0717-109">[in] Flagi określające, części kontekstu, które są zdefiniowane w `initialContext`.</span><span class="sxs-lookup"><span data-stu-id="e0717-109">[in] Flags that specify which parts of the context are defined in `initialContext`.</span></span>  
  
 <span data-ttu-id="e0717-110">cbContext</span><span class="sxs-lookup"><span data-stu-id="e0717-110">cbContext</span></span>  
 <span data-ttu-id="e0717-111">[in] Rozmiar `initialContext`.</span><span class="sxs-lookup"><span data-stu-id="e0717-111">[in] The size of `initialContext`.</span></span>  
  
 <span data-ttu-id="e0717-112">initialContext</span><span class="sxs-lookup"><span data-stu-id="e0717-112">initialContext</span></span>  
 <span data-ttu-id="e0717-113">[in] Dane w kontekście.</span><span class="sxs-lookup"><span data-stu-id="e0717-113">[in] The data in the context.</span></span>  
  
 <span data-ttu-id="e0717-114">ppUnwinder</span><span class="sxs-lookup"><span data-stu-id="e0717-114">ppUnwinder</span></span>  
 <span data-ttu-id="e0717-115">[out] Wskaźnik na adres obiektu interfejsu ICorDebugVirtualUnwinder.</span><span class="sxs-lookup"><span data-stu-id="e0717-115">[out] A pointer to the address of an ICorDebugVirtualUnwinder interface object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e0717-116">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="e0717-116">Return Value</span></span>  
 <span data-ttu-id="e0717-117">`S_OK` Jeśli to się powiedzie.</span><span class="sxs-lookup"><span data-stu-id="e0717-117">`S_OK` if successful.</span></span> <span data-ttu-id="e0717-118">Inne `HRESULT` wskazuje błąd.</span><span class="sxs-lookup"><span data-stu-id="e0717-118">Any other `HRESULT` indicates failure.</span></span> <span data-ttu-id="e0717-119">Wszelkie niepowodzenia `HRESULT` odebranych przez mscordbi jest uważane za krytyczne i powoduje, że [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) metody, aby zwrócić `CORDBG_E_DATA_TARGET_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="e0717-119">Any failing `HRESULT` received by mscordbi is considered fatal and causes [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) methods to return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e0717-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e0717-120">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e0717-121">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="e0717-121">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e0717-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e0717-122">Requirements</span></span>  
 <span data-ttu-id="e0717-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e0717-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e0717-124">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e0717-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e0717-125">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e0717-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e0717-126">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e0717-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e0717-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e0717-127">See also</span></span>
- [<span data-ttu-id="e0717-128">ICorDebugDataTarget2, interfejs</span><span class="sxs-lookup"><span data-stu-id="e0717-128">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)
- [<span data-ttu-id="e0717-129">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="e0717-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

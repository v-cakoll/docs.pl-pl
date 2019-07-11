---
title: Metoda ICorDebugDataTarget2::CreateVirtualUnwinder
ms.date: 03/30/2017
ms.assetid: 354c8b4c-7d23-45c6-a7d7-3be4c2a5b772
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a983561f34bee96f5de1e05d608bff930c7ec8c0
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750233"
---
# <a name="icordebugdatatarget2createvirtualunwinder-method"></a><span data-ttu-id="880f2-102">Metoda ICorDebugDataTarget2::CreateVirtualUnwinder</span><span class="sxs-lookup"><span data-stu-id="880f2-102">ICorDebugDataTarget2::CreateVirtualUnwinder Method</span></span>
<span data-ttu-id="880f2-103">Tworzy nowy unwinder stosu, który rozpoczyna się odwijanie od początkowego kontekstu, (które niekoniecznie liścia wątku).</span><span class="sxs-lookup"><span data-stu-id="880f2-103">Creates a new stack unwinder that starts unwinding from an initial context (which isn't necessarily the leaf of a thread).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="880f2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="880f2-104">Syntax</span></span>  
  
```cpp  
HRESULT CreateVirtualUnwinder(  
    [in] DWORD nativeThreadID,  
    [in] ULONG32 contextFlags,  
    [in] ULONG32 cbContext,  
    [in, size_is(cbContext)] BYTE initialContext[],  
    [out] ICorDebugVirtualUnwinder ** ppUnwinder);  
};  
```  
  
## <a name="parameters"></a><span data-ttu-id="880f2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="880f2-105">Parameters</span></span>  
 <span data-ttu-id="880f2-106">nativeThreadID</span><span class="sxs-lookup"><span data-stu-id="880f2-106">nativeThreadID</span></span>  
 <span data-ttu-id="880f2-107">[in] Identyfikator wątku natywnych wątku, którego stosu, które ma być rozwinięty.</span><span class="sxs-lookup"><span data-stu-id="880f2-107">[in] The native thread ID of the thread whose stack is to be unwound.</span></span>  
  
 <span data-ttu-id="880f2-108">contextFlags</span><span class="sxs-lookup"><span data-stu-id="880f2-108">contextFlags</span></span>  
 <span data-ttu-id="880f2-109">[in] Flagi określające, części kontekstu, które są zdefiniowane w `initialContext`.</span><span class="sxs-lookup"><span data-stu-id="880f2-109">[in] Flags that specify which parts of the context are defined in `initialContext`.</span></span>  
  
 <span data-ttu-id="880f2-110">cbContext</span><span class="sxs-lookup"><span data-stu-id="880f2-110">cbContext</span></span>  
 <span data-ttu-id="880f2-111">[in] Rozmiar `initialContext`.</span><span class="sxs-lookup"><span data-stu-id="880f2-111">[in] The size of `initialContext`.</span></span>  
  
 <span data-ttu-id="880f2-112">initialContext</span><span class="sxs-lookup"><span data-stu-id="880f2-112">initialContext</span></span>  
 <span data-ttu-id="880f2-113">[in] Dane w kontekście.</span><span class="sxs-lookup"><span data-stu-id="880f2-113">[in] The data in the context.</span></span>  
  
 <span data-ttu-id="880f2-114">ppUnwinder</span><span class="sxs-lookup"><span data-stu-id="880f2-114">ppUnwinder</span></span>  
 <span data-ttu-id="880f2-115">[out] Wskaźnik na adres obiektu interfejsu ICorDebugVirtualUnwinder.</span><span class="sxs-lookup"><span data-stu-id="880f2-115">[out] A pointer to the address of an ICorDebugVirtualUnwinder interface object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="880f2-116">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="880f2-116">Return Value</span></span>  
 <span data-ttu-id="880f2-117">`S_OK` Jeśli to się powiedzie.</span><span class="sxs-lookup"><span data-stu-id="880f2-117">`S_OK` if successful.</span></span> <span data-ttu-id="880f2-118">Inne `HRESULT` wskazuje błąd.</span><span class="sxs-lookup"><span data-stu-id="880f2-118">Any other `HRESULT` indicates failure.</span></span> <span data-ttu-id="880f2-119">Wszelkie niepowodzenia `HRESULT` odebranych przez mscordbi jest uważane za krytyczne i powoduje, że [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) metody, aby zwrócić `CORDBG_E_DATA_TARGET_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="880f2-119">Any failing `HRESULT` received by mscordbi is considered fatal and causes [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) methods to return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="880f2-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="880f2-120">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="880f2-121">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="880f2-121">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="880f2-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="880f2-122">Requirements</span></span>  
 <span data-ttu-id="880f2-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="880f2-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="880f2-124">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="880f2-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="880f2-125">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="880f2-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="880f2-126">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="880f2-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="880f2-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="880f2-127">See also</span></span>

- [<span data-ttu-id="880f2-128">ICorDebugDataTarget2, interfejs</span><span class="sxs-lookup"><span data-stu-id="880f2-128">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)
- [<span data-ttu-id="880f2-129">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="880f2-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

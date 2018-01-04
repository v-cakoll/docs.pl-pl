---
title: Metoda ICorDebugDataTarget2::CreateVirtualUnwinder
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 354c8b4c-7d23-45c6-a7d7-3be4c2a5b772
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9bffbf95fc38cba6f311e0641b35e2696bd34099
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugdatatarget2createvirtualunwinder-method"></a><span data-ttu-id="21402-102">Metoda ICorDebugDataTarget2::CreateVirtualUnwinder</span><span class="sxs-lookup"><span data-stu-id="21402-102">ICorDebugDataTarget2::CreateVirtualUnwinder Method</span></span>
<span data-ttu-id="21402-103">Tworzy nowy unwinder stosu, uruchamiany rozwinięcia z kontekstu początkowej (co jest zawsze typu liść wątku).</span><span class="sxs-lookup"><span data-stu-id="21402-103">Creates a new stack unwinder that starts unwinding from an initial context (which isn't necessarily the leaf of a thread).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21402-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="21402-104">Syntax</span></span>  
  
```  
HRESULT CreateVirtualUnwinder(  
    [in] DWORD nativeThreadID,  
    [in] ULONG32 contextFlags,  
    [in] ULONG32 cbContext,  
    [in, size_is(cbContext)] BYTE initialContext[],  
    [out] ICorDebugVirtualUnwinder ** ppUnwinder);  
};  
```  
  
#### <a name="parameters"></a><span data-ttu-id="21402-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="21402-105">Parameters</span></span>  
 <span data-ttu-id="21402-106">nativeThreadID</span><span class="sxs-lookup"><span data-stu-id="21402-106">nativeThreadID</span></span>  
 <span data-ttu-id="21402-107">[in] Wątek macierzysty identyfikator wątku, w których stos jest za oddzielić.</span><span class="sxs-lookup"><span data-stu-id="21402-107">[in] The native thread ID of the thread whose stack is to be unwound.</span></span>  
  
 <span data-ttu-id="21402-108">contextFlags</span><span class="sxs-lookup"><span data-stu-id="21402-108">contextFlags</span></span>  
 <span data-ttu-id="21402-109">[in] Flagi określające, które części kontekstu są zdefiniowane w `initialContext`.</span><span class="sxs-lookup"><span data-stu-id="21402-109">[in] Flags that specify which parts of the context are defined in `initialContext`.</span></span>  
  
 <span data-ttu-id="21402-110">cbContext</span><span class="sxs-lookup"><span data-stu-id="21402-110">cbContext</span></span>  
 <span data-ttu-id="21402-111">[in] Rozmiar `initialContext`.</span><span class="sxs-lookup"><span data-stu-id="21402-111">[in] The size of `initialContext`.</span></span>  
  
 <span data-ttu-id="21402-112">initialContext</span><span class="sxs-lookup"><span data-stu-id="21402-112">initialContext</span></span>  
 <span data-ttu-id="21402-113">[in] Dane w tym kontekście.</span><span class="sxs-lookup"><span data-stu-id="21402-113">[in] The data in the context.</span></span>  
  
 <span data-ttu-id="21402-114">ppUnwinder</span><span class="sxs-lookup"><span data-stu-id="21402-114">ppUnwinder</span></span>  
 <span data-ttu-id="21402-115">[out] Wskaźnik do adresu icordebugvirtualunwinder — interfejs obiektu.</span><span class="sxs-lookup"><span data-stu-id="21402-115">[out] A pointer to the address of an ICorDebugVirtualUnwinder interface object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="21402-116">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="21402-116">Return Value</span></span>  
 <span data-ttu-id="21402-117">`S_OK`w przypadku powodzenia.</span><span class="sxs-lookup"><span data-stu-id="21402-117">`S_OK` if successful.</span></span> <span data-ttu-id="21402-118">Inne `HRESULT` wskazuje błąd.</span><span class="sxs-lookup"><span data-stu-id="21402-118">Any other `HRESULT` indicates failure.</span></span> <span data-ttu-id="21402-119">Wszelkie niepowodzenie `HRESULT` odebranych przez mscordbi jest on traktowany jako krytyczny i powoduje, że [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) metod do zwrócenia `CORDBG_E_DATA_TARGET_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="21402-119">Any failing `HRESULT` received by mscordbi is considered fatal and causes [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) methods to return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="21402-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="21402-120">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="21402-121">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="21402-121">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21402-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="21402-122">Requirements</span></span>  
 <span data-ttu-id="21402-123">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="21402-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="21402-124">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="21402-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="21402-125">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="21402-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="21402-126">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="21402-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="21402-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="21402-127">See Also</span></span>  
 [<span data-ttu-id="21402-128">ICorDebugDataTarget2, interfejs</span><span class="sxs-lookup"><span data-stu-id="21402-128">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 [<span data-ttu-id="21402-129">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="21402-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

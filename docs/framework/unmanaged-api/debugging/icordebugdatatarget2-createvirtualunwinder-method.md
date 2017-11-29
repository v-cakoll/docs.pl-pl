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
ms.openlocfilehash: 421cff28e84106c0859889e6f9e99e870b469a98
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugdatatarget2createvirtualunwinder-method"></a><span data-ttu-id="f8dc9-102">Metoda ICorDebugDataTarget2::CreateVirtualUnwinder</span><span class="sxs-lookup"><span data-stu-id="f8dc9-102">ICorDebugDataTarget2::CreateVirtualUnwinder Method</span></span>
<span data-ttu-id="f8dc9-103">Tworzy nowy unwinder stosu, uruchamiany rozwinięcia z kontekstu początkowej (co jest zawsze typu liść wątku).</span><span class="sxs-lookup"><span data-stu-id="f8dc9-103">Creates a new stack unwinder that starts unwinding from an initial context (which isn't necessarily the leaf of a thread).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8dc9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f8dc9-104">Syntax</span></span>  
  
```  
HRESULT CreateVirtualUnwinder(  
    [in] DWORD nativeThreadID,  
    [in] ULONG32 contextFlags,  
    [in] ULONG32 cbContext,  
    [in, size_is(cbContext)] BYTE initialContext[],  
    [out] ICorDebugVirtualUnwinder ** ppUnwinder);  
};  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f8dc9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f8dc9-105">Parameters</span></span>  
 <span data-ttu-id="f8dc9-106">nativeThreadID</span><span class="sxs-lookup"><span data-stu-id="f8dc9-106">nativeThreadID</span></span>  
 <span data-ttu-id="f8dc9-107">[in] Wątek macierzysty identyfikator wątku, w których stos jest za oddzielić.</span><span class="sxs-lookup"><span data-stu-id="f8dc9-107">[in] The native thread ID of the thread whose stack is to be unwound.</span></span>  
  
 <span data-ttu-id="f8dc9-108">contextFlags</span><span class="sxs-lookup"><span data-stu-id="f8dc9-108">contextFlags</span></span>  
 <span data-ttu-id="f8dc9-109">[in] Flagi określające, które części kontekstu są zdefiniowane w `initialContext`.</span><span class="sxs-lookup"><span data-stu-id="f8dc9-109">[in] Flags that specify which parts of the context are defined in `initialContext`.</span></span>  
  
 <span data-ttu-id="f8dc9-110">cbContext</span><span class="sxs-lookup"><span data-stu-id="f8dc9-110">cbContext</span></span>  
 <span data-ttu-id="f8dc9-111">[in] Rozmiar `initialContext`.</span><span class="sxs-lookup"><span data-stu-id="f8dc9-111">[in] The size of `initialContext`.</span></span>  
  
 <span data-ttu-id="f8dc9-112">initialContext</span><span class="sxs-lookup"><span data-stu-id="f8dc9-112">initialContext</span></span>  
 <span data-ttu-id="f8dc9-113">[in] Dane w tym kontekście.</span><span class="sxs-lookup"><span data-stu-id="f8dc9-113">[in] The data in the context.</span></span>  
  
 <span data-ttu-id="f8dc9-114">ppUnwinder</span><span class="sxs-lookup"><span data-stu-id="f8dc9-114">ppUnwinder</span></span>  
 <span data-ttu-id="f8dc9-115">[out] Wskaźnik do adresu icordebugvirtualunwinder — interfejs obiektu.</span><span class="sxs-lookup"><span data-stu-id="f8dc9-115">[out] A pointer to the address of an ICorDebugVirtualUnwinder interface object.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f8dc9-116">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="f8dc9-116">Return Value</span></span>  
 <span data-ttu-id="f8dc9-117">`S_OK`w przypadku powodzenia.</span><span class="sxs-lookup"><span data-stu-id="f8dc9-117">`S_OK` if successful.</span></span> <span data-ttu-id="f8dc9-118">Inne `HRESULT` wskazuje błąd.</span><span class="sxs-lookup"><span data-stu-id="f8dc9-118">Any other `HRESULT` indicates failure.</span></span> <span data-ttu-id="f8dc9-119">Wszelkie niepowodzenie `HRESULT` odebranych przez mscordbi jest on traktowany jako krytyczny i powoduje, że [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) metod do zwrócenia `CORDBG_E_DATA_TARGET_ERROR`.</span><span class="sxs-lookup"><span data-stu-id="f8dc9-119">Any failing `HRESULT` received by mscordbi is considered fatal and causes [ICorDebug](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md) methods to return `CORDBG_E_DATA_TARGET_ERROR`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f8dc9-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f8dc9-120">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f8dc9-121">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="f8dc9-121">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8dc9-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f8dc9-122">Requirements</span></span>  
 <span data-ttu-id="f8dc9-123">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8dc9-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f8dc9-124">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f8dc9-124">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f8dc9-125">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f8dc9-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f8dc9-126">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f8dc9-126">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8dc9-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f8dc9-127">See Also</span></span>  
 [<span data-ttu-id="f8dc9-128">Interfejs ICorDebugDataTarget2</span><span class="sxs-lookup"><span data-stu-id="f8dc9-128">ICorDebugDataTarget2 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget2-interface.md)  
 [<span data-ttu-id="f8dc9-129">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="f8dc9-129">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

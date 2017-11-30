---
title: "ICorDebugVariableSymbol::SetValue — metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 4609418d-71fa-44bc-9618-4d529d25cabb
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 12c13259d20301b0f485a6041fa884b0996cbbdc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvariablesymbolsetvalue-method"></a><span data-ttu-id="275c9-102">ICorDebugVariableSymbol::SetValue — metoda</span><span class="sxs-lookup"><span data-stu-id="275c9-102">ICorDebugVariableSymbol::SetValue Method</span></span>
<span data-ttu-id="275c9-103">Przypisuje wartość tablica bajtów do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="275c9-103">Assigns the value of a byte array to a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="275c9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="275c9-104">Syntax</span></span>  
  
```  
HRESULT SetValue(  
   [in] ULONG32 offset,  
   [in] DWORD threadID,  
   [in] ULONG32 cbContext,  
   [in, size_is(cbContext)] BYTE context[],  
   [in] ULONG32 cbValue,  
   [in, size_is(cbValue)] BYTE pValue[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="275c9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="275c9-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="275c9-106">[in] Początkowe przesunięcie w zmiennej, w którym można ustawić wartości.</span><span class="sxs-lookup"><span data-stu-id="275c9-106">[in] The starting offset in the variable at which to set the value.</span></span> <span data-ttu-id="275c9-107">Ten parametr jest używany podczas zapisywania do elementu członkowskiego pola obiektu.</span><span class="sxs-lookup"><span data-stu-id="275c9-107">This parameter is used when writing to member fields in an object.</span></span>  
  
 `threadID`  
 <span data-ttu-id="275c9-108">[in] Identyfikator wątku wątku, którego kontekst muszą zostać zaktualizowane w celu uwzględnienia nowej wartości.</span><span class="sxs-lookup"><span data-stu-id="275c9-108">[in] The thread identifier of the thread whose context must be updated to reflect the new value.</span></span>  
  
 `cbContext`  
 <span data-ttu-id="275c9-109">[in] Rozmiar w bajtach kontekst wątku.</span><span class="sxs-lookup"><span data-stu-id="275c9-109">[in] The size in bytes of the thread context.</span></span>  
  
 `context`  
 <span data-ttu-id="275c9-110">[in] Kontekst wątku używany do zapisu wartości.</span><span class="sxs-lookup"><span data-stu-id="275c9-110">[in] The thread context used to write the value.</span></span>  
  
 `cbValue`  
 <span data-ttu-id="275c9-111">[in] Wyrażony w bajtach rozmiar `pValue` buforu.</span><span class="sxs-lookup"><span data-stu-id="275c9-111">[in] The size in bytes of the `pValue` buffer.</span></span>  
  
 `pValue`  
 <span data-ttu-id="275c9-112">[in] Buforu, który zawiera wartość do ustawienia.</span><span class="sxs-lookup"><span data-stu-id="275c9-112">[in] The buffer that contains the value to set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="275c9-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="275c9-113">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="275c9-114">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="275c9-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="275c9-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="275c9-115">Requirements</span></span>  
 <span data-ttu-id="275c9-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="275c9-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="275c9-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="275c9-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="275c9-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="275c9-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="275c9-119">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="275c9-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="275c9-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="275c9-120">See Also</span></span>  
 [<span data-ttu-id="275c9-121">Interfejs ICorDebugVariableSymbol</span><span class="sxs-lookup"><span data-stu-id="275c9-121">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [<span data-ttu-id="275c9-122">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="275c9-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

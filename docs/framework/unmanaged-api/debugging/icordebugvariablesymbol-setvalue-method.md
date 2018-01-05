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
ms.workload: dotnet
ms.openlocfilehash: 2433274c2b8fa3ac547696c03a0d0e25c8b63082
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvariablesymbolsetvalue-method"></a><span data-ttu-id="da4b6-102">ICorDebugVariableSymbol::SetValue — metoda</span><span class="sxs-lookup"><span data-stu-id="da4b6-102">ICorDebugVariableSymbol::SetValue Method</span></span>
<span data-ttu-id="da4b6-103">Przypisuje wartość tablica bajtów do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="da4b6-103">Assigns the value of a byte array to a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="da4b6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="da4b6-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="da4b6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="da4b6-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="da4b6-106">[in] Początkowe przesunięcie w zmiennej, w którym można ustawić wartości.</span><span class="sxs-lookup"><span data-stu-id="da4b6-106">[in] The starting offset in the variable at which to set the value.</span></span> <span data-ttu-id="da4b6-107">Ten parametr jest używany podczas zapisywania do elementu członkowskiego pola obiektu.</span><span class="sxs-lookup"><span data-stu-id="da4b6-107">This parameter is used when writing to member fields in an object.</span></span>  
  
 `threadID`  
 <span data-ttu-id="da4b6-108">[in] Identyfikator wątku wątku, którego kontekst muszą zostać zaktualizowane w celu uwzględnienia nowej wartości.</span><span class="sxs-lookup"><span data-stu-id="da4b6-108">[in] The thread identifier of the thread whose context must be updated to reflect the new value.</span></span>  
  
 `cbContext`  
 <span data-ttu-id="da4b6-109">[in] Rozmiar w bajtach kontekst wątku.</span><span class="sxs-lookup"><span data-stu-id="da4b6-109">[in] The size in bytes of the thread context.</span></span>  
  
 `context`  
 <span data-ttu-id="da4b6-110">[in] Kontekst wątku używany do zapisu wartości.</span><span class="sxs-lookup"><span data-stu-id="da4b6-110">[in] The thread context used to write the value.</span></span>  
  
 `cbValue`  
 <span data-ttu-id="da4b6-111">[in] Wyrażony w bajtach rozmiar `pValue` buforu.</span><span class="sxs-lookup"><span data-stu-id="da4b6-111">[in] The size in bytes of the `pValue` buffer.</span></span>  
  
 `pValue`  
 <span data-ttu-id="da4b6-112">[in] Buforu, który zawiera wartość do ustawienia.</span><span class="sxs-lookup"><span data-stu-id="da4b6-112">[in] The buffer that contains the value to set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="da4b6-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="da4b6-113">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="da4b6-114">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="da4b6-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="da4b6-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="da4b6-115">Requirements</span></span>  
 <span data-ttu-id="da4b6-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="da4b6-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="da4b6-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="da4b6-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="da4b6-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="da4b6-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="da4b6-119">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="da4b6-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="da4b6-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="da4b6-120">See Also</span></span>  
 [<span data-ttu-id="da4b6-121">ICorDebugVariableSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="da4b6-121">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [<span data-ttu-id="da4b6-122">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="da4b6-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

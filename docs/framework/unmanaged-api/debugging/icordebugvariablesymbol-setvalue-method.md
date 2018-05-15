---
title: ICorDebugVariableSymbol::SetValue — metoda
ms.date: 03/30/2017
ms.assetid: 4609418d-71fa-44bc-9618-4d529d25cabb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1ccdb78e522cb037821135c52bf762707f7de76c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugvariablesymbolsetvalue-method"></a><span data-ttu-id="51b54-102">ICorDebugVariableSymbol::SetValue — metoda</span><span class="sxs-lookup"><span data-stu-id="51b54-102">ICorDebugVariableSymbol::SetValue Method</span></span>
<span data-ttu-id="51b54-103">Przypisuje wartość tablica bajtów do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="51b54-103">Assigns the value of a byte array to a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51b54-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="51b54-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="51b54-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="51b54-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="51b54-106">[in] Początkowe przesunięcie w zmiennej, w którym można ustawić wartości.</span><span class="sxs-lookup"><span data-stu-id="51b54-106">[in] The starting offset in the variable at which to set the value.</span></span> <span data-ttu-id="51b54-107">Ten parametr jest używany podczas zapisywania do elementu członkowskiego pola obiektu.</span><span class="sxs-lookup"><span data-stu-id="51b54-107">This parameter is used when writing to member fields in an object.</span></span>  
  
 `threadID`  
 <span data-ttu-id="51b54-108">[in] Identyfikator wątku wątku, którego kontekst muszą zostać zaktualizowane w celu uwzględnienia nowej wartości.</span><span class="sxs-lookup"><span data-stu-id="51b54-108">[in] The thread identifier of the thread whose context must be updated to reflect the new value.</span></span>  
  
 `cbContext`  
 <span data-ttu-id="51b54-109">[in] Rozmiar w bajtach kontekst wątku.</span><span class="sxs-lookup"><span data-stu-id="51b54-109">[in] The size in bytes of the thread context.</span></span>  
  
 `context`  
 <span data-ttu-id="51b54-110">[in] Kontekst wątku używany do zapisu wartości.</span><span class="sxs-lookup"><span data-stu-id="51b54-110">[in] The thread context used to write the value.</span></span>  
  
 `cbValue`  
 <span data-ttu-id="51b54-111">[in] Wyrażony w bajtach rozmiar `pValue` buforu.</span><span class="sxs-lookup"><span data-stu-id="51b54-111">[in] The size in bytes of the `pValue` buffer.</span></span>  
  
 `pValue`  
 <span data-ttu-id="51b54-112">[in] Buforu, który zawiera wartość do ustawienia.</span><span class="sxs-lookup"><span data-stu-id="51b54-112">[in] The buffer that contains the value to set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="51b54-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="51b54-113">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="51b54-114">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="51b54-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51b54-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="51b54-115">Requirements</span></span>  
 <span data-ttu-id="51b54-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51b54-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51b54-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="51b54-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="51b54-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="51b54-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="51b54-119">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51b54-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51b54-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="51b54-120">See Also</span></span>  
 [<span data-ttu-id="51b54-121">ICorDebugVariableSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="51b54-121">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [<span data-ttu-id="51b54-122">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="51b54-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

---
title: ICorDebugVariableSymbol::SetValue Method
ms.date: 03/30/2017
ms.assetid: 4609418d-71fa-44bc-9618-4d529d25cabb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 427c885dc1d7cbf535656a7db3f40da28c55a9b2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54630775"
---
# <a name="icordebugvariablesymbolsetvalue-method"></a><span data-ttu-id="df473-102">ICorDebugVariableSymbol::SetValue Method</span><span class="sxs-lookup"><span data-stu-id="df473-102">ICorDebugVariableSymbol::SetValue Method</span></span>
<span data-ttu-id="df473-103">Wartość tablicy bajtowej jest przypisywany do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="df473-103">Assigns the value of a byte array to a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df473-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="df473-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="df473-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="df473-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="df473-106">[in] Początkowe przesunięcie w zmiennej, w którym można ustawić wartości.</span><span class="sxs-lookup"><span data-stu-id="df473-106">[in] The starting offset in the variable at which to set the value.</span></span> <span data-ttu-id="df473-107">Ten parametr jest używany podczas zapisywania do pola elementu członkowskiego w obiekcie.</span><span class="sxs-lookup"><span data-stu-id="df473-107">This parameter is used when writing to member fields in an object.</span></span>  
  
 `threadID`  
 <span data-ttu-id="df473-108">[in] Identyfikator wątku wątku, którego kontekst muszą zostać zaktualizowane w celu odzwierciedlenia nowej wartości.</span><span class="sxs-lookup"><span data-stu-id="df473-108">[in] The thread identifier of the thread whose context must be updated to reflect the new value.</span></span>  
  
 `cbContext`  
 <span data-ttu-id="df473-109">[in] Rozmiar w bajtach kontekst wątku.</span><span class="sxs-lookup"><span data-stu-id="df473-109">[in] The size in bytes of the thread context.</span></span>  
  
 `context`  
 <span data-ttu-id="df473-110">[in] Kontekst wątku, używany do zapisywania wartości.</span><span class="sxs-lookup"><span data-stu-id="df473-110">[in] The thread context used to write the value.</span></span>  
  
 `cbValue`  
 <span data-ttu-id="df473-111">[in] Rozmiar w bajtach `pValue` buforu.</span><span class="sxs-lookup"><span data-stu-id="df473-111">[in] The size in bytes of the `pValue` buffer.</span></span>  
  
 `pValue`  
 <span data-ttu-id="df473-112">[in] Bufor, który zawiera wartość do ustawienia.</span><span class="sxs-lookup"><span data-stu-id="df473-112">[in] The buffer that contains the value to set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="df473-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="df473-113">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="df473-114">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="df473-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df473-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="df473-115">Requirements</span></span>  
 <span data-ttu-id="df473-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df473-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df473-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="df473-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="df473-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="df473-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="df473-119">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df473-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df473-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="df473-120">See also</span></span>
- [<span data-ttu-id="df473-121">ICorDebugVariableSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="df473-121">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="df473-122">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="df473-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

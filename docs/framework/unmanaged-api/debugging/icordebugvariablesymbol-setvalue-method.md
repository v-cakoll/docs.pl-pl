---
title: ICorDebugVariableSymbol::SetValue Method
ms.date: 03/30/2017
ms.assetid: 4609418d-71fa-44bc-9618-4d529d25cabb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c5c1c77b92d94062206cf9eb38981f38ff2a1cad
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67775452"
---
# <a name="icordebugvariablesymbolsetvalue-method"></a><span data-ttu-id="3d7c0-102">ICorDebugVariableSymbol::SetValue Method</span><span class="sxs-lookup"><span data-stu-id="3d7c0-102">ICorDebugVariableSymbol::SetValue Method</span></span>
<span data-ttu-id="3d7c0-103">Wartość tablicy bajtowej jest przypisywany do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="3d7c0-103">Assigns the value of a byte array to a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d7c0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3d7c0-104">Syntax</span></span>  
  
```cpp  
HRESULT SetValue(  
   [in] ULONG32 offset,  
   [in] DWORD threadID,  
   [in] ULONG32 cbContext,  
   [in, size_is(cbContext)] BYTE context[],  
   [in] ULONG32 cbValue,  
   [in, size_is(cbValue)] BYTE pValue[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3d7c0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3d7c0-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="3d7c0-106">[in] Początkowe przesunięcie w zmiennej, w którym można ustawić wartości.</span><span class="sxs-lookup"><span data-stu-id="3d7c0-106">[in] The starting offset in the variable at which to set the value.</span></span> <span data-ttu-id="3d7c0-107">Ten parametr jest używany podczas zapisywania do pola elementu członkowskiego w obiekcie.</span><span class="sxs-lookup"><span data-stu-id="3d7c0-107">This parameter is used when writing to member fields in an object.</span></span>  
  
 `threadID`  
 <span data-ttu-id="3d7c0-108">[in] Identyfikator wątku wątku, którego kontekst muszą zostać zaktualizowane w celu odzwierciedlenia nowej wartości.</span><span class="sxs-lookup"><span data-stu-id="3d7c0-108">[in] The thread identifier of the thread whose context must be updated to reflect the new value.</span></span>  
  
 `cbContext`  
 <span data-ttu-id="3d7c0-109">[in] Rozmiar w bajtach kontekst wątku.</span><span class="sxs-lookup"><span data-stu-id="3d7c0-109">[in] The size in bytes of the thread context.</span></span>  
  
 `context`  
 <span data-ttu-id="3d7c0-110">[in] Kontekst wątku, używany do zapisywania wartości.</span><span class="sxs-lookup"><span data-stu-id="3d7c0-110">[in] The thread context used to write the value.</span></span>  
  
 `cbValue`  
 <span data-ttu-id="3d7c0-111">[in] Rozmiar w bajtach `pValue` buforu.</span><span class="sxs-lookup"><span data-stu-id="3d7c0-111">[in] The size in bytes of the `pValue` buffer.</span></span>  
  
 `pValue`  
 <span data-ttu-id="3d7c0-112">[in] Bufor, który zawiera wartość do ustawienia.</span><span class="sxs-lookup"><span data-stu-id="3d7c0-112">[in] The buffer that contains the value to set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3d7c0-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3d7c0-113">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3d7c0-114">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="3d7c0-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3d7c0-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3d7c0-115">Requirements</span></span>  
 <span data-ttu-id="3d7c0-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d7c0-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d7c0-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3d7c0-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3d7c0-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3d7c0-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3d7c0-119">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d7c0-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d7c0-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3d7c0-120">See also</span></span>

- [<span data-ttu-id="3d7c0-121">ICorDebugVariableSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="3d7c0-121">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="3d7c0-122">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="3d7c0-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

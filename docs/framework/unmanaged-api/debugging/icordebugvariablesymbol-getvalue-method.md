---
title: Metoda ICorDebugVariableSymbol::GetValue
ms.date: 03/30/2017
ms.assetid: 90abece1-392e-4ade-94a1-30c75b0f7074
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ed88c8ff78006c14bdee51ba6f95aaaedd66cf41
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774831"
---
# <a name="icordebugvariablesymbolgetvalue-method"></a><span data-ttu-id="393a2-102">Metoda ICorDebugVariableSymbol::GetValue</span><span class="sxs-lookup"><span data-stu-id="393a2-102">ICorDebugVariableSymbol::GetValue Method</span></span>
<span data-ttu-id="393a2-103">Pobiera wartość zmiennej w postaci tablicy bajtów.</span><span class="sxs-lookup"><span data-stu-id="393a2-103">Gets the value of a variable as a byte array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="393a2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="393a2-104">Syntax</span></span>  
  
```cpp  
HRESULT GetValue(  
   [in] ULONG32 offset,  
   [in] ULONG32 cbContext,  
   [in, size_is(cbContext)] BYTE context[],  
   [in] ULONG32 cbValue,  
   [out] ULONG32 *pcbValue,  
   [out, size_is(cbValue), length_is(*pcbValue)] BYTE pValue[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="393a2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="393a2-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="393a2-106">[in] Początkowe przesunięcie w zmiennej, z którego ma zostać odczytana wartość.</span><span class="sxs-lookup"><span data-stu-id="393a2-106">[in] The starting offset in the variable from which to read the value.</span></span> <span data-ttu-id="393a2-107">Ten parametr jest używany podczas odczytywania pola elementu członkowskiego w obiekcie.</span><span class="sxs-lookup"><span data-stu-id="393a2-107">This parameter is used when reading member fields in an object.</span></span>  
  
 `cbContext`  
 <span data-ttu-id="393a2-108">[in] Rozmiar w bajtach `context` argumentu.</span><span class="sxs-lookup"><span data-stu-id="393a2-108">[in] The size in bytes of the `context` argument.</span></span>  
  
 `context`  
 <span data-ttu-id="393a2-109">[in] Kontekst wątku, używane do odczytywania wartości.</span><span class="sxs-lookup"><span data-stu-id="393a2-109">[in] The thread context used to read the value.</span></span>  
  
 `cbValue`  
 <span data-ttu-id="393a2-110">[in] Rozmiar w bajtach `pValue` buforu.</span><span class="sxs-lookup"><span data-stu-id="393a2-110">[in] The size in bytes of the `pValue` buffer.</span></span>  
  
 `pcbValue`  
 <span data-ttu-id="393a2-111">[out] Liczba bajtów rzeczywiście zapisanych na `pValue` buforu.</span><span class="sxs-lookup"><span data-stu-id="393a2-111">[out] The number of bytes actually written to the `pValue` buffer.</span></span>  
  
 `pValue`  
 <span data-ttu-id="393a2-112">[out] Tablica bajtów, która zawiera wartość zmiennej.</span><span class="sxs-lookup"><span data-stu-id="393a2-112">[out] A byte array that contains the value of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="393a2-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="393a2-113">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="393a2-114">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="393a2-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="393a2-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="393a2-115">Requirements</span></span>  
 <span data-ttu-id="393a2-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="393a2-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="393a2-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="393a2-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="393a2-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="393a2-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="393a2-119">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="393a2-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="393a2-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="393a2-120">See also</span></span>

- [<span data-ttu-id="393a2-121">ICorDebugVariableSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="393a2-121">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="393a2-122">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="393a2-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

---
title: Metoda ICorDebugVariableSymbol::GetValue
ms.date: 03/30/2017
ms.assetid: 90abece1-392e-4ade-94a1-30c75b0f7074
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 186d9eec0aa6ad9e327b1dd4d0f19e251c79ecf9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59147280"
---
# <a name="icordebugvariablesymbolgetvalue-method"></a><span data-ttu-id="8d32e-102">Metoda ICorDebugVariableSymbol::GetValue</span><span class="sxs-lookup"><span data-stu-id="8d32e-102">ICorDebugVariableSymbol::GetValue Method</span></span>
<span data-ttu-id="8d32e-103">Pobiera wartość zmiennej w postaci tablicy bajtów.</span><span class="sxs-lookup"><span data-stu-id="8d32e-103">Gets the value of a variable as a byte array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d32e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8d32e-104">Syntax</span></span>  
  
```  
HRESULT GetValue(  
   [in] ULONG32 offset,  
   [in] ULONG32 cbContext,  
   [in, size_is(cbContext)] BYTE context[],  
   [in] ULONG32 cbValue,  
   [out] ULONG32 *pcbValue,  
   [out, size_is(cbValue), length_is(*pcbValue)] BYTE pValue[]  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8d32e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8d32e-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="8d32e-106">[in] Początkowe przesunięcie w zmiennej, z którego ma zostać odczytana wartość.</span><span class="sxs-lookup"><span data-stu-id="8d32e-106">[in] The starting offset in the variable from which to read the value.</span></span> <span data-ttu-id="8d32e-107">Ten parametr jest używany podczas odczytywania pola elementu członkowskiego w obiekcie.</span><span class="sxs-lookup"><span data-stu-id="8d32e-107">This parameter is used when reading member fields in an object.</span></span>  
  
 `cbContext`  
 <span data-ttu-id="8d32e-108">[in] Rozmiar w bajtach `context` argumentu.</span><span class="sxs-lookup"><span data-stu-id="8d32e-108">[in] The size in bytes of the `context` argument.</span></span>  
  
 `context`  
 <span data-ttu-id="8d32e-109">[in] Kontekst wątku, używane do odczytywania wartości.</span><span class="sxs-lookup"><span data-stu-id="8d32e-109">[in] The thread context used to read the value.</span></span>  
  
 `cbValue`  
 <span data-ttu-id="8d32e-110">[in] Rozmiar w bajtach `pValue` buforu.</span><span class="sxs-lookup"><span data-stu-id="8d32e-110">[in] The size in bytes of the `pValue` buffer.</span></span>  
  
 `pcbValue`  
 <span data-ttu-id="8d32e-111">[out] Liczba bajtów rzeczywiście zapisanych na `pValue` buforu.</span><span class="sxs-lookup"><span data-stu-id="8d32e-111">[out] The number of bytes actually written to the `pValue` buffer.</span></span>  
  
 `pValue`  
 <span data-ttu-id="8d32e-112">[out] Tablica bajtów, która zawiera wartość zmiennej.</span><span class="sxs-lookup"><span data-stu-id="8d32e-112">[out] A byte array that contains the value of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8d32e-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8d32e-113">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8d32e-114">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="8d32e-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d32e-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8d32e-115">Requirements</span></span>  
 <span data-ttu-id="8d32e-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d32e-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d32e-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8d32e-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8d32e-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8d32e-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8d32e-119">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d32e-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d32e-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8d32e-120">See also</span></span>

- [<span data-ttu-id="8d32e-121">ICorDebugVariableSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="8d32e-121">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="8d32e-122">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="8d32e-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

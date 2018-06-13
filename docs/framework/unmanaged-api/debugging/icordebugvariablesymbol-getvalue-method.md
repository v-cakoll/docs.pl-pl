---
title: ICorDebugVariableSymbol::GetValue — metoda
ms.date: 03/30/2017
ms.assetid: 90abece1-392e-4ade-94a1-30c75b0f7074
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5916b1bd89c4f86d76ef4b61afa211b76be94928
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33422750"
---
# <a name="icordebugvariablesymbolgetvalue-method"></a><span data-ttu-id="488f7-102">ICorDebugVariableSymbol::GetValue — metoda</span><span class="sxs-lookup"><span data-stu-id="488f7-102">ICorDebugVariableSymbol::GetValue Method</span></span>
<span data-ttu-id="488f7-103">Pobiera wartość zmiennej w postaci tablicy bajtów.</span><span class="sxs-lookup"><span data-stu-id="488f7-103">Gets the value of a variable as a byte array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="488f7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="488f7-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="488f7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="488f7-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="488f7-106">[in] Początkowe przesunięcie w zmiennej, z którego można odczytać wartości.</span><span class="sxs-lookup"><span data-stu-id="488f7-106">[in] The starting offset in the variable from which to read the value.</span></span> <span data-ttu-id="488f7-107">Ten parametr jest używany podczas odczytywania elementu członkowskiego pola obiektu.</span><span class="sxs-lookup"><span data-stu-id="488f7-107">This parameter is used when reading member fields in an object.</span></span>  
  
 `cbContext`  
 <span data-ttu-id="488f7-108">[in] Wyrażony w bajtach rozmiar `context` argumentu.</span><span class="sxs-lookup"><span data-stu-id="488f7-108">[in] The size in bytes of the `context` argument.</span></span>  
  
 `context`  
 <span data-ttu-id="488f7-109">[in] Kontekst wątku używany do odczytu wartości.</span><span class="sxs-lookup"><span data-stu-id="488f7-109">[in] The thread context used to read the value.</span></span>  
  
 `cbValue`  
 <span data-ttu-id="488f7-110">[in] Wyrażony w bajtach rozmiar `pValue` buforu.</span><span class="sxs-lookup"><span data-stu-id="488f7-110">[in] The size in bytes of the `pValue` buffer.</span></span>  
  
 `pcbValue`  
 <span data-ttu-id="488f7-111">[out] Liczba bajtów zapisywanych faktycznie `pValue` buforu.</span><span class="sxs-lookup"><span data-stu-id="488f7-111">[out] The number of bytes actually written to the `pValue` buffer.</span></span>  
  
 `pValue`  
 <span data-ttu-id="488f7-112">[out] Tablica bajtów zawierająca wartość zmiennej.</span><span class="sxs-lookup"><span data-stu-id="488f7-112">[out] A byte array that contains the value of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="488f7-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="488f7-113">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="488f7-114">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="488f7-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="488f7-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="488f7-115">Requirements</span></span>  
 <span data-ttu-id="488f7-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="488f7-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="488f7-117">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="488f7-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="488f7-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="488f7-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="488f7-119">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="488f7-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="488f7-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="488f7-120">See Also</span></span>  
 [<span data-ttu-id="488f7-121">ICorDebugVariableSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="488f7-121">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [<span data-ttu-id="488f7-122">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="488f7-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

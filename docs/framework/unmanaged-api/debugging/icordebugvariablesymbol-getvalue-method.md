---
title: 'ICorDebugVariableSymbol:: GetValue — Metoda'
ms.date: 03/30/2017
ms.assetid: 90abece1-392e-4ade-94a1-30c75b0f7074
ms.openlocfilehash: f217f7226d53a27363f66eb90a340fd3604a0217
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396515"
---
# <a name="icordebugvariablesymbolgetvalue-method"></a><span data-ttu-id="331b8-102">ICorDebugVariableSymbol:: GetValue — Metoda</span><span class="sxs-lookup"><span data-stu-id="331b8-102">ICorDebugVariableSymbol::GetValue Method</span></span>
<span data-ttu-id="331b8-103">Pobiera wartość zmiennej jako tablicę bajtów.</span><span class="sxs-lookup"><span data-stu-id="331b8-103">Gets the value of a variable as a byte array.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="331b8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="331b8-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="331b8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="331b8-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="331b8-106">podczas Przesunięcie początkowe w zmiennej, z której ma zostać odczytana wartość.</span><span class="sxs-lookup"><span data-stu-id="331b8-106">[in] The starting offset in the variable from which to read the value.</span></span> <span data-ttu-id="331b8-107">Ten parametr jest używany podczas odczytywania pól elementu członkowskiego w obiekcie.</span><span class="sxs-lookup"><span data-stu-id="331b8-107">This parameter is used when reading member fields in an object.</span></span>  
  
 `cbContext`  
 <span data-ttu-id="331b8-108">podczas Rozmiar w bajtach `context` argumentu.</span><span class="sxs-lookup"><span data-stu-id="331b8-108">[in] The size in bytes of the `context` argument.</span></span>  
  
 `context`  
 <span data-ttu-id="331b8-109">podczas Kontekst wątku używany do odczytywania wartości.</span><span class="sxs-lookup"><span data-stu-id="331b8-109">[in] The thread context used to read the value.</span></span>  
  
 `cbValue`  
 <span data-ttu-id="331b8-110">podczas Rozmiar w bajtach `pValue` buforu.</span><span class="sxs-lookup"><span data-stu-id="331b8-110">[in] The size in bytes of the `pValue` buffer.</span></span>  
  
 `pcbValue`  
 <span data-ttu-id="331b8-111">określoną Liczba bajtów rzeczywiście zapisywana w `pValue` buforze.</span><span class="sxs-lookup"><span data-stu-id="331b8-111">[out] The number of bytes actually written to the `pValue` buffer.</span></span>  
  
 `pValue`  
 <span data-ttu-id="331b8-112">określoną Tablica bajtów, która zawiera wartość zmiennej.</span><span class="sxs-lookup"><span data-stu-id="331b8-112">[out] A byte array that contains the value of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="331b8-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="331b8-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="331b8-114">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="331b8-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="331b8-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="331b8-115">Requirements</span></span>  
 <span data-ttu-id="331b8-116">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="331b8-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="331b8-117">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="331b8-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="331b8-118">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="331b8-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="331b8-119">**.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="331b8-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="331b8-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="331b8-120">See also</span></span>

- [<span data-ttu-id="331b8-121">ICorDebugVariableSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="331b8-121">ICorDebugVariableSymbol Interface</span></span>](icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="331b8-122">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="331b8-122">Debugging Interfaces</span></span>](debugging-interfaces.md)

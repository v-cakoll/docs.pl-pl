---
title: 'ICorDebugVariableSymbol:: SetValue — Metoda'
ms.date: 03/30/2017
ms.assetid: 4609418d-71fa-44bc-9618-4d529d25cabb
ms.openlocfilehash: 38afd355938ec1beb1dbfd33de36116d25b07b4e
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83397078"
---
# <a name="icordebugvariablesymbolsetvalue-method"></a><span data-ttu-id="ecbfd-102">ICorDebugVariableSymbol:: SetValue — Metoda</span><span class="sxs-lookup"><span data-stu-id="ecbfd-102">ICorDebugVariableSymbol::SetValue Method</span></span>
<span data-ttu-id="ecbfd-103">Przypisuje wartość tablicy bajtów do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="ecbfd-103">Assigns the value of a byte array to a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ecbfd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ecbfd-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="ecbfd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ecbfd-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="ecbfd-106">podczas Przesunięcie początkowe w zmiennej, w której ma zostać ustawiona wartość.</span><span class="sxs-lookup"><span data-stu-id="ecbfd-106">[in] The starting offset in the variable at which to set the value.</span></span> <span data-ttu-id="ecbfd-107">Ten parametr jest używany podczas zapisywania do pól elementu członkowskiego w obiekcie.</span><span class="sxs-lookup"><span data-stu-id="ecbfd-107">This parameter is used when writing to member fields in an object.</span></span>  
  
 `threadID`  
 <span data-ttu-id="ecbfd-108">podczas Identyfikator wątku, którego kontekst musi zostać zaktualizowany w celu odzwierciedlenia nowej wartości.</span><span class="sxs-lookup"><span data-stu-id="ecbfd-108">[in] The thread identifier of the thread whose context must be updated to reflect the new value.</span></span>  
  
 `cbContext`  
 <span data-ttu-id="ecbfd-109">podczas Rozmiar w bajtach kontekstu wątku.</span><span class="sxs-lookup"><span data-stu-id="ecbfd-109">[in] The size in bytes of the thread context.</span></span>  
  
 `context`  
 <span data-ttu-id="ecbfd-110">podczas Kontekst wątku używany do zapisania wartości.</span><span class="sxs-lookup"><span data-stu-id="ecbfd-110">[in] The thread context used to write the value.</span></span>  
  
 `cbValue`  
 <span data-ttu-id="ecbfd-111">podczas Rozmiar w bajtach `pValue` buforu.</span><span class="sxs-lookup"><span data-stu-id="ecbfd-111">[in] The size in bytes of the `pValue` buffer.</span></span>  
  
 `pValue`  
 <span data-ttu-id="ecbfd-112">podczas Bufor, który zawiera wartość do ustawienia.</span><span class="sxs-lookup"><span data-stu-id="ecbfd-112">[in] The buffer that contains the value to set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ecbfd-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ecbfd-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="ecbfd-114">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ecbfd-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ecbfd-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ecbfd-115">Requirements</span></span>  
 <span data-ttu-id="ecbfd-116">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ecbfd-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ecbfd-117">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ecbfd-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ecbfd-118">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ecbfd-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ecbfd-119">**.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ecbfd-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ecbfd-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ecbfd-120">See also</span></span>

- [<span data-ttu-id="ecbfd-121">ICorDebugVariableSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="ecbfd-121">ICorDebugVariableSymbol Interface</span></span>](icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="ecbfd-122">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="ecbfd-122">Debugging Interfaces</span></span>](debugging-interfaces.md)

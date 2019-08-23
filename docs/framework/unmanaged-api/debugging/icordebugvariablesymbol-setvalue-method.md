---
title: 'ICorDebugVariableSymbol:: SetValue — Metoda'
ms.date: 03/30/2017
ms.assetid: 4609418d-71fa-44bc-9618-4d529d25cabb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5436f56d3dcad7de3df2296485b0a36e5b3cfd79
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967962"
---
# <a name="icordebugvariablesymbolsetvalue-method"></a><span data-ttu-id="93a2c-102">ICorDebugVariableSymbol:: SetValue — Metoda</span><span class="sxs-lookup"><span data-stu-id="93a2c-102">ICorDebugVariableSymbol::SetValue Method</span></span>
<span data-ttu-id="93a2c-103">Przypisuje wartość tablicy bajtów do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="93a2c-103">Assigns the value of a byte array to a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93a2c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="93a2c-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="93a2c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="93a2c-105">Parameters</span></span>  
 `offset`  
 <span data-ttu-id="93a2c-106">podczas Przesunięcie początkowe w zmiennej, w której ma zostać ustawiona wartość.</span><span class="sxs-lookup"><span data-stu-id="93a2c-106">[in] The starting offset in the variable at which to set the value.</span></span> <span data-ttu-id="93a2c-107">Ten parametr jest używany podczas zapisywania do pól elementu członkowskiego w obiekcie.</span><span class="sxs-lookup"><span data-stu-id="93a2c-107">This parameter is used when writing to member fields in an object.</span></span>  
  
 `threadID`  
 <span data-ttu-id="93a2c-108">podczas Identyfikator wątku, którego kontekst musi zostać zaktualizowany w celu odzwierciedlenia nowej wartości.</span><span class="sxs-lookup"><span data-stu-id="93a2c-108">[in] The thread identifier of the thread whose context must be updated to reflect the new value.</span></span>  
  
 `cbContext`  
 <span data-ttu-id="93a2c-109">podczas Rozmiar w bajtach kontekstu wątku.</span><span class="sxs-lookup"><span data-stu-id="93a2c-109">[in] The size in bytes of the thread context.</span></span>  
  
 `context`  
 <span data-ttu-id="93a2c-110">podczas Kontekst wątku używany do zapisania wartości.</span><span class="sxs-lookup"><span data-stu-id="93a2c-110">[in] The thread context used to write the value.</span></span>  
  
 `cbValue`  
 <span data-ttu-id="93a2c-111">podczas Rozmiar w bajtach `pValue` buforu.</span><span class="sxs-lookup"><span data-stu-id="93a2c-111">[in] The size in bytes of the `pValue` buffer.</span></span>  
  
 `pValue`  
 <span data-ttu-id="93a2c-112">podczas Bufor, który zawiera wartość do ustawienia.</span><span class="sxs-lookup"><span data-stu-id="93a2c-112">[in] The buffer that contains the value to set.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="93a2c-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="93a2c-113">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="93a2c-114">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="93a2c-114">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93a2c-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="93a2c-115">Requirements</span></span>  
 <span data-ttu-id="93a2c-116">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93a2c-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93a2c-117">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="93a2c-117">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="93a2c-118">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="93a2c-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="93a2c-119">**.NET Framework wersje:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93a2c-119">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93a2c-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="93a2c-120">See also</span></span>

- [<span data-ttu-id="93a2c-121">ICorDebugVariableSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="93a2c-121">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="93a2c-122">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="93a2c-122">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

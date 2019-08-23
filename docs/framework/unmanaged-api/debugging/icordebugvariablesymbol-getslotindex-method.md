---
title: 'ICorDebugVariableSymbol:: GetSlotIndex, Metoda'
ms.date: 03/30/2017
ms.assetid: 09c19f5f-afc4-4e0c-bffe-cd7147bc7a43
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 58bb2cc63f2336ca9cfbed8ebeac0d607c18b2c4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968157"
---
# <a name="icordebugvariablesymbolgetslotindex-method"></a><span data-ttu-id="fc80a-102">ICorDebugVariableSymbol:: GetSlotIndex, Metoda</span><span class="sxs-lookup"><span data-stu-id="fc80a-102">ICorDebugVariableSymbol::GetSlotIndex Method</span></span>
<span data-ttu-id="fc80a-103">Pobiera indeks gniazda zarządzanego zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="fc80a-103">Gets the managed slot index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fc80a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fc80a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSlotIndex(  
   [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fc80a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="fc80a-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="fc80a-106">określoną Wskaźnik do indeksu gniazda zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="fc80a-106">[out] A pointer to the local variable's slot index.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fc80a-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="fc80a-107">Return Value</span></span>  
 <span data-ttu-id="fc80a-108">`S_OK`w przypadku powodzenia.</span><span class="sxs-lookup"><span data-stu-id="fc80a-108">`S_OK` if successful.</span></span> <span data-ttu-id="fc80a-109">`E_FAIL`Jeśli zmienna jest argumentem funkcji.</span><span class="sxs-lookup"><span data-stu-id="fc80a-109">`E_FAIL` if the variable is a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fc80a-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fc80a-110">Remarks</span></span>  
 <span data-ttu-id="fc80a-111">Do pobrania informacji o metadanych zmiennej można użyć indeksu gniazda zarządzanego zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="fc80a-111">The managed slot index of a local variable can be used to retrieve the variable's metadata information</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fc80a-112">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="fc80a-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fc80a-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fc80a-113">Requirements</span></span>  
 <span data-ttu-id="fc80a-114">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fc80a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fc80a-115">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fc80a-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fc80a-116">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fc80a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fc80a-117">**.NET Framework wersje:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fc80a-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc80a-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fc80a-118">See also</span></span>

- [<span data-ttu-id="fc80a-119">ICorDebugVariableSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="fc80a-119">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="fc80a-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="fc80a-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

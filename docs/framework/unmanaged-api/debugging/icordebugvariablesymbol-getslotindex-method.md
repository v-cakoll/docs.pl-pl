---
title: 'ICorDebugVariableSymbol:: GetSlotIndex, Metoda'
ms.date: 03/30/2017
ms.assetid: 09c19f5f-afc4-4e0c-bffe-cd7147bc7a43
ms.openlocfilehash: a7a7ecf7d3e3d0d2125b03d3604c44138a2be0cc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120972"
---
# <a name="icordebugvariablesymbolgetslotindex-method"></a><span data-ttu-id="81ade-102">ICorDebugVariableSymbol:: GetSlotIndex, Metoda</span><span class="sxs-lookup"><span data-stu-id="81ade-102">ICorDebugVariableSymbol::GetSlotIndex Method</span></span>
<span data-ttu-id="81ade-103">Pobiera indeks gniazda zarządzanego zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="81ade-103">Gets the managed slot index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81ade-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="81ade-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSlotIndex(  
   [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="81ade-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="81ade-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="81ade-106">określoną Wskaźnik do indeksu gniazda zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="81ade-106">[out] A pointer to the local variable's slot index.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="81ade-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="81ade-107">Return Value</span></span>  
 <span data-ttu-id="81ade-108">`S_OK`, jeśli się to powiedzie.</span><span class="sxs-lookup"><span data-stu-id="81ade-108">`S_OK` if successful.</span></span> <span data-ttu-id="81ade-109">`E_FAIL`, jeśli zmienna jest argumentem funkcji.</span><span class="sxs-lookup"><span data-stu-id="81ade-109">`E_FAIL` if the variable is a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81ade-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="81ade-110">Remarks</span></span>  
 <span data-ttu-id="81ade-111">Do pobrania informacji o metadanych zmiennej można użyć indeksu gniazda zarządzanego zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="81ade-111">The managed slot index of a local variable can be used to retrieve the variable's metadata information</span></span>  
  
> [!NOTE]
> <span data-ttu-id="81ade-112">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="81ade-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81ade-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="81ade-113">Requirements</span></span>  
 <span data-ttu-id="81ade-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81ade-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81ade-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="81ade-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="81ade-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="81ade-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="81ade-117">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81ade-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81ade-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="81ade-118">See also</span></span>

- [<span data-ttu-id="81ade-119">ICorDebugVariableSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="81ade-119">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="81ade-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="81ade-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

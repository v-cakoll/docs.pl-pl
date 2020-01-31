---
title: 'ICorDebugVariableSymbol:: GetSlotIndex, Metoda'
ms.date: 03/30/2017
ms.assetid: 09c19f5f-afc4-4e0c-bffe-cd7147bc7a43
ms.openlocfilehash: 3510daffb55bdb22aa5f835bf27157e7c8428509
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790892"
---
# <a name="icordebugvariablesymbolgetslotindex-method"></a><span data-ttu-id="d5982-102">ICorDebugVariableSymbol:: GetSlotIndex, Metoda</span><span class="sxs-lookup"><span data-stu-id="d5982-102">ICorDebugVariableSymbol::GetSlotIndex Method</span></span>
<span data-ttu-id="d5982-103">Pobiera indeks gniazda zarządzanego zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="d5982-103">Gets the managed slot index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5982-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d5982-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSlotIndex(  
   [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d5982-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d5982-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="d5982-106">określoną Wskaźnik do indeksu gniazda zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="d5982-106">[out] A pointer to the local variable's slot index.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="d5982-107">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="d5982-107">Return Value</span></span>  
 <span data-ttu-id="d5982-108">`S_OK`, jeśli się to powiedzie.</span><span class="sxs-lookup"><span data-stu-id="d5982-108">`S_OK` if successful.</span></span> <span data-ttu-id="d5982-109">`E_FAIL`, jeśli zmienna jest argumentem funkcji.</span><span class="sxs-lookup"><span data-stu-id="d5982-109">`E_FAIL` if the variable is a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5982-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d5982-110">Remarks</span></span>  
 <span data-ttu-id="d5982-111">Do pobrania informacji o metadanych zmiennej można użyć indeksu gniazda zarządzanego zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="d5982-111">The managed slot index of a local variable can be used to retrieve the variable's metadata information</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d5982-112">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="d5982-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5982-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d5982-113">Requirements</span></span>  
 <span data-ttu-id="d5982-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d5982-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d5982-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d5982-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d5982-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d5982-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d5982-117">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d5982-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d5982-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d5982-118">See also</span></span>

- [<span data-ttu-id="d5982-119">ICorDebugVariableSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="d5982-119">ICorDebugVariableSymbol Interface</span></span>](icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="d5982-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="d5982-120">Debugging Interfaces</span></span>](debugging-interfaces.md)

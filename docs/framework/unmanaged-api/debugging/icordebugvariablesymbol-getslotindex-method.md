---
title: Metoda ICorDebugVariableSymbol::GetSlotIndex
ms.date: 03/30/2017
ms.assetid: 09c19f5f-afc4-4e0c-bffe-cd7147bc7a43
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 84d9e30a2baf08f6b7ff530f2fce049d49386a60
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67774843"
---
# <a name="icordebugvariablesymbolgetslotindex-method"></a><span data-ttu-id="0eb7b-102">Metoda ICorDebugVariableSymbol::GetSlotIndex</span><span class="sxs-lookup"><span data-stu-id="0eb7b-102">ICorDebugVariableSymbol::GetSlotIndex Method</span></span>
<span data-ttu-id="0eb7b-103">Pobiera indeks zarządzane miejsce zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="0eb7b-103">Gets the managed slot index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0eb7b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0eb7b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSlotIndex(  
   [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0eb7b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0eb7b-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="0eb7b-106">[out] Wskaźnik do zmiennej lokalnej miejsca indeksu.</span><span class="sxs-lookup"><span data-stu-id="0eb7b-106">[out] A pointer to the local variable's slot index.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0eb7b-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="0eb7b-107">Return Value</span></span>  
 <span data-ttu-id="0eb7b-108">`S_OK` Jeśli to się powiedzie.</span><span class="sxs-lookup"><span data-stu-id="0eb7b-108">`S_OK` if successful.</span></span> <span data-ttu-id="0eb7b-109">`E_FAIL` Jeśli zmienna jest argumentu funkcji.</span><span class="sxs-lookup"><span data-stu-id="0eb7b-109">`E_FAIL` if the variable is a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0eb7b-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0eb7b-110">Remarks</span></span>  
 <span data-ttu-id="0eb7b-111">Indeks gniazda zarządzanych zmienna lokalna może służyć do pobierania informacji o metadanych zmiennej</span><span class="sxs-lookup"><span data-stu-id="0eb7b-111">The managed slot index of a local variable can be used to retrieve the variable's metadata information</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0eb7b-112">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="0eb7b-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0eb7b-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0eb7b-113">Requirements</span></span>  
 <span data-ttu-id="0eb7b-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0eb7b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0eb7b-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0eb7b-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0eb7b-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0eb7b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0eb7b-117">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0eb7b-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0eb7b-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0eb7b-118">See also</span></span>

- [<span data-ttu-id="0eb7b-119">ICorDebugVariableSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="0eb7b-119">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="0eb7b-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="0eb7b-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

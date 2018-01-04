---
title: "ICorDebugVariableSymbol::GetSlotIndex — metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 09c19f5f-afc4-4e0c-bffe-cd7147bc7a43
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: abb84e529768e0be44883511bb89703a4c3199df
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvariablesymbolgetslotindex-method"></a><span data-ttu-id="181e5-102">ICorDebugVariableSymbol::GetSlotIndex — metoda</span><span class="sxs-lookup"><span data-stu-id="181e5-102">ICorDebugVariableSymbol::GetSlotIndex Method</span></span>
<span data-ttu-id="181e5-103">Pobiera indeks gniazda zarządzanych zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="181e5-103">Gets the managed slot index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="181e5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="181e5-104">Syntax</span></span>  
  
```  
HRESULT GetSlotIndex(  
   [out] ULONG32 *pSlotIndex  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="181e5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="181e5-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="181e5-106">[out] Wskaźnik do zmiennej lokalnej miejsca indeksu.</span><span class="sxs-lookup"><span data-stu-id="181e5-106">[out] A pointer to the local variable's slot index.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="181e5-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="181e5-107">Return Value</span></span>  
 <span data-ttu-id="181e5-108">`S_OK`w przypadku powodzenia.</span><span class="sxs-lookup"><span data-stu-id="181e5-108">`S_OK` if successful.</span></span> <span data-ttu-id="181e5-109">`E_FAIL`Jeśli zmienna jest argumentu funkcji.</span><span class="sxs-lookup"><span data-stu-id="181e5-109">`E_FAIL` if the variable is a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="181e5-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="181e5-110">Remarks</span></span>  
 <span data-ttu-id="181e5-111">Indeks gniazda zarządzanych zmiennej lokalnej może służyć do pobierania informacji o metadanych zmiennej</span><span class="sxs-lookup"><span data-stu-id="181e5-111">The managed slot index of a local variable can be used to retrieve the variable's metadata information</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="181e5-112">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="181e5-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="181e5-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="181e5-113">Requirements</span></span>  
 <span data-ttu-id="181e5-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="181e5-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="181e5-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="181e5-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="181e5-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="181e5-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="181e5-117">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="181e5-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="181e5-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="181e5-118">See Also</span></span>  
 [<span data-ttu-id="181e5-119">ICorDebugVariableSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="181e5-119">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [<span data-ttu-id="181e5-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="181e5-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

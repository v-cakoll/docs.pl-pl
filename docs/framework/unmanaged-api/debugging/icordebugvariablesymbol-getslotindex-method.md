---
title: ICorDebugVariableSymbol::GetSlotIndex — metoda
ms.date: 03/30/2017
ms.assetid: 09c19f5f-afc4-4e0c-bffe-cd7147bc7a43
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1657ed4d8326b573fe081b98c1fc414e231ac465
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420625"
---
# <a name="icordebugvariablesymbolgetslotindex-method"></a><span data-ttu-id="9defd-102">ICorDebugVariableSymbol::GetSlotIndex — metoda</span><span class="sxs-lookup"><span data-stu-id="9defd-102">ICorDebugVariableSymbol::GetSlotIndex Method</span></span>
<span data-ttu-id="9defd-103">Pobiera indeks gniazda zarządzanych zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="9defd-103">Gets the managed slot index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9defd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9defd-104">Syntax</span></span>  
  
```  
HRESULT GetSlotIndex(  
   [out] ULONG32 *pSlotIndex  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9defd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9defd-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="9defd-106">[out] Wskaźnik do zmiennej lokalnej miejsca indeksu.</span><span class="sxs-lookup"><span data-stu-id="9defd-106">[out] A pointer to the local variable's slot index.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9defd-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="9defd-107">Return Value</span></span>  
 <span data-ttu-id="9defd-108">`S_OK` w przypadku powodzenia.</span><span class="sxs-lookup"><span data-stu-id="9defd-108">`S_OK` if successful.</span></span> <span data-ttu-id="9defd-109">`E_FAIL` Jeśli zmienna jest argumentu funkcji.</span><span class="sxs-lookup"><span data-stu-id="9defd-109">`E_FAIL` if the variable is a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9defd-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9defd-110">Remarks</span></span>  
 <span data-ttu-id="9defd-111">Indeks gniazda zarządzanych zmiennej lokalnej może służyć do pobierania informacji o metadanych zmiennej</span><span class="sxs-lookup"><span data-stu-id="9defd-111">The managed slot index of a local variable can be used to retrieve the variable's metadata information</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9defd-112">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="9defd-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9defd-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9defd-113">Requirements</span></span>  
 <span data-ttu-id="9defd-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9defd-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9defd-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9defd-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9defd-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9defd-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9defd-117">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9defd-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9defd-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9defd-118">See Also</span></span>  
 [<span data-ttu-id="9defd-119">ICorDebugVariableSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="9defd-119">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [<span data-ttu-id="9defd-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="9defd-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

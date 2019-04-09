---
title: Metoda ICorDebugVariableSymbol::GetSlotIndex
ms.date: 03/30/2017
ms.assetid: 09c19f5f-afc4-4e0c-bffe-cd7147bc7a43
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: affe67006c9e37d55b0f9d107c92441da44c9ab8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59138797"
---
# <a name="icordebugvariablesymbolgetslotindex-method"></a><span data-ttu-id="3dd96-102">Metoda ICorDebugVariableSymbol::GetSlotIndex</span><span class="sxs-lookup"><span data-stu-id="3dd96-102">ICorDebugVariableSymbol::GetSlotIndex Method</span></span>
<span data-ttu-id="3dd96-103">Pobiera indeks zarządzane miejsce zmiennej lokalnej.</span><span class="sxs-lookup"><span data-stu-id="3dd96-103">Gets the managed slot index of a local variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3dd96-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3dd96-104">Syntax</span></span>  
  
```  
HRESULT GetSlotIndex(  
   [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3dd96-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3dd96-105">Parameters</span></span>  
 `pSlotIndex`  
 <span data-ttu-id="3dd96-106">[out] Wskaźnik do zmiennej lokalnej miejsca indeksu.</span><span class="sxs-lookup"><span data-stu-id="3dd96-106">[out] A pointer to the local variable's slot index.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3dd96-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="3dd96-107">Return Value</span></span>  
 `S_OK` <span data-ttu-id="3dd96-108">Jeśli to się powiedzie.</span><span class="sxs-lookup"><span data-stu-id="3dd96-108">if successful.</span></span> `E_FAIL` <span data-ttu-id="3dd96-109">Jeśli zmienna jest argumentu funkcji.</span><span class="sxs-lookup"><span data-stu-id="3dd96-109">if the variable is a function argument.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3dd96-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3dd96-110">Remarks</span></span>  
 <span data-ttu-id="3dd96-111">Indeks gniazda zarządzanych zmienna lokalna może służyć do pobierania informacji o metadanych zmiennej</span><span class="sxs-lookup"><span data-stu-id="3dd96-111">The managed slot index of a local variable can be used to retrieve the variable's metadata information</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3dd96-112">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="3dd96-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3dd96-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3dd96-113">Requirements</span></span>  
 <span data-ttu-id="3dd96-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3dd96-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3dd96-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3dd96-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3dd96-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3dd96-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="3dd96-117">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="3dd96-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3dd96-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3dd96-118">See also</span></span>

- [<span data-ttu-id="3dd96-119">ICorDebugVariableSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="3dd96-119">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="3dd96-120">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="3dd96-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

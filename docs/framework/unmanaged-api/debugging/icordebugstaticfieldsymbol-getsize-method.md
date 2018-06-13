---
title: ICorDebugStaticFieldSymbol::GetSize — metoda
ms.date: 03/30/2017
ms.assetid: 72389860-7e37-4656-ba46-b6aeee1860f8
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: acb72a7d6c39efa5fa93bfddc314d07ec6cd8348
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419097"
---
# <a name="icordebugstaticfieldsymbolgetsize-method"></a><span data-ttu-id="2f0bc-102">ICorDebugStaticFieldSymbol::GetSize — metoda</span><span class="sxs-lookup"><span data-stu-id="2f0bc-102">ICorDebugStaticFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="2f0bc-103">Pobiera rozmiar w bajtach pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="2f0bc-103">Gets the size in bytes of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2f0bc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2f0bc-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2f0bc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2f0bc-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="2f0bc-106">[out] Wskaźnik do długość pola.</span><span class="sxs-lookup"><span data-stu-id="2f0bc-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2f0bc-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2f0bc-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2f0bc-108">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="2f0bc-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2f0bc-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2f0bc-109">Requirements</span></span>  
 <span data-ttu-id="2f0bc-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2f0bc-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2f0bc-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2f0bc-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2f0bc-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2f0bc-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2f0bc-113">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2f0bc-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f0bc-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2f0bc-114">See Also</span></span>  
 [<span data-ttu-id="2f0bc-115">ICorDebugStaticFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="2f0bc-115">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)  
 [<span data-ttu-id="2f0bc-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="2f0bc-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

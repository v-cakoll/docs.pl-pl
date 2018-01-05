---
title: "ICorDebugStaticFieldSymbol::GetSize — metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 72389860-7e37-4656-ba46-b6aeee1860f8
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b67cbe6858e91e089c36047d6ed83743e45e1d1c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugstaticfieldsymbolgetsize-method"></a><span data-ttu-id="e1883-102">ICorDebugStaticFieldSymbol::GetSize — metoda</span><span class="sxs-lookup"><span data-stu-id="e1883-102">ICorDebugStaticFieldSymbol::GetSize Method</span></span>
<span data-ttu-id="e1883-103">Pobiera rozmiar w bajtach pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="e1883-103">Gets the size in bytes of the static field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e1883-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e1883-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbSize  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e1883-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e1883-105">Parameters</span></span>  
 `pcbSize`  
 <span data-ttu-id="e1883-106">[out] Wskaźnik do długość pola.</span><span class="sxs-lookup"><span data-stu-id="e1883-106">[out] A pointer to length of the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e1883-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e1883-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e1883-108">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="e1883-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e1883-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e1883-109">Requirements</span></span>  
 <span data-ttu-id="e1883-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e1883-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e1883-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e1883-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e1883-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e1883-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e1883-113">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e1883-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e1883-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e1883-114">See Also</span></span>  
 [<span data-ttu-id="e1883-115">ICorDebugStaticFieldSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="e1883-115">ICorDebugStaticFieldSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstaticfieldsymbol-interface.md)  
 [<span data-ttu-id="e1883-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="e1883-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

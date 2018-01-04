---
title: Interfejs ICorDebugILCode2
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugILCode2
api_location: mscordbi.dll
api_type: COM
ms.assetid: f9dc2afd-df8a-464d-bdbf-5af0a1d4bf85
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f126d92cebe3261dc92b89cbf66bbcff5fd8808e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugilcode2-interface"></a><span data-ttu-id="844b5-102">Interfejs ICorDebugILCode2</span><span class="sxs-lookup"><span data-stu-id="844b5-102">ICorDebugILCode2 Interface</span></span>
<span data-ttu-id="844b5-103">[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="844b5-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="844b5-104">Rozszerza logicznie [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) interfejsu podania metod tokenem podpisu lokalnego zmiennej funkcji, które zwracają, oraz że mapowanie profilera instrumentowanych język pośredni (IL) przesuwa się do oryginalnej metody IL przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="844b5-104">Logically extends the [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) interface to provide methods that return the token for a function's local variable signature, and that map a profiler's instrumented intermediate language (IL) offsets to original method IL offsets.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="844b5-105">Metody</span><span class="sxs-lookup"><span data-stu-id="844b5-105">Methods</span></span>  
  
|<span data-ttu-id="844b5-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="844b5-106">Method</span></span>|<span data-ttu-id="844b5-107">Opis</span><span class="sxs-lookup"><span data-stu-id="844b5-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="844b5-108">GetInstrumentedILMap, metoda</span><span class="sxs-lookup"><span data-stu-id="844b5-108">GetInstrumentedILMap Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md)|<span data-ttu-id="844b5-109">Zwraca mapę z profilera zinstrumentowane przesunięcia IL do oryginalnego przesunięcia metody IL dla tego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="844b5-109">Returns a map from profiler instrumented IL offsets to original method IL offsets for this instance.</span></span>|  
|[<span data-ttu-id="844b5-110">GetLocalVarSigToken, metoda</span><span class="sxs-lookup"><span data-stu-id="844b5-110">GetLocalVarSigToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getlocalvarsigtoken-method.md)|<span data-ttu-id="844b5-111">Pobiera token metadanych dla zmiennej podpisu lokalnego dla funkcji, która jest reprezentowana przez to wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="844b5-111">Gets the metadata token for the local variable signature for the function that is represented by this instance.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="844b5-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="844b5-112">Requirements</span></span>  
 <span data-ttu-id="844b5-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="844b5-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="844b5-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="844b5-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="844b5-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="844b5-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="844b5-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="844b5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="844b5-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="844b5-117">See Also</span></span>  
 [<span data-ttu-id="844b5-118">ICorDebugILCode, interfejs</span><span class="sxs-lookup"><span data-stu-id="844b5-118">ICorDebugILCode Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)  
 [<span data-ttu-id="844b5-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="844b5-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="844b5-120">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="844b5-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

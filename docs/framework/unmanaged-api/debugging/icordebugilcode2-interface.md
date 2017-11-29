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
ms.openlocfilehash: 2fd6b7b6b097010a307abbc260cda7c4b73e0f00
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugilcode2-interface"></a><span data-ttu-id="b0273-102">Interfejs ICorDebugILCode2</span><span class="sxs-lookup"><span data-stu-id="b0273-102">ICorDebugILCode2 Interface</span></span>
<span data-ttu-id="b0273-103">[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="b0273-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="b0273-104">Rozszerza logicznie [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) interfejsu podania metod tokenem podpisu lokalnego zmiennej funkcji, które zwracają, oraz że mapowanie profilera instrumentowanych język pośredni (IL) przesuwa się do oryginalnej metody IL przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="b0273-104">Logically extends the [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) interface to provide methods that return the token for a function's local variable signature, and that map a profiler's instrumented intermediate language (IL) offsets to original method IL offsets.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b0273-105">Metody</span><span class="sxs-lookup"><span data-stu-id="b0273-105">Methods</span></span>  
  
|<span data-ttu-id="b0273-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="b0273-106">Method</span></span>|<span data-ttu-id="b0273-107">Opis</span><span class="sxs-lookup"><span data-stu-id="b0273-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b0273-108">Metoda GetInstrumentedILMap</span><span class="sxs-lookup"><span data-stu-id="b0273-108">GetInstrumentedILMap Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md)|<span data-ttu-id="b0273-109">Zwraca mapę z profilera zinstrumentowane przesunięcia IL do oryginalnego przesunięcia metody IL dla tego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="b0273-109">Returns a map from profiler instrumented IL offsets to original method IL offsets for this instance.</span></span>|  
|[<span data-ttu-id="b0273-110">GetLocalVarSigToken — metoda</span><span class="sxs-lookup"><span data-stu-id="b0273-110">GetLocalVarSigToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getlocalvarsigtoken-method.md)|<span data-ttu-id="b0273-111">Pobiera token metadanych dla zmiennej podpisu lokalnego dla funkcji, która jest reprezentowana przez to wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="b0273-111">Gets the metadata token for the local variable signature for the function that is represented by this instance.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b0273-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b0273-112">Requirements</span></span>  
 <span data-ttu-id="b0273-113">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b0273-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b0273-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b0273-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b0273-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b0273-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b0273-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b0273-116">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b0273-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b0273-117">See Also</span></span>  
 [<span data-ttu-id="b0273-118">Interfejs ICorDebugILCode</span><span class="sxs-lookup"><span data-stu-id="b0273-118">ICorDebugILCode Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)  
 [<span data-ttu-id="b0273-119">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="b0273-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="b0273-120">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="b0273-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

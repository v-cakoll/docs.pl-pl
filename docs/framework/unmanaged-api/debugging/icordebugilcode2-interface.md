---
title: Interfejs ICorDebugILCode2
ms.date: 03/30/2017
api_name:
- ICorDebugILCode2
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: f9dc2afd-df8a-464d-bdbf-5af0a1d4bf85
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3a27dbd8b5013937bb97f37113687405c988c1fe
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59142665"
---
# <a name="icordebugilcode2-interface"></a><span data-ttu-id="b4eec-102">Interfejs ICorDebugILCode2</span><span class="sxs-lookup"><span data-stu-id="b4eec-102">ICorDebugILCode2 Interface</span></span>
<span data-ttu-id="b4eec-103">[Obsługiwane w programie .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="b4eec-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="b4eec-104">Rozszerza logicznie [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) interfejsu podania metod, które zwracają token do funkcji lokalnej zmiennej podpisu i mapy, program profilujący instrumentowanych języka pośredniego (IL) przesuwa się do oryginalnej metody IL przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="b4eec-104">Logically extends the [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) interface to provide methods that return the token for a function's local variable signature, and that map a profiler's instrumented intermediate language (IL) offsets to original method IL offsets.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="b4eec-105">Metody</span><span class="sxs-lookup"><span data-stu-id="b4eec-105">Methods</span></span>  
  
|<span data-ttu-id="b4eec-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="b4eec-106">Method</span></span>|<span data-ttu-id="b4eec-107">Opis</span><span class="sxs-lookup"><span data-stu-id="b4eec-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="b4eec-108">GetInstrumentedILMap, metoda</span><span class="sxs-lookup"><span data-stu-id="b4eec-108">GetInstrumentedILMap Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md)|<span data-ttu-id="b4eec-109">Zwraca mapę z profilera Instrumentacji przesunięcia IL do oryginalnego przesunięcia IL metody dla tego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="b4eec-109">Returns a map from profiler instrumented IL offsets to original method IL offsets for this instance.</span></span>|  
|[<span data-ttu-id="b4eec-110">GetLocalVarSigToken, metoda</span><span class="sxs-lookup"><span data-stu-id="b4eec-110">GetLocalVarSigToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getlocalvarsigtoken-method.md)|<span data-ttu-id="b4eec-111">Pobiera token metadanych dla lokalnej zmiennej podpisu dla funkcji, która jest reprezentowana przez to wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="b4eec-111">Gets the metadata token for the local variable signature for the function that is represented by this instance.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b4eec-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b4eec-112">Requirements</span></span>  
 <span data-ttu-id="b4eec-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b4eec-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b4eec-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b4eec-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b4eec-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b4eec-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b4eec-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b4eec-116">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b4eec-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b4eec-117">See also</span></span>

- [<span data-ttu-id="b4eec-118">ICorDebugILCode, interfejs</span><span class="sxs-lookup"><span data-stu-id="b4eec-118">ICorDebugILCode Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)
- [<span data-ttu-id="b4eec-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="b4eec-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="b4eec-120">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="b4eec-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

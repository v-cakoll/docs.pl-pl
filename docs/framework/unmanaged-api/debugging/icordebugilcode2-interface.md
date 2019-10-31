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
ms.openlocfilehash: 9c1a5cde5a39a334d655d865c5e44a5eb0c1766a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73131042"
---
# <a name="icordebugilcode2-interface"></a><span data-ttu-id="75682-102">Interfejs ICorDebugILCode2</span><span class="sxs-lookup"><span data-stu-id="75682-102">ICorDebugILCode2 Interface</span></span>
<span data-ttu-id="75682-103">[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="75682-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="75682-104">Logicznie rozszerza interfejs [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) w celu zapewnienia metod, które zwracają token dla sygnatury zmiennej lokalnej funkcji, i mapuje przesunięcia języka pośredniego (IL) narzędzia profilera do oryginalnej metody do przesunięcia Il.</span><span class="sxs-lookup"><span data-stu-id="75682-104">Logically extends the [ICorDebugILCode](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md) interface to provide methods that return the token for a function's local variable signature, and that map a profiler's instrumented intermediate language (IL) offsets to original method IL offsets.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="75682-105">Metody</span><span class="sxs-lookup"><span data-stu-id="75682-105">Methods</span></span>  
  
|<span data-ttu-id="75682-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="75682-106">Method</span></span>|<span data-ttu-id="75682-107">Opis</span><span class="sxs-lookup"><span data-stu-id="75682-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="75682-108">GetInstrumentedILMap, metoda</span><span class="sxs-lookup"><span data-stu-id="75682-108">GetInstrumentedILMap Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getinstrumentedilmap-method.md)|<span data-ttu-id="75682-109">Zwraca mapę z przesunięć Instrumentacji IL do metody oryginalnej dla tego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="75682-109">Returns a map from profiler instrumented IL offsets to original method IL offsets for this instance.</span></span>|  
|[<span data-ttu-id="75682-110">GetLocalVarSigToken, metoda</span><span class="sxs-lookup"><span data-stu-id="75682-110">GetLocalVarSigToken Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode2-getlocalvarsigtoken-method.md)|<span data-ttu-id="75682-111">Pobiera token metadanych lokalnej zmiennej sygnatury dla funkcji reprezentowanej przez to wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="75682-111">Gets the metadata token for the local variable signature for the function that is represented by this instance.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="75682-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="75682-112">Requirements</span></span>  
 <span data-ttu-id="75682-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75682-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75682-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="75682-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="75682-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="75682-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="75682-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75682-116">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75682-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="75682-117">See also</span></span>

- [<span data-ttu-id="75682-118">ICorDebugILCode, interfejs</span><span class="sxs-lookup"><span data-stu-id="75682-118">ICorDebugILCode Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugilcode-interface.md)
- [<span data-ttu-id="75682-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="75682-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="75682-120">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="75682-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)

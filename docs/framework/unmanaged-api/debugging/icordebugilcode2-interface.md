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
ms.openlocfilehash: 30008d6cc98f7d0d0501d67e18703ed5a344d43a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76794366"
---
# <a name="icordebugilcode2-interface"></a><span data-ttu-id="33ab6-102">Interfejs ICorDebugILCode2</span><span class="sxs-lookup"><span data-stu-id="33ab6-102">ICorDebugILCode2 Interface</span></span>
<span data-ttu-id="33ab6-103">[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="33ab6-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="33ab6-104">Logicznie rozszerza interfejs [ICorDebugILCode](icordebugilcode-interface.md) w celu zapewnienia metod, które zwracają token dla sygnatury zmiennej lokalnej funkcji, i mapuje przesunięcia języka pośredniego (IL) narzędzia profilera do oryginalnej metody do przesunięcia Il.</span><span class="sxs-lookup"><span data-stu-id="33ab6-104">Logically extends the [ICorDebugILCode](icordebugilcode-interface.md) interface to provide methods that return the token for a function's local variable signature, and that map a profiler's instrumented intermediate language (IL) offsets to original method IL offsets.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="33ab6-105">Metody</span><span class="sxs-lookup"><span data-stu-id="33ab6-105">Methods</span></span>  
  
|<span data-ttu-id="33ab6-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="33ab6-106">Method</span></span>|<span data-ttu-id="33ab6-107">Opis</span><span class="sxs-lookup"><span data-stu-id="33ab6-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="33ab6-108">GetInstrumentedILMap, metoda</span><span class="sxs-lookup"><span data-stu-id="33ab6-108">GetInstrumentedILMap Method</span></span>](icordebugilcode2-getinstrumentedilmap-method.md)|<span data-ttu-id="33ab6-109">Zwraca mapę z przesunięć Instrumentacji IL do metody oryginalnej dla tego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="33ab6-109">Returns a map from profiler instrumented IL offsets to original method IL offsets for this instance.</span></span>|  
|[<span data-ttu-id="33ab6-110">GetLocalVarSigToken, metoda</span><span class="sxs-lookup"><span data-stu-id="33ab6-110">GetLocalVarSigToken Method</span></span>](icordebugilcode2-getlocalvarsigtoken-method.md)|<span data-ttu-id="33ab6-111">Pobiera token metadanych lokalnej zmiennej sygnatury dla funkcji reprezentowanej przez to wystąpienie.</span><span class="sxs-lookup"><span data-stu-id="33ab6-111">Gets the metadata token for the local variable signature for the function that is represented by this instance.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="33ab6-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="33ab6-112">Requirements</span></span>  
 <span data-ttu-id="33ab6-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33ab6-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33ab6-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="33ab6-114">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="33ab6-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="33ab6-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="33ab6-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33ab6-116">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33ab6-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="33ab6-117">See also</span></span>

- [<span data-ttu-id="33ab6-118">ICorDebugILCode, interfejs</span><span class="sxs-lookup"><span data-stu-id="33ab6-118">ICorDebugILCode Interface</span></span>](icordebugilcode-interface.md)
- [<span data-ttu-id="33ab6-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="33ab6-119">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="33ab6-120">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="33ab6-120">Debugging</span></span>](index.md)

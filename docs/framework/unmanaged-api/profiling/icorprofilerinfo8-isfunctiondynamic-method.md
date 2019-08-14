---
title: ICorProfilerInfo8::IsFunctionDynamic
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.IsFunctionDynamic
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 71c4e749368dce65d5250b9ab78fd8713e9d61a0
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2019
ms.locfileid: "68973709"
---
# <a name="icorprofilerinfo8isfunctiondynamic-method"></a><span data-ttu-id="506ad-102">ICorProfilerInfo8:: IsFunctionDynamic, Metoda</span><span class="sxs-lookup"><span data-stu-id="506ad-102">ICorProfilerInfo8::IsFunctionDynamic Method</span></span>
  
  <span data-ttu-id="506ad-103">Określa, czy funkcja nie ma skojarzonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="506ad-103">Determines if a function does not have associated metadata.</span></span>    
  
## <a name="syntax"></a><span data-ttu-id="506ad-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="506ad-104">Syntax</span></span>  
  
```cpp
HRESULT IsFunctionDynamic( [in]  FunctionID  functionId,
                           [out] BOOL        *isDynamic);
```  
  
#### <a name="parameters"></a><span data-ttu-id="506ad-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="506ad-105">Parameters</span></span>  
 `functionId` \
  <span data-ttu-id="506ad-106">podczas  `FunctionID` Identyfikuje daną funkcję.</span><span class="sxs-lookup"><span data-stu-id="506ad-106">[in]  The `FunctionID` that identifies the function in question.</span></span>

  `isDynamic` \
  <span data-ttu-id="506ad-107">określoną Wskaźnik do elementu `BOOL` , który będzie zawierał wartość wskazującą, czy funkcja nie ma metadanych.</span><span class="sxs-lookup"><span data-stu-id="506ad-107">[out] A pointer to a `BOOL` that will contain a value indicating if the function has no metadata.</span></span>

## <a name="remarks"></a><span data-ttu-id="506ad-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="506ad-108">Remarks</span></span>  
 <span data-ttu-id="506ad-109">Funkcja jest uznawana za dynamiczną, jeśli nie ma metadanych.</span><span class="sxs-lookup"><span data-stu-id="506ad-109">A function is considered dynamic if it has no metadata.</span></span> <span data-ttu-id="506ad-110">Niektóre metody, takie jak elementy zastępcze IL lub metody LCG, nie mają skojarzonych metadanych, które można pobrać za pomocą interfejsów API IMetaDataImport.</span><span class="sxs-lookup"><span data-stu-id="506ad-110">Certain methods like IL Stubs or LCG Methods do not have associated metadata that can be retrieved using the IMetaDataImport APIs.</span></span> <span data-ttu-id="506ad-111">Te metody mogą być napotkane przez program do przechodzenia za pomocą wskaźników instrukcji lub przez nasłuchiwanie [ICorProfilerCallback::D ynamicmethodjitcompilationstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span><span class="sxs-lookup"><span data-stu-id="506ad-111">These methods can be encountered by profilers through instruction pointers or by listening to [ICorProfilerCallback::DynamicMethodJITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="506ad-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="506ad-112">Requirements</span></span>  
 <span data-ttu-id="506ad-113">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="506ad-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="506ad-114">**Nagłówki** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="506ad-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="506ad-115">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="506ad-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="506ad-116">**.NET Framework wersje:** [! UWZGLĘDNIj[net_current_v472plus](../../../../includes/net-current-v472plus.md)</span><span class="sxs-lookup"><span data-stu-id="506ad-116">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="506ad-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="506ad-117">See also</span></span>
- [<span data-ttu-id="506ad-118">ICorProfilerInfo8, interfejs</span><span class="sxs-lookup"><span data-stu-id="506ad-118">ICorProfilerInfo8 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-interface.md)


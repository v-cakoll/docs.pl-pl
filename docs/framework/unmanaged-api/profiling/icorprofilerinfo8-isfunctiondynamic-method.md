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
ms.openlocfilehash: 01aa1df27dccf41060083333588e04bc5ea88520
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855929"
---
# <a name="icorprofilerinfo8isfunctiondynamic-method"></a><span data-ttu-id="5e2af-102">ICorProfilerInfo8:: IsFunctionDynamic, Metoda</span><span class="sxs-lookup"><span data-stu-id="5e2af-102">ICorProfilerInfo8::IsFunctionDynamic Method</span></span>

<span data-ttu-id="5e2af-103">Określa, czy funkcja nie ma skojarzonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="5e2af-103">Determines if a function does not have associated metadata.</span></span>

## <a name="syntax"></a><span data-ttu-id="5e2af-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5e2af-104">Syntax</span></span>

```cpp
HRESULT IsFunctionDynamic( [in]  FunctionID  functionId,
                           [out] BOOL        *isDynamic);
```

#### <a name="parameters"></a><span data-ttu-id="5e2af-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5e2af-105">Parameters</span></span>

`functionId` \
<span data-ttu-id="5e2af-106">podczas  `FunctionID` Identyfikuje daną funkcję.</span><span class="sxs-lookup"><span data-stu-id="5e2af-106">[in]  The `FunctionID` that identifies the function in question.</span></span>

`isDynamic` \
<span data-ttu-id="5e2af-107">określoną Wskaźnik do elementu `BOOL` , który będzie zawierał wartość wskazującą, czy funkcja nie ma metadanych.</span><span class="sxs-lookup"><span data-stu-id="5e2af-107">[out] A pointer to a `BOOL` that will contain a value indicating if the function has no metadata.</span></span>

## <a name="remarks"></a><span data-ttu-id="5e2af-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5e2af-108">Remarks</span></span>

<span data-ttu-id="5e2af-109">Funkcja jest uznawana za dynamiczną, jeśli nie ma metadanych.</span><span class="sxs-lookup"><span data-stu-id="5e2af-109">A function is considered dynamic if it has no metadata.</span></span> <span data-ttu-id="5e2af-110">Niektóre metody, takie jak elementy zastępcze IL lub metody LCG, nie mają skojarzonych metadanych, które można pobrać za pomocą interfejsów API IMetaDataImport.</span><span class="sxs-lookup"><span data-stu-id="5e2af-110">Certain methods like IL Stubs or LCG Methods do not have associated metadata that can be retrieved using the IMetaDataImport APIs.</span></span> <span data-ttu-id="5e2af-111">Te metody mogą być napotkane przez program do przechodzenia za pomocą wskaźników instrukcji lub przez nasłuchiwanie [ICorProfilerCallback::D ynamicmethodjitcompilationstarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span><span class="sxs-lookup"><span data-stu-id="5e2af-111">These methods can be encountered by profilers through instruction pointers or by listening to [ICorProfilerCallback::DynamicMethodJITCompilationStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="5e2af-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5e2af-112">Requirements</span></span>

<span data-ttu-id="5e2af-113">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e2af-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="5e2af-114">**Nagłówki** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="5e2af-114">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="5e2af-115">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5e2af-115">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="5e2af-116">**.NET Framework wersje:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="5e2af-116">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="5e2af-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5e2af-117">See also</span></span>

- [<span data-ttu-id="5e2af-118">ICorProfilerInfo8, interfejs</span><span class="sxs-lookup"><span data-stu-id="5e2af-118">ICorProfilerInfo8 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo8-interface.md)

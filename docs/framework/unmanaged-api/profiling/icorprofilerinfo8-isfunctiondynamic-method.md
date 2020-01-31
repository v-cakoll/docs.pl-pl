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
ms.openlocfilehash: 50b4de2de3e74a5835ee5706999892735269d4c2
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861739"
---
# <a name="icorprofilerinfo8isfunctiondynamic-method"></a><span data-ttu-id="bae5a-102">ICorProfilerInfo8:: IsFunctionDynamic, Metoda</span><span class="sxs-lookup"><span data-stu-id="bae5a-102">ICorProfilerInfo8::IsFunctionDynamic Method</span></span>

<span data-ttu-id="bae5a-103">Określa, czy funkcja nie ma skojarzonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="bae5a-103">Determines if a function does not have associated metadata.</span></span>

## <a name="syntax"></a><span data-ttu-id="bae5a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bae5a-104">Syntax</span></span>

```cpp
HRESULT IsFunctionDynamic( [in]  FunctionID  functionId,
                           [out] BOOL        *isDynamic);
```

## <a name="parameters"></a><span data-ttu-id="bae5a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bae5a-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="bae5a-106">\[w] `FunctionID`, który identyfikuje daną funkcję.</span><span class="sxs-lookup"><span data-stu-id="bae5a-106">\[in]  The `FunctionID` that identifies the function in question.</span></span>

- `isDynamic`

  <span data-ttu-id="bae5a-107">\[out] wskaźnik do `BOOL`, który będzie zawierać wartość wskazującą, czy funkcja nie ma metadanych.</span><span class="sxs-lookup"><span data-stu-id="bae5a-107">\[out] A pointer to a `BOOL` that will contain a value indicating if the function has no metadata.</span></span>

## <a name="remarks"></a><span data-ttu-id="bae5a-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bae5a-108">Remarks</span></span>

<span data-ttu-id="bae5a-109">Funkcja jest uznawana za dynamiczną, jeśli nie ma metadanych.</span><span class="sxs-lookup"><span data-stu-id="bae5a-109">A function is considered dynamic if it has no metadata.</span></span> <span data-ttu-id="bae5a-110">Niektóre metody, takie jak elementy zastępcze IL lub metody LCG, nie mają skojarzonych metadanych, które można pobrać za pomocą interfejsów API IMetaDataImport.</span><span class="sxs-lookup"><span data-stu-id="bae5a-110">Certain methods like IL Stubs or LCG Methods do not have associated metadata that can be retrieved using the IMetaDataImport APIs.</span></span> <span data-ttu-id="bae5a-111">Te metody mogą być napotkane przez program do przechodzenia za pomocą wskaźników instrukcji lub przez nasłuchiwanie [ICorProfilerCallback::D ynamicmethodjitcompilationstarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span><span class="sxs-lookup"><span data-stu-id="bae5a-111">These methods can be encountered by profilers through instruction pointers or by listening to [ICorProfilerCallback::DynamicMethodJITCompilationStarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="bae5a-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bae5a-112">Requirements</span></span>

<span data-ttu-id="bae5a-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bae5a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="bae5a-114">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="bae5a-114">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="bae5a-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="bae5a-115">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="bae5a-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="bae5a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="bae5a-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bae5a-117">See also</span></span>

- [<span data-ttu-id="bae5a-118">ICorProfilerInfo8, interfejs</span><span class="sxs-lookup"><span data-stu-id="bae5a-118">ICorProfilerInfo8 Interface</span></span>](icorprofilerinfo8-interface.md)

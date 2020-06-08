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
ms.openlocfilehash: c88279d361ea78a2e910c4621e92c500902d9124
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495128"
---
# <a name="icorprofilerinfo8isfunctiondynamic-method"></a><span data-ttu-id="f8f26-102">ICorProfilerInfo8:: IsFunctionDynamic, Metoda</span><span class="sxs-lookup"><span data-stu-id="f8f26-102">ICorProfilerInfo8::IsFunctionDynamic Method</span></span>

<span data-ttu-id="f8f26-103">Określa, czy funkcja nie ma skojarzonych metadanych.</span><span class="sxs-lookup"><span data-stu-id="f8f26-103">Determines if a function does not have associated metadata.</span></span>

## <a name="syntax"></a><span data-ttu-id="f8f26-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f8f26-104">Syntax</span></span>

```cpp
HRESULT IsFunctionDynamic( [in]  FunctionID  functionId,
                           [out] BOOL        *isDynamic);
```

## <a name="parameters"></a><span data-ttu-id="f8f26-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f8f26-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="f8f26-106">\[w], `FunctionID` który identyfikuje daną funkcję.</span><span class="sxs-lookup"><span data-stu-id="f8f26-106">\[in]  The `FunctionID` that identifies the function in question.</span></span>

- `isDynamic`

  <span data-ttu-id="f8f26-107">\[out] wskaźnik do elementu `BOOL` , który będzie zawierał wartość wskazującą, czy funkcja nie ma metadanych.</span><span class="sxs-lookup"><span data-stu-id="f8f26-107">\[out] A pointer to a `BOOL` that will contain a value indicating if the function has no metadata.</span></span>

## <a name="remarks"></a><span data-ttu-id="f8f26-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f8f26-108">Remarks</span></span>

<span data-ttu-id="f8f26-109">Funkcja jest uznawana za dynamiczną, jeśli nie ma metadanych.</span><span class="sxs-lookup"><span data-stu-id="f8f26-109">A function is considered dynamic if it has no metadata.</span></span> <span data-ttu-id="f8f26-110">Niektóre metody, takie jak elementy zastępcze IL lub metody LCG, nie mają skojarzonych metadanych, które można pobrać za pomocą interfejsów API IMetaDataImport.</span><span class="sxs-lookup"><span data-stu-id="f8f26-110">Certain methods like IL Stubs or LCG Methods do not have associated metadata that can be retrieved using the IMetaDataImport APIs.</span></span> <span data-ttu-id="f8f26-111">Te metody mogą być napotkane przez program do przechodzenia za pomocą wskaźników instrukcji lub przez nasłuchiwanie [ICorProfilerCallback::D ynamicmethodjitcompilationstarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span><span class="sxs-lookup"><span data-stu-id="f8f26-111">These methods can be encountered by profilers through instruction pointers or by listening to [ICorProfilerCallback::DynamicMethodJITCompilationStarted](icorprofilercallback8-dynamicmethodjitcompilationstarted-method.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="f8f26-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f8f26-112">Requirements</span></span>

<span data-ttu-id="f8f26-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f8f26-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

<span data-ttu-id="f8f26-114">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f8f26-114">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="f8f26-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f8f26-115">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="f8f26-116">**.NET Framework wersje:**[!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="f8f26-116">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="f8f26-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f8f26-117">See also</span></span>

- [<span data-ttu-id="f8f26-118">ICorProfilerInfo8, interfejs</span><span class="sxs-lookup"><span data-stu-id="f8f26-118">ICorProfilerInfo8 Interface</span></span>](icorprofilerinfo8-interface.md)

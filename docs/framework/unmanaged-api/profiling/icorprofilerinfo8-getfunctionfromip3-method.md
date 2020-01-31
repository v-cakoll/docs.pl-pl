---
title: ICorProfilerInfo8::GetFunctionFromIP3
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo8.GetFunctionFromIP3
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 6d50a5d74eccff6fe39aca111f768bac4d8f2e2e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868333"
---
# <a name="icorprofilerinfo8getfunctionfromip3-method"></a><span data-ttu-id="92995-102">ICorProfilerInfo8:: GetFunctionFromIP3, Metoda</span><span class="sxs-lookup"><span data-stu-id="92995-102">ICorProfilerInfo8::GetFunctionFromIP3 Method</span></span>

<span data-ttu-id="92995-103">Mapuje wskaźnik zarządzanej instrukcji kodu na FunctionID.</span><span class="sxs-lookup"><span data-stu-id="92995-103">Maps a managed code instruction pointer to a FunctionID.</span></span> <span data-ttu-id="92995-104">Ta metoda działa w przypadku metod dynamicznych i niedynamicznych.</span><span class="sxs-lookup"><span data-stu-id="92995-104">This method works for both dynamic and non-dynamic methods.</span></span>

## <a name="syntax"></a><span data-ttu-id="92995-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="92995-105">Syntax</span></span>

```cpp
HRESULT GetFunctionFromIP3([in] LPCBYTE ip,
                           [out] FunctionID *functionId,
                           [out] ReJITID * pReJitId);
```

## <a name="parameters"></a><span data-ttu-id="92995-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="92995-106">Parameters</span></span>

- `ip`

  <span data-ttu-id="92995-107">\[w] wskaźnik instrukcji w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="92995-107">\[in] The instruction pointer in managed code.</span></span>

- `pFunctionId`

  <span data-ttu-id="92995-108">\[out] identyfikator funkcji.</span><span class="sxs-lookup"><span data-stu-id="92995-108">\[out] The function ID.</span></span>

- `pReJitId`

  <span data-ttu-id="92995-109">\[out] tożsamość funkcji ponownie skompilowanej w trybie JIT.</span><span class="sxs-lookup"><span data-stu-id="92995-109">\[out] The identity of the JIT-recompiled version of the function.</span></span>

## <a name="remarks"></a><span data-ttu-id="92995-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="92995-110">Remarks</span></span>

<span data-ttu-id="92995-111">Ta metoda działa w przypadku metod dynamicznych i niedynamicznych.</span><span class="sxs-lookup"><span data-stu-id="92995-111">This method works for both dynamic and non-dynamic methods.</span></span> <span data-ttu-id="92995-112">Jest to nadzbiór [GetFunctionFromIP2 —](icorprofilerinfo4-getfunctionfromip2-method.md), który działa tylko w przypadku funkcji z metadanymi.</span><span class="sxs-lookup"><span data-stu-id="92995-112">It is a superset of [GetFunctionFromIP2](icorprofilerinfo4-getfunctionfromip2-method.md), which only works for functions with metadata.</span></span>

## <a name="requirements"></a><span data-ttu-id="92995-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="92995-113">Requirements</span></span>

<span data-ttu-id="92995-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92995-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="92995-115">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="92995-115">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="92995-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="92995-116">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="92995-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span><span class="sxs-lookup"><span data-stu-id="92995-117">**.NET Framework Versions:** [!INCLUDE[net_current_v472plus](../../../../includes/net-current-v472plus.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="92995-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="92995-118">See also</span></span>

- [<span data-ttu-id="92995-119">ICorProfilerInfo8, interfejs</span><span class="sxs-lookup"><span data-stu-id="92995-119">ICorProfilerInfo8 Interface</span></span>](icorprofilerinfo8-interface.md)

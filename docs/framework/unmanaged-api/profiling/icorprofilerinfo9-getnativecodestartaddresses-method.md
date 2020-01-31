---
title: ICorProfilerInfo9::GetNativeCodeStartAddresses
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetNativeCodeStartAddresses
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 8412020fb98fde245b873a2f0c6a355f6436f712
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868281"
---
# <a name="icorprofilerinfo9getnativecodestartaddresses-method"></a><span data-ttu-id="b1abd-102">ICorProfilerInfo9:: GetNativeCodeStartAddresses, Metoda</span><span class="sxs-lookup"><span data-stu-id="b1abd-102">ICorProfilerInfo9::GetNativeCodeStartAddresses Method</span></span>

<span data-ttu-id="b1abd-103">Mając functionId i rejitId, wylicza natywny adres początkowy kodu dla wszystkich wersji trybie JIT tego kodu, który już istnieje.</span><span class="sxs-lookup"><span data-stu-id="b1abd-103">Given a functionId and rejitId, enumerates the native code start address of all jitted versions of this code that currently exist.</span></span>

## <a name="syntax"></a><span data-ttu-id="b1abd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b1abd-104">Syntax</span></span>

```cpp
HRESULT GetNativeCodeStartAddresses( [in]  FunctionID functionID,
                                     [in]  ReJITID reJitId,
                                     [in]  ULONG32 cCodeStartAddresses,
                                     [out] ULONG32 *pcCodeStartAddresses,
                                     [out] UINT_PTR codeStartAddresses[]);
```

## <a name="parameters"></a><span data-ttu-id="b1abd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b1abd-105">Parameters</span></span>

- `functionId`

  <span data-ttu-id="b1abd-106">\[in) identyfikator funkcji, której powinny zostać zwrócone adresy początkowe kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="b1abd-106">\[in] The ID of the function whose native code start addresses should be returned.</span></span>

- `reJitId`

  <span data-ttu-id="b1abd-107">\[] tożsamość funkcji ponownie skompilowanej JIT.</span><span class="sxs-lookup"><span data-stu-id="b1abd-107">\[in] The identity of the JIT-recompiled function.</span></span>

- `cCodeStartAddresses`

  <span data-ttu-id="b1abd-108">\[] maksymalny rozmiar tablicy `codeStartAddresses`.</span><span class="sxs-lookup"><span data-stu-id="b1abd-108">\[in] The maximum size of the `codeStartAddresses` array.</span></span>

- `pcCodeStartAddresses`

  <span data-ttu-id="b1abd-109">\[out] Liczba dostępnych adresów.</span><span class="sxs-lookup"><span data-stu-id="b1abd-109">\[out] The number of available addresses.</span></span>

- `codeStartAddresses`

  <span data-ttu-id="b1abd-110">\[out] tablica `UINT_PTR`, z których każdy jest adresem początkowym dla określonej funkcji.</span><span class="sxs-lookup"><span data-stu-id="b1abd-110">\[out] An array of `UINT_PTR`, each one of which is the start address for a native body for the specified function.</span></span>

## <a name="remarks"></a><span data-ttu-id="b1abd-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b1abd-111">Remarks</span></span>

<span data-ttu-id="b1abd-112">Gdy kompilacja warstwowa jest włączona, funkcja może mieć więcej niż jedną treść kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="b1abd-112">When tiered compilation is enabled, a function may have more than one native code body.</span></span>

## <a name="requirements"></a><span data-ttu-id="b1abd-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b1abd-113">Requirements</span></span>

<span data-ttu-id="b1abd-114">**Platformy:** Zobacz [obsługiwane systemy operacyjne .NET Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="b1abd-114">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>

<span data-ttu-id="b1abd-115">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="b1abd-115">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="b1abd-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b1abd-116">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="b1abd-117">**Wersje .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1abd-117">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="b1abd-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b1abd-118">See also</span></span>

- [<span data-ttu-id="b1abd-119">ICorProfilerInfo9, interfejs</span><span class="sxs-lookup"><span data-stu-id="b1abd-119">ICorProfilerInfo9 Interface</span></span>](icorprofilerinfo9-interface.md)

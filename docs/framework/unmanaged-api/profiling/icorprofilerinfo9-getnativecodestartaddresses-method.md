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
ms.openlocfilehash: 80571933bc8d91c074dbee62aad50cece6277d51
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69665510"
---
# <a name="icorprofilerinfo9getnativecodestartaddresses-method"></a><span data-ttu-id="57af4-102">ICorProfilerInfo9:: GetNativeCodeStartAddresses, Metoda</span><span class="sxs-lookup"><span data-stu-id="57af4-102">ICorProfilerInfo9::GetNativeCodeStartAddresses Method</span></span>

<span data-ttu-id="57af4-103">Mając functionId i rejitId, wylicza natywny adres początkowy kodu dla wszystkich wersji trybie JIT tego kodu, który już istnieje.</span><span class="sxs-lookup"><span data-stu-id="57af4-103">Given a functionId and rejitId, enumerates the native code start address of all jitted versions of this code that currently exist.</span></span>

## <a name="syntax"></a><span data-ttu-id="57af4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="57af4-104">Syntax</span></span>

```cpp
HRESULT GetNativeCodeStartAddresses( [in]  FunctionID functionID,
                                     [in]  ReJITID reJitId,
                                     [in]  ULONG32 cCodeStartAddresses,
                                     [out] ULONG32 *pcCodeStartAddresses,
                                     [out] UINT_PTR codeStartAddresses[]);
```

#### <a name="parameters"></a><span data-ttu-id="57af4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="57af4-105">Parameters</span></span>

`functionId` \
<span data-ttu-id="57af4-106">podczas Identyfikator funkcji, której powinny zostać zwrócone adresy początkowe kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="57af4-106">[in] The ID of the function whose native code start addresses should be returned.</span></span>

`reJitId` \
<span data-ttu-id="57af4-107">podczas Tożsamość funkcji ponownie skompilowanej JIT.</span><span class="sxs-lookup"><span data-stu-id="57af4-107">[in] The identity of the JIT-recompiled function.</span></span>

`cCodeStartAddresses` \
<span data-ttu-id="57af4-108">podczas Maksymalny rozmiar `codeStartAddresses` tablicy.</span><span class="sxs-lookup"><span data-stu-id="57af4-108">[in] The maximum size of the `codeStartAddresses` array.</span></span>

`pcCodeStartAddresses` \
<span data-ttu-id="57af4-109">określoną Liczba dostępnych adresów.</span><span class="sxs-lookup"><span data-stu-id="57af4-109">[out] The number of available addresses.</span></span>

`codeStartAddresses` \
<span data-ttu-id="57af4-110">określoną Tablica, z `UINT_PTR`której każdy jest adresem początkowym dla określonej funkcji.</span><span class="sxs-lookup"><span data-stu-id="57af4-110">[out] An array of `UINT_PTR`, each one of which is the start address for a native body for the specified function.</span></span>

## <a name="remarks"></a><span data-ttu-id="57af4-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="57af4-111">Remarks</span></span>

<span data-ttu-id="57af4-112">Gdy kompilacja warstwowa jest włączona, funkcja może mieć więcej niż jedną treść kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="57af4-112">When tiered compilation is enabled, a function may have more than one native code body.</span></span>

## <a name="requirements"></a><span data-ttu-id="57af4-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="57af4-113">Requirements</span></span>

<span data-ttu-id="57af4-114">**Poszczególnych** Zobacz [obsługiwane systemy operacyjne .NET Core](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span><span class="sxs-lookup"><span data-stu-id="57af4-114">**Platforms:** See [.NET Core supported operating systems](../../../core/windows-prerequisites.md#net-core-supported-operating-systems).</span></span>

<span data-ttu-id="57af4-115">**Nagłówki** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="57af4-115">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="57af4-116">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="57af4-116">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="57af4-117">**Wersje .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="57af4-117">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="57af4-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="57af4-118">See also</span></span>

- [<span data-ttu-id="57af4-119">ICorProfilerInfo9, interfejs</span><span class="sxs-lookup"><span data-stu-id="57af4-119">ICorProfilerInfo9 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo9-interface.md)

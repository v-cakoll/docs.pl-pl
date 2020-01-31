---
title: ICorProfilerInfo9::GetCodeInfo4
ms.date: 08/06/2019
dev_langs:
- cpp
api_name:
- ICorProfilerInfo9.GetCodeInfo4
api_location:
- mscorwks.dll
api_type:
- COM
author: davmason
ms.author: davmason
ms.openlocfilehash: 3e3e3afc221d153ff3573126ff10014d39af761a
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868307"
---
# <a name="icorprofilerinfo9getcodeinfo4-method"></a><span data-ttu-id="87305-102">ICorProfilerInfo9:: GetCodeInfo4, Metoda</span><span class="sxs-lookup"><span data-stu-id="87305-102">ICorProfilerInfo9::GetCodeInfo4 Method</span></span>

<span data-ttu-id="87305-103">Przy podanym adresie początkowym kodu natywnego program zwraca bloki pamięci wirtualnej, która przechowuje ten kod.</span><span class="sxs-lookup"><span data-stu-id="87305-103">Given the native code start address, returns the blocks of virtual memory that store this code.</span></span>

## <a name="syntax"></a><span data-ttu-id="87305-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="87305-104">Syntax</span></span>

```cpp
HRESULT GetCodeInfo4( [in]  UINT_PTR pNativeCodeStartAddress,
                      [in]  ULONG32 cCodeInfos,
                      [out] ULONG32* pcCodeInfos,
                      [out] COR_PRF_CODE_INFO codeInfos[]);
```

## <a name="parameters"></a><span data-ttu-id="87305-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="87305-105">Parameters</span></span>

- `pNativeCodeStartAddress`

  <span data-ttu-id="87305-106">\[w] wskaźnik do początku funkcji natywnej.</span><span class="sxs-lookup"><span data-stu-id="87305-106">\[in] A pointer to the start of a native function.</span></span>

- `cCodeInfos`

  <span data-ttu-id="87305-107">\[w] rozmiar tablicy `codeInfos`.</span><span class="sxs-lookup"><span data-stu-id="87305-107">\[in] The size of the `codeInfos` array.</span></span>

- `pcCodeInfos`

  <span data-ttu-id="87305-108">\[out] wskaźnik do łącznej liczby dostępnych struktur [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="87305-108">\[out] A pointer to the total number of [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structures available.</span></span>

- `codeInfos`

  <span data-ttu-id="87305-109">\[out] bufor dostarczony przez wywołującego.</span><span class="sxs-lookup"><span data-stu-id="87305-109">\[out] A caller-provided buffer.</span></span> <span data-ttu-id="87305-110">Po powrocie metody zawiera tablicę struktur `COR_PRF_CODE_INFO`, z których każdy opisuje blok kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="87305-110">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>

## <a name="remarks"></a><span data-ttu-id="87305-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="87305-111">Remarks</span></span>

<span data-ttu-id="87305-112">Metoda `GetCodeInfo4` jest podobna do [GetCodeInfo3 —](icorprofilerinfo4-getcodeinfo3-method.md), z tą różnicą, że może wyszukiwać informacje o kodzie dla różnych natywnych wersji metody.</span><span class="sxs-lookup"><span data-stu-id="87305-112">The `GetCodeInfo4` method is similar to [GetCodeInfo3](icorprofilerinfo4-getcodeinfo3-method.md), except that it can look up code information for different native versions of a method.</span></span>

> [!NOTE]
> <span data-ttu-id="87305-113">`GetCodeInfo4` może wyzwolić wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="87305-113">`GetCodeInfo4` can trigger a garbage collection.</span></span>

<span data-ttu-id="87305-114">Zakresy są sortowane w kolejności rosnącego, typowego przesunięcia języka pośredniego (CIL).</span><span class="sxs-lookup"><span data-stu-id="87305-114">The extents are sorted in order of increasing Common Intermediate Language (CIL) offset.</span></span>

<span data-ttu-id="87305-115">Po powrocie `GetCodeInfo4` należy sprawdzić, czy bufor `codeInfos` był wystarczająco duży, aby zawierał wszystkie struktury [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="87305-115">After `GetCodeInfo4` returns, you must verify that the `codeInfos` buffer was large enough to contain all the [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structures.</span></span> <span data-ttu-id="87305-116">W tym celu należy porównać wartość `cCodeInfos` z wartością parametru `cchName`.</span><span class="sxs-lookup"><span data-stu-id="87305-116">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="87305-117">Jeśli `cCodeInfos` podzielona przez rozmiar struktury [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) jest mniejsza niż `pcCodeInfos`, Przydziel większy bufor `codeInfos`, zaktualizuj `cCodeInfos` z nowym, większym rozmiarem i ponownie wywołaj `GetCodeInfo4`.</span><span class="sxs-lookup"><span data-stu-id="87305-117">If `cCodeInfos` divided by the size of a [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo4` again.</span></span>

<span data-ttu-id="87305-118">Alternatywnie można najpierw wywołać `GetCodeInfo4` z buforem `codeInfos` o zerowej długości, aby uzyskać prawidłowy rozmiar buforu.</span><span class="sxs-lookup"><span data-stu-id="87305-118">Alternatively, you can first call `GetCodeInfo4` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="87305-119">Następnie można ustawić `codeInfos` rozmiar buforu na wartość zwróconą w `pcCodeInfos`, pomnożoną przez rozmiar struktury [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) i ponownie wywołać `GetCodeInfo4`.</span><span class="sxs-lookup"><span data-stu-id="87305-119">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structure, and call `GetCodeInfo4` again.</span></span>

## <a name="requirements"></a><span data-ttu-id="87305-120">Wymagania</span><span class="sxs-lookup"><span data-stu-id="87305-120">Requirements</span></span>

<span data-ttu-id="87305-121">**Platformy:** Zobacz [obsługiwane systemy operacyjne .NET Core](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span><span class="sxs-lookup"><span data-stu-id="87305-121">**Platforms:** See [.NET Core supported operating systems](../../../core/install/dependencies.md?tabs=netcore30&pivots=os-windows).</span></span>

<span data-ttu-id="87305-122">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="87305-122">**Header:** CorProf.idl, CorProf.h</span></span>

<span data-ttu-id="87305-123">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="87305-123">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="87305-124">**Wersje .NET:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87305-124">**.NET Versions:** [!INCLUDE[net_core_22](../../../../includes/net-core-22-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="87305-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="87305-125">See also</span></span>

- [<span data-ttu-id="87305-126">ICorProfilerInfo9, interfejs</span><span class="sxs-lookup"><span data-stu-id="87305-126">ICorProfilerInfo9 Interface</span></span>](ICorProfilerInfo9-interface.md)

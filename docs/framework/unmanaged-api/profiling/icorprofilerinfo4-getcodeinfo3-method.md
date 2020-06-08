---
title: ICorProfilerInfo4::GetCodeInfo3 — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetCodeInfo3
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetCodeInfo3
helpviewer_keywords:
- GetCodeInfo3 method, ICorProfilerInfo4 interface [.NET Framework profiling]
- ICorProfilerInfo4::GetCodeInfo3 method [.NET Framework profiling]
ms.assetid: bb8c105e-4d9a-4684-8c05-ed6909cc1b8c
topic_type:
- apiref
ms.openlocfilehash: 54e522aaaf23ae81b96b6be7168a9a13f28a16d2
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496142"
---
# <a name="icorprofilerinfo4getcodeinfo3-method"></a><span data-ttu-id="0949c-102">ICorProfilerInfo4::GetCodeInfo3 — Metoda</span><span class="sxs-lookup"><span data-stu-id="0949c-102">ICorProfilerInfo4::GetCodeInfo3 Method</span></span>
<span data-ttu-id="0949c-103">Pobiera zakresy kodu natywnego skojarzone z rekompilowaną ponownie wersją określonej funkcji JIT.</span><span class="sxs-lookup"><span data-stu-id="0949c-103">Gets the extents of native code associated with the JIT-recompiled version of the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0949c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0949c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeInfo3(  
    [in]  FunctionID functionID,  
    [in]  ReJITID reJitId,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0949c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0949c-105">Parameters</span></span>  
 `functionID`  
 <span data-ttu-id="0949c-106">podczas Identyfikator funkcji, z którą jest skojarzony kod natywny.</span><span class="sxs-lookup"><span data-stu-id="0949c-106">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `reJitId`  
 <span data-ttu-id="0949c-107">podczas Tożsamość funkcji ponownie skompilowanej JIT.</span><span class="sxs-lookup"><span data-stu-id="0949c-107">[in] The identity of the JIT-recompiled function.</span></span>  
  
 `cCodeInfos`  
 <span data-ttu-id="0949c-108">podczas Rozmiar `codeInfos` tablicy.</span><span class="sxs-lookup"><span data-stu-id="0949c-108">[in] The size of the `codeInfos` array.</span></span>  
  
 `pcCodeInfos`  
 <span data-ttu-id="0949c-109">określoną Wskaźnik do łącznej liczby dostępnych struktur [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="0949c-109">[out] A pointer to the total number of [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structures available.</span></span>  
  
 `codeInfos`  
 <span data-ttu-id="0949c-110">określoną Bufor dostarczony przez wywołującego.</span><span class="sxs-lookup"><span data-stu-id="0949c-110">[out] A caller-provided buffer.</span></span> <span data-ttu-id="0949c-111">Po powrocie metody zawiera tablicę `COR_PRF_CODE_INFO` struktur, z których każdy opisuje blok kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="0949c-111">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0949c-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0949c-112">Remarks</span></span>  
 <span data-ttu-id="0949c-113">`GetCodeInfo3`Metoda jest podobna do [GetCodeInfo2 —](icorprofilerinfo2-getcodeinfo2-method.md), z tą różnicą, że zostanie pobrany identyfikator funkcji JIT-rekompilowany przez funkcję, która zawiera określony adres IP.</span><span class="sxs-lookup"><span data-stu-id="0949c-113">The `GetCodeInfo3` method is similar to [GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md), except that it will get the JIT-recompiled ID of the function that contains the specified IP address.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0949c-114">`GetCodeInfo3`może wyzwolić wyrzucanie elementów bezużytecznych, natomiast [GetCodeInfo2 —](icorprofilerinfo2-getcodeinfo2-method.md) nie będzie.</span><span class="sxs-lookup"><span data-stu-id="0949c-114">`GetCodeInfo3` can trigger a garbage collection, whereas [GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md) will not.</span></span> <span data-ttu-id="0949c-115">Aby uzyskać więcej informacji, zobacz [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](corprof-e-unsupported-call-sequence-hresult.md) HRESULT.</span><span class="sxs-lookup"><span data-stu-id="0949c-115">For more information, see the [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](corprof-e-unsupported-call-sequence-hresult.md) HRESULT.</span></span>  
  
 <span data-ttu-id="0949c-116">Zakresy są sortowane w kolejności rosnącego, typowego przesunięcia języka pośredniego (CIL).</span><span class="sxs-lookup"><span data-stu-id="0949c-116">The extents are sorted in order of increasing Common Intermediate Language (CIL) offset.</span></span>  
  
 <span data-ttu-id="0949c-117">Po `GetCodeInfo3` powrocie należy sprawdzić, czy `codeInfos` bufor jest wystarczająco duży, aby zawierał wszystkie struktury [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="0949c-117">After `GetCodeInfo3` returns, you must verify that the `codeInfos` buffer was large enough to contain all the [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structures.</span></span> <span data-ttu-id="0949c-118">W tym celu należy porównać wartość `cCodeInfos` z wartością `cchName` parametru.</span><span class="sxs-lookup"><span data-stu-id="0949c-118">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="0949c-119">Jeśli `cCodeInfos` podzielona przez rozmiar struktury [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) jest mniejsza niż `pcCodeInfos` , Przydziel większy `codeInfos` bufor, zaktualizuj `cCodeInfos` przy użyciu nowego, większego rozmiaru i ponownie wywołaj `GetCodeInfo3` .</span><span class="sxs-lookup"><span data-stu-id="0949c-119">If `cCodeInfos` divided by the size of a [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo3` again.</span></span>  
  
 <span data-ttu-id="0949c-120">Alternatywnie, można najpierw wywołać `GetCodeInfo3` z buforem o zerowej długości, `codeInfos` Aby uzyskać prawidłowy rozmiar buforu.</span><span class="sxs-lookup"><span data-stu-id="0949c-120">Alternatively, you can first call `GetCodeInfo3` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="0949c-121">Następnie można ustawić `codeInfos` rozmiar buforu na wartość zwróconą w `pcCodeInfos` , pomnożoną przez rozmiar struktury [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) i `GetCodeInfo3` ponownie wywołać.</span><span class="sxs-lookup"><span data-stu-id="0949c-121">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structure, and call `GetCodeInfo3` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0949c-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0949c-122">Requirements</span></span>  
 <span data-ttu-id="0949c-123">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0949c-123">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0949c-124">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="0949c-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0949c-125">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0949c-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0949c-126">**.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0949c-126">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0949c-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0949c-127">See also</span></span>

- [<span data-ttu-id="0949c-128">GetCodeInfo2, metoda</span><span class="sxs-lookup"><span data-stu-id="0949c-128">GetCodeInfo2 Method</span></span>](icorprofilerinfo2-getcodeinfo2-method.md)
- [<span data-ttu-id="0949c-129">ICorProfilerInfo4 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="0949c-129">ICorProfilerInfo4 Interface</span></span>](icorprofilerinfo4-interface.md)
- [<span data-ttu-id="0949c-130">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="0949c-130">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="0949c-131">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="0949c-131">Profiling</span></span>](index.md)

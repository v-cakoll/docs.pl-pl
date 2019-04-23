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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cb067d16ef7f8177f979a083707f8c6ef36750c0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59145811"
---
# <a name="icorprofilerinfo4getcodeinfo3-method"></a><span data-ttu-id="0c1ba-102">ICorProfilerInfo4::GetCodeInfo3 — Metoda</span><span class="sxs-lookup"><span data-stu-id="0c1ba-102">ICorProfilerInfo4::GetCodeInfo3 Method</span></span>
<span data-ttu-id="0c1ba-103">Pobiera zakres skojarzony z wersją określoną funkcję ponownie skompilowana JIT kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="0c1ba-103">Gets the extents of native code associated with the JIT-recompiled version of the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c1ba-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0c1ba-104">Syntax</span></span>  
  
```  
HRESULT GetCodeInfo3(  
    [in]  FunctionID functionID,  
    [in]  ReJITID reJitId,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c1ba-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0c1ba-105">Parameters</span></span>  
 `functionID`  
 <span data-ttu-id="0c1ba-106">[in] Identyfikator funkcji, z którą jest skojarzony kod macierzysty.</span><span class="sxs-lookup"><span data-stu-id="0c1ba-106">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `reJitId`  
 <span data-ttu-id="0c1ba-107">[in] Tożsamość funkcja ponownie skompilowana JIT.</span><span class="sxs-lookup"><span data-stu-id="0c1ba-107">[in] The identity of the JIT-recompiled function.</span></span>  
  
 `cCodeInfos`  
 <span data-ttu-id="0c1ba-108">[in] Rozmiar `codeInfos` tablicy.</span><span class="sxs-lookup"><span data-stu-id="0c1ba-108">[in] The size of the `codeInfos` array.</span></span>  
  
 `pcCodeInfos`  
 <span data-ttu-id="0c1ba-109">[out] Wskaźnik do liczby całkowitej [cor_prf_code_info —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) struktury dostępne.</span><span class="sxs-lookup"><span data-stu-id="0c1ba-109">[out] A pointer to the total number of [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structures available.</span></span>  
  
 `codeInfos`  
 <span data-ttu-id="0c1ba-110">[out] Bufor dostarczane przez obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="0c1ba-110">[out] A caller-provided buffer.</span></span> <span data-ttu-id="0c1ba-111">Po powrocie z metody zawiera tablicę `COR_PRF_CODE_INFO` struktur, z których każdy zawiera opis bloku kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="0c1ba-111">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c1ba-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0c1ba-112">Remarks</span></span>  
 <span data-ttu-id="0c1ba-113">`GetCodeInfo3` Metoda jest podobna do [getcodeinfo2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md), chyba że uzyska ponownie skompilowana JIT identyfikator funkcji, która zawiera określony adres IP.</span><span class="sxs-lookup"><span data-stu-id="0c1ba-113">The `GetCodeInfo3` method is similar to [GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md), except that it will get the JIT-recompiled ID of the function that contains the specified IP address.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0c1ba-114">`GetCodeInfo3` Możesz wyzwolić wyrzucania elementów bezużytecznych, natomiast [getcodeinfo2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) nie będzie.</span><span class="sxs-lookup"><span data-stu-id="0c1ba-114">`GetCodeInfo3` can trigger a garbage collection, whereas [GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) will not.</span></span> <span data-ttu-id="0c1ba-115">Aby uzyskać więcej informacji, zobacz [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md) HRESULT.</span><span class="sxs-lookup"><span data-stu-id="0c1ba-115">For more information, see the [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md) HRESULT.</span></span>  
  
 <span data-ttu-id="0c1ba-116">Zakresy są sortowane w celu zwiększenia przesunięcie wspólny język pośredni (CIL).</span><span class="sxs-lookup"><span data-stu-id="0c1ba-116">The extents are sorted in order of increasing Common Intermediate Language (CIL) offset.</span></span>  
  
 <span data-ttu-id="0c1ba-117">Po `GetCodeInfo3` zwróci wartość, należy sprawdzić, czy `codeInfos` bufor jest wystarczająco duży, aby zawierała wszystkich [cor_prf_code_info —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="0c1ba-117">After `GetCodeInfo3` returns, you must verify that the `codeInfos` buffer was large enough to contain all the [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structures.</span></span> <span data-ttu-id="0c1ba-118">Aby to zrobić, porównanie wartości `cCodeInfos` z wartością `cchName` parametru.</span><span class="sxs-lookup"><span data-stu-id="0c1ba-118">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="0c1ba-119">Jeśli `cCodeInfos` podzielonej przez rozmiar [cor_prf_code_info —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) struktury jest mniejszy niż `pcCodeInfos`, Przydziel większego `codeInfos` buforu, zaktualizuj `cCodeInfos` przy użyciu nowych, większy rozmiar, a wywołanie `GetCodeInfo3` ponownie.</span><span class="sxs-lookup"><span data-stu-id="0c1ba-119">If `cCodeInfos` divided by the size of a [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo3` again.</span></span>  
  
 <span data-ttu-id="0c1ba-120">Alternatywnie, można wywołać `GetCodeInfo3` o zerowej długości `codeInfos` buforu w celu uzyskania rozmiar buforu poprawne.</span><span class="sxs-lookup"><span data-stu-id="0c1ba-120">Alternatively, you can first call `GetCodeInfo3` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="0c1ba-121">Następnie można ustawić `codeInfos` rozmiar do wartości zwracanej w buforu `pcCodeInfos`, pomnożone przez rozmiar [cor_prf_code_info —](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) struktury i wywołania `GetCodeInfo3` ponownie.</span><span class="sxs-lookup"><span data-stu-id="0c1ba-121">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structure, and call `GetCodeInfo3` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c1ba-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0c1ba-122">Requirements</span></span>  
 <span data-ttu-id="0c1ba-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c1ba-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c1ba-124">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0c1ba-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0c1ba-125">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0c1ba-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0c1ba-126">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c1ba-126">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c1ba-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0c1ba-127">See also</span></span>

- [<span data-ttu-id="0c1ba-128">GetCodeInfo2, metoda</span><span class="sxs-lookup"><span data-stu-id="0c1ba-128">GetCodeInfo2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)
- [<span data-ttu-id="0c1ba-129">ICorProfilerInfo4, interfejs</span><span class="sxs-lookup"><span data-stu-id="0c1ba-129">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="0c1ba-130">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="0c1ba-130">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="0c1ba-131">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="0c1ba-131">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)

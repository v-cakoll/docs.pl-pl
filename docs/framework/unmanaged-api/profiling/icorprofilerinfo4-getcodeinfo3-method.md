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
ms.openlocfilehash: d29145a9c224a064cf9210c56c8617d99f7690ba
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443063"
---
# <a name="icorprofilerinfo4getcodeinfo3-method"></a><span data-ttu-id="f13b7-102">ICorProfilerInfo4::GetCodeInfo3 — Metoda</span><span class="sxs-lookup"><span data-stu-id="f13b7-102">ICorProfilerInfo4::GetCodeInfo3 Method</span></span>
<span data-ttu-id="f13b7-103">Pobiera zakresy kodu natywnego skojarzone z rekompilowaną ponownie wersją określonej funkcji JIT.</span><span class="sxs-lookup"><span data-stu-id="f13b7-103">Gets the extents of native code associated with the JIT-recompiled version of the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f13b7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f13b7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeInfo3(  
    [in]  FunctionID functionID,  
    [in]  ReJITID reJitId,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f13b7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f13b7-105">Parameters</span></span>  
 `functionID`  
 <span data-ttu-id="f13b7-106">podczas Identyfikator funkcji, z którą jest skojarzony kod natywny.</span><span class="sxs-lookup"><span data-stu-id="f13b7-106">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `reJitId`  
 <span data-ttu-id="f13b7-107">podczas Tożsamość funkcji ponownie skompilowanej JIT.</span><span class="sxs-lookup"><span data-stu-id="f13b7-107">[in] The identity of the JIT-recompiled function.</span></span>  
  
 `cCodeInfos`  
 <span data-ttu-id="f13b7-108">podczas Rozmiar tablicy `codeInfos`.</span><span class="sxs-lookup"><span data-stu-id="f13b7-108">[in] The size of the `codeInfos` array.</span></span>  
  
 `pcCodeInfos`  
 <span data-ttu-id="f13b7-109">określoną Wskaźnik do łącznej liczby dostępnych struktur [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="f13b7-109">[out] A pointer to the total number of [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structures available.</span></span>  
  
 `codeInfos`  
 <span data-ttu-id="f13b7-110">określoną Bufor dostarczony przez wywołującego.</span><span class="sxs-lookup"><span data-stu-id="f13b7-110">[out] A caller-provided buffer.</span></span> <span data-ttu-id="f13b7-111">Po powrocie metody zawiera tablicę struktur `COR_PRF_CODE_INFO`, z których każdy opisuje blok kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="f13b7-111">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f13b7-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f13b7-112">Remarks</span></span>  
 <span data-ttu-id="f13b7-113">Metoda `GetCodeInfo3` jest podobna do [GetCodeInfo2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md), z tą różnicą, że otrzyma identyfikator funkcji JIT ponownie, która zawiera określony adres IP.</span><span class="sxs-lookup"><span data-stu-id="f13b7-113">The `GetCodeInfo3` method is similar to [GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md), except that it will get the JIT-recompiled ID of the function that contains the specified IP address.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f13b7-114">`GetCodeInfo3` może wyzwolić wyrzucanie elementów bezużytecznych, natomiast [GetCodeInfo2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) nie będzie.</span><span class="sxs-lookup"><span data-stu-id="f13b7-114">`GetCodeInfo3` can trigger a garbage collection, whereas [GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) will not.</span></span> <span data-ttu-id="f13b7-115">Aby uzyskać więcej informacji, zobacz [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md) HRESULT.</span><span class="sxs-lookup"><span data-stu-id="f13b7-115">For more information, see the [CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](../../../../docs/framework/unmanaged-api/profiling/corprof-e-unsupported-call-sequence-hresult.md) HRESULT.</span></span>  
  
 <span data-ttu-id="f13b7-116">Zakresy są sortowane w kolejności rosnącego, typowego przesunięcia języka pośredniego (CIL).</span><span class="sxs-lookup"><span data-stu-id="f13b7-116">The extents are sorted in order of increasing Common Intermediate Language (CIL) offset.</span></span>  
  
 <span data-ttu-id="f13b7-117">Po powrocie `GetCodeInfo3` należy sprawdzić, czy bufor `codeInfos` był wystarczająco duży, aby zawierał wszystkie struktury [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="f13b7-117">After `GetCodeInfo3` returns, you must verify that the `codeInfos` buffer was large enough to contain all the [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structures.</span></span> <span data-ttu-id="f13b7-118">W tym celu należy porównać wartość `cCodeInfos` z wartością parametru `cchName`.</span><span class="sxs-lookup"><span data-stu-id="f13b7-118">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="f13b7-119">Jeśli `cCodeInfos` podzielona przez rozmiar struktury [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) jest mniejsza niż `pcCodeInfos`, Przydziel większy bufor `codeInfos`, zaktualizuj `cCodeInfos` z nowym, większym rozmiarem i ponownie wywołaj `GetCodeInfo3`.</span><span class="sxs-lookup"><span data-stu-id="f13b7-119">If `cCodeInfos` divided by the size of a [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo3` again.</span></span>  
  
 <span data-ttu-id="f13b7-120">Alternatywnie można najpierw wywołać `GetCodeInfo3` z buforem `codeInfos` o zerowej długości, aby uzyskać prawidłowy rozmiar buforu.</span><span class="sxs-lookup"><span data-stu-id="f13b7-120">Alternatively, you can first call `GetCodeInfo3` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="f13b7-121">Następnie można ustawić `codeInfos` rozmiar buforu na wartość zwróconą w `pcCodeInfos`, pomnożoną przez rozmiar struktury [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) i ponownie wywołać `GetCodeInfo3`.</span><span class="sxs-lookup"><span data-stu-id="f13b7-121">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a [COR_PRF_CODE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-code-info-structure.md) structure, and call `GetCodeInfo3` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f13b7-122">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f13b7-122">Requirements</span></span>  
 <span data-ttu-id="f13b7-123">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f13b7-123">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f13b7-124">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f13b7-124">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f13b7-125">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f13b7-125">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f13b7-126">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f13b7-126">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f13b7-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f13b7-127">See also</span></span>

- [<span data-ttu-id="f13b7-128">GetCodeInfo2, metoda</span><span class="sxs-lookup"><span data-stu-id="f13b7-128">GetCodeInfo2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md)
- [<span data-ttu-id="f13b7-129">ICorProfilerInfo4, interfejs</span><span class="sxs-lookup"><span data-stu-id="f13b7-129">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="f13b7-130">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="f13b7-130">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="f13b7-131">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="f13b7-131">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)

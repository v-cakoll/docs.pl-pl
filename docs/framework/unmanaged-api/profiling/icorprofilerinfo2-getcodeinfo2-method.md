---
title: ICorProfilerInfo2::GetCodeInfo2 — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetCodeInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetCodeInfo2
helpviewer_keywords:
- ICorProfilerInfo2::GetCodeInfo2 method [.NET Framework profiling]
- GetCodeInfo2 method [.NET Framework profiling]
ms.assetid: 532da6ee-7f0a-401b-a61e-fc47ec235d2e
topic_type:
- apiref
ms.openlocfilehash: 9295ea8b22f72529f55cbe13f6a79a0aa34d2fa0
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868799"
---
# <a name="icorprofilerinfo2getcodeinfo2-method"></a><span data-ttu-id="87e8e-102">ICorProfilerInfo2::GetCodeInfo2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="87e8e-102">ICorProfilerInfo2::GetCodeInfo2 Method</span></span>
<span data-ttu-id="87e8e-103">Pobiera zakresy kodu natywnego powiązane z określonym `FunctionID`.</span><span class="sxs-lookup"><span data-stu-id="87e8e-103">Gets the extents of native code associated with the specified `FunctionID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87e8e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="87e8e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeInfo2(  
    [in]  FunctionID functionID,  
    [in]  ULONG32 cCodeInfos,  
    [out] ULONG32 *pcCodeInfos,  
    [out, size_is(cCodeInfos), length_is(*pcCodeInfos)]  
    COR_PRF_CODE_INFO codeInfos[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="87e8e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="87e8e-105">Parameters</span></span>  
 `functionID`  
 <span data-ttu-id="87e8e-106">podczas Identyfikator funkcji, z którą jest skojarzony kod natywny.</span><span class="sxs-lookup"><span data-stu-id="87e8e-106">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `cCodeInfos`  
 <span data-ttu-id="87e8e-107">podczas Rozmiar tablicy `codeInfos`.</span><span class="sxs-lookup"><span data-stu-id="87e8e-107">[in] The size of the `codeInfos` array.</span></span>  
  
 `pcCodeInfos`  
 <span data-ttu-id="87e8e-108">określoną Wskaźnik do łącznej liczby dostępnych struktur [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="87e8e-108">[out] A pointer to the total number of [COR_PRF_CODE_INFO](cor-prf-code-info-structure.md) structures available.</span></span>  
  
 `codeInfos`  
 <span data-ttu-id="87e8e-109">określoną Bufor dostarczony przez wywołującego.</span><span class="sxs-lookup"><span data-stu-id="87e8e-109">[out] A caller-provided buffer.</span></span> <span data-ttu-id="87e8e-110">Po powrocie metody zawiera tablicę struktur `COR_PRF_CODE_INFO`, z których każdy opisuje blok kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="87e8e-110">After the method returns, it contains an array of `COR_PRF_CODE_INFO` structures, each of which describes a block of native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="87e8e-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="87e8e-111">Remarks</span></span>  
 <span data-ttu-id="87e8e-112">Zakresy są sortowane w kolejności rosnącego przesunięcia języka pośredniego firmy Microsoft (MSIL).</span><span class="sxs-lookup"><span data-stu-id="87e8e-112">The extents are sorted in order of increasing Microsoft intermediate language (MSIL) offset.</span></span>  
  
 <span data-ttu-id="87e8e-113">Po powrocie `GetCodeInfo2` należy sprawdzić, czy bufor `codeInfos` był wystarczająco duży, aby zawierał wszystkie struktury `COR_PRF_CODE_INFO`.</span><span class="sxs-lookup"><span data-stu-id="87e8e-113">After `GetCodeInfo2` returns, you must verify that the `codeInfos` buffer was large enough to contain all the `COR_PRF_CODE_INFO` structures.</span></span> <span data-ttu-id="87e8e-114">W tym celu należy porównać wartość `cCodeInfos` z wartością parametru `cchName`.</span><span class="sxs-lookup"><span data-stu-id="87e8e-114">To do this, compare the value of `cCodeInfos` with the value of the `cchName` parameter.</span></span> <span data-ttu-id="87e8e-115">Jeśli `cCodeInfos` podzielona przez rozmiar struktury `COR_PRF_CODE_INFO` jest mniejsza niż `pcCodeInfos`, Przydziel większy bufor `codeInfos`, zaktualizuj `cCodeInfos` z nowym, większym rozmiarem i ponownie wywołaj `GetCodeInfo2`.</span><span class="sxs-lookup"><span data-stu-id="87e8e-115">If `cCodeInfos` divided by the size of a `COR_PRF_CODE_INFO` structure is smaller than `pcCodeInfos`, allocate a larger `codeInfos` buffer, update `cCodeInfos` with the new, larger size, and call `GetCodeInfo2` again.</span></span>  
  
 <span data-ttu-id="87e8e-116">Alternatywnie można najpierw wywołać `GetCodeInfo2` z buforem `codeInfos` o zerowej długości, aby uzyskać prawidłowy rozmiar buforu.</span><span class="sxs-lookup"><span data-stu-id="87e8e-116">Alternatively, you can first call `GetCodeInfo2` with a zero-length `codeInfos` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="87e8e-117">Następnie można ustawić `codeInfos` rozmiar buforu na wartość zwróconą w `pcCodeInfos`, pomnożoną przez rozmiar struktury `COR_PRF_CODE_INFO` i ponownie wywołać `GetCodeInfo2`.</span><span class="sxs-lookup"><span data-stu-id="87e8e-117">You can then set the `codeInfos` buffer size to the value returned in `pcCodeInfos`, multiplied by the size of a `COR_PRF_CODE_INFO` structure, and call `GetCodeInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87e8e-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="87e8e-118">Requirements</span></span>  
 <span data-ttu-id="87e8e-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87e8e-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87e8e-120">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="87e8e-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="87e8e-121">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="87e8e-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="87e8e-122">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87e8e-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87e8e-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="87e8e-123">See also</span></span>

- [<span data-ttu-id="87e8e-124">GetCodeInfo3, metoda</span><span class="sxs-lookup"><span data-stu-id="87e8e-124">GetCodeInfo3 Method</span></span>](icorprofilerinfo4-getcodeinfo3-method.md)
- [<span data-ttu-id="87e8e-125">ICorProfilerInfo2, interfejs</span><span class="sxs-lookup"><span data-stu-id="87e8e-125">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
- [<span data-ttu-id="87e8e-126">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="87e8e-126">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="87e8e-127">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="87e8e-127">Profiling</span></span>](index.md)

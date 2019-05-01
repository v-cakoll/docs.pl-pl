---
title: ICorProfilerInfo::GetCodeInfo — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetCodeInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetCodeInfo
helpviewer_keywords:
- GetCodeInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetCodeInfo method [.NET Framework profiling]
ms.assetid: 90140b0f-a926-4a7e-b6fa-23e05f703cce
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1d069446ecb0b630870f0d2c9c4bdc23232c40c6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991890"
---
# <a name="icorprofilerinfogetcodeinfo-method"></a><span data-ttu-id="c55c9-102">ICorProfilerInfo::GetCodeInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="c55c9-102">ICorProfilerInfo::GetCodeInfo Method</span></span>
<span data-ttu-id="c55c9-103">Pobiera zakres kodu natywnego skojarzony z identyfikatorem określonej funkcji.</span><span class="sxs-lookup"><span data-stu-id="c55c9-103">Gets the extent of native code associated with the specified function ID.</span></span>  
  
 <span data-ttu-id="c55c9-104">Ta metoda jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="c55c9-104">This method is obsolete.</span></span> <span data-ttu-id="c55c9-105">Użyj [icorprofilerinfo2::getcodeinfo2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="c55c9-105">Use the [ICorProfilerInfo2::GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c55c9-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="c55c9-106">Syntax</span></span>  
  
```  
HRESULT GetCodeInfo(  
    [in]  FunctionID functionId,  
    [out] LPCBYTE    *pStart,  
    [out] ULONG      *pcSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c55c9-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="c55c9-107">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="c55c9-108">[in] Identyfikator funkcji, z którą jest skojarzony kod macierzysty.</span><span class="sxs-lookup"><span data-stu-id="c55c9-108">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `pStart`  
 <span data-ttu-id="c55c9-109">[out] Wskaźnik do tablicy bajtów, które tworzą natywny kod funkcji.</span><span class="sxs-lookup"><span data-stu-id="c55c9-109">[out] A pointer to an array of bytes that compose the native code of the function.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="c55c9-110">[out] Wskaźnik na liczbę całkowitą, która określa rozmiar w bajtach, kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="c55c9-110">[out] A pointer to an integer that specifies the size, in bytes, of the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c55c9-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c55c9-111">Remarks</span></span>  
 <span data-ttu-id="c55c9-112">Aby zoptymalizować wydajność, środowiska uruchomieniowego w .NET Framework w wersji 2.0 dzieli wstępnie skompilowanych, natywny kod funkcji w wielu regionach.</span><span class="sxs-lookup"><span data-stu-id="c55c9-112">To optimize performance, the runtime in the .NET Framework version 2.0 splits the precompiled, native code of a function into multiple regions.</span></span> <span data-ttu-id="c55c9-113">W związku z tym `GetCodeInfo` metoda jest przestarzała w programie .NET Framework 2.0, ponieważ jest nie może obsłużyć zakresu funkcji kodu macierzystego.</span><span class="sxs-lookup"><span data-stu-id="c55c9-113">Consequently, the `GetCodeInfo` method is obsolete in the .NET Framework 2.0 because it is unable to handle the extent of a function's native code.</span></span> <span data-ttu-id="c55c9-114">Profilerzy powinni przełączyć się na użycie bardziej ogólnej `ICorProfilerInfo2::GetCodeInfo2` metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="c55c9-114">Profilers should switch to using the more general `ICorProfilerInfo2::GetCodeInfo2` method instead.</span></span>  
  
 <span data-ttu-id="c55c9-115">Ta funkcja używa bufory przypisane do obiektu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="c55c9-115">This function uses caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c55c9-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c55c9-116">Requirements</span></span>  
 <span data-ttu-id="c55c9-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c55c9-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c55c9-118">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c55c9-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c55c9-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c55c9-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c55c9-120">**Wersje programu .NET framework:** 1.0</span><span class="sxs-lookup"><span data-stu-id="c55c9-120">**.NET Framework Versions:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c55c9-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c55c9-121">See also</span></span>

- [<span data-ttu-id="c55c9-122">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="c55c9-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="c55c9-123">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="c55c9-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="c55c9-124">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="c55c9-124">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)

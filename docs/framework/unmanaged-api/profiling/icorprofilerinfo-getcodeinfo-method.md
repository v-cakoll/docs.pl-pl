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
ms.openlocfilehash: 583189cd667af142ab7d0934be34411644dac936
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863923"
---
# <a name="icorprofilerinfogetcodeinfo-method"></a><span data-ttu-id="f6515-102">ICorProfilerInfo::GetCodeInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="f6515-102">ICorProfilerInfo::GetCodeInfo Method</span></span>
<span data-ttu-id="f6515-103">Pobiera zakres kodu natywnego skojarzonego z określonym IDENTYFIKATORem funkcji.</span><span class="sxs-lookup"><span data-stu-id="f6515-103">Gets the extent of native code associated with the specified function ID.</span></span>  
  
 <span data-ttu-id="f6515-104">Ta metoda jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="f6515-104">This method is obsolete.</span></span> <span data-ttu-id="f6515-105">Zamiast tego użyj metody [ICorProfilerInfo2:: GetCodeInfo2 —](icorprofilerinfo2-getcodeinfo2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="f6515-105">Use the [ICorProfilerInfo2::GetCodeInfo2](icorprofilerinfo2-getcodeinfo2-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f6515-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="f6515-106">Syntax</span></span>  
  
```cpp  
HRESULT GetCodeInfo(  
    [in]  FunctionID functionId,  
    [out] LPCBYTE    *pStart,  
    [out] ULONG      *pcSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f6515-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="f6515-107">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="f6515-108">podczas Identyfikator funkcji, z którą jest skojarzony kod natywny.</span><span class="sxs-lookup"><span data-stu-id="f6515-108">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `pStart`  
 <span data-ttu-id="f6515-109">określoną Wskaźnik do tablicy bajtów składających się na kod natywny funkcji.</span><span class="sxs-lookup"><span data-stu-id="f6515-109">[out] A pointer to an array of bytes that compose the native code of the function.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="f6515-110">określoną Wskaźnik do liczby całkowitej, która określa rozmiar (w bajtach) kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="f6515-110">[out] A pointer to an integer that specifies the size, in bytes, of the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f6515-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f6515-111">Remarks</span></span>  
 <span data-ttu-id="f6515-112">Aby zoptymalizować wydajność, środowisko uruchomieniowe w .NET Framework w wersji 2,0 dzieli wstępnie skompilowany kod natywny funkcji na wiele regionów.</span><span class="sxs-lookup"><span data-stu-id="f6515-112">To optimize performance, the runtime in the .NET Framework version 2.0 splits the precompiled, native code of a function into multiple regions.</span></span> <span data-ttu-id="f6515-113">W związku z tym Metoda `GetCodeInfo` jest przestarzała w .NET Framework 2,0, ponieważ nie jest w stanie obsłużyć zakresu kodu natywnego funkcji.</span><span class="sxs-lookup"><span data-stu-id="f6515-113">Consequently, the `GetCodeInfo` method is obsolete in the .NET Framework 2.0 because it is unable to handle the extent of a function's native code.</span></span> <span data-ttu-id="f6515-114">Program do zaprogramowania powinien zamiast tego używać bardziej ogólnej metody `ICorProfilerInfo2::GetCodeInfo2`.</span><span class="sxs-lookup"><span data-stu-id="f6515-114">Profilers should switch to using the more general `ICorProfilerInfo2::GetCodeInfo2` method instead.</span></span>  
  
 <span data-ttu-id="f6515-115">Ta funkcja używa buforów przyznanych przez obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="f6515-115">This function uses caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f6515-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f6515-116">Requirements</span></span>  
 <span data-ttu-id="f6515-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f6515-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f6515-118">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f6515-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f6515-119">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f6515-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f6515-120">**.NET Framework wersje:** 1,0</span><span class="sxs-lookup"><span data-stu-id="f6515-120">**.NET Framework Versions:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f6515-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f6515-121">See also</span></span>

- [<span data-ttu-id="f6515-122">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="f6515-122">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="f6515-123">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="f6515-123">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="f6515-124">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="f6515-124">Profiling</span></span>](index.md)

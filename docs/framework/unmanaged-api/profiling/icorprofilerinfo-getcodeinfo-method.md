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
ms.openlocfilehash: 21dc937bef2bbe197a5dc4af72ff50dff64dbbbd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33454146"
---
# <a name="icorprofilerinfogetcodeinfo-method"></a><span data-ttu-id="45d36-102">ICorProfilerInfo::GetCodeInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="45d36-102">ICorProfilerInfo::GetCodeInfo Method</span></span>
<span data-ttu-id="45d36-103">Pobiera zakres skojarzony z identyfikatorem. określona funkcja kodu natywnego</span><span class="sxs-lookup"><span data-stu-id="45d36-103">Gets the extent of native code associated with the specified function ID.</span></span>  
  
 <span data-ttu-id="45d36-104">Ta metoda jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="45d36-104">This method is obsolete.</span></span> <span data-ttu-id="45d36-105">Użyj [ICorProfilerInfo2::GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="45d36-105">Use the [ICorProfilerInfo2::GetCodeInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getcodeinfo2-method.md) method instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45d36-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="45d36-106">Syntax</span></span>  
  
```  
HRESULT GetCodeInfo(  
    [in]  FunctionID functionId,  
    [out] LPCBYTE    *pStart,  
    [out] ULONG      *pcSize);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="45d36-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="45d36-107">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="45d36-108">[in] Identyfikator funkcji, z którym jest skojarzona kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="45d36-108">[in] The ID of the function with which the native code is associated.</span></span>  
  
 `pStart`  
 <span data-ttu-id="45d36-109">[out] Wskaźnik do tablicy bajtów, które tworzą kodu natywnego funkcji.</span><span class="sxs-lookup"><span data-stu-id="45d36-109">[out] A pointer to an array of bytes that compose the native code of the function.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="45d36-110">[out] Wskaźnik do liczba całkowita określająca rozmiar w bajtach kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="45d36-110">[out] A pointer to an integer that specifies the size, in bytes, of the native code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45d36-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="45d36-111">Remarks</span></span>  
 <span data-ttu-id="45d36-112">Aby zoptymalizować wydajność, środowiska uruchomieniowego w programie .NET Framework w wersji 2.0 dzieli prekompilowany natywnego kodu funkcji na wielu regionach.</span><span class="sxs-lookup"><span data-stu-id="45d36-112">To optimize performance, the runtime in the .NET Framework version 2.0 splits the precompiled, native code of a function into multiple regions.</span></span> <span data-ttu-id="45d36-113">W rezultacie `GetCodeInfo` metoda jest przestarzałe w programie .NET Framework 2.0, ponieważ nie jest w stanie obsłużyć w zakresie funkcji kodu natywnego.</span><span class="sxs-lookup"><span data-stu-id="45d36-113">Consequently, the `GetCodeInfo` method is obsolete in the .NET Framework 2.0 because it is unable to handle the extent of a function's native code.</span></span> <span data-ttu-id="45d36-114">Profilery powinien rozpocząć korzystanie z bardziej ogólnym `ICorProfilerInfo2::GetCodeInfo2` metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="45d36-114">Profilers should switch to using the more general `ICorProfilerInfo2::GetCodeInfo2` method instead.</span></span>  
  
 <span data-ttu-id="45d36-115">Ta funkcja korzysta buforów przydzielone przez obiekt wywołujący.</span><span class="sxs-lookup"><span data-stu-id="45d36-115">This function uses caller-allocated buffers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="45d36-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="45d36-116">Requirements</span></span>  
 <span data-ttu-id="45d36-117">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="45d36-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="45d36-118">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="45d36-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="45d36-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="45d36-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="45d36-120">**Wersje programu .NET framework:** 1.0</span><span class="sxs-lookup"><span data-stu-id="45d36-120">**.NET Framework Versions:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="45d36-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="45d36-121">See Also</span></span>  
 [<span data-ttu-id="45d36-122">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="45d36-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="45d36-123">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="45d36-123">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="45d36-124">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="45d36-124">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)

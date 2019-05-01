---
title: ICorProfilerInfo::BeginInprocDebugging — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.BeginInprocDebugging
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::BeginInprocDebugging
helpviewer_keywords:
- BeginInprocDebugging method [.NET Framework profiling]
- ICorProfilerInfo::BeginInprocDebugging method [.NET Framework profiling]
ms.assetid: c5c82c69-99f8-4447-aee0-42cca0a5eb5c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f12442eb5596ff3dca49cf24e27040f3e92d3a7c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61991929"
---
# <a name="icorprofilerinfobegininprocdebugging-method"></a><span data-ttu-id="88f68-102">ICorProfilerInfo::BeginInprocDebugging — Metoda</span><span class="sxs-lookup"><span data-stu-id="88f68-102">ICorProfilerInfo::BeginInprocDebugging Method</span></span>
<span data-ttu-id="88f68-103">Inicjuje obsługę debugowania w procesie.</span><span class="sxs-lookup"><span data-stu-id="88f68-103">Initializes in-process debugging support.</span></span> <span data-ttu-id="88f68-104">Ta metoda jest przestarzała w programie .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="88f68-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88f68-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="88f68-105">Syntax</span></span>  
  
```  
HRESULT BeginInprocDebugging(  
    [in]  BOOL   fThisThreadOnly,  
    [out] DWORD *pdwProfilerContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="88f68-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="88f68-106">Parameters</span></span>  
 `fThisThreadOnly`  
 <span data-ttu-id="88f68-107">[in] Ustaw tę wartość na `true` zainicjować obsługę debugowania tylko bieżącego wątku; ustaw ją na `false` zainicjować obsługę debugowania dla wszystkich wątków.</span><span class="sxs-lookup"><span data-stu-id="88f68-107">[in] Set this value to `true` to initialize debugging support for only the current thread; set it to `false` to initialize debugging support for all threads.</span></span>  
  
 `pdwProfilerContext`  
 <span data-ttu-id="88f68-108">[out] Wskaźnik do zwrócona wartość, która identyfikuje sesji debugowania.</span><span class="sxs-lookup"><span data-stu-id="88f68-108">[out] The pointer to a returned value that identifies the debugging session.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="88f68-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="88f68-109">Remarks</span></span>  
 <span data-ttu-id="88f68-110">Usług debugowania środowiska CLR obsługiwane, debugowanie wewnątrzprocesowe ograniczone w .NET Framework w wersji 1.0 i 1.1.</span><span class="sxs-lookup"><span data-stu-id="88f68-110">The CLR debugging services supported limited in-process debugging in the .NET Framework versions 1.0 and 1.1.</span></span> <span data-ttu-id="88f68-111">Debugowanie w trakcie włączone program profilujący do użycia inspekcji części interfejsie API debugowania.</span><span class="sxs-lookup"><span data-stu-id="88f68-111">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="88f68-112">Jednak ze względu na opinie klientów, debugowanie wewnątrzprocesowe ma zostały usunięte z programu .NET Framework w wersji 2.0 i zastąpione zestawem funkcji, która jest tworzone są profilowania API.</span><span class="sxs-lookup"><span data-stu-id="88f68-112">However, due to customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88f68-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="88f68-113">Requirements</span></span>  
 <span data-ttu-id="88f68-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88f68-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88f68-115">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="88f68-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="88f68-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="88f68-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="88f68-117">**Wersja programu .NET framework:** 1.0</span><span class="sxs-lookup"><span data-stu-id="88f68-117">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88f68-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="88f68-118">See also</span></span>

- [<span data-ttu-id="88f68-119">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="88f68-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)

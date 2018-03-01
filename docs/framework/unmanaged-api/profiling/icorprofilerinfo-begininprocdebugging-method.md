---
title: "ICorProfilerInfo::BeginInprocDebugging — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 91306bbea7b099f7e9e408f8bf69625f1d7da68e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfobegininprocdebugging-method"></a><span data-ttu-id="64f82-102">ICorProfilerInfo::BeginInprocDebugging — Metoda</span><span class="sxs-lookup"><span data-stu-id="64f82-102">ICorProfilerInfo::BeginInprocDebugging Method</span></span>
<span data-ttu-id="64f82-103">Inicjuje obsługę debugowania w procesie.</span><span class="sxs-lookup"><span data-stu-id="64f82-103">Initializes in-process debugging support.</span></span> <span data-ttu-id="64f82-104">Ta metoda jest przestarzała w programie .NET Framework w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="64f82-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="64f82-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="64f82-105">Syntax</span></span>  
  
```  
HRESULT BeginInprocDebugging(  
    [in]  BOOL   fThisThreadOnly,  
    [out] DWORD *pdwProfilerContext);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="64f82-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="64f82-106">Parameters</span></span>  
 `fThisThreadOnly`  
 <span data-ttu-id="64f82-107">[in] Ta wartość `true` zainicjować obsługę debugowania tylko bieżącego wątku; ustaw ją na `false` zainicjować obsługę debugowania dla wszystkich wątków.</span><span class="sxs-lookup"><span data-stu-id="64f82-107">[in] Set this value to `true` to initialize debugging support for only the current thread; set it to `false` to initialize debugging support for all threads.</span></span>  
  
 `pdwProfilerContext`  
 <span data-ttu-id="64f82-108">[out] Wskaźnik do zwrócona wartość, która identyfikuje sesji debugowania.</span><span class="sxs-lookup"><span data-stu-id="64f82-108">[out] The pointer to a returned value that identifies the debugging session.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="64f82-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="64f82-109">Remarks</span></span>  
 <span data-ttu-id="64f82-110">Usług debugowania środowiska CLR obsługiwane ograniczony w trakcie debugowania w wersji systemu .NET Framework 1.0 i 1.1.</span><span class="sxs-lookup"><span data-stu-id="64f82-110">The CLR debugging services supported limited in-process debugging in the .NET Framework versions 1.0 and 1.1.</span></span> <span data-ttu-id="64f82-111">Debugowanie w trakcie włączone profiler do używania kontroli części interfejsu API debugowania.</span><span class="sxs-lookup"><span data-stu-id="64f82-111">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="64f82-112">Jednak ze względu na opinie klientów, w trakcie debugowania ma został usunięty z programu .NET Framework w wersji 2.0 i zastąpione zestaw funkcji, która jest zgodna z interfejsu API profilowania.</span><span class="sxs-lookup"><span data-stu-id="64f82-112">However, due to customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="64f82-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="64f82-113">Requirements</span></span>  
 <span data-ttu-id="64f82-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="64f82-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="64f82-115">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="64f82-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="64f82-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="64f82-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="64f82-117">**Wersja platformy .NET framework:** 1.0</span><span class="sxs-lookup"><span data-stu-id="64f82-117">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="64f82-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="64f82-118">See Also</span></span>  
 [<span data-ttu-id="64f82-119">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="64f82-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)

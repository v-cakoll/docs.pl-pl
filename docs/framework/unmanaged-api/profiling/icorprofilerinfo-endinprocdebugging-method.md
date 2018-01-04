---
title: "ICorProfilerInfo::EndInprocDebugging — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.EndInprocDebugging
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::EndInprocDebugging
helpviewer_keywords:
- ICorProfilerInfo::EndInprocDebugging method [.NET Framework profiling]
- EndInprocDebugging method [.NET Framework profiling]
ms.assetid: 35bc1188-9767-4141-8038-60ea015b99ac
topic_type: apiref
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a36c557d9ab2fa661808aa2f0be942d11ea9fa61
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfoendinprocdebugging-method"></a><span data-ttu-id="dda0c-102">ICorProfilerInfo::EndInprocDebugging — Metoda</span><span class="sxs-lookup"><span data-stu-id="dda0c-102">ICorProfilerInfo::EndInprocDebugging Method</span></span>
<span data-ttu-id="dda0c-103">Zamyka w trakcie sesji debugowania.</span><span class="sxs-lookup"><span data-stu-id="dda0c-103">Shuts down an in-process debugging session.</span></span> <span data-ttu-id="dda0c-104">Ta metoda jest przestarzała w programie .NET Framework w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="dda0c-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dda0c-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="dda0c-105">Syntax</span></span>  
  
```  
HRESULT EndInprocDebugging(  
    [in]  DWORD dwProfilerContext);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dda0c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="dda0c-106">Parameters</span></span>  
 `dwProfilerContext`  
 <span data-ttu-id="dda0c-107">[in] Wartość, która identyfikuje sesji debugowania.</span><span class="sxs-lookup"><span data-stu-id="dda0c-107">[in] A value that identifies the debugging session.</span></span> <span data-ttu-id="dda0c-108">Ta wartość musi być taka sama, jak została odebrana w [ICorProfilerInfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="dda0c-108">This value must be the same as that received in the [ICorProfilerInfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="dda0c-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dda0c-109">Remarks</span></span>  
 <span data-ttu-id="dda0c-110">Należy wywołać [ICorProfilerInfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) i `EndInprocDebugging` w ramach tej samej metody wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="dda0c-110">You must call [ICorProfilerInfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) and `EndInprocDebugging` within the same callback method.</span></span>  
  
 <span data-ttu-id="dda0c-111">Usług debugowania środowiska CLR obsługiwane ograniczony w trakcie debugowania w wersji systemu .NET Framework 1.0 i 1.1.</span><span class="sxs-lookup"><span data-stu-id="dda0c-111">The CLR debugging services supported limited in-process debugging in the .NET Framework versions 1.0 and 1.1.</span></span> <span data-ttu-id="dda0c-112">Debugowanie w trakcie włączone profiler do używania kontroli części interfejsu API debugowania.</span><span class="sxs-lookup"><span data-stu-id="dda0c-112">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="dda0c-113">Jednak ze względu na opinie klientów, w trakcie debugowania ma został usunięty z programu .NET Framework w wersji 2.0 i zastąpione zestaw funkcji, która jest zgodna z interfejsu API profilowania.</span><span class="sxs-lookup"><span data-stu-id="dda0c-113">However, due to customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dda0c-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dda0c-114">Requirements</span></span>  
 <span data-ttu-id="dda0c-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dda0c-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dda0c-116">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="dda0c-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dda0c-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dda0c-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dda0c-118">**Wersja platformy .NET framework:** 1.0</span><span class="sxs-lookup"><span data-stu-id="dda0c-118">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dda0c-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dda0c-119">See Also</span></span>  
 [<span data-ttu-id="dda0c-120">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="dda0c-120">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)

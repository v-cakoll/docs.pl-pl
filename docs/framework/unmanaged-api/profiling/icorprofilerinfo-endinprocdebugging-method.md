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
ms.openlocfilehash: 6e87cf210fb2717379e6bdc0b687028d680fe624
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfoendinprocdebugging-method"></a><span data-ttu-id="346c3-102">ICorProfilerInfo::EndInprocDebugging — Metoda</span><span class="sxs-lookup"><span data-stu-id="346c3-102">ICorProfilerInfo::EndInprocDebugging Method</span></span>
<span data-ttu-id="346c3-103">Zamyka w trakcie sesji debugowania.</span><span class="sxs-lookup"><span data-stu-id="346c3-103">Shuts down an in-process debugging session.</span></span> <span data-ttu-id="346c3-104">Ta metoda jest przestarzała w programie .NET Framework w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="346c3-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="346c3-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="346c3-105">Syntax</span></span>  
  
```  
HRESULT EndInprocDebugging(  
    [in]  DWORD dwProfilerContext);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="346c3-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="346c3-106">Parameters</span></span>  
 `dwProfilerContext`  
 <span data-ttu-id="346c3-107">[in] Wartość, która identyfikuje sesji debugowania.</span><span class="sxs-lookup"><span data-stu-id="346c3-107">[in] A value that identifies the debugging session.</span></span> <span data-ttu-id="346c3-108">Ta wartość musi być taka sama, jak została odebrana w [ICorProfilerInfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="346c3-108">This value must be the same as that received in the [ICorProfilerInfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="346c3-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="346c3-109">Remarks</span></span>  
 <span data-ttu-id="346c3-110">Należy wywołać [ICorProfilerInfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) i `EndInprocDebugging` w ramach tej samej metody wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="346c3-110">You must call [ICorProfilerInfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) and `EndInprocDebugging` within the same callback method.</span></span>  
  
 <span data-ttu-id="346c3-111">Usług debugowania środowiska CLR obsługiwane ograniczony w trakcie debugowania w wersji systemu .NET Framework 1.0 i 1.1.</span><span class="sxs-lookup"><span data-stu-id="346c3-111">The CLR debugging services supported limited in-process debugging in the .NET Framework versions 1.0 and 1.1.</span></span> <span data-ttu-id="346c3-112">Debugowanie w trakcie włączone profiler do używania kontroli części interfejsu API debugowania.</span><span class="sxs-lookup"><span data-stu-id="346c3-112">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="346c3-113">Jednak ze względu na opinie klientów, w trakcie debugowania ma został usunięty z programu .NET Framework w wersji 2.0 i zastąpione zestaw funkcji, która jest zgodna z interfejsu API profilowania.</span><span class="sxs-lookup"><span data-stu-id="346c3-113">However, due to customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="346c3-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="346c3-114">Requirements</span></span>  
 <span data-ttu-id="346c3-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="346c3-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="346c3-116">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="346c3-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="346c3-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="346c3-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="346c3-118">**Wersja platformy .NET framework:** 1.0</span><span class="sxs-lookup"><span data-stu-id="346c3-118">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="346c3-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="346c3-119">See Also</span></span>  
 [<span data-ttu-id="346c3-120">ICorProfilerInfo — interfejs</span><span class="sxs-lookup"><span data-stu-id="346c3-120">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)

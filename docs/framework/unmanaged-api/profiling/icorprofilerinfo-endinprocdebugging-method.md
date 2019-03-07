---
title: ICorProfilerInfo::EndInprocDebugging — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.EndInprocDebugging
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::EndInprocDebugging
helpviewer_keywords:
- ICorProfilerInfo::EndInprocDebugging method [.NET Framework profiling]
- EndInprocDebugging method [.NET Framework profiling]
ms.assetid: 35bc1188-9767-4141-8038-60ea015b99ac
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f86c680a10a3dcb1009b4f0cedd777ab9da5ac1f
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57501750"
---
# <a name="icorprofilerinfoendinprocdebugging-method"></a><span data-ttu-id="cead8-102">ICorProfilerInfo::EndInprocDebugging — Metoda</span><span class="sxs-lookup"><span data-stu-id="cead8-102">ICorProfilerInfo::EndInprocDebugging Method</span></span>
<span data-ttu-id="cead8-103">Zamyka w trakcie sesji debugowania.</span><span class="sxs-lookup"><span data-stu-id="cead8-103">Shuts down an in-process debugging session.</span></span> <span data-ttu-id="cead8-104">Ta metoda jest przestarzała w programie .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="cead8-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cead8-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="cead8-105">Syntax</span></span>  
  
```  
HRESULT EndInprocDebugging(  
    [in]  DWORD dwProfilerContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cead8-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="cead8-106">Parameters</span></span>  
 `dwProfilerContext`  
 <span data-ttu-id="cead8-107">[in] Wartość, która identyfikuje sesji debugowania.</span><span class="sxs-lookup"><span data-stu-id="cead8-107">[in] A value that identifies the debugging session.</span></span> <span data-ttu-id="cead8-108">Ta wartość musi być taka sama jak trafiła [icorprofilerinfo::BeginInprocDebugging —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="cead8-108">This value must be the same as that received in the [ICorProfilerInfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cead8-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cead8-109">Remarks</span></span>  
 <span data-ttu-id="cead8-110">Należy wywołać [icorprofilerinfo::BeginInprocDebugging —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) i `EndInprocDebugging` w ramach tej samej metody wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="cead8-110">You must call [ICorProfilerInfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) and `EndInprocDebugging` within the same callback method.</span></span>  
  
 <span data-ttu-id="cead8-111">Usług debugowania środowiska CLR obsługiwane, debugowanie wewnątrzprocesowe ograniczone w .NET Framework w wersji 1.0 i 1.1.</span><span class="sxs-lookup"><span data-stu-id="cead8-111">The CLR debugging services supported limited in-process debugging in the .NET Framework versions 1.0 and 1.1.</span></span> <span data-ttu-id="cead8-112">Debugowanie w trakcie włączone program profilujący do użycia inspekcji części interfejsie API debugowania.</span><span class="sxs-lookup"><span data-stu-id="cead8-112">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="cead8-113">Jednak ze względu na opinie klientów, debugowanie wewnątrzprocesowe ma zostały usunięte z programu .NET Framework w wersji 2.0 i zastąpione zestawem funkcji, która jest tworzone są profilowania API.</span><span class="sxs-lookup"><span data-stu-id="cead8-113">However, due to customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cead8-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cead8-114">Requirements</span></span>  
 <span data-ttu-id="cead8-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cead8-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cead8-116">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cead8-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cead8-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cead8-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cead8-118">**Wersja programu .NET framework:** 1.0</span><span class="sxs-lookup"><span data-stu-id="cead8-118">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cead8-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cead8-119">See also</span></span>
- [<span data-ttu-id="cead8-120">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="cead8-120">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)

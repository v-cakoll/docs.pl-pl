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
ms.openlocfilehash: bcae66fd30c29a0a3c9bd0b5ffc2047efdf3788d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62049664"
---
# <a name="icorprofilerinfoendinprocdebugging-method"></a><span data-ttu-id="b3a44-102">ICorProfilerInfo::EndInprocDebugging — Metoda</span><span class="sxs-lookup"><span data-stu-id="b3a44-102">ICorProfilerInfo::EndInprocDebugging Method</span></span>
<span data-ttu-id="b3a44-103">Zamyka w trakcie sesji debugowania.</span><span class="sxs-lookup"><span data-stu-id="b3a44-103">Shuts down an in-process debugging session.</span></span> <span data-ttu-id="b3a44-104">Ta metoda jest przestarzała w programie .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="b3a44-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3a44-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="b3a44-105">Syntax</span></span>  
  
```  
HRESULT EndInprocDebugging(  
    [in]  DWORD dwProfilerContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b3a44-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="b3a44-106">Parameters</span></span>  
 `dwProfilerContext`  
 <span data-ttu-id="b3a44-107">[in] Wartość, która identyfikuje sesji debugowania.</span><span class="sxs-lookup"><span data-stu-id="b3a44-107">[in] A value that identifies the debugging session.</span></span> <span data-ttu-id="b3a44-108">Ta wartość musi być taka sama jak trafiła [icorprofilerinfo::BeginInprocDebugging —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="b3a44-108">This value must be the same as that received in the [ICorProfilerInfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b3a44-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b3a44-109">Remarks</span></span>  
 <span data-ttu-id="b3a44-110">Należy wywołać [icorprofilerinfo::BeginInprocDebugging —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) i `EndInprocDebugging` w ramach tej samej metody wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="b3a44-110">You must call [ICorProfilerInfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) and `EndInprocDebugging` within the same callback method.</span></span>  
  
 <span data-ttu-id="b3a44-111">Usług debugowania środowiska CLR obsługiwane, debugowanie wewnątrzprocesowe ograniczone w .NET Framework w wersji 1.0 i 1.1.</span><span class="sxs-lookup"><span data-stu-id="b3a44-111">The CLR debugging services supported limited in-process debugging in the .NET Framework versions 1.0 and 1.1.</span></span> <span data-ttu-id="b3a44-112">Debugowanie w trakcie włączone program profilujący do użycia inspekcji części interfejsie API debugowania.</span><span class="sxs-lookup"><span data-stu-id="b3a44-112">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="b3a44-113">Jednak ze względu na opinie klientów, debugowanie wewnątrzprocesowe ma zostały usunięte z programu .NET Framework w wersji 2.0 i zastąpione zestawem funkcji, która jest tworzone są profilowania API.</span><span class="sxs-lookup"><span data-stu-id="b3a44-113">However, due to customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3a44-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b3a44-114">Requirements</span></span>  
 <span data-ttu-id="b3a44-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3a44-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3a44-116">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b3a44-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b3a44-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b3a44-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b3a44-118">**Wersja programu .NET framework:** 1.0</span><span class="sxs-lookup"><span data-stu-id="b3a44-118">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3a44-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b3a44-119">See also</span></span>

- [<span data-ttu-id="b3a44-120">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="b3a44-120">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)

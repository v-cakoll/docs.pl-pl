---
title: ICorProfilerInfo::GetInprocInspectionIThisThread — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetInprocInspectionIThisThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetInprocInspectionIThisThread
helpviewer_keywords:
- ICorProfilerInfo::GetInprocInspectionIThisThread method [.NET Framework profiling]
- GetInprocInspectionIThisThread method [.NET Framework profiling]
ms.assetid: badddccd-f85c-416e-9f0f-419eab2c9d42
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 24b7af4b44d51da06e9d65104f1b469ef1d83b8a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59219437"
---
# <a name="icorprofilerinfogetinprocinspectionithisthread-method"></a><span data-ttu-id="5d457-102">ICorProfilerInfo::GetInprocInspectionIThisThread — Metoda</span><span class="sxs-lookup"><span data-stu-id="5d457-102">ICorProfilerInfo::GetInprocInspectionIThisThread Method</span></span>
<span data-ttu-id="5d457-103">Pobiera obiekt, który może być odpytywany icordebugthread — interfejs.</span><span class="sxs-lookup"><span data-stu-id="5d457-103">Gets an object that can be queried for the ICorDebugThread interface.</span></span> <span data-ttu-id="5d457-104">Ta metoda jest przestarzała w programie .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="5d457-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d457-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="5d457-105">Syntax</span></span>  
  
```  
HRESULT GetInprocInspectionIThisThread(  
    [out] IUnknown **ppicd);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5d457-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5d457-106">Parameters</span></span>  
 `ppicd`  
 <span data-ttu-id="5d457-107">[limit](/cpp/atl/iunknown) obiektu, który może być odpytywany dla `ICorDebugThread` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="5d457-107">[out](/cpp/atl/iunknown) object that can be queried for the `ICorDebugThread` interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5d457-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5d457-108">Remarks</span></span>  
 <span data-ttu-id="5d457-109">Środowisko uruchomieniowe języka wspólnego (CLR) debugowanie usług obsługiwane ograniczone w trakcie debugowania w .NET Framework w wersji 1.0.</span><span class="sxs-lookup"><span data-stu-id="5d457-109">The common language runtime (CLR) debugging services supported limited in-process debugging in the .NET Framework version 1.0.</span></span> <span data-ttu-id="5d457-110">Debugowanie w trakcie włączone program profilujący do użycia inspekcji części interfejsie API debugowania.</span><span class="sxs-lookup"><span data-stu-id="5d457-110">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="5d457-111">W wyniku opinie klientów debugowanie wewnątrzprocesowe został usunięty z programu .NET Framework w wersji 2.0 i zastąpione zestawem funkcji, która jest tworzone są profilowania API.</span><span class="sxs-lookup"><span data-stu-id="5d457-111">As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d457-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5d457-112">Requirements</span></span>  
 <span data-ttu-id="5d457-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d457-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d457-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5d457-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5d457-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5d457-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5d457-116">**Wersja programu .NET framework:** 1.0</span><span class="sxs-lookup"><span data-stu-id="5d457-116">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d457-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5d457-117">See also</span></span>

- [<span data-ttu-id="5d457-118">ICorProfilerInfo — Interfejs</span><span class="sxs-lookup"><span data-stu-id="5d457-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)

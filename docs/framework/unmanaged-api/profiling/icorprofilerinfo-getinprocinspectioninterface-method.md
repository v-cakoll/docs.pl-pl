---
title: ICorProfilerInfo::GetInprocInspectionInterface — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetInprocInspectionInterface
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetInprocInspectionInterface
helpviewer_keywords:
- GetInprocInspectionInterface method [.NET Framework profiling]
- ICorProfilerInfo::GetInprocInspectionInterface method [.NET Framework profiling]
ms.assetid: 22a92d1d-8849-4af6-8304-ecc53dd1d289
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fbb4aa43757df86037d9c883e76ee38cef5eeb86
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494431"
---
# <a name="icorprofilerinfogetinprocinspectioninterface-method"></a><span data-ttu-id="c012c-102">ICorProfilerInfo::GetInprocInspectionInterface — Metoda</span><span class="sxs-lookup"><span data-stu-id="c012c-102">ICorProfilerInfo::GetInprocInspectionInterface Method</span></span>
<span data-ttu-id="c012c-103">Pobiera obiekt, który może być odpytywany dla interfejsu "ICorDebugProcess".</span><span class="sxs-lookup"><span data-stu-id="c012c-103">Gets an object that can be queried for an "ICorDebugProcess" interface.</span></span> <span data-ttu-id="c012c-104">Ta metoda jest przestarzała w programie .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="c012c-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c012c-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="c012c-105">Syntax</span></span>  
  
```  
HRESULT GetInprocInspectionInterface(  
    [out] IUnknown **ppicd);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c012c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c012c-106">Parameters</span></span>  
 `ppicd`  
 <span data-ttu-id="c012c-107">[limit](/cpp/atl/iunknown) obiektu, który może być odpytywany dla `ICorDebugProcess` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="c012c-107">[out](/cpp/atl/iunknown) object that can be queried for an `ICorDebugProcess` interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c012c-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c012c-108">Remarks</span></span>  
 <span data-ttu-id="c012c-109">Środowisko uruchomieniowe języka wspólnego (CLR) profilowanie API obsługiwane ograniczone w trakcie debugowania w .NET Framework w wersji 1.0.</span><span class="sxs-lookup"><span data-stu-id="c012c-109">The common language runtime (CLR) debugging API supported limited in-process debugging in the .NET Framework version 1.0.</span></span> <span data-ttu-id="c012c-110">Debugowanie w trakcie włączone program profilujący do użycia inspekcji części interfejsie API debugowania.</span><span class="sxs-lookup"><span data-stu-id="c012c-110">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="c012c-111">W wyniku opinie klientów debugowanie wewnątrzprocesowe został usunięty z programu .NET Framework w wersji 2.0 i zastąpione zestawem funkcji, która jest tworzone są profilowania API.</span><span class="sxs-lookup"><span data-stu-id="c012c-111">As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c012c-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c012c-112">Requirements</span></span>  
 <span data-ttu-id="c012c-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c012c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c012c-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c012c-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c012c-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c012c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c012c-116">**Wersja programu .NET framework:** 1.0</span><span class="sxs-lookup"><span data-stu-id="c012c-116">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c012c-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c012c-117">See also</span></span>
- [<span data-ttu-id="c012c-118">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="c012c-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)

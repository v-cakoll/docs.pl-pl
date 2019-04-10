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
ms.openlocfilehash: 456dd8aedf11b1b27ee4926988fc615ebb7a76d8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59209934"
---
# <a name="icorprofilerinfogetinprocinspectioninterface-method"></a><span data-ttu-id="5009e-102">ICorProfilerInfo::GetInprocInspectionInterface — Metoda</span><span class="sxs-lookup"><span data-stu-id="5009e-102">ICorProfilerInfo::GetInprocInspectionInterface Method</span></span>
<span data-ttu-id="5009e-103">Pobiera obiekt, który może być odpytywany dla interfejsu "ICorDebugProcess".</span><span class="sxs-lookup"><span data-stu-id="5009e-103">Gets an object that can be queried for an "ICorDebugProcess" interface.</span></span> <span data-ttu-id="5009e-104">Ta metoda jest przestarzała w programie .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="5009e-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5009e-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="5009e-105">Syntax</span></span>  
  
```  
HRESULT GetInprocInspectionInterface(  
    [out] IUnknown **ppicd);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5009e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5009e-106">Parameters</span></span>  
 `ppicd`  
 <span data-ttu-id="5009e-107">[limit](/cpp/atl/iunknown) obiektu, który może być odpytywany dla `ICorDebugProcess` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="5009e-107">[out](/cpp/atl/iunknown) object that can be queried for an `ICorDebugProcess` interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5009e-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5009e-108">Remarks</span></span>  
 <span data-ttu-id="5009e-109">Środowisko uruchomieniowe języka wspólnego (CLR) profilowanie API obsługiwane ograniczone w trakcie debugowania w .NET Framework w wersji 1.0.</span><span class="sxs-lookup"><span data-stu-id="5009e-109">The common language runtime (CLR) debugging API supported limited in-process debugging in the .NET Framework version 1.0.</span></span> <span data-ttu-id="5009e-110">Debugowanie w trakcie włączone program profilujący do użycia inspekcji części interfejsie API debugowania.</span><span class="sxs-lookup"><span data-stu-id="5009e-110">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="5009e-111">W wyniku opinie klientów debugowanie wewnątrzprocesowe został usunięty z programu .NET Framework w wersji 2.0 i zastąpione zestawem funkcji, która jest tworzone są profilowania API.</span><span class="sxs-lookup"><span data-stu-id="5009e-111">As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5009e-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5009e-112">Requirements</span></span>  
 <span data-ttu-id="5009e-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5009e-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5009e-114">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5009e-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5009e-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5009e-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5009e-116">**Wersja programu .NET framework:** 1.0</span><span class="sxs-lookup"><span data-stu-id="5009e-116">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5009e-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5009e-117">See also</span></span>

- [<span data-ttu-id="5009e-118">ICorProfilerInfo — Interfejs</span><span class="sxs-lookup"><span data-stu-id="5009e-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)

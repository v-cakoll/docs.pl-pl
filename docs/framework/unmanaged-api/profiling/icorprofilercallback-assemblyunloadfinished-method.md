---
title: "ICorProfilerCallback::AssemblyUnloadFinished — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.AssemblyUnloadFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::AssemblyUnloadFinished
helpviewer_keywords:
- AssemblyUnloadFinished method [.NET Framework profiling]
- ICorProfilerCallback::AssemblyUnloadFinished method [.NET Framework profiling]
ms.assetid: 53fca564-84b1-44d4-9e21-17a492d2aae7
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ead41718e0253de599019112178d64c0ab706924
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilercallbackassemblyunloadfinished-method"></a><span data-ttu-id="788a9-102">ICorProfilerCallback::AssemblyUnloadFinished — Metoda</span><span class="sxs-lookup"><span data-stu-id="788a9-102">ICorProfilerCallback::AssemblyUnloadFinished Method</span></span>
<span data-ttu-id="788a9-103">Powiadamia profilera, że zestaw został usunięty z pamięci.</span><span class="sxs-lookup"><span data-stu-id="788a9-103">Notifies the profiler that an assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="788a9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="788a9-104">Syntax</span></span>  
  
```  
HRESULT AssemblyUnloadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="788a9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="788a9-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="788a9-106">[in] Określa zestaw, który jest zwalniany.</span><span class="sxs-lookup"><span data-stu-id="788a9-106">[in] Identifies the assembly that is being unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="788a9-107">[in] HRESULT, która wskazuje, czy zestaw został pomyślnie usunięty z pamięci.</span><span class="sxs-lookup"><span data-stu-id="788a9-107">[in] An HRESULT that indicates whether the assembly was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="788a9-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="788a9-108">Remarks</span></span>  
 <span data-ttu-id="788a9-109">Wartość `assemblyId` jest nieprawidłowa dla żądania informacji po [ICorProfilerCallback::AssemblyUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md) zwraca metody.</span><span class="sxs-lookup"><span data-stu-id="788a9-109">The value of `assemblyId` is not valid for an information request after the [ICorProfilerCallback::AssemblyUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="788a9-110">Niektórych części zwalnianie zestaw może kontynuować po `AssemblyUnloadFinished` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="788a9-110">Some parts of unloading the assembly might continue after the `AssemblyUnloadFinished` callback.</span></span> <span data-ttu-id="788a9-111">Błąd HRESULT w `hrStatus` oznacza błąd.</span><span class="sxs-lookup"><span data-stu-id="788a9-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="788a9-112">Jednak Powodzenie HRESULT w `hrStatus` tylko wskazuje, że pierwsza część zwalnianie zestawu zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="788a9-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="788a9-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="788a9-113">Requirements</span></span>  
 <span data-ttu-id="788a9-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="788a9-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="788a9-115">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="788a9-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="788a9-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="788a9-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="788a9-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="788a9-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="788a9-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="788a9-118">See Also</span></span>  
 [<span data-ttu-id="788a9-119">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="788a9-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)

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
ms.openlocfilehash: 144f7af59afbb403d9ec1894f06c5c028b767416
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackassemblyunloadfinished-method"></a><span data-ttu-id="f2ed5-102">ICorProfilerCallback::AssemblyUnloadFinished — Metoda</span><span class="sxs-lookup"><span data-stu-id="f2ed5-102">ICorProfilerCallback::AssemblyUnloadFinished Method</span></span>
<span data-ttu-id="f2ed5-103">Powiadamia profilera, że zestaw został usunięty z pamięci.</span><span class="sxs-lookup"><span data-stu-id="f2ed5-103">Notifies the profiler that an assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2ed5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f2ed5-104">Syntax</span></span>  
  
```  
HRESULT AssemblyUnloadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f2ed5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f2ed5-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="f2ed5-106">[in] Określa zestaw, który jest zwalniany.</span><span class="sxs-lookup"><span data-stu-id="f2ed5-106">[in] Identifies the assembly that is being unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="f2ed5-107">[in] HRESULT, która wskazuje, czy zestaw został pomyślnie usunięty z pamięci.</span><span class="sxs-lookup"><span data-stu-id="f2ed5-107">[in] An HRESULT that indicates whether the assembly was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f2ed5-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f2ed5-108">Remarks</span></span>  
 <span data-ttu-id="f2ed5-109">Wartość `assemblyId` jest nieprawidłowa dla żądania informacji po [ICorProfilerCallback::AssemblyUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md) zwraca metody.</span><span class="sxs-lookup"><span data-stu-id="f2ed5-109">The value of `assemblyId` is not valid for an information request after the [ICorProfilerCallback::AssemblyUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="f2ed5-110">Niektórych części zwalnianie zestaw może kontynuować po `AssemblyUnloadFinished` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="f2ed5-110">Some parts of unloading the assembly might continue after the `AssemblyUnloadFinished` callback.</span></span> <span data-ttu-id="f2ed5-111">Błąd HRESULT w `hrStatus` oznacza błąd.</span><span class="sxs-lookup"><span data-stu-id="f2ed5-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="f2ed5-112">Jednak Powodzenie HRESULT w `hrStatus` tylko wskazuje, że pierwsza część zwalnianie zestawu zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="f2ed5-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f2ed5-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f2ed5-113">Requirements</span></span>  
 <span data-ttu-id="f2ed5-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f2ed5-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f2ed5-115">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="f2ed5-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f2ed5-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f2ed5-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f2ed5-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f2ed5-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f2ed5-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f2ed5-118">See Also</span></span>  
 [<span data-ttu-id="f2ed5-119">ICorProfilerCallback — interfejs</span><span class="sxs-lookup"><span data-stu-id="f2ed5-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)

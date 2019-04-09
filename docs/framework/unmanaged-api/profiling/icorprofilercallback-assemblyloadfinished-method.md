---
title: ICorProfilerCallback::AssemblyLoadFinished — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyLoadFinished
helpviewer_keywords:
- ICorProfilerCallback::AssemblyLoadFinished method [.NET Framework profiling]
- AssemblyLoadFinished method [.NET Framework profiling]
ms.assetid: 86d98f39-52e6-4c61-a625-9760f695ff12
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e32af790c755f65b5435455c326d011656da19ed
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59198377"
---
# <a name="icorprofilercallbackassemblyloadfinished-method"></a><span data-ttu-id="c3d94-102">ICorProfilerCallback::AssemblyLoadFinished — Metoda</span><span class="sxs-lookup"><span data-stu-id="c3d94-102">ICorProfilerCallback::AssemblyLoadFinished Method</span></span>
<span data-ttu-id="c3d94-103">Powiadamia program profilujący, że zespół zakończył ładowanie.</span><span class="sxs-lookup"><span data-stu-id="c3d94-103">Notifies the profiler that an assembly has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3d94-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c3d94-104">Syntax</span></span>  
  
```  
HRESULT AssemblyLoadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3d94-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c3d94-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="c3d94-106">[in] Określa zestaw, który został załadowany.</span><span class="sxs-lookup"><span data-stu-id="c3d94-106">[in] Identifies the assembly that was loaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="c3d94-107">[in] Wartość HRESULT, która wskazuje, czy zestaw zakończone pomyślnie ładowania.</span><span class="sxs-lookup"><span data-stu-id="c3d94-107">[in] An HRESULT that indicates whether the assembly finished loading successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3d94-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c3d94-108">Remarks</span></span>  
 <span data-ttu-id="c3d94-109">Wartość `assemblyId` jest nieprawidłowa dla żądania informacje do momentu `AssemblyLoadFinished` metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="c3d94-109">The value of `assemblyId` is not valid for an information request until the `AssemblyLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="c3d94-110">Niektóre części ładowania zestawu może kontynuować po `AssemblyLoadFinished` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="c3d94-110">Some parts of loading the assembly might continue after the `AssemblyLoadFinished` callback.</span></span> <span data-ttu-id="c3d94-111">Błąd HRESULT w `hrStatus` wskazuje błąd.</span><span class="sxs-lookup"><span data-stu-id="c3d94-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="c3d94-112">Jednak sukcesów wartość HRESULT w `hrStatus` tylko wskazuje, czy zakończyła się pomyślnie w pierwszej części ładowania zestawu.</span><span class="sxs-lookup"><span data-stu-id="c3d94-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3d94-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c3d94-113">Requirements</span></span>  
 <span data-ttu-id="c3d94-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3d94-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3d94-115">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c3d94-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c3d94-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c3d94-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="c3d94-117">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="c3d94-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c3d94-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c3d94-118">See also</span></span>

- [<span data-ttu-id="c3d94-119">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="c3d94-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)

---
title: ICorProfilerCallback::AssemblyUnloadFinished — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyUnloadFinished
helpviewer_keywords:
- AssemblyUnloadFinished method [.NET Framework profiling]
- ICorProfilerCallback::AssemblyUnloadFinished method [.NET Framework profiling]
ms.assetid: 53fca564-84b1-44d4-9e21-17a492d2aae7
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b9ee87c926d2377ff8eef53f930fe75251b28ceb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59137777"
---
# <a name="icorprofilercallbackassemblyunloadfinished-method"></a><span data-ttu-id="8af08-102">ICorProfilerCallback::AssemblyUnloadFinished — Metoda</span><span class="sxs-lookup"><span data-stu-id="8af08-102">ICorProfilerCallback::AssemblyUnloadFinished Method</span></span>
<span data-ttu-id="8af08-103">Powiadamia program profilujący, że zestaw został zwolniony.</span><span class="sxs-lookup"><span data-stu-id="8af08-103">Notifies the profiler that an assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8af08-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8af08-104">Syntax</span></span>  
  
```  
HRESULT AssemblyUnloadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8af08-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8af08-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="8af08-106">[in] Identyfikuje zestaw, który jest zwalniany.</span><span class="sxs-lookup"><span data-stu-id="8af08-106">[in] Identifies the assembly that is being unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="8af08-107">[in] Wartość HRESULT, która wskazuje, czy zestaw został pomyślnie usunięty z pamięci.</span><span class="sxs-lookup"><span data-stu-id="8af08-107">[in] An HRESULT that indicates whether the assembly was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8af08-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8af08-108">Remarks</span></span>  
 <span data-ttu-id="8af08-109">Wartość `assemblyId` jest nieprawidłowa dla żądania informacji po [icorprofilercallback::assemblyunloadstarted —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md) metoda zwraca.</span><span class="sxs-lookup"><span data-stu-id="8af08-109">The value of `assemblyId` is not valid for an information request after the [ICorProfilerCallback::AssemblyUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="8af08-110">Niektóre części zwalnianie zestaw może kontynuować po `AssemblyUnloadFinished` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="8af08-110">Some parts of unloading the assembly might continue after the `AssemblyUnloadFinished` callback.</span></span> <span data-ttu-id="8af08-111">Błąd HRESULT w `hrStatus` wskazuje błąd.</span><span class="sxs-lookup"><span data-stu-id="8af08-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="8af08-112">Jednak sukcesów wartość HRESULT w `hrStatus` wskazuje tylko, powiodło się w pierwszej części zwalnianie zestawu.</span><span class="sxs-lookup"><span data-stu-id="8af08-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8af08-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8af08-113">Requirements</span></span>  
 <span data-ttu-id="8af08-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8af08-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8af08-115">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="8af08-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8af08-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8af08-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="8af08-117">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="8af08-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8af08-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8af08-118">See also</span></span>

- [<span data-ttu-id="8af08-119">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="8af08-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)

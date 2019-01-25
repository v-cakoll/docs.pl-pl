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
ms.openlocfilehash: a6a9fe86d6160ebac084625ef94013cce9a27a3d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54501883"
---
# <a name="icorprofilercallbackassemblyunloadfinished-method"></a><span data-ttu-id="5804e-102">ICorProfilerCallback::AssemblyUnloadFinished — Metoda</span><span class="sxs-lookup"><span data-stu-id="5804e-102">ICorProfilerCallback::AssemblyUnloadFinished Method</span></span>
<span data-ttu-id="5804e-103">Powiadamia program profilujący, że zestaw został zwolniony.</span><span class="sxs-lookup"><span data-stu-id="5804e-103">Notifies the profiler that an assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5804e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5804e-104">Syntax</span></span>  
  
```  
HRESULT AssemblyUnloadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="5804e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5804e-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="5804e-106">[in] Identyfikuje zestaw, który jest zwalniany.</span><span class="sxs-lookup"><span data-stu-id="5804e-106">[in] Identifies the assembly that is being unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="5804e-107">[in] Wartość HRESULT, która wskazuje, czy zestaw został pomyślnie usunięty z pamięci.</span><span class="sxs-lookup"><span data-stu-id="5804e-107">[in] An HRESULT that indicates whether the assembly was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5804e-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5804e-108">Remarks</span></span>  
 <span data-ttu-id="5804e-109">Wartość `assemblyId` jest nieprawidłowa dla żądania informacji po [icorprofilercallback::assemblyunloadstarted —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md) metoda zwraca.</span><span class="sxs-lookup"><span data-stu-id="5804e-109">The value of `assemblyId` is not valid for an information request after the [ICorProfilerCallback::AssemblyUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="5804e-110">Niektóre części zwalnianie zestaw może kontynuować po `AssemblyUnloadFinished` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="5804e-110">Some parts of unloading the assembly might continue after the `AssemblyUnloadFinished` callback.</span></span> <span data-ttu-id="5804e-111">Błąd HRESULT w `hrStatus` wskazuje błąd.</span><span class="sxs-lookup"><span data-stu-id="5804e-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="5804e-112">Jednak sukcesów wartość HRESULT w `hrStatus` wskazuje tylko, powiodło się w pierwszej części zwalnianie zestawu.</span><span class="sxs-lookup"><span data-stu-id="5804e-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5804e-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5804e-113">Requirements</span></span>  
 <span data-ttu-id="5804e-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5804e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5804e-115">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5804e-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5804e-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5804e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5804e-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5804e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5804e-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5804e-118">See also</span></span>
- [<span data-ttu-id="5804e-119">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="5804e-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)

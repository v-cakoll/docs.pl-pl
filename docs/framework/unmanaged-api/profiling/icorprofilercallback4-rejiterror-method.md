---
title: ICorProfilerCallback4::ReJITError — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback4.ReJITError
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback4::ReJITError
helpviewer_keywords:
- ReJITError method, ICorProfilerCallback4 interface [.NET Framework profiling]
- ICorProfilerCallback4::ReJITError method [.NET Framework profiling]
ms.assetid: d7888aa9-dfaa-420f-9f99-e06ab35ca482
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ec6472a33c49d9345793d73ac2f78f8896dc218b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilercallback4rejiterror-method"></a><span data-ttu-id="85dc0-102">ICorProfilerCallback4::ReJITError — Metoda</span><span class="sxs-lookup"><span data-stu-id="85dc0-102">ICorProfilerCallback4::ReJITError Method</span></span>
<span data-ttu-id="85dc0-103">Powiadamia profilera, że przy użyciu kompilatora just in time (JIT) napotkał błąd w procesie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="85dc0-103">Notifies the profiler that the just-in-time (JIT) compiler encountered an error in the recompilation process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85dc0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="85dc0-104">Syntax</span></span>  
  
```  
HRESULT ReJITError(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodId,  
    [in] FunctionID  functionId,  
    [in] HRESULT     hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="85dc0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="85dc0-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="85dc0-106">[in] `ModuleID` , W którym nastąpiła próba ponownej kompilacji nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="85dc0-106">[in] The `ModuleID` in which the failed recompilation attempt was made.</span></span>  
  
 `methodId`  
 <span data-ttu-id="85dc0-107">[in] `MethodDef` Metody, na którym została podjęta próba ponownej kompilacji nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="85dc0-107">[in] The `MethodDef` of the method on which the failed recompilation attempt was made.</span></span>  
  
 `functionId`  
 <span data-ttu-id="85dc0-108">[in] Wystąpienie funkcji, które są ponownej kompilacji lub oznaczona do ponownej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="85dc0-108">[in] The function instance that is being recompiled or marked for recompilation.</span></span> <span data-ttu-id="85dc0-109">Ta wartość może być `NULL` Jeśli błąd wystąpił na podstawie-metoda zamiast bazując na wystąpienia (na przykład, jeśli profilera określono token nieprawidłowe metadane dla metody do ponownej kompilacji).</span><span class="sxs-lookup"><span data-stu-id="85dc0-109">This value may be `NULL` if the failure occurred on a per-method basis instead of a per-instantiation basis (for example, if the profiler specified an invalid metadata token for the method to be recompiled).</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="85dc0-110">[in] HRESULT, która wskazuje naturę niepowodzenia.</span><span class="sxs-lookup"><span data-stu-id="85dc0-110">[in] An HRESULT that indicates the nature of the failure.</span></span> <span data-ttu-id="85dc0-111">Zobacz sekcję wyników HRESULT stan listę wartości.</span><span class="sxs-lookup"><span data-stu-id="85dc0-111">See the Status HRESULTS section for a list of values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="85dc0-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="85dc0-112">Return Value</span></span>  
 <span data-ttu-id="85dc0-113">Wartości zwracane z tego wywołania zwrotnego są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="85dc0-113">Return values from this callback are ignored.</span></span>  
  
## <a name="status-hresults"></a><span data-ttu-id="85dc0-114">Stan wyników HRESULT</span><span class="sxs-lookup"><span data-stu-id="85dc0-114">Status HRESULTS</span></span>  
  
|<span data-ttu-id="85dc0-115">Stan tablicy HRESULT</span><span class="sxs-lookup"><span data-stu-id="85dc0-115">Status array HRESULT</span></span>|<span data-ttu-id="85dc0-116">Opis</span><span class="sxs-lookup"><span data-stu-id="85dc0-116">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="85dc0-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="85dc0-117">E_INVALIDARG</span></span>|<span data-ttu-id="85dc0-118">`moduleID` Lub `methodDef` token jest `NULL`.</span><span class="sxs-lookup"><span data-stu-id="85dc0-118">The `moduleID` or `methodDef` token is `NULL`.</span></span>|  
|<span data-ttu-id="85dc0-119">CORPROF_E_DATAINCOMPLETE</span><span class="sxs-lookup"><span data-stu-id="85dc0-119">CORPROF_E_DATAINCOMPLETE</span></span>|<span data-ttu-id="85dc0-120">Moduł nie został jeszcze całkowicie załadowany lub Trwa zwalnianie modułu.</span><span class="sxs-lookup"><span data-stu-id="85dc0-120">The module is not fully loaded yet, or it is in the process of being unloaded.</span></span>|  
|<span data-ttu-id="85dc0-121">CORPROF_E_MODULE_IS_DYNAMIC</span><span class="sxs-lookup"><span data-stu-id="85dc0-121">CORPROF_E_MODULE_IS_DYNAMIC</span></span>|<span data-ttu-id="85dc0-122">Określony moduł został generowane dynamicznie (na przykład przez `Reflection.Emit`) i w związku z tym nie jest obsługiwany przez tę metodę.</span><span class="sxs-lookup"><span data-stu-id="85dc0-122">The specified module was dynamically generated (for example, by `Reflection.Emit`), and is thus not supported by this method.</span></span>|  
|<span data-ttu-id="85dc0-123">CORPROF_E_FUNCTION_IS_COLLECTIBLE</span><span class="sxs-lookup"><span data-stu-id="85dc0-123">CORPROF_E_FUNCTION_IS_COLLECTIBLE</span></span>|<span data-ttu-id="85dc0-124">Metoda zostanie uruchomiony w ramach zestawu kolekcjonowanego i dlatego nie może być ponownie kompilowane.</span><span class="sxs-lookup"><span data-stu-id="85dc0-124">The method is instantiated into a collectible assembly, and is therefore not able to be recompiled.</span></span> <span data-ttu-id="85dc0-125">Należy pamiętać, że typy i funkcje zdefiniowanych w kontekście innych niż odbicia (na przykład `List<MyCollectibleStruct>`) można wdrożyć do zestawu kolekcjonowanego.</span><span class="sxs-lookup"><span data-stu-id="85dc0-125">Note that types and functions defined in a non-reflection context (for example, `List<MyCollectibleStruct>`) can be instantiated into a collectible assembly.</span></span>|  
|<span data-ttu-id="85dc0-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="85dc0-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="85dc0-127">CLR za mało pamięci podczas próby oznaczyć określonej metody dla kompilacji JIT.</span><span class="sxs-lookup"><span data-stu-id="85dc0-127">The CLR ran out of memory while trying to mark the specified method for JIT recompilation.</span></span>|  
|<span data-ttu-id="85dc0-128">Inne</span><span class="sxs-lookup"><span data-stu-id="85dc0-128">Other</span></span>|<span data-ttu-id="85dc0-129">System operacyjny zwrócił błąd poza kontrolą środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="85dc0-129">The operating system returned a failure outside the control of the CLR.</span></span> <span data-ttu-id="85dc0-130">Na przykład jeśli wystąpi błąd wywołania systemu, aby zmienić ustawienia ochrony dostępu do strony pamięci, zostanie wyświetlony błąd systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="85dc0-130">For example, if a system call to change the access protection of a page of memory fails, the operating system error is displayed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="85dc0-131">Wymagania</span><span class="sxs-lookup"><span data-stu-id="85dc0-131">Requirements</span></span>  
 <span data-ttu-id="85dc0-132">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="85dc0-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="85dc0-133">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="85dc0-133">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="85dc0-134">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="85dc0-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="85dc0-135">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="85dc0-135">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85dc0-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="85dc0-136">See Also</span></span>  
 [<span data-ttu-id="85dc0-137">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="85dc0-137">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)  
 [<span data-ttu-id="85dc0-138">ICorProfilerCallback4, interfejs</span><span class="sxs-lookup"><span data-stu-id="85dc0-138">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)

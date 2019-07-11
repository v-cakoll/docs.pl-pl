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
ms.openlocfilehash: 6b01f38fbcf1cb0439b82a933b37971515b06ac4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67758149"
---
# <a name="icorprofilercallback4rejiterror-method"></a><span data-ttu-id="688aa-102">ICorProfilerCallback4::ReJITError — Metoda</span><span class="sxs-lookup"><span data-stu-id="688aa-102">ICorProfilerCallback4::ReJITError Method</span></span>
<span data-ttu-id="688aa-103">Powiadamia program profilujący, że kompilator just-in-time (JIT) napotkał błąd w procesie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="688aa-103">Notifies the profiler that the just-in-time (JIT) compiler encountered an error in the recompilation process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="688aa-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="688aa-104">Syntax</span></span>  
  
```cpp  
HRESULT ReJITError(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodId,  
    [in] FunctionID  functionId,  
    [in] HRESULT     hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="688aa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="688aa-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="688aa-106">[in] `ModuleID` , W której nastąpiła próba ponownej kompilacji nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="688aa-106">[in] The `ModuleID` in which the failed recompilation attempt was made.</span></span>  
  
 `methodId`  
 <span data-ttu-id="688aa-107">[in] `MethodDef` Metody, na którym została podjęta próba ponownej kompilacji nie powiodło się.</span><span class="sxs-lookup"><span data-stu-id="688aa-107">[in] The `MethodDef` of the method on which the failed recompilation attempt was made.</span></span>  
  
 `functionId`  
 <span data-ttu-id="688aa-108">[in] Wystąpienie funkcji, które jest ponownej kompilacji lub oznaczona do ponownej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="688aa-108">[in] The function instance that is being recompiled or marked for recompilation.</span></span> <span data-ttu-id="688aa-109">Ta wartość może być `NULL` czy błąd wystąpił na podstawie-metoda zamiast podstawę dla wystąpienia (na przykład, jeśli program profilujący określony token nieprawidłowe metadane dla metody do ponownej kompilacji).</span><span class="sxs-lookup"><span data-stu-id="688aa-109">This value may be `NULL` if the failure occurred on a per-method basis instead of a per-instantiation basis (for example, if the profiler specified an invalid metadata token for the method to be recompiled).</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="688aa-110">[in] Wartość HRESULT wskazującą naturę niepowodzenia.</span><span class="sxs-lookup"><span data-stu-id="688aa-110">[in] An HRESULT that indicates the nature of the failure.</span></span> <span data-ttu-id="688aa-111">Zobacz sekcję HRESULTS stanu dla listy wartości.</span><span class="sxs-lookup"><span data-stu-id="688aa-111">See the Status HRESULTS section for a list of values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="688aa-112">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="688aa-112">Return Value</span></span>  
 <span data-ttu-id="688aa-113">Wartości zwracane to wywołanie zwrotne są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="688aa-113">Return values from this callback are ignored.</span></span>  
  
## <a name="status-hresults"></a><span data-ttu-id="688aa-114">Stan HRESULTS</span><span class="sxs-lookup"><span data-stu-id="688aa-114">Status HRESULTS</span></span>  
  
|<span data-ttu-id="688aa-115">Stan macierzy HRESULT</span><span class="sxs-lookup"><span data-stu-id="688aa-115">Status array HRESULT</span></span>|<span data-ttu-id="688aa-116">Opis</span><span class="sxs-lookup"><span data-stu-id="688aa-116">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="688aa-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="688aa-117">E_INVALIDARG</span></span>|<span data-ttu-id="688aa-118">`moduleID` Lub `methodDef` token jest `NULL`.</span><span class="sxs-lookup"><span data-stu-id="688aa-118">The `moduleID` or `methodDef` token is `NULL`.</span></span>|  
|<span data-ttu-id="688aa-119">CORPROF_E_DATAINCOMPLETE</span><span class="sxs-lookup"><span data-stu-id="688aa-119">CORPROF_E_DATAINCOMPLETE</span></span>|<span data-ttu-id="688aa-120">Moduł nie jest jeszcze w pełni załadowany lub jest właśnie Trwa zwalnianie.</span><span class="sxs-lookup"><span data-stu-id="688aa-120">The module is not fully loaded yet, or it is in the process of being unloaded.</span></span>|  
|<span data-ttu-id="688aa-121">CORPROF_E_MODULE_IS_DYNAMIC</span><span class="sxs-lookup"><span data-stu-id="688aa-121">CORPROF_E_MODULE_IS_DYNAMIC</span></span>|<span data-ttu-id="688aa-122">Określony moduł dynamicznie został wygenerowany (na przykład przez `Reflection.Emit`), a zatem nie jest obsługiwane przez tę metodę.</span><span class="sxs-lookup"><span data-stu-id="688aa-122">The specified module was dynamically generated (for example, by `Reflection.Emit`), and is thus not supported by this method.</span></span>|  
|<span data-ttu-id="688aa-123">CORPROF_E_FUNCTION_IS_COLLECTIBLE</span><span class="sxs-lookup"><span data-stu-id="688aa-123">CORPROF_E_FUNCTION_IS_COLLECTIBLE</span></span>|<span data-ttu-id="688aa-124">Metoda tworzenia wystąpienia klasy w zestawie i dlatego nie może być ponownie kompilowane.</span><span class="sxs-lookup"><span data-stu-id="688aa-124">The method is instantiated into a collectible assembly, and is therefore not able to be recompiled.</span></span> <span data-ttu-id="688aa-125">Należy zauważyć, że typy i funkcje zdefiniowane w kontekście innych odbicie (na przykład `List<MyCollectibleStruct>`) można utworzyć wystąpienia w zestawie.</span><span class="sxs-lookup"><span data-stu-id="688aa-125">Note that types and functions defined in a non-reflection context (for example, `List<MyCollectibleStruct>`) can be instantiated into a collectible assembly.</span></span>|  
|<span data-ttu-id="688aa-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="688aa-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="688aa-127">Środowisko CLR zabrakło pamięci w trakcie oznaczania określonej metody ponownej kompilacji JIT.</span><span class="sxs-lookup"><span data-stu-id="688aa-127">The CLR ran out of memory while trying to mark the specified method for JIT recompilation.</span></span>|  
|<span data-ttu-id="688aa-128">Inne</span><span class="sxs-lookup"><span data-stu-id="688aa-128">Other</span></span>|<span data-ttu-id="688aa-129">System operacyjny zwrócił błąd poza kontrolą środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="688aa-129">The operating system returned a failure outside the control of the CLR.</span></span> <span data-ttu-id="688aa-130">Na przykład jeśli wywołanie systemowe, aby zmienić ustawienia ochrony dostępu do strony pamięci nie powiedzie się, zostanie wyświetlony błąd systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="688aa-130">For example, if a system call to change the access protection of a page of memory fails, the operating system error is displayed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="688aa-131">Wymagania</span><span class="sxs-lookup"><span data-stu-id="688aa-131">Requirements</span></span>  
 <span data-ttu-id="688aa-132">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="688aa-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="688aa-133">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="688aa-133">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="688aa-134">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="688aa-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="688aa-135">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="688aa-135">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="688aa-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="688aa-136">See also</span></span>

- [<span data-ttu-id="688aa-137">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="688aa-137">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="688aa-138">ICorProfilerCallback4, interfejs</span><span class="sxs-lookup"><span data-stu-id="688aa-138">ICorProfilerCallback4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback4-interface.md)

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
ms.openlocfilehash: 66195ea9df4c8e9ce847b38f7d020a3bebffcd37
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865184"
---
# <a name="icorprofilercallback4rejiterror-method"></a><span data-ttu-id="8b7ca-102">ICorProfilerCallback4::ReJITError — Metoda</span><span class="sxs-lookup"><span data-stu-id="8b7ca-102">ICorProfilerCallback4::ReJITError Method</span></span>
<span data-ttu-id="8b7ca-103">Powiadamia profiler, że kompilator just in Time (JIT) napotkał błąd w procesie ponownej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="8b7ca-103">Notifies the profiler that the just-in-time (JIT) compiler encountered an error in the recompilation process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b7ca-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8b7ca-104">Syntax</span></span>  
  
```cpp  
HRESULT ReJITError(  
    [in] ModuleID    moduleId,  
    [in] mdMethodDef methodId,  
    [in] FunctionID  functionId,  
    [in] HRESULT     hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8b7ca-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8b7ca-105">Parameters</span></span>  
 `moduleID`  
 <span data-ttu-id="8b7ca-106">podczas `ModuleID`, w którym podjęto próbę ponownej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="8b7ca-106">[in] The `ModuleID` in which the failed recompilation attempt was made.</span></span>  
  
 `methodId`  
 <span data-ttu-id="8b7ca-107">podczas `MethodDef` metody, w której podjęto próbę ponownej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="8b7ca-107">[in] The `MethodDef` of the method on which the failed recompilation attempt was made.</span></span>  
  
 `functionId`  
 <span data-ttu-id="8b7ca-108">podczas Wystąpienie funkcji, które jest ponownie kompilowane lub oznaczone do ponownej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="8b7ca-108">[in] The function instance that is being recompiled or marked for recompilation.</span></span> <span data-ttu-id="8b7ca-109">Ta wartość może być `NULL`, jeśli wystąpił błąd w poszczególnych metodach, a nie na podstawie poszczególnych wystąpień (na przykład jeśli Profiler określił nieprawidłowy token metadanych dla metody do ponownego skompilowania).</span><span class="sxs-lookup"><span data-stu-id="8b7ca-109">This value may be `NULL` if the failure occurred on a per-method basis instead of a per-instantiation basis (for example, if the profiler specified an invalid metadata token for the method to be recompiled).</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="8b7ca-110">podczas WYNIK HRESULT wskazujący charakter błędu.</span><span class="sxs-lookup"><span data-stu-id="8b7ca-110">[in] An HRESULT that indicates the nature of the failure.</span></span> <span data-ttu-id="8b7ca-111">Zapoznaj się z sekcją stan HRESULTs, aby zapoznać się z listą wartości.</span><span class="sxs-lookup"><span data-stu-id="8b7ca-111">See the Status HRESULTS section for a list of values.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8b7ca-112">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="8b7ca-112">Return Value</span></span>  
 <span data-ttu-id="8b7ca-113">Zwracane wartości z tego wywołania zwrotnego są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="8b7ca-113">Return values from this callback are ignored.</span></span>  
  
## <a name="status-hresults"></a><span data-ttu-id="8b7ca-114">Stan HRESULT</span><span class="sxs-lookup"><span data-stu-id="8b7ca-114">Status HRESULTS</span></span>  
  
|<span data-ttu-id="8b7ca-115">Wartość HRESULT tablicy stanu</span><span class="sxs-lookup"><span data-stu-id="8b7ca-115">Status array HRESULT</span></span>|<span data-ttu-id="8b7ca-116">Opis</span><span class="sxs-lookup"><span data-stu-id="8b7ca-116">Description</span></span>|  
|--------------------------|-----------------|  
|<span data-ttu-id="8b7ca-117">E_INVALIDARG</span><span class="sxs-lookup"><span data-stu-id="8b7ca-117">E_INVALIDARG</span></span>|<span data-ttu-id="8b7ca-118">`moduleID` lub token `methodDef` jest `NULL`.</span><span class="sxs-lookup"><span data-stu-id="8b7ca-118">The `moduleID` or `methodDef` token is `NULL`.</span></span>|  
|<span data-ttu-id="8b7ca-119">CORPROF_E_DATAINCOMPLETE</span><span class="sxs-lookup"><span data-stu-id="8b7ca-119">CORPROF_E_DATAINCOMPLETE</span></span>|<span data-ttu-id="8b7ca-120">Moduł nie jest jeszcze w pełni załadowany lub jest w trakcie jego zwalniania.</span><span class="sxs-lookup"><span data-stu-id="8b7ca-120">The module is not fully loaded yet, or it is in the process of being unloaded.</span></span>|  
|<span data-ttu-id="8b7ca-121">CORPROF_E_MODULE_IS_DYNAMIC</span><span class="sxs-lookup"><span data-stu-id="8b7ca-121">CORPROF_E_MODULE_IS_DYNAMIC</span></span>|<span data-ttu-id="8b7ca-122">Określony moduł został dynamicznie wygenerowany (na przykład przez `Reflection.Emit`) i nie jest obsługiwany przez tę metodę.</span><span class="sxs-lookup"><span data-stu-id="8b7ca-122">The specified module was dynamically generated (for example, by `Reflection.Emit`), and is thus not supported by this method.</span></span>|  
|<span data-ttu-id="8b7ca-123">CORPROF_E_FUNCTION_IS_COLLECTIBLE</span><span class="sxs-lookup"><span data-stu-id="8b7ca-123">CORPROF_E_FUNCTION_IS_COLLECTIBLE</span></span>|<span data-ttu-id="8b7ca-124">Metoda jest tworzona w zestawie kolekcjonowanym i dlatego nie można jej ponownie skompilować.</span><span class="sxs-lookup"><span data-stu-id="8b7ca-124">The method is instantiated into a collectible assembly, and is therefore not able to be recompiled.</span></span> <span data-ttu-id="8b7ca-125">Należy zauważyć, że typy i funkcje zdefiniowane w kontekście bez odbicia (na przykład `List<MyCollectibleStruct>`) mogą być tworzone w zestawie kolekcjonowanym.</span><span class="sxs-lookup"><span data-stu-id="8b7ca-125">Note that types and functions defined in a non-reflection context (for example, `List<MyCollectibleStruct>`) can be instantiated into a collectible assembly.</span></span>|  
|<span data-ttu-id="8b7ca-126">E_OUTOFMEMORY</span><span class="sxs-lookup"><span data-stu-id="8b7ca-126">E_OUTOFMEMORY</span></span>|<span data-ttu-id="8b7ca-127">Za mało pamięci środowiska CLR podczas próby oznaczenia określonej metody ponownej kompilacji JIT.</span><span class="sxs-lookup"><span data-stu-id="8b7ca-127">The CLR ran out of memory while trying to mark the specified method for JIT recompilation.</span></span>|  
|<span data-ttu-id="8b7ca-128">Inne</span><span class="sxs-lookup"><span data-stu-id="8b7ca-128">Other</span></span>|<span data-ttu-id="8b7ca-129">System operacyjny zwrócił błąd poza kontrolą środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="8b7ca-129">The operating system returned a failure outside the control of the CLR.</span></span> <span data-ttu-id="8b7ca-130">Na przykład, jeśli wywołanie systemowe w celu zmiany ochrony dostępu strony pamięci nie powiedzie się, zostanie wyświetlony komunikat o błędzie systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="8b7ca-130">For example, if a system call to change the access protection of a page of memory fails, the operating system error is displayed.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8b7ca-131">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8b7ca-131">Requirements</span></span>  
 <span data-ttu-id="8b7ca-132">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b7ca-132">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b7ca-133">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="8b7ca-133">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8b7ca-134">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8b7ca-134">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b7ca-135">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b7ca-135">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b7ca-136">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8b7ca-136">See also</span></span>

- [<span data-ttu-id="8b7ca-137">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="8b7ca-137">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="8b7ca-138">ICorProfilerCallback4, interfejs</span><span class="sxs-lookup"><span data-stu-id="8b7ca-138">ICorProfilerCallback4 Interface</span></span>](icorprofilercallback4-interface.md)

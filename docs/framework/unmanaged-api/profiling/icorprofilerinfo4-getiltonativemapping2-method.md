---
title: ICorProfilerInfo4::GetILToNativeMapping2 — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo4.GetILToNativeMapping2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo4::GetILToNativeMapping2
helpviewer_keywords:
- ICorProfilerInfo4::GetILToNativeMapping2 method [.NET Framework profiling]
- GetILToNativeMapping2 method, ICorProfilerInfo4 interface [.NET Framework profiling]
ms.assetid: 756c1c25-08a7-4060-9798-dbeaa2f3bee5
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1b59fe76bd6d8d5887ac825e844e89e85677e2d7
ms.sourcegitcommit: 4735bb7741555bcb870d7b42964d3774f4897a6e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/30/2019
ms.locfileid: "66380350"
---
# <a name="icorprofilerinfo4getiltonativemapping2-method"></a><span data-ttu-id="61a11-102">ICorProfilerInfo4::GetILToNativeMapping2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="61a11-102">ICorProfilerInfo4::GetILToNativeMapping2 Method</span></span>
<span data-ttu-id="61a11-103">Pobiera mapę od firmy Microsoft intermediate language (MSIL) przesuwa się do macierzystych przesunięciach kod zawarty w wersji ponownie skompilowana JIT określonej funkcji.</span><span class="sxs-lookup"><span data-stu-id="61a11-103">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the JIT-recompiled version of the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61a11-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="61a11-104">Syntax</span></span>  
  
```  
HRESULT GetILToNativeMapping(  
    [in] FunctionID functionId,  
    [in] ReJITID reJitId,  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="61a11-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="61a11-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="61a11-106">[in] Identyfikator funkcji, która zawiera kod.</span><span class="sxs-lookup"><span data-stu-id="61a11-106">[in] The ID of the function that contains the code.</span></span>  
  
 `pReJitId`  
 <span data-ttu-id="61a11-107">[in] Tożsamość funkcja ponownie skompilowana JIT.</span><span class="sxs-lookup"><span data-stu-id="61a11-107">[in] The identity of the JIT-recompiled function.</span></span> <span data-ttu-id="61a11-108">Tożsamość musi mieć wartość zero w programie .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="61a11-108">The identity must be zero in the .NET Framework 4.5.</span></span>  
  
 `cMap`  
 <span data-ttu-id="61a11-109">[in] Maksymalny rozmiar `map` tablicy.</span><span class="sxs-lookup"><span data-stu-id="61a11-109">[in] The maximum size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="61a11-110">[out] Całkowita liczba dostępnych struktur cor_debug_il_to_native_map —.</span><span class="sxs-lookup"><span data-stu-id="61a11-110">[out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.</span></span>  
  
 `map`  
 <span data-ttu-id="61a11-111">[out] Tablica `COR_DEBUG_IL_TO_NATIVE_MAP` struktur, z których każdy określa przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="61a11-111">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures, each of which specifies the offsets.</span></span> <span data-ttu-id="61a11-112">Po `GetILToNativeMapping2` metoda zwraca `map` będzie zawierać części lub całości `COR_DEBUG_IL_TO_NATIVE_MAP` struktury.</span><span class="sxs-lookup"><span data-stu-id="61a11-112">After the `GetILToNativeMapping2` method returns, `map` will contain some or all of the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="61a11-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="61a11-113">Remarks</span></span>  
 <span data-ttu-id="61a11-114">`GetILToNativeMapping2` jest podobny do [icorprofilerinfo::getiltonativemapping —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) metody, z tą różnicą, że profiler określić identyfikator funkcji ponownej kompilacji w przyszłości umożliwi wydania.</span><span class="sxs-lookup"><span data-stu-id="61a11-114">`GetILToNativeMapping2` is similar to the [ICorProfilerInfo::GetILToNativeMapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) method, except that it will allow the profiler to specify the ID of the recompiled function in future releases.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="61a11-115">[Icorprofilerfunctioncontrol::setilinstrumentedcodemap —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md) metoda nie jest zaimplementowana w programie .NET Framework 4.5, funkcje, które zostały ponownie skompilowana JIT nie mogą mieć mapowania IL do macierzystego, który różni się od pierwotnie Funkcja skompilowany.</span><span class="sxs-lookup"><span data-stu-id="61a11-115">The [ICorProfilerFunctionControl::SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md) method is not implemented in the .NET Framework 4.5, so functions that have been JIT-recompiled cannot have an IL-to-native mapping that differs from the originally compiled function.</span></span> <span data-ttu-id="61a11-116">W efekcie `GetILToNativeMapping2` nelze volat wartość różną od zera Identyfikatora ponownie skompilowana JIT w .NET Framework 4.5.</span><span class="sxs-lookup"><span data-stu-id="61a11-116">As such, `GetILToNativeMapping2` cannot be called with a nonzero JIT-recompiled ID in the .NET Framework 4.5.</span></span>  
  
 <span data-ttu-id="61a11-117">`GetILToNativeMapping2` Metoda zwraca tablicę `COR_DEBUG_IL_TO_NATIVE_MAP` struktury.</span><span class="sxs-lookup"><span data-stu-id="61a11-117">The `GetILToNativeMapping2` method returns an array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="61a11-118">W celu przekazania, czy określone zakresy natywne instrukcje odpowiadają specjalne regiony kodu (na przykład prologu), mogą mieć wpisu w tablicy jej `ilOffset` pole jest ustawione na wartość [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="61a11-118">To convey that certain ranges of native instructions correspond to special regions of code (for example, the prolog), an entry in the array can have its `ilOffset` field set to a value of the [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="61a11-119">Po `GetILToNativeMapping2` zwróci wartość, należy sprawdzić, czy `map` bufor jest wystarczająco duży, aby zawierała wszystkich `COR_DEBUG_IL_TO_NATIVE_MAP` struktury.</span><span class="sxs-lookup"><span data-stu-id="61a11-119">After `GetILToNativeMapping2` returns, you must verify that the `map` buffer was large enough to contain all the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="61a11-120">Aby to zrobić, porównanie wartości `cMap` z wartością `pcMap` parametru.</span><span class="sxs-lookup"><span data-stu-id="61a11-120">To do this, compare the value of `cMap` with the value of the `pcMap` parameter.</span></span> <span data-ttu-id="61a11-121">Jeśli `pcMap` wartości, gdy jest mnożony przez rozmiar `COR_DEBUG_IL_TO_NATIVE_MAP` struktury, jest większy niż `cMap`, Przydziel większego `map` buforu, zaktualizuj `cMap` przy użyciu nowych, większy rozmiar i Wywołaj `GetILToNativeMapping2` ponownie.</span><span class="sxs-lookup"><span data-stu-id="61a11-121">If the `pcMap` value, when it is multiplied by the size of a `COR_DEBUG_IL_TO_NATIVE_MAP` structure, is larger than `cMap`, allocate a larger `map` buffer, update `cMap` with the new, larger size, and call `GetILToNativeMapping2` again.</span></span>  
  
 <span data-ttu-id="61a11-122">Alternatywnie, można wywołać `GetILToNativeMapping2` o zerowej długości `map` buforu w celu uzyskania rozmiar buforu poprawne.</span><span class="sxs-lookup"><span data-stu-id="61a11-122">Alternatively, you can first call `GetILToNativeMapping2` with a zero-length `map` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="61a11-123">Następnie można ustawić rozmiar buforu do wartości zwracanej w `pcMap` i wywołać `GetILToNativeMapping2` ponownie.</span><span class="sxs-lookup"><span data-stu-id="61a11-123">You can then set the buffer size to the value returned in `pcMap` and call `GetILToNativeMapping2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61a11-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="61a11-124">Requirements</span></span>  
 <span data-ttu-id="61a11-125">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61a11-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61a11-126">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="61a11-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="61a11-127">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="61a11-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="61a11-128">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61a11-128">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61a11-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="61a11-129">See also</span></span>

- [<span data-ttu-id="61a11-130">GetILToNativeMapping, metoda</span><span class="sxs-lookup"><span data-stu-id="61a11-130">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)
- [<span data-ttu-id="61a11-131">ICorProfilerInfo4, interfejs</span><span class="sxs-lookup"><span data-stu-id="61a11-131">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="61a11-132">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="61a11-132">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="61a11-133">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="61a11-133">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)

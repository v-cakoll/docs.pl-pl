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
ms.openlocfilehash: a8ffdb04bdf3fd2f605e2dffc5065a0d786bbaf7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967917"
---
# <a name="icorprofilerinfo4getiltonativemapping2-method"></a><span data-ttu-id="02823-102">ICorProfilerInfo4::GetILToNativeMapping2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="02823-102">ICorProfilerInfo4::GetILToNativeMapping2 Method</span></span>
<span data-ttu-id="02823-103">Pobiera mapę z przesunięcia języka pośredniego firmy Microsoft (MSIL) do natywnych przesunięć dla kodu zawartego w ponownej kompilacji JIT w wersji określonej funkcji.</span><span class="sxs-lookup"><span data-stu-id="02823-103">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the JIT-recompiled version of the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="02823-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="02823-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILToNativeMapping(  
    [in] FunctionID functionId,  
    [in] ReJITID reJitId,  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="02823-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="02823-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="02823-106">podczas Identyfikator funkcji, która zawiera kod.</span><span class="sxs-lookup"><span data-stu-id="02823-106">[in] The ID of the function that contains the code.</span></span>  
  
 `pReJitId`  
 <span data-ttu-id="02823-107">podczas Tożsamość funkcji ponownie skompilowanej JIT.</span><span class="sxs-lookup"><span data-stu-id="02823-107">[in] The identity of the JIT-recompiled function.</span></span> <span data-ttu-id="02823-108">Tożsamość musi być równa zero w .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="02823-108">The identity must be zero in the .NET Framework 4.5.</span></span>  
  
 `cMap`  
 <span data-ttu-id="02823-109">podczas Maksymalny rozmiar `map` tablicy.</span><span class="sxs-lookup"><span data-stu-id="02823-109">[in] The maximum size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="02823-110">określoną Łączna liczba dostępnych struktur COR_DEBUG_IL_TO_NATIVE_MAP.</span><span class="sxs-lookup"><span data-stu-id="02823-110">[out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.</span></span>  
  
 `map`  
 <span data-ttu-id="02823-111">określoną Tablica `COR_DEBUG_IL_TO_NATIVE_MAP` struktur, z których każdy określa przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="02823-111">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures, each of which specifies the offsets.</span></span> <span data-ttu-id="02823-112">Po powrocie `GetILToNativeMapping2` metody `COR_DEBUG_IL_TO_NATIVE_MAP` będzie zawierać niektóre `map` lub wszystkie struktury.</span><span class="sxs-lookup"><span data-stu-id="02823-112">After the `GetILToNativeMapping2` method returns, `map` will contain some or all of the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="02823-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="02823-113">Remarks</span></span>  
 <span data-ttu-id="02823-114">`GetILToNativeMapping2`jest podobna do metody [ICorProfilerInfo:: GetILToNativeMapping —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) , z tą różnicą, że umożliwia profilerowi określenie identyfikatora ponownie skompilowanej funkcji w przyszłych wydaniach.</span><span class="sxs-lookup"><span data-stu-id="02823-114">`GetILToNativeMapping2` is similar to the [ICorProfilerInfo::GetILToNativeMapping](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md) method, except that it will allow the profiler to specify the ID of the recompiled function in future releases.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="02823-115">Metoda [ICorProfilerFunctionControl:: SetILInstrumentedCodeMap —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md) nie jest zaimplementowana w .NET Framework 4,5, dlatego funkcje, które zostały ponownie skompilowane w trybie JIT, nie mogą mieć mapowania Il-to-natywnego, które różni się od pierwotnie skompilowanej funkcji.</span><span class="sxs-lookup"><span data-stu-id="02823-115">The [ICorProfilerFunctionControl::SetILInstrumentedCodeMap](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctioncontrol-setilinstrumentedcodemap-method.md) method is not implemented in the .NET Framework 4.5, so functions that have been JIT-recompiled cannot have an IL-to-native mapping that differs from the originally compiled function.</span></span> <span data-ttu-id="02823-116">W związku z `GetILToNativeMapping2` tym nie można wywołać z niezerowym identyfikatorem ponownej kompilacji JIT w .NET Framework 4,5.</span><span class="sxs-lookup"><span data-stu-id="02823-116">As such, `GetILToNativeMapping2` cannot be called with a nonzero JIT-recompiled ID in the .NET Framework 4.5.</span></span>  
  
 <span data-ttu-id="02823-117">Metoda zwraca tablicę `COR_DEBUG_IL_TO_NATIVE_MAP`struktur. `GetILToNativeMapping2`</span><span class="sxs-lookup"><span data-stu-id="02823-117">The `GetILToNativeMapping2` method returns an array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="02823-118">Aby przekazać, że niektóre zakresy natywnych instrukcji odpowiadają specjalnym regionom kodu (na przykład prologu), wpis w tablicy może mieć `ilOffset` ustawione pole jako wartość wyliczenia [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="02823-118">To convey that certain ranges of native instructions correspond to special regions of code (for example, the prolog), an entry in the array can have its `ilOffset` field set to a value of the [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="02823-119">Po `GetILToNativeMapping2` powrocie należy sprawdzić `map` , czy bufor jest `COR_DEBUG_IL_TO_NATIVE_MAP` wystarczająco duży, aby można było zawierać wszystkie struktury.</span><span class="sxs-lookup"><span data-stu-id="02823-119">After `GetILToNativeMapping2` returns, you must verify that the `map` buffer was large enough to contain all the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="02823-120">W tym celu należy porównać wartość `cMap` z wartością `pcMap` parametru.</span><span class="sxs-lookup"><span data-stu-id="02823-120">To do this, compare the value of `cMap` with the value of the `pcMap` parameter.</span></span> <span data-ttu-id="02823-121">`cMap` `COR_DEBUG_IL_TO_NATIVE_MAP` `GetILToNativeMapping2` `map` `cMap`Jeśli wartość, gdy zostanie pomnożona przez rozmiar struktury, jest większa niż, Przydziel większy bufor, Aktualizuj o nowy, większy rozmiar i ponownie wywołaj. `pcMap`</span><span class="sxs-lookup"><span data-stu-id="02823-121">If the `pcMap` value, when it is multiplied by the size of a `COR_DEBUG_IL_TO_NATIVE_MAP` structure, is larger than `cMap`, allocate a larger `map` buffer, update `cMap` with the new, larger size, and call `GetILToNativeMapping2` again.</span></span>  
  
 <span data-ttu-id="02823-122">Alternatywnie, można najpierw wywołać `GetILToNativeMapping2` z buforem o zerowej długości `map` , aby uzyskać prawidłowy rozmiar buforu.</span><span class="sxs-lookup"><span data-stu-id="02823-122">Alternatively, you can first call `GetILToNativeMapping2` with a zero-length `map` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="02823-123">Następnie można ustawić rozmiar buforu na wartość zwracaną w `pcMap` i ponownie wywołać. `GetILToNativeMapping2`</span><span class="sxs-lookup"><span data-stu-id="02823-123">You can then set the buffer size to the value returned in `pcMap` and call `GetILToNativeMapping2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="02823-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="02823-124">Requirements</span></span>  
 <span data-ttu-id="02823-125">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="02823-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="02823-126">**Nagłówki** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="02823-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="02823-127">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="02823-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="02823-128">**.NET Framework wersje:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="02823-128">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="02823-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="02823-129">See also</span></span>

- [<span data-ttu-id="02823-130">GetILToNativeMapping, metoda</span><span class="sxs-lookup"><span data-stu-id="02823-130">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getiltonativemapping-method.md)
- [<span data-ttu-id="02823-131">ICorProfilerInfo4, interfejs</span><span class="sxs-lookup"><span data-stu-id="02823-131">ICorProfilerInfo4 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-interface.md)
- [<span data-ttu-id="02823-132">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="02823-132">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="02823-133">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="02823-133">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)

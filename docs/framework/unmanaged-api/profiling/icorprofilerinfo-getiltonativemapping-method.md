---
title: "ICorProfilerInfo::GetILToNativeMapping — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerInfo.GetILToNativeMapping
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetILToNativeMapping
helpviewer_keywords:
- GetILToNativeMapping method, ICorProfilerInfo interface [.NET Framework profiling]
- ICorProfilerInfo::GetILToNativeMapping method [.NET Framework profiling]
ms.assetid: 6a5431ef-22fb-4e53-bac5-703986297eb1
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 89ccfcbf69a0d3907ec244d7a214d6f4a5766767
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetiltonativemapping-method"></a><span data-ttu-id="534d7-102">ICorProfilerInfo::GetILToNativeMapping — Metoda</span><span class="sxs-lookup"><span data-stu-id="534d7-102">ICorProfilerInfo::GetILToNativeMapping Method</span></span>
<span data-ttu-id="534d7-103">Pobiera mapy firmy Microsoft do natywnej przesunięć kod źródłowy znajdujący się w określonej funkcji powoduje przesunięcie język pośredni (MSIL).</span><span class="sxs-lookup"><span data-stu-id="534d7-103">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="534d7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="534d7-104">Syntax</span></span>  
  
```  
HRESULT GetILToNativeMapping(  
    [in] FunctionID functionId,  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="534d7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="534d7-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="534d7-106">[in] Identyfikator funkcji, która zawiera kod.</span><span class="sxs-lookup"><span data-stu-id="534d7-106">[in] The ID of the function that contains the code.</span></span>  
  
 `cMap`  
 <span data-ttu-id="534d7-107">[in] Maksymalny rozmiar `map` tablicy.</span><span class="sxs-lookup"><span data-stu-id="534d7-107">[in] The maximum size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="534d7-108">[out] Całkowita liczba dostępnych cor_debug_il_to_native_map — struktury.</span><span class="sxs-lookup"><span data-stu-id="534d7-108">[out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.</span></span>  
  
 `map`  
 <span data-ttu-id="534d7-109">[out] Tablica `COR_DEBUG_IL_TO_NATIVE_MAP` struktury, z których każdy określa przesunięcie.</span><span class="sxs-lookup"><span data-stu-id="534d7-109">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures, each of which specifies the offsets.</span></span> <span data-ttu-id="534d7-110">Po `GetILToNativeMapping` zwraca metoda `map` będzie zawierał niektórych lub wszystkich `COR_DEBUG_IL_TO_NATIVE_MAP` struktury.</span><span class="sxs-lookup"><span data-stu-id="534d7-110">After the `GetILToNativeMapping` method returns, `map` will contain some or all of the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="534d7-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="534d7-111">Remarks</span></span>  
 <span data-ttu-id="534d7-112">`GetILToNativeMapping` Metoda zwraca tablicę `COR_DEBUG_IL_TO_NATIVE_MAP` struktury.</span><span class="sxs-lookup"><span data-stu-id="534d7-112">The `GetILToNativeMapping` method returns an array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="534d7-113">W celu przekazania, że niektórych zakresów instrukcji natywnego odpowiadają specjalne regiony kodu (na przykład prologu), może mieć wpisem w tablicy jego `ilOffset` pole ustawione na wartość [cordebugiltonativemappingtypes —](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="534d7-113">To convey that certain ranges of native instructions correspond to special regions of code (for example, the prolog), an entry in the array can have its `ilOffset` field set to a value of the [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="534d7-114">Po `GetILToNativeMapping` zwróci wartość, należy sprawdzić, czy `map` bufor był wystarczająco duży, aby pomieścić wszystkie `COR_DEBUG_IL_TO_NATIVE_MAP` struktury.</span><span class="sxs-lookup"><span data-stu-id="534d7-114">After `GetILToNativeMapping` returns, you must verify that the `map` buffer was large enough to contain all the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="534d7-115">Aby to zrobić, porównanie wartości `cMap` z wartością `pcMap` parametru.</span><span class="sxs-lookup"><span data-stu-id="534d7-115">To do this, compare the value of `cMap` with the value of the `pcMap` parameter.</span></span> <span data-ttu-id="534d7-116">Jeśli `pcMap` wartość pomnożona przez rozmiar `COR_DEBUG_IL_TO_NATIVE_MAP` struktury, jest większy niż `cMap`, Przydziel większy `map` buforu, zaktualizuj `cMap` z nowej, większy rozmiar i wywołanie `GetILToNativeMapping` ponownie.</span><span class="sxs-lookup"><span data-stu-id="534d7-116">If the `pcMap` value, when it is multiplied by the size of a `COR_DEBUG_IL_TO_NATIVE_MAP` structure, is larger than `cMap`, allocate a larger `map` buffer, update `cMap` with the new, larger size, and call `GetILToNativeMapping` again.</span></span>  
  
 <span data-ttu-id="534d7-117">Alternatywnie można wywołać `GetILToNativeMapping` o zerowej długości `map` buforu w celu uzyskania rozmiar buforu poprawne.</span><span class="sxs-lookup"><span data-stu-id="534d7-117">Alternatively, you can first call `GetILToNativeMapping` with a zero-length `map` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="534d7-118">Rozmiar buforu można następnie ustawić wartość zwracana w `pcMap` i Wywołaj `GetILToNativeMapping` ponownie.</span><span class="sxs-lookup"><span data-stu-id="534d7-118">You can then set the buffer size to the value returned in `pcMap` and call `GetILToNativeMapping` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="534d7-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="534d7-119">Requirements</span></span>  
 <span data-ttu-id="534d7-120">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="534d7-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="534d7-121">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="534d7-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="534d7-122">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="534d7-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="534d7-123">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="534d7-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="534d7-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="534d7-124">See Also</span></span>  
 [<span data-ttu-id="534d7-125">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="534d7-125">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="534d7-126">GetILToNativeMapping2, metoda</span><span class="sxs-lookup"><span data-stu-id="534d7-126">GetILToNativeMapping2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getiltonativemapping2-method.md)  
 [<span data-ttu-id="534d7-127">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="534d7-127">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="534d7-128">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="534d7-128">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)

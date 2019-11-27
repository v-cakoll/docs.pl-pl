---
title: ICorProfilerInfo::GetILToNativeMapping — Metoda
ms.date: 03/30/2017
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
ms.openlocfilehash: 8dc551b2b1e29aba371e56eecfd981f16b4b1e3e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439038"
---
# <a name="icorprofilerinfogetiltonativemapping-method"></a><span data-ttu-id="3a10e-102">ICorProfilerInfo::GetILToNativeMapping — Metoda</span><span class="sxs-lookup"><span data-stu-id="3a10e-102">ICorProfilerInfo::GetILToNativeMapping Method</span></span>
<span data-ttu-id="3a10e-103">Pobiera mapę z przesunięcia języka pośredniego firmy Microsoft (MSIL) do natywnych przesunięć dla kodu zawartego w określonej funkcji.</span><span class="sxs-lookup"><span data-stu-id="3a10e-103">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a10e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3a10e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILToNativeMapping(  
    [in] FunctionID functionId,  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3a10e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3a10e-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="3a10e-106">podczas Identyfikator funkcji, która zawiera kod.</span><span class="sxs-lookup"><span data-stu-id="3a10e-106">[in] The ID of the function that contains the code.</span></span>  
  
 `cMap`  
 <span data-ttu-id="3a10e-107">podczas Maksymalny rozmiar tablicy `map`.</span><span class="sxs-lookup"><span data-stu-id="3a10e-107">[in] The maximum size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="3a10e-108">określoną Łączna liczba dostępnych struktur COR_DEBUG_IL_TO_NATIVE_MAP.</span><span class="sxs-lookup"><span data-stu-id="3a10e-108">[out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.</span></span>  
  
 `map`  
 <span data-ttu-id="3a10e-109">określoną Tablica struktur `COR_DEBUG_IL_TO_NATIVE_MAP`, z których każdy określa przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="3a10e-109">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures, each of which specifies the offsets.</span></span> <span data-ttu-id="3a10e-110">Po powrocie metody `GetILToNativeMapping`, `map` będzie zawierać niektóre lub wszystkie struktury `COR_DEBUG_IL_TO_NATIVE_MAP`.</span><span class="sxs-lookup"><span data-stu-id="3a10e-110">After the `GetILToNativeMapping` method returns, `map` will contain some or all of the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3a10e-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3a10e-111">Remarks</span></span>  
 <span data-ttu-id="3a10e-112">Metoda `GetILToNativeMapping` zwraca tablicę struktur `COR_DEBUG_IL_TO_NATIVE_MAP`.</span><span class="sxs-lookup"><span data-stu-id="3a10e-112">The `GetILToNativeMapping` method returns an array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="3a10e-113">Aby przekazać, że niektóre zakresy natywnych instrukcji odpowiadają specjalnym regionom kodu (na przykład prologu), wpis w tablicy może mieć `ilOffset` pole ustawione na wartość wyliczenia [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="3a10e-113">To convey that certain ranges of native instructions correspond to special regions of code (for example, the prolog), an entry in the array can have its `ilOffset` field set to a value of the [CorDebugIlToNativeMappingTypes](../../../../docs/framework/unmanaged-api/debugging/cordebugiltonativemappingtypes-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="3a10e-114">Po powrocie `GetILToNativeMapping` należy sprawdzić, czy bufor `map` był wystarczająco duży, aby zawierał wszystkie struktury `COR_DEBUG_IL_TO_NATIVE_MAP`.</span><span class="sxs-lookup"><span data-stu-id="3a10e-114">After `GetILToNativeMapping` returns, you must verify that the `map` buffer was large enough to contain all the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="3a10e-115">W tym celu należy porównać wartość `cMap` z wartością parametru `pcMap`.</span><span class="sxs-lookup"><span data-stu-id="3a10e-115">To do this, compare the value of `cMap` with the value of the `pcMap` parameter.</span></span> <span data-ttu-id="3a10e-116">Jeśli wartość `pcMap`, gdy zostanie pomnożona przez rozmiar struktury `COR_DEBUG_IL_TO_NATIVE_MAP`, jest większa niż `cMap`, Przydziel większy bufor `map`, zaktualizuj `cMap` przy użyciu nowego, większego rozmiaru i ponownie wywołaj `GetILToNativeMapping`.</span><span class="sxs-lookup"><span data-stu-id="3a10e-116">If the `pcMap` value, when it is multiplied by the size of a `COR_DEBUG_IL_TO_NATIVE_MAP` structure, is larger than `cMap`, allocate a larger `map` buffer, update `cMap` with the new, larger size, and call `GetILToNativeMapping` again.</span></span>  
  
 <span data-ttu-id="3a10e-117">Alternatywnie można najpierw wywołać `GetILToNativeMapping` z buforem `map` o zerowej długości, aby uzyskać prawidłowy rozmiar buforu.</span><span class="sxs-lookup"><span data-stu-id="3a10e-117">Alternatively, you can first call `GetILToNativeMapping` with a zero-length `map` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="3a10e-118">Następnie można ustawić rozmiar buforu na wartość zwróconą w `pcMap` i ponownie wywołać `GetILToNativeMapping`.</span><span class="sxs-lookup"><span data-stu-id="3a10e-118">You can then set the buffer size to the value returned in `pcMap` and call `GetILToNativeMapping` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a10e-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3a10e-119">Requirements</span></span>  
 <span data-ttu-id="3a10e-120">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a10e-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a10e-121">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="3a10e-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="3a10e-122">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3a10e-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3a10e-123">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a10e-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a10e-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3a10e-124">See also</span></span>

- [<span data-ttu-id="3a10e-125">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="3a10e-125">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="3a10e-126">GetILToNativeMapping2, metoda</span><span class="sxs-lookup"><span data-stu-id="3a10e-126">GetILToNativeMapping2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getiltonativemapping2-method.md)
- [<span data-ttu-id="3a10e-127">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="3a10e-127">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="3a10e-128">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="3a10e-128">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)

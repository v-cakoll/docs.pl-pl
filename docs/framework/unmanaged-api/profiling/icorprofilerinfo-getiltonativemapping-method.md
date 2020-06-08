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
ms.openlocfilehash: b3c0bee44bf49c7966b8fefcfe6460c6255375c5
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502993"
---
# <a name="icorprofilerinfogetiltonativemapping-method"></a><span data-ttu-id="cade5-102">ICorProfilerInfo::GetILToNativeMapping — Metoda</span><span class="sxs-lookup"><span data-stu-id="cade5-102">ICorProfilerInfo::GetILToNativeMapping Method</span></span>
<span data-ttu-id="cade5-103">Pobiera mapę z przesunięcia języka pośredniego firmy Microsoft (MSIL) do natywnych przesunięć dla kodu zawartego w określonej funkcji.</span><span class="sxs-lookup"><span data-stu-id="cade5-103">Gets a map from Microsoft intermediate language (MSIL) offsets to native offsets for the code contained in the specified function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cade5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cade5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetILToNativeMapping(  
    [in] FunctionID functionId,  
    [in] ULONG32 cMap,  
    [out] ULONG32 *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cade5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cade5-105">Parameters</span></span>  
 `functionId`  
 <span data-ttu-id="cade5-106">podczas Identyfikator funkcji, która zawiera kod.</span><span class="sxs-lookup"><span data-stu-id="cade5-106">[in] The ID of the function that contains the code.</span></span>  
  
 `cMap`  
 <span data-ttu-id="cade5-107">podczas Maksymalny rozmiar `map` tablicy.</span><span class="sxs-lookup"><span data-stu-id="cade5-107">[in] The maximum size of the `map` array.</span></span>  
  
 `pcMap`  
 <span data-ttu-id="cade5-108">określoną Łączna liczba dostępnych struktur COR_DEBUG_IL_TO_NATIVE_MAP.</span><span class="sxs-lookup"><span data-stu-id="cade5-108">[out] The total number of available COR_DEBUG_IL_TO_NATIVE_MAP structures.</span></span>  
  
 `map`  
 <span data-ttu-id="cade5-109">określoną Tablica `COR_DEBUG_IL_TO_NATIVE_MAP` struktur, z których każdy określa przesunięcia.</span><span class="sxs-lookup"><span data-stu-id="cade5-109">[out] An array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures, each of which specifies the offsets.</span></span> <span data-ttu-id="cade5-110">Po `GetILToNativeMapping` powrocie metody `map` będzie zawierać niektóre lub wszystkie `COR_DEBUG_IL_TO_NATIVE_MAP` struktury.</span><span class="sxs-lookup"><span data-stu-id="cade5-110">After the `GetILToNativeMapping` method returns, `map` will contain some or all of the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cade5-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cade5-111">Remarks</span></span>  
 <span data-ttu-id="cade5-112">`GetILToNativeMapping`Metoda zwraca tablicę `COR_DEBUG_IL_TO_NATIVE_MAP` struktur.</span><span class="sxs-lookup"><span data-stu-id="cade5-112">The `GetILToNativeMapping` method returns an array of `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="cade5-113">Aby przekazać, że niektóre zakresy natywnych instrukcji odpowiadają specjalnym regionom kodu (na przykład prologu), wpis w tablicy może mieć `ilOffset` ustawione pole jako wartość wyliczenia [CorDebugIlToNativeMappingTypes](../debugging/cordebugiltonativemappingtypes-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="cade5-113">To convey that certain ranges of native instructions correspond to special regions of code (for example, the prolog), an entry in the array can have its `ilOffset` field set to a value of the [CorDebugIlToNativeMappingTypes](../debugging/cordebugiltonativemappingtypes-enumeration.md) enumeration.</span></span>  
  
 <span data-ttu-id="cade5-114">Po `GetILToNativeMapping` powrocie należy sprawdzić, czy `map` bufor jest wystarczająco duży, aby można było zawierać wszystkie `COR_DEBUG_IL_TO_NATIVE_MAP` struktury.</span><span class="sxs-lookup"><span data-stu-id="cade5-114">After `GetILToNativeMapping` returns, you must verify that the `map` buffer was large enough to contain all the `COR_DEBUG_IL_TO_NATIVE_MAP` structures.</span></span> <span data-ttu-id="cade5-115">W tym celu należy porównać wartość `cMap` z wartością `pcMap` parametru.</span><span class="sxs-lookup"><span data-stu-id="cade5-115">To do this, compare the value of `cMap` with the value of the `pcMap` parameter.</span></span> <span data-ttu-id="cade5-116">Jeśli `pcMap` wartość, gdy zostanie pomnożona przez rozmiar `COR_DEBUG_IL_TO_NATIVE_MAP` struktury, jest większa niż `cMap` , Przydziel większy `map` bufor, Aktualizuj `cMap` o nowy, większy rozmiar i ponownie wywołaj `GetILToNativeMapping` .</span><span class="sxs-lookup"><span data-stu-id="cade5-116">If the `pcMap` value, when it is multiplied by the size of a `COR_DEBUG_IL_TO_NATIVE_MAP` structure, is larger than `cMap`, allocate a larger `map` buffer, update `cMap` with the new, larger size, and call `GetILToNativeMapping` again.</span></span>  
  
 <span data-ttu-id="cade5-117">Alternatywnie, można najpierw wywołać `GetILToNativeMapping` z buforem o zerowej długości, `map` Aby uzyskać prawidłowy rozmiar buforu.</span><span class="sxs-lookup"><span data-stu-id="cade5-117">Alternatively, you can first call `GetILToNativeMapping` with a zero-length `map` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="cade5-118">Następnie można ustawić rozmiar buforu na wartość zwracaną w `pcMap` i `GetILToNativeMapping` ponownie wywołać.</span><span class="sxs-lookup"><span data-stu-id="cade5-118">You can then set the buffer size to the value returned in `pcMap` and call `GetILToNativeMapping` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cade5-119">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cade5-119">Requirements</span></span>  
 <span data-ttu-id="cade5-120">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cade5-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cade5-121">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="cade5-121">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cade5-122">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="cade5-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cade5-123">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cade5-123">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cade5-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cade5-124">See also</span></span>

- [<span data-ttu-id="cade5-125">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="cade5-125">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="cade5-126">GetILToNativeMapping2, metoda</span><span class="sxs-lookup"><span data-stu-id="cade5-126">GetILToNativeMapping2 Method</span></span>](icorprofilerinfo4-getiltonativemapping2-method.md)
- [<span data-ttu-id="cade5-127">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="cade5-127">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="cade5-128">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="cade5-128">Profiling</span></span>](index.md)

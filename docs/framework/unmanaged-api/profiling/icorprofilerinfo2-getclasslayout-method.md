---
title: "ICorProfilerInfo2::GetClassLayout — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetClassLayout
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetClassLayout
helpviewer_keywords:
- ICorProfilerInfo2::GetClassLayout method [.NET Framework profiling]
- GetClassLayout method, ICorProfilerInfo2 interface [.NET Framework profiling]
ms.assetid: a3a36987-5666-4e2f-95b5-d0cb246502ec
topic_type: apiref
caps.latest.revision: "21"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 988e9daf54d9b4edd623e2488b68dff007e4495b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2getclasslayout-method"></a><span data-ttu-id="c507b-102">ICorProfilerInfo2::GetClassLayout — Metoda</span><span class="sxs-lookup"><span data-stu-id="c507b-102">ICorProfilerInfo2::GetClassLayout Method</span></span>
<span data-ttu-id="c507b-103">Pobiera informacje o układzie, w pamięci, pól zdefiniowanych przez określonej klasy.</span><span class="sxs-lookup"><span data-stu-id="c507b-103">Gets information about the layout, in memory, of the fields defined by the specified class.</span></span> <span data-ttu-id="c507b-104">Oznacza to, że ta metoda pobiera przesunięcia pól tej klasy.</span><span class="sxs-lookup"><span data-stu-id="c507b-104">That is, this method gets the offsets of the class's fields.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c507b-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="c507b-105">Syntax</span></span>  
  
```  
HRESULT GetClassLayout(  
    [in]  ClassID classID,  
    [in, out] COR_FIELD_OFFSET rFieldOffset[],  
    [in]  ULONG cFieldOffset,  
    [out] ULONG *pcFieldOffset,  
    [out] ULONG *pulClassSize);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c507b-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="c507b-106">Parameters</span></span>  
 `classID`  
 <span data-ttu-id="c507b-107">[in] Identyfikator klasy, dla którego mają zostać pobrane układu.</span><span class="sxs-lookup"><span data-stu-id="c507b-107">[in] The ID of the class for which the layout will be retrieved.</span></span>  
  
 `rFieldOffset`  
 <span data-ttu-id="c507b-108">[w, out] Tablica [cor_field_offset —](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) struktury, z których każdy zawiera tokeny i przesunięcia pól tej klasy.</span><span class="sxs-lookup"><span data-stu-id="c507b-108">[in, out] An array of [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) structures, each of which contains the tokens and offsets of the class's fields.</span></span>  
  
 `cFieldOffset`  
 <span data-ttu-id="c507b-109">[in] Rozmiar `rFieldOffset` tablicy.</span><span class="sxs-lookup"><span data-stu-id="c507b-109">[in] The size of the `rFieldOffset` array.</span></span>  
  
 `pcFieldOffset`  
 <span data-ttu-id="c507b-110">[out] Wskaźnik do całkowitej liczby dostępnych elementów.</span><span class="sxs-lookup"><span data-stu-id="c507b-110">[out] A pointer to the total number of available elements.</span></span> <span data-ttu-id="c507b-111">Jeśli `cFieldOffset` wynosi 0, ta wartość wskazuje liczbę potrzebnych elementów.</span><span class="sxs-lookup"><span data-stu-id="c507b-111">If `cFieldOffset` is 0, this value indicates the number of elements needed.</span></span>  
  
 `pulClassSize`  
 <span data-ttu-id="c507b-112">[out] Wskaźnik do lokalizacji, która zawiera rozmiar w bajtach klasy.</span><span class="sxs-lookup"><span data-stu-id="c507b-112">[out] A pointer to a location that contains the size, in bytes, of the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c507b-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c507b-113">Remarks</span></span>  
 <span data-ttu-id="c507b-114">`GetClassLayout` Metoda zwraca tylko pola zdefiniowane przez samej klasy.</span><span class="sxs-lookup"><span data-stu-id="c507b-114">The `GetClassLayout` method returns only the fields defined by the class itself.</span></span> <span data-ttu-id="c507b-115">Jeśli klasy nadrzędnej klasy zdefiniowano także pól, należy wywołać profilera `GetClassLayout` w klasie nadrzędnej w celu uzyskania tych pól.</span><span class="sxs-lookup"><span data-stu-id="c507b-115">If the class's parent class has defined fields as well, the profiler must call `GetClassLayout` on the parent class to obtain those fields.</span></span>  
  
 <span data-ttu-id="c507b-116">Jeśli używasz `GetClassLayout` z klasami ciąg, metoda zakończy się niepowodzeniem z kodem błędu E_INVALIDARG.</span><span class="sxs-lookup"><span data-stu-id="c507b-116">If you use `GetClassLayout` with string classes, the method will fail with error code E_INVALIDARG.</span></span> <span data-ttu-id="c507b-117">Użyj [ICorProfilerInfo2::GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) można pobrać informacji o układzie ciągu.</span><span class="sxs-lookup"><span data-stu-id="c507b-117">Use [ICorProfilerInfo2::GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) to get information about the layout of a string.</span></span> <span data-ttu-id="c507b-118">`GetClassLayout`również zakończą się po wywołaniu z klasą tablicy.</span><span class="sxs-lookup"><span data-stu-id="c507b-118">`GetClassLayout` will also fail when called with an array class.</span></span>  
  
 <span data-ttu-id="c507b-119">Po `GetClassLayout` zwróci wartość, należy sprawdzić, czy `rFieldOffset` bufor był wystarczająco duży, aby zawierała wszystkie dostępne `COR_FIELD_OFFSET` struktury.</span><span class="sxs-lookup"><span data-stu-id="c507b-119">After `GetClassLayout` returns, you must verify that the `rFieldOffset` buffer was large enough to contain all the available `COR_FIELD_OFFSET` structures.</span></span> <span data-ttu-id="c507b-120">W tym celu należy porównać wartości który `pcFieldOffset` wskazuje rozmiar `rFieldOffset` podzielonej przez rozmiar `COR_FIELD_OFFSET` struktury.</span><span class="sxs-lookup"><span data-stu-id="c507b-120">To do this, compare the value that `pcFieldOffset` points to with the size of `rFieldOffset` divided by the size of a `COR_FIELD_OFFSET` structure.</span></span> <span data-ttu-id="c507b-121">Jeśli `rFieldOffset` nie jest duży, Przydziel wystarczająca, większego `rFieldOffset` buforu, zaktualizuj `cFieldOffset` z nowej, większy rozmiar i wywołanie `GetClassLayout` ponownie.</span><span class="sxs-lookup"><span data-stu-id="c507b-121">If `rFieldOffset` is not large enough, allocate a larger `rFieldOffset` buffer, update `cFieldOffset` with the new, larger size, and call `GetClassLayout` again.</span></span>  
  
 <span data-ttu-id="c507b-122">Alternatywnie można wywołać `GetClassLayout` o zerowej długości `rFieldOffset` buforu w celu uzyskania rozmiar buforu poprawne.</span><span class="sxs-lookup"><span data-stu-id="c507b-122">Alternatively, you can first call `GetClassLayout` with a zero-length `rFieldOffset` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="c507b-123">Rozmiar buforu można następnie ustawić wartość zwracana w `pcFieldOffset` i Wywołaj `GetClassLayout` ponownie.</span><span class="sxs-lookup"><span data-stu-id="c507b-123">You can then set the buffer size to the value returned in `pcFieldOffset` and call `GetClassLayout` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c507b-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c507b-124">Requirements</span></span>  
 <span data-ttu-id="c507b-125">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c507b-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c507b-126">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c507b-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c507b-127">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c507b-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c507b-128">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c507b-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c507b-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c507b-129">See Also</span></span>  
 [<span data-ttu-id="c507b-130">ICorProfilerInfo — interfejs</span><span class="sxs-lookup"><span data-stu-id="c507b-130">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="c507b-131">ICorProfilerInfo2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="c507b-131">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 [<span data-ttu-id="c507b-132">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="c507b-132">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="c507b-133">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="c507b-133">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)

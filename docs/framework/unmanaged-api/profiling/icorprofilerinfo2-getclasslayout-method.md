---
title: ICorProfilerInfo2::GetClassLayout — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetClassLayout
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetClassLayout
helpviewer_keywords:
- ICorProfilerInfo2::GetClassLayout method [.NET Framework profiling]
- GetClassLayout method, ICorProfilerInfo2 interface [.NET Framework profiling]
ms.assetid: a3a36987-5666-4e2f-95b5-d0cb246502ec
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 6dcb9d5b3f1f47d6613be90f181a98ce991f697a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62041096"
---
# <a name="icorprofilerinfo2getclasslayout-method"></a><span data-ttu-id="df876-102">ICorProfilerInfo2::GetClassLayout — Metoda</span><span class="sxs-lookup"><span data-stu-id="df876-102">ICorProfilerInfo2::GetClassLayout Method</span></span>
<span data-ttu-id="df876-103">Pobiera informacje o układu, w pamięci, pól zdefiniowanych przez określonej klasy.</span><span class="sxs-lookup"><span data-stu-id="df876-103">Gets information about the layout, in memory, of the fields defined by the specified class.</span></span> <span data-ttu-id="df876-104">Oznacza to, że ta metoda pobiera przesunięcia pól tej klasy.</span><span class="sxs-lookup"><span data-stu-id="df876-104">That is, this method gets the offsets of the class's fields.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df876-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="df876-105">Syntax</span></span>  
  
```  
HRESULT GetClassLayout(  
    [in]  ClassID classID,  
    [in, out] COR_FIELD_OFFSET rFieldOffset[],  
    [in]  ULONG cFieldOffset,  
    [out] ULONG *pcFieldOffset,  
    [out] ULONG *pulClassSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="df876-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="df876-106">Parameters</span></span>  
 `classID`  
 <span data-ttu-id="df876-107">[in] Identyfikator klasy, dla którego będą pobierane układu.</span><span class="sxs-lookup"><span data-stu-id="df876-107">[in] The ID of the class for which the layout will be retrieved.</span></span>  
  
 `rFieldOffset`  
 <span data-ttu-id="df876-108">[out w] Tablica [cor_field_offset —](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) struktur, z których każdy zawiera tokeny i przesunięcia pól tej klasy.</span><span class="sxs-lookup"><span data-stu-id="df876-108">[in, out] An array of [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) structures, each of which contains the tokens and offsets of the class's fields.</span></span>  
  
 `cFieldOffset`  
 <span data-ttu-id="df876-109">[in] Rozmiar `rFieldOffset` tablicy.</span><span class="sxs-lookup"><span data-stu-id="df876-109">[in] The size of the `rFieldOffset` array.</span></span>  
  
 `pcFieldOffset`  
 <span data-ttu-id="df876-110">[out] Wskaźnik do całkowitej liczby dostępnych elementów.</span><span class="sxs-lookup"><span data-stu-id="df876-110">[out] A pointer to the total number of available elements.</span></span> <span data-ttu-id="df876-111">Jeśli `cFieldOffset` wynosi 0, ta wartość wskazuje liczbę potrzebnych elementów.</span><span class="sxs-lookup"><span data-stu-id="df876-111">If `cFieldOffset` is 0, this value indicates the number of elements needed.</span></span>  
  
 `pulClassSize`  
 <span data-ttu-id="df876-112">[out] Wskaźnik do lokalizacji, która zawiera rozmiar w bajtach klasy.</span><span class="sxs-lookup"><span data-stu-id="df876-112">[out] A pointer to a location that contains the size, in bytes, of the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="df876-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="df876-113">Remarks</span></span>  
 <span data-ttu-id="df876-114">`GetClassLayout` Metoda zwraca tylko te pola, które są definiowane przez samej klasy.</span><span class="sxs-lookup"><span data-stu-id="df876-114">The `GetClassLayout` method returns only the fields defined by the class itself.</span></span> <span data-ttu-id="df876-115">Jeśli klasa nadrzędna klasy została zdefiniowana również pola, program profilujący musi wywołać `GetClassLayout` na klasy nadrzędnej w celu uzyskania tych pól.</span><span class="sxs-lookup"><span data-stu-id="df876-115">If the class's parent class has defined fields as well, the profiler must call `GetClassLayout` on the parent class to obtain those fields.</span></span>  
  
 <span data-ttu-id="df876-116">Jeśli używasz `GetClassLayout` przy użyciu klas parametrów metody zakończy się niepowodzeniem z kodem błędu E_INVALIDARG.</span><span class="sxs-lookup"><span data-stu-id="df876-116">If you use `GetClassLayout` with string classes, the method will fail with error code E_INVALIDARG.</span></span> <span data-ttu-id="df876-117">Użyj [icorprofilerinfo2::getstringlayout —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) można pobrać informacji o układzie ciągu.</span><span class="sxs-lookup"><span data-stu-id="df876-117">Use [ICorProfilerInfo2::GetStringLayout](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getstringlayout-method.md) to get information about the layout of a string.</span></span> <span data-ttu-id="df876-118">`GetClassLayout` zostanie również zakończyć się niepowodzeniem po wywołaniu z klasą tablicy.</span><span class="sxs-lookup"><span data-stu-id="df876-118">`GetClassLayout` will also fail when called with an array class.</span></span>  
  
 <span data-ttu-id="df876-119">Po `GetClassLayout` zwróci wartość, należy sprawdzić, czy `rFieldOffset` bufor jest wystarczająco duży, aby zawierała wszystkich dostępnych `COR_FIELD_OFFSET` struktury.</span><span class="sxs-lookup"><span data-stu-id="df876-119">After `GetClassLayout` returns, you must verify that the `rFieldOffset` buffer was large enough to contain all the available `COR_FIELD_OFFSET` structures.</span></span> <span data-ttu-id="df876-120">Aby to zrobić, porównaj wartość która `pcFieldOffset` wskazuje z rozmiarem `rFieldOffset` podzielonej przez rozmiar `COR_FIELD_OFFSET` struktury.</span><span class="sxs-lookup"><span data-stu-id="df876-120">To do this, compare the value that `pcFieldOffset` points to with the size of `rFieldOffset` divided by the size of a `COR_FIELD_OFFSET` structure.</span></span> <span data-ttu-id="df876-121">Jeśli `rFieldOffset` nie jest duży, Przydziel wystarczająca, większego `rFieldOffset` buforu, zaktualizuj `cFieldOffset` przy użyciu nowych, większy rozmiar i Wywołaj `GetClassLayout` ponownie.</span><span class="sxs-lookup"><span data-stu-id="df876-121">If `rFieldOffset` is not large enough, allocate a larger `rFieldOffset` buffer, update `cFieldOffset` with the new, larger size, and call `GetClassLayout` again.</span></span>  
  
 <span data-ttu-id="df876-122">Alternatywnie, można wywołać `GetClassLayout` o zerowej długości `rFieldOffset` buforu w celu uzyskania rozmiar buforu poprawne.</span><span class="sxs-lookup"><span data-stu-id="df876-122">Alternatively, you can first call `GetClassLayout` with a zero-length `rFieldOffset` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="df876-123">Następnie można ustawić rozmiar buforu do wartości zwracanej w `pcFieldOffset` i wywołać `GetClassLayout` ponownie.</span><span class="sxs-lookup"><span data-stu-id="df876-123">You can then set the buffer size to the value returned in `pcFieldOffset` and call `GetClassLayout` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df876-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="df876-124">Requirements</span></span>  
 <span data-ttu-id="df876-125">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df876-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df876-126">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="df876-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="df876-127">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="df876-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="df876-128">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df876-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df876-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="df876-129">See also</span></span>

- [<span data-ttu-id="df876-130">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="df876-130">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="df876-131">ICorProfilerInfo2, interfejs</span><span class="sxs-lookup"><span data-stu-id="df876-131">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
- [<span data-ttu-id="df876-132">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="df876-132">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)
- [<span data-ttu-id="df876-133">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="df876-133">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)

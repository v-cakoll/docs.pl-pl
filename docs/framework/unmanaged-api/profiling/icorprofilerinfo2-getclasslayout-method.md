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
ms.openlocfilehash: 85319a45861b2b48f7690f69bb8f9f9469af014c
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862805"
---
# <a name="icorprofilerinfo2getclasslayout-method"></a><span data-ttu-id="578f6-102">ICorProfilerInfo2::GetClassLayout — Metoda</span><span class="sxs-lookup"><span data-stu-id="578f6-102">ICorProfilerInfo2::GetClassLayout Method</span></span>
<span data-ttu-id="578f6-103">Pobiera informacje o układzie, w pamięci, pól zdefiniowanych przez określoną klasę.</span><span class="sxs-lookup"><span data-stu-id="578f6-103">Gets information about the layout, in memory, of the fields defined by the specified class.</span></span> <span data-ttu-id="578f6-104">Oznacza to, że ta metoda pobiera przesunięcia pól klasy.</span><span class="sxs-lookup"><span data-stu-id="578f6-104">That is, this method gets the offsets of the class's fields.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="578f6-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="578f6-105">Syntax</span></span>  
  
```cpp  
HRESULT GetClassLayout(  
    [in]  ClassID classID,  
    [in, out] COR_FIELD_OFFSET rFieldOffset[],  
    [in]  ULONG cFieldOffset,  
    [out] ULONG *pcFieldOffset,  
    [out] ULONG *pulClassSize);  
```  
  
## <a name="parameters"></a><span data-ttu-id="578f6-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="578f6-106">Parameters</span></span>  
 `classID`  
 <span data-ttu-id="578f6-107">podczas Identyfikator klasy, dla której zostanie pobrany układ.</span><span class="sxs-lookup"><span data-stu-id="578f6-107">[in] The ID of the class for which the layout will be retrieved.</span></span>  
  
 `rFieldOffset`  
 <span data-ttu-id="578f6-108">[in. out] Tablica struktur [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) , z których każdy zawiera tokeny i przesunięcia pól klasy.</span><span class="sxs-lookup"><span data-stu-id="578f6-108">[in, out] An array of [COR_FIELD_OFFSET](../../../../docs/framework/unmanaged-api/metadata/cor-field-offset-structure.md) structures, each of which contains the tokens and offsets of the class's fields.</span></span>  
  
 `cFieldOffset`  
 <span data-ttu-id="578f6-109">podczas Rozmiar tablicy `rFieldOffset`.</span><span class="sxs-lookup"><span data-stu-id="578f6-109">[in] The size of the `rFieldOffset` array.</span></span>  
  
 `pcFieldOffset`  
 <span data-ttu-id="578f6-110">określoną Wskaźnik do łącznej liczby dostępnych elementów.</span><span class="sxs-lookup"><span data-stu-id="578f6-110">[out] A pointer to the total number of available elements.</span></span> <span data-ttu-id="578f6-111">Jeśli `cFieldOffset` wynosi 0, ta wartość wskazuje liczbę wymaganych elementów.</span><span class="sxs-lookup"><span data-stu-id="578f6-111">If `cFieldOffset` is 0, this value indicates the number of elements needed.</span></span>  
  
 `pulClassSize`  
 <span data-ttu-id="578f6-112">określoną Wskaźnik do lokalizacji zawierającej rozmiar (w bajtach) klasy.</span><span class="sxs-lookup"><span data-stu-id="578f6-112">[out] A pointer to a location that contains the size, in bytes, of the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="578f6-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="578f6-113">Remarks</span></span>  
 <span data-ttu-id="578f6-114">Metoda `GetClassLayout` zwraca tylko pola zdefiniowane przez samą klasę.</span><span class="sxs-lookup"><span data-stu-id="578f6-114">The `GetClassLayout` method returns only the fields defined by the class itself.</span></span> <span data-ttu-id="578f6-115">Jeśli Klasa nadrzędna klasy ma również zdefiniowane pola, profiler musi wywołać `GetClassLayout` w klasie nadrzędnej, aby uzyskać te pola.</span><span class="sxs-lookup"><span data-stu-id="578f6-115">If the class's parent class has defined fields as well, the profiler must call `GetClassLayout` on the parent class to obtain those fields.</span></span>  
  
 <span data-ttu-id="578f6-116">Jeśli używasz `GetClassLayout` z klasami ciągów, metoda zakończy się niepowodzeniem z kodem błędu E_INVALIDARG.</span><span class="sxs-lookup"><span data-stu-id="578f6-116">If you use `GetClassLayout` with string classes, the method will fail with error code E_INVALIDARG.</span></span> <span data-ttu-id="578f6-117">Użyj [ICorProfilerInfo2:: GetStringLayout —](icorprofilerinfo2-getstringlayout-method.md) , aby uzyskać informacje na temat układu ciągu.</span><span class="sxs-lookup"><span data-stu-id="578f6-117">Use [ICorProfilerInfo2::GetStringLayout](icorprofilerinfo2-getstringlayout-method.md) to get information about the layout of a string.</span></span> <span data-ttu-id="578f6-118">`GetClassLayout` również zakończy się niepowodzeniem w przypadku wywołania z klasą Array.</span><span class="sxs-lookup"><span data-stu-id="578f6-118">`GetClassLayout` will also fail when called with an array class.</span></span>  
  
 <span data-ttu-id="578f6-119">Po powrocie `GetClassLayout` należy sprawdzić, czy bufor `rFieldOffset` był wystarczająco duży, aby zawierał wszystkie dostępne struktury `COR_FIELD_OFFSET`.</span><span class="sxs-lookup"><span data-stu-id="578f6-119">After `GetClassLayout` returns, you must verify that the `rFieldOffset` buffer was large enough to contain all the available `COR_FIELD_OFFSET` structures.</span></span> <span data-ttu-id="578f6-120">W tym celu należy porównać wartość `pcFieldOffset` punkty z rozmiarem `rFieldOffset` podzielonym przez rozmiar struktury `COR_FIELD_OFFSET`.</span><span class="sxs-lookup"><span data-stu-id="578f6-120">To do this, compare the value that `pcFieldOffset` points to with the size of `rFieldOffset` divided by the size of a `COR_FIELD_OFFSET` structure.</span></span> <span data-ttu-id="578f6-121">Jeśli `rFieldOffset` nie jest wystarczająco duży, Przydziel większy bufor `rFieldOffset`, zaktualizuj `cFieldOffset` przy użyciu nowego, większego rozmiaru i ponownie wywołaj `GetClassLayout`.</span><span class="sxs-lookup"><span data-stu-id="578f6-121">If `rFieldOffset` is not large enough, allocate a larger `rFieldOffset` buffer, update `cFieldOffset` with the new, larger size, and call `GetClassLayout` again.</span></span>  
  
 <span data-ttu-id="578f6-122">Alternatywnie można najpierw wywołać `GetClassLayout` z buforem `rFieldOffset` o zerowej długości, aby uzyskać prawidłowy rozmiar buforu.</span><span class="sxs-lookup"><span data-stu-id="578f6-122">Alternatively, you can first call `GetClassLayout` with a zero-length `rFieldOffset` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="578f6-123">Następnie można ustawić rozmiar buforu na wartość zwróconą w `pcFieldOffset` i ponownie wywołać `GetClassLayout`.</span><span class="sxs-lookup"><span data-stu-id="578f6-123">You can then set the buffer size to the value returned in `pcFieldOffset` and call `GetClassLayout` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="578f6-124">Wymagania</span><span class="sxs-lookup"><span data-stu-id="578f6-124">Requirements</span></span>  
 <span data-ttu-id="578f6-125">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="578f6-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="578f6-126">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="578f6-126">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="578f6-127">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="578f6-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="578f6-128">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="578f6-128">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="578f6-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="578f6-129">See also</span></span>

- [<span data-ttu-id="578f6-130">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="578f6-130">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="578f6-131">ICorProfilerInfo2, interfejs</span><span class="sxs-lookup"><span data-stu-id="578f6-131">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
- [<span data-ttu-id="578f6-132">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="578f6-132">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="578f6-133">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="578f6-133">Profiling</span></span>](index.md)

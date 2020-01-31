---
title: ICorProfilerInfo2::GetClassIDInfo2 — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetClassIDInfo2
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetClassIDInfo2
helpviewer_keywords:
- GetClassIDInfo2 method [.NET Framework profiling]
- ICorProfilerInfo2::GetClassIDInfo2 method [.NET Framework profiling]
ms.assetid: 0141d582-d066-4d49-8d1f-ae82129a1960
topic_type:
- apiref
ms.openlocfilehash: 64d2cd76dafb1a51814b916b5ce73fb08cdcaef9
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868863"
---
# <a name="icorprofilerinfo2getclassidinfo2-method"></a><span data-ttu-id="cabc5-102">ICorProfilerInfo2::GetClassIDInfo2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="cabc5-102">ICorProfilerInfo2::GetClassIDInfo2 Method</span></span>
<span data-ttu-id="cabc5-103">Pobiera moduł nadrzędny i token metadanych dla otwartej definicji ogólnej określonej klasy, `ClassID` jej klasy nadrzędnej i `ClassID` dla każdego argumentu typu, jeśli istnieje, klasy.</span><span class="sxs-lookup"><span data-stu-id="cabc5-103">Gets the parent module and metadata token for the open generic definition of the specified class, the `ClassID` of its parent class, and the `ClassID` for each type argument, if present, of the class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cabc5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cabc5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClassIDInfo2(  
    [in]  ClassID classId,  
    [out] ModuleID *pModuleId,  
    [out] mdTypeDef *pTypeDefToken,  
    [out] ClassID *pParentClassId,  
    [in]  ULONG32 cNumTypeArgs,  
    [out] ULONG32 *pcNumTypeArgs,  
    [out] ClassID typeArgs[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cabc5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cabc5-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="cabc5-106">podczas Identyfikator klasy, dla której będą pobierane informacje.</span><span class="sxs-lookup"><span data-stu-id="cabc5-106">[in] The ID of the class for which information will be retrieved.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="cabc5-107">określoną Wskaźnik na identyfikator modułu nadrzędnego dla otwartej definicji ogólnej dla określonej klasy.</span><span class="sxs-lookup"><span data-stu-id="cabc5-107">[out] Pointer to the ID of the parent module for the open generic definition of the specified class.</span></span>  
  
 `pTypeDefToken`  
 <span data-ttu-id="cabc5-108">określoną Wskaźnik do tokenu metadanych dla otwartej definicji ogólnej określonej klasy.</span><span class="sxs-lookup"><span data-stu-id="cabc5-108">[out] Pointer to the metadata token for the open generic definition of the specified class.</span></span>  
  
 `pParentClassId`  
 <span data-ttu-id="cabc5-109">określoną Wskaźnik na identyfikator klasy nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="cabc5-109">[out] Pointer to the ID of the parent class.</span></span>  
  
 `cNumTypeArgs`  
 <span data-ttu-id="cabc5-110">podczas Rozmiar tablicy `typeArgs`.</span><span class="sxs-lookup"><span data-stu-id="cabc5-110">[in] The size of the `typeArgs` array.</span></span>  
  
 `pcNumTypeArgs`  
 <span data-ttu-id="cabc5-111">określoną Wskaźnik do całkowitej liczby dostępnych elementów.</span><span class="sxs-lookup"><span data-stu-id="cabc5-111">[out] Pointer to the total number of available elements.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="cabc5-112">określoną Tablica wartości `ClassID`, z których każdy reprezentuje identyfikator argumentu typu klasy.</span><span class="sxs-lookup"><span data-stu-id="cabc5-112">[out] An array of `ClassID` values, each of which represents the ID of a type argument of the class.</span></span> <span data-ttu-id="cabc5-113">Gdy metoda zwraca, `typeArgs` będzie zawierać niektóre lub wszystkie dostępne `ClassID` wartości.</span><span class="sxs-lookup"><span data-stu-id="cabc5-113">When the method returns, `typeArgs` will contain some or all the available `ClassID` values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cabc5-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cabc5-114">Remarks</span></span>  
 <span data-ttu-id="cabc5-115">Metoda `GetClassIDInfo2` jest podobna do metody [ICorProfilerInfo:: GetClassIDInfo —](icorprofilerinfo-getclassidinfo-method.md) , ale `GetClassIDInfo2` uzyskuje dodatkowe informacje o typie ogólnym.</span><span class="sxs-lookup"><span data-stu-id="cabc5-115">The `GetClassIDInfo2` method is similar to the [ICorProfilerInfo::GetClassIDInfo](icorprofilerinfo-getclassidinfo-method.md) method, but `GetClassIDInfo2` obtains additional information about a generic type.</span></span>  
  
 <span data-ttu-id="cabc5-116">Kod profilera może wywołać [ICorProfilerInfo:: GetModuleMetaData —](icorprofilerinfo-getmodulemetadata-method.md) w celu uzyskania interfejsu [metadanych](../../../../docs/framework/unmanaged-api/metadata/index.md) dla danego modułu.</span><span class="sxs-lookup"><span data-stu-id="cabc5-116">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](icorprofilerinfo-getmodulemetadata-method.md) to obtain a [metadata](../../../../docs/framework/unmanaged-api/metadata/index.md) interface for a given module.</span></span> <span data-ttu-id="cabc5-117">Token metadanych, który jest zwracany do lokalizacji, do której odwołuje się `pTypeDefToken`, może następnie zostać użyty w celu uzyskania dostępu do metadanych dla klasy.</span><span class="sxs-lookup"><span data-stu-id="cabc5-117">The metadata token that is returned to the location referenced by `pTypeDefToken` can then be used to access the metadata for the class.</span></span>  
  
 <span data-ttu-id="cabc5-118">Po powrocie `GetClassIDInfo2` należy sprawdzić, czy bufor `typeArgs` był wystarczająco duży, aby zawierał wszystkie wartości `ClassID`.</span><span class="sxs-lookup"><span data-stu-id="cabc5-118">After `GetClassIDInfo2` returns, you must verify that the `typeArgs` buffer was large enough to contain all the `ClassID` values.</span></span> <span data-ttu-id="cabc5-119">W tym celu należy porównać wartość, która `pcNumTypeArgs` wskazuje na wartość parametru `cNumTypeArgs`.</span><span class="sxs-lookup"><span data-stu-id="cabc5-119">To do this, compare the value that `pcNumTypeArgs` points to with the value of the `cNumTypeArgs` parameter.</span></span> <span data-ttu-id="cabc5-120">Jeśli `pcNumTypeArgs` wskazuje wartość, która jest większa niż `cNumTypeArgs`, Przydziel większy bufor `typeArgs`, zaktualizuj `cNumTypeArgs` przy użyciu nowego, większego rozmiaru i ponownie wywołaj `GetClassIDInfo2`.</span><span class="sxs-lookup"><span data-stu-id="cabc5-120">If `pcNumTypeArgs` points to a value that is larger than `cNumTypeArgs`, allocate a larger `typeArgs` buffer, update `cNumTypeArgs` with the new, larger size, and call `GetClassIDInfo2` again.</span></span>  
  
 <span data-ttu-id="cabc5-121">Alternatywnie można najpierw wywołać `GetClassIDInfo2` z buforem `typeArgs` o zerowej długości, aby uzyskać prawidłowy rozmiar buforu.</span><span class="sxs-lookup"><span data-stu-id="cabc5-121">Alternatively, you can first call `GetClassIDInfo2` with a zero-length `typeArgs` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="cabc5-122">Następnie można ustawić `typeArgs` rozmiar buforu na wartość zwróconą w `pcNumTypeArgs` i ponownie wywołać `GetClassIDInfo2`.</span><span class="sxs-lookup"><span data-stu-id="cabc5-122">You can then set the `typeArgs` buffer size to the value returned in `pcNumTypeArgs` and call `GetClassIDInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cabc5-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cabc5-123">Requirements</span></span>  
 <span data-ttu-id="cabc5-124">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cabc5-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cabc5-125">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="cabc5-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cabc5-126">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="cabc5-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cabc5-127">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cabc5-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cabc5-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cabc5-128">See also</span></span>

- [<span data-ttu-id="cabc5-129">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="cabc5-129">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="cabc5-130">ICorProfilerInfo2, interfejs</span><span class="sxs-lookup"><span data-stu-id="cabc5-130">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)
- [<span data-ttu-id="cabc5-131">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="cabc5-131">Profiling Interfaces</span></span>](profiling-interfaces.md)
- [<span data-ttu-id="cabc5-132">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="cabc5-132">Profiling</span></span>](index.md)

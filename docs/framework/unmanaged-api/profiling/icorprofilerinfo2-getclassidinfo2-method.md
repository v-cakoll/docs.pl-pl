---
title: "ICorProfilerInfo2::GetClassIDInfo2 — Metoda"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e0348462cdbff14486b31e1878f06b7565b47182
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getclassidinfo2-method"></a><span data-ttu-id="06077-102">ICorProfilerInfo2::GetClassIDInfo2 — Metoda</span><span class="sxs-lookup"><span data-stu-id="06077-102">ICorProfilerInfo2::GetClassIDInfo2 Method</span></span>
<span data-ttu-id="06077-103">Pobiera moduł nadrzędny i metadanych token dla Otwórz ogólną definicję określonej klasy `ClassID` jego klasy nadrzędnej i `ClassID` dla każdego typu argumentu, jeśli jest obecny, klasy.</span><span class="sxs-lookup"><span data-stu-id="06077-103">Gets the parent module and metadata token for the open generic definition of the specified class, the `ClassID` of its parent class, and the `ClassID` for each type argument, if present, of the class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="06077-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="06077-104">Syntax</span></span>  
  
```  
HRESULT GetClassIDInfo2(  
    [in]  ClassID classId,  
    [out] ModuleID *pModuleId,  
    [out] mdTypeDef *pTypeDefToken,  
    [out] ClassID *pParentClassId,  
    [in]  ULONG32 cNumTypeArgs,  
    [out] ULONG32 *pcNumTypeArgs,  
    [out] ClassID typeArgs[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="06077-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="06077-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="06077-106">[in] Identyfikator klasy, dla których zostaną pobrane informacje.</span><span class="sxs-lookup"><span data-stu-id="06077-106">[in] The ID of the class for which information will be retrieved.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="06077-107">[out] Wskaźnik do Identyfikatora modułu nadrzędnego dla Otwórz ogólną definicję określonej klasy.</span><span class="sxs-lookup"><span data-stu-id="06077-107">[out] Pointer to the ID of the parent module for the open generic definition of the specified class.</span></span>  
  
 `pTypeDefToken`  
 <span data-ttu-id="06077-108">[out] Wskaźnik do token metadanych dla Otwórz ogólną definicję określonej klasy.</span><span class="sxs-lookup"><span data-stu-id="06077-108">[out] Pointer to the metadata token for the open generic definition of the specified class.</span></span>  
  
 `pParentClassId`  
 <span data-ttu-id="06077-109">[out] Wskaźnik do Identyfikatora klasy nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="06077-109">[out] Pointer to the ID of the parent class.</span></span>  
  
 `cNumTypeArgs`  
 <span data-ttu-id="06077-110">[in] Rozmiar `typeArgs` tablicy.</span><span class="sxs-lookup"><span data-stu-id="06077-110">[in] The size of the `typeArgs` array.</span></span>  
  
 `pcNumTypeArgs`  
 <span data-ttu-id="06077-111">[out] Wskaźnik do całkowitej liczby dostępnych elementów.</span><span class="sxs-lookup"><span data-stu-id="06077-111">[out] Pointer to the total number of available elements.</span></span>  
  
 `typeArgs`  
 <span data-ttu-id="06077-112">[out] Tablica `ClassID` wartości, z których każdy reprezentuje identyfikator argumentu typu klasy.</span><span class="sxs-lookup"><span data-stu-id="06077-112">[out] An array of `ClassID` values, each of which represents the ID of a type argument of the class.</span></span> <span data-ttu-id="06077-113">Gdy metoda zwróci wartość, `typeArgs` będzie zawierał niektórych lub wszystkich dostępnych `ClassID` wartości.</span><span class="sxs-lookup"><span data-stu-id="06077-113">When the method returns, `typeArgs` will contain some or all the available `ClassID` values.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06077-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="06077-114">Remarks</span></span>  
 <span data-ttu-id="06077-115">`GetClassIDInfo2` Metoda jest podobna do [ICorProfilerInfo::GetClassIDInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md) metody, ale `GetClassIDInfo2` uzyskuje dodatkowe informacje na temat typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="06077-115">The `GetClassIDInfo2` method is similar to the [ICorProfilerInfo::GetClassIDInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getclassidinfo-method.md) method, but `GetClassIDInfo2` obtains additional information about a generic type.</span></span>  
  
 <span data-ttu-id="06077-116">Kod profiler może wywołać [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) uzyskanie [metadanych](../../../../docs/framework/unmanaged-api/metadata/index.md) interfejs dla danego modułu.</span><span class="sxs-lookup"><span data-stu-id="06077-116">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) to obtain a [metadata](../../../../docs/framework/unmanaged-api/metadata/index.md) interface for a given module.</span></span> <span data-ttu-id="06077-117">Token metadanych, która jest zwracana do lokalizacji odwołuje się `pTypeDefToken` następnie może służyć do uzyskania dostępu do klasy metadanych.</span><span class="sxs-lookup"><span data-stu-id="06077-117">The metadata token that is returned to the location referenced by `pTypeDefToken` can then be used to access the metadata for the class.</span></span>  
  
 <span data-ttu-id="06077-118">Po `GetClassIDInfo2` zwróci wartość, należy sprawdzić, czy `typeArgs` bufor był wystarczająco duży, aby pomieścić wszystkie `ClassID` wartości.</span><span class="sxs-lookup"><span data-stu-id="06077-118">After `GetClassIDInfo2` returns, you must verify that the `typeArgs` buffer was large enough to contain all the `ClassID` values.</span></span> <span data-ttu-id="06077-119">W tym celu należy porównać wartości który `pcNumTypeArgs` wskazuje wartość `cNumTypeArgs` parametru.</span><span class="sxs-lookup"><span data-stu-id="06077-119">To do this, compare the value that `pcNumTypeArgs` points to with the value of the `cNumTypeArgs` parameter.</span></span> <span data-ttu-id="06077-120">Jeśli `pcNumTypeArgs` wskazuje wartość, która jest większa niż `cNumTypeArgs`, Przydziel większy `typeArgs` buforu, zaktualizuj `cNumTypeArgs` z nowej, większy rozmiar i wywołanie `GetClassIDInfo2` ponownie.</span><span class="sxs-lookup"><span data-stu-id="06077-120">If `pcNumTypeArgs` points to a value that is larger than `cNumTypeArgs`, allocate a larger `typeArgs` buffer, update `cNumTypeArgs` with the new, larger size, and call `GetClassIDInfo2` again.</span></span>  
  
 <span data-ttu-id="06077-121">Alternatywnie można wywołać `GetClassIDInfo2` o zerowej długości `typeArgs` buforu w celu uzyskania rozmiar buforu poprawne.</span><span class="sxs-lookup"><span data-stu-id="06077-121">Alternatively, you can first call `GetClassIDInfo2` with a zero-length `typeArgs` buffer to obtain the correct buffer size.</span></span> <span data-ttu-id="06077-122">Następnie można ustawić `typeArgs` rozmiar wartość zwracana w buforu `pcNumTypeArgs` i Wywołaj `GetClassIDInfo2` ponownie.</span><span class="sxs-lookup"><span data-stu-id="06077-122">You can then set the `typeArgs` buffer size to the value returned in `pcNumTypeArgs` and call `GetClassIDInfo2` again.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="06077-123">Wymagania</span><span class="sxs-lookup"><span data-stu-id="06077-123">Requirements</span></span>  
 <span data-ttu-id="06077-124">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="06077-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="06077-125">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="06077-125">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="06077-126">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="06077-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="06077-127">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="06077-127">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06077-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="06077-128">See Also</span></span>  
 [<span data-ttu-id="06077-129">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="06077-129">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="06077-130">ICorProfilerInfo2, interfejs</span><span class="sxs-lookup"><span data-stu-id="06077-130">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)  
 [<span data-ttu-id="06077-131">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="06077-131">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)  
 [<span data-ttu-id="06077-132">Profilowanie</span><span class="sxs-lookup"><span data-stu-id="06077-132">Profiling</span></span>](../../../../docs/framework/unmanaged-api/profiling/index.md)

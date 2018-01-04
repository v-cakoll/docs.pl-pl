---
title: "ICorProfilerInfo::GetObjectSize — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetObjectSize
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetObjectSize
helpviewer_keywords:
- GetObjectSize method [.NET Framework profiling]
- ICorProfilerInfo::GetObjectSize method [.NET Framework profiling]
ms.assetid: 9f02e763-73f7-42cb-a41c-f78499d9482c
topic_type: apiref
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9425938042485c4330fe3fbc50cdabde6451b427
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetobjectsize-method"></a><span data-ttu-id="bfa20-102">ICorProfilerInfo::GetObjectSize — Metoda</span><span class="sxs-lookup"><span data-stu-id="bfa20-102">ICorProfilerInfo::GetObjectSize Method</span></span>
<span data-ttu-id="bfa20-103">Pobiera rozmiar określonego obiektu.</span><span class="sxs-lookup"><span data-stu-id="bfa20-103">Gets the size of a specified object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfa20-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bfa20-104">Syntax</span></span>  
  
```  
HRESULT GetObjectSize(  
    [in]  ObjectID objectId,  
    [out] ULONG  *pcSize);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bfa20-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bfa20-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="bfa20-106">[in] Identyfikator obiektu.</span><span class="sxs-lookup"><span data-stu-id="bfa20-106">[in] The ID of the object.</span></span>  
  
 `pcSize`  
 <span data-ttu-id="bfa20-107">[out] Wskaźnik do obiektu rozmiar w bajtach.</span><span class="sxs-lookup"><span data-stu-id="bfa20-107">[out] A pointer to the object's size, in bytes.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bfa20-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bfa20-108">Remarks</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="bfa20-109">Ta metoda jest przestarzała.</span><span class="sxs-lookup"><span data-stu-id="bfa20-109">This method is obsolete.</span></span> <span data-ttu-id="bfa20-110">Zwraca COR_E_OVERFLOW dla obiektów większych niż 4GB na platformach 64-bitowych.</span><span class="sxs-lookup"><span data-stu-id="bfa20-110">It returns COR_E_OVERFLOW for objects greater than 4GB on 64-bit platforms.</span></span> <span data-ttu-id="bfa20-111">Użyj [ICorProfilerInfo4::GetObjectSize2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md) metody zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="bfa20-111">Use the  [ICorProfilerInfo4::GetObjectSize2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-getobjectsize2-method.md) method instead.</span></span>  
  
 <span data-ttu-id="bfa20-112">Różne obiekty o takich samych typach często mają ten sam rozmiar.</span><span class="sxs-lookup"><span data-stu-id="bfa20-112">Different objects of the same types often have the same size.</span></span> <span data-ttu-id="bfa20-113">Jednak niektóre typy, takich jak macierze czy ciągi, może mieć inny rozmiar dla każdego obiektu.</span><span class="sxs-lookup"><span data-stu-id="bfa20-113">However, some types, such as arrays or strings, may have a different size for each object.</span></span>  
  
 <span data-ttu-id="bfa20-114">Rozmiar zwrócony przez `GetObjectSize` — metoda nie ma żadnych dopełnienie wyrównanie, którym może występować, gdy obiekt jest w stercie kolekcji pamięci.</span><span class="sxs-lookup"><span data-stu-id="bfa20-114">The size returned by the `GetObjectSize` method does not include any alignment padding that may appear after the object is on the garbage collection heap.</span></span> <span data-ttu-id="bfa20-115">Jeśli używasz `GetObjectSize` wyrównanie dopełnienie ręcznie w razie potrzeby dodaj metodę z obiektu do obiektu na stercie kolekcji pamięci.</span><span class="sxs-lookup"><span data-stu-id="bfa20-115">If you use the `GetObjectSize` method to advance from object to object on the garbage collection heap, add alignment padding manually, as necessary.</span></span>  
  
-   <span data-ttu-id="bfa20-116">W 32-bitowej wersji systemu Windows COR_PRF_GC_GEN_0, COR_PRF_GC_GEN_1 i COR_PRF_GC_GEN_2 wyrównanie 4-bajtowych Użyj i COR_PRF_GC_LARGE_OBJECT_HEAP używa wyrównanie 8-bajtowych.</span><span class="sxs-lookup"><span data-stu-id="bfa20-116">On 32-bit Windows, COR_PRF_GC_GEN_0, COR_PRF_GC_GEN_1, and COR_PRF_GC_GEN_2 use 4-byte alignment, and COR_PRF_GC_LARGE_OBJECT_HEAP uses 8-byte alignment.</span></span>  
  
-   <span data-ttu-id="bfa20-117">W 64-bitowej wersji systemu Windows wyrównania jest zawsze 8 bajtów.</span><span class="sxs-lookup"><span data-stu-id="bfa20-117">On 64-bit Windows, the alignment is always 8 bytes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bfa20-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bfa20-118">Requirements</span></span>  
 <span data-ttu-id="bfa20-119">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bfa20-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bfa20-120">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="bfa20-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="bfa20-121">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bfa20-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bfa20-122">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bfa20-122">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bfa20-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bfa20-123">See Also</span></span>  
 [<span data-ttu-id="bfa20-124">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="bfa20-124">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)

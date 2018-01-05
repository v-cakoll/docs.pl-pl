---
title: "ICorProfilerInfo2::GetContextStaticAddress — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetContextStaticAddress
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetContextStaticAddress
helpviewer_keywords:
- GetContextStaticAddress method [.NET Framework profiling]
- ICorProfilerInfo2::GetContextStaticAddress method [.NET Framework profiling]
ms.assetid: 2b374116-0972-416a-8cf5-79213129be9a
topic_type: apiref
caps.latest.revision: "23"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e92435927203bb2a75ff92d883470832126da080
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getcontextstaticaddress-method"></a><span data-ttu-id="19d5a-102">ICorProfilerInfo2::GetContextStaticAddress — Metoda</span><span class="sxs-lookup"><span data-stu-id="19d5a-102">ICorProfilerInfo2::GetContextStaticAddress Method</span></span>
<span data-ttu-id="19d5a-103">Pobiera adres dla określonego pola statycznej kontekstu, który znajduje się w zakresie określonego kontekstu.</span><span class="sxs-lookup"><span data-stu-id="19d5a-103">Gets the address for the specified context-static field that is in the scope of the specified context.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19d5a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="19d5a-104">Syntax</span></span>  
  
```  
HRESULT GetContextStaticAddress(  
    [in] ClassID classId,  
    [in] mdFieldDef fieldToken,  
    [in] ContextID contextId,  
    [out] void **ppAddress);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="19d5a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="19d5a-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="19d5a-106">[in] Identyfikator klasy, która zawiera żądane pole kontekstu statycznego.</span><span class="sxs-lookup"><span data-stu-id="19d5a-106">[in] The ID of the class that contains the requested context-static field.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="19d5a-107">[in] Token metadanych dla żądanego pola kontekstu statycznego.</span><span class="sxs-lookup"><span data-stu-id="19d5a-107">[in] The metadata token for the requested context-static field.</span></span>  
  
 `contextId`  
 <span data-ttu-id="19d5a-108">[in] Identyfikator kontekstu, która jest zakresem dla żądanego pola statyczne kontekstu.</span><span class="sxs-lookup"><span data-stu-id="19d5a-108">[in] The ID of the context that is the scope for the requested context-static field.</span></span>  
  
 `ppAddress`  
 <span data-ttu-id="19d5a-109">[out] Wskaźnik do adresu pola statycznego, który znajduje się w określonym kontekście.</span><span class="sxs-lookup"><span data-stu-id="19d5a-109">[out] A pointer to the address of the static field that is within the specified context.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="19d5a-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="19d5a-110">Remarks</span></span>  
 <span data-ttu-id="19d5a-111">`GetContextStaticAddress` Metoda może zwracać jedną z następujących czynności:</span><span class="sxs-lookup"><span data-stu-id="19d5a-111">The `GetContextStaticAddress` method may return one of the following:</span></span>  
  
-   <span data-ttu-id="19d5a-112">HRESULT CORPROF_E_DATAINCOMPLETE, jeśli nie przypisano danego pola statycznego adresu w określonym kontekście.</span><span class="sxs-lookup"><span data-stu-id="19d5a-112">A CORPROF_E_DATAINCOMPLETE HRESULT if the given static field has not been assigned an address in the specified context.</span></span>  
  
-   <span data-ttu-id="19d5a-113">Adresy obiektów, które mogą znajdować się w pamięci sterty kolekcji.</span><span class="sxs-lookup"><span data-stu-id="19d5a-113">The addresses of objects that may be in the garbage collection heap.</span></span> <span data-ttu-id="19d5a-114">Te adresy mogą być nieprawidłowe po wyrzucanie elementów bezużytecznych, więc po wyrzucanie elementów bezużytecznych profilowania nie należy zakładać, że są prawidłowe.</span><span class="sxs-lookup"><span data-stu-id="19d5a-114">These addresses may become invalid after garbage collection, so after garbage collection, profilers should not assume that they are valid.</span></span>  
  
 <span data-ttu-id="19d5a-115">Przed ukończeniem konstruktora klasy klasy `GetContextStaticAddress` zwróci CORPROF_E_DATAINCOMPLETE dla wszystkich jego pól statycznych, mimo że niektóre pola statyczne już może zainicjować i umieszczanie w katalogu głównym odzyskiwanie kolekcji obiektów.</span><span class="sxs-lookup"><span data-stu-id="19d5a-115">Before a class’s class constructor is completed, `GetContextStaticAddress` will return CORPROF_E_DATAINCOMPLETE for all its static fields, although some of the static fields may already be initialized and rooting garbage collection objects.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="19d5a-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="19d5a-116">Requirements</span></span>  
 <span data-ttu-id="19d5a-117">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="19d5a-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="19d5a-118">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="19d5a-118">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="19d5a-119">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="19d5a-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="19d5a-120">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="19d5a-120">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19d5a-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="19d5a-121">See Also</span></span>  
 [<span data-ttu-id="19d5a-122">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="19d5a-122">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="19d5a-123">ICorProfilerInfo2, interfejs</span><span class="sxs-lookup"><span data-stu-id="19d5a-123">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)

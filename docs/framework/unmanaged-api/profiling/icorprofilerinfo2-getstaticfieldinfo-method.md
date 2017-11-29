---
title: "ICorProfilerInfo2::GetStaticFieldInfo — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetStaticFieldInfo
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetStaticFieldInfo
helpviewer_keywords:
- ICorProfilerInfo2::GetStaticFieldInfo method [.NET Framework profiling]
- GetStaticFieldInfo method [.NET Framework profiling]
ms.assetid: fc663e76-e23f-49a8-bdd5-52cdf1a3b2b3
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7cf16a0fae7f3e2afd095534b2e7f7957d44e3e7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icorprofilerinfo2getstaticfieldinfo-method"></a><span data-ttu-id="16055-102">ICorProfilerInfo2::GetStaticFieldInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="16055-102">ICorProfilerInfo2::GetStaticFieldInfo Method</span></span>
<span data-ttu-id="16055-103">Pobiera wartość wskazującą, rodzaj statyczną, która ma zastosowanie do określonego pola.</span><span class="sxs-lookup"><span data-stu-id="16055-103">Gets a value that indicates the kind of static that applies to the specified field.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="16055-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="16055-104">Syntax</span></span>  
  
```  
HRESULT GetStaticFieldInfo (  
    [in] ClassID               classId,  
    [in] mdFieldDef            fieldToken,  
    [out] COR_PRF_STATIC_TYPE  *pFieldInfo);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="16055-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="16055-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="16055-106">[in] Identyfikator klasy, w którym zdefiniowano pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="16055-106">[in] The ID of the class in which the static field is defined.</span></span>  
  
 `fieldToken`  
 <span data-ttu-id="16055-107">[in] Token metadanych dla pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="16055-107">[in] The metadata token for the static field.</span></span>  
  
 `pFieldInfo`  
 <span data-ttu-id="16055-108">[out] Wskaźnik do wartości [COR_PRF_STATIC_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-static-type-enumeration.md) Wyliczenie wskazujące, czy określone pole jest statyczny, a jeśli tak, rodzaj static dotyczący pola.</span><span class="sxs-lookup"><span data-stu-id="16055-108">[out] A pointer to a value of the [COR_PRF_STATIC_TYPE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-static-type-enumeration.md) enumeration that indicates whether the specified field is static, and if so, the kind of static that applies to the field.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="16055-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="16055-109">Remarks</span></span>  
 <span data-ttu-id="16055-110">Te informacje można określić funkcji do wywołania w celu uzyskania adresu pola statycznego.</span><span class="sxs-lookup"><span data-stu-id="16055-110">This information can be used to determine which function to call to get the address of the static field.</span></span>  
  
 <span data-ttu-id="16055-111">Kod profilera należy sprawdzić metadanych dla pola statycznego upewnić się, że faktycznie ma adres.</span><span class="sxs-lookup"><span data-stu-id="16055-111">The profiler code should still check the metadata for a static field to ensure that it actually has an address.</span></span> <span data-ttu-id="16055-112">Literały statyczne (to znaczy stałych) istnieje tylko w metadanych i nie ma adresu.</span><span class="sxs-lookup"><span data-stu-id="16055-112">Static literals (that is, constants) exist only in the metadata and do not have an address.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="16055-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="16055-113">Requirements</span></span>  
 <span data-ttu-id="16055-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="16055-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="16055-115">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="16055-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="16055-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="16055-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="16055-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="16055-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16055-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="16055-118">See Also</span></span>  
 [<span data-ttu-id="16055-119">ICorProfilerInfo — interfejs</span><span class="sxs-lookup"><span data-stu-id="16055-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="16055-120">ICorProfilerInfo2 — interfejs</span><span class="sxs-lookup"><span data-stu-id="16055-120">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)

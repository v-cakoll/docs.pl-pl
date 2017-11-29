---
title: "ICorProfilerInfo::GetClassIDInfo — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.GetClassIDInfo
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::GetClassIDInfo
helpviewer_keywords:
- GetClassIDInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetClassIDInfo method [.NET Framework profiling]
ms.assetid: 9e93b99e-5aca-415c-8e37-7f33753b612d
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3d8cf1f82ce6df8eed7b0f914003d1b13bf65685
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilerinfogetclassidinfo-method"></a><span data-ttu-id="53101-102">ICorProfilerInfo::GetClassIDInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="53101-102">ICorProfilerInfo::GetClassIDInfo Method</span></span>
<span data-ttu-id="53101-103">Pobiera element nadrzędny Moduł i token metadanych dla określonej klasy.</span><span class="sxs-lookup"><span data-stu-id="53101-103">Gets the parent module and the metadata token for the specified class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53101-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="53101-104">Syntax</span></span>  
  
```  
HRESULT GetClassIDInfo(  
    [in]  ClassID   classId,  
    [out] ModuleID  *pModuleId,  
    [out] mdTypeDef *pTypeDefToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="53101-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="53101-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="53101-106">[in] Identyfikator klasy, do których chcesz uzyskać informacje.</span><span class="sxs-lookup"><span data-stu-id="53101-106">[in] The ID of the class for which to get the information.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="53101-107">[out] Wskaźnik do identyfikator modułu nadrzędnej klasy.</span><span class="sxs-lookup"><span data-stu-id="53101-107">[out] A pointer to the ID of the parent module of the class.</span></span>  
  
 `pTypeDefToken`  
 <span data-ttu-id="53101-108">[out] Wskaźnik do tokenu metadanych dla klasy.</span><span class="sxs-lookup"><span data-stu-id="53101-108">[out] A pointer to the metadata token for the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="53101-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="53101-109">Remarks</span></span>  
 <span data-ttu-id="53101-110">Kod profiler może wywołać [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) uzyskać interfejs metadanych dla danego modułu.</span><span class="sxs-lookup"><span data-stu-id="53101-110">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) to obtain a metadata interface for a given module.</span></span> <span data-ttu-id="53101-111">Token metadanych, która jest zwracana do lokalizacji odwołuje się `pTypeDefToken` następnie może służyć do uzyskania dostępu do klasy metadanych.</span><span class="sxs-lookup"><span data-stu-id="53101-111">The metadata token that is returned to the location referenced by `pTypeDefToken` can then be used to access the metadata for the class.</span></span>  
  
 <span data-ttu-id="53101-112">Aby uzyskać więcej informacji dla typów ogólnych, użyj [ICorProfilerInfo2::GetClassIDInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md).</span><span class="sxs-lookup"><span data-stu-id="53101-112">To get more information for generic types, use [ICorProfilerInfo2::GetClassIDInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="53101-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="53101-113">Requirements</span></span>  
 <span data-ttu-id="53101-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="53101-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="53101-115">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="53101-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="53101-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="53101-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="53101-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="53101-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="53101-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="53101-118">See Also</span></span>  
 [<span data-ttu-id="53101-119">ICorProfilerInfo — interfejs</span><span class="sxs-lookup"><span data-stu-id="53101-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)

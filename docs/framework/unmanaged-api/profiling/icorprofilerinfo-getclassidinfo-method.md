---
title: ICorProfilerInfo::GetClassIDInfo — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetClassIDInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetClassIDInfo
helpviewer_keywords:
- GetClassIDInfo method [.NET Framework profiling]
- ICorProfilerInfo::GetClassIDInfo method [.NET Framework profiling]
ms.assetid: 9e93b99e-5aca-415c-8e37-7f33753b612d
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 97465b5d39b3f6adbb6bccfc7b478ddad97066fc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54563733"
---
# <a name="icorprofilerinfogetclassidinfo-method"></a><span data-ttu-id="00c3b-102">ICorProfilerInfo::GetClassIDInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="00c3b-102">ICorProfilerInfo::GetClassIDInfo Method</span></span>
<span data-ttu-id="00c3b-103">Pobiera element nadrzędny, modułu oraz tokenie metadanych dla określonej klasy.</span><span class="sxs-lookup"><span data-stu-id="00c3b-103">Gets the parent module and the metadata token for the specified class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="00c3b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="00c3b-104">Syntax</span></span>  
  
```  
HRESULT GetClassIDInfo(  
    [in]  ClassID   classId,  
    [out] ModuleID  *pModuleId,  
    [out] mdTypeDef *pTypeDefToken);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="00c3b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="00c3b-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="00c3b-106">[in] Identyfikator klasy, dla którego mają zostać pobrane informacje.</span><span class="sxs-lookup"><span data-stu-id="00c3b-106">[in] The ID of the class for which to get the information.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="00c3b-107">[out] Wskaźnik do identyfikator modułu nadrzędnej klasy.</span><span class="sxs-lookup"><span data-stu-id="00c3b-107">[out] A pointer to the ID of the parent module of the class.</span></span>  
  
 `pTypeDefToken`  
 <span data-ttu-id="00c3b-108">[out] Wskaźnik do tokenu metadanych dla klasy.</span><span class="sxs-lookup"><span data-stu-id="00c3b-108">[out] A pointer to the metadata token for the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="00c3b-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="00c3b-109">Remarks</span></span>  
 <span data-ttu-id="00c3b-110">Program profilujący kodu może wywołać [icorprofilerinfo::getmodulemetadata —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) uzyskać interfejs metadanych dla danego modułu.</span><span class="sxs-lookup"><span data-stu-id="00c3b-110">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) to obtain a metadata interface for a given module.</span></span> <span data-ttu-id="00c3b-111">Token metadanych, które są zwracane do lokalizacji, odwołuje się `pTypeDefToken` następnie może służyć do uzyskania dostępu do klasy metadanych.</span><span class="sxs-lookup"><span data-stu-id="00c3b-111">The metadata token that is returned to the location referenced by `pTypeDefToken` can then be used to access the metadata for the class.</span></span>  
  
 <span data-ttu-id="00c3b-112">Aby uzyskać więcej informacji dla typów ogólnych, należy użyć [icorprofilerinfo2::getclassidinfo2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md).</span><span class="sxs-lookup"><span data-stu-id="00c3b-112">To get more information for generic types, use [ICorProfilerInfo2::GetClassIDInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="00c3b-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="00c3b-113">Requirements</span></span>  
 <span data-ttu-id="00c3b-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="00c3b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="00c3b-115">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="00c3b-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="00c3b-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="00c3b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="00c3b-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="00c3b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00c3b-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="00c3b-118">See also</span></span>
- [<span data-ttu-id="00c3b-119">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="00c3b-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)

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
ms.openlocfilehash: 45abb39fa7266e19bbd375b476f2ab48bfc5914d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59130003"
---
# <a name="icorprofilerinfogetclassidinfo-method"></a><span data-ttu-id="0b5f0-102">ICorProfilerInfo::GetClassIDInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="0b5f0-102">ICorProfilerInfo::GetClassIDInfo Method</span></span>
<span data-ttu-id="0b5f0-103">Pobiera element nadrzędny, modułu oraz tokenie metadanych dla określonej klasy.</span><span class="sxs-lookup"><span data-stu-id="0b5f0-103">Gets the parent module and the metadata token for the specified class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b5f0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0b5f0-104">Syntax</span></span>  
  
```  
HRESULT GetClassIDInfo(  
    [in]  ClassID   classId,  
    [out] ModuleID  *pModuleId,  
    [out] mdTypeDef *pTypeDefToken);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0b5f0-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0b5f0-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="0b5f0-106">[in] Identyfikator klasy, dla którego mają zostać pobrane informacje.</span><span class="sxs-lookup"><span data-stu-id="0b5f0-106">[in] The ID of the class for which to get the information.</span></span>  
  
 `pModuleId`  
 <span data-ttu-id="0b5f0-107">[out] Wskaźnik do identyfikator modułu nadrzędnej klasy.</span><span class="sxs-lookup"><span data-stu-id="0b5f0-107">[out] A pointer to the ID of the parent module of the class.</span></span>  
  
 `pTypeDefToken`  
 <span data-ttu-id="0b5f0-108">[out] Wskaźnik do tokenu metadanych dla klasy.</span><span class="sxs-lookup"><span data-stu-id="0b5f0-108">[out] A pointer to the metadata token for the class.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0b5f0-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0b5f0-109">Remarks</span></span>  
 <span data-ttu-id="0b5f0-110">Program profilujący kodu może wywołać [icorprofilerinfo::getmodulemetadata —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) uzyskać interfejs metadanych dla danego modułu.</span><span class="sxs-lookup"><span data-stu-id="0b5f0-110">The profiler code can call [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) to obtain a metadata interface for a given module.</span></span> <span data-ttu-id="0b5f0-111">Token metadanych, które są zwracane do lokalizacji, odwołuje się `pTypeDefToken` następnie może służyć do uzyskania dostępu do klasy metadanych.</span><span class="sxs-lookup"><span data-stu-id="0b5f0-111">The metadata token that is returned to the location referenced by `pTypeDefToken` can then be used to access the metadata for the class.</span></span>  
  
 <span data-ttu-id="0b5f0-112">Aby uzyskać więcej informacji dla typów ogólnych, należy użyć [icorprofilerinfo2::getclassidinfo2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md).</span><span class="sxs-lookup"><span data-stu-id="0b5f0-112">To get more information for generic types, use [ICorProfilerInfo2::GetClassIDInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-getclassidinfo2-method.md).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b5f0-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0b5f0-113">Requirements</span></span>  
 <span data-ttu-id="0b5f0-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b5f0-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b5f0-115">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0b5f0-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0b5f0-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0b5f0-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="0b5f0-117">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="0b5f0-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0b5f0-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0b5f0-118">See also</span></span>

- [<span data-ttu-id="0b5f0-119">ICorProfilerInfo — Interfejs</span><span class="sxs-lookup"><span data-stu-id="0b5f0-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)

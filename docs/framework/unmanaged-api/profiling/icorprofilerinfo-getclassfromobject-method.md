---
title: ICorProfilerInfo::GetClassFromObject — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetClassFromObject
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetClassFromObject
helpviewer_keywords:
- GetClassFromObject method [.NET Framework profiling]
- ICorProfilerInfo::GetClassFromObject method [.NET Framework profiling]
ms.assetid: b97493fb-713e-49d5-a73e-5688b2ad0700
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 81afb9b40269b04a59c54636c7e88c1f67189593
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59189550"
---
# <a name="icorprofilerinfogetclassfromobject-method"></a><span data-ttu-id="ab526-102">ICorProfilerInfo::GetClassFromObject — Metoda</span><span class="sxs-lookup"><span data-stu-id="ab526-102">ICorProfilerInfo::GetClassFromObject Method</span></span>
<span data-ttu-id="ab526-103">Pobiera `ClassID` obiektu, biorąc pod uwagę jej `ObjectID`.</span><span class="sxs-lookup"><span data-stu-id="ab526-103">Gets the `ClassID` of an object, given its `ObjectID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab526-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ab526-104">Syntax</span></span>  
  
```  
HRESULT GetClassFromObject(  
    [in]  ObjectID objectId,  
    [out] ClassID *pClassId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ab526-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ab526-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="ab526-106">[in] Identyfikator obiektu, dla którego należy pobrać `ClassID`.</span><span class="sxs-lookup"><span data-stu-id="ab526-106">[in] The ID of the object for which to get the `ClassID`.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="ab526-107">[out] Wskaźnik do zwracanego `ClassID`.</span><span class="sxs-lookup"><span data-stu-id="ab526-107">[out] A pointer to the returned `ClassID`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab526-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ab526-108">Remarks</span></span>  
 <span data-ttu-id="ab526-109">Wartość null `pClassId` wskazuje, że `objectId` ma typ, który jest zwolnienie.</span><span class="sxs-lookup"><span data-stu-id="ab526-109">A null `pClassId` indicates that `objectId` has a type that is unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab526-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ab526-110">Requirements</span></span>  
 <span data-ttu-id="ab526-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab526-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab526-112">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ab526-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ab526-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ab526-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="ab526-114">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="ab526-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ab526-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ab526-115">See also</span></span>

- [<span data-ttu-id="ab526-116">ICorProfilerInfo — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ab526-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)

---
title: "ICorProfilerInfo::GetClassFromObject — Metoda"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ffc2e72746074776caee6fa9b87563df41fcc6b6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetclassfromobject-method"></a><span data-ttu-id="a2d67-102">ICorProfilerInfo::GetClassFromObject — Metoda</span><span class="sxs-lookup"><span data-stu-id="a2d67-102">ICorProfilerInfo::GetClassFromObject Method</span></span>
<span data-ttu-id="a2d67-103">Pobiera `ClassID` obiektu podane jego `ObjectID`.</span><span class="sxs-lookup"><span data-stu-id="a2d67-103">Gets the `ClassID` of an object, given its `ObjectID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a2d67-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a2d67-104">Syntax</span></span>  
  
```  
HRESULT GetClassFromObject(  
    [in]  ObjectID objectId,  
    [out] ClassID *pClassId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a2d67-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a2d67-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="a2d67-106">[in] Identyfikator obiektu, dla którego można pobrać `ClassID`.</span><span class="sxs-lookup"><span data-stu-id="a2d67-106">[in] The ID of the object for which to get the `ClassID`.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="a2d67-107">[out] Wskaźnik do zwróconego `ClassID`.</span><span class="sxs-lookup"><span data-stu-id="a2d67-107">[out] A pointer to the returned `ClassID`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a2d67-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a2d67-108">Remarks</span></span>  
 <span data-ttu-id="a2d67-109">Wartość null `pClassId` oznacza to, że `objectId` ma typ, który jest zwalnianie.</span><span class="sxs-lookup"><span data-stu-id="a2d67-109">A null `pClassId` indicates that `objectId` has a type that is unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a2d67-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a2d67-110">Requirements</span></span>  
 <span data-ttu-id="a2d67-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a2d67-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a2d67-112">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a2d67-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a2d67-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a2d67-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a2d67-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a2d67-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a2d67-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a2d67-115">See Also</span></span>  
 [<span data-ttu-id="a2d67-116">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="a2d67-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)

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
ms.openlocfilehash: 104dfcaa4120d72f3aa758b66134050f178fef75
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453424"
---
# <a name="icorprofilerinfogetclassfromobject-method"></a><span data-ttu-id="15c7f-102">ICorProfilerInfo::GetClassFromObject — Metoda</span><span class="sxs-lookup"><span data-stu-id="15c7f-102">ICorProfilerInfo::GetClassFromObject Method</span></span>
<span data-ttu-id="15c7f-103">Pobiera `ClassID` obiektu podane jego `ObjectID`.</span><span class="sxs-lookup"><span data-stu-id="15c7f-103">Gets the `ClassID` of an object, given its `ObjectID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15c7f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="15c7f-104">Syntax</span></span>  
  
```  
HRESULT GetClassFromObject(  
    [in]  ObjectID objectId,  
    [out] ClassID *pClassId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="15c7f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="15c7f-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="15c7f-106">[in] Identyfikator obiektu, dla którego można pobrać `ClassID`.</span><span class="sxs-lookup"><span data-stu-id="15c7f-106">[in] The ID of the object for which to get the `ClassID`.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="15c7f-107">[out] Wskaźnik do zwróconego `ClassID`.</span><span class="sxs-lookup"><span data-stu-id="15c7f-107">[out] A pointer to the returned `ClassID`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="15c7f-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="15c7f-108">Remarks</span></span>  
 <span data-ttu-id="15c7f-109">Wartość null `pClassId` oznacza to, że `objectId` ma typ, który jest zwalnianie.</span><span class="sxs-lookup"><span data-stu-id="15c7f-109">A null `pClassId` indicates that `objectId` has a type that is unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="15c7f-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="15c7f-110">Requirements</span></span>  
 <span data-ttu-id="15c7f-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="15c7f-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="15c7f-112">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="15c7f-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="15c7f-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="15c7f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="15c7f-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="15c7f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15c7f-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="15c7f-115">See Also</span></span>  
 [<span data-ttu-id="15c7f-116">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="15c7f-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)

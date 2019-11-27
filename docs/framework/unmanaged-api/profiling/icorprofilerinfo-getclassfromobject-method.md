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
ms.openlocfilehash: 460162f0fbc9993635d1bce0c5b130358ced4fa7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448150"
---
# <a name="icorprofilerinfogetclassfromobject-method"></a><span data-ttu-id="5d790-102">ICorProfilerInfo::GetClassFromObject — Metoda</span><span class="sxs-lookup"><span data-stu-id="5d790-102">ICorProfilerInfo::GetClassFromObject Method</span></span>
<span data-ttu-id="5d790-103">Pobiera `ClassID` obiektu, uwzględniając jego `ObjectID`.</span><span class="sxs-lookup"><span data-stu-id="5d790-103">Gets the `ClassID` of an object, given its `ObjectID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5d790-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5d790-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClassFromObject(  
    [in]  ObjectID objectId,  
    [out] ClassID *pClassId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5d790-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5d790-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="5d790-106">podczas Identyfikator obiektu, dla którego ma zostać pobrany `ClassID`.</span><span class="sxs-lookup"><span data-stu-id="5d790-106">[in] The ID of the object for which to get the `ClassID`.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="5d790-107">określoną Wskaźnik do zwracanej `ClassID`.</span><span class="sxs-lookup"><span data-stu-id="5d790-107">[out] A pointer to the returned `ClassID`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5d790-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5d790-108">Remarks</span></span>  
 <span data-ttu-id="5d790-109">`pClassId` o wartości null wskazuje, że `objectId` ma typ, który jest wyładowania.</span><span class="sxs-lookup"><span data-stu-id="5d790-109">A null `pClassId` indicates that `objectId` has a type that is unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5d790-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5d790-110">Requirements</span></span>  
 <span data-ttu-id="5d790-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5d790-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5d790-112">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="5d790-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5d790-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5d790-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5d790-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5d790-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d790-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5d790-115">See also</span></span>

- [<span data-ttu-id="5d790-116">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="5d790-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)

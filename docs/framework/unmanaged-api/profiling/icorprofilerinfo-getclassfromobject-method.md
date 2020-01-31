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
ms.openlocfilehash: a5573765486112a83f5ea7cc9258447692f72166
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864074"
---
# <a name="icorprofilerinfogetclassfromobject-method"></a><span data-ttu-id="e4a38-102">ICorProfilerInfo::GetClassFromObject — Metoda</span><span class="sxs-lookup"><span data-stu-id="e4a38-102">ICorProfilerInfo::GetClassFromObject Method</span></span>
<span data-ttu-id="e4a38-103">Pobiera `ClassID` obiektu, uwzględniając jego `ObjectID`.</span><span class="sxs-lookup"><span data-stu-id="e4a38-103">Gets the `ClassID` of an object, given its `ObjectID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4a38-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e4a38-104">Syntax</span></span>  
  
```cpp  
HRESULT GetClassFromObject(  
    [in]  ObjectID objectId,  
    [out] ClassID *pClassId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e4a38-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e4a38-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="e4a38-106">podczas Identyfikator obiektu, dla którego ma zostać pobrany `ClassID`.</span><span class="sxs-lookup"><span data-stu-id="e4a38-106">[in] The ID of the object for which to get the `ClassID`.</span></span>  
  
 `pClassId`  
 <span data-ttu-id="e4a38-107">określoną Wskaźnik do zwracanej `ClassID`.</span><span class="sxs-lookup"><span data-stu-id="e4a38-107">[out] A pointer to the returned `ClassID`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e4a38-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e4a38-108">Remarks</span></span>  
 <span data-ttu-id="e4a38-109">`pClassId` o wartości null wskazuje, że `objectId` ma typ, który jest wyładowania.</span><span class="sxs-lookup"><span data-stu-id="e4a38-109">A null `pClassId` indicates that `objectId` has a type that is unloading.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4a38-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e4a38-110">Requirements</span></span>  
 <span data-ttu-id="e4a38-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e4a38-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e4a38-112">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e4a38-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e4a38-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e4a38-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e4a38-114">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e4a38-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4a38-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e4a38-115">See also</span></span>

- [<span data-ttu-id="e4a38-116">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="e4a38-116">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)

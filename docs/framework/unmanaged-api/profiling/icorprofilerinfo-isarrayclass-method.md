---
title: ICorProfilerInfo::IsArrayClass — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.IsArrayClass
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::IsArrayClass
helpviewer_keywords:
- IsArrayClass method [.NET Framework profiling]
- ICorProfilerInfo::IsArrayClass method [.NET Framework profiling]
ms.assetid: 7f230961-23a6-4d56-ad2d-7a876d65705f
topic_type:
- apiref
ms.openlocfilehash: 57515ac4670b9b7e25bb496851347a62e1b246df
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74438707"
---
# <a name="icorprofilerinfoisarrayclass-method"></a><span data-ttu-id="4c2e9-102">ICorProfilerInfo::IsArrayClass — Metoda</span><span class="sxs-lookup"><span data-stu-id="4c2e9-102">ICorProfilerInfo::IsArrayClass Method</span></span>
<span data-ttu-id="4c2e9-103">Determines whether the specified class is an array class.</span><span class="sxs-lookup"><span data-stu-id="4c2e9-103">Determines whether the specified class is an array class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c2e9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4c2e9-104">Syntax</span></span>  
  
```cpp  
HRESULT IsArrayClass(  
    [in]  ClassID        classId,  
    [out] CorElementType *pBaseElemType,  
    [out] ClassID        *pBaseClassId,  
    [out] ULONG          *pcRank);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4c2e9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4c2e9-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="4c2e9-106">[in] The ID of the class to be examined.</span><span class="sxs-lookup"><span data-stu-id="4c2e9-106">[in] The ID of the class to be examined.</span></span>  
  
 `pBaseElemType`  
 <span data-ttu-id="4c2e9-107">[out] A pointer to a value of the CorElementType enumeration that indicates the type of the array elements.</span><span class="sxs-lookup"><span data-stu-id="4c2e9-107">[out] A pointer to a value of the CorElementType enumeration that indicates the type of the array elements.</span></span>  
  
 `pBaseClassId`  
 <span data-ttu-id="4c2e9-108">[out] A pointer to the class ID of the array elements, when available.</span><span class="sxs-lookup"><span data-stu-id="4c2e9-108">[out] A pointer to the class ID of the array elements, when available.</span></span>  
  
 `pcRank`  
 <span data-ttu-id="4c2e9-109">[out] A pointer to an integer that indicates the rank (that is, number of dimensions) of the array.</span><span class="sxs-lookup"><span data-stu-id="4c2e9-109">[out] A pointer to an integer that indicates the rank (that is, number of dimensions) of the array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4c2e9-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4c2e9-110">Remarks</span></span>  
 <span data-ttu-id="4c2e9-111">If the specified class is an array class, the `IsArrayClass` method returns an S_OK HRESULT and values for any non-null output parameters.</span><span class="sxs-lookup"><span data-stu-id="4c2e9-111">If the specified class is an array class, the `IsArrayClass` method returns an S_OK HRESULT and values for any non-null output parameters.</span></span> <span data-ttu-id="4c2e9-112">Otherwise, it returns S_FALSE.</span><span class="sxs-lookup"><span data-stu-id="4c2e9-112">Otherwise, it returns S_FALSE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4c2e9-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4c2e9-113">Requirements</span></span>  
 <span data-ttu-id="4c2e9-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4c2e9-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4c2e9-115">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4c2e9-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4c2e9-116">**Library:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4c2e9-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4c2e9-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4c2e9-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4c2e9-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4c2e9-118">See also</span></span>

- [<span data-ttu-id="4c2e9-119">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="4c2e9-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)

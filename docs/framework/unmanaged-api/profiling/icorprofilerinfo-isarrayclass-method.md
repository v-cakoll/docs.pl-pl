---
title: "ICorProfilerInfo::IsArrayClass — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo.IsArrayClass
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo::IsArrayClass
helpviewer_keywords:
- IsArrayClass method [.NET Framework profiling]
- ICorProfilerInfo::IsArrayClass method [.NET Framework profiling]
ms.assetid: 7f230961-23a6-4d56-ad2d-7a876d65705f
topic_type: apiref
caps.latest.revision: "14"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a1063aea795d73ebaad0803abb7e555e1bb8b7e4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfoisarrayclass-method"></a><span data-ttu-id="2db83-102">ICorProfilerInfo::IsArrayClass — Metoda</span><span class="sxs-lookup"><span data-stu-id="2db83-102">ICorProfilerInfo::IsArrayClass Method</span></span>
<span data-ttu-id="2db83-103">Określa, czy określona klasa jest klasą tablicy.</span><span class="sxs-lookup"><span data-stu-id="2db83-103">Determines whether the specified class is an array class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2db83-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2db83-104">Syntax</span></span>  
  
```  
HRESULT IsArrayClass(  
    [in]  ClassID        classId,  
    [out] CorElementType *pBaseElemType,  
    [out] ClassID        *pBaseClassId,  
    [out] ULONG          *pcRank);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2db83-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2db83-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="2db83-106">[in] Identyfikator klasy należy zbadać.</span><span class="sxs-lookup"><span data-stu-id="2db83-106">[in] The ID of the class to be examined.</span></span>  
  
 `pBaseElemType`  
 <span data-ttu-id="2db83-107">[out] Wskaźnik do wartości wyliczenia CorElementType, który wskazuje na typ elementów tablicy.</span><span class="sxs-lookup"><span data-stu-id="2db83-107">[out] A pointer to a value of the CorElementType enumeration that indicates the type of the array elements.</span></span>  
  
 `pBaseClassId`  
 <span data-ttu-id="2db83-108">[out] Wskaźnik do Identyfikatora klasy elementów tablicy, jeśli jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="2db83-108">[out] A pointer to the class ID of the array elements, when available.</span></span>  
  
 `pcRank`  
 <span data-ttu-id="2db83-109">[out] Wskaźnik na liczbę całkowitą, która wskazuje rangą tablicy (to znaczy, że liczba wymiarów).</span><span class="sxs-lookup"><span data-stu-id="2db83-109">[out] A pointer to an integer that indicates the rank (that is, number of dimensions) of the array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2db83-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2db83-110">Remarks</span></span>  
 <span data-ttu-id="2db83-111">Jeśli określona klasa jest klasą tablicy `IsArrayClass` metoda zwraca wartość S_OK HRESULT i wartości parametrów wyjściowych inną niż null.</span><span class="sxs-lookup"><span data-stu-id="2db83-111">If the specified class is an array class, the `IsArrayClass` method returns an S_OK HRESULT and values for any non-null output parameters.</span></span> <span data-ttu-id="2db83-112">W przeciwnym wypadku zwraca wartości S_FALSE.</span><span class="sxs-lookup"><span data-stu-id="2db83-112">Otherwise, it returns S_FALSE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2db83-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2db83-113">Requirements</span></span>  
 <span data-ttu-id="2db83-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2db83-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2db83-115">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2db83-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2db83-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2db83-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2db83-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2db83-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2db83-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2db83-118">See Also</span></span>  
 [<span data-ttu-id="2db83-119">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="2db83-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)

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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bf8e74094b15163fe86e18c397f4637557df8329
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57468237"
---
# <a name="icorprofilerinfoisarrayclass-method"></a><span data-ttu-id="83807-102">ICorProfilerInfo::IsArrayClass — Metoda</span><span class="sxs-lookup"><span data-stu-id="83807-102">ICorProfilerInfo::IsArrayClass Method</span></span>
<span data-ttu-id="83807-103">Określa, czy określona klasa jest klasą tablicy.</span><span class="sxs-lookup"><span data-stu-id="83807-103">Determines whether the specified class is an array class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83807-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="83807-104">Syntax</span></span>  
  
```  
HRESULT IsArrayClass(  
    [in]  ClassID        classId,  
    [out] CorElementType *pBaseElemType,  
    [out] ClassID        *pBaseClassId,  
    [out] ULONG          *pcRank);  
```  
  
## <a name="parameters"></a><span data-ttu-id="83807-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="83807-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="83807-106">[in] Identyfikator klasy do badania.</span><span class="sxs-lookup"><span data-stu-id="83807-106">[in] The ID of the class to be examined.</span></span>  
  
 `pBaseElemType`  
 <span data-ttu-id="83807-107">[out] Wskaźnik do wartości corelementtype — wyliczenie, który wskazuje na typ elementów tablicy.</span><span class="sxs-lookup"><span data-stu-id="83807-107">[out] A pointer to a value of the CorElementType enumeration that indicates the type of the array elements.</span></span>  
  
 `pBaseClassId`  
 <span data-ttu-id="83807-108">[out] Wskaźnik do Identyfikatora klasy elementów tablicy, jeśli jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="83807-108">[out] A pointer to the class ID of the array elements, when available.</span></span>  
  
 `pcRank`  
 <span data-ttu-id="83807-109">[out] Wskaźnik na liczbę całkowitą, która określa rangę tablicy (oznacza to, że liczba wymiarów).</span><span class="sxs-lookup"><span data-stu-id="83807-109">[out] A pointer to an integer that indicates the rank (that is, number of dimensions) of the array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="83807-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="83807-110">Remarks</span></span>  
 <span data-ttu-id="83807-111">Jeśli określona klasa jest klasą tablicy `IsArrayClass` metoda zwraca wartość HRESULT S_OK i wartości dla parametrów innych niż null w danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="83807-111">If the specified class is an array class, the `IsArrayClass` method returns an S_OK HRESULT and values for any non-null output parameters.</span></span> <span data-ttu-id="83807-112">W przeciwnym razie zwraca wartość S_FALSE.</span><span class="sxs-lookup"><span data-stu-id="83807-112">Otherwise, it returns S_FALSE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="83807-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="83807-113">Requirements</span></span>  
 <span data-ttu-id="83807-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="83807-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="83807-115">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="83807-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="83807-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="83807-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="83807-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="83807-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83807-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="83807-118">See also</span></span>
- [<span data-ttu-id="83807-119">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="83807-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)

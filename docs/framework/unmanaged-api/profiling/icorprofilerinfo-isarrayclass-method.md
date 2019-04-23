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
ms.openlocfilehash: 350221ae205636cef82581f3fe11367006dd8b2b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59072175"
---
# <a name="icorprofilerinfoisarrayclass-method"></a><span data-ttu-id="483bd-102">ICorProfilerInfo::IsArrayClass — Metoda</span><span class="sxs-lookup"><span data-stu-id="483bd-102">ICorProfilerInfo::IsArrayClass Method</span></span>
<span data-ttu-id="483bd-103">Określa, czy określona klasa jest klasą tablicy.</span><span class="sxs-lookup"><span data-stu-id="483bd-103">Determines whether the specified class is an array class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="483bd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="483bd-104">Syntax</span></span>  
  
```  
HRESULT IsArrayClass(  
    [in]  ClassID        classId,  
    [out] CorElementType *pBaseElemType,  
    [out] ClassID        *pBaseClassId,  
    [out] ULONG          *pcRank);  
```  
  
## <a name="parameters"></a><span data-ttu-id="483bd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="483bd-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="483bd-106">[in] Identyfikator klasy do badania.</span><span class="sxs-lookup"><span data-stu-id="483bd-106">[in] The ID of the class to be examined.</span></span>  
  
 `pBaseElemType`  
 <span data-ttu-id="483bd-107">[out] Wskaźnik do wartości corelementtype — wyliczenie, który wskazuje na typ elementów tablicy.</span><span class="sxs-lookup"><span data-stu-id="483bd-107">[out] A pointer to a value of the CorElementType enumeration that indicates the type of the array elements.</span></span>  
  
 `pBaseClassId`  
 <span data-ttu-id="483bd-108">[out] Wskaźnik do Identyfikatora klasy elementów tablicy, jeśli jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="483bd-108">[out] A pointer to the class ID of the array elements, when available.</span></span>  
  
 `pcRank`  
 <span data-ttu-id="483bd-109">[out] Wskaźnik na liczbę całkowitą, która określa rangę tablicy (oznacza to, że liczba wymiarów).</span><span class="sxs-lookup"><span data-stu-id="483bd-109">[out] A pointer to an integer that indicates the rank (that is, number of dimensions) of the array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="483bd-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="483bd-110">Remarks</span></span>  
 <span data-ttu-id="483bd-111">Jeśli określona klasa jest klasą tablicy `IsArrayClass` metoda zwraca wartość HRESULT S_OK i wartości dla parametrów innych niż null w danych wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="483bd-111">If the specified class is an array class, the `IsArrayClass` method returns an S_OK HRESULT and values for any non-null output parameters.</span></span> <span data-ttu-id="483bd-112">W przeciwnym razie zwraca wartość S_FALSE.</span><span class="sxs-lookup"><span data-stu-id="483bd-112">Otherwise, it returns S_FALSE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="483bd-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="483bd-113">Requirements</span></span>  
 <span data-ttu-id="483bd-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="483bd-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="483bd-115">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="483bd-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="483bd-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="483bd-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="483bd-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="483bd-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="483bd-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="483bd-118">See also</span></span>

- [<span data-ttu-id="483bd-119">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="483bd-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)

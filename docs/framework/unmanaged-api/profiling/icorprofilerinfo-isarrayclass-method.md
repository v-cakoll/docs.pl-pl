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
ms.openlocfilehash: a6e483d820d183afc8ba6a68fc4635730ffd1e51
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76869341"
---
# <a name="icorprofilerinfoisarrayclass-method"></a><span data-ttu-id="ead56-102">ICorProfilerInfo::IsArrayClass — Metoda</span><span class="sxs-lookup"><span data-stu-id="ead56-102">ICorProfilerInfo::IsArrayClass Method</span></span>
<span data-ttu-id="ead56-103">Określa, czy określona Klasa jest klasą Array.</span><span class="sxs-lookup"><span data-stu-id="ead56-103">Determines whether the specified class is an array class.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ead56-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ead56-104">Syntax</span></span>  
  
```cpp  
HRESULT IsArrayClass(  
    [in]  ClassID        classId,  
    [out] CorElementType *pBaseElemType,  
    [out] ClassID        *pBaseClassId,  
    [out] ULONG          *pcRank);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ead56-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ead56-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="ead56-106">podczas Identyfikator klasy, która ma zostać zbadana.</span><span class="sxs-lookup"><span data-stu-id="ead56-106">[in] The ID of the class to be examined.</span></span>  
  
 `pBaseElemType`  
 <span data-ttu-id="ead56-107">określoną Wskaźnik do wartości wyliczenia CorElementType —, który wskazuje typ elementów tablicy.</span><span class="sxs-lookup"><span data-stu-id="ead56-107">[out] A pointer to a value of the CorElementType enumeration that indicates the type of the array elements.</span></span>  
  
 `pBaseClassId`  
 <span data-ttu-id="ead56-108">określoną Wskaźnik do identyfikatora klasy elementów tablicy, jeśli jest dostępny.</span><span class="sxs-lookup"><span data-stu-id="ead56-108">[out] A pointer to the class ID of the array elements, when available.</span></span>  
  
 `pcRank`  
 <span data-ttu-id="ead56-109">określoną Wskaźnik do liczby całkowitej, która wskazuje rangę (czyli liczbę wymiarów) tablicy.</span><span class="sxs-lookup"><span data-stu-id="ead56-109">[out] A pointer to an integer that indicates the rank (that is, number of dimensions) of the array.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ead56-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ead56-110">Remarks</span></span>  
 <span data-ttu-id="ead56-111">Jeśli określona Klasa jest klasą Array, Metoda `IsArrayClass` zwraca S_OK HRESULT i wartości dla wszystkich parametrów wyjściowych o wartości innej niż null.</span><span class="sxs-lookup"><span data-stu-id="ead56-111">If the specified class is an array class, the `IsArrayClass` method returns an S_OK HRESULT and values for any non-null output parameters.</span></span> <span data-ttu-id="ead56-112">W przeciwnym razie zwraca S_FALSE.</span><span class="sxs-lookup"><span data-stu-id="ead56-112">Otherwise, it returns S_FALSE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ead56-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ead56-113">Requirements</span></span>  
 <span data-ttu-id="ead56-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ead56-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ead56-115">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="ead56-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ead56-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ead56-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ead56-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ead56-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ead56-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ead56-118">See also</span></span>

- [<span data-ttu-id="ead56-119">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="ead56-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)

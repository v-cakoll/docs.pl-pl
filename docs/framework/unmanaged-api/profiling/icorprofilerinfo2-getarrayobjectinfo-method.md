---
title: ICorProfilerInfo2::GetArrayObjectInfo — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetArrayObjectInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetArrayObjectInfo
helpviewer_keywords:
- ICorProfilerInfo2::GetArrayObjectInfo method [.NET Framework profiling]
- GetArrayObjectInfo method [.NET Framework profiling]
ms.assetid: bda75017-739f-4ce5-9000-f3b526e8473c
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7fe86fbe7ee51e5f53eeea74d7d5a56046de5e00
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57484397"
---
# <a name="icorprofilerinfo2getarrayobjectinfo-method"></a><span data-ttu-id="5bc1c-102">ICorProfilerInfo2::GetArrayObjectInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="5bc1c-102">ICorProfilerInfo2::GetArrayObjectInfo Method</span></span>
<span data-ttu-id="5bc1c-103">Pobiera szczegółowe informacje dotyczące obiektu array.</span><span class="sxs-lookup"><span data-stu-id="5bc1c-103">Gets detailed information about an array object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5bc1c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5bc1c-104">Syntax</span></span>  
  
```  
HRESULT GetArrayObjectInfo(  
    [in] ObjectID objectId,  
    [in] ULONG32 cDimensions,  
    [out, size_is(cDimensions), length_is(cDimensions)] ULONG32 pDimensionSizes[],  
    [out, size_is(cDimensions), length_is(cDimensions)] int pDimensionLowerBounds[],  
    [out] BYTE **ppData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5bc1c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5bc1c-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="5bc1c-106">[in] Identyfikator obiektu prawidłową tablicą.</span><span class="sxs-lookup"><span data-stu-id="5bc1c-106">[in] The ID of a valid array object.</span></span>  
  
 `cDimensions`  
 <span data-ttu-id="5bc1c-107">[in] Ranga (liczba wymiarów) tablicy.</span><span class="sxs-lookup"><span data-stu-id="5bc1c-107">[in] The rank (number of dimensions) of the array.</span></span>  
  
 `pDimensionSizes`  
 <span data-ttu-id="5bc1c-108">[out] Tablica, która zawiera liczby całkowite, każdy reprezentuje rozmiar wymiaru tablicy.</span><span class="sxs-lookup"><span data-stu-id="5bc1c-108">[out] An array that contains integers, each representing the size of a dimension of the array.</span></span>  
  
 `pDimensionLowerBounds`  
 <span data-ttu-id="5bc1c-109">[out] Tablica, która zawiera liczby całkowite, każda reprezentująca dolna granica wymiaru tablicy.</span><span class="sxs-lookup"><span data-stu-id="5bc1c-109">[out] An array that contains integers, each representing the lower bound of a dimension of the array.</span></span>  
  
 `ppData`  
 <span data-ttu-id="5bc1c-110">[out] Wskaźnik na adres surowy bufor dla tablicy, która jest poukładany zgodnie z konwencją języka C++.</span><span class="sxs-lookup"><span data-stu-id="5bc1c-110">[out] A pointer to the address of the raw buffer for the array, which is laid out according to the C++ convention.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5bc1c-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5bc1c-111">Remarks</span></span>  
 <span data-ttu-id="5bc1c-112">`pDimensionSizes` i `pDimensionLowerBounds` są równoległe tablic, więc elementy znajdujące się w ten sam indeks tablic są właściwości tego samego obiektu.</span><span class="sxs-lookup"><span data-stu-id="5bc1c-112">The `pDimensionSizes` and `pDimensionLowerBounds` are parallel arrays, so the elements located at the same index in each array are characteristics of the same entity.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5bc1c-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5bc1c-113">Requirements</span></span>  
 <span data-ttu-id="5bc1c-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5bc1c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5bc1c-115">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="5bc1c-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="5bc1c-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="5bc1c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5bc1c-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5bc1c-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bc1c-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5bc1c-118">See also</span></span>
- [<span data-ttu-id="5bc1c-119">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="5bc1c-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="5bc1c-120">ICorProfilerInfo2, interfejs</span><span class="sxs-lookup"><span data-stu-id="5bc1c-120">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)

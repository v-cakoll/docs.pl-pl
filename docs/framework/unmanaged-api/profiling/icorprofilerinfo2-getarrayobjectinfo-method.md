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
ms.openlocfilehash: 3ebf8c736cdd1362cae1b1e0b734ce14bea49b18
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67751887"
---
# <a name="icorprofilerinfo2getarrayobjectinfo-method"></a><span data-ttu-id="161d7-102">ICorProfilerInfo2::GetArrayObjectInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="161d7-102">ICorProfilerInfo2::GetArrayObjectInfo Method</span></span>
<span data-ttu-id="161d7-103">Pobiera szczegółowe informacje dotyczące obiektu array.</span><span class="sxs-lookup"><span data-stu-id="161d7-103">Gets detailed information about an array object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="161d7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="161d7-104">Syntax</span></span>  
  
```cpp  
HRESULT GetArrayObjectInfo(  
    [in] ObjectID objectId,  
    [in] ULONG32 cDimensions,  
    [out, size_is(cDimensions), length_is(cDimensions)] ULONG32 pDimensionSizes[],  
    [out, size_is(cDimensions), length_is(cDimensions)] int pDimensionLowerBounds[],  
    [out] BYTE **ppData);  
```  
  
## <a name="parameters"></a><span data-ttu-id="161d7-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="161d7-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="161d7-106">[in] Identyfikator obiektu prawidłową tablicą.</span><span class="sxs-lookup"><span data-stu-id="161d7-106">[in] The ID of a valid array object.</span></span>  
  
 `cDimensions`  
 <span data-ttu-id="161d7-107">[in] Ranga (liczba wymiarów) tablicy.</span><span class="sxs-lookup"><span data-stu-id="161d7-107">[in] The rank (number of dimensions) of the array.</span></span>  
  
 `pDimensionSizes`  
 <span data-ttu-id="161d7-108">[out] Tablica, która zawiera liczby całkowite, każdy reprezentuje rozmiar wymiaru tablicy.</span><span class="sxs-lookup"><span data-stu-id="161d7-108">[out] An array that contains integers, each representing the size of a dimension of the array.</span></span>  
  
 `pDimensionLowerBounds`  
 <span data-ttu-id="161d7-109">[out] Tablica, która zawiera liczby całkowite, każda reprezentująca dolna granica wymiaru tablicy.</span><span class="sxs-lookup"><span data-stu-id="161d7-109">[out] An array that contains integers, each representing the lower bound of a dimension of the array.</span></span>  
  
 `ppData`  
 <span data-ttu-id="161d7-110">[out] Wskaźnik na adres surowy bufor dla tablicy, która jest poukładany zgodnie z opisem w C++ Konwencji.</span><span class="sxs-lookup"><span data-stu-id="161d7-110">[out] A pointer to the address of the raw buffer for the array, which is laid out according to the C++ convention.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="161d7-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="161d7-111">Remarks</span></span>  
 <span data-ttu-id="161d7-112">`pDimensionSizes` i `pDimensionLowerBounds` są równoległe tablic, więc elementy znajdujące się w ten sam indeks tablic są właściwości tego samego obiektu.</span><span class="sxs-lookup"><span data-stu-id="161d7-112">The `pDimensionSizes` and `pDimensionLowerBounds` are parallel arrays, so the elements located at the same index in each array are characteristics of the same entity.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="161d7-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="161d7-113">Requirements</span></span>  
 <span data-ttu-id="161d7-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="161d7-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="161d7-115">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="161d7-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="161d7-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="161d7-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="161d7-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="161d7-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="161d7-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="161d7-118">See also</span></span>

- [<span data-ttu-id="161d7-119">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="161d7-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="161d7-120">ICorProfilerInfo2, interfejs</span><span class="sxs-lookup"><span data-stu-id="161d7-120">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)

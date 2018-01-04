---
title: "ICorProfilerInfo2::GetArrayObjectInfo — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerInfo2.GetArrayObjectInfo
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerInfo2::GetArrayObjectInfo
helpviewer_keywords:
- ICorProfilerInfo2::GetArrayObjectInfo method [.NET Framework profiling]
- GetArrayObjectInfo method [.NET Framework profiling]
ms.assetid: bda75017-739f-4ce5-9000-f3b526e8473c
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b20530081f7c9ad32f4702099abacc78e052ebd9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfo2getarrayobjectinfo-method"></a><span data-ttu-id="1f256-102">ICorProfilerInfo2::GetArrayObjectInfo — Metoda</span><span class="sxs-lookup"><span data-stu-id="1f256-102">ICorProfilerInfo2::GetArrayObjectInfo Method</span></span>
<span data-ttu-id="1f256-103">Pobiera szczegółowe informacje o tablicy obiektów.</span><span class="sxs-lookup"><span data-stu-id="1f256-103">Gets detailed information about an array object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f256-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1f256-104">Syntax</span></span>  
  
```  
HRESULT GetArrayObjectInfo(  
    [in] ObjectID objectId,  
    [in] ULONG32 cDimensions,  
    [out, size_is(cDimensions), length_is(cDimensions)] ULONG32 pDimensionSizes[],  
    [out, size_is(cDimensions), length_is(cDimensions)] int pDimensionLowerBounds[],  
    [out] BYTE **ppData);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1f256-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1f256-105">Parameters</span></span>  
 `objectId`  
 <span data-ttu-id="1f256-106">[in] Identyfikator obiektu prawidłowy tablicy.</span><span class="sxs-lookup"><span data-stu-id="1f256-106">[in] The ID of a valid array object.</span></span>  
  
 `cDimensions`  
 <span data-ttu-id="1f256-107">[in] Ranga (liczba wymiarów) tablicy.</span><span class="sxs-lookup"><span data-stu-id="1f256-107">[in] The rank (number of dimensions) of the array.</span></span>  
  
 `pDimensionSizes`  
 <span data-ttu-id="1f256-108">[out] Tablica zawiera liczb całkowitych, każdy reprezentuje rozmiaru wymiaru tablicy.</span><span class="sxs-lookup"><span data-stu-id="1f256-108">[out] An array that contains integers, each representing the size of a dimension of the array.</span></span>  
  
 `pDimensionLowerBounds`  
 <span data-ttu-id="1f256-109">[out] Tablica zawiera liczb całkowitych, każdy reprezentuje niższa granica wymiaru tablicy.</span><span class="sxs-lookup"><span data-stu-id="1f256-109">[out] An array that contains integers, each representing the lower bound of a dimension of the array.</span></span>  
  
 `ppData`  
 <span data-ttu-id="1f256-110">[out] Wskaźnik do adresu raw buforu dla tablicy, która jest rozmieszczona zgodnie z Konwencją C++.</span><span class="sxs-lookup"><span data-stu-id="1f256-110">[out] A pointer to the address of the raw buffer for the array, which is laid out according to the C++ convention.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f256-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1f256-111">Remarks</span></span>  
 <span data-ttu-id="1f256-112">`pDimensionSizes` i `pDimensionLowerBounds` są równoległych tablic, więc elementy znajdujące się w tym samym indeksie w każdej macierzy właściwości tej samej jednostki.</span><span class="sxs-lookup"><span data-stu-id="1f256-112">The `pDimensionSizes` and `pDimensionLowerBounds` are parallel arrays, so the elements located at the same index in each array are characteristics of the same entity.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f256-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1f256-113">Requirements</span></span>  
 <span data-ttu-id="1f256-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f256-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f256-115">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1f256-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1f256-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1f256-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1f256-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f256-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f256-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1f256-118">See Also</span></span>  
 [<span data-ttu-id="1f256-119">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="1f256-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="1f256-120">ICorProfilerInfo2, interfejs</span><span class="sxs-lookup"><span data-stu-id="1f256-120">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)

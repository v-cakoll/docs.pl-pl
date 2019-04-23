---
title: ICorProfilerInfo2::GetBoxClassLayout — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetBoxClassLayout
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetBoxClassLayout
helpviewer_keywords:
- GetBoxClassLayout method [.NET Framework profiling]
- ICorProfilerInfo2::GetBoxClassLayout method [.NET Framework profiling]
ms.assetid: 624672b5-1189-488a-85d2-3e12b49617c1
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4dac7e38d1e767a3edeef932a0c0916daffe24b8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59092035"
---
# <a name="icorprofilerinfo2getboxclasslayout-method"></a><span data-ttu-id="a1122-102">ICorProfilerInfo2::GetBoxClassLayout — Metoda</span><span class="sxs-lookup"><span data-stu-id="a1122-102">ICorProfilerInfo2::GetBoxClassLayout Method</span></span>
<span data-ttu-id="a1122-103">Pobiera informacje o tym, gdzie typ określona wartość jest znajduje się, gdy jest ona umieszczona.</span><span class="sxs-lookup"><span data-stu-id="a1122-103">Gets information about where the specified value type is located when it is boxed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1122-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a1122-104">Syntax</span></span>  
  
```  
HRESULT GetBoxClassLayout(  
    [in] ClassID classId,  
    [out] ULONG32 *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a1122-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a1122-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="a1122-106">[in] Identyfikator klasy, która opisuje typ wartości, który jest spakowany.</span><span class="sxs-lookup"><span data-stu-id="a1122-106">[in] The ID of the class that describes the value type that is boxed.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="a1122-107">[out] Liczba całkowita, która jest przesunięcie, względem obiektu w ramce wskaźnika identyfikator typu wartości.</span><span class="sxs-lookup"><span data-stu-id="a1122-107">[out] An integer that is the offset, relative to the boxed object ID pointer, of the value type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a1122-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a1122-108">Remarks</span></span>  
 <span data-ttu-id="a1122-109">`pBufferOffset` Wartość wskazuje lokalizację typ wartości w polu.</span><span class="sxs-lookup"><span data-stu-id="a1122-109">The `pBufferOffset` value is the location of the value type within a box.</span></span> <span data-ttu-id="a1122-110">Po `pBufferOffset` jest stosowany do obiektu w ramce układ klasy typ wartości może służyć do interpretowania wartości obiektu.</span><span class="sxs-lookup"><span data-stu-id="a1122-110">After `pBufferOffset` is applied to a boxed object, the value type's class layout can be used to interpret the object's value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1122-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a1122-111">Requirements</span></span>  
 <span data-ttu-id="a1122-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1122-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1122-113">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a1122-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a1122-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a1122-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a1122-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1122-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1122-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a1122-116">See also</span></span>

- [<span data-ttu-id="a1122-117">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="a1122-117">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="a1122-118">ICorProfilerInfo2, interfejs</span><span class="sxs-lookup"><span data-stu-id="a1122-118">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)

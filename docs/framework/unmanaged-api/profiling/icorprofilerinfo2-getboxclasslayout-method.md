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
ms.openlocfilehash: f046fb51753bfa79d333d465e8850794ecc73973
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33453541"
---
# <a name="icorprofilerinfo2getboxclasslayout-method"></a><span data-ttu-id="81be6-102">ICorProfilerInfo2::GetBoxClassLayout — Metoda</span><span class="sxs-lookup"><span data-stu-id="81be6-102">ICorProfilerInfo2::GetBoxClassLayout Method</span></span>
<span data-ttu-id="81be6-103">Pobiera informacje o którym typu podana wartość znajduje się po jej jest opakowany.</span><span class="sxs-lookup"><span data-stu-id="81be6-103">Gets information about where the specified value type is located when it is boxed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="81be6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="81be6-104">Syntax</span></span>  
  
```  
HRESULT GetBoxClassLayout(  
    [in] ClassID classId,  
    [out] ULONG32 *pBufferOffset);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="81be6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="81be6-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="81be6-106">[in] Identyfikator klasy, która opisuje typ wartości, która jest opakowany.</span><span class="sxs-lookup"><span data-stu-id="81be6-106">[in] The ID of the class that describes the value type that is boxed.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="81be6-107">[out] Liczba całkowita, która jest przesunięcie względem obiektu spakowanego wskaźnik identyfikator typu wartości.</span><span class="sxs-lookup"><span data-stu-id="81be6-107">[out] An integer that is the offset, relative to the boxed object ID pointer, of the value type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81be6-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="81be6-108">Remarks</span></span>  
 <span data-ttu-id="81be6-109">`pBufferOffset` Wartość to lokalizacja typu wartości w polu.</span><span class="sxs-lookup"><span data-stu-id="81be6-109">The `pBufferOffset` value is the location of the value type within a box.</span></span> <span data-ttu-id="81be6-110">Po `pBufferOffset` została zastosowana do obiektu spakowanego układ klasy typ wartości może służyć do interpretowania wartości obiektu.</span><span class="sxs-lookup"><span data-stu-id="81be6-110">After `pBufferOffset` is applied to a boxed object, the value type's class layout can be used to interpret the object's value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="81be6-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="81be6-111">Requirements</span></span>  
 <span data-ttu-id="81be6-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="81be6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="81be6-113">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="81be6-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="81be6-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="81be6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="81be6-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="81be6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81be6-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="81be6-116">See Also</span></span>  
 [<span data-ttu-id="81be6-117">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="81be6-117">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [<span data-ttu-id="81be6-118">ICorProfilerInfo2, interfejs</span><span class="sxs-lookup"><span data-stu-id="81be6-118">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)

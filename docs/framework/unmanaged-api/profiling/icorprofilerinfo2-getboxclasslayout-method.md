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
ms.openlocfilehash: 5f98c35f77fdb200be2e96364c9ac06c386faa62
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74436020"
---
# <a name="icorprofilerinfo2getboxclasslayout-method"></a><span data-ttu-id="097c1-102">ICorProfilerInfo2::GetBoxClassLayout — Metoda</span><span class="sxs-lookup"><span data-stu-id="097c1-102">ICorProfilerInfo2::GetBoxClassLayout Method</span></span>
<span data-ttu-id="097c1-103">Pobiera informacje o miejscu, w którym znajduje się określony typ wartości, gdy jest on opakowany.</span><span class="sxs-lookup"><span data-stu-id="097c1-103">Gets information about where the specified value type is located when it is boxed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="097c1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="097c1-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBoxClassLayout(  
    [in] ClassID classId,  
    [out] ULONG32 *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="097c1-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="097c1-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="097c1-106">podczas Identyfikator klasy opisującej typ wartości, która jest opakowana.</span><span class="sxs-lookup"><span data-stu-id="097c1-106">[in] The ID of the class that describes the value type that is boxed.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="097c1-107">określoną Liczba całkowita, która jest przesunięciem względem wskaźnika identyfikatora obiektu zapakowanego typu wartości.</span><span class="sxs-lookup"><span data-stu-id="097c1-107">[out] An integer that is the offset, relative to the boxed object ID pointer, of the value type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="097c1-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="097c1-108">Remarks</span></span>  
 <span data-ttu-id="097c1-109">Wartość `pBufferOffset` jest lokalizacją typu wartości w polu.</span><span class="sxs-lookup"><span data-stu-id="097c1-109">The `pBufferOffset` value is the location of the value type within a box.</span></span> <span data-ttu-id="097c1-110">Po zastosowaniu `pBufferOffset` do obiektu opakowanego układ klasy typu wartości może służyć do interpretowania wartości obiektu.</span><span class="sxs-lookup"><span data-stu-id="097c1-110">After `pBufferOffset` is applied to a boxed object, the value type's class layout can be used to interpret the object's value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="097c1-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="097c1-111">Requirements</span></span>  
 <span data-ttu-id="097c1-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="097c1-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="097c1-113">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="097c1-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="097c1-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="097c1-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="097c1-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="097c1-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="097c1-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="097c1-116">See also</span></span>

- [<span data-ttu-id="097c1-117">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="097c1-117">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="097c1-118">ICorProfilerInfo2, interfejs</span><span class="sxs-lookup"><span data-stu-id="097c1-118">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)

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
ms.openlocfilehash: 500cf74c320438fc1b78f0aac737b418716e1a11
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76862831"
---
# <a name="icorprofilerinfo2getboxclasslayout-method"></a><span data-ttu-id="7d7b5-102">ICorProfilerInfo2::GetBoxClassLayout — Metoda</span><span class="sxs-lookup"><span data-stu-id="7d7b5-102">ICorProfilerInfo2::GetBoxClassLayout Method</span></span>
<span data-ttu-id="7d7b5-103">Pobiera informacje o miejscu, w którym znajduje się określony typ wartości, gdy jest on opakowany.</span><span class="sxs-lookup"><span data-stu-id="7d7b5-103">Gets information about where the specified value type is located when it is boxed.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d7b5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7d7b5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetBoxClassLayout(  
    [in] ClassID classId,  
    [out] ULONG32 *pBufferOffset);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7d7b5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7d7b5-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="7d7b5-106">podczas Identyfikator klasy opisującej typ wartości, która jest opakowana.</span><span class="sxs-lookup"><span data-stu-id="7d7b5-106">[in] The ID of the class that describes the value type that is boxed.</span></span>  
  
 `pBufferOffset`  
 <span data-ttu-id="7d7b5-107">określoną Liczba całkowita, która jest przesunięciem względem wskaźnika identyfikatora obiektu zapakowanego typu wartości.</span><span class="sxs-lookup"><span data-stu-id="7d7b5-107">[out] An integer that is the offset, relative to the boxed object ID pointer, of the value type.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7d7b5-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7d7b5-108">Remarks</span></span>  
 <span data-ttu-id="7d7b5-109">Wartość `pBufferOffset` jest lokalizacją typu wartości w polu.</span><span class="sxs-lookup"><span data-stu-id="7d7b5-109">The `pBufferOffset` value is the location of the value type within a box.</span></span> <span data-ttu-id="7d7b5-110">Po zastosowaniu `pBufferOffset` do obiektu opakowanego układ klasy typu wartości może służyć do interpretowania wartości obiektu.</span><span class="sxs-lookup"><span data-stu-id="7d7b5-110">After `pBufferOffset` is applied to a boxed object, the value type's class layout can be used to interpret the object's value.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d7b5-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7d7b5-111">Requirements</span></span>  
 <span data-ttu-id="7d7b5-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d7b5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d7b5-113">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="7d7b5-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7d7b5-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7d7b5-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7d7b5-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d7b5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d7b5-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7d7b5-116">See also</span></span>

- [<span data-ttu-id="7d7b5-117">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="7d7b5-117">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="7d7b5-118">ICorProfilerInfo2, interfejs</span><span class="sxs-lookup"><span data-stu-id="7d7b5-118">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)

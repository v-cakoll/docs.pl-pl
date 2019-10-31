---
title: Metoda ICorProfilerInfo5::GetEventMask2
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- ICorProfilerInfo5.GetEventMask2
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: f854b68f-009c-4ffb-89cd-ca874d1c0fb7
topic_type:
- apiref
ms.openlocfilehash: 2e814eaba04fd6781d10bbcb67ade9acdefa161d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73114746"
---
# <a name="icorprofilerinfo5geteventmask2-method"></a><span data-ttu-id="a89c1-102">Metoda ICorProfilerInfo5::GetEventMask2</span><span class="sxs-lookup"><span data-stu-id="a89c1-102">ICorProfilerInfo5::GetEventMask2 Method</span></span>
<span data-ttu-id="a89c1-103">[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="a89c1-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="a89c1-104">Pobiera bieżące kategorie zdarzeń, dla których profiler chce otrzymywać powiadomienia z aparatu plików wykonywalnych języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="a89c1-104">Gets the current event categories for which the profiler wants to receive notifications from the common language runtime (CLR).</span></span>  <span data-ttu-id="a89c1-105">Zapewnia funkcje niedostarczone przez metodę [ICorProfilerInfo:: GetEventMask —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a89c1-105">It provides functionality not provided by the [ICorProfilerInfo::GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a89c1-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="a89c1-106">Syntax</span></span>  
  
```cpp
HRESULT GetEventMask2(  
        [out] DWORD* pdwEventsLow,  
        [out] DWORD* pdwEventsHigh  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a89c1-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="a89c1-107">Parameters</span></span>  
 `pdwEventsLow`  
 <span data-ttu-id="a89c1-108">określoną Wskaźnik do 4-bajtowej wartości, która określa kategorie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a89c1-108">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="a89c1-109">Każdy bit steruje inną możliwością, zachowaniem lub typem zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a89c1-109">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="a89c1-110">Bity są opisane w [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) Wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="a89c1-110">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 `pdwEventsHigh`  
 <span data-ttu-id="a89c1-111">określoną Wskaźnik do 4-bajtowej wartości, która określa kategorie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a89c1-111">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span>  <span data-ttu-id="a89c1-112">Każdy bit steruje inną możliwością, zachowaniem lub typem zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a89c1-112">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="a89c1-113">Bity są opisane w [COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) Wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="a89c1-113">The bits are described in the [COR_PRF_HIGH_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a89c1-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a89c1-114">Remarks</span></span>  
 <span data-ttu-id="a89c1-115">Metoda `GetEventMask2` służy do określania, które wywołania zwrotne zasubskrybował Profiler.</span><span class="sxs-lookup"><span data-stu-id="a89c1-115">The `GetEventMask2` method is used to determine which callbacks the profiler has subscribed to.</span></span> <span data-ttu-id="a89c1-116">Zazwyczaj należy wykonać wartość logiczną lub `pdwEventsLow` i `pdwEventsHigh`, a także wszystkie nowe bity, które mają zostać ustawione, a następnie wywołać metodę [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a89c1-116">Typically, you perform a logical OR of the `pdwEventsLow` and `pdwEventsHigh` values and any new bits you want to set, and then call the [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method.</span></span>  
  
 <span data-ttu-id="a89c1-117">Ta metoda jest zalecaną alternatywą dla metody [GetEventMask —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a89c1-117">This method is the recommended alternative to the [GetEventMask](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-geteventmask-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a89c1-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a89c1-118">Requirements</span></span>  
 <span data-ttu-id="a89c1-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a89c1-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a89c1-120">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a89c1-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a89c1-121">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a89c1-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a89c1-122">**Wersje .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a89c1-122">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a89c1-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a89c1-123">See also</span></span>

- [<span data-ttu-id="a89c1-124">ICorProfilerInfo5, interfejs</span><span class="sxs-lookup"><span data-stu-id="a89c1-124">ICorProfilerInfo5 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-interface.md)
- [<span data-ttu-id="a89c1-125">SetEventMask2, metoda</span><span class="sxs-lookup"><span data-stu-id="a89c1-125">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)

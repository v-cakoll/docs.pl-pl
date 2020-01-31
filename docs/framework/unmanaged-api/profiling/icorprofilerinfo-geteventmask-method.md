---
title: ICorProfilerInfo::GetEventMask — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetEventMask
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetEventMask
helpviewer_keywords:
- GetEventMask method [.NET Framework profiling]
- ICorProfilerInfo::GetEventMask method [.NET Framework profiling]
ms.assetid: ec34cc13-45a3-4695-abc3-b3347d4e6fc2
topic_type:
- apiref
ms.openlocfilehash: 63f19fe899abd75380249e171f248480949bc471
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863910"
---
# <a name="icorprofilerinfogeteventmask-method"></a><span data-ttu-id="7de00-102">ICorProfilerInfo::GetEventMask — Metoda</span><span class="sxs-lookup"><span data-stu-id="7de00-102">ICorProfilerInfo::GetEventMask Method</span></span>
<span data-ttu-id="7de00-103">Pobiera bieżące kategorie zdarzeń, dla których profiler chce otrzymywać powiadomienia o zdarzeniach z aparatu plików wykonywalnych języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="7de00-103">Gets the current event categories for which the profiler wants to receive event notifications from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7de00-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7de00-104">Syntax</span></span>  
  
```cpp  
HRESULT GetEventMask(  
    [out] DWORD *pdwEvents);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7de00-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7de00-105">Parameters</span></span>  
 `pdwEvents`  
 <span data-ttu-id="7de00-106">określoną Wskaźnik do 4-bajtowej wartości, która określa kategorie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="7de00-106">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="7de00-107">Każdy bit steruje inną możliwością, zachowaniem lub typem zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="7de00-107">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="7de00-108">Bity są opisane w [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) Wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="7de00-108">The bits are described in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7de00-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7de00-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7de00-110">Zamiast tej metody należy wywołać metodę [GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="7de00-110">You should call the [GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) method instead of this method.</span></span> <span data-ttu-id="7de00-111">Mimo że metoda `SetEventMask` nadal jest obsługiwana, [GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) oferuje dodatkowe funkcje.</span><span class="sxs-lookup"><span data-stu-id="7de00-111">Although the `SetEventMask` method continues to be supported, [GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) provides additional functionality.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7de00-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7de00-112">Requirements</span></span>  
 <span data-ttu-id="7de00-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7de00-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7de00-114">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="7de00-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7de00-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7de00-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7de00-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7de00-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7de00-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7de00-117">See also</span></span>

- [<span data-ttu-id="7de00-118">GetEventMask2, metoda</span><span class="sxs-lookup"><span data-stu-id="7de00-118">GetEventMask2 Method</span></span>](icorprofilerinfo5-geteventmask2-method.md)
- [<span data-ttu-id="7de00-119">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="7de00-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)

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
ms.openlocfilehash: f6a4ee32d1f0bd6f66b2cd2249dd90522062cdab
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120952"
---
# <a name="icorprofilerinfogeteventmask-method"></a><span data-ttu-id="9e6f9-102">ICorProfilerInfo::GetEventMask — Metoda</span><span class="sxs-lookup"><span data-stu-id="9e6f9-102">ICorProfilerInfo::GetEventMask Method</span></span>
<span data-ttu-id="9e6f9-103">Pobiera bieżące kategorie zdarzeń, dla których profiler chce otrzymywać powiadomienia o zdarzeniach z aparatu plików wykonywalnych języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="9e6f9-103">Gets the current event categories for which the profiler wants to receive event notifications from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9e6f9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9e6f9-104">Syntax</span></span>  
  
```cpp  
HRESULT GetEventMask(  
    [out] DWORD *pdwEvents);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9e6f9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="9e6f9-105">Parameters</span></span>  
 `pdwEvents`  
 <span data-ttu-id="9e6f9-106">określoną Wskaźnik do 4-bajtowej wartości, która określa kategorie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="9e6f9-106">[out] A pointer to a 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="9e6f9-107">Każdy bit steruje inną możliwością, zachowaniem lub typem zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="9e6f9-107">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="9e6f9-108">Bity są opisane w [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) Wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="9e6f9-108">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="9e6f9-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9e6f9-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9e6f9-110">Zamiast tej metody należy wywołać metodę [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="9e6f9-110">You should call the [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) method instead of this method.</span></span> <span data-ttu-id="9e6f9-111">Mimo że metoda `SetEventMask` nadal jest obsługiwana, [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) oferuje dodatkowe funkcje.</span><span class="sxs-lookup"><span data-stu-id="9e6f9-111">Although the `SetEventMask` method continues to be supported, [GetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md) provides additional functionality.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9e6f9-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9e6f9-112">Requirements</span></span>  
 <span data-ttu-id="9e6f9-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9e6f9-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9e6f9-114">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="9e6f9-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="9e6f9-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="9e6f9-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9e6f9-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9e6f9-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e6f9-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9e6f9-117">See also</span></span>

- [<span data-ttu-id="9e6f9-118">GetEventMask2, metoda</span><span class="sxs-lookup"><span data-stu-id="9e6f9-118">GetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-geteventmask2-method.md)
- [<span data-ttu-id="9e6f9-119">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="9e6f9-119">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)

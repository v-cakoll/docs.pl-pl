---
title: ICorProfilerInfo::SetEventMask — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.SetEventMask
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::SetEventMask
helpviewer_keywords:
- ICorProfilerInfo::SetEventMask method [.NET Framework profiling]
- SetEventMask method [.NET Framework profiling]
ms.assetid: 44bc0f56-32fa-491e-a62d-52fc96d48125
topic_type:
- apiref
ms.openlocfilehash: b79668130570dc69a580fbf7da4dc122389d9ef0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73136697"
---
# <a name="icorprofilerinfoseteventmask-method"></a><span data-ttu-id="2c303-102">ICorProfilerInfo::SetEventMask — Metoda</span><span class="sxs-lookup"><span data-stu-id="2c303-102">ICorProfilerInfo::SetEventMask Method</span></span>
<span data-ttu-id="2c303-103">Ustawia wartość określającą typy zdarzeń, dla których profiler chce otrzymywać powiadomienia z aparatu plików wykonywalnych języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="2c303-103">Sets a value that specifies the types of events for which the profiler wants to receive notification from the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c303-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2c303-104">Syntax</span></span>  
  
```cpp  
HRESULT SetEventMask(  
    [in] DWORD dwEvents);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2c303-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2c303-105">Parameters</span></span>  
 `dwEvents`  
 <span data-ttu-id="2c303-106">podczas Wartość 4-bajtowa, która określa kategorie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="2c303-106">[in] A 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="2c303-107">Każdy bit steruje inną możliwością, zachowaniem lub typem zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="2c303-107">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="2c303-108">Bity są opisane w [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) Wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="2c303-108">The bits are described in the [COR_PRF_MONITOR](../../../../docs/framework/unmanaged-api/profiling/cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2c303-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2c303-109">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2c303-110">Zamiast tej metody należy wywołać metodę [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) .</span><span class="sxs-lookup"><span data-stu-id="2c303-110">You should call the [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) method instead of this method.</span></span> <span data-ttu-id="2c303-111">Mimo że metoda `SetEventMask` nadal jest obsługiwana, [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) oferuje dodatkowe funkcje.</span><span class="sxs-lookup"><span data-stu-id="2c303-111">Although the `SetEventMask` method continues to be supported, [SetEventMask2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md) provides additional functionality.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2c303-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2c303-112">Requirements</span></span>  
 <span data-ttu-id="2c303-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2c303-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2c303-114">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="2c303-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2c303-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="2c303-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2c303-116">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2c303-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2c303-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2c303-117">See also</span></span>

- [<span data-ttu-id="2c303-118">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="2c303-118">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="2c303-119">SetEventMask2, metoda</span><span class="sxs-lookup"><span data-stu-id="2c303-119">SetEventMask2 Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo5-seteventmask2-method.md)

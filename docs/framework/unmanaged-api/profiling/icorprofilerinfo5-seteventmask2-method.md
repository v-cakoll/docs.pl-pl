---
title: Metoda ICorProfilerInfo5::SetEventMask2
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- IcorProfilerInfo5.SetEventMask2
api_location:
- mscorwks.dll
api_type:
- COM
ms.assetid: 05dbbe2b-049c-4a60-be69-2ad7a949405e
topic_type:
- apiref
ms.openlocfilehash: 8027cdcde8281c363207e309bf65fcd90c03b626
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84495635"
---
# <a name="icorprofilerinfo5seteventmask2-method"></a><span data-ttu-id="52358-102">Metoda ICorProfilerInfo5::SetEventMask2</span><span class="sxs-lookup"><span data-stu-id="52358-102">ICorProfilerInfo5::SetEventMask2 Method</span></span>
<span data-ttu-id="52358-103">[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="52358-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="52358-104">Ustawia wartość określającą typy zdarzeń, dla których profiler chce otrzymywać powiadomienia o zdarzeniach z aparatu plików wykonywalnych języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="52358-104">Sets a value that specifies the types of events for which the profiler wants to receive event notifications from the common language runtime (CLR).</span></span> <span data-ttu-id="52358-105">Zapewnia większą funkcjonalność niż Metoda [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) .</span><span class="sxs-lookup"><span data-stu-id="52358-105">It provides more functionality than the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52358-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="52358-106">Syntax</span></span>  
  
```cpp
HRESULT SetEventMask2(        [in] DWORD dwEventsLow,        [in] DWORD dwEventsHigh  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="52358-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="52358-107">Parameters</span></span>  
 `dwEventsLow`  
 <span data-ttu-id="52358-108">podczas Wartość 4-bajtowa, która określa kategorie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="52358-108">[in] A 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="52358-109">Każdy bit steruje inną możliwością, zachowaniem lub typem zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="52358-109">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="52358-110">Bity są opisane w [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) Wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="52358-110">The bits are described in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 `dwEventsHigh`  
 <span data-ttu-id="52358-111">podczas Wartość 4-bajtowa, która określa kategorie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="52358-111">[in] A 4-byte value that specifies the categories of events.</span></span>  <span data-ttu-id="52358-112">Każdy bit steruje inną możliwością, zachowaniem lub typem zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="52358-112">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="52358-113">Bity są opisane w [COR_PRF_HIGH_MONITOR](cor-prf-high-monitor-enumeration.md) Wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="52358-113">The bits are described in the [COR_PRF_HIGH_MONITOR](cor-prf-high-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="52358-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="52358-114">Remarks</span></span>  
 <span data-ttu-id="52358-115">`SetEventMask2`Metoda służy do ustawiania wywołań zwrotnych, do których jest subskrybowany Profiler.</span><span class="sxs-lookup"><span data-stu-id="52358-115">The `SetEventMask2` method is used to set the callbacks to which the profiler subscribes.</span></span> <span data-ttu-id="52358-116">Zazwyczaj należy wywołać metodę [GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) , aby określić, które bity są ustawione, wykonać wartość logiczną lub jego `pdwEventsLow` wartości oraz `pdwEventsHigh` wszystkie nowe bity, które mają zostać ustawione, a następnie wywołać `SetEventMask2` metodę.</span><span class="sxs-lookup"><span data-stu-id="52358-116">Typically, you call the [GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) method to determine which bits are set, perform a logical OR of its `pdwEventsLow` and `pdwEventsHigh` values and any new bits you want to set, and then call the `SetEventMask2` method.</span></span>  
  
 <span data-ttu-id="52358-117">Ta metoda jest zalecaną alternatywą dla metody [SetEventMask](icorprofilerinfo-seteventmask-method.md) .</span><span class="sxs-lookup"><span data-stu-id="52358-117">This method is the recommended alternative to the [SetEventMask](icorprofilerinfo-seteventmask-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52358-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="52358-118">Requirements</span></span>  
 <span data-ttu-id="52358-119">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="52358-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="52358-120">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="52358-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="52358-121">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="52358-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="52358-122">**.NET Framework wersje:**[!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="52358-122">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52358-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="52358-123">See also</span></span>

- [<span data-ttu-id="52358-124">ICorProfilerInfo5, interfejs</span><span class="sxs-lookup"><span data-stu-id="52358-124">ICorProfilerInfo5 Interface</span></span>](icorprofilerinfo5-interface.md)
- [<span data-ttu-id="52358-125">GetEventMask2, metoda</span><span class="sxs-lookup"><span data-stu-id="52358-125">GetEventMask2 Method</span></span>](icorprofilerinfo5-geteventmask2-method.md)

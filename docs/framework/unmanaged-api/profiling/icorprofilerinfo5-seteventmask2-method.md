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
ms.openlocfilehash: 10e84b729c8af607165009a8591a69dbc1afcb1e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76868385"
---
# <a name="icorprofilerinfo5seteventmask2-method"></a><span data-ttu-id="a17bf-102">Metoda ICorProfilerInfo5::SetEventMask2</span><span class="sxs-lookup"><span data-stu-id="a17bf-102">ICorProfilerInfo5::SetEventMask2 Method</span></span>
<span data-ttu-id="a17bf-103">[Obsługiwane w .NET Framework 4.5.2 i nowszych wersjach]</span><span class="sxs-lookup"><span data-stu-id="a17bf-103">[Supported in the .NET Framework 4.5.2 and later versions]</span></span>  
  
 <span data-ttu-id="a17bf-104">Ustawia wartość określającą typy zdarzeń, dla których profiler chce otrzymywać powiadomienia o zdarzeniach z aparatu plików wykonywalnych języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="a17bf-104">Sets a value that specifies the types of events for which the profiler wants to receive event notifications from the common language runtime (CLR).</span></span> <span data-ttu-id="a17bf-105">Zapewnia większą funkcjonalność niż Metoda [ICorProfilerInfo:: SetEventMask](icorprofilerinfo-seteventmask-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a17bf-105">It provides more functionality than the [ICorProfilerInfo::SetEventMask](icorprofilerinfo-seteventmask-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a17bf-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="a17bf-106">Syntax</span></span>  
  
```cpp
HRESULT SetEventMask2(        [in] DWORD dwEventsLow,        [in] DWORD dwEventsHigh  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a17bf-107">Parametry</span><span class="sxs-lookup"><span data-stu-id="a17bf-107">Parameters</span></span>  
 `dwEventsLow`  
 <span data-ttu-id="a17bf-108">podczas Wartość 4-bajtowa, która określa kategorie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a17bf-108">[in] A 4-byte value that specifies the categories of events.</span></span> <span data-ttu-id="a17bf-109">Każdy bit steruje inną możliwością, zachowaniem lub typem zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a17bf-109">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="a17bf-110">Bity są opisane w [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) Wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="a17bf-110">The bits are described in the [COR_PRF_MONITOR](cor-prf-monitor-enumeration.md) enumeration.</span></span>  
  
 `dwEventsHigh`  
 <span data-ttu-id="a17bf-111">podczas Wartość 4-bajtowa, która określa kategorie zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="a17bf-111">[in] A 4-byte value that specifies the categories of events.</span></span>  <span data-ttu-id="a17bf-112">Każdy bit steruje inną możliwością, zachowaniem lub typem zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="a17bf-112">Each bit controls a different capability, behavior, or type of event.</span></span> <span data-ttu-id="a17bf-113">Bity są opisane w [COR_PRF_HIGH_MONITOR](cor-prf-high-monitor-enumeration.md) Wyliczenie.</span><span class="sxs-lookup"><span data-stu-id="a17bf-113">The bits are described in the [COR_PRF_HIGH_MONITOR](cor-prf-high-monitor-enumeration.md) enumeration.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a17bf-114">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a17bf-114">Remarks</span></span>  
 <span data-ttu-id="a17bf-115">Metoda `SetEventMask2` służy do ustawiania wywołań zwrotnych, do których jest subskrybowany Profiler.</span><span class="sxs-lookup"><span data-stu-id="a17bf-115">The `SetEventMask2` method is used to set the callbacks to which the profiler subscribes.</span></span> <span data-ttu-id="a17bf-116">Zazwyczaj należy wywołać metodę [GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) , aby określić, które bity są ustawione, wykonywać wartości logiczne lub `pdwEventsLow` i `pdwEventsHigh`, a także wszelkie nowe bity, które chcesz ustawić, a następnie wywołać metodę `SetEventMask2`.</span><span class="sxs-lookup"><span data-stu-id="a17bf-116">Typically, you call the [GetEventMask2](icorprofilerinfo5-geteventmask2-method.md) method to determine which bits are set, perform a logical OR of its `pdwEventsLow` and `pdwEventsHigh` values and any new bits you want to set, and then call the `SetEventMask2` method.</span></span>  
  
 <span data-ttu-id="a17bf-117">Ta metoda jest zalecaną alternatywą dla metody [SetEventMask](icorprofilerinfo-seteventmask-method.md) .</span><span class="sxs-lookup"><span data-stu-id="a17bf-117">This method is the recommended alternative to the [SetEventMask](icorprofilerinfo-seteventmask-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a17bf-118">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a17bf-118">Requirements</span></span>  
 <span data-ttu-id="a17bf-119">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a17bf-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a17bf-120">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="a17bf-120">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a17bf-121">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a17bf-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a17bf-122">**Wersje .NET Framework:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a17bf-122">**.NET Framework Versions:** [!INCLUDE[net_current_v452plus](../../../../includes/net-current-v452plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a17bf-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a17bf-123">See also</span></span>

- [<span data-ttu-id="a17bf-124">ICorProfilerInfo5, interfejs</span><span class="sxs-lookup"><span data-stu-id="a17bf-124">ICorProfilerInfo5 Interface</span></span>](icorprofilerinfo5-interface.md)
- [<span data-ttu-id="a17bf-125">GetEventMask2, metoda</span><span class="sxs-lookup"><span data-stu-id="a17bf-125">GetEventMask2 Method</span></span>](icorprofilerinfo5-geteventmask2-method.md)

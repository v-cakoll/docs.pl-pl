---
title: ICorProfilerCallback::Shutdown — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.Shutdown
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::Shutdown
helpviewer_keywords:
- ICorProfilerCallback::Shutdown method [.NET Framework profiling]
- Shutdown method [.NET Framework profiling]
ms.assetid: 1ea194f0-a331-4855-a2ce-37393b8e5f84
topic_type:
- apiref
ms.openlocfilehash: f6873de1a864489d144a671b1a9e1349eaf77d15
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84503188"
---
# <a name="icorprofilercallbackshutdown-method"></a><span data-ttu-id="dcf6b-102">ICorProfilerCallback::Shutdown — Metoda</span><span class="sxs-lookup"><span data-stu-id="dcf6b-102">ICorProfilerCallback::Shutdown Method</span></span>
<span data-ttu-id="dcf6b-103">Powiadamia program profilujący, że aplikacja jest zamykana.</span><span class="sxs-lookup"><span data-stu-id="dcf6b-103">Notifies the profiler that the application is shutting down.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcf6b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dcf6b-104">Syntax</span></span>  
  
```cpp  
HRESULT Shutdown();  
```  
  
## <a name="remarks"></a><span data-ttu-id="dcf6b-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dcf6b-105">Remarks</span></span>  
 <span data-ttu-id="dcf6b-106">Kod profilera nie może bezpiecznie wywołać metod interfejsu [ICorProfilerInfo](icorprofilerinfo-interface.md) po `Shutdown` wywołaniu metody.</span><span class="sxs-lookup"><span data-stu-id="dcf6b-106">The profiler code cannot safely call methods of the [ICorProfilerInfo](icorprofilerinfo-interface.md) interface after the `Shutdown` method is called.</span></span> <span data-ttu-id="dcf6b-107">Wszystkie wywołania `ICorProfilerInfo` metod powodują niezdefiniowane zachowanie po `Shutdown` powrocie metody.</span><span class="sxs-lookup"><span data-stu-id="dcf6b-107">Any calls to `ICorProfilerInfo` methods result in undefined behavior after the `Shutdown` method returns.</span></span> <span data-ttu-id="dcf6b-108">Po zamknięciu mogą nadal występować pewne niezmienne zdarzenia. Profiler powinien zwrócić uwagę natychmiast po wystąpieniu tego problemu.</span><span class="sxs-lookup"><span data-stu-id="dcf6b-108">Certain immutable events may still occur after shutdown; the profiler should take care to return immediately when this occurs.</span></span>  
  
 <span data-ttu-id="dcf6b-109">`Shutdown`Metoda zostanie wywołana tylko wtedy, gdy zarządzana aplikacja, która jest profilowana, została uruchomiona jako kod zarządzany (oznacza to, że początkowa ramka na stosie procesów jest zarządzana).</span><span class="sxs-lookup"><span data-stu-id="dcf6b-109">The `Shutdown` method will be called only if the managed application that is being profiled started as managed code (that is, the initial frame on the process stack is managed).</span></span> <span data-ttu-id="dcf6b-110">Jeśli aplikacja została uruchomiona jako kod niezarządzany, ale później przeskoczy do kodu zarządzanego, tworząc wystąpienie środowiska uruchomieniowego języka wspólnego (CLR), wówczas `Shutdown` nie zostanie wywołane.</span><span class="sxs-lookup"><span data-stu-id="dcf6b-110">If the application started as unmanaged code but later jumped into managed code, thereby creating an instance of the common language runtime (CLR), then `Shutdown` will not be called.</span></span> <span data-ttu-id="dcf6b-111">W takich przypadkach Profiler powinien zawierać w swojej bibliotece `DllMain` procedurę, która używa wartości DLL_PROCESS_DETACH do zwolnienia wszelkich zasobów i przeprowadzania czyszczenia danych, takich jak opróżnianie śladów na dysk i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="dcf6b-111">For these cases, the profiler should include in its library a `DllMain` routine that uses the DLL_PROCESS_DETACH value to free any resources and perform clean-up processing of its data, such as flushing traces to disk and so on.</span></span>  
  
 <span data-ttu-id="dcf6b-112">Ogólnie rzecz biorąc, profiler musi poradzić sobie z nieoczekiwanymi zamknięciami.</span><span class="sxs-lookup"><span data-stu-id="dcf6b-112">In general, the profiler must cope with unexpected shutdowns.</span></span> <span data-ttu-id="dcf6b-113">Na przykład proces może być zatrzymany przez `TerminateProcess` metodę Win32's (zadeklarowany w Winbase. h).</span><span class="sxs-lookup"><span data-stu-id="dcf6b-113">For example, a process might be halted by Win32's `TerminateProcess` method (declared in Winbase.h).</span></span> <span data-ttu-id="dcf6b-114">W innych przypadkach środowisko CLR zatrzyma pewne zarządzane wątki (wątki w tle) bez dostarczania do nich uporządkowanych komunikatów o zniszczeniu.</span><span class="sxs-lookup"><span data-stu-id="dcf6b-114">In other cases, the CLR will halt certain managed threads (background threads) without delivering orderly destruction messages for them.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dcf6b-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dcf6b-115">Requirements</span></span>  
 <span data-ttu-id="dcf6b-116">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dcf6b-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dcf6b-117">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="dcf6b-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="dcf6b-118">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="dcf6b-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dcf6b-119">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dcf6b-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dcf6b-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="dcf6b-120">See also</span></span>

- [<span data-ttu-id="dcf6b-121">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="dcf6b-121">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="dcf6b-122">Initialize — Metoda</span><span class="sxs-lookup"><span data-stu-id="dcf6b-122">Initialize Method</span></span>](icorprofilercallback-initialize-method.md)

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
ms.openlocfilehash: 490f9dd5446a51bd07881cdb9825d737e380a63e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76865860"
---
# <a name="icorprofilercallbackshutdown-method"></a><span data-ttu-id="0bd81-102">ICorProfilerCallback::Shutdown — Metoda</span><span class="sxs-lookup"><span data-stu-id="0bd81-102">ICorProfilerCallback::Shutdown Method</span></span>
<span data-ttu-id="0bd81-103">Powiadamia program profilujący, że aplikacja jest zamykana.</span><span class="sxs-lookup"><span data-stu-id="0bd81-103">Notifies the profiler that the application is shutting down.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0bd81-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0bd81-104">Syntax</span></span>  
  
```cpp  
HRESULT Shutdown();  
```  
  
## <a name="remarks"></a><span data-ttu-id="0bd81-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0bd81-105">Remarks</span></span>  
 <span data-ttu-id="0bd81-106">Kod profilera nie może bezpiecznie wywołać metod interfejsu [ICorProfilerInfo](icorprofilerinfo-interface.md) po wywołaniu metody `Shutdown`.</span><span class="sxs-lookup"><span data-stu-id="0bd81-106">The profiler code cannot safely call methods of the [ICorProfilerInfo](icorprofilerinfo-interface.md) interface after the `Shutdown` method is called.</span></span> <span data-ttu-id="0bd81-107">Wszystkie wywołania metod `ICorProfilerInfo` powodują niezdefiniowane zachowanie po powrocie metody `Shutdown`.</span><span class="sxs-lookup"><span data-stu-id="0bd81-107">Any calls to `ICorProfilerInfo` methods result in undefined behavior after the `Shutdown` method returns.</span></span> <span data-ttu-id="0bd81-108">Po zamknięciu mogą nadal występować pewne niezmienne zdarzenia. Profiler powinien zwrócić uwagę natychmiast po wystąpieniu tego problemu.</span><span class="sxs-lookup"><span data-stu-id="0bd81-108">Certain immutable events may still occur after shutdown; the profiler should take care to return immediately when this occurs.</span></span>  
  
 <span data-ttu-id="0bd81-109">Metoda `Shutdown` zostanie wywołana tylko wtedy, gdy zarządzana aplikacja, która jest profilowana, została uruchomiona jako kod zarządzany (oznacza to, że początkowa ramka na stosie procesów jest zarządzana).</span><span class="sxs-lookup"><span data-stu-id="0bd81-109">The `Shutdown` method will be called only if the managed application that is being profiled started as managed code (that is, the initial frame on the process stack is managed).</span></span> <span data-ttu-id="0bd81-110">Jeśli aplikacja została uruchomiona jako kod niezarządzany, ale później przeskoczy do kodu zarządzanego, tworząc wystąpienie środowiska uruchomieniowego języka wspólnego (CLR), a następnie `Shutdown` nie zostanie wywołana.</span><span class="sxs-lookup"><span data-stu-id="0bd81-110">If the application started as unmanaged code but later jumped into managed code, thereby creating an instance of the common language runtime (CLR), then `Shutdown` will not be called.</span></span> <span data-ttu-id="0bd81-111">W takich przypadkach Profiler powinien znajdować się w swojej bibliotece `DllMain` procedura, która używa wartości DLL_PROCESS_DETACH do zwolnienia wszelkich zasobów i wykonywania czyszczenia danych, takich jak opróżnianie śladów na dysk i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="0bd81-111">For these cases, the profiler should include in its library a `DllMain` routine that uses the DLL_PROCESS_DETACH value to free any resources and perform clean-up processing of its data, such as flushing traces to disk and so on.</span></span>  
  
 <span data-ttu-id="0bd81-112">Ogólnie rzecz biorąc, profiler musi poradzić sobie z nieoczekiwanymi zamknięciami.</span><span class="sxs-lookup"><span data-stu-id="0bd81-112">In general, the profiler must cope with unexpected shutdowns.</span></span> <span data-ttu-id="0bd81-113">Na przykład proces może być zatrzymany przez metodę Win32's `TerminateProcess` (zadeklarowany w Winbase. h).</span><span class="sxs-lookup"><span data-stu-id="0bd81-113">For example, a process might be halted by Win32's `TerminateProcess` method (declared in Winbase.h).</span></span> <span data-ttu-id="0bd81-114">W innych przypadkach środowisko CLR zatrzyma pewne zarządzane wątki (wątki w tle) bez dostarczania do nich uporządkowanych komunikatów o zniszczeniu.</span><span class="sxs-lookup"><span data-stu-id="0bd81-114">In other cases, the CLR will halt certain managed threads (background threads) without delivering orderly destruction messages for them.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0bd81-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0bd81-115">Requirements</span></span>  
 <span data-ttu-id="0bd81-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0bd81-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0bd81-117">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="0bd81-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0bd81-118">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0bd81-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0bd81-119">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0bd81-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0bd81-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0bd81-120">See also</span></span>

- [<span data-ttu-id="0bd81-121">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="0bd81-121">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)
- [<span data-ttu-id="0bd81-122">Initialize, metoda</span><span class="sxs-lookup"><span data-stu-id="0bd81-122">Initialize Method</span></span>](icorprofilercallback-initialize-method.md)

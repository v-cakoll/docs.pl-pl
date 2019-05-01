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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1696cb49170ba245a657e5efb6c8ba4b694af32f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62041759"
---
# <a name="icorprofilercallbackshutdown-method"></a><span data-ttu-id="cd900-102">ICorProfilerCallback::Shutdown — Metoda</span><span class="sxs-lookup"><span data-stu-id="cd900-102">ICorProfilerCallback::Shutdown Method</span></span>
<span data-ttu-id="cd900-103">Powiadamia program profilujący, że aplikacja jest zamykana.</span><span class="sxs-lookup"><span data-stu-id="cd900-103">Notifies the profiler that the application is shutting down.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd900-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cd900-104">Syntax</span></span>  
  
```  
HRESULT Shutdown();  
```  
  
## <a name="remarks"></a><span data-ttu-id="cd900-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cd900-105">Remarks</span></span>  
 <span data-ttu-id="cd900-106">Kod profilera nie można bezpiecznie wywołać metody [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) interfejsu po `Shutdown` metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="cd900-106">The profiler code cannot safely call methods of the [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) interface after the `Shutdown` method is called.</span></span> <span data-ttu-id="cd900-107">Wszelkie wywołania `ICorProfilerInfo` metody spowodować niezdefiniowane zachowanie po `Shutdown` metoda zwraca.</span><span class="sxs-lookup"><span data-stu-id="cd900-107">Any calls to `ICorProfilerInfo` methods result in undefined behavior after the `Shutdown` method returns.</span></span> <span data-ttu-id="cd900-108">Niektóre zdarzenia niezmiennego nadal mogą wystąpić po zamknięciu systemu; Program profilujący powinien zajmie się do zwrócenia natychmiast w takiej sytuacji.</span><span class="sxs-lookup"><span data-stu-id="cd900-108">Certain immutable events may still occur after shutdown; the profiler should take care to return immediately when this occurs.</span></span>  
  
 <span data-ttu-id="cd900-109">`Shutdown` Metoda zostanie wywołana tylko wtedy, gdy w aplikacji zarządzanej, która jest profilowana pracę jako kod zarządzany (czyli początkowej ramki na stosie proces odbywa się).</span><span class="sxs-lookup"><span data-stu-id="cd900-109">The `Shutdown` method will be called only if the managed application that is being profiled started as managed code (that is, the initial frame on the process stack is managed).</span></span> <span data-ttu-id="cd900-110">Jeśli aplikacja uruchomiona jako kod niezarządzany, ale później wyniósł wywołanie kodu zarządzanego, tworząc wystąpienie środowisko uruchomieniowe języka wspólnego (CLR), następnie `Shutdown` nie zostaną wywołane.</span><span class="sxs-lookup"><span data-stu-id="cd900-110">If the application started as unmanaged code but later jumped into managed code, thereby creating an instance of the common language runtime (CLR), then `Shutdown` will not be called.</span></span> <span data-ttu-id="cd900-111">W takich przypadkach program profilujący powinien zawierać w swojej bibliotece `DllMain` procedura, która używa komunikat DLL_PROCESS_DETACH wartość zwolnić wszystkie zasoby do wykonywania oczyszczania przetwarzania swoich danych, takich jak opróżniania danych śledzenia na dysku, i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="cd900-111">For these cases, the profiler should include in its library a `DllMain` routine that uses the DLL_PROCESS_DETACH value to free any resources and perform clean-up processing of its data, such as flushing traces to disk and so on.</span></span>  
  
 <span data-ttu-id="cd900-112">Ogólnie rzecz biorąc program profilujący musi sprostać nieoczekiwanego zamknięcia systemu.</span><span class="sxs-lookup"><span data-stu-id="cd900-112">In general, the profiler must cope with unexpected shutdowns.</span></span> <span data-ttu-id="cd900-113">Na przykład proces może zostać wstrzymane przez firmy Win32 `TerminateProcess` — metoda (deklaracja w Winbase.h).</span><span class="sxs-lookup"><span data-stu-id="cd900-113">For example, a process might be halted by Win32's `TerminateProcess` method (declared in Winbase.h).</span></span> <span data-ttu-id="cd900-114">W innych przypadkach CLR zostanie zatrzymany niektórych zarządzanych wątków (tła) bez dostarczanie wiadomości uporządkowany zniszczenie ich.</span><span class="sxs-lookup"><span data-stu-id="cd900-114">In other cases, the CLR will halt certain managed threads (background threads) without delivering orderly destruction messages for them.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd900-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cd900-115">Requirements</span></span>  
 <span data-ttu-id="cd900-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd900-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd900-117">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="cd900-117">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="cd900-118">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cd900-118">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cd900-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd900-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd900-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cd900-120">See also</span></span>

- [<span data-ttu-id="cd900-121">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="cd900-121">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="cd900-122">Initialize, metoda</span><span class="sxs-lookup"><span data-stu-id="cd900-122">Initialize Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-initialize-method.md)

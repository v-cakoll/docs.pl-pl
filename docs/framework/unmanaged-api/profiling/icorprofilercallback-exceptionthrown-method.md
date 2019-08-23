---
title: ICorProfilerCallback::ExceptionThrown — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ExceptionThrown
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ExceptionThrown
helpviewer_keywords:
- ExceptionThrown method [.NET Framework profiling]
- ICorProfilerCallback::ExceptionThrown method [.NET Framework profiling]
ms.assetid: f1a23f3b-ac21-4905-8abf-8ea59f15af53
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 01e407b726ce4426f3b58bc29854b30bd6add257
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69953879"
---
# <a name="icorprofilercallbackexceptionthrown-method"></a><span data-ttu-id="76f6a-102">ICorProfilerCallback::ExceptionThrown — Metoda</span><span class="sxs-lookup"><span data-stu-id="76f6a-102">ICorProfilerCallback::ExceptionThrown Method</span></span>
<span data-ttu-id="76f6a-103">Powiadamia profiler o zgłoszonym wyjątku.</span><span class="sxs-lookup"><span data-stu-id="76f6a-103">Notifies the profiler that an exception has been thrown.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="76f6a-104">Ta funkcja jest wywoływana tylko wtedy, gdy wyjątek osiągnie kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="76f6a-104">This function is called only if the exception reaches managed code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="76f6a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="76f6a-105">Syntax</span></span>  
  
```cpp  
HRESULT ExceptionThrown(  
    [in] ObjectID thrownObjectId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="76f6a-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="76f6a-106">Parameters</span></span>  
 `thrownObjectId`  
 <span data-ttu-id="76f6a-107">podczas Identyfikator obiektu, który spowodował wyjątek.</span><span class="sxs-lookup"><span data-stu-id="76f6a-107">[in] The ID of the object that caused the exception to be thrown.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="76f6a-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="76f6a-108">Remarks</span></span>  
 <span data-ttu-id="76f6a-109">Profiler nie powinien blokować swojej implementacji tej metody, ponieważ stos może nie znajdować się w stanie, który zezwala na wyrzucanie elementów bezużytecznych i dlatego nie można włączyć zastępujący elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="76f6a-109">The profiler should not block in its implementation of this method because the stack may not be in a state that allows garbage collection, and therefore preemptive garbage collection cannot be enabled.</span></span> <span data-ttu-id="76f6a-110">Jeśli profiler blokuje tutaj i zostanie podjęta próba wyrzucania elementów bezużytecznych, środowisko uruchomieniowe zostanie zablokowane do momentu wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="76f6a-110">If the profiler blocks here and garbage collection is attempted, the runtime will block until this callback returns.</span></span>  
  
 <span data-ttu-id="76f6a-111">Implementacja profilera nie powinna być wywoływana w kodzie zarządzanym lub w jakikolwiek sposób spowodować alokację pamięci zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="76f6a-111">The profiler's implementation of this method should not call into managed code or in any way cause a managed-memory allocation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="76f6a-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="76f6a-112">Requirements</span></span>  
 <span data-ttu-id="76f6a-113">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="76f6a-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="76f6a-114">**Nagłówki** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="76f6a-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="76f6a-115">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="76f6a-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="76f6a-116">**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="76f6a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="76f6a-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="76f6a-117">See also</span></span>

- [<span data-ttu-id="76f6a-118">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="76f6a-118">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)

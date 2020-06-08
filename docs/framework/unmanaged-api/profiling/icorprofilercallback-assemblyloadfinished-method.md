---
title: ICorProfilerCallback::AssemblyLoadFinished — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyLoadFinished
helpviewer_keywords:
- ICorProfilerCallback::AssemblyLoadFinished method [.NET Framework profiling]
- AssemblyLoadFinished method [.NET Framework profiling]
ms.assetid: 86d98f39-52e6-4c61-a625-9760f695ff12
topic_type:
- apiref
ms.openlocfilehash: ce4a842bc71ff144e46efb0d6f7068dfca9d207d
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84500445"
---
# <a name="icorprofilercallbackassemblyloadfinished-method"></a><span data-ttu-id="92d06-102">ICorProfilerCallback::AssemblyLoadFinished — Metoda</span><span class="sxs-lookup"><span data-stu-id="92d06-102">ICorProfilerCallback::AssemblyLoadFinished Method</span></span>
<span data-ttu-id="92d06-103">Powiadamia profiler o zakończeniu ładowania zestawu.</span><span class="sxs-lookup"><span data-stu-id="92d06-103">Notifies the profiler that an assembly has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92d06-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="92d06-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyLoadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="92d06-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="92d06-105">Parameters</span></span>

- `assemblyId`

  <span data-ttu-id="92d06-106">\[w] identyfikuje zestaw, który został załadowany.</span><span class="sxs-lookup"><span data-stu-id="92d06-106">\[in] Identifies the assembly that was loaded.</span></span>

- `hrStatus`

  <span data-ttu-id="92d06-107">\[w] wynik HRESULT wskazujący, czy zestaw zakończył pomyślne ładowanie.</span><span class="sxs-lookup"><span data-stu-id="92d06-107">\[in] An HRESULT that indicates whether the assembly finished loading successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="92d06-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="92d06-108">Remarks</span></span>  
 <span data-ttu-id="92d06-109">Wartość `assemblyId` nie jest prawidłowa dla żądania informacji, dopóki `AssemblyLoadFinished` Metoda nie zostanie wywołana.</span><span class="sxs-lookup"><span data-stu-id="92d06-109">The value of `assemblyId` is not valid for an information request until the `AssemblyLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="92d06-110">Niektóre części ładowania zestawu mogą być kontynuowane po `AssemblyLoadFinished` wywołaniu wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="92d06-110">Some parts of loading the assembly might continue after the `AssemblyLoadFinished` callback.</span></span> <span data-ttu-id="92d06-111">Błąd HRESULT w elemencie `hrStatus` wskazuje na błąd.</span><span class="sxs-lookup"><span data-stu-id="92d06-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="92d06-112">Jednak powodzenie HRESULT w programie `hrStatus` wskazuje tylko, że pierwsza część ładowania zestawu zakończyła się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="92d06-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92d06-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="92d06-113">Requirements</span></span>  
 <span data-ttu-id="92d06-114">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92d06-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92d06-115">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="92d06-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="92d06-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="92d06-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92d06-117">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92d06-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92d06-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="92d06-118">See also</span></span>

- [<span data-ttu-id="92d06-119">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="92d06-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)

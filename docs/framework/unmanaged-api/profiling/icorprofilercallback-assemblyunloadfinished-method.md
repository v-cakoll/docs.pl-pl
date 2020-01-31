---
title: ICorProfilerCallback::AssemblyUnloadFinished — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.AssemblyUnloadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::AssemblyUnloadFinished
helpviewer_keywords:
- AssemblyUnloadFinished method [.NET Framework profiling]
- ICorProfilerCallback::AssemblyUnloadFinished method [.NET Framework profiling]
ms.assetid: 53fca564-84b1-44d4-9e21-17a492d2aae7
topic_type:
- apiref
ms.openlocfilehash: 734ae1d14d02d47c7d3126f1b4cf55dcb4ad151b
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866627"
---
# <a name="icorprofilercallbackassemblyunloadfinished-method"></a><span data-ttu-id="98e27-102">ICorProfilerCallback::AssemblyUnloadFinished — Metoda</span><span class="sxs-lookup"><span data-stu-id="98e27-102">ICorProfilerCallback::AssemblyUnloadFinished Method</span></span>
<span data-ttu-id="98e27-103">Powiadamia program profilujący, że zestaw został zwolniony.</span><span class="sxs-lookup"><span data-stu-id="98e27-103">Notifies the profiler that an assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="98e27-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="98e27-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyUnloadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="98e27-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="98e27-105">Parameters</span></span>

- `assemblyId`

  <span data-ttu-id="98e27-106">\[in] określa zestaw, który jest zwalniany.</span><span class="sxs-lookup"><span data-stu-id="98e27-106">\[in] Identifies the assembly that is being unloaded.</span></span>

- `hrStatus`

  <span data-ttu-id="98e27-107">\[in] wynik HRESULT wskazujący, czy zestaw został zwolniony pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="98e27-107">\[in] An HRESULT that indicates whether the assembly was unloaded successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="98e27-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="98e27-108">Remarks</span></span>  
 <span data-ttu-id="98e27-109">Wartość `assemblyId` nie jest prawidłowa dla żądania informacji po powrocie metody [ICorProfilerCallback:: AssemblyUnloadStarted —](icorprofilercallback-assemblyunloadstarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="98e27-109">The value of `assemblyId` is not valid for an information request after the [ICorProfilerCallback::AssemblyUnloadStarted](icorprofilercallback-assemblyunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="98e27-110">Niektóre części zwalniania zestawu mogą być kontynuowane po wywołaniu wywołania zwrotnego `AssemblyUnloadFinished`.</span><span class="sxs-lookup"><span data-stu-id="98e27-110">Some parts of unloading the assembly might continue after the `AssemblyUnloadFinished` callback.</span></span> <span data-ttu-id="98e27-111">Błąd HRESULT w `hrStatus` wskazuje na błąd.</span><span class="sxs-lookup"><span data-stu-id="98e27-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="98e27-112">Jednak wynik HRESULT w `hrStatus` wskazuje tylko, że pierwsza część zwalniania zestawu zakończyła się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="98e27-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="98e27-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="98e27-113">Requirements</span></span>  
 <span data-ttu-id="98e27-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="98e27-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="98e27-115">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="98e27-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="98e27-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="98e27-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="98e27-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="98e27-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98e27-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="98e27-118">See also</span></span>

- [<span data-ttu-id="98e27-119">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="98e27-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)

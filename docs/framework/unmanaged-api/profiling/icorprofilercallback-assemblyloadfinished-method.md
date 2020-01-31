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
ms.openlocfilehash: 15ce195af0c0e8f8777f6e5d02043e17e32308da
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76866653"
---
# <a name="icorprofilercallbackassemblyloadfinished-method"></a><span data-ttu-id="44c54-102">ICorProfilerCallback::AssemblyLoadFinished — Metoda</span><span class="sxs-lookup"><span data-stu-id="44c54-102">ICorProfilerCallback::AssemblyLoadFinished Method</span></span>
<span data-ttu-id="44c54-103">Powiadamia profiler o zakończeniu ładowania zestawu.</span><span class="sxs-lookup"><span data-stu-id="44c54-103">Notifies the profiler that an assembly has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44c54-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="44c54-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyLoadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="44c54-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="44c54-105">Parameters</span></span>

- `assemblyId`

  <span data-ttu-id="44c54-106">\[in] określa zestaw, który został załadowany.</span><span class="sxs-lookup"><span data-stu-id="44c54-106">\[in] Identifies the assembly that was loaded.</span></span>

- `hrStatus`

  <span data-ttu-id="44c54-107">\[in] wynik HRESULT wskazujący, czy zestaw zakończył pomyślne ładowanie.</span><span class="sxs-lookup"><span data-stu-id="44c54-107">\[in] An HRESULT that indicates whether the assembly finished loading successfully.</span></span>

## <a name="remarks"></a><span data-ttu-id="44c54-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="44c54-108">Remarks</span></span>  
 <span data-ttu-id="44c54-109">Wartość `assemblyId` nie jest prawidłowa dla żądania informacji, dopóki nie zostanie wywołana metoda `AssemblyLoadFinished`.</span><span class="sxs-lookup"><span data-stu-id="44c54-109">The value of `assemblyId` is not valid for an information request until the `AssemblyLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="44c54-110">Niektóre części ładowania zestawu mogą być kontynuowane po wywołaniu wywołania zwrotnego `AssemblyLoadFinished`.</span><span class="sxs-lookup"><span data-stu-id="44c54-110">Some parts of loading the assembly might continue after the `AssemblyLoadFinished` callback.</span></span> <span data-ttu-id="44c54-111">Błąd HRESULT w `hrStatus` wskazuje na błąd.</span><span class="sxs-lookup"><span data-stu-id="44c54-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="44c54-112">Jednak wynik HRESULT w `hrStatus` wskazuje tylko, że pierwsza część ładowania zestawu zakończyła się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="44c54-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44c54-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="44c54-113">Requirements</span></span>  
 <span data-ttu-id="44c54-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="44c54-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="44c54-115">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="44c54-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="44c54-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="44c54-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="44c54-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="44c54-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44c54-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="44c54-118">See also</span></span>

- [<span data-ttu-id="44c54-119">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="44c54-119">ICorProfilerCallback Interface</span></span>](icorprofilercallback-interface.md)

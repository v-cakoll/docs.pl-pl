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
ms.openlocfilehash: 01404d23707be90b6b15cf741632400d49f164de
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445149"
---
# <a name="icorprofilercallbackassemblyunloadfinished-method"></a><span data-ttu-id="24c19-102">ICorProfilerCallback::AssemblyUnloadFinished — Metoda</span><span class="sxs-lookup"><span data-stu-id="24c19-102">ICorProfilerCallback::AssemblyUnloadFinished Method</span></span>
<span data-ttu-id="24c19-103">Powiadamia program profilujący, że zestaw został zwolniony.</span><span class="sxs-lookup"><span data-stu-id="24c19-103">Notifies the profiler that an assembly has been unloaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="24c19-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="24c19-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyUnloadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="24c19-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="24c19-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="24c19-106">podczas Identyfikuje zestaw, który jest zwalniany.</span><span class="sxs-lookup"><span data-stu-id="24c19-106">[in] Identifies the assembly that is being unloaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="24c19-107">podczas WYNIK HRESULT wskazujący, czy zestaw został zwolniony pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="24c19-107">[in] An HRESULT that indicates whether the assembly was unloaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="24c19-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="24c19-108">Remarks</span></span>  
 <span data-ttu-id="24c19-109">Wartość `assemblyId` nie jest prawidłowa dla żądania informacji po powrocie metody [ICorProfilerCallback:: AssemblyUnloadStarted —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md) .</span><span class="sxs-lookup"><span data-stu-id="24c19-109">The value of `assemblyId` is not valid for an information request after the [ICorProfilerCallback::AssemblyUnloadStarted](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-assemblyunloadstarted-method.md) method returns.</span></span>  
  
 <span data-ttu-id="24c19-110">Niektóre części zwalniania zestawu mogą być kontynuowane po wywołaniu wywołania zwrotnego `AssemblyUnloadFinished`.</span><span class="sxs-lookup"><span data-stu-id="24c19-110">Some parts of unloading the assembly might continue after the `AssemblyUnloadFinished` callback.</span></span> <span data-ttu-id="24c19-111">Błąd HRESULT w `hrStatus` wskazuje na błąd.</span><span class="sxs-lookup"><span data-stu-id="24c19-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="24c19-112">Jednak wynik HRESULT w `hrStatus` wskazuje tylko, że pierwsza część zwalniania zestawu zakończyła się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="24c19-112">However, a success HRESULT in `hrStatus` indicates only that the first part of unloading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="24c19-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="24c19-113">Requirements</span></span>  
 <span data-ttu-id="24c19-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="24c19-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="24c19-115">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="24c19-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="24c19-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="24c19-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="24c19-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="24c19-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24c19-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="24c19-118">See also</span></span>

- [<span data-ttu-id="24c19-119">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="24c19-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)

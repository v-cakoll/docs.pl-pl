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
ms.openlocfilehash: 33b72c8d089e5b335069fe465987086dfa1243bc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74445172"
---
# <a name="icorprofilercallbackassemblyloadfinished-method"></a><span data-ttu-id="c1ec2-102">ICorProfilerCallback::AssemblyLoadFinished — Metoda</span><span class="sxs-lookup"><span data-stu-id="c1ec2-102">ICorProfilerCallback::AssemblyLoadFinished Method</span></span>
<span data-ttu-id="c1ec2-103">Powiadamia profiler o zakończeniu ładowania zestawu.</span><span class="sxs-lookup"><span data-stu-id="c1ec2-103">Notifies the profiler that an assembly has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1ec2-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c1ec2-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyLoadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c1ec2-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c1ec2-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="c1ec2-106">podczas Identyfikuje zestaw, który został załadowany.</span><span class="sxs-lookup"><span data-stu-id="c1ec2-106">[in] Identifies the assembly that was loaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="c1ec2-107">podczas WYNIK HRESULT wskazujący, czy zestaw zakończył się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="c1ec2-107">[in] An HRESULT that indicates whether the assembly finished loading successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c1ec2-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c1ec2-108">Remarks</span></span>  
 <span data-ttu-id="c1ec2-109">Wartość `assemblyId` nie jest prawidłowa dla żądania informacji, dopóki nie zostanie wywołana metoda `AssemblyLoadFinished`.</span><span class="sxs-lookup"><span data-stu-id="c1ec2-109">The value of `assemblyId` is not valid for an information request until the `AssemblyLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="c1ec2-110">Niektóre części ładowania zestawu mogą być kontynuowane po wywołaniu wywołania zwrotnego `AssemblyLoadFinished`.</span><span class="sxs-lookup"><span data-stu-id="c1ec2-110">Some parts of loading the assembly might continue after the `AssemblyLoadFinished` callback.</span></span> <span data-ttu-id="c1ec2-111">Błąd HRESULT w `hrStatus` wskazuje na błąd.</span><span class="sxs-lookup"><span data-stu-id="c1ec2-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="c1ec2-112">Jednak wynik HRESULT w `hrStatus` wskazuje tylko, że pierwsza część ładowania zestawu zakończyła się powodzeniem.</span><span class="sxs-lookup"><span data-stu-id="c1ec2-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c1ec2-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c1ec2-113">Requirements</span></span>  
 <span data-ttu-id="c1ec2-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c1ec2-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c1ec2-115">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="c1ec2-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c1ec2-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="c1ec2-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c1ec2-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c1ec2-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1ec2-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c1ec2-118">See also</span></span>

- [<span data-ttu-id="c1ec2-119">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="c1ec2-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)

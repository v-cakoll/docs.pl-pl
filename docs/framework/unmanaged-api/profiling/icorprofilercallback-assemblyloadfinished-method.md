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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 174e71fca8c59dbd4842d0fc0b84bb9a3d7b10df
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67763047"
---
# <a name="icorprofilercallbackassemblyloadfinished-method"></a><span data-ttu-id="33457-102">ICorProfilerCallback::AssemblyLoadFinished — Metoda</span><span class="sxs-lookup"><span data-stu-id="33457-102">ICorProfilerCallback::AssemblyLoadFinished Method</span></span>
<span data-ttu-id="33457-103">Powiadamia program profilujący, że zespół zakończył ładowanie.</span><span class="sxs-lookup"><span data-stu-id="33457-103">Notifies the profiler that an assembly has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33457-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="33457-104">Syntax</span></span>  
  
```cpp  
HRESULT AssemblyLoadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="33457-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="33457-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="33457-106">[in] Określa zestaw, który został załadowany.</span><span class="sxs-lookup"><span data-stu-id="33457-106">[in] Identifies the assembly that was loaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="33457-107">[in] Wartość HRESULT, która wskazuje, czy zestaw zakończone pomyślnie ładowania.</span><span class="sxs-lookup"><span data-stu-id="33457-107">[in] An HRESULT that indicates whether the assembly finished loading successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="33457-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="33457-108">Remarks</span></span>  
 <span data-ttu-id="33457-109">Wartość `assemblyId` jest nieprawidłowa dla żądania informacje do momentu `AssemblyLoadFinished` metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="33457-109">The value of `assemblyId` is not valid for an information request until the `AssemblyLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="33457-110">Niektóre części ładowania zestawu może kontynuować po `AssemblyLoadFinished` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="33457-110">Some parts of loading the assembly might continue after the `AssemblyLoadFinished` callback.</span></span> <span data-ttu-id="33457-111">Błąd HRESULT w `hrStatus` wskazuje błąd.</span><span class="sxs-lookup"><span data-stu-id="33457-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="33457-112">Jednak sukcesów wartość HRESULT w `hrStatus` tylko wskazuje, czy zakończyła się pomyślnie w pierwszej części ładowania zestawu.</span><span class="sxs-lookup"><span data-stu-id="33457-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33457-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="33457-113">Requirements</span></span>  
 <span data-ttu-id="33457-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33457-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33457-115">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="33457-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="33457-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="33457-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="33457-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33457-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33457-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="33457-118">See also</span></span>

- [<span data-ttu-id="33457-119">ICorProfilerCallback, interfejs</span><span class="sxs-lookup"><span data-stu-id="33457-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)

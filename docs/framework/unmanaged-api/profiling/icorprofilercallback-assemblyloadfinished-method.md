---
title: "ICorProfilerCallback::AssemblyLoadFinished — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorProfilerCallback.AssemblyLoadFinished
api_location: mscorwks.dll
api_type: COM
f1_keywords: ICorProfilerCallback::AssemblyLoadFinished
helpviewer_keywords:
- ICorProfilerCallback::AssemblyLoadFinished method [.NET Framework profiling]
- AssemblyLoadFinished method [.NET Framework profiling]
ms.assetid: 86d98f39-52e6-4c61-a625-9760f695ff12
topic_type: apiref
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: af5089603c2044b10061a32c5921b9eeadf86b36
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icorprofilercallbackassemblyloadfinished-method"></a><span data-ttu-id="b3a5b-102">ICorProfilerCallback::AssemblyLoadFinished — Metoda</span><span class="sxs-lookup"><span data-stu-id="b3a5b-102">ICorProfilerCallback::AssemblyLoadFinished Method</span></span>
<span data-ttu-id="b3a5b-103">Powiadamia profilera zakończenie zestawu ładowania.</span><span class="sxs-lookup"><span data-stu-id="b3a5b-103">Notifies the profiler that an assembly has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3a5b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b3a5b-104">Syntax</span></span>  
  
```  
HRESULT AssemblyLoadFinished(  
    [in] AssemblyID assemblyId,  
    [in] HRESULT    hrStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b3a5b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b3a5b-105">Parameters</span></span>  
 `assemblyId`  
 <span data-ttu-id="b3a5b-106">[in] Określa zestaw, który został załadowany.</span><span class="sxs-lookup"><span data-stu-id="b3a5b-106">[in] Identifies the assembly that was loaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="b3a5b-107">[in] HRESULT, która wskazuje, czy zestaw zakończone pomyślnie ładowania.</span><span class="sxs-lookup"><span data-stu-id="b3a5b-107">[in] An HRESULT that indicates whether the assembly finished loading successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b3a5b-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b3a5b-108">Remarks</span></span>  
 <span data-ttu-id="b3a5b-109">Wartość `assemblyId` jest nieprawidłowa dla żądania informacji do `AssemblyLoadFinished` metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="b3a5b-109">The value of `assemblyId` is not valid for an information request until the `AssemblyLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="b3a5b-110">Podczas ładowania zestawu niektóre elementy mogą nadal po `AssemblyLoadFinished` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="b3a5b-110">Some parts of loading the assembly might continue after the `AssemblyLoadFinished` callback.</span></span> <span data-ttu-id="b3a5b-111">Błąd HRESULT w `hrStatus` oznacza błąd.</span><span class="sxs-lookup"><span data-stu-id="b3a5b-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="b3a5b-112">Jednak Powodzenie HRESULT w `hrStatus` tylko wskazuje, że pierwsza część podczas ładowania zestawu zakończyła się pomyślnie.</span><span class="sxs-lookup"><span data-stu-id="b3a5b-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the assembly has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3a5b-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b3a5b-113">Requirements</span></span>  
 <span data-ttu-id="b3a5b-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b3a5b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b3a5b-115">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="b3a5b-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="b3a5b-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b3a5b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b3a5b-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b3a5b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3a5b-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b3a5b-118">See Also</span></span>  
 [<span data-ttu-id="b3a5b-119">ICorProfilerCallback — interfejs</span><span class="sxs-lookup"><span data-stu-id="b3a5b-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)

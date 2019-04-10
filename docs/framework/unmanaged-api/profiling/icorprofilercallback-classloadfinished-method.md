---
title: ICorProfilerCallback::ClassLoadFinished — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerCallback.ClassLoadFinished
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerCallback::ClassLoadFinished
helpviewer_keywords:
- ClassLoadFinished method [.NET Framework profiling]
- ICorProfilerCallback::ClassLoadFinished method [.NET Framework profiling]
ms.assetid: 3dd80fbe-d62d-4d4d-acf8-5b7d0efe607e
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cab4b039d225f4ee1b00add6ffec63fd35be8857
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59202810"
---
# <a name="icorprofilercallbackclassloadfinished-method"></a><span data-ttu-id="efbd6-102">ICorProfilerCallback::ClassLoadFinished — Metoda</span><span class="sxs-lookup"><span data-stu-id="efbd6-102">ICorProfilerCallback::ClassLoadFinished Method</span></span>
<span data-ttu-id="efbd6-103">Powiadamia program profilujący, że klasa została zakończona podczas ładowania.</span><span class="sxs-lookup"><span data-stu-id="efbd6-103">Notifies the profiler that a class has finished loading.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efbd6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="efbd6-104">Syntax</span></span>  
  
```  
HRESULT ClassLoadFinished(  
    [in] ClassID classId,  
    [in] HRESULT hrStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="efbd6-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="efbd6-105">Parameters</span></span>  
 `classId`  
 <span data-ttu-id="efbd6-106">[in] Określa klasę, która została załadowana.</span><span class="sxs-lookup"><span data-stu-id="efbd6-106">[in] Identifies the class that was loaded.</span></span>  
  
 `hrStatus`  
 <span data-ttu-id="efbd6-107">[in] Wartość HRESULT, która wskazuje, czy klasa został pomyślnie załadowany.</span><span class="sxs-lookup"><span data-stu-id="efbd6-107">[in] An HRESULT that indicates whether the class loaded successfully.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="efbd6-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="efbd6-108">Remarks</span></span>  
 <span data-ttu-id="efbd6-109">Wartość `classId` jest nieprawidłowa dla żądania informacje do momentu `ClassLoadFinished` metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="efbd6-109">The value of `classId` is not valid for an information request until the `ClassLoadFinished` method is called.</span></span>  
  
 <span data-ttu-id="efbd6-110">Niektóre części ładowania klasy może kontynuować po `ClassLoadFinished` wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="efbd6-110">Some parts of loading the class might continue after the `ClassLoadFinished` callback.</span></span> <span data-ttu-id="efbd6-111">Błąd HRESULT w `hrStatus` wskazuje błąd.</span><span class="sxs-lookup"><span data-stu-id="efbd6-111">A failure HRESULT in `hrStatus` indicates a failure.</span></span> <span data-ttu-id="efbd6-112">Jednak sukcesów wartość HRESULT w `hrStatus` wskazuje tylko, powiodło się w pierwszej części ładowania klasy.</span><span class="sxs-lookup"><span data-stu-id="efbd6-112">However, a success HRESULT in `hrStatus` indicates only that the first part of loading the class has succeeded.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="efbd6-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="efbd6-113">Requirements</span></span>  
 <span data-ttu-id="efbd6-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="efbd6-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="efbd6-115">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="efbd6-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="efbd6-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="efbd6-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="efbd6-117">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="efbd6-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="efbd6-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="efbd6-118">See also</span></span>

- [<span data-ttu-id="efbd6-119">ICorProfilerCallback — Interfejs</span><span class="sxs-lookup"><span data-stu-id="efbd6-119">ICorProfilerCallback Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)
- [<span data-ttu-id="efbd6-120">ClassLoadStarted, metoda</span><span class="sxs-lookup"><span data-stu-id="efbd6-120">ClassLoadStarted Method</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-classloadstarted-method.md)

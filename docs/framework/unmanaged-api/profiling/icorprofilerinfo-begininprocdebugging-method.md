---
title: ICorProfilerInfo::BeginInprocDebugging — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.BeginInprocDebugging
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::BeginInprocDebugging
helpviewer_keywords:
- BeginInprocDebugging method [.NET Framework profiling]
- ICorProfilerInfo::BeginInprocDebugging method [.NET Framework profiling]
ms.assetid: c5c82c69-99f8-4447-aee0-42cca0a5eb5c
topic_type:
- apiref
ms.openlocfilehash: c14979fa711145b9f1a134f90d7450b24e6d8a15
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864300"
---
# <a name="icorprofilerinfobegininprocdebugging-method"></a><span data-ttu-id="4f0a0-102">ICorProfilerInfo::BeginInprocDebugging — Metoda</span><span class="sxs-lookup"><span data-stu-id="4f0a0-102">ICorProfilerInfo::BeginInprocDebugging Method</span></span>
<span data-ttu-id="4f0a0-103">Inicjuje obsługę debugowania w procesie.</span><span class="sxs-lookup"><span data-stu-id="4f0a0-103">Initializes in-process debugging support.</span></span> <span data-ttu-id="4f0a0-104">Ta metoda jest przestarzała w .NET Framework w wersji 2,0.</span><span class="sxs-lookup"><span data-stu-id="4f0a0-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4f0a0-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="4f0a0-105">Syntax</span></span>  
  
```cpp  
HRESULT BeginInprocDebugging(  
    [in]  BOOL   fThisThreadOnly,  
    [out] DWORD *pdwProfilerContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4f0a0-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="4f0a0-106">Parameters</span></span>  
 `fThisThreadOnly`  
 <span data-ttu-id="4f0a0-107">podczas Ustaw tę wartość na `true`, aby zainicjować obsługę debugowania tylko dla bieżącego wątku; Ustaw ją na `false`, aby zainicjować obsługę debugowania dla wszystkich wątków.</span><span class="sxs-lookup"><span data-stu-id="4f0a0-107">[in] Set this value to `true` to initialize debugging support for only the current thread; set it to `false` to initialize debugging support for all threads.</span></span>  
  
 `pdwProfilerContext`  
 <span data-ttu-id="4f0a0-108">określoną Wskaźnik do zwracanej wartości, która identyfikuje sesję debugowania.</span><span class="sxs-lookup"><span data-stu-id="4f0a0-108">[out] The pointer to a returned value that identifies the debugging session.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4f0a0-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4f0a0-109">Remarks</span></span>  
 <span data-ttu-id="4f0a0-110">Usługi debugowania CLR obsługiwały ograniczone debugowanie w procesie w .NET Framework wersje 1,0 i 1,1.</span><span class="sxs-lookup"><span data-stu-id="4f0a0-110">The CLR debugging services supported limited in-process debugging in the .NET Framework versions 1.0 and 1.1.</span></span> <span data-ttu-id="4f0a0-111">Debugowanie w procesie umożliwia profilerowi użycie części inspekcji interfejsu API debugowania.</span><span class="sxs-lookup"><span data-stu-id="4f0a0-111">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="4f0a0-112">Jednak ze względu na Opinie klientów, debugowanie w procesie zostało usunięte z .NET Framework w wersji 2,0 i zastąpione zestawem funkcji, który jest bardziej aktualny z profilem API profilowania.</span><span class="sxs-lookup"><span data-stu-id="4f0a0-112">However, due to customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4f0a0-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4f0a0-113">Requirements</span></span>  
 <span data-ttu-id="4f0a0-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4f0a0-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4f0a0-115">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="4f0a0-115">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4f0a0-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4f0a0-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4f0a0-117">**Wersja .NET Framework:** 1,0</span><span class="sxs-lookup"><span data-stu-id="4f0a0-117">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f0a0-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4f0a0-118">See also</span></span>

- [<span data-ttu-id="4f0a0-119">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="4f0a0-119">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)

---
title: ICorProfilerInfo::GetInprocInspectionInterface — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetInprocInspectionInterface
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetInprocInspectionInterface
helpviewer_keywords:
- GetInprocInspectionInterface method [.NET Framework profiling]
- ICorProfilerInfo::GetInprocInspectionInterface method [.NET Framework profiling]
ms.assetid: 22a92d1d-8849-4af6-8304-ecc53dd1d289
topic_type:
- apiref
ms.openlocfilehash: 5c9258126c872bd501b4eebc4698b4dded402dfe
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863364"
---
# <a name="icorprofilerinfogetinprocinspectioninterface-method"></a><span data-ttu-id="69b5c-102">ICorProfilerInfo::GetInprocInspectionInterface — Metoda</span><span class="sxs-lookup"><span data-stu-id="69b5c-102">ICorProfilerInfo::GetInprocInspectionInterface Method</span></span>
<span data-ttu-id="69b5c-103">Pobiera obiekt, który może być badany dla interfejsu "ICorDebugProcess".</span><span class="sxs-lookup"><span data-stu-id="69b5c-103">Gets an object that can be queried for an "ICorDebugProcess" interface.</span></span> <span data-ttu-id="69b5c-104">Ta metoda jest przestarzała w .NET Framework w wersji 2,0.</span><span class="sxs-lookup"><span data-stu-id="69b5c-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69b5c-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="69b5c-105">Syntax</span></span>  
  
```cpp  
HRESULT GetInprocInspectionInterface(  
    [out] IUnknown **ppicd);  
```  
  
## <a name="parameters"></a><span data-ttu-id="69b5c-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="69b5c-106">Parameters</span></span>  
 `ppicd`  
 <span data-ttu-id="69b5c-107">Obiekt [out](/cpp/atl/iunknown) , który może być badany dla interfejsu `ICorDebugProcess`.</span><span class="sxs-lookup"><span data-stu-id="69b5c-107">[out](/cpp/atl/iunknown) object that can be queried for an `ICorDebugProcess` interface.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="69b5c-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="69b5c-108">Remarks</span></span>  
 <span data-ttu-id="69b5c-109">Interfejs API debugowania środowiska uruchomieniowego języka wspólnego (CLR) obsługuje ograniczone debugowanie w procesie w .NET Framework w wersji 1,0.</span><span class="sxs-lookup"><span data-stu-id="69b5c-109">The common language runtime (CLR) debugging API supported limited in-process debugging in the .NET Framework version 1.0.</span></span> <span data-ttu-id="69b5c-110">Debugowanie w procesie umożliwia profilerowi użycie części inspekcji interfejsu API debugowania.</span><span class="sxs-lookup"><span data-stu-id="69b5c-110">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="69b5c-111">W wyniku opinii klientów, debugowanie w procesie zostało usunięte z .NET Framework w wersji 2,0 i zastąpione zestawem funkcji, który jest bardziej aktualny z profilem API profilowania.</span><span class="sxs-lookup"><span data-stu-id="69b5c-111">As a result of customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="69b5c-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="69b5c-112">Requirements</span></span>  
 <span data-ttu-id="69b5c-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69b5c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69b5c-114">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="69b5c-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="69b5c-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="69b5c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="69b5c-116">**Wersja .NET Framework:** 1,0</span><span class="sxs-lookup"><span data-stu-id="69b5c-116">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69b5c-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="69b5c-117">See also</span></span>

- [<span data-ttu-id="69b5c-118">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="69b5c-118">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)

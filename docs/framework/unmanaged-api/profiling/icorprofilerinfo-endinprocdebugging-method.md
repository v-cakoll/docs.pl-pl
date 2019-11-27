---
title: ICorProfilerInfo::EndInprocDebugging — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.EndInprocDebugging
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::EndInprocDebugging
helpviewer_keywords:
- ICorProfilerInfo::EndInprocDebugging method [.NET Framework profiling]
- EndInprocDebugging method [.NET Framework profiling]
ms.assetid: 35bc1188-9767-4141-8038-60ea015b99ac
topic_type:
- apiref
ms.openlocfilehash: 09b1b81bde486db67acede99e0d67ff85cb01bae
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74447754"
---
# <a name="icorprofilerinfoendinprocdebugging-method"></a><span data-ttu-id="1099e-102">ICorProfilerInfo::EndInprocDebugging — Metoda</span><span class="sxs-lookup"><span data-stu-id="1099e-102">ICorProfilerInfo::EndInprocDebugging Method</span></span>
<span data-ttu-id="1099e-103">Zamyka sesję debugowania w procesie.</span><span class="sxs-lookup"><span data-stu-id="1099e-103">Shuts down an in-process debugging session.</span></span> <span data-ttu-id="1099e-104">Ta metoda jest przestarzała w .NET Framework w wersji 2,0.</span><span class="sxs-lookup"><span data-stu-id="1099e-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1099e-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="1099e-105">Syntax</span></span>  
  
```cpp  
HRESULT EndInprocDebugging(  
    [in]  DWORD dwProfilerContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1099e-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="1099e-106">Parameters</span></span>  
 `dwProfilerContext`  
 <span data-ttu-id="1099e-107">podczas Wartość, która identyfikuje sesję debugowania.</span><span class="sxs-lookup"><span data-stu-id="1099e-107">[in] A value that identifies the debugging session.</span></span> <span data-ttu-id="1099e-108">Ta wartość musi być taka sama jak odebrana w metodzie [ICorProfilerInfo:: BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) .</span><span class="sxs-lookup"><span data-stu-id="1099e-108">This value must be the same as that received in the [ICorProfilerInfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1099e-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1099e-109">Remarks</span></span>  
 <span data-ttu-id="1099e-110">Należy wywołać [ICorProfilerInfo:: BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) i `EndInprocDebugging` w ramach tej samej metody wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="1099e-110">You must call [ICorProfilerInfo::BeginInprocDebugging](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-begininprocdebugging-method.md) and `EndInprocDebugging` within the same callback method.</span></span>  
  
 <span data-ttu-id="1099e-111">Usługi debugowania CLR obsługiwały ograniczone debugowanie w procesie w .NET Framework wersje 1,0 i 1,1.</span><span class="sxs-lookup"><span data-stu-id="1099e-111">The CLR debugging services supported limited in-process debugging in the .NET Framework versions 1.0 and 1.1.</span></span> <span data-ttu-id="1099e-112">Debugowanie w procesie umożliwia profilerowi użycie części inspekcji interfejsu API debugowania.</span><span class="sxs-lookup"><span data-stu-id="1099e-112">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="1099e-113">Jednak ze względu na Opinie klientów, debugowanie w procesie zostało usunięte z .NET Framework w wersji 2,0 i zastąpione zestawem funkcji, który jest bardziej aktualny z profilem API profilowania.</span><span class="sxs-lookup"><span data-stu-id="1099e-113">However, due to customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1099e-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1099e-114">Requirements</span></span>  
 <span data-ttu-id="1099e-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1099e-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1099e-116">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="1099e-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1099e-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1099e-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1099e-118">**Wersja .NET Framework:** 1,0</span><span class="sxs-lookup"><span data-stu-id="1099e-118">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1099e-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1099e-119">See also</span></span>

- [<span data-ttu-id="1099e-120">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="1099e-120">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)

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
ms.openlocfilehash: 8a15843e9169442d89996375ee85f62b38f92e30
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864261"
---
# <a name="icorprofilerinfoendinprocdebugging-method"></a><span data-ttu-id="4d9cc-102">ICorProfilerInfo::EndInprocDebugging — Metoda</span><span class="sxs-lookup"><span data-stu-id="4d9cc-102">ICorProfilerInfo::EndInprocDebugging Method</span></span>
<span data-ttu-id="4d9cc-103">Zamyka sesję debugowania w procesie.</span><span class="sxs-lookup"><span data-stu-id="4d9cc-103">Shuts down an in-process debugging session.</span></span> <span data-ttu-id="4d9cc-104">Ta metoda jest przestarzała w .NET Framework w wersji 2,0.</span><span class="sxs-lookup"><span data-stu-id="4d9cc-104">This method is obsolete in the .NET Framework version 2.0.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d9cc-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="4d9cc-105">Syntax</span></span>  
  
```cpp  
HRESULT EndInprocDebugging(  
    [in]  DWORD dwProfilerContext);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4d9cc-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="4d9cc-106">Parameters</span></span>  
 `dwProfilerContext`  
 <span data-ttu-id="4d9cc-107">podczas Wartość, która identyfikuje sesję debugowania.</span><span class="sxs-lookup"><span data-stu-id="4d9cc-107">[in] A value that identifies the debugging session.</span></span> <span data-ttu-id="4d9cc-108">Ta wartość musi być taka sama jak odebrana w metodzie [ICorProfilerInfo:: BeginInprocDebugging](icorprofilerinfo-begininprocdebugging-method.md) .</span><span class="sxs-lookup"><span data-stu-id="4d9cc-108">This value must be the same as that received in the [ICorProfilerInfo::BeginInprocDebugging](icorprofilerinfo-begininprocdebugging-method.md) method.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4d9cc-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4d9cc-109">Remarks</span></span>  
 <span data-ttu-id="4d9cc-110">Należy wywołać [ICorProfilerInfo:: BeginInprocDebugging](icorprofilerinfo-begininprocdebugging-method.md) i `EndInprocDebugging` w ramach tej samej metody wywołania zwrotnego.</span><span class="sxs-lookup"><span data-stu-id="4d9cc-110">You must call [ICorProfilerInfo::BeginInprocDebugging](icorprofilerinfo-begininprocdebugging-method.md) and `EndInprocDebugging` within the same callback method.</span></span>  
  
 <span data-ttu-id="4d9cc-111">Usługi debugowania CLR obsługiwały ograniczone debugowanie w procesie w .NET Framework wersje 1,0 i 1,1.</span><span class="sxs-lookup"><span data-stu-id="4d9cc-111">The CLR debugging services supported limited in-process debugging in the .NET Framework versions 1.0 and 1.1.</span></span> <span data-ttu-id="4d9cc-112">Debugowanie w procesie umożliwia profilerowi użycie części inspekcji interfejsu API debugowania.</span><span class="sxs-lookup"><span data-stu-id="4d9cc-112">In-process debugging enabled a profiler to use the inspection portions of the debugging API.</span></span> <span data-ttu-id="4d9cc-113">Jednak ze względu na Opinie klientów, debugowanie w procesie zostało usunięte z .NET Framework w wersji 2,0 i zastąpione zestawem funkcji, który jest bardziej aktualny z profilem API profilowania.</span><span class="sxs-lookup"><span data-stu-id="4d9cc-113">However, due to customer feedback, in-process debugging has been removed from the .NET Framework in version 2.0, and replaced with a set of functionality that is more in line with the profiling API.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4d9cc-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4d9cc-114">Requirements</span></span>  
 <span data-ttu-id="4d9cc-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4d9cc-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4d9cc-116">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="4d9cc-116">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4d9cc-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4d9cc-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4d9cc-118">**Wersja .NET Framework:** 1,0</span><span class="sxs-lookup"><span data-stu-id="4d9cc-118">**.NET Framework Version:** 1.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4d9cc-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4d9cc-119">See also</span></span>

- [<span data-ttu-id="4d9cc-120">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="4d9cc-120">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)

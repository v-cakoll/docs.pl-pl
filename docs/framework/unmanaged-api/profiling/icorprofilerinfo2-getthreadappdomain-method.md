---
title: ICorProfilerInfo2::GetThreadAppDomain — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetThreadAppDomain
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetThreadAppDomain
helpviewer_keywords:
- ICorProfilerInfo2::GetThreadAppDomain method [.NET Framework profiling]
- GetThreadAppDomain method [.NET Framework profiling]
ms.assetid: 4a11b264-8540-4732-aa35-bc2d95b95b8e
topic_type:
- apiref
ms.openlocfilehash: 70535f8bcee95c2596c43617eb5893e2d92a355b
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84496784"
---
# <a name="icorprofilerinfo2getthreadappdomain-method"></a><span data-ttu-id="8a8cb-102">ICorProfilerInfo2::GetThreadAppDomain — Metoda</span><span class="sxs-lookup"><span data-stu-id="8a8cb-102">ICorProfilerInfo2::GetThreadAppDomain Method</span></span>
<span data-ttu-id="8a8cb-103">Pobiera identyfikator domeny aplikacji, w której określony wątek aktualnie wykonuje kod.</span><span class="sxs-lookup"><span data-stu-id="8a8cb-103">Gets the ID of the application domain in which the specified thread is currently executing code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a8cb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8a8cb-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadAppDomain(  
    [in]  ThreadID threadId,  
    [out] AppDomainID *pAppDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a8cb-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8a8cb-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="8a8cb-106">podczas Identyfikator określający wątek.</span><span class="sxs-lookup"><span data-stu-id="8a8cb-106">[in] The ID specifying the thread.</span></span>  
  
 `pAppDomainId`  
 <span data-ttu-id="8a8cb-107">określoną Wskaźnik do identyfikatora domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="8a8cb-107">[out] A pointer to the ID of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a8cb-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8a8cb-108">Requirements</span></span>  
 <span data-ttu-id="8a8cb-109">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a8cb-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a8cb-110">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="8a8cb-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="8a8cb-111">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8a8cb-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a8cb-112">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a8cb-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a8cb-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8a8cb-113">See also</span></span>

- [<span data-ttu-id="8a8cb-114">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="8a8cb-114">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
- [<span data-ttu-id="8a8cb-115">ICorProfilerInfo2, interfejs</span><span class="sxs-lookup"><span data-stu-id="8a8cb-115">ICorProfilerInfo2 Interface</span></span>](icorprofilerinfo2-interface.md)

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
ms.openlocfilehash: 8637be3c0a59676dc52aea985d7418bfd8f247bc
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74443103"
---
# <a name="icorprofilerinfo2getthreadappdomain-method"></a><span data-ttu-id="0c0ce-102">ICorProfilerInfo2::GetThreadAppDomain — Metoda</span><span class="sxs-lookup"><span data-stu-id="0c0ce-102">ICorProfilerInfo2::GetThreadAppDomain Method</span></span>
<span data-ttu-id="0c0ce-103">Pobiera identyfikator domeny aplikacji, w której określony wątek aktualnie wykonuje kod.</span><span class="sxs-lookup"><span data-stu-id="0c0ce-103">Gets the ID of the application domain in which the specified thread is currently executing code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c0ce-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0c0ce-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadAppDomain(  
    [in]  ThreadID threadId,  
    [out] AppDomainID *pAppDomainId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c0ce-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0c0ce-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="0c0ce-106">podczas Identyfikator określający wątek.</span><span class="sxs-lookup"><span data-stu-id="0c0ce-106">[in] The ID specifying the thread.</span></span>  
  
 `pAppDomainId`  
 <span data-ttu-id="0c0ce-107">określoną Wskaźnik do identyfikatora domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0c0ce-107">[out] A pointer to the ID of the application domain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c0ce-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0c0ce-108">Requirements</span></span>  
 <span data-ttu-id="0c0ce-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c0ce-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c0ce-110">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="0c0ce-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0c0ce-111">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0c0ce-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0c0ce-112">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c0ce-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c0ce-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0c0ce-113">See also</span></span>

- [<span data-ttu-id="0c0ce-114">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="0c0ce-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="0c0ce-115">ICorProfilerInfo2, interfejs</span><span class="sxs-lookup"><span data-stu-id="0c0ce-115">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)

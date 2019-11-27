---
title: ICorProfilerInfo::ForceGC — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.ForceGC
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::ForceGC
helpviewer_keywords:
- ICorProfilerInfo::ForceGC method [.NET Framework profiling]
- ForceGC method [.NET Framework profiling]
ms.assetid: 0da1ef80-d242-4636-87d0-43e0470b342a
topic_type:
- apiref
ms.openlocfilehash: 9f97da4e68d4b76178198e91c3fb8f08b56dda7b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448189"
---
# <a name="icorprofilerinfoforcegc-method"></a><span data-ttu-id="fef7e-102">ICorProfilerInfo::ForceGC — Metoda</span><span class="sxs-lookup"><span data-stu-id="fef7e-102">ICorProfilerInfo::ForceGC Method</span></span>
<span data-ttu-id="fef7e-103">Wymusza wyrzucanie elementów bezużytecznych w środowisku uruchomieniowym języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="fef7e-103">Forces garbage collection to occur within the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fef7e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fef7e-104">Syntax</span></span>  
  
```cpp  
HRESULT ForceGC();  
```  
  
## <a name="remarks"></a><span data-ttu-id="fef7e-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fef7e-105">Remarks</span></span>  
 <span data-ttu-id="fef7e-106">Metoda `ForceGC` musi być wywoływana tylko z wątku, w którym nigdy nie uruchomiono kodu zarządzanego i nie ma żadnych wywołań zwrotnych profilera na stosie.</span><span class="sxs-lookup"><span data-stu-id="fef7e-106">The `ForceGC` method must be called only from a thread that has never run managed code and does not have any profiler callbacks on its stack.</span></span> <span data-ttu-id="fef7e-107">Najbardziej wygodna implementacja polega na utworzeniu oddzielnego wątku w profilerze, który wywołuje `ForceGC` po zasygnalizowaniu.</span><span class="sxs-lookup"><span data-stu-id="fef7e-107">The most convenient implementation is to create a separate thread within the profiler that calls `ForceGC` when signaled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fef7e-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fef7e-108">Requirements</span></span>  
 <span data-ttu-id="fef7e-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fef7e-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fef7e-110">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="fef7e-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="fef7e-111">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="fef7e-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fef7e-112">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fef7e-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fef7e-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fef7e-113">See also</span></span>

- [<span data-ttu-id="fef7e-114">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="fef7e-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)

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
ms.openlocfilehash: e1fe38419cda328c919f0840d51cf6336919aa60
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76864222"
---
# <a name="icorprofilerinfoforcegc-method"></a><span data-ttu-id="87f03-102">ICorProfilerInfo::ForceGC — Metoda</span><span class="sxs-lookup"><span data-stu-id="87f03-102">ICorProfilerInfo::ForceGC Method</span></span>
<span data-ttu-id="87f03-103">Wymusza wyrzucanie elementów bezużytecznych w środowisku uruchomieniowym języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="87f03-103">Forces garbage collection to occur within the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="87f03-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="87f03-104">Syntax</span></span>  
  
```cpp  
HRESULT ForceGC();  
```  
  
## <a name="remarks"></a><span data-ttu-id="87f03-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="87f03-105">Remarks</span></span>  
 <span data-ttu-id="87f03-106">Metoda `ForceGC` musi być wywoływana tylko z wątku, w którym nigdy nie uruchomiono kodu zarządzanego i nie ma żadnych wywołań zwrotnych profilera na stosie.</span><span class="sxs-lookup"><span data-stu-id="87f03-106">The `ForceGC` method must be called only from a thread that has never run managed code and does not have any profiler callbacks on its stack.</span></span> <span data-ttu-id="87f03-107">Najbardziej wygodna implementacja polega na utworzeniu oddzielnego wątku w profilerze, który wywołuje `ForceGC` po zasygnalizowaniu.</span><span class="sxs-lookup"><span data-stu-id="87f03-107">The most convenient implementation is to create a separate thread within the profiler that calls `ForceGC` when signaled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="87f03-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="87f03-108">Requirements</span></span>  
 <span data-ttu-id="87f03-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="87f03-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="87f03-110">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="87f03-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="87f03-111">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="87f03-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="87f03-112">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="87f03-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="87f03-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="87f03-113">See also</span></span>

- [<span data-ttu-id="87f03-114">ICorProfilerInfo, interfejs</span><span class="sxs-lookup"><span data-stu-id="87f03-114">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)

---
title: ICorProfilerObjectEnum::GetCount — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerObjectEnum.GetCount
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum::GetCount
helpviewer_keywords:
- ICorProfilerObjectEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerObjectEnum interface [.NET Framework profiling]
ms.assetid: 166b0761-ed80-4ccd-9973-dc20e61bf8fa
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a5f23950eea94cde0655d364ad0c6701e04a7c1b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerobjectenumgetcount-method"></a><span data-ttu-id="c8145-102">ICorProfilerObjectEnum::GetCount — Metoda</span><span class="sxs-lookup"><span data-stu-id="c8145-102">ICorProfilerObjectEnum::GetCount Method</span></span>
<span data-ttu-id="c8145-103">Pobiera całkowitą liczbę obiektów zablokowane w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="c8145-103">Gets the total number of frozen objects in the collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8145-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c8145-104">Syntax</span></span>  
  
```  
HRESULT GetCount (  
    [out] ULONG   *pcelt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c8145-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c8145-105">Parameters</span></span>  
 `pcelt`  
 <span data-ttu-id="c8145-106">[out] Wskaźnik do liczby obiektów zablokowane w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="c8145-106">[out] A pointer to the number of frozen objects in the collection.</span></span>  
  
 <span data-ttu-id="c8145-107">Ta metoda zawsze zwraca zero w programie .NET Framework w wersji 3.5 z dodatkiem Service Pack 1 (SP1) lub nowszy.</span><span class="sxs-lookup"><span data-stu-id="c8145-107">This method will always return zero in the .NET Framework version 3.5 Service Pack 1 (SP1) and later versions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c8145-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c8145-108">Requirements</span></span>  
 <span data-ttu-id="c8145-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c8145-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c8145-110">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="c8145-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="c8145-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c8145-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c8145-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c8145-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c8145-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c8145-113">See Also</span></span>  
 [<span data-ttu-id="c8145-114">ICorProfilerObjectEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="c8145-114">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)

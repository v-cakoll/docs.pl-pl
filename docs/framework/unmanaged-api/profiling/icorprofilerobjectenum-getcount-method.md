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
ms.openlocfilehash: 077e6d729eb98ddad25cd0c0cccf6d4641e2602c
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428256"
---
# <a name="icorprofilerobjectenumgetcount-method"></a><span data-ttu-id="7f5ba-102">ICorProfilerObjectEnum::GetCount — Metoda</span><span class="sxs-lookup"><span data-stu-id="7f5ba-102">ICorProfilerObjectEnum::GetCount Method</span></span>
<span data-ttu-id="7f5ba-103">Pobiera łączną liczbę zablokowanych obiektów w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="7f5ba-103">Gets the total number of frozen objects in the collection.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f5ba-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7f5ba-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount (  
    [out] ULONG   *pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7f5ba-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7f5ba-105">Parameters</span></span>  
 `pcelt`  
 <span data-ttu-id="7f5ba-106">określoną Wskaźnik do liczby zamrożonych obiektów w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="7f5ba-106">[out] A pointer to the number of frozen objects in the collection.</span></span>  
  
 <span data-ttu-id="7f5ba-107">Ta metoda zawsze zwróci zero w .NET Framework wersji 3,5 Service Pack 1 (SP1) i nowszych wersjach.</span><span class="sxs-lookup"><span data-stu-id="7f5ba-107">This method will always return zero in the .NET Framework version 3.5 Service Pack 1 (SP1) and later versions.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7f5ba-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7f5ba-108">Requirements</span></span>  
 <span data-ttu-id="7f5ba-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f5ba-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f5ba-110">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="7f5ba-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7f5ba-111">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7f5ba-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7f5ba-112">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f5ba-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f5ba-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7f5ba-113">See also</span></span>

- [<span data-ttu-id="7f5ba-114">ICorProfilerObjectEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="7f5ba-114">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)

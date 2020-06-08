---
title: ICorProfilerThreadEnum::GetCount — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.GetCount
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::GetCount
helpviewer_keywords:
- ICorProfilerThreadEnum::GetCount method [.NET Framework profiling]
- GetCount method, ICorProfilerThreadEnum interface [.NET Framework profiling]
ms.assetid: d6dbdc4a-6115-455d-a3f3-704a81d3646b
topic_type:
- apiref
ms.openlocfilehash: 4bc2ea083d5278afc9278d388f57b048f7682ca6
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84494400"
---
# <a name="icorprofilerthreadenumgetcount-method"></a><span data-ttu-id="e3c0f-102">ICorProfilerThreadEnum::GetCount — Metoda</span><span class="sxs-lookup"><span data-stu-id="e3c0f-102">ICorProfilerThreadEnum::GetCount Method</span></span>
<span data-ttu-id="e3c0f-103">Pobiera liczbę wątków, które są używane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="e3c0f-103">Gets the number of threads that are used by the application.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e3c0f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e3c0f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCount (    [out] ULONG * pcelt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="e3c0f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="e3c0f-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="e3c0f-106">określoną Liczba wątków używanych przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="e3c0f-106">[out] The number of threads used by the application.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e3c0f-107">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e3c0f-107">Requirements</span></span>  
 <span data-ttu-id="e3c0f-108">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e3c0f-108">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e3c0f-109">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="e3c0f-109">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="e3c0f-110">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="e3c0f-110">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e3c0f-111">**.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e3c0f-111">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3c0f-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e3c0f-112">See also</span></span>

- [<span data-ttu-id="e3c0f-113">ICorProfilerThreadEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="e3c0f-113">ICorProfilerThreadEnum Interface</span></span>](icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="e3c0f-114">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="e3c0f-114">Profiling Interfaces</span></span>](profiling-interfaces.md)

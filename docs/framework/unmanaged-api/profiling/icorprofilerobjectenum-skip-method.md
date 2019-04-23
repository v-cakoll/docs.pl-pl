---
title: ICorProfilerObjectEnum::Skip — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerObjectEnum.Skip
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerObjectEnum::Skip
helpviewer_keywords:
- ICorProfilerObjectEnum::Skip method [.NET Framework profiling]
- Skip method, ICorProfilerObjectEnum interface [.NET Framework profiling]
ms.assetid: f8e498f8-f93a-4b82-bd22-55bdbf5e8d45
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2bcc837fede7e7db59bdf88a0b5434a7c1924335
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59210948"
---
# <a name="icorprofilerobjectenumskip-method"></a><span data-ttu-id="4a05c-102">ICorProfilerObjectEnum::Skip — Metoda</span><span class="sxs-lookup"><span data-stu-id="4a05c-102">ICorProfilerObjectEnum::Skip Method</span></span>
<span data-ttu-id="4a05c-103">Przesuwa kursor tego modułu wyliczającego z jego bieżącej pozycji, dzięki czemu są pomijane przez określoną liczbę elementów.</span><span class="sxs-lookup"><span data-stu-id="4a05c-103">Advances the cursor of this enumerator from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a05c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4a05c-104">Syntax</span></span>  
  
```  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4a05c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4a05c-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="4a05c-106">[in] Liczba elementów, które mają zostać pominięte.</span><span class="sxs-lookup"><span data-stu-id="4a05c-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a05c-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4a05c-107">Remarks</span></span>  
 <span data-ttu-id="4a05c-108">Nowe położenie kursora ten moduł wyliczający jest: (bieżącej pozycji) + `celt` .</span><span class="sxs-lookup"><span data-stu-id="4a05c-108">The new position of this enumerator's cursor is: (current position) + `celt` .</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a05c-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4a05c-109">Requirements</span></span>  
 <span data-ttu-id="4a05c-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a05c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a05c-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="4a05c-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4a05c-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4a05c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a05c-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a05c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a05c-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4a05c-114">See also</span></span>

- [<span data-ttu-id="4a05c-115">ICorProfilerObjectEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="4a05c-115">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)

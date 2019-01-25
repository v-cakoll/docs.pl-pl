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
ms.openlocfilehash: 2f1e12e59eefece1aa3a2a2294b34f5cee7c700c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54543110"
---
# <a name="icorprofilerobjectenumskip-method"></a><span data-ttu-id="ab621-102">ICorProfilerObjectEnum::Skip — Metoda</span><span class="sxs-lookup"><span data-stu-id="ab621-102">ICorProfilerObjectEnum::Skip Method</span></span>
<span data-ttu-id="ab621-103">Przesuwa kursor tego modułu wyliczającego z jego bieżącej pozycji, dzięki czemu są pomijane przez określoną liczbę elementów.</span><span class="sxs-lookup"><span data-stu-id="ab621-103">Advances the cursor of this enumerator from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab621-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ab621-104">Syntax</span></span>  
  
```  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="ab621-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ab621-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="ab621-106">[in] Liczba elementów, które mają zostać pominięte.</span><span class="sxs-lookup"><span data-stu-id="ab621-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ab621-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ab621-107">Remarks</span></span>  
 <span data-ttu-id="ab621-108">Nowe położenie kursora ten moduł wyliczający jest: (bieżącej pozycji) + `celt` .</span><span class="sxs-lookup"><span data-stu-id="ab621-108">The new position of this enumerator's cursor is: (current position) + `celt` .</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ab621-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ab621-109">Requirements</span></span>  
 <span data-ttu-id="ab621-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab621-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab621-111">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="ab621-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="ab621-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ab621-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ab621-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab621-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab621-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ab621-114">See also</span></span>
- [<span data-ttu-id="ab621-115">ICorProfilerObjectEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="ab621-115">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)

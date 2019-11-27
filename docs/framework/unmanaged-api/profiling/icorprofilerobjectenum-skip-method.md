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
ms.openlocfilehash: 3c573c709e765fa723a726f5c8990ba59222ed1f
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74428130"
---
# <a name="icorprofilerobjectenumskip-method"></a><span data-ttu-id="26829-102">ICorProfilerObjectEnum::Skip — Metoda</span><span class="sxs-lookup"><span data-stu-id="26829-102">ICorProfilerObjectEnum::Skip Method</span></span>
<span data-ttu-id="26829-103">Przesuwa kursor tego modułu wyliczającego z jego bieżącej pozycji, tak aby określona liczba elementów została pominięta.</span><span class="sxs-lookup"><span data-stu-id="26829-103">Advances the cursor of this enumerator from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26829-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="26829-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="26829-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="26829-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="26829-106">podczas Liczba elementów, które mają zostać pominięte.</span><span class="sxs-lookup"><span data-stu-id="26829-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26829-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="26829-107">Remarks</span></span>  
 <span data-ttu-id="26829-108">Nowa pozycja kursora tego modułu wyliczającego to: (bieżąca pozycja) + `celt`.</span><span class="sxs-lookup"><span data-stu-id="26829-108">The new position of this enumerator's cursor is: (current position) + `celt` .</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="26829-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="26829-109">Requirements</span></span>  
 <span data-ttu-id="26829-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26829-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26829-111">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="26829-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="26829-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="26829-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="26829-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26829-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26829-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="26829-114">See also</span></span>

- [<span data-ttu-id="26829-115">ICorProfilerObjectEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="26829-115">ICorProfilerObjectEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerobjectenum-interface.md)

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
ms.openlocfilehash: 096489fcdc9d604e003386501c22967b45ba6d7f
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76861115"
---
# <a name="icorprofilerobjectenumskip-method"></a><span data-ttu-id="0c661-102">ICorProfilerObjectEnum::Skip — Metoda</span><span class="sxs-lookup"><span data-stu-id="0c661-102">ICorProfilerObjectEnum::Skip Method</span></span>
<span data-ttu-id="0c661-103">Przesuwa kursor tego modułu wyliczającego z jego bieżącej pozycji, tak aby określona liczba elementów została pominięta.</span><span class="sxs-lookup"><span data-stu-id="0c661-103">Advances the cursor of this enumerator from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c661-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0c661-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip (  
    [in] ULONG   celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c661-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0c661-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="0c661-106">podczas Liczba elementów, które mają zostać pominięte.</span><span class="sxs-lookup"><span data-stu-id="0c661-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c661-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0c661-107">Remarks</span></span>  
 <span data-ttu-id="0c661-108">Nowa pozycja kursora tego modułu wyliczającego to: (bieżąca pozycja) + `celt`.</span><span class="sxs-lookup"><span data-stu-id="0c661-108">The new position of this enumerator's cursor is: (current position) + `celt` .</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c661-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0c661-109">Requirements</span></span>  
 <span data-ttu-id="0c661-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c661-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c661-111">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="0c661-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0c661-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0c661-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0c661-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c661-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c661-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0c661-114">See also</span></span>

- [<span data-ttu-id="0c661-115">ICorProfilerObjectEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="0c661-115">ICorProfilerObjectEnum Interface</span></span>](icorprofilerobjectenum-interface.md)

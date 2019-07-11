---
title: ICorProfilerFunctionEnum::Skip — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerFunctionEnum.Skip Method
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerFunctionEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerFunctionEnum interface [.NET Framework profiling]
- ICorProfilerFunctionEnum::Skip method [.NET Framework profiling]
ms.assetid: 051465b9-e479-494a-804b-c880323b4cbe
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 755b022dde01a1d424fea58bcefe5df2bce401b3
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67780283"
---
# <a name="icorprofilerfunctionenumskip-method"></a><span data-ttu-id="78c11-102">ICorProfilerFunctionEnum::Skip — Metoda</span><span class="sxs-lookup"><span data-stu-id="78c11-102">ICorProfilerFunctionEnum::Skip Method</span></span>
<span data-ttu-id="78c11-103">Przesuwa kursor modułu wyliczającego z jego bieżącej pozycji, tak, aby określoną liczbę elementów są pomijane.</span><span class="sxs-lookup"><span data-stu-id="78c11-103">Advances the enumerator's cursor from its current position so that the specified number of elements are skipped.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78c11-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="78c11-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip([in] ULONG celt);  
```  
  
## <a name="parameters"></a><span data-ttu-id="78c11-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="78c11-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="78c11-106">[in] Liczba elementów, które mają zostać pominięte.</span><span class="sxs-lookup"><span data-stu-id="78c11-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="78c11-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="78c11-107">Return Value</span></span>  
 <span data-ttu-id="78c11-108">Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="78c11-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="78c11-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="78c11-109">HRESULT</span></span>|<span data-ttu-id="78c11-110">Opis</span><span class="sxs-lookup"><span data-stu-id="78c11-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="78c11-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="78c11-111">S_OK</span></span>|<span data-ttu-id="78c11-112">`celt` elementy zostały pominięte.</span><span class="sxs-lookup"><span data-stu-id="78c11-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="78c11-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="78c11-113">S_FALSE</span></span>|<span data-ttu-id="78c11-114">Mniej niż `celt` elementy zostały pominięte, co oznacza, że nie istnieją żadne więcej elementów.</span><span class="sxs-lookup"><span data-stu-id="78c11-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="78c11-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="78c11-115">Remarks</span></span>  
 <span data-ttu-id="78c11-116">Nowe położenie kursora ten moduł wyliczający jest (bieżącej pozycji) + `celt`.</span><span class="sxs-lookup"><span data-stu-id="78c11-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78c11-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="78c11-117">Requirements</span></span>  
 <span data-ttu-id="78c11-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78c11-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78c11-119">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="78c11-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="78c11-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="78c11-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="78c11-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78c11-121">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78c11-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="78c11-122">See also</span></span>

- [<span data-ttu-id="78c11-123">ICorProfilerFunctionEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="78c11-123">ICorProfilerFunctionEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerfunctionenum-interface.md)
- [<span data-ttu-id="78c11-124">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="78c11-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)

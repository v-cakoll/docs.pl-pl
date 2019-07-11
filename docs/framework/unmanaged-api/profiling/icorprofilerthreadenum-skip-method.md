---
title: ICorProfilerThreadEnum::Skip — Metoda
ms.date: 03/30/2017
api_name:
- ICorProfilerThreadEnum.Skip
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerThreadEnum::Skip
helpviewer_keywords:
- Skip method, ICorProfilerThreadEnum interface [.NET Framework profiling]
- ICorProfilerThreadEnum::Skip method [.NET Framework profiling]
ms.assetid: acb8b029-4a96-4ed7-ae3c-310204e5ceea
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2c394c2b17404351bd0813ab1eb21230a1edd9de
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781097"
---
# <a name="icorprofilerthreadenumskip-method"></a><span data-ttu-id="a0a38-102">ICorProfilerThreadEnum::Skip — Metoda</span><span class="sxs-lookup"><span data-stu-id="a0a38-102">ICorProfilerThreadEnum::Skip Method</span></span>
<span data-ttu-id="a0a38-103">Przesuwa kursor modułu wyliczającego z jego bieżącej pozycji, aby pominąć określoną liczbę elementów.</span><span class="sxs-lookup"><span data-stu-id="a0a38-103">Advances the enumerator's cursor from its current position to skip the specified number of elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0a38-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a0a38-104">Syntax</span></span>  
  
```cpp  
HRESULT Skip (    [in] ULONG celt  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a0a38-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a0a38-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="a0a38-106">[in] Liczba elementów, które mają zostać pominięte.</span><span class="sxs-lookup"><span data-stu-id="a0a38-106">[in] The number of elements to be skipped.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a0a38-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="a0a38-107">Return Value</span></span>  
 <span data-ttu-id="a0a38-108">Ta metoda zwraca następujące specyficzne wyniki HRESULT, a także HRESULT błędów wskazujących Niepowodzenie metody.</span><span class="sxs-lookup"><span data-stu-id="a0a38-108">This method returns the following specific HRESULTs as well as HRESULT errors that indicate method failure.</span></span>  
  
|<span data-ttu-id="a0a38-109">HRESULT</span><span class="sxs-lookup"><span data-stu-id="a0a38-109">HRESULT</span></span>|<span data-ttu-id="a0a38-110">Opis</span><span class="sxs-lookup"><span data-stu-id="a0a38-110">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="a0a38-111">S_OK</span><span class="sxs-lookup"><span data-stu-id="a0a38-111">S_OK</span></span>|<span data-ttu-id="a0a38-112">`celt` elementy zostały pominięte.</span><span class="sxs-lookup"><span data-stu-id="a0a38-112">`celt` elements were skipped.</span></span>|  
|<span data-ttu-id="a0a38-113">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="a0a38-113">S_FALSE</span></span>|<span data-ttu-id="a0a38-114">Mniej niż `celt` elementy zostały pominięte, co oznacza, że nie istnieją żadne więcej elementów.</span><span class="sxs-lookup"><span data-stu-id="a0a38-114">Fewer than `celt` elements were skipped, which indicates that there are no more elements.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0a38-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a0a38-115">Remarks</span></span>  
 <span data-ttu-id="a0a38-116">Nowe położenie kursora ten moduł wyliczający jest (bieżącej pozycji) + `celt`.</span><span class="sxs-lookup"><span data-stu-id="a0a38-116">The new position of this enumerator's cursor is (current position) + `celt`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0a38-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a0a38-117">Requirements</span></span>  
 <span data-ttu-id="a0a38-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0a38-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0a38-119">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a0a38-119">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a0a38-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a0a38-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a0a38-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0a38-121">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0a38-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a0a38-122">See also</span></span>

- [<span data-ttu-id="a0a38-123">ICorProfilerThreadEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="a0a38-123">ICorProfilerThreadEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerthreadenum-interface.md)
- [<span data-ttu-id="a0a38-124">Interfejsy profilowania</span><span class="sxs-lookup"><span data-stu-id="a0a38-124">Profiling Interfaces</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-interfaces.md)

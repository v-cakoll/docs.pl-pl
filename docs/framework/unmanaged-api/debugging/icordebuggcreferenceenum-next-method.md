---
title: ICorDebugGCReferenceEnum::Next — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugGCReferenceEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGCReferenceEnum::Next
helpviewer_keywords:
- Next method, ICorDebugGCReferenceEnum interface [.NET Framework debugging]
- ICorDebugGCReferenceEnum::Next method [.NET Framework debugging]
ms.assetid: 91b1345c-a94f-4ef8-9696-3823d06c6d05
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 829d114c4aa2b2ce292ff2ae365af77784d49b52
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54673847"
---
# <a name="icordebuggcreferenceenumnext-method"></a><span data-ttu-id="edebc-102">ICorDebugGCReferenceEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="edebc-102">ICorDebugGCReferenceEnum::Next Method</span></span>
<span data-ttu-id="edebc-103">Pobiera określoną liczbę [cor_gc_reference —](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) wystąpień, które zawierają informacje o obiektach, których będzie jesdnostką zbierającą śmieci.</span><span class="sxs-lookup"><span data-stu-id="edebc-103">Gets the specified number of [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instances that contain information about objects that will be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="edebc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="edebc-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_GC_REFERENCE roots[],   
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="edebc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="edebc-105">Parameters</span></span>  
 <span data-ttu-id="edebc-106">celt</span><span class="sxs-lookup"><span data-stu-id="edebc-106">celt</span></span>  
 <span data-ttu-id="edebc-107">[in] Liczba głównych do pobrania.</span><span class="sxs-lookup"><span data-stu-id="edebc-107">[in] The number of roots to be retrieved.</span></span>  
  
 <span data-ttu-id="edebc-108">elementy główne</span><span class="sxs-lookup"><span data-stu-id="edebc-108">roots</span></span>  
 <span data-ttu-id="edebc-109">[out] Tablica wskaźników, z których każdy wskazuje [cor_gc_reference —](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) obiekt, który reprezentuje katalog główny obiekt można było zebranych elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="edebc-109">[out] An array of pointers, each of which points to a [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) object that represents the root of an object to be garbage-collected.</span></span>  
  
 <span data-ttu-id="edebc-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="edebc-110">pceltFetched</span></span>  
 <span data-ttu-id="edebc-111">[out] Wskaźnik do liczby [cor_gc_reference —](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) obiekty, które faktycznie są zwracane w `roots`.</span><span class="sxs-lookup"><span data-stu-id="edebc-111">[out] A pointer to the number of [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objects actually returned in `roots`.</span></span> <span data-ttu-id="edebc-112">Ta wartość może być `null` Jeśli `celt` 1.</span><span class="sxs-lookup"><span data-stu-id="edebc-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="edebc-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="edebc-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="edebc-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="edebc-114">Requirements</span></span>  
 <span data-ttu-id="edebc-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="edebc-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="edebc-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="edebc-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="edebc-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="edebc-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="edebc-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="edebc-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="edebc-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="edebc-119">See also</span></span>
- [<span data-ttu-id="edebc-120">ICorDebugGCReferenceEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="edebc-120">ICorDebugGCReferenceEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)
- [<span data-ttu-id="edebc-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="edebc-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

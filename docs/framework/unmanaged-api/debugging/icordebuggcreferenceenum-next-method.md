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
ms.openlocfilehash: 01e52385f1a94ffb9682bdbe92e5c95e9870611e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33416806"
---
# <a name="icordebuggcreferenceenumnext-method"></a><span data-ttu-id="919d4-102">ICorDebugGCReferenceEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="919d4-102">ICorDebugGCReferenceEnum::Next Method</span></span>
<span data-ttu-id="919d4-103">Pobiera określoną liczbę [cor_gc_reference —](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) wystąpień, które zawierają informacje o obiektach, które mają być zbierane z pamięci.</span><span class="sxs-lookup"><span data-stu-id="919d4-103">Gets the specified number of [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instances that contain information about objects that will be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="919d4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="919d4-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_GC_REFERENCE roots[],   
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="919d4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="919d4-105">Parameters</span></span>  
 <span data-ttu-id="919d4-106">celt</span><span class="sxs-lookup"><span data-stu-id="919d4-106">celt</span></span>  
 <span data-ttu-id="919d4-107">[in] Liczba głównych, które mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="919d4-107">[in] The number of roots to be retrieved.</span></span>  
  
 <span data-ttu-id="919d4-108">elementy główne</span><span class="sxs-lookup"><span data-stu-id="919d4-108">roots</span></span>  
 <span data-ttu-id="919d4-109">[out] Tablicy wskaźników, z których każdy wskazuje [cor_gc_reference —](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) obiekt, który reprezentuje katalog główny obiekt, aby być zbierane z pamięci.</span><span class="sxs-lookup"><span data-stu-id="919d4-109">[out] An array of pointers, each of which points to a [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) object that represents the root of an object to be garbage-collected.</span></span>  
  
 <span data-ttu-id="919d4-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="919d4-110">pceltFetched</span></span>  
 <span data-ttu-id="919d4-111">[out] Wskaźnik do liczby [cor_gc_reference —](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) obiekty zwrócone faktycznie w `roots`.</span><span class="sxs-lookup"><span data-stu-id="919d4-111">[out] A pointer to the number of [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objects actually returned in `roots`.</span></span> <span data-ttu-id="919d4-112">Ta wartość może być `null` Jeśli `celt` 1.</span><span class="sxs-lookup"><span data-stu-id="919d4-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="919d4-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="919d4-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="919d4-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="919d4-114">Requirements</span></span>  
 <span data-ttu-id="919d4-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="919d4-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="919d4-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="919d4-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="919d4-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="919d4-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="919d4-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="919d4-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="919d4-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="919d4-119">See Also</span></span>  
 [<span data-ttu-id="919d4-120">ICorDebugGCReferenceEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="919d4-120">ICorDebugGCReferenceEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)  
 [<span data-ttu-id="919d4-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="919d4-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

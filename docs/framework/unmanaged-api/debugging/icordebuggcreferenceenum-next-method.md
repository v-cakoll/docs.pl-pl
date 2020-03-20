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
ms.openlocfilehash: d87f414e9dfd05a519b60efc7ecdd5328a6dd86f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178863"
---
# <a name="icordebuggcreferenceenumnext-method"></a><span data-ttu-id="d3cf3-102">ICorDebugGCReferenceEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="d3cf3-102">ICorDebugGCReferenceEnum::Next Method</span></span>
<span data-ttu-id="d3cf3-103">Pobiera określoną liczbę [COR_GC_REFERENCE](cor-gc-reference-structure.md) wystąpień, które zawierają informacje o obiektach, które będą zbierane śmieci.</span><span class="sxs-lookup"><span data-stu-id="d3cf3-103">Gets the specified number of [COR_GC_REFERENCE](cor-gc-reference-structure.md) instances that contain information about objects that will be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3cf3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d3cf3-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_GC_REFERENCE roots[],
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d3cf3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d3cf3-105">Parameters</span></span>  
 <span data-ttu-id="d3cf3-106">Celt</span><span class="sxs-lookup"><span data-stu-id="d3cf3-106">celt</span></span>  
 <span data-ttu-id="d3cf3-107">[w] Liczba katalogów głównych do pobrania.</span><span class="sxs-lookup"><span data-stu-id="d3cf3-107">[in] The number of roots to be retrieved.</span></span>  
  
 <span data-ttu-id="d3cf3-108">Korzenie</span><span class="sxs-lookup"><span data-stu-id="d3cf3-108">roots</span></span>  
 <span data-ttu-id="d3cf3-109">[na zewnątrz] Tablica wskaźników, z których każdy wskazuje [na obiekt COR_GC_REFERENCE,](cor-gc-reference-structure.md) który reprezentuje katalog główny obiektu, który ma być zbierane od śmieci.</span><span class="sxs-lookup"><span data-stu-id="d3cf3-109">[out] An array of pointers, each of which points to a [COR_GC_REFERENCE](cor-gc-reference-structure.md) object that represents the root of an object to be garbage-collected.</span></span>  
  
 <span data-ttu-id="d3cf3-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="d3cf3-110">pceltFetched</span></span>  
 <span data-ttu-id="d3cf3-111">[na zewnątrz] Wskaźnik do liczby [obiektów COR_GC_REFERENCE](cor-gc-reference-structure.md) faktycznie zwróconych w `roots`.</span><span class="sxs-lookup"><span data-stu-id="d3cf3-111">[out] A pointer to the number of [COR_GC_REFERENCE](cor-gc-reference-structure.md) objects actually returned in `roots`.</span></span> <span data-ttu-id="d3cf3-112">Ta wartość `null` może `celt` być, jeśli jest 1.</span><span class="sxs-lookup"><span data-stu-id="d3cf3-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d3cf3-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d3cf3-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3cf3-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d3cf3-114">Requirements</span></span>  
 <span data-ttu-id="d3cf3-115">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3cf3-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3cf3-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d3cf3-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d3cf3-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d3cf3-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d3cf3-118">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3cf3-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3cf3-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d3cf3-119">See also</span></span>

- [<span data-ttu-id="d3cf3-120">ICorDebugGCReferenceEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="d3cf3-120">ICorDebugGCReferenceEnum Interface</span></span>](icordebuggcreferenceenum-interface.md)
- [<span data-ttu-id="d3cf3-121">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="d3cf3-121">Debugging Interfaces</span></span>](debugging-interfaces.md)

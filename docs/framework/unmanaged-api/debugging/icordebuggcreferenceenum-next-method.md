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
ms.openlocfilehash: 43408486fec9cd50222eed08ec2d3397bc11bc18
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73134622"
---
# <a name="icordebuggcreferenceenumnext-method"></a><span data-ttu-id="b508d-102">ICorDebugGCReferenceEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="b508d-102">ICorDebugGCReferenceEnum::Next Method</span></span>
<span data-ttu-id="b508d-103">Pobiera określoną liczbę wystąpień [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) , które zawierają informacje o obiektach, które będą zbierane jako elementy bezużyteczne.</span><span class="sxs-lookup"><span data-stu-id="b508d-103">Gets the specified number of [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instances that contain information about objects that will be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b508d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b508d-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_GC_REFERENCE roots[],   
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b508d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b508d-105">Parameters</span></span>  
 <span data-ttu-id="b508d-106">celt</span><span class="sxs-lookup"><span data-stu-id="b508d-106">celt</span></span>  
 <span data-ttu-id="b508d-107">podczas Liczba katalogów głównych do pobrania.</span><span class="sxs-lookup"><span data-stu-id="b508d-107">[in] The number of roots to be retrieved.</span></span>  
  
 <span data-ttu-id="b508d-108">główny</span><span class="sxs-lookup"><span data-stu-id="b508d-108">roots</span></span>  
 <span data-ttu-id="b508d-109">określoną Tablica wskaźników, z których każdy wskazuje obiekt [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) , który reprezentuje element główny obiektu, który ma zostać odrzucony.</span><span class="sxs-lookup"><span data-stu-id="b508d-109">[out] An array of pointers, each of which points to a [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) object that represents the root of an object to be garbage-collected.</span></span>  
  
 <span data-ttu-id="b508d-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="b508d-110">pceltFetched</span></span>  
 <span data-ttu-id="b508d-111">określoną Wskaźnik do liczby obiektów [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) faktycznie zwróconych w `roots`.</span><span class="sxs-lookup"><span data-stu-id="b508d-111">[out] A pointer to the number of [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objects actually returned in `roots`.</span></span> <span data-ttu-id="b508d-112">Ta wartość może być `null`, jeśli `celt` wynosi 1.</span><span class="sxs-lookup"><span data-stu-id="b508d-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b508d-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b508d-113">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b508d-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b508d-114">Requirements</span></span>  
 <span data-ttu-id="b508d-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b508d-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b508d-116">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b508d-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b508d-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b508d-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b508d-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b508d-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b508d-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b508d-119">See also</span></span>

- [<span data-ttu-id="b508d-120">ICorDebugGCReferenceEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="b508d-120">ICorDebugGCReferenceEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md)
- [<span data-ttu-id="b508d-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="b508d-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

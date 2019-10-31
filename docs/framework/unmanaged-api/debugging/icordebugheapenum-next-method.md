---
title: ICorDebugHeapEnum::Next — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugHeapEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapEnum::Next
helpviewer_keywords:
- ICorDebugHeapEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugHeapEnum interface [.NET Framework debugging]
ms.assetid: 2221fd06-9e27-4113-972e-2530db8c3594
topic_type:
- apiref
ms.openlocfilehash: 1beb69bfaad9acb9c269ad8becb81bea64edb6a2
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138468"
---
# <a name="icordebugheapenumnext-method"></a><span data-ttu-id="8fe69-102">ICorDebugHeapEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="8fe69-102">ICorDebugHeapEnum::Next Method</span></span>
<span data-ttu-id="8fe69-103">Pobiera określoną liczbę wystąpień [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) , które zawierają informacje o obiektach na zarządzanym stosie.</span><span class="sxs-lookup"><span data-stu-id="8fe69-103">Gets the specified number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) instances that contain information about objects on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fe69-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8fe69-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_HEAPOBJECT  objects[],   
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8fe69-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8fe69-105">Parameters</span></span>  
 <span data-ttu-id="8fe69-106">celt</span><span class="sxs-lookup"><span data-stu-id="8fe69-106">celt</span></span>  
 <span data-ttu-id="8fe69-107">podczas Liczba obiektów do pobrania.</span><span class="sxs-lookup"><span data-stu-id="8fe69-107">[in] The number of objects to be retrieved.</span></span>  
  
 <span data-ttu-id="8fe69-108">— obiekty</span><span class="sxs-lookup"><span data-stu-id="8fe69-108">objects</span></span>  
 <span data-ttu-id="8fe69-109">określoną Tablica wskaźników, z których każdy wskazuje obiekt [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) , który zawiera informacje o obiekcie na zarządzanym stosie.</span><span class="sxs-lookup"><span data-stu-id="8fe69-109">[out] An array of pointers, each of which points to a [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) object that provides information about an object on the managed heap.</span></span>  
  
 <span data-ttu-id="8fe69-110">pceltFetched</span><span class="sxs-lookup"><span data-stu-id="8fe69-110">pceltFetched</span></span>  
 <span data-ttu-id="8fe69-111">określoną Wskaźnik do liczby obiektów [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) faktycznie zwróconych w `objects`.</span><span class="sxs-lookup"><span data-stu-id="8fe69-111">[out] A pointer to the number of [COR_HEAPOBJECT](../../../../docs/framework/unmanaged-api/debugging/cor-heapobject-structure.md) objects actually returned in `objects`.</span></span> <span data-ttu-id="8fe69-112">Ta wartość może być `null`, jeśli `celt` wynosi 1.</span><span class="sxs-lookup"><span data-stu-id="8fe69-112">This value may be `null` if `celt` is 1.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8fe69-113">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8fe69-113">Remarks</span></span>  
 <span data-ttu-id="8fe69-114">Pole `COR_HEAPOBJECT.type` jest identyfikatorem zagnieżdżonego, odwołującego się interfejsu COM.</span><span class="sxs-lookup"><span data-stu-id="8fe69-114">The `COR_HEAPOBJECT.type` field is the identifier of a nested reference-counted COM interface.</span></span> <span data-ttu-id="8fe69-115">To odwołanie musi zostać wydane przez obiekt wywołujący `ICorDebugHeapEnum::Next`.</span><span class="sxs-lookup"><span data-stu-id="8fe69-115">This reference must be released by the caller of `ICorDebugHeapEnum::Next`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8fe69-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8fe69-116">Requirements</span></span>  
 <span data-ttu-id="8fe69-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8fe69-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8fe69-118">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8fe69-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8fe69-119">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8fe69-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8fe69-120">**Wersje .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8fe69-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8fe69-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8fe69-121">See also</span></span>

- [<span data-ttu-id="8fe69-122">ICorDebugHeapEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="8fe69-122">ICorDebugHeapEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md)
- [<span data-ttu-id="8fe69-123">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="8fe69-123">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

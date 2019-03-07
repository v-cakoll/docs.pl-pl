---
title: ICorDebugExceptionObjectCallStackEnum::Next — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugExceptionObjectCallStackEnum::Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugExceptionObjectCallStackEnum::Next
helpviewer_keywords:
- ICorDebugExceptionObjectCallStackEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugExceptionObjectCallStackEnum interface [.NET Framework debugging]
ms.assetid: 3328a2c0-1e48-4a54-802a-9b474cf82c21
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0e7d8344c36fb97a73d0f64ebc3a47645527202e
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57494119"
---
# <a name="icordebugexceptionobjectcallstackenumnext-method"></a><span data-ttu-id="6d5e9-102">ICorDebugExceptionObjectCallStackEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="6d5e9-102">ICorDebugExceptionObjectCallStackEnum::Next Method</span></span>
<span data-ttu-id="6d5e9-103">Pobiera określoną liczbę [cordebugexceptionobjectstackframe —](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) wystąpień, które zawierają informacje ze stosu wywołań obiekt wyjątku.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-103">Gets the specified number of [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) instances that contain information from an exception object's call stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d5e9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6d5e9-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] CorDebugExceptionObjectStackFrame values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d5e9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6d5e9-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="6d5e9-106">[in] Liczba [cordebugexceptionobjectstackframe —](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) wystąpienia mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-106">[in] The number of [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="6d5e9-107">[out] Tablica wskaźników, z których każdy wskazuje [cordebugexceptionobjectstackframe —](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) obiektu.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-107">[out] An array of pointers, each of which points to a [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="6d5e9-108">[out] Wskaźnik do liczby [cordebugexceptionobjectstackframe —](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) wystąpień rzeczywistego zwrotu.</span><span class="sxs-lookup"><span data-stu-id="6d5e9-108">[out] A pointer to the number of [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) instances actually returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d5e9-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6d5e9-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d5e9-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6d5e9-110">Requirements</span></span>  
 <span data-ttu-id="6d5e9-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d5e9-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d5e9-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6d5e9-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6d5e9-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6d5e9-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d5e9-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d5e9-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d5e9-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6d5e9-115">See also</span></span>
- [<span data-ttu-id="6d5e9-116">ICorDebugExceptionObjectCallStackEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="6d5e9-116">ICorDebugExceptionObjectCallStackEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)
- [<span data-ttu-id="6d5e9-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="6d5e9-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

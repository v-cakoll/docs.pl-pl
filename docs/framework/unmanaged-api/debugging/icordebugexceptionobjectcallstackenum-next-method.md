---
title: "ICorDebugExceptionObjectCallStackEnum::Next — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugExceptionObjectCallStackEnum::Next
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugExceptionObjectCallStackEnum::Next
helpviewer_keywords:
- ICorDebugExceptionObjectCallStackEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugExceptionObjectCallStackEnum interface [.NET Framework debugging]
ms.assetid: 3328a2c0-1e48-4a54-802a-9b474cf82c21
topic_type: apiref
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: be050ad1c7b6e10f286a45844f5741689f264923
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugexceptionobjectcallstackenumnext-method"></a><span data-ttu-id="342de-102">ICorDebugExceptionObjectCallStackEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="342de-102">ICorDebugExceptionObjectCallStackEnum::Next Method</span></span>
<span data-ttu-id="342de-103">Pobiera określoną liczbę [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) wystąpień, które zawierają informacje dotyczące stosu wywołań obiekt wyjątku.</span><span class="sxs-lookup"><span data-stu-id="342de-103">Gets the specified number of [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) instances that contain information from an exception object's call stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="342de-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="342de-104">Syntax</span></span>  
  
```  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] CorDebugExceptionObjectStackFrame values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="342de-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="342de-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="342de-106">[in] Liczba [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) wystąpienia mają zostać pobrane.</span><span class="sxs-lookup"><span data-stu-id="342de-106">[in] The number of [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="342de-107">[out] Tablicy wskaźników, z których każdy wskazuje [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) obiektu.</span><span class="sxs-lookup"><span data-stu-id="342de-107">[out] An array of pointers, each of which points to a [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="342de-108">[out] Wskaźnik do liczby [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) wystąpienia faktycznie zwracane.</span><span class="sxs-lookup"><span data-stu-id="342de-108">[out] A pointer to the number of [CorDebugExceptionObjectStackFrame](../../../../docs/framework/unmanaged-api/debugging/cordebugexceptionobjectstackframe-structure.md) instances actually returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="342de-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="342de-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="342de-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="342de-110">Requirements</span></span>  
 <span data-ttu-id="342de-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="342de-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="342de-112">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="342de-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="342de-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="342de-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="342de-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="342de-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="342de-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="342de-115">See Also</span></span>  
 [<span data-ttu-id="342de-116">ICorDebugExceptionObjectCallStackEnum, interfejs</span><span class="sxs-lookup"><span data-stu-id="342de-116">ICorDebugExceptionObjectCallStackEnum Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugexceptionobjectcallstackenum-interface.md)  
 [<span data-ttu-id="342de-117">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="342de-117">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

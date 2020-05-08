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
ms.openlocfilehash: 6fce9f61e222d0fc1763495de162a94a7fc22689
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2020
ms.locfileid: "82975982"
---
# <a name="icordebugexceptionobjectcallstackenumnext-method"></a><span data-ttu-id="6b16f-102">ICorDebugExceptionObjectCallStackEnum::Next — Metoda</span><span class="sxs-lookup"><span data-stu-id="6b16f-102">ICorDebugExceptionObjectCallStackEnum::Next Method</span></span>
<span data-ttu-id="6b16f-103">Pobiera określoną liczbę wystąpień [CorDebugExceptionObjectStackFrame —](cordebugexceptionobjectstackframe-structure.md) , które zawierają informacje z stosu wywołań obiektu wyjątku.</span><span class="sxs-lookup"><span data-stu-id="6b16f-103">Gets the specified number of [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) instances that contain information from an exception object's call stack.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b16f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6b16f-104">Syntax</span></span>  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] CorDebugExceptionObjectStackFrame values[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6b16f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6b16f-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="6b16f-106">podczas Liczba wystąpień [CorDebugExceptionObjectStackFrame —](cordebugexceptionobjectstackframe-structure.md) do pobrania.</span><span class="sxs-lookup"><span data-stu-id="6b16f-106">[in] The number of [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) instances to be retrieved.</span></span>  
  
 `values`  
 <span data-ttu-id="6b16f-107">określoną Tablica wskaźników, z których każdy wskazuje obiekt [CorDebugExceptionObjectStackFrame —](cordebugexceptionobjectstackframe-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="6b16f-107">[out] An array of pointers, each of which points to a [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) object.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="6b16f-108">określoną Wskaźnik do liczby zwróconych wystąpień [CorDebugExceptionObjectStackFrame —](cordebugexceptionobjectstackframe-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="6b16f-108">[out] A pointer to the number of [CorDebugExceptionObjectStackFrame](cordebugexceptionobjectstackframe-structure.md) instances actually returned.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6b16f-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6b16f-109">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6b16f-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6b16f-110">Requirements</span></span>  
 <span data-ttu-id="6b16f-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b16f-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6b16f-112">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6b16f-112">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6b16f-113">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6b16f-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6b16f-114">**.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b16f-114">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b16f-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6b16f-115">See also</span></span>

- [<span data-ttu-id="6b16f-116">ICorDebugExceptionObjectCallStackEnum — Interfejs</span><span class="sxs-lookup"><span data-stu-id="6b16f-116">ICorDebugExceptionObjectCallStackEnum Interface</span></span>](icordebugexceptionobjectcallstackenum-interface.md)
- [<span data-ttu-id="6b16f-117">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="6b16f-117">Debugging Interfaces</span></span>](debugging-interfaces.md)

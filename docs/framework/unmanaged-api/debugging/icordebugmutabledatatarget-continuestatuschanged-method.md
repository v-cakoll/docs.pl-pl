---
title: 'ICorDebugMutableDataTarget:: ContinueStatusChanged, Metoda'
ms.date: 03/30/2017
ms.assetid: 5a66d3f4-dd16-4d62-9dcc-0eab7041d894
ms.openlocfilehash: 49f517c0c09771ce86e43b801f6d7fce695d907a
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213312"
---
# <a name="icordebugmutabledatatargetcontinuestatuschanged-method"></a><span data-ttu-id="982aa-102">ICorDebugMutableDataTarget:: ContinueStatusChanged, Metoda</span><span class="sxs-lookup"><span data-stu-id="982aa-102">ICorDebugMutableDataTarget::ContinueStatusChanged Method</span></span>
<span data-ttu-id="982aa-103">Zmienia stan kontynuacji dla zaległego zdarzenia debugowania w określonym wątku.</span><span class="sxs-lookup"><span data-stu-id="982aa-103">Changes the continuation status for the outstanding debug event on the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="982aa-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="982aa-104">Syntax</span></span>  
  
```cpp  
HRESULT ContinueStatusChanged(  
   [in] DWORD dwThreadId,  
   [in] CORDB_CONTINUE_STATUS continueStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="982aa-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="982aa-105">Parameters</span></span>  
 `dwThreadId`  
 <span data-ttu-id="982aa-106">Identyfikator wątku zdefiniowanego przez system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="982aa-106">The operating system-defined thread identifier.</span></span>  
  
 `continueStatus`  
 <span data-ttu-id="982aa-107">Wartość [COREDB_CONTINUE_STATUS](../common-data-types-unmanaged-api-reference.md) , która reprezentuje nowy żądany stan kontynuacji.</span><span class="sxs-lookup"><span data-stu-id="982aa-107">A [COREDB_CONTINUE_STATUS](../common-data-types-unmanaged-api-reference.md) value that represents the new requested continuation status.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="982aa-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="982aa-108">Remarks</span></span>  
 <span data-ttu-id="982aa-109">Debuger wywołuje metodę, `ContinueStatusChanged` gdy wywołuje metodę ICorDebug, która wymaga, aby bieżące zdarzenie debugowania zostało obsłużone w sposób, który może się różnić od sposobu, w jaki zwykle jest obsługiwany.</span><span class="sxs-lookup"><span data-stu-id="982aa-109">The debugger calls the `ContinueStatusChanged` method when it calls an ICorDebug method that requires the current debug event to be handled in a way that is potentially different from the way in which it normally would be handled.</span></span> <span data-ttu-id="982aa-110">Na przykład jeśli wystąpi wyjątek, a debuger żąda operacji, która spowodowałaby anulowanie wyjątku (na przykład [ICorDebugILFrame:: SetIP](icordebugilframe-setip-method.md) lub `FuncEval` ), ten interfejs API jest używany do żądania anulowania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="982aa-110">For example, if there is an outstanding exception, and the debugger requests an operation that would cancel the exception (such as [ICorDebugILFrame::SetIP](icordebugilframe-setip-method.md) or `FuncEval`), this API is used to request that the exception be cancelled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="982aa-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="982aa-111">Requirements</span></span>  
 <span data-ttu-id="982aa-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="982aa-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="982aa-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="982aa-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="982aa-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="982aa-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="982aa-115">**.NET Framework wersje:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="982aa-115">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="982aa-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="982aa-116">See also</span></span>

- [<span data-ttu-id="982aa-117">ICorDebugMutableDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="982aa-117">ICorDebugMutableDataTarget Interface</span></span>](icordebugmutabledatatarget-interface.md)
- [<span data-ttu-id="982aa-118">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="982aa-118">Debugging Interfaces</span></span>](debugging-interfaces.md)

---
title: 'ICorDebugMutableDataTarget:: ContinueStatusChanged, Metoda'
ms.date: 03/30/2017
ms.assetid: 5a66d3f4-dd16-4d62-9dcc-0eab7041d894
ms.openlocfilehash: c918bb60fba5bc1ec3f0f7c58b103d05a3c7ddfd
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792872"
---
# <a name="icordebugmutabledatatargetcontinuestatuschanged-method"></a><span data-ttu-id="a5993-102">ICorDebugMutableDataTarget:: ContinueStatusChanged, Metoda</span><span class="sxs-lookup"><span data-stu-id="a5993-102">ICorDebugMutableDataTarget::ContinueStatusChanged Method</span></span>
<span data-ttu-id="a5993-103">Zmienia stan kontynuacji dla zaległego zdarzenia debugowania w określonym wątku.</span><span class="sxs-lookup"><span data-stu-id="a5993-103">Changes the continuation status for the outstanding debug event on the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a5993-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a5993-104">Syntax</span></span>  
  
```cpp  
HRESULT ContinueStatusChanged(  
   [in] DWORD dwThreadId,  
   [in] CORDB_CONTINUE_STATUS continueStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="a5993-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a5993-105">Parameters</span></span>  
 `dwThreadId`  
 <span data-ttu-id="a5993-106">Identyfikator wątku zdefiniowanego przez system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="a5993-106">The operating system-defined thread identifier.</span></span>  
  
 `continueStatus`  
 <span data-ttu-id="a5993-107">Wartość [COREDB_CONTINUE_STATUS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) , która reprezentuje nowy żądany stan kontynuacji.</span><span class="sxs-lookup"><span data-stu-id="a5993-107">A [COREDB_CONTINUE_STATUS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the new requested continuation status.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a5993-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a5993-108">Remarks</span></span>  
 <span data-ttu-id="a5993-109">Debuger wywołuje metodę `ContinueStatusChanged`, gdy wywołuje metodę ICorDebug, która wymaga, aby bieżące zdarzenie debugowania zostało obsłużone w sposób, który może się różnić w zależności od tego, w jaki sposób zwykle byłyby obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="a5993-109">The debugger calls the `ContinueStatusChanged` method when it calls an ICorDebug method that requires the current debug event to be handled in a way that is potentially different from the way in which it normally would be handled.</span></span> <span data-ttu-id="a5993-110">Jeśli na przykład wystąpił wyjątek oczekujący, a debuger żąda operacji, która spowodowałaby anulowanie wyjątku (na przykład [ICorDebugILFrame:: SetIP](icordebugilframe-setip-method.md) lub `FuncEval`), ten interfejs API jest używany do żądania anulowania wyjątku.</span><span class="sxs-lookup"><span data-stu-id="a5993-110">For example, if there is an outstanding exception, and the debugger requests an operation that would cancel the exception (such as [ICorDebugILFrame::SetIP](icordebugilframe-setip-method.md) or `FuncEval`), this API is used to request that the exception be cancelled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a5993-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a5993-111">Requirements</span></span>  
 <span data-ttu-id="a5993-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a5993-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a5993-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="a5993-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a5993-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="a5993-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a5993-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a5993-115">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a5993-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a5993-116">See also</span></span>

- [<span data-ttu-id="a5993-117">ICorDebugMutableDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="a5993-117">ICorDebugMutableDataTarget Interface</span></span>](icordebugmutabledatatarget-interface.md)
- [<span data-ttu-id="a5993-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="a5993-118">Debugging Interfaces</span></span>](debugging-interfaces.md)

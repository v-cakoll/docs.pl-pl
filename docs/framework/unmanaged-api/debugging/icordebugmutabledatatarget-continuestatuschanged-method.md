---
title: ICorDebugMutableDataTarget::ContinueStatusChanged Method
ms.date: 03/30/2017
ms.assetid: 5a66d3f4-dd16-4d62-9dcc-0eab7041d894
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 52b5c63f35732655834768eb5b914406203d423c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61927364"
---
# <a name="icordebugmutabledatatargetcontinuestatuschanged-method"></a><span data-ttu-id="0421d-102">ICorDebugMutableDataTarget::ContinueStatusChanged Method</span><span class="sxs-lookup"><span data-stu-id="0421d-102">ICorDebugMutableDataTarget::ContinueStatusChanged Method</span></span>
<span data-ttu-id="0421d-103">Zmienia stan kontynuacji dla zdarzenia debugowania oczekujących na określonego wątku.</span><span class="sxs-lookup"><span data-stu-id="0421d-103">Changes the continuation status for the outstanding debug event on the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0421d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0421d-104">Syntax</span></span>  
  
```  
HRESULT ContinueStatusChanged(  
   [in] DWORD dwThreadId,  
   [in] CORDB_CONTINUE_STATUS continueStatus);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0421d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0421d-105">Parameters</span></span>  
 `dwThreadId`  
 <span data-ttu-id="0421d-106">Identyfikator wątku zdefiniowaną przez system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="0421d-106">The operating system-defined thread identifier.</span></span>  
  
 `continueStatus`  
 <span data-ttu-id="0421d-107">A [COREDB_CONTINUE_STATUS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) wartość, która reprezentuje nowy żądany stan kontynuacji.</span><span class="sxs-lookup"><span data-stu-id="0421d-107">A [COREDB_CONTINUE_STATUS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) value that represents the new requested continuation status.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0421d-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0421d-108">Remarks</span></span>  
 <span data-ttu-id="0421d-109">Wywołuje debugera `ContinueStatusChanged` metody, gdy wywołuje metodę ICorDebug wymaga bieżącego zdarzenia debugowania, które mają być obsługiwane w sposób, który potencjalnie różni się od sposobu, w którym ją będą przechowywane i udostępniane.</span><span class="sxs-lookup"><span data-stu-id="0421d-109">The debugger calls the `ContinueStatusChanged` method when it calls an ICorDebug method that requires the current debug event to be handled in a way that is potentially different from the way in which it normally would be handled.</span></span> <span data-ttu-id="0421d-110">Na przykład, jeśli występuje wyjątek zaległe i debuger żądania operacji, która spowoduje anulowanie wyjątku (takie jak [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) lub `FuncEval`), ten interfejs API jest używany do żądania, aby był wyjątek anulowane.</span><span class="sxs-lookup"><span data-stu-id="0421d-110">For example, if there is an outstanding exception, and the debugger requests an operation that would cancel the exception (such as [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) or `FuncEval`), this API is used to request that the exception be cancelled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0421d-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0421d-111">Requirements</span></span>  
 <span data-ttu-id="0421d-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0421d-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0421d-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0421d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0421d-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0421d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0421d-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0421d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0421d-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0421d-116">See also</span></span>

- [<span data-ttu-id="0421d-117">ICorDebugMutableDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="0421d-117">ICorDebugMutableDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)
- [<span data-ttu-id="0421d-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="0421d-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

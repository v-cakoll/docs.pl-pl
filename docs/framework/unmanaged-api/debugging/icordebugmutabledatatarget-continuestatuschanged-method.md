---
title: ICorDebugMutableDataTarget::ContinueStatusChanged — metoda
ms.date: 03/30/2017
ms.assetid: 5a66d3f4-dd16-4d62-9dcc-0eab7041d894
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cb07c519743c41a7a31994e42d2fdc5220e5e2ef
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmutabledatatargetcontinuestatuschanged-method"></a><span data-ttu-id="2b99c-102">ICorDebugMutableDataTarget::ContinueStatusChanged — metoda</span><span class="sxs-lookup"><span data-stu-id="2b99c-102">ICorDebugMutableDataTarget::ContinueStatusChanged Method</span></span>
<span data-ttu-id="2b99c-103">Zmienia stan kontynuacji dla zdarzenia debugowania oczekujących na określony wątek.</span><span class="sxs-lookup"><span data-stu-id="2b99c-103">Changes the continuation status for the outstanding debug event on the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b99c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2b99c-104">Syntax</span></span>  
  
```  
HRESULT ContinueStatusChanged(  
   [in] DWORD dwThreadId,  
   [in] CORDB_CONTINUE_STATUS continueStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2b99c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2b99c-105">Parameters</span></span>  
 `dwThreadId`  
 <span data-ttu-id="2b99c-106">Identyfikator wątku zdefiniowane przez system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="2b99c-106">The operating system-defined thread identifier.</span></span>  
  
 `continueStatus`  
 <span data-ttu-id="2b99c-107">A[COREDB_CONTINUE_STATUS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)wartość, która reprezentuje nowe żądanie kontynuacji stanu.</span><span class="sxs-lookup"><span data-stu-id="2b99c-107">A[COREDB_CONTINUE_STATUS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)value that represents the new requested continuation status.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2b99c-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2b99c-108">Remarks</span></span>  
 <span data-ttu-id="2b99c-109">Wywołań debugera `ContinueStatusChanged` metody, gdy wywołuje metodę ICorDebug wymaga bieżącego zdarzenia debugowania mają zostać obsłużone w sposób zapewniający potencjalnie różni się od sposób, w którym go zwykle może być obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="2b99c-109">The debugger calls the `ContinueStatusChanged` method when it calls an ICorDebug method that requires the current debug event to be handled in a way that is potentially different from the way in which it normally would be handled.</span></span> <span data-ttu-id="2b99c-110">Na przykład, jeśli istnieje oczekujące wyjątek i debuger żądań operację, która spowoduje anulowanie wyjątek (takich jak [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) lub `FuncEval`), ten interfejs API jest używany do żądania, aby był wyjątek anulowane.</span><span class="sxs-lookup"><span data-stu-id="2b99c-110">For example, if there is an outstanding exception, and the debugger requests an operation that would cancel the exception (such as [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) or `FuncEval`), this API is used to request that the exception be cancelled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b99c-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2b99c-111">Requirements</span></span>  
 <span data-ttu-id="2b99c-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b99c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b99c-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2b99c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2b99c-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2b99c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2b99c-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b99c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b99c-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2b99c-116">See Also</span></span>  
 [<span data-ttu-id="2b99c-117">ICorDebugMutableDataTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="2b99c-117">ICorDebugMutableDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 [<span data-ttu-id="2b99c-118">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="2b99c-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

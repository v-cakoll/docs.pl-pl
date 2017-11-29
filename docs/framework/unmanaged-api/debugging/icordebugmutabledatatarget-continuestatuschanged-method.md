---
title: "ICorDebugMutableDataTarget::ContinueStatusChanged — metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 5a66d3f4-dd16-4d62-9dcc-0eab7041d894
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 2f4f3890f2cfb2e3b017b8c7d0705d8c8e063957
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmutabledatatargetcontinuestatuschanged-method"></a><span data-ttu-id="62e08-102">ICorDebugMutableDataTarget::ContinueStatusChanged — metoda</span><span class="sxs-lookup"><span data-stu-id="62e08-102">ICorDebugMutableDataTarget::ContinueStatusChanged Method</span></span>
<span data-ttu-id="62e08-103">Zmienia stan kontynuacji dla zdarzenia debugowania oczekujących na określony wątek.</span><span class="sxs-lookup"><span data-stu-id="62e08-103">Changes the continuation status for the outstanding debug event on the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62e08-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="62e08-104">Syntax</span></span>  
  
```  
HRESULT ContinueStatusChanged(  
   [in] DWORD dwThreadId,  
   [in] CORDB_CONTINUE_STATUS continueStatus);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="62e08-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="62e08-105">Parameters</span></span>  
 `dwThreadId`  
 <span data-ttu-id="62e08-106">Identyfikator wątku zdefiniowane przez system operacyjny.</span><span class="sxs-lookup"><span data-stu-id="62e08-106">The operating system-defined thread identifier.</span></span>  
  
 `continueStatus`  
 <span data-ttu-id="62e08-107">A[COREDB_CONTINUE_STATUS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)wartość, która reprezentuje nowe żądanie kontynuacji stanu.</span><span class="sxs-lookup"><span data-stu-id="62e08-107">A[COREDB_CONTINUE_STATUS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md)value that represents the new requested continuation status.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="62e08-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="62e08-108">Remarks</span></span>  
 <span data-ttu-id="62e08-109">Wywołań debugera `ContinueStatusChanged` metody, gdy wywołuje metodę ICorDebug wymaga bieżącego zdarzenia debugowania mają zostać obsłużone w sposób zapewniający potencjalnie różni się od sposób, w którym go zwykle może być obsługiwane.</span><span class="sxs-lookup"><span data-stu-id="62e08-109">The debugger calls the `ContinueStatusChanged` method when it calls an ICorDebug method that requires the current debug event to be handled in a way that is potentially different from the way in which it normally would be handled.</span></span> <span data-ttu-id="62e08-110">Na przykład, jeśli istnieje oczekujące wyjątek i debuger żądań operację, która spowoduje anulowanie wyjątek (takich jak [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) lub `FuncEval`), ten interfejs API jest używany do żądania, aby był wyjątek anulowane.</span><span class="sxs-lookup"><span data-stu-id="62e08-110">For example, if there is an outstanding exception, and the debugger requests an operation that would cancel the exception (such as [ICorDebugILFrame::SetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-setip-method.md) or `FuncEval`), this API is used to request that the exception be cancelled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="62e08-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="62e08-111">Requirements</span></span>  
 <span data-ttu-id="62e08-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="62e08-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="62e08-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="62e08-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="62e08-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="62e08-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="62e08-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="62e08-115">**.NET Framework Versions:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62e08-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="62e08-116">See Also</span></span>  
 [<span data-ttu-id="62e08-117">Interfejs ICorDebugMutableDataTarget</span><span class="sxs-lookup"><span data-stu-id="62e08-117">ICorDebugMutableDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 [<span data-ttu-id="62e08-118">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="62e08-118">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)

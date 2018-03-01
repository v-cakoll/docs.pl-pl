---
title: "ICorDebugController::Continue — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugController.Continue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugController::Continue
helpviewer_keywords:
- Continue method [.NET Framework debugging]
- ICorDebugController::Continue method [.NET Framework debugging]
ms.assetid: 8684cd06-ad3e-48ef-832e-15320e1f43a2
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e6a96145801aa8ef6482e30e9c00b763d2501f36
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugcontrollercontinue-method"></a><span data-ttu-id="68150-102">ICorDebugController::Continue — Metoda</span><span class="sxs-lookup"><span data-stu-id="68150-102">ICorDebugController::Continue Method</span></span>
<span data-ttu-id="68150-103">Wznawia wykonywanie wątków zarządzanych po wywołaniu [Metoda Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span><span class="sxs-lookup"><span data-stu-id="68150-103">Resumes execution of managed threads after a call to [Stop Method](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68150-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="68150-104">Syntax</span></span>  
  
```  
HRESULT Continue (  
    [in] BOOL fIsOutOfBand  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="68150-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="68150-105">Parameters</span></span>  
 `fIsOutOfBand`  
 <span data-ttu-id="68150-106">[in] Ustaw `true` Jeśli kontynuowanie ze zdarzenia poza pasmem; w przeciwnym razie wartość `false`.</span><span class="sxs-lookup"><span data-stu-id="68150-106">[in] Set to `true` if continuing from an out-of-band event; otherwise, set to `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="68150-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="68150-107">Remarks</span></span>  
 <span data-ttu-id="68150-108">`Continue`kontynuuje proces po wywołaniu `ICorDebugController::Stop` metody.</span><span class="sxs-lookup"><span data-stu-id="68150-108">`Continue` continues the process after a call to the `ICorDebugController::Stop` method.</span></span>  
  
 <span data-ttu-id="68150-109">Podczas debugowania w trybie mieszanym, nie należy wywoływać `Continue` na Win32 zdarzeń wątku, chyba że trwają ze zdarzenia poza pasmem.</span><span class="sxs-lookup"><span data-stu-id="68150-109">When doing mixed-mode debugging, do not call `Continue` on the Win32 event thread unless you are continuing from an out-of-band event.</span></span>  
  
 <span data-ttu-id="68150-110">*Zdarzeń wewnątrzpasmowe* zarządzanych zdarzeń lub normalne zdarzeń niezarządzane podczas którego debuger obsługuje interakcji z zarządzanego stan procesu.</span><span class="sxs-lookup"><span data-stu-id="68150-110">An *in-band event* is either a managed event or a normal unmanaged event during which the debugger supports interaction with the managed state of the process.</span></span> <span data-ttu-id="68150-111">W takim przypadku odbiera debuger [ICorDebugUnmanagedCallback::DebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md) wywołania zwrotnego z jego `fOutOfBand` ustawiono parametr `false`.</span><span class="sxs-lookup"><span data-stu-id="68150-111">In this case, the debugger receives the [ICorDebugUnmanagedCallback::DebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md) callback with its `fOutOfBand` parameter set to `false`.</span></span>  
  
 <span data-ttu-id="68150-112">*Poza pasmem zdarzenia* jest zdarzeniem niezarządzany, podczas którego interakcji z zarządzanego stan procesu jest niemożliwe, gdy proces jest zatrzymana z powodu zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="68150-112">An *out-of-band event* is an unmanaged event during which interaction with the managed state of the process is impossible while the process is stopped due to the event.</span></span> <span data-ttu-id="68150-113">W takim przypadku odbiera debuger `ICorDebugUnmanagedCallback::DebugEvent` wywołania zwrotnego z jego `fOutOfBand` ustawiono parametr `true`.</span><span class="sxs-lookup"><span data-stu-id="68150-113">In this case, the debugger receives the `ICorDebugUnmanagedCallback::DebugEvent` callback with its `fOutOfBand` parameter set to `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="68150-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="68150-114">Requirements</span></span>  
 <span data-ttu-id="68150-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="68150-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="68150-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="68150-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="68150-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="68150-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="68150-118">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="68150-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="68150-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="68150-119">See Also</span></span>  
 

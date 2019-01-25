---
title: ICorDebugController::Continue — Metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 115a998f8be233c38efac1a301b4b24b7d861662
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54540185"
---
# <a name="icordebugcontrollercontinue-method"></a><span data-ttu-id="97801-102">ICorDebugController::Continue — Metoda</span><span class="sxs-lookup"><span data-stu-id="97801-102">ICorDebugController::Continue Method</span></span>
<span data-ttu-id="97801-103">Wznawia wykonywanie wątków zarządzanych po wywołaniu [Metoda Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span><span class="sxs-lookup"><span data-stu-id="97801-103">Resumes execution of managed threads after a call to [Stop Method](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97801-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="97801-104">Syntax</span></span>  
  
```  
HRESULT Continue (  
    [in] BOOL fIsOutOfBand  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="97801-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="97801-105">Parameters</span></span>  
 `fIsOutOfBand`  
 <span data-ttu-id="97801-106">[in] Ustaw `true` Jeśli kontynuując zdarzenie out-of-band; w przeciwnym razie wartość `false`.</span><span class="sxs-lookup"><span data-stu-id="97801-106">[in] Set to `true` if continuing from an out-of-band event; otherwise, set to `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="97801-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="97801-107">Remarks</span></span>  
 <span data-ttu-id="97801-108">`Continue` kontynuuje proces po wywołaniu `ICorDebugController::Stop` metody.</span><span class="sxs-lookup"><span data-stu-id="97801-108">`Continue` continues the process after a call to the `ICorDebugController::Stop` method.</span></span>  
  
 <span data-ttu-id="97801-109">Podczas ustalania, debugowanie w trybie mieszanym, nie należy wywoływać metody `Continue` na Win32 zdarzeń wątku, chyba że trwają ze zdarzenia poza pasmem.</span><span class="sxs-lookup"><span data-stu-id="97801-109">When doing mixed-mode debugging, do not call `Continue` on the Win32 event thread unless you are continuing from an out-of-band event.</span></span>  
  
 <span data-ttu-id="97801-110">*Zdarzeń wewnątrzpasmowe* jest zdarzenie zarządzane lub normalne zdarzeń niezarządzanych, podczas którego debuger obsługuje interakcję z zarządzanego stan procesu.</span><span class="sxs-lookup"><span data-stu-id="97801-110">An *in-band event* is either a managed event or a normal unmanaged event during which the debugger supports interaction with the managed state of the process.</span></span> <span data-ttu-id="97801-111">W tym przypadku odbiera jest debugera [ICorDebugUnmanagedCallback::DebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md) wywołania zwrotnego z jego `fOutOfBand` parametr `false`.</span><span class="sxs-lookup"><span data-stu-id="97801-111">In this case, the debugger receives the [ICorDebugUnmanagedCallback::DebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md) callback with its `fOutOfBand` parameter set to `false`.</span></span>  
  
 <span data-ttu-id="97801-112">*Zdarzeń out-of-band* to zdarzenie niezarządzany, podczas którego interakcji z zarządzanego stan procesu jest niemożliwe, gdy proces zostanie zatrzymany z powodu zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="97801-112">An *out-of-band event* is an unmanaged event during which interaction with the managed state of the process is impossible while the process is stopped due to the event.</span></span> <span data-ttu-id="97801-113">W tym przypadku odbiera jest debugera `ICorDebugUnmanagedCallback::DebugEvent` wywołania zwrotnego z jego `fOutOfBand` parametr `true`.</span><span class="sxs-lookup"><span data-stu-id="97801-113">In this case, the debugger receives the `ICorDebugUnmanagedCallback::DebugEvent` callback with its `fOutOfBand` parameter set to `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97801-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="97801-114">Requirements</span></span>  
 <span data-ttu-id="97801-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="97801-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="97801-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="97801-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="97801-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="97801-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="97801-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="97801-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97801-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="97801-119">See also</span></span>


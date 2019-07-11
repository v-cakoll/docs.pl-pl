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
ms.openlocfilehash: c3a4e98a7265bda288b20b1cee1a10ab11990e8e
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67748886"
---
# <a name="icordebugcontrollercontinue-method"></a><span data-ttu-id="1f6fd-102">ICorDebugController::Continue — Metoda</span><span class="sxs-lookup"><span data-stu-id="1f6fd-102">ICorDebugController::Continue Method</span></span>
<span data-ttu-id="1f6fd-103">Wznawia wykonywanie wątków zarządzanych po wywołaniu [Metoda Stop](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span><span class="sxs-lookup"><span data-stu-id="1f6fd-103">Resumes execution of managed threads after a call to [Stop Method](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-stop-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f6fd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1f6fd-104">Syntax</span></span>  
  
```cpp  
HRESULT Continue (  
    [in] BOOL fIsOutOfBand  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1f6fd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1f6fd-105">Parameters</span></span>  
 `fIsOutOfBand`  
 <span data-ttu-id="1f6fd-106">[in] Ustaw `true` Jeśli kontynuując zdarzenie out-of-band; w przeciwnym razie wartość `false`.</span><span class="sxs-lookup"><span data-stu-id="1f6fd-106">[in] Set to `true` if continuing from an out-of-band event; otherwise, set to `false`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1f6fd-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1f6fd-107">Remarks</span></span>  
 <span data-ttu-id="1f6fd-108">`Continue` kontynuuje proces po wywołaniu `ICorDebugController::Stop` metody.</span><span class="sxs-lookup"><span data-stu-id="1f6fd-108">`Continue` continues the process after a call to the `ICorDebugController::Stop` method.</span></span>  
  
 <span data-ttu-id="1f6fd-109">Podczas ustalania, debugowanie w trybie mieszanym, nie należy wywoływać metody `Continue` na Win32 zdarzeń wątku, chyba że trwają ze zdarzenia poza pasmem.</span><span class="sxs-lookup"><span data-stu-id="1f6fd-109">When doing mixed-mode debugging, do not call `Continue` on the Win32 event thread unless you are continuing from an out-of-band event.</span></span>  
  
 <span data-ttu-id="1f6fd-110">*Zdarzeń wewnątrzpasmowe* jest zdarzenie zarządzane lub normalne zdarzeń niezarządzanych, podczas którego debuger obsługuje interakcję z zarządzanego stan procesu.</span><span class="sxs-lookup"><span data-stu-id="1f6fd-110">An *in-band event* is either a managed event or a normal unmanaged event during which the debugger supports interaction with the managed state of the process.</span></span> <span data-ttu-id="1f6fd-111">W tym przypadku odbiera jest debugera [ICorDebugUnmanagedCallback::DebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md) wywołania zwrotnego z jego `fOutOfBand` parametr `false`.</span><span class="sxs-lookup"><span data-stu-id="1f6fd-111">In this case, the debugger receives the [ICorDebugUnmanagedCallback::DebugEvent](../../../../docs/framework/unmanaged-api/debugging/icordebugunmanagedcallback-debugevent-method.md) callback with its `fOutOfBand` parameter set to `false`.</span></span>  
  
 <span data-ttu-id="1f6fd-112">*Zdarzeń out-of-band* to zdarzenie niezarządzany, podczas którego interakcji z zarządzanego stan procesu jest niemożliwe, gdy proces zostanie zatrzymany z powodu zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="1f6fd-112">An *out-of-band event* is an unmanaged event during which interaction with the managed state of the process is impossible while the process is stopped due to the event.</span></span> <span data-ttu-id="1f6fd-113">W tym przypadku odbiera jest debugera `ICorDebugUnmanagedCallback::DebugEvent` wywołania zwrotnego z jego `fOutOfBand` parametr `true`.</span><span class="sxs-lookup"><span data-stu-id="1f6fd-113">In this case, the debugger receives the `ICorDebugUnmanagedCallback::DebugEvent` callback with its `fOutOfBand` parameter set to `true`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f6fd-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1f6fd-114">Requirements</span></span>  
 <span data-ttu-id="1f6fd-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1f6fd-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1f6fd-116">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1f6fd-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1f6fd-117">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1f6fd-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1f6fd-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1f6fd-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f6fd-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1f6fd-119">See also</span></span>

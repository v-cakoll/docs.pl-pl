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
ms.openlocfilehash: 14356a12c944ef93dba5e7b818d3ee5cf5adc607
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125422"
---
# <a name="icordebugcontrollercontinue-method"></a><span data-ttu-id="ea910-102">ICorDebugController::Continue — Metoda</span><span class="sxs-lookup"><span data-stu-id="ea910-102">ICorDebugController::Continue Method</span></span>

<span data-ttu-id="ea910-103">Wznawia wykonywanie zarządzanych wątków po wywołaniu [metody Stop](icordebugcontroller-stop-method.md).</span><span class="sxs-lookup"><span data-stu-id="ea910-103">Resumes execution of managed threads after a call to [Stop Method](icordebugcontroller-stop-method.md).</span></span>

## <a name="syntax"></a><span data-ttu-id="ea910-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ea910-104">Syntax</span></span>

```cpp
HRESULT Continue (
    [in] BOOL fIsOutOfBand
);
```

## <a name="parameters"></a><span data-ttu-id="ea910-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ea910-105">Parameters</span></span>

`fIsOutOfBand`  
<span data-ttu-id="ea910-106">podczas Ustaw, aby `true` w przypadku kontynuowania z poziomu zdarzenia poza pasmem; w przeciwnym razie ustaw wartość `false`.</span><span class="sxs-lookup"><span data-stu-id="ea910-106">[in] Set to `true` if continuing from an out-of-band event; otherwise, set to `false`.</span></span>

## <a name="remarks"></a><span data-ttu-id="ea910-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ea910-107">Remarks</span></span>

<span data-ttu-id="ea910-108">`Continue` kontynuuje proces po wywołaniu metody `ICorDebugController::Stop`.</span><span class="sxs-lookup"><span data-stu-id="ea910-108">`Continue` continues the process after a call to the `ICorDebugController::Stop` method.</span></span>

<span data-ttu-id="ea910-109">Podczas przeprowadzania debugowania w trybie mieszanym nie należy wywoływać `Continue` w wątku zdarzenia Win32, chyba że będziesz kontynuować z poziomu zdarzenia poza pasmem.</span><span class="sxs-lookup"><span data-stu-id="ea910-109">When doing mixed-mode debugging, do not call `Continue` on the Win32 event thread unless you are continuing from an out-of-band event.</span></span>

<span data-ttu-id="ea910-110">*Zdarzenie w paśmie* jest zdarzeniem zarządzanym lub normalnym niezarządzanym zdarzeniem, w którym debuger obsługuje interakcje ze stanem zarządzanym procesu.</span><span class="sxs-lookup"><span data-stu-id="ea910-110">An *in-band event* is either a managed event or a normal unmanaged event during which the debugger supports interaction with the managed state of the process.</span></span> <span data-ttu-id="ea910-111">W takim przypadku debuger otrzymuje wywołanie zwrotne [ICorDebugUnmanagedCallback::D ebugevent](icordebugunmanagedcallback-debugevent-method.md) z parametrem `fOutOfBand` ustawionym na `false`.</span><span class="sxs-lookup"><span data-stu-id="ea910-111">In this case, the debugger receives the [ICorDebugUnmanagedCallback::DebugEvent](icordebugunmanagedcallback-debugevent-method.md) callback with its `fOutOfBand` parameter set to `false`.</span></span>

<span data-ttu-id="ea910-112">*Zdarzenie poza pasmem* jest zdarzeniem niezarządzanym, podczas którego interakcja ze stanem zarządzanym procesu jest niemożliwa, gdy proces został zatrzymany z powodu zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="ea910-112">An *out-of-band event* is an unmanaged event during which interaction with the managed state of the process is impossible while the process is stopped due to the event.</span></span> <span data-ttu-id="ea910-113">W takim przypadku debuger otrzymuje wywołanie zwrotne `ICorDebugUnmanagedCallback::DebugEvent` z parametrem `fOutOfBand` ustawionym na `true`.</span><span class="sxs-lookup"><span data-stu-id="ea910-113">In this case, the debugger receives the `ICorDebugUnmanagedCallback::DebugEvent` callback with its `fOutOfBand` parameter set to `true`.</span></span>

## <a name="requirements"></a><span data-ttu-id="ea910-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ea910-114">Requirements</span></span>

<span data-ttu-id="ea910-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ea910-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

<span data-ttu-id="ea910-116">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="ea910-116">**Header:** CorDebug.idl, CorDebug.h</span></span>

<span data-ttu-id="ea910-117">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="ea910-117">**Library:** CorGuids.lib</span></span>

<span data-ttu-id="ea910-118">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ea910-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>

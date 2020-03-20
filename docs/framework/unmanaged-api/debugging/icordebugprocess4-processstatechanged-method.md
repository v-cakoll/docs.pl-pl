---
title: ICorDebugProcess4::PproessStateChanged Method
ms.date: 02/07/2019
api_name:
- ICorDebugProcess4::ProcessStateChanged
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess4::ProcessStateChanged
helpviewer_keywords:
- ICorDebugProcess4::ProcessStateChanged method [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: a6f36f5b86b4fa58ce2a4ef4aa23d527f797a5a5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178631"
---
# <a name="icordebugprocess4processstatechanged-method"></a><span data-ttu-id="cedd8-102">ICorDebugProcess4::PproessStateChanged Method</span><span class="sxs-lookup"><span data-stu-id="cedd8-102">ICorDebugProcess4::ProcessStateChanged Method</span></span>

<span data-ttu-id="cedd8-103">Powiadamia potokU ICorDebug, że debuger poza procesem kontynuuje wykonanie debugee.</span><span class="sxs-lookup"><span data-stu-id="cedd8-103">Notifies the ICorDebug pipeline that the out of process debugger is continuing the debugee's execution.</span></span>

## <a name="syntax"></a><span data-ttu-id="cedd8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cedd8-104">Syntax</span></span>

```cpp
HRESULT ProcessStateChanged(
    [in] CorDebugStateChange change
);
```

## <a name="parameters"></a><span data-ttu-id="cedd8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cedd8-105">Parameters</span></span>

 `eChange`\
<span data-ttu-id="cedd8-106">[w] Członek [wyliczenia CorDebugStateChange](cordebugstatechange-enumeration.md) opisujące zmiany w stanie wykonywania procesu.</span><span class="sxs-lookup"><span data-stu-id="cedd8-106">[in] A member of the [CorDebugStateChange enumeration](cordebugstatechange-enumeration.md) describing a change in the process's execution state.</span></span>

## <a name="remarks"></a><span data-ttu-id="cedd8-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cedd8-107">Remarks</span></span>

<span data-ttu-id="cedd8-108">Podana metoda jest `ICorDebugProcess4` częścią interfejsu i odpowiada czwartemu slotowi tabeli metod wirtualnych.</span><span class="sxs-lookup"><span data-stu-id="cedd8-108">The provided method is part of the `ICorDebugProcess4` interface and corresponds to the fourth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="cedd8-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cedd8-109">Requirements</span></span>

 <span data-ttu-id="cedd8-110">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cedd8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

 <span data-ttu-id="cedd8-111">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="cedd8-111">**Header:** None</span></span>

 <span data-ttu-id="cedd8-112">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="cedd8-112">**Library:** None</span></span>

 <span data-ttu-id="cedd8-113">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cedd8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="cedd8-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cedd8-114">See also</span></span>

- [<span data-ttu-id="cedd8-115">ICorDebugProcess4, interfejs</span><span class="sxs-lookup"><span data-stu-id="cedd8-115">ICorDebugProcess4 Interface</span></span>](icordebugprocess4-interface.md)
- [<span data-ttu-id="cedd8-116">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="cedd8-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="cedd8-117">Debugging</span><span class="sxs-lookup"><span data-stu-id="cedd8-117">Debugging</span></span>](index.md)

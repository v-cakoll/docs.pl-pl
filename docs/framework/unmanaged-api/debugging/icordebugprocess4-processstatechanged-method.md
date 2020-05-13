---
title: ICorDebugProcess4::P rocessStateChanged Metoda
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
ms.openlocfilehash: 910c411d2c63ce2c6cf262e28e08546657dc2a4c
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213572"
---
# <a name="icordebugprocess4processstatechanged-method"></a><span data-ttu-id="498e9-102">ICorDebugProcess4::P rocessStateChanged Metoda</span><span class="sxs-lookup"><span data-stu-id="498e9-102">ICorDebugProcess4::ProcessStateChanged Method</span></span>

<span data-ttu-id="498e9-103">Powiadamia potok ICorDebug, że debuger out of process kontynuuje wykonywanie operacji debugee.</span><span class="sxs-lookup"><span data-stu-id="498e9-103">Notifies the ICorDebug pipeline that the out of process debugger is continuing the debugee's execution.</span></span>

## <a name="syntax"></a><span data-ttu-id="498e9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="498e9-104">Syntax</span></span>

```cpp
HRESULT ProcessStateChanged(
    [in] CorDebugStateChange change
);
```

## <a name="parameters"></a><span data-ttu-id="498e9-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="498e9-105">Parameters</span></span>

 `eChange`\
<span data-ttu-id="498e9-106">podczas Składowa [wyliczenia CorDebugStateChange](cordebugstatechange-enumeration.md) opisującego zmianę stanu wykonywania procesu.</span><span class="sxs-lookup"><span data-stu-id="498e9-106">[in] A member of the [CorDebugStateChange enumeration](cordebugstatechange-enumeration.md) describing a change in the process's execution state.</span></span>

## <a name="remarks"></a><span data-ttu-id="498e9-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="498e9-107">Remarks</span></span>

<span data-ttu-id="498e9-108">Podana metoda jest częścią `ICorDebugProcess4` interfejsu i odpowiada czwartemu gnieździe tabeli metody wirtualnej.</span><span class="sxs-lookup"><span data-stu-id="498e9-108">The provided method is part of the `ICorDebugProcess4` interface and corresponds to the fourth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="498e9-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="498e9-109">Requirements</span></span>

 <span data-ttu-id="498e9-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="498e9-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="498e9-111">**Nagłówek:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="498e9-111">**Header:** None</span></span>

 <span data-ttu-id="498e9-112">**Biblioteka:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="498e9-112">**Library:** None</span></span>

 <span data-ttu-id="498e9-113">**.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="498e9-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="498e9-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="498e9-114">See also</span></span>

- [<span data-ttu-id="498e9-115">ICorDebugProcess4, interfejs</span><span class="sxs-lookup"><span data-stu-id="498e9-115">ICorDebugProcess4 Interface</span></span>](icordebugprocess4-interface.md)
- [<span data-ttu-id="498e9-116">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="498e9-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="498e9-117">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="498e9-117">Debugging</span></span>](index.md)

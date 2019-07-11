---
title: ICorDebugProcess4::ProcessStateChanged Method
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
ms.openlocfilehash: adfd563e19389642ac0ed0a3cef4aae8a32fa466
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67767183"
---
# <a name="icordebugprocess4processstatechanged-method"></a><span data-ttu-id="69aa4-102">ICorDebugProcess4::ProcessStateChanged Method</span><span class="sxs-lookup"><span data-stu-id="69aa4-102">ICorDebugProcess4::ProcessStateChanged Method</span></span>

<span data-ttu-id="69aa4-103">Powiadamia potoku ICorDebug, poza debugera proces kontynuuje wykonywanie debugee.</span><span class="sxs-lookup"><span data-stu-id="69aa4-103">Notifies the ICorDebug pipeline that the out of process debugger is continuing the debugee's execution.</span></span>

## <a name="syntax"></a><span data-ttu-id="69aa4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="69aa4-104">Syntax</span></span>

```cpp
HRESULT ProcessStateChanged(
    [in] CorDebugStateChange change
);
```

## <a name="parameters"></a><span data-ttu-id="69aa4-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="69aa4-105">Parameters</span></span>

 `eChange`\
<span data-ttu-id="69aa4-106">[in] Członek [wyliczenie CorDebugStateChange](cordebugstatechange-enumeration.md) opisujące zmianę stanu wykonywania procesu.</span><span class="sxs-lookup"><span data-stu-id="69aa4-106">[in] A member of the [CorDebugStateChange enumeration](cordebugstatechange-enumeration.md) describing a change in the process's execution state.</span></span>

## <a name="remarks"></a><span data-ttu-id="69aa4-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="69aa4-107">Remarks</span></span>

<span data-ttu-id="69aa4-108">Podana metoda jest częścią `ICorDebugProcess4` interfejs i odpowiada czwarte miejsce tabeli wirtualnej metody.</span><span class="sxs-lookup"><span data-stu-id="69aa4-108">The provided method is part of the `ICorDebugProcess4` interface and corresponds to the fourth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="69aa4-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="69aa4-109">Requirements</span></span>

 <span data-ttu-id="69aa4-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69aa4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

 <span data-ttu-id="69aa4-111">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="69aa4-111">**Header:** None</span></span>

 <span data-ttu-id="69aa4-112">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="69aa4-112">**Library:** None</span></span>
 
 <span data-ttu-id="69aa4-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69aa4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="69aa4-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="69aa4-114">See also</span></span>

- [<span data-ttu-id="69aa4-115">ICorDebugProcess4 Interface</span><span class="sxs-lookup"><span data-stu-id="69aa4-115">ICorDebugProcess4 Interface</span></span>](icordebugprocess4-interface.md)
- [<span data-ttu-id="69aa4-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="69aa4-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="69aa4-117">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="69aa4-117">Debugging</span></span>](index.md)

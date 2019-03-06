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
ms.openlocfilehash: b77dd1277e7d23729f30d9d495c5417055a22759
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57378993"
---
# <a name="icordebugprocess4processstatechanged-method"></a><span data-ttu-id="55849-102">ICorDebugProcess4::ProcessStateChanged Method</span><span class="sxs-lookup"><span data-stu-id="55849-102">ICorDebugProcess4::ProcessStateChanged Method</span></span>

<span data-ttu-id="55849-103">Powiadamia potoku ICorDebug, poza debugera proces kontynuuje wykonywanie debugee.</span><span class="sxs-lookup"><span data-stu-id="55849-103">Notifies the ICorDebug pipeline that the out of process debugger is continuing the debugee's execution.</span></span>

## <a name="syntax"></a><span data-ttu-id="55849-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="55849-104">Syntax</span></span>

```
HRESULT ProcessStateChanged(
    [in] CorDebugStateChange change
);
```

## <a name="parameters"></a><span data-ttu-id="55849-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="55849-105">Parameters</span></span>

 `eChange`\
<span data-ttu-id="55849-106">[in] Członek [wyliczenie CorDebugStateChange](cordebugstatechange-enumeration.md) opisujące zmianę stanu wykonywania procesu.</span><span class="sxs-lookup"><span data-stu-id="55849-106">[in] A member of the [CorDebugStateChange enumeration](cordebugstatechange-enumeration.md) describing a change in the process's execution state.</span></span>

## <a name="remarks"></a><span data-ttu-id="55849-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="55849-107">Remarks</span></span>

<span data-ttu-id="55849-108">Podana metoda jest częścią `ICorDebugProcess4` interfejs i odpowiada czwarte miejsce tabeli wirtualnej metody.</span><span class="sxs-lookup"><span data-stu-id="55849-108">The provided method is part of the `ICorDebugProcess4` interface and corresponds to the fourth slot of the virtual method table.</span></span>

## <a name="requirements"></a><span data-ttu-id="55849-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="55849-109">Requirements</span></span>

 <span data-ttu-id="55849-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55849-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

 <span data-ttu-id="55849-111">**Nagłówek:** Brak</span><span class="sxs-lookup"><span data-stu-id="55849-111">**Header:** None</span></span>

 <span data-ttu-id="55849-112">**Biblioteka:** Brak</span><span class="sxs-lookup"><span data-stu-id="55849-112">**Library:** None</span></span>
 
 <span data-ttu-id="55849-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55849-113">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="55849-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="55849-114">See also</span></span>

- [<span data-ttu-id="55849-115">ICorDebugProcess4 Interface</span><span class="sxs-lookup"><span data-stu-id="55849-115">ICorDebugProcess4 Interface</span></span>](icordebugprocess4-interface.md)
- [<span data-ttu-id="55849-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="55849-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
- [<span data-ttu-id="55849-117">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="55849-117">Debugging</span></span>](index.md)
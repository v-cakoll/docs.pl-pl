---
title: Wyliczenie CorDebugStateChange
ms.date: 02/07/2019
api_name:
- CorDebugStateChange
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 1d4424ab-5143-4e50-a84a-ceeb4ddf3bba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 676489880cb30ca540cb78d70797dbf4eedf7395
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739587"
---
# <a name="cordebugstatechange-enumeration"></a><span data-ttu-id="47d4b-102">Wyliczenie CorDebugStateChange</span><span class="sxs-lookup"><span data-stu-id="47d4b-102">CorDebugStateChange Enumeration</span></span>

<span data-ttu-id="47d4b-103">W tym artykule opisano wielkość pamięci podręcznej danych, które muszą zostać odrzucone na podstawie zmian do procesu.</span><span class="sxs-lookup"><span data-stu-id="47d4b-103">Describes the amount of cached data that must be discarded based on changes to the process.</span></span>

## <a name="syntax"></a><span data-ttu-id="47d4b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="47d4b-104">Syntax</span></span>

```cpp
typedef enum CorDebugStateChange
{
    PROCESS_RUNNING = 0x0000001,
    FLUSH_ALL       = 0x0000002,
} CorDebugStateChange;
```

## <a name="members"></a><span data-ttu-id="47d4b-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="47d4b-105">Members</span></span>

| <span data-ttu-id="47d4b-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="47d4b-106">Member</span></span>            | <span data-ttu-id="47d4b-107">Opis</span><span class="sxs-lookup"><span data-stu-id="47d4b-107">Description</span></span>                                                              |
| ----------------- | ------------------------------------------------------------------------ |
| `PROCESS_RUNNING` | <span data-ttu-id="47d4b-108">Proces osiągnięto nowy stan pamięci za pomocą wykonywania do przodu.</span><span class="sxs-lookup"><span data-stu-id="47d4b-108">The process reached a new memory state via forward execution.</span></span>            |
| `FLUSH_ALL`       | <span data-ttu-id="47d4b-109">Pamięć procesu może być dowolnie inny niż wcześniej.</span><span class="sxs-lookup"><span data-stu-id="47d4b-109">The process' memory may be arbitrarily different than it was previously.</span></span> |

## <a name="remarks"></a><span data-ttu-id="47d4b-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="47d4b-110">Remarks</span></span>

 <span data-ttu-id="47d4b-111">Członek `CorDebugStateChange` wyliczenia jest dostarczana jako argument, gdy wywołuje debugera `ProcessStateChanged` metody za pomocą [ICorDebugProcess4::ProcessStateChanged](icordebugprocess4-processstatechanged-method.md) lub [ICorDebugProcess6:: ProcessStateChanged](icordebugprocess6-processstatechanged-method.md)</span><span class="sxs-lookup"><span data-stu-id="47d4b-111">A member of the `CorDebugStateChange` enumeration is provided as an argument when the debugger calls the `ProcessStateChanged` method either with [ICorDebugProcess4::ProcessStateChanged](icordebugprocess4-processstatechanged-method.md) or [ICorDebugProcess6::ProcessStateChanged](icordebugprocess6-processstatechanged-method.md)</span></span>

## <a name="requirements"></a><span data-ttu-id="47d4b-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="47d4b-112">Requirements</span></span>

 <span data-ttu-id="47d4b-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47d4b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

 <span data-ttu-id="47d4b-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="47d4b-114">**Header:** CorDebug.idl, CorDebug.h</span></span>

 <span data-ttu-id="47d4b-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="47d4b-115">**Library:** CorGuids.lib</span></span>

 <span data-ttu-id="47d4b-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47d4b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="47d4b-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="47d4b-117">See also</span></span>

- [<span data-ttu-id="47d4b-118">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="47d4b-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="47d4b-119">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="47d4b-119">Debugging</span></span>](index.md)

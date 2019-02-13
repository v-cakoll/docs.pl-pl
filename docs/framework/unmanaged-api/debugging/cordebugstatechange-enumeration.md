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
ms.openlocfilehash: 05a29022d3ebad37322aef9826f10689d2b5b06b
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/13/2019
ms.locfileid: "56221137"
---
# <a name="cordebugstatechange-enumeration"></a><span data-ttu-id="6b251-102">Wyliczenie CorDebugStateChange</span><span class="sxs-lookup"><span data-stu-id="6b251-102">CorDebugStateChange Enumeration</span></span>

<span data-ttu-id="6b251-103">W tym artykule opisano wielkość pamięci podręcznej danych, które muszą zostać odrzucone na podstawie zmian do procesu.</span><span class="sxs-lookup"><span data-stu-id="6b251-103">Describes the amount of cached data that must be discarded based on changes to the process.</span></span>

## <a name="syntax"></a><span data-ttu-id="6b251-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6b251-104">Syntax</span></span>

```
typedef enum CorDebugStateChange
{
    PROCESS_RUNNING = 0x0000001,
    FLUSH_ALL       = 0x0000002,
} CorDebugStateChange;
```

## <a name="members"></a><span data-ttu-id="6b251-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="6b251-105">Members</span></span>

| <span data-ttu-id="6b251-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="6b251-106">Member</span></span>            | <span data-ttu-id="6b251-107">Opis</span><span class="sxs-lookup"><span data-stu-id="6b251-107">Description</span></span>                                                              |
| ----------------- | ------------------------------------------------------------------------ |
| `PROCESS_RUNNING` | <span data-ttu-id="6b251-108">Proces osiągnięto nowy stan pamięci za pomocą wykonywania do przodu.</span><span class="sxs-lookup"><span data-stu-id="6b251-108">The process reached a new memory state via forward execution.</span></span>            |
| `FLUSH_ALL`       | <span data-ttu-id="6b251-109">Pamięć procesu może być dowolnie inny niż wcześniej.</span><span class="sxs-lookup"><span data-stu-id="6b251-109">The process' memory may be arbitrarily different than it was previously.</span></span> |

## <a name="remarks"></a><span data-ttu-id="6b251-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6b251-110">Remarks</span></span>

 <span data-ttu-id="6b251-111">Członek `CorDebugStateChange` wyliczenia jest dostarczana jako argument, gdy wywołuje debugera `ProcessStateChanged` metody za pomocą [ICorDebugProcess4::ProcessStateChanged](icordebugprocess4-processstatechanged-method.md) lub [ICorDebugProcess6:: ProcessStateChanged](icordebugprocess6-processstatechanged-method.md)</span><span class="sxs-lookup"><span data-stu-id="6b251-111">A member of the `CorDebugStateChange` enumeration is provided as an argument when the debugger calls the `ProcessStateChanged` method either with [ICorDebugProcess4::ProcessStateChanged](icordebugprocess4-processstatechanged-method.md) or [ICorDebugProcess6::ProcessStateChanged](icordebugprocess6-processstatechanged-method.md)</span></span>

## <a name="requirements"></a><span data-ttu-id="6b251-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6b251-112">Requirements</span></span>

 <span data-ttu-id="6b251-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6b251-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>

 <span data-ttu-id="6b251-114">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6b251-114">**Header:** CorDebug.idl, CorDebug.h</span></span>

 <span data-ttu-id="6b251-115">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6b251-115">**Library:** CorGuids.lib</span></span>

 <span data-ttu-id="6b251-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6b251-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="6b251-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6b251-117">See also</span></span>

- [<span data-ttu-id="6b251-118">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="6b251-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="6b251-119">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="6b251-119">Debugging</span></span>](index.md)

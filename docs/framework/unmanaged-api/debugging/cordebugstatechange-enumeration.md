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
ms.openlocfilehash: d94422d25da91cd2a6653a95cbd852c3930a151a
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795693"
---
# <a name="cordebugstatechange-enumeration"></a><span data-ttu-id="f488a-102">Wyliczenie CorDebugStateChange</span><span class="sxs-lookup"><span data-stu-id="f488a-102">CorDebugStateChange Enumeration</span></span>

<span data-ttu-id="f488a-103">Opisuje ilość danych buforowanych, które muszą zostać odrzucone na podstawie zmian w procesie.</span><span class="sxs-lookup"><span data-stu-id="f488a-103">Describes the amount of cached data that must be discarded based on changes to the process.</span></span>

## <a name="syntax"></a><span data-ttu-id="f488a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f488a-104">Syntax</span></span>

```cpp
typedef enum CorDebugStateChange
{
    PROCESS_RUNNING = 0x0000001,
    FLUSH_ALL       = 0x0000002,
} CorDebugStateChange;
```

## <a name="members"></a><span data-ttu-id="f488a-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="f488a-105">Members</span></span>

| <span data-ttu-id="f488a-106">Członek</span><span class="sxs-lookup"><span data-stu-id="f488a-106">Member</span></span>            | <span data-ttu-id="f488a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="f488a-107">Description</span></span>                                                              |
| ----------------- | ------------------------------------------------------------------------ |
| `PROCESS_RUNNING` | <span data-ttu-id="f488a-108">Proces osiągnął nowy stan pamięci przez wykonanie do przodu.</span><span class="sxs-lookup"><span data-stu-id="f488a-108">The process reached a new memory state via forward execution.</span></span>            |
| `FLUSH_ALL`       | <span data-ttu-id="f488a-109">Pamięć procesu może być arbitralnie inna niż wcześniej.</span><span class="sxs-lookup"><span data-stu-id="f488a-109">The process' memory may be arbitrarily different than it was previously.</span></span> |

## <a name="remarks"></a><span data-ttu-id="f488a-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f488a-110">Remarks</span></span>

 <span data-ttu-id="f488a-111">Element członkowski `CorDebugStateChange` wyliczenia jest dostarczany jako argument, gdy debuger wywołuje `ProcessStateChanged` metodę z [ICorDebugProcess4::P rocessStateChanged](icordebugprocess4-processstatechanged-method.md) lub [Metoda ICorDebugProcess6::P rocessstatechanged](icordebugprocess6-processstatechanged-method.md)</span><span class="sxs-lookup"><span data-stu-id="f488a-111">A member of the `CorDebugStateChange` enumeration is provided as an argument when the debugger calls the `ProcessStateChanged` method either with [ICorDebugProcess4::ProcessStateChanged](icordebugprocess4-processstatechanged-method.md) or [ICorDebugProcess6::ProcessStateChanged](icordebugprocess6-processstatechanged-method.md)</span></span>

## <a name="requirements"></a><span data-ttu-id="f488a-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f488a-112">Requirements</span></span>

 <span data-ttu-id="f488a-113">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f488a-113">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>

 <span data-ttu-id="f488a-114">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f488a-114">**Header:** CorDebug.idl, CorDebug.h</span></span>

 <span data-ttu-id="f488a-115">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f488a-115">**Library:** CorGuids.lib</span></span>

 <span data-ttu-id="f488a-116">**.NET Framework wersje:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f488a-116">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v20plus-md.md)]</span></span>

## <a name="see-also"></a><span data-ttu-id="f488a-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f488a-117">See also</span></span>

- [<span data-ttu-id="f488a-118">Debugowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="f488a-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="f488a-119">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="f488a-119">Debugging</span></span>](index.md)

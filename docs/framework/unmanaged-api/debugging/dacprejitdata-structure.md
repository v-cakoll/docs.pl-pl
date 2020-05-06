---
title: DacpReJitData, struktura
ms.date: 02/01/2019
api.name:
- DacpReJitData Structure
api.location:
- mscordacwks.dll
api.type:
- COM
f1.keywords:
- DacpReJitData Structure
helpviewer.keywords:
- DacpReJitData Structure [.NET Framework debugging]
topic_type:
- apiref
author: hoyosjs
ms.author: juhoyosa
ms.openlocfilehash: 4436ece72b0a6a405fc41cba5413093fc42ce750
ms.sourcegitcommit: d9c7ac5d06735a01c1fafe34efe9486734841a72
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/06/2020
ms.locfileid: "82860781"
---
# <a name="dacprejitdata-structure"></a><span data-ttu-id="9fec1-102">DacpReJitData, struktura</span><span class="sxs-lookup"><span data-stu-id="9fec1-102">DacpReJitData Structure</span></span>

<span data-ttu-id="9fec1-103">Definiuje podstawowe informacje o danej metodzie Instrumentacji.</span><span class="sxs-lookup"><span data-stu-id="9fec1-103">Defines the basic information about a given profiler-instrumented method.</span></span>

[!INCLUDE[debugging-api-recommended-note](../../../../includes/debugging-api-recommended-note.md)]

## <a name="syntax"></a><span data-ttu-id="9fec1-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9fec1-104">Syntax</span></span>

```cpp
struct MSLAYOUT DacpReJitData
{
    enum Flags
    {
        kUnknown,
        kRequested,
        kActive,
        kReverted,
    };

    CLRDATA_ADDRESS                 rejitID;
    Flags                           flags;
    CLRDATA_ADDRESS                 NativeCodeAddr;
};
```

## <a name="members"></a><span data-ttu-id="9fec1-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="9fec1-105">Members</span></span>

| <span data-ttu-id="9fec1-106">Członek</span><span class="sxs-lookup"><span data-stu-id="9fec1-106">Member</span></span>           | <span data-ttu-id="9fec1-107">Opis</span><span class="sxs-lookup"><span data-stu-id="9fec1-107">Description</span></span>                                                                                      |
| ---------------- | ------------------------------------------------------------------------------------------------ |
| `rejitID`        | <span data-ttu-id="9fec1-108">Numer poprawki ReJit dla metody.</span><span class="sxs-lookup"><span data-stu-id="9fec1-108">The ReJit revision number for a method.</span></span>                                                          |
| `flags`          | <span data-ttu-id="9fec1-109">Flaga wskazująca bieżący stan Instrumentacji ReJit metody dla danej wersji.</span><span class="sxs-lookup"><span data-stu-id="9fec1-109">A flag indicating the current state of the method's ReJit instrumentation for the given version.</span></span> |
| `NativeCodeAddr` | <span data-ttu-id="9fec1-110">Adres podstawowy implementacji rejitted metody.</span><span class="sxs-lookup"><span data-stu-id="9fec1-110">The base address of the method's rejitted implementation.</span></span>                                         |

## <a name="remarks"></a><span data-ttu-id="9fec1-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9fec1-111">Remarks</span></span>

<span data-ttu-id="9fec1-112">Ta struktura jest w czasie wykonywania i nie jest udostępniana za pomocą żadnych plików nagłówkowych ani bibliotek.</span><span class="sxs-lookup"><span data-stu-id="9fec1-112">This structure lives inside the runtime and is not exposed through any headers or library files.</span></span> <span data-ttu-id="9fec1-113">Aby go użyć, Zdefiniuj strukturę zgodnie z powyższym opisem.</span><span class="sxs-lookup"><span data-stu-id="9fec1-113">To use it, define the structure as specified above.</span></span> <span data-ttu-id="9fec1-114">Strukturę należy również zdefiniować przy użyciu `ms_struct` pakowania, jeśli nie używa kompilatorów firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="9fec1-114">The structure must also be defined using `ms_struct` packing if not using the Microsoft compilers.</span></span>

## <a name="requirements"></a><span data-ttu-id="9fec1-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9fec1-115">Requirements</span></span>
<span data-ttu-id="9fec1-116">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9fec1-116">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
<span data-ttu-id="9fec1-117">**Nagłówek:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="9fec1-117">**Header:** None</span></span>  
<span data-ttu-id="9fec1-118">**Biblioteka:** Dawaj</span><span class="sxs-lookup"><span data-stu-id="9fec1-118">**Library:** None</span></span>  
<span data-ttu-id="9fec1-119">**.NET Framework wersje:**[!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span><span class="sxs-lookup"><span data-stu-id="9fec1-119">**.NET Framework Versions:** [!INCLUDE[net_current_v47plus](../../../../includes/net-current-v47plus.md)]</span></span>  

## <a name="see-also"></a><span data-ttu-id="9fec1-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9fec1-120">See also</span></span>

- [<span data-ttu-id="9fec1-121">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="9fec1-121">Debugging</span></span>](index.md)
- [<span data-ttu-id="9fec1-122">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="9fec1-122">Debugging Structures</span></span>](debugging-structures.md)
